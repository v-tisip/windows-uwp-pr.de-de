---
author: laurenhughes
ms.assetid: 96361CAF-C347-4671-9721-8208CE118CA4
title: Verpacken von UWP-Apps
description: Um Ihre UWP-App (Universelle Windows-Plattform) zu vertreiben und zu verkaufen, müssen Sie ein App-Paket erstellen.
ms.author: lahugh
ms.date: 06/10/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
f1_keywords:
- vs.packagewizard
- vs.storeassociationwizard
ms.localizationpriority: medium
ms.openlocfilehash: eb930c5e6b2c1c1f864f2e63fbce97c89bb89e1f
ms.sourcegitcommit: 232543fba1fb30bb1489b053310ed6bd4b8f15d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2018
ms.locfileid: "4180941"
---
# <a name="package-a-uwp-app-with-visual-studio"></a>Verpacken einer UWP-App mit Visual Studio

Um Ihre Universelle Windows Plattform (UWP)-App zu verkaufen oder an andere Benutzer zu verteilen, müssen Sie es verpacken. Wenn Sie Ihre App nicht über den Microsoft Store verteilen möchten, können Sie das App-Paket direkt auf einem Gerät querladen oder über [Web Install](installing-UWP-apps-web.md) verteilen. In diesem Artikel wird das Konfigurieren, Erstellen und Testen von UWP-App-Paketen mit Visual Studio beschrieben. Weitere Informationen zum Verwalten und Bereitstellen von branchenspezifischen Apps (Line-of-Business, LOB) finden Sie unter [Enterprise-App-Verwaltung](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management).

In Windows 10 können Sie ein App-Paket (.appx), ein App-Bündel (.appxbundle) oder eine vollständige App-Paketuploaddatei (.appxupload) an das Windows Dev Center übermitteln. Unter diesen Optionen werden mit der Übermittlung einer Paketuploaddatei optimale Ergebnisse erzielt. 

## <a name="types-of-app-packages"></a>App-Pakettypen

- **App-Paket (.appx)**  
    Eine Datei, die Ihre App in einem Format enthält, das auf einem Gerät quergeladen werden kann. Einzelne, von Visual Studio erstellte .appx-Paketdateien sollten **nicht** an Dev Center übermittelt werden und sind nur für das Querladen und zu Testzwecken zu verwenden. Wenn Sie Ihre App an Dev Center übermitteln möchten, verwenden Sie die App-Paketuploaddatei.  

- **App Bundle (.appxbundle)**  
    Ein App-Bündel ist ein Pakettyp, der mehrere App-Pakete enthalten kann, von denen jedes so erstellt wurde, dass es eine bestimmte Gerätearchitektur unterstützt. Beispielsweise kann ein App-Bündel drei separate App-Pakete für die Konfigurationen x86, x64 und ARM enthalten. App-Bündel sollten nach Möglichkeit generiert werden, da sie ermöglichen, dass Ihre App auf den verschiedensten Geräten verfügbar ist.  

