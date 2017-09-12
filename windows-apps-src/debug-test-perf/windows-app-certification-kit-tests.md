---
author: PatrickFarley
ms.assetid: 1526FF4B-9E68-458A-B002-0A5F3A9A81FD
title: "Tests im Zertifizierungskit für Windows-Apps"
description: "Das Zertifizierungskit für Windows-Apps enthält eine Reihe von Tests, mit denen Sie sicherstellen können, dass eine App für die Veröffentlichung im Windows Store bereit ist."
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 5e3ae74ba4392b5021159f9fcb825009137701d3
ms.sourcegitcommit: e8cc657d85566768a6efb7cd972ebf64c25e0628
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2017
---
# <a name="windows-app-certification-kit-tests"></a><span data-ttu-id="b90d2-104">Tests im Zertifizierungskit für Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="b90d2-104">Windows App Certification Kit tests</span></span>

<span data-ttu-id="b90d2-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="b90d2-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="b90d2-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="b90d2-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="b90d2-107">Das Zertifizierungskit für Windows-Apps enthält eine Reihe von Tests, mit denen Sie sicherstellen können, dass eine App für die Veröffentlichung im Windows Store bereit ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-107">The Windows App Certification Kit contains a number of tests that can help ensure that your app is ready to be published on the Windows Store.</span></span>

## <a name="deployment-and-launch-tests"></a><span data-ttu-id="b90d2-108">Bereitstellungs- und Starttests</span><span class="sxs-lookup"><span data-stu-id="b90d2-108">Deployment and launch tests</span></span>

<span data-ttu-id="b90d2-109">Überwachen die App während des Zertifizierungstests, um aufzuzeichnen, wann sie abstürzt oder sich aufhängt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-109">Monitors the app during certification testing to record when it crashes or hangs.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-110">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-110">Background</span></span>

<span data-ttu-id="b90d2-111">Apps, die nicht mehr reagieren oder abstürzen, können zu einem Datenverlust und zu einer Beeinträchtigung des Benutzererlebnisses führen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-111">Apps that stop responding or crash can cause the user to lose data and have a poor experience.</span></span>

<span data-ttu-id="b90d2-112">Apps müssen voll funktionsfähig sein, ohne Windows-Kompatibilitätsmodi, AppHelp-Meldungen oder andere Kompatibilitätspatches zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-112">We expect apps to be fully functional without the use of Windows compatibility modes, AppHelp messages, or compatibility fixes.</span></span>

<span data-ttu-id="b90d2-113">Apps dürfen im Registrierungsschlüssel HKEY\-LOCAL\-MACHINE\\Software\\Microsoft\\Windows NT\\CurrentVersion\\Windows\\AppInit\-DLLs keine DLLs zum Laden auflisten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-113">Apps must not list DLLs to load in the HKEY\-LOCAL\-MACHINE\\Software\\Microsoft\\Windows NT\\CurrentVersion\\Windows\\AppInit\-DLLs registry key.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-114">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-114">Test details</span></span>

<span data-ttu-id="b90d2-115">Die App wird beim Zertifizierungstest durchgehend auf Flexibilität und Stabilität geprüft.</span><span class="sxs-lookup"><span data-stu-id="b90d2-115">We test the app resilience and stability throughout the certification testing.</span></span>

