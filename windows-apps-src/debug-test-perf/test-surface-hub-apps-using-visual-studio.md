---
author: PatrickFarley
ms.assetid: A5320094-DF53-42FC-A6BA-A958F8E9210B
title: Testen von Surface Hub-Apps mit Visual Studio
description: "Der Visual Studio-Simulator bietet eine Umgebung für das Entwerfen, Entwickeln, Debuggen und Testen von UWP-Apps, einschließlich Apps für Surface Hub."
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 859c28d59e3c289ac3cb7151f0b9e396d52546c3
ms.sourcegitcommit: e8cc657d85566768a6efb7cd972ebf64c25e0628
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2017
---
# <a name="test-surface-hub-apps-using-visual-studio"></a><span data-ttu-id="5f23a-104">Testen von Surface Hub-Apps mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5f23a-104">Test Surface Hub apps using Visual Studio</span></span>
<span data-ttu-id="5f23a-105">Der Visual Studio-Simulator bietet eine Umgebung, in der Sie Universelle Windows-Plattform (UWP)-Apps entwerfen, entwickeln, debuggen und testen können, einschließlich Apps, die Sie für Microsoft Surface Hub entwickelt haben.</span><span class="sxs-lookup"><span data-stu-id="5f23a-105">The Visual Studio simulator provides an environment where you can design, develop, debug, and test Universal Windows Platform (UWP) apps, including apps that you have built for Microsoft Surface Hub.</span></span> <span data-ttu-id="5f23a-106">Der Simulator verwendet nicht dieselbe Benutzeroberfläche wie ein Surface Hub, ist jedoch hilfreich, um das Erscheinungsbild und Verhalten Ihrer App bei der Bildschirmgröße und -auflösung von Surface Hubs zu testen.</span><span class="sxs-lookup"><span data-stu-id="5f23a-106">The simulator does not use the same user interface as Surface Hub, but it is useful for testing how your app looks and behaves at the Surface Hub's screen size and resolution.</span></span>

