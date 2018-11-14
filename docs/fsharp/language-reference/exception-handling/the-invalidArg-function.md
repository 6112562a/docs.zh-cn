---
title: 异常：invalidArg 函数 (F#)
description: 了解如何为 F# invalidArg 函数生成参数异常。
ms.date: 05/16/2016
ms.openlocfilehash: 8bf65fae9392a88205e3cdec8b7d7a3ff42f8416
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2018
ms.locfileid: "44180314"
---
# <a name="exceptions-the-invalidarg-function"></a>异常：invalidArg 函数

`invalidArg`函数生成参数异常。

## <a name="syntax"></a>语法

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>备注

在上述语法中的参数名称是参数的其参数是参数的无效名称的字符串。 *错误消息字符串*是文本字符串或类型的值`string`。 它将成为`Message`异常对象的属性。

由生成的异常`invalidArg`是`System.ArgumentException`异常。 下面的代码演示如何使用`invalidArg`引发异常。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

输出是以下内容，然后由堆栈跟踪 （未显示）。

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>请参阅

- [异常处理](index.md)
- [异常类型](exception-types.md)
- [异常：`try...with` 表达式](the-try-with-expression.md)
- [异常：`try...finally` 表达式](the-try-finally-expression.md)
- [异常：`raise` 函数](the-raise-function.md)
- [异常：`failwith` 函数](the-failwith-function.md)
