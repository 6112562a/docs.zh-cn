---
title: 如何：使用命令行创建和使用程序集 (C#)
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 0a8db22a05d834d15f6e6b7f049f59f86bc1fe1d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595966"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>如何：使用命令行创建和使用程序集 (C#)
程序集或动态链接库 (DLL) 会在运行时链接到程序。 为了演示如何生成和使用 DLL，请考虑以下方案：  
  
- `MathLibrary.DLL`：包含要在运行时调用的方法的库文件。 在此示例中，DLL 包含两个方法，即 `Add` 和 `Multiply`。  
  
- `Add`：包含方法 `Add` 的源文件。 它返回其参数的总和。 包含方法 `Add` 的类 `AddClass` 是命名空间 `UtilityMethods` 的成员。  
  
- `Mult`：包含方法 `Multiply` 的源代码。 它返回其参数的乘积。 包含方法 `Multiply` 的类 `MultiplyClass` 也是命名空间 `UtilityMethods` 的成员。  
  
- `TestCode`：包含 `Main` 方法的文件。 它使用 DLL 文件中的方法计算运行时参数的总和与乘积。  
  
## <a name="example"></a>示例  
  
```csharp  
// File: Add.cs   
namespace UtilityMethods  
{  
    public class AddClass   
    {  
        public static long Add(long i, long j)   
        {   
            return (i + j);  
        }  
    }  
}  
```  
  
```csharp  
// File: Mult.cs  
namespace UtilityMethods   
{  
    public class MultiplyClass  
    {  
        public static long Multiply(long x, long y)   
        {  
            return (x * y);   
        }  
    }  
}  
```  
  
```csharp  
// File: TestCode.cs  
  
using UtilityMethods;  
  
class TestCode  
{  
    static void Main(string[] args)   
    {  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:");  
  
        if (args.Length != 2)  
        {  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>");  
            return;  
        }  
  
        long num1 = long.Parse(args[0]);  
        long num2 = long.Parse(args[1]);  
  
        long sum = AddClass.Add(num1, num2);  
        long product = MultiplyClass.Multiply(num1, num2);  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum);  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product);  
    }  
}  
/* Output (assuming 1234 and 5678 are entered as command-line arguments):  
    Calling methods from MathLibrary.DLL:  
    1234 + 5678 = 6912  
    1234 * 5678 = 7006652          
*/  
```  
  
 此文件包含使用 DLL 方法 `Add` 和 `Multiply` 的算法。 它首先分析从命令行输入的参数 `num1` 和 `num2`。 然后通过对 `AddClass` 类使用 `Add` 方法来计算总和，并通过对 `MultiplyClass` 类使用 `Multiply` 方法来计算乘积。  
  
 请注意，文件开头的 `using` 指令使你可以使用非限定类名在编译时引用 DLL 方法，如下所示：  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 否则，你必须使用完全限定的名称，如下所示：  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>执行  
 若要运行程序，请输入 EXE 文件的名称，后跟两个数字，如下所示：  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../../index.md)
- [.NET 中的程序集](../../../../standard/assembly/index.md)
- [创建用于容纳 DLL 函数的类](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
