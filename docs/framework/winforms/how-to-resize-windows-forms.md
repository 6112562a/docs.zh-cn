---
title: 调整窗体大小
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 8d4ce46ada505f952fc3090d10c5d893338d19f2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739301"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="be111-102">방법: Windows Forms 크기 조정</span><span class="sxs-lookup"><span data-stu-id="be111-102">How to: Resize Windows Forms</span></span>

<span data-ttu-id="be111-103">여러가지 방법으로 Windows Form의 크기를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be111-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="be111-104"><xref:System.Windows.Forms.Form.Size%2A> 속성에 대해 새 값을 설정하거나 <xref:System.Windows.Forms.Control.Height%2A> 또는 <xref:System.Windows.Forms.Control.Width%2A> 속성을 개별적으로 조정하여 프로그래밍 방식으로 폼의 높이와 너비를 모두 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be111-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="be111-105">如果使用的是 Visual Studio，则可以使用 Windows 窗体设计器更改大小。</span><span class="sxs-lookup"><span data-stu-id="be111-105">If you're using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="be111-106">另请参阅[如何：使用设计器调整 Windows 窗体大小](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="be111-106">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>

## <a name="resize-a-form-programmatically"></a><span data-ttu-id="be111-107">以编程方式调整窗体的大小</span><span class="sxs-lookup"><span data-stu-id="be111-107">Resize a form programmatically</span></span>

<span data-ttu-id="be111-108">폼의 <xref:System.Windows.Forms.Form.Size%2A> 속성을 설정하여 런타임에 폼의 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="be111-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>

<span data-ttu-id="be111-109">다음 코드 예제에서는 100 × 100 픽셀로 설정된 폼 크기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="be111-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a><span data-ttu-id="be111-110">以编程方式更改窗体的宽度和高度</span><span class="sxs-lookup"><span data-stu-id="be111-110">Change form width and height programmatically</span></span>

<span data-ttu-id="be111-111"><xref:System.Windows.Forms.Form.Size%2A>가 정의된 후 <xref:System.Windows.Forms.Control.Width%2A> 또는 <xref:System.Windows.Forms.Control.Height%2A> 속성을 사용하여 폼 높이나 너비를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="be111-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

<span data-ttu-id="be111-112">다음 코드 예제에서는 높이가 일정하게 유지되고 폼의 왼쪽 가장자리에서 300픽셀로 설정된 폼의 너비를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="be111-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

<span data-ttu-id="be111-113">-또는-</span><span class="sxs-lookup"><span data-stu-id="be111-113">-or-</span></span>

<span data-ttu-id="be111-114"><xref:System.Windows.Forms.Form.Size%2A> 속성을 설정하여 <xref:System.Drawing.Size.Width%2A> 또는 <xref:System.Drawing.Size.Height%2A>를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="be111-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>

<span data-ttu-id="be111-115">그러나 다음 코드 예제와 같이 이 접근 방식은 단순히 <xref:System.Windows.Forms.Control.Width%2A> 또는 <xref:System.Windows.Forms.Control.Height%2A> 속성을 설정하는 것보다 성가십니다.</span><span class="sxs-lookup"><span data-stu-id="be111-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a><span data-ttu-id="be111-116">以编程方式更改窗体大小</span><span class="sxs-lookup"><span data-stu-id="be111-116">Change form size by increments programmatically</span></span>

<span data-ttu-id="be111-117">폼의 크기를 증가시키려면 <xref:System.Drawing.Size.Width%2A> 및 <xref:System.Drawing.Size.Height%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="be111-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>

<span data-ttu-id="be111-118">다음 코드 예제에서는 현재 설정보다 200픽셀 넓게 설정된 폼의 너비를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="be111-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>

```vb
Form1.Width += 200
```

```csharp
Form1.Width += 200;
```

```cpp
Form1->Width += 200;
```

> [!CAUTION]
> <span data-ttu-id="be111-119"><xref:System.Windows.Forms.Form.Size%2A> 속성을 새로운 <xref:System.Drawing.Size> 구조체로 설정하여 동시에 높이 및 너비 크기를 설정하지 않는 한 항상 <xref:System.Drawing.Size.Height%2A> 또는 <xref:System.Drawing.Size.Width%2A> 속성을 사용하여 폼의 크기를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="be111-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="be111-120"><xref:System.Windows.Forms.Form.Size%2A> 속성은 값 형식인 <xref:System.Drawing.Size> 구조체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="be111-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="be111-121">값 형식의 속성에 새 값을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be111-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="be111-122">따라서 다음 코드 예제는 컴파일되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be111-122">Therefore, the following code example will not compile.</span></span>

```vb
' NOTE: CODE WILL NOT COMPILE
Dim f As New Form()
f.Size.Width += 100
```

```csharp
// NOTE: CODE WILL NOT COMPILE
Form f = new Form();
f.Size.Width += 100;
```

```cpp
// NOTE: CODE WILL NOT COMPILE
Form^ f = gcnew Form();
f->Size->X += 100;
```

## <a name="see-also"></a><span data-ttu-id="be111-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be111-123">See also</span></span>

- [<span data-ttu-id="be111-124">Windows Forms 시작</span><span class="sxs-lookup"><span data-stu-id="be111-124">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="be111-125">Windows Forms 애플리케이션 강화</span><span class="sxs-lookup"><span data-stu-id="be111-125">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
