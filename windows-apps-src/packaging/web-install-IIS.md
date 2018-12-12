---
title: Installieren einer UWP-App von einem IIS-Server
description: In diesem Lernprogramm wird veranschaulicht, wie Sie einen IIS-Server einrichten, stellen Sie sicher, dass Ihre Web-app kann app-Pakete hosten und aufrufen und verwenden App-Installer effektiv.
ms.date: 05/30/2018
ms.topic: article
keywords: Windows 10, Uwp, app-Installer, AppInstaller, querladen, im Zusammenhang mit festgelegten optionale Pakete, IIS-Server
ms.localizationpriority: medium
ms.openlocfilehash: 6a4512229a29a7adc59d6b61edd596eaeb56a5a8
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8932106"
---
# <a name="install-a-uwp-app-from-an-iis-server"></a>Installieren einer UWP-App von einem IIS-Server

In diesem Lernprogramm wird veranschaulicht, wie Sie einen IIS-Server einrichten, stellen Sie sicher, dass Ihre Web-app kann app-Pakete hosten und aufrufen und verwenden App-Installer effektiv.

Mit der App-Installer-App können Entwickler und IT-Spezialisten Windows10-Apps verteilen, indem sie diese in ihrem eigenen Content Delivery Network (CDN) hosten. Das ist nützlich für Unternehmen, die ihre Apps nicht im Microsoft Store veröffentlichen möchten oder müssen, aber weiterhin die Windows10-Verpackungs- und -Bereitstellungsplattform nutzen möchten. 

## <a name="setup"></a>Setup

Um erfolgreich mit diesem Lernprogramm durchlaufen, benötigen Sie Folgendes:

1. VisualStudio2017  
2. Web-Entwicklungstools und IIS 
3. UWP-App-Paket – das App-Paket, die Sie verteilen möchten

