---
title: 定义控件属性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: 0fec817226a7da4b44ec992f9e384a2ad5449001
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746109"
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="7961d-102">Windows Forms 컨트롤에서 속성 정의</span><span class="sxs-lookup"><span data-stu-id="7961d-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="7961d-103">속성의 개요는 [속성 개요](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7961d-103">For an overview of properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="7961d-104">속성을 정의할 때 다음과 같은 몇 가지 주요 고려 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-104">There are a few important considerations when defining a property:</span></span>  
  
- <span data-ttu-id="7961d-105">정의한 속성에 특성을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="7961d-106">특성은 디자이너가 속성을 표시하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="7961d-107">자세한 내용은 [구성 요소의 디자인 타임 특성](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7961d-107">For details, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
- <span data-ttu-id="7961d-108">如果更改属性会影响控件的可视显示，请从 `set` 访问器调用 <xref:System.Windows.Forms.Control.Invalidate%2A> 方法（控件从 <xref:System.Windows.Forms.Control>继承）。</span><span class="sxs-lookup"><span data-stu-id="7961d-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="7961d-109"><xref:System.Windows.Forms.Control.Invalidate%2A> 依次调用用于重绘控件的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7961d-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="7961d-110">多次调用 <xref:System.Windows.Forms.Control.Invalidate%2A> 会导致对 <xref:System.Windows.Forms.Control.OnPaint%2A> 的单个调用，从而提高效率。</span><span class="sxs-lookup"><span data-stu-id="7961d-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
- <span data-ttu-id="7961d-111">.NET Framework 클래스 라이브러리는 정수, 10진수 숫자, 부울 값 등과 같은 일반적인 데이터 형식에 대해 형식 변환기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="7961d-112">형식 변환기의 목적은 일반적으로 문자열을 값으로 변환하도록 제공합니다(문자열 데이터에서 다른 데이터 형식으로).</span><span class="sxs-lookup"><span data-stu-id="7961d-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="7961d-113">일반적인 데이터 형식은 값을 문자열로 변환하고 문자열을 적절한 데이터 형식으로 변환하는 기본 형식 변환기와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="7961d-114">사용자 지정(즉, 비표준) 데이터 형식인 속성을 정의하는 경우 형식 변환기를 지정하는 특성을 적용하여 해당 속성과 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="7961d-115">특성을 사용하여 사용자 지정 UI 형식 편집기를 속성과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="7961d-116">UI 형식 편집기는 속성이나 데이터 형식을 편집하는 사용자 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="7961d-117">색 선택은 UI 형식 편집기의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="7961d-118">이 항목의 끝에 특성의 예가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7961d-119">사용자 지정 속성에 형식 변환기 또는 UI 형식 편집기를 사용할 수 없는 경우 [디자인 타임 지원 확장](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))에 설명된 대로 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span></span>  
  
 <span data-ttu-id="7961d-120">다음 코드 조각은 사용자 지정 컨트롤 `FlashTrackBar`에 대해 `EndColor`이라는 사용자 지정 속성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
```vb  
Public Class FlashTrackBar  
   Inherits Control  
   ...  
   ' Private data member that backs the EndColor property.  
   Private _endColor As Color = Color.LimeGreen  
  
   ' The Category attribute tells the designer to display  
   ' it in the Flash grouping.   
   ' The Description attribute provides a description of  
   ' the property.   
   <Category("Flash"), _  
   Description("The ending color of the bar.")>  _  
   Public Property EndColor() As Color  
      ' The public property EndColor accesses _endColor.  
      Get  
         Return _endColor  
      End Get  
      Set  
         _endColor = value  
         If Not (baseBackground Is Nothing) And showGradient Then  
            baseBackground.Dispose()  
            baseBackground = Nothing  
         End If  
         ' The Invalidate method calls the OnPaint method, which redraws    
         ' the control.  
         Invalidate()  
      End Set  
   End Property  
   ...  
End Class  
```  
  
```csharp  
public class FlashTrackBar : Control {  
   ...  
   // Private data member that backs the EndColor property.  
   private Color endColor = Color.LimeGreen;  
   // The Category attribute tells the designer to display  
   // it in the Flash grouping.   
   // The Description attribute provides a description of  
   // the property.   
   [  
   Category("Flash"),  
   Description("The ending color of the bar.")  
   ]  
   // The public property EndColor accesses endColor.  
   public Color EndColor {  
      get {  
         return endColor;  
      }  
      set {  
         endColor = value;  
         if (baseBackground != null && showGradient) {  
            baseBackground.Dispose();  
            baseBackground = null;  
         }  
         // The Invalidate method calls the OnPaint method, which redraws   
         // the control.  
         Invalidate();  
      }  
   }  
   ...  
}  
```  
  
 <span data-ttu-id="7961d-121">다음 코드 조각은 형식 변환기 및 UI 형식 편집기를 속성 `Value`과 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="7961d-122">在这种情况下 `Value` 是一个整数，并且具有默认类型转换器，但 <xref:System.ComponentModel.TypeConverterAttribute> 特性应用一个自定义类型转换器（`FlashTrackBarValueConverter`），该转换器使设计器能够将其显示为百分比。</span><span class="sxs-lookup"><span data-stu-id="7961d-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="7961d-123">UI 형식 편집기인 `FlashTrackBarValueEditor`은 백분율을 시각적으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7961d-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="7961d-124">此示例还显示 <xref:System.ComponentModel.TypeConverterAttribute> 或 <xref:System.ComponentModel.EditorAttribute> 特性指定的类型转换器或编辑器将重写默认转换器。</span><span class="sxs-lookup"><span data-stu-id="7961d-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
```vb  
<Category("Flash"), _  
TypeConverter(GetType(FlashTrackBarValueConverter)), _  
Editor(GetType(FlashTrackBarValueEditor), _  
GetType(UITypeEditor)), _  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")>  _  
Public ReadOnly Property Value() As Integer  
...  
End Property  
```  
  
```csharp  
[  
Category("Flash"),   
TypeConverter(typeof(FlashTrackBarValueConverter)),  
Editor(typeof(FlashTrackBarValueEditor), typeof(UITypeEditor)),  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")  
]  
public int Value {  
...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7961d-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7961d-125">See also</span></span>

- [<span data-ttu-id="7961d-126">Windows Forms 컨트롤의 속성</span><span class="sxs-lookup"><span data-stu-id="7961d-126">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="7961d-127">ShouldSerialize 및 Reset 메서드를 사용하여 기본값 정의</span><span class="sxs-lookup"><span data-stu-id="7961d-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [<span data-ttu-id="7961d-128">속성 변경 이벤트</span><span class="sxs-lookup"><span data-stu-id="7961d-128">Property-Changed Events</span></span>](property-changed-events.md)
- [<span data-ttu-id="7961d-129">Windows Forms 컨트롤의 특성</span><span class="sxs-lookup"><span data-stu-id="7961d-129">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
