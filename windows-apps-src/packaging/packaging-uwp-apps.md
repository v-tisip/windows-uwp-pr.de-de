---
author: laurenhughes
ms.assetid: 96361CAF-C347-4671-9721-8208CE118CA4
title: Verpacken von UWP-Apps
description: Um Ihre UWP-App (Universelle Windows-Plattform) zu vertreiben und zu verkaufen, müssen Sie ein App-Paket erstellen.
ms.author: lahugh
ms.date: 09/30/2018
ms.topic: article
keywords: Windows10, UWP
f1_keywords:
- vs.packagewizard
- vs.storeassociationwizard
ms.localizationpriority: medium
ms.openlocfilehash: 03d656d7a79dfa2a09e98f0fd54d9d0a4924559e
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6985432"
---
# <a name="package-a-uwp-app-with-visual-studio"></a>Verpacken einer UWP-App mit Visual Studio

Um Ihre Universelle Windows Plattform (UWP)-App zu verkaufen oder an andere Benutzer zu verteilen, müssen Sie es verpacken. Wenn Sie Ihre App nicht über den Microsoft Store verteilen möchten, können Sie das App-Paket direkt auf einem Gerät querladen oder über [Web Install](installing-UWP-apps-web.md) verteilen. In diesem Artikel wird das Konfigurieren, Erstellen und Testen von UWP-App-Paketen mit Visual Studio beschrieben. Weitere Informationen zum Verwalten und Bereitstellen von branchenspezifischen Apps (Line-of-Business, LOB) finden Sie unter [Enterprise-App-Verwaltung](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management).

