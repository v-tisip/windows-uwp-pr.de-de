---
author: joannaleecy
title: Handbuch zur Entwicklung von Spielen unter Windows10
description: Ein umfassender Leitfaden mit Ressourcen und Informationen zur Entwicklung von Spielen für die universelle Windows-Plattform (UWP).
ms.assetid: 6061F498-96A8-44EF-9711-68AE5A1218C9
ms.author: joanlee
ms.date: 04/16/2018
ms.topic: article
keywords: Windows10, Uwp, Spiele, Entwickeln von Spielen
ms.localizationpriority: medium
ms.openlocfilehash: d29e647b2932e1d89247da5b91d8f836d11260d6
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5768394"
---
# <a name="windows-10-game-development-guide"></a><span data-ttu-id="55c05-104">Handbuch zur Entwicklung von Spielen unter Windows10</span><span class="sxs-lookup"><span data-stu-id="55c05-104">Windows 10 game development guide</span></span>


<span data-ttu-id="55c05-105">Willkommen beim Windows10-Handbuch für die Entwicklung von Spielen.</span><span class="sxs-lookup"><span data-stu-id="55c05-105">Welcome to the Windows 10 game development guide!</span></span>

<span data-ttu-id="55c05-106">Dieses Handbuch enthält eine umfassende Sammlung von Ressourcen und Informationen, die Sie für die Entwicklung von Spielen für die Universelle Windows-Plattform (UWP) benötigen.</span><span class="sxs-lookup"><span data-stu-id="55c05-106">This guide provides an end-to-end collection of the resources and information you'll need to develop a Universal Windows Platform (UWP) game.</span></span> <span data-ttu-id="55c05-107">Eine englische Version (USA) dieses Handbuchs steht im [PDF](http://download.microsoft.com/download/9/C/9/9C9D344F-611F-412E-BB01-259E5C76B17F/Windev_Game_Dev_Guide_Oct_2017.pdf)-Format zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="55c05-107">An English (US) version of this guide is available in [PDF](http://download.microsoft.com/download/9/C/9/9C9D344F-611F-412E-BB01-259E5C76B17F/Windev_Game_Dev_Guide_Oct_2017.pdf) format.</span></span>

## <a name="introduction-to-game-development-for-the-universal-windows-platform-uwp"></a><span data-ttu-id="55c05-108">Einführung in die Spieleentwicklung für die universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="55c05-108">Introduction to game development for the Universal Windows Platform (UWP)</span></span>


<span data-ttu-id="55c05-109">Mit einem Windows10-Spiel können Sie Millionen Smartphone-, PC- und XboxOne-Benutzer auf der ganzen Welt erreichen.</span><span class="sxs-lookup"><span data-stu-id="55c05-109">When you create a Windows 10 game, you have the opportunity to reach millions of players worldwide across phone, PC, and Xbox One.</span></span> <span data-ttu-id="55c05-110">Dank Xbox auf Windows, Xbox Live, geräteübergreifendem Multiplayer, einer tollen Spiele-Community und leistungsstarken neuen Features wie die Universelle Windows-Plattform (UWP) und DirectX12 begeistern Windows10-Spiele Spieler aller Altersklassen und Genres.</span><span class="sxs-lookup"><span data-stu-id="55c05-110">With Xbox on Windows, Xbox Live, cross-device multiplayer, an amazing gaming community, and powerful new features like the Universal Windows Platform (UWP) and DirectX 12, Windows 10 games thrill players of all ages and genres.</span></span> <span data-ttu-id="55c05-111">Die neue universelle Windows-Plattform (UWP) gewährleistet durch eine gemeinsame API für Smartphone, PC und Xbox One die geräteübergreifende Kompatibilität Ihres Spiels unter Windows10 und stellt zudem Tools und Optionen bereit, mit denen Sie Ihr Spiel optimal an die jeweilige Geräteumgebung anpassen können.</span><span class="sxs-lookup"><span data-stu-id="55c05-111">The new Universal Windows Platform (UWP) delivers compatibility for your game across Windows 10 devices with a common API for phone, PC, and Xbox One, along with tools and options to tailor your game to each device experience.</span></span>

<span data-ttu-id="55c05-112">Dieses Handbuch enthält eine umfassende Sammlung von hilfreichen Informationen und Ressourcen für die Spieleentwicklung.</span><span class="sxs-lookup"><span data-stu-id="55c05-112">This guide provides an end-to-end collection of information and resources that will help you as you develop your game.</span></span> <span data-ttu-id="55c05-113">Die Abschnittsstruktur orientiert sich an den Entwicklungsphasen und vereinfacht die Informationssuche.</span><span class="sxs-lookup"><span data-stu-id="55c05-113">The sections are organized according to the stages of game development, so you'll know where to look for information when you need it.</span></span>

<span data-ttu-id="55c05-114">Wenn Sie das Entwickeln von Spielen für Windows oder Xbox noch nicht kennen, sollten Sie möglicherweise mit dem Handbuch [Erste Schritte](getting-started.md) beginnen.</span><span class="sxs-lookup"><span data-stu-id="55c05-114">If you're new to developing games on Windows or Xbox, the [Getting Started](getting-started.md) guide may be where you want to start off.</span></span> <span data-ttu-id="55c05-115">Der Einführungsabschnitt [Ressourcen für die Spieleentwicklung](#game-development-resources) bietet ebenfalls einen allgemeinen Überblick über die Dokumentation, Programme und andere hilfreiche Ressourcen für die Spieleerstellung.</span><span class="sxs-lookup"><span data-stu-id="55c05-115">The [Game development resources](#game-development-resources) section also provides a high-level survey of documentation, programs, and other resources that are helpful when creating a game.</span></span> <span data-ttu-id="55c05-116">Wenn Sie mit dem Einblick auf UWP-Code beginnen möchten, lesen Sie [Spielbeispiele](#game-samples).</span><span class="sxs-lookup"><span data-stu-id="55c05-116">If you want to start by looking at some UWP code instead, see [Game samples](#game-samples).</span></span>

<span data-ttu-id="55c05-117">Dieses Handbuch wird bei Bedarf mit weiteren Ressourcen für die Entwicklung von Windows10-Spielen aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="55c05-117">This guide will be updated as additional Windows 10 game development resources and material become available.</span></span>

## <a name="game-development-resources"></a><span data-ttu-id="55c05-118">Ressourcen für die Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="55c05-118">Game development resources</span></span>

<span data-ttu-id="55c05-119">Von der Dokumentation bis hin zu Entwicklerprogrammen, Foren, Blogs und Beispielen steht Ihnen bei der Spieleentwicklung eine Vielzahl hilfreicher Ressourcen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="55c05-119">From documentation to developer programs, forums, blogs, and samples, there are many resources available to help you on your game development journey.</span></span> <span data-ttu-id="55c05-120">Hier finden Sie eine Zusammenfassung wichtiger Ressourcen für den Einstieg in die Entwicklung Ihres Windows 10-Spiels.</span><span class="sxs-lookup"><span data-stu-id="55c05-120">Here's a roundup of resources to know about as you begin developing your Windows 10 game.</span></span>

