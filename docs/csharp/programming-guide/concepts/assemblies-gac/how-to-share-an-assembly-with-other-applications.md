---
title: 如何：与其他应用程序共享程序集 (C#)
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 8bb36c2aded1144349b86b17a45eef4b48c8aabe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314784"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>如何：与其他应用程序共享程序集 (C#)
程序集可以是私有或共享程序集：默认情况下，大多数简单程序都包含一个私有程序集，因为它们并不打算由其他应用程序使用。  
  
 若要与其他应用程序共享程序集，必须将它放置在[全局程序集缓存](../../../../framework/app-domains/gac.md) (GAC) 中。  
  
### <a name="sharing-an-assembly"></a>共享程序集  
  
1. 创建程序集。 有关详细信息，请参阅[创建程序集](../../../../framework/app-domains/create-assemblies.md)。  
  
2. 向程序集分配强名称。 有关详细信息，请参阅[如何：使用强名称为程序集签名](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。  
  
3. 将版本信息分配给程序集。 有关详细信息，请参阅[程序集版本控制](../../../../../docs/framework/app-domains/assembly-versioning.md)。  
  
4. 将程序集添加到全局程序集缓存中。 有关详细信息，请参阅[如何：将程序集安装到全局程序集缓存](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)。  
  
5. 从其他应用程序访问该程序集中包含的类型。 有关详细信息，请参阅[如何：引用具有强名称的程序集](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)。  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../../../../csharp/programming-guide/index.md)
- [使用程序集编程](../../../../framework/app-domains/programming-with-assemblies.md)
