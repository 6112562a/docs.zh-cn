---
title: 文本 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: 6196c1b026b49847bd06cc9cda5ea6b6af289858
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953291"
---
# <a name="literals-entity-sql"></a>文本 (Entity SQL)
本主题介绍 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 对于文字的支持。  
  
## <a name="null"></a>null  
 空文字用于表示对任何类型均为空的值。 空文字与任何类型兼容。  
  
 强制转换可以在空文字之上创建类型空值。 有关详细信息, 请参阅[CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)。  
  
 有关可以使用自由浮动 null 文本的规则, 请参阅[Null 文本和类型推理](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)。  
  
## <a name="boolean"></a>Boolean  
 布尔值文字由关键字 `true` 和 `false` 表示。  
  
## <a name="integer"></a>整数  
 整型文字可以为类型 <xref:System.Int32> 或 <xref:System.Int64>。 <xref:System.Int32> 文字是一系列数字字符。 <xref:System.Int64> 文字是一系列数字字符，后跟一个大写 L。  
  
## <a name="decimal"></a>Decimal  
 固定点数字（小数）是一系列数字字符、一个圆点 (.) 和另一系列数字字符，后跟一个大写“M”。  
  
## <a name="float-double"></a>浮点，双精度  
 双精度浮点数字是一系列数字字符、一个圆点 (.) 和另一系列数字字符，后面可能跟一个指数。 单精度浮点数字（或浮点数）是双精度浮点数字语法后跟小写 f。  
  
## <a name="string"></a>String  
 字符串是包含在引号内的一系列字符。 引号可以同时为单引号 (`'`) 或同时为双引号 (")。 字符串文字可以是 Unicode 或非 Unicode。 若要将字符串文字声明为 Unicode，请在文字之前加上大写“N”作为前缀。 默认值为非 Unicode 字符串文字。 在 N 与字符串文字负载之间不能存在空格，并且 N 必须为大写。  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a>DateTime  
 日期时间文字独立于区域设置并由日期部分和时间部分组成。 日期部分和时间部分都是必需的，并且没有默认值。  
  
 日期`YYYY`部分的格式必须为: - - `MM` `DD` `MM` , 其中是`YYYY`介于0001和9999之间的四位数年份值, 是介于1和12之间的月份, 是`DD`给定月份`MM`有效的日期值。  
  
 时间部分的格式必须为：`HH`:`MM`[:`SS`[.fffffff]]，其中 `HH` 为介于 0 至 23 之间的小时值，`MM` 为介于 0 至 59 之间的分钟值，`SS` 为介于 0 至 59 之间的秒值，而 fffffff 为介于 0 至 9999999 之间的秒的小数部分值。 所有值范围都包含两端。 秒的小数部分是可选的。 除非指定了秒的小数部分，否则秒是可选的；在指定了秒的小数部分时秒是必需的。 在未指定秒或秒的小数部分时，将使用默认值零。  
  
 在 DATETIME 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a>时间  
 时间文字独立于区域设置并仅由时间部分组成。 时间部分为必选项，且没有默认值。 其格式必须为 HH:MM[:SS[.fffffff]]，其中 HH 为介于 0 至 23 之间的小时值，MM 为介于 0 至 59 之间的分钟值，SS 为介于 0 至 59 之间的秒值，而 fffffff 为介于 0 至 9999999 之间的秒的小数部分值。 所有值范围都包含两端。 秒的小数部分是可选的。 除非指定了秒的小数部分，否则秒是可选的；在指定了秒的小数部分时秒是必需的。 在未指定秒或秒的小数部分时，将使用默认值零。  
  
 在 TIME 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a>DateTimeOffset  
 datetimeoffset 文字独立于区域设置并由日期部分、时间部分和偏移量部分组成。 所有日期、时间和偏移量部分都是必选项，并且没有默认值。 日期部分的格式必须为 YYYY-MM-DD，其中 YYYY 是介于 0001 与 9999 之间的四位年度值，MM 是介于 1 与 12 之间的月份，而 DD 是对给定月份有效的日期值。 时间部分的格式必须为 HH:MM[:SS[.fffffff]]，其中 HH 为介于 0 至 23 之间的小时值，MM 为介于 0 至 59 之间的分钟值，SS 为介于 0 至 59 之间的秒值，而 fffffff 为介于 0 至 9999999 之间的秒的小数部分值。 所有值范围都包含两端。 秒的小数部分是可选的。 除非指定了秒的小数部分，否则秒是可选的；在指定了秒的小数部分时秒是必需的。 在未指定秒或秒的小数部分时，将使用默认值零。 偏移量部分的格式必须为 {+&#124;-} HH: MM, 其中 HH 和 MM 与时间部分具有相同的含义。 但是，偏移量的范围必须介于 -14:00 至 + 14:00 之间。  
  
 在 DATETIMEOFFSET 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> 有效的 Entity SQL 文字值可能处于 CLR 或数据源所支持的范围之外。 这可能会导致异常。  
  
## <a name="binary"></a>二进制  
 二进制字符串文字是由单引号分隔的一系列十六进制数字，后跟关键字“binary”或快捷方式符号 `X`/`x`。 快捷方式符号 `X` 是不区分大小写的。 在关键字 `binary` 与二进制字符串值之间可以有零个或零个以上空格。  
  
 十六进制字符也不区分大小写。 如果文字由奇数个十六进制数字组成，则将通过在文字之前附加十六进制数字零作为前缀，使文字与下一个偶数十六进制数字对齐。 对于二进制字符串的大小，不存在正式的限制。  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a>Guid  
 `GUID` 文本表示全局唯一标识符。 它是由关键字`GUID`构成的序列, 后跟十六进制数字, 格式称为*注册表*格式:包含在单引号内的 8-4-4-4-12。 十六进制数字区分大小写。  
  
 在 GUID 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a>请参阅

- [实体 SQL 概述](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
