---
title: 如何：创建应用程序设置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: 52687347707139ba583ef4dfdeebbb41d568e95c
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441354"
---
# <a name="how-to-create-application-settings"></a><span data-ttu-id="df1b4-102">如何：创建应用程序设置</span><span class="sxs-lookup"><span data-stu-id="df1b4-102">How to: Create Application Settings</span></span>
<span data-ttu-id="df1b4-103">使用托管代码时，你可以创建新的应用程序设置并将其绑定窗体或窗体控件的属性上，以便在运行时自动加载和保存这些设置。</span><span class="sxs-lookup"><span data-stu-id="df1b4-103">Using managed code, you can create new application settings and bind them to properties on your form or your form's controls, so that these settings are loaded and saved automatically at run time.</span></span>  
  
 <span data-ttu-id="df1b4-104">在以下过程中，手动创建从 <xref:System.Configuration.ApplicationSettingsBase> 派生的包装类。</span><span class="sxs-lookup"><span data-stu-id="df1b4-104">In the following procedure, you manually create a wrapper class that derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="df1b4-105">对于此类，你可以为每个想要公开的应用程序设置添加可公开访问的属性。</span><span class="sxs-lookup"><span data-stu-id="df1b4-105">To this class you add a publicly accessible property for each application setting that you want to expose.</span></span>  
  
 <span data-ttu-id="df1b4-106">你还可以使用 Visual Studio 设计器中的最小代码执行该过程。</span><span class="sxs-lookup"><span data-stu-id="df1b4-106">You can also perform this procedure using minimal code in the Visual Studio designer.</span></span>  <span data-ttu-id="df1b4-107">另请参阅[如何：创建使用设计器的应用程序设置](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="df1b4-107">Also see [How to: Create Application Settings Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).</span></span>  
  
### <a name="to-create-new-application-settings-programmatically"></a><span data-ttu-id="df1b4-108">以编程的方式创建新的应用程序设置</span><span class="sxs-lookup"><span data-stu-id="df1b4-108">To create new Application Settings programmatically</span></span>  
  
1.  <span data-ttu-id="df1b4-109">向你的项目添加新类，并对其重命名。</span><span class="sxs-lookup"><span data-stu-id="df1b4-109">Add a new class to your project, and rename it.</span></span> <span data-ttu-id="df1b4-110">对于此过程中，我们将调用此类`MyUserSettings`。</span><span class="sxs-lookup"><span data-stu-id="df1b4-110">For this procedure, we will call this class `MyUserSettings`.</span></span> <span data-ttu-id="df1b4-111">更改类定义，以使类从 <xref:System.Configuration.ApplicationSettingsBase> 派生。</span><span class="sxs-lookup"><span data-stu-id="df1b4-111">Change the class definition so that the class derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span>  
  
2.  <span data-ttu-id="df1b4-112">为你需要的每个应用程序设置定义此包装类的属性，并将该属性应用到 <xref:System.Configuration.ApplicationScopedSettingAttribute> 或 <xref:System.Configuration.UserScopedSettingAttribute>，具体取决于设置的作用域。</span><span class="sxs-lookup"><span data-stu-id="df1b4-112">Define a property on this wrapper class for each application setting you require, and apply that property with either the <xref:System.Configuration.ApplicationScopedSettingAttribute> or <xref:System.Configuration.UserScopedSettingAttribute>, depending on the scope of the setting.</span></span> <span data-ttu-id="df1b4-113">有关设置作用域的详细信息，请参阅[应用程序设置概述](../../../../docs/framework/winforms/advanced/application-settings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="df1b4-113">For more information about settings scope, see [Application Settings Overview](../../../../docs/framework/winforms/advanced/application-settings-overview.md).</span></span> <span data-ttu-id="df1b4-114">现在，代码应如下所示：</span><span class="sxs-lookup"><span data-stu-id="df1b4-114">By now, your code should look like this:</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  <span data-ttu-id="df1b4-115">在你的应用程序中创建此包装类的实例。</span><span class="sxs-lookup"><span data-stu-id="df1b4-115">Create an instance of this wrapper class in your application.</span></span> <span data-ttu-id="df1b4-116">该实例通常为主窗体的私有成员。</span><span class="sxs-lookup"><span data-stu-id="df1b4-116">It will commonly be a private member of the main form.</span></span> <span data-ttu-id="df1b4-117">对类进行定义后，你需要将其绑定到属性；在这种情况下，是指绑定到你窗体的 <xref:System.Windows.Forms.Form.BackColor%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="df1b4-117">Now that you have defined your class, you need to bind it to a property; in this case, the <xref:System.Windows.Forms.Form.BackColor%2A> property of your form.</span></span> <span data-ttu-id="df1b4-118">可以完成此操作在窗体的`Load`事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="df1b4-118">You can accomplish this in your form's `Load` event handler.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="df1b4-119">如果你在运行时提供了一种更改设置的方法，则关闭窗体时需要将用户的当前设置保存到磁盘，否则将丢失这些更改。</span><span class="sxs-lookup"><span data-stu-id="df1b4-119">If you provide a way to change settings at run time, you will need to save the user's current settings to disk when your form closes, or else these changes will be lost.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     <span data-ttu-id="df1b4-120">现在，你已成功创建了一个新的应用程序设置并将其绑定到了指定的属性中。</span><span class="sxs-lookup"><span data-stu-id="df1b4-120">You have now successfully created a new application setting and bound it to the specified property.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="df1b4-121">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="df1b4-121">.NET Framework Security</span></span>  
 <span data-ttu-id="df1b4-122">默认的设置提供程序 <xref:System.Configuration.LocalFileSettingsProvider> 会将配置文件的信息视为纯文本处理。</span><span class="sxs-lookup"><span data-stu-id="df1b4-122">The default settings provider, <xref:System.Configuration.LocalFileSettingsProvider>, persists information to configuration files as plain text.</span></span> <span data-ttu-id="df1b4-123">这将限制由当前用户由的操作系统提供的文件访问安全性的安全。</span><span class="sxs-lookup"><span data-stu-id="df1b4-123">This limits security to the file access security provided by the operating system for the current user.</span></span> <span data-ttu-id="df1b4-124">因此，必须谨慎处理配置文件中存储的信息。</span><span class="sxs-lookup"><span data-stu-id="df1b4-124">Because of this, care must be taken with the information stored in configuration files.</span></span> <span data-ttu-id="df1b4-125">例如，应用程序设置一种常见的用法就是，存储指向应用程序数据存储的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="df1b4-125">For example, one common use for application settings is to store connection strings that point to the application's data store.</span></span> <span data-ttu-id="df1b4-126">但是，出于安全考虑，此类字符串不应包括密码。</span><span class="sxs-lookup"><span data-stu-id="df1b4-126">However, because of security concerns, such strings should not include passwords.</span></span> <span data-ttu-id="df1b4-127">有关连接字符串的详细信息，请参阅 <xref:System.Configuration.SpecialSetting>。</span><span class="sxs-lookup"><span data-stu-id="df1b4-127">For more information about connection strings, see <xref:System.Configuration.SpecialSetting>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df1b4-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="df1b4-128">See also</span></span>
- <xref:System.Configuration.SpecialSettingAttribute>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [<span data-ttu-id="df1b4-129">应用程序设置概述</span><span class="sxs-lookup"><span data-stu-id="df1b4-129">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="df1b4-130">如何：验证应用程序设置</span><span class="sxs-lookup"><span data-stu-id="df1b4-130">How to: Validate Application Settings</span></span>](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)
