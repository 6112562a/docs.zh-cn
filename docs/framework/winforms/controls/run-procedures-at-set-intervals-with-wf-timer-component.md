---
title: 用计时器组件按设置的时间间隔运行过程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], timers
- timers [Windows Forms], event intervals
- initialization [Windows Forms], Timer components
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], initializing
- procedures [Windows Forms], specific time intervals
ms.assetid: 8025247a-2de4-4d86-b8ab-a8cb8aeab2ea
ms.openlocfilehash: dcc88beee947e2a83b426dcd2f3fd9d70c20fb67
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743109"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>방법: Windows Forms Timer 구성 요소를 사용하여 설정된 간격마다 프로시저 실행
루프가 완료될 때까지 특정 시간 간격으로 실행되거나 설정된 시간 간격이 경과할 때 실행되는 프로시저를 만들려는 경우도 있습니다. <xref:System.Windows.Forms.Timer> 구성 요소는 이러한 프로시저를 가능하게 합니다.  
  
 이 구성 요소는 Windows Forms 환경에 맞게 설계되었습니다. 서버 환경에 적합한 타이머가 필요한 경우 [서버 기반 타이머 소개](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))를 참조하세요.  
  
> [!NOTE]
> <xref:System.Windows.Forms.Timer> 구성 요소를 사용하는 경우 몇 가지 제한 사항이 있습니다. 有关详细信息，请参阅[Windows 窗体 Timer 组件的 Interval 属性的限制](limitations-of-the-timer-component-interval-property.md)。  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Timer 구성 요소를 사용하여 설정된 간격마다 프로시저를 실행하려면  
  
1. 폼에 <xref:System.Windows.Forms.Timer>를 추가합니다. 이 작업을 프로그래밍 방식으로 수행하는 방법은 다음 예제 섹션을 참조하세요. Visual Studio 还支持将组件添加到窗体。 另请参阅[如何：将没有用户界面的控件添加到 Windows 窗体](how-to-add-controls-without-a-user-interface-to-windows-forms.md)。  
  
2. 타이머에 대한 <xref:System.Windows.Forms.Timer.Interval%2A> 속성(밀리초)을 설정합니다. 이 속성은 프로시저가 다시 실행되기까지 남은 시간을 결정합니다.  
  
    > [!NOTE]
    > 타이머 이벤트가 자주 발생할수록 이벤트에 응답하는 데 더 많은 프로세서 시간이 사용됩니다. 이 경우 전반적인 성능이 느려질 수 있습니다. 필요 이상으로 작은 간격을 설정하지 마세요.  
  
3. <xref:System.Windows.Forms.Timer.Tick> 이벤트 처리기에서 적절한 코드를 작성합니다. 이 이벤트에서 작성하는 코드는 <xref:System.Windows.Forms.Timer.Interval%2A> 속성에 지정된 간격마다 실행됩니다.  
  
4. <xref:System.Windows.Forms.Timer.Enabled%2A> 속성을 `true`로 설정하여 타이머를 시작합니다. <xref:System.Windows.Forms.Timer.Tick> 이벤트 발생이 시작되고 설정된 간격마다 프로시저를 실행합니다.  
  
5. 적절한 시간에 <xref:System.Windows.Forms.Timer.Enabled%2A> 속성을 `false`로 설정하여 프로시저가 다시 실행되지 않도록 중지합니다. 将间隔设置为 `0` 不会导致计时器停止。  
  
## <a name="example"></a>示例  
 이 첫 번째 코드 예제에서는 1초 증분으로 시간을 추적합니다. 폼의 <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label> 및 <xref:System.Windows.Forms.Timer> 구성 요소를 사용합니다. <xref:System.Windows.Forms.Timer.Interval%2A> 속성은 1000(1초와 같음)으로 설정됩니다. <xref:System.Windows.Forms.Timer.Tick> 이벤트에서 레이블의 캡션은 현재 시간으로 설정됩니다. 단추를 클릭하면 <xref:System.Windows.Forms.Timer.Enabled%2A> 속성이 `false`로 설정되어 타이머가 레이블 캡션 업데이트를 중지합니다. 下面的代码示例要求你有一个窗体，其中包含名为 `Button1`的 <xref:System.Windows.Forms.Button> 控件、一个名为 `Timer1`的 <xref:System.Windows.Forms.Timer> 控件以及一个名为 <xref:System.Windows.Forms.Label> 的 `Label1`控件。  
  
