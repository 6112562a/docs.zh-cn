---
title: 如何：为应用程序设置基于位置的缓存策略
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 6fe569e781b005461ea41e3d6b90859666f9601a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180779"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="17527-102">如何：为应用程序设置基于位置的缓存策略</span><span class="sxs-lookup"><span data-stu-id="17527-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="17527-103">基于位置的缓存策略允许应用程序基于所请求资源的位置显式定义缓存行为。</span><span class="sxs-lookup"><span data-stu-id="17527-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="17527-104">本主题演示如何以编程方式设置缓存策略。</span><span class="sxs-lookup"><span data-stu-id="17527-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="17527-105">有关使用配置文件为应用程序设置策略的信息，请参阅 [\<requestCaching > 元素（网络设置）](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="17527-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="17527-106">为应用程序设置基于位置的缓存策略</span><span class="sxs-lookup"><span data-stu-id="17527-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="17527-107">创建 <xref:System.Net.Cache.RequestCachePolicy> 或 <xref:System.Net.Cache.HttpRequestCachePolicy> 对象。</span><span class="sxs-lookup"><span data-stu-id="17527-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="17527-108">将策略对象设置为应用程序域的默认对象。</span><span class="sxs-lookup"><span data-stu-id="17527-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="17527-109">设置获取来自缓存的请求资源的策略</span><span class="sxs-lookup"><span data-stu-id="17527-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="17527-110">创建获取来自缓存的请求资源的策略（若可用），否则通过将缓存级别设置为 <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable> 向服务器发送请求。</span><span class="sxs-lookup"><span data-stu-id="17527-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="17527-111">可以由客户端和服务器之间的任何缓存实现请求，包括远程缓存。</span><span class="sxs-lookup"><span data-stu-id="17527-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="17527-112">设置防止任何缓存提供资源的策略</span><span class="sxs-lookup"><span data-stu-id="17527-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="17527-113">通过将缓存级别设置为 <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>，创建防止缓存提供请求的资源的策略。</span><span class="sxs-lookup"><span data-stu-id="17527-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="17527-114">此策略级别从本地缓存中删除资源（如果存在），并指示远程缓存也应删除资源。</span><span class="sxs-lookup"><span data-stu-id="17527-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="17527-115">设置仅当请求的资源在本地缓存中时返回请求的资源的策略</span><span class="sxs-lookup"><span data-stu-id="17527-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="17527-116">通过将缓存级别设置为 <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>，创建仅当请求的资源在本地缓存中时返回请求的资源的策略。</span><span class="sxs-lookup"><span data-stu-id="17527-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="17527-117">如果请求的资源不在缓存中，将引发 <xref:System.Net.WebException> 异常。</span><span class="sxs-lookup"><span data-stu-id="17527-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="17527-118">设置防止本地缓存提供资源的策略</span><span class="sxs-lookup"><span data-stu-id="17527-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="17527-119">通过将缓存级别设置为 <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>，创建防止本地缓存提供请求的资源的策略。</span><span class="sxs-lookup"><span data-stu-id="17527-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="17527-120">如果请求的资源是中间缓存并已成功重新验证，中间缓存可提供请求的资源。</span><span class="sxs-lookup"><span data-stu-id="17527-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="17527-121">设置防止任何缓存提供请求的资源的策略</span><span class="sxs-lookup"><span data-stu-id="17527-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="17527-122">通过将缓存级别设置为 <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>，创建防止缓存提供请求的资源的策略。</span><span class="sxs-lookup"><span data-stu-id="17527-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="17527-123">服务器返回的资源可以存储在缓存中。</span><span class="sxs-lookup"><span data-stu-id="17527-123">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="17527-124">设置当服务器上的资源不比缓存副本新时，允许任何缓存提供请求的资源的策略</span><span class="sxs-lookup"><span data-stu-id="17527-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="17527-125">通过将缓存级别设置为 <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>，创建当服务器上的资源不比缓存副本新时，允许任何缓存提供请求的资源的策略。</span><span class="sxs-lookup"><span data-stu-id="17527-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="17527-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17527-126">See also</span></span>

- [<span data-ttu-id="17527-127">网络应用程序的缓存管理</span><span class="sxs-lookup"><span data-stu-id="17527-127">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="17527-128">缓存策略</span><span class="sxs-lookup"><span data-stu-id="17527-128">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="17527-129">基于位置的缓存策略</span><span class="sxs-lookup"><span data-stu-id="17527-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="17527-130">基于时间的缓存策略</span><span class="sxs-lookup"><span data-stu-id="17527-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="17527-131">\<requestCaching> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="17527-131">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
