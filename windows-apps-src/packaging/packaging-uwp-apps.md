---
author: laurenhughes
ms.assetid: 96361CAF-C347-4671-9721-8208CE118CA4
title: Verpacken von UWP-Apps
description: "Um Ihre UWP-App (Universelle Windows-Plattform) zu vertreiben und zu verkaufen, müssen Sie ein App-Paket erstellen."
ms.author: lahugh
ms.date: 08/09/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: c6aa08c8c2e62bfed388000944de5520cbe58501
ms.sourcegitcommit: 63c815f8c6665872987b5410cabf324f2b7e3c7c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2017
---
# <a name="package-a-uwp-app-with-visual-studio"></a>Verpacken einer UWP-App mit Visual Studio

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

Um Ihre UWP-App (Universelle Windows-Plattform) zu verkaufen oder an andere Benutzer zu verteilen, müssen Sie ein UWP-App-Paket erstellen. Wenn Sie Ihre App nicht über den Store verteilen möchten, können Sie das App-Paket direkt auf einem Gerät querladen. In diesem Artikel wird das Konfigurieren, Erstellen und Testen von UWP-App-Paketen mit Visual Studio beschrieben. Weitere Informationen über das Querladen von Unternehmens-Apps und Branchen-Apps finden Sie unter [Querladen von Branchen-Apps in Windows10](https://docs.microsoft.com/windows/application-management/sideload-apps-in-windows-10).

Sie können in Windows10 ein App-Paket (.appx), ein App-Bundle (.appxbundle) oder eine vollständige Datei (.appxupload) hochladen. Die appxupload-Datei ist ein Ordner, der sowohl das App-Paket oder Bundle sowie andere wichtige Debuginformationen enthält. Es wird dringend empfohlen, eine appxupload-Datei zu übermitteln. Nachdem das App-Paket an den Store gesendet wurde, steht Ihre App zur Installation auf allen Windows10-Geräten bereit. 

Hier sehen Sie eine Übersicht über die Schrittezum Vorbereiten und Erstellen eines App-Pakets.

1.  [Vor dem Verpacken der App](#before-packaging-your-app). Führen Sie die folgenden Schritte aus, um sicherzustellen, dass die App verpackt und an den Store übermittelt werden kann.
2.  [Konfigurieren eines App-Pakets](#configure-an-app-package). Verwenden Sie den Manifest-Designer, um das Paket zu konfigurieren. Fügen Sie beispielsweise Kachelbilder hinzu, und wählen Sie die von Ihrer App unterstützten Ausrichtungen aus.
3.  [Erstellen eines App-Pakets](#create-an-app-package). Verwenden Sie den Visual Studio App-Verpackungsassistenten, um ein App-Paket zu erstellen. Zertifizieren Sie dann Ihr Paket mit dem Zertifizierungskit für Windows-Apps.
4.  [Querladen des App-Pakets](#sideload-your-app-package). Nach dem Querladen Ihrer App auf ein Gerät können Sie testen, ob es ordnungsgemäß funktioniert.

Nachdem Sie die vorangehenden Schritte abgeschlossen haben, können Sie Ihre App im Store verteilen. Eine branchenspezifische App, die Sie nicht verkaufen, sondern nur internen Benutzern zur Verfügung stellen möchten, können Sie querladen, um sie auf einem beliebigen Windows 10-Gerät zu installieren.

## <a name="before-packaging-your-app"></a>Vor dem Verpacken der App

1.  **Testen der App.** Bevor Sie Ihre App für die Übermittlung an den Store verpacken, stellen Sie sicher, dass sie auf allen Gerätefamilien, die unterstützt werden sollen, erwartungsgemäß funktioniert. Diese Gerätefamilien umfassen Desktop-, Mobile-, Surface Hub-, Xbox-, IoT- und andere Geräte.
2.  **Optimieren der App.** Sie können die Profilerstellungs- und Debugtools von Visual Studio verwenden, um die Leistung Ihrer UWP-App zu optimieren. Zu diesen Tools gehören das Zeitachsentool für „Reaktionsfähigkeit der Benutzeroberfläche“, das Speichernutzungstool, das CPU-Auslastungstool und viele mehr. Weitere Informationen zu diesen Tools finden Sie unter [Ausführen von Diagnosetools ohne Debugging](https://msdn.microsoft.com/library/dn957936.aspx).
3.  **Überprüfen der .NET Native-Kompatibilität (für VB- und C#-Apps).** Mit der Universelle Windows-Plattform wurde ein neuer systemeigener Compiler eingeführt, der die Laufzeitleistung Ihrer App verbessert. Diese Änderung macht es dringend erforderlich, dass Sie Ihre App in dieser Kompilierungsumgebung testen. Standardmäßig aktiviert die **Release**-Buildkonfiguration die .NET Native-Toolkette. Daher ist es wichtig, die App und das erwartete Verhalten mit dieser **Release**-Konfiguration zu testen. Einige häufige Debugprobleme, die bei .NET Native auftreten können, werden [Native .NET Windows Universal Apps debuggen](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx) ausführlich erläutert.

## <a name="configure-an-app-package"></a>Konfigurieren eines App-Pakets

Die App-Manifestdatei (Package.appxmanifest.xml) ist eine XML-Datei, die über die Eigenschaften und Einstellungen verfügt, die für die Erstellung des App-Pakets erforderlich sind. Die Eigenschaften in der Manifestdatei beschreiben z. B. das Bild, das als App-Kachel verwendet wird, und die Ausrichtungen, die von der App beim Drehen des Geräts unterstützt werden.

Visual Studio verfügt über einen Manifest-Designer, mit dem Sie die Manifestdatei ohne Bearbeitung der XML-Rohdaten der Datei aktualisieren können.

**Konfigurieren eines Pakets mit dem Manifest-Designer**

1.  Erweitern Sie im **Projektmappen-Explorer** den Projektknoten Ihrer UWP-App.
2.  Doppelklicken Sie auf die Datei **Package.appxmanifest**. Wenn die Manifestdatei bereits in der XML-Codeansicht geöffnet ist, werden Sie von Visual Studio zum Schließen der Datei aufgefordert.
3.  Jetzt können Sie entscheiden, wie Sie Ihre App konfigurieren möchten. Jede Registerkarte enthält Informationen, die Sie für Ihre App konfigurieren können, sowie Links zu weiteren Informationen, wenn notwendig.<br/>
    ![Manifest-Designer in Visual Studio](images/packaging-screen1.jpg)

    Überprüfen Sie auf der Registerkarte **Visuelle Anlagen**, ob Sie über alle Bilder verfügen, die für eine UWP-App erforderlich sind.

    Auf der Registerkarte **Verpacken** können Sie Veröffentlichungsdaten eingeben. An dieser Stelle können Sie auswählen, welches Zertifikat zur Signierung der App verwendet werden soll. Alle UWP-Apps müssen anhand eines Zertifikats signiert werden. Wenn Sie ein App-Paket querladen möchten, müssen Sie dem Paket vertrauen. Das Zertifikat muss auf diesem Gerät installiert sein, damit das Paket vertrauenswürdig ist. Weitere Informationen zum Querladen finden Sie unter [Aktivieren Ihres Geräts für die Entwicklung](https://msdn.microsoft.com/library/windows/apps/Dn706236).

4.  Speichern Sie Ihre Datei, nachdem Sie die erforderlichen Bearbeitungsschritte für die App vorgenommen haben.

Visual Studio kann Ihr Paket dem Store zuordnen. Dabei werden einige Felder der Registerkarte „Verpacken“ im Manifest-Designer automatisch aktualisiert.

## <a name="create-an-app-package"></a>Erstellen eines App-Pakets

Um eine App über den Store zu verteilen, müssen Sie ein App-Paket (.appx), ein App-Bundle (.appxbundle) oder ein Upload-Paket (.appxupload) erstellen. Verwenden Sie dazu den Assistenten **App-Pakete erstellen**. Führen Sie die folgenden Schritte aus, um ein Paket zu erstellen, das für die Store-Übermittlung in Visual Studio geeignet ist.

**So erstellen Sie das App-Paket**

1.  Öffnen Sie im **Projektmappen-Explorer** die Projektmappe für Ihr UWP-App-Projekt.
2.  Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Store**->**App-Pakete erstellen** aus. Wenn diese Option deaktiviert ist oder nicht angezeigt wird, überprüfen Sie, ob es sich beim Projekt um ein UWP-Projekt handelt.<br/>
    ![Kontextmenü mit Navigation zu „App-Pakete erstellen“](images/packaging-screen2.jpg)

    Der Assistent **App-Pakete erstellen** wird angezeigt.

3.  Wählen Sie im ersten Dialogfeld, in dem Sie gefragt werden, ob Sie Pakete zum Hochladen in den Windows Store erstellen möchten, „Ja“ aus, und klicken Sie auf „Weiter“.<br/>
    ![Dialogfeld „Ihre Pakete erstellen“](images/packaging-screen3.jpg)

    Wenn Sie hier „Nein“ auswählen, wird das für die Store-Übermittlung benötigte APPXUPLOAD-Paket von Visual Studio nicht generiert. Sie können diese Option auswählen, wenn Sie die App lediglich für die Ausführung auf internen Geräten querladen möchten. Weitere Informationen zum Querladen finden Sie unter [Aktivieren Ihres Geräts für die Entwicklung](https://msdn.microsoft.com/library/windows/apps/Dn706236).

4.  Melden Sie sich mit Ihrem Entwicklerkonto beim Windows Dev Center an. (Wenn Sie noch kein Entwicklerkonto besitzen, hilft Ihnen der Assistent bei der Erstellung.)
5.  Wählen Sie den App-Namen für das Paket aus, oder reservieren Sie einen neuen Namen, wenn Sie noch kein Paket im Windows Dev Center-Portal reserviert haben.<br/>
    ![Dialogfeld „App-Pakete erstellen“ mit Auswahl des App-Namens](images/packaging-screen4.jpg)
6.  Stellen Sie sicher, dass Sie im Dialogfeld **Auswählen und Konfigurieren von Paketen** alle drei Architekturkonfigurationen (x86, x64 und ARM) auswählen. Auf diese Weise kann Ihre App auf einer breiten Palette von Geräten bereitgestellt werden. Wählen Sie im Listenfeld **App-Bundle erstellen** die Option **Immer**. Dadurch wird die Store-Übermittlung an den Store erheblich vereinfacht, weil nur eine Datei („.appxupload“) hochgeladen werden muss. Das einzelne Bundle enthält alle notwendigen Pakete für die Bereitstellung auf Geräten mit den einzelnen Prozessorarchitekturen, sowie wichtige Informationen für das Debugging und die Absturzanalyse. Weitere Informationen zu Paket-Architekturen für verschiedene Geräte finden Sie unter [App-Paket-Architekturen](https://docs.microsoft.com/windows/uwp/packaging/device-architecture).<br/>
    ![Dialogfeld „App-Pakete erstellen“ mit Paketkonfiguration](images/packaging-screen5.jpg)
7.  Es empfiehlt sich dringend, vollständige PDB-Symboldateien einzuschließen, um eine optimale [Absturzanalyse](http://blogs.windows.com/buildingapps/2015/07/13/crash-analysis-in-the-unified-dev-center/) im Windows Dev Center zu erhalten. Weitere Informationen zum Debuggen mit Symbolen finden Sie unter [Debuggen mit Symbolen](https://msdn.microsoft.com/library/windows/desktop/Ee416588).
8.  Jetzt können Sie die Details für die Paketerstellung konfigurieren. Sobald Sie für die Veröffentlichung der App bereit sind, laden Sie die Pakete aus dem Ausgabepfad hoch.
9.  Klicken Sie auf **Erstellen**, um das APPXUPLOAD-Paket zu generieren.
10. Anschließend wird Ihnen dieses Dialogfeld angezeigt.<br/>
    ![Dialogfeld „Paketerstellung abgeschlossen“ mit Überprüfungsoptionen](images/packaging-screen6.jpg)

    Überprüfen Sie Ihre App, bevor Sie sie zur Zertifizierung an den Store übermitteln, auf einem lokalen oder Remotecomputer. Versionsbuilds können nur für Ihr App-Paket, nicht aber für Debugbuilds überprüft werden.

11. Für eine lokale Überprüfung lassen Sie die Option **Lokaler Computer** aktiviert und klicken auf **Zertifizierungskit für Windows-Apps starten**. Weitere Informationen zum Testen der App mit dem Zertifizierungskit für Windows-Apps finden Sie unter [Zertifizierungskit für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/Mt186449).

    Das Zertifizierungskit für Windows-Apps führt die verschiedene Tests aus und gibt die Ergebnisse zurück. Weitere Informationen finden Sie unter [Tests des Zertifizierungskits für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/mt186450).

    Wenn Sie über ein Windows 10-Gerät verfügen, das Sie zum Testen verwenden möchten, müssen Sie das Zertifizierungskit für Windows-Apps manuell auf dem Gerät installieren. Im nächsten Abschnitt werden die erforderlichen Schritte beschrieben. Nachdem Sie damit fertig sind, wählen Sie **Remotecomputer** und klicken auf **Zertifizierungskit für Windows-Apps starten**, um eine Verbindung zum Remotegerät herzustellen und die Überprüfungen ausführen.

12. Nachdem das WACK abgeschlossen ist und die App erfolgreich getestet wurde, können Sie sie in den Store übermitteln. Stellen Sie sicher, dass Sie die richtige Datei hochladen. Sie befindet sich im Stammordner der Projektmappe „\\\[AppName\]\\AppPackages“ und endet mit der Dateierweiterung „.appxupload“ (oder der Erweiterung .appx/.appxbundle – je nach Szenario). Der Name hat das Format „\[AppName\]\_\[AppVersion\]\_x86\_x64\_arm\_bundle.appxupload“.

**Überprüfen des App-Pakets auf einem Windows 10-Remotegerät**

1.  Aktivieren Sie das Windows 10-Gerät für die Entwicklung, indem Sie die Anweisungen unter [Aktivieren Ihres Geräts für die Entwicklung](https://msdn.microsoft.com/library/windows/apps/Dn706236) befolgen.
    **Wichtig**  Sie können das App-Paket nicht auf einem ARM-Remotegerät für Windows10 überprüfen.
2.  Laden Sie die Remotetools für Visual Studio herunter, und installieren Sie sie. Diese Tools werden verwendet, um das Zertifizierungskit für Windows-Apps remote auszuführen. Weitere Informationen zu diesen Tools einschließlich der Downloadseite finden Sie unter [Ausführen von Windows Store-Apps auf einem Remotecomputer](https://msdn.microsoft.com/library/hh441469.aspx#BKMK_Starting_the_Remote_Debugger_Monitor).
3.  Laden Sie das erforderliche [Zertifizierungskit für Windows-Apps](http://go.microsoft.com/fwlink/p/?LinkID=309666) herunter, und installieren Sie es auf Ihrem Windows 10-Remotegerät.
4.  Aktivieren Sie auf der Seite **Paketerstellung abgeschlossen** des Assistenten das Optionsfeld **Remotecomputer**. Klicken Sie anschließend neben der Schaltfläche **Testverbindung** auf die Schaltfläche mit den Auslassungszeichen.
    **Hinweis**  Das Optionsfeld **Remotecomputer** ist nur verfügbar, wenn Sie mindestens eine Projektmappenkonfiguration ausgewählt haben, die die Überprüfung unterstützt. Weitere Informationen zum Testen der App mit dem WACK finden Sie unter [Zertifizierungskit für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/Mt186449).
5.  Geben Sie ein Gerät vom Subnetz aus an, oder geben Sie den DNS-Namen (Domain Name Server) oder die IP-Adresse eines Geräts an, das sich außerhalb des Subnetzes befindet.
6.  Wählen Sie in der Liste **Authentifizierungsmodus** die Option **Keiner** aus, wenn Ihr Gerät keine Anmeldung mittels Windows-Anmeldeinformationen erfordert.
7.  Klicken Sie auf die Schaltfläche **Auswählen** und anschließend auf die Schaltfläche **Zertifizierungskit für Windows-Apps starten**. Wenn die Remotetools auf diesem Gerät ausgeführt werden, stellt Visual Studio eine Verbindung her und führt die Überprüfungstests aus. Weitere Informationen finden Sie unter [Tests im Zertifizierungskit für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/mt186450).

## <a name="sideload-your-app-package"></a>Querladen des App-Pakets

In Windows10 Anniversary Update wurden App-Pakete eingeführt, die einfach durch Doppelklicken auf die App-Paketdatei installiert werden. Um dies zu verwenden, navigieren Sie einfach zu Ihrer App-Paket- (.appx) oder App-Bundle (.appxbundle)-Datei, und doppelklicken Sie darauf. Die App-Installer startet und bietet einfache App-Informationen sowie auch eine Installieren-Schaltfläche, Installationsstatusanzeige und alle relevanten Meldungen. 

![App-Installer zeigt eine Beispiel-App namens Contoso für die Installation an](images/appinstaller-screen.png)

> [!NOTE]
> Die App-Installer geht davon aus, dass die App vom Gerät als vertrauenswürdig eingestuft wird. Wenn Sie eine Entwickler- oder Unternehmens-App Querladen, müssen Sie das Signaturzertifikat im Speicher für vertrauenswürdige Stammzertifizierungsstellen auf dem Gerät installieren. Wenn Sie nicht sicher sind, wie Sie hierzu vorgehen, finden Sie unter [Testzertifikate installieren](https://docs.microsoft.com/windows-hardware/drivers/install/installing-test-certificates) weitere Infos.

### <a name="sideload-your-app-on-previous-versions-of-windows"></a>Querladen Ihrer App auf früheren Versionen von Windows
Apps werden nicht mit UWP-App-Paketen auf einem Gerät installiert, mit Desktop-Apps werden. In der Regel Laden Sie UWP-Apps aus dem Store herunter, der die App Ihr Gerät auch für Sie installiert. Apps können ohne die Übermittlung an den Store installiert werden (Querladen). Bei dieser Vorgehensweise können Sie die App nach der Installation mit dem erstellten App-Paket („.appx“) testen. Wenn Sie über eine App verfügen, die Sie nicht im Store anbieten möchten (z. B. eine branchenspezifische App), können Sie diese App querladen, um sie für Kollegen im Unternehmen bereitzustellen.

Die folgende Liste enthält die Anforderungen für das Querladen von Apps.

-   Sie müssen [Ihr Gerät für die Entwicklung aktivieren](https://msdn.microsoft.com/library/windows/apps/Dn706236).
-   Wenn Sie Ihre App auf ein Windows 10 Mobile-Gerät querladen möchten, verwenden Sie das Tool [WinAppDeployCmd.exe](install-universal-windows-apps-with-the-winappdeploycmd-tool.md).

**Querladen einer App auf einen Desktop, Laptop oder Tablet**

1.  Kopieren Sie die Ordner der zu installierenden App-Version auf das Zielgerät.

    Wenn Sie ein App-Bündel erstellt haben, verfügen Sie über einen Ordnernamen bestehend aus Versionsnummer und dem Zusatz `*\_Test`. Zum Beispiel die beiden folgenden Ordner (wobei die Version 1.0.2.0 installiert wird):

    -   `C:\\Projects\\MyApp\\MyApp\\AppPackages\\MyApp\_1.0.2.0`
    -   `C:\\Projects\\MyApp\\MyApp\\AppPackages\\MyApp\_1.0.2.0\_Test`

    Wenn Sie über kein App-Bündel verfügen, können Sie den Ordner kopieren, um die richtige Architektur und den entsprechenden `*\_Test`-Ordner zu übernehmen. Die beiden Ordner sind ein Beispiel für ein App-Paket mit der x64 Architektur und seinen `*\_Test`-Ordner:

    -   `C:\\Projects\\MyApp\\MyApp\\AppPackages\\MyApp\_1.0.2.0\_x64`
    -   `C:\\Projects\\MyApp\\MyApp\\AppPackages\\MyApp\_1.0.2.0\_x64\_Test`

2.  Öffnen Sie den `*\_Test`-Ordner auf dem Zielgerät.
3.  Mit der rechten Maustaste auf die **Add-AppDevPackage.ps1**-Datei. Wählen Sie **Mit PowerShell ausführen** und befolgen die Anweisungen.<br/>
    ![Datei-Explorer mit Navigation zum PowerShell-Skript](images/packaging-screen7.jpg)

    Nachdem das App-Paket installiert wurde, wird Ihnen die folgende Meldung im PowerShell-Fenster angezeigt: **Ihre App wurde erfolgreich installiert**.

    **Tipp**: Wenn Sie das Kontextmenü auf einem Tablet öffnen möchten, berühren Sie den Bildschirm an der Stelle, an der Sie mit der rechten Maustaste klicken möchten. Drücken Sie so lange, bis ein vollständiger Kreis angezeigt wird, und lassen Sie dann wieder los. Das Kontextmenü wird geöffnet, sobald Sie loslassen.
4.  Klicken Sie auf die Schaltfläche „Start“, und geben Sie den Namen der App ein, um sie zu suchen und zu starten.
