---
title: 如何：使用平台调用播放波形文件 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: cf8415b2d501ae2394fa76170eb232da33c3e308
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589108"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>如何：使用平台调用播放波形文件（C# 编程指南）
下面的 C# 代码示例说明了如何使用平台调用服务在 Windows 操作系统中播放波形声音文件。  
  
## <a name="example"></a>示例  
 此示例代码使用 `DllImport` 将 `winmm.dll` 的 `PlaySound` 方法入口点导入为 `Form1 PlaySound()`。 本示例具有一个带按钮的简单 Windows 窗体。 单击该按钮将打开一个标准的 Windows <xref:System.Windows.Forms.OpenFileDialog> 对话框，以便你可以打开要播放的文件。 选中波形文件时，将使用 `winmm.dll` 库的 `PlaySound()` 方法进行播放。 有关此方法的详细信息，请参阅[使用 PlaySound 功能处理波形音频文件](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files)。 浏览并选择具有 .wav 扩展名的文件，然后单击“打开”  以使用平台调用播放波形文件。 文本框中显示所选文件的完整路径。  
  
 通过筛选器设置对“打开文件”  对话框进行筛选，以仅显示扩展名为 .wav 的文件：  
  
 [!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]  
  
 [!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]  
  
## <a name="compiling-the-code"></a>编译代码  
  
1. 在 Visual Studio 中创建新的 C# Windows 应用程序项目，然后将其命名为“WinSound”  。  
  
2. 复制上面的代码，然后将其粘贴到 `Form1.cs` 文件的内容上。  
  
3. 复制以下代码，然后用 `InitializeComponent()` 方法将其粘贴到 `Form1.Designer.cs` 文件中任何现有代码之后。  
  
     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]  
  
4. 编译并运行该代码。  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../index.md)
- [互操作性概述](./interoperability-overview.md)
- [平台调用详解](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [用平台调用封送数据](../../../framework/interop/marshaling-data-with-platform-invoke.md)
