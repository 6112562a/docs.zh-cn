---
ms.openlocfilehash: 72acd0029d0189de1c724856572957f111b9d18f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675881"
---
## <a name="installation-instructions"></a><span data-ttu-id="83b0f-101">安装说明</span><span class="sxs-lookup"><span data-stu-id="83b0f-101">Installation instructions</span></span> 

<span data-ttu-id="83b0f-102">在“Visual Studio 安装程序”中查找“.NET Compiler Platform SDK”有两种不同的方法：</span><span class="sxs-lookup"><span data-stu-id="83b0f-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-workloads-view"></a><span data-ttu-id="83b0f-103">使用“工作负荷”视图进行安装</span><span class="sxs-lookup"><span data-stu-id="83b0f-103">Install using the Workloads view</span></span>

<span data-ttu-id="83b0f-104">Visual Studio 扩展开发工作负荷中不会自动选择 .NET Compiler Platform SDK。</span><span class="sxs-lookup"><span data-stu-id="83b0f-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="83b0f-105">必须将其作为可选组件进行选择。</span><span class="sxs-lookup"><span data-stu-id="83b0f-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="83b0f-106">运行“Visual Studio 安装程序”</span><span class="sxs-lookup"><span data-stu-id="83b0f-106">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="83b0f-107">选择“修改”</span><span class="sxs-lookup"><span data-stu-id="83b0f-107">Select **Modify**</span></span> 
1. <span data-ttu-id="83b0f-108">检查“Visual Studio 扩展开发”工作负荷。</span><span class="sxs-lookup"><span data-stu-id="83b0f-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="83b0f-109">在摘要树中打开“Visual Studio 扩展开发”节点。</span><span class="sxs-lookup"><span data-stu-id="83b0f-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="83b0f-110">选中“.NET Compiler Platform SDK”框。</span><span class="sxs-lookup"><span data-stu-id="83b0f-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="83b0f-111">将在可选组件最下面找到它。</span><span class="sxs-lookup"><span data-stu-id="83b0f-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="83b0f-112">还可使“DGML 编辑器”在可视化工具中显示关系图：</span><span class="sxs-lookup"><span data-stu-id="83b0f-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="83b0f-113">在摘要树中打开“单个组件”节点。</span><span class="sxs-lookup"><span data-stu-id="83b0f-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="83b0f-114">选中“DGML 编辑器”框</span><span class="sxs-lookup"><span data-stu-id="83b0f-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-individual-components-tab"></a><span data-ttu-id="83b0f-115">使用“单个组件”选项卡进行安装</span><span class="sxs-lookup"><span data-stu-id="83b0f-115">Install using the Individual components tab</span></span>

1. <span data-ttu-id="83b0f-116">运行“Visual Studio 安装程序”</span><span class="sxs-lookup"><span data-stu-id="83b0f-116">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="83b0f-117">选择“修改”</span><span class="sxs-lookup"><span data-stu-id="83b0f-117">Select **Modify**</span></span> 
1. <span data-ttu-id="83b0f-118">选择“单个组件”选项卡</span><span class="sxs-lookup"><span data-stu-id="83b0f-118">Select the **Individual components** tab</span></span> 
1. <span data-ttu-id="83b0f-119">选中“.NET Compiler Platform SDK”框。</span><span class="sxs-lookup"><span data-stu-id="83b0f-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="83b0f-120">将在“编译器、生成工具和运行时”部分最上方找到它。</span><span class="sxs-lookup"><span data-stu-id="83b0f-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="83b0f-121">还可使“DGML 编辑器”在可视化工具中显示关系图：</span><span class="sxs-lookup"><span data-stu-id="83b0f-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="83b0f-122">选中“DGML 编辑器”框。</span><span class="sxs-lookup"><span data-stu-id="83b0f-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="83b0f-123">将在“代码工具”部分下找到它。</span><span class="sxs-lookup"><span data-stu-id="83b0f-123">You'll find it under the **Code tools** section.</span></span>
