---
ms.openlocfilehash: 649e4456ef6a11903ab1b390baf56583f31f5562
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760797"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a><span data-ttu-id="6e6db-101">WPF TextBox/PasswordBox 文本选择不遵循系统颜色</span><span class="sxs-lookup"><span data-stu-id="6e6db-101">WPF TextBox/PasswordBox Text Selection Does Not Follow System Colors</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6e6db-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="6e6db-102">Details</span></span>|<span data-ttu-id="6e6db-103">在 .NET Framework 4.7.1 和更早版本中，WPF <code>System.Windows.Controls.TextBox</code> 和 <code>System.Windows.Controls.PasswordBox</code> 只能在装饰器层呈现文本选择。</span><span class="sxs-lookup"><span data-stu-id="6e6db-103">In .NET Framework 4.7.1 and earlier versions, WPF <code>System.Windows.Controls.TextBox</code> and <code>System.Windows.Controls.PasswordBox</code> could only render a text selection in the Adorner layer.</span></span> <span data-ttu-id="6e6db-104">在某些系统主题中，这会遮蔽文本，使其难以阅读。</span><span class="sxs-lookup"><span data-stu-id="6e6db-104">In some system themes this would occlude text, making it hard to read.</span></span>  <span data-ttu-id="6e6db-105">在 .NET Framework 4.7.2 及更高版本中，开发人员可选择启用基于非装饰器的选择呈现方案，从而缓解此问题。</span><span class="sxs-lookup"><span data-stu-id="6e6db-105">In .NET Framework 4.7.2 and later, developers have an option of enabling a non-Adorner-based selection rendering scheme that alleviates this issue.</span></span>|
|<span data-ttu-id="6e6db-106">建议</span><span class="sxs-lookup"><span data-stu-id="6e6db-106">Suggestion</span></span>|<span data-ttu-id="6e6db-107">开发人员若要利用此更改，必须正确设置以下 AppContext 标记。</span><span class="sxs-lookup"><span data-stu-id="6e6db-107">A developer who wants to utilize this change must set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="6e6db-108">若要利用此功能，已安装的 .NET Framework 必须是 4.7.2 或更高版本。若要启用基于非装饰器的选择，请使用以下 AppContext 标记。</span><span class="sxs-lookup"><span data-stu-id="6e6db-108">To utilize this feature, the installed .NET Framework version must be 4.7.2 or greater.To enabled the non-adorner-based selection, use the following AppContext flag.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="6e6db-109">范围</span><span class="sxs-lookup"><span data-stu-id="6e6db-109">Scope</span></span>|<span data-ttu-id="6e6db-110">边缘</span><span class="sxs-lookup"><span data-stu-id="6e6db-110">Edge</span></span>|
|<span data-ttu-id="6e6db-111">版本</span><span class="sxs-lookup"><span data-stu-id="6e6db-111">Version</span></span>|<span data-ttu-id="6e6db-112">4.7.2</span><span class="sxs-lookup"><span data-stu-id="6e6db-112">4.7.2</span></span>|
|<span data-ttu-id="6e6db-113">类型</span><span class="sxs-lookup"><span data-stu-id="6e6db-113">Type</span></span>|<span data-ttu-id="6e6db-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="6e6db-114">Retargeting</span></span>|

