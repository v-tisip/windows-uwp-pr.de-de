---
author: GrantMeStrength
ms.assetid: 54973C62-9669-4988-934E-9273FB0425FD
title: "Aktivieren Ihres Geräts für die Entwicklung"
description: "Konfigurieren Sie Ihr Windows10-Gerät für die Entwicklung und das Debugging."
keywords: "Erste Schritte Entwicklerlizenz Visual Studio, Entwicklerlizenz Gerät aktivieren"
ms.author: jken
ms.date: 03/12/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: 8a7b01205acf12d4a0ab6d3d7024311b3944f103
ms.sourcegitcommit: 0fa9ae00117e8e6b04ed38956e605bb74c1261c6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2017
---
# <a name="enable-your-device-for-development"></a>Aktivieren Ihres Geräts für die Entwicklung

## <a name="activate-developer-mode-sideload-apps-and-access-other-developer-features"></a>Aktivieren Sie den Entwicklermodus, laden Sie Apps quer und greifen Sie auf andere Entwicklerfeatures zu

![Aktivieren Sie Ihre Geräte für die Entwicklung](images/developer-poster.png)

Wenn Sie Ihren Computer für normale tägliche Aktivitäten wie Spiele, Surfen im Web, E-Mail oder Office-Apps verwenden, müssen und sollten Sie den Entwicklermodus *nicht* aktivieren. Die restlichen Informationen auf dieser Seite sind nicht von Bedeutung und Sie können beruhigt Ihre Arbeit fortsetzen. Vielen Dank für Ihren Besuch!

Wenn Sie allerdings Software schreiben und dazu Visual Studio zum ersten Mal auf einem Computer verwenden, *müssen* Sie den Entwicklermodus auf dem Entwicklungs-PC und auf allen Geräten aktivieren, die Sie zum Testen des Codes verwenden. Wenn Sie ein UWP-Projekt öffnen, während der Entwicklermodus nicht aktiviert ist, wird entweder die Seite mit den Einstellungen **Für Entwickler** oder dieses Dialogfeld in Visual Studio angezeigt:

![Dialogfeld zum Aktivieren des Entwicklermodus in Visual Studio](images/latestenabledialog.png)

Wenn dieses Dialogfeld angezeigt wird, klicken Sie auf **Einstellungen für Entwickler**, um die Einstellungsseite **Für Entwickler** zu öffnen.

> [!NOTE]
> Sie können jederzeit zur Seite **Für Entwickler** wechseln, um den Entwicklermodus zu aktivieren oder zu deaktivieren: Geben Sie einfach in der Taskleiste im Cortana-Suchfeld „für Entwickler“ ein.

## <a name="accessing-settings-for-developers"></a>Zugriff auf Entwicklereinstellungen

So aktivieren Sie den Entwicklermodus und greifen auf andere Einstellungen zu:

1.  Wählen Sie im Dialogfeld **Für Entwickler** die Zugriffsebene aus, die Sie benötigen.
2.  Lesen Sie den Haftungsausschluss für die ausgewählte Einstellung, und klicken Sie dann auf **Ja**, um die Änderung zu übernehmen.

> [!NOTE]
> Wenn Ihr Gerät einem Unternehmen gehört, sind einige Optionen möglicherweise von Ihrer Organisation deaktiviert.

Hier sehen Sie die Einstellungsseite auf Desktopgeräten:

![Navigieren Sie zu „Einstellungen > Update und Sicherheit“, und wählen Sie „Für Entwickler“ aus, um Ihre Optionen anzuzeigen.](images/devmode-pc-options.png)

Hier sehen Sie die Einstellungsseite auf Mobilgeräten:

![Navigieren Sie auf Ihrem Smartphone unter „Einstellungen“ zu „Update und Sicherheit“.](images/devmode-mob.png)

## <a name="which-setting-should-i-choose-sideload-apps-or-developer-mode"></a>Welche Einstellung soll ich auswählen: Querladen von Apps oder Entwicklermodus?

 Sie können ein Gerät für die Entwicklung oder nur für das Querladen aktivieren.

