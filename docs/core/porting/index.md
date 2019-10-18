---
title: 将代码从 .NET Framework 移植到 .NET Core
description: 了解移植过程以及发现在将 .NET Framework 项目移植到 .NET Core 时可能有用的工具。
author: cartermp
ms.date: 09/13/2019
ms.custom: seodec18
ms.openlocfilehash: c349f7df3726e7a9814e5ad5e738742ab1bb9ff8
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522983"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a>将代码从 .NET Framework 移植到 .NET Core

如果有在 .NET Framework 上运行的代码，用户也可能会对在 .NET Core 上运行代码感兴趣。 下面提供了移植过程的概述以及在将代码移植到 .NET Core 时可能非常有用的工具列表。

## <a name="overview-of-the-porting-process"></a>移植过程概述

这是我们建议在将项目移植到.NET Core 时采取的过程。 该过程的每个步骤将在以后的文章中详细介绍。

1. 标识并记录第三方依赖项。

   此步骤包含了解什么是第三方依赖项，如何依赖于它们，如何查看它们是否也在 .NET Core 上运行，以及如果没有在其上运行可以采取的步骤。 它还介绍了如何将依赖项迁移到 .NET Core 中使用的 [PackageReference](/nuget/consume-packages/package-references-in-project-files) 格式。

2. 将希望移植的所有项目重定向到目标 .NET Framework 4.7.2 或更高版本。

   此步骤可确保在 .NET Core 不支持特殊 API 的情况下，可以为特定于 .NET Framework 的目标使用备用 API。

3. 使用 [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) 来分析程序集并基于结果制定移植计划。

   API Portability Analyzer 工具分析已编译的程序集并生成报表，该报表将显示高级可移植性摘要和不可用于目标 .NET Core 平台公共图面上的正在使用的每个 API 的细目。 可以使用此报表和代码库的分析结果一起制定移植代码的计划。

4. 将项目文件转换为目标 .NET Core 版本后，可以使用基于 Roslyn 的 [.NET API 分析器](../../standard/analyzers/api-analyzer.md)来确定在一些平台上触发 <xref:System.PlatformNotSupportedException> 的 API 以及一些其他潜在兼容性问题。

5. 移植测试代码。

   由于移植到 .NET Core 对代码库来说是很大的更改，因此强烈建议移植测试代码，以便在移植代码时可以进行测试。 MSTest、xUnit 和 NUnit 都支持 .NET Core。

6. 执行移植计划！

以下列表显示了在移植过程中使用可能有所帮助的工具：

- .NET 可移植性分析器 - [命令行工具](https://github.com/Microsoft/dotnet-apiport/releases)或 [Visual Studio 扩展](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)，一款可就代码在 .NET Framework 与目标 .NET Core 平台之间的可移植性生成报表的工具。 此报表按逐个程序集细分列出了目标 .NET Core 平台上缺少的类型和 API。 有关详细信息，请参阅 [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md)。 建议开始移植之前先运行 .NET 可移植性分析器工具，因为它可帮助确定特定目标 .NET 平台公共图面上缺少的 API 中的任何空白。
- .NET API 分析器 - 一款 Roslyn 分析器，可用于发现在某些平台上引发 <xref:System.PlatformNotSupportedException> 的 .NET Standard API、检测对已弃用的 API 的调用，并发现不同平台上针对 C# API 的潜在兼容性风险。 有关详细信息，请参阅 [.NET API 分析器](../../standard/analyzers/api-analyzer.md)。 在已创建 .NET Core 项目来确定不同平台上的运行时行为差异之后，此分析器非常有用。
- Reverse Package Search - 一个[有用的 Web 服务](https://packagesearch.azurewebsites.net)，能够实现搜索某一类型并找到包含该类型的包。

此外，可以尝试使用 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) 工具将较小的解决方案或单个项目移植到 .NET Core 项目文件格式。

> [!WARNING]
> CsprojToVs2017 是第三方工具。 不能保证它适用于所有项目，而且它可能会导致所依赖的行为发生细微变化。 CsprojToVs2017 应作为一个起点  ，以自动化可自动执行的基本操作。 它不是迁移项目文件格式的有保证的解决方案。

>[!div class="step-by-step"]
>[下一页](net-framework-tech-unavailable.md)
