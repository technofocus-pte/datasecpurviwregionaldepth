# Lab 7 - 配置Communication Compliance

## 目标：

在本 lab
中，您将配置合规性策略，以检测组织中用户传达的任何敏感信息。您将使用在前面的实验室中创建的敏感信息类型来检测通过电子邮件传达的员工健康数据或员工
ID。

练习 1 - 启用Communication compliance权限

在此任务中，您将用户分配到特定角色组，以对组织中不同用户之间的communication
compliance、访问权限和职责进行分段。

1.  如果 Microsoft Purview 门户已打开，请继续执行步骤 2，否则，请打开
    **+++https://purview.microsoft.com+++** 并使用 **MOD
    管理员**凭据登录。

2.  

3.  在导航 中选择 "**设置"**，然后在 "角色组 "下选择 "**角色组**" ，选择
    " **Communication Compliance** " 。然后选择
    "**编辑**"。在侧窗格中，再次选择 "**编辑**"。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

4.  在**编辑角色组成员** 上选择 "**选择用户"**。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  确保选择 **MOD 管理员**、**Megan Bowen** 和 **Patti Fernandez**
    。然后选择 "**选择**"。

![](./media/image7.png)

6.  

7.  选择 **下一步**。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

8.  选择**保存**将用户添加到角色组。选择 Done 以完成这些步骤。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

![A screenshot of a computer Description automatically
generated](./media/image13.png)

练习 2 - 设置Communication compliance性组

在策略中，您将使用电子邮件地址来识别个人或人群。为简化设置，您可以为需要审核其通信的人员创建组，为审核这些通信的人员创建组。

您可以使用 PowerShell
为指定组的全局通信合规性策略配置一个分发组。这样，您就可以使用单个策略检测成千上万用户的信息，并在新员工加入组织时不断更新communication
compliance 策略。

1.  以管理员模式打开 **PowerShell**。

2.  输入以下 cmdlet 以使用 **Exchange Online PowerShell**
    模块并连接到租户：

**+++Connect-ExchangeOnline++++**

![Text Description automatically generated](./media/image14.png)

3.  **登录**窗口显示后，以 **MOD 管理员**身份登录。

![BrokenImage](./media/image15.png)

4.  为您的全局 Communication Compliance
    策略创建一个具有以下属性的专用分发组：

    - **MemberDepartRestriction =
      已关闭。**确保用户无法将自己从通讯组中删除。

    - **MemberJoinRestriction =
      已关闭。**确保用户无法将自己添加到通讯组。

    - **ModerationEnabled =
      True。**确保发送到此组的所有消息都需要审批，并且该组不用于通信合规性策略配置之外的通信。

**New-DistributionGroup -Name "Communication Purview Group Contoso"
-Alias "CCG_Contoso" -MemberDepartRestriction 'Closed'
-MemberJoinRestriction 'Closed' -ModerationEnabled
$true** ![BrokenImage](./media/image16.png)

**注意：**您可以添加 **Exchange
自定义属性（如下**命令**所示），以**跟踪添加到组织内 Communication
Compliance 策略中的用户。

**+++Set-DistributionGroup -Identity "Communication Compliance Group
Contoso"-CustomAttribute1 "MonitoredCommunication "+++**

![A screen shot of a computer Description automatically
generated](./media/image17.png)

5.  按周期运行以下 PowerShell 脚本，将用户添加到 Communication
    Compliance 策略中：

> **$Mbx = (Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize
> Unlimited -Filter {CustomAttribute9 -eq $Null})** 
>
> **$i = 0** 
>
> **ForEach ($M in $Mbx)** 
>
> **{** 
>
> ** Write-Host "Adding" $M.DisplayName** 
>
> ** Add-DistributionGroupMember -Identity "Communication Compliance
> Group Contoso" -Member $M.DistinguishedName -ErrorAction
> SilentlyContinue** 
>
> ** Set-Mailbox -Identity $M.Alias -CustomAttribute1
> "MonitoredCommunication"** 
>
> ** $i++** 
>
> **}** 
>
> **Write-Host $i "Mailboxes added to supervisory review distribution
> group."**

![BrokenImage](./media/image18.png)

**注意：**该脚本应在每个特定时间间隔后运行。现在，您可以在 Microsoft 365
管理中心的 "Active teams & Groups（活动团队和组）"下看到分发列表。

点击群组名称，就能看到成员选项卡下列出的所有用户。

![BrokenImage](./media/image19.png)

## 练习 3 - 创建Communication Compliance政策

1.  如果 Microsoft Purview 合规门户已打开，请继续执行步骤
    2，否则，请打开 **+++https://purview.microsoft.com+++** 并以 **MOD
    管理员**身份登录。

2.  在 **Microsoft Purview portal**, 选择 **Solutions** \>
    **Communication compliance**. **。**

![A screenshot of a computer Description automatically
generated](./media/image21.png)

3.  从子导航中选择 "**策略**"。然后选择**创建策略**。

![A screenshot of a computer Description automatically
generated](./media/image23.png)

4.  从下拉菜单中选择**自定义策略**。

![](./media/image25.png)

5.  在 "命名您的 DLP 策略 "页面，在 "**名称 "**字段中键入 **+++
    我的第一个通信合规性策略++++，**在 "**说明** "字段中键入 **+++
    这是一个测试通信合规性的策略+++**。选择**下一步**。

![Graphical user interface, text, application Description automatically
generated](./media/image26.png)