-   *Windows Store-Apps* ist die Standardeinstellung. Wenn Sie keine Apps entwickeln oder spezielle interne Apps verwenden, die von Ihrem Unternehmen ausgestellt sind, sollten Sie diese Einstellung aktiviert lassen.
-   *Querladen* dient zum Installieren und Ausführen oder Testen einer App, die nicht vom Windows Store zertifiziert wurde. Hierzu zählen beispielsweise interne Unternehmens-Apps.
-   Im *Entwicklermodus* können Sie Apps querladen und Apps aus Visual Studio im Debugmodus ausführen. 

Standardmäßig können Sie nur UWP-Apps (Universelle Windows-Plattform) aus dem Windows Store installieren. Wenn Sie diese Einstellungen ändern, um die Entwicklerfeatures zu verwenden, kann hierdurch die Sicherheitsstufe Ihres Geräts geändert werden. Sie sollten keine Apps aus nicht überprüften Quellen installieren.

### <a name="sideload-apps"></a>Querladen von Apps

Die Einstellung für das Querladen von Apps wird normalerweise von Unternehmen oder Bildungseinrichtungen verwendet, die benutzerdefinierte Apps auf verwalteten Geräten installieren müssen, ohne den Windows Store zu nutzen. In diesem Fall wird im Unternehmen häufig eine Richtlinie erzwungen, mit der die Einstellung *Windows Store-Apps* deaktiviert wird, wie oben in der Abbildung der Einstellungsseite dargestellt. Die Organisation stellt außerdem das erforderliche Zertifikat und den Installationsspeicherort zum Querladen von Apps bereit. Weitere Informationen finden Sie in den TechNet-Artikeln [Querladen von Branchen-Apps in Windows 10](https://technet.microsoft.com/library/mt269549.aspx) und [Erste Schritte mit der Bereitstellung von Apps in Microsoft Intune](https://technet.microsoft.com/library/dn646955.aspx).

Spezifische Informationen für Gerätefamilien

-   Desktopgeräte: Sie können ein App-Paket (APPX-Datei) und jedes Zertifikat, das zur Ausführung der App benötigt wird, mit dem Windows PowerShell-Skript installieren, das mit dem Paket erstellt wird („Add-AppDevPackage.ps1“). Weitere Informationen finden Sie unter [Verpacken von UWP-Apps](../packaging/packaging-uwp-apps.md).

-   Mobilgeräte: Wenn das erforderliche Zertifikat bereits installiert ist, tippen Sie auf die Datei, um beliebige APPX-Dateien zu installieren, die Sie über eine E-Mail oder eine SD-Karte erhalten haben.

Das **Querladen von Apps** ist eine sicherere Option als der Entwicklermodus, da Sie Apps ohne vertrauenswürdiges Zertifikat nicht auf dem Gerät installieren können.

> [!NOTE]
> Achten Sie beim Querladen von Apps darauf, dass diese von einer vertrauenswürdigen Quelle stammen. Wenn Sie eine quergeladene, nicht vom Windows Store zertifizierte App installieren, bestätigen Sie, dass Sie über alle erforderlichen Rechte zum Querladen dieser App verfügen und die alleinige Verantwortung für jegliche Schäden tragen, die durch das Installieren und Ausführen dieser App entstehen können. Weitere Informationen finden Sie in diesen [Datenschutzbestimmungen](http://go.microsoft.com/fwlink/?LinkId=521839) im Abschnitt zu Windows &gt; „Windows Store“.

### <a name="developer-mode"></a>Entwicklermodus

Der Entwicklermodus ersetzt die Windows 8.1-Anforderungen durch eine Entwicklerlizenz.  Neben dem Querladen bietet der Entwicklermodus Debug- und zusätzliche Bereitstellungsoptionen. Hierzu gehört das Starten eines SSH-Diensts, der Bereitstellungen auf diesem Gerät ermöglicht. Um den Dienst zu beenden, müssen Sie den Entwicklermodus deaktivieren.

Spezifische Informationen für Gerätefamilien

-   Desktopgeräte:

    Aktivieren Sie den Entwicklermodus, um Apps in Visual Studio zu entwickeln und zu debuggen. Wie bereits beschrieben, wird in Visual Studio eine Meldung angezeigt, wenn der Entwicklermodus nicht aktiviert ist.

    Auf PCs mit Version vor dem Fall Creators Update ermöglicht dies Aktivieren das Windows-Subsystem für Linux. Weitere Informationen finden Sie unter [Über Bash on Ubuntu unter Windows](https://msdn.microsoft.com/commandline/wsl/about).  Ab dem Fall Creators Update ist der Entwicklermodus für WSL nicht mehr erforderlich.  

-   Mobilgeräte:

    Aktivieren Sie den Entwicklermodus, um Apps aus Visual Studio auf dem Gerät bereitzustellen und zu debuggen.

    Sie können auf die Datei tippen, um beliebige APPX-Dateien zu installieren, die Sie per E-Mail oder auf einer SD-Karte erhalten haben. Installieren Sie keine Apps aus nicht überprüften Quellen.

## <a name="additional-developer-mode-features"></a>Weitere Features im Entwicklermodus

Für jede Gerätefamilie können zusätzliche Entwicklerfeatures verfügbar sein. Diese Features sind nur verfügbar, wenn der Entwicklermodus auf dem Gerät aktiviert ist, und können sich abhängig von der verwendeten Betriebssystemversion unterscheiden.

Wenn Sie den Entwicklermodus aktivieren, wird ein Paket mit Optionen installiert, das Folgendes enthält:
- Windows Device Portal. Nur wenn die Option **Geräteportal aktivieren** aktiviert ist, ist das Geräteportal aktiviert und Firewallregeln werden für es konfiguriert.
- Installiert, aktiviert und konfiguriert die Firewallregeln für SSH-Dienste, die eine Remote-Installation von Apps ermöglichen.


Diese Abbildung zeigt Entwicklerfeatures für Mobilgeräte mit Windows 10:

![Entwicklermodusoptionen für Mobilgeräte](images/devmode-mob-options.png) 

### <a name="span-iddevice-discovery-and-pairingspandevice-portal"></a><span id="device-discovery-and-pairing"></span>Geräteportal

Weitere Informationen zum Device Portal finden Sie in der [Übersicht über das Windows Device Portal](../debug-test-perf/device-portal.md).

Gerätespezifische Anweisungen zum Einrichten finden Sie in folgenden Artikeln:
- [Geräteportal für Desktop](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop)
- [Geräteportal für HoloLens](https://developer.microsoft.com/windows/holographic/using_the_windows_device_portal)
- [Device Portal für IoT](https://developer.microsoft.com/windows/iot/docs/DevicePortal)
- [Device Portal für Mobilgeräte](../debug-test-perf/device-portal-mobile.md)
- [Geräteportal für Xbox](../debug-test-perf/device-portal-xbox.md)

Wenn Sie Probleme beim Aktivieren des Entwicklermodus oder des Geräteportals haben, finden Sie im Forum [Bekannte Probleme](https://social.msdn.microsoft.com/Forums/en-US/home?forum=Win10SDKToolsIssues&sort=relevancedesc&brandIgnore=True&searchTerm=%22device+portal%22) Problemumgehungen für diese Probleme. Suchen Sie andernfalls unter [Fehler beim Installieren des Entwicklermoduspakets](#failure-to-install-developer-mode-package) nach zusätzlichen Detail und welche WSUS KBs zugelassen werden, um das Paket im Entwicklermodus zu erlauben oder zu entsperren. 

###<a name="ssh"></a>SSH

Wenn Sie den Entwicklermodus auf Ihrem Gerät aktivieren, sind SSH-Dienste aktiviert.  Diese werden verwendet, wenn Ihr Gerät ein Bereitstellungsziel für UWP-Anwendungen ist.   Die Namen der Dienste sind „SSH Server Broker“ und „SSH Server Proxy“.

> [!NOTE]
> Dies ist nicht die OpenSSH-Implementierung von Microsoft, die Sie auf [GitHub](https://github.com/PowerShell/Win32-OpenSSH) finden.

Wenn Sie die SSH-Dienste nutzen möchten, können Sie die Gerätesuche aktivieren, um eine Pin-Kopplung zu ermöglichen. Wenn ein anderer SSH-Dienst ausgeführt werden soll, können Sie diesen auf einem anderen Anschluss einrichten oder die SSH-Dienste im Entwicklermodus deaktivieren. Um die SSH-Dienste zu deaktivieren, deaktivieren Sie einfach den Entwicklermodus.  

### <a name="device-discovery"></a>Gerätesuche

Wenn Sie die Gerätesuche aktivieren, ist Ihr Gerät über mDNS für andere Geräte im Netzwerk sichtbar.  Dieses Feature ermöglicht auch das Abrufen der SSH-PIN zur Kopplung mit diesem Gerät.  

![PIN-Kopplung](images/devmode-pc-pinpair.PNG)

Die Gerätesuche sollte nur aktiviert werden, wenn das Gerät ein Bereitstellungsziel sein soll. Wenn beispielsweise eine App über das Geräteportal zum Testen auf einem Smartphone bereitgestellt wird, müssen Sie die Gerätesuche auf dem Smartphone, jedoch nicht auf Ihrem Entwicklungscomputer aktivieren.

### <a name="error-reporting-mobile-only"></a>Fehlerberichterstattung (nur Mobile)

Legen Sie diesen Wert fest, um anzugeben, wie viele Absturzabbilder auf dem Smartphone gespeichert werden.

Indem Sie Absturzabbilder auf Ihrem Smartphone speichern, haben Sie direkt nach einem Absturz sofort Zugriff auf wichtige Informationen. Abbilder werden nur für von Entwicklern signierte Apps erfasst. Sie finden die Abbilder im Speicher Ihres Smartphones im Ordner „Documents\\Debug“. Weitere Informationen zu Abbilddateien finden Sie im Artikel zum [Verwenden von Dumpdateien](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="optimizations-for-windows-explorer-remote-desktop-and-powershell-desktop-only"></a>Optimierungen für Windows-Explorer, Remotedesktop und PowerShell (nur Desktop)

 Auf der Desktopgerätefamilie finden Sie auf der Einstellungsseite **Für Entwickler** Verknüpfungen zu den Einstellungen, die Sie zum Optimieren Ihres PCs für Entwicklungsaufgaben verwenden können. Für jede Einstellung können Sie das Kontrollkästchen aktivieren und auf **Übernehmen** klicken, oder Sie können auf den Link **Einstellungen anzeigen** klicken, um die Einstellungsseite für diese Option zu öffnen. 



**Tipp**  
Es gibt verschiedene Tools, mit denen Sie eine App von einem Windows10-PC auf einem mobilen Gerät bereitstellen können. Beide Geräte müssen über eine kabelgebundene oder drahtlose Verbindung mit dem gleichen Subnetz des Netzwerks verbunden sein oder über USB verbunden werden. Mit beiden aufgeführten Methoden wird nur das App-Paket (APPX) installiert, nicht die Zertifikate.

-   Verwenden Sie das Tool für die Windows10-Anwendungsbereitstellung (WinAppDeployCmd). Weitere Informationen zum [Tool WinAppDeployCmd](http://msdn.microsoft.com/library/windows/apps/mt203806.aspx).
-   Ab Windows10, Version 1511, ist im [Device Portal](../debug-test-perf/device-portal-desktop.md) die Bereitstellung aus Ihrem Browser auf einem mobilen Gerät unter Windows10, Version 1511 oder höher, möglich. Im Geräteportal können Sie auf der Seite **[Apps](../debug-test-perf/device-portal.md#apps)** ein App-Paket (APPX) hochladen und auf dem Gerät installieren.

## <a name="failure-to-install-developer-mode-package"></a>Fehler beim Installieren des Entwicklermoduspakets
In manchen Fällen wird der Entwicklermodus aufgrund von Problemen mit dem Netzwerk oder dem Administrator nicht ordnungsgemäß installiert. Das Entwicklermoduspaket ist für die **dezentrale** Bereitstellungen auf diesem PC erforderlich – verwenden Sie Device Portal über einen Browser oder Device Discovery SSH – aber nicht für die lokale Entwicklung.  Selbst wenn diese Probleme auftreten, können Sie Ihre App weiterhin mithilfe von Visual Studio oder von diesem Gerät auf ein anderes Gerät bereitstellen. 

Im Forum zu den [bekannten Problemen](https://social.msdn.microsoft.com/Forums/en-US/home?forum=Win10SDKToolsIssues&sort=relevancedesc&brandIgnore=True&searchTerm=%22device+portal%22) finden Sie entsprechende Problemumgehungen und vieles mehr. 

### <a name="failed-to-locate-the-package"></a>Das Paket konnte nicht gefunden werden

"Developer Mode package couldn’t be located in Windows Update. Error Code 0x80004005 Learn more"   

Dieser Fehler kann aufgrund eines Netzwerkverbindungsproblems, aufgrund von Enterprise-Einstellungen oder weil das Paket nicht vorhanden ist, auftreten. 

So beheben Sie dieses Problem:

1. Stellen Sie sicher, dass Ihr Computer mit dem Internet verbunden ist. 
2. Wenn Sie einen in eine Domäne eingebundenen Computer verwenden, sprechen Sie mit dem Netzwerkadministrator. Das Entwicklermoduspaket ist genau wie alle anderen Features standardmäßig in WSUS blockiert. 2.1. Um das Entwicklermoduspaket in der aktuellen und vorherigen Versionen zu entsperren, sollte die folgenden KBs in WSUS zugelassen werden: 4016509, 3180030, 3197985  
3. Suchen nach Windows-Updates in den Einstellungen > Updates und Sicherheit > Windows-Updates.
4. Stellen Sie sicher, dass das Windows-Entwicklermoduspaket in den Einstellungen > System > Apps und Features > Optionale Features verwalten > Feature hinzufügen vorhanden ist. Wenn es nicht vorhanden ist, kann Windows das richtige Paket für Ihren Computer nicht finden. 

Nachdem Sie einen der oben genannten Schritte durchgeführt haben, deaktivieren Sie den Entwicklermodus, und aktivieren Sie ihn dann erneut, um die Korrektur zu überprüfen. 


### <a name="failed-to-install-the-package"></a>Fehler beim Installieren des Pakets

"Developer Mode package failed to install. Error Code 0x80004005 Learn more"

Dieser Fehler kann aufgrund von Inkompatibilitäten zwischen dem Build von Windows und dem Entwicklermoduspaket auftreten. 

So beheben Sie dieses Problem:

1. Suchen nach Windows-Updates in den Einstellungen > Updates und Sicherheit > Windows-Updates.
2. Starten Sie Ihren Computer neu, um sicherzustellen, dass alle Updates angewendet wurden.


## <a name="use-group-policies-or-registry-keys-to-enable-a-device"></a>Verwenden von Gruppenrichtlinien oder Registrierungsschlüsseln zum Aktivieren von Geräten

Entwickler sollten meist die Einstellungs-Apps verwenden, um Geräte für das Debuggen zu aktivieren. In bestimmten Szenarien wie z.B. bei automatisierten Tests stehen weitere Möglichkeiten zum Aktivieren Ihres Windows10-Desktopgeräts für die Entwicklung zur Verfügung.

Sie können mithilfe von „gpedit.msc“ die Gruppenrichtlinien für die Geräteaktivierung festlegen (es sei denn, Sie verwenden Windows10 Home). In Windows10 Home müssen die Registrierungsschlüssel für die Geräteaktivierung direkt mithilfe von regedit oder von PowerShell-Befehlen festgelegt werden.

**Aktivieren des Geräts mithilfe von „gpedit“**

1.  Führen Sie **Gpedit.msc** aus.
2.  Navigieren Sie zu „Richtlinie für "Lokaler Computer" &gt; Computerkonfiguration &gt; Administrative Vorlagen &gt; Windows-Komponenten &gt; App-Paketbereitstellung.
3.  Bearbeiten Sie zum Aktivieren des Querladens die folgenden Richtlinien:

    -   **Zulassen, dass alle vertrauenswürdigen Apps installiert werden**

    - ODER

    Bearbeiten Sie zum Aktivieren des Entwicklermodus die Richtlinien, um beide zu aktivieren:

    -   **Zulassen, dass alle vertrauenswürdigen Apps installiert werden**
    -   **Hiermit wird die Entwicklung von Windows Store-Apps und Ihre Installation aus einer integrierten Entwicklungsumgebung (IDE) zugelassen.**

4.  Starten Sie Ihren Computer neu.

**Aktivieren des Geräts mithilfe von „regedit“**

1.  Führen Sie **regedit** aus.
2.  Legen Sie diesen DWORD-Wert auf 1 fest, um das Querladen zu aktivieren.

    -   **HKLM\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\AppModelUnlock\\AllowAllTrustedApps**

    - ODER

    Um den Entwicklermodus zu aktivieren, legen Sie diese DWORD-Werte auf 1 fest:

    -   **HKLM\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\AppModelUnlock\\AllowDevelopmentWithoutDevLicense**

**Aktivieren des Geräts mithilfe von PowerShell**

1.  Führen Sie PowerShell mit Administratorrechten aus.
2.  Führen Sie zum Aktivieren des Querladens diesen Befehl aus:

    -   **PS C:\\WINDOWS\\system32&gt; reg add "HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\AppModelUnlock" /t REG\_DWORD /f /v "AllowAllTrustedApps" /d "1"**

    - ODER

    Führen Sie zum Aktivieren des Entwicklermodus diesen Befehl aus:

    -   **PS C:\\WINDOWS\\system32&gt; reg add "HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\AppModelUnlock" /t REG\_DWORD /f /v "AllowDevelopmentWithoutDevLicense" /d "1"**

## <a name="upgrade-your-device-from-windows-81-to-windows-10"></a>Aktualisieren Ihres Geräts von Windows 8.1 auf Windows 10

Wenn Sie Apps auf Ihrem Windows8.1-Gerät erstellen oder querladen, müssen Sie eine Entwicklerlizenz installieren. Beim Upgrade Ihres Geräts von Windows8.1 auf Windows10 bleiben diese Informationen erhalten. Führen Sie den folgenden Befehl aus, um diese Informationen von Ihrem aktualisierten Windows10-Gerät zu entfernen. Dieser Schritt ist nicht erforderlich, wenn Sie ein Upgrade von Windows8.1 direkt auf Windows10, Version1511 oder höher, ausführen.

**So heben Sie die Registrierung einer Entwicklerlizenz auf**

1.  Führen Sie PowerShell mit Administratorrechten aus.
2.  Führen Sie folgenden Befehl aus: **unregister-windowsdeveloperlicense**.

Danach müssen Sie Ihr Gerät wie in diesem Thema beschrieben für die Entwicklung aktivieren, damit Sie weiterhin auf diesem Gerät entwickeln können. Andernfalls erhalten Sie möglicherweise eine Fehlermeldung, wenn Sie Ihre App debuggen oder versuchen, ein Paket dafür zu erstellen. Hier ist ein Beispiel für diesen Fehler:

Fehler : DEP0700 : Registrierung der App fehlgeschlagen.

## <a name="see-also"></a>Weitere Informationen

* [Ihre erste App](your-first-app.md)
* [Veröffentlichen Ihrer Windows Store-Apps](https://developer.microsoft.com/store/publish-apps).
* [Anleitungen zur Entwicklung von UWP-Apps](https://developer.microsoft.com/windows/apps/develop)
* [Codebeispiele für UWP-Entwickler](https://developer.microsoft.com/windows/samples)
* [Was ist eine universelle Windows-App?](whats-a-uwp.md)
* [Für Windows-Konto anmelden](sign-up.md)
