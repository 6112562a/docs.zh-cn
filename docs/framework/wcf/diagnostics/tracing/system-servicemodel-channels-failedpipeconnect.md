---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.date: 03/30/2017
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
ms.openlocfilehash: 472821d880433cd6a3292838a48bcb0b5bb34c43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666725"
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="698fc-102">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="698fc-102">System.ServiceModel.Channels.FailedPipeConnect</span></span>
<span data-ttu-id="698fc-103">尝试连接到指定的管道终结点失败。</span><span class="sxs-lookup"><span data-stu-id="698fc-103">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="698fc-104">将在指定的超时期限内再次进行尝试。</span><span class="sxs-lookup"><span data-stu-id="698fc-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="698fc-105">描述</span><span class="sxs-lookup"><span data-stu-id="698fc-105">Description</span></span>  
 <span data-ttu-id="698fc-106">此信息跟踪指示未能连接到指定的管道终结点。</span><span class="sxs-lookup"><span data-stu-id="698fc-106">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="698fc-107">如果未找到指定的管道终结点或指定的管道终结点正忙，则可能会发生此情况。</span><span class="sxs-lookup"><span data-stu-id="698fc-107">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="698fc-108">将进行更多的尝试（两次尝试之间的时间较短），直到尝试成功或 OpenTimeout 过期。</span><span class="sxs-lookup"><span data-stu-id="698fc-108">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="698fc-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="698fc-109">See also</span></span>

- [<span data-ttu-id="698fc-110">跟踪</span><span class="sxs-lookup"><span data-stu-id="698fc-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="698fc-111">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="698fc-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="698fc-112">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="698fc-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
