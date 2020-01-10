---
title: 创建加密方案
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 00fff5f346633a9682d75cf6a3be7e8e7d5db7e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706287"
---
# <a name="creating-a-cryptographic-scheme"></a>创建加密方案
可结合使用 .NET Framework 的加密组件来创建不同的方案，以加密和解密数据。  
  
 用于加密和解密数据的简单加密方案可能指定以下步骤：  
  
1. 每个参与方均生成一个公钥/私钥对。  
  
2. 双方交换各自的公钥。  
  
3. 例如，每个参与方均生成一个用于加密 TripleDES 的密钥，并使用对方的公钥对新创建的密钥进行加密。  
  
4. 每个参与方都将数据发送给另一方，并以特定的顺序将对方的密钥与自身的密钥相结合，以创建新密钥。  
  
5. 然后，双方使用对称加密启动一个对话。  
  
 创建加密方案是一项重要任务。
  
## <a name="see-also"></a>另请参阅

- [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
