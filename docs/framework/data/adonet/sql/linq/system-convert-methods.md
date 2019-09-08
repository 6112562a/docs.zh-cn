---
title: System.Convert 方法
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: d0aa0b11223e23b874471962d727d8e16e152ceb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781057"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="4c84e-102">System.Convert 方法</span><span class="sxs-lookup"><span data-stu-id="4c84e-102">System.Convert Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="4c84e-103">不支持以下 <xref:System.Convert> 方法。</span><span class="sxs-lookup"><span data-stu-id="4c84e-103">does not support the following <xref:System.Convert> methods.</span></span>

- <span data-ttu-id="4c84e-104">带有 <xref:System.IFormatProvider> 参数的版本。</span><span class="sxs-lookup"><span data-stu-id="4c84e-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>

- <span data-ttu-id="4c84e-105">涉及字符数组或字节数组的方法：</span><span class="sxs-lookup"><span data-stu-id="4c84e-105">Methods that involve char arrays or byte arrays:</span></span>

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- <span data-ttu-id="4c84e-106">以下方法：</span><span class="sxs-lookup"><span data-stu-id="4c84e-106">The following methods:</span></span>

  - <span data-ttu-id="4c84e-107">`public static <Type2> To<Type2>(<Type1> value);`，其中</span><span class="sxs-lookup"><span data-stu-id="4c84e-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>

    <span data-ttu-id="4c84e-108">`Type1` 和 `Type2` 各自是 `sbyte`、`uint`、`ulong` 或 `ushort` 之一。</span><span class="sxs-lookup"><span data-stu-id="4c84e-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>

  - <span data-ttu-id="4c84e-109">C#：</span><span class="sxs-lookup"><span data-stu-id="4c84e-109">C#:</span></span>

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - <span data-ttu-id="4c84e-110">Visual Basic：</span><span class="sxs-lookup"><span data-stu-id="4c84e-110">Visual Basic:</span></span>

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a><span data-ttu-id="4c84e-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="4c84e-111">See also</span></span>

- [<span data-ttu-id="4c84e-112">数据类型和函数</span><span class="sxs-lookup"><span data-stu-id="4c84e-112">Data Types and Functions</span></span>](data-types-and-functions.md)
