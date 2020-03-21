---
title: StrongNameTokenFromPublicKey 函数
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175052"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey 函数
获取表示公钥的令牌。 强名称令牌是公钥的缩写形式。  
  
 此函数已被弃用。 改用[ICLR 强名称：：强名称令牌来自公共密钥](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)方法。  
  
## <a name="syntax"></a>语法  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>parameters  
 `pbPublicKeyBlob`  
 [在][公共密钥Blob](publickeyblob-structure.md)类型的结构，其中包含用于生成强名称签名的密钥对的公共部分。  
  
 `cbPublicKeyBlob`  
 [在]的大小（以字节为单位）的大小`pbPublicKeyBlob`。  
  
 `ppbStrongNameToken`  
 [出]与传入的键对应的强名称令牌`pbPublicKeyBlob`。 通用语言运行时分配要返回令牌的内存。 调用方必须使用[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函数释放此内存。  
  
 `pcbStrongNameToken`  
 [出]返回的强名称令牌的大小（以字节为单位）。  
  
## <a name="return-value"></a>返回值  
 `true`成功完成;否则， `false`.  
  
## <a name="remarks"></a>备注  
 强名称令牌是公钥的缩写形式，用于在元数据中存储关键信息时节省空间。 具体而言，强名称令牌用于程序集引用以引用从属程序集。  
  
 如果`StrongNameTokenFromPublicKey`函数未成功完成，请调用[StrongNameErrorInfo 函数](strongnameerrorinfo-function.md)以检索上次生成的错误。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标题：** 强名称.h  
  
 **库：** 作为资源包含在 mscoree.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [StrongNameTokenFromPublicKey 方法](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey 方法](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob Strong Naming](publickeyblob-structure.md)
