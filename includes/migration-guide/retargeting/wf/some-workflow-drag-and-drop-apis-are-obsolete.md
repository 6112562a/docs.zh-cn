---
ms.openlocfilehash: 297af393e86c65e84ea7271d98eab36dbc6dbb0e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774310"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="965d0-101">某些工作流拖放 API 已过时</span><span class="sxs-lookup"><span data-stu-id="965d0-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="965d0-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="965d0-102">Details</span></span>|<span data-ttu-id="965d0-103">此工作流拖放 API 已过时，如果针对 4.5 重新生成应用，将引发编译器警告。</span><span class="sxs-lookup"><span data-stu-id="965d0-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>|
|<span data-ttu-id="965d0-104">建议</span><span class="sxs-lookup"><span data-stu-id="965d0-104">Suggestion</span></span>|<span data-ttu-id="965d0-105">应改用支持包含多个对象的操作的新 <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> API。</span><span class="sxs-lookup"><span data-stu-id="965d0-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="965d0-106">或者，可以禁止显示生成警告，也可以使用较早的编译器避免出现此类警告。</span><span class="sxs-lookup"><span data-stu-id="965d0-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="965d0-107">API 仍受支持。</span><span class="sxs-lookup"><span data-stu-id="965d0-107">The APIs are still supported.</span></span>|
|<span data-ttu-id="965d0-108">范围</span><span class="sxs-lookup"><span data-stu-id="965d0-108">Scope</span></span>|<span data-ttu-id="965d0-109">次要</span><span class="sxs-lookup"><span data-stu-id="965d0-109">Minor</span></span>|
|<span data-ttu-id="965d0-110">版本</span><span class="sxs-lookup"><span data-stu-id="965d0-110">Version</span></span>|<span data-ttu-id="965d0-111">4.5</span><span class="sxs-lookup"><span data-stu-id="965d0-111">4.5</span></span>|
|<span data-ttu-id="965d0-112">类型</span><span class="sxs-lookup"><span data-stu-id="965d0-112">Type</span></span>|<span data-ttu-id="965d0-113">重定目标</span><span class="sxs-lookup"><span data-stu-id="965d0-113">Retargeting</span></span>|
|<span data-ttu-id="965d0-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="965d0-114">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|
