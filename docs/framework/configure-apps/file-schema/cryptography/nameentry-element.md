---
title: <nameEntry> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: b5f92ca2956f32382b12c9a1dec4e5d41ea4ee2a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285916"
---
# <a name="nameentry-element"></a><span data-ttu-id="b5c4b-102">\<nameEntry > 元素</span><span class="sxs-lookup"><span data-stu-id="b5c4b-102">\<nameEntry> Element</span></span>
<span data-ttu-id="b5c4b-103">将类名称映射到友好算法名称，允许一个类具有多个友好名称。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="b5c4b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b5c4b-104">\<configuration></span></span>  
<span data-ttu-id="b5c4b-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="b5c4b-105">\<mscorlib></span></span>  
<span data-ttu-id="b5c4b-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="b5c4b-106">\<cryptographySettings></span></span>  
<span data-ttu-id="b5c4b-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="b5c4b-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="b5c4b-108">\<nameEntry></span><span class="sxs-lookup"><span data-stu-id="b5c4b-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5c4b-109">语法</span><span class="sxs-lookup"><span data-stu-id="b5c4b-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5c4b-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b5c4b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b5c4b-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5c4b-112">特性</span><span class="sxs-lookup"><span data-stu-id="b5c4b-112">Attributes</span></span>  
  
|<span data-ttu-id="b5c4b-113">特性</span><span class="sxs-lookup"><span data-stu-id="b5c4b-113">Attribute</span></span>|<span data-ttu-id="b5c4b-114">描述</span><span class="sxs-lookup"><span data-stu-id="b5c4b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5c4b-115">**name**</span><span class="sxs-lookup"><span data-stu-id="b5c4b-115">**name**</span></span>|<span data-ttu-id="b5c4b-116">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="b5c4b-117">指定加密类实现的算法的友好名称。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="b5c4b-118">**class**</span><span class="sxs-lookup"><span data-stu-id="b5c4b-118">**class**</span></span>|<span data-ttu-id="b5c4b-119">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="b5c4b-120">指定的值**名称**属性中[ \<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5c4b-121">子元素</span><span class="sxs-lookup"><span data-stu-id="b5c4b-121">Child Elements</span></span>  
 <span data-ttu-id="b5c4b-122">无。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5c4b-123">父元素</span><span class="sxs-lookup"><span data-stu-id="b5c4b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b5c4b-124">元素</span><span class="sxs-lookup"><span data-stu-id="b5c4b-124">Element</span></span>|<span data-ttu-id="b5c4b-125">描述</span><span class="sxs-lookup"><span data-stu-id="b5c4b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b5c4b-126">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="b5c4b-127">为 ASP.NET 配置节指定根元素。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5c4b-128">备注</span><span class="sxs-lookup"><span data-stu-id="b5c4b-128">Remarks</span></span>  
 <span data-ttu-id="b5c4b-129">**名称**属性可以是一个抽象类中找到的名称<xref:System.Security.Cryptography>命名空间。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="b5c4b-130">当您调用**创建**抽象加密类的方法，抽象类名称将传递给<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="b5c4b-131">**CreateFromName**返回指示的类型的实例**类**属性。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="b5c4b-132">如果**名称**特性是一个短名称，例如 RSA，则可以使用该名称时调用**CreateFromName**方法。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5c4b-133">示例</span><span class="sxs-lookup"><span data-stu-id="b5c4b-133">Example</span></span>  
 <span data-ttu-id="b5c4b-134">下面的示例演示如何使用 **\<nameEntry >** 元素来引用一个密码类并配置运行时。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="b5c4b-135">然后可以将字符串"RSA"传递给<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法，并使用<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法以返回`MyCryptoRSAClass`对象。</span><span class="sxs-lookup"><span data-stu-id="b5c4b-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5c4b-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="b5c4b-136">See also</span></span>
- [<span data-ttu-id="b5c4b-137">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="b5c4b-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="b5c4b-138">加密设置架构</span><span class="sxs-lookup"><span data-stu-id="b5c4b-138">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="b5c4b-139">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="b5c4b-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="b5c4b-140">配置加密类</span><span class="sxs-lookup"><span data-stu-id="b5c4b-140">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
