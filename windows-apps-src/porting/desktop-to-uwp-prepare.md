---
author: awkoren
Description: "In diesem Artikel sind Punkte aufgeführt, die Sie vor dem Konvertieren von Apps mit der Desktop-zu-UWP-Brücke wissen sollten. Sie müssen möglicherweise nicht viel tun, um Ihre App für die Konvertierung vorzubereiten."
Search.Product: eADQiWindows 10XVcnh
title: "Vorbereiten von Apps für die Desktop-zu-UWP-Brücke"
translationtype: Human Translation
ms.sourcegitcommit: d22d51d52c129534f8766ab76e043a12d140e8b7
ms.openlocfilehash: a93d5ad1c1f429182c8df7d29df85dee70064e2f

---

# <a name="prepare-an-app-for-conversion-with-the-desktop-bridge"></a>Vorbereiten einer App für die Konvertierung mit der Desktop-Brücke

In diesem Artikel sind Punkte aufgeführt, die Sie vor dem Konvertieren von Apps mit der Desktop-zu-UWP-Brücke wissen sollten. Sie müssen möglicherweise nicht viel tun, um Ihre App für die Konvertierung vorzubereiten. Trifft jedoch einer der folgenden Punkte auf Ihre Anwendung zu, müssen Sie sich vor der Konvertierung darum kümmern. Denken Sie daran, dass Lizenzierung und automatische Updates im Rahmen des Windows Store erfolgen, sodass Sie diese Features aus Ihrer Codebasis entfernen können.

+ __Ihre App verwendet eine frühere .NET-Version als 4.6.1__. Es wird nur .NET 4.6.1 unterstützt. Sie müssen Ihre App vor dem Konvertieren für .NET 4.6.1 neu zuweisen. 

+ __Ihre App wird immer mit erhöhten Sicherheitsberechtigungen ausgeführt__. Ihre App muss als interaktiver Benutzer ausgeführt werden können. Benutzer, die Ihre App über den Windows Store installieren, sind möglicherweise keine Systemadministratoren. Wenn für die Ausführung Ihrer App erhöhte Rechte erforderlich sind, wird die App für Standardbenutzer nicht korrekt ausgeführt.

