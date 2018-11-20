---
author: stevewhims
description: Aktionen, die Sie für eine netzwerkfähige App ausführen müssen.
title: Vernetzungsgrundlagen
ms.assetid: 1F47D33B-6F00-4F74-A52D-538851FD38BE
ms.author: stwhi
ms.date: 06/01/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 50ac9fcf984fa6c4ebad7e480ebfc2d002256e26
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7301408"
---
# <a name="networking-basics"></a><span data-ttu-id="a3437-104">Networking-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="a3437-104">Networking basics</span></span>
<span data-ttu-id="a3437-105">Aktionen, die Sie für eine netzwerkfähige App ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="a3437-105">Things you must do for any network-enabled app.</span></span>

## <a name="capabilities"></a><span data-ttu-id="a3437-106">Funktionen</span><span class="sxs-lookup"><span data-stu-id="a3437-106">Capabilities</span></span>
<span data-ttu-id="a3437-107">Um das Netzwerk verwenden zu können, müssen Sie die entsprechenden Funktionselemente zum App-Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a3437-107">In order to use networking, you must add appropriate capability elements to your app manifest.</span></span> <span data-ttu-id="a3437-108">Wenn in Ihrem App-Manifest keine Netzwerkfunktion angegeben ist, besitzt Ihre App keine Netzwerkfunktion, und jeder Versuch, eine Verbindung mit dem Netzwerk herzustellen, führt zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="a3437-108">If no network capability is specified in your app's manifest, your app will have no networking capability, and any attempt to connect to the network will fail.</span></span>

<span data-ttu-id="a3437-109">Im Folgenden finden Sie die am häufigsten verwendeten Netzwerkfunktionen:</span><span class="sxs-lookup"><span data-stu-id="a3437-109">The following are the most-used networking capabilities.</span></span>

| <span data-ttu-id="a3437-110">Funktion</span><span class="sxs-lookup"><span data-stu-id="a3437-110">Capability</span></span> | <span data-ttu-id="a3437-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a3437-111">Description</span></span> |
|------------|-------------|
| **<span data-ttu-id="a3437-112">internetClient</span><span class="sxs-lookup"><span data-stu-id="a3437-112">internetClient</span></span>** | <span data-ttu-id="a3437-113">Bietet ausgehenden Zugriff auf das Internet und Netzwerke an öffentlichen Orten wie Flughäfen und Cafés.</span><span class="sxs-lookup"><span data-stu-id="a3437-113">Provides outbound access to the Internet and networks in public places, like airports and coffee shop.</span></span> <span data-ttu-id="a3437-114">Diese Funktion sollte von den meisten Apps verwendet werden, die einen Internetzugriff benötigen.</span><span class="sxs-lookup"><span data-stu-id="a3437-114">Most apps that require Internet access should use this capability.</span></span> |
| **<span data-ttu-id="a3437-115">internetClientServer</span><span class="sxs-lookup"><span data-stu-id="a3437-115">internetClientServer</span></span>** | <span data-ttu-id="a3437-116">Bietet der App ein- und ausgehenden Netzwerkzugriff aus dem Internet und aus Netzwerken an öffentlichen Orten wie Flughäfen und Cafés.</span><span class="sxs-lookup"><span data-stu-id="a3437-116">Gives the app inbound and outbound network access from the Internet and networks in public places like airports and coffee shops.</span></span> |
| **<span data-ttu-id="a3437-117">privateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="a3437-117">privateNetworkClientServer</span></span>** | <span data-ttu-id="a3437-118">Bietet der App eingehenden und ausgehenden Netzwerkzugriff an vertrauenswürdigen Orten des Benutzers (z. B. zu Hause und am Arbeitsplatz).</span><span class="sxs-lookup"><span data-stu-id="a3437-118">Gives the app inbound and outbound network access at the user's trusted places, like home and work.</span></span> |

<span data-ttu-id="a3437-119">In bestimmten Situationen sind möglicherweise weitere Funktionen für Ihre App erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a3437-119">There are other capabilities that might be necessary for your app, in certain circumstances.</span></span>

| <span data-ttu-id="a3437-120">Funktion</span><span class="sxs-lookup"><span data-stu-id="a3437-120">Capability</span></span> | <span data-ttu-id="a3437-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a3437-121">Description</span></span> |
|------------|-------------|
| **<span data-ttu-id="a3437-122">enterpriseAuthentication</span><span class="sxs-lookup"><span data-stu-id="a3437-122">enterpriseAuthentication</span></span>** | <span data-ttu-id="a3437-123">Ermöglicht einer App, eine Verbindung mit Netzwerkressourcen herzustellen, für die Domänenanmeldeinformationen nötig sind.</span><span class="sxs-lookup"><span data-stu-id="a3437-123">Allows an app to connect to network resources that require domain credentials.</span></span> <span data-ttu-id="a3437-124">Bei dieser Funktion muss ein Domänenadministrator die Funktionalität für alle Apps aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a3437-124">This capability will require a domain administrator to enable the functionality for all apps.</span></span> <span data-ttu-id="a3437-125">Beispielsweise kann es sich um eine App handeln, die Daten von SharePoint-Servern in einem privaten Intranet abruft.</span><span class="sxs-lookup"><span data-stu-id="a3437-125">An example would be an app that retrieves data from SharePoint servers on a private Intranet.</span></span> <br/> <span data-ttu-id="a3437-126">Mit dieser Funktion können Ihre Anmeldeinformationen für den Zugriff auf Netzwerkressourcen in einem Netzwerk verwendet werden, für das Anmeldeinformationen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="a3437-126">With this capability your credentials can be used to access network resources on a network that requires credentials.</span></span> <span data-ttu-id="a3437-127">Eine App mit dieser Funktion kann Ihre Identität im Netzwerk annehmen.</span><span class="sxs-lookup"><span data-stu-id="a3437-127">An app with this capability can impersonate you on the network.</span></span> <br/> <span data-ttu-id="a3437-128">Für den Internetzugriff einer App mithilfe eines Authentifizierungsproxys ist diese Funktion nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a3437-128">This capability is not required to allow an app to access the Internet via an authenticating proxy.</span></span> |
| **<span data-ttu-id="a3437-129">proximity</span><span class="sxs-lookup"><span data-stu-id="a3437-129">proximity</span></span>** | <span data-ttu-id="a3437-130">Sie ist für die Nahfeldnäherungskommunikation mit Geräten in geringem Abstand zum Computer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a3437-130">Required for near-field proximity communication with devices in close proximity to the computer.</span></span> <span data-ttu-id="a3437-131">Die Nahfeldnäherung kann zum Senden an eine Anwendung oder Verbinden mit einer Anwendung auf einem in der Nähe befindlichen Gerät verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a3437-131">Near-field proximity may be used to send or connect with an application on a nearby device.</span></span> <br/> <span data-ttu-id="a3437-132">Mit dieser Funktion kann eine App auf das Netzwerk zugreifen, um eine Verbindung mit einem Gerät in geringem Abstand herzustellen und mit der Zustimmen des Benutzers eine Einladung zu senden oder anzunehmen.</span><span class="sxs-lookup"><span data-stu-id="a3437-132">This capability allows an app to access the network to connect to a device in close proximity, with user consent to send an invite or accept an invite.</span></span> |
| **<span data-ttu-id="a3437-133">sharedUserCertificates</span><span class="sxs-lookup"><span data-stu-id="a3437-133">sharedUserCertificates</span></span>** | <span data-ttu-id="a3437-134">Ermöglicht einer App den Zugriff auf Software- und Hardwarezertifikate wie etwa Smartcardzertifikate.</span><span class="sxs-lookup"><span data-stu-id="a3437-134">This capability allows an app to access software and hardware certificates, such as smart card certificates.</span></span> <span data-ttu-id="a3437-135">Wenn diese Funktion zur Laufzeit aufgerufen wird, muss der Benutzer eine Aktion ausführen (z. B. eine Karte einsetzen oder ein Zertifikat auswählen).</span><span class="sxs-lookup"><span data-stu-id="a3437-135">When this capability is invoked at runtime, the user must take action, such as inserting a card or selecting a certificate.</span></span> <br/> <span data-ttu-id="a3437-136">Bei dieser Funktion werden Ihre Software- und Hardwarezertifikate oder eine Smartcard zur Identifikation in der Anwendung verwendet.</span><span class="sxs-lookup"><span data-stu-id="a3437-136">With this capability, your software and hardware certificates or a smart card are used for identification in the app.</span></span> <span data-ttu-id="a3437-137">Diese Funktion kann von Ihrem Arbeitgeber, Ihrer Bank oder Regierungsbehörden zur Identifikation verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a3437-137">This capability may be used by your employer, bank, or government services for identification.</span></span> |

