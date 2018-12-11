---
description: Diese Anleitung hilft Ihnen, Fluent-basierte UWP-UIs direkt in einer WPF- oder Windows Forms-Anwendung zu erstellen.
title: UWP-Steuerelemente in Desktopanwendungen
ms.date: 09/21/2018
ms.topic: article
keywords: Windows 10, UWP, Windows Forms, WPF
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: bd22aa761d4a9a79c95c7bc424ab1d2a31ca6cdf
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8880859"
---
# <a name="uwp-controls-in-desktop-applications"></a>UWP-Steuerelemente in Desktopanwendungen

> [!NOTE]
> Die APIs und in diesem Artikel beschriebenen Steuerelemente sind derzeit als eine Vorschau für Entwickler zur Verfügung. Obwohl wir Sie Sie diese in Ihrem eigenen Code Prototyp ausprobieren können, jetzt dazu ermutigen, wird nicht empfohlen, dass Sie sie zu diesem Zeitpunkt in Produktionscode verwenden. Diese APIs und Steuerelemente erhalten auch weiterhin breiter und Stabilisierung in zukünftigen Windows-Versionen. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Windows 10 können jetzt Sie UWP-Steuerelemente in nicht-UWP-desktop-Apps zu verwenden, damit Sie das Erscheinungsbild und Funktionalität Ihrer vorhandenen desktop-Anwendungen mit den neuesten Windows 10-UI-Funktionen, die nur über UWP-Steuerelemente sind verbessern können. Dies bedeutet, dass Sie verwenden können UWP-Features wie [Windows Ink](../design/input/pen-and-stylus-interactions.md) und Steuerelemente, die das [Fluent Design-Systems](../design/fluent-design-system/index.md) in Ihrer vorhandenen WPF-, Windows Forms und C++ Win32-Anwendungen zu unterstützen. In diesem Szenario Entwickler wird *XAML-Inseln*bezeichnet.

Wir bieten verschiedene Möglichkeiten, verwenden Sie XAML-Inseln in Ihren WPF, Windows Forms und C++ Win32-Anwendungen, je nach Technologie oder Framework, die Sie verwenden werden.

## <a name="wrapped-controls"></a>Mit dem Steuerelemente

WPF- oder Windows Forms-Anwendung können eine Auswahl mit dem UWP-Steuerelemente in der [Windows-Community Toolkit](https://docs.microsoft.com/windows/uwpcommunitytoolkit/)verwenden. Wir bezeichnen diese Steuerelemente als *Steuerelemente eingeschlossen* , da sie die Benutzeroberfläche und Funktionen von einem bestimmten UWP-Steuerelement umschließen. Sie können diese Steuerelemente direkt auf der Entwurfsoberfläche Ihres WPF- oder Windows Forms-Projekts hinzufügen und sie dann wie jedes andere WPF- oder Windows Forms-Steuerelement im Designer verwenden.

> [!NOTE]
> Mit dem Steuerelemente sind nicht für C++ Win32-desktop-Apps verfügbar. Diese Arten von Anwendungen müssen die [UWP-XAML hosting-API](#uwp-xaml-hosting-api)verwenden.

Die folgenden mit dem UWP-Steuerelemente sind derzeit für WPF- oder Windows Forms-Anwendung verfügbar. Weitere umschlossen UWP-Steuerelemente sind für zukünftige Versionen von Windows Community Toolkit geplant.

| Steuerelement | Betriebssystem | Beschreibung |
|-----------------|-------------------------------|-------------|
| [WebView](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/webview) | Windows10, Version1803 | Mithilfe der Microsoft Edge-Renderingmodul Webinhalt angezeigt. |
| [WebViewCompatible](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/webviewcompatible) | Windows 7 | Bietet eine Version des **WebView** , die mit Weitere Betriebssystemversionen kompatibel ist. Dieses Steuerelement verwendet, die Microsoft Edge-Rendering-Engine zur Anzeige von Webinhalten auf Windows 10, Version 1803, und die Internet Explorer-Rendering-Engine zur Anzeige von Webinhalten in früheren Versionen von Windows 10, Windows 8.x und Windows 7. |
| [InkCanvas](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/inkcanvas)<br>[InkToolbar](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/inktoolbar) | Windows 10 Insider Preview SDK Build 17709 | Geben Sie einen Surface und die zugehörigen Symbolleisten für Windows Ink-basierte Benutzerinteraktion in Ihre Windows Forms- oder WPF-desktop-Anwendung. |
| [MediaPlayerElement](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/mediaplayerelement) | Windows 10 Insider Preview SDK Build 17709 | Bettet eine Ansicht, die streamt und rendert Medieninhalte z. B. Videowiedergabe in Ihre Windows Forms- oder WPF-desktop-Anwendung. |

## <a name="host-controls"></a>Host-Steuerelemente

Für Szenarien mit mehr als die von den verfügbaren mit Steuerelementen in können WPF- oder Windows Forms-Anwendung das Steuerelement [WindowsXamlHost](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost) auch im [Windows Community Toolkit](https://docs.microsoft.com/windows/uwpcommunitytoolkit/)verwenden. Dieses Steuerelement kann alle UWP-Steuerelement hosten, die von [**Windows.UI.Xaml.UIElement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement), z. B. alle UWP-Steuerelemente, die von Windows SDK als auch benutzerdefinierte Steuerelemente bereitgestellten abgeleitet wird. Dieses Steuerelement unterstützt Windows 10 Insider Preview SDK-Build 17709 und spätere Versionen.

> [!NOTE]
> Host-Steuerelemente sind nicht für C++ Win32-desktop-Apps verfügbar. Diese Arten von Anwendungen müssen die [UWP-XAML hosting-API](#uwp-xaml-hosting-api)verwenden.

## <a name="uwp-xaml-hosting-api"></a>UWP-XAML hosting-API

Wenn Sie eine C++ Win32-Anwendung verfügen, können die *UWP-XAML hosting-API* Sie alle UWP-Steuerelement hosten, die von [**Windows.UI.Xaml.UIElement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement) in alle UI-Element in der Anwendung abgeleitet wird, die über eine zugeordnete Fenster-Handle (HWND) verfügt. Diese API wurde in Windows 10 Insider Preview SDK Build 17709 eingeführt. Weitere Informationen zur Verwendung dieser API finden Sie [unter Verwendung des XAML-API in einer desktop-Anwendung hosten](using-the-xaml-hosting-api.md).

> [!NOTE]
> C++ Win32-desktop-Apps müssen die UWP-XAML hosting-API zum Hosten von UWP-Steuerelementen verwenden. Mit dem Steuerelemente und Host-Steuerelemente sind nicht für diese Arten von Anwendungen verfügbar. WPF- oder Windows Forms-Anwendung empfehlen wir, die mit dem Steuerelemente und die Host-Steuerelemente in der Windows-Community-Toolkit anstelle der UWP-XAML verwenden, hosting-API. Diese Steuerelemente verwenden, die UWP-XAML intern hosting-API und ein einfacher Development-Erlebnis zu bieten. Allerdings können Sie die UWP-XAML hosting-API direkt in WPF- oder Windows Forms-Anwendung, wenn Sie auswählen.

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
