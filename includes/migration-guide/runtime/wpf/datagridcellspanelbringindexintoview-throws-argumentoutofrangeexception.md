---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802472"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView 引发 ArgumentOutOfRangeException

|   |   |
|---|---|
|详细信息|启用列虚拟化但尚未确定列宽时，<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 将以异步方式执行工作。  如果在异步工作执行之前删除列，可能会出现 <xref:System.ArgumentOutOfRangeException?displayProperty=name>。|
|建议|以下任一项：<ol><li>升级到 .NET Framework 4.7。</li><li>安装 .NET Framework 4.6.2 的最新服务修补程序。</li><li>在对 <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 的异步响应完成前，避免删除列。</li></ol>|
|范围|边缘|
|Version|4.6.2|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
