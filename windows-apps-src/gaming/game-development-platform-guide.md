---
title: Spieletechnologien für UWP-Apps
description: Dieses Handbuch enthält Informationen über verfügbare Technologien zur Entwicklung von Spielen für die Universelle Windows-Plattform (UWP).
ms.assetid: bc4d4648-0d6e-efbb-7608-80bd09decd6e
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Technologie, DirectX
ms.localizationpriority: medium
ms.openlocfilehash: c6d2ebad640849cd81d6a2704f89ca1f05cc1b27
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8687561"
---
# <a name="game-technologies-for-uwp-apps"></a><span data-ttu-id="88121-104">Spieletechnologien für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="88121-104">Game technologies for UWP apps</span></span>



<span data-ttu-id="88121-105">Dieses Handbuch enthält Informationen über verfügbare Technologien zur Entwicklung von Spielen für die Universelle Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="88121-105">In this guide, you'll learn about the technologies available for developing Universal Windows Platform (UWP) games.</span></span>

##  <a name="benefits-of-windows10-for-game-development"></a><span data-ttu-id="88121-106">Vorteile von Windows 10 für die Spieleentwicklung</span><span class="sxs-lookup"><span data-stu-id="88121-106">Benefits of Windows10 for game development</span></span>


<span data-ttu-id="88121-107">Mit der Einführung von UWP in Windows 10 werden Ihre Windows 10-Titel auf allen Microsoft-Plattformen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="88121-107">With the introduction of UWP in Windows10, your Windows10 titles will be able to span all of the Microsoft platforms.</span></span> <span data-ttu-id="88121-108">Dank der kostenlosen Migration von früheren Versionen von Windows besteht Zahl von Windows 10-Clients ständig zunehmende.</span><span class="sxs-lookup"><span data-stu-id="88121-108">With free migration from previous versions of Windows, there is a steadily increasing number of Windows10 clients.</span></span> <span data-ttu-id="88121-109">Die Kombination dieser beiden Umstände bedeutet, dass Ihre Windows 10-Titel eine große Zahl von Kunden über den Microsoft Store zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="88121-109">The combination of these two things means that your Windows10 titles will be able to reach a huge number of customers through the Microsoft Store.</span></span>

<span data-ttu-id="88121-110">Darüber hinaus bietet Windows 10 zahlreiche neue Features, die besonders für Spiele nützlich sind:</span><span class="sxs-lookup"><span data-stu-id="88121-110">In addition, Windows10 offers many new features that are particularly beneficial to games:</span></span>

-   <span data-ttu-id="88121-111">Reduzierte Speicherauslagerung und reduzierte Gesamtgröße des Speichersystems</span><span class="sxs-lookup"><span data-stu-id="88121-111">Reduced memory paging and reduced overall memory system size</span></span>
-   <span data-ttu-id="88121-112">Mit der verbesserten Grafikspeicherverwaltung wird aktiv mehr Speicher für das Spiel im Vordergrund zugeordnet und reserviert.</span><span class="sxs-lookup"><span data-stu-id="88121-112">Improved graphics memory management actively allocates and protects more memory for the foreground game</span></span>

## <a name="uwp-games-with-c-and-directx"></a><span data-ttu-id="88121-113">UWP-Spiele mit C++ und DirectX</span><span class="sxs-lookup"><span data-stu-id="88121-113">UWP Games with C++ and DirectX</span></span>


<span data-ttu-id="88121-114">Echtzeitspiele, die hohe Leistung erfordern, sollten DirectX-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="88121-114">Real-time games requiring high performance should make use of the DirectX APIs.</span></span> <span data-ttu-id="88121-115">DirectX ist eine Sammlung systemeigener APIs zum Erstellen von Spielen und Multimedia-Anwendungen, die hohe Leistung erfordern, z. B. 3D-Spiele.</span><span class="sxs-lookup"><span data-stu-id="88121-115">DirectX is a collection of native APIs for creating games and multimedia applications that require high performance, such as 3D games.</span></span>

## <a name="development-environment"></a><span data-ttu-id="88121-116">Entwicklungsumgebung</span><span class="sxs-lookup"><span data-stu-id="88121-116">Development Environment</span></span>


<span data-ttu-id="88121-117">Um Spiele für UWP zu erstellen, müssen Sie Ihre Entwicklungsumgebung einrichten, indem Sie Visual Studio 2015 oder höher installieren.</span><span class="sxs-lookup"><span data-stu-id="88121-117">To create games for UWP, you'll need to set up your development environment by installing Visual Studio 2015 or later.</span></span> <span data-ttu-id="88121-118">Es wird empfohlen, dass Sie die neueste Version von Visual Studio installieren gibt Ihnen Zugriff auf die neuesten Updates Entwicklung und Sicherheit.</span><span class="sxs-lookup"><span data-stu-id="88121-118">We recommend that you install the latest version of Visual Studio, giving you access to the latest development and security updates.</span></span> <span data-ttu-id="88121-119">Visual Studio können Sie UWP-apps zu erstellen und stellt Tools für die Spielentwicklung bereit:</span><span class="sxs-lookup"><span data-stu-id="88121-119">Visual Studio allows you to create UWP apps and provides tools for game development:</span></span>

-   <span data-ttu-id="88121-120">Visual Studio-Tools für die DX-Spielprogrammierung – Visual Studio stellt Tools zum Erstellen, Bearbeiten, Anzeigen einer Vorschau und Exportieren von Bild-, Modell- und Shaderressourcen bereit.</span><span class="sxs-lookup"><span data-stu-id="88121-120">Visual Studio tools for DX game programming - Visual Studio provides tools for creating, editing, previewing, and exporting image, model, and shader resources.</span></span> <span data-ttu-id="88121-121">Außerdem sind Tools verfügbar, mit denen Sie Ressourcen zur Erstellungszeit konvertieren und DirectX-Grafikcode debuggen können.</span><span class="sxs-lookup"><span data-stu-id="88121-121">There are also tools that you can use to convert resources at build time and debug DirectX graphics code.</span></span> <span data-ttu-id="88121-122">Weitere Informationen finden Sie unter [Visual Studio-Tools für die Spieleprogrammierung](set-up-visual-studio-for-game-development.md).</span><span class="sxs-lookup"><span data-stu-id="88121-122">For more information, see [Use Visual Studio tools for game programming](set-up-visual-studio-for-game-development.md).</span></span>
-   <span data-ttu-id="88121-123">Visual Studio-Grafikdiagnosefeatures – Grafikdiagnosetools stehen nun als optionales Feature in Windows zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="88121-123">Visual Studio graphics diagnostics features - Graphics diagnostic tools are now available from within Windows as an optional feature.</span></span> <span data-ttu-id="88121-124">Mit den Diagnosetools können Sie Grafiken debuggen, Grafikframeanalysen ausführen und die GPU-Nutzung in Echtzeit überwachen.</span><span class="sxs-lookup"><span data-stu-id="88121-124">The diagnostic tools allow you to do graphics debugging, graphics frame analysis, and monitor GPU usage in real time.</span></span> <span data-ttu-id="88121-125">Weitere Informationen finden Sie unter [Tools für die Grafikdiagnose](use-the-directx-runtime-and-visual-studio-graphics-diagnostic-features.md).</span><span class="sxs-lookup"><span data-stu-id="88121-125">For more information, see [Use the DirectX runtime and Visual Studio graphics diagnostic features](use-the-directx-runtime-and-visual-studio-graphics-diagnostic-features.md).</span></span>

