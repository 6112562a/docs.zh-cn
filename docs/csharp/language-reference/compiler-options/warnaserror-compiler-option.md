---
title: -warnaserror（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 66c78ee56c9d5153b5b878b2e695ad4ee6bffe0b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606249"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror（C# 编译器选项）
-warnaserror+ 选项将所有警告视为错误   
  
## <a name="syntax"></a>语法  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>备注  
 通常报告为警告的消息被报告为错误，生成过程暂停（不生成任何输出文件）。  
  
 默认情况下，-warnaserror- 将生效，导致警告不会阻止生成输出文件  。 -warnaserror 与 -warnaserror+ 相同，会导致将警告视为错误   。  
  
 （可选）如果希望仅将一些特定警告视为错误，则可以指定视为错误的警告编号的逗号分隔列表。  
  
 使用 [-warn](./warn-compiler-option.md) 指定想要编译器显示的警告等级。 使用 [-nowarn](./nowarn-compiler-option.md) 禁用某些警告。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1. 打开项目的“属性”  页。  
  
2. 单击“生成”  属性页。  
  
3. 修改“将警告视为错误”  属性。  
  
 若要以编程方式设置此编译器选项，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>。  
  
## <a name="example"></a>示例  
 编译 `in.cs` 并使编译器不显示警告：  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>请参阅

- [C# 编译器选项](./index.md)
- [管理项目和解决方案属性](/visualstudio/ide/managing-project-and-solution-properties)
