---
title: 服务：Transactions Flowed Per Second（每秒流动的事务数）
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: cb41abe74568c3e9641443b81fce3fb6eb6e41bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939407"
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="d8869-102">服务：Transactions Flowed Per Second（每秒流动的事务数）</span><span class="sxs-lookup"><span data-stu-id="d8869-102">Service: Transactions Flowed Per Second</span></span>
<span data-ttu-id="d8869-103">计数器名称：每秒流动的事务。</span><span class="sxs-lookup"><span data-stu-id="d8869-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d8869-104">描述</span><span class="sxs-lookup"><span data-stu-id="d8869-104">Description</span></span>  
 <span data-ttu-id="d8869-105">一秒内流向此服务中操作的事务数。</span><span class="sxs-lookup"><span data-stu-id="d8869-105">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="d8869-106">此计数器为性能计数器类型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用以下公式计算其值。</span><span class="sxs-lookup"><span data-stu-id="d8869-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d8869-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d8869-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
