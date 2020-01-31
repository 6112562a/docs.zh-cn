---
title: NotifyIcon 구성 요소 개요
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 587bf514db853f1122ed16abc05a195985c5ce8d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742121"
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon 구성 요소 개요(Windows Forms)

Windows Forms <xref:System.Windows.Forms.NotifyIcon> 구성 요소는 일반적으로 백그라운드에서 실행되고 대체로 사용자 인터페이스를 표시하지 않는 프로세스에 대한 아이콘을 표시하는 데 사용됩니다. 예를 들어 작업 표시줄의 상태 알림 영역에서 아이콘을 클릭하여 액세스할 수 있는 바이러스 방지 프로그램이 있습니다.

## <a name="key-properties-of-notifyicons"></a>NotifyIcons의 키 속성

각 <xref:System.Windows.Forms.NotifyIcon> 구성 요소는 상태 영역에 단일 아이콘을 표시합니다. 3개의 백그라운드 프로세스가 있고 각 프로세스에 대한 아이콘을 표시하려는 경우 <xref:System.Windows.Forms.NotifyIcon> 구성 요소 3개를 폼에 추가해야 합니다. <xref:System.Windows.Forms.NotifyIcon> 구성 요소의 키 속성은 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 및 <xref:System.Windows.Forms.NotifyIcon.Visible%2A>입니다. <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 속성은 상태 영역에 표시되는 아이콘을 설정합니다. 아이콘이 표시되려면 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 속성을 `true`로 설정해야 합니다.

## <a name="notifyicons-options"></a>NotifyIcons 옵션

풍선 설명, 바로 가기 메뉴 및 도구 설명을 <xref:System.Windows.Forms.NotifyIcon>에 연결하여 사용자를 지원할 수 있습니다.

풍선 설명을 표시할 시간 범위를 지정하고 <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> 메서드를 호출하여 <xref:System.Windows.Forms.NotifyIcon>에 대한 풍선 설명을 표시할 수 있습니다. <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> 및 <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>을 각각 사용하여 풍선 설명의 텍스트, 아이콘 및 제목을 지정할 수도 있습니다. <xref:System.Windows.Forms.NotifyIcon> 구성 요소에 연결된 도구 설명 및 바로 가기 메뉴가 있을 수도 있습니다. 有关详细信息，请参阅[ToolTip 组件概述](tooltip-component-overview-windows-forms.md)和[ContextMenu 组件概述](contextmenu-component-overview-windows-forms.md)。

## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.NotifyIcon>
- [NotifyIcon 구성 요소](notifyicon-component-windows-forms.md)
