---
title: 属性&#39; &lt;attributename&gt; &#39;不能应用多次
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 6609ce299799bc3c4b78d48478e99e4d4101dd72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565158"
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="b1b05-102">属性&#39; &lt;attributename&gt; &#39;不能应用多次</span><span class="sxs-lookup"><span data-stu-id="b1b05-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="b1b05-103">该特性仅应用一次。</span><span class="sxs-lookup"><span data-stu-id="b1b05-103">The attribute can only be applied once.</span></span> <span data-ttu-id="b1b05-104">`AttributeUsage`属性确定是否可以多次应用属性。</span><span class="sxs-lookup"><span data-stu-id="b1b05-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="b1b05-105">**错误 ID:** BC30663</span><span class="sxs-lookup"><span data-stu-id="b1b05-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b1b05-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="b1b05-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b1b05-107">请确保该属性只应用一次。</span><span class="sxs-lookup"><span data-stu-id="b1b05-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="b1b05-108">如果使用的您开发的自定义特性，请考虑更改其`AttributeUsage`属性以允许多个特性用法，与下面的示例一样。</span><span class="sxs-lookup"><span data-stu-id="b1b05-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1b05-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="b1b05-109">See also</span></span>
- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="b1b05-110">创建自定义特性</span><span class="sxs-lookup"><span data-stu-id="b1b05-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="b1b05-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="b1b05-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
