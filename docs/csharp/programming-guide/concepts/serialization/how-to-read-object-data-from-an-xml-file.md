---
title: 如何从 XML 文件读取对象数据 (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 18428cbe2f2d3b9434a77ee4d063ceabbba6bcb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167813"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="78410-102">如何从 XML 文件读取对象数据 (C#)</span><span class="sxs-lookup"><span data-stu-id="78410-102">How to read object data from an XML file (C#)</span></span>
<span data-ttu-id="78410-103">本示例使用 <xref:System.Xml.Serialization.XmlSerializer> 类读取之前写入 XML 文件的对象数据。</span><span class="sxs-lookup"><span data-stu-id="78410-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78410-104">示例</span><span class="sxs-lookup"><span data-stu-id="78410-104">Example</span></span>  
  
```csharp  
public class Book  
{  
    public String title;  
}
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="78410-105">编译代码</span><span class="sxs-lookup"><span data-stu-id="78410-105">Compiling the Code</span></span>  
<span data-ttu-id="78410-106">将文件名称“c:\temp\SerializationOverview.xml”替换为包含序列化数据的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="78410-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="78410-107">有关序列化数据的详细信息，请参阅[如何将对象数据写入 XML 文件 (C#)](./how-to-write-object-data-to-an-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="78410-107">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="78410-108">类必须有一个公共的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="78410-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="78410-109">只有公共属性和字段才会进行反序列化。</span><span class="sxs-lookup"><span data-stu-id="78410-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="78410-110">可靠编程</span><span class="sxs-lookup"><span data-stu-id="78410-110">Robust Programming</span></span>  
 <span data-ttu-id="78410-111">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="78410-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="78410-112">进行序列化的类没有公共的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="78410-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="78410-113">文件中的数据不表示要进行反序列化的类中的数据。</span><span class="sxs-lookup"><span data-stu-id="78410-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="78410-114">该文件不存在 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="78410-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="78410-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="78410-115">.NET Framework Security</span></span>  
 <span data-ttu-id="78410-116">始终验证输入，并且绝不会反序列化来自不受信任源的数据。</span><span class="sxs-lookup"><span data-stu-id="78410-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="78410-117">重新创建的对象会在具有对它进行反序列化的代码的权限的本地计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="78410-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="78410-118">在应用程序中使用输入的数据之前，需验证所有的输入内容。</span><span class="sxs-lookup"><span data-stu-id="78410-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78410-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78410-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="78410-120">如何将对象数据写入 XML 文件 (C#)</span><span class="sxs-lookup"><span data-stu-id="78410-120">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="78410-121">序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="78410-121">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="78410-122">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="78410-122">C# Programming Guide</span></span>](../../index.md)
