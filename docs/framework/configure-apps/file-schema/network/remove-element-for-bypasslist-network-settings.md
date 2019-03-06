---
title: bypasslist -> <remove> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: a04cca3e57af5cc422776c5b2444a140e86f98b9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354253"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="6be64-102">\<删除 > bypasslist （网络设置） 的元素</span><span class="sxs-lookup"><span data-stu-id="6be64-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="6be64-103">从代理跳过列表中删除 IP 地址或 DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="6be64-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

<span data-ttu-id="6be64-104">\<configuration>\\</span><span class="sxs-lookup"><span data-stu-id="6be64-104">\<configuration>\\</span></span>
<span data-ttu-id="6be64-105">\<system.net>\\</span><span class="sxs-lookup"><span data-stu-id="6be64-105">\<system.net>\\</span></span>
<span data-ttu-id="6be64-106">\<defaultProxy>\\</span><span class="sxs-lookup"><span data-stu-id="6be64-106">\<defaultProxy>\\</span></span>
<span data-ttu-id="6be64-107">\<bypasslist>\\</span><span class="sxs-lookup"><span data-stu-id="6be64-107">\<bypasslist>\\</span></span>
<span data-ttu-id="6be64-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="6be64-108">\<remove></span></span>

## <a name="syntax"></a><span data-ttu-id="6be64-109">语法</span><span class="sxs-lookup"><span data-stu-id="6be64-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6be64-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6be64-110">Attributes and Elements</span></span>

<span data-ttu-id="6be64-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6be64-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6be64-112">特性</span><span class="sxs-lookup"><span data-stu-id="6be64-112">Attributes</span></span>

|<span data-ttu-id="6be64-113">**特性**</span><span class="sxs-lookup"><span data-stu-id="6be64-113">**Attribute**</span></span>|<span data-ttu-id="6be64-114">**说明**</span><span class="sxs-lookup"><span data-stu-id="6be64-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="6be64-115">正则表达式描述 IP 地址或 DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="6be64-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6be64-116">子元素</span><span class="sxs-lookup"><span data-stu-id="6be64-116">Child Elements</span></span>

<span data-ttu-id="6be64-117">无。</span><span class="sxs-lookup"><span data-stu-id="6be64-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6be64-118">父元素</span><span class="sxs-lookup"><span data-stu-id="6be64-118">Parent Elements</span></span>

|<span data-ttu-id="6be64-119">**元素**</span><span class="sxs-lookup"><span data-stu-id="6be64-119">**Element**</span></span>|<span data-ttu-id="6be64-120">**说明**</span><span class="sxs-lookup"><span data-stu-id="6be64-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="6be64-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="6be64-121">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="6be64-122">提供一组描述不使用代理的地址的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="6be64-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6be64-123">备注</span><span class="sxs-lookup"><span data-stu-id="6be64-123">Remarks</span></span>

<span data-ttu-id="6be64-124">`remove`元素中删除描述 IP 地址或 DNS 服务器名称，从列表中的绕过代理服务器的地址的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="6be64-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="6be64-125">配置文件中或在配置层次结构中较高级别上，前面已定义地址。</span><span class="sxs-lookup"><span data-stu-id="6be64-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="6be64-126">值为`address`属性应为描述一组 IP 地址或主机名的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="6be64-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="6be64-127">有关正则表达式的详细信息，请参阅。[.NET framework 正则表达式](../../../../../docs/standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="6be64-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="6be64-128">配置文件</span><span class="sxs-lookup"><span data-stu-id="6be64-128">Configuration Files</span></span>

<span data-ttu-id="6be64-129">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="6be64-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="6be64-130">示例</span><span class="sxs-lookup"><span data-stu-id="6be64-130">Example</span></span>

<span data-ttu-id="6be64-131">下面的示例删除 adventure-works.com 域中，任何以前定义，然后将 contoso.com 域添加到忽略列表。</span><span class="sxs-lookup"><span data-stu-id="6be64-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="6be64-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="6be64-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="6be64-133">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="6be64-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
