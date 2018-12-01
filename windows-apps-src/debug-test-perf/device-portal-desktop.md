---
ms.assetid: 5c34c78e-9ff7-477b-87f6-a31367cd3f8b
title: Geräteportal für Windows-Desktop
description: Hier erfahren Sie, wie das Windows Device Portal die Diagnose und Automatisierung auf dem Windows-Desktop öffnet.
ms.date: 03/15/2018
ms.topic: article
keywords: Windows 10, Uwp, geräteportal
ms.localizationpriority: medium
ms.openlocfilehash: 1be8dfd11e68dc8e6382f98e08e6c23f2a4d6be6
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8337133"
---
# <a name="device-portal-for-windows-desktop"></a><span data-ttu-id="c4be3-104">Geräteportal für Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="c4be3-104">Device Portal for Windows Desktop</span></span>



<span data-ttu-id="c4be3-105">Im Windows-Geräteportal können Sie Diagnoseinformationen anzeigen und über HTTP aus dem Browserfenster mit Ihrem Desktop interagieren.</span><span class="sxs-lookup"><span data-stu-id="c4be3-105">Windows Device Portal lets you view diagnostic information and interact with your desktop over HTTP from a browser window.</span></span> <span data-ttu-id="c4be3-106">Sie haben im Geräteportal folgende Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="c4be3-106">You can use Device Portal to do the following:</span></span>
- <span data-ttu-id="c4be3-107">Anzeigen und Bearbeiten einer Liste laufender Prozesse</span><span class="sxs-lookup"><span data-stu-id="c4be3-107">See and manipulate a list of running processes</span></span>
- <span data-ttu-id="c4be3-108">Installieren, Löschen, Starten und Beenden von Apps</span><span class="sxs-lookup"><span data-stu-id="c4be3-108">Install, delete, launch, and terminate apps</span></span>
- <span data-ttu-id="c4be3-109">Ändern von WLAN-Profilen und Anzeigen der Signalstärke und der ipconfig</span><span class="sxs-lookup"><span data-stu-id="c4be3-109">Change Wi-Fi profiles, view signal strength, and see ipconfig</span></span>
- <span data-ttu-id="c4be3-110">Anzeigen von Live-Diagrammen zur Auslastung von CPU, Arbeitsspeicher, E/A, Netzwerk und GPU</span><span class="sxs-lookup"><span data-stu-id="c4be3-110">View live graphs of CPU, memory, I/O, network, and GPU usage</span></span>
- <span data-ttu-id="c4be3-111">Sammeln von Prozesssicherungen</span><span class="sxs-lookup"><span data-stu-id="c4be3-111">Collect process dumps</span></span>
- <span data-ttu-id="c4be3-112">Sammeln von ETW-Ablaufverfolgungen</span><span class="sxs-lookup"><span data-stu-id="c4be3-112">Collect ETW traces</span></span> 
- <span data-ttu-id="c4be3-113">Bearbeiten des isolierten Speichers quergeladener Apps</span><span class="sxs-lookup"><span data-stu-id="c4be3-113">Manipulate the isolated storage of sideloaded apps</span></span>

## <a name="set-up-device-portal-on-windows-desktop"></a><span data-ttu-id="c4be3-114">Einrichten von des Geräteportals unter Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="c4be3-114">Set up Device Portal on Windows Desktop</span></span>

### <a name="turn-on-developer-mode"></a><span data-ttu-id="c4be3-115">Entwicklermodus aktivieren</span><span class="sxs-lookup"><span data-stu-id="c4be3-115">Turn on developer mode</span></span>

