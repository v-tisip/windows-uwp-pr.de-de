---
author: mtoepke
title: DirectX11 – Häufig gestellte Fragen zur Portierung
description: Antworten auf häufig gestellte Fragen zur Portierung von Spielen zur Universellen Windows-Plattform (UWP)
ms.assetid: 79c3b4c0-86eb-5019-97bb-5feee5667a2d
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, uwp, spiele, directx 11
ms.localizationpriority: medium
ms.openlocfilehash: 06a4c9b434afedabc17a48e9929da8dc4460fe03
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7298629"
---
# <a name="directx-11-porting-faq"></a><span data-ttu-id="056b6-104">DirectX11 – Häufig gestellte Fragen zur Portierung</span><span class="sxs-lookup"><span data-stu-id="056b6-104">DirectX 11 porting FAQ</span></span>




<span data-ttu-id="056b6-105">Antworten auf häufig gestellte Fragen zur Portierung von Spielen zur Universellen Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="056b6-105">Answers to frequently-asked questions about porting games to Universal Windows Platform (UWP).</span></span>

## <a name="is-porting-my-game-going-to-be-a-set-of-search-and-replace-operations-on-api-methods-or-do-i-need-to-plan-for-a-more-thoughtful-porting-process"></a><span data-ttu-id="056b6-106">Kann ich mein Spiel durch Suchen und Ersetzen von API-Methoden portieren, oder ist eine sorgfältigere Planung des Portierungsprozesses erforderlich?</span><span class="sxs-lookup"><span data-stu-id="056b6-106">Is porting my game going to be a set of search-and-replace operations on API methods, or do I need to plan for a more thoughtful porting process?</span></span>


<span data-ttu-id="056b6-107">Direct3D11 wurde gegenüber Direct3D9 deutlich aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="056b6-107">Direct3D 11 is a significant upgrade from Direct3D 9.</span></span> <span data-ttu-id="056b6-108">Es wurden mehrere Paradigmenwechsel vorgenommen, darunter separate APIs für den virtualisierten Grafikadapter und seinen Kontext sowie eine neue Polymorphieebene für Geräteressourcen.</span><span class="sxs-lookup"><span data-stu-id="056b6-108">There are several paradigm shifts, including separate APIs for the virtualized graphics adapter and its context as well as a new layer of polymorphism for device resources.</span></span> <span data-ttu-id="056b6-109">Im Wesentlichen kann Ihr Spiel Grafikhardware weiter wie zuvor verwenden. Sie müssen sich allerdings mit der neuen API-Architektur von Direct3D11 vertraut machen und alle Teile Ihres Grafikcodes zur Verwendung der richtigen API-Komponenten aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="056b6-109">Your game can still use graphics hardware in essentially the same way, but you'll need to learn about the new Direct3D 11 API architecture and update each part of your graphics code to use the correct API components.</span></span> <span data-ttu-id="056b6-110">Siehe [Portierungskonzepte und Überlegungen zur Portierung](porting-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="056b6-110">See [Porting concepts and considerations](porting-considerations.md).</span></span>

## <a name="what-is-the-new-device-context-for-am-i-supposed-to-replace-my-direct3d-9-device-with-the-direct3d-11-device-the-device-context-or-both"></a><span data-ttu-id="056b6-111">Wofür dient der neue Gerätekontext?</span><span class="sxs-lookup"><span data-stu-id="056b6-111">What is the new device context for?</span></span> <span data-ttu-id="056b6-112">Muss ich mein Direct3D9-Gerät durch das Direct3D11-Gerät ersetzen, den Gerätekontext oder beides?</span><span class="sxs-lookup"><span data-stu-id="056b6-112">Am I supposed to replace my Direct3D 9 device with the Direct3D 11 device, the device context, or both?</span></span>


