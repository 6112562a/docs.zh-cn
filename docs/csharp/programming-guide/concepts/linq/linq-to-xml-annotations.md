---
title: LINQ to XML 批注 3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 5f1940be2fc126ff9e9c7a4cb37e5cc7fc95d3c3
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689939"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="61111-102">LINQ to XML 批注</span><span class="sxs-lookup"><span data-stu-id="61111-102">LINQ to XML Annotations</span></span>

<span data-ttu-id="61111-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的注释可将任意类型的任意对象与 XML 树中的任何 XML 组件相关联。</span><span class="sxs-lookup"><span data-stu-id="61111-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="61111-104">若要向 XML 组件（例如 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute>）中添加批注，需调用 <xref:System.Xml.Linq.XObject.AddAnnotation%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="61111-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="61111-105">批注是按类型检索的。</span><span class="sxs-lookup"><span data-stu-id="61111-105">You retrieve annotations by type.</span></span>

<span data-ttu-id="61111-106">请注意，批注不是 XML 信息集的一部分，不对它们进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="61111-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="61111-107">方法</span><span class="sxs-lookup"><span data-stu-id="61111-107">Methods</span></span>

<span data-ttu-id="61111-108">处理批注时可以使用以下方法：</span><span class="sxs-lookup"><span data-stu-id="61111-108">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="61111-109">方法</span><span class="sxs-lookup"><span data-stu-id="61111-109">Method</span></span>|<span data-ttu-id="61111-110">说明</span><span class="sxs-lookup"><span data-stu-id="61111-110">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="61111-111">向 <xref:System.Xml.Linq.XObject> 的批注列表中添加对象。</span><span class="sxs-lookup"><span data-stu-id="61111-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="61111-112">从 <xref:System.Xml.Linq.XObject> 获取指定类型的第一个批注对象。</span><span class="sxs-lookup"><span data-stu-id="61111-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="61111-113">获取 <xref:System.Xml.Linq.XObject> 的指定类型的批注集合。</span><span class="sxs-lookup"><span data-stu-id="61111-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="61111-114">从 <xref:System.Xml.Linq.XObject> 移除指定类型的批注。</span><span class="sxs-lookup"><span data-stu-id="61111-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
