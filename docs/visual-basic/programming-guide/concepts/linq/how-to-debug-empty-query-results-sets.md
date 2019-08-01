---
title: 如何：调试空查询结果集 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: cc6a370545b9e4d8c28e0096f5cff73f4d937bd3
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710432"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="80d77-102">如何：调试空查询结果集 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80d77-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>

<span data-ttu-id="80d77-103">查询 XML 树时遇到的一个最常见问题是，如果 XML 树具有默认命名空间，开发人员在编写查询时，有时会将 XML 视为不在命名空间内。</span><span class="sxs-lookup"><span data-stu-id="80d77-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="80d77-104">本主题的第一个示例集演示一种加载并按不正确方式查询默认命名空间中的 XML 的典型方式。</span><span class="sxs-lookup"><span data-stu-id="80d77-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>

<span data-ttu-id="80d77-105">第二个示例集演示必需的更正，以便可以查询命名空间中的 XML。</span><span class="sxs-lookup"><span data-stu-id="80d77-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="80d77-106">有关详细信息, 请参阅[命名空间概述 (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="80d77-106">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>

## <a name="example"></a><span data-ttu-id="80d77-107">示例</span><span class="sxs-lookup"><span data-stu-id="80d77-107">Example</span></span>

<span data-ttu-id="80d77-108">此示例演示如何在命名空间中创建 XML 和一个返回空结果集的查询。</span><span class="sxs-lookup"><span data-stu-id="80d77-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

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

<span data-ttu-id="80d77-109">此示例产生下面的结果：</span><span class="sxs-lookup"><span data-stu-id="80d77-109">This example produces the following result:</span></span>

```
Result set follows:
End of result set
```

## <a name="example"></a><span data-ttu-id="80d77-110">示例</span><span class="sxs-lookup"><span data-stu-id="80d77-110">Example</span></span>

<span data-ttu-id="80d77-111">本示例演示如何在命名空间中创建 XML 和一个正确编码的查询。</span><span class="sxs-lookup"><span data-stu-id="80d77-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>

<span data-ttu-id="80d77-112">解决方法是声明和初始化一个全局默认命名空间。</span><span class="sxs-lookup"><span data-stu-id="80d77-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="80d77-113">这样会将所有 XML 属性放入该默认命名空间。</span><span class="sxs-lookup"><span data-stu-id="80d77-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="80d77-114">无需对该示例做任何其他修改，即可使它正常运行。</span><span class="sxs-lookup"><span data-stu-id="80d77-114">No other modifications are required to the example to make it work properly.</span></span>

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

<span data-ttu-id="80d77-115">此示例产生下面的结果：</span><span class="sxs-lookup"><span data-stu-id="80d77-115">This example produces the following result:</span></span>

```
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="80d77-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="80d77-116">See also</span></span>

- [<span data-ttu-id="80d77-117">基本查询 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80d77-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
