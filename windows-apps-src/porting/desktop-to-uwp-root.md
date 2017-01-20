---
author: awkoren
Description: "Machen Sie Ihre ersten Schritte mit der Desktop-zu-UWP-Brücke, und konvertieren Sie Ihre Windows-Desktopanwendung (wie Win32, WPF und Windows Forms) in eine App für die universelle Windows-Plattform (UWP)."
Search.Product: eADQiWindows 10XVcnh
title: "Portieren Ihrer Desktop-App zur universellen Windows-Plattform (UWP) mit der Desktop-Brücke"
translationtype: Human Translation
ms.sourcegitcommit: 462d2b13cefc6abb4d7c6f814ec4ee659e4afde8
ms.openlocfilehash: 1ef54c3c45113e434333058d0f039e213ea8eed2

---

# <a name="bring-your-desktop-app-to-the-universal-windows-platform-uwp-with-the-desktop-bridge"></a>Portieren Ihrer Desktop-App zur universellen Windows-Plattform (UWP) mit der Desktop-Brücke

Machen Sie Ihre ersten Schritte mit der Desktop-zu-UWP-Brücke, und konvertieren Sie Ihre Windows-Desktopanwendung in eine App für die universelle Windows-Plattform (UWP).

Die Desktop-Brücke umfasst eine Reihe von Technologien, die es Ihnen ermöglichen, Ihre Windows-Desktopanwendung (z. B. Win32, Windows Forms oder WPF) oder Ihr Spiel in eine UWP-App oder ein UWP-Spiel zu konvertieren. Nach der Konvertierung wird die Windows-Desktopanwendung gepackt, gewartet und als UWP-App-Paket (eine APPX- oder APPXBUNDLE-Datei) für Windows 10 Desktop bereitgestellt.

Es gibt zwei Bestandteile der Technologie, die das Konvertieren von Desktop-Apps in UWP-Pakete ermöglichen. Der erste Bestandteil ist der Konvertierungsprozesses, mit dem Ihre vorhandenen Binärdateien neu als UWP-Paket gepackt werden. Der Code wird beibehalten, er wird nur anders gepackt. Der zweite Bestandteil umfasst Laufzeittechnologien im Windows Anniversary-Update, mit denen die im UWP-Paket enthaltenen ausführbaren Dateien, statt in einem App-Container, als vertrauenswürdige Dateien ausgeführt werden. Diese Technologie fügt außerdem einer konvertierten App eine Paketidentität hinzu, die zur Verwendung einiger UWP-APIs erforderlich ist.

## <a name="benefits"></a>Vorteile

Im Folgenden werden einige Vorteile der Konvertierung von Windows-Desktopanwendungen aufgeführt: 

**Optimierte Bereitstellung**. Apps und Spiele, für die die Brücke verwendet wird, verfügen über eine großartige Bereitstellungsumgebung, die sicherstellt, dass Benutzer Apps zuverlässig installieren und aktualisieren können. Wenn ein Benutzer die App deinstalliert, wird sie vollständig entfernt, ohne dass irgendwelche Spuren zurückbleiben. Dadurch wird der Zeitaufwand zum Erstellen des Setups und zum Bereitstellen von Updates verringert.

**Automatische Updates und Lizenzierung**. Ihre App kann an der im Windows Store integrierten Lizenzierung und an automatischen Updatemöglichkeiten teilnehmen. Automatische Updates stellen einen sehr zuverlässigen und effizienten Mechanismus dar, da nur die geänderten Teile von Dateien heruntergeladen werden.

**Höhere Reichweite und vereinfachte Monetarisierung**. Wenn Sie Ihre Apps über den Windows Store vertreiben, können Sie Millionen Windows 10-Benutzer erreichen, die Apps, Spiele und In-App-Käufe mit lokalen Zahlungsoptionen erwerben können.

**Hinzufügen von UWP-Features**.  Sie können in Ihrem eigenen Tempo Ihrem App-Paket UWP-Features hinzufügen, beispielsweise eine XAML-Benutzeroberfläche, Aktualisierungen von Live-Kacheln, UWP-Hintergrundaufgaben, App-Dienste und vieles mehr.

