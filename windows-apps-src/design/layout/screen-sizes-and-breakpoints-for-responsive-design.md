---
author: mijacobs
title: Bildschirmgrößen und Haltepunkte für reaktionsfähiges Design
description: Anstatt Ihre Benutzeroberfläche für die vielen Geräte im gesamten Windows 10-Ökosystem zu optimieren, empfehlen wir, ein Design für einige Schlüsselbreiten (sogenannte Breakpoints) zu erstellen.
ms.author: mijacobs
ms.date: 08/30/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 0d84530c1a7c3795c566495c1eae121691b0766a
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "1688936"
---
#  <a name="screen-sizes-and-breakpoints"></a><span data-ttu-id="9075c-104">Bildschirmgrößen und Breakpoints</span><span class="sxs-lookup"><span data-stu-id="9075c-104">Screen sizes and breakpoints</span></span>

<span data-ttu-id="9075c-105">UWP-Apps können auf jedem Gerät mit Windows 10 ausgeführt werden – z. B. Telefone, Tablets, Desktops, Fernseher und mehr.</span><span class="sxs-lookup"><span data-stu-id="9075c-105">UWP apps can run on any device running Windows 10, which includes phones, tablets, desktops, TVs, and more.</span></span> <span data-ttu-id="9075c-106">Anstatt Ihre Benutzeroberfläche für die vielen Geräte im gesamten Windows 10-Ökosystem zu optimieren, empfehlen wir, ein Design für einige Schlüsselbreiten (sogenannte Breakpoints) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9075c-106">With a huge number of device targets and screen sizes across the Windows 10 ecosystem, rather than optimizing your UI for each device, we recommended designing for a few key width categories (also called "breakpoints"):</span></span> 
- <span data-ttu-id="9075c-107">Klein (kleiner als 640 Pixel)</span><span class="sxs-lookup"><span data-stu-id="9075c-107">Small (smaller than 640px)</span></span>
- <span data-ttu-id="9075c-108">Mittel (641 Pixel bis 1007 Pixel)</span><span class="sxs-lookup"><span data-stu-id="9075c-108">Medium (641px to 1007px)</span></span>
- <span data-ttu-id="9075c-109">Groß (1008 Pixel und größer)</span><span class="sxs-lookup"><span data-stu-id="9075c-109">Large (1008px and larger)</span></span>

