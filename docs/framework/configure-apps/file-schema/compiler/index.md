---
title: 编译器和语言提供程序设置架构
ms.date: 03/30/2017
helpviewer_keywords:
- configuration settings [.NET Framework], compilers
- compiler configuration elements, schema
- compiler configuration elements
- language providers
- compiler configuration settings, schema
- configuration schema [.NET Framework], compiler settings
- language providers, settings schema
- compiler configuration settings
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
ms.openlocfilehash: a651e4ca76fda9e65ea4a5848c19b1f0ebfe91b1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168931"
---
# <a name="compiler-and-language-provider-settings-schema"></a>编译器和语言提供程序设置架构
编译器和语言提供程序设置指定可用语言提供程序的编译器配置元素。 每个编译器配置元素指定代码提供程序类型名称、编译器参数、支持语言名称以及支持的文件扩展名。  
  
.NET Framework 在计算机配置文件 (Machine.config) 中定义初始编译器设置。 开发人员和编译器供应商可以添加新 <xref:System.CodeDom.Compiler.CodeDomProvider> 实现的配置设置。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以编程方式枚举计算机上的语言提供程序和编译器配置设置。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<system.object >** ](system-codedom-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<编译器 >** ](compilers-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<编译器 >** ](compiler-element.md)  
  
|元素|描述|  
|-------------|-----------------|  
|[\<system.codedom>](system-codedom-element.md)|指定可用语言提供程序的编译器配置设置。|  
|[\<compilers>](compilers-element.md)|编译器配置元素的容器；包含零个或多个 [\<compiler>](compiler-element.md) 元素。|  
|[\<compiler>](compiler-element.md)|指定语言提供程序的编译器配置属性。|  
  
## <a name="example"></a>示例  
 以下示例说明典型的编译器配置元素。  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler  
          language="c#;cs;csharp"  
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""  
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [配置文件架构](../index.md)
- [\<compiler> Element](compiler-element.md)
