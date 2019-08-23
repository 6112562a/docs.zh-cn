---
title: SQL Server 中的所有权和用户架构分离
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: 520772acc5edd812f64c61cc7fdda9db3441c87c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961085"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a><span data-ttu-id="451be-102">SQL Server 中的所有权和用户架构分离</span><span class="sxs-lookup"><span data-stu-id="451be-102">Ownership and User-Schema Separation in SQL Server</span></span>
<span data-ttu-id="451be-103">SQL Server 安全性的核心概念是对象的所有者具有管理这些对象的不可撤消的权限。</span><span class="sxs-lookup"><span data-stu-id="451be-103">A core concept of SQL Server security is that owners of objects have irrevocable permissions to administer them.</span></span> <span data-ttu-id="451be-104">您不能取消对象所有者的特权，并且如果用户在数据库中拥有对象，您也不能将用户从数据库中删除。</span><span class="sxs-lookup"><span data-stu-id="451be-104">You cannot remove privileges from an object owner, and you cannot drop users from a database if they own objects in it.</span></span>  
  
## <a name="user-schema-separation"></a><span data-ttu-id="451be-105">用户架构分离</span><span class="sxs-lookup"><span data-stu-id="451be-105">User-Schema Separation</span></span>  
 <span data-ttu-id="451be-106">通过用户架构分离，可实现管理数据库对象权限的更大灵活性。</span><span class="sxs-lookup"><span data-stu-id="451be-106">User-schema separation allows for more flexibility in managing database object permissions.</span></span> <span data-ttu-id="451be-107">*架构*是数据库对象的命名容器, 使你能够将对象分组到不同的命名空间中。</span><span class="sxs-lookup"><span data-stu-id="451be-107">A *schema* is a named container for database objects, which allows you to group objects into separate namespaces.</span></span> <span data-ttu-id="451be-108">例如，AdventureWorks 示例数据库包含 Production、Sales 和 HumanResources 的架构。</span><span class="sxs-lookup"><span data-stu-id="451be-108">For example, the AdventureWorks sample database contains schemas for Production, Sales, and HumanResources.</span></span>  
  
 <span data-ttu-id="451be-109">用于引用对象的由四部分组成的命名语法指定架构名称。</span><span class="sxs-lookup"><span data-stu-id="451be-109">The four-part naming syntax for referring to objects specifies the schema name.</span></span>  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a><span data-ttu-id="451be-110">架构所有者和权限</span><span class="sxs-lookup"><span data-stu-id="451be-110">Schema Owners and Permissions</span></span>  
 <span data-ttu-id="451be-111">任何数据库主体都可以拥有架构，并且一个主体可拥有多个架构。</span><span class="sxs-lookup"><span data-stu-id="451be-111">Schemas can be owned by any database principal, and a single principal can own multiple schemas.</span></span> <span data-ttu-id="451be-112">您可以对架构应用安全规则，安全规则将由架构中的所有对象继承。</span><span class="sxs-lookup"><span data-stu-id="451be-112">You can apply security rules to a schema, which are inherited by all objects in the schema.</span></span> <span data-ttu-id="451be-113">如果设置了对架构的访问权限，则当新对象添加到架构时，新对象会自动应用这些权限。</span><span class="sxs-lookup"><span data-stu-id="451be-113">Once you set up access permissions for a schema, those permissions are automatically applied as new objects are added to the schema.</span></span> <span data-ttu-id="451be-114">可以为用户分配一个默认的架构，且多个数据库用户可以共享同一架构。</span><span class="sxs-lookup"><span data-stu-id="451be-114">Users can be assigned a default schema, and multiple database users can share the same schema.</span></span>  
  
 <span data-ttu-id="451be-115">默认情况下，当开发人员在架构中创建对象时，该对象由拥有架构的安全主体而不是开发人员拥有。</span><span class="sxs-lookup"><span data-stu-id="451be-115">By default, when developers create objects in a schema, the objects are owned by the security principal that owns the schema, not the developer.</span></span> <span data-ttu-id="451be-116">可以使用 ALTER AUTHORIZATION Transact-SQL 语句转移对象所有权。</span><span class="sxs-lookup"><span data-stu-id="451be-116">Object ownership can be transferred with ALTER AUTHORIZATION Transact-SQL statement.</span></span> <span data-ttu-id="451be-117">虽因架构会增大管理权限的复杂度而不建议使用，但架构仍然可以包含由不同用户拥有的对象并可具有比分配给架构的权限更加细化的权限。</span><span class="sxs-lookup"><span data-stu-id="451be-117">A schema can also contain objects that are owned by different users and have more granular permissions than those assigned to the schema, although this is not recommended because it adds complexity to managing permissions.</span></span> <span data-ttu-id="451be-118">对象可以在架构之间移动，架构所有权也可以在主体之间转移。</span><span class="sxs-lookup"><span data-stu-id="451be-118">Objects can be moved between schemas, and schema ownership can be transferred between principals.</span></span> <span data-ttu-id="451be-119">可以在不影响架构的情况下删除数据库用户。</span><span class="sxs-lookup"><span data-stu-id="451be-119">Database users can be dropped without affecting schemas.</span></span>  
  
