---
title: Installieren einer UWP-App von einem IIS-Server
description: In diesem Lernprogramm wird veranschaulicht, wie Sie einen IIS-Server einrichten, stellen Sie sicher, dass Ihre Web-app kann app-Pakete hosten und aufrufen und verwenden App-Installer effektiv.
ms.date: 05/30/2018
ms.topic: article
keywords: Windows 10, Uwp, app-Installer, AppInstaller, querladen, im Zusammenhang mit festgelegten optionale Pakete, IIS-Server
ms.localizationpriority: medium
ms.openlocfilehash: 6a4512229a29a7adc59d6b61edd596eaeb56a5a8
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8873308"
---
# <a name="install-a-uwp-app-from-an-iis-server"></a><span data-ttu-id="cefdb-104">Installieren einer UWP-App von einem IIS-Server</span><span class="sxs-lookup"><span data-stu-id="cefdb-104">Install a UWP app from an IIS server</span></span>

<span data-ttu-id="cefdb-105">In diesem Lernprogramm wird veranschaulicht, wie Sie einen IIS-Server einrichten, stellen Sie sicher, dass Ihre Web-app kann app-Pakete hosten und aufrufen und verwenden App-Installer effektiv.</span><span class="sxs-lookup"><span data-stu-id="cefdb-105">This tutorial demonstrates how to set up an IIS server, verify that your web app can host app packages, and invoke and use App Installer effectively.</span></span>

<span data-ttu-id="cefdb-106">Mit der App-Installer-App können Entwickler und IT-Spezialisten Windows10-Apps verteilen, indem sie diese in ihrem eigenen Content Delivery Network (CDN) hosten.</span><span class="sxs-lookup"><span data-stu-id="cefdb-106">The App Installer app allows developers and IT Pros to distribute Windows 10 apps by hosting them on their own Content Delivery Network (CDN).</span></span> <span data-ttu-id="cefdb-107">Das ist nützlich für Unternehmen, die ihre Apps nicht im Microsoft Store veröffentlichen möchten oder müssen, aber weiterhin die Windows10-Verpackungs- und -Bereitstellungsplattform nutzen möchten.</span><span class="sxs-lookup"><span data-stu-id="cefdb-107">This is useful for enterprises that don't want or need to publish their apps to the Microsoft Store, but still want to take advantage of the Windows 10 packaging and deployment platform.</span></span> 

## <a name="setup"></a><span data-ttu-id="cefdb-108">Setup</span><span class="sxs-lookup"><span data-stu-id="cefdb-108">Setup</span></span>

<span data-ttu-id="cefdb-109">Um erfolgreich mit diesem Lernprogramm durchlaufen, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="cefdb-109">To successfully go through with this tutorial, you will need the following:</span></span>

1. <span data-ttu-id="cefdb-110">VisualStudio2017</span><span class="sxs-lookup"><span data-stu-id="cefdb-110">Visual Studio 2017</span></span>  
2. <span data-ttu-id="cefdb-111">Web-Entwicklungstools und IIS</span><span class="sxs-lookup"><span data-stu-id="cefdb-111">Web development tools and IIS</span></span> 
3. <span data-ttu-id="cefdb-112">UWP-App-Paket – das App-Paket, die Sie verteilen möchten</span><span class="sxs-lookup"><span data-stu-id="cefdb-112">UWP app package - The app package that you will distribute</span></span>

