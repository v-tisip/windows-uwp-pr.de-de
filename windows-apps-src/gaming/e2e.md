---
title: Handbuch zur Entwicklung von Spielen unter Windows10
description: Ein umfassender Leitfaden mit Ressourcen und Informationen zur Entwicklung von Spielen für die universelle Windows-Plattform (UWP).
ms.assetid: 6061F498-96A8-44EF-9711-68AE5A1218C9
ms.date: 04/16/2018
ms.topic: article
keywords: Windows10, Uwp, Spiele, Entwickeln von Spielen
ms.localizationpriority: medium
ms.openlocfilehash: 58044fba24450c397ee58b1034429f2af8d23ed6
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8780558"
---
# <a name="windows-10-game-development-guide"></a><span data-ttu-id="dbf99-104">Handbuch zur Entwicklung von Spielen unter Windows10</span><span class="sxs-lookup"><span data-stu-id="dbf99-104">Windows 10 game development guide</span></span>


<span data-ttu-id="dbf99-105">Willkommen beim Windows10-Handbuch für die Entwicklung von Spielen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-105">Welcome to the Windows 10 game development guide!</span></span>

<span data-ttu-id="dbf99-106">Dieses Handbuch enthält eine umfassende Sammlung von Ressourcen und Informationen, die Sie für die Entwicklung von Spielen für die Universelle Windows-Plattform (UWP) benötigen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-106">This guide provides an end-to-end collection of the resources and information you'll need to develop a Universal Windows Platform (UWP) game.</span></span> <span data-ttu-id="dbf99-107">Eine englische Version (USA) dieses Handbuchs steht im [PDF](http://download.microsoft.com/download/9/C/9/9C9D344F-611F-412E-BB01-259E5C76B17F/Windev_Game_Dev_Guide_Oct_2017.pdf)-Format zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-107">An English (US) version of this guide is available in [PDF](http://download.microsoft.com/download/9/C/9/9C9D344F-611F-412E-BB01-259E5C76B17F/Windev_Game_Dev_Guide_Oct_2017.pdf) format.</span></span>

## <a name="introduction-to-game-development-for-the-universal-windows-platform-uwp"></a><span data-ttu-id="dbf99-108">Einführung in die Spieleentwicklung für die universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="dbf99-108">Introduction to game development for the Universal Windows Platform (UWP)</span></span>


<span data-ttu-id="dbf99-109">Mit einem Windows10-Spiel können Sie Millionen Smartphone-, PC- und XboxOne-Benutzer auf der ganzen Welt erreichen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-109">When you create a Windows 10 game, you have the opportunity to reach millions of players worldwide across phone, PC, and Xbox One.</span></span> <span data-ttu-id="dbf99-110">Dank Xbox auf Windows, Xbox Live, geräteübergreifendem Multiplayer, einer tollen Spiele-Community und leistungsstarken neuen Features wie die Universelle Windows-Plattform (UWP) und DirectX12 begeistern Windows10-Spiele Spieler aller Altersklassen und Genres.</span><span class="sxs-lookup"><span data-stu-id="dbf99-110">With Xbox on Windows, Xbox Live, cross-device multiplayer, an amazing gaming community, and powerful new features like the Universal Windows Platform (UWP) and DirectX 12, Windows 10 games thrill players of all ages and genres.</span></span> <span data-ttu-id="dbf99-111">Die neue universelle Windows-Plattform (UWP) gewährleistet durch eine gemeinsame API für Smartphone, PC und Xbox One die geräteübergreifende Kompatibilität Ihres Spiels unter Windows10 und stellt zudem Tools und Optionen bereit, mit denen Sie Ihr Spiel optimal an die jeweilige Geräteumgebung anpassen können.</span><span class="sxs-lookup"><span data-stu-id="dbf99-111">The new Universal Windows Platform (UWP) delivers compatibility for your game across Windows 10 devices with a common API for phone, PC, and Xbox One, along with tools and options to tailor your game to each device experience.</span></span>

<span data-ttu-id="dbf99-112">Dieses Handbuch enthält eine umfassende Sammlung von hilfreichen Informationen und Ressourcen für die Spieleentwicklung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-112">This guide provides an end-to-end collection of information and resources that will help you as you develop your game.</span></span> <span data-ttu-id="dbf99-113">Die Abschnittsstruktur orientiert sich an den Entwicklungsphasen und vereinfacht die Informationssuche.</span><span class="sxs-lookup"><span data-stu-id="dbf99-113">The sections are organized according to the stages of game development, so you'll know where to look for information when you need it.</span></span>

<span data-ttu-id="dbf99-114">Wenn Sie das Entwickeln von Spielen für Windows oder Xbox noch nicht kennen, sollten Sie möglicherweise mit dem Handbuch [Erste Schritte](getting-started.md) beginnen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-114">If you're new to developing games on Windows or Xbox, the [Getting Started](getting-started.md) guide may be where you want to start off.</span></span> <span data-ttu-id="dbf99-115">Der Einführungsabschnitt [Ressourcen für die Spieleentwicklung](#game-development-resources) bietet ebenfalls einen allgemeinen Überblick über die Dokumentation, Programme und andere hilfreiche Ressourcen für die Spieleerstellung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-115">The [Game development resources](#game-development-resources) section also provides a high-level survey of documentation, programs, and other resources that are helpful when creating a game.</span></span> <span data-ttu-id="dbf99-116">Wenn Sie mit dem Einblick auf UWP-Code beginnen möchten, lesen Sie [Spielbeispiele](#game-samples).</span><span class="sxs-lookup"><span data-stu-id="dbf99-116">If you want to start by looking at some UWP code instead, see [Game samples](#game-samples).</span></span>

<span data-ttu-id="dbf99-117">Dieses Handbuch wird bei Bedarf mit weiteren Ressourcen für die Entwicklung von Windows10-Spielen aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="dbf99-117">This guide will be updated as additional Windows 10 game development resources and material become available.</span></span>

## <a name="game-development-resources"></a><span data-ttu-id="dbf99-118">Ressourcen für die Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="dbf99-118">Game development resources</span></span>

<span data-ttu-id="dbf99-119">Von der Dokumentation bis hin zu Entwicklerprogrammen, Foren, Blogs und Beispielen steht Ihnen bei der Spieleentwicklung eine Vielzahl hilfreicher Ressourcen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-119">From documentation to developer programs, forums, blogs, and samples, there are many resources available to help you on your game development journey.</span></span> <span data-ttu-id="dbf99-120">Hier finden Sie eine Zusammenfassung wichtiger Ressourcen für den Einstieg in die Entwicklung Ihres Windows 10-Spiels.</span><span class="sxs-lookup"><span data-stu-id="dbf99-120">Here's a roundup of resources to know about as you begin developing your Windows 10 game.</span></span>

> [!Note]
> <span data-ttu-id="dbf99-121">Einige Features werden über verschiedene Programme verwaltet.</span><span class="sxs-lookup"><span data-stu-id="dbf99-121">Some features are managed through various programs.</span></span> <span data-ttu-id="dbf99-122">Dieses Handbuch behandelt eine breite Palette von Ressourcen. Je nach Programmteilnahme oder spezifischer Entwicklungsrolle stehen Ihnen bestimmte Ressourcen unter Umständen nicht zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-122">This guide covers a broad range of resources, so you may find that some resources are inaccessible depending on the program you are in or your specific development role.</span></span> <span data-ttu-id="dbf99-123">Beispiele wären etwa Links, die zu „developer.xboxlive.com“, „forums.xboxlive.com“, „xdi.xboxlive.com“ oder zum Netzwerk für Spieleentwickler (Game Developer Network, GDN) aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="dbf99-123">Examples are links that resolve to developer.xboxlive.com, forums.xboxlive.com, xdi.xboxlive.com, or the Game Developer Network (GDN).</span></span> <span data-ttu-id="dbf99-124">Informationen zur Partnerschaft mit Microsoft finden Sie unter [Entwicklerprogramme](#developer-programs).</span><span class="sxs-lookup"><span data-stu-id="dbf99-124">For information about partnering with Microsoft, see [Developer Programs](#developer-programs).</span></span>


### <a name="game-development-documentation"></a><span data-ttu-id="dbf99-125">Dokumentation für die Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="dbf99-125">Game development documentation</span></span>

<span data-ttu-id="dbf99-126">In diesem Handbuch finden Sie immer wieder direkte Links zu relevanten Dokumentationen – strukturiert nach Aufgabe, Technologie und Entwicklungsphase.</span><span class="sxs-lookup"><span data-stu-id="dbf99-126">Throughout this guide, you'll find deep links to relevant documentation—organized by task, technology, and stage of game development.</span></span> <span data-ttu-id="dbf99-127">Hier sehen Sie eine Übersicht über die wichtigsten verfügbaren Dokumentationsportale für die Entwicklung von Windows10-Spielen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-127">To give you a broad view of what's available, here are the main documentation portals for Windows 10 game development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-128">Hauptportal für Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="dbf99-128">Windows Dev Center main portal</span></span></td>
        <td><a href="https://dev.windows.com"><span data-ttu-id="dbf99-129">Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="dbf99-129">Windows Dev Center</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-130">Entwickeln von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-130">Developing Windows apps</span></span></td>
        <td><a href="https://dev.windows.com/develop"><span data-ttu-id="dbf99-131">Entwickeln von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-131">Develop Windows apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-132">Entwicklung von UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="dbf99-132">Universal Windows Platform app development</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt244352"><span data-ttu-id="dbf99-133">Anleitungen für Windows 10-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-133">How-to guides for Windows 10 apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-134">Anleitungen für UWP-Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-134">How-to guides for UWP games</span></span></td>
        <td><a href="index.md"><span data-ttu-id="dbf99-135">Spiele und DirectX</span><span class="sxs-lookup"><span data-stu-id="dbf99-135">Games and DirectX</span></span></a> </td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-136">DirectX-Referenz und -Übersichten</span><span class="sxs-lookup"><span data-stu-id="dbf99-136">DirectX reference and overviews</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/ee663274"><span data-ttu-id="dbf99-137">DirectX-Grafiken und -Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-137">DirectX Graphics and Gaming</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-138">Azure für Gaming</span><span class="sxs-lookup"><span data-stu-id="dbf99-138">Azure for gaming</span></span></td>
        <td><a href="https://azure.microsoft.com/solutions/gaming/"><span data-ttu-id="dbf99-139">Erstellen und Skalieren von Spielen mit Azure</span><span class="sxs-lookup"><span data-stu-id="dbf99-139">Build and scale your games using Azure</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-140">PlayFab</span><span class="sxs-lookup"><span data-stu-id="dbf99-140">PlayFab</span></span></td>
        <td><a href="https://api.playfab.com/"><span data-ttu-id="dbf99-141">Vollständige Back-End-Lösung für Live-Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-141">Complete backend solution for live games</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-142">UWP auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="dbf99-142">UWP on Xbox One</span></span></td>
        <td><a href="https://msdn.microsoft.com/windows/uwp/xbox-apps/index"><span data-ttu-id="dbf99-143">Erstellen von UWP-Apps auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="dbf99-143">Building UWP apps on Xbox One</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-144">UWP auf HoloLens</span><span class="sxs-lookup"><span data-stu-id="dbf99-144">UWP on HoloLens</span></span></td>
        <td><a href="https://developer.microsoft.com/windows/mixed-reality/development_overview"><span data-ttu-id="dbf99-145">Erstellen von UWP-Apps auf HoloLens</span><span class="sxs-lookup"><span data-stu-id="dbf99-145">Building UWP apps on HoloLens</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-146">Xbox Live-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="dbf99-146">Xbox Live documentation</span></span></td>
        <td><a href="../xbox-live/index.md"><span data-ttu-id="dbf99-147">Xbox Live – Entwicklerhandbuch</span><span class="sxs-lookup"><span data-stu-id="dbf99-147">Xbox Live developer guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-148">Xbox One – Entwicklerdokumentation (XGD)</span><span class="sxs-lookup"><span data-stu-id="dbf99-148">Xbox One development documentation (XGD)</span></span></td>
        <td><a href="https://developer.microsoft.com/games/xbox/partner/development-home"><span data-ttu-id="dbf99-149">Xbox One – Entwicklung</span><span class="sxs-lookup"><span data-stu-id="dbf99-149">Xbox One Development</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-150">Xbox One – Whitepapers für Entwickler (XGD)</span><span class="sxs-lookup"><span data-stu-id="dbf99-150">Xbox One development whitepapers (XGD)</span></span></td>
        <td><a href="https://developer.microsoft.com/games/xbox/partner/development-education-whitepapers"><span data-ttu-id="dbf99-151">Whitepapers</span><span class="sxs-lookup"><span data-stu-id="dbf99-151">White Papers</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-152">Interaktive Mixer-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="dbf99-152">Mixer Interactive documentation</span></span></td>
        <td><a href="https://dev.mixer.com/reference/interactive/index.html"><span data-ttu-id="dbf99-153">Fügen Sie Interaktivität zu Ihrem Spiel hinzu</span><span class="sxs-lookup"><span data-stu-id="dbf99-153">Add interactivity to your game</span></span></a></td>
    </tr>        
</table>

### <a name="partner-center"></a><span data-ttu-id="dbf99-154">Partner Center</span><span class="sxs-lookup"><span data-stu-id="dbf99-154">Partner Center</span></span>

<span data-ttu-id="dbf99-155">[Registrieren Sie ein Entwicklerkonto im Partner Center](https://developer.microsoft.com/store/register) ist der erste Schritt beim Veröffentlichen Ihres Spiels Windows.</span><span class="sxs-lookup"><span data-stu-id="dbf99-155">[Registering a developer account in Partner Center](https://developer.microsoft.com/store/register) is the first step towards publishing your Windows game.</span></span> <span data-ttu-id="dbf99-156">Mit einem Entwicklerkonto können Sie den Namen Ihres Spiels reservieren und kostenlose oder kostenpflichtige Spiele für alle Windows-Geräte an den Microsoft Store übermitteln.</span><span class="sxs-lookup"><span data-stu-id="dbf99-156">A developer account lets you reserve your game's name and submit free or paid games to the Microsoft Store for all Windows devices.</span></span> <span data-ttu-id="dbf99-157">Sie können Ihr Spiel und Ihre spielinternen Produkte verwalten, ausführliche Analysen abrufen und Dienste aktivieren, die Spieler auf der ganzen Welt begeistern.</span><span class="sxs-lookup"><span data-stu-id="dbf99-157">Use your developer account to manage your game and in-game products, get detailed analytics, and enable services that create great experiences for your players around the world.</span></span> 

<span data-ttu-id="dbf99-158">Microsoft bietet ebenfalls mehrere Entwicklerprogramme an, die Sie bei der Entwicklung und Veröffentlichung von Windows-Spielen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-158">Microsoft also offers several developer programs to help you develop and publish Windows games.</span></span> <span data-ttu-id="dbf99-159">Wir empfehlen angezeigt wird, wenn diese vor dem Registrieren für ein Partner Center-Konto für Sie geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="dbf99-159">We recommend seeing if any are right for you before registering for a Partner Center account.</span></span> <span data-ttu-id="dbf99-160">Weitere Informationen finden Sie unter [Entwicklerprogramme](#developer-programs)</span><span class="sxs-lookup"><span data-stu-id="dbf99-160">For more info, go to [Developer programs](#developer-programs)</span></span>


### <a name="developer-programs"></a><span data-ttu-id="dbf99-161">Entwicklerprogramme</span><span class="sxs-lookup"><span data-stu-id="dbf99-161">Developer programs</span></span>

<span data-ttu-id="dbf99-162">Microsoft bietet mehrere Entwicklerprogramme an, die Sie bei der Entwicklung und Veröffentlichung von Windows-Spielen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-162">Microsoft offers several developer programs to help you develop and publish Windows games.</span></span> <span data-ttu-id="dbf99-163">Erwägen Sie, an einem Entwicklerprogramm teilzunehmen, wenn Sie Spiele für Xbox One entwickeln möchten und Xbox Live-Features in Ihrem Spiel integrieren möchten.</span><span class="sxs-lookup"><span data-stu-id="dbf99-163">Consider joining a developer program if you want to develop games for Xbox One and integrate Xbox Live features in your game.</span></span> <span data-ttu-id="dbf99-164">Wenn ein Spiel im Microsoft Store veröffentlichen möchten, müssen Sie auch ein Entwicklerkonto im [Partner Center](https://partner.microsoft.com/dashboard) erstellen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-164">To publish a game in the Microsoft Store, you'll also need to create a developer account in [Partner Center](https://partner.microsoft.com/dashboard) .</span></span>

#### <a name="xbox-live-creators-program"></a><span data-ttu-id="dbf99-165">Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="dbf99-165">Xbox Live Creators Program</span></span>

<span data-ttu-id="dbf99-166">Mit dem Xbox Live Creators-Programm kann jeder Xbox Live in seine Titel integrieren und sie auf Xbox One und Windows 10 veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-166">The Xbox Live Creators Program allows anyone to integrate Xbox Live into their title and publish to Xbox One and Windows 10.</span></span> <span data-ttu-id="dbf99-167">Wir haben einen vereinfachten Zertifizierungsprozess ohne Konzeptgenehmigung außerhalb der standardmäßigen [Microsoft Store-Richtlinien](https://msdn.microsoft.com/library/windows/apps/dn764944.aspx).</span><span class="sxs-lookup"><span data-stu-id="dbf99-167">There is a simplified certification process and no concept approval is required outside of the standard [Microsoft Store Policies](https://msdn.microsoft.com/library/windows/apps/dn764944.aspx).</span></span>

<span data-ttu-id="dbf99-168">Sie können Ihr Spiel im Creators-Programm ohne einen dedizierten Entwicklerkit bereitstellen, entwerfen und veröffentlichen, indem Sie nur Einzelhandels-Hardware verwenden.</span><span class="sxs-lookup"><span data-stu-id="dbf99-168">You can deploy, design, and publish your game in the Creators Program without a dedicated dev kit, using only retail hardware.</span></span> <span data-ttu-id="dbf99-169">Laden Sie zunächst die [DEVMODE-Aktivierungs-App](https://docs.microsoft.com/windows/uwp/xbox-apps/devkit-activation) auf Ihre Xbox One.</span><span class="sxs-lookup"><span data-stu-id="dbf99-169">To get started, download the [Dev Mode Activation app](https://docs.microsoft.com/windows/uwp/xbox-apps/devkit-activation) on your Xbox One.</span></span>

<span data-ttu-id="dbf99-170">Treten Sie dem [ID@Xbox](http://www.xbox.com/Developers/id) bei, wenn Sie Zugriff auf weitere Xbox Live-Funktionen wünschen, dedizierte Marketing- und Entwicklungsunterstützung benötigen oder im allgemeinen Xbox One-Store vertreten sein möchten.</span><span class="sxs-lookup"><span data-stu-id="dbf99-170">If you want access to even more Xbox Live capabilities, dedicated marketing and development support, and the chance to be featured in the main Xbox One store, apply to the [ID@Xbox](http://www.xbox.com/Developers/id) program.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-171">Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="dbf99-171">Xbox Live Creators Program</span></span></td>
        <td><a href="https://developer.microsoft.com/games/xbox/xboxlive/creator"><span data-ttu-id="dbf99-172">Erfahren Sie mehr über das Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="dbf99-172">Learn more about the Xbox Live Creators Program</span></span></a></td>
    </tr>
</table>

#### <a name="idxbox"></a>ID@Xbox

<span data-ttu-id="dbf99-173">Das ID@Xbox-Programm unterstützt qualifizierte Spieleentwickler bei der eigenständigen Veröffentlichung für Windows und Xbox One.</span><span class="sxs-lookup"><span data-stu-id="dbf99-173">The ID@Xbox program helps qualified game developers self-publish on Windows and Xbox One.</span></span> <span data-ttu-id="dbf99-174">Wenn Sie für Xbox One entwickeln oder Ihr Windows10-Spiel mit XboxLive-Features wie Gamerscore, Erfolgen und Ranglisten versehen möchten, registrieren Sie sich bei ID@Xbox.</span><span class="sxs-lookup"><span data-stu-id="dbf99-174">If you want to develop for Xbox One, or add Xbox Live features like Gamerscore, achievements, and leaderboards to your Windows 10 game, sign up with ID@Xbox.</span></span> <span data-ttu-id="dbf99-175">Als ID@Xbox-Entwickler erhalten Sie Zugriff auf Tools und Supportleistungen, mit denen Sie Ihrer Kreativität freien Lauf lassen und Ihren Erfolg maximieren können.</span><span class="sxs-lookup"><span data-stu-id="dbf99-175">Become an ID@Xbox developer to get the tools and support you need to unleash your creativity and maximize your success.</span></span> <span data-ttu-id="dbf99-176">Es wird empfohlen, dass Sie auf Anwenden ID@Xbox vor dem Registrieren für ein Entwicklerkonto im Partner Center.</span><span class="sxs-lookup"><span data-stu-id="dbf99-176">We recommend that you apply to ID@Xbox first before registering for a developer account in Partner Center.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-177">ID@Xbox Entwicklerprogramm</span><span class="sxs-lookup"><span data-stu-id="dbf99-177">ID@Xbox developer program</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?LinkID=526271"><span data-ttu-id="dbf99-178">Unabhängiges Entwicklerprogramm für Xbox One</span><span class="sxs-lookup"><span data-stu-id="dbf99-178">Independent Developer Program for Xbox One</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-179">ID@Xbox Verbraucherwebsite</span><span class="sxs-lookup"><span data-stu-id="dbf99-179">ID@Xbox consumer site</span></span></td>
        <td><a href="http://www.idatxbox.com/">ID@Xbox</a></td>
    </tr>
</table>

#### <a name="xbox-tools-and-middleware"></a><span data-ttu-id="dbf99-180">Xbox-Tools und Middleware</span><span class="sxs-lookup"><span data-stu-id="dbf99-180">Xbox tools and middleware</span></span>

<span data-ttu-id="dbf99-181">Im Rahmen des Programms für Xbox-Tools und Middleware werden Xbox-Entwicklungskits für professionelle Entwickler von Spieletools und Middleware lizenziert.</span><span class="sxs-lookup"><span data-stu-id="dbf99-181">The Xbox Tools and Middleware Program licenses Xbox development kits to professional developers of game tools and middleware.</span></span> <span data-ttu-id="dbf99-182">Entwickler, die in das Programm aufgenommen werden, können ihre Xbox XDK-Technologien an andere lizenzierte Xbox-Entwickler weitergeben und vertreiben.</span><span class="sxs-lookup"><span data-stu-id="dbf99-182">Developers accepted into the program can share and distribute their Xbox XDK technologies to other licensed Xbox developers.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-183">Programm für Tools und Middleware kontaktieren</span><span class="sxs-lookup"><span data-stu-id="dbf99-183">Contact the tools and middleware program</span></span></td>
        <td><xboxtlsm@microsoft.com></td>
    </tr>
</table>


### <a name="game-samples"></a><span data-ttu-id="dbf99-184">Beispielspiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-184">Game samples</span></span>

<span data-ttu-id="dbf99-185">Für Windows 10-Spiele und -Apps stehen zahlreiche Beispiele zur Verfügung, die einen Eindruck von den Features von Windows 10-Spielen vermitteln und den Einstieg in die Spieleentwicklung erleichtern.</span><span class="sxs-lookup"><span data-stu-id="dbf99-185">There are many Windows 10 game and app samples available to help you understand Windows 10 gaming features and get a quick start on game development.</span></span> <span data-ttu-id="dbf99-186">Es werden regelmäßig weitere Beispiele entwickelt und veröffentlicht. Schauen Sie daher immer mal wieder bei den Beispielportalen vorbei.</span><span class="sxs-lookup"><span data-stu-id="dbf99-186">More samples are developed and published regularly, so don't forget to occasionally check back at sample portals to see what's new.</span></span> <span data-ttu-id="dbf99-187">Darüber hinaus können Sie GitHub-Repositorys [überwachen](https://help.github.com/articles/watching-repositories/), um über Änderungen und Ergänzungen informiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="dbf99-187">You can also [watch](https://help.github.com/articles/watching-repositories/) GitHub repos to be notified of changes and additions.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-188">Beispiele für Universelle Windows-Plattform-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-188">Universal Windows Platform app samples</span></span></td>
        <td><a href="https://github.com/Microsoft/Windows-universal-samples"><span data-ttu-id="dbf99-189">Windows-universal-samples</span><span class="sxs-lookup"><span data-stu-id="dbf99-189">Windows-universal-samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-190">Grafikbeispiele für Direct3D12</span><span class="sxs-lookup"><span data-stu-id="dbf99-190">Direct3D 12 graphics samples</span></span></td>
        <td><a href="https://github.com/Microsoft/DirectX-Graphics-Samples"><span data-ttu-id="dbf99-191">DirectX-Grafikbeispiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-191">DirectX-Graphics-Samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-192">Grafikbeispiele für Direct3D11</span><span class="sxs-lookup"><span data-stu-id="dbf99-192">Direct3D 11 graphics samples</span></span></td>
        <td><a href="https://github.com/walbourn/directx-sdk-samples"><span data-ttu-id="dbf99-193">directx-sdk-samples</span><span class="sxs-lookup"><span data-stu-id="dbf99-193">directx-sdk-samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-194">Beispiel für ein First-Person-Spiel mit Direct3D11</span><span class="sxs-lookup"><span data-stu-id="dbf99-194">Direct3D 11 first-person game sample</span></span></td>
        <td><a href="tutorial--create-your-first-uwp-directx-game.md"><span data-ttu-id="dbf99-195">Erstellen eines einfachen UWP-Spiels mit DirectX</span><span class="sxs-lookup"><span data-stu-id="dbf99-195">Create a simple UWP game with DirectX</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-196">Beispiel für benutzerdefinierte Direct2D-Bildeffekte</span><span class="sxs-lookup"><span data-stu-id="dbf99-196">Direct2D custom image effects sample</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?LinkId=620531"><span data-ttu-id="dbf99-197">D2DCustomEffects</span><span class="sxs-lookup"><span data-stu-id="dbf99-197">D2DCustomEffects</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-198">Beispiel für ein Direct2D-Farbverlaufsgitter</span><span class="sxs-lookup"><span data-stu-id="dbf99-198">Direct2D gradient mesh sample</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?LinkId=620532"><span data-ttu-id="dbf99-199">D2DGradientMesh</span><span class="sxs-lookup"><span data-stu-id="dbf99-199">D2DGradientMesh</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-200">Beispiel für eine Direct2D-Fotoanpassung</span><span class="sxs-lookup"><span data-stu-id="dbf99-200">Direct2D photo adjustment sample</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?LinkId=620533"><span data-ttu-id="dbf99-201">D2DPhotoAdjustment</span><span class="sxs-lookup"><span data-stu-id="dbf99-201">D2DPhotoAdjustment</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-202">Xbox Advanced Technology Group – öffentliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-202">Xbox Advanced Technology Group public samples</span></span></td>
        <td><a href="https://github.com/Microsoft/Xbox-ATG-Samples"><span data-ttu-id="dbf99-203">Xbox-ATG-Beispiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-203">Xbox-ATG-Samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-204">Xbox Live-Beispiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-204">Xbox Live samples</span></span></td>
        <td><a href="https://github.com/Microsoft/xbox-live-samples"><span data-ttu-id="dbf99-205">xbox-live-samples</span><span class="sxs-lookup"><span data-stu-id="dbf99-205">xbox-live-samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-206">Beispiele für XboxOne-Spiele (XGD)</span><span class="sxs-lookup"><span data-stu-id="dbf99-206">Xbox One game samples (XGD)</span></span></td>
        <td><a href="https://developer.microsoft.com/games/xbox/partner/development-education-samples"><span data-ttu-id="dbf99-207">Beispiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-207">Samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-208">Beispiele für Windows-Spiele (MSDN Code Gallery)</span><span class="sxs-lookup"><span data-stu-id="dbf99-208">Windows game samples (MSDN Code Gallery)</span></span></td>
        <td><a href="https://code.msdn.microsoft.com/windowsapps/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=game&f%5B1%5D.Type=Contributors&f%5B1%5D.Value=Microsoft&f%5B1%5D.Text=Microsoft"><span data-ttu-id="dbf99-209">Beispiele für MicrosoftStore-Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-209">Microsoft Store game samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-210">Beispiel für ein Spiel mit JavaScript und 2D</span><span class="sxs-lookup"><span data-stu-id="dbf99-210">JavaScript 2D game sample</span></span></td>
        <td><a href="../get-started/get-started-tutorial-game-js2d.md"><span data-ttu-id="dbf99-211">Erstellen eines UWP-Spiels in JavaScript</span><span class="sxs-lookup"><span data-stu-id="dbf99-211">Create a UWP game in JavaScript</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-212">Beispiel für ein Spiel mit JavaScript und 3D</span><span class="sxs-lookup"><span data-stu-id="dbf99-212">JavaScript 3D game sample</span></span></td>
        <td><a href="../get-started/get-started-tutorial-game-js3d.md"><span data-ttu-id="dbf99-213">Erstellen eines 3D-JavaScript-Spiels mit three.js</span><span class="sxs-lookup"><span data-stu-id="dbf99-213">Creating a 3D JavaScript game using three.js</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-214">Beispiel für ein MonoGame 2D UWP-Spiel</span><span class="sxs-lookup"><span data-stu-id="dbf99-214">MonoGame 2D UWP game sample</span></span></td>
        <td><a href="../get-started/get-started-tutorial-game-mg2d.md"><span data-ttu-id="dbf99-215">Erstellen eines UWP-Spiels in MonoGame-2D</span><span class="sxs-lookup"><span data-stu-id="dbf99-215">Create a UWP game in MonoGame 2D</span></span></a></td>
    </tr>      
</table>


### <a name="developer-forums"></a><span data-ttu-id="dbf99-216">Entwicklerforen</span><span class="sxs-lookup"><span data-stu-id="dbf99-216">Developer forums</span></span>

<span data-ttu-id="dbf99-217">In Entwicklerforen können Entwickler Fragen zur Spieleentwicklung stellen und beantworten und sich mit anderen Spieleentwicklern austauschen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-217">Developer forums are a great place to ask and answer game development questions and connect with the game development community.</span></span> <span data-ttu-id="dbf99-218">Darüber hinaus halten Foren häufig Lösungen für komplizierte Probleme bereit, die Entwickler bereits bewältigt haben.</span><span class="sxs-lookup"><span data-stu-id="dbf99-218">Forums can also be fantastic resources for finding existing answers to difficult issues that developers have faced and solved in the past.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-219">Veröffentlichung Entwicklerforen für apps und Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-219">Publishing apps and games developer forums</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/en-us/home?category=windowsapps"><span data-ttu-id="dbf99-220">Veröffentlichen und anzeigen in apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-220">Publishing and ads-in-apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-221">Entwicklerforum für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-221">UWP apps developer forum</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/en-us/home?forum=wpdevelop"><span data-ttu-id="dbf99-222">Entwicklung von UWP-Apps (Apps für die Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="dbf99-222">Developing Universal Windows Platform apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-223">Entwicklerforen für Desktopanwendungen</span><span class="sxs-lookup"><span data-stu-id="dbf99-223">Desktop applications developer forums</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/en-us/home?category=windowsdesktopdev"><span data-ttu-id="dbf99-224">Foren für Windows-Desktopanwendungen</span><span class="sxs-lookup"><span data-stu-id="dbf99-224">Windows desktop applications forums</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-225">Microsoft Store-Spiele mit DirectX (archivierte Forenbeiträge)</span><span class="sxs-lookup"><span data-stu-id="dbf99-225">DirectX Microsoft Store games (archived forum posts)</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/vstudio/home?forum=wingameswithdirectx"><span data-ttu-id="dbf99-226">Erstellen von MicrosoftStore-Spielen mit DirectX (archiviert)</span><span class="sxs-lookup"><span data-stu-id="dbf99-226">Building Microsoft Store games with DirectX (archived)</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-227">Windows10-Entwicklerforen für verwaltete Partner</span><span class="sxs-lookup"><span data-stu-id="dbf99-227">Windows 10 managed partner developer forums</span></span></td>
        <td><a href="http://aka.ms/win10devforums"><span data-ttu-id="dbf99-228">Xbox-Entwicklerforen: Windows10</span><span class="sxs-lookup"><span data-stu-id="dbf99-228">XBOX Developer Forums: Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-229">DirectX-Foren</span><span class="sxs-lookup"><span data-stu-id="dbf99-229">DirectX forums</span></span></td>
        <td><a href="http://forums.directxtech.com/index.php"><span data-ttu-id="dbf99-230">DirectX12-Forum</span><span class="sxs-lookup"><span data-stu-id="dbf99-230">DirectX 12 forum</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-231">Azure-Plattform-Foren</span><span class="sxs-lookup"><span data-stu-id="dbf99-231">Azure platform forums</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/en-us/home?category=windowsazureplatform"><span data-ttu-id="dbf99-232">Azure-Forum</span><span class="sxs-lookup"><span data-stu-id="dbf99-232">Azure forum</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-233">Xbox Live-Forum</span><span class="sxs-lookup"><span data-stu-id="dbf99-233">Xbox Live forum</span></span></td>
        <td><a href="https://social.msdn.microsoft.com/Forums/en-US/home?forum=xboxlivedev"><span data-ttu-id="dbf99-234">Xbox Live-Entwicklerforum</span><span class="sxs-lookup"><span data-stu-id="dbf99-234">Xbox Live development forum</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-235">PlayFab-Foren</span><span class="sxs-lookup"><span data-stu-id="dbf99-235">PlayFab forums</span></span></td>
        <td><a href="https://community.playfab.com/index.html"><span data-ttu-id="dbf99-236">PlayFab-Foren</span><span class="sxs-lookup"><span data-stu-id="dbf99-236">PlayFab forums</span></span></a></td>
    </tr>
</table>


### <a name="developer-blogs"></a><span data-ttu-id="dbf99-237">Entwicklerblogs</span><span class="sxs-lookup"><span data-stu-id="dbf99-237">Developer blogs</span></span>

<span data-ttu-id="dbf99-238">Entwicklerblogs sind eine weitere praktische Ressource für topaktuelle Informationen zur Spieleentwicklung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-238">Developer blogs are another great resource for the latest information about game development.</span></span> <span data-ttu-id="dbf99-239">Hier finden Sie Beiträge zu neuen Features, Implementierungsdetails, bewährte Methoden, Hintergrundinformationen zur Architektur und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="dbf99-239">You'll find posts about new features, implementation details, best practices, architecture background, and more.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-240">Blog „Building Apps for Windows“</span><span class="sxs-lookup"><span data-stu-id="dbf99-240">Building apps for Windows blog</span></span></td>
        <td><a href="http://blogs.windows.com/buildingapps/"><span data-ttu-id="dbf99-241">Building Apps for Windows</span><span class="sxs-lookup"><span data-stu-id="dbf99-241">Building Apps for Windows</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-242">Windows10 (Blogbeiträge)</span><span class="sxs-lookup"><span data-stu-id="dbf99-242">Windows 10 (blog posts)</span></span></td>
        <td><a href="http://blogs.windows.com/blog/tag/windows-10/"><span data-ttu-id="dbf99-243">Beiträge in Windows10</span><span class="sxs-lookup"><span data-stu-id="dbf99-243">Posts in Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-244">Blog des VisualStudio-Entwicklerteams</span><span class="sxs-lookup"><span data-stu-id="dbf99-244">Visual Studio engineering team blog</span></span></td>
        <td><a href="http://blogs.msdn.com/b/visualstudio/"><span data-ttu-id="dbf99-245">The Visual Studio Blog</span><span class="sxs-lookup"><span data-stu-id="dbf99-245">The Visual Studio Blog</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-246">Blogs zu VisualStudio-Entwicklertools</span><span class="sxs-lookup"><span data-stu-id="dbf99-246">Visual Studio developer tools blogs</span></span></td>
        <td><a href="http://blogs.msdn.com/b/developer-tools/"><span data-ttu-id="dbf99-247">Developer Tools Blogs</span><span class="sxs-lookup"><span data-stu-id="dbf99-247">Developer Tools Blogs</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-248">Somasegars-Blog zu Entwicklertools</span><span class="sxs-lookup"><span data-stu-id="dbf99-248">Somasegar's developer tools blog</span></span></td>
        <td><a href="http://blogs.msdn.com/b/somasegar/"><span data-ttu-id="dbf99-249">Somasegar’s blog</span><span class="sxs-lookup"><span data-stu-id="dbf99-249">Somasegar’s blog</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-250">DirectX-Entwicklerblog</span><span class="sxs-lookup"><span data-stu-id="dbf99-250">DirectX developer blog</span></span></td>
        <td><a href="http://blogs.msdn.com/b/directx"><span data-ttu-id="dbf99-251">DirectX Developer Blog</span><span class="sxs-lookup"><span data-stu-id="dbf99-251">DirectX Developer blog</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-252">Einführung in DirectX12 (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="dbf99-252">DirectX 12 introduction (blog post)</span></span></td>
        <td><a href="http://blogs.msdn.com/b/directx/archive/2014/03/20/directx-12.aspx"><span data-ttu-id="dbf99-253">DirectX12</span><span class="sxs-lookup"><span data-stu-id="dbf99-253">DirectX 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-254">Teamblog zu VisualC++-Tools</span><span class="sxs-lookup"><span data-stu-id="dbf99-254">Visual C++ tools team blog</span></span></td>
        <td><a href="http://blogs.msdn.com/b/vcblog/"><span data-ttu-id="dbf99-255">Teamblog zu Visual C++</span><span class="sxs-lookup"><span data-stu-id="dbf99-255">Visual C++ team blog</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-256">Blog des PIX-Teams</span><span class="sxs-lookup"><span data-stu-id="dbf99-256">PIX team blog</span></span></td>
        <td><a href="https://blogs.msdn.microsoft.com/pix/"><span data-ttu-id="dbf99-257">Leistungsoptimierung und -Debuggen von DirectX12-Spielen für Windows und Xbox</span><span class="sxs-lookup"><span data-stu-id="dbf99-257">Performance tuning and debugging for DirectX 12 games on Windows and Xbox</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-258">Universelle Windows-App – Blog des Bereitstellungsteams</span><span class="sxs-lookup"><span data-stu-id="dbf99-258">Universal Windows App Deployment team blog</span></span></td>
        <td><a href="https://blogs.msdn.microsoft.com/appinstaller/"><span data-ttu-id="dbf99-259">Erstellen und Bereitstellen von UWP-Apps – Teamblog</span><span class="sxs-lookup"><span data-stu-id="dbf99-259">Build and deploy UWP apps team blog</span></span></a></td>
    </tr>
</table>
 

## <a name="concept-and-planning"></a><span data-ttu-id="dbf99-260">Konzept und Planung</span><span class="sxs-lookup"><span data-stu-id="dbf99-260">Concept and planning</span></span>


<span data-ttu-id="dbf99-261">In der Konzeptionierungs- und Planungsphase entscheiden Sie, welches Spiel Sie entwickeln möchten und mit welchen Tools und Technologien Sie es zum Leben erwecken.</span><span class="sxs-lookup"><span data-stu-id="dbf99-261">In the concept and planning stage, you're deciding what your game is going to be like and the technologies and tools you'll use to bring it to life.</span></span>

### <a name="overview-of-game-development-technologies"></a><span data-ttu-id="dbf99-262">Übersicht über Technologien für die Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="dbf99-262">Overview of game development technologies</span></span>

<span data-ttu-id="dbf99-263">Zu Beginn der Entwicklung eines UWP-Spiels haben Sie die Wahl zwischen verschiedenen Optionen für Grafik, Eingabe, Audio, Netzwerk, Hilfsprogramme und Bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="dbf99-263">When you start developing a game for the UWP you have multiple options available for graphics, input, audio, networking, utilities, and libraries.</span></span>

<span data-ttu-id="dbf99-264">Vielleicht haben Sie ja bereits entschieden, welche Technologien Sie in Ihrem Spiel verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="dbf99-264">If you've already decided on all the technologies you'll be using in your game, great!</span></span> <span data-ttu-id="dbf99-265">Andernfalls finden Sie im Handbuch [Spieletechnologien für UWP-Apps](game-development-platform-guide.md) eine hervorragende Übersicht über viele der verfügbaren Technologien. Es wird nachdrücklich empfohlen, dieses Handbuch zu lesen, um mehr über die Optionen und ihre Kombinationsmöglichkeiten zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="dbf99-265">If not, the [Game technologies for UWP apps](game-development-platform-guide.md) guide is an excellent overview of many of the technologies available, and is highly recommended reading to help you understand the options and how they fit together.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-266">Überblick über UWP-Spieletechnologien</span><span class="sxs-lookup"><span data-stu-id="dbf99-266">Survey of UWP game technologies</span></span></td>
        <td><a href="game-development-platform-guide.md"><span data-ttu-id="dbf99-267">Spieletechnologien für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-267">Game technologies for UWP apps</span></span></a></td>
    </tr>
</table>
 

<span data-ttu-id="dbf99-268">Diese drei GDC2015-Videos vermitteln einen guten Überblick über die Entwicklung von Windows10-Spielen und das Spielerlebnis unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="dbf99-268">These three GDC 2015 videos give a good overview of Windows 10 game development and the Windows 10 gaming experience.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-269">Übersicht über die Entwicklung von Windows10-Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-269">Overview of Windows 10 game development (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Developing-Games-for-Windows-10"><span data-ttu-id="dbf99-270">Entwickeln von Spielen für Windows10</span><span class="sxs-lookup"><span data-stu-id="dbf99-270">Developing Games for Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-271">Spielerlebnis unter Windows10 (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-271">Windows 10 gaming experience (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Gaming-Consumer-Experience-on-Windows-10"><span data-ttu-id="dbf99-272">Spielerfahrung von Endbenutzern unter Windows10</span><span class="sxs-lookup"><span data-stu-id="dbf99-272">Gaming Consumer Experience on Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-273">Übergreifendes Spielen im gesamten Microsoft-Ökosystem (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-273">Gaming across the Microsoft ecosystem (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/The-Future-of-Gaming-Across-the-Microsoft-Ecosystem"><span data-ttu-id="dbf99-274">Die Zukunft des Spielens im gesamten Microsoft-Ökosystem</span><span class="sxs-lookup"><span data-stu-id="dbf99-274">The Future of Gaming Across the Microsoft Ecosystem</span></span></a></td>
    </tr>
</table>

### <a name="game-planning"></a><span data-ttu-id="dbf99-275">Planen von Spielen</span><span class="sxs-lookup"><span data-stu-id="dbf99-275">Game planning</span></span>

<span data-ttu-id="dbf99-276">Im Folgenden finden Sie einige Konzept- und Planungsthemen, die Ihnen einen Überblick über das geben, was Sie bei der Planung Ihres Spiels berücksichtigen sollten.</span><span class="sxs-lookup"><span data-stu-id="dbf99-276">These are some high level concept and planning topics to consider when planning for your game.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-277">Erstellen barrierefreier Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-277">Make your game accessible</span></span></td>
        <td><a href="https://msdn.microsoft.com/windows/uwp/gaming/accessibility-for-games"><span data-ttu-id="dbf99-278">Barrierefreiheit von Spielen</span><span class="sxs-lookup"><span data-stu-id="dbf99-278">Accessibility for games</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-279">Erstellen von Spielen mit der Cloud</span><span class="sxs-lookup"><span data-stu-id="dbf99-279">Build games using cloud</span></span></td>
        <td><a href="https://msdn.microsoft.com/windows/uwp/gaming/cloud-for-games"><span data-ttu-id="dbf99-280">Cloud für Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-280">Cloud for games</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-281">Monetisierung eines Spiels</span><span class="sxs-lookup"><span data-stu-id="dbf99-281">Monetize your game</span></span></td>
        <td><a href="https://msdn.microsoft.com/windows/uwp/gaming/monetization-for-games"><span data-ttu-id="dbf99-282">Monetarisierung von Spielen</span><span class="sxs-lookup"><span data-stu-id="dbf99-282">Monetization for games</span></span></a></td>
    </tr>
</table>



### <a name="choosing-your-graphics-technology-and-programming-language"></a><span data-ttu-id="dbf99-283">Auswählen der Grafiktechnologie und Programmiersprache</span><span class="sxs-lookup"><span data-stu-id="dbf99-283">Choosing your graphics technology and programming language</span></span>

<span data-ttu-id="dbf99-284">Für Windows10-Spiele stehen verschiedene Programmiersprachen und Grafiktechnologien zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-284">There are several programming languages and graphics technologies available for use in Windows 10 games.</span></span> <span data-ttu-id="dbf99-285">Der jeweilige Ansatz richtet sich nach der Art des Spiels, das Sie entwickeln, der Erfahrung und den Vorlieben Ihres Entwicklungsstudios und den bestimmten Funktionsanforderungen Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="dbf99-285">The path you take depends on the type of game you’re developing, the experience and preferences of your development studio, and specific feature requirements of your game.</span></span> <span data-ttu-id="dbf99-286">Möchten Sie C#, C++ oder JavaScript verwenden?</span><span class="sxs-lookup"><span data-stu-id="dbf99-286">Will you use C#, C++, or JavaScript?</span></span> <span data-ttu-id="dbf99-287">DirectX, XAML oder HTML5?</span><span class="sxs-lookup"><span data-stu-id="dbf99-287">DirectX, XAML, or HTML5?</span></span>

#### <a name="directx"></a><span data-ttu-id="dbf99-288">DirectX</span><span class="sxs-lookup"><span data-stu-id="dbf99-288">DirectX</span></span>

<span data-ttu-id="dbf99-289">Microsoft DirectX ist die richtige Wahl für 2D/3D-Grafik und Multimediaelemente.</span><span class="sxs-lookup"><span data-stu-id="dbf99-289">Microsoft DirectX is the choice to make for the highest-performance 2D and 3D graphics and multimedia.</span></span>

<span data-ttu-id="dbf99-290">DirectX 12 ist schneller und effizienter als alle früheren Versionen von Direct3D.</span><span class="sxs-lookup"><span data-stu-id="dbf99-290">DirectX 12 is faster and more efficient than any previous version.</span></span> <span data-ttu-id="dbf99-291">Direct3D12 ermöglicht detaillierte Umgebungen, mehr Objekte, komplexere Effekte und eine optimale Nutzung moderner GPU-Hardware auf Windows 10 PCs und Xbox One.</span><span class="sxs-lookup"><span data-stu-id="dbf99-291">Direct3D 12 enables richer scenes, more objects, more complex effects, and full utilization of modern GPU hardware on Windows 10 PCs and Xbox One.</span></span>

<span data-ttu-id="dbf99-292">Sie können weiterhin die vertraute Grafikpipeline von Direct3D11 verwenden und gleichzeitig von den neuen Rendering- und Optimierungsfeatures profitieren, die in Direct3D11.3 hinzugekommen sind.</span><span class="sxs-lookup"><span data-stu-id="dbf99-292">If you want to use the familiar graphics pipeline of Direct3D 11, you’ll still benefit from the new rendering and optimization features added to Direct3D 11.3.</span></span> <span data-ttu-id="dbf99-293">Und wenn Sie ein richtiger Windows-API-Entwickler für den Desktop mit Win32-Erfahrung sind, steht Ihnen unter Windows10 auch diese Option zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-293">And, if you’re a tried-and-true desktop Windows API developer with roots in Win32, you’ll still have that option in Windows 10.</span></span>

<span data-ttu-id="dbf99-294">Dank umfangreicher Features und einer umfassenden Plattformintegration lassen sich mit DirectX selbst anspruchsvollste Spiele realisieren.</span><span class="sxs-lookup"><span data-stu-id="dbf99-294">The extensive features and deep platform integration of DirectX provide the power and performance needed by the most demanding games.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-295">DirectX für die UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="dbf99-295">DirectX for UWP development</span></span></td>
        <td><a href="directx-programming.md"><span data-ttu-id="dbf99-296">DirectX-Programmierung</span><span class="sxs-lookup"><span data-stu-id="dbf99-296">DirectX programming</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-297">Lernprogramm: Erstellen eines UWP-DirectX-Spiels</span><span class="sxs-lookup"><span data-stu-id="dbf99-297">Tutorial: How to create a UWP DirectX game</span></span></td>
        <td><a href="tutorial--create-your-first-uwp-directx-game.md"><span data-ttu-id="dbf99-298">Erstellen eines einfachen UWP-Spiels mit DirectX</span><span class="sxs-lookup"><span data-stu-id="dbf99-298">Create a simple UWP game with DirectX</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-299">Übersichten und Referenzen zu DirectX</span><span class="sxs-lookup"><span data-stu-id="dbf99-299">DirectX overviews and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/ee663274"><span data-ttu-id="dbf99-300">DirectX-Grafiken und -Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-300">DirectX Graphics and Gaming</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-301">Direct3D12-Programmieranleitung und -referenz</span><span class="sxs-lookup"><span data-stu-id="dbf99-301">Direct3D 12 programming guide and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn903821"><span data-ttu-id="dbf99-302">Direct3D12-Grafiken</span><span class="sxs-lookup"><span data-stu-id="dbf99-302">Direct3D 12 Graphics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-303">Videos zu Grafiken und zur DirectX 12-Entwicklung (YouTube-Kanal)</span><span class="sxs-lookup"><span data-stu-id="dbf99-303">Graphics and DirectX 12 development videos (YouTube channel)</span></span></td>
        <td><a href="https://www.youtube.com/channel/UCiaX2B8XiXR70jaN7NK-FpA"><span data-ttu-id="dbf99-304">Informationen zu Microsoft DirectX12 und Grafiken</span><span class="sxs-lookup"><span data-stu-id="dbf99-304">Microsoft DirectX 12 and Graphics Education</span></span></a></td>
    </tr>
</table>
 

#### <a name="xaml"></a><span data-ttu-id="dbf99-305">XAML</span><span class="sxs-lookup"><span data-stu-id="dbf99-305">XAML</span></span>

<span data-ttu-id="dbf99-306">XAML ist eine benutzerfreundliche deklarative UI-Sprache mit nützlichen Features wie Animationen, Storyboards, Datenbindung, skalierbaren vektorbasierten Grafiken, dynamischer Größenänderung und Szenendiagrammen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-306">XAML is an easy-to-use declarative UI language with convenient features like animations, storyboards, data binding, scalable vector-based graphics, dynamic resizing, and scene graphs.</span></span> <span data-ttu-id="dbf99-307">XAML eignet sich gut für Benutzeroberflächen, Menüs, Sprites und 2D-Grafiken von Spielen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-307">XAML works great for game UI, menus, sprites, and 2D graphics.</span></span> <span data-ttu-id="dbf99-308">Zur Vereinfachung der UI-Layouterstellung ist XAML mit Entwurfs- und Entwicklungstools wie Expression Blend und Microsoft Visual Studio kompatibel.</span><span class="sxs-lookup"><span data-stu-id="dbf99-308">To make UI layout easy, XAML is compatible with design and development tools like Expression Blend and Microsoft Visual Studio.</span></span> <span data-ttu-id="dbf99-309">XAML wird häufig mit C# kombiniert, aber auch C++ ist eine gute Wahl, falls dies Ihre bevorzugte Programmiersprache ist oder Ihr Spiel hohe Ansprüche an die CPU stellt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-309">XAML is commonly used with C#, but C++ is also a good choice if that’s your preferred language or if your game has high CPU demands.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-310">XAML-Plattformübersicht</span><span class="sxs-lookup"><span data-stu-id="dbf99-310">XAML platform overview</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt228259"><span data-ttu-id="dbf99-311">XAML-Plattform</span><span class="sxs-lookup"><span data-stu-id="dbf99-311">XAML platform</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-312">XAML-UI und -Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="dbf99-312">XAML UI and controls</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt228348"><span data-ttu-id="dbf99-313">Steuerelemente, Layouts und Text</span><span class="sxs-lookup"><span data-stu-id="dbf99-313">Controls, layouts, and text</span></span></a></td>
    </tr>
</table>
 

#### <a name="html-5"></a><span data-ttu-id="dbf99-314">HTML5</span><span class="sxs-lookup"><span data-stu-id="dbf99-314">HTML 5</span></span>

<span data-ttu-id="dbf99-315">Die HyperText Markup Language (HTML) ist eine häufig verwendete Markup-Sprache für Benutzeroberflächen, die bei Webseiten, Apps und Rich-Clients zum Einsatz kommt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-315">HyperText Markup Language (HTML) is a common UI markup language used for web pages, apps, and rich clients.</span></span> <span data-ttu-id="dbf99-316">Für Windows-Spiele kann HTML5 als Darstellungsschicht mit vollem Funktionsumfang genutzt werden. Dabei stehen die vertrauten Features von HTML, Zugriff auf die universelle Windows-Plattform und Unterstützung für moderne Webfeatures wie AppCache, Web-Worker, Canvas, Drag&Drop, asynchrone Programmierung und SVG zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-316">Windows games can use HTML5 as a full-featured presentation layer with the familiar features of HTML, access to the Universal Windows Platform, and support for modern web features like AppCache, Web Workers, canvas, drag-and-drop, asynchronous programming, and SVG.</span></span> <span data-ttu-id="dbf99-317">Im Hintergrund wird für das HTML-Rendering die leistungsstarke DirectX-Hardwarebeschleunigung genutzt, sodass Sie weiterhin in den Genuss der Leistungsvorteile von DirectX kommen, ohne zusätzlichen Code schreiben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-317">Behind the scenes, HTML rendering takes advantage of the power of DirectX hardware acceleration, so you can still get the performance benefits of DirectX without writing any extra code.</span></span> <span data-ttu-id="dbf99-318">HTML5 ist eine gute Wahl, wenn Sie sich mit der Webentwicklung auskennen, ein Webspiel portieren oder Sprach- und Grafikebenen nutzen möchten, die unter Umständen leichter zugänglich als andere Optionen sind.</span><span class="sxs-lookup"><span data-stu-id="dbf99-318">HTML5 is a good choice if you are proficient with web development, porting a web game, or want to use language and graphics layers that can be easier to approach than the other choices.</span></span> <span data-ttu-id="dbf99-319">HTML5 wird zusammen mit JavaScript verwendet, kann aber auch mit Komponenten verknüpft werden, die mit C# oder C++/CX erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="dbf99-319">HTML5 is used with JavaScript, but can also call into components created with C# or C++/CX.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-320">Informationen zu HTML5 und zum Dokumentobjektmodell</span><span class="sxs-lookup"><span data-stu-id="dbf99-320">HTML5 and Document Object Model information</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/br212882.aspx"><span data-ttu-id="dbf99-321">HTML- und DOM-Referenz</span><span class="sxs-lookup"><span data-stu-id="dbf99-321">HTML and DOM reference</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-322">Die HTML5-Empfehlung des W3C</span><span class="sxs-lookup"><span data-stu-id="dbf99-322">The HTML5 W3C Recommendation</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?linkid=221374"><span data-ttu-id="dbf99-323">HTML5</span><span class="sxs-lookup"><span data-stu-id="dbf99-323">HTML5</span></span></a></td>
    </tr>
</table>
 

#### <a name="combining-presentation-technologies"></a><span data-ttu-id="dbf99-324">Kombinieren von Darstellungstechnologien</span><span class="sxs-lookup"><span data-stu-id="dbf99-324">Combining presentation technologies</span></span>

<span data-ttu-id="dbf99-325">Die Microsoft DirectX Graphic Infrastructure (DXGI) bietet Interoperabilität und Kompatibilität mit mehreren Arten von Grafiktechnologien.</span><span class="sxs-lookup"><span data-stu-id="dbf99-325">The Microsoft DirectX Graphics Infrastructure (DXGI) provides interop and compatibility across multiple graphics technologies.</span></span> <span data-ttu-id="dbf99-326">Für Hochleistungsgrafiken können Sie XAML und DirectX kombinieren, indem Sie XAML für Menüs und andere einfache UI-Elemente und DirectX für das Rendern von komplexen 2D- und 3D-Szenen nutzen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-326">For high-performance graphics, you can combine XAML and DirectX, using XAML for menus and other simple UI, and DirectX for rendering complex 2D and 3D scenes.</span></span> <span data-ttu-id="dbf99-327">DXGI sorgt auch für Kompatibilität zwischen Direct2D, Direct3D, DirectWrite, DirectCompute und der Microsoft Media Foundation.</span><span class="sxs-lookup"><span data-stu-id="dbf99-327">DXGI also provides compatibility between Direct2D, Direct3D, DirectWrite, DirectCompute, and the Microsoft Media Foundation.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-328">Programmieranleitung und Referenz für die DirectX Graphic Infrastructure</span><span class="sxs-lookup"><span data-stu-id="dbf99-328">DirectX Graphics Infrastructure programming guide and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/hh404534"><span data-ttu-id="dbf99-329">DXGI</span><span class="sxs-lookup"><span data-stu-id="dbf99-329">DXGI</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-330">Kombinieren von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="dbf99-330">Combining DirectX and XAML</span></span></td>
        <td><a href="directx-and-xaml-interop.md"><span data-ttu-id="dbf99-331">Interoperabilität von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="dbf99-331">DirectX and XAML interop</span></span></a></td>
    </tr>
</table>
 

#### <a name="c"></a><span data-ttu-id="dbf99-332">C++</span><span class="sxs-lookup"><span data-stu-id="dbf99-332">C++</span></span>

<span data-ttu-id="dbf99-333">C++/CX ist eine effiziente Hochleistungssprache und bietet eine erstklassige Mischung aus Geschwindigkeit, Kompatibilität und Plattformzugriff.</span><span class="sxs-lookup"><span data-stu-id="dbf99-333">C++/CX is a high-performance, low overhead language that provides the powerful combination of speed, compatibility, and platform access.</span></span> <span data-ttu-id="dbf99-334">C++/CX erleichtert Ihnen die Nutzung aller nützlichen Gaming-Features unter Windows10, z.B. DirectX und Xbox Live.</span><span class="sxs-lookup"><span data-stu-id="dbf99-334">C++/CX makes it easy to use all of the great gaming features in Windows 10, including DirectX and Xbox Live.</span></span> <span data-ttu-id="dbf99-335">Außerdem können Sie vorhandenen C++-Code und die dazugehörigen Bibliotheken verwenden.</span><span class="sxs-lookup"><span data-stu-id="dbf99-335">You can also reuse existing C++ code and libraries.</span></span> <span data-ttu-id="dbf99-336">Mit C++/CX wird schneller, systemeigener Code erstellt, bei dem kein Aufwand für die Garbage Collection anfällt. So kann Ihr Spiel mit einer hohen Leistung und einem geringen Stromverbrauch aufwarten und somit auch eine längere Akkulaufzeit ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-336">C++/CX creates fast, native code that doesn’t incur the overhead of garbage collection, so your game can have great performance and low power consumption, which leads to longer battery life.</span></span> <span data-ttu-id="dbf99-337">Verwenden Sie C++/CX mit DirectX oder XAML, oder erstellen Sie ein Spiel mit einer Kombination aus beidem.</span><span class="sxs-lookup"><span data-stu-id="dbf99-337">Use C++/CX with DirectX or XAML, or create a game that uses a combination of both.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-338">Referenz und Übersichten für C++/CX</span><span class="sxs-lookup"><span data-stu-id="dbf99-338">C++/CX reference and overviews</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/hh699871.aspx"><span data-ttu-id="dbf99-339">Visual C++-Programmiersprachenreferenz (C++/CX)</span><span class="sxs-lookup"><span data-stu-id="dbf99-339">Visual C++ Language Reference (C++/CX)</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-340">Visual C++-Programmieranleitung und -Referenz</span><span class="sxs-lookup"><span data-stu-id="dbf99-340">Visual C++ programming guide and reference</span></span></td>
        <td><a href="https://docs.microsoft.com/cpp/visual-cpp-in-visual-studio"><span data-ttu-id="dbf99-341">Visual C++ in Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="dbf99-341">Visual C++ in Visual Studio 2017</span></span></a></td>
    </tr>
</table>
 

#### <a name="c"></a><span data-ttu-id="dbf99-342">C#</span><span class="sxs-lookup"><span data-stu-id="dbf99-342">C#</span></span>

<span data-ttu-id="dbf99-343">C# (sprich: „C sharp“) ist eine moderne, innovative Programmiersprache, die einfach, leistungsstark, typsicher und objektorientiert ist.</span><span class="sxs-lookup"><span data-stu-id="dbf99-343">C# (pronounced "C sharp") is a modern, innovative language that is simple, powerful, type-safe, and object-oriented.</span></span> <span data-ttu-id="dbf99-344">C# ermöglicht eine schnelle Entwicklung, während gleichzeitig die Vertrautheit und Ausdruckskraft von Sprachen im C-Stil gewahrt bleibt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-344">C# enables rapid development while retaining the familiarity and expressiveness of C-style languages.</span></span> <span data-ttu-id="dbf99-345">Obwohl C# einfach zu verwenden ist, verfügt die Sprache über viele moderne Sprachfeatures wie Polymorphie, Delegate, Lambda-Elemente, Abschlüsse, Iteratormethoden, Kovarianz und LINQ-Ausdrücke (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="dbf99-345">Though easy to use, C# has numerous advanced language features like polymorphism, delegates, lambdas, closures, iterator methods, covariance, and Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="dbf99-346">C# ist eine ausgezeichnete Wahl, wenn Sie XAML verwenden möchten, schnell mit der Entwicklung Ihres Spiels beginnen möchten oder bereits über C#-Erfahrung verfügen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-346">C# is an excellent choice if you are targeting XAML, want to get a quick start developing your game, or have previous C# experience.</span></span> <span data-ttu-id="dbf99-347">C# wird vorrangig mit XAML genutzt. Wenn Sie also DirectX verwenden möchten, entscheiden Sie sich besser für C++, oder schreiben Sie einen Teil des Spiels als C++-Komponente, die mit DirectX interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="dbf99-347">C# is used primarily with XAML, so if you want to use DirectX, choose C++ instead, or write part of your game as a C++ component that interacts with DirectX.</span></span> <span data-ttu-id="dbf99-348">Eine weitere Alternative wäre [Win2D](https://github.com/Microsoft/Win2D) – eine Direct2D-Grafikbibliothek im unmittelbaren Modus für C# und C++.</span><span class="sxs-lookup"><span data-stu-id="dbf99-348">Or, consider [Win2D](https://github.com/Microsoft/Win2D), an immediate mode Direct2D graphics libary for C# and C++.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-349">C#-Programmieranleitung und -Referenz</span><span class="sxs-lookup"><span data-stu-id="dbf99-349">C# programming guide and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/kx37x362.aspx"><span data-ttu-id="dbf99-350">C#-Programmiersprachenreferenz</span><span class="sxs-lookup"><span data-stu-id="dbf99-350">C# language reference</span></span></a></td>
    </tr>
</table>
 

#### <a name="javascript"></a><span data-ttu-id="dbf99-351">JavaScript</span><span class="sxs-lookup"><span data-stu-id="dbf99-351">JavaScript</span></span>

<span data-ttu-id="dbf99-352">JavaScript ist eine dynamische Skriptsprache, die gerne für moderne Webanwendungen und Rich-Client-Anwendungen eingesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="dbf99-352">JavaScript is a dynamic scripting language widely used for modern web and rich client applications.</span></span>

<span data-ttu-id="dbf99-353">Bei Windows-JavaScript-Apps kann auf einfache und intuitive Weise auf die leistungsfähigen Features der universellen Windows-Plattform zugegriffen werden – in Form von Methoden und Eigenschaften objektorientierter JavaScript-Klassen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-353">Windows JavaScript apps can access the powerful features of the Universal Windows Platform in an easy, intuitive way—as methods and properties of object-oriented JavaScript classes.</span></span> <span data-ttu-id="dbf99-354">JavaScript ist für Ihr Spiel eine gute Wahl, wenn Sie aus dem Bereich der Webentwicklung kommen, sich mit JavaScript bereits auskennen oder HTML5-, CSS-, WinJS- oder JavaScript-Bibliotheken verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="dbf99-354">JavaScript is a good choice for your game if you’re coming from a web development environment, are already familiar with JavaScript, or want to use HTML5, CSS, WinJS, or JavaScript libraries.</span></span> <span data-ttu-id="dbf99-355">Wenn Sie Ihre Entwicklung auf DirectX oder XAML ausrichten möchten, ist C# oder C++/CX die bessere Wahl.</span><span class="sxs-lookup"><span data-stu-id="dbf99-355">If you’re targeting DirectX or XAML, choose C# or C++/CX instead.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-356">Referenz zu JavaScript und Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="dbf99-356">JavaScript and Windows Runtime reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/jj613794"><span data-ttu-id="dbf99-357">JavaScript-Referenz</span><span class="sxs-lookup"><span data-stu-id="dbf99-357">JavaScript reference</span></span></a></td>
    </tr>
</table>


#### <a name="use-windows-runtime-components-to-combine-languages"></a><span data-ttu-id="dbf99-358">Kombinieren von Programmiersprachen mithilfe von Windows-Runtime-Komponenten</span><span class="sxs-lookup"><span data-stu-id="dbf99-358">Use Windows Runtime Components to combine languages</span></span>

<span data-ttu-id="dbf99-359">Mit der universellen Windows-Plattform lassen sich problemlos Komponenten in unterschiedlichen Programmiersprachen kombinieren.</span><span class="sxs-lookup"><span data-stu-id="dbf99-359">With the Universal Windows Platform, it’s easy to combine components written in different languages.</span></span> <span data-ttu-id="dbf99-360">Erstellen Sie Komponenten für Windows-Runtime in C++, C# oder Visual Basic, und nutzen Sie diese dann per JavaScript, C#, C++ oder Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dbf99-360">Create Windows Runtime Components in C++, C#, or Visual Basic, and then call into them from JavaScript, C#, C++, or Visual Basic.</span></span> <span data-ttu-id="dbf99-361">Dies ist eine hervorragende Möglichkeit, wenn Sie Teile des Spiels in der Sprache Ihrer Wahl programmieren möchten.</span><span class="sxs-lookup"><span data-stu-id="dbf99-361">This is a great way to program portions of your game in the language of your choice.</span></span> <span data-ttu-id="dbf99-362">Über Komponenten können Sie außerdem externe Bibliotheken nutzen, die nur in einer bestimmten Programmiersprache verfügbar sind, oder auch älteren Code, den Sie bereits geschrieben haben.</span><span class="sxs-lookup"><span data-stu-id="dbf99-362">Components also let you consume external libraries that are only available in a particular language, as well as use legacy code you’ve already written.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-363">So wird's gemacht: Erstellen von Komponenten für die Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="dbf99-363">How to create Windows Runtime Components</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp"><span data-ttu-id="dbf99-364">Erstellen von Windows-Runtime-Komponenten</span><span class="sxs-lookup"><span data-stu-id="dbf99-364">Creating Windows Runtime Components</span></span></a></td>
    </tr>
</table>


### <a name="which-version-of-directx-should-your-game-use"></a><span data-ttu-id="dbf99-365">Welche DirectX-Version sollte Ihr Spiel verwenden?</span><span class="sxs-lookup"><span data-stu-id="dbf99-365">Which version of DirectX should your game use?</span></span>

<span data-ttu-id="dbf99-366">Wenn Sie für Ihr Spiel mit DirectX entwickeln, müssen Sie entscheiden, welche Version Sie verwenden: Microsoft Direct3D12 oder Microsoft Direct3D11.</span><span class="sxs-lookup"><span data-stu-id="dbf99-366">If you are choosing DirectX for your game, you'll need to decide which version to use: Microsoft Direct3D12 or Microsoft Direct3D11.</span></span>

<span data-ttu-id="dbf99-367">DirectX 12 ist schneller und effizienter als alle früheren Versionen von Direct3D.</span><span class="sxs-lookup"><span data-stu-id="dbf99-367">DirectX 12 is faster and more efficient than any previous version.</span></span> <span data-ttu-id="dbf99-368">Direct3D12 ermöglicht detaillierte Umgebungen, mehr Objekte, komplexere Effekte und eine optimale Nutzung moderner GPU-Hardware auf Windows 10 PCs und Xbox One.</span><span class="sxs-lookup"><span data-stu-id="dbf99-368">Direct3D 12 enables richer scenes, more objects, more complex effects, and full utilization of modern GPU hardware on Windows 10 PCs and Xbox One.</span></span> <span data-ttu-id="dbf99-369">Da Direct3D12 auf einer sehr niedrigen Ebene ausgeführt wird, erhält ein erfahrenes Grafikentwicklungs- oder DirectX11-Entwicklungsteam alle notwendigen Steuerungsmöglichkeiten für die Maximierung der Grafikoptimierung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-369">Since Direct3D 12 works at a very low level, it is able to give an expert graphics development team or an experienced DirectX 11 development team all the control they need to maximize graphics optimization.</span></span>

<span data-ttu-id="dbf99-370">Direct3D11.3 ist eine Grafik-API auf einem niedrigen Niveau, die das vertraute Direct3D-Programmiermodell verwendet und Ihnen einen größeren Teil der Komplexität abnimmt, die mit dem GPU-Rendering verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="dbf99-370">Direct3D 11.3 is a low level graphics API that uses the familiar Direct3D programming model and handles for you more of the complexity involved in GPU rendering.</span></span> <span data-ttu-id="dbf99-371">Sie wird auch von Windows10 und Xbox One unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-371">It is also supported in Windows 10 and Xbox One.</span></span> <span data-ttu-id="dbf99-372">Wenn Sie über ein vorhandenes Modul verfügen, das in Direct3D 11 geschrieben wurde, und noch nicht bereit sind, zu Direct3D12 zu wechseln, können Sie Direct3D11 auf 12 verwenden, um einige Leistungsverbesserungen zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-372">If you have an existing engine written in Direct3D 11, and you're not quite ready to make the jump to Direct3D 12, you can use Direct3D 11 on 12 to achieve some performance improvements.</span></span> <span data-ttu-id="dbf99-373">Die Versionen ab 11.3 enthalten die neuen Rendering- und Optimierungsfeatures, die auch in Direct3D12 zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-373">Versions 11.3+ contain the new rendering and optimization features enabled also in Direct3D 12.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-374">Auswählen von Direct3D12 oder Direct3D11</span><span class="sxs-lookup"><span data-stu-id="dbf99-374">Choosing Direct3D12 or Direct3D11</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn899228"><span data-ttu-id="dbf99-375">Was ist Direct3D12?</span><span class="sxs-lookup"><span data-stu-id="dbf99-375">What is Direct3D12?</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-376">Übersicht über Direct3D11</span><span class="sxs-lookup"><span data-stu-id="dbf99-376">Overview of Direct3D11</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/ff476080"><span data-ttu-id="dbf99-377">Direct3D11-Grafik</span><span class="sxs-lookup"><span data-stu-id="dbf99-377">Direct3D 11 Graphics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-378">Übersicht über „Direct3D 11 on 12“</span><span class="sxs-lookup"><span data-stu-id="dbf99-378">Overview of Direct3D 11 on 12</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn913195"><span data-ttu-id="dbf99-379">Direct3D 11 on 12</span><span class="sxs-lookup"><span data-stu-id="dbf99-379">Direct3D 11 on 12</span></span></a></td>
    </tr>
</table>


### <a name="bridges-game-engines-and-middleware"></a><span data-ttu-id="dbf99-380">Brücken, Spielengines und Middleware</span><span class="sxs-lookup"><span data-stu-id="dbf99-380">Bridges, game engines, and middleware</span></span>

<span data-ttu-id="dbf99-381">Mithilfe von Brücken, Spielengines und Middleware können Sie je nach Spiel unter Umständen die Entwicklung und das Testing beschleunigen und den damit verbundenen Ressourcenaufwand verringern.</span><span class="sxs-lookup"><span data-stu-id="dbf99-381">Depending on the needs of your game, using bridges, game engines, or middleware can save development and testing time and resources.</span></span> <span data-ttu-id="dbf99-382">Hier ist eine Übersicht und Ressourcen für Brücken, Spielengines und Middleware.</span><span class="sxs-lookup"><span data-stu-id="dbf99-382">Here are some overview and resources for bridges, game engines, and middleware.</span></span>

#### <a name="universal-windows-platform-bridges"></a><span data-ttu-id="dbf99-383">Brücken für die universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="dbf99-383">Universal Windows Platform Bridges</span></span>

<span data-ttu-id="dbf99-384">Bei Brücken für die universelle Windows-Plattform handelt es sich um Technologien für die UWP-Portierung Ihrer vorhandenen Apps oder Spiele.</span><span class="sxs-lookup"><span data-stu-id="dbf99-384">Universal Windows Platform Bridges are technologies that bring your existing app or game over to the UWP.</span></span> <span data-ttu-id="dbf99-385">Brücken eignen sich sehr gut für den schnellen Einstieg in die Entwicklung von UWP-Spielen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-385">Bridges are a great way to get a quick start on UWP game development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-386">UWP Brücken</span><span class="sxs-lookup"><span data-stu-id="dbf99-386">UWP bridges</span></span></td>
        <td><a href="https://dev.windows.com/bridges/"><span data-ttu-id="dbf99-387">Portieren Ihres Codes für Windows</span><span class="sxs-lookup"><span data-stu-id="dbf99-387">Bring your code to Windows</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-388">Windows-Brücke für iOS</span><span class="sxs-lookup"><span data-stu-id="dbf99-388">Windows Bridge for iOS</span></span></td>
        <td><a href="https://dev.windows.com/bridges/ios"><span data-ttu-id="dbf99-389">Portieren Ihrer iOS-Apps für Windows</span><span class="sxs-lookup"><span data-stu-id="dbf99-389">Bring your iOS apps to Windows</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-390">Windows-Brücke für Desktop-Anwendungen (.NET und Win32)</span><span class="sxs-lookup"><span data-stu-id="dbf99-390">Windows Bridge for desktop applications (.NET and Win32)</span></span></td>
        <td><a href="https://developer.microsoft.com/windows/bridges/desktop"><span data-ttu-id="dbf99-391">Konvertieren Ihrer Desktopanwendung in eine UWP-App</span><span class="sxs-lookup"><span data-stu-id="dbf99-391">Convert your desktop application to a UWP app</span></span></a></td>
    </tr>
</table>

#### <a name="playfab"></a><span data-ttu-id="dbf99-392">PlayFab</span><span class="sxs-lookup"><span data-stu-id="dbf99-392">PlayFab</span></span>

<span data-ttu-id="dbf99-393">PlayFab ist jetzt Teil von Microsoft Family und eine vollständige Back-End-Plattform für Live-Spiele und ein leistungsstarkes Mittel für die ersten Schritte unabhängiger Studios.</span><span class="sxs-lookup"><span data-stu-id="dbf99-393">Now part of the Microsoft family, PlayFab is a complete back-end platform for live games and a powerful way for independent studios to get started.</span></span> <span data-ttu-id="dbf99-394">Steigern Sie Umsatz, Engagement und Bindung – bei gleichzeitigen Kosteneinsparungen – mit Spieldiensten, Echtzeitanalysen und LiveOps.</span><span class="sxs-lookup"><span data-stu-id="dbf99-394">Boost revenue, engagement, and retention—while cutting costs—with game services, real-time analytics, and LiveOps.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-395">PlayFab</span><span class="sxs-lookup"><span data-stu-id="dbf99-395">PlayFab</span></span></td>
        <td><a href="https://playfab.com/"><span data-ttu-id="dbf99-396">Übersicht über Tools und Dienste</span><span class="sxs-lookup"><span data-stu-id="dbf99-396">Overview of tools and services</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-397">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="dbf99-397">Getting started</span></span></td>
        <td><a href="https://api.playfab.com/docs/general-getting-started"><span data-ttu-id="dbf99-398">Generelles Handbuch über erste Schritte</span><span class="sxs-lookup"><span data-stu-id="dbf99-398">General getting started guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-399">Video-Lernprogrammserie</span><span class="sxs-lookup"><span data-stu-id="dbf99-399">Video tutorial series</span></span></td>
        <td><a href="https://www.youtube.com/watch?v=fGNpiqVi5xU&list=PLHCfyL7JpoPbLpA_oh_T5PKrfzPgCpPT5"><span data-ttu-id="dbf99-400">Serie von Demovideos über Kernsysteme von PlayFab</span><span class="sxs-lookup"><span data-stu-id="dbf99-400">Series of demo videos about PlayFab's core systems</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-401">Rezepte</span><span class="sxs-lookup"><span data-stu-id="dbf99-401">Recipes</span></span></td>
        <td><a href="https://api.playfab.com/docs/tutorials/recipes-index"><span data-ttu-id="dbf99-402">Beliebte Spielmechanismen und Designmusterbeispiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-402">Popular game mechanics and design pattern samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-403">Plattformen</span><span class="sxs-lookup"><span data-stu-id="dbf99-403">Platforms</span></span></td>
        <td><a href="https://api.playfab.com/platforms"><span data-ttu-id="dbf99-404">Spezielle Dokumentation für verschiedene Plattformen und Spielengines</span><span class="sxs-lookup"><span data-stu-id="dbf99-404">Specific documentation for various platforms and game engines</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-405">GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="dbf99-405">GitHub repo</span></span></td>
        <td><a href="https://github.com/PlayFab"><span data-ttu-id="dbf99-406">Hier erhalten Sie Skripts und SDKs für verschiedene Plattformen, einschließlich Android, iOS, Windows, Unity und Unreal.</span><span class="sxs-lookup"><span data-stu-id="dbf99-406">Get scripts and SDKs for various platforms including Android, iOS, Windows, Unity, and Unreal.</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-407">API-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="dbf99-407">API documentation</span></span></td>
        <td><a href="https://api.playfab.com/documentation/"><span data-ttu-id="dbf99-408">PlayFab-Dienst direkt über REST-ähnlichen Web-APIs</span><span class="sxs-lookup"><span data-stu-id="dbf99-408">Access PlayFab service directly via REST-like Web APIs</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-409">Foren</span><span class="sxs-lookup"><span data-stu-id="dbf99-409">Forums</span></span></td>
        <td><a href="https://community.playfab.com/index.html"><span data-ttu-id="dbf99-410">PlayFab-Foren</span><span class="sxs-lookup"><span data-stu-id="dbf99-410">PlayFab forums</span></span></a></td>
    </tr>
</table>
 

#### <a name="unity"></a><span data-ttu-id="dbf99-411">Unity</span><span class="sxs-lookup"><span data-stu-id="dbf99-411">Unity</span></span>

<span data-ttu-id="dbf99-412">Unity bietet eine Plattform zum Erstellen ansprechender 2D, 3D, VR, und AR-Spiele und Apps.</span><span class="sxs-lookup"><span data-stu-id="dbf99-412">Unity offers a platform for creating beautiful and engaging 2D, 3D, VR, and AR games and apps.</span></span> <span data-ttu-id="dbf99-413">Es ermöglicht Ihnen, Ihre kreative Vision schnell umzusetzen und Ihre Inhalte auf nahezu alle Medien oder Geräten anzubieten.</span><span class="sxs-lookup"><span data-stu-id="dbf99-413">It enables you to realize your creative vision fast and delivers your content to virtually any media or device.</span></span>

<span data-ttu-id="dbf99-414">Unity unterstützt ab Unity5.4 die Direct3D12-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-414">Beginning with Unity 5.4, Unity supports Direct3D 12 development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-415">Die Unity-Spielengine</span><span class="sxs-lookup"><span data-stu-id="dbf99-415">The Unity game engine</span></span></td>
        <td><a href="http://unity3d.com/"><span data-ttu-id="dbf99-416">Unity – Spielengine</span><span class="sxs-lookup"><span data-stu-id="dbf99-416">Unity - Game Engine</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-417">Unity herunterladen</span><span class="sxs-lookup"><span data-stu-id="dbf99-417">Get Unity</span></span></td>
        <td><a href="http://unity3d.com/get-unity"><span data-ttu-id="dbf99-418">Unity herunterladen</span><span class="sxs-lookup"><span data-stu-id="dbf99-418">Get Unity</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-419">Unity-Dokumentation für Windows</span><span class="sxs-lookup"><span data-stu-id="dbf99-419">Unity documentation for Windows</span></span></td>
        <td><a href="http://docs.unity3d.com/Manual/Windows.html"><span data-ttu-id="dbf99-420">Unity-Handbuch/Windows</span><span class="sxs-lookup"><span data-stu-id="dbf99-420">Unity Manual / Windows</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-421">Fügen Sie mit PlayFab LiveOps hinzu</span><span class="sxs-lookup"><span data-stu-id="dbf99-421">Add LiveOps using PlayFab</span></span></td>
        <td><a href="https://api.playfab.com/docs/getting-started/unity-getting-started"><span data-ttu-id="dbf99-422">Erste Schritte – führen Sie Ihren ersten PlayFab-API-Aufruf aus Ihrem Unity-Spiel durch</span><span class="sxs-lookup"><span data-stu-id="dbf99-422">Getting started - Make your first PlayFab API call from your Unity game</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-423">Wie fügen Sie Ihrem Spiel mit dem interaktiven Mixer Interaktivität hinzu</span><span class="sxs-lookup"><span data-stu-id="dbf99-423">How to add interactivity to your game using Mixer Interactive</span></span></td>
        <td><a href="https://github.com/mixer/interactive-unity-plugin/wiki/Getting-started"><span data-ttu-id="dbf99-424">Leitfaden für erste Schritte</span><span class="sxs-lookup"><span data-stu-id="dbf99-424">Getting started guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-425">Mixer SDK für Unity</span><span class="sxs-lookup"><span data-stu-id="dbf99-425">Mixer SDK for Unity</span></span></td>
        <td><a href="https://www.assetstore.unity3d.com/en/#!/content/88585"><span data-ttu-id="dbf99-426">Mixer Unity-Plug-In</span><span class="sxs-lookup"><span data-stu-id="dbf99-426">Mixer Unity plugin</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-427">Vollständige Referenzdokumentation für Mixer SDK für Unity</span><span class="sxs-lookup"><span data-stu-id="dbf99-427">Mixer SDK for Unity reference documentation</span></span></td>
        <td><a href="https://dev.mixer.com/reference/interactive/csharp/index.html"><span data-ttu-id="dbf99-428">API-Referenz für das Mixer Unity-Plug-In</span><span class="sxs-lookup"><span data-stu-id="dbf99-428">API reference for Mixer Unity plugin</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-429">Veröffentlichen eines Unity-Spiels im Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="dbf99-429">Publish your Unity game to Microsoft Store</span></span></td>
        <td><a href="https://unity3d.com/partners/microsoft/porting-guides"><span data-ttu-id="dbf99-430">Portierungsleitfaden</span><span class="sxs-lookup"><span data-stu-id="dbf99-430">Porting guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-431">Problembehandlung bei fehlenden Assemblyverweisen im Zusammenhang mit .NET APIs</span><span class="sxs-lookup"><span data-stu-id="dbf99-431">Troubleshooting missing assembly references related to .NET APIs</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/gaming/missing-dot-net-apis-in-unity-and-uwp"><span data-ttu-id="dbf99-432">Fehlende .NET-APIs in Unity und UWP</span><span class="sxs-lookup"><span data-stu-id="dbf99-432">Missing .NET APIs in Unity and UWP</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-433">Veröffentlichen eines Unity-Spiels als UWP-App (Universelle Windows-Plattform) (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-433">Publish your Unity game as a Universal Windows Platform app (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app"><span data-ttu-id="dbf99-434">So veröffentlichen Sie Ihr Unity-Spiel als UWP-App</span><span class="sxs-lookup"><span data-stu-id="dbf99-434">How to publish your Unity game as a UWP app</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-435">Verwenden von Unity zum Erstellen von Windows-Spielen und -Apps (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-435">Use Unity to make Windows games and apps (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Blogs/One-Dev-Minute/Making-games-and-apps-with-Unity"><span data-ttu-id="dbf99-436">Erstellen von Windows-Spielen und -Apps mit Unity</span><span class="sxs-lookup"><span data-stu-id="dbf99-436">Making Windows games and apps with Unity</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-437">Unity-Spielentwicklung mit Visual Studio (Videoserie)</span><span class="sxs-lookup"><span data-stu-id="dbf99-437">Unity game development using Visual Studio (video series)</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=722359"><span data-ttu-id="dbf99-438">Verwendung von Unity mit Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="dbf99-438">Using Unity with Visual Studio 2015</span></span></a></td>
    </tr>
</table>
 

#### <a name="havok"></a><span data-ttu-id="dbf99-439">Havok</span><span class="sxs-lookup"><span data-stu-id="dbf99-439">Havok</span></span>

<span data-ttu-id="dbf99-440">Mit den Tools und Technologien aus der modular aufgebauten Suite von Havok erreichen Spieleentwickler eine noch nie dagewesene Interaktivität und Immersion.</span><span class="sxs-lookup"><span data-stu-id="dbf99-440">Havok’s modular suite of tools and technologies help game creators reach new levels of interactivity and immersion.</span></span> <span data-ttu-id="dbf99-441">Havok bietet eine äußerst realistische Physik, interaktive Simulationen und beeindruckende Effekte.</span><span class="sxs-lookup"><span data-stu-id="dbf99-441">Havok enables highly realistic physics, interactive simulations, and stunning cinematics.</span></span> <span data-ttu-id="dbf99-442">Version 2015.1 und höher unterstützen UWP in Visual Studio2015 auf x86-, 64-Bit- und ARM-Plattformen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-442">Version 2015.1 and higher officially supports UWP in Visual Studio 2015 on x86, 64-bit, and ARM.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-443">Havok-Website</span><span class="sxs-lookup"><span data-stu-id="dbf99-443">Havok website</span></span></td>
        <td><a href="http://www.havok.com/"><span data-ttu-id="dbf99-444">Havok</span><span class="sxs-lookup"><span data-stu-id="dbf99-444">Havok</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-445">Havok-Toolsuite</span><span class="sxs-lookup"><span data-stu-id="dbf99-445">Havok tool suite</span></span></td>
        <td><a href="http://www.havok.com/products/"><span data-ttu-id="dbf99-446">Havok-Produktübersicht</span><span class="sxs-lookup"><span data-stu-id="dbf99-446">Havok Product Overview</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-447">Havok-Supportforen</span><span class="sxs-lookup"><span data-stu-id="dbf99-447">Havok support forums</span></span></td>
        <td><a href="http://support.havok.com"><span data-ttu-id="dbf99-448">Havok</span><span class="sxs-lookup"><span data-stu-id="dbf99-448">Havok</span></span></a></td>
    </tr>
</table>
 

#### <a name="monogame"></a><span data-ttu-id="dbf99-449">MonoGame</span><span class="sxs-lookup"><span data-stu-id="dbf99-449">MonoGame</span></span>

<span data-ttu-id="dbf99-450">MonoGame ist ein plattformübergreifendes Open-Source-Framework für die Spieleentwicklung, das ursprünglich auf XNA Framework 4.0 von Microsoft basierte.</span><span class="sxs-lookup"><span data-stu-id="dbf99-450">MonoGame is an open source, cross-platform game development framework originally based on Microsoft's XNA Framework 4.0.</span></span> <span data-ttu-id="dbf99-451">MonoGame unterstützt derzeit Windows, Windows Phone und Xbox sowie Linux, macOS, iOS, Android und verschiedene andere Plattformen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-451">Monogame currently supports Windows, Windows Phone, and Xbox, as well as Linux, macOS, iOS, Android, and several other platforms.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-452">MonoGame</span><span class="sxs-lookup"><span data-stu-id="dbf99-452">MonoGame</span></span></td>
        <td><a href="http://www.monogame.net"><span data-ttu-id="dbf99-453">MonoGame-Website</span><span class="sxs-lookup"><span data-stu-id="dbf99-453">MonoGame website</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-454">MonoGame-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="dbf99-454">MonoGame Documentation</span></span></td>
        <td><a href="http://www.monogame.net/documentation/"><span data-ttu-id="dbf99-455">MonoGame-Dokumentation (aktuell)</span><span class="sxs-lookup"><span data-stu-id="dbf99-455">MonoGame Documentation (latest)</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-456">MonoGame-Downloads</span><span class="sxs-lookup"><span data-stu-id="dbf99-456">Monogame Downloads</span></span></td>
        <td><span data-ttu-id="dbf99-457"><a href="http://www.monogame.net/downloads/">Laden Sie Versionen, Entwicklungsbuilds und Quellcode</a> von der MonoGame-Website herunter, oder <a href="https://www.nuget.org/profiles/MonoGame">rufen Sie die neueste Version über NuGet ab</a>.</span><span class="sxs-lookup"><span data-stu-id="dbf99-457"><a href="http://www.monogame.net/downloads/">Download releases, development builds, and source code</a> from the MonoGame website, or <a href="https://www.nuget.org/profiles/MonoGame">get the latest release via NuGet</a>.</span></span>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-458">Beispiel für ein MonoGame 2D UWP-Spiel</span><span class="sxs-lookup"><span data-stu-id="dbf99-458">MonoGame 2D UWP game sample</span></span></td>
        <td><a href="../get-started/get-started-tutorial-game-mg2d.md"><span data-ttu-id="dbf99-459">Erstellen eines UWP-Spiels in MonoGame-2D</span><span class="sxs-lookup"><span data-stu-id="dbf99-459">Create a UWP game in MonoGame 2D</span></span></a></td>
    </tr>    
</table>


#### <a name="cocos2d"></a><span data-ttu-id="dbf99-460">Cocos2d</span><span class="sxs-lookup"><span data-stu-id="dbf99-460">Cocos2d</span></span>

<span data-ttu-id="dbf99-461">Cocos2d-X ist eine plattformübergreifende Suite mit Open-Source-Spieleentwicklungsengine und Tools, die die Erstellung von UWP-Spielen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-461">Cocos2d-x is a cross-platform open source game development engine and tools suite that supports building UWP games.</span></span> <span data-ttu-id="dbf99-462">Ab Version3 werden auch 3D-Features hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-462">Beginning with version 3, 3D features are being added as well.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-463">Cocos2d-X</span><span class="sxs-lookup"><span data-stu-id="dbf99-463">Cocos2d-x</span></span></td>
        <td><a href="http://www.cocos2d-x.org/"><span data-ttu-id="dbf99-464">Was ist Cocos2d-X?</span><span class="sxs-lookup"><span data-stu-id="dbf99-464">What is Cocos2d-x?</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-465">Cocos2d-X-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="dbf99-465">Cocos2d-x programmer's guide</span></span></td>
        <td><a href="http://www.cocos2d-x.org/programmersguide/"><span data-ttu-id="dbf99-466">Cocos2d-X-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="dbf99-466">Cocos2d-x Programmers Guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-467">Cocos2d-X unter Windows10 (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="dbf99-467">Cocos2d-x on Windows 10 (blog post)</span></span></td>
        <td><a href="https://blogs.windows.com/buildingapps/2015/06/15/running-cocos2d-x-on-windows-10/"><span data-ttu-id="dbf99-468">Ausführen von Cocos2d-X unter Windows10</span><span class="sxs-lookup"><span data-stu-id="dbf99-468">Running Cocos2d-x on Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-469">Fügen Sie mit PlayFab LiveOps hinzu</span><span class="sxs-lookup"><span data-stu-id="dbf99-469">Add LiveOps using PlayFab</span></span></td>
        <td><a href="https://api.playfab.com/docs/getting-started/cocos2d-x-getting-started-guide"><span data-ttu-id="dbf99-470">Erste Schritte – führen Sie Ihren ersten PlayFab-API-Aufruf aus Ihrem Cocos2d-Spiel durch</span><span class="sxs-lookup"><span data-stu-id="dbf99-470">Getting started - Make your first PlayFab API call from your Cocos2d game</span></span></a></td>
    </tr>
</table>


#### <a name="unreal-engine"></a><span data-ttu-id="dbf99-471">Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="dbf99-471">Unreal Engine</span></span>

<span data-ttu-id="dbf99-472">Unreal Engine4 ist eine umfassende, für alle Arten von Spielen und Entwicklern geeignete Suite mit Tools für die Spieleentwicklung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-472">Unreal Engine 4 is a complete suite of game development tools for all types of games and developers.</span></span> <span data-ttu-id="dbf99-473">Die Unreal Engine wird von Spieleentwicklern auf der ganzen Welt für besonders anspruchsvolle Konsolen- und PC-Spiele eingesetzt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-473">For the most demanding console and PC games, Unreal Engine is used by game developers worldwide.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-474">Übersicht über die Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="dbf99-474">Unreal Engine overview</span></span></td>
        <td><a href="https://www.unrealengine.com/what-is-unreal-engine-4"><span data-ttu-id="dbf99-475">Unreal Engine4</span><span class="sxs-lookup"><span data-stu-id="dbf99-475">Unreal Engine 4</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-476">Fügen Sie mit PlayFab LiveOps hinzu - C++</span><span class="sxs-lookup"><span data-stu-id="dbf99-476">Add LiveOps using PlayFab - C++</span></span></td>
        <td><a href="https://api.playfab.com/docs/getting-started/unreal-cpp-getting-started"><span data-ttu-id="dbf99-477">Erste Schritte – führen Sie Ihren ersten PlayFab-API-Aufruf aus Ihrem Unreal-Spiel durch</span><span class="sxs-lookup"><span data-stu-id="dbf99-477">Getting started - Make your first PlayFab API call from your Unreal game</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-478">Fügen Sie mit PlayFab LiveOps hinzu - Entwürfe</span><span class="sxs-lookup"><span data-stu-id="dbf99-478">Add LiveOps using PlayFab - Blueprints</span></span></td>
        <td><a href="https://api.playfab.com/docs/getting-started/unreal-blueprints-getting-started"><span data-ttu-id="dbf99-479">Erste Schritte – führen Sie Ihren ersten PlayFab-API-Aufruf aus Ihrem Unreal-Spiel durch</span><span class="sxs-lookup"><span data-stu-id="dbf99-479">Getting started - Make your first PlayFab API call from your Unreal game</span></span></a></td>
    </tr>
</table>

#### <a name="babylonjs"></a><span data-ttu-id="dbf99-480">BabylonJS</span><span class="sxs-lookup"><span data-stu-id="dbf99-480">BabylonJS</span></span>

<span data-ttu-id="dbf99-481">BabylonJS ist ein vollständiges JavaScript-Framework für die Erstellung von 3D-Spielen mit HTML5, WebGL, WebVR und Web-Audio.</span><span class="sxs-lookup"><span data-stu-id="dbf99-481">BabylonJS is a complete JavaScript framework for building 3D games with HTML5, WebGL, WebVR, and Web Audio.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-482">BabylonJS</span><span class="sxs-lookup"><span data-stu-id="dbf99-482">BabylonJS</span></span></td>
        <td><a href="http://www.babylonjs.com/"><span data-ttu-id="dbf99-483">BabylonJS</span><span class="sxs-lookup"><span data-stu-id="dbf99-483">BabylonJS</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-484">WebGL-3D mit HTML5 und BabylonJS (Videoserie)</span><span class="sxs-lookup"><span data-stu-id="dbf99-484">WebGL 3D with HTML5 and BabylonJS (video series)</span></span></td>
        <td><a href="https://channel9.msdn.com/Series/Introduction-to-WebGL-3D-with-HTML5-and-Babylonjs/01"><span data-ttu-id="dbf99-485">Learning WebGL 3D- und BabylonJS</span><span class="sxs-lookup"><span data-stu-id="dbf99-485">Learning WebGL 3D and BabylonJS</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-486">Erstellen eines plattformübergreifenden WebGL-Spiels mit BabylonJS</span><span class="sxs-lookup"><span data-stu-id="dbf99-486">Building a cross-platform WebGL game with BabylonJS</span></span></td>
        <td><a href="https://www.smashingmagazine.com/2016/07/babylon-js-building-sponza-a-cross-platform-webgl-game/"><span data-ttu-id="dbf99-487">Verwenden von BabylonJS zur Entwicklung eines plattformübergreifenden Spiels</span><span class="sxs-lookup"><span data-stu-id="dbf99-487">Use BabylonJS to develop a cross-platform game</span></span></a></td>
    </tr>    
</table>

### <a name="porting-your-game"></a><span data-ttu-id="dbf99-488">Portieren Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="dbf99-488">Porting your game</span></span>

<span data-ttu-id="dbf99-489">Entwicklern, die bereits über ein Spiel verfügen, stehen zahlreiche Ressourcen und Handbücher für eine schnelle UWP-Portierung ihres Spiels zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-489">If you have an existing game, there are many resources and guides available to help you quickly bring your game to the UWP.</span></span> <span data-ttu-id="dbf99-490">Als Starthilfe bei der Portierung empfiehlt sich unter Umständen die Verwendung einer [Brücke für die universelle Windows-Plattform](#universal-windows-platform-bridges).</span><span class="sxs-lookup"><span data-stu-id="dbf99-490">To jumpstart your porting efforts, you might also consider using a [Universal Windows Platform Bridge](#universal-windows-platform-bridges).</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-491">Portieren einer Windows8-App zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="dbf99-491">Porting a Windows 8 app to a Universal Windows Platform app</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt238322"><span data-ttu-id="dbf99-492">Wechsel von Windows-Runtime 8.x zu UWP</span><span class="sxs-lookup"><span data-stu-id="dbf99-492">Move from Windows Runtime 8.x to UWP</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-493">Portieren einer Windows 8-App zu einer UWP-App (Universelle Windows-Plattform) (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-493">Porting a Windows 8 app to a Universal Windows Platform app (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Series/A-Developers-Guide-to-Windows-10/21"><span data-ttu-id="dbf99-494">Portieren von Windows 8.1-Apps zu Windows 10</span><span class="sxs-lookup"><span data-stu-id="dbf99-494">Porting 8.1 Apps to Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-495">Portieren einer iOS-App zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="dbf99-495">Porting an iOS app to a Universal Windows Platform app</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt238320"><span data-ttu-id="dbf99-496">Wechsel von iOS zu UWP</span><span class="sxs-lookup"><span data-stu-id="dbf99-496">Move from iOS to UWP</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-497">Portieren einer Silverlight-App zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="dbf99-497">Porting a Silverlight app to a Universal Windows Platform app</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt238323"><span data-ttu-id="dbf99-498">Wechsel von Windows Phone Silverlight zu UWP</span><span class="sxs-lookup"><span data-stu-id="dbf99-498">Move from Windows Phone Silverlight to UWP</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-499">Portieren von XAML oder Silverlight zu einer UWP-App (Universelle Windows-Plattform) (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-499">Porting from XAML or Silverlight to a Universal Windows Platform app (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/Build/2015/3-741"><span data-ttu-id="dbf99-500">Portieren einer App von XAML oder Silverlight zu Windows 10</span><span class="sxs-lookup"><span data-stu-id="dbf99-500">Porting an App from XAML or Silverlight to Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-501">Portieren eines Xbox-Spiels zu einer UWP-App (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="dbf99-501">Porting an Xbox game to a Universal Windows Platform app</span></span></td>
        <td><a href="https://developer.xboxlive.com/en-us/platform/development/education/Documents/Porting%20from%20Xbox%20One%20to%20Windows%2010.aspx"><span data-ttu-id="dbf99-502">Portieren von Xbox One zu Windows 10 (UWP)</span><span class="sxs-lookup"><span data-stu-id="dbf99-502">Porting from Xbox One to Windows 10 UWP</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-503">Portieren von DirectX 9 zu DirectX 11</span><span class="sxs-lookup"><span data-stu-id="dbf99-503">Porting from DirectX 9 to DirectX 11</span></span></td>
        <td><a href="porting-your-directx-9-game-to-windows-store.md"><span data-ttu-id="dbf99-504">Portieren von DirectX9 zur universellen Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="dbf99-504">Port from DirectX 9 to Universal Windows Platform (UWP)</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-505">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="dbf99-505">Porting from Direct3D 11 to Direct3D 12</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt431709"><span data-ttu-id="dbf99-506">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="dbf99-506">Porting from Direct3D 11 to Direct3D 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-507">Portieren von OpenGLES zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="dbf99-507">Porting from OpenGL ES to Direct3D 11</span></span></td>
        <td><a href="port-from-opengl-es-2-0-to-directx-11-1.md"><span data-ttu-id="dbf99-508">Portieren von OpenGLES2.0 zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="dbf99-508">Port from OpenGL ES 2.0 to Direct3D 11</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-509">OpenGLES2.0 zu Direct3D11 mit ANGLE</span><span class="sxs-lookup"><span data-stu-id="dbf99-509">OpenGL ES to Direct3D 11 using ANGLE</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/p/?linkid=618387"><span data-ttu-id="dbf99-510">ANGLE</span><span class="sxs-lookup"><span data-stu-id="dbf99-510">ANGLE</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-511">Entsprechungen für die klassische Windows-API in der UWP</span><span class="sxs-lookup"><span data-stu-id="dbf99-511">Classic Windows API equivalents in the UWP</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/hh464945"><span data-ttu-id="dbf99-512">Alternativen zu Windows-APIs in Apps für die Universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="dbf99-512">Alternatives to Windows APIs in Universal Windows Platform (UWP) apps</span></span></a></td>
    </tr>
</table>


## <a name="prototype-and-design"></a><span data-ttu-id="dbf99-513">Prototyp und Design</span><span class="sxs-lookup"><span data-stu-id="dbf99-513">Prototype and design</span></span>


<span data-ttu-id="dbf99-514">Nachdem Sie sich entschieden haben, welche Art von Spiel Sie entwickeln und welche Tools und Grafiktechnologie Sie dabei verwenden möchten, können Sie sich der Gestaltung zuwenden und einen Prototyp entwickeln.</span><span class="sxs-lookup"><span data-stu-id="dbf99-514">Now that you've decided the type of game you want to create and the tools and graphics technology you'll use to build it, you're ready to get started with the design and prototype.</span></span> <span data-ttu-id="dbf99-515">Da es sich bei Ihrem Spiel im Grunde um eine UWP-App (Universelle Windows-Plattform) handelt, beginnen Sie dort.</span><span class="sxs-lookup"><span data-stu-id="dbf99-515">At its core, your game is a Universal Windows Platform app, so that's where you'll begin.</span></span>

### <a name="introduction-to-the-universal-windows-platform-uwp"></a><span data-ttu-id="dbf99-516">Einführung in die universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="dbf99-516">Introduction to the Universal Windows Platform (UWP)</span></span>

<span data-ttu-id="dbf99-517">Windows10 führt die universelle Windows-Plattform (UWP) ein. Diese stellt eine gemeinsame, übergreifende API-Plattform für Windows10-Geräte bereit.</span><span class="sxs-lookup"><span data-stu-id="dbf99-517">Windows 10 introduces the Universal Windows Platform (UWP), which provides a common API platform across Windows 10 devices.</span></span> <span data-ttu-id="dbf99-518">Bei der UWP handelt es sich um eine Weiterentwicklung und Erweiterung des Windows-Runtime-Modells zu einem geschlossenen, einheitlichen Kern.</span><span class="sxs-lookup"><span data-stu-id="dbf99-518">UWP evolves and expands the Windows Runtime model and hones it into a cohesive, unified core.</span></span> <span data-ttu-id="dbf99-519">Für die UWP entwickelte Spiele können WinRT-APIs aufrufen, die bei allen Geräten vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="dbf99-519">Games that target the UWP can call WinRT APIs that are common to all devices.</span></span> <span data-ttu-id="dbf99-520">Da die UWP eine garantierte API-Ebene bereitstellt, können Sie ein einzelnes App-Paket erstellen, das dann auf allen Windows10-Geräten installiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="dbf99-520">Because the UWP provides guaranteed API layers, you can choose to create a single app package that will install across Windows 10 devices.</span></span> <span data-ttu-id="dbf99-521">Bei Bedarf kann Ihr Spiel natürlich auch weiterhin spezifische APIs der Geräte aufrufen, auf denen das Spiel ausgeführt wird – etwa einige klassische Windows-APIs von Win32 und .NET.</span><span class="sxs-lookup"><span data-stu-id="dbf99-521">And if you want to, your game can still call APIs (including some classic Windows APIs from Win32 and .NET) that are specific to the devices your game runs on.</span></span>

<span data-ttu-id="dbf99-522">Im Anschluss finden Sie praktische Handbücher, die sich ausführlich mit UWP-Apps (Universelle Windows-Plattform) auseinandersetzen und hilfreiche Erkenntnisse zur Plattform liefern.</span><span class="sxs-lookup"><span data-stu-id="dbf99-522">The following are excellent guides that discuss the Universal Windows Platform apps in detail, and are recommended reading to help you understand the platform.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-523">Einführung in UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="dbf99-523">Introduction to Universal Windows Platform apps</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/dn726767"><span data-ttu-id="dbf99-524">Was ist eine UWP-App (Universelle Windows-Plattform)?</span><span class="sxs-lookup"><span data-stu-id="dbf99-524">What's a Universal Windows Platform app?</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-525">Übersicht über die UWP</span><span class="sxs-lookup"><span data-stu-id="dbf99-525">Overview of the UWP</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/dn894631"><span data-ttu-id="dbf99-526">Anleitung für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-526">Guide to UWP apps</span></span></a></td>
    </tr>
</table>
 

### <a name="getting-started-with-uwp-development"></a><span data-ttu-id="dbf99-527">Erste Schritte bei der UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="dbf99-527">Getting started with UWP development</span></span>

<span data-ttu-id="dbf99-528">Die Vorbereitung auf die Entwicklung einer UWP-App (Universelle Windows-Plattform) ist ganz einfach und im Handumdrehen erledigt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-528">Getting set up and ready to develop a Universal Windows Platform app is quick and easy.</span></span> <span data-ttu-id="dbf99-529">Die erforderlichen Schritte werden in den folgenden Handbüchern erläutert:</span><span class="sxs-lookup"><span data-stu-id="dbf99-529">The following guides take you through the process step-by-step.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-530">Erste Schritte bei der UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="dbf99-530">Getting started with UWP development</span></span></td>
        <td><a href="https://dev.windows.com/getstarted"><span data-ttu-id="dbf99-531">Erste Schritte mit Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-531">Get started with Windows apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-532">Vorbereitung auf die UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="dbf99-532">Getting set up for UWP development</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/dn726766"><span data-ttu-id="dbf99-533">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="dbf99-533">Get set up</span></span></a></td>
    </tr>
</table>

<span data-ttu-id="dbf99-534">Wenn Sie noch keine Erfahrungen mit der UWP-Programmierung haben und die Verwendung von XAML in Ihrem Spiel in Betracht ziehen (siehe [Auswählen von Grafiktechnologie und Programmiersprache](#choosing-your-graphics-technology-and-programming-language)), ist die Videoserie [Windows10-Entwicklung für Neueinsteiger](https://channel9.msdn.com/Series/Windows-10-development-for-absolute-beginners) ein guter Ausgangspunkt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-534">If you're an "absolute beginner" to UWP programming, and are considering using XAML in your game (see [Choosing your graphics technology and programming language](#choosing-your-graphics-technology-and-programming-language)), the [Windows 10 development for absolute beginners](https://channel9.msdn.com/Series/Windows-10-development-for-absolute-beginners) video series is a good place to start.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-535">Einsteigerhandbuch für die Windows10-Entwicklung mit XAML (Videoserie)</span><span class="sxs-lookup"><span data-stu-id="dbf99-535">Beginners guide to Windows 10 development with XAML (Video series)</span></span></td>
        <td><a href="https://channel9.msdn.com/Series/Windows-10-development-for-absolute-beginners"><span data-ttu-id="dbf99-536">Windows10-Entwicklung für Neueinsteiger</span><span class="sxs-lookup"><span data-stu-id="dbf99-536">Windows 10 development for absolute beginners</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-537">Ankündigung der Windows10-Neueinsteigerserie mit XAML (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="dbf99-537">Announcing the Windows 10 absolute beginners series using XAML (blog post)</span></span></td>
        <td><a href="http://blogs.windows.com/buildingapps/2015/09/30/windows-10-development-for-absolute-beginners/"><span data-ttu-id="dbf99-538">Windows10-Entwicklung für Neueinsteiger</span><span class="sxs-lookup"><span data-stu-id="dbf99-538">Windows 10 development for absolute beginners</span></span></a></td>
    </tr>
</table>

### <a name="uwp-development-concepts"></a><span data-ttu-id="dbf99-539">UWP-Entwicklungskonzepte</span><span class="sxs-lookup"><span data-stu-id="dbf99-539">UWP development concepts</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-540">Übersicht über die Entwicklung von UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="dbf99-540">Overview of Universal Windows Platform app development</span></span></td>
        <td><a href="https://dev.windows.com/develop"><span data-ttu-id="dbf99-541">Entwickeln von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-541">Develop Windows apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-542">Übersicht über die Netzwerkprogrammierung der UWP</span><span class="sxs-lookup"><span data-stu-id="dbf99-542">Overview of network programming in the UWP</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt280378"><span data-ttu-id="dbf99-543">Netzwerk und Webdienste</span><span class="sxs-lookup"><span data-stu-id="dbf99-543">Networking and web services</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-544">Verwenden von „Windows.Web.HTTP“ und „Windows.Networking.Sockets“ in Spielen</span><span class="sxs-lookup"><span data-stu-id="dbf99-544">Using Windows.Web.HTTP and Windows.Networking.Sockets in games</span></span></td>
        <td><a href="work-with-networking-in-your-directx-game.md"><span data-ttu-id="dbf99-545">Netzwerkfunktionen für Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-545">Networking for games</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-546">Asynchrone Programmierkonzepte der UWP</span><span class="sxs-lookup"><span data-stu-id="dbf99-546">Asynchronous programming concepts in the UWP</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt187335"><span data-ttu-id="dbf99-547">Asynchrone Programmierung</span><span class="sxs-lookup"><span data-stu-id="dbf99-547">Asynchronous programming</span></span></a></td>
    </tr>
</table>

### <a name="windows-desktop-apisto-uwp"></a><span data-ttu-id="dbf99-548">Windows-Desktop APIsto UWP</span><span class="sxs-lookup"><span data-stu-id="dbf99-548">Windows Desktop APIsto UWP</span></span>

<span data-ttu-id="dbf99-549">Hier finden Sie einige Links, die Sie beim Wechsel von Windows-Desktop-Spielen zu UWP-Spielen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-549">These are some links to help you move your Windows desktop game to UWP.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-550">Verwenden Sie vorhandenen C++-Code für die UWP-Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="dbf99-550">Use existing C++ code for UWP game development</span></span></td>
        <td><a href="https://docs.microsoft.com/cpp/porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app"><span data-ttu-id="dbf99-551">Vorgehensweise: Verwenden von vorhandenem C++-Code in einer UWP-App</span><span class="sxs-lookup"><span data-stu-id="dbf99-551">How to: Use existing C++ code in a UWP app</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-552">UWP-APIs für Win32- und COM-APIs</span><span class="sxs-lookup"><span data-stu-id="dbf99-552">UWP APIs for Win32 and COM APIs</span></span></td>
        <td><a href="https://docs.microsoft.com/uwp/win32-and-com/win32-and-com-for-uwp-apps"><span data-ttu-id="dbf99-553">Win32- und COM-APIs für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-553">Win32 and COM APIs for UWP apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-554">Nicht unterstützte CRT-Funktionen in UWP</span><span class="sxs-lookup"><span data-stu-id="dbf99-554">Unsupported CRT functions in UWP</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/jj606124.aspx"><span data-ttu-id="dbf99-555">Nicht unterstützte CRT-Funktionen in Apps für die universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="dbf99-555">CRT functions not supported in Universal Windows Platform apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-556">Alternativen zu Windows-APIs</span><span class="sxs-lookup"><span data-stu-id="dbf99-556">Alternatives for Windows APIs</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt592894.aspx"><span data-ttu-id="dbf99-557">Alternativen zu Windows-APIs in Apps für die universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="dbf99-557">Alternatives to Windows APIs in Universal Windows Platform (UWP) apps</span></span></a></td>
    </tr>
</table>
 

### <a name="process-lifetime-management"></a><span data-ttu-id="dbf99-558">Prozesslebensdauer-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="dbf99-558">Process lifetime management</span></span>

<span data-ttu-id="dbf99-559">Prozesslebensdauer-Verwaltung (oder App-Lebenszyklus) beschreibt die verschiedenen Aktivierungszustände, die eine UWP-App (Universelle Windows-Plattform) durchlaufen kann.</span><span class="sxs-lookup"><span data-stu-id="dbf99-559">Process lifetime management, or app lifecyle, describes the various activation states that a Universal Windows Platform app can transition through.</span></span> <span data-ttu-id="dbf99-560">Ihr Spiel kann aktiviert, angehalten, fortgesetzt oder beendet werden und diese Zustände auf unterschiedliche Arten durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-560">Your game can be activated, suspended, resumed, or terminated, and can transition through those states in a variety of ways.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-561">Behandeln von App-Lebenszyklusübergängen</span><span class="sxs-lookup"><span data-stu-id="dbf99-561">Handling app lifecyle transitions</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt243287"><span data-ttu-id="dbf99-562">App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="dbf99-562">App lifecycle</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-563">Auslösen von App-Übergängen mithilfe von Microsoft Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dbf99-563">Using Microsoft Visual Studio to trigger app transitions</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/hh974425.aspx"><span data-ttu-id="dbf99-564">So wird's gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen für UWP-Apps in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dbf99-564">How to trigger suspend, resume, and background events for UWP apps in Visual Studio</span></span></a></td>
    </tr>
</table>
 

### <a name="designing-game-ux"></a><span data-ttu-id="dbf99-565">Gestalten der UX von Spielen</span><span class="sxs-lookup"><span data-stu-id="dbf99-565">Designing game UX</span></span>

<span data-ttu-id="dbf99-566">Großartigen Spielen liegt in der Regel ein kreatives Design zugrunde.</span><span class="sxs-lookup"><span data-stu-id="dbf99-566">The genesis of a great game is inspired design.</span></span>

<span data-ttu-id="dbf99-567">Spiele und Apps teilen sich zwar einige Benutzeroberflächenelemente und Designprinzipien, beim Spieldesign werden jedoch häufig ein ganz besonderer Look und ein einzigartiges Spielgefühl angestrebt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-567">Games share some common user interface elements and design principles with apps, but games often have a unique look, feel, and design goal for their user experience.</span></span> <span data-ttu-id="dbf99-568">Spiele sind erfolgreich, wenn in beiden Bereichen ein durchdachtes Design gewählt wird: Wann sollten Sie in Ihrem Spiel bewährte Benutzeroberflächenelemente verwenden, und wann sollten Sie davon abweichen und innovativ vorgehen?</span><span class="sxs-lookup"><span data-stu-id="dbf99-568">Games succeed when thoughtful design is applied to both aspects—when should your game use tested UX, and when should it diverge and innovate?</span></span> <span data-ttu-id="dbf99-569">Die Darstellungstechnologie, die Sie für das Spiel auswählen – DirectX, XAML, HTML5 oder eine beliebige Kombination –, wird sich auf die Implementierungsdetails auswirken. Die von Ihnen angewendeten Entwurfsprinzipien sind aber nicht von der jeweiligen Wahl abhängig.</span><span class="sxs-lookup"><span data-stu-id="dbf99-569">The presentation technology that you choose for your game—DirectX, XAML, HTML5, or some combination of the three—will influence implementation details, but the design principles you apply are largely independent of that choice.</span></span>

<span data-ttu-id="dbf99-570">Zusätzlich zum UX-Design müssen Sie sich auch mit dem Gameplay-Design auseinandersetzen, was unter anderem Aspekte wie Leveldesign, Pacing und Umgebungsdesign umfasst. Da es sich hierbei um eine ganz eigene Kunstform handelt, gehen wir in diesem Dokument nicht näher darauf ein, sondern überlassen diesen Bereich ganz Ihnen und Ihrem Team.</span><span class="sxs-lookup"><span data-stu-id="dbf99-570">Separately from UX design, gameplay design such as level design, pacing, world design, and other aspects is an art form of its own—one that's up to you and your team, and not covered in this development guide.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-571">UWP-Gestaltungsgrundlagen und -richtlinien</span><span class="sxs-lookup"><span data-stu-id="dbf99-571">UWP design basics and guidelines</span></span></td>
        <td><a href="https://dev.windows.com/design"><span data-ttu-id="dbf99-572">Gestalten von UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-572">Designing UWP apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-573">Gestalten für App-Lebenszykluszustände</span><span class="sxs-lookup"><span data-stu-id="dbf99-573">Designing for app lifecycle states</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/dn611862"><span data-ttu-id="dbf99-574">UX-Richtlinien für das Starten, Anhalten und Fortsetzen von Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-574">UX guidelines for launch, suspend, and resume</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-575">Entwerfen Sie Ihre UWP-App für Xbox One und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="dbf99-575">Design your UWP app for Xbox One and television screens</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/design/devices/designing-for-tv"><span data-ttu-id="dbf99-576">Entwerfen für Xbox und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="dbf99-576">Designing for Xbox and TV</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-577">Ausrichten auf verschiedene Geräteformfaktoren (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-577">Targeting multiple device form factors (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Designing-Games-for-a-Windows-Core-World"><span data-ttu-id="dbf99-578">Entwerfen von Spielen für eine WindowsCore-Welt</span><span class="sxs-lookup"><span data-stu-id="dbf99-578">Designing Games for a Windows Core World</span></span></a></td>
    </tr>   
</table>
 

#### <a name="color-guideline-and-palette"></a><span data-ttu-id="dbf99-579">Farbrichtlinie und -palette</span><span class="sxs-lookup"><span data-stu-id="dbf99-579">Color guideline and palette</span></span>

<span data-ttu-id="dbf99-580">Eine einheitliche Farbrichtlinie verbessert die Spielästhetik, vereinfacht die Navigation und ist ein wirksames Mittel, um Spieler über Menü- und HUD-Funktionen zu informieren.</span><span class="sxs-lookup"><span data-stu-id="dbf99-580">Following a consistent color guideline in your game improves aesthetics, aids navigation, and is a powerful tool to inform the player of menu and HUD functionality.</span></span> <span data-ttu-id="dbf99-581">Eine einheitliche Farbgestaltung von Spielelementen wie Warnungen, Schäden, Erfahrungspunkten und Erfolgen kann die Übersichtlichkeit der Benutzeroberfläche verbessern und explizite Beschriftungen überflüssig machen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-581">Consistent coloring of game elements like warnings, damage, XP, and achievements can lead to cleaner UI and reduce the need for explicit labels.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-582">Farbhandbuch</span><span class="sxs-lookup"><span data-stu-id="dbf99-582">Color guide</span></span></td>
        <td><a href="https://assets.windowsphone.com/499cd2be-64ed-4b05-a4f5-cd0c9ad3f6a3/101_BestPractices_Color_InvariantCulture_Default.zip"><span data-ttu-id="dbf99-583">Bewährte Methoden: Farbe</span><span class="sxs-lookup"><span data-stu-id="dbf99-583">Best Practices: Color</span></span></a></td>
    </tr>
</table>
 

#### <a name="typography"></a><span data-ttu-id="dbf99-584">Typografie</span><span class="sxs-lookup"><span data-stu-id="dbf99-584">Typography</span></span>

<span data-ttu-id="dbf99-585">Durch den angemessenen Einsatz von Typografie können Sie Ihr Spiel in vielerlei Hinsicht verbessern – etwa in Bezug auf UI-Layout, Navigation, Lesbarkeit, Atmosphäre und Spielerimmersion.</span><span class="sxs-lookup"><span data-stu-id="dbf99-585">The appropriate use of typography enhances many aspects of your game, including UI layout, navigation, readability, atmosphere, brand, and player immersion.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-586">Typografiehandbuch</span><span class="sxs-lookup"><span data-stu-id="dbf99-586">Typography guide</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=535007"><span data-ttu-id="dbf99-587">Bewährte Methoden: Typografie</span><span class="sxs-lookup"><span data-stu-id="dbf99-587">Best Practices: Typography</span></span></a></td>
    </tr>
</table>
 

#### <a name="ui-map"></a><span data-ttu-id="dbf99-588">UI-Zuordnung</span><span class="sxs-lookup"><span data-stu-id="dbf99-588">UI map</span></span>

<span data-ttu-id="dbf99-589">Bei einer UI-Zuordnung handelt es sich um eine Layoutübersicht über die Navigation und Menüs eines Spiels in Form eines Flussdiagramms.</span><span class="sxs-lookup"><span data-stu-id="dbf99-589">A UI map is a layout of game navigation and menus expressed as a flowchart.</span></span> <span data-ttu-id="dbf99-590">Die UI-Zuordnung verbessert die Nachvollziehbarkeit der Oberfläche und der Navigationspfade eines Spiels für alle Beteiligten und trägt zur frühzeitigen Erkennung potenzieller Probleme und Sackgassen bei.</span><span class="sxs-lookup"><span data-stu-id="dbf99-590">The UI map helps all involved stakeholders understand the game’s interface and navigation paths, and can expose potential roadblocks and dead ends early in the development cycle.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-591">Anleitung für die UI-Zuordnung</span><span class="sxs-lookup"><span data-stu-id="dbf99-591">UI map guide</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=535008"><span data-ttu-id="dbf99-592">Bewährte Methoden: UI-Zuordnung</span><span class="sxs-lookup"><span data-stu-id="dbf99-592">Best Practices: UI Map</span></span></a></td>
    </tr>
</table>

### <a name="game-audio"></a><span data-ttu-id="dbf99-593">Audio in Spielen</span><span class="sxs-lookup"><span data-stu-id="dbf99-593">Game audio</span></span>

<span data-ttu-id="dbf99-594">Anleitungen und Referenzen für die Implementierung von Audio in Spielen mit XAudio2, XAPO und Windows Sonic.</span><span class="sxs-lookup"><span data-stu-id="dbf99-594">Guides and references for implementing audio in games using XAudio2, XAPO, and Windows Sonic.</span></span> <span data-ttu-id="dbf99-595">XAudio2 ist eine Low-Level-Audio-API, die eine grundlegende Signalverarbeitung und -abmischung zum Entwickeln von Audiomodulen mit hoher Leistung für Spiele bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-595">XAudio2 is a low-level audio API that provides signal processing and mixing foundation for developing high performance audio engines.</span></span> <span data-ttu-id="dbf99-596">XAPO-API ermöglicht die Erstellung von plattformübergreifenden Audioverarbeitungsobjekten (XAPO) zur Verwendung in XAudio2 für Windows und Xbox.</span><span class="sxs-lookup"><span data-stu-id="dbf99-596">XAPO API allows the creation of cross-platform audio processing objects (XAPO) for use in XAudio2 on both Windows and Xbox.</span></span> <span data-ttu-id="dbf99-597">Mit der Windows Sonic Audiounterstützung können Sie Ihrem Spiel oder der Streaming-Media-Anwendung Dolby Atmos for Home Theater, Dolby Atmos for Headphones und Windows kopfbezogene Übertragungsfunktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-597">Windows Sonic audio support allows you to add Dolby Atmos for Home Theater, Dolby Atmos for Headphones, and Windows HRTF support to your game or streaming media application.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-598">XAudio2-APIs</span><span class="sxs-lookup"><span data-stu-id="dbf99-598">XAudio2 APIs</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx"><span data-ttu-id="dbf99-599">Programmieranleitung und API-Referenz für XAudio2</span><span class="sxs-lookup"><span data-stu-id="dbf99-599">Programming guide and API reference for XAudio2</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-600">Plattformübergreifende Audioverarbeitungsobjekte erstellen</span><span class="sxs-lookup"><span data-stu-id="dbf99-600">Create cross-platform audio processing objects</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx"><span data-ttu-id="dbf99-601">XAPO: Übersicht</span><span class="sxs-lookup"><span data-stu-id="dbf99-601">XAPO Overview</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-602">Einführung in Audio-Konzepte</span><span class="sxs-lookup"><span data-stu-id="dbf99-602">Intro to audio concepts</span></span></td>
        <td><a href="working-with-audio-in-your-directx-game.md"><span data-ttu-id="dbf99-603">Audio für Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-603">Audio for games</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-604">Übersicht über Windows Sonic</span><span class="sxs-lookup"><span data-stu-id="dbf99-604">Windows Sonic overview</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt807491.aspx"><span data-ttu-id="dbf99-605">Raumklang</span><span class="sxs-lookup"><span data-stu-id="dbf99-605">Spatial sound</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-606">Windows-Sonic Raumklang - Beispiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-606">Windows Sonic spatial sound samples</span></span></td>
        <td><a href="https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/UWPSamples/Audio"><span data-ttu-id="dbf99-607">Xbox Advanced Technology Group – Audiobeispiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-607">Xbox Advanced Technology Group audio samples</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-608">Hier erfahren Sie, wie Sie Windows Sonic in Ihre Spiele (Video) integrieren</span><span class="sxs-lookup"><span data-stu-id="dbf99-608">Learn how to integrate Windows Sonic into your games (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/GDC/GDC-2017/GDC2017-002"><span data-ttu-id="dbf99-609">Einführung in die räumliche Audiowiedergabe Funktionen für Xbox oder Windows</span><span class="sxs-lookup"><span data-stu-id="dbf99-609">Introducing Spatial Audio Capabilities for Xbox andWindows</span></span></a></td>
    </tr>
</table>

### <a name="directx-development"></a><span data-ttu-id="dbf99-610">DirectX-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="dbf99-610">DirectX development</span></span>

<span data-ttu-id="dbf99-611">Anleitungen und Referenzen für die Entwicklung von DirectX-Spielen</span><span class="sxs-lookup"><span data-stu-id="dbf99-611">Guides and references for DirectX game development.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-612">DirectX für die UWP-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="dbf99-612">DirectX for UWP development</span></span></td>
        <td><a href="directx-programming.md"><span data-ttu-id="dbf99-613">DirectX-Programmierung</span><span class="sxs-lookup"><span data-stu-id="dbf99-613">DirectX programming</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-614">Lernprogramm: Erstellen eines UWP-DirectX-Spiels</span><span class="sxs-lookup"><span data-stu-id="dbf99-614">Tutorial: How to create a UWP DirectX game</span></span></td>
        <td><a href="tutorial--create-your-first-uwp-directx-game.md"><span data-ttu-id="dbf99-615">Erstellen eines einfachen UWP-Spiels mit DirectX</span><span class="sxs-lookup"><span data-stu-id="dbf99-615">Create a simple UWP game with DirectX</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-616">DirectX-Interaktionen mit dem UWP-App-Modell</span><span class="sxs-lookup"><span data-stu-id="dbf99-616">DirectX interaction with the UWP app model</span></span></td>
        <td><a href="about-the-uwp-user-interface-and-directx.md"><span data-ttu-id="dbf99-617">Das App-Objekt und DirectX</span><span class="sxs-lookup"><span data-stu-id="dbf99-617">The app object and DirectX</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-618">Videos zu Grafiken und zur DirectX12-Entwicklung (YouTube-Kanal)</span><span class="sxs-lookup"><span data-stu-id="dbf99-618">Graphics and DirectX 12 development videos (YouTube channel)</span></span></td>
        <td><a href="https://www.youtube.com/channel/UCiaX2B8XiXR70jaN7NK-FpA"><span data-ttu-id="dbf99-619">Informationen zu Microsoft DirectX12 und Grafiken</span><span class="sxs-lookup"><span data-stu-id="dbf99-619">Microsoft DirectX 12 and Graphics Education</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-620">Übersichten und Referenzen zu DirectX</span><span class="sxs-lookup"><span data-stu-id="dbf99-620">DirectX overviews and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/ee663274"><span data-ttu-id="dbf99-621">DirectX-Grafiken und -Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-621">DirectX Graphics and Gaming</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-622">Direct3D12-Programmieranleitung und -referenz</span><span class="sxs-lookup"><span data-stu-id="dbf99-622">Direct3D 12 programming guide and reference</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn903821"><span data-ttu-id="dbf99-623">Direct3D12-Grafiken</span><span class="sxs-lookup"><span data-stu-id="dbf99-623">Direct3D 12 Graphics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-624">DirectX12-Grundlagen (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-624">DirectX 12 fundamentals (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Better-Power-Better-Performance-Your-Game-on-DirectX12"><span data-ttu-id="dbf99-625">Bessere Leistung und Performance: Ihr Spiel unter DirectX12</span><span class="sxs-lookup"><span data-stu-id="dbf99-625">Better Power, Better Performance: Your Game on DirectX 12</span></span></a></td>
    </tr>
</table>

#### <a name="learning-direct3d-12"></a><span data-ttu-id="dbf99-626">Erlernen von Direct3D2</span><span class="sxs-lookup"><span data-stu-id="dbf99-626">Learning Direct3D 12</span></span>

<span data-ttu-id="dbf99-627">Erfahren Sie mehr über die Änderungen in Direct3D12 und wie Sie mit der Programmierung in Direct3D12 beginnen können.</span><span class="sxs-lookup"><span data-stu-id="dbf99-627">Learn what changed in Direct3D 12 and how to start programming using Direct3D 12.</span></span> 

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-628">Einrichten der Programmierumgebung</span><span class="sxs-lookup"><span data-stu-id="dbf99-628">Set up programming environment</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn899120.aspx"><span data-ttu-id="dbf99-629">Einrichtung der Direct3D12 Programmierungsumgebung</span><span class="sxs-lookup"><span data-stu-id="dbf99-629">Direct3D 12 programming environment setup</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-630">Erstellen einer Grundkomponente</span><span class="sxs-lookup"><span data-stu-id="dbf99-630">How to create a basic component</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn859356.aspx"><span data-ttu-id="dbf99-631">Erstellen einer einfachen Direct3D12-Komponente</span><span class="sxs-lookup"><span data-stu-id="dbf99-631">Creating a basic Direct3D 12 component</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-632">Änderungen in Direct3D12</span><span class="sxs-lookup"><span data-stu-id="dbf99-632">Changes in Direct3D 12</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn899194.aspx"><span data-ttu-id="dbf99-633">Wichtige Änderungen bei der Migration von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="dbf99-633">Important changes migrating from Direct3D 11 to Direct3D 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-634">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="dbf99-634">How to port from Direct3D 11 to Direct3D 12</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt431709.aspx"><span data-ttu-id="dbf99-635">Portieren von Direct3D11 zu Direct3D12</span><span class="sxs-lookup"><span data-stu-id="dbf99-635">Porting from Direct3D 11 to Direct3D 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-636">Konzepte für die Ressourcenbindung (deckt Deskriptor, Deskriptortabelle, Deskriptorheap und Stammsignatur ab)</span><span class="sxs-lookup"><span data-stu-id="dbf99-636">Resource binding concepts (covering descriptor, descriptor table, descriptor heap, and root signature)</span></span> </td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn899206.aspx"><span data-ttu-id="dbf99-637">Ressourcenbindung in Direct3D12</span><span class="sxs-lookup"><span data-stu-id="dbf99-637">Resource binding in Direct3D 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-638">Verwalten des Arbeitsspeichers</span><span class="sxs-lookup"><span data-stu-id="dbf99-638">Managing memory</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn899198.aspx"><span data-ttu-id="dbf99-639">Arbeitsspeicherverwaltung in Direct3D12</span><span class="sxs-lookup"><span data-stu-id="dbf99-639">Memory management in Direct3D 12</span></span></a></td>
    </tr>
</table>
 

#### <a name="directx-tool-kit-and-libraries"></a><span data-ttu-id="dbf99-640">DirectX-Toolkit und -Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="dbf99-640">DirectX Tool Kit and libraries</span></span>

<span data-ttu-id="dbf99-641">Das DirectX-Toolkit, die DirectX-Texturverarbeitungsbibliothek, die DirectXMesh-Geometrieverarbeitungsbibliothek, die UVAtlas-Bibliothek und die DirectXMath-Bibliothek bieten textur-, gitter- und spritebezogene sowie weitere Hilfsprogrammfunktionen und Hilfsklassen für die DirectX-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-641">The DirectX Tool Kit, DirectX texture processing library, DirectXMesh geometry processing library, UVAtlas library, and DirectXMath library provide texture, mesh, sprite, and other utility functionality and helper classes for DirectX development.</span></span> <span data-ttu-id="dbf99-642">Diese Bibliotheken können Ihnen helfen, Entwicklungszeit und -aufwand einzusparen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-642">These libraries can help you save development time and effort.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-643">DirectX-Toolkit für DirectX11 herunterladen</span><span class="sxs-lookup"><span data-stu-id="dbf99-643">Get DirectX Tool Kit for DirectX 11</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=248929"><span data-ttu-id="dbf99-644">DirectXTK</span><span class="sxs-lookup"><span data-stu-id="dbf99-644">DirectXTK</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-645">DirectX-Toolkit für DirectX12 herunterladen</span><span class="sxs-lookup"><span data-stu-id="dbf99-645">Get DirectX Tool Kit for DirectX 12</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkID=615561"><span data-ttu-id="dbf99-646">DirectXTK12</span><span class="sxs-lookup"><span data-stu-id="dbf99-646">DirectXTK 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-647">DirectX-Texturverarbeitungsbibliothek herunterladen</span><span class="sxs-lookup"><span data-stu-id="dbf99-647">Get DirectX texture processing library</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=248926"><span data-ttu-id="dbf99-648">DirectXTex</span><span class="sxs-lookup"><span data-stu-id="dbf99-648">DirectXTex</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-649">DirectXMesh-Geometrieverarbeitungsbibliothek herunterladen</span><span class="sxs-lookup"><span data-stu-id="dbf99-649">Get DirectXMesh geometry processing library</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkID=324981"><span data-ttu-id="dbf99-650">DirectXMesh</span><span class="sxs-lookup"><span data-stu-id="dbf99-650">DirectXMesh</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-651">UVAtlas zum Erstellen und Verpacken des isoChart-Texturatlas herunterladen</span><span class="sxs-lookup"><span data-stu-id="dbf99-651">Get UVAtlas for creating and packing isochart texture atlas</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkID=512686"><span data-ttu-id="dbf99-652">UVAtlas</span><span class="sxs-lookup"><span data-stu-id="dbf99-652">UVAtlas</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-653">DirectXMath-Bibliothek herunterladen</span><span class="sxs-lookup"><span data-stu-id="dbf99-653">Get the DirectXMath library</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkID=615560"><span data-ttu-id="dbf99-654">DirectXMath</span><span class="sxs-lookup"><span data-stu-id="dbf99-654">DirectXMath</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-655">Direct3D12-Unterstützung im DirectXTK (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="dbf99-655">Direct3D12 support in the DirectXTK (blog post)</span></span></td>
        <td><a href="https://github.com/Microsoft/DirectXTK/issues/2"><span data-ttu-id="dbf99-656">Unterstützung für DirectX12</span><span class="sxs-lookup"><span data-stu-id="dbf99-656">Support for DirectX 12</span></span></a></td>
    </tr>
</table>

#### <a name="directx-resources-from-partners"></a><span data-ttu-id="dbf99-657">DirectX-Ressourcen von Partnern</span><span class="sxs-lookup"><span data-stu-id="dbf99-657">DirectX resources from partners</span></span>

<span data-ttu-id="dbf99-658">Dies sind einige zusätzliche DirectX-Dokumentationen, die von externen Partnern erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="dbf99-658">These are some additional DirectX documentation created by external partners.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-659">Nvidia: Empfohlene und nicht empfohlene Vorgehensweisen für DX12 (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="dbf99-659">Nvidia: DX12 Do's and Don'ts (blog post)</span></span> </td>
        <td><a href="https://developer.nvidia.com/dx12-dos-and-donts-updated"><span data-ttu-id="dbf99-660">DirectX12 auf Nvidia-GPUs</span><span class="sxs-lookup"><span data-stu-id="dbf99-660">DirectX 12 on Nvidia GPUs</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-661">Intel: Effizientes Rendering mit DirectX12</span><span class="sxs-lookup"><span data-stu-id="dbf99-661">Intel: Efficient rendering with DirectX 12</span></span></td>
        <td><a href="https://software.intel.com/sites/default/files/managed/4a/38/Efficient-Rendering-with-DirectX-12-on-Intel-Graphics.pdf"><span data-ttu-id="dbf99-662">DirectX12-Rendering auf Intel-Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="dbf99-662">DirectX 12 rendering on Intel Graphics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-663">Intel: Mehrfachadapterunterstützung in DirectX12</span><span class="sxs-lookup"><span data-stu-id="dbf99-663">Intel: Multi adapter support in DirectX 12</span></span></td>
        <td><a href="https://software.intel.com/articles/multi-adapter-support-in-directx-12"><span data-ttu-id="dbf99-664">Implementieren einer expliziten Mehrfachadapteranwendung mit DirectX12</span><span class="sxs-lookup"><span data-stu-id="dbf99-664">How to implement an explicit multi-adapter application using DirectX 12</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-665">Intel: DirectX12-Lernprogramm</span><span class="sxs-lookup"><span data-stu-id="dbf99-665">Intel: DirectX 12 tutorial</span></span></td>
        <td><a href="https://software.intel.com/articles/tutorial-migrating-your-apps-to-directx-12-part-1"><span data-ttu-id="dbf99-666">Gemeinsames Whitepaper von Intel, Suzhou Snail und Microsoft</span><span class="sxs-lookup"><span data-stu-id="dbf99-666">Collaborative white paper by Intel, Suzhou Snail and Microsoft</span></span></a></td>
    </tr>
</table>


## <a name="production"></a><span data-ttu-id="dbf99-667">Produktion</span><span class="sxs-lookup"><span data-stu-id="dbf99-667">Production</span></span>


<span data-ttu-id="dbf99-668">Ihr Studio ist jetzt vollständig eingebunden und beginnt mit dem Produktionszyklus, wobei die Arbeiten auf die einzelnen Teammitglieder aufgeteilt werden.</span><span class="sxs-lookup"><span data-stu-id="dbf99-668">Your studio is now fully engaged and moving into the production cycle, with work distributed throughout your team.</span></span> <span data-ttu-id="dbf99-669">Der Prototyp wird optimiert, überarbeitet und erweitert, um ein vollständiges Spiel zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="dbf99-669">You're polishing, refactoring, and extending the prototype to craft it into a full game.</span></span>

### <a name="notifications-and-live-tiles"></a><span data-ttu-id="dbf99-670">Benachrichtigungen und Live-Kacheln</span><span class="sxs-lookup"><span data-stu-id="dbf99-670">Notifications and live tiles</span></span>

<span data-ttu-id="dbf99-671">Ihr Spiel wird im Menü „Start“ durch eine Kachel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-671">A tile is your game's representation on the Start Menu.</span></span> <span data-ttu-id="dbf99-672">Über Kacheln und Benachrichtigungen können Sie das Interesse von Spielern wecken, auch wenn diese das Spiel gerade gar nicht spielen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-672">Tiles and notifications can drive player interest even when they aren't currently playing your game.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-673">Entwickeln von Kacheln und Signalen</span><span class="sxs-lookup"><span data-stu-id="dbf99-673">Developing tiles and badges</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt185606"><span data-ttu-id="dbf99-674">Kacheln, Badges und Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="dbf99-674">Tiles, badges, and notifications</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-675">Beispiel zur Veranschaulichung von Live-Kacheln und Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="dbf99-675">Sample illustrating live tiles and notifications</span></span></td>
        <td><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Notifications"><span data-ttu-id="dbf99-676">Benachrichtigungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="dbf99-676">Notifications sample</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-677">Vorlagen für adaptive Kacheln (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="dbf99-677">Adaptive tile templates (blog post)</span></span></td>
        <td><a href="http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/06/30/adaptive-tile-templates-schema-and-documentation.aspx"><span data-ttu-id="dbf99-678">Vorlagen für adaptive Kacheln – Schema und Dokumentation</span><span class="sxs-lookup"><span data-stu-id="dbf99-678">Adaptive Tile Templates - Schema and Documentation</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-679">Gestalten von Kacheln und Signalen</span><span class="sxs-lookup"><span data-stu-id="dbf99-679">Designing tiles and badges</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/hh465403"><span data-ttu-id="dbf99-680">Richtlinien für Kacheln und Signale</span><span class="sxs-lookup"><span data-stu-id="dbf99-680">Guidelines for tiles and badges</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-681">Windows10-App für die interaktive Entwicklung von Vorlagen für Live-Kacheln</span><span class="sxs-lookup"><span data-stu-id="dbf99-681">Windows 10 app for interactively developing live tile templates</span></span></td>
        <td><a href="https://www.microsoft.com/store/apps/9nblggh5xsl1"><span data-ttu-id="dbf99-682">Notifications Visualizer</span><span class="sxs-lookup"><span data-stu-id="dbf99-682">Notifications Visualizer</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-683">UWP-Erweiterung für die Generierung von Kacheln für Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dbf99-683">UWP Tile Generator extension for Visual Studio</span></span></td>
        <td><a href="https://visualstudiogallery.msdn.microsoft.com/09611e90-f3e8-44b7-9c83-18dba8275bb2"><span data-ttu-id="dbf99-684">Tool zum Erstellen aller erforderlichen Kacheln über ein einziges Image</span><span class="sxs-lookup"><span data-stu-id="dbf99-684">Tool for creating all required tiles using single image</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-685">UWP-Erweiterung für die Generierung von Kacheln für Visual Studio (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="dbf99-685">UWP Tile Generator extension for Visual Studio (blog post)</span></span></td>
        <td><a href="https://blogs.windows.com/buildingapps/2016/02/15/uwp-tile-generator-extension-for-visual-studio/"><span data-ttu-id="dbf99-686">Tipps zum Verwenden des UWP-Tools für die Generierung von Kacheln</span><span class="sxs-lookup"><span data-stu-id="dbf99-686">Tips on using the UWP Tile Generator tool</span></span></a></td>
    </tr>
</table>
 

### <a name="enable-in-app-product-add-on-purchases"></a><span data-ttu-id="dbf99-687">Aktivieren von in-app-Produktkäufen (Add-on)</span><span class="sxs-lookup"><span data-stu-id="dbf99-687">Enable in-app product (add-on) purchases</span></span>

<span data-ttu-id="dbf99-688">Ein Add-on (in-app-Produkt) ist es sich um einen zusätzlichen Artikel, dass Spieler in-Game-erwerben können.</span><span class="sxs-lookup"><span data-stu-id="dbf99-688">An add-on (in-app product) is a supplementary item that players can purchase in-game.</span></span> <span data-ttu-id="dbf99-689">Add-Ons sind spiellevels, Elemente und alles andere, die Ihre Spieler interessant sein könnte.</span><span class="sxs-lookup"><span data-stu-id="dbf99-689">Add-ons can be game levels, items, or anything else that your players might enjoy.</span></span> <span data-ttu-id="dbf99-690">Entsprechend verwendet, können-Add-Ons Umsätze generieren und gleichzeitig das Spielerlebnis verbessern.</span><span class="sxs-lookup"><span data-stu-id="dbf99-690">Used appropriately, add-ons can provide revenue while improving the game experience.</span></span> <span data-ttu-id="dbf99-691">Sie definieren und Veröffentlichen Ihres Spiels Add-Ons über das Partner Center und in-app-Käufen im Code Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="dbf99-691">You define and publish your game's add-ons through Partner Center, and enable in-app purchases in your game's code.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-692">Dauerhafte add-ons</span><span class="sxs-lookup"><span data-stu-id="dbf99-692">Durable add-ons</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt219684"><span data-ttu-id="dbf99-693">Unterstützen von Käufen von In-App-Produkten</span><span class="sxs-lookup"><span data-stu-id="dbf99-693">Enable in-app product purchases</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-694">Konsumierbaren add-ons</span><span class="sxs-lookup"><span data-stu-id="dbf99-694">Consumable add-ons</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt219683"><span data-ttu-id="dbf99-695">Aktivieren von Käufen von konsumierbaren In-App-Produkten</span><span class="sxs-lookup"><span data-stu-id="dbf99-695">Enable consumable in-app product purchases</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-696">Add-On-Details zu und Einreichung</span><span class="sxs-lookup"><span data-stu-id="dbf99-696">Add-on details and submission</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt148551"><span data-ttu-id="dbf99-697">Add-On-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="dbf99-697">Add-on submissions</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-698">Überwachen von Add-on-Verkauf und Demografie für Ihr Spiel</span><span class="sxs-lookup"><span data-stu-id="dbf99-698">Monitor add-on sales and demographics for your game</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt148538"><span data-ttu-id="dbf99-699">Bericht zu Add-On-Käufen</span><span class="sxs-lookup"><span data-stu-id="dbf99-699">Add-on acquisitions report</span></span></a></td>
    </tr>
</table>
 

### <a name="debugging-performance-optimization-and-monitoring"></a><span data-ttu-id="dbf99-700">Debuggen, Leistungsoptimierung und Überwachung</span><span class="sxs-lookup"><span data-stu-id="dbf99-700">Debugging, performance optimization, and monitoring</span></span>

<span data-ttu-id="dbf99-701">Zur Optimierung der Leistung, nutzen Sie den Spielmodus in Windows10, um Ihren Spielern ein optimales Erlebnis durch die vollständige Nutzung der Kapazität ihrer aktuellen Hardware zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="dbf99-701">To optimize performance, take advantage of Game Mode in Windows 10 to provide your gamers with the best possible gaming experience by fully utilizing the capacity of their current hardware.</span></span>

<span data-ttu-id="dbf99-702">Das Windows Performance Toolkit (WPT) besteht aus Leistungsüberwachungstools, die detaillierte Leistungsprofile von Windows-Betriebssystemen und -Anwendungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-702">The Windows Performance Toolkit (WPT) consists of performance monitoring tools that produce in-depth performance profiles of Windows operating systems and applications.</span></span> <span data-ttu-id="dbf99-703">Dies ist besonders hilfreich für die Überwachung der Speicherverwendung und zum Verbessern der Leistung eines Spiels.</span><span class="sxs-lookup"><span data-stu-id="dbf99-703">This is especially useful for monitoring memory usage and improving game performance.</span></span> <span data-ttu-id="dbf99-704">Das Windows Performance Toolkit ist im SDK für Windows 10 und im Windows ADK enthalten.</span><span class="sxs-lookup"><span data-stu-id="dbf99-704">The Windows Performance Toolkit is included in the Windows 10 SDK and Windows ADK.</span></span> <span data-ttu-id="dbf99-705">Dieses Toolkit besteht aus zwei unabhängigen Tools: Windows Performance Recorder (WPR) und Windows Performance Analyzer (WPA).</span><span class="sxs-lookup"><span data-stu-id="dbf99-705">This toolkit consists of two independent tools: Windows Performance Recorder (WPR) and Windows Performance Analyzer (WPA).</span></span> <span data-ttu-id="dbf99-706">ProcDump ist Teil von [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) und ist ein Befehlszeilenprogramm, das die Leistungsspitzen der CPU überwacht und Speicherabbilddateien während der Spielabstürze generiert.</span><span class="sxs-lookup"><span data-stu-id="dbf99-706">ProcDump, which is part of [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default), is a command-line utility that monitors CPU spikes and generates dump files during game crashes.</span></span> 

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-707">Leistungstest für Ihren Code</span><span class="sxs-lookup"><span data-stu-id="dbf99-707">Performance test your code</span></span></td>
        <td><a href="https://www.visualstudio.com/team-services/cloud-load-testing/"><span data-ttu-id="dbf99-708">Cloud-basierte Auslastungstests</span><span class="sxs-lookup"><span data-stu-id="dbf99-708">Cloud based load testing</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-709">Erhalten Sie Xbox-Konsolentypen mithilfe der Geräteinformationen für Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-709">Get Xbox console type using Gaming Device Information</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt825235"><span data-ttu-id="dbf99-710">Gaming-Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="dbf99-710">Gaming Device Information</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-711">Verbessern Sie die Leistung durch einen exklusiven oder prioritären Zugriff auf Hardwareressourcen mithilfe der Spielmodus-APIs</span><span class="sxs-lookup"><span data-stu-id="dbf99-711">Improve performance by getting exclusive or priority access to hardware resources using Game Mode APIs</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt808808"><span data-ttu-id="dbf99-712">Spielmodus</span><span class="sxs-lookup"><span data-stu-id="dbf99-712">Game Mode</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-713">Abrufen von Windows Performance Toolkit (WPT) aus dem Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="dbf99-713">Get Windows Performance Toolkit (WPT) from Windows 10 SDK</span></span></td>
        <td><a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk"><span data-ttu-id="dbf99-714">Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="dbf99-714">Windows 10 SDK</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-715">Abrufen von Windows Performance Toolkit (WPT) aus dem Windows ADK</span><span class="sxs-lookup"><span data-stu-id="dbf99-715">Get Windows Performance Toolkit (WPT) from Windows ADK</span></span></td>
        <td><a href="https://msdn.microsoft.com/windows/hardware/dn913721.aspx"><span data-ttu-id="dbf99-716">Windows ADK</span><span class="sxs-lookup"><span data-stu-id="dbf99-716">Windows ADK</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-717">Problembehandlung bei nicht reagierender Benutzeroberfläche mit Windows Performance Analyzer (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-717">Troubleshoot unresponsible UI using Windows Performance Analyzer (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-156-Critical-Path-Analysis-with-Windows-Performance-Analyzer"><span data-ttu-id="dbf99-718">Analyse des kritischen Pfads in WPA</span><span class="sxs-lookup"><span data-stu-id="dbf99-718">Critical path analysis with WPA</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-719">Diagnostizieren von Speicherverwendung und Arbeitsspeicherverlusten mit Windows Performance Recorder (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-719">Diagnose memory usage and leaks using Windows Performance Recorder (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-154-Memory-Footprint-and-Leaks"><span data-ttu-id="dbf99-720">Speicherbedarf und Arbeitsspeicherverluste</span><span class="sxs-lookup"><span data-stu-id="dbf99-720">Memory footprint and leaks</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-721">Abrufen von ProcDump</span><span class="sxs-lookup"><span data-stu-id="dbf99-721">Get ProcDump</span></span></td>
        <td><a href="https://technet.microsoft.com/sysinternals/dd996900"><span data-ttu-id="dbf99-722">ProcDump</span><span class="sxs-lookup"><span data-stu-id="dbf99-722">ProcDump</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-723">Informationen zur Verwendung von ProcDump (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-723">Learn to use ProcDump (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-131-Windows-10-SDK"><span data-ttu-id="dbf99-724">Konfigurieren von ProcDump zum Erstellen von Speicherabbilddateien</span><span class="sxs-lookup"><span data-stu-id="dbf99-724">Configure ProcDump to create dump files</span></span></a></td>
    </tr>
</table>

### <a name="advanced-directx-techniques-and-concepts"></a><span data-ttu-id="dbf99-725">Erweiterte DirectX-Techniken und -Konzepte</span><span class="sxs-lookup"><span data-stu-id="dbf99-725">Advanced DirectX techniques and concepts</span></span>

<span data-ttu-id="dbf99-726">Einige Aspekte der DirectX-Entwicklung können sich als differenziert und komplex erweisen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-726">Some portions of DirectX development can be nuanced and complex.</span></span> <span data-ttu-id="dbf99-727">Wenn Sie sich im Rahmen der Produktionsphase mit den Einzelheiten des DirectX-Moduls auseinandersetzen oder komplexe Leistungsprobleme debuggen müssen, können Sie auf die Ressourcen und Informationen in diesem Abschnitt zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-727">When you get to the point in production where you need to dig down into the details of your DirectX engine, or debug difficult performance problems, the resources and information in this section can help.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-728">PIX für Windows</span><span class="sxs-lookup"><span data-stu-id="dbf99-728">PIX on Windows</span></span></td>
        <td><a href="https://blogs.msdn.microsoft.com/pix/2017/01/17/introducing-pix-on-windows-beta/"><span data-ttu-id="dbf99-729">Leistungsoptimierungs- und -Debugg-Tools von DirectX12 für Windows</span><span class="sxs-lookup"><span data-stu-id="dbf99-729">Performance tuning and debugging tool for DirectX 12 on Windows</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-730">Überprüfungs- und Debugg-Tools für die Entwicklung von D3D12 (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-730">Debugging and validation tools for D3D12 development (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/GDC/GDC-2017/GDC2017-003"><span data-ttu-id="dbf99-731">D3D12-Leistung Leistungsoptimierung und-Debuggen mit PIX und GPUValidation</span><span class="sxs-lookup"><span data-stu-id="dbf99-731">D3D12 Performance Tuning and Debugging with PIX and GPUValidation</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-732">Grafik- und Leistungsoptimierung (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-732">Optimizing graphics and performance (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Advanced-DirectX12-Graphics-and-Performance"><span data-ttu-id="dbf99-733">Erweiterte DirectX12-Grafiken und -Leistung</span><span class="sxs-lookup"><span data-stu-id="dbf99-733">Advanced DirectX 12 Graphics and Performance</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-734">Debuggen von DirectX-Grafiken (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-734">DirectX graphics debugging (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools"><span data-ttu-id="dbf99-735">Lösen Sie komplexe Grafikprobleme in Ihrem Spiel mithilfe von DirectX-Tools.</span><span class="sxs-lookup"><span data-stu-id="dbf99-735">Solve the tough graphics problems with your game using DirectX Tools</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-736">Visual Studio2015-Tools zum Debuggen von DirectX12 (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-736">Visual Studio 2015 tools for debugging DirectX 12 (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Series/ConnectOn-Demand/212"><span data-ttu-id="dbf99-737">DirectX-Tools für Windows10 in Visual Studio2015</span><span class="sxs-lookup"><span data-stu-id="dbf99-737">DirectX tools for Windows 10 in Visual Studio 2015</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-738">Direct3D12-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="dbf99-738">Direct3D 12 programming guide</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/dn903821"><span data-ttu-id="dbf99-739">Direct3D12-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="dbf99-739">Direct3D 12 Programming Guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-740">Kombinieren von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="dbf99-740">Combining DirectX and XAML</span></span></td>
        <td><a href="directx-and-xaml-interop.md"><span data-ttu-id="dbf99-741">Interoperabilität von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="dbf99-741">DirectX and XAML interop</span></span></a></td>
    </tr>
</table>

### <a name="high-dynamic-range-hdr-content-development"></a><span data-ttu-id="dbf99-742">Entwicklung von HDR (HDR)-Inhalt</span><span class="sxs-lookup"><span data-stu-id="dbf99-742">High dynamic range (HDR) content development</span></span>

<span data-ttu-id="dbf99-743">Erstellen Sie Spieleinhalt, der die vollständigen Farbfunktionen von HDR verwendet.</span><span class="sxs-lookup"><span data-stu-id="dbf99-743">Build game content that uses the full color capabilities of HDR.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-744">Einführung in die Konzepte für HDR und Farbe (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-744">Introduction to HDR and color concepts (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/Build/2017/P4061"><span data-ttu-id="dbf99-745">Verbessern von HDR und erweiterte Farbe in DirectX</span><span class="sxs-lookup"><span data-stu-id="dbf99-745">Lighting up HDR and advanced color in DirectX</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-746">Erfahren Sie, wie Sie HDR-Inhalt darstellen, und ermitteln Sie, ob die aktuelle Anzeige dies unterstützt</span><span class="sxs-lookup"><span data-stu-id="dbf99-746">Learn how to render HDR content and detect whether the current display supports it</span></span></td>
        <td><a href="https://github.com/Microsoft/DirectX-Graphics-Samples/tree/master/Samples/UWP/D3D12HDR"><span data-ttu-id="dbf99-747">HDR-Beispiel</span><span class="sxs-lookup"><span data-stu-id="dbf99-747">HDR sample</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-748">Erstellen Sie und konfigurieren Sie eine erweiterte Farbe mit DirectX</span><span class="sxs-lookup"><span data-stu-id="dbf99-748">Create and configure an advanced color using DirectX</span></span></td>
        <td><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/D2DAdvancedColorImages"><span data-ttu-id="dbf99-749">Beispiel der erweiterten Farbe in Direct2D für das Rendering von Bildern</span><span class="sxs-lookup"><span data-stu-id="dbf99-749">Direct2D advanced color image rendering sample</span></span></a></td>
    </tr>   
</table>


### <a name="globalization-and-localization"></a><span data-ttu-id="dbf99-750">Globalisierung und Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="dbf99-750">Globalization and localization</span></span>

<span data-ttu-id="dbf99-751">Entwickeln Sie Windows-Spiele für den weltweiten Markt, und erfahren Sie mehr über die internationalen Features, die in die führenden Produkte von Microsoft integriert sind.</span><span class="sxs-lookup"><span data-stu-id="dbf99-751">Develop world-ready games for the Windows platform and learn about the international features built into Microsoft’s top products.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-752">Vorbereiten Ihres Spiels für den globalen Markt</span><span class="sxs-lookup"><span data-stu-id="dbf99-752">Preparing your game for the global market</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/xaml/mt186453.aspx"><span data-ttu-id="dbf99-753">Richtlinien für die Entwicklung für eine weltweite Zielgruppe</span><span class="sxs-lookup"><span data-stu-id="dbf99-753">Guidelines when developing for a global audience</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-754">Überwinden sprachlicher, kultureller und technologischer Barrieren</span><span class="sxs-lookup"><span data-stu-id="dbf99-754">Bridging languages, cultures, and technology</span></span></td>
        <td><a href="http://www.microsoft.com/Language/Default.aspx"><span data-ttu-id="dbf99-755">Onlineressource für Sprachkonventionen und Microsoft-Standardterminologie</span><span class="sxs-lookup"><span data-stu-id="dbf99-755">Online resource for language conventions and standard Microsoft terminology</span></span></a></td>
    </tr>
</table>

### <a name="security"></a><span data-ttu-id="dbf99-756">Sicherheit</span><span class="sxs-lookup"><span data-stu-id="dbf99-756">Security</span></span>

<span data-ttu-id="dbf99-757">Erstellen einer Umgebung, in der Spieler spielen und fair konkurrieren.</span><span class="sxs-lookup"><span data-stu-id="dbf99-757">Create an environment where your gamers can play and compete fairly.</span></span> <span data-ttu-id="dbf99-758">Ein Spiel, das mit TruePlay registriert wird, wird in einem geschützten Prozess ausgeführt, das eine Klasse von häufigen Angriffen verringert.</span><span class="sxs-lookup"><span data-stu-id="dbf99-758">A game enrolled in TruePlay runs in a protected process which mitigates a class of common attacks.</span></span> <span data-ttu-id="dbf99-759">Das Überwachungssystem der Spiele hilft Ihnen, allgemeine Täuschungsszenarien zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="dbf99-759">The game monitoring system also helps to identify common cheating scenarios.</span></span> 

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-760">Tools zur Bekämpfung von Täuschungen innerhalb von PC-Spielen</span><span class="sxs-lookup"><span data-stu-id="dbf99-760">Tools to combat cheating within PC games</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/mt808781"><span data-ttu-id="dbf99-761">TruePlay</span><span class="sxs-lookup"><span data-stu-id="dbf99-761">TruePlay</span></span></a></td>
    </tr>
</table>

## <a name="submitting-and-publishing-your-game"></a><span data-ttu-id="dbf99-762">Übermitteln und Veröffentlichen Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="dbf99-762">Submitting and publishing your game</span></span>

<span data-ttu-id="dbf99-763">Die folgenden Handbücher und Informationen sorgen für eine möglichst reibungslose Veröffentlichung und Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-763">The following guides and information help make the publishing and submission process as smooth as possible.</span></span>

### <a name="publishing"></a><span data-ttu-id="dbf99-764">Publishing</span><span class="sxs-lookup"><span data-stu-id="dbf99-764">Publishing</span></span>

<span data-ttu-id="dbf99-765">Verwenden Sie [Partner Center](https://partner.microsoft.com/dashboard) zum Veröffentlichen und Verwalten von spielpakete.</span><span class="sxs-lookup"><span data-stu-id="dbf99-765">You'll use [Partner Center](https://partner.microsoft.com/dashboard) to publish and manage your game packages.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-766">Partner Center-app-Veröffentlichung</span><span class="sxs-lookup"><span data-stu-id="dbf99-766">Partner Center app publishing</span></span></td>
        <td><a href="https://dev.windows.com/publish"><span data-ttu-id="dbf99-767">Veröffentlichen von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-767">Publish Windows apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-768">Partner Center erweiterte Veröffentlichung (GDN)</span><span class="sxs-lookup"><span data-stu-id="dbf99-768">Partner Center advanced publishing (GDN)</span></span></td>
        <td><a href="https://developer.xboxlive.com/en-us/windows/documentation/Pages/home.aspx"><span data-ttu-id="dbf99-769">Partner Center publishing-Handbuch</span><span class="sxs-lookup"><span data-stu-id="dbf99-769">Partner Center advanced publishing guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-770">Verwenden von Azure Active Directory (AAD) Ihrem Partner Center-Konto Benutzer hinzufügen</span><span class="sxs-lookup"><span data-stu-id="dbf99-770">Use Azure Active Directory (AAD) to add users to your Partner Center account</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/publish/manage-account-users"><span data-ttu-id="dbf99-771">Verwalten von Kontobenutzern</span><span class="sxs-lookup"><span data-stu-id="dbf99-771">Manage account users</span></span></a></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="dbf99-772">Bewertung des Spiels (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="dbf99-772">Rating your game (blog post)</span></span></td>
        <td><a href="https://blogs.windows.com/buildingapps/2016/01/06/now-available-single-age-rating-system-to-simplify-app-submissions/"><span data-ttu-id="dbf99-773">Einzelner Workflow zum Zuweisen von Altersfreigaben mit IARC-System</span><span class="sxs-lookup"><span data-stu-id="dbf99-773">Single workflow to assign age ratings using IARC system</span></span></a></td>
    </tr>
</table>

#### <a name="packaging-and-uploading"></a><span data-ttu-id="dbf99-774">Packen und Hochladen</span><span class="sxs-lookup"><span data-stu-id="dbf99-774">Packaging and uploading</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-775">Informationen zur Verwendung der Streaming-Installation und optionale Pakete (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-775">Learn to use streaming install and optional packages (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/Build/2017/B8093"><span data-ttu-id="dbf99-776">Nextgen UWP-app-Verteilung: Erstellen von extensible, Stream können Componentizedapps</span><span class="sxs-lookup"><span data-stu-id="dbf99-776">Nextgen UWP app distribution: Building extensible, stream-able, componentizedapps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-777">Unterteilen und Gruppieren zum Aktivieren von Inhalten für die Streaming-Installation</span><span class="sxs-lookup"><span data-stu-id="dbf99-777">Divide and group content to enable streaming install</span></span></td>
        <td><a href="../packaging/streaming-install.md"><span data-ttu-id="dbf99-778">UWP-App-Streaming installieren</span><span class="sxs-lookup"><span data-stu-id="dbf99-778">UWP App Streaming install</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-779">Optionale Pakete wie DLC-Spielinhalte erstellen</span><span class="sxs-lookup"><span data-stu-id="dbf99-779">Create optional packages like DLC game content</span></span></td>
        <td><a href="../packaging/optional-packages.md"><span data-ttu-id="dbf99-780">Optionale Pakete und die Erstellung zugehöriger Sets</span><span class="sxs-lookup"><span data-stu-id="dbf99-780">Optional packages and related set authoring</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-781">Packen Ihres UWP-Spiels</span><span class="sxs-lookup"><span data-stu-id="dbf99-781">Package your UWP game</span></span></td>
        <td><a href="../packaging/index.md"><span data-ttu-id="dbf99-782">Verpacken von Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-782">Packaging apps</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-783">Packen Ihres UWP-DirectX-Spiels</span><span class="sxs-lookup"><span data-stu-id="dbf99-783">Package your UWP DirectX game</span></span></td>
        <td><a href="package-your-windows-store-directx-game.md"><span data-ttu-id="dbf99-784">Packen Ihres UWP-DirectX-Spiels</span><span class="sxs-lookup"><span data-stu-id="dbf99-784">Package your UWP DirectX game</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-785">Packen Ihres Spiels als Drittentwickler (Blogbeitrag)</span><span class="sxs-lookup"><span data-stu-id="dbf99-785">Packaging your game as a 3rd party developer (blog post)</span></span></td>
        <td><a href="https://blogs.windows.com/buildingapps/2015/12/15/building-an-app-for-a-3rd-party-how-to-package-their-store-app/"><span data-ttu-id="dbf99-786">Erstellen von hochladbaren Paketen ohne Zugriff auf das Store-Konto des Veröffentlichers</span><span class="sxs-lookup"><span data-stu-id="dbf99-786">Create uploadable packages without publisher's store account access</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-787">Erstellen von App-Paketen und App-Paketbündeln mit MakeAppx</span><span class="sxs-lookup"><span data-stu-id="dbf99-787">Creating app packages and app package bundles using MakeAppx</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool"><span data-ttu-id="dbf99-788">Erstellen von Paketen mit dem App-Verpackungsprogramm MakeAppx.exe</span><span class="sxs-lookup"><span data-stu-id="dbf99-788">Create packages using app packager tool MakeAppx.exe</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-789">Digitales Signieren Ihrer Dateien mithilfe von SignTool</span><span class="sxs-lookup"><span data-stu-id="dbf99-789">Signing your files digitally using SignTool</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/desktop/aa387764"><span data-ttu-id="dbf99-790">Signieren von Dateien und Überprüfen von Signaturen in Dateien mithilfe von SignTool</span><span class="sxs-lookup"><span data-stu-id="dbf99-790">Sign files and verify signatures in files using SignTool</span></span></a></td>
    </tr>    
    <tr>
        <td><span data-ttu-id="dbf99-791">Hochladen und Verwalten der Versionen Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="dbf99-791">Uploading and versioning your game</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt148542"><span data-ttu-id="dbf99-792">Hochladen von App-Paketen</span><span class="sxs-lookup"><span data-stu-id="dbf99-792">Upload app packages</span></span></a></td>
    </tr>
</table>


### <a name="policies-and-certification"></a><span data-ttu-id="dbf99-793">Richtlinien und Zertifizierung</span><span class="sxs-lookup"><span data-stu-id="dbf99-793">Policies and certification</span></span>

<span data-ttu-id="dbf99-794">Stellen Sie sicher, dass sich die Veröffentlichung Ihres Spiels nicht aufgrund von Zertifizierungsproblemen verzögert.</span><span class="sxs-lookup"><span data-stu-id="dbf99-794">Don't let certification issues delay your game's release.</span></span> <span data-ttu-id="dbf99-795">Hier finden Sie Richtlinien und Informationen zu gängigen Zertifizierungsproblemen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-795">Here are policies and common certification issues to be aware of.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-796">Vereinbarung für Entwickler von MicrosoftStore-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-796">Microsoft Store App Developer Agreement</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/hh694058"><span data-ttu-id="dbf99-797">Vereinbarung für App-Entwickler</span><span class="sxs-lookup"><span data-stu-id="dbf99-797">App Developer Agreement</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-798">Richtlinien für die Veröffentlichung von Apps im MicrosoftStore</span><span class="sxs-lookup"><span data-stu-id="dbf99-798">Policies for publishing apps in the Microsoft Store</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/dn764944"><span data-ttu-id="dbf99-799">Microsoft Store-Richtlinien</span><span class="sxs-lookup"><span data-stu-id="dbf99-799">Microsoft Store Policies</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-800">So wird's gemacht: Vermeiden allgemeiner Probleme bei der App-Zertifizierung</span><span class="sxs-lookup"><span data-stu-id="dbf99-800">How to avoid some common app certification issues</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/jj657968"><span data-ttu-id="dbf99-801">Vermeiden allgemeiner Zertifizierungsfehler</span><span class="sxs-lookup"><span data-stu-id="dbf99-801">Avoid common certification failures</span></span></a></td>
    </tr>
</table>
 

### <a name="store-manifest-storemanifestxml"></a><span data-ttu-id="dbf99-802">Store-Manifest („StoreManifest.xml“)</span><span class="sxs-lookup"><span data-stu-id="dbf99-802">Store manifest (StoreManifest.xml)</span></span>

<span data-ttu-id="dbf99-803">Das Store-Manifest („StoreManifest.xml“) ist eine optionale Konfigurationsdatei, die Sie Ihrem App-Paket hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="dbf99-803">The store manifest (StoreManifest.xml) is an optional configuration file that can be included in your app package.</span></span> <span data-ttu-id="dbf99-804">Das Store-Manifest bietet zusätzliche Features, die über den Umfang der Datei „AppxManifest.xml“ hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-804">The store manifest provides additional features that are not part of the AppxManifest.xml file.</span></span> <span data-ttu-id="dbf99-805">So können Sie mithilfe des Store-Manifests etwa die Installation Ihres Spiels blockieren, wenn ein Zielgerät nicht über die mindestens erforderliche DirectX-Featureebene verfügt oder der verfügbare Systemspeicher nicht ausreicht.</span><span class="sxs-lookup"><span data-stu-id="dbf99-805">For example, you can use the store manifest to block installation of your game if a target device doesn't have the specified minimum DirectX feature level, or the specified minimum system memory.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-806">Store-Manifest-Schema</span><span class="sxs-lookup"><span data-stu-id="dbf99-806">Store manifest schema</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt617335"><span data-ttu-id="dbf99-807">StoreManifest-Schema (Windows10)</span><span class="sxs-lookup"><span data-stu-id="dbf99-807">StoreManifest schema (Windows 10)</span></span></a></td>
    </tr>
</table>
 

## <a name="game-lifecycle-management"></a><span data-ttu-id="dbf99-808">Spiellebenszyklusverwaltung</span><span class="sxs-lookup"><span data-stu-id="dbf99-808">Game lifecycle management</span></span>


<span data-ttu-id="dbf99-809">Wer glaubt, sich nach dem Abschluss der Entwicklung und der Auslieferung eines Spiels entspannt zurücklehnen zu können, irrt:</span><span class="sxs-lookup"><span data-stu-id="dbf99-809">After you've finished development and shipped your game, it's not "game over".</span></span> <span data-ttu-id="dbf99-810">Die Entwicklung von Version1 mag zwar abgeschlossen sein, die Marktphase Ihres Spiels hat jedoch gerade erst begonnen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-810">You may be done with development on version one, but your game's journey in the marketplace has only just begun.</span></span> <span data-ttu-id="dbf99-811">Sie sollten Verwendung und Fehlerberichte überwachen, auf Benutzerfeedback reagieren und Updates für Ihr Spiel veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="dbf99-811">You'll want to monitor usage and error reporting, respond to user feedback, and publish updates to your game.</span></span>

### <a name="partner-center-analytics-and-promotion"></a><span data-ttu-id="dbf99-812">Partner Center-Analysen und Werbung</span><span class="sxs-lookup"><span data-stu-id="dbf99-812">Partner Center analytics and promotion</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-813">Partner Center analytics</span><span class="sxs-lookup"><span data-stu-id="dbf99-813">Partner Center analytics</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt148522"><span data-ttu-id="dbf99-814">Analysieren der App-Leistung</span><span class="sxs-lookup"><span data-stu-id="dbf99-814">Analyze app performance</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-815">Hier erfahren Sie, wie Ihre Kunden mit der Xbox-Features in Ihrem Spiel interagieren</span><span class="sxs-lookup"><span data-stu-id="dbf99-815">Learn how your customers are engaging with the Xbox features in your game</span></span></td>
        <td><a href="../publish/xbox-analytics-report.md"><span data-ttu-id="dbf99-816">Bericht der Xbox Analyse</span><span class="sxs-lookup"><span data-stu-id="dbf99-816">Xbox analytics report</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-817">Reagieren auf Kundenrezensionen</span><span class="sxs-lookup"><span data-stu-id="dbf99-817">Responding to customer reviews</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt148546"><span data-ttu-id="dbf99-818">Reagieren auf Kundenrezensionen</span><span class="sxs-lookup"><span data-stu-id="dbf99-818">Respond to customer reviews</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-819">Werbemöglichkeiten für Ihr Spiel</span><span class="sxs-lookup"><span data-stu-id="dbf99-819">Ways to promote your game</span></span></td>
        <td><a href="https://dev.windows.com/store-promotion"><span data-ttu-id="dbf99-820">Bewerben Ihrer Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-820">Promote your apps</span></span></a></td>
    </tr>
</table>
 

### <a name="visual-studio-application-insights"></a><span data-ttu-id="dbf99-821">Visual Studio Application Insights</span><span class="sxs-lookup"><span data-stu-id="dbf99-821">Visual Studio Application Insights</span></span>

<span data-ttu-id="dbf99-822">Visual Studio Application Insights bietet Leistungs-, Telemetrie- und Verwendungsanalysen für Ihr veröffentlichtes Spiel.</span><span class="sxs-lookup"><span data-stu-id="dbf99-822">Visual Studio Application Insights provides performance, telemetry, and usage analytics for your published game.</span></span> <span data-ttu-id="dbf99-823">Application Insights unterstützt Sie nach der Veröffentlichung Ihres Spiels beim Erkennen und Beheben von Problemen sowie bei der kontinuierlichen Überwachung und Optimierung der Verwendung und beim Nachvollziehen der weiteren Spielerinteraktionen mit Ihrem Spiel.</span><span class="sxs-lookup"><span data-stu-id="dbf99-823">Application Insights helps you detect and solve issues after your game is released, continuously monitor and improve usage, and understand how players are continuing to interact with your game.</span></span> <span data-ttu-id="dbf99-824">Application Insights fügt Ihrer App ein SDK hinzu, das Telemetriedaten an das [Azure-Portal](http://portal.azure.com/) übermittelt.</span><span class="sxs-lookup"><span data-stu-id="dbf99-824">Application Insights works by adding an SDK into your app, which sends telemetry to the [Azure portal](http://portal.azure.com/).</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-825">Analyse von Anwendungsleistung und -verwendung</span><span class="sxs-lookup"><span data-stu-id="dbf99-825">Application performance and usage analytics</span></span></td>
        <td><a href="https://azure.microsoft.com/documentation/articles/app-insights-get-started/"><span data-ttu-id="dbf99-826">Visual Studio Application Insights</span><span class="sxs-lookup"><span data-stu-id="dbf99-826">Visual Studio Application Insights</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-827">Aktivieren von Application Insights in Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-827">Enable Application Insights in Windows apps</span></span></td>
        <td><a href="https://azure.microsoft.com/documentation/articles/app-insights-windows-get-started/"><span data-ttu-id="dbf99-828">Application Insights für Windows Phone- und Windows Store-Apps</span><span class="sxs-lookup"><span data-stu-id="dbf99-828">Application Insights for Windows Phone and Store apps</span></span></a></td>
    </tr>
</table>


### <a name="third-party-solutions-for-analytics-and-promotion"></a><span data-ttu-id="dbf99-829">Lösungen von Drittanbietern für Analysen und Werbung</span><span class="sxs-lookup"><span data-stu-id="dbf99-829">Third party solutions for analytics and promotion</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-830">Verstehen der Spielerverhalten mit GameAnalytics</span><span class="sxs-lookup"><span data-stu-id="dbf99-830">Understand player behavior using GameAnalytics</span></span></td>
        <td><a href="http://www.gameanalytics.com/"><span data-ttu-id="dbf99-831">GameAnalytics</span><span class="sxs-lookup"><span data-stu-id="dbf99-831">GameAnalytics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-832">Verbinden Sie Ihr UWP-Spiel mit Google Analytics</span><span class="sxs-lookup"><span data-stu-id="dbf99-832">Connect your UWP game to Google Analytics</span></span></td>
        <td><a href="https://github.com/dotnet/windows-sdk-for-google-analytics"><span data-ttu-id="dbf99-833">Holen Sie sich Windows SDK für Google Analytics</span><span class="sxs-lookup"><span data-stu-id="dbf99-833">Get Windows SDK for Google Analytics</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-834">Hier erfahren Sie, wie Sie Windows SDK für Google Analytics (Video) verwenden</span><span class="sxs-lookup"><span data-stu-id="dbf99-834">Learn how to use Windows SDK for Google Analytics (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Creators-Update/Getting-started-with-the-Windows-SDK-for-Google-Analytics"><span data-ttu-id="dbf99-835">Erste Schritte mit Windows SDK für Google Analytics</span><span class="sxs-lookup"><span data-stu-id="dbf99-835">Getting started with Windows SDK for Google Analytics</span></span></a></td>
    </tr>    
    <tr>
        <td><span data-ttu-id="dbf99-836">Verwenden der Facebook-App zum Installieren von Anzeigen, bietet Werbemöglichkeiten für Ihr Spiel für Facebook-Benutzer an</span><span class="sxs-lookup"><span data-stu-id="dbf99-836">Use Facebook App Installs Ads to promote your game to Facebook users</span></span></td>
        <td><a href="https://github.com/Microsoft/winsdkfb"><span data-ttu-id="dbf99-837">Holen Sie sich Windows SDK für Facebook</span><span class="sxs-lookup"><span data-stu-id="dbf99-837">Get Windows SDK for Facebook</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-838">Hier erfahren Sie, wie Sie die Facebook-App zum Installieren von Anzeigen verwenden (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-838">Learn how to use Facebook App Installs Ads (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Creators-Update/Getting-started-with-Facebook-App-Install-Ads"><span data-ttu-id="dbf99-839">Erste Schritte mit Windows SDK für Facebook</span><span class="sxs-lookup"><span data-stu-id="dbf99-839">Getting started with Windows SDK for Facebook</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-840">Verwenden von Vungle, um Ihren Spielen Videoanzeigen hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="dbf99-840">Use Vungle to add video ads into your games</span></span></td>
        <td><a href="https://v.vungle.com/sdk"><span data-ttu-id="dbf99-841">WindowsSDK für Vungle herunterladen</span><span class="sxs-lookup"><span data-stu-id="dbf99-841">Get Windows SDK for Vungle</span></span></a></td>
    </tr>
</table>
 

### <a name="creating-and-managing-content-updates"></a><span data-ttu-id="dbf99-842">Erstellen und Verwalten von Inhaltsaktualisierungen</span><span class="sxs-lookup"><span data-stu-id="dbf99-842">Creating and managing content updates</span></span>

<span data-ttu-id="dbf99-843">Zum Aktualisieren Ihres veröffentlichten Spiels übermitteln Sie ein neues App-Paket mit einer höheren Versionsnummer.</span><span class="sxs-lookup"><span data-stu-id="dbf99-843">To update your published game, submit a new app package with a higher version number.</span></span> <span data-ttu-id="dbf99-844">Nachdem das Paket den Übermittlungs- und Zertifizierungsprozess durchlaufen hat, wird es für die Kunden automatisch als Update verfügbar.</span><span class="sxs-lookup"><span data-stu-id="dbf99-844">After the package makes its way through submission and certification, it will automatically be available to customers as an update.</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-845">Aktualisieren und Verwalten der Versionen Ihres Spiels</span><span class="sxs-lookup"><span data-stu-id="dbf99-845">Updating and versioning your game</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt188602"><span data-ttu-id="dbf99-846">Paketversionsnummern</span><span class="sxs-lookup"><span data-stu-id="dbf99-846">Package version numbering</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-847">Leitfaden für die Spielpaketverwaltung</span><span class="sxs-lookup"><span data-stu-id="dbf99-847">Game package management guidance</span></span></td>
        <td><a href="https://msdn.microsoft.com/library/windows/apps/mt188602"><span data-ttu-id="dbf99-848">Leitfaden für die App-Paketverwaltung</span><span class="sxs-lookup"><span data-stu-id="dbf99-848">Guidance for app package management</span></span></a></td>
    </tr>
</table>


## <a name="adding-xbox-live-to-your-game"></a><span data-ttu-id="dbf99-849">Hinzufügen von Xbox Live zu Ihrem Spiel</span><span class="sxs-lookup"><span data-stu-id="dbf99-849">Adding Xbox Live to your game</span></span>

<span data-ttu-id="dbf99-850">Xbox Live ist ein erstklassiges Gaming-Netzwerk, das Millionen von Spielern weltweit verbindet.</span><span class="sxs-lookup"><span data-stu-id="dbf99-850">Xbox Live is a premier gaming network that connects millions of gamers across the world.</span></span> <span data-ttu-id="dbf99-851">Entwickler haben Zugriff auf Xbox Live-Features, die die Spielerzielgruppe steigern, einschließlich Xbox Live, Bestenlisten, Cloudspeicherungen, Spielehubs, Clubs, Party-Chat, Game DVR und mehr.</span><span class="sxs-lookup"><span data-stu-id="dbf99-851">Developers gain access to Xbox Live features that can organically grow their game’s audience, including Xbox Live presence, Leaderboards, Cloud Saves, Game Hubs, Clubs, Party Chat, Game DVR, and more.</span></span>

> [!Note]
> <span data-ttu-id="dbf99-852">Wenn Sie Xbox Live aktivierte Titel entwickeln möchten, stehen Ihnen verschiedene Optionen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="dbf99-852">If you would like to develop Xbox Live enabled titles, there are several options are available to you.</span></span> <span data-ttu-id="dbf99-853">Informationen zu den verschiedenen Programmen finden Sie unter [Übersicht über das Entwickler-Programm](../xbox-live/developer-program-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dbf99-853">For info about the various programs, see [Developer program overview](../xbox-live/developer-program-overview.md).</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-854">Xbox Live – Übersicht</span><span class="sxs-lookup"><span data-stu-id="dbf99-854">Xbox Live overview</span></span></td>
        <td><a href="../xbox-live/index.md"><span data-ttu-id="dbf99-855">Xbox Live – Entwicklerhandbuch</span><span class="sxs-lookup"><span data-stu-id="dbf99-855">Xbox Live developer guide</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-856">Verstehen, welche Features je nach Programm verfügbar sind</span><span class="sxs-lookup"><span data-stu-id="dbf99-856">Understand which features are available depending on program</span></span></td>
        <td><a href="../xbox-live/developer-program-overview.md#feature-table"><span data-ttu-id="dbf99-857">Übersicht über das Entwickler-Programm: Tabelle der Features</span><span class="sxs-lookup"><span data-stu-id="dbf99-857">Developer program overview: Feature table</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-858">Links zu nützlichen Ressourcen für die Entwicklung von Xbox Live-Spielen</span><span class="sxs-lookup"><span data-stu-id="dbf99-858">Links to useful resources for developing Xbox Live games</span></span></td>
        <td><a href="../xbox-live/xbox-live-resources.md"><span data-ttu-id="dbf99-859">Xbox Live-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="dbf99-859">Xbox Live resources</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-860">Erfahren Sie, wie Sie Informationen über Xbox Live-Dienste abrufen</span><span class="sxs-lookup"><span data-stu-id="dbf99-860">Learn how to get info from Xbox Live services</span></span></td>
        <td><a href="../xbox-live/introduction-to-xbox-live-apis.md"><span data-ttu-id="dbf99-861">Einführung in Xbox Live APIs</span><span class="sxs-lookup"><span data-stu-id="dbf99-861">Introduction to Xbox Live APIs</span></span></a></td>
    </tr>
</table>


### <a name="for-developers-in-the-xbox-live-creators-program"></a><span data-ttu-id="dbf99-862">Für Entwickler im Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="dbf99-862">For developers in the Xbox Live Creators Program</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-863">Übersicht</span><span class="sxs-lookup"><span data-stu-id="dbf99-863">Overview</span></span></td>
        <td><a href="../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md"><span data-ttu-id="dbf99-864">Erste Schritte – Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="dbf99-864">Get started with the Xbox Live Creators Program</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-865">Hinzufügen von Xbox Live zu Ihrem Spiel</span><span class="sxs-lookup"><span data-stu-id="dbf99-865">Add Xbox Live to your game</span></span></td>
        <td><a href="../xbox-live/get-started-with-creators/creators-step-by-step-guide.md"><span data-ttu-id="dbf99-866">Schrittweise Anleitung zur Integration mit dem Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="dbf99-866">Step by step guide to integrate Xbox Live Creators Program</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-867">Hinzufügen von Xbox Live zu Ihrem UWP-Spiel, das mit Unity erstellt wurde</span><span class="sxs-lookup"><span data-stu-id="dbf99-867">Add Xbox Live to your UWP game created using Unity</span></span></td>
        <td><a href="../xbox-live/get-started-with-creators/develop-creators-title-with-unity.md"><span data-ttu-id="dbf99-868">Erste Schritte bei der Entwicklung eines Titels im Xbox Live Creators-Programm mit der Unity-Spielengine</span><span class="sxs-lookup"><span data-stu-id="dbf99-868">Get started developing an Xbox Live Creators Program title with the Unity game engine</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-869">Einrichten der Entwicklungs-Sandbox</span><span class="sxs-lookup"><span data-stu-id="dbf99-869">Set up your development sandbox</span></span></td>
        <td><a href="../xbox-live/get-started-with-creators/xbox-live-sandboxes-creators.md"><span data-ttu-id="dbf99-870">Einführung in die Xbox Live-Sandbox</span><span class="sxs-lookup"><span data-stu-id="dbf99-870">Xbox Live sandboxes introduction</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-871">Einrichten von Konten zum Testen</span><span class="sxs-lookup"><span data-stu-id="dbf99-871">Set up accounts for testing</span></span></td>
        <td><a href="../xbox-live/get-started-with-creators/authorize-xbox-live-accounts.md"><span data-ttu-id="dbf99-872">Xbox Live-Konten in Ihrer Testumgebung autorisieren</span><span class="sxs-lookup"><span data-stu-id="dbf99-872">Authorize Xbox Live accounts in your test environment</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-873">Beispiele für das Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="dbf99-873">Samples for Xbox Live Creators Program</span></span></td>
        <td><a href="https://github.com/Microsoft/xbox-live-samples/tree/master/Samples/CreatorsSDK"><span data-ttu-id="dbf99-874">Codebeispiele für Creators Programm-Entwickler</span><span class="sxs-lookup"><span data-stu-id="dbf99-874">Code samples for Creators Program developers</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-875">Enthält Informationen zum Integrieren von plattformübergreifenden Xbox Live-Umgebungen in UWP-Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-875">Learn how to integrate cross-platform Xbox Live experiences in UWP games (video)</span></span></td>
        <td><a href="https://channel9.msdn.com/Events/GDC/GDC-2017/GDC2017-005"><span data-ttu-id="dbf99-876">Xbox Live Creators-Programm</span><span class="sxs-lookup"><span data-stu-id="dbf99-876">Xbox Live Creators Program</span></span></a></td>
    </tr>  
</table>

### <a name="for-managed-partners-and-developers-in-the-idxbox-program"></a><span data-ttu-id="dbf99-877">Für verwaltete Partner und Entwickler im ID@Xbox-Programm</span><span class="sxs-lookup"><span data-stu-id="dbf99-877">For managed partners and developers in the ID@Xbox program</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-878">Übersicht</span><span class="sxs-lookup"><span data-stu-id="dbf99-878">Overview</span></span></td>
        <td><a href="../xbox-live/get-started-with-partner/get-started-with-xbox-live-partner.md"><span data-ttu-id="dbf99-879">Erste Schritte mit Xbox Live als verwalteter Partner oder ID-Entwickler</span><span class="sxs-lookup"><span data-stu-id="dbf99-879">Get started with Xbox Live as a managed partner or an ID developer</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-880">Hinzufügen von Xbox Live zu Ihrem Spiel</span><span class="sxs-lookup"><span data-stu-id="dbf99-880">Add Xbox Live to your game</span></span></td>
        <td><a href="../xbox-live/get-started-with-partner/partners-step-by-step-guide.md"><span data-ttu-id="dbf99-881">Schrittweise Anleitung zum Integrieren von Xbox Live für verwaltete Partner und ID Mitglieder</span><span class="sxs-lookup"><span data-stu-id="dbf99-881">Step by step guide to integrate Xbox Live for managed partners and ID members</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-882">Hinzufügen von Xbox Live zu Ihrem UWP-Spiel, das mit Unity erstellt wurde</span><span class="sxs-lookup"><span data-stu-id="dbf99-882">Add Xbox Live to your UWP game created using Unity</span></span></td>
        <td><a href="../xbox-live/get-started-with-partner/partner-unity-uwp-il2cpp.md"><span data-ttu-id="dbf99-883">Hinzufügen von Xbox Live-Unterstützung zu Unity für UWP mit IL2CPP Scripting-Back-End für ID- und verwaltete Partner</span><span class="sxs-lookup"><span data-stu-id="dbf99-883">Add Xbox Live support to Unity for UWP with IL2CPP scripting backend for ID and managed partners</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-884">Einrichten der Entwicklungs-Sandbox</span><span class="sxs-lookup"><span data-stu-id="dbf99-884">Set up your development sandbox</span></span></td>
        <td><a href="../xbox-live/get-started-with-partner/advanced-xbox-live-sandboxes.md"><span data-ttu-id="dbf99-885">Erweiterte Xbox Live-Sandbox</span><span class="sxs-lookup"><span data-stu-id="dbf99-885">Advanced Xbox Live sandboxes</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-886">Anforderungen für Spiele mit Xbox Live (GDN)</span><span class="sxs-lookup"><span data-stu-id="dbf99-886">Requirements for games that use Xbox Live (GDN)</span></span></td>
        <td><a href="http://go.microsoft.com/fwlink/?LinkId=533217"><span data-ttu-id="dbf99-887">Xbox-Anforderungen für Xbox Live unter Windows 10</span><span class="sxs-lookup"><span data-stu-id="dbf99-887">Xbox Requirements for Xbox Live on Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-888">Beispiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-888">Samples</span></span></td>
        <td><a href="https://github.com/Microsoft/xbox-live-samples/tree/master/Samples/ID%40XboxSDK"><span data-ttu-id="dbf99-889">Codebeispiele für ID@Xbox-Entwickler</span><span class="sxs-lookup"><span data-stu-id="dbf99-889">Code samples for ID@Xbox developers</span></span></a></td>
    </tr>  
    <tr>
        <td><span data-ttu-id="dbf99-890">Übersicht über die Entwicklung von Spielen mit Xbox Live (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-890">Overview of Xbox Live game development (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Developing-with-Xbox-Live-for-Windows-10"><span data-ttu-id="dbf99-891">Entwickeln mit Xbox Live für Windows10</span><span class="sxs-lookup"><span data-stu-id="dbf99-891">Developing with Xbox Live for Windows 10</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-892">Plattformübergreifende Spielersuche (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-892">Cross-platform matchmaking (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Xbox-Live-Multiplayer-Introducing-services-for-cross-platform-matchmaking-and-gameplay"><span data-ttu-id="dbf99-893">Xbox Live Multiplayer: Einführung in die Dienste für plattformübergreifende Spielersuche und Spiele</span><span class="sxs-lookup"><span data-stu-id="dbf99-893">Xbox Live Multiplayer: Introducing services for cross-platform matchmaking and gameplay</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-894">Geräteübergreifendes Spielen in Fable Legends (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-894">Cross-device gameplay in Fable Legends (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Fable-Legends-Cross-device-Gameplay-with-Xbox-Live"><span data-ttu-id="dbf99-895">Fable Legends: Geräteübergreifendes Spielen mit Xbox Live</span><span class="sxs-lookup"><span data-stu-id="dbf99-895">Fable Legends: Cross-device Gameplay with Xbox Live</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-896">Xbox Live und Erfolge (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-896">Xbox Live stats and achievements (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Best-Practices-for-Leveraging-Cloud-Based-User-Stats-and-Achievements-in-Xbox-Live"><span data-ttu-id="dbf99-897">Bewährte Methoden für die Nutzung von cloudbasierten Benutzerstatistiken und Erfolgen in Xbox Live</span><span class="sxs-lookup"><span data-stu-id="dbf99-897">Best Practices for Leveraging Cloud-Based User Stats and Achievements in Xbox Live</span></span></a></td>
    </tr>
</table>


## <a name="additional-resources"></a><span data-ttu-id="dbf99-898">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="dbf99-898">Additional resources</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dbf99-899">Entwicklung von Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-899">Game development videos</span></span></td>
        <td><a href="https://docs.microsoft.com/windows/uwp/gaming/game-development-videos"><span data-ttu-id="dbf99-900">Videos von wichtigen Konferenzen wie GDC und //Build</span><span class="sxs-lookup"><span data-stu-id="dbf99-900">Videos from major conferences like GDC and //build</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-901">Entwicklung von Indie-Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-901">Indie game development (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/New-Opportunities-for-Independent-Developers"><span data-ttu-id="dbf99-902">Neue Möglichkeiten für unabhängige Entwickler</span><span class="sxs-lookup"><span data-stu-id="dbf99-902">New Opportunities for Independent Developers</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-903">Überlegungen für mobile Multi-Core-Geräte (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-903">Considerations for multi-core mobile devices (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/Sustained-gaming-performance-in-multi-core-mobile-devices"><span data-ttu-id="dbf99-904">Kontinuierlich hohe Spieleleistung auf mobilen Multi-Core-Geräten</span><span class="sxs-lookup"><span data-stu-id="dbf99-904">Sustained Gaming Performance in multi-core mobile devices</span></span></a></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dbf99-905">Entwickeln von Windows10-Desktopspielen (Video)</span><span class="sxs-lookup"><span data-stu-id="dbf99-905">Developing Windows 10 desktop games (video)</span></span></td>
        <td><a href="http://channel9.msdn.com/Events/GDC/GDC-2015/PC-Games-for-Windows-10"><span data-ttu-id="dbf99-906">PC-Spiele für Windows10</span><span class="sxs-lookup"><span data-stu-id="dbf99-906">PC Games for Windows 10</span></span></a></td>
    </tr>
</table>



 

 

 
