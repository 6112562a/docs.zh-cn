---
ms.openlocfilehash: 1f5bc43dcba15c28c179b23352558411f511c82f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235177"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>XmlTextReader DTD 实体扩展限制为 10,000,000 个字符

|   |   |
|---|---|
|详细信息|DTD 实体扩展现在限制为 10,000,000 个字符。 加载不带 DTD 实体扩展或带有限的 DTD 实体扩展的 XML 文件不受影响。 包含了扩展到 10,000,000 个字符以上的 DTD 实体的文件将无法加载，且会立即引发异常。|
|建议|如果 DTD 实体扩展的限制低于 10,000,000，该值可使用 <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> 属性重写。 可以将具有适当 <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=name> 值的 <xref:System.Xml.XmlReaderSettings?displayProperty=name> 传递给采用 <xref:System.Xml.XmlReaderSettings?displayProperty=name>（例如 <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>）的 <code>XmlReader.Create</code>|
|范围|边缘|
|版本|4.5|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Xml.XmlTextReader?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)?displayProperty=nameWithType></li></ul>|
