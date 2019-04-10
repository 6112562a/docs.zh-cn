---
title: <Uri> 元素 （Uri 设置）
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 1f3573babd2e363a78f0ad454f0ba36c87ba6390
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212136"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="19883-102">\<Uri > 元素 （Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="19883-102">\<Uri> Element (Uri Settings)</span></span>
<span data-ttu-id="19883-103">包含指定.NET Framework 如何处理使用统一资源标识符 (Uri) 表示的 web 地址的设置。</span><span class="sxs-lookup"><span data-stu-id="19883-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="19883-104">架构层次结构</span><span class="sxs-lookup"><span data-stu-id="19883-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="19883-105">\<配置 > 元素</span><span class="sxs-lookup"><span data-stu-id="19883-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="19883-106">\<uri></span><span class="sxs-lookup"><span data-stu-id="19883-106">\<uri></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="19883-107">语法</span><span class="sxs-lookup"><span data-stu-id="19883-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19883-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="19883-108">Attributes and Elements</span></span>  
 <span data-ttu-id="19883-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="19883-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19883-110">特性</span><span class="sxs-lookup"><span data-stu-id="19883-110">Attributes</span></span>  
 <span data-ttu-id="19883-111">无。</span><span class="sxs-lookup"><span data-stu-id="19883-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="19883-112">子元素</span><span class="sxs-lookup"><span data-stu-id="19883-112">Child Elements</span></span>  
  
|**<span data-ttu-id="19883-113">元素</span><span class="sxs-lookup"><span data-stu-id="19883-113">Element</span></span>**|**<span data-ttu-id="19883-114">描述</span><span class="sxs-lookup"><span data-stu-id="19883-114">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="19883-115">idn</span><span class="sxs-lookup"><span data-stu-id="19883-115">idn</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="19883-116">指定是否对域名应用国际化域名 (IDN) 分析。</span><span class="sxs-lookup"><span data-stu-id="19883-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="19883-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="19883-117">iriParsing</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="19883-118">指定是否对应用国际资源标识符 (IRI) 分析<xref:System.Uri>，以及是否应该应用 IRI 分析规则。</span><span class="sxs-lookup"><span data-stu-id="19883-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="19883-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="19883-119">schemeSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="19883-120">指定如何分析特定方案的 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="19883-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19883-121">父元素</span><span class="sxs-lookup"><span data-stu-id="19883-121">Parent Elements</span></span>  
  
|**<span data-ttu-id="19883-122">元素</span><span class="sxs-lookup"><span data-stu-id="19883-122">Element</span></span>**|**<span data-ttu-id="19883-123">描述</span><span class="sxs-lookup"><span data-stu-id="19883-123">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="19883-124">配置</span><span class="sxs-lookup"><span data-stu-id="19883-124">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="19883-125">包含所有命名空间的设置。</span><span class="sxs-lookup"><span data-stu-id="19883-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19883-126">备注</span><span class="sxs-lookup"><span data-stu-id="19883-126">Remarks</span></span>  
 <span data-ttu-id="19883-127">`uri`元素包含的成员设置<xref:System.Uri>类中的类使用<xref:System.Net>命名空间。</span><span class="sxs-lookup"><span data-stu-id="19883-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="19883-128">设置配置为 IRI 和 IDN 的支持。</span><span class="sxs-lookup"><span data-stu-id="19883-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19883-129">示例</span><span class="sxs-lookup"><span data-stu-id="19883-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="19883-130">描述</span><span class="sxs-lookup"><span data-stu-id="19883-130">Description</span></span>  
 <span data-ttu-id="19883-131">下面的示例演示使用的配置<xref:System.Uri>类，以支持分析 IRI 和 IDN 名称。</span><span class="sxs-lookup"><span data-stu-id="19883-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="19883-132">该示例还会清除所有方案设置，然后添加对未转义的 http 方案的百分比编码路径分隔符的支持。</span><span class="sxs-lookup"><span data-stu-id="19883-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="19883-133">代码</span><span class="sxs-lookup"><span data-stu-id="19883-133">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19883-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="19883-134">See also</span></span>

- [<span data-ttu-id="19883-135">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="19883-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
