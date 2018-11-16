---
author: normesta
Description: This article lists things you need to know before packaging your desktop application. You may not need to do much to get your app ready for the packaging process.
Search.Product: eADQiWindows 10XVcnh
title: Vorbereiten des Verpackens eine desktop-Anwendung (Desktop-Brücke)
ms.author: normesta
ms.date: 05/18/20188
ms.topic: article
keywords: windows10, UWP
ms.assetid: 71a57ca2-ca00-471d-8ad9-52f285f3022e
ms.localizationpriority: medium
ms.openlocfilehash: ba89ab06062f5ba40bb96f4d558bd89a16e591d1
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6987267"
---
# <a name="prepare-to-package-a-desktop-application"></a>Vorbereiten des Verpackens eine desktop-Anwendung

In diesem Artikel sind Punkte aufgeführt, die Sie vor dem Verpacken von Desktop-Apps wissen sollten. Müssen Sie möglicherweise nicht viel tun, um Ihre Anwendung für die Verpackung vorzubereiten, aber wenn eines der folgenden Elemente bezieht sich auf Ihre Anwendung müssen Sie sich vor der Verpackung darum kümmern. Denken Sie daran, dass Lizenzierung und automatische Updates im Rahmen des MicrosoftStore erfolgen, sodass Sie alle mit diesen Aufgaben verbundenen Features aus Ihrer Codebasis entfernen können.

>[!IMPORTANT]
>Die Fähigkeit zum Erstellen eines Windows-app-Pakets für Ihre desktop-Anwendung (auch bekannt als der Desktop-Brücke) wurde in Windows 10, Version 1607, eingeführt und kann nur in Projekten für die Windows 10 Anniversary Update (10.0; verwendet werden Build 14393) oder einer neueren Version in Visual Studio.

+ __Ihre Anwendung erfordert eine Version von .NET älter als 4.6.2 sind__. Sie müssen sicherstellen, dass Ihre Anwendung in .NET 4.6.2 ausgeführt wird. Sie können keine Versionen erfordern oder weiterverteilen, die älter als 4.6.2 sind. Dies ist die .NET-Version, die im Windows10 Anniversary Update ausgeliefert wurde. Überprüfen, dass Ihre Anwendung in dieser Version funktioniert wird sichergestellt, dass Ihre Anwendung weiterhin mit zukünftigen Updates von Windows 10 kompatibel ist.  Wenn Ihre Anwendung das .NET Framework 4.0 oder höher ausgerichtet ist, es wird erwartet, .NET 4.6.2 ausgeführt werden, aber Sie sollten dies dennoch testen.

+ __Die Anwendung immer mit erhöhten Sicherheitsberechtigungen ausgeführt wird__. Die Anwendung muss als interaktiver Benutzer ausgeführt werden können. Benutzer, die Ihre Anwendung aus dem Microsoft Store installieren möglicherweise keine Systemadministratoren, so dass Ihre Anwendung erhöhte ausgeführt werden, die es für Standardbenutzer nicht korrekt ausgeführt. Apps, die für erhöhte Rechte für einen beliebigen Teil ihrer Funktionalität benötigen, werden nicht im MicrosoftStore akzeptiert.

