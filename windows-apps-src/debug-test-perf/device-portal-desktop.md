---
author: PatrickFarley
ms.assetid: 5c34c78e-9ff7-477b-87f6-a31367cd3f8b
title: "Device Portal für Desktop"
description: "Hier erfahren Sie, wie das Windows Device Portal die Diagnose und Automatisierung auf dem Windows-Desktop öffnet."
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.openlocfilehash: 32155bfbb676a5f79dd4b1629f0a88368da36828
ms.sourcegitcommit: 0fa9ae00117e8e6b04ed38956e605bb74c1261c6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2017
---
# <a name="device-portal-for-desktop"></a><span data-ttu-id="4f58e-104">Device Portal für Desktop</span><span class="sxs-lookup"><span data-stu-id="4f58e-104">Device Portal for Desktop</span></span>

<span data-ttu-id="4f58e-105">Ab Windows 10, Version 1607, sind weitere Entwicklerfeatures für Desktop verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4f58e-105">Starting in Windows 10, Version 1607, additional developer features are available for desktop.</span></span> <span data-ttu-id="4f58e-106">Diese Features sind nur verfügbar, wenn der Entwicklermodus aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="4f58e-106">These features are available only when Developer Mode is enabled.</span></span>

<span data-ttu-id="4f58e-107">Informationen zum Aktivieren des Entwicklermodus finden Sie unter [Aktivieren Ihres Geräts für die Entwicklung](../get-started/enable-your-device-for-development.md).</span><span class="sxs-lookup"><span data-stu-id="4f58e-107">For information about how to enable Developer Mode, see [Enable your device for development](../get-started/enable-your-device-for-development.md).</span></span>

<span data-ttu-id="4f58e-108">Im Device Portal können Sie Diagnoseinformationen anzeigen und über HTTP aus dem Browser mit Ihrem Desktop interagieren.</span><span class="sxs-lookup"><span data-stu-id="4f58e-108">Device Portal lets you view diagnostic information and interact with your desktop over HTTP from your browser.</span></span> <span data-ttu-id="4f58e-109">Sie haben im Device Portal folgende Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="4f58e-109">You can use Device Portal to do the following:</span></span>
- <span data-ttu-id="4f58e-110">Anzeigen und Bearbeiten einer Liste laufender Prozesse</span><span class="sxs-lookup"><span data-stu-id="4f58e-110">See and manipulate a list of running processes</span></span>
- <span data-ttu-id="4f58e-111">Installieren, Löschen, Starten und Beenden von Apps</span><span class="sxs-lookup"><span data-stu-id="4f58e-111">Install, delete, launch, and terminate apps</span></span>
- <span data-ttu-id="4f58e-112">Ändern von WLAN-Profilen und Anzeigen der Signalstärke und der ipconfig</span><span class="sxs-lookup"><span data-stu-id="4f58e-112">Change Wi-Fi profiles, view signal strength, and see ipconfig</span></span>
- <span data-ttu-id="4f58e-113">Anzeigen von Live-Diagrammen zur Auslastung von CPU, Arbeitsspeicher, E/A, Netzwerk und GPU</span><span class="sxs-lookup"><span data-stu-id="4f58e-113">View live graphs of CPU, memory, I/O, network, and GPU usage</span></span>
- <span data-ttu-id="4f58e-114">Sammeln von Prozesssicherungen</span><span class="sxs-lookup"><span data-stu-id="4f58e-114">Collect process dumps</span></span>
- <span data-ttu-id="4f58e-115">Sammeln von ETW-Ablaufverfolgungen</span><span class="sxs-lookup"><span data-stu-id="4f58e-115">Collect ETW traces</span></span> 
- <span data-ttu-id="4f58e-116">Bearbeiten des isolierten Speichers quergeladener Apps</span><span class="sxs-lookup"><span data-stu-id="4f58e-116">Manipulate the isolated storage of sideloaded apps</span></span>

