---
ms.assetid: A5320094-DF53-42FC-A6BA-A958F8E9210B
title: Testen von Surface Hub-Apps mit Visual Studio
description: Der Visual Studio-Simulator bietet eine Umgebung für das Entwerfen, Entwickeln, Debuggen und Testen von UWP-Apps, einschließlich Apps für Surface Hub.
ms.date: 10/26/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: b40fd56a85be6dce441324a427790cda28f9d7ac
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8929532"
---
# <a name="test-surface-hub-apps-using-visual-studio"></a><span data-ttu-id="a9fdc-104">Testen von Surface Hub-Apps mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a9fdc-104">Test Surface Hub apps using Visual Studio</span></span>
<span data-ttu-id="a9fdc-105">Der Visual Studio-Simulator bietet eine Umgebung, in der Sie Universelle Windows-Plattform (UWP)-Apps entwerfen, entwickeln, debuggen und testen können, einschließlich Apps, die Sie für Microsoft Surface Hub entwickelt haben.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-105">The Visual Studio simulator provides an environment where you can design, develop, debug, and test Universal Windows Platform (UWP) apps, including apps that you have built for Microsoft Surface Hub.</span></span> <span data-ttu-id="a9fdc-106">Der Simulator verwendet nicht dieselbe Benutzeroberfläche wie ein Surface Hub, aber es ist hilfreich, wie Ihre app aussieht, und mit dem Surface Hub-Bildschirmgröße und-Auflösung Verhalten zu testen.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-106">The simulator does not use the same user interface as Surface Hub, but it is useful for testing how your app looks and behaves with the Surface Hub's screen size and resolution.</span></span>

