---
title: '#pragma warning - C# 参考'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5620ea9e5f31c22e26bee95a450335bb179ced25
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712463"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="c307e-102">#pragma warning（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="c307e-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="c307e-103">`#pragma warning` 可以启用或禁用特定警告。</span><span class="sxs-lookup"><span data-stu-id="c307e-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c307e-104">语法</span><span class="sxs-lookup"><span data-stu-id="c307e-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="c307e-105">参数</span><span class="sxs-lookup"><span data-stu-id="c307e-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="c307e-106">以逗号分隔的警告编号的列表。</span><span class="sxs-lookup"><span data-stu-id="c307e-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="c307e-107">“CS”前缀是可选的。</span><span class="sxs-lookup"><span data-stu-id="c307e-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="c307e-108">未指定警告编号时，`disable` 会禁用所有警告，`restore` 会启用所有警告。</span><span class="sxs-lookup"><span data-stu-id="c307e-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c307e-109">若要在 Visual Studio 中查找警告编号，请生成项目，然后在“输出”  窗口中查找警告编号。</span><span class="sxs-lookup"><span data-stu-id="c307e-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c307e-110">示例</span><span class="sxs-lookup"><span data-stu-id="c307e-110">Example</span></span>  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c307e-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="c307e-111">See also</span></span>

- [<span data-ttu-id="c307e-112">C# 参考</span><span class="sxs-lookup"><span data-stu-id="c307e-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c307e-113">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="c307e-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c307e-114">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="c307e-114">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="c307e-115">C# 编译器错误</span><span class="sxs-lookup"><span data-stu-id="c307e-115">C# Compiler Errors</span></span>](../compiler-messages/index.md)
