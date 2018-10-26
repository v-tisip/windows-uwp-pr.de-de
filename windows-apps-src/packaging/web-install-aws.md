---
author: laurenhughes
title: Hosten von UWP-App-Paketen auf AWS für die Webinstallation
description: Lernprogramm für die Einrichtung AWS-Webservers zum Überprüfen der app-Installation über App-Installer-App
ms.author: cdon
ms.date: 05/30/2018
ms.topic: article
keywords: Windows 10, Windows 10, UWP, app-Installer, AppInstaller, querladen, im Zusammenhang mit festgelegten, optionale Pakete, AWS
ms.localizationpriority: medium
ms.openlocfilehash: f24abac93e2444a3c9f454c8883902e5db4d31be
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5548834"
---
# <a name="hosting-uwp-app-packages-on-aws-for-web-install"></a><span data-ttu-id="3349a-104">Hosten von UWP-App-Paketen auf AWS für die Webinstallation</span><span class="sxs-lookup"><span data-stu-id="3349a-104">Hosting UWP app packages on AWS for web install</span></span>

<span data-ttu-id="3349a-105">Mit der App-Installer-App können Entwickler und IT-Spezialisten Windows10-Apps verteilen, indem sie diese in ihrem eigenen Content Delivery Network (CDN) hosten.</span><span class="sxs-lookup"><span data-stu-id="3349a-105">The App Installer app allows developers and IT Pros to distribute Windows 10 apps by hosting them on their own Content Delivery Network (CDN).</span></span> <span data-ttu-id="3349a-106">Das ist nützlich für Unternehmen, die ihre Apps nicht im Microsoft Store veröffentlichen möchten oder müssen, aber weiterhin die Windows10-Verpackungs- und -Bereitstellungsplattform nutzen möchten.</span><span class="sxs-lookup"><span data-stu-id="3349a-106">This is useful for enterprises that don't want or need to publish their apps to the Microsoft Store, but still want to take advantage of the Windows 10 packaging and deployment platform.</span></span>

<span data-ttu-id="3349a-107">In diesem Thema werden die Schritte zum Konfigurieren einer Website Amazon Web Services (AWS), um UWP-app-Pakete hosten und wie Sie die App-Installer-app verwenden, um die app-Pakete zu installieren.</span><span class="sxs-lookup"><span data-stu-id="3349a-107">This topic outlines the steps to configure an Amazon Web Services (AWS) website to host UWP app packages, and how to use the App Installer app to install the app packages.</span></span>

## <a name="setup"></a><span data-ttu-id="3349a-108">Setup</span><span class="sxs-lookup"><span data-stu-id="3349a-108">Setup</span></span>

<span data-ttu-id="3349a-109">Für eine erfolgreiche Durchführung dieses Lernprogramms benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="3349a-109">To successfully follow this tutorial, you will need the following:</span></span>
 
1. <span data-ttu-id="3349a-110">AWS Abonnement</span><span class="sxs-lookup"><span data-stu-id="3349a-110">AWS subscription</span></span> 
2. <span data-ttu-id="3349a-111">Webseite</span><span class="sxs-lookup"><span data-stu-id="3349a-111">Web page</span></span>
3. <span data-ttu-id="3349a-112">UWP-App-Paket – das App-Paket, die Sie verteilen möchten</span><span class="sxs-lookup"><span data-stu-id="3349a-112">UWP app package - The app package that you will distribute</span></span>