+ __Ihre App erfordert einen Kernelmodustreiber oder einen Windows-Dienst__. Die Brücke eignet sich für eine App, ein Kernelmodustreiber oder ein Windows-Dienst, die unter einem Systemkonto ausgeführt werden müssen, werden jedoch nicht unterstützt. Verwenden Sie anstelle eines Windows-Diensts eine [Hintergrundaufgabe](https://msdn.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task).

+ __Ihre App-Module werden im Prozess für Prozesse geladen, die nicht im APPX-Paket enthalten sind__. Dies ist nicht zulässig. Prozessinterne Erweiterungen, beispielsweise [Shellerweiterungen](https://msdn.microsoft.com/library/windows/desktop/dd758089.aspx), werden nicht unterstützt. Wenn zwei Apps in einem Paket enthalten sind, können Sie jedoch die prozessübergreifende Kommunikation zwischen diesen verwenden.

+ __Ihre App ruft [SetDllDirectory](https://msdn.microsoft.com/library/windows/desktop/ms686203) oder [AddDllDirectory](https://msdn.microsoft.com/library/windows/desktop/hh310513)__ auf. Diese Funktionen werden derzeit für konvertierte Apps nicht unterstützt. Die Unterstützung ist in einer zukünftigen Version enthalten. Um dieses Problem zu umgehen, können Sie all jene DLLs in das Paketstammverzeichnis kopieren, die mit diesen Funktionen gefunden wurden. 

+ __Ihre App verwendet eine benutzerdefinierte Anwendungsbenutzermodell-ID (Application User Model ID, AUMID)__. Wenn der Prozess [SetCurrentProcessExplicitAppUserModelID](https://msdn.microsoft.com/library/windows/desktop/dd378422.aspx) zum Festlegen einer eigenen Anwendungsbenutzermodell-ID aufruft, kann er nur die von der App-Modellumgebung/vom AppX-Paket generierte Anwendungsbenutzermodell-ID verwenden. Sie können keine benutzerdefinierten Anwendungsbenutzermodell-IDs definieren.

+ __Ihre App ändert die HKLM-Registrierungsstruktur (HKEY_LOCAL_MACHINE)__. Bei jedem Versuch, einen HKLM-Schlüssel zu erstellen oder einen zum Ändern zu öffnen, wird der Zugriff verweigert. Denken Sie daran, dass Ihre App über eine eigene private virtualisierte Ansicht der Registrierung verfügt. Damit kann das Konzept einer benutzer- und computerweiten Registrierungsstruktur (Zweck von HKLM) nicht angewendet werden. Sie müssen stattdessen eine andere Möglichkeit finden, um das zu erreichen, wozu Sie HKLM verwendet haben, beispielsweise Schreiben in HKEY_CURRENT_USER (HKCU).

+ __Ihre App verwendet einen DDEEXEC-Registrierungsunterschlüssel zum Starten einer anderen App__. Verwenden Sie stattdessen einen der DelegateExecute-Verbhandler genau wie von den verschiedenen Activatable*-Erweiterungen in dem [App-Paketmanifest](https://msdn.microsoft.com/library/windows/apps/br211474.aspx) konfiguriert.

+ __Ihre App schreibt in den AppData-Ordner, um Daten für eine andere App freizugeben__. Nach der Konvertierung wird AppData an den lokalen App-Datenspeicher weitergeleitet, der ein privater Speicher für jede UWP-App ist. Verwenden Sie verschiedene Methoden für die prozessübergreifende Datenfreigabe. Weitere Informationen finden Sie unter [Speichern und Abrufen von Einstellungen und anderen App-Daten](https://msdn.microsoft.com/windows/uwp/app-settings/store-and-retrieve-app-data).

+ __Ihre App schreibt in das Installationsverzeichnis für die App__. Ihre App schreibt z. B. in eine Protokolldatei, die sich in demselben Verzeichnis wie die EXE-Datei befindet. Dies wird nicht unterstützt. Sie müssen daher einen anderen Speicherort wählen, z. B. den lokalen App-Datenspeicher.

+ __Ihre App-Installation erfordert eine Benutzerinteraktion__. Der App-Installer muss automatisch ausgeführt werden können und muss alle erforderlichen Komponenten installieren, die nicht standardmäßig auf einem sauberen Betriebssystemimage aktiviert sind.

+ __Ihre App verwendet das aktuelle Arbeitsverzeichnis__. Zur Laufzeit nutzt die konvertierte App nicht das gleiche Arbeitsverzeichnis, das Sie zuvor in Ihrer Desktop-LNK-Verknüpfung angegeben haben. Sie müssen das aktuelle Arbeitsverzeichnis zur Laufzeit ändern, wenn das richtige Verzeichnis notwendig ist, damit Ihre App ordnungsgemäß funktioniert.

+ __Ihre App benötigt UIAccess__. Wenn Ihre Anwendung `UIAccess=true` für das `requestedExecutionLevel`-Element im UAC-Manifest angibt, wird die Konvertierung in eine UWP-App derzeit nicht unterstützt. Weitere Informationen finden Sie unter [Sicherheit bei der Benutzeroberflächenautomatisierung – Übersicht](https://msdn.microsoft.com/library/ms742884.aspx).

+ __Ihre App macht COM-Objekte oder GAC-Assemblys zur Verwendung durch andere Prozesse verfügbar__. In der aktuellen Version kann Ihre App COM-Objekte oder GAC-Assemblys nicht zur Verwendung durch Prozesse verfügbar machen, die von ausführbaren Dateien stammen, die sich außerhalb Ihres AppX-Pakets befinden. Prozesse aus dem Paket können COM-Objekte und GAC-Assemblys wie gewohnt registrieren und verwenden, aber sie sind nicht extern sichtbar. Dies bedeutet, dass Interoperabilitätsszenarien wie OLE nicht funktionieren, wenn sie von externen Prozessen aufgerufen werden. 

+ __Ihre App verknüpft C-Laufzeitbibliotheken (CRT) auf eine nicht unterstützte Weise__. Die Microsoft C/C++-Laufzeitbibliothek enthält Routinen für die Programmierung für das Microsoft Windows-Betriebssystem. Diese Routinen automatisieren viele allgemeine Programmieraufgaben, die von den Programmiersprachen C# und C++ nicht bereitgestellt werden. Wenn Ihre App eine C/C++-Laufzeitbibliothek verwendet, müssen Sie sicherstellen, dass sie auf eine unterstützte Weise verknüpft ist. 
    
    Visual Studio 2015 unterstützt die dynamische Verknüpfung, damit Ihr Code gängige DLL-Dateien verwenden kann, und statische Verknüpfung, um die Bibliothek direkt in Ihren Code, mit der aktuellen Version der CRT, zu verknüpfen. Wir empfehlen, dass Ihre App möglichst die dynamische Verknüpfung mit VS 2015 verwendet. 

    Unterstützung in früheren Versionen von Visual Studio variiert. Weitere Informationen finden Sie in der folgenden Tabelle: 

    <table>
    <th>Version von Visual Studio</td><th>Dynamische Verknüpfung</th><th>Statische Verknüpfung</th></th>
    <tr><td>2005 (VC 8)</td><td>Nicht unterstützt</td><td>Unterstützt</td>
    <tr><td>2008 (VC 9)</td><td>Nicht unterstützt</td><td>Unterstützt</td>
    <tr><td>2010 (VC 10)</td><td>Unterstützt</td><td>Unterstützt</td>
    <tr><td>2012 (VC 11)</td><td>Unterstützt</td><td>Nicht unterstützt</td>
    <tr><td>2013 (VC 12)</td><td>Unterstützt</td><td>Nicht unterstützt</td>
    <tr><td>2015 (VC 14)</td><td>Unterstützt</td><td>Unterstützt</td>
    </table>
    
    Hinweis: In allen Fällen müssen Sie eine Verknüpfung zur neuesten öffentlich verfügbaren CRT herstellen.

+ __Ihre App installiert und lädt Assemblys aus dem Windows-Seite-an-Seite-Ordner__. Beispielsweise verwendet Ihre App C-Laufzeitbibliotheken VC8 oder VC9 und verknüpft diese dynamisch aus dem Windows-Seite-an-Seite-Ordner, was bedeutet, dass Ihr Code die gemeinsamen DLL-Dateien aus einem freigegebenen Ordner verwendet. Dies wird nicht unterstützt. Sie müssen diese statisch verknüpfen, indem sie eine Verknüpfung mit den verteilbaren Bibliotheksdateien direkt in den Code erstellen.

+ __Ihre App verwendet eine Abhängigkeit im Ordner System32/SysWOW64__. Damit diese DLL-Dateien funktionieren, müssen Sie sie im virtuellen Dateisystem Ihres AppX-Pakets einschließen. Dadurch wird sichergestellt, dass sich die App verhält, als ob die DLL-Dateien im Ordner **System32**/**SysWOW64** installiert wären. Erstellen Sie im Stammordner des Pakets einen Ordner mit dem Namen **VFS**. Erstellen Sie innerhalb dieses Ordners die Ordner **SystemX64** und **SystemX86**. Platzieren Sie die 32-Bit-Version Ihrer DLL-Datei im Ordner **SystemX86** und die 64-Bit-Version im Ordner **SystemX64**.

+ __Ihre App verwendet das Frameworkpaket Dev11 VCLibs__. Die VCLibs 11-Bibliotheken können direkt aus dem Windows Store installiert werden, wenn sie im AppX-Paket als Abhängigkeit definiert sind. Zu diesem Zweck führen Sie die folgende Änderung in Ihrem App-Paketmanifest aus: Fügen Sie unter dem Knoten `<Dependencies>` Folgendes hinzu:  
`<PackageDependency Name="Microsoft.VCLibs.110.00.UWPDesktop" MinVersion="11.0.24217.0" Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US" />`  
Während der Installation aus dem Windows Store wird die korrekte Version des VCLibs 11-Frameworks (x86 oder x64) vor der Installation der App installiert.  
Die Abhängigkeiten werden nicht installiert, wenn die App durch Querladen installiert wird. Um die Abhängigkeiten manuell auf dem Computer zu installieren, müssen Sie die [VC 11.0-Frameworkpakete für die Desktop-Brücke](https://www.microsoft.com/download/details.aspx?id=53340&WT.mc_id=DX_MVP4025064) herunterladen und installieren. Weitere Informationen zu diesen Szenarien finden Sie unter [Verwenden von Visual C++-Laufzeitbibliotheken im Projekt „Centennial“](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/).

+ __Ihre App erstellt Sprunglisteneinträge und ruft [ICustomDestinationList::SetAppID](https://msdn.microsoft.com/library/windows/desktop/dd378403(v=vs.85).aspx) oder [SetCurrentProcessExplicitAppUserModelID](https://msdn.microsoft.com/library/windows/desktop/dd378422(v=vs.85).aspx)__ auf. Legen Sie „AppID“ nicht programmgesteuert im Code fest. Andernfalls werden die Sprunglisteneinträge nicht angezeigt. Wenn Ihre App eine benutzerdefinierte ID benötigt, geben Sie sie mithilfe der Manifestdatei an. Anweisungen finden Sie unter [Manuelles Konvertieren Ihrer App zu UWP mithilfe der Desktop-Brücke](desktop-to-uwp-manual-conversion.md). Die App-ID für die Anwendung ist im Abschnitt *YOUR_PRAID_HERE* angegeben. 

+ __Ihre App fügt einen Sprunglistenshell-Link hinzu, der auf eine ausführbare Datei im Paket verweist__. Sie können ausführbare Dateien in Ihrem Paket nicht direkt aus einer Sprungliste starten (mit Ausnahme des absoluten Pfads einer eigenen EXE-Datei einer App). Registrieren Sie stattdessen einen App-Ausführungsalias (mit dem die konvertierte App über ein Schlüsselwort gestartet werden kann, als befände sie sich im PFAD), und legen Sie den Linkzielpfad stattdessen auf den Alias fest. Ausführliche Informationen zur Verwendung der appExecutionAlias-Erweiterung finden Sie unter [App-Erweiterungen für die Desktopbrücke](desktop-to-uwp-extensions.md). Hinweis: Wenn Ressourcen des Links in der Sprungliste der ursprünglichen EXE-Datei entsprechen müssen, müssen Sie Ressourcen wie etwa das Symbol mithilfe von [**SetIconLocation**](https://msdn.microsoft.com/library/windows/desktop/bb761047(v=vs.85).aspx) und den Anzeigenamen mit „PKEY_Title“ festlegen (wie bei anderen benutzerdefinierten Einträgen). 

+ __Ihre App fügt Sprunglisteneinträge hinzu, die auf Ressourcen im Paket Ihrer App nach absoluten Pfaden verweisen__. Der Installationspfad der App ändert sich möglicherweise, wenn Pakete aktualisiert werden. Dadurch ändert sich auch der Ort der Ressourcen (z. B. Symbole, Dokumente, ausführbare Dateien usw.). Falls Sprunglisteneinträge auf derartige Ressourcen nach absoluten Pfaden verweisen, muss die App ihre Sprungliste in regelmäßigen Abständen (z. B. beim App-Start) aktualisieren, um eine ordnungsgemäße Auflösung der Pfade sicherzustellen. Sie können stattdessen auch die UWP-[**Windows.UI.StartScreen.JumpList**](https://msdn.microsoft.com/library/windows/apps/windows.ui.startscreen.jumplist.aspx)-APIs verwenden. Diese APIs ermöglichen den Verweis auf Zeichenfolgen- und Bildressourcen mithilfe des relativen ms-resource-URI-Paketschemas (das zudem Sprache, DPI und hohen Kontrast berücksichtigt). 


<!--HONumber=Dec16_HO1-->


