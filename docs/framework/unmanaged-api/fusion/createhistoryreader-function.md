---
title: CreateHistoryReader 函数
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee30d4f32e05fab27ae70052b28d3d152594cf90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778426"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="336c6-102">CreateHistoryReader 函数</span><span class="sxs-lookup"><span data-stu-id="336c6-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="336c6-103">创建指定的文件的历史记录读取。</span><span class="sxs-lookup"><span data-stu-id="336c6-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="336c6-104">语法</span><span class="sxs-lookup"><span data-stu-id="336c6-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="336c6-105">参数</span><span class="sxs-lookup"><span data-stu-id="336c6-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="336c6-106">[in]文件路径中。</span><span class="sxs-lookup"><span data-stu-id="336c6-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="336c6-107">[out]成功完成后，将包含历史记录读取器指向的指针。</span><span class="sxs-lookup"><span data-stu-id="336c6-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="336c6-108">返回值</span><span class="sxs-lookup"><span data-stu-id="336c6-108">Return Value</span></span>  
 <span data-ttu-id="336c6-109">定义在 WinError.h，除了下表中描述的值之外，此方法将返回标准 COM 错误代码。</span><span class="sxs-lookup"><span data-stu-id="336c6-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="336c6-110">返回代码</span><span class="sxs-lookup"><span data-stu-id="336c6-110">Return code</span></span>|<span data-ttu-id="336c6-111">描述</span><span class="sxs-lookup"><span data-stu-id="336c6-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="336c6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="336c6-112">S_OK</span></span>|<span data-ttu-id="336c6-113">指示该方法已成功完成。</span><span class="sxs-lookup"><span data-stu-id="336c6-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="336c6-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="336c6-114">E_INVALIDARG</span></span>|<span data-ttu-id="336c6-115">指示`wzFilePath`或`ppHistoryReader`设置为 null 引用。</span><span class="sxs-lookup"><span data-stu-id="336c6-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="336c6-116">要求</span><span class="sxs-lookup"><span data-stu-id="336c6-116">Requirements</span></span>  
 <span data-ttu-id="336c6-117">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="336c6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="336c6-118">**库：** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="336c6-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="336c6-119">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="336c6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="336c6-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="336c6-120">See also</span></span>

- [<span data-ttu-id="336c6-121">合成全局静态函数</span><span class="sxs-lookup"><span data-stu-id="336c6-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
