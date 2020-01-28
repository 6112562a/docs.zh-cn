---
title: 编译应用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
ms.openlocfilehash: 00c76dfcdcedc7ceaefaaae785368f8b343457a7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744763"
---
# <a name="compile-a-wpf-application"></a>编译 WPF 应用程序

Windows Presentation Foundation （WPF）应用程序可以生成为 .NET Framework 可执行文件（.exe）、库（.dll）或这两种类型的程序集的组合。 本主题介绍如何构建 WPF 应用程序，并介绍生成过程中的关键步骤。

<a name="Building_a_WPF_Application_using_Command_Line"></a>

## <a name="building-a-wpf-application"></a>WPF 애플리케이션 빌드

다음과 같은 방법으로 WPF 애플리케이션을 컴파일할 수 있습니다.

- 명령줄. 애플리케이션에 코드(XAML 없음)와 애플리케이션 정의 파일만 포함되어야 합니다. 자세한 내용은 [csc.exe를 사용한 명령줄 빌드](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) 또는 [명령줄에서 빌드(Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)를 참조하세요.

- MSBuild(Microsoft Build Engine). 애플리케이션에 코드 및 XAML 파일 외에 MSBuild 프로젝트 파일이 포함되어야 합니다. 자세한 내용은 "MSBuild"를 참조하세요.

- 보여 줍니다. Visual Studio는 MSBuild를 사용하여 WPF 애플리케이션을 컴파일하고 UI를 만들기 위한 비주얼 디자이너를 포함하는 통합 개발 환경입니다. 有关详细信息，请参阅[使用 Visual Studio 编写和管理代码](/visualstudio/ide/index-writing-code)和[在 Visual STUDIO 中设计 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)。

<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>

## <a name="wpf-build-pipeline"></a>WPF 빌드 파이프라인

生成 WPF 项目时，将调用语言特定目标和特定于 WPF 的目标的组合。 이러한 대상을 실행 중인 프로세스를 빌드 파이프라인이라고 하며 주요 단계는 다음 그림에서와 같이 설명됩니다.

![WPF 生成过程](./media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")

<a name="Pre_Build_Initializations"></a>

### <a name="pre-build-initializations"></a>빌드 전 초기화

在生成之前，MSBuild 确定重要工具和库的位置，包括以下各项：

- .NET Framework。

- Windows SDK 的目录。

- WPF 引用程序集的位置。

- 어셈블리 검색 경로의 속성

MSBuild 在其中搜索程序集的第一个位置是引用程序集目录（%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.0\\）。 이 단계에서 빌드 프로세스는 다양한 속성 및 항목 그룹을 초기화하고 필요한 정리 작업을 수행합니다.

<a name="Resolving_references"></a>

### <a name="resolving-references"></a>참조 확인

빌드 프로세스는 애플리케이션 프로젝트를 빌드하는 데 필요한 어셈블리를 찾아서 바인딩합니다. 이 논리는 `ResolveAssemblyReference` 작업에 포함되어 있습니다. 프로젝트 파일에서 `Reference`로 선언된 모든 어셈블리는 시스템에 이미 설치된 어셈블리의 메타데이터 및 검색 경로에 대한 정보와 함께 작업에 제공됩니다. 该任务将查找程序集，并使用已安装的程序集的元数据来筛选出那些不需要显示在输出清单中的核心 WPF 程序集。 이 작업의 목적은 ClickOnce 매니페스트에서 중복되는 정보를 방지하는 것입니다. 例如，由于 PresentationFramework 可被视为在和 WPF 上构建的应用程序的代表，并且由于在安装了 .NET Framework 的每台计算机上的同一位置都存在所有 WPF 程序集，因此无需包括所有有关清单中所有 .NET Framework 引用程序集的信息。

<a name="Markup_Compilation___Pass_1"></a>

### <a name="markup-compilationpass-1"></a>태그 컴파일 - 패스 1

在此步骤中，将对 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件进行分析和编译，使运行时不会花费时间分析 XML 和验证属性值。 컴파일된 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일은 사전 토큰화되어 있으므로 런타임 시 이 파일을 로드하면 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일을 로드하는 것보다 훨씬 속도가 빨라집니다.

이 단계에서 다음 작업은 `Page` 빌드 항목인 모든 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일에 대해 수행됩니다.

1. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일은 태그 컴파일러에 의해 구문 분석됩니다.

2. 컴파일된 표현은 해당 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]에 대해 만들어져서 obj\Release 폴더에 복사됩니다.

3. 새 partial 클래스의 CodeDOM 표현이 만들어져서 obj\Release 폴더에 복사됩니다.

또한 모든 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일에 대해 언어별 코드 파일이 생성됩니다. 例如，对于 Visual Basic 项目中的 Page1 页，生成了 Page1. g.;对于C#项目中的 Page1 页，会生成 Page1.g.cs。 파일 이름에 ".g"가 있으면 파일이 태그 파일(예: `Page` 또는 `Window`)의 최상위 수준 요소에 대한 partial 클래스 선언을 포함하여 생성된 코드라는 의미입니다. 此类是用中C#的 `partial` 修饰符声明的（`Extends` 在 Visual Basic 中），以指示该类的其他声明（通常在代码隐藏文件 Page1.xaml.cs 中）。

分部类从适当的基类（如页面 <xref:System.Windows.Controls.Page>）进行扩展并实现 <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> 接口。 <xref:System.Windows.Markup.IComponentConnector> 接口包含用于初始化组件并连接其内容中元素上的名称和事件的方法。 결과적으로 생성된 코드 파일에는 다음과 같은 메서드 구현이 있습니다.

```csharp
public void InitializeComponent() {
    if (_contentLoaded) {
        return;
    }
    _contentLoaded = true;
    System.Uri resourceLocater =
        new System.Uri(
            "window1.xaml",
            System.UriKind.RelativeOrAbsolute);
    System.Windows.Application.LoadComponent(this, resourceLocater);
}
```

```vb
Public Sub InitializeComponent() _

    If _contentLoaded Then
        Return
    End If

    _contentLoaded = True
    Dim resourceLocater As System.Uri = _
        New System.Uri("mainwindow.xaml", System.UriKind.Relative)

    System.Windows.Application.LoadComponent(Me, resourceLocater)

End Sub
```

默认情况下，标记编译在与 MSBuild 引擎相同的 <xref:System.AppDomain> 中运行。 따라서 성능이 크게 향상됩니다. 이 동작은 `AlwaysCompileMarkupFilesInSeparateDomain` 속성을 통해 전환할 수 있습니다. 此方法的优点是通过卸载单独的 <xref:System.AppDomain>卸载所有引用程序集。

<a name="Pass_2_of_Markup_Compilation"></a>

### <a name="markup-compilationpass-2"></a>태그 컴파일 - 패스 2

일부 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 페이지는 태그 컴파일의 패스 1에서 컴파일됩니다. 이때 로컬로 정의된 형식 참조(동일한 프로젝트의 코드에서 정의된 형식에 대한 참조)가 있는 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일은 컴파일에서 제외됩니다. 이는 로컬로 정의된 형식이 소스에만 있어 아직 컴파일되지 않았기 때문입니다. 이를 확인하기 위해 파서는 추론을 사용하여 태그 파일에서 `x:Name`과 같은 항목을 찾습니다. 이러한 인스턴스를 찾은 경우 코드 파일이 컴파일될 때까지 해당 태그 파일의 컴파일이 연기되며 나중에 두 번째 태그 컴파일 패스가 이러한 파일을 처리합니다.

<a name="File_Classification"></a>

### <a name="file-classification"></a>파일 분류

빌드 프로세스는 출력 파일을 배치할 애플리케이션 어셈블리를 기반으로 다른 리소스 그룹에 출력 파일을 배치합니다. 일반적으로 지역화되지 않은 애플리케이션에서 `Resource`로 표시된 모든 데이터 파일은 주 어셈블리(실행 파일 또는 라이브러리)에 배치됩니다. 프로젝트에서 `UICulture`가 설정된 경우 컴파일된 모든 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일 및 해당 리소스(특히 언어별로 표시된 리소스)가 위성 리소스 어셈블리에 배치됩니다. 또한 모든 언어 중립 리소스는 주 어셈블리에 배치됩니다. 빌드 프로세스의 이 단계에서 해당 사항이 결정됩니다.

프로젝트 파일의 `ApplicationDefinition`, `Page` 및 `Resource` 빌드 작업은 `Localizable` 메타데이터(허용 가능한 값은 `true` 및 `false`)를 통해 보강할 수 있으며 이는 파일이 언어와 관련되었는지 또는 언어 중립적인지 지정합니다.

<a name="Core_Compilation"></a>

### <a name="core-compilation"></a>핵심 컴파일

핵심 컴파일 단계에서는 코드 파일을 컴파일합니다. 이 작업은 언어별 대상 파일 Microsoft.CSharp.targets 및 Microsoft.VisualBasic.targets의 논리에 의해 오케스트레이션됩니다. 추론을 통해 태그 컴파일러의 단일 패스로 충분하다고 판단된 경우 주 어셈블리가 생성됩니다. 그러나 프로젝트에서 하나 이상의 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일에 로컬로 정의된 형식에 대한 참조가 있는 경우 태그 컴파일의 두 번째 패스가 완료된 후 최종 애플리케이션 어셈블리가 만들어질 수 있도록 임시 .dll 파일이 생성됩니다.

<a name="Manifest_generation"></a>

### <a name="manifest-generation"></a>매니페스트 생성

在生成过程结束时，所有应用程序程序集和内容文件都准备就绪后，将生成应用程序的 ClickOnce 清单。

배포 매니페스트 파일은 배포 모델, 즉 현재 버전, 업데이트 동작 및 게시자 ID를 디지털 시그니처와 함께 설명합니다. 이 매니페스트는 배포를 처리하는 관리자가 작성합니다. 文件扩展名为 xbap （适用于 XAML 浏览器应用程序（Xbap））和应用程序。 .xbap는 `HostInBrowser` 프로젝트 속성에 의해 지정되며 그 결과 매니페스트는 애플리케이션이 브라우저에 호스트되는 것으로 식별합니다.

애플리케이션 매니페스트(.exe.manifest 파일)는 애플리케이션 어셈블리 및 종속 라이브러리를 설명하고 애플리케이션에 필요한 사용 권한을 나열합니다. 이 파일은 애플리케이션 개발자가 작성합니다. 为了启动 ClickOnce 应用程序，用户将打开该应用程序的部署清单文件。

这些清单文件始终为 Xbap 创建。 설치된 애플리케이션의 경우 프로젝트 파일에서 `GenerateManifests` 속성 값이 `true`로 지정되지 않는 한 만들어지지 않습니다.

Xbap 在分配给典型 Internet 区域应用程序的权限之上或更高的其他两个权限： <xref:System.Security.Permissions.WebBrowserPermission> 和 <xref:System.Security.Permissions.MediaPermission>。 WPF 生成系统会在应用程序清单中声明这些权限。

<a name="Incremental_Build_Support"></a>

## <a name="incremental-build-support"></a>증분 빌드 지원

WPF 生成系统为增量生成提供支持。 태그 또는 코드에 대한 변경 사항을 지능적으로 검색하고 변경 사항의 영향을 받는 아티팩트만 컴파일합니다. 증분 빌드 메커니즘은 다음 파일을 사용합니다.

- 현재 컴파일러 상태를 유지 관리하는 $(*AssemblyName*)_MarkupCompiler.Cache 파일

- 로컬로 정의된 형식에 대한 참조가 있는 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일을 캐시하는 $(*AssemblyName*) _MarkupCompiler.lref 파일

다음은 증분 빌드를 제어하는 규칙 집합입니다.

- 파일은 빌드 시스템이 변경을 검색하는 가장 작은 단위입니다. 따라서 코드 파일의 경우 빌드 시스템에서 형식이 변경되었는지 또는 코드가 추가되었는지 확인할 수 없습니다. 이는 프로젝트 파일도 마찬가지입니다.

- 증분 빌드 메커니즘은 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 페이지가 클래스를 정의하거나 다른 클래스를 사용한다는 것을 인식해야 합니다.

- `Reference` 항목이 변경된 경우 모든 페이지를 다시 컴파일합니다.

- 코드 파일이 변경되면 로컬로 정의된 형식 참조가 있는 모든 페이지를 다시 컴파일합니다.

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일이 변경된 경우:

  - 프로젝트에서 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]이 `Page`로 선언된 경우: [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]에 로컬로 정의된 형식 참조가 없는 경우 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 및 모든 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 페이지를 로컬 참조와 함께 다시 컴파일합니다. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]에 로컬 참조가 있는 경우 모든 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 페이지를 로컬 참조와 함께 다시 컴파일합니다.

  - 如果 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 在项目中声明为 `ApplicationDefinition`：重新编译所有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页（原因：每个 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 都引用了可能已更改的 <xref:System.Windows.Application> 类型）。

