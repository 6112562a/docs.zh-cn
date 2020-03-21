---
title: 入门
ms.date: 01/26/2018
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF [WPF], getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
ms.openlocfilehash: 7bd6219a9773620fcacf591950f2fb4e62beaf13
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546771"
---
# <a name="getting-started-wpf"></a><span data-ttu-id="92255-102">入门 (WPF)</span><span class="sxs-lookup"><span data-stu-id="92255-102">Getting Started (WPF)</span></span>
<span data-ttu-id="92255-103">Windows Presentation Foundation (WPF) 是一个可创建桌面客户端应用程序的 UI 框架。</span><span class="sxs-lookup"><span data-stu-id="92255-103">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="92255-104">WPF 开发平台支持广泛的应用程序开发功能，包括应用程序模型、资源、控件、图形、布局、数据绑定、文档和安全性。</span><span class="sxs-lookup"><span data-stu-id="92255-104">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="92255-105">它是 .NET Framework 的子集，因此，如果你曾经使用 ASP.NET 或 Windows 窗体通过 .NET Framework 构建应用程序，应该会熟悉此编程体验。</span><span class="sxs-lookup"><span data-stu-id="92255-105">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="92255-106">WPF 使用可扩展应用程序标记语言 (XAML) 为应用程序编程提供声明性模型。</span><span class="sxs-lookup"><span data-stu-id="92255-106">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="92255-107">本节包含 WPF 简介及入门帮助等主题。</span><span class="sxs-lookup"><span data-stu-id="92255-107">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="92255-108">从何处开始？</span><span class="sxs-lookup"><span data-stu-id="92255-108">Where Should I Start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="92255-109">我希望直接开始使用…</span><span class="sxs-lookup"><span data-stu-id="92255-109">I want to jump right in…</span></span>|[<span data-ttu-id="92255-110">演练：我的第一个 WPF 桌面应用程序</span><span class="sxs-lookup"><span data-stu-id="92255-110">Walkthrough: My first WPF desktop application</span></span>](walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="92255-111">如何设计应用程序 UI？</span><span class="sxs-lookup"><span data-stu-id="92255-111">How do I design the application UI?</span></span>|[<span data-ttu-id="92255-112">在 Visual Studio 中设计 XAML</span><span class="sxs-lookup"><span data-stu-id="92255-112">Designing XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)|  
|<span data-ttu-id="92255-113">是否是初次使用 .NET？</span><span class="sxs-lookup"><span data-stu-id="92255-113">New to .NET?</span></span>|[<span data-ttu-id="92255-114">.NET Framework 概述</span><span class="sxs-lookup"><span data-stu-id="92255-114">Overview of the .NET Framework</span></span>](../../get-started/overview.md)<br /><br /> [<span data-ttu-id="92255-115">.NET Framework 应用程序要点</span><span class="sxs-lookup"><span data-stu-id="92255-115">.NET Framework Application Essentials</span></span>](../../../standard/application-essentials.md)<br /><br /> [<span data-ttu-id="92255-116">Visual C# 和 Visual Basic 入门</span><span class="sxs-lookup"><span data-stu-id="92255-116">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/quickstart-visual-basic-console)|  
|<span data-ttu-id="92255-117">有关 WPF 的详细信息...</span><span class="sxs-lookup"><span data-stu-id="92255-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="92255-118">Visual Studio 中的 WPF 简介</span><span class="sxs-lookup"><span data-stu-id="92255-118">Introduction to WPF in Visual Studio</span></span>](introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="92255-119">XAML 概述 (WPF)</span><span class="sxs-lookup"><span data-stu-id="92255-119">XAML Overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)<br /><br /> [<span data-ttu-id="92255-120">控制</span><span class="sxs-lookup"><span data-stu-id="92255-120">Controls</span></span>](../controls/index.md)<br /><br /> [<span data-ttu-id="92255-121">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="92255-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="92255-122">是否是 Windows 窗体开发人员？</span><span class="sxs-lookup"><span data-stu-id="92255-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="92255-123">窗口窗体控件和等效 WPF 控件</span><span class="sxs-lookup"><span data-stu-id="92255-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="92255-124">WPF 和 Windows 窗体互操作</span><span class="sxs-lookup"><span data-stu-id="92255-124">WPF and Windows Forms Interoperation</span></span>](../advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="92255-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92255-125">See also</span></span>

- [<span data-ttu-id="92255-126">类库</span><span class="sxs-lookup"><span data-stu-id="92255-126">Class Library</span></span>](../class-library-wpf.md)
- [<span data-ttu-id="92255-127">应用程序开发</span><span class="sxs-lookup"><span data-stu-id="92255-127">Application Development</span></span>](../app-development/index.md)
- [<span data-ttu-id="92255-128">.NET framework 开发人员中心</span><span class="sxs-lookup"><span data-stu-id="92255-128">.NET Framework Developer Center</span></span>](https://dotnet.microsoft.com)
