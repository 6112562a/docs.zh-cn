---
title: <Type>元素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ffe37540fe089bfd1e0eca1958498e725eb9b5b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049152"
---
# <a name="type-element-net-native"></a><span data-ttu-id="9dd79-102">\<类型 > 元素（.NET Native）</span><span class="sxs-lookup"><span data-stu-id="9dd79-102">\<Type> Element (.NET Native)</span></span>

<span data-ttu-id="9dd79-103">将运行时策略应用到一个特定类型，例如一个类或结构。</span><span class="sxs-lookup"><span data-stu-id="9dd79-103">Applies runtime policy to a particular type, such as a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="9dd79-104">语法</span><span class="sxs-lookup"><span data-stu-id="9dd79-104">Syntax</span></span>

```xml
<Type Name="type_name"
      Activate="policy_type"
      Browse="policy_type"
      Dynamic="policy_type"
      Serialize="policy_type"
      DataContractSerializer="policy_setting"
      DataContractJsonSerializer="policy_setting"
      XmlSerializer="policy_setting"
      MarshalObject="policy_setting"
      MarshalDelegate="policy_setting"
      MarshalStructure="policy_setting" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9dd79-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9dd79-105">Attributes and Elements</span></span>

<span data-ttu-id="9dd79-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9dd79-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9dd79-107">特性</span><span class="sxs-lookup"><span data-stu-id="9dd79-107">Attributes</span></span>

|<span data-ttu-id="9dd79-108">特性</span><span class="sxs-lookup"><span data-stu-id="9dd79-108">Attribute</span></span>|<span data-ttu-id="9dd79-109">特性类型</span><span class="sxs-lookup"><span data-stu-id="9dd79-109">Attribute type</span></span>|<span data-ttu-id="9dd79-110">描述</span><span class="sxs-lookup"><span data-stu-id="9dd79-110">Description</span></span>|
|---------------|--------------------|-----------------|
|`Name`|<span data-ttu-id="9dd79-111">常规</span><span class="sxs-lookup"><span data-stu-id="9dd79-111">General</span></span>|<span data-ttu-id="9dd79-112">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-112">Required attribute.</span></span> <span data-ttu-id="9dd79-113">指定类型名称。</span><span class="sxs-lookup"><span data-stu-id="9dd79-113">Specifies the type name.</span></span>|
|`Activate`|<span data-ttu-id="9dd79-114">映像</span><span class="sxs-lookup"><span data-stu-id="9dd79-114">Reflection</span></span>|<span data-ttu-id="9dd79-115">可选特性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-115">Optional attribute.</span></span> <span data-ttu-id="9dd79-116">控制运行时对构造函数的访问，以启用实例激活。</span><span class="sxs-lookup"><span data-stu-id="9dd79-116">Controls runtime access to constructors to enable activation of instances.</span></span>|
|`Browse`|<span data-ttu-id="9dd79-117">映像</span><span class="sxs-lookup"><span data-stu-id="9dd79-117">Reflection</span></span>|<span data-ttu-id="9dd79-118">可选特性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-118">Optional attribute.</span></span> <span data-ttu-id="9dd79-119">控制对有关程序元素信息的查询，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="9dd79-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|
|`Dynamic`|<span data-ttu-id="9dd79-120">映像</span><span class="sxs-lookup"><span data-stu-id="9dd79-120">Reflection</span></span>|<span data-ttu-id="9dd79-121">可选特性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-121">Optional attribute.</span></span> <span data-ttu-id="9dd79-122">控制运行时对所有类型成员的访问，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="9dd79-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|
|`Serialize`|<span data-ttu-id="9dd79-123">序列化</span><span class="sxs-lookup"><span data-stu-id="9dd79-123">Serialization</span></span>|<span data-ttu-id="9dd79-124">可选特性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-124">Optional attribute.</span></span> <span data-ttu-id="9dd79-125">控制运行时对构造函数、字段和属性的访问，使类型实例得到序列化和反序列化处理，这是通过库进行的，例如 Newtonsoft JSON 序列化程序。</span><span class="sxs-lookup"><span data-stu-id="9dd79-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|
|`DataContractSerializer`|<span data-ttu-id="9dd79-126">序列化</span><span class="sxs-lookup"><span data-stu-id="9dd79-126">Serialization</span></span>|<span data-ttu-id="9dd79-127">可选特性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-127">Optional attribute.</span></span> <span data-ttu-id="9dd79-128">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 类的序列化策略。</span><span class="sxs-lookup"><span data-stu-id="9dd79-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|
|`DataContractJsonSerializer`|<span data-ttu-id="9dd79-129">序列化</span><span class="sxs-lookup"><span data-stu-id="9dd79-129">Serialization</span></span>|<span data-ttu-id="9dd79-130">可选特性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-130">Optional attribute.</span></span> <span data-ttu-id="9dd79-131">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 类的 JSON 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="9dd79-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|
|`XmlSerializer`|<span data-ttu-id="9dd79-132">序列化</span><span class="sxs-lookup"><span data-stu-id="9dd79-132">Serialization</span></span>|<span data-ttu-id="9dd79-133">可选特性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-133">Optional attribute.</span></span> <span data-ttu-id="9dd79-134">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 类的 XML 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="9dd79-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|
|`MarshalObject`|<span data-ttu-id="9dd79-135">Interop</span><span class="sxs-lookup"><span data-stu-id="9dd79-135">Interop</span></span>|<span data-ttu-id="9dd79-136">可选特性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-136">Optional attribute.</span></span> <span data-ttu-id="9dd79-137">控制封送引用类型到 Windows 运行时和 COM 的策略。</span><span class="sxs-lookup"><span data-stu-id="9dd79-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|
|`MarshalDelegate`|<span data-ttu-id="9dd79-138">Interop</span><span class="sxs-lookup"><span data-stu-id="9dd79-138">Interop</span></span>|<span data-ttu-id="9dd79-139">可选特性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-139">Optional attribute.</span></span> <span data-ttu-id="9dd79-140">控制将委托类型作为函数指针封送到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="9dd79-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|
|`MarshalStructure`|<span data-ttu-id="9dd79-141">Interop</span><span class="sxs-lookup"><span data-stu-id="9dd79-141">Interop</span></span>|<span data-ttu-id="9dd79-142">可选特性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-142">Optional attribute.</span></span> <span data-ttu-id="9dd79-143">控制封送处理值类型到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="9dd79-143">Controls policy for marshaling value types to native code.</span></span>|

## <a name="name-attribute"></a><span data-ttu-id="9dd79-144">Name 特性</span><span class="sxs-lookup"><span data-stu-id="9dd79-144">Name attribute</span></span>

|<span data-ttu-id="9dd79-145">值</span><span class="sxs-lookup"><span data-stu-id="9dd79-145">Value</span></span>|<span data-ttu-id="9dd79-146">描述</span><span class="sxs-lookup"><span data-stu-id="9dd79-146">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="9dd79-147">type_name</span><span class="sxs-lookup"><span data-stu-id="9dd79-147">*type_name*</span></span>|<span data-ttu-id="9dd79-148">类型名称。</span><span class="sxs-lookup"><span data-stu-id="9dd79-148">The type name.</span></span> <span data-ttu-id="9dd79-149">如果此 `<Type>` 元素是 [\<Namespace>](namespace-element-net-native.md) 元素或另一个 `<Type>` 元素的子元素，type_name 可能包括类型名称而不包括其命名空间。</span><span class="sxs-lookup"><span data-stu-id="9dd79-149">If this `<Type>` element is the child of either a [\<Namespace>](namespace-element-net-native.md) element or another `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="9dd79-150">否则，type_name 必须包含完全限定的类型名称。</span><span class="sxs-lookup"><span data-stu-id="9dd79-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|

