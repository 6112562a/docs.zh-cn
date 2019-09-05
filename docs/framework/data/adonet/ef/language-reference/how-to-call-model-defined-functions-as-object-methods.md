---
title: 如何：调用模型定义的函数作为对象方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
ms.openlocfilehash: 787ead2c52f874af2ca1a02bf009da40cee875ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250772"
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a><span data-ttu-id="aa1e6-102">如何：调用模型定义的函数作为对象方法</span><span class="sxs-lookup"><span data-stu-id="aa1e6-102">How to: Call Model-Defined Functions as Object Methods</span></span>
<span data-ttu-id="aa1e6-103">本主题介绍如何将模型定义函数作为 <xref:System.Data.Objects.ObjectContext> 对象的方法调用或作为自定义类的静态方法调用。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-103">This topic describes how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object or as a static method on a custom class.</span></span> <span data-ttu-id="aa1e6-104">*模型定义的函数*是在概念模型中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-104">A *model-defined function* is a function that is defined in the conceptual model.</span></span> <span data-ttu-id="aa1e6-105">本主题中的过程介绍如何直接调用这些函数，而不是从 LINQ to Entities 查询中调用它们。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-105">The procedures in the topic describe how to call these functions directly instead of calling them from LINQ to Entities queries.</span></span> <span data-ttu-id="aa1e6-106">有关在 LINQ to Entities 查询中调用模型定义函数的信息，请[参阅如何：在查询](how-to-call-model-defined-functions-in-queries.md)中调用模型定义的函数。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-106">For information about calling model-defined functions in LINQ to Entities queries, see [How to: Call Model-Defined Functions in Queries](how-to-call-model-defined-functions-in-queries.md).</span></span>  
  
 <span data-ttu-id="aa1e6-107">无论您是将模型定义函数作为 <xref:System.Data.Objects.ObjectContext> 方法调用，还是作为自定义类的静态方法调用，首先都必须使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 将该方法映射到模型定义函数。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-107">Whether you call a model-defined function as an <xref:System.Data.Objects.ObjectContext> method or as a static method on a custom class, you must first map the method to the model-defined function with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="aa1e6-108">但是，当您定义 <xref:System.Data.Objects.ObjectContext> 类的方法时，必须使用 <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> 属性公开 LINQ 提供程序，而当您定义自定义类的静态方法时，必须使用 <xref:System.Linq.IQueryable.Provider%2A> 属性公开 LINQ 提供程序。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-108">However, when you define a method on the <xref:System.Data.Objects.ObjectContext> class, you must use the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property to expose the LINQ provider, whereas when you define a static method on a custom class, you must use the <xref:System.Linq.IQueryable.Provider%2A> property to expose the LINQ provider.</span></span> <span data-ttu-id="aa1e6-109">有关更多信息，请参见下述过程后面的示例。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-109">For more information, see the examples that follow the procedures below.</span></span>  
  
 <span data-ttu-id="aa1e6-110">下面的这些过程高度概括了将模型定义函数作为 <xref:System.Data.Objects.ObjectContext> 对象的方法调用和作为自定义类的静态方法调用的信息。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-110">The procedures below provide high-level outlines for calling a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object and as a static method on a custom class.</span></span> <span data-ttu-id="aa1e6-111">后面的示例提供了有关这些过程中各个步骤的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-111">The examples that follow provide more detail about the steps in the procedures.</span></span> <span data-ttu-id="aa1e6-112">这些过程假定您在概念模型中定义了一个函数。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-112">The procedures assume that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="aa1e6-113">有关详细信息，请参阅[如何：在概念模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))中定义自定义函数。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-113">For more information, see [How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span></span>  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a><span data-ttu-id="aa1e6-114">将模型定义函数作为 ObjectContext 对象的方法调用</span><span class="sxs-lookup"><span data-stu-id="aa1e6-114">To call a model-defined function as a method on an ObjectContext object</span></span>  
  
1. <span data-ttu-id="aa1e6-115">添加一个源文件，以扩展派生自 <xref:System.Data.Objects.ObjectContext> 类（该类由实体框架工具自动生成）的分部类。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-115">Add a source file to extend the partial class derived from the <xref:System.Data.Objects.ObjectContext> class, auto-generated by the Entity Framework tools.</span></span> <span data-ttu-id="aa1e6-116">在单独的源文件中定义 CLR 存根可防止在重新生成文件时丢失所做的更改。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-116">Defining the CLR stub in a separate source file will prevent the changes from being lost when the file is regenerated.</span></span>  
  
2. <span data-ttu-id="aa1e6-117">将一个公共语言运行时 (CLR) 方法添加到 <xref:System.Data.Objects.ObjectContext> 类，该方法可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="aa1e6-117">Add a common language runtime (CLR) method to your <xref:System.Data.Objects.ObjectContext> class that does the following:</span></span>  
  
    - <span data-ttu-id="aa1e6-118">映射到在概念模型中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-118">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="aa1e6-119">若要映射方法，必须将 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 应用于此方法。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-119">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="aa1e6-120">请注意，此特性的 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> 和 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> 参数分别是概念模型的命名空间名称和概念模型中的函数名称。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-120">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span> <span data-ttu-id="aa1e6-121">LINQ 的函数名称解析区分大小写。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-121">Function name resolution for LINQ is case sensitive.</span></span>  
  
    - <span data-ttu-id="aa1e6-122">返回由 <xref:System.Linq.IQueryProvider.Execute%2A> 属性返回的 <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> 方法的结果。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-122">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property.</span></span>  
  
3. <span data-ttu-id="aa1e6-123">将此方法作为 <xref:System.Data.Objects.ObjectContext> 类的实例的一个成员调用。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-123">Call the method as a member on an instance of the <xref:System.Data.Objects.ObjectContext> class.</span></span>  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a><span data-ttu-id="aa1e6-124">将模型定义函数作为自定义类的静态方法调用</span><span class="sxs-lookup"><span data-stu-id="aa1e6-124">To call a model-defined function as static method on a custom class</span></span>  
  
1. <span data-ttu-id="aa1e6-125">向应用程序添加一个类，该类带有一个静态方法，可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="aa1e6-125">Add a class to your application with a static method that does the following:</span></span>  
  
    - <span data-ttu-id="aa1e6-126">映射到在概念模型中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-126">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="aa1e6-127">若要映射方法，必须将 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 应用于此方法。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-127">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="aa1e6-128">请注意，此特性的 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> 和 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> 参数分别是概念模型的命名空间名称和概念模型中的函数名称。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-128">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span>  
  
    - <span data-ttu-id="aa1e6-129">接受 <xref:System.Linq.IQueryable> 自变量。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-129">Accepts an <xref:System.Linq.IQueryable> argument.</span></span>  
  
    - <span data-ttu-id="aa1e6-130">返回由 <xref:System.Linq.IQueryProvider.Execute%2A> 属性返回的 <xref:System.Linq.IQueryable.Provider%2A> 方法的结果。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-130">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Linq.IQueryable.Provider%2A> property.</span></span>  
  
2. <span data-ttu-id="aa1e6-131">将此方法作为自定义类的一个静态成员调用</span><span class="sxs-lookup"><span data-stu-id="aa1e6-131">Call the method as a member a static method on the custom class</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa1e6-132">示例</span><span class="sxs-lookup"><span data-stu-id="aa1e6-132">Example</span></span>  
 <span data-ttu-id="aa1e6-133">**在 ObjectContext 对象上调用模型定义函数作为方法**</span><span class="sxs-lookup"><span data-stu-id="aa1e6-133">**Calling a Model-Defined Function as a Method on an ObjectContext Object**</span></span>  
  
 <span data-ttu-id="aa1e6-134">下面的示例演示如何将模型定义函数作为 <xref:System.Data.Objects.ObjectContext> 对象的一个方法调用。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-134">The following example demonstrates how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object.</span></span> <span data-ttu-id="aa1e6-135">该示例使用[AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-135">The example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
 <span data-ttu-id="aa1e6-136">请考虑下面的概念模型函数，它可返回指定产品的产品收入。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-136">Consider the conceptual model function below that returns product revenue for a specified product.</span></span> <span data-ttu-id="aa1e6-137">（有关向概念模型添加函数的信息，请参阅[如何：在概念模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))中定义自定义函数。）</span><span class="sxs-lookup"><span data-stu-id="aa1e6-137">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a><span data-ttu-id="aa1e6-138">示例</span><span class="sxs-lookup"><span data-stu-id="aa1e6-138">Example</span></span>  
 <span data-ttu-id="aa1e6-139">下面的代码向 `AdventureWorksEntities` 类添加了一个方法，该方法映射到上述的概念模型函数。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-139">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="aa1e6-140">示例</span><span class="sxs-lookup"><span data-stu-id="aa1e6-140">Example</span></span>  
 <span data-ttu-id="aa1e6-141">下面的代码调用上面的方法，以显示指定产品的产品收入：</span><span class="sxs-lookup"><span data-stu-id="aa1e6-141">The following code calls the method above to display the product revenue for a specified product:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="aa1e6-142">示例</span><span class="sxs-lookup"><span data-stu-id="aa1e6-142">Example</span></span>  
 <span data-ttu-id="aa1e6-143">下面的示例演示如何调用一个返回集合（作为 <xref:System.Linq.IQueryable%601> 对象）的模型定义函数。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-143">The following example demonstrates how to call a model-defined function that returns a collection (as an <xref:System.Linq.IQueryable%601> object).</span></span> <span data-ttu-id="aa1e6-144">请考虑下面的概念模型函数，它可返回给定产品 ID 的所有 `SalesOrderDetails`。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-144">Consider the conceptual model function below that returns all the `SalesOrderDetails` for a given product ID.</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a><span data-ttu-id="aa1e6-145">示例</span><span class="sxs-lookup"><span data-stu-id="aa1e6-145">Example</span></span>  
 <span data-ttu-id="aa1e6-146">下面的代码向 `AdventureWorksEntities` 类添加了一个方法，该方法映射到上述的概念模型函数。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-146">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="aa1e6-147">示例</span><span class="sxs-lookup"><span data-stu-id="aa1e6-147">Example</span></span>  
 <span data-ttu-id="aa1e6-148">下面的代码示例调用此方法。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-148">The following code calls the method.</span></span> <span data-ttu-id="aa1e6-149">请注意，返回的 <xref:System.Linq.IQueryable%601> 查询将进一步优化，以返回每个 `SalesOrderDetail` 的行合计。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-149">Note that the returned <xref:System.Linq.IQueryable%601> query is further refined to return line totals for each `SalesOrderDetail`.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="aa1e6-150">示例</span><span class="sxs-lookup"><span data-stu-id="aa1e6-150">Example</span></span>  
 <span data-ttu-id="aa1e6-151">**将模型定义函数作为自定义类的静态方法调用**</span><span class="sxs-lookup"><span data-stu-id="aa1e6-151">**Calling a Model-Defined Function as a Static Method on a Custom Class**</span></span>  
  
 <span data-ttu-id="aa1e6-152">下一个示例演示如何将模型定义函数作为自定义类的静态方法调用。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-152">The next example demonstrates how to call a model-defined function as a static method on a custom class.</span></span> <span data-ttu-id="aa1e6-153">该示例使用[AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-153">The example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa1e6-154">当您将模型定义函数作为自定义类的静态方法调用时，此模型定义函数必须接受集合且在集合中返回值的聚合。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-154">When you call a model-defined function as a static method on a custom class, the model-defined function must accept a collection and return an aggregation of values in the collection.</span></span>  
  
 <span data-ttu-id="aa1e6-155">请考虑下面的概念模型函数，它可返回 SalesOrderDetail 集合的产品收入。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-155">Consider the conceptual model function below that returns product revenue for a SalesOrderDetail collection.</span></span> <span data-ttu-id="aa1e6-156">（有关向概念模型添加函数的信息，请参阅[如何：在概念模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))中定义自定义函数。）</span><span class="sxs-lookup"><span data-stu-id="aa1e6-156">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).).</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="aa1e6-157">示例</span><span class="sxs-lookup"><span data-stu-id="aa1e6-157">Example</span></span>  
 <span data-ttu-id="aa1e6-158">下面的代码向应用程序添加了一个类，该类包含一个映射到上述概念模型函数的静态方法。</span><span class="sxs-lookup"><span data-stu-id="aa1e6-158">The following code adds a class to your application that contains a static method that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="aa1e6-159">示例</span><span class="sxs-lookup"><span data-stu-id="aa1e6-159">Example</span></span>  
 <span data-ttu-id="aa1e6-160">下面的代码调用上面的方法，以显示指定 SalesOrderDetail 集合的产品收入：</span><span class="sxs-lookup"><span data-stu-id="aa1e6-160">The following code calls the method above to display the product revenue for a SalesOrderDetail collection:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="aa1e6-161">请参阅</span><span class="sxs-lookup"><span data-stu-id="aa1e6-161">See also</span></span>

- <span data-ttu-id="aa1e6-162">[.edmx 文件概述](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="aa1e6-162">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="aa1e6-163">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="aa1e6-163">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="aa1e6-164">在 LINQ to Entities 查询中调用函数</span><span class="sxs-lookup"><span data-stu-id="aa1e6-164">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
