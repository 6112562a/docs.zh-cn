---
title: 将对象标识符映射到加密算法
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: e035ff04a70a441f7f64bbc230ba6d8036fb2ace
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130606"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="84978-102">将对象标识符映射到加密算法</span><span class="sxs-lookup"><span data-stu-id="84978-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="84978-103">数字签名确保数据不被篡改时它从一个程序发送到另一个。</span><span class="sxs-lookup"><span data-stu-id="84978-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="84978-104">通常通过将一个数学函数应用于的数据进行签名的哈希计算的数字签名。</span><span class="sxs-lookup"><span data-stu-id="84978-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="84978-105">当设置格式的哈希值进行签名，某些数字签名算法将格式设置操作的一部分 ASN.1 对象标识符 (OID)。</span><span class="sxs-lookup"><span data-stu-id="84978-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="84978-106">OID 标识用于计算哈希的算法。</span><span class="sxs-lookup"><span data-stu-id="84978-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="84978-107">您可以映射到对象标识符，以扩展加密机制，以便使用自定义算法的算法。</span><span class="sxs-lookup"><span data-stu-id="84978-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="84978-108">下面的示例演示如何将对象标识符映射到新的哈希算法。</span><span class="sxs-lookup"><span data-stu-id="84978-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="84978-109">[ \<OidEntry > 元素](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)包含两个属性。</span><span class="sxs-lookup"><span data-stu-id="84978-109">The [\<oidEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="84978-110">**OID**属性是对象标识符编号。</span><span class="sxs-lookup"><span data-stu-id="84978-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="84978-111">**名称**属性是值**名称**属性从[ \<nameEntry > 元素](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)。</span><span class="sxs-lookup"><span data-stu-id="84978-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="84978-112">必须从算法名称映射到一个类之前的对象标识符可以映射到一个简单的名称。</span><span class="sxs-lookup"><span data-stu-id="84978-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84978-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="84978-113">See also</span></span>

- [<span data-ttu-id="84978-114">配置加密类</span><span class="sxs-lookup"><span data-stu-id="84978-114">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="84978-115">加密服务</span><span class="sxs-lookup"><span data-stu-id="84978-115">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
