---
title: 如何：使用 BindingSource 和 INotifyPropertyChanged 接口引发更改通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 6a622e64076d2ed2a073dc0f0e55204d1767cfd7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591831"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="6884a-102">如何：使用 BindingSource 和 INotifyPropertyChanged 接口引发更改通知</span><span class="sxs-lookup"><span data-stu-id="6884a-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="6884a-103"><xref:System.Windows.Forms.BindingSource> 组件将在数据源中包含的类型实现 <xref:System.ComponentModel.INotifyPropertyChanged> 接口时自动删除数据源中的更改，并在属性值更改时引发 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="6884a-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="6884a-104">上述操作非常有用，因为已绑定到 <xref:System.Windows.Forms.BindingSource> 的控件之后会在数据源值更改时自动更新。</span><span class="sxs-lookup"><span data-stu-id="6884a-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6884a-105">如果数据源实现 <xref:System.ComponentModel.INotifyPropertyChanged>，并且你正在执行异步操作，则不应更改后台线程上的数据源。</span><span class="sxs-lookup"><span data-stu-id="6884a-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="6884a-106">相反，应读取后台线程上的数据，并将数据合并到 UI 线程上的列表。</span><span class="sxs-lookup"><span data-stu-id="6884a-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6884a-107">示例</span><span class="sxs-lookup"><span data-stu-id="6884a-107">Example</span></span>  
 <span data-ttu-id="6884a-108">下面的代码示例演示了如何简单实现 <xref:System.ComponentModel.INotifyPropertyChanged> 接口。</span><span class="sxs-lookup"><span data-stu-id="6884a-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="6884a-109">它还演示了当将 <xref:System.Windows.Forms.BindingSource> 绑定到 <xref:System.ComponentModel.INotifyPropertyChanged> 类型的列表时，<xref:System.Windows.Forms.BindingSource> 如何将数据源更改自动传递到绑定控件。</span><span class="sxs-lookup"><span data-stu-id="6884a-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="6884a-110">如果使用 `CallerMemberName` 特性，则调用 `NotifyPropertyChanged` 方法不必将属性名称指定为字符串参数。</span><span class="sxs-lookup"><span data-stu-id="6884a-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="6884a-111">有关详细信息，请参阅[调用方信息 (C#)](../../../csharp/programming-guide/concepts/caller-information.md)或[调用方信息 (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md)。</span><span class="sxs-lookup"><span data-stu-id="6884a-111">For more information, see [Caller Information (C#)](../../../csharp/programming-guide/concepts/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6884a-112">编译代码</span><span class="sxs-lookup"><span data-stu-id="6884a-112">Compiling the Code</span></span>  
 <span data-ttu-id="6884a-113">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="6884a-113">This example requires:</span></span>  
  
- <span data-ttu-id="6884a-114">对 System、System.Data、System.Drawing 和 System.Windows.Forms 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="6884a-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6884a-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="6884a-115">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="6884a-116">BindingSource 组件</span><span class="sxs-lookup"><span data-stu-id="6884a-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="6884a-117">如何：使用 BindingSource ResetItem 方法引发更改通知</span><span class="sxs-lookup"><span data-stu-id="6884a-117">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