6.  在 "**选择受监督的用户和审核员** "页面，保留其余默认设置，并在 "审核
    "下添加 Patti **Fernandez**。然后点击**下一步**。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

7.  在**通信**页面上，选中 **Microsoft 365
    位置**下的所有复选框，然后点击下**一步**。

![A screenshot of a computer Description automatically
generated](./media/image30.png)

8.  在 "**选择条件和审查百分比** "中，选择
    "**添加条件**"，从下拉菜单中选择
    "**内容包含任何这些敏感信息类型**"。

![A screenshot of a computer screen Description automatically
generated](./media/image32.png)

9.  在 "**内容包含任何这些敏感信息类型** "框中，选择 "**添加**"，单击
    "**敏感信息类型**"，然后搜索
    **contoso**。选中我们在之前的实验室中创建的所有敏感信息类型的复选框。然后单击**添加**

![Graphical user interface, text, application Description automatically
generated](./media/image33.png)

10. 在 **"选择条件和审查百分比** "中，选中 "**使用 OCR
    从图像中提取文本** "旁边的复选框，将**审查百分比设为
    100%**，然后单击 "**下一步**"。

![Graphical user interface, application Description automatically
generated](./media/image34.png)

11. 在**审查和完成**页面，选择**创建策略**。

![Graphical user interface, text, application Description automatically
generated](./media/image35.png)

12. 将显示 "**已创建**策略
    "页面，其中包含关于何时激活策略和捕获哪些通信的指导。

![Graphical user interface, text, application Description automatically
generated](./media/image36.png)

## 练习 4 - 编辑communication compliance政策

1.  如果 Microsoft Purview 合规性门户已打开，请继续执行步骤
    2，否则，请打开 **+++https://** **purview.microsoft.com+++** 并以
    **MOD 管理员**身份登录。

2.  在 Microsoft purview portal 中选择\> **Communication compliance**
    "\>"**策略**"，选择 "**我的第一个Communication compliance策略
    "**附近的三个点，然后选择 "**编辑**"。

![A screenshot of a computer Description automatically
generated](./media/image37.png)

3.  将 "**名称 "和 "政策描述** "留空，然后单击 "**下一步**"。

![Graphical user interface, text, application Description automatically
generated](./media/image39.png)

4.  在 **"选择受监督用户和审阅人** "和 **"受监督用户和组** "下，选择
    "**选择用户** "按钮。

![Graphical user interface, application, Teams Description automatically
generated](./media/image40.png)

5.  

6.  在**开始键入查找用户或组**，搜索 **Communication (通信)**并选择
    **Communication Compliance Groups Contoso**。

![](./media/image42.png)

7.  在 "审阅人 "下的 "选择受监督的用户和审阅人 "中，将 MOD
    管理员添加到审阅人中。

![Graphical user interface, application, Teams Description automatically
generated](./media/image44.png)

8.  选择 "**下一步"**，直至到达 "**审查和完成** "页面。

9.  点击**保存**。

## 练习 5 - 创建通知模板和配置用户 匿名化

1.  在 Microsoft Purview 门户中， ，从右上角选择 "设置"，然后选择
    **Communication Compliance**。

![](./media/image45.png)

2.  选择 "**隐私** "选项卡。要启用匿名化，
    ，确保选中了**显示匿名版本的用户名**。选择**保存**。

![A screenshot of a computer Description automatically
generated](./media/image48.png)

3.  导航至**通知模板**选项卡，然后选择**创建通知模板**。

![](./media/image49.png)

4.  在**修改通知模板**页面，填写以下字段：

    - 模板名称（必填）：**+++通知样本+++**

    - 发送自（必填）：选择 Patti **Fernandez**，输入 Patti
      并从下拉菜单中选择姓名。

    - 抄送（可选）：输入 **MOD** 并从下拉菜单中选择 **MOD
      管理员**的姓名。

    - 主题（必填）：**+++您的通信紫罗兰公司通信合规政策。**

    - 信息正文（必填）：**+++Your communication violets company
      Communication compliance policy.+++**

5.  选择**创建**，创建并保存通知模板。

![A screenshot of a computer Description automatically
generated](./media/image52.png)

## 练习 6 - 测试您的communication compliance政策

在试用账户中，您没有发送任何电子邮件的权限，但您可以查看以下步骤，了解在拥有自己的许可证后如何测试策略。您可以执行步骤，但您的邮件将无法从当前租户发送到收件人。

1.  进入 **+++https://outlook.office365.com/mail/+++** 打开
    outlook**，**使用用户名 **+++ adelev@WWLxXXXXXX.onmicrosoft.com+++**
    和用户密码登录。

2.  向您的个人电子邮件账户发送一封电子邮件，邮件内容如下： 正文 。

信息正文：**+++Employee Patti Fernandez EMP123456 is on absence because
of flu/influenza++++** **+++Employee Patti Fernandez EMP123456 is on
absence because of flu/influenza++++**

**注意** 电子邮件信息在策略中完全处理大约需要 24 小时。Microsoft
Teams、Yammer 和第三方平台中的通信大约需要 48 小时才能在策略中完全处理。

登录 **+++https://purview.microsoft.com/+++** 作为 Patti **Fernandez**
。导航至 **Communication Compliance** \> **警报**，查看 24
小时后的保单**警报**。

**摘要**

在本 lab
中，我们学习了如何启用通信合规性权限、创建策略、管理策略，然后创建通知模板并配置用户匿名化。
