---
ms.openlocfilehash: 705e1a22b8a5791c1103dd374a8bab19356cadfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803262"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF 将不再引发有特定特征的 QueryViews

|   |   |
|---|---|
|详细信息|当应用执行涉及到带有 0..1 导航属性（此属性尝试将相关实体包含为查询的一部分）的查询时，Entity Framework 将不再引发 <xref:System.StackOverflowException?displayProperty=name> 异常。 例如，通过调用 <code>.Include(e =&gt; e.RelatedNavProp)</code>。|
|建议|在运行调用 .Include 的查询时，此更改仅影响使用带有 1-0..1 关系的 QueryViews 的代码。 它可以改善可靠性，并且应该几乎对所有应用透明。 但是，如果它导致意外的行为，你可以通过将以下项添加到应用配置文件的 <code>&lt;appSettings&gt;</code> 部分来禁用它：<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|范围|边缘|
|Version|4.5.2|
|类型|运行时|
