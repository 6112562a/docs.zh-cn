---
title: 推断元素文本
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: d457985bfbec924748d1a418e318609b6837b9d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745143"
---
# <a name="inferring-element-text"></a><span data-ttu-id="6cf07-102">推断元素文本</span><span class="sxs-lookup"><span data-stu-id="6cf07-102">Inferring Element Text</span></span>
<span data-ttu-id="6cf07-103">如果元素包含文本但不包含任何子元素被推断为表 （具有属性的元素） 或重复的元素，例如具有名称的新列**TableName_Text**将添加到为该元素推断的表。</span><span class="sxs-lookup"><span data-stu-id="6cf07-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="6cf07-104">该元素中包含的文本将添加到此表中的一行，并存储在新列中。</span><span class="sxs-lookup"><span data-stu-id="6cf07-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="6cf07-105">**ColumnMapping**的新列的属性将设置为**MappingType.SimpleContent**。</span><span class="sxs-lookup"><span data-stu-id="6cf07-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="6cf07-106">例如，考虑以下 XML。</span><span class="sxs-lookup"><span data-stu-id="6cf07-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="6cf07-107">推断过程将生成名为的表**Element1**包含两个列： **attr1**并**Element1_Text**。</span><span class="sxs-lookup"><span data-stu-id="6cf07-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="6cf07-108">**ColumnMapping**的属性**attr1**列将设置为**MappingType.Attribute**。</span><span class="sxs-lookup"><span data-stu-id="6cf07-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="6cf07-109">**ColumnMapping**的属性**Element1_Text**列将设置为**MappingType.SimpleContent**。</span><span class="sxs-lookup"><span data-stu-id="6cf07-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="6cf07-110">**数据集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="6cf07-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="6cf07-111">**表：** Element1</span><span class="sxs-lookup"><span data-stu-id="6cf07-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="6cf07-112">attr1</span><span class="sxs-lookup"><span data-stu-id="6cf07-112">attr1</span></span>|<span data-ttu-id="6cf07-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="6cf07-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="6cf07-114">value1</span><span class="sxs-lookup"><span data-stu-id="6cf07-114">value1</span></span>|<span data-ttu-id="6cf07-115">Text1</span><span class="sxs-lookup"><span data-stu-id="6cf07-115">Text1</span></span>|  
  
 <span data-ttu-id="6cf07-116">如果某元素包含文本，并且还具有包含文本的子元素，则不会将列添加到表中来存储该元素所包含的文本。</span><span class="sxs-lookup"><span data-stu-id="6cf07-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="6cf07-117">该元素中包含的文本将被忽略，但子元素中的文本将包含在表的一行中。</span><span class="sxs-lookup"><span data-stu-id="6cf07-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="6cf07-118">例如，考虑以下 XML。</span><span class="sxs-lookup"><span data-stu-id="6cf07-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="6cf07-119">推断过程将生成名为的表**Element1**具有一个名为的列**ChildElement1**。</span><span class="sxs-lookup"><span data-stu-id="6cf07-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="6cf07-120">文本**ChildElement1**元素将包含在表中的行。</span><span class="sxs-lookup"><span data-stu-id="6cf07-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="6cf07-121">其他文本则将被忽略。</span><span class="sxs-lookup"><span data-stu-id="6cf07-121">The other text will be ignored.</span></span> <span data-ttu-id="6cf07-122">**ColumnMapping**的属性**ChildElement1**列将设置为**MappingType.Element**。</span><span class="sxs-lookup"><span data-stu-id="6cf07-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="6cf07-123">**数据集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="6cf07-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="6cf07-124">**表：** Element1</span><span class="sxs-lookup"><span data-stu-id="6cf07-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="6cf07-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="6cf07-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="6cf07-126">Text2</span><span class="sxs-lookup"><span data-stu-id="6cf07-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6cf07-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="6cf07-127">See also</span></span>
- [<span data-ttu-id="6cf07-128">从 XML 推断数据集关系结构</span><span class="sxs-lookup"><span data-stu-id="6cf07-128">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="6cf07-129">从 XML 加载数据集</span><span class="sxs-lookup"><span data-stu-id="6cf07-129">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="6cf07-130">从 XML 加载数据集构架信息</span><span class="sxs-lookup"><span data-stu-id="6cf07-130">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="6cf07-131">在数据集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="6cf07-131">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="6cf07-132">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="6cf07-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="6cf07-133">ADO.NET 托管提供程序和数据集开发人员中心</span><span class="sxs-lookup"><span data-stu-id="6cf07-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
