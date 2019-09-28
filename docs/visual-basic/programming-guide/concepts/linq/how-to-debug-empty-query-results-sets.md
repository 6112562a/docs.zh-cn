---
title: 如何：调试空查询结果集（Visual Basic）
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 6fc194432b1d44c1214da32d2c6978a4eeb316dc
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351775"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a>如何：调试空查询结果集（Visual Basic）

查询 XML 树时遇到的一个最常见问题是，如果 XML 树具有默认命名空间，开发人员在编写查询时，有时会将 XML 视为不在命名空间内。

本主题的第一个示例集演示一种加载并按不正确方式查询默认命名空间中的 XML 的典型方式。

第二个示例集演示必需的更正，以便可以查询命名空间中的 XML。

有关详细信息，请参阅[命名空间概述（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。

## <a name="example"></a>示例

此示例演示如何在命名空间中创建 XML 和一个返回空结果集的查询。

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
        <Child>1</Child>
        <Child>2</Child>
        <Child>3</Child>
        <AnotherChild>4</AnotherChild>
        <AnotherChild>5</AnotherChild>
        <AnotherChild>6</AnotherChild>
    </Root>
Dim c1 As IEnumerable(Of XElement) = _
        From el In root.<Child> _
        Select el
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

此示例产生下面的结果：

```console
Result set follows:
End of result set
```

## <a name="example"></a>示例

本示例演示如何在命名空间中创建 XML 和一个正确编码的查询。

解决方法是声明和初始化一个全局默认命名空间。 这样会将所有 XML 属性放入该默认命名空间。 无需对该示例做任何其他修改，即可使它正常运行。

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

此示例产生下面的结果：

```console
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a>请参阅

- [基本查询（LINQ to XML）（Visual Basic）](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
