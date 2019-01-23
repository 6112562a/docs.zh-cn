---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: d6f0e4741aa10bff450a29cfd7a9e63e226c6495
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498877"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="16ce4-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="16ce4-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="16ce4-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="16ce4-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16ce4-104">语法</span><span class="sxs-lookup"><span data-stu-id="16ce4-104">Syntax</span></span>  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="16ce4-105">方法</span><span class="sxs-lookup"><span data-stu-id="16ce4-105">Methods</span></span>  
 <span data-ttu-id="16ce4-106">ServiceDebugBehavior 类未定义任何方法。</span><span class="sxs-lookup"><span data-stu-id="16ce4-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="16ce4-107">Properties</span><span class="sxs-lookup"><span data-stu-id="16ce4-107">Properties</span></span>  
 <span data-ttu-id="16ce4-108">ServiceDebugBehavior 类具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="16ce4-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="16ce4-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="16ce4-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="16ce4-110">数据类型：Boolean</span><span class="sxs-lookup"><span data-stu-id="16ce4-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="16ce4-111">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="16ce4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16ce4-112">控制服务是否在 `HttpGetUrl` 属性控制的地址上发布其 WSDL。</span><span class="sxs-lookup"><span data-stu-id="16ce4-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="16ce4-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="16ce4-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="16ce4-114">数据类型：String</span><span class="sxs-lookup"><span data-stu-id="16ce4-114">Data type: string</span></span>  
  
 <span data-ttu-id="16ce4-115">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="16ce4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16ce4-116">设置位置，在该位置发布服务 WSDL 以便使用 HTTP 进行检索。</span><span class="sxs-lookup"><span data-stu-id="16ce4-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="16ce4-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="16ce4-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="16ce4-118">数据类型：Boolean</span><span class="sxs-lookup"><span data-stu-id="16ce4-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="16ce4-119">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="16ce4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16ce4-120">控制服务是否在 `HttpsGetUrl` 属性控制的地址上通过 HTTPS 发布其 WSDL。</span><span class="sxs-lookup"><span data-stu-id="16ce4-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="16ce4-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="16ce4-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="16ce4-122">数据类型：String</span><span class="sxs-lookup"><span data-stu-id="16ce4-122">Data type: string</span></span>  
  
 <span data-ttu-id="16ce4-123">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="16ce4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16ce4-124">设置位置，在该位置发布服务 WSDL 以便使用 HTTPS 进行检索。</span><span class="sxs-lookup"><span data-stu-id="16ce4-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="16ce4-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="16ce4-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="16ce4-126">数据类型：Boolean</span><span class="sxs-lookup"><span data-stu-id="16ce4-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="16ce4-127">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="16ce4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16ce4-128">指定是否在返回给客户端的 SOAP 错误详细信息中包含托管异常信息以供调试。</span><span class="sxs-lookup"><span data-stu-id="16ce4-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16ce4-129">要求</span><span class="sxs-lookup"><span data-stu-id="16ce4-129">Requirements</span></span>  
  
|<span data-ttu-id="16ce4-130">MOF</span><span class="sxs-lookup"><span data-stu-id="16ce4-130">MOF</span></span>|<span data-ttu-id="16ce4-131">已在 Servicemodel.mof 中声明。</span><span class="sxs-lookup"><span data-stu-id="16ce4-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="16ce4-132">命名空间</span><span class="sxs-lookup"><span data-stu-id="16ce4-132">Namespace</span></span>|<span data-ttu-id="16ce4-133">已在 root\ServiceModel 中定义</span><span class="sxs-lookup"><span data-stu-id="16ce4-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16ce4-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="16ce4-134">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
