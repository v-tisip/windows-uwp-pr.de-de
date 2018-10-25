---
author: ridomin
title: Erstellen einer App-Installer-Datei mit Visual Studio
description: Hier erfahren Sie, wie Sie Visual Studio verwenden, um automatische Updates mithilfe der .appinstaller-Datei zu aktivieren.
ms.author: rmpablos
ms.date: 5/2/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, app-installer, AppInstaller, querladen
ms.localizationpriority: medium
ms.openlocfilehash: 6158b804e1d4ece3c76099a3f8d33d5fa562078d
ms.sourcegitcommit: 2c4daa36fb9fd3e8daa83c2bd0825f3989d24be8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5517350"
---
# <a name="create-an-app-installer-file-with-visual-studio"></a><span data-ttu-id="a86dd-104">Erstellen einer App-Installer-Datei mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a86dd-104">Create an App Installer file with Visual Studio</span></span>

<span data-ttu-id="a86dd-105">Ab Windows10, Version 1804 und Visual Studio2017, Update 15.7, können quergeladene Apps so konfiguriert werden, dass sie mithilfe einer `.appinstaller`-Datei automatische Updates erhalten.</span><span class="sxs-lookup"><span data-stu-id="a86dd-105">Starting with Windows 10, Version 1804, and Visual Studio 2017, Update 15.7, sideloaded apps can be configured to receive automatic updates using an `.appinstaller` file.</span></span> <span data-ttu-id="a86dd-106">Visual Studio unterstützt das Aktivieren dieser Updates.</span><span class="sxs-lookup"><span data-stu-id="a86dd-106">Visual Studio supports enabling these updates.</span></span>

## <a name="app-installer-file-location"></a><span data-ttu-id="a86dd-107">Speicherort der App-Installer-Datei</span><span class="sxs-lookup"><span data-stu-id="a86dd-107">App Installer file location</span></span>
<span data-ttu-id="a86dd-108">Die `.appinstaller`-Datei in kann an einem freigegebenen Speicherort wie einem HTTP-Endpunkt oder einem freigegebenen UNC-Ordner gehostet werden, und enthält den Pfad zum Suchen der zu installierenden App-Pakete.</span><span class="sxs-lookup"><span data-stu-id="a86dd-108">The `.appinstaller` file can be hosted in a shared location like a HTTP endpoint or a UNC shared folder, and includes the path to find the app packages to be installed.</span></span> <span data-ttu-id="a86dd-109">Benutzer installieren die App vom freigegebenen Speicherort und aktivieren regelmäßige Überprüfungen auf neue Updates.</span><span class="sxs-lookup"><span data-stu-id="a86dd-109">Users install the app from the shared location and enable periodic checks for new updates.</span></span> 


### <a name="configure-the-project-to-target-the-correct-windows-version"></a><span data-ttu-id="a86dd-110">Konfigurieren des Projekts für die richtige Windows-Version</span><span class="sxs-lookup"><span data-stu-id="a86dd-110">Configure the project to target the correct Windows version</span></span>

<span data-ttu-id="a86dd-111">Sie können die `TargetPlatformMinVersion`-Eigenschaft entweder beim Erstellen des Projekts konfigurieren, oder später in den Projekteigenschaften ändern.</span><span class="sxs-lookup"><span data-stu-id="a86dd-111">You can either configure the `TargetPlatformMinVersion` property when you create the project, or change it later from the project properties.</span></span> 

>[!IMPORTANT]
> <span data-ttu-id="a86dd-112">Die App-Installer-Datei wird nur generiert, wenn die `TargetPlatformMinVersion` Windows10, Version 1804 oder höher ist.</span><span class="sxs-lookup"><span data-stu-id="a86dd-112">The app installer file is only generated when the `TargetPlatformMinVersion` is Windows 10, Version 1804 or greater.</span></span>


### <a name="create-packages"></a><span data-ttu-id="a86dd-113">Erstellen von Paketen</span><span class="sxs-lookup"><span data-stu-id="a86dd-113">Create Packages</span></span>

<span data-ttu-id="a86dd-114">Um eine app über querladen zu verteilen, müssen Sie ein app-Paket (.appx/.msix) oder app-Bündel (.appxbundle/.msixbundle) erstellen und es an einem freigegebenen Speicherort veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="a86dd-114">To distribute an app via sideloading, you must create an app package (.appx/.msix) or app bundle (.appxbundle/.msixbundle) and publish it in a shared location.</span></span>

