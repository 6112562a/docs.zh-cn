---
title: 调用方信息 (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4b2c34945b47db01b0e655f68f92e4dae7445c2c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595348"
---
# <a name="caller-information-c"></a><span data-ttu-id="2cf74-102">调用方信息 (C#)</span><span class="sxs-lookup"><span data-stu-id="2cf74-102">Caller Information (C#)</span></span>

<span data-ttu-id="2cf74-103">通过使用调用方信息特性，可获取有关方法的调用方的信息。</span><span class="sxs-lookup"><span data-stu-id="2cf74-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="2cf74-104">可以获取源代码的文件路径、源代码中的行号和调用方的成员名称。</span><span class="sxs-lookup"><span data-stu-id="2cf74-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="2cf74-105">此信息有助于跟踪、调试和创建诊断工具。</span><span class="sxs-lookup"><span data-stu-id="2cf74-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="2cf74-106">若要获取此信息，可以使用应用于可选参数的特性，每个特性都具有默认值。</span><span class="sxs-lookup"><span data-stu-id="2cf74-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="2cf74-107">下表列出在 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空间中定义的调用方信息特性：</span><span class="sxs-lookup"><span data-stu-id="2cf74-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="2cf74-108">特性</span><span class="sxs-lookup"><span data-stu-id="2cf74-108">Attribute</span></span>|<span data-ttu-id="2cf74-109">说明</span><span class="sxs-lookup"><span data-stu-id="2cf74-109">Description</span></span>|<span data-ttu-id="2cf74-110">类型</span><span class="sxs-lookup"><span data-stu-id="2cf74-110">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="2cf74-111">包含调用方的源文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="2cf74-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="2cf74-112">这是编译时的文件路径。</span><span class="sxs-lookup"><span data-stu-id="2cf74-112">This is the file path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="2cf74-113">源文件中调用方法的行号。</span><span class="sxs-lookup"><span data-stu-id="2cf74-113">Line number in the source file at which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="2cf74-114">调用方的方法或属性名称。</span><span class="sxs-lookup"><span data-stu-id="2cf74-114">Method or property name of the caller.</span></span> <span data-ttu-id="2cf74-115">请参阅本主题后面的[成员名称](#member-names)。</span><span class="sxs-lookup"><span data-stu-id="2cf74-115">See [Member Names](#member-names) later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="2cf74-116">示例</span><span class="sxs-lookup"><span data-stu-id="2cf74-116">Example</span></span>

<span data-ttu-id="2cf74-117">下面的示例演示如何使用调用方信息特性。</span><span class="sxs-lookup"><span data-stu-id="2cf74-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="2cf74-118">每次调用 `TraceMessage` 方法时，调用方信息将替换为可选参数的变量。</span><span class="sxs-lookup"><span data-stu-id="2cf74-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    System.Diagnostics.Trace.WriteLine("message: " + message);
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

## <a name="remarks"></a><span data-ttu-id="2cf74-119">备注</span><span class="sxs-lookup"><span data-stu-id="2cf74-119">Remarks</span></span>

<span data-ttu-id="2cf74-120">你必须为每个可选参数指定显式默认值。</span><span class="sxs-lookup"><span data-stu-id="2cf74-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="2cf74-121">不能将调用方信息特性应用于未指定为可选的参数。</span><span class="sxs-lookup"><span data-stu-id="2cf74-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>

<span data-ttu-id="2cf74-122">调用方信息特性不会使参数成为可选参数。</span><span class="sxs-lookup"><span data-stu-id="2cf74-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="2cf74-123">相反，它们会在忽略此参数时影响传入的默认值。</span><span class="sxs-lookup"><span data-stu-id="2cf74-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>

<span data-ttu-id="2cf74-124">在编译时，调用方信息值将作为文本传入中间语言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="2cf74-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="2cf74-125">与异常的 <xref:System.Exception.StackTrace%2A> 属性的结果不同，这些结果不受模糊处理的影响。</span><span class="sxs-lookup"><span data-stu-id="2cf74-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="2cf74-126">你可显式提供可选参数来控制调用方信息或隐藏调用方信息。</span><span class="sxs-lookup"><span data-stu-id="2cf74-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="2cf74-127">成员名称</span><span class="sxs-lookup"><span data-stu-id="2cf74-127">Member names</span></span>

<span data-ttu-id="2cf74-128">可以使用 `CallerMemberName` 特性来避免将成员名称指定为所调用的方法的 `String` 参数。</span><span class="sxs-lookup"><span data-stu-id="2cf74-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="2cf74-129">通过使用这种技术，可以避免“重命名重构”  不更改 `String` 值的问题。</span><span class="sxs-lookup"><span data-stu-id="2cf74-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="2cf74-130">此好处对于以下任务特别有用：</span><span class="sxs-lookup"><span data-stu-id="2cf74-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="2cf74-131">使用跟踪和诊断例程。</span><span class="sxs-lookup"><span data-stu-id="2cf74-131">Using tracing and diagnostic routines.</span></span>

- <span data-ttu-id="2cf74-132">在绑定数据时实现 <xref:System.ComponentModel.INotifyPropertyChanged> 接口。</span><span class="sxs-lookup"><span data-stu-id="2cf74-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="2cf74-133">此接口允许对象的属性通知绑定控件该属性已更改，以便此控件能够显示更新的信息。</span><span class="sxs-lookup"><span data-stu-id="2cf74-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="2cf74-134">如果没有 `CallerMemberName` 特性，则必须将属性名称指定为文本。</span><span class="sxs-lookup"><span data-stu-id="2cf74-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="2cf74-135">以下图表显示在使用 `CallerMemberName` 特性时返回的成员名称。</span><span class="sxs-lookup"><span data-stu-id="2cf74-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="2cf74-136">调用发生中</span><span class="sxs-lookup"><span data-stu-id="2cf74-136">Calls occurs within</span></span>|<span data-ttu-id="2cf74-137">成员名称结果</span><span class="sxs-lookup"><span data-stu-id="2cf74-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="2cf74-138">方法、属性或事件</span><span class="sxs-lookup"><span data-stu-id="2cf74-138">Method, property, or event</span></span>|<span data-ttu-id="2cf74-139">从中发起调用的方法、属性或事件的名称。</span><span class="sxs-lookup"><span data-stu-id="2cf74-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="2cf74-140">构造函数</span><span class="sxs-lookup"><span data-stu-id="2cf74-140">Constructor</span></span>|<span data-ttu-id="2cf74-141">字符串“.ctor”</span><span class="sxs-lookup"><span data-stu-id="2cf74-141">The string ".ctor"</span></span>|
|<span data-ttu-id="2cf74-142">静态构造函数</span><span class="sxs-lookup"><span data-stu-id="2cf74-142">Static constructor</span></span>|<span data-ttu-id="2cf74-143">字符串“.cctor”</span><span class="sxs-lookup"><span data-stu-id="2cf74-143">The string ".cctor"</span></span>|
|<span data-ttu-id="2cf74-144">析构函数</span><span class="sxs-lookup"><span data-stu-id="2cf74-144">Destructor</span></span>|<span data-ttu-id="2cf74-145">字符串“Finalize”</span><span class="sxs-lookup"><span data-stu-id="2cf74-145">The string "Finalize"</span></span>|
|<span data-ttu-id="2cf74-146">用户定义的运算符或转换</span><span class="sxs-lookup"><span data-stu-id="2cf74-146">User-defined operators or conversions</span></span>|<span data-ttu-id="2cf74-147">为成员生成的名称，例如，“op_Addition”。</span><span class="sxs-lookup"><span data-stu-id="2cf74-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="2cf74-148">特性构造函数</span><span class="sxs-lookup"><span data-stu-id="2cf74-148">Attribute constructor</span></span>|<span data-ttu-id="2cf74-149">要应用特性的方法或属性的名称。</span><span class="sxs-lookup"><span data-stu-id="2cf74-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="2cf74-150">如果该特性是成员中的任何元素（如参数、返回值或泛型参数），则此结果是与该元素关联的成员的名称。</span><span class="sxs-lookup"><span data-stu-id="2cf74-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="2cf74-151">无包含的成员（例如，程序集级别或应用于类型的特性）</span><span class="sxs-lookup"><span data-stu-id="2cf74-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="2cf74-152">可选参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="2cf74-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2cf74-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="2cf74-153">See also</span></span>

- [<span data-ttu-id="2cf74-154">特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="2cf74-154">Attributes (C#)</span></span>](./attributes/index.md)
- [<span data-ttu-id="2cf74-155">通用特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="2cf74-155">Common Attributes (C#)</span></span>](./attributes/common-attributes.md)
- [<span data-ttu-id="2cf74-156">命名参数和可选参数</span><span class="sxs-lookup"><span data-stu-id="2cf74-156">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="2cf74-157">编程概念 (C#)</span><span class="sxs-lookup"><span data-stu-id="2cf74-157">Programming Concepts (C#)</span></span>](./index.md)
