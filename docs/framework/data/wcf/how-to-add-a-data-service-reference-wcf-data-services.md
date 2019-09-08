---
title: 如何：添加数据服务引用（WCF 数据服务）
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790739"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="fc224-102">如何：添加数据服务引用（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="fc224-102">How to: Add a data service reference (WCF Data Services)</span></span>

<span data-ttu-id="fc224-103">您可以使用 Visual Studio 中的**添加服务引用**对话框添加对 WCF 数据服务的引用。</span><span class="sxs-lookup"><span data-stu-id="fc224-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="fc224-104">这使您可以更轻松地在使用 Visual Studio 开发的客户端应用程序中访问数据服务。</span><span class="sxs-lookup"><span data-stu-id="fc224-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="fc224-105">完成此过程后，会基于从数据服务获取的元数据生成数据类。</span><span class="sxs-lookup"><span data-stu-id="fc224-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="fc224-106">有关详细信息，请参阅[生成数据服务客户端库](generating-the-data-service-client-library-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fc224-106">For more information, see [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="fc224-107">添加数据服务引用</span><span class="sxs-lookup"><span data-stu-id="fc224-107">Add a data service reference</span></span>

1. <span data-ttu-id="fc224-108">（可选）如果数据服务不是解决方案的一部分，且未运行，请启动数据服务，并记下数据服务的 URI。</span><span class="sxs-lookup"><span data-stu-id="fc224-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="fc224-109">在 Visual Studio 的**解决方案资源管理器**中，右键单击客户端项目，然后选择 "**添加** > **服务引用**"。</span><span class="sxs-lookup"><span data-stu-id="fc224-109">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="fc224-110">如果数据服务是当前解决方案的一部分，请单击 "**发现**"。</span><span class="sxs-lookup"><span data-stu-id="fc224-110">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="fc224-111">或</span><span class="sxs-lookup"><span data-stu-id="fc224-111">-or-</span></span>

     <span data-ttu-id="fc224-112">在 "**地址**" 文本框中，键入数据服务的基 URL （例如`http://localhost:1234/Northwind.svc`），然后单击 "**开始**"。</span><span class="sxs-lookup"><span data-stu-id="fc224-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="fc224-113">选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="fc224-113">Select **OK**.</span></span>

     <span data-ttu-id="fc224-114">一个新的代码文件，其中包含可以访问数据服务资源并与其交互的数据类将添加到该项目中。</span><span class="sxs-lookup"><span data-stu-id="fc224-114">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc224-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="fc224-115">See also</span></span>

- [<span data-ttu-id="fc224-116">快速入门</span><span class="sxs-lookup"><span data-stu-id="fc224-116">Quickstart</span></span>](quickstart-wcf-data-services.md)
