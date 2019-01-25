---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 4e89dbe35a5232c612555b273c3d771aad42aeb0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584800"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="0abd6-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="0abd6-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="0abd6-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="0abd6-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0abd6-104">语法</span><span class="sxs-lookup"><span data-stu-id="0abd6-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0abd6-105">方法</span><span class="sxs-lookup"><span data-stu-id="0abd6-105">Methods</span></span>  
 <span data-ttu-id="0abd6-106">TcpConnectionPoolSettings 类不定义任何方法。</span><span class="sxs-lookup"><span data-stu-id="0abd6-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0abd6-107">Properties</span><span class="sxs-lookup"><span data-stu-id="0abd6-107">Properties</span></span>  
 <span data-ttu-id="0abd6-108">TcpConnectionPoolSettings 类具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="0abd6-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="0abd6-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="0abd6-109">GroupName</span></span>  
 <span data-ttu-id="0abd6-110">数据类型：String</span><span class="sxs-lookup"><span data-stu-id="0abd6-110">Data type: string</span></span>  
  
 <span data-ttu-id="0abd6-111">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="0abd6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0abd6-112">绑定元素使用的连接池的组名。</span><span class="sxs-lookup"><span data-stu-id="0abd6-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="0abd6-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="0abd6-113">IdleTimeout</span></span>  
 <span data-ttu-id="0abd6-114">数据类型：DateTime</span><span class="sxs-lookup"><span data-stu-id="0abd6-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="0abd6-115">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="0abd6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0abd6-116">连接在断开前可以空闲的最长时间。</span><span class="sxs-lookup"><span data-stu-id="0abd6-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="0abd6-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="0abd6-117">LeaseTimeout</span></span>  
 <span data-ttu-id="0abd6-118">数据类型：DateTime</span><span class="sxs-lookup"><span data-stu-id="0abd6-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="0abd6-119">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="0abd6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0abd6-120">超时前完成租约操作的最大时间。</span><span class="sxs-lookup"><span data-stu-id="0abd6-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="0abd6-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="0abd6-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="0abd6-122">数据类型：sint32</span><span class="sxs-lookup"><span data-stu-id="0abd6-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="0abd6-123">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="0abd6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0abd6-124">每个终结点的最大出站连接数。</span><span class="sxs-lookup"><span data-stu-id="0abd6-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0abd6-125">要求</span><span class="sxs-lookup"><span data-stu-id="0abd6-125">Requirements</span></span>  
  
|<span data-ttu-id="0abd6-126">MOF</span><span class="sxs-lookup"><span data-stu-id="0abd6-126">MOF</span></span>|<span data-ttu-id="0abd6-127">已在 Servicemodel.mof 中声明。</span><span class="sxs-lookup"><span data-stu-id="0abd6-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0abd6-128">命名空间</span><span class="sxs-lookup"><span data-stu-id="0abd6-128">Namespace</span></span>|<span data-ttu-id="0abd6-129">已在 root\ServiceModel 中定义</span><span class="sxs-lookup"><span data-stu-id="0abd6-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0abd6-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="0abd6-130">See also</span></span>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
