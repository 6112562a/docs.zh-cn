---
title: 表达式是一个值，因此不能作为赋值目标
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: b2c33cb9ba0479df5e69b6979a789253f9fae565
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597328"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="07724-102">表达式是一个值，因此不能作为赋值目标</span><span class="sxs-lookup"><span data-stu-id="07724-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="07724-103">语句试图将值分配为表达式。</span><span class="sxs-lookup"><span data-stu-id="07724-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="07724-104">您可以在运行时分配到可写的变量、 属性或数组元素的值。</span><span class="sxs-lookup"><span data-stu-id="07724-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="07724-105">下面的示例说明了如何可能出现此错误。</span><span class="sxs-lookup"><span data-stu-id="07724-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="07724-106">相似的示例可以应用于属性和数组元素。</span><span class="sxs-lookup"><span data-stu-id="07724-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="07724-107">**间接访问权限。**</span><span class="sxs-lookup"><span data-stu-id="07724-107">**Indirect Access.**</span></span> <span data-ttu-id="07724-108">通过值类型的间接访问还可以生成此错误。</span><span class="sxs-lookup"><span data-stu-id="07724-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="07724-109">请考虑下面的代码示例，它会尝试设置的值<xref:System.Drawing.Point>通过访问间接通过<xref:System.Windows.Forms.Control.Location%2A>。</span><span class="sxs-lookup"><span data-stu-id="07724-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="07724-110">前面的示例中的最后一个语句失败，因为它将创建的临时分配仅<xref:System.Drawing.Point>返回的结构<xref:System.Windows.Forms.Control.Location%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="07724-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="07724-111">结构是值类型，并运行该语句后不会保留临时结构。</span><span class="sxs-lookup"><span data-stu-id="07724-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="07724-112">通过声明和使用变量中的以解决此问题<xref:System.Windows.Forms.Control.Location%2A>，这将创建的更永久分配<xref:System.Drawing.Point>结构。</span><span class="sxs-lookup"><span data-stu-id="07724-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="07724-113">下面的示例显示了可以替换前面的示例中的最后一个语句的代码。</span><span class="sxs-lookup"><span data-stu-id="07724-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="07724-114">**错误 ID:** BC30068</span><span class="sxs-lookup"><span data-stu-id="07724-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="07724-115">更正此错误</span><span class="sxs-lookup"><span data-stu-id="07724-115">To correct this error</span></span>  
  
-   <span data-ttu-id="07724-116">如果该语句将值分配给一个表达式，用单个可写的变量、 属性或数组元素替换该表达式。</span><span class="sxs-lookup"><span data-stu-id="07724-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="07724-117">如果该语句进行间接访问通过值类型 （通常是结构），创建一个变量来保存值类型。</span><span class="sxs-lookup"><span data-stu-id="07724-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="07724-118">为变量分配相应的结构 （或其他值类型）。</span><span class="sxs-lookup"><span data-stu-id="07724-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="07724-119">使用变量来访问要为其赋值的属性。</span><span class="sxs-lookup"><span data-stu-id="07724-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07724-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="07724-120">See also</span></span>
- [<span data-ttu-id="07724-121">运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="07724-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="07724-122">语句</span><span class="sxs-lookup"><span data-stu-id="07724-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="07724-123">过程疑难解答</span><span class="sxs-lookup"><span data-stu-id="07724-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
