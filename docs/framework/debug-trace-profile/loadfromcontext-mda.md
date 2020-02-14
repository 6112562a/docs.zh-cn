---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 28ef6e12c82cf5ca56962756b9ea964d0ae9baaa
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216161"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="03c14-102">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="03c14-102">loadFromContext MDA</span></span>
<span data-ttu-id="03c14-103">如果程序集加载到 `loadFromContext` 上下文，将激活 `LoadFrom` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="03c14-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="03c14-104">这种情况可能由于调用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 或其他类似方法而发生。</span><span class="sxs-lookup"><span data-stu-id="03c14-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="03c14-105">症状</span><span class="sxs-lookup"><span data-stu-id="03c14-105">Symptoms</span></span>  
 <span data-ttu-id="03c14-106">使用某些加载器方法可能导致在 `LoadFrom` 上下文中加载程序集。</span><span class="sxs-lookup"><span data-stu-id="03c14-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="03c14-107">使用此上下文可能导致序列化、转换和依赖项解析出现意外的行为。</span><span class="sxs-lookup"><span data-stu-id="03c14-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="03c14-108">通常，建议将程序集加载到 `Load` 上下文来避免这些问题。</span><span class="sxs-lookup"><span data-stu-id="03c14-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="03c14-109">如果没有此 MDA，很难确定程序集加载到了哪个上下文。</span><span class="sxs-lookup"><span data-stu-id="03c14-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="03c14-110">原因</span><span class="sxs-lookup"><span data-stu-id="03c14-110">Cause</span></span>  
 <span data-ttu-id="03c14-111">通常，如果从 `LoadFrom` 上下文外部的路径加载程序集（例如全局程序集缓存或 `Load` 属性），则会将程序集加载到 <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> 上下文。</span><span class="sxs-lookup"><span data-stu-id="03c14-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="03c14-112">解决方法</span><span class="sxs-lookup"><span data-stu-id="03c14-112">Resolution</span></span>  
 <span data-ttu-id="03c14-113">配置应用程序使其不再需要 <xref:System.Reflection.Assembly.LoadFrom%2A> 调用。</span><span class="sxs-lookup"><span data-stu-id="03c14-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="03c14-114">可以使用以下技术进行此操作：</span><span class="sxs-lookup"><span data-stu-id="03c14-114">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="03c14-115">在全局程序集缓存中安装程序集。</span><span class="sxs-lookup"><span data-stu-id="03c14-115">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="03c14-116">将程序集放在 <xref:System.AppDomainSetup.ApplicationBase%2A> 的 <xref:System.AppDomain> 目录。</span><span class="sxs-lookup"><span data-stu-id="03c14-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="03c14-117">如果采用默认域，<xref:System.AppDomainSetup.ApplicationBase%2A> 目录是包含启动该进程的可执行文件的目录。</span><span class="sxs-lookup"><span data-stu-id="03c14-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="03c14-118">如果不方便移动程序集，可能还需要创建新的 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="03c14-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="03c14-119">将探测路径添加到应用程序配置 (.config) 文件，如果依赖程序集位于可执行文件相对的子目录，则添加到辅助应用程序域。</span><span class="sxs-lookup"><span data-stu-id="03c14-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="03c14-120">每种情况下，均可将代码更改为使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="03c14-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="03c14-121">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="03c14-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="03c14-122">MDA 对 CLR 没有任何影响。</span><span class="sxs-lookup"><span data-stu-id="03c14-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="03c14-123">它报告由于加载请求而使用的上下文。</span><span class="sxs-lookup"><span data-stu-id="03c14-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="03c14-124">输出</span><span class="sxs-lookup"><span data-stu-id="03c14-124">Output</span></span>  
 <span data-ttu-id="03c14-125">MDA 报告程序集已加载到 `LoadFrom` 上下文。</span><span class="sxs-lookup"><span data-stu-id="03c14-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="03c14-126">它指定程序集的简单名称和路径。</span><span class="sxs-lookup"><span data-stu-id="03c14-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="03c14-127">它还建议避免使用 `LoadFrom` 上下文来减轻风险。</span><span class="sxs-lookup"><span data-stu-id="03c14-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="03c14-128">配置</span><span class="sxs-lookup"><span data-stu-id="03c14-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="03c14-129">示例</span><span class="sxs-lookup"><span data-stu-id="03c14-129">Example</span></span>  
 <span data-ttu-id="03c14-130">以下代码示例展示了一种可激活该 MDA 的情况：</span><span class="sxs-lookup"><span data-stu-id="03c14-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```csharp
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is   
            // located outside of the Load context probing path.   
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="03c14-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03c14-131">See also</span></span>

- [<span data-ttu-id="03c14-132">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="03c14-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
