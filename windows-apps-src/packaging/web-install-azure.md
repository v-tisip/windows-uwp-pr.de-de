---
title: Installation einer UWP-App von einem Azure-Webserver
description: In diesem Lernprogramm wird gezeigt, wie Sie einen Azure-Webserver einrichten, überprüfen, ob Ihre Web-App kann App-Pakete hosten kann, und App-Installer auf effektive Weise aufrufen und verwenden.
ms.date: 11/30/2018
ms.topic: article
keywords: Windows10, UWP, App-Installer, AppInstaller, querladen, zusammengehörig, optionale Pakete, Azure-Webserver
ms.localizationpriority: medium
ms.openlocfilehash: 074a8e9941d4314bb35c28b0ee296e9d86fa23a5
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8896726"
---
# <a name="install-a-uwp-app-from-an-azure-web-app"></a><span data-ttu-id="d54d3-104">Installieren einer UWP-App aus einer Azure-Web-App</span><span class="sxs-lookup"><span data-stu-id="d54d3-104">Install a UWP app from an Azure Web App</span></span>

<span data-ttu-id="d54d3-105">Mit der App-Installer-App können Entwickler und IT-Spezialisten Windows10-Apps verteilen, indem sie diese in ihrem eigenen Content Delivery Network (CDN) hosten.</span><span class="sxs-lookup"><span data-stu-id="d54d3-105">The App Installer app allows developers and IT Pros to distribute Windows 10 apps by hosting them on their own Content Delivery Network (CDN).</span></span> <span data-ttu-id="d54d3-106">Das ist nützlich für Unternehmen, die ihre Apps nicht im Microsoft Store veröffentlichen möchten oder müssen, aber weiterhin die Windows10-Verpackungs- und -Bereitstellungsplattform nutzen möchten.</span><span class="sxs-lookup"><span data-stu-id="d54d3-106">This is useful for enterprises that don't want or need to publish their apps to the Microsoft Store, but still want to take advantage of the Windows 10 packaging and deployment platform.</span></span>

<span data-ttu-id="d54d3-107">In diesem Thema sind die Schritte zum Konfigurieren eines Azure-Webservers zum Hosten von UWP-App-Paketen aufgeführt, und Sie erfahren, wie Sie die App-Installer-App verwenden, um die App-Pakete zu installieren.</span><span class="sxs-lookup"><span data-stu-id="d54d3-107">This topic outlines the steps to configure an Azure Web Server to host UWP app packages, and how to use the App Installer app to install the app packages.</span></span>

## <a name="setup"></a><span data-ttu-id="d54d3-108">Setup</span><span class="sxs-lookup"><span data-stu-id="d54d3-108">Setup</span></span>

<span data-ttu-id="d54d3-109">Für eine erfolgreiche Durchführung dieses Lernprogramms benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="d54d3-109">To successfully follow this tutorial, you will need the following:</span></span>
 
1. <span data-ttu-id="d54d3-110">Microsoft Azure-Abonnement</span><span class="sxs-lookup"><span data-stu-id="d54d3-110">Microsoft Azure subscription</span></span> 
2. <span data-ttu-id="d54d3-111">UWP-App-Paket – das App-Paket, die Sie verteilen möchten</span><span class="sxs-lookup"><span data-stu-id="d54d3-111">UWP app package - The app package that you will distribute</span></span>

