---
title: 可视化继承
ms.date: 03/30/2017
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
ms.openlocfilehash: c6aa104a1c9ebe6f59c11ce70e3352169132e714
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732475"
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="fc1e7-102">Windows Forms 시각적 상속</span><span class="sxs-lookup"><span data-stu-id="fc1e7-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="fc1e7-103">경우에 따라 프로젝트에서 이전 프로젝트에서 작성한 것과 비슷한 폼을 필요로 하는지 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="fc1e7-104">또는 이후에 프로젝트 내에서 다시 사용할 워터마크나 특정 컨트롤 레이아웃 등의 설정이 포함되고 반복마다 원본 폼 템플릿에 대한 수정이 포함된 기본적인 폼을 만들려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="fc1e7-105">폼 상속을 사용하면 기본 폼을 만든 다음 기본 폼을 상속하고 필요한 모든 원래 설정을 유지하면서 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="fc1e7-106">프로그래밍 방식으로 또는 시각적 상속 선택을 사용하여 파생 클래스 폼을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc1e7-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="fc1e7-107">In This Section</span></span>  
 [<span data-ttu-id="fc1e7-108">방법: Windows Forms 상속</span><span class="sxs-lookup"><span data-stu-id="fc1e7-108">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)  
 <span data-ttu-id="fc1e7-109">코드에 상속된 폼을 만들도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="fc1e7-110">방법: 상속 선택 대화 상자를 사용하여 폼 상속</span><span class="sxs-lookup"><span data-stu-id="fc1e7-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="fc1e7-111">상속 선택으로 상속된 폼을 만들도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="fc1e7-112">기본 폼의 모양 수정 효과</span><span class="sxs-lookup"><span data-stu-id="fc1e7-112">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="fc1e7-113">기본 폼의 컨트롤과 해당 속성을 변경하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="fc1e7-114">연습: 시각적 상속 설명</span><span class="sxs-lookup"><span data-stu-id="fc1e7-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="fc1e7-115">기본 Windows Form을 만들고 클래스 라이브러리로 컴파일하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="fc1e7-116">이 클래스 라이브러리를 다른 프로젝트로 가져와 기본 폼에서 상속하는 새 폼을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="fc1e7-117">방법: Modifiers 및 GenerateMember 속성 사용</span><span class="sxs-lookup"><span data-stu-id="fc1e7-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="fc1e7-118">Windows Forms 디자이너에서 구성 요소에 대한 멤버 변수를 생성할 때와 관련된 `GenerateMember` 및 `Modifiers` 속성을 사용하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fc1e7-119">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="fc1e7-119">Related Sections</span></span>  
 [<span data-ttu-id="fc1e7-120">상속 기본 사항(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc1e7-120">Inheritance basics (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="fc1e7-121">다른 클래스에 대한 기본 클래스 역할을 하는 Visual Basic 클래스를 정의하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="fc1e7-122">클래스</span><span class="sxs-lookup"><span data-stu-id="fc1e7-122">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="fc1e7-123">단일 상속이 허용되는 C# 클래스 접근 방식을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="fc1e7-124">Visual Basic에서 상속된 이벤트 처리기 관련 문제 해결</span><span class="sxs-lookup"><span data-stu-id="fc1e7-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="fc1e7-125">상속된 구성 요소의 이벤트 처리기에서 발생하는 일반적인 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1e7-125">Lists common issues that arise with event handlers in inherited components</span></span>
