---
title: 如何：将时区保存到嵌入的资源
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c67a97193d186275e6a788f6b18bbc17c535f367
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592869"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="10909-102">如何：将时区保存到嵌入的资源</span><span class="sxs-lookup"><span data-stu-id="10909-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="10909-103">时区感知应用程序通常需要某个特定时区存在。</span><span class="sxs-lookup"><span data-stu-id="10909-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="10909-104">但是，因为单个可用性<xref:System.TimeZoneInfo>对象取决于存储在本地系统注册表中的信息，即使通常可用的时区可能不存在。</span><span class="sxs-lookup"><span data-stu-id="10909-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="10909-105">此外，有关自定义时区的信息通过使用实例化<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法不会存储在注册表中其他时区信息。</span><span class="sxs-lookup"><span data-stu-id="10909-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="10909-106">若要确保这些时间区域可在需要时，可以通过序列化，将其保存，并更高版本进行反序列化这些还原它们。</span><span class="sxs-lookup"><span data-stu-id="10909-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="10909-107">通常情况下，序列化<xref:System.TimeZoneInfo>对象出现除了时区感知应用程序。</span><span class="sxs-lookup"><span data-stu-id="10909-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="10909-108">具体取决于用来保存序列化数据存储<xref:System.TimeZoneInfo>对象所在的时区数据可能会进行序列化 （例如，当数据存储在注册表的应用程序密钥），设置或安装例程的一部分或作为运行实用程序例程的一部分之前在最终应用程序 （例如，当序列化的数据存储在.NET XML 资源 (.resx) 文件） 编译。</span><span class="sxs-lookup"><span data-stu-id="10909-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="10909-109">与应用程序编译的资源文件，除了几个其他数据存储可以用于时区信息。</span><span class="sxs-lookup"><span data-stu-id="10909-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="10909-110">其中包括：</span><span class="sxs-lookup"><span data-stu-id="10909-110">These include the following:</span></span>

* <span data-ttu-id="10909-111">在注册表中。</span><span class="sxs-lookup"><span data-stu-id="10909-111">The registry.</span></span> <span data-ttu-id="10909-112">请注意应用程序应使用其自己的应用程序项的子项来存储自定义时区数据，而不是使用 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones 的子项。</span><span class="sxs-lookup"><span data-stu-id="10909-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

* <span data-ttu-id="10909-113">配置文件。</span><span class="sxs-lookup"><span data-stu-id="10909-113">Configuration files.</span></span>

* <span data-ttu-id="10909-114">其他系统文件。</span><span class="sxs-lookup"><span data-stu-id="10909-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="10909-115">若要通过序列化到.resx 文件中保存时区</span><span class="sxs-lookup"><span data-stu-id="10909-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="10909-116">检索现有的时区，或者创建新的时区。</span><span class="sxs-lookup"><span data-stu-id="10909-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="10909-117">若要检索现有的时区，请参阅[如何：访问预定义的 UTC 和本地时区对象](../../../docs/standard/datetime/access-utc-and-local.md)和[如何：实例化 TimeZoneInfo 对象](../../../docs/standard/datetime/instantiate-time-zone-info.md)。</span><span class="sxs-lookup"><span data-stu-id="10909-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="10909-118">若要创建新的时区，请调用的重载之一<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="10909-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="10909-119">有关详细信息，请参阅[如何：创建不含调整规则的时区](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)和[如何：创建含调整规则的时区](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="10909-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="10909-120">调用<xref:System.TimeZoneInfo.ToSerializedString%2A>方法来创建包含时区的数据的字符串。</span><span class="sxs-lookup"><span data-stu-id="10909-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="10909-121">实例化<xref:System.IO.StreamWriter>对象提供名称和 （可选） 的.resx 文件的路径<xref:System.IO.StreamWriter>类构造函数。</span><span class="sxs-lookup"><span data-stu-id="10909-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="10909-122">实例化<xref:System.Resources.ResXResourceWriter>对象通过传递<xref:System.IO.StreamWriter>对象传递给<xref:System.Resources.ResXResourceWriter>类构造函数。</span><span class="sxs-lookup"><span data-stu-id="10909-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="10909-123">Pass 时区的序列化到字符串<xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="10909-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="10909-124">调用 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="10909-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="10909-125">调用 <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="10909-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="10909-126">关闭<xref:System.IO.StreamWriter>对象通过调用其<xref:System.IO.StreamWriter.Close%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="10909-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="10909-127">将生成的.resx 文件添加到应用程序的 Visual Studio 项目。</span><span class="sxs-lookup"><span data-stu-id="10909-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="10909-128">使用**属性**窗口在 Visual Studio 中，请确保.resx 文件**生成操作**属性设置为**嵌入的资源**。</span><span class="sxs-lookup"><span data-stu-id="10909-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="10909-129">示例</span><span class="sxs-lookup"><span data-stu-id="10909-129">Example</span></span>

<span data-ttu-id="10909-130">下面的示例序列化为<xref:System.TimeZoneInfo>对象，表示中部标准时间和<xref:System.TimeZoneInfo>表示帕默站，南极时间名为 SerializedTimeZones.resx.NET XML 资源文件的对象。</span><span class="sxs-lookup"><span data-stu-id="10909-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="10909-131">在注册表中; 通常定义中部标准时间帕默站，南极是自定义时区。</span><span class="sxs-lookup"><span data-stu-id="10909-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="10909-132">此示例中序列化<xref:System.TimeZoneInfo>对象，使他们能够在资源文件在编译时。</span><span class="sxs-lookup"><span data-stu-id="10909-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="10909-133">因为<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>方法将完整的标头信息添加到.NET XML 资源文件，所以不能用来将资源添加到现有文件。</span><span class="sxs-lookup"><span data-stu-id="10909-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="10909-134">通过检查 SerializedTimeZones.resx 文件，该示例处理这和，如果存在，而不存储所有其资源的两个序列化时区为泛型<xref:System.Collections.Generic.Dictionary%602>对象。</span><span class="sxs-lookup"><span data-stu-id="10909-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="10909-135">然后删除现有文件和现有的资源添加到新的 SerializedTimeZones.resx 文件。</span><span class="sxs-lookup"><span data-stu-id="10909-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="10909-136">序列化的时区数据也添加到此文件。</span><span class="sxs-lookup"><span data-stu-id="10909-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="10909-137">密钥 (或**名称**) 的资源的字段不应包含嵌入的空格。</span><span class="sxs-lookup"><span data-stu-id="10909-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="10909-138"><xref:System.String.Replace%28System.String%2CSystem.String%29>调用方法之前分配给资源文件所在的时区标识符中删除所有嵌入的空格。</span><span class="sxs-lookup"><span data-stu-id="10909-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="10909-139">编译代码</span><span class="sxs-lookup"><span data-stu-id="10909-139">Compiling the code</span></span>

<span data-ttu-id="10909-140">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="10909-140">This example requires:</span></span>

* <span data-ttu-id="10909-141">对 system.windows.forms.dll 的引用和 System.Core.dll 的引用将添加到项目。</span><span class="sxs-lookup"><span data-stu-id="10909-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="10909-142">将导入以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="10909-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="10909-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="10909-143">See also</span></span>

- [<span data-ttu-id="10909-144">日期、时间和时区</span><span class="sxs-lookup"><span data-stu-id="10909-144">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="10909-145">时区概述</span><span class="sxs-lookup"><span data-stu-id="10909-145">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="10909-146">如何：从嵌入的资源还原时区</span><span class="sxs-lookup"><span data-stu-id="10909-146">How to: Restore time zones from an embedded resource</span></span>](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
