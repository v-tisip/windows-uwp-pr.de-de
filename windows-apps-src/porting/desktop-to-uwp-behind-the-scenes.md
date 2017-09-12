---
author: normesta
Description: "Dieser Artikel beschäftigt sich eingehender damit, wie die Desktop-Brücke funktioniert."
title: "Hintergrundinformationen zur Desktop-Brücke"
ms.author: normesta
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: a399fae9-122c-46c4-a1dc-a1a241e5547a
ms.openlocfilehash: 050499baaf383fc135d833ae1e4733c95f2b5fa1
ms.sourcegitcommit: 7540962003b38811e6336451bb03d46538b35671
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2017
---
# <a name="behind-the-scenes-of-the-desktop-bridge"></a>Hintergrundinformationen zur Desktop-Brücke

Dieser Artikel beschäftigt sich eingehender damit, wie die Desktop-Brücke funktioniert.

Ein wichtiges Ziel der Desktop-Brücke besteht darin, den Anwendungszustand vom Systemzustand bestmöglich zu trennen und dabei die Kompatibilität mit anderen Apps aufrechtzuerhalten. Die Brücke erreicht dies, indem sie die Anwendung in einem Paket für die universelle Windows-Plattform (UWP) platziert und anschließend einige zur Laufzeit am Dateisystem und an der Registrierung vorgenommene Änderungen ermittelt und umleitet.

Pakete, die Sie für die Desktop-App erstellen, sind vertrauenswürdige Anwendungen nur für den Desktop, die nicht virtualisiert sind und sich nicht in der Sandbox befinden. Dies ermöglicht es ihnen, auf die gleiche Weise mit anderen Apps zu interagieren wie klassische Desktop-Anwendungen.

## <a name="installation"></a>Installation

App-Pakete werden mit der ausführbaren Datei *app_name.exe* unter *C:\Programme\WindowsApps\package_name* installiert. Jeder Paketordner enthält ein Manifest (AppxManifest.xml), das einen speziellen XML-Namespace für verpackte Apps enthält. In der Manifestdatei ist ein ```<EntryPoint>```-Element enthalten, das auf die vertrauenswürdige App verweist. Wenn die App gestartet wird, wird sie nicht im App-Container, sondern stattdessen wie gewohnt als Benutzer ausgeführt.

Nach der Bereitstellung werden Paketdateien als schreibgeschützt markiert und vom Betriebssystem gesperrt. Windows verhindert, dass Apps gestartet werden, wenn diese Dateien manipuliert werden.

## <a name="file-system"></a>Dateisystem

Zur Aufnahme des App-Zustands versucht die Brücke, Änderungen zu erfassen, die die App an „AppData“ vornimmt. Alle Schreibvorgänge in den AppData-Ordner des Benutzers (z.B. *C:\Benutzer\Benutzername\AppData*), einschließlich Erstellungs-, Lösch- und Aktualisierungsvorgänge, werden direkt an einen privaten Speicherort pro Benutzer und App kopiert. Dadurch entsteht der Eindruck, dass die verpackte App die tatsächlichen AppData-Elemente bearbeitet, obwohl eigentlich eine private Kopie geändert wird. Durch eine derartige Umleitung von Schreibvorgängen kann das System alle von der App vorgenommenen Dateiänderungen nachverfolgen. Dadurch kann das System diese Dateien bereinigen, wenn die App deinstalliert wird, und somit die Systemüberlastung verringern und bessere App-Deinstallationsmöglichkeiten für den Benutzer bereitstellen.

Zusätzlich zur Umleitung von „AppData“ führt die Brücke bekannte Windows-Ordner („System32“, „Programme (x86)“ usw.) dynamisch mit den entsprechenden Verzeichnissen im App-Paket zusammen. Jedes verpackte Paket enthält im Stammverzeichnis einen Ordner mit dem Namen „VFS“. Alle Lesevorgänge für Verzeichnisse oder Dateien im VFS-Verzeichnis werden zur Laufzeit mit den jeweiligen nativen Entsprechungen zusammengeführt. Beispiel: Eine App kann *C:\Programme\WindowsApps\Paketname\VFS\SystemX86\vc10.dll* als Teil des App-Pakets enthalten, die Datei wird aber scheinbar unter *C:\Windows\System32\vc10.dll* installiert.  Dies gewährleistet die Kompatibilität mit Desktopanwendungen, die davon ausgehen, dass sich Dateien an Speicherorten ohne Pakete befinden.

