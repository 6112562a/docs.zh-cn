---
title: 如何：继续 Windows 服务 (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
author: ghogen
ms.openlocfilehash: a10e05b0460608a9e67ee4527adf80be3d47438e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053639"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="66335-102">如何：继续 Windows 服务 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66335-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="66335-103">本示例使用 <xref:System.ServiceProcess.ServiceController> 组件继续在本地计算机上执行 IIS 管理服务。</span><span class="sxs-lookup"><span data-stu-id="66335-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66335-104">示例</span><span class="sxs-lookup"><span data-stu-id="66335-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="66335-105">此代码示例也可作为 IntelliSense 代码片段。</span><span class="sxs-lookup"><span data-stu-id="66335-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="66335-106">在代码片段选取器中，它位于“Windows 操作系统 > Windows 服务”中。</span><span class="sxs-lookup"><span data-stu-id="66335-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="66335-107">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="66335-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="66335-108">编译代码</span><span class="sxs-lookup"><span data-stu-id="66335-108">Compiling the Code</span></span>  
 <span data-ttu-id="66335-109">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="66335-109">This example requires:</span></span>  
  
- <span data-ttu-id="66335-110">对 System.serviceprocess.dll 的项目引用。</span><span class="sxs-lookup"><span data-stu-id="66335-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="66335-111">对 <xref:System.ServiceProcess> 命名空间成员的访问权限。</span><span class="sxs-lookup"><span data-stu-id="66335-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="66335-112">如果未在代码中完全限定成员名称，则添加 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="66335-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="66335-113">有关详细信息，请参阅 [Imports 语句（.NET 命名空间和类型）](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="66335-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="66335-114">可靠编程</span><span class="sxs-lookup"><span data-stu-id="66335-114">Robust Programming</span></span>  
 <span data-ttu-id="66335-115">默认情况下，<xref:System.ServiceProcess.ServiceController> 类的 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 属性是本地计算机。</span><span class="sxs-lookup"><span data-stu-id="66335-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="66335-116">要在其他计算机上引用 Windows 服务，请将 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 属性更改为该计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="66335-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="66335-117">在服务控制器状态为 <xref:System.ServiceProcess.ServiceControllerStatus.Paused> 之前，无法调用服务上的 <xref:System.ServiceProcess.ServiceController.Continue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="66335-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="66335-118">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="66335-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="66335-119">服务无法恢复。</span><span class="sxs-lookup"><span data-stu-id="66335-119">The service cannot be resumed.</span></span> <span data-ttu-id="66335-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="66335-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="66335-121">访问 API 时出错。</span><span class="sxs-lookup"><span data-stu-id="66335-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="66335-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="66335-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="66335-123">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="66335-123">.NET Framework Security</span></span>  
 <span data-ttu-id="66335-124">通过使用 <xref:System.ServiceProcess.ServiceControllerPermissionAccess> 枚举在 <xref:System.ServiceProcess.ServiceControllerPermission> 类中设置权限，可以限制计算机上的服务控制。</span><span class="sxs-lookup"><span data-stu-id="66335-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="66335-125">通过使用 <xref:System.Security.Permissions.PermissionState> 枚举在 <xref:System.Security.Permissions.SecurityPermission> 类中设置权限，可以限制访问服务信息。</span><span class="sxs-lookup"><span data-stu-id="66335-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66335-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="66335-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="66335-127">如何：暂停 Windows 服务 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66335-127">How to: Pause a Windows Service (Visual Basic)</span></span>](how-to-pause-a-windows-service-visual-basic.md)
