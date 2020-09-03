﻿# 迷你实验室：使用 Azure 多重身份验证保护用户登录事件

多重身份验证 (MFA) 是在登录事件期间提示用户完成其他形式的身份识别的过程。可能会提示用户在手机上输入密码或提供指纹扫描。要求第二种形式的身份验证可提高安全性，因为攻击者不容易获得或复制其他因素。

在特定的登录事件期间，可以通过 Azure 多重身份验证和条件访问策略来灵活地为用户启用 MFA。

**前提条件**

若要执行此微型实验室，你需要以下资源和特权：

* 已启用 Azure AD Premium 或试用许可证的有效 Azure AD 租户。 


* 具有全局管理员特权的帐户。

* 具有已知密码的非管理员用户，例如 testuser。在此小型实验室中使用此帐户测试最终用户 Azure 多重身份验证体验。 


* 非管理员用户所属的组，例如 MFA-Test-Group。在此小型实验室中为此组启用 Azure 多重身份验证。 


## 创建“条件访问策略”

启用和使用 Azure 多重身份验证的推荐方法是使用条件访问策略。借助条件访问，可以创建和定义对登录事件作出反应并请求其他操作的策略，然后再授予用户对应用程序或服务的访问权限。

![条件访问如何确保登录过程安全的概述图](../../Linked_Image_Files/demo_conditional_access_image1.png)

此小型实验室将创建一个基本的条件访问策略，用于在用户登录 Azure 门户时提示进行 MFA。 

首先，按如下所述创建一个条件访问策略，并分配测试用户组：

1. 使用拥有全局管理员权限的帐户登录到 [Azure 门户](https://portal.azure.com/)。

2. 搜索并选择 **“Azure Active Directory”**，然后选择 **“安全”**。

3. 依次选择 **“条件访问”**、 **“+ 新建策略”**。

4. 输入策略名称，例如 *“MFA Pilot”*。

5. 在 **“分配”** 下，选择 **“用户和组”** ，然后是 **“选择用户和组”**。

6. 选中复选框 **“用户和组”**，然后单击 **“选择”**。

7. 浏览并选择 Azure AD 组（例如 *MFA-Test-Group*），然后选择 **“选择”**。

    [![图 3](../../Linked_Image_Files/conditional_access_image2.png)](https://docs.microsoft.com/zh-cn/azure/active-directory/authentication/media/tutorial-enable-azure-mfa/select-group-for-conditional-access.png#lightbox)

8. 若要对该组应用条件访问策略，请选择 **“完成”**。

## 配置多重身份验证的条件

创建条件访问策略并分配测试用户组后，现在可以定义触发该策略的云应用或操作。这些云应用或操作是你确定需要进一步处理的方案，例如，提示执行 MFA。 

将条件访问策略配置为在用户登录 Azure 门户时要求进行 MFA。

1. 选择 **“云应用或操作”**。可以选择将条件访问策略应用到 *“所有云应用”* 或者 *“选择应用”*。

1. 在 **“包含”** 页面上，选择 **“选择应用”**。

2. 选择 **“选择”**，然后浏览可用的登录事件列表。

1. 选择 **“Microsoft Azure 管理”**，从而将策略应用于 Azure 门户的登录事件。

3. 若要应用选定的应用，请选择 **“选择”**，然后选择 **“完成”**。

    ![选择要包含在条件访问策略中的 Microsoft Azure 管理应用](../../Linked_Image_Files/demo_conditional_access_image3.png)

1. 访问控制使你可以定义授予用户访问权限的要求，例如需要经过批准的客户端应用或使用已加入混合 Azure AD 的设备。将访问控制配置为在 Azure 门户的登录事件期间需要进行 MFA。

1. 在 **“访问控制”** 下，选择 **“授权”**，然后确保选择 **“授予访问权限”**。

2. 选中 **“需要多重身份验证”** 对应的复选框，然后选择 **“选择”**。

    如果希望查看配置对用户的影响，可以将“条件访问”策略设置为“仅报告”；如果不想立即使用策略，可以设置为“关”。因为该演示针对的是一组测试用户，所以我们启用策略，然后测试 Azure 多重身份验证。

1. 将 *“启用策略”* 设置为 **“开”**。

2. 若要应*用条件访问策略*，请选择 **“创建”**。

## 测试 Azure 多重身份验证

若要查看条件访问策略和 Azure 多重身份验证，请按以下步骤登录到不需要 MFA 的资源：

1. 在 InPrivate 模式或隐身模式下打开新的浏览器窗口，然后浏览到 [https://account.activedirectory.windowsazure.com](https://account.activedirectory.windowsazure.com/)。

2. 以非管理员测试用户（例如 testuser）的身份登录。系统不会提示完成 MFA。

3. 关闭浏览器窗口。

    现在登录到 Azure 门户。由于在条件访问策略中将 Azure 门户配置为需要附加验证，因此你将收到 Azure 多重身份验证提示。

1. 在 InPrivate 模式或隐身模式下打开新的浏览器窗口，然后浏览到 [https://portal.azure.com](https://portal.azure.com/)。

2. 以非管理员测试用户（例如 testuser）的身份登录。需要注册并使用 Azure 多重身份验证。按照提示完成流程，并确认已成功登录到 Azure 门户。

    ![遵循浏览器提示，然后在你注册的多重身份验证提示上登录](../../Linked_Image_Files/demo_conditional_access_image4.png)

 