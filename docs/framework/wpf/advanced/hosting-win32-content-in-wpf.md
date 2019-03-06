---
title: 在 WPF 中承载 Win32 内容
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: 9764b995cea0ba5c93625495509b7ee2dd8393ff
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370028"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="5454b-102">在 WPF 中承载 Win32 内容</span><span class="sxs-lookup"><span data-stu-id="5454b-102">Hosting Win32 Content in WPF</span></span>
## <a name="prerequisites"></a><span data-ttu-id="5454b-103">系统必备</span><span class="sxs-lookup"><span data-stu-id="5454b-103">Prerequisites</span></span>  
 <span data-ttu-id="5454b-104">请参阅[WPF 和 Win32 互操作](wpf-and-win32-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="5454b-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="5454b-105">Win32 Windows Presentation Framework (HwndHost) 中的演练</span><span class="sxs-lookup"><span data-stu-id="5454b-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>  
 <span data-ttu-id="5454b-106">若要重用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]内的内容[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序，使用<xref:System.Windows.Interop.HwndHost>，这就是使看起来像 Hwnd 控件[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内容。</span><span class="sxs-lookup"><span data-stu-id="5454b-106">To reuse [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>  <span data-ttu-id="5454b-107">像<xref:System.Windows.Interop.HwndSource>，<xref:System.Windows.Interop.HwndHost>简单易用： 派生自<xref:System.Windows.Interop.HwndHost>并实现`BuildWindowCore`和`DestroyWindowCore`方法，然后实例化您<xref:System.Windows.Interop.HwndHost>派生的类并将其放入你[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序。</span><span class="sxs-lookup"><span data-stu-id="5454b-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
 <span data-ttu-id="5454b-108">如果你[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]逻辑已打包为一个控件，然后在`BuildWindowCore`实现是比调用更多`CreateWindow`。</span><span class="sxs-lookup"><span data-stu-id="5454b-108">If your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span>  <span data-ttu-id="5454b-109">例如，若要创建[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]LISTBOX 控件中的[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="5454b-109">For example, to create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX control in [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span></span>  
  
```  
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
    HWND handle = CreateWindowEx(0, L"LISTBOX",   
    L"this is a Win32 listbox",  
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY  
    | WS_VSCROLL | WS_BORDER,  
    0, 0, // x, y  
    30, 70, // height, width  
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd  
    0, // hmenu  
    0, // hinstance  
    0); // lparam  
  
    return HandleRef(this, IntPtr(handle));  
}  
  
virtual void DestroyWindowCore(HandleRef hwnd) override {  
    // HwndHost will dispose the hwnd for us  
}  
```  
  
 <span data-ttu-id="5454b-110">但是，假设[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]代码不是那么自包含？</span><span class="sxs-lookup"><span data-stu-id="5454b-110">But suppose the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code is not quite so self-contained?</span></span> <span data-ttu-id="5454b-111">如果这样，您可以创建[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]对话框框，并将其内容嵌入到更大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序。</span><span class="sxs-lookup"><span data-stu-id="5454b-111">If so, you can create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="5454b-112">此示例演示了这[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]和[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]，但还有可能以不同的语言或在命令行执行此操作。</span><span class="sxs-lookup"><span data-stu-id="5454b-112">The sample shows this in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], although it is also possible to do this in a different language or at the command line.</span></span>  
  
 <span data-ttu-id="5454b-113">开始编译为一个简单对话框[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)][!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]项目。</span><span class="sxs-lookup"><span data-stu-id="5454b-113">Start with a simple dialog, which is compiled into a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] project.</span></span>  
  
 <span data-ttu-id="5454b-114">接下来，将对话框中引入到较大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序：</span><span class="sxs-lookup"><span data-stu-id="5454b-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>  
  
-   <span data-ttu-id="5454b-115">编译[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]为托管 (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="5454b-115">Compile the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] as managed (`/clr`)</span></span>  
  
-   <span data-ttu-id="5454b-116">将转换为一个控件的对话框</span><span class="sxs-lookup"><span data-stu-id="5454b-116">Turn the dialog into a control</span></span>  
  
-   <span data-ttu-id="5454b-117">定义的派生的类<xref:System.Windows.Interop.HwndHost>与`BuildWindowCore`和`DestroyWindowCore`方法</span><span class="sxs-lookup"><span data-stu-id="5454b-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>  
  
-   <span data-ttu-id="5454b-118">重写`TranslateAccelerator`方法以处理对话框键</span><span class="sxs-lookup"><span data-stu-id="5454b-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>  
  
-   <span data-ttu-id="5454b-119">重写`TabInto`方法，以支持按 tab 键</span><span class="sxs-lookup"><span data-stu-id="5454b-119">Override `TabInto` method to support tabbing</span></span>  
  
-   <span data-ttu-id="5454b-120">重写`OnMnemonic`方法，以支持助记键</span><span class="sxs-lookup"><span data-stu-id="5454b-120">Override `OnMnemonic` method to support mnemonics</span></span>  
  
-   <span data-ttu-id="5454b-121">实例化<xref:System.Windows.Interop.HwndHost>子类并将其放在右侧[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]元素</span><span class="sxs-lookup"><span data-stu-id="5454b-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>  
  
### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="5454b-122">将变成一个控件的对话框</span><span class="sxs-lookup"><span data-stu-id="5454b-122">Turn the Dialog into a Control</span></span>  
 <span data-ttu-id="5454b-123">到子 HWND 使用 WS_CHILD 和 DS_CONTROL 样式可以打开一个对话框。</span><span class="sxs-lookup"><span data-stu-id="5454b-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span>  <span data-ttu-id="5454b-124">转到资源文件 (.rc)，其中定义对话框，并找到对话框中定义的开头：</span><span class="sxs-lookup"><span data-stu-id="5454b-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 <span data-ttu-id="5454b-125">更改第二个代码行：</span><span class="sxs-lookup"><span data-stu-id="5454b-125">Change the second line to:</span></span>  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 <span data-ttu-id="5454b-126">此操作不会不完全其打包到一个自包含的控件;您仍然需要调用`IsDialogMessage()`因此[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]可以处理特定消息，但控件更改提供了将放在另一个 HWND 内的这些控件的简单方法。</span><span class="sxs-lookup"><span data-stu-id="5454b-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>  
  
## <a name="subclass-hwndhost"></a><span data-ttu-id="5454b-127">子类 HwndHost</span><span class="sxs-lookup"><span data-stu-id="5454b-127">Subclass HwndHost</span></span>  
 <span data-ttu-id="5454b-128">导入下列命名空间：</span><span class="sxs-lookup"><span data-stu-id="5454b-128">Import the following namespaces:</span></span>  
  
```  
namespace ManagedCpp  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Input;  
    using namespace System::Windows::Media;  
    using namespace System::Runtime::InteropServices;  
```  
  
 <span data-ttu-id="5454b-129">然后创建一个派生的类<xref:System.Windows.Interop.HwndHost>并重写`BuildWindowCore`和`DestroyWindowCore`方法：</span><span class="sxs-lookup"><span data-stu-id="5454b-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>  
  
```  
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {  
    private:  
        HWND dialog;  
  
    protected:   
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
            InitializeGlobals();   
            dialog = CreateDialog(hInstance,   
                MAKEINTRESOURCE(IDD_DIALOG1),   
                (HWND) hwndParent.Handle.ToPointer(),  
                (DLGPROC) About);   
            return HandleRef(this, IntPtr(dialog));  
        }  
  
        virtual void DestroyWindowCore(HandleRef hwnd) override {  
            // hwnd will be disposed for us  
        }  
```  
  
 <span data-ttu-id="5454b-130">在本例中使用`CreateDialog`创建实际上是一个控件的对话框。</span><span class="sxs-lookup"><span data-stu-id="5454b-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span>  <span data-ttu-id="5454b-131">由于这是一个内部调用的第一个方法[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]，你还应执行一些标准[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]通过调用更高版本，您将定义的函数的初始化调用`InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="5454b-131">Since this is one of the first methods called inside the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], you should also do some standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>  
  
```  
bool initialized = false;  
    void InitializeGlobals() {  
        if (initialized) return;  
        initialized = true;  
  
        // TODO: Place code here.  
        MSG msg;  
        HACCEL hAccelTable;  
  
        // Initialize global strings  
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);  
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);  
        MyRegisterClass(hInstance);  
```  
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="5454b-132">重写 TranslateAccelerator 方法以处理对话框键</span><span class="sxs-lookup"><span data-stu-id="5454b-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>  
 <span data-ttu-id="5454b-133">如果运行此示例现在，你会收到一个对话框控件的显示，但它会忽略所有键盘处理，这样可以对话框功能的对话框。</span><span class="sxs-lookup"><span data-stu-id="5454b-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span>  <span data-ttu-id="5454b-134">现在应重写`TranslateAccelerator`实现 (这来自`IKeyboardInputSink`，一个接口，<xref:System.Windows.Interop.HwndHost>实现)。</span><span class="sxs-lookup"><span data-stu-id="5454b-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span>  <span data-ttu-id="5454b-135">当应用程序收到 WM_KEYDOWN 和 WM_SYSKEYDOWN 时调用此方法。</span><span class="sxs-lookup"><span data-stu-id="5454b-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>  
  
```  
#undef TranslateAccelerator  
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
            ModifierKeys modifiers) override   
        {  
            ::MSG m = ConvertMessage(msg);  
  
            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know   
            // what to do when it reaches the last tab stop  
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
                TraversalRequest^ request = nullptr;  
  
                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
                    // this code should work, but there’s a bug with interop shift-tab in current builds                      
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
                }  
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {  
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
                }  
  
                if (request != nullptr)  
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
  
            }  
  
            // Only call IsDialogMessage for keys it will do something with.  
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
                switch (m.wParam) {  
                    case VK_TAB:  
                    case VK_LEFT:  
                    case VK_UP:  
                    case VK_RIGHT:  
                    case VK_DOWN:  
                    case VK_EXECUTE:  
                    case VK_RETURN:  
                    case VK_ESCAPE:  
                    case VK_CANCEL:  
                        IsDialogMessage(dialog, &m);  
                        // IsDialogMessage should be called ProcessDialogMessage --  
                        // it processes messages without ever really telling you  
                        // if it handled a specific message or not  
                        return true;  
                }  
            }  
  
            return false; // not a key we handled  
        }  
```  
  
 <span data-ttu-id="5454b-136">这是代码的很多以单个片段，因此它可以使用一些更详细的解释。</span><span class="sxs-lookup"><span data-stu-id="5454b-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span>  <span data-ttu-id="5454b-137">首先，代码使用[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]并[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]宏; 您需要了解已存在一个名为宏`TranslateAccelerator`，定义在 winuser.h 中：</span><span class="sxs-lookup"><span data-stu-id="5454b-137">First, the code using [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 <span data-ttu-id="5454b-138">因此请务必定义`TranslateAccelerator`方法，而不`TranslateAcceleratorW`方法。</span><span class="sxs-lookup"><span data-stu-id="5454b-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>  
  
 <span data-ttu-id="5454b-139">同样，还有非托管的 winuser.h MSG 和托管`Microsoft::Win32::MSG`结构。</span><span class="sxs-lookup"><span data-stu-id="5454b-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span>  <span data-ttu-id="5454b-140">你可以使用这两者之间区分[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]`::`运算符。</span><span class="sxs-lookup"><span data-stu-id="5454b-140">You can disambiguate between the two using the [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operator.</span></span>  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 <span data-ttu-id="5454b-141">两个消息具有相同的数据，但是有时更轻松地使用非托管的定义，因此在此示例中，您可以定义明显转换例程：</span><span class="sxs-lookup"><span data-stu-id="5454b-141">Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:</span></span>  
  
```  
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {  
    ::MSG m;  
    m.hwnd = (HWND) msg.hwnd.ToPointer();  
    m.lParam = (LPARAM) msg.lParam.ToPointer();  
    m.message = msg.message;  
    m.wParam = (WPARAM) msg.wParam.ToPointer();  
  
    m.time = msg.time;  
  
    POINT pt;  
    pt.x = msg.pt_x;  
    pt.y = msg.pt_y;  
    m.pt = pt;  
  
    return m;  
}  
```  
  
 <span data-ttu-id="5454b-142">返回到`TranslateAccelerator`。</span><span class="sxs-lookup"><span data-stu-id="5454b-142">Back to `TranslateAccelerator`.</span></span>  <span data-ttu-id="5454b-143">基本原则是调用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函数`IsDialogMessage`执行尽可能多工作，但`IsDialogMessage`不能访问该对话框之外的任何内容。</span><span class="sxs-lookup"><span data-stu-id="5454b-143">The basic principle is to call the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="5454b-144">在对话框中，按 tab 键周围的用户选项卡运行过去的对话框中的最后一个控件时，需要将焦点设置到[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]通过调用部分`IKeyboardInputSite::OnNoMoreStops`。</span><span class="sxs-lookup"><span data-stu-id="5454b-144">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>  
  
```  
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know   
// what to do when it reaches the last tab stop  
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
    TraversalRequest^ request = nullptr;  
  
    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
    }  
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
    }  
  
    if (request != nullptr)  
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
}  
```  
  
 <span data-ttu-id="5454b-145">最后，调用 `IsDialogMessage`。</span><span class="sxs-lookup"><span data-stu-id="5454b-145">Finally, call `IsDialogMessage`.</span></span>  <span data-ttu-id="5454b-146">但的职责之一`TranslateAccelerator`方法的告诉[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是否处理击键。</span><span class="sxs-lookup"><span data-stu-id="5454b-146">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="5454b-147">如果未处理，输入的事件可以向下和向上遍历应用程序的其余部分。</span><span class="sxs-lookup"><span data-stu-id="5454b-147">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="5454b-148">在这里，您将公开的键盘消息处理是意料之中的事和中的输入体系结构的性质[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5454b-148">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span></span> <span data-ttu-id="5454b-149">遗憾的是，`IsDialogMessage`不返回任何方式是否它处理特定击键。</span><span class="sxs-lookup"><span data-stu-id="5454b-149">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span>  <span data-ttu-id="5454b-150">更糟糕的是，它将调用`DispatchMessage()`上不应处理的键击 ！</span><span class="sxs-lookup"><span data-stu-id="5454b-150">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="5454b-151">因此你必须进行反向工程到`IsDialogMessage`，并仅为您知道的密钥将处理调用它：</span><span class="sxs-lookup"><span data-stu-id="5454b-151">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>  
  
```  
// Only call IsDialogMessage for keys it will do something with.  
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
    switch (m.wParam) {  
        case VK_TAB:  
        case VK_LEFT:  
        case VK_UP:  
        case VK_RIGHT:  
        case VK_DOWN:  
        case VK_EXECUTE:  
        case VK_RETURN:  
        case VK_ESCAPE:  
        case VK_CANCEL:  
            IsDialogMessage(dialog, &m);  
            // IsDialogMessage should be called ProcessDialogMessage --  
            // it processes messages without ever really telling you  
            // if it handled a specific message or not  
            return true;  
    }  
```  
  
### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="5454b-152">重写到支持按 tab 键的 TabInto 方法</span><span class="sxs-lookup"><span data-stu-id="5454b-152">Override TabInto Method to Support Tabbing</span></span>  
 <span data-ttu-id="5454b-153">现在，已实现`TranslateAccelerator`，围绕选项卡的用户可以在对话框内框和 tab 键跳出这个到更大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序。</span><span class="sxs-lookup"><span data-stu-id="5454b-153">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="5454b-154">但用户不能返回到对话框的选项卡上。</span><span class="sxs-lookup"><span data-stu-id="5454b-154">But a user cannot tab back into the dialog box.</span></span>  <span data-ttu-id="5454b-155">若要解决此问题，重写`TabInto`:</span><span class="sxs-lookup"><span data-stu-id="5454b-155">To solve that, you override `TabInto`:</span></span>  
  
```  
public:   
    virtual bool TabInto(TraversalRequest^ request) override {  
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {  
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
            SetFocus(lastTabStop);  
        }  
        else {  
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
            SetFocus(firstTabStop);  
        }  
        return true;  
    }  
```  
  
 <span data-ttu-id="5454b-156">`TraversalRequest`参数指示选项卡操作是一个选项卡或 shift 选项卡。</span><span class="sxs-lookup"><span data-stu-id="5454b-156">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="5454b-157">重写 OnMnemonic 方法以支持助记键</span><span class="sxs-lookup"><span data-stu-id="5454b-157">Override OnMnemonic Method to Support Mnemonics</span></span>  
 <span data-ttu-id="5454b-158">键盘处理的方法是几乎已完成，但还有一个缺 – 助记键不起作用。</span><span class="sxs-lookup"><span data-stu-id="5454b-158">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span>  <span data-ttu-id="5454b-159">如果用户按下 alt-F，焦点 doe 不跳转到"第一个名称:"编辑框。</span><span class="sxs-lookup"><span data-stu-id="5454b-159">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="5454b-160">因此，重写`OnMnemonic`方法：</span><span class="sxs-lookup"><span data-stu-id="5454b-160">So, you override the `OnMnemonic` method:</span></span>  
  
```  
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {  
    ::MSG m = ConvertMessage(msg);  
  
    // If it's one of our mnemonics, set focus to the appropriate hwnd  
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {  
        int dialogitem = 9999;  
        switch (m.wParam) {  
            case 's': dialogitem = IDOK; break;  
            case 'c': dialogitem = IDCANCEL; break;  
            case 'f': dialogitem = IDC_EDIT1; break;  
            case 'l': dialogitem = IDC_EDIT2; break;  
            case 'p': dialogitem = IDC_EDIT3; break;  
            case 'a': dialogitem = IDC_EDIT4; break;  
            case 'i': dialogitem = IDC_EDIT5; break;  
            case 't': dialogitem = IDC_EDIT6; break;  
            case 'z': dialogitem = IDC_EDIT7; break;  
        }  
        if (dialogitem != 9999) {  
            HWND hwnd = GetDlgItem(dialog, dialogitem);  
            SetFocus(hwnd);  
            return true;  
        }  
    }  
    return false; // key unhandled  
};  
```  
  
 <span data-ttu-id="5454b-161">为什么不调用`IsDialogMessage`此处？</span><span class="sxs-lookup"><span data-stu-id="5454b-161">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="5454b-162">根据需要之前-若要能够通知具有同样的问题[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]代码是否在代码或不是，处理击键和`IsDialogMessage`无法做到这一点。</span><span class="sxs-lookup"><span data-stu-id="5454b-162">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span>  <span data-ttu-id="5454b-163">还有第二个问题，因为`IsDialogMessage`拒绝处理助记键，如果已设定焦点的 HWND 内对话框的不是。</span><span class="sxs-lookup"><span data-stu-id="5454b-163">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>  
  
### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="5454b-164">实例化 HwndHost 派生类</span><span class="sxs-lookup"><span data-stu-id="5454b-164">Instantiate the HwndHost Derived Class</span></span>  
 <span data-ttu-id="5454b-165">最后，现在，所有键和选项卡支持都后，您可以将你<xref:System.Windows.Interop.HwndHost>组成较大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序。</span><span class="sxs-lookup"><span data-stu-id="5454b-165">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="5454b-166">如果主应用程序以[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，将其放在正确的位置的最简单方法是将一个空<xref:System.Windows.Controls.Border>想要放置的元素<xref:System.Windows.Interop.HwndHost>。</span><span class="sxs-lookup"><span data-stu-id="5454b-166">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span>  <span data-ttu-id="5454b-167">此处创建<xref:System.Windows.Controls.Border>名为`insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="5454b-167">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>  
  
```  
<Window x:Class="WPFApplication1.Window1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    Title="Windows Presentation Framework Application"  
    Loaded="Window1_Loaded"  
    >  
    <StackPanel>  
        <Button Content="WPF button"/>  
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>  
        <Button Content="WPF button"/>  
    </StackPanel>  
</Window>  
```  
  
 <span data-ttu-id="5454b-168">然后剩下的就是在实例化的代码序列中查找，一个好<xref:System.Windows.Interop.HwndHost>并将其连接到<xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="5454b-168">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span>  <span data-ttu-id="5454b-169">在此示例中，你会将它放在构造函数内<xref:System.Windows.Window>派生的类：</span><span class="sxs-lookup"><span data-stu-id="5454b-169">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>  
  
```  
public partial class Window1 : Window {  
    public Window1() {  
    }  
  
    void Window1_Loaded(object sender, RoutedEventArgs e) {  
        HwndHost host = new ManagedCpp.MyHwndHost();  
        insertHwndHostHere.Child = host;  
    }  
}  
```  
  
 <span data-ttu-id="5454b-170">后者可提供：</span><span class="sxs-lookup"><span data-stu-id="5454b-170">Which gives you:</span></span>  
  
 <span data-ttu-id="5454b-171">![WPF 应用程序屏幕截图](./media/interoparch09.PNG "InteropArch09")</span><span class="sxs-lookup"><span data-stu-id="5454b-171">![WPF application screen shot](./media/interoparch09.PNG "InteropArch09")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5454b-172">请参阅</span><span class="sxs-lookup"><span data-stu-id="5454b-172">See also</span></span>
- [<span data-ttu-id="5454b-173">WPF 和 Win32 互操作</span><span class="sxs-lookup"><span data-stu-id="5454b-173">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
