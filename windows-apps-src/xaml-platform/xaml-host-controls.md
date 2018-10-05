---
author: normesta
description: Diese Anleitung hilft Ihnen, Fluent-basierte UWP-UIs direkt in einer WPF- oder Windows Forms-Anwendung zu erstellen.
title: UWP-Steuerelemente in desktop-Apps
ms.author: normesta
ms.date: 09/21/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp, windows forms, wpf
keywords: Windows 10, UWP, Windows Forms, WPF
ms.localizationpriority: medium
ms.openlocfilehash: 67669dd30f376df823f2f9ad08ad69c193cdb602
ms.sourcegitcommit: 63cef0a7805f1594984da4d4ff2f76894f12d942
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2018
ms.locfileid: "4386735"
---
# <a name="uwp-controls-in-desktop-applications"></a>UWP-Steuerelemente in desktop-Apps

> [!NOTE]
> Die APIs und in diesem Artikel beschriebenen Steuerelemente sind als Entwicklervorschau derzeit verfügbar ist. Obwohl wir Sie Sie diese in Ihrem eigenen Code Prototyp ausprobieren können, jetzt dazu ermutigen, empfohlen nicht, dass Sie sie in Produktionscode zu diesem Zeitpunkt verwenden. Diese APIs und Steuerelemente werden weiterhin breiter und Stabilisierung in zukünftigen Windows-Versionen. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Windows 10 können jetzt Sie UWP-Steuerelemente in nicht-UWP-desktopanwendungen verwenden, sodass Sie das Erscheinungsbild, und Funktionalität Ihrer vorhandenen desktop-Anwendungen mit den neuesten Windows 10-UI-Funktionen, die nur über UWP-Steuerelemente sind verbessern können. Dies bedeutet, dass Sie verwenden können UWP-Features wie [Windows Ink](../design/input/pen-and-stylus-interactions.md) und Steuerelemente, die das [Fluent Design-Systems](../design/fluent-design-system/index.md) in Ihrer vorhandenen WPF-, Windows Forms und C++ Win32-Anwendungen zu unterstützen. In diesem Szenario Entwickler wird *XAML-Inseln*bezeichnet.

Wir bieten verschiedene Möglichkeiten, verwenden Sie XAML-Inseln in WPF, Windows Forms und C++ Win32-Anwendung, abhängig von der Technologie oder Framework, die Sie verwenden werden.

## <a name="wrapped-controls"></a>Umschlossenen Steuerelemente

