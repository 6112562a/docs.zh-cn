---
title: 如何：使用 WIF 显示登录状态
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: d2500c6ded485fca76715425b9a52258e07be08d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851567"
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="6fb03-102">如何：使用 WIF 显示登录状态</span><span class="sxs-lookup"><span data-stu-id="6fb03-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="6fb03-103">适用于</span><span class="sxs-lookup"><span data-stu-id="6fb03-103">Applies To</span></span>  
  
- <span data-ttu-id="6fb03-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span><span class="sxs-lookup"><span data-stu-id="6fb03-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
- <span data-ttu-id="6fb03-105">ASP.NET® Web 窗体</span><span class="sxs-lookup"><span data-stu-id="6fb03-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="6fb03-106">总结</span><span class="sxs-lookup"><span data-stu-id="6fb03-106">Summary</span></span>  
 <span data-ttu-id="6fb03-107">本主题介绍如何在已启用 WIF 的 ASP.NET 应用程序中显示登录状态。</span><span class="sxs-lookup"><span data-stu-id="6fb03-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="6fb03-108">WIF 提供的机制可使应用程序声明感知、管理应用程序资源的身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="6fb03-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="6fb03-109">内容</span><span class="sxs-lookup"><span data-stu-id="6fb03-109">Contents</span></span>  
  
- <span data-ttu-id="6fb03-110">概述</span><span class="sxs-lookup"><span data-stu-id="6fb03-110">Overview</span></span>  
  
- <span data-ttu-id="6fb03-111">步骤摘要</span><span class="sxs-lookup"><span data-stu-id="6fb03-111">Summary of Steps</span></span>  
  
- <span data-ttu-id="6fb03-112">步骤 1 – 安装标识和访问扩展</span><span class="sxs-lookup"><span data-stu-id="6fb03-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="6fb03-113">步骤 2 – 创建信赖方 ASP.NET 应用程序</span><span class="sxs-lookup"><span data-stu-id="6fb03-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="6fb03-114">步骤 3 – 启用本地开发 STS 以验证用户身份</span><span class="sxs-lookup"><span data-stu-id="6fb03-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="6fb03-115">步骤 4 – 修改 ASP.NET 应用程序以显示登录状态</span><span class="sxs-lookup"><span data-stu-id="6fb03-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="6fb03-116">步骤 5 - 测试 WIF 和 ASP.NET 应用程序之间的集成</span><span class="sxs-lookup"><span data-stu-id="6fb03-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="6fb03-117">概述</span><span class="sxs-lookup"><span data-stu-id="6fb03-117">Overview</span></span>  
 <span data-ttu-id="6fb03-118">本主题演示如何使用 WIF 创建简单的声明感知应用程序，以及如何轻松显示用户是否已登录。</span><span class="sxs-lookup"><span data-stu-id="6fb03-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="6fb03-119">以下步骤使用的本地开发 STS 包含在标识和访问 Visual Studio 扩展中。</span><span class="sxs-lookup"><span data-stu-id="6fb03-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="6fb03-120">本地开发 STS 专门用于测试和开发环境，提供一种简单的方法将声明集成到应用程序中。</span><span class="sxs-lookup"><span data-stu-id="6fb03-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="6fb03-121">它不可用于生产环境，因为它不执行实际的身份验证，也不需要凭据。</span><span class="sxs-lookup"><span data-stu-id="6fb03-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="6fb03-122">但以下步骤中的指令性代码与使用实际身份验证的生产就绪应用程序的相同。</span><span class="sxs-lookup"><span data-stu-id="6fb03-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="6fb03-123">步骤摘要</span><span class="sxs-lookup"><span data-stu-id="6fb03-123">Summary of Steps</span></span>  
  
