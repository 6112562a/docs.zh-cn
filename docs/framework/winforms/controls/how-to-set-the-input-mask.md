---
title: 如何：设置输入掩码
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06dee48765653ac7a659246cc3dfe865c795ca21
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949148"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="11fcc-102">如何：设置输入掩码</span><span class="sxs-lookup"><span data-stu-id="11fcc-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="11fcc-103">掩码文本框控件是一个增强型文本框控件, 支持用于接受或拒绝用户输入的声明性语法。</span><span class="sxs-lookup"><span data-stu-id="11fcc-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="11fcc-104">设置 Mask 属性可以指定允许的用户输入, 而无需在应用程序中编写任何自定义验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="11fcc-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="11fcc-105">有关详细信息, 请参阅<xref:System.Windows.Forms.MaskedTextBox>类的 "备注" 部分。</span><span class="sxs-lookup"><span data-stu-id="11fcc-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="11fcc-106">手动设置 Mask 属性</span><span class="sxs-lookup"><span data-stu-id="11fcc-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="11fcc-107">如果你熟悉 Mask 属性支持的字符, 则可以手动输入。</span><span class="sxs-lookup"><span data-stu-id="11fcc-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="11fcc-108">有关 Mask 属性支持的字符摘要, 请参阅<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>属性的 "备注" 部分。</span><span class="sxs-lookup"><span data-stu-id="11fcc-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="11fcc-109">手动设置 Mask 属性</span><span class="sxs-lookup"><span data-stu-id="11fcc-109">To set the Mask property manually</span></span>  
  
1. <span data-ttu-id="11fcc-110">在 "**设计**" 视图中<xref:System.Windows.Forms.MaskedTextBox>, 选择。</span><span class="sxs-lookup"><span data-stu-id="11fcc-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2. <span data-ttu-id="11fcc-111">在 "**属性**" 窗口中, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>找到 "属性"。</span><span class="sxs-lookup"><span data-stu-id="11fcc-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3. <span data-ttu-id="11fcc-112">键入所需的掩码。</span><span class="sxs-lookup"><span data-stu-id="11fcc-112">Type the mask that you want.</span></span> <span data-ttu-id="11fcc-113">例如，键入 `###`。</span><span class="sxs-lookup"><span data-stu-id="11fcc-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="11fcc-114">使用 "输入掩码" 对话框</span><span class="sxs-lookup"><span data-stu-id="11fcc-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="11fcc-115">"输入掩码" 对话框提供一些预定义的输入掩码。</span><span class="sxs-lookup"><span data-stu-id="11fcc-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="11fcc-116">还可以更改预定义掩码或手动输入自己的掩码。</span><span class="sxs-lookup"><span data-stu-id="11fcc-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="11fcc-117">打开 "输入掩码" 对话框</span><span class="sxs-lookup"><span data-stu-id="11fcc-117">To open the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="11fcc-118">在 "**设计**" 视图中<xref:System.Windows.Forms.MaskedTextBox>, 选择。</span><span class="sxs-lookup"><span data-stu-id="11fcc-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1. <span data-ttu-id="11fcc-119">单击智能标记以打开**MaskedTextBox 任务**面板。</span><span class="sxs-lookup"><span data-stu-id="11fcc-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2. <span data-ttu-id="11fcc-120">单击 "**设置掩码**"。</span><span class="sxs-lookup"><span data-stu-id="11fcc-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="11fcc-121">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="11fcc-121">\- or -</span></span>  
  
    1. <span data-ttu-id="11fcc-122">在 "**属性**" 窗口中, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>选择属性。</span><span class="sxs-lookup"><span data-stu-id="11fcc-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2. <span data-ttu-id="11fcc-123">单击 "属性值" 列中的省略号按钮。</span><span class="sxs-lookup"><span data-stu-id="11fcc-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="11fcc-124">此时将显示 "**输入掩码**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="11fcc-124">The **Input Mask** dialog box appears.</span></span>  
  
### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="11fcc-125">使用 "输入掩码" 对话框</span><span class="sxs-lookup"><span data-stu-id="11fcc-125">To use the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="11fcc-126">可有可无单击列表中的一个预定义掩码。</span><span class="sxs-lookup"><span data-stu-id="11fcc-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2. <span data-ttu-id="11fcc-127">可有可无在 "**掩码**" 框中编辑预定义掩码。</span><span class="sxs-lookup"><span data-stu-id="11fcc-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3. <span data-ttu-id="11fcc-128">可有可无在 "**掩码**" 框中键入新掩码。</span><span class="sxs-lookup"><span data-stu-id="11fcc-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="11fcc-129">也就是说, 您不必使用其中一个预定义掩码。</span><span class="sxs-lookup"><span data-stu-id="11fcc-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="11fcc-130">"预览" 框显示用户在中<xref:System.Windows.Forms.MaskedTextBox>看到的字符。</span><span class="sxs-lookup"><span data-stu-id="11fcc-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="11fcc-131">这些字符是帮助用户正确输入数据的指南。</span><span class="sxs-lookup"><span data-stu-id="11fcc-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4. <span data-ttu-id="11fcc-132">选中或清除 "**使用 ValidatingType** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="11fcc-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="11fcc-133">"**使用 ValidatingType** " 复选框指定数据类型是否用于验证用户输入的数据。</span><span class="sxs-lookup"><span data-stu-id="11fcc-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="11fcc-134">有关更多信息，请参见 <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="11fcc-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5. <span data-ttu-id="11fcc-135">单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="11fcc-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="11fcc-136">掩码在 "**属性**" 窗口的 " **mask** " 属性中输入。</span><span class="sxs-lookup"><span data-stu-id="11fcc-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fcc-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="11fcc-137">See also</span></span>

- [<span data-ttu-id="11fcc-138">演练：使用 MaskedTextBox 控件</span><span class="sxs-lookup"><span data-stu-id="11fcc-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
