---
title: <GenericParameter>元素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2898d804f7a351045b2fbce42042f9fd322ebb0a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049745"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="50f2f-102">\<泛型参数 > 元素（.NET Native）</span><span class="sxs-lookup"><span data-stu-id="50f2f-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="50f2f-103">将策略应用到一个泛型类型或方法的参数类型。</span><span class="sxs-lookup"><span data-stu-id="50f2f-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50f2f-104">语法</span><span class="sxs-lookup"><span data-stu-id="50f2f-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50f2f-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="50f2f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="50f2f-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="50f2f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50f2f-107">特性</span><span class="sxs-lookup"><span data-stu-id="50f2f-107">Attributes</span></span>  
  
|<span data-ttu-id="50f2f-108">特性</span><span class="sxs-lookup"><span data-stu-id="50f2f-108">Attribute</span></span>|<span data-ttu-id="50f2f-109">特性类型</span><span class="sxs-lookup"><span data-stu-id="50f2f-109">Attribute type</span></span>|<span data-ttu-id="50f2f-110">描述</span><span class="sxs-lookup"><span data-stu-id="50f2f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="50f2f-111">常规</span><span class="sxs-lookup"><span data-stu-id="50f2f-111">General</span></span>|<span data-ttu-id="50f2f-112">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-112">Required attribute.</span></span> <span data-ttu-id="50f2f-113">泛型参数的名称。</span><span class="sxs-lookup"><span data-stu-id="50f2f-113">The name of the generic parameter.</span></span> <span data-ttu-id="50f2f-114">例如，对于泛型委托 <xref:System.Func%603>，`Name` 特性的值为“TResult”，从而将运行时策略应用到该委托的返回值。</span><span class="sxs-lookup"><span data-stu-id="50f2f-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="50f2f-115">映像</span><span class="sxs-lookup"><span data-stu-id="50f2f-115">Reflection</span></span>|<span data-ttu-id="50f2f-116">可选特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-116">Optional attribute.</span></span> <span data-ttu-id="50f2f-117">控制运行时对构造函数的访问，以启用实例激活。</span><span class="sxs-lookup"><span data-stu-id="50f2f-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="50f2f-118">映像</span><span class="sxs-lookup"><span data-stu-id="50f2f-118">Reflection</span></span>|<span data-ttu-id="50f2f-119">可选特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-119">Optional attribute.</span></span> <span data-ttu-id="50f2f-120">控制对有关程序元素信息的查询，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="50f2f-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="50f2f-121">映像</span><span class="sxs-lookup"><span data-stu-id="50f2f-121">Reflection</span></span>|<span data-ttu-id="50f2f-122">可选特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-122">Optional attribute.</span></span> <span data-ttu-id="50f2f-123">控制运行时对所有类型成员的访问，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="50f2f-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="50f2f-124">序列化</span><span class="sxs-lookup"><span data-stu-id="50f2f-124">Serialization</span></span>|<span data-ttu-id="50f2f-125">可选特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-125">Optional attribute.</span></span> <span data-ttu-id="50f2f-126">控制运行时对构造函数、字段和属性的访问，使类型实例得到序列化和反序列化处理，这是通过库进行的，例如 Newtonsoft JSON 序列化程序。</span><span class="sxs-lookup"><span data-stu-id="50f2f-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="50f2f-127">序列化</span><span class="sxs-lookup"><span data-stu-id="50f2f-127">Serialization</span></span>|<span data-ttu-id="50f2f-128">可选特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-128">Optional attribute.</span></span> <span data-ttu-id="50f2f-129">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 类的序列化策略。</span><span class="sxs-lookup"><span data-stu-id="50f2f-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="50f2f-130">序列化</span><span class="sxs-lookup"><span data-stu-id="50f2f-130">Serialization</span></span>|<span data-ttu-id="50f2f-131">可选特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-131">Optional attribute.</span></span> <span data-ttu-id="50f2f-132">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 类的 JSON 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="50f2f-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="50f2f-133">序列化</span><span class="sxs-lookup"><span data-stu-id="50f2f-133">Serialization</span></span>|<span data-ttu-id="50f2f-134">可选特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-134">Optional attribute.</span></span> <span data-ttu-id="50f2f-135">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 类的 XML 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="50f2f-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="50f2f-136">Interop</span><span class="sxs-lookup"><span data-stu-id="50f2f-136">Interop</span></span>|<span data-ttu-id="50f2f-137">可选特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-137">Optional attribute.</span></span> <span data-ttu-id="50f2f-138">控制封送引用类型到 Windows 运行时和 COM 的策略。</span><span class="sxs-lookup"><span data-stu-id="50f2f-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="50f2f-139">Interop</span><span class="sxs-lookup"><span data-stu-id="50f2f-139">Interop</span></span>|<span data-ttu-id="50f2f-140">可选特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-140">Optional attribute.</span></span> <span data-ttu-id="50f2f-141">控制将委托类型作为函数指针封送到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="50f2f-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="50f2f-142">Interop</span><span class="sxs-lookup"><span data-stu-id="50f2f-142">Interop</span></span>|<span data-ttu-id="50f2f-143">可选特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-143">Optional attribute.</span></span> <span data-ttu-id="50f2f-144">控制封送处理值类型到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="50f2f-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="50f2f-145">Name 特性</span><span class="sxs-lookup"><span data-stu-id="50f2f-145">Name attribute</span></span>  
  