Optional: [Startprojekt](https://github.com/AppInstaller/MySampleWebApp) auf GitHub. Dies ist hilfreich, wenn Sie keinen app-Pakete mit arbeiten, aber dennoch möchten erfahren, wie Sie dieses Feature verwenden.

## <a name="step-1---install-iis-and-aspnet"></a>Schritt 1: Installieren von IIS und ASP.NET 

[Internet Information Services](https://www.iis.net/) ist ein Feature von Windows, die über das Menü "Start" installiert werden kann. Im **Menü "Start"** Suchen nach **Windows-Funktionen ein- oder ausschalten**.

Suchen Sie und wählen Sie die **Internet Information Services** , IIS zu installieren.

> [!NOTE]
> Sie müssen nicht alle Kontrollkästchen unter Internetinformationsdiensten wählen. Nur diejenigen, die ausgewählt, wenn Sie überprüfen, dass **Internet Information Services** reichen.

Sie müssen auch ASP.NET 4.5 oder höher installieren. Um die Installation, suchen Sie nach **Internet Information Services-World Wide Web > -> Anwendungsentwicklungsfeatures**. Wählen Sie eine Version von ASP.NET, die größer als oder gleich ASP.NET 4.5 ist.

![Installieren von ASP.NET](images/install-asp.png)

## <a name="step-2---install-visual-studio-2017-and-web-development-tools"></a>Schritt 2: installieren Visual Studio 2017 und Webentwicklung-tools 

[Installieren Sie Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio) , wenn Sie nicht bereits installiert haben. Wenn Sie bereits über Visual Studio 2017 haben, stellen Sie sicher, dass die folgenden Workloads installiert sind. Wenn die Workloads nicht auf Ihre Installation vorhanden sind, führen Sie zusammen mit der Visual Studio Installer (aus dem Menü "Start" gefunden).  

Wählen Sie während der Installation **ASP.NET und -Entwicklung** und dass andere Workloads, denen Sie von Interesse sind. 

Nachdem die Installation abgeschlossen ist, starten Sie Visual Studio, und Erstellen eines neuen Projekts (**Datei** -> **Neues Projekt**).

## <a name="step-3---build-a-web-app"></a>Schritt 3: Erstellen einer Web-App

Starten Sie Visual Studio 2017 als **Administrator** , und erstellen Sie ein neues Projekt **Visual C#-Web-Anwendung** mit einer **leeren** Projektvorlage. 

![Neues Projekt](images/sample-web-app.png)

## <a name="step-4---configure-iis-with-our-web-app"></a>Schritt 4: Konfigurieren von IIS mit unseren Web-App 

Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Root-Projekt, und wählen Sie **Eigenschaften**.

Wählen Sie in der Web-app-Eigenschaften der Registerkarte " **Web** ". Wählen Sie im Abschnitt **Server** aus, **Lokale IIS** aus der Dropdown-Menü aus, und klicken Sie auf **Virtuellen Verzeichnis erstellen**. 

![Registerkarte Web](images/web-tab.png)

## <a name="step-5---add-an-app-package-to-a-web-application"></a>Schritt 5: Hinzufügen eines app-Pakets für eine Anwendung 

Fügen Sie das app-Paket, das Sie in der Anwendung verteilen möchten. Sie können das app-Paket verwenden, das Teil der bereitgestellten [Starter Projektpakete](https://github.com/AppInstaller/MySampleWebApp/tree/master/MySampleWebApp/packages) auf GitHub ist, besitzen Sie ein app-Paket zur Verfügung. Die Zertifikat (MySampleApp.cer), mit dem das Paket signiert wurde, ist ebenfalls im Beispiel auf GitHub enthalten. Sie müssen das Zertifikat vor der Installation der app (Schritt 9) auf Ihrem Gerät installiert haben.

Die Web-App mit Starter-Projekt ein neuer Ordner wurde die Web-app aufgerufen hinzugefügt `packages` , enthält die app-Pakete verteilt werden. Um den Ordner in Visual Studio erstellen, klicken Sie mit der rechten Maustaste auf das Stammverzeichnis des im Projektmappen-Explorer, wählen Sie **Hinzufügen** -> **Neuen Ordner** und nennen Sie es `packages`. Zum Hinzufügen von app-Pakete in den Ordner, klicken Sie mit der rechten Maustaste auf die `packages` Ordner, und wählen Sie **Hinzufügen** -> **Vorhandenes Element** und navigieren Sie zu der app-Pakets Speicherort. 

![Paket hinzufügen](images/add-package.png)

## <a name="step-6---create-a-web-page"></a>Schritt 6: Erstellen Sie eine Webseite

Diese Beispiel-Web-app verwendet einfaches HTML. Sie können Ihre Web-app nach Bedarf pro Ihren Anforderungen erstellen. 

Klicken Sie mit der rechten Maustaste auf das Stammprojekt der Projektmappen-Explorer, wählen Sie **Hinzufügen** -> **Neues Element**, und fügen Sie eine neue **HTML-Seite** aus dem **Web** -Abschnitt.

Wenn die HTML-Seite erstellt wurde, klicken Sie mit der rechten Maustaste auf die HTML-Seite im Projektmappen-Explorer, und wählen Sie **Als Startseite festlegen**.  

Doppelklicken Sie auf die HTML-Datei, um sie im Code-Editor-Fenster zu öffnen. In diesem Lernprogramm werden nur für die Elemente in der erforderlichen auf der Webseite zum Aufrufen der App-Installer-app erfolgreich zum Installieren von Windows 10-app verwendet werden. 

Fügen Sie den folgenden HTML-Code in Ihrer Webseite. Der Schlüssel zum Aufrufen von App-Installer erfolgreich ist, benutzerdefinierte Schema verwenden, die mit dem Betriebssystem App-Installer registriert: `ms-appinstaller:?source=`. Siehe Codebeispiel unten für Weitere Informationen.

> [!NOTE]
> Stellen Sie sicher, dass den URL-Pfad angegeben wird, nachdem das benutzerdefinierte Schema die Projekt-Url in der Registerkarte "Web" VS-Lösung übereinstimmt.
 
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

Aufgrund der Netzwerkisolation, sind UWP-apps, z. B. App-Installer beschränkt, mit der IP-Loopbackadressen wie http://localhost/. Bei Verwendung von lokalen IIS-Server muss die App-Installer der ausgenommene Loopback-Liste hinzugefügt werden. 

Zu diesem Zweck öffnen Sie die **Befehlszeile** als **Administrator** , und geben Sie Folgendes: ''' Befehlszeile CheckNetIsolation.exe LoopbackExempt - ein-n="microsoft.desktopappinstaller_8wekyb3d8bbwe"
```

To verify that the app is added to the exempt list, use the following command to display the apps in the loopback exempt list: 
```Command Line
CheckNetIsolation.exe LoopbackExempt -s
```

Finden Sie `microsoft.desktopappinstaller_8wekyb3d8bbwe` in der Liste.

Nachdem die lokale app-Installation über App-Installer-Überprüfung abgeschlossen ist, können Sie die loopbackausnahme entfernen, die Sie in diesem Schritt hinzugefügt:

' Befehlszeile CheckNetIsolation.exe LoopbackExempt -d-n="microsoft.desktopappinstaller_8wekyb3d8bbwe"
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
