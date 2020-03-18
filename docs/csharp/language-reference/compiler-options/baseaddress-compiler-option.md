---
title: -baseaddress（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: f138f445b8a335c7505e25b34f560c4da40ab2dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937214"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="73ebe-102">-baseaddress（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="73ebe-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="73ebe-103">通过 -baseaddress 选项可指定加载 DLL 的首选基址  。</span><span class="sxs-lookup"><span data-stu-id="73ebe-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="73ebe-104">若要深入了解何时且为何要使用此选项，请参阅 [Larry Osterman 的网络日志](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system)。</span><span class="sxs-lookup"><span data-stu-id="73ebe-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ebe-105">语法</span><span class="sxs-lookup"><span data-stu-id="73ebe-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="73ebe-106">参数</span><span class="sxs-lookup"><span data-stu-id="73ebe-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="73ebe-107">DLL 的基址。</span><span class="sxs-lookup"><span data-stu-id="73ebe-107">The base address for the DLL.</span></span> <span data-ttu-id="73ebe-108">可将此地址指定为十进制数、十六进制数或八进制数。</span><span class="sxs-lookup"><span data-stu-id="73ebe-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73ebe-109">备注</span><span class="sxs-lookup"><span data-stu-id="73ebe-109">Remarks</span></span>  
 <span data-ttu-id="73ebe-110">DLL 的默认基址由 .NET Framework 公共语言运行时设置。</span><span class="sxs-lookup"><span data-stu-id="73ebe-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="73ebe-111">请注意，此地址中的低序字将被舍入取整。</span><span class="sxs-lookup"><span data-stu-id="73ebe-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="73ebe-112">例如，如果指定 0x11110001，它将被舍入为 0x11110000。</span><span class="sxs-lookup"><span data-stu-id="73ebe-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="73ebe-113">要完成 DLL 的签名过程，请使用具有 -R 选项的 SN.EXE。</span><span class="sxs-lookup"><span data-stu-id="73ebe-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="73ebe-114">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="73ebe-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="73ebe-115">打开项目的“属性”  页。</span><span class="sxs-lookup"><span data-stu-id="73ebe-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="73ebe-116">单击“生成”  属性页。</span><span class="sxs-lookup"><span data-stu-id="73ebe-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="73ebe-117">单击 **“高级”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="73ebe-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="73ebe-118">修改“DLL 基址”  属性。</span><span class="sxs-lookup"><span data-stu-id="73ebe-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="73ebe-119">若要以编程方式设置此编译器选项，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>。</span><span class="sxs-lookup"><span data-stu-id="73ebe-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ebe-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73ebe-120">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="73ebe-121">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="73ebe-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="73ebe-122">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="73ebe-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