- **App-Paketuploaddatei (.appxupload)**  
    Eine einzelne Datei, die mehrere App-Pakete oder ein App-Bündel zur Unterstützung verschiedener Prozessorarchitekturen enthalten kann. Die Upload-Datei enthält auch eine Symboldatei für das [Analysieren der App-Leistung](https://docs.microsoft.com/windows/uwp/publish/analytics) nach der Veröffentlichung Ihrer App im Microsoft Store. Diese Datei wird automatisch für Sie erstellt, wenn Sie Ihre App mit Visual Studio verpacken, um sie zur Veröffentlichung an Dev Center zu übermitteln. Es ist wichtig zu beachten, dass dies die **einzige** gültige Übermittlung eines App-Pakets an Dev Center ist, die mithilfe von Visual Studio erstellt werden kann.

Hier sehen Sie eine Übersicht über die Schrittezum Vorbereiten und Erstellen eines App-Pakets:

1.  [Vor dem Verpacken der App](#before-packaging-your-app). Führen Sie die folgenden Schritte aus, um sicherzustellen, dass die App verpackt und an Dev Center übermittelt werden kann.
2.  [Konfigurieren eines App-Pakets](#configure-an-app-package). Verwenden Sie den Visual Studio Manifest-Designer, um das Paket zu konfigurieren. Fügen Sie beispielsweise Kachelbilder hinzu, und wählen Sie die von Ihrer App unterstützten Ausrichtungen aus.
3.  [Erstellen einer App-Paketuploaddatei](#create-an-app-package-upload-file). Verwenden Sie den Visual Studio App-Verpackungsassistenten, um ein App-Paket zu erstellen. Zertifizieren Sie dann Ihr Paket mit dem Zertifizierungskit für Windows-Apps.
4.  [Querladen des App-Pakets](#sideload-your-app-package). Nach dem Querladen Ihrer App auf ein Gerät können Sie testen, ob sie erwartungsgemäß funktioniert.

Nachdem Sie die vorangehenden Schritte abgeschlossen haben, können Sie Ihre App verteilen. Eine branchenspezifische App, die Sie nicht verkaufen, sondern nur internen Benutzern zur Verfügung stellen möchten, können Sie querladen, um sie auf einem beliebigen Windows 10-Gerät zu installieren.

## <a name="before-packaging-your-app"></a>Vor dem Verpacken der App

1.  **Testen der App.** Bevor Sie Ihre App für die Übermittlung an Dev Center verpacken, stellen Sie sicher, dass sie auf allen Gerätefamilien, die unterstützt werden sollen, erwartungsgemäß funktioniert. Diese Gerätefamilien umfassen Desktop-, Mobile-, Surface Hub-, Xbox-, IoT- und andere Geräte.
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

Um eine App über den Microsoft Store zu verteilen, müssen Sie ein App-Paket (.appx), ein App-Bündel (.appxbundle) oder ein Upload-Paket (.appxupload) erstellen und [die verpackte App an Dev Center übermitteln](https://docs.microsoft.com/windows/uwp/publish/app-submissions). Es ist zwar möglich, nur ein App-Paket oder App-Bündel an Dev Center zu übermitteln, es wird jedoch empfohlen, ein Uploadpaket zu übermitteln.

>[!NOTE]
> Die App-Paketuploaddatei (.appxupload) ist der **einzig** gültige App-Pakettyp für Dev Center, der mithilfe von Visual Studio erstellt werden kann. Weitere gültige [App-Pakete können manuell](https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool), ohne Visual Studio erstellt werden. 

Verwenden Sie dazu den Assistenten **App-Pakete erstellen**. Führen Sie die folgenden Schritte aus, um ein Paket zu erstellen, das für die Übermittlung an Dev Center mithilfe von Visual Studio geeignet ist.

**So erstellen Sie Ihre App-Paketuploaddatei**

1.  Öffnen Sie im **Projektmappen-Explorer** die Projektmappe für Ihr UWP-App-Projekt.
2.  Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Store**->**App-Pakete erstellen** aus. Wenn diese Option deaktiviert ist oder nicht angezeigt wird, überprüfen Sie, ob es sich beim Projekt um ein Universal Windows-Projekt handelt.  
    ![Kontextmenü mit Navigation zu „App-Pakete erstellen“](images/packaging-screen2.jpg)

    Der Assistent **App-Pakete erstellen** wird angezeigt.

3.  Wählen Sie im ersten Dialogfeld, in dem Sie gefragt werden, ob Sie Pakete zum Hochladen ins Dev Center erstellen möchten, „Ja“ aus, und klicken Sie auf „Weiter“.  
    ![Dialogfeld „Ihre Pakete erstellen“](images/packaging-screen3.jpg)

    Wenn Sie „Nein“ auswählen, wird die für die Übermittlung an Dev Center benötigte App-Paketuploaddatei (.appxupload) von Visual Studio nicht generiert. Sie können diese Option auswählen, wenn Sie die App lediglich für die Ausführung auf internen Geräten querladen oder für Testzwecke verwenden möchten. Weitere Informationen zum Querladen finden Sie unter [Aktivieren Ihres Geräts für die Entwicklung](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development).
4.  Melden Sie sich mit Ihrem Entwicklerkonto beim Windows Dev Center an. Wenn Sie noch kein Entwicklerkonto besitzen, hilft Ihnen der Assistent bei der Erstellung.
5.  Wählen Sie den App-Namen für das Paket aus, oder reservieren Sie einen neuen Namen, wenn Sie noch kein Paket im Windows Dev Center-Portal reserviert haben.  
    ![Dialogfeld „App-Pakete erstellen“ mit Auswahl des App-Namens](images/packaging-screen4.jpg)
6.  Stellen Sie sicher, dass Sie im Dialogfeld **Auswählen und Konfigurieren von Paketen** alle drei Architekturkonfigurationen (x86, x64 und ARM) auswählen, um zu gewährleisten, dass Ihre App auf einer breiten Palette von Geräten bereitgestellt werden kann. Wählen Sie im Listenfeld **App-Bündel erstellen** die Option **Immer**. Ein App-Bündel (.appxbundle) wird gegenüber einem einzelnen App-Paket (.appx) bevorzugt, da es eine Sammlung von App-Paketen enthält, die für jeden Prozessor-Architekturtyp konfiguriert sind. Wenn Sie das App-Bündel generieren, wird es zusammen mit Informationen für das Debugging und die Absturzanalyse in die endgültige App-Paketuploaddatei (.appxupload) mit aufgenommen. Wenn Sie nicht sicher sind, welche Architektur(en) Sie auswählen sollen, oder wenn Sie mehr darüber erfahren möchten, welche Architekturen von verschiedenen Geräten verwendet werden, finden Sie weitere Informationen unter [App-Paketarchitekturen](https://docs.microsoft.com/windows/uwp/packaging/device-architecture).  
    ![Dialogfeld „App-Pakete erstellen“ mit Paketkonfiguration](images/packaging-screen5.jpg)


7.  Schließen Sie vollständige PDB-Symboldateien aus dem Windows Dev Center ein, um die [App-Leistung zu analysieren](https://docs.microsoft.com/windows/uwp/publish/analytics), nachdem Ihre App veröffentlicht wurde. Konfigurieren Sie zusätzliche Details wie die Versionsnummer oder den Ausgabespeicherort des Pakets.
9.  Klicken Sie zum Erstellen des App-Pakets auf **Erstellen**. Wenn Sie bei Schritt 3 **Ja** ausgewählt haben und nun ein Paket für die Übermittlung an Dev Center erstellen, erstellt der Assistent eine Paketuploaddatei (".appxupload"). Wenn Sie in Schritt 3 **Nein** ausgewählt haben, erstellt der Assistent je nach Ihrer Auswahl in Schritt 6 entweder ein einzelnes App-Paket oder ein App-Bündel.
10. Wenn Ihre App erfolgreich verpackt wurde, wird dieses Dialogfeld angezeigt.  
    ![Dialogfeld „Paketerstellung abgeschlossen“ mit Überprüfungsoptionen](images/packaging-screen6.jpg)

    Überprüfen Sie Ihre App auf einem lokalen oder Remotecomputer, bevor Sie sie zur Zertifizierung an Dev Center übermitteln. Versionsbuilds können nur für Ihr App-Paket, nicht aber für Debugbuilds überprüft werden.

11. Für eine lokale Überprüfung Ihrer App lassen Sie die Option **Lokaler Computer** aktiviert und klicken auf **Zertifizierungskit für Windows-Apps starten**. Weitere Informationen zum Testen der App mit dem Zertifizierungskit für Windows-Apps finden Sie unter [Zertifizierungskit für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/Mt186449).

    Das Zertifizierungskit für Windows-Apps führt die verschiedene Tests aus und gibt die Ergebnisse zurück. Weitere Informationen finden Sie unter [Tests des Zertifizierungskits für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/mt186450).

    Wenn Sie über ein Windows 10-Gerät verfügen, das Sie zum Testen verwenden möchten, müssen Sie das Zertifizierungskit für Windows-Apps manuell auf dem Gerät installieren. Im nächsten Abschnitt werden die erforderlichen Schritte beschrieben. Nachdem Sie damit fertig sind, wählen Sie **Remotecomputer** und klicken auf **Zertifizierungskit für Windows-Apps starten**, um eine Verbindung zum Remotegerät herzustellen und die Überprüfungen ausführen.

12. Nachdem das WACK abgeschlossen ist und die App erfolgreich zertifiziert wurde, können Sie sie an Dev Center übermitteln. Stellen Sie sicher, dass Sie die richtige Datei hochladen. Der Standardspeicherort der Datei befindet sich im Stammordner der Projektmappe `\[AppName]\AppPackages` und endet mit der Dateierweiterung „.appxupload“. Wenn Sie ein App-Bündel mit allen ausgewählten Paketarchitekturen gewählt haben, nimmt der Name das Format `[AppName]_[AppVersion]_x86_x64_arm_bundle.appxupload` an.

Weitere Informationen zum Übermitteln Ihrer App an Dev Center finden Sie unter [App-Übermittlungen](https://docs.microsoft.com/windows/uwp/publish/app-submissions).

**Überprüfen des App-Pakets auf einem Windows 10-Remotegerät**

1.  Aktivieren Sie das Windows 10-Gerät für die Entwicklung, indem Sie die Anweisungen unter [Aktivieren Ihres Geräts für die Entwicklung](https://msdn.microsoft.com/library/windows/apps/Dn706236) befolgen.
    **Wichtig**  Sie können das App-Paket nicht auf einem ARM-Remotegerät für Windows10 überprüfen.
2.  Laden Sie die Remotetools für Visual Studio herunter, und installieren Sie sie. Diese Tools werden verwendet, um das Zertifizierungskit für Windows-Apps remote auszuführen. Weitere Informationen zu diesen Tools einschließlich der Downloadseite finden Sie unter [Ausführen von UWP-Apps auf einem Remotecomputer](https://msdn.microsoft.com/library/hh441469.aspx#BKMK_Starting_the_Remote_Debugger_Monitor).
3.  Laden Sie das erforderliche [Zertifizierungskit für Windows-Apps](http://go.microsoft.com/fwlink/p/?LinkID=309666) herunter, und installieren Sie es auf Ihrem Windows 10-Remotegerät.
4.  Aktivieren Sie auf der Seite **Paketerstellung abgeschlossen** des Assistenten das Optionsfeld **Remotecomputer**. Klicken Sie anschließend neben der Schaltfläche **Testverbindung** auf die Schaltfläche mit den Auslassungszeichen.
    **Hinweis**  Das Optionsfeld **Remotecomputer** ist nur verfügbar, wenn Sie mindestens eine Projektmappenkonfiguration ausgewählt haben, die die Überprüfung unterstützt. Weitere Informationen zum Testen der App mit dem WACK finden Sie unter [Zertifizierungskit für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/Mt186449).
5.  Geben Sie ein Gerät vom Subnetz aus an, oder geben Sie den DNS-Namen (Domain Name Server) oder die IP-Adresse eines Geräts an, das sich außerhalb des Subnetzes befindet.
6.  Wählen Sie in der Liste **Authentifizierungsmodus** die Option **Keiner** aus, wenn Ihr Gerät keine Anmeldung mittels Windows-Anmeldeinformationen erfordert.
7.  Klicken Sie auf die Schaltfläche **Auswählen** und anschließend auf die Schaltfläche **Zertifizierungskit für Windows-Apps starten**. Wenn die Remotetools auf diesem Gerät ausgeführt werden, stellt Visual Studio eine Verbindung mit dem Gerät her und führt die Überprüfungstests aus. Weitere Informationen finden Sie unter [Tests im Zertifizierungskit für Windows-Apps](https://msdn.microsoft.com/library/windows/apps/mt186450).

## <a name="sideload-your-app-package"></a>Querladen des App-Pakets

In Windows10 Anniversary Update wurden App-Pakete eingeführt, die einfach durch Doppelklicken auf die App-Paketdatei installiert werden. Um dies zu verwenden, navigieren Sie einfach zu Ihrer App-Paket- (.appx) oder App-Bündel (.appxbundle)-Datei, und doppelklicken Sie darauf. Die App-Installer startet und bietet einfache App-Informationen sowie auch eine Installieren-Schaltfläche, Installationsstatusanzeige und alle relevanten Meldungen. 

![App-Installer zeigt eine Beispiel-App namens Contoso für die Installation an](images/appinstaller-screen.png)

> [!NOTE]
> Die App-Installer geht davon aus, dass die App vom Gerät als vertrauenswürdig eingestuft wird. Wenn Sie eine Entwickler- oder Unternehmens-App querladen, müssen Sie das Signaturzertifikat im Speicher für vertrauenswürdige Personen oder vertrauenswürdige Herausgeber auf dem Gerät installieren. Wenn Sie nicht sicher sind, wie Sie hierzu vorgehen, finden Sie unter [Testzertifikate installieren](https://docs.microsoft.com/windows-hardware/drivers/install/installing-test-certificates) weitere Infos.

### <a name="sideload-your-app-on-previous-versions-of-windows"></a>Querladen Ihrer App auf früheren Versionen von Windows
Apps werden nicht mit UWP-App-Paketen auf einem Gerät installiert, mit Desktop-Apps werden. In der Regel laden Sie UWP-Apps aus dem Microsoft Store herunter, wodurch die App auch auf Ihrem Gerät installiert wird. Apps können installiert werden, ohne im Store veröffentlicht zu werden (Querladen). Bei dieser Vorgehensweise können Sie die App mit dem App-Paket (.appx), das Sie erstellt haben, installieren und testen. Wenn Sie über eine App verfügen, die Sie nicht im Store anbieten möchten (z. B. eine branchenspezifische App), können Sie diese App querladen, um sie für Kollegen im Unternehmen bereitzustellen.

Die folgende Liste enthält die Anforderungen für das Querladen von Apps.

-   Sie müssen [Ihr Gerät für die Entwicklung aktivieren](https://msdn.microsoft.com/library/windows/apps/Dn706236).
-   Wenn Sie Ihre App auf ein Windows 10 Mobile-Gerät querladen möchten, verwenden Sie das Tool [WinAppDeployCmd.exe](install-universal-windows-apps-with-the-winappdeploycmd-tool.md).

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

    **Tipp**: Wenn Sie das Kontextmenü auf einem Tablet öffnen möchten, berühren Sie den Bildschirm an der Stelle, an der Sie mit der rechten Maustaste klicken möchten. Drücken Sie so lange, bis ein vollständiger Kreis angezeigt wird, und lassen Sie dann wieder los. Das Kontextmenü wird geöffnet, sobald Sie loslassen.
4.  Klicken Sie auf die Schaltfläche „Start“, und geben Sie den Namen der App ein, um sie zu suchen und zu starten.
