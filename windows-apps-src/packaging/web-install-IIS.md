---
author: laurenhughes
title: Installieren einer UWP-App von einem IIS-Server
description: In diesem Lernprogramm wird veranschaulicht, wie Sie einen IIS-Server einrichten, stellen Sie sicher, dass Ihre Web-app kann app-Pakete hosten und aufrufen und App-Installer effektiv verwenden.
ms.author: cdon
ms.date: 05/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, app-Installer, AppInstaller, querladen, im Zusammenhang mit festgelegten, optionale Pakete, IIS-Server
ms.localizationpriority: medium
ms.openlocfilehash: 214ddd2b55bca1acecbab0a841cf2048335e7b3a
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4750997"
---
# <a name="install-a-uwp-app-from-an-iis-server"></a>Installieren einer UWP-App von einem IIS-Server

In diesem Lernprogramm wird veranschaulicht, wie Sie einen IIS-Server einrichten, stellen Sie sicher, dass Ihre Web-app kann app-Pakete hosten und aufrufen und App-Installer effektiv verwenden.

Mit der App-Installer-App können Entwickler und IT-Spezialisten Windows10-Apps verteilen, indem sie diese in ihrem eigenen Content Delivery Network (CDN) hosten. Das ist nützlich für Unternehmen, die ihre Apps nicht im Microsoft Store veröffentlichen möchten oder müssen, aber weiterhin die Windows10-Verpackungs- und -Bereitstellungsplattform nutzen möchten. 

## <a name="setup"></a>Setup

Um erfolgreich mit diesem Lernprogramm durchlaufen, benötigen Sie Folgendes:

1. VisualStudio2017  
2. Web-Entwicklungstools und IIS 
3. UWP-App-Paket – das App-Paket, die Sie verteilen möchten

