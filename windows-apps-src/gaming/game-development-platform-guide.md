---
author: mtoepke
title: "Spieletechnologien für UWP-Apps"
description: "Dieses Handbuch enthält Informationen über verfügbare Technologien zur Entwicklung von Spielen für die Universelle Windows-Plattform (UWP)."
ms.assetid: bc4d4648-0d6e-efbb-7608-80bd09decd6e
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Technologie, DirectX
ms.openlocfilehash: afbab8d6e38bad7c72d4863f97d90b7eb8ff4cac
ms.sourcegitcommit: ae20971c4c8276034cd22fd7e10b0e3ddfddf480
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2017
---
# <a name="game-technologies-for-uwp-apps"></a><span data-ttu-id="e5612-104">Spieletechnologien für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="e5612-104">Game technologies for UWP apps</span></span>


<span data-ttu-id="e5612-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="e5612-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="e5612-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="e5612-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="e5612-107">Dieses Handbuch enthält Informationen über verfügbare Technologien für die Entwicklung von Spielen für die Universelle Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="e5612-107">In this guide, you'll learn about the technologies available for developing Universal Windows Platform (UWP) games.</span></span>

##  <a name="benefits-of-windows-10-for-game-development"></a><span data-ttu-id="e5612-108">Vorteile von Windows10 für die Spielentwicklung</span><span class="sxs-lookup"><span data-stu-id="e5612-108">Benefits of Windows 10 for game development</span></span>


<span data-ttu-id="e5612-109">Mit der Einführung von UWP in Windows10 können Ihre Windows10-Titel auf allen Microsoft-Plattformen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e5612-109">With the introduction of UWP in Windows 10, your Windows 10 titles will be able to span all of the Microsoft platforms.</span></span> <span data-ttu-id="e5612-110">Dank der kostenlosen Migration von früheren Windows-Versionen wird die Zahl der Windows10-Clients ständig zunehmen.</span><span class="sxs-lookup"><span data-stu-id="e5612-110">With free migration from previous versions of Windows, there is a steadily increasing number of Windows 10 clients.</span></span> <span data-ttu-id="e5612-111">Die Kombination dieser beiden Umstände bedeutet, dass Ihre Windows10-Titel über den Windows Store eine große Zahl von Kunden erreichen werden.</span><span class="sxs-lookup"><span data-stu-id="e5612-111">The combination of these two things means that your Windows 10 titles will be able to reach a huge number of customers through the Windows Store.</span></span>

<span data-ttu-id="e5612-112">Darüber hinaus bietet Windows10 zahlreiche neue Features, die besonders für Spiele nützlich sind:</span><span class="sxs-lookup"><span data-stu-id="e5612-112">In addition, Windows 10 offers many new features that are particularly beneficial to games:</span></span>

-   <span data-ttu-id="e5612-113">Reduzierte Speicherauslagerung und reduzierte Gesamtgröße des Speichersystems</span><span class="sxs-lookup"><span data-stu-id="e5612-113">Reduced memory paging and reduced overall memory system size</span></span>
-   <span data-ttu-id="e5612-114">Mit der verbesserten Grafikspeicherverwaltung wird aktiv mehr Speicher für das Spiel im Vordergrund zugeordnet und reserviert.</span><span class="sxs-lookup"><span data-stu-id="e5612-114">Improved graphics memory management actively allocates and protects more memory for the foreground game</span></span>

## <a name="uwp-games-with-c-and-directx"></a><span data-ttu-id="e5612-115">UWP-Spiele mit C++ und DirectX</span><span class="sxs-lookup"><span data-stu-id="e5612-115">UWP Games with C++ and DirectX</span></span>


<span data-ttu-id="e5612-116">Echtzeitspiele, die hohe Leistung erfordern, sollten DirectX-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5612-116">Real-time games requiring high performance should make use of the DirectX APIs.</span></span> <span data-ttu-id="e5612-117">DirectX ist eine Sammlung systemeigener APIs zum Erstellen von Spielen und Multimedia-Anwendungen, die hohe Leistung erfordern, z. B. 3D-Spiele.</span><span class="sxs-lookup"><span data-stu-id="e5612-117">DirectX is a collection of native APIs for creating games and multimedia applications that require high performance, such as 3D games.</span></span>

## <a name="development-environment"></a><span data-ttu-id="e5612-118">Entwicklungsumgebung</span><span class="sxs-lookup"><span data-stu-id="e5612-118">Development Environment</span></span>


<span data-ttu-id="e5612-119">Um Spiele für UWP zu erstellen, müssen Sie Ihre Entwicklungsumgebung einrichten, indem Sie Visual Studio 2015 oder höher installieren.</span><span class="sxs-lookup"><span data-stu-id="e5612-119">To create games for UWP, you'll need to set up your development environment by installing Visual Studio 2015 and later.</span></span> <span data-ttu-id="e5612-120">Visual Studio2015 ermöglicht Ihnen das Erstellen von UWP-Apps und stellt Tools für die Spielentwicklung bereit:</span><span class="sxs-lookup"><span data-stu-id="e5612-120">Visual Studio 2015 allows you to create UWP apps and provides tools for game development:</span></span>

-   <span data-ttu-id="e5612-121">Visual Studio-Tools für die DX-Spielprogrammierung – Visual Studio stellt Tools zum Erstellen, Bearbeiten, Anzeigen einer Vorschau und Exportieren von Bild-, Modell- und Shaderressourcen bereit.</span><span class="sxs-lookup"><span data-stu-id="e5612-121">Visual Studio tools for DX game programming - Visual Studio provides tools for creating, editing, previewing, and exporting image, model, and shader resources.</span></span> <span data-ttu-id="e5612-122">Außerdem sind Tools verfügbar, mit denen Sie Ressourcen zur Erstellungszeit konvertieren und DirectX-Grafikcode debuggen können.</span><span class="sxs-lookup"><span data-stu-id="e5612-122">There are also tools that you can use to convert resources at build time and debug DirectX graphics code.</span></span> <span data-ttu-id="e5612-123">Weitere Informationen finden Sie unter [Visual Studio-Tools für die Spieleprogrammierung](set-up-visual-studio-for-game-development.md).</span><span class="sxs-lookup"><span data-stu-id="e5612-123">For more information, see [Use Visual Studio tools for game programming](set-up-visual-studio-for-game-development.md).</span></span>
-   <span data-ttu-id="e5612-124">Visual Studio-Grafikdiagnosefeatures – Grafikdiagnosetools stehen nun als optionales Feature in Windows zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e5612-124">Visual Studio graphics diagnostics features - Graphics diagnostic tools are now available from within Windows as an optional feature.</span></span> <span data-ttu-id="e5612-125">Mit den Diagnosetools können Sie Grafiken debuggen, Grafikframeanalysen ausführen und die GPU-Nutzung in Echtzeit überwachen.</span><span class="sxs-lookup"><span data-stu-id="e5612-125">The diagnostic tools allow you to do graphics debugging, graphics frame analysis, and monitor GPU usage in real time.</span></span> <span data-ttu-id="e5612-126">Weitere Informationen finden Sie unter [Tools für die Grafikdiagnose](use-the-directx-runtime-and-visual-studio-graphics-diagnostic-features.md).</span><span class="sxs-lookup"><span data-stu-id="e5612-126">For more information, see [Use the DirectX runtime and Visual Studio graphics diagnostic features](use-the-directx-runtime-and-visual-studio-graphics-diagnostic-features.md).</span></span>

