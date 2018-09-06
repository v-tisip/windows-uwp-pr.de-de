---
author: PatrickFarley
ms.assetid: 78D833B9-E528-4BCA-9C48-A757F17E6C22
title: Zertifizierungskit für Windows-Apps
description: Damit Ihre app die beste Chance auf der Microsoft Store oder Chancen Windows-Zertifizierung veröffentlicht wird, überprüfen Sie und Testen sie lokal, bevor Sie sie zur Zertifizierung übermitteln. In diesem Thema wird erläutert, wie Sie das Zertifizierungskit für Windows-Apps installieren und ausführen.
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, app-Zertifizierung
ms.localizationpriority: medium
ms.openlocfilehash: b7a72a89704aa3768cc43cdfbb75b620bae303e3
ms.sourcegitcommit: 7aa1933e6970f878faf50d59e1f799b90afd7cc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "3370176"
---
# <a name="windows-app-certification-kit"></a><span data-ttu-id="e8f4e-105">Zertifizierungskit für Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="e8f4e-105">Windows App Certification Kit</span></span>



<span data-ttu-id="e8f4e-106">Zum Abrufen von Ihrer app, die [Windows-Zertifizierung](https://msdn.microsoft.com/windows/desktop/jj134964.aspx) , oder für die [Veröffentlichung im Microsoft Store](https://msdn.microsoft.com/library/windows/apps/Hh694062)vorbereiten, sollten Sie überprüfen und testen es zunächst lokal.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-106">To get your app [Windows Certified](https://msdn.microsoft.com/windows/desktop/jj134964.aspx) or prepare it for [publication to the Microsoft Store](https://msdn.microsoft.com/library/windows/apps/Hh694062), you should validate and test it locally first.</span></span> <span data-ttu-id="e8f4e-107">In diesem Thema wird das Installieren und Ausführen der [Zertifizierungskit für Windows-Apps](http://go.microsoft.com/fwlink/p/?LinkID=309666) , um sicherzustellen, dass Ihre app sicheren und effizienten veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-107">This topic shows you how to install and run the [Windows App Certification Kit](http://go.microsoft.com/fwlink/p/?LinkID=309666) to ensure your app is safe and efficient.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e8f4e-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e8f4e-108">Prerequisites</span></span>

<span data-ttu-id="e8f4e-109">Voraussetzungen für das Testen einer universellen Windows-App:</span><span class="sxs-lookup"><span data-stu-id="e8f4e-109">Prerequisites for testing a Universal Windows app:</span></span>

-   <span data-ttu-id="e8f4e-110">Installieren und verwenden Sie Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-110">You must install and run Windows 10.</span></span>
-   <span data-ttu-id="e8f4e-111">Sie müssen das [Zertifizierungskit für Windows-Apps, Version10]( http://go.microsoft.com/fwlink/p/?LinkID=309666) installieren, das im Windows Software Development Kit (SDK) für Windows10 enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-111">You must install [Windows App Certification Kit version 10]( http://go.microsoft.com/fwlink/p/?LinkID=309666), which is included in the Windows Software Development Kit (SDK) for Windows 10.</span></span>
-   <span data-ttu-id="e8f4e-112">Sie müssen [Ihr Gerät für die Entwicklung aktivieren](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development).</span><span class="sxs-lookup"><span data-stu-id="e8f4e-112">You must [enable your device for development](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development).</span></span>
-   <span data-ttu-id="e8f4e-113">Sie müssen die zu testende Windows-App auf Ihrem Computer bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-113">You must deploy the Windows app that you want to test to your computer.</span></span>

**<span data-ttu-id="e8f4e-114">Hinweis zu direkten Upgrades</span><span class="sxs-lookup"><span data-stu-id="e8f4e-114">A note about in-place upgrades</span></span>**

<span data-ttu-id="e8f4e-115">Beim Installieren einer neueren Version des [Zertifizierungskits für Windows-Apps]( http://go.microsoft.com/fwlink/p/?LinkID=309666) werden alle vorherigen Versionen des Kits ersetzt, die auf dem Computer installiert sind.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-115">The installation of a more recent [Windows App Certification Kit]( http://go.microsoft.com/fwlink/p/?LinkID=309666) will replace any previous version of the kit that is installed on the machine.</span></span>

## <a name="validate-your-windows-app-using-the-windows-app-certification-kit-interactively"></a><span data-ttu-id="e8f4e-116">Interaktive Überprüfung der Windows-App mit dem Zertifizierungskit für Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="e8f4e-116">Validate your Windows app using the Windows App Certification Kit interactively</span></span>

1.  <span data-ttu-id="e8f4e-117">Suchen Sie im Startmenü**** nach den Einträgen **Apps** und **Windows Kits**, und klicken Sie auf die Option für das Zertifizierungskit für Windows-Apps****.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-117">From the **Start** menu, search **Apps**, find **Windows Kits**, and click **Windows App Cert Kit**.</span></span>

2.  <span data-ttu-id="e8f4e-118">Wählen Sie im Zertifizierungskit für Windows-Apps die Kategorie der auszuführenden Überprüfung aus.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-118">From the Windows App Certification Kit, select the category of validation you would like to perform.</span></span> <span data-ttu-id="e8f4e-119">Beispiel: Wenn Sie eine Windows-App überprüfen, wählen Sie die Option zum **Überprüfen einer Windows-App** aus.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-119">For example: If you are validating a Windows app, select **Validate a Windows app**.</span></span>

    <span data-ttu-id="e8f4e-120">Sie können direkt zur jeweiligen App navigieren oder die App in einer Liste auf der Benutzeroberfläche auswählen.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-120">You may browse directly to the app you're testing, or choose the app from a list in the UI.</span></span> <span data-ttu-id="e8f4e-121">Bei der erstmaligen Ausführung des Zertifizierungskits für Windows-Apps werden auf der Benutzeroberfläche alle Windows-Apps aufgelistet, die auf dem Computer installiert sind.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-121">When the Windows App Certification Kit is run for the first time, the UI lists all the Windows apps that you have installed on your computer.</span></span> <span data-ttu-id="e8f4e-122">Bei nachfolgenden Ausführungen werden die Windows-Apps angezeigt, die Sie bereits überprüft haben.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-122">For any subsequent runs, the UI will display the most recent Windows apps that you have validated.</span></span> <span data-ttu-id="e8f4e-123">Falls die zu testende App nicht in der Liste enthalten ist, können Sie auf **Meine App ist nicht aufgeführt** klicken, um eine Liste aller installierten Apps im System anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-123">If the app that you want to test is not listed, you can click on **My app isn't listed** to get a comprehensive list of all apps installed on your system.</span></span>

3.  <span data-ttu-id="e8f4e-124">Nachdem Sie die zu testende App eingegeben oder ausgewählt haben, klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-124">After you have input or selected the app that you want to test, click **Next**.</span></span>

4.  <span data-ttu-id="e8f4e-125">Auf dem nächsten Bildschirm sehen Sie den Testworkflow für die App, die Sie testen möchten.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-125">From the next screen, you will see the test workflow that aligns to the app type you are testing.</span></span> <span data-ttu-id="e8f4e-126">Wenn ein Test in der Liste deaktiviert ist, kann er nicht für Ihre Umgebung angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-126">If a test is grayed out in the list, the test is not applicable to your environment.</span></span> <span data-ttu-id="e8f4e-127">Wenn Sie eine z.B. einer Windows10-App unter Windows7 testen, werden nur statische Tests für den Workflow angewendet.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-127">For example, if you are testing a Windows 10 app on Windows 7, only static tests will apply to the workflow.</span></span> <span data-ttu-id="e8f4e-128">Beachten Sie, dass der Microsoft Store alle Tests aus diesem Workflow anwenden kann.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-128">Note that the Microsoft Store may apply all tests from this workflow.</span></span> <span data-ttu-id="e8f4e-129">Wählen Sie aus, welche Tests Sie ausführen möchten, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-129">Select the tests you want to run and click **Next**.</span></span>

    <span data-ttu-id="e8f4e-130">Das Zertifizierungskit für Windows-Apps beginnt mit dem Überprüfen der App.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-130">The Windows App Certification Kit begins validating the app.</span></span>

5.  <span data-ttu-id="e8f4e-131">Geben Sie den Pfad zu dem Ordner an, in dem der Testbericht gespeichert werden soll, wenn Sie nach dem Testen dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-131">At the prompt after the test, enter the path to the folder where you want to save the test report.</span></span>

    <span data-ttu-id="e8f4e-132">Vom Zertifizierungskit für Windows-Apps werden ein XML-Bericht und ein HTML-Bericht erstellt und in diesem Ordner gespeichert.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-132">The Windows App Certification Kit creates an HTML along with an XML report and saves it in this folder.</span></span>

6.  <span data-ttu-id="e8f4e-133">Öffnen Sie die Berichtsdatei, und überprüfen Sie die Ergebnisse des Tests.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-133">Open the report file and review the results of the test.</span></span>

<span data-ttu-id="e8f4e-134">**Hinweis**  Bei Verwendung von Visual Studio können Sie das Zertifizierungskit für Windows-Apps ausführen, wenn Sie das App-Paket erstellen.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-134">**Note**  If you're using Visual Studio, you can run the Windows App Certification Kit when you create your app package.</span></span> <span data-ttu-id="e8f4e-135">Informationen zur Vorgehensweise finden Sie unter [Verpacken von UWP-Apps](https://msdn.microsoft.com/library/windows/apps/Mt627715).</span><span class="sxs-lookup"><span data-stu-id="e8f4e-135">See [Packaging UWP apps](https://msdn.microsoft.com/library/windows/apps/Mt627715) to learn how.</span></span>

 

## <a name="validate-your-windows-app-using-the-windows-app-certification-kit-from-a-command-line"></a><span data-ttu-id="e8f4e-136">Überprüfung der Windows-App mit dem Zertifizierungskit für Windows-Apps über eine Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="e8f4e-136">Validate your Windows app using the Windows App Certification Kit from a command line</span></span>

<span data-ttu-id="e8f4e-137">**Wichtig**  Das Zertifizierungskit für Windows-Apps muss im Kontext einer aktiven Benutzersitzung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-137">**Important**  The Windows App Certification Kit must be run within the context of an active user session.</span></span>

1.  <span data-ttu-id="e8f4e-138">Navigieren Sie im Befehlsfenster zum Verzeichnis mit dem Zertifizierungskit für Windows-Apps.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-138">In the command window, navigate to the directory that contains the Windows App Certification Kit.</span></span>

    <span data-ttu-id="e8f4e-139">**Hinweis**   Der Standardpfad lautet „C:\\Programme\\Windows Kits\\10\\App Certification Kit\\“.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-139">**Note**   The default path is C:\\Program Files\\Windows Kits\\10\\App Certification Kit\\.</span></span>

2.  <span data-ttu-id="e8f4e-140">Geben Sie die folgenden Befehle in dieser Reihenfolge ein, um eine App zu testen, die bereits auf dem Testcomputer installiert ist:</span><span class="sxs-lookup"><span data-stu-id="e8f4e-140">Enter the following commands in this order to test an app that is already installed on your test computer:</span></span>

    `appcert.exe reset`

    `appcert.exe test -packagefullname [package full name] -reportoutputpath [report file name]`

    <span data-ttu-id="e8f4e-141">Wenn Sie App nicht installiert ist, können Sie die folgenden Befehle verwenden.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-141">Or you can use the following commands if the app is not installed.</span></span> <span data-ttu-id="e8f4e-142">Das Zertifizierungskit für Windows-Apps öffnet das Paket und wendet den entsprechenden Testworkflow an:</span><span class="sxs-lookup"><span data-stu-id="e8f4e-142">The Windows App Certification Kit will open the package and apply the appropriate test workflow:</span></span>

    `appcert.exe reset`

    `appcert.exe test -appxpackagepath [package path] -reportoutputpath [report file name]`

3.  <span data-ttu-id="e8f4e-143">Öffnen Sie nach dem Test die Berichtsdatei `[report file name]`, und überprüfen Sie die Testergebnisse.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-143">After the test completes, open the report file named `[report file name]` and review the test results.</span></span>

<span data-ttu-id="e8f4e-144">**Hinweis**  Das Zertifizierungskit für Windows-Apps kann über einen Dienst ausgeführt werden. Der Dienst muss den Kitvorgang jedoch innerhalb einer aktiven Benutzersitzung initiieren, und die Ausführung unter „Session0“ ist nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-144">**Note**  The Windows App Certification Kit can be run from a service, but the service must initiate the kit process within an active user session and cannot be run in Session0.</span></span>

<span data-ttu-id="e8f4e-145">**Hinweis**   Weitere Informationen zur Befehlszeile des Zertifizierungskits für Windows-Apps erhalten Sie durch Eingabe des Befehls</span><span class="sxs-lookup"><span data-stu-id="e8f4e-145">**Note**   For more info about the Windows App Certification Kit command line, enter the command</span></span> `appcert.exe /?`

## <a name="testing-with-a-low-power-computer"></a><span data-ttu-id="e8f4e-146">Testen mit einem Computer mit geringem Energieverbrauch</span><span class="sxs-lookup"><span data-stu-id="e8f4e-146">Testing with a low-power computer</span></span>

<span data-ttu-id="e8f4e-147">Die Leistungstestgrenzen des Zertifizierungskits für Windows-Apps basieren auf der Leistung eines Computers mit geringem Energieverbrauch.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-147">The performance test thresholds of the Windows App Certification Kit are based on the performance of a low-power computer.</span></span>

<span data-ttu-id="e8f4e-148">Die Eigenschaften des Computers, auf dem der Test ausgeführt wird, können die Testergebnisse beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-148">The characteristics of the computer on which the test is performed can influence the test results.</span></span> <span data-ttu-id="e8f4e-149">Um festzustellen, ob die Leistung Ihrer app die [Microsoft Store-Richtlinien](https://msdn.microsoft.com/library/windows/apps/Dn764944)erfüllt, wird empfohlen, dass Sie Ihre app auf einem Computer mit geringem Energieverbrauch, z. B. eine Intel Atom-Prozessor-basierten Computer mit einer Auflösung von 1366 x 768 (oder höher) und einer rotierenden Festplatte testen Laufwerk (im Gegensatz zu einem Festkörperlaufwerk).</span><span class="sxs-lookup"><span data-stu-id="e8f4e-149">To determine if your app’s performance meets the [Microsoft Store Policies](https://msdn.microsoft.com/library/windows/apps/Dn764944), we recommend that you test your app on a low-power computer, such as an Intel Atom processor-based computer with a screen resolution of 1366x768 (or higher) and a rotational hard drive (as opposed to a solid-state hard drive).</span></span>

<span data-ttu-id="e8f4e-150">Da Computer mit geringem Energieverbrauch weiterentwickelt werden, können sich die Leistungsmerkmale im Laufe der Zeit ändern.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-150">As low-power computers evolve, their performance characteristics might change over time.</span></span> <span data-ttu-id="e8f4e-151">Verweisen auf die aktuelle [Microsoft Store-Richtlinien](https://msdn.microsoft.com/library/windows/apps/Dn764944) , und Testen Sie Ihre app mit der aktuellen Version des Zertifizierungskits für Windows-App sicherstellen, dass Ihre app die aktuellen leistungsanforderungen entspricht.</span><span class="sxs-lookup"><span data-stu-id="e8f4e-151">Refer to the most current [Microsoft Store Policies](https://msdn.microsoft.com/library/windows/apps/Dn764944) and test your app with the most current version of the Windows App Certification Kit to make sure that your app complies with the latest performance requirements.</span></span>

## <a name="related-topics"></a><span data-ttu-id="e8f4e-152">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e8f4e-152">Related topics</span></span>

* [<span data-ttu-id="e8f4e-153">Tests im Zertifizierungskit für Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="e8f4e-153">Windows App Certification Kit tests</span></span>](windows-app-certification-kit-tests.md)
* [<span data-ttu-id="e8f4e-154">Microsoft Store-Richtlinien</span><span class="sxs-lookup"><span data-stu-id="e8f4e-154">Microsoft Store Policies</span></span>](https://msdn.microsoft.com/library/windows/apps/Dn764944)
 

 




