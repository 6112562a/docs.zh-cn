---
title: <add>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: ec6d5045580e887de5f05a05c8f39fa62c6e3f2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921339"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="84133-102">\<添加 NameValueSectionHandler 和 DictionarySectionHandler 的 > 元素</span><span class="sxs-lookup"><span data-stu-id="84133-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="84133-103">添加自定义应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="84133-103">Adds custom application settings.</span></span> <span data-ttu-id="84133-104">每个 **\<add >** 标记都包含一个键/值对。</span><span class="sxs-lookup"><span data-stu-id="84133-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="84133-105">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="84133-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="84133-106">&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="84133-106">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="84133-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="84133-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="84133-108">语法</span><span class="sxs-lookup"><span data-stu-id="84133-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="84133-109">特性</span><span class="sxs-lookup"><span data-stu-id="84133-109">Attributes</span></span>

| <span data-ttu-id="84133-110">特性</span><span class="sxs-lookup"><span data-stu-id="84133-110">Attribute</span></span> | <span data-ttu-id="84133-111">描述</span><span class="sxs-lookup"><span data-stu-id="84133-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="84133-112">**key**</span><span class="sxs-lookup"><span data-stu-id="84133-112">**key**</span></span>   | <span data-ttu-id="84133-113">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="84133-113">Required attribute.</span></span><br><br><span data-ttu-id="84133-114">指定设置的名称。</span><span class="sxs-lookup"><span data-stu-id="84133-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="84133-115">**值**</span><span class="sxs-lookup"><span data-stu-id="84133-115">**value**</span></span> | <span data-ttu-id="84133-116">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="84133-116">Required attribute.</span></span><br><br><span data-ttu-id="84133-117">指定设置的值。</span><span class="sxs-lookup"><span data-stu-id="84133-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="84133-118">父元素</span><span class="sxs-lookup"><span data-stu-id="84133-118">Parent element</span></span>

| <span data-ttu-id="84133-119">元素</span><span class="sxs-lookup"><span data-stu-id="84133-119">Element</span></span> | <span data-ttu-id="84133-120">描述</span><span class="sxs-lookup"><span data-stu-id="84133-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="84133-121"> **sectionName>\<** 元素</span><span class="sxs-lookup"><span data-stu-id="84133-121">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="84133-122">定义使用<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>类的自定义配置节的设置。</span><span class="sxs-lookup"><span data-stu-id="84133-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="84133-123">子元素</span><span class="sxs-lookup"><span data-stu-id="84133-123">Child elements</span></span>

<span data-ttu-id="84133-124">无</span><span class="sxs-lookup"><span data-stu-id="84133-124">None</span></span>

## <a name="example"></a><span data-ttu-id="84133-125">示例</span><span class="sxs-lookup"><span data-stu-id="84133-125">Example</span></span>

<span data-ttu-id="84133-126">下面的示例演示如何定义自定义配置节, 并使用 **\<add >** 元素将设置放入部分:</span><span class="sxs-lookup"><span data-stu-id="84133-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="84133-127">配置文件</span><span class="sxs-lookup"><span data-stu-id="84133-127">Configuration file</span></span>

<span data-ttu-id="84133-128">此元素可用于应用程序配置文件、计算机配置文件 (*machine.config*) 和不在应用程序目录级别的 web.config 文件。</span><span class="sxs-lookup"><span data-stu-id="84133-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="84133-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="84133-129">See also</span></span>

- [<span data-ttu-id="84133-130">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="84133-130">Configuration file schema for the .NET Framework</span></span>](index.md)
