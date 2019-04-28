---
title: 查找本地系统上定义的时区
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a65798c46b01bb7a702559d685590ecf7a6f2793
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61819751"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="95044-102">查找本地系统上定义的时区</span><span class="sxs-lookup"><span data-stu-id="95044-102">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="95044-103"><xref:System.TimeZoneInfo> 类不公开公共构造函数。</span><span class="sxs-lookup"><span data-stu-id="95044-103">The <xref:System.TimeZoneInfo> class does not expose a public constructor.</span></span> <span data-ttu-id="95044-104">因此，`new` 关键字不能用于创建新的 <xref:System.TimeZoneInfo> 对象。</span><span class="sxs-lookup"><span data-stu-id="95044-104">As a result, the `new` keyword cannot be used to create a new <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="95044-105">相反，<xref:System.TimeZoneInfo> 对象通过从注册表检索关于预定义时区的信息或通过创建自定义时区而完成实例化。</span><span class="sxs-lookup"><span data-stu-id="95044-105">Instead, <xref:System.TimeZoneInfo> objects are instantiated either by retrieving information on predefined time zones from the registry or by creating a custom time zone.</span></span> <span data-ttu-id="95044-106">本主题讨论从存储在注册表中的数据实例化时区。</span><span class="sxs-lookup"><span data-stu-id="95044-106">This topic discusses instantiating a time zone from data stored in the registry.</span></span> <span data-ttu-id="95044-107">此外，<xref:System.TimeZoneInfo> 类的 `static`（Visual Basic 中的 `shared`）属性提供对协调世界时 (UTC) 和本地时区的访问。</span><span class="sxs-lookup"><span data-stu-id="95044-107">In addition, `static` (`shared` in Visual Basic) properties of the <xref:System.TimeZoneInfo> class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

> [!NOTE]
> <span data-ttu-id="95044-108">对于在注册表中未定义的时区，可以通过调用 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法的重载创建自定义时区。</span><span class="sxs-lookup"><span data-stu-id="95044-108">For time zones that are not defined in the registry, you can create custom time zones by calling the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="95044-109">在讨论创建自定义时区[如何：创建不含调整规则的时区](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)和[如何：创建含调整规则的时区](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)主题。</span><span class="sxs-lookup"><span data-stu-id="95044-109">Creating a custom time zone is discussed in the [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) topics.</span></span> <span data-ttu-id="95044-110">此外，可以通过使用 <xref:System.TimeZoneInfo.FromSerializedString%2A> 方法将 <xref:System.TimeZoneInfo> 对象从序列化字符串还原来对其实例化。</span><span class="sxs-lookup"><span data-stu-id="95044-110">In addition, you can instantiate a <xref:System.TimeZoneInfo> object by restoring it from a serialized string with the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span> <span data-ttu-id="95044-111">序列化和反序列化<xref:System.TimeZoneInfo>中讨论对象[如何：将时区保存到嵌入的资源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)和[如何：从嵌入的资源还原时区](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)主题。</span><span class="sxs-lookup"><span data-stu-id="95044-111">Serializing and deserializing a <xref:System.TimeZoneInfo> object is discussed in the [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore Time Zones from an Embedded Resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) topics.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="95044-112">访问独立时区</span><span class="sxs-lookup"><span data-stu-id="95044-112">Accessing individual time zones</span></span>

<span data-ttu-id="95044-113"><xref:System.TimeZoneInfo> 类提供两个预定义的时区对象，分别表示 UTC 时间和本地时区。</span><span class="sxs-lookup"><span data-stu-id="95044-113">The <xref:System.TimeZoneInfo> class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="95044-114">它们分别可从 <xref:System.TimeZoneInfo.Utc%2A> 和 <xref:System.TimeZoneInfo.Local%2A> 属性获得。</span><span class="sxs-lookup"><span data-stu-id="95044-114">They are available from the <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A> properties, respectively.</span></span> <span data-ttu-id="95044-115">有关访问 UTC 或本地时区的说明，请参阅[如何：访问预定义的 UTC 和本地时区对象](../../../docs/standard/datetime/access-utc-and-local.md)。</span><span class="sxs-lookup"><span data-stu-id="95044-115">For instructions on accessing the UTC or local time zones, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md).</span></span>

<span data-ttu-id="95044-116">还可以实例化表示注册表中定义的任何时区的 <xref:System.TimeZoneInfo> 对象。</span><span class="sxs-lookup"><span data-stu-id="95044-116">You can also instantiate a <xref:System.TimeZoneInfo> object that represents any time zone defined in the registry.</span></span> <span data-ttu-id="95044-117">有关实例化特定时区对象的说明，请参阅[如何：实例化 TimeZoneInfo 对象](../../../docs/standard/datetime/instantiate-time-zone-info.md)。</span><span class="sxs-lookup"><span data-stu-id="95044-117">For instructions on instantiating a specific time zone object, see [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="95044-118">时区标识符</span><span class="sxs-lookup"><span data-stu-id="95044-118">Time zone identifiers</span></span>

<span data-ttu-id="95044-119">时区标识符是唯一标识时区的键字段。</span><span class="sxs-lookup"><span data-stu-id="95044-119">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="95044-120">虽然大多数键都相对较短，但时区标识符相对较长。</span><span class="sxs-lookup"><span data-stu-id="95044-120">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="95044-121">在大多数情况下，其值对应于 <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> 属性，该属性用于提供时区标准时间的名称。</span><span class="sxs-lookup"><span data-stu-id="95044-121">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="95044-122">但是，有例外情况。</span><span class="sxs-lookup"><span data-stu-id="95044-122">However, there are exceptions.</span></span> <span data-ttu-id="95044-123">确保提供有效标识符最好的办法是枚举系统上可用的时区，并记下其关联的标识符。</span><span class="sxs-lookup"><span data-stu-id="95044-123">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span>

## <a name="see-also"></a><span data-ttu-id="95044-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="95044-124">See also</span></span>

- [<span data-ttu-id="95044-125">日期、时间和时区</span><span class="sxs-lookup"><span data-stu-id="95044-125">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="95044-126">如何：访问预定义的 UTC 和本地时区对象</span><span class="sxs-lookup"><span data-stu-id="95044-126">How to: Access the predefined UTC and local time zone objects</span></span>](../../../docs/standard/datetime/access-utc-and-local.md)
- [<span data-ttu-id="95044-127">如何：实例化 TimeZoneInfo 对象</span><span class="sxs-lookup"><span data-stu-id="95044-127">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
- [<span data-ttu-id="95044-128">在各时区之间转换时间</span><span class="sxs-lookup"><span data-stu-id="95044-128">Converting times between time zones</span></span>](../../../docs/standard/datetime/converting-between-time-zones.md)