<span data-ttu-id="a9fdc-107">Weitere Informationen zum Simulator im Allgemeinen finden Sie unter [Ausführen von UWP-apps im Simulator](https://docs.microsoft.com/visualstudio/debugger/run-windows-store-apps-in-the-simulator).</span><span class="sxs-lookup"><span data-stu-id="a9fdc-107">For more information on the simulator tool in general, see [Run UWP apps in the simulator](https://docs.microsoft.com/visualstudio/debugger/run-windows-store-apps-in-the-simulator).</span></span>

## <a name="add-surface-hub-resolutions-to-the-simulator"></a><span data-ttu-id="a9fdc-108">Hinzufügen von Surface Hub-Auflösungen zum Simulator</span><span class="sxs-lookup"><span data-stu-id="a9fdc-108">Add Surface Hub resolutions to the simulator</span></span>
<span data-ttu-id="a9fdc-109">So fügen Sie Surface Hub-Auflösungen zum Simulator hinzu:</span><span class="sxs-lookup"><span data-stu-id="a9fdc-109">To add Surface Hub resolutions to the simulator:</span></span>

1. <span data-ttu-id="a9fdc-110">Erstellen Sie eine Konfiguration für 55" Surface Hub, indem Sie den folgenden XML-Code in eine Datei mit dem Namen *HardwareConfigurations-SurfaceHub55.xml*speichern.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-110">Create a configuration for the 55" Surface Hub by saving the following XML code into a file named *HardwareConfigurations-SurfaceHub55.xml*.</span></span>  

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

2. <span data-ttu-id="a9fdc-111">Erstellen Sie eine Konfiguration für 84" Surface Hub, indem Sie den folgenden XML-Code in eine Datei mit dem Namen *HardwareConfigurations-SurfaceHub84.xml*speichern.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-111">Create a configuration for the 84" Surface Hub by saving the following XML code into a file named  *HardwareConfigurations-SurfaceHub84.xml*.</span></span>

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

3. <span data-ttu-id="a9fdc-112">Kopieren Sie die zwei XML-Dateien in *C:\Programme (x86)\Gemeinsame Dateien\Microsoft Shared\Windows Simulator\\&lt;Versionsnummer&gt;\HardwareConfigurations*.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-112">Copy the two XML files into *C:\Program Files (x86)\Common Files\Microsoft Shared\Windows Simulator\\&lt;version number&gt;\HardwareConfigurations*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a9fdc-113">Zum Speichern der Dateien in diesem Ordner werden Administratorrechte benötigt.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-113">Administrative privileges are required to save files into this folder.</span></span>

4. <span data-ttu-id="a9fdc-114">Führen Sie Ihre App im Visual Studio-Simulator aus.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-114">Run your app in the Visual Studio simulator.</span></span> <span data-ttu-id="a9fdc-115">Klicken Sie in der Palette auf die Schaltfläche **Change Resolution**, und wählen Sie in der Liste eine Surface Hub-Konfiguration aus.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-115">Click the **Change Resolution** button on the palette and select a Surface Hub configuration from the list.</span></span>

    ![Auflösungen des Visual Studio-Simulators](images/vs-simulator-resolutions.png)

   > [!TIP]
   > <span data-ttu-id="a9fdc-117">[Tablet-Modus aktivieren](http://windows.microsoft.com/windows-10/getstarted-like-a-tablet) , können Sie sich die Erfahrung von Surface Hub zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-117">[Turn on Tablet mode](http://windows.microsoft.com/windows-10/getstarted-like-a-tablet) to better simulate the experience of a Surface Hub.</span></span>

## <a name="deploy-apps-to-a-surface-hub-device-from-visual-studio"></a><span data-ttu-id="a9fdc-118">Bereitstellen von apps auf einem Surface Hub-Gerät aus Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a9fdc-118">Deploy apps to a Surface Hub device from Visual Studio</span></span>
<span data-ttu-id="a9fdc-119">Manuelle Bereitstellen einer app auf einem Surface Hub ist ein einfacher Vorgang.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-119">Manually deploying an app to a Surface Hub is a simple process.</span></span>

### <a name="enable-developer-mode"></a><span data-ttu-id="a9fdc-120">Aktivieren des Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="a9fdc-120">Enable developer mode</span></span>
<span data-ttu-id="a9fdc-121">Standardmäßig installiert Surface Hub nur apps aus dem Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-121">By default, Surface Hub only installs apps from the Microsoft Store.</span></span> <span data-ttu-id="a9fdc-122">Um Apps, die von einer anderen Quelle signiert wurden, zu installieren, müssen Sie den Entwicklermodus aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-122">To install apps signed by other sources, you must enable developer mode.</span></span>

> [!NOTE]
> <span data-ttu-id="a9fdc-123">Nachdem der Entwicklermodus aktiviert wurde, müssen Sie die Surface Hub zurücksetzen, wenn Sie wieder zu deaktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-123">After developer mode has been enabled, you will need to reset the Surface Hub if you wish to disable it again.</span></span> <span data-ttu-id="a9fdc-124">Durch das Zurücksetzen des Geräts werden alle lokalen Benutzerdateien und die Konfiguration gelöscht, und anschließend wird Windows neu installiert.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-124">Resetting the device removes all local user files and configurations and then reinstalls Windows.</span></span>

1. <span data-ttu-id="a9fdc-125">Öffnen Sie im **Startmenü** des Surface Hub die Einstellungs-App.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-125">From the Surface Hub's **Start** menu, open the Settings app.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a9fdc-126">Greifen Sie auf die Einstellungs-app auf Surface Hub werden Administratorrechte benötigt.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-126">Administrative privileges are required to access the Settings app on Surface Hub.</span></span>

2. <span data-ttu-id="a9fdc-127">Navigieren Sie zu **Update und Sicherheit \ > für Entwickler**.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-127">Navigate to **Update & security \> For developers**.</span></span>

3. <span data-ttu-id="a9fdc-128">Wählen Sie **Entwicklermodus** aus, und akzeptieren Sie die Warnung.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-128">Choose **Developer mode** and accept the warning prompt.</span></span>

### <a name="deploy-your-app-from-visual-studio"></a><span data-ttu-id="a9fdc-129">Bereitstellen Ihrer App aus Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a9fdc-129">Deploy your app from Visual Studio</span></span>
<span data-ttu-id="a9fdc-130">Weitere Informationen zu den Bereitstellungsprozess finden Sie in der Regel [Bereitstellen und Debuggen von UWP-apps](https://msdn.microsoft.com/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps).</span><span class="sxs-lookup"><span data-stu-id="a9fdc-130">For more information on the deployment process in general, see [Deploying and debugging UWP apps](https://msdn.microsoft.com/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps).</span></span>

   > [!NOTE]
   > <span data-ttu-id="a9fdc-131">Dieses Feature erfordert Visual Studio 2015 Update 1 oder höher, aber es wird empfohlen, dass Sie die neueste aktuelle Version von Visual Studio verwenden.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-131">This feature requires Visual Studio 2015 Update 1 or later, however we recommend that you use the latest most up to date version of Visual Studio.</span></span> <span data-ttu-id="a9fdc-132">Eine auf dem neuesten Stand Visual Studio-Instanz wird Sie alle neuesten Entwicklungen und Sicherheitsupdates gibe.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-132">An up to date Visual Studio instance will gibe you all the latest development and security updates.</span></span>

1. <span data-ttu-id="a9fdc-133">Zur Auswahl eines Ziels navigieren Sie zur Dropdownliste mit Debugzielen neben der Schaltfläche **Debugging starten** und wählen **Remotecomputer** aus.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-133">Navigate to the debug target dropdown next to the **Start Debugging** button and select **Remote Machine**.</span></span>

    <!--lcap: in your screenshot, you have local machine selected-->

   ![Dropdownliste der Debugziele in Visual Studio](images/vs-debug-target.png)

2. <span data-ttu-id="a9fdc-135">Geben Sie die IP-Adresse des Surface Hub ein.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-135">Enter the Surface Hub's IP address.</span></span> <span data-ttu-id="a9fdc-136">Stellen Sie sicher, dass der Authentifizierungsmodus **Universell** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-136">Ensure that the **Universal** authentication mode is selected.</span></span>

   > [!TIP] 
   > <span data-ttu-id="a9fdc-137">Nachdem Sie den Entwicklermodus aktiviert haben, finden Sie den Surface Hub IP-Adresse auf der Willkommensseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-137">After you have enabled developer mode, you can find the Surface Hub's IP address on the welcome screen.</span></span>

3. <span data-ttu-id="a9fdc-138">Wählen Sie zum Bereitstellen und Debuggen Sie Ihre app auf dem Surface Hub **Debugging starten (F5)** , oder drücken Sie STRG + F5, um nur die app bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-138">Select **Start Debugging (F5)** to deploy and debug your app on the Surface Hub, or press Ctrl+F5 to just deploy your app.</span></span>

   > [!TIP]
   > <span data-ttu-id="a9fdc-139">Wenn Surface Hub auf die Willkommensseite angezeigt wird, können schließen Sie diesen durch Drücken einer beliebigen Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="a9fdc-139">If the Surface Hub is displaying the welcome screen, dismiss it by choosing any button.</span></span>