Schreibvorgänge in Dateien/Ordner im verpackten App-Paket sind nicht zulässig. Schreibvorgänge in Dateien und Ordner, die nicht Teil des Pakets sind, werden von der Brücke ignoriert und sind nur zulässig, wenn der Benutzer über entsprechende Berechtigungen verfügt.

### <a name="common-operations"></a>Allgemeine Vorgänge

Diese kurze Referenztabelle enthält allgemeine Dateisystemvorgänge und Informationen zur Verarbeitung durch die Brücke.

Vorgang | Ergebnis | Beispiel
:--- | :--- | :---
Lesen oder Enumerieren einer bekannten Windows-Datei oder eines bekannten Windows-Ordners | Eine dynamische Zusammenführung von *C:\Programme\Paketname\VFS\bekannter Ordner* mit der lokalen Systementsprechung | Der Lesevorgang für *C:\Windows\System32* gibt den Inhalt von *C:\Windows\System32* und den Inhalt von *C:\Programme\WindowsApps\Paketname\VFS\SystemX86* zurück.
Schreiben unter „AppData“ | Kopie bei Schreibvorgang an einem Speicherort pro Benutzer und App | Für „AppData“ ist dies in der Regel *C:\Benutzer\Benutzername\AppData*.  
Schreibvorgänge im Paket | Nicht zulässig Das Paket ist schreibgeschützt. | Schreibvorgänge unter *C:\Programme\WindowsApps\Paketname* sind nicht zulässig.
Schreibvorgänge außerhalb des Pakets | Von der Brücke ignoriert. Zulässig, wenn der Benutzer über entsprechende Berechtigungen verfügt. | Ein Schreibvorgang in *C:\Windows\System32\foo.dll* ist zulässig, wenn das Paket nicht *C:\Programme\WindowsApps\Paketname\VFS\SystemX86\foo.dll* enthält und der Benutzer über entsprechende Berechtigungen verfügt.

### <a name="packaged-vfs-locations"></a>Gepackte VFS-Speicherorte

