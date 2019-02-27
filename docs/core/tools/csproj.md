---
title: .NET Core 的 csproj 格式的新增内容
description: 了解现有文件和 .NET Core csproj 文件之间的区别
author: blackdwarf
ms.date: 09/22/2017
ms.openlocfilehash: d715a3a30c48f1c3fa837b24ee21b49fa947011a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748005"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="e6183-103">.NET Core 的 csproj 格式的新增内容</span><span class="sxs-lookup"><span data-stu-id="e6183-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="e6183-104">本文档概述了作为从 *project.json* 移动到 *csproj* 和 [MSBuild](https://github.com/Microsoft/MSBuild) 的一部分，添加到项目文件的更改。</span><span class="sxs-lookup"><span data-stu-id="e6183-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="e6183-105">有关常规项目文件的语法和引用的详细信息，请参阅 [MSBuild 项目文件](/visualstudio/msbuild/msbuild-project-file-schema-reference)文档。</span><span class="sxs-lookup"><span data-stu-id="e6183-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="e6183-106">隐式包引用</span><span class="sxs-lookup"><span data-stu-id="e6183-106">Implicit package references</span></span>
<span data-ttu-id="e6183-107">基于项目文件的 `<TargetFramework>` 或 `<TargetFrameworks>` 属性中指定的目标框架对元包进行隐式引用。</span><span class="sxs-lookup"><span data-stu-id="e6183-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="e6183-108">如果指定了 `<TargetFramework>`，则忽略 `<TargetFrameworks>`，而与顺序无关。</span><span class="sxs-lookup"><span data-stu-id="e6183-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="e6183-109">建议</span><span class="sxs-lookup"><span data-stu-id="e6183-109">Recommendations</span></span>
<span data-ttu-id="e6183-110">由于隐式引用了 `Microsoft.NETCore.App` 或 `NetStandard.Library` 元包，以下是建议的最佳做法：</span><span class="sxs-lookup"><span data-stu-id="e6183-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="e6183-111">面向 .NET Core 或 .NET Standard 时，绝不通过项目文件中的 `<PackageReference>` 项，对 `Microsoft.NETCore.App` 或 `NetStandard.Library` 元包进行显式引用。</span><span class="sxs-lookup"><span data-stu-id="e6183-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="e6183-112">面向 .NET Core 时，如果需要特定版本的运行时，应使用项目中的 `<RuntimeFrameworkVersion>` 属性（例如，`1.0.4`），而不是引用元包。</span><span class="sxs-lookup"><span data-stu-id="e6183-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="e6183-113">例如，如果使用[独立部署](../deploying/index.md#self-contained-deployments-scd)且需要 1.0.0 LTS 运行时的特定修补程序版本，可能会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="e6183-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="e6183-114">面向 .NET Standard 时，如果需要特定版本的 `NetStandard.Library` 元包，可以使用 `<NetStandardImplicitPackageVersion>` 属性并设置所需版本。</span><span class="sxs-lookup"><span data-stu-id="e6183-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="e6183-115">请勿在 .NET Framework 项目中显式添加或更新对 `Microsoft.NETCore.App` 或 `NetStandard.Library` 元包的引用。</span><span class="sxs-lookup"><span data-stu-id="e6183-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="e6183-116">使用基于 .NET Standard 的 NuGet 包时，如果需要任意版本的 `NetStandard.Library`，NuGet 可自动安装该版本。</span><span class="sxs-lookup"><span data-stu-id="e6183-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="e6183-117">.NET Core 项目中默认包含的编译项</span><span class="sxs-lookup"><span data-stu-id="e6183-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="e6183-118">已通过移动到最新 SDK 版本中的 *csproj* 格式，将默认的编译项和嵌入资源的包含项和排除项移至 SDK 属性文件。</span><span class="sxs-lookup"><span data-stu-id="e6183-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="e6183-119">这意味着不需要再在项目文件中指定这些项。</span><span class="sxs-lookup"><span data-stu-id="e6183-119">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="e6183-120">执行此操作的主要目的是减少项目文件中的混杂。</span><span class="sxs-lookup"><span data-stu-id="e6183-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="e6183-121">SDK 中的默认设置应涵盖最常见的用例，由此便无需在创建的每个项目中重复这些设置。</span><span class="sxs-lookup"><span data-stu-id="e6183-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="e6183-122">这可使项目文件更小，更易于理解和进行手动编辑（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="e6183-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="e6183-123">下表显示同时在 SDK 中包含和排除的元素和 [globs](https://en.wikipedia.org/wiki/Glob_(programming))：</span><span class="sxs-lookup"><span data-stu-id="e6183-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="e6183-124">元素</span><span class="sxs-lookup"><span data-stu-id="e6183-124">Element</span></span>           | <span data-ttu-id="e6183-125">包含 glob</span><span class="sxs-lookup"><span data-stu-id="e6183-125">Include glob</span></span>                              | <span data-ttu-id="e6183-126">排除 glob</span><span class="sxs-lookup"><span data-stu-id="e6183-126">Exclude glob</span></span>                                                  | <span data-ttu-id="e6183-127">删除 glob</span><span class="sxs-lookup"><span data-stu-id="e6183-127">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="e6183-128">Compile</span><span class="sxs-lookup"><span data-stu-id="e6183-128">Compile</span></span>           | <span data-ttu-id="e6183-129">\*\*/\*.cs（或其他语言扩展名）</span><span class="sxs-lookup"><span data-stu-id="e6183-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="e6183-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="e6183-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="e6183-131">不可用</span><span class="sxs-lookup"><span data-stu-id="e6183-131">N/A</span></span>                        |
| <span data-ttu-id="e6183-132">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="e6183-132">EmbeddedResource</span></span>  | <span data-ttu-id="e6183-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="e6183-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="e6183-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="e6183-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="e6183-135">不可用</span><span class="sxs-lookup"><span data-stu-id="e6183-135">N/A</span></span>                        |
| <span data-ttu-id="e6183-136">None</span><span class="sxs-lookup"><span data-stu-id="e6183-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="e6183-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="e6183-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="e6183-138">- \*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="e6183-138">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="e6183-139">如果项目中有 glob，却又尝试使用最新的 SDK 生成它，则将收到以下错误：</span><span class="sxs-lookup"><span data-stu-id="e6183-139">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="e6183-140">包含重复的编译项。</span><span class="sxs-lookup"><span data-stu-id="e6183-140">Duplicate Compile items were included.</span></span> <span data-ttu-id="e6183-141">默认情况下，.NET SDK 包括项目目录中的编译项。</span><span class="sxs-lookup"><span data-stu-id="e6183-141">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="e6183-142">可从项目文件中删除这些项，或如果想要在项目文件中显式包括它们，则将“EnableDefaultCompileItems”属性设为“false”。</span><span class="sxs-lookup"><span data-stu-id="e6183-142">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="e6183-143">要解决此错误，可以删除与前表中所列项匹配的显式 `Compile` 项，也可以将 `<EnableDefaultCompileItems>` 属性设置为 `false`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e6183-143">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="e6183-144">将此属性设置为 `false` 将禁用隐式包含，并还原到以前 SDK 的行为，在这种情况下，必须在项目中指定默认 glob。</span><span class="sxs-lookup"><span data-stu-id="e6183-144">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="e6183-145">此更改不会修改其他包含项的主要机制。</span><span class="sxs-lookup"><span data-stu-id="e6183-145">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="e6183-146">但是，如果要指定（例如，指定某些文件通过应用发布），仍可以使用 *csproj* 中相应的已知机制来实现（例如，`<Content>` 元素）。</span><span class="sxs-lookup"><span data-stu-id="e6183-146">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="e6183-147">`<EnableDefaultCompileItems>` 仅禁用 `Compile` glob，但不会影响其他 glob（如隐式 `None` glob），这也适用于 \*.cs 项。</span><span class="sxs-lookup"><span data-stu-id="e6183-147">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="e6183-148">因此，解决方案资源管理器继续显示在项目中作为 `None` 项的 \*.cs 项。</span><span class="sxs-lookup"><span data-stu-id="e6183-148">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="e6183-149">可按照类似的方式使用 `<EnableDefaultNoneItems>` 禁用隐式 `None` glob。</span><span class="sxs-lookup"><span data-stu-id="e6183-149">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="e6183-150">要禁用所有隐式 glob，可将 `<EnableDefaultItems>` 属性设置为 `false`，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="e6183-150">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="e6183-151">如何像 MSBuild 一样查看整个项目</span><span class="sxs-lookup"><span data-stu-id="e6183-151">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="e6183-152">虽然这些 csproj 更改极大地简化了项目文件，但建议查看完全展开的项目，就像 MSBuild 查看添加了 SDK 及其目标的项目一样。</span><span class="sxs-lookup"><span data-stu-id="e6183-152">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="e6183-153">使用 [`dotnet msbuild`](dotnet-msbuild.md) 命令的 [`/pp` 开关](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)预处理项目，显示导入的文件、文件源及其在生成中的参与情况，而无需实际生成项目：</span><span class="sxs-lookup"><span data-stu-id="e6183-153">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="e6183-154">如果项目有多个目标框架，命令结果应仅侧重于框架之一，具体方法为将相应框架指定为 MSBuild 属性：</span><span class="sxs-lookup"><span data-stu-id="e6183-154">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="e6183-155">新增内容</span><span class="sxs-lookup"><span data-stu-id="e6183-155">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="e6183-156">Sdk 特性</span><span class="sxs-lookup"><span data-stu-id="e6183-156">Sdk attribute</span></span> 
<span data-ttu-id="e6183-157">.csproj 文件的根 `<Project>` 元素具有名为 `Sdk` 的新特性。</span><span class="sxs-lookup"><span data-stu-id="e6183-157">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="e6183-158">`Sdk` 指定项目将使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="e6183-158">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="e6183-159">如[分层文档](cli-msbuild-architecture.md)中所述，SDK 是一组可生成 .NET Core 代码的 MSBuild [任务](/visualstudio/msbuild/msbuild-tasks)和[目标](/visualstudio/msbuild/msbuild-targets)。</span><span class="sxs-lookup"><span data-stu-id="e6183-159">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="e6183-160">.NET Core 工具随附了三个主要 SDK：</span><span class="sxs-lookup"><span data-stu-id="e6183-160">We ship three main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="e6183-161">ID 为 `Microsoft.NET.Sdk` 的 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e6183-161">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="e6183-162">ID 为 `Microsoft.NET.Sdk.Web` 的 .NET Core Web SDK</span><span class="sxs-lookup"><span data-stu-id="e6183-162">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="e6183-163">ID 为 `Microsoft.NET.Sdk.Razor` 的 .NET Core Razor 类库 SDK</span><span class="sxs-lookup"><span data-stu-id="e6183-163">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>

<span data-ttu-id="e6183-164">需要在 `<Project>` 元素上将 `Sdk` 属性设置为这两个 ID 之一，以使用 .NET Core 工具和生成代码。</span><span class="sxs-lookup"><span data-stu-id="e6183-164">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="e6183-165">PackageReference</span><span class="sxs-lookup"><span data-stu-id="e6183-165">PackageReference</span></span>
<span data-ttu-id="e6183-166">`<PackageReference>` 项元素指定[项目中的 NuGet 依赖项](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="e6183-166">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="e6183-167">`Include` 属性指定包 ID。</span><span class="sxs-lookup"><span data-stu-id="e6183-167">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="e6183-168">Version</span><span class="sxs-lookup"><span data-stu-id="e6183-168">Version</span></span>
<span data-ttu-id="e6183-169">所需的 `Version` 属性指定要还原的包的版本。</span><span class="sxs-lookup"><span data-stu-id="e6183-169">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="e6183-170">此属性遵循 [NuGet 版本控制](/nuget/reference/package-versioning#version-ranges-and-wildcards)方案规则。</span><span class="sxs-lookup"><span data-stu-id="e6183-170">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="e6183-171">默认行为是精确的版本匹配。</span><span class="sxs-lookup"><span data-stu-id="e6183-171">The default behavior is an exact version match.</span></span> <span data-ttu-id="e6183-172">例如，指定 `Version="1.2.3"` 等效于包的 1.2.3 版本的 NuGet 表示法 `[1.2.3]`。</span><span class="sxs-lookup"><span data-stu-id="e6183-172">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="e6183-173">IncludeAssets、ExcludeAssets 和 PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="e6183-173">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="e6183-174">`IncludeAssets` 属性指定应使用 `<PackageReference>` 指定的包中的哪些资产。</span><span class="sxs-lookup"><span data-stu-id="e6183-174">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="e6183-175">默认情况下，包含所有包资产。</span><span class="sxs-lookup"><span data-stu-id="e6183-175">By default, all package assets are included.</span></span>

<span data-ttu-id="e6183-176">`ExcludeAssets` 属性指定不应使用 `<PackageReference>` 指定的包中的哪些资产。</span><span class="sxs-lookup"><span data-stu-id="e6183-176">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="e6183-177">`PrivateAssets` 属性指定应使用 `<PackageReference>` 指定的包中的哪些资产，但不得将这些资产传递到下一个项目。</span><span class="sxs-lookup"><span data-stu-id="e6183-177">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="e6183-178">不存在此属性时，`Analyzers`、`Build` 和 `ContentFiles` 资产默认为私有。</span><span class="sxs-lookup"><span data-stu-id="e6183-178">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="e6183-179">`PrivateAssets` 等效于 *project.json*/*xproj* `SuppressParent` 元素。</span><span class="sxs-lookup"><span data-stu-id="e6183-179">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="e6183-180">这些属性可以包含以下一个或多个项，如果列出多个项，则用分号 `;` 字符进行分隔：</span><span class="sxs-lookup"><span data-stu-id="e6183-180">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

* <span data-ttu-id="e6183-181">`Compile` - 可对 lib 文件夹内容进行编译。</span><span class="sxs-lookup"><span data-stu-id="e6183-181">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="e6183-182">`Runtime` - 分发运行时文件夹内容。</span><span class="sxs-lookup"><span data-stu-id="e6183-182">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="e6183-183">`ContentFiles` - 使用 *contentfiles* 文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="e6183-183">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="e6183-184">`Build` - 使用生成文件夹中的属性/目标。</span><span class="sxs-lookup"><span data-stu-id="e6183-184">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="e6183-185">`Native` - 将本机资产内容复制到运行时输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="e6183-185">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="e6183-186">`Analyzers` - 使用分析器。</span><span class="sxs-lookup"><span data-stu-id="e6183-186">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="e6183-187">此属性也可以包含：</span><span class="sxs-lookup"><span data-stu-id="e6183-187">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="e6183-188">`None` - 不使用任何资产。</span><span class="sxs-lookup"><span data-stu-id="e6183-188">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="e6183-189">`All` - 使用所有资产。</span><span class="sxs-lookup"><span data-stu-id="e6183-189">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="e6183-190">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="e6183-190">DotNetCliToolReference</span></span>
<span data-ttu-id="e6183-191">`<DotNetCliToolReference>` 项元素指定用户想要在项目的上下文中还原的 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="e6183-191">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="e6183-192">在 *project.json* 中，它可以替换 `tools` 节点。</span><span class="sxs-lookup"><span data-stu-id="e6183-192">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="e6183-193">Version</span><span class="sxs-lookup"><span data-stu-id="e6183-193">Version</span></span>
<span data-ttu-id="e6183-194">`Version` 指定要还原的包的版本。</span><span class="sxs-lookup"><span data-stu-id="e6183-194">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="e6183-195">此属性遵循 [NuGet 版本控制](/nuget/create-packages/dependency-versions#version-ranges)方案规则。</span><span class="sxs-lookup"><span data-stu-id="e6183-195">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="e6183-196">默认行为是精确的版本匹配。</span><span class="sxs-lookup"><span data-stu-id="e6183-196">The default behavior is an exact version match.</span></span> <span data-ttu-id="e6183-197">例如，指定 `Version="1.2.3"` 等效于包的 1.2.3 版本的 NuGet 表示法 `[1.2.3]`。</span><span class="sxs-lookup"><span data-stu-id="e6183-197">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="e6183-198">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="e6183-198">RuntimeIdentifiers</span></span>
<span data-ttu-id="e6183-199">`<RuntimeIdentifiers>` 属性元素可用于指定项目的[运行时标识符 (RID)](../rid-catalog.md) 的列表（以分号分隔）。</span><span class="sxs-lookup"><span data-stu-id="e6183-199">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="e6183-200">RID 允许发布独立部署。</span><span class="sxs-lookup"><span data-stu-id="e6183-200">RIDs enable publishing self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="e6183-201">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="e6183-201">RuntimeIdentifier</span></span>
<span data-ttu-id="e6183-202">`<RuntimeIdentifier>` 属性元素可用于指定项目的唯一[运行时标识符 (RID)](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="e6183-202">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="e6183-203">RID 支持发布独立部署。</span><span class="sxs-lookup"><span data-stu-id="e6183-203">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="e6183-204">如果需要为多个运行时发布，请使用 `<RuntimeIdentifiers>`（复数）。</span><span class="sxs-lookup"><span data-stu-id="e6183-204">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="e6183-205">如果只需要单个运行时，`<RuntimeIdentifier>` 可以进行较快的生成。</span><span class="sxs-lookup"><span data-stu-id="e6183-205">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="e6183-206">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="e6183-206">PackageTargetFallback</span></span> 
<span data-ttu-id="e6183-207">`<PackageTargetFallback>` 属性元素可用于指定要在还原包时使用的一组兼容目标。</span><span class="sxs-lookup"><span data-stu-id="e6183-207">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="e6183-208">旨在允许使用 dotnet [TxM（目标 x 名字对象）](/nuget/schema/target-frameworks) 的包处理未声明 dotnet TxM 的包。</span><span class="sxs-lookup"><span data-stu-id="e6183-208">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="e6183-209">如果项目使用 dotnet TxM，那么所依赖的所有包也必须有 dotnet TxM，除非将 `<PackageTargetFallback>` 添加到项目中，以允许非 dotnet 平台与 dotnet 兼容。</span><span class="sxs-lookup"><span data-stu-id="e6183-209">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="e6183-210">以下示例展示了项目中所有目标的回退：</span><span class="sxs-lookup"><span data-stu-id="e6183-210">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="e6183-211">以下示例仅指定了 `netcoreapp2.1` 目标的回退：</span><span class="sxs-lookup"><span data-stu-id="e6183-211">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="e6183-212">NugetMetadataProperties</span><span class="sxs-lookup"><span data-stu-id="e6183-212">NuGet metadata properties</span></span>
<span data-ttu-id="e6183-213">迁移到 MSBuild 后，我们已将在打包 NuGet 包时使用的输入元数据从 project.json 移到 .csproj 文件中。</span><span class="sxs-lookup"><span data-stu-id="e6183-213">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="e6183-214">输入为 MSBuild 属性，因此它们必须转到 `<PropertyGroup>` 组中。</span><span class="sxs-lookup"><span data-stu-id="e6183-214">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="e6183-215">下面列出了在使用 `dotnet pack` 命令或属于 SDK 的 `Pack` MSBuild 目标时，用作打包进程的输入的属性。</span><span class="sxs-lookup"><span data-stu-id="e6183-215">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="e6183-216">IsPackable</span><span class="sxs-lookup"><span data-stu-id="e6183-216">IsPackable</span></span>
<span data-ttu-id="e6183-217">一个指定能否打包项目的布尔值。</span><span class="sxs-lookup"><span data-stu-id="e6183-217">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="e6183-218">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="e6183-218">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="e6183-219">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="e6183-219">PackageVersion</span></span>
<span data-ttu-id="e6183-220">指定生成的包所具有的版本。</span><span class="sxs-lookup"><span data-stu-id="e6183-220">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="e6183-221">接受所有形式的 NuGet 版本字符串。</span><span class="sxs-lookup"><span data-stu-id="e6183-221">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="e6183-222">默认为值 `$(Version)`，即项目中 `Version` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="e6183-222">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="e6183-223">PackageId</span><span class="sxs-lookup"><span data-stu-id="e6183-223">PackageId</span></span>
<span data-ttu-id="e6183-224">指定生成的包的名称。</span><span class="sxs-lookup"><span data-stu-id="e6183-224">Specifies the name for the resulting package.</span></span> <span data-ttu-id="e6183-225">如果未指定，`pack` 操作将默认使用 `AssemblyName` 或目录名称作为包的名称。</span><span class="sxs-lookup"><span data-stu-id="e6183-225">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="e6183-226">Title</span><span class="sxs-lookup"><span data-stu-id="e6183-226">Title</span></span>
<span data-ttu-id="e6183-227">明了易用的包标题，通常用在 UI 显示中，如 nuget.org 上和 Visual Studio 中包管理器上的那样。</span><span class="sxs-lookup"><span data-stu-id="e6183-227">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="e6183-228">如果未指定，则改为使用包 ID。</span><span class="sxs-lookup"><span data-stu-id="e6183-228">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="e6183-229">Authors</span><span class="sxs-lookup"><span data-stu-id="e6183-229">Authors</span></span>
<span data-ttu-id="e6183-230">其中名称以分号分隔的包作者列表，其中名称与 nuget.org 上的配置文件名称匹配。这些信息显示在 nuget.org 上的 NuGet 库中，并用于交叉引用同一作者的包。</span><span class="sxs-lookup"><span data-stu-id="e6183-230">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="e6183-231">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="e6183-231">PackageDescription</span></span>

<span data-ttu-id="e6183-232">用于 UI 显示的包的详细说明。</span><span class="sxs-lookup"><span data-stu-id="e6183-232">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="e6183-233">Description</span><span class="sxs-lookup"><span data-stu-id="e6183-233">Description</span></span>
<span data-ttu-id="e6183-234">程序集的详细说明。</span><span class="sxs-lookup"><span data-stu-id="e6183-234">A long description for the assembly.</span></span> <span data-ttu-id="e6183-235">如果未指定 `PackageDescription`，则此属性还可用作程序包的说明。</span><span class="sxs-lookup"><span data-stu-id="e6183-235">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="e6183-236">Copyright</span><span class="sxs-lookup"><span data-stu-id="e6183-236">Copyright</span></span>
<span data-ttu-id="e6183-237">包的版权详细信息。</span><span class="sxs-lookup"><span data-stu-id="e6183-237">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="e6183-238">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="e6183-238">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="e6183-239">一个布尔值，指定客户端是否必须提示使用者接受包许可证后才可安装包。</span><span class="sxs-lookup"><span data-stu-id="e6183-239">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="e6183-240">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="e6183-240">The default is `false`.</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="e6183-241">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="e6183-241">PackageLicenseExpression</span></span>

<span data-ttu-id="e6183-242">SPDX 许可证表达式或包中许可证文件的路径，通常显示在 UI 和 nuget.org 中。</span><span class="sxs-lookup"><span data-stu-id="e6183-242">An SPDX license expression or path to a license file within the package, often shown in UI displays as well as nuget.org.</span></span>

<span data-ttu-id="e6183-243">下面是 [SPDX 许可证标识符](https://spdx.org/licenses/)的完整列表。</span><span class="sxs-lookup"><span data-stu-id="e6183-243">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="e6183-244">NuGet.org 在使用许可证类型表达式时只接受 OSI 或 FSF 批准的许可证。</span><span class="sxs-lookup"><span data-stu-id="e6183-244">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="e6183-245">许可证表达式的准确语法如下面的 [ABNF](https://tools.ietf.org/html/rfc5234) 所述。</span><span class="sxs-lookup"><span data-stu-id="e6183-245">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>
```cli
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /                
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> <span data-ttu-id="e6183-246">一次只能指定 `PackageLicenseExpression`、`PackageLicenseFile` 和 `PackageLicenseUrl` 中的一个。</span><span class="sxs-lookup"><span data-stu-id="e6183-246">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="e6183-247">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="e6183-247">PackageLicenseFile</span></span>

<span data-ttu-id="e6183-248">如果使用的许可证没有分配 SPDX 标识符，或者它是自定义许可证，则它是包中许可证文件的路径（否则，优先选择 `PackageLicenseExpression`）</span><span class="sxs-lookup"><span data-stu-id="e6183-248">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is prefered)</span></span>

> [!NOTE]
> <span data-ttu-id="e6183-249">一次只能指定 `PackageLicenseExpression`、`PackageLicenseFile` 和 `PackageLicenseUrl` 中的一个。</span><span class="sxs-lookup"><span data-stu-id="e6183-249">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="e6183-250">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="e6183-250">PackageLicenseUrl</span></span>

<span data-ttu-id="e6183-251">适用于包的许可证的 URL。</span><span class="sxs-lookup"><span data-stu-id="e6183-251">An URL to the license that is applicable to the package.</span></span> <span data-ttu-id="e6183-252">（自 Visual Studio 15.9.4、.NET SDK 2.1.502 和 2.2.101 起已弃用）</span><span class="sxs-lookup"><span data-stu-id="e6183-252">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="e6183-253">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="e6183-253">PackageLicenseExpression</span></span>

<span data-ttu-id="e6183-254">[SPDX 许可证标识符](https://spdx.org/licenses/)或表达式，即 `Apache-2.0`。</span><span class="sxs-lookup"><span data-stu-id="e6183-254">An [SPDX license identifier](https://spdx.org/licenses/) or expression, i.e. `Apache-2.0`.</span></span>

<span data-ttu-id="e6183-255">替换 `PackageLicenseUrl`，不能与 `PackageLicenseFile` 结合使用，并且需要 Visual Studio 15.9.4、.NET SDK 2.1.502 或 2.2.101 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e6183-255">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseFile` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="e6183-256">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="e6183-256">PackageLicenseFile</span></span>

<span data-ttu-id="e6183-257">磁盘上许可证文件（相对于项目文件）的路径，即 `LICENSE.txt`。</span><span class="sxs-lookup"><span data-stu-id="e6183-257">A path to the license file on disk, relative to the project file, i.e. `LICENSE.txt`.</span></span>

<span data-ttu-id="e6183-258">替换 `PackageLicenseUrl`，不能与 `PackageLicenseExpression` 结合使用，并且需要 Visual Studio 15.9.4、.NET SDK 2.1.502 或 2.2.101 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e6183-258">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

<span data-ttu-id="e6183-259">将需要通过显式地将许可证文件添加到项目中来确保许可证文件已打包，示例用法如下：</span><span class="sxs-lookup"><span data-stu-id="e6183-259">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>
```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```
### <a name="packageiconurl"></a><span data-ttu-id="e6183-260">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="e6183-260">PackageIconUrl</span></span>
<span data-ttu-id="e6183-261">64x64 透明背景图像的 URL，用作 UI 显示中包的图标。</span><span class="sxs-lookup"><span data-stu-id="e6183-261">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="e6183-262">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="e6183-262">PackageReleaseNotes</span></span>
<span data-ttu-id="e6183-263">包的发行说明。</span><span class="sxs-lookup"><span data-stu-id="e6183-263">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="e6183-264">PackageTags</span><span class="sxs-lookup"><span data-stu-id="e6183-264">PackageTags</span></span>
<span data-ttu-id="e6183-265">标记的分号分隔列表，这些标记用于指定包。</span><span class="sxs-lookup"><span data-stu-id="e6183-265">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="e6183-266">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="e6183-266">PackageOutputPath</span></span>
<span data-ttu-id="e6183-267">确定用于已打包的包的输出路径。</span><span class="sxs-lookup"><span data-stu-id="e6183-267">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="e6183-268">默认值为 `$(OutputPath)`。</span><span class="sxs-lookup"><span data-stu-id="e6183-268">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="e6183-269">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="e6183-269">IncludeSymbols</span></span>
<span data-ttu-id="e6183-270">此布尔值指示在打包项目时，包是否应创建一个附加的符号包。</span><span class="sxs-lookup"><span data-stu-id="e6183-270">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="e6183-271">此包将具有 *.symbols.nupkg* 扩展名，并将 PDB 文件连同 DLL 和其他输出文件一并复制。</span><span class="sxs-lookup"><span data-stu-id="e6183-271">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="e6183-272">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="e6183-272">IncludeSource</span></span>
<span data-ttu-id="e6183-273">此布尔值指示包进程是否应创建源包。</span><span class="sxs-lookup"><span data-stu-id="e6183-273">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="e6183-274">源包中包含库的源代码以及 PDB 文件。</span><span class="sxs-lookup"><span data-stu-id="e6183-274">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="e6183-275">源文件置于生成的包文件中的 `src/ProjectName` 目录下。</span><span class="sxs-lookup"><span data-stu-id="e6183-275">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="e6183-276">IsTool</span><span class="sxs-lookup"><span data-stu-id="e6183-276">IsTool</span></span>
<span data-ttu-id="e6183-277">指定是否将所有输出文件复制到 *tools* 文件夹，而不是 *lib* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e6183-277">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="e6183-278">请注意，这不同于 `DotNetCliTool`，后者通过在 *.csproj* 文件中设置 `PackageType` 进行指定。</span><span class="sxs-lookup"><span data-stu-id="e6183-278">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="e6183-279">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="e6183-279">RepositoryUrl</span></span>
<span data-ttu-id="e6183-280">指定存储库的 URL，该存储库是包的源代码所驻留和/或生成的位置。</span><span class="sxs-lookup"><span data-stu-id="e6183-280">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="e6183-281">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="e6183-281">RepositoryType</span></span>
<span data-ttu-id="e6183-282">指定存储库的类型。</span><span class="sxs-lookup"><span data-stu-id="e6183-282">Specifies the type of the repository.</span></span> <span data-ttu-id="e6183-283">默认值为“git”。</span><span class="sxs-lookup"><span data-stu-id="e6183-283">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="e6183-284">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="e6183-284">NoPackageAnalysis</span></span>
<span data-ttu-id="e6183-285">指定 pack 不应在生成包后运行包分析。</span><span class="sxs-lookup"><span data-stu-id="e6183-285">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="e6183-286">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="e6183-286">MinClientVersion</span></span>
<span data-ttu-id="e6183-287">指定可安装此包的最低 NuGet 客户端版本，并由 nuget.exe 和 Visual Studio 程序包管理器强制实施。</span><span class="sxs-lookup"><span data-stu-id="e6183-287">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="e6183-288">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="e6183-288">IncludeBuildOutput</span></span>
<span data-ttu-id="e6183-289">此布尔值指定是否应将生成输出程序集打包到 *.nupkg* 文件中。</span><span class="sxs-lookup"><span data-stu-id="e6183-289">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="e6183-290">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="e6183-290">IncludeContentInPack</span></span>
<span data-ttu-id="e6183-291">此布尔值指定是否将含有 `Content` 类型的任何项自动包含在生成的包中。</span><span class="sxs-lookup"><span data-stu-id="e6183-291">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="e6183-292">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="e6183-292">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="e6183-293">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="e6183-293">BuildOutputTargetFolder</span></span>
<span data-ttu-id="e6183-294">指定放置输出程序集的文件夹。</span><span class="sxs-lookup"><span data-stu-id="e6183-294">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="e6183-295">输出程序集（和其他输出文件）会复制到各自的框架文件夹中。</span><span class="sxs-lookup"><span data-stu-id="e6183-295">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="e6183-296">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="e6183-296">ContentTargetFolders</span></span>
<span data-ttu-id="e6183-297">此属性指定放置所有内容文件的默认位置（如果未为其指定 `PackagePath`）。</span><span class="sxs-lookup"><span data-stu-id="e6183-297">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="e6183-298">默认值为“content;contentFiles”。</span><span class="sxs-lookup"><span data-stu-id="e6183-298">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="e6183-299">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="e6183-299">NuspecFile</span></span>
<span data-ttu-id="e6183-300">用于打包的 *.nuspec* 文件的相对或绝对路径。</span><span class="sxs-lookup"><span data-stu-id="e6183-300">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="e6183-301">如果指定了 *.nuspec* 文件，则**以独占方式**将其用于打包信息，并且不使用项目中的任何信息。</span><span class="sxs-lookup"><span data-stu-id="e6183-301">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="e6183-302">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="e6183-302">NuspecBasePath</span></span>
<span data-ttu-id="e6183-303">*.nuspec* 文件的基路径。</span><span class="sxs-lookup"><span data-stu-id="e6183-303">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="e6183-304">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="e6183-304">NuspecProperties</span></span>
<span data-ttu-id="e6183-305">键=值对的分号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="e6183-305">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="e6183-306">AssemblyInfoProperties</span><span class="sxs-lookup"><span data-stu-id="e6183-306">AssemblyInfo properties</span></span>
<span data-ttu-id="e6183-307">现在，*AssemblyInfo* 文件中通常存在的[程序集特性](../../framework/app-domains/set-assembly-attributes.md)将自动从属性生成。</span><span class="sxs-lookup"><span data-stu-id="e6183-307">[Assembly attributes](../../framework/app-domains/set-assembly-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="e6183-308">PropertiesPerAttribute</span><span class="sxs-lookup"><span data-stu-id="e6183-308">Properties per attribute</span></span>

<span data-ttu-id="e6183-309">每个特性都有一个可控制其内容的属性，还有一个可以禁用其生成的属性，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="e6183-309">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="e6183-310">特性</span><span class="sxs-lookup"><span data-stu-id="e6183-310">Attribute</span></span>                                                      | <span data-ttu-id="e6183-311">属性</span><span class="sxs-lookup"><span data-stu-id="e6183-311">Property</span></span>               | <span data-ttu-id="e6183-312">要禁用的属性</span><span class="sxs-lookup"><span data-stu-id="e6183-312">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="e6183-313">注意：</span><span class="sxs-lookup"><span data-stu-id="e6183-313">Notes:</span></span>

* <span data-ttu-id="e6183-314">`AssemblyVersion` 和 `FileVersion` 默认采用 `$(Version)` 的值而不带后缀。</span><span class="sxs-lookup"><span data-stu-id="e6183-314">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="e6183-315">例如，如果 `$(Version)` 为 `1.2.3-beta.4`，则值将为 `1.2.3`。</span><span class="sxs-lookup"><span data-stu-id="e6183-315">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* <span data-ttu-id="e6183-316">`InformationalVersion` 默认是 `$(Version)` 的值。</span><span class="sxs-lookup"><span data-stu-id="e6183-316">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
* <span data-ttu-id="e6183-317">如果存在此属性，则 `InformationalVersion` 附加 `$(SourceRevisionId)`。</span><span class="sxs-lookup"><span data-stu-id="e6183-317">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="e6183-318">可以使用 `IncludeSourceRevisionInInformationalVersion` 来禁用它。</span><span class="sxs-lookup"><span data-stu-id="e6183-318">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* <span data-ttu-id="e6183-319">`Copyright` 和 `Description` 属性也可用于 NuGet 元数据。</span><span class="sxs-lookup"><span data-stu-id="e6183-319">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
* <span data-ttu-id="e6183-320">`Configuration` 与所有生成过程共享，并通过 `dotnet` 命令的 `--configuration` 参数进行设置。</span><span class="sxs-lookup"><span data-stu-id="e6183-320">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="e6183-321">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="e6183-321">GenerateAssemblyInfo</span></span> 
<span data-ttu-id="e6183-322">一个布尔值，用于启用或禁用所有 AssemblyInfo 生成。</span><span class="sxs-lookup"><span data-stu-id="e6183-322">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="e6183-323">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="e6183-323">The default value is `true`.</span></span> 

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="e6183-324">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="e6183-324">GeneratedAssemblyInfoFile</span></span> 
<span data-ttu-id="e6183-325">生成的程序集信息文件的路径。</span><span class="sxs-lookup"><span data-stu-id="e6183-325">The path of the generated assembly info file.</span></span> <span data-ttu-id="e6183-326">默认为 `$(IntermediateOutputPath)` (obj) 目录中的某个文件。</span><span class="sxs-lookup"><span data-stu-id="e6183-326">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
