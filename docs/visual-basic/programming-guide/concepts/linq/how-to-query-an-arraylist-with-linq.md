---
title: 如何：使用 LINQ 查询 ArrayList （Visual Basic）
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: 5b05fa2ed5c9b3b701571ef4760600caac7193d5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524148"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>如何：使用 LINQ 查询 ArrayList （Visual Basic）

如果使用 LINQ 来查询非泛型 <xref:System.Collections.IEnumerable> 集合（例如 <xref:System.Collections.ArrayList>），必须显式声明范围变量的类型，以反映集合中对象的特定类型。 例如，如果有 `Student` 对象的 <xref:System.Collections.ArrayList>，则[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)应如下所示：

```vb
Dim query = From student As Student In arrList
'...
```

通过指定范围变量的类型，可将 <xref:System.Collections.ArrayList> 中的每项强制转换为 `Student`。

在查询表达式中使用显式类型范围变量等效于调用 <xref:System.Linq.Enumerable.Cast%2A> 方法。 如果无法执行指定的强制转换，<xref:System.Linq.Enumerable.Cast%2A> 将引发异常。 <xref:System.Linq.Enumerable.Cast%2A> 和 <xref:System.Linq.Enumerable.OfType%2A> 是两个标准查询运算符方法，可对非泛型 <xref:System.Collections.IEnumerable> 类型执行操作。 在 Visual Basic 中，必须对数据源显式调用 <xref:System.Linq.Enumerable.Cast%2A> 方法以确保特定范围变量类型。 有关详细信息，请参阅[查询操作中的类型关系（Visual Basic）](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。

## <a name="example"></a>示例

下面的示例演示对 <xref:System.Collections.ArrayList> 的简单查询。 请注意，本示例在代码调用 <xref:System.Collections.ArrayList.Add%2A> 方法时使用对象初始值设定项，但这不是必需的。

```vb
Imports System.Collections
Imports System.Linq

Module Module1

    Public Class Student
        Public Property FirstName As String
        Public Property LastName As String
        Public Property Scores As Integer()
    End Class

    Sub Main()

        Dim student1 As New Student With {.FirstName = "Svetlana",
                                     .LastName = "Omelchenko",
                                     .Scores = New Integer() {98, 92, 81, 60}}
        Dim student2 As New Student With {.FirstName = "Claire",
                                    .LastName = "O'Donnell",
                                    .Scores = New Integer() {75, 84, 91, 39}}
        Dim student3 As New Student With {.FirstName = "Cesar",
                                    .LastName = "Garcia",
                                    .Scores = New Integer() {97, 89, 85, 82}}
        Dim student4 As New Student With {.FirstName = "Sven",
                                    .LastName = "Mortensen",
                                    .Scores = New Integer() {88, 94, 65, 91}}

        Dim arrList As New ArrayList()
        arrList.Add(student1)
        arrList.Add(student2)
        arrList.Add(student3)
        arrList.Add(student4)

        ' Use an explicit type for non-generic collections
        Dim query = From student As Student In arrList
                    Where student.Scores(0) > 95
                    Select student

        For Each student As Student In query
            Console.WriteLine(student.LastName & ": " & student.Scores(0))
        Next
        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Module
' Output:
'   Omelchenko: 98
'   Garcia: 97
```

## <a name="see-also"></a>请参阅

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
