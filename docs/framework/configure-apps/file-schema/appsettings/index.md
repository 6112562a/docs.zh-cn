---
title: 应用设置架构
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 548d93e5447c06480629658b13b673aa3d15fc86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705462"
---
# <a name="app-settings-schema"></a><span data-ttu-id="39e04-102">应用设置架构</span><span class="sxs-lookup"><span data-stu-id="39e04-102">App Settings schema</span></span>

<span data-ttu-id="39e04-103">包含自定义应用程序设置，如文件路径、XML Web service URL 或应用程序的任何其他自定义配置信息。</span><span class="sxs-lookup"><span data-stu-id="39e04-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="39e04-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="39e04-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="39e04-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="39e04-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="39e04-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="39e04-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="39e04-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="39e04-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="39e04-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="39e04-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="39e04-109">元素</span><span class="sxs-lookup"><span data-stu-id="39e04-109">Element</span></span> | <span data-ttu-id="39e04-110">描述</span><span class="sxs-lookup"><span data-stu-id="39e04-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="39e04-111">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="39e04-111">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="39e04-112">包含 **\<add>**、**\<clear>** 和 **\<remove>** 标记，用于控制应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="39e04-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="39e04-113">具有可选的“file”属性。</span><span class="sxs-lookup"><span data-stu-id="39e04-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="39e04-114">**\<add>**</span><span class="sxs-lookup"><span data-stu-id="39e04-114">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="39e04-115">定义设置。</span><span class="sxs-lookup"><span data-stu-id="39e04-115">Defines a setting.</span></span> <span data-ttu-id="39e04-116">**\<appSettings>** 的子级。</span><span class="sxs-lookup"><span data-stu-id="39e04-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="39e04-117">需要“key”和“value”属性。</span><span class="sxs-lookup"><span data-stu-id="39e04-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="39e04-118">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="39e04-118">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="39e04-119">清除所有设置。</span><span class="sxs-lookup"><span data-stu-id="39e04-119">Clears all settings.</span></span> <span data-ttu-id="39e04-120">**\<appSettings>** 的子级。</span><span class="sxs-lookup"><span data-stu-id="39e04-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="39e04-121">不具有属性。</span><span class="sxs-lookup"><span data-stu-id="39e04-121">Has no attributes.</span></span> |
| [<span data-ttu-id="39e04-122">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="39e04-122">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="39e04-123">删除设置。</span><span class="sxs-lookup"><span data-stu-id="39e04-123">Removes a setting.</span></span> <span data-ttu-id="39e04-124">**\<appSettings>** 的子级。</span><span class="sxs-lookup"><span data-stu-id="39e04-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="39e04-125">需要“key”属性。</span><span class="sxs-lookup"><span data-stu-id="39e04-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="39e04-126">\<appSettings> 元素</span><span class="sxs-lookup"><span data-stu-id="39e04-126">\<appSettings> element</span></span>

<span data-ttu-id="39e04-127">此元素包含 **\<add>**、**\<clear>** 和 **\<remove>** 标记，用于控制应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="39e04-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="39e04-128">它定义“file”的一个可选属性。</span><span class="sxs-lookup"><span data-stu-id="39e04-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="39e04-129">\<add> 元素</span><span class="sxs-lookup"><span data-stu-id="39e04-129">\<add> element</span></span>

<span data-ttu-id="39e04-130">将自定义应用程序设置作为名称/值对添加到应用程序设置集合。</span><span class="sxs-lookup"><span data-stu-id="39e04-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="39e04-131">它定义“key”和“value”的属性。</span><span class="sxs-lookup"><span data-stu-id="39e04-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="39e04-132">\<clear> 元素</span><span class="sxs-lookup"><span data-stu-id="39e04-132">\<clear> element</span></span>

<span data-ttu-id="39e04-133">删除对继承的自定义应用程序设置的所有引用，并仅允许由 **\<add>** 元素（位于 **\<clear>** 元素后）添加的引用。</span><span class="sxs-lookup"><span data-stu-id="39e04-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="39e04-134">未定义任何属性。</span><span class="sxs-lookup"><span data-stu-id="39e04-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="39e04-135">\<remove> 元素</span><span class="sxs-lookup"><span data-stu-id="39e04-135">\<remove> element</span></span>

<span data-ttu-id="39e04-136">删除对应用程序设置集合中继承的自定义应用程序设置的引用。</span><span class="sxs-lookup"><span data-stu-id="39e04-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="39e04-137">定义“key”的属性。</span><span class="sxs-lookup"><span data-stu-id="39e04-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="39e04-138">示例</span><span class="sxs-lookup"><span data-stu-id="39e04-138">Example</span></span>

<span data-ttu-id="39e04-139">下面的示例演示外部应用程序设置文件 (custom.config)，该文件定义自定义应用程序设置：</span><span class="sxs-lookup"><span data-stu-id="39e04-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="39e04-140">下面的示例演示使用外部设置文件中的设置并自行设置应用程序设置的应用程序配置文件：</span><span class="sxs-lookup"><span data-stu-id="39e04-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="39e04-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="39e04-141">See also</span></span>

- [<span data-ttu-id="39e04-142">应用程序设置概述</span><span class="sxs-lookup"><span data-stu-id="39e04-142">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="39e04-143">应用程序设置体系结构</span><span class="sxs-lookup"><span data-stu-id="39e04-143">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