<span data-ttu-id="a86dd-115">Verwenden Sie dazu den Assistenten **App-Pakete erstellen** in Visual Studio mit den folgenden Schritten.</span><span class="sxs-lookup"><span data-stu-id="a86dd-115">To do that, use the **Create App Packages** wizard in Visual Studio with the following steps.</span></span>

1. <span data-ttu-id="a86dd-116">Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Store** -> **App-Pakete erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="a86dd-116">Right-click the project and choose **Store** -> **Create App Packages**.</span></span>  

![Kontextmenü mit Navigation zu „App-Pakete erstellen“](images/packaging-screen2.jpg)   

<span data-ttu-id="a86dd-118">Der Assistent **App-Pakete erstellen** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a86dd-118">The **Create App Packages** wizard appears.</span></span>

2. <span data-ttu-id="a86dd-119">Wählen Sie **Ich möchte Pakete zum Querladen erstellen.**</span><span class="sxs-lookup"><span data-stu-id="a86dd-119">Select **I want to create packages for sideloading.**</span></span> <span data-ttu-id="a86dd-120">und **Automatische Updates aktivieren** aus.</span><span class="sxs-lookup"><span data-stu-id="a86dd-120">and **Enable automatic updates**</span></span>  

![Dialogfeld „Ihre Pakete erstellen“](images/select-sideloading.png)  

<span data-ttu-id="a86dd-122">Die Option **Automatische Updates aktivieren** ist nur aktiviert, wenn die `TargetPlatformMinVersion` des Projekts auf die richtige Version von Windows10 festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a86dd-122">**Enable automatic updates** is enabled only if the project's `TargetPlatformMinVersion` is set to the correct version of Windows 10.</span></span>

3. <span data-ttu-id="a86dd-123">Im Dialogfeld **Auswählen und Konfigurieren von Paketen** können Sie die unterstützten Architekturkonfigurationen auswählen.</span><span class="sxs-lookup"><span data-stu-id="a86dd-123">The **Select and Configure Packages** dialog allows you to select the supported architecture configurations.</span></span> <span data-ttu-id="a86dd-124">Wenn Sie ein Bündel auswählen, wird ein einzelnes Installationsprogramm generiert. Wenn Sie jedoch kein Bündel wünschen und ein Paket pro Architektur bevorzugen, erhalten Sie auch eine Installationsdatei pro Architektur.</span><span class="sxs-lookup"><span data-stu-id="a86dd-124">If you select a bundle it will generate a single installer, however if you don't want a bundle and prefer one package per architecture you will also get one installer file per architecture.</span></span>  <span data-ttu-id="a86dd-125">Wenn Sie nicht sicher sind, welche Architektur(en) Sie auswählen sollen, oder wenn Sie mehr darüber erfahren möchten, welche Architekturen von verschiedenen Geräten verwendet werden, finden Sie weitere Informationen unter [App-Paketarchitekturen](device-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="a86dd-125">If you're unsure which architecture(s) to choose, or want to learn more about which architectures are used by various devices, see [App package architectures](device-architecture.md).</span></span>

4. <span data-ttu-id="a86dd-126">Konfigurieren Sie zusätzliche Details wie die Versionsnummer oder den Ausgabespeicherort des Pakets.</span><span class="sxs-lookup"><span data-stu-id="a86dd-126">Configure any additional details, such as version numbering or the package output location.</span></span>

![Dialogfeld „App-Pakete erstellen“ mit Paketkonfiguration](images/packaging-screen5.jpg)  

5. <span data-ttu-id="a86dd-128">Wenn Sie in Schritt 2 **Automatische Updates aktivieren** aktiviert haben, wird das Dialogfeld **Konfigurieren der Update-Einstellungen** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a86dd-128">If you checked **Enable automatic updates** in Step 2, the **Configure Update Settings** dialog will appear.</span></span> <span data-ttu-id="a86dd-129">Hier können Sie die **Installations-URL** und die Häufigkeit der Update-Prüfungen angeben.</span><span class="sxs-lookup"><span data-stu-id="a86dd-129">Here, you can specify the **Installation URL** and the frequency of update checks.</span></span>

![Anzeige des Dialogfelds „Konfigurieren der Update-Einstellungen” mit Konfiguration des Veröffentlichungsortes](images/sideloading-screen.png)  

