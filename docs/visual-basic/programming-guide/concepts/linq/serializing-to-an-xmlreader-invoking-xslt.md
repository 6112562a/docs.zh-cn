---
title: 序列化为 XmlReader（调用 XSLT）
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: 39ecbc1851764d221ac99c3e47c26bcbe84c9e46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349356"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a>Serializing to an XmlReader (Invoking XSLT) (Visual Basic)
在使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的 <xref:System.Xml?displayProperty=nameWithType> 互操作性功能时，可以使用 <xref:System.Xml.Linq.XNode.CreateReader%2A> 来创建 <xref:System.Xml.XmlReader>。 从该 <xref:System.Xml.XmlReader> 进行读取的模块从 XML 树读取节点，并对它们进行相应的处理。  
  
## <a name="invoking-an-xslt-transformation"></a>调用 XSLT 转换  
 此方法可能在调用 XSLT 转换时使用。 可以创建 XML 树，从 XML 树创建 <xref:System.Xml.XmlReader>，创建新文档，然后创建 <xref:System.Xml.XmlWriter> 以写入新文档。 接着，可以调用 XSLT 转换，传入 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter>。 在转换成功完成后，使用转换的结果，填充新的 XML 树。  
  
```vb  
Dim xslMarkup As XDocument = _  
    <?xml version='1.0'?>  
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
        <xsl:template match='/Parent'>  
            <Root>  
                <C1>  
                    <xsl:value-of select='Child1'/>  
                </C1>  
                <C2>  
                    <xsl:value-of select='Child2'/>  
                </C2>  
            </Root>  
        </xsl:template>  
    </xsl:stylesheet>  
  
Dim xmlTree As XDocument = _  
    <?xml version='1.0'?>  
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>请参阅

- [Serializing XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
