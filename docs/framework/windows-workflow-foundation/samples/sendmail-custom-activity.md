---
title: SendMail 自定义活动
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 89252098402deee991ea01b8e76082a5f4b8c389
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321856"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="f3aba-102">SendMail 自定义活动</span><span class="sxs-lookup"><span data-stu-id="f3aba-102">SendMail Custom Activity</span></span>
<span data-ttu-id="f3aba-103">本示例演示如何创建派生自 <xref:System.Activities.AsyncCodeActivity> 的自定义活动，以使用 SMTP 发送邮件供在工作流应用程序内使用。</span><span class="sxs-lookup"><span data-stu-id="f3aba-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="f3aba-104">自定义活动使用的功能的<xref:System.Net.Mail.SmtpClient>以异步方式发送电子邮件以及发送身份验证的邮件。</span><span class="sxs-lookup"><span data-stu-id="f3aba-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="f3aba-105">它还提供一些最终用户功能，例如测试模式、标记替换、文件模板和测试放置路径。</span><span class="sxs-lookup"><span data-stu-id="f3aba-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="f3aba-106">下表详细描述了 `SendMail` 活动的自变量。</span><span class="sxs-lookup"><span data-stu-id="f3aba-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="f3aba-107">名称</span><span class="sxs-lookup"><span data-stu-id="f3aba-107">Name</span></span>|<span data-ttu-id="f3aba-108">类型</span><span class="sxs-lookup"><span data-stu-id="f3aba-108">Type</span></span>|<span data-ttu-id="f3aba-109">描述</span><span class="sxs-lookup"><span data-stu-id="f3aba-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f3aba-110">Host</span><span class="sxs-lookup"><span data-stu-id="f3aba-110">Host</span></span>|<span data-ttu-id="f3aba-111">String</span><span class="sxs-lookup"><span data-stu-id="f3aba-111">String</span></span>|<span data-ttu-id="f3aba-112">SMTP 服务器主机的地址。</span><span class="sxs-lookup"><span data-stu-id="f3aba-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="f3aba-113">端口</span><span class="sxs-lookup"><span data-stu-id="f3aba-113">Port</span></span>|<span data-ttu-id="f3aba-114">String</span><span class="sxs-lookup"><span data-stu-id="f3aba-114">String</span></span>|<span data-ttu-id="f3aba-115">主机中 SMTP 服务的端口。</span><span class="sxs-lookup"><span data-stu-id="f3aba-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="f3aba-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="f3aba-116">EnableSsl</span></span>|<span data-ttu-id="f3aba-117">bool</span><span class="sxs-lookup"><span data-stu-id="f3aba-117">bool</span></span>|<span data-ttu-id="f3aba-118">指定 <xref:System.Net.Mail.SmtpClient> 是否使用安全套接字层 (SSL) 来对连接进行加密。</span><span class="sxs-lookup"><span data-stu-id="f3aba-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="f3aba-119">UserName</span><span class="sxs-lookup"><span data-stu-id="f3aba-119">UserName</span></span>|<span data-ttu-id="f3aba-120">String</span><span class="sxs-lookup"><span data-stu-id="f3aba-120">String</span></span>|<span data-ttu-id="f3aba-121">设置用于验证发件人 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 属性的凭据的用户名。</span><span class="sxs-lookup"><span data-stu-id="f3aba-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="f3aba-122">Password</span><span class="sxs-lookup"><span data-stu-id="f3aba-122">Password</span></span>|<span data-ttu-id="f3aba-123">String</span><span class="sxs-lookup"><span data-stu-id="f3aba-123">String</span></span>|<span data-ttu-id="f3aba-124">设置用于验证发件人 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 属性的凭据的密码。</span><span class="sxs-lookup"><span data-stu-id="f3aba-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="f3aba-125">Subject</span><span class="sxs-lookup"><span data-stu-id="f3aba-125">Subject</span></span>|<span data-ttu-id="f3aba-126"><xref:System.Activities.InArgument%601>\<string></span><span class="sxs-lookup"><span data-stu-id="f3aba-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="f3aba-127">邮件主题。</span><span class="sxs-lookup"><span data-stu-id="f3aba-127">Subject of the message.</span></span>|  
|<span data-ttu-id="f3aba-128">正文</span><span class="sxs-lookup"><span data-stu-id="f3aba-128">Body</span></span>|<span data-ttu-id="f3aba-129"><xref:System.Activities.InArgument%601>\<string></span><span class="sxs-lookup"><span data-stu-id="f3aba-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="f3aba-130">邮件正文。</span><span class="sxs-lookup"><span data-stu-id="f3aba-130">Body of the message.</span></span>|  
|<span data-ttu-id="f3aba-131">附件</span><span class="sxs-lookup"><span data-stu-id="f3aba-131">Attachments</span></span>|<span data-ttu-id="f3aba-132"><xref:System.Activities.InArgument%601>\<string></span><span class="sxs-lookup"><span data-stu-id="f3aba-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="f3aba-133">用于存储数据附加到此电子邮件的附件集合。</span><span class="sxs-lookup"><span data-stu-id="f3aba-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="f3aba-134">From</span><span class="sxs-lookup"><span data-stu-id="f3aba-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="f3aba-135">来自此电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="f3aba-135">From address for this email message.</span></span>|  
|<span data-ttu-id="f3aba-136">功能</span><span class="sxs-lookup"><span data-stu-id="f3aba-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="f3aba-137">包含此电子邮件的收件人的地址集合。</span><span class="sxs-lookup"><span data-stu-id="f3aba-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="f3aba-138">CC</span><span class="sxs-lookup"><span data-stu-id="f3aba-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="f3aba-139">地址包含此电子邮件的抄送 (CC) 收件人的集合。</span><span class="sxs-lookup"><span data-stu-id="f3aba-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="f3aba-140">BCC</span><span class="sxs-lookup"><span data-stu-id="f3aba-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="f3aba-141">包含此电子邮件的密件抄送 (BCC) 收件人的地址集合。</span><span class="sxs-lookup"><span data-stu-id="f3aba-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="f3aba-142">标记</span><span class="sxs-lookup"><span data-stu-id="f3aba-142">Tokens</span></span>|<span data-ttu-id="f3aba-143"><xref:System.Activities.InArgument%601>< IDictionary\<字符串、 字符串 >></span><span class="sxs-lookup"><span data-stu-id="f3aba-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="f3aba-144">会在正文中进行替换的标记。</span><span class="sxs-lookup"><span data-stu-id="f3aba-144">Tokens to replace in the body.</span></span> <span data-ttu-id="f3aba-145">此功能允许用户在正文中指定一些值，这些值稍后可由使用此属性提供的标记进行替换。</span><span class="sxs-lookup"><span data-stu-id="f3aba-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="f3aba-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="f3aba-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="f3aba-147">String</span><span class="sxs-lookup"><span data-stu-id="f3aba-147">String</span></span>|<span data-ttu-id="f3aba-148">正文模板的路径。</span><span class="sxs-lookup"><span data-stu-id="f3aba-148">Path of a template for the body.</span></span> <span data-ttu-id="f3aba-149">`SendMail` 活动将此文件的内容复制到其 body 属性中。</span><span class="sxs-lookup"><span data-stu-id="f3aba-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="f3aba-150">此模板可包含由 tokens 属性的内容替换的标记。</span><span class="sxs-lookup"><span data-stu-id="f3aba-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="f3aba-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="f3aba-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="f3aba-152">当设置此属性时，所有电子邮件发送到在其中指定的地址。</span><span class="sxs-lookup"><span data-stu-id="f3aba-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="f3aba-153">此属性应在测试工作流时使用。</span><span class="sxs-lookup"><span data-stu-id="f3aba-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="f3aba-154">例如，如果想要确保不将它们发送到实际收件人的情况下发送所有电子邮件。</span><span class="sxs-lookup"><span data-stu-id="f3aba-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="f3aba-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="f3aba-155">TestDropPath</span></span>|<span data-ttu-id="f3aba-156">String</span><span class="sxs-lookup"><span data-stu-id="f3aba-156">String</span></span>|<span data-ttu-id="f3aba-157">如果设置此属性，还会在指定的文件中保存所有电子邮件。</span><span class="sxs-lookup"><span data-stu-id="f3aba-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="f3aba-158">此属性应在测试或调试工作流，以确保为相应的格式和内容的传出电子邮件时使用。</span><span class="sxs-lookup"><span data-stu-id="f3aba-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="f3aba-159">解决方案内容</span><span class="sxs-lookup"><span data-stu-id="f3aba-159">Solution Contents</span></span>  
 <span data-ttu-id="f3aba-160">解决方案包含两个项目。</span><span class="sxs-lookup"><span data-stu-id="f3aba-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="f3aba-161">项目</span><span class="sxs-lookup"><span data-stu-id="f3aba-161">Project</span></span>|<span data-ttu-id="f3aba-162">描述</span><span class="sxs-lookup"><span data-stu-id="f3aba-162">Description</span></span>|<span data-ttu-id="f3aba-163">重要文件</span><span class="sxs-lookup"><span data-stu-id="f3aba-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="f3aba-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="f3aba-164">SendMail</span></span>|<span data-ttu-id="f3aba-165">SendMail 活动</span><span class="sxs-lookup"><span data-stu-id="f3aba-165">The SendMail activity</span></span>|<span data-ttu-id="f3aba-166">1.SendMail.cs：主要活动的实现</span><span class="sxs-lookup"><span data-stu-id="f3aba-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="f3aba-167">2.SendMailDesigner.xaml 和 SendMailDesigner.xaml.cs：SendMail 活动的设计器</span><span class="sxs-lookup"><span data-stu-id="f3aba-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="f3aba-168">3.MailTemplateBody.htm：要发出的电子邮件的模板。</span><span class="sxs-lookup"><span data-stu-id="f3aba-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="f3aba-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="f3aba-169">SendMailTestClient</span></span>|<span data-ttu-id="f3aba-170">测试 SendMail 活动的客户端。</span><span class="sxs-lookup"><span data-stu-id="f3aba-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="f3aba-171">此项目演示两种调用 SendMail 活动的方式：声明方式和编程方式。</span><span class="sxs-lookup"><span data-stu-id="f3aba-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="f3aba-172">1.Sequence1.xaml：调用 SendMail 活动的工作流。</span><span class="sxs-lookup"><span data-stu-id="f3aba-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="f3aba-173">2.Program.cs：调用 Sequence1，并以编程方式创建使用 SendMail 的工作流。</span><span class="sxs-lookup"><span data-stu-id="f3aba-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="f3aba-174">SendMail 活动的进一步配置</span><span class="sxs-lookup"><span data-stu-id="f3aba-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="f3aba-175">虽然在此示例中未显示，但用户可以执行 SendMail 活动的其他配置。</span><span class="sxs-lookup"><span data-stu-id="f3aba-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="f3aba-176">以下三部分演示如何完成此操作。</span><span class="sxs-lookup"><span data-stu-id="f3aba-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="f3aba-177">使用正文中指定的标记发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="f3aba-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="f3aba-178">此代码段演示如何使用正文中的标记发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="f3aba-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="f3aba-179">注意在 body 属性中提供标记的方式。</span><span class="sxs-lookup"><span data-stu-id="f3aba-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="f3aba-180">将以下标记的值提供给 tokens 属性。</span><span class="sxs-lookup"><span data-stu-id="f3aba-180">Values for those tokens are provided to the tokens property.</span></span>  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="f3aba-181">使用模板发送电子邮件</span><span class="sxs-lookup"><span data-stu-id="f3aba-181">Sending an email using a template</span></span>  
 <span data-ttu-id="f3aba-182">此代码段演示如何使用正文中的模板标记发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="f3aba-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="f3aba-183">请注意，设置 `BodyTemplateFilePath` 属性时，不需要提供 Body 属性的值（模板文件的内容将复制到正文）。</span><span class="sxs-lookup"><span data-stu-id="f3aba-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="f3aba-184">在测试模式下发送电子邮件</span><span class="sxs-lookup"><span data-stu-id="f3aba-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="f3aba-185">此代码片段演示如何设置两个测试属性： 通过设置`TestMailTo`到所有消息将发送到`john.doe@contoso.con`（而无需考虑的值的收件人、 抄送、 密件抄送）。</span><span class="sxs-lookup"><span data-stu-id="f3aba-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="f3aba-186">通过设置 TestDropPath，所有传出电子邮件还将记录在提供的路径中。</span><span class="sxs-lookup"><span data-stu-id="f3aba-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="f3aba-187">可单独设置这些属性（它们不相关）。</span><span class="sxs-lookup"><span data-stu-id="f3aba-187">These properties can be set independently (they are not related).</span></span>  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a><span data-ttu-id="f3aba-188">设置说明</span><span class="sxs-lookup"><span data-stu-id="f3aba-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="f3aba-189">此示例要求具有对 SMTP 服务器的访问权限。</span><span class="sxs-lookup"><span data-stu-id="f3aba-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="f3aba-190">有关设置 SMTP 服务器的详细信息，请参阅以下链接。</span><span class="sxs-lookup"><span data-stu-id="f3aba-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
