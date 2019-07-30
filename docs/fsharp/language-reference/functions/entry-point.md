---
title: 入口点
description: 了解如何将入口点设置为编译为F#可执行文件的程序, 在该文件中, 执行正式启动。
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630518"
---
# <a name="entry-point"></a><span data-ttu-id="ded82-103">入口点</span><span class="sxs-lookup"><span data-stu-id="ded82-103">Entry Point</span></span>

<span data-ttu-id="ded82-104">本主题介绍用于将入口点设置为F#程序的方法。</span><span class="sxs-lookup"><span data-stu-id="ded82-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>

## <a name="syntax"></a><span data-ttu-id="ded82-105">语法</span><span class="sxs-lookup"><span data-stu-id="ded82-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="ded82-106">备注</span><span class="sxs-lookup"><span data-stu-id="ded82-106">Remarks</span></span>

<span data-ttu-id="ded82-107">在前面的语法中,*函数绑定*是`let`绑定中函数的定义。</span><span class="sxs-lookup"><span data-stu-id="ded82-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="ded82-108">编译为可执行文件的程序的入口点是执行正式启动的位置。</span><span class="sxs-lookup"><span data-stu-id="ded82-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="ded82-109">通过将`EntryPoint`特性应用于程序的F# `main`函数, 可以指定应用程序的入口点。</span><span class="sxs-lookup"><span data-stu-id="ded82-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="ded82-110">此函数 (使用`let`绑定创建) 必须是最后编译的文件中的最后一个函数。</span><span class="sxs-lookup"><span data-stu-id="ded82-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="ded82-111">最后编译的文件是项目中的最后一个文件, 或者是传递到命令行的最后一个文件。</span><span class="sxs-lookup"><span data-stu-id="ded82-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="ded82-112">入口点函数的类型`string array -> int`为。</span><span class="sxs-lookup"><span data-stu-id="ded82-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="ded82-113">在命令行上提供的参数会传递到字符串`main`数组中的函数。</span><span class="sxs-lookup"><span data-stu-id="ded82-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="ded82-114">数组的第一个元素是第一个参数;数组中未包含可执行文件的名称, 因为它采用其他一些语言。</span><span class="sxs-lookup"><span data-stu-id="ded82-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="ded82-115">返回值用作进程的退出代码。</span><span class="sxs-lookup"><span data-stu-id="ded82-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="ded82-116">零通常指示成功;非零值表示错误。</span><span class="sxs-lookup"><span data-stu-id="ded82-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="ded82-117">非零返回代码的特定含义没有约定;返回代码的含义是特定于应用程序的。</span><span class="sxs-lookup"><span data-stu-id="ded82-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="ded82-118">下面的示例演示一个简单`main`的函数。</span><span class="sxs-lookup"><span data-stu-id="ded82-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="ded82-119">当通过命令行`EntryPoint.exe 1 2 3`执行此代码时, 输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="ded82-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="ded82-120">隐式入口点</span><span class="sxs-lookup"><span data-stu-id="ded82-120">Implicit Entry Point</span></span>

<span data-ttu-id="ded82-121">当程序没有显式指示入口点的**EntryPoint**属性时, 最后一个要编译的文件中的顶级绑定将用作入口点。</span><span class="sxs-lookup"><span data-stu-id="ded82-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="ded82-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="ded82-122">See also</span></span>

- [<span data-ttu-id="ded82-123">函数</span><span class="sxs-lookup"><span data-stu-id="ded82-123">Functions</span></span>](index.md)
- [<span data-ttu-id="ded82-124">let 绑定</span><span class="sxs-lookup"><span data-stu-id="ded82-124">let Bindings</span></span>](let-bindings.md)
