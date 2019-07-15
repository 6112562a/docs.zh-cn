---
ms.openlocfilehash: f672645fb98f511f7e1326c9c584b287a0fae7dc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859233"
---
### <a name="long-path-support"></a>长路径支持

|   |   |
|---|---|
|详细信息|从面向 .NET Framework 4.6.2 的应用开始，支持长路径（最多 32K 个字符），并删除了 260 个字符（或 <code>MAX_PATH</code>）的路径长度限制。对于经过重新编译以面向 .NET Framework 4.6.2 的应用，之前因路径超过 260 个字符而引发 <xref:System.IO.PathTooLongException?displayProperty=name> 的代码路径，现在仅在以下情况下引发 <xref:System.IO.PathTooLongException?displayProperty=name>：<ul><li>路径长度必须大于 <xref:System.Int16.MaxValue> (32,767) 个字符。</li><li>操作系统返回 <code>COR_E_PATHTOOLONG</code> 或其等同项。</li></ul>对于面向 .NET Framework 4.6.1 及更早版本的应用，只要路径超过 260 个字符，运行时就会自动引发 <xref:System.IO.PathTooLongException?displayProperty=name>。|
|建议|对于面向 .NET Framework 4.6.2 的应用，如果无需长路径支持，可通过将以下内容添加到 <code>app.config</code> 文件的 <code>&lt;runtime&gt;</code> 部分来选择弃用该支持：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>对于面向旧版 .NET Framework，但在 .NET Framework 4.6.2 或更高版本上运行的应用，可通过将以下内容添加到 <code>app.config</code> 文件的 <code>&lt;runtime&gt;</code> 部分来选择启用长路径支持：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|范围|次要|
|版本|4.6.2|
|类型|重定目标|

