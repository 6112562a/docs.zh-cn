---
title: ISymUnmanagedWriter::DefineField 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37794d40b4b379c5d3a05935cf1f2b7b3da11baa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777363"
---
# <a name="isymunmanagedwriterdefinefield-method"></a>ISymUnmanagedWriter::DefineField 方法
定义一个不在方法内的变量。 此方法是使用类中的某些字段、 位域等。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>参数  
 `parent`  
 [in]元数据类型或方法令牌。  
  
 `name`  
 [in]字段名称。  
  
 `attributes`  
 [in]字段特性。  
  
 `cSig`  
 [in]一个`ULONG32`，它是大小，以字符为单位，包含字段签名所需的缓冲区。  
  
 `signature`  
 [in]字段签名的数组。  
  
 `addrKind`  
 [in]地址类型。  
  
 `addr1`  
 [in]字段规格的第一个地址。  
  
 `addr2`  
 [in]字段规格的第二个地址。  
  
 `addr3`  
 [in]字段规格的第三个地址。  
  
## <a name="return-value"></a>返回值  
 如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。  
  
## <a name="requirements"></a>要求  
 **标头：** CorSym.idl CorSym.h  
  
## <a name="see-also"></a>请参阅

- [ISymUnmanagedWriter 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
