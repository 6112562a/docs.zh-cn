---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: 591e1a1dcb6746d79ff5eceba7e74e890f327354
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779491"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="f0913-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="f0913-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="f0913-103">由于未处理的执行异常，导致指定操作的指定事务处于完成状态。</span><span class="sxs-lookup"><span data-stu-id="f0913-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f0913-104">描述</span><span class="sxs-lookup"><span data-stu-id="f0913-104">Description</span></span>  
 <span data-ttu-id="f0913-105">在尝试完成当前事务过程中发生错误时跟踪。</span><span class="sxs-lookup"><span data-stu-id="f0913-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="f0913-106">在将答复或错误发送给调用方之前，会发生此情况。</span><span class="sxs-lookup"><span data-stu-id="f0913-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f0913-107">疑难解答</span><span class="sxs-lookup"><span data-stu-id="f0913-107">Troubleshooting</span></span>  
 <span data-ttu-id="f0913-108">检查跟踪的消息，以查找异常消息和所有可操作的项。</span><span class="sxs-lookup"><span data-stu-id="f0913-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0913-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="f0913-109">See also</span></span>

- [<span data-ttu-id="f0913-110">跟踪</span><span class="sxs-lookup"><span data-stu-id="f0913-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="f0913-111">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="f0913-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f0913-112">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="f0913-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
