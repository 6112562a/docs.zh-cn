---
title: 变量和自变量跟踪
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: 4e59a6838d93a57302f0c894445ab9da5d4252ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625206"
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="02a70-102">变量和自变量跟踪</span><span class="sxs-lookup"><span data-stu-id="02a70-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="02a70-103">当跟踪工作流的执行时，提取数据往往很有用。</span><span class="sxs-lookup"><span data-stu-id="02a70-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="02a70-104">这在访问跟踪记录后续执行时可提供其他上下文。</span><span class="sxs-lookup"><span data-stu-id="02a70-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="02a70-105">在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中，您可以使用跟踪在工作流的任意活动范围内提取所有可见变量或参数。</span><span class="sxs-lookup"><span data-stu-id="02a70-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="02a70-106">跟踪配置文件简化了对数据的提取。</span><span class="sxs-lookup"><span data-stu-id="02a70-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="02a70-107">变量和参数</span><span class="sxs-lookup"><span data-stu-id="02a70-107">Variables and Arguments</span></span>  
 <span data-ttu-id="02a70-108">变量和参数在活动发出 ActivityStateRecord 时提取。</span><span class="sxs-lookup"><span data-stu-id="02a70-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="02a70-109">仅当变量位于活动范围中时，才能提取该变量。</span><span class="sxs-lookup"><span data-stu-id="02a70-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="02a70-110">按如下方式指定将在活动中提取的变量：</span><span class="sxs-lookup"><span data-stu-id="02a70-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
-   <span data-ttu-id="02a70-111">如果变量用变量名称指定，跟踪则在正跟踪的当前活动和父活动中查找变量。</span><span class="sxs-lookup"><span data-stu-id="02a70-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="02a70-112">系统将在当前活动范围和父范围中搜索变量。</span><span class="sxs-lookup"><span data-stu-id="02a70-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
-   <span data-ttu-id="02a70-113">如果要提取的变量使用指定的名称 ="\*"，则提取正跟踪的当前活动中的所有变量。</span><span class="sxs-lookup"><span data-stu-id="02a70-113">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="02a70-114">此种情况下，将不会提取范围中在父活动中定义的变量。</span><span class="sxs-lookup"><span data-stu-id="02a70-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="02a70-115">当提取参数时，提取的参数依赖于活动状态。</span><span class="sxs-lookup"><span data-stu-id="02a70-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="02a70-116">当活动状态为 Executing 时，只能提取 `InArguments`。</span><span class="sxs-lookup"><span data-stu-id="02a70-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="02a70-117">对于任何其他活动状态（Closed、Faulted、Canceled），则可以提取所有参数，即 InArguments 和 OutArguments。</span><span class="sxs-lookup"><span data-stu-id="02a70-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="02a70-118">下面的示例演示用于在发出活动的 `Closed` 跟踪记录时提取变量和参数的活动状态查询。</span><span class="sxs-lookup"><span data-stu-id="02a70-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="02a70-119">变量和参数只能使用 <xref:System.Activities.Tracking.ActivityStateRecord> 来提取，因此使用 <xref:System.Activities.Tracking.ActivityStateQuery> 在跟踪配置文件内进行订阅。</span><span class="sxs-lookup"><span data-stu-id="02a70-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="02a70-120">保护存储在变量和参数中的信息</span><span class="sxs-lookup"><span data-stu-id="02a70-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="02a70-121">默认情况下，跟踪变量或参数对 WF 运行时可见。</span><span class="sxs-lookup"><span data-stu-id="02a70-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="02a70-122">工作流开发人员可以采取以下步骤，阻止访问这些变量或参数：</span><span class="sxs-lookup"><span data-stu-id="02a70-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1.  <span data-ttu-id="02a70-123">对变量的值进行加密。</span><span class="sxs-lookup"><span data-stu-id="02a70-123">Encrypt the value of a variable.</span></span>  
  
2.  <span data-ttu-id="02a70-124">控制跟踪配置文件的创作，以阻止提取变量或参数。</span><span class="sxs-lookup"><span data-stu-id="02a70-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3.  <span data-ttu-id="02a70-125">对于自定义跟踪参与者，请确保 WF 代码不会泄露存储在变量或自变量中的敏感信息。</span><span class="sxs-lookup"><span data-stu-id="02a70-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a70-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="02a70-126">See also</span></span>
- [<span data-ttu-id="02a70-127">Windows Server App Fabric 监视</span><span class="sxs-lookup"><span data-stu-id="02a70-127">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="02a70-128">使用 App Fabric 监视应用程序</span><span class="sxs-lookup"><span data-stu-id="02a70-128">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
