---
title: 如何：确定文件是否为程序集 (C#)
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: 0cf9258aa4a5a1a633ee0bb04808d384de8f48d0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125530"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="ba894-102">如何：确定文件是否为程序集 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba894-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="ba894-103">当且仅当程序集处于托管状态，并在其元数据中包含程序集条目时，该文件才为程序集。</span><span class="sxs-lookup"><span data-stu-id="ba894-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="ba894-104">有关程序集和元数据的详细信息，请参阅主题[程序集清单](../../../../../docs/framework/app-domains/assembly-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="ba894-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../../docs/framework/app-domains/assembly-manifest.md).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="ba894-105">如何手动确定文件是否为程序集</span><span class="sxs-lookup"><span data-stu-id="ba894-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="ba894-106">启动 [Ildasm.exe（IL 反汇编程序）](../../../../framework/tools/ildasm-exe-il-disassembler.md)。</span><span class="sxs-lookup"><span data-stu-id="ba894-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2.  <span data-ttu-id="ba894-107">加载要测试的文件。</span><span class="sxs-lookup"><span data-stu-id="ba894-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="ba894-108">如果 **ILDASM** 报告文件不是可移植的可执行 (PE) 文件，则不是程序集。</span><span class="sxs-lookup"><span data-stu-id="ba894-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="ba894-109">有关详细信息，请参阅主题 [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md)（如何：查看程序集内容）。</span><span class="sxs-lookup"><span data-stu-id="ba894-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="ba894-110">如何以编程方式确定文件是否为程序集</span><span class="sxs-lookup"><span data-stu-id="ba894-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="ba894-111">调用 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法，传递要测试的文件的完整文件路径和名称。</span><span class="sxs-lookup"><span data-stu-id="ba894-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="ba894-112">如果引发 <xref:System.BadImageFormatException> 异常，则该文件不是程序集。</span><span class="sxs-lookup"><span data-stu-id="ba894-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba894-113">示例</span><span class="sxs-lookup"><span data-stu-id="ba894-113">Example</span></span>  
 <span data-ttu-id="ba894-114">此示例测试 DLL 以查看其是否为程序集。</span><span class="sxs-lookup"><span data-stu-id="ba894-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  
  
 <span data-ttu-id="ba894-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法加载测试文件，然后在读取信息之后释放它。</span><span class="sxs-lookup"><span data-stu-id="ba894-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba894-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="ba894-116">See Also</span></span>

- <xref:System.Reflection.AssemblyName>  
- [<span data-ttu-id="ba894-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="ba894-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ba894-118">程序集和全局程序集缓存 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba894-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
