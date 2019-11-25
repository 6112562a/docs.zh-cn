---
title: '.NET Framework 4.8、4.7、4.6 和 4.5 的迁移指南 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: 2fa992e1c0897d360f322581888c51dca8d8a734
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974977"
---
# <a name="migration-guide-to-the-net-framework-48-47-46-and-45"></a>.NET Framework 4.8、4.7、4.6 和 4.5 的迁移指南

如果使用之前版本的 .NET Framework 创建了应用，通常可以轻松地将它升级为 .NET Framework 4.5 及其子版本（4.5.1 和 4.5.2）、.NET Framework 4.6 及其子版本（4.6.1 和 4.6.2）、.NET Framework 4.7 及其子版本（4.7.1 和 4.7.2）或者 .NET Framework 4.8。 在 Visual Studio 中打开项目。 如果项目是在之前版本的 Visual Studio 中创建的，则会自动打开“项目兼容性”  对话框。 有关在 Visual Studio 中升级项目的详细信息，请参阅[移植、迁移和升级 Visual Studio 项目](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)和 [Visual Studio 2019 平台目标以及兼容性](/visualstudio/releases/2019/compatibility)。

 但是，.NET Framework 中的某些更改需要更改你的代码。 也可利用 .NET Framework 4.5 及其子版本、.NET Framework 4.6 及其子版本、.NET Framework 4.7 及其子版本或 .NET Framework 4.8 中的新增功能。 通常，针对新版本的 .NET Framework 来对应用进行这些类型的更改的过程称作“迁移”  。 如果不需要迁移应用，可以在 .NET Framework 4.5 或更高版本中运行此应用，无需对其进行重新编译。

## <a name="migration-resources"></a>迁移资源

将应用从之前版本的 .NET Framework 迁移到版本 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 或 4.8 之前，需查看下列文档：

- 请参阅[版本和依赖关系](versions-and-dependencies.md)以了解作为每个 .NET Framework 版本基础的 CLR 版本，并查看成功设定应用目标的指南。

- 查看[应用程序兼容性](application-compatibility.md)以了解可能影响应用的运行时和重定目标更改以及如何处理这些更改。

- 查看[类库中过时的内容](../whats-new/whats-obsolete.md)以确定代码中已过时的任何类型或成员以及建议的备选项。

- 查看[新增功能](../whats-new/index.md)以了解可能需要向应用添加的新功能的说明。

## <a name="see-also"></a>请参阅

- [应用程序兼容性](application-compatibility.md)
- [从 .NET Framework 1.1 迁移](migrating-from-the-net-framework-1-1.md)
- [版本兼容性](version-compatibility.md)
- [版本和依赖关系](versions-and-dependencies.md)
- [如何：将应用配置为支持 .NET Framework 4 或更高版本](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [新增功能](../whats-new/index.md)
- [类库中过时的内容](../whats-new/whats-obsolete.md)
- [.NET Framework 官方支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [.NET Framework 4 迁移问题](net-framework-4-migration-issues.md)
