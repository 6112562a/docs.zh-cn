---
title: 类型化数据集
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 92ed3f8fd392238785fd2d205668f14fe477f2b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098645"
---
# <a name="typed-datasets"></a><span data-ttu-id="97784-102">类型化数据集</span><span class="sxs-lookup"><span data-stu-id="97784-102">Typed DataSets</span></span>
<span data-ttu-id="97784-103">在允许通过弱类型化变量对值进行后期绑定访问的同时，<xref:System.Data.DataSet> 还允许通过强类型化比喻对数据进行访问。</span><span class="sxs-lookup"><span data-stu-id="97784-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="97784-104">表和列的一部分**数据集**可以使用用户友好的名称来访问和强类型化变量。</span><span class="sxs-lookup"><span data-stu-id="97784-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="97784-105">类型化**数据集**是派生一个类**数据集**。</span><span class="sxs-lookup"><span data-stu-id="97784-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="97784-106">在这种情况下，它将继承所有方法、 事件和属性的**数据集**。</span><span class="sxs-lookup"><span data-stu-id="97784-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="97784-107">此外，类型化**数据集**提供强类型的方法、 事件和属性。</span><span class="sxs-lookup"><span data-stu-id="97784-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="97784-108">这意味着可以按名称（而不是使用基于集合的方法）访问表和列。</span><span class="sxs-lookup"><span data-stu-id="97784-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="97784-109">除了改进的类型化的代码可读性**数据集**还允许 Visual Studio.NET 代码编辑器中键入时自动完成的行。</span><span class="sxs-lookup"><span data-stu-id="97784-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="97784-110">此外，强类型**数据集**提供对正确类型在编译时对值的访问。</span><span class="sxs-lookup"><span data-stu-id="97784-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="97784-111">使用强类型化**数据集**，当代码是编译而不是在运行时捕获类型不匹配错误。</span><span class="sxs-lookup"><span data-stu-id="97784-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97784-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="97784-112">In This Section</span></span>  
 [<span data-ttu-id="97784-113">生成强类型化数据集</span><span class="sxs-lookup"><span data-stu-id="97784-113">Generating Strongly Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 <span data-ttu-id="97784-114">介绍如何创建和使用强类型化**数据集**。</span><span class="sxs-lookup"><span data-stu-id="97784-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="97784-115">为类型化的数据集进行注释</span><span class="sxs-lookup"><span data-stu-id="97784-115">Annotating Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 <span data-ttu-id="97784-116">描述如何批注 XML 架构定义语言 (XSD) 架构用于生成强类型化**数据集**，以便**数据集**元素友好的名称，而无需更改基础架构。</span><span class="sxs-lookup"><span data-stu-id="97784-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97784-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="97784-117">See also</span></span>

- [<span data-ttu-id="97784-118">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="97784-118">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="97784-119">ADO.NET 托管提供程序和数据集开发人员中心</span><span class="sxs-lookup"><span data-stu-id="97784-119">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
