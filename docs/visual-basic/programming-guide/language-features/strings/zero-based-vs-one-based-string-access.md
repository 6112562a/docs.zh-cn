---
title: 从零开始的 vs。在 Visual Basic 中的基于 1 的字符串访问
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: d4b2f73f8955b103e70e240e714e2b31d6198438
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535524"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>从零开始的 vs。在 Visual Basic 中的基于 1 的字符串访问
本主题将比较了 Visual Basic 和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]提供对字符串中字符的访问。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]始终提供了对字符串中字符的从零开始访问权限，而 Visual Basic 提供的从零开始的和基于 1 的访问权限，具体取决于该函数。  
  
## <a name="one-based"></a>基于 1 的  
 对于基于 1 的 Visual Basic 函数的示例，请考虑`Mid`函数。 它采用自变量，指示子字符串开始，从位置 1 开始的字符位置。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType>方法接受的字符的索引子字符串将启动，请在字符串中从位置 0 开始。 因此，如果您有一个字符串"ABCDE"，单个字符进行编号用于 1,2,3,4,5`Mid`函数，但用于 0,1,2,3,4<xref:System.String.Substring%2A?displayProperty=nameWithType>方法。  
  
## <a name="zero-based"></a>从零开始  
 从零开始的 Visual Basic 函数的示例，请考虑`Split`函数。 它将字符串拆分，并返回一个包含子字符串的数组。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType>方法还将字符串拆分，并返回一个包含子字符串的数组。 因为`Split`函数和<xref:System.String.Split%2A>方法将返回[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]的数组，它们必须是从零开始。  
  
## <a name="see-also"></a>请参阅
- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Visual Basic 中的字符串简介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