## <a name="set-up-device-portal-on-windows-desktop"></a><span data-ttu-id="4f58e-117">Einrichten von Device Portal unter Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="4f58e-117">Set up device portal on Windows Desktop</span></span>

### <a name="turn-on-device-portal"></a><span data-ttu-id="4f58e-118">Aktivieren von Device Portal</span><span class="sxs-lookup"><span data-stu-id="4f58e-118">Turn on device portal</span></span>

<span data-ttu-id="4f58e-119">Sie können Device Portal im Menü **Entwicklereinstellungen** mit aktiviertem Entwicklermodus aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4f58e-119">In the **Developer Settings** menu, with Developer Mode enabled, you can enable Device Portal.</span></span>  

<span data-ttu-id="4f58e-120">Wenn Sie Device Portal aktivieren, müssen Sie einen Benutzernamen und ein Kennwort für Device Portal erstellen.</span><span class="sxs-lookup"><span data-stu-id="4f58e-120">When you enable Device Portal, you must also create a username and password for Device Portal.</span></span> <span data-ttu-id="4f58e-121">Verwenden Sie nicht Ihr Microsoft-Konto oder andere Windows-Anmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="4f58e-121">Do not use your Microsoft account or other Windows credentials.</span></span>  

<span data-ttu-id="4f58e-122">Nachdem Device Portal aktiviert wurde, werden unten im Abschnitt **Einstellungen** Links angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4f58e-122">After Device Portal is enabled, you will see links to it at the bottom of the **Settings** section.</span></span> <span data-ttu-id="4f58e-123">Beachten Sie die Portnummer am Ende der URL: Diese Portnummer wird nach dem Zufallsprinzip generiert, wenn Device Portal aktiviert wird, sollte jedoch zwischen Neustarts des Desktops konsistent bleiben.</span><span class="sxs-lookup"><span data-stu-id="4f58e-123">Take note of the port number applied to the end of the URL: this port number is randomly generated when Device Portal is enabled, but should remain consistent between reboots of the desktop.</span></span> <span data-ttu-id="4f58e-124">Wenn Sie die Portnummern manuell festlegen möchten, sodass sie erhalten bleiben, finden Sie unter [Portnummern setzen](device-portal-desktop.md#setting-port-numbers) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="4f58e-124">If you'd like to set the port numbers manually so they remain permanent, see [Setting port numbers](device-portal-desktop.md#setting-port-numbers).</span></span>

<span data-ttu-id="4f58e-125">Sie haben zwei Möglichkeiten zum Herstellen einer Verbindung mit Device Portal: über einen lokalen Host und über das lokale Netzwerk (einschließlich VPN).</span><span class="sxs-lookup"><span data-stu-id="4f58e-125">You can choose from two ways to connect to Device Portal: local host and over the local network (including VPN).</span></span>

**<span data-ttu-id="4f58e-126">So stellen Sie eine Verbindung mit dem Device Portal her</span><span class="sxs-lookup"><span data-stu-id="4f58e-126">To connect to Device Portal</span></span>**

1. <span data-ttu-id="4f58e-127">Geben Sie in Ihrem Browser die hier angegebene Adresse für den verwendeten Verbindungstyp ein.</span><span class="sxs-lookup"><span data-stu-id="4f58e-127">In your browser, enter the address shown here for the connection type you're using.</span></span>

    - <span data-ttu-id="4f58e-128">Lokaler Host: `http://127.0.0.1:PORT` oder</span><span class="sxs-lookup"><span data-stu-id="4f58e-128">Localhost: `http://127.0.0.1:PORT` or</span></span> `http://localhost:PORT`

    <span data-ttu-id="4f58e-129">Verwenden Sie diese Adresse, um Device Portal lokal anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4f58e-129">Use this address to view Device Portal locally.</span></span>
    
    - <span data-ttu-id="4f58e-130">Lokales Netzwerk:</span><span class="sxs-lookup"><span data-stu-id="4f58e-130">Local Network:</span></span> `https://<The IP address of the desktop>:PORT`

    <span data-ttu-id="4f58e-131">Verwenden Sie diese Adresse, um die Verbindung über ein lokales Netzwerk herzustellen.</span><span class="sxs-lookup"><span data-stu-id="4f58e-131">Use this address to connect over a local network.</span></span>