**Erweiterte Anwendungsmöglichkeiten auf allen Geräten**. Wenn Sie die Brücke verwenden, können Sie Ihren Code nach und nach auf die universelle Windows-Plattform migrieren, um jedes Windows 10-Gerät zu erreichen, einschließlich Smartphones, Xbox One und HoloLens.

## <a name="prepare"></a>Vorbereiten

Die Desktop-zu-UWP-Brücke ist benutzerfreundlich gestaltet, und es sind nicht viele Schritte von Ihrer Seite erforderlich, um die App auf den Konvertierungsprozess vorzubereiten. Vor der Konvertierung sind jedoch einige Punkte und bestimmte Situationen zu berücksichtigen. Lesen Sie den Artikel [Vorbereiten Ihrer App für die Desktop-zu-UWP-Brücke](desktop-to-uwp-prepare.md), und beheben Sie alle ggf. vorhandenen Probleme Ihrer App, bevor Sie fortfahren.

## <a name="convert"></a>Konvertieren

Sie verfügen über eine Reihe von Optionen für das Konvertieren der App.

**Desktop App Converter (DAC)**. DAC ist ein Tool, das Ihre App automatisch konvertiert und signiert. DAC ist praktisch, erfolgt automatisch und ist hilfreich, wenn die App zahlreiche Systemänderungen vornimmt oder wenn nicht vollständig klar ist, was das Installationsprogramm durchführt. Informationen zu Ihren ersten Schritten finden Sie im Artikel zum [Desktop App Converter](desktop-to-uwp-run-desktop-app-converter.md). 

**Manuelles Konvertieren**. Wenn Ihre App mit XCOPY installiert wurde oder Ihnen die Änderungen bekannt sind, die das Installationsprogramm am System vornimmt, ist die manuelle Konvertierung unter Umständen die einfachste Option. Diese Option umfasst das Erstellen einer Manifestdatei, das Ausführen des Tools MakeAppx.exe sowie das Signieren des App-Pakets. Informationen zur manuellen Konvertierung finden Sie unter [Manuelles Konvertieren Ihrer App zu UWP mithilfe der Desktop-Brücke](desktop-to-uwp-manual-conversion.md). 

**Installationsprogramme von Drittanbietern**. Verschiedene beliebte Produkte und Installer von Drittanbietern unterstützen nun die Desktopbrücke und können MSI-Installationsprogramme oder konvertierte App-Pakete mit nur wenigen Klicks erstellen. Einige Optionen umfassen: 

