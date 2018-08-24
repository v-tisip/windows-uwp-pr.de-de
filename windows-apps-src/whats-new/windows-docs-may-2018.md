---
author: QuinnRadich
title: Was ist neu in Windows-Dokumente im Mai 2018 – Entwickeln von apps UWP
description: Die Windows-10-Entwicklerdokumentation für Mai 2018 und der Konferenz Microsoft Build wurden Developer Leitfaden, Videos und neue Features hinzugefügt.
keywords: Was ist neu, aktualisieren, features, Anleitungen für Entwickler, Windows 10, Mai, Build
ms.author: quradic
ms.date: 5/7/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 322bc056411095019dfc027078cbfef7de0883fb
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2842751"
---
# <a name="whats-new-in-the-windows-developer-docs-in-may-2018"></a>Was ist neu in der Windows-Entwicklerdokumente im Mai 2018

Die Entwicklerdokumentation für die Windows-Plattform wird ständig mit Informationen über neue Features für Entwickler aktualisiert. Die folgenden Featureübersichten, Hinweise für Entwickler, Videos und Beispiele haben in den Monat Mai mit der [Microsoft Build 2018](https://www.microsoft.com/build) – Entwicklerkonferenz verfügbar gemacht wurden.

Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows10 können Sie entweder [eine neue universelle Windows-App erstellen](../get-started/create-uwp-apps.md) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](../porting/index.md) vertraut machen.

## <a name="features"></a>Features

### <a name="motion-in-fluent-design"></a>Bewegung in Fluent Design

Der Benutzer der Bewegung in der Fluent-Design-System ist entwickelt, über die Grundlagen von Timing, Beschleunigung, richtungsabhängigkeit und Gravity erstellt. Anwenden von diesen Grundlagen helfen über Ihre app im Benutzerhandbuch und Rechtecke durch ihre digitale Erfahrung durch Spiegeln der natürlichen Welt. Weitere Informationen finden Sie in diesen Artikeln:

* [Übersicht über die Bewegung](../design/motion/index.md) wurde aktualisiert, um diesen Grundlagen widerspiegeln.
* [In der Praxis Bewegung](../design/motion/motion-in-practice.md) enthält Beispiele dafür, wie Sie diese Grundlagen Ihrer App anwenden.
* [Richtung und Gravity](../design/motion/directionality-and-gravity.md) verdichtet geistige Benutzermodell Ihrer App.
* [Timing und Beschleunigung](../design/motion/timing-and-easing.md) hinzugefügt der Bewegung in Ihrer app realistische.

![Bewegung in Aktion](../design/motion/images/contextual.gif)

### <a name="fluent-design-updates"></a>Fluent-Design-Updates

An den folgenden Seiten Fluent Design wurden Visual Updates und geringfügige Änderungen vorgenommen:

* [Ausrichtung, Abstand, Ränder](../design/layout/alignment-margin-padding.md)
* [Farbe](../design/style/color.md)
* [Befehlsgrundlagen](../design/basics/commanding-basics.md)
* [Fluent-Design für apps für Windows](../design/fluent-design-system/index.md)
* [Einführung in das app-design](../design/basics/design-and-ui-intro.md)
* [Navigationsgrundlagen](../design/basics/navigation-basics.md)
* [Reaktionsfähige Designtechniken](../design/layout/responsive-design.md)
* [Bildschirmgrößen und Breakpoints](../design/layout/screen-sizes-and-breakpoints-for-responsive-design.md)
* [Übersicht über die Formatvorlage](../design/style/index.md)
* [Schreibstil](../design/style/writing-style.md)

Darüber hinaus haben wir die folgenden Seiten mit neuen Informationen zu ihren Inhaltsbereiche umgeschrieben:

* [Symbole](../design/style/icons.md) enthält nun praktische Empfehlungen für die Verwendung von Symbolen und macht sie geklickt werden kann.
* [Typografie](../design/style/typography.md) konsolidiert Informationen aus ähnliche Artikel an alles aus einem einzigen Speicherort mit aktualisierten Anweisungen und Abbildungen.

![Farbe Palette Bild](../design/style/images/color/accent-color-palette.svg)

### <a name="app-installer-files-in-visual-studio"></a>App-Installer-Dateien in Visual Studio

