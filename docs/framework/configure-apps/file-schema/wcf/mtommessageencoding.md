---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 538591c85d91960eb4d4fa04caa945954ee5a997
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397707"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="cdb4c-101">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="cdb4c-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="cdb4c-102">指定用于基于 SOAP 消息传输优化机制 (MTOM) 的消息的编码和消息版本控制。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
<span data-ttu-id="cdb4c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cdb4c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cdb4c-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cdb4c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cdb4c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<绑定 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="cdb4c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="cdb4c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="cdb4c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="cdb4c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<绑定 >** </span><span class="sxs-lookup"><span data-stu-id="cdb4c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="cdb4c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mtomMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="cdb4c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdb4c-109">语法</span><span class="sxs-lookup"><span data-stu-id="cdb4c-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdb4c-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cdb4c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cdb4c-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdb4c-112">特性</span><span class="sxs-lookup"><span data-stu-id="cdb4c-112">Attributes</span></span>  
  
|<span data-ttu-id="cdb4c-113">特性</span><span class="sxs-lookup"><span data-stu-id="cdb4c-113">Attribute</span></span>|<span data-ttu-id="cdb4c-114">描述</span><span class="sxs-lookup"><span data-stu-id="cdb4c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cdb4c-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="cdb4c-115">maxBufferSize</span></span>|<span data-ttu-id="cdb4c-116">一个指定可以使用的缓冲区最大大小的整数。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="cdb4c-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="cdb4c-117">maxReadPoolSize</span></span>|<span data-ttu-id="cdb4c-118">一个整数，指定在无需分配新读取器的情况下可以同时读取的消息数。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="cdb4c-119">池越大，系统允许的活动峰值就越大，但工作集也会随之增大。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="cdb4c-120">默认值为 64。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-120">The default is 64.</span></span>|  
|<span data-ttu-id="cdb4c-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="cdb4c-121">maxWritePoolSize</span></span>|<span data-ttu-id="cdb4c-122">一个整数，指定在无需分配新编写器的情况下可以同时发送的消息数。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="cdb4c-123">池越大，系统允许的活动峰值就越大，但工作集也会随之增大。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="cdb4c-124">默认值为 16。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-124">The default is 16.</span></span>|  
|<span data-ttu-id="cdb4c-125">messageVersion</span><span class="sxs-lookup"><span data-stu-id="cdb4c-125">messageVersion</span></span>|<span data-ttu-id="cdb4c-126">指定使用此绑定发送的消息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="cdb4c-127">有效值为</span><span class="sxs-lookup"><span data-stu-id="cdb4c-127">Valid values are</span></span><br /><br /> <span data-ttu-id="cdb4c-128">-   Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="cdb4c-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="cdb4c-129">-   Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="cdb4c-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="cdb4c-130">默认值为 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="cdb4c-131">此属性的类型为 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="cdb4c-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="cdb4c-132">writeEncoding</span></span>|<span data-ttu-id="cdb4c-133">指定要用来在绑定上发出消息的字符集编码。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="cdb4c-134">有效值为</span><span class="sxs-lookup"><span data-stu-id="cdb4c-134">Valid values are</span></span><br /><br /> <span data-ttu-id="cdb4c-135">UnicodeFffeTextEncodingUnicode BigEndian 编码</span><span class="sxs-lookup"><span data-stu-id="cdb4c-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="cdb4c-136">Utf16TextEncodingUnicode 编码</span><span class="sxs-lookup"><span data-stu-id="cdb4c-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="cdb4c-137">Utf8TextEncoding8位编码</span><span class="sxs-lookup"><span data-stu-id="cdb4c-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="cdb4c-138">默认值为 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="cdb4c-139">此属性的类型为 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdb4c-140">子元素</span><span class="sxs-lookup"><span data-stu-id="cdb4c-140">Child Elements</span></span>  
  
|<span data-ttu-id="cdb4c-141">元素</span><span class="sxs-lookup"><span data-stu-id="cdb4c-141">Element</span></span>|<span data-ttu-id="cdb4c-142">描述</span><span class="sxs-lookup"><span data-stu-id="cdb4c-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cdb4c-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cdb4c-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="cdb4c-144">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="cdb4c-145">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdb4c-146">父元素</span><span class="sxs-lookup"><span data-stu-id="cdb4c-146">Parent Elements</span></span>  
  
|<span data-ttu-id="cdb4c-147">元素</span><span class="sxs-lookup"><span data-stu-id="cdb4c-147">Element</span></span>|<span data-ttu-id="cdb4c-148">描述</span><span class="sxs-lookup"><span data-stu-id="cdb4c-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdb4c-149">\<binding></span><span class="sxs-lookup"><span data-stu-id="cdb4c-149">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="cdb4c-150">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdb4c-151">备注</span><span class="sxs-lookup"><span data-stu-id="cdb4c-151">Remarks</span></span>  
 <span data-ttu-id="cdb4c-152">编码是将消息转换为一个字节序列的过程。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="cdb4c-153">解码是反向过程。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-153">Decoding is the reverse process.</span></span> <span data-ttu-id="cdb4c-154">Windows Communication Foundation （WCF）包含三种类型的 SOAP 消息编码：文本、二进制和消息传输优化机制（MTOM）。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="cdb4c-155">`MtomMessageEncoding` 元素指定使用消息传输优化机制 (MTOM) 编码的消息所用的字符编码和消息版本管理以及其他设置。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="cdb4c-156">MTOM 是一种用于在 WCF 消息中传输二进制数据的有效技术。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="cdb4c-157">MTOM 编码器会尝试在效率和互操作性之间建立平衡。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="cdb4c-158">MTOM 编码以文本形式传输大多数 XML，但通过按原样传输来优化大型二进制数据块的传输，无需将其转换为 base64 编码格式。</span><span class="sxs-lookup"><span data-stu-id="cdb4c-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdb4c-159">示例</span><span class="sxs-lookup"><span data-stu-id="cdb4c-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="cdb4c-160">请参阅</span><span class="sxs-lookup"><span data-stu-id="cdb4c-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="cdb4c-161">消息编码</span><span class="sxs-lookup"><span data-stu-id="cdb4c-161">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="cdb4c-162">选择消息编码器</span><span class="sxs-lookup"><span data-stu-id="cdb4c-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="cdb4c-163">绑定</span><span class="sxs-lookup"><span data-stu-id="cdb4c-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cdb4c-164">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="cdb4c-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cdb4c-165">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="cdb4c-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="cdb4c-166">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="cdb4c-166">\<customBinding></span></span>](custombinding.md)
