---
title: 平台调用示例
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
ms.openlocfilehash: 358d1ce662d56b8c31124f4b3264ec25a0f94586
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181317"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="6ad6b-102">平台调用示例</span><span class="sxs-lookup"><span data-stu-id="6ad6b-102">Platform Invoke Examples</span></span>
<span data-ttu-id="6ad6b-103">以下示例演示如何定义和调用 User32.dll 中的 MessageBox 函数，并将简单字符串作为参数传递。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6ad6b-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="6ad6b-104">在这些示例中，<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> 字段设置为 Auto，以让目标平台确定字符宽度和字符串封送处理。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6ad6b-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="6ad6b-105">有关其他示例，请参阅[通过平台调用封送处理数据](marshaling-data-with-platform-invoke.md)。</span><span class="sxs-lookup"><span data-stu-id="6ad6b-105">For additional examples, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad6b-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ad6b-106">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="6ad6b-107">在托管代码中创建原型</span><span class="sxs-lookup"><span data-stu-id="6ad6b-107">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="6ad6b-108">指定字符集</span><span class="sxs-lookup"><span data-stu-id="6ad6b-108">Specifying a Character Set</span></span>](specifying-a-character-set.md)
