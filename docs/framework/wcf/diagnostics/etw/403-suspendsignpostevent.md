---
title: 403 - SuspendSignpostEvent
ms.date: 03/30/2017
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
ms.openlocfilehash: 727d164b9cd47657af0d7810103a766f33cb35de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758049"
---
# <a name="403---suspendsignpostevent"></a><span data-ttu-id="06c0a-102">403 - SuspendSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="06c0a-102">403 - SuspendSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="06c0a-103">属性</span><span class="sxs-lookup"><span data-stu-id="06c0a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06c0a-104">Id</span><span class="sxs-lookup"><span data-stu-id="06c0a-104">ID</span></span>|<span data-ttu-id="06c0a-105">403</span><span class="sxs-lookup"><span data-stu-id="06c0a-105">403</span></span>|  
|<span data-ttu-id="06c0a-106">关键字</span><span class="sxs-lookup"><span data-stu-id="06c0a-106">Keywords</span></span>|<span data-ttu-id="06c0a-107">疑难解答</span><span class="sxs-lookup"><span data-stu-id="06c0a-107">Troubleshooting</span></span>|  
|<span data-ttu-id="06c0a-108">级别</span><span class="sxs-lookup"><span data-stu-id="06c0a-108">Level</span></span>|<span data-ttu-id="06c0a-109">信息</span><span class="sxs-lookup"><span data-stu-id="06c0a-109">Information</span></span>|  
|<span data-ttu-id="06c0a-110">通道</span><span class="sxs-lookup"><span data-stu-id="06c0a-110">Channel</span></span>|<span data-ttu-id="06c0a-111">Microsoft-Windows-应用程序服务器-应用程序/分析</span><span class="sxs-lookup"><span data-stu-id="06c0a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="06c0a-112">描述</span><span class="sxs-lookup"><span data-stu-id="06c0a-112">Description</span></span>  
 <span data-ttu-id="06c0a-113">此事件标记端对端活动的挂起，</span><span class="sxs-lookup"><span data-stu-id="06c0a-113">This event marks the suspension of an end-to-end activity.</span></span> <span data-ttu-id="06c0a-114">它包含活动的名称。</span><span class="sxs-lookup"><span data-stu-id="06c0a-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="06c0a-115">消息</span><span class="sxs-lookup"><span data-stu-id="06c0a-115">Message</span></span>  
 <span data-ttu-id="06c0a-116">活动边界。</span><span class="sxs-lookup"><span data-stu-id="06c0a-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="06c0a-117">详细信息</span><span class="sxs-lookup"><span data-stu-id="06c0a-117">Details</span></span>  
  
|<span data-ttu-id="06c0a-118">数据项名称</span><span class="sxs-lookup"><span data-stu-id="06c0a-118">Data Item Name</span></span>|<span data-ttu-id="06c0a-119">数据项类型</span><span class="sxs-lookup"><span data-stu-id="06c0a-119">Data Item Type</span></span>|<span data-ttu-id="06c0a-120">描述</span><span class="sxs-lookup"><span data-stu-id="06c0a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="06c0a-121">扩展数据</span><span class="sxs-lookup"><span data-stu-id="06c0a-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="06c0a-122">活动的名称。</span><span class="sxs-lookup"><span data-stu-id="06c0a-122">The name of the activity.</span></span>|  
|<span data-ttu-id="06c0a-123">应用程序域</span><span class="sxs-lookup"><span data-stu-id="06c0a-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="06c0a-124">由 AppDomain.CurrentDomain.FriendlyName 返回的字符串。</span><span class="sxs-lookup"><span data-stu-id="06c0a-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
