---
title: 垃圾回收器配置设置
description: 了解用于配置垃圾回收器如何为 .NET Core 应用管理内存的运行时设置。
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: ec575bdd17c8a7c290673b7085074bbba94cedef
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102861"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>用于垃圾回收的运行时配置选项

此页包含有关可在运行时更改的垃圾回收器 (GC) 设置的信息。 如果你要尝试让正在运行的应用达到最佳性能，请考虑使用这些设置。 然而，在特定情况下，默认值为大多数应用程序提供最佳性能。

设置在此页上被排入组中。 每个组内的设置通常彼此结合使用以实现特定的结果。

> [!NOTE]
>
> - 这些设置也可以在应用运行时由应用动态地进行更改，因此，你设置的任何运行时设置都可能会被覆盖。
> - 某些设置（如[延迟级别](../../standard/garbage-collection/latency.md)）通常仅在设计时通过 API 进行设置。 此页面省略了此类设置。
> - 对于数值，请对 runtimeconfig.json  文件中的设置使用十进制表示法，而对环境变量设置使用十六进制表示法。 对于十六进制值，可以使用或不使用“0x”前缀来指定它们。

## <a name="flavors-of-garbage-collection"></a>垃圾回收的风格

垃圾回收的两种主要风格是工作站 GC 和服务器 GC。 有关两者之间的差异的详细信息，请参阅[工作站和服务器垃圾回收](../../standard/garbage-collection/workstation-server-gc.md)。

垃圾回收的次要风格是后台垃圾回收和非并发垃圾回收。

使用以下设置，选择垃圾回收的风格：

### <a name="systemgcservercomplus_gcserver"></a>System.GC.Server/COMPlus_gcServer

- 配置应用程序是使用工作站垃圾回收还是服务器垃圾回收。
- 默认：工作站垃圾回收 (`false`)。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Server` | `false` - 工作站<br/>`true` - 服务器 | .NET Core 1.0 |
| MSBuild 属性  | `ServerGarbageCollection` | `false` - 工作站<br/>`true` - 服务器 | .NET Core 1.0 |
| **环境变量** | `COMPlus_gcServer` | `0` - 工作站<br/>`1` - 服务器 | .NET Core 1.0 |
| **.NET Framework 的 app.config** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false` - 工作站<br/>`true` - 服务器 |  |

### <a name="examples"></a>示例

runtimeconfig.json 文件： 

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

项目文件：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System.GC.Concurrent/COMPlus_gcConcurrent

- 配置是否启用后台（并发）垃圾回收。
- 默认：启用 (`true`)。
- 有关详细信息，请参阅[后台垃圾回收](../../standard/garbage-collection/background-gc.md)。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Concurrent` | `true` - 后台 GC<br/>`false` - 非并发 GC | .NET Core 1.0 |
| MSBuild 属性  | `ConcurrentGarbageCollection` | `true` - 后台 GC<br/>`false` - 非并发 GC | .NET Core 1.0 |
| **环境变量** | `COMPlus_gcConcurrent` | `true` - 后台 GC<br/>`false` - 非并发 GC | .NET Core 1.0 |
| **.NET Framework 的 app.config** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true` - 后台 GC<br/>`false` - 非并发 GC |  |

### <a name="examples"></a>示例

runtimeconfig.json 文件： 

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

项目文件：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a>管理资源使用情况

使用此部分中所述的设置，管理垃圾回收器的内存和处理器使用情况。

有关其中某些设置的详细信息，请参阅 [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)（服务器和工作站 GC 之间的中间地带）博客条目。

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System.GC.HeapCount/COMPlus_GCHeapCount

