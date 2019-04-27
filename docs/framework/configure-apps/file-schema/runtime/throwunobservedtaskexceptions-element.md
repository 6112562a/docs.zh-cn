---
title: <ThrowUnobservedTaskExceptions> 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdce2181490d32212cd2629e98267e43bbe0d334
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673994"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="b04d5-102">\<ThrowUnobservedTaskExceptions > 元素</span><span class="sxs-lookup"><span data-stu-id="b04d5-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="b04d5-103">指定未经处理的任务异常是否应终止正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="b04d5-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="b04d5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b04d5-104">\<configuration></span></span>  
<span data-ttu-id="b04d5-105">\<运行时 ></span><span class="sxs-lookup"><span data-stu-id="b04d5-105">\<runtime></span></span>  
<span data-ttu-id="b04d5-106">\<ThrowUnobservedTaskExceptions></span><span class="sxs-lookup"><span data-stu-id="b04d5-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04d5-107">语法</span><span class="sxs-lookup"><span data-stu-id="b04d5-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b04d5-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b04d5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b04d5-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b04d5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b04d5-110">特性</span><span class="sxs-lookup"><span data-stu-id="b04d5-110">Attributes</span></span>  
  
|<span data-ttu-id="b04d5-111">特性</span><span class="sxs-lookup"><span data-stu-id="b04d5-111">Attribute</span></span>|<span data-ttu-id="b04d5-112">描述</span><span class="sxs-lookup"><span data-stu-id="b04d5-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b04d5-113">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="b04d5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b04d5-114">指定未经处理的任务异常是否应终止正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="b04d5-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b04d5-115">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="b04d5-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="b04d5-116">“值”</span><span class="sxs-lookup"><span data-stu-id="b04d5-116">Value</span></span>|<span data-ttu-id="b04d5-117">描述</span><span class="sxs-lookup"><span data-stu-id="b04d5-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b04d5-118">不会终止正在运行的进程的未经处理的任务异常。</span><span class="sxs-lookup"><span data-stu-id="b04d5-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="b04d5-119">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="b04d5-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b04d5-120">终止正在运行的进程的未经处理的任务异常。</span><span class="sxs-lookup"><span data-stu-id="b04d5-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b04d5-121">子元素</span><span class="sxs-lookup"><span data-stu-id="b04d5-121">Child Elements</span></span>  
 <span data-ttu-id="b04d5-122">无。</span><span class="sxs-lookup"><span data-stu-id="b04d5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b04d5-123">父元素</span><span class="sxs-lookup"><span data-stu-id="b04d5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b04d5-124">元素</span><span class="sxs-lookup"><span data-stu-id="b04d5-124">Element</span></span>|<span data-ttu-id="b04d5-125">描述</span><span class="sxs-lookup"><span data-stu-id="b04d5-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b04d5-126">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="b04d5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b04d5-127">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="b04d5-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="b04d5-128">备注</span><span class="sxs-lookup"><span data-stu-id="b04d5-128">Remarks</span></span>  
 <span data-ttu-id="b04d5-129">如果与关联的异常<xref:System.Threading.Tasks.Task>未观察，没有任何<xref:System.Threading.Tasks.Task.Wait%2A>未附加操作，父级，和<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType>属性未读取任务异常被视为未观察到。</span><span class="sxs-lookup"><span data-stu-id="b04d5-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="b04d5-130">在中[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，也可由默认情况下，如果<xref:System.Threading.Tasks.Task>具有未观察到异常进行垃圾收集，终结器引发异常，并终止进程。</span><span class="sxs-lookup"><span data-stu-id="b04d5-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="b04d5-131">终止进程取决于垃圾回收和终止的时间。</span><span class="sxs-lookup"><span data-stu-id="b04d5-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="b04d5-132">为了简化开发人员能够编写基于任务的异步代码[!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]更改此默认行为为未观察到异常。</span><span class="sxs-lookup"><span data-stu-id="b04d5-132">To make it easier for developers to write asynchronous code based on tasks, the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="b04d5-133">未观察到的异常仍会导致<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>事件被引发，但默认情况下，该过程不会终止。</span><span class="sxs-lookup"><span data-stu-id="b04d5-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="b04d5-134">相反，该异常被忽略后引发该事件，而不考虑是否将事件处理程序观察异常。</span><span class="sxs-lookup"><span data-stu-id="b04d5-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="b04d5-135">在中[!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]，可以使用[ \<ThrowUnobservedTaskExceptions > 元素](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)若要启用应用程序配置文件中[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]引发异常的行为。</span><span class="sxs-lookup"><span data-stu-id="b04d5-135">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="b04d5-136">此外可以通过以下方式之一中指定的异常行为：</span><span class="sxs-lookup"><span data-stu-id="b04d5-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
-   <span data-ttu-id="b04d5-137">通过设置环境变量`COMPlus_ThrowUnobservedTaskExceptions`(`set COMPlus_ThrowUnobservedTaskExceptions=1`)。</span><span class="sxs-lookup"><span data-stu-id="b04d5-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
-   <span data-ttu-id="b04d5-138">通过设置注册表 DWORD 值 ThrowUnobservedTaskExceptions = 1 在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\。NETFramework 键。</span><span class="sxs-lookup"><span data-stu-id="b04d5-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b04d5-139">示例</span><span class="sxs-lookup"><span data-stu-id="b04d5-139">Example</span></span>  
 <span data-ttu-id="b04d5-140">下面的示例演示如何启用任务中的异常引发使用应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="b04d5-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="b04d5-141">示例</span><span class="sxs-lookup"><span data-stu-id="b04d5-141">Example</span></span>  
 <span data-ttu-id="b04d5-142">下面的示例演示如何从任务引发未观察到的异常。</span><span class="sxs-lookup"><span data-stu-id="b04d5-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="b04d5-143">作为已发布的程序才能正常工作，必须运行代码。</span><span class="sxs-lookup"><span data-stu-id="b04d5-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b04d5-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="b04d5-144">See also</span></span>

- [<span data-ttu-id="b04d5-145">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="b04d5-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="b04d5-146">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="b04d5-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