## <a name="all-other-attributes"></a><span data-ttu-id="9dd79-151">所有其他特性</span><span class="sxs-lookup"><span data-stu-id="9dd79-151">All other attributes</span></span>

|<span data-ttu-id="9dd79-152">值</span><span class="sxs-lookup"><span data-stu-id="9dd79-152">Value</span></span>|<span data-ttu-id="9dd79-153">描述</span><span class="sxs-lookup"><span data-stu-id="9dd79-153">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="9dd79-154">policy_setting</span><span class="sxs-lookup"><span data-stu-id="9dd79-154">*policy_setting*</span></span>|<span data-ttu-id="9dd79-155">该设置将应用到这种策略类型。</span><span class="sxs-lookup"><span data-stu-id="9dd79-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="9dd79-156">可能值为 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 以及 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="9dd79-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="9dd79-157">有关详细信息，请参阅[运行时指令策略设置](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="9dd79-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9dd79-158">子元素</span><span class="sxs-lookup"><span data-stu-id="9dd79-158">Child Elements</span></span>

|<span data-ttu-id="9dd79-159">元素</span><span class="sxs-lookup"><span data-stu-id="9dd79-159">Element</span></span>|<span data-ttu-id="9dd79-160">描述</span><span class="sxs-lookup"><span data-stu-id="9dd79-160">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9dd79-161">\<AttributeImplies></span><span class="sxs-lookup"><span data-stu-id="9dd79-161">\<AttributeImplies></span></span>](attributeimplies-element-net-native.md)|<span data-ttu-id="9dd79-162">如果包含类型是一个特性，为该特性所应用到的代码元素定义一个运行时策略。</span><span class="sxs-lookup"><span data-stu-id="9dd79-162">If the containing type is an attribute, defines runtime policy for code elements to which the attribute is applied.</span></span>|
|[<span data-ttu-id="9dd79-163">\<Event></span><span class="sxs-lookup"><span data-stu-id="9dd79-163">\<Event></span></span>](event-element-net-native.md)|<span data-ttu-id="9dd79-164">将反射策略应用到属于这种类型的一个事件。</span><span class="sxs-lookup"><span data-stu-id="9dd79-164">Applies reflection policy to an event belonging to this type.</span></span>|
|[<span data-ttu-id="9dd79-165">\<Field></span><span class="sxs-lookup"><span data-stu-id="9dd79-165">\<Field></span></span>](field-element-net-native.md)|<span data-ttu-id="9dd79-166">将反射策略应用到属于这种类型的一个字段。</span><span class="sxs-lookup"><span data-stu-id="9dd79-166">Applies reflection policy to a field belonging to this type.</span></span>|
|[<span data-ttu-id="9dd79-167">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="9dd79-167">\<GenericParameter></span></span>](genericparameter-element-net-native.md)|<span data-ttu-id="9dd79-168">将策略应用到一个泛型类型的参数类型。</span><span class="sxs-lookup"><span data-stu-id="9dd79-168">Applies policy to the parameter type of a generic type.</span></span>|
|[<span data-ttu-id="9dd79-169">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="9dd79-169">\<ImpliesType></span></span>](impliestype-element-net-native.md)|<span data-ttu-id="9dd79-170">如果该策略已应用到以包含 `<Type>` 元素为代表的类型，将该策略应用到一个类型。</span><span class="sxs-lookup"><span data-stu-id="9dd79-170">Applies policy to a type, if that policy has been applied to the type represented by the containing `<Type>` element.</span></span>|
|[<span data-ttu-id="9dd79-171">\<Method></span><span class="sxs-lookup"><span data-stu-id="9dd79-171">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="9dd79-172">将反射策略应用到属于这种类型的一个方法。</span><span class="sxs-lookup"><span data-stu-id="9dd79-172">Applies reflection policy to a method belonging to this type.</span></span>|
|[<span data-ttu-id="9dd79-173">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="9dd79-173">\<MethodInstantiation></span></span>](methodinstantiation-element-net-native.md)|<span data-ttu-id="9dd79-174">将反射策略应用到属于这种类型的一个构造泛型方法。</span><span class="sxs-lookup"><span data-stu-id="9dd79-174">Applies reflection policy to a constructed generic method belonging to this type.</span></span>|
|[<span data-ttu-id="9dd79-175">\<Property></span><span class="sxs-lookup"><span data-stu-id="9dd79-175">\<Property></span></span>](property-element-net-native.md)|<span data-ttu-id="9dd79-176">将反射策略应用到属于这种类型的一个属性。</span><span class="sxs-lookup"><span data-stu-id="9dd79-176">Applies reflection policy to a property belonging to this type.</span></span>|
|[<span data-ttu-id="9dd79-177">\<Subtypes></span><span class="sxs-lookup"><span data-stu-id="9dd79-177">\<Subtypes></span></span>](subtypes-element-net-native.md)|<span data-ttu-id="9dd79-178">将运行时策略应用到从包含类型继承的所有类。</span><span class="sxs-lookup"><span data-stu-id="9dd79-178">Applies runtime policy to all classes inherited from the containing type.</span></span>|
|`<Type>`|<span data-ttu-id="9dd79-179">将反射策略应用到一个嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="9dd79-179">Applies reflection policy to a nested type.</span></span>|
|[<span data-ttu-id="9dd79-180">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="9dd79-180">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="9dd79-181">将反射策略应用到一个构造泛型类型。</span><span class="sxs-lookup"><span data-stu-id="9dd79-181">Applies reflection policy to a constructed generic type.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9dd79-182">父元素</span><span class="sxs-lookup"><span data-stu-id="9dd79-182">Parent Elements</span></span>

|<span data-ttu-id="9dd79-183">元素</span><span class="sxs-lookup"><span data-stu-id="9dd79-183">Element</span></span>|<span data-ttu-id="9dd79-184">描述</span><span class="sxs-lookup"><span data-stu-id="9dd79-184">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9dd79-185">\<Application></span><span class="sxs-lookup"><span data-stu-id="9dd79-185">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="9dd79-186">作为应用程序范围内的类型和元数据可以反应在运行时间的类型成员的容器而服务。</span><span class="sxs-lookup"><span data-stu-id="9dd79-186">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span>|
|[<span data-ttu-id="9dd79-187">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="9dd79-187">\<Assembly></span></span>](assembly-element-net-native.md)|<span data-ttu-id="9dd79-188">将反射策略应用到指定程序集中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="9dd79-188">Applies reflection policy to all the types in a specified assembly.</span></span>|
|[<span data-ttu-id="9dd79-189">\<Library></span><span class="sxs-lookup"><span data-stu-id="9dd79-189">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="9dd79-190">定义包含元数据在运行时间可以用于反射的类型和类型成员的程序集。</span><span class="sxs-lookup"><span data-stu-id="9dd79-190">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>|
|[<span data-ttu-id="9dd79-191">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="9dd79-191">\<Namespace></span></span>](namespace-element-net-native.md)|<span data-ttu-id="9dd79-192">将反射策略应用到命名空间中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="9dd79-192">Applies reflection policy to all the types in a namespace.</span></span>|
|`<Type>`|<span data-ttu-id="9dd79-193">将反射策略应用到一种类型及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="9dd79-193">Applies reflection policy to a type and all its members.</span></span>|
|[<span data-ttu-id="9dd79-194">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="9dd79-194">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="9dd79-195">将反射策略应用到一种构造泛型类型及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="9dd79-195">Applies reflection policy to a constructed generic type and all its members.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9dd79-196">备注</span><span class="sxs-lookup"><span data-stu-id="9dd79-196">Remarks</span></span>

<span data-ttu-id="9dd79-197">反射、序列化和互操作特性都是可选项。</span><span class="sxs-lookup"><span data-stu-id="9dd79-197">The reflection, serialization, and interop attributes are all optional.</span></span> <span data-ttu-id="9dd79-198">如果这些都不存在，`<Type>` 元素会充当容器，其子类型为独立成员定义策略。</span><span class="sxs-lookup"><span data-stu-id="9dd79-198">If none are present, the `<Type>` element serves as a container whose child types define policy for individual members.</span></span>

<span data-ttu-id="9dd79-199">如果一个 `<Type>` 元素是 [\<Assembly>](assembly-element-net-native.md)、[\<Namespace>](namespace-element-net-native.md)、`<Type>` 或 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 元素的子元素，它会替代由父元素定义的策略设置。</span><span class="sxs-lookup"><span data-stu-id="9dd79-199">If a `<Type>` element is the child of an [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), `<Type>`, or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element, it overrides the policy settings defined by the parent element.</span></span>

<span data-ttu-id="9dd79-200">一个泛型类型的 `<Type>` 元素会将其策略应用到所有不具有自身策略的实例化。</span><span class="sxs-lookup"><span data-stu-id="9dd79-200">A `<Type>` element of a generic type applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="9dd79-201">构造泛型类型的策略是由 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 元素定义的。</span><span class="sxs-lookup"><span data-stu-id="9dd79-201">The policy of constructed generic types is defined by the [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>

<span data-ttu-id="9dd79-202">如果该类型是一个泛型类型，其名称包含一个重读音符 (\`)，后面还跟着其泛型参数的编号。</span><span class="sxs-lookup"><span data-stu-id="9dd79-202">If the type is a generic type, its name is decorated by a grave accent symbol (\`) followed by its number of generic parameters.</span></span> <span data-ttu-id="9dd79-203">例如，`Name` 的 `<Type>` 元素 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 特性为 ``Name="System.Collections.Generic.List`1"``。</span><span class="sxs-lookup"><span data-stu-id="9dd79-203">For example, the `Name` attribute of a `<Type>` element for the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class appears as ``Name="System.Collections.Generic.List`1"``.</span></span>

## <a name="example"></a><span data-ttu-id="9dd79-204">示例</span><span class="sxs-lookup"><span data-stu-id="9dd79-204">Example</span></span>

<span data-ttu-id="9dd79-205">以下实例使用反射来展示 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 类的字段、属性和方法。</span><span class="sxs-lookup"><span data-stu-id="9dd79-205">The following example uses reflection to display information about the fields, properties, and methods of the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="9dd79-206">示例中`b`的变量是一个<xref:Windows.UI.Xaml.Controls.TextBlock>控件。</span><span class="sxs-lookup"><span data-stu-id="9dd79-206">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span> <span data-ttu-id="9dd79-207">因为实例仅仅检索了类型信息，元数据的可用性是由 `Browse` 策略设置控制的。</span><span class="sxs-lookup"><span data-stu-id="9dd79-207">Because the example simply retrieves type information, the availability of metadata is controlled by the `Browse` policy setting.</span></span>

 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]

 <span data-ttu-id="9dd79-208">由于<xref:System.Collections.Generic.List%601>类的元数据不会由 .NET Native 工具链自动包含，因此该示例在运行时无法显示请求的成员信息。</span><span class="sxs-lookup"><span data-stu-id="9dd79-208">Because metadata for the <xref:System.Collections.Generic.List%601> class isn't automatically included by the .NET Native tool chain, the example fails to display the requested member information at run time.</span></span> <span data-ttu-id="9dd79-209">为提供所需的元数据，将以下 `<Type>` 元素添加到运行时指令文件。</span><span class="sxs-lookup"><span data-stu-id="9dd79-209">To provide the necessary metadata, add the following `<Type>` element to the runtime directives file.</span></span> <span data-ttu-id="9dd79-210">注意，因为我们已经提供了父 [<Namespace\>](namespace-element-net-native.md) 元素，因此不必在 `<Type>` 元素中提供完全限定的类型名称。</span><span class="sxs-lookup"><span data-stu-id="9dd79-210">Note that, because we've provided a parent [<Namespace\>](namespace-element-net-native.md) element, we don't have to provide a fully qualified type name in the `<Type>` element.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="*Application*" Dynamic="Required All" />
      <Namespace Name ="System.Collections.Generic" >
        <Type Name="List`1" Browse="Required All" />
     </Namespace>
   </Application>
</Directives>
```

## <a name="example"></a><span data-ttu-id="9dd79-211">示例</span><span class="sxs-lookup"><span data-stu-id="9dd79-211">Example</span></span>
 <span data-ttu-id="9dd79-212">以下实例使用了反射来检索一个代表 <xref:System.Reflection.PropertyInfo> 属性的 <xref:System.String.Chars%2A?displayProperty=nameWithType> 对象。</span><span class="sxs-lookup"><span data-stu-id="9dd79-212">The following example uses reflection to retrieve a <xref:System.Reflection.PropertyInfo> object that represents the <xref:System.String.Chars%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9dd79-213">它使用 <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法来检索一个字符串中的七个字符的值，并在该字符串中显示所有字符。</span><span class="sxs-lookup"><span data-stu-id="9dd79-213">It then uses the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method to retrieve the value of the seventh character in a string, and to display all the characters in the string.</span></span> <span data-ttu-id="9dd79-214">示例中`b`的变量是一个<xref:Windows.UI.Xaml.Controls.TextBlock>控件。</span><span class="sxs-lookup"><span data-stu-id="9dd79-214">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>

 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]

 <span data-ttu-id="9dd79-215">由于<xref:System.String>对象的元数据不可用，因此在使用 .NET Native <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>工具链编译<xref:System.NullReferenceException>时，对方法的调用会在运行时引发异常。</span><span class="sxs-lookup"><span data-stu-id="9dd79-215">Because metadata for the <xref:System.String> object isn't available, the call to the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method throws a <xref:System.NullReferenceException> exception at run time when compiled with the .NET Native tool chain.</span></span> <span data-ttu-id="9dd79-216">要消除异常并提供必需的元数据，请将以下 `<Type>` 元素添加到运行时指令文件：</span><span class="sxs-lookup"><span data-stu-id="9dd79-216">To eliminate the exception and provide the necessary metadata, add the following `<Type>` element to the runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
    <Type Name="System.String" Dynamic="Required Public"/> -->
  </Application>
</Directives>
```

## <a name="see-also"></a><span data-ttu-id="9dd79-217">请参阅</span><span class="sxs-lookup"><span data-stu-id="9dd79-217">See also</span></span>

- [<span data-ttu-id="9dd79-218">运行时指令 (rd.xml) 配置文件参考</span><span class="sxs-lookup"><span data-stu-id="9dd79-218">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9dd79-219">运行时指令元素</span><span class="sxs-lookup"><span data-stu-id="9dd79-219">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="9dd79-220">运行时指令策略设置</span><span class="sxs-lookup"><span data-stu-id="9dd79-220">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
