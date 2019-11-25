---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 62f70ae7f40fa3cde9492563b7bd14dfa5940a5f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352246"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="3427a-101">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3427a-101">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="3427a-102">Specifies the return value of the property or function.</span><span class="sxs-lookup"><span data-stu-id="3427a-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3427a-103">语法</span><span class="sxs-lookup"><span data-stu-id="3427a-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3427a-104">参数</span><span class="sxs-lookup"><span data-stu-id="3427a-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="3427a-105">返回值的说明。</span><span class="sxs-lookup"><span data-stu-id="3427a-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3427a-106">备注</span><span class="sxs-lookup"><span data-stu-id="3427a-106">Remarks</span></span>  
 <span data-ttu-id="3427a-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span><span class="sxs-lookup"><span data-stu-id="3427a-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="3427a-108">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="3427a-108">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3427a-109">示例</span><span class="sxs-lookup"><span data-stu-id="3427a-109">Example</span></span>  
 <span data-ttu-id="3427a-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span><span class="sxs-lookup"><span data-stu-id="3427a-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3427a-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="3427a-111">See also</span></span>

- [<span data-ttu-id="3427a-112">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="3427a-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
