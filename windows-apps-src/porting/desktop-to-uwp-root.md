---
author: normesta
Description: "Erstellen Sie eine moderne Windows-App-Paket für Ihre vorhandenen Windows Forms-, WPF- oder Win32-Anwendung oder ein Spiel. Fügen Sie moderne Umgebungen für Windows10-Benutzer hinzu und Vereinfachung Sie die Bereitstellung und Monetarisierung."
Search.Product: eADQiWindows 10XVcnh
title: "Desktop-Brücke"
ms.author: normesta
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: 74373c24-f948-43bb-aa85-01e2e8e87162
ms.openlocfilehash: 1830c1661325afe68e8e7cd32528ec075e098b1d
ms.sourcegitcommit: 77bbd060f9253f2b03f0b9d74954c187bceb4a30
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2017
---
# <a name="desktop-bridge"></a>Desktop-Brücke

Nehmen Sie Ihre vorhandene Desktop-App und fügen Sie moderne Umgebungen für Windows10-Benutzer hinzu. Sorgen Sie über die Verteilung über den Windows Store für eine größerer Reichweite in internationalen Märkten. Sie können Ihre App durch die Nutzung von Features aus dem Store viel einfacher vermarkten. Natürlich müssen Sie den Store nicht verwenden. Sie können auch Ihre vorhandenen Vertriebskanäle nutzen.
<div style="float: left; padding: 10px">
    ![Abbildung der Desktop-zu-UWP-Brücke](images/desktop-to-uwp/desktop-bridge-4.png)
</div>
Der Desktop-zu-UWP-Brücke ist der Infrastruktur, die wir in die Plattform integriert haben. Mit ihr können Sie Ihre Windows Forms-, WPF- oder Win32-Desktop-App oder Ihr Spiel effizient mithilfe über ein modernes Windows-App-Paket verteilen.

Dieses Paket gibt Ihrer App eine Identität. Mit dieser Identität hat Ihre Desktop-App Zugriff auf UWP-APIs (Universelle Windows-Plattform). Sie können diese für moderne und ansprechende Benutzeroberflächen wie z.B. Live-Kacheln und Benachrichtigungen verwenden.  Verwenden Sie eine einfache bedingte Kompilierung und Lautzeitüberprüfungen, um UWP-Code nur dann auszuführen, wenn Ihre App unter Windows10 ausgeführt wird.

Abgesehen von den Code, mit denen Sie zur Verbesserung der Windows10-Umgebung nutzen, bleibt Ihre App unverändert und Sie können sie weiterhin für Ihre vorhandene Windows7-, Windows Vista- oder Windows XP-Benutzerbasis bereitstellen. Unter Windows10 wird Ihre App genau wie heute weiterhin im vertrauenswürdigen Benutzermodus ausgeführt.

> [!NOTE]
> Sehen Sie sich <a href="https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373?l=oZG0B1WhD_8406218965/">diese Reihe</a> von kurzen Videos an, die von der Microsoft Virtual Academy veröffentlicht wurden. Diese Videos erläutern den gesamten Prozess der Integration Ihrer Desktop-Apps auf die Universelle Windows-Plattform (UWP).

## <a name="benefits"></a>Vorteile

Hier sind einige Gründe für die Erstellung eines Windows-App-Pakets für Ihre Desktop-Anwendung:

**Optimierte Bereitstellung**. Apps und Spiele, die die Brücke verwenden, profitieren von einer hervorragenden Bereitstellung. Die Bereitstellung stellt sicher, dass Benutzer zuverlässig eine App installieren und aktualisieren können. Wenn ein Benutzer die App deinstalliert, wird sie vollständig entfernt, ohne dass irgendwelche Spuren zurückbleiben. Dadurch wird der Zeitaufwand zum Erstellen des Setups und zum Bereitstellen von Updates verringert.

**Automatische Updates und Lizenzierung**. Ihre App kann an der im Windows Store integrierten Lizenzierung und an automatischen Updatemöglichkeiten teilnehmen. Automatische Updates stellen einen sehr zuverlässigen und effizienten Mechanismus dar, da nur die geänderten Teile von Dateien heruntergeladen werden.

