---
title: 数据成员顺序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: d717673139ba810c1593e5c60e488537426f1f64
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754406"
---
# <a name="data-member-order"></a><span data-ttu-id="0493d-102">数据成员顺序</span><span class="sxs-lookup"><span data-stu-id="0493d-102">Data Member Order</span></span>
<span data-ttu-id="0493d-103">在一些应用程序中，有必要知道各个数据成员中数据的发送顺序或预期接收顺序（比如序列化 XML 中数据的显示顺序）。</span><span class="sxs-lookup"><span data-stu-id="0493d-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="0493d-104">有时，必须要更改此顺序。</span><span class="sxs-lookup"><span data-stu-id="0493d-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="0493d-105">本主题说明排序规则。</span><span class="sxs-lookup"><span data-stu-id="0493d-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="0493d-106">基本规则</span><span class="sxs-lookup"><span data-stu-id="0493d-106">Basic Rules</span></span>  
 <span data-ttu-id="0493d-107">数据排序的基本规则包括：</span><span class="sxs-lookup"><span data-stu-id="0493d-107">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="0493d-108">如果数据协定类型是继承层次结构的一部分，则其基类型的数据成员始终排在第一位。</span><span class="sxs-lookup"><span data-stu-id="0493d-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="0493d-109">排在下一位的是当前类型的数据成员（按字母顺序排列），这些成员未设置 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 属性 (attribute) 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性 (property)。</span><span class="sxs-lookup"><span data-stu-id="0493d-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="0493d-110">再下面是设置了 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 属性 (attribute) 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性 (property) 的任何数据成员。</span><span class="sxs-lookup"><span data-stu-id="0493d-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="0493d-111">这些成员首先按 `Order` 属性的值排序，如果多个成员具有特定的 `Order` 值，则按字母顺序排列。</span><span class="sxs-lookup"><span data-stu-id="0493d-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="0493d-112">可以跳过 Order 值。</span><span class="sxs-lookup"><span data-stu-id="0493d-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="0493d-113">字母顺序是通过调用 <xref:System.String.CompareOrdinal%2A> 方法确定的。</span><span class="sxs-lookup"><span data-stu-id="0493d-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0493d-114">示例</span><span class="sxs-lookup"><span data-stu-id="0493d-114">Examples</span></span>  
 <span data-ttu-id="0493d-115">考虑下列代码。</span><span class="sxs-lookup"><span data-stu-id="0493d-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="0493d-116">生成的 XML 类似于以下形式。</span><span class="sxs-lookup"><span data-stu-id="0493d-116">The XML produced is similar to the following.</span></span>  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>   
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>   
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>   
</DerivedType>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0493d-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="0493d-117">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="0493d-118">数据协定等效性</span><span class="sxs-lookup"><span data-stu-id="0493d-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="0493d-119">使用数据协定</span><span class="sxs-lookup"><span data-stu-id="0493d-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