<span data-ttu-id="5f23a-107">Weitere Informationen finden Sie unter [Ausführen von WindowsStore-Apps im Simulator](https://msdn.microsoft.com/library/hh441475.aspx).</span><span class="sxs-lookup"><span data-stu-id="5f23a-107">For more information, see [Run Windows Store apps in the simulator](https://msdn.microsoft.com/library/hh441475.aspx).</span></span>

## <a name="add-surface-hub-resolutions-to-the-simulator"></a><span data-ttu-id="5f23a-108">Hinzufügen von Surface Hub-Auflösungen zum Simulator</span><span class="sxs-lookup"><span data-stu-id="5f23a-108">Add Surface Hub resolutions to the simulator</span></span>
<span data-ttu-id="5f23a-109">So fügen Sie Surface Hub-Auflösungen zum Simulator hinzu:</span><span class="sxs-lookup"><span data-stu-id="5f23a-109">To add Surface Hub resolutions to the simulator:</span></span>

1. <span data-ttu-id="5f23a-110">Erstellen Sie eine Konfiguration für denSurface Hub mit 55Zoll, indem Sie den folgenden XML-Code in einer Datei namens **HardwareConfigurations-SurfaceHub55.xml** speichern.</span><span class="sxs-lookup"><span data-stu-id="5f23a-110">Create a configuration for the 55" Surface Hub by saving the following XML into a file named **HardwareConfigurations-SurfaceHub55.xml**.</span></span>  

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <ArrayOfHardwareConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema"
                                  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <HardwareConfiguration>
            <Name>SurfaceHub55</Name>
            <DisplayName>Surface Hub 55"</DisplayName>
            <Resolution>
                <Height>1080</Height>
                <Width>1920</Width>
            </Resolution>
            <DeviceSize>55</DeviceSize>
            <DeviceScaleFactor>100</DeviceScaleFactor>
        </HardwareConfiguration>
    </ArrayOfHardwareConfiguration>
    ```

2. <span data-ttu-id="5f23a-111">Erstellen Sie eine Konfiguration für denSurface Hub mit 84Zoll, indem Sie den folgenden XML-Code in einer Datei namens **HardwareConfigurations-SurfaceHub84.xml** speichern.</span><span class="sxs-lookup"><span data-stu-id="5f23a-111">Create a configuration for the 84" Surface Hub by saving the following XML into a file named  **HardwareConfigurations-SurfaceHub84.xml**.</span></span>

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <ArrayOfHardwareConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema"
                                  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <HardwareConfiguration>
            <Name>SurfaceHub84</Name>
            <DisplayName>Surface Hub 84"</DisplayName>
            <Resolution>
                <Height>2160</Height>
                <Width>3840</Width>
            </Resolution>
            <DeviceSize>84</DeviceSize>
            <DeviceScaleFactor>150</DeviceScaleFactor>
        </HardwareConfiguration>
    </ArrayOfHardwareConfiguration>
    ```

3. <span data-ttu-id="5f23a-112">Kopieren Sie die zwei XML-Dateien in **C:\Programme (x86)\Gemeinsame Dateien\Microsoft Shared\Windows Simulator\\&lt;Versionsnummer&gt;\HardwareConfigurations**.</span><span class="sxs-lookup"><span data-stu-id="5f23a-112">Copy the two XML files into **C:\Program Files (x86)\Common Files\Microsoft Shared\Windows Simulator\\&lt;version number&gt;\HardwareConfigurations**.</span></span>

   > <span data-ttu-id="5f23a-113">**Hinweis**&nbsp;&nbsp;Zum Speichern der Dateien in diesem Ordner werden Administratorrechte benötigt.</span><span class="sxs-lookup"><span data-stu-id="5f23a-113">**Note**&nbsp;&nbsp;Administrative privileges are required to save files into this folder.</span></span>

4. <span data-ttu-id="5f23a-114">Führen Sie Ihre App im Visual Studio-Simulator aus.</span><span class="sxs-lookup"><span data-stu-id="5f23a-114">Run your app in the Visual Studio simulator.</span></span> <span data-ttu-id="5f23a-115">Klicken Sie in der Palette auf die Schaltfläche **Change Resolution**, und wählen Sie in der Liste eine Surface Hub-Konfiguration aus.</span><span class="sxs-lookup"><span data-stu-id="5f23a-115">Click the **Change Resolution** button on the palette and select a Surface Hub configuration from the list.</span></span>

    ![Auflösungen des Visual Studio-Simulators](images/vs-simulator-resolutions.png)

   > <span data-ttu-id="5f23a-117">**Tipp**&nbsp;&nbsp;[Schalten Sie den Tablet-Modus ein](http://windows.microsoft.com/windows-10/getstarted-like-a-tablet), um das Verhalten auf einem Surface Hub besser zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="5f23a-117">**Tip**&nbsp;&nbsp;[Turn on Tablet mode](http://windows.microsoft.com/windows-10/getstarted-like-a-tablet) to better simulate the experience on a Surface Hub.</span></span>

## <a name="deploy-apps-to-a-surface-hub-from-visual-studio"></a><span data-ttu-id="5f23a-118">Bereitstellen von Apps aus Visual Studio auf einem Surface Hub</span><span class="sxs-lookup"><span data-stu-id="5f23a-118">Deploy apps to a Surface Hub from Visual Studio</span></span>
<span data-ttu-id="5f23a-119">Das manuelle Bereitstellen einer App ist ein einfacher Vorgang.</span><span class="sxs-lookup"><span data-stu-id="5f23a-119">Manually deploying an app is a simple process.</span></span>

### <a name="enable-developer-mode"></a><span data-ttu-id="5f23a-120">Aktivieren des Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="5f23a-120">Enable developer mode</span></span>
<span data-ttu-id="5f23a-121">Standardmäßig installiert Surface Hub nur Apps aus dem Windows Store.</span><span class="sxs-lookup"><span data-stu-id="5f23a-121">By default, Surface Hub only installs apps from the Windows Store.</span></span> <span data-ttu-id="5f23a-122">Um Apps, die von einer anderen Quelle signiert wurden, zu installieren, müssen Sie den Entwicklermodus aktivieren.</span><span class="sxs-lookup"><span data-stu-id="5f23a-122">To install apps signed by other sources, you must enable developer mode.</span></span>

> <span data-ttu-id="5f23a-123">**Hinweis**&nbsp;&nbsp;Nachdem der Entwicklermodus aktiviert wurde, müssen Sie den Surface Hub zurücksetzen, um den Entwicklermodus wieder zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="5f23a-123">**Note**&nbsp;&nbsp;After developer mode has been enabled, you will need to reset the Surface Hub to disable it again.</span></span> <span data-ttu-id="5f23a-124">Durch das Zurücksetzen des Geräts werden alle lokalen Benutzerdateien und die Konfiguration gelöscht, und anschließend wird Windows neu installiert.</span><span class="sxs-lookup"><span data-stu-id="5f23a-124">Resetting the device removes all local user files and configurations and then reinstalls Windows.</span></span>

1. <span data-ttu-id="5f23a-125">Öffnen Sie im **Startmenü** des Surface Hub die Einstellungs-App.</span><span class="sxs-lookup"><span data-stu-id="5f23a-125">From the Surface Hub's **Start** menu, open the Settings app.</span></span>

   >  <span data-ttu-id="5f23a-126">**Hinweis**&nbsp;&nbsp;Für den Zugriff auf die Einstellungs-App werden Administratorrechte benötigt.</span><span class="sxs-lookup"><span data-stu-id="5f23a-126">**Note**&nbsp;&nbsp;Administrative privileges are required to access the Settings app.</span></span>

2. <span data-ttu-id="5f23a-127">Navigieren Sie zu **Update und Sicherheit > Für Entwickler**.</span><span class="sxs-lookup"><span data-stu-id="5f23a-127">Navigate to **Update & security > For developers**.</span></span>

3. <span data-ttu-id="5f23a-128">Wählen Sie **Entwicklermodus** aus, und akzeptieren Sie die Warnung.</span><span class="sxs-lookup"><span data-stu-id="5f23a-128">Choose **Developer mode** and accept the warning prompt.</span></span>

### <a name="deploy-your-app-from-visual-studio"></a><span data-ttu-id="5f23a-129">Bereitstellen Ihrer App aus Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5f23a-129">Deploy your app from Visual Studio</span></span>
<span data-ttu-id="5f23a-130">Weitere Informationen finden Sie unter [Bereitstellen und Debuggen von Apps für die Universelle Windows-Plattform (UWP)](https://msdn.microsoft.com/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps).</span><span class="sxs-lookup"><span data-stu-id="5f23a-130">For more information, see [Deploying and debugging Universal Windows Platform (UWP) apps](https://msdn.microsoft.com/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps).</span></span>

   > <span data-ttu-id="5f23a-131">**Hinweis**&nbsp;&nbsp;Dieses Feature erfordert mindestens **Visual Studio 2015 Update 1**.</span><span class="sxs-lookup"><span data-stu-id="5f23a-131">**Note**&nbsp;&nbsp;This feature requires at least **Visual Studio 2015 Update 1**.</span></span>

1. <span data-ttu-id="5f23a-132">Zur Auswahl eines Ziels navigieren Sie zur Dropdownliste mit Debugzielen neben der Schaltfläche **Debugging starten** und wählen **Remotecomputer** aus.</span><span class="sxs-lookup"><span data-stu-id="5f23a-132">Navigate to the debug target dropdown next to the **Start Debugging** button and select **Remote Machine**.</span></span>

    <!--lcap: in your screenshot, you have local machine selected-->

   ![Dropdownliste der Debugziele in Visual Studio](images/vs-debug-target.png)

2. <span data-ttu-id="5f23a-134">Geben Sie die IP-Adresse des Surface Hub ein.</span><span class="sxs-lookup"><span data-stu-id="5f23a-134">Enter the Surface Hub's IP address.</span></span> <span data-ttu-id="5f23a-135">Stellen Sie sicher, dass der Authentifizierungsmodus **Universell** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="5f23a-135">Ensure that the **Universal** authentication mode is selected.</span></span>

   > <span data-ttu-id="5f23a-136">**Tipp**&nbsp;&nbsp;Nachdem Sie den Entwicklermodus aktiviert haben, sehen Sie die IP-Adresse des Surface Hub auf dem Willkommensbildschirm.</span><span class="sxs-lookup"><span data-stu-id="5f23a-136">**Tip**&nbsp;&nbsp;After you have enabled developer mode, you can find the Surface Hub's IP address on the welcome screen.</span></span>

3. <span data-ttu-id="5f23a-137">Wählen Sie entweder **Debugging starten (F5)** aus, um die Bereitstellung und das Debugging Ihrer App auf dem Surface Hub auszuführen, oder drücken Sie STRG+F5, um nur die Bereitstellung Ihrer App auszuführen.</span><span class="sxs-lookup"><span data-stu-id="5f23a-137">Choose **Start Debugging (F5)** to deploy and debug your app on the Surface Hub, or press Ctrl+F5 to just deploy your app.</span></span>

   > <span data-ttu-id="5f23a-138">**Tipp**&nbsp;&nbsp;Sollte auf dem Surface Hub der Willkommensbildschirm angezeigt werden, können Sie diesen durch Drücken einer beliebigen Schaltfläche schließen.</span><span class="sxs-lookup"><span data-stu-id="5f23a-138">**Tip**&nbsp;&nbsp;If the Surface Hub is on the welcome screen, dismiss it by choosing any button.</span></span>