- <span data-ttu-id="6fb03-124">步骤 1 – 安装标识和访问扩展</span><span class="sxs-lookup"><span data-stu-id="6fb03-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="6fb03-125">步骤 2 – 创建信赖方 ASP.NET 应用程序</span><span class="sxs-lookup"><span data-stu-id="6fb03-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="6fb03-126">步骤 3 – 启用本地开发 STS 以验证用户身份</span><span class="sxs-lookup"><span data-stu-id="6fb03-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="6fb03-127">步骤 4 – 修改 ASP.NET 应用程序以显示登录状态</span><span class="sxs-lookup"><span data-stu-id="6fb03-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="6fb03-128">步骤 5 - 测试 WIF 和 ASP.NET 应用程序之间的集成</span><span class="sxs-lookup"><span data-stu-id="6fb03-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="6fb03-129">步骤 1 – 安装标识和访问扩展</span><span class="sxs-lookup"><span data-stu-id="6fb03-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="6fb03-130">此步骤介绍如何为 Visual Studio 2012 配置标识和访问扩展。</span><span class="sxs-lookup"><span data-stu-id="6fb03-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="6fb03-131">此扩展会自动启动配置应用程序过程，以与 STS 终结点进行通信。</span><span class="sxs-lookup"><span data-stu-id="6fb03-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="6fb03-132">安装标识和访问扩展</span><span class="sxs-lookup"><span data-stu-id="6fb03-132">To install the Identity and Access extension</span></span>  
  
1. <span data-ttu-id="6fb03-133">以管理员身份在提升模式下启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="6fb03-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2. <span data-ttu-id="6fb03-134">在 Visual Studio 中，单击“工具”，然后单击“展开管理器”。</span><span class="sxs-lookup"><span data-stu-id="6fb03-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="6fb03-135">此时将打开“扩展管理器”窗口。</span><span class="sxs-lookup"><span data-stu-id="6fb03-135">The **Extension Manager** window appears.</span></span>  
  
3. <span data-ttu-id="6fb03-136">在“扩展管理器”中，单击左侧菜单中的“联机扩展”，然后选择“Visual Studio 库”。</span><span class="sxs-lookup"><span data-stu-id="6fb03-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4. <span data-ttu-id="6fb03-137">在“扩展管理器”的右上角，搜索“标识和访问”。</span><span class="sxs-lookup"><span data-stu-id="6fb03-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5. <span data-ttu-id="6fb03-138">此时将在搜索结果中显示“标识和访问”项。</span><span class="sxs-lookup"><span data-stu-id="6fb03-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="6fb03-139">单击该项，然后单击“下载”。</span><span class="sxs-lookup"><span data-stu-id="6fb03-139">Click it, and then click **Download**.</span></span>  
  
6. <span data-ttu-id="6fb03-140">此时将打开“下载并安装”对话框。</span><span class="sxs-lookup"><span data-stu-id="6fb03-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="6fb03-141">如果同意许可条款，请单击“安装”。</span><span class="sxs-lookup"><span data-stu-id="6fb03-141">If you agree with the license terms, click **Install**.</span></span>  
  
7. <span data-ttu-id="6fb03-142">“标识和访问”扩展安装完成后，在管理员模式下重启 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="6fb03-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="6fb03-143">步骤 2 – 创建信赖方 ASP.NET 应用程序</span><span class="sxs-lookup"><span data-stu-id="6fb03-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="6fb03-144">此步骤介绍如何创建与 WIF 集成的信赖方 ASP.NET Web 窗体应用程序。</span><span class="sxs-lookup"><span data-stu-id="6fb03-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="6fb03-145">创建一个简单 ASP.NET 应用程序</span><span class="sxs-lookup"><span data-stu-id="6fb03-145">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="6fb03-146">启动 Visual Studio，然后依次单击“文件”、“新建”和“项目”。</span><span class="sxs-lookup"><span data-stu-id="6fb03-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="6fb03-147">在“新建项目”窗口中，单击“ASP.NET Web 窗体应用程序”。</span><span class="sxs-lookup"><span data-stu-id="6fb03-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="6fb03-148">在“名称”中，输入 `TestApp`，然后按“确定”。</span><span class="sxs-lookup"><span data-stu-id="6fb03-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="6fb03-149">步骤 3 – 启用本地开发 STS 以验证用户身份</span><span class="sxs-lookup"><span data-stu-id="6fb03-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="6fb03-150">此步骤介绍如何在应用程序中启用本地开发 STS。</span><span class="sxs-lookup"><span data-stu-id="6fb03-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="6fb03-151">使用 Visual Studio 的标识和访问扩展可启用本地开发 STS。</span><span class="sxs-lookup"><span data-stu-id="6fb03-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="6fb03-152">在 ASP.NET 应用程序中启用本地开发 STS</span><span class="sxs-lookup"><span data-stu-id="6fb03-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1. <span data-ttu-id="6fb03-153">在 Visual Studio 中，右键单击“解决方案资源管理器”下的“TestApp”项目，然后选择“标识和访问”。</span><span class="sxs-lookup"><span data-stu-id="6fb03-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2. <span data-ttu-id="6fb03-154">“标识和访问”窗口随即出现。</span><span class="sxs-lookup"><span data-stu-id="6fb03-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="6fb03-155">在“提供程序”下，选择“使用本地开发 STS 测试应用程序”，然后单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="6fb03-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="6fb03-156">步骤 4 – 修改 ASP.NET 应用程序以显示登录状态</span><span class="sxs-lookup"><span data-stu-id="6fb03-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="6fb03-157">此步骤介绍如何修改 ASP.NET 应用程序，以动态显示当前用户是否已登录。</span><span class="sxs-lookup"><span data-stu-id="6fb03-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="6fb03-158">配置 STS 提供程序后，WIF 将处理传入的声明。</span><span class="sxs-lookup"><span data-stu-id="6fb03-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="6fb03-159">现在，需要配置应用程序代码，以显示身份验证的结果。</span><span class="sxs-lookup"><span data-stu-id="6fb03-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
### <a name="to-display-sign-in-status"></a><span data-ttu-id="6fb03-160">显示登录状态</span><span class="sxs-lookup"><span data-stu-id="6fb03-160">To display sign in status</span></span>  
  
