---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 027ace6ea9fc2a0e5ce63efa84e1a49c0ed2cd0a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188022"
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>语法  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>方法  
 TransactionFlowBindingElement 类未定义任何方法。  
  
## <a name="properties"></a>属性  
 TransactionFlowBindingElement 类具有以下属性：  
  
### <a name="issuedtokens"></a>IssuedTokens  
 数据类型：String  
  
 访问类型：只读  
  
 指定对已颁发的安全令牌标头（来自 WS-Trust 的 IssuedTokens）的需求。  
  
### <a name="transactionprotocol"></a>TransactionProtocol  
 数据类型：String  
  
 访问类型：只读  
  
 对事务进行流处理时使用的事务处理协议。  
  
### <a name="transactions"></a>事务  
 数据类型：Boolean  
  
 访问类型：只读  
  
 指示是否支持传入事务。  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|  
  
## <a name="see-also"></a>请参阅  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