<span data-ttu-id="056b6-113">Das Direct3D-Gerät wird jetzt zum Erstellen von Ressourcen im Videospeicher verwendet. Der Gerätekontext dient dagegen zum Festlegen des Pipelinestatus und Generieren von Renderbefehlen.</span><span class="sxs-lookup"><span data-stu-id="056b6-113">The Direct3D device is now used to create resources in video memory, while the device context is used to set pipeline state and generate rendering commands.</span></span> <span data-ttu-id="056b6-114">Weitere Informationen finden Sie unter [Was sind die wichtigsten Änderungen seit Direct3D9?](understand-direct3d-11-1-concepts.md)</span><span class="sxs-lookup"><span data-stu-id="056b6-114">For more info see: [What are the most important changes since Direct3D 9?](understand-direct3d-11-1-concepts.md)</span></span>

##  <a name="do-i-have-to-update-my-game-timer-for-uwp"></a><span data-ttu-id="056b6-115">Muss ich meinen Spieltimer für UWP aktualisieren?</span><span class="sxs-lookup"><span data-stu-id="056b6-115">Do I have to update my game timer for UWP?</span></span>


<span data-ttu-id="056b6-116">[**QueryPerformanceCounter**](https://msdn.microsoft.com/library/windows/desktop/ms644904) in Verbindung mit [**QueryPerformanceFrequency**](https://msdn.microsoft.com/library/windows/desktop/ms644905) ist nach wie vor die beste Methode, um einen Spieltimer für UWP-Apps zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="056b6-116">[**QueryPerformanceCounter**](https://msdn.microsoft.com/library/windows/desktop/ms644904), along with [**QueryPerformanceFrequency**](https://msdn.microsoft.com/library/windows/desktop/ms644905), is still the best way to implement a game timer for UWP apps.</span></span>

<span data-ttu-id="056b6-117">Eine Kleinigkeit sollten Sie im Hinblick auf Timer und den UWP-App-Lebenszyklus beachten.</span><span class="sxs-lookup"><span data-stu-id="056b6-117">You should be aware of a nuance with timers and the UWP app lifecycle.</span></span> <span data-ttu-id="056b6-118">Das Anhalten und Fortsetzen ist nicht das Gleiche wie das erneute Starten eines Desktopspiels durch den Spieler, da das Spiel in diesem Fall eine Momentaufnahme ab dem Zeitpunkt fortsetzt, zu dem das Spiel zuletzt gespielt wurde.</span><span class="sxs-lookup"><span data-stu-id="056b6-118">Suspend/resume is different from a player re-launching a desktop game because your game will resume a snapshot in time from when the game was last played.</span></span> <span data-ttu-id="056b6-119">Ist viel Zeit vergangen – z.B. einige Wochen – können bei einigen Timerimplementierungen Fehler auftreten.</span><span class="sxs-lookup"><span data-stu-id="056b6-119">If a large amount of time has passed - for example, a few weeks - some game timer implementations might not behave gracefully.</span></span> <span data-ttu-id="056b6-120">Sie können App-Lebenszyklusereignisse verwenden, um Ihren Timer beim Fortsetzen des Spiels zurückzusetzen.</span><span class="sxs-lookup"><span data-stu-id="056b6-120">You can use app lifecycle events to reset your timer when the game resumes.</span></span>

<span data-ttu-id="056b6-121">Spiele, die noch immer die RDTSC-Anweisung verwenden, müssen aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="056b6-121">Games that still use the RDTSC instruction need to upgrade.</span></span> <span data-ttu-id="056b6-122">Siehe [Zeitliche Steuerung von Spielen und Multi-Core-Prozessoren](https://msdn.microsoft.com/library/windows/desktop/ee417693).</span><span class="sxs-lookup"><span data-stu-id="056b6-122">See [Game Timing and Multicore Processors](https://msdn.microsoft.com/library/windows/desktop/ee417693).</span></span>

## <a name="my-game-code-is-based-on-d3dx-and-dxut-is-there-anything-available-that-can-help-me-migrate-my-code"></a><span data-ttu-id="056b6-123">Mein Spielcode basiert auf D3DX und DXUT.</span><span class="sxs-lookup"><span data-stu-id="056b6-123">My game code is based on D3DX and DXUT.</span></span> <span data-ttu-id="056b6-124">Gibt es irgendetwas, das ich zum Migrieren des Codes verwenden kann?</span><span class="sxs-lookup"><span data-stu-id="056b6-124">Is there anything available that can help me migrate my code?</span></span>


<span data-ttu-id="056b6-125">Das Communityprojekt [DirectX-Toolkit (DirectXTK)](http://go.microsoft.com/fwlink/p/?LinkID=248929) bietet Hilfsklassen zur Verwendung mit Direct3D11.</span><span class="sxs-lookup"><span data-stu-id="056b6-125">The [DirectX Tool Kit (DirectXTK)](http://go.microsoft.com/fwlink/p/?LinkID=248929) community project offers helper classes for use with Direct3D 11.</span></span>

##  <a name="how-do-i-maintain-code-paths-for-the-desktop-and-the-microsoft-store"></a><span data-ttu-id="056b6-126">Verwalten ich wie Codepfade für den Desktop und Microsoft Store?</span><span class="sxs-lookup"><span data-stu-id="056b6-126">How do I maintain code paths for the desktop and the Microsoft Store?</span></span>


<span data-ttu-id="056b6-127">Chuck Walbourns Artikelserie [Dual-Use Coding Techniques for Games](http://go.microsoft.com/fwlink/p/?LinkID=286210) bietet Informationen zum Freigeben von Code zwischen Desktop und Microsoft Store-Codepfaden.</span><span class="sxs-lookup"><span data-stu-id="056b6-127">Chuck Walbourn's article series titled [Dual-use Coding Techniques for Games](http://go.microsoft.com/fwlink/p/?LinkID=286210) offers guidance on sharing code between the desktop and the Microsoft Store code paths.</span></span>

##  <a name="how-do-i-load-image-resources-in-my-directx-uwp-app"></a><span data-ttu-id="056b6-128">Wie lade ich Bildressourcen in meine DirectX-UWP-App?</span><span class="sxs-lookup"><span data-stu-id="056b6-128">How do I load image resources in my DirectX UWP app?</span></span>


<span data-ttu-id="056b6-129">Zum Laden von Bildern sind zwei API-Pfade verfügbar:</span><span class="sxs-lookup"><span data-stu-id="056b6-129">There are two API paths for loading images:</span></span>

-   <span data-ttu-id="056b6-130">Die Inhaltspipeline konvertiert Bilder in DDS-Dateien, die als Direct3D-Texturressourcen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="056b6-130">The content pipeline converts images into DDS files used as Direct3D texture resources.</span></span> <span data-ttu-id="056b6-131">Siehe [Verwenden von 3D-Ressourcen in Spielen oder Apps](https://msdn.microsoft.com/library/windows/apps/hh972446.aspx).</span><span class="sxs-lookup"><span data-stu-id="056b6-131">See [Using 3-D Assets in Your Game or App](https://msdn.microsoft.com/library/windows/apps/hh972446.aspx).</span></span>
-   <span data-ttu-id="056b6-132">Mit der [Windows-Bilderstellungskomponente](https://msdn.microsoft.com/library/windows/desktop/ee719902) können Bilder in vielen verschiedenen Formaten geladen werden. Sie kann sowohl für Direct2D-Bitmaps als auch für Direct3D-Texturressourcen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="056b6-132">The [Windows Imaging Component](https://msdn.microsoft.com/library/windows/desktop/ee719902) can be used to load images from a variety of formats, and can be used for Direct2D bitmaps as well as Direct3D texture resources.</span></span>

<span data-ttu-id="056b6-133">Sie können auch den DDSTextureLoader und den WICTextureLoader aus [DirectXTK](http://go.microsoft.com/fwlink/p/?LinkID=248929) oder [DirectXTex](http://go.microsoft.com/fwlink/p/?LinkID=248926) verwenden.</span><span class="sxs-lookup"><span data-stu-id="056b6-133">You can also use the DDSTextureLoader, and the WICTextureLoader, from the [DirectXTK](http://go.microsoft.com/fwlink/p/?LinkID=248929) or [DirectXTex](http://go.microsoft.com/fwlink/p/?LinkID=248926).</span></span>

## <a name="where-is-the-directx-sdk"></a><span data-ttu-id="056b6-134">Wo finde ich das DirectX SDK?</span><span class="sxs-lookup"><span data-stu-id="056b6-134">Where is the DirectX SDK?</span></span>


<span data-ttu-id="056b6-135">Das DirectXSDK ist im WindowsSDK enthalten.</span><span class="sxs-lookup"><span data-stu-id="056b6-135">The DirectX SDK is included as part of the Windows SDK.</span></span> <span data-ttu-id="056b6-136">Das neueste DirectXSDK, das vom WindowsSDK getrennt war, wurde im Juni 2010 veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="056b6-136">The most recent DirectX SDK that was separate from the Windows SDK was in June 2010.</span></span> <span data-ttu-id="056b6-137">Direct3D-Beispiele sind wie die anderen Windows-App-Beispiele in der Codegalerie enthalten.</span><span class="sxs-lookup"><span data-stu-id="056b6-137">Direct3D samples are in the Code Gallery along with the rest of the Windows app samples.</span></span>

## <a name="what-about-directx-redistributables"></a><span data-ttu-id="056b6-138">Was ist mit verteilbaren DirectX-Komponenten?</span><span class="sxs-lookup"><span data-stu-id="056b6-138">What about DirectX redistributables?</span></span>


<span data-ttu-id="056b6-139">Der Großteil der Komponenten im Windows SDK ist bereits in unterstützten Versionen des Betriebssystems enthalten oder verfügt nicht über eine DLL-Komponente (z.B. DirectXMath).</span><span class="sxs-lookup"><span data-stu-id="056b6-139">The vast majority of components in the Windows SDK are already included in supported versions of the OS, or have no DLL component (such as DirectXMath).</span></span> <span data-ttu-id="056b6-140">Alle Direct3D-API-Komponenten, die von UWP-Apps verwendet werden können, werden bereits für Ihr Spiel verfügbar sein. Sie müssen sie nicht neu verteilen.</span><span class="sxs-lookup"><span data-stu-id="056b6-140">All Direct3D API components that UWP apps can use will already available to your game; you don't need to be redistribute them.</span></span>

<span data-ttu-id="056b6-141">Win32-Desktopanwendungen verwenden weiterhin DirectSetup. Wenn Sie die Desktopversion Ihres Spiels aktualisieren, gehen Sie daher wie unter [Direct3D11-Bereitstellung für Spielentwickler](https://msdn.microsoft.com/library/windows/desktop/ee416644) beschrieben vor.</span><span class="sxs-lookup"><span data-stu-id="056b6-141">Win32 desktop applications still use DirectSetup, so if you are also upgrading the desktop version of your game see [Direct3D 11 Deployment for Game Developers](https://msdn.microsoft.com/library/windows/desktop/ee416644).</span></span>

## <a name="is-there-any-way-i-can-update-my-desktop-code-to-directx-11-before-moving-away-from-effects"></a><span data-ttu-id="056b6-142">Kann ich meinen Desktopcode vor der Umstellung von Effects auf DirectX11 aktualisieren?</span><span class="sxs-lookup"><span data-stu-id="056b6-142">Is there any way I can update my desktop code to DirectX 11 before moving away from Effects?</span></span>


<span data-ttu-id="056b6-143">Siehe [Effects für Direct3D11-Update](http://go.microsoft.com/fwlink/p/?LinkId=271568).</span><span class="sxs-lookup"><span data-stu-id="056b6-143">See the [Effects for Direct3D 11 Update](http://go.microsoft.com/fwlink/p/?LinkId=271568).</span></span> <span data-ttu-id="056b6-144">Mit Effects11 können Abhängigkeiten von älteren DirectX-SDK-Headern entfernt werden. Es ist als Portierungshilfsmittel vorgesehen und kann nur für Desktop-Apps verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="056b6-144">Effects 11 helps remove dependencies on legacy DirectX SDK headers; it's intended for use as a porting aid and can only be used with desktop apps.</span></span>

##  <a name="is-there-a-path-for-porting-my-directx-8-game-to-uwp"></a><span data-ttu-id="056b6-145">Gibt es einen Pfad für die Portierung meines DirectX8-Spiels zu UWP?</span><span class="sxs-lookup"><span data-stu-id="056b6-145">Is there a path for porting my DirectX 8 game to UWP?</span></span>


<span data-ttu-id="056b6-146">Ja:</span><span class="sxs-lookup"><span data-stu-id="056b6-146">Yes:</span></span>

-   <span data-ttu-id="056b6-147">Lesen Sie [Konvertieren in Direct3D9](https://msdn.microsoft.com/library/windows/desktop/bb204851).</span><span class="sxs-lookup"><span data-stu-id="056b6-147">Read [Converting to Direct3D 9](https://msdn.microsoft.com/library/windows/desktop/bb204851).</span></span>
-   <span data-ttu-id="056b6-148">Stellen Sie sicher, dass Ihr Spiel keine Überreste der festen Pipeline enthält (siehe [Veraltete Funktionen](https://msdn.microsoft.com/library/windows/desktop/cc308047)).</span><span class="sxs-lookup"><span data-stu-id="056b6-148">Make sure your game has no remnants of the fixed pipeline - see [Deprecated Features](https://msdn.microsoft.com/library/windows/desktop/cc308047).</span></span>
-   <span data-ttu-id="056b6-149">Verwenden Sie anschließend den DirectX9-Portierungspfad: [Portieren von D3D9 zu UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md).</span><span class="sxs-lookup"><span data-stu-id="056b6-149">Then take the DirectX 9 porting path: [Port from D3D 9 to UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md).</span></span>

##  <a name="can-i-port-my-directx-10-or-11-game-to-uwp"></a><span data-ttu-id="056b6-150">Kann ich mein DirectX10- oder 11-Spiel zu UWP portieren?</span><span class="sxs-lookup"><span data-stu-id="056b6-150">Can I port my DirectX 10 or 11 game to UWP?</span></span>


<span data-ttu-id="056b6-151">DirectX10.x- und 11-Desktopspiele können ohne großen Aufwand zu UWP portiert werden.</span><span class="sxs-lookup"><span data-stu-id="056b6-151">DirectX 10.x and 11 desktop games are easy to port to UWP.</span></span> <span data-ttu-id="056b6-152">Siehe [Migrieren zu Direct3D11](https://msdn.microsoft.com/library/windows/desktop/ff476190).</span><span class="sxs-lookup"><span data-stu-id="056b6-152">See [Migrating to Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476190).</span></span>

## <a name="how-do-i-choose-the-right-display-device-in-a-multi-monitor-system"></a><span data-ttu-id="056b6-153">Wie wähle ich bei einem Multi-Monitor-System das richtige Anzeigegerät aus?</span><span class="sxs-lookup"><span data-stu-id="056b6-153">How do I choose the right display device in a multi-monitor system?</span></span>


<span data-ttu-id="056b6-154">Der Benutzer wählt aus, auf welchem Monitor Ihre App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="056b6-154">The user selects which monitor your app is displayed on.</span></span> <span data-ttu-id="056b6-155">Rufen Sie [**D3D11CreateDevice**](https://msdn.microsoft.com/library/windows/desktop/ff476082) auf, und legen Sie den ersten Parameter auf **nullptr** fest, damit Windows den korrekten Adapter auswählt.</span><span class="sxs-lookup"><span data-stu-id="056b6-155">Let Windows provide the correct adapter by calling [**D3D11CreateDevice**](https://msdn.microsoft.com/library/windows/desktop/ff476082) with the first parameter set to **nullptr**.</span></span> <span data-ttu-id="056b6-156">Rufen Sie anschließend die [**IDXGIDevice interface**](https://msdn.microsoft.com/library/windows/desktop/bb174527) des Geräts ab, rufen Sie [**GetAdapter**](https://msdn.microsoft.com/library/windows/desktop/bb174531) auf, und erstellen Sie die Swapchain mit dem DXGI-Adapter.</span><span class="sxs-lookup"><span data-stu-id="056b6-156">Then get the device's [**IDXGIDevice interface**](https://msdn.microsoft.com/library/windows/desktop/bb174527), call [**GetAdapter**](https://msdn.microsoft.com/library/windows/desktop/bb174531) and use the DXGI adapter to create the swap chain.</span></span>

## <a name="how-do-i-turn-on-antialiasing"></a><span data-ttu-id="056b6-157">Wie aktiviere ich Antialiasing?</span><span class="sxs-lookup"><span data-stu-id="056b6-157">How do I turn on antialiasing?</span></span>


<span data-ttu-id="056b6-158">Antialiasing (Multisampling) wird beim Erstellen des Direct3D-Geräts aktiviert.</span><span class="sxs-lookup"><span data-stu-id="056b6-158">Antialiasing (multisampling) is enabled when you create the Direct3D device.</span></span> <span data-ttu-id="056b6-159">Listen Sie die Multisamplingunterstützung auf, indem Sie [**CheckMultisampleQualityLevels**](https://msdn.microsoft.com/library/windows/desktop/ff476499) aufrufen, und legen Sie dann Multisamplingoptionen in der [**DXGI\_SAMPLE\_DESC-Struktur**](https://msdn.microsoft.com/library/windows/desktop/bb173072) fest, wenn Sie [**CreateSurface**](https://msdn.microsoft.com/library/windows/desktop/bb174530) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="056b6-159">Enumerate multisampling support by calling [**CheckMultisampleQualityLevels**](https://msdn.microsoft.com/library/windows/desktop/ff476499), then set multisample options in the [**DXGI\_SAMPLE\_DESC structure**](https://msdn.microsoft.com/library/windows/desktop/bb173072) when you call [**CreateSurface**](https://msdn.microsoft.com/library/windows/desktop/bb174530).</span></span>

## <a name="my-game-renders-using-multithreading-andor-deferred-rendering-what-do-i-need-to-know-for-direct3d-11"></a><span data-ttu-id="056b6-160">Mein Spiel rendert mit Multithreading und/oder verzögertem Rendering.</span><span class="sxs-lookup"><span data-stu-id="056b6-160">My game renders using multithreading and/or deferred rendering.</span></span> <span data-ttu-id="056b6-161">Was muss ich in diesem Zusammenhang bei Direct3D11 beachten?</span><span class="sxs-lookup"><span data-stu-id="056b6-161">What do I need to know for Direct3D 11?</span></span>


<span data-ttu-id="056b6-162">Lesen Sie [Einführung in das Multithreading in Direct3D11](https://msdn.microsoft.com/library/windows/desktop/ff476891). Dort werden die ersten Schritte erläutert.</span><span class="sxs-lookup"><span data-stu-id="056b6-162">Visit [Introduction to Multithreading in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476891) to get started.</span></span> <span data-ttu-id="056b6-163">Eine Liste der wichtigsten Unterschiede finden Sie unter [Unterschiede beim Threading zwischen Direct3D-Versionen](https://msdn.microsoft.com/library/windows/desktop/ff476890).</span><span class="sxs-lookup"><span data-stu-id="056b6-163">For a list of key differences, see [Threading Differences between Direct3D Versions](https://msdn.microsoft.com/library/windows/desktop/ff476890).</span></span> <span data-ttu-id="056b6-164">Beachten Sie, dass beim verzögerten Rendering ein *verzögerter Gerätekontext* anstelle eines *unmittelbaren Kontextes* verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="056b6-164">Note that deferred rendering uses a device *deferred context* instead of an *immediate context*.</span></span>

## <a name="where-can-i-read-more-about-the-programmable-pipeline-since-direct3d-9"></a><span data-ttu-id="056b6-165">Wo finde ich weitere Informationen zur programmierbaren Pipeline seit Direct3D9?</span><span class="sxs-lookup"><span data-stu-id="056b6-165">Where can I read more about the programmable pipeline since Direct3D 9?</span></span>


<span data-ttu-id="056b6-166">Lesen Sie die folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="056b6-166">Visit the following topics:</span></span>

-   [<span data-ttu-id="056b6-167">Programmieranleitung für HLSL</span><span class="sxs-lookup"><span data-stu-id="056b6-167">Programming Guide for HLSL</span></span>](https://msdn.microsoft.com/library/windows/desktop/bb509635)
-   [<span data-ttu-id="056b6-168">Häufig gestellte Fragen zu Direct3D10</span><span class="sxs-lookup"><span data-stu-id="056b6-168">Direct3D 10 Frequently Asked Questions</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee416643)

## <a name="what-should-i-use-instead-of-the-x-file-format-for-my-models"></a><span data-ttu-id="056b6-169">Was sollte ich anstelle des X-Dateiformats für meine Modelle verwenden?</span><span class="sxs-lookup"><span data-stu-id="056b6-169">What should I use instead of the .x file format for my models?</span></span>


<span data-ttu-id="056b6-170">Es gibt zwar keinen offiziellen Ersatz für das X-Dateiformat, in vielen Beispielen wird aber das SDKMesh-Format verwendet.</span><span class="sxs-lookup"><span data-stu-id="056b6-170">While we don’t have an official replacement for the .x file format, many of the samples utilize the SDKMesh format.</span></span> <span data-ttu-id="056b6-171">Visual Studio bietet außerdem eine [Inhaltspipeline](https://msdn.microsoft.com/library/windows/apps/hh972446.aspx), die verschiedene gängige Formate in CMO-Dateien kompiliert, die mit Code aus dem Visual Studio3D-Starter Kit oder mit dem [DirectXTK](http://go.microsoft.com/fwlink/p/?LinkID=248929) geladen werden können.</span><span class="sxs-lookup"><span data-stu-id="056b6-171">Visual Studio also has a [content pipeline](https://msdn.microsoft.com/library/windows/apps/hh972446.aspx) that compiles several popular formats into CMO files that can be loaded with code from the Visual Studio 3D starter kit, or loaded using the [DirectXTK](http://go.microsoft.com/fwlink/p/?LinkID=248929).</span></span>

## <a name="how-do-i-debug-my-shaders"></a><span data-ttu-id="056b6-172">Wie debugge ich meine Shader?</span><span class="sxs-lookup"><span data-stu-id="056b6-172">How do I debug my shaders?</span></span>


<span data-ttu-id="056b6-173">Microsoft Visual Studio2015 umfasst Diagnosetools für DirectX-Grafiken.</span><span class="sxs-lookup"><span data-stu-id="056b6-173">Microsoft Visual Studio2015 includes diagnostic tools for DirectX graphics.</span></span> <span data-ttu-id="056b6-174">Siehe [Debuggen von DirectX-Grafiken](https://msdn.microsoft.com/library/windows/apps/hh315751.aspx).</span><span class="sxs-lookup"><span data-stu-id="056b6-174">See [Debugging DirectX Graphics](https://msdn.microsoft.com/library/windows/apps/hh315751.aspx).</span></span>

##  <a name="what-is-the-direct3d-11-equivalent-for-x-function"></a><span data-ttu-id="056b6-175">Was ist das Direct3D11-Äquivalent für die *x*-Funktion?</span><span class="sxs-lookup"><span data-stu-id="056b6-175">What is the Direct3D 11 equivalent for *x* function?</span></span>


<span data-ttu-id="056b6-176">Informationen hierzu finden Sie in der [Funktionszuordnung](feature-mapping.md#function-mapping) in „Zuordnung von DirectX9-Features zu DirectX11-APIs“.</span><span class="sxs-lookup"><span data-stu-id="056b6-176">See the [function mapping](feature-mapping.md#function-mapping) provided in Map DirectX 9 features to DirectX 11 APIs.</span></span>

##  <a name="what-is-the-dxgiformat-equivalent-of-y-surface-format"></a><span data-ttu-id="056b6-177">Was ist das DXGI\_FORMAT-Äquivalent des *y*-Oberflächenformats?</span><span class="sxs-lookup"><span data-stu-id="056b6-177">What is the DXGI\_FORMAT equivalent of *y* surface format?</span></span>


<span data-ttu-id="056b6-178">Informationen hierzu finden Sie in der [Oberflächenformatzuordnung](feature-mapping.md#surface-format-mapping) in „Zuordnung von DirectX9-Funktionen zu DirectX11-APIs“.</span><span class="sxs-lookup"><span data-stu-id="056b6-178">See the [surface format mapping](feature-mapping.md#surface-format-mapping) provided in Map DirectX 9 features to DirectX 11 APIs.</span></span>

 

 