<span data-ttu-id="4f58e-132">Für die Authentifizierung und sichere Kommunikation ist HTTPS erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4f58e-132">HTTPS is required for authentication and secure communication.</span></span>

<span data-ttu-id="4f58e-133">Sie können die Authentifizierung deaktivieren, wenn Sie Device Portal in einer geschützten Umgebung verwenden, z.B. in einem Testlabor, in dem Sie allen im lokalen Netzwerk vertrauen, keine persönlichen Informationen auf dem Gerät gespeichert haben und in dem spezielle Anforderungen bestehen.</span><span class="sxs-lookup"><span data-stu-id="4f58e-133">If you are using Device Portal in a protected environment, like a test lab, where you trust everyone on your local network, have no personal information on the device, and have unique requirements, you can disable authentication.</span></span> <span data-ttu-id="4f58e-134">Dies ermöglicht eine unverschlüsselte Kommunikation, und jeder, der die IP-Adresse Ihres Computers kennt, kann es steuern.</span><span class="sxs-lookup"><span data-stu-id="4f58e-134">This enables unencrypted communication, and allows anyone with the IP address of your computer to control it.</span></span>

## <a name="device-portal-pages"></a><span data-ttu-id="4f58e-135">Seiten von Device Portal</span><span class="sxs-lookup"><span data-stu-id="4f58e-135">Device Portal pages</span></span>

<span data-ttu-id="4f58e-136">Device Portal für Desktop enthält den Standardsatz der Seiten.</span><span class="sxs-lookup"><span data-stu-id="4f58e-136">Device Portal on desktop provides the standard set of pages.</span></span> <span data-ttu-id="4f58e-137">Ausführliche Beschreibungen finden Sie unter [Übersicht über das Windows Device Portal](device-portal.md).</span><span class="sxs-lookup"><span data-stu-id="4f58e-137">For detailed descriptions, see [Windows Device Portal overview](device-portal.md).</span></span>

- <span data-ttu-id="4f58e-138">Apps</span><span class="sxs-lookup"><span data-stu-id="4f58e-138">Apps</span></span>
- <span data-ttu-id="4f58e-139">Prozesse</span><span class="sxs-lookup"><span data-stu-id="4f58e-139">Processes</span></span>
- <span data-ttu-id="4f58e-140">Leistung</span><span class="sxs-lookup"><span data-stu-id="4f58e-140">Performance</span></span>
- <span data-ttu-id="4f58e-141">Debuggen</span><span class="sxs-lookup"><span data-stu-id="4f58e-141">Debugging</span></span>
- <span data-ttu-id="4f58e-142">Ereignisablaufverfolgung für Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="4f58e-142">Event Tracing for Windows (ETW)</span></span>
- <span data-ttu-id="4f58e-143">Leistungsüberwachung</span><span class="sxs-lookup"><span data-stu-id="4f58e-143">Performance tracing</span></span>
- <span data-ttu-id="4f58e-144">Geräte</span><span class="sxs-lookup"><span data-stu-id="4f58e-144">Devices</span></span>
- <span data-ttu-id="4f58e-145">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="4f58e-145">Networking</span></span>
- <span data-ttu-id="4f58e-146">App-Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="4f58e-146">App File Explorer</span></span> 

## <a name="setting-port-numbers"></a><span data-ttu-id="4f58e-147">Festlegen von Portnummern</span><span class="sxs-lookup"><span data-stu-id="4f58e-147">Setting port numbers</span></span>

<span data-ttu-id="4f58e-148">Wenn Sie Portnummern für Device Portal auswählen möchten (z. B. 80 und 443), können Sie die folgenden Registrierungsschlüssel festlegen:</span><span class="sxs-lookup"><span data-stu-id="4f58e-148">If you would like to select port numbers for Device Portal (such as 80 and 443), you can set the following regkeys:</span></span>

