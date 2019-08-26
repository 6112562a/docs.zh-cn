---
title: 互操作封送处理
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, COM interop
- interop marshaling
- interop marshaling, about interop marshaling
ms.assetid: 115f7a2f-d422-4605-ab36-13a8dd28142a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20766f4f7971d8aa304c7c3eead94f089f059d64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946707"
---
# <a name="interop-marshaling"></a><span data-ttu-id="b7307-102">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="b7307-102">Interop Marshaling</span></span>
<a name="top"></a> <span data-ttu-id="b7307-103">互操作封送处理控制调用期间，通过方法自变量和返回值在托管内存和非托管内存之间传递数据的方式。</span><span class="sxs-lookup"><span data-stu-id="b7307-103">Interop marshaling governs how data is passed in method arguments and return values between managed and unmanaged memory during calls.</span></span> <span data-ttu-id="b7307-104">互操作封送处理是由公共语言运行时的封送处理服务执行的运行时活动。</span><span class="sxs-lookup"><span data-stu-id="b7307-104">Interop marshaling is a run-time activity performed by the common language runtime's marshaling service.</span></span>  
  
 <span data-ttu-id="b7307-105">大多数数据类型在托管和非托管内存中都具有公共的表示形式。</span><span class="sxs-lookup"><span data-stu-id="b7307-105">Most data types have common representations in both managed and unmanaged memory.</span></span> <span data-ttu-id="b7307-106">互操作封送拆收器为你处理这些类型。</span><span class="sxs-lookup"><span data-stu-id="b7307-106">The interop marshaler handles these types for you.</span></span> <span data-ttu-id="b7307-107">其他类型可能是不明确的，或根本不在托管内存中表示。</span><span class="sxs-lookup"><span data-stu-id="b7307-107">Other types can be ambiguous or not represented at all in managed memory.</span></span>  
  
 <span data-ttu-id="b7307-108">不明确的类型可能具有多种映射到单个托管类型的非托管表示形式，或者可能缺少类型信息（如数组的大小）。</span><span class="sxs-lookup"><span data-stu-id="b7307-108">An ambiguous type can have either multiple unmanaged representations that map to a single managed type, or missing type information, such as the size of an array.</span></span> <span data-ttu-id="b7307-109">对于不明确的类型，封送拆收器提供默认表示形式和替换表示形式（如果存在多种表示形式）。</span><span class="sxs-lookup"><span data-stu-id="b7307-109">For ambiguous types, the marshaler provides a default representation and alternative representations where multiple representations exist.</span></span> <span data-ttu-id="b7307-110">可以向封送拆收器提供有关它如何封送不明确类型的显式指令。</span><span class="sxs-lookup"><span data-stu-id="b7307-110">You can supply explicit instructions to the marshaler on how it is to marshal an ambiguous type.</span></span>  
  
 <span data-ttu-id="b7307-111">本概述包含以下几节：</span><span class="sxs-lookup"><span data-stu-id="b7307-111">This overview contains the following sections:</span></span>  
  
