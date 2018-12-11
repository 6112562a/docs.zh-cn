---
title: 如何对 .NET Core 运行时和 SDK 进行版本控制
description: 本文介绍了 .NET Core SDK 和运行时的版本控制方式（类似于语义版本控制）。
author: bleroy
ms.date: 07/26/2018
ms.custom: seodec18
ms.openlocfilehash: 54b09a6b74b2cf213cea781dec95a413ac2ad059
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170712"
---
# <a name="overview-of-how-net-core-is-versioned"></a><span data-ttu-id="a38ac-103">.NET Core 的版本控制方式概述</span><span class="sxs-lookup"><span data-stu-id="a38ac-103">Overview of how .NET Core is versioned</span></span>

<span data-ttu-id="a38ac-104">.NET Core 是指 .NET Core 运行时和 .NET Core SDK，它包含开发应用程序所需的工具。</span><span class="sxs-lookup"><span data-stu-id="a38ac-104">.NET Core refers to the .NET Core Runtime and the .NET Core SDK, which contains the tools you need to develop applications.</span></span> <span data-ttu-id="a38ac-105">.NET Core SDK 可与任何以前版本的 .NET Core 运行时一起使用。</span><span class="sxs-lookup"><span data-stu-id="a38ac-105">.NET Core SDKs are designed to work with any previous version of the .NET Core Runtime.</span></span> <span data-ttu-id="a38ac-106">本文介绍运行时和 SDK 版本策略。</span><span class="sxs-lookup"><span data-stu-id="a38ac-106">This article explains the runtime and the SDK version strategy.</span></span> <span data-ttu-id="a38ac-107">有关 .NET Standard 版本号的说明，请参阅介绍 [.NET Standar](../../standard/net-standard.md#net-implementation-support) 的文章。</span><span class="sxs-lookup"><span data-stu-id="a38ac-107">An explanation of version numbers for .NET Standard can be found in the article introducing [.NET Standard](../../standard/net-standard.md#net-implementation-support).</span></span>

<span data-ttu-id="a38ac-108">.NET Core 运行时和 .NET Core SDK 以不同的速率添加新功能，通常情况下，.NET Core SDK 提供更新工具的速度比 .NET Core 运行时更改生产中所用运行时的速度快。</span><span class="sxs-lookup"><span data-stu-id="a38ac-108">The .NET Core Runtime and .NET Core SDK add new features at a different rate - in general the .NET Core SDK provides updated tools more quickly than the .NET Core Runtime changes the runtime you use in production.</span></span> <span data-ttu-id="a38ac-109">但麻烦的是，这个问题导致过去几年出现了多种版本控制策略。</span><span class="sxs-lookup"><span data-stu-id="a38ac-109">Unfortunately, this problem has resulted in several versioning strategies over the last few years.</span></span> <span data-ttu-id="a38ac-110">可在有关 [.NET Core 版本控制](version-history.md)的文章中了解相关历史记录。</span><span class="sxs-lookup"><span data-stu-id="a38ac-110">You can learn about the history in the article on [.NET Core versioning](version-history.md).</span></span>

## <a name="versioning-details"></a><span data-ttu-id="a38ac-111">版本控制详细信息</span><span class="sxs-lookup"><span data-stu-id="a38ac-111">Versioning details</span></span>

<span data-ttu-id="a38ac-112">“.NET Core 2.1”是指 .NET Core 运行时版本号。</span><span class="sxs-lookup"><span data-stu-id="a38ac-112">".NET Core 2.1" refers to the .NET Core Runtime version number.</span></span> <span data-ttu-id="a38ac-113">.NET Core 运行时用于版本控制的主要/次要/补丁方法需遵循[语义版本控制](#semantic-versioning)。</span><span class="sxs-lookup"><span data-stu-id="a38ac-113">The .NET Core Runtime has a major/minor/patch approach to versioning that follows [semantic versioning](#semantic-versioning).</span></span>

<span data-ttu-id="a38ac-114">.NET Core SDK 不遵循语义版本控制。</span><span class="sxs-lookup"><span data-stu-id="a38ac-114">The .NET Core SDK doesn't follow semantic versioning.</span></span> <span data-ttu-id="a38ac-115">.NET Core SDK 发布速度更快，其版本必须传达相应的运行时和 SDK 自己的次要版本和修补程序版本。</span><span class="sxs-lookup"><span data-stu-id="a38ac-115">The .NET Core SDK releases faster and its versions must communicate both the aligned runtime and the SDK's own minor and patch releases.</span></span> <span data-ttu-id="a38ac-116">.NET Core SDK 版本的前两个位置被锁定到与之一起发布的 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="a38ac-116">The first two positions of the .NET Core SDK version are locked to the .NET Core Runtime it released with.</span></span> <span data-ttu-id="a38ac-117">每个版本的 SDK 都可以为此版本或任何更低版本的运行时创建应用程序。</span><span class="sxs-lookup"><span data-stu-id="a38ac-117">Each version of the SDK can create applications for this runtime or any lower version.</span></span>

<span data-ttu-id="a38ac-118">SDK 版本号的第三个位置同时传达次要编号和修补程序编号。</span><span class="sxs-lookup"><span data-stu-id="a38ac-118">The third position of the SDK version number communicates both the minor and patch number.</span></span> <span data-ttu-id="a38ac-119">次要版本乘以 100。</span><span class="sxs-lookup"><span data-stu-id="a38ac-119">The minor version is multiplied by 100.</span></span> <span data-ttu-id="a38ac-120">次要版本 1，修补程序版本 2 将表示为 102。</span><span class="sxs-lookup"><span data-stu-id="a38ac-120">Minor version 1, patch version 2 would be represented as 102.</span></span> <span data-ttu-id="a38ac-121">最后两位数代表修补程序号。</span><span class="sxs-lookup"><span data-stu-id="a38ac-121">The final two digits represent the patch number.</span></span> <span data-ttu-id="a38ac-122">例如，.NET Core 2.2 可能会创建如下表所示的版本：</span><span class="sxs-lookup"><span data-stu-id="a38ac-122">For example, the release of .NET Core 2.2 may create releases like the following table:</span></span>

| <span data-ttu-id="a38ac-123">更改</span><span class="sxs-lookup"><span data-stu-id="a38ac-123">Change</span></span>                | <span data-ttu-id="a38ac-124">.NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="a38ac-124">.NET Core Runtime</span></span> | <span data-ttu-id="a38ac-125">.NET Core SDK (\*)</span><span class="sxs-lookup"><span data-stu-id="a38ac-125">.NET Core SDK (\*)</span></span> |
|-----------------------|-------------------|-------------------|
| <span data-ttu-id="a38ac-126">初始版本</span><span class="sxs-lookup"><span data-stu-id="a38ac-126">Initial release</span></span>       | <span data-ttu-id="a38ac-127">2.2.0</span><span class="sxs-lookup"><span data-stu-id="a38ac-127">2.2.0</span></span>             | <span data-ttu-id="a38ac-128">2.2.100</span><span class="sxs-lookup"><span data-stu-id="a38ac-128">2.2.100</span></span>           |
| <span data-ttu-id="a38ac-129">SDK 修补程序</span><span class="sxs-lookup"><span data-stu-id="a38ac-129">SDK Patch</span></span>             | <span data-ttu-id="a38ac-130">2.2.0</span><span class="sxs-lookup"><span data-stu-id="a38ac-130">2.2.0</span></span>             | <span data-ttu-id="a38ac-131">2.2.101</span><span class="sxs-lookup"><span data-stu-id="a38ac-131">2.2.101</span></span>           |
| <span data-ttu-id="a38ac-132">运行时和 SDK 修补程序</span><span class="sxs-lookup"><span data-stu-id="a38ac-132">Runtime and SDK Patch</span></span> | <span data-ttu-id="a38ac-133">2.2.1</span><span class="sxs-lookup"><span data-stu-id="a38ac-133">2.2.1</span></span>             | <span data-ttu-id="a38ac-134">2.2.102</span><span class="sxs-lookup"><span data-stu-id="a38ac-134">2.2.102</span></span>           |
| <span data-ttu-id="a38ac-135">SDK 功能更改</span><span class="sxs-lookup"><span data-stu-id="a38ac-135">SDK Feature change</span></span>    | <span data-ttu-id="a38ac-136">2.2.1</span><span class="sxs-lookup"><span data-stu-id="a38ac-136">2.2.1</span></span>             | <span data-ttu-id="a38ac-137">2.2.200</span><span class="sxs-lookup"><span data-stu-id="a38ac-137">2.2.200</span></span>           |

<span data-ttu-id="a38ac-138">(\*) 此图表以未来的 2.2 .NET Core 运行时示例，因为历史项目 .NET Core 2.1 的第一个 SDK 是 2.1.300。</span><span class="sxs-lookup"><span data-stu-id="a38ac-138">(\*) This chart uses a future 2.2 .NET Core Runtime as the example because a historic artifact meant the first SDK for .NET Core 2.1 is 2.1.300.</span></span> <span data-ttu-id="a38ac-139">有关详细信息，请参阅 [.NET Core 版本控制历史记录](version-history.md)。</span><span class="sxs-lookup"><span data-stu-id="a38ac-139">For more information, See the [history of .NET Core versioning](version-history.md).</span></span>

<span data-ttu-id="a38ac-140">注意：</span><span class="sxs-lookup"><span data-stu-id="a38ac-140">NOTES:</span></span>

* <span data-ttu-id="a38ac-141">如果在运行时功能更新之前，SDK 有 10 个功能更新，则版本号将滚动到 1000 系列，2.2.1000 等编号为 2.2.900 之后的功能版本。</span><span class="sxs-lookup"><span data-stu-id="a38ac-141">If the SDK has 10 feature updates before a runtime feature update, version numbers roll into the 1000 series with numbers like 2.2.1000 as the feature release following 2.2.900.</span></span> <span data-ttu-id="a38ac-142">应该不会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="a38ac-142">This situation isn't expected to occur.</span></span>
* <span data-ttu-id="a38ac-143">不会出现为发布功能的 99 修补程序版本。</span><span class="sxs-lookup"><span data-stu-id="a38ac-143">99 patch releases without a feature release won't occur.</span></span> <span data-ttu-id="a38ac-144">如果某版本接近此数字，则会强制发布功能。</span><span class="sxs-lookup"><span data-stu-id="a38ac-144">If a release approaches this number, it forces a feature release.</span></span>

<span data-ttu-id="a38ac-145">可在 [dotnet/设计](https://github.com/dotnet/designs/pull/29) 存储库中查看初始建议的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="a38ac-145">You can see more details in the initial proposal at the [dotnet/designs](https://github.com/dotnet/designs/pull/29) repository.</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="a38ac-146">语义化版本控制</span><span class="sxs-lookup"><span data-stu-id="a38ac-146">Semantic versioning</span></span>

<span data-ttu-id="a38ac-147">.NET Core 运行时大致遵循[语义版本控制 (SemVer)](https://semver.org/)，采用 `MAJOR.MINOR.PATCH` 版本控制，通过版本号的各部分来描述更改程度和类型。</span><span class="sxs-lookup"><span data-stu-id="a38ac-147">The .NET Core *Runtime* roughly adheres to [Semantic Versioning (SemVer)](https://semver.org/), adopting the use of `MAJOR.MINOR.PATCH` versioning, using the various parts of the version number to describe the degree and type of change.</span></span>

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

<span data-ttu-id="a38ac-148">可选的 `PRERELEASE` 和 `BUILDNUMBER` 部分永远不会成为受支持版本的一部分，并且将仅存在于夜间版本、来自源目标的本地版本，以及不受支持的预览版本中。</span><span class="sxs-lookup"><span data-stu-id="a38ac-148">The optional `PRERELEASE` and `BUILDNUMBER` parts are never part of supported releases and only exist on nightly builds, local builds from source targets, and unsupported preview releases.</span></span>

### <a name="understand-runtime-version-number-changes"></a><span data-ttu-id="a38ac-149">了解运行时版本号更改</span><span class="sxs-lookup"><span data-stu-id="a38ac-149">Understand runtime version number changes</span></span>

<span data-ttu-id="a38ac-150">`MAJOR` 在下列情况时递增：</span><span class="sxs-lookup"><span data-stu-id="a38ac-150">`MAJOR` is incremented when:</span></span>

* <span data-ttu-id="a38ac-151">产品或新产品方向发生重大更改。</span><span class="sxs-lookup"><span data-stu-id="a38ac-151">Significant changes occur to the product, or a new product direction.</span></span>
* <span data-ttu-id="a38ac-152">发生了中断性变更。</span><span class="sxs-lookup"><span data-stu-id="a38ac-152">Breaking changes were taken.</span></span> <span data-ttu-id="a38ac-153">接受中断性变更存在较大障碍。</span><span class="sxs-lookup"><span data-stu-id="a38ac-153">There's a high bar to accepting breaking changes.</span></span>
* <span data-ttu-id="a38ac-154">旧版本不再受支持。</span><span class="sxs-lookup"><span data-stu-id="a38ac-154">An old version is no longer supported.</span></span>
* <span data-ttu-id="a38ac-155">采用了现有依赖项的较新 `MAJOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="a38ac-155">A newer `MAJOR` version of an existing dependency is adopted.</span></span>

<span data-ttu-id="a38ac-156">`MINOR` 在下列情况时递增：</span><span class="sxs-lookup"><span data-stu-id="a38ac-156">`MINOR` is incremented when:</span></span>

* <span data-ttu-id="a38ac-157">添加了公共 API 外围应用。</span><span class="sxs-lookup"><span data-stu-id="a38ac-157">Public API surface area is added.</span></span>
* <span data-ttu-id="a38ac-158">添加了新行为。</span><span class="sxs-lookup"><span data-stu-id="a38ac-158">A new behavior is added.</span></span>
* <span data-ttu-id="a38ac-159">采用了现有依赖项的较新 `MINOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="a38ac-159">A newer `MINOR` version of an existing dependency is adopted.</span></span>
* <span data-ttu-id="a38ac-160">引入了新依赖项。</span><span class="sxs-lookup"><span data-stu-id="a38ac-160">A new dependency is introduced.</span></span>

<span data-ttu-id="a38ac-161">`PATCH` 在下列情况时递增：</span><span class="sxs-lookup"><span data-stu-id="a38ac-161">`PATCH` is incremented when:</span></span>

* <span data-ttu-id="a38ac-162">进行了 Bug 修复。</span><span class="sxs-lookup"><span data-stu-id="a38ac-162">Bug fixes are made.</span></span>
* <span data-ttu-id="a38ac-163">添加了对较新平台的支持。</span><span class="sxs-lookup"><span data-stu-id="a38ac-163">Support for a newer platform is added.</span></span>
* <span data-ttu-id="a38ac-164">采用了现有依赖项的较新 `PATCH` 版本。</span><span class="sxs-lookup"><span data-stu-id="a38ac-164">A newer `PATCH` version of an existing dependency is adopted.</span></span>
* <span data-ttu-id="a38ac-165">任何其他不符合上述情况的更改。</span><span class="sxs-lookup"><span data-stu-id="a38ac-165">Any other change doesn't fit one of the previous cases.</span></span>

<span data-ttu-id="a38ac-166">存在多处更改时，单个更改影响的最高级别元素会递增，并将随后的元素重置为零。</span><span class="sxs-lookup"><span data-stu-id="a38ac-166">When there are multiple changes, the highest element affected by individual changes is incremented, and the following ones are reset to zero.</span></span> <span data-ttu-id="a38ac-167">例如，当 `MAJOR` 递增时，`MINOR` 和 `PATCH` 将重置为零。</span><span class="sxs-lookup"><span data-stu-id="a38ac-167">For example, when `MAJOR` is incremented, `MINOR` and `PATCH` are reset to zero.</span></span> <span data-ttu-id="a38ac-168">当 `MINOR` 递增时，`PATCH` 将重置为零，而 `MAJOR` 保持不变。</span><span class="sxs-lookup"><span data-stu-id="a38ac-168">When `MINOR` is incremented, `PATCH` is reset to zero while `MAJOR` is left untouched.</span></span>

## <a name="version-numbers-in-file-names"></a><span data-ttu-id="a38ac-169">文件名中的版本号</span><span class="sxs-lookup"><span data-stu-id="a38ac-169">Version numbers in file names</span></span>

<span data-ttu-id="a38ac-170">为 .NET Core 下载的文件带有版本，例如 `dotnet-sdk-2.1.300-win10-x64.exe`。</span><span class="sxs-lookup"><span data-stu-id="a38ac-170">The files downloaded for .NET Core carry the version, for example, `dotnet-sdk-2.1.300-win10-x64.exe`.</span></span>

### <a name="preview-versions"></a><span data-ttu-id="a38ac-171">预览版</span><span class="sxs-lookup"><span data-stu-id="a38ac-171">Preview versions</span></span>

<span data-ttu-id="a38ac-172">预览版向版本中追加了 `-preview[number]-([build]|"final")`。</span><span class="sxs-lookup"><span data-stu-id="a38ac-172">Preview versions have a `-preview[number]-([build]|"final")` appended to the version.</span></span> <span data-ttu-id="a38ac-173">例如 `2.0.0-preview1-final`。</span><span class="sxs-lookup"><span data-stu-id="a38ac-173">For example, `2.0.0-preview1-final`.</span></span>

### <a name="servicing-versions"></a><span data-ttu-id="a38ac-174">服务版本</span><span class="sxs-lookup"><span data-stu-id="a38ac-174">Servicing versions</span></span>

<span data-ttu-id="a38ac-175">在版本发布后，版本分支通常停止生成日常版本，而开始生成服务版本。</span><span class="sxs-lookup"><span data-stu-id="a38ac-175">After a release goes out, the release branches generally stop producing daily builds and instead start producing servicing builds.</span></span> <span data-ttu-id="a38ac-176">服务版本向版本追加了 `-servicing-[number]`。</span><span class="sxs-lookup"><span data-stu-id="a38ac-176">Servicing versions have a `-servicing-[number]` appended to the version.</span></span> <span data-ttu-id="a38ac-177">例如 `2.0.1-servicing-006924`。</span><span class="sxs-lookup"><span data-stu-id="a38ac-177">For example, `2.0.1-servicing-006924`.</span></span>

## <a name="relationship-to-net-standard-versions"></a><span data-ttu-id="a38ac-178">与 .NET Standard 版本的关系</span><span class="sxs-lookup"><span data-stu-id="a38ac-178">Relationship to .NET Standard versions</span></span>

<span data-ttu-id="a38ac-179">.NET Standard 由 .NET 引用程序集组成。</span><span class="sxs-lookup"><span data-stu-id="a38ac-179">.NET Standard consists of a .NET reference assembly.</span></span> <span data-ttu-id="a38ac-180">每个平台都有多个特定的实现。</span><span class="sxs-lookup"><span data-stu-id="a38ac-180">There are multiple implementations specific to each platform.</span></span> <span data-ttu-id="a38ac-181">引用程序集包含 .NET API 的定义，后者是给定 .NET Standard 版本的一部分。</span><span class="sxs-lookup"><span data-stu-id="a38ac-181">The reference assembly contains the definition of .NET APIs which are part of a given .NET Standard version.</span></span> <span data-ttu-id="a38ac-182">每个实现均满足特定平台上的 .NET Standard 协定。</span><span class="sxs-lookup"><span data-stu-id="a38ac-182">Each implementation fulfills the .NET Standard contract on the specific platform.</span></span> <span data-ttu-id="a38ac-183">可参阅 .NET 指南中有关 [.NET Standard](../../standard/net-standard.md) 的文章，深入了解 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="a38ac-183">You can learn more about .NET Standard in the article on [.NET Standard](../../standard/net-standard.md) in the .NET Guide.</span></span>

<span data-ttu-id="a38ac-184">.NET Standard 引用程序集使用 `MAJOR.MINOR` 版本控制方案。</span><span class="sxs-lookup"><span data-stu-id="a38ac-184">The .NET Standard reference assembly uses a `MAJOR.MINOR` versioning scheme.</span></span> <span data-ttu-id="a38ac-185">`PATCH` 级别对 .NET Standard 并无用处，因为它只公开 API 规范（没有实现），并且根据定义，对 API 的任何更改都将作为功能集的更改，从进而产生新的 `MINOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="a38ac-185">`PATCH` level isn't useful for .NET Standard because it exposes only an API specification (no implementation) and by definition any change to the API would represent a change in the feature set, and thus a new `MINOR` version.</span></span>

<span data-ttu-id="a38ac-186">每个平台上的实现通常可作为平台版本的一部分更新，因此对于在该平台上使用 .NET Standard 的程序员来说并不明显。</span><span class="sxs-lookup"><span data-stu-id="a38ac-186">The implementations on each platform may be updated, typically as part of the platform release, and thus not evident to the programmers using .NET Standard on that platform.</span></span>

<span data-ttu-id="a38ac-187">每个版本的 .NET Core 都实现了某一版本的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="a38ac-187">Each version of .NET Core implements a version of .NET Standard.</span></span> <span data-ttu-id="a38ac-188">实现某一版本的 .NET Standard 意味着支持以前版本的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="a38ac-188">Implementing a version of .NET Standard implies support for previous versions of .NET Standard.</span></span> <span data-ttu-id="a38ac-189">.NET Standard 和 .NET Core 版本独立。</span><span class="sxs-lookup"><span data-stu-id="a38ac-189">.NET Standard and .NET Core version independently.</span></span> <span data-ttu-id="a38ac-190">.NET Core 2.0 实现 .NET Standard 2.0 是巧合。</span><span class="sxs-lookup"><span data-stu-id="a38ac-190">It's a coincidence that .NET Core 2.0 implements .NET Standard 2.0.</span></span> <span data-ttu-id="a38ac-191">.NET Core 2.1 也可实现 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="a38ac-191">.NET Core 2.1 also implements .NET Standard 2.0.</span></span> <span data-ttu-id="a38ac-192">.NET Standard 的未来版本出现后，.NET Core 将支持这些版本。</span><span class="sxs-lookup"><span data-stu-id="a38ac-192">.NET Core will support future versions of .NET Standard as they become available.</span></span>

| <span data-ttu-id="a38ac-193">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a38ac-193">.NET Core</span></span> | <span data-ttu-id="a38ac-194">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="a38ac-194">.NET Standard</span></span> |
|-----------|---------------|
| <span data-ttu-id="a38ac-195">1.0</span><span class="sxs-lookup"><span data-stu-id="a38ac-195">1.0</span></span>       | <span data-ttu-id="a38ac-196">达 1.6</span><span class="sxs-lookup"><span data-stu-id="a38ac-196">up to 1.6</span></span>     |
| <span data-ttu-id="a38ac-197">2.0</span><span class="sxs-lookup"><span data-stu-id="a38ac-197">2.0</span></span>       | <span data-ttu-id="a38ac-198">达 2.0</span><span class="sxs-lookup"><span data-stu-id="a38ac-198">up to 2.0</span></span>     |
| <span data-ttu-id="a38ac-199">2.1</span><span class="sxs-lookup"><span data-stu-id="a38ac-199">2.1</span></span>       | <span data-ttu-id="a38ac-200">达 2.0</span><span class="sxs-lookup"><span data-stu-id="a38ac-200">up to 2.0</span></span>     |

## <a name="see-also"></a><span data-ttu-id="a38ac-201">请参阅</span><span class="sxs-lookup"><span data-stu-id="a38ac-201">See also</span></span>

* [<span data-ttu-id="a38ac-202">目标框架</span><span class="sxs-lookup"><span data-stu-id="a38ac-202">Target frameworks</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="a38ac-203">.NET Core 分发打包</span><span class="sxs-lookup"><span data-stu-id="a38ac-203">.NET Core distribution packaging</span></span>](../build/distribution-packaging.md)  
* [<span data-ttu-id="a38ac-204">.NET Core 支持生命周期简报</span><span class="sxs-lookup"><span data-stu-id="a38ac-204">.NET Core Support Lifecycle Fact Sheet</span></span>](https://www.microsoft.com/net/core/support)  
* [<span data-ttu-id="a38ac-205">.NET Core 2 和版本绑定</span><span class="sxs-lookup"><span data-stu-id="a38ac-205">.NET Core 2+ Version Binding</span></span>](https://github.com/dotnet/designs/issues/3)  
* [<span data-ttu-id="a38ac-206">.NET Core 的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="a38ac-206">Docker images for .NET Core</span></span>](https://hub.docker.com/r/microsoft/dotnet/)
