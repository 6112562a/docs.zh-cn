---
title: GetErrorInfo 函数 （非托管 API 参考）
description: GetErrorInfo 函数从上一个函数调用中检索错误信息。
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e33a18487da420eb3b317bb70e0ac9e68b4b8ad6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746550"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="21513-103">GetErrorInfo 函数</span><span class="sxs-lookup"><span data-stu-id="21513-103">GetErrorInfo function</span></span>
<span data-ttu-id="21513-104">从上一个函数调用中检索错误信息。</span><span class="sxs-lookup"><span data-stu-id="21513-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="21513-105">语法</span><span class="sxs-lookup"><span data-stu-id="21513-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="21513-106">返回值</span><span class="sxs-lookup"><span data-stu-id="21513-106">Return value</span></span>

<span data-ttu-id="21513-107">指向的指针[IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)对象，如果函数调用成功，或`null`失败。</span><span class="sxs-lookup"><span data-stu-id="21513-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="21513-108">备注</span><span class="sxs-lookup"><span data-stu-id="21513-108">Remarks</span></span>

<span data-ttu-id="21513-109">此函数包装对的调用[IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)方法。</span><span class="sxs-lookup"><span data-stu-id="21513-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="21513-110">要求</span><span class="sxs-lookup"><span data-stu-id="21513-110">Requirements</span></span>  
 <span data-ttu-id="21513-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21513-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21513-112">**标头：** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="21513-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="21513-113">**.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="21513-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21513-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="21513-114">See also</span></span>

- [<span data-ttu-id="21513-115">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="21513-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
