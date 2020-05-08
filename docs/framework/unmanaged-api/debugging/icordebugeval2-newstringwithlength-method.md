---
title: ICorDebugEval2::NewStringWithLength 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: a2b76cb59a95082e0cf9c0884b8277cca3c8fe8d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976065"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="0e2d7-102">ICorDebugEval2::NewStringWithLength 方法</span><span class="sxs-lookup"><span data-stu-id="0e2d7-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="0e2d7-103">使用指定的内容创建指定长度的字符串。</span><span class="sxs-lookup"><span data-stu-id="0e2d7-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e2d7-104">语法</span><span class="sxs-lookup"><span data-stu-id="0e2d7-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e2d7-105">参数</span><span class="sxs-lookup"><span data-stu-id="0e2d7-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="0e2d7-106">中指向字符串值的指针。</span><span class="sxs-lookup"><span data-stu-id="0e2d7-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="0e2d7-107">中字符串的长度。</span><span class="sxs-lookup"><span data-stu-id="0e2d7-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e2d7-108">备注</span><span class="sxs-lookup"><span data-stu-id="0e2d7-108">Remarks</span></span>  
 <span data-ttu-id="0e2d7-109">如果字符串的尾随空字符应在托管字符串中，则该`NewStringWithLength`方法的调用方必须确保字符串长度包含结尾的 null 字符。</span><span class="sxs-lookup"><span data-stu-id="0e2d7-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="0e2d7-110">始终在当前执行线程的应用程序域中创建字符串。</span><span class="sxs-lookup"><span data-stu-id="0e2d7-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e2d7-111">要求</span><span class="sxs-lookup"><span data-stu-id="0e2d7-111">Requirements</span></span>  
 <span data-ttu-id="0e2d7-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e2d7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e2d7-113">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e2d7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e2d7-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e2d7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e2d7-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e2d7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
