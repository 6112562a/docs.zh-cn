---
ms.openlocfilehash: e36dac19beb6251debef100656670a6623344eea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237854"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a><span data-ttu-id="1881f-101">与解析为 `localhost` 的 SQL Server 数据库的 TCP/IP 连接尝试失败</span><span class="sxs-lookup"><span data-stu-id="1881f-101">Attempting a TCP/IP connection to a SQL Server database that resolves to `localhost` fails</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1881f-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1881f-102">Details</span></span>|<span data-ttu-id="1881f-103">在 .NET Framework 4.6 和 4.6.1 中，与解析为 <code>localhost</code> 的 SQL Server 数据库的 TCP/IP 连接尝试失败，出现错误：“在与 SQL Server 建立连接时出现与网络相关的错误或特定于实例的错误。</span><span class="sxs-lookup"><span data-stu-id="1881f-103">In the .NET Framework 4.6 and 4.6.1, attempting a TCP/IP connection to a SQL Server database that resolves to <code>localhost</code> fails with the error, &quot;A network-related or instance-specific error occurred while establishing a connection to SQL Server.</span></span> <span data-ttu-id="1881f-104">找不到或无法访问服务器。</span><span class="sxs-lookup"><span data-stu-id="1881f-104">The server was not found or was not accessible.</span></span> <span data-ttu-id="1881f-105">请验证实例名称是否正确，SQL Server 是否已配置为允许远程连接。</span><span class="sxs-lookup"><span data-stu-id="1881f-105">Verify that the instance name is correct and that SQL Server is configured to allow remote connections.</span></span> <span data-ttu-id="1881f-106">（提供程序：SQL 网络接口，错误：26 - 定位指定的服务器/实例时出错）”</span><span class="sxs-lookup"><span data-stu-id="1881f-106">(provider: SQL Network Interfaces, error: 26 - Error Locating Server/Instance Specified)&quot;</span></span>|
|<span data-ttu-id="1881f-107">建议</span><span class="sxs-lookup"><span data-stu-id="1881f-107">Suggestion</span></span>|<span data-ttu-id="1881f-108">在 .NET Framework 4.6.2 中，此问题已得到解决，并已恢复以前的行为。</span><span class="sxs-lookup"><span data-stu-id="1881f-108">This issue has been addressed and the previous behavior restored in the .NET Framework 4.6.2.</span></span> <span data-ttu-id="1881f-109">若要连接到会解析为 <code>localhost</code> 的 SQL Server 数据库，请升级到 .NET Framework 4.6.2。</span><span class="sxs-lookup"><span data-stu-id="1881f-109">To connect to a SQL Server databsae that resolves to <code>localhost</code>, upgrade to the .NET Framework 4.6.2.</span></span>|
|<span data-ttu-id="1881f-110">范围</span><span class="sxs-lookup"><span data-stu-id="1881f-110">Scope</span></span>|<span data-ttu-id="1881f-111">次要</span><span class="sxs-lookup"><span data-stu-id="1881f-111">Minor</span></span>|
|<span data-ttu-id="1881f-112">Version</span><span class="sxs-lookup"><span data-stu-id="1881f-112">Version</span></span>|<span data-ttu-id="1881f-113">4.6</span><span class="sxs-lookup"><span data-stu-id="1881f-113">4.6</span></span>|
|<span data-ttu-id="1881f-114">类型</span><span class="sxs-lookup"><span data-stu-id="1881f-114">Type</span></span>|<span data-ttu-id="1881f-115">运行时</span><span class="sxs-lookup"><span data-stu-id="1881f-115">Runtime</span></span>|
