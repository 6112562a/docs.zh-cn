---
title: <module> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: 0d108f2350d82666e3dc24f0f6854fe64ea4755f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674475"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="4a5c7-102">\<模块 > 元素 （网络设置）</span><span class="sxs-lookup"><span data-stu-id="4a5c7-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="4a5c7-103">向应用程序添加新的代理模块。</span><span class="sxs-lookup"><span data-stu-id="4a5c7-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="4a5c7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4a5c7-104">\<configuration></span></span>  
<span data-ttu-id="4a5c7-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4a5c7-105">\<system.net></span></span>  
<span data-ttu-id="4a5c7-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="4a5c7-106">\<defaultProxy></span></span>  
<span data-ttu-id="4a5c7-107">\<模块 ></span><span class="sxs-lookup"><span data-stu-id="4a5c7-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a5c7-108">语法</span><span class="sxs-lookup"><span data-stu-id="4a5c7-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a5c7-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4a5c7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4a5c7-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4a5c7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a5c7-111">特性</span><span class="sxs-lookup"><span data-stu-id="4a5c7-111">Attributes</span></span>  
  
|<span data-ttu-id="4a5c7-112">**特性**</span><span class="sxs-lookup"><span data-stu-id="4a5c7-112">**Attribute**</span></span>|<span data-ttu-id="4a5c7-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="4a5c7-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="4a5c7-114">完全限定的类型名 (由<xref:System.Type.FullName%2A>属性) 和程序集名称 (由<xref:System.Reflection.Assembly.FullName%2A>属性)、 分隔一个逗号，来实现该代理。</span><span class="sxs-lookup"><span data-stu-id="4a5c7-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a5c7-115">子元素</span><span class="sxs-lookup"><span data-stu-id="4a5c7-115">Child Elements</span></span>  
 <span data-ttu-id="4a5c7-116">无。</span><span class="sxs-lookup"><span data-stu-id="4a5c7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a5c7-117">父元素</span><span class="sxs-lookup"><span data-stu-id="4a5c7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4a5c7-118">**元素**</span><span class="sxs-lookup"><span data-stu-id="4a5c7-118">**Element**</span></span>|<span data-ttu-id="4a5c7-119">**说明**</span><span class="sxs-lookup"><span data-stu-id="4a5c7-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4a5c7-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="4a5c7-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="4a5c7-121">配置超文本传输协议 (HTTP) 代理服务器。</span><span class="sxs-lookup"><span data-stu-id="4a5c7-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a5c7-122">备注</span><span class="sxs-lookup"><span data-stu-id="4a5c7-122">Remarks</span></span>  
 <span data-ttu-id="4a5c7-123">`module`元素注册代理类实现的<xref:System.Net.IWebProxy>接口。</span><span class="sxs-lookup"><span data-stu-id="4a5c7-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="4a5c7-124">在注册代理类之后，该 `module` 可用于通过所支持的代理请求信息。</span><span class="sxs-lookup"><span data-stu-id="4a5c7-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="4a5c7-125">值为`type`属性应为该模块的类名和名称的其对应的动态链接库 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="4a5c7-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4a5c7-126">配置文件</span><span class="sxs-lookup"><span data-stu-id="4a5c7-126">Configuration Files</span></span>  
 <span data-ttu-id="4a5c7-127">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="4a5c7-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a5c7-128">示例</span><span class="sxs-lookup"><span data-stu-id="4a5c7-128">Example</span></span>  
 <span data-ttu-id="4a5c7-129">下面的示例注册自定义代理类。</span><span class="sxs-lookup"><span data-stu-id="4a5c7-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a5c7-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="4a5c7-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="4a5c7-131">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="4a5c7-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
