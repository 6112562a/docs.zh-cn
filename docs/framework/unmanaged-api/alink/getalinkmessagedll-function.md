---
title: GetALinkMessageDll 函数
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 41e79a4c9587e3e738039cbf6a84087a2e7fc9b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741953"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="0d96f-102">GetALinkMessageDll 函数</span><span class="sxs-lookup"><span data-stu-id="0d96f-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="0d96f-103">查找并加载 DLL 的消息。</span><span class="sxs-lookup"><span data-stu-id="0d96f-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="0d96f-104">如果无法找到或加载 DLL 的消息，则返回 0。</span><span class="sxs-lookup"><span data-stu-id="0d96f-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="0d96f-105">消息 DLL 应在其名称是一个语言 ID、 一个子目录或当前目录中。</span><span class="sxs-lookup"><span data-stu-id="0d96f-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d96f-106">语法</span><span class="sxs-lookup"><span data-stu-id="0d96f-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="0d96f-107">要求</span><span class="sxs-lookup"><span data-stu-id="0d96f-107">Requirements</span></span>  
 <span data-ttu-id="0d96f-108">**标头：** alink.h</span><span class="sxs-lookup"><span data-stu-id="0d96f-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="0d96f-109">**库**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="0d96f-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d96f-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="0d96f-110">See also</span></span>

- [<span data-ttu-id="0d96f-111">Al.exe（程序集链接器）</span><span class="sxs-lookup"><span data-stu-id="0d96f-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
