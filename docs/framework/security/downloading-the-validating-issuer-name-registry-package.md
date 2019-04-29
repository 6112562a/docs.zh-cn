---
title: 下载验证颁发者名称注册表包
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 833a0722fdd27df4e488ed7fac99444c6d9b8905
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940577"
---
# <a name="download-the-validating-issuer-name-registry-package"></a><span data-ttu-id="9a4b6-102">下载验证颁发者名称注册表包</span><span class="sxs-lookup"><span data-stu-id="9a4b6-102">Download the Validating Issuer Name Registry Package</span></span>

<span data-ttu-id="9a4b6-103">本主题讨论如何在项目中下载和使用验证颁发者名称注册表 (VINR)。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>

<span data-ttu-id="9a4b6-104">VINR 可用作 NuGet 包，可将必要程序集和引用添加到项目。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-104">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="9a4b6-105">如果尚未安装 NuGet，请转到 [nuget.org](https://nuget.org) 进行安装。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="9a4b6-106">可以通过在 NuGet 上访问其页面看到扩展的版本控制历史记录：[Microsoft 验证 NuGet 上的颁发者名称注册表](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span><span class="sxs-lookup"><span data-stu-id="9a4b6-106">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="9a4b6-107">使用程序包管理器 GUI</span><span class="sxs-lookup"><span data-stu-id="9a4b6-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="9a4b6-108">在 Visual Studio 中，在解决方案资源管理器中右键单击项目，然后选择“管理 NuGet 包”。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="9a4b6-109">在“管理 NuGet 包”窗口中，单击搜索框并输入 `ValidatingIssuerNameRegistry`，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-109">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>

3. <span data-ttu-id="9a4b6-110">单击结果窗格中第一个结果的“安装”按钮。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="9a4b6-111">将开始下载包。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-111">The package will begin downloading.</span></span> <span data-ttu-id="9a4b6-112">将包添加到项目前，会出现“许可证接受”对话框。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="9a4b6-113">如果同意许可条款，请单击“我接受”。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="9a4b6-114">将下载并添加最新 VINR 程序集到项目。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-114">The latest VINR assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="9a4b6-115">使用包管理器控制台</span><span class="sxs-lookup"><span data-stu-id="9a4b6-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="9a4b6-116">在 Visual Studio 中，单击**工具** > **NuGet 包管理器** > **程序包管理器控制台**。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="9a4b6-117">随即出现“包管理器控制台”。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="9a4b6-118">输入以下文本并按 Enter：</span><span class="sxs-lookup"><span data-stu-id="9a4b6-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. <span data-ttu-id="9a4b6-119">将下载并添加最新 VINR 程序集到项目。</span><span class="sxs-lookup"><span data-stu-id="9a4b6-119">The latest VINR assemblies will be downloaded and added to your project.</span></span>