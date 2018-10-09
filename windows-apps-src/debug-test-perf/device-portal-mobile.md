---
author: PatrickFarley
ms.assetid: 5c34c78e-9ff7-477b-87f6-a31367cd3f8b
title: Geräteportal für mobile Geräte
description: Hier erfahren Sie, wie Sie mit dem Windows Device Portal Ihr mobiles Gerät per Fernzugriff konfigurieren und verwalten können.
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Device portal
ms.localizationpriority: medium
ms.openlocfilehash: 0531cbefef509f7bc323829031b366bec3c798d8
ms.sourcegitcommit: fbdc9372dea898a01c7686be54bea47125bab6c0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2018
ms.locfileid: "4424978"
---
# <a name="device-portal-for-mobile"></a><span data-ttu-id="6be80-104">Device Portal für Mobilgeräte</span><span class="sxs-lookup"><span data-stu-id="6be80-104">Device Portal for Mobile</span></span>

<span data-ttu-id="6be80-105">Ab Windows 10, Version 1511, sind weitere Entwicklerfeatures für Mobilgeräte verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6be80-105">Starting in Windows 10, Version 1511, additional developer features are available for the mobile device family.</span></span> <span data-ttu-id="6be80-106">Diese Features sind nur verfügbar, wenn der Entwicklermodus auf dem Gerät aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="6be80-106">These features are available only when Developer mode is enabled on the device.</span></span>

<span data-ttu-id="6be80-107">Informationen zum Aktivieren des Entwicklermodus finden Sie unter [Aktivieren Ihres Geräts für die Entwicklung](../get-started/enable-your-device-for-development.md).</span><span class="sxs-lookup"><span data-stu-id="6be80-107">For info about how to enable Developer mode, see [Enable your device for development](../get-started/enable-your-device-for-development.md).</span></span>

![Device Portal-Einstellungen](images/device-portal/mob-dev-mode-options.png)

## <a name="set-up-device-portal-on-windows-phone"></a><span data-ttu-id="6be80-109">Einrichten eines Device Portal auf Windows Phone</span><span class="sxs-lookup"><span data-stu-id="6be80-109">Set up Device Portal on Windows Phone</span></span>

### <a name="turn-on-device-discovery-and-pairing"></a><span data-ttu-id="6be80-110">Aktivieren der Geräteermittlung und -kopplung</span><span class="sxs-lookup"><span data-stu-id="6be80-110">Turn on device discovery and pairing</span></span>

<span data-ttu-id="6be80-111">Damit Sie eine Verbindung mit Device Portal herstellen können, müssen Sie in den Einstellungen Ihres Telefons die Geräteermittlung und Device Portal aktivieren.</span><span class="sxs-lookup"><span data-stu-id="6be80-111">To connect to Device Portal, you must enable Device discovery and Device Portal in your phone's settings.</span></span> <span data-ttu-id="6be80-112">Auf diese Weise können Sie Ihr Telefon mit einem PC oder einem anderen Windows 10-Gerät koppeln.</span><span class="sxs-lookup"><span data-stu-id="6be80-112">This lets you pair your phone with a PC or other Windows 10 device.</span></span> <span data-ttu-id="6be80-113">Beide Geräte müssen über eine kabelgebundene oder drahtlose Verbindung mit dem gleichen Subnetz des Netzwerks verbunden sein oder über USB verbunden werden.</span><span class="sxs-lookup"><span data-stu-id="6be80-113">Both devices must be connected to the same subnet of the network by a wired or wireless connection, or they must be connected by USB.</span></span>

<span data-ttu-id="6be80-114">Wenn Sie das erste Mal eine Verbindung mit dem Geräteportal herstellen, werden Sie aufgefordert, einen sechsstelligen Sicherheitscode einzugeben (mit Beachtung der Groß- und Kleinschreibung).</span><span class="sxs-lookup"><span data-stu-id="6be80-114">The first time you connect to Device Portal, you are asked for a case-sensitive, 6 character security code.</span></span> <span data-ttu-id="6be80-115">Dadurch wird sichergestellt, dass Sie Zugriff auf das Smartphone haben, und Sie werden vor Angriffen geschützt.</span><span class="sxs-lookup"><span data-stu-id="6be80-115">This ensures that you have access to the phone, and keeps you safe from attackers.</span></span> <span data-ttu-id="6be80-116">Tippen Sie auf Ihrem Smartphone auf die Schaltfläche „Koppeln“, um den Code zu generieren und anzuzeigen. Geben Sie dann die sechs Zeichen in das Textfeld im Browser ein.</span><span class="sxs-lookup"><span data-stu-id="6be80-116">Press the Pair button on your phone to generate and display the code, then enter the 6 characters into the text box in the browser.</span></span>

