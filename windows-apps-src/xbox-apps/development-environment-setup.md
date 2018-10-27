---
author: Mtoepke
title: Einrichten der Umgebung für die UWP-Entwicklung auf Xbox
description: Schritte zum Einrichten und Testen der Umgebung für die UWP-Entwicklung auf Xbox
ms.author: scotmi
ms.date: 02/08/2017
ms.topic: article
keywords: windows 10, uwp
ms.assetid: 8801c0d9-94a5-41a2-bec3-14f523d230df
ms.localizationpriority: medium
ms.openlocfilehash: 2234b7d39f130da03562176f0df878701d524635
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5702734"
---
# <a name="set-up-your-uwp-on-xbox-development-environment"></a><span data-ttu-id="6875f-104">Einrichten der UWP-Entwicklungsumgebung auf Xbox</span><span class="sxs-lookup"><span data-stu-id="6875f-104">Set up your UWP on Xbox development environment</span></span>

<span data-ttu-id="6875f-105">Die Umgebung für die UWP-Entwicklung (Universelle Windows-Plattform) auf Xbox besteht aus einem Entwicklungscomputer, der über ein lokales Netzwerk mit einer Xbox One-Konsole verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="6875f-105">The Universal Windows Platform (UWP) on Xbox development environment consists of a development PC connected to an Xbox One console through a local network.</span></span>
<span data-ttu-id="6875f-106">Der Entwicklungscomputer erfordert Windows 10, Visual Studio 2017 oder Visual Studio 2015 Update 3, Windows 10 SDK Build 14393 oder neuer und eine Reihe von Unterstützungstools.</span><span class="sxs-lookup"><span data-stu-id="6875f-106">The development PC requires Windows 10, Visual Studio 2017 or Visual Studio 2015 Update 3, the Windows 10 SDK build 14393 or later, and a range of supporting tools.</span></span>


<span data-ttu-id="6875f-107">In diesem Artikel werden die Schritte zum Einrichten und Testen der Entwicklungsumgebung beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6875f-107">This article covers the steps to set up and test your development environment.</span></span>

## <a name="visual-studio-setup"></a><span data-ttu-id="6875f-108">Einrichten von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6875f-108">Visual Studio setup</span></span>

1. <span data-ttu-id="6875f-109">Installieren Sie Visual Studio 2017 oder Visual Studio 2015 Update 3, die neueste Version von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6875f-109">Install Visual Studio 2017, Visual Studio 2015 Update 3, or the latest release of Visual Studio.</span></span> <span data-ttu-id="6875f-110">Weitere Informationen und Downloads für die Installation finden Sie unter [Downloads und Tools für Windows 10](https://dev.windows.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="6875f-110">For more information and to install, see [Downloads and tools for Windows 10](https://dev.windows.com/downloads).</span></span> <span data-ttu-id="6875f-111">Es wird empfohlen, dass Sie die neueste Version von Visual Studio verwenden, damit Sie die neuesten Updates für Entwickler und Sicherheit erhalten können.</span><span class="sxs-lookup"><span data-stu-id="6875f-111">We recommend that you use the latest version of Visual Studio so that you can recieve the latest updates for developers and security.</span></span>

2. <span data-ttu-id="6875f-112">Wenn Sie Visual Studio2017 erneut installieren, stellen Sie sicher, dass Sie die Arbeitsauslastung **Entwicklung für die universelle Windows-Plattform** auswählen.</span><span class="sxs-lookup"><span data-stu-id="6875f-112">If you're installing Visual Studio 2017, make sure that you choose the **Universal Windows Platform development** workload.</span></span> <span data-ttu-id="6875f-113">Wenn Sie ein C++-Entwickler sind, stellen Sie sicher, dass Sie auch das Kontrollkästchen \*\* 	UWP-Tools für C++\*\* im Bereich **Zusammenfassung** rechts unter **Entwicklung für die universelle Windows-Plattform** wählen.</span><span class="sxs-lookup"><span data-stu-id="6875f-113">If you're a C++ developer, make sure that you also select the **C++ Universal Windows Platform tools** checkbox in the **Summary** pane on the right, under **Universal Windows Platform development**.</span></span> <span data-ttu-id="6875f-114">Es ist nicht Teil der Standardinstallation.</span><span class="sxs-lookup"><span data-stu-id="6875f-114">It's not part of the default installation.</span></span>

    ![Installieren von Visual Studio2017](images/development-environment-setup-1.png)

    <span data-ttu-id="6875f-116">Wenn Sie Visual Studio 2015 Update 3 installieren, stellen Sie sicher, dass das Kontrollkästchen **Entwicklungstools für universelle Windows-Apps** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="6875f-116">If you're installing Visual Studio 2015 Update 3, ensure that the **Universal Windows App Development Tools** check box is selected.</span></span>

    ![Installieren von Visual Studio 2015 Update 2](images/vs_install_tools.png)

