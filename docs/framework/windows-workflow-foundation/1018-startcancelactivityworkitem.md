---
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: 8d7045b0a7f31ecfd5dd90f319192bd202804353
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008858"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="3c031-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="3c031-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3c031-103">属性</span><span class="sxs-lookup"><span data-stu-id="3c031-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3c031-104">Id</span><span class="sxs-lookup"><span data-stu-id="3c031-104">ID</span></span>|<span data-ttu-id="3c031-105">1018</span><span class="sxs-lookup"><span data-stu-id="3c031-105">1018</span></span>|  
|<span data-ttu-id="3c031-106">关键字</span><span class="sxs-lookup"><span data-stu-id="3c031-106">Keywords</span></span>|<span data-ttu-id="3c031-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3c031-107">WFRuntime</span></span>|  
|<span data-ttu-id="3c031-108">级别</span><span class="sxs-lookup"><span data-stu-id="3c031-108">Level</span></span>|<span data-ttu-id="3c031-109">详细</span><span class="sxs-lookup"><span data-stu-id="3c031-109">Verbose</span></span>|  
|<span data-ttu-id="3c031-110">通道</span><span class="sxs-lookup"><span data-stu-id="3c031-110">Channel</span></span>|<span data-ttu-id="3c031-111">Microsoft-Windows-应用程序服务器-应用程序/调试</span><span class="sxs-lookup"><span data-stu-id="3c031-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3c031-112">描述</span><span class="sxs-lookup"><span data-stu-id="3c031-112">Description</span></span>  
 <span data-ttu-id="3c031-113">指示 CancelActivityWorkItem 正在开始执行。</span><span class="sxs-lookup"><span data-stu-id="3c031-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3c031-114">消息</span><span class="sxs-lookup"><span data-stu-id="3c031-114">Message</span></span>  
 <span data-ttu-id="3c031-115">开始为 Activity“%1”、DisplayName“%2”、InstanceId“%3”执行 CancelActivityWorkItem。</span><span class="sxs-lookup"><span data-stu-id="3c031-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3c031-116">详细信息</span><span class="sxs-lookup"><span data-stu-id="3c031-116">Details</span></span>  
  
|<span data-ttu-id="3c031-117">数据项名称</span><span class="sxs-lookup"><span data-stu-id="3c031-117">Data Item Name</span></span>|<span data-ttu-id="3c031-118">数据项类型</span><span class="sxs-lookup"><span data-stu-id="3c031-118">Data Item Type</span></span>|<span data-ttu-id="3c031-119">描述</span><span class="sxs-lookup"><span data-stu-id="3c031-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3c031-120">活动</span><span class="sxs-lookup"><span data-stu-id="3c031-120">Activity</span></span>|<span data-ttu-id="3c031-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3c031-121">xs:string</span></span>|<span data-ttu-id="3c031-122">活动的类型名称。</span><span class="sxs-lookup"><span data-stu-id="3c031-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="3c031-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3c031-123">DisplayName</span></span>|<span data-ttu-id="3c031-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3c031-124">xs:string</span></span>|<span data-ttu-id="3c031-125">活动的显示名称。</span><span class="sxs-lookup"><span data-stu-id="3c031-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="3c031-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="3c031-126">InstanceId</span></span>|<span data-ttu-id="3c031-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="3c031-127">xs:string</span></span>|<span data-ttu-id="3c031-128">活动的实例 ID。</span><span class="sxs-lookup"><span data-stu-id="3c031-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3c031-129">应用程序域</span><span class="sxs-lookup"><span data-stu-id="3c031-129">AppDomain</span></span>|<span data-ttu-id="3c031-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="3c031-130">xs:string</span></span>|<span data-ttu-id="3c031-131">由 AppDomain.CurrentDomain.FriendlyName 返回的字符串。</span><span class="sxs-lookup"><span data-stu-id="3c031-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
