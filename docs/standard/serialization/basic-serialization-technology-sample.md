---
title: 基本序列化技术示例
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: 43e69ce90b86053badad91b62ec288378e63e2ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681698"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="cf1bc-102">基本序列化技术示例</span><span class="sxs-lookup"><span data-stu-id="cf1bc-102">Basic Serialization Technology Sample</span></span>
[<span data-ttu-id="cf1bc-103">下载示例</span><span class="sxs-lookup"><span data-stu-id="cf1bc-103">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 <span data-ttu-id="cf1bc-104">本示例说明公共语言运行时将内存中的对象图序列化成流的能力。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-104">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="cf1bc-105">此示例可以使用 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 或 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 来进行序列化。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-105">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="cf1bc-106">用数据填充的链接列表可以被序列化成文件流，也可以从文件流反序列化该链接列表。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-106">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="cf1bc-107">上述任何一种情况都会显示该列表，这样，您就可以看到相应的结果。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-107">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="cf1bc-108">链接列表的类型为 `LinkedList`，该类型由此示例定义。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-108">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>  
  
 <span data-ttu-id="cf1bc-109">有关序列化的更多信息，请查看源代码中的注释以及 build.proj 文件。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-109">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="cf1bc-110">使用命令提示生成示例</span><span class="sxs-lookup"><span data-stu-id="cf1bc-110">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="cf1bc-111">使用命令提示定位到 Technologies\Serialization\Runtime Serialization\Basic 目录下语言特定的子目录之一。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-111">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="cf1bc-112">在命令行中键入 msbuild SerializationCS.sln、msbuild SerializationJSL.sln 或 msbuild SerializationVB.sln，具体取决于所选的编程语言。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-112">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="cf1bc-113">使用 Visual Studio 生成示例</span><span class="sxs-lookup"><span data-stu-id="cf1bc-113">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="cf1bc-114">打开[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]，定位到该示例的特定语言的子目录。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="cf1bc-115">根据所选的编程语言，双击 SerializationCS.sln、SerializationJSL.sln 或 SerializationVB.sln 文件的图标，在 Visual Studio 中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-115">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="cf1bc-116">在“生成”菜单中选择“生成解决方案”。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-116">In the **Build** menu, select **Build Solution**.</span></span>  
  
 <span data-ttu-id="cf1bc-117">示例应用程序将在默认的 \bin 或 \bin\Debug 子目录中生成。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-117">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="cf1bc-118">运行示例</span><span class="sxs-lookup"><span data-stu-id="cf1bc-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="cf1bc-119">定位到包含生成的可执行文件的目录。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-119">Navigate to the directory containing the built executable.</span></span>  
  
2.  <span data-ttu-id="cf1bc-120">在命令行中键入 Serialization.exe 以及所需的参数值。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-120">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cf1bc-121">此示例生成控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-121">This sample builds a console application.</span></span> <span data-ttu-id="cf1bc-122">必须使用命令提示来启动该程序，才能查看相应的输出。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-122">You must launch it using the command prompt in order to view its output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf1bc-123">备注</span><span class="sxs-lookup"><span data-stu-id="cf1bc-123">Remarks</span></span>  
 <span data-ttu-id="cf1bc-124">示例应用程序接受指示您要执行何种测试的命令行参数。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-124">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="cf1bc-125">若要使用 SOAP 格式化程序将 10 节点列表序列化成名为 Test.xml 的文件，请使用参数 sx Test.xml 10。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-125">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>  
  
 <span data-ttu-id="cf1bc-126">例如：</span><span class="sxs-lookup"><span data-stu-id="cf1bc-126">For Example:</span></span>  
  
 <span data-ttu-id="cf1bc-127">**Serialize.exe -sx Test.xml 10**</span><span class="sxs-lookup"><span data-stu-id="cf1bc-127">**Serialize.exe -sx Test.xml 10**</span></span>  
  
 <span data-ttu-id="cf1bc-128">若要从先前的示例中反序列化 Test.xml文件，请使用参数 dx Test.xml。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-128">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>  
  
 <span data-ttu-id="cf1bc-129">例如：</span><span class="sxs-lookup"><span data-stu-id="cf1bc-129">For Example:</span></span>  
  
 <span data-ttu-id="cf1bc-130">**Serialize.exe -dx Test.xml**</span><span class="sxs-lookup"><span data-stu-id="cf1bc-130">**Serialize.exe -dx Test.xml**</span></span>  
  
 <span data-ttu-id="cf1bc-131">在上面的两个示例中，命令行开关中的“x”指示您需要 XML SOAP 序列化。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="cf1bc-132">您可以用“b”来代替它，以使用二进制序列化。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="cf1bc-133">如果您想尝试对非常多的节点进行序列化，则可能需要将控制台输出重定向到某个文件。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>  
  
 <span data-ttu-id="cf1bc-134">例如：</span><span class="sxs-lookup"><span data-stu-id="cf1bc-134">For Example:</span></span>  
  
 <span data-ttu-id="cf1bc-135">**Serialize.exe -sb Test.bin 10000 >somefile.txt**</span><span class="sxs-lookup"><span data-stu-id="cf1bc-135">**Serialize.exe -sb Test.bin 10000 >somefile.txt**</span></span>  
  
 <span data-ttu-id="cf1bc-136">下面的项目符号简要说明了此示例所使用的类和技术。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-136">The following bullets briefly describe the classes and technologies used by this sample.</span></span>  
  
-   <span data-ttu-id="cf1bc-137">运行时序列化</span><span class="sxs-lookup"><span data-stu-id="cf1bc-137">Runtime Serialization</span></span>  
  
    -   <span data-ttu-id="cf1bc-138"><xref:System.Runtime.Serialization.IFormatter> 可用于引用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 或 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 对象。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-138"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>  
  
    -   <span data-ttu-id="cf1bc-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 可用于将链接列表序列化成二进制格式的流。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="cf1bc-140">二进制格式化程序使用了只有 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 类型才理解的格式。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-140">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="cf1bc-141">然而，该数据非常简明。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-141">However, the data is concise.</span></span>  
  
    -   <span data-ttu-id="cf1bc-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 可用于将链接列表序列化成 SOAP 格式的流。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="cf1bc-143">SOAP 是一种标准格式。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-143">SOAP is a standard format.</span></span>  
  
-   <span data-ttu-id="cf1bc-144">流 I/O</span><span class="sxs-lookup"><span data-stu-id="cf1bc-144">Stream I/O</span></span>  
  
    -   <span data-ttu-id="cf1bc-145"><xref:System.IO.Stream> 可用于序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-145"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="cf1bc-146">此示例中使用的特定流类型是 <xref:System.IO.FileStream> 类型。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-146">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="cf1bc-147">然而，序列化可以用于从 <xref:System.IO.Stream> 派生的任何类型。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-147">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>  
  
    -   <span data-ttu-id="cf1bc-148"><xref:System.IO.File> 可用于创建 <xref:System.IO.FileStream> 对象，以便在磁盘上读取和创建文件。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-148"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>  
  
    -   <span data-ttu-id="cf1bc-149"><xref:System.IO.FileStream> 可用于对链接列表进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="cf1bc-149"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf1bc-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="cf1bc-150">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File>
- <xref:System.IO.FileStream>
- <xref:System.IO.Stream>
- <xref:System.Random>
- <xref:System.Runtime.Serialization>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.IFormatter>
- <xref:System.SerializableAttribute>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="cf1bc-151">基本序列化</span><span class="sxs-lookup"><span data-stu-id="cf1bc-151">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)
- [<span data-ttu-id="cf1bc-152">二进制序列化</span><span class="sxs-lookup"><span data-stu-id="cf1bc-152">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
- [<span data-ttu-id="cf1bc-153">使用属性控制 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="cf1bc-153">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="cf1bc-154">XML 序列化简介</span><span class="sxs-lookup"><span data-stu-id="cf1bc-154">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="cf1bc-155">序列化</span><span class="sxs-lookup"><span data-stu-id="cf1bc-155">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="cf1bc-156">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="cf1bc-156">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
