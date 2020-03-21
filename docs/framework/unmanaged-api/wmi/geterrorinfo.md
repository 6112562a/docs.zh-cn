---
title: GetErrorInfo 函数（非托管 API 引用）
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
ms.openlocfilehash: 802ee66a5be213ac7a599b193ec6de589773ea17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176807"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="02579-103">GetErrorInfo 函数</span><span class="sxs-lookup"><span data-stu-id="02579-103">GetErrorInfo function</span></span>
<span data-ttu-id="02579-104">从上一个函数调用中检索错误信息。</span><span class="sxs-lookup"><span data-stu-id="02579-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="02579-105">语法</span><span class="sxs-lookup"><span data-stu-id="02579-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="02579-106">返回值</span><span class="sxs-lookup"><span data-stu-id="02579-106">Return value</span></span>

<span data-ttu-id="02579-107">如果函数调用成功或`null`失败，则指向[IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)对象的指针。</span><span class="sxs-lookup"><span data-stu-id="02579-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="02579-108">备注</span><span class="sxs-lookup"><span data-stu-id="02579-108">Remarks</span></span>

<span data-ttu-id="02579-109">此函数包装对[IComThreadingInfo 的调用：：GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)方法。</span><span class="sxs-lookup"><span data-stu-id="02579-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="02579-110">要求</span><span class="sxs-lookup"><span data-stu-id="02579-110">Requirements</span></span>  
 <span data-ttu-id="02579-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02579-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02579-112">**标题：** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="02579-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="02579-113">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="02579-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02579-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02579-114">See also</span></span>

- [<span data-ttu-id="02579-115">WMI 和性能计数器（非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="02579-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
