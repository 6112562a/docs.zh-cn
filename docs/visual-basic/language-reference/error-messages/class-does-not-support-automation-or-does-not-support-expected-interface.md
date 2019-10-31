---
title: 类不支持自动化或不支持所需的接口
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: d249648748249af438ee6228cccc8e74f68407fb
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197529"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="485ac-102">类不支持自动化或不支持所需的接口</span><span class="sxs-lookup"><span data-stu-id="485ac-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="485ac-103">在 `GetObject` 或 `CreateObject` 函数调用中所指定的类尚未公开可编程接口，或者将项目从 .dll 更改为 .exe 或相反。</span><span class="sxs-lookup"><span data-stu-id="485ac-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="485ac-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="485ac-104">To correct this error</span></span>  
  
1. <span data-ttu-id="485ac-105">检查创建对象的应用程序的相关文档，确定该对象类是否存在使用自动化的限制。</span><span class="sxs-lookup"><span data-stu-id="485ac-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="485ac-106">如果将项目从 .dll 更改为 .exe 或者相反，必须手动注销旧的 .dll 或 .exe。</span><span class="sxs-lookup"><span data-stu-id="485ac-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="485ac-107">请参阅</span><span class="sxs-lookup"><span data-stu-id="485ac-107">See also</span></span>

- [<span data-ttu-id="485ac-108">错误类型</span><span class="sxs-lookup"><span data-stu-id="485ac-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="485ac-109">与我们交流</span><span class="sxs-lookup"><span data-stu-id="485ac-109">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
