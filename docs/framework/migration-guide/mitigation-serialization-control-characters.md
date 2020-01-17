---
title: 使用 DataContractJsonSerializer 对控制字符进行序列化
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: 209f7827e61ef72de1d64fad46dc9f241fa6edef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346576"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="7ecb5-102">缓解：使用 DataContractJsonSerializer 对控制字符进行序列化</span><span class="sxs-lookup"><span data-stu-id="7ecb5-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="7ecb5-103">自 .NET Framework 4.7 起，使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 对控制字符进行序列化的方式已更改为与 ECMAScript V6 和 V8 兼容。</span><span class="sxs-lookup"><span data-stu-id="7ecb5-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="7ecb5-104">影响</span><span class="sxs-lookup"><span data-stu-id="7ecb5-104">Impact</span></span>

<span data-ttu-id="7ecb5-105">在 .NET framework 4.6.2 及更低版本中，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 未按与 ECMAScript V6 和 V8 标准兼容的方式对一些特殊控制字符（如 `\b`、`\f` 和 `\t`）进行序列化。</span><span class="sxs-lookup"><span data-stu-id="7ecb5-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="7ecb5-106">对于定位 .NET Framework 4.7 及更高版本的应用程序，这些控制字符的序列化与 ECMAScript V6 和 V8 兼容。</span><span class="sxs-lookup"><span data-stu-id="7ecb5-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="7ecb5-107">以下 API 受到影响：</span><span class="sxs-lookup"><span data-stu-id="7ecb5-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="7ecb5-108">缓解</span><span class="sxs-lookup"><span data-stu-id="7ecb5-108">Mitigation</span></span>

<span data-ttu-id="7ecb5-109">对于定位 .NET Framework 4.7 及更高版本的应用程序，此行为默认启用。</span><span class="sxs-lookup"><span data-stu-id="7ecb5-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="7ecb5-110">如果不需要此行为，可以在 app.config 或 web.config 文件的 `<runtime>` 部分中添加下面的代码行，从而选择禁用此功能：</span><span class="sxs-lookup"><span data-stu-id="7ecb5-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="7ecb5-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="7ecb5-111">See also</span></span>

- [<span data-ttu-id="7ecb5-112">应用程序兼容性</span><span class="sxs-lookup"><span data-stu-id="7ecb5-112">Application compatibility</span></span>](application-compatibility.md)