<span data-ttu-id="c4be3-116">Ab Windows 10, Version 1607, sind einige der neueren Funktionen für den Desktop nur verfügbar, wenn der Entwicklermodus aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="c4be3-116">Starting in Windows 10, version 1607, some of the newer features for desktop are only available when developer mode is enabled.</span></span> <span data-ttu-id="c4be3-117">Informationen zum Aktivieren des Entwicklermodus finden Sie unter [Aktivieren Ihres Geräts für die Entwicklung](../get-started/enable-your-device-for-development.md).</span><span class="sxs-lookup"><span data-stu-id="c4be3-117">For information about how to enable developer mode, see [Enable your device for development](../get-started/enable-your-device-for-development.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4be3-118">In manchen Fällen wird der Entwicklermodus aufgrund von Problemen mit dem Netzwerk oder der Kompatibilität nicht ordnungsgemäß installiert.</span><span class="sxs-lookup"><span data-stu-id="c4be3-118">Sometimes, due to network or compatibility issues, developer mode won't install correctly on your device.</span></span> <span data-ttu-id="c4be3-119">Lesen Sie den [entsprechenden Abschnitt von „Aktivieren Sie Ihr Gerät für die Entwicklung”](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development#failure-to-install-developer-mode-package), um Hilfe bei der Behebung dieser Probleme zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c4be3-119">See the [relevant section of Enable your device for development](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development#failure-to-install-developer-mode-package) for help troubleshooting these issues.</span></span>

### <a name="turn-on-device-portal"></a><span data-ttu-id="c4be3-120">Geräteportal einschalten</span><span class="sxs-lookup"><span data-stu-id="c4be3-120">Turn on Device Portal</span></span>

<span data-ttu-id="c4be3-121">Sie können das Geräteportal im Bereich **Für Entwickler** unter **Einstellungen** aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c4be3-121">You can enable Device Portal in the **For developers** section of **Settings**.</span></span> <span data-ttu-id="c4be3-122">Wenn Sie es aktivieren, müssen Sie auch einen entsprechenden Benutzernamen und ein Kennwort erstellen.</span><span class="sxs-lookup"><span data-stu-id="c4be3-122">When you enable it, you must also create a corresponding username and password.</span></span> <span data-ttu-id="c4be3-123">Verwenden Sie nicht Ihr Microsoft-Konto oder andere Windows-Anmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="c4be3-123">Do not use your Microsoft account or other Windows credentials.</span></span> 

![Geräteportal-Abschnitt der Einstellungen-App](images/device-portal/device-portal-desk-settings.png) 

<span data-ttu-id="c4be3-125">Nachdem Geräteportal aktiviert wurde, werden unten im Abschnitt Links angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c4be3-125">Once Device Portal is enabled, you will see web links at the bottom of the section.</span></span> <span data-ttu-id="c4be3-126">Beachten Sie die Portnummer am Ende der aufgeführten URLs: Diese Nummer wird zufällig generiert, wenn Geräteportal aktiviert ist, sollte aber zwischen den Neustarts des Desktops konsistent bleiben.</span><span class="sxs-lookup"><span data-stu-id="c4be3-126">Take note of the port number appended to the end of the listed URLs: this number is randomly generated when Device Portal is enabled but should remain consistent between reboots of the desktop.</span></span> <span data-ttu-id="c4be3-127">Wenn Sie die Portnummern manuell festlegen möchten, sodass sie erhalten bleiben, finden Sie unter [Portnummern setzen](device-portal-desktop.md#setting-port-numbers) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="c4be3-127">If you'd like to set the port numbers manually so that they remain permanent, see [Setting port numbers](device-portal-desktop.md#setting-port-numbers).</span></span>

<span data-ttu-id="c4be3-128">Diese Links bieten zwei Möglichkeiten, sich mit dem Geräteportal zu verbinden: über das lokale Netzwerk (einschließlich VPN) oder über den lokalen Host.</span><span class="sxs-lookup"><span data-stu-id="c4be3-128">These links offer two ways to connect to Device Portal: over the local network (including VPN) or through the local host.</span></span>

### <a name="connect-to-device-portal"></a><span data-ttu-id="c4be3-129">Mit dem Geräteportal verbinden</span><span class="sxs-lookup"><span data-stu-id="c4be3-129">Connect to Device Portal</span></span>

<span data-ttu-id="c4be3-130">Um eine Verbindung über einen lokalen Host herzustellen, öffnen Sie ein Browserfenster und geben Sie die hier angezeigte Adresse für den von Ihnen verwendeten Verbindungstyp ein.</span><span class="sxs-lookup"><span data-stu-id="c4be3-130">To connet through local host, open a browser window and enter the address shown here for the connection type you're using.</span></span>

* <span data-ttu-id="c4be3-131">Localhost: `http://127.0.0.1:<PORT>` oder</span><span class="sxs-lookup"><span data-stu-id="c4be3-131">Localhost: `http://127.0.0.1:<PORT>` or</span></span> `http://localhost:<PORT>`
* <span data-ttu-id="c4be3-132">Local Network:</span><span class="sxs-lookup"><span data-stu-id="c4be3-132">Local Network:</span></span> `https://<IP address of the desktop>:<PORT>`

<span data-ttu-id="c4be3-133">Für die Authentifizierung und sichere Kommunikation ist HTTPS erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c4be3-133">HTTPS is required for authentication and secure communication.</span></span>

<span data-ttu-id="c4be3-134">Sie können die Authentifizierung deaktivieren, wenn Sie Geräteportal in einer geschützten Umgebung verwenden, z.B. in einem Testlabor, in dem Sie allen im lokalen Netzwerk vertrauen, keine persönlichen Informationen auf dem Gerät gespeichert haben und in dem spezielle Anforderungen bestehen.</span><span class="sxs-lookup"><span data-stu-id="c4be3-134">If you are using Device Portal in a protected environment, like a test lab, in which you trust everyone on your local network, have no personal information on the device, and have unique requirements, you can disable the Authentication option.</span></span> <span data-ttu-id="c4be3-135">Dies ermöglicht eine unverschlüsselte Kommunikation, und jeder, der die IP-Adresse Ihres Computers kennt, kann sich verbinden und es steuern.</span><span class="sxs-lookup"><span data-stu-id="c4be3-135">This enables unencrypted communication, and allows anyone with the IP address of your computer to connect to and control it.</span></span>

## <a name="device-portal-content-on-windows-desktop"></a><span data-ttu-id="c4be3-136">Geräteportal-Inhalte auf dem Windows-Desktop</span><span class="sxs-lookup"><span data-stu-id="c4be3-136">Device Portal content on Windows Desktop</span></span>

<span data-ttu-id="c4be3-137">Das Geräteportal auf dem Windows-Desktop bietet die Standardseiten.</span><span class="sxs-lookup"><span data-stu-id="c4be3-137">Device Portal on Windows Desktop provides the standard set of pages.</span></span> <span data-ttu-id="c4be3-138">Ausführliche Beschreibungen finden Sie unter [Übersicht über das Windows-Geräteportal](device-portal.md).</span><span class="sxs-lookup"><span data-stu-id="c4be3-138">For detailed descriptions of these, see [Windows Device Portal overview](device-portal.md).</span></span>

- <span data-ttu-id="c4be3-139">App-Manager</span><span class="sxs-lookup"><span data-stu-id="c4be3-139">Apps manager</span></span>
- <span data-ttu-id="c4be3-140">Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="c4be3-140">File explorer</span></span>
- <span data-ttu-id="c4be3-141">Laufende Prozesse</span><span class="sxs-lookup"><span data-stu-id="c4be3-141">Running Processes</span></span>
- <span data-ttu-id="c4be3-142">Leistung</span><span class="sxs-lookup"><span data-stu-id="c4be3-142">Performance</span></span>
- <span data-ttu-id="c4be3-143">Debugging</span><span class="sxs-lookup"><span data-stu-id="c4be3-143">Debug</span></span>
- <span data-ttu-id="c4be3-144">Ereignisablaufverfolgung für Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="c4be3-144">Event Tracing for Windows (ETW)</span></span>
- <span data-ttu-id="c4be3-145">Leistungsüberwachung</span><span class="sxs-lookup"><span data-stu-id="c4be3-145">Performance tracing</span></span>
- <span data-ttu-id="c4be3-146">Geräte-Manager</span><span class="sxs-lookup"><span data-stu-id="c4be3-146">Device manager</span></span>
- <span data-ttu-id="c4be3-147">Networking</span><span class="sxs-lookup"><span data-stu-id="c4be3-147">Networking</span></span>
- <span data-ttu-id="c4be3-148">Absturzdaten</span><span class="sxs-lookup"><span data-stu-id="c4be3-148">Crash data</span></span>
- <span data-ttu-id="c4be3-149">Features</span><span class="sxs-lookup"><span data-stu-id="c4be3-149">Features</span></span>
- <span data-ttu-id="c4be3-150">Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c4be3-150">Mixed Reality</span></span>
- <span data-ttu-id="c4be3-151">Streaming Install-Debugger</span><span class="sxs-lookup"><span data-stu-id="c4be3-151">Streaming Install Debugger</span></span>
- <span data-ttu-id="c4be3-152">Speicherort</span><span class="sxs-lookup"><span data-stu-id="c4be3-152">Location</span></span>
- <span data-ttu-id="c4be3-153">Entwurf</span><span class="sxs-lookup"><span data-stu-id="c4be3-153">Scratch</span></span>

## <a name="more-device-portal-options"></a><span data-ttu-id="c4be3-154">Weitere Optionen für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="c4be3-154">More Device Portal options</span></span>
### <a name="registry-based-configuration-for-device-portal"></a><span data-ttu-id="c4be3-155">Registrierungsbasierte Konfiguration für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="c4be3-155">Registry-based configuration for Device Portal</span></span>

<span data-ttu-id="c4be3-156">Wenn Sie Portnummern für Geräteportal auswählen möchten (z. B. 80 und 443), können Sie die folgenden Registrierungsschlüssel festlegen:</span><span class="sxs-lookup"><span data-stu-id="c4be3-156">If you would like to select port numbers for Device Portal (such as 80 and 443), you can set the following regkeys:</span></span>

- <span data-ttu-id="c4be3-157">Under</span><span class="sxs-lookup"><span data-stu-id="c4be3-157">Under</span></span> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\WebManagement\Service`
    - `UseDynamicPorts`<span data-ttu-id="c4be3-158">: Ein erforderlicher DWORD-Wert.</span><span class="sxs-lookup"><span data-stu-id="c4be3-158">: A required DWORD.</span></span> <span data-ttu-id="c4be3-159">Legen Sie den Wert auf 0 fest, um die von Ihnen ausgewählten Portnummern beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="c4be3-159">Set this to 0 in order to retain the port numbers you've chosen.</span></span>
    - `HttpPort`<span data-ttu-id="c4be3-160">: Ein erforderlicher DWORD-Wert.</span><span class="sxs-lookup"><span data-stu-id="c4be3-160">: A required DWORD.</span></span> <span data-ttu-id="c4be3-161">Enthält die Portnummer, an der Geräteportal nach HTTP-Verbindungen lauscht.</span><span class="sxs-lookup"><span data-stu-id="c4be3-161">Contains the port number that Device Portal will listen for HTTP connections on.</span></span>    
    - `HttpsPort`<span data-ttu-id="c4be3-162">: Ein erforderlicher DWORD-Wert.</span><span class="sxs-lookup"><span data-stu-id="c4be3-162">: A required DWORD.</span></span> <span data-ttu-id="c4be3-163">Enthält die Portnummer, an der Geräteportal nach HTTPS-Verbindungen lauscht.</span><span class="sxs-lookup"><span data-stu-id="c4be3-163">Contains the port number that Device Portal will listen for HTTPS connections on.</span></span>
    
<span data-ttu-id="c4be3-164">Unter dem gleichen regkey-Pfad können Sie auch die Authentifizierungsanforderung deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="c4be3-164">Under the same regkey path, you can also turn off the authentication requirement:</span></span>
- `UseDefaultAuthorizer`<span data-ttu-id="c4be3-165"> - `0` für deaktiviert, `1` für aktiviert.</span><span class="sxs-lookup"><span data-stu-id="c4be3-165"> - `0` for disabled, `1` for enabled.</span></span>  
    - <span data-ttu-id="c4be3-166">Dies steuert sowohl die grundlegende Authentifizierungsanforderung für jede Verbindung als auch die Weiterleitung von HTTP nach HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c4be3-166">This controls both the basic auth requirement for each connection and the redirect from HTTP to HTTPS.</span></span>  
    
### <a name="command-line-options-for-device-portal"></a><span data-ttu-id="c4be3-167">Befehlszeilenoptionen für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="c4be3-167">Command line options for Device Portal</span></span>
<span data-ttu-id="c4be3-168">Über eine administrative Eingabeaufforderung können Sie Teile des Geräteportal aktivieren und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c4be3-168">From an administrative command prompt, you can enable and configure parts of Device Portal.</span></span> <span data-ttu-id="c4be3-169">Um den neuesten Satz von Befehlen zu sehen, die von Ihrem Build unterstützt werden, können Sie Folgendes ausführen</span><span class="sxs-lookup"><span data-stu-id="c4be3-169">To see the latest set of commands supported on your build, you can run</span></span> `webmanagement /?`

- `sc start webmanagement` <span data-ttu-id="c4be3-170">oder</span><span class="sxs-lookup"><span data-stu-id="c4be3-170">or</span></span> `sc stop webmanagement` 
    - <span data-ttu-id="c4be3-171">Schalten Sie den Dienst ein oder aus.</span><span class="sxs-lookup"><span data-stu-id="c4be3-171">Turn the service on or off.</span></span> <span data-ttu-id="c4be3-172">Dazu muss ebenfalls der Entwicklermodus aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="c4be3-172">This still requires developer mode to be enabled.</span></span> 
- `-Credentials <username> <password>` 
    - <span data-ttu-id="c4be3-173">Legen Sie einen Benutzernamen und ein Passwort für das Geräteportal fest.</span><span class="sxs-lookup"><span data-stu-id="c4be3-173">Set a username and password for Device Portal.</span></span> <span data-ttu-id="c4be3-174">Der Benutzername muss den Basic-Auth-Standards entsprechen, darf also keinen Doppelpunkt (:) enthalten und sollte aus Standard-ASCII-Zeichen wie z. B. [a-z, A-Z, 0-9] aufgebaut sein, da Browser standardmäßig nicht den gesamten Zeichensatz verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="c4be3-174">The username must conform to Basic Auth standards, so cannot contain a colon (:) and should be built out of standard ASCII characters e.g. [a-zA-Z0-9] as browsers do not parse the full character set in a standard way.</span></span>  
- `-DeleteSSL` 
    - <span data-ttu-id="c4be3-175">Dadurch wird der für HTTPS-Verbindungen verwendete SSL-Zertifikat-Cache zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="c4be3-175">This resets the SSL certificate cache used for HTTPS connections.</span></span> <span data-ttu-id="c4be3-176">Wenn Sie auf TLS-Verbindungsfehler stoßen, die nicht umgangen werden können (im Gegensatz zur erwarteten Zertifikatswarnung), kann diese Option das Problem für Sie beheben.</span><span class="sxs-lookup"><span data-stu-id="c4be3-176">If you encounter TLS connection errors that cannot be bypassed (as opposed to the expected certificate warning), this option may fix the problem for you.</span></span> 
- `-SetCert <pfxPath> <pfxPassword>`
    - <span data-ttu-id="c4be3-177">Weitere Informationen finden Sie unter [Bereitstellen eines Geräteportals mit einem benutzerdefinierten SSL-Zertifikat](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span><span class="sxs-lookup"><span data-stu-id="c4be3-177">See [Provisioning Device Portal with a custom SSL certificate](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl) for details.</span></span>  
    - <span data-ttu-id="c4be3-178">Auf diese Weise können Sie Ihr eigenes SSL-Zertifikat installieren, um die SSL-Warnseite zu reparieren, die normalerweise im Geräteportal angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c4be3-178">This allows you to install your own SSL certificate to fix the SSL warning page that is typically seen in Device Portal.</span></span> 
- `-Debug <various options for authentication, port selection, and tracing level>`
    - <span data-ttu-id="c4be3-179">Führen Sie eine eigenständige Version des Geräteportals mit einer bestimmten Konfiguration und sichtbaren Debug-Meldungen aus.</span><span class="sxs-lookup"><span data-stu-id="c4be3-179">Run a standalone version of Device Portal with a specific configuration and visible debug messages.</span></span> <span data-ttu-id="c4be3-180">Dies ist besonders nützlich für die Erstellung eines [gepackten Plugins](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-plugin).</span><span class="sxs-lookup"><span data-stu-id="c4be3-180">This is most useful for building a [packaged plugin](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-plugin).</span></span> 
    - <span data-ttu-id="c4be3-181">Lesen Sie den [Artikel im MSDN Magazine](https://msdn.microsoft.com/en-us/magazine/mt826332.aspx) mit Details darüber, wie Sie es als „System” ausführen können, um Ihr gepacktes Plugin vollständig zu testen.</span><span class="sxs-lookup"><span data-stu-id="c4be3-181">See the [MSDN Magazine article](https://msdn.microsoft.com/en-us/magazine/mt826332.aspx) for details on how to run this as System to fully test your packaged plugin.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4be3-182">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="c4be3-182">See also</span></span>

* [<span data-ttu-id="c4be3-183">Übersicht über das Windows Geräteportal</span><span class="sxs-lookup"><span data-stu-id="c4be3-183">Windows Device Portal overview</span></span>](device-portal.md)
* [<span data-ttu-id="c4be3-184">Referenz zu Kern-APIs des Geräteportal</span><span class="sxs-lookup"><span data-stu-id="c4be3-184">Device Portal core API reference</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
