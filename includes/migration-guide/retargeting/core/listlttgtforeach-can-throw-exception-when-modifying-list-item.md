---
ms.openlocfilehash: 4e81087431091dfa4d5432d5ea5e2b665be2b130
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774297"
---
### <a name="listtforeach-can-throw-exception-when-modifying-list-item"></a>List\<T>.ForEach 在修改列表项时可能会抛出异常

|   |   |
|---|---|
|详细信息|从 .NET Framework 4.5 开始，如果修改了调用集合中的元素，<xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> 枚举器将引发 <xref:System.InvalidOperationException?displayProperty=name> 异常。 该操作在以前不会引发异常，但可能会导致争用条件。|
|建议|理想情况下，应修复代码以便在枚举列表元素时不会修改列表，因为这始终不是安全操作。 但是，若要还原到以前的行为，应用可面向 .NET Framework 4.0。|
|范围|边缘|
|版本|4.5|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|
