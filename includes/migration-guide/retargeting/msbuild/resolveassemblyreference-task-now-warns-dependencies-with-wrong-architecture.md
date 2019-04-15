---
ms.openlocfilehash: 39a329597ef28e002242103a247515d94761676a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234612"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a><span data-ttu-id="18e7c-101">ResolveAssemblyReference 任务现在将对体系结构错误的依赖项发出警告</span><span class="sxs-lookup"><span data-stu-id="18e7c-101">ResolveAssemblyReference task now warns of dependencies with the wrong architecture</span></span>

|   |   |
|---|---|
|<span data-ttu-id="18e7c-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="18e7c-102">Details</span></span>|<span data-ttu-id="18e7c-103">此任务发出警告 MSB3270，它表示引用或任何依赖项不匹配应用程序的体系结构。</span><span class="sxs-lookup"><span data-stu-id="18e7c-103">The task emits a warning, MSB3270, which indicates that a reference or any of its dependencies does not match the app's architecture.</span></span> <span data-ttu-id="18e7c-104">例如，如果使用 <code>AnyCPU</code> 选项编译的应用程序包括 x86 引用，则会发生此情况。</span><span class="sxs-lookup"><span data-stu-id="18e7c-104">For example, this occurs if an app that was compiled with the <code>AnyCPU</code> option includes an x86 reference.</span></span> <span data-ttu-id="18e7c-105">这样的情况可能导致运行时应用失败（在本例中为，如果应用部署为 x64 过程）。</span><span class="sxs-lookup"><span data-stu-id="18e7c-105">Such a scenario could result in an app failure at run time (in this case, if the app is deployed as an x64 process).</span></span>|
|<span data-ttu-id="18e7c-106">建议</span><span class="sxs-lookup"><span data-stu-id="18e7c-106">Suggestion</span></span>|<span data-ttu-id="18e7c-107">有两方面的影响：</span><span class="sxs-lookup"><span data-stu-id="18e7c-107">There are two areas of impact:</span></span><ul><li><span data-ttu-id="18e7c-108">重新编译将生成警告，当应用在以前版本的 MSBuild 下编译时，此类警告未显示。</span><span class="sxs-lookup"><span data-stu-id="18e7c-108">Recompilation generates warnings that did not appear when the app was compiled under a previous version of MSBuild.</span></span> <span data-ttu-id="18e7c-109">但是，由于该警告可标识运行时失败可能的来源，所以应该调查并处理它。</span><span class="sxs-lookup"><span data-stu-id="18e7c-109">However, because the warning identifies a possible source of runtime failure, it should be investigated and addressed.</span></span></li><li><span data-ttu-id="18e7c-110">如果警告被视为错误，则应用将无法进行编译。</span><span class="sxs-lookup"><span data-stu-id="18e7c-110">If warnings are treated as errors, the app will fail to compile.</span></span></li></ul>|
|<span data-ttu-id="18e7c-111">范围</span><span class="sxs-lookup"><span data-stu-id="18e7c-111">Scope</span></span>|<span data-ttu-id="18e7c-112">次要</span><span class="sxs-lookup"><span data-stu-id="18e7c-112">Minor</span></span>|
|<span data-ttu-id="18e7c-113">版本</span><span class="sxs-lookup"><span data-stu-id="18e7c-113">Version</span></span>|<span data-ttu-id="18e7c-114">4.5.1</span><span class="sxs-lookup"><span data-stu-id="18e7c-114">4.5.1</span></span>|
|<span data-ttu-id="18e7c-115">类型</span><span class="sxs-lookup"><span data-stu-id="18e7c-115">Type</span></span>|<span data-ttu-id="18e7c-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="18e7c-116">Retargeting</span></span>|