* [InstallShield von Flexera](http://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer)
* [WiX von FireGiant](https://www.firegiant.com/r/appx) 
* [Advanced Installer von Caphyon](http://www.advancedinstaller.com/uwp-app-package)
* [RAD Studio von Embarcadero](https://www.embarcadero.com/products/rad-studio/windows-10-store-desktop-bridge) 
* [InstallAware](https://www.installaware.com/appx.htm)

Weitere Informationen finden Sie auf den Websites der einzelnen Installationsprogramme. 

## <a name="enhance"></a>Verbessern 

Sie können Ihre konvertierte Desktop-App mit diversen UWP-APIs verbessern und Features wie Live-Kacheln, Pushbenachrichtigungen usw. hinzufügen. Vollständige Codebeispiele finden Sie in den Repositorys [Desktop-App-Brücke zu UWP: Beispiele](https://github.com/Microsoft/DesktopBridgeToUWP-Samples) und [Apps für die universelle Windows-Plattform (UWP): Beispiele](https://github.com/Microsoft/Windows-universal-samples) auf GitHub. Eine vollständige Liste der unterstützten APIs finden Sie unter [Unterstützte UWP-APIs für mit der Desktop-Brücke konvertierte Apps](desktop-to-uwp-supported-api.md). 

Neben dem Aufrufen von UWP-APIs können Sie Ihre App auch mit Features erweitern, auf die nur konvertierte Apps zugreifen können. Dies umfasst Szenarien wie das Starten eines Prozesses, wenn sich der Benutzer anmeldet, oder die Integration des Datei-Explorers, was einen reibungslosen Übergang von der ursprünglichen Desktop-App zum vollständigen UWP-App-Paket ermöglichen soll. Weitere Informationen finden Sie unter [App-Erweiterungen für die Desktop-Brücke](desktop-to-uwp-extensions.md). 

## <a name="migrate"></a>Migrieren

Mithilfe der Brücke können Sie Ihren älteren Code schrittweise zu UWP migrieren, wobei die Möglichkeit, Ihre App auf Windows Desktop auszuführen und zu veröffentlichen, weiterhin besteht. Nach der vollständigen Migration zu UWP (wenn Ihre App keine WPF-/Win32-Komponenten mehr enthält), können Sie alle Windows-Geräte, einschließlich Smartphones, Xbox One und HoloLens, erreichen.

## <a name="debug"></a>Debugging

Sie können Ihre App mithilfe von Visual Studio debuggen. Detaillierte Informationen finden Sie unter [Debuggen von Apps, die mit der Desktop-Brücke konvertiert wurden](desktop-to-uwp-debug.md). 

Details zur Funktionsweise der Desktop-Brücke finden Sie unter [Hintergrundinformationen zur Desktop-Brücke](desktop-to-uwp-behind-the-scenes.md). 

## <a name="distribute"></a>Vertreiben

Der Vertrieb Ihrer App ist über den Windows Store sowie durch Querladen möglich. Ausführliche Informationen finden Sie unter [Verteilen von Apps, die mit der Desktop-Brücke konvertiert wurden](desktop-to-uwp-distribute.md). Beachten Sie, dass Sie Ihre App signieren müssen, bevor Sie sie für Benutzer bereitstellen können. Eine schrittweise Anleitung finden Sie unter [Signieren einer App, die mit der Desktop-Brücke konvertiert wurde](desktop-to-uwp-signing.md). 

## <a name="support-and-feedback"></a>Support und Feedback

Wenn beim Konvertieren Ihrer App Probleme auftreten, finden Sie Hilfe in den [Foren](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/home?forum=wpdevelop). 

Wenn Sie Feedback oder Vorschläge für Features übermitteln möchten, können Sie über [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial) Elemente übermitteln oder abstimmen. 

## <a name="in-this-section"></a>Inhalt dieses Abschnitts

| Thema | Beschreibung |
|-------|-------------|
| [Desktop App Converter](desktop-to-uwp-run-desktop-app-converter.md) | Beinhaltet Informationen zum Ausführen von Desktop App Converter. |
| [Manuelles Konvertieren Ihrer App zu UWP mithilfe der Desktop-Brücke](desktop-to-uwp-manual-conversion.md) | Enthält Informationen zum manuellen Erstellen eines App-Pakets und -Manifests. |
| [App-Erweiterungen für die Desktop-Brücke](desktop-to-uwp-extensions.md) | Optimieren Sie die konvertierte App mit Erweiterungen, um Features wie z. B. Startaufgaben und Datei-Explorer-Integration zu ermöglichen. |
| [Unterstützte UWP-APIs für mit der Desktop-Brücke konvertierte Apps](desktop-to-uwp-supported-api.md) | Erfahren Sie, welche UWP-APIs für Ihre konvertierte Desktop-App verfügbar sind. |
| [Debuggen von Apps, die mit der Desktop-Brücke konvertiert wurden](desktop-to-uwp-debug.md) | Erläutert die Optionen für das Debuggen der konvertierten App. | 
| [Signieren einer App, die mit der Desktop-Brücke konvertiert wurde](desktop-to-uwp-signing.md) | Erfahren Sie, wie Sie Ihr konvertiertes App-Paket mit einem Zertifikat signieren können. |
| [Verteilen von Apps, die mit der Desktop-Brücke konvertiert wurden](desktop-to-uwp-distribute.md) | Erfahren Sie, wie Sie die konvertierte App an Benutzer verteilen können.  |
| [Hintergrundinformationen zur Desktop-Brücke](desktop-to-uwp-behind-the-scenes.md) | Beschäftigen Sie sich eingehender damit, wie die Desktop-zu-UWP-Brücke funktioniert. | 
| [Bekannte Probleme mit der Desktop-Brücke](desktop-to-uwp-known-issues.md) | Listet bekannte Probleme bei der Desktop-zu-UWP-Brücke auf. | 
| [Desktop-App-Brücke zu UWP: Codebeispiele](https://github.com/Microsoft/DesktopBridgeToUWP-Samples) | Codebeispiele auf GitHub veranschaulichen Funktionen konvertierter Apps. |


<!--HONumber=Dec16_HO3-->