- 限制通过垃圾回收器创建的堆数。
- 仅适用于服务器垃圾回收。
- 如果启用了默认的 [GC 处理器关联](#systemgcnoaffinitizecomplus_gcnoaffinitize)，堆计数设置会将 `n` 个 GC 堆/线程关联到前 `n` 个处理器。 （使用[关联掩码](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)或[关联范围](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges)设置可精确指定要关联的处理器。）
- 如果禁用了 [GC 处理器关联](#systemgcnoaffinitizecomplus_gcnoaffinitize)，则此设置会限制 GC 堆的数量。
- 有关详细信息，请参阅 [GCHeapCount 备注](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapCount` | 十进制值  | .NET Core 3.0 |
| **环境变量** | `COMPlus_GCHeapCount` | 十六进制值  | .NET Core 3.0 |
| **.NET Framework 的 app.config** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | 十进制值  | .NET Framework 4.6.2 |

示例：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> 如果要在 runtimeconfig.template.json  中设置该选项，请指定一个十进制值。 如果要将选项设置为一个环境变量，请指定一个十六进制值。 例如，若要将堆数限制为 16，则该值对于 JSON 文件为 16，对于环境变量则为 0x10 或 10。

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- 指定垃圾回收器线程应使用的确切处理器数。
- 如果禁用了 [GC 处理器关联](#systemgcnoaffinitizecomplus_gcnoaffinitize)，则忽略此设置。
- 仅适用于服务器垃圾回收。
- 该值是一个位掩码，用于定义可用于该进程的处理器。 例如，十进制值 1023 或十六进制值 0x3FF 或 3FF（如果使用环境变量）在二进制记数法中为 0011 1111 1111。 这指定将使用前 10 个处理器。 若要指定接下来使用的 10 个处理器（即处理器 10-19），请指定一个十进制值 1047552（或十六进制值 0xFFC00 或 FFC00），它等效于二进制值 1111 1111 1100 0000 0000。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapAffinitizeMask` | 十进制值  | .NET Core 3.0 |
| **环境变量** | `COMPlus_GCHeapAffinitizeMask` | 十六进制值  | .NET Core 3.0 |
| **.NET Framework 的 app.config** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | 十进制值  | .NET Framework 4.6.2 |

示例：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- 指定用于垃圾回收器线程的处理器列表。
- 此设置与 [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) 类似，只是它允许你指定超过 64 个的处理器。
- 对于 Windows 操作系统，请为处理器编号或范围加上相应的 [CPU 组](/windows/win32/procthread/processor-groups)作为前缀，例如“0:1-10,0:12,1:50-52,1:70”。
- 如果禁用了 [GC 处理器关联](#systemgcnoaffinitizecomplus_gcnoaffinitize)，则忽略此设置。
- 仅适用于服务器垃圾回收。
- 有关详细信息，请参阅 Maoni Stephens 的博客文章 [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/)（在 CPU 大于 64 个的计算机上，为 GC 提供更好的 CPU 配置）。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.GCHeapAffinitizeRanges` | 以逗号分隔的处理器编号列表或处理器编号范围。<br/>Unix 示例：“1-10,12,50-52,70”<br/>Windows 示例：“0:1-10,0:12,1:50-52,1:70” | .NET Core 3.0 |
| **环境变量** | `COMPlus_GCHeapAffinitizeRanges` | 以逗号分隔的处理器编号列表或处理器编号范围。<br/>Unix 示例：“1-10,12,50-52,70”<br/>Windows 示例：“0:1-10,0:12,1:50-52,1:70” | .NET Core 3.0 |

示例：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a>COMPlus_GCCpuGroup

- 配置垃圾回收器是否使用 [CPU 组](/windows/win32/procthread/processor-groups)。

  当 64 位 Windows 计算机具有多个 CPU 组（即，有超过 64 个处理器）时，通过启用此元素，可跨所有 CPU 组扩展垃圾回收。 垃圾回收器使用所有核心来创建和平衡堆。

- 仅适用于 64 位 Windows 操作系统上的服务器垃圾回收。
- 默认：禁用 (`0`)。
- 有关详细信息，请参阅 Maoni Stephens 的博客文章 [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/)（在 CPU 大于 64 个的计算机上，为 GC 提供更好的 CPU 配置）。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | 不可用 | 不可用 | 不可用 |
| **环境变量** | `COMPlus_GCCpuGroup` | `0` - 禁用<br/>`1` - 启用 | .NET Core 1.0 |
| **.NET Framework 的 app.config** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false` - 禁用<br/>`true` - 启用 |  |

> [!NOTE]
> 若要配置公共语言运行时 (CLR)，使其也在所有 CPU 组之间分配线程池中的线程，请启用 [Thread_UseAllCpuGroups 元素](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)选项。 对于 .NET Core 应用，可以通过将 `COMPlus_Thread_UseAllCpuGroups` 环境变量的值设置为 `1` 以启用此选项。

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System.GC.NoAffinitize/COMPlus_GCNoAffinitize

- 指定是否将垃圾回收线程与处理器关联  。 若要关联一个 GC 线程，则意味着它只能在其特定的 CPU 上运行。 为每个 GC 线程创建一个堆。
- 仅适用于服务器垃圾回收。
- 默认：将垃圾回收线程与处理器关联 (`false`)。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.NoAffinitize` | `false` - 关联<br/>`true` - 不关联 | .NET Core 3.0 |
| **环境变量** | `COMPlus_GCNoAffinitize` | `0` - 关联<br/>`1` - 不关联 | .NET Core 3.0 |
| **.NET Framework 的 app.config** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false` - 关联<br/>`true` - 不关联 | .NET Framework 4.6.2 |

示例：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit

- 指定 GC 堆和 GC 簿记的最大提交大小（以字节为单位）。
- 此设置仅适用于 64 位计算机。
- 默认值（仅在某些情况下适用）是 20 MB 或容器内存限制的 75%（以较大者为准）。 此默认值在以下情况下适用：

  - 进程正在具有指定内存限制的容器中运行。
  - [HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) 未设置。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimit` | 十进制值  | .NET Core 3.0 |
| **环境变量** | `COMPlus_GCHeapHardLimit` | 十六进制值  | .NET Core 3.0 |

示例：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> 如果要在 runtimeconfig.template.json  中设置该选项，请指定一个十进制值。 如果要将选项设置为一个环境变量，请指定一个十六进制值。 例如，若要将堆硬限制指定为 200 个兆字节 (MiB)，则该值对于 JSON 文件为 209715200，对于环境变量则为 0xC800000 或 C800000。

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- 指定允许的 GC 堆使用量占总物理内存的百分比。
- 如果还设置了 [System.GC.heaphdlimit](#systemgcheaphardlimitcomplus_gcheaphardlimit)，则忽略此设置。
- 此设置仅适用于 64 位计算机。
- 如果进程正在具有指定内存限制的容器中运行，则百分比的计算结果将为该内存限制的百分比。
- 默认值（仅在某些情况下适用）是 20 MB 或容器内存限制的 75%（以较小者为准）。 此默认值在以下情况下适用：

  - 进程正在具有指定内存限制的容器中运行。
  - [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) 未设置。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitPercent` | 十进制值  | .NET Core 3.0 |
| **环境变量** | `COMPlus_GCHeapHardLimitPercent` | 十六进制值  | .NET Core 3.0 |

示例：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> 如果要在 runtimeconfig.template.json  中设置该选项，请指定一个十进制值。 如果要将选项设置为一个环境变量，请指定一个十六进制值。 例如，若要将堆使用率限制为 30%，则该值对于 JSON 文件为 30，对于环境变量则为 0x1E 或 1E。

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System.GC.RetainVM/COMPlus_GCRetainVM

- 配置是将应删除的段置于备用列表上供将来使用，还是将其释放回操作系统 (OS)。
- 默认：将段释放回操作系统 (`false`)。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.RetainVM` | `false` - 释放到 OS<br/>`true` - 置于备用列表上 | .NET Core 1.0 |
| MSBuild 属性  | `RetainVMGarbageCollection` | `false` - 释放到 OS<br/>`true` - 置于备用列表上 | .NET Core 1.0 |
| **环境变量** | `COMPlus_GCRetainVM` | `0` - 释放到 OS<br/>`1` - 置于备用列表上 | .NET Core 1.0 |

### <a name="examples"></a>示例

runtimeconfig.json 文件： 

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

项目文件：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a>大型页面

### <a name="complus_gclargepages"></a>COMPlus_GCLargePages

- 指定设置堆硬限制时是否应使用大型页面。
- 默认：禁用 (`0`)。
- 这是一项实验性设置。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | 不可用 | 不可用 | 不可用 |
| **环境变量** | `COMPlus_GCLargePages` | `0` - 禁用<br/>`1` - 启用 | .NET Core 3.0 |

## <a name="large-objects"></a>大型对象

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- 在 64 位平台上，为总大小大于 2 千兆字节 (GB) 的数组配置垃圾回收器支持。
- 默认：启用 (`1`)。
- 在未来的 .NET 版本中，此选项可能会过时。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | 不可用 | 不可用 | 不可用 |
| **环境变量** | `COMPlus_gcAllowVeryLargeObjects` | `1` - 启用<br/> `0` - 禁用 | .NET Core 1.0 |
| **.NET Framework 的 app.config** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1` - 启用<br/> `0` - 禁用 | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>大型对象堆阈值

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System.GC.LOHThreshold/COMPlus_GCLOHThreshold

- 指定导致对象进入大型对象堆 (LOH) 的阈值大小（以字节为单位）。
- 默认阈值为 85,000 字节。
- 指定的值必须大于默认阈值。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.LOHThreshold` | 十进制值  | .NET Core 1.0 |
| **环境变量** | `COMPlus_GCLOHThreshold` | 十六进制值  | .NET Core 1.0 |
| **.NET Framework 的 app.config** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | 十进制值  | .NET Framework 4.8 |

示例：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> 如果要在 runtimeconfig.template.json  中设置该选项，请指定一个十进制值。 如果要将选项设置为一个环境变量，请指定一个十六进制值。 例如，若要将阙值大小设置为 120,000 个字节，则该值对于 JSON 文件为 120,000，对于环境变量则为 0x1D4C0 或 1D4C0。

## <a name="standalone-gc"></a>独立 GC

### <a name="complus_gcname"></a>COMPlus_GCName

- 指定库的路径，该库包含运行时打算加载的垃圾回收器。
- 有关详细信息，请参阅 [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md)（独立 GC 加载程序设计）。

| | 设置名 | 值 | 引入的版本 |
| - | - | - | - |
| **runtimeconfig.json** | 不可用 | 不可用 | 不可用 |
| **环境变量** | `COMPlus_GCName` | string_path  | .NET Core 2.0 |
