---
title: 隐式类型化 lambda 表达式
description: 了解为什么不能使用隐式类型化变量声明来声明 lambda 表达式。
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: c6b0f2666a5c67ce8c89222da5959304ecb8fb93
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039126"
---
# <a name="implicitly-typed-lambda-expressions"></a>隐式类型化 lambda 表达式

不能使用隐式类型化变量声明来声明 lambda 表达式。
它会对编译器造成循环逻辑问题。 `var` 声明会告知编译器通过赋值运算符右侧的表达式的类型查明变量的类型。 Lambda 表达式没有编译时类型，但是可转换为任何匹配委托或表达式类型。 将 lambda 表达式分配给委托或表达式类型的变量时，可告知编译器尝试并将 lambda 表达式转换为与“分配对象”变量的签名匹配的表达式或委托。 编译器必须尝试使赋值右侧的内容与赋值左侧的类型匹配。 

赋值两侧都无法告知编译器查看赋值运算符另一侧的对象并查看我的类型是否匹配。

通过阅读[这篇文章](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf)（PDF 下载），甚至可以获得有关 C# 语言为何指定该行为的详细信息