<span data-ttu-id="88121-126">Weitere Informationen finden Sie unter „Vorbereiten der Universellen Windows-Plattform und [DirectX-Programmierung](directx-programming.md).</span><span class="sxs-lookup"><span data-stu-id="88121-126">For more information, see Prepare your Universal Windows Platform and [DirectX programming](directx-programming.md).</span></span>

## <a name="getting-started-with-directx-game-project-templates"></a><span data-ttu-id="88121-127">Erste Schritte mit DirectX-Spielprojektvorlagen</span><span class="sxs-lookup"><span data-stu-id="88121-127">Getting Started with DirectX Game Project Templates</span></span>


<span data-ttu-id="88121-128">Nach Einrichtung der Entwicklungsumgebung können Sie eine verwandte DirectX-Projektvorlage zum Erstellen Ihres DirectX-Spiels für UWP verwenden.</span><span class="sxs-lookup"><span data-stu-id="88121-128">After setting up your development environment, you can use one of the DirectX related project templates to create your UWP DirectX game.</span></span> <span data-ttu-id="88121-129">Visual Studio2015 enthält drei Vorlagen für das Erstellen neuer UWP-DirectX-Projekte, **DirectX11-App (Universelles Windows)**, **DirectX12-App (Universelles Windows)** und **DirectX11- und XAML-App (Universelles Windows)**.</span><span class="sxs-lookup"><span data-stu-id="88121-129">Visual Studio 2015 has three templates available for creating new UWP DirectX projects, **DirectX 11 App (Universal Windows)**, **DirectX 12 App (Universal Windows)**, and **DirectX 11 and XAML App (Universal Windows)**.</span></span> <span data-ttu-id="88121-130">Weitere Informationen finden Sie unter [DirectX-Spielprojektvorlagen](user-interface.md).</span><span class="sxs-lookup"><span data-stu-id="88121-130">For more information, see [Create a Universal Windows Platform and DirectX game project from a template](user-interface.md).</span></span>

## <a name="windows-10-apis"></a><span data-ttu-id="88121-131">Windows10-APIs</span><span class="sxs-lookup"><span data-stu-id="88121-131">Windows 10 APIs</span></span>


<span data-ttu-id="88121-132">Windows 10 bietet eine umfangreiche Sammlung von APIs, die für die Spieleentwicklung hilfreich sind.</span><span class="sxs-lookup"><span data-stu-id="88121-132">Windows 10 provides an extensive collection of APIs that are useful for game development.</span></span> <span data-ttu-id="88121-133">Es gibt APIs für praktisch alle Aspekte von Spielen: 3D- und 2D-Grafiken, Audio, Eingabe, Textressourcen, Benutzeroberfläche und Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="88121-133">There are APIs for almost all aspects of games including, 3D Graphics, 2D Graphics, Audio, Input, Text Resources, User Interface, and networking.</span></span>

<span data-ttu-id="88121-134">Es gibt viele verwandte APIs für die Spielentwicklung, nicht für alle Spiele müssen jedoch alle APIs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="88121-134">There are many APIs related to game development, but not all games need to use all of the APIs.</span></span> <span data-ttu-id="88121-135">Einige Spiele werden beispielsweise nur 3D-Grafiken und Direct3D verwenden; andere Spielen werden nur 2D-Grafiken und Direct2D verwenden; und einige Spiele werden möglicherweise beides verwenden.</span><span class="sxs-lookup"><span data-stu-id="88121-135">For example, some games will only use 3D graphics and only make use of Direct3D, some games may only use 2D graphics and only make use of Direct2D, and still other games may make use of both.</span></span> <span data-ttu-id="88121-136">Im folgenden Diagramm werden die mit der Entwicklung von Spielen zusammenhängenden APIs nach Funktionalitätstyp aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="88121-136">The following diagram shows the game development related APIs grouped by functionality type.</span></span>

![Technologien für die Spielplattform](images/gameplatformtechnologies.png)