- 프로젝트 파일에서 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일 대신 애플리케이션 정의로 코드 파일을 선언한 경우:

  - 프로젝트 파일의 `ApplicationClassName` 값이 변경되었는지(새로운 애플리케이션 형식이 있는지) 확인합니다. 변경된 경우 전체 애플리케이션을 다시 컴파일합니다.

  - 변경되지 않은 경우 모든 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 페이지를 로컬 참조와 함께 다시 컴파일합니다.

- 프로젝트 파일이 변경된 경우: 앞에서 설명한 규칙을 모두 적용하고 다시 컴파일해야 할 항목을 확인합니다. `AssemblyName`, `IntermediateOutputPath`, `RootNamespace` 및 `HostInBrowser` 속성이 변경되면 전체 다시 컴파일됩니다.

다시 컴파일 작업은 다음과 같은 시나리오로 수행될 수 있습니다.

- 전체 애플리케이션이 다시 컴파일됩니다.

- 로컬로 정의된 형식 참조가 있는 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일만 다시 컴파일됩니다.

- 모든 항목이 다시 컴파일되지 않습니다(프로젝트의 모든 항목이 변경되지 않음).

## <a name="see-also"></a>另请参阅

- [WPF 애플리케이션 배포](deploying-a-wpf-application-wpf.md)
- [WPF MSBuild 참조](/visualstudio/msbuild/wpf-msbuild-reference)
- [WPF의 Pack URI](pack-uris-in-wpf.md)
- [WPF 애플리케이션 리소스, 콘텐츠 및 데이터 파일](wpf-application-resource-content-and-data-files.md)
