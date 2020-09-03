﻿# 迷你实验室：Blob 存储

在本迷你实验室中，你将探索 Blob 存储。

**注意**：本迷你实验室需要一个存储帐户。

## 创建容器

1. 前往 Azure 门户中的存储帐户。

2. 在存储帐户的左侧菜单中，滚动到 **“Blob 服务”** 部分，然后选择 **“Blob”**。

3. 选择 **“＋容器”** 按钮。

4. 为您的新容器输入一个 **“名称”**。容器名称必须小写，必须以字母或数字开头，并且只能包含字母、数字和短划线（-）字符。 

5. 设置容器的公共访问级别。默认级别为“私人”（无匿名访问）。

6. 选择 **“确定”**，创建容器。

## 上传一个块 blob

1. 在 Azure 门户中，前往您在上一部分中创建的容器。

2. 选择容器，以显示其包含的 blob 列表。由于该容器是新的，因此它不会包含任何 blob。

3. 选择  **“上传”** 按钮，将 blob 上传到容器。

4. 展开  **“高级”** 部分。

5. 注意  **“身份验证类型”**、 **“blob 类型”**、 **“块大小”**、以及 **“上传到文件夹”** 的能力。

6. 注意，默认的 **身份验证类型** 为 SAS。

4. 浏览你的本地文件系统，查找要作为块 Blob 上传的文件，然后选择 **“上传”**。

5. 以该方式上传任意多个 Blob。你会发现新的 Blob 已经位于容器的列表中。

## 下载数据块 Blob

你可以下载块 Blob，以在浏览器中显示，或保存到本地文件系统。 

1. 前往你在上一部分中上传的 Blob 列表。

2. 右键单击你要下载的 Blob，然后选择**下载**。