6. <span data-ttu-id="a86dd-131">Wenn Ihre App erfolgreich verpackt wurde, wird in einem Dialogfeld der Speicherort des Ausgabeordners, der Ihr App-Paket enthält, angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a86dd-131">When your app has been successfully packaged, a dialog will display the location of the output folder containing your app package.</span></span> <span data-ttu-id="a86dd-132">Der Ausgabeordner enthält alle Dateien, die für das Querladen der App erforderlich sind, einschließlich einer HTML-Seite, die zum Bewerben Ihrer App verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="a86dd-132">The output folder includes all the files needed to sideload the app, including an HTML page that can be used to promote your app.</span></span>

### <a name="publish-packages"></a><span data-ttu-id="a86dd-133">Veröffentlichung von Paketen</span><span class="sxs-lookup"><span data-stu-id="a86dd-133">Publish packages</span></span>

<span data-ttu-id="a86dd-134">Um die Anwendung verfügbar zu machen, müssen die generierten Dateien am angegebenen Speicherort veröffentlicht werden:</span><span class="sxs-lookup"><span data-stu-id="a86dd-134">To make the application available the generated files must be published to the location specified:</span></span>

#### <a name="publish-to-shared-folders-unc"></a><span data-ttu-id="a86dd-135">Veröffentlichung in freigegebenen Ordnern (UNC)</span><span class="sxs-lookup"><span data-stu-id="a86dd-135">Publish to shared folders (UNC)</span></span>

<span data-ttu-id="a86dd-136">Wenn Sie Ihre Pakete über freigegebene UNC (Universal Naming Convention)-Ordner veröffentlichen möchten, konfigurieren Sie den Ausgabeordner des App-Pakets sowie die Installations-URL (Details finden Sie unter Schritt6) im selben Pfad.</span><span class="sxs-lookup"><span data-stu-id="a86dd-136">If you want to publish your packages over Universal Naming Convention (UNC) shared folders, configure the app package output folder and the Installation URL (see Step 6 for details) to the same path.</span></span> <span data-ttu-id="a86dd-137">Der Assistent generiert die Dateien am richtigen Speicherort, und Benutzer erhalten sowohl die App, als auch die zukünftigen Updates vom selben Pfad.</span><span class="sxs-lookup"><span data-stu-id="a86dd-137">The wizard will generate the files in the correct location, and users will get both the app and future updates from the same path.</span></span>

#### <a name="publish-to-a-web-location-http"></a><span data-ttu-id="a86dd-138">Veröffentlichung an einem Webspeicherort (HTTP)</span><span class="sxs-lookup"><span data-stu-id="a86dd-138">Publish to a web location (HTTP)</span></span>

<span data-ttu-id="a86dd-139">Für die Veröffentlichung an einem Webspeicherort ist ein Zugriff erforderlich, damit Inhalte auf dem Webserver veröffentlicht werden können. Dabei muss sichergestellt werden, dass die endgültige URL der im Assistenten definierten Installations-URL entspricht (Details finden Sie unter Schritt6).</span><span class="sxs-lookup"><span data-stu-id="a86dd-139">Publishing to a web location requires access to publish content to the web server, making sure the final URL matches the Installation URL defined in the wizard (see Step 6 for details).</span></span> <span data-ttu-id="a86dd-140">In der Regel werden das File Transfer Protocol (FTP) oder das SSH-File Transfer Protocol (SFTP) zum Hochladen der Dateien verwendet, es gibt aber je nach Ihrem Web-Provider auch andere Veröffentlichungsmethoden wie MSDeploy, SSH oder Blob Storage.</span><span class="sxs-lookup"><span data-stu-id="a86dd-140">Typically, File Transfer Protocol (FTP) or SSH File Transfer Protocol (SFTP) are used to upload the files, but there are other publishing methods like MSDeploy, SSH, or Blob storage, depending on your web provider.</span></span>

<span data-ttu-id="a86dd-141">Um den Webserver zu konfigurieren, müssen Sie die MIME-Typen überprüfen, die für die verwendeten Dateitypen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a86dd-141">To configure the web server you must verify the MIME types used for the file types in use.</span></span> <span data-ttu-id="a86dd-142">Dies ist ein Beispiel aus `web.config` für Internetinformationsdienste (IIS):</span><span class="sxs-lookup"><span data-stu-id="a86dd-142">This example is of the `web.config` for Internet Information Services (IIS):</span></span>

```xml
<configuration>
  <system.webServer>
    <staticContent>
      <mimeMap fileExtension=".appx" mimeType="application/vns.ms-appx" />
      <mimeMap fileExtension=".appxbundle" mimeType="application/vns.ms-appx" />
      <mimeMap fileExtension=".appinstaller" mimeType="application/xml" />
    </staticContent>  
  </system.webServer>  
</configuration>
```




















