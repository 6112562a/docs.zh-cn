---
title: 如何：使实体可序列化
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 40a0b4d5a49f88af1bedcbefdd117f6c000b791d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793563"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="364b8-102">如何：使实体可序列化</span><span class="sxs-lookup"><span data-stu-id="364b8-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="364b8-103">当您生成代码时，可以使实体可序列化。</span><span class="sxs-lookup"><span data-stu-id="364b8-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="364b8-104">实体类使用 <xref:System.Runtime.Serialization.DataContractAttribute> 属性修饰，列使用 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性修饰。</span><span class="sxs-lookup"><span data-stu-id="364b8-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="364b8-105">使用 Visual Studio 的开发人员可以使用对象关系设计器来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="364b8-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="364b8-106">如果使用 SQLMetal 命令行工具，请将 **/serialization**选项与`unidirectional`参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="364b8-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="364b8-107">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="364b8-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="364b8-108">示例</span><span class="sxs-lookup"><span data-stu-id="364b8-108">Example</span></span>  
 <span data-ttu-id="364b8-109">以下 SQLMetal 命令行会产生包含可序列化实体的文件。</span><span class="sxs-lookup"><span data-stu-id="364b8-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="364b8-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="364b8-110">See also</span></span>

- [<span data-ttu-id="364b8-111">序列化</span><span class="sxs-lookup"><span data-stu-id="364b8-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="364b8-112">创建对象模型</span><span class="sxs-lookup"><span data-stu-id="364b8-112">Creating the Object Model</span></span>](creating-the-object-model.md)
