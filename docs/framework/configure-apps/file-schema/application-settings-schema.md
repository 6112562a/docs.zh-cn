---
title: 应用程序设置架构
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: a74716bcdf3c85c08d0ff3bf66407dce30ee91cc
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083465"
---
# <a name="application-settings-schema"></a><span data-ttu-id="f40e8-102">应用程序设置架构</span><span class="sxs-lookup"><span data-stu-id="f40e8-102">Application Settings schema</span></span>

<span data-ttu-id="f40e8-103">应用程序设置允许 Windows 窗体或 ASP.NET 应用程序来存储和检索应用程序范围和用户范围的设置。</span><span class="sxs-lookup"><span data-stu-id="f40e8-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="f40e8-104">在此上下文中，*设置*是任何可能是特定于应用程序或特定于当前用户的信息 — 从用户的数据库连接字符串的任何内容的首选默认窗口大小。</span><span class="sxs-lookup"><span data-stu-id="f40e8-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="f40e8-105">默认情况下，应用程序设置 Windows 窗体应用程序中的使用<xref:System.Configuration.LocalFileSettingsProvider>类，该类使用.NET 配置系统来存储在 XML 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="f40e8-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="f40e8-106">有关使用应用程序设置的文件的详细信息，请参阅[应用程序设置体系结构](~/docs/framework/winforms/advanced/application-settings-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="f40e8-106">For more information about the files used by application settings, see [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="f40e8-107">应用程序设置定义了以下元素，它使用的配置文件的一部分。</span><span class="sxs-lookup"><span data-stu-id="f40e8-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="f40e8-108">元素</span><span class="sxs-lookup"><span data-stu-id="f40e8-108">Element</span></span>                    | <span data-ttu-id="f40e8-109">描述</span><span class="sxs-lookup"><span data-stu-id="f40e8-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="f40e8-110">**\<applicationSettings>**</span><span class="sxs-lookup"><span data-stu-id="f40e8-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="f40e8-111">包含所有**\<设置 >** 标记特定于应用程序。</span><span class="sxs-lookup"><span data-stu-id="f40e8-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="f40e8-112">**\<userSettings>**</span><span class="sxs-lookup"><span data-stu-id="f40e8-112">**\<userSettings>**</span></span>        | <span data-ttu-id="f40e8-113">包含所有**\<设置 >** 特定于当前用户的标记。</span><span class="sxs-lookup"><span data-stu-id="f40e8-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="f40e8-114">**\<setting>**</span><span class="sxs-lookup"><span data-stu-id="f40e8-114">**\<setting>**</span></span>             | <span data-ttu-id="f40e8-115">定义设置。</span><span class="sxs-lookup"><span data-stu-id="f40e8-115">Defines a setting.</span></span> <span data-ttu-id="f40e8-116">子 **\<applicationSettings >** 或 **\<userSettings >**。</span><span class="sxs-lookup"><span data-stu-id="f40e8-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="f40e8-117">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="f40e8-117">**\<value>**</span></span>               | <span data-ttu-id="f40e8-118">定义设置的值。</span><span class="sxs-lookup"><span data-stu-id="f40e8-118">Defines a setting's value.</span></span> <span data-ttu-id="f40e8-119">子级**\<设置 >**。</span><span class="sxs-lookup"><span data-stu-id="f40e8-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="f40e8-120">\<applicationSettings > 元素</span><span class="sxs-lookup"><span data-stu-id="f40e8-120">\<applicationSettings> element</span></span>

<span data-ttu-id="f40e8-121">此元素包含所有**\<设置 >** 特定于客户端计算机上的应用程序的实例的标记。</span><span class="sxs-lookup"><span data-stu-id="f40e8-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="f40e8-122">未定义任何属性。</span><span class="sxs-lookup"><span data-stu-id="f40e8-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="f40e8-123">\<用户设置 > 元素</span><span class="sxs-lookup"><span data-stu-id="f40e8-123">\<userSettings> element</span></span>

