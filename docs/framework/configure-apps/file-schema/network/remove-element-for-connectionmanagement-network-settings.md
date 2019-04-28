---
title: connectionManagement 的 <remove> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: d9c584fb2faa971e7ce1ca287a94c8c6129820fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705189"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="93465-102">\<删除 > connectionManagement （网络设置） 的元素</span><span class="sxs-lookup"><span data-stu-id="93465-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="93465-103">从连接管理列表中删除 IP 地址或 DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="93465-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="93465-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="93465-104">\<configuration></span></span>  
<span data-ttu-id="93465-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="93465-105">\<system.net></span></span>  
<span data-ttu-id="93465-106">\<connectionManagement></span><span class="sxs-lookup"><span data-stu-id="93465-106">\<connectionManagement></span></span>  
<span data-ttu-id="93465-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="93465-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93465-108">语法</span><span class="sxs-lookup"><span data-stu-id="93465-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93465-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="93465-109">Attributes and Elements</span></span>  
 <span data-ttu-id="93465-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="93465-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93465-111">特性</span><span class="sxs-lookup"><span data-stu-id="93465-111">Attributes</span></span>  
  
|<span data-ttu-id="93465-112">**特性**</span><span class="sxs-lookup"><span data-stu-id="93465-112">**Attribute**</span></span>|<span data-ttu-id="93465-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="93465-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="93465-114">IP 地址或 DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="93465-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93465-115">子元素</span><span class="sxs-lookup"><span data-stu-id="93465-115">Child Elements</span></span>  
 <span data-ttu-id="93465-116">无。</span><span class="sxs-lookup"><span data-stu-id="93465-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93465-117">父元素</span><span class="sxs-lookup"><span data-stu-id="93465-117">Parent Elements</span></span>  
  
|<span data-ttu-id="93465-118">**元素**</span><span class="sxs-lookup"><span data-stu-id="93465-118">**Element**</span></span>|<span data-ttu-id="93465-119">**说明**</span><span class="sxs-lookup"><span data-stu-id="93465-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="93465-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="93465-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="93465-121">指定到网络主机的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="93465-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93465-122">备注</span><span class="sxs-lookup"><span data-stu-id="93465-122">Remarks</span></span>  
 <span data-ttu-id="93465-123">`remove`元素中移除指定的服务器的连接管理列表项。</span><span class="sxs-lookup"><span data-stu-id="93465-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="93465-124">值`address`属性应为有效的 IP 地址或主机名。</span><span class="sxs-lookup"><span data-stu-id="93465-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="93465-125">配置文件</span><span class="sxs-lookup"><span data-stu-id="93465-125">Configuration Files</span></span>  
 <span data-ttu-id="93465-126">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="93465-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93465-127">示例</span><span class="sxs-lookup"><span data-stu-id="93465-127">Example</span></span>  
 <span data-ttu-id="93465-128">以下示例将删除任何服务器的连接管理列表项`www.adventure-works.com`，然后配置应用程序使用与服务器的四个连接`www.contoso.com`和两个连接到所有其他服务器。</span><span class="sxs-lookup"><span data-stu-id="93465-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="93465-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="93465-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="93465-130">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="93465-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
