---
title: 所有字段宽度（除了最后一个元素外）都必须大于零
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_FieldWidthsMustPositive
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
ms.openlocfilehash: 806dcef7b7a29afa8804a581659023c817662434
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "58024540"
---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a><span data-ttu-id="b787f-102">所有字段宽度（除了最后一个元素外）都必须大于零</span><span class="sxs-lookup"><span data-stu-id="b787f-102">All field widths, except the last element, must be greater than zero</span></span>
<span data-ttu-id="b787f-103">所有字段宽度（除了最后一个元素外）都必须大于零。</span><span class="sxs-lookup"><span data-stu-id="b787f-103">All field widths, except the last element, must be greater than zero.</span></span> <span data-ttu-id="b787f-104">最后一个元素的字段宽度小于或等于零表示最后一个字段的长度是可变的。</span><span class="sxs-lookup"><span data-stu-id="b787f-104">A field width less than or equal to zero in the last element indicates the last field is of variable length.</span></span>  
  
 <span data-ttu-id="b787f-105">操作已失败，因为最后一个元素以外的某个字段宽度被设置为等于或小于零。</span><span class="sxs-lookup"><span data-stu-id="b787f-105">The operation has failed because a field width other than the last element is set to zero or less.</span></span> <span data-ttu-id="b787f-106">可将小于或等于零的字段宽度用作最后一个元素以指示最后一个字段的长度可变，但不能将它用作任何其他元素。</span><span class="sxs-lookup"><span data-stu-id="b787f-106">A field width less than or equal to zero can be used as the last element to indicate that the last field is of variable length, but it cannot be used as any other element.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b787f-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="b787f-107">To correct this error</span></span>  
  
-   <span data-ttu-id="b787f-108">将字段宽度设置为正确的长度。</span><span class="sxs-lookup"><span data-stu-id="b787f-108">Set the field width to the correct length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b787f-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="b787f-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths>
- [<span data-ttu-id="b787f-110">如何：读取固定宽度的文本文件</span><span class="sxs-lookup"><span data-stu-id="b787f-110">How to: Read From Fixed-width Text Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="b787f-111">TextFieldParser 对象</span><span class="sxs-lookup"><span data-stu-id="b787f-111">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