```vb  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   ' Set to 1 second.  
   Timer1.Interval = 1000  
   ' Enable timer.  
   Timer1.Enabled = True  
   Button1.Text = "Enabled"  
End Sub  
x  
Private Sub Timer1_Tick(ByVal Sender As Object, ByVal e As EventArgs) Handles Timer1.Tick  
' Set the caption to the current time.  
   Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
      If Button1.Text = "Stop" Then  
         Button1.Text = "Start"  
         Timer1.Enabled = False  
      Else  
         Button1.Text = "Stop"  
         Timer1.Enabled = True  
      End If  
End Sub  
```  
  
```csharp  
private void InitializeTimer()  
{  
    // Call this procedure when the application starts.  
    // Set to 1 second.  
    Timer1.Interval = 1000;  
    Timer1.Tick += new EventHandler(Timer1_Tick);  
  
    // Enable timer.  
    Timer1.Enabled = true;  
  
    Button1.Text = "Stop";  
    Button1.Click += new EventHandler(Button1_Click);  
}  
  
private void Timer1_Tick(object Sender, EventArgs e)     
{  
   // Set the caption to the current time.  
   Label1.Text = DateTime.Now.ToString();  
}  
  
private void Button1_Click(object sender, EventArgs e)  
{  
  if ( Button1.Text == "Stop" )  
  {  
    Button1.Text = "Start";  
    Timer1.Enabled = false;  
  }  
  else  
  {  
    Button1.Text = "Stop";  
    Timer1.Enabled = true;  
  }  
}  
```  
  
```cpp  
private:  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      // Set to 1 second.  
      timer1->Interval = 1000;  
      // Enable timer.  
      timer1->Enabled = true;  
      this->timer1->Tick += gcnew System::EventHandler(this,    
                               &Form1::timer1_Tick);  
  
      button1->Text = S"Stop";  
      this->button1->Click += gcnew System::EventHandler(this,   
                               &Form1::button1_Click);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      // Set the caption to the current time.  
      label1->Text = DateTime::Now.ToString();  
   }  
  
   void button1_Click(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if ( button1->Text == "Stop" )  
      {  
         button1->Text = "Start";  
         timer1->Enabled = false;  
      }  
      else  
      {  
         button1->Text = "Stop";  
         timer1->Enabled = true;  
      }  
   }  
```  
  
## <a name="example"></a>示例  
 이 두 번째 코드 예제는 루프가 완료될 때까지 600밀리초마다 프로시저를 실행합니다. 下面的代码示例要求你有一个窗体，其中包含名为 `Button1`的 <xref:System.Windows.Forms.Button> 控件、一个名为 `Timer1`的 <xref:System.Windows.Forms.Timer> 控件以及一个名为 <xref:System.Windows.Forms.Label> 的 `Label1`控件。  
  
```vb  
' This variable will be the loop counter.  
Private counter As Integer  
  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   counter = 0  
   Timer1.Interval = 600  
   Timer1.Enabled = True  
End Sub  
  
Private Sub Timer1_Tick(ByVal sender As Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
   If counter => 10 Then  
      ' Exit loop code.  
      Timer1.Enabled = False  
      counter = 0  
   Else  
      ' Run your procedure here.  
      ' Increment counter.  
      counter = counter + 1  
      Label1.Text = "Procedures Run: " & counter.ToString  
   End If  
End Sub  
```  
  
```csharp  
// This variable will be the loop counter.  
private int counter;  
  
private void InitializeTimer()  
{  
   // Run this procedure in an appropriate event.  
   counter = 0;  
   timer1.Interval = 600;  
   timer1.Enabled = true;  
   // Hook up timer's tick event handler.  
   this.timer1.Tick += new System.EventHandler(this.timer1_Tick);  
}  
  
private void timer1_Tick(object sender, System.EventArgs e)     
{  
   if (counter >= 10)   
   {  
      // Exit loop code.  
      timer1.Enabled = false;  
      counter = 0;  
   }  
   else  
   {  
      // Run your procedure here.  
      // Increment counter.  
      counter = counter + 1;  
      label1.Text = "Procedures Run: " + counter.ToString();  
      }  
}  
```  
  
```cpp  
private:  
   int counter;  
  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      counter = 0;  
      timer1->Interval = 600;  
      timer1->Enabled = true;  
      // Hook up timer's tick event handler.  
      this->timer1->Tick += gcnew System::EventHandler(this, &Form1::timer1_Tick);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if (counter >= 10)   
      {  
         // Exit loop code.  
         timer1->Enabled = false;  
         counter = 0;  
      }  
      else  
      {  
         // Run your procedure here.  
         // Increment counter.  
         counter = counter + 1;  
         label1->Text = String::Concat("Procedures Run: ",  
            counter.ToString());  
      }  
   }  
```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.Timer>
- [Timer 구성 요소](timer-component-windows-forms.md)
- [Timer 구성 요소 개요](timer-component-overview-windows-forms.md)