<span data-ttu-id="cefdb-113">Optional: [Startprojekt](https://github.com/AppInstaller/MySampleWebApp) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="cefdb-113">Optional: [Starter Project](https://github.com/AppInstaller/MySampleWebApp) on GitHub.</span></span> <span data-ttu-id="cefdb-114">Dies ist hilfreich, wenn Sie keinen app-Pakete mit arbeiten, aber dennoch möchten erfahren, wie Sie dieses Feature verwenden.</span><span class="sxs-lookup"><span data-stu-id="cefdb-114">This is helpful if you don't have app packages to work with, but would still like to learn how to use this feature.</span></span>

## <a name="step-1---install-iis-and-aspnet"></a><span data-ttu-id="cefdb-115">Schritt 1: Installieren von IIS und ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cefdb-115">Step 1 - Install IIS and ASP.NET</span></span> 

<span data-ttu-id="cefdb-116">[Internet Information Services](https://www.iis.net/) ist ein Feature von Windows, die über das Menü "Start" installiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="cefdb-116">[Internet Information Services](https://www.iis.net/) is a Windows feature that can be installed via the Start menu.</span></span> <span data-ttu-id="cefdb-117">Im **Menü "Start"** Suchen nach **Windows-Funktionen ein- oder ausschalten**.</span><span class="sxs-lookup"><span data-stu-id="cefdb-117">In **Start menu** search for **Turn Windows features on or off**.</span></span>

<span data-ttu-id="cefdb-118">Suchen Sie und wählen Sie die **Internet Information Services** , IIS zu installieren.</span><span class="sxs-lookup"><span data-stu-id="cefdb-118">Find and select **Internet Information Services** to install IIS.</span></span>

> [!NOTE]
> <span data-ttu-id="cefdb-119">Sie müssen nicht alle Kontrollkästchen unter Internetinformationsdiensten wählen.</span><span class="sxs-lookup"><span data-stu-id="cefdb-119">You don't need to select all the check boxes under Internet Information Services.</span></span> <span data-ttu-id="cefdb-120">Nur diejenigen, die ausgewählt, wenn Sie überprüfen, dass **Internet Information Services** reichen.</span><span class="sxs-lookup"><span data-stu-id="cefdb-120">Only the ones selected when you check **Internet Information Services** are sufficient.</span></span>

<span data-ttu-id="cefdb-121">Sie müssen auch ASP.NET 4.5 oder höher installieren.</span><span class="sxs-lookup"><span data-stu-id="cefdb-121">You will also need to install ASP.NET 4.5 or greater.</span></span> <span data-ttu-id="cefdb-122">Um die Installation, suchen Sie nach **Internet Information Services-World Wide Web > -> Anwendungsentwicklungsfeatures**.</span><span class="sxs-lookup"><span data-stu-id="cefdb-122">To install it, locate **Internet Information Services -> World Wide Web Services -> Application Development Features**.</span></span> <span data-ttu-id="cefdb-123">Wählen Sie eine Version von ASP.NET, die größer als oder gleich ASP.NET 4.5 ist.</span><span class="sxs-lookup"><span data-stu-id="cefdb-123">Select a version of ASP.NET that is greater than or equal to ASP.NET 4.5.</span></span>

![Installieren von ASP.NET](images/install-asp.png)

## <a name="step-2---install-visual-studio-2017-and-web-development-tools"></a><span data-ttu-id="cefdb-125">Schritt 2: installieren Visual Studio 2017 und Webentwicklung-tools</span><span class="sxs-lookup"><span data-stu-id="cefdb-125">Step 2 - Install Visual Studio 2017 and Web Development tools</span></span> 

<span data-ttu-id="cefdb-126">[Installieren Sie Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio) , wenn Sie nicht bereits installiert haben.</span><span class="sxs-lookup"><span data-stu-id="cefdb-126">[Install Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio) if you have not already installed it.</span></span> <span data-ttu-id="cefdb-127">Wenn Sie bereits über Visual Studio 2017 haben, stellen Sie sicher, dass die folgenden Workloads installiert sind.</span><span class="sxs-lookup"><span data-stu-id="cefdb-127">If you already have Visual Studio 2017, ensure that the following workloads are installed.</span></span> <span data-ttu-id="cefdb-128">Wenn die Workloads nicht auf Ihre Installation vorhanden sind, führen Sie zusammen mit der Visual Studio Installer (aus dem Menü "Start" gefunden).</span><span class="sxs-lookup"><span data-stu-id="cefdb-128">If the workloads are not present on your installation, follow along using the Visual Studio Installer (found from the Start menu).</span></span>  

<span data-ttu-id="cefdb-129">Wählen Sie während der Installation **ASP.NET und -Entwicklung** und dass andere Workloads, denen Sie von Interesse sind.</span><span class="sxs-lookup"><span data-stu-id="cefdb-129">During installation, select **ASP.NET and Web development** and any other workloads that you are interested in.</span></span> 

<span data-ttu-id="cefdb-130">Nachdem die Installation abgeschlossen ist, starten Sie Visual Studio, und Erstellen eines neuen Projekts (**Datei** -> **Neues Projekt**).</span><span class="sxs-lookup"><span data-stu-id="cefdb-130">Once installation is complete, launch Visual Studio and create a new project (**File** -> **New Project**).</span></span>

## <a name="step-3---build-a-web-app"></a><span data-ttu-id="cefdb-131">Schritt 3: Erstellen einer Web-App</span><span class="sxs-lookup"><span data-stu-id="cefdb-131">Step 3 - Build a Web App</span></span>

<span data-ttu-id="cefdb-132">Starten Sie Visual Studio 2017 als **Administrator** , und erstellen Sie ein neues Projekt **Visual C#-Web-Anwendung** mit einer **leeren** Projektvorlage.</span><span class="sxs-lookup"><span data-stu-id="cefdb-132">Launch Visual Studio 2017 as **Administrator** and create a new **Visual C# Web Application** project with an **empty** project template.</span></span> 

![Neues Projekt](images/sample-web-app.png)

## <a name="step-4---configure-iis-with-our-web-app"></a><span data-ttu-id="cefdb-134">Schritt 4: Konfigurieren von IIS mit unseren Web-App</span><span class="sxs-lookup"><span data-stu-id="cefdb-134">Step 4 - Configure IIS with our Web App</span></span> 

<span data-ttu-id="cefdb-135">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Root-Projekt, und wählen Sie **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="cefdb-135">From the Solution Explorer, right click on the root project and select **Properties**.</span></span>

<span data-ttu-id="cefdb-136">Wählen Sie in der Web-app-Eigenschaften der Registerkarte " **Web** ". Wählen Sie im Abschnitt **Server** aus, **Lokale IIS** aus der Dropdown-Menü aus, und klicken Sie auf **Virtuellen Verzeichnis erstellen**.</span><span class="sxs-lookup"><span data-stu-id="cefdb-136">In the web app properties, select the **Web** tab. In the **Servers** section, choose **Local IIS** from the drop down menu and click **Create Virtual Directory**.</span></span> 

![Registerkarte Web](images/web-tab.png)

## <a name="step-5---add-an-app-package-to-a-web-application"></a><span data-ttu-id="cefdb-138">Schritt 5: Hinzufügen eines app-Pakets für eine Anwendung</span><span class="sxs-lookup"><span data-stu-id="cefdb-138">Step 5 - Add an app package to a web application</span></span> 

<span data-ttu-id="cefdb-139">Fügen Sie das app-Paket, das Sie in der Anwendung verteilen möchten.</span><span class="sxs-lookup"><span data-stu-id="cefdb-139">Add the app package that you are going to distribute into the web application.</span></span> <span data-ttu-id="cefdb-140">Sie können das app-Paket verwenden, das Teil der bereitgestellten [Starter Projektpakete](https://github.com/AppInstaller/MySampleWebApp/tree/master/MySampleWebApp/packages) auf GitHub ist, besitzen Sie ein app-Paket zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="cefdb-140">You can use the app package that is part of the provided [starter project packages](https://github.com/AppInstaller/MySampleWebApp/tree/master/MySampleWebApp/packages) on GitHub if you don't have an app package available.</span></span> <span data-ttu-id="cefdb-141">Die Zertifikat (MySampleApp.cer), mit dem das Paket signiert wurde, ist ebenfalls im Beispiel auf GitHub enthalten.</span><span class="sxs-lookup"><span data-stu-id="cefdb-141">The certificate (MySampleApp.cer) that the package was signed with is also with the sample on GitHub.</span></span> <span data-ttu-id="cefdb-142">Sie müssen das Zertifikat vor der Installation der app (Schritt 9) auf Ihrem Gerät installiert haben.</span><span class="sxs-lookup"><span data-stu-id="cefdb-142">You must have the certificate installed to your device prior to installing the app (Step 9).</span></span>

<span data-ttu-id="cefdb-143">Die Web-App mit Starter-Projekt ein neuer Ordner wurde die Web-app aufgerufen hinzugefügt `packages` , enthält die app-Pakete verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="cefdb-143">In the starter project web application, a new folder was added to the web app called `packages` that contains the app packages to be distributed.</span></span> <span data-ttu-id="cefdb-144">Um den Ordner in Visual Studio erstellen, klicken Sie mit der rechten Maustaste auf das Stammverzeichnis des im Projektmappen-Explorer, wählen Sie **Hinzufügen** -> **Neuen Ordner** und nennen Sie es `packages`.</span><span class="sxs-lookup"><span data-stu-id="cefdb-144">To create the folder in Visual Studio, right click on the root of the Solution Explorer, select **Add** -> **New Folder** and name it `packages`.</span></span> <span data-ttu-id="cefdb-145">Zum Hinzufügen von app-Pakete in den Ordner, klicken Sie mit der rechten Maustaste auf die `packages` Ordner, und wählen Sie **Hinzufügen** -> **Vorhandenes Element** und navigieren Sie zu der app-Pakets Speicherort.</span><span class="sxs-lookup"><span data-stu-id="cefdb-145">To add app packages to the folder, right click on the `packages` folder and select **Add** -> **Existing Item...** and browse to the app package location.</span></span> 

![Paket hinzufügen](images/add-package.png)

## <a name="step-6---create-a-web-page"></a><span data-ttu-id="cefdb-147">Schritt 6: Erstellen Sie eine Webseite</span><span class="sxs-lookup"><span data-stu-id="cefdb-147">Step 6 - Create a Web Page</span></span>

<span data-ttu-id="cefdb-148">Diese Beispiel-Web-app verwendet einfaches HTML.</span><span class="sxs-lookup"><span data-stu-id="cefdb-148">This sample web app uses simple HTML.</span></span> <span data-ttu-id="cefdb-149">Sie können Ihre Web-app nach Bedarf pro Ihren Anforderungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="cefdb-149">You are free to build your web app as required per your needs.</span></span> 

<span data-ttu-id="cefdb-150">Klicken Sie mit der rechten Maustaste auf das Stammprojekt der Projektmappen-Explorer, wählen Sie **Hinzufügen** -> **Neues Element**, und fügen Sie eine neue **HTML-Seite** aus dem **Web** -Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="cefdb-150">Right click on the root project of the Solution explorer, select **Add** -> **New Item**, and add a new **HTML Page** from the **Web** section.</span></span>

<span data-ttu-id="cefdb-151">Wenn die HTML-Seite erstellt wurde, klicken Sie mit der rechten Maustaste auf die HTML-Seite im Projektmappen-Explorer, und wählen Sie **Als Startseite festlegen**.</span><span class="sxs-lookup"><span data-stu-id="cefdb-151">Once the HTML page is created, right click on the HTML page in the Solution Explorer and select **Set As Start Page**.</span></span>  

<span data-ttu-id="cefdb-152">Doppelklicken Sie auf die HTML-Datei, um sie im Code-Editor-Fenster zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="cefdb-152">Double-click the HTML file to open it in the code editor window.</span></span> <span data-ttu-id="cefdb-153">In diesem Lernprogramm werden nur für die Elemente in der erforderlichen auf der Webseite zum Aufrufen der App-Installer-app erfolgreich zum Installieren von Windows 10-app verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cefdb-153">In this tutorial, only the elements in the required in the web page to invoke the App Installer app successfully to install a Windows 10 app will be used.</span></span> 

<span data-ttu-id="cefdb-154">Fügen Sie den folgenden HTML-Code in Ihrer Webseite.</span><span class="sxs-lookup"><span data-stu-id="cefdb-154">Include the following HTML code in your web page.</span></span> <span data-ttu-id="cefdb-155">Der Schlüssel zum Aufrufen von App-Installer erfolgreich ist, benutzerdefinierte Schema verwenden, die mit dem Betriebssystem App-Installer registriert: `ms-appinstaller:?source=`.</span><span class="sxs-lookup"><span data-stu-id="cefdb-155">The key to successfully invoking App Installer is to use the custom scheme that App Installer registers with the OS: `ms-appinstaller:?source=`.</span></span> <span data-ttu-id="cefdb-156">Siehe Codebeispiel unten für Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="cefdb-156">See the code example below for more details.</span></span>

> [!NOTE]
> <span data-ttu-id="cefdb-157">Stellen Sie sicher, dass den URL-Pfad angegeben wird, nachdem das benutzerdefinierte Schema die Projekt-Url in der Registerkarte "Web" VS-Lösung übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="cefdb-157">Ensure that the URL path specified after the custom scheme matches the Project Url in the web tab of your VS solution.</span></span>
 
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

## <a name="step-7---configure-the-web-app-for-app-package-mime-types"></a><span data-ttu-id="cefdb-158">Schritt 7: Konfigurieren der Web-app für app-Paket-MIME-Typen</span><span class="sxs-lookup"><span data-stu-id="cefdb-158">Step 7 - Configure the web app for app package MIME types</span></span>

<span data-ttu-id="cefdb-159">Öffnen Sie die **Datei "Web.config** " im Projektmappen-Explorer und fügen Sie die folgenden Zeilen in der `<configuration>` Element.</span><span class="sxs-lookup"><span data-stu-id="cefdb-159">Open the **Web.config** file from the solution explorer and add the following lines within the `<configuration>` element.</span></span> 

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

## <a name="step-8---add-loopback-exemption-for-app-installer"></a><span data-ttu-id="cefdb-160">Schritt 8: Hinzufügen von loopbackausnahme für App-Installer</span><span class="sxs-lookup"><span data-stu-id="cefdb-160">Step 8 - Add loopback exemption for App Installer</span></span>

<span data-ttu-id="cefdb-161">Aufgrund der Netzwerkisolation, sind UWP-apps, z. B. App-Installer beschränkt, mit der IP-Loopbackadressen wie http://localhost/.</span><span class="sxs-lookup"><span data-stu-id="cefdb-161">Due to network isolation, UWP apps like App Installer are restricted to use IP loopback addresses like http://localhost/.</span></span> <span data-ttu-id="cefdb-162">Bei Verwendung von lokalen IIS-Server muss die App-Installer der ausgenommene Loopback-Liste hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="cefdb-162">When using local IIS Server, App Installer must be added to the loopback exempt list.</span></span> 

<span data-ttu-id="cefdb-163">Zu diesem Zweck öffnen Sie die **Befehlszeile** als **Administrator** , und geben Sie Folgendes: ''' Befehlszeile CheckNetIsolation.exe LoopbackExempt - ein-n="microsoft.desktopappinstaller_8wekyb3d8bbwe"</span><span class="sxs-lookup"><span data-stu-id="cefdb-163">To do this, open **Command Prompt** as an **Administrator** and enter the following: \`\`\`Command Line CheckNetIsolation.exe LoopbackExempt -a -n="microsoft.desktopappinstaller_8wekyb3d8bbwe"</span></span>
```

To verify that the app is added to the exempt list, use the following command to display the apps in the loopback exempt list: 
```Command Line
CheckNetIsolation.exe LoopbackExempt -s
```

<span data-ttu-id="cefdb-164">Finden Sie `microsoft.desktopappinstaller_8wekyb3d8bbwe` in der Liste.</span><span class="sxs-lookup"><span data-stu-id="cefdb-164">You should find `microsoft.desktopappinstaller_8wekyb3d8bbwe` in the list.</span></span>

<span data-ttu-id="cefdb-165">Nachdem die lokale app-Installation über App-Installer-Überprüfung abgeschlossen ist, können Sie die loopbackausnahme entfernen, die Sie in diesem Schritt hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="cefdb-165">Once the local validation of app installation via App Installer is complete, you can remove the loopback exemption that you added in this step by:</span></span>

<span data-ttu-id="cefdb-166">' Befehlszeile CheckNetIsolation.exe LoopbackExempt -d-n="microsoft.desktopappinstaller_8wekyb3d8bbwe"</span><span class="sxs-lookup"><span data-stu-id="cefdb-166">\`\`\`Command Line CheckNetIsolation.exe LoopbackExempt -d -n="microsoft.desktopappinstaller_8wekyb3d8bbwe"</span></span>
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