<span data-ttu-id="f40e8-124">此元素包含所有**\<设置 >** 特定于当前正在使用该应用程序的用户的标记。</span><span class="sxs-lookup"><span data-stu-id="f40e8-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="f40e8-125">未定义任何属性。</span><span class="sxs-lookup"><span data-stu-id="f40e8-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="f40e8-126">\<设置 > 元素</span><span class="sxs-lookup"><span data-stu-id="f40e8-126">\<setting> element</span></span>

<span data-ttu-id="f40e8-127">此元素定义设置。</span><span class="sxs-lookup"><span data-stu-id="f40e8-127">This element defines a setting.</span></span> <span data-ttu-id="f40e8-128">它具有以下属性。</span><span class="sxs-lookup"><span data-stu-id="f40e8-128">It has the following attributes.</span></span>

| <span data-ttu-id="f40e8-129">特性</span><span class="sxs-lookup"><span data-stu-id="f40e8-129">Attribute</span></span>        | <span data-ttu-id="f40e8-130">描述</span><span class="sxs-lookup"><span data-stu-id="f40e8-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="f40e8-131">**name**</span><span class="sxs-lookup"><span data-stu-id="f40e8-131">**name**</span></span>         | <span data-ttu-id="f40e8-132">必需。</span><span class="sxs-lookup"><span data-stu-id="f40e8-132">Required.</span></span> <span data-ttu-id="f40e8-133">设置的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="f40e8-133">The unique ID of the setting.</span></span> <span data-ttu-id="f40e8-134">通过 Visual Studio 创建的设置保存名称`ProjectName.Properties.Settings`。</span><span class="sxs-lookup"><span data-stu-id="f40e8-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="f40e8-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="f40e8-135">**serializedAs**</span></span> | <span data-ttu-id="f40e8-136">必需。</span><span class="sxs-lookup"><span data-stu-id="f40e8-136">Required.</span></span> <span data-ttu-id="f40e8-137">要用来序列化的值为文本的格式。</span><span class="sxs-lookup"><span data-stu-id="f40e8-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="f40e8-138">有效值为：</span><span class="sxs-lookup"><span data-stu-id="f40e8-138">Valid values are:</span></span><br><br><span data-ttu-id="f40e8-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="f40e8-139">- `string`.</span></span> <span data-ttu-id="f40e8-140">值序列化为字符串使用<xref:System.ComponentModel.TypeConverter>。</span><span class="sxs-lookup"><span data-stu-id="f40e8-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="f40e8-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="f40e8-141">- `xml`.</span></span> <span data-ttu-id="f40e8-142">使用 XML 序列化序列化值。</span><span class="sxs-lookup"><span data-stu-id="f40e8-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="f40e8-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="f40e8-143">- `binary`.</span></span> <span data-ttu-id="f40e8-144">值序列化为文本编码的二进制文件使用二进制序列化。</span><span class="sxs-lookup"><span data-stu-id="f40e8-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="f40e8-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="f40e8-145">- `custom`.</span></span> <span data-ttu-id="f40e8-146">设置提供程序具有此设置的固有知识和序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="f40e8-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="f40e8-147">\<值 > 元素</span><span class="sxs-lookup"><span data-stu-id="f40e8-147">\<value> element</span></span>

<span data-ttu-id="f40e8-148">此元素包含设置的值。</span><span class="sxs-lookup"><span data-stu-id="f40e8-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="f40e8-149">示例</span><span class="sxs-lookup"><span data-stu-id="f40e8-149">Example</span></span>

<span data-ttu-id="f40e8-150">下面的示例演示定义了两个应用程序范围设置和两个用户范围设置的应用程序设置文件：</span><span class="sxs-lookup"><span data-stu-id="f40e8-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f40e8-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="f40e8-151">See also</span></span>

- [<span data-ttu-id="f40e8-152">应用程序设置概述</span><span class="sxs-lookup"><span data-stu-id="f40e8-152">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="f40e8-153">应用程序设置体系结构</span><span class="sxs-lookup"><span data-stu-id="f40e8-153">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
