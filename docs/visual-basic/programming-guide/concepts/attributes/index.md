---
title: 特性概述 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: bb012b49c76963306d723d7732b4c7054bf13ebb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968046"
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="ea343-102">特性概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea343-102">Attributes overview (Visual Basic)</span></span>
<span data-ttu-id="ea343-103">使用特性，可以有效地将元数据或声明性信息与代码（程序集、类型、方法、属性等）相关联。</span><span class="sxs-lookup"><span data-stu-id="ea343-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="ea343-104">将特性与程序实体相关联后，可以在运行时使用*反射*这项技术查询特性。</span><span class="sxs-lookup"><span data-stu-id="ea343-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="ea343-105">有关详细信息，请参阅[反射 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="ea343-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="ea343-106">特性具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="ea343-106">Attributes have the following properties:</span></span>  
  
- <span data-ttu-id="ea343-107">特性向程序添加元数据。</span><span class="sxs-lookup"><span data-stu-id="ea343-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="ea343-108">*元数据*是程序中定义的类型的相关信息。</span><span class="sxs-lookup"><span data-stu-id="ea343-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="ea343-109">所有 .NET 程序集都包含一组指定的元数据，用于描述程序集中定义的类型和类型成员。</span><span class="sxs-lookup"><span data-stu-id="ea343-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="ea343-110">可以添加自定义特性来指定所需的其他任何信息。</span><span class="sxs-lookup"><span data-stu-id="ea343-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="ea343-111">有关详细信息，请参阅[创建自定义特性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="ea343-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
- <span data-ttu-id="ea343-112">可以将一个或多个特性应用于整个程序集、模块或较小的程序元素（如类和属性）。</span><span class="sxs-lookup"><span data-stu-id="ea343-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
- <span data-ttu-id="ea343-113">特性可以像方法和属性一样接受自变量。</span><span class="sxs-lookup"><span data-stu-id="ea343-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
- <span data-ttu-id="ea343-114">程序可使用反射来检查自己的元数据或其他程序中的元数据。</span><span class="sxs-lookup"><span data-stu-id="ea343-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="ea343-115">有关详细信息，请参阅[使用反射访问特性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="ea343-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="ea343-116">使用属性</span><span class="sxs-lookup"><span data-stu-id="ea343-116">Using Attributes</span></span>  
 <span data-ttu-id="ea343-117">可以将特性附加到大多数的声明中，尽管特定特性可能会限制可有效附加到的声明的类型。</span><span class="sxs-lookup"><span data-stu-id="ea343-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="ea343-118">在 Visual Basic 中，特性是用尖括号 (\< >) 括起来的。</span><span class="sxs-lookup"><span data-stu-id="ea343-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="ea343-119">特性的后面必须紧接着应用它的元素，且两者必须位于同一代码行。</span><span class="sxs-lookup"><span data-stu-id="ea343-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>  
  
 <span data-ttu-id="ea343-120">在此示例中，<xref:System.SerializableAttribute> 特性用于将具体特征应用于类：</span><span class="sxs-lookup"><span data-stu-id="ea343-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 <span data-ttu-id="ea343-121">下方声明了一个具有特性 <xref:System.Runtime.InteropServices.DllImportAttribute> 的方法：</span><span class="sxs-lookup"><span data-stu-id="ea343-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 <span data-ttu-id="ea343-122">可以将多个特性附加到声明中：</span><span class="sxs-lookup"><span data-stu-id="ea343-122">More than one attribute can be placed on a declaration:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 <span data-ttu-id="ea343-123">对于给定实体，一些特性可以指定多次。</span><span class="sxs-lookup"><span data-stu-id="ea343-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="ea343-124"><xref:System.Diagnostics.ConditionalAttribute> 便属于此类多用途特性：</span><span class="sxs-lookup"><span data-stu-id="ea343-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="ea343-125">按照约定，所有特性名称均以“Attribute”一词结尾，以便与 .NET Framework 中的其他项区分开来。</span><span class="sxs-lookup"><span data-stu-id="ea343-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="ea343-126">不过，在代码中使用特性时，无需指定特性后缀。</span><span class="sxs-lookup"><span data-stu-id="ea343-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="ea343-127">例如，`[DllImport]` 等同于 `[DllImportAttribute]`，但 `DllImportAttribute` 是此特性在 .NET Framework 中的实际名称。</span><span class="sxs-lookup"><span data-stu-id="ea343-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="ea343-128">特性参数</span><span class="sxs-lookup"><span data-stu-id="ea343-128">Attribute Parameters</span></span>  
 <span data-ttu-id="ea343-129">许多属性都有参数，可以是位置参数、未命名参数或已命名参数。</span><span class="sxs-lookup"><span data-stu-id="ea343-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="ea343-130">所有位置参数都必须按特定的顺序指定，不能省略；已命名参数是可选的，可以按任意顺序指定。</span><span class="sxs-lookup"><span data-stu-id="ea343-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="ea343-131">首先指定的是位置参数。</span><span class="sxs-lookup"><span data-stu-id="ea343-131">Positional parameters are specified first.</span></span> <span data-ttu-id="ea343-132">例如，下面这三个特性是等同的：</span><span class="sxs-lookup"><span data-stu-id="ea343-132">For example, these three attributes are equivalent:</span></span>  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 <span data-ttu-id="ea343-133">第一个参数（DLL 名称）是位置参数，始终第一个出现；其他是已命名参数。</span><span class="sxs-lookup"><span data-stu-id="ea343-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="ea343-134">在此示例中，两个已命名参数的默认值均为 false，因此可以省略。</span><span class="sxs-lookup"><span data-stu-id="ea343-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="ea343-135">若要了解默认参数值，请参阅各个特性文档。</span><span class="sxs-lookup"><span data-stu-id="ea343-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="ea343-136">特性目标</span><span class="sxs-lookup"><span data-stu-id="ea343-136">Attribute Targets</span></span>  
 <span data-ttu-id="ea343-137">特性的*目标*是指应用特性的实体。</span><span class="sxs-lookup"><span data-stu-id="ea343-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="ea343-138">例如，特性可应用于类、特定方法或整个程序集。</span><span class="sxs-lookup"><span data-stu-id="ea343-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="ea343-139">默认情况下，特性应用于它后面紧接着的元素。</span><span class="sxs-lookup"><span data-stu-id="ea343-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="ea343-140">不过，还可以进行显式标识。例如，可以标识为将特性应用于方法，还是应用于其参数或返回值。</span><span class="sxs-lookup"><span data-stu-id="ea343-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="ea343-141">若要显式标识特性目标，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="ea343-141">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```vb  
<target : attribute-list>  
```  
  
 <span data-ttu-id="ea343-142">下表列出了可能的 `target` 值。</span><span class="sxs-lookup"><span data-stu-id="ea343-142">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="ea343-143">目标值</span><span class="sxs-lookup"><span data-stu-id="ea343-143">Target value</span></span>|<span data-ttu-id="ea343-144">适用对象</span><span class="sxs-lookup"><span data-stu-id="ea343-144">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="ea343-145">整个程序集</span><span class="sxs-lookup"><span data-stu-id="ea343-145">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="ea343-146">当前的程序集模块（不同于 Visual Basic 模块）</span><span class="sxs-lookup"><span data-stu-id="ea343-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|  
  
 <span data-ttu-id="ea343-147">下面的示例展示了如何将特性应用于程序集和模块。</span><span class="sxs-lookup"><span data-stu-id="ea343-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="ea343-148">有关详细信息，请参阅[常见特性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="ea343-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="ea343-149">特性的常见用途</span><span class="sxs-lookup"><span data-stu-id="ea343-149">Common Uses for Attributes</span></span>  
 <span data-ttu-id="ea343-150">下面列出了代码中特性的一些常见用途：</span><span class="sxs-lookup"><span data-stu-id="ea343-150">The following list includes a few of the common uses of attributes in code:</span></span>  
  
- <span data-ttu-id="ea343-151">在 Web 服务中使用 `WebMethod` 特性标记方法，以指明方法应可通过 SOAP 协议进行调用。</span><span class="sxs-lookup"><span data-stu-id="ea343-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="ea343-152">有关详细信息，请参阅 <xref:System.Web.Services.WebMethodAttribute>。</span><span class="sxs-lookup"><span data-stu-id="ea343-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
- <span data-ttu-id="ea343-153">描述在与本机代码互操作时如何封送方法参数。</span><span class="sxs-lookup"><span data-stu-id="ea343-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="ea343-154">有关详细信息，请参阅 <xref:System.Runtime.InteropServices.MarshalAsAttribute>。</span><span class="sxs-lookup"><span data-stu-id="ea343-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
- <span data-ttu-id="ea343-155">描述类、方法和接口的 COM 属性。</span><span class="sxs-lookup"><span data-stu-id="ea343-155">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
- <span data-ttu-id="ea343-156">使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 类调用非托管代码。</span><span class="sxs-lookup"><span data-stu-id="ea343-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
- <span data-ttu-id="ea343-157">从标题、版本、说明或商标方面描述程序集。</span><span class="sxs-lookup"><span data-stu-id="ea343-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
- <span data-ttu-id="ea343-158">描述要序列化并暂留类的哪些成员。</span><span class="sxs-lookup"><span data-stu-id="ea343-158">Describing which members of a class to serialize for persistence.</span></span>  
  
- <span data-ttu-id="ea343-159">描述如何为了执行 XML 序列化在类成员和 XML 节点之间进行映射。</span><span class="sxs-lookup"><span data-stu-id="ea343-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
- <span data-ttu-id="ea343-160">描述的方法的安全要求。</span><span class="sxs-lookup"><span data-stu-id="ea343-160">Describing the security requirements for methods.</span></span>  
  
- <span data-ttu-id="ea343-161">指定用于强制实施安全规范的特征。</span><span class="sxs-lookup"><span data-stu-id="ea343-161">Specifying characteristics used to enforce security.</span></span>  
  
- <span data-ttu-id="ea343-162">通过实时 (JIT) 编译器控制优化，这样代码就一直都易于调试。</span><span class="sxs-lookup"><span data-stu-id="ea343-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
- <span data-ttu-id="ea343-163">获取方法调用方的相关信息。</span><span class="sxs-lookup"><span data-stu-id="ea343-163">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ea343-164">相关章节</span><span class="sxs-lookup"><span data-stu-id="ea343-164">Related Sections</span></span>  
 <span data-ttu-id="ea343-165">有关详细信息，请参见:</span><span class="sxs-lookup"><span data-stu-id="ea343-165">For more information, see:</span></span>  
  
- [<span data-ttu-id="ea343-166">创建自定义特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea343-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
- [<span data-ttu-id="ea343-167">使用反射访问特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea343-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
- [<span data-ttu-id="ea343-168">如何：创建 C /C++联合使用特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea343-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
- [<span data-ttu-id="ea343-169">常见特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea343-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
- [<span data-ttu-id="ea343-170">调用方信息 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea343-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="ea343-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="ea343-171">See also</span></span>

- [<span data-ttu-id="ea343-172">Visual Basic 编程指南</span><span class="sxs-lookup"><span data-stu-id="ea343-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="ea343-173">反射 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea343-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="ea343-174">属性</span><span class="sxs-lookup"><span data-stu-id="ea343-174">Attributes</span></span>](../../../../standard/attributes/index.md)
