# ����ʵ���ң�Azure Cloud Shell �е� Bash �Ŀ�������

������ϸ����������� Azure �Ż��� Azure Cloud Shell ��ʹ�� Bash��

## ���� Cloud Shell

1. ʹ�� Azure �ʻ���¼�� [Azure �Ż�](https://portal.azure.com)��

1. �� Azure �Ż��Ķ��������˵����� **��Cloud Shell��**��

![Cloud Shell ͼ��](../../Linked_Image_Files/shell-icon.png)

1. ѡ�����Դ����洢�ʻ��� Microsoft Azure �ļ�����

1. ѡ�� **�������洢��**��

>:pencil: **��ʾ:** ��ÿ���Ự�У��㽫���Զ�ͨ�� Azure CLI ���������֤��

## ѡ�� Bash ����

��鲢ȷ�� shell �������Ļ��������б���ʾ **��Bash��**��

![��ʾ Bash �Ļ���ѡ����](../../Linked_Image_Files/env-selector.png)

## ������Ķ���

1. �г���Ȩ���ʵĶ��ġ�

    ```
    az account list
    ```

1. ���������ѡ���ģ�

    ```
    az account set --subscription 'my-subscription-name'
    ```
>:pencil: **��ʾ��** ��ʹ�� `/home/<user>/.azure/azureProfile.json` ��ס���ģ��Թ��պ�Ựʹ�á�

## ������Դ��

�� WestUS �д�����Ϊ��MyRG��������Դ�顣

```
az group create --location westus --name MyRG
```

## ���� Linux VM

������Դ���д��� Ubuntu VM��Azure CLI ������ SSH ��Կ��ʹ����Щ��Կ���� VM��

```
az vm create -n myVM -g MyRG --image UbuntuLTS --generate-ssh-keys
```

>:heavy_check_mark: **ע�⣺** ʹ�� `generate-ssh-keys` ָʾ Azure CLI �� VM �� `$ Home` Ŀ¼�д��������ù�Կ��˽Կ��Ĭ������£���Կ���� Cloud Shell �е� `/home/<user>/.ssh/id_rsa` �� `/home/<user>/.ssh/id_rsa.pub` λ�á�`.ssh` �ļ��лᱣ���ڸ����ļ���������ڱ��� `$Home` �� 5 GB ӳ���С�

�� VM �ϵ��û������� Cloud Shell ��ʹ�õ��û��� ($User@Azure:)��

## SSH �� Linux VM

1. �� Azure �Ż������������� VM ���ơ�

1. ���� **�����ӡ�** �Ի�ȡ VM ���ƺ͹��� IP ��ַ��

    ![�����ӡ�ѡ��](../../Linked_Image_Files/sshcmd-copy.png)

1. ʹ�� ssh cmd �� SSH �� VM��

    ```
    ssh username@ipaddress
    ```

���� SSH ����ʱ��Ӧ�ÿ��Կ��� Ubuntu ��ӭ��ʾ��

![Ubuntu ��ӭ��ʾ](../../Linked_Image_Files/ubuntu-welcome.png)

## ����

1. �˳� SSH �Ự��

    ```
    exit
    ```

1. ɾ����Դ���Լ����е�������Դ��

    ```
    az group delete -n MyRG
    ```
