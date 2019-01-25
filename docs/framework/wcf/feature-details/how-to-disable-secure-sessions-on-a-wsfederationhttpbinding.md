---
title: 如何：禁用安全会话在 WSFederationHttpBinding 上
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: 8c03bb9601ecbaaf8694d1df26ba43e34434ac47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720023"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="f7540-102">如何：禁用安全会话在 WSFederationHttpBinding 上</span><span class="sxs-lookup"><span data-stu-id="f7540-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>
<span data-ttu-id="f7540-103">某些服务可能需要联合凭据，但不支持安全会话。</span><span class="sxs-lookup"><span data-stu-id="f7540-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="f7540-104">在这种情况下，必须禁用安全会话功能。</span><span class="sxs-lookup"><span data-stu-id="f7540-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="f7540-105">与 <xref:System.ServiceModel.WSHttpBinding> 不同，<xref:System.ServiceModel.WSFederationHttpBinding> 类不支持在与服务通信时禁用安全会话。</span><span class="sxs-lookup"><span data-stu-id="f7540-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="f7540-106">相反，你必须创建一个自定义绑定，以便用引导来替换安全会话设置。</span><span class="sxs-lookup"><span data-stu-id="f7540-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>  
  
 <span data-ttu-id="f7540-107">本主题演示如何修改 <xref:System.ServiceModel.WSFederationHttpBinding> 中包含的绑定元素以创建自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="f7540-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="f7540-108">结果与 <xref:System.ServiceModel.WSFederationHttpBinding> 基本相同，只是它不使用安全会话。</span><span class="sxs-lookup"><span data-stu-id="f7540-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="f7540-109">创建不使用安全会话的自定义联合绑定</span><span class="sxs-lookup"><span data-stu-id="f7540-109">To create a custom federated binding without secure session</span></span>  
  
1.  <span data-ttu-id="f7540-110">创建 <xref:System.ServiceModel.WSFederationHttpBinding> 类的一个实例，方法可以是在代码中以强制方式创建，也可以是从配置文件中加载。</span><span class="sxs-lookup"><span data-stu-id="f7540-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>  
  
2.  <span data-ttu-id="f7540-111">将 <xref:System.ServiceModel.WSFederationHttpBinding> 克隆到一个 <xref:System.ServiceModel.Channels.CustomBinding> 中。</span><span class="sxs-lookup"><span data-stu-id="f7540-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
3.  <span data-ttu-id="f7540-112">在 <xref:System.ServiceModel.Channels.SecurityBindingElement> 中查找 <xref:System.ServiceModel.Channels.CustomBinding>。</span><span class="sxs-lookup"><span data-stu-id="f7540-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
4.  <span data-ttu-id="f7540-113">在 <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> 中查找 <xref:System.ServiceModel.Channels.SecurityBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="f7540-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
5.  <span data-ttu-id="f7540-114">用 <xref:System.ServiceModel.Channels.SecurityBindingElement> 中的引导安全绑定元素替换原始 <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>。</span><span class="sxs-lookup"><span data-stu-id="f7540-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7540-115">示例</span><span class="sxs-lookup"><span data-stu-id="f7540-115">Example</span></span>  
 <span data-ttu-id="f7540-116">下面的示例创建一个不使用安全会话的自定义联合绑定。</span><span class="sxs-lookup"><span data-stu-id="f7540-116">This following example creates a custom federated binding without secure session.</span></span>  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f7540-117">编译代码</span><span class="sxs-lookup"><span data-stu-id="f7540-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="f7540-118">若要编译代码示例，请创建一个引用 System.ServiceModel.dll 程序集的项目。</span><span class="sxs-lookup"><span data-stu-id="f7540-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7540-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="f7540-119">See also</span></span>
- [<span data-ttu-id="f7540-120">绑定与安全</span><span class="sxs-lookup"><span data-stu-id="f7540-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