-   [<span data-ttu-id="f3aba-191">Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="f3aba-191">Microsoft Technet</span></span>](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [<span data-ttu-id="f3aba-192">配置 SMTP 服务 (IIS 6.0)</span><span class="sxs-lookup"><span data-stu-id="f3aba-192">Configuring the SMTP Service (IIS 6.0)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [<span data-ttu-id="f3aba-193">IIS 7.0:配置 SMTP 电子邮件</span><span class="sxs-lookup"><span data-stu-id="f3aba-193">IIS 7.0: Configure SMTP E-Mail</span></span>](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [<span data-ttu-id="f3aba-194">如何安装 SMTP 服务</span><span class="sxs-lookup"><span data-stu-id="f3aba-194">How to Install the SMTP Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="f3aba-195">可下载第三方提供的 SMTP 模拟器。</span><span class="sxs-lookup"><span data-stu-id="f3aba-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="f3aba-196">运行此示例</span><span class="sxs-lookup"><span data-stu-id="f3aba-196">To run this sample</span></span>  
  
1. <span data-ttu-id="f3aba-197">使用 Visual Studio 2010 打开 SendMail.sln 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="f3aba-197">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="f3aba-198">确保您具有对有效 SMTP 服务器的访问权限。</span><span class="sxs-lookup"><span data-stu-id="f3aba-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="f3aba-199">查看设置说明。</span><span class="sxs-lookup"><span data-stu-id="f3aba-199">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="f3aba-200">使用你的服务器地址，并从 / 向电子邮件地址，请配置该程序。</span><span class="sxs-lookup"><span data-stu-id="f3aba-200">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="f3aba-201">若要正确运行此示例，可能需要在 Program.cs 中和 Sequence.xaml 中配置从 / 向电子邮件地址和 SMTP 服务器的地址的值。</span><span class="sxs-lookup"><span data-stu-id="f3aba-201">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="f3aba-202">您将需要更改这两个位置中的地址，因为程序用两种不同的方式发送邮件。</span><span class="sxs-lookup"><span data-stu-id="f3aba-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="f3aba-203">要生成解决方案，按 Ctrl+Shift+B。</span><span class="sxs-lookup"><span data-stu-id="f3aba-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="f3aba-204">若要运行解决方案，请按 Ctrl+F5。</span><span class="sxs-lookup"><span data-stu-id="f3aba-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f3aba-205">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="f3aba-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f3aba-206">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="f3aba-206">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f3aba-207">如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。</span><span class="sxs-lookup"><span data-stu-id="f3aba-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f3aba-208">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="f3aba-208">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`