## <a name="communicating-when-your-app-is-not-in-the-foreground"></a><span data-ttu-id="a3437-138">Kommunikation, wenn Ihre App nicht im Vordergrund ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="a3437-138">Communicating when your app is not in the foreground</span></span>
<span data-ttu-id="a3437-139">[Unterstützen Ihrer App mit Hintergrundaufgaben](https://msdn.microsoft.com/library/windows/apps/mt299103) enthält allgemeine Informationen zur Verwendung von Hintergrundaufgaben, um Aufgaben auszuführen, während sich Ihre App nicht im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="a3437-139">[Support your app with background tasks](https://msdn.microsoft.com/library/windows/apps/mt299103) contains general information about using background tasks to do work when your app is not in the foreground.</span></span> <span data-ttu-id="a3437-140">Genauer gesagt muss Ihr Code besondere Schritte vornehmen, damit eine Benachrichtigung erfolgt, wenn es sich dabei nicht um die aktuelle App im Vordergrund handelt und diese Daten über das Netzwerk empfängt.</span><span class="sxs-lookup"><span data-stu-id="a3437-140">More specifically, your code must take special steps to be notified when it is not the current foreground app and data arrives over the network for it.</span></span> <span data-ttu-id="a3437-141">Sie in Windows8 zu diesem Zweck Steuerkanalauslöser verwendet, und sie werden in Windows 10 weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a3437-141">You used Control Channel Triggers for this purpose in Windows8, and they are still supported in Windows10.</span></span> <span data-ttu-id="a3437-142">Vollständige Informationen zur Verwendung der Steuerkanalauslöser finden Sie [**hier**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span><span class="sxs-lookup"><span data-stu-id="a3437-142">Full information about using Control Channel Triggers is available [**here**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span> <span data-ttu-id="a3437-143">Eine neue Technologie in Windows 10 bietet eine bessere Funktionalität mit weniger Aufwand für einige Szenarien, wie etwa pushfähige Datenstromsockets: die socketbroker und Socket-aktivitätsauslöser.</span><span class="sxs-lookup"><span data-stu-id="a3437-143">A new technology in Windows10 provides better functionality with lower overhead for some scenarios, such as push-enabled stream sockets: the socket broker and socket activity triggers.</span></span>

<span data-ttu-id="a3437-144">Wenn die App [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319), [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) oder [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906) verwendet, kann sie die Beteiligung eines offenen Sockets an einen vom System bereitgestellten Socketbroker übertragen und sie dann im Vordergrund belassen oder sogar beenden.</span><span class="sxs-lookup"><span data-stu-id="a3437-144">If your app uses [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319), [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882), or [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906), then your app can transfer ownership of an open socket to a socket broker provided by the system, and then leave the foreground, or even terminate.</span></span> <span data-ttu-id="a3437-145">Wenn eine Verbindung zum übertragenen Socket hergestellt oder Datenverkehr auf diesem Socket empfangen wird, wird Ihre App oder die festgelegten Hintergrundaufgabe aktiviert.</span><span class="sxs-lookup"><span data-stu-id="a3437-145">When a connection is made on the transferred socket, or traffic arrives on that socket, then your app or its designated background task are activated.</span></span> <span data-ttu-id="a3437-146">Wenn Ihre App nicht ausgeführt wird, wird sie gestartet.</span><span class="sxs-lookup"><span data-stu-id="a3437-146">If your app is not running, it is started.</span></span> <span data-ttu-id="a3437-147">Der Socketbroker benachrichtigt Ihre App mittels [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009) darüber, dass neuer Datenverkehr eingegangen ist.</span><span class="sxs-lookup"><span data-stu-id="a3437-147">The socket broker then notifies your app using a [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009) that new traffic has arrived.</span></span> <span data-ttu-id="a3437-148">Ihre App gibt den Socket aus dem Socketbroker frei und verarbeitet den Datenverkehr auf dem Socket.</span><span class="sxs-lookup"><span data-stu-id="a3437-148">Your app reclaims the socket from the socket broker and process the traffic on the socket.</span></span> <span data-ttu-id="a3437-149">Das heißt, Ihre App beansprucht deutlich weniger Systemressourcen, wenn es aktiv keinen Netzwerkdatenverkehr verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="a3437-149">This means that your app consumes far less system resources when it is not actively processing network traffic.</span></span>

<span data-ttu-id="a3437-150">Der Socketbroker soll den Steuerkanal-Auslöser ersetzen, in dem er anwendbar ist, da er die gleiche Funktionalität bietet, jedoch weniger Einschränkungen besitzt und weniger Speicherbedarf benötigt.</span><span class="sxs-lookup"><span data-stu-id="a3437-150">The socket broker is intended to replace Control Channel Triggers where it is applicable, because it provides the same functionality, but with fewer restrictions and a smaller memory footprint.</span></span> <span data-ttu-id="a3437-151">Der Socketbroker kann von Sperrbildschirm-Apps verwendet werden und wird auf Telefonen und anderen Geräten auf die gleiche Weise verwendet.</span><span class="sxs-lookup"><span data-stu-id="a3437-151">Socket broker can be used by apps that are not lock screen apps, and it is used the same way on phones as on other devices.</span></span> <span data-ttu-id="a3437-152">Apps müssen nicht ausgeführt werden, wenn Datenverkehr eingeht, damit sie vom Socketbroker aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="a3437-152">Apps need not be running when traffic arrives in order to be activated by the socket broker.</span></span> <span data-ttu-id="a3437-153">Der Socketbroker unterstützt darüber hinaus die Erkennung auf TCP-Sockets. Dies ist bei Steuerkanalauslösern nicht der Fall.</span><span class="sxs-lookup"><span data-stu-id="a3437-153">And the socket broker supports listening on TCP sockets, which Control Channel Triggers do not support.</span></span>

### <a name="choosing-a-network-trigger"></a><span data-ttu-id="a3437-154">Wählen eines Netzwerkauslösers</span><span class="sxs-lookup"><span data-stu-id="a3437-154">Choosing a network trigger</span></span>
<span data-ttu-id="a3437-155">Es gibt einige Szenarien, in denen beide Auslöserarten geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="a3437-155">There are some scenarios where either kind of trigger would be suitable.</span></span> <span data-ttu-id="a3437-156">Beachten Sie bei der Auswahl der Auslöserart der App Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a3437-156">When you are choosing which kind of trigger to use in your app, consider the following advice.</span></span>

-   <span data-ttu-id="a3437-157">Bei Verwendung von [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151), [**System.Net.Http.HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) oder [System.Net.Http.HttpClientHandler](http://go.microsoft.com/fwlink/p/?linkid=241638) müssen Sie [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032) verwenden.</span><span class="sxs-lookup"><span data-stu-id="a3437-157">If you are using [**IXMLHTTPRequest2**](https://msdn.microsoft.com/library/windows/desktop/hh831151), [**System.Net.Http.HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) or [System.Net.Http.HttpClientHandler](http://go.microsoft.com/fwlink/p/?linkid=241638), you must use [**ControlChannelTrigger**](https://msdn.microsoft.com/library/windows/apps/hh701032).</span></span>
-   <span data-ttu-id="a3437-158">Wenn Sie pushfähige **StreamSockets** verwenden, können Sie Kanaltrigger und vorzugsweise [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009) verwenden.</span><span class="sxs-lookup"><span data-stu-id="a3437-158">If you are using push-enabled **StreamSockets**, you can use control channel triggers, but should prefer [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009).</span></span> <span data-ttu-id="a3437-159">In letzterem Fall kann das System Arbeitsspeicher freigeben und den Stromverbrauch verringern, wenn die Verbindung nicht aktiv verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a3437-159">The latter choice allows the system to free up memory and reduce power requirements when the connection is not being actively used.</span></span>
-   <span data-ttu-id="a3437-160">Wenn Sie den Speicherbedarf Ihrer App während der aktiven Verarbeitung von Netzwerkanforderungen minimieren möchten, sollten Sie nach Möglichkeit [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009) verwenden.</span><span class="sxs-lookup"><span data-stu-id="a3437-160">If you want to minimize the memory footprint of your app when it is not actively servicing network requests, prefer [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009) when possible.</span></span>
-   <span data-ttu-id="a3437-161">Wenn Sie möchten, dass Ihre App Daten empfängt, während sich das System im verbundenen Standbymodus befindet, verwenden Sie [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009).</span><span class="sxs-lookup"><span data-stu-id="a3437-161">If you want your app to be able to receive data while the system is in Connected Standby mode, use [**SocketActivityTrigger**](https://msdn.microsoft.com/library/windows/apps/dn806009).</span></span>

<span data-ttu-id="a3437-162">Ausführliche Informationen und Beispiele zur Verwendung des Socketbrokers finden Sie unter [Netzwerkkommunikation im Hintergrund](network-communications-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="a3437-162">For details and examples of how to use the socket broker, see [Network communications in the background](network-communications-in-the-background.md).</span></span>

## <a name="secured-connections"></a><span data-ttu-id="a3437-163">Sichere Verbindungen</span><span class="sxs-lookup"><span data-stu-id="a3437-163">Secured connections</span></span>
<span data-ttu-id="a3437-164">Secure Sockets Layer (SSL) und das aktuellere Transport Layer Security (TLS) sind Verschlüsselungsprotokolle für die Authentifizierung und Verschlüsselung der Kommunikation in Netzwerken.</span><span class="sxs-lookup"><span data-stu-id="a3437-164">Secure Sockets Layer (SSL) and the more recent Transport Layer Security (TLS) are cryptographic protocols designed to provide authentication and encryption for network communication.</span></span> <span data-ttu-id="a3437-165">Diese Protokolle dienen dazu, das Mitverfolgen und Manipulieren von Daten zu verhindern, die im Netzwerk gesendet und empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="a3437-165">These protocols are designed to prevent eavesdropping and tampering when sending and receiving network data.</span></span> <span data-ttu-id="a3437-166">Für den Protokollaustausch wird dabei ein Client-Server-Modell verwendet.</span><span class="sxs-lookup"><span data-stu-id="a3437-166">These protocols use a client-server model for the protocol exchanges.</span></span> <span data-ttu-id="a3437-167">Diese Protokolle verwenden zudem digitale Zertifikate und Zertifizierungsstellen, um den jeweiligen Server zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="a3437-167">These protocols also use digital certificates and certificate authorities to verify that the server is who it claims to be.</span></span>

### <a name="creating-secure-socket-connections"></a><span data-ttu-id="a3437-168">Erstellen von sicheren Socketverbindungen</span><span class="sxs-lookup"><span data-stu-id="a3437-168">Creating secure socket connections</span></span>
<span data-ttu-id="a3437-169">Ein [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Objekt kann für die Verwendung von SSL/TLS für die Kommunikation zwischen dem Client und dem Server konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="a3437-169">A [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) object can be configured to use SSL/TLS for communications between the client and the server.</span></span> <span data-ttu-id="a3437-170">Diese Unterstützung für SSL/TLS beschränkt sich auf die Verwendung des **StreamSocket**-Objekts als Client in der SSL/TLS-Aushandlung.</span><span class="sxs-lookup"><span data-stu-id="a3437-170">This support for SSL/TLS is limited to using the **StreamSocket** object as the client in the SSL/TLS negotiation.</span></span> <span data-ttu-id="a3437-171">Sie können SSL/TLS nicht mit dem von einer [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906)-Klasse erstellten **StreamSocket**-Objekt verwenden, wenn eingehende Kommunikation empfangen wird, da SSL/TLS-Aushandlung als Server nicht von der **StreamSocket**-Klasse implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="a3437-171">You cannot use SSL/TLS with the **StreamSocket** created by a [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906) when incoming communications are received, because SSL/TLS negotiation as a server is not implemented by the **StreamSocket** class.</span></span>

<span data-ttu-id="a3437-172">Es gibt zwei Möglichkeiten, eine [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Verbindung mit SSL/TLS zu sichern:</span><span class="sxs-lookup"><span data-stu-id="a3437-172">There are two ways to secure a [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) connection with SSL/TLS:</span></span>

-   <span data-ttu-id="a3437-173">[**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504) – Stellt die erste Verbindung mit einem Netzwerkdienst her und handelt sofort die Verwendung von SSL/TLS für jede Kommunikation aus.</span><span class="sxs-lookup"><span data-stu-id="a3437-173">[**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504) - Make the initial connection to a network service and negotiate immediately to use SSL/TLS for all communications.</span></span>
-   <span data-ttu-id="a3437-174">[**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922) – Stellt die erste Verbindung mit einem Netzwerkdienst ohne Verschlüsselung her.</span><span class="sxs-lookup"><span data-stu-id="a3437-174">[**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922) - Connect initially to a network service without encryption.</span></span> <span data-ttu-id="a3437-175">Die App kann Daten senden oder empfangen.</span><span class="sxs-lookup"><span data-stu-id="a3437-175">The app may send or receive data.</span></span> <span data-ttu-id="a3437-176">Dann wird die Verbindung für die Verwendung von SSL/TLS für jede weitere Verbindung hochgestuft.</span><span class="sxs-lookup"><span data-stu-id="a3437-176">Then, upgrade the connection to use SSL/TLS for all further communications.</span></span>

<span data-ttu-id="a3437-177">SocketProtectionLevel gibt die gewünschte Socket-Schutzebene an, mit der die App eingerichtet oder die Verbindung aktualisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="a3437-177">The SocketProtectionLevel specifies the desired socket protection level the app wants to establish or upgrade the connection with.</span></span> <span data-ttu-id="a3437-178">Die letztendliche Schutzebene der hergestellten Verbindung wird jedoch im Aushandlungsprozess zwischen beiden Endpunkten der Verbindung festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a3437-178">However, the eventual protection level of the established connection is determined in a negotiation process between both endpoints of the connection.</span></span> <span data-ttu-id="a3437-179">Dies kann zu einer niedrigeren Schutzebene führen, die sichererer als die von Ihnen angegebene Ebene ist, wenn der andere Endpunkt eine niedrigere Ebene erfordert.</span><span class="sxs-lookup"><span data-stu-id="a3437-179">The result can be a lower protection level than the one you specified, if the other endpoint requests a lower level.</span></span> 

 <span data-ttu-id="a3437-180">Nachdem der asynchrone Vorgang erfolgreich abgeschlossen wurde, können Sie die erforderliche Schutzebene abrufen, die im Aufruf von [**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504) oder [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922) über die [**StreamSocketinformation.ProtectionLevel**](https://msdn.microsoft.com/library/windows/apps/hh967868)-Eigenschaften verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a3437-180">After the async operation has completed successfully, you can retrieve the requested protection level used in the [**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504) or [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922) call through the  [**StreamSocketinformation.ProtectionLevel**](https://msdn.microsoft.com/library/windows/apps/hh967868) property.</span></span> <span data-ttu-id="a3437-181">Dies entspricht jedoch nicht der tatsächlichen Schutzebene, die in der Verbindung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a3437-181">However, this does not reflect the actual protection level the connection is using.</span></span>

> [!NOTE]
> <span data-ttu-id="a3437-182">Ihr Code sollte nicht implizit von der Verwendung einer bestimmten Schutzebene oder der Annahme abhängig sein, dass standardmäßig eine bestimmte Sicherheitsstufe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a3437-182">Your code should not implicitly depend on using a particular protection level, or on the assumption that a given security level is used by default.</span></span> <span data-ttu-id="a3437-183">Die Sicherheitslandschaft befindet sich in einem steten Wandel, und Protokolle und Standardschutzebenen ändern sich mit der Zeit, um die Verwendung von Protokollen mit bekannten Schwachstellen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="a3437-183">The security landscape changes constantly, and protocols and default protection levels change over time in order to avoid the use of protocols with known weaknesses.</span></span> <span data-ttu-id="a3437-184">Die Standardwerte können je nach Konfiguration einzelner Computer oder abhängig von der installierten Software oder angewendeten Patches variieren.</span><span class="sxs-lookup"><span data-stu-id="a3437-184">Defaults can vary depending on individual machine configuration, or on which software is installed and which patches have been applied.</span></span> <span data-ttu-id="a3437-185">Wenn Ihre App von der Verwendung einer bestimmten Sicherheitsstufe abhängt, müssen Sie diese Stufe explizit angeben und dann durch eine Überprüfung sicherstellen, dass sie tatsächlich für die hergestellte Verbindung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a3437-185">If your app depends on the use of a particular security level, then you must explicitly specify that level and then check to be sure that it is actually in use on the established connection.</span></span>

### <a name="use-connectasync"></a><span data-ttu-id="a3437-186">Verwenden von ConnectAsync</span><span class="sxs-lookup"><span data-stu-id="a3437-186">Use ConnectAsync</span></span>
<span data-ttu-id="a3437-187">[**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504) kann verwendet werden, um die erste Verbindung mit einem Netzwerkdienst herzustellen und dann sofort die Verwendung von SSL/TLS für jede Kommunikation auszuhandeln.</span><span class="sxs-lookup"><span data-stu-id="a3437-187">[**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504) can be used to establish the initial connection with a network service and then negotiate immediately to use SSL/TLS for all communications.</span></span> <span data-ttu-id="a3437-188">Es gibt zwei **ConnectAsync**-Methoden, die das Übergeben eines *protectionLevel*-Parameters unterstützen:</span><span class="sxs-lookup"><span data-stu-id="a3437-188">There are two **ConnectAsync** methods that support passing a *protectionLevel* parameter:</span></span>

-   <span data-ttu-id="a3437-189">[**ConnectAsync(EndpointPair, SocketProtectionLevel)**](https://msdn.microsoft.com/library/windows/apps/hh701511) – Startet einen asynchronen Vorgang für ein [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Objekt, um eine Verbindung mit einem Remotenetzwerkziel herzustellen, das durch ein [**EndpointPair**](https://msdn.microsoft.com/library/windows/apps/hh700953)-Objekt und eine [**SocketProtectionLevel**](https://msdn.microsoft.com/library/windows/apps/br226880) angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="a3437-189">[**ConnectAsync(EndpointPair, SocketProtectionLevel)**](https://msdn.microsoft.com/library/windows/apps/hh701511) - Starts an asynchronous operation on a [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) object to connect to a remote network destination specified as an [**EndpointPair**](https://msdn.microsoft.com/library/windows/apps/hh700953) object and a [**SocketProtectionLevel**](https://msdn.microsoft.com/library/windows/apps/br226880).</span></span>
-   <span data-ttu-id="a3437-190">[**ConnectAsync(HostName, String, SocketProtectionLevel)**](https://msdn.microsoft.com/library/windows/apps/br226916) – Startet einen asynchronen Vorgang für ein [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Objekt, um eine Verbindung mit einem Remoteziel herzustellen, das durch einen Remotehostnamen, einen Remotedienstnamen und eine [**SocketProtectionLevel**](https://msdn.microsoft.com/library/windows/apps/br226880) angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="a3437-190">[**ConnectAsync(HostName, String, SocketProtectionLevel)**](https://msdn.microsoft.com/library/windows/apps/br226916) - Starts an asynchronous operation on a [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) object to connect to a remote destination specified by a remote hostname, a remote service name, and a [**SocketProtectionLevel**](https://msdn.microsoft.com/library/windows/apps/br226880).</span></span>

<span data-ttu-id="a3437-191">Wenn der *protectionLevel*-Parameter beim Aufruf einer der obigen [**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504)-Methoden auf **Windows.Networking.Sockets.SocketProtectionLevel.Ssl** festgelegt ist, muss mit [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) die Verwendung von SSL/TLS für die Verschlüsselung sichergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="a3437-191">If the *protectionLevel* parameter is set to **Windows.Networking.Sockets.SocketProtectionLevel.Ssl** when calling either of the above [**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504) methods, the [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) must will be established to use SSL/TLS for encryption.</span></span> <span data-ttu-id="a3437-192">Dieser Wert erfordert eine Verschlüsselung, wobei keine NULL-Verschlüsselung zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="a3437-192">This value requires encryption and never allows a NULL cipher to be used.</span></span>

<span data-ttu-id="a3437-193">Der übliche Ablauf ist bei beiden [**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504)-Methoden gleich.</span><span class="sxs-lookup"><span data-stu-id="a3437-193">The normal sequence to use with one of these [**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504) methods is the same.</span></span>

-   <span data-ttu-id="a3437-194">Erstellen Sie ein [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="a3437-194">Create a [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882).</span></span>
-   <span data-ttu-id="a3437-195">Wenn eine erweiterte Option für den Socket erforderlich ist, rufen Sie mit der [**StreamSocket.Control**](https://msdn.microsoft.com/library/windows/apps/br226917)-Eigenschaft die [**StreamSocketControl**](https://msdn.microsoft.com/library/windows/apps/br226893)-Instanz ab, die einem [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Objekt zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="a3437-195">If an advanced option on the socket is needed, use the [**StreamSocket.Control**](https://msdn.microsoft.com/library/windows/apps/br226917) property to get the [**StreamSocketControl**](https://msdn.microsoft.com/library/windows/apps/br226893) instance associated with a [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) object.</span></span> <span data-ttu-id="a3437-196">Legen Sie eine Eigenschaft für **StreamSocketControl** fest.</span><span class="sxs-lookup"><span data-stu-id="a3437-196">Set a property on the **StreamSocketControl**.</span></span>
-   <span data-ttu-id="a3437-197">Rufen Sie eine der obigen [**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504)-Methoden auf, um einen Vorgang zu starten, bei dem eine Verbindung mit einem Remoteziel hergestellt und sofort mit der Aushandlung von SSL/TLS begonnen wird.</span><span class="sxs-lookup"><span data-stu-id="a3437-197">Call one of the above [**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504) methods to start an operation to connect to a remote destination and immediately negotiate the use of SSL/TLS.</span></span>
-   <span data-ttu-id="a3437-198">Die tatsächlich mithilfe von [**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504) ausgehandelte SSL-Schlüsselstärke kann durch Abruf der [**StreamSocketinformation.ProtectionLevel**](https://msdn.microsoft.com/library/windows/apps/hh967868)-Eigenschaft bestimmt werden, nachdem der asynchrone Vorgang erfolgreich abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="a3437-198">The SSL strength actually negotiated using [**ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/hh701504) can be determined by getting the [**StreamSocketinformation.ProtectionLevel**](https://msdn.microsoft.com/library/windows/apps/hh967868) property after the async operation has completed successfully.</span></span>

<span data-ttu-id="a3437-199">Das folgende Beispiel erstellt ein [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Objekt und versucht, eine Verbindung mit dem Netzwerkdienst herzustellen und sofort die Verwendung von SSL/TLS auszuhandeln.</span><span class="sxs-lookup"><span data-stu-id="a3437-199">The following example creates a [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) and tries to establish a connection to the network service and negotiate immediately to use SSL/TLS.</span></span> <span data-ttu-id="a3437-200">Bei einer erfolgreichen Aushandlung wird jede Netzwerkkommunikation zwischen dem Client und dem Netzwerkserver verschlüsselt, bei der das **StreamSocket**-Objekt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a3437-200">If the negotiation is successful, all network communication using the **StreamSocket** between the client the network server will be encrypted.</span></span>

```csharp
using Windows.Networking;
using Windows.Networking.Sockets;

    // Define some variables and set values
    StreamSocket clientSocket = new StreamSocket();
     
    HostName serverHost = new HostName("www.contoso.com");
    string serverServiceName = "https";
    
    // For simplicity, the sample omits implementation of the
    // NotifyUser method used to display status and error messages 
    
    // Try to connect to contoso using HTTPS (port 443)
    try {

        // Call ConnectAsync method with SSL
        await clientSocket.ConnectAsync(serverHost, serverServiceName, SocketProtectionLevel.Ssl);

        NotifyUser("Connected");
    }
    catch (Exception exception) {
        // If this is an unknown status it means that the error is fatal and retry will likely fail.
        if (SocketError.GetStatus(exception.HResult) == SocketErrorStatus.Unknown) {
            throw;
        }
        
        NotifyUser("Connect failed with error: " + exception.Message);
        // Could retry the connection, but for this simple example
        // just close the socket.
        
        clientSocket.Dispose();
        clientSocket = null; 
    }
           
    // Add code to send and receive data using the clientSocket
    // and then close the clientSocket
```

```cppwinrt
#include <winrt/Windows.Networking.Sockets.h>

using namespace winrt;
...
    // Define some variables, and set values.
    Windows::Networking::Sockets::StreamSocket clientSocket;

    Windows::Networking::HostName serverHost{ L"www.contoso.com" };
    winrt::hstring serverServiceName{ L"https" };

    // For simplicity, the sample omits implementation of the
    // NotifyUser method used to display status and error messages.

    // Try to connect to the server using HTTPS and SSL (port 443).
    try
    {
        co_await clientSocket.ConnectAsync(serverHost, serverServiceName, Windows::Networking::Sockets::SocketProtectionLevel::Tls12);
        NotifyUser(L"Connected");
    }
    catch (winrt::hresult_error const& exception)
    {
        NotifyUser(L"Connect failed with error: " + exception.message());
        clientSocket = nullptr;
    }
    // Add code to send and receive data using the clientSocket,
    // then set the clientSocket to nullptr when done to close it.
```

```cpp
using Windows::Networking;
using Windows::Networking::Sockets;

    // Define some variables and set values
    StreamSocket^ clientSocket = new ref StreamSocket();
 
    HostName^ serverHost = new ref HostName("www.contoso.com");
    String serverServiceName = "https";

    // For simplicity, the sample omits implementation of the
    // NotifyUser method used to display status and error messages 

    // Try to connect to the server using HTTPS and SSL (port 443)
    task<void>(clientSocket->ConnectAsync(serverHost, serverServiceName, SocketProtectionLevel::SSL)).then([this] (task<void> previousTask) {
        try
        {
            // Try getting all exceptions from the continuation chain above this point.
            previousTask.Get();
            NotifyUser("Connected");
        }
        catch (Exception^ exception)
        {
            NotifyUser("Connect failed with error: " + exception->Message);
            
            clientSocket.Close();
            clientSocket = null;
        }
    });
    // Add code to send and receive data using the clientSocket
    // Then close the clientSocket when done
```

### <a name="use-upgradetosslasync"></a><span data-ttu-id="a3437-201">Verwenden von UpgradeToSslAsync</span><span class="sxs-lookup"><span data-stu-id="a3437-201">Use UpgradeToSslAsync</span></span>
<span data-ttu-id="a3437-202">Wenn der Code [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922) verwendet, stellt er zuerst eine Verbindung mit einem Netzwerkdienst ohne Verschlüsselung her.</span><span class="sxs-lookup"><span data-stu-id="a3437-202">When your code uses [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922), it first establishes a connection to a network service without encryption.</span></span> <span data-ttu-id="a3437-203">Die App kann ein gewisse Datenmenge senden oder empfangen, bevor sie die Verbindung für jegliche weitere Kommunikation auf die Verwendung von SSL/TLS heraufgestuft.</span><span class="sxs-lookup"><span data-stu-id="a3437-203">The app may send or receive some data, then upgrade the connection to use SSL/TLS for all further communications.</span></span>

<span data-ttu-id="a3437-204">Die [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922)-Methode besitzt zwei Parameter.</span><span class="sxs-lookup"><span data-stu-id="a3437-204">The [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922) method takes two parameters.</span></span> <span data-ttu-id="a3437-205">Der *protectionLevel*-Parameter gibt den gewünschten Schutzgrad an.</span><span class="sxs-lookup"><span data-stu-id="a3437-205">The *protectionLevel* parameter indicates the protection level desired.</span></span> <span data-ttu-id="a3437-206">Der *validationHostName*-Parameter ist der Hostname des Remotenetzwerkziels, der bei der Höherstufung auf SSL für die Validierung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a3437-206">The *validationHostName* parameter is the hostname of the remote network destination that is used for validation when upgrading to SSL.</span></span> <span data-ttu-id="a3437-207">In der Regel entspricht *validationHostName* dem Hostnamen, mit dem die App die erste Verbindung hergestellt hat.</span><span class="sxs-lookup"><span data-stu-id="a3437-207">Normally the *validationHostName* would be the same hostname that the app used to initially establish the connection.</span></span> <span data-ttu-id="a3437-208">Wenn der *protectionLevel*-Parameter beim Aufrufen von **UpgradeToSslAsync** auf **Windows.System.Socket.SocketProtectionLevel.Ssl** festgelegt ist, muss [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) für die weitere Kommunikation über den Socket die SSL/TLS-Verschlüsselung verwenden.</span><span class="sxs-lookup"><span data-stu-id="a3437-208">If the *protectionLevel* parameter is set to **Windows.System.Socket.SocketProtectionLevel.Ssl** when calling **UpgradeToSslAsync**, the [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) must use the SSL/TLS for encryption on further communications over the socket.</span></span> <span data-ttu-id="a3437-209">Dieser Wert erfordert eine Verschlüsselung, wobei keine NULL-Verschlüsselung zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="a3437-209">This value requires encryption and never allows a NULL cipher to be used.</span></span>

<span data-ttu-id="a3437-210">Der übliche Ablauf bei dieser [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922)-Methode lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="a3437-210">The normal sequence to use with the [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922) method is as follows:</span></span>

-   <span data-ttu-id="a3437-211">Erstellen Sie ein [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="a3437-211">Create a [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882).</span></span>
-   <span data-ttu-id="a3437-212">Wenn eine erweiterte Option für den Socket erforderlich ist, rufen Sie mit der [**StreamSocket.Control**](https://msdn.microsoft.com/library/windows/apps/br226917)-Eigenschaft die [**StreamSocketControl**](https://msdn.microsoft.com/library/windows/apps/br226893)-Instanz ab, die einem [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Objekt zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="a3437-212">If an advanced option on the socket is needed, use the [**StreamSocket.Control**](https://msdn.microsoft.com/library/windows/apps/br226917) property to get the [**StreamSocketControl**](https://msdn.microsoft.com/library/windows/apps/br226893) instance associated with a [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) object.</span></span> <span data-ttu-id="a3437-213">Legen Sie eine Eigenschaft für **StreamSocketControl** fest.</span><span class="sxs-lookup"><span data-stu-id="a3437-213">Set a property on the **StreamSocketControl**.</span></span>
-   <span data-ttu-id="a3437-214">Senden Sie jetzt alle Daten, die gegebenenfalls unverschlüsselt gesendet oder empfangen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="a3437-214">If any data needs to be sent and received unencrypted, send it now.</span></span>
-   <span data-ttu-id="a3437-215">Rufen Sie die [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922)-Methode auf, um einen Vorgang zum Höherstufen der Verbindung auf SSL/TLS zu starten.</span><span class="sxs-lookup"><span data-stu-id="a3437-215">Call the [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922) method to start an operation to upgrade the connection to use SSL/TLS.</span></span>
-   <span data-ttu-id="a3437-216">Die tatsächlich mithilfe von [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922) ausgehandelte SSL-Schlüsselstärke kann durch Abruf der [**StreamSocketinformation.ProtectionLevel**](https://msdn.microsoft.com/library/windows/apps/hh967868)-Eigenschaft bestimmt werden, nachdem der asynchrone Vorgang erfolgreich abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="a3437-216">The SSL strength actually negotiated using [**UpgradeToSslAsync**](https://msdn.microsoft.com/library/windows/apps/br226922) can be determined by getting the [**StreamSocketinformation.ProtectionLevel**](https://msdn.microsoft.com/library/windows/apps/hh967868) property after the async operation completes successfully.</span></span>

<span data-ttu-id="a3437-217">Das folgende Beispiel erstellt ein [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Objekt, versucht, eine Verbindung mit dem Netzwerkdienst herzustellen, sendet einige erste Daten und handelt dann die Verwendung von SSL/TLS aus.</span><span class="sxs-lookup"><span data-stu-id="a3437-217">The following example creates a [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882), tries to establish a connection to the network service, sends some initial data, and then negotiates to use SSL/TLS.</span></span> <span data-ttu-id="a3437-218">Bei einer erfolgreichen Aushandlung wird jede Netzwerkkommunikation zwischen dem Client und dem Netzwerkserver verschlüsselt, bei der **StreamSocket** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a3437-218">If the negotiation is successful, all network communication using the **StreamSocket** between the client and the network server will be encrypted.</span></span>

```csharp
using Windows.Networking;
using Windows.Networking.Sockets;
using Windows.Storage.Streams;

    // Define some variables and set values
    StreamSocket clientSocket = new StreamSocket();
 
    HostName serverHost = new HostName("www.contoso.com");
    string serverServiceName = "http";

    // For simplicity, the sample omits implementation of the
    // NotifyUser method used to display status and error messages 

    // Try to connect to contoso using HTTP (port 80)
    try {
        // Call ConnectAsync method with a plain socket
        await clientSocket.ConnectAsync(serverHost, serverServiceName, SocketProtectionLevel.PlainSocket);

        NotifyUser("Connected");

    }
    catch (Exception exception) {
        // If this is an unknown status it means that the error is fatal and retry will likely fail.
        if (SocketError.GetStatus(exception.HResult) == SocketErrorStatus.Unknown) {
            throw;
        }

        NotifyUser("Connect failed with error: " + exception.Message, NotifyType.ErrorMessage);
        // Could retry the connection, but for this simple example
        // just close the socket.

        clientSocket.Dispose();
        clientSocket = null; 
        return;
    }

    // Now try to send some data
    DataWriter writer = new DataWriter(clientSocket.OutputStream);
    string hello = "Hello, World! ☺ ";
    Int32 len = (int) writer.MeasureString(hello); // Gets the UTF-8 string length.
    writer.WriteInt32(len);
    writer.WriteString(hello);
    NotifyUser("Client: sending hello");

    try {
        // Call StoreAsync method to store the hello message
        await writer.StoreAsync();

        NotifyUser("Client: sent data");

        writer.DetachStream(); // Detach stream, if not, DataWriter destructor will close it.
    }
    catch (Exception exception) {
        NotifyUser("Store failed with error: " + exception.Message);
        // Could retry the store, but for this simple example
            // just close the socket.

            clientSocket.Dispose();
            clientSocket = null; 
            return;
    }

    // Now upgrade the client to use SSL
    try {
        // Try to upgrade to SSL
        await clientSocket.UpgradeToSslAsync(SocketProtectionLevel.Ssl, serverHost);

        NotifyUser("Client: upgrade to SSL completed");
           
        // Add code to send and receive data 
        // The close clientSocket when done
    }
    catch (Exception exception) {
        // If this is an unknown status it means that the error is fatal and retry will likely fail.
        if (SocketError.GetStatus(exception.HResult) == SocketErrorStatus.Unknown) {
            throw;
        }

        NotifyUser("Upgrade to SSL failed with error: " + exception.Message);

        clientSocket.Dispose();
        clientSocket = null; 
        return;
    }
```

```cppwinrt
#include <winrt/Windows.Networking.Sockets.h>
#include <winrt/Windows.Storage.Streams.h>

using namespace winrt;
using namespace Windows::Storage::Streams;
...
    // Define some variables, and set values.
    Windows::Networking::Sockets::StreamSocket clientSocket;

    Windows::Networking::HostName serverHost{ L"www.contoso.com" };
    winrt::hstring serverServiceName{ L"https" };

    // For simplicity, the sample omits implementation of the
    // NotifyUser method used to display status and error messages. 

    // Try to connect to the server using HTTP (port 80).
    try
    {
        co_await clientSocket.ConnectAsync(serverHost, serverServiceName, Windows::Networking::Sockets::SocketProtectionLevel::PlainSocket);
        NotifyUser(L"Connected");
    }
    catch (winrt::hresult_error const& exception)
    {
        NotifyUser(L"Connect failed with error: " + exception.message());
        clientSocket = nullptr;
    }

    // Now, try to send some data.
    DataWriter writer{ clientSocket.OutputStream() };
    winrt::hstring hello{ L"Hello, World! ☺ " };
    uint32_t len{ writer.MeasureString(hello) }; // Gets the size of the string, in bytes.
    writer.WriteInt32(len);
    writer.WriteString(hello);
    NotifyUser(L"Client: sending hello");

    try
    {
        co_await writer.StoreAsync();
        NotifyUser(L"Client: sent hello");

        writer.DetachStream(); // Detach the stream when you want to continue using it; otherwise, the DataWriter destructor closes it.
    }
    catch (winrt::hresult_error const& exception)
    {
        NotifyUser(L"Store failed with error: " + exception.message());
        // We could retry the store operation. But, for this simple example, just close the socket by setting it to nullptr.
        clientSocket = nullptr;
        co_return;
    }

    // Now, upgrade the client to use SSL.
    try
    {
        co_await clientSocket.UpgradeToSslAsync(Windows::Networking::Sockets::SocketProtectionLevel::Tls12, serverHost);
        NotifyUser(L"Client: upgrade to SSL completed");

        // Add code to send and receive data using the clientSocket,
        // then set the clientSocket to nullptr when done to close it.
    }
    catch (winrt::hresult_error const& exception)
    {
        // If this is an unknown status, then the error is fatal and retry will likely fail.
        Windows::Networking::Sockets::SocketErrorStatus socketErrorStatus{ Windows::Networking::Sockets::SocketError::GetStatus(exception.to_abi()) };
        if (socketErrorStatus == Windows::Networking::Sockets::SocketErrorStatus::Unknown)
        {
            throw;
        }

        NotifyUser(L"Upgrade to SSL failed with error: " + exception.message());
        // We could retry the store operation. But for this simple example, just close the socket by setting it to nullptr.
        clientSocket = nullptr;
        co_return;
    }
```

```cpp
using Windows::Networking;
using Windows::Networking::Sockets;
using Windows::Storage::Streams;

    // Define some variables and set values
    StreamSocket^ clientSocket = new ref StreamSocket();
 
    Hostname^ serverHost = new ref HostName("www.contoso.com");
    String serverServiceName = "http";

    // For simplicity, the sample omits implementation of the
    // NotifyUser method used to display status and error messages 

    // Try to connect to contoso using HTTP (port 80)
    task<void>(clientSocket->ConnectAsync(serverHost, serverServiceName, SocketProtectionLevel::PlainSocket)).then([this] (task<void> previousTask) {
        try
        {
            // Try getting all exceptions from the continuation chain above this point.
            previousTask.Get();
            NotifyUser("Connected");
        }
        catch (Exception^ exception)
        {
            NotifyUser("Connect failed with error: " + exception->Message);
 
            clientSocket->Close();
            clientSocket = null;
        }
    });
       
    // Now try to send some data
    DataWriter^ writer = new ref DataWriter(clientSocket.OutputStream);
    String hello = "Hello, World! ☺ ";
    Int32 len = (int) writer->MeasureString(hello); // Gets the UTF-8 string length.
    writer->writeInt32(len);
    writer->writeString(hello);
    NotifyUser("Client: sending hello");

    task<void>(writer->StoreAsync()).then([this] (task<void> previousTask) {
        try {
            // Try getting all exceptions from the continuation chain above this point.
            previousTask.Get();

            NotifyUser("Client: sent hello");

            writer->DetachStream(); // Detach stream, if not, DataWriter destructor will close it.
       }
       catch (Exception^ exception) {
               NotifyUser("Store failed with error: " + exception->Message);
               // Could retry the store, but for this simple example
               // just close the socket.
 
               clientSocket->Close();
               clientSocket = null;
               return
       }
    });

    // Now upgrade the client to use SSL
    task<void>(clientSocket->UpgradeToSslAsync(clientSocket.SocketProtectionLevel.Ssl, serverHost)).then([this] (task<void> previousTask) {
        try {
            // Try getting all exceptions from the continuation chain above this point.
            previousTask.Get();

           NotifyUser("Client: upgrade to SSL completed");
           
           // Add code to send and receive data 
           // Then close clientSocket when done
        }
        catch (Exception^ exception) {
            // If this is an unknown status it means that the error is fatal and retry will likely fail.
            if (SocketError.GetStatus(exception.HResult) == SocketErrorStatus.Unknown) {
                throw;
            }

            NotifyUser("Upgrade to SSL failed with error: " + exception.Message);

            clientSocket->Close();
            clientSocket = null; 
            return;
        }
    });
```

### <a name="creating-secure-websocket-connections"></a><span data-ttu-id="a3437-219">Erstellen von sicheren WebSocket-Verbindungen</span><span class="sxs-lookup"><span data-stu-id="a3437-219">Creating secure WebSocket connections</span></span>
<span data-ttu-id="a3437-220">WebSocket-Verbindungen können wie herkömmliche Socketverbindungen mit TLS (Transport Layer Security)/SSL (Secure Sockets Layer) verschlüsselt werden, wenn Sie die Features [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) und [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) für eine UWP-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="a3437-220">Like traditional socket connections, WebSocket connections can also be encrypted with Transport Layer Security (TLS)/Secure Sockets Layer (SSL) when using the [**StreamWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226923) and [**MessageWebSocket**](https://msdn.microsoft.com/library/windows/apps/br226842) features for a UWP app.</span></span> <span data-ttu-id="a3437-221">In den meisten Fällen empfiehlt sich die Verwendung einer sicheren WebSocket-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="a3437-221">In most cases you'll want to use a secure WebSocket connection.</span></span> <span data-ttu-id="a3437-222">Dadurch ist es wahrscheinlicher, dass die Verbindung funktioniert, da andernfalls viele Proxys unverschlüsselte WebSocket-Verbindungen ablehnen.</span><span class="sxs-lookup"><span data-stu-id="a3437-222">This will increase the chances that your connection will succeed, as many proxies will reject unencrypted WebSocket connections.</span></span>

<span data-ttu-id="a3437-223">Beispiele für das Erstellen einer sicheren WebSocket-Verbindung mit einem Netzwerkdienst bzw. für das Schützen einer WebSocket-Verbindung mit einem Netzwerkdienst finden Sie unter [So wird’s gemacht: Schützen von WebSocket-Verbindungen mit TLS/SSL](https://msdn.microsoft.com/library/windows/apps/xaml/hh994399).</span><span class="sxs-lookup"><span data-stu-id="a3437-223">For examples of how to create, or upgrade to, a secure socket connection to a network service, see [How to secure WebSocket connections with TLS/SSL](https://msdn.microsoft.com/library/windows/apps/xaml/hh994399).</span></span>

<span data-ttu-id="a3437-224">Ein Server benötigt möglicherweise zusätzlich zur TLS/SSL-Verschlüsselung einen **Sec-WebSocket-Protocol**-Headerwert, um den ersten Handshake auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a3437-224">In addition to TLS/SSL encryption, a server may require a **Sec-WebSocket-Protocol** header value to complete the initial handshake.</span></span> <span data-ttu-id="a3437-225">Dieser Wert, der von der [**StreamWebSocketInformation.Protocol**](https://msdn.microsoft.com/library/windows/apps/hh701514)-Eigenschaft und der [**MessageWebSocketInformation.Protocol**](https://msdn.microsoft.com/library/windows/apps/hh701358)-Eigenschaft dargestellt wird, gibt die Protokollversion der Verbindung an und ermöglicht es dem Server, den Handshake zum Öffnen der Verbindung und die anschließend ausgetauschten Daten korrekt zu interpretieren.</span><span class="sxs-lookup"><span data-stu-id="a3437-225">This value, represented by the [**StreamWebSocketInformation.Protocol**](https://msdn.microsoft.com/library/windows/apps/hh701514) and [**MessageWebSocketInformation.Protocol**](https://msdn.microsoft.com/library/windows/apps/hh701358) properties, indicate the protocol version of the connection and enables the server to correctly interpret the opening handshake and the data being exchanged afterwards.</span></span> <span data-ttu-id="a3437-226">Anhand dieser Protokollinformationen kann die Verbindung jederzeit geschlossen werden, wenn der Server die eingehenden Daten nicht auf sichere Weise interpretieren kann.</span><span class="sxs-lookup"><span data-stu-id="a3437-226">Using this protocol information, if at any point if the server cannot interpret the incoming data in a safe manner the connection can be closed.</span></span>

<span data-ttu-id="a3437-227">Wenn die erste Anforderung vom Client nicht diesen Wert enthält oder einen Wert bereitstellt, der vom Server nicht erwartet wird, tritt ein WebSocket-Handshakefehler auf, und der Server sendet den erwarteten Wert an den Client.</span><span class="sxs-lookup"><span data-stu-id="a3437-227">If the initial request from the client either does not contain this value, or provides a value that doesn't match what the server expects, the expected value is sent from the server to the client on WebSocket handshake error.</span></span>

## <a name="authentication"></a><span data-ttu-id="a3437-228">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="a3437-228">Authentication</span></span>
<span data-ttu-id="a3437-229">So werden beim Herstellen einer Verbindung über das Netzwerk die Authentifizierungsanmeldeinformationen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="a3437-229">How to provide authentication credentials when connecting over the network.</span></span>

### <a name="providing-a-client-certificate-with-the-streamsocket-class"></a><span data-ttu-id="a3437-230">Bereitstellen eines Clientzertifikats mit der StreamSocket-Klasse</span><span class="sxs-lookup"><span data-stu-id="a3437-230">Providing a client certificate with the StreamSocket class</span></span>
<span data-ttu-id="a3437-231">Die [**Windows.Networking.StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Klasse unterstützt die Verwendung von SSL/TLS zum Authentifizieren des Servers, mit dem die App kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="a3437-231">The [**Windows.Networking.StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) class supports using SSL/TLS to authenticate the server the app is talking to.</span></span> <span data-ttu-id="a3437-232">In bestimmten Fällen muss auch die App selbst mit einem TLS-Clientzertifikat am Server authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="a3437-232">In certain cases, the app also needs to authenticate itself to the server using a TLS client certificate.</span></span> <span data-ttu-id="a3437-233">In Windows 10 können Sie ein Clientzertifikat für das Objekt [**StreamSocket.Control**](https://msdn.microsoft.com/library/windows/apps/br226893) bereitstellen (Dies muss festgelegt werden, bevor der TLS-Handshake gestartet wird).</span><span class="sxs-lookup"><span data-stu-id="a3437-233">In Windows10, you can provide a client certificate on the [**StreamSocket.Control**](https://msdn.microsoft.com/library/windows/apps/br226893) object (this must be set before the TLS handshake is started).</span></span> <span data-ttu-id="a3437-234">Wenn der Server das Clientzertifikat anfordert, reagiert Windows mit dem bereitgestellten Zertifikat.</span><span class="sxs-lookup"><span data-stu-id="a3437-234">If the server requests the client certificate, Windows will respond with the certificate provided.</span></span>

<span data-ttu-id="a3437-235">Hier ist ein Codeausschnitt, in dem die Implementierung dazu dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="a3437-235">Here is a code snippet showing how to implement this:</span></span>

```csharp
var socket = new StreamSocket();
Windows.Security.Cryptography.Certificates.Certificate certificate = await GetClientCert();
socket.Control.ClientCertificate = certificate;
await socket.ConnectAsync(destination, SocketProtectionLevel.Tls12);
```

### <a name="providing-authentication-credentials-to-a-web-service"></a><span data-ttu-id="a3437-236">Bereitstellen von Anmeldeinformationen zum Authentifizieren für einen Webdienst</span><span class="sxs-lookup"><span data-stu-id="a3437-236">Providing authentication credentials to a web service</span></span>
<span data-ttu-id="a3437-237">Die Netzwerk-APIs, die Apps die Interaktion mit sicheren Webdiensten ermöglichen, stellen jeweils eigene Methoden zum Initialisieren eines Clients oder Festlegen eines Anforderungsheaders mit Anmeldeinformationen für die Server- und Proxyauthentifizierung bereit.</span><span class="sxs-lookup"><span data-stu-id="a3437-237">The networking APIs that enable apps to interact with secure web services each provide their own methods to either initialize a client or set a request header with server and proxy authentication credentials.</span></span> <span data-ttu-id="a3437-238">Jede Methode wird mit einem [**PasswordCredential**](https://msdn.microsoft.com/library/windows/apps/br227061)-Objekt festgelegt, das einen Benutzernamen, ein Kennwort und die Ressource angibt, für die die Anmeldeinformationen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a3437-238">Each method is set with a [**PasswordCredential**](https://msdn.microsoft.com/library/windows/apps/br227061) object that indicates a user name, password, and the resource for which these credentials are used.</span></span> <span data-ttu-id="a3437-239">In der folgenden Tabelle werden diese APIs zugeordnet:</span><span class="sxs-lookup"><span data-stu-id="a3437-239">The following table provides a mapping of these APIs:</span></span>

| **<span data-ttu-id="a3437-240">WebSockets</span><span class="sxs-lookup"><span data-stu-id="a3437-240">WebSockets</span></span>** | [**<span data-ttu-id="a3437-241">MessageWebSocketControl.ServerCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-241">MessageWebSocketControl.ServerCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/br226848) |
|-------------------------|----------------------------------------------------------------------------------------------------------|
|  | [**<span data-ttu-id="a3437-242">MessageWebSocketControl.ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-242">MessageWebSocketControl.ProxyCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/br226847) |
|  | [**<span data-ttu-id="a3437-243">StreamWebSocketControl.ServerCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-243">StreamWebSocketControl.ServerCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/br226928) |
|  | [**<span data-ttu-id="a3437-244">StreamWebSocketControl.ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-244">StreamWebSocketControl.ProxyCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/br226927) |
| **<span data-ttu-id="a3437-245">Hintergrundübertragung</span><span class="sxs-lookup"><span data-stu-id="a3437-245">Background Transfer</span></span>** | [**<span data-ttu-id="a3437-246">BackgroundDownloader.ServerCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-246">BackgroundDownloader.ServerCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701076) |
|  | [**<span data-ttu-id="a3437-247">BackgroundDownloader.ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-247">BackgroundDownloader.ProxyCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701068) |
|  | [**<span data-ttu-id="a3437-248">BackgroundUploader.ServerCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-248">BackgroundUploader.ServerCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701184) |
|  | [**<span data-ttu-id="a3437-249">BackgroundUploader.ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-249">BackgroundUploader.ProxyCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701178) |
| **<span data-ttu-id="a3437-250">Veröffentlichung</span><span class="sxs-lookup"><span data-stu-id="a3437-250">Syndication</span></span>** | [**<span data-ttu-id="a3437-251">SyndicationClient(PasswordCredential)</span><span class="sxs-lookup"><span data-stu-id="a3437-251">SyndicationClient(PasswordCredential)</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh702355) |
|  | [**<span data-ttu-id="a3437-252">SyndicationClient.ServerCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-252">SyndicationClient.ServerCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243461) |
|  | [**<span data-ttu-id="a3437-253">SyndicationClient.ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-253">SyndicationClient.ProxyCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243459) |
| **<span data-ttu-id="a3437-254">AtomPub</span><span class="sxs-lookup"><span data-stu-id="a3437-254">AtomPub</span></span>** | [**<span data-ttu-id="a3437-255">AtomPubClient(PasswordCredential)</span><span class="sxs-lookup"><span data-stu-id="a3437-255">AtomPubClient(PasswordCredential)</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh702262) |
|  | [**<span data-ttu-id="a3437-256">AtomPubClient.ServerCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-256">AtomPubClient.ServerCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243428) |
|  | [**<span data-ttu-id="a3437-257">AtomPubClient.ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a3437-257">AtomPubClient.ProxyCredential</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243423) |

## <a name="handling-network-exceptions"></a><span data-ttu-id="a3437-258">Behandeln von Netzwerkausnahmen</span><span class="sxs-lookup"><span data-stu-id="a3437-258">Handling network exceptions</span></span>
<span data-ttu-id="a3437-259">In den meisten Bereichen der Programmierung ist eine Ausnahme auf ein erhebliches Problem oder einen Fehler zurückzuführen, dass durch einige Fehler im Programm verursacht wurde.</span><span class="sxs-lookup"><span data-stu-id="a3437-259">In most areas of programming, an exception indicates a significant problem or failure, caused by some flaw in the program.</span></span> <span data-ttu-id="a3437-260">In der Netzwerkprogrammierung gibt es eine zusätzliche Quelle für Ausnahmen: das Netzwerk selbst und der Art der Netzwerkkommunikation.</span><span class="sxs-lookup"><span data-stu-id="a3437-260">In network programming, there is an additional source for exceptions: the network itself, and the nature of network communications.</span></span> <span data-ttu-id="a3437-261">Die Netzwerkkommunikation sind grundsätzlich nicht zuverlässig und anfällig für unerwartete Fehler.</span><span class="sxs-lookup"><span data-stu-id="a3437-261">Network communications are inherently unreliable and prone to unexpected failure.</span></span> <span data-ttu-id="a3437-262">Für jede der Möglichkeiten, mit der Ihre App das Netzwerke verwendet, müssen Sie einige Statusinformationen verwalten; und der App-Code muss Netzwerkausnahmen behandeln, indem er diese Statusinformationen aktualisiert und die entsprechende Logik für Ihre App erneut initialisiert, um Kommunikationsfehler wiederherzustellen oder zu wiederholen.</span><span class="sxs-lookup"><span data-stu-id="a3437-262">For each of the ways your app uses networking, you must maintain some state information; and your app code must handle network exceptions by updating that state information and initiating appropriate logic for your app to re-establish or retry communication failures.</span></span>

<span data-ttu-id="a3437-263">Wenn Universelle Windows-Apps eine Ausnahme auslösen, kann Ihr Ausnahmehandler detailliertere Informationen zur Ursache der Ausnahme abrufen, um die Ausnahme besser verstehen und entsprechende Entscheidungen treffen zu können.</span><span class="sxs-lookup"><span data-stu-id="a3437-263">When Universal Windows apps throw an exception, your exception handler can retrieve more detailed information on the cause of the exception to better understand the failure and make appropriate decisions.</span></span>

<span data-ttu-id="a3437-264">Jede Programmiersprache unterstützt eine Methode, mit der auf diese detaillierteren Informationen zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="a3437-264">Each language projection supports a method to access this more detailed information.</span></span> <span data-ttu-id="a3437-265">Eine Ausnahme wird als **HRESULT**-Wert in Universellen Windows-Apps projiziert.</span><span class="sxs-lookup"><span data-stu-id="a3437-265">An exception projects as an **HRESULT** value in Universal Windows apps.</span></span> <span data-ttu-id="a3437-266">Die *Winerror.h*-Includedatei enthält eine sehr umfangreiche Liste möglicher **HRESULT**-Werte, die Netzwerkfehler beinhaltet.</span><span class="sxs-lookup"><span data-stu-id="a3437-266">The *Winerror.h* include file contains a very large list of possible **HRESULT** values that includes network errors.</span></span>

<span data-ttu-id="a3437-267">Die Netzwerk-APIs unterstützen verschiedene Methoden zum Abrufen der detaillierten Informationen zur Ursache der Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="a3437-267">The networking APIs support different methods for retrieving this detailed information on the cause of an exception.</span></span>

-   <span data-ttu-id="a3437-268">Einige APIs bieten eine Hilfsmethode, die den **HRESULT**-Wert der Ausnahme in einen Enumerationswert konvertiert.</span><span class="sxs-lookup"><span data-stu-id="a3437-268">Some APIs provide a helper method that converts the **HRESULT** value from the exception to an enumeration value.</span></span>
-   <span data-ttu-id="a3437-269">Andere APIs bieten eine Methode zum Abrufen des tatsächlichen **HRESULT**-Werts.</span><span class="sxs-lookup"><span data-stu-id="a3437-269">Other APIs provide a method to retrieve the actual **HRESULT** value.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a3437-270">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a3437-270">Related topics</span></span>
* [<span data-ttu-id="a3437-271">Verbesserungen bei der Netzwerk-API unter Windows 10</span><span class="sxs-lookup"><span data-stu-id="a3437-271">Networking API Improvements in Windows 10</span></span>](http://blogs.windows.com/buildingapps/2015/07/02/networking-api-improvements-in-windows-10/)
