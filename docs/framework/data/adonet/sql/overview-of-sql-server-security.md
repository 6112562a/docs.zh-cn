---
title: SQL Server 安全性概述
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: de0c79a95a786f33b05c88ce4ed298837f2a6923
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148585"
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="2d1ac-102">SQL Server 安全性概述</span><span class="sxs-lookup"><span data-stu-id="2d1ac-102">Overview of SQL Server Security</span></span>
<span data-ttu-id="2d1ac-103">具有重叠安全层的全面防御策略是抵御安全威胁的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-103">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="2d1ac-104">SQL Server 提供的安全体系结构旨在允许数据库管理员和开发人员创建安全的数据库应用程序并抵御威胁。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-104">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="2d1ac-105">通过引入新功能，SQL Server 的每个版本都在先前的 SQL Server 版本基础上得到改善。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-105">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="2d1ac-106">但是，安全性并不是现成的。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-106">However, security does not ship in the box.</span></span> <span data-ttu-id="2d1ac-107">每个应用程序都具有其独特的安全要求。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-107">Each application is unique in its security requirements.</span></span> <span data-ttu-id="2d1ac-108">开发人员需要了解哪些功能组合最适合抵御已知的威胁，并需要预见未来可能出现的威胁。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-108">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="2d1ac-109">SQL Server 实例包含以服务器为首的实体的分层集合。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-109">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="2d1ac-110">每个服务器均包含多个数据库，而每个数据库均包含可保护对象的集合。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-110">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="2d1ac-111">每个 SQL 服务器安全对象相关联*权限*，可以授予*主体*，这是个人、 组或进程授予访问 SQL Server 权限。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-111">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="2d1ac-112">SQL Server 安全框架管理通过安全对象实体的访问权限*身份验证*并*授权*。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-112">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
-   <span data-ttu-id="2d1ac-113">身份验证是指通过提交服务器评估的凭据以登录到主体请求访问的 SQL Server 的过程。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-113">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="2d1ac-114">身份验证可以确定接受身份验证的用户或进程的标识。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-114">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
-   <span data-ttu-id="2d1ac-115">授权是指确定主体可以访问哪些可保护资源以及允许对这些资源执行哪些操作的过程。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-115">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="2d1ac-116">本节中的主题介绍 SQL Server 安全基础知识，并提供到相关版本 SQL Server 联机丛书中完整文档的链接。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-116">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d1ac-117">本节内容</span><span class="sxs-lookup"><span data-stu-id="2d1ac-117">In This Section</span></span>  
 [<span data-ttu-id="2d1ac-118">SQL Server 中的身份验证</span><span class="sxs-lookup"><span data-stu-id="2d1ac-118">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 <span data-ttu-id="2d1ac-119">说明 SQL Server 中的登录名和身份验证并提供到其他资源的链接。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-119">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="2d1ac-120">SQL Server 中的服务器和数据库角色</span><span class="sxs-lookup"><span data-stu-id="2d1ac-120">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="2d1ac-121">说明固定服务器和数据库角色、自定义数据库角色和内置帐户，并提供到其他资源的链接。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-121">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="2d1ac-122">SQL Server 中的所有权和用户架构分离</span><span class="sxs-lookup"><span data-stu-id="2d1ac-122">Ownership and User-Schema Separation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="2d1ac-123">说明对象所属权和用户架构分离，并提供到其他资源的链接。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-123">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="2d1ac-124">SQL Server 中的授权和权限</span><span class="sxs-lookup"><span data-stu-id="2d1ac-124">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="2d1ac-125">说明使用最低特权原则授予权限并提供到其他资源的链接。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-125">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="2d1ac-126">SQL Server 中的数据加密</span><span class="sxs-lookup"><span data-stu-id="2d1ac-126">Data Encryption in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 <span data-ttu-id="2d1ac-127">说明 SQL Server 中的数据加密选项并提供到其他资源的链接。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-127">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="2d1ac-128">SQL Server 中的 CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="2d1ac-128">CLR Integration Security in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="2d1ac-129">提供到 CLR 集成安全资源的链接。</span><span class="sxs-lookup"><span data-stu-id="2d1ac-129">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1ac-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="2d1ac-130">See also</span></span>

- [<span data-ttu-id="2d1ac-131">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="2d1ac-131">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="2d1ac-132">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="2d1ac-132">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [<span data-ttu-id="2d1ac-133">SQL Server 中的应用程序安全性方案</span><span class="sxs-lookup"><span data-stu-id="2d1ac-133">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="2d1ac-134">ADO.NET 托管提供程序和 DataSet 开发人员中心</span><span class="sxs-lookup"><span data-stu-id="2d1ac-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
