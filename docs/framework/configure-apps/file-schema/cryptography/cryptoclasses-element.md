---
title: <cryptoClasses> 요소
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 6601417f0b80f623b7698c4b072c35eca44343b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732890"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="73e29-102">\<cryptoClasses > 元素</span><span class="sxs-lookup"><span data-stu-id="73e29-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="73e29-103">[\<nameEntry>](nameentry-element.md) 요소에 있는 이름에 매핑되는 암호화 클래스의 목록이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73e29-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="73e29-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="73e29-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="73e29-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="73e29-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="73e29-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<g s >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="73e29-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="73e29-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="73e29-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="73e29-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptoClasses >**</span><span class="sxs-lookup"><span data-stu-id="73e29-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e29-109">구문</span><span class="sxs-lookup"><span data-stu-id="73e29-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73e29-110">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="73e29-110">Attributes and Elements</span></span>  
 <span data-ttu-id="73e29-111">다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="73e29-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73e29-112">특성</span><span class="sxs-lookup"><span data-stu-id="73e29-112">Attributes</span></span>  
 <span data-ttu-id="73e29-113">없음.</span><span class="sxs-lookup"><span data-stu-id="73e29-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="73e29-114">자식 요소</span><span class="sxs-lookup"><span data-stu-id="73e29-114">Child Elements</span></span>  
  
|<span data-ttu-id="73e29-115">요소</span><span class="sxs-lookup"><span data-stu-id="73e29-115">Element</span></span>|<span data-ttu-id="73e29-116">설명</span><span class="sxs-lookup"><span data-stu-id="73e29-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73e29-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="73e29-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="73e29-118">**\<nameEntry>** 요소에 있는 이름에 매핑되는 암호화 클래스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73e29-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73e29-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="73e29-119">Parent Elements</span></span>  
  
|<span data-ttu-id="73e29-120">요소</span><span class="sxs-lookup"><span data-stu-id="73e29-120">Element</span></span>|<span data-ttu-id="73e29-121">설명</span><span class="sxs-lookup"><span data-stu-id="73e29-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="73e29-122">공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="73e29-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="73e29-123">암호화 설정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73e29-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="73e29-124">이름에 대한 클래스의 매핑이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73e29-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="73e29-125">包含 `cryptographySettings` 元素。</span><span class="sxs-lookup"><span data-stu-id="73e29-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="73e29-126">示例</span><span class="sxs-lookup"><span data-stu-id="73e29-126">Example</span></span>  
 <span data-ttu-id="73e29-127">下面的示例演示如何使用 **\<cryptoClass >** 元素来引用加密类并配置运行时。</span><span class="sxs-lookup"><span data-stu-id="73e29-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="73e29-128">然后，你可以将字符串 "RSA" 传递到 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，并使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法返回 `MyCryptoRSAClass` 对象。</span><span class="sxs-lookup"><span data-stu-id="73e29-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="73e29-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73e29-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="73e29-130">구성 파일 스키마</span><span class="sxs-lookup"><span data-stu-id="73e29-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="73e29-131">암호화 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="73e29-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="73e29-132">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="73e29-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="73e29-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="73e29-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="73e29-134">암호화 클래스 구성</span><span class="sxs-lookup"><span data-stu-id="73e29-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
