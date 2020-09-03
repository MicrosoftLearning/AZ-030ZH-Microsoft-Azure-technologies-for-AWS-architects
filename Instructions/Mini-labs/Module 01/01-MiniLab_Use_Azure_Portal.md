﻿# 迷你实验室：使用 Azure 门户。

Azure 门户提供多种功能和服务；我们来看一下你通常使用的一些更常见领域。首先，花一点时间将鼠标指针悬停在顶部菜单栏中的每个图标上，并分别停留几秒钟。你应该会看到每个图标对应的工具提示标签弹出窗口。此标签是菜单项的名称。稍后将使用这些图标。

![Azure 门户图标栏的屏幕截图](../../Linked_Image_Files/5-portal-icon-bar.png)

## 所有服务

1. 使用 Azure 帐户登录到 [Azure 门户](https://portal.azure.com)。

1. 在 Azure 门户的左上角选择 **“显示门户”** 菜单。

     ![门户菜单选项的屏幕截图](../../Linked_Image_Files/5-show-portal-menu.png)

1. 选择**所有服务**。花几分钟时间浏览列表，查看 Azure 提供了多少服务。

1. 可以通过 **“搜索全部”** 框来搜索服务。

1. 选择 **“虚拟机”**。如果看不到该选项，请使用搜索框。 **“虚拟机”** 窗格出现。你尚未创建任何虚拟机，因此没有结果显示。

1. 选择 **“+ 添加”**。即会出现 **“创建虚拟机”** 窗格。

1. 选择右上角的 **“X”** 关闭 **“创建虚拟机”** 窗格。

1. 选择右上角的 **“X”** 关闭 **“虚拟机”** 窗格。

1. 选择左上角的 **“Microsoft Azure”** 返回主页。

## Azure Cloud Shell

![表示 Azure Cloud Shell 的图标](../../Linked_Image_Files/5-cloud-shell-icon.png)

Azure Cloud Shell 使你可以在 Azure 订阅中使用命令行接口 (CLI) 执行命令。可以通过选择工具栏中的图标来访问它。还可以导航到 https://shell.azure.com，并在独立于门户的浏览器中启动 Cloud Shell。

Azure Cloud Shell 适用于沙盒环境，但是沙盒版 Shell 的功能有所减少。若要使用所有 Azure Cloud Shell 功能，请使用自己的 Azure 订阅。

启动 shell 时，你会看到一个欢迎窗口。可以选择 **Bash** 或 **PowerShell** 环境，具体取决于个人喜好。也可以随时通过 shell 左侧的语言下拉列表更改 shell。

最后，创建的环境中包含各种管理和编程工具。

- Azure 命令行工具（Azure CLI、AzCopy 等）

- 语言/框架，包括 .NET Core、Python 和 Java

- 针对 Docker、Kubernetes 等的容器管理支持

- 代码编辑器，例如 vim、emacs、code 和 nano

- 生成工具（make、maven、npm 等）

- 数据库查询工具，例如 sqlcmd

## 目录和订阅

![表示订阅面板的图标](../../Linked_Image_Files/5-subscription-icon.png)

1. 选择 **“目录+订阅”** （书和过滤器）图标来显示 **“目录+订阅”** 窗格。

  在这里可以在多个订阅或目录之间切换。你应该可以看到自己位于这里的 Microsoft Learn Sandbox 目录的礼宾订阅中。如果将其他 Azure 目录绑定到同一电子邮件地址，则这些订阅也将可用。

  还有一个用于了解有关目录和订阅更多信息的链接。

2. 选择右上角的 **“X”**，关闭 **“目录 + 订阅”** 窗格。

## “通知”窗格

1. 在图标栏菜单栏上，选择 **“通知”** （钟形）图标。该窗口列出所有挂起的通知。

    ![通知窗口的屏幕截图](../../Linked_Image_Files/5-notifications-pane.png)

1. 如果出现任何通知，请将鼠标悬停在其中一个通知上。选择该通知中出现的 **“X”** 来将其关闭。

1. 选择 **“全部消除”**。现在应该没有任何通知显示。

1. 选择右上角的 **“X”** 来关闭 **“通知”** 窗格。

## 设置

![表示设置面板的图标](../../Linked_Image_Files/5-settings-icon.png)

1. 选择 **“设置”** （齿轮）图标来打开 **“门户设置”** 窗格，默认显示 **“常规”** 设置。

1. 下拉 **“不活动时将我注销”** 设置，然后选择 **“一小时后”**。

1. 在 **“选择主题”** 下，选择不同颜色的主题，并观察门户 UI 的变化。将其设置为你最喜欢的一种。

1. 在 **“高对比度主题”** 下，请尝试三个不同的选项。

1. 选择 **“启用弹出式通知”**。选中此选项后，通知将显示为“toast”风格的弹出式通知。并且仍将出现在通知（钟形）图标中。

1. 选择设置中的 **“语言和区域”** 选项卡。选择 **“语言”** 并选择 **“Español”**，然后选择 **“应用”** 按钮。如果出现 **“翻译此页面”** 对话框，则将其关闭。现在，整个门户都以西班牙语显示。

1. 要恢复为英文，请选择顶部菜单栏中的**设置** （齿轮）图标，然后切换到 **“Idioma y región”** 设置。选择 **“Idioma”**，然后选择 **“英语”**。选择 **“Aplicar”** 按钮。门户将重新以英语显示。

## “帮助”窗格

![表示帮助面板的图标](../../Linked_Image_Files/5-help-icon.png)

1. 选择**帮助** (?) 图标以显示 **“帮助”** 窗格。

1. 选择 **“帮助 + 支持”** 按钮。

1. 在 **“帮助 + 支持”** 窗格中的 **“支持”** 下面，选择 **“新建支持请求。”** 要新建支持请求，需要在以下各部分填写信息，然后选择 **“创建”** 来提出问题。

    - **基本信息**： 问题类型

    - **问题**： 问题严重性、摘要和描述以及任何其他信息

    - **联系信息**： 首选联系方式以及与此联系方式相关的信息

1. 可以通过选择 **“所有支持请求”** 来查看支持请求的状态。

>:heavy_check_mark:**注意:** 支持请求只能使用活动付费订阅创建。

### 新增功能和其他信息

1. 选择**帮助**图标并选择 **“新增功能”**。

1. 查看最近发布的功能。另请注意和探索其他 **“帮助”** 菜单选项，例如：

    - Azure 路线图

    - 启动指导教程

    - 键盘快捷键

    - 显示诊断

    - 隐私声明

1. 选择右上角的 **“X”** 关闭 **“帮助”** 窗格。

1. 关闭 **“新增功能”** 窗格。你现在应该会回到“仪表板”。

## “反馈”窗格

![表示反馈面板的图标](../../Linked_Image_Files/5-feedback-icon.png)

1. 选择**反馈**（笑脸）图标打开 **“向我们发送反馈”** 窗格。

1. 在 **“告诉我们你的体验”** 框中输入你对 Azure 的印象，选择显示 **“Microsoft 可就你的反馈向你发送电子邮件”** 框，然后选择 **“提交反馈”**。

1. **“反馈已发送”** 消息将出现，然后关闭。你现在应该会回到“仪表板”。

## 个人资料设置

1. 在门户的右上角选择你的姓名。选项包括：

    - 使用其他帐户登录，或完全退出

    - 查看帐户资料，可以从中更改密码

    - 提交想法

    - 检查权限

    - 查看帐单

    - 更新联系信息

    除非选择“...”图标，否则其中一些项目不会出现。

1. 选择“...”，然后选择 **“查看我的帐单”** 导航到 **“成本管理 + 计费 - 发票”** 页，该页可帮助分析 Azure 在何处产生成本。

1. 从下拉列表中选择订阅。

1. 选择计费周期。

1. 记下服务费用，并对照当前订阅的预期费用进行检查。

1. 选择右上角的 **“X”** 关闭 **“按服务划分的费用”** 窗格。

1. 选择右上角的 **“X”** 关闭 **“成本管理 + 计费 - 发票”** 页面并返回主页。