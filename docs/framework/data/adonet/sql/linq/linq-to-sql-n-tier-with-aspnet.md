---
title: 具有 ASP.NET 的 LINQ to SQL N 层
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1770d84053b57e05d1a4e41919a3eb4122dc73a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793034"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>具有 ASP.NET 的 LINQ to SQL N 层
在使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]的 ASP.NET 应用程序中，你<xref:System.Web.UI.WebControls.LinqDataSource>将使用 Web 服务器控件。 此控件处理查询 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]时必须使用的大部分逻辑，将数据传递到浏览器，检索数据，并将数据提交给 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> ，然后由其更新数据库。 只需要在标记中配置该控件，然后由该控件处理 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 和浏览器之间的所有数据传输。 由于该控件处理与表示层之间的交互，并[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]处理与数据层之间的通信，因此，ASP.NET 多层应用程序中的主要焦点是编写自定义业务逻辑。  
  
 有关的详细信息`LINQDataSource`，请参阅[LinqDataSource Web 服务器控件概述](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))。  
  
## <a name="see-also"></a>请参阅

- [使用 LINQ to SQL 的 N 层和远程应用程序](n-tier-and-remote-applications-with-linq-to-sql.md)
