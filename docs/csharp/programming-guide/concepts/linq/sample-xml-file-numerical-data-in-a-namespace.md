---
title: 示例 XML 文件：命名空间 3 中的数值数据
ms.date: 07/20/2015
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
ms.openlocfilehash: 02788b73a7af9922b5a50237f2d2e401cba8abe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "66483699"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="89b52-102">示例 XML 文件：命名空间中的数值数据</span><span class="sxs-lookup"><span data-stu-id="89b52-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="89b52-103">下面的 XML 文件用在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 文档的很多示例中。</span><span class="sxs-lookup"><span data-stu-id="89b52-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="89b52-104">此文件包含数值数据，用于求和、求平均值和分组。</span><span class="sxs-lookup"><span data-stu-id="89b52-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="89b52-105">该 XML 在某个命名空间中。</span><span class="sxs-lookup"><span data-stu-id="89b52-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="89b52-106">data</span><span class="sxs-lookup"><span data-stu-id="89b52-106">Data</span></span>  
  
```xml  
<Root xmlns='http://www.adatum.com'>  
  <TaxRate>7.25</TaxRate>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>24.50</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>1</Quantity>  
    <Price>89.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>5</Quantity>  
    <Price>4.95</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>66.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>10</Quantity>  
    <Price>.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>15</Quantity>  
    <Price>29.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>8</Quantity>  
    <Price>6.99</Price>  
  </Data>  
</Root>  
```  
