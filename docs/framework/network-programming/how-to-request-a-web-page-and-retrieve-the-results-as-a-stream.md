---
title: 如何：请求网页并以数据流的形式检索结果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: b3d24a958ec93084d03d2ad2e0eb6d9d2507e155
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048180"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="f007d-102">如何：请求网页并以数据流的形式检索结果</span><span class="sxs-lookup"><span data-stu-id="f007d-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="f007d-103">此示例演示如何请求 Web 页并在流中检索结果。</span><span class="sxs-lookup"><span data-stu-id="f007d-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f007d-104">示例</span><span class="sxs-lookup"><span data-stu-id="f007d-104">Example</span></span>  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f007d-105">编译代码</span><span class="sxs-lookup"><span data-stu-id="f007d-105">Compiling the Code</span></span>  
 <span data-ttu-id="f007d-106">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="f007d-106">This example requires:</span></span>  
  
- <span data-ttu-id="f007d-107">对 <xref:System.IO> 和 <xref:System.Net> 命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="f007d-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f007d-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="f007d-108">See also</span></span>

- [<span data-ttu-id="f007d-109">请求数据</span><span class="sxs-lookup"><span data-stu-id="f007d-109">Requesting Data</span></span>](requesting-data.md)
