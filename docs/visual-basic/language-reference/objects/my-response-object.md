---
title: My.Response 对象 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 0e49a3b5732ee1a3626666ce06e366c4940eca05
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881966"
---
# <a name="myresponse-object"></a>My.Response 对象
获取<xref:System.Web.HttpResponse>对象与关联<xref:System.Web.UI.Page>。 使用此对象，可以将 HTTP 响应数据发送到客户端，并包含此响应的相关信息。  
  
## <a name="remarks"></a>备注  
 `My.Response`对象包含当前<xref:System.Web.HttpResponse>与页关联的对象。  
  
 `My.Response`对象功能仅适用于 ASP.NET 应用程序。  
  
## <a name="example"></a>示例  
 下面的示例获取的标头集合`My.Request`对象，并使用`My.Response`要写入到 ASP.NET 页面对象。  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Web.HttpResponse>
- [My.Request 对象](../../../visual-basic/language-reference/objects/my-request-object.md)