WPF- oder Windows Forms-Anwendung können eine Auswahl von umschlossenen UWP-Steuerelemente in der [Windows-Community Toolkit](https://docs.microsoft.com/windows/uwpcommunitytoolkit/)verwenden. Wir bezeichnen diese Steuerelemente als *umschlossen Steuerelemente* , da sie die Schnittstelle und Funktionen für ein bestimmtes UWP-Steuerelement umschließen. Sie können diese Steuerelemente direkt auf der Entwurfsoberfläche Ihres WPF- oder Windows Forms-Projekts hinzufügen und sie dann wie jedes andere WPF- oder Windows Forms-Steuerelement im Designer verwenden.

> [!NOTE]
> Umschlossenen Steuerelemente sind nicht für C++ Win32-desktop-Apps verfügbar. Diese Arten von Anwendungen müssen die [UWP-XAML hosting-API](#uwp-xaml-hosting-api)verwenden.

Die folgenden umschlossenen UWP-Steuerelemente sind derzeit für WPF und Windows Forms-Anwendungen verfügbar. Weitere umschlossen UWP-Steuerelemente sind für zukünftige Versionen von Windows Community Toolkit geplant.

| Steuerelement | Unterstützte Mindestversion OS | Beschreibung |
|-----------------|-------------------------------|-------------|
| [WebView](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/webview) | Windows10, Version1803 | Mithilfe der Microsoft Edge-Renderingmodul Webinhalt angezeigt. |
| [WebViewCompatible](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/webviewcompatible) | Windows 7 | Bietet eine Version des **WebView** , die mit Weitere Betriebssystemversionen kompatibel ist. Dieses Steuerelement verwendet, die Microsoft Edge-Rendering-Engine zur Anzeige von Webinhalten auf Windows 10, Version 1803 oder höher und die Internet Explorer-Rendering-Engine zur Anzeige von Webinhalten auf früheren Versionen von Windows 10, Windows 8.x und Windows 7. |
| [InkCanvas](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/inkcanvas)<br>[InkToolbar](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/inktoolbar) | Windows 10 Insider Preview SDK Build 17709 | Stellen Sie eine Fläche und die zugehörigen Symbolleisten für Windows Ink-basierte Benutzerinteraktion in Ihre Windows Forms- oder WPF-desktop-Anwendung. |
| [MediaPlayerElement](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/mediaplayerelement) | Windows 10 Insider Preview SDK Build 17709 | Bettet eine Ansicht, die streamt und rendert Medieninhalte wie z. B. Videos in Ihre Windows Forms- oder WPF-desktop-Anwendung. |

## <a name="host-controls"></a>Host-Steuerelemente

Für Szenarien mit mehr als die verfügbaren umschlossenen Steuerelemente abgedeckten können WPF- oder Windows Forms-Anwendung auch das Steuerelement [WindowsXamlHost](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost) im [Windows Community Toolkit](https://docs.microsoft.com/windows/uwpcommunitytoolkit/)verwenden. Dieses Steuerelement kann alle UWP-Steuerelement hosten, die von [**Windows.UI.Xaml.UIElement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement), einschließlich alle UWP-Steuerelement, das von der Windows SDK sowie benutzerdefinierte Steuerelemente bereitgestellten abgeleitet wird. Dieses Steuerelement unterstützt Windows 10 Insider Preview SDK-Build 17709 und spätere Versionen.

> [!NOTE]
> Hoststeuerelemente sind nicht für C++ Win32-desktop-Apps verfügbar. Diese Arten von Anwendungen müssen die [UWP-XAML hosting-API](#uwp-xaml-hosting-api)verwenden.

## <a name="uwp-xaml-hosting-api"></a>UWP-XAML hosting-API

Wenn Sie eine C++ Win32-Anwendung verfügen, können die *UWP-XAML hosting-API* Sie alle UWP-Steuerelement hosten, die von [**Windows.UI.Xaml.UIElement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement) in alle UI-Element in der Anwendung abgeleitet wird, das über eine zugeordnete Fenster-Handle (HWND) verfügt. Diese API wurde in Windows 10 Insider Preview SDK Build 17709 eingeführt. Weitere Informationen zur Verwendung dieser API finden Sie [unter Verwendung des XAML-API in einer desktop-Anwendung hosten](using-the-xaml-hosting-api.md).

> [!NOTE]
> C++ Win32-desktop-Apps müssen die UWP-XAML hosting-API zum Hosten von UWP-Steuerelementen verwenden. Umschlossenen Steuerelemente und Hoststeuerelemente sind nicht für diese Arten von Anwendungen verfügbar. Für WPF und Windows Forms-Anwendungen empfehlen wir die Verwendung von umschlossenen Steuerelemente und der Host-Steuerelemente in der Windows-Community-Toolkit anstelle der UWP-XAML hosting-API werden. Diese Steuerelemente verwenden, die UWP-XAML intern hosting-API und bieten eine einfachere Erfahrung in der Entwicklung. Sie können jedoch die UWP-XAML hosting-API direkt in WPF und Windows Forms-Anwendung, wenn Sie auswählen.

## <a name="architecture-overview"></a>Übersicht über die Architektur

Nachfolgend ist dargestellt, wie diese Steuerelemente architektonisch organisiert sind. Die in diesem Diagramm verwendeten Namen werden möglicherweise noch geändert.  

![Hoststeuerelement-Architektur](images/host-controls.png)

Die am Diagrammende aufgeführten APIs sind im Lieferumfang des Windows SDK enthalten. Die Steuerelemente für den Designer sind als Nuget-Pakete im Windows Community Toolkit geliefert enthalten.

Diese neuen Steuerelemente haben noch Einschränkungen. Bevor Sie die Steuerelemente verwenden, sollten Sie sich einen Moment Zeit nehmen und lesen, was noch nicht unterstützt wird oder nur mit Problemumgehungen funktioniert.

## <a name="limitations"></a>Einschränkungen

### <a name="whats-supported"></a>Nicht unterstützt

In den meisten Fällen wird nur die Funktionalität nicht unterstützt, die in der folgenden Liste aufgeführt ist.

### <a name="whats-supported-only-with-workarounds"></a>Nur mit Problemumgehungen unterstützt

:heavy_check_mark: Hosting mehrerer Inbox-Steuerelemente innerhalb mehrerer Fenster Sie müssen jedes Fenster in seinem eigenen Thread platzieren.

:heavy_check_mark: Verwendung von ``x:Bind`` mit gehosteten Steuerelementen Sie müssen das Datenmodell in einer .NET Standardbibliothek deklarieren.

:heavy_check_mark: C#-basierte Drittanbieter-Steuerelemente Wenn Sie über den Quellcode eines Drittanbieter-Steuerelements verfügen, können Sie ihn kompilieren.

### <a name="whats-not-yet-supported"></a>Noch nicht unterstützt

:no_entry_sign: Tools mit Bedienungshilfen, die gleichartig für die Anwendung und die gehosteten Steuerelemente funktionieren

:no_entry_sign: Lokalisierter Inhalt in Steuerelementen für Anwendungen, die kein Windows-App-Paket enthalten

:no_entry_sign: Asset-Verweise in XAML innerhalb von Anwendungen, die kein Windows-App-Paket enthalten

:no_entry_sign: Steuerelemente, die korrekt bezüglich Änderungen von DPI und Skalierung reagieren

:no_entry_sign: Hinzufügen eines **WebView**-Steuerelements zu einem benutzerdefinierten Steuerelement (entweder „on-thread”, „off-thread” oder „out of proc”)

:no_entry_sign: Der Fluent-Effekt [Reveal Highlight](https://docs.microsoft.com/windows/uwp/design/style/reveal)

:no_entry_sign: Inline-Freihandeingabe, @Places und @People für Eingabesteuerelemente

:no_entry_sign: Zuweisen von Zugriffstasten

:no_entry_sign: C++-basierte Steuerelemente von Drittanbietern

:no_entry_sign: Hosten benutzerdefinierter Steuerelemente

Die Elemente in dieser Liste werden sich wahrscheinlich ändern, da wir ständig daran arbeiten, Fluent auf dem Desktop zu optimieren.  
