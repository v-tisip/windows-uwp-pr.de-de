---
author: normesta
Description: This article lists things you need to know before packaging your app with the Desktop Bridge. You may not need to do much to get your app ready for the packaging process.
Search.Product: eADQiWindows 10XVcnh
title: Vorbereiten der Verpackung einer App (Desktop-Brücke)
ms.author: normesta
ms.date: 05/18/20188
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 71a57ca2-ca00-471d-8ad9-52f285f3022e
ms.localizationpriority: medium
ms.openlocfilehash: 46e71812acdad92a5d017cee44490e7d8cc0de32
ms.sourcegitcommit: c0f58410c4ff5b907176b1ffa275e2c202f099d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2018
ms.locfileid: "1905391"
---
# <a name="prepare-to-package-an-app-desktop-bridge"></a>Vorbereiten der Verpackung einer App (Desktop-Brücke)

In diesem Artikel sind Punkte aufgeführt, die Sie vor dem Verpacken von Desktop-Apps wissen sollten. Sie müssen möglicherweise nicht viel tun, um Ihre App für die Verpackung vorzubereiten. Trifft jedoch einer der folgenden Punkte auf Ihre Anwendung zu, müssen Sie sich vor der Verpackung darum kümmern. Denken Sie daran, dass Lizenzierung und automatische Updates im Rahmen des MicrosoftStore erfolgen, sodass Sie alle mit diesen Aufgaben verbundenen Features aus Ihrer Codebasis entfernen können.

>[!IMPORTANT]
>Der Desktop-Brücke wurde in Windows10, Version 1607, eingeführt und kann nur in Projekten für das Windows10 Anniversary Update (10.0; Build 14393) oder einer neueren Version in Visual Studio verwendet werden.

+ __Ihre App erfordert eine frühere .NET-Version als 4.6.2__. Sie müssen sicherstellen, dass Ihre App in .NET 4.6.2 ausgeführt wird. Sie können keine Versionen erfordern oder weiterverteilen, die älter als 4.6.2 sind. Dies ist die .NET-Version, die im Windows10 Anniversary Update ausgeliefert wurde. Durch die Überprüfung, dass Ihre App in dieser Version funktioniert, wird sichergestellt, dass Ihre App weiterhin mit zukünftigen Updates von Windows10 kompatibel ist.  Wenn Ihre App auf .NET Framework 4.0 oder höher ausgerichtet ist, wird davon ausgegangen, dass sie unter .NET 4.6.2 ausgeführt wird, aber Sie sollten dies dennoch testen.

+ __Ihre App wird immer mit erhöhten Sicherheitsberechtigungen ausgeführt__. Ihre App muss als interaktiver Benutzer ausgeführt werden können. Benutzer, die Ihre App über den MicrosoftStore installieren, sind möglicherweise keine Systemadministratoren. Wenn für die Ausführung Ihrer App erhöhte Rechte erforderlich sind, wird die App für Standardbenutzer nicht korrekt ausgeführt. Apps, die für erhöhte Rechte für einen beliebigen Teil ihrer Funktionalität benötigen, werden nicht im MicrosoftStore akzeptiert.