|<span data-ttu-id="50f2f-146">值</span><span class="sxs-lookup"><span data-stu-id="50f2f-146">Value</span></span>|<span data-ttu-id="50f2f-147">描述</span><span class="sxs-lookup"><span data-stu-id="50f2f-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50f2f-148">generic_parameter_name</span><span class="sxs-lookup"><span data-stu-id="50f2f-148">*generic_parameter_name*</span></span>|<span data-ttu-id="50f2f-149">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="50f2f-149">Required attribute.</span></span> <span data-ttu-id="50f2f-150">泛型类型参数的名称。</span><span class="sxs-lookup"><span data-stu-id="50f2f-150">The name of the generic type parameter.</span></span> <span data-ttu-id="50f2f-151">例如，对于泛型委托 <xref:System.Func%603>，“TResult”的一个 generic_parameter_name 值将运行时策略应用到该委托的返回值。</span><span class="sxs-lookup"><span data-stu-id="50f2f-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="50f2f-152">所有其他特性</span><span class="sxs-lookup"><span data-stu-id="50f2f-152">All other attributes</span></span>  
  
|<span data-ttu-id="50f2f-153">值</span><span class="sxs-lookup"><span data-stu-id="50f2f-153">Value</span></span>|<span data-ttu-id="50f2f-154">描述</span><span class="sxs-lookup"><span data-stu-id="50f2f-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50f2f-155">policy_setting</span><span class="sxs-lookup"><span data-stu-id="50f2f-155">*policy_setting*</span></span>|<span data-ttu-id="50f2f-156">该设置将应用到这种策略类型。</span><span class="sxs-lookup"><span data-stu-id="50f2f-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="50f2f-157">可能值为 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 以及 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="50f2f-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="50f2f-158">有关详细信息，请参阅[运行时指令策略设置](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="50f2f-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50f2f-159">子元素</span><span class="sxs-lookup"><span data-stu-id="50f2f-159">Child Elements</span></span>  
 <span data-ttu-id="50f2f-160">无。</span><span class="sxs-lookup"><span data-stu-id="50f2f-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50f2f-161">父元素</span><span class="sxs-lookup"><span data-stu-id="50f2f-161">Parent Elements</span></span>  
  
|<span data-ttu-id="50f2f-162">元素</span><span class="sxs-lookup"><span data-stu-id="50f2f-162">Element</span></span>|<span data-ttu-id="50f2f-163">描述</span><span class="sxs-lookup"><span data-stu-id="50f2f-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50f2f-164">\<Method></span><span class="sxs-lookup"><span data-stu-id="50f2f-164">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="50f2f-165">将运行时反射策略应用到一个构造函数或方法。</span><span class="sxs-lookup"><span data-stu-id="50f2f-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="50f2f-166">\<Type></span><span class="sxs-lookup"><span data-stu-id="50f2f-166">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="50f2f-167">将运行时反射策略应用到一个特定类型，例如一个类或结构。</span><span class="sxs-lookup"><span data-stu-id="50f2f-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50f2f-168">备注</span><span class="sxs-lookup"><span data-stu-id="50f2f-168">Remarks</span></span>  
 <span data-ttu-id="50f2f-169">`<GenericParameter>` 元素是 [\<Method>](method-element-net-native.md) 或 [\<Type>](type-element-net-native.md) 元素的子元素，用于将策略应用到一个特定的泛型类型参数，该参数由其在泛型类型或方法签名中的名称指定。</span><span class="sxs-lookup"><span data-stu-id="50f2f-169">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="50f2f-170">`<GenericParameter>` 元素在同序列化程序一起使用时非常有用。</span><span class="sxs-lookup"><span data-stu-id="50f2f-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="50f2f-171">以下示例使用 `<GenericParameter>` 元素在对 NewtonSoft JSON 序列化程序的 [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) 方法重载的调用中，将策略应用到类型 `T`。</span><span class="sxs-lookup"><span data-stu-id="50f2f-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="50f2f-172">请参阅</span><span class="sxs-lookup"><span data-stu-id="50f2f-172">See also</span></span>

- [<span data-ttu-id="50f2f-173">\<Method> 元素</span><span class="sxs-lookup"><span data-stu-id="50f2f-173">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="50f2f-174">\<类型 > 元素</span><span class="sxs-lookup"><span data-stu-id="50f2f-174">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="50f2f-175">运行时指令 (rd.xml) 配置文件参考</span><span class="sxs-lookup"><span data-stu-id="50f2f-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="50f2f-176">运行时指令策略设置</span><span class="sxs-lookup"><span data-stu-id="50f2f-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="50f2f-177">运行时指令元素</span><span class="sxs-lookup"><span data-stu-id="50f2f-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
