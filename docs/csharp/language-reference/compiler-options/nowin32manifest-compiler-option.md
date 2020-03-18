---
title: -nowin32manifest（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602712"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="8b35d-102">-nowin32manifest（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="8b35d-102">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="8b35d-103">使用 -nowin32manifest 选项可指示编译器不将任何应用程序清单嵌入到可执行文件中  。</span><span class="sxs-lookup"><span data-stu-id="8b35d-103">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b35d-104">语法</span><span class="sxs-lookup"><span data-stu-id="8b35d-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="8b35d-105">备注</span><span class="sxs-lookup"><span data-stu-id="8b35d-105">Remarks</span></span>  
 <span data-ttu-id="8b35d-106">使用此选项时，除非在 Win32 资源文件或以后的生成步骤中提供应用程序清单，否则应用程序会受到 Windows Vista 上虚拟化的影响。</span><span class="sxs-lookup"><span data-stu-id="8b35d-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="8b35d-107">在 Visual Studio 的“应用程序属性”  页中，通过在“清单”下拉列表中选择“创建不带清单的应用程序”选项来设置此选项   。</span><span class="sxs-lookup"><span data-stu-id="8b35d-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="8b35d-108">有关详细信息，请参阅[“项目设计器”->“应用程序”页 (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="8b35d-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="8b35d-109">有关创建清单的详细信息，请参阅 [-win32manifest（C# 编译器选项）](./win32manifest-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="8b35d-109">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b35d-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b35d-110">See also</span></span>

- [<span data-ttu-id="8b35d-111">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="8b35d-111">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="8b35d-112">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="8b35d-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
