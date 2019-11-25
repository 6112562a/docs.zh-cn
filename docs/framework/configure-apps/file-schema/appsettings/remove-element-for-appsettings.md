---
title: <appSettings> 的 <remove> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0fcdb75aa733a9d7634ec1c3b31dcbbb87e090e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088717"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="9b47a-102">\<删除 \<appSettings > 元素 ></span><span class="sxs-lookup"><span data-stu-id="9b47a-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="9b47a-103">删除自定义应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="9b47a-103">Removes custom application settings.</span></span>

<span data-ttu-id="9b47a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b47a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9b47a-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="9b47a-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="9b47a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<删除 >**</span><span class="sxs-lookup"><span data-stu-id="9b47a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9b47a-107">语法</span><span class="sxs-lookup"><span data-stu-id="9b47a-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="9b47a-108">特性</span><span class="sxs-lookup"><span data-stu-id="9b47a-108">Attribute</span></span>

|         | <span data-ttu-id="9b47a-109">描述</span><span class="sxs-lookup"><span data-stu-id="9b47a-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="9b47a-110">**key**</span><span class="sxs-lookup"><span data-stu-id="9b47a-110">**key**</span></span> | <span data-ttu-id="9b47a-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="9b47a-111">Required attribute.</span></span><br><br><span data-ttu-id="9b47a-112">指定要删除的密钥的名称。</span><span class="sxs-lookup"><span data-stu-id="9b47a-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="9b47a-113">父元素</span><span class="sxs-lookup"><span data-stu-id="9b47a-113">Parent element</span></span>

|     | <span data-ttu-id="9b47a-114">描述</span><span class="sxs-lookup"><span data-stu-id="9b47a-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9b47a-115"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="9b47a-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="9b47a-116">包含自定义应用程序设置，如文件路径、XML Web service URL 或应用程序的任何其他自定义配置信息。</span><span class="sxs-lookup"><span data-stu-id="9b47a-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9b47a-117">子元素</span><span class="sxs-lookup"><span data-stu-id="9b47a-117">Child elements</span></span>

<span data-ttu-id="9b47a-118">None</span><span class="sxs-lookup"><span data-stu-id="9b47a-118">None</span></span>

## <a name="example"></a><span data-ttu-id="9b47a-119">示例</span><span class="sxs-lookup"><span data-stu-id="9b47a-119">Example</span></span>

<span data-ttu-id="9b47a-120">下面的示例演示如何删除 `ApplicationName`的自定义配置设置：</span><span class="sxs-lookup"><span data-stu-id="9b47a-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="9b47a-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="9b47a-121">See also</span></span>

- [<span data-ttu-id="9b47a-122">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="9b47a-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
