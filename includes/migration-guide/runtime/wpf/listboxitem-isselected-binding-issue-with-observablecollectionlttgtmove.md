---
ms.openlocfilehash: 44cb833fc93caaa79000147421e1c013f755b9cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "68238024"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ObservableCollection&lt;T&gt;.Move 的 ListBoxItem IsSelected 绑定问题

|   |   |
|---|---|
|详细信息|在绑定到有选中项的 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> 的集合上调用 <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> 或 <xref:System.Windows.Controls.ListBox?displayProperty=name> 可能导致未来选择或不选 <xref:System.Windows.Controls.ListBox?displayProperty=name> 项的不稳定行为。|
|建议|调用 <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> 和 <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name>（而不是 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)>）将解决此问题。 此外，此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。|
|范围|次要|
|Version|4.5|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