Der folgenden Tabelle können Sie entnehmen, wo Dateien, die zu Ihrem Paket gehören, für die App im System überlagert sind. Die App geht davon aus, dass sich diese Dateien an den aufgeführten Systemspeicherorten befinden, während sie sich tatsächlich an den umgeleiteten Speicherorten unter *C:\Programme\WindowsApps\Paketname\VFS* befinden. Die FOLDERID-Speicherorte stammen von der [**KNOWNFOLDERID**](https://msdn.microsoft.com/library/windows/desktop/dd378457.aspx)-Konstante.

Systemspeicherort | Umgeleiteter Speicherort (unter [Paketstammverzeichnis]\VFS\) | Gültig für Architekturen
 :--- | :--- | :---
FOLDERID_SystemX86 | SystemX86 | x86, amd64
FOLDERID_System | SystemX64 | amd64
FOLDERID_ProgramFilesX86 | ProgramFilesX86 | x86, amd6
FOLDERID_ProgramFilesX64 | ProgramFilesX64 | amd64
FOLDERID_ProgramFilesCommonX86 | ProgramFilesCommonX86 | x86, amd64
FOLDERID_ProgramFilesCommonX64 | ProgramFilesCommonX64 | amd64
FOLDERID_Windows | Windows | x86, amd64
FOLDERID_ProgramData | Gemeinsamer AppData-Ordner | x86, amd64
FOLDERID_System\catroot | AppVSystem32Catroot | x86, amd64
FOLDERID_System\catroot2 | AppVSystem32Catroot2 | x86, amd64
FOLDERID_System\drivers\etc | AppVSystem32DriversEtc | x86, amd64
FOLDERID_System\driverstore | AppVSystem32Driverstore | x86, amd64
FOLDERID_System\logfiles | AppVSystem32Logfiles | x86, amd64
FOLDERID_System\spool | AppVSystem32Spool | x86, amd64

## <a name="registry"></a>Registrierung

Die Brücke behandelt die Registrierung ähnlich wie das Dateisystem. App-Pakete enthalten eine Datei namens „registry.dat“, die als logische Entsprechung für *HKLM\Software* in der tatsächlichen Registrierung dient. Zur Laufzeit führt diese virtuelle Registrierung den Inhalt dieser Struktur in der nativen Systemstruktur zusammen, um beide Strukturen in einer Ansicht darzustellen. Wenn „registry.dat“ beispielsweise einen einzelnen Schlüssel namens „Foo“ enthält, enthält ein Lesevorgang für *HKLM\Software* zur Laufzeit scheinbar ebenfalls „Foo“ (zusätzlich zu allen nativen Systemschlüsseln).

Nur Schlüssel unter *HKLM\Software* sind Teil des Pakets. Schlüssel unter *HKCU* oder in anderen Registrierungsbereichen sind nicht Teil des Pakets. Schreibvorgänge für Schlüssel oder Werte im Paket sind nicht zulässig. Schreibvorgänge für Schlüssel oder Werte, die nicht Teil des Pakets sind, werden von der Brücke ignoriert und sind nur zulässig, wenn der Benutzer über entsprechende Berechtigungen verfügt.

Alle Schreibvorgänge unter „HKCU“ entsprechen Kopie bei Schreibvorgang an einem privaten Speicherort pro Benutzer und App. Dies bietet die gleichen Vorteile wie die Behandlung des Dateisystems durch die Brücke in Bezug auf die Bereinigung bei der Deinstallation. In der Regel können Deinstallationsprogramme *HKEY_CURRENT_USER* nicht bereinigen, da die Bereitstellung von Registrierungsdaten für abgemeldete Benutzer aufgehoben wird und die Daten daher nicht verfügbar sind.

Alle Schreibvorgänge werden während der Paketaktualisierung beibehalten und nur gelöscht, wenn die App vollständig entfernt wird.

### <a name="common-operations"></a>Allgemeine Vorgänge

Diese kurze Referenztabelle enthält allgemeine Registrierungsvorgänge und Informationen zur Verarbeitung durch die Brücke.

Vorgang | Ergebnis | Beispiel
:--- | :--- | :---
Lesen oder Enumerieren von *HKLM\Software* | Eine dynamische Zusammenführung der Paketstruktur mit der lokalen Systementsprechung | Wenn „registry.dat“ einen einzelnen Schlüssel namens „Foo“ enthält, zeigt ein Lesevorgang von *HKLM\Software* zur Laufzeit die Inhalte von *HKLM\Software* und *HKLM\Software\Foo* an.
Schreibvorgänge unter „HKCU“ | Kopie bei Schreibvorgang an einem privaten Speicherort pro Benutzer und App | Identisch mit „AppData“ für Dateien
Schreibvorgänge im Paket | Nicht zulässig Das Paket ist schreibgeschützt. | Schreibvorgänge unter *HKLM\Software* sind nicht zulässig, wenn ein entsprechender Schlüssel/Wert in der Paketstruktur vorhanden ist.
Schreibvorgänge außerhalb des Pakets | Von der Brücke ignoriert. Zulässig, wenn der Benutzer über entsprechende Berechtigungen verfügt. | Schreibvorgänge unter *HKLM\Software* sind zulässig, sofern kein entsprechender Schlüssel/Wert in der Paketstruktur vorhanden ist und der Benutzer über entsprechende Zugriffsberechtigungen verfügt.

## <a name="uninstallation"></a>Deinstallation

Wenn ein Paket vom Benutzer deinstalliert wird, werden alle Dateien und Ordner unter *C:\Programme\WindowsApps\Paketname* sowie alle umgeleiteten Schreibvorgänge für „AppData“ oder die Registrierung entfernt, die von der Brücke erfasst wurden.

## <a name="next-steps"></a>Nächste Schritte

**Antworten auf bestimmte Fragen finden**

Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).

**Geben Sie Feedback zu diesem Artikel**

Verwenden Sie den Kommentarabschnitt weiter unten.