**Höhere Reichweite und vereinfachte Monetarisierung**. Wenn Sie Ihre Apps über den Windows Store vertreiben, können Sie Millionen Windows10-Benutzer erreichen, die Apps, Spiele und In-App-Käufe mit lokalen Zahlungsoptionen erwerben können.

**Hinzufügen von UWP-Features**.  Sie können in Ihrem eigenen Tempo Ihrem App-Paket UWP-Features hinzufügen, beispielsweise eine XAML-Benutzeroberfläche, Aktualisierungen von Live-Kacheln, UWP-Hintergrundaufgaben, App-Dienste und vieles mehr.

**Erweiterte Anwendungsmöglichkeiten auf allen Geräten**. Wenn Sie die Brücke verwenden, können Sie Ihren Code nach und nach auf die universelle Windows-Plattform migrieren, um jedes Windows10-Gerät zu erreichen, einschließlich Smartphones, Xbox One und HoloLens.

Eine vollständige Liste der Vorteile finden Sie unter [Desktop-Brücke](https://developer.microsoft.com/windows/bridges/desktop).

## <a name="prepare"></a>Vorbereiten

Möchten Sie Ihre App auf dem [Windows App Store](https://www.microsoft.com/store/apps) veröffentlichen? Wenn ja, beginnen Sie mit dem Ausfüllen [dieses Formulars](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge). Microsoft nimmt mit Ihnen Kontakt auf und beginnt den Onboardingprozess. Im Rahmen dieses Prozesses reservieren Sie einen Namen im Store und erhalten Informationen, die Sie benötigen, um ein Windows-App-Paket zu erstellen.

Lesen Sie dann den Artikel [Vorbereiten Ihrer Desktop-App](desktop-to-uwp-prepare.md), und beheben Sie alle ggf. vorhandenen Probleme Ihrer App, bevor Sie ein Windows-App-Paket für sie erstellen. Sie müssen eventuell nicht viele Änderungen an Ihrer App vornehmen, bevor Sie das Paket erstellen. Es gibt jedoch bestimmte Situationen, bei denen Sie Ihre App optimieren müssen, bevor Sie ein Paket erstellen können.

<span id="convert" />
## <a name="package"></a>Paket

Hier sind einige Tools für die Erstellung eines Windows-App-Pakets für Ihre App.

### <a name="desktop-app-converter"></a>Desktop App Converter

Zwar taucht der Begriff „Konverter“ im Namen dieses Tools auf, es konvertiert aber Ihre App aber nicht wirklich. Ihre App bleibt unverändert. Das Tool generiert ein Windows-App-Paket für Sie. Es ist in Fällen sehr praktisch, in denen Ihre App viele Systemänderungen vornimmt, oder wenn Sie sich unsicher sind, welche Funktion das Installationsprogramm hat.

Der Desktop App Converter erledigt für Sie auch einige zusätzliche Aufgaben. Nachfolgend sind einige aufgelistet.

* Automatisches Registrieren Ihrer Preview-Handler, Miniaturansichthandler, Eigenschaftenhandler, Firewall-Regeln, URL-Kennzeichen.

* Automatisches Registrieren Ihrer Dateizuordnungen, mit denen Benutzer Dateien mithilfe der **Art**-Spalte im Datei-Explorer gruppieren können.

* Registrieren Ihrer öffentlichen COM-Server.

* Erstellen eines Zertifikats, das Sie verwenden können, um Ihre App auszuführen.

* Überprüfen Sie Ihrer App für die Desktop-Brücke- und Windows Store-Anforderungen.

Weitere Informationen finden Sie unter [Packen einer App mit dem Desktop App Converter (Desktop-zu-UWP-Brücke)](desktop-to-uwp-run-desktop-app-converter.md)

### <a name="manual-packaging"></a>Manuelles Verpacken

Wenn Sie eine präzise Steuerung der Konvertierung bevorzugen, können Sie eine Manifestdatei erstellen und anschließend das **MakeAppx.exe**-Tool ausführen, um das Windows-App-Paket zu erstellen.

Dieser Ansatz kann sinnvoll sein, wenn Sie mit den Änderungen vertraut sind, die das Installationsprogramm am System vornimmt, oder wenn Sie kein Installationsprogramm besitzen und Sie Ihre App anhand des physischen Kopierens von Dateien zu einem Ordner oder mithilfe der Befehle wie **Xcopy** installieren. Das Fehlen eines Installationsprogramms sollte Sie jedoch nicht dazu bewegen, Ihre App manuell zu verpacken. Sie können den Desktop App Converter verwenden, um Ihre App zu verpacken, auch wenn Sie kein Installationsprogramm besitzen.

Weitere Informationen finden Sie in [Manuelles Verpacken einer App (Desktop-zu-UWP-Brücke)](desktop-to-uwp-manual-conversion.md)

### <a name="visual-studio"></a>Visual Studio

Diese Option ist ähnlich zur oben beschriebenen manuellen Option, mit Ausnahme der Tatsache, dass Visual Studio einige Aufgaben für Sie übernimmt, wie etwa das Generieren eines App-Pakets und visuellen Objekten für Ihre App. Stellen Sie sich Visual Studio als ein Tool vor, mit dem Sie Ihre App manuell verpacken können, und das Ihnen einige zusätzliche Vorteile bietet.

Weitere Informationen finden Sie in [Verpacken von .NET-Apps mit Visual Studio (Desktop-zu-UWP-Brücke)](desktop-to-uwp-packaging-dot-net.md)

### <a name="third-party-installer"></a>Installationsprogramme von Drittanbietern.

 Einige beliebte Drittanbieter-Produkte und -Installer unterstützen jetzt Desktop-zu-UWP-Brücke. Sie können zum Generieren von MSI-Installationsprogrammen oder verpackten App-Paketen mit nur wenigen Klicks verwenden. Obwohl wir keine Dokumentation zur Verwendung dieser Tools bereitstellen, finden Sie auf unseren Websites zusätzliche Informationen.

 Hier finden Sie einige Optionen:

#### <a name="advanced-installer"></a>Erweiterter Installer

Caphyon bietet ein kostenloses, GUI-basiertes Desktop-App-Verpackungstool an, das Ihnen hilft, ein Windows-App-Paket für Ihre Anwendung mit nur wenigen Klicks zu erstellen. Es kann jedes Installationsprogramm verwenden; auch solche, die im Hintergrund ausgeführt werden, und führt eine Überprüfung durch, um festzustellen, ob die App für die Verpackung geeignet ist.
<div style="float: left; padding: 10px; width: 20%">
     ![Advanced Installer-Logo](images/desktop-to-uwp/Advanced_Installer_Vertical.png)
</div>
Der Desktop App Converter kann auch mit Hyper-V und [VMware](http://www.vmware.com/) integriert werden. Dies bedeutet, dass Sie Ihren eigenen virtuellen Computern verwenden können, ohne ein entsprechendes [Docker](https://docs.docker.com/)-Bild herunterladen zu müssen, das über 3GB groß sein kann.

Sie können den [Erweiterten Installer](http://www.advancedinstaller.com/) verwenden, um eine MSI-Datei und [Windows-App-Pakete](http://www.advancedinstaller.com/uwp-app-package.html) von vorhandenen Projekten zu generieren. Sie können den erweiterten Installer auch verwenden, um Windows-App-Pakete zu importieren, die Sie mithilfe des Microsoft Desktop App Converters generieren. Nach dem Importieren können Sie sie mithilfe der visuellen Tools verwalten, die speziell für UWP-Apps entwickelt wurden.

Der erweiterte Installer bietet auch eine Erweiterung für Visual Studio2017 und 2015, die zum [erstellen und debuggen von Desktop-Brücke-Apps](http://www.advancedinstaller.com/debug-desktop-bridge-apps.html) verwendet werden können.

In diesem [Video](https://www.youtube.com/watch?v=cmLKgn04Vfg&feature=youtu.be) finden Sie einen kurzen Überblick.

#### <a name="cloudhouse-compatibility-containers"></a>Cloudhouse Compatibility-Container

Unternehmenskunden, die über Branchenanwendungen verfügen, die mit Windows10 und Windows10 S nicht kompatibel sind, können mit den Compatibility-Containern von Cloudhouse Windows XP- und Windows7-Apps zu UWP konvertieren und diese dann über den Windows Store für Unternehmen oder Microsoft Intune bereitstellen, ohne den Quellcode zu ändern.
<div style="float: left; padding: 10px; width: 20%">
     ![Cloudhouse Compatibility-Container](images/desktop-to-uwp/container.png)
</div>
Cloudhouse bietet einen Auto Packager, der eine Anwendung nimmt und einen Compatibility-Container erstellt, indem er die App für Betriebssysteme wie Windows XP verpackt. Der Container kann in das neue UWP-Format konvertiert werden, indem sie mit dem Desktop Bridge Converter-Tool integriert wird und ein Windows-App-Paket erstellt wird.

Der Auto Packager verwendet Installationsdaten/Datenerfassungen und Laufzeitanalysen, um einen Container für die Anwendung zu erstellen. Dieser enthält die Anwendungsdateien und die Registrierungsdaten sowie ein Umleitungsmodul, mit dem die Anwendung unter Windows10 ausgeführt werden kann. Außerdem kann es jegliche Laufzeitumgebungen oder Voraussetzungen zum Ausführen der Anwendung enthalten und isolieren. So entstehen keine Konflikte mit anderen Apps oder Laufzeitumgebungen, die bereits installiert sind.


Sehen Sie sich die [Blog](http://www.cloudhouse.com/resources/release-solution-to-get-any-line-of-business-app-to-uwp)-Ankündigung zur Unterstützung für Universelle Windows-Apps und den Windows Store für Unternehmen an.

#### <a name="firegiant"></a>FireGiant

Mit der [FireGiant Appx-Erweiterung](https://www.firegiant.com/products/wix-expansion-pack/appx) können Sie die Windows-App-Pakete und MSI-Pakete aus dem gleichen WiX-Quellcode erstellen. Jedes Mal, wenn Sie eine Erstellung durchführen, können Sie dies für die Desktop-Brücke in Windows10 mit einem Windows-App-Paket und für frühere Versionen von Windows mit MSI durchführen.
<div style="float: left; padding: 10px; width: 20%">
     ![Advanced Installer-Logo](images/desktop-to-uwp/FG3rdPartyLogo.png)
</div>
Die FireGiant Appx-Erweiterung verwendet statische Analysen und eine intelligente Emulation Ihrer WiX-Projekte zum Erstellen von Windows-App-Paketen, ohne, dass der Datenträgerspeicherplatz oder Laufzeit-Overhead von Containern oder virtuellen Computern erforderlich wird.

Da die FireGiant Appx-Erweiterung Ihren Installer nicht über eine Ausführung konvertieren, können Sie das WiX-Installationsprogramm pflegen, ohne es immer wieder in Windows-App-Pakete zu konvertieren. Alle Benutzer der verschiedenen Versionen von Windows erhalten die neuesten Verbesserungen und brauchen sich darum zu kümmern, ob MSI- und Windows-App-Pakete identisch sind.

Sehen Sie sich dieses [Video](https://www.youtube.com/watch?v=AFBpdBiAYQE) an und überprüfen Sie, mit wie wenigen Codezeilen FireGiant-CEO Rob Mensching eine Appx-Version (Windows-App-Paket)des beliebten Open-Source-Tools 7 Zip erstellt und dann die Windows-App und MSI-Pakete mit Änderungen im selben WiX-Quellcode verbessert.

#### <a name="installaware"></a>InstallAware

Install**Aware** bietet kostenlose Install**Aware**-Erweiterungen für Visual Studio2012-2017. Sie Können sie verwenden, um Windows-App-Pakete mit einem einzigen Klick in die [Visual Studio-Symbolleiste](https://www.installaware.com/visual-studio-installer-2015.htm) zu erstellen.
<div style="float: left; padding: 10px; width: 20%">
    ![FireGiant-Logo](images/desktop-to-uwp/installaware.png)
</div>
Sie können außerdem mit Package**Aware** (Snapshot-freie Setup-Erfassung) oder dem Database Import Wizard (für alle MSI-Installationsprogramme und MSM-Merge-Module) jedes Setup importieren, auch dann, wenn Sie nicht den Quellcode für das Setup haben. Sie können [GUI-Tools](https://www.installaware.com/scripting-two-way-integrated-ide.htm) zur visuellen oder skriptgesteuerten Pflege und Erweiterung Ihrer Importe verwenden.

[Erweiterte APPX-Erstellungsoptionen](https://www.installaware.com/mhtml5/desktop/appx.htm) ermöglichen die Unterstützung von Windows Store-Beiträgen oder die Erstellung von signierten Windows-App-Paket-Binärdateien für die Verteilung per Querladen. Sie können sogar **WSA**-Installer-Pakete (Windows Server-Anwendungen) für Bereitstellungen auf **Nano Server** erstellen – und zwar über einen einzigen Quellcode und mit vollständiger Unterstützung für die [Befehlszeile Automatisierung](https://www.installaware.com/scripting-automation-interface.htm) (zusätzlich zu einer GUI).

Install**Aware** bietet außerdem eine [Open-Source-Version](https://www.installaware.com/gnu.asp) einer **APPX-Builder-Bibliothek**, sowie ein Beispiel-Befehlszeile-Applet, unter der GNU Affero GPL-Lizenz. Diese sind für die Verwendung mit Open-Source-Plattformen wie WiX entwickelt worden.

#### <a name="installshield"></a>InstallShield

InstallShield bietet eine einzige Lösung zur Entwicklung von MSI- und EXE-Installationsprogrammen, Erstellung von UWP-Paketen und WSA-Paketen und zur Virtualisierung von Anwendungen mit nur minimalem Aufwand für das Skripting, Erstellen von Code und Überarbeiten der Anwendung.
<div style="float: left; padding: 10px; width: 20%">
    ![InstallShield-Logo](images/desktop-to-uwp/InstallShield-logo.jpg)
</div>
Scannen Sie Ihr InstallShield-Projekt in wenigen Sekunden und sparen Sie sich stundenlanges Nachforschen. Erkennen Sie automatisch potenzielle Kompatibilitätsprobleme zwischen der Anwendung und den UWP- und WSA-Paketen.

Bereiten Sie für den Windows Store vor und vereinfachen Sie die Softwareinstallation unter Windows10 durch die Erstellung von UWP-App-Paketen aus Ihren vorhandenen InstallShield-Projekten. Erstellen von Windows-Installer- und UWP-App-Pakete für alle gewünschten Bereitstellungsszenarien Ihrer Kunden. Unterstützung von Nano Server- und Windows Server2016-Bereitstellungen durch die Erstellung von WSA-Paketen aus Ihren vorhandenen InstallShield-Projekten.

Entwickeln Sie Ihre Installation in Modulen für eine einfachere Bereitstellung und Wartung, und fügen Sie anschließend die Komponenten und die Abhängigkeiten zum Erstellungszeitpunkt in einem einzigen UWP-App-Paket für den Windows Store hinzu. Für die direkte Bereitstellung außerhalb des Stores bündeln Sie Ihre UWP-App-Pakete und anderen Abhängigkeiten zusammen mit einem Installationsprogramm oder einem erweiterten UI-Installer.

Erfahren Sie mehr in diesem [E-Book](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fresources.flexerasoftware.com%2Fweb%2Fpdf%2FeBook-IS-Your-Fast-Track-to-Profit.pdf&data=02%7C01%7Cnormesta%40microsoft.com%7C86b9a00bc8e345c2ac6208d4ba464802%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C1%7C636338258409706554&sdata=IAYNp9nFc8B5ayxwrs%2FQTWowUmOda6p%2Fn%2BjdHea257M%3D&reserved=0).


#### <a name="rad-studio"></a>RAD Studio

Mehr unter [RAD Studio by Embarcadero](https://www.embarcadero.com/products/rad-studio/windows-10-store-desktop-bridge)

## <a name="integrate"></a>integrieren

Wenn Ihre App mit dem System integrieren werden muss (z.B. zum Einrichten der Firewall-Regeln), können Sie diese Dinge im Paketmanifest Ihrer App beschreiben und das Systems erledigt den Rest. Für die meisten dieser Aufgaben müssen Sie gar keinen Code schreiben. Mit etwas XML im Manifest, können Sie Aktionen wie etwa das Starten eines Prozesses bei der Anmeldung eines Benutzers, die Integration Ihrer App in den Datei-Explorer und das Hinzufügen Ihrer App zu einer Liste der Druckerziele, die in anderen Apps angezeigt wird, durchführen.

Weitere Informationen finden Sie in [Integrieren Sie Ihre App in Windows10 (Windows-Desktop-Brücke)](desktop-to-uwp-extensions.md).

## <a name="enhance"></a>Verbessern

Nachdem Sie Ihre App verpackt haben, können Sie Features wie Live-Kacheln und Push-Benachrichtigungen nutzen. Einige dieser Funktionen können die Interaktion mit Ihrer App erheblich verbessern. Es kostet nur sehr wenig Zeit, diese Funktionen hinzuzufügen. Für einige Erweiterungen ist etwas mehr Code erforderlich.

Weitere Informationen finden Sie unter [Verbessern Sie Ihre Desktopanwendung für Windows10](desktop-to-uwp-enhance.md).

## <a name="extend"></a>Erweitern

Einige Windows 10-Umgebungen (z. B. eine touch-fähige UI-Seite) müssen sich in einem Modern-App-Container befinden. In der Regel sollten Sie zuerst ermitteln, ob Sie Ihre Umgebung über die [Erweiterung](desktop-to-uwp-enhance.md) Ihre vorhandene Desktopanwendung mit UWP-APIs hinzufügen können. Wenn Sie eine UWP-Komponente verwenden müssen, um die Erweiterung umzusetzen, können Sie der Projektmappe ein UWP-Projekt hinzufügen und App-Diensten für die Kommunikation zwischen Ihrer Desktop-App und der UWP-Komponente verwenden.

Weitere Informationen finden Sie unter [Erweitern Ihrer Desktopanwendung mit modernen UWP-Komponenten](desktop-to-uwp-extend.md).

## <a name="migrate"></a>Migrieren

Sie können Ihren älteren Code schrittweise zu UWP migrieren, wobei die Möglichkeit, Ihre App auf Windows Desktop auszuführen und zu veröffentlichen, weiterhin besteht. Nach der vollständigen Migration zu UWP (wenn Ihre App keine WPF-/Win32-Komponenten mehr enthält), können Sie alle Windows-Geräte, einschließlich Smartphones, Xbox One und HoloLens, erreichen.

## <a name="test"></a>Testen

Um Ihre App vor der Verteilung in einer realistischen Umgebung zu testen, empfiehlt es sich, Ihre App zu signieren und sie anschließend zu installieren. Mehr unter [Tests für Ihre App](https://docs.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-debug#test-your-app).

>[!IMPORTANT]
> Wenn Sie Ihre App im Windows Store veröffentlichen möchten, stellen Sie sicher, dass Ihre App auf Geräten, auf denen Windows10 S ausgeführt wird, ordnungsgemäß ausgeführt wird. Dies ist eine Store-Anforderung. Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](desktop-to-uwp-test-windows-s.md).

## <a name="validate"></a>Überprüfen

Damit Ihre App möglichst gute Chancen auf eine Veröffentlichung im Windows Store oder [Windows-Zertifizierung](http://go.microsoft.com/fwlink/p/?LinkID=309666) hat, sollten Sie sie auf Ihrem Computer überprüfen und testen, bevor Sie sie zur Zertifizierung übermitteln.

Wenn Sie den DAC verwenden, um Ihre App zu verpacken, können Sie das neue ``-Verify``-Kennzeichen verwenden, um Ihr Paket hinsichtlich der Desktop-Brücke- und Store-Anforderungen zu überprüfen. Weitere Informationen finden Sie unter [Verpacken einer App, Signieren der App, und Vorbereiten der App für die Übermittlung an den Store](desktop-to-uwp-run-desktop-app-converter.md#optional-parameters).

Wenn Sie Visual Studio verwenden, können Sie Ihre App über den Assistenten **App-Pakete erstellen** überprüfen. Weitere Informationen finden Sie in [Erstellen eines App-Pakets](../packaging/packaging-uwp-apps.md#create-an-app-package).

Um das Tool manuell auszuführen, lesen Sie sich [Zertifizierungskit für Windows-Apps](../debug-test-perf/windows-app-certification-kit.md) durch.

Informationen zur Liste der Tests, die die Windows-Apps-Zertifizierung für die Überprüfung Ihrer App verwendet, finden Sie unter [App-Tests für Windows-Desktop-Brücke](../debug-test-perf/windows-desktop-bridge-app-tests.md).

## <a name="distribute"></a>Verteilen

Sie können Ihre App durch die Veröffentlichung im Windows Store oder durch das Querladen es auf andere Systeme verteilen.

Weitere Informationen finden Sie in [Verteilen einer verpacken Desktop-App (Desktop-Brücke)](desktop-to-uwp-distribute.md)

## <a name="support-and-feedback"></a>Support und Feedback

**Antworten auf spezifische Fragen**

Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).

**Geben Sie Feedback zu diesem Artikel**

Verwenden Sie den Kommentarabschnitt weiter unten.

## <a name="in-this-section"></a>Inhalt dieses Abschnitts

| Thema | Beschreibung |
|-------|-------------|
| [Vorbereiten des Verpackens einer App](desktop-to-uwp-prepare.md) | Enthält eine Liste von Elementen, die vor dem Verpacken Ihrer Desktop-App überprüft werden sollten. |
| [Verpacken einer App mit dem Desktop App Converter (Desktop-Brücke)](desktop-to-uwp-run-desktop-app-converter.md) | Beinhaltet Informationen zum Ausführen von Desktop App Converter. |
| [Manuelles Verpacken einer App (Desktop-Brücke)](desktop-to-uwp-manual-conversion.md) | Enthält Informationen zum manuellen Erstellen eines App-Pakets und -Manifests. |
| [Verpacken von .NET-Apps mit Visual Studio (Desktop-Brücke)](desktop-to-uwp-packaging-dot-net.md)| Enthält Informationen zum Verpassen Ihrer Desktop-App mithilfe von Visual Studio. |
| [Integrieren Ihrer App in Windows10 (Desktop-Brücke)](desktop-to-uwp-extensions.md) | Integrieren Sie Ihre App mit Windows10 mithilfe von Aufgaben in der Paketmanifestdatei Ihres Paketprojekts. |
| [Verbessern Ihrer Desktopanwendung für Windows10](desktop-to-uwp-enhance.md)| Verwenden Sie UWP-APIs, um moderne Umgebungen für Windows10-Benutzer hinzuzufügen. |
| [UWP-APIs für eine verpackte Desktop-App (Desktop-Brücke)](desktop-to-uwp-supported-api.md) | Erfahren Sie, welche UWP-APIs für Ihre verpackte Desktop-App verfügbar sind. |
| [Erweitern Ihrer Desktopanwendung mit modernen UWP-Komponenten](desktop-to-uwp-extend.md)| Fügen Sie erweiterte Funktionen hinzu, die in einem UWP-App-Container ausgeführt werden müssen. Verbinden Sie Ihre Desktop-App mit dem UWP-Prozess mithilfe von App-Diensten.|
| [Ausführen, Debuggen und Testen einer verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-debug.md) | Erläutert die Optionen für das Debuggen der verpacken App. |
| [in Verteilen einer verpacken Desktop-App (Desktop-Brücke)](desktop-to-uwp-distribute.md) | Erfahren Sie, wie Sie die konvertierte App an Benutzer verteilen können.  |
| [Hintergrundinformationen zur Desktop-Brücke (Desktop-Brücke)](desktop-to-uwp-behind-the-scenes.md) | Beschäftigen Sie sich eingehender damit, wie die Desktop-zu-UWP-Brücke funktioniert. |
| [Bekannte Probleme (Desktop-Brücke)](desktop-to-uwp-known-issues.md) | Listet bekannte Probleme bei der Desktop-zu-UWP-Brücke auf. |
| [Desktop-Brücke: Codebeispiele](https://github.com/Microsoft/DesktopBridgeToUWP-Samples) | Codebeispiele auf GitHub veranschaulichen Funktionen konvertierter Apps. |
