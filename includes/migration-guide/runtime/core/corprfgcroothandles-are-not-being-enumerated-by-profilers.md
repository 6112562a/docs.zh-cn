---
ms.openlocfilehash: 8dc98b2d9c2c0b5f145ebce48cf8f5e054975c6e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858394"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="d3c2d-101">探查器未枚举 COR_PRF_GC_ROOT_HANDLEs</span><span class="sxs-lookup"><span data-stu-id="d3c2d-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d3c2d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="d3c2d-102">Details</span></span>|<span data-ttu-id="d3c2d-103">在 .NET Framework v4.5.1 中，分析 API <code>RootReferences2()</code> 错误地不会返回 <code>COR_PRF_GC_ROOT_HANDLE</code>（而是返回 <code>COR_PRF_GC_ROOT_OTHER</code>）。</span><span class="sxs-lookup"><span data-stu-id="d3c2d-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="d3c2d-104">此问题已从 .NET Framework 4.6 开始修复。</span><span class="sxs-lookup"><span data-stu-id="d3c2d-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="d3c2d-105">建议</span><span class="sxs-lookup"><span data-stu-id="d3c2d-105">Suggestion</span></span>|<span data-ttu-id="d3c2d-106">此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="d3c2d-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="d3c2d-107">范围</span><span class="sxs-lookup"><span data-stu-id="d3c2d-107">Scope</span></span>|<span data-ttu-id="d3c2d-108">次要</span><span class="sxs-lookup"><span data-stu-id="d3c2d-108">Minor</span></span>|
|<span data-ttu-id="d3c2d-109">版本</span><span class="sxs-lookup"><span data-stu-id="d3c2d-109">Version</span></span>|<span data-ttu-id="d3c2d-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d3c2d-110">4.5.1</span></span>|
|<span data-ttu-id="d3c2d-111">类型</span><span class="sxs-lookup"><span data-stu-id="d3c2d-111">Type</span></span>|<span data-ttu-id="d3c2d-112">运行时</span><span class="sxs-lookup"><span data-stu-id="d3c2d-112">Runtime</span></span>|

