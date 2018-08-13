---
author: mtoepke
title: Netzwerkfunktionen für Spiele
description: Erfahren Sie, wie Sie Netzwerkfeatures entwickeln und in ein DirectX-Spiel integrieren.
ms.assetid: 212eee15-045c-8ba1-e274-4532b2120c55
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Netzwerke, directx
ms.openlocfilehash: ce94dda0eaf156f1e09fefbd76f50bc764050970
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "235388"
---
# <a name="networking-for-games"></a><span data-ttu-id="42d7a-104">Netzwerk für Spiele</span><span class="sxs-lookup"><span data-stu-id="42d7a-104">Networking for games</span></span>


<span data-ttu-id="42d7a-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="42d7a-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="42d7a-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="42d7a-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="42d7a-107">Hier erfahren Sie, wie Sie Netzwerkfeatures entwickeln und in ein DirectX-Spiel integrieren.</span><span class="sxs-lookup"><span data-stu-id="42d7a-107">Learn how to develop and incorporate networking features into your DirectX game.</span></span>

## <a name="concepts-at-a-glance"></a><span data-ttu-id="42d7a-108">Konzepte auf einen Blick</span><span class="sxs-lookup"><span data-stu-id="42d7a-108">Concepts at a glance</span></span>


<span data-ttu-id="42d7a-109">Unabhängig davon, ob es sich um ein einfaches eigenständiges Spiel oder ein umfangreiches Multiplayer-Spiel handelt, können für DirectX-Spiele verschiedene Netzwerkfeatures verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="42d7a-109">A variety of networking features can be used in your DirectX game, whether it is a simple standalone game to massively multi-player games.</span></span> <span data-ttu-id="42d7a-110">Das einfachste Netzwerkfeature dient zum Speichern von Benutzernamen und Spielständen auf einem zentralen Netzwerkserver.</span><span class="sxs-lookup"><span data-stu-id="42d7a-110">The simplest use of networking would be to store user names and game scores on a central network server.</span></span>

<span data-ttu-id="42d7a-111">Netzwerk-APIs werden für Multiplayer-Spiele mit Infrastrukturmodell (Client-Server oder Peer-zu-Peer über das Internet) sowie für Ad-hoc-Spiele (lokales Peer-zu-Peer) benötigt.</span><span class="sxs-lookup"><span data-stu-id="42d7a-111">Networking APIs are needed in multi-player games that use the infrastructure (client-server or internet peer-to-peer) model and also by ad hoc (local peer-to-peer) games.</span></span> <span data-ttu-id="42d7a-112">Bei serverbasierten Multiplayer-Spielen erfolgen die meisten Spielvorgänge in der Regel auf einem zentralen Spielserver, und die Client-Spiel-App wird für Eingaben, die Grafikanzeige, die Audiowiedergabe und weitere Features verwendet.</span><span class="sxs-lookup"><span data-stu-id="42d7a-112">For server-based multi-player games, a central game server usually handles most of the game operations and the client game app is used for input, displaying graphics, playing audio, and other features.</span></span> <span data-ttu-id="42d7a-113">Die Geschwindigkeit und Latenz von Netzwerkübertragungen sind entscheidend für ein ansprechendes Spielerlebnis.</span><span class="sxs-lookup"><span data-stu-id="42d7a-113">The speed and latency of network transfers is a concern for a satisfactory game experience.</span></span>

<span data-ttu-id="42d7a-114">Bei Peer-zu-Peer-Spielen werden die Eingaben und Grafiken in der App jedes Spielers verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="42d7a-114">For peer-to-peer games, each player's app handles the input and graphics.</span></span> <span data-ttu-id="42d7a-115">In den meisten Fällen sind die Spieler nicht weit voneinander entfernt, sodass die Netzwerklatenz zwar niedriger ist, aber dennoch eine Rolle spielt.</span><span class="sxs-lookup"><span data-stu-id="42d7a-115">In most cases, the game players are located in close proximity so that network latency should be lower but is still a concern.</span></span> <span data-ttu-id="42d7a-116">In diesem Fall ist es wichtig, wie Mitspieler gefunden werden und eine Verbindung mit ihnen hergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="42d7a-116">How to discovery peers and establish a connection becomes a concern.</span></span>

<span data-ttu-id="42d7a-117">Bei Spielen mit einem Spieler wird oft ein zentraler Webserver oder -service zum Speichern von Benutzernamen, Spielständen und weiteren Informationen verwendet.</span><span class="sxs-lookup"><span data-stu-id="42d7a-117">For single-player games, a central Web server or service is often used to store user names, game scores, and other miscellaneous information.</span></span> <span data-ttu-id="42d7a-118">Bei diesen Spielen stellt die Geschwindigkeit und Latenz von Netzwerkübertragungen in der Regel kein Problem dar, da die Spielvorgänge nicht unmittelbar damit zusammenhängen.</span><span class="sxs-lookup"><span data-stu-id="42d7a-118">In these games, the speed and latency of networking transfers is less of a concern since it doesn't directly affect game operation.</span></span>

