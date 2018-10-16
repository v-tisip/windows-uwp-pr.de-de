---
author: QuinnRadich
title: Was ist neu in Windows-Dokumentation im Mai 2018 – Entwicklung von UWP-apps
description: Neue Features, Videos und entwicklerleitfäden verfügen über die Windows 10-Entwicklerdokumentation für Mai 2018 und der Microsoft Build-Konferenz hinzugefügt wurde.
keywords: Neuigkeiten, update, features, Anleitungen für Entwickler, Windows 10, Mai, Build
ms.author: quradic
ms.date: 5/7/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 322bc056411095019dfc027078cbfef7de0883fb
ms.sourcegitcommit: 106aec1e59ba41aae2ac00f909b81bf7121a6ef1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "4621301"
---
# <a name="whats-new-in-the-windows-developer-docs-in-may-2018"></a>Neuigkeiten in der Windows-Entwicklerdokumentation im Mai 2018

Die Entwicklerdokumentation für die Windows-Plattform wird ständig mit Informationen über neue Features für Entwickler aktualisiert. Die folgenden Featureübersichten, entwicklerleitfäden, Videos und Beispiele wurden im Mai mit der [Microsoft Build 2018](https://www.microsoft.com/build) -Entwicklerkonferenz zur Verfügung gestellt wurden.

Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows10 können Sie entweder [eine neue universelle Windows-App erstellen](../get-started/create-uwp-apps.md) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](../porting/index.md) vertraut machen.

## <a name="features"></a>Features

### <a name="motion-in-fluent-design"></a>Bewegung in der Fluent Design

Der Benutzer der Bewegung in der Fluent Design-Systems wird weiterentwickelt, die auf die Grundlagen der Timing, geschwindigkeitsverlauf, direktionalität und Schwerkraft erstellt. Anwenden von diesen Grundlagen hilft Führung des Benutzers über Ihre app und Spiegeln der natürlichen Welt mit seiner digitalen Erfahrung verbunden. Weitere Informationen finden Sie in diesen Artikeln:

* [Übersicht über die Bewegungen](../design/motion/index.md) wurde aktualisiert, um diese Grundlagen widerspiegeln.
* [In der Praxis Bewegung](../design/motion/motion-in-practice.md) enthält Beispiele zur Verwendung von diesen Grundlagen innerhalb Ihrer app anwenden.
* [Direktionalität und Schwerkraft](../design/motion/directionality-and-gravity.md) festigt das mentale Benutzermodell Ihrer App.
* [Timing und geschwindigkeitsverlauf](../design/motion/timing-and-easing.md) wird die Bewegung in Ihrer app Realismus hinzugefügt.

![Bewegung in Aktion zu sehen](../design/motion/images/contextual.gif)

### <a name="fluent-design-updates"></a>Fluent Design-Updates

Visuelle Updates und geringfügigen Änderungen wurden die folgenden Fluent Design-Seiten vorgenommen:

* [Ausrichtung, Abstände, Ränder](../design/layout/alignment-margin-padding.md)
* [Farbe](../design/style/color.md)
* [Befehlsgrundlagen](../design/basics/commanding-basics.md)
* [Fluent Design für Windows-apps](../design/fluent-design-system/index.md)
* [Einführung in das app-design](../design/basics/design-and-ui-intro.md)
* [Navigationsgrundlagen](../design/basics/navigation-basics.md)
* [Reaktionsfähige Designtechniken](../design/layout/responsive-design.md)
* [Bildschirmgrößen und Breakpoints](../design/layout/screen-sizes-and-breakpoints-for-responsive-design.md)
* [Übersicht über die Stil](../design/style/index.md)
* [Schreibstil](../design/style/writing-style.md)

Darüber hinaus haben wir die folgenden Seiten mit neuen Informationen zu ihren Inhaltsbereiche umgeschrieben:

* [Symbole](../design/style/icons.md) enthält jetzt praktische Empfehlungen für Symbole und dass diese geklickt werden kann.
* [Typografie](../design/style/typography.md) konsolidiert Informationen aus ähnlichen Artikeln Sie alles an einem Ort mit aktualisierten Hilfestellungen und Illustrationen einfügen.

![Bild mit Farbpalette](../design/style/images/color/accent-color-palette.svg)

### <a name="app-installer-files-in-visual-studio"></a>App-Installer-Dateien in Visual Studio

