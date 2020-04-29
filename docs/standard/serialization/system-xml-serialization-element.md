---
title: <system.xml.serialization> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 02027a238bc9a2f82963ea841584d2bb3c6446c6
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410549"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="0831e-102">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="0831e-102">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="0831e-103">用于控制 XML 序列化的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="0831e-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="0831e-104">有关配置文件的详细信息，请参阅[配置文件架构](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0831e-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="0831e-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0831e-105">\<configuration></span></span>\
<span data-ttu-id="0831e-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="0831e-106">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="0831e-107">语法</span><span class="sxs-lookup"><span data-stu-id="0831e-107">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0831e-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0831e-108">Attributes and Elements</span></span>

<span data-ttu-id="0831e-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0831e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0831e-110">特性</span><span class="sxs-lookup"><span data-stu-id="0831e-110">Attributes</span></span>

<span data-ttu-id="0831e-111">无。</span><span class="sxs-lookup"><span data-stu-id="0831e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0831e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="0831e-112">Child Elements</span></span>

|<span data-ttu-id="0831e-113">元素</span><span class="sxs-lookup"><span data-stu-id="0831e-113">Element</span></span>|<span data-ttu-id="0831e-114">描述</span><span class="sxs-lookup"><span data-stu-id="0831e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0831e-115">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="0831e-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="0831e-116">确定 <xref:System.DateTime> 对象的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="0831e-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="0831e-117">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="0831e-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="0831e-118">包含将 XSD 类型映射到 .NET Framework 类型时 <xref:System.Xml.Serialization.XmlSchemaImporter> 所用的类型。</span><span class="sxs-lookup"><span data-stu-id="0831e-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0831e-119">父元素</span><span class="sxs-lookup"><span data-stu-id="0831e-119">Parent Elements</span></span>

|<span data-ttu-id="0831e-120">元素</span><span class="sxs-lookup"><span data-stu-id="0831e-120">Element</span></span>|<span data-ttu-id="0831e-121">描述</span><span class="sxs-lookup"><span data-stu-id="0831e-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0831e-122">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="0831e-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="0831e-123">公共语言运行库和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="0831e-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="0831e-124">示例</span><span class="sxs-lookup"><span data-stu-id="0831e-124">Example</span></span>

<span data-ttu-id="0831e-125">下面的代码示例演示如何指定 <xref:System.DateTime> 对象的序列化模式，以及将 XSD 类型映射到 .NET Framework 类型时 <xref:System.Xml.Serialization.XmlSchemaImporter> 所用的其他类型。</span><span class="sxs-lookup"><span data-stu-id="0831e-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a><span data-ttu-id="0831e-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="0831e-126">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="0831e-127">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="0831e-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="0831e-128">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="0831e-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="0831e-129">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="0831e-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="0831e-130">\<schemaImporterExtensions> 的 \<add> 元素</span><span class="sxs-lookup"><span data-stu-id="0831e-130">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
