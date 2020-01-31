---
title: ICLRDataTarget3::GetExceptionRecord 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
ms.openlocfilehash: 037e216cb93e3aa6fce28966fc724498024abd52
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789060"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="eb842-102">ICLRDataTarget3::GetExceptionRecord 方法</span><span class="sxs-lookup"><span data-stu-id="eb842-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="eb842-103">由公共语言运行时 (CLR) 数据访问服务调用，以检索与目标进程关联的异常记录。</span><span class="sxs-lookup"><span data-stu-id="eb842-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="eb842-104">例如，对于转储目标，此操作等效于通过 Windows 调试帮助库（Dbghelp.dll）中的[MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump)函数的 `ExceptionParam` 参数传入的异常记录。</span><span class="sxs-lookup"><span data-stu-id="eb842-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb842-105">语法</span><span class="sxs-lookup"><span data-stu-id="eb842-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb842-106">参数</span><span class="sxs-lookup"><span data-stu-id="eb842-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="eb842-107">[in] 输入缓冲区大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="eb842-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="eb842-108">这必须等于 `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`。</span><span class="sxs-lookup"><span data-stu-id="eb842-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="eb842-109">[out] 指向接收实际写入缓冲区的字节数的 `ULONG32` 类型的指针。</span><span class="sxs-lookup"><span data-stu-id="eb842-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="eb842-110">[out] 指向接收异常记录副本的内存缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="eb842-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="eb842-111">异常记录作为[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)类型返回。</span><span class="sxs-lookup"><span data-stu-id="eb842-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb842-112">返回值</span><span class="sxs-lookup"><span data-stu-id="eb842-112">Return Value</span></span>  
 <span data-ttu-id="eb842-113">如果成功，则返回值是 `S_OK`；如果失败，则返回失败 `HRESULT` 代码。</span><span class="sxs-lookup"><span data-stu-id="eb842-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="eb842-114">`HRESULT` 代码可以包括但不限于以下代码：</span><span class="sxs-lookup"><span data-stu-id="eb842-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="eb842-115">返回代码</span><span class="sxs-lookup"><span data-stu-id="eb842-115">Return code</span></span>|<span data-ttu-id="eb842-116">描述</span><span class="sxs-lookup"><span data-stu-id="eb842-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="eb842-117">方法成功。</span><span class="sxs-lookup"><span data-stu-id="eb842-117">Method succeeded.</span></span> <span data-ttu-id="eb842-118">已将异常记录复制到输出缓冲区。</span><span class="sxs-lookup"><span data-stu-id="eb842-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="eb842-119">没有与目标关联的异常记录。</span><span class="sxs-lookup"><span data-stu-id="eb842-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="eb842-120">输入缓冲区大小不等于 `sizeof(MINIDUMP_EXCEPTION)`。</span><span class="sxs-lookup"><span data-stu-id="eb842-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb842-121">备注</span><span class="sxs-lookup"><span data-stu-id="eb842-121">Remarks</span></span>  
 <span data-ttu-id="eb842-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)是在 Windows SDK 中的 dbghelp.dll 和 imagehlp.dll 中定义的结构。</span><span class="sxs-lookup"><span data-stu-id="eb842-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="eb842-123">此方法由调试应用程序的编写器实现。</span><span class="sxs-lookup"><span data-stu-id="eb842-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb842-124">需求</span><span class="sxs-lookup"><span data-stu-id="eb842-124">Requirements</span></span>  
 <span data-ttu-id="eb842-125">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb842-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb842-126">**标头：** ClrData，ClrData</span><span class="sxs-lookup"><span data-stu-id="eb842-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="eb842-127">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb842-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb842-128">**.NET Framework 版本：** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eb842-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb842-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb842-129">See also</span></span>

- [<span data-ttu-id="eb842-130">ICLRDataTarget3 接口</span><span class="sxs-lookup"><span data-stu-id="eb842-130">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="eb842-131">GetExceptionContextRecord 方法</span><span class="sxs-lookup"><span data-stu-id="eb842-131">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="eb842-132">GetExceptionThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="eb842-132">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)
