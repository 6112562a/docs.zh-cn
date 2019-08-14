---
title: 如何：将 IIS 5.0 和 IIS 6.0 配置为部署 WPF 应用程序
ms.date: 03/30/2017
helpviewer_keywords:
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
ms.openlocfilehash: 3179679abcf32e40374c7f02e64466a326a73195
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2019
ms.locfileid: "69013022"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>如何：将 IIS 5.0 和 IIS 6.0 配置为部署 WPF 应用程序

你可以从大多数[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Web 服务器部署应用程序, 前提是这些服务器是使用适当的多用途 Internet 邮件扩展 (MIME) 类型配置的。 默认情况下[!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] , 使用这些 MIME 类型配置, 但[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)]并[!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)]不配置。

本主题介绍如何配置 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 和 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] 以部署 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序。

> [!NOTE]
> 你可以在注册表中检查*UserAgent*字符串, 以确定系统是否安装了 .NET Framework。 有关详细信息和检查*UserAgent*字符串以确定系统是否安装了 .NET Framework 的脚本, 请参阅[检测是否安装了 .NET Framework 3.0](how-to-detect-whether-the-net-framework-3-0-is-installed.md)。

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a>调整内容过期设置

应将内容过期设置调整为 1 分钟。 以下过程概述了如何通过 [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] 执行此操作。

1. 单击“开始”菜单，指向“管理工具”，然后单击“Internet Information Services (IIS) 管理器”。 还可以使用“%systemroot%\system32\inetsrv\iis.msc”从命令行启动此应用程序。

2. 展开 [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] 树，直到找到“默认网站”节点。

3. 右键单击“默认网站”，然后从上下文菜单中选择“属性”。

4. 选择“HTTP 头”选项卡，然后单击“启用内容过期”。

5. 将内容设置为在 1 分钟后过期。

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a>注册 MIME 类型和文件扩展名

必须注册多个 MIME 类型和文件扩展名, 以便客户端系统上的浏览器可以加载正确的处理程序。 需要添加以下类型：

|扩展名|MIME 类型|
|---------------|---------------|
|.manifest|application/manifest|
|.xaml|application/xaml+xml|
|.application|application/x-ms-application|
|.xbap|application/x-ms-xbap|
|.deploy|application/octet-stream|
|.xps|application/vnd.ms-xpsdocument|

> [!NOTE]
> 无需在客户端系统上注册 MIME 类型或文件扩展名。 当你安装 Microsoft .NET Framework 时, 它们会自动注册。

以下 Microsoft Visual Basic Scripting Edition (VBScript) 示例自动向添加所需的 MIME 类型[!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]。 若要使用该脚本，请将代码复制到服务器上的 .vbs 文件。 然后，通过从命令行运行该文件或在 [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)] 中双击该文件来运行脚本。

```vb
' This script adds the necessary Windows Presentation Foundation MIME types
' to an IIS Server.
' To use this script, just double-click or execute it from a command line.
' Running this script multiple times results in multiple entries in the IIS MimeMap.

Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec
Const ADS_PROPERTY_UPDATE = 2

' Set the MIME types to be added
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _
    "application/xaml+xml", ".application", "application/x-ms-application", _
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _
    ".xps", "application/vnd.ms-xpsdocument")

' Get the MimeMap object
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")

' Call AddMimeType for every pair of extension/MIME type
For counter = 0 to UBound(MimeTypesToAddArray) Step 2
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)
Next

' Create a Shell object
Set WshShell = CreateObject("WScript.Shell")

' Stop and Start the IIS Service
Set oExec = WshShell.Exec("net stop w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = WshShell.Exec("net start w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = Nothing

' Report status to user
WScript.Echo "Windows Presentation Foundation MIME types have been registered."

' AddMimeType Sub
Sub AddMimeType (Ext, MType)

    ' Get the mappings from the MimeMap property.
    MimeMapArray = MimeMapObj.GetEx("MimeMap")

    ' Add a new mapping.
    i = UBound(MimeMapArray) + 1
    ReDim Preserve MimeMapArray(i)
    Set MimeMapArray(i) = CreateObject("MimeMap")
    MimeMapArray(i).Extension = Ext
    MimeMapArray(i).MimeType = MType
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray
    MimeMapObj.SetInfo

End Sub
```

> [!NOTE]
> 多次运行此脚本会在[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)]或[!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)]元数据库中创建多个 MIME 映射条目。

运行此脚本后, 你可能看不到或[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] Microsoft 管理控制台 (MMC) 中的其他 MIME 类型。 但是, 这些 MIME 类型已添加到[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)]或[!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)]元数据库中。 以下脚本将显示[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)]或[!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)]元数据库中的所有 MIME 类型。

```vb
' This script lists the MIME types for an IIS Server.
' To use this script, just double-click or execute it from a command line
' by calling cscript.exe

dim mimeMapEntry, allMimeMaps

' Get the MimeMap object.
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")
allMimeMaps = mimeMapEntry.GetEx("MimeMap")

' Display the mappings in the table.
For Each mimeMap In allMimeMaps
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")
Next
```

将脚本另存为 `.vbs` 文件（例如，`DiscoverIISMimeTypes.vbs`），并使用以下命令从命令提示符运行它：

```console
cscript DiscoverIISMimeTypes.vbs
```
