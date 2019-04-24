---
ms.openlocfilehash: cbe1b32fa40e509f620845866c7a584e37f49a80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774129"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>默认应用域的 TargetFrameworkName 不再默认为 null（如果未设置）

|   |   |
|---|---|
|详细信息|以前，除非显式设置，否则默认应用域中的 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> 为 null。 从 4.6 开始，默认应用域的 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> 属性将具有派生自 TargetFrameworkAttribute 的默认值（如果存在）。 除非显式重写，否则非默认应用域将继续从默认应用域继承 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name>（在 4.6 中不会默认为 null）。|
|建议|应更新代码，以独立于默认为 null 的 <xref:System.AppDomainSetup.TargetFrameworkName>。 如果需要此属性继续评估为 null，它可显式设为该值。|
|范围|边缘|
|版本|4.6|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
