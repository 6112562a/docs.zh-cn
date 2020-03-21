---
title: 演练：使用 Visual C# 创作复合控件
ms.date: 03/30/2017
dev_langs:
- CSharp
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ad9aad026a1a6a1266845736d7651db77fd5d5c
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546719"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a>演练：使用 C 编写复合控件\#

复合控件提供了一种创建和重用自定义图形界面的方法。 复合控件本质上是具有可视化表示形式的组件。 因此，它可能包含一个或多个 Windows 窗体控件、组件或代码块，它们能够通过验证用户输入、修改显示属性或执行作者所需的其他任务来扩展功能。 可以按照与其他控件相同的方式将复合控件置于 Windows 窗体中。 在本演练的第一部分，将创建一个名为 `ctlClock` 的简单复合控件。 在本演练的第二部分，将通过继承扩展 `ctlClock` 的功能。

## <a name="create-the-project"></a>创建项目

创建新的项目时应指定其名称，以设置根命名空间、程序集名称和项目名称，并确保默认组件将位于正确的命名空间中。

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>创建 ctlClockLib 控件库和 ctlClock 控件

1. 在可视化工作室中，创建新的**Windows 窗体控件库**项目，并将其命名为**ctlClockLib**。

     默认情况下，项目名称 `ctlClockLib` 也会分配到根命名空间中。 根命名空间用于限定程序集中的组件名。 例如，如果两个程序集都提供名为 `ctlClock` 的组件，则可以使用 `ctlClockLib.ctlClock.` 指定 `ctlClock` 组件

2. 在**解决方案资源管理器**中，右键单击**UserControl1.cs，** 然后单击 **"重命名**"。 将文件名更改为 `ctlClock.cs`。 当系统询问是否重命名对代码元素“UserControl1”的所有引用时，单击“是”**** 按钮。

    > [!NOTE]
    > 默认情况下，复合控件从系统提供的<xref:System.Windows.Forms.UserControl>类继承。 该<xref:System.Windows.Forms.UserControl>类提供所有复合控件所需的功能，并实现标准方法和属性。

3. 在“文件”**** 菜单上，单击“全部保存”**** 保存项目。

## <a name="add-windows-controls-and-components-to-the-composite-control"></a>将 Windows 控件和组件添加到复合控件

可视化界面是复合控件的基本部分。 这种可视化界面通过向设计器图面添加一个或多个 Windows 控件实现。 在下面的演示中，将向复合控件中加入 Windows 控件并编写代码实现功能。

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>将标签和计时器添加到复合控件

1. 在 **"解决方案资源管理器"** 中，右键单击**ctlClock.cs，** 然后单击"**查看设计器**"。

2. 在**工具箱**中，展开 **"常见控件"** 节点，然后双击 **"标签**"。

     名为<xref:System.Windows.Forms.Label>的`label1`控件将添加到设计器表面上的控件中。

3. 在设计器中，单击**标签 1**。 在“属性”窗口中，设置下列属性。

    |properties|更改为|
    |--------------|---------------|
    |**名称**|`lblDisplay`|
    |**文本**|`(blank space)`|
    |**TextAlign**|`MiddleCenter`|
    |**字体.大小**|`14`|

4. 在“工具箱****”中，展开“组件”**** 节点，然后双击“计时器”****。

     由于<xref:System.Windows.Forms.Timer>是组件，因此它在运行时没有可视表示形式。 因此，它不与设计器表面上的控件一起显示，而是出现在**组件设计器**（设计器表面底部的托盘）中。

5. 在**组件设计器**中，**单击计时器1，** 然后将<xref:System.Windows.Forms.Timer.Interval%2A>属性`1000`设置为 和<xref:System.Windows.Forms.Timer.Enabled%2A>属性。 `true`

     属性<xref:System.Windows.Forms.Timer.Interval%2A>控制<xref:System.Windows.Forms.Timer>组件滴答的频率。 `timer1` 每走过一个刻度，它都会运行一次 `timer1_Tick` 事件中的代码。 间隔表示计时之间的毫秒数。

6. 在**组件设计器**中，双击**计时器1**转到 的事件`timer1_Tick``ctlClock`。

7. 将代码修改为类似如下所示的代码示例。 确保将访问修饰符从 `private` 更改为 `protected`。

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     此代码将使得当前时间显示在 `lblDisplay` 中。 因为 `timer1` 的间隔设置为 `1000`，所以该事件每 1000 毫秒发生一次，从而每一秒更新一次当前时间。

8. 修改该方法使其可通过 `virtual` 关键字重写。 有关详细信息，请参阅下面的“从用户控件继承”一节。

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. 在“文件”**** 菜单上，单击“全部保存”**** 保存项目。

## <a name="add-properties-to-the-composite-control"></a>将属性添加到复合控件

