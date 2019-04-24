---
ms.openlocfilehash: d4f22aa41eb7aeffd655d980cb8418649462273e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757737"
---
## <a name="introduction"></a>介绍
重定目标更改影响重新编译为定位不同 .NET Framework 的应用程序。 它们包括：

* 设计时环境的更改。 例如，生成工具可能在之前没有发出警告时发出警告。

* 运行时环境的更改。 它们仅影响专门面向重定目标的 .NET Framework 的应用。 面向之前版本 .NET Framework 的应用的行为与在这些版本下运行时相同。

在介绍重定目标更改的主题中，我们已根据其预期影响为单独的项进行了分类，如下所示：

**主要** 这是显著的更改，可影响大量应用或需要修改大量代码。

**次要** 此更改影响少量应用或需要修改少量代码。

**边缘事例** 此类更改仅在少数非常特定的情况下影响应用。

**透明** 此类更改对应用的开发人员或用户没有明显影响。 不需要由于此更改而修改应用。
