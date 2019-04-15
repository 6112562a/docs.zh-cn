---
ms.openlocfilehash: 0056baa1e5f0cdc5bfcf8b0e83c9490ec5722926
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235197"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>HttpUtility.JavaScriptStringEncode 转义 & 号

|   |   |
|---|---|
|详细信息|自 .NET Framework 4.5 起，<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> 转义 &amp; 符号。|
|建议|如果应用依赖于此方法以前的行为，可将 aspnet:JavaScriptDoNotEncodeAmpersand 设置添加到配置文件中的 [ASP.NET appSettings 元素](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120))。|
|范围|次要|
|版本|4.5|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
