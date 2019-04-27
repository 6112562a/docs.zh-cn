---
title: <defaultFtpCachePolicy> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 36d174beea58ff96674bd873bfbcb8be89591669
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674553"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="3ea07-102">\<defaultFtpCachePolicy > 元素 （网络设置）</span><span class="sxs-lookup"><span data-stu-id="3ea07-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="3ea07-103">介绍 FTP 缓存功能是否处于活动状态并介绍了默认的缓存策略。</span><span class="sxs-lookup"><span data-stu-id="3ea07-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="3ea07-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3ea07-104">\<configuration></span></span>  
<span data-ttu-id="3ea07-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3ea07-105">\<system.net></span></span>  
<span data-ttu-id="3ea07-106">\<requestCaching></span><span class="sxs-lookup"><span data-stu-id="3ea07-106">\<requestCaching></span></span>  
<span data-ttu-id="3ea07-107">\<defaultFtpCachePolicy></span><span class="sxs-lookup"><span data-stu-id="3ea07-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea07-108">语法</span><span class="sxs-lookup"><span data-stu-id="3ea07-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ea07-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3ea07-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3ea07-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3ea07-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ea07-111">特性</span><span class="sxs-lookup"><span data-stu-id="3ea07-111">Attributes</span></span>  
  
|<span data-ttu-id="3ea07-112">特性</span><span class="sxs-lookup"><span data-stu-id="3ea07-112">Attribute</span></span>|<span data-ttu-id="3ea07-113">描述</span><span class="sxs-lookup"><span data-stu-id="3ea07-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="3ea07-114">指定 FTP 缓存策略。</span><span class="sxs-lookup"><span data-stu-id="3ea07-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="3ea07-115">默认值为 `Default`。</span><span class="sxs-lookup"><span data-stu-id="3ea07-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="3ea07-116">policyLevel 属性</span><span class="sxs-lookup"><span data-stu-id="3ea07-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="3ea07-117">“值”</span><span class="sxs-lookup"><span data-stu-id="3ea07-117">Value</span></span>|<span data-ttu-id="3ea07-118">描述</span><span class="sxs-lookup"><span data-stu-id="3ea07-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="3ea07-119">如果资源是最新、 内容长度是准确的并且存在过期、 修改和内容长度属性将，返回缓存的资源。</span><span class="sxs-lookup"><span data-stu-id="3ea07-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="3ea07-120">从服务器返回的资源。</span><span class="sxs-lookup"><span data-stu-id="3ea07-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="3ea07-121">如果内容长度存在并且匹配的项大小，则返回缓存的资源。</span><span class="sxs-lookup"><span data-stu-id="3ea07-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="3ea07-122">如果提供了内容的长度，并且与匹配项的大小;，返回缓存的资源否则为该资源从服务器下载，并返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="3ea07-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="3ea07-123">如果缓存资源的时间戳是与服务器; 上的资源的时间戳相同，则返回缓存的资源否则为资源是从服务器下载，存储在缓存中，并返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="3ea07-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="3ea07-124">从服务器下载资源、 将其存储在缓存中，并返回给调用方的资源。</span><span class="sxs-lookup"><span data-stu-id="3ea07-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="3ea07-125">如果缓存的资源存在，将删除它。</span><span class="sxs-lookup"><span data-stu-id="3ea07-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="3ea07-126">资源从服务器下载，并返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="3ea07-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="3ea07-127">如果时间戳与服务器上的资源的时间戳相同，则使用资源的缓存副本满足请求；否则从服务器下载资源，将资源展示给调用方，然后再存储在缓存中。</span><span class="sxs-lookup"><span data-stu-id="3ea07-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ea07-128">子元素</span><span class="sxs-lookup"><span data-stu-id="3ea07-128">Child Elements</span></span>  
 <span data-ttu-id="3ea07-129">无。</span><span class="sxs-lookup"><span data-stu-id="3ea07-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ea07-130">父元素</span><span class="sxs-lookup"><span data-stu-id="3ea07-130">Parent Elements</span></span>  
  
|<span data-ttu-id="3ea07-131">元素</span><span class="sxs-lookup"><span data-stu-id="3ea07-131">Element</span></span>|<span data-ttu-id="3ea07-132">描述</span><span class="sxs-lookup"><span data-stu-id="3ea07-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ea07-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="3ea07-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="3ea07-134">控制网络请求的缓存机制。</span><span class="sxs-lookup"><span data-stu-id="3ea07-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ea07-135">备注</span><span class="sxs-lookup"><span data-stu-id="3ea07-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ea07-136">示例</span><span class="sxs-lookup"><span data-stu-id="3ea07-136">Example</span></span>  
 <span data-ttu-id="3ea07-137">下面的示例演示如何指定缓存策略的 FTP `NoCacheNoStore`。</span><span class="sxs-lookup"><span data-stu-id="3ea07-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ea07-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="3ea07-138">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="3ea07-139">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="3ea07-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
