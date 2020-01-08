---
title: 其他 CLI 工具
description: 概述了可安装的支持和扩展 .NET Core 功能的其他工具。
author: mlacouture
ms.date: 12/02/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: 39c2dd6de8e9a8faad0ab19bd162f09abf6801eb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344121"
---
# <a name="net-core-additional-tools-overview"></a>.NET Core 附加工具概述

本节除了 [.NET Core 命令行接口 (CLI)](../tools/index.md) 工具外，还编译了可支持和扩展 .NET Core 功能的工具列表。

## <a name="net-core-uninstall-tooluninstall-toolmd"></a>[.NET Core 卸载工具](uninstall-tool.md)

使用 [.NET Core 卸载工具](https://dotnet.microsoft.com/download/dotnet-core/uninstall-tool) (`dotnet-core-uninstall`)，可清理系统上的 .NET Core SDK 和运行时，以便仅保留指定的版本。 可使用选项集合来指定要卸载的版本。

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web 服务引用工具](wcf-web-service-reference-guide.md)

WCF (Windows Communication Foundation) Web 服务引用是一个 Visual Studio 连接服务提供程序，首次推出是在 [Visual Studio 2017 版本 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools) 中。 此工具可从网络位置上当前解决方案的 Web 服务中，或从 WSDL 文件中检索元数据。 还可生成与 .NET Core 兼容的源文件并使用可用于访问 Web 服务操作的方法定义 WCF 代理类。

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet-svcutil 工具](dotnet-svcutil-guide.md)

WCF (Windows Communication Foundation) dotnet-svcutil.exe 工具是一种 .NET Core CLI 工具，可从网络位置上的 Web 服务中或从 WSDL 文件中检索元数据。 还可生成与 .NET Core 兼容的源文件并使用可用于访问 Web 服务操作的方法定义 WCF 代理类。

dotnet-svcutil 工具是 [WCF Web 服务引用](wcf-web-service-reference-guide.md) Visual Studio 连接服务提供程序（随 Visual Studio 2017 版本 15.5 首次推出）的替代选项   。 dotnet-svcutil 工具作为一种 .NET Core CLI 工具，可跨平台用于 Linux、macOS 和 Windows  。

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[WCF dotnet-svcutil.xmlserializer 工具](dotnet-svcutil.xmlserializer-guide.md)

在 .NET Framework 中，可以使用 svcutil 工具预生成序列化程序集。 dotnet-svcutil.xmlserializer NuGet 包提供与 .NET Core 上类似的功能。 它为客户端应用程序中 WCF 服务协定使用且可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化的类型预生成 C# 序列化代码。 当序列化或反序列化这些类型的对象时，这会提高 XML 序列化的启动性能。

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML 序列化程序生成器](xml-serializer-generator.md)

正如 [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) 适用于 .NET Framework，[Microsoft.XmlSerializer.Generator NuGet 包](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) 是适用于 .NET Core 和 .NET 标准库的解决方案。 它为程序集中包含的类型创建 XML 序列化程序集，从而提高使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化或反序列化这些类型对象时，XML 序列化的启动性能。
