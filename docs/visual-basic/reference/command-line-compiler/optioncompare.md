---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: b88cba4d16c5a770a72b47868d11b16cbba6cae8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340433"
---
# <a name="-optioncompare"></a><span data-ttu-id="7c5b5-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="7c5b5-102">-optioncompare</span></span>
<span data-ttu-id="7c5b5-103">指定如何进行字符串比较。</span><span class="sxs-lookup"><span data-stu-id="7c5b5-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c5b5-104">语法</span><span class="sxs-lookup"><span data-stu-id="7c5b5-104">Syntax</span></span>  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="7c5b5-105">备注</span><span class="sxs-lookup"><span data-stu-id="7c5b5-105">Remarks</span></span>  
 <span data-ttu-id="7c5b5-106">您可以指定`-optioncompare`在两种形式之一：`-optioncompare:binary`使用二进制字符串比较和`-optioncompare:text`使用文本字符串比较。</span><span class="sxs-lookup"><span data-stu-id="7c5b5-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="7c5b5-107">默认情况下，编译器使用`-optioncompare:binary`。</span><span class="sxs-lookup"><span data-stu-id="7c5b5-107">By default, the compiler uses `-optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="7c5b5-108">在 Microsoft Windows 中的当前代码页确定二进制排序顺序。</span><span class="sxs-lookup"><span data-stu-id="7c5b5-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="7c5b5-109">典型的二进制排序顺序是按如下所示：</span><span class="sxs-lookup"><span data-stu-id="7c5b5-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="7c5b5-110">基于文本的字符串比较将基于由您的系统区域设置的不区分大小写的文本排序顺序。</span><span class="sxs-lookup"><span data-stu-id="7c5b5-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="7c5b5-111">典型的文本排序顺序是按如下所示：</span><span class="sxs-lookup"><span data-stu-id="7c5b5-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="7c5b5-112">若要在 Visual Studio IDE 中设置-optioncompare</span><span class="sxs-lookup"><span data-stu-id="7c5b5-112">To set -optioncompare in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="7c5b5-113">在 **“解决方案资源管理器”** 中选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="7c5b5-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7c5b5-114">在“项目”菜单上，单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="7c5b5-114">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="7c5b5-115">单击“编译”选项卡。</span><span class="sxs-lookup"><span data-stu-id="7c5b5-115">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="7c5b5-116">修改中的值**Option Compare**框。</span><span class="sxs-lookup"><span data-stu-id="7c5b5-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="7c5b5-117">若要以编程方式设置-optioncompare</span><span class="sxs-lookup"><span data-stu-id="7c5b5-117">To set -optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="7c5b5-118">请参阅[Option Compare 语句](../../../visual-basic/language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5b5-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c5b5-119">示例</span><span class="sxs-lookup"><span data-stu-id="7c5b5-119">Example</span></span>  
 <span data-ttu-id="7c5b5-120">下面的代码编译`ProjFile.vb`，并使用二进制字符串比较。</span><span class="sxs-lookup"><span data-stu-id="7c5b5-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c5b5-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="7c5b5-121">See also</span></span>

- [<span data-ttu-id="7c5b5-122">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="7c5b5-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7c5b5-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="7c5b5-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="7c5b5-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="7c5b5-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="7c5b5-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="7c5b5-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="7c5b5-126">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="7c5b5-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="7c5b5-127">Option Compare 语句</span><span class="sxs-lookup"><span data-stu-id="7c5b5-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="7c5b5-128">“选项”对话框 ->“项目”->“Visual Basic 默认值”</span><span class="sxs-lookup"><span data-stu-id="7c5b5-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
