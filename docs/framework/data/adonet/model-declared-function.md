---
title: 模型声明函数
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: cb2fca52604bd57f25469f5621c292a27638c76f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794799"
---
# <a name="model-declared-function"></a>模型声明函数
*模型声明函数*是在概念模型中声明的、但未在该概念模型中定义的函数。 该函数可能是在承载或存储环境中定义的。 例如，模型声明函数可能映射至在数据库中定义的函数，从而在概念模型中提供服务器端的功能。  
  
 模型声明函数的声明包含以下信息：  
  
- 函数名。 （必需）  
  
- 返回值的类型。 （可选）  
  
    > [!NOTE]
    > 如果未指定返回值，则返回类型为 void。  
  
- 参数信息，包括参数名和类型。 （可选）  
  
## <a name="example"></a>示例  
 [ADO.NET 实体框架](./ef/index.md)使用一种称为概念架构定义语言（[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)）的域特定语言（DSL）来定义概念模型。 在 CSDL 中，模型声明函数的一个实现是函数导入（使用[FunctionImport 元素](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)）。 下面的 CSDL 定义了一个实体容器，其中包含一个函数导入定义。 请注意，由于未指定返回类型，因而该函数的返回类型为 void。  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>请参阅

- [实体数据模型关键概念](entity-data-model-key-concepts.md)
- [实体数据模型](entity-data-model.md)
