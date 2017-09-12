---
author: joannaleecy
title: Handbuch zur Entwicklung von Spielen unter Windows10
description: "Ein umfassender Leitfaden mit Ressourcen und Informationen zur Entwicklung von Spielen für die universelle Windows-Plattform (UWP)."
ms.assetid: 6061F498-96A8-44EF-9711-68AE5A1218C9
ms.author: joanlee
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Spiele, Entwickeln von Spielen
ms.openlocfilehash: f84f33f4e30391624ae8d2615cb9c27442e168fb
ms.sourcegitcommit: 63c815f8c6665872987b5410cabf324f2b7e3c7c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2017
---
# <a name="windows-10-game-development-guide"></a><span data-ttu-id="1b065-104">Handbuch zur Entwicklung von Spielen unter Windows10</span><span class="sxs-lookup"><span data-stu-id="1b065-104">Windows 10 game development guide</span></span>


<span data-ttu-id="1b065-105">Willkommen beim Windows10-Handbuch für die Entwicklung von Spielen.</span><span class="sxs-lookup"><span data-stu-id="1b065-105">Welcome to the Windows 10 game development guide!</span></span>

<span data-ttu-id="1b065-106">Dieses Handbuch enthält eine umfassende Sammlung von Ressourcen und Informationen, die Sie für die Entwicklung von Spielen für die Universelle Windows-Plattform (UWP) benötigen.</span><span class="sxs-lookup"><span data-stu-id="1b065-106">This guide provides an end-to-end collection of the resources and information you'll need to develop a Universal Windows Platform (UWP) game.</span></span> <span data-ttu-id="1b065-107">Eine englische Version (USA) dieses Handbuchs steht im [PDF](http://download.microsoft.com/download/3/E/8/3E8F6376-D239-41A3-989C-DA1494C0024D/Windev_Game_Dev_Guide_May_2017.pdf)-Format zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1b065-107">An English (US) version of this guide is available in [PDF](http://download.microsoft.com/download/3/E/8/3E8F6376-D239-41A3-989C-DA1494C0024D/Windev_Game_Dev_Guide_May_2017.pdf) format.</span></span>

## <a name="introduction-to-game-development-for-the-universal-windows-platform-uwp"></a><span data-ttu-id="1b065-108">Einführung in die Spieleentwicklung für die universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="1b065-108">Introduction to game development for the Universal Windows Platform (UWP)</span></span>


<span data-ttu-id="1b065-109">Mit einem Windows10-Spiel können Sie Millionen Smartphone-, PC- und XboxOne-Benutzer auf der ganzen Welt erreichen.</span><span class="sxs-lookup"><span data-stu-id="1b065-109">When you create a Windows 10 game, you have the opportunity to reach millions of players worldwide across phone, PC, and Xbox One.</span></span> <span data-ttu-id="1b065-110">Dank Xbox auf Windows, Xbox Live, geräteübergreifendem Multiplayer, einer tollen Spiele-Community und leistungsstarken neuen Features wie die Universelle Windows-Plattform (UWP) und DirectX12 begeistern Windows10-Spiele Spieler aller Altersklassen und Genres.</span><span class="sxs-lookup"><span data-stu-id="1b065-110">With Xbox on Windows, Xbox Live, cross-device multiplayer, an amazing gaming community, and powerful new features like the Universal Windows Platform (UWP) and DirectX 12, Windows 10 games thrill players of all ages and genres.</span></span> <span data-ttu-id="1b065-111">Die neue universelle Windows-Plattform (UWP) gewährleistet durch eine gemeinsame API für Smartphone, PC und Xbox One die geräteübergreifende Kompatibilität Ihres Spiels unter Windows10 und stellt zudem Tools und Optionen bereit, mit denen Sie Ihr Spiel optimal an die jeweilige Geräteumgebung anpassen können.</span><span class="sxs-lookup"><span data-stu-id="1b065-111">The new Universal Windows Platform (UWP) delivers compatibility for your game across Windows 10 devices with a common API for phone, PC, and Xbox One, along with tools and options to tailor your game to each device experience.</span></span>

<span data-ttu-id="1b065-112">Dieses Handbuch enthält eine umfassende Sammlung von hilfreichen Informationen und Ressourcen für die Spieleentwicklung.</span><span class="sxs-lookup"><span data-stu-id="1b065-112">This guide provides an end-to-end collection of information and resources that will help you as you develop your game.</span></span> <span data-ttu-id="1b065-113">Die Abschnittsstruktur orientiert sich an den Entwicklungsphasen und vereinfacht die Informationssuche.</span><span class="sxs-lookup"><span data-stu-id="1b065-113">The sections are organized according to the stages of game development, so you'll know where to look for information when you need it.</span></span>

