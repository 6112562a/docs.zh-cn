---
title: ICorDebugRegisterSet::GetRegisters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 737993ac80b26d490915af3e97fd6a9552246aee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792111"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="92fd0-102">ICorDebugRegisterSet::GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="92fd0-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="92fd0-103">获取位掩码指定的每个寄存器的值（在当前正在执行代码的计算机上）。</span><span class="sxs-lookup"><span data-stu-id="92fd0-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92fd0-104">语法</span><span class="sxs-lookup"><span data-stu-id="92fd0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92fd0-105">参数</span><span class="sxs-lookup"><span data-stu-id="92fd0-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="92fd0-106">中指定要检索的寄存器值的位掩码。</span><span class="sxs-lookup"><span data-stu-id="92fd0-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="92fd0-107">每个位对应于一个寄存器。</span><span class="sxs-lookup"><span data-stu-id="92fd0-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="92fd0-108">如果将位设置为1，则将检索寄存器的值;否则，不检索寄存器的值。</span><span class="sxs-lookup"><span data-stu-id="92fd0-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="92fd0-109">中要检索的寄存器值的数目。</span><span class="sxs-lookup"><span data-stu-id="92fd0-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="92fd0-110">弄`CORDB_REGISTER` 对象的数组，其中每个对象都接收寄存器的值。</span><span class="sxs-lookup"><span data-stu-id="92fd0-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92fd0-111">备注</span><span class="sxs-lookup"><span data-stu-id="92fd0-111">Remarks</span></span>  
 <span data-ttu-id="92fd0-112">数组的大小应等于位掩码中设置为1的位数。</span><span class="sxs-lookup"><span data-stu-id="92fd0-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="92fd0-113">`regCount` 参数指定将接收寄存器值的缓冲区中的元素数。</span><span class="sxs-lookup"><span data-stu-id="92fd0-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="92fd0-114">如果 `regCount` 值对于掩码指示的寄存器数量太小，则将从该集中截断编号较高的寄存器。</span><span class="sxs-lookup"><span data-stu-id="92fd0-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="92fd0-115">如果 `regCount` 值太大，则不会修改未使用的 `regBuffer` 元素。</span><span class="sxs-lookup"><span data-stu-id="92fd0-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="92fd0-116">如果位掩码指定的寄存器不可用，`GetRegisters` 将为该寄存器返回一个不确定的值。</span><span class="sxs-lookup"><span data-stu-id="92fd0-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92fd0-117">需求</span><span class="sxs-lookup"><span data-stu-id="92fd0-117">Requirements</span></span>  
 <span data-ttu-id="92fd0-118">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92fd0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92fd0-119">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92fd0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92fd0-120">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92fd0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92fd0-121">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92fd0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92fd0-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92fd0-122">See also</span></span>

- [<span data-ttu-id="92fd0-123">ICorDebugRegisterSet 接口</span><span class="sxs-lookup"><span data-stu-id="92fd0-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="92fd0-124">ICorDebugRegisterSet2 接口</span><span class="sxs-lookup"><span data-stu-id="92fd0-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
