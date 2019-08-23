---
title: 查询投影（WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
ms.openlocfilehash: 44e99db2d75fcd8e84f91f0afc8da54ff6c3f707
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931171"
---
# <a name="query-projections-wcf-data-services"></a><span data-ttu-id="71bed-102">查询投影（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="71bed-102">Query Projections (WCF Data Services)</span></span>

<span data-ttu-id="71bed-103">投影在中[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]提供了一种机制, 可通过指定仅在响应中返回实体的某些属性来减少查询返回的源中的数据量。</span><span class="sxs-lookup"><span data-stu-id="71bed-103">Projection provides a mechanism in the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to reduce the amount of data in the feed returned by a query by specifying that only certain properties of an entity are returned in the response.</span></span> <span data-ttu-id="71bed-104">有关详细信息, 请[参阅 OData:选择系统查询选项 ($select)](https://go.microsoft.com/fwlink/?LinkId=186076)。</span><span class="sxs-lookup"><span data-stu-id="71bed-104">For more information, see [OData: Select System Query Option ($select)](https://go.microsoft.com/fwlink/?LinkId=186076).</span></span>

<span data-ttu-id="71bed-105">本主题介绍如何定义查询投影、实体和非实体类型的需求、对投影的结果进行更新、创建投影的类型，还列出一些投影的注意事项。</span><span class="sxs-lookup"><span data-stu-id="71bed-105">This topic describes how to define a query projection, what the requirements are for entity and non-entity types, making updates to projected results, creating projected types, and lists some projection considerations.</span></span>

## <a name="defining-a-query-projection"></a><span data-ttu-id="71bed-106">定义查询投影</span><span class="sxs-lookup"><span data-stu-id="71bed-106">Defining a Query Projection</span></span>

<span data-ttu-id="71bed-107">您可以通过使用 URI 中的`$select`查询选项或在 LINQ 查询中使用[select](../../../csharp/language-reference/keywords/select-clause.md)子句 (在 Visual Basic 中[选择](../../../visual-basic/language-reference/queries/select-clause.md)), 将投影子句添加到查询中。</span><span class="sxs-lookup"><span data-stu-id="71bed-107">You can add a projection clause to a query either by using the `$select` query option in a URI or by using the [select](../../../csharp/language-reference/keywords/select-clause.md) clause ([Select](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) in a LINQ query.</span></span> <span data-ttu-id="71bed-108">可以将返回的实体数据投影到客户端上的实体类型或非实体类型。</span><span class="sxs-lookup"><span data-stu-id="71bed-108">Returned entity data can be projected into either entity types or non-entity types on the client.</span></span> <span data-ttu-id="71bed-109">本主题中的示例演示如何在 LINQ 查询中使用 `select` 子句。</span><span class="sxs-lookup"><span data-stu-id="71bed-109">Examples in this topic demonstrate how to use the `select` clause in a LINQ query.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71bed-110">保存对投影的类型所进行的更新时，数据服务中可能会发生数据丢失。</span><span class="sxs-lookup"><span data-stu-id="71bed-110">Data loss might occur in the data service when you save updates that were made to projected types.</span></span> <span data-ttu-id="71bed-111">有关详细信息, 请参阅[投影注意事项](#considerations)。</span><span class="sxs-lookup"><span data-stu-id="71bed-111">For more information, see [Projection Considerations](#considerations).</span></span>

## <a name="requirements-for-entity-and-non-entity-types"></a><span data-ttu-id="71bed-112">实体类型和非实体类型的需求</span><span class="sxs-lookup"><span data-stu-id="71bed-112">Requirements for Entity and Non-Entity Types</span></span>

<span data-ttu-id="71bed-113">实体类型必须拥有组成实体键的一个或多个标识属性。</span><span class="sxs-lookup"><span data-stu-id="71bed-113">Entity types must have one or more identity properties that make up the entity key.</span></span> <span data-ttu-id="71bed-114">在客户端上采用以下方式之一定义实体类型：</span><span class="sxs-lookup"><span data-stu-id="71bed-114">Entity types are defined on clients in one of the following ways:</span></span>

- <span data-ttu-id="71bed-115">将 <xref:System.Data.Services.Common.DataServiceKeyAttribute> 或 <xref:System.Data.Services.Common.DataServiceEntityAttribute> 应用于类型。</span><span class="sxs-lookup"><span data-stu-id="71bed-115">By applying the <xref:System.Data.Services.Common.DataServiceKeyAttribute> or <xref:System.Data.Services.Common.DataServiceEntityAttribute> to the type.</span></span>

- <span data-ttu-id="71bed-116">当类型拥有一个名为 `ID` 的属性时。</span><span class="sxs-lookup"><span data-stu-id="71bed-116">When the type has a property named `ID`.</span></span>

- <span data-ttu-id="71bed-117">当该类型具有一个名为*type*`ID`的属性时, 其中*type*是该类型的名称。</span><span class="sxs-lookup"><span data-stu-id="71bed-117">When the type has a property named *type*`ID`, where *type* is the name of the type.</span></span>

<span data-ttu-id="71bed-118">默认情况下，将查询结果投影到在客户端定义的类型时，投影中所请求的属性必须存在于客户端类型中。</span><span class="sxs-lookup"><span data-stu-id="71bed-118">By default, when you project query results into a type defined at the client, the properties requested in the projection must exist in the client type.</span></span> <span data-ttu-id="71bed-119">但是，当为 `true` 的 <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> 属性指定值 <xref:System.Data.Services.Client.DataServiceContext> 时，投影中指定的属性不必出现在客户端类型中。</span><span class="sxs-lookup"><span data-stu-id="71bed-119">However, when you specify a value of `true` for the <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> property of the <xref:System.Data.Services.Client.DataServiceContext>, properties specified in the projection are not required to occur in the client type.</span></span>

### <a name="making-updates-to-projected-results"></a><span data-ttu-id="71bed-120">对投影的结果进行更新</span><span class="sxs-lookup"><span data-stu-id="71bed-120">Making Updates to Projected Results</span></span>

<span data-ttu-id="71bed-121">将查询结果投影到客户端上的实体类型时，<xref:System.Data.Services.Client.DataServiceContext> 可以跟踪会在调用 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法时将更新发送回数据服务的那些对象。</span><span class="sxs-lookup"><span data-stu-id="71bed-121">When you project query results into entity types on the client, the <xref:System.Data.Services.Client.DataServiceContext> can track those objects with updates to be sent back to the data service when the <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> method is called.</span></span> <span data-ttu-id="71bed-122">但是，如果进行更新的数据投影到的是客户端上的非实体类型，则无法将更新发送回数据服务。</span><span class="sxs-lookup"><span data-stu-id="71bed-122">However, updates that are made to data projected into non-entity types on the client cannot be sent back to the data service.</span></span> <span data-ttu-id="71bed-123">这是因为非实体类型没有键来标识实体实例，因此数据服务无法更新数据源中的正确实体。</span><span class="sxs-lookup"><span data-stu-id="71bed-123">This is because without a key to identify the entity instance, the data service cannot update the correct entity in the data source.</span></span> <span data-ttu-id="71bed-124">非实体类型不会被附加到 <xref:System.Data.Services.Client.DataServiceContext>。</span><span class="sxs-lookup"><span data-stu-id="71bed-124">Non-entity types are not attached to the <xref:System.Data.Services.Client.DataServiceContext>.</span></span>

<span data-ttu-id="71bed-125">如果在数据服务中定义的某个实体类型的一个或多个属性没有出现在将该实体投影到的客户端类型中，插入新实体时将不包含这些缺少的属性。</span><span class="sxs-lookup"><span data-stu-id="71bed-125">When one or more properties of an entity type defined in the data service do not occur in the client type into which the entity is projected, inserts of new entities will not contain these missing properties.</span></span> <span data-ttu-id="71bed-126">在这种情况下, 对现有实体进行的更新**也**不包含这些缺少的属性。</span><span class="sxs-lookup"><span data-stu-id="71bed-126">In this case, updates that are made to existing entities will **also** not include these missing properties.</span></span> <span data-ttu-id="71bed-127">如果此类属性存在值，更新时会该属性重置为在数据源中所定义的默认值。</span><span class="sxs-lookup"><span data-stu-id="71bed-127">When a value exists for such a property, the update resets it to the default value for the property, as defined in the data source.</span></span>

### <a name="creating-projected-types"></a><span data-ttu-id="71bed-128">创建投影的类型</span><span class="sxs-lookup"><span data-stu-id="71bed-128">Creating Projected Types</span></span>

<span data-ttu-id="71bed-129">下面的示例使用一个匿名 LINQ 查询，该查询将与地址相关的 `Customers` 类型的属性投影到新的 `CustomerAddress` 类型，该类型在客户端上定义并且属于实体类型：</span><span class="sxs-lookup"><span data-stu-id="71bed-129">The following example uses an anonymous LINQ query that projects the address-related properties of the `Customers` type into a new `CustomerAddress` type, which is defined on the client and is attributed as an entity type:</span></span>

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

<span data-ttu-id="71bed-130">在本示例中，使用对象初始值设定项模式而不是调用构造函数来创建 `CustomerAddress` 类型的新实例。</span><span class="sxs-lookup"><span data-stu-id="71bed-130">In this example, the object initializer pattern is used to create a new instance of the `CustomerAddress` type instead of calling a constructor.</span></span> <span data-ttu-id="71bed-131">投影到实体类型时不支持构造函数，但是投影到非实体类型和匿名类型时可以使用构造函数。</span><span class="sxs-lookup"><span data-stu-id="71bed-131">Constructors are not supported when projecting into entity types, but they can be used when projecting into non-entity and anonymous types.</span></span> <span data-ttu-id="71bed-132">由于 `CustomerAddress` 是实体类型，因此可以进行更改并将更改发送回数据服务。</span><span class="sxs-lookup"><span data-stu-id="71bed-132">Because `CustomerAddress` is an entity type, changes can be made and sent back to the data service.</span></span>

<span data-ttu-id="71bed-133">此外，还将 `Customer` 类型的数据投影到 `CustomerAddress` 实体类型（而不是匿名类型）的实例。</span><span class="sxs-lookup"><span data-stu-id="71bed-133">Also, the data from the `Customer` type is projected into an instance of the `CustomerAddress` entity type instead of an anonymous type.</span></span> <span data-ttu-id="71bed-134">支持投影到匿名类型，但数据将为只读数据，因为匿名类型被视为非实体类型。</span><span class="sxs-lookup"><span data-stu-id="71bed-134">Projection into anonymous types is supported, but the data is read-only because anonymous types are treated as non-entity types.</span></span>

<span data-ttu-id="71bed-135"><xref:System.Data.Services.Client.DataServiceContext> 的 <xref:System.Data.Services.Client.MergeOption> 设置用于在查询投影期间标识解析。</span><span class="sxs-lookup"><span data-stu-id="71bed-135">The <xref:System.Data.Services.Client.MergeOption> settings of the <xref:System.Data.Services.Client.DataServiceContext> are used for identity resolution during query projection.</span></span> <span data-ttu-id="71bed-136">这意味着，如果 `Customer` 类型的实例已存在于 <xref:System.Data.Services.Client.DataServiceContext> 中，则具有相同标识的 `CustomerAddress` 实例将遵循由 <xref:System.Data.Services.Client.MergeOption> 设置的标识解析规则</span><span class="sxs-lookup"><span data-stu-id="71bed-136">This means that if an instance of the `Customer` type already exists in the <xref:System.Data.Services.Client.DataServiceContext>, an instance of `CustomerAddress` with the same identity will follow the identity resolution rules set by the <xref:System.Data.Services.Client.MergeOption></span></span>

<span data-ttu-id="71bed-137">下面介绍将结果投影到实体和非实体类型时的行为:</span><span class="sxs-lookup"><span data-stu-id="71bed-137">The following describes the behaviors when projecting results into entity and non-entity types:</span></span>

<span data-ttu-id="71bed-138">**使用初始值设定项创建新的投影实例**</span><span class="sxs-lookup"><span data-stu-id="71bed-138">**Creating a new projected instance by using initializers**</span></span>

- <span data-ttu-id="71bed-139">示例:</span><span class="sxs-lookup"><span data-stu-id="71bed-139">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- <span data-ttu-id="71bed-140">实体类型:支持</span><span class="sxs-lookup"><span data-stu-id="71bed-140">Entity type: Supported</span></span>

- <span data-ttu-id="71bed-141">非实体类型:支持</span><span class="sxs-lookup"><span data-stu-id="71bed-141">Non-entity type: Supported</span></span>

<span data-ttu-id="71bed-142">**使用构造函数创建新的投影实例**</span><span class="sxs-lookup"><span data-stu-id="71bed-142">**Creating a new projected instance by using constructors**</span></span>

- <span data-ttu-id="71bed-143">示例:</span><span class="sxs-lookup"><span data-stu-id="71bed-143">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- <span data-ttu-id="71bed-144">实体类型:引发 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="71bed-144">Entity type: A <xref:System.NotSupportedException> is raised.</span></span>

- <span data-ttu-id="71bed-145">非实体类型:支持</span><span class="sxs-lookup"><span data-stu-id="71bed-145">Non-entity type: Supported</span></span>

<span data-ttu-id="71bed-146">**使用投影转换属性值**</span><span class="sxs-lookup"><span data-stu-id="71bed-146">**Using projection to transform a property value**</span></span>

- <span data-ttu-id="71bed-147">示例:</span><span class="sxs-lookup"><span data-stu-id="71bed-147">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- <span data-ttu-id="71bed-148">实体类型:实体类型不支持此转换，因为这会导致混淆并且可能会覆盖数据源中属于另一个实体的数据。</span><span class="sxs-lookup"><span data-stu-id="71bed-148">Entity type: This transformation is not supported for entity types because it can lead to confusion and potentially overwriting the data in the data source that belongs to another entity.</span></span> <span data-ttu-id="71bed-149">引发 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="71bed-149">A <xref:System.NotSupportedException> is raised.</span></span>

- <span data-ttu-id="71bed-150">非实体类型:支持</span><span class="sxs-lookup"><span data-stu-id="71bed-150">Non-entity type: Supported</span></span>

<a name="considerations"></a>

## <a name="projection-considerations"></a><span data-ttu-id="71bed-151">投影注意事项</span><span class="sxs-lookup"><span data-stu-id="71bed-151">Projection Considerations</span></span>

<span data-ttu-id="71bed-152">定义查询投影时需要额外考虑下列注意事项。</span><span class="sxs-lookup"><span data-stu-id="71bed-152">The following additional considerations apply when defining a query projection.</span></span>

- <span data-ttu-id="71bed-153">定义 Atom 格式的自定义源时，必须确保已定义自定义映射的所有实体属性都包含在投影中。</span><span class="sxs-lookup"><span data-stu-id="71bed-153">When you define custom feeds for the Atom format, you must make sure that all entity properties that have custom mappings defined are included in the projection.</span></span> <span data-ttu-id="71bed-154">如果投影中不包含某个已映射的实体属性，则可能会丢失数据。</span><span class="sxs-lookup"><span data-stu-id="71bed-154">When a mapped entity property is not included in the projection, data loss might occur.</span></span> <span data-ttu-id="71bed-155">有关详细信息, 请参阅[源自定义](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="71bed-155">For more information, see [Feed Customization](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span></span>

- <span data-ttu-id="71bed-156">当对投影的类型进行插入时，如果对于数据服务的数据模型中的实体，该投影类型不包含其所有属性，则客户端上不包含在投影中的属性设置为其默认值。</span><span class="sxs-lookup"><span data-stu-id="71bed-156">When inserts are made to a projected type that does not contain all of the properties of the entity in the data model of the data service, the properties not included in the projection at the client are set to their default values.</span></span>

- <span data-ttu-id="71bed-157">当对投影的类型进行更新时，如果对于数据服务的数据模型中的实体，该投影类型不包含其所有属性，则客户端上不包含在投影中的现有值将被未初始化的默认值覆盖。</span><span class="sxs-lookup"><span data-stu-id="71bed-157">When updates are made to a projected type that does not contain all of the properties of the entity in the data model of the data service, existing values not included in the projection on the client will be overwritten with uninitialized default values.</span></span>

- <span data-ttu-id="71bed-158">当投影包括复杂属性时，必须返回整个复杂对象。</span><span class="sxs-lookup"><span data-stu-id="71bed-158">When a projection includes a complex property, the entire complex object must be returned.</span></span>

- <span data-ttu-id="71bed-159">当投影包括导航属性时，会隐式加载相关对象，而无需调用 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="71bed-159">When a projection includes a navigation property, the related objects are loaded implicitly without having to call the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method.</span></span> <span data-ttu-id="71bed-160">不支持在投影的查询中使用 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="71bed-160">The <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is not supported for use in a projected query.</span></span>

- <span data-ttu-id="71bed-161">在客户端上进行查询的查询投影在请求 URI 中转换为使用 `$select` 查询选项。</span><span class="sxs-lookup"><span data-stu-id="71bed-161">Query projections queries on the client are translated to use the `$select` query option in the request URI.</span></span> <span data-ttu-id="71bed-162">基于不支持 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 查询选项的早期 `$select` 版本执行具有投影的查询时，将会返回错误。</span><span class="sxs-lookup"><span data-stu-id="71bed-162">When a query with projection is executed against a previous version of [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] that does not support the `$select` query option, an error is returned.</span></span> <span data-ttu-id="71bed-163">当数据服务的 <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> 的 <xref:System.Data.Services.DataServiceBehavior> 设置为值 <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1> 时也会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="71bed-163">This can also happen when the <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> of the <xref:System.Data.Services.DataServiceBehavior> for the data service is set to a value of <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>.</span></span> <span data-ttu-id="71bed-164">有关详细信息, 请参阅[数据服务版本控制](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="71bed-164">For more information, see [Data Service Versioning](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).</span></span>

<span data-ttu-id="71bed-165">有关详细信息，请参阅[如何：项目查询结果](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="71bed-165">For more information, see [How to: Project Query Results](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="71bed-166">请参阅</span><span class="sxs-lookup"><span data-stu-id="71bed-166">See also</span></span>

- [<span data-ttu-id="71bed-167">查询数据服务</span><span class="sxs-lookup"><span data-stu-id="71bed-167">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
