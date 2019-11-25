---
title: Error 语句
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 668ffbc7b8db73a706c5771bb0734a77f8fc0206
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351235"
---
# <a name="error-statement"></a><span data-ttu-id="bb736-102">Error 语句</span><span class="sxs-lookup"><span data-stu-id="bb736-102">Error Statement</span></span>
<span data-ttu-id="bb736-103">Simulates the occurrence of an error.</span><span class="sxs-lookup"><span data-stu-id="bb736-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb736-104">语法</span><span class="sxs-lookup"><span data-stu-id="bb736-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="bb736-105">部件</span><span class="sxs-lookup"><span data-stu-id="bb736-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="bb736-106">必须的。</span><span class="sxs-lookup"><span data-stu-id="bb736-106">Required.</span></span> <span data-ttu-id="bb736-107">Can be any valid error number.</span><span class="sxs-lookup"><span data-stu-id="bb736-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb736-108">备注</span><span class="sxs-lookup"><span data-stu-id="bb736-108">Remarks</span></span>  
 <span data-ttu-id="bb736-109">The `Error` statement is supported for backward compatibility.</span><span class="sxs-lookup"><span data-stu-id="bb736-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="bb736-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span><span class="sxs-lookup"><span data-stu-id="bb736-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="bb736-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span><span class="sxs-lookup"><span data-stu-id="bb736-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="bb736-112">Property</span><span class="sxs-lookup"><span data-stu-id="bb736-112">Property</span></span>|<span data-ttu-id="bb736-113">“值”</span><span class="sxs-lookup"><span data-stu-id="bb736-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="bb736-114">Value specified as argument to `Error` statement.</span><span class="sxs-lookup"><span data-stu-id="bb736-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="bb736-115">Can be any valid error number.</span><span class="sxs-lookup"><span data-stu-id="bb736-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="bb736-116">Name of the current Visual Basic project.</span><span class="sxs-lookup"><span data-stu-id="bb736-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="bb736-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span><span class="sxs-lookup"><span data-stu-id="bb736-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="bb736-118">If the string does not exist, `Description` contains a zero-length string ("").</span><span class="sxs-lookup"><span data-stu-id="bb736-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="bb736-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span><span class="sxs-lookup"><span data-stu-id="bb736-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="bb736-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span><span class="sxs-lookup"><span data-stu-id="bb736-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="bb736-121">Zero.</span><span class="sxs-lookup"><span data-stu-id="bb736-121">Zero.</span></span>|  
  
 <span data-ttu-id="bb736-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span><span class="sxs-lookup"><span data-stu-id="bb736-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb736-123">Some Visual Basic host applications cannot create objects.</span><span class="sxs-lookup"><span data-stu-id="bb736-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="bb736-124">See your host application's documentation to determine whether it can create classes and objects.</span><span class="sxs-lookup"><span data-stu-id="bb736-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb736-125">示例</span><span class="sxs-lookup"><span data-stu-id="bb736-125">Example</span></span>  
 <span data-ttu-id="bb736-126">This example uses the `Error` statement to generate error number 11.</span><span class="sxs-lookup"><span data-stu-id="bb736-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="bb736-127">要求</span><span class="sxs-lookup"><span data-stu-id="bb736-127">Requirements</span></span>  
 <span data-ttu-id="bb736-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="bb736-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="bb736-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="bb736-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb736-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="bb736-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="bb736-131">On Error 语句</span><span class="sxs-lookup"><span data-stu-id="bb736-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="bb736-132">Resume 语句</span><span class="sxs-lookup"><span data-stu-id="bb736-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="bb736-133">错误消息</span><span class="sxs-lookup"><span data-stu-id="bb736-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