<span data-ttu-id="e5612-127">Weitere Informationen finden Sie unter „Vorbereiten der Universellen Windows-Plattform und [DirectX-Programmierung](directx-programming.md).</span><span class="sxs-lookup"><span data-stu-id="e5612-127">For more information, see Prepare your Universal Windows Platform and [DirectX programming](directx-programming.md).</span></span>

## <a name="getting-started-with-directx-game-project-templates"></a><span data-ttu-id="e5612-128">Erste Schritte mit DirectX-Spielprojektvorlagen</span><span class="sxs-lookup"><span data-stu-id="e5612-128">Getting Started with DirectX Game Project Templates</span></span>


<span data-ttu-id="e5612-129">Nach Einrichtung der Entwicklungsumgebung können Sie eine verwandte DirectX-Projektvorlage zum Erstellen Ihres DirectX-Spiels für UWP verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5612-129">After setting up you development environment, you can use one of the DirectX related project templates to create your UWP DirectX game.</span></span> <span data-ttu-id="e5612-130">Visual Studio2015 enthält drei Vorlagen für das Erstellen neuer UWP-DirectX-Projekte, **DirectX11-App (Universelles Windows)**, **DirectX12-App (Universelles Windows)** und **DirectX11- und XAML-App (Universelles Windows)**.</span><span class="sxs-lookup"><span data-stu-id="e5612-130">Visual Studio 2015 has three templates available for creating new UWP DirectX projects, **DirectX 11 App (Universal Windows)**, **DirectX 12 App (Universal Windows)**, and **DirectX 11 and XAML App (Universal Windows)**.</span></span> <span data-ttu-id="e5612-131">Weitere Informationen finden Sie unter [DirectX-Spielprojektvorlagen](user-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e5612-131">For more information, see [Create a Universal Windows Platform and DirectX game project from a template](user-interface.md).</span></span>

## <a name="windows-10-apis"></a><span data-ttu-id="e5612-132">Windows10-APIs</span><span class="sxs-lookup"><span data-stu-id="e5612-132">Windows 10 APIs</span></span>


<span data-ttu-id="e5612-133">Windows 10 bietet eine umfangreiche Sammlung von APIs, die für die Spieleentwicklung hilfreich sind.</span><span class="sxs-lookup"><span data-stu-id="e5612-133">Windows 10 provides a an extensive collection of APIs that are useful for game development.</span></span> <span data-ttu-id="e5612-134">Es gibt APIs für praktisch alle Aspekte von Spielen: 3D- und 2D-Grafiken, Audio, Eingabe, Textressourcen, Benutzeroberfläche und Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="e5612-134">There are APIs for almost all aspects of games including, 3D Graphics, 2D Graphics, Audio, Input, Text Resources, User Interface, and networking.</span></span>

<span data-ttu-id="e5612-135">Es gibt viele verwandte APIs für die Spielentwicklung, nicht für alle Spiele müssen jedoch alle APIs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e5612-135">There are many APIs related to game development, but not all games need to use all of the APIs.</span></span> <span data-ttu-id="e5612-136">Einige Spiele werden beispielsweise nur 3D-Grafiken und Direct3D verwenden; andere Spielen werden nur 2D-Grafiken und Direct2D verwenden; und einige Spiele werden möglicherweise beides verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5612-136">For example, some games will only use 3D graphics and only make use of Direct3D, some games may only use 2D graphics and only make use of Direct2D, and still other games may make use of both.</span></span> <span data-ttu-id="e5612-137">Im folgenden Diagramm werden die mit der Entwicklung von Spielen zusammenhängenden APIs nach Funktionalitätstyp aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="e5612-137">The following diagram shows the game development related APIs grouped by functionality type.</span></span>

![Technologien für die Spielplattform](images/gameplatformtechnologies.png)

