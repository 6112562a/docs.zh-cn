---
title: XML 注释异常必须具有&#39;cref&#39;属性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 0f276781165e80b2d869da2518dbe34b33085d5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649942"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="098e1-102">XML 注释异常必须具有&#39;cref&#39;属性</span><span class="sxs-lookup"><span data-stu-id="098e1-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="098e1-103">\<异常 > 标记提供了一种方法来记录方法可能引发的异常。</span><span class="sxs-lookup"><span data-stu-id="098e1-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="098e1-104">所需`cref`特性将指定的成员，它由文档生成器检查名称。</span><span class="sxs-lookup"><span data-stu-id="098e1-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="098e1-105">如果存在该成员，它被转换为文档文件中的规范的元素名称。</span><span class="sxs-lookup"><span data-stu-id="098e1-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="098e1-106">**错误 ID:** BC42319</span><span class="sxs-lookup"><span data-stu-id="098e1-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="098e1-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="098e1-107">To correct this error</span></span>  
  
-   <span data-ttu-id="098e1-108">添加`cref`属性为异常，如下所示：</span><span class="sxs-lookup"><span data-stu-id="098e1-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="098e1-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="098e1-109">See also</span></span>
- [<span data-ttu-id="098e1-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="098e1-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="098e1-111">如何：创建 XML 文档</span><span class="sxs-lookup"><span data-stu-id="098e1-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="098e1-112">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="098e1-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
