---
title: x:Subclass 指令
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: 850fe8acf9e47149bd385e78b30e04ba77d7a8b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140785"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="60948-102">x:Subclass 指令</span><span class="sxs-lookup"><span data-stu-id="60948-102">x:Subclass Directive</span></span>
<span data-ttu-id="60948-103">修改 XAML 标记编译行为时`x:Class`还提供了。</span><span class="sxs-lookup"><span data-stu-id="60948-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="60948-104">而不是创建的分部类的基于`x:Class`，提供`x:Class`中间类，作为创建，然后在提供的派生的类需基于`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="60948-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="60948-105">XAML 属性用法</span><span class="sxs-lookup"><span data-stu-id="60948-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="60948-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="60948-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`namespace`|<span data-ttu-id="60948-107">可选。</span><span class="sxs-lookup"><span data-stu-id="60948-107">Optional.</span></span> <span data-ttu-id="60948-108">指定一个包含的 CLR 命名空间`classname`。</span><span class="sxs-lookup"><span data-stu-id="60948-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="60948-109">如果`namespace`指定一个点 （.） 分隔`namespace`和`classname`。</span><span class="sxs-lookup"><span data-stu-id="60948-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|  
|`classname`|<span data-ttu-id="60948-110">必需。</span><span class="sxs-lookup"><span data-stu-id="60948-110">Required.</span></span> <span data-ttu-id="60948-111">指定连接加载的 XAML 和代码隐藏中为该 XAML 的分部类的 CLR 名称。</span><span class="sxs-lookup"><span data-stu-id="60948-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="60948-112">请参阅“备注”。</span><span class="sxs-lookup"><span data-stu-id="60948-112">See Remarks.</span></span>|  
|`subclassNamespace`|<span data-ttu-id="60948-113">可选。</span><span class="sxs-lookup"><span data-stu-id="60948-113">Optional.</span></span> <span data-ttu-id="60948-114">可以不同于`namespace`如果每个命名空间可以解析其他。</span><span class="sxs-lookup"><span data-stu-id="60948-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="60948-115">指定一个包含的 CLR 命名空间`subclassName`。</span><span class="sxs-lookup"><span data-stu-id="60948-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="60948-116">如果`subclassName`指定一个点 （.） 分隔`subclassNamespace`和`subclassName`。</span><span class="sxs-lookup"><span data-stu-id="60948-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|  
|`subclassName`|<span data-ttu-id="60948-117">必需。</span><span class="sxs-lookup"><span data-stu-id="60948-117">Required.</span></span> <span data-ttu-id="60948-118">指定子类的 CLR 名称。</span><span class="sxs-lookup"><span data-stu-id="60948-118">Specifies the CLR name of the subclass.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="60948-119">依赖项</span><span class="sxs-lookup"><span data-stu-id="60948-119">Dependencies</span></span>  
 <span data-ttu-id="60948-120">[X:class 指令](x-class-directive.md)还必须提供对同一对象，并且该对象必须是 XAML 生产的根元素。</span><span class="sxs-lookup"><span data-stu-id="60948-120">[x:Class Directive](x-class-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60948-121">备注</span><span class="sxs-lookup"><span data-stu-id="60948-121">Remarks</span></span>  
 `x:Subclass` <span data-ttu-id="60948-122">使用情况主要适用于不支持分部类声明的语言。</span><span class="sxs-lookup"><span data-stu-id="60948-122">usage is primarily intended for languages that do not support partial class declarations.</span></span>  
  
 <span data-ttu-id="60948-123">类用作`x:Subclass`不能为嵌套的类和`x:Subclass`必须引用根对象中的"依赖关系"部分所述。</span><span class="sxs-lookup"><span data-stu-id="60948-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>  
  
 <span data-ttu-id="60948-124">否则为概念的含义`x:Subclass`未定义的由.NET Framework XAML 服务实现。</span><span class="sxs-lookup"><span data-stu-id="60948-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET Framework XAML Services implementation.</span></span> <span data-ttu-id="60948-125">这是因为.NET Framework XAML 服务行为未指定的 XAML 的标记和备份代码已连接的总体编程模型。</span><span class="sxs-lookup"><span data-stu-id="60948-125">This is because .NET Framework XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="60948-126">与相关的更多概念实现`x:Class`和`x:Subclass`执行的特定框架所使用的编程模型或应用程序模型来定义如何连接 XAML 标记、 编译的标记和基于 CLR 的代码隐藏。</span><span class="sxs-lookup"><span data-stu-id="60948-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="60948-127">每个框架都可能具有其自己启用某些行为或必须包含在生成环境中的特定组件的生成操作。</span><span class="sxs-lookup"><span data-stu-id="60948-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="60948-128">在框架中，生成操作也可因特定 CLR 语言用于代码隐藏。</span><span class="sxs-lookup"><span data-stu-id="60948-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="60948-129">WPF 用法说明</span><span class="sxs-lookup"><span data-stu-id="60948-129">WPF Usage Notes</span></span>  
 `x:Subclass` <span data-ttu-id="60948-130">可以是页面根元素上或在<xref:System.Windows.Application>在应用程序定义中，其中已经有根`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="60948-130">can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="60948-131">声明`x:Subclass`之外的页面或应用程序的根，或在不指定它的任何元素`x:Class`存在，则会导致编译时错误。</span><span class="sxs-lookup"><span data-stu-id="60948-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>  
  
 <span data-ttu-id="60948-132">创建派生类，这些类为正确`x:Subclass`方案是相当复杂。</span><span class="sxs-lookup"><span data-stu-id="60948-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="60948-133">您可能需要检查的中间文件 （你的项目的 obj 文件夹中生成的标记编译，其名称合并.xaml 文件名称的.g 文件）。</span><span class="sxs-lookup"><span data-stu-id="60948-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="60948-134">这些中间文件可以帮助您确定的源的已编译的应用程序中的联接分部类中的某些编程构造。</span><span class="sxs-lookup"><span data-stu-id="60948-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>  
  
 <span data-ttu-id="60948-135">在派生类中的事件处理程序必须以`internal override`(`Friend Overrides` Microsoft Visual Basic 中) 若要在编译期间创建中间类中重写的处理程序存根。</span><span class="sxs-lookup"><span data-stu-id="60948-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="60948-136">否则为派生的类实现隐藏） 的中间类实现，并且不调用中间类处理程序。</span><span class="sxs-lookup"><span data-stu-id="60948-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>  
  
 <span data-ttu-id="60948-137">同时定义何时`x:Class`并`x:Subclass`，不需要提供的类的引用的任何实现`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="60948-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="60948-138">只需为其提供通过名称`x:Class`属性，以便编译器具有中间文件 （编译器不会选择一个默认名称在这种情况下） 中创建的类的一些指导。</span><span class="sxs-lookup"><span data-stu-id="60948-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="60948-139">可让`x:Class`类实现; 但是，这不是同时使用这二者的典型情景`x:Class`和`x:Subclass`。</span><span class="sxs-lookup"><span data-stu-id="60948-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60948-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="60948-140">See also</span></span>

- [<span data-ttu-id="60948-141">x:Class 指令</span><span class="sxs-lookup"><span data-stu-id="60948-141">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="60948-142">XAML 及 WPF 的自定义类</span><span class="sxs-lookup"><span data-stu-id="60948-142">XAML and Custom Classes for WPF</span></span>](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
