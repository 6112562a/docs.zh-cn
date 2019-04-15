---
ms.openlocfilehash: 84f570cbbd97be79426e117d4c97ec182a397fd4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235149"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>不应在自定义功能文件中使用 IPad，因为它现在是浏览器功能

|   |   |
|---|---|
|详细信息|自 .NET Framework 4.5 起，iPad 是默认 ASP.NET 浏览器功能文件中的标识符，所以它不应在自定义功能文件中使用|
|建议|如果需要特定于 iPad 的功能，则需要修改 iPad 行为，具体方法为 设置预定义网关 refID &quot;IPad&quot; 上的功能，而不是通过用户代理匹配生成新的 &quot;IPad&quot; ID。|
|范围|边缘|
|版本|4.5|
|类型|运行时|
