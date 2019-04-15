---
ms.openlocfilehash: 3cd5052dffcb059c240a310e0b89384f28409264
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234356"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="e7689-101">在启用触摸的系统上调用 System.Windows.Input.PenContext.Disable 可能会引发 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="e7689-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e7689-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="e7689-102">Details</span></span>|<span data-ttu-id="e7689-103">在某些情况下，在启用触摸的系统上调用内部 <strong>System.Windows.Intput.PenContext.Disable</strong> 方法可能会因为重新进入而引发未处理的 <code>T:System.ArgumentException</code>。</span><span class="sxs-lookup"><span data-stu-id="e7689-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="e7689-104">建议</span><span class="sxs-lookup"><span data-stu-id="e7689-104">Suggestion</span></span>|<span data-ttu-id="e7689-105">此问题已在 .NET Framework 4.7 中得到解决。</span><span class="sxs-lookup"><span data-stu-id="e7689-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="e7689-106">若要避免此异常，升级到 .NET Framework 4.7 及以上版本。</span><span class="sxs-lookup"><span data-stu-id="e7689-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="e7689-107">范围</span><span class="sxs-lookup"><span data-stu-id="e7689-107">Scope</span></span>|<span data-ttu-id="e7689-108">边缘</span><span class="sxs-lookup"><span data-stu-id="e7689-108">Edge</span></span>|
|<span data-ttu-id="e7689-109">版本</span><span class="sxs-lookup"><span data-stu-id="e7689-109">Version</span></span>|<span data-ttu-id="e7689-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="e7689-110">4.6.1</span></span>|
|<span data-ttu-id="e7689-111">类型</span><span class="sxs-lookup"><span data-stu-id="e7689-111">Type</span></span>|<span data-ttu-id="e7689-112">重定目标</span><span class="sxs-lookup"><span data-stu-id="e7689-112">Retargeting</span></span>|
