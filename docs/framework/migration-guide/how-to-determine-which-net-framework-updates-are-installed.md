---
title: 如何：确定安装了哪些 .NET Framework 安全更新和修补程序
description: 了解如何确定计算机上安装了哪些 .NET Framework 安全更新和修补程序。
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4c505c679c46494f7dc2534c2bbe9f50243a7dd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790062"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="5925e-103">如何：确定安装了哪些 .NET Framework 安全更新和修补程序</span><span class="sxs-lookup"><span data-stu-id="5925e-103">How to: Determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="5925e-104">本文介绍如何找出计算机上安装了哪些 .NET Framework 安全更新和修补程序。</span><span class="sxs-lookup"><span data-stu-id="5925e-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="5925e-105">本文中介绍的所有方法均需要具有管理权限的帐户。</span><span class="sxs-lookup"><span data-stu-id="5925e-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="to-find-installed-updates-using-the-registry"></a><span data-ttu-id="5925e-106">使用注册表找到已安装的更新</span><span class="sxs-lookup"><span data-stu-id="5925e-106">To find installed updates using the registry</span></span>

<span data-ttu-id="5925e-107">安装在计算机上的各个版本 .NET Framework 的已安装安全更新和修补程序都列在 Windows 注册表中。</span><span class="sxs-lookup"><span data-stu-id="5925e-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="5925e-108">可以使用注册表编辑器 (regedit.exe) 程序查看此信息  。</span><span class="sxs-lookup"><span data-stu-id="5925e-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="5925e-109">打开程序 **regedit.exe**。</span><span class="sxs-lookup"><span data-stu-id="5925e-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="5925e-110">在 Windows 8 和更高版本中，右键单击“开始”![Windows 徽标](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")，然后选择“运行”   。</span><span class="sxs-lookup"><span data-stu-id="5925e-110">In Windows 8 and later versions, right-click **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="5925e-111">在“打开”对话框中，输入“regedit.exe”并选择“确定”    。</span><span class="sxs-lookup"><span data-stu-id="5925e-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="5925e-112">在注册表编辑器中，打开以下子项：</span><span class="sxs-lookup"><span data-stu-id="5925e-112">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     <span data-ttu-id="5925e-113">已安装的更新在标识适用的 .NET Framework 版本的子项下方列出。</span><span class="sxs-lookup"><span data-stu-id="5925e-113">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="5925e-114">每个更新均由知识库 (KB) 编号进行标识。</span><span class="sxs-lookup"><span data-stu-id="5925e-114">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="5925e-115">在注册表编辑器中，.NET Framework 版本和每个版本已安装的更新都保存在不同的子项中。</span><span class="sxs-lookup"><span data-stu-id="5925e-115">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="5925e-116">有关检测已安装版本号的信息，请参阅[如何：确定已安装的 .NET Framework 版本](how-to-determine-which-versions-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="5925e-116">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a><span data-ttu-id="5925e-117">通过在代码中查询注册表找到已安装的更新</span><span class="sxs-lookup"><span data-stu-id="5925e-117">To find installed updates by querying the registry in code</span></span>

<span data-ttu-id="5925e-118">以下示例以编程方式确定已安装在计算机上的 .NET Framework 安全更新和修补程序：</span><span class="sxs-lookup"><span data-stu-id="5925e-118">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="5925e-119">该示例生成类似下面内容的输出：</span><span class="sxs-lookup"><span data-stu-id="5925e-119">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a><span data-ttu-id="5925e-120">在 PowerShell 中查询注册表找到已安装的更新</span><span class="sxs-lookup"><span data-stu-id="5925e-120">To find installed updates by querying the registry in PowerShell</span></span>

<span data-ttu-id="5925e-121">以下示例介绍如何使用 PowerShell 确定已安装在计算机上的 .NET Framework 安全更新和修补程序：</span><span class="sxs-lookup"><span data-stu-id="5925e-121">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){
    
   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

<span data-ttu-id="5925e-122">该示例生成类似下面内容的输出：</span><span class="sxs-lookup"><span data-stu-id="5925e-122">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a><span data-ttu-id="5925e-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="5925e-123">See also</span></span>

- [<span data-ttu-id="5925e-124">如何：确定已安装的 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="5925e-124">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="5925e-125">安装面向开发者的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5925e-125">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="5925e-126">版本和依赖关系</span><span class="sxs-lookup"><span data-stu-id="5925e-126">Versions and dependencies</span></span>](versions-and-dependencies.md)
