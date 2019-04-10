---
title: 如何：在不使用反射的情况下获取打印系统对象属性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: bb906dafd98e75708764b5f0f009900719f6a475
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335194"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="77f89-102">如何：在不使用反射的情况下获取打印系统对象属性</span><span class="sxs-lookup"><span data-stu-id="77f89-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="77f89-103">使用反射对某个对象中列举的属性 （以及这些属性的类型） 可能会降低应用程序性能。</span><span class="sxs-lookup"><span data-stu-id="77f89-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="77f89-104"><xref:System.Printing.IndexedProperties>命名空间提供了一种方式获取此信息与使用反射。</span><span class="sxs-lookup"><span data-stu-id="77f89-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77f89-105">示例</span><span class="sxs-lookup"><span data-stu-id="77f89-105">Example</span></span>  
 <span data-ttu-id="77f89-106">执行此操作的步骤如下所示。</span><span class="sxs-lookup"><span data-stu-id="77f89-106">The steps for doing this are as follows.</span></span>  
  
1. <span data-ttu-id="77f89-107">创建类型的实例。</span><span class="sxs-lookup"><span data-stu-id="77f89-107">Create an instance of the type.</span></span> <span data-ttu-id="77f89-108">在以下示例中，类型是<xref:System.Printing.PrintQueue>附带 Microsoft.NET Framework，但几乎完全相同的代码的类型应适用于从派生类型<xref:System.Printing.PrintSystemObject>。</span><span class="sxs-lookup"><span data-stu-id="77f89-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with Microsoft .NET Framework, but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2. <span data-ttu-id="77f89-109">创建<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>从该类型的<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>。</span><span class="sxs-lookup"><span data-stu-id="77f89-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="77f89-110"><xref:System.Collections.DictionaryEntry.Value%2A>此字典中的每个条目的属性是一个派生自的类型的一个对象<xref:System.Printing.IndexedProperties.PrintProperty>。</span><span class="sxs-lookup"><span data-stu-id="77f89-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3. <span data-ttu-id="77f89-111">枚举将字典中的成员。</span><span class="sxs-lookup"><span data-stu-id="77f89-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="77f89-112">为每个，执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="77f89-112">For each of them, do the following.</span></span>  
  
4. <span data-ttu-id="77f89-113">向上转换为每个条目的值<xref:System.Printing.IndexedProperties.PrintProperty>并使用它来创建<xref:System.Printing.IndexedProperties.PrintProperty>对象。</span><span class="sxs-lookup"><span data-stu-id="77f89-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5. <span data-ttu-id="77f89-114">获取类型的<xref:System.Printing.IndexedProperties.PrintProperty.Value%2A>的每个<xref:System.Printing.IndexedProperties.PrintProperty>对象。</span><span class="sxs-lookup"><span data-stu-id="77f89-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="77f89-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="77f89-115">See also</span></span>

- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [<span data-ttu-id="77f89-116">WPF 中的文档</span><span class="sxs-lookup"><span data-stu-id="77f89-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="77f89-117">打印概述</span><span class="sxs-lookup"><span data-stu-id="77f89-117">Printing Overview</span></span>](printing-overview.md)
