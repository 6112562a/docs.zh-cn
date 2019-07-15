---
ms.openlocfilehash: dd4e387f798b3f93f3eabccb5357399fbe5a4fc1
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804586"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>通过 ClickOnce 使用 SHA-256 代码签名证书发布的应用在 Windows 2003 中可能会失败

|   |   |
|---|---|
|详细信息|使用 SHA256 对可执行文件签名。 以前，无论代码签名证书是 SHA-1 还是 SHA-256，都使用 SHA1 进行签名。 这适用于：<ul><li>使用 Visual Studio 2012 或更高版本生成的所有应用程序。</li><li>使用 Visual Studio 2010 或更早版本在安装了 .NET Framework 4.5 的系统上生成的应用程序。</li></ul>此外，如果安装了 .NET Framework 4.5 或更高版本，则 ClickOnce 清单也会采用 SHA-256 签名，因为 SHA-256 证书与编译所采用的 .NET Framework 版本无关。|
|建议|更改 ClickOnce 可执行文件的签名仅影响 Windows Server 2003 系统；它们需要安装 KB 938397。即使应用是面向 .NET Framework 4.0 或早期版本，对使用 SHA-256 签名的清单进行更改，将引入依赖 .NET Framework 4.5 或更高版本的运行时。|
|范围|边缘|
|版本|4.5|
|类型|重定目标|

