---
title: <cryptoNameMapping> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: 87b24595f5013ad3b981256fd97bc758863c600b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921103"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="e4c51-102">\<cryptoNameMapping > 元素</span><span class="sxs-lookup"><span data-stu-id="e4c51-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="e4c51-103">包含类到友好名称的映射。</span><span class="sxs-lookup"><span data-stu-id="e4c51-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="e4c51-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e4c51-104">\<configuration></span></span>  
<span data-ttu-id="e4c51-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="e4c51-105">\<mscorlib></span></span>  
<span data-ttu-id="e4c51-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="e4c51-106">\<cryptographySettings></span></span>  
<span data-ttu-id="e4c51-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="e4c51-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4c51-108">语法</span><span class="sxs-lookup"><span data-stu-id="e4c51-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4c51-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e4c51-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e4c51-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e4c51-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4c51-111">特性</span><span class="sxs-lookup"><span data-stu-id="e4c51-111">Attributes</span></span>  
 <span data-ttu-id="e4c51-112">无。</span><span class="sxs-lookup"><span data-stu-id="e4c51-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4c51-113">子元素</span><span class="sxs-lookup"><span data-stu-id="e4c51-113">Child Elements</span></span>  
  
|<span data-ttu-id="e4c51-114">元素</span><span class="sxs-lookup"><span data-stu-id="e4c51-114">Element</span></span>|<span data-ttu-id="e4c51-115">描述</span><span class="sxs-lookup"><span data-stu-id="e4c51-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="e4c51-116">包含密码类的列表，这些类具有到 **\<nameEntry>** 元素中的友好名称的映射。</span><span class="sxs-lookup"><span data-stu-id="e4c51-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="e4c51-117">将类名称映射到友好算法名称，允许一个类具有多个友好名称。</span><span class="sxs-lookup"><span data-stu-id="e4c51-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4c51-118">父元素</span><span class="sxs-lookup"><span data-stu-id="e4c51-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e4c51-119">元素</span><span class="sxs-lookup"><span data-stu-id="e4c51-119">Element</span></span>|<span data-ttu-id="e4c51-120">描述</span><span class="sxs-lookup"><span data-stu-id="e4c51-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e4c51-121">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="e4c51-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="e4c51-122">包含加密设置。</span><span class="sxs-lookup"><span data-stu-id="e4c51-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="e4c51-123">包含类到友好名称的映射。</span><span class="sxs-lookup"><span data-stu-id="e4c51-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="e4c51-124">\<包含 g s > 元素。</span><span class="sxs-lookup"><span data-stu-id="e4c51-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e4c51-125">示例</span><span class="sxs-lookup"><span data-stu-id="e4c51-125">Example</span></span>  
 <span data-ttu-id="e4c51-126">下面的示例演示如何使用 **\<cryptoNameMapping >** 元素来引用加密类并配置运行时。</span><span class="sxs-lookup"><span data-stu-id="e4c51-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="e4c51-127">然后, 你可以将字符串 "RSA" 传递给<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法, 并<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>使用方法返回`MyCryptoRSAClass`对象。</span><span class="sxs-lookup"><span data-stu-id="e4c51-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4c51-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="e4c51-128">See also</span></span>

- [<span data-ttu-id="e4c51-129">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="e4c51-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e4c51-130">加密设置架构</span><span class="sxs-lookup"><span data-stu-id="e4c51-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e4c51-131">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="e4c51-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="e4c51-132">配置加密类</span><span class="sxs-lookup"><span data-stu-id="e4c51-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
