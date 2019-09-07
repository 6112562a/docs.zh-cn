---
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: c45a4e67d0a2d98c0e9c1a91e07f25b81370244c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398053"
---
# <a name="declaredtypes"></a><span data-ttu-id="e5791-101">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="e5791-101">\<declaredTypes></span></span>
<span data-ttu-id="e5791-102">包含在进行反序列化时 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知类型。</span><span class="sxs-lookup"><span data-stu-id="e5791-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="e5791-103">有关数据协定和已知类型的详细信息，请参阅[数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e5791-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
<span data-ttu-id="e5791-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5791-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e5791-105">&nbsp;&nbsp;[ **\<system.object >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="e5791-105">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="e5791-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dataContractSerializer >** ](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="e5791-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="e5791-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<declaredTypes >**</span><span class="sxs-lookup"><span data-stu-id="e5791-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5791-108">语法</span><span class="sxs-lookup"><span data-stu-id="e5791-108">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5791-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e5791-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e5791-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e5791-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5791-111">特性</span><span class="sxs-lookup"><span data-stu-id="e5791-111">Attributes</span></span>  
 <span data-ttu-id="e5791-112">无。</span><span class="sxs-lookup"><span data-stu-id="e5791-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5791-113">子元素</span><span class="sxs-lookup"><span data-stu-id="e5791-113">Child Elements</span></span>  
  
|<span data-ttu-id="e5791-114">元素</span><span class="sxs-lookup"><span data-stu-id="e5791-114">Element</span></span>|<span data-ttu-id="e5791-115">描述</span><span class="sxs-lookup"><span data-stu-id="e5791-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5791-116">\<add></span><span class="sxs-lookup"><span data-stu-id="e5791-116">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="e5791-117">添加需要已知类型的类型。</span><span class="sxs-lookup"><span data-stu-id="e5791-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5791-118">父元素</span><span class="sxs-lookup"><span data-stu-id="e5791-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e5791-119">元素</span><span class="sxs-lookup"><span data-stu-id="e5791-119">Element</span></span>|<span data-ttu-id="e5791-120">描述</span><span class="sxs-lookup"><span data-stu-id="e5791-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5791-121">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="e5791-121">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="e5791-122">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的配置数据。</span><span class="sxs-lookup"><span data-stu-id="e5791-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5791-123">备注</span><span class="sxs-lookup"><span data-stu-id="e5791-123">Remarks</span></span>  
 <span data-ttu-id="e5791-124">有关已知类型的详细信息，请参阅[数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="e5791-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5791-125">示例</span><span class="sxs-lookup"><span data-stu-id="e5791-125">Example</span></span>  
 <span data-ttu-id="e5791-126">以下 XML 代码显示了已声明的类型和添加到元素`DataContractSerializer`的已知类型。</span><span class="sxs-lookup"><span data-stu-id="e5791-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="e5791-127">此示例演示要添加的三个类型。</span><span class="sxs-lookup"><span data-stu-id="e5791-127">The example shows three types being added.</span></span> <span data-ttu-id="e5791-128">第一个类型是名为“Orders”的自定义类型，它使用一个名为“Item”的已知类型。</span><span class="sxs-lookup"><span data-stu-id="e5791-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="e5791-129">第二个声明类型 <xref:System.Collections.Generic.List%601>，它使用 `Item` 作为已知类型。</span><span class="sxs-lookup"><span data-stu-id="e5791-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="e5791-130">最后，第三个声明类型是 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="e5791-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="e5791-131"><xref:System.Collections.Generic.Dictionary%602> 类类型是泛型类型，并带有两个类型参数。</span><span class="sxs-lookup"><span data-stu-id="e5791-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="e5791-132">第一个参数表示键，第二个参数表示值。</span><span class="sxs-lookup"><span data-stu-id="e5791-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="e5791-133">下面的示例将第二个类型的 <xref:System.Collections.Generic.List%601>（值）添加到已知类型的列表中。</span><span class="sxs-lookup"><span data-stu-id="e5791-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="e5791-134">必须使用 `index` 属性来指定在已知类型中使用的类型参数。</span><span class="sxs-lookup"><span data-stu-id="e5791-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="e5791-135">在此例中，通过将 index 属性设置为“1”（基于零的集合）来指示值类型。</span><span class="sxs-lookup"><span data-stu-id="e5791-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="e5791-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="e5791-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="e5791-137">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="e5791-137">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="e5791-138">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="e5791-138">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="e5791-139">\<add></span><span class="sxs-lookup"><span data-stu-id="e5791-139">\<add></span></span>](add-of-declaredtypes-element.md)