App-Installer-Dateien können jetzt mit Visual Studio 2017, Update 15.7 erstellt werden. [Erfahren Sie, wie Sie Visual Studio zum Erstellen einer App-Installer-Datei verwenden](../packaging/create-appinstallerfile-vs.md) und aktivieren Sie automatische Updates für Ihre apps. Wenn Probleme auftreten, finden Sie unter [Problembehandlung bei der Installation mit der App-Installer-Datei](../packaging/troubleshoot-appinstaller-issues.md) , um allgemeine Probleme und Lösungen anzuzeigen.

### <a name="edge-webview-control-for-windows-forms-and-wpf-applications"></a>Edge-WebView-Steuerelement für Windows Forms oder WPF-Anwendung

Anzeigen von Webinhalten in Ihrer desktop-Anwendung mit der WebView-Steuerelement, das zuvor nur für UWP-Anwendungen verfügbar. Dieses Steuerelement verwendet die Microsoft Edge Modul zu eine Ansicht einbetten rendert Rich-Text HTML formatiert Inhalte von einem Remotewebserver, dynamisch generiertem Code oder Inhaltsdateien rendern. Suchen Sie das WebView-Steuerelement in der neuesten Version von der [Windows Community Toolkit.](https://docs.microsoft.com/windows/uwpcommunitytoolkit/)

Suchen Sie für andere Steuerelemente wie WebView im Windows Community Toolkit finden in zukünftigen Versionen. Weitere Informationen finden Sie unter [Host-UWP-Steuerelemente in WPF- oder Windows Forms-Anwendung.](https://docs.microsoft.com/windows/uwp/xaml-platform/xaml-host-controls)

### <a name="gaze-input-and-interactions"></a>Eingabe via anvisieren und Interaktionen

[Verfolgen Sie den Blick, die Aufmerksamkeit und die Präsenz eines Benutzers anhand der Position und Bewegung seiner Augen.](../design/input/gaze-interactions.md) Diese leistungsstarke neue Methode zur Verwendung und Interaktion mit Ihren UWP-apps ist besonders hilfreich als unterstützende Technologie. Die blickeingabe bietet zudem überzeugende Möglichkeiten für Spiele (einschließlich zielerfassung und -Verfolgung) und andere interaktiven Szenarien, in denen herkömmliche Eingabegeräte (Tastatur, Maus, Touch) nicht verfügbar sind.

### <a name="msix-packaging-format"></a>MSIX-Paketformat

MSIX ist auf der Microsoft Build 2018 Konferenz angekündigt, eine neue Containerization-Paketformat, die für alle Windows-desktopanwendungen, die z. B. Win32, Windows Forms, WPF und UWP gilt. Dieses neue Format erbt großartige Features von UWP:

* Stabile Installation und Aktualisierung. 
* Sicherheitsmodell mit einer flexiblen Funktion des Systems verwaltet.
* Unterstützung für den Microsoft Store, Enterprise Management und viele benutzerdefinierte Verteilung Modelle.

Tools zur Erstellung dieser Pakete werden in einer zukünftigen Version von Visual Studio und Windows SDK verfügbar sein.

MSIX-Paketformat ist ein open-Source-Format mit einer leichter unsere Partner mit das MSIX-Ökosystem mit Tools und Lösungen für ihr unterstützen kann. Weitere Informationen zu den MSIX-Paketformat erhalten, finden Sie unter [MSIX-SDK](https://github.com/Microsoft/msix-packaging). 

![MSIX-Packaging-image](images/msix.png)

### <a name="optional-packages-with-executable-code"></a>Optionale Pakete mit ausführbarem Code

Optionale Pakete in Ihrer app können nun ausführbaren C#-Code enthalten. [Hier erfahren Sie, wie Sie mithilfe von Visual Studio so konfigurieren Sie optionale Add-on Pakete zum das Haupt-app-Paket zu unterstützen.](../packaging/optional-packages-with-executable-code.md)

### <a name="page-transitions"></a>Seitenübergänge

[Seitenübergänge](../design/motion/page-transitions.md) , wenn Benutzer zwischen Seiten in einer app navigieren. Sie können Benutzern das Verständnis, wo sie in der Navigationshierarchie sind, und geben Sie Feedback über die Beziehung zwischen Seiten.

### <a name="project-rome"></a>Projekt Rome

Das Projekt "ROME"-Team hat ihre IOS- und Android-SDKs, Hinzufügen neuer Funktionen wie Aktivitäten des Benutzers und Umgestaltung Großteil ihres Codes, um eine konsistente programmiererfahrung über die verschiedenen SDKs bieten überholt. [Alle neuen API-Referenz und Vorgehensweisen Dokumente](https://docs.microsoft.com/windows/project-rome/) werden während der Build 2018-Entwicklerkonferenz freischalten.

### <a name="sets"></a>Sets

Die Funktion ist in Windows-Insider Preview-builds verfügbar. Wenn das Sets-Feature verwendet, wird Ihre app in einem Fenster gezeichnet, die mit anderen apps zu jeder app müssen eine eigene Registerkarte in der Titelleiste gemeinsam genutzt werden kann. [Entwerfen für Sets](../design/shell/design-for-sets.md) enthält eine Anleitung zum Optimieren Sie Ihre app, um die bestmögliche Erfahrung in der Benutzeroberfläche legt zu bieten.

## <a name="developer-guidance"></a>Anleitungen für Entwickler

### <a name="get-started"></a>Erste Schritte

Wir haben unsere Get revitalized Inhalte mit neuen Lernpfade gestartet. Diese neuen Themen zielt darauf ab, bieten neuen Windows 10-Entwickler mit Informationen über eine Reihe häufiger Aufgaben, dass sie möglicherweise erreichen möchten. Sie sind nicht Lernprogramme und eine tragbaren dieser exemplarischen Vorgehensweise nicht bereitstellen, sondern stattdessen weisen Sie darauf hin, in denen Dokumentation vorhanden ist und wie sie zu verwenden. Sehen Sie sich die überarbeitete [Programmieren](../get-started/create-uwp-apps.md) Seite oder Erkunden Sie jede einzelne Lernpfad:

* [Erstellen eines Formulars](../get-started/construct-form-learning-track.md)
* [Anzeigen von Kunden in einer Liste](../get-started/display-customers-in-list-learning-track.md)
* [Speichern und Laden von Einstellungen](../get-started/settings-learning-track.md)
* [Arbeiten mit Dateien](../get-started/fileio-learning-track.md)

![Abrufen von gestartete image](../get-started/images/build-your-app.png)

### <a name="advertising-performance-report"></a>Bericht zur Anzeigenleistung

Der [Bericht zur anzeigen-Performance](../publish/advertising-performance-report.md) in Dev Center-Dashboard bietet jetzt Metriken. Wir haben auch den [Optimieren der anzeigbarkeit Ihrer Werbeeinheiten](../monetize/optimize-ad-unit-viewability.md) Artikel aus, um Empfehlungen für das Optimieren der anzeigbarkeit Ihrer anzeigen bieten hinzugefügt.

### <a name="targeted-push-notifications"></a>Benutzerorientierte Pushbenachrichtigungen

Die Seite " [Notifications](../publish/send-push-notifications-to-your-apps-customers.md) " im Dev Center-Dashboard bietet jetzt zusätzliche Analysedaten für Ihre Benachrichtigungen in Diagramm- und weltkartenform Kartenansichten.

## <a name="videos"></a>Videos

### <a name="cwinrt"></a>C++/WinRT

C++ / WinRT ist eine neue Art der Erstellung und Nutzung von Windows-Runtime-APIs. Es verfügt über alleinige in Headerdateien implementiert und bietet Ihnen einen erstklassigen Zugriff auf moderne app-Features. [Das Video ansehen](https://www.youtube.com/watch?v=TLSul1XxppA&feature=youtu.be) , um zu erfahren, wie es funktioniert, dann [Lesen Sie die Entwicklerdokumentation](../cpp-and-winrt-apis/index.md) für Weitere Informationen.

### <a name="multi-instance-uwp-apps"></a>UWP-Apps mit mehreren Instanzen

Windows können nun mehrere Instanzen von Ihrer UWP-app mit jeweils in eine eigene getrennten Prozess ausgeführt werden. Erfahren Sie, wie Sie eine neue app erstellen, die dieses Feature, dann [Lesen Sie die Entwicklerdokumentation](../launch-resume/multi-instance-uwp.md) für Weitere Hinweise zur Verwendung unterstützt und warum Sie dieses Feature verwenden [das Video ansehen](https://www.youtube.com/watch?v=clnnf4cigd0&feature=youtu.be) .

## <a name="samples"></a>Beispiele

### <a name="customer-database-tutorial"></a>Lernprogramm für die Kunden

In diesem Lernprogramm erstellt eine einfache UWP-app für die Verwaltung von eine Liste der Kunden und führt Konzepte und Verfahren vorherrschen hilfreich. Es führt Sie durch die Implementierung von UI-Elemente und Vorgänge mit einer lokalen SQLite-Datenbank hinzufügen und losen Hinweise zum Herstellen einer Verbindung mit einer REST Remotedatenbank, wenn Sie fortfahren möchten. [Sehen Sie sich das Lernprogramm hier](../enterprise/customer-database-tutorial.md)