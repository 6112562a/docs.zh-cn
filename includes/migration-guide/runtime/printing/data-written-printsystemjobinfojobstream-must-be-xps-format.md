---
ms.openlocfilehash: 74f00821f2304664729faa8de2f0163c6611f513
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803313"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a><span data-ttu-id="ed62a-101">写入到 PrintSystemJobInfo.JobStream 的数据必须采用 XPS 格式</span><span class="sxs-lookup"><span data-stu-id="ed62a-101">Data written to PrintSystemJobInfo.JobStream must be in XPS format</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ed62a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ed62a-102">Details</span></span>|<span data-ttu-id="ed62a-103"><xref:System.Printing.PrintSystemJobInfo.JobStream> 属性公开打印作业的流。</span><span class="sxs-lookup"><span data-stu-id="ed62a-103">The <xref:System.Printing.PrintSystemJobInfo.JobStream> property exposes the stream of a print job.</span></span> <span data-ttu-id="ed62a-104">通过写入到此流，用户可以将原始数据发送到基础操作系统打印组件。从 Windows 操作系统的 Windows 8 和更高版本上的 .NET Framework 4.5 起，写入到此流的数据必须采用作为包流的 XPS 格式。</span><span class="sxs-lookup"><span data-stu-id="ed62a-104">The user can send raw data to the underlying operating system printing components by writing to this stream.Starting with the .NET Framework 4.5 on Windows 8 and later versions of the Windows operating system, data written to this stream must be in XPS format as a package stream.</span></span>|
|<span data-ttu-id="ed62a-105">建议</span><span class="sxs-lookup"><span data-stu-id="ed62a-105">Suggestion</span></span>|<span data-ttu-id="ed62a-106">若要输出打印内容，可以执行下列任一操作：</span><span class="sxs-lookup"><span data-stu-id="ed62a-106">To output print content, you can do either of the following:</span></span><ul><li><span data-ttu-id="ed62a-107">使用 <xref:System.Windows.Xps.XpsDocumentWriter> 类输出打印内容。</span><span class="sxs-lookup"><span data-stu-id="ed62a-107">Use the <xref:System.Windows.Xps.XpsDocumentWriter> class to output print content.</span></span> <span data-ttu-id="ed62a-108">这是建议的替代项。</span><span class="sxs-lookup"><span data-stu-id="ed62a-108">This is the recommended alternative.</span></span></li><li><span data-ttu-id="ed62a-109">确保发送给 <xref:System.Printing.PrintSystemJobInfo.JobStream> 属性返回的流的数据作为包流采用 XPS 格式。</span><span class="sxs-lookup"><span data-stu-id="ed62a-109">Ensure that the data sent to the stream returned by the <xref:System.Printing.PrintSystemJobInfo.JobStream> property is in XPS format as a package stream.</span></span></li></ul>|
|<span data-ttu-id="ed62a-110">范围</span><span class="sxs-lookup"><span data-stu-id="ed62a-110">Scope</span></span>|<span data-ttu-id="ed62a-111">次要</span><span class="sxs-lookup"><span data-stu-id="ed62a-111">Minor</span></span>|
|<span data-ttu-id="ed62a-112">版本</span><span class="sxs-lookup"><span data-stu-id="ed62a-112">Version</span></span>|<span data-ttu-id="ed62a-113">4.5</span><span class="sxs-lookup"><span data-stu-id="ed62a-113">4.5</span></span>|
|<span data-ttu-id="ed62a-114">类型</span><span class="sxs-lookup"><span data-stu-id="ed62a-114">Type</span></span>|<span data-ttu-id="ed62a-115">运行时</span><span class="sxs-lookup"><span data-stu-id="ed62a-115">Runtime</span></span>|
|<span data-ttu-id="ed62a-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="ed62a-116">Affected APIs</span></span>|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
