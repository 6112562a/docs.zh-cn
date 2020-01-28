---
title: 开发自定义控件
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 9dbc1c4530b3a0f4e579ca67c7ae88c1685222ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746000"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="53074-102">.NET Framework에서 사용자 지정 Windows Forms 컨트롤 개발</span><span class="sxs-lookup"><span data-stu-id="53074-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="53074-103">Windows Forms 컨트롤은 사용자 인터페이스 기능을 캡슐화하고 클라이언트 측 Windows 기반 애플리케이션에서 사용되는 재사용 가능한 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="53074-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="53074-104">Windows Forms은 바로 사용할 수 있는 많은 컨트롤을 제공할 뿐만 아니라 고유한 컨트롤을 개발하기 위한 인프라도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="53074-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="53074-105">기존 컨트롤을 결합 또는 확장하거나 고유한 사용자 지정 컨트롤을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53074-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="53074-106">이 섹션에서는 Windows Forms 컨트롤을 개발하는 데 도움이 되는 배경 정보 및 샘플을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="53074-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53074-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="53074-107">In This Section</span></span>  
 [<span data-ttu-id="53074-108">Windows Forms에서 컨트롤 사용 개요</span><span class="sxs-lookup"><span data-stu-id="53074-108">Overview of Using Controls in Windows Forms</span></span>](overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="53074-109">Windows Forms 애플리케이션에 있는 컨트롤 사용의 필수 요소를 요약해서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53074-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="53074-110">사용자 지정 컨트롤의 종류</span><span class="sxs-lookup"><span data-stu-id="53074-110">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="53074-111"><xref:System.Windows.Forms?displayProperty=nameWithType> 네임스페이스로 작성할 수 있는 다양한 종류의 사용자 지정 컨트롤을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53074-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="53074-112">Windows Forms 컨트롤 개발 기본 사항</span><span class="sxs-lookup"><span data-stu-id="53074-112">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)  
 <span data-ttu-id="53074-113">Windows Forms 컨트롤 개발의 첫 번째 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53074-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="53074-114">Windows Forms 컨트롤의 속성</span><span class="sxs-lookup"><span data-stu-id="53074-114">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)  
 <span data-ttu-id="53074-115">Windows Forms 컨트롤에 속성을 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="53074-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="53074-116">Windows Forms 컨트롤의 이벤트</span><span class="sxs-lookup"><span data-stu-id="53074-116">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)  
 <span data-ttu-id="53074-117">Windows Forms 컨트롤에서 이벤트를 처리 및 정의하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="53074-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="53074-118">Windows Forms 컨트롤의 특성</span><span class="sxs-lookup"><span data-stu-id="53074-118">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="53074-119">사용자 지정 컨트롤 및 구성 요소의 속성이나 다른 멤버에 적용할 수 있는 특성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53074-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="53074-120">사용자 지정 컨트롤 그리기 및 렌더링</span><span class="sxs-lookup"><span data-stu-id="53074-120">Custom Control Painting and Rendering</span></span>](custom-control-painting-and-rendering.md)  
 <span data-ttu-id="53074-121">컨트롤의 모양을 사용자 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="53074-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="53074-122">Windows Forms 컨트롤의 레이아웃</span><span class="sxs-lookup"><span data-stu-id="53074-122">Layout in Windows Forms Controls</span></span>](layout-in-windows-forms-controls.md)  
 <span data-ttu-id="53074-123">컨트롤 및 폼에 사용할 정교한 레이아웃을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="53074-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="53074-124">Windows Forms 컨트롤의 다중 스레딩</span><span class="sxs-lookup"><span data-stu-id="53074-124">Multithreading in Windows Forms Controls</span></span>](multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="53074-125">다중 스레드 컨트롤을 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="53074-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="53074-126">참조</span><span class="sxs-lookup"><span data-stu-id="53074-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="53074-127">이 클래스를 설명하고 모든 해당 멤버의 링크를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="53074-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="53074-128">이 클래스를 설명하고 모든 해당 멤버의 링크를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="53074-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="53074-129">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="53074-129">Related Sections</span></span>  
 <span data-ttu-id="53074-130">[구성 요소의 디자인 타임 특성](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="53074-130">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="53074-131">비주얼 디자이너에서 디자인 타임에 올바르게 표시되도록 구성 요소 및 컨트롤에 적용할 메타데이터 특성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="53074-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="53074-132">[디자인 타임 지원 확장](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="53074-132">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="53074-133">디자인 타임 지원을 제공하는 편집기 및 디자이너와 같은 클래스를 구현하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53074-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="53074-134">[방법: 구성 요소 및 컨트롤 라이선스](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="53074-134">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="53074-135">컨트롤이나 구성 요소에서 라이선스를 구현하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="53074-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="53074-136">또한 [디자인 타임에서 Windows Forms 컨트롤 개발](developing-windows-forms-controls-at-design-time.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53074-136">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>
