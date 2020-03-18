---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803203"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="77010-101">分析 ASP.Net MVC4 应用可能导致严重的执行引擎错误</span><span class="sxs-lookup"><span data-stu-id="77010-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="77010-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="77010-102">Details</span></span>|<span data-ttu-id="77010-103">使用 NGEN /Profile 程序集的探查器可能会在启动时使已配置的 ASP.NET MVC4 应用程序出故障，引发“严重的执行引擎异常”</span><span class="sxs-lookup"><span data-stu-id="77010-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="77010-104">建议</span><span class="sxs-lookup"><span data-stu-id="77010-104">Suggestion</span></span>|<span data-ttu-id="77010-105">此问题已在 .NET Framework 4.5.2 中解决。</span><span class="sxs-lookup"><span data-stu-id="77010-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="77010-106">或者，探查器可通过在其事件掩码中指定 <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> 来避免此问题。</span><span class="sxs-lookup"><span data-stu-id="77010-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="77010-107">范围</span><span class="sxs-lookup"><span data-stu-id="77010-107">Scope</span></span>|<span data-ttu-id="77010-108">边缘</span><span class="sxs-lookup"><span data-stu-id="77010-108">Edge</span></span>|
|<span data-ttu-id="77010-109">Version</span><span class="sxs-lookup"><span data-stu-id="77010-109">Version</span></span>|<span data-ttu-id="77010-110">4.5</span><span class="sxs-lookup"><span data-stu-id="77010-110">4.5</span></span>|
|<span data-ttu-id="77010-111">类型</span><span class="sxs-lookup"><span data-stu-id="77010-111">Type</span></span>|<span data-ttu-id="77010-112">运行时</span><span class="sxs-lookup"><span data-stu-id="77010-112">Runtime</span></span>|