- <span data-ttu-id="4f58e-149">Unter HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\WebManagement\Service</span><span class="sxs-lookup"><span data-stu-id="4f58e-149">Under HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\WebManagement\Service</span></span>
    - <span data-ttu-id="4f58e-150">UseDynamicPorts: Ein erforderlicher DWORD-Wert.</span><span class="sxs-lookup"><span data-stu-id="4f58e-150">UseDynamicPorts: A required DWORD.</span></span> <span data-ttu-id="4f58e-151">Legen Sie den Wert auf 0 fest, um die von Ihnen ausgewählten Portnummern beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="4f58e-151">Set this to 0 in order to retain the port numbers you've chosen.</span></span>
    - <span data-ttu-id="4f58e-152">HttpPort: Ein erforderlicher DWORD-Wert.</span><span class="sxs-lookup"><span data-stu-id="4f58e-152">HttpPort: A required DWORD.</span></span> <span data-ttu-id="4f58e-153">Enthält die Portnummer, an der Device Portal nach HTTP-Verbindungen lauscht.</span><span class="sxs-lookup"><span data-stu-id="4f58e-153">Contains the port number that Device Portal will listen for HTTP connections on.</span></span>  
    - <span data-ttu-id="4f58e-154">HttpsPort: Ein erforderlicher DWORD-Wert.</span><span class="sxs-lookup"><span data-stu-id="4f58e-154">HttpsPort: A required DWORD.</span></span> <span data-ttu-id="4f58e-155">Enthält die Portnummer, an der Device Portal nach HTTPS-Verbindungen lauscht.</span><span class="sxs-lookup"><span data-stu-id="4f58e-155">Contains the port number that Device Portal will listen for HTTPS connections on.</span></span>

## <a name="failure-to-install-developer-mode-package"></a><span data-ttu-id="4f58e-156">Fehler beim Installieren des Entwicklermoduspakets</span><span class="sxs-lookup"><span data-stu-id="4f58e-156">Failure to install Developer Mode package</span></span>
<span data-ttu-id="4f58e-157">In manchen Fällen wird der Entwicklermodus aufgrund von Problemen mit dem Netzwerk oder der Kompatibilität nicht ordnungsgemäß installiert.</span><span class="sxs-lookup"><span data-stu-id="4f58e-157">Sometimes, due to network or compatibility issues, Developer Mode won't install correctly.</span></span> <span data-ttu-id="4f58e-158">Das Entwicklermoduspaket ist für die **remote** Bereitstellung auf dem PC erforderlich – verwenden Sie Device Portal über einen Browser oder Device Discovery zur Aktivierung von SSH – aber nicht für die lokale Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="4f58e-158">The Developer Mode package is required for **remote** deployment to the PC -- using Device Portal from a browser or Device Discovery to enable SSH -- but not for local development.</span></span>  <span data-ttu-id="4f58e-159">Selbst wenn diese Probleme auftreten, können Sie Ihre App weiterhin mithilfe von Visual Studio bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="4f58e-159">Even if you encounter these issues, you can still deploy your app locally using Visual Studio.</span></span> 

<span data-ttu-id="4f58e-160">Im Forum [Bekannte Probleme](https://social.msdn.microsoft.com/Forums/en-US/home?forum=Win10SDKToolsIssues&sort=relevancedesc&brandIgnore=True&searchTerm=%22device+portal%22) und auf der [Entwicklermodusseite](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development#failure-to-install-developer-mode-package) finden Sie entsprechende Problemumgehungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="4f58e-160">See the [Known Issues](https://social.msdn.microsoft.com/Forums/en-US/home?forum=Win10SDKToolsIssues&sort=relevancedesc&brandIgnore=True&searchTerm=%22device+portal%22) forum and the [Developer Mode page](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development#failure-to-install-developer-mode-package) to find workarounds to these issues and more.</span></span> 