<span data-ttu-id="d54d3-112">Optional: [Startprojekt](https://github.com/AppInstaller/MySampleWebApp) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="d54d3-112">Optional: [Starter Project](https://github.com/AppInstaller/MySampleWebApp) on GitHub.</span></span> <span data-ttu-id="d54d3-113">Dies ist hilfreich, wenn Sie kein App-Paket oder keine Webseite zum Arbeiten verfügbar haben, aber dennoch lernen möchten, wie Sie dieses Feature verwenden.</span><span class="sxs-lookup"><span data-stu-id="d54d3-113">This is helpful if you don't an app package or web page to work with, but would still like to learn how to use this feature.</span></span>

### <a name="step-1---get-an-azure-subscription"></a><span data-ttu-id="d54d3-114">Schritt1: Erwerben eines Azure-Abonnements</span><span class="sxs-lookup"><span data-stu-id="d54d3-114">Step 1 - Get an Azure subscription</span></span>
<span data-ttu-id="d54d3-115">Informationen zum Erwerben eines Azure-Abonnements finden Sie auf der [Azure Kontoseite](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="d54d3-115">To get an Azure subscription, visit the [Azure account page](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="d54d3-116">Für die Zwecke dieses Lernprogramms können Sie eine kostenlose Mitgliedschaft verwenden.</span><span class="sxs-lookup"><span data-stu-id="d54d3-116">For the purposes of this tutorial, you can use a free membership.</span></span>

### <a name="step-2---create-an-azure-web-app"></a><span data-ttu-id="d54d3-117">Schritt2: Erstellen einer Azure-Web-App</span><span class="sxs-lookup"><span data-stu-id="d54d3-117">Step 2 - Create an Azure Web App</span></span> 
<span data-ttu-id="d54d3-118">Klicken Sie auf der Azure-Portalseite auf die Schaltfläche **+ Ressource erstellen**, und wählen Sie dann **Web-App** aus.</span><span class="sxs-lookup"><span data-stu-id="d54d3-118">In the Azure portal page, click the **+ Create a Resource** button and then select **Web App**</span></span>

![erstellen](images/azure-create-app.png)

<span data-ttu-id="d54d3-120">Erstellen Sie einen eindeutigen **App-Namen**, und behalten Sie für die restlichen Felder die Standardwerte bei.</span><span class="sxs-lookup"><span data-stu-id="d54d3-120">Create a unique **App name** and leave the rest of the fields as default.</span></span> <span data-ttu-id="d54d3-121">Klicken Sie auf **Erstellen**, um den Assistenten zum Erstellen von Web-Apps abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="d54d3-121">Click **Create** to finish the Web App creation wizard.</span></span> 

![Erstellen einer Web-App](images/azure-create-app-2.png)

### <a name="step-3---hosting-the-app-package-and-the-web-page"></a><span data-ttu-id="d54d3-123">Schritt3: Hosten des App-Pakets und der Webseite</span><span class="sxs-lookup"><span data-stu-id="d54d3-123">Step 3 - Hosting the app package and the web page</span></span> 
<span data-ttu-id="d54d3-124">Nach die Web-App erstellt wurde, können Sie über das Dashboard im Azure-Portal darauf zugreifen.</span><span class="sxs-lookup"><span data-stu-id="d54d3-124">Once the web app had been created, you can access it from the dashboard on the Azure portal.</span></span> <span data-ttu-id="d54d3-125">In diesem Schritt werden wir eine einfache Webseite mit der GUI des Azure-Portals erstellen.</span><span class="sxs-lookup"><span data-stu-id="d54d3-125">In this step, we're going to create a simple web page with the GUI of the Azure portal.</span></span>

<span data-ttu-id="d54d3-126">Nach Auswahl der neu erstellten Web-App über das Dashboard, verwenden Sie das Suchfeld, um nach dem **App-Dienst-Editor** zu suchen und ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d54d3-126">After selecting the newly created web app from the dashboard, use the search field to find and open **App Service Editor**.</span></span> 

<span data-ttu-id="d54d3-127">Im Editor gibt es eine standardmäßige `hostingstart.html`-Datei.</span><span class="sxs-lookup"><span data-stu-id="d54d3-127">In the editor, there is a default `hostingstart.html` file.</span></span> <span data-ttu-id="d54d3-128">Klicken Sie mit der rechten Maustaste in den leeren Bereich des Datei-Explorer-Panels, und wählen Sie **Dateien hochladen** aus, um das Hochladen Ihrer App-Pakete zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="d54d3-128">Right-click in the empty space of file explorer panel and select **Upload Files** to begin uploading your app packages.</span></span>

> [!NOTE]
> <span data-ttu-id="d54d3-129">Sie können das App-Paket verwenden, das Teil des bereitgestellten [Startprojekt](https://github.com/AppInstaller/MySampleWebApp)-Repositorys auf GitHub ist, falls Ihnen kein App-Paket zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="d54d3-129">You can use the app package that is part of the provided [Starter Project](https://github.com/AppInstaller/MySampleWebApp) repository on GitHub if you don't have an app package available.</span></span> <span data-ttu-id="d54d3-130">Die Zertifikat (MySampleApp.cer), mit dem das Paket signiert wurde, ist ebenfalls im Beispiel auf GitHub enthalten.</span><span class="sxs-lookup"><span data-stu-id="d54d3-130">The certificate (MySampleApp.cer) that the package was signed with is also with the sample on GitHub.</span></span> <span data-ttu-id="d54d3-131">Sie müssen das Zertifikat vor der Installation der App auf Ihrem Gerät installieren.</span><span class="sxs-lookup"><span data-stu-id="d54d3-131">You must have the certificate installed to your device prior to installing the app.</span></span>

![Upload](images/azure-upload-file.png)

<span data-ttu-id="d54d3-133">Klicken Sie mit der rechten Maustaste in den leeren Bereich des Datei-Explorer-Panels, und wählen Sie **Neue Dateien** aus, um eine neue Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d54d3-133">Right-click in the empty space of file explorer panel and select **New Files** to create a new file.</span></span> <span data-ttu-id="d54d3-134">Geben Sie der Datei den Namen: `default.html`.</span><span class="sxs-lookup"><span data-stu-id="d54d3-134">Name the file: `default.html`.</span></span>

<span data-ttu-id="d54d3-135">Wenn Sie das im [Startprojekt](https://github.com/AppInstaller/MySampleWebApp) bereitgestellte App-Paket verwenden, kopieren Sie den folgenden HTML-Code in die neu erstellte Webseite `default.html`.</span><span class="sxs-lookup"><span data-stu-id="d54d3-135">If you're using the app package provided in the [Starter Project](https://github.com/AppInstaller/MySampleWebApp), copy the following HTML code to the newly create web page `default.html`.</span></span> <span data-ttu-id="d54d3-136">Wenn Sie ein eigenes App-Paket verwenden, ändern Sie die App-Dienst-URL (die URL nach `source=`).</span><span class="sxs-lookup"><span data-stu-id="d54d3-136">If you're using your own app package, modify the app service URL (the URL after `source=`).</span></span> <span data-ttu-id="d54d3-137">Sie können die App-Dienst-URL von der Übersichtsseite Ihrer App im Azure-Portal abrufen.</span><span class="sxs-lookup"><span data-stu-id="d54d3-137">You can get the app service URL from your app's overview page in the Azure portal.</span></span>

```html
<html>
<head>
    <meta charset="utf-8" />
    <title> Install My Sample App</title>
</head>
<body>
    <a href="ms-appinstaller:?source=https://appinstaller-azure-demo.azurewebsites.net/MySampleApp.appxbundle"> Install My Sample App</a>
</body>
</html>
```

### <a name="step-4---configure-the-web-app-for-app-package-mime-types"></a><span data-ttu-id="d54d3-138">Schritt4: Konfigurieren der Web-App für App-Paket-MIME-Typen</span><span class="sxs-lookup"><span data-stu-id="d54d3-138">Step 4 - Configure the web app for app package MIME types</span></span>

<span data-ttu-id="d54d3-139">Fügen Sie der Web-App eine neue Datei mit dem folgenden Namen hinzu: `Web.config`.</span><span class="sxs-lookup"><span data-stu-id="d54d3-139">Add a new file to the web app named: `Web.config`.</span></span> <span data-ttu-id="d54d3-140">Öffnen Sie die Datei `Web.config` im Explorer, und fügen Sie die folgenden Zeilen hinzu.</span><span class="sxs-lookup"><span data-stu-id="d54d3-140">Open the `Web.config` file from the explorer and add the following lines.</span></span> 

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
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
</configuration>
```

### <a name="step-5---run-and-test"></a><span data-ttu-id="d54d3-141">Schritt5: Ausführen und Testen</span><span class="sxs-lookup"><span data-stu-id="d54d3-141">Step 5 - Run and test</span></span>

<span data-ttu-id="d54d3-142">Um die von Ihnen erstellte Webseite zu starten, geben die URL aus Schritt3 in den Browser ein, gefolgt von `/default.html`.</span><span class="sxs-lookup"><span data-stu-id="d54d3-142">To launch the web page that you created, use the URL from step 3 into the browser followed by `/default.html`.</span></span> 

![Edge](images/edge.png)

<span data-ttu-id="d54d3-144">Klicken Sie auf „Meine Beispiel-App installieren“, um App-Installer zu starten und Ihr App-Paket zu installieren.</span><span class="sxs-lookup"><span data-stu-id="d54d3-144">Click "Install My Sample App" to launch App Installer and install your app package.</span></span> 

## <a name="troubleshooting-issues"></a><span data-ttu-id="d54d3-145">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="d54d3-145">Troubleshooting Issues</span></span>

### <a name="app-installer-app-fails-to-install"></a><span data-ttu-id="d54d3-146">Fehler bei der Installation der App-Installer-App</span><span class="sxs-lookup"><span data-stu-id="d54d3-146">App Installer app fails to install</span></span> 
<span data-ttu-id="d54d3-147">Die App-Installation schlägt fehl, wenn das Zertifikat, mit dem das App-Paket signiert ist, nicht auf dem Gerät installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d54d3-147">App install will fail if the certificate that the app package is signed with isn't installed on the device.</span></span> <span data-ttu-id="d54d3-148">Um dieses Problem zu beheben, müssen Sie das Zertifikat vor der Installation der App installieren.</span><span class="sxs-lookup"><span data-stu-id="d54d3-148">To fix this, you will need to install the certificate prior to the installation of the app.</span></span> <span data-ttu-id="d54d3-149">Wenn Sie ein App-Paket für die öffentliche Verteilung hosten, wird empfohlen, das App-Paket mit einem Zertifikat von einer Zertifizierungsstelle zu signieren.</span><span class="sxs-lookup"><span data-stu-id="d54d3-149">If you are hosting an app package for public distribution, we recommended signing your app package with a certificate from a certificate authority.</span></span> 

![App-Zertifikat](images/aws-app-cert.png)

### <a name="nothing-happens-when-you-click-the-link"></a><span data-ttu-id="d54d3-151">Beim Klicken auf den Link geschieht nichts</span><span class="sxs-lookup"><span data-stu-id="d54d3-151">Nothing happens when you click the link</span></span> 
<span data-ttu-id="d54d3-152">Stellen Sie sicher, dass die App-Installer-App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d54d3-152">Ensure that the App Installer app is installed.</span></span> <span data-ttu-id="d54d3-153">Wechseln Sie zu **Einstellungen** -> **Apps und Features**, und suchen Sie in der Liste der installierten Apps nach App-Installer.</span><span class="sxs-lookup"><span data-stu-id="d54d3-153">Go to **Settings** -> **Apps & Features** and find App Installer in the installed apps list.</span></span> 