1. <span data-ttu-id="6fb03-161">在 Visual Studio 中，打开“Default.aspx”文件下的“TestApp”项目。</span><span class="sxs-lookup"><span data-stu-id="6fb03-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2. <span data-ttu-id="6fb03-162">在“Default.aspx”文件中，将现有标记替换为以下标记：</span><span class="sxs-lookup"><span data-stu-id="6fb03-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
    ```aspx-csharp  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3. <span data-ttu-id="6fb03-163">保存 Default.aspx 文件，然后打开名为 Default.aspx.cs 的代码隐藏文件。</span><span class="sxs-lookup"><span data-stu-id="6fb03-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6fb03-164">在解决方案资源管理器中，Default.aspx.cs 文件可能隐藏在 Default.aspx 文件下。</span><span class="sxs-lookup"><span data-stu-id="6fb03-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="6fb03-165">如果 Default.aspx.cs 文件不可见，请单击文件旁边的三角形，展开 Default.aspx。</span><span class="sxs-lookup"><span data-stu-id="6fb03-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4. <span data-ttu-id="6fb03-166">在 Default.aspx 文件中，将现有代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="6fb03-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5. <span data-ttu-id="6fb03-167">保存 Default.aspx.cs，并生成该应用程序。</span><span class="sxs-lookup"><span data-stu-id="6fb03-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="6fb03-168">步骤 5 - 测试 WIF 和 ASP.NET 应用程序之间的集成</span><span class="sxs-lookup"><span data-stu-id="6fb03-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="6fb03-169">此步骤介绍如何测试 WIF 和 ASP.NET 应用程序之间的集成。</span><span class="sxs-lookup"><span data-stu-id="6fb03-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="6fb03-170">测试 WIF 和 ASP.NET 之间的集成</span><span class="sxs-lookup"><span data-stu-id="6fb03-170">To test the integration between WIF and ASP.NET</span></span>  
  
1. <span data-ttu-id="6fb03-171">在 Visual Studio 中，按“F5”开始调试应用程序。</span><span class="sxs-lookup"><span data-stu-id="6fb03-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="6fb03-172">如果未发现任何错误，将打开一个新的浏览器窗口。</span><span class="sxs-lookup"><span data-stu-id="6fb03-172">If no errors are found, a new browser window will open.</span></span>  
  
2. <span data-ttu-id="6fb03-173">你可能会注意到，浏览器会以无提示方式将请求重定向到 STS，然后打开 Default.aspx 页。</span><span class="sxs-lookup"><span data-stu-id="6fb03-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="6fb03-174">如果 WIF 配置正确，则会看到站点显示以下文本： **"您已登录"** 。</span><span class="sxs-lookup"><span data-stu-id="6fb03-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
