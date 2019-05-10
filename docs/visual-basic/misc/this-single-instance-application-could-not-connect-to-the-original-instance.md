---
title: 此单实例应用程序未能连接到原始实例
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 5585da7f2ccf7d5d3ec8db281ab9534249020a63
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619850"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>此单实例应用程序未能连接到原始实例
此单实例应用程序未能连接到原始实例。 一些可能导致此问题的原因包括：  
  
- 原始实例停止了响应。  
  
- 应用程序没有创建内核对象的权限。 有关内核对象的详细信息，请参阅[Mutex](../../standard/threading/mutexes.md)。  
  
     内核对象的基名称是通过串联程序集的 GUID、主版本号和次版本号得到的。 例如，基名称可能是 `3639f15d-9547-43da-8145-60da347829915.1`。  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>在开发应用程序时更正此错误  
  
1. 检查应用程序未进入未响应状态。  
  
2. 检查应用程序是否具有创建内核对象的足够权限。  
  
3. 重启应用程序的原始实例。  
  
4. 重启计算机，以清除可能正在使用连接到原始实例应用程序所需资源的任何进程。  
  
5. 记录发生错误的环境，并与 Microsoft 产品支持服务联系。  
  
## <a name="see-also"></a>请参阅

- [调试器基础知识](/visualstudio/debugger/debugger-basics)