### <a name="built-in-schemas"></a><span data-ttu-id="451be-120">内置架构</span><span class="sxs-lookup"><span data-stu-id="451be-120">Built-In Schemas</span></span>  
 <span data-ttu-id="451be-121">SQL Server 随附了十个预定义的架构，它们与内置数据库用户和角色具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="451be-121">SQL Server ships with ten pre-defined schemas that have the same names as the built-in database users and roles.</span></span> <span data-ttu-id="451be-122">这些架构主要用于向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="451be-122">These exist mainly for backward compatibility.</span></span> <span data-ttu-id="451be-123">如果您不需要与固定数据库角色具有相同名称的架构，则可以删除它们。</span><span class="sxs-lookup"><span data-stu-id="451be-123">You can drop the schemas that have the same names as the fixed database roles if you do not need them.</span></span> <span data-ttu-id="451be-124">您不能删除下列架构：</span><span class="sxs-lookup"><span data-stu-id="451be-124">You cannot drop the following schemas:</span></span>  
  
- `dbo`  
  
- `guest`  
  
- `sys`  
  
- `INFORMATION_SCHEMA`  
  
 <span data-ttu-id="451be-125">如果从模型数据库中删除这些架构，它们将不会显示在新数据库中。</span><span class="sxs-lookup"><span data-stu-id="451be-125">If you drop them from the model database, they will not appear in new databases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="451be-126">`sys` 和 `INFORMATION_SCHEMA` 架构是为系统对象而保留的。</span><span class="sxs-lookup"><span data-stu-id="451be-126">The `sys` and `INFORMATION_SCHEMA` schemas are reserved for system objects.</span></span> <span data-ttu-id="451be-127">您不能在这些架构中创建对象，而且不能删除它们。</span><span class="sxs-lookup"><span data-stu-id="451be-127">You cannot create objects in these schemas and you cannot drop them.</span></span>  
  
#### <a name="the-dbo-schema"></a><span data-ttu-id="451be-128">dbo 架构</span><span class="sxs-lookup"><span data-stu-id="451be-128">The dbo Schema</span></span>  
 <span data-ttu-id="451be-129">`dbo` 是新创建的数据库的默认架构。</span><span class="sxs-lookup"><span data-stu-id="451be-129">The `dbo` schema is the default schema for a newly created database.</span></span> <span data-ttu-id="451be-130">`dbo` 架构由 `dbo` 用户帐户拥有。</span><span class="sxs-lookup"><span data-stu-id="451be-130">The `dbo` schema is owned by the `dbo` user account.</span></span> <span data-ttu-id="451be-131">默认情况下，使用 CREATE USER Transact-SQL 命令创建的用户的默认架构为 `dbo`。</span><span class="sxs-lookup"><span data-stu-id="451be-131">By default, users created with the CREATE USER Transact-SQL command have `dbo` as their default schema.</span></span>  
  
 <span data-ttu-id="451be-132">分配了 `dbo` 架构的用户不继承 `dbo` 用户帐户的权限。</span><span class="sxs-lookup"><span data-stu-id="451be-132">Users who are assigned the `dbo` schema do not inherit the permissions of the `dbo` user account.</span></span> <span data-ttu-id="451be-133">用户不从架构继承权限；架构权限由架构中包含的数据库对象继承。</span><span class="sxs-lookup"><span data-stu-id="451be-133">No permissions are inherited from a schema by users; schema permissions are inherited by the database objects contained in the schema.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="451be-134">当使用部分名称来引用数据库对象时，SQL Server 首先在用户的默认架构中查找。</span><span class="sxs-lookup"><span data-stu-id="451be-134">When database objects are referenced by using a one-part name, SQL Server first looks in the user's default schema.</span></span> <span data-ttu-id="451be-135">如果在此处未找到该对象，则 SQL Server 其次将在 `dbo` 架构中查找。</span><span class="sxs-lookup"><span data-stu-id="451be-135">If the object is not found there, SQL Server looks next in the `dbo` schema.</span></span> <span data-ttu-id="451be-136">如果对象不在 `dbo` 架构中，则会返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="451be-136">If the object is not in the `dbo` schema, an error is returned.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="451be-137">外部资源</span><span class="sxs-lookup"><span data-stu-id="451be-137">External Resources</span></span>  
 <span data-ttu-id="451be-138">有关对象所有权和架构的更多信息，请参见下列资源。</span><span class="sxs-lookup"><span data-stu-id="451be-138">For more information on object ownership and schemas, see the following resources.</span></span>  
  
|<span data-ttu-id="451be-139">资源</span><span class="sxs-lookup"><span data-stu-id="451be-139">Resource</span></span>|<span data-ttu-id="451be-140">描述</span><span class="sxs-lookup"><span data-stu-id="451be-140">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="451be-141">[用户架构分离](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="451be-141">[User-Schema Separation](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span></span>|<span data-ttu-id="451be-142">描述用户架构分离引发的变化，</span><span class="sxs-lookup"><span data-stu-id="451be-142">Describes the changes introduced by user-schema separation.</span></span> <span data-ttu-id="451be-143">包括新行为及其对所有权、目录视图和权限的影响。</span><span class="sxs-lookup"><span data-stu-id="451be-143">Includes new behavior, its impact on ownership, catalog views, and permissions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="451be-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="451be-144">See also</span></span>

- [<span data-ttu-id="451be-145">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="451be-145">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="451be-146">SQL Server 中的应用程序安全性方案</span><span class="sxs-lookup"><span data-stu-id="451be-146">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="451be-147">SQL Server 中的身份验证</span><span class="sxs-lookup"><span data-stu-id="451be-147">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [<span data-ttu-id="451be-148">SQL Server 中的服务器和数据库角色</span><span class="sxs-lookup"><span data-stu-id="451be-148">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)
- [<span data-ttu-id="451be-149">SQL Server 中的授权和权限</span><span class="sxs-lookup"><span data-stu-id="451be-149">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [<span data-ttu-id="451be-150">ADO.NET 托管提供程序和数据集开发人员中心</span><span class="sxs-lookup"><span data-stu-id="451be-150">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