In Windows 10 können Sie ein app-Paket oder app-Bündel, eine vollständige app-paketuploaddatei in das [Partner Center](https://partner.microsoft.com/dashboard)übermitteln. Unter diesen Optionen werden mit der Übermittlung einer Paketuploaddatei optimale Ergebnisse erzielt. 

## <a name="types-of-app-packages"></a>App-Pakettypen

- **App-Paket (.appx oder .msix)**  
    Eine Datei, die Ihre App in einem Format enthält, das auf einem Gerät quergeladen werden kann. Jeder einzelnen app-Paketdatei von Visual Studio erstellte ist **nicht** dafür vorgesehen, in das Partner Center übermittelt werden und für das querladen und nur zu Testzwecken verwendet werden soll. Wenn Sie Ihre app in das Partner Center übermitteln möchten, verwenden Sie die app-paketuploaddatei.  

- **App-Bündel (.appxbundle oder .msixbundle)**  
    Ein App-Bündel ist ein Pakettyp, der mehrere App-Pakete enthalten kann, von denen jedes so erstellt wurde, dass es eine bestimmte Gerätearchitektur unterstützt. Beispielsweise kann ein App-Bündel drei separate App-Pakete für die Konfigurationen x86, x64 und ARM enthalten. App-Bündel sollten nach Möglichkeit generiert werden, da sie ermöglichen, dass Ihre App auf den verschiedensten Geräten verfügbar ist.  

- **App-Paketuploaddatei (.appxupload)**  
    Eine einzelne Datei, die mehrere App-Pakete oder ein App-Bündel zur Unterstützung verschiedener Prozessorarchitekturen enthalten kann. Die Upload-Datei enthält auch eine Symboldatei für das [Analysieren der App-Leistung](https://docs.microsoft.com/windows/uwp/publish/analytics) nach der Veröffentlichung Ihrer App im Microsoft Store. Diese Datei wird automatisch für Sie erstellt werden, wenn Sie Ihre app mit Visual Studio Verpacken, um es in das Partner Center für die Veröffentlichung zu übermitteln. Es ist wichtig zu beachten, dass hierbei handelt es sich die **nur** gültige app-Paket Partner Center-Übermittlungen, die mithilfe von Visual Studio erstellt werden kann.

Hier sehen Sie eine Übersicht über die Schrittezum Vorbereiten und Erstellen eines App-Pakets:

1.  [Vor dem Verpacken der App](#before-packaging-your-app). Um sicherzustellen, dass Ihre app zum Partner Center verpackt werden bereit ist, gehen Sie wie folgt vor.
2.  [Konfigurieren eines App-Pakets](#configure-an-app-package). Verwenden Sie den Visual Studio Manifest-Designer, um das Paket zu konfigurieren. Fügen Sie beispielsweise Kachelbilder hinzu, und wählen Sie die von Ihrer App unterstützten Ausrichtungen aus.
3.  [Erstellen einer App-Paketuploaddatei](#create-an-app-package-upload-file). Verwenden Sie den Visual Studio App-Verpackungsassistenten, um ein App-Paket zu erstellen. Zertifizieren Sie dann Ihr Paket mit dem Zertifizierungskit für Windows-Apps.
4.  [Querladen des App-Pakets](#sideload-your-app-package). Nach dem Querladen Ihrer App auf ein Gerät können Sie testen, ob sie erwartungsgemäß funktioniert.

Nachdem Sie die vorangehenden Schritte abgeschlossen haben, können Sie Ihre App verteilen. Wenn Sie eine Line-of-Business (LOB)-app, die Sie nicht verkaufen verfügen, sondern nur internen Benutzern möchten, können Sie diese app zur Installation auf jedem Windows 10-Gerät querladen.

## <a name="before-packaging-your-app"></a>Vor dem Verpacken der App

1.  **Testen der App.** Bevor Sie Ihre app für die Übermittlung Partner Center Verpacken, stellen Sie sicher, dass sie erwartungsgemäß funktioniert auf allen gerätefamilien, die Sie unterstützen möchten. Diese Gerätefamilien umfassen Desktop-, Mobile-, Surface Hub-, Xbox-, IoT- und andere Geräte.
2.  **Optimieren der App.** Sie können die Profilerstellungs- und Debugtools von Visual Studio verwenden, um die Leistung Ihrer UWP-App zu optimieren. Zu diesen Tools gehören das Zeitachsentool für „Reaktionsfähigkeit der Benutzeroberfläche“, das Speichernutzungstool, das CPU-Auslastungstool und viele mehr. Weitere Informationen zur Verwendung dieser Tools finden Sie im Thema [Profilerstellungsfeature-Tour](https://docs.microsoft.com/visualstudio/profiling/profiling-feature-tour).
3.  **Überprüfen der .NET Native-Kompatibilität (für VB- und C#-Apps).** Mit der Universelle Windows-Plattform wurde ein neuer systemeigener Compiler eingeführt, der die Laufzeitleistung Ihrer App verbessert. Diese Änderung macht es erforderlich, dass Sie Ihre App in dieser Kompilierungsumgebung testen. Standardmäßig aktiviert die **Release**-Buildkonfiguration die .NET Native-Toolkette. Daher ist es wichtig, die App und das erwartete Verhalten mit dieser **Release**-Konfiguration zu testen. Einige häufige Debugprobleme, die bei .NET Native auftreten können, werden [Native .NET Windows Universal Apps debuggen](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx) ausführlich erläutert.

## <a name="configure-an-app-package"></a>Konfigurieren eines App-Pakets

Die App-Manifestdatei (Package.appxmanifest.xml) ist eine XML-Datei, die über die Eigenschaften und Einstellungen verfügt, die für die Erstellung des App-Pakets erforderlich sind. Die Eigenschaften in der App-Manifestdatei beschreiben z. B. das Bild, das als App-Kachel verwendet wird, und die Ausrichtungen, die von der App beim Drehen des Geräts unterstützt werden.

Visual Studio verfügt über einen Manifest-Designer, mit dem Sie die Manifestdatei ohne Bearbeitung der XML-Rohdaten der Datei aktualisieren können.

**Konfigurieren eines Pakets mit dem Manifest-Designer**

1.  Erweitern Sie im **Projektmappen-Explorer** den Projektknoten Ihrer UWP-App.
2.  Doppelklicken Sie auf die Datei **Package.appxmanifest**. Wenn die Manifestdatei bereits in der XML-Codeansicht geöffnet ist, werden Sie von Visual Studio zum Schließen der Datei aufgefordert.
3.  Jetzt können Sie entscheiden, wie Sie Ihre App konfigurieren möchten. Jede Registerkarte enthält Informationen, die Sie für Ihre App konfigurieren können, sowie Links zu weiteren Informationen, wenn notwendig.  
    ![Manifest-Designer in Visual Studio](images/packaging-screen1.jpg)

    Überprüfen Sie auf der Registerkarte **Visuelle Anlagen**, ob Sie über alle Bilder verfügen, die für eine UWP-App erforderlich sind.

    Auf der Registerkarte **Verpacken** können Sie Veröffentlichungsdaten eingeben. An dieser Stelle können Sie auswählen, welches Zertifikat zur Signierung der App verwendet werden soll. Alle UWP-Apps müssen anhand eines Zertifikats signiert werden. 
    
    >[!IMPORTANT]
    >Wenn Sie Ihre App im Microsoft Store veröffentlichen, wird Ihre App mit einem vertrauenswürdigen Zertifikat für Sie signiert. Dadurch kann der Benutzer Ihre App installieren und ausführen, ohne das zugehörige App-Signaturzertifikat zu installieren. 
    
    Wenn Sie Ihre App nicht veröffentlichen und einfach ein App-Paket querladen möchten, müssen Sie zunächst dem Paket vertrauen. Um dem Paket zu vertrauen, muss das Zertifikat auf dem Gerät des Benutzers installiert sein. Weitere Informationen zum Querladen finden Sie unter [Aktivieren Ihres Geräts für die Entwicklung](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development).

4.  Speichern Sie die Datei **Package.appxmanifest**, nachdem Sie die erforderlichen Bearbeitungsschritte für die App vorgenommen haben.

Wenn Sie Ihre App über den Microsoft Store verteilen, kann Visual Studio Ihr Paket dem Store zuordnen. Wenn Sie Ihre App zuordnen, werden einige Felder der Registerkarte „Verpacken“ im Manifest-Designer automatisch aktualisiert.

## <a name="create-an-app-package-upload-file"></a>Erstellen einer App-Paketuploaddatei

Um eine app über den Microsoft Store verteilen müssen Sie ein app-Paket (.appx oder .msix), app-Bündel (.appxbundle oder .msixbundle), oder ein Upload-Paket (.appxupload) und [übermitteln das app-Paket in das Partner Center](https://docs.microsoft.com/windows/uwp/publish/app-submissions)erstellen. Obwohl es möglich, ein app-Paket oder app-Bündel in das Partner Center allein zu übermitteln, werden Sie aufgefordert, ein uploadpaket zu übermitteln.

>[!NOTE]
> Die app-paketuploaddatei (.appxupload) ist der Typ **nur** gültige app-Pakets für das Partner Center, die mithilfe von Visual Studio erstellt werden kann. Weitere gültige [App-Pakete können manuell](https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool), ohne Visual Studio erstellt werden. 

Verwenden Sie dazu den Assistenten **App-Pakete erstellen**. Befolgen Sie diese Schritte, um ein Paket zu erstellen, die für die Übermittlung von Partner Center mithilfe von Visual Studio geeignet ist.

**So erstellen Sie Ihre App-Paketuploaddatei**

1.  Öffnen Sie im **Projektmappen-Explorer** die Projektmappe für Ihr UWP-App-Projekt.
2.  Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Store**->**App-Pakete erstellen** aus. Wenn diese Option deaktiviert ist oder nicht angezeigt wird, überprüfen Sie, ob es sich beim Projekt um ein Universal Windows-Projekt handelt.  
    ![Kontextmenü mit Navigation zu „App-Pakete erstellen“](images/packaging-screen2.jpg)

    Der Assistent **App-Pakete erstellen** wird angezeigt.

3.  Wählen Sie "Ja" im ersten Dialogfeld gefragt werden, ob Sie Pakete zum Hochladen in Partner Center, und klicken Sie dann als Nächstes erstellen möchten.  
    ![Dialogfeld „Ihre Pakete erstellen“](images/packaging-screen3.jpg)

    Wenn Sie auf "Nein" auswählen, wird die app-paketuploaddatei (.appxupload) an für Partner Center-Übermittlungen von Visual Studio nicht generiert. Sie können diese Option auswählen, wenn Sie die App lediglich für die Ausführung auf internen Geräten querladen oder für Testzwecke verwenden möchten. Weitere Informationen zum Querladen finden Sie unter [Aktivieren Ihres Geräts für die Entwicklung](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development).
4.  Melden Sie sich mit Ihrem Entwicklerkonto beim Partner Center werden soll. Wenn Sie noch kein Entwicklerkonto besitzen, hilft Ihnen der Assistent bei der Erstellung.
5.  Wählen Sie den app-Namen für Ihr Paket, oder reservieren Sie eine neue, wenn Sie noch kein Paket im Partner Center reserviert haben.  
    ![Dialogfeld „App-Pakete erstellen“ mit Auswahl des App-Namens](images/packaging-screen4.jpg)
6.  Stellen Sie sicher, dass Sie im Dialogfeld **Auswählen und Konfigurieren von Paketen** alle drei Architekturkonfigurationen (x86, x64 und ARM) auswählen, um zu gewährleisten, dass Ihre App auf einer breiten Palette von Geräten bereitgestellt werden kann. Wählen Sie im Listenfeld **App-Bündel erstellen** die Option **Immer**. Ein app-Bündel (.appxbundle) wird über eine einzelne app-Paketdatei bevorzugt, da es enthält eine Sammlung von app-Pakete, die für jeden Prozessor-Architekturtyp konfiguriert sind. Wenn Sie das App-Bündel generieren, wird es zusammen mit Informationen für das Debugging und die Absturzanalyse in die endgültige App-Paketuploaddatei (.appxupload) mit aufgenommen. Wenn Sie nicht sicher sind, welche Architektur(en) Sie auswählen sollen, oder wenn Sie mehr darüber erfahren möchten, welche Architekturen von verschiedenen Geräten verwendet werden, finden Sie weitere Informationen unter [App-Paketarchitekturen](https://docs.microsoft.com/windows/uwp/packaging/device-architecture).  
    ![Dialogfeld „App-Pakete erstellen“ mit Paketkonfiguration](images/packaging-screen5.jpg)


7.  Einbinden Sie vollständige PDB-Symboldateien wird zu [Analysieren app-Leistung](https://docs.microsoft.com/windows/uwp/publish/analytics) aus dem Partner Center, nachdem Ihre app veröffentlicht wurde. Konfigurieren Sie zusätzliche Details wie die Versionsnummer oder den Ausgabespeicherort des Pakets.
9.  Klicken Sie zum Erstellen des App-Pakets auf **Erstellen**. Wenn Sie in Schritt 3 **Ja** ausgewählt und ein Paket für die Übermittlung Partner Center erstellen, erstellt der Assistent eine paketuploaddatei (.appxupload). Wenn Sie in Schritt 3 **Nein** ausgewählt haben, erstellt der Assistent je nach Ihrer Auswahl in Schritt 6 entweder ein einzelnes App-Paket oder ein App-Bündel.
10. Wenn Ihre App erfolgreich verpackt wurde, wird dieses Dialogfeld angezeigt.  
    ![Dialogfeld „Paketerstellung abgeschlossen“ mit Überprüfungsoptionen](images/packaging-screen6.jpg)

    Überprüfen Sie Ihre app, bevor Sie sie zur Zertifizierung auf einem lokalen oder Remotecomputer zu Partner Center übermitteln. Versionsbuilds können nur für Ihr App-Paket, nicht aber für Debugbuilds überprüft werden.

11. Für eine lokale Überprüfung Ihrer App lassen Sie die Option **Lokaler Computer** aktiviert und klicken auf **Zertifizierungskit für Windows-Apps starten**. Weitere Informationen zum Testen der App mit dem Zertifizierungskit für Windows-Apps finden Sie unter [Zertifizierungskit für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/Mt186449).

    Das Zertifizierungskit für Windows-Apps führt die verschiedene Tests aus und gibt die Ergebnisse zurück. Weitere Informationen finden Sie unter [Tests des Zertifizierungskits für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/mt186450).

    Wenn Sie ein Windows 10-Remotegerät, die Sie zum Testen verwenden möchten verfügen, müssen Sie das Zertifizierungskit für Windows-Apps manuell auf dem Gerät installieren. Im nächsten Abschnitt werden die erforderlichen Schritte beschrieben. Nachdem Sie damit fertig sind, wählen Sie **Remotecomputer** und klicken auf **Zertifizierungskit für Windows-Apps starten**, um eine Verbindung zum Remotegerät herzustellen und die Überprüfungen ausführen.

12. Nachdem WACK abgeschlossen hat, und Ihre app Zertifizierung bestanden hat, können Sie Ihre app in das Partner Center übermitteln. Stellen Sie sicher, dass Sie die richtige Datei hochladen. Der Standardspeicherort der Datei befindet sich im Stammordner der Projektmappe `\[AppName]\AppPackages` und endet mit der Dateierweiterung „.appxupload“. Wenn Sie ein App-Bündel mit allen ausgewählten Paketarchitekturen gewählt haben, nimmt der Name das Format `[AppName]_[AppVersion]_x86_x64_arm_bundle.appxupload` an.

Weitere Informationen zum Übermitteln Ihrer app in das Partner Center finden Sie in der [App-Übermittlungen](https://docs.microsoft.com/windows/uwp/publish/app-submissions).

**Überprüfen Sie Ihre app-Paket auf einem Windows 10-Remotegerät**

1.  Aktivieren Sie Ihr Windows 10-Gerät für die Entwicklung gemäß die Anweisungen zum [Aktivieren Ihres Geräts für die Entwicklung](https://msdn.microsoft.com/library/windows/apps/Dn706236) .
    **Wichtige**Sie können das app-Paket auf einem ARM-Remotegerät für Windows 10 überprüfen.
2.  Laden Sie die Remotetools für Visual Studio herunter, und installieren Sie sie. Diese Tools werden verwendet, um das Zertifizierungskit für Windows-Apps remote auszuführen. Weitere Informationen zu diesen Tools einschließlich der Downloadseite finden Sie unter [Ausführen von UWP-Apps auf einem Remotecomputer](https://msdn.microsoft.com/library/hh441469.aspx#BKMK_Starting_the_Remote_Debugger_Monitor).
3.  Herunterladen Sie erforderliche [Zertifizierungskits](http://go.microsoft.com/fwlink/p/?LinkID=309666) und installieren Sie es auf Ihrem Windows 10-Remotegerät.
4.  Aktivieren Sie auf der Seite **Paketerstellung abgeschlossen** des Assistenten das Optionsfeld **Remotecomputer**. Klicken Sie anschließend neben der Schaltfläche **Testverbindung** auf die Schaltfläche mit den Auslassungszeichen.
    **Hinweis:** das Optionsfeld **Remotecomputer** ist nur verfügbar, wenn Sie mindestens eine Projektmappenkonfiguration ausgewählt haben, die Überprüfung unterstützt. Weitere Informationen zum Testen der App mit dem WACK finden Sie unter [Zertifizierungskit für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/Mt186449).
5.  Geben Sie ein Gerät vom Subnetz aus an, oder geben Sie den DNS-Namen (Domain Name Server) oder die IP-Adresse eines Geräts an, das sich außerhalb des Subnetzes befindet.
6.  Wählen Sie in der Liste **Authentifizierungsmodus** die Option **Keiner** aus, wenn Ihr Gerät keine Anmeldung mittels Windows-Anmeldeinformationen erfordert.
7.  Klicken Sie auf die Schaltfläche **Auswählen** und anschließend auf die Schaltfläche **Zertifizierungskit für Windows-Apps starten**. Wenn die Remotetools auf diesem Gerät ausgeführt werden, stellt Visual Studio eine Verbindung mit dem Gerät her und führt die Überprüfungstests aus. Weitere Informationen finden Sie unter [Tests im Zertifizierungskit für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/mt186450).

## <a name="sideload-your-app-package"></a>Querladen des App-Pakets

In Windows10 Anniversary Update wurden App-Pakete eingeführt, die einfach durch Doppelklicken auf die App-Paketdatei installiert werden. Um dies zu verwenden, navigieren Sie zu Ihrer app-Paket oder app-Bündel-Datei, und doppelklicken darauf klicken. Die App-Installer startet und bietet einfache App-Informationen sowie auch eine Installieren-Schaltfläche, Installationsstatusanzeige und alle relevanten Meldungen. 

![App-Installer zeigt eine Beispiel-App namens Contoso für die Installation an](images/appinstaller-screen.png)

> [!NOTE]
> Die App-Installer geht davon aus, dass die App vom Gerät als vertrauenswürdig eingestuft wird. Wenn Sie eine Entwickler- oder Unternehmens-App querladen, müssen Sie das Signaturzertifikat im Speicher für vertrauenswürdige Personen oder vertrauenswürdige Herausgeber auf dem Gerät installieren. Wenn Sie nicht sicher sind, wie Sie hierzu vorgehen, finden Sie unter [Testzertifikate installieren](https://docs.microsoft.com/windows-hardware/drivers/install/installing-test-certificates) weitere Infos.

### <a name="sideload-your-app-on-previous-versions-of-windows"></a>Querladen Ihrer App auf früheren Versionen von Windows
Apps werden nicht mit UWP-App-Paketen auf einem Gerät installiert, mit Desktop-Apps werden. In der Regel laden Sie UWP-Apps aus dem Microsoft Store herunter, wodurch die App auch auf Ihrem Gerät installiert wird. Apps können installiert werden, ohne im Store veröffentlicht zu werden (Querladen). Auf diese Weise können Sie bei der Installation und Test mit dem app-Paket-Datei, die Sie erstellt haben. Wenn Sie über eine App verfügen, die Sie nicht im Store anbieten möchten (z. B. eine branchenspezifische App), können Sie diese App querladen, um sie für Kollegen im Unternehmen bereitzustellen.

Die folgende Liste enthält die Anforderungen für das Querladen von Apps.

-   Sie müssen [Ihr Gerät für die Entwicklung aktivieren](https://msdn.microsoft.com/library/windows/apps/Dn706236).
-   Verwenden Sie zum querladen Ihrer app auf einem Windows 10 Mobile-Gerät das [WinAppDeployCmd.exe](install-universal-windows-apps-with-the-winappdeploycmd-tool.md) Tool.

**Querladen einer App auf einen Desktop, Laptop oder Tablet**

1.  Kopieren Sie die Ordner der zu installierenden App-Version auf das Zielgerät.

    Wenn Sie ein App-Bündel erstellt haben, verfügen Sie über einen Ordnernamen bestehend aus Versionsnummer und dem Zusatz `*_Test`. Zum Beispiel die beiden folgenden Ordner (wobei die Version 1.0.2.0 installiert wird):

    -   `C:\Projects\MyApp\MyApp\AppPackages\MyApp_1.0.2.0`
    -   `C:\Projects\MyApp\MyApp\AppPackages\MyApp_1.0.2.0_Test`

    Wenn Sie über kein App-Bündel verfügen, können Sie den Ordner kopieren, um die richtige Architektur und den entsprechenden `*_Test`-Ordner zu übernehmen. Die beiden Ordner sind ein Beispiel für ein App-Paket mit der x64 Architektur und seinen `*_Test`-Ordner:

    -   `C:\Projects\MyApp\MyApp\AppPackages\MyApp_1.0.2.0_x64`
    -   `C:\Projects\MyApp\MyApp\AppPackages\MyApp_1.0.2.0_x64_Test`

2.  Öffnen Sie den `*_Test`-Ordner auf dem Zielgerät.
3.  Mit der rechten Maustaste auf die **Add-AppDevPackage.ps1**-Datei. Wählen Sie **Mit PowerShell ausführen** und befolgen die Anweisungen.  
    ![Datei-Explorer mit Navigation zum PowerShell-Skript](images/packaging-screen7.jpg)

    Nachdem das App-Paket installiert wurde, wird Ihnen die folgende Meldung im PowerShell-Fenster angezeigt: **Ihre App wurde erfolgreich installiert**.

    **Tipp**: um das Kontextmenü auf einem Tablet öffnen möchten, berühren Sie ihn, in denen Sie mit der rechten Maustaste, bis ein vollständiger Kreis angezeigt wird, und heben Ihre Finger möchten. Das Kontextmenü wird geöffnet, sobald Sie loslassen.
4.  Klicken Sie auf die Schaltfläche „Start“, und geben Sie den Namen der App ein, um sie zu suchen und zu starten.
