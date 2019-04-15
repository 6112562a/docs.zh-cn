---
ms.openlocfilehash: b4e062fe3a00b76da144e706841f87b2a95888e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234611"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="5855f-101">EncoderParameter ctor 已过时</span><span class="sxs-lookup"><span data-stu-id="5855f-101">EncoderParameter ctor is obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5855f-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="5855f-102">Details</span></span>|<span data-ttu-id="5855f-103"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 构造函数现已过时，使用它将引发生成警告。</span><span class="sxs-lookup"><span data-stu-id="5855f-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>|
|<span data-ttu-id="5855f-104">建议</span><span class="sxs-lookup"><span data-stu-id="5855f-104">Suggestion</span></span>|<span data-ttu-id="5855f-105">虽然 <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 构造函数仍将继续运行，但应改用以下构造函数，以避免在使用 .NET Framework 4.5 工具重新编译代码时出现已过时生成警告：<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>。</span><span class="sxs-lookup"><span data-stu-id="5855f-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>|
|<span data-ttu-id="5855f-106">范围</span><span class="sxs-lookup"><span data-stu-id="5855f-106">Scope</span></span>|<span data-ttu-id="5855f-107">次要</span><span class="sxs-lookup"><span data-stu-id="5855f-107">Minor</span></span>|
|<span data-ttu-id="5855f-108">版本</span><span class="sxs-lookup"><span data-stu-id="5855f-108">Version</span></span>|<span data-ttu-id="5855f-109">4.5</span><span class="sxs-lookup"><span data-stu-id="5855f-109">4.5</span></span>|
|<span data-ttu-id="5855f-110">类型</span><span class="sxs-lookup"><span data-stu-id="5855f-110">Type</span></span>|<span data-ttu-id="5855f-111">重定目标</span><span class="sxs-lookup"><span data-stu-id="5855f-111">Retargeting</span></span>|
|<span data-ttu-id="5855f-112">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="5855f-112">Affected APIs</span></span>|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
