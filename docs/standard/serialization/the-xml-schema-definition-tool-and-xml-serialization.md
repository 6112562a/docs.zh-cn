---
title: XML 架构定义工具和 XML 序列化
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: 4c950d84cc95c20c2ae85340a2987ea51bed9570
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979315"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="d9422-102">XML 架构定义工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="d9422-102">The XML Schema Definition Tool and XML Serialization</span></span>
<span data-ttu-id="d9422-103">XML 架构定义工具 ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) 是作为 Windows® 软件开发工具包 (SDK) 的一部分随 .NET Framework 工具一起安装的。</span><span class="sxs-lookup"><span data-stu-id="d9422-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows® Software Development Kit (SDK).</span></span> <span data-ttu-id="d9422-104">该工具主要有下面两个用途：</span><span class="sxs-lookup"><span data-stu-id="d9422-104">The tool is designed primarily for two purposes:</span></span>  
  
-   <span data-ttu-id="d9422-105">生成 C# 或 Visual Basic 类文件，而这些文件符合特定的 XML 架构定义语言 (XSD) 架构。</span><span class="sxs-lookup"><span data-stu-id="d9422-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="d9422-106">该工具将 XML 架构用作参数，并输出一个包含若干类的文件，在使用 <xref:System.Xml.Serialization.XmlSerializer> 进行序列化时，这些类符合这种架构。</span><span class="sxs-lookup"><span data-stu-id="d9422-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="d9422-107">有关如何使用该工具生成符合特定架构的类的信息，请参阅[如何：使用 XML 架构定义工具生成类和 XML 架构文档](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)。</span><span class="sxs-lookup"><span data-stu-id="d9422-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
-   <span data-ttu-id="d9422-108">通过 .dll 或 .exe 文件生成 XML 架构文档。</span><span class="sxs-lookup"><span data-stu-id="d9422-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="d9422-109">若要查看已经创建或已使用特性进行修改的一组文件的架构，可以将 DLL 或 EXE 作为参数传递到该工具，以便生成 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="d9422-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="d9422-110">有关如何使用该工具从一组类生成 XML 架构文档的信息，请参阅[如何：使用 XML 架构定义工具生成类和 XML 架构文档](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)。</span><span class="sxs-lookup"><span data-stu-id="d9422-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
 <span data-ttu-id="d9422-111">有关此工具和其他工具的更多信息，请参阅[工具](../../../docs/framework/tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d9422-111">For more information about this tool and others, see [Tools](../../../docs/framework/tools/index.md).</span></span> <span data-ttu-id="d9422-112">有关此工具的选项的信息，请参阅 [XML 架构定义工具 (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="d9422-112">For information about the tool's options, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9422-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="d9422-113">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="d9422-114">XML 序列化简介</span><span class="sxs-lookup"><span data-stu-id="d9422-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="d9422-115">XML 架构定义工具 (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="d9422-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="d9422-116">如何：将对象序列化</span><span class="sxs-lookup"><span data-stu-id="d9422-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="d9422-117">如何：反序列化对象</span><span class="sxs-lookup"><span data-stu-id="d9422-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="d9422-118">如何：使用 XML 架构定义工具生成类和 XML 架构文档</span><span class="sxs-lookup"><span data-stu-id="d9422-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- <span data-ttu-id="d9422-119">[XML 架构绑定支持](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d9422-119">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>
