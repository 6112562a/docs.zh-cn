---
title: 如何：使用相同类型的多个安全令牌
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 7de5d52587e1796ecfa05048024f8847a555655c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972830"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>如何：使用相同类型的多个安全令牌
- 在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0 中，客户端消息只包含一个任意给定类型的令牌。 现在，客户端消息可以包含某种类型的多个令牌。 本主题演示如何将同一类型的多个令牌包含在客户端消息中。  
  
- 请注意，不能以这种方式配置服务：一个服务只能包含一个支持令牌。  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>使用相同类型的多个安全令牌  
  
1. 创建要填充的空绑定元素集合。  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. 通过调用 <xref:System.ServiceModel.Channels.SecurityBindingElement> 创建 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>。  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. 创建一个 <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> 集合。  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. 将 SAML 令牌添加到集合中。  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. 将集合添加到 <xref:System.ServiceModel.Channels.SecurityBindingElement> 中。  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. 将绑定元素添加到绑定元素集合中。  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. 返回从绑定元素集合创建的新自定义绑定。  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>示例  
 下面是前面的过程所描述的整个方法。  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
