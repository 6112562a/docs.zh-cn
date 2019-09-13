---
title: 如何：使用相同类型的多个安全令牌
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 84009eacca113fcd83a0e4908c7d6eb0c82db7d5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928763"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="1f433-102">如何：使用相同类型的多个安全令牌</span><span class="sxs-lookup"><span data-stu-id="1f433-102">How to: Use Multiple Security Tokens of the Same Type</span></span>

- <span data-ttu-id="1f433-103">在 .NET Framework 3.0 中，客户端消息只包含任何给定类型的一个令牌。</span><span class="sxs-lookup"><span data-stu-id="1f433-103">In .NET Framework 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="1f433-104">现在，客户端消息可以包含某种类型的多个令牌。</span><span class="sxs-lookup"><span data-stu-id="1f433-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="1f433-105">本主题演示如何将同一类型的多个令牌包含在客户端消息中。</span><span class="sxs-lookup"><span data-stu-id="1f433-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
- <span data-ttu-id="1f433-106">请注意，不能以这种方式配置服务：一个服务只能包含一个支持令牌。</span><span class="sxs-lookup"><span data-stu-id="1f433-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="1f433-107">使用相同类型的多个安全令牌</span><span class="sxs-lookup"><span data-stu-id="1f433-107">To use multiple security tokens of the same type</span></span>  
  
1. <span data-ttu-id="1f433-108">创建要填充的空绑定元素集合。</span><span class="sxs-lookup"><span data-stu-id="1f433-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <span data-ttu-id="1f433-109">通过调用 <xref:System.ServiceModel.Channels.SecurityBindingElement> 创建 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>。</span><span class="sxs-lookup"><span data-stu-id="1f433-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <span data-ttu-id="1f433-110">创建一个 <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> 集合。</span><span class="sxs-lookup"><span data-stu-id="1f433-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. <span data-ttu-id="1f433-111">将 SAML 令牌添加到集合中。</span><span class="sxs-lookup"><span data-stu-id="1f433-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. <span data-ttu-id="1f433-112">将集合添加到 <xref:System.ServiceModel.Channels.SecurityBindingElement> 中。</span><span class="sxs-lookup"><span data-stu-id="1f433-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. <span data-ttu-id="1f433-113">将绑定元素添加到绑定元素集合中。</span><span class="sxs-lookup"><span data-stu-id="1f433-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. <span data-ttu-id="1f433-114">返回从绑定元素集合创建的新自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="1f433-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="1f433-115">示例</span><span class="sxs-lookup"><span data-stu-id="1f433-115">Example</span></span>  
 <span data-ttu-id="1f433-116">下面是前面的过程所描述的整个方法。</span><span class="sxs-lookup"><span data-stu-id="1f433-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
