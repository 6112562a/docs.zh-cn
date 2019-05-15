---
title: 如何：在 Visual Basic 中检查连接状态
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 1a03b181c2e363c3380c4f9858b629713641f2c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620673"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="2763e-102">如何：在 Visual Basic 中检查连接状态</span><span class="sxs-lookup"><span data-stu-id="2763e-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="2763e-103"><xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> 属性可用于确定计算机是否具有有效的网络连接或 Internet 连接。</span><span class="sxs-lookup"><span data-stu-id="2763e-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="2763e-104">检查计算机是否具有有效的网络连接</span><span class="sxs-lookup"><span data-stu-id="2763e-104">To check whether a computer has a working connection</span></span>  
  
- <span data-ttu-id="2763e-105">确定 `IsAvailable` 属性是 `True` 还是 `False`。</span><span class="sxs-lookup"><span data-stu-id="2763e-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="2763e-106">以下代码检查属性的状态并进行报告：</span><span class="sxs-lookup"><span data-stu-id="2763e-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="2763e-107">此代码示例也可作为 IntelliSense 代码片段。</span><span class="sxs-lookup"><span data-stu-id="2763e-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="2763e-108">它位于代码片段选取器的“连接和网络”中。</span><span class="sxs-lookup"><span data-stu-id="2763e-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="2763e-109">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="2763e-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2763e-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="2763e-110">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
