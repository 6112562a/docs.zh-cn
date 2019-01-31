---
title: 如何：一次一行地读取文本文件 (Visual C#)
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 831f306a19d926b70170c1a6ebc4ab670f1b9851
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718645"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a><span data-ttu-id="63c5a-102">如何：一次一行地读取文本文件 (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="63c5a-102">How to: Read a Text File One Line at a Time (Visual C#)</span></span>
<span data-ttu-id="63c5a-103">此示例使用 `StreamReader` 类的 `ReadLine` 方法，一次一行地将文本文件内容读入字符串。</span><span class="sxs-lookup"><span data-stu-id="63c5a-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="63c5a-104">每个文本行都存储到字符串 `line` 中并显示在屏幕上。</span><span class="sxs-lookup"><span data-stu-id="63c5a-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63c5a-105">示例</span><span class="sxs-lookup"><span data-stu-id="63c5a-105">Example</span></span>  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="63c5a-106">编译代码</span><span class="sxs-lookup"><span data-stu-id="63c5a-106">Compiling the Code</span></span>  
 <span data-ttu-id="63c5a-107">复制代码，并将其粘贴到控制台应用程序的 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="63c5a-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="63c5a-108">将 `"c:\test.txt"` 替换为实际文件名。</span><span class="sxs-lookup"><span data-stu-id="63c5a-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="63c5a-109">可靠编程</span><span class="sxs-lookup"><span data-stu-id="63c5a-109">Robust Programming</span></span>  
 <span data-ttu-id="63c5a-110">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="63c5a-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="63c5a-111">文件可能不存在。</span><span class="sxs-lookup"><span data-stu-id="63c5a-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="63c5a-112">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="63c5a-112">.NET Framework Security</span></span>  
 <span data-ttu-id="63c5a-113">不要根据文件的名称来判断文件的内容。</span><span class="sxs-lookup"><span data-stu-id="63c5a-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="63c5a-114">例如，文件 `myFile.cs` 可能不是 C# 源文件。</span><span class="sxs-lookup"><span data-stu-id="63c5a-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c5a-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="63c5a-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="63c5a-116">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="63c5a-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="63c5a-117">文件系统和注册表（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="63c5a-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