<span data-ttu-id="b90d2-116">Das Zertifizierungskit für Windows-Apps ruft [**IApplicationActivationManager::ActivateApplication**](https://msdn.microsoft.com/library/windows/desktop/Hh706903) auf, um Apps zu starten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-116">The Windows App Certification Kit calls [**IApplicationActivationManager::ActivateApplication**](https://msdn.microsoft.com/library/windows/desktop/Hh706903) to launch apps.</span></span> <span data-ttu-id="b90d2-117">Damit eine App mit **ActivateApplication** gestartet werden kann, muss die Benutzerkontensteuerung (UAC) aktiviert sein und die Bildschirmauflösung mindestens 1024x768 oder 768x1024 betragen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-117">For **ActivateApplication** to launch an app, User Account Control (UAC) must be enabled and the screen resolution must be at least 1024 x 768 or 768 x 1024.</span></span> <span data-ttu-id="b90d2-118">Ist eine dieser Bedingungen nicht erfüllt, fällt die App bei diesem Test durch.</span><span class="sxs-lookup"><span data-stu-id="b90d2-118">If either condition is not met, your app will fail this test.</span></span>

### <a name="corrective-actions"></a><span data-ttu-id="b90d2-119">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-119">Corrective actions</span></span>

<span data-ttu-id="b90d2-120">Stellen Sie sicher, dass die Benutzerkontensteuerung (UAC) auf dem Test-PC aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-120">Make sure UAC is enabled on the test computer.</span></span>

<span data-ttu-id="b90d2-121">Führen Sie den Test auf einem PC mit ausreichend großem Bildschirm aus.</span><span class="sxs-lookup"><span data-stu-id="b90d2-121">Make sure you are running the test on a computer with large enough screen.</span></span>

<span data-ttu-id="b90d2-122">Falls die App nicht gestartet werden kann, obwohl die Testplattform die Voraussetzungen für [**ActivateApplication**](https://msdn.microsoft.com/library/windows/desktop/Hh706903) erfüllt, können Sie das Problem mithilfe des Aktivierungsereignisprotokolls beheben.</span><span class="sxs-lookup"><span data-stu-id="b90d2-122">If your app fails to launch and your test platform satisfies the prerequisites of [**ActivateApplication**](https://msdn.microsoft.com/library/windows/desktop/Hh706903), you can troubleshoot the problem by reviewing the activation event log.</span></span> <span data-ttu-id="b90d2-123">So finden Sie die Einträge im Ereignisprotokoll:</span><span class="sxs-lookup"><span data-stu-id="b90d2-123">To find these entries in the event log:</span></span>

1.  <span data-ttu-id="b90d2-124">Öffnen Sie die Datei „eventvwr.exe“, und navigieren Sie zum Ordner „Application and Services Log\\Microsoft\\Windows\\Immersive-Shell“.</span><span class="sxs-lookup"><span data-stu-id="b90d2-124">Open eventvwr.exe and navigate to the Application and Services Log\\Microsoft\\Windows\\Immersive-Shell folder.</span></span>
2.  <span data-ttu-id="b90d2-125">Filtern Sie die Ansicht entsprechend, um folgende Ereigniskennungen anzuzeigen: 5900-6000.</span><span class="sxs-lookup"><span data-stu-id="b90d2-125">Filter the view to show Event Ids: 5900-6000.</span></span>
3.  <span data-ttu-id="b90d2-126">Prüfen Sie die Protokolleinträge, um zu ermitteln, weshalb die App nicht gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="b90d2-126">Review the log entries for info that might explain why the app didn't launch.</span></span>

<span data-ttu-id="b90d2-127">Führen Sie für die Datei mit dem Problem eine Problembehandlung durch, um das Problem zu identifizieren und zu beheben.</span><span class="sxs-lookup"><span data-stu-id="b90d2-127">Troubleshoot the file with the problem, identify and fix the problem.</span></span> <span data-ttu-id="b90d2-128">Erstellen Sie die App neu, und wiederholen Sie den Test.</span><span class="sxs-lookup"><span data-stu-id="b90d2-128">Rebuild and re-test the app.</span></span> <span data-ttu-id="b90d2-129">Sie können auch überprüfen, ob im Protokollordner des Zertifizierungskits für Windows-Apps eine Dumpdatei erstellt wurde, die zum Debuggen Ihrer App verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="b90d2-129">You can also check if a dump file was generated in the Windows App Certification Kit log folder that can be used to debug your app.</span></span>

## <a name="platform-version-launch-test"></a><span data-ttu-id="b90d2-130">Test der Funktionsfähigkeit auf Plattformversionen</span><span class="sxs-lookup"><span data-stu-id="b90d2-130">Platform Version Launch test</span></span>

<span data-ttu-id="b90d2-131">Überprüft, ob die Windows-App auf einer zukünftigen Version des Betriebssystems ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b90d2-131">Checks that the Windows app can run on a future version of the OS.</span></span> <span data-ttu-id="b90d2-132">Dieser Test wurde bisher nur beim Desktop-App-Workflow angewendet, ist jetzt jedoch für die Workflows für den Store und die universelle Windows-Plattform (UWP) aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b90d2-132">This test has historically been only applied to the Desktop app workflow, but this is now enabled for the Store and Universal Windows Platform (UWP) workflows.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-133">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-133">Background</span></span>

<span data-ttu-id="b90d2-134">Die Verwendung der Betriebssystemversionsinformationen ist für den WindowsStore eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-134">Operating system version info has restricted usage for the Windows Store.</span></span> <span data-ttu-id="b90d2-135">Diese wurde von Apps häufig fälschlicherweise zum Überprüfen der Betriebssystemversion verwendet, damit Benutzern spezielle Funktionen für eine bestimmte Betriebssystemversion von der App bereitgestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="b90d2-135">This has often been incorrectly used by apps to check OS version so that the app can provide users with functionality that is specific to an OS version.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-136">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-136">Test details</span></span>

<span data-ttu-id="b90d2-137">Das Zertifizierungskit für Windows-Apps verwendet „HighVersionLie“, um zu ermitteln, wie die App die Betriebssystemversion prüft.</span><span class="sxs-lookup"><span data-stu-id="b90d2-137">The Windows App Certification Kit uses the HighVersionLie to detect how the app checks the OS version.</span></span> <span data-ttu-id="b90d2-138">Wenn die App abstürzt, besteht sie diesen Test nicht.</span><span class="sxs-lookup"><span data-stu-id="b90d2-138">If the app crashes, it will fail this test.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-139">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-139">Corrective action</span></span>

<span data-ttu-id="b90d2-140">Apps sollten dies anhand von API-Funktionen zur Versionsabfrage überprüfen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-140">Apps should use Version API helper functions to check this.</span></span> <span data-ttu-id="b90d2-141">Weitere Informationen finden Sie unter [Version des Betriebssystems](https://msdn.microsoft.com/library/windows/desktop/ms724832).</span><span class="sxs-lookup"><span data-stu-id="b90d2-141">See [Operating System Version](https://msdn.microsoft.com/library/windows/desktop/ms724832) for more information.</span></span>

## <a name="background-tasks-cancellation-handler-validation"></a><span data-ttu-id="b90d2-142">Überprüfung des Abbruchhandlers für Aufgaben</span><span class="sxs-lookup"><span data-stu-id="b90d2-142">Background tasks cancellation handler validation</span></span>

<span data-ttu-id="b90d2-143">Dieser Test stellt sicher, dass die App über einen Abbruchhandler für deklarierte Hintergrundaufgaben verfügt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-143">This verifies that the app has a cancellation handler for declared background tasks.</span></span> <span data-ttu-id="b90d2-144">Es muss eine dedizierte Funktion vorhanden sein, die beim Abbruch der Aufgabe aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b90d2-144">There needs to be a dedicated function that will be called when the task is cancelled.</span></span> <span data-ttu-id="b90d2-145">Dieser Test wird nur für bereitgestellte Apps durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-145">This test is applied only for deployed apps.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-146">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-146">Background</span></span>

<span data-ttu-id="b90d2-147">Windows-Apps können einen Prozess registrieren, der im Hintergrund ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b90d2-147">Store apps can register a process that runs in the background.</span></span> <span data-ttu-id="b90d2-148">Eine E-Mail-App kann z.B. von Zeit zu Zeit einen Pingbefehl an einen Server senden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-148">For example, an email app may ping a server from time to time.</span></span> <span data-ttu-id="b90d2-149">Wenn das Betriebssystem diese Ressourcen jedoch benötigt, wird die Hintergrundaufgabe abgebrochen, und Apps sollten diesen Abbruch problemlos behandeln.</span><span class="sxs-lookup"><span data-stu-id="b90d2-149">However, if the OS needs these resources, it will cancel the background task, and apps should gracefully handle this cancellation.</span></span> <span data-ttu-id="b90d2-150">Apps ohne Abbruchhandler stürzen u.U. ab oder werden nicht geschlossen, wenn der Benutzer versucht, die App zu schließen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-150">Apps that don't have a cancellation handler may crash or not close when the user tries to close the app.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-151">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-151">Test details</span></span>

<span data-ttu-id="b90d2-152">Die App wird gestartet und angehalten, und der Teil der App, der sich nicht im Hintergrund befindet, wird beendet.</span><span class="sxs-lookup"><span data-stu-id="b90d2-152">The app is launched, suspended and the non-background portion of the app is terminated.</span></span> <span data-ttu-id="b90d2-153">Anschließend werden die Hintergrundaufgaben im Zusammenhang mit dieser App abgebrochen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-153">Then the background tasks associated with this app are cancelled.</span></span> <span data-ttu-id="b90d2-154">Der Zustand der App wird überprüft, und wenn die App noch ausgeführt, besteht sie diesen Test nicht.</span><span class="sxs-lookup"><span data-stu-id="b90d2-154">The state of the app is checked, and if the app is still running then it will fail this test.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-155">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-155">Corrective action</span></span>

<span data-ttu-id="b90d2-156">Fügen Sie Ihrer App den Abbruchhandler hinzu.</span><span class="sxs-lookup"><span data-stu-id="b90d2-156">Add the cancellation handler to your app.</span></span> <span data-ttu-id="b90d2-157">Weitere Informationen finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](https://msdn.microsoft.com/library/windows/apps/Mt299103).</span><span class="sxs-lookup"><span data-stu-id="b90d2-157">For more information see [Support your app with background tasks](https://msdn.microsoft.com/library/windows/apps/Mt299103).</span></span>

## <a name="app-count"></a><span data-ttu-id="b90d2-158">App-Anzahl</span><span class="sxs-lookup"><span data-stu-id="b90d2-158">App count</span></span>

<span data-ttu-id="b90d2-159">Dieser Test stellt sicher, dass ein App-Paket (APPX, App-Bündel) genau eine Anwendung enthält.</span><span class="sxs-lookup"><span data-stu-id="b90d2-159">This verifies that an app package (APPX, app bundle) contains one application.</span></span> <span data-ttu-id="b90d2-160">Dies wurde im Kit zu einem eigenständigen Test geändert.</span><span class="sxs-lookup"><span data-stu-id="b90d2-160">This was changed in the kit to be a standalone test.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-161">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-161">Background</span></span>

<span data-ttu-id="b90d2-162">Dieser Test wurde gemäß der Store-Richtlinie implementiert.</span><span class="sxs-lookup"><span data-stu-id="b90d2-162">This test was implemented as per Store policy.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-163">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-163">Test details</span></span>

<span data-ttu-id="b90d2-164">Für Windows Phone8.1-Apps wird mit dem Test geprüft, ob die Gesamtzahl der APPX-Pakete im Bündel kleiner als &lt; 512 ist, ob nur ein Hauptpaket im Bündel vorhanden ist und ob die Architektur des Hauptpakets im Bündel als ARM oder neutral gekennzeichnet ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-164">For Windows Phone 8.1 apps the test verifies the total number of appx packages in the bundle is &lt; 512, there is only one main package in the bundle, and that the architecture of the main package in the bundle is marked as ARM or neutral.</span></span>

<span data-ttu-id="b90d2-165">Für Windows10-Apps wird mit dem Test geprüft, ob die Revisionsnummer in der Version des Bündels auf 0 festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-165">For Windows 10 apps the test verifies that the revision number in the version of the bundle is set to 0.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-166">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-166">Corrective action</span></span>

<span data-ttu-id="b90d2-167">Stellen Sie sicher, dass App-Paket und -Bündel die weiter oben in den Testdetails angegebenen Anforderungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-167">Ensure the app package and bundle meet requirements above in Test details.</span></span>

## <a name="app-manifest-compliance-test"></a><span data-ttu-id="b90d2-168">Test der Erfüllung technischer Anforderungen für das App-Manifest</span><span class="sxs-lookup"><span data-stu-id="b90d2-168">App manifest compliance test</span></span>

<span data-ttu-id="b90d2-169">Überprüft die Inhalte des App-Manifests auf Korrektheit.</span><span class="sxs-lookup"><span data-stu-id="b90d2-169">Test the contents of app manifest to make sure its contents are correct.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-170">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-170">Background</span></span>

<span data-ttu-id="b90d2-171">Apps müssen ein korrekt formatiertes App-Manifest besitzen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-171">Apps must have a correctly formatted app manifest.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-172">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-172">Test details</span></span>

<span data-ttu-id="b90d2-173">Überprüft das App-Manifest, um sicherzustellen, dass der Inhalt der Beschreibung in den [App-Paketanforderungen](https://msdn.microsoft.com/library/windows/apps/Mt148525) entspricht.</span><span class="sxs-lookup"><span data-stu-id="b90d2-173">Examines the app manifest to verify the contents are correct as described in the [App package requirements](https://msdn.microsoft.com/library/windows/apps/Mt148525).</span></span>

-   **<span data-ttu-id="b90d2-174">Dateierweiterungen und Protokolle</span><span class="sxs-lookup"><span data-stu-id="b90d2-174">File extensions and protocols</span></span>**

    <span data-ttu-id="b90d2-175">Von der App können die Dateierweiterungen deklariert werden, die ihr zugeordnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-175">Your app can declare the file extensions that it wants to associate with.</span></span> <span data-ttu-id="b90d2-176">Bei nicht korrekter Verwendung wird von einer App u.U. eine große Anzahl von Dateierweiterungen deklariert, von denen die meisten nicht verwendet werden. Darunter leidet die Benutzerfreundlichkeit.</span><span class="sxs-lookup"><span data-stu-id="b90d2-176">Used improperly, an app can declare a large number of file extensions, most of which it may not even use, resulting in a bad user experience.</span></span> <span data-ttu-id="b90d2-177">Mit diesem Test wird eine Überprüfung der Anzahl von Dateierweiterungen durchgeführt, die einer App zugeordnet werden können.</span><span class="sxs-lookup"><span data-stu-id="b90d2-177">This test will add a check to limit the number of file extensions that an app can associate with.</span></span>

-   **<span data-ttu-id="b90d2-178">Frameworkabhängigkeitsregel</span><span class="sxs-lookup"><span data-stu-id="b90d2-178">Framework Dependency rule</span></span>**

    <span data-ttu-id="b90d2-179">Mit diesem Test wird die Anforderung durchgesetzt, dass für die Apps geeignete Abhängigkeiten von der UWP bestehen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-179">This test enforces the requirement that apps take appropriate dependencies on the UWP.</span></span> <span data-ttu-id="b90d2-180">Für den Test tritt ein Fehler auf, wenn eine unzulässige Abhängigkeit besteht.</span><span class="sxs-lookup"><span data-stu-id="b90d2-180">If there is an inappropriate dependency, this test will fail.</span></span>

    <span data-ttu-id="b90d2-181">Liegt ein Konflikt zwischen der Betriebssystemversion, in der die App verwendet wird, und den bestehenden Frameworkabhängigkeiten vor, schlägt der Test fehl.</span><span class="sxs-lookup"><span data-stu-id="b90d2-181">If there is a mismatch between the OS version the app applies to and the framework dependencies made, the test will fail.</span></span> <span data-ttu-id="b90d2-182">Der Test schlägt ebenfalls fehl, wenn sich die App auf eine Vorschauversion der Framework-DLLs bezieht.</span><span class="sxs-lookup"><span data-stu-id="b90d2-182">The test would also fail if the app refers to any preview versions of the framework dlls.</span></span>

-   **<span data-ttu-id="b90d2-183">Überprüfung der prozessübergreifenden Kommunikation (Inter-process Communication, IPC)</span><span class="sxs-lookup"><span data-stu-id="b90d2-183">Inter-process Communication (IPC) verification</span></span>**

    <span data-ttu-id="b90d2-184">Dieser Test setzt die Anforderung durch, dass WindowsStore-Apps außerhalb des App-Containers nicht mit Desktopkomponenten kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="b90d2-184">This test enforces the requirement that Windows Store apps do not communicate outside of the app container to Desktop components.</span></span> <span data-ttu-id="b90d2-185">Die prozessübergreifende Kommunikation ist nur für quergeladene Apps vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-185">Inter-process communication is intended for side-loaded apps only.</span></span> <span data-ttu-id="b90d2-186">Apps, die für [**ActivatableClassAttribute**](https://msdn.microsoft.com/library/windows/apps/BR211414) den Namen „DesktopApplicationPath“ angeben, bestehen diesen Test nicht.</span><span class="sxs-lookup"><span data-stu-id="b90d2-186">Apps that specify the [**ActivatableClassAttribute**](https://msdn.microsoft.com/library/windows/apps/BR211414) with name equal to "DesktopApplicationPath" will fail this test.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-187">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-187">Corrective action</span></span>

<span data-ttu-id="b90d2-188">Gleichen Sie das App-Manifest mit den [App-Paketanforderungen](https://msdn.microsoft.com/library/windows/apps/Mt148525) ab.</span><span class="sxs-lookup"><span data-stu-id="b90d2-188">Review the app's manifest against the requirements described in the [App package requirements](https://msdn.microsoft.com/library/windows/apps/Mt148525).</span></span>

## <a name="windows-security-features-test"></a><span data-ttu-id="b90d2-189">Test der Windows-Sicherheitsfeatures</span><span class="sxs-lookup"><span data-stu-id="b90d2-189">Windows Security features test</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-190">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-190">Background</span></span>

<span data-ttu-id="b90d2-191">Durch Ändern der standardmäßigen Windows-Sicherheitsvorkehrungen können Kunden einem erhöhten Risiko ausgesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-191">Changing the default Windows security protections can put customers at increased risk.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-192">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-192">Test details</span></span>

<span data-ttu-id="b90d2-193">Testet die Sicherheit der App durch Ausführen des [BinScope Binary Analyzers](#binscope-binary-analyzer-tests).</span><span class="sxs-lookup"><span data-stu-id="b90d2-193">Tests the app's security by running the [BinScope Binary Analyzer](#binscope-binary-analyzer-tests).</span></span>

<span data-ttu-id="b90d2-194">Bei den BinScope Binary Analyzer-Tests werden die Binärdateien der App auf Code- und Erstellungsmerkmale untersucht, die die App weniger anfällig für Angriffe oder für die Verwendung als Angriffsmittel machen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-194">The BinScope Binary Analyzer tests examine the app's binary files to check for coding and building practices that make the app less vulnerable to attack or to being used as an attack vector.</span></span>

<span data-ttu-id="b90d2-195">Die BinScope-Tests des Analyzers für Binärdateien prüfen, ob folgende sicherheitsrelevante Features korrekt verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="b90d2-195">The BinScope Binary Analyzer tests check for the correct use of the following security-related features.</span></span>

-   <span data-ttu-id="b90d2-196">BinScope-Tests des Analyzers für Binärdateien</span><span class="sxs-lookup"><span data-stu-id="b90d2-196">BinScope Binary Analyzer tests</span></span>
-   <span data-ttu-id="b90d2-197">Private Codesignatur</span><span class="sxs-lookup"><span data-stu-id="b90d2-197">Private Code Signing</span></span>

### <a name="binscope-binary-analyzer-tests"></a><span data-ttu-id="b90d2-198">BinScope-Tests des Analyzers für Binärdateien</span><span class="sxs-lookup"><span data-stu-id="b90d2-198">BinScope Binary Analyzer tests</span></span>

<span data-ttu-id="b90d2-199">Die [BinScope-Tests des Analyzers für Binärdateien](https://www.microsoft.com/en-us/download/details.aspx?id=44995) untersuchen die Binärdateien der App auf Code- und Erstellungsmerkmale, die die App weniger anfällig für Angriffe oder für die Verwendung als Angriffsmittel machen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-199">The [BinScope Binary Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=44995) tests examine the app's binary files to check for coding and building practices that make the app less vulnerable to attack or to being used as an attack vector.</span></span>

<span data-ttu-id="b90d2-200">Die BinScope-Tests des Analyzers für Binärdateien prüfen, ob die sicherheitsrelevanten Features korrekt verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="b90d2-200">The BinScope Binary Analyzer tests check for the correct use of these security-related features:</span></span>

-   [<span data-ttu-id="b90d2-201">AllowPartiallyTrustedCallersAttribute</span><span class="sxs-lookup"><span data-stu-id="b90d2-201">AllowPartiallyTrustedCallersAttribute</span></span>](#binscope-1)
-   [<span data-ttu-id="b90d2-202">/SafeSEH-Ausnahmebehandlungsschutz</span><span class="sxs-lookup"><span data-stu-id="b90d2-202">/SafeSEH Exception Handling Protection</span></span>](#binscope-2)
-   [<span data-ttu-id="b90d2-203">Datenausführungsverhinderung</span><span class="sxs-lookup"><span data-stu-id="b90d2-203">Data Execution Prevention</span></span>](#binscope-3)
-   [<span data-ttu-id="b90d2-204">Zufallsgestaltung des Adressraumlayouts</span><span class="sxs-lookup"><span data-stu-id="b90d2-204">Address Space Layout Randomization</span></span>](#binscope-4)
-   [<span data-ttu-id="b90d2-205">Lesen/Schreiben des freigegebenen PE-Abschnitts</span><span class="sxs-lookup"><span data-stu-id="b90d2-205">Read/Write Shared PE Section</span></span>](#binscope-5)
-   [<span data-ttu-id="b90d2-206">AppContainerCheck</span><span class="sxs-lookup"><span data-stu-id="b90d2-206">AppContainerCheck</span></span>](#appcontainercheck)
-   [<span data-ttu-id="b90d2-207">ExecutableImportsCheck</span><span class="sxs-lookup"><span data-stu-id="b90d2-207">ExecutableImportsCheck</span></span>](#binscope-7)
-   [<span data-ttu-id="b90d2-208">WXCheck</span><span class="sxs-lookup"><span data-stu-id="b90d2-208">WXCheck</span></span>](#binscope-8)

### <a name="span-idbinscope-1spanallowpartiallytrustedcallersattribute"></a><span data-ttu-id="b90d2-209"><span id="binscope-1"></span>AllowPartiallyTrustedCallersAttribute</span><span class="sxs-lookup"><span data-stu-id="b90d2-209"><span id="binscope-1"></span>AllowPartiallyTrustedCallersAttribute</span></span>

<span data-ttu-id="b90d2-210">**Fehlermeldung des Zertifizierungskits für Windows-Apps:** APTCACheck Test failed (Fehler beim APTCACheck-Test.)</span><span class="sxs-lookup"><span data-stu-id="b90d2-210">**Windows App Certification Kit error message:** APTCACheck Test failed</span></span>

<span data-ttu-id="b90d2-211">Das AllowPartiallyTrustedCallersAttribute-Attribut (kurz: APTCA-Attribut) ermöglicht den Zugriff auf vollständig vertrauenswürdigen Code aus teilweise vertrauenswürdigem Code in signierten Assemblys.</span><span class="sxs-lookup"><span data-stu-id="b90d2-211">The AllowPartiallyTrustedCallersAttribute (APTCA) attribute enables access to fully trusted code from partially trusted code in signed assemblies.</span></span> <span data-ttu-id="b90d2-212">Wenn Sie das APTCA-Attribut auf eine Assembly anwenden, können teilweise vertrauenswürdige Aufrufer diese Assembly aufrufen, solange die Assembly besteht. Dies kann ein Sicherheitsrisiko darstellen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-212">When you apply the APTCA attribute to an assembly, partially trusted callers can access that assembly for the life of the assembly, which can compromise security.</span></span>

**<span data-ttu-id="b90d2-213">Was ist zu tun, wenn die App den Test nicht besteht?</span><span class="sxs-lookup"><span data-stu-id="b90d2-213">What to do if your app fails this test</span></span>**

<span data-ttu-id="b90d2-214">Verwenden Sie das APTCA-Attribut nur dann für Assemblys mit starkem Namen, falls dies für das Projekt erforderlich ist und die Risiken bekannt sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-214">Don't use the APTCA attribute on strong named assemblies unless your project requires it and the risks are well understood.</span></span> <span data-ttu-id="b90d2-215">Falls das Attribut erforderlich ist, stellen Sie sicher, dass alle APIs durch geeignete Sicherheitsanforderungen für den Codezugriff geschützt sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-215">In cases where it's required, make sure that all APIs are protected with appropriate code access security demands.</span></span> <span data-ttu-id="b90d2-216">APTCA hat keine Auswirkung, wenn die Assembly Teil einer UWP-App (Universelle Windows-Plattform) ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-216">APTCA has no effect when the assembly is a part of a Universal Windows Platform (UWP) app.</span></span>

**<span data-ttu-id="b90d2-217">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="b90d2-217">Remarks</span></span>**

<span data-ttu-id="b90d2-218">Dieser Test wird nur für verwalteten Code (C#, .NET usw.) ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-218">This test is performed only on managed code (C#, .NET, etc.).</span></span>

### <a name="span-idbinscope-2spansafeseh-exception-handling-protection"></a><span data-ttu-id="b90d2-219"><span id="binscope-2"></span>/SafeSEH-Ausnahmebehandlungsschutz</span><span class="sxs-lookup"><span data-stu-id="b90d2-219"><span id="binscope-2"></span>/SafeSEH Exception Handling Protection</span></span>

<span data-ttu-id="b90d2-220">**Fehlermeldung des Zertifizierungskits für Windows-Apps:** SafeSEHCheck Test failed (Fehler beim SafeSEHCheck-Test).</span><span class="sxs-lookup"><span data-stu-id="b90d2-220">**Windows App Certification Kit error message:** SafeSEHCheck Test failed</span></span>

<span data-ttu-id="b90d2-221">Ein Ausnahmehandler wird ausgeführt, wenn in der App eine Ausnahmebedingung auftritt – beispielsweise bei einem Fehler aufgrund einer Division durch Null.</span><span class="sxs-lookup"><span data-stu-id="b90d2-221">An exception handler runs when the app encounters an exceptional condition, such as a divide-by-zero error.</span></span> <span data-ttu-id="b90d2-222">Da die Adresse des Ausnahmehandlers beim Aufrufen einer Funktion im Stapel gespeichert wird, besteht das Risiko eines Pufferüberlaufangriffs, sollte Schadsoftware den Stapel überschreiben.</span><span class="sxs-lookup"><span data-stu-id="b90d2-222">Because the address of the exception handler is stored on the stack when a function is called, it could be vulnerable to a buffer overflow attacker if some malicious software were to overwrite the stack.</span></span>

**<span data-ttu-id="b90d2-223">Was ist zu tun, wenn die App den Test nicht besteht?</span><span class="sxs-lookup"><span data-stu-id="b90d2-223">What to do if your app fails this test</span></span>**

<span data-ttu-id="b90d2-224">Aktivieren Sie beim Erstellen der App die Option "/SAFESEH" im Linker-Befehl.</span><span class="sxs-lookup"><span data-stu-id="b90d2-224">Enable the /SAFESEH option in the linker command when you build your app.</span></span> <span data-ttu-id="b90d2-225">Diese Option ist in den Veröffentlichungskonfigurationen von VisualStudio standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b90d2-225">This option is on by default in the Release configurations of Visual Studio.</span></span> <span data-ttu-id="b90d2-226">Vergewissern Sie sich, dass diese Option in den Erstellungsanweisungen für alle alle ausführbaren Module Ihrer App aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-226">Verify this option is enabled in the build instructions for all executable modules in your app.</span></span>

**<span data-ttu-id="b90d2-227">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="b90d2-227">Remarks</span></span>**

<span data-ttu-id="b90d2-228">Für 64-Bit-Binärdateien oder für Binärdateien für den ARM-Chipsatz wird dieser Test nicht ausgeführt, da hier keine Ausnahmehandleradressen im Stapel gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-228">The test is not performed on 64-bit binaries or ARM chipset binaries because they don't store exception handler addresses on the stack.</span></span>

### <a name="span-idbinscope-3spandata-execution-prevention"></a><span data-ttu-id="b90d2-229"><span id="binscope-3"></span>Datenausführungsverhinderung</span><span class="sxs-lookup"><span data-stu-id="b90d2-229"><span id="binscope-3"></span>Data Execution Prevention</span></span>

<span data-ttu-id="b90d2-230">**Fehlermeldung des Zertifizierungskits für Windows-Apps:** NXCheck Test failed (Fehler beim NXCheck-Test.)</span><span class="sxs-lookup"><span data-stu-id="b90d2-230">**Windows App Certification Kit error message:** NXCheck Test failed</span></span>

<span data-ttu-id="b90d2-231">Dieser Test stellt sicher, dass die App keinen Code ausführt, der in einem Datensegment gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-231">This test verifies that an app doesn't run code that is stored in a data segment.</span></span>

**<span data-ttu-id="b90d2-232">Was ist zu tun, wenn die App den Test nicht besteht?</span><span class="sxs-lookup"><span data-stu-id="b90d2-232">What to do if your app fails this test</span></span>**

<span data-ttu-id="b90d2-233">Aktivieren Sie beim Erstellen der App die Option „/NXCOMPAT“ im Linker-Befehl.</span><span class="sxs-lookup"><span data-stu-id="b90d2-233">Enable the /NXCOMPAT option in the linker command when you build your app.</span></span> <span data-ttu-id="b90d2-234">Diese Option ist in Linker-Versionen mit Unterstützung der Datenausführungsverhinderung (Data Execution Prevention, DEP) standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b90d2-234">This option is on by default in linker versions that support Data Execution Prevention (DEP).</span></span>

**<span data-ttu-id="b90d2-235">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="b90d2-235">Remarks</span></span>**

<span data-ttu-id="b90d2-236">Wir empfehlen, Apps auf einer DEP-fähigen CPU zu testen und alle DEP-bedingten Fehler zu beheben.</span><span class="sxs-lookup"><span data-stu-id="b90d2-236">We recommend that you test your apps on a DEP-capable CPU and fix any failures you find that result from DEP.</span></span>

### <a name="span-idbinscope-4spanaddress-space-layout-randomization"></a><span data-ttu-id="b90d2-237"><span id="binscope-4"></span>Zufallsgestaltung des Adressraumlayouts</span><span class="sxs-lookup"><span data-stu-id="b90d2-237"><span id="binscope-4"></span>Address Space Layout Randomization</span></span>

<span data-ttu-id="b90d2-238">**Fehlermeldung des Zertifizierungskits für Windows-Apps:** DBCheck Test failed (Fehler beim DBCheck-Test.)</span><span class="sxs-lookup"><span data-stu-id="b90d2-238">**Windows App Certification Kit error message:** DBCheck Test failed</span></span>

<span data-ttu-id="b90d2-239">Die Zufallsgestaltung des Adressraumlayouts (Address Space Layout Randomization, ASLR) lädt ausführbare Bilder in unvorhersehbare Speicherbereiche. Dadurch wird eine größere Hürde für Schadsoftware geschaffen, die erwartet, dass ein Programm an einer bestimmten virtuellen Adresse geladen wird.</span><span class="sxs-lookup"><span data-stu-id="b90d2-239">Address Space Layout Randomization (ASLR) loads executable images into unpredictable locations in memory, which makes it harder for malicious software that expects a program to be loaded at a certain virtual address to operate predictably.</span></span> <span data-ttu-id="b90d2-240">Ihre App und alle von der App verwendeten Komponenten müssen über ASLR-Unterstützung verfügen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-240">Your app and all components that your app uses must support ASLR.</span></span>

**<span data-ttu-id="b90d2-241">Was ist zu tun, wenn die App den Test nicht besteht?</span><span class="sxs-lookup"><span data-stu-id="b90d2-241">What to do if your app fails this test</span></span>**

<span data-ttu-id="b90d2-242">Aktivieren Sie beim Erstellen der App die Option "/DYNAMICBASE" im Linker-Befehl.</span><span class="sxs-lookup"><span data-stu-id="b90d2-242">Enable the /DYNAMICBASE option in the linker command when you build your app.</span></span> <span data-ttu-id="b90d2-243">Vergewissern Sie sich, dass auch alle von der App verwendeten Module diese Linker-Option verwenden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-243">Verify that all modules that your app uses also use this linker option.</span></span>

**<span data-ttu-id="b90d2-244">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="b90d2-244">Remarks</span></span>**

<span data-ttu-id="b90d2-245">ASLR hat in der Regel keine Auswirkungen auf die Leistung.</span><span class="sxs-lookup"><span data-stu-id="b90d2-245">Normally, ASLR doesn't affect performance.</span></span> <span data-ttu-id="b90d2-246">In einigen Szenarios ist auf 32-Bit-Systemen aber eine geringfügige Leistungsverbesserung zu beobachten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-246">But in some scenarios there is a slight performance improvement on 32-bit systems.</span></span> <span data-ttu-id="b90d2-247">Es ist möglich, dass sich die Leistung bei einem stark belasteten System verschlechtert, bei dem viele Bilder an vielen unterschiedlichen Speicherbereichen geladen sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-247">It is possible that performance could degrade in a highly congested system that have many images loaded in many different memory locations.</span></span>

<span data-ttu-id="b90d2-248">Dieser Test wird nur für Apps ausgeführt, die in verwaltetem Code geschrieben wurden, z.B. mit C# oder .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b90d2-248">This test is performed on only apps written in managed code, such as by using C# or .NET Framework.</span></span>

### <a name="span-idbinscope-5spanreadwrite-shared-pe-section"></a><span data-ttu-id="b90d2-249"><span id="binscope-5"></span>Lesen/Schreiben des freigegebenen PE-Abschnitts</span><span class="sxs-lookup"><span data-stu-id="b90d2-249"><span id="binscope-5"></span>Read/Write Shared PE Section</span></span>

<span data-ttu-id="b90d2-250">**Fehlermeldung des Zertifizierungskits für Windows-Apps:** SharedSectionsCheck Test failed (Fehler beim SharedSectionsCheck-Test).</span><span class="sxs-lookup"><span data-stu-id="b90d2-250">**Windows App Certification Kit error message:** SharedSectionsCheck Test failed.</span></span>

<span data-ttu-id="b90d2-251">Binärdateien mit beschreibbaren Abschnitten, die als freigegeben gekennzeichnet sind, stellen eine Sicherheitsbedrohung dar.</span><span class="sxs-lookup"><span data-stu-id="b90d2-251">Binary files with writable sections that are marked as shared are a security threat.</span></span> <span data-ttu-id="b90d2-252">Erstellen Sie keine Apps mit freigegebenen beschreibbaren Abschnitten, wenn dies nicht notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-252">Don't build apps with shared writable sections unless necessary.</span></span> <span data-ttu-id="b90d2-253">Verwenden Sie [**CreateFileMapping**](https://msdn.microsoft.com/library/windows/desktop/Aa366537) oder [**MapViewOfFile**](https://msdn.microsoft.com/library/windows/desktop/Aa366761), um ein freigegebenes Speicherobjekt zu erstellen, das korrekt gesichert ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-253">Use [**CreateFileMapping**](https://msdn.microsoft.com/library/windows/desktop/Aa366537) or [**MapViewOfFile**](https://msdn.microsoft.com/library/windows/desktop/Aa366761) to create a properly secured shared memory object.</span></span>

**<span data-ttu-id="b90d2-254">Was ist zu tun, wenn die App den Test nicht besteht?</span><span class="sxs-lookup"><span data-stu-id="b90d2-254">What to do if your app fails this test</span></span>**

<span data-ttu-id="b90d2-255">Entfernen Sie sämtliche freigegebenen Abschnitte aus der App, und erstellen Sie freigegebene Speicherobjekte, indem Sie [**CreateFileMapping**](https://msdn.microsoft.com/library/windows/desktop/Aa366537) oder [**MapViewOfFile**](https://msdn.microsoft.com/library/windows/desktop/Aa366761) mit den passenden Sicherheitsattributen aufrufen und die App dann neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-255">Remove any shared sections from the app and create shared memory objects by calling [**CreateFileMapping**](https://msdn.microsoft.com/library/windows/desktop/Aa366537) or [**MapViewOfFile**](https://msdn.microsoft.com/library/windows/desktop/Aa366761) with the proper security attributes and then rebuild your app.</span></span>

**<span data-ttu-id="b90d2-256">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="b90d2-256">Remarks</span></span>**

<span data-ttu-id="b90d2-257">Dieser Test wird nur für Apps ausgeführt, die in nicht verwalteten Sprachen geschrieben wurden, z.B. mit C oder C++.</span><span class="sxs-lookup"><span data-stu-id="b90d2-257">This test is performed only on apps written in unmanaged languages, such as by using C or C++.</span></span>

### <a name="appcontainercheck"></a><span data-ttu-id="b90d2-258">AppContainerCheck</span><span class="sxs-lookup"><span data-stu-id="b90d2-258">AppContainerCheck</span></span>

<span data-ttu-id="b90d2-259">**Fehlermeldung des Zertifizierungskits für Windows-Apps:** AppContainerCheck Test failed (Fehler beim AppContainerCheck-Test).</span><span class="sxs-lookup"><span data-stu-id="b90d2-259">**Windows App Certification Kit error message:** AppContainerCheck Test failed.</span></span>

<span data-ttu-id="b90d2-260">Der AppContainerCheck-Test prüft, ob das **appcontainer**-Bit im PE-Header einer ausführbaren Binärdatei gesetzt ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-260">The AppContainerCheck verifies that the **appcontainer** bit in the portable executable (PE) header of an executable binary is set.</span></span> <span data-ttu-id="b90d2-261">Für Apps muss das **appcontainer**-Bit für alle EXE-Dateien und nicht verwalteten DLLs gesetzt sein, damit diese korrekt ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-261">Apps must have the **appcontainer** bit set on all .exe files and all unmanaged DLLs to execute properly.</span></span>

**<span data-ttu-id="b90d2-262">Was ist zu tun, wenn die App den Test nicht besteht?</span><span class="sxs-lookup"><span data-stu-id="b90d2-262">What to do if your app fails this test</span></span>**

<span data-ttu-id="b90d2-263">Wenn der Test für eine systemeigene ausführbare Datei nicht erfolgreich ist, stellen Sie sicher, dass Sie zum Erstellen der Datei den aktuellen Compiler und Linker und für den Linker das Kennzeichen */appcontainer* verwenden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-263">If a native executable file fails the test, make sure that you used the latest compiler and linker to build the file and that you use the */appcontainer* flag on the linker.</span></span>

<span data-ttu-id="b90d2-264">Wenn der Test für eine verwaltete ausführbare Datei nicht erfolgreich ist, stellen Sie sicher, dass Sie zum Erstellen der WindowsStore-App den aktuellen Compiler und Linker wie beispielsweise Microsoft Visual Studio verwenden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-264">If a managed executable fails the test, make sure that you used the latest compiler and linker, such as Microsoft Visual Studio, to build the Windows Store app.</span></span>

**<span data-ttu-id="b90d2-265">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="b90d2-265">Remarks</span></span>**

<span data-ttu-id="b90d2-266">Dieser Test wird für alle EXE-Dateien und nicht verwalteten DLLs ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-266">This test is performed on all .exe files and on unmanaged DLLs.</span></span>

### <a name="span-idbinscope-7spanexecutableimportscheck"></a><span data-ttu-id="b90d2-267"><span id="binscope-7"></span>ExecutableImportsCheck</span><span class="sxs-lookup"><span data-stu-id="b90d2-267"><span id="binscope-7"></span>ExecutableImportsCheck</span></span>

<span data-ttu-id="b90d2-268">**Fehlermeldung des Zertifizierungskits für Windows-Apps:** ExecutableImportsCheck Test failed (Fehler beim ExecutableImportsCheck-Test).</span><span class="sxs-lookup"><span data-stu-id="b90d2-268">**Windows App Certification Kit error message:** ExecutableImportsCheck Test failed.</span></span>

<span data-ttu-id="b90d2-269">Ein portierbares ausführbares Image (Portable Executable, PE) besteht diesen Test nicht, wenn es in einen Abschnitt mit ausführbaren Code eingefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="b90d2-269">A portable executable (PE) image fails this test if its import table has been placed in an executable code section.</span></span> <span data-ttu-id="b90d2-270">Dies kann auftreten, wenn Sie für das PE-Image das Zusammenführen von „.rdata“ ermöglicht haben, indem Sie das Kennzeichen */merge* des Visual C++-Linkers auf */merge:.rdata=.text* festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="b90d2-270">This can occur if you enabled .rdata merging for the PE image by setting the */merge* flag of the Visual C++ linker as */merge:.rdata=.text*.</span></span>

**<span data-ttu-id="b90d2-271">Was ist zu tun, wenn die App den Test nicht besteht?</span><span class="sxs-lookup"><span data-stu-id="b90d2-271">What to do if your app fails this test</span></span>**

<span data-ttu-id="b90d2-272">Führen Sie die Importtabelle nicht in einem Abschnitt mit ausführbarem Code zusammen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-272">Don't merge the import table into an executable code section.</span></span> <span data-ttu-id="b90d2-273">Stellen Sie sicher, dass das Kennzeichen */merge* des Visual C++-Linkers nicht so eingestellt ist, dass der Abschnitt „.rdata“ in einem Codeabschnitt zusammengeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b90d2-273">Make sure that the */merge* flag of the Visual C++ linker is not set to merge the ".rdata" section into a code section.</span></span>

**<span data-ttu-id="b90d2-274">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="b90d2-274">Remarks</span></span>**

<span data-ttu-id="b90d2-275">Dieser Test wird für den gesamten Binärcode ausgeführt, außer für ausschließlich verwaltete Assemblys.</span><span class="sxs-lookup"><span data-stu-id="b90d2-275">This test is performed on all binary code except purely managed assemblies.</span></span>

### <a name="span-idbinscope-8spanwxcheck"></a><span data-ttu-id="b90d2-276"><span id="binscope-8"></span>WXCheck</span><span class="sxs-lookup"><span data-stu-id="b90d2-276"><span id="binscope-8"></span>WXCheck</span></span>

<span data-ttu-id="b90d2-277">**Fehlermeldung des Zertifizierungskits für Windows-Apps:** WXCheck Test failed (Fehler beim WXCheck-Test).</span><span class="sxs-lookup"><span data-stu-id="b90d2-277">**Windows App Certification Kit error message:** WXCheck Test failed.</span></span>

<span data-ttu-id="b90d2-278">Mit dieser Überprüfung können Sie sicherstellen, dass eine Binärdatei keine Seiten enthält, die als schreibbar und ausführbar gekennzeichnet sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-278">The check helps to ensure that a binary does not have any pages that are mapped as writable and executable.</span></span> <span data-ttu-id="b90d2-279">Dies kann vorkommen, wenn die Binärdatei einen schreibbaren und ausführbaren Abschnitt enthält oder wenn *SectionAlignment* der Binärdatei kleiner als *PAGE\-SIZE* ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-279">This can occur if the binary has a writable and executable section or if the binary’s *SectionAlignment* is less than *PAGE\-SIZE*.</span></span>

**<span data-ttu-id="b90d2-280">Was ist zu tun, wenn die App den Test nicht besteht?</span><span class="sxs-lookup"><span data-stu-id="b90d2-280">What to do if your app fails this test</span></span>**

<span data-ttu-id="b90d2-281">Stellen Sie sicher, dass die Binärdatei keinen schreibbaren oder ausführbaren Abschnitt enthält und dass der *SectionAlignment*-Wert der Binärdatei mindestens seiner *PAGE\-SIZE* entspricht.</span><span class="sxs-lookup"><span data-stu-id="b90d2-281">Make sure that the binary does not have a writeable or executable section and that the binary's *SectionAlignment* value is at least equal to its *PAGE\-SIZE*.</span></span>

**<span data-ttu-id="b90d2-282">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="b90d2-282">Remarks</span></span>**

<span data-ttu-id="b90d2-283">Dieser Test wird für alle EXE-Dateien und systemeigenen, nicht verwalteten DLLs ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-283">This test is performed on all .exe files and on native, unmanaged DLLs.</span></span>

<span data-ttu-id="b90d2-284">Eine ausführbare Datei kann einen schreibbaren und ausführbaren Abschnitt enthalten, wenn bei ihrer Erstellung "Bearbeiten und Fortfahren" aktiviert wurden (/ZI).</span><span class="sxs-lookup"><span data-stu-id="b90d2-284">An executable may have a writable and executable section if it has been built with Edit and Continue enabled (/ZI).</span></span> <span data-ttu-id="b90d2-285">Bei Deaktivierung von „Bearbeiten und Fortfahren“ ist der ungültige Abschnitt nicht mehr enthalten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-285">Disabling Edit and Continue will cause the invalid section to not be present.</span></span>

<span data-ttu-id="b90d2-286">*PAGE\-SIZE* ist der Standardwert von *SectionAlignment* für ausführbare Dateien.</span><span class="sxs-lookup"><span data-stu-id="b90d2-286">*PAGE\-SIZE* is the default *SectionAlignment* for executables.</span></span>

### <a name="private-code-signing"></a><span data-ttu-id="b90d2-287">Private Codesignatur</span><span class="sxs-lookup"><span data-stu-id="b90d2-287">Private Code Signing</span></span>

<span data-ttu-id="b90d2-288">Überprüft, ob innerhalb des App-Pakets Binärdateien für private Codesignaturen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-288">Tests for the existence of private code signing binaries within the app package.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-289">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-289">Background</span></span>

<span data-ttu-id="b90d2-290">Signaturdateien für privaten Code sollten privat bleiben, da sie im Fall einer Gefährdung zu bösartigen Zwecken missbraucht werden könnten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-290">Private code signing files should be kept private as they may be used for malicious purposes in the event they are compromised.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-291">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-291">Test details</span></span>

<span data-ttu-id="b90d2-292">Überprüft, ob innerhalb des App-Pakets Dateien mit der Erweiterung ".pfx" oder ".snk", die darauf hinweisen, dass private Signaturschlüssel verwendet wurden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-292">Tests for files within the app package that have an extension of .pfx or.snk that would indicate that private signing keys were included.</span></span>

### <a name="corrective-actions"></a><span data-ttu-id="b90d2-293">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-293">Corrective actions</span></span>

<span data-ttu-id="b90d2-294">Entfernen Sie alle Signaturschlüssel für privaten Code (z.B. PFX- und SNK-Dateien) aus dem Paket.</span><span class="sxs-lookup"><span data-stu-id="b90d2-294">Remove any private code signing keys (e.g. .pfx and .snk files) from the package.</span></span>

## <a name="supported-api-test"></a><span data-ttu-id="b90d2-295">Test der unterstützten APIs</span><span class="sxs-lookup"><span data-stu-id="b90d2-295">Supported API test</span></span>

<span data-ttu-id="b90d2-296">Testet die App, um festzustellen, ob nicht kompatible APIs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-296">Test the app for the use of any non-compliant APIs.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-297">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-297">Background</span></span>

<span data-ttu-id="b90d2-298">Apps müssen die APIs für Windows Store-Apps verwenden (Windows-Runtime- oder unterstützte Win32-APIs), um für den Windows Store zertifiziert zu werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-298">Apps must use the APIs for Windows Store apps (Windows Runtime or supported Win32 APIs) to be certified for the Windows Store.</span></span> <span data-ttu-id="b90d2-299">Dieser Test ermittelt auch Situationen, in denen eine verwaltete Binärdatei eine Abhängigkeit von einer Funktion außerhalb des genehmigten Profils aufweist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-299">This test also identifies situations where a managed binary takes a dependency on a function outside of the approved profile.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-300">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-300">Test details</span></span>

-   <span data-ttu-id="b90d2-301">Es wird sichergestellt, dass die im App-Paket enthaltenen Binärdateien nicht über Abhängigkeiten von einer Win32-API verfügen, die für die Entwicklung von Windows Store-Apps nicht unterstützt wird. Dazu wird jeweils die Importadressentabelle der Binärdatei überprüft.</span><span class="sxs-lookup"><span data-stu-id="b90d2-301">Verifies that each binary within the app package doesn't have a dependency on a Win32 API that is not supported for Windows Store app development by checking the import address table of the binary.</span></span>
-   <span data-ttu-id="b90d2-302">Stellt sicher, dass eine verwaltete Binärdatei des App-Pakets keine Abhängigkeit von einer Funktion außerhalb des genehmigten Profils aufweist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-302">Verifies that each managed binary within the app package doesn't have a dependency on a function outside of the approved profile.</span></span>

### <a name="corrective-actions"></a><span data-ttu-id="b90d2-303">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-303">Corrective actions</span></span>

<span data-ttu-id="b90d2-304">Stellen Sie sicher, dass die App als Releasebuild und nicht als Debugbuild kompiliert wurde.</span><span class="sxs-lookup"><span data-stu-id="b90d2-304">Make sure that the app was compiled as a release build and not a debug build.</span></span>

> <span data-ttu-id="b90d2-305">**Hinweis**  Der Debugbuild einer App besteht diesen Test nicht, auch wenn die App nur [APIs für Windows Store-Apps](https://msdn.microsoft.com/library/windows/apps/xaml/bg124285.aspx) verwendet.</span><span class="sxs-lookup"><span data-stu-id="b90d2-305">**Note**  The debug build of an app will fail this test even if the app uses only [APIs for Windows Store apps](https://msdn.microsoft.com/library/windows/apps/xaml/bg124285.aspx).</span></span>

<span data-ttu-id="b90d2-306">Prüfen Sie die Fehlermeldungen, um die von der App verwendete API zu identifizieren, die keine [API für Windows Store-Apps](https://msdn.microsoft.com/library/windows/apps/xaml/bg124285.aspx) ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-306">Review the error messages to identify the API the app uses that is not an [API for Windows Store apps](https://msdn.microsoft.com/library/windows/apps/xaml/bg124285.aspx).</span></span>

> <span data-ttu-id="b90d2-307">**Hinweis**  C++-Apps, die unter einer Debugkonfiguration erstellt wurden, bestehen diesen Test nicht. Dies gilt auch, wenn für die Konfiguration nur APIs aus dem Windows SDK für Windows Store-Apps verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-307">**Note**  C++ apps that are built in a debug configuration will fail this test even if the configuration only uses APIs from the Windows SDK for Windows Store apps.</span></span> <span data-ttu-id="b90d2-308">Weitere Informationen finden Sie unter [Alternativen zu Windows-APIs in Windows Store-Apps](http://go.microsoft.com/fwlink/p/?LinkID=244022).</span><span class="sxs-lookup"><span data-stu-id="b90d2-308">See, [Alternatives to Windows APIs in Windows Store apps](http://go.microsoft.com/fwlink/p/?LinkID=244022) for more info.</span></span>

## <a name="performance-tests"></a><span data-ttu-id="b90d2-309">Leistungstests</span><span class="sxs-lookup"><span data-stu-id="b90d2-309">Performance tests</span></span>

<span data-ttu-id="b90d2-310">Die App muss schnell auf Benutzerinteraktionen und Systembefehle reagieren, um Benutzern eine schnelle und flüssige Benutzeroberfläche zu bieten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-310">The app must respond quickly to user interaction and system commands in order to present a fast and fluid user experience.</span></span>

<span data-ttu-id="b90d2-311">Die Merkmale des Computers, auf dem der Test ausgeführt wird, können die Testergebnisse beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-311">The characteristics of the computer on which the test is performed can influence the test results.</span></span> <span data-ttu-id="b90d2-312">Die Schwellenwerte des Leistungstests für die App-Zertifizierung sind so festgelegt, dass Computer mit geringem Energieverbrauch die Erwartungen der Kunden an eine schnelle und flüssige Benutzeroberfläche erfüllen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-312">The performance test thresholds for app certification are set such that low-power computers meet the customer’s expectation of a fast and fluid experience.</span></span> <span data-ttu-id="b90d2-313">Um die Leistung Ihrer App zu ermitteln, empfehlen wir, die App auf einem PC mit geringem Energieverbrauch (z.B. einem PC mit Intel Atom-Prozessor) bei einer Auflösung von mindestens 1366x768 und mit einem herkömmlichen Festplattenlaufwerk (im Gegensatz zu einem Festkörperlaufwerk) zu testen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-313">To determine your app’s performance, we recommend that you test on a low-power computer, such as an Intel Atom processor-based computer with a screen resolution of 1366x768 (or higher) and a rotational hard drive (as opposed to a solid-state hard drive).</span></span>

### <a name="bytecode-generation"></a><span data-ttu-id="b90d2-314">Generierung von Bytecode</span><span class="sxs-lookup"><span data-stu-id="b90d2-314">Bytecode generation</span></span>

<span data-ttu-id="b90d2-315">Als Leistungsoptimierungsmaßnahme zum Beschleunigen der JavaScript-Ausführungszeit wird von JavaScript-Dateien mit JS-Erweiterung Bytecode generiert, wenn die App bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="b90d2-315">As a performance optimization to accelerate JavaScript execution time, JavaScript files ending in the .js extension generate bytecode when the app is deployed.</span></span> <span data-ttu-id="b90d2-316">Für JavaScript-Vorgänge können die Zeiträume für den Startvorgang und die laufende Ausführung so erheblich verkürzt werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-316">This significantly improves startup and ongoing execution times for JavaScript operations.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-317">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-317">Test Details</span></span>

<span data-ttu-id="b90d2-318">Die App-Bereitstellung wird daraufhin überprüft, ob alle JS-Dateien in Bytecode konvertiert wurden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-318">Checks the app deployment to verify that all .js files have been converted to bytecode.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-319">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-319">Corrective Action</span></span>

<span data-ttu-id="b90d2-320">Wenn bei diesem Test Fehler ermittelt werden, sollten Sie bei der Behandlung dieses Problems folgende Schritte berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="b90d2-320">If this test fails, consider the following when addressing the issue:</span></span>

-   <span data-ttu-id="b90d2-321">Stellen Sie sicher, dass die Ereignisprotokollierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-321">Verify that event logging is enabled.</span></span>
-   <span data-ttu-id="b90d2-322">Stellen Sie sicher, dass alle JavaScript-Dateien in Bezug auf die Syntax gültig sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-322">Verify that all JavaScript files are syntactically valid.</span></span>
-   <span data-ttu-id="b90d2-323">Vergewissern Sie sich, dass alle vorherigen Versionen der App deinstalliert wurden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-323">Confirm that all previous versions of the app are uninstalled.</span></span>
-   <span data-ttu-id="b90d2-324">Schließen Sie die identifizierten Dateien aus dem App-Paket aus.</span><span class="sxs-lookup"><span data-stu-id="b90d2-324">Exclude identified files from the app package.</span></span>

### <a name="optimized-binding-references"></a><span data-ttu-id="b90d2-325">Optimierte Bindungsverweise</span><span class="sxs-lookup"><span data-stu-id="b90d2-325">Optimized binding references</span></span>

<span data-ttu-id="b90d2-326">Beim Verwenden von Bindungen sollte WinJS.Binding.optimizeBindingReferences auf "true" festgelegt werden, um die Speicherauslastung zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="b90d2-326">When using bindings, WinJS.Binding.optimizeBindingReferences should be set to true in order to optimize memory usage.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-327">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-327">Test Details</span></span>

<span data-ttu-id="b90d2-328">Überprüfen Sie den Wert von "WinJS.Binding.optimizeBindingReferences".</span><span class="sxs-lookup"><span data-stu-id="b90d2-328">Verify the value of WinJS.Binding.optimizeBindingReferences.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-329">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-329">Corrective Action</span></span>

<span data-ttu-id="b90d2-330">Legen Sie „WinJS.Binding.optimizeBindingReferences“ im JavaScript der App auf **true** fest.</span><span class="sxs-lookup"><span data-stu-id="b90d2-330">Set WinJS.Binding.optimizeBindingReferences to **true** in the app JavaScript.</span></span>

## <a name="app-manifest-resources-test"></a><span data-ttu-id="b90d2-331">Test der App-Manifestressourcen</span><span class="sxs-lookup"><span data-stu-id="b90d2-331">App manifest resources test</span></span>

### <a name="app-resources-validation"></a><span data-ttu-id="b90d2-332">App-Ressourcenüberprüfung</span><span class="sxs-lookup"><span data-stu-id="b90d2-332">App resources validation</span></span>

<span data-ttu-id="b90d2-333">Die App wird ggf. nicht installiert, wenn die im App-Manifest deklarierten Zeichenfolgen oder Bilder falsch sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-333">The app might not install if the strings or images declared in your app’s manifest are incorrect.</span></span> <span data-ttu-id="b90d2-334">Wenn die App mit diesen Fehlern installiert wird, werden das Logo der App oder andere von der App verwendete Bilder möglicherweise nicht richtig angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-334">If the app does install with these errors, your app’s logo or other images used by your app might not display correctly.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-335">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-335">Test Details</span></span>

<span data-ttu-id="b90d2-336">Prüft die im App-Manifest definierten Ressourcen, um sicherzustellen, dass sie vorhanden und gültig sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-336">Inspects the resources defined in the app manifest to make sure they are present and valid.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-337">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-337">Corrective Action</span></span>

<span data-ttu-id="b90d2-338">Orientieren Sie sich an der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="b90d2-338">Use the following table as guidance.</span></span>

<table>
<tr><th><span data-ttu-id="b90d2-339">Fehlermeldung</span><span class="sxs-lookup"><span data-stu-id="b90d2-339">Error message</span></span></th><th><span data-ttu-id="b90d2-340">Kommentare</span><span class="sxs-lookup"><span data-stu-id="b90d2-340">Comments</span></span></th></tr>
<tr><td>
<p><span data-ttu-id="b90d2-341">Das Bild "{Bildname}" definiert sowohl einen Scale- als auch einen TargetSize-Qualifizierer. Es darf jedoch jeweils nur ein Qualifizierer definiert sein.</span><span class="sxs-lookup"><span data-stu-id="b90d2-341">The image {image name} defines both Scale and TargetSize qualifiers; you can define only one qualifier at a time.</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-342">Sie können Bilder für unterschiedliche Auflösungen anpassen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-342">You can customize images for different resolutions.</span></span></p>
<p><span data-ttu-id="b90d2-343">In der tatsächlichen Meldung enthält „{image name}“ den Namen des Bilds mit dem Fehler.</span><span class="sxs-lookup"><span data-stu-id="b90d2-343">In the actual message, {image name} contains the name of the image with the error.</span></span></p>
<p> <span data-ttu-id="b90d2-344">Stellen Sie sicher, dass für jedes Bild entweder „Scale” oder „TargetSize” als Qualifizierer definiert ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-344">Make sure that each image defines either Scale or TargetSize as the qualifier.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-345">Das Bild "{Bildname}" überschreitet die Größenbeschränkung von {Größenangabe}.</span><span class="sxs-lookup"><span data-stu-id="b90d2-345">The image {image name} failed the size restrictions.</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-346">Stellen Sie sicher, dass alle Bilder der App den Größenbeschränkungen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-346">Ensure that all the app images adhere to the proper size restrictions.</span></span></p>
<p><span data-ttu-id="b90d2-347">In der tatsächlichen Meldung enthält „{Bildname}“ den Namen des Bilds mit dem Fehler.</span><span class="sxs-lookup"><span data-stu-id="b90d2-347">In the actual message, {image name} contains the name of the image with the error.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-348">Das Bild "{Bildname}" fehlt im Paket.</span><span class="sxs-lookup"><span data-stu-id="b90d2-348">The image {image name} is missing from the package.</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-349">Ein erforderliches Bild fehlt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-349">A required image is missing.</span></span></p>
<p><span data-ttu-id="b90d2-350">In der tatsächlichen Meldung enthält "{Bildname}“ den Namen des fehlenden Bilds.</span><span class="sxs-lookup"><span data-stu-id="b90d2-350">In the actual message, {image name} contains the name of the image that is missing.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-351">Das Bild "{Bildname}" ist keine gültige Bilddatei.</span><span class="sxs-lookup"><span data-stu-id="b90d2-351">The image {image name} is not a valid image file.</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-352">Stellen Sie sicher, dass alle Bilder der App den Einschränkungen für Dateiformattypen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-352">Ensure that all the app images adhere to the proper file format type restrictions.</span></span></p>
<p><span data-ttu-id="b90d2-353">In der tatsächlichen Meldung enthält „{image name}“ den Namen des ungültigen Bilds.</span><span class="sxs-lookup"><span data-stu-id="b90d2-353">In the actual message, {image name} contains the name of the image that is not valid.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-354">Das Bild „BadgeLogo“ enthält einen ungültigen ABGR-Wert {value} an der Position (x, y).</span><span class="sxs-lookup"><span data-stu-id="b90d2-354">The image "BadgeLogo" has an ABGR value {value} at position (x, y) that is not valid.</span></span> <span data-ttu-id="b90d2-355">Das Pixel muss weiß (##FFFFFF) oder transparent (00######) sein.</span><span class="sxs-lookup"><span data-stu-id="b90d2-355">The pixel must be white (##FFFFFF) or transparent (00######)</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-356">Das Signallogo ist ein Bild, das neben der Signalbenachrichtigung angezeigt wird, um die App auf dem Sperrbildschirm zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="b90d2-356">The badge logo is an image that appears next to the badge notification to identify the app on the lock screen.</span></span> <span data-ttu-id="b90d2-357">Dieses Bild muss einfarbig sein (es darf nur weiße und transparente Pixel enthalten).</span><span class="sxs-lookup"><span data-stu-id="b90d2-357">This image must be monochromatic (it can contain only white and transparent pixels).</span></span></p>
<p><span data-ttu-id="b90d2-358">In der tatsächlichen Meldung enthält {Wert} den Namen des ungültigen Farbwerts im Bild.</span><span class="sxs-lookup"><span data-stu-id="b90d2-358">In the actual message, {value} contains the color value in the image that is not valid.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-359">Das Bild „BadgeLogo“ enthält einen ABGR-Wert {Wert} an der Position (x, y), der für ein Bild mit hohem Kontrast (Weiß) ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-359">The image "BadgeLogo" has an ABGR value {value} at position (x, y) that is not valid for a high-contrast white image.</span></span> <span data-ttu-id="b90d2-360">Das Pixel muss (##2A2A2A) oder dunkler oder transparent (00######) sein.</span><span class="sxs-lookup"><span data-stu-id="b90d2-360">The pixel must be (##2A2A2A) or darker, or transparent (00######).</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-361">Das Signallogo ist ein Bild, das neben der Signalbenachrichtigung angezeigt wird, um die App auf dem Sperrbildschirm zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="b90d2-361">The badge logo is an image that appears next to the badge notification to identify the app on the lock screen.</span></span>   <span data-ttu-id="b90d2-362">Da das Signallogo bei hohem Kontrast (Weiß) auf einem weißen Hintergrund angezeigt wird, muss es sich um eine dunkle Version des normalen Signallogos handeln.</span><span class="sxs-lookup"><span data-stu-id="b90d2-362">Because the badge logo  appears on a white background when in high-contrast white, it must be a dark version of the normal badge logo.</span></span> <span data-ttu-id="b90d2-363">Bei hohem Kontrast (Weiß) darf das Signallogo nur Pixel enthalten, die dunkler als (##2A2A2A) oder transparent sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-363">In high-contrast white, the badge logo can only contain pixels that are darker than (##2A2A2A) or transparent.</span></span></p>
<p><span data-ttu-id="b90d2-364">In der tatsächlichen Meldung enthält {Wert} den Namen des ungültigen Farbwerts im Bild.</span><span class="sxs-lookup"><span data-stu-id="b90d2-364">In the actual message, {value} contains the color value in the image that is not valid.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-365">Für das Bild muss mindestens eine Variante ohne TargetSize-Qualifizierer definiert sein.</span><span class="sxs-lookup"><span data-stu-id="b90d2-365">The image must define at least one variant without a TargetSize qualifier.</span></span> <span data-ttu-id="b90d2-366">Sie müssen einen Scale-Qualifizierer definieren oder „Scale” und „TargetSize” nicht angeben. In diesem Fall wird „Scale-100” verwendet.</span><span class="sxs-lookup"><span data-stu-id="b90d2-366">It must define a Scale qualifier or leave Scale and TargetSize unspecified, which defaults to Scale-100.</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-367">Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/apps/xaml/dn958435.aspx">Reaktionsfähiges Design für UWP-Apps (Universelle Windows-Plattform) – Grundlagen</a> und <a href="https://msdn.microsoft.com/library/windows/apps/xaml/hh465241.aspx">Richtlinien für App-Ressourcen</a>.</span><span class="sxs-lookup"><span data-stu-id="b90d2-367">For more info, see <a href="https://msdn.microsoft.com/library/windows/apps/xaml/dn958435.aspx">Responsive design 101 for UWP apps</a> and <a href="https://msdn.microsoft.com/library/windows/apps/xaml/hh465241.aspx">Guidelines for app resources</a>.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-368">Das Paket enthält keine Datei „resources.pri”.</span><span class="sxs-lookup"><span data-stu-id="b90d2-368">The package is missing a "resources.pri" file.</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-369">Wenn das App-Manifest lokalisierbaren Inhalt enthält, müssen Sie sicherstellen, dass das Paket der App eine gültige Datei „resources.pri“ enthält.</span><span class="sxs-lookup"><span data-stu-id="b90d2-369">If you have localizable content in your app manifest, make sure that your app's package includes a valid resources.pri file.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-370">Die Datei „resources.pri“ muss eine Ressourcenzuordnung enthalten, bei der der Name dem Paketnamen „{vollständiger Paketname}“ entspricht.</span><span class="sxs-lookup"><span data-stu-id="b90d2-370">The "resources.pri" file must contain a resource map with a name that matches the package name  {package full name}</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-371">Dieser Fehler wird angezeigt, wenn das Manifest geändert wird und der Name der Ressourcenzuordnung in „resources.pri“ dem Paketnamen im Manifest nicht mehr entspricht.</span><span class="sxs-lookup"><span data-stu-id="b90d2-371">You can get this error if the manifest changed and  the name of the resource map in resources.pri no longer matches the package name in the manifest.</span></span></p>
<p><span data-ttu-id="b90d2-372">In der tatsächlichen Meldung enthält „{vollständiger Paketname}“ den Paketnamen, den „resources.pri“ enthalten muss.</span><span class="sxs-lookup"><span data-stu-id="b90d2-372">In the actual message, {package full name} contains the package name that resources.pri must contain.</span></span></p>
<p><span data-ttu-id="b90d2-373">Um diesen Fehler zu beheben, müssen Sie die Datei „resources.pri“ neu erstellen. Am besten erstellen Sie dazu das App-Paket neu.</span><span class="sxs-lookup"><span data-stu-id="b90d2-373">To fix this, you need to rebuild resources.pri and the easiest way to do that is  by rebuilding the app's package.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-374">Für die Datei „resources.pri“ darf „Automatisch zusammenführen“ nicht aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="b90d2-374">The "resources.pri" file must not have AutoMerge enabled.</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-375">„MakePRI.exe“ unterstützt eine Option mit dem Namen <strong>AutoMerge</strong>.</span><span class="sxs-lookup"><span data-stu-id="b90d2-375">MakePRI.exe supports an option called <strong>AutoMerge</strong>.</span></span> <span data-ttu-id="b90d2-376">Der Standardwert von <strong>AutoMerge</strong> ist <strong>Aus</strong>.</span><span class="sxs-lookup"><span data-stu-id="b90d2-376">The default value of <strong>AutoMerge</strong> is <strong>off</strong>.</span></span> <span data-ttu-id="b90d2-377">Ist sie aktiviert, führt <strong>AutoMerge</strong> die App-Sprachpaketressourcen in einer einzelnen Datei „resources.pri“ zur Laufzeit zusammen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-377">When enabled, <strong>AutoMerge</strong> merges an app's  language pack resources into a single resources.pri at runtime.</span></span> <span data-ttu-id="b90d2-378">Für Apps, die Sie über den Windows Store vertreiben möchten, wird dies nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-378">We don't recommend this for apps that you intend to distribute through  the Windows Store.</span></span> <span data-ttu-id="b90d2-379">Die Datei „resources.pri“ einer über den Windows Store vertriebenen Windows Store-App muss sich im Stammverzeichnis des App-Pakets befinden und alle von der App unterstützten Sprachverweise enthalten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-379">The resources.pri of an app that is distributed through the  Windows Store must be in  the root of the app's package and contain all the language references that the app supports.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-380">Die Zeichenfolge „{string}“ entspricht nicht der Längenbeschränkung von maximal {number} Zeichen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-380">The string {string} failed the max length restriction of {number} characters.</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-381">Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/apps/xaml/mt148525.aspx">App-Paketanforderungen</a>.</span><span class="sxs-lookup"><span data-stu-id="b90d2-381">Refer to the <a href="https://msdn.microsoft.com/library/windows/apps/xaml/mt148525.aspx">App package requirements</a>.</span></span></p>
<p><span data-ttu-id="b90d2-382">In der tatsächlichen Meldung wird „{string}“ durch die Zeichenfolge mit dem Fehler ersetzt, und {number} enthält die maximale Länge.</span><span class="sxs-lookup"><span data-stu-id="b90d2-382">In the actual message, {string} is replaced by the string with the error and {number} contains the maximum length.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-383">Die Zeichenfolge „{string}“ darf keine führenden/nachgestellten Leerzeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-383">The string {string} must not have leading/trailing whitespace.</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-384">Das Schema für die Elemente im App-Manifest lässt führende oder nachgestellte Leerzeichen nicht zu.</span><span class="sxs-lookup"><span data-stu-id="b90d2-384">The schema for the elements in the app manifest don't allow leading or trailing white space characters.</span></span></p>
<p><span data-ttu-id="b90d2-385">In der tatsächlichen Meldung wird „{string}“ durch die Zeichenfolge mit dem Fehler ersetzt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-385">In the actual message, {string} is replaced by the string with the error.</span></span></p>
<p><span data-ttu-id="b90d2-386">Stellen Sie sicher, dass keiner der lokalisierten Werte der Manifestfelder in „resources.pri“ führende oder nachgestellte Leerzeichen enthält.</span><span class="sxs-lookup"><span data-stu-id="b90d2-386">Make sure that none of the localized values of the manifest fields in resources.pri have leading or trailing white space characters.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-387">Die Zeichenfolge darf nicht leer sein (Länge größer 0 (null)).</span><span class="sxs-lookup"><span data-stu-id="b90d2-387">The string must be non-empty (greater than zero in length)</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-388">Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/apps/xaml/mt148525.aspx">App-Paketanforderungen</a>.</span><span class="sxs-lookup"><span data-stu-id="b90d2-388">For more info, see <a href="https://msdn.microsoft.com/library/windows/apps/xaml/mt148525.aspx">App package requirements</a>.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-389">In der Datei „resources.pri” ist keine Standardressource angegeben.</span><span class="sxs-lookup"><span data-stu-id="b90d2-389">There is no default resource specified in the "resources.pri" file.</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-390">Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/apps/xaml/hh465241.aspx">Richtlinien für App-Ressourcen</a>.</span><span class="sxs-lookup"><span data-stu-id="b90d2-390">For more info, see <a href="https://msdn.microsoft.com/library/windows/apps/xaml/hh465241.aspx">Guidelines for app resources</a>.</span></span></p>
<p><span data-ttu-id="b90d2-391">In der Standardbuildkonfiguration nimmt Visual Studio nur Bildressourcen mit der Skalierung 200% in das App-Paket auf, wenn ein Bündel generiert wird, andere Ressourcen werden im Ressourcenpaket abgelegt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-391">In the default build configuration,  Visual Studio only includes scale-200 image resources in the app package when generating bundles, putting other resources in the resource package.</span></span> <span data-ttu-id="b90d2-392">Stellen Sie sicher, dass Sie entweder Bildressourcen mit der Skalierung 200% einschließen oder Ihr Projekt für die Aufnahme der vorhandenen Ressourcen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="b90d2-392">Make sure  you either include scale-200 image resources or configure your project to include the resources you have.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-393">In der Datei „resources.pri“ ist kein Ressourcenwert angegeben.</span><span class="sxs-lookup"><span data-stu-id="b90d2-393">There is no resource value specified in the "resources.pri" file.</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-394">Stellen Sie sicher, dass für das App-Manifest gültige Ressourcen in „resources.pri“ definiert sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-394">Make sure that the app manifest has valid resources defined in resources.pri.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-395">Die Bilddatei „{Dateiname}“ muss kleiner als 204.800Bytes sein.\*\*</span><span class="sxs-lookup"><span data-stu-id="b90d2-395">The image file {filename} must be smaller than 204800 bytes.\*\*</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-396">Verringern Sie die Größe der angegebenen Bilder.</span><span class="sxs-lookup"><span data-stu-id="b90d2-396">Reduce the size of the indicated images.</span></span></p>
</td></tr>
<tr><td>
<p><span data-ttu-id="b90d2-397">Die Datei „{Dateiname}“ darf keinen Abschnitt mit umgekehrter Zuordnung enthalten.\*\*</span><span class="sxs-lookup"><span data-stu-id="b90d2-397">The {filename} file must not contain a reverse map section.\*\*</span></span></p>
</td><td>
<p><span data-ttu-id="b90d2-398">Die umgekehrte Zuordnung wird zwar während des Debuggens mit F5 in VisualStudio beim Aufrufen von „makepri.exe“ generiert, sie kann jedoch entfernt werden, indem „makepri.exe“ beim Generieren einer PRI-Datei ohne den Parameter „/m“ ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b90d2-398">While the reverse map is generated during Visual Studio 'F5 debugging' when calling into makepri.exe, it can be removed by running makepri.exe without the /m parameter when generating a pri file.</span></span></p>
</td></tr>
<tr><td colspan="2">
<p><span data-ttu-id="b90d2-399">\*\* bedeutet, dass der Version3.3 des Zertifizierungskits für Windows-Apps für Windows 8.1 ein Test hinzugefügt wurde, der nur bei der Verwendung dieser oder einer höheren Version des Kits anwendbar ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-399">\*\* Indicates that a test was added in the Windows App Certification Kit 3.3 for Windows 8.1 and is only applicable when using the that version of the kit or later.</span></span></p>
</td></tr>
</table>



 

### <a name="branding-validation"></a><span data-ttu-id="b90d2-400">Branding-Validierung</span><span class="sxs-lookup"><span data-stu-id="b90d2-400">Branding validation</span></span>

<span data-ttu-id="b90d2-401">Windows Store-Apps sollten vollständig und betriebsbereit sein.</span><span class="sxs-lookup"><span data-stu-id="b90d2-401">Windows Store apps are expected to be complete and fully functional.</span></span> <span data-ttu-id="b90d2-402">Apps, für die Standardbilder (aus Vorlagen oder SDK-Beispielen) verwendet werden, verfügen über eine schlechte Benutzeroberfläche und können im Store-Katalog nicht leicht identifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-402">Apps using the default images (from templates or SDK samples) present a poor user experience and cannot be easily identified in the store catalog.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-403">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-403">Test Details</span></span>

<span data-ttu-id="b90d2-404">Bei diesem Test wird sichergestellt, dass die von der App verwendeten Bilder keine Standardbilder aus SDK-Beispielen oder aus VisualStudio sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-404">The test will validate if the images used by the app are not default images either from SDK samples or from Visual Studio.</span></span>

### <a name="corrective-actions"></a><span data-ttu-id="b90d2-405">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-405">Corrective actions</span></span>

<span data-ttu-id="b90d2-406">Ersetzen Sie Standardbilder durch eigene Bilder, die über Aussagekraft für Ihre App verfügen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-406">Replace default images with something more distinct and representative of your app.</span></span>

## <a name="debug-configuration-test"></a><span data-ttu-id="b90d2-407">Test der Debugkonfiguration</span><span class="sxs-lookup"><span data-stu-id="b90d2-407">Debug configuration test</span></span>

<span data-ttu-id="b90d2-408">Testet die App, um sicherzustellen, dass es sich nicht um einen Debugbuild handelt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-408">Test the app to make sure it is not a debug build.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-409">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-409">Background</span></span>

<span data-ttu-id="b90d2-410">Um für den Windows Store zertifiziert zu werden, dürfen Apps nicht zum Debuggen kompiliert werden und nicht auf die Debugversionen einer ausführbaren Datei verweisen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-410">To be certified for the Windows Store, apps must not be compiled for debug and they must not reference debug versions of an executable file.</span></span> <span data-ttu-id="b90d2-411">Darüber hinaus müssen Sie den Code für die App optimiert erstellen, damit dieser Test bestanden wird.</span><span class="sxs-lookup"><span data-stu-id="b90d2-411">In addition, you must build your code as optimized for your app to pass this test.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-412">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-412">Test details</span></span>

<span data-ttu-id="b90d2-413">Testen Sie die App, um sicherzustellen, dass es sich nicht um einen Debugbuild handelt und dass die App mit keinen Debugframeworks verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-413">Test the app to make sure it is not a debug build and is not linked to any debug frameworks.</span></span>

### <a name="corrective-actions"></a><span data-ttu-id="b90d2-414">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-414">Corrective actions</span></span>

-   <span data-ttu-id="b90d2-415">Erstellen Sie die App als Veröffentlichungsbuild, bevor Sie die App an den Windows Store übermitteln.</span><span class="sxs-lookup"><span data-stu-id="b90d2-415">Build the app as a release build before you submit it to the Windows Store.</span></span>
-   <span data-ttu-id="b90d2-416">Stellen Sie sicher, dass Sie die richtige .NET Framework-Version installiert haben.</span><span class="sxs-lookup"><span data-stu-id="b90d2-416">Make sure that you have the correct version of .NET framework installed.</span></span>
-   <span data-ttu-id="b90d2-417">Stellen Sie sicher, dass die App nicht über Links zu Debugversionen eines Frameworks verfügt und dass die Erstellung mit einer Releaseversion erfolgt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-417">Make sure the app isn't linking to debug versions of a framework and that it is building with a release version.</span></span> <span data-ttu-id="b90d2-418">Wenn diese App .NET-Komponenten enthält, sollten Sie sich vergewissern, dass Sie die richtige Version des .NET-Frameworks installiert haben.</span><span class="sxs-lookup"><span data-stu-id="b90d2-418">If this app contains .NET components, make sure that you have installed the correct version of the .NET framework.</span></span>

## <a name="file-encoding-test"></a><span data-ttu-id="b90d2-419">Test der Dateicodierung</span><span class="sxs-lookup"><span data-stu-id="b90d2-419">File encoding test</span></span>

### <a name="utf-8-file-encoding"></a><span data-ttu-id="b90d2-420">UTF-8-Dateicodierung</span><span class="sxs-lookup"><span data-stu-id="b90d2-420">UTF-8 file encoding</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-421">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-421">Background</span></span>

<span data-ttu-id="b90d2-422">HTML-, CSS- und JavaScript-Dateien müssen im UTF-8-Format codiert sein und über eine entsprechende Bytereihenfolgemarke (BOM) verfügen, um von der Bytecode-Zwischenspeicherung profitieren und bestimmte Laufzeitfehlerbedingungen vermeiden zu können.</span><span class="sxs-lookup"><span data-stu-id="b90d2-422">HTML, CSS, and JavaScript files must be encoded in UTF-8 form with a corresponding byte-order mark (BOM) to benefit from bytecode caching and avoid certain runtime error conditions.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-423">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-423">Test details</span></span>

<span data-ttu-id="b90d2-424">Testet den Inhalt der App-Pakete, um sicherzustellen, dass darin die richtige Dateicodierung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b90d2-424">Test the contents of app packages to make sure that they use the correct file encoding.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-425">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-425">Corrective Action</span></span>

<span data-ttu-id="b90d2-426">Öffnen Sie die betroffene Datei, und wählen Sie in Visual Studio im Menü **Datei** die Option **Speichern unter**.</span><span class="sxs-lookup"><span data-stu-id="b90d2-426">Open the affected file and select **Save As** from the **File** menu in Visual Studio.</span></span> <span data-ttu-id="b90d2-427">Wählen Sie neben der Schaltfläche **Speichern** das Dropdownsteuerelement aus, und wählen Sie **Mit Codierung speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="b90d2-427">Select the drop-down control next to the **Save** button and select **Save with Encoding**.</span></span> <span data-ttu-id="b90d2-428">Wählen Sie im Dialogfeld mit den erweiterten Speicheroptionen die Option **Unicode (UTF-8 mit Signatur)** aus, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="b90d2-428">From the **Advanced** save options dialog, choose the Unicode (UTF-8 with signature) option and click **OK**.</span></span>

## <a name="direct3d-feature-level-test"></a><span data-ttu-id="b90d2-429">Test der Direct3D-Featureebene</span><span class="sxs-lookup"><span data-stu-id="b90d2-429">Direct3D feature level test</span></span>

### <a name="direct3d-feature-level-support"></a><span data-ttu-id="b90d2-430">Test auf Unterstützung der Direct3D-Featureebene</span><span class="sxs-lookup"><span data-stu-id="b90d2-430">Direct3D feature level support</span></span>

<span data-ttu-id="b90d2-431">Testet MicrosoftDirect3D-Apps, um sicherzustellen, dass sie auf Geräten mit älterer Grafikhardware nicht abstürzen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-431">Tests Microsoft Direct3D apps to ensure that they won't crash on devices with older graphics hardware.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-432">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-432">Background</span></span>

<span data-ttu-id="b90d2-433">Für den Windows Store ist es erforderlich, dass alle Anwendungen mit Direct3D bei Grafikkarten der Featureebene9\-1 richtig gerendert bzw. ordnungsgemäß beendet werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-433">Windows Store requires all applications using Direct3D to render properly or fail gracefully on feature level 9\-1 graphics cards.</span></span>

<span data-ttu-id="b90d2-434">Da die Benutzer die Grafikhardware ihrer Geräte nach der Installation der App ändern können, muss Ihre App für den Fall, dass Sie eine Featureebene höher als 9\-1 verwenden, beim Start erkennen, ob die aktuelle Hardware die Mindestanforderungen erfüllt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-434">Because users can change the graphics hardware in their device after the app is installed, if you choose a minimum feature level higher than 9\-1, your app must detect at launch whether or not the current hardware meets the minimum requirements.</span></span> <span data-ttu-id="b90d2-435">Wenn die Mindestanforderungen nicht erfüllt sind, muss Ihre App dem Benutzer eine Meldung mit den Direct3D-Anforderungen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-435">If the minimum requirements are not met, the app must display a message to the user detailing the Direct3D requirements.</span></span> <span data-ttu-id="b90d2-436">Wird zudem eine App auf ein Gerät heruntergeladen, mit dem sie nicht kompatibel ist, sollte sie dies beim Start erkennen und dem Kunden eine Meldung bezüglich der erforderlichen Voraussetzungen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-436">Also, if an app is downloaded on a device with which it is not compatible, it should detect that at launch and display a message to the customer detailing the requirements.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-437">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-437">Test Details</span></span>

<span data-ttu-id="b90d2-438">Bei diesem Test wird überprüft, ob Apps unter der Featureebene9\-1 richtig gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-438">The test will validate if the apps render accurately on feature level 9\-1.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-439">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-439">Corrective Action</span></span>

<span data-ttu-id="b90d2-440">Stellen Sie sicher, dass die App unter der Direct3D-Featureebene9\-1 richtig gerendert wird. Dies gilt auch, wenn die App für die Ausführung auf einer höheren Featureebene bestimmt ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-440">Ensure that your app renders correctly on Direct3D feature level 9\-1, even if you expect it to run at a higher feature level.</span></span> <span data-ttu-id="b90d2-441">Weitere Informationen finden Sie unter [Entwickeln für unterschiedliche Direct3D-Featureebenen](http://go.microsoft.com/fwlink/p/?LinkID=253575).</span><span class="sxs-lookup"><span data-stu-id="b90d2-441">See [Developing for different Direct3D feature levels](http://go.microsoft.com/fwlink/p/?LinkID=253575) for more info.</span></span>

### <a name="direct3d-trim-after-suspend"></a><span data-ttu-id="b90d2-442">Direct3D-Kürzung nach dem Anhalten</span><span class="sxs-lookup"><span data-stu-id="b90d2-442">Direct3D Trim after suspend</span></span>

> <span data-ttu-id="b90d2-443">**Hinweis**  Dieser Test gilt nur für Windows Store-Apps, die für Windows8.1 und höher entwickelt wurden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-443">**Note**  This test only applies to Windows Store apps developed for Windows 8.1 and later.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-444">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-444">Background</span></span>

<span data-ttu-id="b90d2-445">Wenn von der App auf ihrem jeweiligen Direct3D-Gerät [**Trim**](https://msdn.microsoft.com/library/windows/desktop/Dn280346) nicht aufgerufen wird, gibt sie keinen Speicher frei, der für die vorherigen 3D-Arbeitsschritte zugeordnet wurde.</span><span class="sxs-lookup"><span data-stu-id="b90d2-445">If the app does not call [**Trim**](https://msdn.microsoft.com/library/windows/desktop/Dn280346) on its Direct3D device, the app will not release memory allocated for its earlier 3D work.</span></span> <span data-ttu-id="b90d2-446">Dies erhöht das Risiko, dass Apps aufgrund von unzureichendem Systemspeicher beendet werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-446">This increases the risk of apps being terminated due to system memory pressure.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-447">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-447">Test Details</span></span>

<span data-ttu-id="b90d2-448">Apps werden auf die Einhaltung der d3d-Anforderungen überprüft. Außerdem wird sichergestellt, dass Apps beim Anhalterückruf (Suspend) eine neue [**Trim**](https://msdn.microsoft.com/library/windows/desktop/Dn280346)-API aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-448">Checks apps for compliance with d3d requirements and ensures that apps are calling a new [**Trim**](https://msdn.microsoft.com/library/windows/desktop/Dn280346) API upon their Suspend callback.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-449">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-449">Corrective Action</span></span>

<span data-ttu-id="b90d2-450">Von der App sollte die [**Trim**](https://msdn.microsoft.com/library/windows/desktop/Dn280346)-API für ihre [**IDXGIDevice3**](https://msdn.microsoft.com/library/windows/desktop/Dn280345)-Schnittstelle vor jedem Anhaltevorgang aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-450">The app should call the [**Trim**](https://msdn.microsoft.com/library/windows/desktop/Dn280346) API on its [**IDXGIDevice3**](https://msdn.microsoft.com/library/windows/desktop/Dn280345) interface anytime it is about to be suspended.</span></span>

## <a name="app-capabilities-test"></a><span data-ttu-id="b90d2-451">Test der App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="b90d2-451">App Capabilities test</span></span>

### <a name="special-use-capabilities"></a><span data-ttu-id="b90d2-452">Sonderfunktionen</span><span class="sxs-lookup"><span data-stu-id="b90d2-452">Special use capabilities</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-453">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-453">Background</span></span>

<span data-ttu-id="b90d2-454">Sonderfunktionen sind für sehr spezielle Szenarien vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-454">Special use capabilities are intended for very specific scenarios.</span></span> <span data-ttu-id="b90d2-455">Diese Funktionen dürfen nur mit Unternehmenskonten genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-455">Only company accounts are allowed to use these capabilities.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-456">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-456">Test Details</span></span>

<span data-ttu-id="b90d2-457">Es wird überprüft, ob von der App die folgenden Funktionen deklariert werden:</span><span class="sxs-lookup"><span data-stu-id="b90d2-457">Validate if the app is declaring any of the below capabilities:</span></span>

-   <span data-ttu-id="b90d2-458">EnterpriseAuthentication</span><span class="sxs-lookup"><span data-stu-id="b90d2-458">EnterpriseAuthentication</span></span>
-   <span data-ttu-id="b90d2-459">SharedUserCertificates</span><span class="sxs-lookup"><span data-stu-id="b90d2-459">SharedUserCertificates</span></span>
-   <span data-ttu-id="b90d2-460">DocumentsLibrary</span><span class="sxs-lookup"><span data-stu-id="b90d2-460">DocumentsLibrary</span></span>

<span data-ttu-id="b90d2-461">Falls eine oder mehrere dieser Funktionen deklariert werden, wird Benutzern während des Tests eine Warnung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-461">If any of these capabilities are declared, the test will display a warning to the user.</span></span>

### <a name="corrective-actions"></a><span data-ttu-id="b90d2-462">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-462">Corrective Actions</span></span>

<span data-ttu-id="b90d2-463">Sie können erwägen, die Sonderfunktion zu entfernen, wenn diese für die App nicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-463">Consider removing the special use capability if your app doesn't require it.</span></span> <span data-ttu-id="b90d2-464">Die Verwendung dieser Funktionen unterliegt außerdem einer weiteren Prüfung anhand der Richtlinie für die Aufnahme.</span><span class="sxs-lookup"><span data-stu-id="b90d2-464">Additionally, use of these capabilities are subject to additional on-boarding policy review.</span></span>
<!--TODO: after migrating dev-packaging, link to [if your app doesn't require it](dev-packaging.app-capability-declarations#special-and-restricted-capabilities)-->

## <a name="windows-runtime-metadata-validation"></a><span data-ttu-id="b90d2-465">Windows-Runtime-Metadatenvalidierung</span><span class="sxs-lookup"><span data-stu-id="b90d2-465">Windows Runtime metadata validation</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-466">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-466">Background</span></span>

<span data-ttu-id="b90d2-467">Es wird sichergestellt, dass die Komponenten, die als Teil einer App mitgeliefert werden, mit dem UWP-Typsystem kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-467">Ensures that the components that ship in an app conform to the UWP type system.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-468">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-468">Test Details</span></span>

<span data-ttu-id="b90d2-469">Es wird überprüft, ob die **WINMD**-Dateien im Paket den UWP-Regeln entsprechen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-469">Verifies that the **.winmd** files in the package conform to UWP rules.</span></span>

### <a name="corrective-actions"></a><span data-ttu-id="b90d2-470">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-470">Corrective Actions</span></span>

-   <span data-ttu-id="b90d2-471">**ExclusiveTo-Attributtest:** Stellen Sie sicher, dass von UWP-Klassen keine Schnittstellen implementiert werden, die für eine andere Klasse als „ExclusiveTo” gekennzeichnet sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-471">**ExclusiveTo attribute test:** Ensure that UWP classes don't implement interfaces that are marked as ExclusiveTo another class.</span></span>
-   <span data-ttu-id="b90d2-472">**Test auf Anordnung von Typen:** Stellen Sie sicher, dass die Metadaten für alle UWP-Typen in der WINMD-Datei enthalten sind, die im App-Paket über den längsten Namen mit Namespaceübereinstimmung verfügt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-472">**Type location test:** Ensure that the metadata for all UWP types is located in the winmd file that has the longest namespace-matching name in the app package.</span></span>
-   <span data-ttu-id="b90d2-473">**Test auf Groß-/Kleinschreibung von Typnamen:** Stellen Sie sicher, dass alle UWP-Typen im App-Paket eindeutige Namen aufweisen, bei denen die Groß-/Kleinschreibung nicht zu berücksichtigen ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-473">**Type name case-sensitivity test:** Ensure that all UWP types have unique, case-insensitive names within your app package.</span></span> <span data-ttu-id="b90d2-474">Vergewissern Sie sich außerdem, dass UWP-Typnamen im App-Paket nicht auch als Namespacename verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-474">Also ensure that no UWP type name is also used as a namespace name within your app package.</span></span>
-   <span data-ttu-id="b90d2-475">**Test auf Korrektheit des Typnamens:** Stellen Sie sicher, dass im globalen Namespace oder im Windows-Namespace der obersten Ebene keine UWP-Typen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-475">**Type name correctness test:** Ensure there are no UWP types in the global namespace or in the Windows top-level namespace.</span></span>
-   <span data-ttu-id="b90d2-476">**Test auf Korrektheit der allgemeinen Metadaten:** Stellen Sie sicher, dass der zum Generieren der Typen verwendete Compiler in Bezug auf die UWP-Spezifikationen auf dem neuesten Stand ist.</span><span class="sxs-lookup"><span data-stu-id="b90d2-476">**General metadata correctness test:** Ensure that the compiler you are using to generate your types is up to date with the UWP specifications.</span></span>
-   <span data-ttu-id="b90d2-477">**Eigenschaftentest:** Stellen Sie sicher, dass alle Eigenschaften einer UWP-Klasse über eine get-Methode verfügen (set-Methoden sind optional).</span><span class="sxs-lookup"><span data-stu-id="b90d2-477">**Properties test:** ensure that all properties on a UWP class have a get method (set methods are optional).</span></span> <span data-ttu-id="b90d2-478">Vergewissern Sie sich, dass der Typ des Rückgabewerts der get-Methode für alle Eigenschaften von UWP-Typen jeweils mit dem Typ des Eingabeparameters der set-Methode übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-478">Ensure that the type of the get method return value matches the type of the set method input parameter, for all properties on UWP types.</span></span>

## <a name="package-sanity-tests"></a><span data-ttu-id="b90d2-479">Tests für die Paketintegrität</span><span class="sxs-lookup"><span data-stu-id="b90d2-479">Package Sanity tests</span></span>

### <a name="platform-appropriate-files-test"></a><span data-ttu-id="b90d2-480">Test auf für Plattform geeignete Dateien</span><span class="sxs-lookup"><span data-stu-id="b90d2-480">Platform appropriate files test</span></span>

<span data-ttu-id="b90d2-481">Apps, von denen gemischte Binärdateien installiert werden, stürzen je nach der Prozessorarchitektur von Benutzern möglicherweise ab oder werden nicht richtig ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b90d2-481">Apps that install mixed binaries may crash or not run correctly depending upon the user’s processor architecture.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-482">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-482">Background</span></span>

<span data-ttu-id="b90d2-483">Bei diesem Test werden die Binärdateien in einem App-Paket auf Architekturkonflikte geprüft.</span><span class="sxs-lookup"><span data-stu-id="b90d2-483">This test validates the binaries in an app package for architecture conflicts.</span></span> <span data-ttu-id="b90d2-484">Ein App-Paket sollte keine Binärdateien enthalten, die unter der im Manifest angegebenen Prozessorarchitektur nicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="b90d2-484">An app package should not include binaries that can't be used on the processor architecture specified in the manifest.</span></span> <span data-ttu-id="b90d2-485">Das Einfügen von nicht unterstützten Binärdateien kann zum Absturz der App oder zu einem unnötigen Anstieg der Paketgröße einer App führen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-485">Including unsupported binaries can lead to your app crashing or an unnecessary increase in the app package size.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-486">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-486">Test Details</span></span>

<span data-ttu-id="b90d2-487">Es wird überprüft, ob die Bitanzahl jeder einzelnen Datei im PE-Header korrekt ist, wenn Querverweise mit der Prozessorarchitekturdeklaration des App-Pakets eingerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-487">Validates that each file's "bitness" in the PE header is appropriate when cross-referenced with the app package processor architecture declaration</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-488">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-488">Corrective Action</span></span>

<span data-ttu-id="b90d2-489">Befolgen Sie diese Richtlinien, um sicherzustellen, dass Ihr App-Paket nur Dateien enthält, die von der im App-Manifest angegebenen Architektur unterstützt werden:</span><span class="sxs-lookup"><span data-stu-id="b90d2-489">Follow these guidelines to ensure that your app package only contains files supported by the architecture specified in the app manifest:</span></span>

-   <span data-ttu-id="b90d2-490">Wenn die Zielprozessorarchitektur der App den Prozessortyp "Neutral" aufweist, kann die App keine x86-, x64- oder ARM-Binärdateien oder -Abbilddateien enthalten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-490">If the Target Processor Architecture for your app is Neutral processor Type, the app package cannot contain x86, x64, or ARM binary or image type files.</span></span>

-   <span data-ttu-id="b90d2-491">Wenn die Zielprozessorarchitektur der App den Prozessortyp "x86" aufweist, darf das App-Paket nur x86-Binärdateien oder -Abbilddateien enthalten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-491">If the Target Processor Architecture for your app is x86 processor type, the app package must only contain x86 binary or image type files.</span></span> <span data-ttu-id="b90d2-492">Wenn das Paket x64- oder ARM-Binärtypen oder -Imagetypen enthält, tritt beim Test ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="b90d2-492">If the package contains x64 or ARM binary or image types, it will fail the test.</span></span>

-   <span data-ttu-id="b90d2-493">Wenn die Zielprozessorarchitektur der App den Prozessortyp "x64" aufweist, muss das App-Paket x64-Binärdateien oder -Abbilddateien enthalten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-493">If the Target Processor Architecture for your app is x64 processor type, the app package must contain x64 binary or image type files.</span></span> <span data-ttu-id="b90d2-494">Beachten Sie, dass das Paket in diesem Fall auch x86-Dateien enthalten kann. Für die Hauptoberfläche der App sollte jedoch die x64-Binärdatei genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-494">Note that in this case the package can also include x86 files, but the primary app experience should utilize the x64 binary.</span></span>

    <span data-ttu-id="b90d2-495">Falls das Paket jedoch ARM-Binärdateien oder -Abbilddateien oder ausschließlich x86-Binärdateien oder -Abbilddateien enthält, tritt beim Test ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="b90d2-495">However, if the package contains ARM binary or image type files, or only contains x86 binaries or image type files, it will fail the test.</span></span>

-   <span data-ttu-id="b90d2-496">Wenn die Zielprozessorarchitektur der App den Prozessortyp "ARM" aufweist, darf das App-Paket nur ARM-Binärdateien oder -Abbilddateien enthalten.</span><span class="sxs-lookup"><span data-stu-id="b90d2-496">If the Target Processor Architecture for your app is ARM processor type, the app package must only contain ARM binary or image type files.</span></span> <span data-ttu-id="b90d2-497">Wenn das Paket x64- oder x86-Binärdateien oder -Abbilddateien enthält, tritt beim Test ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="b90d2-497">If the package contains x64 or x86 binary or image type files, it will fail the test.</span></span>

### <a name="supported-directory-structure-test"></a><span data-ttu-id="b90d2-498">Test der unterstützten Verzeichnisstruktur</span><span class="sxs-lookup"><span data-stu-id="b90d2-498">Supported Directory Structure test</span></span>

<span data-ttu-id="b90d2-499">Es wird sichergestellt, dass von Anwendungen während der Installation keine Unterverzeichnisse erstellt werden, die länger als MAX\-PATH sind.</span><span class="sxs-lookup"><span data-stu-id="b90d2-499">Validates that applications are not creating subdirectories as part of installation that are longer than MAX\-PATH.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-500">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-500">Background</span></span>

<span data-ttu-id="b90d2-501">Komponenten des Betriebssystems (z.B. Trident, WWAHost usw.) sind für Dateisystempfade intern auf den MAX\-PATH-Wert begrenzt und funktionieren nicht ordnungsgemäß, wenn längere Pfade verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-501">OS components (including Trident, WWAHost, etc.) are internally limited to MAX\-PATH for file system paths and will not work correctly for longer paths.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-502">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-502">Test Details</span></span>

<span data-ttu-id="b90d2-503">Es wird überprüft, ob für Pfade im Installationsverzeichnis der App der MAX\-PATH-Wert überschritten wird.</span><span class="sxs-lookup"><span data-stu-id="b90d2-503">Verifies that no path within the app install directory exceeds MAX\-PATH.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-504">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-504">Corrective Action</span></span>

<span data-ttu-id="b90d2-505">Verwenden Sie eine kürzere Verzeichnisstruktur bzw. kürzere Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-505">Use a shorter directory structure, and or file name.</span></span>

## <a name="resource-usage-test"></a><span data-ttu-id="b90d2-506">Test für die Ressourcennutzung</span><span class="sxs-lookup"><span data-stu-id="b90d2-506">Resource Usage test</span></span>

### <a name="winjs-background-task-test"></a><span data-ttu-id="b90d2-507">Test der WinJS-Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="b90d2-507">WinJS Background Task test</span></span>

<span data-ttu-id="b90d2-508">Mit dem Test der WinJS-Hintergrundaufgabe wird sichergestellt, dass JavaScript-Apps über die richtigen close-Anweisungen verfügen, damit die Apps nicht unnötig Akkuenergie verbrauchen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-508">WinJS background task test ensures that JavaScript apps have the proper close statements so apps don’t consume battery.</span></span>

### <a name="background"></a><span data-ttu-id="b90d2-509">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="b90d2-509">Background</span></span>

<span data-ttu-id="b90d2-510">Apps mit JavaScript-Hintergrundaufgaben müssen "Close()" als letzte Anweisung der Hintergrundaufgabe aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b90d2-510">Apps that have JavaScript background tasks need to call Close() as the last statement in their background task.</span></span> <span data-ttu-id="b90d2-511">Ist dies bei Apps nicht der Fall, kann das System unter Umständen nicht in den verbundenen Standbymodus zurückkehren, was zu einer schnelleren Entleerung des Akkus führen kann.</span><span class="sxs-lookup"><span data-stu-id="b90d2-511">Apps that do not do this could keep the system from returning to connected standby mode and result in draining the battery.</span></span>

### <a name="test-details"></a><span data-ttu-id="b90d2-512">Testdetails</span><span class="sxs-lookup"><span data-stu-id="b90d2-512">Test Details</span></span>

<span data-ttu-id="b90d2-513">Wenn für Apps im Manifest keine Hintergrundaufgabe angegeben ist, gilt der Test als bestanden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-513">If the app does not have a background task file specified in the manifest, the test will pass.</span></span> <span data-ttu-id="b90d2-514">Andernfalls wird beim Testen die JavaScript-Hintergrundaufgabendatei analysiert, die im App-Paket angegeben ist, und nach einer Close()-Anweisung gesucht.</span><span class="sxs-lookup"><span data-stu-id="b90d2-514">Otherwise the test will parse the JavaScript background task file that is specified in the app package, and look for a Close() statement.</span></span> <span data-ttu-id="b90d2-515">Wird diese gefunden, gilt der Test als bestanden. Falls nicht, gilt der Test als nicht bestanden.</span><span class="sxs-lookup"><span data-stu-id="b90d2-515">If found, the test will pass; otherwise the test will fail.</span></span>

### <a name="corrective-action"></a><span data-ttu-id="b90d2-516">Maßnahmen</span><span class="sxs-lookup"><span data-stu-id="b90d2-516">Corrective Action</span></span>

<span data-ttu-id="b90d2-517">Aktualisieren Sie den JavaScript-Hintergrundcode so, dass „Close()” richtig aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b90d2-517">Update the background JavaScript code to call Close() correctly.</span></span>

> <span data-ttu-id="b90d2-518">**Hinweis**  Dieser Artikel ist für Windows10-Entwickler gedacht, die UWP-Apps schreiben.</span><span class="sxs-lookup"><span data-stu-id="b90d2-518">**Note**  This article is for Windows 10 developers writing UWP apps.</span></span> <span data-ttu-id="b90d2-519">Wenn Sie für Windows8.x oder Windows Phone8.x entwickeln, finden Sie Informationen dazu in der [archivierten Dokumentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span><span class="sxs-lookup"><span data-stu-id="b90d2-519">If you’re developing for Windows 8.x or Windows Phone 8.x, see the [archived documentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span></span>

## <a name="related-topics"></a><span data-ttu-id="b90d2-520">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b90d2-520">Related topics</span></span>

* [<span data-ttu-id="b90d2-521">Tests für Windows Desktop-Brücke-Apps</span><span class="sxs-lookup"><span data-stu-id="b90d2-521">Windows Desktop Bridge app tests</span></span>](windows-desktop-bridge-app-tests.md)
* [<span data-ttu-id="b90d2-522">WindowsStore-Richtlinien</span><span class="sxs-lookup"><span data-stu-id="b90d2-522">Windows Store Policies</span></span>](https://msdn.microsoft.com/library/windows/apps/Dn764944)
 
