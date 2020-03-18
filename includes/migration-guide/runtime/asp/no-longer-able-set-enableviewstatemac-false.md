---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803234"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>无法再将 EnableViewStateMac 设为 false

|   |   |
|---|---|
|详细信息|ASP.NET 不再允许开发者指定 <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> 或 <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>。 现在，针对所有带嵌入视图状态的请求强制执行视图状态消息身份验证代码 (MAC)。 仅影响将 EnableViewStateMac 属性显式设置为 <code>false</code> 的应用。|
|建议|EnableViewStateMac 必须假设为 true，并且必须解决任何生成的 MAC 错误（如[本指南](https://support.microsoft.com/kb/2915218)所述，该指南包含多种解决方法，具体视引发 MAC 错误的具体原因而定）。|
|范围|主要|
|Version|4.5.2|
|类型|运行时|
