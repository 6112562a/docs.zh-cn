---
title: 在托管代码中创建原型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
ms.openlocfilehash: 712040c3482b51c4dafe0ee87fdda8cd848fb7fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123615"
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="30209-102">在托管代码中创建原型</span><span class="sxs-lookup"><span data-stu-id="30209-102">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="30209-103">本主题介绍了如何访问非托管函数，并介绍了在托管代码中批注方法定义的若干属性字段。</span><span class="sxs-lookup"><span data-stu-id="30209-103">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="30209-104">有关演示如何构造要用于平台调用、基于 .NET 的声明的示例，请参阅[用平台调用封送数据](marshaling-data-with-platform-invoke.md)。</span><span class="sxs-lookup"><span data-stu-id="30209-104">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="30209-105">在从托管代码访问非托管 DLL 函数之前，需要知道函数的名称以及将其导出的 DLL 的名称。</span><span class="sxs-lookup"><span data-stu-id="30209-105">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="30209-106">使用此信息，可开始为 DLL 中实现的非托管函数编写托管定义。</span><span class="sxs-lookup"><span data-stu-id="30209-106">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="30209-107">此外，可调整平台调用创建函数以及将数据封送到函数和从中封送数据的方法。</span><span class="sxs-lookup"><span data-stu-id="30209-107">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30209-108">借助分配字符串的 Windows API 函数，可以使用 `LocalFree` 等方法释放字符串。</span><span class="sxs-lookup"><span data-stu-id="30209-108">Windows API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="30209-109">平台调用以不同方式处理此类参数。</span><span class="sxs-lookup"><span data-stu-id="30209-109">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="30209-110">为了调用平台调用，将参数设为 `IntPtr` 类型，而不是 `String` 类型。</span><span class="sxs-lookup"><span data-stu-id="30209-110">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="30209-111">使用 <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> 类提供的方法手动将类型转换为字符串，并将其手动释放。</span><span class="sxs-lookup"><span data-stu-id="30209-111">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="30209-112">声明基本知识</span><span class="sxs-lookup"><span data-stu-id="30209-112">Declaration Basics</span></span>  
 <span data-ttu-id="30209-113">如以下示例所示，非托管函数的托管定义依赖于语言。</span><span class="sxs-lookup"><span data-stu-id="30209-113">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="30209-114">有关更完整的代码示例，请参阅[平台调用示例](platform-invoke-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="30209-114">For more complete code examples, see [Platform Invoke Examples](platform-invoke-examples.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <span data-ttu-id="30209-115">若要将 <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>、<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>、<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>、<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>、<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType> 或 <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> 字段应用到 Visual Basic 声明，必须使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 属性，而不是 `Declare` 语句。</span><span class="sxs-lookup"><span data-stu-id="30209-115">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> fields to a Visual Basic declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb
Imports System.Runtime.InteropServices

Friend Class NativeMethods
    <DllImport("user32.dll", CharSet:=CharSet.Auto)>
    Friend Shared Function MessageBox(
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
    End Function
End Class
```
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("user32.dll")]
extern "C" int MessageBox(
    IntPtr hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="30209-116">调整定义</span><span class="sxs-lookup"><span data-stu-id="30209-116">Adjusting the Definition</span></span>  
 <span data-ttu-id="30209-117">无论是否设置为显式，属性字段都将定义托管代码的行为。</span><span class="sxs-lookup"><span data-stu-id="30209-117">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="30209-118">平台调用根据程序集中作为元数据存在的各个字段上设置的默认值进行操作。</span><span class="sxs-lookup"><span data-stu-id="30209-118">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="30209-119">可通过调整一个或多个字段的值来更改此默认行为。</span><span class="sxs-lookup"><span data-stu-id="30209-119">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="30209-120">在很多情况下，使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 设置值。</span><span class="sxs-lookup"><span data-stu-id="30209-120">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="30209-121">下表列出了与平台调用相关的完整的属性字段集。</span><span class="sxs-lookup"><span data-stu-id="30209-121">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="30209-122">对于每个字段，此表包括了默认值以及有关如何使用这些字段来定义非托管 DLL 函数的信息的链接。</span><span class="sxs-lookup"><span data-stu-id="30209-122">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="30209-123">字段</span><span class="sxs-lookup"><span data-stu-id="30209-123">Field</span></span>|<span data-ttu-id="30209-124">描述</span><span class="sxs-lookup"><span data-stu-id="30209-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="30209-125">启用或禁用最佳映射。</span><span class="sxs-lookup"><span data-stu-id="30209-125">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="30209-126">指定要用于传递方法自变量的调用约定。</span><span class="sxs-lookup"><span data-stu-id="30209-126">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="30209-127">默认值是 `WinAPI`，此值对应于 32 位基于 Intel 的平台的 `__stdcall`。</span><span class="sxs-lookup"><span data-stu-id="30209-127">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="30209-128">控件名称重整以及应将字符串参数封送到函数的方法。</span><span class="sxs-lookup"><span data-stu-id="30209-128">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="30209-129">默认值为 `CharSet.Ansi`。</span><span class="sxs-lookup"><span data-stu-id="30209-129">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="30209-130">指定要调用的 DLL 入口点。</span><span class="sxs-lookup"><span data-stu-id="30209-130">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="30209-131">控制是否应修改入口点以对应字符集。</span><span class="sxs-lookup"><span data-stu-id="30209-131">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="30209-132">默认值因编程语言而异。</span><span class="sxs-lookup"><span data-stu-id="30209-132">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="30209-133">控制是否应将托管方法签名转换为返回 HRESULT 并具有返回值的附加 [out，retval] 参数的非托管签名。</span><span class="sxs-lookup"><span data-stu-id="30209-133">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="30209-134">默认值为 `true`（不应转换签名）。</span><span class="sxs-lookup"><span data-stu-id="30209-134">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="30209-135">允许调用方使用 `Marshal.GetLastWin32Error` API 函数确定执行此方法时是否发生了错误。</span><span class="sxs-lookup"><span data-stu-id="30209-135">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="30209-136">在 Visual Basic 中，默认值为 `true`；在 C# 和 C++ 中，默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="30209-136">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="30209-137">控制在转换为 ANSI "?" 字符的非托管 Unicode 字符上引发的异常。</span><span class="sxs-lookup"><span data-stu-id="30209-137">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="30209-138">详细的引用信息，请参阅 <xref:System.Runtime.InteropServices.DllImportAttribute>。</span><span class="sxs-lookup"><span data-stu-id="30209-138">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="30209-139">平台调用安全注意事项</span><span class="sxs-lookup"><span data-stu-id="30209-139">Platform invoke security considerations</span></span>  
 <span data-ttu-id="30209-140"><xref:System.Security.Permissions.SecurityAction> 枚举的 `Assert`、`Deny` 和 `PermitOnly` 成员被称为堆栈审核修饰符。</span><span class="sxs-lookup"><span data-stu-id="30209-140">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="30209-141">如果将这些成员用作平台调用声明和 COM 接口定义语言 (IDL) 语句上的声明性属性，则会被忽略。</span><span class="sxs-lookup"><span data-stu-id="30209-141">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="30209-142">平台调用示例</span><span class="sxs-lookup"><span data-stu-id="30209-142">Platform Invoke Examples</span></span>  
 <span data-ttu-id="30209-143">本节中的平台调用示例阐明了如何将 `RegistryPermission` 属性和堆栈审核修饰符一起使用。</span><span class="sxs-lookup"><span data-stu-id="30209-143">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="30209-144">在下面的示例中，<xref:System.Security.Permissions.SecurityAction>`Assert`、`Deny` 和 `PermitOnly` 修饰符被忽略。</span><span class="sxs-lookup"><span data-stu-id="30209-144">In the following example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```csharp  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="30209-145">但是，以下示例接受 `Demand` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="30209-145">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="30209-146">如果将 <xref:System.Security.Permissions.SecurityAction> 修饰符放置在包含（包装）平台调用的类中，则无法正常运行。</span><span class="sxs-lookup"><span data-stu-id="30209-146"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 <span data-ttu-id="30209-147">如果 <xref:System.Security.Permissions.SecurityAction> 修饰符位于嵌套方案中平台调用的调用方上，则也可在此方案中正常运行：</span><span class="sxs-lookup"><span data-stu-id="30209-147"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a><span data-ttu-id="30209-148">COM 互操作示例</span><span class="sxs-lookup"><span data-stu-id="30209-148">COM Interop Examples</span></span>  
 <span data-ttu-id="30209-149">本节中的 COM 互操作示例阐明了如何将 `RegistryPermission` 属性和堆栈审核修饰符一起使用。</span><span class="sxs-lookup"><span data-stu-id="30209-149">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="30209-150">与上节中的平台调用示例相似，以下 COM 互操作接口声明也会忽略 `Assert`、`Deny` 和 `PermitOnly` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="30209-150">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```csharp
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 <span data-ttu-id="30209-151">此外，COM 互操作接口声明方案不接受 `Demand` 修饰符，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="30209-151">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```csharp  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="30209-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="30209-152">See also</span></span>

- [<span data-ttu-id="30209-153">使用非托管 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="30209-153">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="30209-154">指定入口点</span><span class="sxs-lookup"><span data-stu-id="30209-154">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="30209-155">指定字符集</span><span class="sxs-lookup"><span data-stu-id="30209-155">Specifying a Character Set</span></span>](specifying-a-character-set.md)
- [<span data-ttu-id="30209-156">平台调用示例</span><span class="sxs-lookup"><span data-stu-id="30209-156">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- <span data-ttu-id="30209-157">[平台调用安全注意事项](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="30209-157">[Platform Invoke Security Considerations](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span></span>
- [<span data-ttu-id="30209-158">标识 DLL 中的函数</span><span class="sxs-lookup"><span data-stu-id="30209-158">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="30209-159">创建用于容纳 DLL 函数的类</span><span class="sxs-lookup"><span data-stu-id="30209-159">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="30209-160">调用 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="30209-160">Calling a DLL Function</span></span>](calling-a-dll-function.md)
