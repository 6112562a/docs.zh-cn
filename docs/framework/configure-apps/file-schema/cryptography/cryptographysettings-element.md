---
title: <cryptographySettings> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: 572a5856c9f92f105e727df1ecd8eb2e0a92fc09
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664281"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="b83a2-102">\<G s > 元素</span><span class="sxs-lookup"><span data-stu-id="b83a2-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="b83a2-103">包含加密设置。</span><span class="sxs-lookup"><span data-stu-id="b83a2-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="b83a2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b83a2-104">\<configuration></span></span>  
<span data-ttu-id="b83a2-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="b83a2-105">\<mscorlib></span></span>  
<span data-ttu-id="b83a2-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="b83a2-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b83a2-107">语法</span><span class="sxs-lookup"><span data-stu-id="b83a2-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b83a2-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b83a2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b83a2-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b83a2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b83a2-110">特性</span><span class="sxs-lookup"><span data-stu-id="b83a2-110">Attributes</span></span>  
 <span data-ttu-id="b83a2-111">无。</span><span class="sxs-lookup"><span data-stu-id="b83a2-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b83a2-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b83a2-112">Child Elements</span></span>  
  
|<span data-ttu-id="b83a2-113">元素</span><span class="sxs-lookup"><span data-stu-id="b83a2-113">Element</span></span>|<span data-ttu-id="b83a2-114">描述</span><span class="sxs-lookup"><span data-stu-id="b83a2-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b83a2-115">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="b83a2-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="b83a2-116">包含类到友好名称的映射。</span><span class="sxs-lookup"><span data-stu-id="b83a2-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="b83a2-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="b83a2-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="b83a2-118">包含与类的 ASN 对象标识符 (OID) 映射。</span><span class="sxs-lookup"><span data-stu-id="b83a2-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b83a2-119">父元素</span><span class="sxs-lookup"><span data-stu-id="b83a2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b83a2-120">元素</span><span class="sxs-lookup"><span data-stu-id="b83a2-120">Element</span></span>|<span data-ttu-id="b83a2-121">描述</span><span class="sxs-lookup"><span data-stu-id="b83a2-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b83a2-122">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="b83a2-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="b83a2-123">`cryptographySettings`包含元素。</span><span class="sxs-lookup"><span data-stu-id="b83a2-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b83a2-124">示例</span><span class="sxs-lookup"><span data-stu-id="b83a2-124">Example</span></span>  
 <span data-ttu-id="b83a2-125">下面的示例演示如何使用 **\<g s >** 元素包含加密名称映射和 OID 映射。</span><span class="sxs-lookup"><span data-stu-id="b83a2-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="b83a2-126">此示例将配置运行时, <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>以便`MyHashClass`返回对象, `MyCryptoClass`类映射到对象标识符1.3.36.2.1。</span><span class="sxs-lookup"><span data-stu-id="b83a2-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b83a2-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="b83a2-127">See also</span></span>

- [<span data-ttu-id="b83a2-128">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="b83a2-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b83a2-129">加密设置架构</span><span class="sxs-lookup"><span data-stu-id="b83a2-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b83a2-130">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="b83a2-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
