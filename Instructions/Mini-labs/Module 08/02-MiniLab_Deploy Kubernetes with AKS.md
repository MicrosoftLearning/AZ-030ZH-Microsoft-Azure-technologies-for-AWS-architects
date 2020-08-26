# 迷你实验室：使用 AKS 部署 Kubernetes

你将在本小型实验室中了解以下内容：

* 创建新资源组。

* 配置群集网络。

* 创建一个 Azure Kubernetes 服务群集。

* 使用 kubectl 连接到 Kubernetes 群集。

* 创建 Kubernetes 命名空间。

## 创建新资源组

首先，你需要创建一个资源组，以便将资源部署到其中。

1. 使用你的 Azure 帐户登录 Azure Cloud Shell。选择 Cloud Shell 的 Bash 版本。

[Azure Cloud Shell](https://shell.azure.com/)

2. 你需要选择一个要在其中创建资源组的区域，例如 **“美国东部”** 。如果选择其他值，请在本模块的其余练习中记住该值。可能需要在 Cloud Shell 会话之间重新定义值。运行以下命令以将这些值记录在 Bash 变量中。

```Azure CLI
REGION_NAME=eastus
RESOURCE_GROUP=aksworkshop
SUBNET_NAME=aks-subnet
VNET_NAME=aks-vnet
 ```

你可以使用 echo 命令检查每个值，例如 echo ```$REGION_NAME```。

3. 使用名称**aksworkshop 创建一个新的资源组。在这些资源组中部署在这些练习中创建的所有资源。完成模块后，单个资源组使清理资源变得更加容易。

```Azure CLI
az group create \
    --name $RESOURCE_GROUP \
    --location $REGION_NAME
```

## 网络配置

部署 AKS 群集时，有两种网络模型可供选择。第一个模型是 *Kubenet 网络*，第二个是 *Azure 容器网络接口 (CNI) 网络*。

## Kubenet 网络

Kubenet 网络是 Kubernetes 中的默认网络模型。通过 Kubenet 网络，可以从 Azure 虚拟网络子网为节点分配 IP 地址。Pod 从逻辑上不同的地址空间接收到节点的 Azure 虚拟网络子网的 IP 地址。

然后配置网络地址转换 (NAT)，以便 Pod 可以访问 Azure 虚拟网络上的资源。流量的源 IP 地址将转换为节点的主 IP 地址，然后在节点上进行配置。请注意，Pod 收到的 IP 地址“隐藏”在节点 IP 后面。

## Azure 容器网络接口 (CNI) 网络

通过 Azure 容器网络接口 (CNI)，AKS 群集会连接到现有虚拟网络资源和配置。在这种网络模型中，每个 Pod 从子网获取 IP 地址，并且可以直接访问。这些 IP 地址在整个网络空间中必须是唯一的，并且需要预先计算。

你将要使用的某些功能要求你通过使用 *Azure 容器网络接口网络* 配置。

在下面，你将为 AKS 群集创建虚拟网络。部署群集时，将使用此虚拟网络并指定网络模型。

1. 首先，创建虚拟网络和子网。将对群集中部署的 Pod 分配该子网中的 IP。运行以下命令以创建虚拟网络。

```Azure CLI
az network vnet create \
    --resource-group $RESOURCE_GROUP \
    --location $REGION_NAME \
    --name $VNET_NAME \
    --address-prefixes 10.0.0.0/8 \
    --subnet-name $SUBNET_NAME \
    --subnet-prefix 10.240.0.0/16
```

2. 接下来，通过运行以下命令检索子网 ID 并将其存储在 Bash 变量中。

```Azure CLI
SUBNET_ID=$(az network vnet subnet show \
    --resource-group $RESOURCE_GROUP \
    --vnet-name $VNET_NAME \
    --name $SUBNET_NAME \
    --query id -o tsv)
```

## 创建一个 AKS 群集

有了新的虚拟网络后，你可以创建新的群集。在运行 ```az aks create``` 命令之前，需要了解两个值。第一个是所选区域中可用的最新非预览版 Kubernetes 的版本，第二个是群集的唯一名称。

1. 要获得最新的非预览版 Kubernetes，请使用 ```az aks get-versions``` 命令。将命令返回的值存储在名为 ```VERSION``` 的 Bash 变量中。运行下面的命令，检索并存储版本号。

```Azure CLI
SUBNET_ID=$(az network vnet subnet show \
    --resource-group $RESOURCE_GROUP \
    --vnet-name $VNET_NAME \
    --name $SUBNET_NAME \
    --query id -o tsv)
```

2. AKS 群集名称必须唯一。运行以下命令以创建具有唯一名称的 Bash 变量。

```Bash
AKS_CLUSTER_NAME=aksworkshop-$RANDOM
```

3. 运行以下命令以输出存储在 ```$AKS_CLUSTER_NAME``` 中的值。请记下以备后用。如有必要，你将需要它在以后重新配置变量。

```Bash
echo $AKS_CLUSTER_NAME
```

4. 运行以下 ```az aks create``` 命令来创建运行最新 Kubernetes 版本的 AKS 群集。执行此命令可能需要几分钟。

```Azure CLI
az aks create \
--resource-group $RESOURCE_GROUP \
--name $AKS_CLUSTER_NAME \
--vm-set-type VirtualMachineScaleSets \
--load-balancer-sku standard \
--location $REGION_NAME \
--kubernetes-version $VERSION \
--network-plugin azure \
--vnet-subnet-id $SUBNET_ID \
--service-cidr 10.2.0.0/24 \
--dns-service-ip 10.2.0.10 \
--docker-bridge-address 172.17.0.1/16 \
--generate-ssh-keys
```

## 使用 Kubectl 测试群集连接性

```kubectl``` 是用于与群集交互的主要 Kubernetes 命令行客户端，可在 Cloud Shell 中使用。需要群集上下文，以允许 ```kubectl``` 连接到群集。上下文包含群集的地址、用户和命名空间。使用 az aks get-credentials 命令配置 ```kubectl``` 实例。

1. 通过运行以下命令来检索群集凭据。

```Azure CLI
az aks get-credentials \
    --resource-group $RESOURCE_GROUP \
    --name $AKS_CLUSTER_NAME
```

2. 你可以通过列出群集中的所有节点来查看部署的内容。使用 ```kubectl``` get nodes 命令列出所有节点。

```Bash
kubectl get nodes
```

你将看到群集节点列表。举个例子：

```Ouput
NAME                                STATUS   ROLES   AGE  VERSION
aks-nodepool1-24503160-vmss000000   Ready    agent   1m   v1.15.7
aks-nodepool1-24503160-vmss000001   Ready    agent   1m   v1.15.7
aks-nodepool1-24503160-vmss000002   Ready    agent   1m   v1.15.7
```

## 为应用程序创建 Kubernetes 命名空间

Kubernetes 中的命名空间会创建逻辑隔离边界。资源名称必须是命名空间内的唯一名称，而非跨命名空间的唯一名称。如果在使用 Kubernetes 资源时未指定命名空间，意味着使用默认命名空间。

为你的评级应用程序创建一个命名空间。

1. 列出群集中的当前命名空间。

```Bash
kubectl get namespace
```

你将看到与此输出类似的命名空间列表。

```Ouput
NAME              STATUS   AGE
default           Active   1h
kube-node-lease   Active   1h
kube-public       Active   1h
kube-system       Active   1h
```

2. 使用 ```kubectl``` create namespace 命令为名为 **ratingapp** 的应用程序创建一个命名空间。

```Bash
kubectl create namespace ratingsapp
```

你将看到提示已创建命名空间的确认消息。

```Output
namespace/ratingsapp created
```


 
