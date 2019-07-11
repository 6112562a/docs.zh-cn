---
title: ICorProfilerCallback::RemotingClientSendingMessage 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4729a8d3ac2c6f7ec51a032a07ebfd1c2838cb9a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782911"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="5f141-102">ICorProfilerCallback::RemotingClientSendingMessage 方法</span><span class="sxs-lookup"><span data-stu-id="5f141-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="5f141-103">通知探查器客户端向服务器发送请求。</span><span class="sxs-lookup"><span data-stu-id="5f141-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f141-104">语法</span><span class="sxs-lookup"><span data-stu-id="5f141-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f141-105">参数</span><span class="sxs-lookup"><span data-stu-id="5f141-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="5f141-106">[in]使用中提供的值相对应的值[icorprofilercallback:: Remotingserverreceivingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)在这些情况下：</span><span class="sxs-lookup"><span data-stu-id="5f141-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="5f141-107">远程处理 GUID cookie 处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="5f141-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="5f141-108">通道成功传输消息。</span><span class="sxs-lookup"><span data-stu-id="5f141-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="5f141-109">GUID cookie 处于活动状态的服务器端的过程。</span><span class="sxs-lookup"><span data-stu-id="5f141-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="5f141-110">这允许轻松配对的远程处理调用以及逻辑调用堆栈的创建。</span><span class="sxs-lookup"><span data-stu-id="5f141-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="5f141-111">[in]一个值，则该值`true`的调用是异步的; 否则为如果`false`。</span><span class="sxs-lookup"><span data-stu-id="5f141-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f141-112">要求</span><span class="sxs-lookup"><span data-stu-id="5f141-112">Requirements</span></span>  
 <span data-ttu-id="5f141-113">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f141-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f141-114">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f141-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5f141-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f141-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f141-116">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f141-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f141-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f141-117">See also</span></span>

- [<span data-ttu-id="5f141-118">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="5f141-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