<span data-ttu-id="3349a-113">Optional: [Startprojekt](https://github.com/AppInstaller/MySampleWebApp) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="3349a-113">Optional: [Starter Project](https://github.com/AppInstaller/MySampleWebApp) on GitHub.</span></span> <span data-ttu-id="3349a-114">Dies ist hilfreich, wenn Sie kein App-Paket oder keine Webseite zum Arbeiten verfügbar haben, aber dennoch lernen möchten, wie Sie dieses Feature verwenden.</span><span class="sxs-lookup"><span data-stu-id="3349a-114">This is helpful if you don't an app package or web page to work with, but would still like to learn how to use this feature.</span></span>

<span data-ttu-id="3349a-115">In diesem Lernprogramm wird über eine Webseite und Host-Paketen auf AWS Einrichtung geleitet.</span><span class="sxs-lookup"><span data-stu-id="3349a-115">This tutorial will go over how to setup a web page and host packages on AWS.</span></span> <span data-ttu-id="3349a-116">Dies ist ein AWS-Abonnement erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3349a-116">This will require an AWS subscription.</span></span> <span data-ttu-id="3349a-117">Je nach der Skalierung des Vorgangs können Sie ihre kostenlose Mitgliedschaft verwenden, um dieses Lernprogramms.</span><span class="sxs-lookup"><span data-stu-id="3349a-117">Depending on the scale of your operation, you can use their free membership to follow this tutorial.</span></span> 

## <a name="step-1---aws-membership"></a><span data-ttu-id="3349a-118">Schritt 1: AWS Mitgliedschaft</span><span class="sxs-lookup"><span data-stu-id="3349a-118">Step 1 - AWS membership</span></span>
<span data-ttu-id="3349a-119">Um eine AWS-Mitgliedschaft erhalten, finden Sie auf der [Detailseite für das Konto AWS](https://aws.amazon.com/free/).</span><span class="sxs-lookup"><span data-stu-id="3349a-119">To get an AWS membership, visit the [AWS account details page](https://aws.amazon.com/free/).</span></span> <span data-ttu-id="3349a-120">Für die Zwecke dieses Lernprogramms können Sie eine kostenlose Mitgliedschaft verwenden.</span><span class="sxs-lookup"><span data-stu-id="3349a-120">For the purposes of this tutorial, you can use a free membership.</span></span>

## <a name="step-2---create-an-amazon-s3-bucket"></a><span data-ttu-id="3349a-121">Schritt 2: Erstellen einer Amazon S3 Buckets</span><span class="sxs-lookup"><span data-stu-id="3349a-121">Step 2 - Create an Amazon S3 bucket</span></span>

<span data-ttu-id="3349a-122">Amazon Simple Storage Service (S3) ist eine Lösung für die Erfassung, speichern und Analysieren von Daten AWS.</span><span class="sxs-lookup"><span data-stu-id="3349a-122">Amazon Simple Storage Service (S3) is an AWS offering for collecting, storing and analyzing data.</span></span> <span data-ttu-id="3349a-123">S3 Buckets handelt es sich um eine praktische Möglichkeit zum UWP-app-Pakete hosten und Webseiten für die Verteilung.</span><span class="sxs-lookup"><span data-stu-id="3349a-123">S3 buckets are a convenient way to host UWP app packages and web pages for distribution.</span></span> 

<span data-ttu-id="3349a-124">Nach der Anmeldung an AWS mit Ihren Anmeldeinformationen unter `Services` suchen `S3`.</span><span class="sxs-lookup"><span data-stu-id="3349a-124">After logging in to AWS with your credentials, under `Services` find `S3`.</span></span> 

<span data-ttu-id="3349a-125">Wählen Sie **Buckets erstellen**, und geben Sie einen **Namen Buckets** für Ihre Website.</span><span class="sxs-lookup"><span data-stu-id="3349a-125">Select **Create bucket**, and enter a **Bucket name** for your website.</span></span> <span data-ttu-id="3349a-126">Befolgen Sie die Anweisungen im Dialogfeld zum Festlegen von Eigenschaften und Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="3349a-126">Follow the dialog prompts for setting properties and permissions.</span></span> <span data-ttu-id="3349a-127">Um sicherzustellen, dass Ihre UWP-app aus Ihrer Website verteilt werden kann, aktivieren Sie **Lesen** und **Schreiben von** Berechtigungen für Ihre Buckets zu, und wählen Sie **Öffentliche Lesezugriff auf diese Buckets gewähren**.</span><span class="sxs-lookup"><span data-stu-id="3349a-127">To ensure that your UWP app can be distributed from your website, enable **Read** and **Write** permissions for your bucket and select **Grant public read access to this bucket**.</span></span>

![Festlegen von Berechtigungen für Amazon S3 Buckets](images/aws-permissions.png) 

<span data-ttu-id="3349a-129">Überprüfen Sie die Zusammenfassung, um sicherzustellen, dass die ausgewählten Optionen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3349a-129">Review the summary to make sure the selected options are reflected.</span></span> <span data-ttu-id="3349a-130">Klicken Sie auf **Buckets erstellen** , um diesen Schritt abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="3349a-130">Click **Create bucket** to finish this step.</span></span> 

## <a name="step-3---upload-uwp-app-package-and-web-pages-to-an-s3-bucket"></a><span data-ttu-id="3349a-131">Schritt 3: UWP-app-Paket und Webseiten in einer S3 Buckets hochladen</span><span class="sxs-lookup"><span data-stu-id="3349a-131">Step 3 - Upload UWP app package and web pages to an S3 bucket</span></span>

<span data-ttu-id="3349a-132">Eine haben Sie eine Amazon S3 Buckets erstellt, können in Ihrer Amazon S3-Ansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3349a-132">One you have created an Amazon S3 bucket, you will be able to see it in your Amazon S3 view.</span></span> <span data-ttu-id="3349a-133">Hier ist ein Beispiel, wie unsere Demo Buckets aussieht:</span><span class="sxs-lookup"><span data-stu-id="3349a-133">Here's an example of what our demo bucket looks like:</span></span>

![Amazon S3 Buckets Ansicht](images/aws-post-create.png)

<span data-ttu-id="3349a-135">Wir sind jetzt Hochladen der app-Pakete und Webseiten, die wir in unserem Amazon S3 Buckets hosten möchten.</span><span class="sxs-lookup"><span data-stu-id="3349a-135">We are now ready to upload the app packages and web pages that we would like to host in our Amazon S3 bucket.</span></span> 

<span data-ttu-id="3349a-136">Klicken Sie auf die neu erstellte Buckets zum Hochladen von Inhalten.</span><span class="sxs-lookup"><span data-stu-id="3349a-136">Click on the newly created bucket to upload content.</span></span> <span data-ttu-id="3349a-137">Die Buckets ist derzeit leer, da nichts noch nicht hochgeladen wurde.</span><span class="sxs-lookup"><span data-stu-id="3349a-137">The bucket is currently empty since nothing has been uploaded yet.</span></span> <span data-ttu-id="3349a-138">Klicken Sie auf die Schaltfläche **Hochladen** , und wählen Sie die app-Pakete und die Webseite-Dateien, die Sie hochladen möchten.</span><span class="sxs-lookup"><span data-stu-id="3349a-138">Click the **Upload** button and select the app packages and web page files that you like to upload.</span></span>

> [!NOTE]
> <span data-ttu-id="3349a-139">Sie können das App-Paket verwenden, das Teil des bereitgestellten [Startprojekt](https://github.com/AppInstaller/MySampleWebApp)-Repositorys auf GitHub ist, falls Ihnen kein App-Paket zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="3349a-139">You can use the app package that is part of the provided [Starter Project](https://github.com/AppInstaller/MySampleWebApp) repository on GitHub if you don't have an app package available.</span></span> <span data-ttu-id="3349a-140">Die Zertifikat (MySampleApp.cer), mit dem das Paket signiert wurde, ist ebenfalls im Beispiel auf GitHub enthalten.</span><span class="sxs-lookup"><span data-stu-id="3349a-140">The certificate (MySampleApp.cer) that the package was signed with is also with the sample on GitHub.</span></span> <span data-ttu-id="3349a-141">Sie müssen das Zertifikat vor der Installation der App auf Ihrem Gerät installieren.</span><span class="sxs-lookup"><span data-stu-id="3349a-141">You must have the certificate installed to your device prior to installing the app.</span></span>

![Hochladen von app-Paket](images/aws-upload-package.png)

<span data-ttu-id="3349a-143">Ähnlich wie die Berechtigungen für die Erstellung einer Amazon S3 Buckets, muss der Inhalt in der Buckets auch **Lesen**, **Schreiben**und **öffentlichen Lesezugriff auf diese Objekte Grant** -Berechtigungen verfügen.</span><span class="sxs-lookup"><span data-stu-id="3349a-143">Similar to the permissions for creating an Amazon S3 bucket, the content in the bucket must also have **read**, **write**, and **Grant public read access to this object(s)** permissions.</span></span>

<span data-ttu-id="3349a-144">Wenn Sie Testen einer Webseite hochladen möchten, aber nicht haben, können Sie die Beispiel für HTML-Seite (default.html) aus dem [Startprojekt](https://github.com/AppInstaller/MySampleWebApp/blob/master/MySampleWebApp/default.html)verwenden.</span><span class="sxs-lookup"><span data-stu-id="3349a-144">If you would like to test uploading a web page, but don't have one, you can use the sample html page (default.html) from the [Starter Project](https://github.com/AppInstaller/MySampleWebApp/blob/master/MySampleWebApp/default.html).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3349a-145">Bevor Sie die Webseite hochgeladen haben, stellen Sie sicher, dass die app-Paket-Referenz auf Ihrer Webseite korrekt ist.</span><span class="sxs-lookup"><span data-stu-id="3349a-145">Before you upload the web page, confirm that the app package reference in your web page is correct.</span></span> 

<span data-ttu-id="3349a-146">Zum Abrufen der Referenz zur app-Paket zuerst Hochladen von app-Paket, und kopieren Sie die app-Paket-URL.</span><span class="sxs-lookup"><span data-stu-id="3349a-146">To get the app package reference, upload the app package first and copy the app package URL.</span></span> <span data-ttu-id="3349a-147">Bearbeiten Sie die HTML-Webseite entsprechend den Pfad der richtigen app-Paket.</span><span class="sxs-lookup"><span data-stu-id="3349a-147">Edit the html web page to reflect the correct app package path.</span></span> <span data-ttu-id="3349a-148">Finden Sie im Codebeispiel für weitere Details.</span><span class="sxs-lookup"><span data-stu-id="3349a-148">See the code example for more details.</span></span> 

<span data-ttu-id="3349a-149">Wählen Sie die Datei hochgeladenen app-Paket auf den Referenzlink zum app-Paket abrufen, ähnlich wie in diesem Beispiel wird:</span><span class="sxs-lookup"><span data-stu-id="3349a-149">Select the uploaded app package file to get the reference link to the app package, it should be similar to this example:</span></span>

![hochgeladene Paketpfad](images/aws-package-path.png)

<span data-ttu-id="3349a-151">**Kopieren** der Link zur app Verpacken und fügen Sie den Verweis auf der Webseite hinzu.</span><span class="sxs-lookup"><span data-stu-id="3349a-151">**Copy** the link to the app package and add the reference in your web page.</span></span> 

```html
<html>
    <head>
        <meta charset="utf-8" />
        <title> Install My Sample App</title>
    </head>
    <body>
        <a href="ms-appinstaller:?source=https://s3-us-west-2.amazonaws.com/appinstaller-aws-demo/MySampleApp.appxbundle"> Install My Sample App</a>
    </body>
</html>
```
<span data-ttu-id="3349a-152">Hochladen der HTML-Datei in Ihrem Amazon S3 Buckets.</span><span class="sxs-lookup"><span data-stu-id="3349a-152">Upload the html file to your Amazon S3 bucket.</span></span> <span data-ttu-id="3349a-153">Denken Sie daran, legen Sie die Berechtigungen zum **Lesen** und **Schreiben von** Zugriff zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="3349a-153">Remember to set the permissions to allow **read** and **write** access.</span></span>

## <a name="step-4---test"></a><span data-ttu-id="3349a-154">Schritt 4: Test</span><span class="sxs-lookup"><span data-stu-id="3349a-154">Step 4 - Test</span></span>

<span data-ttu-id="3349a-155">Nachdem der Webseite in Ihre Amazon S3 Buckets hochgeladen wurde, rufen Sie den Link zu der Webseite durch die Auswahl der hochgeladenen HTML-Datei.</span><span class="sxs-lookup"><span data-stu-id="3349a-155">Once the web page is uploaded into your Amazon S3 bucket, get the link to the web page by selecting the uploaded html file.</span></span>

<span data-ttu-id="3349a-156">Verwenden Sie den Link, um die Webseite zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="3349a-156">Use the link to open the web page.</span></span> <span data-ttu-id="3349a-157">Da wir Berechtigungen erteilen öffentlichen Zugriff auf die app-Paket und die Webseite festgelegt haben, wird jeder Benutzer mit einem Link zu der Webseite werden darauf zugreifen und Ihre UWP-app-Pakete mithilfe von App-Installer installiert.</span><span class="sxs-lookup"><span data-stu-id="3349a-157">Since we set permissions to grant public access to the app package and web page, anyone with the link to the web page will be able to access it and install your UWP app packages using App Installer.</span></span> <span data-ttu-id="3349a-158">Beachten Sie, dass App-Installer Teil von Windows 10-Plattform ist.</span><span class="sxs-lookup"><span data-stu-id="3349a-158">Note that App Installer is part of the Windows 10 platform.</span></span> <span data-ttu-id="3349a-159">Als Entwickler müssen Sie keine Features oder zusätzlichen Code zu Ihrer app für die Verwendung der App-Installer ermöglichen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3349a-159">As a developer, you do not need to add any additional code or features to your app to enable the use of App Installer.</span></span> 

## <a name="troubleshooting"></a><span data-ttu-id="3349a-160">Fehlerbehebung</span><span class="sxs-lookup"><span data-stu-id="3349a-160">Troubleshooting</span></span>

### <a name="app-installer-fails-to-install"></a><span data-ttu-id="3349a-161">App-Installer Fehler bei der Installation</span><span class="sxs-lookup"><span data-stu-id="3349a-161">App Installer fails to install</span></span> 

<span data-ttu-id="3349a-162">App-Installation schlägt fehl, wenn das Zertifikat, dem mit das app-Paket signiert ist nicht auf dem Gerät installiert ist.</span><span class="sxs-lookup"><span data-stu-id="3349a-162">App installation will fail if the certificate that the app package is signed with isn't installed on the device.</span></span> <span data-ttu-id="3349a-163">Um dieses Problem zu beheben, müssen Sie das Zertifikat vor der Installation der App installieren.</span><span class="sxs-lookup"><span data-stu-id="3349a-163">To fix this, you will need to install the certificate prior to the installation of the app.</span></span> <span data-ttu-id="3349a-164">Wenn Sie ein app-Paket für die öffentliche Verteilung hosten, hat es empfohlen, um Ihr app-Paket mit einem Zertifikat von einer Zertifizierungsstelle zu signieren.</span><span class="sxs-lookup"><span data-stu-id="3349a-164">If you are hosting an app package for public distribution, it's recommended to sign your app package with a certificate from a certificate authority.</span></span> 


