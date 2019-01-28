---
title: -codepage（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 7cbd3ec1b2d134106c6c9429341f5603444dac27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693975"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="58749-102">-codepage（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="58749-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="58749-103">如果所需页不是系统的当前默认代码页，则此选项指定编译期间要使用的代码页。</span><span class="sxs-lookup"><span data-stu-id="58749-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58749-104">语法</span><span class="sxs-lookup"><span data-stu-id="58749-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="58749-105">自变量</span><span class="sxs-lookup"><span data-stu-id="58749-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="58749-106">要用于编译中所有源代码文件的代码页 ID。</span><span class="sxs-lookup"><span data-stu-id="58749-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58749-107">备注</span><span class="sxs-lookup"><span data-stu-id="58749-107">Remarks</span></span>  
 <span data-ttu-id="58749-108">如果编译一个或多个并非是为使用计算机上默认代码页而创建的源代码文件，可使用 -codepage 选项指定应使用的代码页。</span><span class="sxs-lookup"><span data-stu-id="58749-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="58749-109">-codepage 适用于编译中的所有源代码文件。</span><span class="sxs-lookup"><span data-stu-id="58749-109">**-codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="58749-110">如果源代码文件是使用计算机上采用的相同代码页创建的，或者如果是通过 UNICODE 或 UTF-8 创建的，则无需使用 -codepage。</span><span class="sxs-lookup"><span data-stu-id="58749-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **-codepage**.</span></span>  
  
 <span data-ttu-id="58749-111">有关如何查找系统上支持哪些代码页的信息，请参阅 [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo)。</span><span class="sxs-lookup"><span data-stu-id="58749-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="58749-112">此编译器选项在 Visual Studio 中不可用，并且无法以编程方式更改。</span><span class="sxs-lookup"><span data-stu-id="58749-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58749-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="58749-113">See also</span></span>

- [<span data-ttu-id="58749-114">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="58749-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="58749-115">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="58749-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
