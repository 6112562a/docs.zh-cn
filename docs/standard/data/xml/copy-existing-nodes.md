---
title: 复制现有节点
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: fb9ccd7b16d00355ba87bb32f5447906feeecd94
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711059"
---
# <a name="copy-existing-nodes"></a>复制现有节点
XML 文档对象模型 (DOM) 包含许多可用于选择节点的方法和属性，如 SelectSingleNode  、ChildNodes[int i]  、Attributes[int i]  。 选择节点后，可以使用适用于特定节点类型的插入方法之一将该节点插入到树中。 将节点插入到树中的唯一限制是在插入节点后文档的格式仍必须是正确的。 将现有节点插入到 DOM 树中时，该节点从其原始位置移除并添加到它的目标位置。  
  
## <a name="see-also"></a>请参阅

- [XML 文档对象模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
