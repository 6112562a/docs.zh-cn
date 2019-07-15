---
ms.openlocfilehash: d7cf32eb369e2607ee540d7188cc680b9506c261
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856955"
---
### <a name="keytips-behavior-improved-in-wpf"></a>WPF 中改进的 Keytip 行为

|   |   |
|---|---|
|详细信息|已修改 Keytip 行为，以便对 Microsoft Word 和 Windows 资源管理器行为进行奇偶校验。 通过在按下 <xref:System.Windows.Input.KeyEventArgs.SystemKey>（特别是 <xref:System.Windows.Input.Key> 或 <xref:System.Windows.Input.Key.F11>）的情况下检查是否启用 keytip 状态，WPF 可正确地处理 keytip 键。 现在，即使是通过鼠标打开的菜单，keytip 也可将其关闭。|
|建议|不可用|
|范围|边缘|
|版本|4.7.2|
|类型|运行时|

