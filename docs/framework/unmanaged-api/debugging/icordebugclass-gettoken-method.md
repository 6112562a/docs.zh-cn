---
title: ICorDebugClass::GetToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b944112ce0b00e84da6243e2e48917e2318b0f1c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746842"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="29020-102">ICorDebugClass::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="29020-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="29020-103">获取`TypeDef`元数据标记所引用的此类定义。</span><span class="sxs-lookup"><span data-stu-id="29020-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29020-104">语法</span><span class="sxs-lookup"><span data-stu-id="29020-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29020-105">参数</span><span class="sxs-lookup"><span data-stu-id="29020-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="29020-106">[out]一个指向`mdTypeDef`引用此类定义的令牌。</span><span class="sxs-lookup"><span data-stu-id="29020-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29020-107">要求</span><span class="sxs-lookup"><span data-stu-id="29020-107">Requirements</span></span>  
 <span data-ttu-id="29020-108">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29020-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29020-109">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29020-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29020-110">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29020-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29020-111">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29020-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29020-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="29020-112">See also</span></span>

- [<span data-ttu-id="29020-113">元数据接口</span><span class="sxs-lookup"><span data-stu-id="29020-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