> [!Note]
> <span data-ttu-id="55c05-121">Einige Features werden über verschiedene Programme verwaltet.</span><span class="sxs-lookup"><span data-stu-id="55c05-121">Some features are managed through various programs.</span></span> <span data-ttu-id="55c05-122">Dieses Handbuch behandelt eine breite Palette von Ressourcen. Je nach Programmteilnahme oder spezifischer Entwicklungsrolle stehen Ihnen bestimmte Ressourcen unter Umständen nicht zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="55c05-122">This guide covers a broad range of resources, so you may find that some resources are inaccessible depending on the program you are in or your specific development role.</span></span> <span data-ttu-id="55c05-123">Beispiele wären etwa Links, die zu „developer.xboxlive.com“, „forums.xboxlive.com“, „xdi.xboxlive.com“ oder zum Netzwerk für Spieleentwickler (Game Developer Network, GDN) aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="55c05-123">Examples are links that resolve to developer.xboxlive.com, forums.xboxlive.com, xdi.xboxlive.com, or the Game Developer Network (GDN).</span></span> <span data-ttu-id="55c05-124">Informationen zur Partnerschaft mit Microsoft finden Sie unter [Entwicklerprogramme](#developer-programs).</span><span class="sxs-lookup"><span data-stu-id="55c05-124">For information about partnering with Microsoft, see [Developer Programs](#developer-programs).</span></span>


### <a name="game-development-documentation"></a><span data-ttu-id="55c05-125">Dokumentation für die Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="55c05-125">Game development documentation</span></span>

<span data-ttu-id="55c05-126">In diesem Handbuch finden Sie immer wieder direkte Links zu relevanten Dokumentationen – strukturiert nach Aufgabe, Technologie und Entwicklungsphase.</span><span class="sxs-lookup"><span data-stu-id="55c05-126">Throughout this guide, you'll find deep links to relevant documentation—organized by task, technology, and stage of game development.</span></span> <span data-ttu-id="55c05-127">Hier sehen Sie eine Übersicht über die wichtigsten verfügbaren Dokumentationsportale für die Entwicklung von Windows10-Spielen.</span><span class="sxs-lookup"><span data-stu-id="55c05-127">To give you a broad view of what's available, here are the main documentation portals for Windows 10 game development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-128">Hauptportal für Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="55c05-128">Windows Dev Center main portal</span></span></td>
        <td><a href="https://dev.windows.com"><span data-ttu-id="55c05-129">Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="55c05-129">Windows Dev Center</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-130">Entwickeln von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-130">Developing Windows apps</span></span></td>
        <td><a href="https://dev.windows.com/develop"><span data-ttu-id="55c05-131">Entwickeln von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-131">Develop Windows apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-132">Entwicklung von UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="55c05-132">Universal Windows Platform app development</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt244352"><span data-ttu-id="55c05-133">Anleitungen für Windows 10-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-133">How-to guides for Windows 10 apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-134">Anleitungen für UWP-Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-134">How-to guides for UWP games</span></span></td>
        <td><a href="index.md"><span data-ttu-id="55c05-135">Spiele und DirectX</span><span class="sxs-lookup"><span data-stu-id="55c05-135">Games and DirectX</span></span></a> </td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-136">DirectX-Referenz und -Übersichten</span><span class="sxs-lookup"><span data-stu-id="55c05-136">DirectX reference and overviews</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/ee663274"><span data-ttu-id="55c05-137">DirectX-Grafiken und -Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-137">DirectX Graphics and Gaming</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-138">Azure für Gaming</span><span class="sxs-lookup"><span data-stu-id="55c05-138">Azure for gaming</span></span></td>
        <td><a href="https://azure.microsoft.com/solutions/gaming/"><span data-ttu-id="55c05-139">Erstellen und Skalieren von Spielen mit Azure</span><span class="sxs-lookup"><span data-stu-id="55c05-139">Build and scale your games using Azure</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-140">PlayFab</span><span class="sxs-lookup"><span data-stu-id="55c05-140">PlayFab</span></span></td>
        <td><a href="https://api.playfab.com/"><span data-ttu-id="55c05-141">Vollständige Back-End-Lösung für Live-Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-141">Complete backend solution for live games</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-142">UWP auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="55c05-142">UWP on Xbox One</span></span></td>
        <td><a href="https://msdn.microsoft.com/windows/uwp/xbox-apps/index"><span data-ttu-id="55c05-143">Erstellen von UWP-Apps auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="55c05-143">Building UWP apps on Xbox One</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-144">UWP auf HoloLens</span><span class="sxs-lookup"><span data-stu-id="55c05-144">UWP on HoloLens</span></span></td>
        <td><a href="https://developer.microsoft.com/windows/mixed-reality/development_overview"><span data-ttu-id="55c05-145">Erstellen von UWP-Apps auf HoloLens</span><span class="sxs-lookup"><span data-stu-id="55c05-145">Building UWP apps on HoloLens</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-146">Xbox Live-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="55c05-146">Xbox Live documentation</span></span></td>
        <td><a href="../xbox-live/index.md"><span data-ttu-id="55c05-147">Xbox Live – Entwicklerhandbuch</span><span class="sxs-lookup"><span data-stu-id="55c05-147">Xbox Live developer guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-148">Xbox One – Entwicklerdokumentation (XGD)</span><span class="sxs-lookup"><span data-stu-id="55c05-148">Xbox One development documentation (XGD)</span></span></td>
        <td><a href="https://developer.microsoft.com/games/xbox/partner/development-home"><span data-ttu-id="55c05-149">Xbox One – Entwicklung</span><span class="sxs-lookup"><span data-stu-id="55c05-149">Xbox One Development</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-150">Xbox One – Whitepapers für Entwickler (XGD)</span><span class="sxs-lookup"><span data-stu-id="55c05-150">Xbox One development whitepapers (XGD)</span></span></td>
        <td><a href="https://developer.microsoft.com/games/xbox/partner/development-education-whitepapers"><span data-ttu-id="55c05-151">Whitepapers</span><span class="sxs-lookup"><span data-stu-id="55c05-151">White Papers</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-152">Interaktive Mixer-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="55c05-152">Mixer Interactive documentation</span></span></td>
        <td><a href="https://dev.mixer.com/reference/interactive/index.html"><span data-ttu-id="55c05-153">Fügen Sie Interaktivität zu Ihrem Spiel hinzu</span><span class="sxs-lookup"><span data-stu-id="55c05-153">Add interactivity to your game</span></span></a></td>
    </tr>        
</table>

### <a name="windows-dev-center"></a><span data-ttu-id="55c05-154">Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="55c05-154">Windows Dev Center</span></span>

<span data-ttu-id="55c05-155">Der Prozess für die Veröffentlichung Ihres Windows-Spiels beginnt mit der Registrierung eines Entwicklerkontos bei Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="55c05-155">Registering a developer account on the Windows Dev Center is the first step towards publishing your Windows game.</span></span> <span data-ttu-id="55c05-156">Mit einem Entwicklerkonto können Sie den Namen Ihres Spiels reservieren und kostenlose oder kostenpflichtige Spiele für alle Windows-Geräte an den Microsoft Store übermitteln.</span><span class="sxs-lookup"><span data-stu-id="55c05-156">A developer account lets you reserve your game's name and submit free or paid games to the Microsoft Store for all Windows devices.</span></span> <span data-ttu-id="55c05-157">Sie können Ihr Spiel und Ihre spielinternen Produkte verwalten, ausführliche Analysen abrufen und Dienste aktivieren, die Spieler auf der ganzen Welt begeistern.</span><span class="sxs-lookup"><span data-stu-id="55c05-157">Use your developer account to manage your game and in-game products, get detailed analytics, and enable services that create great experiences for your players around the world.</span></span> 

<span data-ttu-id="55c05-158">Microsoft bietet ebenfalls mehrere Entwicklerprogramme an, die Sie bei der Entwicklung und Veröffentlichung von Windows-Spielen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="55c05-158">Microsoft also offers several developer programs to help you develop and publish Windows games.</span></span> <span data-ttu-id="55c05-159">Wir empfehlen, vor dem Registrieren für ein Dev Center-Konto zu überprüfen, ob diese für Sie geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="55c05-159">We recommend seeing if any are right for you before registering for a Dev Center account.</span></span> <span data-ttu-id="55c05-160">Weitere Informationen finden Sie unter [Entwicklerprogramme](#developer-programs)</span><span class="sxs-lookup"><span data-stu-id="55c05-160">For more info, go to [Developer programs](#developer-programs)</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-161">Entwicklerkonto registrieren</span><span class="sxs-lookup"><span data-stu-id="55c05-161">Register a developer account</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/bg124287"><span data-ttu-id="55c05-162">Bereit für die Registrierung?</span><span class="sxs-lookup"><span data-stu-id="55c05-162">Ready to sign up?</span></span></a></td>
    </tr> 
</table>

### <a name="developer-programs"></a><span data-ttu-id="55c05-163">Entwicklerprogramme</span><span class="sxs-lookup"><span data-stu-id="55c05-163">Developer programs</span></span>

<span data-ttu-id="55c05-164">Microsoft bietet mehrere Entwicklerprogramme an, die Sie bei der Entwicklung und Veröffentlichung von Windows-Spielen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="55c05-164">Microsoft offers several developer programs to help you develop and publish Windows games.</span></span> <span data-ttu-id="55c05-165">Erwägen Sie, an einem Entwicklerprogramm teilzunehmen, wenn Sie Spiele für Xbox One entwickeln möchten und Xbox Live-Features in Ihrem Spiel integrieren möchten.</span><span class="sxs-lookup"><span data-stu-id="55c05-165">Consider joining a developer program if you want to develop games for Xbox One and integrate Xbox Live features in your game.</span></span> <span data-ttu-id="55c05-166">Wenn Sie ein Spiel im Microsoft Store veröffentlichen möchten, benötigen Sie ebenfalls ein Entwicklerkonto in Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="55c05-166">To publish a game in the Microsoft Store, you'll also need to create a developer account on Windows Dev Center.</span></span>

#### <a name="xbox-live-creators-program"></a><span data-ttu-id="55c05-167">Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="55c05-167">Xbox Live Creators Program</span></span>

<span data-ttu-id="55c05-168">Mit dem Xbox Live Creators-Programm kann jeder Xbox Live in seine Titel integrieren und sie auf Xbox One und Windows 10 veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="55c05-168">The Xbox Live Creators Program allows anyone to integrate Xbox Live into their title and publish to Xbox One and Windows 10.</span></span> <span data-ttu-id="55c05-169">Wir haben einen vereinfachten Zertifizierungsprozess ohne Konzeptgenehmigung außerhalb der standardmäßigen [Microsoft Store-Richtlinien](https://msdn.microsoft.com/library/windows/apps/dn764944.aspx).</span><span class="sxs-lookup"><span data-stu-id="55c05-169">There is a simplified certification process and no concept approval is required outside of the standard [Microsoft Store Policies](https://msdn.microsoft.com/library/windows/apps/dn764944.aspx).</span></span>

<span data-ttu-id="55c05-170">Sie können Ihr Spiel im Creators-Programm ohne einen dedizierten Entwicklerkit bereitstellen, entwerfen und veröffentlichen, indem Sie nur Einzelhandels-Hardware verwenden.</span><span class="sxs-lookup"><span data-stu-id="55c05-170">You can deploy, design, and publish your game in the Creators Program without a dedicated dev kit, using only retail hardware.</span></span> <span data-ttu-id="55c05-171">Laden Sie zunächst die [DEVMODE-Aktivierungs-App](https://docs.microsoft.com/windows/uwp/xbox-apps/devkit-activation) auf Ihre Xbox One.</span><span class="sxs-lookup"><span data-stu-id="55c05-171">To get started, download the [Dev Mode Activation app](https://docs.microsoft.com/windows/uwp/xbox-apps/devkit-activation) on your Xbox One.</span></span>

<span data-ttu-id="55c05-172">Treten Sie dem [ID@Xbox](http://www.xbox.com/Developers/id) bei, wenn Sie Zugriff auf weitere Xbox Live-Funktionen wünschen, dedizierte Marketing- und Entwicklungsunterstützung benötigen oder im allgemeinen Xbox One-Store vertreten sein möchten.</span><span class="sxs-lookup"><span data-stu-id="55c05-172">If you want access to even more Xbox Live capabilities, dedicated marketing and development support, and the chance to be featured in the main Xbox One store, apply to the [ID@Xbox](http://www.xbox.com/Developers/id) program.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-173">Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="55c05-173">Xbox Live Creators Program</span></span></td>
        <td><a href="https://developer.microsoft.com/games/xbox/xboxlive/creator"><span data-ttu-id="55c05-174">Erfahren Sie mehr über das Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="55c05-174">Learn more about the Xbox Live Creators Program</span></span></a></td>
    </tr>
</table>

#### <a name="idxbox"></a>ID@Xbox

<span data-ttu-id="55c05-175">Das ID@Xbox-Programm unterstützt qualifizierte Spieleentwickler bei der eigenständigen Veröffentlichung für Windows und Xbox One.</span><span class="sxs-lookup"><span data-stu-id="55c05-175">The ID@Xbox program helps qualified game developers self-publish on Windows and Xbox One.</span></span> <span data-ttu-id="55c05-176">Wenn Sie für Xbox One entwickeln oder Ihr Windows10-Spiel mit XboxLive-Features wie Gamerscore, Erfolgen und Ranglisten versehen möchten, registrieren Sie sich bei ID@Xbox.</span><span class="sxs-lookup"><span data-stu-id="55c05-176">If you want to develop for Xbox One, or add Xbox Live features like Gamerscore, achievements, and leaderboards to your Windows 10 game, sign up with ID@Xbox.</span></span> <span data-ttu-id="55c05-177">Als ID@Xbox-Entwickler erhalten Sie Zugriff auf Tools und Supportleistungen, mit denen Sie Ihrer Kreativität freien Lauf lassen und Ihren Erfolg maximieren können.</span><span class="sxs-lookup"><span data-stu-id="55c05-177">Become an ID@Xbox developer to get the tools and support you need to unleash your creativity and maximize your success.</span></span> <span data-ttu-id="55c05-178">Es wird empfohlen, die Sie sich zuerst an ID@Xbox wenden, bevor Sie ein Entwicklerkonto im Windows Dev Center registrieren.</span><span class="sxs-lookup"><span data-stu-id="55c05-178">We recommend that you apply to ID@Xbox first before registering for a developer account on Windows Dev Center.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-179">ID@Xbox Entwicklerprogramm</span><span class="sxs-lookup"><span data-stu-id="55c05-179">ID@Xbox developer program</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?LinkID=526271"><span data-ttu-id="55c05-180">Unabhängiges Entwicklerprogramm für Xbox One</span><span class="sxs-lookup"><span data-stu-id="55c05-180">Independent Developer Program for Xbox One</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-181">ID@Xbox Verbraucherwebsite</span><span class="sxs-lookup"><span data-stu-id="55c05-181">ID@Xbox consumer site</span></span></td>
        <td><a href="http://www.idatxbox.com/">ID@Xbox</a></td>
    </tr>
</table>

#### <a name="xbox-tools-and-middleware"></a><span data-ttu-id="55c05-182">Xbox-Tools und Middleware</span><span class="sxs-lookup"><span data-stu-id="55c05-182">Xbox tools and middleware</span></span>

<span data-ttu-id="55c05-183">Im Rahmen des Programms für Xbox-Tools und Middleware werden Xbox-Entwicklungskits für professionelle Entwickler von Spieletools und Middleware lizenziert.</span><span class="sxs-lookup"><span data-stu-id="55c05-183">The Xbox Tools and Middleware Program licenses Xbox development kits to professional developers of game tools and middleware.</span></span> <span data-ttu-id="55c05-184">Entwickler, die in das Programm aufgenommen werden, können ihre Xbox XDK-Technologien an andere lizenzierte Xbox-Entwickler weitergeben und vertreiben.</span><span class="sxs-lookup"><span data-stu-id="55c05-184">Developers accepted into the program can share and distribute their Xbox XDK technologies to other licensed Xbox developers.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-185">Programm für Tools und Middleware kontaktieren</span><span class="sxs-lookup"><span data-stu-id="55c05-185">Contact the tools and middleware program</span></span></td>
        <td><xboxtlsm@microsoft.com></td>
    </tr>
</table>


### <a name="game-samples"></a><span data-ttu-id="55c05-186">Beispielspiele</span><span class="sxs-lookup"><span data-stu-id="55c05-186">Game samples</span></span>

<span data-ttu-id="55c05-187">Für Windows 10-Spiele und -Apps stehen zahlreiche Beispiele zur Verfügung, die einen Eindruck von den Features von Windows 10-Spielen vermitteln und den Einstieg in die Spieleentwicklung erleichtern.</span><span class="sxs-lookup"><span data-stu-id="55c05-187">There are many Windows 10 game and app samples available to help you understand Windows 10 gaming features and get a quick start on game development.</span></span> <span data-ttu-id="55c05-188">Es werden regelmäßig weitere Beispiele entwickelt und veröffentlicht. Schauen Sie daher immer mal wieder bei den Beispielportalen vorbei.</span><span class="sxs-lookup"><span data-stu-id="55c05-188">More samples are developed and published regularly, so don't forget to occasionally check back at sample portals to see what's new.</span></span> <span data-ttu-id="55c05-189">Darüber hinaus können Sie GitHub-Repositorys [überwachen](https://help.github.com/articles/watching-repositories/), um über Änderungen und Ergänzungen informiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="55c05-189">You can also [watch](https://help.github.com/articles/watching-repositories/) GitHub repos to be notified of changes and additions.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-190">Beispiele für Universelle Windows-Plattform-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-190">Universal Windows Platform app samples</span></span></td>
        <td><a href="https://github.com/Microsoft/Windows-universal-samples"><span data-ttu-id="55c05-191">Windows-universal-samples</span><span class="sxs-lookup"><span data-stu-id="55c05-191">Windows-universal-samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-192">Grafikbeispiele für Direct3D12</span><span class="sxs-lookup"><span data-stu-id="55c05-192">Direct3D 12 graphics samples</span></span></td>
        <td><a href="https://github.com/Microsoft/DirectX-Graphics-Samples"><span data-ttu-id="55c05-193">DirectX-Grafikbeispiele</span><span class="sxs-lookup"><span data-stu-id="55c05-193">DirectX-Graphics-Samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-194">Grafikbeispiele für Direct3D11</span><span class="sxs-lookup"><span data-stu-id="55c05-194">Direct3D 11 graphics samples</span></span></td>
        <td><a href="https://github.com/walbourn/directx-sdk-samples"><span data-ttu-id="55c05-195">directx-sdk-samples</span><span class="sxs-lookup"><span data-stu-id="55c05-195">directx-sdk-samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-196">Beispiel für ein First-Person-Spiel mit Direct3D11</span><span class="sxs-lookup"><span data-stu-id="55c05-196">Direct3D 11 first-person game sample</span></span></td>
        <td><a href="tutorial--create-your-first-uwp-directx-game.md"><span data-ttu-id="55c05-197">Erstellen eines einfachen UWP-Spiels mit DirectX</span><span class="sxs-lookup"><span data-stu-id="55c05-197">Create a simple UWP game with DirectX</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-198">Beispiel für benutzerdefinierte Direct2D-Bildeffekte</span><span class="sxs-lookup"><span data-stu-id="55c05-198">Direct2D custom image effects sample</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?LinkId=620531"><span data-ttu-id="55c05-199">D2DCustomEffects</span><span class="sxs-lookup"><span data-stu-id="55c05-199">D2DCustomEffects</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-200">Beispiel für ein Direct2D-Farbverlaufsgitter</span><span class="sxs-lookup"><span data-stu-id="55c05-200">Direct2D gradient mesh sample</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?LinkId=620532"><span data-ttu-id="55c05-201">D2DGradientMesh</span><span class="sxs-lookup"><span data-stu-id="55c05-201">D2DGradientMesh</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-202">Beispiel für eine Direct2D-Fotoanpassung</span><span class="sxs-lookup"><span data-stu-id="55c05-202">Direct2D photo adjustment sample</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?LinkId=620533"><span data-ttu-id="55c05-203">D2DPhotoAdjustment</span><span class="sxs-lookup"><span data-stu-id="55c05-203">D2DPhotoAdjustment</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-204">Xbox Advanced Technology Group – öffentliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="55c05-204">Xbox Advanced Technology Group public samples</span></span></td>
        <td><a href="https://github.com/Microsoft/Xbox-ATG-Samples"><span data-ttu-id="55c05-205">Xbox-ATG-Beispiele</span><span class="sxs-lookup"><span data-stu-id="55c05-205">Xbox-ATG-Samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-206">Xbox Live-Beispiele</span><span class="sxs-lookup"><span data-stu-id="55c05-206">Xbox Live samples</span></span></td>
        <td><a href="https://github.com/Microsoft/xbox-live-samples"><span data-ttu-id="55c05-207">xbox-live-samples</span><span class="sxs-lookup"><span data-stu-id="55c05-207">xbox-live-samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-208">Beispiele für XboxOne-Spiele (XGD)</span><span class="sxs-lookup"><span data-stu-id="55c05-208">Xbox One game samples (XGD)</span></span></td>
        <td><a href="https://developer.microsoft.com/games/xbox/partner/development-education-samples"><span data-ttu-id="55c05-209">Beispiele</span><span class="sxs-lookup"><span data-stu-id="55c05-209">Samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-210">Beispiele für Windows-Spiele (MSDN Code Gallery)</span><span class="sxs-lookup"><span data-stu-id="55c05-210">Windows game samples (MSDN Code Gallery)</span></span></td>
        <td><a href="https://code.msdn.microsoft.com/windowsapps/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=game&f%5B1%5D.Type=Contributors&f%5B1%5D.Value=Microsoft&f%5B1%5D.Text=Microsoft"><span data-ttu-id="55c05-211">Beispiele für MicrosoftStore-Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-211">Microsoft Store game samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-212">Beispiel für ein Spiel mit JavaScript und 2D</span><span class="sxs-lookup"><span data-stu-id="55c05-212">JavaScript 2D game sample</span></span></td>
        <td><a href="../get-started/get-started-tutorial-game-js2d.md"><span data-ttu-id="55c05-213">Erstellen eines UWP-Spiels in JavaScript</span><span class="sxs-lookup"><span data-stu-id="55c05-213">Create a UWP game in JavaScript</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-214">Beispiel für ein Spiel mit JavaScript und 3D</span><span class="sxs-lookup"><span data-stu-id="55c05-214">JavaScript 3D game sample</span></span></td>
        <td><a href="../get-started/get-started-tutorial-game-js3d.md"><span data-ttu-id="55c05-215">Erstellen eines 3D-JavaScript-Spiels mit three.js</span><span class="sxs-lookup"><span data-stu-id="55c05-215">Creating a 3D JavaScript game using three.js</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-216">Beispiel für ein MonoGame 2D UWP-Spiel</span><span class="sxs-lookup"><span data-stu-id="55c05-216">MonoGame 2D UWP game sample</span></span></td>
        <td><a href="../get-started/get-started-tutorial-game-mg2d.md"><span data-ttu-id="55c05-217">Erstellen eines UWP-Spiels in MonoGame-2D</span><span class="sxs-lookup"><span data-stu-id="55c05-217">Create a UWP game in MonoGame 2D</span></span></a></td>
    </tr>      
</table>


### <a name="developer-forums"></a><span data-ttu-id="55c05-218">Entwicklerforen</span><span class="sxs-lookup"><span data-stu-id="55c05-218">Developer forums</span></span>

<span data-ttu-id="55c05-219">In Entwicklerforen können Entwickler Fragen zur Spieleentwicklung stellen und beantworten und sich mit anderen Spieleentwicklern austauschen.</span><span class="sxs-lookup"><span data-stu-id="55c05-219">Developer forums are a great place to ask and answer game development questions and connect with the game development community.</span></span> <span data-ttu-id="55c05-220">Darüber hinaus halten Foren häufig Lösungen für komplizierte Probleme bereit, die Entwickler bereits bewältigt haben.</span><span class="sxs-lookup"><span data-stu-id="55c05-220">Forums can also be fantastic resources for finding existing answers to difficult issues that developers have faced and solved in the past.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-221">Windows-Apps-Entwicklerforen</span><span class="sxs-lookup"><span data-stu-id="55c05-221">Windows apps developer forums</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/en-us/home?category=windowsapps"><span data-ttu-id="55c05-222">Foren für Windows Store und Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-222">Windows store and apps forums</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-223">Entwicklerforum für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-223">UWP apps developer forum</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/en-us/home?forum=wpdevelop"><span data-ttu-id="55c05-224">Entwicklung von UWP-Apps (Apps für die Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="55c05-224">Developing Universal Windows Platform apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-225">Entwicklerforen für Desktopanwendungen</span><span class="sxs-lookup"><span data-stu-id="55c05-225">Desktop applications developer forums</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/en-us/home?category=windowsdesktopdev"><span data-ttu-id="55c05-226">Foren für Windows-Desktopanwendungen</span><span class="sxs-lookup"><span data-stu-id="55c05-226">Windows desktop applications forums</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-227">Microsoft Store-Spiele mit DirectX (archivierte Forenbeiträge)</span><span class="sxs-lookup"><span data-stu-id="55c05-227">DirectX Microsoft Store games (archived forum posts)</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/vstudio/home?forum=wingameswithdirectx"><span data-ttu-id="55c05-228">Erstellen von MicrosoftStore-Spielen mit DirectX (archiviert)</span><span class="sxs-lookup"><span data-stu-id="55c05-228">Building Microsoft Store games with DirectX (archived)</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-229">Windows10-Entwicklerforen für verwaltete Partner</span><span class="sxs-lookup"><span data-stu-id="55c05-229">Windows 10 managed partner developer forums</span></span></td>
        <td><a href="http://aka.ms/win10devforums"><span data-ttu-id="55c05-230">Xbox-Entwicklerforen: Windows10</span><span class="sxs-lookup"><span data-stu-id="55c05-230">XBOX Developer Forums: Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-231">DirectX-Foren</span><span class="sxs-lookup"><span data-stu-id="55c05-231">DirectX forums</span></span></td>
        <td><a href="http://forums.directxtech.com/index.php"><span data-ttu-id="55c05-232">DirectX12-Forum</span><span class="sxs-lookup"><span data-stu-id="55c05-232">DirectX 12 forum</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-233">Azure-Plattform-Foren</span><span class="sxs-lookup"><span data-stu-id="55c05-233">Azure platform forums</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/en-us/home?category=windowsazureplatform"><span data-ttu-id="55c05-234">Azure-Forum</span><span class="sxs-lookup"><span data-stu-id="55c05-234">Azure forum</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-235">Xbox Live-Forum</span><span class="sxs-lookup"><span data-stu-id="55c05-235">Xbox Live forum</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/en-US/home?forum=xboxlivedev"><span data-ttu-id="55c05-236">Xbox Live-Entwicklerforum</span><span class="sxs-lookup"><span data-stu-id="55c05-236">Xbox Live development forum</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-237">PlayFab-Foren</span><span class="sxs-lookup"><span data-stu-id="55c05-237">PlayFab forums</span></span></td>
        <td><a href="https://community.playfab.com/index.html"><span data-ttu-id="55c05-238">PlayFab-Foren</span><span class="sxs-lookup"><span data-stu-id="55c05-238">PlayFab forums</span></span></a></td>
    </tr>
</table>


### <a name="developer-blogs"></a><span data-ttu-id="55c05-239">Entwicklerblogs</span><span class="sxs-lookup"><span data-stu-id="55c05-239">Developer blogs</span></span>

<span data-ttu-id="55c05-240">Entwicklerblogs sind eine weitere praktische Ressource für topaktuelle Informationen zur Spieleentwicklung.</span><span class="sxs-lookup"><span data-stu-id="55c05-240">Developer blogs are another great resource for the latest information about game development.</span></span> <span data-ttu-id="55c05-241">Hier finden Sie Beiträge zu neuen Features, Implementierungsdetails, bewährte Methoden, Hintergrundinformationen zur Architektur und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="55c05-241">You'll find posts about new features, implementation details, best practices, architecture background, and more.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-242">Blog „Building Apps for Windows“</span><span class="sxs-lookup"><span data-stu-id="55c05-242">Building apps for Windows blog</span></span></td>
        <td><a href="http://blogs.windows.com/buildingapps/"><span data-ttu-id="55c05-243">Building Apps for Windows</span><span class="sxs-lookup"><span data-stu-id="55c05-243">Building Apps for Windows</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-244">Windows10 (Blogbeiträge)</span><span class="sxs-lookup"><span data-stu-id="55c05-244">Windows 10 (blog posts)</span></span></td>
        <td><a href="http://blogs.windows.com/blog/tag/windows-10/"><span data-ttu-id="55c05-245">Beiträge in Windows10</span><span class="sxs-lookup"><span data-stu-id="55c05-245">Posts in Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-246">Blog des VisualStudio-Entwicklerteams</span><span class="sxs-lookup"><span data-stu-id="55c05-246">Visual Studio engineering team blog</span></span></td>
        <td><a href="http://blogs.msdn.com/b/visualstudio/"><span data-ttu-id="55c05-247">The Visual Studio Blog</span><span class="sxs-lookup"><span data-stu-id="55c05-247">The Visual Studio Blog</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-248">Blogs zu VisualStudio-Entwicklertools</span><span class="sxs-lookup"><span data-stu-id="55c05-248">Visual Studio developer tools blogs</span></span></td>
        <td><a href="http://blogs.msdn.com/b/developer-tools/"><span data-ttu-id="55c05-249">Developer Tools Blogs</span><span class="sxs-lookup"><span data-stu-id="55c05-249">Developer Tools Blogs</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-250">Somasegars-Blog zu Entwicklertools</span><span class="sxs-lookup"><span data-stu-id="55c05-250">Somasegar's developer tools blog</span></span></td>
        <td><a href="http://blogs.msdn.com/b/somasegar/"><span data-ttu-id="55c05-251">Somasegar’s blog</span><span class="sxs-lookup"><span data-stu-id="55c05-251">Somasegar’s blog</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-252">DirectX-Entwicklerblog</span><span class="sxs-lookup"><span data-stu-id="55c05-252">DirectX developer blog</span></span></td>
        <td><a href="http://blogs.msdn.com/b/directx"><span data-ttu-id="55c05-253">DirectX Developer Blog</span><span class="sxs-lookup"><span data-stu-id="55c05-253">DirectX Developer blog</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-254">Einführung in DirectX12 (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="55c05-254">DirectX 12 introduction (blog post)</span></span></td>
        <td><a href="http://blogs.msdn.com/b/directx/archive/2014/03/20/directx-12.aspx"><span data-ttu-id="55c05-255">DirectX12</span><span class="sxs-lookup"><span data-stu-id="55c05-255">DirectX 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-256">Teamblog zu VisualC++-Tools</span><span class="sxs-lookup"><span data-stu-id="55c05-256">Visual C++ tools team blog</span></span></td>
        <td><a href="http://blogs.msdn.com/b/vcblog/"><span data-ttu-id="55c05-257">Teamblog zu Visual C++</span><span class="sxs-lookup"><span data-stu-id="55c05-257">Visual C++ team blog</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-258">Blog des PIX-Teams</span><span class="sxs-lookup"><span data-stu-id="55c05-258">PIX team blog</span></span></td>
        <td><a href="https://blogs.msdn.microsoft.com/pix/"><span data-ttu-id="55c05-259">Leistungsoptimierung und -Debuggen von DirectX12-Spielen für Windows und Xbox</span><span class="sxs-lookup"><span data-stu-id="55c05-259">Performance tuning and debugging for DirectX 12 games on Windows and Xbox</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-260">Universelle Windows-App – Blog des Bereitstellungsteams</span><span class="sxs-lookup"><span data-stu-id="55c05-260">Universal Windows App Deployment team blog</span></span></td>
        <td><a href="https://blogs.msdn.microsoft.com/appinstaller/"><span data-ttu-id="55c05-261">Erstellen und Bereitstellen von UWP-Apps – Teamblog</span><span class="sxs-lookup"><span data-stu-id="55c05-261">Build and deploy UWP apps team blog</span></span></a></td>
    </tr>
</table>
 

## <a name="concept-and-planning"></a><span data-ttu-id="55c05-262">Konzept und Planung</span><span class="sxs-lookup"><span data-stu-id="55c05-262">Concept and planning</span></span>


<span data-ttu-id="55c05-263">In der Konzeptionierungs- und Planungsphase entscheiden Sie, welches Spiel Sie entwickeln möchten und mit welchen Tools und Technologien Sie es zum Leben erwecken.</span><span class="sxs-lookup"><span data-stu-id="55c05-263">In the concept and planning stage, you're deciding what your game is going to be like and the technologies and tools you'll use to bring it to life.</span></span>

### <a name="overview-of-game-development-technologies"></a><span data-ttu-id="55c05-264">Übersicht über Technologien für die Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="55c05-264">Overview of game development technologies</span></span>

<span data-ttu-id="55c05-265">Zu Beginn der Entwicklung eines UWP-Spiels haben Sie die Wahl zwischen verschiedenen Optionen für Grafik, Eingabe, Audio, Netzwerk, Hilfsprogramme und Bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="55c05-265">When you start developing a game for the UWP you have multiple options available for graphics, input, audio, networking, utilities, and libraries.</span></span>

<span data-ttu-id="55c05-266">Vielleicht haben Sie ja bereits entschieden, welche Technologien Sie in Ihrem Spiel verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="55c05-266">If you've already decided on all the technologies you'll be using in your game, great!</span></span> <span data-ttu-id="55c05-267">Andernfalls finden Sie im Handbuch [Spieletechnologien für UWP-Apps](game-development-platform-guide.md) eine hervorragende Übersicht über viele der verfügbaren Technologien. Es wird nachdrücklich empfohlen, dieses Handbuch zu lesen, um mehr über die Optionen und ihre Kombinationsmöglichkeiten zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="55c05-267">If not, the [Game technologies for UWP apps](game-development-platform-guide.md) guide is an excellent overview of many of the technologies available, and is highly recommended reading to help you understand the options and how they fit together.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-268">Überblick über UWP-Spieletechnologien</span><span class="sxs-lookup"><span data-stu-id="55c05-268">Survey of UWP game technologies</span></span></td>
        <td><a href="game-development-platform-guide.md"><span data-ttu-id="55c05-269">Spieletechnologien für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-269">Game technologies for UWP apps</span></span></a></td>
    </tr>
</table>
 

<span data-ttu-id="55c05-270">Diese drei GDC2015-Videos vermitteln einen guten Überblick über die Entwicklung von Windows10-Spielen und das Spielerlebnis unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="55c05-270">These three GDC 2015 videos give a good overview of Windows 10 game development and the Windows 10 gaming experience.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-271">Übersicht über die Entwicklung von Windows10-Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-271">Overview of Windows 10 game development (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Developing-Games-for-Windows-10"><span data-ttu-id="55c05-272">Entwickeln von Spielen für Windows10</span><span class="sxs-lookup"><span data-stu-id="55c05-272">Developing Games for Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-273">Spielerlebnis unter Windows10 (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-273">Windows 10 gaming experience (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Gaming-Consumer-Experience-on-Windows-10"><span data-ttu-id="55c05-274">Spielerfahrung von Endbenutzern unter Windows10</span><span class="sxs-lookup"><span data-stu-id="55c05-274">Gaming Consumer Experience on Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-275">Übergreifendes Spielen im gesamten Microsoft-Ökosystem (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-275">Gaming across the Microsoft ecosystem (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/The-Future-of-Gaming-Across-the-Microsoft-Ecosystem"><span data-ttu-id="55c05-276">Die Zukunft des Spielens im gesamten Microsoft-Ökosystem</span><span class="sxs-lookup"><span data-stu-id="55c05-276">The Future of Gaming Across the Microsoft Ecosystem</span></span></a></td>
    </tr>
</table>

### <a name="game-planning"></a><span data-ttu-id="55c05-277">Planen von Spielen</span><span class="sxs-lookup"><span data-stu-id="55c05-277">Game planning</span></span>

<span data-ttu-id="55c05-278">Im Folgenden finden Sie einige Konzept- und Planungsthemen, die Ihnen einen Überblick über das geben, was Sie bei der Planung Ihres Spiels berücksichtigen sollten.</span><span class="sxs-lookup"><span data-stu-id="55c05-278">These are some high level concept and planning topics to consider when planning for your game.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-279">Erstellen barrierefreier Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-279">Make your game accessible</span></span></td>
        <td><a href="https://msdn.microsoft.com/windows/uwp/gaming/accessibility-for-games"><span data-ttu-id="55c05-280">Barrierefreiheit von Spielen</span><span class="sxs-lookup"><span data-stu-id="55c05-280">Accessibility for games</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-281">Erstellen von Spielen mit der Cloud</span><span class="sxs-lookup"><span data-stu-id="55c05-281">Build games using cloud</span></span></td>
        <td><a href="https://msdn.microsoft.com/windows/uwp/gaming/cloud-for-games"><span data-ttu-id="55c05-282">Cloud für Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-282">Cloud for games</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-283">Monetisierung eines Spiels</span><span class="sxs-lookup"><span data-stu-id="55c05-283">Monetize your game</span></span></td>
        <td><a href="https://msdn.microsoft.com/windows/uwp/gaming/monetization-for-games"><span data-ttu-id="55c05-284">Monetarisierung von Spielen</span><span class="sxs-lookup"><span data-stu-id="55c05-284">Monetization for games</span></span></a></td>
    </tr>
</table>



### <a name="choosing-your-graphics-technology-and-programming-language"></a><span data-ttu-id="55c05-285">Auswählen der Grafiktechnologie und Programmiersprache</span><span class="sxs-lookup"><span data-stu-id="55c05-285">Choosing your graphics technology and programming language</span></span>

<span data-ttu-id="55c05-286">Für Windows10-Spiele stehen verschiedene Programmiersprachen und Grafiktechnologien zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="55c05-286">There are several programming languages and graphics technologies available for use in Windows 10 games.</span></span> <span data-ttu-id="55c05-287">Der jeweilige Ansatz richtet sich nach der Art des Spiels, das Sie entwickeln, der Erfahrung und den Vorlieben Ihres Entwicklungsstudios und den bestimmten Funktionsanforderungen Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="55c05-287">The path you take depends on the type of game you’re developing, the experience and preferences of your development studio, and specific feature requirements of your game.</span></span> <span data-ttu-id="55c05-288">Möchten Sie C#, C++ oder JavaScript verwenden?</span><span class="sxs-lookup"><span data-stu-id="55c05-288">Will you use C#, C++, or JavaScript?</span></span> <span data-ttu-id="55c05-289">DirectX, XAML oder HTML5?</span><span class="sxs-lookup"><span data-stu-id="55c05-289">DirectX, XAML, or HTML5?</span></span>

#### <a name="directx"></a><span data-ttu-id="55c05-290">DirectX</span><span class="sxs-lookup"><span data-stu-id="55c05-290">DirectX</span></span>

<span data-ttu-id="55c05-291">Microsoft DirectX ist die richtige Wahl für 2D/3D-Grafik und Multimediaelemente.</span><span class="sxs-lookup"><span data-stu-id="55c05-291">Microsoft DirectX is the choice to make for the highest-performance 2D and 3D graphics and multimedia.</span></span>

<span data-ttu-id="55c05-292">DirectX 12 ist schneller und effizienter als alle früheren Versionen von Direct3D.</span><span class="sxs-lookup"><span data-stu-id="55c05-292">DirectX 12 is faster and more efficient than any previous version.</span></span> <span data-ttu-id="55c05-293">Direct3D12 ermöglicht detaillierte Umgebungen, mehr Objekte, komplexere Effekte und eine optimale Nutzung moderner GPU-Hardware auf Windows 10 PCs und Xbox One.</span><span class="sxs-lookup"><span data-stu-id="55c05-293">Direct3D 12 enables richer scenes, more objects, more complex effects, and full utilization of modern GPU hardware on Windows 10 PCs and Xbox One.</span></span>

<span data-ttu-id="55c05-294">Sie können weiterhin die vertraute Grafikpipeline von Direct3D11 verwenden und gleichzeitig von den neuen Rendering- und Optimierungsfeatures profitieren, die in Direct3D11.3 hinzugekommen sind.</span><span class="sxs-lookup"><span data-stu-id="55c05-294">If you want to use the familiar graphics pipeline of Direct3D 11, you’ll still benefit from the new rendering and optimization features added to Direct3D 11.3.</span></span> <span data-ttu-id="55c05-295">Und wenn Sie ein richtiger Windows-API-Entwickler für den Desktop mit Win32-Erfahrung sind, steht Ihnen unter Windows10 auch diese Option zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="55c05-295">And, if you’re a tried-and-true desktop Windows API developer with roots in Win32, you’ll still have that option in Windows 10.</span></span>

<span data-ttu-id="55c05-296">Dank umfangreicher Features und einer umfassenden Plattformintegration lassen sich mit DirectX selbst anspruchsvollste Spiele realisieren.</span><span class="sxs-lookup"><span data-stu-id="55c05-296">The extensive features and deep platform integration of DirectX provide the power and performance needed by the most demanding games.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-297">DirectX für die UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="55c05-297">DirectX for UWP development</span></span></td>
        <td><a href="directx-programming.md"><span data-ttu-id="55c05-298">DirectX-Programmierung</span><span class="sxs-lookup"><span data-stu-id="55c05-298">DirectX programming</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-299">Lernprogramm: Erstellen eines UWP-DirectX-Spiels</span><span class="sxs-lookup"><span data-stu-id="55c05-299">Tutorial: How to create a UWP DirectX game</span></span></td>
        <td><a href="tutorial--create-your-first-uwp-directx-game.md"><span data-ttu-id="55c05-300">Erstellen eines einfachen UWP-Spiels mit DirectX</span><span class="sxs-lookup"><span data-stu-id="55c05-300">Create a simple UWP game with DirectX</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-301">Übersichten und Referenzen zu DirectX</span><span class="sxs-lookup"><span data-stu-id="55c05-301">DirectX overviews and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/ee663274"><span data-ttu-id="55c05-302">DirectX-Grafiken und -Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-302">DirectX Graphics and Gaming</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-303">Direct3D12-Programmieranleitung und -referenz</span><span class="sxs-lookup"><span data-stu-id="55c05-303">Direct3D 12 programming guide and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn903821"><span data-ttu-id="55c05-304">Direct3D12-Grafiken</span><span class="sxs-lookup"><span data-stu-id="55c05-304">Direct3D 12 Graphics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-305">Videos zu Grafiken und zur DirectX 12-Entwicklung (YouTube-Kanal)</span><span class="sxs-lookup"><span data-stu-id="55c05-305">Graphics and DirectX 12 development videos (YouTube channel)</span></span></td>
        <td><a href="https://www.youtube.com/channel/UCiaX2B8XiXR70jaN7NK-FpA"><span data-ttu-id="55c05-306">Informationen zu Microsoft DirectX12 und Grafiken</span><span class="sxs-lookup"><span data-stu-id="55c05-306">Microsoft DirectX 12 and Graphics Education</span></span></a></td>
    </tr>
</table>
 

#### <a name="xaml"></a><span data-ttu-id="55c05-307">XAML</span><span class="sxs-lookup"><span data-stu-id="55c05-307">XAML</span></span>

<span data-ttu-id="55c05-308">XAML ist eine benutzerfreundliche deklarative UI-Sprache mit nützlichen Features wie Animationen, Storyboards, Datenbindung, skalierbaren vektorbasierten Grafiken, dynamischer Größenänderung und Szenendiagrammen.</span><span class="sxs-lookup"><span data-stu-id="55c05-308">XAML is an easy-to-use declarative UI language with convenient features like animations, storyboards, data binding, scalable vector-based graphics, dynamic resizing, and scene graphs.</span></span> <span data-ttu-id="55c05-309">XAML eignet sich gut für Benutzeroberflächen, Menüs, Sprites und 2D-Grafiken von Spielen.</span><span class="sxs-lookup"><span data-stu-id="55c05-309">XAML works great for game UI, menus, sprites, and 2D graphics.</span></span> <span data-ttu-id="55c05-310">Zur Vereinfachung der UI-Layouterstellung ist XAML mit Entwurfs- und Entwicklungstools wie Expression Blend und Microsoft Visual Studio kompatibel.</span><span class="sxs-lookup"><span data-stu-id="55c05-310">To make UI layout easy, XAML is compatible with design and development tools like Expression Blend and Microsoft Visual Studio.</span></span> <span data-ttu-id="55c05-311">XAML wird häufig mit C# kombiniert, aber auch C++ ist eine gute Wahl, falls dies Ihre bevorzugte Programmiersprache ist oder Ihr Spiel hohe Ansprüche an die CPU stellt.</span><span class="sxs-lookup"><span data-stu-id="55c05-311">XAML is commonly used with C#, but C++ is also a good choice if that’s your preferred language or if your game has high CPU demands.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-312">XAML-Plattformübersicht</span><span class="sxs-lookup"><span data-stu-id="55c05-312">XAML platform overview</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt228259"><span data-ttu-id="55c05-313">XAML-Plattform</span><span class="sxs-lookup"><span data-stu-id="55c05-313">XAML platform</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-314">XAML-UI und -Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="55c05-314">XAML UI and controls</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt228348"><span data-ttu-id="55c05-315">Steuerelemente, Layouts und Text</span><span class="sxs-lookup"><span data-stu-id="55c05-315">Controls, layouts, and text</span></span></a></td>
    </tr>
</table>
 

#### <a name="html-5"></a><span data-ttu-id="55c05-316">HTML5</span><span class="sxs-lookup"><span data-stu-id="55c05-316">HTML 5</span></span>

<span data-ttu-id="55c05-317">Die HyperText Markup Language (HTML) ist eine häufig verwendete Markup-Sprache für Benutzeroberflächen, die bei Webseiten, Apps und Rich-Clients zum Einsatz kommt.</span><span class="sxs-lookup"><span data-stu-id="55c05-317">HyperText Markup Language (HTML) is a common UI markup language used for web pages, apps, and rich clients.</span></span> <span data-ttu-id="55c05-318">Für Windows-Spiele kann HTML5 als Darstellungsschicht mit vollem Funktionsumfang genutzt werden. Dabei stehen die vertrauten Features von HTML, Zugriff auf die universelle Windows-Plattform und Unterstützung für moderne Webfeatures wie AppCache, Web-Worker, Canvas, Drag&Drop, asynchrone Programmierung und SVG zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="55c05-318">Windows games can use HTML5 as a full-featured presentation layer with the familiar features of HTML, access to the Universal Windows Platform, and support for modern web features like AppCache, Web Workers, canvas, drag-and-drop, asynchronous programming, and SVG.</span></span> <span data-ttu-id="55c05-319">Im Hintergrund wird für das HTML-Rendering die leistungsstarke DirectX-Hardwarebeschleunigung genutzt, sodass Sie weiterhin in den Genuss der Leistungsvorteile von DirectX kommen, ohne zusätzlichen Code schreiben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="55c05-319">Behind the scenes, HTML rendering takes advantage of the power of DirectX hardware acceleration, so you can still get the performance benefits of DirectX without writing any extra code.</span></span> <span data-ttu-id="55c05-320">HTML5 ist eine gute Wahl, wenn Sie sich mit der Webentwicklung auskennen, ein Webspiel portieren oder Sprach- und Grafikebenen nutzen möchten, die unter Umständen leichter zugänglich als andere Optionen sind.</span><span class="sxs-lookup"><span data-stu-id="55c05-320">HTML5 is a good choice if you are proficient with web development, porting a web game, or want to use language and graphics layers that can be easier to approach than the other choices.</span></span> <span data-ttu-id="55c05-321">HTML5 wird zusammen mit JavaScript verwendet, kann aber auch mit Komponenten verknüpft werden, die mit C# oder C++/CX erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="55c05-321">HTML5 is used with JavaScript, but can also call into components created with C# or C++/CX.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-322">Informationen zu HTML5 und zum Dokumentobjektmodell</span><span class="sxs-lookup"><span data-stu-id="55c05-322">HTML5 and Document Object Model information</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/br212882.aspx"><span data-ttu-id="55c05-323">HTML- und DOM-Referenz</span><span class="sxs-lookup"><span data-stu-id="55c05-323">HTML and DOM reference</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-324">Die HTML5-Empfehlung des W3C</span><span class="sxs-lookup"><span data-stu-id="55c05-324">The HTML5 W3C Recommendation</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?linkid=221374"><span data-ttu-id="55c05-325">HTML5</span><span class="sxs-lookup"><span data-stu-id="55c05-325">HTML5</span></span></a></td>
    </tr>
</table>
 

#### <a name="combining-presentation-technologies"></a><span data-ttu-id="55c05-326">Kombinieren von Darstellungstechnologien</span><span class="sxs-lookup"><span data-stu-id="55c05-326">Combining presentation technologies</span></span>

<span data-ttu-id="55c05-327">Die Microsoft DirectX Graphic Infrastructure (DXGI) bietet Interoperabilität und Kompatibilität mit mehreren Arten von Grafiktechnologien.</span><span class="sxs-lookup"><span data-stu-id="55c05-327">The Microsoft DirectX Graphics Infrastructure (DXGI) provides interop and compatibility across multiple graphics technologies.</span></span> <span data-ttu-id="55c05-328">Für Hochleistungsgrafiken können Sie XAML und DirectX kombinieren, indem Sie XAML für Menüs und andere einfache UI-Elemente und DirectX für das Rendern von komplexen 2D- und 3D-Szenen nutzen.</span><span class="sxs-lookup"><span data-stu-id="55c05-328">For high-performance graphics, you can combine XAML and DirectX, using XAML for menus and other simple UI, and DirectX for rendering complex 2D and 3D scenes.</span></span> <span data-ttu-id="55c05-329">DXGI sorgt auch für Kompatibilität zwischen Direct2D, Direct3D, DirectWrite, DirectCompute und der Microsoft Media Foundation.</span><span class="sxs-lookup"><span data-stu-id="55c05-329">DXGI also provides compatibility between Direct2D, Direct3D, DirectWrite, DirectCompute, and the Microsoft Media Foundation.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-330">Programmieranleitung und Referenz für die DirectX Graphic Infrastructure</span><span class="sxs-lookup"><span data-stu-id="55c05-330">DirectX Graphics Infrastructure programming guide and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/hh404534"><span data-ttu-id="55c05-331">DXGI</span><span class="sxs-lookup"><span data-stu-id="55c05-331">DXGI</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-332">Kombinieren von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="55c05-332">Combining DirectX and XAML</span></span></td>
        <td><a href="directx-and-xaml-interop.md"><span data-ttu-id="55c05-333">Interoperabilität von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="55c05-333">DirectX and XAML interop</span></span></a></td>
    </tr>
</table>
 

#### <a name="c"></a><span data-ttu-id="55c05-334">C++</span><span class="sxs-lookup"><span data-stu-id="55c05-334">C++</span></span>

<span data-ttu-id="55c05-335">C++/CX ist eine effiziente Hochleistungssprache und bietet eine erstklassige Mischung aus Geschwindigkeit, Kompatibilität und Plattformzugriff.</span><span class="sxs-lookup"><span data-stu-id="55c05-335">C++/CX is a high-performance, low overhead language that provides the powerful combination of speed, compatibility, and platform access.</span></span> <span data-ttu-id="55c05-336">C++/CX erleichtert Ihnen die Nutzung aller nützlichen Gaming-Features unter Windows10, z.B. DirectX und Xbox Live.</span><span class="sxs-lookup"><span data-stu-id="55c05-336">C++/CX makes it easy to use all of the great gaming features in Windows 10, including DirectX and Xbox Live.</span></span> <span data-ttu-id="55c05-337">Außerdem können Sie vorhandenen C++-Code und die dazugehörigen Bibliotheken verwenden.</span><span class="sxs-lookup"><span data-stu-id="55c05-337">You can also reuse existing C++ code and libraries.</span></span> <span data-ttu-id="55c05-338">Mit C++/CX wird schneller, systemeigener Code erstellt, bei dem kein Aufwand für die Garbage Collection anfällt. So kann Ihr Spiel mit einer hohen Leistung und einem geringen Stromverbrauch aufwarten und somit auch eine längere Akkulaufzeit ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="55c05-338">C++/CX creates fast, native code that doesn’t incur the overhead of garbage collection, so your game can have great performance and low power consumption, which leads to longer battery life.</span></span> <span data-ttu-id="55c05-339">Verwenden Sie C++/CX mit DirectX oder XAML, oder erstellen Sie ein Spiel mit einer Kombination aus beidem.</span><span class="sxs-lookup"><span data-stu-id="55c05-339">Use C++/CX with DirectX or XAML, or create a game that uses a combination of both.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-340">Referenz und Übersichten für C++/CX</span><span class="sxs-lookup"><span data-stu-id="55c05-340">C++/CX reference and overviews</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/hh699871.aspx"><span data-ttu-id="55c05-341">Visual C++-Programmiersprachenreferenz (C++/CX)</span><span class="sxs-lookup"><span data-stu-id="55c05-341">Visual C++ Language Reference (C++/CX)</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-342">Visual C++-Programmieranleitung und -Referenz</span><span class="sxs-lookup"><span data-stu-id="55c05-342">Visual C++ programming guide and reference</span></span></td>
        <td><a href="https://docs.microsoft.com/cpp/visual-cpp-in-visual-studio"><span data-ttu-id="55c05-343">Visual C++ in Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="55c05-343">Visual C++ in Visual Studio 2017</span></span></a></td>
    </tr>
</table>
 

#### <a name="c"></a><span data-ttu-id="55c05-344">C#</span><span class="sxs-lookup"><span data-stu-id="55c05-344">C#</span></span>

<span data-ttu-id="55c05-345">C# (sprich: „C sharp“) ist eine moderne, innovative Programmiersprache, die einfach, leistungsstark, typsicher und objektorientiert ist.</span><span class="sxs-lookup"><span data-stu-id="55c05-345">C# (pronounced "C sharp") is a modern, innovative language that is simple, powerful, type-safe, and object-oriented.</span></span> <span data-ttu-id="55c05-346">C# ermöglicht eine schnelle Entwicklung, während gleichzeitig die Vertrautheit und Ausdruckskraft von Sprachen im C-Stil gewahrt bleibt.</span><span class="sxs-lookup"><span data-stu-id="55c05-346">C# enables rapid development while retaining the familiarity and expressiveness of C-style languages.</span></span> <span data-ttu-id="55c05-347">Obwohl C# einfach zu verwenden ist, verfügt die Sprache über viele moderne Sprachfeatures wie Polymorphie, Delegate, Lambda-Elemente, Abschlüsse, Iteratormethoden, Kovarianz und LINQ-Ausdrücke (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="55c05-347">Though easy to use, C# has numerous advanced language features like polymorphism, delegates, lambdas, closures, iterator methods, covariance, and Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="55c05-348">C# ist eine ausgezeichnete Wahl, wenn Sie XAML verwenden möchten, schnell mit der Entwicklung Ihres Spiels beginnen möchten oder bereits über C#-Erfahrung verfügen.</span><span class="sxs-lookup"><span data-stu-id="55c05-348">C# is an excellent choice if you are targeting XAML, want to get a quick start developing your game, or have previous C# experience.</span></span> <span data-ttu-id="55c05-349">C# wird vorrangig mit XAML genutzt. Wenn Sie also DirectX verwenden möchten, entscheiden Sie sich besser für C++, oder schreiben Sie einen Teil des Spiels als C++-Komponente, die mit DirectX interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="55c05-349">C# is used primarily with XAML, so if you want to use DirectX, choose C++ instead, or write part of your game as a C++ component that interacts with DirectX.</span></span> <span data-ttu-id="55c05-350">Eine weitere Alternative wäre [Win2D](https://github.com/Microsoft/Win2D) – eine Direct2D-Grafikbibliothek im unmittelbaren Modus für C# und C++.</span><span class="sxs-lookup"><span data-stu-id="55c05-350">Or, consider [Win2D](https://github.com/Microsoft/Win2D), an immediate mode Direct2D graphics libary for C# and C++.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-351">C#-Programmieranleitung und -Referenz</span><span class="sxs-lookup"><span data-stu-id="55c05-351">C# programming guide and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/kx37x362.aspx"><span data-ttu-id="55c05-352">C#-Programmiersprachenreferenz</span><span class="sxs-lookup"><span data-stu-id="55c05-352">C# language reference</span></span></a></td>
    </tr>
</table>
 

#### <a name="javascript"></a><span data-ttu-id="55c05-353">JavaScript</span><span class="sxs-lookup"><span data-stu-id="55c05-353">JavaScript</span></span>

<span data-ttu-id="55c05-354">JavaScript ist eine dynamische Skriptsprache, die gerne für moderne Webanwendungen und Rich-Client-Anwendungen eingesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="55c05-354">JavaScript is a dynamic scripting language widely used for modern web and rich client applications.</span></span>

<span data-ttu-id="55c05-355">Bei Windows-JavaScript-Apps kann auf einfache und intuitive Weise auf die leistungsfähigen Features der universellen Windows-Plattform zugegriffen werden – in Form von Methoden und Eigenschaften objektorientierter JavaScript-Klassen.</span><span class="sxs-lookup"><span data-stu-id="55c05-355">Windows JavaScript apps can access the powerful features of the Universal Windows Platform in an easy, intuitive way—as methods and properties of object-oriented JavaScript classes.</span></span> <span data-ttu-id="55c05-356">JavaScript ist für Ihr Spiel eine gute Wahl, wenn Sie aus dem Bereich der Webentwicklung kommen, sich mit JavaScript bereits auskennen oder HTML5-, CSS-, WinJS- oder JavaScript-Bibliotheken verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="55c05-356">JavaScript is a good choice for your game if you’re coming from a web development environment, are already familiar with JavaScript, or want to use HTML5, CSS, WinJS, or JavaScript libraries.</span></span> <span data-ttu-id="55c05-357">Wenn Sie Ihre Entwicklung auf DirectX oder XAML ausrichten möchten, ist C# oder C++/CX die bessere Wahl.</span><span class="sxs-lookup"><span data-stu-id="55c05-357">If you’re targeting DirectX or XAML, choose C# or C++/CX instead.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-358">Referenz zu JavaScript und Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="55c05-358">JavaScript and Windows Runtime reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/jj613794"><span data-ttu-id="55c05-359">JavaScript-Referenz</span><span class="sxs-lookup"><span data-stu-id="55c05-359">JavaScript reference</span></span></a></td>
    </tr>
</table>


#### <a name="use-windows-runtime-components-to-combine-languages"></a><span data-ttu-id="55c05-360">Kombinieren von Programmiersprachen mithilfe von Windows-Runtime-Komponenten</span><span class="sxs-lookup"><span data-stu-id="55c05-360">Use Windows Runtime Components to combine languages</span></span>

<span data-ttu-id="55c05-361">Mit der universellen Windows-Plattform lassen sich problemlos Komponenten in unterschiedlichen Programmiersprachen kombinieren.</span><span class="sxs-lookup"><span data-stu-id="55c05-361">With the Universal Windows Platform, it’s easy to combine components written in different languages.</span></span> <span data-ttu-id="55c05-362">Erstellen Sie Komponenten für Windows-Runtime in C++, C# oder Visual Basic, und nutzen Sie diese dann per JavaScript, C#, C++ oder Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="55c05-362">Create Windows Runtime Components in C++, C#, or Visual Basic, and then call into them from JavaScript, C#, C++, or Visual Basic.</span></span> <span data-ttu-id="55c05-363">Dies ist eine hervorragende Möglichkeit, wenn Sie Teile des Spiels in der Sprache Ihrer Wahl programmieren möchten.</span><span class="sxs-lookup"><span data-stu-id="55c05-363">This is a great way to program portions of your game in the language of your choice.</span></span> <span data-ttu-id="55c05-364">Über Komponenten können Sie außerdem externe Bibliotheken nutzen, die nur in einer bestimmten Programmiersprache verfügbar sind, oder auch älteren Code, den Sie bereits geschrieben haben.</span><span class="sxs-lookup"><span data-stu-id="55c05-364">Components also let you consume external libraries that are only available in a particular language, as well as use legacy code you’ve already written.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-365">So wird's gemacht: Erstellen von Komponenten für die Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="55c05-365">How to create Windows Runtime Components</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp"><span data-ttu-id="55c05-366">Erstellen von Windows-Runtime-Komponenten</span><span class="sxs-lookup"><span data-stu-id="55c05-366">Creating Windows Runtime Components</span></span></a></td>
    </tr>
</table>


### <a name="which-version-of-directx-should-your-game-use"></a><span data-ttu-id="55c05-367">Welche DirectX-Version sollte Ihr Spiel verwenden?</span><span class="sxs-lookup"><span data-stu-id="55c05-367">Which version of DirectX should your game use?</span></span>

<span data-ttu-id="55c05-368">Wenn Sie DirectX für Ihr Spiel auswählen, müssen Sie entscheiden, welche Version Sie verwenden: Microsoft Direct3D12 oder Microsoft Direct3D11.</span><span class="sxs-lookup"><span data-stu-id="55c05-368">If you are choosing DirectX for your game, you'll need to decide which version to use: Microsoft Direct3D12 or Microsoft Direct3D11.</span></span>

<span data-ttu-id="55c05-369">DirectX 12 ist schneller und effizienter als alle früheren Versionen von Direct3D.</span><span class="sxs-lookup"><span data-stu-id="55c05-369">DirectX 12 is faster and more efficient than any previous version.</span></span> <span data-ttu-id="55c05-370">Direct3D12 ermöglicht detaillierte Umgebungen, mehr Objekte, komplexere Effekte und eine optimale Nutzung moderner GPU-Hardware auf Windows 10 PCs und Xbox One.</span><span class="sxs-lookup"><span data-stu-id="55c05-370">Direct3D 12 enables richer scenes, more objects, more complex effects, and full utilization of modern GPU hardware on Windows 10 PCs and Xbox One.</span></span> <span data-ttu-id="55c05-371">Da Direct3D12 auf einer sehr niedrigen Ebene ausgeführt wird, erhält ein erfahrenes Grafikentwicklungs- oder DirectX11-Entwicklungsteam alle notwendigen Steuerungsmöglichkeiten für die Maximierung der Grafikoptimierung.</span><span class="sxs-lookup"><span data-stu-id="55c05-371">Since Direct3D 12 works at a very low level, it is able to give an expert graphics development team or an experienced DirectX 11 development team all the control they need to maximize graphics optimization.</span></span>

<span data-ttu-id="55c05-372">Direct3D11.3 ist eine Grafik-API auf einem niedrigen Niveau, die das vertraute Direct3D-Programmiermodell verwendet und Ihnen einen größeren Teil der Komplexität abnimmt, die mit dem GPU-Rendering verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="55c05-372">Direct3D 11.3 is a low level graphics API that uses the familiar Direct3D programming model and handles for you more of the complexity involved in GPU rendering.</span></span> <span data-ttu-id="55c05-373">Sie wird auch von Windows10 und Xbox One unterstützt.</span><span class="sxs-lookup"><span data-stu-id="55c05-373">It is also supported in Windows 10 and Xbox One.</span></span> <span data-ttu-id="55c05-374">Wenn Sie über ein vorhandenes Modul verfügen, das in Direct3D 11 geschrieben wurde, und noch nicht bereit sind, zu Direct3D12 zu wechseln, können Sie Direct3D11 auf 12 verwenden, um einige Leistungsverbesserungen zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="55c05-374">If you have an existing engine written in Direct3D 11, and you're not quite ready to make the jump to Direct3D 12, you can use Direct3D 11 on 12 to achieve some performance improvements.</span></span> <span data-ttu-id="55c05-375">Die Versionen ab 11.3 enthalten die neuen Rendering- und Optimierungsfeatures, die auch in Direct3D12 zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="55c05-375">Versions 11.3+ contain the new rendering and optimization features enabled also in Direct3D 12.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-376">Auswählen von Direct3D12 oder Direct3D11</span><span class="sxs-lookup"><span data-stu-id="55c05-376">Choosing Direct3D12 or Direct3D11</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn899228"><span data-ttu-id="55c05-377">Was ist Direct3D12?</span><span class="sxs-lookup"><span data-stu-id="55c05-377">What is Direct3D12?</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-378">Übersicht über Direct3D11</span><span class="sxs-lookup"><span data-stu-id="55c05-378">Overview of Direct3D11</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/ff476080"><span data-ttu-id="55c05-379">Direct3D11-Grafik</span><span class="sxs-lookup"><span data-stu-id="55c05-379">Direct3D 11 Graphics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-380">Übersicht über „Direct3D 11 on 12“</span><span class="sxs-lookup"><span data-stu-id="55c05-380">Overview of Direct3D 11 on 12</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn913195"><span data-ttu-id="55c05-381">Direct3D 11 on 12</span><span class="sxs-lookup"><span data-stu-id="55c05-381">Direct3D 11 on 12</span></span></a></td>
    </tr>
</table>


### <a name="bridges-game-engines-and-middleware"></a><span data-ttu-id="55c05-382">Brücken, Spielengines und Middleware</span><span class="sxs-lookup"><span data-stu-id="55c05-382">Bridges, game engines, and middleware</span></span>

<span data-ttu-id="55c05-383">Mithilfe von Brücken, Spielengines und Middleware können Sie je nach Spiel unter Umständen die Entwicklung und das Testing beschleunigen und den damit verbundenen Ressourcenaufwand verringern.</span><span class="sxs-lookup"><span data-stu-id="55c05-383">Depending on the needs of your game, using bridges, game engines, or middleware can save development and testing time and resources.</span></span> <span data-ttu-id="55c05-384">Hier ist eine Übersicht und Ressourcen für Brücken, Spielengines und Middleware.</span><span class="sxs-lookup"><span data-stu-id="55c05-384">Here are some overview and resources for bridges, game engines, and middleware.</span></span>

#### <a name="universal-windows-platform-bridges"></a><span data-ttu-id="55c05-385">Brücken für die universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="55c05-385">Universal Windows Platform Bridges</span></span>

<span data-ttu-id="55c05-386">Bei Brücken für die universelle Windows-Plattform handelt es sich um Technologien für die UWP-Portierung Ihrer vorhandenen Apps oder Spiele.</span><span class="sxs-lookup"><span data-stu-id="55c05-386">Universal Windows Platform Bridges are technologies that bring your existing app or game over to the UWP.</span></span> <span data-ttu-id="55c05-387">Brücken eignen sich sehr gut für den schnellen Einstieg in die Entwicklung von UWP-Spielen.</span><span class="sxs-lookup"><span data-stu-id="55c05-387">Bridges are a great way to get a quick start on UWP game development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-388">UWP Brücken</span><span class="sxs-lookup"><span data-stu-id="55c05-388">UWP bridges</span></span></td>
        <td><a href="https://dev.windows.com/bridges/"><span data-ttu-id="55c05-389">Portieren Ihres Codes für Windows</span><span class="sxs-lookup"><span data-stu-id="55c05-389">Bring your code to Windows</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-390">Windows-Brücke für iOS</span><span class="sxs-lookup"><span data-stu-id="55c05-390">Windows Bridge for iOS</span></span></td>
        <td><a href="https://dev.windows.com/bridges/ios"><span data-ttu-id="55c05-391">Portieren Ihrer iOS-Apps für Windows</span><span class="sxs-lookup"><span data-stu-id="55c05-391">Bring your iOS apps to Windows</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-392">Windows-Brücke für Desktop-Anwendungen (.NET und Win32)</span><span class="sxs-lookup"><span data-stu-id="55c05-392">Windows Bridge for desktop applications (.NET and Win32)</span></span></td>
        <td><a href="https://developer.microsoft.com/windows/bridges/desktop"><span data-ttu-id="55c05-393">Konvertieren Ihrer Desktopanwendung in eine UWP-App</span><span class="sxs-lookup"><span data-stu-id="55c05-393">Convert your desktop application to a UWP app</span></span></a></td>
    </tr>
</table>

#### <a name="playfab"></a><span data-ttu-id="55c05-394">PlayFab</span><span class="sxs-lookup"><span data-stu-id="55c05-394">PlayFab</span></span>

<span data-ttu-id="55c05-395">PlayFab ist jetzt Teil von Microsoft Family und eine vollständige Back-End-Plattform für Live-Spiele und ein leistungsstarkes Mittel für die ersten Schritte unabhängiger Studios.</span><span class="sxs-lookup"><span data-stu-id="55c05-395">Now part of the Microsoft family, PlayFab is a complete back-end platform for live games and a powerful way for independent studios to get started.</span></span> <span data-ttu-id="55c05-396">Steigern Sie Umsatz, Engagement und Bindung – bei gleichzeitigen Kosteneinsparungen – mit Spieldiensten, Echtzeitanalysen und LiveOps.</span><span class="sxs-lookup"><span data-stu-id="55c05-396">Boost revenue, engagement, and retention—while cutting costs—with game services, real-time analytics, and LiveOps.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-397">PlayFab</span><span class="sxs-lookup"><span data-stu-id="55c05-397">PlayFab</span></span></td>
        <td><a href="https://playfab.com/"><span data-ttu-id="55c05-398">Übersicht über Tools und Dienste</span><span class="sxs-lookup"><span data-stu-id="55c05-398">Overview of tools and services</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-399">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="55c05-399">Getting started</span></span></td>
        <td><a href="https://api.playfab.com/docs/general-getting-started"><span data-ttu-id="55c05-400">Generelles Handbuch über erste Schritte</span><span class="sxs-lookup"><span data-stu-id="55c05-400">General getting started guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-401">Video-Lernprogrammserie</span><span class="sxs-lookup"><span data-stu-id="55c05-401">Video tutorial series</span></span></td>
        <td><a href="https://www.youtube.com/watch?v=fGNpiqVi5xU&list=PLHCfyL7JpoPbLpA_oh_T5PKrfzPgCpPT5"><span data-ttu-id="55c05-402">Serie von Demovideos über Kernsysteme von PlayFab</span><span class="sxs-lookup"><span data-stu-id="55c05-402">Series of demo videos about PlayFab's core systems</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-403">Rezepte</span><span class="sxs-lookup"><span data-stu-id="55c05-403">Recipes</span></span></td>
        <td><a href="https://api.playfab.com/docs/tutorials/recipes-index"><span data-ttu-id="55c05-404">Beliebte Spielmechanismen und Designmusterbeispiele</span><span class="sxs-lookup"><span data-stu-id="55c05-404">Popular game mechanics and design pattern samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-405">Plattformen</span><span class="sxs-lookup"><span data-stu-id="55c05-405">Platforms</span></span></td>
        <td><a href="https://api.playfab.com/platforms"><span data-ttu-id="55c05-406">Spezielle Dokumentation für verschiedene Plattformen und Spielengines</span><span class="sxs-lookup"><span data-stu-id="55c05-406">Specific documentation for various platforms and game engines</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-407">GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="55c05-407">GitHub repo</span></span></td>
        <td><a href="https://github.com/PlayFab"><span data-ttu-id="55c05-408">Hier erhalten Sie Skripts und SDKs für verschiedene Plattformen, einschließlich Android, iOS, Windows, Unity und Unreal.</span><span class="sxs-lookup"><span data-stu-id="55c05-408">Get scripts and SDKs for various platforms including Android, iOS, Windows, Unity, and Unreal.</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-409">API-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="55c05-409">API documentation</span></span></td>
        <td><a href="https://api.playfab.com/documentation/"><span data-ttu-id="55c05-410">PlayFab-Dienst direkt über REST-ähnlichen Web-APIs</span><span class="sxs-lookup"><span data-stu-id="55c05-410">Access PlayFab service directly via REST-like Web APIs</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-411">Foren</span><span class="sxs-lookup"><span data-stu-id="55c05-411">Forums</span></span></td>
        <td><a href="https://community.playfab.com/index.html"><span data-ttu-id="55c05-412">PlayFab-Foren</span><span class="sxs-lookup"><span data-stu-id="55c05-412">PlayFab forums</span></span></a></td>
    </tr>
</table>
 

#### <a name="unity"></a><span data-ttu-id="55c05-413">Unity</span><span class="sxs-lookup"><span data-stu-id="55c05-413">Unity</span></span>

<span data-ttu-id="55c05-414">Unity bietet eine Plattform zum Erstellen ansprechender 2D, 3D, VR, und AR-Spiele und Apps.</span><span class="sxs-lookup"><span data-stu-id="55c05-414">Unity offers a platform for creating beautiful and engaging 2D, 3D, VR, and AR games and apps.</span></span> <span data-ttu-id="55c05-415">Es ermöglicht Ihnen, Ihre kreative Vision schnell umzusetzen und Ihre Inhalte auf nahezu alle Medien oder Geräten anzubieten.</span><span class="sxs-lookup"><span data-stu-id="55c05-415">It enables you to realize your creative vision fast and delivers your content to virtually any media or device.</span></span>

<span data-ttu-id="55c05-416">Unity unterstützt ab Unity5.4 die Direct3D12-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="55c05-416">Beginning with Unity 5.4, Unity supports Direct3D 12 development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-417">Die Unity-Spielengine</span><span class="sxs-lookup"><span data-stu-id="55c05-417">The Unity game engine</span></span></td>
        <td><a href="http://unity3d.com/"><span data-ttu-id="55c05-418">Unity – Spielengine</span><span class="sxs-lookup"><span data-stu-id="55c05-418">Unity - Game Engine</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-419">Unity herunterladen</span><span class="sxs-lookup"><span data-stu-id="55c05-419">Get Unity</span></span></td>
        <td><a href="http://unity3d.com/get-unity"><span data-ttu-id="55c05-420">Unity herunterladen</span><span class="sxs-lookup"><span data-stu-id="55c05-420">Get Unity</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-421">Unity-Dokumentation für Windows</span><span class="sxs-lookup"><span data-stu-id="55c05-421">Unity documentation for Windows</span></span></td>
        <td><a href="http://docs.unity3d.com/Manual/Windows.html"><span data-ttu-id="55c05-422">Unity-Handbuch/Windows</span><span class="sxs-lookup"><span data-stu-id="55c05-422">Unity Manual / Windows</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-423">Fügen Sie mit PlayFab LiveOps hinzu</span><span class="sxs-lookup"><span data-stu-id="55c05-423">Add LiveOps using PlayFab</span></span></td>
        <td><a href="https://api.playfab.com/docs/getting-started/unity-getting-started"><span data-ttu-id="55c05-424">Erste Schritte – führen Sie Ihren ersten PlayFab-API-Aufruf aus Ihrem Unity-Spiel durch</span><span class="sxs-lookup"><span data-stu-id="55c05-424">Getting started - Make your first PlayFab API call from your Unity game</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-425">Wie fügen Sie Ihrem Spiel mit dem interaktiven Mixer Interaktivität hinzu</span><span class="sxs-lookup"><span data-stu-id="55c05-425">How to add interactivity to your game using Mixer Interactive</span></span></td>
        <td><a href="https://github.com/mixer/interactive-unity-plugin/wiki/Getting-started"><span data-ttu-id="55c05-426">Leitfaden für erste Schritte</span><span class="sxs-lookup"><span data-stu-id="55c05-426">Getting started guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-427">Mixer SDK für Unity</span><span class="sxs-lookup"><span data-stu-id="55c05-427">Mixer SDK for Unity</span></span></td>
        <td><a href="https://www.assetstore.unity3d.com/en/#!/content/88585"><span data-ttu-id="55c05-428">Mixer Unity-Plug-In</span><span class="sxs-lookup"><span data-stu-id="55c05-428">Mixer Unity plugin</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-429">Vollständige Referenzdokumentation für Mixer SDK für Unity</span><span class="sxs-lookup"><span data-stu-id="55c05-429">Mixer SDK for Unity reference documentation</span></span></td>
        <td><a href="https://dev.mixer.com/reference/interactive/csharp/index.html"><span data-ttu-id="55c05-430">API-Referenz für das Mixer Unity-Plug-In</span><span class="sxs-lookup"><span data-stu-id="55c05-430">API reference for Mixer Unity plugin</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-431">Veröffentlichen eines Unity-Spiels im Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="55c05-431">Publish your Unity game to Microsoft Store</span></span></td>
        <td><a href="https://unity3d.com/partners/microsoft/porting-guides"><span data-ttu-id="55c05-432">Portierungsleitfaden</span><span class="sxs-lookup"><span data-stu-id="55c05-432">Porting guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-433">Problembehandlung bei fehlenden Assemblyverweisen im Zusammenhang mit .NET APIs</span><span class="sxs-lookup"><span data-stu-id="55c05-433">Troubleshooting missing assembly references related to .NET APIs</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/gaming/missing-dot-net-apis-in-unity-and-uwp"><span data-ttu-id="55c05-434">Fehlende .NET-APIs in Unity und UWP</span><span class="sxs-lookup"><span data-stu-id="55c05-434">Missing .NET APIs in Unity and UWP</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-435">Veröffentlichen eines Unity-Spiels als UWP-App (Universelle Windows-Plattform) (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-435">Publish your Unity game as a Universal Windows Platform app (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app"><span data-ttu-id="55c05-436">So veröffentlichen Sie Ihr Unity-Spiel als UWP-App</span><span class="sxs-lookup"><span data-stu-id="55c05-436">How to publish your Unity game as a UWP app</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-437">Verwenden von Unity zum Erstellen von Windows-Spielen und -Apps (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-437">Use Unity to make Windows games and apps (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Blogs/One-Dev-Minute/Making-games-and-apps-with-Unity"><span data-ttu-id="55c05-438">Erstellen von Windows-Spielen und -Apps mit Unity</span><span class="sxs-lookup"><span data-stu-id="55c05-438">Making Windows games and apps with Unity</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-439">Unity-Spielentwicklung mit Visual Studio (Videoserie)</span><span class="sxs-lookup"><span data-stu-id="55c05-439">Unity game development using Visual Studio (video series)</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=722359"><span data-ttu-id="55c05-440">Verwendung von Unity mit Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="55c05-440">Using Unity with Visual Studio 2015</span></span></a></td>
    </tr>
</table>
 

#### <a name="havok"></a><span data-ttu-id="55c05-441">Havok</span><span class="sxs-lookup"><span data-stu-id="55c05-441">Havok</span></span>

<span data-ttu-id="55c05-442">Mit den Tools und Technologien aus der modular aufgebauten Suite von Havok erreichen Spieleentwickler eine noch nie dagewesene Interaktivität und Immersion.</span><span class="sxs-lookup"><span data-stu-id="55c05-442">Havok’s modular suite of tools and technologies help game creators reach new levels of interactivity and immersion.</span></span> <span data-ttu-id="55c05-443">Havok bietet eine äußerst realistische Physik, interaktive Simulationen und beeindruckende Effekte.</span><span class="sxs-lookup"><span data-stu-id="55c05-443">Havok enables highly realistic physics, interactive simulations, and stunning cinematics.</span></span> <span data-ttu-id="55c05-444">Version 2015.1 und höher unterstützen UWP in Visual Studio2015 auf x86-, 64-Bit- und ARM-Plattformen.</span><span class="sxs-lookup"><span data-stu-id="55c05-444">Version 2015.1 and higher officially supports UWP in Visual Studio 2015 on x86, 64-bit, and ARM.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-445">Havok-Website</span><span class="sxs-lookup"><span data-stu-id="55c05-445">Havok website</span></span></td>
        <td><a href="http://www.havok.com/"><span data-ttu-id="55c05-446">Havok</span><span class="sxs-lookup"><span data-stu-id="55c05-446">Havok</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-447">Havok-Toolsuite</span><span class="sxs-lookup"><span data-stu-id="55c05-447">Havok tool suite</span></span></td>
        <td><a href="http://www.havok.com/products/"><span data-ttu-id="55c05-448">Havok-Produktübersicht</span><span class="sxs-lookup"><span data-stu-id="55c05-448">Havok Product Overview</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-449">Havok-Supportforen</span><span class="sxs-lookup"><span data-stu-id="55c05-449">Havok support forums</span></span></td>
        <td><a href="http://support.havok.com"><span data-ttu-id="55c05-450">Havok</span><span class="sxs-lookup"><span data-stu-id="55c05-450">Havok</span></span></a></td>
    </tr>
</table>
 

#### <a name="monogame"></a><span data-ttu-id="55c05-451">MonoGame</span><span class="sxs-lookup"><span data-stu-id="55c05-451">MonoGame</span></span>

<span data-ttu-id="55c05-452">MonoGame ist ein plattformübergreifendes Open-Source-Framework für die Spieleentwicklung, das ursprünglich auf XNA Framework 4.0 von Microsoft basierte.</span><span class="sxs-lookup"><span data-stu-id="55c05-452">MonoGame is an open source, cross-platform game development framework originally based on Microsoft's XNA Framework 4.0.</span></span> <span data-ttu-id="55c05-453">MonoGame unterstützt derzeit Windows, Windows Phone und Xbox sowie Linux, macOS, iOS, Android und verschiedene andere Plattformen.</span><span class="sxs-lookup"><span data-stu-id="55c05-453">Monogame currently supports Windows, Windows Phone, and Xbox, as well as Linux, macOS, iOS, Android, and several other platforms.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-454">MonoGame</span><span class="sxs-lookup"><span data-stu-id="55c05-454">MonoGame</span></span></td>
        <td><a href="http://www.monogame.net"><span data-ttu-id="55c05-455">MonoGame-Website</span><span class="sxs-lookup"><span data-stu-id="55c05-455">MonoGame website</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-456">MonoGame-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="55c05-456">MonoGame Documentation</span></span></td>
        <td><a href="http://www.monogame.net/documentation/"><span data-ttu-id="55c05-457">MonoGame-Dokumentation (aktuell)</span><span class="sxs-lookup"><span data-stu-id="55c05-457">MonoGame Documentation (latest)</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-458">MonoGame-Downloads</span><span class="sxs-lookup"><span data-stu-id="55c05-458">Monogame Downloads</span></span></td>
        <td><span data-ttu-id="55c05-459"><a href="http://www.monogame.net/downloads/">Laden Sie Versionen, Entwicklungsbuilds und Quellcode</a> von der MonoGame-Website herunter, oder <a href="https://www.nuget.org/profiles/MonoGame">rufen Sie die neueste Version über NuGet ab</a>.</span><span class="sxs-lookup"><span data-stu-id="55c05-459"><a href="http://www.monogame.net/downloads/">Download releases, development builds, and source code</a> from the MonoGame website, or <a href="https://www.nuget.org/profiles/MonoGame">get the latest release via NuGet</a>.</span></span>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-460">Beispiel für ein MonoGame 2D UWP-Spiel</span><span class="sxs-lookup"><span data-stu-id="55c05-460">MonoGame 2D UWP game sample</span></span></td>
        <td><a href="../get-started/get-started-tutorial-game-mg2d.md"><span data-ttu-id="55c05-461">Erstellen eines UWP-Spiels in MonoGame-2D</span><span class="sxs-lookup"><span data-stu-id="55c05-461">Create a UWP game in MonoGame 2D</span></span></a></td>
    </tr>    
</table>


#### <a name="cocos2d"></a><span data-ttu-id="55c05-462">Cocos2d</span><span class="sxs-lookup"><span data-stu-id="55c05-462">Cocos2d</span></span>

<span data-ttu-id="55c05-463">Cocos2d-X ist eine plattformübergreifende Suite mit Open-Source-Spieleentwicklungsengine und Tools, die die Erstellung von UWP-Spielen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="55c05-463">Cocos2d-x is a cross-platform open source game development engine and tools suite that supports building UWP games.</span></span> <span data-ttu-id="55c05-464">Ab Version3 werden auch 3D-Features hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="55c05-464">Beginning with version 3, 3D features are being added as well.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-465">Cocos2d-X</span><span class="sxs-lookup"><span data-stu-id="55c05-465">Cocos2d-x</span></span></td>
        <td><a href="http://www.cocos2d-x.org/"><span data-ttu-id="55c05-466">Was ist Cocos2d-X?</span><span class="sxs-lookup"><span data-stu-id="55c05-466">What is Cocos2d-x?</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-467">Cocos2d-X-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="55c05-467">Cocos2d-x programmer's guide</span></span></td>
        <td><a href="http://www.cocos2d-x.org/programmersguide/"><span data-ttu-id="55c05-468">Cocos2d-X-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="55c05-468">Cocos2d-x Programmers Guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-469">Cocos2d-X unter Windows10 (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="55c05-469">Cocos2d-x on Windows 10 (blog post)</span></span></td>
        <td><a href="https://blogs.windows.com/buildingapps/2015/06/15/running-cocos2d-x-on-windows-10/"><span data-ttu-id="55c05-470">Ausführen von Cocos2d-X unter Windows10</span><span class="sxs-lookup"><span data-stu-id="55c05-470">Running Cocos2d-x on Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-471">Fügen Sie mit PlayFab LiveOps hinzu</span><span class="sxs-lookup"><span data-stu-id="55c05-471">Add LiveOps using PlayFab</span></span></td>
        <td><a href="https://api.playfab.com/docs/getting-started/cocos2d-x-getting-started-guide"><span data-ttu-id="55c05-472">Erste Schritte – führen Sie Ihren ersten PlayFab-API-Aufruf aus Ihrem Cocos2d-Spiel durch</span><span class="sxs-lookup"><span data-stu-id="55c05-472">Getting started - Make your first PlayFab API call from your Cocos2d game</span></span></a></td>
    </tr>
</table>


#### <a name="unreal-engine"></a><span data-ttu-id="55c05-473">Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="55c05-473">Unreal Engine</span></span>

<span data-ttu-id="55c05-474">Unreal Engine4 ist eine umfassende, für alle Arten von Spielen und Entwicklern geeignete Suite mit Tools für die Spieleentwicklung.</span><span class="sxs-lookup"><span data-stu-id="55c05-474">Unreal Engine 4 is a complete suite of game development tools for all types of games and developers.</span></span> <span data-ttu-id="55c05-475">Die Unreal Engine wird von Spieleentwicklern auf der ganzen Welt für besonders anspruchsvolle Konsolen- und PC-Spiele eingesetzt.</span><span class="sxs-lookup"><span data-stu-id="55c05-475">For the most demanding console and PC games, Unreal Engine is used by game developers worldwide.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-476">Übersicht über die Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="55c05-476">Unreal Engine overview</span></span></td>
        <td><a href="https://www.unrealengine.com/what-is-unreal-engine-4"><span data-ttu-id="55c05-477">Unreal Engine4</span><span class="sxs-lookup"><span data-stu-id="55c05-477">Unreal Engine 4</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-478">Fügen Sie mit PlayFab LiveOps hinzu - C++</span><span class="sxs-lookup"><span data-stu-id="55c05-478">Add LiveOps using PlayFab - C++</span></span></td>
        <td><a href="https://api.playfab.com/docs/getting-started/unreal-cpp-getting-started"><span data-ttu-id="55c05-479">Erste Schritte – führen Sie Ihren ersten PlayFab-API-Aufruf aus Ihrem Unreal-Spiel durch</span><span class="sxs-lookup"><span data-stu-id="55c05-479">Getting started - Make your first PlayFab API call from your Unreal game</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-480">Fügen Sie mit PlayFab LiveOps hinzu - Entwürfe</span><span class="sxs-lookup"><span data-stu-id="55c05-480">Add LiveOps using PlayFab - Blueprints</span></span></td>
        <td><a href="https://api.playfab.com/docs/getting-started/unreal-blueprints-getting-started"><span data-ttu-id="55c05-481">Erste Schritte – führen Sie Ihren ersten PlayFab-API-Aufruf aus Ihrem Unreal-Spiel durch</span><span class="sxs-lookup"><span data-stu-id="55c05-481">Getting started - Make your first PlayFab API call from your Unreal game</span></span></a></td>
    </tr>
</table>

#### <a name="babylonjs"></a><span data-ttu-id="55c05-482">BabylonJS</span><span class="sxs-lookup"><span data-stu-id="55c05-482">BabylonJS</span></span>

<span data-ttu-id="55c05-483">BabylonJS ist ein vollständiges JavaScript-Framework für die Erstellung von 3D-Spielen mit HTML5, WebGL, WebVR und Web-Audio.</span><span class="sxs-lookup"><span data-stu-id="55c05-483">BabylonJS is a complete JavaScript framework for building 3D games with HTML5, WebGL, WebVR, and Web Audio.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-484">BabylonJS</span><span class="sxs-lookup"><span data-stu-id="55c05-484">BabylonJS</span></span></td>
        <td><a href="http://www.babylonjs.com/"><span data-ttu-id="55c05-485">BabylonJS</span><span class="sxs-lookup"><span data-stu-id="55c05-485">BabylonJS</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-486">WebGL-3D mit HTML5 und BabylonJS (Videoserie)</span><span class="sxs-lookup"><span data-stu-id="55c05-486">WebGL 3D with HTML5 and BabylonJS (video series)</span></span></td>
        <td><a href="https://channel9.msdn.com/Series/Introduction-to-WebGL-3D-with-HTML5-and-Babylonjs/01"><span data-ttu-id="55c05-487">Learning WebGL 3D- und BabylonJS</span><span class="sxs-lookup"><span data-stu-id="55c05-487">Learning WebGL 3D and BabylonJS</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-488">Erstellen eines plattformübergreifenden WebGL-Spiels mit BabylonJS</span><span class="sxs-lookup"><span data-stu-id="55c05-488">Building a cross-platform WebGL game with BabylonJS</span></span></td>
        <td><a href="https://www.smashingmagazine.com/2016/07/babylon-js-building-sponza-a-cross-platform-webgl-game/"><span data-ttu-id="55c05-489">Verwenden von BabylonJS zur Entwicklung eines plattformübergreifenden Spiels</span><span class="sxs-lookup"><span data-stu-id="55c05-489">Use BabylonJS to develop a cross-platform game</span></span></a></td>
    </tr>    
</table>

### <a name="porting-your-game"></a><span data-ttu-id="55c05-490">Portieren Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="55c05-490">Porting your game</span></span>

<span data-ttu-id="55c05-491">Entwicklern, die bereits über ein Spiel verfügen, stehen zahlreiche Ressourcen und Handbücher für eine schnelle UWP-Portierung ihres Spiels zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="55c05-491">If you have an existing game, there are many resources and guides available to help you quickly bring your game to the UWP.</span></span> <span data-ttu-id="55c05-492">Als Starthilfe bei der Portierung empfiehlt sich unter Umständen die Verwendung einer [Brücke für die universelle Windows-Plattform](#universal-windows-platform-bridges).</span><span class="sxs-lookup"><span data-stu-id="55c05-492">To jumpstart your porting efforts, you might also consider using a [Universal Windows Platform Bridge](#universal-windows-platform-bridges).</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-493">Portieren einer Windows8-App zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="55c05-493">Porting a Windows 8 app to a Universal Windows Platform app</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt238322"><span data-ttu-id="55c05-494">Wechsel von Windows-Runtime 8.x zu UWP</span><span class="sxs-lookup"><span data-stu-id="55c05-494">Move from Windows Runtime 8.x to UWP</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-495">Portieren einer Windows 8-App zu einer UWP-App (Universelle Windows-Plattform) (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-495">Porting a Windows 8 app to a Universal Windows Platform app (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Series/A-Developers-Guide-to-Windows-10/21"><span data-ttu-id="55c05-496">Portieren von Windows 8.1-Apps zu Windows 10</span><span class="sxs-lookup"><span data-stu-id="55c05-496">Porting 8.1 Apps to Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-497">Portieren einer iOS-App zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="55c05-497">Porting an iOS app to a Universal Windows Platform app</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt238320"><span data-ttu-id="55c05-498">Wechsel von iOS zu UWP</span><span class="sxs-lookup"><span data-stu-id="55c05-498">Move from iOS to UWP</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-499">Portieren einer Silverlight-App zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="55c05-499">Porting a Silverlight app to a Universal Windows Platform app</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt238323"><span data-ttu-id="55c05-500">Wechsel von Windows Phone Silverlight zu UWP</span><span class="sxs-lookup"><span data-stu-id="55c05-500">Move from Windows Phone Silverlight to UWP</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-501">Portieren von XAML oder Silverlight zu einer UWP-App (Universelle Windows-Plattform) (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-501">Porting from XAML or Silverlight to a Universal Windows Platform app (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/Build/2015/3-741"><span data-ttu-id="55c05-502">Portieren einer App von XAML oder Silverlight zu Windows 10</span><span class="sxs-lookup"><span data-stu-id="55c05-502">Porting an App from XAML or Silverlight to Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-503">Portieren eines Xbox-Spiels zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="55c05-503">Porting an Xbox game to a Universal Windows Platform app</span></span></td>
        <td><a href="https://developer.xboxlive.com/en-us/platform/development/education/Documents/Porting%20from%20Xbox%20One%20to%20Windows%2010.aspx"><span data-ttu-id="55c05-504">Portieren von Xbox One zu Windows 10 (UWP)</span><span class="sxs-lookup"><span data-stu-id="55c05-504">Porting from Xbox One to Windows 10 UWP</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-505">Portieren von DirectX 9 zu DirectX 11</span><span class="sxs-lookup"><span data-stu-id="55c05-505">Porting from DirectX 9 to DirectX 11</span></span></td>
        <td><a href="porting-your-directx-9-game-to-windows-store.md"><span data-ttu-id="55c05-506">Portieren von DirectX9 zur universellen Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="55c05-506">Port from DirectX 9 to Universal Windows Platform (UWP)</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-507">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="55c05-507">Porting from Direct3D 11 to Direct3D 12</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt431709"><span data-ttu-id="55c05-508">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="55c05-508">Porting from Direct3D 11 to Direct3D 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-509">Portieren von OpenGLES zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="55c05-509">Porting from OpenGL ES to Direct3D 11</span></span></td>
        <td><a href="port-from-opengl-es-2-0-to-directx-11-1.md"><span data-ttu-id="55c05-510">Portieren von OpenGLES2.0 zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="55c05-510">Port from OpenGL ES 2.0 to Direct3D 11</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-511">OpenGLES2.0 zu Direct3D11 mit ANGLE</span><span class="sxs-lookup"><span data-stu-id="55c05-511">OpenGL ES to Direct3D 11 using ANGLE</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?linkid=618387"><span data-ttu-id="55c05-512">ANGLE</span><span class="sxs-lookup"><span data-stu-id="55c05-512">ANGLE</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-513">Entsprechungen für die klassische Windows-API in der UWP</span><span class="sxs-lookup"><span data-stu-id="55c05-513">Classic Windows API equivalents in the UWP</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/hh464945"><span data-ttu-id="55c05-514">Alternativen zu Windows-APIs in Apps für die Universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="55c05-514">Alternatives to Windows APIs in Universal Windows Platform (UWP) apps</span></span></a></td>
    </tr>
</table>


## <a name="prototype-and-design"></a><span data-ttu-id="55c05-515">Prototyp und Design</span><span class="sxs-lookup"><span data-stu-id="55c05-515">Prototype and design</span></span>


<span data-ttu-id="55c05-516">Nachdem Sie sich entschieden haben, welche Art von Spiel Sie entwickeln und welche Tools und Grafiktechnologie Sie dabei verwenden möchten, können Sie sich der Gestaltung zuwenden und einen Prototyp entwickeln.</span><span class="sxs-lookup"><span data-stu-id="55c05-516">Now that you've decided the type of game you want to create and the tools and graphics technology you'll use to build it, you're ready to get started with the design and prototype.</span></span> <span data-ttu-id="55c05-517">Da es sich bei Ihrem Spiel im Grunde um eine UWP-App (Universelle Windows-Plattform) handelt, beginnen Sie dort.</span><span class="sxs-lookup"><span data-stu-id="55c05-517">At its core, your game is a Universal Windows Platform app, so that's where you'll begin.</span></span>

### <a name="introduction-to-the-universal-windows-platform-uwp"></a><span data-ttu-id="55c05-518">Einführung in die universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="55c05-518">Introduction to the Universal Windows Platform (UWP)</span></span>

<span data-ttu-id="55c05-519">Windows10 führt die universelle Windows-Plattform (UWP) ein. Diese stellt eine gemeinsame, übergreifende API-Plattform für Windows10-Geräte bereit.</span><span class="sxs-lookup"><span data-stu-id="55c05-519">Windows 10 introduces the Universal Windows Platform (UWP), which provides a common API platform across Windows 10 devices.</span></span> <span data-ttu-id="55c05-520">Bei der UWP handelt es sich um eine Weiterentwicklung und Erweiterung des Windows-Runtime-Modells zu einem geschlossenen, einheitlichen Kern.</span><span class="sxs-lookup"><span data-stu-id="55c05-520">UWP evolves and expands the Windows Runtime model and hones it into a cohesive, unified core.</span></span> <span data-ttu-id="55c05-521">Für die UWP entwickelte Spiele können WinRT-APIs aufrufen, die bei allen Geräten vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="55c05-521">Games that target the UWP can call WinRT APIs that are common to all devices.</span></span> <span data-ttu-id="55c05-522">Da die UWP eine garantierte API-Ebene bereitstellt, können Sie ein einzelnes App-Paket erstellen, das dann auf allen Windows10-Geräten installiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="55c05-522">Because the UWP provides guaranteed API layers, you can choose to create a single app package that will install across Windows 10 devices.</span></span> <span data-ttu-id="55c05-523">Bei Bedarf kann Ihr Spiel natürlich auch weiterhin spezifische APIs der Geräte aufrufen, auf denen das Spiel ausgeführt wird – etwa einige klassische Windows-APIs von Win32 und .NET.</span><span class="sxs-lookup"><span data-stu-id="55c05-523">And if you want to, your game can still call APIs (including some classic Windows APIs from Win32 and .NET) that are specific to the devices your game runs on.</span></span>

<span data-ttu-id="55c05-524">Im Anschluss finden Sie praktische Handbücher, die sich ausführlich mit UWP-Apps (Universelle Windows-Plattform) auseinandersetzen und hilfreiche Erkenntnisse zur Plattform liefern.</span><span class="sxs-lookup"><span data-stu-id="55c05-524">The following are excellent guides that discuss the Universal Windows Platform apps in detail, and are recommended reading to help you understand the platform.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-525">Einführung in UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="55c05-525">Introduction to Universal Windows Platform apps</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/dn726767"><span data-ttu-id="55c05-526">Was ist eine UWP-App (Universelle Windows-Plattform)?</span><span class="sxs-lookup"><span data-stu-id="55c05-526">What's a Universal Windows Platform app?</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-527">Übersicht über die UWP</span><span class="sxs-lookup"><span data-stu-id="55c05-527">Overview of the UWP</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/dn894631"><span data-ttu-id="55c05-528">Anleitung für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-528">Guide to UWP apps</span></span></a></td>
    </tr>
</table>
 

### <a name="getting-started-with-uwp-development"></a><span data-ttu-id="55c05-529">Erste Schritte bei der UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="55c05-529">Getting started with UWP development</span></span>

<span data-ttu-id="55c05-530">Die Vorbereitung auf die Entwicklung einer UWP-App (Universelle Windows-Plattform) ist ganz einfach und im Handumdrehen erledigt.</span><span class="sxs-lookup"><span data-stu-id="55c05-530">Getting set up and ready to develop a Universal Windows Platform app is quick and easy.</span></span> <span data-ttu-id="55c05-531">Die erforderlichen Schritte werden in den folgenden Handbüchern erläutert:</span><span class="sxs-lookup"><span data-stu-id="55c05-531">The following guides take you through the process step-by-step.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-532">Erste Schritte bei der UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="55c05-532">Getting started with UWP development</span></span></td>
        <td><a href="https://dev.windows.com/getstarted"><span data-ttu-id="55c05-533">Erste Schritte mit Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-533">Get started with Windows apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-534">Vorbereitung auf die UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="55c05-534">Getting set up for UWP development</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/dn726766"><span data-ttu-id="55c05-535">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="55c05-535">Get set up</span></span></a></td>
    </tr>
</table>

<span data-ttu-id="55c05-536">Wenn Sie noch keine Erfahrungen mit der UWP-Programmierung haben und die Verwendung von XAML in Ihrem Spiel in Betracht ziehen (siehe [Auswählen von Grafiktechnologie und Programmiersprache](#choosing-your-graphics-technology-and-programming-language)), ist die Videoserie [Windows10-Entwicklung für Neueinsteiger](https://channel9.msdn.com/Series/Windows-10-development-for-absolute-beginners) ein guter Ausgangspunkt.</span><span class="sxs-lookup"><span data-stu-id="55c05-536">If you're an "absolute beginner" to UWP programming, and are considering using XAML in your game (see [Choosing your graphics technology and programming language](#choosing-your-graphics-technology-and-programming-language)), the [Windows 10 development for absolute beginners](https://channel9.msdn.com/Series/Windows-10-development-for-absolute-beginners) video series is a good place to start.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-537">Einsteigerhandbuch für die Windows10-Entwicklung mit XAML (Videoserie)</span><span class="sxs-lookup"><span data-stu-id="55c05-537">Beginners guide to Windows 10 development with XAML (Video series)</span></span></td>
        <td><a href="https://channel9.msdn.com/Series/Windows-10-development-for-absolute-beginners"><span data-ttu-id="55c05-538">Windows10-Entwicklung für Neueinsteiger</span><span class="sxs-lookup"><span data-stu-id="55c05-538">Windows 10 development for absolute beginners</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-539">Ankündigung der Windows10-Neueinsteigerserie mit XAML (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="55c05-539">Announcing the Windows 10 absolute beginners series using XAML (blog post)</span></span></td>
        <td><a href="http://blogs.windows.com/buildingapps/2015/09/30/windows-10-development-for-absolute-beginners/"><span data-ttu-id="55c05-540">Windows 10-Entwicklung für Neueinsteiger</span><span class="sxs-lookup"><span data-stu-id="55c05-540">Windows 10 development for absolute beginners</span></span></a></td>
    </tr>
</table>

### <a name="uwp-development-concepts"></a><span data-ttu-id="55c05-541">UWP-Entwicklungskonzepte</span><span class="sxs-lookup"><span data-stu-id="55c05-541">UWP development concepts</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-542">Übersicht über die Entwicklung von UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="55c05-542">Overview of Universal Windows Platform app development</span></span></td>
        <td><a href="https://dev.windows.com/develop"><span data-ttu-id="55c05-543">Entwickeln von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-543">Develop Windows apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-544">Übersicht über die Netzwerkprogrammierung der UWP</span><span class="sxs-lookup"><span data-stu-id="55c05-544">Overview of network programming in the UWP</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt280378"><span data-ttu-id="55c05-545">Netzwerk und Webdienste</span><span class="sxs-lookup"><span data-stu-id="55c05-545">Networking and web services</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-546">Verwenden von „Windows.Web.HTTP“ und „Windows.Networking.Sockets“ in Spielen</span><span class="sxs-lookup"><span data-stu-id="55c05-546">Using Windows.Web.HTTP and Windows.Networking.Sockets in games</span></span></td>
        <td><a href="work-with-networking-in-your-directx-game.md"><span data-ttu-id="55c05-547">Netzwerkfunktionen für Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-547">Networking for games</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-548">Asynchrone Programmierkonzepte der UWP</span><span class="sxs-lookup"><span data-stu-id="55c05-548">Asynchronous programming concepts in the UWP</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt187335"><span data-ttu-id="55c05-549">Asynchrone Programmierung</span><span class="sxs-lookup"><span data-stu-id="55c05-549">Asynchronous programming</span></span></a></td>
    </tr>
</table>

### <a name="windows-desktop-apisto-uwp"></a><span data-ttu-id="55c05-550">Windows Desktop APIsto UWP</span><span class="sxs-lookup"><span data-stu-id="55c05-550">Windows Desktop APIsto UWP</span></span>

<span data-ttu-id="55c05-551">Hier finden Sie einige Links, die Sie beim Wechsel von Windows-Desktop-Spielen zu UWP-Spielen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="55c05-551">These are some links to help you move your Windows desktop game to UWP.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-552">Verwenden Sie vorhandenen C++-Code für die UWP-Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="55c05-552">Use existing C++ code for UWP game development</span></span></td>
        <td><a href="https://docs.microsoft.com/cpp/porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app"><span data-ttu-id="55c05-553">Vorgehensweise: Verwenden von vorhandenem C++-Code in einer UWP-App</span><span class="sxs-lookup"><span data-stu-id="55c05-553">How to: Use existing C++ code in a UWP app</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-554">UWP-APIs für Win32- und COM-APIs</span><span class="sxs-lookup"><span data-stu-id="55c05-554">UWP APIs for Win32 and COM APIs</span></span></td>
        <td><a href="https://docs.microsoft.com/uwp/win32-and-com/win32-and-com-for-uwp-apps"><span data-ttu-id="55c05-555">Win32- und COM-APIs für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-555">Win32 and COM APIs for UWP apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-556">Nicht unterstützte CRT-Funktionen in UWP</span><span class="sxs-lookup"><span data-stu-id="55c05-556">Unsupported CRT functions in UWP</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/jj606124.aspx"><span data-ttu-id="55c05-557">Nicht unterstützte CRT-Funktionen in Apps für die universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="55c05-557">CRT functions not supported in Universal Windows Platform apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-558">Alternativen zu Windows-APIs</span><span class="sxs-lookup"><span data-stu-id="55c05-558">Alternatives for Windows APIs</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt592894.aspx"><span data-ttu-id="55c05-559">Alternativen zu Windows-APIs in Apps für die universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="55c05-559">Alternatives to Windows APIs in Universal Windows Platform (UWP) apps</span></span></a></td>
    </tr>
</table>
 

### <a name="process-lifetime-management"></a><span data-ttu-id="55c05-560">Prozesslebensdauer-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="55c05-560">Process lifetime management</span></span>

<span data-ttu-id="55c05-561">Prozesslebensdauer-Verwaltung (oder App-Lebenszyklus) beschreibt die verschiedenen Aktivierungszustände, die eine UWP-App (Universelle Windows-Plattform) durchlaufen kann.</span><span class="sxs-lookup"><span data-stu-id="55c05-561">Process lifetime management, or app lifecyle, describes the various activation states that a Universal Windows Platform app can transition through.</span></span> <span data-ttu-id="55c05-562">Ihr Spiel kann aktiviert, angehalten, fortgesetzt oder beendet werden und diese Zustände auf unterschiedliche Arten durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="55c05-562">Your game can be activated, suspended, resumed, or terminated, and can transition through those states in a variety of ways.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-563">Behandeln von App-Lebenszyklusübergängen</span><span class="sxs-lookup"><span data-stu-id="55c05-563">Handling app lifecyle transitions</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt243287"><span data-ttu-id="55c05-564">App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="55c05-564">App lifecycle</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-565">Auslösen von App-Übergängen mithilfe von Microsoft Visual Studio</span><span class="sxs-lookup"><span data-stu-id="55c05-565">Using Microsoft Visual Studio to trigger app transitions</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/hh974425.aspx"><span data-ttu-id="55c05-566">So wird's gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen für UWP-Apps in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="55c05-566">How to trigger suspend, resume, and background events for UWP apps in Visual Studio</span></span></a></td>
    </tr>
</table>
 

### <a name="designing-game-ux"></a><span data-ttu-id="55c05-567">Gestalten der UX von Spielen</span><span class="sxs-lookup"><span data-stu-id="55c05-567">Designing game UX</span></span>

<span data-ttu-id="55c05-568">Großartigen Spielen liegt in der Regel ein kreatives Design zugrunde.</span><span class="sxs-lookup"><span data-stu-id="55c05-568">The genesis of a great game is inspired design.</span></span>

<span data-ttu-id="55c05-569">Spiele und Apps teilen sich zwar einige Benutzeroberflächenelemente und Designprinzipien, beim Spieldesign werden jedoch häufig ein ganz besonderer Look und ein einzigartiges Spielgefühl angestrebt.</span><span class="sxs-lookup"><span data-stu-id="55c05-569">Games share some common user interface elements and design principles with apps, but games often have a unique look, feel, and design goal for their user experience.</span></span> <span data-ttu-id="55c05-570">Spiele sind erfolgreich, wenn in beiden Bereichen ein durchdachtes Design gewählt wird: Wann sollten Sie in Ihrem Spiel bewährte Benutzeroberflächenelemente verwenden, und wann sollten Sie davon abweichen und innovativ vorgehen?</span><span class="sxs-lookup"><span data-stu-id="55c05-570">Games succeed when thoughtful design is applied to both aspects—when should your game use tested UX, and when should it diverge and innovate?</span></span> <span data-ttu-id="55c05-571">Die Darstellungstechnologie, die Sie für das Spiel auswählen – DirectX, XAML, HTML5 oder eine beliebige Kombination –, wird sich auf die Implementierungsdetails auswirken. Die von Ihnen angewendeten Entwurfsprinzipien sind aber nicht von der jeweiligen Wahl abhängig.</span><span class="sxs-lookup"><span data-stu-id="55c05-571">The presentation technology that you choose for your game—DirectX, XAML, HTML5, or some combination of the three—will influence implementation details, but the design principles you apply are largely independent of that choice.</span></span>

<span data-ttu-id="55c05-572">Zusätzlich zum UX-Design müssen Sie sich auch mit dem Gameplay-Design auseinandersetzen, was unter anderem Aspekte wie Leveldesign, Pacing und Umgebungsdesign umfasst. Da es sich hierbei um eine ganz eigene Kunstform handelt, gehen wir in diesem Dokument nicht näher darauf ein, sondern überlassen diesen Bereich ganz Ihnen und Ihrem Team.</span><span class="sxs-lookup"><span data-stu-id="55c05-572">Separately from UX design, gameplay design such as level design, pacing, world design, and other aspects is an art form of its own—one that's up to you and your team, and not covered in this development guide.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-573">UWP-Gestaltungsgrundlagen und -richtlinien</span><span class="sxs-lookup"><span data-stu-id="55c05-573">UWP design basics and guidelines</span></span></td>
        <td><a href="https://dev.windows.com/design"><span data-ttu-id="55c05-574">Gestalten von UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-574">Designing UWP apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-575">Gestalten für App-Lebenszykluszustände</span><span class="sxs-lookup"><span data-stu-id="55c05-575">Designing for app lifecycle states</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/dn611862"><span data-ttu-id="55c05-576">UX-Richtlinien für das Starten, Anhalten und Fortsetzen von Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-576">UX guidelines for launch, suspend, and resume</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-577">Entwerfen Sie Ihre UWP-App für Xbox One und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="55c05-577">Design your UWP app for Xbox One and television screens</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/design/devices/designing-for-tv"><span data-ttu-id="55c05-578">Entwerfen für Xbox und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="55c05-578">Designing for Xbox and TV</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-579">Ausrichten auf verschiedene Geräteformfaktoren (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-579">Targeting multiple device form factors (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Designing-Games-for-a-Windows-Core-World"><span data-ttu-id="55c05-580">Entwerfen von Spielen für eine WindowsCore-Welt</span><span class="sxs-lookup"><span data-stu-id="55c05-580">Designing Games for a Windows Core World</span></span></a></td>
    </tr>   
</table>
 

#### <a name="color-guideline-and-palette"></a><span data-ttu-id="55c05-581">Farbrichtlinie und -palette</span><span class="sxs-lookup"><span data-stu-id="55c05-581">Color guideline and palette</span></span>

<span data-ttu-id="55c05-582">Eine einheitliche Farbrichtlinie verbessert die Spielästhetik, vereinfacht die Navigation und ist ein wirksames Mittel, um Spieler über Menü- und HUD-Funktionen zu informieren.</span><span class="sxs-lookup"><span data-stu-id="55c05-582">Following a consistent color guideline in your game improves aesthetics, aids navigation, and is a powerful tool to inform the player of menu and HUD functionality.</span></span> <span data-ttu-id="55c05-583">Eine einheitliche Farbgestaltung von Spielelementen wie Warnungen, Schäden, Erfahrungspunkten und Erfolgen kann die Übersichtlichkeit der Benutzeroberfläche verbessern und explizite Beschriftungen überflüssig machen.</span><span class="sxs-lookup"><span data-stu-id="55c05-583">Consistent coloring of game elements like warnings, damage, XP, and achievements can lead to cleaner UI and reduce the need for explicit labels.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-584">Farbhandbuch</span><span class="sxs-lookup"><span data-stu-id="55c05-584">Color guide</span></span></td>
        <td><a href="https://assets.windowsphone.com/499cd2be-64ed-4b05-a4f5-cd0c9ad3f6a3/101_BestPractices_Color_InvariantCulture_Default.zip"><span data-ttu-id="55c05-585">Bewährte Methoden: Farbe</span><span class="sxs-lookup"><span data-stu-id="55c05-585">Best Practices: Color</span></span></a></td>
    </tr>
</table>
 

#### <a name="typography"></a><span data-ttu-id="55c05-586">Typografie</span><span class="sxs-lookup"><span data-stu-id="55c05-586">Typography</span></span>

<span data-ttu-id="55c05-587">Durch den angemessenen Einsatz von Typografie können Sie Ihr Spiel in vielerlei Hinsicht verbessern – etwa in Bezug auf UI-Layout, Navigation, Lesbarkeit, Atmosphäre und Spielerimmersion.</span><span class="sxs-lookup"><span data-stu-id="55c05-587">The appropriate use of typography enhances many aspects of your game, including UI layout, navigation, readability, atmosphere, brand, and player immersion.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-588">Typografiehandbuch</span><span class="sxs-lookup"><span data-stu-id="55c05-588">Typography guide</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=535007"><span data-ttu-id="55c05-589">Bewährte Methoden: Typografie</span><span class="sxs-lookup"><span data-stu-id="55c05-589">Best Practices: Typography</span></span></a></td>
    </tr>
</table>
 

#### <a name="ui-map"></a><span data-ttu-id="55c05-590">UI-Zuordnung</span><span class="sxs-lookup"><span data-stu-id="55c05-590">UI map</span></span>

<span data-ttu-id="55c05-591">Bei einer UI-Zuordnung handelt es sich um eine Layoutübersicht über die Navigation und Menüs eines Spiels in Form eines Flussdiagramms.</span><span class="sxs-lookup"><span data-stu-id="55c05-591">A UI map is a layout of game navigation and menus expressed as a flowchart.</span></span> <span data-ttu-id="55c05-592">Die UI-Zuordnung verbessert die Nachvollziehbarkeit der Oberfläche und der Navigationspfade eines Spiels für alle Beteiligten und trägt zur frühzeitigen Erkennung potenzieller Probleme und Sackgassen bei.</span><span class="sxs-lookup"><span data-stu-id="55c05-592">The UI map helps all involved stakeholders understand the game’s interface and navigation paths, and can expose potential roadblocks and dead ends early in the development cycle.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-593">Anleitung für die UI-Zuordnung</span><span class="sxs-lookup"><span data-stu-id="55c05-593">UI map guide</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=535008"><span data-ttu-id="55c05-594">Bewährte Methoden: UI-Zuordnung</span><span class="sxs-lookup"><span data-stu-id="55c05-594">Best Practices: UI Map</span></span></a></td>
    </tr>
</table>

### <a name="game-audio"></a><span data-ttu-id="55c05-595">Audio in Spielen</span><span class="sxs-lookup"><span data-stu-id="55c05-595">Game audio</span></span>

<span data-ttu-id="55c05-596">Anleitungen und Referenzen für die Implementierung von Audio in Spielen mit XAudio2, XAPO und Windows Sonic.</span><span class="sxs-lookup"><span data-stu-id="55c05-596">Guides and references for implementing audio in games using XAudio2, XAPO, and Windows Sonic.</span></span> <span data-ttu-id="55c05-597">XAudio2 ist eine Low-Level-Audio-API, die eine grundlegende Signalverarbeitung und -abmischung zum Entwickeln von Audiomodulen mit hoher Leistung für Spiele bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="55c05-597">XAudio2 is a low-level audio API that provides signal processing and mixing foundation for developing high performance audio engines.</span></span> <span data-ttu-id="55c05-598">XAPO-API ermöglicht die Erstellung von plattformübergreifenden Audioverarbeitungsobjekten (XAPO) zur Verwendung in XAudio2 für Windows und Xbox.</span><span class="sxs-lookup"><span data-stu-id="55c05-598">XAPO API allows the creation of cross-platform audio processing objects (XAPO) for use in XAudio2 on both Windows and Xbox.</span></span> <span data-ttu-id="55c05-599">Mit der Windows Sonic Audiounterstützung können Sie Ihrem Spiel oder der Streaming-Media-Anwendung Dolby Atmos for Home Theater, Dolby Atmos for Headphones und Windows kopfbezogene Übertragungsfunktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="55c05-599">Windows Sonic audio support allows you to add Dolby Atmos for Home Theater, Dolby Atmos for Headphones, and Windows HRTF support to your game or streaming media application.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-600">XAudio2-APIs</span><span class="sxs-lookup"><span data-stu-id="55c05-600">XAudio2 APIs</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx"><span data-ttu-id="55c05-601">Programmieranleitung und API-Referenz für XAudio2</span><span class="sxs-lookup"><span data-stu-id="55c05-601">Programming guide and API reference for XAudio2</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-602">Plattformübergreifende Audioverarbeitungsobjekte erstellen</span><span class="sxs-lookup"><span data-stu-id="55c05-602">Create cross-platform audio processing objects</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx"><span data-ttu-id="55c05-603">XAPO: Übersicht</span><span class="sxs-lookup"><span data-stu-id="55c05-603">XAPO Overview</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-604">Einführung in Audio-Konzepte</span><span class="sxs-lookup"><span data-stu-id="55c05-604">Intro to audio concepts</span></span></td>
        <td><a href="working-with-audio-in-your-directx-game.md"><span data-ttu-id="55c05-605">Audio für Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-605">Audio for games</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-606">Übersicht über Windows Sonic</span><span class="sxs-lookup"><span data-stu-id="55c05-606">Windows Sonic overview</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt807491.aspx"><span data-ttu-id="55c05-607">Raumklang</span><span class="sxs-lookup"><span data-stu-id="55c05-607">Spatial sound</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-608">Windows-Sonic Raumklang - Beispiele</span><span class="sxs-lookup"><span data-stu-id="55c05-608">Windows Sonic spatial sound samples</span></span></td>
        <td><a href="https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/UWPSamples/Audio"><span data-ttu-id="55c05-609">Xbox Advanced Technology Group – Audiobeispiele</span><span class="sxs-lookup"><span data-stu-id="55c05-609">Xbox Advanced Technology Group audio samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-610">Hier erfahren Sie, wie Sie Windows Sonic in Ihre Spiele (Video) integrieren</span><span class="sxs-lookup"><span data-stu-id="55c05-610">Learn how to integrate Windows Sonic into your games (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/GDC/GDC-2017/GDC2017-002"><span data-ttu-id="55c05-611">Einführung in die räumliche Audiowiedergabe Funktionen für Xbox oder Windows</span><span class="sxs-lookup"><span data-stu-id="55c05-611">Introducing Spatial Audio Capabilities for Xbox andWindows</span></span></a></td>
    </tr>
</table>

### <a name="directx-development"></a><span data-ttu-id="55c05-612">DirectX-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="55c05-612">DirectX development</span></span>

<span data-ttu-id="55c05-613">Anleitungen und Referenzen für die Entwicklung von DirectX-Spielen</span><span class="sxs-lookup"><span data-stu-id="55c05-613">Guides and references for DirectX game development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-614">DirectX für die UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="55c05-614">DirectX for UWP development</span></span></td>
        <td><a href="directx-programming.md"><span data-ttu-id="55c05-615">DirectX-Programmierung</span><span class="sxs-lookup"><span data-stu-id="55c05-615">DirectX programming</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-616">Lernprogramm: Erstellen eines UWP-DirectX-Spiels</span><span class="sxs-lookup"><span data-stu-id="55c05-616">Tutorial: How to create a UWP DirectX game</span></span></td>
        <td><a href="tutorial--create-your-first-uwp-directx-game.md"><span data-ttu-id="55c05-617">Erstellen eines einfachen UWP-Spiels mit DirectX</span><span class="sxs-lookup"><span data-stu-id="55c05-617">Create a simple UWP game with DirectX</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-618">DirectX-Interaktionen mit dem UWP-App-Modell</span><span class="sxs-lookup"><span data-stu-id="55c05-618">DirectX interaction with the UWP app model</span></span></td>
        <td><a href="about-the-uwp-user-interface-and-directx.md"><span data-ttu-id="55c05-619">Das App-Objekt und DirectX</span><span class="sxs-lookup"><span data-stu-id="55c05-619">The app object and DirectX</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-620">Videos zu Grafiken und zur DirectX12-Entwicklung (YouTube-Kanal)</span><span class="sxs-lookup"><span data-stu-id="55c05-620">Graphics and DirectX 12 development videos (YouTube channel)</span></span></td>
        <td><a href="https://www.youtube.com/channel/UCiaX2B8XiXR70jaN7NK-FpA"><span data-ttu-id="55c05-621">Informationen zu Microsoft DirectX12 und Grafiken</span><span class="sxs-lookup"><span data-stu-id="55c05-621">Microsoft DirectX 12 and Graphics Education</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-622">Übersichten und Referenzen zu DirectX</span><span class="sxs-lookup"><span data-stu-id="55c05-622">DirectX overviews and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/ee663274"><span data-ttu-id="55c05-623">DirectX-Grafiken und -Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-623">DirectX Graphics and Gaming</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-624">Direct3D12-Programmieranleitung und -referenz</span><span class="sxs-lookup"><span data-stu-id="55c05-624">Direct3D 12 programming guide and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn903821"><span data-ttu-id="55c05-625">Direct3D12-Grafiken</span><span class="sxs-lookup"><span data-stu-id="55c05-625">Direct3D 12 Graphics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-626">DirectX12-Grundlagen (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-626">DirectX 12 fundamentals (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Better-Power-Better-Performance-Your-Game-on-DirectX12"><span data-ttu-id="55c05-627">Bessere Leistung und Performance: Ihr Spiel unter DirectX12</span><span class="sxs-lookup"><span data-stu-id="55c05-627">Better Power, Better Performance: Your Game on DirectX 12</span></span></a></td>
    </tr>
</table>

#### <a name="learning-direct3d-12"></a><span data-ttu-id="55c05-628">Erlernen von Direct3D2</span><span class="sxs-lookup"><span data-stu-id="55c05-628">Learning Direct3D 12</span></span>

<span data-ttu-id="55c05-629">Erfahren Sie mehr über die Änderungen in Direct3D12 und wie Sie mit der Programmierung in Direct3D12 beginnen können.</span><span class="sxs-lookup"><span data-stu-id="55c05-629">Learn what changed in Direct3D 12 and how to start programming using Direct3D 12.</span></span> 

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-630">Einrichten der Programmierumgebung</span><span class="sxs-lookup"><span data-stu-id="55c05-630">Set up programming environment</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn899120.aspx"><span data-ttu-id="55c05-631">Einrichtung der Direct3D12 Programmierungsumgebung</span><span class="sxs-lookup"><span data-stu-id="55c05-631">Direct3D 12 programming environment setup</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-632">Erstellen einer Grundkomponente</span><span class="sxs-lookup"><span data-stu-id="55c05-632">How to create a basic component</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn859356.aspx"><span data-ttu-id="55c05-633">Erstellen einer einfachen Direct3D12-Komponente</span><span class="sxs-lookup"><span data-stu-id="55c05-633">Creating a basic Direct3D 12 component</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-634">Änderungen in Direct3D12</span><span class="sxs-lookup"><span data-stu-id="55c05-634">Changes in Direct3D 12</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn899194.aspx"><span data-ttu-id="55c05-635">Wichtige Änderungen bei der Migration von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="55c05-635">Important changes migrating from Direct3D 11 to Direct3D 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-636">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="55c05-636">How to port from Direct3D 11 to Direct3D 12</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt431709.aspx"><span data-ttu-id="55c05-637">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="55c05-637">Porting from Direct3D 11 to Direct3D 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-638">Konzepte für die Ressourcenbindung (deckt Deskriptor, Deskriptortabelle, Deskriptorheap und Stammsignatur ab)</span><span class="sxs-lookup"><span data-stu-id="55c05-638">Resource binding concepts (covering descriptor, descriptor table, descriptor heap, and root signature)</span></span> </td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn899206.aspx"><span data-ttu-id="55c05-639">Ressourcenbindung in Direct3D12</span><span class="sxs-lookup"><span data-stu-id="55c05-639">Resource binding in Direct3D 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-640">Verwalten des Arbeitsspeichers</span><span class="sxs-lookup"><span data-stu-id="55c05-640">Managing memory</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn899198.aspx"><span data-ttu-id="55c05-641">Arbeitsspeicherverwaltung in Direct3D12</span><span class="sxs-lookup"><span data-stu-id="55c05-641">Memory management in Direct3D 12</span></span></a></td>
    </tr>
</table>
 

#### <a name="directx-tool-kit-and-libraries"></a><span data-ttu-id="55c05-642">DirectX-Toolkit und -Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="55c05-642">DirectX Tool Kit and libraries</span></span>

<span data-ttu-id="55c05-643">Das DirectX-Toolkit, die DirectX-Texturverarbeitungsbibliothek, die DirectXMesh-Geometrieverarbeitungsbibliothek, die UVAtlas-Bibliothek und die DirectXMath-Bibliothek bieten textur-, gitter- und spritebezogene sowie weitere Hilfsprogrammfunktionen und Hilfsklassen für die DirectX-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="55c05-643">The DirectX Tool Kit, DirectX texture processing library, DirectXMesh geometry processing library, UVAtlas library, and DirectXMath library provide texture, mesh, sprite, and other utility functionality and helper classes for DirectX development.</span></span> <span data-ttu-id="55c05-644">Diese Bibliotheken können Ihnen helfen, Entwicklungszeit und -aufwand einzusparen.</span><span class="sxs-lookup"><span data-stu-id="55c05-644">These libraries can help you save development time and effort.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-645">DirectX-Toolkit für DirectX11 herunterladen</span><span class="sxs-lookup"><span data-stu-id="55c05-645">Get DirectX Tool Kit for DirectX 11</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=248929"><span data-ttu-id="55c05-646">DirectXTK</span><span class="sxs-lookup"><span data-stu-id="55c05-646">DirectXTK</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-647">DirectX-Toolkit für DirectX12 herunterladen</span><span class="sxs-lookup"><span data-stu-id="55c05-647">Get DirectX Tool Kit for DirectX 12</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkID=615561"><span data-ttu-id="55c05-648">DirectXTK12</span><span class="sxs-lookup"><span data-stu-id="55c05-648">DirectXTK 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-649">DirectX-Texturverarbeitungsbibliothek herunterladen</span><span class="sxs-lookup"><span data-stu-id="55c05-649">Get DirectX texture processing library</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=248926"><span data-ttu-id="55c05-650">DirectXTex</span><span class="sxs-lookup"><span data-stu-id="55c05-650">DirectXTex</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-651">DirectXMesh-Geometrieverarbeitungsbibliothek herunterladen</span><span class="sxs-lookup"><span data-stu-id="55c05-651">Get DirectXMesh geometry processing library</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkID=324981"><span data-ttu-id="55c05-652">DirectXMesh</span><span class="sxs-lookup"><span data-stu-id="55c05-652">DirectXMesh</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-653">UVAtlas zum Erstellen und Verpacken des isoChart-Texturatlas herunterladen</span><span class="sxs-lookup"><span data-stu-id="55c05-653">Get UVAtlas for creating and packing isochart texture atlas</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkID=512686"><span data-ttu-id="55c05-654">UVAtlas</span><span class="sxs-lookup"><span data-stu-id="55c05-654">UVAtlas</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-655">DirectXMath-Bibliothek herunterladen</span><span class="sxs-lookup"><span data-stu-id="55c05-655">Get the DirectXMath library</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkID=615560"><span data-ttu-id="55c05-656">DirectXMath</span><span class="sxs-lookup"><span data-stu-id="55c05-656">DirectXMath</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-657">Direct3D12-Unterstützung im DirectXTK (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="55c05-657">Direct3D12 support in the DirectXTK (blog post)</span></span></td>
        <td><a href="https://github.com/Microsoft/DirectXTK/issues/2"><span data-ttu-id="55c05-658">Unterstützung für DirectX12</span><span class="sxs-lookup"><span data-stu-id="55c05-658">Support for DirectX 12</span></span></a></td>
    </tr>
</table>

#### <a name="directx-resources-from-partners"></a><span data-ttu-id="55c05-659">DirectX-Ressourcen von Partnern</span><span class="sxs-lookup"><span data-stu-id="55c05-659">DirectX resources from partners</span></span>

<span data-ttu-id="55c05-660">Dies sind einige zusätzliche DirectX-Dokumentationen, die von externen Partnern erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="55c05-660">These are some additional DirectX documentation created by external partners.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-661">Nvidia: Empfohlene und nicht empfohlene Vorgehensweisen für DX12 (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="55c05-661">Nvidia: DX12 Do's and Don'ts (blog post)</span></span> </td>
        <td><a href="https://developer.nvidia.com/dx12-dos-and-donts-updated"><span data-ttu-id="55c05-662">DirectX12 auf Nvidia-GPUs</span><span class="sxs-lookup"><span data-stu-id="55c05-662">DirectX 12 on Nvidia GPUs</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-663">Intel: Effizientes Rendering mit DirectX12</span><span class="sxs-lookup"><span data-stu-id="55c05-663">Intel: Efficient rendering with DirectX 12</span></span></td>
        <td><a href="https://software.intel.com/sites/default/files/managed/4a/38/Efficient-Rendering-with-DirectX-12-on-Intel-Graphics.pdf"><span data-ttu-id="55c05-664">DirectX12-Rendering auf Intel-Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="55c05-664">DirectX 12 rendering on Intel Graphics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-665">Intel: Mehrfachadapterunterstützung in DirectX12</span><span class="sxs-lookup"><span data-stu-id="55c05-665">Intel: Multi adapter support in DirectX 12</span></span></td>
        <td><a href="https://software.intel.com/articles/multi-adapter-support-in-directx-12"><span data-ttu-id="55c05-666">Implementieren einer expliziten Mehrfachadapteranwendung mit DirectX12</span><span class="sxs-lookup"><span data-stu-id="55c05-666">How to implement an explicit multi-adapter application using DirectX 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-667">Intel: DirectX12-Lernprogramm</span><span class="sxs-lookup"><span data-stu-id="55c05-667">Intel: DirectX 12 tutorial</span></span></td>
        <td><a href="https://software.intel.com/articles/tutorial-migrating-your-apps-to-directx-12-part-1"><span data-ttu-id="55c05-668">Gemeinsames Whitepaper von Intel, Suzhou Snail und Microsoft</span><span class="sxs-lookup"><span data-stu-id="55c05-668">Collaborative white paper by Intel, Suzhou Snail and Microsoft</span></span></a></td>
    </tr>
</table>


## <a name="production"></a><span data-ttu-id="55c05-669">Produktion</span><span class="sxs-lookup"><span data-stu-id="55c05-669">Production</span></span>


<span data-ttu-id="55c05-670">Ihr Studio ist jetzt vollständig eingebunden und beginnt mit dem Produktionszyklus, wobei die Arbeiten auf die einzelnen Teammitglieder aufgeteilt werden.</span><span class="sxs-lookup"><span data-stu-id="55c05-670">Your studio is now fully engaged and moving into the production cycle, with work distributed throughout your team.</span></span> <span data-ttu-id="55c05-671">Der Prototyp wird optimiert, überarbeitet und erweitert, um ein vollständiges Spiel zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="55c05-671">You're polishing, refactoring, and extending the prototype to craft it into a full game.</span></span>

### <a name="notifications-and-live-tiles"></a><span data-ttu-id="55c05-672">Benachrichtigungen und Live-Kacheln</span><span class="sxs-lookup"><span data-stu-id="55c05-672">Notifications and live tiles</span></span>

<span data-ttu-id="55c05-673">Ihr Spiel wird im Menü „Start“ durch eine Kachel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="55c05-673">A tile is your game's representation on the Start Menu.</span></span> <span data-ttu-id="55c05-674">Über Kacheln und Benachrichtigungen können Sie das Interesse von Spielern wecken, auch wenn diese das Spiel gerade gar nicht spielen.</span><span class="sxs-lookup"><span data-stu-id="55c05-674">Tiles and notifications can drive player interest even when they aren't currently playing your game.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-675">Entwickeln von Kacheln und Signalen</span><span class="sxs-lookup"><span data-stu-id="55c05-675">Developing tiles and badges</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt185606"><span data-ttu-id="55c05-676">Kacheln, Badges und Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="55c05-676">Tiles, badges, and notifications</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-677">Beispiel zur Veranschaulichung von Live-Kacheln und Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="55c05-677">Sample illustrating live tiles and notifications</span></span></td>
        <td><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications"><span data-ttu-id="55c05-678">Benachrichtigungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="55c05-678">Notifications sample</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-679">Vorlagen für adaptive Kacheln (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="55c05-679">Adaptive tile templates (blog post)</span></span></td>
        <td><a href="http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/06/30/adaptive-tile-templates-schema-and-documentation.aspx"><span data-ttu-id="55c05-680">Vorlagen für adaptive Kacheln – Schema und Dokumentation</span><span class="sxs-lookup"><span data-stu-id="55c05-680">Adaptive Tile Templates - Schema and Documentation</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-681">Gestalten von Kacheln und Signalen</span><span class="sxs-lookup"><span data-stu-id="55c05-681">Designing tiles and badges</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/hh465403"><span data-ttu-id="55c05-682">Richtlinien für Kacheln und Signale</span><span class="sxs-lookup"><span data-stu-id="55c05-682">Guidelines for tiles and badges</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-683">Windows10-App für die interaktive Entwicklung von Vorlagen für Live-Kacheln</span><span class="sxs-lookup"><span data-stu-id="55c05-683">Windows 10 app for interactively developing live tile templates</span></span></td>
        <td><a href="https://www.microsoft.com/store/apps/9nblggh5xsl1"><span data-ttu-id="55c05-684">Notifications Visualizer</span><span class="sxs-lookup"><span data-stu-id="55c05-684">Notifications Visualizer</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-685">UWP-Erweiterung für die Generierung von Kacheln für Visual Studio</span><span class="sxs-lookup"><span data-stu-id="55c05-685">UWP Tile Generator extension for Visual Studio</span></span></td>
        <td><a href="https://visualstudiogallery.msdn.microsoft.com/09611e90-f3e8-44b7-9c83-18dba8275bb2"><span data-ttu-id="55c05-686">Tool zum Erstellen aller erforderlichen Kacheln über ein einziges Image</span><span class="sxs-lookup"><span data-stu-id="55c05-686">Tool for creating all required tiles using single image</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-687">UWP-Erweiterung für die Generierung von Kacheln für Visual Studio (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="55c05-687">UWP Tile Generator extension for Visual Studio (blog post)</span></span></td>
        <td><a href="https://blogs.windows.com/buildingapps/2016/02/15/uwp-tile-generator-extension-for-visual-studio/"><span data-ttu-id="55c05-688">Tipps zum Verwenden des UWP-Tools für die Generierung von Kacheln</span><span class="sxs-lookup"><span data-stu-id="55c05-688">Tips on using the UWP Tile Generator tool</span></span></a></td>
    </tr>
</table>
 

### <a name="enable-in-app-product-iap-purchases"></a><span data-ttu-id="55c05-689">Unterstützen von In-App-Produktkäufen (IAP-Käufen)</span><span class="sxs-lookup"><span data-stu-id="55c05-689">Enable in-app product (IAP) purchases</span></span>

<span data-ttu-id="55c05-690">Bei einem IAP (In-App-Produkt) handelt es sich um einen zusätzlichen Artikel, den Spieler innerhalb des Spiels erwerben können.</span><span class="sxs-lookup"><span data-stu-id="55c05-690">An IAP (in-app product) is a supplementary item that players can purchase in-game.</span></span> <span data-ttu-id="55c05-691">Beispiele für IAPs sind Add-Ons, Spielelevels, Gegenstände und alles andere, was für die Spieler interessant sein könnte.</span><span class="sxs-lookup"><span data-stu-id="55c05-691">IAPs can be new add-ons, game levels, items, or anything else that your players might enjoy.</span></span> <span data-ttu-id="55c05-692">Bei richtiger Anwendung können IAPs Umsätze generieren und gleichzeitig das Spielerlebnis verbessern.</span><span class="sxs-lookup"><span data-stu-id="55c05-692">Used appropriately, IAPs can provide revenue while improving the game experience.</span></span> <span data-ttu-id="55c05-693">Die IAPs Ihres Spiels werden über das WindowsDevCenter-Dashboard definiert und veröffentlicht. Die Aktivierung von In-App-Käufen erfolgt über den Code Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="55c05-693">You define and publish your game's IAPs through the Windows Dev Center dashboard, and enable in-app purchases in your game's code.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-694">Langlebige In-App-Produkte</span><span class="sxs-lookup"><span data-stu-id="55c05-694">Durable in-app products</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt219684"><span data-ttu-id="55c05-695">Unterstützen von Käufen von In-App-Produkten</span><span class="sxs-lookup"><span data-stu-id="55c05-695">Enable in-app product purchases</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-696">In-App-Verbrauchsprodukte</span><span class="sxs-lookup"><span data-stu-id="55c05-696">Consumable in-app products</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt219683"><span data-ttu-id="55c05-697">Käufe von konsumierbaren In-App-Produkten aktivieren</span><span class="sxs-lookup"><span data-stu-id="55c05-697">Enable consumable in-app product purchases</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-698">Details zu und Einreichung von In-App-Produkten</span><span class="sxs-lookup"><span data-stu-id="55c05-698">In-app product details and submission</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt148551"><span data-ttu-id="55c05-699">IAP-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="55c05-699">IAP submissions</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-700">Überwachen von IAP-Verkauf und Demografie für Ihr Spiel</span><span class="sxs-lookup"><span data-stu-id="55c05-700">Monitor IAP sales and demographics for your game</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt148538"><span data-ttu-id="55c05-701">Bericht zu IAP-Käufen</span><span class="sxs-lookup"><span data-stu-id="55c05-701">IAP acquisitions report</span></span></a></td>
    </tr>
</table>
 

### <a name="debugging-performance-optimization-and-monitoring"></a><span data-ttu-id="55c05-702">Debuggen, Leistungsoptimierung und Überwachung</span><span class="sxs-lookup"><span data-stu-id="55c05-702">Debugging, performance optimization, and monitoring</span></span>

<span data-ttu-id="55c05-703">Zur Optimierung der Leistung, nutzen Sie den Spielmodus in Windows10, um Ihren Spielern ein optimales Erlebnis durch die vollständige Nutzung der Kapazität ihrer aktuellen Hardware zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="55c05-703">To optimize performance, take advantage of Game Mode in Windows 10 to provide your gamers with the best possible gaming experience by fully utilizing the capacity of their current hardware.</span></span>

<span data-ttu-id="55c05-704">Das Windows Performance Toolkit (WPT) besteht aus Leistungsüberwachungstools, die detaillierte Leistungsprofile von Windows-Betriebssystemen und -Anwendungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="55c05-704">The Windows Performance Toolkit (WPT) consists of performance monitoring tools that produce in-depth performance profiles of Windows operating systems and applications.</span></span> <span data-ttu-id="55c05-705">Dies ist besonders hilfreich für die Überwachung der Speicherverwendung und zum Verbessern der Leistung eines Spiels.</span><span class="sxs-lookup"><span data-stu-id="55c05-705">This is especially useful for monitoring memory usage and improving game performance.</span></span> <span data-ttu-id="55c05-706">Das Windows Performance Toolkit ist im SDK für Windows 10 und im Windows ADK enthalten.</span><span class="sxs-lookup"><span data-stu-id="55c05-706">The Windows Performance Toolkit is included in the Windows 10 SDK and Windows ADK.</span></span> <span data-ttu-id="55c05-707">Dieses Toolkit besteht aus zwei unabhängigen Tools: Windows Performance Recorder (WPR) und Windows Performance Analyzer (WPA).</span><span class="sxs-lookup"><span data-stu-id="55c05-707">This toolkit consists of two independent tools: Windows Performance Recorder (WPR) and Windows Performance Analyzer (WPA).</span></span> <span data-ttu-id="55c05-708">ProcDump ist Teil von [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) und ist ein Befehlszeilenprogramm, das die Leistungsspitzen der CPU überwacht und Speicherabbilddateien während der Spielabstürze generiert.</span><span class="sxs-lookup"><span data-stu-id="55c05-708">ProcDump, which is part of [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default), is a command-line utility that monitors CPU spikes and generates dump files during game crashes.</span></span> 

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-709">Leistungstest für Ihren Code</span><span class="sxs-lookup"><span data-stu-id="55c05-709">Performance test your code</span></span></td>
        <td><a href="https://www.visualstudio.com/team-services/cloud-load-testing/"><span data-ttu-id="55c05-710">Cloud-basierte Auslastungstests</span><span class="sxs-lookup"><span data-stu-id="55c05-710">Cloud based load testing</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-711">Erhalten Sie Xbox-Konsolentypen mithilfe der Geräteinformationen für Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-711">Get Xbox console type using Gaming Device Information</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt825235"><span data-ttu-id="55c05-712">Gaming-Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="55c05-712">Gaming Device Information</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-713">Verbessern Sie die Leistung durch einen exklusiven oder prioritären Zugriff auf Hardwareressourcen mithilfe der Spielmodus-APIs</span><span class="sxs-lookup"><span data-stu-id="55c05-713">Improve performance by getting exclusive or priority access to hardware resources using Game Mode APIs</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt808808"><span data-ttu-id="55c05-714">Spielmodus</span><span class="sxs-lookup"><span data-stu-id="55c05-714">Game Mode</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-715">Abrufen von Windows Performance Toolkit (WPT) aus dem Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="55c05-715">Get Windows Performance Toolkit (WPT) from Windows 10 SDK</span></span></td>
        <td><a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk"><span data-ttu-id="55c05-716">Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="55c05-716">Windows 10 SDK</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-717">Abrufen von Windows Performance Toolkit (WPT) aus dem Windows ADK</span><span class="sxs-lookup"><span data-stu-id="55c05-717">Get Windows Performance Toolkit (WPT) from Windows ADK</span></span></td>
        <td><a href="https://msdn.microsoft.com/windows/hardware/dn913721.aspx"><span data-ttu-id="55c05-718">Windows ADK</span><span class="sxs-lookup"><span data-stu-id="55c05-718">Windows ADK</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-719">Problembehandlung bei nicht reagierender Benutzeroberfläche mit Windows Performance Analyzer (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-719">Troubleshoot unresponsible UI using Windows Performance Analyzer (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-156-Critical-Path-Analysis-with-Windows-Performance-Analyzer"><span data-ttu-id="55c05-720">Analyse des kritischen Pfads in WPA</span><span class="sxs-lookup"><span data-stu-id="55c05-720">Critical path analysis with WPA</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-721">Diagnostizieren von Speicherverwendung und Arbeitsspeicherverlusten mit Windows Performance Recorder (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-721">Diagnose memory usage and leaks using Windows Performance Recorder (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-154-Memory-Footprint-and-Leaks"><span data-ttu-id="55c05-722">Speicherbedarf und Arbeitsspeicherverluste</span><span class="sxs-lookup"><span data-stu-id="55c05-722">Memory footprint and leaks</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-723">Abrufen von ProcDump</span><span class="sxs-lookup"><span data-stu-id="55c05-723">Get ProcDump</span></span></td>
        <td><a href="https://technet.microsoft.com/sysinternals/dd996900"><span data-ttu-id="55c05-724">ProcDump</span><span class="sxs-lookup"><span data-stu-id="55c05-724">ProcDump</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-725">Informationen zur Verwendung von ProcDump (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-725">Learn to use ProcDump (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-131-Windows-10-SDK"><span data-ttu-id="55c05-726">Konfigurieren von ProcDump zum Erstellen von Speicherabbilddateien</span><span class="sxs-lookup"><span data-stu-id="55c05-726">Configure ProcDump to create dump files</span></span></a></td>
    </tr>
</table>

### <a name="advanced-directx-techniques-and-concepts"></a><span data-ttu-id="55c05-727">Erweiterte DirectX-Techniken und -Konzepte</span><span class="sxs-lookup"><span data-stu-id="55c05-727">Advanced DirectX techniques and concepts</span></span>

<span data-ttu-id="55c05-728">Einige Aspekte der DirectX-Entwicklung können sich als differenziert und komplex erweisen.</span><span class="sxs-lookup"><span data-stu-id="55c05-728">Some portions of DirectX development can be nuanced and complex.</span></span> <span data-ttu-id="55c05-729">Wenn Sie sich im Rahmen der Produktionsphase mit den Einzelheiten des DirectX-Moduls auseinandersetzen oder komplexe Leistungsprobleme debuggen müssen, können Sie auf die Ressourcen und Informationen in diesem Abschnitt zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="55c05-729">When you get to the point in production where you need to dig down into the details of your DirectX engine, or debug difficult performance problems, the resources and information in this section can help.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-730">PIX für Windows</span><span class="sxs-lookup"><span data-stu-id="55c05-730">PIX on Windows</span></span></td>
        <td><a href="https://blogs.msdn.microsoft.com/pix/2017/01/17/introducing-pix-on-windows-beta/"><span data-ttu-id="55c05-731">Leistungsoptimierungs- und -Debugg-Tools von DirectX12 für Windows</span><span class="sxs-lookup"><span data-stu-id="55c05-731">Performance tuning and debugging tool for DirectX 12 on Windows</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-732">Überprüfungs- und Debugg-Tools für die Entwicklung von D3D12 (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-732">Debugging and validation tools for D3D12 development (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/GDC/GDC-2017/GDC2017-003"><span data-ttu-id="55c05-733">D3D12-Leistung Leistungsoptimierung und-Debuggen mit PIX und GPUValidation</span><span class="sxs-lookup"><span data-stu-id="55c05-733">D3D12 Performance Tuning and Debugging with PIX and GPUValidation</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-734">Grafik- und Leistungsoptimierung (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-734">Optimizing graphics and performance (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Advanced-DirectX12-Graphics-and-Performance"><span data-ttu-id="55c05-735">Erweiterte DirectX12-Grafiken und -Leistung</span><span class="sxs-lookup"><span data-stu-id="55c05-735">Advanced DirectX 12 Graphics and Performance</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-736">Debuggen von DirectX-Grafiken (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-736">DirectX graphics debugging (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools"><span data-ttu-id="55c05-737">Lösen Sie komplexe Grafikprobleme in Ihrem Spiel mithilfe von DirectX-Tools.</span><span class="sxs-lookup"><span data-stu-id="55c05-737">Solve the tough graphics problems with your game using DirectX Tools</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-738">Visual Studio2015-Tools zum Debuggen von DirectX12 (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-738">Visual Studio 2015 tools for debugging DirectX 12 (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Series/ConnectOn-Demand/212"><span data-ttu-id="55c05-739">DirectX-Tools für Windows10 in Visual Studio2015</span><span class="sxs-lookup"><span data-stu-id="55c05-739">DirectX tools for Windows 10 in Visual Studio 2015</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-740">Direct3D12-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="55c05-740">Direct3D 12 programming guide</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn903821"><span data-ttu-id="55c05-741">Direct3D12-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="55c05-741">Direct3D 12 Programming Guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-742">Kombinieren von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="55c05-742">Combining DirectX and XAML</span></span></td>
        <td><a href="directx-and-xaml-interop.md"><span data-ttu-id="55c05-743">Interoperabilität von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="55c05-743">DirectX and XAML interop</span></span></a></td>
    </tr>
</table>

### <a name="high-dynamic-range-hdr-content-development"></a><span data-ttu-id="55c05-744">Entwicklung von HDR (HDR)-Inhalt</span><span class="sxs-lookup"><span data-stu-id="55c05-744">High dynamic range (HDR) content development</span></span>

<span data-ttu-id="55c05-745">Erstellen Sie Spieleinhalt, der die vollständigen Farbfunktionen von HDR verwendet.</span><span class="sxs-lookup"><span data-stu-id="55c05-745">Build game content that uses the full color capabilities of HDR.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-746">Einführung in die Konzepte für HDR und Farbe (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-746">Introduction to HDR and color concepts (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/Build/2017/P4061"><span data-ttu-id="55c05-747">Verbessern von HDR und erweiterte Farbe in DirectX</span><span class="sxs-lookup"><span data-stu-id="55c05-747">Lighting up HDR and advanced color in DirectX</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-748">Erfahren Sie, wie Sie HDR-Inhalt darstellen, und ermitteln Sie, ob die aktuelle Anzeige dies unterstützt</span><span class="sxs-lookup"><span data-stu-id="55c05-748">Learn how to render HDR content and detect whether the current display supports it</span></span></td>
        <td><a href="https://github.com/Microsoft/DirectX-Graphics-Samples/tree/master/Samples/UWP/D3D12HDR"><span data-ttu-id="55c05-749">HDR-Beispiel</span><span class="sxs-lookup"><span data-stu-id="55c05-749">HDR sample</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-750">Erstellen Sie und konfigurieren Sie eine erweiterte Farbe mit DirectX</span><span class="sxs-lookup"><span data-stu-id="55c05-750">Create and configure an advanced color using DirectX</span></span></td>
        <td><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/D2DAdvancedColorImages"><span data-ttu-id="55c05-751">Beispiel der erweiterten Farbe in Direct2D für das Rendering von Bildern</span><span class="sxs-lookup"><span data-stu-id="55c05-751">Direct2D advanced color image rendering sample</span></span></a></td>
    </tr>   
</table>


### <a name="globalization-and-localization"></a><span data-ttu-id="55c05-752">Globalisierung und Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="55c05-752">Globalization and localization</span></span>

<span data-ttu-id="55c05-753">Entwickeln Sie Windows-Spiele für den weltweiten Markt, und erfahren Sie mehr über die internationalen Features, die in die führenden Produkte von Microsoft integriert sind.</span><span class="sxs-lookup"><span data-stu-id="55c05-753">Develop world-ready games for the Windows platform and learn about the international features built into Microsoft’s top products.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-754">Vorbereiten Ihres Spiels für den globalen Markt</span><span class="sxs-lookup"><span data-stu-id="55c05-754">Preparing your game for the global market</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/xaml/mt186453.aspx"><span data-ttu-id="55c05-755">Richtlinien für die Entwicklung für eine weltweite Zielgruppe</span><span class="sxs-lookup"><span data-stu-id="55c05-755">Guidelines when developing for a global audience</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-756">Überwinden sprachlicher, kultureller und technologischer Barrieren</span><span class="sxs-lookup"><span data-stu-id="55c05-756">Bridging languages, cultures, and technology</span></span></td>
        <td><a href="http://www.microsoft.com/Language/Default.aspx"><span data-ttu-id="55c05-757">Onlineressource für Sprachkonventionen und Microsoft-Standardterminologie</span><span class="sxs-lookup"><span data-stu-id="55c05-757">Online resource for language conventions and standard Microsoft terminology</span></span></a></td>
    </tr>
</table>

### <a name="security"></a><span data-ttu-id="55c05-758">Sicherheit</span><span class="sxs-lookup"><span data-stu-id="55c05-758">Security</span></span>

<span data-ttu-id="55c05-759">Erstellen einer Umgebung, in der Spieler spielen und fair konkurrieren.</span><span class="sxs-lookup"><span data-stu-id="55c05-759">Create an environment where your gamers can play and compete fairly.</span></span> <span data-ttu-id="55c05-760">Ein Spiel, das mit TruePlay registriert wird, wird in einem geschützten Prozess ausgeführt, das eine Klasse von häufigen Angriffen verringert.</span><span class="sxs-lookup"><span data-stu-id="55c05-760">A game enrolled in TruePlay runs in a protected process which mitigates a class of common attacks.</span></span> <span data-ttu-id="55c05-761">Das Überwachungssystem der Spiele hilft Ihnen, allgemeine Täuschungsszenarien zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="55c05-761">The game monitoring system also helps to identify common cheating scenarios.</span></span> 

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-762">Tools zur Bekämpfung von Täuschungen innerhalb von PC-Spielen</span><span class="sxs-lookup"><span data-stu-id="55c05-762">Tools to combat cheating within PC games</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt808781"><span data-ttu-id="55c05-763">TruePlay</span><span class="sxs-lookup"><span data-stu-id="55c05-763">TruePlay</span></span></a></td>
    </tr>
</table>

## <a name="submitting-and-publishing-your-game"></a><span data-ttu-id="55c05-764">Übermitteln und Veröffentlichen Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="55c05-764">Submitting and publishing your game</span></span>

<span data-ttu-id="55c05-765">Die folgenden Handbücher und Informationen sorgen für eine möglichst reibungslose Veröffentlichung und Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="55c05-765">The following guides and information help make the publishing and submission process as smooth as possible.</span></span>

### <a name="publishing"></a><span data-ttu-id="55c05-766">Publishing</span><span class="sxs-lookup"><span data-stu-id="55c05-766">Publishing</span></span>

<span data-ttu-id="55c05-767">Spielpakete werden über das neue einheitliche Windows Dev Center-Dashboard veröffentlicht und verwaltet.</span><span class="sxs-lookup"><span data-stu-id="55c05-767">You'll use the new unified Windows Dev Center dashboard to publish and manage your game packages.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-768">App-Veröffentlichung mit Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="55c05-768">Windows Dev Center app publishing</span></span></td>
        <td><a href="https://dev.windows.com/publish"><span data-ttu-id="55c05-769">Veröffentlichen von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-769">Publish Windows apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-770">Erweiterte Veröffentlichung (GDN) über das Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="55c05-770">Windows Dev Center advanced publishing (GDN)</span></span></td>
        <td><a href="https://developer.xboxlive.com/en-us/windows/documentation/Pages/home.aspx"><span data-ttu-id="55c05-771">Handbuch zur erweiterten Veröffentlichung über das Windows Dev Center-Dashboard</span><span class="sxs-lookup"><span data-stu-id="55c05-771">Windows Dev Center Dashboard advanced publishing guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-772">Sie können mit Azure Active Directory (AAD) Ihrem Dev Center-Konto Benutzer hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="55c05-772">Use Azure Active Directory (AAD) to add users to your Dev Center account</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/publish/manage-account-users"><span data-ttu-id="55c05-773">Verwalten von Kontobenutzern</span><span class="sxs-lookup"><span data-stu-id="55c05-773">Manage account users</span></span></a></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="55c05-774">Bewertung des Spiels (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="55c05-774">Rating your game (blog post)</span></span></td>
        <td><a href="https://blogs.windows.com/buildingapps/2016/01/06/now-available-single-age-rating-system-to-simplify-app-submissions/"><span data-ttu-id="55c05-775">Einzelner Workflow zum Zuweisen von Altersfreigaben mit IARC-System</span><span class="sxs-lookup"><span data-stu-id="55c05-775">Single workflow to assign age ratings using IARC system</span></span></a></td>
    </tr>
</table>

#### <a name="packaging-and-uploading"></a><span data-ttu-id="55c05-776">Packen und Hochladen</span><span class="sxs-lookup"><span data-stu-id="55c05-776">Packaging and uploading</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-777">Informationen zur Verwendung der Streaming-Installation und optionale Pakete (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-777">Learn to use streaming install and optional packages (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/Build/2017/B8093"><span data-ttu-id="55c05-778">Nextgen UWP-app-Verteilung: Erstellen erweiterbare, Stream-fähig Componentizedapps</span><span class="sxs-lookup"><span data-stu-id="55c05-778">Nextgen UWP app distribution: Building extensible, stream-able, componentizedapps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-779">Unterteilen und Gruppieren zum Aktivieren von Inhalten für die Streaming-Installation</span><span class="sxs-lookup"><span data-stu-id="55c05-779">Divide and group content to enable streaming install</span></span></td>
        <td><a href="../packaging/streaming-install.md"><span data-ttu-id="55c05-780">UWP-App-Streaming installieren</span><span class="sxs-lookup"><span data-stu-id="55c05-780">UWP App Streaming install</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-781">Optionale Pakete wie DLC-Spielinhalte erstellen</span><span class="sxs-lookup"><span data-stu-id="55c05-781">Create optional packages like DLC game content</span></span></td>
        <td><a href="../packaging/optional-packages.md"><span data-ttu-id="55c05-782">Optionale Pakete und die Erstellung zugehöriger Sets</span><span class="sxs-lookup"><span data-stu-id="55c05-782">Optional packages and related set authoring</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-783">Packen Ihres UWP-Spiels</span><span class="sxs-lookup"><span data-stu-id="55c05-783">Package your UWP game</span></span></td>
        <td><a href="../packaging/index.md"><span data-ttu-id="55c05-784">Verpacken von Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-784">Packaging apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-785">Packen Ihres UWP-DirectX-Spiels</span><span class="sxs-lookup"><span data-stu-id="55c05-785">Package your UWP DirectX game</span></span></td>
        <td><a href="package-your-windows-store-directx-game.md"><span data-ttu-id="55c05-786">Packen Ihres UWP-DirectX-Spiels</span><span class="sxs-lookup"><span data-stu-id="55c05-786">Package your UWP DirectX game</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-787">Packen Ihres Spiels als Drittentwickler (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="55c05-787">Packaging your game as a 3rd party developer (blog post)</span></span></td>
        <td><a href="https://blogs.windows.com/buildingapps/2015/12/15/building-an-app-for-a-3rd-party-how-to-package-their-store-app/"><span data-ttu-id="55c05-788">Erstellen von hochladbaren Paketen ohne Zugriff auf das Store-Konto des Veröffentlichers</span><span class="sxs-lookup"><span data-stu-id="55c05-788">Create uploadable packages without publisher's store account access</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-789">Erstellen von App-Paketen und App-Paketbündeln mit MakeAppx</span><span class="sxs-lookup"><span data-stu-id="55c05-789">Creating app packages and app package bundles using MakeAppx</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool"><span data-ttu-id="55c05-790">Erstellen von Paketen mit dem App-Verpackungsprogramm MakeAppx.exe</span><span class="sxs-lookup"><span data-stu-id="55c05-790">Create packages using app packager tool MakeAppx.exe</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-791">Digitales Signieren Ihrer Dateien mithilfe von SignTool</span><span class="sxs-lookup"><span data-stu-id="55c05-791">Signing your files digitally using SignTool</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/aa387764"><span data-ttu-id="55c05-792">Signieren von Dateien und Überprüfen von Signaturen in Dateien mithilfe von SignTool</span><span class="sxs-lookup"><span data-stu-id="55c05-792">Sign files and verify signatures in files using SignTool</span></span></a></td>
    </tr>    
    <tr>
        <td><span data-ttu-id="55c05-793">Hochladen und Verwalten der Versionen Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="55c05-793">Uploading and versioning your game</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt148542"><span data-ttu-id="55c05-794">Hochladen von App-Paketen</span><span class="sxs-lookup"><span data-stu-id="55c05-794">Upload app packages</span></span></a></td>
    </tr>
</table>


### <a name="policies-and-certification"></a><span data-ttu-id="55c05-795">Richtlinien und Zertifizierung</span><span class="sxs-lookup"><span data-stu-id="55c05-795">Policies and certification</span></span>

<span data-ttu-id="55c05-796">Stellen Sie sicher, dass sich die Veröffentlichung Ihres Spiels nicht aufgrund von Zertifizierungsproblemen verzögert.</span><span class="sxs-lookup"><span data-stu-id="55c05-796">Don't let certification issues delay your game's release.</span></span> <span data-ttu-id="55c05-797">Hier finden Sie Richtlinien und Informationen zu gängigen Zertifizierungsproblemen.</span><span class="sxs-lookup"><span data-stu-id="55c05-797">Here are policies and common certification issues to be aware of.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-798">Vereinbarung für Entwickler von MicrosoftStore-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-798">Microsoft Store App Developer Agreement</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/hh694058"><span data-ttu-id="55c05-799">Vereinbarung für App-Entwickler</span><span class="sxs-lookup"><span data-stu-id="55c05-799">App Developer Agreement</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-800">Richtlinien für die Veröffentlichung von Apps im MicrosoftStore</span><span class="sxs-lookup"><span data-stu-id="55c05-800">Policies for publishing apps in the Microsoft Store</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/dn764944"><span data-ttu-id="55c05-801">Microsoft Store-Richtlinien</span><span class="sxs-lookup"><span data-stu-id="55c05-801">Microsoft Store Policies</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-802">So wird's gemacht: Vermeiden allgemeiner Probleme bei der App-Zertifizierung</span><span class="sxs-lookup"><span data-stu-id="55c05-802">How to avoid some common app certification issues</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/jj657968"><span data-ttu-id="55c05-803">Vermeiden allgemeiner Zertifizierungsfehler</span><span class="sxs-lookup"><span data-stu-id="55c05-803">Avoid common certification failures</span></span></a></td>
    </tr>
</table>
 

### <a name="store-manifest-storemanifestxml"></a><span data-ttu-id="55c05-804">Store-Manifest („StoreManifest.xml“)</span><span class="sxs-lookup"><span data-stu-id="55c05-804">Store manifest (StoreManifest.xml)</span></span>

<span data-ttu-id="55c05-805">Das Store-Manifest („StoreManifest.xml“) ist eine optionale Konfigurationsdatei, die Sie Ihrem App-Paket hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="55c05-805">The store manifest (StoreManifest.xml) is an optional configuration file that can be included in your app package.</span></span> <span data-ttu-id="55c05-806">Das Store-Manifest bietet zusätzliche Features, die über den Umfang der Datei „AppxManifest.xml“ hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="55c05-806">The store manifest provides additional features that are not part of the AppxManifest.xml file.</span></span> <span data-ttu-id="55c05-807">So können Sie mithilfe des Store-Manifests etwa die Installation Ihres Spiels blockieren, wenn ein Zielgerät nicht über die mindestens erforderliche DirectX-Featureebene verfügt oder der verfügbare Systemspeicher nicht ausreicht.</span><span class="sxs-lookup"><span data-stu-id="55c05-807">For example, you can use the store manifest to block installation of your game if a target device doesn't have the specified minimum DirectX feature level, or the specified minimum system memory.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-808">Store-Manifest-Schema</span><span class="sxs-lookup"><span data-stu-id="55c05-808">Store manifest schema</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt617335"><span data-ttu-id="55c05-809">StoreManifest-Schema (Windows10)</span><span class="sxs-lookup"><span data-stu-id="55c05-809">StoreManifest schema (Windows 10)</span></span></a></td>
    </tr>
</table>
 

## <a name="game-lifecycle-management"></a><span data-ttu-id="55c05-810">Spiellebenszyklusverwaltung</span><span class="sxs-lookup"><span data-stu-id="55c05-810">Game lifecycle management</span></span>


<span data-ttu-id="55c05-811">Wer glaubt, sich nach dem Abschluss der Entwicklung und der Auslieferung eines Spiels entspannt zurücklehnen zu können, irrt:</span><span class="sxs-lookup"><span data-stu-id="55c05-811">After you've finished development and shipped your game, it's not "game over".</span></span> <span data-ttu-id="55c05-812">Die Entwicklung von Version1 mag zwar abgeschlossen sein, die Marktphase Ihres Spiels hat jedoch gerade erst begonnen.</span><span class="sxs-lookup"><span data-stu-id="55c05-812">You may be done with development on version one, but your game's journey in the marketplace has only just begun.</span></span> <span data-ttu-id="55c05-813">Sie sollten Verwendung und Fehlerberichte überwachen, auf Benutzerfeedback reagieren und Updates für Ihr Spiel veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="55c05-813">You'll want to monitor usage and error reporting, respond to user feedback, and publish updates to your game.</span></span>

### <a name="windows-dev-center-analytics-and-promotion"></a><span data-ttu-id="55c05-814">Windows Dev Center-Analysen und Werbung</span><span class="sxs-lookup"><span data-stu-id="55c05-814">Windows Dev Center analytics and promotion</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-815">DevCenter-App</span><span class="sxs-lookup"><span data-stu-id="55c05-815">Dev Center App</span></span></td>
        <td><a href="https://www.microsoft.com/store/apps/dev-center/9nblggh4r5ws"><span data-ttu-id="55c05-816">Dev Center-App unter Windows10 zum Anzeigen Ihrer veröffentlichten Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-816">Dev Center Windows 10 app to view performance of your published apps</span></span></a></td>
    </tr>  
    <tr>
        <td><span data-ttu-id="55c05-817">Windows Dev Center-Analysen</span><span class="sxs-lookup"><span data-stu-id="55c05-817">Windows Dev Center analytics</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt148522"><span data-ttu-id="55c05-818">Analysieren der App-Leistung</span><span class="sxs-lookup"><span data-stu-id="55c05-818">Analyze app performance</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-819">Hier erfahren Sie, wie Ihre Kunden mit der Xbox-Features in Ihrem Spiel interagieren</span><span class="sxs-lookup"><span data-stu-id="55c05-819">Learn how your customers are engaging with the Xbox features in your game</span></span></td>
        <td><a href="../publish/xbox-analytics-report.md"><span data-ttu-id="55c05-820">Bericht der Xbox Analyse</span><span class="sxs-lookup"><span data-stu-id="55c05-820">Xbox analytics report</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-821">Reagieren auf Kundenrezensionen</span><span class="sxs-lookup"><span data-stu-id="55c05-821">Responding to customer reviews</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt148546"><span data-ttu-id="55c05-822">Reagieren auf Kundenrezensionen</span><span class="sxs-lookup"><span data-stu-id="55c05-822">Respond to customer reviews</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-823">Werbemöglichkeiten für Ihr Spiel</span><span class="sxs-lookup"><span data-stu-id="55c05-823">Ways to promote your game</span></span></td>
        <td><a href="https://dev.windows.com/store-promotion"><span data-ttu-id="55c05-824">Bewerben Ihrer Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-824">Promote your apps</span></span></a></td>
    </tr>
</table>
 

### <a name="visual-studio-application-insights"></a><span data-ttu-id="55c05-825">Visual Studio Application Insights</span><span class="sxs-lookup"><span data-stu-id="55c05-825">Visual Studio Application Insights</span></span>

<span data-ttu-id="55c05-826">Visual Studio Application Insights bietet Leistungs-, Telemetrie- und Verwendungsanalysen für Ihr veröffentlichtes Spiel.</span><span class="sxs-lookup"><span data-stu-id="55c05-826">Visual Studio Application Insights provides performance, telemetry, and usage analytics for your published game.</span></span> <span data-ttu-id="55c05-827">Application Insights unterstützt Sie nach der Veröffentlichung Ihres Spiels beim Erkennen und Beheben von Problemen sowie bei der kontinuierlichen Überwachung und Optimierung der Verwendung und beim Nachvollziehen der weiteren Spielerinteraktionen mit Ihrem Spiel.</span><span class="sxs-lookup"><span data-stu-id="55c05-827">Application Insights helps you detect and solve issues after your game is released, continuously monitor and improve usage, and understand how players are continuing to interact with your game.</span></span> <span data-ttu-id="55c05-828">Application Insights fügt Ihrer App ein SDK hinzu, das Telemetriedaten an das [Azure-Portal](http://portal.azure.com/) übermittelt.</span><span class="sxs-lookup"><span data-stu-id="55c05-828">Application Insights works by adding an SDK into your app, which sends telemetry to the [Azure portal](http://portal.azure.com/).</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-829">Analyse von Anwendungsleistung und -verwendung</span><span class="sxs-lookup"><span data-stu-id="55c05-829">Application performance and usage analytics</span></span></td>
        <td><a href="https://azure.microsoft.com/documentation/articles/app-insights-get-started/"><span data-ttu-id="55c05-830">Visual Studio Application Insights</span><span class="sxs-lookup"><span data-stu-id="55c05-830">Visual Studio Application Insights</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-831">Aktivieren von Application Insights in Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-831">Enable Application Insights in Windows apps</span></span></td>
        <td><a href="https://azure.microsoft.com/documentation/articles/app-insights-windows-get-started/"><span data-ttu-id="55c05-832">Application Insights für Windows Phone- und Windows Store-Apps</span><span class="sxs-lookup"><span data-stu-id="55c05-832">Application Insights for Windows Phone and Store apps</span></span></a></td>
    </tr>
</table>


### <a name="third-party-solutions-for-analytics-and-promotion"></a><span data-ttu-id="55c05-833">Lösungen von Drittanbietern für Analysen und Werbung</span><span class="sxs-lookup"><span data-stu-id="55c05-833">Third party solutions for analytics and promotion</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-834">Verstehen der Spielerverhalten mit GameAnalytics</span><span class="sxs-lookup"><span data-stu-id="55c05-834">Understand player behavior using GameAnalytics</span></span></td>
        <td><a href="http://www.gameanalytics.com/"><span data-ttu-id="55c05-835">GameAnalytics</span><span class="sxs-lookup"><span data-stu-id="55c05-835">GameAnalytics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-836">Verbinden Sie Ihr UWP-Spiel mit Google Analytics</span><span class="sxs-lookup"><span data-stu-id="55c05-836">Connect your UWP game to Google Analytics</span></span></td>
        <td><a href="https://github.com/dotnet/windows-sdk-for-google-analytics"><span data-ttu-id="55c05-837">Holen Sie sich Windows SDK für Google Analytics</span><span class="sxs-lookup"><span data-stu-id="55c05-837">Get Windows SDK for Google Analytics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-838">Hier erfahren Sie, wie Sie Windows SDK für Google Analytics (Video) verwenden</span><span class="sxs-lookup"><span data-stu-id="55c05-838">Learn how to use Windows SDK for Google Analytics (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Creators-Update/Getting-started-with-the-Windows-SDK-for-Google-Analytics"><span data-ttu-id="55c05-839">Erste Schritte mit Windows SDK für Google Analytics</span><span class="sxs-lookup"><span data-stu-id="55c05-839">Getting started with Windows SDK for Google Analytics</span></span></a></td>
    </tr>    
    <tr>
        <td><span data-ttu-id="55c05-840">Verwenden der Facebook-App zum Installieren von Anzeigen, bietet Werbemöglichkeiten für Ihr Spiel für Facebook-Benutzer an</span><span class="sxs-lookup"><span data-stu-id="55c05-840">Use Facebook App Installs Ads to promote your game to Facebook users</span></span></td>
        <td><a href="https://github.com/Microsoft/winsdkfb"><span data-ttu-id="55c05-841">Holen Sie sich Windows SDK für Facebook</span><span class="sxs-lookup"><span data-stu-id="55c05-841">Get Windows SDK for Facebook</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-842">Hier erfahren Sie, wie Sie die Facebook-App zum Installieren von Anzeigen verwenden (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-842">Learn how to use Facebook App Installs Ads (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Creators-Update/Getting-started-with-Facebook-App-Install-Ads"><span data-ttu-id="55c05-843">Erste Schritte mit Windows SDK für Facebook</span><span class="sxs-lookup"><span data-stu-id="55c05-843">Getting started with Windows SDK for Facebook</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-844">Verwenden von Vungle, um Ihren Spielen Videoanzeigen hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="55c05-844">Use Vungle to add video ads into your games</span></span></td>
        <td><a href="https://v.vungle.com/sdk"><span data-ttu-id="55c05-845">WindowsSDK für Vungle herunterladen</span><span class="sxs-lookup"><span data-stu-id="55c05-845">Get Windows SDK for Vungle</span></span></a></td>
    </tr>
</table>
 

### <a name="creating-and-managing-content-updates"></a><span data-ttu-id="55c05-846">Erstellen und Verwalten von Inhaltsaktualisierungen</span><span class="sxs-lookup"><span data-stu-id="55c05-846">Creating and managing content updates</span></span>

<span data-ttu-id="55c05-847">Zum Aktualisieren Ihres veröffentlichten Spiels übermitteln Sie ein neues App-Paket mit einer höheren Versionsnummer.</span><span class="sxs-lookup"><span data-stu-id="55c05-847">To update your published game, submit a new app package with a higher version number.</span></span> <span data-ttu-id="55c05-848">Nachdem das Paket den Übermittlungs- und Zertifizierungsprozess durchlaufen hat, wird es für die Kunden automatisch als Update verfügbar.</span><span class="sxs-lookup"><span data-stu-id="55c05-848">After the package makes its way through submission and certification, it will automatically be available to customers as an update.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-849">Aktualisieren und Verwalten der Versionen Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="55c05-849">Updating and versioning your game</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt188602"><span data-ttu-id="55c05-850">Paketversionsnummern</span><span class="sxs-lookup"><span data-stu-id="55c05-850">Package version numbering</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-851">Leitfaden für die Spielpaketverwaltung</span><span class="sxs-lookup"><span data-stu-id="55c05-851">Game package management guidance</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt188602"><span data-ttu-id="55c05-852">Leitfaden für die App-Paketverwaltung</span><span class="sxs-lookup"><span data-stu-id="55c05-852">Guidance for app package management</span></span></a></td>
    </tr>
</table>


## <a name="adding-xbox-live-to-your-game"></a><span data-ttu-id="55c05-853">Hinzufügen von Xbox Live zu Ihrem Spiel</span><span class="sxs-lookup"><span data-stu-id="55c05-853">Adding Xbox Live to your game</span></span>

<span data-ttu-id="55c05-854">Xbox Live ist ein erstklassiges Gaming-Netzwerk, das Millionen von Spielern weltweit verbindet.</span><span class="sxs-lookup"><span data-stu-id="55c05-854">Xbox Live is a premier gaming network that connects millions of gamers across the world.</span></span> <span data-ttu-id="55c05-855">Entwickler haben Zugriff auf Xbox Live-Features, die die Spielerzielgruppe steigern, einschließlich Xbox Live, Bestenlisten, Cloudspeicherungen, Spielehubs, Clubs, Party-Chat, Game DVR und mehr.</span><span class="sxs-lookup"><span data-stu-id="55c05-855">Developers gain access to Xbox Live features that can organically grow their game’s audience, including Xbox Live presence, Leaderboards, Cloud Saves, Game Hubs, Clubs, Party Chat, Game DVR, and more.</span></span>

> [!Note]
> <span data-ttu-id="55c05-856">Wenn Sie Xbox Live aktivierte Titel entwickeln möchten, stehen Ihnen verschiedene Optionen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="55c05-856">If you would like to develop Xbox Live enabled titles, there are several options are available to you.</span></span> <span data-ttu-id="55c05-857">Informationen zu den verschiedenen Programmen finden Sie unter [Übersicht über das Entwickler-Programm](../xbox-live/developer-program-overview.md).</span><span class="sxs-lookup"><span data-stu-id="55c05-857">For info about the various programs, see [Developer program overview](../xbox-live/developer-program-overview.md).</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-858">Xbox Live – Übersicht</span><span class="sxs-lookup"><span data-stu-id="55c05-858">Xbox Live overview</span></span></td>
        <td><a href="../xbox-live/index.md"><span data-ttu-id="55c05-859">Xbox Live – Entwicklerhandbuch</span><span class="sxs-lookup"><span data-stu-id="55c05-859">Xbox Live developer guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-860">Verstehen, welche Features je nach Programm verfügbar sind</span><span class="sxs-lookup"><span data-stu-id="55c05-860">Understand which features are available depending on program</span></span></td>
        <td><a href="../xbox-live/developer-program-overview.md#feature-table"><span data-ttu-id="55c05-861">Übersicht über das Entwickler-Programm: Tabelle der Features</span><span class="sxs-lookup"><span data-stu-id="55c05-861">Developer program overview: Feature table</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-862">Links zu nützlichen Ressourcen für die Entwicklung von Xbox Live-Spielen</span><span class="sxs-lookup"><span data-stu-id="55c05-862">Links to useful resources for developing Xbox Live games</span></span></td>
        <td><a href="../xbox-live/xbox-live-resources.md"><span data-ttu-id="55c05-863">Xbox Live-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="55c05-863">Xbox Live resources</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-864">Erfahren Sie, wie Sie Informationen über Xbox Live-Dienste abrufen</span><span class="sxs-lookup"><span data-stu-id="55c05-864">Learn how to get info from Xbox Live services</span></span></td>
        <td><a href="../xbox-live/introduction-to-xbox-live-apis.md"><span data-ttu-id="55c05-865">Einführung in Xbox Live APIs</span><span class="sxs-lookup"><span data-stu-id="55c05-865">Introduction to Xbox Live APIs</span></span></a></td>
    </tr>
</table>


### <a name="for-developers-in-the-xbox-live-creators-program"></a><span data-ttu-id="55c05-866">Für Entwickler im Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="55c05-866">For developers in the Xbox Live Creators Program</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-867">Übersicht</span><span class="sxs-lookup"><span data-stu-id="55c05-867">Overview</span></span></td>
        <td><a href="../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md"><span data-ttu-id="55c05-868">Erste Schritte – Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="55c05-868">Get started with the Xbox Live Creators Program</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-869">Hinzufügen von Xbox Live zu Ihrem Spiel</span><span class="sxs-lookup"><span data-stu-id="55c05-869">Add Xbox Live to your game</span></span></td>
        <td><a href="../xbox-live/get-started-with-creators/creators-step-by-step-guide.md"><span data-ttu-id="55c05-870">Schrittweise Anleitung zur Integration mit dem Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="55c05-870">Step by step guide to integrate Xbox Live Creators Program</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-871">Hinzufügen von Xbox Live zu Ihrem UWP-Spiel, das mit Unity erstellt wurde</span><span class="sxs-lookup"><span data-stu-id="55c05-871">Add Xbox Live to your UWP game created using Unity</span></span></td>
        <td><a href="../xbox-live/get-started-with-creators/develop-creators-title-with-unity.md"><span data-ttu-id="55c05-872">Erste Schritte bei der Entwicklung eines Titels im Xbox Live Creators-Programm mit der Unity-Spielengine</span><span class="sxs-lookup"><span data-stu-id="55c05-872">Get started developing an Xbox Live Creators Program title with the Unity game engine</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-873">Einrichten der Entwicklungs-Sandbox</span><span class="sxs-lookup"><span data-stu-id="55c05-873">Set up your development sandbox</span></span></td>
        <td><a href="../xbox-live/get-started-with-creators/xbox-live-sandboxes-creators.md"><span data-ttu-id="55c05-874">Einführung in die Xbox Live-Sandbox</span><span class="sxs-lookup"><span data-stu-id="55c05-874">Xbox Live sandboxes introduction</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-875">Einrichten von Konten zum Testen</span><span class="sxs-lookup"><span data-stu-id="55c05-875">Set up accounts for testing</span></span></td>
        <td><a href="../xbox-live/get-started-with-creators/authorize-xbox-live-accounts.md"><span data-ttu-id="55c05-876">Xbox Live-Konten in Ihrer Testumgebung autorisieren</span><span class="sxs-lookup"><span data-stu-id="55c05-876">Authorize Xbox Live accounts in your test environment</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-877">Beispiele für das Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="55c05-877">Samples for Xbox Live Creators Program</span></span></td>
        <td><a href="https://github.com/Microsoft/xbox-live-samples/tree/master/Samples/CreatorsSDK"><span data-ttu-id="55c05-878">Codebeispiele für Creators Programm-Entwickler</span><span class="sxs-lookup"><span data-stu-id="55c05-878">Code samples for Creators Program developers</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-879">Enthält Informationen zum Integrieren von plattformübergreifenden Xbox Live-Umgebungen in UWP-Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-879">Learn how to integrate cross-platform Xbox Live experiences in UWP games (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/GDC/GDC-2017/GDC2017-005"><span data-ttu-id="55c05-880">Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="55c05-880">Xbox Live Creators Program</span></span></a></td>
    </tr>  
</table>

### <a name="for-managed-partners-and-developers-in-the-idxbox-program"></a><span data-ttu-id="55c05-881">Für verwaltete Partner und Entwickler im ID@Xbox-Programm</span><span class="sxs-lookup"><span data-stu-id="55c05-881">For managed partners and developers in the ID@Xbox program</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-882">Übersicht</span><span class="sxs-lookup"><span data-stu-id="55c05-882">Overview</span></span></td>
        <td><a href="../xbox-live/get-started-with-partner/get-started-with-xbox-live-partner.md"><span data-ttu-id="55c05-883">Erste Schritte mit Xbox Live als verwalteter Partner oder ID-Entwickler</span><span class="sxs-lookup"><span data-stu-id="55c05-883">Get started with Xbox Live as a managed partner or an ID developer</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-884">Hinzufügen von Xbox Live zu Ihrem Spiel</span><span class="sxs-lookup"><span data-stu-id="55c05-884">Add Xbox Live to your game</span></span></td>
        <td><a href="../xbox-live/get-started-with-partner/partners-step-by-step-guide.md"><span data-ttu-id="55c05-885">Schrittweise Anleitung zum Integrieren von Xbox Live für verwaltete Partner und ID Mitglieder</span><span class="sxs-lookup"><span data-stu-id="55c05-885">Step by step guide to integrate Xbox Live for managed partners and ID members</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-886">Hinzufügen von Xbox Live zu Ihrem UWP-Spiel, das mit Unity erstellt wurde</span><span class="sxs-lookup"><span data-stu-id="55c05-886">Add Xbox Live to your UWP game created using Unity</span></span></td>
        <td><a href="../xbox-live/get-started-with-partner/partner-unity-uwp-il2cpp.md"><span data-ttu-id="55c05-887">Hinzufügen von Xbox Live-Unterstützung zu Unity für UWP mit IL2CPP Scripting-Back-End für ID- und verwaltete Partner</span><span class="sxs-lookup"><span data-stu-id="55c05-887">Add Xbox Live support to Unity for UWP with IL2CPP scripting backend for ID and managed partners</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-888">Einrichten der Entwicklungs-Sandbox</span><span class="sxs-lookup"><span data-stu-id="55c05-888">Set up your development sandbox</span></span></td>
        <td><a href="../xbox-live/get-started-with-partner/advanced-xbox-live-sandboxes.md"><span data-ttu-id="55c05-889">Erweiterte Xbox Live-Sandbox</span><span class="sxs-lookup"><span data-stu-id="55c05-889">Advanced Xbox Live sandboxes</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-890">Anforderungen für Spiele mit Xbox Live (GDN)</span><span class="sxs-lookup"><span data-stu-id="55c05-890">Requirements for games that use Xbox Live (GDN)</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=533217"><span data-ttu-id="55c05-891">Xbox-Anforderungen für Xbox Live unter Windows 10</span><span class="sxs-lookup"><span data-stu-id="55c05-891">Xbox Requirements for Xbox Live on Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-892">Beispiele</span><span class="sxs-lookup"><span data-stu-id="55c05-892">Samples</span></span></td>
        <td><a href="https://github.com/Microsoft/xbox-live-samples/tree/master/Samples/ID%40XboxSDK"><span data-ttu-id="55c05-893">Codebeispiele für ID@Xbox-Entwickler</span><span class="sxs-lookup"><span data-stu-id="55c05-893">Code samples for ID@Xbox developers</span></span></a></td>
    </tr>  
    <tr>
        <td><span data-ttu-id="55c05-894">Übersicht über die Entwicklung von Spielen mit Xbox Live (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-894">Overview of Xbox Live game development (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Developing-with-Xbox-Live-for-Windows-10"><span data-ttu-id="55c05-895">Entwickeln mit Xbox Live für Windows10</span><span class="sxs-lookup"><span data-stu-id="55c05-895">Developing with Xbox Live for Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-896">Plattformübergreifende Spielersuche (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-896">Cross-platform matchmaking (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Xbox-Live-Multiplayer-Introducing-services-for-cross-platform-matchmaking-and-gameplay"><span data-ttu-id="55c05-897">Xbox Live Multiplayer: Einführung in die Dienste für plattformübergreifende Spielersuche und Spiele</span><span class="sxs-lookup"><span data-stu-id="55c05-897">Xbox Live Multiplayer: Introducing services for cross-platform matchmaking and gameplay</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-898">Geräteübergreifendes Spielen in Fable Legends (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-898">Cross-device gameplay in Fable Legends (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Fable-Legends-Cross-device-Gameplay-with-Xbox-Live"><span data-ttu-id="55c05-899">Fable Legends: Geräteübergreifendes Spielen mit Xbox Live</span><span class="sxs-lookup"><span data-stu-id="55c05-899">Fable Legends: Cross-device Gameplay with Xbox Live</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-900">Xbox Live und Erfolge (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-900">Xbox Live stats and achievements (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Best-Practices-for-Leveraging-Cloud-Based-User-Stats-and-Achievements-in-Xbox-Live"><span data-ttu-id="55c05-901">Bewährte Methoden für die Nutzung von cloudbasierten Benutzerstatistiken und Erfolgen in Xbox Live</span><span class="sxs-lookup"><span data-stu-id="55c05-901">Best Practices for Leveraging Cloud-Based User Stats and Achievements in Xbox Live</span></span></a></td>
    </tr>
</table>


## <a name="additional-resources"></a><span data-ttu-id="55c05-902">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="55c05-902">Additional resources</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55c05-903">Entwicklung von Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-903">Game development videos</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/gaming/game-development-videos"><span data-ttu-id="55c05-904">Videos von wichtigen Konferenzen wie GDC und //Build</span><span class="sxs-lookup"><span data-stu-id="55c05-904">Videos from major conferences like GDC and //build</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-905">Entwicklung von Indie-Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-905">Indie game development (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/New-Opportunities-for-Independent-Developers"><span data-ttu-id="55c05-906">Neue Möglichkeiten für unabhängige Entwickler</span><span class="sxs-lookup"><span data-stu-id="55c05-906">New Opportunities for Independent Developers</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-907">Überlegungen für mobile Multi-Core-Geräte (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-907">Considerations for multi-core mobile devices (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Sustained-gaming-performance-in-multi-core-mobile-devices"><span data-ttu-id="55c05-908">Kontinuierlich hohe Spieleleistung auf mobilen Multi-Core-Geräten</span><span class="sxs-lookup"><span data-stu-id="55c05-908">Sustained Gaming Performance in multi-core mobile devices</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="55c05-909">Entwickeln von Windows10-Desktopspielen (Video)</span><span class="sxs-lookup"><span data-stu-id="55c05-909">Developing Windows 10 desktop games (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/PC-Games-for-Windows-10"><span data-ttu-id="55c05-910">PC-Spiele für Windows10</span><span class="sxs-lookup"><span data-stu-id="55c05-910">PC Games for Windows 10</span></span></a></td>
    </tr>
</table>



 

 

 