App-Installer-Dateien können jetzt mit Visual Studio 2017, Update 15.7 erstellt werden. Automatische Updates auf Ihre apps [erfahren Sie, wie mithilfe von Visual Studio zum Erstellen einer App-Installer-Datei](../packaging/create-appinstallerfile-vs.md) und aktivieren. Wenn Sie Probleme ausführen, finden Sie unter [Problembehandlung bei der Installation mit der App-Installer-Datei](../packaging/troubleshoot-appinstaller-issues.md) , häufige Probleme und Lösungen anzeigen.

### <a name="edge-webview-control-for-windows-forms-and-wpf-applications"></a>Edge-Webansicht-Steuerelement für Windows Forms und WPF-Anwendungen

Anzeigen von Webinhalten in Ihrem desktop-Anwendung mithilfe des Steuerelements Webansicht, die zuvor nur für UWP-Clientanwendungen verfügbar. Dieses Steuerelement verwendet die Microsoft Edge Rendern von Inhalt aus einer remote-Webserver, dynamisch generierte Code oder Inhaltsdateien Engine eine Ansicht einbetten, dass rendert HTML Rich-Text formatiert. Hier finden Sie das Webansicht-Steuerelement in die neueste Version von der [Windows Community Toolkit.](https://docs.microsoft.com/windows/uwpcommunitytoolkit/)

Suchen Sie für andere Steuerelemente wie Webansicht des Windows-Community Toolkit in zukünftigen Versionen. Weitere Informationen finden Sie unter [Host UWP in WPF und Windows Forms-Anwendung steuert.](https://docs.microsoft.com/windows/uwp/xaml-platform/xaml-host-controls)

### <a name="gaze-input-and-interactions"></a>Eingabe bestaunen und damit zusammenhängende Interaktionen

[Verfolgen Sie den Blick, die Aufmerksamkeit und die Präsenz eines Benutzers anhand der Position und Bewegung seiner Augen.](../design/input/gaze-interactions.md) Diese neue leistungsfähige verwenden und interagieren mit Ihren apps UWP ist besonders hilfreich, als ein hilfstechnologie. Eingabe bestaunen außerdem überzeugende Verkaufschancen für Spiele (einschließlich Ziel Erwerb und Nachverfolgen) und andere interaktiven Szenarien, in dem herkömmlichen Eingabegeräte (Tastatur, Maus, Touch) nicht verfügbar sind.

### <a name="msix-packaging-format"></a>MSIX Packaging-Format

Auf der Microsoft Build 2018 Konferenz vorgestellt, ist MSIX ein neues Containerization-Paket-Format, das für alle Windows-Anwendungen, einschließlich Win32, Windows Forms, WPF und UWP gilt. Dieses neue Format erbt großartige Features von UWP:

* Sichere Installation und Aktualisierung. 
* Sicherheitsmodell mit einem System flexible Funktion verwaltet.
* Unterstützung für Microsoft Store, Enterprise Management und viele benutzerdefinierte Verteilung Modelle.

Tools zum Erstellen eines diese werden in einer zukünftigen Version von Visual Studio und Windows SDK verfügbar sein.

Das MSIX Packaging-Format ist ein open-Source-Format mit einer für unsere Partner zur Unterstützung der MSIX Ökosystems mit ihren Tools und Lösungen vereinfacht. Weitere Informationen zu den MSIX Packaging-Format finden, finden Sie unter [MSIX SDK](https://github.com/Microsoft/msix-packaging). 

![MSIX Verpackung Bild](images/msix.png)

### <a name="optional-packages-with-executable-code"></a>Optionale Pakete mit ausführbarem Code

Optionale Pakete in Ihrer app können jetzt ausführbaren C#-Code enthalten. [Hier erfahren Sie, wie Sie mithilfe von Visual Studio so konfigurieren Sie optional Add-On-Pakete zur Unterstützung Ihrer wichtigsten app-Pakets.](../packaging/optional-packages-with-executable-code.md)

### <a name="page-transitions"></a>Seitenübergänge

[Übergänge](../design/motion/page-transitions.md) Navigation der Benutzer zwischen den Seiten in einer app. Sie helfen Benutzern bei verstehen, wo sie in der Navigationshierarchie sind, und geben Sie Feedback zur Beziehung zwischen den Seiten.

### <a name="project-rome"></a>Projekt Rome

Das Team Project ROM hat ihre iOS und Android SDKs, Hinzufügen neuer Features wie die Benutzeraktivitäten und Umgestalten von großer Teil ihres Codes, um ein konsistentes programming über die verschiedenen SDKs bieten überholt. [Alle neuen API-Referenz und Vorgehensweisen Dokumente](https://docs.microsoft.com/windows/project-rome/) werden während der Konferenz Build 2018 Developer live wechseln.

### <a name="sets"></a>Legt

Die Funktion ist in Windows-Insider Preview erstellt verfügbar. Wenn Sie die Funktion verwenden, wird Sie app in einem Fenster gezeichnet, die mit anderen apps mit jeder app müssen eine eigene Registerkarte in der Titelleiste gemeinsam genutzt werden kann. [Entwerfen für legt](../design/shell/design-for-sets.md) hat Hinweise zum Optimieren der Leistung von Ihrer app, um bieten die beste Erfahrung in der Benutzeroberfläche festgelegt.

## <a name="developer-guidance"></a>Anleitungen für Entwickler

### <a name="get-started"></a>Erste Schritte

Haben wir unsere Get revitalized Schritten mit neuen Learning Spuren. Diese neuen Themen Ziel bieten neue Windows 10 Entwickler mit Informationen zu einige allgemeinen Aufgaben, die sie möglicherweise ausführen möchten. Sie sind nicht Lernprogramme und Handheld eine exemplarische Vorgehensweise nicht enthalten, sondern stattdessen weisen Sie darauf hin, in der Dokumentation vorhanden ist und wie sie mit. Checken Sie die überarbeitete [Erlernen der Codierung](../get-started/create-uwp-apps.md) Seite, oder Erkunden Sie jede einzelne Learning nachverfolgen:

* [Erstellen eines Formulars](../get-started/construct-form-learning-track.md)
* [Anzeigen von Kunden in einer Liste](../get-started/display-customers-in-list-learning-track.md)
* [Speichern und Laden von Einstellungen](../get-started/settings-learning-track.md)
* [Arbeiten mit Dateien](../get-started/fileio-learning-track.md)

![Erste Schritte beim Bild](../get-started/images/build-your-app.png)

### <a name="advertising-performance-report"></a>Bericht zur Anzeigenleistung

Der [Werbung Leistungsbericht](../publish/advertising-performance-report.md) im Dashboard Developer Center bietet nun Viewability Metriken. Wir haben auch [Optimieren der Viewability der Ad-Einheiten](../monetize/optimize-ad-unit-viewability.md) Artikel zum Bereitstellen von Empfehlungen zum Optimieren der Viewability der anzeigen hinzugefügt.

### <a name="targeted-push-notifications"></a>Gezielte Pushbenachrichtigungen

Die Seite [Benachrichtigungen](../publish/send-push-notifications-to-your-apps-customers.md) im Developer Center Dashboard bietet jetzt zusätzliche Analytics-Daten für alle Ihre Benachrichtigungen im Diagramm und World Kartenansichten.

## <a name="videos"></a>Videos

### <a name="cwinrt"></a>C++/WinRT

C + / WinRT ist eine neue Art des Erstellens und Verarbeiten von Windows-Runtime-APIs. Es wurde in Headerdateien ausschließlichen implementiert und bietet Ihnen erstklassige Zugriff auf modernen app-Funktionen. [Video ansehen](https://www.youtube.com/watch?v=TLSul1XxppA&feature=youtu.be) , um zu erfahren, wie es funktioniert, klicken Sie dann [der entwicklerdokumente lesen](../cpp-and-winrt-apis/index.md) , Weitere Informationen.

### <a name="multi-instance-uwp-apps"></a>UWP-Apps mit mehreren Instanzen

Windows kann jetzt Sie mehrere Instanzen von Ihrer app UWP mit jeweils in einem eigenen separaten Prozess ausgeführt werden. [Video ansehen](https://www.youtube.com/watch?v=clnnf4cigd0&feature=youtu.be) , um Hier erfahren, wie Sie eine neue app erstellen, die dieses Feature, anschließend auf [die entwicklerdokumente lesen](../launch-resume/multi-instance-uwp.md) Weitere Anleitungen unterstützt und warum dieses Feature verwenden können.

## <a name="samples"></a>Beispiele

### <a name="customer-database-tutorial"></a>Lernprogramm für Kunden

In diesem Lernprogramm erstellt eine einfache UWP-app für die Verwaltung einer Liste von Kunden und stellt die Konzepte und Methoden, insbesondere für die Entwicklung für Unternehmen. Es führt Sie durch Implementieren der Benutzeroberflächenelemente und Hinzufügen von Vorgängen für eine lokale SQLite Datenbank und weit Anleitungen für die Verbindung mit einer Remotedatenbank REST, wenn Sie fortfahren möchten. [Informieren Sie sich hier die Lernprogramms](../enterprise/customer-database-tutorial.md)