> [!TIP]
> <span data-ttu-id="9075c-110">Beim Entwerfen für bestimmte Breakpoints sollten Sie den für Ihre App verfügbaren Bildschirmbereich (App-Fenster) berücksichtigen, nicht die Bildschirmgröße.</span><span class="sxs-lookup"><span data-stu-id="9075c-110">When designing for specific breakpoints, design for the amount of screen space available to your app (the app's window), not the screen size.</span></span> <span data-ttu-id="9075c-111">Wenn die App im Vollbildmodus läuft, hat das App-Fenster die gleiche Größe wie der Bildschirm, aber wenn die App nicht im Vollbildmodus ist, ist das Fenster kleiner als der Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="9075c-111">When the app is running full-screen, the app window is the same size as the screen, but when the app is not full-screen, the window is smaller than the screen.</span></span>

## <a name="breakpoints"></a><span data-ttu-id="9075c-112">Breakpoints</span><span class="sxs-lookup"><span data-stu-id="9075c-112">Breakpoints</span></span>
<span data-ttu-id="9075c-113">Diese Tabelle beschreibt die verschiedenen Größenklassen und Breakpoints.</span><span class="sxs-lookup"><span data-stu-id="9075c-113">This table describes the different size classes and breakpoints.</span></span>

![Reaktionsfähige Design-Breakpoints](images/rsp-design/rspd-breakpoints.png)

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="9075c-115">Größenklasse</span><span class="sxs-lookup"><span data-stu-id="9075c-115">Size class</span></span></th>
<th align="left"><span data-ttu-id="9075c-116">Breakpoints</span><span class="sxs-lookup"><span data-stu-id="9075c-116">Breakpoints</span></span></th>
<th align="left"><span data-ttu-id="9075c-117">Bildschirmgröße (diagonal)</span><span class="sxs-lookup"><span data-stu-id="9075c-117">Screen size (diagonal)</span></span></th>
<th align="left"><span data-ttu-id="9075c-118">Geräte</span><span class="sxs-lookup"><span data-stu-id="9075c-118">Devices</span></span></th>
<th align="left"><span data-ttu-id="9075c-119">Fenstergrößen</span><span class="sxs-lookup"><span data-stu-id="9075c-119">Window sizes</span></span></th>
</tr>
</thead>
<tbody>
<tr class="even">
<td style="vertical-align:top;"><span data-ttu-id="9075c-120">Klein</span><span class="sxs-lookup"><span data-stu-id="9075c-120">Small</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-121">640 Pixel oder weniger</span><span class="sxs-lookup"><span data-stu-id="9075c-121">640px or less</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-122">4&quot; bis 6&quot;</span><span class="sxs-lookup"><span data-stu-id="9075c-122">4&quot; to 6&quot;</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-123">Smartphones</span><span class="sxs-lookup"><span data-stu-id="9075c-123">Phones</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-124">320 x 569, 360 x 640, 480 x 854</span><span class="sxs-lookup"><span data-stu-id="9075c-124">320x569, 360x640, 480x854</span></span></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><span data-ttu-id="9075c-125">Mittel</span><span class="sxs-lookup"><span data-stu-id="9075c-125">Medium</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-126">641 Pixel bis 1007 Pixel</span><span class="sxs-lookup"><span data-stu-id="9075c-126">641px to 1007px</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-127">7&quot; bis 12&quot;</span><span class="sxs-lookup"><span data-stu-id="9075c-127">7&quot; to 12&quot;</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-128">Phablets, Tablets, TV-Geräte</span><span class="sxs-lookup"><span data-stu-id="9075c-128">Phablets, tablets, TVs</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-129">960 x 540</span><span class="sxs-lookup"><span data-stu-id="9075c-129">960x540</span></span></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><span data-ttu-id="9075c-130">Groß</span><span class="sxs-lookup"><span data-stu-id="9075c-130">Large</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-131">1008 Pixel oder größer</span><span class="sxs-lookup"><span data-stu-id="9075c-131">1008px or greater</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-132">13&quot; und größer</span><span class="sxs-lookup"><span data-stu-id="9075c-132">13&quot; and larger</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-133">PCs, Laptops, Surface Hubs</span><span class="sxs-lookup"><span data-stu-id="9075c-133">PCs, laptops, Surface Hubs</span></span></td>
<td style="vertical-align:top;"><span data-ttu-id="9075c-134">1024 x 640, 1366 x 768, 1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="9075c-134">1024x640, 1366x768, 1920x1080</span></span></td>
</tr>
</tbody>
</table>

## <a name="general-recommendations"></a><span data-ttu-id="9075c-135">Allgemeine Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9075c-135">General recommendations</span></span>

### <a name="small"></a><span data-ttu-id="9075c-136">Klein</span><span class="sxs-lookup"><span data-stu-id="9075c-136">Small</span></span>
- <span data-ttu-id="9075c-137">Legen Sie den linken und den rechten Fensterrand auf 12px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="9075c-137">Set left and right window margins to 12px to create a visual separation between the left and right edges of the app window.</span></span>
- <span data-ttu-id="9075c-138">Docken Sie [App-Leisten](../controls-and-patterns/app-bars.md) für bessere Erreichbarkeit am unteren Fensterrand an.</span><span class="sxs-lookup"><span data-stu-id="9075c-138">Dock [app bars](../controls-and-patterns/app-bars.md) to the bottom of the window for improved reachability.</span></span>
- <span data-ttu-id="9075c-139">Verwenden Sie jeweils eine Spalte/Region.</span><span class="sxs-lookup"><span data-stu-id="9075c-139">Use one column/region at a time.</span></span>
- <span data-ttu-id="9075c-140">Verwenden Sie ein Symbol zum Darstellen der Suche (kein Suchfeld anzeigen).</span><span class="sxs-lookup"><span data-stu-id="9075c-140">Use an icon to represent search (don't show a search box).</span></span>
- <span data-ttu-id="9075c-141">Verwenden Sie den [Navigationsbereich](../controls-and-patterns/navigationview.md) im Überlagerungsmodus, um Platz auf dem Bildschirm zu sparen.</span><span class="sxs-lookup"><span data-stu-id="9075c-141">Put the [navigation pane](../controls-and-patterns/navigationview.md) in overlay mode to conserve screen space.</span></span>
- <span data-ttu-id="9075c-142">Verwenden Sie für das [Master/Details-Modell](../controls-and-patterns/master-details.md) den gestapelten Darstellungsmodus, um Platz auf dem Bildschirm zu sparen.</span><span class="sxs-lookup"><span data-stu-id="9075c-142">If you're using the [master details pattern](../controls-and-patterns/master-details.md), use the stacked presentation mode to save screen space.</span></span>

### <a name="medium"></a><span data-ttu-id="9075c-143">Mittel</span><span class="sxs-lookup"><span data-stu-id="9075c-143">Medium</span></span>
- <span data-ttu-id="9075c-144">Legen Sie den linken und den rechten Fensterrand auf 24px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="9075c-144">Set left and right window margins to 24px to create a visual separation between the left and right edges of the app window.</span></span>
- <span data-ttu-id="9075c-145">Positionieren Sie Elemente wie [App-Leisten](../controls-and-patterns/app-bars.md) am oberen Rand des App-Fensters.</span><span class="sxs-lookup"><span data-stu-id="9075c-145">Put command elements like [app bars](../controls-and-patterns/app-bars.md) at the top of the app window.</span></span>
- <span data-ttu-id="9075c-146">Verwenden Sie bis zu zwei Spalten/Regionen.</span><span class="sxs-lookup"><span data-stu-id="9075c-146">Use up to two columns/regions.</span></span>
- <span data-ttu-id="9075c-147">Zeigen Sie das Suchfeld an.</span><span class="sxs-lookup"><span data-stu-id="9075c-147">Show the search box.</span></span>
- <span data-ttu-id="9075c-148">Legen Sie für [Navigationsleiste](../controls-and-patterns/navigationview.md) den Streifenmodus fest, sodass immer ein schmaler Streifen mit Symbolen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9075c-148">Put the [navigation pane](../controls-and-patterns/navigationview.md) into sliver mode so a narrow strip of icons always shows.</span></span>
- <span data-ttu-id="9075c-149">Ziehen Sie weitere Anpassungen für [TV-Umgebungen](http://go.microsoft.com/fwlink/?LinkId=760736) in Erwägung.</span><span class="sxs-lookup"><span data-stu-id="9075c-149">Consider further tailoring for [TV experiences](http://go.microsoft.com/fwlink/?LinkId=760736).</span></span>

### <a name="large"></a><span data-ttu-id="9075c-150">Groß</span><span class="sxs-lookup"><span data-stu-id="9075c-150">Large</span></span>
- <span data-ttu-id="9075c-151">Legen Sie den linken und den rechten Fensterrand auf 24px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="9075c-151">Set left and right window margins to 24px to create a visual separation between the left and right edges of the app window.</span></span>
- <span data-ttu-id="9075c-152">Positionieren Sie Elemente wie [App-Leisten](../controls-and-patterns/app-bars.md) am oberen Rand des App-Fensters.</span><span class="sxs-lookup"><span data-stu-id="9075c-152">Put command elements like [app bars](../controls-and-patterns/app-bars.md) at the top of the app window.</span></span>
- <span data-ttu-id="9075c-153">Verwenden Sie bis zu drei Spalten/Regionen.</span><span class="sxs-lookup"><span data-stu-id="9075c-153">Use up to three columns/regions.</span></span>
- <span data-ttu-id="9075c-154">Zeigen Sie das Suchfeld an.</span><span class="sxs-lookup"><span data-stu-id="9075c-154">Show the search box.</span></span>
- <span data-ttu-id="9075c-155">Platzieren Sie den [Navigationsbereich](../controls-and-patterns/navigationview.md) im angedockten Modus so, dass er immer angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9075c-155">Put the [navigation pane](../controls-and-patterns/navigationview.md) into docked mode so that it always shows.</span></span>

>[!TIP] 
> <span data-ttu-id="9075c-156">Mit [**Continuum for Phones**](http://go.microsoft.com/fwlink/p/?LinkID=699431), können Anwender sich mit kompatiblen Windows 10-Mobilgeräten mit einem Bildschirm, einer Maus und einer Tastatur verbinden und damit ihr Gerät wie einen Laptop nutzen.</span><span class="sxs-lookup"><span data-stu-id="9075c-156">With [**Continuum for Phones**](http://go.microsoft.com/fwlink/p/?LinkID=699431), users can connect compatible Windows 10 mobile devices to a monitor, mouse and keyboard to make their phones work like laptops.</span></span> <span data-ttu-id="9075c-157">Berücksichtigen Sie diese neue Funktion beim Entwerfen für bestimmte Breakpoints – ein Mobiltelefon bleibt nicht immer in einer Klasse mit geringer Größe.</span><span class="sxs-lookup"><span data-stu-id="9075c-157">Keep this new capability in mind when designing for specific breakpoints - a mobile phone will not always stay in the size class.</span></span>

## <a name="effective-pixels-and-scale-factor"></a><span data-ttu-id="9075c-158">Effektive Pixel und Skalierungsfaktor</span><span class="sxs-lookup"><span data-stu-id="9075c-158">Effective pixels and scale factor</span></span>

<span data-ttu-id="9075c-159">UWP-Apps skalieren Ihre Benutzeroberfläche automatisch, um sicherzustellen, dass Ihre Anwendung auf allen Windows 10-Geräten lesbar ist.</span><span class="sxs-lookup"><span data-stu-id="9075c-159">UWP apps automatically scale your UI to guarantee that your app will be legible on all Windows 10 devices.</span></span> <span data-ttu-id="9075c-160">Windows wählt automatisch einen Skalierungsfaktor für jede Anzeige aus, basierend auf dem DPI-Wert (Punkte pro Zoll) und dem Betrachtungsabstand des Geräts.</span><span class="sxs-lookup"><span data-stu-id="9075c-160">Windows automatically scales for each display based on its DPI (dots-per-inch) and the viewing distance of the device.</span></span> <span data-ttu-id="9075c-161">Benutzer können den Standardwert überschreiben, indem Sie auf **Einstellungen** > **Anzeige** > **Skalierung und Layout**-Einstellungsseite wechseln.</span><span class="sxs-lookup"><span data-stu-id="9075c-161">Users can override the default value and by going to **Settings** > **Display** > **Scale and layout** settings page.</span></span> 
