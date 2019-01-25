---
title: 通过使用分部方法添加业务逻辑
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: 082994085a3cbb9a229ae6c6eea30f15b796fc20
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543930"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="a25c4-102">通过使用分部方法添加业务逻辑</span><span class="sxs-lookup"><span data-stu-id="a25c4-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="a25c4-103">你可以自定义 Visual Basic 和C#生成的代码中的您[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]通过使用项目*分部方法*。</span><span class="sxs-lookup"><span data-stu-id="a25c4-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="a25c4-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 生成的代码定义签名作为分部方法的一部分。</span><span class="sxs-lookup"><span data-stu-id="a25c4-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="a25c4-105">如果您要实现此方法，您可以添加自己的分部方法。</span><span class="sxs-lookup"><span data-stu-id="a25c4-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="a25c4-106">如果您不添加自己的实现，编译器将丢弃分部方法签名并调用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的默认方法。</span><span class="sxs-lookup"><span data-stu-id="a25c4-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a25c4-107">如果使用的 Visual Studio，则可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]向实体类添加验证及其他自定义项。</span><span class="sxs-lookup"><span data-stu-id="a25c4-107">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="a25c4-108">例如，Northwind 示例数据库中 `Customer` 类的默认映射包括下面的分部方法：</span><span class="sxs-lookup"><span data-stu-id="a25c4-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="a25c4-109">你可以向自己的分部 `Customer` 类添加诸如以下内容的代码来实现自己的方法。</span><span class="sxs-lookup"><span data-stu-id="a25c4-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="a25c4-110">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中通常使用这种方式来重写 `Insert`、`Update`、`Delete` 的默认方法以及在对象生命周期事件过程中验证属性。</span><span class="sxs-lookup"><span data-stu-id="a25c4-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="a25c4-111">有关详细信息，请参阅[分部方法](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)(Visual Basic) 或[分部 （方法） (C#引用)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#)。</span><span class="sxs-lookup"><span data-stu-id="a25c4-111">For more information, see [Partial Methods](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a25c4-112">示例</span><span class="sxs-lookup"><span data-stu-id="a25c4-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a25c4-113">描述</span><span class="sxs-lookup"><span data-stu-id="a25c4-113">Description</span></span>  
 <span data-ttu-id="a25c4-114">下面的示例首先显示了 `ExampleClass`，因为它可能是由像 SQLMetal 这样的代码生成工具定义的；然后，此示例演示了如何只实现两个方法之一。</span><span class="sxs-lookup"><span data-stu-id="a25c4-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a25c4-115">代码</span><span class="sxs-lookup"><span data-stu-id="a25c4-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="a25c4-116">示例</span><span class="sxs-lookup"><span data-stu-id="a25c4-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a25c4-117">描述</span><span class="sxs-lookup"><span data-stu-id="a25c4-117">Description</span></span>  
 <span data-ttu-id="a25c4-118">下面的示例用到了 `Shipper` 和 `Order` 实体之间的关系。</span><span class="sxs-lookup"><span data-stu-id="a25c4-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="a25c4-119">请注意这些方法中的分部方法 `InsertShipper` 和 `DeleteShipper`。</span><span class="sxs-lookup"><span data-stu-id="a25c4-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="a25c4-120">这些方法重写了由 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 映射提供的默认分部方法。</span><span class="sxs-lookup"><span data-stu-id="a25c4-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a25c4-121">代码</span><span class="sxs-lookup"><span data-stu-id="a25c4-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a25c4-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="a25c4-122">See also</span></span>
- [<span data-ttu-id="a25c4-123">进行和提交数据更改</span><span class="sxs-lookup"><span data-stu-id="a25c4-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="a25c4-124">自定义插入、更新和删除操作</span><span class="sxs-lookup"><span data-stu-id="a25c4-124">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
