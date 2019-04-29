---
title: 下载 JSON Web 标记处理程序包
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: 8f878d23afd76488de7da03f16f72cbfa43c17d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792744"
---
# <a name="download-the-json-web-token-handler-package"></a><span data-ttu-id="5f641-102">下载 JSON Web 令牌处理程序包</span><span class="sxs-lookup"><span data-stu-id="5f641-102">Download the JSON Web Token Handler Package</span></span>

<span data-ttu-id="5f641-103">本主题讨论了如何在项目中下载和使用 JSON Web 令牌处理程序。</span><span class="sxs-lookup"><span data-stu-id="5f641-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>

<span data-ttu-id="5f641-104">JSON Web 令牌处理程序扩展可用作 NuGet 程序包，可将必要程序集和引用添加到项目。</span><span class="sxs-lookup"><span data-stu-id="5f641-104">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="5f641-105">如果尚未安装 NuGet，请转到 [nuget.org](https://nuget.org) 进行安装。</span><span class="sxs-lookup"><span data-stu-id="5f641-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="5f641-106">可以通过在 NuGet 上访问其页面看到扩展的版本控制历史记录：[JSON Web 令牌处理程序 NuGet 上](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="5f641-106">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="5f641-107">使用程序包管理器 GUI</span><span class="sxs-lookup"><span data-stu-id="5f641-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="5f641-108">在 Visual Studio 中，在解决方案资源管理器中右键单击项目，然后选择“管理 NuGet 包”。</span><span class="sxs-lookup"><span data-stu-id="5f641-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="5f641-109">在“管理 NuGet 包”窗口中，单击搜索框并输入 `JWT Token Handler`，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="5f641-109">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>

3. <span data-ttu-id="5f641-110">单击结果窗格中第一个结果的“安装”按钮。</span><span class="sxs-lookup"><span data-stu-id="5f641-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="5f641-111">将开始下载包。</span><span class="sxs-lookup"><span data-stu-id="5f641-111">The package will begin downloading.</span></span> <span data-ttu-id="5f641-112">将包添加到项目前，会出现“许可证接受”对话框。</span><span class="sxs-lookup"><span data-stu-id="5f641-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="5f641-113">如果同意许可条款，请单击“我接受”。</span><span class="sxs-lookup"><span data-stu-id="5f641-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="5f641-114">将下载最新的 JSON Web 令牌处理程序程序集并添加到项目。</span><span class="sxs-lookup"><span data-stu-id="5f641-114">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="5f641-115">使用包管理器控制台</span><span class="sxs-lookup"><span data-stu-id="5f641-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="5f641-116">在 Visual Studio 中，单击**工具** > **NuGet 包管理器** > **程序包管理器控制台**。</span><span class="sxs-lookup"><span data-stu-id="5f641-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="5f641-117">随即出现“包管理器控制台”。</span><span class="sxs-lookup"><span data-stu-id="5f641-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="5f641-118">输入以下文本并按 Enter：</span><span class="sxs-lookup"><span data-stu-id="5f641-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. <span data-ttu-id="5f641-119">将下载最新的 JSON Web 令牌处理程序程序集并添加到项目。</span><span class="sxs-lookup"><span data-stu-id="5f641-119">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>