- [<span data-ttu-id="b7307-112">平台调用和 COM 互操作模型</span><span class="sxs-lookup"><span data-stu-id="b7307-112">Platform Invoke and COM Interop Models</span></span>](#platform_invoke_and_com_interop_models)  
  
- [<span data-ttu-id="b7307-113">封送和 COM 单元</span><span class="sxs-lookup"><span data-stu-id="b7307-113">Marshaling and COM Apartments</span></span>](#marshaling_and_com_apartments)  
  
- [<span data-ttu-id="b7307-114">封送远程调用</span><span class="sxs-lookup"><span data-stu-id="b7307-114">Marshaling Remote Calls</span></span>](#marshaling_remote_calls)  
  
- [<span data-ttu-id="b7307-115">相关主题</span><span class="sxs-lookup"><span data-stu-id="b7307-115">Related Topics</span></span>](#related_topics)  
  
- [<span data-ttu-id="b7307-116">引用</span><span class="sxs-lookup"><span data-stu-id="b7307-116">Reference</span></span>](#reference)  
  
<a name="platform_invoke_and_com_interop_models"></a>   
## <a name="platform-invoke-and-com-interop-models"></a><span data-ttu-id="b7307-117">平台调用和 COM 互操作模型</span><span class="sxs-lookup"><span data-stu-id="b7307-117">Platform Invoke and COM Interop Models</span></span>  
 <span data-ttu-id="b7307-118">公共语言运行时提供两种用于与非托管代码进行交互的机制：</span><span class="sxs-lookup"><span data-stu-id="b7307-118">The common language runtime provides two mechanisms for interoperating with unmanaged code:</span></span>  
  
- <span data-ttu-id="b7307-119">平台调用，它使托管代码能够调用从非托管库中导出的函数。</span><span class="sxs-lookup"><span data-stu-id="b7307-119">Platform invoke, which enables managed code to call functions exported from an unmanaged library.</span></span>  
  
- <span data-ttu-id="b7307-120">COM 互操作，它使托管代码能够通过接口与组件对象模型 (COM) 对象交互。</span><span class="sxs-lookup"><span data-stu-id="b7307-120">COM interop, which enables managed code to interact with Component Object Model (COM) objects through interfaces.</span></span>  
  
 <span data-ttu-id="b7307-121">平台调用和 COM 互操作都使用互操作封送处理在调用方和被调用方之间准确地移动方法参数，并且如果需要，也可以将数据从被调用方移回调用方。</span><span class="sxs-lookup"><span data-stu-id="b7307-121">Both platform invoke and COM interop use interop marshaling to accurately move method arguments between caller and callee and back, if required.</span></span> <span data-ttu-id="b7307-122">正如下图所示，除涉及 [回调函数](callback-functions.md) 以外，平台调用方法调用从托管代码流向非托管代码，而绝不会以相反方向流动。</span><span class="sxs-lookup"><span data-stu-id="b7307-122">As the following illustration shows, a platform invoke method call flows from managed to unmanaged code and never the other way, except when [callback functions](callback-functions.md) are involved.</span></span> <span data-ttu-id="b7307-123">虽然平台调用的调用只能从托管代码流向非托管代码，但是数据仍然可以作为输入参数或输出参数在两个方向流动。</span><span class="sxs-lookup"><span data-stu-id="b7307-123">Even though platform invoke calls can flow only from managed to unmanaged code, data can flow in both directions as input or output parameters.</span></span> <span data-ttu-id="b7307-124">COM 互操作方法调用可以在任一方向流动。</span><span class="sxs-lookup"><span data-stu-id="b7307-124">COM interop method calls can flow in either direction.</span></span>  
  
 <span data-ttu-id="b7307-125">![平台调用](./media/interop-marshaling/interop-marshaling-invoke-and-com.png "平台调用和 COM 互操作调用流")</span><span class="sxs-lookup"><span data-stu-id="b7307-125">![Platform invoke](./media/interop-marshaling/interop-marshaling-invoke-and-com.png "Platform invoke and COM interop call flow")</span></span>  
  
 <span data-ttu-id="b7307-126">在最低级别，这两种机制都使用同一种互操作封送处理服务；不过，某些数据类型则仅受 COM 互操作或平台调用支持。</span><span class="sxs-lookup"><span data-stu-id="b7307-126">At the lowest level, both mechanisms use the same interop marshaling service; however, certain data types are supported exclusively by COM interop or platform invoke.</span></span> <span data-ttu-id="b7307-127">有关详细信息，请参阅 [默认封送行为](default-marshaling-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="b7307-127">For details, see [Default Marshaling Behavior](default-marshaling-behavior.md).</span></span>  
  
 [<span data-ttu-id="b7307-128">返回页首</span><span class="sxs-lookup"><span data-stu-id="b7307-128">Back to top</span></span>](#top)  
  
<a name="marshaling_and_com_apartments"></a>   
## <a name="marshaling-and-com-apartments"></a><span data-ttu-id="b7307-129">封送和 COM 单元</span><span class="sxs-lookup"><span data-stu-id="b7307-129">Marshaling and COM Apartments</span></span>  
 <span data-ttu-id="b7307-130">互操作封送拆收器在公共语言运行时堆和非托管堆之间封送数据。</span><span class="sxs-lookup"><span data-stu-id="b7307-130">The interop marshaler marshals data between the common language runtime heap and the unmanaged heap.</span></span> <span data-ttu-id="b7307-131">每当调用方和被调用方无法操作数据的同一个实例时就发生封送。</span><span class="sxs-lookup"><span data-stu-id="b7307-131">Marshaling occurs whenever the caller and callee cannot operate on the same instance of data.</span></span> <span data-ttu-id="b7307-132">互操作封送拆收器使调用方和被调用方都能够看上去像是在操作同一数据，即使它们都有自己的数据副本。</span><span class="sxs-lookup"><span data-stu-id="b7307-132">The interop marshaler makes it possible for the caller and callee to appear to be operating on the same data even if they have their own copy of the data.</span></span>  
  
 <span data-ttu-id="b7307-133">COM 也有一个在 COM 单元或不同的 COM 进程之间封送数据的封送拆收器。</span><span class="sxs-lookup"><span data-stu-id="b7307-133">COM also has a marshaler that marshals data between COM apartments or different COM processes.</span></span> <span data-ttu-id="b7307-134">当在同一个 COM 单元内的托管和非托管代码之间进行调用时，互操作封送拆收器是涉及到的唯一一个封送拆收器。</span><span class="sxs-lookup"><span data-stu-id="b7307-134">When calling between managed and unmanaged code within the same COM apartment, the interop marshaler is the only marshaler involved.</span></span> <span data-ttu-id="b7307-135">当在另一个 COM 单元或另一个进程中的托管代码和非托管代码之间进行调用时，则同时涉及互操作封送拆收器和 COM 封送拆收器。</span><span class="sxs-lookup"><span data-stu-id="b7307-135">When calling between managed code and unmanaged code in a different COM apartment or a different process, both the interop marshaler and the COM marshaler are involved.</span></span>  
  
### <a name="com-clients-and-managed-servers"></a><span data-ttu-id="b7307-136">COM 客户端和托管服务器</span><span class="sxs-lookup"><span data-stu-id="b7307-136">COM Clients and Managed Servers</span></span>  
 <span data-ttu-id="b7307-137">具有由 [Regasm.exe（程序集注册工具）](../tools/regasm-exe-assembly-registration-tool.md) 注册的类型库的导出的托管服务器有一个设置为 `Both` 的 `ThreadingModel` 注册表项。</span><span class="sxs-lookup"><span data-stu-id="b7307-137">An exported managed server with a type library registered by the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) has a `ThreadingModel` registry entry set to `Both`.</span></span> <span data-ttu-id="b7307-138">此值指示服务器可以在单线程单元 (STA) 或多线程单元 (MTA) 中激活。</span><span class="sxs-lookup"><span data-stu-id="b7307-138">This value indicates that the server can be activated in a single-threaded apartment (STA) or a multithreaded apartment (MTA).</span></span> <span data-ttu-id="b7307-139">服务器对象在与其调用方相同的单元中创建，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="b7307-139">The server object is created in the same apartment as its caller, as shown in the following table.</span></span>  
  
|<span data-ttu-id="b7307-140">COM 客户端</span><span class="sxs-lookup"><span data-stu-id="b7307-140">COM client</span></span>|<span data-ttu-id="b7307-141">.NET 服务器</span><span class="sxs-lookup"><span data-stu-id="b7307-141">.NET server</span></span>|<span data-ttu-id="b7307-142">封送需求</span><span class="sxs-lookup"><span data-stu-id="b7307-142">Marshaling requirements</span></span>|  
|----------------|-----------------|-----------------------------|  
|<span data-ttu-id="b7307-143">STA</span><span class="sxs-lookup"><span data-stu-id="b7307-143">STA</span></span>|<span data-ttu-id="b7307-144">`Both` 将变成 STA。</span><span class="sxs-lookup"><span data-stu-id="b7307-144">`Both` becomes STA.</span></span>|<span data-ttu-id="b7307-145">相同单元封送。</span><span class="sxs-lookup"><span data-stu-id="b7307-145">Same-apartment marshaling.</span></span>|  
|<span data-ttu-id="b7307-146">MTA</span><span class="sxs-lookup"><span data-stu-id="b7307-146">MTA</span></span>|<span data-ttu-id="b7307-147">`Both` 将变成 MTA。</span><span class="sxs-lookup"><span data-stu-id="b7307-147">`Both` becomes MTA.</span></span>|<span data-ttu-id="b7307-148">相同单元封送。</span><span class="sxs-lookup"><span data-stu-id="b7307-148">Same-apartment marshaling.</span></span>|  
  
 <span data-ttu-id="b7307-149">由于客户端和服务器位于同一单元中，因此互操作封送处理服务将自动处理所有数据封送。</span><span class="sxs-lookup"><span data-stu-id="b7307-149">Because the client and server are in the same apartment, the interop marshaling service automatically handles all data marshaling.</span></span> <span data-ttu-id="b7307-150">下图显示了在同一个 COM 样式的单元内的托管和非托管堆之间进行的互操作封送处理服务。</span><span class="sxs-lookup"><span data-stu-id="b7307-150">The following illustration shows the interop marshaling service operating between managed and unmanaged heaps within the same COM-style apartment.</span></span>  
  
 <span data-ttu-id="b7307-151">![托管堆和未托管堆之间的互操作封送处理](./media/interop-marshaling/interop-heaps-managed-and-unmanaged.gif "相同单元封送处理过程")</span><span class="sxs-lookup"><span data-stu-id="b7307-151">![Interop marshaling between managed and unmanaged heaps](./media/interop-marshaling/interop-heaps-managed-and-unmanaged.gif "Same-apartment marshaling process")</span></span>  
  
 <span data-ttu-id="b7307-152">如果计划导出托管服务器，请注意，COM 客户端确定服务器的单元。</span><span class="sxs-lookup"><span data-stu-id="b7307-152">If you plan to export a managed server, be aware that the COM client determines the apartment of the server.</span></span> <span data-ttu-id="b7307-153">在 MTA 中初始化的 COM 客户端所调用的托管服务器必须确保线程安全。</span><span class="sxs-lookup"><span data-stu-id="b7307-153">A managed server called by a COM client initialized in an MTA must ensure thread safety.</span></span>  
  
### <a name="managed-clients-and-com-servers"></a><span data-ttu-id="b7307-154">托管客户端和 COM 服务器</span><span class="sxs-lookup"><span data-stu-id="b7307-154">Managed Clients and COM Servers</span></span>  
 <span data-ttu-id="b7307-155">托管客户端单元的默认设置为 MTA；但是，.NET 客户端的应用程序类型可以更改默认设置。</span><span class="sxs-lookup"><span data-stu-id="b7307-155">The default setting for managed client apartments is MTA; however, the application type of the .NET client can change the default setting.</span></span> <span data-ttu-id="b7307-156">例如，Visual Basic 客户端单元设置为 STA。</span><span class="sxs-lookup"><span data-stu-id="b7307-156">For example, a Visual Basic client apartment setting is STA.</span></span> <span data-ttu-id="b7307-157">可以使用 <xref:System.STAThreadAttribute?displayProperty=nameWithType>、<xref:System.MTAThreadAttribute?displayProperty=nameWithType>、<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> 属性或 <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType> 属性检查并更改托管客户端的单元设置。</span><span class="sxs-lookup"><span data-stu-id="b7307-157">You can use the <xref:System.STAThreadAttribute?displayProperty=nameWithType>, the <xref:System.MTAThreadAttribute?displayProperty=nameWithType>, the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property, or the <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType> property to examine and change the apartment setting of a managed client.</span></span>  
  
 <span data-ttu-id="b7307-158">组件的作者设置 COM 服务器的线程关联。</span><span class="sxs-lookup"><span data-stu-id="b7307-158">The author of the component sets the thread affinity of a COM server.</span></span> <span data-ttu-id="b7307-159">下表显示 .NET 客户端和 COM 服务器的单元设置的组合。</span><span class="sxs-lookup"><span data-stu-id="b7307-159">The following table shows the combinations of apartment settings for .NET clients and COM servers.</span></span> <span data-ttu-id="b7307-160">同时还显示得到的针对这些组合的封送需求。</span><span class="sxs-lookup"><span data-stu-id="b7307-160">It also shows the resulting marshaling requirements for the combinations.</span></span>  
  
|<span data-ttu-id="b7307-161">.NET 客户端</span><span class="sxs-lookup"><span data-stu-id="b7307-161">.NET client</span></span>|<span data-ttu-id="b7307-162">COM 服务器</span><span class="sxs-lookup"><span data-stu-id="b7307-162">COM server</span></span>|<span data-ttu-id="b7307-163">封送需求</span><span class="sxs-lookup"><span data-stu-id="b7307-163">Marshaling requirements</span></span>|  
|-----------------|----------------|-----------------------------|  
|<span data-ttu-id="b7307-164">MTA（默认值）</span><span class="sxs-lookup"><span data-stu-id="b7307-164">MTA (default)</span></span>|<span data-ttu-id="b7307-165">MTA</span><span class="sxs-lookup"><span data-stu-id="b7307-165">MTA</span></span><br /><br /> <span data-ttu-id="b7307-166">STA</span><span class="sxs-lookup"><span data-stu-id="b7307-166">STA</span></span>|<span data-ttu-id="b7307-167">互操作封送处理。</span><span class="sxs-lookup"><span data-stu-id="b7307-167">Interop marshaling.</span></span><br /><br /> <span data-ttu-id="b7307-168">互操作封送处理和 COM 封送处理。</span><span class="sxs-lookup"><span data-stu-id="b7307-168">Interop and COM marshaling.</span></span>|  
|<span data-ttu-id="b7307-169">STA</span><span class="sxs-lookup"><span data-stu-id="b7307-169">STA</span></span>|<span data-ttu-id="b7307-170">MTA</span><span class="sxs-lookup"><span data-stu-id="b7307-170">MTA</span></span><br /><br /> <span data-ttu-id="b7307-171">STA</span><span class="sxs-lookup"><span data-stu-id="b7307-171">STA</span></span>|<span data-ttu-id="b7307-172">互操作封送处理和 COM 封送处理。</span><span class="sxs-lookup"><span data-stu-id="b7307-172">Interop and COM marshaling.</span></span><br /><br /> <span data-ttu-id="b7307-173">互操作封送处理。</span><span class="sxs-lookup"><span data-stu-id="b7307-173">Interop marshaling.</span></span>|  
  
 <span data-ttu-id="b7307-174">当托管客户端和非托管服务器位于同一单元中时，互操作封送处理服务处理所有数据封送。</span><span class="sxs-lookup"><span data-stu-id="b7307-174">When a managed client and unmanaged server are in the same apartment, the interop marshaling service handles all data marshaling.</span></span> <span data-ttu-id="b7307-175">但是，当客户端和服务器在不同的单元中初始化时，还需要 COM 封送处理。</span><span class="sxs-lookup"><span data-stu-id="b7307-175">However, when client and server are initialized in different apartments, COM marshaling is also required.</span></span> <span data-ttu-id="b7307-176">下图显示跨单元调用的元素。</span><span class="sxs-lookup"><span data-stu-id="b7307-176">The following illustration shows the elements of a cross-apartment call.</span></span>  
  
 <span data-ttu-id="b7307-177">![COM 封送处理](./media/interop-marshaling/single-process-across-multi-apartment.gif ".NET 客户端和 COM 对象之间的跨单元调用")</span><span class="sxs-lookup"><span data-stu-id="b7307-177">![COM marshaling](./media/interop-marshaling/single-process-across-multi-apartment.gif "Cross-apartment call between a .NET client and COM object")</span></span>  
  
 <span data-ttu-id="b7307-178">对于跨单元封送，可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="b7307-178">For cross-apartment marshaling, you can do the following:</span></span>  
  
- <span data-ttu-id="b7307-179">接受跨单元封送的系统开销，它只在存在许多跨边界调用时才值得注意。</span><span class="sxs-lookup"><span data-stu-id="b7307-179">Accept the overhead of the cross-apartment marshaling, which is noticeable only when there are many calls across the boundary.</span></span> <span data-ttu-id="b7307-180">若要使调用能够成功跨过单元边界，必须注册 COM 组件的类型库。</span><span class="sxs-lookup"><span data-stu-id="b7307-180">You must register the type library of the COM component for calls to successfully cross the apartment boundary.</span></span>  
  
- <span data-ttu-id="b7307-181">通过将客户端线程设置为 STA 或 MTA 改变主线程。</span><span class="sxs-lookup"><span data-stu-id="b7307-181">Alter the main thread by setting the client thread to STA or MTA.</span></span> <span data-ttu-id="b7307-182">如，如果 C# 客户端调用许多 STA COM 组件，则可以通过将主线程设置为 STA 来避免跨单元封送。</span><span class="sxs-lookup"><span data-stu-id="b7307-182">For example, if your C# client calls many STA COM components, you can avoid cross-apartment marshaling by setting the main thread to STA.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b7307-183">将 C# 客户端的线程设置为 STA 后，对 MTA COM 组件的调用将需要跨单元封送。</span><span class="sxs-lookup"><span data-stu-id="b7307-183">Once the thread of a C# client is set to STA, calls to MTA COM components will require cross-apartment marshaling.</span></span>  
  
 <span data-ttu-id="b7307-184">有关显式选择单元模型的说明， 请参阅 [托管和非托管线程处理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="b7307-184">For instructions on explicitly selecting an apartment model, see [Managed and Unmanaged Threading](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100)).</span></span>  
  
 [<span data-ttu-id="b7307-185">返回页首</span><span class="sxs-lookup"><span data-stu-id="b7307-185">Back to top</span></span>](#top)  
  
<a name="marshaling_remote_calls"></a>   
## <a name="marshaling-remote-calls"></a><span data-ttu-id="b7307-186">封送远程调用</span><span class="sxs-lookup"><span data-stu-id="b7307-186">Marshaling Remote Calls</span></span>  
 <span data-ttu-id="b7307-187">与跨单元封送一样，只要对象驻留在不同的进程中，托管代码和非托管代码之间的每个调用就都涉及 COM 封送处理。</span><span class="sxs-lookup"><span data-stu-id="b7307-187">As with cross-apartment marshaling, COM marshaling is involved in each call between managed and unmanaged code whenever the objects reside in separate processes.</span></span> <span data-ttu-id="b7307-188">例如:</span><span class="sxs-lookup"><span data-stu-id="b7307-188">For example:</span></span>  
  
- <span data-ttu-id="b7307-189">调用远程主机上的托管服务器的 COM 客户端使用分布式 COM (DCOM)。</span><span class="sxs-lookup"><span data-stu-id="b7307-189">A COM client that invokes a managed server on a remote host uses distributed COM (DCOM).</span></span>  
  
- <span data-ttu-id="b7307-190">调用远程主机上的 COM 服务器的托管客户端使用 DCOM。</span><span class="sxs-lookup"><span data-stu-id="b7307-190">A managed client that invokes a COM server on a remote host uses DCOM.</span></span>  
  
 <span data-ttu-id="b7307-191">下图显示互操作封送处理和 COM 封送处理如何跨进程和主机边界提供通信信道。</span><span class="sxs-lookup"><span data-stu-id="b7307-191">The following illustration shows how interop marshaling and COM marshaling provide communications channels across process and host boundaries.</span></span>  
  
 <span data-ttu-id="b7307-192">![COM 封送处理](./media/interop-marshaling/interop-and-com-marshaling.gif "跨进程封送处理")</span><span class="sxs-lookup"><span data-stu-id="b7307-192">![COM marshaling](./media/interop-marshaling/interop-and-com-marshaling.gif "Cross-process marshaling")</span></span>  
  
### <a name="preserving-identity"></a><span data-ttu-id="b7307-193">保留标识</span><span class="sxs-lookup"><span data-stu-id="b7307-193">Preserving Identity</span></span>  
 <span data-ttu-id="b7307-194">公共语言运行时保留托管引用和非托管引用的标识。</span><span class="sxs-lookup"><span data-stu-id="b7307-194">The common language runtime preserves the identity of managed and unmanaged references.</span></span> <span data-ttu-id="b7307-195">下图显示跨进程和主机边界的直接非托管引用（顶部行）和直接托管引用（底部行）的流。</span><span class="sxs-lookup"><span data-stu-id="b7307-195">The following illustration shows the flow of direct unmanaged references (top row) and direct managed references (bottom row) across process and host boundaries.</span></span>  
  
 <span data-ttu-id="b7307-196">![COM 可调用包装器和运行时可调用包装器](./media/interop-marshaling/interop-direct-ref-across-process.gif "跨进程和主机边界传递引用")</span><span class="sxs-lookup"><span data-stu-id="b7307-196">![COM callable wrapper and runtime callable wrapper](./media/interop-marshaling/interop-direct-ref-across-process.gif "Reference passing across process and host boundaries")</span></span>  
  
 <span data-ttu-id="b7307-197">在此图中：</span><span class="sxs-lookup"><span data-stu-id="b7307-197">In this illustration:</span></span>  
  
- <span data-ttu-id="b7307-198">非托管客户端从一个托管对象获取一个对 COM 对象的引用，而该托管对象是从一台远程主机获取该引用的。</span><span class="sxs-lookup"><span data-stu-id="b7307-198">An unmanaged client gets a reference to a COM object from a managed object that gets this reference from a remote host.</span></span> <span data-ttu-id="b7307-199">远程处理机制为 DCOM。</span><span class="sxs-lookup"><span data-stu-id="b7307-199">The remoting mechanism is DCOM.</span></span>  
  
- <span data-ttu-id="b7307-200">托管客户端从一个 COM 对象获取一个对托管对象的引用，而该 COM 对象是从一台远程主机获取该引用的。</span><span class="sxs-lookup"><span data-stu-id="b7307-200">A managed client gets a reference to a managed object from a COM object that gets this reference from a remote host.</span></span> <span data-ttu-id="b7307-201">远程处理机制为 DCOM。</span><span class="sxs-lookup"><span data-stu-id="b7307-201">The remoting mechanism is DCOM.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b7307-202">必须注册该托管服务器的导出类型库。</span><span class="sxs-lookup"><span data-stu-id="b7307-202">The exported type library of the managed server must be registered.</span></span>  
  
 <span data-ttu-id="b7307-203">调用方和被调用方之间的进程边界的数目并不相干；对于进程内和进程外调用都会发生相同的直接引用处理。</span><span class="sxs-lookup"><span data-stu-id="b7307-203">The number of process boundaries between caller and callee is irrelevant; the same direct referencing occurs for in-process and out-of-process calls.</span></span>  
  
### <a name="managed-remoting"></a><span data-ttu-id="b7307-204">托管远程处理</span><span class="sxs-lookup"><span data-stu-id="b7307-204">Managed Remoting</span></span>  
 <span data-ttu-id="b7307-205">运行时还提供了托管远程处理，可用于跨进程和主机边界建立托管对象之间的通信信道。</span><span class="sxs-lookup"><span data-stu-id="b7307-205">The runtime also provides managed remoting, which you can use to establish a communications channel between managed objects across process and host boundaries.</span></span> <span data-ttu-id="b7307-206">托管远程处理可以适应通信组件之间的防火墙，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="b7307-206">Managed remoting can accommodate a firewall between the communicating components, as the following illustration shows.</span></span>  
  
 <span data-ttu-id="b7307-207">![SOAP 或 TcpChannel](./media/interop-marshaling/interop-remote-soap-or-tcp.gif "跨使用 SOAP 或 TcpChannel 类的防火墙的远程调用")</span><span class="sxs-lookup"><span data-stu-id="b7307-207">![SOAP or TcpChannel](./media/interop-marshaling/interop-remote-soap-or-tcp.gif "Remote calls across firewalls using SOAP or the TcpChannel class")</span></span>  
<span data-ttu-id="b7307-208">跨使用 SOAP 或 TcpChannel 类的防火墙的远程调用</span><span class="sxs-lookup"><span data-stu-id="b7307-208">Remote calls across firewalls using SOAP or the TcpChannel class</span></span>  
  
 <span data-ttu-id="b7307-209">某些非托管调用可以通过 SOAP 传递，如服务组件和 COM 之间的调用。</span><span class="sxs-lookup"><span data-stu-id="b7307-209">Some unmanaged calls can be channeled through SOAP, such as the calls between serviced components and COM.</span></span>  
  
 [<span data-ttu-id="b7307-210">返回页首</span><span class="sxs-lookup"><span data-stu-id="b7307-210">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="b7307-211">相关主题</span><span class="sxs-lookup"><span data-stu-id="b7307-211">Related Topics</span></span>  
  
|<span data-ttu-id="b7307-212">Title</span><span class="sxs-lookup"><span data-stu-id="b7307-212">Title</span></span>|<span data-ttu-id="b7307-213">说明</span><span class="sxs-lookup"><span data-stu-id="b7307-213">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b7307-214">默认封送处理行为</span><span class="sxs-lookup"><span data-stu-id="b7307-214">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)|<span data-ttu-id="b7307-215">描述互操作封送处理服务用于封送数据的规则。</span><span class="sxs-lookup"><span data-stu-id="b7307-215">Describes the rules that the interop marshaling service uses to marshal data.</span></span>|  
|[<span data-ttu-id="b7307-216">用平台调用封送数据</span><span class="sxs-lookup"><span data-stu-id="b7307-216">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)|<span data-ttu-id="b7307-217">描述如何声明方法形参以及如何将实参传递给由非托管库导出的函数。</span><span class="sxs-lookup"><span data-stu-id="b7307-217">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>|  
|[<span data-ttu-id="b7307-218">用 COM 互操作对数据进行封送处理</span><span class="sxs-lookup"><span data-stu-id="b7307-218">Marshaling Data with COM Interop</span></span>](marshaling-data-with-com-interop.md)|<span data-ttu-id="b7307-219">描述如何自定义 COM 包装器以更改封送行为。</span><span class="sxs-lookup"><span data-stu-id="b7307-219">Describes how to customize COM wrappers to alter marshaling behavior.</span></span>|  
|[<span data-ttu-id="b7307-220">如何：将托管代码 DCOM 迁移到 WCF</span><span class="sxs-lookup"><span data-stu-id="b7307-220">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)|<span data-ttu-id="b7307-221">描述如何从 DCOM 迁移到 WCF。</span><span class="sxs-lookup"><span data-stu-id="b7307-221">Describes how to migrate from DCOM to WCF.</span></span>|  
|[<span data-ttu-id="b7307-222">如何：映射 HRESULT 和异常</span><span class="sxs-lookup"><span data-stu-id="b7307-222">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)|<span data-ttu-id="b7307-223">描述如何将自定义异常映射到 HRESULT，并提供从每个 HRESULT 到其在 .NET Framework 中的相似异常类的完整映射。</span><span class="sxs-lookup"><span data-stu-id="b7307-223">Describes how to map custom exceptions to HRESULTs and provides the complete mapping from each HRESULT to its comparable exception class in the .NET Framework.</span></span>|  
|<span data-ttu-id="b7307-224">[使用泛型类型进行交互操作](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b7307-224">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>|<span data-ttu-id="b7307-225">描述在使用用于 COM 互操作性的泛型类型时，哪些操作受支持。</span><span class="sxs-lookup"><span data-stu-id="b7307-225">Describes which actions are supported when using generic types for COM interoperability.</span></span>|  
|[<span data-ttu-id="b7307-226">与非托管代码交互操作</span><span class="sxs-lookup"><span data-stu-id="b7307-226">Interoperating with Unmanaged Code</span></span>](index.md)|<span data-ttu-id="b7307-227">描述由公共语言运行时提供的互操作性服务。</span><span class="sxs-lookup"><span data-stu-id="b7307-227">Describes interoperability services provided by the common language runtime.</span></span>|  
|<span data-ttu-id="b7307-228">[高级 COM 互操作性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b7307-228">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>|<span data-ttu-id="b7307-229">提供一些链接，指向关于将 COM 组件并入 .NET Framework 应用程序中的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b7307-229">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>|  
|<span data-ttu-id="b7307-230">[互操作的设计注意事项](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b7307-230">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>|<span data-ttu-id="b7307-231">提供有关编写集成 COM 组件的提示。</span><span class="sxs-lookup"><span data-stu-id="b7307-231">Provides tips for writing integrated COM components.</span></span>|  
  
 [<span data-ttu-id="b7307-232">返回页首</span><span class="sxs-lookup"><span data-stu-id="b7307-232">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="b7307-233">参考</span><span class="sxs-lookup"><span data-stu-id="b7307-233">Reference</span></span>  
 <xref:System.Runtime.InteropServices?displayProperty=nameWithType>  
  
 [<span data-ttu-id="b7307-234">返回页首</span><span class="sxs-lookup"><span data-stu-id="b7307-234">Back to top</span></span>](#top)