<span data-ttu-id="1b065-114">Der Einführungsabschnitt [Ressourcen für die Spieleentwicklung](#game-development-resources) bietet einen allgemeinen Überblick über die Dokumentation, Programme und andere hilfreiche Ressourcen für die Spieleerstellung.</span><span class="sxs-lookup"><span data-stu-id="1b065-114">To get started, the [Game development resources](#game-development-resources) section provides a high-level survey of documentation, programs, and other resources that are helpful when creating a game.</span></span>

<span data-ttu-id="1b065-115">Dieses Handbuch wird bei Bedarf mit weiteren Ressourcen für die Entwicklung von Windows10-Spielen aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="1b065-115">This guide will be updated as additional Windows 10 game development resources and material become available.</span></span>  

## <a name="game-development-resources"></a><span data-ttu-id="1b065-116">Ressourcen für die Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="1b065-116">Game development resources</span></span>

<span data-ttu-id="1b065-117">Von der Dokumentation bis hin zu Entwicklerprogrammen, Foren, Blogs und Beispielen steht Ihnen bei der Spieleentwicklung eine Vielzahl hilfreicher Ressourcen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1b065-117">From documentation to developer programs, forums, blogs, and samples, there are many resources available to help you on your game development journey.</span></span> <span data-ttu-id="1b065-118">Hier finden Sie eine Zusammenfassung wichtiger Ressourcen für den Einstieg in die Entwicklung Ihres Windows 10-Spiels.</span><span class="sxs-lookup"><span data-stu-id="1b065-118">Here's a roundup of resources to know about as you begin developing your Windows 10 game.</span></span>

> [!Note]
> <span data-ttu-id="1b065-119">Einige Features werden über verschiedene Programme verwaltet.</span><span class="sxs-lookup"><span data-stu-id="1b065-119">Some features are managed through various programs.</span></span> <span data-ttu-id="1b065-120">Dieses Handbuch behandelt eine breite Palette von Ressourcen. Je nach Programmteilnahme oder spezifischer Entwicklungsrolle stehen Ihnen bestimmte Ressourcen unter Umständen nicht zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1b065-120">This guide covers a broad range of resources, so you may find that some resources are inaccessible depending on the program you are in or your specific development role.</span></span> <span data-ttu-id="1b065-121">Beispiele wären etwa Links, die zu „developer.xboxlive.com“, „forums.xboxlive.com“, „xdi.xboxlive.com“ oder zum Netzwerk für Spieleentwickler (Game Developer Network, GDN) aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="1b065-121">Examples are links that resolve to developer.xboxlive.com, forums.xboxlive.com, xdi.xboxlive.com, or the Game Developer Network (GDN).</span></span> <span data-ttu-id="1b065-122">Informationen zur Partnerschaft mit Microsoft finden Sie unter [Entwicklerprogramme](#developer-programs).</span><span class="sxs-lookup"><span data-stu-id="1b065-122">For information about partnering with Microsoft, see [Developer Programs](#developer-programs).</span></span>


### <a name="game-development-documentation"></a><span data-ttu-id="1b065-123">Dokumentation für die Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="1b065-123">Game development documentation</span></span>

<span data-ttu-id="1b065-124">In diesem Handbuch finden Sie immer wieder direkte Links zu relevanten Dokumentationen – strukturiert nach Aufgabe, Technologie und Entwicklungsphase.</span><span class="sxs-lookup"><span data-stu-id="1b065-124">Throughout this guide, you'll find deep links to relevant documentation—organized by task, technology, and stage of game development.</span></span> <span data-ttu-id="1b065-125">Hier sehen Sie eine Übersicht über die wichtigsten verfügbaren Dokumentationsportale für die Entwicklung von Windows10-Spielen.</span><span class="sxs-lookup"><span data-stu-id="1b065-125">To give you a broad view of what's available, here are the main documentation portals for Windows 10 game development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-126">Hauptportal für Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="1b065-126">Windows Dev Center main portal</span></span></td>
        <td>[<span data-ttu-id="1b065-127">Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="1b065-127">Windows Dev Center</span></span>](https://dev.windows.com)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-128">Entwickeln von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-128">Developing Windows apps</span></span></td>
        <td>[<span data-ttu-id="1b065-129">Entwickeln von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-129">Develop Windows apps</span></span>](https://dev.windows.com/develop)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-130">Entwicklung von UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="1b065-130">Universal Windows Platform app development</span></span></td>
        <td>[<span data-ttu-id="1b065-131">Anleitungen für Windows 10-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-131">How-to guides for Windows 10 apps</span></span>](https://msdn.microsoft.com/library/windows/apps/mt244352)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-132">Anleitungen für UWP-Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-132">How-to guides for UWP games</span></span></td>
        <td>[<span data-ttu-id="1b065-133">Spiele und DirectX</span><span class="sxs-lookup"><span data-stu-id="1b065-133">Games and DirectX</span></span>](index.md) </td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-134">DirectX-Referenz und -Übersichten</span><span class="sxs-lookup"><span data-stu-id="1b065-134">DirectX reference and overviews</span></span></td>
        <td>[<span data-ttu-id="1b065-135">DirectX-Grafiken und -Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-135">DirectX Graphics and Gaming</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee663274)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-136">Azure für Gaming</span><span class="sxs-lookup"><span data-stu-id="1b065-136">Azure for gaming</span></span></td>
        <td>[<span data-ttu-id="1b065-137">Erstellen und Skalieren von Spielen mit Azure</span><span class="sxs-lookup"><span data-stu-id="1b065-137">Build and scale your games using Azure</span></span>](https://azure.microsoft.com/solutions/gaming/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-138">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="1b065-138">UWP on Xbox One</span></span></td>
        <td>[<span data-ttu-id="1b065-139">Erstellen von UWP-Apps auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="1b065-139">Building UWP apps on Xbox One</span></span>](https://msdn.microsoft.com/windows/uwp/xbox-apps/index)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-140">UWP auf HoloLens</span><span class="sxs-lookup"><span data-stu-id="1b065-140">UWP on HoloLens</span></span></td>
        <td>[<span data-ttu-id="1b065-141">Erstellen von UWP-Apps auf HoloLens</span><span class="sxs-lookup"><span data-stu-id="1b065-141">Building UWP apps on HoloLens</span></span>](https://developer.microsoft.com/windows/mixed-reality/development_overview)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-142">Xbox Live-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="1b065-142">Xbox Live documentation</span></span></td>
        <td>[<span data-ttu-id="1b065-143">Xbox Live – Entwicklerhandbuch</span><span class="sxs-lookup"><span data-stu-id="1b065-143">Xbox Live developer guide</span></span>](../xbox-live/index.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-144">Xbox One-Entwicklerdokumentation (GDN)</span><span class="sxs-lookup"><span data-stu-id="1b065-144">Xbox One developer documentation (GDN)</span></span></td>
        <td>[<span data-ttu-id="1b065-145">XboxOneXDK-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="1b065-145">Xbox One XDK documentation</span></span>](https://developer.xboxlive.com/en-us/platform/development/documentation/Pages/home.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-146">XboxOne-Whitepapers für Entwickler (GDN)</span><span class="sxs-lookup"><span data-stu-id="1b065-146">Xbox One developer whitepapers (GDN)</span></span></td>
        <td>[<span data-ttu-id="1b065-147">Whitepapers</span><span class="sxs-lookup"><span data-stu-id="1b065-147">White Papers</span></span>](https://developer.xboxlive.com/en-us/platform/development/education/Pages/WhitePapers.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-148">Interaktive Mixer-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="1b065-148">Mixer Interactive documentation</span></span></td>
        <td>[<span data-ttu-id="1b065-149">Fügen Sie Interaktivität zu Ihrem Spiel hinzu</span><span class="sxs-lookup"><span data-stu-id="1b065-149">Add interactivity to your game</span></span>](https://dev.mixer.com/reference/interactive/index.html)</td>
    </tr>        
</table>

### <a name="windows-dev-center"></a><span data-ttu-id="1b065-150">Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="1b065-150">Windows Dev Center</span></span>

<span data-ttu-id="1b065-151">Der Prozess für die Veröffentlichung Ihres Windows-Spiels beginnt mit der Registrierung eines Entwicklerkontos bei Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="1b065-151">Registering a developer account on the Windows Dev Center is the first step towards publishing your Windows game.</span></span> <span data-ttu-id="1b065-152">Mit einem Entwicklerkonto können Sie den Namen Ihres Spiels reservieren und kostenlose oder kostenpflichtige Spiele für alle Windows-Geräte an den Windows Store übermitteln.</span><span class="sxs-lookup"><span data-stu-id="1b065-152">A developer account lets you reserve your game's name and submit free or paid games to the Windows Store for all Windows devices.</span></span> <span data-ttu-id="1b065-153">Sie können Ihr Spiel und Ihre spielinternen Produkte verwalten, ausführliche Analysen abrufen und Dienste aktivieren, die Spieler auf der ganzen Welt begeistern.</span><span class="sxs-lookup"><span data-stu-id="1b065-153">Use your developer account to manage your game and in-game products, get detailed analytics, and enable services that create great experiences for your players around the world.</span></span> 

<span data-ttu-id="1b065-154">Microsoft bietet ebenfalls mehrere Entwicklerprogramme an, die Sie bei der Entwicklung und Veröffentlichung von Windows-Spielen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="1b065-154">Microsoft also offers several developer programs to help you develop and publish Windows games.</span></span> <span data-ttu-id="1b065-155">Wir empfehlen, vor dem Registrieren für ein Dev Center-Konto zu überprüfen, ob diese für Sie geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="1b065-155">We recommend seeing if any are right for you before registering for a Dev Center account.</span></span> <span data-ttu-id="1b065-156">Weitere Informationen finden Sie unter [Entwicklerprogramme](#developer-programs)</span><span class="sxs-lookup"><span data-stu-id="1b065-156">For more info, go to [Developer programs](#developer-programs)</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-157">Entwicklerkonto registrieren</span><span class="sxs-lookup"><span data-stu-id="1b065-157">Register a developer account</span></span></td>
        <td>[<span data-ttu-id="1b065-158">Bereit für die Registrierung?</span><span class="sxs-lookup"><span data-stu-id="1b065-158">Ready to sign up?</span></span>](https://msdn.microsoft.com/library/windows/apps/bg124287)</td>
    </tr> 
</table>

### <a name="developer-programs"></a><span data-ttu-id="1b065-159">Entwicklerprogramme</span><span class="sxs-lookup"><span data-stu-id="1b065-159">Developer programs</span></span>

<span data-ttu-id="1b065-160">Microsoft bietet mehrere Entwicklerprogramme an, die Sie bei der Entwicklung und Veröffentlichung von Windows-Spielen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="1b065-160">Microsoft offers several developer programs to help you develop and publish Windows games.</span></span> <span data-ttu-id="1b065-161">Erwägen Sie, an einem Entwicklerprogramm teilzunehmen, wenn Sie Spiele für Xbox One entwickeln möchten und Xbox Live-Features in Ihrem Spiel integrieren möchten.</span><span class="sxs-lookup"><span data-stu-id="1b065-161">Consider joining a developer program if you want to develop games for Xbox One and integrate Xbox Live features in your game.</span></span> <span data-ttu-id="1b065-162">Wenn Sie ein Spiel im Windows Store veröffentlichen möchten, benötigen Sie ebenfalls ein Entwicklerkonto in Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="1b065-162">To publish a game in the Windows Store, you'll also need to create a developer account on Windows Dev Center.</span></span> 

#### <a name="idxbox"></a>ID@Xbox

<span data-ttu-id="1b065-163">Das ID@Xbox-Programm unterstützt qualifizierte Spieleentwickler bei der eigenständigen Veröffentlichung für Windows und Xbox One.</span><span class="sxs-lookup"><span data-stu-id="1b065-163">The ID@Xbox program helps qualified game developers self-publish on Windows and Xbox One.</span></span> <span data-ttu-id="1b065-164">Wenn Sie für Xbox One entwickeln oder Ihr Windows10-Spiel mit XboxLive-Features wie Gamerscore, Erfolgen und Ranglisten versehen möchten, registrieren Sie sich bei ID@Xbox.</span><span class="sxs-lookup"><span data-stu-id="1b065-164">If you want to develop for Xbox One, or add Xbox Live features like Gamerscore, achievements, and leaderboards to your Windows 10 game, sign up with ID@Xbox.</span></span> <span data-ttu-id="1b065-165">Als ID@Xbox-Entwickler erhalten Sie Zugriff auf Tools und Supportleistungen, mit denen Sie Ihrer Kreativität freien Lauf lassen und Ihren Erfolg maximieren können.</span><span class="sxs-lookup"><span data-stu-id="1b065-165">Become an ID@Xbox developer to get the tools and support you need to unleash your creativity and maximize your success.</span></span> <span data-ttu-id="1b065-166">Es wird empfohlen, die Sie sich zuerst an ID@Xbox wenden, bevor Sie ein Entwicklerkonto im Windows Dev Center registrieren.</span><span class="sxs-lookup"><span data-stu-id="1b065-166">We recommend that you apply to ID@Xbox first before registering for a developer account on Windows Dev Center.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-167">ID@Xbox Entwicklerprogramm</span><span class="sxs-lookup"><span data-stu-id="1b065-167">ID@Xbox developer program</span></span></td>
        <td>[<span data-ttu-id="1b065-168">Unabhängiges Entwicklerprogramm für Xbox One</span><span class="sxs-lookup"><span data-stu-id="1b065-168">Independent Developer Program for Xbox One</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=526271)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-169">ID@Xbox Verbraucherwebsite</span><span class="sxs-lookup"><span data-stu-id="1b065-169">ID@Xbox consumer site</span></span></td>
        <td>[ID@Xbox](http://www.idatxbox.com/)</td>
    </tr>
</table>

#### <a name="xbox-live-creators-program"></a><span data-ttu-id="1b065-170">Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="1b065-170">Xbox Live Creators Program</span></span>

<span data-ttu-id="1b065-171">Mit dem Xbox Live Creators-Programm kann jeder Xbox Live in seine Titel integrieren und sie auf Xbox One und Windows 10 veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="1b065-171">The Xbox Live Creators Program allows anyone to integrate Xbox Live into their title and publish to Xbox One and Windows 10.</span></span> <span data-ttu-id="1b065-172">Um mit der Entwicklung über das Xbox Live Creators-Programm zu beginnen, melden Sie sich heute noch an.</span><span class="sxs-lookup"><span data-stu-id="1b065-172">To start developing with the Xbox Live Creators Program, sign up today.</span></span>

<span data-ttu-id="1b065-173">Treten Sie dem [ID@Xbox](http://www.xbox.com/Developers/id) bei, wenn Sie Zugriff auf weitere Xbox Live-Funktionen wünschen, dedizierte Marketing- und Entwicklungsunterstützung benötigen oder im allgemeinen Xbox One-Store vertreten sein möchten.</span><span class="sxs-lookup"><span data-stu-id="1b065-173">If you want access to even more Xbox Live capabilities, dedicated marketing and development support, and the chance to be featured in the main Xbox One store, apply to the [ID@Xbox](http://www.xbox.com/Developers/id) program.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-174">Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="1b065-174">Xbox Live Creators Program</span></span></td>
        <td>[<span data-ttu-id="1b065-175">Integrieren von Xbox Live in Ihren Spieletitel</span><span class="sxs-lookup"><span data-stu-id="1b065-175">Integrate Xbox Live into your title</span></span>](https://developer.microsoft.com/games/xbox/xboxlive/creator)</td>
    </tr>
</table>

#### <a name="xbox-tools-and-middleware"></a><span data-ttu-id="1b065-176">Xbox-Tools und Middleware</span><span class="sxs-lookup"><span data-stu-id="1b065-176">Xbox tools and middleware</span></span>

<span data-ttu-id="1b065-177">Im Rahmen des Programms für Xbox-Tools und Middleware werden Xbox-Entwicklungskits für professionelle Entwickler von Spieletools und Middleware lizenziert.</span><span class="sxs-lookup"><span data-stu-id="1b065-177">The Xbox Tools and Middleware Program licenses Xbox development kits to professional developers of game tools and middleware.</span></span> <span data-ttu-id="1b065-178">Entwickler, die in das Programm aufgenommen werden, können ihre Xbox XDK-Technologien an andere lizenzierte Xbox-Entwickler weitergeben und vertreiben.</span><span class="sxs-lookup"><span data-stu-id="1b065-178">Developers accepted into the program can share and distribute their Xbox XDK technologies to other licensed Xbox developers.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-179">Programm für Tools und Middleware kontaktieren</span><span class="sxs-lookup"><span data-stu-id="1b065-179">Contact the tools and middleware program</span></span></td>
        <td><xboxtlsm@microsoft.com></td>
    </tr>
</table>


### <a name="game-samples"></a><span data-ttu-id="1b065-180">Beispielspiele</span><span class="sxs-lookup"><span data-stu-id="1b065-180">Game samples</span></span>

<span data-ttu-id="1b065-181">Für Windows 10-Spiele und -Apps stehen zahlreiche Beispiele zur Verfügung, die einen Eindruck von den Features von Windows 10-Spielen vermitteln und den Einstieg in die Spieleentwicklung erleichtern.</span><span class="sxs-lookup"><span data-stu-id="1b065-181">There are many Windows 10 game and app samples available to help you understand Windows 10 gaming features and get a quick start on game development.</span></span> <span data-ttu-id="1b065-182">Es werden regelmäßig weitere Beispiele entwickelt und veröffentlicht. Schauen Sie daher immer mal wieder bei den Beispielportalen vorbei.</span><span class="sxs-lookup"><span data-stu-id="1b065-182">More samples are developed and published regularly, so don't forget to occasionally check back at sample portals to see what's new.</span></span> <span data-ttu-id="1b065-183">Darüber hinaus können Sie GitHub-Repositorys [überwachen](https://help.github.com/articles/watching-repositories/), um über Änderungen und Ergänzungen informiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="1b065-183">You can also [watch](https://help.github.com/articles/watching-repositories/) GitHub repos to be notified of changes and additions.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-184">Beispiele für Universelle Windows-Plattform-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-184">Universal Windows Platform app samples</span></span></td>
        <td>[<span data-ttu-id="1b065-185">Windows-universal-samples</span><span class="sxs-lookup"><span data-stu-id="1b065-185">Windows-universal-samples</span></span>](https://github.com/Microsoft/Windows-universal-samples)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-186">Xbox Advanced Technology Group – öffentliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="1b065-186">Xbox Advanced Technology Group public samples</span></span></td>
        <td>[<span data-ttu-id="1b065-187">Xbox-ATG-Beispiele</span><span class="sxs-lookup"><span data-stu-id="1b065-187">Xbox-ATG-Samples</span></span>](https://github.com/Microsoft/Xbox-ATG-Samples)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-188">Grafikbeispiele für Direct3D12</span><span class="sxs-lookup"><span data-stu-id="1b065-188">Direct3D 12 graphics samples</span></span></td>
        <td>[<span data-ttu-id="1b065-189">DirectX-Grafikbeispiele</span><span class="sxs-lookup"><span data-stu-id="1b065-189">DirectX-Graphics-Samples</span></span>](https://github.com/Microsoft/DirectX-Graphics-Samples)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-190">Grafikbeispiele für Direct3D11</span><span class="sxs-lookup"><span data-stu-id="1b065-190">Direct3D 11 graphics samples</span></span></td>
        <td>[<span data-ttu-id="1b065-191">directx-sdk-samples</span><span class="sxs-lookup"><span data-stu-id="1b065-191">directx-sdk-samples</span></span>](https://github.com/walbourn/directx-sdk-samples)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-192">Beispiel für ein First-Person-Spiel mit Direct3D11</span><span class="sxs-lookup"><span data-stu-id="1b065-192">Direct3D 11 first-person game sample</span></span></td>
        <td>[<span data-ttu-id="1b065-193">Erstellen eines einfachen UWP-Spiels mit DirectX</span><span class="sxs-lookup"><span data-stu-id="1b065-193">Create a simple UWP game with DirectX</span></span>](tutorial--create-your-first-metro-style-directx-game.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-194">Beispiel für benutzerdefinierte Direct2D-Bildeffekte</span><span class="sxs-lookup"><span data-stu-id="1b065-194">Direct2D custom image effects sample</span></span></td>
        <td>[<span data-ttu-id="1b065-195">D2DCustomEffects</span><span class="sxs-lookup"><span data-stu-id="1b065-195">D2DCustomEffects</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620531)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-196">Beispiel für ein Direct2D-Farbverlaufsgitter</span><span class="sxs-lookup"><span data-stu-id="1b065-196">Direct2D gradient mesh sample</span></span></td>
        <td>[<span data-ttu-id="1b065-197">D2DGradientMesh</span><span class="sxs-lookup"><span data-stu-id="1b065-197">D2DGradientMesh</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620532)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-198">Beispiel für eine Direct2D-Fotoanpassung</span><span class="sxs-lookup"><span data-stu-id="1b065-198">Direct2D photo adjustment sample</span></span></td>
        <td>[<span data-ttu-id="1b065-199">D2DPhotoAdjustment</span><span class="sxs-lookup"><span data-stu-id="1b065-199">D2DPhotoAdjustment</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620533)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-200">Beispiele für XboxOne-Spiele (GDN)</span><span class="sxs-lookup"><span data-stu-id="1b065-200">Xbox One game samples (GDN)</span></span></td>
        <td>[<span data-ttu-id="1b065-201">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1b065-201">Samples</span></span>](https://developer.xboxlive.com/en-us/platform/development/education/Pages/Samples.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-202">Beispiele für Windows8-Spiele (MSDN Code Gallery)</span><span class="sxs-lookup"><span data-stu-id="1b065-202">Windows 8 game samples (MSDN Code Gallery)</span></span></td>
        <td>[<span data-ttu-id="1b065-203">Beispiele für WindowsStore-Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-203">Windows Store game samples</span></span>](https://code.msdn.microsoft.com/windowsapps/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=game&f%5B1%5D.Type=Contributors&f%5B1%5D.Value=Microsoft&f%5B1%5D.Text=Microsoft)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-204">Beispiel für ein Spiel mit JavaScript und HTML5</span><span class="sxs-lookup"><span data-stu-id="1b065-204">JavaScript and HTML5 game sample</span></span></td>
        <td>[<span data-ttu-id="1b065-205">Beispiel für ein Spiel mit JavaScript, HTML5 und Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="1b065-205">JavaScript and HTML5 touch game sample</span></span>](https://code.msdn.microsoft.com/windowsapps/JavaScript-and-HTML5-touch-d96f6031)</td>
    </tr>      
</table>


### <a name="developer-forums"></a><span data-ttu-id="1b065-206">Entwicklerforen</span><span class="sxs-lookup"><span data-stu-id="1b065-206">Developer forums</span></span>

<span data-ttu-id="1b065-207">In Entwicklerforen können Entwickler Fragen zur Spieleentwicklung stellen und beantworten und sich mit anderen Spieleentwicklern austauschen.</span><span class="sxs-lookup"><span data-stu-id="1b065-207">Developer forums are a great place to ask and answer game development questions and connect with the game development community.</span></span> <span data-ttu-id="1b065-208">Darüber hinaus halten Foren häufig Lösungen für komplizierte Probleme bereit, die Entwickler bereits bewältigt haben.</span><span class="sxs-lookup"><span data-stu-id="1b065-208">Forums can also be fantastic resources for finding existing answers to difficult issues that developers have faced and solved in the past.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-209">Windows-Apps-Entwicklerforen</span><span class="sxs-lookup"><span data-stu-id="1b065-209">Windows apps developer forums</span></span></td>
        <td>[<span data-ttu-id="1b065-210">Foren für Windows Store und Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-210">Windows store and apps forums</span></span>](https://social.msdn.microsoft.com/Forums/en-us/home?category=windowsapps)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-211">Entwicklerforum für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-211">UWP apps developer forum</span></span></td>
        <td>[<span data-ttu-id="1b065-212">Entwicklung von UWP-Apps (Apps für die Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="1b065-212">Developing Universal Windows Platform apps</span></span>](https://social.msdn.microsoft.com/Forums/en-us/home?forum=wpdevelop)</td>
    </tr>

    <tr>
        <td><span data-ttu-id="1b065-213">Entwicklerforen für Desktopanwendungen</span><span class="sxs-lookup"><span data-stu-id="1b065-213">Desktop applications developer forums</span></span></td>
        <td>[<span data-ttu-id="1b065-214">Foren für Windows-Desktopanwendungen</span><span class="sxs-lookup"><span data-stu-id="1b065-214">Windows desktop applications forums</span></span>](https://social.msdn.microsoft.com/Forums/en-us/home?category=windowsdesktopdev)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-215">Windows Store-Spiele mit DirectX (archivierte Forenbeiträge)</span><span class="sxs-lookup"><span data-stu-id="1b065-215">DirectX Windows Store games (archived forum posts)</span></span></td>
        <td>[<span data-ttu-id="1b065-216">Erstellen von WindowsStore-Spielen mit DirectX (archiviert)</span><span class="sxs-lookup"><span data-stu-id="1b065-216">Building Windows Store games with DirectX (archived)</span></span>](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=wingameswithdirectx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-217">Windows10-Entwicklerforen für verwaltete Partner</span><span class="sxs-lookup"><span data-stu-id="1b065-217">Windows 10 managed partner developer forums</span></span></td>
        <td>[<span data-ttu-id="1b065-218">Xbox-Entwicklerforen: Windows10</span><span class="sxs-lookup"><span data-stu-id="1b065-218">XBOX Developer Forums: Windows 10</span></span>](http://aka.ms/win10devforums)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-219">DirectX-Foren</span><span class="sxs-lookup"><span data-stu-id="1b065-219">DirectX forums</span></span></td>
        <td>[<span data-ttu-id="1b065-220">DirectX12-Forum</span><span class="sxs-lookup"><span data-stu-id="1b065-220">DirectX 12 forum</span></span>](http://forums.directxtech.com/index.php)</td>
    </tr>
</table>


### <a name="developer-blogs"></a><span data-ttu-id="1b065-221">Entwicklerblogs</span><span class="sxs-lookup"><span data-stu-id="1b065-221">Developer blogs</span></span>

<span data-ttu-id="1b065-222">Entwicklerblogs sind eine weitere praktische Ressource für topaktuelle Informationen zur Spieleentwicklung.</span><span class="sxs-lookup"><span data-stu-id="1b065-222">Developer blogs are another great resource for the latest information about game development.</span></span> <span data-ttu-id="1b065-223">Hier finden Sie Beiträge zu neuen Features, Implementierungsdetails, bewährte Methoden, Hintergrundinformationen zur Architektur und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="1b065-223">You'll find posts about new features, implementation details, best practices, architecture background, and more.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-224">Blog „Building Apps for Windows“</span><span class="sxs-lookup"><span data-stu-id="1b065-224">Building apps for Windows blog</span></span></td>
        <td>[<span data-ttu-id="1b065-225">Building Apps for Windows</span><span class="sxs-lookup"><span data-stu-id="1b065-225">Building Apps for Windows</span></span>](http://blogs.windows.com/buildingapps/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-226">Windows10 (Blogbeiträge)</span><span class="sxs-lookup"><span data-stu-id="1b065-226">Windows 10 (blog posts)</span></span></td>
        <td>[<span data-ttu-id="1b065-227">Beiträge in Windows10</span><span class="sxs-lookup"><span data-stu-id="1b065-227">Posts in Windows 10</span></span>](http://blogs.windows.com/blog/tag/windows-10/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-228">Blog des VisualStudio-Entwicklerteams</span><span class="sxs-lookup"><span data-stu-id="1b065-228">Visual Studio engineering team blog</span></span></td>
        <td>[<span data-ttu-id="1b065-229">The Visual Studio Blog</span><span class="sxs-lookup"><span data-stu-id="1b065-229">The Visual Studio Blog</span></span>](http://blogs.msdn.com/b/visualstudio/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-230">Blogs zu VisualStudio-Entwicklertools</span><span class="sxs-lookup"><span data-stu-id="1b065-230">Visual Studio developer tools blogs</span></span></td>
        <td>[<span data-ttu-id="1b065-231">Developer Tools Blogs</span><span class="sxs-lookup"><span data-stu-id="1b065-231">Developer Tools Blogs</span></span>](http://blogs.msdn.com/b/developer-tools/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-232">Somasegars-Blog zu Entwicklertools</span><span class="sxs-lookup"><span data-stu-id="1b065-232">Somasegar's developer tools blog</span></span></td>
        <td>[<span data-ttu-id="1b065-233">Somasegar’s blog</span><span class="sxs-lookup"><span data-stu-id="1b065-233">Somasegar’s blog</span></span>](http://blogs.msdn.com/b/somasegar/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-234">DirectX-Entwicklerblog</span><span class="sxs-lookup"><span data-stu-id="1b065-234">DirectX developer blog</span></span></td>
        <td>[<span data-ttu-id="1b065-235">DirectX Developer Blog</span><span class="sxs-lookup"><span data-stu-id="1b065-235">DirectX Developer blog</span></span>](http://blogs.msdn.com/b/directx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-236">Einführung in DirectX12 (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="1b065-236">DirectX 12 introduction (blog post)</span></span></td>
        <td>[<span data-ttu-id="1b065-237">DirectX12</span><span class="sxs-lookup"><span data-stu-id="1b065-237">DirectX 12</span></span>](http://blogs.msdn.com/b/directx/archive/2014/03/20/directx-12.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-238">Teamblog zu VisualC++-Tools</span><span class="sxs-lookup"><span data-stu-id="1b065-238">Visual C++ tools team blog</span></span></td>
        <td>[<span data-ttu-id="1b065-239">Teamblog zu Visual C++</span><span class="sxs-lookup"><span data-stu-id="1b065-239">Visual C++ team blog</span></span>](http://blogs.msdn.com/b/vcblog/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-240">Blog des PIX-Teams</span><span class="sxs-lookup"><span data-stu-id="1b065-240">PIX team blog</span></span></td>
        <td>[<span data-ttu-id="1b065-241">Leistungsoptimierung und -Debuggen von DirectX12-Spielen für Windows und Xbox</span><span class="sxs-lookup"><span data-stu-id="1b065-241">Performance tuning and debugging for DirectX 12 games on Windows and Xbox</span></span>](https://blogs.msdn.microsoft.com/pix/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-242">Universelle Windows-App – Blog des Bereitstellungsteams</span><span class="sxs-lookup"><span data-stu-id="1b065-242">Universal Windows App Deployment team blog</span></span></td>
        <td>[<span data-ttu-id="1b065-243">Erstellen und Bereitstellen von UWP-Apps – Teamblog</span><span class="sxs-lookup"><span data-stu-id="1b065-243">Build and deploy UWP apps team blog</span></span>](https://blogs.msdn.microsoft.com/appinstaller/)</td>
    </tr>
</table>
 

## <a name="concept-and-planning"></a><span data-ttu-id="1b065-244">Konzept und Planung</span><span class="sxs-lookup"><span data-stu-id="1b065-244">Concept and planning</span></span>


<span data-ttu-id="1b065-245">In der Konzeptionierungs- und Planungsphase entscheiden Sie, welches Spiel Sie entwickeln möchten und mit welchen Tools und Technologien Sie es zum Leben erwecken.</span><span class="sxs-lookup"><span data-stu-id="1b065-245">In the concept and planning stage, you're deciding what your game is going to be like and the technologies and tools you'll use to bring it to life.</span></span>

### <a name="overview-of-game-development-technologies"></a><span data-ttu-id="1b065-246">Übersicht über Technologien für die Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="1b065-246">Overview of game development technologies</span></span>

<span data-ttu-id="1b065-247">Zu Beginn der Entwicklung eines UWP-Spiels haben Sie die Wahl zwischen verschiedenen Optionen für Grafik, Eingabe, Audio, Netzwerk, Hilfsprogramme und Bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="1b065-247">When you start developing a game for the UWP you have multiple options available for graphics, input, audio, networking, utilities, and libraries.</span></span>

<span data-ttu-id="1b065-248">Vielleicht haben Sie ja bereits entschieden, welche Technologien Sie in Ihrem Spiel verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="1b065-248">If you've already decided on all the technologies you'll be using in your game, great!</span></span> <span data-ttu-id="1b065-249">Andernfalls finden Sie im Handbuch [Spieletechnologien für UWP-Apps](game-development-platform-guide.md) eine hervorragende Übersicht über viele der verfügbaren Technologien. Es wird nachdrücklich empfohlen, dieses Handbuch zu lesen, um mehr über die Optionen und ihre Kombinationsmöglichkeiten zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="1b065-249">If not, the [Game technologies for UWP apps](game-development-platform-guide.md) guide is an excellent overview of many of the technologies available, and is highly recommended reading to help you understand the options and how they fit together.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-250">Überblick über UWP-Spieletechnologien</span><span class="sxs-lookup"><span data-stu-id="1b065-250">Survey of UWP game technologies</span></span></td>
        <td>[<span data-ttu-id="1b065-251">Spieletechnologien für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-251">Game technologies for UWP apps</span></span>](game-development-platform-guide.md)</td>
    </tr>
</table>
 

<span data-ttu-id="1b065-252">Diese drei GDC2015-Videos vermitteln einen guten Überblick über die Entwicklung von Windows10-Spielen und das Spielerlebnis unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="1b065-252">These three GDC 2015 videos give a good overview of Windows 10 game development and the Windows 10 gaming experience.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-253">Übersicht über die Entwicklung von Windows10-Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-253">Overview of Windows 10 game development (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-254">Entwickeln von Spielen für Windows10</span><span class="sxs-lookup"><span data-stu-id="1b065-254">Developing Games for Windows 10</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/Developing-Games-for-Windows-10)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-255">Spielerlebnis unter Windows10 (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-255">Windows 10 gaming experience (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-256">Spielerfahrung von Endbenutzern unter Windows10</span><span class="sxs-lookup"><span data-stu-id="1b065-256">Gaming Consumer Experience on Windows 10</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/Gaming-Consumer-Experience-on-Windows-10)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-257">Übergreifendes Spielen im gesamten Microsoft-Ökosystem (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-257">Gaming across the Microsoft ecosystem (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-258">Die Zukunft des Spielens im gesamten Microsoft-Ökosystem</span><span class="sxs-lookup"><span data-stu-id="1b065-258">The Future of Gaming Across the Microsoft Ecosystem</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/The-Future-of-Gaming-Across-the-Microsoft-Ecosystem)</td>
    </tr>
</table>

### <a name="game-planning"></a><span data-ttu-id="1b065-259">Planen von Spielen</span><span class="sxs-lookup"><span data-stu-id="1b065-259">Game planning</span></span>

<span data-ttu-id="1b065-260">Im Folgenden finden Sie einige Konzept- und Planungsthemen, die Ihnen einen Überblick über das geben, was Sie bei der Planung Ihres Spiels berücksichtigen sollten.</span><span class="sxs-lookup"><span data-stu-id="1b065-260">These are some high level concept and planning topics to consider when planning for your game.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-261">Erstellen barrierefreier Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-261">Make your game accessible</span></span></td>
        <td>[<span data-ttu-id="1b065-262">Barrierefreiheit von Spielen</span><span class="sxs-lookup"><span data-stu-id="1b065-262">Accessibility for games</span></span>](https://msdn.microsoft.com/windows/uwp/gaming/accessibility-for-games)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-263">Erstellen von Spielen mit der Cloud</span><span class="sxs-lookup"><span data-stu-id="1b065-263">Build games using cloud</span></span></td>
        <td>[<span data-ttu-id="1b065-264">Cloud für Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-264">Cloud for games</span></span>](https://msdn.microsoft.com/windows/uwp/gaming/cloud-for-games)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-265">Monetisierung eines Spiels</span><span class="sxs-lookup"><span data-stu-id="1b065-265">Monetize your game</span></span></td>
        <td>[<span data-ttu-id="1b065-266">Monetarisierung von Spielen</span><span class="sxs-lookup"><span data-stu-id="1b065-266">Monetization for games</span></span>](https://msdn.microsoft.com/windows/uwp/gaming/monetization-for-games)</td>
    </tr>
</table>



### <a name="choosing-your-graphics-technology-and-programming-language"></a><span data-ttu-id="1b065-267">Auswählen der Grafiktechnologie und Programmiersprache</span><span class="sxs-lookup"><span data-stu-id="1b065-267">Choosing your graphics technology and programming language</span></span>

<span data-ttu-id="1b065-268">Für Windows10-Spiele stehen verschiedene Programmiersprachen und Grafiktechnologien zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1b065-268">There are several programming languages and graphics technologies available for use in Windows 10 games.</span></span> <span data-ttu-id="1b065-269">Der jeweilige Ansatz richtet sich nach der Art des Spiels, das Sie entwickeln, der Erfahrung und den Vorlieben Ihres Entwicklungsstudios und den bestimmten Funktionsanforderungen Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="1b065-269">The path you take depends on the type of game you’re developing, the experience and preferences of your development studio, and specific feature requirements of your game.</span></span> <span data-ttu-id="1b065-270">Möchten Sie C#, C++ oder JavaScript verwenden?</span><span class="sxs-lookup"><span data-stu-id="1b065-270">Will you use C#, C++, or JavaScript?</span></span> <span data-ttu-id="1b065-271">DirectX, XAML oder HTML5?</span><span class="sxs-lookup"><span data-stu-id="1b065-271">DirectX, XAML, or HTML5?</span></span>

#### <a name="directx"></a><span data-ttu-id="1b065-272">DirectX</span><span class="sxs-lookup"><span data-stu-id="1b065-272">DirectX</span></span>

<span data-ttu-id="1b065-273">Microsoft DirectX ist die richtige Wahl für 2D/3D-Grafik und Multimediaelemente.</span><span class="sxs-lookup"><span data-stu-id="1b065-273">Microsoft DirectX is the choice to make for the highest-performance 2D and 3D graphics and multimedia.</span></span> 

<span data-ttu-id="1b065-274">Direct3D 12 wird mit Windows 10 neu eingeführt, stellt die Leistung einer konsolenähnlichen API bereit und ist schneller und effizienter als je zuvor.</span><span class="sxs-lookup"><span data-stu-id="1b065-274">Direct3D 12, new in Windows 10, brings the power of a console-like API and is faster and more efficient than ever before.</span></span> <span data-ttu-id="1b065-275">Ihr Spiel kann in vollem Umfang von moderner Grafikhardware profitieren und mehr Objekte, aufwendigere Szenen und beeindruckendere Effekte enthalten.</span><span class="sxs-lookup"><span data-stu-id="1b065-275">Your game can fully utilize modern graphics hardware and feature more objects, richer scenes, and enhanced effects.</span></span> <span data-ttu-id="1b065-276">Direct3D12 bietet optimierte Grafiken für Windows10-PCs und Xbox One.</span><span class="sxs-lookup"><span data-stu-id="1b065-276">Direct3D 12 delivers optimized graphics on Windows 10 PCs and Xbox One.</span></span> <span data-ttu-id="1b065-277">Sie können weiterhin die vertraute Grafikpipeline von Direct3D11 verwenden und gleichzeitig von den neuen Rendering- und Optimierungsfeatures profitieren, die in Direct3D11.3 hinzugekommen sind.</span><span class="sxs-lookup"><span data-stu-id="1b065-277">If you want to use the familiar graphics pipeline of Direct3D 11, you’ll still benefit from the new rendering and optimization features added to Direct3D 11.3.</span></span> <span data-ttu-id="1b065-278">Und wenn Sie ein richtiger Windows-API-Entwickler für den Desktop mit Win32-Erfahrung sind, steht Ihnen unter Windows10 auch diese Option zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1b065-278">And, if you’re a tried-and-true desktop Windows API developer with roots in Win32, you’ll still have that option in Windows 10.</span></span>

<span data-ttu-id="1b065-279">Dank umfangreicher Features und einer umfassenden Plattformintegration lassen sich mit DirectX selbst anspruchsvollste Spiele realisieren.</span><span class="sxs-lookup"><span data-stu-id="1b065-279">The extensive features and deep platform integration of DirectX provide the power and performance needed by the most demanding games.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-280">Anleitungen für DirectX-Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-280">How-to guides for DirectX games</span></span></td>
        <td>[<span data-ttu-id="1b065-281">Spiele und DirectX</span><span class="sxs-lookup"><span data-stu-id="1b065-281">Games and DirectX</span></span>](index.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-282">Übersichten und Referenzen zu DirectX</span><span class="sxs-lookup"><span data-stu-id="1b065-282">DirectX overviews and reference</span></span></td>
        <td>[<span data-ttu-id="1b065-283">DirectX-Grafiken und -Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-283">DirectX Graphics and Gaming</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee663274)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-284">Direct3D12-Programmieranleitung und -referenz</span><span class="sxs-lookup"><span data-stu-id="1b065-284">Direct3D 12 programming guide and reference</span></span></td>
        <td>[<span data-ttu-id="1b065-285">Direct3D12-Grafiken</span><span class="sxs-lookup"><span data-stu-id="1b065-285">Direct3D 12 Graphics</span></span>](https://msdn.microsoft.com/library/windows/desktop/dn903821)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-286">Videos zu Grafiken und zur DirectX 12-Entwicklung (YouTube-Kanal)</span><span class="sxs-lookup"><span data-stu-id="1b065-286">Graphics and DirectX 12 development videos (YouTube channel)</span></span></td>
        <td>[<span data-ttu-id="1b065-287">Informationen zu Microsoft DirectX12 und Grafiken</span><span class="sxs-lookup"><span data-stu-id="1b065-287">Microsoft DirectX 12 and Graphics Education</span></span>](https://www.youtube.com/channel/UCiaX2B8XiXR70jaN7NK-FpA)</td>
    </tr>
</table>
 

#### <a name="xaml"></a><span data-ttu-id="1b065-288">XAML</span><span class="sxs-lookup"><span data-stu-id="1b065-288">XAML</span></span>

<span data-ttu-id="1b065-289">XAML ist eine benutzerfreundliche deklarative UI-Sprache mit nützlichen Features wie Animationen, Storyboards, Datenbindung, skalierbaren vektorbasierten Grafiken, dynamischer Größenänderung und Szenendiagrammen.</span><span class="sxs-lookup"><span data-stu-id="1b065-289">XAML is an easy-to-use declarative UI language with convenient features like animations, storyboards, data binding, scalable vector-based graphics, dynamic resizing, and scene graphs.</span></span> <span data-ttu-id="1b065-290">XAML eignet sich gut für Benutzeroberflächen, Menüs, Sprites und 2D-Grafiken von Spielen.</span><span class="sxs-lookup"><span data-stu-id="1b065-290">XAML works great for game UI, menus, sprites, and 2D graphics.</span></span> <span data-ttu-id="1b065-291">Zur Vereinfachung der UI-Layouterstellung ist XAML mit Entwurfs- und Entwicklungstools wie Expression Blend und Microsoft Visual Studio kompatibel.</span><span class="sxs-lookup"><span data-stu-id="1b065-291">To make UI layout easy, XAML is compatible with design and development tools like Expression Blend and Microsoft Visual Studio.</span></span> <span data-ttu-id="1b065-292">XAML wird häufig mit C# kombiniert, aber auch C++ ist eine gute Wahl, falls dies Ihre bevorzugte Programmiersprache ist oder Ihr Spiel hohe Ansprüche an die CPU stellt.</span><span class="sxs-lookup"><span data-stu-id="1b065-292">XAML is commonly used with C#, but C++ is also a good choice if that’s your preferred language or if your game has high CPU demands.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-293">XAML-Plattformübersicht</span><span class="sxs-lookup"><span data-stu-id="1b065-293">XAML platform overview</span></span></td>
        <td>[<span data-ttu-id="1b065-294">XAML-Plattform</span><span class="sxs-lookup"><span data-stu-id="1b065-294">XAML platform</span></span>](https://msdn.microsoft.com/library/windows/apps/mt228259)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-295">XAML-UI und -Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="1b065-295">XAML UI and controls</span></span></td>
        <td>[<span data-ttu-id="1b065-296">Steuerelemente, Layouts und Text</span><span class="sxs-lookup"><span data-stu-id="1b065-296">Controls, layouts, and text</span></span>](https://msdn.microsoft.com/library/windows/apps/mt228348)</td>
    </tr>
</table>
 

#### <a name="html-5"></a><span data-ttu-id="1b065-297">HTML5</span><span class="sxs-lookup"><span data-stu-id="1b065-297">HTML 5</span></span>

<span data-ttu-id="1b065-298">Die HyperText Markup Language (HTML) ist eine häufig verwendete Markup-Sprache für Benutzeroberflächen, die bei Webseiten, Apps und Rich-Clients zum Einsatz kommt.</span><span class="sxs-lookup"><span data-stu-id="1b065-298">HyperText Markup Language (HTML) is a common UI markup language used for web pages, apps, and rich clients.</span></span> <span data-ttu-id="1b065-299">Für Windows-Spiele kann HTML5 als Darstellungsschicht mit vollem Funktionsumfang genutzt werden. Dabei stehen die vertrauten Features von HTML, Zugriff auf die universelle Windows-Plattform und Unterstützung für moderne Webfeatures wie AppCache, Web-Worker, Canvas, Drag&Drop, asynchrone Programmierung und SVG zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1b065-299">Windows games can use HTML5 as a full-featured presentation layer with the familiar features of HTML, access to the Universal Windows Platform, and support for modern web features like AppCache, Web Workers, canvas, drag-and-drop, asynchronous programming, and SVG.</span></span> <span data-ttu-id="1b065-300">Im Hintergrund wird für das HTML-Rendering die leistungsstarke DirectX-Hardwarebeschleunigung genutzt, sodass Sie weiterhin in den Genuss der Leistungsvorteile von DirectX kommen, ohne zusätzlichen Code schreiben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="1b065-300">Behind the scenes, HTML rendering takes advantage of the power of DirectX hardware acceleration, so you can still get the performance benefits of DirectX without writing any extra code.</span></span> <span data-ttu-id="1b065-301">HTML5 ist eine gute Wahl, wenn Sie sich mit der Webentwicklung auskennen, ein Webspiel portieren oder Sprach- und Grafikebenen nutzen möchten, die unter Umständen leichter zugänglich als andere Optionen sind.</span><span class="sxs-lookup"><span data-stu-id="1b065-301">HTML5 is a good choice if you are proficient with web development, porting a web game, or want to use language and graphics layers that can be easier to approach than the other choices.</span></span> <span data-ttu-id="1b065-302">HTML5 wird zusammen mit JavaScript verwendet, kann aber auch mit Komponenten verknüpft werden, die mit C# oder C++/CX erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="1b065-302">HTML5 is used with JavaScript, but can also call into components created with C# or C++/CX.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-303">Informationen zu HTML5 und zum Dokumentobjektmodell</span><span class="sxs-lookup"><span data-stu-id="1b065-303">HTML5 and Document Object Model information</span></span></td>
        <td>[<span data-ttu-id="1b065-304">HTML- und DOM-Referenz</span><span class="sxs-lookup"><span data-stu-id="1b065-304">HTML and DOM reference</span></span>](https://msdn.microsoft.com/library/windows/apps/br212882.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-305">Die HTML5-Empfehlung des W3C</span><span class="sxs-lookup"><span data-stu-id="1b065-305">The HTML5 W3C Recommendation</span></span></td>
        <td>[<span data-ttu-id="1b065-306">HTML5</span><span class="sxs-lookup"><span data-stu-id="1b065-306">HTML5</span></span>](http://go.microsoft.com/fwlink/p/?linkid=221374)</td>
    </tr>
</table>
 

#### <a name="combining-presentation-technologies"></a><span data-ttu-id="1b065-307">Kombinieren von Darstellungstechnologien</span><span class="sxs-lookup"><span data-stu-id="1b065-307">Combining presentation technologies</span></span>

<span data-ttu-id="1b065-308">Die Microsoft DirectX Graphic Infrastructure (DXGI) bietet Interoperabilität und Kompatibilität mit mehreren Arten von Grafiktechnologien.</span><span class="sxs-lookup"><span data-stu-id="1b065-308">The Microsoft DirectX Graphics Infrastructure (DXGI) provides interop and compatibility across multiple graphics technologies.</span></span> <span data-ttu-id="1b065-309">Für Hochleistungsgrafiken können Sie XAML und DirectX kombinieren, indem Sie XAML für Menüs und andere einfache UI-Elemente und DirectX für das Rendern von komplexen 2D- und 3D-Szenen nutzen.</span><span class="sxs-lookup"><span data-stu-id="1b065-309">For high-performance graphics, you can combine XAML and DirectX, using XAML for menus and other simple UI, and DirectX for rendering complex 2D and 3D scenes.</span></span> <span data-ttu-id="1b065-310">DXGI sorgt auch für Kompatibilität zwischen Direct2D, Direct3D, DirectWrite, DirectCompute und der Microsoft Media Foundation.</span><span class="sxs-lookup"><span data-stu-id="1b065-310">DXGI also provides compatibility between Direct2D, Direct3D, DirectWrite, DirectCompute, and the Microsoft Media Foundation.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-311">Programmieranleitung und Referenz für die DirectX Graphic Infrastructure</span><span class="sxs-lookup"><span data-stu-id="1b065-311">DirectX Graphics Infrastructure programming guide and reference</span></span></td>
        <td>[<span data-ttu-id="1b065-312">DXGI</span><span class="sxs-lookup"><span data-stu-id="1b065-312">DXGI</span></span>](https://msdn.microsoft.com/library/windows/desktop/hh404534)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-313">Kombinieren von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="1b065-313">Combining DirectX and XAML</span></span></td>
        <td>[<span data-ttu-id="1b065-314">Interoperabilität von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="1b065-314">DirectX and XAML interop</span></span>](directx-and-xaml-interop.md)</td>
    </tr>
</table>
 

#### <a name="c"></a><span data-ttu-id="1b065-315">C++</span><span class="sxs-lookup"><span data-stu-id="1b065-315">C++</span></span>

<span data-ttu-id="1b065-316">C++/CX ist eine effiziente Hochleistungssprache und bietet eine erstklassige Mischung aus Geschwindigkeit, Kompatibilität und Plattformzugriff.</span><span class="sxs-lookup"><span data-stu-id="1b065-316">C++/CX is a high-performance, low overhead language that provides the powerful combination of speed, compatibility, and platform access.</span></span> <span data-ttu-id="1b065-317">C++/CX erleichtert Ihnen die Nutzung aller nützlichen Gaming-Features unter Windows10, z.B. DirectX und Xbox Live.</span><span class="sxs-lookup"><span data-stu-id="1b065-317">C++/CX makes it easy to use all of the great gaming features in Windows 10, including DirectX and Xbox Live.</span></span> <span data-ttu-id="1b065-318">Außerdem können Sie vorhandenen C++-Code und die dazugehörigen Bibliotheken verwenden.</span><span class="sxs-lookup"><span data-stu-id="1b065-318">You can also reuse existing C++ code and libraries.</span></span> <span data-ttu-id="1b065-319">Mit C++/CX wird schneller, systemeigener Code erstellt, bei dem kein Aufwand für die Garbage Collection anfällt. So kann Ihr Spiel mit einer hohen Leistung und einem geringen Stromverbrauch aufwarten und somit auch eine längere Akkulaufzeit ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="1b065-319">C++/CX creates fast, native code that doesn’t incur the overhead of garbage collection, so your game can have great performance and low power consumption, which leads to longer battery life.</span></span> <span data-ttu-id="1b065-320">Verwenden Sie C++/CX mit DirectX oder XAML, oder erstellen Sie ein Spiel mit einer Kombination aus beidem.</span><span class="sxs-lookup"><span data-stu-id="1b065-320">Use C++/CX with DirectX or XAML, or create a game that uses a combination of both.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-321">Referenz und Übersichten für C++/CX</span><span class="sxs-lookup"><span data-stu-id="1b065-321">C++/CX reference and overviews</span></span></td>
        <td>[<span data-ttu-id="1b065-322">Visual C++-Programmiersprachenreferenz (C++/CX)</span><span class="sxs-lookup"><span data-stu-id="1b065-322">Visual C++ Language Reference (C++/CX)</span></span>](https://msdn.microsoft.com/library/windows/apps/hh699871.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-323">Visual C++-Programmieranleitung und -Referenz</span><span class="sxs-lookup"><span data-stu-id="1b065-323">Visual C++ programming guide and reference</span></span></td>
        <td>[<span data-ttu-id="1b065-324">Visual C++ in Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="1b065-324">Visual C++ in Visual Studio 2015</span></span>](https://msdn.microsoft.com/library/60k1461a.aspx)</td>
    </tr>
</table>
 

#### <a name="c"></a><span data-ttu-id="1b065-325">C#</span><span class="sxs-lookup"><span data-stu-id="1b065-325">C#</span></span>

<span data-ttu-id="1b065-326">C# (sprich: „C sharp“) ist eine moderne, innovative Programmiersprache, die einfach, leistungsstark, typsicher und objektorientiert ist.</span><span class="sxs-lookup"><span data-stu-id="1b065-326">C# (pronounced "C sharp") is a modern, innovative language that is simple, powerful, type-safe, and object-oriented.</span></span> <span data-ttu-id="1b065-327">C# ermöglicht eine schnelle Entwicklung, während gleichzeitig die Vertrautheit und Ausdruckskraft von Sprachen im C-Stil gewahrt bleibt.</span><span class="sxs-lookup"><span data-stu-id="1b065-327">C# enables rapid development while retaining the familiarity and expressiveness of C-style languages.</span></span> <span data-ttu-id="1b065-328">Obwohl C# einfach zu verwenden ist, verfügt die Sprache über viele moderne Sprachfeatures wie Polymorphie, Delegate, Lambda-Elemente, Abschlüsse, Iteratormethoden, Kovarianz und LINQ-Ausdrücke (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="1b065-328">Though easy to use, C# has numerous advanced language features like polymorphism, delegates, lambdas, closures, iterator methods, covariance, and Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="1b065-329">C# ist eine ausgezeichnete Wahl, wenn Sie XAML verwenden möchten, schnell mit der Entwicklung Ihres Spiels beginnen möchten oder bereits über C#-Erfahrung verfügen.</span><span class="sxs-lookup"><span data-stu-id="1b065-329">C# is an excellent choice if you are targeting XAML, want to get a quick start developing your game, or have previous C# experience.</span></span> <span data-ttu-id="1b065-330">C# wird vorrangig mit XAML genutzt. Wenn Sie also DirectX verwenden möchten, entscheiden Sie sich besser für C++, oder schreiben Sie einen Teil des Spiels als C++-Komponente, die mit DirectX interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="1b065-330">C# is used primarily with XAML, so if you want to use DirectX, choose C++ instead, or write part of your game as a C++ component that interacts with DirectX.</span></span> <span data-ttu-id="1b065-331">Eine weitere Alternative wäre [Win2D](https://github.com/Microsoft/Win2D) – eine Direct2D-Grafikbibliothek im unmittelbaren Modus für C# und C++.</span><span class="sxs-lookup"><span data-stu-id="1b065-331">Or, consider [Win2D](https://github.com/Microsoft/Win2D), an immediate mode Direct2D graphics libary for C# and C++.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-332">C#-Programmieranleitung und -Referenz</span><span class="sxs-lookup"><span data-stu-id="1b065-332">C# programming guide and reference</span></span></td>
        <td>[<span data-ttu-id="1b065-333">C#-Programmiersprachenreferenz</span><span class="sxs-lookup"><span data-stu-id="1b065-333">C# language reference</span></span>](https://msdn.microsoft.com/library/kx37x362.aspx)</td>
    </tr>
</table>
 

#### <a name="javascript"></a><span data-ttu-id="1b065-334">JavaScript</span><span class="sxs-lookup"><span data-stu-id="1b065-334">JavaScript</span></span>

<span data-ttu-id="1b065-335">JavaScript ist eine dynamische Skriptsprache, die gerne für moderne Webanwendungen und Rich-Client-Anwendungen eingesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="1b065-335">JavaScript is a dynamic scripting language widely used for modern web and rich client applications.</span></span>

<span data-ttu-id="1b065-336">Bei Windows-JavaScript-Apps kann auf einfache und intuitive Weise auf die leistungsfähigen Features der universellen Windows-Plattform zugegriffen werden – in Form von Methoden und Eigenschaften objektorientierter JavaScript-Klassen.</span><span class="sxs-lookup"><span data-stu-id="1b065-336">Windows JavaScript apps can access the powerful features of the Universal Windows Platform in an easy, intuitive way—as methods and properties of object-oriented JavaScript classes.</span></span> <span data-ttu-id="1b065-337">JavaScript ist für Ihr Spiel eine gute Wahl, wenn Sie aus dem Bereich der Webentwicklung kommen, sich mit JavaScript bereits auskennen oder HTML5-, CSS-, WinJS- oder JavaScript-Bibliotheken verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="1b065-337">JavaScript is a good choice for your game if you’re coming from a web development environment, are already familiar with JavaScript, or want to use HTML5, CSS, WinJS, or JavaScript libraries.</span></span> <span data-ttu-id="1b065-338">Wenn Sie Ihre Entwicklung auf DirectX oder XAML ausrichten möchten, ist C# oder C++/CX die bessere Wahl.</span><span class="sxs-lookup"><span data-stu-id="1b065-338">If you’re targeting DirectX or XAML, choose C# or C++/CX instead.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-339">Referenz zu JavaScript und Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="1b065-339">JavaScript and Windows Runtime reference</span></span></td>
        <td>[<span data-ttu-id="1b065-340">JavaScript-Referenz</span><span class="sxs-lookup"><span data-stu-id="1b065-340">JavaScript reference</span></span>](https://msdn.microsoft.com/library/windows/apps/jj613794)</td>
    </tr>
</table>


#### <a name="use-windows-runtime-components-to-combine-languages"></a><span data-ttu-id="1b065-341">Kombinieren von Programmiersprachen mithilfe von Windows-Runtime-Komponenten</span><span class="sxs-lookup"><span data-stu-id="1b065-341">Use Windows Runtime Components to combine languages</span></span>

<span data-ttu-id="1b065-342">Mit der universellen Windows-Plattform lassen sich problemlos Komponenten in unterschiedlichen Programmiersprachen kombinieren.</span><span class="sxs-lookup"><span data-stu-id="1b065-342">With the Universal Windows Platform, it’s easy to combine components written in different languages.</span></span> <span data-ttu-id="1b065-343">Erstellen Sie Komponenten für Windows-Runtime in C++, C# oder Visual Basic, und nutzen Sie diese dann per JavaScript, C#, C++ oder Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1b065-343">Create Windows Runtime Components in C++, C#, or Visual Basic, and then call into them from JavaScript, C#, C++, or Visual Basic.</span></span> <span data-ttu-id="1b065-344">Dies ist eine hervorragende Möglichkeit, wenn Sie Teile des Spiels in der Sprache Ihrer Wahl programmieren möchten.</span><span class="sxs-lookup"><span data-stu-id="1b065-344">This is a great way to program portions of your game in the language of your choice.</span></span> <span data-ttu-id="1b065-345">Über Komponenten können Sie außerdem externe Bibliotheken nutzen, die nur in einer bestimmten Programmiersprache verfügbar sind, oder auch älteren Code, den Sie bereits geschrieben haben.</span><span class="sxs-lookup"><span data-stu-id="1b065-345">Components also let you consume external libraries that are only available in a particular language, as well as use legacy code you’ve already written.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-346">So wird's gemacht: Erstellen von Komponenten für die Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="1b065-346">How to create Windows Runtime Components</span></span></td>
        <td>[<span data-ttu-id="1b065-347">Erstellen von Windows-Runtime-Komponenten</span><span class="sxs-lookup"><span data-stu-id="1b065-347">Creating Windows Runtime Components</span></span>](https://docs.microsoft.com/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)</td>
    </tr>
</table>


### <a name="which-version-of-directx-should-your-game-use"></a><span data-ttu-id="1b065-348">Welche DirectX-Version sollte Ihr Spiel verwenden?</span><span class="sxs-lookup"><span data-stu-id="1b065-348">Which version of DirectX should your game use?</span></span>

<span data-ttu-id="1b065-349">Wenn Sie ein Spiel mit DirectX entwickeln, müssen Sie sich zwischen Microsoft Direct3D12 und Microsoft Direct3D11 entscheiden.</span><span class="sxs-lookup"><span data-stu-id="1b065-349">If you are choosing DirectX for your game, you'll need to decide which version to use: Microsoft Direct3D 12 or Microsoft Direct3D 11.</span></span>

<span data-ttu-id="1b065-350">Direct3D12 wird mit Windows10 neu eingeführt, stellt die Leistung einer konsolenähnlichen API bereit und ist schneller und effizienter als je zuvor.</span><span class="sxs-lookup"><span data-stu-id="1b065-350">Direct3D 12, new in Windows 10, brings the power of a console-like API and is faster and more efficient than ever before.</span></span> <span data-ttu-id="1b065-351">Ihr Spiel kann in vollem Umfang von moderner Grafikhardware profitieren und mehr Objekte, aufwendigere Szenen und beeindruckendere Effekte enthalten.</span><span class="sxs-lookup"><span data-stu-id="1b065-351">Your game can fully utilize modern graphics hardware and feature more objects, richer scenes, and enhanced effects.</span></span> <span data-ttu-id="1b065-352">Direct3D12 bietet optimierte Grafiken für Windows10-PCs und Xbox One.</span><span class="sxs-lookup"><span data-stu-id="1b065-352">Direct3D 12 delivers optimized graphics on Windows 10 PCs and Xbox One.</span></span> <span data-ttu-id="1b065-353">Da Direct3D12 auf einer sehr niedrigen Ebene ausgeführt wird, erhält ein erfahrenes Grafikentwicklungs- oder DirectX11-Entwicklungsteam alle notwendigen Steuerungsmöglichkeiten für die Maximierung der Grafikoptimierung.</span><span class="sxs-lookup"><span data-stu-id="1b065-353">Since Direct3D 12 works at a very low level, it is able to give an expert graphics development team or an experienced DirectX 11 development team all the control they need to maximize graphics optimization.</span></span>

<span data-ttu-id="1b065-354">Direct3D11.3 ist eine Grafik-API auf einem niedrigen Niveau, die das vertraute Direct3D-Programmiermodell verwendet und Ihnen einen größeren Teil der Komplexität abnimmt, die mit dem GPU-Rendering verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="1b065-354">Direct3D 11.3 is a low level graphics API that uses the familiar Direct3D programming model and handles for you more of the complexity involved in GPU rendering.</span></span> <span data-ttu-id="1b065-355">Sie wird auch von Windows10 und Xbox One unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1b065-355">It is also supported in Windows 10 and Xbox One.</span></span> <span data-ttu-id="1b065-356">Wenn Sie über ein vorhandenes Modul verfügen, das in Direct3D 11 geschrieben wurde, und noch nicht bereit sind, zu Direct3D12 zu wechseln, können Sie Direct3D11 auf 12 verwenden, um einige Leistungsverbesserungen zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="1b065-356">If you have an existing engine written in Direct3D 11, and you're not quite ready to make the jump to Direct3D 12, you can use Direct3D 11 on 12 to achieve some performance improvements.</span></span> <span data-ttu-id="1b065-357">Die Versionen ab 11.3 enthalten die neuen Rendering- und Optimierungsfeatures, die auch in Direct3D12 zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="1b065-357">Versions 11.3+ contain the new rendering and optimization features enabled also in Direct3D 12.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-358">Entscheidung zwischen Direct3D12 und Direct3D11</span><span class="sxs-lookup"><span data-stu-id="1b065-358">Choosing Direct3D 12 or Direct3D 11</span></span></td>
        <td>[<span data-ttu-id="1b065-359">Was ist Direct3D12?</span><span class="sxs-lookup"><span data-stu-id="1b065-359">What is Direct3D 12?</span></span>](https://msdn.microsoft.com/library/windows/desktop/dn899228)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-360">Übersicht über Direct3D11</span><span class="sxs-lookup"><span data-stu-id="1b065-360">Overview of Direct3D 11</span></span></td>
        <td>[<span data-ttu-id="1b065-361">Direct3D11-Grafik</span><span class="sxs-lookup"><span data-stu-id="1b065-361">Direct3D 11 Graphics</span></span>](https://msdn.microsoft.com/library/windows/desktop/ff476080)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-362">Übersicht über „Direct3D 11 on 12“</span><span class="sxs-lookup"><span data-stu-id="1b065-362">Overview of Direct3D 11 on 12</span></span></td>
        <td>[<span data-ttu-id="1b065-363">Direct3D 11 on 12</span><span class="sxs-lookup"><span data-stu-id="1b065-363">Direct3D 11 on 12</span></span>](https://msdn.microsoft.com/library/windows/desktop/dn913195)</td>
    </tr>
</table>


### <a name="bridges-game-engines-and-middleware"></a><span data-ttu-id="1b065-364">Brücken, Spielengines und Middleware</span><span class="sxs-lookup"><span data-stu-id="1b065-364">Bridges, game engines, and middleware</span></span>

<span data-ttu-id="1b065-365">Mithilfe von Brücken, Spielengines und Middleware können Sie je nach Spiel unter Umständen die Entwicklung und das Testing beschleunigen und den damit verbundenen Ressourcenaufwand verringern.</span><span class="sxs-lookup"><span data-stu-id="1b065-365">Depending on the needs of your game, using bridges, game engines, or middleware can save development and testing time and resources.</span></span> <span data-ttu-id="1b065-366">Anhand der folgenden Übersicht und Ressourcen für Brücken, Spielengines und Middleware können Sie ermitteln, ob etwas für Sie dabei ist.</span><span class="sxs-lookup"><span data-stu-id="1b065-366">Here are some overview and resources for bridges, game engines, and middleware to help you decide if any are right for you.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-367">Spieleentwicklung mit Middleware (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-367">Game Development with Middleware (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-368">Beschleunigen der Windows Store-Spieleentwicklung mit Middleware</span><span class="sxs-lookup"><span data-stu-id="1b065-368">Accelerating Windows Store Game Development with Middleware</span></span>](https://channel9.msdn.com/Events/Build/2013/3-187)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-369">Einführung in Middleware für Spiele (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="1b065-369">Introduction to game middleware (blog post)</span></span></td>
        <td>[<span data-ttu-id="1b065-370">Was ist Middleware für die Spieleentwicklung?</span><span class="sxs-lookup"><span data-stu-id="1b065-370">Game Development Middleware - What is it?</span></span> <span data-ttu-id="1b065-371">Brauche ich das?</span><span class="sxs-lookup"><span data-stu-id="1b065-371">Do I need it?</span></span>](http://blogs.msdn.com/b/wsdevsol/archive/2014/05/02/game-development-middleware-what-is-it-do-i-need-it.aspx)</td>
    </tr>
</table>
 

#### <a name="universal-windows-platform-bridges"></a><span data-ttu-id="1b065-372">Brücken für die universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="1b065-372">Universal Windows Platform Bridges</span></span>

<span data-ttu-id="1b065-373">Bei Brücken für die universelle Windows-Plattform handelt es sich um Technologien für die UWP-Portierung Ihrer vorhandenen Apps oder Spiele.</span><span class="sxs-lookup"><span data-stu-id="1b065-373">Universal Windows Platform Bridges are technologies that bring your existing app or game over to the UWP.</span></span> <span data-ttu-id="1b065-374">Brücken eignen sich sehr gut für den schnellen Einstieg in die Entwicklung von UWP-Spielen.</span><span class="sxs-lookup"><span data-stu-id="1b065-374">Bridges are a great way to get a quick start on UWP game development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-375">UWP Brücken</span><span class="sxs-lookup"><span data-stu-id="1b065-375">UWP bridges</span></span></td>
        <td>[<span data-ttu-id="1b065-376">Portieren Ihres Codes für Windows</span><span class="sxs-lookup"><span data-stu-id="1b065-376">Bring your code to Windows</span></span>](https://dev.windows.com/bridges/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-377">Windows-Brücke für iOS</span><span class="sxs-lookup"><span data-stu-id="1b065-377">Windows Bridge for iOS</span></span></td>
        <td>[<span data-ttu-id="1b065-378">Portieren Ihrer iOS-Apps für Windows</span><span class="sxs-lookup"><span data-stu-id="1b065-378">Bring your iOS apps to Windows</span></span>](https://dev.windows.com/bridges/ios)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-379">Windows-Brücke für Desktop-Anwendungen (.NET und Win32)</span><span class="sxs-lookup"><span data-stu-id="1b065-379">Windows Bridge for desktop applications (.NET and Win32)</span></span></td>
        <td>[<span data-ttu-id="1b065-380">Konvertieren Ihrer Desktopanwendung in eine UWP-App</span><span class="sxs-lookup"><span data-stu-id="1b065-380">Convert your desktop application to a UWP app</span></span>](https://developer.microsoft.com/windows/bridges/desktop)</td>
    </tr>
</table>
 

#### <a name="unity"></a><span data-ttu-id="1b065-381">Unity</span><span class="sxs-lookup"><span data-stu-id="1b065-381">Unity</span></span>

<span data-ttu-id="1b065-382">Unity5 stellt die nächste Generation der preisgekrönten Entwicklungsplattform zur Erstellung von 2D- und 3D-Spielen und interaktiven Benutzeroberflächen dar.</span><span class="sxs-lookup"><span data-stu-id="1b065-382">Unity 5 is the next generation of the award-winning development platform for creating 2D and 3D games and interactive experiences.</span></span> <span data-ttu-id="1b065-383">Unity 5 zeichnet sich durch neue künstlerische Möglichkeiten, verbesserte Grafikfunktionen und eine höhere Effizienz aus.</span><span class="sxs-lookup"><span data-stu-id="1b065-383">Unity 5 brings new artistic power, enhanced graphics capabilities, and improved efficiency.</span></span>

<span data-ttu-id="1b065-384">Unity unterstützt ab Unity5.4 die Direct3D12-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="1b065-384">Beginning with Unity 5.4, Unity supports Direct3D 12 development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-385">Die Unity-Spielengine</span><span class="sxs-lookup"><span data-stu-id="1b065-385">The Unity game engine</span></span></td>
        <td>[<span data-ttu-id="1b065-386">Unity – Spielengine</span><span class="sxs-lookup"><span data-stu-id="1b065-386">Unity - Game Engine</span></span>](http://unity3d.com/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-387">Unity 5 herunterladen</span><span class="sxs-lookup"><span data-stu-id="1b065-387">Get Unity 5</span></span></td>
        <td>[<span data-ttu-id="1b065-388">Unity herunterladen</span><span class="sxs-lookup"><span data-stu-id="1b065-388">Get Unity</span></span>](http://unity3d.com/get-unity)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-389">Unterstützung von UWP-Apps (Universelle Windows-Plattform) in Unity 5.2 (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="1b065-389">Universal Windows Platform app support in Unity 5.2 (blog post)</span></span></td>
        <td>[<span data-ttu-id="1b065-390">Windows 10-Apps für Universelle Windows-Plattform in Unity 5.2</span><span class="sxs-lookup"><span data-stu-id="1b065-390">Windows 10 Universal Platform apps in Unity 5.2</span></span>](http://blogs.unity3d.com/2015/09/09/windows-10-universal-apps-in-unity-5-2/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-391">Unity-Dokumentation für Windows</span><span class="sxs-lookup"><span data-stu-id="1b065-391">Unity documentation for Windows</span></span></td>
        <td>[<span data-ttu-id="1b065-392">Unity-Handbuch/Windows</span><span class="sxs-lookup"><span data-stu-id="1b065-392">Unity Manual / Windows</span></span>](http://docs.unity3d.com/Manual/Windows.html)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-393">Wie fügen Sie Ihrem Spiel mit dem interaktiven Mixer Interaktivität hinzu</span><span class="sxs-lookup"><span data-stu-id="1b065-393">How to add interactivity to your game using Mixer Interactive</span></span></td>
        <td>[<span data-ttu-id="1b065-394">Leitfaden für erste Schritte</span><span class="sxs-lookup"><span data-stu-id="1b065-394">Getting started guide</span></span>](https://github.com/mixer/interactive-unity-plugin/wiki/Getting-started)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-395">Mixer SDK für Unity</span><span class="sxs-lookup"><span data-stu-id="1b065-395">Mixer SDK for Unity</span></span></td>
        <td>[<span data-ttu-id="1b065-396">Mixer Unity-Plug-In</span><span class="sxs-lookup"><span data-stu-id="1b065-396">Mixer Unity plugin</span></span>](https://www.assetstore.unity3d.com/en/#!/content/88585)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-397">Vollständige Referenzdokumentation für Mixer SDK für Unity</span><span class="sxs-lookup"><span data-stu-id="1b065-397">Mixer SDK for Unity reference documentation</span></span></td>
        <td>[<span data-ttu-id="1b065-398">API-Referenz für das Mixer Unity-Plug-In</span><span class="sxs-lookup"><span data-stu-id="1b065-398">API reference for Mixer Unity plugin</span></span>](https://dev.mixer.com/reference/interactive/csharp/index.html)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-399">Veröffentlichen eines Unity-Spiels im Windows Store</span><span class="sxs-lookup"><span data-stu-id="1b065-399">Publish your Unity game to Windows Store</span></span></td>
        <td>[<span data-ttu-id="1b065-400">Portierungsleitfaden</span><span class="sxs-lookup"><span data-stu-id="1b065-400">Porting guide</span></span>](https://unity3d.com/partners/microsoft/porting-guides)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-401">Veröffentlichen eines Unity-Spiels als UWP-App (Universelle Windows-Plattform) (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-401">Publish your Unity game as a Universal Windows Platform app (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-402">So veröffentlichen Sie Ihr Unity-Spiel als UWP-App</span><span class="sxs-lookup"><span data-stu-id="1b065-402">How to publish your Unity game as a UWP app</span></span>](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-403">Verwenden von Unity zum Erstellen von Windows-Spielen und -Apps (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-403">Use Unity to make Windows games and apps (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-404">Erstellen von Windows-Spielen und -Apps mit Unity</span><span class="sxs-lookup"><span data-stu-id="1b065-404">Making Windows games and apps with Unity</span></span>](https://channel9.msdn.com/Blogs/One-Dev-Minute/Making-games-and-apps-with-Unity)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-405">Unity-Spielentwicklung mit Visual Studio (Videoserie)</span><span class="sxs-lookup"><span data-stu-id="1b065-405">Unity game development using Visual Studio (video series)</span></span></td>
        <td>[<span data-ttu-id="1b065-406">Verwendung von Unity mit Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="1b065-406">Using Unity with Visual Studio 2015</span></span>](http://go.microsoft.com/fwlink/?LinkId=722359)</td>
    </tr>
</table>
 

#### <a name="havok"></a><span data-ttu-id="1b065-407">Havok</span><span class="sxs-lookup"><span data-stu-id="1b065-407">Havok</span></span>

<span data-ttu-id="1b065-408">Mit den Tools und Technologien aus der modular aufgebauten Suite von Havok erreichen Spieleentwickler eine noch nie dagewesene Interaktivität und Immersion.</span><span class="sxs-lookup"><span data-stu-id="1b065-408">Havok’s modular suite of tools and technologies help game creators reach new levels of interactivity and immersion.</span></span> <span data-ttu-id="1b065-409">Havok bietet eine äußerst realistische Physik, interaktive Simulationen und beeindruckende Effekte.</span><span class="sxs-lookup"><span data-stu-id="1b065-409">Havok enables highly realistic physics, interactive simulations, and stunning cinematics.</span></span> <span data-ttu-id="1b065-410">Version 2015.1 und höher unterstützen UWP in Visual Studio2015 auf x86-, 64-Bit- und ARM-Plattformen.</span><span class="sxs-lookup"><span data-stu-id="1b065-410">Version 2015.1 and higher officially supports UWP in Visual Studio 2015 on x86, 64-bit, and ARM.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-411">Havok-Website</span><span class="sxs-lookup"><span data-stu-id="1b065-411">Havok website</span></span></td>
        <td>[<span data-ttu-id="1b065-412">Havok</span><span class="sxs-lookup"><span data-stu-id="1b065-412">Havok</span></span>](http://www.havok.com/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-413">Havok-Toolsuite</span><span class="sxs-lookup"><span data-stu-id="1b065-413">Havok tool suite</span></span></td>
        <td>[<span data-ttu-id="1b065-414">Havok-Produktübersicht</span><span class="sxs-lookup"><span data-stu-id="1b065-414">Havok Product Overview</span></span>](http://www.havok.com/products/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-415">Havok-Supportforen</span><span class="sxs-lookup"><span data-stu-id="1b065-415">Havok support forums</span></span></td>
        <td>[<span data-ttu-id="1b065-416">Havok</span><span class="sxs-lookup"><span data-stu-id="1b065-416">Havok</span></span>](http://support.havok.com)</td>
    </tr>
</table>
 

#### <a name="monogame"></a><span data-ttu-id="1b065-417">MonoGame</span><span class="sxs-lookup"><span data-stu-id="1b065-417">MonoGame</span></span>

<span data-ttu-id="1b065-418">MonoGame ist ein plattformübergreifendes Open-Source-Framework für die Spieleentwicklung, das ursprünglich auf XNA Framework 4.0 von Microsoft basierte.</span><span class="sxs-lookup"><span data-stu-id="1b065-418">MonoGame is an open source, cross-platform game development framework originally based on Microsoft's XNA Framework 4.0.</span></span> <span data-ttu-id="1b065-419">MonoGame unterstützt derzeit Windows, Windows Phone und Xbox sowie Linux, macOS, iOS, Android und verschiedene andere Plattformen.</span><span class="sxs-lookup"><span data-stu-id="1b065-419">Monogame currently supports Windows, Windows Phone, and Xbox, as well as Linux, macOS, iOS, Android, and several other platforms.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-420">MonoGame</span><span class="sxs-lookup"><span data-stu-id="1b065-420">MonoGame</span></span></td>
        <td>[<span data-ttu-id="1b065-421">MonoGame-Website</span><span class="sxs-lookup"><span data-stu-id="1b065-421">MonoGame website</span></span>](http://www.monogame.net)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-422">MonoGame-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="1b065-422">MonoGame Documentation</span></span></td>
        <td>[<span data-ttu-id="1b065-423">MonoGame-Dokumentation (aktuell)</span><span class="sxs-lookup"><span data-stu-id="1b065-423">MonoGame Documentation (latest)</span></span>](http://www.monogame.net/documentation/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-424">MonoGame-Downloads</span><span class="sxs-lookup"><span data-stu-id="1b065-424">Monogame Downloads</span></span></td>
        <td><span data-ttu-id="1b065-425">[Laden Sie Versionen, Entwicklungsbuilds und Quellcode](http://www.monogame.net/downloads/) von der MonoGame-Website herunter, oder [rufen Sie die neueste Version über NuGet ab](https://www.nuget.org/profiles/MonoGame).</span><span class="sxs-lookup"><span data-stu-id="1b065-425">[Download releases, development builds, and source code](http://www.monogame.net/downloads/) from the MonoGame website, or [get the latest release via NuGet](https://www.nuget.org/profiles/MonoGame).</span></span>
    </tr>
</table>


#### <a name="cocos2d"></a><span data-ttu-id="1b065-426">Cocos2d</span><span class="sxs-lookup"><span data-stu-id="1b065-426">Cocos2d</span></span>

<span data-ttu-id="1b065-427">Cocos2d-X ist eine plattformübergreifende Suite mit Open-Source-Spieleentwicklungsengine und Tools, die die Erstellung von UWP-Spielen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1b065-427">Cocos2d-X is a cross-platform open source game development engine and tools suite that supports building UWP games.</span></span> <span data-ttu-id="1b065-428">Ab Version3 werden auch 3D-Features hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="1b065-428">Beginning with version 3, 3D features are being added as well.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-429">Cocos2d-X</span><span class="sxs-lookup"><span data-stu-id="1b065-429">Cocos2d-x</span></span></td>
        <td>[<span data-ttu-id="1b065-430">Was ist Cocos2d-X?</span><span class="sxs-lookup"><span data-stu-id="1b065-430">What is Cocos2d-X?</span></span>](http://www.cocos2d-x.org/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-431">Cocos2d-X-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="1b065-431">Cocos2d-x programmer's guide</span></span></td>
        <td>[<span data-ttu-id="1b065-432">Cocos2d-X-Programmieranleitungv3.8</span><span class="sxs-lookup"><span data-stu-id="1b065-432">Cocos2d-x Programmers Guide v3.8</span></span>](http://www.cocos2d-x.org/programmersguide/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-433">Cocos2d-X unter Windows10 (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="1b065-433">Cocos2d-x on Windows 10 (blog post)</span></span></td>
        <td>[<span data-ttu-id="1b065-434">Ausführen von Cocos2d-X unter Windows10</span><span class="sxs-lookup"><span data-stu-id="1b065-434">Running Cocos2d-x on Windows 10</span></span>](https://blogs.windows.com/buildingapps/2015/06/15/running-cocos2d-x-on-windows-10/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-435">Windows Store-Spiele mit Cocos2d-X (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-435">Cocos2d-x Windows Store games (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-436">Erstellen eines Spiels für Windows-Geräte mit Cocos2d-X</span><span class="sxs-lookup"><span data-stu-id="1b065-436">Build a Game with Cocos2d-x for Windows Devices</span></span>](http://www.microsoftvirtualacademy.com/training-courses/build-a-game-with-cocos2d-x-for-windows-devices)</td>
    </tr>
</table>


#### <a name="unreal-engine"></a><span data-ttu-id="1b065-437">Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="1b065-437">Unreal Engine</span></span>

<span data-ttu-id="1b065-438">Unreal Engine4 ist eine umfassende, für alle Arten von Spielen und Entwicklern geeignete Suite mit Tools für die Spieleentwicklung.</span><span class="sxs-lookup"><span data-stu-id="1b065-438">Unreal Engine 4 is a complete suite of game development tools for all types of games and developers.</span></span> <span data-ttu-id="1b065-439">Die Unreal Engine wird von Spieleentwicklern auf der ganzen Welt für besonders anspruchsvolle Konsolen- und PC-Spiele eingesetzt.</span><span class="sxs-lookup"><span data-stu-id="1b065-439">For the most demanding console and PC games, Unreal Engine is used by game developers worldwide.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-440">Übersicht über die Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="1b065-440">Unreal Engine overview</span></span></td>
        <td>[<span data-ttu-id="1b065-441">Unreal Engine4</span><span class="sxs-lookup"><span data-stu-id="1b065-441">Unreal Engine 4</span></span>](https://www.unrealengine.com/what-is-unreal-engine-4)</td>
    </tr>
</table>

#### <a name="babylonjs"></a><span data-ttu-id="1b065-442">BabylonJS</span><span class="sxs-lookup"><span data-stu-id="1b065-442">BabylonJS</span></span>

<span data-ttu-id="1b065-443">BabylonJS ist ein vollständiges JavaScript-Framework für die Erstellung von 3D-Spielen mit HTML5, WebGL und Web-Audio.</span><span class="sxs-lookup"><span data-stu-id="1b065-443">BabylonJS is a complete JavaScript framework for building 3D games with HTML5, WebGL, and Web Audio.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-444">BabylonJS</span><span class="sxs-lookup"><span data-stu-id="1b065-444">BabylonJS</span></span></td>
        <td>[<span data-ttu-id="1b065-445">BabylonJS</span><span class="sxs-lookup"><span data-stu-id="1b065-445">BabylonJS</span></span>](http://www.babylonjs.com/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-446">WebGL-3D mit HTML5 und BabylonJS (Videoserie)</span><span class="sxs-lookup"><span data-stu-id="1b065-446">WebGL 3D with HTML5 and BabylonJS (video series)</span></span></td>
        <td>[<span data-ttu-id="1b065-447">Learning WebGL 3D- und BabylonJS</span><span class="sxs-lookup"><span data-stu-id="1b065-447">Learning WebGL 3D and BabylonJS</span></span>](https://channel9.msdn.com/Series/Introduction-to-WebGL-3D-with-HTML5-and-Babylonjs/01)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-448">Erstellen eines plattformübergreifenden WebGL-Spiels mit BabylonJS</span><span class="sxs-lookup"><span data-stu-id="1b065-448">Building a cross-platform WebGL game with BabylonJS</span></span></td>
        <td>[<span data-ttu-id="1b065-449">Verwenden von BabylonJS zur Entwicklung eines plattformübergreifenden Spiels</span><span class="sxs-lookup"><span data-stu-id="1b065-449">Use BabylonJS to develop a cross-platform game</span></span>](https://www.smashingmagazine.com/2016/07/babylon-js-building-sponza-a-cross-platform-webgl-game/)</td>
    </tr>    
</table>

### <a name="middleware-and-partners"></a><span data-ttu-id="1b065-450">Middleware und Partner</span><span class="sxs-lookup"><span data-stu-id="1b065-450">Middleware and partners</span></span>

<span data-ttu-id="1b065-451">Es gibt noch viele weitere Middleware- und Engine-Partner, die Sie ggf. mit Lösungen für Ihre individuellen Anforderungen bei der Spieleentwicklung unterstützen können.</span><span class="sxs-lookup"><span data-stu-id="1b065-451">There are many other middleware and engine partners that can provide solutions depending on your game development needs.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-452">Windows Dev Center-Partner</span><span class="sxs-lookup"><span data-stu-id="1b065-452">Windows Dev Center partners</span></span></td>
        <td>[<span data-ttu-id="1b065-453">DevCenter-Partner</span><span class="sxs-lookup"><span data-stu-id="1b065-453">Dev Center Partners</span></span>](https://developer.microsoft.com/windows/app-middleware-partners)</td>
    </tr>
</table>


### <a name="porting-your-game"></a><span data-ttu-id="1b065-454">Portieren Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="1b065-454">Porting your game</span></span>

<span data-ttu-id="1b065-455">Entwicklern, die bereits über ein Spiel verfügen, stehen zahlreiche Ressourcen und Handbücher für eine schnelle UWP-Portierung ihres Spiels zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1b065-455">If you have an existing game, there are many resources and guides available to help you quickly bring your game to the UWP.</span></span> <span data-ttu-id="1b065-456">Als Starthilfe bei der Portierung empfiehlt sich unter Umständen die Verwendung einer [Brücke für die universelle Windows-Plattform](#universal-windows-platform-bridges).</span><span class="sxs-lookup"><span data-stu-id="1b065-456">To jumpstart your porting efforts, you might also consider using a [Universal Windows Platform Bridge](#universal-windows-platform-bridges).</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-457">Portieren einer Windows8-App zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="1b065-457">Porting a Windows 8 app to a Universal Windows Platform app</span></span></td>
        <td>[<span data-ttu-id="1b065-458">Wechsel von Windows-Runtime 8.x zu UWP</span><span class="sxs-lookup"><span data-stu-id="1b065-458">Move from Windows Runtime 8.x to UWP</span></span>](https://msdn.microsoft.com/library/windows/apps/mt238322)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-459">Portieren einer Windows 8-App zu einer UWP-App (Universelle Windows-Plattform) (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-459">Porting a Windows 8 app to a Universal Windows Platform app (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-460">Portieren von Windows 8.1-Apps zu Windows 10</span><span class="sxs-lookup"><span data-stu-id="1b065-460">Porting 8.1 Apps to Windows 10</span></span>](https://channel9.msdn.com/Series/A-Developers-Guide-to-Windows-10/21)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-461">Portieren einer iOS-App zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="1b065-461">Porting an iOS app to a Universal Windows Platform app</span></span></td>
        <td>[<span data-ttu-id="1b065-462">Wechsel von iOS zu UWP</span><span class="sxs-lookup"><span data-stu-id="1b065-462">Move from iOS to UWP</span></span>](https://msdn.microsoft.com/library/windows/apps/mt238320)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-463">Portieren einer Silverlight-App zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="1b065-463">Porting a Silverlight app to a Universal Windows Platform app</span></span></td>
        <td>[<span data-ttu-id="1b065-464">Wechsel von Windows Phone Silverlight zu UWP</span><span class="sxs-lookup"><span data-stu-id="1b065-464">Move from Windows Phone Silverlight to UWP</span></span>](https://msdn.microsoft.com/library/windows/apps/mt238323)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-465">Portieren von XAML oder Silverlight zu einer UWP-App (Universelle Windows-Plattform) (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-465">Porting from XAML or Silverlight to a Universal Windows Platform app (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-466">Portieren einer App von XAML oder Silverlight zu Windows 10</span><span class="sxs-lookup"><span data-stu-id="1b065-466">Porting an App from XAML or Silverlight to Windows 10</span></span>](https://channel9.msdn.com/Events/Build/2015/3-741)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-467">Portieren eines Xbox-Spiels zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="1b065-467">Porting an Xbox game to a Universal Windows Platform app</span></span></td>
        <td>[<span data-ttu-id="1b065-468">Portieren von Xbox One zu Windows 10 (UWP)</span><span class="sxs-lookup"><span data-stu-id="1b065-468">Porting from Xbox One to Windows 10 UWP</span></span>](https://developer.xboxlive.com/en-us/platform/development/education/Documents/Porting%20from%20Xbox%20One%20to%20Windows%2010.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-469">Portieren von DirectX 9 zu DirectX 11</span><span class="sxs-lookup"><span data-stu-id="1b065-469">Porting from DirectX 9 to DirectX 11</span></span></td>
        <td>[<span data-ttu-id="1b065-470">Portieren von DirectX9 zur universellen Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="1b065-470">Port from DirectX 9 to Universal Windows Platform (UWP)</span></span>](porting-your-directx-9-game-to-windows-store.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-471">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="1b065-471">Porting from Direct3D 11 to Direct3D 12</span></span></td>
        <td>[<span data-ttu-id="1b065-472">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="1b065-472">Porting from Direct3D 11 to Direct3D 12</span></span>](https://msdn.microsoft.com/library/windows/desktop/mt431709)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-473">Portieren von OpenGLES zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="1b065-473">Porting from OpenGL ES to Direct3D 11</span></span></td>
        <td>[<span data-ttu-id="1b065-474">Portieren von OpenGLES2.0 zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="1b065-474">Port from OpenGL ES 2.0 to Direct3D 11</span></span>](port-from-opengl-es-2-0-to-directx-11-1.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-475">OpenGLES2.0 zu Direct3D11 mit ANGLE</span><span class="sxs-lookup"><span data-stu-id="1b065-475">OpenGL ES to Direct3D 11 using ANGLE</span></span></td>
        <td>[<span data-ttu-id="1b065-476">ANGLE</span><span class="sxs-lookup"><span data-stu-id="1b065-476">ANGLE</span></span>](http://go.microsoft.com/fwlink/p/?linkid=618387)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-477">Entsprechungen für die klassische Windows-API in der UWP</span><span class="sxs-lookup"><span data-stu-id="1b065-477">Classic Windows API equivalents in the UWP</span></span></td>
        <td>[<span data-ttu-id="1b065-478">Alternativen zu Windows-APIs in Apps für die Universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="1b065-478">Alternatives to Windows APIs in Universal Windows Platform (UWP) apps</span></span>](https://msdn.microsoft.com/library/windows/apps/hh464945)</td>
    </tr>
</table>


## <a name="prototype-and-design"></a><span data-ttu-id="1b065-479">Prototyp und Design</span><span class="sxs-lookup"><span data-stu-id="1b065-479">Prototype and design</span></span>


<span data-ttu-id="1b065-480">Nachdem Sie sich entschieden haben, welche Art von Spiel Sie entwickeln und welche Tools und Grafiktechnologie Sie dabei verwenden möchten, können Sie sich der Gestaltung zuwenden und einen Prototyp entwickeln.</span><span class="sxs-lookup"><span data-stu-id="1b065-480">Now that you've decided the type of game you want to create and the tools and graphics technology you'll use to build it, you're ready to get started with the design and prototype.</span></span> <span data-ttu-id="1b065-481">Da es sich bei Ihrem Spiel im Grunde um eine UWP-App (Universelle Windows-Plattform) handelt, beginnen Sie dort.</span><span class="sxs-lookup"><span data-stu-id="1b065-481">At its core, your game is a Universal Windows Platform app, so that's where you'll begin.</span></span>

### <a name="introduction-to-the-universal-windows-platform-uwp"></a><span data-ttu-id="1b065-482">Einführung in die universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="1b065-482">Introduction to the Universal Windows Platform (UWP)</span></span>

<span data-ttu-id="1b065-483">Windows10 führt die universelle Windows-Plattform (UWP) ein. Diese stellt eine gemeinsame, übergreifende API-Plattform für Windows10-Geräte bereit.</span><span class="sxs-lookup"><span data-stu-id="1b065-483">Windows 10 introduces the Universal Windows Platform (UWP), which provides a common API platform across Windows 10 devices.</span></span> <span data-ttu-id="1b065-484">Bei der UWP handelt es sich um eine Weiterentwicklung und Erweiterung des Windows-Runtime-Modells zu einem geschlossenen, einheitlichen Kern.</span><span class="sxs-lookup"><span data-stu-id="1b065-484">UWP evolves and expands the Windows Runtime model and hones it into a cohesive, unified core.</span></span> <span data-ttu-id="1b065-485">Für die UWP entwickelte Spiele können WinRT-APIs aufrufen, die bei allen Geräten vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="1b065-485">Games that target the UWP can call WinRT APIs that are common to all devices.</span></span> <span data-ttu-id="1b065-486">Da die UWP eine garantierte Kern-API-Ebene bereitstellt, können Sie ein einzelnes App-Paket erstellen, das dann auf allen Windows10-Geräten installiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="1b065-486">Because the UWP provides a guaranteed core API layer, you can choose to create a single app package that will install across Windows 10 devices.</span></span> <span data-ttu-id="1b065-487">Bei Bedarf kann Ihr Spiel natürlich auch weiterhin spezifische APIs der Geräte aufrufen, auf denen das Spiel ausgeführt wird – etwa einige klassische Windows-APIs von Win32 und .NET.</span><span class="sxs-lookup"><span data-stu-id="1b065-487">And if you want to, your game can still call APIs (including some classic Windows APIs from Win32 and .NET) that are specific to the devices your game runs on.</span></span>

<span data-ttu-id="1b065-488">Ziele der UWP:</span><span class="sxs-lookup"><span data-stu-id="1b065-488">The goal of the UWP is to have:</span></span>

-   <span data-ttu-id="1b065-489">Ein Kernbetriebssystem</span><span class="sxs-lookup"><span data-stu-id="1b065-489">One core operating system</span></span>
-   <span data-ttu-id="1b065-490">Eine Anwendungsplattform</span><span class="sxs-lookup"><span data-stu-id="1b065-490">One application platform</span></span>
-   <span data-ttu-id="1b065-491">Ein soziales Netzwerk für Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-491">One gaming social network</span></span>
-   <span data-ttu-id="1b065-492">Ein Shop</span><span class="sxs-lookup"><span data-stu-id="1b065-492">One store</span></span>
-   <span data-ttu-id="1b065-493">Ein Aufnahmepfad</span><span class="sxs-lookup"><span data-stu-id="1b065-493">One ingestion path</span></span>

<span data-ttu-id="1b065-494">Im Anschluss finden Sie praktische Handbücher, die sich ausführlich mit UWP-Apps (Universelle Windows-Plattform) auseinandersetzen und hilfreiche Erkenntnisse zur Plattform liefern.</span><span class="sxs-lookup"><span data-stu-id="1b065-494">The following are excellent guides that discuss the Universal Windows Platform apps in detail, and are recommended reading to help you understand the platform.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-495">Einführung in UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="1b065-495">Introduction to Universal Windows Platform apps</span></span></td>
        <td>[<span data-ttu-id="1b065-496">Was ist eine UWP-App (Universelle Windows-Plattform)?</span><span class="sxs-lookup"><span data-stu-id="1b065-496">What's a Universal Windows Platform app?</span></span>](https://msdn.microsoft.com/library/windows/apps/dn726767)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-497">Übersicht über die UWP</span><span class="sxs-lookup"><span data-stu-id="1b065-497">Overview of the UWP</span></span></td>
        <td>[<span data-ttu-id="1b065-498">Anleitung für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-498">Guide to UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn894631)</td>
    </tr>
</table>
 

### <a name="getting-started-with-uwp-development"></a><span data-ttu-id="1b065-499">Erste Schritte bei der UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="1b065-499">Getting started with UWP development</span></span>

<span data-ttu-id="1b065-500">Die Vorbereitung auf die Entwicklung einer UWP-App (Universelle Windows-Plattform) ist ganz einfach und im Handumdrehen erledigt.</span><span class="sxs-lookup"><span data-stu-id="1b065-500">Getting set up and ready to develop a Universal Windows Platform app is quick and easy.</span></span> <span data-ttu-id="1b065-501">Die erforderlichen Schritte werden in den folgenden Handbüchern erläutert:</span><span class="sxs-lookup"><span data-stu-id="1b065-501">The following guides take you through the process step-by-step.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-502">Erste Schritte bei der UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="1b065-502">Getting started with UWP development</span></span></td>
        <td>[<span data-ttu-id="1b065-503">Erste Schritte mit Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-503">Get started with Windows apps</span></span>](https://dev.windows.com/getstarted)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-504">Vorbereitung auf die UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="1b065-504">Getting set up for UWP development</span></span></td>
        <td>[<span data-ttu-id="1b065-505">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="1b065-505">Get set up</span></span>](https://msdn.microsoft.com/library/windows/apps/dn726766)</td>
    </tr>
</table>

<span data-ttu-id="1b065-506">Wenn Sie noch keine Erfahrungen mit der UWP-Programmierung haben und die Verwendung von XAML in Ihrem Spiel in Betracht ziehen (siehe [Auswählen von Grafiktechnologie und Programmiersprache](#choosing-your-graphics-technology-and-programming-language)), ist die Videoserie [Windows10-Entwicklung für Neueinsteiger](https://channel9.msdn.com/Series/Windows-10-development-for-absolute-beginners) ein guter Ausgangspunkt.</span><span class="sxs-lookup"><span data-stu-id="1b065-506">If you're an "absolute beginner" to UWP programming, and are considering using XAML in your game (see [Choosing your graphics technology and programming language](#choosing-your-graphics-technology-and-programming-language)), the [Windows 10 development for absolute beginners](https://channel9.msdn.com/Series/Windows-10-development-for-absolute-beginners) video series is a good place to start.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-507">Einsteigerhandbuch für die Windows10-Entwicklung mit XAML (Videoserie)</span><span class="sxs-lookup"><span data-stu-id="1b065-507">Beginners guide to Windows 10 development with XAML (Video series)</span></span></td>
        <td>[<span data-ttu-id="1b065-508">Windows10-Entwicklung für Neueinsteiger</span><span class="sxs-lookup"><span data-stu-id="1b065-508">Windows 10 development for absolute beginners</span></span>](https://channel9.msdn.com/Series/Windows-10-development-for-absolute-beginners)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-509">Ankündigung der Windows10-Neueinsteigerserie mit XAML (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="1b065-509">Announcing the Windows 10 absolute beginners series using XAML (blog post)</span></span></td>
        <td>[<span data-ttu-id="1b065-510">Windows 10-Entwicklung für Neueinsteiger</span><span class="sxs-lookup"><span data-stu-id="1b065-510">Windows 10 development for absolute beginners</span></span>](http://blogs.windows.com/buildingapps/2015/09/30/windows-10-development-for-absolute-beginners/)</td>
    </tr>
</table>

### <a name="uwp-development-concepts"></a><span data-ttu-id="1b065-511">UWP-Entwicklungskonzepte</span><span class="sxs-lookup"><span data-stu-id="1b065-511">UWP development concepts</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-512">Übersicht über die Entwicklung von UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="1b065-512">Overview of Universal Windows Platform app development</span></span></td>
        <td>[<span data-ttu-id="1b065-513">Entwickeln von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-513">Develop Windows apps</span></span>](https://dev.windows.com/develop)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-514">Übersicht über die Netzwerkprogrammierung der UWP</span><span class="sxs-lookup"><span data-stu-id="1b065-514">Overview of network programming in the UWP</span></span></td>
        <td>[<span data-ttu-id="1b065-515">Netzwerk und Webdienste</span><span class="sxs-lookup"><span data-stu-id="1b065-515">Networking and web services</span></span>](https://msdn.microsoft.com/library/windows/apps/mt280378)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-516">Verwenden von „Windows.Web.HTTP“ und „Windows.Networking.Sockets“ in Spielen</span><span class="sxs-lookup"><span data-stu-id="1b065-516">Using Windows.Web.HTTP and Windows.Networking.Sockets in games</span></span></td>
        <td>[<span data-ttu-id="1b065-517">Netzwerkfunktionen für Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-517">Networking for games</span></span>](work-with-networking-in-your-directx-game.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-518">Asynchrone Programmierkonzepte der UWP</span><span class="sxs-lookup"><span data-stu-id="1b065-518">Asynchronous programming concepts in the UWP</span></span></td>
        <td>[<span data-ttu-id="1b065-519">Asynchrone Programmierung</span><span class="sxs-lookup"><span data-stu-id="1b065-519">Asynchronous programming</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187335)</td>
    </tr>
</table>

### <a name="windows-desktop-apis-to-uwp"></a><span data-ttu-id="1b065-520">Windows-Desktop-APIs zu UWP</span><span class="sxs-lookup"><span data-stu-id="1b065-520">Windows Desktop APIs to UWP</span></span>

<span data-ttu-id="1b065-521">Hier finden Sie einige Links, die Sie beim Wechsel von Windows-Desktop-Spielen zu UWP-Spielen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="1b065-521">These are some links to help you move your Windows desktop game to UWP.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-522">Verwenden Sie vorhandenen C++-Code für die UWP-Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="1b065-522">Use existing C++ code for UWP game development</span></span></td>
        <td>[<span data-ttu-id="1b065-523">Vorgehensweise: Verwenden von vorhandenem C++-Code in einer UWP-App</span><span class="sxs-lookup"><span data-stu-id="1b065-523">How to: Use existing C++ code in a UWP app</span></span>](https://docs.microsoft.com/cpp/porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-524">UWP-APIs für Win32- und COM-APIs</span><span class="sxs-lookup"><span data-stu-id="1b065-524">UWP APIs for Win32 and COM APIs</span></span></td>
        <td>[<span data-ttu-id="1b065-525">Win32- und COM-APIs für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-525">Win32 and COM APIs for UWP apps</span></span>](https://docs.microsoft.com/uwp/win32-and-com/win32-and-com-for-uwp-apps)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-526">Nicht unterstützte CRT-Funktionen in UWP</span><span class="sxs-lookup"><span data-stu-id="1b065-526">Unsupported CRT functions in UWP</span></span></td>
        <td>[<span data-ttu-id="1b065-527">Nicht unterstützte CRT-Funktionen in Apps für die universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="1b065-527">CRT functions not supported in Universal Windows Platform apps</span></span>](https://msdn.microsoft.com/library/windows/apps/jj606124.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-528">Alternativen zu Windows-APIs</span><span class="sxs-lookup"><span data-stu-id="1b065-528">Alternatives for Windows APIs</span></span></td>
        <td>[<span data-ttu-id="1b065-529">Alternativen zu Windows-APIs in Apps für die universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="1b065-529">Alternatives to Windows APIs in Universal Windows Platform (UWP) apps</span></span>](https://msdn.microsoft.com/library/windows/apps/mt592894.aspx)</td>
    </tr>
</table>
 

### <a name="process-lifetime-management"></a><span data-ttu-id="1b065-530">Prozesslebensdauer-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="1b065-530">Process lifetime management</span></span>

<span data-ttu-id="1b065-531">Prozesslebensdauer-Verwaltung (oder App-Lebenszyklus) beschreibt die verschiedenen Aktivierungszustände, die eine UWP-App (Universelle Windows-Plattform) durchlaufen kann.</span><span class="sxs-lookup"><span data-stu-id="1b065-531">Process lifetime management, or app lifecyle, describes the various activation states that a Universal Windows Platform app can transition through.</span></span> <span data-ttu-id="1b065-532">Ihr Spiel kann aktiviert, angehalten, fortgesetzt oder beendet werden und diese Zustände auf unterschiedliche Arten durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="1b065-532">Your game can be activated, suspended, resumed, or terminated, and can transition through those states in a variety of ways.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-533">Behandeln von App-Lebenszyklusübergängen</span><span class="sxs-lookup"><span data-stu-id="1b065-533">Handling app lifecyle transitions</span></span></td>
        <td>[<span data-ttu-id="1b065-534">App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="1b065-534">App lifecycle</span></span>](https://msdn.microsoft.com/library/windows/apps/mt243287)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-535">Auslösen von App-Übergängen mithilfe von Microsoft Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b065-535">Using Microsoft Visual Studio to trigger app transitions</span></span></td>
        <td>[<span data-ttu-id="1b065-536">So wird's gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen für WindowsStore-Apps in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b065-536">How to trigger suspend, resume, and background events for Windows Store apps in Visual Studio</span></span>](https://msdn.microsoft.com/library/hh974425.aspx)</td>
    </tr>
</table>
 

### <a name="designing-game-ux"></a><span data-ttu-id="1b065-537">Gestalten der UX von Spielen</span><span class="sxs-lookup"><span data-stu-id="1b065-537">Designing game UX</span></span>

<span data-ttu-id="1b065-538">Großartigen Spielen liegt in der Regel ein kreatives Design zugrunde.</span><span class="sxs-lookup"><span data-stu-id="1b065-538">The genesis of a great game is inspired design.</span></span>

<span data-ttu-id="1b065-539">Spiele und Apps teilen sich zwar einige Benutzeroberflächenelemente und Designprinzipien, beim Spieldesign werden jedoch häufig ein ganz besonderer Look und ein einzigartiges Spielgefühl angestrebt.</span><span class="sxs-lookup"><span data-stu-id="1b065-539">Games share some common user interface elements and design principles with apps, but games often have a unique look, feel, and design goal for their user experience.</span></span> <span data-ttu-id="1b065-540">Spiele sind erfolgreich, wenn in beiden Bereichen ein durchdachtes Design gewählt wird: Wann sollten Sie in Ihrem Spiel bewährte Benutzeroberflächenelemente verwenden, und wann sollten Sie davon abweichen und innovativ vorgehen?</span><span class="sxs-lookup"><span data-stu-id="1b065-540">Games succeed when thoughtful design is applied to both aspects—when should your game use tested UX, and when should it diverge and innovate?</span></span> <span data-ttu-id="1b065-541">Die Darstellungstechnologie, die Sie für das Spiel auswählen – DirectX, XAML, HTML5 oder eine beliebige Kombination –, wird sich auf die Implementierungsdetails auswirken. Die von Ihnen angewendeten Entwurfsprinzipien sind aber nicht von der jeweiligen Wahl abhängig.</span><span class="sxs-lookup"><span data-stu-id="1b065-541">The presentation technology that you choose for your game—DirectX, XAML, HTML5, or some combination of the three—will influence implementation details, but the design principles you apply are largely independent of that choice.</span></span>

<span data-ttu-id="1b065-542">Zusätzlich zum UX-Design müssen Sie sich auch mit dem Gameplay-Design auseinandersetzen, was unter anderem Aspekte wie Leveldesign, Pacing und Umgebungsdesign umfasst. Da es sich hierbei um eine ganz eigene Kunstform handelt, gehen wir in diesem Dokument nicht näher darauf ein, sondern überlassen diesen Bereich ganz Ihnen und Ihrem Team.</span><span class="sxs-lookup"><span data-stu-id="1b065-542">Separately from UX design, gameplay design such as level design, pacing, world design, and other aspects is an art form of its own—one that's up to you and your team, and not covered in this development guide.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-543">UWP-Gestaltungsgrundlagen und -richtlinien</span><span class="sxs-lookup"><span data-stu-id="1b065-543">UWP design basics and guidelines</span></span></td>
        <td>[<span data-ttu-id="1b065-544">Gestalten von UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-544">Designing UWP apps</span></span>](https://dev.windows.com/design)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-545">Gestalten für App-Lebenszykluszustände</span><span class="sxs-lookup"><span data-stu-id="1b065-545">Designing for app lifecycle states</span></span></td>
        <td>[<span data-ttu-id="1b065-546">UX-Richtlinien für das Starten, Anhalten und Fortsetzen von Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-546">UX guidelines for launch, suspend, and resume</span></span>](https://msdn.microsoft.com/library/windows/apps/dn611862)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-547">Entwerfen Sie Ihre UWP-App für Xbox One und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="1b065-547">Design your UWP app for Xbox One and television screens</span></span></td>
        <td>[<span data-ttu-id="1b065-548">Entwerfen für Xbox und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="1b065-548">Designing for Xbox and TV</span></span>](https://docs.microsoft.com/windows/uwp/input-and-devices/designing-for-tv)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-549">Ausrichten auf verschiedene Geräteformfaktoren (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-549">Targeting multiple device form factors (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-550">Entwerfen von Spielen für eine WindowsCore-Welt</span><span class="sxs-lookup"><span data-stu-id="1b065-550">Designing Games for a Windows Core World</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/Designing-Games-for-a-Windows-Core-World)</td>
    </tr>   
</table>
 

#### <a name="color-guideline-and-palette"></a><span data-ttu-id="1b065-551">Farbrichtlinie und -palette</span><span class="sxs-lookup"><span data-stu-id="1b065-551">Color guideline and palette</span></span>

<span data-ttu-id="1b065-552">Eine einheitliche Farbrichtlinie verbessert die Spielästhetik, vereinfacht die Navigation und ist ein wirksames Mittel, um Spieler über Menü- und HUD-Funktionen zu informieren.</span><span class="sxs-lookup"><span data-stu-id="1b065-552">Following a consistent color guideline in your game improves aesthetics, aids navigation, and is a powerful tool to inform the player of menu and HUD functionality.</span></span> <span data-ttu-id="1b065-553">Eine einheitliche Farbgestaltung von Spielelementen wie Warnungen, Schäden, Erfahrungspunkten und Erfolgen kann die Übersichtlichkeit der Benutzeroberfläche verbessern und explizite Beschriftungen überflüssig machen.</span><span class="sxs-lookup"><span data-stu-id="1b065-553">Consistent coloring of game elements like warnings, damage, XP, and achievements can lead to cleaner UI and reduce the need for explicit labels.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-554">Farbhandbuch</span><span class="sxs-lookup"><span data-stu-id="1b065-554">Color guide</span></span></td>
        <td>[<span data-ttu-id="1b065-555">Bewährte Methoden: Farbe</span><span class="sxs-lookup"><span data-stu-id="1b065-555">Best Practices: Color</span></span>](https://assets.windowsphone.com/499cd2be-64ed-4b05-a4f5-cd0c9ad3f6a3/101_BestPractices_Color_InvariantCulture_Default.zip)</td>
    </tr>
</table>
 

#### <a name="typography"></a><span data-ttu-id="1b065-556">Typografie</span><span class="sxs-lookup"><span data-stu-id="1b065-556">Typography</span></span>

<span data-ttu-id="1b065-557">Durch den angemessenen Einsatz von Typografie können Sie Ihr Spiel in vielerlei Hinsicht verbessern – etwa in Bezug auf UI-Layout, Navigation, Lesbarkeit, Atmosphäre und Spielerimmersion.</span><span class="sxs-lookup"><span data-stu-id="1b065-557">The appropriate use of typography enhances many aspects of your game, including UI layout, navigation, readability, atmosphere, brand, and player immersion.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-558">Typografiehandbuch</span><span class="sxs-lookup"><span data-stu-id="1b065-558">Typography guide</span></span></td>
        <td>[<span data-ttu-id="1b065-559">Bewährte Methoden: Typografie</span><span class="sxs-lookup"><span data-stu-id="1b065-559">Best Practices: Typography</span></span>](http://go.microsoft.com/fwlink/?LinkId=535007)</td>
    </tr>
</table>
 

#### <a name="ui-map"></a><span data-ttu-id="1b065-560">UI-Zuordnung</span><span class="sxs-lookup"><span data-stu-id="1b065-560">UI map</span></span>

<span data-ttu-id="1b065-561">Bei einer UI-Zuordnung handelt es sich um eine Layoutübersicht über die Navigation und Menüs eines Spiels in Form eines Flussdiagramms.</span><span class="sxs-lookup"><span data-stu-id="1b065-561">A UI map is a layout of game navigation and menus expressed as a flowchart.</span></span> <span data-ttu-id="1b065-562">Die UI-Zuordnung verbessert die Nachvollziehbarkeit der Oberfläche und der Navigationspfade eines Spiels für alle Beteiligten und trägt zur frühzeitigen Erkennung potenzieller Probleme und Sackgassen bei.</span><span class="sxs-lookup"><span data-stu-id="1b065-562">The UI map helps all involved stakeholders understand the game’s interface and navigation paths, and can expose potential roadblocks and dead ends early in the development cycle.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-563">Anleitung für die UI-Zuordnung</span><span class="sxs-lookup"><span data-stu-id="1b065-563">UI map guide</span></span></td>
        <td>[<span data-ttu-id="1b065-564">Bewährte Methoden: UI-Zuordnung</span><span class="sxs-lookup"><span data-stu-id="1b065-564">Best Practices: UI Map</span></span>](http://go.microsoft.com/fwlink/?LinkId=535008)</td>
    </tr>
</table>

### <a name="game-audio"></a><span data-ttu-id="1b065-565">Audio in Spielen</span><span class="sxs-lookup"><span data-stu-id="1b065-565">Game audio</span></span>

<span data-ttu-id="1b065-566">Anleitungen und Referenzen für die Implementierung von Audio in Spielen mit XAudio2, XAPO und Windows Sonic.</span><span class="sxs-lookup"><span data-stu-id="1b065-566">Guides and references for implementing audio in games using XAudio2, XAPO, and Windows Sonic.</span></span> <span data-ttu-id="1b065-567">XAudio2 ist eine Low-Level-Audio-API, die eine grundlegende Signalverarbeitung und -abmischung zum Entwickeln von Audiomodulen mit hoher Leistung für Spiele bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="1b065-567">XAudio2 is a low-level audio API that provides signal processing and mixing foundation for developing high performance audio engines.</span></span> <span data-ttu-id="1b065-568">XAPO-API ermöglicht die Erstellung von plattformübergreifenden Audioverarbeitungsobjekten (XAPO) zur Verwendung in XAudio2 für Windows und Xbox.</span><span class="sxs-lookup"><span data-stu-id="1b065-568">XAPO API allows the creation of cross-platform audio processing objects (XAPO) for use in XAudio2 on both Windows and Xbox.</span></span> <span data-ttu-id="1b065-569">Mit der Windows Sonic Audiounterstützung können Sie Ihrem Spiel oder der Streaming-Media-Anwendung Dolby Atmos for Home Theater, Dolby Atmos for Headphones und Windows kopfbezogene Übertragungsfunktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1b065-569">Windows Sonic audio support allows you to add Dolby Atmos for Home Theater, Dolby Atmos for Headphones, and Windows HRTF support to your game or streaming media application.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-570">XAudio2-APIs</span><span class="sxs-lookup"><span data-stu-id="1b065-570">XAudio2 APIs</span></span></td>
        <td>[<span data-ttu-id="1b065-571">Programmieranleitung und API-Referenz für XAudio2</span><span class="sxs-lookup"><span data-stu-id="1b065-571">Programming guide and API reference for XAudio2</span></span>](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-572">Plattformübergreifende Audioverarbeitungsobjekte erstellen</span><span class="sxs-lookup"><span data-stu-id="1b065-572">Create cross-platform audio processing objects</span></span></td>
        <td>[<span data-ttu-id="1b065-573">XAPO: Übersicht</span><span class="sxs-lookup"><span data-stu-id="1b065-573">XAPO Overview</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-574">Einführung in Audio-Konzepte</span><span class="sxs-lookup"><span data-stu-id="1b065-574">Intro to audio concepts</span></span></td>
        <td>[<span data-ttu-id="1b065-575">Audio für Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-575">Audio for games</span></span>](working-with-audio-in-your-directx-game.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-576">Übersicht über Windows Sonic</span><span class="sxs-lookup"><span data-stu-id="1b065-576">Windows Sonic overview</span></span></td>
        <td>[<span data-ttu-id="1b065-577">Raumklang</span><span class="sxs-lookup"><span data-stu-id="1b065-577">Spatial sound</span></span>](https://msdn.microsoft.com/library/windows/desktop/mt807491.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-578">Windows-Sonic Raumklang - Beispiele</span><span class="sxs-lookup"><span data-stu-id="1b065-578">Windows Sonic spatial sound samples</span></span></td>
        <td>[<span data-ttu-id="1b065-579">Xbox Advanced Technology Group – Audiobeispiele</span><span class="sxs-lookup"><span data-stu-id="1b065-579">Xbox Advanced Technology Group audio samples</span></span>](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/Audio)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-580">Hier erfahren Sie, wie Sie Windows Sonic in Ihre Spiele (Video) integrieren</span><span class="sxs-lookup"><span data-stu-id="1b065-580">Learn how to integrate Windows Sonic into your games (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-581">Einführung in die räumlichen Audiofunktionen für Xbox und Windows</span><span class="sxs-lookup"><span data-stu-id="1b065-581">Introducing Spatial Audio Capabilities for Xbox and Windows</span></span>](https://channel9.msdn.com/Events/GDC/GDC-2017/GDC2017-002)</td>
    </tr>
</table>

### <a name="directx-development"></a><span data-ttu-id="1b065-582">DirectX-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="1b065-582">DirectX development</span></span>

<span data-ttu-id="1b065-583">Anleitungen und Referenzen für die Entwicklung von DirectX-Spielen</span><span class="sxs-lookup"><span data-stu-id="1b065-583">Guides and references for DirectX game development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-584">Entwicklung von DirectX-Spielen auf der UWP</span><span class="sxs-lookup"><span data-stu-id="1b065-584">DirectX game development on the UWP</span></span></td>
        <td>[<span data-ttu-id="1b065-585">Spiele und DirectX</span><span class="sxs-lookup"><span data-stu-id="1b065-585">Games and DirectX</span></span>](index.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-586">DirectX-Interaktionen mit dem UWP-App-Modell</span><span class="sxs-lookup"><span data-stu-id="1b065-586">DirectX interaction with the UWP app model</span></span></td>
        <td>[<span data-ttu-id="1b065-587">Das App-Objekt und DirectX</span><span class="sxs-lookup"><span data-stu-id="1b065-587">The app object and DirectX</span></span>](about-the-metro-style-user-interface-and-directx.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-588">Videos zu Grafiken und zur DirectX12-Entwicklung (YouTube-Kanal)</span><span class="sxs-lookup"><span data-stu-id="1b065-588">Graphics and DirectX 12 development videos (YouTube channel)</span></span></td>
        <td>[<span data-ttu-id="1b065-589">Informationen zu Microsoft DirectX12 und Grafiken</span><span class="sxs-lookup"><span data-stu-id="1b065-589">Microsoft DirectX 12 and Graphics Education</span></span>](https://www.youtube.com/channel/UCiaX2B8XiXR70jaN7NK-FpA)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-590">Übersichten und Referenzen zu DirectX</span><span class="sxs-lookup"><span data-stu-id="1b065-590">DirectX overviews and reference</span></span></td>
        <td>[<span data-ttu-id="1b065-591">DirectX-Grafiken und -Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-591">DirectX Graphics and Gaming</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee663274)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-592">Direct3D12-Programmieranleitung und -referenz</span><span class="sxs-lookup"><span data-stu-id="1b065-592">Direct3D 12 programming guide and reference</span></span></td>
        <td>[<span data-ttu-id="1b065-593">Direct3D12-Grafiken</span><span class="sxs-lookup"><span data-stu-id="1b065-593">Direct3D 12 Graphics</span></span>](https://msdn.microsoft.com/library/windows/desktop/dn903821)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-594">DirectX12-Grundlagen (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-594">DirectX 12 fundamentals (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-595">Bessere Leistung und Performance: Ihr Spiel unter DirectX12</span><span class="sxs-lookup"><span data-stu-id="1b065-595">Better Power, Better Performance: Your Game on DirectX 12</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/Better-Power-Better-Performance-Your-Game-on-DirectX12)</td>
    </tr>
</table>

#### <a name="learning-direct3d-12"></a><span data-ttu-id="1b065-596">Erlernen von Direct3D2</span><span class="sxs-lookup"><span data-stu-id="1b065-596">Learning Direct3D 12</span></span>

<span data-ttu-id="1b065-597">Erfahren Sie mehr über die Änderungen in Direct3D12 und wie Sie mit der Programmierung in Direct3D12 beginnen können.</span><span class="sxs-lookup"><span data-stu-id="1b065-597">Learn what changed in Direct3D 12 and how to start programming using Direct3D 12.</span></span> 

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-598">Einrichten der Programmierumgebung</span><span class="sxs-lookup"><span data-stu-id="1b065-598">Set up programming environment</span></span></td>
        <td>[<span data-ttu-id="1b065-599">Einrichtung der Direct3D12 Programmierungsumgebung</span><span class="sxs-lookup"><span data-stu-id="1b065-599">Direct3D 12 programming environment setup</span></span>](https://msdn.microsoft.com/library/windows/desktop/dn899120.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-600">Erstellen einer Grundkomponente</span><span class="sxs-lookup"><span data-stu-id="1b065-600">How to create a basic component</span></span></td>
        <td>[<span data-ttu-id="1b065-601">Erstellen einer einfachen Direct3D12-Komponente</span><span class="sxs-lookup"><span data-stu-id="1b065-601">Creating a basic Direct3D 12 component</span></span>](https://msdn.microsoft.com/library/windows/desktop/dn859356.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-602">Änderungen in Direct3D12</span><span class="sxs-lookup"><span data-stu-id="1b065-602">Changes in Direct3D 12</span></span></td>
        <td>[<span data-ttu-id="1b065-603">Wichtige Änderungen bei der Migration von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="1b065-603">Important changes migrating from Direct3D 11 to Direct3D 12</span></span>](https://msdn.microsoft.com/library/windows/desktop/dn899194.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-604">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="1b065-604">How to port from Direct3D 11 to Direct3D 12</span></span></td>
        <td>[<span data-ttu-id="1b065-605">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="1b065-605">Porting from Direct3D 11 to Direct3D 12</span></span>](https://msdn.microsoft.com/library/windows/desktop/mt431709.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-606">Konzepte für die Ressourcenbindung (deckt Deskriptor, Deskriptortabelle, Deskriptorheap und Stammsignatur ab)</span><span class="sxs-lookup"><span data-stu-id="1b065-606">Resource binding concepts (covering descriptor, descriptor table, descriptor heap, and root signature)</span></span> </td>
        <td>[<span data-ttu-id="1b065-607">Ressourcenbindung in Direct3D12</span><span class="sxs-lookup"><span data-stu-id="1b065-607">Resource binding in Direct3D 12</span></span>](https://msdn.microsoft.com/library/windows/desktop/dn899206.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-608">Verwalten des Arbeitsspeichers</span><span class="sxs-lookup"><span data-stu-id="1b065-608">Managing memory</span></span></td>
        <td>[<span data-ttu-id="1b065-609">Arbeitsspeicherverwaltung in Direct3D12</span><span class="sxs-lookup"><span data-stu-id="1b065-609">Memory management in Direct3D 12</span></span>](https://msdn.microsoft.com/library/windows/desktop/dn899198.aspx)</td>
    </tr>
</table>
 
#### <a name="directx-tool-kit-and-libraries"></a><span data-ttu-id="1b065-610">DirectX-Toolkit und -Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="1b065-610">DirectX Tool Kit and libraries</span></span>

<span data-ttu-id="1b065-611">Das DirectX-Toolkit, die DirectX-Texturverarbeitungsbibliothek, die DirectXMesh-Geometrieverarbeitungsbibliothek, die UVAtlas-Bibliothek und die DirectXMath-Bibliothek bieten textur-, gitter- und spritebezogene sowie weitere Hilfsprogrammfunktionen und Hilfsklassen für die DirectX-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="1b065-611">The DirectX Tool Kit, DirectX texture processing library, DirectXMesh geometry processing library, UVAtlas library, and DirectXMath library provide texture, mesh, sprite, and other utility functionality and helper classes for DirectX development.</span></span> <span data-ttu-id="1b065-612">Diese Bibliotheken können Ihnen helfen, Entwicklungszeit und -aufwand einzusparen.</span><span class="sxs-lookup"><span data-stu-id="1b065-612">These libraries can help you save development time and effort.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-613">DirectX-Toolkit für DirectX11 herunterladen</span><span class="sxs-lookup"><span data-stu-id="1b065-613">Get DirectX Tool Kit for DirectX 11</span></span></td>
        <td>[<span data-ttu-id="1b065-614">DirectXTK</span><span class="sxs-lookup"><span data-stu-id="1b065-614">DirectXTK</span></span>](http://go.microsoft.com/fwlink/?LinkId=248929)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-615">DirectX-Toolkit für DirectX12 herunterladen</span><span class="sxs-lookup"><span data-stu-id="1b065-615">Get DirectX Tool Kit for DirectX 12</span></span></td>
        <td>[<span data-ttu-id="1b065-616">DirectXTK12</span><span class="sxs-lookup"><span data-stu-id="1b065-616">DirectXTK 12</span></span>](http://go.microsoft.com/fwlink/?LinkID=615561)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-617">DirectX-Texturverarbeitungsbibliothek herunterladen</span><span class="sxs-lookup"><span data-stu-id="1b065-617">Get DirectX texture processing library</span></span></td>
        <td>[<span data-ttu-id="1b065-618">DirectXTex</span><span class="sxs-lookup"><span data-stu-id="1b065-618">DirectXTex</span></span>](http://go.microsoft.com/fwlink/?LinkId=248926)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-619">DirectXMesh-Geometrieverarbeitungsbibliothek herunterladen</span><span class="sxs-lookup"><span data-stu-id="1b065-619">Get DirectXMesh geometry processing library</span></span></td>
        <td>[<span data-ttu-id="1b065-620">DirectXMesh</span><span class="sxs-lookup"><span data-stu-id="1b065-620">DirectXMesh</span></span>](http://go.microsoft.com/fwlink/?LinkID=324981)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-621">UVAtlas zum Erstellen und Verpacken des isoChart-Texturatlas herunterladen</span><span class="sxs-lookup"><span data-stu-id="1b065-621">Get UVAtlas for creating and packing isochart texture atlas</span></span></td>
        <td>[<span data-ttu-id="1b065-622">UVAtlas</span><span class="sxs-lookup"><span data-stu-id="1b065-622">UVAtlas</span></span>](http://go.microsoft.com/fwlink/?LinkID=512686)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-623">DirectXMath-Bibliothek herunterladen</span><span class="sxs-lookup"><span data-stu-id="1b065-623">Get the DirectXMath library</span></span></td>
        <td>[<span data-ttu-id="1b065-624">DirectXMath</span><span class="sxs-lookup"><span data-stu-id="1b065-624">DirectXMath</span></span>](http://go.microsoft.com/fwlink/?LinkID=615560)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-625">Direct3D12-Unterstützung im DirectXTK (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="1b065-625">Direct3D 12 support in the DirectXTK (blog post)</span></span></td>
        <td>[<span data-ttu-id="1b065-626">Unterstützung für DirectX12</span><span class="sxs-lookup"><span data-stu-id="1b065-626">Support for DirectX 12</span></span>](https://github.com/Microsoft/DirectXTK/issues/2)</td>
    </tr>
</table>

#### <a name="directx-resources-from-partners"></a><span data-ttu-id="1b065-627">DirectX-Ressourcen von Partnern</span><span class="sxs-lookup"><span data-stu-id="1b065-627">DirectX resources from partners</span></span>

<span data-ttu-id="1b065-628">Dies sind einige zusätzliche DirectX-Dokumentationen, die von externen Partnern erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="1b065-628">These are some additional DirectX documentation created by external partners.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-629">Nvidia: Empfohlene und nicht empfohlene Vorgehensweisen für DX12 (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="1b065-629">Nvidia: DX12 Do's and Don'ts (blog post)</span></span> </td>
        <td>[<span data-ttu-id="1b065-630">DirectX12 auf Nvidia-GPUs</span><span class="sxs-lookup"><span data-stu-id="1b065-630">DirectX 12 on Nvidia GPUs</span></span>](https://developer.nvidia.com/dx12-dos-and-donts-updated)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-631">Intel: Effizientes Rendering mit DirectX12</span><span class="sxs-lookup"><span data-stu-id="1b065-631">Intel: Efficient rendering with DirectX 12</span></span></td>
        <td>[<span data-ttu-id="1b065-632">DirectX12-Rendering auf Intel-Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="1b065-632">DirectX 12 rendering on Intel Graphics</span></span>](https://software.intel.com/sites/default/files/managed/4a/38/Efficient-Rendering-with-DirectX-12-on-Intel-Graphics.pdf)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-633">Intel: Mehrfachadapterunterstützung in DirectX12</span><span class="sxs-lookup"><span data-stu-id="1b065-633">Intel: Multi adapter support in DirectX 12</span></span></td>
        <td>[<span data-ttu-id="1b065-634">Implementieren einer expliziten Mehrfachadapteranwendung mit DirectX12</span><span class="sxs-lookup"><span data-stu-id="1b065-634">How to implement an explicit multi-adapter application using DirectX 12</span></span>](https://software.intel.com/articles/multi-adapter-support-in-directx-12)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-635">Intel: DirectX12-Lernprogramm</span><span class="sxs-lookup"><span data-stu-id="1b065-635">Intel: DirectX 12 tutorial</span></span></td>
        <td>[<span data-ttu-id="1b065-636">Gemeinsames Whitepaper von Intel, Suzhou Snail und Microsoft</span><span class="sxs-lookup"><span data-stu-id="1b065-636">Collaborative white paper by Intel, Suzhou Snail and Microsoft</span></span>](https://software.intel.com/articles/tutorial-migrating-your-apps-to-directx-12-part-1)</td>
    </tr>
</table>


## <a name="production"></a><span data-ttu-id="1b065-637">Produktion</span><span class="sxs-lookup"><span data-stu-id="1b065-637">Production</span></span>


<span data-ttu-id="1b065-638">Ihr Studio ist jetzt vollständig eingebunden und beginnt mit dem Produktionszyklus, wobei die Arbeiten auf die einzelnen Teammitglieder aufgeteilt werden.</span><span class="sxs-lookup"><span data-stu-id="1b065-638">Your studio is now fully engaged and moving into the production cycle, with work distributed throughout your team.</span></span> <span data-ttu-id="1b065-639">Der Prototyp wird optimiert, überarbeitet und erweitert, um ein vollständiges Spiel zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1b065-639">You're polishing, refactoring, and extending the prototype to craft it into a full game.</span></span>

### <a name="notifications-and-live-tiles"></a><span data-ttu-id="1b065-640">Benachrichtigungen und Live-Kacheln</span><span class="sxs-lookup"><span data-stu-id="1b065-640">Notifications and live tiles</span></span>

<span data-ttu-id="1b065-641">Ihr Spiel wird im Menü „Start“ durch eine Kachel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1b065-641">A tile is your game's representation on the Start Menu.</span></span> <span data-ttu-id="1b065-642">Über Kacheln und Benachrichtigungen können Sie das Interesse von Spielern wecken, auch wenn diese das Spiel gerade gar nicht spielen.</span><span class="sxs-lookup"><span data-stu-id="1b065-642">Tiles and notifications can drive player interest even when they aren't currently playing your game.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-643">Entwickeln von Kacheln und Signalen</span><span class="sxs-lookup"><span data-stu-id="1b065-643">Developing tiles and badges</span></span></td>
        <td>[<span data-ttu-id="1b065-644">Kacheln, Badges und Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="1b065-644">Tiles, badges, and notifications</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185606)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-645">Beispiel zur Veranschaulichung von Live-Kacheln und Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="1b065-645">Sample illustrating live tiles and notifications</span></span></td>
        <td>[<span data-ttu-id="1b065-646">Benachrichtigungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="1b065-646">Notifications sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-647">Vorlagen für adaptive Kacheln (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="1b065-647">Adaptive tile templates (blog post)</span></span></td>
        <td>[<span data-ttu-id="1b065-648">Vorlagen für adaptive Kacheln – Schema und Dokumentation</span><span class="sxs-lookup"><span data-stu-id="1b065-648">Adaptive Tile Templates - Schema and Documentation</span></span>](http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/06/30/adaptive-tile-templates-schema-and-documentation.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-649">Gestalten von Kacheln und Signalen</span><span class="sxs-lookup"><span data-stu-id="1b065-649">Designing tiles and badges</span></span></td>
        <td>[<span data-ttu-id="1b065-650">Richtlinien für Kacheln und Signale</span><span class="sxs-lookup"><span data-stu-id="1b065-650">Guidelines for tiles and badges</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465403)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-651">Windows10-App für die interaktive Entwicklung von Vorlagen für Live-Kacheln</span><span class="sxs-lookup"><span data-stu-id="1b065-651">Windows 10 app for interactively developing live tile templates</span></span></td>
        <td>[<span data-ttu-id="1b065-652">Notifications Visualizer</span><span class="sxs-lookup"><span data-stu-id="1b065-652">Notifications Visualizer</span></span>](https://www.microsoft.com/store/apps/9nblggh5xsl1)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-653">UWP-Erweiterung für die Generierung von Kacheln für Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b065-653">UWP Tile Generator extension for Visual Studio</span></span></td>
        <td>[<span data-ttu-id="1b065-654">Tool zum Erstellen aller erforderlichen Kacheln über ein einziges Image</span><span class="sxs-lookup"><span data-stu-id="1b065-654">Tool for creating all required tiles using single image</span></span>](https://visualstudiogallery.msdn.microsoft.com/09611e90-f3e8-44b7-9c83-18dba8275bb2)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-655">UWP-Erweiterung für die Generierung von Kacheln für Visual Studio (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="1b065-655">UWP Tile Generator extension for Visual Studio (blog post)</span></span></td>
        <td>[<span data-ttu-id="1b065-656">Tipps zum Verwenden des UWP-Tools für die Generierung von Kacheln</span><span class="sxs-lookup"><span data-stu-id="1b065-656">Tips on using the UWP Tile Generator tool</span></span>](https://blogs.windows.com/buildingapps/2016/02/15/uwp-tile-generator-extension-for-visual-studio/)</td>
    </tr>
</table>
 

### <a name="enable-in-app-product-iap-purchases"></a><span data-ttu-id="1b065-657">Unterstützen von In-App-Produktkäufen (IAP-Käufen)</span><span class="sxs-lookup"><span data-stu-id="1b065-657">Enable in-app product (IAP) purchases</span></span>

<span data-ttu-id="1b065-658">Bei einem IAP (In-App-Produkt) handelt es sich um einen zusätzlichen Artikel, den Spieler innerhalb des Spiels erwerben können.</span><span class="sxs-lookup"><span data-stu-id="1b065-658">An IAP (in-app product) is a supplementary item that players can purchase in-game.</span></span> <span data-ttu-id="1b065-659">Beispiele für IAPs sind Add-Ons, Spielelevels, Gegenstände und alles andere, was für die Spieler interessant sein könnte.</span><span class="sxs-lookup"><span data-stu-id="1b065-659">IAPs can be new add-ons, game levels, items, or anything else that your players might enjoy.</span></span> <span data-ttu-id="1b065-660">Bei richtiger Anwendung können IAPs Umsätze generieren und gleichzeitig das Spielerlebnis verbessern.</span><span class="sxs-lookup"><span data-stu-id="1b065-660">Used appropriately, IAPs can provide revenue while improving the game experience.</span></span> <span data-ttu-id="1b065-661">Die IAPs Ihres Spiels werden über das WindowsDevCenter-Dashboard definiert und veröffentlicht. Die Aktivierung von In-App-Käufen erfolgt über den Code Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="1b065-661">You define and publish your game's IAPs through the Windows Dev Center dashboard, and enable in-app purchases in your game's code.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-662">Langlebige In-App-Produkte</span><span class="sxs-lookup"><span data-stu-id="1b065-662">Durable in-app products</span></span></td>
        <td>[<span data-ttu-id="1b065-663">Unterstützen von Käufen von In-App-Produkten</span><span class="sxs-lookup"><span data-stu-id="1b065-663">Enable in-app product purchases</span></span>](https://msdn.microsoft.com/library/windows/apps/mt219684)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-664">In-App-Verbrauchsprodukte</span><span class="sxs-lookup"><span data-stu-id="1b065-664">Consumable in-app products</span></span></td>
        <td>[<span data-ttu-id="1b065-665">Käufe von konsumierbaren In-App-Produkten aktivieren</span><span class="sxs-lookup"><span data-stu-id="1b065-665">Enable consumable in-app product purchases</span></span>](https://msdn.microsoft.com/library/windows/apps/mt219683)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-666">Details zu und Einreichung von In-App-Produkten</span><span class="sxs-lookup"><span data-stu-id="1b065-666">In-app product details and submission</span></span></td>
        <td>[<span data-ttu-id="1b065-667">IAP-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="1b065-667">IAP submissions</span></span>](https://msdn.microsoft.com/library/windows/apps/mt148551)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-668">Überwachen von IAP-Verkauf und Demografie für Ihr Spiel</span><span class="sxs-lookup"><span data-stu-id="1b065-668">Monitor IAP sales and demographics for your game</span></span></td>
        <td>[<span data-ttu-id="1b065-669">Bericht zu IAP-Käufen</span><span class="sxs-lookup"><span data-stu-id="1b065-669">IAP acquisitions report</span></span>](https://msdn.microsoft.com/library/windows/apps/mt148538)</td>
    </tr>
</table>
 
### <a name="debugging-performance-optimization-and-monitoring"></a><span data-ttu-id="1b065-670">Debuggen, Leistungsoptimierung und Überwachung</span><span class="sxs-lookup"><span data-stu-id="1b065-670">Debugging, performance optimization, and monitoring</span></span>

<span data-ttu-id="1b065-671">Zur Optimierung der Leistung, nutzen Sie den Spielmodus in Windows10, um Ihren Spielern ein optimales Erlebnis durch die vollständige Nutzung der Kapazität ihrer aktuellen Hardware zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="1b065-671">To optimize performance, take advantage of Game Mode in Windows 10 to provide your gamers with the best possible gaming experience by fully utilizing the capacity of their current hardware.</span></span>

<span data-ttu-id="1b065-672">Das Windows Performance Toolkit (WPT) besteht aus Leistungsüberwachungstools, die detaillierte Leistungsprofile von Windows-Betriebssystemen und -Anwendungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="1b065-672">The Windows Performance Toolkit (WPT) consists of performance monitoring tools that produce in-depth performance profiles of Windows operating systems and applications.</span></span> <span data-ttu-id="1b065-673">Dies ist besonders hilfreich für die Überwachung der Speicherverwendung und zum Verbessern der Leistung eines Spiels.</span><span class="sxs-lookup"><span data-stu-id="1b065-673">This is especially useful for monitoring memory usage and improving game performance.</span></span> <span data-ttu-id="1b065-674">Das Windows Performance Toolkit ist im SDK für Windows 10 und im Windows ADK enthalten.</span><span class="sxs-lookup"><span data-stu-id="1b065-674">The Windows Performance Toolkit is included in the Windows 10 SDK and Windows ADK.</span></span> <span data-ttu-id="1b065-675">Dieses Toolkit besteht aus zwei unabhängigen Tools: Windows Performance Recorder (WPR) und Windows Performance Analyzer (WPA).</span><span class="sxs-lookup"><span data-stu-id="1b065-675">This toolkit consists of two independent tools: Windows Performance Recorder (WPR) and Windows Performance Analyzer (WPA).</span></span> <span data-ttu-id="1b065-676">ProcDump ist Teil von [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) und ist ein Befehlszeilenprogramm, das die Leistungsspitzen der CPU überwacht und Speicherabbilddateien während der Spielabstürze generiert.</span><span class="sxs-lookup"><span data-stu-id="1b065-676">ProcDump, which is part of [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default), is a command-line utility that monitors CPU spikes and generates dump files during game crashes.</span></span> 

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-677">Verbessern Sie die Leistung durch einen exklusiven oder prioritären Zugriff auf Hardwareressourcen mithilfe der Spielmodus-APIs</span><span class="sxs-lookup"><span data-stu-id="1b065-677">Improve performance by getting exclusive or priority access to hardware resources using Game Mode APIs</span></span></td>
        <td>[<span data-ttu-id="1b065-678">Spielmodus</span><span class="sxs-lookup"><span data-stu-id="1b065-678">Game Mode</span></span>](https://msdn.microsoft.com/library/windows/desktop/mt808808)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-679">Abrufen von Windows Performance Toolkit (WPT) aus dem Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="1b065-679">Get Windows Performance Toolkit (WPT) from Windows 10 SDK</span></span></td>
        <td>[<span data-ttu-id="1b065-680">Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="1b065-680">Windows 10 SDK</span></span>](https://developer.microsoft.com/windows/downloads/windows-10-sdk)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-681">Abrufen von Windows Performance Toolkit (WPT) aus dem Windows ADK</span><span class="sxs-lookup"><span data-stu-id="1b065-681">Get Windows Performance Toolkit (WPT) from Windows ADK</span></span></td>
        <td>[<span data-ttu-id="1b065-682">Windows ADK</span><span class="sxs-lookup"><span data-stu-id="1b065-682">Windows ADK</span></span>](https://msdn.microsoft.com/windows/hardware/dn913721.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-683">Problembehandlung bei nicht reagierender Benutzeroberfläche mit Windows Performance Analyzer (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-683">Troubleshoot unresponsible UI using Windows Performance Analyzer (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-684">Analyse des kritischen Pfads in WPA</span><span class="sxs-lookup"><span data-stu-id="1b065-684">Critical path analysis with WPA</span></span>](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-156-Critical-Path-Analysis-with-Windows-Performance-Analyzer)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-685">Diagnostizieren von Speicherverwendung und Arbeitsspeicherverlusten mit Windows Performance Recorder (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-685">Diagnose memory usage and leaks using Windows Performance Recorder (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-686">Speicherbedarf und Arbeitsspeicherverluste</span><span class="sxs-lookup"><span data-stu-id="1b065-686">Memory footprint and leaks</span></span>](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-154-Memory-Footprint-and-Leaks)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-687">Abrufen von ProcDump</span><span class="sxs-lookup"><span data-stu-id="1b065-687">Get ProcDump</span></span></td>
        <td>[<span data-ttu-id="1b065-688">ProcDump</span><span class="sxs-lookup"><span data-stu-id="1b065-688">ProcDump</span></span>](https://technet.microsoft.com/sysinternals/dd996900)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-689">Informationen zur Verwendung von ProcDump (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-689">Learn to use ProcDump (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-690">Konfigurieren von ProcDump zum Erstellen von Speicherabbilddateien</span><span class="sxs-lookup"><span data-stu-id="1b065-690">Configure ProcDump to create dump files</span></span>](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-131-Windows-10-SDK)</td>
    </tr>
</table>

### <a name="advanced-directx-techniques-and-concepts"></a><span data-ttu-id="1b065-691">Erweiterte DirectX-Techniken und -Konzepte</span><span class="sxs-lookup"><span data-stu-id="1b065-691">Advanced DirectX techniques and concepts</span></span>

<span data-ttu-id="1b065-692">Einige Aspekte der DirectX-Entwicklung können sich als differenziert und komplex erweisen.</span><span class="sxs-lookup"><span data-stu-id="1b065-692">Some portions of DirectX development can be nuanced and complex.</span></span> <span data-ttu-id="1b065-693">Wenn Sie sich im Rahmen der Produktionsphase mit den Einzelheiten des DirectX-Moduls auseinandersetzen oder komplexe Leistungsprobleme debuggen müssen, können Sie auf die Ressourcen und Informationen in diesem Abschnitt zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="1b065-693">When you get to the point in production where you need to dig down into the details of your DirectX engine, or debug difficult performance problems, the resources and information in this section can help.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-694">PIX für Windows</span><span class="sxs-lookup"><span data-stu-id="1b065-694">PIX on Windows</span></span></td>
        <td>[<span data-ttu-id="1b065-695">Leistungsoptimierungs- und -Debugg-Tools von DirectX12 für Windows</span><span class="sxs-lookup"><span data-stu-id="1b065-695">Performance tuning and debugging tool for DirectX 12 on Windows</span></span>](https://blogs.msdn.microsoft.com/pix/2017/01/17/introducing-pix-on-windows-beta/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-696">Überprüfungs- und Debugg-Tools für die Entwicklung von D3D12 (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-696">Debugging and validation tools for D3D12 development (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-697">D3D12-Leistungsoptimierung und Debuggen mit PIX und GPU-Überprüfung</span><span class="sxs-lookup"><span data-stu-id="1b065-697">D3D12 Performance Tuning and Debugging with PIX and GPU Validation</span></span>](https://channel9.msdn.com/Events/GDC/GDC-2017/GDC2017-003)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-698">Grafik- und Leistungsoptimierung (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-698">Optimizing graphics and performance (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-699">Erweiterte DirectX12-Grafiken und -Leistung</span><span class="sxs-lookup"><span data-stu-id="1b065-699">Advanced DirectX 12 Graphics and Performance</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/Advanced-DirectX12-Graphics-and-Performance)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-700">Debuggen von DirectX-Grafiken (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-700">DirectX graphics debugging (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-701">Lösen Sie komplexe Grafikprobleme in Ihrem Spiel mithilfe von DirectX-Tools.</span><span class="sxs-lookup"><span data-stu-id="1b065-701">Solve the tough graphics problems with your game using DirectX Tools</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-702">Visual Studio2015-Tools zum Debuggen von DirectX12 (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-702">Visual Studio 2015 tools for debugging DirectX 12 (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-703">DirectX-Tools für Windows10 in Visual Studio2015</span><span class="sxs-lookup"><span data-stu-id="1b065-703">DirectX tools for Windows 10 in Visual Studio 2015</span></span>](https://channel9.msdn.com/Series/ConnectOn-Demand/212)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-704">Direct3D12-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="1b065-704">Direct3D 12 programming guide</span></span></td>
        <td>[<span data-ttu-id="1b065-705">Direct3D12-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="1b065-705">Direct3D 12 Programming Guide</span></span>](https://msdn.microsoft.com/library/windows/desktop/dn903821)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-706">Kombinieren von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="1b065-706">Combining DirectX and XAML</span></span></td>
        <td>[<span data-ttu-id="1b065-707">Interoperabilität von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="1b065-707">DirectX and XAML interop</span></span>](directx-and-xaml-interop.md)</td>
    </tr>
</table>

### <a name="globalization-and-localization"></a><span data-ttu-id="1b065-708">Globalisierung und Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="1b065-708">Globalization and localization</span></span>

<span data-ttu-id="1b065-709">Entwickeln Sie Windows-Spiele für den weltweiten Markt, und erfahren Sie mehr über die internationalen Features, die in die führenden Produkte von Microsoft integriert sind.</span><span class="sxs-lookup"><span data-stu-id="1b065-709">Develop world-ready games for the Windows platform and learn about the international features built into Microsoft’s top products.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-710">Vorbereiten Ihres Spiels für den globalen Markt</span><span class="sxs-lookup"><span data-stu-id="1b065-710">Preparing your game for the global market</span></span></td>
        <td>[<span data-ttu-id="1b065-711">Richtlinien für die Entwicklung für eine weltweite Zielgruppe</span><span class="sxs-lookup"><span data-stu-id="1b065-711">Guidelines when developing for a global audience</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/mt186453.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-712">Überwinden sprachlicher, kultureller und technologischer Barrieren</span><span class="sxs-lookup"><span data-stu-id="1b065-712">Bridging languages, cultures, and technology</span></span></td>
        <td>[<span data-ttu-id="1b065-713">Onlineressource für Sprachkonventionen und Microsoft-Standardterminologie</span><span class="sxs-lookup"><span data-stu-id="1b065-713">Online resource for language conventions and standard Microsoft terminology</span></span>](http://www.microsoft.com/Language/Default.aspx)</td>
    </tr>
</table>

## <a name="submitting-and-publishing-your-game"></a><span data-ttu-id="1b065-714">Übermitteln und Veröffentlichen Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="1b065-714">Submitting and publishing your game</span></span>

<span data-ttu-id="1b065-715">Die folgenden Handbücher und Informationen sorgen für eine möglichst reibungslose Veröffentlichung und Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="1b065-715">The following guides and information help make the publishing and submission process as smooth as possible.</span></span>

### <a name="publishing"></a><span data-ttu-id="1b065-716">Publishing</span><span class="sxs-lookup"><span data-stu-id="1b065-716">Publishing</span></span>

<span data-ttu-id="1b065-717">Spielpakete werden über das neue einheitliche Windows Dev Center-Dashboard veröffentlicht und verwaltet.</span><span class="sxs-lookup"><span data-stu-id="1b065-717">You'll use the new unified Windows Dev Center dashboard to publish and manage your game packages.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-718">App-Veröffentlichung mit Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="1b065-718">Windows Dev Center app publishing</span></span></td>
        <td>[<span data-ttu-id="1b065-719">Veröffentlichen von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-719">Publish Windows apps</span></span>](https://dev.windows.com/publish)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-720">Erweiterte Veröffentlichung (GDN) über das Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="1b065-720">Windows Dev Center advanced publishing (GDN)</span></span></td>
        <td>[<span data-ttu-id="1b065-721">Handbuch zur erweiterten Veröffentlichung über das Windows Dev Center-Dashboard</span><span class="sxs-lookup"><span data-stu-id="1b065-721">Windows Dev Center Dashboard advanced publishing guide</span></span>](https://developer.xboxlive.com/en-us/windows/documentation/Pages/home.aspx)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-722">Sie können mit Azure Active Directory (AAD) Ihrem Dev Center-Konto Benutzer hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1b065-722">Use Azure Active Directory (AAD) to add users to your Dev Center account</span></span></td>
        <td>[<span data-ttu-id="1b065-723">Verwalten von Kontobenutzern</span><span class="sxs-lookup"><span data-stu-id="1b065-723">Manage account users</span></span>](https://docs.microsoft.com/windows/uwp/publish/manage-account-users)</td>
    </tr>   
    <tr>
        <td><span data-ttu-id="1b065-724">Bewertung des Spiels (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="1b065-724">Rating your game (blog post)</span></span></td>
        <td>[<span data-ttu-id="1b065-725">Einzelner Workflow zum Zuweisen von Altersfreigaben mit IARC-System</span><span class="sxs-lookup"><span data-stu-id="1b065-725">Single workflow to assign age ratings using IARC system</span></span>](https://blogs.windows.com/buildingapps/2016/01/06/now-available-single-age-rating-system-to-simplify-app-submissions/)</td>
    </tr>
</table>

#### <a name="packaging-and-uploading"></a><span data-ttu-id="1b065-726">Packen und Hochladen</span><span class="sxs-lookup"><span data-stu-id="1b065-726">Packaging and uploading</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-727">Informationen zur Verwendung der Streaming-Installation und optionale Pakete (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-727">Learn to use streaming install and optional packages (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-728">Nextgen UWP-App-Verteilung: Erstellen erweiterbarer, komponentenbasierte Apps für das Streamen</span><span class="sxs-lookup"><span data-stu-id="1b065-728">Nextgen UWP app distribution: Building extensible, stream-able, componentized apps</span></span>](https://channel9.msdn.com/Events/Build/2017/B8093)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-729">Unterteilen und Gruppieren zum Aktivieren von Inhalten für die Streaming-Installation</span><span class="sxs-lookup"><span data-stu-id="1b065-729">Divide and group content to enable streaming install</span></span></td>
        <td>[<span data-ttu-id="1b065-730">UWP-App-Streaming installieren</span><span class="sxs-lookup"><span data-stu-id="1b065-730">UWP App Streaming install</span></span>](../packaging/streaming-install.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-731">Optionale Pakete wie DLC-Spielinhalte erstellen</span><span class="sxs-lookup"><span data-stu-id="1b065-731">Create optional packages like DLC game content</span></span></td>
        <td>[<span data-ttu-id="1b065-732">Optionale Pakete und die Erstellung zugehöriger Sets</span><span class="sxs-lookup"><span data-stu-id="1b065-732">Optional packages and related set authoring</span></span>](../packaging/optional-packages.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-733">Packen Ihres UWP-Spiels</span><span class="sxs-lookup"><span data-stu-id="1b065-733">Package your UWP game</span></span></td>
        <td>[<span data-ttu-id="1b065-734">Verpacken von Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-734">Packaging apps</span></span>](../packaging/index.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-735">Packen Ihres UWP-DirectX-Spiels</span><span class="sxs-lookup"><span data-stu-id="1b065-735">Package your UWP DirectX game</span></span></td>
        <td>[<span data-ttu-id="1b065-736">Packen Ihres UWP-DirectX-Spiels</span><span class="sxs-lookup"><span data-stu-id="1b065-736">Package your UWP DirectX game</span></span>](package-your-windows-store-directx-game.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-737">Packen Ihres Spiels als Drittentwickler (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="1b065-737">Packaging your game as a 3rd party developer (blog post)</span></span></td>
        <td>[<span data-ttu-id="1b065-738">Erstellen von hochladbaren Paketen ohne Zugriff auf das Store-Konto des Veröffentlichers</span><span class="sxs-lookup"><span data-stu-id="1b065-738">Create uploadable packages without publisher's store account access</span></span>](https://blogs.windows.com/buildingapps/2015/12/15/building-an-app-for-a-3rd-party-how-to-package-their-store-app/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-739">Erstellen von App-Paketen und App-Paketbündeln mit MakeAppx</span><span class="sxs-lookup"><span data-stu-id="1b065-739">Creating app packages and app package bundles using MakeAppx</span></span></td>
        <td>[<span data-ttu-id="1b065-740">Erstellen von Paketen mit dem App-Verpackungsprogramm MakeAppx.exe</span><span class="sxs-lookup"><span data-stu-id="1b065-740">Create packages using app packager tool MakeAppx.exe</span></span>](https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-741">Digitales Signieren Ihrer Dateien mithilfe von SignTool</span><span class="sxs-lookup"><span data-stu-id="1b065-741">Signing your files digitally using SignTool</span></span></td>
        <td>[<span data-ttu-id="1b065-742">Signieren von Dateien und Überprüfen von Signaturen in Dateien mithilfe von SignTool</span><span class="sxs-lookup"><span data-stu-id="1b065-742">Sign files and verify signatures in files using SignTool</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa387764)</td>
    </tr>    
    <tr>
        <td><span data-ttu-id="1b065-743">Hochladen und Verwalten der Versionen Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="1b065-743">Uploading and versioning your game</span></span></td>
        <td>[<span data-ttu-id="1b065-744">Hochladen von App-Paketen</span><span class="sxs-lookup"><span data-stu-id="1b065-744">Upload app packages</span></span>](https://msdn.microsoft.com/library/windows/apps/mt148542)</td>
    </tr>
</table>


### <a name="policies-and-certification"></a><span data-ttu-id="1b065-745">Richtlinien und Zertifizierung</span><span class="sxs-lookup"><span data-stu-id="1b065-745">Policies and certification</span></span>

<span data-ttu-id="1b065-746">Stellen Sie sicher, dass sich die Veröffentlichung Ihres Spiels nicht aufgrund von Zertifizierungsproblemen verzögert.</span><span class="sxs-lookup"><span data-stu-id="1b065-746">Don't let certification issues delay your game's release.</span></span> <span data-ttu-id="1b065-747">Hier finden Sie Richtlinien und Informationen zu gängigen Zertifizierungsproblemen.</span><span class="sxs-lookup"><span data-stu-id="1b065-747">Here are policies and common certification issues to be aware of.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-748">Vereinbarung für Entwickler von WindowsStore-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-748">Windows Store App Developer Agreement</span></span></td>
        <td>[<span data-ttu-id="1b065-749">Vereinbarung für App-Entwickler</span><span class="sxs-lookup"><span data-stu-id="1b065-749">App Developer Agreement</span></span>](https://msdn.microsoft.com/library/windows/apps/hh694058)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-750">Richtlinien für die Veröffentlichung von Apps im WindowsStore</span><span class="sxs-lookup"><span data-stu-id="1b065-750">Policies for publishing apps in the Windows Store</span></span></td>
        <td>[<span data-ttu-id="1b065-751">WindowsStore-Richtlinien</span><span class="sxs-lookup"><span data-stu-id="1b065-751">Windows Store Policies</span></span>](https://msdn.microsoft.com/library/windows/apps/dn764944)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-752">So wird's gemacht: Vermeiden allgemeiner Probleme bei der App-Zertifizierung</span><span class="sxs-lookup"><span data-stu-id="1b065-752">How to avoid some common app certification issues</span></span></td>
        <td>[<span data-ttu-id="1b065-753">Vermeiden allgemeiner Zertifizierungsfehler</span><span class="sxs-lookup"><span data-stu-id="1b065-753">Avoid common certification failures</span></span>](https://msdn.microsoft.com/library/windows/apps/jj657968)</td>
    </tr>
</table>
 

### <a name="store-manifest-storemanifestxml"></a><span data-ttu-id="1b065-754">Store-Manifest („StoreManifest.xml“)</span><span class="sxs-lookup"><span data-stu-id="1b065-754">Store manifest (StoreManifest.xml)</span></span>

<span data-ttu-id="1b065-755">Das Store-Manifest („StoreManifest.xml“) ist eine optionale Konfigurationsdatei, die Sie Ihrem App-Paket hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="1b065-755">The store manifest (StoreManifest.xml) is an optional configuration file that can be included in your app package.</span></span> <span data-ttu-id="1b065-756">Das Store-Manifest bietet zusätzliche Features, die über den Umfang der Datei „AppxManifest.xml“ hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="1b065-756">The store manifest provides additional features that are not part of the AppxManifest.xml file.</span></span> <span data-ttu-id="1b065-757">So können Sie mithilfe des Store-Manifests etwa die Installation Ihres Spiels blockieren, wenn ein Zielgerät nicht über die mindestens erforderliche DirectX-Featureebene verfügt oder der verfügbare Systemspeicher nicht ausreicht.</span><span class="sxs-lookup"><span data-stu-id="1b065-757">For example, you can use the store manifest to block installation of your game if a target device doesn't have the specified minimum DirectX feature level, or the specified minimum system memory.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-758">Store-Manifest-Schema</span><span class="sxs-lookup"><span data-stu-id="1b065-758">Store manifest schema</span></span></td>
        <td>[<span data-ttu-id="1b065-759">StoreManifest-Schema (Windows10)</span><span class="sxs-lookup"><span data-stu-id="1b065-759">StoreManifest schema (Windows 10)</span></span>](https://msdn.microsoft.com/library/windows/apps/mt617335)</td>
    </tr>
</table>
 

## <a name="game-lifecycle-management"></a><span data-ttu-id="1b065-760">Spiellebenszyklusverwaltung</span><span class="sxs-lookup"><span data-stu-id="1b065-760">Game lifecycle management</span></span>


<span data-ttu-id="1b065-761">Wer glaubt, sich nach dem Abschluss der Entwicklung und der Auslieferung eines Spiels entspannt zurücklehnen zu können, irrt:</span><span class="sxs-lookup"><span data-stu-id="1b065-761">After you've finished development and shipped your game, it's not "game over".</span></span> <span data-ttu-id="1b065-762">Die Entwicklung von Version1 mag zwar abgeschlossen sein, die Marktphase Ihres Spiels hat jedoch gerade erst begonnen.</span><span class="sxs-lookup"><span data-stu-id="1b065-762">You may be done with development on version one, but your game's journey in the marketplace has only just begun.</span></span> <span data-ttu-id="1b065-763">Sie sollten Verwendung und Fehlerberichte überwachen, auf Benutzerfeedback reagieren und Updates für Ihr Spiel veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="1b065-763">You'll want to monitor usage and error reporting, respond to user feedback, and publish updates to your game.</span></span>

### <a name="windows-dev-center-analytics-and-promotion"></a><span data-ttu-id="1b065-764">Windows Dev Center-Analysen und Werbung</span><span class="sxs-lookup"><span data-stu-id="1b065-764">Windows Dev Center analytics and promotion</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-765">DevCenter-App</span><span class="sxs-lookup"><span data-stu-id="1b065-765">Dev Center App</span></span></td>
        <td>[<span data-ttu-id="1b065-766">Dev Center-App unter Windows10 zum Anzeigen Ihrer veröffentlichten Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-766">Dev Center Windows 10 app to view performance of your published apps</span></span>](https://www.microsoft.com/store/apps/dev-center/9nblggh4r5ws)</td>
    </tr>  
    <tr>
        <td><span data-ttu-id="1b065-767">Windows Dev Center-Analysen</span><span class="sxs-lookup"><span data-stu-id="1b065-767">Windows Dev Center analytics</span></span></td>
        <td>[<span data-ttu-id="1b065-768">Analysen</span><span class="sxs-lookup"><span data-stu-id="1b065-768">Analytics</span></span>](https://msdn.microsoft.com/library/windows/apps/mt148522)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-769">Reagieren auf Kundenrezensionen</span><span class="sxs-lookup"><span data-stu-id="1b065-769">Responding to customer reviews</span></span></td>
        <td>[<span data-ttu-id="1b065-770">Reagieren auf Kundenrezensionen</span><span class="sxs-lookup"><span data-stu-id="1b065-770">Respond to customer reviews</span></span>](https://msdn.microsoft.com/library/windows/apps/mt148546)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-771">Werbemöglichkeiten für Ihr Spiel</span><span class="sxs-lookup"><span data-stu-id="1b065-771">Ways to promote your game</span></span></td>
        <td>[<span data-ttu-id="1b065-772">Bewerben Ihrer Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-772">Promote your apps</span></span>](https://dev.windows.com/store-promotion)</td>
    </tr>
</table>
 

### <a name="visual-studio-application-insights"></a><span data-ttu-id="1b065-773">Visual Studio Application Insights</span><span class="sxs-lookup"><span data-stu-id="1b065-773">Visual Studio Application Insights</span></span>

<span data-ttu-id="1b065-774">Visual Studio Application Insights bietet Leistungs-, Telemetrie- und Verwendungsanalysen für Ihr veröffentlichtes Spiel.</span><span class="sxs-lookup"><span data-stu-id="1b065-774">Visual Studio Application Insights provides performance, telemetry, and usage analytics for your published game.</span></span> <span data-ttu-id="1b065-775">Application Insights unterstützt Sie nach der Veröffentlichung Ihres Spiels beim Erkennen und Beheben von Problemen sowie bei der kontinuierlichen Überwachung und Optimierung der Verwendung und beim Nachvollziehen der weiteren Spielerinteraktionen mit Ihrem Spiel.</span><span class="sxs-lookup"><span data-stu-id="1b065-775">Application Insights helps you detect and solve issues after your game is released, continuously monitor and improve usage, and understand how players are continuing to interact with your game.</span></span> <span data-ttu-id="1b065-776">Application Insights fügt Ihrer App ein SDK hinzu, das Telemetriedaten an das [Azure-Portal](http://portal.azure.com/) übermittelt.</span><span class="sxs-lookup"><span data-stu-id="1b065-776">Application Insights works by adding an SDK into your app, which sends telemetry to the [Azure portal](http://portal.azure.com/).</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-777">Analyse von Anwendungsleistung und -verwendung</span><span class="sxs-lookup"><span data-stu-id="1b065-777">Application performance and usage analytics</span></span></td>
        <td>[<span data-ttu-id="1b065-778">Visual Studio Application Insights</span><span class="sxs-lookup"><span data-stu-id="1b065-778">Visual Studio Application Insights</span></span>](https://azure.microsoft.com/documentation/articles/app-insights-get-started/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-779">Aktivieren von Application Insights in Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-779">Enable Application Insights in Windows apps</span></span></td>
        <td>[<span data-ttu-id="1b065-780">Application Insights für Windows Phone- und Windows Store-Apps</span><span class="sxs-lookup"><span data-stu-id="1b065-780">Application Insights for Windows Phone and Store apps</span></span>](https://azure.microsoft.com/documentation/articles/app-insights-windows-get-started/)</td>
    </tr>
</table>


### <a name="third-party-solutions-for-analytics-and-promotion"></a><span data-ttu-id="1b065-781">Lösungen von Drittanbietern für Analysen und Werbung</span><span class="sxs-lookup"><span data-stu-id="1b065-781">Third party solutions for analytics and promotion</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-782">Verstehen der Spielerverhalten mit GameAnalytics</span><span class="sxs-lookup"><span data-stu-id="1b065-782">Understand player behavior using GameAnalytics</span></span></td>
        <td>[<span data-ttu-id="1b065-783">GameAnalytics</span><span class="sxs-lookup"><span data-stu-id="1b065-783">GameAnalytics</span></span>](http://www.gameanalytics.com/)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-784">Verbinden Sie Ihr UWP-Spiel mit Google Analytics</span><span class="sxs-lookup"><span data-stu-id="1b065-784">Connect your UWP game to Google Analytics</span></span></td>
        <td>[<span data-ttu-id="1b065-785">Holen Sie sich Windows SDK für Google Analytics</span><span class="sxs-lookup"><span data-stu-id="1b065-785">Get Windows SDK for Google Analytics</span></span>](https://github.com/dotnet/windows-sdk-for-google-analytics)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-786">Hier erfahren Sie, wie Sie Windows SDK für Google Analytics (Video) verwenden</span><span class="sxs-lookup"><span data-stu-id="1b065-786">Learn how to use Windows SDK for Google Analytics (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-787">Erste Schritte mit Windows SDK für Google Analytics</span><span class="sxs-lookup"><span data-stu-id="1b065-787">Getting started with Windows SDK for Google Analytics</span></span>](https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Creators-Update/Getting-started-with-the-Windows-SDK-for-Google-Analytics)</td>
    </tr>    
    <tr>
        <td><span data-ttu-id="1b065-788">Verwenden der Facebook-App zum Installieren von Anzeigen, bietet Werbemöglichkeiten für Ihr Spiel für Facebook-Benutzer an</span><span class="sxs-lookup"><span data-stu-id="1b065-788">Use Facebook App Installs Ads to promote your game to Facebook users</span></span></td>
        <td>[<span data-ttu-id="1b065-789">Holen Sie sich Windows SDK für Facebook</span><span class="sxs-lookup"><span data-stu-id="1b065-789">Get Windows SDK for Facebook</span></span>](https://github.com/Microsoft/winsdkfb)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-790">Hier erfahren Sie, wie Sie die Facebook-App zum Installieren von Anzeigen verwenden (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-790">Learn how to use Facebook App Installs Ads (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-791">Erste Schritte mit Windows SDK für Facebook</span><span class="sxs-lookup"><span data-stu-id="1b065-791">Getting started with Windows SDK for Facebook</span></span>](https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Creators-Update/Getting-started-with-Facebook-App-Install-Ads)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-792">Verwenden von Vungle, um Ihren Spielen Videoanzeigen hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="1b065-792">Use Vungle to add video ads into your games</span></span></td>
        <td>[<span data-ttu-id="1b065-793">WindowsSDK für Vungle herunterladen</span><span class="sxs-lookup"><span data-stu-id="1b065-793">Get Windows SDK for Vungle</span></span>](https://v.vungle.com/sdk)</td>
    </tr>
</table>
 

### <a name="creating-and-managing-content-updates"></a><span data-ttu-id="1b065-794">Erstellen und Verwalten von Inhaltsaktualisierungen</span><span class="sxs-lookup"><span data-stu-id="1b065-794">Creating and managing content updates</span></span>

<span data-ttu-id="1b065-795">Zum Aktualisieren Ihres veröffentlichten Spiels übermitteln Sie ein neues App-Paket mit einer höheren Versionsnummer.</span><span class="sxs-lookup"><span data-stu-id="1b065-795">To update your published game, submit a new app package with a higher version number.</span></span> <span data-ttu-id="1b065-796">Nachdem das Paket den Übermittlungs- und Zertifizierungsprozess durchlaufen hat, wird es für die Kunden automatisch als Update verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1b065-796">After the package makes its way through submission and certification, it will automatically be available to customers as an update.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-797">Aktualisieren und Verwalten der Versionen Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="1b065-797">Updating and versioning your game</span></span></td>
        <td>[<span data-ttu-id="1b065-798">Paketversionsnummern</span><span class="sxs-lookup"><span data-stu-id="1b065-798">Package version numbering</span></span>](https://msdn.microsoft.com/library/windows/apps/mt188602)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-799">Leitfaden für die Spielpaketverwaltung</span><span class="sxs-lookup"><span data-stu-id="1b065-799">Game package management guidance</span></span></td>
        <td>[<span data-ttu-id="1b065-800">Leitfaden für die App-Paketverwaltung</span><span class="sxs-lookup"><span data-stu-id="1b065-800">Guidance for app package management</span></span>](https://msdn.microsoft.com/library/windows/apps/mt188602)</td>
    </tr>
</table>


## <a name="adding-xbox-live-to-your-game"></a><span data-ttu-id="1b065-801">Hinzufügen von Xbox Live zu Ihrem Spiel</span><span class="sxs-lookup"><span data-stu-id="1b065-801">Adding Xbox Live to your game</span></span>

> <span data-ttu-id="1b065-802">**Hinweis:** Wenn Sie Xbox Live aktivierte Titel entwickeln möchten, stehen Ihnen verschiedene Optionen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1b065-802">**Note**   If you would like to develop Xbox Live enabled titles, there are several options are available to you.</span></span> <span data-ttu-id="1b065-803">Informationen zu den verschiedenen Programmen finden Sie unter [Übersicht über das Entwickler-Programm](../xbox-live/developer-program-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b065-803">For info about the various programs, see [Developer program overview](../xbox-live/developer-program-overview.md).</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-804">Xbox Live – Übersicht</span><span class="sxs-lookup"><span data-stu-id="1b065-804">Xbox Live overview</span></span></td>
        <td>[<span data-ttu-id="1b065-805">Xbox Live – Entwicklerhandbuch</span><span class="sxs-lookup"><span data-stu-id="1b065-805">Xbox Live developer guide</span></span>](../xbox-live/index.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-806">Verstehen, welche Features je nach Programm verfügbar sind</span><span class="sxs-lookup"><span data-stu-id="1b065-806">Understand which features are available depending on program</span></span></td>
        <td>[<span data-ttu-id="1b065-807">Übersicht über das Entwickler-Programm: Tabelle der Features</span><span class="sxs-lookup"><span data-stu-id="1b065-807">Developer program overview: Feature table</span></span>](../xbox-live/developer-program-overview.md#feature-table)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-808">Erfahren Sie, wie Sie Informationen über Xbox Live-Dienste abrufen</span><span class="sxs-lookup"><span data-stu-id="1b065-808">Learn how to get info from Xbox Live services</span></span></td>
        <td>[<span data-ttu-id="1b065-809">Einführung in Xbox Live APIs</span><span class="sxs-lookup"><span data-stu-id="1b065-809">Introduction to Xbox Live APIs</span></span>](../xbox-live/introduction-to-xbox-live-apis.md)</td>
    </tr>
</table>


### <a name="for-developers-in-the-xbox-live-creators-program"></a><span data-ttu-id="1b065-810">Für Entwickler im Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="1b065-810">For developers in the Xbox Live Creators Program</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-811">Übersicht</span><span class="sxs-lookup"><span data-stu-id="1b065-811">Overview</span></span></td>
        <td>[<span data-ttu-id="1b065-812">Erste Schritte – Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="1b065-812">Get started with the Xbox Live Creators Program</span></span>](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-813">Hinzufügen von Xbox Live zu Ihrem Spiel</span><span class="sxs-lookup"><span data-stu-id="1b065-813">Add Xbox Live to your game</span></span></td>
        <td>[<span data-ttu-id="1b065-814">Schrittweise Anleitung zur Integration mit dem Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="1b065-814">Step by step guide to integrate Xbox Live Creators program</span></span>](../xbox-live/get-started-with-creators/creators-step-by-step-guide.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-815">Hinzufügen von Xbox Live zu Ihrem UWP-Spiel, das mit Unity erstellt wurde</span><span class="sxs-lookup"><span data-stu-id="1b065-815">Add Xbox Live to your UWP game created using Unity</span></span></td>
        <td>[<span data-ttu-id="1b065-816">Erste Schritte bei der Entwicklung eines Titels im Xbox Live Creators-Programm mit der Unity-Spielengine</span><span class="sxs-lookup"><span data-stu-id="1b065-816">Get started developing an Xbox Live Creators Program title with the Unity game engine</span></span>](../xbox-live/get-started-with-creators/develop-creators-title-with-unity.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-817">Enthält Informationen zum Integrieren von plattformübergreifenden Xbox Live-Umgebungen in UWP-Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-817">Learn how to integrate cross-platform Xbox Live experiences in UWP games (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-818">Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="1b065-818">Xbox Live Creators Program</span></span>](https://channel9.msdn.com/Events/GDC/GDC-2017/GDC2017-005)</td>
    </tr>
</table>

### <a name="for-managed-partners-and-developers-in-the-idxbox-program"></a><span data-ttu-id="1b065-819">Für verwaltete Partner und Entwickler im ID@Xbox-Programm</span><span class="sxs-lookup"><span data-stu-id="1b065-819">For managed partners and developers in the ID@Xbox program</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-820">Übersicht</span><span class="sxs-lookup"><span data-stu-id="1b065-820">Overview</span></span></td>
        <td>[<span data-ttu-id="1b065-821">Erste Schritte mit Xbox Live als verwalteter Partner oder ID-Entwickler</span><span class="sxs-lookup"><span data-stu-id="1b065-821">Get started with Xbox Live as a managed partner or an ID developer</span></span>](../xbox-live/get-started-with-partner/get-started-with-xbox-live-partner.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-822">Hinzufügen von Xbox Live zu Ihrem Spiel</span><span class="sxs-lookup"><span data-stu-id="1b065-822">Add Xbox Live to your game</span></span></td>
        <td>[<span data-ttu-id="1b065-823">Schrittweise Anleitung zum Integrieren von Xbox Live für verwaltete Partner und ID Mitglieder</span><span class="sxs-lookup"><span data-stu-id="1b065-823">Step by step guide to integrate Xbox Live for managed partners and ID members</span></span>](../xbox-live/get-started-with-partner/partners-step-by-step-guide.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-824">Hinzufügen von Xbox Live zu Ihrem UWP-Spiel, das mit Unity erstellt wurde</span><span class="sxs-lookup"><span data-stu-id="1b065-824">Add Xbox Live to your UWP game created using Unity</span></span></td>
        <td>[<span data-ttu-id="1b065-825">Hinzufügen von Xbox Live-Unterstützung zu Unity für UWP mit IL2CPP Scripting-Back-End für ID- und verwaltete Partner</span><span class="sxs-lookup"><span data-stu-id="1b065-825">Add Xbox Live support to Unity for UWP with IL2CPP scripting backend for ID and managed partners</span></span>](../xbox-live/get-started-with-partner/partner-unity-uwp-il2cpp.md)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-826">Anforderungen für Spiele mit Xbox Live (GDN)</span><span class="sxs-lookup"><span data-stu-id="1b065-826">Requirements for games that use Xbox Live (GDN)</span></span></td>
        <td>[<span data-ttu-id="1b065-827">Xbox-Anforderungen für Xbox Live unter Windows 10</span><span class="sxs-lookup"><span data-stu-id="1b065-827">Xbox Requirements for Xbox Live on Windows 10</span></span>](http://go.microsoft.com/fwlink/?LinkId=533217)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-828">Übersicht über die Entwicklung von Spielen mit Xbox Live (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-828">Overview of Xbox Live game development (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-829">Entwickeln mit Xbox Live für Windows10</span><span class="sxs-lookup"><span data-stu-id="1b065-829">Developing with Xbox Live for Windows 10</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/Developing-with-Xbox-Live-for-Windows-10)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-830">Plattformübergreifende Spielersuche (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-830">Cross-platform matchmaking (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-831">Xbox Live Multiplayer: Einführung in die Dienste für plattformübergreifende Spielersuche und Spiele</span><span class="sxs-lookup"><span data-stu-id="1b065-831">Xbox Live Multiplayer: Introducing services for cross-platform matchmaking and gameplay</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/Xbox-Live-Multiplayer-Introducing-services-for-cross-platform-matchmaking-and-gameplay)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-832">Geräteübergreifendes Spielen in Fable Legends (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-832">Cross-device gameplay in Fable Legends (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-833">Fable Legends: Geräteübergreifendes Spielen mit Xbox Live</span><span class="sxs-lookup"><span data-stu-id="1b065-833">Fable Legends: Cross-device Gameplay with Xbox Live</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/Fable-Legends-Cross-device-Gameplay-with-Xbox-Live)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-834">Xbox Live und Erfolge (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-834">Xbox Live stats and achievements (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-835">Bewährte Methoden für die Nutzung von cloudbasierten Benutzerstatistiken und Erfolgen in Xbox Live</span><span class="sxs-lookup"><span data-stu-id="1b065-835">Best Practices for Leveraging Cloud-Based User Stats and Achievements in Xbox Live</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/Best-Practices-for-Leveraging-Cloud-Based-User-Stats-and-Achievements-in-Xbox-Live)</td>
    </tr>
</table>


## <a name="additional-resources"></a><span data-ttu-id="1b065-836">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="1b065-836">Additional resources</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b065-837">Entwicklung von Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-837">Game development videos</span></span></td>
        <td>[<span data-ttu-id="1b065-838">Videos von wichtigen Konferenzen wie GDC und //Build</span><span class="sxs-lookup"><span data-stu-id="1b065-838">Videos from major conferences like GDC and //build</span></span>](https://docs.microsoft.com/windows/uwp/gaming/game-development-videos)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-839">Entwicklung von Indie-Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-839">Indie game development (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-840">Neue Möglichkeiten für unabhängige Entwickler</span><span class="sxs-lookup"><span data-stu-id="1b065-840">New Opportunities for Independent Developers</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/New-Opportunities-for-Independent-Developers)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-841">Überlegungen für mobile Multi-Core-Geräte (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-841">Considerations for multi-core mobile devices (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-842">Kontinuierlich hohe Spieleleistung auf mobilen Multi-Core-Geräten</span><span class="sxs-lookup"><span data-stu-id="1b065-842">Sustained Gaming Performance in multi-core mobile devices</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/Sustained-gaming-performance-in-multi-core-mobile-devices)</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b065-843">Entwickeln von Windows10-Desktopspielen (Video)</span><span class="sxs-lookup"><span data-stu-id="1b065-843">Developing Windows 10 desktop games (video)</span></span></td>
        <td>[<span data-ttu-id="1b065-844">PC-Spiele für Windows10</span><span class="sxs-lookup"><span data-stu-id="1b065-844">PC Games for Windows 10</span></span>](http://channel9.msdn.com/Events/GDC/GDC-2015/PC-Games-for-Windows-10)</td>
    </tr>
</table>



 

 

 
