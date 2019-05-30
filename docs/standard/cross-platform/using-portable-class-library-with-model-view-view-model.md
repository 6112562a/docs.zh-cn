---
title: 将可移植类库与模型-视图-视图模型配合使用
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a8c2b6ca9701f5eec4a8f43eaae531a0cfc18c1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377720"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="038b2-102">将可移植类库与模型-视图-视图模型配合使用</span><span class="sxs-lookup"><span data-stu-id="038b2-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="038b2-103">可以使用.NET Framework[可移植类库](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)实现模型-视图-视图模型 (MVVM) 模式并跨多个平台共享程序集。</span><span class="sxs-lookup"><span data-stu-id="038b2-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="038b2-104">MVVM 是将用户界面与基础业务逻辑相隔离的应用程序模式。</span><span class="sxs-lookup"><span data-stu-id="038b2-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="038b2-105">您可以实现中的模型和视图模型类[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]项目在 Visual Studio 2012 中，然后创建针对不同平台自定义的视图。</span><span class="sxs-lookup"><span data-stu-id="038b2-105">You can implement the model and view model classes in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="038b2-106">通过此方法，只需编写数据模型和业务逻辑一次，即可将该代码用于 .NET Framework、Silverlight、Windows Phone 和 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 应用，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="038b2-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, as shown in the following illustration.</span></span>

 ![显示跨平台可移植类库与 MVVM 共享程序集。](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="038b2-108">本主题不提供有关 MVVM 模式的一般信息。</span><span class="sxs-lookup"><span data-stu-id="038b2-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="038b2-109">它仅提供有关如何使用信息[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]来实现 MVVM。</span><span class="sxs-lookup"><span data-stu-id="038b2-109">It only provides information about how to use [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] to implement MVVM.</span></span> <span data-ttu-id="038b2-110">有关 MVVM 的详细信息，请参阅[MVVM 快速入门使用 Prism Library 5.0 的 WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40))。</span><span class="sxs-lookup"><span data-stu-id="038b2-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="038b2-111">支持 MVVM 类</span><span class="sxs-lookup"><span data-stu-id="038b2-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="038b2-112">如果面向.NET Framework 4.5 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]，Silverlight 或 Windows Phone 7.5 的你[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]项目中，下列类是可用于实现 MVVM 模式：</span><span class="sxs-lookup"><span data-stu-id="038b2-112">When you target the .NET Framework 4.5, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="038b2-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="038b2-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="038b2-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="038b2-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="038b2-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="038b2-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="038b2-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="038b2-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="038b2-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="038b2-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="038b2-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="038b2-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="038b2-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="038b2-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="038b2-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="038b2-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="038b2-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="038b2-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="038b2-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="038b2-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="038b2-123">中的所有类<xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>命名空间</span><span class="sxs-lookup"><span data-stu-id="038b2-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="038b2-124">实现 MVVM</span><span class="sxs-lookup"><span data-stu-id="038b2-124">Implementing MVVM</span></span>
 <span data-ttu-id="038b2-125">若要实现 MVVM，您通常创建模型和视图模型中的[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]项目，因为[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]项目不能引用不可移植的项目。</span><span class="sxs-lookup"><span data-stu-id="038b2-125">To implement MVVM, you typically create both the model and the view model in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, because a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project cannot reference a non-portable project.</span></span> <span data-ttu-id="038b2-126">模型和视图模型可以是同一个项目中或单独的项目中。</span><span class="sxs-lookup"><span data-stu-id="038b2-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="038b2-127">如果使用单独的项目，添加从视图模型项目到模型项目的引用。</span><span class="sxs-lookup"><span data-stu-id="038b2-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="038b2-128">编译模型并查看模型项目后，您引用的包含视图的应用中的这些程序集。</span><span class="sxs-lookup"><span data-stu-id="038b2-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="038b2-129">如果该视图仅与视图模型进行交互，只需引用包含视图模型的程序集。</span><span class="sxs-lookup"><span data-stu-id="038b2-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="038b2-130">模型</span><span class="sxs-lookup"><span data-stu-id="038b2-130">Model</span></span>
 <span data-ttu-id="038b2-131">下面的示例演示可驻留在简化的模型类[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]项目。</span><span class="sxs-lookup"><span data-stu-id="038b2-131">The following example shows a simplified model class that could reside in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="038b2-132">下面的示例演示填充、 检索和更新中的数据的简单方法[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]项目。</span><span class="sxs-lookup"><span data-stu-id="038b2-132">The following example shows a simple way to populate, retrieve, and update the data in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span> <span data-ttu-id="038b2-133">在实际应用中，将从 Windows Communication Foundation (WCF) 服务等源检索数据。</span><span class="sxs-lookup"><span data-stu-id="038b2-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="038b2-134">视图模型</span><span class="sxs-lookup"><span data-stu-id="038b2-134">View Model</span></span>
 <span data-ttu-id="038b2-135">在实现 MVVM 模式时，经常添加的视图模型的基类。</span><span class="sxs-lookup"><span data-stu-id="038b2-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="038b2-136">下面的示例显示了一个基类。</span><span class="sxs-lookup"><span data-stu-id="038b2-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="038b2-137">实现<xref:System.Windows.Input.ICommand>接口经常采用 MVVM 模式。</span><span class="sxs-lookup"><span data-stu-id="038b2-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="038b2-138">下面的示例演示 <xref:System.Windows.Input.ICommand> 接口的实现。</span><span class="sxs-lookup"><span data-stu-id="038b2-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="038b2-139">下面的示例显示了一个简化的视图模型。</span><span class="sxs-lookup"><span data-stu-id="038b2-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="038b2-140">视图</span><span class="sxs-lookup"><span data-stu-id="038b2-140">View</span></span>  
 <span data-ttu-id="038b2-141">从.NET Framework 4.5 应用程序，[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]应用、 基于 Silverlight 的应用或 Windows Phone 7.5 应用程序，可以引用包含模型和视图模型项目的程序集。</span><span class="sxs-lookup"><span data-stu-id="038b2-141">From a .NET Framework 4.5 app, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="038b2-142">您然后创建视图模型进行交互的视图。</span><span class="sxs-lookup"><span data-stu-id="038b2-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="038b2-143">下面的示例演示一个简化的 Windows Presentation Foundation (WPF) 应用检索和更新视图模型中的数据。</span><span class="sxs-lookup"><span data-stu-id="038b2-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="038b2-144">可以在 Silverlight 中，Windows Phone 创建类似的视图或[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]应用。</span><span class="sxs-lookup"><span data-stu-id="038b2-144">You could create similar views in Silverlight, Windows Phone, or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="038b2-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="038b2-145">See also</span></span>

- [<span data-ttu-id="038b2-146">可移植类库</span><span class="sxs-lookup"><span data-stu-id="038b2-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
