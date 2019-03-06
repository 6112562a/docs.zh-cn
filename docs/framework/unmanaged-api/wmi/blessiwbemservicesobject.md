---
title: BlessIWbemServicesObject 函数 （非托管 API 参考）
description: BlessIWbemServicesObject 函数指示用户凭据是否允许 IWbemServices 对象的访问权限
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1eb6b870beabb71e340b0ec39c489cedb02128cf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366629"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="5630d-103">BlessIWbemServicesObject 函数</span><span class="sxs-lookup"><span data-stu-id="5630d-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="5630d-104">指示用户凭据是否允许访问指定[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)对象。</span><span class="sxs-lookup"><span data-stu-id="5630d-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="5630d-105">语法</span><span class="sxs-lookup"><span data-stu-id="5630d-105">Syntax</span></span>

```
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a><span data-ttu-id="5630d-106">参数</span><span class="sxs-lookup"><span data-stu-id="5630d-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="5630d-107">[in]指向 WMI 服务对象的指针。</span><span class="sxs-lookup"><span data-stu-id="5630d-107">[in] A pointer to a WMI service object.</span></span>

`strUser`\
<span data-ttu-id="5630d-108">[in]用户名称。</span><span class="sxs-lookup"><span data-stu-id="5630d-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="5630d-109">[in]与关联的密码`strUser`。</span><span class="sxs-lookup"><span data-stu-id="5630d-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="5630d-110">[in]用户的域名。</span><span class="sxs-lookup"><span data-stu-id="5630d-110">[in] The domain name of the user.</span></span> <span data-ttu-id="5630d-111">请参阅[ConnectServerWmi](connectserverwmi.md)函数的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5630d-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="5630d-112">[in]模拟级别。</span><span class="sxs-lookup"><span data-stu-id="5630d-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="5630d-113">[in]授权级别。</span><span class="sxs-lookup"><span data-stu-id="5630d-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="5630d-114">返回值</span><span class="sxs-lookup"><span data-stu-id="5630d-114">Return value</span></span>

<span data-ttu-id="5630d-115">此函数返回以下值中定义*WinError.h*标头文件，也可以在定义它们为常量在代码中：</span><span class="sxs-lookup"><span data-stu-id="5630d-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5630d-116">返回的常量</span><span class="sxs-lookup"><span data-stu-id="5630d-116">Constant</span></span>  |<span data-ttu-id="5630d-117">值</span><span class="sxs-lookup"><span data-stu-id="5630d-117">Value</span></span>  |<span data-ttu-id="5630d-118">描述</span><span class="sxs-lookup"><span data-stu-id="5630d-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="5630d-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="5630d-119">0x80070057</span></span> | <span data-ttu-id="5630d-120">一个或多个参数均无效。</span><span class="sxs-lookup"><span data-stu-id="5630d-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="5630d-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="5630d-121">0x80004003</span></span> | <span data-ttu-id="5630d-122">`pIWbemServices` 为 `null`。</span><span class="sxs-lookup"><span data-stu-id="5630d-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="5630d-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="5630d-123">0x80000008</span></span> | <span data-ttu-id="5630d-124">发生未知的错误。</span><span class="sxs-lookup"><span data-stu-id="5630d-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="5630d-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="5630d-125">0x80000002</span></span> | <span data-ttu-id="5630d-126">没有足够的内存是可用于执行该操作。</span><span class="sxs-lookup"><span data-stu-id="5630d-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="5630d-127">0</span><span class="sxs-lookup"><span data-stu-id="5630d-127">0</span></span> | <span data-ttu-id="5630d-128">函数调用成功。</span><span class="sxs-lookup"><span data-stu-id="5630d-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="5630d-129">要求</span><span class="sxs-lookup"><span data-stu-id="5630d-129">Requirements</span></span>

 <span data-ttu-id="5630d-130">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5630d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="5630d-131">**标头：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5630d-131">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="5630d-132">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5630d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5630d-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="5630d-133">See also</span></span>

- [<span data-ttu-id="5630d-134">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="5630d-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)