---
title: 疑难解答：服务应用程序无法安装
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
ms.openlocfilehash: c45ab03ec4577d88953b0e43531082a46c29e8fd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053538"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="b2a2e-102">疑难解答：服务应用程序无法安装</span><span class="sxs-lookup"><span data-stu-id="b2a2e-102">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="b2a2e-103">如果服务应用程序无法正确安装，请检查以确保服务类的 <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> 属性设置为与该服务安装程序中显示的值相同的值。</span><span class="sxs-lookup"><span data-stu-id="b2a2e-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="b2a2e-104">两个实例中的值必须相同才能正确安装服务。</span><span class="sxs-lookup"><span data-stu-id="b2a2e-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2a2e-105">还可以查看安装日志以获取有关安装进程的反馈。</span><span class="sxs-lookup"><span data-stu-id="b2a2e-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="b2a2e-106">还应该检查以确定是否已安装具有相同名称的其他服务。</span><span class="sxs-lookup"><span data-stu-id="b2a2e-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="b2a2e-107">服务名称必须唯一，安装才能成功。</span><span class="sxs-lookup"><span data-stu-id="b2a2e-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a2e-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="b2a2e-108">See also</span></span>

- [<span data-ttu-id="b2a2e-109">Windows 服务应用程序介绍</span><span class="sxs-lookup"><span data-stu-id="b2a2e-109">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