Optional: [Startprojekt](https://github.com/AppInstaller/MySampleWebApp) auf GitHub. Dies ist hilfreich, wenn Sie keinen app-Pakete mit arbeiten, aber dennoch möchten erfahren, wie Sie dieses Feature verwenden.

## <a name="step-1---install-iis-and-aspnet"></a>Schritt 1: Installieren von IIS und ASP.NET 

[Internet Information Services](https://www.iis.net/) ist ein Feature von Windows, die über das Menü "Start" installiert werden kann. Im **Menü "Start"** Suchen nach **Windows-Funktionen ein- oder ausschalten**.

Suchen Sie und wählen Sie **Internet Information Services** , IIS zu installieren.

> [!NOTE]
> Sie müssen nicht alle Kontrollkästchen unter Internet Information Services wählen. Nur diejenigen, die ausgewählt, wenn Sie überprüfen, dass **Internet Information Services** reichen.

Sie müssen auch ASP.NET 4.5 oder höher installieren. Um die Installation, suchen Sie nach **Internet Information Services -> World Wide Web Services -> Anwendungsentwicklungsfeatures**. Wählen Sie eine Version von ASP.NET, die größer als oder gleich ASP.NET 4.5 ist.

![Installieren von ASP.NET](images/install-asp.png)

## <a name="step-2---install-visual-studio-2017-and-web-development-tools"></a>Schritt 2: installieren Visual Studio 2017 und Webentwicklung-tools 

[Installieren Sie Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio) , wenn Sie nicht bereits installiert haben. Wenn Sie Visual Studio 2017 noch, stellen Sie sicher, dass die folgenden Workloads installiert sind. Wenn die Workloads nicht auf Ihre Installation vorhanden sind, führen Sie entlang mit dem Visual Studio Installer (finden Sie im Menü "Start").  

Wählen Sie während der Installation **ASP.NET und Webentwicklung** und dass andere Workloads, denen Sie von Interesse sind. 

Sobald die Installation abgeschlossen ist, starten Sie Visual Studio, und Erstellen eines neuen Projekts (**Datei** -> **Neues Projekt**).

## <a name="step-3---build-a-web-app"></a>Schritt 3: Erstellen einer Web-App

Starten Sie Visual Studio 2017 als **Administrator** , und erstellen Sie ein neues Projekt **Visual C#-Web-Anwendung** mit einer **leeren** Projektvorlage "". 

![Neues Projekt](images/sample-web-app.png)

## <a name="step-4---configure-iis-with-our-web-app"></a>Schritt 4: Konfigurieren von IIS mit unseren Web-App 

Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Root-Projekt, und wählen Sie **Eigenschaften**.

Wählen Sie in der Web-app-Eigenschaften der Registerkarte " **Web** ". Wählen Sie im Abschnitt **Server** aus, **Lokale IIS** aus der Dropdown-Menü ", und klicken Sie auf **Virtuellen Verzeichnis erstellen**. 

![Registerkarte "Web"](images/web-tab.png)

## <a name="step-5---add-an-app-package-to-a-web-application"></a>Schritt 5: Hinzufügen eines app-Pakets zu einer Web-Anwendung 

Fügen Sie das app-Paket, das Sie in der Anwendung verteilen möchten. Sie können das app-Paket verwenden, das Teil der bereitgestellten [Starter Projektpakete](https://github.com/AppInstaller/MySampleWebApp/tree/master/MySampleWebApp/packages) auf GitHub ist, besitzen Sie ein app-Paket zur Verfügung. Die Zertifikat (MySampleApp.cer), mit dem das Paket signiert wurde, ist ebenfalls im Beispiel auf GitHub enthalten. Sie müssen das Zertifikat vor der Installation der app (Schritt 9) auf Ihrem Gerät installiert haben.

In die Web-App mit Starter-Projekt ein neuer Ordner namens Web-app hinzugefügt wurde `packages` , enthält die app-Pakete verteilt werden soll. Um den Ordner "in Visual Studio erstellen, klicken Sie mit der rechten Maustaste auf das Stammverzeichnis des Projektmappen-Explorer, wählen Sie **Hinzufügen** -> **Neuen Ordner** und nennen Sie es `packages`. Zum Hinzufügen von app-Pakete in den Ordner, klicken Sie mit der rechten Maustaste auf die `packages` Ordner und **Hinzufügen** -> **Vorhandenes Element** und navigieren Sie zu der app-Pakets Speicherort. 

![Paket hinzufügen](images/add-package.png)

## <a name="step-6---create-a-web-page"></a>Schritt 6: Erstellen einer Webseite

Diese Beispiel-Web-app unter Verwendung von einfachen HTML. Sie können Ihre Web-app nach Bedarf pro Ihren Anforderungen erstellen. 

Klicken Sie mit der rechten Maustaste auf das Stammprojekt der Projektmappen-Explorer, wählen Sie **Hinzufügen** -> **Neues Element**, und fügen Sie eine neue **HTML-Seite** aus dem **Web** -Abschnitt.

Wenn die HTML-Seite erstellt wurde, klicken Sie mit der rechten Maustaste auf die HTML-Seite im Projektmappen-Explorer, und wählen Sie **Als Startseite festlegen**.  

Doppelklicken Sie auf die HTML-Datei, um sie im Code-Editor-Fenster zu öffnen. In diesem Lernprogramm werden nur für die Elemente im erforderlichen auf der Webseite zum Aufrufen der App-Installer-app erfolgreich zum Installieren von Windows 10-app verwendet werden. 

Fügen Sie den folgenden HTML-Code in Ihrer Webseite. Die Taste, um erfolgreich Aufrufen von App-Installer ist die Verwendung von benutzerdefinierten Schema, die App-Installer mit dem Betriebssystem registriert: `ms-appinstaller:?source=`. Siehe Codebeispiel unten für weitere Details.

> [!NOTE]
> Stellen Sie sicher, dass die URL-Pfad angegeben, nachdem das benutzerdefinierte Schema die Projekt-Url in der Registerkarte "Web" die VS-Projektmappe übereinstimmt.
 
```HTML
<html>
<head>
    <meta charset="utf-8" />
    <title> Install Page </title>
</head>
<body>
    <a href="ms-appinstaller:?source=http://localhost/SampleWebApp/packages/MySampleApp.appxbundle"> Install My Sample App</a>
</body>
</html>
```

## <a name="step-7---configure-the-web-app-for-app-package-mime-types"></a>Schritt 7: Konfigurieren der Web-app für app-Paket-MIME-Typen

Öffnen Sie die **Datei "Web.config** " im Projektmappen-Explorer und fügen Sie die folgenden Zeilen in der `<configuration>` Element. 

```xml
<system.webServer>
    <!--This is to allow the web server to serve resources with the appropriate file extension-->
    <staticContent>
      <mimeMap fileExtension=".appx" mimeType="application/appx" />
      <mimeMap fileExtension=".msix" mimeType="application/msix" />
      <mimeMap fileExtension=".appxbundle" mimeType="application/appxbundle" />
      <mimeMap fileExtension=".msixbundle" mimeType="application/msixbundle" />
      <mimeMap fileExtension=".appinstaller" mimeType="application/appinstaller" />
    </staticContent>
</system.webServer>
```

## <a name="step-8---add-loopback-exemption-for-app-installer"></a>Schritt 8: Hinzufügen von loopbackausnahme für App-Installer

Aufgrund der Netzwerkisolation sind UWP-apps, z. B. App-Installer beschränkt IP-Loopbackadressen wie verwenden http://localhost/. Bei Verwendung von lokalen IIS-Server muss der App-Installer der ausgenommene Loopback-Liste hinzugefügt werden. 

Zu diesem Zweck öffnen Sie die **Befehlszeile** als **Administrator** , und geben Sie Folgendes: ''' Befehlszeile CheckNetIsolation.exe LoopbackExempt - a-n=microsoft.desktopappinstaller_8wekyb3d8bbwe
```

To verify that the app is added to the exempt list, use the following command to display the apps in the loopback exempt list: 
```Command Line
CheckNetIsolation.exe LoopbackExempt -s
```

Finden Sie `microsoft.desktopappinstaller_8wekyb3d8bbwe` in der Liste.

Sobald die lokale Überprüfung des app-Installation über App-Installer abgeschlossen ist, können Sie die loopbackausnahme entfernen, die Sie in diesem Schritt hinzugefügt:

''' Befehlszeile CheckNetIsolation.exe LoopbackExempt -d-n=microsoft.desktopappinstaller_8wekyb3d8bbwe
```

## Step 9 - Run the Web App 

Build and run the web application by clicking on the run button on the VS Ribbon as shown in the image below:

![run](images/run.png)

A web page will open in your browser:

![web page](images/web-page.png)

Click on the link in the web page to launch the App Installer app and install your Windows 10 app package.


## Troubleshooting issues

### Not sufficient privilege 

If running the web app in Visual Studio displays an error such as "You do not have sufficient privilege to access IIS web sites on your machine", you will need to run Visual Studio as an administrator. Close the current instance of Visual Studio and reopen it as an admin.

### Set start page 

If running the web app causes the browser to load with an HTTP 403.14 - Forbidden error, it's because the web app doesn't have a defined start page. Refer to Step 6 in this tutorial to learn how to define a start page.
