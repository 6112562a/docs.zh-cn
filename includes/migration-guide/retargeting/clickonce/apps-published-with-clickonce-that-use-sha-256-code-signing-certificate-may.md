---
ms.openlocfilehash: da79a19b3276f6fd2d679eb98406dd85e2a19948
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997560"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>通过 ClickOnce 使用 SHA-256 代码签名证书发布的应用在 Windows 2003 中可能会失败

|   |   |
|---|---|
|详细信息|使用 SHA256 对可执行文件签名。 以前，无论代码签名证书是 SHA-1 还是 SHA-256，都使用 SHA1 进行签名。 这适用于：<ul><li>使用 Visual Studio 2012 或更高版本生成的所有应用程序。</li><li>使用 Visual Studio 2010 或更早版本在安装了 .NET Framework 4.5 的系统上生成的应用程序。</li></ul>此外，如果安装了 .NET Framework 4.5 或更高版本，则 ClickOnce 清单也会采用 SHA-256 签名，因为 SHA-256 证书与编译所采用的 .NET Framework 版本无关。|
|建议|更改 ClickOnce 可执行文件的签名仅影响 Windows Server 2003 系统；它们需要安装 KB 938397。 即使应用是面向 .NET Framework 4.0 或早期版本，对使用 SHA-256 签名的清单进行更改，将引入依赖 .NET Framework 4.5 或更高版本的运行时。|
|范围|边缘|
|Version|4.5|
|类型|重定目标|
