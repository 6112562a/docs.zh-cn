---
title: 如何：在 Visual Basic 上传文件
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 0d0aaca06a72b9bd2631a652a0b4756f4681df7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704402"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>如何：在 Visual Basic 上传文件
可使用 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> 方法上传文件并将文件存储到远程位置。 如果 `ShowUI` 参数设置为 `True`，则显示一个对话框，该对话框显示上传进度并允许用户取消该操作。  
  
### <a name="to-upload-a-file"></a>上传文件  
  
-   可以使用 `UploadFile` 方法上传文件，同时将源文件的位置和目标目录位置指定为字符串或 URI（统一资源标识符）。此示例将文件 `Order.txt` 上传到 `http://www.cohowinery.com/uploads.aspx`。  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>上传文件并显示操作进度  
  
-   可以使用 `UploadFile` 方法上传文件，同时将源文件的位置和目标目录位置指定为字符串或 URI。 此示例在不提供用户名或密码的情况下将文件 `Order.txt` 上传到 `http://www.cohowinery.com/uploads.aspx`显示了上传操作的进度，并将将超时间隔为 500 毫秒。  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>上传文件并提供用户名和密码  
  
-   可以使用 `UploadFile` 方法上传文件，同时将源文件的位置和目标目录位置指定为字符串或 URI，并指定用户名和密码。 此示例将文件 `Order.txt` 上传到 `http://www.cohowinery.com/uploads.aspx`，并提供了用户名 `anonymous` 和空白密码。  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]  
  
## <a name="robust-programming"></a>可靠编程  
 以下情况可能会引发异常：  
  
-   本地文件路径无效 (<xref:System.ArgumentException>)。  
  
-   身份验证失败 (<xref:System.Security.SecurityException>)。  
  
-   连接超时 (<xref:System.TimeoutException>)。  
  
## <a name="see-also"></a>请参阅
- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [如何：下载文件](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [如何：分析文件路径](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
