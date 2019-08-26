---
title: 如何：向文件对话框添加自定义区域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 824c948fafd0a0995ad261389414d2d79918c8a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916339"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>如何：向文件对话框添加自定义区域
[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] 上的默认打开和保存对话框在名为“收藏夹链接”的对话框左侧有一个区域。 此区域称为自定义区域。 和类允许将文件夹添加到<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>集合中。 <xref:System.Windows.Forms.SaveFileDialog> <xref:System.Windows.Forms.OpenFileDialog>  
  
> [!NOTE]
> 若要使自定义位置显示<xref:System.Windows.Forms.OpenFileDialog>在或<xref:System.Windows.Forms.SaveFileDialog>中, 则<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>属性必须设置为`true` (默认值)。  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>向文件对话框添加自定义区域  
  
- 将路径、已知文件夹 GUID 或<xref:System.Windows.Forms.FileDialogCustomPlace>对象添加<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>到对话框的集合中。  
  
     以下代码示例演示了如何添加路径：  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [文件对话框自定义区域的已知文件夹 GUID](known-folder-guids-for-file-dialog-custom-places.md)
