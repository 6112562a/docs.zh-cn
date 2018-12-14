---
title: .NET Core 的 csproj 格式的新增内容
description: 了解现有文件和 .NET Core csproj 文件之间的区别
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.openlocfilehash: f2ab476ee20ae90a84de7a6ccc76ce72738c1343
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143696"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="d18f8-103">.NET Core 的 csproj 格式的新增内容</span><span class="sxs-lookup"><span data-stu-id="d18f8-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="d18f8-104">本文档概述了作为从 *project.json* 移动到 *csproj* 和 [MSBuild](https://github.com/Microsoft/MSBuild) 的一部分，添加到项目文件的更改。</span><span class="sxs-lookup"><span data-stu-id="d18f8-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="d18f8-105">有关常规项目文件的语法和引用的详细信息，请参阅 [MSBuild 项目文件](/visualstudio/msbuild/msbuild-project-file-schema-reference)文档。</span><span class="sxs-lookup"><span data-stu-id="d18f8-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="d18f8-106">隐式包引用</span><span class="sxs-lookup"><span data-stu-id="d18f8-106">Implicit package references</span></span>
<span data-ttu-id="d18f8-107">基于项目文件的 `<TargetFramework>` 或 `<TargetFrameworks>` 属性中指定的目标框架对元包进行隐式引用。</span><span class="sxs-lookup"><span data-stu-id="d18f8-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="d18f8-108">如果指定了 `<TargetFramework>`，则忽略 `<TargetFrameworks>`，而与顺序无关。</span><span class="sxs-lookup"><span data-stu-id="d18f8-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="d18f8-109">建议</span><span class="sxs-lookup"><span data-stu-id="d18f8-109">Recommendations</span></span>
<span data-ttu-id="d18f8-110">由于隐式引用了 `Microsoft.NETCore.App` 或 `NetStandard.Library` 元包，以下是建议的最佳做法：</span><span class="sxs-lookup"><span data-stu-id="d18f8-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="d18f8-111">面向 .NET Core 或 .NET Standard 时，绝不通过项目文件中的 `<PackageReference>` 项，对 `Microsoft.NETCore.App` 或 `NetStandard.Library` 元包进行显式引用。</span><span class="sxs-lookup"><span data-stu-id="d18f8-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="d18f8-112">面向 .NET Core 时，如果需要特定版本的运行时，应使用项目中的 `<RuntimeFrameworkVersion>` 属性（例如，`1.0.4`），而不是引用元包。</span><span class="sxs-lookup"><span data-stu-id="d18f8-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="d18f8-113">例如，如果使用[独立部署](../deploying/index.md#self-contained-deployments-scd)且需要 1.0.0 LTS 运行时的特定修补程序版本，可能会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="d18f8-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="d18f8-114">面向 .NET Standard 时，如果需要特定版本的 `NetStandard.Library` 元包，可以使用 `<NetStandardImplicitPackageVersion>` 属性并设置所需版本。</span><span class="sxs-lookup"><span data-stu-id="d18f8-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="d18f8-115">请勿在 .NET Framework 项目中显式添加或更新对 `Microsoft.NETCore.App` 或 `NetStandard.Library` 元包的引用。</span><span class="sxs-lookup"><span data-stu-id="d18f8-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="d18f8-116">使用基于 .NET Standard 的 NuGet 包时，如果需要任意版本的 `NetStandard.Library`，NuGet 可自动安装该版本。</span><span class="sxs-lookup"><span data-stu-id="d18f8-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="d18f8-117">.NET Core 项目中默认包含的编译项</span><span class="sxs-lookup"><span data-stu-id="d18f8-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="d18f8-118">已通过移动到最新 SDK 版本中的 *csproj* 格式，将默认的编译项和嵌入资源的包含项和排除项移至 SDK 属性文件。</span><span class="sxs-lookup"><span data-stu-id="d18f8-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="d18f8-119">这意味着不需要再在项目文件中指定这些项。</span><span class="sxs-lookup"><span data-stu-id="d18f8-119">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="d18f8-120">执行此操作的主要目的是减少项目文件中的混杂。</span><span class="sxs-lookup"><span data-stu-id="d18f8-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="d18f8-121">SDK 中的默认设置应涵盖最常见的用例，由此便无需在创建的每个项目中重复这些设置。</span><span class="sxs-lookup"><span data-stu-id="d18f8-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="d18f8-122">这可使项目文件更小，更易于理解和进行手动编辑（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="d18f8-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="d18f8-123">下表显示同时在 SDK 中包含和排除的元素和 [globs](https://en.wikipedia.org/wiki/Glob_(programming))：</span><span class="sxs-lookup"><span data-stu-id="d18f8-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="d18f8-124">元素</span><span class="sxs-lookup"><span data-stu-id="d18f8-124">Element</span></span>           | <span data-ttu-id="d18f8-125">包含 glob</span><span class="sxs-lookup"><span data-stu-id="d18f8-125">Include glob</span></span>                              | <span data-ttu-id="d18f8-126">排除 glob</span><span class="sxs-lookup"><span data-stu-id="d18f8-126">Exclude glob</span></span>                                                  | <span data-ttu-id="d18f8-127">删除 glob</span><span class="sxs-lookup"><span data-stu-id="d18f8-127">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="d18f8-128">Compile</span><span class="sxs-lookup"><span data-stu-id="d18f8-128">Compile</span></span>           | <span data-ttu-id="d18f8-129">\*\*/\*.cs（或其他语言扩展名）</span><span class="sxs-lookup"><span data-stu-id="d18f8-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="d18f8-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d18f8-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="d18f8-131">不可用</span><span class="sxs-lookup"><span data-stu-id="d18f8-131">N/A</span></span>                        |
| <span data-ttu-id="d18f8-132">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="d18f8-132">EmbeddedResource</span></span>  | <span data-ttu-id="d18f8-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="d18f8-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="d18f8-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d18f8-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="d18f8-135">不可用</span><span class="sxs-lookup"><span data-stu-id="d18f8-135">N/A</span></span>                        |
| <span data-ttu-id="d18f8-136">无</span><span class="sxs-lookup"><span data-stu-id="d18f8-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="d18f8-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d18f8-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="d18f8-138">- \*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="d18f8-138">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="d18f8-139">如果项目中有 glob，却又尝试使用最新的 SDK 生成它，则将收到以下错误：</span><span class="sxs-lookup"><span data-stu-id="d18f8-139">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="d18f8-140">包含重复的编译项。</span><span class="sxs-lookup"><span data-stu-id="d18f8-140">Duplicate Compile items were included.</span></span> <span data-ttu-id="d18f8-141">默认情况下，.NET SDK 包括项目目录中的编译项。</span><span class="sxs-lookup"><span data-stu-id="d18f8-141">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="d18f8-142">可从项目文件中删除这些项，或如果想要在项目文件中显式包括它们，则将“EnableDefaultCompileItems”属性设为“false”。</span><span class="sxs-lookup"><span data-stu-id="d18f8-142">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="d18f8-143">要解决此错误，可以删除与前表中所列项匹配的显式 `Compile` 项，也可以将 `<EnableDefaultCompileItems>` 属性设置为 `false`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d18f8-143">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="d18f8-144">将此属性设置为 `false` 将替代隐式包含，且该行为将恢复到以前的 SDK，在这种情况下，必须在项目中指定默认 glob。</span><span class="sxs-lookup"><span data-stu-id="d18f8-144">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="d18f8-145">此更改不会修改其他包含项的主要机制。</span><span class="sxs-lookup"><span data-stu-id="d18f8-145">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="d18f8-146">但是，如果要指定（例如，指定某些文件通过应用发布），仍可以使用 *csproj* 中相应的已知机制来实现（例如，`<Content>` 元素）。</span><span class="sxs-lookup"><span data-stu-id="d18f8-146">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="d18f8-147">`<EnableDefaultCompileItems>` 仅禁用 `Compile` glob，但不会影响其他 glob（如隐式 `None` glob），这也适用于 \*.cs 项。</span><span class="sxs-lookup"><span data-stu-id="d18f8-147">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="d18f8-148">因此，解决方案资源管理器继续显示在项目中作为 `None` 项的 \*.cs 项。</span><span class="sxs-lookup"><span data-stu-id="d18f8-148">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="d18f8-149">可按照类似的方式使用 `<EnableDefaultNoneItems>` 禁用隐式 `None` glob。</span><span class="sxs-lookup"><span data-stu-id="d18f8-149">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="d18f8-150">要禁用所有隐式 glob，可将 `<EnableDefaultItems>` 属性设置为 `false`，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="d18f8-150">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="d18f8-151">如何像 MSBuild 一样查看整个项目</span><span class="sxs-lookup"><span data-stu-id="d18f8-151">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="d18f8-152">虽然这些 csproj 更改极大地简化了项目文件，但建议查看完全展开的项目，就像 MSBuild 查看添加了 SDK 及其目标的项目一样。</span><span class="sxs-lookup"><span data-stu-id="d18f8-152">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="d18f8-153">使用 [`dotnet msbuild`](dotnet-msbuild.md) 命令的 [`/pp` 开关](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)预处理项目，显示导入的文件、文件源及其在生成中的参与情况，而无需实际生成项目：</span><span class="sxs-lookup"><span data-stu-id="d18f8-153">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="d18f8-154">如果项目有多个目标框架，命令结果应仅侧重于框架之一，具体方法为将相应框架指定为 MSBuild 属性：</span><span class="sxs-lookup"><span data-stu-id="d18f8-154">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="d18f8-155">新增内容</span><span class="sxs-lookup"><span data-stu-id="d18f8-155">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="d18f8-156">Sdk 特性</span><span class="sxs-lookup"><span data-stu-id="d18f8-156">Sdk attribute</span></span> 
<span data-ttu-id="d18f8-157">*.csproj* 文件的 `<Project>` 元素具有名为 `Sdk` 的新特性。</span><span class="sxs-lookup"><span data-stu-id="d18f8-157">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="d18f8-158">`Sdk` 指定项目将使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="d18f8-158">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="d18f8-159">如[分层文档](cli-msbuild-architecture.md)中所述，SDK 是一组可生成 .NET Core 代码的 MSBuild [任务](/visualstudio/msbuild/msbuild-tasks)和[目标](/visualstudio/msbuild/msbuild-targets)。</span><span class="sxs-lookup"><span data-stu-id="d18f8-159">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="d18f8-160">.NET Core 工具随附了三个主要 SDK：</span><span class="sxs-lookup"><span data-stu-id="d18f8-160">We ship three main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="d18f8-161">ID 为 `Microsoft.NET.Sdk` 的 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="d18f8-161">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="d18f8-162">ID 为 `Microsoft.NET.Sdk.Web` 的 .NET Core Web SDK</span><span class="sxs-lookup"><span data-stu-id="d18f8-162">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="d18f8-163">ID 为 `Microsoft.NET.Sdk.Razor` 的 .NET Core Razor 类库 SDK</span><span class="sxs-lookup"><span data-stu-id="d18f8-163">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>

<span data-ttu-id="d18f8-164">需要在 `<Project>` 元素上将 `Sdk` 属性设置为这两个 ID 之一，以使用 .NET Core 工具和生成代码。</span><span class="sxs-lookup"><span data-stu-id="d18f8-164">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="d18f8-165">PackageReference</span><span class="sxs-lookup"><span data-stu-id="d18f8-165">PackageReference</span></span>
<span data-ttu-id="d18f8-166">用于指定项目中 NuGet 依赖项的项。</span><span class="sxs-lookup"><span data-stu-id="d18f8-166">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="d18f8-167">`Include` 属性指定包 ID。</span><span class="sxs-lookup"><span data-stu-id="d18f8-167">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="d18f8-168">版本</span><span class="sxs-lookup"><span data-stu-id="d18f8-168">Version</span></span>
<span data-ttu-id="d18f8-169">`Version` 指定要还原的包的版本。</span><span class="sxs-lookup"><span data-stu-id="d18f8-169">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="d18f8-170">此属性遵循 [NuGet 版本控制](/nuget/create-packages/dependency-versions#version-ranges)方案规则。</span><span class="sxs-lookup"><span data-stu-id="d18f8-170">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="d18f8-171">默认行为是精确的版本匹配。</span><span class="sxs-lookup"><span data-stu-id="d18f8-171">The default behavior is an exact version match.</span></span> <span data-ttu-id="d18f8-172">例如，指定 `Version="1.2.3"` 等效于包的 1.2.3 版本的 NuGet 表示法 `[1.2.3]`。</span><span class="sxs-lookup"><span data-stu-id="d18f8-172">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="d18f8-173">IncludeAssets、ExcludeAssets 和 PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="d18f8-173">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="d18f8-174">`IncludeAssets` 属性指定应使用 `<PackageReference>` 指定的包中的哪些资产。</span><span class="sxs-lookup"><span data-stu-id="d18f8-174">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="d18f8-175">`ExcludeAssets` 属性指定不应使用 `<PackageReference>` 指定的包中的哪些资产。</span><span class="sxs-lookup"><span data-stu-id="d18f8-175">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="d18f8-176">`PrivateAssets` 属性指定应使用 `<PackageReference>` 指定的包中的哪些资产，但不得将这些资产传递到下一个项目。</span><span class="sxs-lookup"><span data-stu-id="d18f8-176">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="d18f8-177">`PrivateAssets` 等效于 *project.json*/*xproj* `SuppressParent` 元素。</span><span class="sxs-lookup"><span data-stu-id="d18f8-177">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="d18f8-178">这些属性可以包含下列一个或多个项：</span><span class="sxs-lookup"><span data-stu-id="d18f8-178">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="d18f8-179">`Compile` - 可对 lib 文件夹内容进行编译。</span><span class="sxs-lookup"><span data-stu-id="d18f8-179">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="d18f8-180">`Runtime` - 分发运行时文件夹内容。</span><span class="sxs-lookup"><span data-stu-id="d18f8-180">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="d18f8-181">`ContentFiles` - 使用 *contentfiles* 文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="d18f8-181">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="d18f8-182">`Build` - 使用生成文件夹中的属性/目标。</span><span class="sxs-lookup"><span data-stu-id="d18f8-182">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="d18f8-183">`Native` - 将本机资产内容复制到运行时输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="d18f8-183">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="d18f8-184">`Analyzers` - 使用分析器。</span><span class="sxs-lookup"><span data-stu-id="d18f8-184">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="d18f8-185">此属性也可以包含：</span><span class="sxs-lookup"><span data-stu-id="d18f8-185">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="d18f8-186">`None` - 不使用任何资产。</span><span class="sxs-lookup"><span data-stu-id="d18f8-186">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="d18f8-187">`All` - 使用所有资产。</span><span class="sxs-lookup"><span data-stu-id="d18f8-187">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="d18f8-188">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="d18f8-188">DotNetCliToolReference</span></span>
<span data-ttu-id="d18f8-189">`<DotNetCliToolReference>` 项元素指定用户想要在项目的上下文中还原的 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="d18f8-189">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="d18f8-190">在 *project.json* 中，它可以替换 `tools` 节点。</span><span class="sxs-lookup"><span data-stu-id="d18f8-190">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="d18f8-191">版本</span><span class="sxs-lookup"><span data-stu-id="d18f8-191">Version</span></span>
<span data-ttu-id="d18f8-192">`Version` 指定要还原的包的版本。</span><span class="sxs-lookup"><span data-stu-id="d18f8-192">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="d18f8-193">此属性遵循 [NuGet 版本控制](/nuget/create-packages/dependency-versions#version-ranges)方案规则。</span><span class="sxs-lookup"><span data-stu-id="d18f8-193">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="d18f8-194">默认行为是精确的版本匹配。</span><span class="sxs-lookup"><span data-stu-id="d18f8-194">The default behavior is an exact version match.</span></span> <span data-ttu-id="d18f8-195">例如，指定 `Version="1.2.3"` 等效于包的 1.2.3 版本的 NuGet 表示法 `[1.2.3]`。</span><span class="sxs-lookup"><span data-stu-id="d18f8-195">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="d18f8-196">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="d18f8-196">RuntimeIdentifiers</span></span>
<span data-ttu-id="d18f8-197">`<RuntimeIdentifiers>` 元素可用于指定项目的[运行时标识符 (RID)](../rid-catalog.md) 的列表（以分号分隔）。</span><span class="sxs-lookup"><span data-stu-id="d18f8-197">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="d18f8-198">使用 RID ，可发布独立部署。</span><span class="sxs-lookup"><span data-stu-id="d18f8-198">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="d18f8-199">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="d18f8-199">RuntimeIdentifier</span></span>
<span data-ttu-id="d18f8-200">`<RuntimeIdentifier>` 元素可用于指定项目的唯一[运行时标识符 (RID)](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="d18f8-200">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="d18f8-201">使用 RID ，可发布独立部署。</span><span class="sxs-lookup"><span data-stu-id="d18f8-201">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="d18f8-202">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="d18f8-202">PackageTargetFallback</span></span> 
<span data-ttu-id="d18f8-203">`<PackageTargetFallback>` 元素可用于指定要在还原包时使用的一组兼容目标。</span><span class="sxs-lookup"><span data-stu-id="d18f8-203">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="d18f8-204">旨在允许使用 dotnet [TxM（目标 x 名字对象）](/nuget/schema/target-frameworks) 的包处理未声明 dotnet TxM 的包。</span><span class="sxs-lookup"><span data-stu-id="d18f8-204">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="d18f8-205">如果项目使用 dotnet TxM，那么所依赖的所有包也必须有 dotnet TxM，除非将 `<PackageTargetFallback>` 添加到项目中，以允许非 dotnet 平台与 dotnet 兼容。</span><span class="sxs-lookup"><span data-stu-id="d18f8-205">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="d18f8-206">以下示例展示了项目中所有目标的回退：</span><span class="sxs-lookup"><span data-stu-id="d18f8-206">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="d18f8-207">以下示例仅指定了 `netcoreapp2.1` 目标的回退：</span><span class="sxs-lookup"><span data-stu-id="d18f8-207">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="d18f8-208">NuGet 元数据属性</span><span class="sxs-lookup"><span data-stu-id="d18f8-208">NuGet metadata properties</span></span>
<span data-ttu-id="d18f8-209">迁移到 MSbuild 后，我们已将在打包 NuGet 包时使用的输入元数据从 *project.json* 移到 *.csproj* 文件中。</span><span class="sxs-lookup"><span data-stu-id="d18f8-209">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="d18f8-210">输入为 MSBuild 属性，因此它们必须转到 `<PropertyGroup>` 组中。</span><span class="sxs-lookup"><span data-stu-id="d18f8-210">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="d18f8-211">下面列出了在使用 `dotnet pack` 命令或属于 SDK 的 `Pack` MSBuild 目标时，用作打包进程的输入的属性。</span><span class="sxs-lookup"><span data-stu-id="d18f8-211">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="d18f8-212">IsPackable</span><span class="sxs-lookup"><span data-stu-id="d18f8-212">IsPackable</span></span>
<span data-ttu-id="d18f8-213">一个指定能否打包项目的布尔值。</span><span class="sxs-lookup"><span data-stu-id="d18f8-213">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="d18f8-214">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="d18f8-214">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="d18f8-215">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="d18f8-215">PackageVersion</span></span>
<span data-ttu-id="d18f8-216">指定生成的包所具有的版本。</span><span class="sxs-lookup"><span data-stu-id="d18f8-216">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="d18f8-217">接受所有形式的 NuGet 版本字符串。</span><span class="sxs-lookup"><span data-stu-id="d18f8-217">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="d18f8-218">默认为值 `$(Version)`，即项目中 `Version` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="d18f8-218">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="d18f8-219">PackageId</span><span class="sxs-lookup"><span data-stu-id="d18f8-219">PackageId</span></span>
<span data-ttu-id="d18f8-220">指定生成的包的名称。</span><span class="sxs-lookup"><span data-stu-id="d18f8-220">Specifies the name for the resulting package.</span></span> <span data-ttu-id="d18f8-221">如果未指定，`pack` 操作将默认使用 `AssemblyName` 或目录名称作为包的名称。</span><span class="sxs-lookup"><span data-stu-id="d18f8-221">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="d18f8-222">标题</span><span class="sxs-lookup"><span data-stu-id="d18f8-222">Title</span></span>
<span data-ttu-id="d18f8-223">明了易用的包标题，通常用在 UI 显示中，如 nuget.org 上和 Visual Studio 中包管理器上的那样。</span><span class="sxs-lookup"><span data-stu-id="d18f8-223">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="d18f8-224">如果未指定，则改为使用包 ID。</span><span class="sxs-lookup"><span data-stu-id="d18f8-224">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="d18f8-225">作者</span><span class="sxs-lookup"><span data-stu-id="d18f8-225">Authors</span></span>
<span data-ttu-id="d18f8-226">其中名称以分号分隔的包作者列表，其中名称与 nuget.org 上的配置文件名称匹配。这些信息显示在 nuget.org 上的 NuGet 库中，并用于交叉引用同一作者的包。</span><span class="sxs-lookup"><span data-stu-id="d18f8-226">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="d18f8-227">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="d18f8-227">PackageDescription</span></span>

<span data-ttu-id="d18f8-228">用于 UI 显示的包的详细说明。</span><span class="sxs-lookup"><span data-stu-id="d18f8-228">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="d18f8-229">说明</span><span class="sxs-lookup"><span data-stu-id="d18f8-229">Description</span></span>
<span data-ttu-id="d18f8-230">程序集的详细说明。</span><span class="sxs-lookup"><span data-stu-id="d18f8-230">A long description for the assembly.</span></span> <span data-ttu-id="d18f8-231">如果未指定 `PackageDescription`，则此属性还可用作程序包的说明。</span><span class="sxs-lookup"><span data-stu-id="d18f8-231">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="d18f8-232">Copyright</span><span class="sxs-lookup"><span data-stu-id="d18f8-232">Copyright</span></span>
<span data-ttu-id="d18f8-233">包的版权详细信息。</span><span class="sxs-lookup"><span data-stu-id="d18f8-233">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="d18f8-234">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="d18f8-234">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="d18f8-235">一个布尔值，指定客户端是否必须提示使用者接受包许可证后才可安装包。</span><span class="sxs-lookup"><span data-stu-id="d18f8-235">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="d18f8-236">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="d18f8-236">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="d18f8-237">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="d18f8-237">PackageLicenseUrl</span></span>
<span data-ttu-id="d18f8-238">适用于包的许可证的 URL。</span><span class="sxs-lookup"><span data-stu-id="d18f8-238">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="d18f8-239">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="d18f8-239">PackageProjectUrl</span></span>
<span data-ttu-id="d18f8-240">包的主页 URL，通常显示在 UI 中以及 nuget.org 中。</span><span class="sxs-lookup"><span data-stu-id="d18f8-240">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="d18f8-241">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="d18f8-241">PackageIconUrl</span></span>
<span data-ttu-id="d18f8-242">64x64 透明背景图像的 URL，用作 UI 显示中包的图标。</span><span class="sxs-lookup"><span data-stu-id="d18f8-242">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="d18f8-243">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="d18f8-243">PackageReleaseNotes</span></span>
<span data-ttu-id="d18f8-244">包的发行说明。</span><span class="sxs-lookup"><span data-stu-id="d18f8-244">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="d18f8-245">PackageTags</span><span class="sxs-lookup"><span data-stu-id="d18f8-245">PackageTags</span></span>
<span data-ttu-id="d18f8-246">标记的分号分隔列表，这些标记用于指定包。</span><span class="sxs-lookup"><span data-stu-id="d18f8-246">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="d18f8-247">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="d18f8-247">PackageOutputPath</span></span>
<span data-ttu-id="d18f8-248">确定用于已打包的包的输出路径。</span><span class="sxs-lookup"><span data-stu-id="d18f8-248">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="d18f8-249">默认值为 `$(OutputPath)`。</span><span class="sxs-lookup"><span data-stu-id="d18f8-249">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="d18f8-250">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="d18f8-250">IncludeSymbols</span></span>
<span data-ttu-id="d18f8-251">此布尔值指示在打包项目时，包是否应创建一个附加的符号包。</span><span class="sxs-lookup"><span data-stu-id="d18f8-251">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="d18f8-252">此包将具有 *.symbols.nupkg* 扩展名，并将 PDB 文件连同 DLL 和其他输出文件一并复制。</span><span class="sxs-lookup"><span data-stu-id="d18f8-252">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="d18f8-253">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="d18f8-253">IncludeSource</span></span>
<span data-ttu-id="d18f8-254">此布尔值指示包进程是否应创建源包。</span><span class="sxs-lookup"><span data-stu-id="d18f8-254">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="d18f8-255">源包中包含库的源代码以及 PDB 文件。</span><span class="sxs-lookup"><span data-stu-id="d18f8-255">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="d18f8-256">源文件置于生成的包文件中的 `src/ProjectName` 目录下。</span><span class="sxs-lookup"><span data-stu-id="d18f8-256">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="d18f8-257">IsTool</span><span class="sxs-lookup"><span data-stu-id="d18f8-257">IsTool</span></span>
<span data-ttu-id="d18f8-258">指定是否将所有输出文件复制到 *tools* 文件夹，而不是 *lib* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="d18f8-258">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="d18f8-259">请注意，这不同于 `DotNetCliTool`，后者通过在 *.csproj* 文件中设置 `PackageType` 进行指定。</span><span class="sxs-lookup"><span data-stu-id="d18f8-259">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="d18f8-260">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="d18f8-260">RepositoryUrl</span></span>
<span data-ttu-id="d18f8-261">指定存储库的 URL，该存储库是包的源代码所驻留和/或生成的位置。</span><span class="sxs-lookup"><span data-stu-id="d18f8-261">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="d18f8-262">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="d18f8-262">RepositoryType</span></span>
<span data-ttu-id="d18f8-263">指定存储库的类型。</span><span class="sxs-lookup"><span data-stu-id="d18f8-263">Specifies the type of the repository.</span></span> <span data-ttu-id="d18f8-264">默认值为“git”。</span><span class="sxs-lookup"><span data-stu-id="d18f8-264">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="d18f8-265">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="d18f8-265">NoPackageAnalysis</span></span>
<span data-ttu-id="d18f8-266">指定 pack 不应在生成包后运行包分析。</span><span class="sxs-lookup"><span data-stu-id="d18f8-266">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="d18f8-267">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="d18f8-267">MinClientVersion</span></span>
<span data-ttu-id="d18f8-268">指定可安装此包的最低 NuGet 客户端版本，并由 nuget.exe 和 Visual Studio 程序包管理器强制实施。</span><span class="sxs-lookup"><span data-stu-id="d18f8-268">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="d18f8-269">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="d18f8-269">IncludeBuildOutput</span></span>
<span data-ttu-id="d18f8-270">此布尔值指定是否应将生成输出程序集打包到 *.nupkg* 文件中。</span><span class="sxs-lookup"><span data-stu-id="d18f8-270">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="d18f8-271">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="d18f8-271">IncludeContentInPack</span></span>
<span data-ttu-id="d18f8-272">此布尔值指定是否将含有 `Content` 类型的任何项自动包含在生成的包中。</span><span class="sxs-lookup"><span data-stu-id="d18f8-272">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="d18f8-273">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="d18f8-273">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="d18f8-274">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="d18f8-274">BuildOutputTargetFolder</span></span>
<span data-ttu-id="d18f8-275">指定放置输出程序集的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d18f8-275">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="d18f8-276">输出程序集（和其他输出文件）会复制到各自的框架文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d18f8-276">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="d18f8-277">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="d18f8-277">ContentTargetFolders</span></span>
<span data-ttu-id="d18f8-278">此属性指定放置所有内容文件的默认位置（如果未为其指定 `PackagePath`）。</span><span class="sxs-lookup"><span data-stu-id="d18f8-278">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="d18f8-279">默认值为“content;contentFiles”。</span><span class="sxs-lookup"><span data-stu-id="d18f8-279">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="d18f8-280">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="d18f8-280">NuspecFile</span></span>
<span data-ttu-id="d18f8-281">用于打包的 *.nuspec* 文件的相对或绝对路径。</span><span class="sxs-lookup"><span data-stu-id="d18f8-281">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="d18f8-282">如果指定了 *.nuspec* 文件，则**以独占方式**将其用于打包信息，并且不使用项目中的任何信息。</span><span class="sxs-lookup"><span data-stu-id="d18f8-282">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="d18f8-283">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="d18f8-283">NuspecBasePath</span></span>
<span data-ttu-id="d18f8-284">*.nuspec* 文件的基路径。</span><span class="sxs-lookup"><span data-stu-id="d18f8-284">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="d18f8-285">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="d18f8-285">NuspecProperties</span></span>
<span data-ttu-id="d18f8-286">键=值对的分号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="d18f8-286">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="d18f8-287">AssemblyInfo 属性</span><span class="sxs-lookup"><span data-stu-id="d18f8-287">AssemblyInfo properties</span></span>
<span data-ttu-id="d18f8-288">现在，*AssemblyInfo* 文件中通常存在的[程序集特性](../../framework/app-domains/set-assembly-attributes.md)将自动从属性生成。</span><span class="sxs-lookup"><span data-stu-id="d18f8-288">[Assembly attributes](../../framework/app-domains/set-assembly-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="d18f8-289">每个特性的属性</span><span class="sxs-lookup"><span data-stu-id="d18f8-289">Properties per attribute</span></span>

<span data-ttu-id="d18f8-290">每个特性都有一个可控制其内容的属性，还有一个可以禁用其生成的属性，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="d18f8-290">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="d18f8-291">特性</span><span class="sxs-lookup"><span data-stu-id="d18f8-291">Attribute</span></span>                                                      | <span data-ttu-id="d18f8-292">属性</span><span class="sxs-lookup"><span data-stu-id="d18f8-292">Property</span></span>               | <span data-ttu-id="d18f8-293">要禁用的属性</span><span class="sxs-lookup"><span data-stu-id="d18f8-293">Property to disable</span></span>                             |
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

<span data-ttu-id="d18f8-294">注意：</span><span class="sxs-lookup"><span data-stu-id="d18f8-294">Notes:</span></span>

* <span data-ttu-id="d18f8-295">`AssemblyVersion` 和 `FileVersion` 默认采用 `$(Version)` 的值而不带后缀。</span><span class="sxs-lookup"><span data-stu-id="d18f8-295">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="d18f8-296">例如，如果 `$(Version)` 为 `1.2.3-beta.4`，则值将为 `1.2.3`。</span><span class="sxs-lookup"><span data-stu-id="d18f8-296">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* <span data-ttu-id="d18f8-297">`InformationalVersion` 默认是 `$(Version)` 的值。</span><span class="sxs-lookup"><span data-stu-id="d18f8-297">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
* <span data-ttu-id="d18f8-298">如果存在此属性，则 `InformationalVersion` 附加 `$(SourceRevisionId)`。</span><span class="sxs-lookup"><span data-stu-id="d18f8-298">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="d18f8-299">可以使用 `IncludeSourceRevisionInInformationalVersion` 来禁用它。</span><span class="sxs-lookup"><span data-stu-id="d18f8-299">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* <span data-ttu-id="d18f8-300">`Copyright` 和 `Description` 属性也可用于 NuGet 元数据。</span><span class="sxs-lookup"><span data-stu-id="d18f8-300">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
* <span data-ttu-id="d18f8-301">`Configuration` 与所有生成过程共享，并通过 `dotnet` 命令的 `--configuration` 参数进行设置。</span><span class="sxs-lookup"><span data-stu-id="d18f8-301">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="d18f8-302">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="d18f8-302">GenerateAssemblyInfo</span></span> 
<span data-ttu-id="d18f8-303">一个布尔值，用于启用或禁用所有 AssemblyInfo 生成。</span><span class="sxs-lookup"><span data-stu-id="d18f8-303">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="d18f8-304">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="d18f8-304">The default value is `true`.</span></span> 

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="d18f8-305">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="d18f8-305">GeneratedAssemblyInfoFile</span></span> 
<span data-ttu-id="d18f8-306">生成的程序集信息文件的路径。</span><span class="sxs-lookup"><span data-stu-id="d18f8-306">The path of the generated assembly info file.</span></span> <span data-ttu-id="d18f8-307">默认为 `$(IntermediateOutputPath)` (obj) 目录中的某个文件。</span><span class="sxs-lookup"><span data-stu-id="d18f8-307">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
