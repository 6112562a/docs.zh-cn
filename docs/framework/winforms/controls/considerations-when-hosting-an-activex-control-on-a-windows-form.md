---
title: 在 Windows 窗体上承载 ActiveX 控件时的注意事项
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
ms.openlocfilehash: 4b604502e0fea591460f30cae28b64ff1703da65
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589432"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a><span data-ttu-id="54c7f-102">在 Windows 窗体上承载 ActiveX 控件时的注意事项</span><span class="sxs-lookup"><span data-stu-id="54c7f-102">Considerations When Hosting an ActiveX Control on a Windows Form</span></span>
<span data-ttu-id="54c7f-103">尽管 Windows 窗体已经为承载 Windows 窗体控件而进行了优化，但仍可使用 ActiveX 控件。</span><span class="sxs-lookup"><span data-stu-id="54c7f-103">Although Windows Forms have been optimized to host Windows Forms controls, you can still use ActiveX controls.</span></span> <span data-ttu-id="54c7f-104">规划使用 ActiveX 控件的应用程序时应谨记以下注意事项：</span><span class="sxs-lookup"><span data-stu-id="54c7f-104">Keep the following considerations in mind when planning an application that uses ActiveX controls:</span></span>  
  
- <span data-ttu-id="54c7f-105">**安全性** - 公共语言运行时已在代码访问安全性方面得到了增强。</span><span class="sxs-lookup"><span data-stu-id="54c7f-105">**Security** The common language runtime has been enhanced with regard to code access security.</span></span> <span data-ttu-id="54c7f-106">以 Windows 窗体为特色的应用程序在完全信任的环境中运行不会有任何问题；在不完全信任的环境中运行时，大部分功能也是可访问的。</span><span class="sxs-lookup"><span data-stu-id="54c7f-106">Applications featuring Windows Forms can run in a fully trusted environment without issue and in a semi-trusted environment with most of the functionality accessible.</span></span> <span data-ttu-id="54c7f-107">Windows 窗体控件不用编译就可以在浏览器中承载。</span><span class="sxs-lookup"><span data-stu-id="54c7f-107">Windows Forms controls can be hosted in a browser with no complications.</span></span> <span data-ttu-id="54c7f-108">然而，Windows 窗体上的 ActiveX 控件无法利用这些安全性增强功能。</span><span class="sxs-lookup"><span data-stu-id="54c7f-108">However, ActiveX controls on Windows Forms cannot take advantage of these security enhancements.</span></span> <span data-ttu-id="54c7f-109">运行 ActiveX 控件需要非托管的代码权限，这与设置<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType>属性。</span><span class="sxs-lookup"><span data-stu-id="54c7f-109">Running an ActiveX control requires unmanaged code permission, which is set with the <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="54c7f-110">有关安全和非托管的代码权限的详细信息，请参阅<xref:System.Security.Permissions.SecurityPermissionAttribute>。</span><span class="sxs-lookup"><span data-stu-id="54c7f-110">For more information about security and unmanaged code permission, see <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span></span>  
  
- <span data-ttu-id="54c7f-111">**总拥有成本** - 添加到 Windows 窗体的 ActiveX 控件将作为一个整体部署到该 Windows 窗体中，这会显著增加所创建文件的大小。</span><span class="sxs-lookup"><span data-stu-id="54c7f-111">**Total Cost of Ownership** ActiveX controls added to a Windows Form are deployed with that Windows Form in their entirety, which can add significantly to the size of the file(s) created.</span></span> <span data-ttu-id="54c7f-112">另外，在 Windows 窗体上使用 ActiveX 控件时需要写入注册表。</span><span class="sxs-lookup"><span data-stu-id="54c7f-112">Additionally, using ActiveX controls on Windows Forms requires writing to the registry.</span></span> <span data-ttu-id="54c7f-113">对用户的计算机来说，这比 Windows 窗体控件更具侵入性，因为后者不需要这样做。</span><span class="sxs-lookup"><span data-stu-id="54c7f-113">This is more invasive to a user's computer than Windows Forms controls, which do not require this.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="54c7f-114">使用 ActiveX 控件时需要使用 COM 互操作包装器。</span><span class="sxs-lookup"><span data-stu-id="54c7f-114">Working with an ActiveX control requires the use of a COM interop wrapper.</span></span> <span data-ttu-id="54c7f-115">有关详细信息，请参阅 [Visual Basic 和 Visual C# 中的 COM 互操作性](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="54c7f-115">For more information, see [COM Interoperability in Visual Basic and Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="54c7f-116">如果 ActiveX 控件的成员的名称与.NET Framework 中定义的名称，则 ActiveX 控件导入程序将成员名称加上前缀**Ctl**在创建时<xref:System.Windows.Forms.AxHost>派生的类。</span><span class="sxs-lookup"><span data-stu-id="54c7f-116">If the name of a member of the ActiveX control matches a name defined in the .NET Framework, then the ActiveX Control Importer will prefix the member name with **Ctl** when it creates the <xref:System.Windows.Forms.AxHost> derived class.</span></span> <span data-ttu-id="54c7f-117">例如，如果 ActiveX 控件有一个名为成员**布局**，将其重命名**CtlLayout** AxHost 派生类中因为**布局**中定义事件。NET Framework。</span><span class="sxs-lookup"><span data-stu-id="54c7f-117">For example, if your ActiveX control has a member named **Layout**, it is renamed **CtlLayout** in the AxHost-derived class because the **Layout** event is defined within the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c7f-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="54c7f-118">See also</span></span>

- [<span data-ttu-id="54c7f-119">如何：向 Windows 窗体添加 ActiveX 控件</span><span class="sxs-lookup"><span data-stu-id="54c7f-119">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="54c7f-120">代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="54c7f-120">Code Access Security</span></span>](../../misc/code-access-security.md)
- <span data-ttu-id="54c7f-121">[不同语言和库中的控件和可编程对象的比较](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="54c7f-121">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="54c7f-122">将控件置于 Windows 窗体上</span><span class="sxs-lookup"><span data-stu-id="54c7f-122">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="54c7f-123">Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="54c7f-123">Windows Forms Controls</span></span>](index.md)