-   <span data-ttu-id="88121-138">3D-Grafiken – Windows10 unterstützt zwei Sätze von 3D-Grafik-APIs, Direct3D11 und [Direct3D12](https://msdn.microsoft.com/library/windows/desktop/dn899121).</span><span class="sxs-lookup"><span data-stu-id="88121-138">3D Graphics - Windows 10 supports two 3D graphics API sets, Direct3D 11, and [Direct3D 12](https://msdn.microsoft.com/library/windows/desktop/dn899121).</span></span> <span data-ttu-id="88121-139">Mit diesen beiden APIs können 3D- und 2D-Grafiken erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="88121-139">Both of these APIs provide the capability to create 3D and 2D graphics.</span></span> <span data-ttu-id="88121-140">Direct3D 11 und Direct3D 12 werden nicht zusammen verwendet, können jedoch zusammen mit APIs in der 2D-Grafik- und Benutzeroberflächengruppe verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="88121-140">Direct3D 11 and Direct3D 12 are not used together, but either can be used with any of the APIs in the 2D Graphics and UI group.</span></span> <span data-ttu-id="88121-141">Weitere Informationen zum Verwenden der Grafik-APIs in Ihrem Spiel finden Sie unter [Grundlegendes zu 3D-Grafiken für DirectX-Spiele](an-introduction-to-3d-graphics-with-directx.md).</span><span class="sxs-lookup"><span data-stu-id="88121-141">For more information about using the graphics APIs in your game, see [Basic 3D graphics for DirectX games](an-introduction-to-3d-graphics-with-directx.md).</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="88121-142">API</span><span class="sxs-lookup"><span data-stu-id="88121-142">API</span></span></th>
    <th align="left"><span data-ttu-id="88121-143">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="88121-143">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="88121-144">Direct3D12</span><span class="sxs-lookup"><span data-stu-id="88121-144">Direct3D 12</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-145">Direct3D12 stellt die nächste Version von Direct3D vor, der 3D-Grafik-API im Herzen von DirectX.</span><span class="sxs-lookup"><span data-stu-id="88121-145">Direct3D 12 introduces the next version of Direct3D, the 3D graphics API at the heart of DirectX.</span></span> <span data-ttu-id="88121-146">Diese Version von Direct3D ist schneller und effizienter als frühere Versionen von Direct3D.</span><span class="sxs-lookup"><span data-stu-id="88121-146">This version of Direct3D is designed to be faster and more efficient than previous versions of Direct3D.</span></span> <span data-ttu-id="88121-147">Der Kompromiss für die höhere Geschwindigkeit von Direct3D12 besteht darin, dass die Ebene niedrigerer ist. Sie müssen Ihre Grafikressourcen selbst verwalten und über eine umfassendere Grafikprogrammiererfahrung verfügen, um die höhere Geschwindigkeit zu realisieren.</span><span class="sxs-lookup"><span data-stu-id="88121-147">The tradeoff for Direct3D 12's increased speed is that it is lower level and requires you to manage your graphics resources yourself and have more extensive graphics programming experience to realize the increased speed.</span></span></p>
    <p><strong><span data-ttu-id="88121-148">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-148">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-149">Verwenden Sie Direct3D 12, wenn Sie die Leistung Ihres Spiels optimieren müssen und das Spiel CPU-gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="88121-149">Use Direct3D 12 when you need to maximize your game's performance and your game is CPU bound.</span></span></p>
    <p><strong><span data-ttu-id="88121-150">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-150">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-151">Weitere Informationen finden Sie in der <a href="https://msdn.microsoft.com/library/windows/desktop/dn899121">Direct3D 12</a>-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="88121-151">See the <a href="https://msdn.microsoft.com/library/windows/desktop/dn899121">Direct3d 12</a> documentation.</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="88121-152">Direct3D11</span><span class="sxs-lookup"><span data-stu-id="88121-152">Direct3D 11</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-153">Direct3D11 ist die vorherige Version von Direct3D, mit der Sie 3D-Grafiken unter Verwendung einer höheren Ebene der Hardwareabstraktion als bei D3D12 erstellen können.</span><span class="sxs-lookup"><span data-stu-id="88121-153">Direct3D 11 is the previous version of Direct3D and allows you to create 3D graphics using a higher level of hardware abstraction than D3D 12.</span></span></p>
    <p><strong><span data-ttu-id="88121-154">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-154">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-155">Verwenden Sie Direct3D 11, wenn Sie über vorhandenen Direct3D 11-Code verfügen, Ihr Spiel nicht CPU-gebunden ist, oder Sie davon profitieren möchten, dass Ihre Ressourcen verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="88121-155">Use Direct3D 11 if you have existing Direct3D 11 code, your game is not CPU bound, or you want the benefit of having resources managed for you.</span></span></p>
    <p><strong><span data-ttu-id="88121-156">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-156">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-157">Weitere Informationen finden Sie in der <a href="https://msdn.microsoft.com/library/windows/desktop/ff476080">Direct3D 11</a>-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="88121-157">See the <a href="https://msdn.microsoft.com/library/windows/desktop/ff476080">Direct3D 11</a> documentation.</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="88121-158">2D-Grafiken und Benutzeroberfläche – APIs für 2D-Grafiken z.B. Text und Benutzeroberflächen.</span><span class="sxs-lookup"><span data-stu-id="88121-158">2D Graphics and UI - APIs concerning 2D graphics such as text and user interfaces.</span></span> <span data-ttu-id="88121-159">Alle 2D-Grafiken und Benutzeroberflächen-APIs sind optional.</span><span class="sxs-lookup"><span data-stu-id="88121-159">All of the 2D graphics and UI APIs are optional.</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="88121-160">API</span><span class="sxs-lookup"><span data-stu-id="88121-160">API</span></span></th>
    <th align="left"><span data-ttu-id="88121-161">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="88121-161">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="88121-162">Direct2D</span><span class="sxs-lookup"><span data-stu-id="88121-162">Direct2D</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-163">Direct2D ist eine hardwarebeschleunigte 2D-Grafik-API mit unmittelbarem Modus, die das Rendern mit hoher Leistung und in hoher Qualität für 2D-Geometrie, Bitmaps und Text bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="88121-163">Direct2D is a hardware-accelerated, immediate-mode, 2-D graphics API that provides high performance and high-quality rendering for 2-D geometry, bitmaps, and text.</span></span> <span data-ttu-id="88121-164">Die Direct2D-API baut auf Direct3D auf und ist für die Verwendung mit GDI, GDI+ und Direct3D konzipiert.</span><span class="sxs-lookup"><span data-stu-id="88121-164">The Direct2D API is built on Direct3D and is designed to interoperate well with GDI, GDI+, and Direct3D.</span></span></p>
    <p><strong><span data-ttu-id="88121-165">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-165">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-166">Direct2D kann anstelle von Direct3D zum Bereitstellen von Grafiken für reine 2D-Spiele verwendet werden, beispielsweise Side-Scroller oder Brettspiele. Es kann auch mit Direct3D für die vereinfachte Erstellung von 2D-Grafiken in einem 3D-Spiel verwendet werden, beispielsweise einer Benutzeroberfläche oder einer Heads-Up-Anzeige.</span><span class="sxs-lookup"><span data-stu-id="88121-166">Direct2D can be used instead of Direct3D to provide graphics for pure 2D games such as a side-scroller or board game, or can be used with Direct3D to simplify creation of 2D graphics in a 3D game, such as a user interface or heads-up-display.</span></span></p>
    <p><strong><span data-ttu-id="88121-167">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-167">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-168">Weitere Informationen finden Sie in der <a href="https://msdn.microsoft.com/library/windows/desktop/dd370990">Direct2D</a>-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="88121-168">See the <a href="https://msdn.microsoft.com/library/windows/desktop/dd370990">Direct2D</a> documentation.</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="88121-169">DirectWrite</span><span class="sxs-lookup"><span data-stu-id="88121-169">DirectWrite</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-170">DirectWrite stellt zusätzliche Funktionen für das Arbeiten mit Text bereit und kann mit Direct3D oder Direct2D zum Bereitstellen der Textausgabe für Benutzeroberflächen oder andere Bereiche verwendet werden, in denen Text erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="88121-170">DirectWrite provides extra capabilities for working with text and can be used with Direct3D or Direct2D to provide text output for user interfaces or other areas where text is required.</span></span> <span data-ttu-id="88121-171">DirectWrite unterstützt Messung, Zeichnung und Treffererkennung von Text in mehreren Formaten.</span><span class="sxs-lookup"><span data-stu-id="88121-171">DirectWrite supports measuring, drawing, and hit-testing of multi-format text.</span></span> <span data-ttu-id="88121-172">DirectWrite behandelt Text in allen unterstützten Sprachen für globale und lokalisierte Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="88121-172">DirectWrite handles text in all supported languages for global and localized applications.</span></span> <span data-ttu-id="88121-173">DirectWrite stellt außerdem eine API für Glyphenrendering auf niedriger Ebene für Entwickler zur Ausführung von eigenem Layout und eigener Unicode-zu-Glyphen-Verarbeitung bereit.</span><span class="sxs-lookup"><span data-stu-id="88121-173">DirectWrite also provides a low-level glyph rendering API for developers who want to perform their own layout and Unicode-to-glyph processing.</span></span></p>
    <p><strong><span data-ttu-id="88121-174">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-174">When to use</span></span></strong></p>
    <p></p>
    <p><strong><span data-ttu-id="88121-175">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-175">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-176">Weitere Informationen finden Sie in der <a href="https://msdn.microsoft.com/library/windows/desktop/dd368038">DirectWrite</a>-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="88121-176">See the <a href="https://msdn.microsoft.com/library/windows/desktop/dd368038">DirectWrite</a> documentation.</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><span data-ttu-id="88121-177">DirectComposition</span><span class="sxs-lookup"><span data-stu-id="88121-177">DirectComposition</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-178">DirectComposition ist eine Windows-Komponente, die eine Hochleistungs-Bitmapanordnung mit Übergängen, Effekten und Animationen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="88121-178">DirectComposition is a Windows component that enables high-performance bitmap composition with transforms, effects, and animations.</span></span> <span data-ttu-id="88121-179">Anwendungsentwickler können die DirectComposition-API zum Erstellen von visuell ansprechenden Benutzeroberflächen verwenden, die umfassende und fließende animierte Übergänge von einem visuellen Objekt zum nächsten ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="88121-179">Application developers can use the DirectComposition API to create visually engaging user interfaces that feature rich and fluid animated transitions from one visual to another.</span></span></p>
    <p><strong><span data-ttu-id="88121-180">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-180">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-181">DirectComposition wurde für die vereinfachte Anordnung von visuellen Objekten und Erstellen von animierten Übergängen entwickelt.</span><span class="sxs-lookup"><span data-stu-id="88121-181">DirectComposition is designed to simplify the process of composing visuals and creating animated transitions.</span></span> <span data-ttu-id="88121-182">Wenn Ihr Spiel eine komplexe Benutzeroberfläche erfordert, können Sie DirectComposition zum vereinfachten Erstellen und Verwalten der Benutzeroberfläche verwenden.</span><span class="sxs-lookup"><span data-stu-id="88121-182">If your game requires complex user interfaces, you can use DirectComposition to simplify the creation and management of the UI.</span></span></p>
    <p><strong><span data-ttu-id="88121-183">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-183">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-184">Weitere Informationen finden Sie in der <a href="https://msdn.microsoft.com/library/windows/desktop/hh437371">DirectComposition</a>-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="88121-184">See the <a href="https://msdn.microsoft.com/library/windows/desktop/hh437371">DirectComposition</a> documentation.</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="88121-185">Audio – APIs für die Audiowiedergabe und die Anwendung von Audioeffekten.</span><span class="sxs-lookup"><span data-stu-id="88121-185">Audio - APIs concerning playing audio and applying audio effects.</span></span> <span data-ttu-id="88121-186">Informationen zum Verwenden von Audio-APIs in Ihrem Spiel finden Sie unter [Audio für Spiele](working-with-audio-in-your-directx-game.md).</span><span class="sxs-lookup"><span data-stu-id="88121-186">For information about using the audio APIs in your game, see [Audio for games](working-with-audio-in-your-directx-game.md).</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="88121-187">API</span><span class="sxs-lookup"><span data-stu-id="88121-187">API</span></span></th>
    <th align="left"><span data-ttu-id="88121-188">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="88121-188">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="88121-189">XAudio2</span><span class="sxs-lookup"><span data-stu-id="88121-189">XAudio2</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-190">XAudio2 ist eine Low-Level-Audio-API, die eine grundlegende Signalverarbeitung und -abmischung bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="88121-190">XAudio2 is a low-level audio API that provides a foundation for signal processing and mixing.</span></span> <span data-ttu-id="88121-191">XAudio wurde für eine hohe Reaktionsfähigkeit in Bezug auf Audiomodule von Spielen entwickelt. Gleichzeitig können weiterhin benutzerdefinierte Audioeffekte und komplexe Ketten von Audioeffekten und -filtern erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="88121-191">XAudio is designed to be very responsive for game audio engines while maintaining the ability to create custom audio effects and complex chains of audio effects and filters.</span></span></p>
    <p><strong><span data-ttu-id="88121-192">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-192">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-193">Verwenden Sie XAudio2, wenn Ihr Spiel Sounds mit minimalem Aufwand und minimaler Verzögerung wiedergeben muss.</span><span class="sxs-lookup"><span data-stu-id="88121-193">Use XAudio2 when your game needs to play sounds with minimal overhead and delay.</span></span></p>
    <p><strong><span data-ttu-id="88121-194">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-194">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-195">Weitere Informationen finden Sie in der <a href="https://msdn.microsoft.com/library/windows/desktop/hh405049">XAudio2</a>-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="88121-195">See the <a href="https://msdn.microsoft.com/library/windows/desktop/hh405049">XAudio2</a> documentation.</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="88121-196">Media Foundation</span><span class="sxs-lookup"><span data-stu-id="88121-196">Media Foundation</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-197">Microsoft Media Foundation wurde für die Wiedergabe von Mediendateien und Streams (Audio und Video) entwickelt, kann jedoch auch in Spielen verwendet werden, wenn eine Funktionalität auf höherer Ebene als XAudio2 erforderlich ist und der zusätzliche Aufwand akzeptabel ist.</span><span class="sxs-lookup"><span data-stu-id="88121-197">Microsoft Media Foundation is designed for the playback of media files and streams, both audio and video, but can also be used in games when higher level functionality than XAudio2 is required and some additional overhead is acceptable.</span></span></p>
    <p><strong><span data-ttu-id="88121-198">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-198">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-199">Media Foundation ist bei Filmszenen oder nichtinteraktiven Komponenten des Spiels besonders nützlich.</span><span class="sxs-lookup"><span data-stu-id="88121-199">Media foundation is particularly useful for cinematic scenes or non-interactive components of your game.</span></span> <span data-ttu-id="88121-200">Media Foundation ist auch für die Decodierung von Audiodateien für die Wiedergabe mit XAudio2 nützlich.</span><span class="sxs-lookup"><span data-stu-id="88121-200">Media foundation is also useful for decoding audio files for playback using XAudio2.</span></span></p>
    <p><strong><span data-ttu-id="88121-201">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-201">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-202">Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/desktop/ms694197">Microsoft Media Foundation</a>.</span><span class="sxs-lookup"><span data-stu-id="88121-202">See the <a href="https://msdn.microsoft.com/library/windows/desktop/ms694197">Microsoft Media Foundation</a> overview.</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="88121-203">Eingabe – APIs für die Eingabe über Tastatur, Maus, Gamepad und andere Benutzereingabequellen.</span><span class="sxs-lookup"><span data-stu-id="88121-203">Input - APIs concerning input from the keyboard, mouse, gamepad, and other user input sources.</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="88121-204">API</span><span class="sxs-lookup"><span data-stu-id="88121-204">API</span></span></th>
    <th align="left"><span data-ttu-id="88121-205">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="88121-205">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="88121-206">XInput</span><span class="sxs-lookup"><span data-stu-id="88121-206">XInput</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-207">Mit der XInput-Gamecontroller-API können Anwendungen Eingaben von Gamecontrollern erhalten.</span><span class="sxs-lookup"><span data-stu-id="88121-207">The XInput Game Controller API enables applications to receive input from game controllers.</span></span></p>
    <p><strong><span data-ttu-id="88121-208">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-208">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-209">Wenn Ihr Spiel die Gamepadeingabe unterstützen muss und Sie über vorhandenen XInput-Code verfügen, können Sie weiterhin XInput verwenden.</span><span class="sxs-lookup"><span data-stu-id="88121-209">If your game needs to support gampad input and you have existing XInput code, you can continue to make use of XInput.</span></span> <span data-ttu-id="88121-210">XInput wurde durch Windows.Gaming.Input für UWP ersetzt, und Sie sollten beim Schreiben von neuem Eingabecode Windows.Gaming.Input anstelle von XInput verwenden.</span><span class="sxs-lookup"><span data-stu-id="88121-210">XInput has been replaced by Windows.Gaming.Input for UWP, and if you're writing new input code, you should use Windows.Gaming.Input instead of XInput.</span></span></p>
    <p><strong><span data-ttu-id="88121-211">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-211">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-212">Weitere Informationen finden Sie in der <a href="https://msdn.microsoft.com/library/windows/desktop/hh405053">XInput</a>-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="88121-212">See the <a href="https://msdn.microsoft.com/library/windows/desktop/hh405053">XInput</a> documentation.</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="88121-213">Windows.Gaming.Input</span><span class="sxs-lookup"><span data-stu-id="88121-213">Windows.Gaming.Input</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-214">Die Windows.Gaming.Input-API ersetzt XInput und bietet die gleiche Funktionalität mit den folgenden Vorteilen gegenüber Xinput:</span><span class="sxs-lookup"><span data-stu-id="88121-214">The Windows.Gaming.Input API replaces XInput and provides the same functionality with the following advantages over Xinput:</span></span></p>
    <ul>
    <li><span data-ttu-id="88121-215">Geringere Ressourcenverwendung</span><span class="sxs-lookup"><span data-stu-id="88121-215">Lower resource usage</span></span></li>
    <li><span data-ttu-id="88121-216">Geringere Latenz des API-Aufrufs zum Abrufen von Eingaben</span><span class="sxs-lookup"><span data-stu-id="88121-216">Lower API call latency for retrieving input</span></span></li>
    <li><span data-ttu-id="88121-217">Die Möglichkeit, mit mehr als 4 Gamepads gleichzeitig zu arbeiten</span><span class="sxs-lookup"><span data-stu-id="88121-217">The ability to work with more than 4 gamepads at once</span></span></li>
    <li><span data-ttu-id="88121-218">Die Möglichkeit zum Zugreifen auf zusätzliche Xbox One-Gamepadfeatures, z.B. Triggervibrationsmotoren.</span><span class="sxs-lookup"><span data-stu-id="88121-218">The ability to access additional Xbox One gamepad features, such as the trigger vibration motors</span></span></li>
    <li><span data-ttu-id="88121-219">Die Möglichkeit, beim Herstellen oder Trennen einer Verbindung durch ein Ereignis anstelle von Abruf benachrichtigt zu werden.</span><span class="sxs-lookup"><span data-stu-id="88121-219">The ability to be notified when controllers connect/disconnect via event instead of polling</span></span></li>
    <li><span data-ttu-id="88121-220">Die Möglichkeit zum Zuweisen der Eingabe an einen bestimmten Benutzer (Windows.System.User)</span><span class="sxs-lookup"><span data-stu-id="88121-220">The ability to attribute input to a specific user (Windows.System.User)</span></span></li>
    </ul>
    <p><strong><span data-ttu-id="88121-221">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-221">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-222">Wenn Ihr Spiel Eingaben über ein Gamepad unterstützen muss und einen vorhandenen XInput-Code nicht verwendet, oder wenn Sie einen der oben genannten Vorteile nutzen möchten, sollten Sie Windows.Gaming.Input verwenden.</span><span class="sxs-lookup"><span data-stu-id="88121-222">If your game needs to support gamepad input and is not using existing XInput code or you need one of the benefits listed above, you should make use of Windows.Gaming.Input.</span></span></p>
    <p><strong><span data-ttu-id="88121-223">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-223">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-224">Weitere Informationen finden Sie in der Dokumentation für <a href="https://msdn.microsoft.com/library/windows/apps/dn707817">Windows.Gaming.Input</a>.</span><span class="sxs-lookup"><span data-stu-id="88121-224">See the <a href="https://msdn.microsoft.com/library/windows/apps/dn707817">Windows.Gaming.Input</a> documentation.</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><span data-ttu-id="88121-225">Windows.UI.Core.CoreWindow</span><span class="sxs-lookup"><span data-stu-id="88121-225">Windows.UI.Core.CoreWindow</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-226">Mit der Windows.UI.Core.CoreWindow-Klasse können Sie nachverfolgen, wann der Zeiger gedrückt oder verschoben wird oder wann eine Taste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="88121-226">The Windows.UI.Core.CoreWindow class provides events for tracking pointer presses and movement, and key down and key up events.</span></span></p>
    <p><strong><span data-ttu-id="88121-227">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-227">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-228">Verwenden Sie die Windows.UI.Core.CoreWindows-Ereignisse, wenn Sie nachverfolgen möchten, wann die Maus oder eine Taste in Ihrem Spiel gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="88121-228">Use Windows.UI.Core.CoreWindows events when you need to track the mouse or key presses in your game.</span></span></p>
    <p><strong><span data-ttu-id="88121-229">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-229">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-230">Weitere Informationen zum Verwenden der Maus oder Tastatur in Ihrem Spiel finden Sie unter <a href="https://docs.microsoft.com/windows/uwp/gaming/tutorial--adding-move-look-controls-to-your-directx-game">Bewegungs-/Blicksteuerungen für Spiele</a>.</span><span class="sxs-lookup"><span data-stu-id="88121-230">See <a href="https://docs.microsoft.com/windows/uwp/gaming/tutorial--adding-move-look-controls-to-your-directx-game">Move-look controls for games</a> for more information about using the mouse or keyboard in your game.</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="88121-231">Math-APIs – APIs zum Vereinfachen häufig verwendeter mathematischer Vorgänge.</span><span class="sxs-lookup"><span data-stu-id="88121-231">Math - APIs concerning simplifying commonly used mathematical operations.</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="88121-232">API</span><span class="sxs-lookup"><span data-stu-id="88121-232">API</span></span></th>
    <th align="left"><span data-ttu-id="88121-233">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="88121-233">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="88121-234">DirectXMath</span><span class="sxs-lookup"><span data-stu-id="88121-234">DirectXMath</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-235">Die DirectXMath-API bietet SIMD-freundliche C++-Typen und Funktionen für allgemeine lineare Algebra- und mathematische Grafikvorgänge für Spiele.</span><span class="sxs-lookup"><span data-stu-id="88121-235">The DirectXMath API provides SIMD-friendly C++ types and functions for common linear algebra and graphics math operations common to games.</span></span></p>
    <p><strong><span data-ttu-id="88121-236">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-236">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-237">Die Verwendung von DirectXMath ist optional und vereinfacht allgemeine mathematische Vorgänge.</span><span class="sxs-lookup"><span data-stu-id="88121-237">Use of DirectXMath is optional and simplifies common mathematical operations.</span></span></p>
    <p><strong><span data-ttu-id="88121-238">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-238">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-239">Weitere Informationen finden Sie in der <a href="https://msdn.microsoft.com/library/windows/desktop/hh437833">DirectXMath</a>-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="88121-239">See the <a href="https://msdn.microsoft.com/library/windows/desktop/hh437833">DirectXMath</a> documentation.</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="88121-240">Netzwerke – APIs für die Kommunikation mit anderen Computern und Geräten entweder über das Internet oder private Netzwerke.</span><span class="sxs-lookup"><span data-stu-id="88121-240">Networking - APIs concerning communicating with other computers and devices over either the Internet or private networks.</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="88121-241">API</span><span class="sxs-lookup"><span data-stu-id="88121-241">API</span></span></th>
    <th align="left"><span data-ttu-id="88121-242">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="88121-242">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="88121-243">Windows.Networking.Sockets</span><span class="sxs-lookup"><span data-stu-id="88121-243">Windows.Networking.Sockets</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-244">Der Windows.Networking.Sockets-Namespace stellt TCP- und UDP-Sockets bereit, die eine zuverlässige bzw. nicht zuverlässige Netzwerkkommunikation ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="88121-244">The Windows.Networking.Sockets namespace provides TCP and UDP sockets that allow reliable or unreliable network communication.</span></span></p>
    <p><strong><span data-ttu-id="88121-245">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-245">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-246">Verwenden Sie Windows.Networking.Sockets, wenn Ihr Spiel mit anderen Computern und Geräten über das Netzwerk kommunizieren muss.</span><span class="sxs-lookup"><span data-stu-id="88121-246">Use Windows.Networking.Sockets if your game needs to communicate with other computers or devices over the network.</span></span></p>
    <p><strong><span data-ttu-id="88121-247">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-247">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-248">Weitere Informationen finden Sie unter <a href="https://docs.microsoft.com/windows/uwp/gaming/work-with-networking-in-your-directx-game">Netzwerk für Spiele</a>.</span><span class="sxs-lookup"><span data-stu-id="88121-248">See <a href="https://docs.microsoft.com/windows/uwp/gaming/work-with-networking-in-your-directx-game">Work with networking in your game</a>.</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="88121-249">Windows.Web.HTTP</span><span class="sxs-lookup"><span data-stu-id="88121-249">Windows.Web.HTTP</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-250">Der Windows.Web.HTTP-Namespace stellt eine zuverlässige Verbindung mit HTTP-Servern bereit, die für den Zugriff auf eine Website verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="88121-250">The Windows.Web.HTTP namespace provides a reliable connection to HTTP servers that can be used to access a web site.</span></span></p>
    <p><strong><span data-ttu-id="88121-251">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-251">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-252">Verwenden Sie Windows.Web.HTTP, wenn Ihr Spiel zum Abrufen oder Speichern von Informationen auf eine Website zugreifen muss.</span><span class="sxs-lookup"><span data-stu-id="88121-252">Use Windows.Web.HTTP when your game needs to access a web site to retrieve or store information.</span></span></p>
    <p><strong><span data-ttu-id="88121-253">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-253">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-254">Weitere Informationen finden Sie unter <a href="https://docs.microsoft.com/windows/uwp/gaming/work-with-networking-in-your-directx-game">Netzwerk für Spiele</a>.</span><span class="sxs-lookup"><span data-stu-id="88121-254">See <a href="https://docs.microsoft.com/windows/uwp/gaming/work-with-networking-in-your-directx-game">Work with networking in your game</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="88121-255">Support-Dienstprogramme - Bibliotheken, die auf Grundlage von Windows 10-APIs entwickelt wurden.</span><span class="sxs-lookup"><span data-stu-id="88121-255">Support Utilities - Libraries that build on the Windows 10 APIs.</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="88121-256">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="88121-256">Library</span></span></th>
    <th align="left"><span data-ttu-id="88121-257">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="88121-257">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="88121-258">DirectX-Toolkit</span><span class="sxs-lookup"><span data-stu-id="88121-258">DirectX Tool Kit</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-259">Das DirectX-Toolkit (DirectXTK) ist eine Sammlung von Hilfsklassen für DirectX 11.x-Code in C++.</span><span class="sxs-lookup"><span data-stu-id="88121-259">The DirectX Tool Kit (DirectXTK) is a collection of helper classes for writing DirectX 11.x code in C++.</span></span></p>
    <p><strong><span data-ttu-id="88121-260">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-260">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-261">Verwenden Sie das DirectX-Toolkit, wenn Sie C++-Entwickler und auf der Suche nach einem modernen Ersatz für älteren D3DX-Hilfsprogrammcode sind, oder ein XNA Game Studio-Entwickler sind, der zu systemeigenen C++ wechselt.</span><span class="sxs-lookup"><span data-stu-id="88121-261">Use the DirectX Tool Kit if you're a C++ developer looking for a modern replacement to the legacy D3DX utility code or you're an XNA Game Studio developer transitioning to native C++.</span></span></p>
    <p><strong><span data-ttu-id="88121-262">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-262">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-263">Weitere Informationen finden Sie unter der DirectX-Toolkit-Projektseite <a href="https://github.com/Microsoft/DirectXTK">https://github.com/Microsoft/DirectXTK</a>.</span><span class="sxs-lookup"><span data-stu-id="88121-263">See the DirectX Tool Kit project page, <a href="https://github.com/Microsoft/DirectXTK">https://github.com/Microsoft/DirectXTK</a>.</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="88121-264">Win2D</span><span class="sxs-lookup"><span data-stu-id="88121-264">Win2D</span></span></td>
    <td align="left"><p><span data-ttu-id="88121-265">Win2D ist eine einfach zu verwendende Windows-Runtime-API für 2D-Grafikrendering im unmittelbaren Modus.</span><span class="sxs-lookup"><span data-stu-id="88121-265">Win2D is an easy-to-use Windows Runtime API for immediate mode 2D graphics rendering.</span></span></p>
    <p><strong><span data-ttu-id="88121-266">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="88121-266">When to use</span></span></strong></p>
    <p><span data-ttu-id="88121-267">Verwenden Sie Win2D, wenn Sie C++-Entwickler sind und einen einfacher zu verwendenden WinRT-Wrapper für Direct2D und DirectWrite benötigen, oder C#-Entwickler sind und Direct2D und DirectWrite verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="88121-267">Use Win2D if you're a C++ developer and want an easier to use WinRT wrapper for Direct2D and DirectWrite, or you're a C# developer wanting to use Direct2D and DirectWrite.</span></span></p>
    <p><strong><span data-ttu-id="88121-268">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88121-268">For more information</span></span></strong></p>
    <p><span data-ttu-id="88121-269">Weitere Informationen finden Sie unter der Win2D-Projektseite <a href="https://github.com/Microsoft/Win2D">https://github.com/Microsoft/Win2D</a>.</span><span class="sxs-lookup"><span data-stu-id="88121-269">See the Win2D project page, <a href="https://github.com/Microsoft/Win2D">https://github.com/Microsoft/Win2D</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

## <a name="xbox-live-services"></a><span data-ttu-id="88121-270">Xbox Live-Dienste</span><span class="sxs-lookup"><span data-stu-id="88121-270">Xbox Live Services</span></span>

<span data-ttu-id="88121-271">Das [Xbox Live Creators-Programm](https://developer.microsoft.com/games/xbox/xboxlive/creator) kann jeder Entwickler Xbox Live in seine UWP-Spiele integrieren und auf Xbox One und Windows 10 veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="88121-271">The [Xbox Live Creators Program](https://developer.microsoft.com/games/xbox/xboxlive/creator) allows any developer to integrate Xbox Live into their UWP game and publish to Xbox One and Windows10.</span></span> <span data-ttu-id="88121-272">Integrieren Sie soziale Xbox Live-Funktionen wie Anmelden, Präsenzinformationen, Ranglisten und mehr mit minimaler Entwicklungszeit in Ihre Titel.</span><span class="sxs-lookup"><span data-stu-id="88121-272">Integrate Xbox Live social experiences such as sign-in, presence, leaderboards, and more into your title, with minimal development time.</span></span> <span data-ttu-id="88121-273">Die sozialen Xbox Live-Features wurden entwickelt, damit Sie Ihre Zielgruppe organisch auf bis zu 55Millionen aktive Spieler erweitern können.</span><span class="sxs-lookup"><span data-stu-id="88121-273">Xbox Live social features are designed to organically grow your audience, spreading awareness to over 55 million active gamers.</span></span>

<span data-ttu-id="88121-274">Treten Sie dem [ID@Xbox](http://www.xbox.com/developers/id) bei, wenn Sie Zugriff auf weitere Xbox Live-Funktionen wünschen, dedizierte Marketing- und Entwicklungsunterstützung benötigen oder im allgemeinen Xbox One-Store vertreten sein möchten.</span><span class="sxs-lookup"><span data-stu-id="88121-274">If you want access to even more Xbox Live capabilities, dedicated marketing and development support, and the chance to be featured in the main Xbox One store, apply to the [ID@Xbox](http://www.xbox.com/developers/id) program.</span></span> <span data-ttu-id="88121-275">Um festzustellen, welche Features für das Xbox Live Creators-Programm und das ID@Xbox-Programm verfügbar sind, wechseln Sie auf die [Tabelle der Features](../xbox-live/developer-program-overview.md#feature-table).</span><span class="sxs-lookup"><span data-stu-id="88121-275">To see which features are available to the Xbox Live Creators Program and ID@Xbox program, see the [Feature table](../xbox-live/developer-program-overview.md#feature-table).</span></span>

<span data-ttu-id="88121-276">Weitere Informationen finden Sie unter [Hinzufügen von Xbox Live zu Ihrem Spiel](e2e.md#adding-xbox-live-to-your-game).</span><span class="sxs-lookup"><span data-stu-id="88121-276">For more info, go to [Adding Xbox Live to your game](e2e.md#adding-xbox-live-to-your-game).</span></span>

##  <a name="alternatives-to-writing-games-with-directx-and-uwp"></a><span data-ttu-id="88121-277">Alternativen zum Schreiben von Spielen mit DirectX und UWP</span><span class="sxs-lookup"><span data-stu-id="88121-277">Alternatives to writing games with DirectX and UWP</span></span>


### <a name="uwp-games-without-directx"></a><span data-ttu-id="88121-278">UWP-Spiele ohne DirectX</span><span class="sxs-lookup"><span data-stu-id="88121-278">UWP Games without DirectX</span></span>

<span data-ttu-id="88121-279">Einfachere Spiele mit minimalem Leistungsanforderungen, z.B. Kartenspiele oder Brettspiele, können ohne DirectX und müssen nicht unbedingt in C++ geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="88121-279">Simpler games with minimal performance requirements, such as card games or board games, can be written without DirectX and don't necessarily need to be written in C++.</span></span> <span data-ttu-id="88121-280">Bei dieser Art von Spielen können alle von UWP unterstützten Sprachen verwendet werden, z.B. C#, Visual Basic, C++ und HTML/JavaScript.</span><span class="sxs-lookup"><span data-stu-id="88121-280">These sort of games can make use of any of the languages supported by UWP such as C#, Visual Basic, C++, and HTML/JavaScript.</span></span> <span data-ttu-id="88121-281">Wenn Ihr Spiel weder eine hohe Leistung noch rechenintensive Grafiken erfordert, sollten Sie sich das [Beispiel für ein JavaScript- und HTML5-Fingereingabespiel](http://code.msdn.microsoft.com/windowsapps/JavaScript-and-HTML5-touch-d96f6031) ansehen.</span><span class="sxs-lookup"><span data-stu-id="88121-281">If performance and intensive graphics are not a requirement for your game, checkout [JavaScript and HTML5 touch game sample](http://code.msdn.microsoft.com/windowsapps/JavaScript-and-HTML5-touch-d96f6031) as an example.</span></span>

### <a name="game-engines"></a><span data-ttu-id="88121-282">Spielengines</span><span class="sxs-lookup"><span data-stu-id="88121-282">Game Engines</span></span>

<span data-ttu-id="88121-283">Eine Alternative zum Schreiben eigener Spielemodule mithilfe der Windows-APIs für die Entwicklung von Spielen stellen die zahlreichen qualitativ hochwertigen Spielemodule dar, die auf den Windows-APIs für die Entwicklung von Spielen basieren und für die Entwicklung von Spielen auf Windows-Plattformen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="88121-283">As an alternative to writing your own game engine using the Windows game development APIs, many high quality game engines that build on the Windows game development APIs are available for developing games on Windows platforms.</span></span> <span data-ttu-id="88121-284">Wenn Sie eine Spielengine oder Bibliothek in Erwägung ziehen, können Sie zwischen den folgenden Möglichkeiten wählen:</span><span class="sxs-lookup"><span data-stu-id="88121-284">When considering a game engine or library, you have multiple options:</span></span>

-   <span data-ttu-id="88121-285">Vollständige Spielengine – Eine vollständige Spielengine umfasst die meisten bzw. alle Windows 10-APIs, die Sie zum Schreiben einer eigenen Spielengine verwenden würden, z.B. Grafik, Eingabe und Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="88121-285">Full game engine - A full game engine encapsulates most or all of the Windows 10 APIs you would use when writing a game engine from scratch, such as graphics, audio, input, and networking.</span></span> <span data-ttu-id="88121-286">Vollständige Spielengines können auch Spiellogikfunktionalität bereitstellen, z.B. künstliche Intelligenz und Pfadsuche.</span><span class="sxs-lookup"><span data-stu-id="88121-286">Full game engines may also provide game logic functionality such as artificial intelligence and pathfinding.</span></span>
-   <span data-ttu-id="88121-287">Grafikengine – Grafikengines umfassen Windows 10-Grafik-APIs, verwalten Grafikressourcen und unterstützen zahlreiche Modell- und Weltformate.</span><span class="sxs-lookup"><span data-stu-id="88121-287">Graphics engine - Graphics engines encapsulate the Windows 10 graphics APIs, manage graphics resources, and support a variety of model and world formats.</span></span>
-   <span data-ttu-id="88121-288">Audioengine – Audioengines umfassen Windows 10-Audio-APIs, verwalten Audioressourcen und stellen erweiterte Audiowiedergabe und -Effekte bereit.</span><span class="sxs-lookup"><span data-stu-id="88121-288">Audio engine - Audio engines encapsulate the Windows 10 audio APIs, manage audio resources, and provide advanced audio processing and effects.</span></span>
-   <span data-ttu-id="88121-289">Netzwerkengine – Netzwerkengines umfassen Windows 10-Netzwerk-APIs zum Hinzufügen von Peer-zu-Peer- oder serverbasierter Multiplayerunterstützung zu Ihrem Spiel und enthalten ggf. erweiterte Netzwerkfunktionalität zur Unterstützung einer großen Anzahl von Spielern.</span><span class="sxs-lookup"><span data-stu-id="88121-289">Network engine - Network engines encapsulate Windows 10 networking APIs for adding peer-to-peer or server-based multiplayer support to your game, and may include advanced networking functionality to support large numbers of players.</span></span>
-   <span data-ttu-id="88121-290">Engine für künstliche Intelligenz und Pfadsuche – Engines für künstliche Intelligenz und Pfadsuche stellen ein Framework zur Steuerung des Agentverhaltens in einem Spiel bereit.</span><span class="sxs-lookup"><span data-stu-id="88121-290">Artificial intelligence and pathfinding engine - AI and pathfinding engines provide a framework for controlling the behavior of agents in your game.</span></span>
-   <span data-ttu-id="88121-291">Engines für besondere Zwecke – Es stehen unterschiedliche weitere Engines zur Bewältigung von nahezu allen möglichen Spielentwicklungsaufgaben zur Verfügung, z.B. Erstellen von Inventarsystemen und Dialogstrukturen.</span><span class="sxs-lookup"><span data-stu-id="88121-291">Special purpose engines - A variety of additional engines exist for handling almost any game development related task you might run into, such as creating inventory systems and dialog trees.</span></span>

## <a name="submitting-a-game-to-the-store"></a><span data-ttu-id="88121-292">Übermitteln eines Spiels an den Store</span><span class="sxs-lookup"><span data-stu-id="88121-292">Submitting a game to the Store</span></span>


<span data-ttu-id="88121-293">Wenn Ihr Spiel zur Veröffentlichung bereit steht, müssen Sie ein Entwicklerkonto erstellen und Ihr Spiel an den Microsoft Store übermitteln.</span><span class="sxs-lookup"><span data-stu-id="88121-293">Once you’re ready to publish your game, you’ll need to create a developer account and submit your game to the Microsoft Store.</span></span>

<span data-ttu-id="88121-294">Informationen zum Übermitteln Ihres Spiels an den Microsoft Store finden Sie unter [Übermitteln und Veröffentlichen Ihres Spiels](e2e.md#submitting-and-publishing-your-game).</span><span class="sxs-lookup"><span data-stu-id="88121-294">For information about submitting your game to the Microsoft Store, see [Submitting and publishing your game](e2e.md#submitting-and-publishing-your-game).</span></span>

 

 