![Einstellungen für die Geräteerkennung im Entwicklermodus](images/device-portal/mob-dev-mode-pairing.png)

<span data-ttu-id="6be80-118">Sie haben 3 Möglichkeiten zum Herstellen einer Verbindung mit dem Geräteportal: USB, über einen lokalen Host und über das lokale Netzwerk (einschließlich VPN und Tethering).</span><span class="sxs-lookup"><span data-stu-id="6be80-118">You can choose from 3 ways to connect to Device Portal: USB, local host, and over the local network (including VPN and tethering).</span></span>

**<span data-ttu-id="6be80-119">So erstellen Sie eine Verbindung mit dem Geräteportal</span><span class="sxs-lookup"><span data-stu-id="6be80-119">To connect to Device Portal</span></span>**

1. <span data-ttu-id="6be80-120">Geben Sie in Ihrem Browser die hier angegebene Adresse für den verwendeten Verbindungstyp ein.</span><span class="sxs-lookup"><span data-stu-id="6be80-120">In your browser, enter the address shown here for the connection type you're using.</span></span>

    - <span data-ttu-id="6be80-121">USB: </span><span class="sxs-lookup"><span data-stu-id="6be80-121">USB:</span></span> `http://127.0.0.1:10080`

    <span data-ttu-id="6be80-122">Verwenden Sie diese Adresse, wenn das Smartphone über USB mit einem PC verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="6be80-122">Use this address when the phone is connected to a PC via a USB connection.</span></span> <span data-ttu-id="6be80-123">Auf beiden Geräten muss Windows 10, Version 1511 oder höher, ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6be80-123">Both devices must have Windows 10, Version 1511 or later.</span></span>
    
    - <span data-ttu-id="6be80-124">Lokaler Host: </span><span class="sxs-lookup"><span data-stu-id="6be80-124">Localhost:</span></span> `http://127.0.0.1`

    <span data-ttu-id="6be80-125">Verwenden Sie diese Adresse, um das Geräteportal lokal auf dem Smartphone in Microsoft Edge für Windows 10 Mobile anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6be80-125">Use this address to view Device Portal locally on the phone in Microsoft Edge for Windows 10 Mobile.</span></span>
    
    - <span data-ttu-id="6be80-126">Lokales Netzwerk: </span><span class="sxs-lookup"><span data-stu-id="6be80-126">Local Network:</span></span> `https://<The IP address or hostname of the phone>`

    <span data-ttu-id="6be80-127">Verwenden Sie diese Adresse, um die Verbindung über ein lokales Netzwerk herzustellen.</span><span class="sxs-lookup"><span data-stu-id="6be80-127">Use this address to connect over a local network.</span></span>

    <span data-ttu-id="6be80-128">Die IP-Adresse des Smartphones wird in den Geräteportaleinstellungen auf dem Telefon angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6be80-128">The IP address of the phone is shown in the Device Portal settings on the phone.</span></span> <span data-ttu-id="6be80-129">Für die Authentifizierung und sichere Kommunikation ist HTTPS erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6be80-129">HTTPS is required for authentication and secure communication.</span></span> <span data-ttu-id="6be80-130">Der Hostname (kann in „Einstellungen“ > „System“ > „Info“ bearbeitet werden) kann auch für den Zugriff auf das Geräteportal im lokalen Netzwerk verwendet werden (Beispiel: http://Phone360)). Dies ist hilfreich, wenn Netzwerke oder IP-Adressen von Geräten häufig geändert werden oder freigegeben werden müssen.</span><span class="sxs-lookup"><span data-stu-id="6be80-130">The hostname (editable in Settings > System > About) can also be used to access Device Portal on the local network (e.g. http://Phone360), which is useful for devices that may change networks or IP addresses frequently, or need to be shared.</span></span> 

2. <span data-ttu-id="6be80-131">Tippen Sie auf Ihrem Smartphone auf die Schaltfläche „Koppeln“, um den Code zu generieren und anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6be80-131">Press the Pair button on your phone to generate and display the required security code</span></span>

3. <span data-ttu-id="6be80-132">Geben Sie den sechsstelligen Sicherheitscode im Browser in das Kennwortfeld des Geräteportals ein.</span><span class="sxs-lookup"><span data-stu-id="6be80-132">Enter the 6 character security code into the Device Portal password box in your browser.</span></span>

4. <span data-ttu-id="6be80-133">(Optional) Aktivieren Sie das Kontrollkästchen Computer merken in Ihrem Browser, um diese Kopplung für die spätere Verwendung zu speichern.</span><span class="sxs-lookup"><span data-stu-id="6be80-133">(Optional) Check the Remember my computer box in your browser to remember this pairing in the future.</span></span>

<span data-ttu-id="6be80-134">Dies ist der Geräteportalabschnitt auf der Seite mit den Entwicklerseiten in Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="6be80-134">Here's the Device Portal section of the developer settings page on Windows Phone.</span></span>

![Einstellungen im Geräteportal](images/device-portal/mob-dev-mode-portal.png)

<span data-ttu-id="6be80-136">Sie können die Authentifizierung deaktivieren, wenn Sie Device Portal in einer geschützten Umgebung verwenden, z.B. in einem Testlabor, in dem Sie allen im lokalen Netzwerk vertrauen, keine persönlichen Informationen auf dem Gerät gespeichert haben und in dem spezielle Anforderungen bestehen.</span><span class="sxs-lookup"><span data-stu-id="6be80-136">If you are using Device Portal in a protected environment, like a test lab, where you trust everyone on your local network, have no personal information on the device, and have unique requirements, you can disable authentication.</span></span> <span data-ttu-id="6be80-137">Dies ermöglicht eine unverschlüsselte Kommunikation, und jeder, der die IP-Adresse Ihres Smartphones kennt, kann es steuern.</span><span class="sxs-lookup"><span data-stu-id="6be80-137">This enables unencrypted communication, and allows anyone with the IP address of your phone to control it.</span></span>

## <a name="tool-notes"></a><span data-ttu-id="6be80-138">Anmerkungen zu Tools</span><span class="sxs-lookup"><span data-stu-id="6be80-138">Tool Notes</span></span>

## <a name="device-portal-pages"></a><span data-ttu-id="6be80-139">Seiten des Geräteportals</span><span class="sxs-lookup"><span data-stu-id="6be80-139">Device Portal pages</span></span>
### <a name="processes"></a><span data-ttu-id="6be80-140">Prozesse</span><span class="sxs-lookup"><span data-stu-id="6be80-140">Processes</span></span>

<span data-ttu-id="6be80-141">Im Windows Mobile Device Portal ist es nicht möglich, beliebige Prozesse zu beenden.</span><span class="sxs-lookup"><span data-stu-id="6be80-141">The ability to terminate arbitrary processes is not included in the Windows Mobile Device Portal.</span></span> 

<span data-ttu-id="6be80-142">Das Geräteportal für mobile Geräte enthält den Standardsatz der Seiten.</span><span class="sxs-lookup"><span data-stu-id="6be80-142">Device Portal on mobile devices provides the standard set of pages.</span></span> <span data-ttu-id="6be80-143">Ausführliche Beschreibungen finden Sie unter [Übersicht über das Windows Device Portal](device-portal.md).</span><span class="sxs-lookup"><span data-stu-id="6be80-143">For detailed descriptions, see [Windows Device Portal overview](device-portal.md).</span></span>

- <span data-ttu-id="6be80-144">App-Manager</span><span class="sxs-lookup"><span data-stu-id="6be80-144">App Manager</span></span>
- <span data-ttu-id="6be80-145">App-Datei-Explorer (Isolierter Speicher-Explorer)</span><span class="sxs-lookup"><span data-stu-id="6be80-145">App File Explorer (Isolated Storage Explorer)</span></span>
- <span data-ttu-id="6be80-146">Prozesse</span><span class="sxs-lookup"><span data-stu-id="6be80-146">Processes</span></span>
- <span data-ttu-id="6be80-147">Leistungsdiagramme</span><span class="sxs-lookup"><span data-stu-id="6be80-147">Performance charts</span></span>
- <span data-ttu-id="6be80-148">Ereignisablaufverfolgung für Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="6be80-148">Event Tracing for Windows (ETW)</span></span>
- <span data-ttu-id="6be80-149">Leistungsüberwachung (WPR)</span><span class="sxs-lookup"><span data-stu-id="6be80-149">Performance tracing (WPR)</span></span> 
- <span data-ttu-id="6be80-150">Geräte</span><span class="sxs-lookup"><span data-stu-id="6be80-150">Devices</span></span>
- <span data-ttu-id="6be80-151">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="6be80-151">Networking</span></span>

## <a name="see-also"></a><span data-ttu-id="6be80-152">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="6be80-152">See also</span></span>

* [<span data-ttu-id="6be80-153">Übersicht über das Windows Geräteportal</span><span class="sxs-lookup"><span data-stu-id="6be80-153">Windows Device Portal overview</span></span>](device-portal.md)
* [<span data-ttu-id="6be80-154">Referenz zu Kern-APIs des Geräteportal</span><span class="sxs-lookup"><span data-stu-id="6be80-154">Device Portal core API reference</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)