## <a name="windows-10-sdk-setup"></a><span data-ttu-id="6875f-118">Einrichten des Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="6875f-118">Windows 10 SDK setup</span></span>

<span data-ttu-id="6875f-119">Installieren Sie das aktuelle Windows10 SDK.</span><span class="sxs-lookup"><span data-stu-id="6875f-119">Install the latest Windows 10 SDK.</span></span> <span data-ttu-id="6875f-120">Dies ist in der Installation von Visual Studio enthalten, aber wenn Sie es separat herunterladen möchten, finden Sie weitere Informationen unter [Windows10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="6875f-120">This comes with your Visual Studio installation, but if you want to download it separately, see [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>


## <a name="enabling-developer-mode"></a><span data-ttu-id="6875f-121">Aktivieren des Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="6875f-121">Enabling Developer Mode</span></span>

<span data-ttu-id="6875f-122">Bevor Sie Apps von Ihrem Entwicklungs-PC bereitstellen können, müssen Sie den Entwicklermodus aktivieren.</span><span class="sxs-lookup"><span data-stu-id="6875f-122">Before you can deploy apps from your development PC, you must enable Developer Mode.</span></span> <span data-ttu-id="6875f-123">Navigieren Sie unter **Einstellungen** zu **Update und Sicherheit** / **Für Entwickler**, und wählen Sie unter **Entwicklerfunktionen verwenden** die Option **Entwicklermodus**.</span><span class="sxs-lookup"><span data-stu-id="6875f-123">In the **Settings** app, navigate to **Update & Security** / **For developers**, and under **Use developer features**, select **Developer mode**.</span></span>

## <a name="setting-up-your-xbox-one"></a><span data-ttu-id="6875f-124">Einrichten Ihrer Xbox One</span><span class="sxs-lookup"><span data-stu-id="6875f-124">Setting up your Xbox One</span></span>

<span data-ttu-id="6875f-125">Bevor Sie eine App auf Ihrer Xbox One bereitstellen können, muss ein Benutzer auf der Konsole angemeldet sein.</span><span class="sxs-lookup"><span data-stu-id="6875f-125">Before you can deploy an app to your Xbox One, you must have a user signed in on the console.</span></span> <span data-ttu-id="6875f-126">Sie können entweder ein vorhandenes Xbox Live-Konto verwenden oder ein neues Konto für Ihre Konsole im Entwicklermodus erstellen.</span><span class="sxs-lookup"><span data-stu-id="6875f-126">You can either use your existing Xbox Live account or create a new account for your console in Developer Mode.</span></span> 

## <a name="create-your-first-app"></a><span data-ttu-id="6875f-127">Erstellen Ihrer ersten App</span><span class="sxs-lookup"><span data-stu-id="6875f-127">Create your first app</span></span>

1. <span data-ttu-id="6875f-128">Stellen Sie sicher, dass sich der Entwicklungscomputer in demselben lokalen Netzwerk wie die gewünschte Xbox One befindet.</span><span class="sxs-lookup"><span data-stu-id="6875f-128">Make sure your development PC is on the same local network as the target Xbox One console.</span></span> <span data-ttu-id="6875f-129">Dies bedeutet normalerweise, dass beide denselben Router verwenden und sich im gleichen Subnetz befinden.</span><span class="sxs-lookup"><span data-stu-id="6875f-129">Typically, this means they should use the same router and be on the same subnet.</span></span> <span data-ttu-id="6875f-130">Es wird eine drahtgebundene Netzwerkverbindung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="6875f-130">A wired network connection is recommended.</span></span>

2. <span data-ttu-id="6875f-131">Stellen Sie sicher, dass sich die Xbox One Konsole im Entwicklermodus befindet.</span><span class="sxs-lookup"><span data-stu-id="6875f-131">Ensure that your Xbox One console is in Developer Mode.</span></span>  <span data-ttu-id="6875f-132">Weitere Informationen finden Sie unter [Aktivierung des Xbox One-Entwicklermodus](devkit-activation.md).</span><span class="sxs-lookup"><span data-stu-id="6875f-132">For more information, see [Xbox One Developer Mode activation](devkit-activation.md).</span></span>

3. <span data-ttu-id="6875f-133">Legen Sie die Programmiersprache fest, die Sie für Ihre UWP-App verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="6875f-133">Decide the programming language that you want to use for your UWP app.</span></span>

4. <span data-ttu-id="6875f-134">Wählen Sie auf Ihrem Entwicklungs-PC in Visual Studio **Neu/Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="6875f-134">On your development PC, in Visual Studio, select **New / Project**.</span></span>

5. <span data-ttu-id="6875f-135">Wählen Sie im Fenster **Neues Projekt** **Windows Universal/Leere App (Universal Windows)** aus.</span><span class="sxs-lookup"><span data-stu-id="6875f-135">In the **New Project** window, select **Windows Universal / Blank App (Universal Windows)**.</span></span>

### <a name="starting-a-c-project"></a><span data-ttu-id="6875f-136">Starten eines C#-Projekts</span><span class="sxs-lookup"><span data-stu-id="6875f-136">Starting a C# project</span></span>

  ![Dialogfeld „Neues Projekt“](images/development-environment-setup-2.png)

1. <span data-ttu-id="6875f-138">Wählen Sie im Dialogfeld **Neues universelles Windows-Projekt** Build 14393 oder höher im Dropdownmenü **Mindestens erforderliche Version** aus.</span><span class="sxs-lookup"><span data-stu-id="6875f-138">In the **New Universal Windows Project** dialog, select build 14393 or later in the **Minimum Version** dropdown.</span></span> <span data-ttu-id="6875f-139">Wählen Sie das aktuelle SDK im Dropdownmenü **Zielversion** aus.</span><span class="sxs-lookup"><span data-stu-id="6875f-139">Select the latest SDK in the **Target Version** dropdown.</span></span> <span data-ttu-id="6875f-140">Wenn das Dialogfeld **Entwicklermodus** angezeigt wird, klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="6875f-140">If the **Developer Mode** dialog appears, click **OK**.</span></span> <span data-ttu-id="6875f-141">Es wird eine neue leere App erstellt.</span><span class="sxs-lookup"><span data-stu-id="6875f-141">A new blank app is created.</span></span>

2. <span data-ttu-id="6875f-142">Konfigurieren Sie die Entwicklungsumgebung für das Remotedebuggen:</span><span class="sxs-lookup"><span data-stu-id="6875f-142">Configure your development environment for remote debugging:</span></span>

    <span data-ttu-id="6875f-143">a.</span><span class="sxs-lookup"><span data-stu-id="6875f-143">a.</span></span> <span data-ttu-id="6875f-144">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="6875f-144">Right-click the project in the **Solution Explorer**, and then select **Properties**.</span></span>

    <span data-ttu-id="6875f-145">b.</span><span class="sxs-lookup"><span data-stu-id="6875f-145">b.</span></span> <span data-ttu-id="6875f-146">Ändern Sie auf der Registerkarte **Debuggen** die Option **Plattform** in **x64**.</span><span class="sxs-lookup"><span data-stu-id="6875f-146">On the **Debug** tab, change **Platform** to **x64**.</span></span> <span data-ttu-id="6875f-147">(x86 wird nicht mehr als Plattform auf Xbox unterstützt.)</span><span class="sxs-lookup"><span data-stu-id="6875f-147">(x86 is no longer a supported platform on Xbox.)</span></span>

    <span data-ttu-id="6875f-148">c.</span><span class="sxs-lookup"><span data-stu-id="6875f-148">c.</span></span> <span data-ttu-id="6875f-149">Ändern Sie unter **Startoptionen** das **Zielgerät** in **Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="6875f-149">Under **Start options**, change **Target device** to **Remote Machine**.</span></span>

    <span data-ttu-id="6875f-150">d.</span><span class="sxs-lookup"><span data-stu-id="6875f-150">d.</span></span> <span data-ttu-id="6875f-151">Geben Sie in **Remotecomputer** die System-IP-Adresse oder den Hostnamen der Xbox One Konsole ein.</span><span class="sxs-lookup"><span data-stu-id="6875f-151">In **Remote machine**, enter the system IP address or hostname of the Xbox One console.</span></span> <span data-ttu-id="6875f-152">Informationen zum Ermitteln der IP-Adresse oder des Hostnamens finden Sie unter [Einführung in Xbox One-Tools](introduction-to-xbox-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6875f-152">For information about obtaining the IP address or hostname, see [Introduction to Xbox One tools](introduction-to-xbox-tools.md).</span></span>

    <span data-ttu-id="6875f-153">e.</span><span class="sxs-lookup"><span data-stu-id="6875f-153">e.</span></span> <span data-ttu-id="6875f-154">Wählen Sie in der Dropdownliste **Authentifizierungsmodus** den Eintrag **Universell (unverschlüsseltes Protokoll)** aus.</span><span class="sxs-lookup"><span data-stu-id="6875f-154">In the **Authentication Mode** drop-down list, select **Universal (Unencrypted Protocol)**.</span></span>

    ![C#-Eigenschaftenseiten für „Leere App“](images/vs_remote.jpg)

### <a name="starting-a-c-project"></a><span data-ttu-id="6875f-156">Starten eines C++-Projekts</span><span class="sxs-lookup"><span data-stu-id="6875f-156">Starting a C++ project</span></span>

  ![C++-Projekt](images/development-environment-setup-3.png)

1. <span data-ttu-id="6875f-158">Wählen Sie im Dialogfeld **Neues universelles Windows-Projekt** Build 14393 oder höher im Dropdownmenü **Mindestens erforderliche Version** aus.</span><span class="sxs-lookup"><span data-stu-id="6875f-158">In the **New Universal Windows Project** dialog, select build 14393 or later in the **Minimum Version** dropdown.</span></span> <span data-ttu-id="6875f-159">Wählen Sie das aktuelle SDK im Dropdownmenü **Zielversion** aus.</span><span class="sxs-lookup"><span data-stu-id="6875f-159">Select the latest SDK in the **Target Version** dropdown.</span></span> <span data-ttu-id="6875f-160">Wenn das Dialogfeld **Entwicklermodus** angezeigt wird, klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="6875f-160">If the **Developer Mode** dialog appears, click **OK**.</span></span> <span data-ttu-id="6875f-161">Es wird eine neue leere App erstellt.</span><span class="sxs-lookup"><span data-stu-id="6875f-161">A new blank app is created.</span></span>

2. <span data-ttu-id="6875f-162">Konfigurieren Sie die Entwicklungsumgebung für das Remotedebuggen:</span><span class="sxs-lookup"><span data-stu-id="6875f-162">Configure your development environment for remote debugging:</span></span>

   <span data-ttu-id="6875f-163">a.</span><span class="sxs-lookup"><span data-stu-id="6875f-163">a.</span></span> <span data-ttu-id="6875f-164">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="6875f-164">Right-click the project in the **Solution Explorer**, and then select **Properties**.</span></span>

   <span data-ttu-id="6875f-165">b.</span><span class="sxs-lookup"><span data-stu-id="6875f-165">b.</span></span> <span data-ttu-id="6875f-166">Ändern Sie **Zu startender Debugger** auf der Registerkarte **Debuggen** in **Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="6875f-166">On the **Debugging** tab, change **Debugger to launch** to **Remote Machine**.</span></span>

   <span data-ttu-id="6875f-167">c.</span><span class="sxs-lookup"><span data-stu-id="6875f-167">c.</span></span> <span data-ttu-id="6875f-168">Geben Sie in **Computername** die System-IP-Adresse oder den Hostnamen der Xbox One Konsole ein.</span><span class="sxs-lookup"><span data-stu-id="6875f-168">In **Machine Name**, enter the system IP address or hostname of the Xbox One console.</span></span> <span data-ttu-id="6875f-169">Informationen zum Ermitteln der IP-Adresse oder des Hostnamens finden Sie unter [Einführung in Xbox One-Tools](introduction-to-xbox-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6875f-169">For information about obtaining the IP address or hostname, see [Introduction to Xbox One tools](introduction-to-xbox-tools.md).</span></span>

   <span data-ttu-id="6875f-170">d.</span><span class="sxs-lookup"><span data-stu-id="6875f-170">d.</span></span> <span data-ttu-id="6875f-171">Wählen Sie in der Dropdownliste **Authentifizierungstyp** den Eintrag **Universell (unverschlüsseltes Protokoll)** aus.</span><span class="sxs-lookup"><span data-stu-id="6875f-171">In the **Authentication Type** drop-down list, select **Universal (Unencrypted Protocol)**.</span></span>

   <span data-ttu-id="6875f-172">e.</span><span class="sxs-lookup"><span data-stu-id="6875f-172">e.</span></span> <span data-ttu-id="6875f-173">Wählen Sie in der Dropdownliste **Plattform** die Option **x64** aus.</span><span class="sxs-lookup"><span data-stu-id="6875f-173">In the **Platform** drop-down, select **x64**.</span></span>

    ![C++-Eigenschaftenseiten für „Leere App“](images/development-environment-setup-4.png)

### <a name="pin-pair-your-device-with-visual-studio"></a><span data-ttu-id="6875f-175">Koppeln des Geräts per PIN mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6875f-175">PIN-pair your device with Visual Studio</span></span>

1. <span data-ttu-id="6875f-176">Speichern Sie die Einstellungen, und stellen Sie sicher, dass sich die Xbox One Konsole im Entwicklermodus befindet.</span><span class="sxs-lookup"><span data-stu-id="6875f-176">Save your settings, and make sure your Xbox One console is in Developer Mode.</span></span>

2. <span data-ttu-id="6875f-177">Drücken Sie im geöffneten Projekt in Visual Studio F5.</span><span class="sxs-lookup"><span data-stu-id="6875f-177">With your project open in Visual Studio, press F5.</span></span>

3. <span data-ttu-id="6875f-178">Wenn dies Ihre erste Bereitstellung ist, werden Sie in einem Dialogfeld in Visual Studio aufgefordert, Ihr Gerät per PIN zu koppeln.</span><span class="sxs-lookup"><span data-stu-id="6875f-178">If this is your first deployment, you will get a dialog from Visual Studio asking to PIN-pair your device.</span></span>

    <span data-ttu-id="6875f-179">a.</span><span class="sxs-lookup"><span data-stu-id="6875f-179">a.</span></span> <span data-ttu-id="6875f-180">Um eine PIN abzurufen, öffnen Sie auf der Startseite der Xbox One Konsole **Dev Home**.</span><span class="sxs-lookup"><span data-stu-id="6875f-180">To obtain a PIN, open **Dev Home** from the Home screen on your Xbox One console.</span></span>

    <span data-ttu-id="6875f-181">b.</span><span class="sxs-lookup"><span data-stu-id="6875f-181">b.</span></span> <span data-ttu-id="6875f-182">Wählen Sie auf der Registerkarte **Startseite** unter **Schnelle Aktionen** die Option **Visual Studio-Pin anzeigen** aus.</span><span class="sxs-lookup"><span data-stu-id="6875f-182">On the **Home** tab, under **Quick actions**, select **Show Visual Studio pin**.</span></span>
  
    ![Dialogfeld „Mit Visual Studio koppeln“](images/development-environment-setup-5.png)

    <span data-ttu-id="6875f-184">c.</span><span class="sxs-lookup"><span data-stu-id="6875f-184">c.</span></span> <span data-ttu-id="6875f-185">Geben Sie im Dialogfeld **Mit Visual Studio koppeln** die PIN ein.</span><span class="sxs-lookup"><span data-stu-id="6875f-185">Enter your PIN into the **Pair with Visual Studio** dialog.</span></span> <span data-ttu-id="6875f-186">Die folgende PIN ist nur ein Beispiel und stimmt nicht mit Ihrer PIN überein.</span><span class="sxs-lookup"><span data-stu-id="6875f-186">The following PIN is just an example; yours will differ.</span></span>

    ![Dialogfeld „Mit Visual Studio per PIN koppeln“](images/devhome_pin.png)

    <span data-ttu-id="6875f-188">d.</span><span class="sxs-lookup"><span data-stu-id="6875f-188">d.</span></span> <span data-ttu-id="6875f-189">Gegebenenfalls auftretende Bereitstellungsfehler werden im Fenster **Ausgabe** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6875f-189">Deployment errors, if any, will appear in the **Output** window.</span></span>

<span data-ttu-id="6875f-190">Herzlichen Glückwunsch! Sie haben Ihre erste UWP-App auf Xbox erfolgreich erstellt und bereitgestellt!</span><span class="sxs-lookup"><span data-stu-id="6875f-190">Congratulations, you've successfully created and deployed your first UWP app on Xbox!</span></span>

## <a name="see-also"></a><span data-ttu-id="6875f-191">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6875f-191">See also</span></span>
- [<span data-ttu-id="6875f-192">Aktivierung des Xbox One-Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="6875f-192">Xbox One Developer Mode activation</span></span>](devkit-activation.md)  
- [<span data-ttu-id="6875f-193">Downloads und Tools für Windows 10</span><span class="sxs-lookup"><span data-stu-id="6875f-193">Downloads and tools for Windows 10</span></span>](https://dev.windows.com/downloads)  
- [<span data-ttu-id="6875f-194">Windows-Insider-Programm</span><span class="sxs-lookup"><span data-stu-id="6875f-194">Windows Insider Program</span></span>](http://go.microsoft.com/fwlink/?LinkId=780552)  
- [<span data-ttu-id="6875f-195">Einführung in Xbox One-Tools</span><span class="sxs-lookup"><span data-stu-id="6875f-195">Introduction to Xbox One tools</span></span>](introduction-to-xbox-tools.md) 
- [<span data-ttu-id="6875f-196">UWP auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="6875f-196">UWP on Xbox One</span></span>](index.md)