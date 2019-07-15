---
ms.openlocfilehash: 64d540278544e74c46d46b77c97bccd26d4116dd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803279"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>选择中断以从不同的 4.5 SQL 生成还原到更简单的 4.0 SQL 生成

|   |   |
|---|---|
|详细信息|生成 JOIN 语句并包含对限制操作的调用（无需先使用 OrderBy）的查询现在可以生成更简单的 SQL。 升级到 .NET Framework 4.5 后，这些查询生成了比以前版本更复杂的 SQL。|
|建议|在默认情况下，禁用此功能。 如果实体框架生成可导致性能降低的额外 JOIN 语句，则可以通过将以下项添加到应用程序配置 (app.config) 文件的 <code>&lt;appSettings&gt;</code> 部分来启用此功能：<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|范围|透明|
|Version|4.5.2|
|类型|运行时|

