---
title: 封送 MDA
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a6399828f934ad97cde9f36d75cfe3bfc410885
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052488"
---
# <a name="marshaling-mda"></a>封送 MDA
当 CLR 为方法参数或结构的字段设置封送处理信息时，将激活 `marshaling` 托管调试助手 (MDA)。 此 MDA 不适合 JIT 编译的程序集。  
  
## <a name="effect-on-the-runtime"></a>对运行时的影响  
 此 MDA 对 CLR 无任何影响。  
  
## <a name="output"></a>Output  
 此 MDA 显示托管和非托管上下文中参数或字段的类型，以及包含此类型的结构或方法。  以下是字段输出的示例：  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a>配置  
 MDA 配置允许你基于所涉及的字段或方法名称，筛选报告的封送处理信息。  以下示例演示如何使用 `methodFilter`、`fieldFilter` 和 `match` 元素指定筛选器。  将属性设置为星号（\*）可匹配所有内容。 `name`  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [使用托管调试助手诊断错误](diagnosing-errors-with-managed-debugging-assistants.md)
- [互操作封送处理](../interop/interop-marshaling.md)
