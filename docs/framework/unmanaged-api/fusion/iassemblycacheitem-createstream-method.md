---
title: IAssemblyCacheItem::CreateStream 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58fb8e3ae0f9485399aebe81b5f77ee61ee8f3ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641091"
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream 方法
创建具有指定的名称和格式的流。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwFlags`  
 [in]包括的标志。  
  
 `pszStreamName`  
 [in]若要创建的流的名称。  
  
 `dwFormat`  
 [in]要进行流处理的文件的格式。  
  
 `dwFormatFlags`  
 [in]包括特定于格式的标志。  
  
 `ppIStream`  
 [out]指向所返回的地址的指针[IStream](/windows/desktop/api/objidl/nn-objidl-istream)实例。  
  
 `puliMaxSize`  
 [in，可选]引用的流的最大大小`ppIStream`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Fusion.h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅
- [IAssemblyCacheItem 接口](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
