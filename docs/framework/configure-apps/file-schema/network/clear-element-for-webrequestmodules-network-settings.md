---
title: webRequestModules 的 <clear> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: 5dea238629b282776cb45f7b388e655fa557d084
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674592"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="07110-102">\<清除 > webRequestModules （网络设置） 的</span><span class="sxs-lookup"><span data-stu-id="07110-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="07110-103">从应用程序中删除所有已注册的 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="07110-103">Removes all registered Web request modules from the application.</span></span>  
  
 <span data-ttu-id="07110-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="07110-104">\<configuration></span></span>  
<span data-ttu-id="07110-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="07110-105">\<system.net></span></span>  
<span data-ttu-id="07110-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="07110-106">\<webRequestModules></span></span>  
<span data-ttu-id="07110-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="07110-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07110-108">语法</span><span class="sxs-lookup"><span data-stu-id="07110-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07110-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="07110-109">Attributes and Elements</span></span>  
 <span data-ttu-id="07110-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="07110-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07110-111">特性</span><span class="sxs-lookup"><span data-stu-id="07110-111">Attributes</span></span>  
 <span data-ttu-id="07110-112">无。</span><span class="sxs-lookup"><span data-stu-id="07110-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="07110-113">子元素</span><span class="sxs-lookup"><span data-stu-id="07110-113">Child Elements</span></span>  
 <span data-ttu-id="07110-114">无。</span><span class="sxs-lookup"><span data-stu-id="07110-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07110-115">父元素</span><span class="sxs-lookup"><span data-stu-id="07110-115">Parent Elements</span></span>  
  
|<span data-ttu-id="07110-116">**元素**</span><span class="sxs-lookup"><span data-stu-id="07110-116">**Element**</span></span>|<span data-ttu-id="07110-117">**说明**</span><span class="sxs-lookup"><span data-stu-id="07110-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="07110-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="07110-118">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="07110-119">指定模块用于从网络主机请求信息。</span><span class="sxs-lookup"><span data-stu-id="07110-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07110-120">备注</span><span class="sxs-lookup"><span data-stu-id="07110-120">Remarks</span></span>  
 <span data-ttu-id="07110-121">`clear`元素中删除所有已注册的配置文件中或在配置层次结构中较高级别上前面定义的 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="07110-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="07110-122">配置文件</span><span class="sxs-lookup"><span data-stu-id="07110-122">Configuration Files</span></span>  
 <span data-ttu-id="07110-123">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="07110-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07110-124">示例</span><span class="sxs-lookup"><span data-stu-id="07110-124">Example</span></span>  
 <span data-ttu-id="07110-125">下面的示例将清除所有 Web 请求模块，然后为 HTTP 注册 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="07110-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07110-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="07110-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="07110-127">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="07110-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
