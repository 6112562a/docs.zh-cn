---
title: 用来控制编码的 SOAP 序列化的属性
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 2961d9abc6c32e78b5a61e8f2bbea5cfcf6677bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794935"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="7f001-102">用来控制编码的 SOAP 序列化的属性</span><span class="sxs-lookup"><span data-stu-id="7f001-102">Attributes That Control Encoded SOAP Serialization</span></span>

<span data-ttu-id="7f001-103">命名为[“简单对象访问协议 (SOAP) 1.1”](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)的万维网联合会 (W3C) 文档包含一个可选章节（第 5 节），该节描述了如何编码 SOAP 参数。</span><span class="sxs-lookup"><span data-stu-id="7f001-103">The World Wide Web Consortium (W3C) document named [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="7f001-104">要符合该规范的第 5 节，必须使用在 <xref:System.Xml.Serialization> 命名空间中找到的一组特殊属性。</span><span class="sxs-lookup"><span data-stu-id="7f001-104">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="7f001-105">将这些特性适当应用于类和类的成员，然后使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化一个或多个类的实例。</span><span class="sxs-lookup"><span data-stu-id="7f001-105">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>

<span data-ttu-id="7f001-106">下表显示属性、属性的应用范围及其作用。</span><span class="sxs-lookup"><span data-stu-id="7f001-106">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="7f001-107">有关使用这些特性控制 XML 序列化的更多信息，请参阅[如何：将对象序列化为 SOAP 编码的 XML 流](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)以及[如何：替代编码的 SOAP XML 序列化](how-to-override-encoded-soap-xml-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="7f001-107">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](how-to-override-encoded-soap-xml-serialization.md).</span></span>

<span data-ttu-id="7f001-108">有关属性的详细信息，请参阅[属性](../../../docs/standard/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7f001-108">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span>

|<span data-ttu-id="7f001-109">特性</span><span class="sxs-lookup"><span data-stu-id="7f001-109">Attribute</span></span>|<span data-ttu-id="7f001-110">适用对象</span><span class="sxs-lookup"><span data-stu-id="7f001-110">Applies to</span></span>|<span data-ttu-id="7f001-111">指定</span><span class="sxs-lookup"><span data-stu-id="7f001-111">Specifies</span></span>|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="7f001-112">公共字段、属性、参数或返回值。</span><span class="sxs-lookup"><span data-stu-id="7f001-112">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="7f001-113">类成员将序列化为 XML 属性。</span><span class="sxs-lookup"><span data-stu-id="7f001-113">The class member will be serialized as an XML attribute.</span></span>|
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="7f001-114">公共字段、属性、参数或返回值。</span><span class="sxs-lookup"><span data-stu-id="7f001-114">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="7f001-115">类将序列化为 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="7f001-115">The class will be serialized as an XML element.</span></span>|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="7f001-116">作为枚举标识符的公共字段。</span><span class="sxs-lookup"><span data-stu-id="7f001-116">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="7f001-117">枚举成员的元素名称。</span><span class="sxs-lookup"><span data-stu-id="7f001-117">The element name of an enumeration member.</span></span>|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="7f001-118">公共属性和公共字段。</span><span class="sxs-lookup"><span data-stu-id="7f001-118">Public properties and fields.</span></span>|<span data-ttu-id="7f001-119">序列化包含类时，应该忽略属性或字段。</span><span class="sxs-lookup"><span data-stu-id="7f001-119">The property or field should be ignored when the containing class is serialized.</span></span>|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="7f001-120">公共的派生类声明，以及 Web 服务描述语言 (WSDL) 文档的公共方法。</span><span class="sxs-lookup"><span data-stu-id="7f001-120">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="7f001-121">生成要在序列化时识别的架构时，应该将该类型包括在内。</span><span class="sxs-lookup"><span data-stu-id="7f001-121">The type should be included when generating schemas (to be recognized when serialized).</span></span>|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="7f001-122">公共类声明。</span><span class="sxs-lookup"><span data-stu-id="7f001-122">Public class declarations.</span></span>|<span data-ttu-id="7f001-123">类应序列化为 XML 类型。</span><span class="sxs-lookup"><span data-stu-id="7f001-123">The class should be serialized as an XML type.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7f001-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="7f001-124">See also</span></span>

- [<span data-ttu-id="7f001-125">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="7f001-125">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="7f001-126">如何：将对象序列化为 SOAP 编码的 XML 流</span><span class="sxs-lookup"><span data-stu-id="7f001-126">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [<span data-ttu-id="7f001-127">如何：替代编码的 SOAP XML 序列化</span><span class="sxs-lookup"><span data-stu-id="7f001-127">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)
- [<span data-ttu-id="7f001-128">特性</span><span class="sxs-lookup"><span data-stu-id="7f001-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="7f001-129">如何：序列化对象</span><span class="sxs-lookup"><span data-stu-id="7f001-129">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="7f001-130">如何：反序列化对象</span><span class="sxs-lookup"><span data-stu-id="7f001-130">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
