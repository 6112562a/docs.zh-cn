---
title: <dataContractSerializer>< 的 >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: eb556f533af1f99049382e9a2e34465f88d563db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398084"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="cb628-102">\<dataContractSerializer > 的\<></span><span class="sxs-lookup"><span data-stu-id="cb628-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="cb628-103">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的配置数据。</span><span class="sxs-lookup"><span data-stu-id="cb628-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="cb628-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cb628-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cb628-105">&nbsp;&nbsp;[ **\<system.object >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="cb628-105">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="cb628-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<dataContractSerializer >**</span><span class="sxs-lookup"><span data-stu-id="cb628-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb628-107">语法</span><span class="sxs-lookup"><span data-stu-id="cb628-107">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer"
                       type="String" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb628-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cb628-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cb628-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cb628-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb628-110">特性</span><span class="sxs-lookup"><span data-stu-id="cb628-110">Attributes</span></span>  
  
|<span data-ttu-id="cb628-111">元素</span><span class="sxs-lookup"><span data-stu-id="cb628-111">Element</span></span>|<span data-ttu-id="cb628-112">描述</span><span class="sxs-lookup"><span data-stu-id="cb628-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb628-113">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="cb628-113">ignoreExtensionDataObject</span></span>|<span data-ttu-id="cb628-114">一个布尔值，指定在对终结点进行序列化或反序列化时，是否要忽略由该终结点提供的数据。</span><span class="sxs-lookup"><span data-stu-id="cb628-114">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="cb628-115">只可对 `<dataContractSerializer>` 元素下的 `<behavior>` 设置此属性。</span><span class="sxs-lookup"><span data-stu-id="cb628-115">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="cb628-116">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="cb628-116">maxItemsInObjectGraph</span></span>|<span data-ttu-id="cb628-117">一个整数，指定要序列化或反序列化的最大项数。</span><span class="sxs-lookup"><span data-stu-id="cb628-117">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="cb628-118">此属性为 65536。</span><span class="sxs-lookup"><span data-stu-id="cb628-118">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb628-119">子元素</span><span class="sxs-lookup"><span data-stu-id="cb628-119">Child Elements</span></span>  
  
|<span data-ttu-id="cb628-120">元素</span><span class="sxs-lookup"><span data-stu-id="cb628-120">Element</span></span>|<span data-ttu-id="cb628-121">描述</span><span class="sxs-lookup"><span data-stu-id="cb628-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb628-122">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="cb628-122">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="cb628-123">包含在进行反序列化时 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知类型。</span><span class="sxs-lookup"><span data-stu-id="cb628-123">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="cb628-124">有关数据协定和已知类型的详细信息，请参阅[数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cb628-124">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb628-125">父元素</span><span class="sxs-lookup"><span data-stu-id="cb628-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cb628-126">元素</span><span class="sxs-lookup"><span data-stu-id="cb628-126">Element</span></span>|<span data-ttu-id="cb628-127">描述</span><span class="sxs-lookup"><span data-stu-id="cb628-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb628-128">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="cb628-128">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="cb628-129">表示 <xref:System.Runtime.Serialization> 命名空间节的根元素，并包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的设置选项的元素。</span><span class="sxs-lookup"><span data-stu-id="cb628-129">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb628-130">备注</span><span class="sxs-lookup"><span data-stu-id="cb628-130">Remarks</span></span>  
 <span data-ttu-id="cb628-131">有关已知类型的详细信息，请<xref:System.Runtime.Serialization.DataContractSerializer>参阅和[数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cb628-131">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb628-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="cb628-132">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="cb628-133">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="cb628-133">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