<span data-ttu-id="42d7a-119">Netzwerkbedingungen können sich jederzeit ändern, sodass jedes Spiel, für das Netzwerk-APIs verwendet werden, eventuell auftretende Netzwerkausnahmen behandeln muss.</span><span class="sxs-lookup"><span data-stu-id="42d7a-119">Network conditions can change at any time, so any game that uses networking APIs needs to handle network exceptions that may occur.</span></span> <span data-ttu-id="42d7a-120">Weitere Informationen zum Behandeln von Netzwerkausnahmen finden Sie unter [Grundlagen zum Netzwerk](https://msdn.microsoft.com/library/windows/apps/mt280233).</span><span class="sxs-lookup"><span data-stu-id="42d7a-120">To learn more about handling network exceptions, see [Networking basics](https://msdn.microsoft.com/library/windows/apps/mt280233).</span></span>

<span data-ttu-id="42d7a-121">Firewalls und Webproxys werden häufig verwendet und können die Verwendung von Netzwerkfeatures beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="42d7a-121">Firewalls and web proxies are common and can affect the ability to use networking features.</span></span> <span data-ttu-id="42d7a-122">In einem Spiel über ein Netzwerk müssen Firewalls und Proxys ordnungsgemäß verarbeitet werden können.</span><span class="sxs-lookup"><span data-stu-id="42d7a-122">A game that uses networking needs to be prepared to properly handle firewalls and proxies.</span></span>

<span data-ttu-id="42d7a-123">Bei mobilen Geräten ist es wichtig, verfügbare Netzwerkressourcen zu überwachen und in getakteten Netzwerken entsprechend zu reagieren, da Roaming-oder Datenkosten anfallen können.</span><span class="sxs-lookup"><span data-stu-id="42d7a-123">For mobile devices, it is important to monitor available network resources and behave accordingly when on metered networks where roaming or data costs can be significant.</span></span>

<span data-ttu-id="42d7a-124">Die Netzwerkisolation ist Teil des von Windows verwendeten App-Sicherheitsmodells.</span><span class="sxs-lookup"><span data-stu-id="42d7a-124">Network isolation is part of the app security model used by Windows.</span></span> <span data-ttu-id="42d7a-125">Unter Windows werden Netzwerkgrenzen aktiv erkannt und Netzwerkzugriffsbeschränkungen für die Netzwerkisolation erzwungen.</span><span class="sxs-lookup"><span data-stu-id="42d7a-125">Windows actively discovers network boundaries and enforces network access restrictions for network isolation.</span></span> <span data-ttu-id="42d7a-126">Apps müssen Netzwerkisolationsfunktionen deklarieren, um den Umfang des Netzwerkzugriffs festzulegen.</span><span class="sxs-lookup"><span data-stu-id="42d7a-126">Apps must declare network isolation capabilities in order to define the scope of network access.</span></span> <span data-ttu-id="42d7a-127">Ohne Deklaration dieser Funktionen hat Ihre App keinen Zugriff auf Netzwerkressourcen.</span><span class="sxs-lookup"><span data-stu-id="42d7a-127">Without declaring these capabilities, your app will not have access to network resources.</span></span> <span data-ttu-id="42d7a-128">Unter [Konfigurieren von Netzwerkisolationsfunktionen](https://msdn.microsoft.com/library/windows/apps/hh770532) finden Sie weitere Informationen zur Erzwingung der Netzwerkisolation für Apps durch Windows.</span><span class="sxs-lookup"><span data-stu-id="42d7a-128">To learn more about how Windows enforces network isolation for apps, see [How to configure network isolation capabilities](https://msdn.microsoft.com/library/windows/apps/hh770532).</span></span>

## <a name="design-considerations"></a><span data-ttu-id="42d7a-129">Überlegungen bei der Entwicklung</span><span class="sxs-lookup"><span data-stu-id="42d7a-129">Design considerations</span></span>


<span data-ttu-id="42d7a-130">In DirectX-Spielen können verschiedene Netzwerk-APIs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="42d7a-130">A variety of networking APIs can be used in DirectX games.</span></span> <span data-ttu-id="42d7a-131">Daher ist es wichtig, die richtige API auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="42d7a-131">So, it is important to pick the right API.</span></span> <span data-ttu-id="42d7a-132">Windows unterstützt verschiedene Netzwerk-APIs, die Ihre App für die Kommunikation mit anderen Computern und Geräten entweder über das Internet oder private Netzwerke nutzen kann.</span><span class="sxs-lookup"><span data-stu-id="42d7a-132">Windows supports a variety of networking APIs that your app can use to communicate with other computers and devices over either the Internet or private networks.</span></span> <span data-ttu-id="42d7a-133">Sie müssen zunächst ermitteln, welche Netzwerkfeatures Ihre App erfordert.</span><span class="sxs-lookup"><span data-stu-id="42d7a-133">Your first step is to figure out what networking features your app needs.</span></span>

<span data-ttu-id="42d7a-134">Zu den beliebtesten Netzwerk-APIs für Spiele gehören:</span><span class="sxs-lookup"><span data-stu-id="42d7a-134">The more popular network APIs for games include:</span></span>

-   <span data-ttu-id="42d7a-135">TCP und Sockets – sorgen für eine zuverlässige Verbindung.</span><span class="sxs-lookup"><span data-stu-id="42d7a-135">TCP and sockets - Provides a reliable connection.</span></span> <span data-ttu-id="42d7a-136">Verwenden Sie TCP für Spielvorgänge, die keine Sicherheit erfordern.</span><span class="sxs-lookup"><span data-stu-id="42d7a-136">Use TCP for game operations that don’t need security.</span></span> <span data-ttu-id="42d7a-137">TCP ermöglicht eine einfache Skalierung des Servers, daher wird es häufig in Spielen mit dem Infrastruktur (Client-Server oder Peer-zu-Peer über das Internet)-Modell verwendet.</span><span class="sxs-lookup"><span data-stu-id="42d7a-137">TCP allows the server to easily scale, so it is commonly used in games that use the infrastructure (client-server or internet peer-to-peer) model.</span></span> <span data-ttu-id="42d7a-138">TCP kann auch für Ad-hoc-Spiele (lokales Peer-zu-Peer) über Wi-Fi Direct und Bluetooth verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="42d7a-138">TCP can also be used by ad hoc (local peer-to-peer) games over Wi-Fi Direct and Bluetooth.</span></span> <span data-ttu-id="42d7a-139">TCP wird in der Regel für die Bewegung von Spielobjekten, die Interaktion zwischen Spielfiguren, Textchat und andere Vorgänge verwendet.</span><span class="sxs-lookup"><span data-stu-id="42d7a-139">TCP is commonly used for game object movement, character interaction, text chat, and other operations.</span></span> <span data-ttu-id="42d7a-140">Die [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Klasse stellt einen TCP-Socket bereit, der in Windows Store-Spielen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="42d7a-140">The [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) class provides a TCP socket that can be used in Windows Store games.</span></span> <span data-ttu-id="42d7a-141">Die **StreamSocket**-Klasse wird zusammen mit verwandten Klassen im [**Windows::Networking::Sockets**](https://msdn.microsoft.com/library/windows/apps/br226960)-Namespace verwendet.</span><span class="sxs-lookup"><span data-stu-id="42d7a-141">The **StreamSocket** class is used with related classes in the [**Windows::Networking::Sockets**](https://msdn.microsoft.com/library/windows/apps/br226960) namespace.</span></span>
-   <span data-ttu-id="42d7a-142">TCP und Sockets mit SSL – sorgen für zuverlässige Verbindung und verhindern Mitverfolgung.</span><span class="sxs-lookup"><span data-stu-id="42d7a-142">TCP and sockets using SSL - Provides a reliable connection that prevents eavesdropping.</span></span> <span data-ttu-id="42d7a-143">Verwenden Sie TCP-Verbindungen mit SSL für Spielvorgänge, die Sicherheit erfordern.</span><span class="sxs-lookup"><span data-stu-id="42d7a-143">Use TCP connections with SSL for game operations that need security.</span></span> <span data-ttu-id="42d7a-144">Die Verschlüsselung und der Mehraufwand von SSL erhöht die Latenz- und Leistungskosten, daher wird SSL nur verwendet, wenn Sicherheit erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="42d7a-144">The encryption and overhead of SSL adds a cost in latency and performance, so it is only used when security is needed.</span></span> <span data-ttu-id="42d7a-145">TCP mit SSL wird in der Regel für Anmelde-, Kauf- und Handelsressourcen sowie die Erstellung und Verwaltung von Spielfiguren verwendet.</span><span class="sxs-lookup"><span data-stu-id="42d7a-145">TCP with SSL is commonly used for login, purchasing and trading assets, game character creation and management.</span></span> <span data-ttu-id="42d7a-146">Die [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)-Klasse bietet einen TCP-Socket, der SSL unterstützt.</span><span class="sxs-lookup"><span data-stu-id="42d7a-146">The [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882) class provides a TCP socket that supports SSL.</span></span>
-   <span data-ttu-id="42d7a-147">UDP und Sockets – bieten unzuverlässige Netzwerkübertragungen mit wenig Mehraufwand.</span><span class="sxs-lookup"><span data-stu-id="42d7a-147">UDP and sockets - Provides unreliable network transfers with low overhead.</span></span> <span data-ttu-id="42d7a-148">UDP wird für Spielvorgänge verwendet, die niedrige Latenz erfordern und Paketverluste tolerieren können.</span><span class="sxs-lookup"><span data-stu-id="42d7a-148">UDP is used for game operations that require low latency and can tolerate some packet loss.</span></span> <span data-ttu-id="42d7a-149">Dies wird häufig für Kampfspiele, Schießen mit Leuchtspur, Netzwerkaudio und Sprachchat verwendet.</span><span class="sxs-lookup"><span data-stu-id="42d7a-149">This is often used for fighting games, shooting and tracers, network audio, and voice chat.</span></span> <span data-ttu-id="42d7a-150">Die [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319)-Klasse stellt einen UDP-Socket bereit, der in Windows Store-Spielen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="42d7a-150">The [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319) class provides a UDP socket that can be used in Windows Store games.</span></span> <span data-ttu-id="42d7a-151">Die **DatagramSocket**-Klasse wird zusammen mit verwandten Klassen im [**Windows::Networking::Sockets**](https://msdn.microsoft.com/library/windows/apps/br226960)-Namespace verwendet.</span><span class="sxs-lookup"><span data-stu-id="42d7a-151">The **DatagramSocket** class is used with related classes in the [**Windows::Networking::Sockets**](https://msdn.microsoft.com/library/windows/apps/br226960) namespace.</span></span>
-   <span data-ttu-id="42d7a-152">HTTP-Client – stellt eine zuverlässige Verbindung mit HTTP-Servern bereit.</span><span class="sxs-lookup"><span data-stu-id="42d7a-152">HTTP Client - Provides a reliable connection to HTTP servers.</span></span> <span data-ttu-id="42d7a-153">Das gängigste Netzwerkszenario ist der Zugriff auf eine Website, um Informationen abzurufen oder zu speichern.</span><span class="sxs-lookup"><span data-stu-id="42d7a-153">The most common networking scenario is to access a web site to retrieve or store information.</span></span> <span data-ttu-id="42d7a-154">Ein einfaches Beispiel dafür ist ein Spiel, das eine Website zum Speichern von Benutzerinformationen und Spielständen verwendet.</span><span class="sxs-lookup"><span data-stu-id="42d7a-154">A simple example would be a game that uses a website to store user information and game scores.</span></span> <span data-ttu-id="42d7a-155">Wenn ein HTTP-Client zusammen mit SSL für die Sicherheit verwendet wird, kann er für Anmelde-, Kauf- und Handelsressourcen sowie die Erstellung und Verwaltung von Spielfiguren verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="42d7a-155">When used with SSL for security, an HTTP client can be used for login, purchasing, trading assets, game character creation, and management.</span></span> <span data-ttu-id="42d7a-156">Die [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639)-Klasse bietet eine moderne HTTP-Client-API zur Verwendung in Windows Store-Spielen.</span><span class="sxs-lookup"><span data-stu-id="42d7a-156">The [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) class provides a modern HTTP client API for use in Windows Store games.</span></span> <span data-ttu-id="42d7a-157">Die **HttpClient**-Klasse wird zusammen mit verwandten Klassen im [**Windows::Web::Http**](https://msdn.microsoft.com/library/windows/apps/dn279692)-Namespace verwendet.</span><span class="sxs-lookup"><span data-stu-id="42d7a-157">The **HttpClient** class is used with related classes in the [**Windows::Web::Http**](https://msdn.microsoft.com/library/windows/apps/dn279692) namespace.</span></span>

## <a name="handling-network-exceptions-in-your-directx-game"></a><span data-ttu-id="42d7a-158">Behandeln von Netzwerkausnahmen in einem DirectX-Spiel</span><span class="sxs-lookup"><span data-stu-id="42d7a-158">Handling network exceptions in your DirectX game</span></span>


<span data-ttu-id="42d7a-159">Wenn in Ihrem DirectX-Spiel eine Netzwerkausnahme auftritt, weist dies auf ein erhebliches Problem oder einen Fehler hin.</span><span class="sxs-lookup"><span data-stu-id="42d7a-159">When a network exception occurs in your DirectX game, this indicates a significant problem or failure.</span></span> <span data-ttu-id="42d7a-160">Ausnahmen können bei der Nutzung von Netzwerk-APIs viele Gründe haben.</span><span class="sxs-lookup"><span data-stu-id="42d7a-160">Exceptions can occur for many reasons when using networking APIs.</span></span> <span data-ttu-id="42d7a-161">Häufig ergeben sich Ausnahmen aus Änderungen bei der Netzwerkverbindung oder anderen Netzwerkproblemen mit dem Remotehost oder Server.</span><span class="sxs-lookup"><span data-stu-id="42d7a-161">Often, the exception can result from changes in network connectivity or other networking issues with the remote host or server.</span></span>

<span data-ttu-id="42d7a-162">Bei der Verwendung von Netzwerk-APIs können beispielsweise aus folgenden Gründen Ausnahmen auftreten:</span><span class="sxs-lookup"><span data-stu-id="42d7a-162">Some causes of exceptions when using networking APIs include the following:</span></span>

-   <span data-ttu-id="42d7a-163">Die Eingabe des Benutzers für einen Hostnamen oder einen URI enthält Fehler und ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="42d7a-163">Input from the user for a hostname or a URI contains errors and is not valid.</span></span>
-   <span data-ttu-id="42d7a-164">Fehler bei der Namensauflösung beim Suchen nach einem Hostnamen oder URI</span><span class="sxs-lookup"><span data-stu-id="42d7a-164">Name resolutions failures when looking up a hostname or a URi.</span></span>
-   <span data-ttu-id="42d7a-165">Verlust oder Änderung der Netzwerkverbindung</span><span class="sxs-lookup"><span data-stu-id="42d7a-165">Loss or change in network connectivity.</span></span>
-   <span data-ttu-id="42d7a-166">Netzwerkverbindungsfehler mit Sockets oder HTTP-Client-APIs</span><span class="sxs-lookup"><span data-stu-id="42d7a-166">Network connection failures using sockets or the HTTP client APIs.</span></span>
-   <span data-ttu-id="42d7a-167">Netzwerkserver- oder Remoteendpunktfehler</span><span class="sxs-lookup"><span data-stu-id="42d7a-167">Network server or remote endpoint errors.</span></span>
-   <span data-ttu-id="42d7a-168">Andere Netzwerkfehler</span><span class="sxs-lookup"><span data-stu-id="42d7a-168">Miscellaneous networking errors.</span></span>

<span data-ttu-id="42d7a-169">Ausnahmen aufgrund von Netzwerkfehlern (z.B. Unterbrechung oder Änderung der Netzwerkverbindung, Verbindungsfehler und Serverfehler) können jederzeit auftreten.</span><span class="sxs-lookup"><span data-stu-id="42d7a-169">Exceptions from network errors (for example, loss or change of connectivity, connection failures, and server failures) can happen at any time.</span></span> <span data-ttu-id="42d7a-170">Diese Fehler haben zur Folge, dass Ausnahmen ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="42d7a-170">These errors result in exceptions being thrown.</span></span> <span data-ttu-id="42d7a-171">Wenn eine Ausnahme nicht von Ihrer App behandelt wird, kann sie dazu führen, dass die gesamte App von der Runtime beendet wird.</span><span class="sxs-lookup"><span data-stu-id="42d7a-171">If an exception is not handled by your app, it can cause your entire app to be terminated by the runtime.</span></span>

<span data-ttu-id="42d7a-172">Beim Aufrufen der meisten asynchronen Netzwerkmethoden müssen Sie Code zum Behandeln von Ausnahmen schreiben.</span><span class="sxs-lookup"><span data-stu-id="42d7a-172">You must write code to handle exceptions when you call most asynchronous network methods.</span></span> <span data-ttu-id="42d7a-173">In manchen Fällen kann versucht werden, eine Netzwerkmethode beim Auftreten einer Ausnahme zu wiederholen, um das Problem zu beheben.</span><span class="sxs-lookup"><span data-stu-id="42d7a-173">Sometimes, when an exception occurs, a network method can be retried as a way to resolve the problem.</span></span> <span data-ttu-id="42d7a-174">In anderen Fällen muss die App ohne Netzwerkverbindung mit zuvor zwischengespeicherten Daten weiter ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="42d7a-174">Other times, your app may need to plan to continue without network connectivity using previously cached data.</span></span>

<span data-ttu-id="42d7a-175">UWP-Apps (Universelle Windows-Plattform) lösen im Allgemeinen nur eine Ausnahme aus.</span><span class="sxs-lookup"><span data-stu-id="42d7a-175">Universal Windows Platform (UWP) apps generally throw a single exception.</span></span> <span data-ttu-id="42d7a-176">Ihr Ausnahmehandler kann detailliertere Informationen zur Ursache abrufen, um die Ausnahme besser verstehen und entsprechende Entscheidungen treffen zu können.</span><span class="sxs-lookup"><span data-stu-id="42d7a-176">Your exception handler can retrieve more detailed information about the cause of the exception to better understand the failure and make appropriate decisions.</span></span>

<span data-ttu-id="42d7a-177">Wenn eine Ausnahme in einem DirectX-Spiel auftritt, bei dem es sich um eine UWP-App handelt, kann der **HRESULT**-Wert zur Ermittlung der Fehlerursache abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="42d7a-177">When an exception occurs in a DirectX game that is a UWP app, the **HRESULT** value for the cause of the error can be retrieved.</span></span> <span data-ttu-id="42d7a-178">Die *Winerror.h*-Includedatei enthält eine umfangreiche Liste möglicher **HRESULT**-Werte, die Netzwerkfehler umfasst.</span><span class="sxs-lookup"><span data-stu-id="42d7a-178">The *Winerror.h* include file contains a large list of possible **HRESULT** values that includes network errors.</span></span>

<span data-ttu-id="42d7a-179">Die Netzwerk-APIs unterstützen verschiedene Methoden zum Abrufen der detaillierten Informationen zur Ursache der Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="42d7a-179">The networking APIs support different methods for retrieving this detailed information about the cause of an exception.</span></span>

-   <span data-ttu-id="42d7a-180">Eine Methode zum Abrufen des **HRESULT**-Werts des Fehlers, der die Ausnahme verursacht hat.</span><span class="sxs-lookup"><span data-stu-id="42d7a-180">A method to retrieve the **HRESULT** value of the error that caused the exception.</span></span> <span data-ttu-id="42d7a-181">Die mögliche Liste potenzieller **HRESULT**-Werte ist lang und nicht spezifiziert.</span><span class="sxs-lookup"><span data-stu-id="42d7a-181">The possible list of potential **HRESULT** values is large and unspecified.</span></span> <span data-ttu-id="42d7a-182">Der **HRESULT**-Wert kann abgerufen werden, wenn eine der Netzwerk-APIs verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="42d7a-182">The **HRESULT** value can be retrieved when using any of the networking APIs.</span></span>
-   <span data-ttu-id="42d7a-183">Eine Hilfsmethode, die den **HRESULT**-Wert in einen Enumerationswert konvertiert.</span><span class="sxs-lookup"><span data-stu-id="42d7a-183">A helper method that converts the **HRESULT** value to an enumeration value.</span></span> <span data-ttu-id="42d7a-184">Die Liste der möglichen Enumerationswerte ist spezifiziert und relativ kurz.</span><span class="sxs-lookup"><span data-stu-id="42d7a-184">The list of possible enumeration values is specified and relatively small.</span></span> <span data-ttu-id="42d7a-185">Eine Hilfsmethode für die Socketklassen ist in [**Windows::Networking::Sockets**](https://msdn.microsoft.com/library/windows/apps/br226960) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="42d7a-185">A helper method is available for the socket classes in the [**Windows::Networking::Sockets**](https://msdn.microsoft.com/library/windows/apps/br226960).</span></span>

### <a name="exceptions-in-windowsnetworkingsockets"></a><span data-ttu-id="42d7a-186">Ausnahmen in „Windows.Networking.Sockets“</span><span class="sxs-lookup"><span data-stu-id="42d7a-186">Exceptions in Windows.Networking.Sockets</span></span>

<span data-ttu-id="42d7a-187">Der Konstruktor für die [**HostName**](https://msdn.microsoft.com/library/windows/apps/br207113)-Klasse in Verbindung mit Sockets kann eine Ausnahme auslösen, wenn die übergebene Zeichenfolge kein gültiger Hostname ist (enthält Zeichen, die in einem Hostnamen nicht zulässig sind).</span><span class="sxs-lookup"><span data-stu-id="42d7a-187">The constructor for the [**HostName**](https://msdn.microsoft.com/library/windows/apps/br207113) class used with sockets can throw an exception if the string passed is not a valid hostname (contains characters that are not allowed in a host name).</span></span> <span data-ttu-id="42d7a-188">Wenn eine App vom Benutzer eine Eingabe für das **HostName**-Element einer Peerverbindung zum Spielen erhält, sollte sich der Konstruktor innerhalb eines try/catch-Blocks befinden.</span><span class="sxs-lookup"><span data-stu-id="42d7a-188">If an app gets input from the user for the **HostName** for a peer connection for gaming, the constructor should be in a try/catch block.</span></span> <span data-ttu-id="42d7a-189">Wenn eine Ausnahme ausgelöst wird, kann die App den Benutzer benachrichtigen und einen neuen Hostnamen anfordern.</span><span class="sxs-lookup"><span data-stu-id="42d7a-189">If an exception is thrown, the app can notify the user and request a new hostname.</span></span>

<span data-ttu-id="42d7a-190">Hinzufügen von Code zum Überprüfen einer Zeichenfolge für einen Hostnamen vom Benutzer</span><span class="sxs-lookup"><span data-stu-id="42d7a-190">Add code to validate a string for a hostname from the user</span></span>

```cpp

    // Define some variables at the class level.
    Windows::Networking::HostName^ remoteHost;

    bool isHostnameFromUser = false;
    bool isHostnameValid = false;

    ///...

    // If the value of 'remoteHostname' is set by the user in a control as input 
    // and is therefore untrusted input and could contain errors. 
    // If we can't create a valid hostname, we notify the user in statusText 
    // about the incorrect input.

    String ^hostString = remoteHostname;

    try 
    {
        remoteHost = ref new Windows::Networking:Host(hostString);
        isHostnameValid = true;
    }
    catch (InvalidArgumentException ^ex)
    {
        statusText->Text = "You entered a bad hostname, please re-enter a valid hostname.";
        return;
    }

    isHostnameFromUser = true;


    // ... Continue with code to execute with a valid hostname.
```

<span data-ttu-id="42d7a-191">Der [**Windows.Networking.Sockets**](https://msdn.microsoft.com/library/windows/apps/br226960)-Namespace enthält praktische Hilfsmethoden und Enumerationen für die Behandlung von Fehlern bei der Verwendung von Sockets.</span><span class="sxs-lookup"><span data-stu-id="42d7a-191">The [**Windows.Networking.Sockets**](https://msdn.microsoft.com/library/windows/apps/br226960) namespace has convenient helper methods and enumerations for handling errors when using sockets.</span></span> <span data-ttu-id="42d7a-192">Mit ihnen lassen sich spezifische Netzwerkausnahmen in der App unterschiedlich behandeln.</span><span class="sxs-lookup"><span data-stu-id="42d7a-192">This can be useful for handling specific network exceptions differently in your app.</span></span>

<span data-ttu-id="42d7a-193">Ein Fehler, der für einen [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319)-, [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882)- oder [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906)-Vorgang auftritt, führt zur Auslösung einer Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="42d7a-193">An error encountered on [**DatagramSocket**](https://msdn.microsoft.com/library/windows/apps/br241319), [**StreamSocket**](https://msdn.microsoft.com/library/windows/apps/br226882), or [**StreamSocketListener**](https://msdn.microsoft.com/library/windows/apps/br226906) operation results in an exception being thrown.</span></span> <span data-ttu-id="42d7a-194">Die Ursache der Ausnahme ist ein Fehlerwert, der als **HRESULT**-Wert dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="42d7a-194">The cause of the exception is an error value represented as an **HRESULT** value.</span></span> <span data-ttu-id="42d7a-195">Mit der [**SocketError.GetStatus**](https://msdn.microsoft.com/library/windows/apps/hh701462)-Methode wird ein Netzwerkfehler aus einem Socketvorgang in einen [**SocketErrorStatus**](https://msdn.microsoft.com/library/windows/apps/hh701457)-Enumerationswert konvertiert.</span><span class="sxs-lookup"><span data-stu-id="42d7a-195">The [**SocketError.GetStatus**](https://msdn.microsoft.com/library/windows/apps/hh701462) method is used to convert a network error from a socket operation to a [**SocketErrorStatus**](https://msdn.microsoft.com/library/windows/apps/hh701457) enumeration value.</span></span> <span data-ttu-id="42d7a-196">Die meisten **SocketErrorStatus**-Enumerationswerte entsprechen einem vom systemeigenen WindowsSockets-Vorgang zurückgegebenen Fehler.</span><span class="sxs-lookup"><span data-stu-id="42d7a-196">Most of the **SocketErrorStatus** enumeration values correspond to an error returned by the native Windows sockets operation.</span></span> <span data-ttu-id="42d7a-197">Eine App kann nach bestimmten **SocketErrorStatus**-Enumerationswerten filtern, um das App-Verhalten je nach Ausnahmeursache zu ändern.</span><span class="sxs-lookup"><span data-stu-id="42d7a-197">An app can filter on specific **SocketErrorStatus** enumeration values to modify app behavior depending on the cause of the exception.</span></span>

<span data-ttu-id="42d7a-198">Bei Parameterprüfungsfehlern kann eine App den **HRESULT**-Wert aus der Ausnahme auch verwenden, um ausführlichere Informationen zum zugehörigen Fehler zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="42d7a-198">For parameter validation errors, an app can also use the **HRESULT** from the exception to learn more detailed information about the error that caused the exception.</span></span> <span data-ttu-id="42d7a-199">Mögliche **HRESULT**-Werte sind in der Headerdatei *Winerror.h* aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="42d7a-199">Possible **HRESULT** values are listed in the *Winerror.h* header file.</span></span> <span data-ttu-id="42d7a-200">Für die meisten Parameterüberprüfungsfehler wird der **HRESULT**-Wert **E\_INVALIDARG** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="42d7a-200">For most parameter validation errors, the **HRESULT** returned is **E\_INVALIDARG**.</span></span>

<span data-ttu-id="42d7a-201">Hinzufügen von Code zum Behandeln von Ausnahmen beim Herstellen einer Streamsocketverbindung</span><span class="sxs-lookup"><span data-stu-id="42d7a-201">Add code to handle exceptions when trying to make a stream socket connection</span></span>

```cpp
using namespace Windows::Networking;
using namespace Windows::Networking::Sockets;

    
    // Define some more variables at the class level.

    bool isSocketConnected = false
    bool retrySocketConnect = false;

    // The number of times we have tried to connect the socket.
    unsigned int retryConnectCount = 0;

    // The maximum number of times to retry a connect operation.
    unsigned int maxRetryConnectCount = 5; 
    ///...

    // We pass in a valid remoteHost and serviceName parameter.
    // The hostname can contain a name or an IP address.
    // The servicename can contain a string or a TCP port number.

    StreamSocket ^ socket = ref new StreamSocket();
    SocketErrorStatus errorStatus; 
    HResult hr;

    // Save the socket, so any subsequent steps can use it.
    CoreApplication::Properties->Insert("clientSocket", socket);

    // Connect to the remote server. 
    create_task(socket->ConnectAsync(
            remoteHost,
            serviceName,
            SocketProtectionLevel::PlainSocket)).then([this] (task<void> previousTask)
    {
        try
        {
            // Try getting all exceptions from the continuation chain above this point.
            previousTask.get();

            isSocketConnected = true;
            // Mark the socket as connected. We do not really care about the value of the property, but the mere 
            // existence of  it means that we are connected.
            CoreApplication::Properties->Insert("connected", nullptr);
        }
        catch (Exception^ ex)
        {
            hr = ex.HResult;
            errorStatus = SocketStatus::GetStatus(hr); 
            if (errorStatus != Unknown)
            {
                                                                switch (errorStatus) 
                   {
                    case HostNotFound:
                        // If the hostname is from the user, this may indicate a bad input.
                        // Set a flag to ask the user to re-enter the hostname.
                        isHostnameValid = false;
                        return;
                        break;
                    case ConnectionRefused:
                        // The server might be temporarily busy.
                        retrySocketConnect = true;
                        return;
                        break; 
                    case NetworkIsUnreachable: 
                        // This could be a connectivity issue.
                        retrySocketConnect = true;
                        break;
                    case UnreachableHost: 
                        // This could be a connectivity issue.
                        retrySocketConnect = true;
                        break;
                    case NetworkIsDown: 
                        // This could be a connectivity issue.
                        retrySocketConnect = true;
                        break;
                    // Handle other errors. 
                    default: 
                        // The connection failed and no options are available.
                        // Try to use cached data if it is available. 
                        // You may want to tell the user that the connect failed.
                        break;
                }
                }
                else 
                {
                    // Received an Hresult that is not mapped to an enum.
                    // This could be a connectivity issue.
                    retrySocketConnect = true;
                }
            }
        });
    }

```

### <a name="exceptions-in-windowswebhttp"></a><span data-ttu-id="42d7a-202">Ausnahmen in „Windows.Web.Http“</span><span class="sxs-lookup"><span data-stu-id="42d7a-202">Exceptions in Windows.Web.Http</span></span>

<span data-ttu-id="42d7a-203">Der Konstruktor für die [**Windows::Foundation::Uri**](https://msdn.microsoft.com/library/windows/apps/br225998)-Klasse in Verbindung mit [**Windows::Web::Http::HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) kann eine Ausnahme auslösen, wenn die übergebene Zeichenfolge kein gültiger URI ist (enthält Zeichen, die in einem URI nicht zulässig sind).</span><span class="sxs-lookup"><span data-stu-id="42d7a-203">The constructor for the [**Windows::Foundation::Uri**](https://msdn.microsoft.com/library/windows/apps/br225998) class used with [**Windows::Web::Http::HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) can throw an exception if the string passed is not a valid URI (contains characters that are not allowed in a URI).</span></span> <span data-ttu-id="42d7a-204">In C++ gibt es keine Methode zum Analysieren einer Zeichenfolge für einen URI.</span><span class="sxs-lookup"><span data-stu-id="42d7a-204">In C++, there is no method to try and parse a string to a URI.</span></span> <span data-ttu-id="42d7a-205">Wenn eine App vom Benutzer eine Eingabe für das **Windows::Foundation::Uri**-Element erhält, sollte sich der Konstruktor innerhalb eines try/catch-Blocks befinden.</span><span class="sxs-lookup"><span data-stu-id="42d7a-205">If an app gets input from the user for the **Windows::Foundation::Uri**, the constructor should be in a try/catch block.</span></span> <span data-ttu-id="42d7a-206">Wenn eine Ausnahme ausgelöst wird, kann die App den Benutzer benachrichtigen und einen neuen URI anfordern.</span><span class="sxs-lookup"><span data-stu-id="42d7a-206">If an exception is thrown, the app can notify the user and request a new URI.</span></span>

<span data-ttu-id="42d7a-207">Von der App sollte auch überprüft werden, ob das Schema im URI HTTP oder HTTPS lautet, da dies die einzigen von [**Windows::Web::Http::HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) unterstützten Schemas sind.</span><span class="sxs-lookup"><span data-stu-id="42d7a-207">Your app should also check that the scheme in the URI is HTTP or HTTPS since these are the only schemes supported by the [**Windows::Web::Http::HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639).</span></span>

<span data-ttu-id="42d7a-208">Hinzufügen von Code zum Überprüfen einer Zeichenfolge für einen URI vom Benutzer</span><span class="sxs-lookup"><span data-stu-id="42d7a-208">Add code to validate a string for a URI from the user</span></span>

```cpp

    // Define some variables at the class level.
    Windows::Foundation::Uri^ resourceUri;

    bool isUriFromUser = false;
    bool isUriValid = false;

    ///...

    // If the value of 'inputUri' is set by the user in a control as input 
    // and is therefore untrusted input and could contain errors. 
    // If we can't create a valid hostname, we notify the user in statusText 
    // about the incorrect input.

    String ^uriString = inputUri;

    try 
    {
        isUriValid = false;
        resourceUri = ref new Windows::Foundation:Uri(uriString);

        if (resourceUri->SchemeName != "http" && resourceUri->SchemeName != "https")
        {
            statusText->Text = "Only 'http' and 'https' schemes supported. Please re-enter URI";
            return;
        }
        isUriValid = true;
    }
    catch (InvalidArgumentException ^ex)
    {
        statusText->Text = "You entered a bad URI, please re-enter Uri to continue.";
        return;
    }

    isUriFromUser = true;


    // ... Continue with code to execute with a valid URI.
```

<span data-ttu-id="42d7a-209">Der [**Windows::Web::Http**](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx)-Namespace bietet keine Funktion, die die Behandlung von Ausnahmen erleichtert.</span><span class="sxs-lookup"><span data-stu-id="42d7a-209">The [**Windows::Web::Http**](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx) namespace lacks a convenience function.</span></span> <span data-ttu-id="42d7a-210">Eine App, die [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) und andere Klassen in diesem Namespace verwendet, muss daher den **HRESULT**-Wert verwenden.</span><span class="sxs-lookup"><span data-stu-id="42d7a-210">So, an app using [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) and other classes in this namespace needs to use the **HRESULT** value.</span></span>

<span data-ttu-id="42d7a-211">In Apps mit C++ stellt das [**Platform::Exception**](https://msdn.microsoft.com/library/windows/apps/hh755825.aspx)-Objekt einen Fehler während der App-Ausführung dar, wenn eine Ausnahme auftritt.</span><span class="sxs-lookup"><span data-stu-id="42d7a-211">In apps using C++, the [**Platform::Exception**](https://msdn.microsoft.com/library/windows/apps/hh755825.aspx) represents an error during app execution when an exception occurs.</span></span> <span data-ttu-id="42d7a-212">Die [**Platform::Exception::HResult**](https://msdn.microsoft.com/library/windows/apps/hh763371.aspx)-Eigenschaft gibt den **HRESULT**-Wert zurück, der der jeweiligen Ausnahme zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="42d7a-212">The [**Platform::Exception::HResult**](https://msdn.microsoft.com/library/windows/apps/hh763371.aspx) property returns the **HRESULT** assigned to the specific exception.</span></span> <span data-ttu-id="42d7a-213">Die [**Platform::Exception::Message**](https://msdn.microsoft.com/library/windows/apps/hh763375.aspx)-Eigenschaft gibt die vom System bereitgestellte Zeichenfolge zurück, die dem **HRESULT**-Wert zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="42d7a-213">The [**Platform::Exception::Message**](https://msdn.microsoft.com/library/windows/apps/hh763375.aspx) property returns the system-provided string that is associated with the **HRESULT** value.</span></span> <span data-ttu-id="42d7a-214">Mögliche **HRESULT**-Werte sind in der Headerdatei *Winerror.h* aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="42d7a-214">Possible **HRESULT** values are listed in the *Winerror.h* header file.</span></span> <span data-ttu-id="42d7a-215">Eine App kann nach bestimmten **HRESULT**-Werten filtern, um das App-Verhalten je nach Ausnahmeursache zu ändern.</span><span class="sxs-lookup"><span data-stu-id="42d7a-215">An app can filter on specific **HRESULT** values to modify app behavior depending on the cause of the exception.</span></span>

<span data-ttu-id="42d7a-216">Für die meisten Parameterüberprüfungsfehler wird der **HRESULT**-Wert **E\_INVALIDARG** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="42d7a-216">For most parameter validation errors, the **HRESULT** returned is **E\_INVALIDARG**.</span></span> <span data-ttu-id="42d7a-217">Bei manchen unzulässigen Methodenaufrufen wird der **HRESULT**-Wert **E\_ILLEGAL\_METHOD\_CALL** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="42d7a-217">For some illegal method calls, the **HRESULT** returned is **E\_ILLEGAL\_METHOD\_CALL**.</span></span>

<span data-ttu-id="42d7a-218">Hinzufügen von Code zum Behandeln von Ausnahmen beim Verwenden von [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) zum Herstellen einer Verbindung mit einem HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="42d7a-218">Add code to handle exceptions when trying to use [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) to connect to an HTTP server</span></span>

```cpp
using namespace Windows::Foundation;
using namespace Windows::Web::Http;
    
    // Define some more variables at the class level.

    bool isHttpClientConnected = false
    bool retryHttpClient = false;

    // The number of times we have tried to connect the socket
    unsigned int retryConnectCount = 0;

    // The maximum number of times to retry a connect operation.
    unsigned int maxRetryConnectCount = 5; 
    ///...

    // We pass in a valid resourceUri parameter.
    // The URI must contain a scheme and a name or an IP address.

    HttpClient ^ httpClient = ref new HttpClient();
    HResult hr;

    // Save the httpClient, so any subsequent steps can use it.
    CoreApplication::Properties->Insert("httpClient", httpClient);

    // Send a GET request to the HTTP server. 
    create_task(httpClient->GetAsync(resourceUri)).then([this] (task<void> previousTask)
    {
        try
        {
            // Try getting all exceptions from the continuation chain above this point.
            previousTask.get();

            isHttpClientConnected = true;
            // Mark the HttClient as connected. We do not really care about the value of the property, but the mere 
            // existence of  it means that we are connected.
            CoreApplication::Properties->Insert("connected", nullptr);
        }
        catch (Exception^ ex)
        {
            hr = ex.HResult;
                                                switch (errorStatus) 
               {
                case WININET_E_NAME_NOT_RESOLVED:
                    // If the Uri is from the user, this may indicate a bad input.
                    // Set a flag to ask user to re-enter the Uri.
                    isUriValid = false;
                    return;
                    break;
                case WININET_E_CANNOT_CONNECT:
                    // The server might be temporarily busy.
                    retryHttpClientConnect = true;
                    return;
                    break; 
                case WININET_E_CONNECTION_ABORTED: 
                    // This could be a connectivity issue.
                    retryHttpClientConnect = true;
                    break;
                case WININET_E_CONNECTION_RESET: 
                    // This could be a connectivity issue.
                    retryHttpClientConnect = true;
                    break;
                case INET_E_RESOURCE_NOT_FOUND: 
                    // The server cannot locate the resource specified in the uri.
                    // If the Uri is from user, this may indicate a bad input.
                    // Set a flag to ask the user to re-enter the Uri
                    isUriValid = false;
                    return;
                    break;
                // Handle other errors. 
                default: 
                    // The connection failed and no options are available.
                    // Try to use cached data if it is available. 
                    // You may want to tell the user that the connect failed.
                    break;
            }
            else 
            {
                // Received an Hresult that is not mapped to an enum.
                // This could be a connectivity issue.
                retrySocketConnect = true;
            }
        }
    });
    

```

## <a name="related-topics"></a><span data-ttu-id="42d7a-219">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="42d7a-219">Related topics</span></span>


**<span data-ttu-id="42d7a-220">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="42d7a-220">Other resources</span></span>**

* [<span data-ttu-id="42d7a-221">Herstellen einer Verbindung mit einem Datagrammsocket</span><span class="sxs-lookup"><span data-stu-id="42d7a-221">Connecting with a datagram socket</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj635238)
* [<span data-ttu-id="42d7a-222">Herstellen einer Verbindung mit einer Netzwerkressource mit einem Streamsocket</span><span class="sxs-lookup"><span data-stu-id="42d7a-222">Connecting to a network resource with a stream socket</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj150599)
* [<span data-ttu-id="42d7a-223">Herstellen einer Verbindung mit Netzwerkdiensten</span><span class="sxs-lookup"><span data-stu-id="42d7a-223">Connecting to network services</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452976)
* [<span data-ttu-id="42d7a-224">Herstellen von Verbindungen mit Webdiensten</span><span class="sxs-lookup"><span data-stu-id="42d7a-224">Connecting to web services</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh761504)
* [<span data-ttu-id="42d7a-225">Grundlagen zum Netzwerk</span><span class="sxs-lookup"><span data-stu-id="42d7a-225">Networking basics</span></span>](https://msdn.microsoft.com/library/windows/apps/mt280233)
* [<span data-ttu-id="42d7a-226">So wird's gemacht: Konfigurieren von Netzwerkisolationsfunktionen</span><span class="sxs-lookup"><span data-stu-id="42d7a-226">How to configure network isolation capabilities</span></span>](https://msdn.microsoft.com/library/windows/apps/hh770532)
* [<span data-ttu-id="42d7a-227">Aktivieren von Loopback und Debuggen der Netzwerkisolation</span><span class="sxs-lookup"><span data-stu-id="42d7a-227">How to enable loopback and debug network isolation</span></span>](https://msdn.microsoft.com/library/windows/apps/hh780593)

**<span data-ttu-id="42d7a-228">Referenz</span><span class="sxs-lookup"><span data-stu-id="42d7a-228">Reference</span></span>**

* [**<span data-ttu-id="42d7a-229">DatagramSocket</span><span class="sxs-lookup"><span data-stu-id="42d7a-229">DatagramSocket</span></span>**](https://msdn.microsoft.com/library/windows/apps/br241319)
* [**<span data-ttu-id="42d7a-230">HttpClient</span><span class="sxs-lookup"><span data-stu-id="42d7a-230">HttpClient</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn298639)
* [**<span data-ttu-id="42d7a-231">StreamSocket</span><span class="sxs-lookup"><span data-stu-id="42d7a-231">StreamSocket</span></span>**](https://msdn.microsoft.com/library/windows/apps/br226882)
* [**<span data-ttu-id="42d7a-232">Windows::Web::Http</span><span class="sxs-lookup"><span data-stu-id="42d7a-232">Windows::Web::Http</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn279692)
* [**<span data-ttu-id="42d7a-233">Windows::Networking::Sockets</span><span class="sxs-lookup"><span data-stu-id="42d7a-233">Windows::Networking::Sockets</span></span>**](https://msdn.microsoft.com/library/windows/apps/br226960)

**<span data-ttu-id="42d7a-234">Beispiele</span><span class="sxs-lookup"><span data-stu-id="42d7a-234">Samples</span></span>**

* [<span data-ttu-id="42d7a-235">DatagramSocket-Beispiel</span><span class="sxs-lookup"><span data-stu-id="42d7a-235">DatagramSocket sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=243037)
* [<span data-ttu-id="42d7a-236">HttpClient-Beispiel</span><span class="sxs-lookup"><span data-stu-id="42d7a-236">HttpClient Sample</span></span>]( http://go.microsoft.com/fwlink/p/?linkid=242550)
* [<span data-ttu-id="42d7a-237">Näherungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="42d7a-237">Proximity sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=245082)
* [<span data-ttu-id="42d7a-238">Beispiel für StreamSocket</span><span class="sxs-lookup"><span data-stu-id="42d7a-238">StreamSocket sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=243037)