时钟控件现在封装了控件<xref:System.Windows.Forms.Label>和<xref:System.Windows.Forms.Timer>组件，每个控件和组件都有自己的固有属性集。 尽管控件的后续用户无法访问这些控件的单个属性，但可以通过编写适当的代码块来创建和公开自定义属性。 在下面的过程中，将向控件添加属性，这些属性可使用户能够更改背景和文本的颜色。

### <a name="to-add-a-property-to-your-composite-control"></a>将属性添加到复合控件

1. 在**解决方案资源管理器**中，右键单击**ctlClock.cs，** 然后单击"**查看代码**"。

     将打开控件**的代码编辑器**。

2. 找到 `public partial class ctlClock` 语句。 在左大括号 (`{)` 下键入下以下代码。

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     这些语句会创建私有变量，用来存储要创建的属性的值。

3. 输入或粘贴步骤 2 中的变量声明下方的以下代码。

    ```csharp
    // Declares the name and type of the property.
    public Color ClockBackColor
    {
        // Retrieves the value of the private variable colBColor.
        get
        {
            return colBColor;
        }
        // Stores the selected value in the private variable colBColor, and
        // updates the background color of the label control lblDisplay.
        set
        {
            colBColor = value;
            lblDisplay.BackColor = colBColor;
        }
    }
    // Provides a similar set of instructions for the foreground color.
    public Color ClockForeColor
    {
        get
        {
            return colFColor;
        }
        set
        {
            colFColor = value;
            lblDisplay.ForeColor = colFColor;
        }
    }
    ```

     上述代码使得后续用户能够使用 `ClockForeColor` 和 `ClockBackColor` 这两个自定义属性。 `get` 和 `set` 语句提供了该属性值的存储和检索，还提供了实现适合于该属性的功能的代码。

4. 在“文件”**** 菜单上，单击“全部保存”**** 保存项目。

## <a name="test-the-control"></a>测试控件

控件不是独立应用程序，它们必须托管在容器中。 测试控件的运行时行为，并使用“UserControl 测试容器”**** 运用其属性。 有关详细信息，请参阅[如何：测试 UserControl 的运行时行为](how-to-test-the-run-time-behavior-of-a-usercontrol.md)。

### <a name="to-test-your-control"></a>测试控件

1. 按**F5**生成项目并在**UserControl 测试容器**中运行控件。

2. 在测试容器的属性网格中，找到 `ClockBackColor` 属性，然后选择该属性以显示调色板。

3. 通过单击选择颜色。

   控件的背景颜色更改为你选择的颜色。

4. 使用类似的事件序列来验证 `ClockForeColor` 属性的功能是否与预期的相符。

   本节和前面的几节演示了如何将组件和 Windows 控件与代码和打包相结合，以复合控件的形式提供自定义功能。 你现已了解如何在复合控件中公开属性，以及如何在完成后对控件进行测试。 下一节将介绍如何以 `ctlClock` 为基础构造继承的复合控件。

## <a name="inherit-from-a-composite-control"></a>从复合控件继承

前面的章节中介绍了如何将 Windows 控件、组件和代码组合成可重用的复合控件。 现在即可将复合控件用作生成其他控件的基础。 从基类派生类的过程称为继承**。 在本节中，将创建一个称为 `ctlAlarmClock` 的复合控件。 此控件将从其父控件 `ctlClock` 派生。 将介绍如何通过重写父级方法并添加新的方法和属性来扩展 `ctlClock` 的功能。

创建继承控件的第一步是从它的父控件派生。 该操作创建一个新控件，它具有父控件的所有属性、方法和图形特征，但也可以用作添加新功能或修改过的功能的基础。

### <a name="to-create-the-inherited-control"></a>创建继承的控件

1. 在**解决方案资源管理器**中，右键单击**ctlClockLib，** 指向**添加**，然后单击 **"用户控制**"。

     **“添加新项”** 对话框将会打开。

2. 选择“继承的用户控件”**** 模板。

3. 在“名称”**** 框中，键入 `ctlAlarmClock.cs`，然后单击“添加”****。

     “继承选择器”**** 对话框将出现。

4. 在“组件名称”**** 下，双击“ctlClock”****。

5. 在**解决方案资源管理器中**，浏览当前项目。

    > [!NOTE]
    > 当前项目中添加了一个名为“ctlAlarmClock.cs”**** 的文件。

### <a name="add-the-alarm-properties"></a>添加报警属性

将属性添加到继承的控件的方法与将其添加到复合控件的方法相同。 现在将使用属性声明语法向控件中添加两个属性：`AlarmTime` 和 `AlarmSet`，前者将存储发出警报的日期和时间值，后者指示是否设置了警报。

#### <a name="to-add-properties-to-your-composite-control"></a>将属性添加到复合控件

1. 在**解决方案资源管理器**中，右键单击**ctlAlarmClock，** 然后单击"**查看代码**"。

2. 找到 `public class` 语句。 请注意，控件继承自 `ctlClockLib.ctlClock`。 在左大括号 (`{)` 语句下键入下以下代码。

    ```csharp
    private DateTime dteAlarmTime;
    private bool blnAlarmSet;
    // These properties will be declared as public to allow future
    // developers to access them.
    public DateTime AlarmTime
    {
        get
        {
            return dteAlarmTime;
        }
        set
        {
            dteAlarmTime = value;
        }
    }
    public bool AlarmSet
    {
        get
        {
            return blnAlarmSet;
        }
        set
        {
            blnAlarmSet = value;
        }
    }
    ```

### <a name="add-to-the-graphical-interface-of-the-control"></a>添加到控件的图形界面

继承的控件具有可视化界面，该界面与它从中继承的控件的界面完全相同。 它与其父控件拥有相同的构成控件，但除非将构成控件的属性特别公开，否则它们将不可用。 可以向继承的复合控件的图形界面进行添加，方法与向任意复合控件进行添加相同。 若要继续向警报时钟的可视化界面进行添加，请添加一个标签控件，它将在警报响起时闪烁。

#### <a name="to-add-the-label-control"></a>添加标签控件

1. 在**解决方案资源管理器**中，右键单击**ctlAlarmClock，** 然后单击 **"查看设计器**"。

     `ctlAlarmClock` 的设计器将在主窗口中打开。

2. 单击该控件的显示部分，然后查看“属性”窗口。

    > [!NOTE]
    > 当显示所有属性时，属性是浅灰色的。 这表示这些属性是 `lblDisplay` 所固有的，不能在“属性”窗口中修改或访问。 默认情况下，复合控件中所包含的控件为 `private`，通过任何途径都无法访问其属性。

    > [!NOTE]
    > 如果希望复合控件的后续用户可以访问其内部控件，则可将其声明为 `public` 或 `protected`。 如此即可使用适当的代码设置和修改复合控件内所包含控件的属性。

3. 向<xref:System.Windows.Forms.Label>复合控件添加控件。

4. 使用鼠标，立即在<xref:System.Windows.Forms.Label>显示框下方拖动控件。 在“属性”窗口中，设置下列属性。

    |properties|设置|
    |--------------|-------------|
    |**名称**|`lblAlarm`|
    |**文本**|**报警！**|
    |**TextAlign**|`MiddleCenter`|
    |**可见**|`false`|

### <a name="add-the-alarm-functionality"></a>添加报警功能

在前面的章节中，已经添加了一些属性和一个控件，它们将启用复合控件中的警报功能。 在本过程中，将添加代码以比较当前时间和警报时间，如果两者相同，则警报闪烁。 通过重写 `ctlClock` 的 `timer1_Tick` 方法并向其中添加其他代码，可扩展 `ctlAlarmClock` 的功能，同时会保留 `ctlClock` 的所有固有功能。

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>重写 ctlClock 的 timer1_Tick 方法

1. 在“代码编辑器”**** 中，找到 `private bool blnAlarmSet;` 语句。 在其紧下方添加下列语句。

    ```csharp
    private bool blnColorTicker;
    ```

2. 在“代码编辑器”**** 中，在类的结尾找到右大括号 (`})`。 在大括号的前面添加以下代码。

    ```csharp
    protected override void timer1_Tick(object sender, System.EventArgs e)
    {
        // Calls the Timer1_Tick method of ctlClock.
        base.timer1_Tick(sender, e);
        // Checks to see if the alarm is set.
        if (AlarmSet == false)
            return;
        else
            // If the date, hour, and minute of the alarm time are the same as
            // the current time, flash an alarm.
        {
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)
            {
                // Sets lblAlarmVisible to true, and changes the background color based on
                // the value of blnColorTicker. The background color of the label
                // will flash once per tick of the clock.
                lblAlarm.Visible = true;
                if (blnColorTicker == false)
                {
                    lblAlarm.BackColor = Color.Red;
                    blnColorTicker = true;
                }
                else
                {
                    lblAlarm.BackColor = Color.Blue;
                    blnColorTicker = false;
                }
            }
            else
            {
                // Once the alarm has sounded for a minute, the label is made
                // invisible again.
                lblAlarm.Visible = false;
            }
        }
    }
    ```

     添加此代码将完成多项任务。 `override` 语句指示控件使用此方法替换从基控件继承的方法。 调用此方法时，它通过调用 `base.timer1_Tick` 语句来调用它重写的方法，从而确保在该控件中重现原始控件包含的所有功能。 然后，运行附加代码以合并警报功能。 警报触发时，将会出现闪烁的标签控件。

     警报时钟控件已基本完成。 剩下的唯一事情是实现关闭它的方法。 为此，将向 `lblAlarm_Click` 方法添加代码。

#### <a name="to-implement-the-shutoff-method"></a>实现关闭方法

1. 在 **"解决方案资源管理器"** 中，右键单击**ctlAlarmClock.cs，** 然后单击"**查看设计器**"。

     设计器随即打开。

2. 将按钮添加到控件。 按如下方式设置该按钮的属性。

    |properties|值|
    |--------------|-----------|
    |**名称**|`btnAlarmOff`|
    |**文本**|**禁用警报**|

3. 在设计器中，双击“btnAlarmOff”**** 控件。

     “代码编辑器”**** 随即打开并显示 `private void btnAlarmOff_Click` 行。

4. 将此方法修改为类似如下所示的代码。

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. 在“文件”**** 菜单上，单击“全部保存”**** 保存项目。

### <a name="use-the-inherited-control-on-a-form"></a>在窗体上使用继承控件

您可以测试继承的控件与测试基类控件的方式相同：`ctlClock`按**F5**生成项目并在**UserControl 测试容器**中运行控件。 有关详细信息，请参阅[如何：测试 UserControl 的运行时行为](how-to-test-the-run-time-behavior-of-a-usercontrol.md)。

若要使用控件，还需要将其放入窗体中。 与标准复合控件一样，继承的复合控件不能独立存在，而必须承载在窗体或其他容器中。 由于 `ctlAlarmClock` 的功能更加深入，因此需要附加代码以对其进行测试。 在本过程中，将编写一个简单的程序来测试 `ctlAlarmClock` 的功能。 将编写代码来设置和显示 `ctlAlarmClock` 的 `AlarmTime` 属性，并测试其固有功能。

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>生成测试窗体并将控件添加到该窗体

1. 在**解决方案资源管理器**中，右键单击**ctlClockLib，** 然后单击 **"生成**"。

2. 向解决方案添加新**的 Windows 窗体应用程序**项目，并命名为 **"测试**"。

3. 在**解决方案资源管理器中**，右键单击测试项目的**参考**节点。 单击“添加引用”****，显示“添加引用”**** 对话框。 单击标记为“项目”**** 的选项卡。 “项目名称”**** 下将列出 `ctlClockLib` 项目。 双击该项目将引用添加到测试项目。

4. 在**解决方案资源管理器**中，右键单击 **"测试**"，然后单击"**生成**"。

5. 在“工具箱”**** 中，展开“ctlClockLib 组件”**** 节点。

6. 双击“ctlAlarmClock”**** 向窗体添加 `ctlAlarmClock` 的副本。

7. 在**工具箱**中，找到并双击**DateTimePicker**以向<xref:System.Windows.Forms.DateTimePicker>表单添加控件，然后通过双击<xref:System.Windows.Forms.Label>**"标签**"添加控件。

8. 使用鼠标将这些控件放置在窗体上合适的位置。

9. 按下述方法设置这些控件的属性。

    |控制|properties|值|
    |-------------|--------------|-----------|
    |`label1`|**文本**|`(blank space)`|
    ||**名称**|`lblTest`|
    |`dateTimePicker1`|**名称**|`dtpTest`|
    ||**格式**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. 在设计器中，双击“dtpTest”****。

     “代码编辑器”**** 随即打开并显示 `private void dtpTest_ValueChanged`。

11. 像如下所示修改代码。

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. 在**解决方案资源管理器**中，右键单击 **"测试**"，然后单击"**设置为启动项目**"。

13. 在**调试**菜单上，单击"**开始调试**"。

     测试程序随即启动。 请注意，当前时间在`ctlAlarmClock`控件中更新，并且开始时间显示在控件中。 <xref:System.Windows.Forms.DateTimePicker>

14. 单击<xref:System.Windows.Forms.DateTimePicker>显示小时分钟的位置。

15. 使用键盘设置一个分钟值，使它比 `ctlAlarmClock` 显示的当前时间快一分钟。

     警报设置的时间在 `lblTest` 中显示。 等候显示的时间到达警报设置时间。 显示时间到达警报设置的时间时，`lblAlarm` 会闪烁。

16. 单击 `btnAlarmOff` 关闭警报。 现在可以重置警报。

本文介绍了一些关键概念。 现已应了解如何通过将控件和组件组合到复合控件容器中来创建复合控件。 还应了解图和将属性添加到控件，以及如何编写代码以实现自定义功能。 在最后一节中，应了解到如何通过继承来扩展给定复合控件的功能，以及如何通过重写承载方法来改变这些方法的功能。

## <a name="see-also"></a>另请参阅

- [各种自定义控件](varieties-of-custom-controls.md)
- [如何：在“选择工具箱项”对话框中显示控件](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [演练：使用 Visual C# 从 Windows 窗体控件继承](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
