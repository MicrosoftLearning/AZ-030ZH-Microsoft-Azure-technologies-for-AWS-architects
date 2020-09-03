﻿# 迷你实验室：创建共享访问签名（端口）

在本迷你实验室中，我们将创建共享访问签名 (SAS)。

>:heavy_check_mark: **注意：** 本迷你实验室需要带有 Blob 容器和上传文件的存储帐户。 

## 在服务级别创建 SAS

1. 登录至 Azure 门户，网址：[https://portal.azure.com](https://portal.azure.com/)

2. 寻找需要使用的存储帐户并将其打开。深入分析你的 blob 容器。

3. 单击希望为其提供访问权限的文件。

4. 选择 **“生成 SAS”** 选项卡。

5. 使用以下参数配置共享访问签名：

   * **权限**： 读取

   * **开始和到期日期/时间**。今天为开始日期，1 年后到期

   * **允许的协议**： HTTPS

   * **签名密钥**： Key1

6. 复制 **Blob 服务器 SAS URL** 并将 URL 粘贴到浏览器中。

7. 验证 blob 文件是否显示。

8. 查看你在课程中了解到的不同 URL 参数。 

## 在帐户级别创建 SAS

1. 返回存储帐户。

2. 单击 **“共享访问签名”**。

3. 请注意，你可以配置各种服务、资源类型和权限。 

4. 单击 **“生成 SAS 和连接字符串”**。

5. 查看提供的连接字符串、SAS 令牌和 URL 信息。 