+ __Die Anwendung erfordert einen Kernelmodustreiber oder ein Windowsdienst__. Die Brücke eignet sich für eine App, ein Kernelmodustreiber oder ein Windows-Dienst, die unter einem Systemkonto ausgeführt werden müssen, werden jedoch nicht unterstützt. Verwenden Sie anstelle eines Windows-Diensts eine [Hintergrundaufgabe](https://msdn.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task).

+ __Ihre App-Module werden im Prozess für Prozesse geladen, die nicht im Windows-App-Paket enthalten sind__. Dies ist nicht zulässig. Prozessinterne Erweiterungen, beispielsweise [Shellerweiterungen](https://msdn.microsoft.com/library/windows/desktop/dd758089.aspx), werden nicht unterstützt. Wenn zwei Apps in einem Paket enthalten sind, können Sie jedoch die prozessübergreifende Kommunikation zwischen diesen verwenden.

+ __Ihre Anwendung verwendet eine benutzerdefinierte Application User Model ID (AUMID)__. Wenn der Prozess [SetCurrentProcessExplicitAppUserModelID](https://msdn.microsoft.com/library/windows/desktop/dd378422.aspx) zum Festlegen einer eigenen ANWENDUNGSBENUTZERMODELL, kann er nur die AUMID, die von der Anwendung Modell modellumgebung/vom Windows-app-Paket generierte verwenden. Sie können keine benutzerdefinierten Anwendungsbenutzermodell-IDs definieren.

+ __Ihre Anwendung ändert die HKLM-Registrierungsstruktur (HKEY_LOCAL_MACHINE)__. Jeder Versuch, Ihre Anwendung einen HKLM-Schlüssel erstellen oder einen zum Ändern zu öffnen führt zu einem Fehler Zugriff verweigert. Denken Sie daran, dass Ihre Anwendung hat eine eigene private virtualisierte Ansicht der Registrierung, damit das Konzept einer Benutzer- und computerweiten Registrierungsstruktur (Was ist, was ist der HKLM) nicht angewendet werden kann. Sie müssen stattdessen eine andere Möglichkeit finden, um das zu erreichen, wozu Sie HKLM verwendet haben, beispielsweise Schreiben in HKEY_CURRENT_USER (HKCU).

+ __Ihre Anwendung verwendet einen Ddeexec-Registrierungsunterschlüssel zum Starten einer anderen app__. Verwenden Sie stattdessen einen der DelegateExecute-Verbhandler genau wie von den verschiedenen Activatable*-Erweiterungen in dem [App-Paketmanifest](https://msdn.microsoft.com/library/windows/apps/br211474.aspx) konfiguriert.

+ __Die Anwendung schreibt in den AppData-Ordner oder die Registrierung, um Daten freizugeben mit einer anderen app__. Nach der Konvertierung wird AppData an den lokalen App-Datenspeicher weitergeleitet, der ein privater Speicher für jede UWP-App ist.

  Alle Einträge, die die Anwendung in der Registrierungsstruktur HKEY_LOCAL_MACHINE schreibt werden in eine isolierte Binärdatei umgeleitet, und alle Einträge, die die Anwendung in der Registrierungsstruktur HKEY_CURRENT_USER schreibt werden in einem privaten Speicherort pro Benutzer, pro app platziert. Weitere Informationen zur Datei- und Registrierungsumleitung finden Sie unter [Hintergrundinformationen zur Desktop-Brücke](desktop-to-uwp-behind-the-scenes.md).  

  Verwenden Sie verschiedene Methoden für die prozessübergreifende Datenfreigabe. Weitere Informationen finden Sie unter [Speichern und Abrufen von Einstellungen und anderen App-Daten](https://msdn.microsoft.com/windows/uwp/app-settings/store-and-retrieve-app-data).

+ __Die Anwendung in das Installationsverzeichnis für Ihre app schreibt__. Zum Beispiel schreibt Ihrer Anwendung in eine Protokolldatei, die Sie in demselben Verzeichnis wie die EXE-Datei einfügen. Dies wird nicht unterstützt. Sie müssen daher einen anderen Speicherort wählen, z. B. den lokalen App-Datenspeicher.

+ __Die Installation Ihrer Anwendung erfordert eine Benutzerinteraktion__. Das Installationsprogramm der Anwendung muss in der Lage, im Hintergrund ausgeführt und muss alle erforderlichen Komponenten, die nicht über standardmäßig auf einem sauberen Betriebssystemimage installieren.

+ __Ihre Anwendung verwendet das aktuelle Arbeitsverzeichnis__. Zur Laufzeit Arbeitsverzeichnis nicht Ihre verpackte desktop-Anwendung das gleiche, die Sie zuvor in Ihrem Desktop angegeben. LNK-Verknüpfung. Sie müssen das aktuelle Arbeitsverzeichnis zur Laufzeit zu ändern, wenn das richtige Verzeichnis notwendig für Ihre Anwendung ordnungsgemäß funktioniert.

+ __Ihre Anwendung benötigt UIAccess__. Wenn Ihre Anwendung `UIAccess=true` für das `requestedExecutionLevel`-Element im UAC-Manifest angibt, wird die Konvertierung in eine UWP-App derzeit nicht unterstützt. Weitere Informationen finden Sie unter [Sicherheit bei der Benutzeroberflächenautomatisierung – Übersicht](https://msdn.microsoft.com/library/ms742884.aspx).

+ __Ihre Anwendung macht COM-Objekte__. Prozesse und Erweiterungen innerhalb des Pakets können OLE & COM-Server sowohl im Prozess und Out-of-Process (OOP) registrieren und verwenden.  Der Creators Update stellt verpackte COM-Unterstützung bereit, die die Möglichkeit bietet, OLE & OOP-COM-Server zu registrieren, die außerhalb des Pakets sichtbar sind.  Weitere Informationen finden Sie unter [COM-Server und OLE-Dokument-Support für Desktop-Brücke](https://blogs.windows.com/buildingapps/2017/04/13/com-server-ole-document-support-desktop-bridge/#bjPyETFgtpZBGrS1.97).

   Die verpackte COM-Unterstützung funktioniert mit den vorhandenen COM-APIs. Sie funktioniert aber nicht bei Anwendungserweiterungen, die vom direkten Lesen der Registrierung abhängig sind, da der Speicherort für die verpackte COM privat ist.

+ __Ihre Anwendung macht GAC-Assemblys zur Verwendung durch andere Prozesse zu verhindern__. In der aktuellen Version kann nicht Ihrer Anwendung GAC-Assemblys zur Verwendung durch Prozesse, die von ausführbaren Dateien stammen, die für Ihr Windows-app-Paket verfügbar machen. Prozesse aus dem Paket können GAC-Assemblys wie gewohnt registrieren und verwenden, aber sie sind nicht extern sichtbar. Dies bedeutet, dass Interoperabilitätsszenarien wie OLE nicht funktionieren, wenn sie von externen Prozessen aufgerufen werden.

+ __Ihre Anwendung ist C-Laufzeitbibliotheken (CRT) auf eine nicht unterstützte Weise verknüpfen__. Die Microsoft C/C++-Laufzeitbibliothek enthält Routinen für die Programmierung für das Microsoft Windows-Betriebssystem. Diese Routinen automatisieren viele allgemeine Programmieraufgaben, die von den Programmiersprachen C# und C++ nicht bereitgestellt werden. Wenn Ihre Anwendung C/C++-Laufzeitbibliothek verwendet, müssen Sie sicherstellen, dass sie auf eine unterstützte Weise verknüpft ist.

    Visual Studio 2017 unterstützt die statische und dynamische Verknüpfung, damit Ihr Code gängige DLL-Dateien verwenden kann, und statische Verknüpfung, um die Bibliothek direkt in Ihren Code, mit der aktuellen Version der CRT, zu verknüpfen. Wenn möglich, empfehlen wir die dynamische Verknüpfung mit VS 2017 Anwendungsverwendung.

    Unterstützung in früheren Versionen von Visual Studio variiert. Weitere Informationen finden Sie in der folgenden Tabelle:

    <table>
    <th>Version von Visual Studio</td><th>Dynamische Verknüpfung</th><th>Statische Verknüpfung</th></th>
    <tr><td>2005 (VC 8)</td><td>Nicht unterstützt</td><td>Unterstützt</td>
    <tr><td>2008 (VC 9)</td><td>Nicht unterstützt</td><td>Unterstützt</td>
    <tr><td>2010 (VC 10)</td><td>Unterstützt</td><td>Unterstützt</td>
    <tr><td>2012 (VC 11)</td><td>Unterstützt</td><td>Nicht unterstützt</td>
    <tr><td>2013 (VC 12)</td><td>Unterstützt</td><td>Nicht unterstützt</td>
    <tr><td>2015 und 2017 (VC 14)</td><td>Unterstützt</td><td>Unterstützt</td>
    </table>

    Hinweis: In allen Fällen müssen Sie eine Verknüpfung zur neuesten öffentlich verfügbaren CRT herstellen.

+ __Die Anwendung installiert und lädt Assemblys aus dem Windows-Seite-an-Seite-Ordner__. Beispielsweise wird die Anwendung verwendet C-Laufzeitbibliotheken VC8 oder VC9 und verknüpft diese dynamisch aus Windows Side-by-Side-Ordner, was bedeutet, dass Ihr Code gängige DLL-Dateien aus einem freigegebenen Ordner verwendet wird. Dies wird nicht unterstützt. Sie müssen diese statisch verknüpfen, indem sie eine Verknüpfung mit den verteilbaren Bibliotheksdateien direkt in den Code erstellen.

+ __Ihre Anwendung verwendet eine Abhängigkeit im Ordner "System32/SysWOW64"__. Damit diese DLL-Dateien funktionieren, müssen Sie sie im virtuellen Dateisystem Ihres Windows-App-Pakets einschließen. Dadurch wird sichergestellt, dass die Anwendung verhält, als wären die DLL-Dateien in das **System32**installiert/**SysWOW64** -Ordner. Erstellen Sie im Stammordner des Pakets einen Ordner mit dem Namen **VFS**. Erstellen Sie innerhalb dieses Ordners die Ordner **SystemX64** und **SystemX86**. Platzieren Sie die 32-Bit-Version Ihrer DLL-Datei im Ordner **SystemX86** und die 64-Bit-Version im Ordner **SystemX64**.

+ __Ihre App verwendet ein VCLibs-Frameworkpaket__. Die VCLibs-Bibliotheken können direkt aus dem MicrosoftStore installiert werden, wenn sie im Windows-App-Paket als Abhängigkeit definiert sind. Beispielsweise, wenn Ihre Anwendung Dev11-VCLibs-Pakete verwendet, ändern Sie Folgendes zu Ihrem Paket Anwendungsmanifest: unter der `<Dependencies>` Knoten hinzufügen:  
`<PackageDependency Name="Microsoft.VCLibs.110.00.UWPDesktop" MinVersion="11.0.24217.0" Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US" />`  
Während der Installation aus dem MicrosoftStore wird die korrekte Version des VCLibs-Frameworks (x86 oder x64) vor der Installation der App installiert.  
Die Abhängigkeiten werden nicht installiert, wenn die Anwendung durch querladen installiert wird. Um die Abhängigkeiten manuell auf dem Computer zu installieren, müssen Sie das passende VCLibs-Frameworkpaket für die Desktop-Brücke herunterladen und installieren. Weitere Informationen über diese Szenarien finden Sie unter [Verwenden der Visual C++-Laufzeitbibliotheken in einem Centennial-Projekt](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/).

  **Frameworkpakete**:

  * [VC14.0-Frameworkpakete für Desktop-Brücke](https://www.microsoft.com/download/details.aspx?id=53175)
  * [VC12.0-Frameworkpakete für Desktop-Brücke](https://www.microsoft.com/download/details.aspx?id=53176)
  * [VC11.0-Frameworkpakete für Desktop-Brücke](https://www.microsoft.com/download/details.aspx?id=53340)


+ __Die Anwendung enthält eine angepasste Sprungliste__. Bei der Verwendung von Sprunglisten müssen mehrere Probleme und Vorsichtsmaßnahme berücksichtigt werden.

    - __Die Architektur der App passt nicht zum Betriebssystem.__  Sprunglisten derzeit nicht ordnungsgemäß, wenn die Anwendung und die Betriebssystemarchitektur nicht übereinstimmen (z. B. eine X86 X64 ausgeführte Anwendung Windows). Zu diesem Zeitpunkt kann nicht umgangen werden anders als Ihre Anwendung übereinstimmenden Architektur neu kompilieren.

    - __Ihre Anwendung erstellt sprunglisteneinträge und ruft [icustomdestinationlist:: Setappid](https://msdn.microsoft.com/library/windows/desktop/dd378403(v=vs.85).aspx) oder [SetCurrentProcessExplicitAppUserModelID](https://msdn.microsoft.com/library/windows/desktop/dd378422(v=vs.85).aspx)__. Legen Sie „AppID“ nicht programmgesteuert im Code fest. Andernfalls werden die Sprunglisteneinträge nicht angezeigt. Wenn Ihre Anwendung eine benutzerdefinierte Id benötigt, geben Sie sie mithilfe der Manifestdatei. Anweisungen finden Sie in [einer desktop-Anwendung manuell zu verpacken](desktop-to-uwp-manual-conversion.md) . Die App-ID für die Anwendung ist im Abschnitt *YOUR_PRAID_HERE* angegeben.

    - __Die Anwendung fügt einen sprunglistenshell-Link, der auf eine ausführbare Datei im Paket verweist__. Sie können ausführbare Dateien in Ihrem Paket nicht direkt aus einer Sprungliste starten (mit Ausnahme des absoluten Pfads einer eigenen EXE-Datei einer App). Registrieren Sie stattdessen einen app-ausführungsalias (mit dem Ihre verpackte desktop-Anwendung über ein Schlüsselwort gestartet werden soll, als befände sie sich im Pfad), und legen Sie den linkzielpfad stattdessen auf den Alias. Weitere Informationen zur Verwendung der AppExecutionAlias-Erweiterungs finden [Integration Ihrer desktop-Anwendung mit Windows 10](desktop-to-uwp-extensions.md). Hinweis: Wenn Ressourcen des Links in der Sprungliste der ursprünglichen EXE-Datei entsprechen müssen, müssen Sie Ressourcen wie etwa das Symbol mithilfe von [**SetIconLocation**](https://msdn.microsoft.com/library/windows/desktop/bb761047(v=vs.85).aspx) und den Anzeigenamen mit „PKEY_Title“ festlegen (wie bei anderen benutzerdefinierten Einträgen).

    - __Die Anwendung fügt sprunglisteneinträge, die Ressourcen in das app Paket nach absoluten Pfaden verweisen__. Der Installationspfad der Anwendung unter Umständen ändern, wenn Pakete aktualisiert werden, ändern den Speicherort der Ressourcen (z. B. Symbole, Dokumente, ausführbare Datei usw.). Falls sprunglisteneinträge auf derartige Ressourcen nach absoluten Pfaden verweisen, muss die Anwendung die Sprungliste in regelmäßigen Abständen (z. B. auf Anwendung starten) aktualisieren ordnungsgemäße Auflösung der Pfade sicherzustellen. Sie können stattdessen auch die UWP-[**Windows.UI.StartScreen.JumpList**](https://msdn.microsoft.com/library/windows/apps/windows.ui.startscreen.jumplist.aspx)-APIs verwenden. Diese APIs ermöglichen den Verweis auf Zeichenfolgen- und Bildressourcen mithilfe des relativen ms-resource-URI-Paketschemas (das zudem Sprache, DPI und hohen Kontrast berücksichtigt).

+ __Ihre Anwendung startet ein Hilfsprogramm zum Ausführen von Aufgaben__. Vermeiden Sie das Starten von Befehlshilfsprogrammen wie PowerShell und Cmd.exe. Tatsächlich, wenn Benutzer Ihre Anwendung auf einem System, die Windows 10 S ausgeführt wird installieren, klicken Sie dann Ihre Anwendung können sie alle zu starten nicht. Dies kann Ihre Anwendung aus der Übermittlung an den Microsoft Store blockieren, da alle an den Microsoft Store übermittelten apps mit Windows 10 s kompatibel sein müssen.

Das Starten eines Hilfsprogramms kann oft eine bequeme Methode für das Abrufen von Informationen aus dem Betriebssystem, Zugreifen auf die Registrierung oder das Zugreifen auf Systemfunktionen bereitstellen. Sie können jedoch stattdessen UWP-APIs verwenden, um diese Aufgaben auszuführen. Diese APIs sind leistungsstärker, da sie keine separate ausführbare Datei an, aber wichtiger ist, sie die Anwendung halten von außerhalb des Pakets. Das Design der app bleibt im Einklang mit die Netzwerkisolation, Vertrauensstellung und Sicherheit, die mit einer Anwendung, die Sie verpackt haben, und Ihre Anwendung verhält sich erwartungsgemäß auf Systemen mit Windows 10 S.

+ __Ihre Anwendung Hosts-add-ins, -Plug-ins, oder Erweiterungen__.   In vielen Fällen werden Erweiterungen im COM-Stil wahrscheinlich weiterhin funktionieren, sofern die Erweiterung nicht verpackt wurde und sie als vertrauenswürdig installiert wurde. Ist, dass die Installationsprogramme ihre vertrauenswürdigen Funktionen verwenden können, um die Registrierung ändern und einer beliebigen Stelle Erweiterungsdateien Ihrer Anwendung geht davon aus, um sie zu finden.

   Jedoch, wenn diese Erweiterungen verpackt und als ein Windows-app-Paket installiert, nicht funktionieren, da jedes Paket (die Host-Anwendung und die Erweiterung) voneinander isoliert sein wird. Um mehr darüber zu erfahren wie Anwendungen werden vom System isoliert, sehen [hinter den Kulissen der Desktop-Brücke](desktop-to-uwp-behind-the-scenes.md).

 Alle Anwendungen und Erweiterungen, die Benutzer auf einem System mit Windows10 S installieren, müssen als Windows-App-Pakete installiert werden. Wenn Sie beabsichtigen, Ihre Erweiterungen zu verpacken oder Sie die Contributors Verpackung empfehlen möchten, erwägen Sie also, wie Sie Kommunikation zwischen dem Host-Anwendungspaket und Erweiterung Pakete vereinfachen können. Eine Möglichkeit wäre die Verwendung eines [App-Dienstes](../launch-resume/app-services.md).

+ __Ihre Anwendung wird Code generiert__. Die Anwendung kann Code generieren, der es nutzt im Arbeitsspeicher, jedoch schreiben Code auf den Datenträger vermeiden, da der Windows-App-Zertifizierungsprozess diesen Code vor der app-Übermittlung nicht überprüfen kann. Darüber hinaus wird nicht apps, die Code auf den Datenträger schreiben ordnungsgemäß auf Systemen mit Windows 10 s ausgeführt Dies kann Ihre Anwendung aus der Übermittlung an den Microsoft Store blockieren, da alle an den Microsoft Store übermittelten apps mit Windows 10 s kompatibel sein müssen.

>[!IMPORTANT]
> Nachdem Sie Ihre Windows-app-Paket erstellt haben, testen Sie Ihre Anwendung, um sicherzustellen, dass es ordnungsgemäß auf Systemen funktioniert, die Windows 10 s ausgeführt werden. Alle an den Microsoft Store übermittelten apps müssen mit kompatibel sein Windows 10 s-Apps, die nicht kompatibel sind, wird nicht im Store akzeptiert werden. Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](desktop-to-uwp-test-windows-s.md).

## <a name="next-steps"></a>Nächste Schritte

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).

**Erstellen eines Windows-App-Pakets für Ihre Desktop-App**

Weitere Informationen erhalten Sie unter [Erstellen eines Windows-App-Pakets](desktop-to-uwp-root.md#convert).