-   <span data-ttu-id="e5612-139">3D-Grafiken – Windows10 unterstützt zwei Sätze von 3D-Grafik-APIs, Direct3D11 und [Direct3D12](https://msdn.microsoft.com/library/windows/desktop/dn899121).</span><span class="sxs-lookup"><span data-stu-id="e5612-139">3D Graphics - Windows 10 supports two 3D graphics API sets, Direct3D 11, and [Direct3D 12](https://msdn.microsoft.com/library/windows/desktop/dn899121).</span></span> <span data-ttu-id="e5612-140">Mit diesen beiden APIs können 3D- und 2D-Grafiken erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="e5612-140">Both of these APIs provide the capability to create 3D and 2D graphics.</span></span> <span data-ttu-id="e5612-141">Direct3D 11 und Direct3D 12 werden nicht zusammen verwendet, können jedoch zusammen mit APIs in der 2D-Grafik- und Benutzeroberflächengruppe verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e5612-141">Direct3D 11 and Direct3D 12 are not used together, but either can be used with any of the APIs in the 2D Graphics and UI group.</span></span> <span data-ttu-id="e5612-142">Weitere Informationen zum Verwenden der Grafik-APIs in Ihrem Spiel finden Sie unter [Grundlegendes zu 3D-Grafiken für DirectX-Spiele](an-introduction-to-3d-graphics-with-directx.md).</span><span class="sxs-lookup"><span data-stu-id="e5612-142">For more information about using the graphics APIs in your game, see [Basic 3D graphics for DirectX games](an-introduction-to-3d-graphics-with-directx.md).</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="e5612-143">API</span><span class="sxs-lookup"><span data-stu-id="e5612-143">API</span></span></th>
    <th align="left"><span data-ttu-id="e5612-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5612-144">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="e5612-145">Direct3D12</span><span class="sxs-lookup"><span data-stu-id="e5612-145">Direct3D 12</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-146">Direct3D12 stellt die nächste Version von Direct3D vor, der 3D-Grafik-API im Herzen von DirectX.</span><span class="sxs-lookup"><span data-stu-id="e5612-146">Direct3D 12 introduces the next version of Direct3D, the 3D graphics API at the heart of DirectX.</span></span> <span data-ttu-id="e5612-147">Diese Version von Direct3D ist schneller und effizienter als frühere Versionen von Direct3D.</span><span class="sxs-lookup"><span data-stu-id="e5612-147">This version of Direct3D is designed to be faster and more efficient than previous versions of Direct3D.</span></span> <span data-ttu-id="e5612-148">Der Kompromiss für die höhere Geschwindigkeit von Direct3D12 besteht darin, dass die Ebene niedrigerer ist. Sie müssen Ihre Grafikressourcen selbst verwalten und über eine umfassendere Grafikprogrammiererfahrung verfügen, um die höhere Geschwindigkeit zu realisieren.</span><span class="sxs-lookup"><span data-stu-id="e5612-148">The tradeoff for Direct3D 12's increased speed is that it is lower level and requires you to manage your graphics resources yourself and have more extensive graphics programming experience to realize the increased speed.</span></span></p>
    <p><strong><span data-ttu-id="e5612-149">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-149">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-150">Verwenden Sie Direct3D 12, wenn Sie die Leistung Ihres Spiels optimieren müssen und das Spiel CPU-gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="e5612-150">Use Direct3D 12 when you need to maximize your game's performance and your game is CPU bound.</span></span></p>
    <p><strong><span data-ttu-id="e5612-151">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-151">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-152">Weitere Informationen finden Sie in der [Direct3D 12](https://msdn.microsoft.com/library/windows/desktop/dn899121)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e5612-152">See the [Direct3d 12](https://msdn.microsoft.com/library/windows/desktop/dn899121) documentation.</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="e5612-153">Direct3D11</span><span class="sxs-lookup"><span data-stu-id="e5612-153">Direct3D 11</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-154">Direct3D11 ist die vorherige Version von Direct3D, mit der Sie 3D-Grafiken unter Verwendung einer höheren Ebene der Hardwareabstraktion als bei D3D12 erstellen können.</span><span class="sxs-lookup"><span data-stu-id="e5612-154">Direct3D 11 is the previous version of Direct3D and allows you to create 3D graphics using a higher level of hardware abstraction than D3D 12.</span></span></p>
    <p><strong><span data-ttu-id="e5612-155">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-155">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-156">Verwenden Sie Direct3D 11, wenn Sie über vorhandenen Direct3D 11-Code verfügen, Ihr Spiel nicht CPU-gebunden ist, oder Sie davon profitieren möchten, dass Ihre Ressourcen verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="e5612-156">Use Direct3D 11 if you have existing Direct3D 11 code, your game is not CPU bound, or you want the benefit of having resources managed for you.</span></span></p>
    <p><strong><span data-ttu-id="e5612-157">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-157">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-158">Weitere Informationen finden Sie in der [Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476080)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e5612-158">See the [Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476080) documentation.</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="e5612-159">2D-Grafiken und Benutzeroberfläche – APIs für 2D-Grafiken z.B. Text und Benutzeroberflächen.</span><span class="sxs-lookup"><span data-stu-id="e5612-159">2D Graphics and UI - APIs concerning 2D graphics such as text and user interfaces.</span></span> <span data-ttu-id="e5612-160">Alle 2D-Grafiken und Benutzeroberflächen-APIs sind optional.</span><span class="sxs-lookup"><span data-stu-id="e5612-160">All of the 2D graphics and UI APIs are optional.</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="e5612-161">API</span><span class="sxs-lookup"><span data-stu-id="e5612-161">API</span></span></th>
    <th align="left"><span data-ttu-id="e5612-162">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5612-162">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="e5612-163">Direct2D</span><span class="sxs-lookup"><span data-stu-id="e5612-163">Direct2D</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-164">Direct2D ist eine hardwarebeschleunigte 2D-Grafik-API mit unmittelbarem Modus, die das Rendern mit hoher Leistung und in hoher Qualität für 2D-Geometrie, Bitmaps und Text bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="e5612-164">Direct2D is a hardware-accelerated, immediate-mode, 2-D graphics API that provides high performance and high-quality rendering for 2-D geometry, bitmaps, and text.</span></span> <span data-ttu-id="e5612-165">Die Direct2D-API baut auf Direct3D auf und ist für die Verwendung mit GDI, GDI+ und Direct3D konzipiert.</span><span class="sxs-lookup"><span data-stu-id="e5612-165">The Direct2D API is built on Direct3D and is designed to interoperate well with GDI, GDI+, and Direct3D.</span></span></p>
    <p><strong><span data-ttu-id="e5612-166">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-166">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-167">Direct2D kann anstelle von Direct3D zum Bereitstellen von Grafiken für reine 2D-Spiele verwendet werden, beispielsweise Side-Scroller oder Brettspiele. Es kann auch mit Direct3D für die vereinfachte Erstellung von 2D-Grafiken in einem 3D-Spiel verwendet werden, beispielsweise einer Benutzeroberfläche oder einer Heads-Up-Anzeige.</span><span class="sxs-lookup"><span data-stu-id="e5612-167">Direct2D can be used instead of Direct3D to provide graphics for pure 2D games such as a side-scroller or board game, or can be used with Direct3D to simplify creation of 2D graphics in a 3D game, such as a user interface or heads-up-display.</span></span></p>
    <p><strong><span data-ttu-id="e5612-168">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-168">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-169">Weitere Informationen finden Sie in der [Direct2D](https://msdn.microsoft.com/library/windows/desktop/dd370990)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e5612-169">See the [Direct2D](https://msdn.microsoft.com/library/windows/desktop/dd370990) documentation.</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="e5612-170">DirectWrite</span><span class="sxs-lookup"><span data-stu-id="e5612-170">DirectWrite</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-171">DirectWrite stellt zusätzliche Funktionen für das Arbeiten mit Text bereit und kann mit Direct3D oder Direct2D zum Bereitstellen der Textausgabe für Benutzeroberflächen oder andere Bereiche verwendet werden, in denen Text erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="e5612-171">DirectWrite provides extra capabilities for working with text and can be used with Direct3D or Direct2D to provide text output for user interfaces or other areas where text is required.</span></span> <span data-ttu-id="e5612-172">DirectWrite unterstützt Messung, Zeichnung und Treffererkennung von Text in mehreren Formaten.</span><span class="sxs-lookup"><span data-stu-id="e5612-172">DirectWrite supports measuring, drawing, and hit-testing of multi-format text.</span></span> <span data-ttu-id="e5612-173">DirectWrite behandelt Text in allen unterstützten Sprachen für globale und lokalisierte Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="e5612-173">DirectWrite handles text in all supported languages for global and localized applications.</span></span> <span data-ttu-id="e5612-174">DirectWrite stellt außerdem eine API für Glyphenrendering auf niedriger Ebene für Entwickler zur Ausführung von eigenem Layout und eigener Unicode-zu-Glyphen-Verarbeitung bereit.</span><span class="sxs-lookup"><span data-stu-id="e5612-174">DirectWrite also provides a low-level glyph rendering API for developers who want to perform their own layout and Unicode-to-glyph processing.</span></span></p>
    <p><strong><span data-ttu-id="e5612-175">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-175">When to use</span></span></strong></p>
    <p></p>
    <p><strong><span data-ttu-id="e5612-176">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-176">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-177">Weitere Informationen finden Sie in der [DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e5612-177">See the [DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038) documentation.</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><span data-ttu-id="e5612-178">DirectComposition</span><span class="sxs-lookup"><span data-stu-id="e5612-178">DirectComposition</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-179">DirectComposition ist eine Windows-Komponente, die eine Hochleistungs-Bitmapanordnung mit Übergängen, Effekten und Animationen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="e5612-179">DirectComposition is a Windows component that enables high-performance bitmap composition with transforms, effects, and animations.</span></span> <span data-ttu-id="e5612-180">Anwendungsentwickler können die DirectComposition-API zum Erstellen von visuell ansprechenden Benutzeroberflächen verwenden, die umfassende und fließende animierte Übergänge von einem visuellen Objekt zum nächsten ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e5612-180">Application developers can use the DirectComposition API to create visually engaging user interfaces that feature rich and fluid animated transitions from one visual to another.</span></span></p>
    <p><strong><span data-ttu-id="e5612-181">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-181">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-182">DirectComposition wurde für die vereinfachte Anordnung von visuellen Objekten und Erstellen von animierten Übergängen entwickelt.</span><span class="sxs-lookup"><span data-stu-id="e5612-182">DirectComposition is designed to simplify the process of composing visuals and creating animated transitions.</span></span> <span data-ttu-id="e5612-183">Wenn Ihr Spiel eine komplexe Benutzeroberfläche erfordert, können Sie DirectComposition zum vereinfachten Erstellen und Verwalten der Benutzeroberfläche verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5612-183">If your game requires complex user interfaces, you can use DirectComposition to simplify the creation and management of the UI.</span></span></p>
    <p><strong><span data-ttu-id="e5612-184">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-184">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-185">Weitere Informationen finden Sie in der [DirectComposition](https://msdn.microsoft.com/library/windows/desktop/hh437371)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e5612-185">See the [DirectComposition](https://msdn.microsoft.com/library/windows/desktop/hh437371) documentation.</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="e5612-186">Audio – APIs für die Audiowiedergabe und die Anwendung von Audioeffekten.</span><span class="sxs-lookup"><span data-stu-id="e5612-186">Audio - APIs concerning playing audio and applying audio effects.</span></span> <span data-ttu-id="e5612-187">Informationen zum Verwenden von Audio-APIs in Ihrem Spiel finden Sie unter [Audio für Spiele](working-with-audio-in-your-directx-game.md).</span><span class="sxs-lookup"><span data-stu-id="e5612-187">For information about using the audio APIs in your game, see [Audio for games](working-with-audio-in-your-directx-game.md).</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="e5612-188">API</span><span class="sxs-lookup"><span data-stu-id="e5612-188">API</span></span></th>
    <th align="left"><span data-ttu-id="e5612-189">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5612-189">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="e5612-190">XAudio2</span><span class="sxs-lookup"><span data-stu-id="e5612-190">XAudio2</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-191">XAudio2 ist eine Low-Level-Audio-API, die eine grundlegende Signalverarbeitung und -abmischung bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="e5612-191">XAudio2 is a low-level audio API that provides a foundation for signal processing and mixing.</span></span> <span data-ttu-id="e5612-192">XAudio wurde für eine hohe Reaktionsfähigkeit in Bezug auf Audiomodule von Spielen entwickelt. Gleichzeitig können weiterhin benutzerdefinierte Audioeffekte und komplexe Ketten von Audioeffekten und -filtern erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="e5612-192">XAudio is designed to be very responsive for game audio engines while maintaining the ability to create custom audio effects and complex chains of audio effects and filters.</span></span></p>
    <p><strong><span data-ttu-id="e5612-193">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-193">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-194">Verwenden Sie XAudio2, wenn Ihr Spiel Sounds mit minimalem Aufwand und minimaler Verzögerung wiedergeben muss.</span><span class="sxs-lookup"><span data-stu-id="e5612-194">Use XAudio2 when your game needs to play sounds with minimal overhead and delay.</span></span></p>
    <p><strong><span data-ttu-id="e5612-195">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-195">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-196">Weitere Informationen finden Sie in der [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e5612-196">See the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049) documentation.</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="e5612-197">Media Foundation</span><span class="sxs-lookup"><span data-stu-id="e5612-197">Media Foundation</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-198">Microsoft Media Foundation wurde für die Wiedergabe von Mediendateien und Streams (Audio und Video) entwickelt, kann jedoch auch in Spielen verwendet werden, wenn eine Funktionalität auf höherer Ebene als XAudio2 erforderlich ist und der zusätzliche Aufwand akzeptabel ist.</span><span class="sxs-lookup"><span data-stu-id="e5612-198">Microsoft Media Foundation is designed for the playback of media files and streams, both audio and video, but can also be used in games when higher level functionality than XAudio2 is required and some additional overhead is acceptable.</span></span></p>
    <p><strong><span data-ttu-id="e5612-199">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-199">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-200">Media Foundation ist bei Filmszenen oder nichtinteraktiven Komponenten des Spiels besonders nützlich.</span><span class="sxs-lookup"><span data-stu-id="e5612-200">Media foundation is particularly useful for cinematic scenes or non-interactive components of your game.</span></span> <span data-ttu-id="e5612-201">Media Foundation ist auch für die Decodierung von Audiodateien für die Wiedergabe mit XAudio2 nützlich.</span><span class="sxs-lookup"><span data-stu-id="e5612-201">Media foundation is also useful for decoding audio files for playback using XAudio2.</span></span></p>
    <p><strong><span data-ttu-id="e5612-202">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-202">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-203">Weitere Informationen finden Sie unter [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="e5612-203">See the [Microsoft Media Foundation overview](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="e5612-204">Eingabe – APIs für die Eingabe über Tastatur, Maus, Gamepad und andere Benutzereingabequellen.</span><span class="sxs-lookup"><span data-stu-id="e5612-204">Input - APIs concerning input from the keyboard, mouse, gamepad, and other user input sources.</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="e5612-205">API</span><span class="sxs-lookup"><span data-stu-id="e5612-205">API</span></span></th>
    <th align="left"><span data-ttu-id="e5612-206">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5612-206">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="e5612-207">XInput</span><span class="sxs-lookup"><span data-stu-id="e5612-207">XInput</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-208">Mit der XInput-Gamecontroller-API können Anwendungen Eingaben von Gamecontrollern erhalten.</span><span class="sxs-lookup"><span data-stu-id="e5612-208">The XInput Game Controller API enables applications to receive input from game controllers.</span></span></p>
    <p><strong><span data-ttu-id="e5612-209">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-209">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-210">Wenn Ihr Spiel die Gamepadeingabe unterstützen muss und Sie über vorhandenen XInput-Code verfügen, können Sie weiterhin XInput verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5612-210">If your game needs to support gampad input and you have existing XInput code, you can continue to make use of XInput.</span></span> <span data-ttu-id="e5612-211">XInput wurde durch Windows.Gaming.Input für UWP ersetzt, und Sie sollten beim Schreiben von neuem Eingabecode Windows.Gaming.Input anstelle von XInput verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5612-211">XInput has been replaced by Windows.Gaming.Input for UWP, and if you're writing new input code, you should use Windows.Gaming.Input instead of XInput.</span></span></p>
    <p><strong><span data-ttu-id="e5612-212">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-212">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-213">Weitere Informationen finden Sie in der [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e5612-213">See the [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053) documentation.</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="e5612-214">Windows.Gaming.Input</span><span class="sxs-lookup"><span data-stu-id="e5612-214">Windows.Gaming.Input</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-215">Die Windows.Gaming.Input-API ersetzt XInput und bietet die gleiche Funktionalität mit den folgenden Vorteilen gegenüber Xinput:</span><span class="sxs-lookup"><span data-stu-id="e5612-215">The Windows.Gaming.Input API replaces XInput and provides the same functionality with the following advantages over Xinput:</span></span></p>
    <ul>
    <li><span data-ttu-id="e5612-216">Geringere Ressourcenverwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-216">Lower resource usage</span></span></li>
    <li><span data-ttu-id="e5612-217">Geringere Latenz des API-Aufrufs zum Abrufen von Eingaben</span><span class="sxs-lookup"><span data-stu-id="e5612-217">Lower API call latency for retrieving input</span></span></li>
    <li><span data-ttu-id="e5612-218">Die Möglichkeit, mit mehr als 4 Gamepads gleichzeitig zu arbeiten</span><span class="sxs-lookup"><span data-stu-id="e5612-218">The ability to work with more than 4 gamepads at once</span></span></li>
    <li><span data-ttu-id="e5612-219">Die Möglichkeit zum Zugreifen auf zusätzliche Xbox One-Gamepadfeatures, z.B. Triggervibrationsmotoren.</span><span class="sxs-lookup"><span data-stu-id="e5612-219">The ability to access addition Xbox One gamepad features, such as the trigger vibration motors</span></span></li>
    <li><span data-ttu-id="e5612-220">Die Möglichkeit, beim Herstellen oder Trennen einer Verbindung durch ein Ereignis anstelle von Abruf benachrichtigt zu werden.</span><span class="sxs-lookup"><span data-stu-id="e5612-220">The ability to be notified when controllers connect/disconnect via event instead of polling</span></span></li>
    <li><span data-ttu-id="e5612-221">Die Möglichkeit zum Zuweisen der Eingabe an einen bestimmten Benutzer (Windows.System.User)</span><span class="sxs-lookup"><span data-stu-id="e5612-221">The ability to attribute input to a specific user (Windows.System.User)</span></span></li>
    </ul>
    <p><strong><span data-ttu-id="e5612-222">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-222">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-223">Wenn Ihr Spiel Eingaben über ein Gamepad unterstützen muss und einen vorhandenen XInput-Code nicht verwendet, oder wenn Sie einen der oben genannten Vorteile nutzen möchten, sollten Sie Windows.Gaming.Input verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5612-223">If your game needs to support gamepad input and is not using existing XInput code or you need one of the benefits listed above, you should make use of Windows.Gaming.Input.</span></span></p>
    <p><strong><span data-ttu-id="e5612-224">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-224">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-225">Weitere Informationen finden Sie in der Dokumentation [<strong>Windows.Gaming.Input</strong>](https://msdn.microsoft.com/library/windows/apps/dn707817).</span><span class="sxs-lookup"><span data-stu-id="e5612-225">See the [<strong>Windows.Gaming.Input</strong>](https://msdn.microsoft.com/library/windows/apps/dn707817) documentation.</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><span data-ttu-id="e5612-226">Windows.UI.Core.CoreWindow</span><span class="sxs-lookup"><span data-stu-id="e5612-226">Windows.UI.Core.CoreWindow</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-227">Mit der Windows.UI.Core.CoreWindow-Klasse können Sie nachverfolgen, wann der Zeiger gedrückt oder verschoben wird oder wann eine Taste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="e5612-227">The Windows.UI.Core.CoreWindow class provides events for tracking pointer presses and movement, and key down and key up events.</span></span></p>
    <p><strong><span data-ttu-id="e5612-228">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-228">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-229">Verwenden Sie die Windows.UI.Core.CoreWindows-Ereignisse, wenn Sie nachverfolgen möchten, wann die Maus oder eine Taste in Ihrem Spiel gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="e5612-229">Use Windows.UI.Core.CoreWindows events when you need to track the mouse or key presses in your game.</span></span></p>
    <p><strong><span data-ttu-id="e5612-230">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-230">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-231">Weitere Informationen zum Verwenden der Maus oder Tastatur in Ihrem Spiel finden Sie unter [Bewegungs-/Blicksteuerungen für Spiele](tutorial--adding-move-look-controls-to-your-directx-game.md).</span><span class="sxs-lookup"><span data-stu-id="e5612-231">See [Move-look controls for games](tutorial--adding-move-look-controls-to-your-directx-game.md) for more information about using the mouse or keyboard in your game.</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="e5612-232">Math-APIs – APIs zum Vereinfachen häufig verwendeter mathematischer Vorgänge.</span><span class="sxs-lookup"><span data-stu-id="e5612-232">Math - APIs concerning simplifying commonly used mathematical operations.</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="e5612-233">API</span><span class="sxs-lookup"><span data-stu-id="e5612-233">API</span></span></th>
    <th align="left"><span data-ttu-id="e5612-234">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5612-234">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="e5612-235">DirectXMath</span><span class="sxs-lookup"><span data-stu-id="e5612-235">DirectXMath</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-236">Die DirectXMath-API bietet SIMD-freundliche C++-Typen und Funktionen für allgemeine lineare Algebra- und mathematische Grafikvorgänge für Spiele.</span><span class="sxs-lookup"><span data-stu-id="e5612-236">The DirectXMath API provides SIMD-friendly C++ types and functions for common linear algebra and graphics math operations common to games.</span></span></p>
    <p><strong><span data-ttu-id="e5612-237">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-237">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-238">Die Verwendung von DirectXMath ist optional und vereinfacht allgemeine mathematische Vorgänge.</span><span class="sxs-lookup"><span data-stu-id="e5612-238">Use of DirectXMath is optional and simplifies common mathematical operations.</span></span></p>
    <p><strong><span data-ttu-id="e5612-239">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-239">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-240">Weitere Informationen finden Sie in der [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e5612-240">See the [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833) documentation.</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="e5612-241">Netzwerke – APIs für die Kommunikation mit anderen Computern und Geräten entweder über das Internet oder private Netzwerke.</span><span class="sxs-lookup"><span data-stu-id="e5612-241">Networking - APIs concerning communicating with other computers and devices over either the Internet or private networks.</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="e5612-242">API</span><span class="sxs-lookup"><span data-stu-id="e5612-242">API</span></span></th>
    <th align="left"><span data-ttu-id="e5612-243">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5612-243">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="e5612-244">Windows.Networking.Sockets</span><span class="sxs-lookup"><span data-stu-id="e5612-244">Windows.Networking.Sockets</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-245">Der Windows.Networking.Sockets-Namespace stellt TCP- und UDP-Sockets bereit, die eine zuverlässige bzw. nicht zuverlässige Netzwerkkommunikation ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e5612-245">The Windows.Networking.Sockets namespace provides TCP and UDP sockets that allow reliable or unreliable network communication.</span></span></p>
    <p><strong><span data-ttu-id="e5612-246">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-246">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-247">Verwenden Sie Windows.Networking.Sockets, wenn Ihr Spiel mit anderen Computern und Geräten über das Netzwerk kommunizieren muss.</span><span class="sxs-lookup"><span data-stu-id="e5612-247">Use Windows.Networking.Sockets if your game needs to communicate with other computers or devices over the network.</span></span></p>
    <p><strong><span data-ttu-id="e5612-248">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-248">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-249">Weitere Informationen finden Sie unter [Netzwerk für Spiele](work-with-networking-in-your-directx-game.md).</span><span class="sxs-lookup"><span data-stu-id="e5612-249">See [Work with networking in your game](work-with-networking-in-your-directx-game.md).</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="e5612-250">Windows.Web.HTTP</span><span class="sxs-lookup"><span data-stu-id="e5612-250">Windows.Web.HTTP</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-251">Der Windows.Web.HTTP-Namespace stellt eine zuverlässige Verbindung mit HTTP-Servern bereit, die für den Zugriff auf eine Website verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="e5612-251">The Windows.Web.HTTP namespace provides a reliable connection to HTTP servers that can be used to access a web site.</span></span></p>
    <p><strong><span data-ttu-id="e5612-252">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-252">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-253">Verwenden Sie Windows.Web.HTTP, wenn Ihr Spiel zum Abrufen oder Speichern von Informationen auf eine Website zugreifen muss.</span><span class="sxs-lookup"><span data-stu-id="e5612-253">Use Windows.Web.HTTP when your game needs to access a web site to retrieve or store information.</span></span></p>
    <p><strong><span data-ttu-id="e5612-254">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-254">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-255">Weitere Informationen finden Sie unter [Netzwerk für Spiele](work-with-networking-in-your-directx-game.md).</span><span class="sxs-lookup"><span data-stu-id="e5612-255">See [Work with networking in your game](work-with-networking-in-your-directx-game.md).</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

-   <span data-ttu-id="e5612-256">Support-Dienstprogramme - Bibliotheken, die auf Grundlage von Windows 10-APIs entwickelt wurden.</span><span class="sxs-lookup"><span data-stu-id="e5612-256">Support Utilities - Libraries that build on the Windows 10 APIs.</span></span>

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="e5612-257">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e5612-257">Library</span></span></th>
    <th align="left"><span data-ttu-id="e5612-258">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5612-258">Description</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><span data-ttu-id="e5612-259">DirectX-Toolkit</span><span class="sxs-lookup"><span data-stu-id="e5612-259">DirectX Tool Kit</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-260">Das DirectX-Toolkit (DirectXTK) ist eine Sammlung von Hilfsklassen für DirectX 11.x-Code in C++.</span><span class="sxs-lookup"><span data-stu-id="e5612-260">The DirectX Tool Kit (DirectXTK) is a collection of helper classes for writing DirectX 11.x code in C++.</span></span></p>
    <p><strong><span data-ttu-id="e5612-261">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-261">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-262">Verwenden Sie das DirectX-Toolkit, wenn Sie C++-Entwickler und auf der Suche nach einem modernen Ersatz für älteren D3DX-Hilfsprogrammcode sind, oder ein XNA Game Studio-Entwickler sind, der zu systemeigenen C++ wechselt.</span><span class="sxs-lookup"><span data-stu-id="e5612-262">Use the DirectX Tool Kit if you're a C++ developer looking for a modern replacement to the legacy D3DX utility code or you're an XNA Game Studio developer transitioning to native C++.</span></span></p>
    <p><strong><span data-ttu-id="e5612-263">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-263">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-264">Weitere Informationen finden Sie auf der DirectX-Toolkit-Projektseite [https://github.com/Microsoft/DirectXTK](https://github.com/Microsoft/DirectXTK).</span><span class="sxs-lookup"><span data-stu-id="e5612-264">See the DirectX Tool Kit project page, [https://github.com/Microsoft/DirectXTK](https://github.com/Microsoft/DirectXTK).</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><span data-ttu-id="e5612-265">Win2D</span><span class="sxs-lookup"><span data-stu-id="e5612-265">Win2D</span></span></td>
    <td align="left"><p><span data-ttu-id="e5612-266">Win2D ist eine einfach zu verwendende Windows-Runtime-API für 2D-Grafikrendering im unmittelbaren Modus.</span><span class="sxs-lookup"><span data-stu-id="e5612-266">Win2D is an easy-to-use Windows Runtime API for immediate mode 2D graphics rendering.</span></span></p>
    <p><strong><span data-ttu-id="e5612-267">Gründe für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5612-267">When to use</span></span></strong></p>
    <p><span data-ttu-id="e5612-268">Verwenden Sie Win2D, wenn Sie C++-Entwickler sind und einen einfacher zu verwendenden WinRT-Wrapper für Direct2D und DirectWrite benötigen, oder C#-Entwickler sind und Direct2D und DirectWrite verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="e5612-268">Use Win2D if you're a C++ developer and want an easier to use WinRT wrapper for Direct2D and DirectWrite, or you're a C# developer wanting to use Direct2D and DirectWrite.</span></span></p>
    <p><strong><span data-ttu-id="e5612-269">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5612-269">For more information</span></span></strong></p>
    <p><span data-ttu-id="e5612-270">Weitere Informationen finden Sie auf der Win2D-Projektseite [https://github.com/Microsoft/Win2D](https://github.com/Microsoft/Win2D)</span><span class="sxs-lookup"><span data-stu-id="e5612-270">See the Win2D project page, [https://github.com/Microsoft/Win2D](https://github.com/Microsoft/Win2D).</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

## <a name="xbox-live-services"></a><span data-ttu-id="e5612-271">Xbox Live-Dienste</span><span class="sxs-lookup"><span data-stu-id="e5612-271">Xbox Live Services</span></span>

<span data-ttu-id="e5612-272">Mit dem [Xbox Live Creators-Programm](https://developer.microsoft.com/games/xbox/xboxlive/creator) kann jeder Entwickler Xbox Live in seine UWP-Spiele integrieren und sie auf Xbox One und Windows 10 veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="e5612-272">The [Xbox Live Creators Program](https://developer.microsoft.com/games/xbox/xboxlive/creator) allows any developer to integrate Xbox Live into their UWP game and publish to Xbox One and Windows 10.</span></span> <span data-ttu-id="e5612-273">Integrieren Sie soziale Xbox Live-Funktionen wie Anmelden, Präsenzinformationen, Ranglisten und mehr mit minimaler Entwicklungszeit in Ihre Titel.</span><span class="sxs-lookup"><span data-stu-id="e5612-273">Integrate Xbox Live social experiences such as sign-in, presence, leaderboards, and more into your title, with minimal development time.</span></span> <span data-ttu-id="e5612-274">Die sozialen Xbox Live-Features wurden entwickelt, damit Sie Ihre Zielgruppe organisch auf bis zu 55Millionen aktive Spieler erweitern können.</span><span class="sxs-lookup"><span data-stu-id="e5612-274">Xbox Live social features are designed to organically grow your audience, spreading awareness to over 55 million active gamers.</span></span>

<span data-ttu-id="e5612-275">Treten Sie dem [ID@Xbox](http://www.xbox.com/developers/id) bei, wenn Sie Zugriff auf weitere Xbox Live-Funktionen wünschen, dedizierte Marketing- und Entwicklungsunterstützung benötigen oder im allgemeinen Xbox One-Store vertreten sein möchten.</span><span class="sxs-lookup"><span data-stu-id="e5612-275">If you want access to even more Xbox Live capabilities, dedicated marketing and development support, and the chance to be featured in the main Xbox One store, apply to the [ID@Xbox](http://www.xbox.com/developers/id) program.</span></span> <span data-ttu-id="e5612-276">Um festzustellen, welche Features für das Xbox Live Creators-Programm und das ID@Xbox-Programm verfügbar sind, wechseln Sie auf die [Tabelle der Features](../xbox-live/developer-program-overview.md#feature-table).</span><span class="sxs-lookup"><span data-stu-id="e5612-276">To see which features are available to the Xbox Live Creators Program and ID@Xbox program, see the [Feature table](../xbox-live/developer-program-overview.md#feature-table).</span></span>

<span data-ttu-id="e5612-277">Weitere Informationen finden Sie unter [Hinzufügen von Xbox Live zu Ihrem Spiel](e2e.md#adding-xbox-live-to-your-game).</span><span class="sxs-lookup"><span data-stu-id="e5612-277">For more info, go to [Adding Xbox Live to your game](e2e.md#adding-xbox-live-to-your-game).</span></span>

##  <a name="alternatives-to-writing-games-with-directx-and-uwp"></a><span data-ttu-id="e5612-278">Alternativen zum Schreiben von Spielen mit DirectX und UWP</span><span class="sxs-lookup"><span data-stu-id="e5612-278">Alternatives to writing games with DirectX and UWP</span></span>


### <a name="uwp-games-without-directx"></a><span data-ttu-id="e5612-279">UWP-Spiele ohne DirectX</span><span class="sxs-lookup"><span data-stu-id="e5612-279">UWP Games without DirectX</span></span>

<span data-ttu-id="e5612-280">Einfachere Spiele mit minimalem Leistungsanforderungen, z.B. Kartenspiele oder Brettspiele, können ohne DirectX und müssen nicht unbedingt in C++ geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="e5612-280">Simpler games with minimal performance requirements, such as card games or board games, can be written without DirectX and don't necessarily need to be written in C++.</span></span> <span data-ttu-id="e5612-281">Bei dieser Art von Spielen können alle von UWP unterstützten Sprachen verwendet werden, z.B. C#, Visual Basic, C++ und HTML/JavaScript.</span><span class="sxs-lookup"><span data-stu-id="e5612-281">These sort of games can make use of any of the languages supported by UWP such as C#, Visual Basic, C++, and HTML/JavaScript.</span></span> <span data-ttu-id="e5612-282">Wenn Ihr Spiel weder eine hohe Leistung noch rechenintensive Grafiken erfordert, sollten Sie sich das [Beispiel für ein JavaScript- und HTML5-Fingereingabespiel](http://code.msdn.microsoft.com/windowsapps/JavaScript-and-HTML5-touch-d96f6031) ansehen.</span><span class="sxs-lookup"><span data-stu-id="e5612-282">If performance and intensive graphics are not a requirement for your game, checkout [JavaScript and HTML5 touch game sample](http://code.msdn.microsoft.com/windowsapps/JavaScript-and-HTML5-touch-d96f6031) as an example.</span></span>

### <a name="game-engines"></a><span data-ttu-id="e5612-283">Spielengines</span><span class="sxs-lookup"><span data-stu-id="e5612-283">Game Engines</span></span>

<span data-ttu-id="e5612-284">Eine Alternative zum Schreiben eigener Spielemodule mithilfe der Windows-APIs für die Entwicklung von Spielen stellen die zahlreichen qualitativ hochwertigen Spielemodule dar, die auf den Windows-APIs für die Entwicklung von Spielen basieren und für die Entwicklung von Spielen auf Windows-Plattformen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="e5612-284">As an alternative to writing your own game engine using the Windows game development APIs, many high quality game engines that build on the Windows game development APIs are available for developing games on Windows platforms.</span></span> <span data-ttu-id="e5612-285">Wenn Sie eine Spielengine oder Bibliothek in Erwägung ziehen, können Sie zwischen den folgenden Möglichkeiten wählen:</span><span class="sxs-lookup"><span data-stu-id="e5612-285">When considering a game engine or library, you have multiple options:</span></span>

-   <span data-ttu-id="e5612-286">Vollständige Spielengine – Eine vollständige Spielengine umfasst die meisten bzw. alle Windows 10-APIs, die Sie zum Schreiben einer eigenen Spielengine verwenden würden, z.B. Grafik, Eingabe und Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="e5612-286">Full game engine - A full game engine encapsulates most or all of the Windows 10 APIs you would use when writing a game engine from scratch, such as graphics, audio, input, and networking.</span></span> <span data-ttu-id="e5612-287">Vollständige Spielengines können auch Spiellogikfunktionalität bereitstellen, z.B. künstliche Intelligenz und Pfadsuche.</span><span class="sxs-lookup"><span data-stu-id="e5612-287">Full game engines may also provide game logic functionality such as artificial intelligence and pathfinding.</span></span>
-   <span data-ttu-id="e5612-288">Grafikengine – Grafikengines umfassen Windows 10-Grafik-APIs, verwalten Grafikressourcen und unterstützen zahlreiche Modell- und Weltformate.</span><span class="sxs-lookup"><span data-stu-id="e5612-288">Graphics engine - Graphics engines encapsulate the Windows 10 graphics APIs, manage graphics resources, and support a variety of model and world formats.</span></span>
-   <span data-ttu-id="e5612-289">Audioengine – Audioengines umfassen Windows 10-Audio-APIs, verwalten Audioressourcen und stellen erweiterte Audiowiedergabe und -Effekte bereit.</span><span class="sxs-lookup"><span data-stu-id="e5612-289">Audio engine - Audio engines encapsulate the Windows 10 audio APIs, manage audio resources, and provide advanced audio processing and effects.</span></span>
-   <span data-ttu-id="e5612-290">Netzwerkengine – Netzwerkengines umfassen Windows 10-Netzwerk-APIs zum Hinzufügen von Peer-zu-Peer- oder serverbasierter Multiplayerunterstützung zu Ihrem Spiel und enthalten ggf. erweiterte Netzwerkfunktionalität zur Unterstützung einer großen Anzahl von Spielern.</span><span class="sxs-lookup"><span data-stu-id="e5612-290">Network engine - Network engines encapsulate Windows 10 networking APIs for adding peer-to-peer or server-based multiplayer support to your game, and may include advanced networking functionality to support large numbers of players.</span></span>
-   <span data-ttu-id="e5612-291">Engine für künstliche Intelligenz und Pfadsuche – Engines für künstliche Intelligenz und Pfadsuche stellen ein Framework zur Steuerung des Agentverhaltens in einem Spiel bereit.</span><span class="sxs-lookup"><span data-stu-id="e5612-291">Artificial intelligence and pathfinding engine - AI and pathfinding engines provide a framework for controlling the behavior of agents in your game.</span></span>
-   <span data-ttu-id="e5612-292">Engines für besondere Zwecke – Es stehen unterschiedliche weitere Engines zur Bewältigung von nahezu allen möglichen Spielentwicklungsaufgaben zur Verfügung, z.B. Erstellen von Inventarsystemen und Dialogstrukturen.</span><span class="sxs-lookup"><span data-stu-id="e5612-292">Special purpose engines - A variety of additional engines exist for handling almost any game development related task you might run into, such as creating inventory systems and dialog trees.</span></span>

## <a name="submitting-a-game-to-the-store"></a><span data-ttu-id="e5612-293">Übermitteln eines Spiels an den Store</span><span class="sxs-lookup"><span data-stu-id="e5612-293">Submitting a game to the Store</span></span>


<span data-ttu-id="e5612-294">Wenn Ihr Spiel zur Veröffentlichung bereit steht, müssen Sie ein Entwicklerkonto erstellen und Ihr Spiel an den Windows Store übermitteln.</span><span class="sxs-lookup"><span data-stu-id="e5612-294">Once you’re ready to publish your game, you’ll need to create a developer account and submit your game to the Windows Store.</span></span>

<span data-ttu-id="e5612-295">Informationen zum Übermitteln Ihres Spiels an den Windows Store finden Sie unter [Übermitteln und Veröffentlichen Ihres Spiels](e2e.md#submitting-and-publishing-your-game).</span><span class="sxs-lookup"><span data-stu-id="e5612-295">For information about submitting your game to the Windows Store, see [Submitting and publishing your game](e2e.md#submitting-and-publishing-your-game).</span></span>

 

 




