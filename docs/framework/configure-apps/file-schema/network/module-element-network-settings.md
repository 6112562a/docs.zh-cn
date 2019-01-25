---
title: '&lt;模块&gt;元素 （网络设置）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: 4daa0d133342d2bbbf4dd716246d8ba90e49ef9c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685034"
---
# <a name="ltmodulegt-element-network-settings"></a><span data-ttu-id="6fb29-102">&lt;模块&gt;元素 （网络设置）</span><span class="sxs-lookup"><span data-stu-id="6fb29-102">&lt;module&gt; Element (Network Settings)</span></span>
<span data-ttu-id="6fb29-103">向应用程序添加新的代理模块。</span><span class="sxs-lookup"><span data-stu-id="6fb29-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="6fb29-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6fb29-104">\<configuration></span></span>  
<span data-ttu-id="6fb29-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6fb29-105">\<system.net></span></span>  
<span data-ttu-id="6fb29-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="6fb29-106">\<defaultProxy></span></span>  
<span data-ttu-id="6fb29-107">\<模块 ></span><span class="sxs-lookup"><span data-stu-id="6fb29-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb29-108">语法</span><span class="sxs-lookup"><span data-stu-id="6fb29-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fb29-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6fb29-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6fb29-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6fb29-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fb29-111">特性</span><span class="sxs-lookup"><span data-stu-id="6fb29-111">Attributes</span></span>  
  
|<span data-ttu-id="6fb29-112">**特性**</span><span class="sxs-lookup"><span data-stu-id="6fb29-112">**Attribute**</span></span>|<span data-ttu-id="6fb29-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="6fb29-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="6fb29-114">完全限定的类型名 (由<xref:System.Type.FullName%2A>属性) 和程序集名称 (由<xref:System.Reflection.Assembly.FullName%2A>属性)、 分隔一个逗号，来实现该代理。</span><span class="sxs-lookup"><span data-stu-id="6fb29-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fb29-115">子元素</span><span class="sxs-lookup"><span data-stu-id="6fb29-115">Child Elements</span></span>  
 <span data-ttu-id="6fb29-116">无。</span><span class="sxs-lookup"><span data-stu-id="6fb29-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6fb29-117">父元素</span><span class="sxs-lookup"><span data-stu-id="6fb29-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6fb29-118">**元素**</span><span class="sxs-lookup"><span data-stu-id="6fb29-118">**Element**</span></span>|<span data-ttu-id="6fb29-119">**说明**</span><span class="sxs-lookup"><span data-stu-id="6fb29-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6fb29-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="6fb29-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="6fb29-121">配置超文本传输协议 (HTTP) 代理服务器。</span><span class="sxs-lookup"><span data-stu-id="6fb29-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fb29-122">备注</span><span class="sxs-lookup"><span data-stu-id="6fb29-122">Remarks</span></span>  
 <span data-ttu-id="6fb29-123">`module`元素注册代理类实现的<xref:System.Net.IWebProxy>接口。</span><span class="sxs-lookup"><span data-stu-id="6fb29-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="6fb29-124">在注册代理类之后，该 `module` 可用于通过所支持的代理请求信息。</span><span class="sxs-lookup"><span data-stu-id="6fb29-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="6fb29-125">值为`type`属性应为该模块的类名和名称的其对应的动态链接库 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="6fb29-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6fb29-126">配置文件</span><span class="sxs-lookup"><span data-stu-id="6fb29-126">Configuration Files</span></span>  
 <span data-ttu-id="6fb29-127">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="6fb29-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fb29-128">示例</span><span class="sxs-lookup"><span data-stu-id="6fb29-128">Example</span></span>  
 <span data-ttu-id="6fb29-129">下面的示例注册自定义代理类。</span><span class="sxs-lookup"><span data-stu-id="6fb29-129">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6fb29-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="6fb29-130">See also</span></span>
- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="6fb29-131">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="6fb29-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