+ __Ihre App erfordert einen Kernelmodustreiber oder einen Windows-Dienst__. Die Brücke eignet sich für eine App, ein Kernelmodustreiber oder ein Windows-Dienst, die unter einem Systemkonto ausgeführt werden müssen, werden jedoch nicht unterstützt. Verwenden Sie anstelle eines Windows-Diensts eine [Hintergrundaufgabe](https://msdn.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task).

+ __Ihre App-Module werden im Prozess für Prozesse geladen, die nicht im Windows-App-Paket enthalten sind__. Dies ist nicht zulässig. Prozessinterne Erweiterungen, beispielsweise [Shellerweiterungen](https://msdn.microsoft.com/library/windows/desktop/dd758089.aspx), werden nicht unterstützt. Wenn zwei Apps in einem Paket enthalten sind, können Sie jedoch die prozessübergreifende Kommunikation zwischen diesen verwenden.

+ __Ihre App verwendet eine benutzerdefinierte Anwendungsbenutzermodell-ID (Application User Model ID, AUMID)__. Wenn der Prozess [SetCurrentProcessExplicitAppUserModelID](https://msdn.microsoft.com/library/windows/desktop/dd378422.aspx) zum Festlegen einer eigenen Anwendungsbenutzermodell-ID aufruft, kann er nur die von der App-Modellumgebung/vom Windows-App-Paket generierte Anwendungsbenutzermodell-ID verwenden. Sie können keine benutzerdefinierten Anwendungsbenutzermodell-IDs definieren.

+ __Ihre App ändert die HKLM-Registrierungsstruktur (HKEY_LOCAL_MACHINE)__. Bei jedem Versuch, einen HKLM-Schlüssel zu erstellen oder einen zum Ändern zu öffnen, wird der Zugriff verweigert. Denken Sie daran, dass Ihre App über eine eigene private virtualisierte Ansicht der Registrierung verfügt. Damit kann das Konzept einer benutzer- und computerweiten Registrierungsstruktur (Zweck von HKLM) nicht angewendet werden. Sie müssen stattdessen eine andere Möglichkeit finden, um das zu erreichen, wozu Sie HKLM verwendet haben, beispielsweise Schreiben in HKEY_CURRENT_USER (HKCU).

+ __Ihre App verwendet einen DDEEXEC-Registrierungsunterschlüssel zum Starten einer anderen App__. Verwenden Sie stattdessen einen der DelegateExecute-Verbhandler genau wie von den verschiedenen Activatable*-Erweiterungen in dem [App-Paketmanifest](https://msdn.microsoft.com/library/windows/apps/br211474.aspx) konfiguriert.

+ __Ihre App schreibt in den AppData-Ordner oder die Registrierung, um Daten für eine andere App freizugeben__. Nach der Konvertierung wird AppData an den lokalen App-Datenspeicher weitergeleitet, der ein privater Speicher für jede UWP-App ist.

  Alle Einträge, die Ihre App in der Registrierungsstruktur HKEY_LOCAL_MACHINE schreibt werden in eine isolierte Binärdatei umgeleitet, und alle Einträge, die Ihre App in der Registrierungsstruktur HKEY_CURRENT_USER schreibt werden in einem privaten Speicherort pro Benutzer, pro App platziert. Weitere Informationen zur Datei- und Registrierungsumleitung finden Sie unter [Hintergrundinformationen zur Desktop-Brücke](desktop-to-uwp-behind-the-scenes.md).  

  Verwenden Sie verschiedene Methoden für die prozessübergreifende Datenfreigabe. Weitere Informationen finden Sie unter [Speichern und Abrufen von Einstellungen und anderen App-Daten](https://msdn.microsoft.com/windows/uwp/app-settings/store-and-retrieve-app-data).

+ __Ihre App schreibt in das Installationsverzeichnis für die App__. Ihre App schreibt z. B. in eine Protokolldatei, die sich in demselben Verzeichnis wie die EXE-Datei befindet. Dies wird nicht unterstützt. Sie müssen daher einen anderen Speicherort wählen, z. B. den lokalen App-Datenspeicher.

+ __Ihre App-Installation erfordert eine Benutzerinteraktion__. Der App-Installer muss automatisch ausgeführt werden können und muss alle erforderlichen Komponenten installieren, die nicht standardmäßig auf einem sauberen Betriebssystemimage aktiviert sind.

+ __Ihre App verwendet das aktuelle Arbeitsverzeichnis__. Zur Laufzeit nutzt die verpackte Desktop-App nicht das gleiche Arbeitsverzeichnis, das Sie zuvor in Ihrer Desktop-LNK-Verknüpfung angegeben haben. Sie müssen das aktuelle Arbeitsverzeichnis zur Laufzeit ändern, wenn das richtige Verzeichnis notwendig ist, damit Ihre App ordnungsgemäß funktioniert.

+ __Ihre App benötigt UIAccess__. Wenn Ihre Anwendung `UIAccess=true` für das `requestedExecutionLevel`-Element im UAC-Manifest angibt, wird die Konvertierung in eine UWP-App derzeit nicht unterstützt. Weitere Informationen finden Sie unter [Sicherheit bei der Benutzeroberflächenautomatisierung – Übersicht](https://msdn.microsoft.com/library/ms742884.aspx).

+ __Ihre App macht COM-Objekte verfügbar__. Prozesse und Erweiterungen innerhalb des Pakets können OLE & COM-Server sowohl im Prozess und Out-of-Process (OOP) registrieren und verwenden.  Der Creators Update stellt verpackte COM-Unterstützung bereit, die die Möglichkeit bietet, OLE & OOP-COM-Server zu registrieren, die außerhalb des Pakets sichtbar sind.  Weitere Informationen finden Sie unter [COM-Server und OLE-Dokument-Support für Desktop-Brücke](https://blogs.windows.com/buildingapps/2017/04/13/com-server-ole-document-support-desktop-bridge/#bjPyETFgtpZBGrS1.97).

   Die verpackte COM-Unterstützung funktioniert mit den vorhandenen COM-APIs. Sie funktioniert aber nicht bei Anwendungserweiterungen, die vom direkten Lesen der Registrierung abhängig sind, da der Speicherort für die verpackte COM privat ist.

+ __Ihre App macht GAC-Assemblys zur Verwendung durch andere Prozesse verfügbar__. In der aktuellen Version kann Ihre App GAC-Assemblys nicht zur Verwendung durch Prozesse verfügbar machen, die von ausführbaren Dateien stammen, die sich außerhalb Ihres Windows-App-Pakets befinden. Prozesse aus dem Paket können GAC-Assemblys wie gewohnt registrieren und verwenden, aber sie sind nicht extern sichtbar. Dies bedeutet, dass Interoperabilitätsszenarien wie OLE nicht funktionieren, wenn sie von externen Prozessen aufgerufen werden.

+ __Ihre App verknüpft C-Laufzeitbibliotheken (CRT) auf eine nicht unterstützte Weise__. Die Microsoft C/C++-Laufzeitbibliothek enthält Routinen für die Programmierung für das Microsoft Windows-Betriebssystem. Diese Routinen automatisieren viele allgemeine Programmieraufgaben, die von den Programmiersprachen C# und C++ nicht bereitgestellt werden. Wenn Ihre App eine C/C++-Laufzeitbibliothek verwendet, müssen Sie sicherstellen, dass sie auf eine unterstützte Weise verknüpft ist.

    Visual Studio 2017 unterstützt die statische und dynamische Verknüpfung, damit Ihr Code gängige DLL-Dateien verwenden kann, und statische Verknüpfung, um die Bibliothek direkt in Ihren Code, mit der aktuellen Version der CRT, zu verknüpfen. Wir empfehlen, dass Ihre App möglichst die dynamische Verknüpfung mit VS 2017 verwendet.

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

+ __Ihre App installiert und lädt Assemblys aus dem Windows-Seite-an-Seite-Ordner__. Beispielsweise verwendet Ihre App C-Laufzeitbibliotheken VC8 oder VC9 und verknüpft diese dynamisch aus dem Windows-Seite-an-Seite-Ordner, was bedeutet, dass Ihr Code die gemeinsamen DLL-Dateien aus einem freigegebenen Ordner verwendet. Dies wird nicht unterstützt. Sie müssen diese statisch verknüpfen, indem sie eine Verknüpfung mit den verteilbaren Bibliotheksdateien direkt in den Code erstellen.

+ __Ihre App verwendet eine Abhängigkeit im Ordner System32/SysWOW64__. Damit diese DLL-Dateien funktionieren, müssen Sie sie im virtuellen Dateisystem Ihres Windows-App-Pakets einschließen. Dadurch wird sichergestellt, dass sich die App verhält, als ob die DLL-Dateien im Ordner **System32**/**SysWOW64** installiert wären. Erstellen Sie im Stammordner des Pakets einen Ordner mit dem Namen **VFS**. Erstellen Sie innerhalb dieses Ordners die Ordner **SystemX64** und **SystemX86**. Platzieren Sie die 32-Bit-Version Ihrer DLL-Datei im Ordner **SystemX86** und die 64-Bit-Version im Ordner **SystemX64**.

+ __Ihre App verwendet ein VCLibs-Frameworkpaket__. Die VCLibs-Bibliotheken können direkt aus dem MicrosoftStore installiert werden, wenn sie im Windows-App-Paket als Abhängigkeit definiert sind. Wenn Ihre App beispielsweise Dev11-VCLibs-Pakete verwendet, ändern Sie Folgendes am App-Paketmanifest: Fügen Sie unter dem `<Dependencies>`-Knoten Folgendes hinzu:  
`<PackageDependency Name="Microsoft.VCLibs.110.00.UWPDesktop" MinVersion="11.0.24217.0" Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US" />`  
Während der Installation aus dem MicrosoftStore wird die korrekte Version des VCLibs-Frameworks (x86 oder x64) vor der Installation der App installiert.  
Die Abhängigkeiten werden nicht installiert, wenn die App durch Querladen installiert wird. Um die Abhängigkeiten manuell auf dem Computer zu installieren, müssen Sie das passende VCLibs-Frameworkpaket für die Desktop-Brücke herunterladen und installieren. Weitere Informationen über diese Szenarien finden Sie unter [Verwenden der Visual C++-Laufzeitbibliotheken in einem Centennial-Projekt](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/).

  **Frameworkpakete**:

  * [VC14.0-Frameworkpakete für Desktop-Brücke](https://www.microsoft.com/download/details.aspx?id=53175)
  * [VC12.0-Frameworkpakete für Desktop-Brücke](https://www.microsoft.com/download/details.aspx?id=53176)
  * [VC11.0-Frameworkpakete für Desktop-Brücke](https://www.microsoft.com/download/details.aspx?id=53340)


+ __Ihre App enthält eine angepasste Sprungliste__. Bei der Verwendung von Sprunglisten müssen mehrere Probleme und Vorsichtsmaßnahme berücksichtigt werden.

    - __Die Architektur der App passt nicht zum Betriebssystem.__  Wenn die App- und die Betriebssystemarchitektur nicht übereinstimmen (z.B. eine x86-App unter einem x64-Windows) funktionieren Sprunglisten derzeit nicht ordnungsgemäß. Zurzeit gibt es keine Umgehung. Sie können die App nur mit einer übereinstimmenden Architektur neu compilieren.

    - __Ihre App erstellt Sprunglisteneinträge und ruft [ICustomDestinationList::SetAppID](https://msdn.microsoft.com/library/windows/desktop/dd378403(v=vs.85).aspx) oder [SetCurrentProcessExplicitAppUserModelID](https://msdn.microsoft.com/library/windows/desktop/dd378422(v=vs.85).aspx)__ auf. Legen Sie „AppID“ nicht programmgesteuert im Code fest. Andernfalls werden die Sprunglisteneinträge nicht angezeigt. Wenn Ihre App eine benutzerdefinierte ID benötigt, geben Sie sie mithilfe der Manifestdatei an. Weitere Informationen finden Sie unter [Einer App manuell verpacken (Desktop-Brücke)](desktop-to-uwp-manual-conversion.md). Die App-ID für die Anwendung ist im Abschnitt *YOUR_PRAID_HERE* angegeben.

    - __Ihre App fügt einen Sprunglistenshell-Link hinzu, der auf eine ausführbare Datei im Paket verweist__. Sie können ausführbare Dateien in Ihrem Paket nicht direkt aus einer Sprungliste starten (mit Ausnahme des absoluten Pfads einer eigenen EXE-Datei einer App). Registrieren Sie stattdessen einen App-Ausführungsalias (mit dem die verpackte Desktop-App über ein Schlüsselwort gestartet werden kann, als befände sie sich im PFAD), und legen Sie den Linkzielpfad stattdessen auf den Alias fest. Weitere Informationen zur Verwendung der appExecutionAlias-Erweiterung finden Sie unter [Integrieren Ihrer App in Windows10 (Desktop-Brücke)](desktop-to-uwp-extensions.md). Hinweis: Wenn Ressourcen des Links in der Sprungliste der ursprünglichen EXE-Datei entsprechen müssen, müssen Sie Ressourcen wie etwa das Symbol mithilfe von [**SetIconLocation**](https://msdn.microsoft.com/library/windows/desktop/bb761047(v=vs.85).aspx) und den Anzeigenamen mit „PKEY_Title“ festlegen (wie bei anderen benutzerdefinierten Einträgen).

    - __Ihre App fügt Sprunglisteneinträge hinzu, die auf Ressourcen im Paket Ihrer App nach absoluten Pfaden verweisen__. Der Installationspfad der App ändert sich möglicherweise, wenn Pakete aktualisiert werden. Dadurch ändert sich auch der Ort der Ressourcen (z.B. Symbole, Dokumente, ausführbare Dateien usw.). Falls Sprunglisteneinträge auf derartige Ressourcen nach absoluten Pfaden verweisen, muss die App ihre Sprungliste in regelmäßigen Abständen (z.B. beim App-Start) aktualisieren, um eine ordnungsgemäße Auflösung der Pfade sicherzustellen. Sie können stattdessen auch die UWP-[**Windows.UI.StartScreen.JumpList**](https://msdn.microsoft.com/library/windows/apps/windows.ui.startscreen.jumplist.aspx)-APIs verwenden. Diese APIs ermöglichen den Verweis auf Zeichenfolgen- und Bildressourcen mithilfe des relativen ms-resource-URI-Paketschemas (das zudem Sprache, DPI und hohen Kontrast berücksichtigt).

+ __Ihre App startet ein Hilfsprogramm zum Ausführen von Aufgaben__. Vermeiden Sie das Starten von Befehlshilfsprogrammen wie PowerShell und Cmd.exe. Wenn Benutzer Ihre App auf einem System mit Windows10 S installieren, wird Ihre App nicht in der Lage sein, sie alle zu starten. Die kann die Übermittlung Ihre App an den MicrosoftStore blockieren, da alle Übermittlung an den MicrosoftStore mit Windows10 S kompatibel sein müssen.

Das Starten eines Hilfsprogramms kann oft eine bequeme Methode für das Abrufen von Informationen aus dem Betriebssystem, Zugreifen auf die Registrierung oder das Zugreifen auf Systemfunktionen bereitstellen. Sie können jedoch stattdessen UWP-APIs verwenden, um diese Aufgaben auszuführen. Diese APIs sind leistungsstärker, da sie für die Ausführung keine separate ausführliche Datei benötigen. Darüber hinaus hindern sie eine Ausführung der App außerhalb des Pakets. Das Design der App bleibt im Einklang mit der Netzwerkisolation, Vertrauensstellung und Sicherheit, die zu einer mit der Desktop-Brücke verpackten Anwendung gehören, und Ihre App verhält sich erwartungsgemäß auf Systemen mit Windows10 S.

+ __Ihre App hostet Add-ins, -Plug-Ins oder Erweiterungen__.   In vielen Fällen werden Erweiterungen im COM-Stil wahrscheinlich weiterhin funktionieren, sofern die Erweiterung nicht verpackt wurde und sie als vertrauenswürdig installiert wurde. Grund dafür ist, dass die Installationsprogramme ihre vertrauenswürdigen Funktionen verwenden können, um die Registrierung zu bearbeiten und Erweiterungsdateien an beliebigen Stellen zu platzieren, damit die Host-App sie findet.

   Wenn diese Erweiterungen jedoch verpackt und als Windows-App-Paket installiert werden, werden sie nicht funktionieren, da jedes Paket (die Host-App und die Erweiterung) voneinander isoliert sein wird. Weitere Informationen über wie Desktop-Brücke Anwendungen aus dem System isoliert finden Sie unter [Hinter den Kulissen der Desktop-Brücke](desktop-to-uwp-behind-the-scenes.md).

 Alle Anwendungen und Erweiterungen, die Benutzer auf einem System mit Windows10 S installieren, müssen als Windows-App-Pakete installiert werden. Wenn Sie also beabsichtigen, Ihre Erweiterungen zu verpacken oder Sie Ihren Mitwirkenden eine Verpackung empfehlen möchten, sollten Sie sich überlegen, wie Sie die Kommunikation zwischen dem Host-App-Paket und der Erweiterungspakete vereinfachen können. Eine Möglichkeit wäre die Verwendung eines [App-Dienstes](../launch-resume/app-services.md).

+ __Ihre App generiert Code__. Ihre App kann Code generieren, den sie im Arbeitsspeicher verwendet. Vermeiden Sie es jedoch, Code auf einen Datenträger zu schreiben, da der Windows-App-Zertifizierungsprozess diesen Code vor der App-Übermittlung nicht überprüfen kann. Darüber hinaus werden Apps, die Code auf den Datenträger Schreiben, nicht ordnungsgemäß auf Systemen mit Windows10 S ausgeführt. Dadurch kann die Übermittlung Ihrer App an den Microsoft Store blockiert werden, da alle Übermittlungen an den Microsoft Store mit Windows10 S kompatibel sein müssen.

>[!IMPORTANT]
> Nachdem Sie das Windows-App-Paket erstellt haben, testen Sie Ihre App, um sicherzustellen, dass sie auf Systemen funktioniert, auf denen Windows10 S ausgeführt wird. Alle an den Microsoft Store übermittelten Apps müssen mit Windows10 S-Apps kompatibel sein. Apps, die nicht kompatibel sind, werden nicht im Store akzeptiert. Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](desktop-to-uwp-test-windows-s.md).

## <a name="next-steps"></a>Nächste Schritte

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).

**Erstellen eines Windows-App-Pakets für Ihre Desktop-App**

Weitere Informationen erhalten Sie unter [Erstellen eines Windows-App-Pakets](desktop-to-uwp-root.md#convert).
