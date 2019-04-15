---
ms.openlocfilehash: 0b087fca59d60a086a9ea8b2bb19c09f646c3dfd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236365"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="0bf37-101">某些 .NET SDK 工具的改进的辅助功能</span><span class="sxs-lookup"><span data-stu-id="0bf37-101">Improved accessibility for some .NET SDK tools</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0bf37-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="0bf37-102">Details</span></span>|<span data-ttu-id="0bf37-103">在 .NET Framework SDK 4.7.1 中，已通过修复各种辅助功能问题，改进了 SvcConfigEditor.exe 和 SvcTraceViewer.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="0bf37-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="0bf37-104">其中大多数都是一些小问题，如未定义名称或未正确实现某些 UI 自动化模式。</span><span class="sxs-lookup"><span data-stu-id="0bf37-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="0bf37-105">虽然许多用户不会意识到这些小问题的重要性，但使用屏幕阅读器等辅助技术的客户会发现这些 SDK 工具更易于访问。</span><span class="sxs-lookup"><span data-stu-id="0bf37-105">While many users wouldn’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="0bf37-106">当然，这些修复程序改变了以前的某些行为，如键盘焦点顺序。为获取这些工具中的所有辅助功能修复程序，可对 app.config 文件执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="0bf37-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="0bf37-107">范围</span><span class="sxs-lookup"><span data-stu-id="0bf37-107">Scope</span></span>|<span data-ttu-id="0bf37-108">边缘</span><span class="sxs-lookup"><span data-stu-id="0bf37-108">Edge</span></span>|
|<span data-ttu-id="0bf37-109">版本</span><span class="sxs-lookup"><span data-stu-id="0bf37-109">Version</span></span>|<span data-ttu-id="0bf37-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="0bf37-110">4.7.1</span></span>|
|<span data-ttu-id="0bf37-111">类型</span><span class="sxs-lookup"><span data-stu-id="0bf37-111">Type</span></span>|<span data-ttu-id="0bf37-112">重定目标</span><span class="sxs-lookup"><span data-stu-id="0bf37-112">Retargeting</span></span>|
