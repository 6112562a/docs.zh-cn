---
ms.openlocfilehash: f01d0a24202ecda7e23cbe925bb6dc8962cb7574
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750718"
---
> [!CAUTION]
>  <span data-ttu-id="61049-101">代码访问安全性和部分受信任的代码</span><span class="sxs-lookup"><span data-stu-id="61049-101">Code Access Security and Partially Trusted Code</span></span>  
>   
>  <span data-ttu-id="61049-102">.NET Framework 提供一种机制，对在相同应用程序中运行的不同代码强制实施不同的信任级别，该机制称为代码访问安全性 (CAS)。</span><span class="sxs-lookup"><span data-stu-id="61049-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>  <span data-ttu-id="61049-103">.NET Framework 中的代码访问安全性不应用作基于代码来源或其他标识方面强制实施安全边界的一种机制。</span><span class="sxs-lookup"><span data-stu-id="61049-103">Code Access Security in .NET Framework should not  be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="61049-104">我们正在更新相应指南以反映代码访问安全性，并且将不支持把安全透明代码用作部分受信任的代码（尤其是未知来源的代码）的安全边界。</span><span class="sxs-lookup"><span data-stu-id="61049-104">We are updating our guidance to reflect that Code Access Security and Security-Transparent Code will not be supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="61049-105">建议在未实施其他安全措施的情况下，不要加载和执行未知来源的代码。</span><span class="sxs-lookup"><span data-stu-id="61049-105">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>  
>   
>  <span data-ttu-id="61049-106">此策略适用于 .NET Framework 的所有版本，但不适用于 Silverlight 中所含的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="61049-106">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>