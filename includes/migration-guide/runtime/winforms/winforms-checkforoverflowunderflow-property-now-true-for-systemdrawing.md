---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803374"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="4ba52-101">对于 System.Drawing，WinForm 的 CheckForOverflowUnderflow 属性现在为 true</span><span class="sxs-lookup"><span data-stu-id="4ba52-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4ba52-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="4ba52-102">Details</span></span>|<span data-ttu-id="4ba52-103">System.Drawing.dll 程序集的 CheckForOverflowUnderflow 设置为 true。</span><span class="sxs-lookup"><span data-stu-id="4ba52-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="4ba52-104">建议</span><span class="sxs-lookup"><span data-stu-id="4ba52-104">Suggestion</span></span>|<span data-ttu-id="4ba52-105">之前在发生溢出时，结果会在不提示的情况下被截断。</span><span class="sxs-lookup"><span data-stu-id="4ba52-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="4ba52-106">现在引发了 <xref:System.OverflowException?displayProperty=name> 异常。</span><span class="sxs-lookup"><span data-stu-id="4ba52-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="4ba52-107">范围</span><span class="sxs-lookup"><span data-stu-id="4ba52-107">Scope</span></span>|<span data-ttu-id="4ba52-108">边缘</span><span class="sxs-lookup"><span data-stu-id="4ba52-108">Edge</span></span>|
|<span data-ttu-id="4ba52-109">版本</span><span class="sxs-lookup"><span data-stu-id="4ba52-109">Version</span></span>|<span data-ttu-id="4ba52-110">4.5</span><span class="sxs-lookup"><span data-stu-id="4ba52-110">4.5</span></span>|
|<span data-ttu-id="4ba52-111">类型</span><span class="sxs-lookup"><span data-stu-id="4ba52-111">Type</span></span>|<span data-ttu-id="4ba52-112">运行时</span><span class="sxs-lookup"><span data-stu-id="4ba52-112">Runtime</span></span>|
