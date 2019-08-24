---
title: Windows 窗体设计器中的设计时错误
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cce9baf1523391e281593428b633c401103b42b5
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015974"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="a0d0d-102">Windows 窗体设计器中的设计时错误</span><span class="sxs-lookup"><span data-stu-id="a0d0d-102">Design-time errors in the Windows Forms Designer</span></span>

<span data-ttu-id="a0d0d-103">本主题说明在无法加载 Windows 窗体设计器时, 在 Visual Studio 中显示的设计时错误列表的含义和用法。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-103">This topic explains the meaning and use of the design-time error list that appears in Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="a0d0d-104">如果出现此错误列表，则不应将其视为设计器中的 Bug，而应作为纠正代码中的错误的辅助手段。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>

<span data-ttu-id="a0d0d-105">此错误列表提供有关错误的详细信息和建议的可能解决方案，对此错误列表有一个基本了解可帮助调试应用程序。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>

## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="a0d0d-106">设计时错误列表接口</span><span class="sxs-lookup"><span data-stu-id="a0d0d-106">The design-time error list interface</span></span>

<span data-ttu-id="a0d0d-107">如果 Windows 窗体设计器无法加载, 则设计器中将显示错误列表。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-107">If the Windows Forms Designer fails to load, an error list appears in the designer.</span></span> <span data-ttu-id="a0d0d-108">错误按类别进行分组。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-108">The errors are grouped into categories.</span></span> <span data-ttu-id="a0d0d-109">例如，如果具有四个未声明变量的实例，则这些实例会归到同一错误类别中。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="a0d0d-110">每个错误类别包含一个概述错误的简短说明。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-110">Each error category includes a brief description that summarizes the error.</span></span>

<span data-ttu-id="a0d0d-111">通过单击错误类别标题或单击 V 形展开/折叠按钮，可展开或折叠错误类别。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="a0d0d-112">展开错误类别时，将显示以下附加帮助信息：</span><span class="sxs-lookup"><span data-stu-id="a0d0d-112">When you expand an error category, the following additional help is displayed:</span></span>

- <span data-ttu-id="a0d0d-113">此错误的实例。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-113">Instances of this error.</span></span>

- <span data-ttu-id="a0d0d-114">有关此错误的帮助。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-114">Help with this error.</span></span>

- <span data-ttu-id="a0d0d-115">有关此错误的论坛帖子。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-115">Forum posts about this error.</span></span>

### <a name="instances-of-this-error"></a><span data-ttu-id="a0d0d-116">此错误的实例</span><span class="sxs-lookup"><span data-stu-id="a0d0d-116">Instances of this error</span></span>

<span data-ttu-id="a0d0d-117">附加帮助信息中列出了当前项目中所含错误的所有实例。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="a0d0d-118">许多错误包含用以下格式表示的确切位置：[项目名称] [窗体名称]行:[行号]列:[列号]。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="a0d0d-119">单击“转到代码”链接可跳转到代码中发生错误的位置。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>

<span data-ttu-id="a0d0d-120">如果调用堆栈与错误关联，则可单击“显示调用堆栈”链接，这会进一步展开错误以显示调用堆栈。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="a0d0d-121">检查堆栈可获取有价值的调试信息。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="a0d0d-122">例如，可跟踪错误发生之前调用过的函数。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="a0d0d-123">调用堆栈是可选定的，以便进行复制并保存。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-123">The call stack is selectable so that you can copy and save it.</span></span>

> [!NOTE]
> <span data-ttu-id="a0d0d-124">在 Visual Basic 中，设计时错误列表不显示多个错误，但可能显示同一错误的多个实例。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="a0d0d-125">在 Visual C++ 中，错误不含“转到代码”链接/行号链接。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>

### <a name="forum-posts-about-this-error"></a><span data-ttu-id="a0d0d-126">有关此错误的论坛帖子</span><span class="sxs-lookup"><span data-stu-id="a0d0d-126">Forum posts about this error</span></span>

<span data-ttu-id="a0d0d-127">其他帮助包含与该错误相关的论坛帖子的链接。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-127">The additional help includes a link to forum posts related to the error.</span></span> <span data-ttu-id="a0d0d-128">将基于错误消息字符串来搜索论坛。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-128">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="a0d0d-129">你还可以尝试搜索以下论坛:</span><span class="sxs-lookup"><span data-stu-id="a0d0d-129">You can also try searching on the following forums:</span></span>

- [<span data-ttu-id="a0d0d-130">Windows 窗体设计器论坛</span><span class="sxs-lookup"><span data-stu-id="a0d0d-130">Windows Forms Designer forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)

- [<span data-ttu-id="a0d0d-131">Windows 窗体论坛</span><span class="sxs-lookup"><span data-stu-id="a0d0d-131">Windows Forms forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)

### <a name="ignore-and-continue"></a><span data-ttu-id="a0d0d-132">忽略并继续</span><span class="sxs-lookup"><span data-stu-id="a0d0d-132">Ignore and continue</span></span>

<span data-ttu-id="a0d0d-133">可选择忽略错误条件并继续加载设计器。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-133">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="a0d0d-134">选择此操作可能会导致意外行为。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-134">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="a0d0d-135">例如，控件可能不会显示在设计图面上。</span><span class="sxs-lookup"><span data-stu-id="a0d0d-135">For example, controls may not appear on the design surface.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0d0d-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="a0d0d-136">See also</span></span>

- <span data-ttu-id="a0d0d-137">[设计时开发疑难解答](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="a0d0d-137">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
- [<span data-ttu-id="a0d0d-138">控件和组件创作疑难解答</span><span class="sxs-lookup"><span data-stu-id="a0d0d-138">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)
- [<span data-ttu-id="a0d0d-139">设计时开发 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="a0d0d-139">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="a0d0d-140">[Windows 窗体设计器错误信息](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a0d0d-140">[Windows Forms Designer Error Messages](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span></span>
