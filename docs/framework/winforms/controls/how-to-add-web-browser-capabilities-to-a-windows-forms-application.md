---
title: 将 web 浏览器功能添加到应用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: 5feecd975700745541103e81fd09bfc5e788c729
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747224"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="eb99d-102">방법: Windows Forms 애플리케이션에 웹 브라우저 기능 추가</span><span class="sxs-lookup"><span data-stu-id="eb99d-102">How to: Add Web Browser Capabilities to a Windows Forms Application</span></span>
<span data-ttu-id="eb99d-103"><xref:System.Windows.Forms.WebBrowser> 컨트롤을 통해 애플리케이션에 웹 브라우저 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb99d-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="eb99d-104">컨트롤은 기본적으로 웹 브라우저처럼 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="eb99d-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="eb99d-105"><xref:System.Windows.Forms.WebBrowser.Url%2A> 속성을 설정하여 초기 URL을 로드한 후 하이퍼링크를 클릭하거나 바로 가기 키를 통해 탐색 기록을 앞뒤로 이동하여 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb99d-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="eb99d-106">기본적으로 오른쪽 클릭 바로 가기 메뉴를 통해 추가 브라우저 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb99d-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="eb99d-107">컨트롤에 끌어서 놓아 새 문서를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb99d-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="eb99d-108"><xref:System.Windows.Forms.WebBrowser> 컨트롤에는 Internet Explorer에 있는 것과 비슷한 사용자 인터페이스 기능을 구현하는 데 사용할 수 있는 여러 속성, 메서드 및 이벤트도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb99d-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>  
  
 <span data-ttu-id="eb99d-109">다음 코드 예제에서는 주소 표시줄, 일반적인 브라우저 단추, **파일** 메뉴, 상태 표시줄 및 현재 페이지 제목을 표시하는 제목 표시줄을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="eb99d-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb99d-110">示例</span><span class="sxs-lookup"><span data-stu-id="eb99d-110">Example</span></span>  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eb99d-111">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="eb99d-111">Compiling the Code</span></span>  
 <span data-ttu-id="eb99d-112">이 예제에는 다음 사항이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="eb99d-112">This example requires:</span></span>  
  
- <span data-ttu-id="eb99d-113">`System`, `System.Drawing` 및 `System.Windows.Forms` 어셈블리에 대한 참조</span><span class="sxs-lookup"><span data-stu-id="eb99d-113">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb99d-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb99d-114">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="eb99d-115">WebBrowser 컨트롤</span><span class="sxs-lookup"><span data-stu-id="eb99d-115">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
