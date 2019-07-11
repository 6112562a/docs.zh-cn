---
title: 层次结构支持
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 576fa896364d603f2cdbb7b6532e3efc3cd6f674
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743070"
---
# <a name="inheritance-support"></a><span data-ttu-id="c2ad2-102">层次结构支持</span><span class="sxs-lookup"><span data-stu-id="c2ad2-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c2ad2-103">支持*单表映射*。</span><span class="sxs-lookup"><span data-stu-id="c2ad2-103">supports *single-table mapping*.</span></span> <span data-ttu-id="c2ad2-104">换言之，整个继承层次结构存储在单个数据库表中。</span><span class="sxs-lookup"><span data-stu-id="c2ad2-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="c2ad2-105">该表包含整个层次结构的所有可能数据列的平展联合。</span><span class="sxs-lookup"><span data-stu-id="c2ad2-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="c2ad2-106">（联合是将两个表组合成一个表的结果，组合后的表包含任一原始表中存在的行。）每行中不适用于该行所表示的实例类型的列为 null。</span><span class="sxs-lookup"><span data-stu-id="c2ad2-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="c2ad2-107">单表映射策略是最简单的继承表示形式，为许多不同类别的查询提供了良好的性能特征。</span><span class="sxs-lookup"><span data-stu-id="c2ad2-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="c2ad2-108">若要在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中实现这种映射，必须在继承层次结构的根类中指定属性 (Attribute) 和属性 (Attribute) 的属性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="c2ad2-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="c2ad2-109">有关详细信息，请参阅[如何：映射继承层次结构](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="c2ad2-109">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="c2ad2-110">使用 Visual Studio 的开发人员还可以使用对象关系设计器来映射继承层次结构。</span><span class="sxs-lookup"><span data-stu-id="c2ad2-110">Developers using Visual Studio can also use the Object Relational Designer to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ad2-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="c2ad2-111">See also</span></span>

- [<span data-ttu-id="c2ad2-112">背景信息</span><span class="sxs-lookup"><span data-stu-id="c2ad2-112">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
