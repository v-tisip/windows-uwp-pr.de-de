---
description: ''
title: Inhalte als Objekte
template: detail.hbs
ms.localizationpriority: medium
ms.openlocfilehash: ed2ac8530d69929cc0e0e921cfb1cc5368058cd2
ms.sourcegitcommit: 7d0e6662de336a3d0e82ae9d1b61b1b0edb5aeeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2018
ms.locfileid: "8981444"
---
# <a name="content-as-objects"></a><span data-ttu-id="78c28-102">Inhalte als Objekte</span><span class="sxs-lookup"><span data-stu-id="78c28-102">Content as objects</span></span>

 

<span data-ttu-id="78c28-103">Sie können die Tiefe oder z-Reihenfolge von Elementen manipulieren, um eine visuelle Hierarchie zu erstellen, die die Bedienung Ihrer Anwendung erleichtert.</span><span class="sxs-lookup"><span data-stu-id="78c28-103">You can manipulating the depth, or z-order, of elements to create a visual hierarchy that helps makes your app easier to use.</span></span>  

> <span data-ttu-id="78c28-104">Hinweis: Dieser Artikel ist ein früher Entwurf für eine neue Funktion von Windows 10 RS2.</span><span class="sxs-lookup"><span data-stu-id="78c28-104">Note: This article is an early draft for a new feature of Windows 10 RS2.</span></span> <span data-ttu-id="78c28-105">Featurenamen, Terminologie und Funktionen sind nicht endgültig.</span><span class="sxs-lookup"><span data-stu-id="78c28-105">Feature names, terminology, and functionality are not final.</span></span> 

## <a name="why-visual-hierarchy-is-important"></a><span data-ttu-id="78c28-106">Warum visuelle Hierarchie wichtig ist</span><span class="sxs-lookup"><span data-stu-id="78c28-106">Why visual hierarchy is important</span></span>

<span data-ttu-id="78c28-107">Die Benutzer werden ständig mit Anfragen nach ihrer Aufmerksamkeit bombardiert.</span><span class="sxs-lookup"><span data-stu-id="78c28-107">Users are constantly being bombarded with requests for their attention.</span></span> <span data-ttu-id="78c28-108">Jedes Element auf dem Bildschirm bittet darum, betrachtet zu werden, jeder Text will gelesen werden, jeder Button angeklickt werden.</span><span class="sxs-lookup"><span data-stu-id="78c28-108">Every element on the screen begs to be looked at, every string of text wants to be read, every button clicked.</span></span> <span data-ttu-id="78c28-109">Da die visuelle Umgebung immer chaotischer und chaotischer wird, erfordert es mehr Mühe, die Szene zu analysieren und herauszufinden, was vor sich geht.</span><span class="sxs-lookup"><span data-stu-id="78c28-109">As the visual environment grows more jumbled and chaotic, it takes more effort to parse the scene and figure out what's going on.</span></span>  

<span data-ttu-id="78c28-110">Deshalb ist es so wichtig, die Elemente Ihrer Benutzeroberfläche sorgfältig auszuwählen und ein Layout zu erstellen, das eine klare visuelle Hierarchie zwischen Ihren UI-Elementen herstellt.</span><span class="sxs-lookup"><span data-stu-id="78c28-110">That's why it's so important to carefully select the elements of your user interface, and why it's important to create a layout that establishes a clear visual hierarchy among your UI elements.</span></span> <!-- Every element is competing for the user's attention, and every time you add an element, you add a mental tax to the user. -->

<span data-ttu-id="78c28-111">Eine klare visuelle Hierarchie sagt dem Benutzer, welche Elemente am wichtigsten sind und schafft Beziehungen zwischen den Elementen.</span><span class="sxs-lookup"><span data-stu-id="78c28-111">A clear visual hierarchy tells users which elements are the most important and creates relationships between the elements.</span></span> <span data-ttu-id="78c28-112">Mit einer guten visuellen Hierarchie versteht der Benutzer das Layout der Seite auf einen Blick und kann sich auf seine Aufgabe konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="78c28-112">With a good visual hierarchy, users understand the layout of the page at a glance and can focus on the task they're trying to accomplish.</span></span> 

<p></p>


<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  <p><span data-ttu-id="78c28-113">Wie schafft man also eine klare visuelle Hierarchie?</span><span class="sxs-lookup"><span data-stu-id="78c28-113">So, how do you create a clear visual hierarchy?</span></span> <span data-ttu-id="78c28-114">In früheren Versionen von Windows 10 konnten Sie Leerraum, Position und Typografie verwenden, um eine visuelle Hierarchie zu definieren.</span><span class="sxs-lookup"><span data-stu-id="78c28-114">With earlier versions of Windows 10, you could use white space, position, and typography to define a visual hierarchy.</span></span> </p>
  </div>
  <div class="side-by-side-content-right">
    <a href="images/content-as-objects/flat-layout.png"><span data-ttu-id="78c28-115">Ein flaches Layout</span><span class="sxs-lookup"><span data-stu-id="78c28-115">A flat layout</span></span></a>
    
  </div>
</div>
</div>

<span data-ttu-id="78c28-116">Mit Windows 10 RS2 haben wir buchstäblich eine weitere Dimension hinzugefügt: die Tiefe.</span><span class="sxs-lookup"><span data-stu-id="78c28-116">With Windows 10 RS2, we literally added another dimension: depth.</span></span> 

<a href="images/content-as-objects/depth-in-layout2.png"><span data-ttu-id="78c28-117">Tiefe im Layout</span><span class="sxs-lookup"><span data-stu-id="78c28-117">Depth in layout</span></span></a>


## <a name="use-depth-to-establish-a-hierarchy"></a><span data-ttu-id="78c28-118">Aufbau einer Hierarchie über Tiefe</span><span class="sxs-lookup"><span data-stu-id="78c28-118">Use depth to establish a hierarchy</span></span> 

<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
     <p><span data-ttu-id="78c28-119">Sie können die Tiefe (z-Reihenfolge) zusammen mit Ihren anderen Designtools (Leerraum, Position, Typografie) verwenden, um eine Hierarchie aufzubauen.</span><span class="sxs-lookup"><span data-stu-id="78c28-119">You can use depth (z-order), along with your other design tools (whitespace, position, typography) to establish a hierarchy.</span></span> <span data-ttu-id="78c28-120">Heben Sie Ihre wichtigsten Elemente auf die vorderste Ebene; verwenden Sie die unteren Ebenen, um eine weniger kritische Benutzeroberfläche anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="78c28-120">Elevate your most important elements to the forward-most layer; use lower layers to display less critical UI.</span></span> 

    The relative importance of an element can change throughout an experience, so you can bring elements forward as they become more important and backward as they become less important. 
    </p>
  </div>
  <div class="side-by-side-content-right">
    <a href="images/content-as-objects/elements-forward-backward.png"><span data-ttu-id="78c28-121">Tiefe im Layout</span><span class="sxs-lookup"><span data-stu-id="78c28-121">Depth in layout</span></span></a> 
    
  </div>
</div>
</div>

## <a name="how-does-it-work"></a><span data-ttu-id="78c28-122">Wie funktioniert das?</span><span class="sxs-lookup"><span data-stu-id="78c28-122">How does it work?</span></span>
> <span data-ttu-id="78c28-123">TODO: Kurze Beschreibung, wie Sie die z-Reihenfolge der Elemente steuern können.</span><span class="sxs-lookup"><span data-stu-id="78c28-123">TODO: Brief description of how you can control the z-order of elements.</span></span> <span data-ttu-id="78c28-124">Ist die z-Reihenfolge explizit fest implementiert, oder gibt es ein semantisches Ranking-System?</span><span class="sxs-lookup"><span data-stu-id="78c28-124">To you explicitly hard-code the z-order, or is there a semantic ranking system?</span></span> <span data-ttu-id="78c28-125">Wie bewegen sich Objekte von einer Ebene zur anderen?</span><span class="sxs-lookup"><span data-stu-id="78c28-125">How do items move from one layer to another?</span></span> <span data-ttu-id="78c28-126">Was macht das System automatisch, und worüber müssen sich Designer/Entwickler Gedanken machen?</span><span class="sxs-lookup"><span data-stu-id="78c28-126">What does the system do automatically, and what do designers/developers need to worry about?</span></span> 

## <a name="the-four-layers-of-a-typical-app-layers"></a><span data-ttu-id="78c28-127">Die vier Ebenen einer typischen App</span><span class="sxs-lookup"><span data-stu-id="78c28-127">The four layers of a typical app layers</span></span>

<p><span data-ttu-id="78c28-128">Eine typische App besteht aus 4 Ebenen.</span><span class="sxs-lookup"><span data-stu-id="78c28-128">A typical app has 4 layers.</span></span></p>
<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left"><span data-ttu-id="78c28-129">
<b>Hinter dem Hintergrund</b> Diese Ebene liegt hinter der app.</span><span class="sxs-lookup"><span data-stu-id="78c28-129">
<b>Beyond background</b> This layer lives behind the app.</span></span>  <span data-ttu-id="78c28-130">Wenn Elemente auf diese Ebene verschoben werden, empfehlen wir, sie nicht interaktiv zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="78c28-130">When elements move to this layer, we recommend making them non-interactive.</span></span> <span data-ttu-id="78c28-131">Elemente auf dieser Ebene haben den langsamsten Parallax-Effekt und werden auf das App-Fenster beschnitten.</span><span class="sxs-lookup"><span data-stu-id="78c28-131">Elements at this layer has the slowest parallax and are clipped to the app window.</span></span> <span data-ttu-id="78c28-132">TODO: Ist diese Ebene skalierbar?</span><span class="sxs-lookup"><span data-stu-id="78c28-132">TODO: Does this layer scale?</span></span> 

<p><span data-ttu-id="78c28-133">Beispiele für Hintergrundelemente sind das Bild hinter dem Inhalt, TODO: Beispiel, TODO: Beispiel.</span><span class="sxs-lookup"><span data-stu-id="78c28-133">Example background elements include image behind content, TODO: Example, TODO: Example.</span></span></p>
  </div>
  <div class="side-by-side-content-right">
    <a href="images/content-as-objects/elements-forward-backward.png"><span data-ttu-id="78c28-134">Die Hintergrundebene einer App</span><span class="sxs-lookup"><span data-stu-id="78c28-134">The beyond background layer of an app</span></span></a>
    
  </div>
</div>
</div>

<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left"><span data-ttu-id="78c28-135">
<b>Passive Ebene</b> Dies ist die Basisebene der app, in denen UI-Elemente in der Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="78c28-135">
<b>Passive layer</b> This is the base layer of the app, where UI elements live by default.</span></span>  <span data-ttu-id="78c28-136">Elemente bewegen sich auf dieser Ebene in Echtzeit (keine Parallax-Effekt). Sie werden auf das App-Fenster beschnitten und auf 100 % skaliert.</span><span class="sxs-lookup"><span data-stu-id="78c28-136">Elements move in real-time on this layer (no parallax), are clipped to the app window, and are rendered at 100% scale.</span></span> 

<p><span data-ttu-id="78c28-137">Beispielelemente: Der App-Hintergrund, der Text, das sekundäre UI, wie z. B. das App-Navigations-UI.</span><span class="sxs-lookup"><span data-stu-id="78c28-137">Example elements: The app background, text, secondary UI, such as app navigation UI.</span></span></p>
  </div>
  <div class="side-by-side-content-right">
    <a href="images/content-as-objects/elements-forward-backward.png"><span data-ttu-id="78c28-138">Die passive Ebene einer App</span><span class="sxs-lookup"><span data-stu-id="78c28-138">The passive layer of an app</span></span></a>
    
  </div>
</div>
</div>

<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left"><span data-ttu-id="78c28-139">
<b>Handlungsaufforderungen</b> Diese Ebene ist für interaktive Elemente, die Sie über Elemente auf der passiven Ebene priorisieren.</span><span class="sxs-lookup"><span data-stu-id="78c28-139">
<b>Calls to action</b> This layer is for interactive items that you prioritize above passive layer elements.</span></span> <span data-ttu-id="78c28-140">Elemente auf dieser Ebene haben einen mittleren Parallax-Effekt und werden auf das App-Fenster beschnitten.</span><span class="sxs-lookup"><span data-stu-id="78c28-140">Elements on this layer have medium parallax and are clipped to the app window.</span></span> <span data-ttu-id="78c28-141">TODO: Skalieren Elemente auf dieser Ebene oder haben sie einen Schlagschatten?</span><span class="sxs-lookup"><span data-stu-id="78c28-141">TODO: Do elements at this layer scale or have a drop shadow?</span></span>

<p><span data-ttu-id="78c28-142">Beispielelemente: Listen, Raster, primäre Befehle (TODO: z.B.....).</span><span class="sxs-lookup"><span data-stu-id="78c28-142">Example elements: lists, grids, primary commands (TODO: Such as...).</span></span></p> 
  </div>
  <div class="side-by-side-content-right">
    <a href="images/content-as-objects/elements-forward-backward.png"><span data-ttu-id="78c28-143">Die Call-to-Action-Schicht einer App</span><span class="sxs-lookup"><span data-stu-id="78c28-143">The call-to-action layer of an app</span></span></a>
    
  </div>
</div>
</div>

<p></p>
<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left"><span data-ttu-id="78c28-144">
<b>Hero-Ebene</b> Diese Ebene ist für das Element mit der höchsten Priorität auf dem Bildschirm zum Zeitpunkt.</span><span class="sxs-lookup"><span data-stu-id="78c28-144">
<b>Hero layer</b> This layer is for the highest priority element on the screen at the time.</span></span>  <span data-ttu-id="78c28-145">Elemente auf dieser Ebene können die Grenzen des App-Fensters sprengen, sie können skalieren, und sie erhalten automatisch einen Schlagschatten.</span><span class="sxs-lookup"><span data-stu-id="78c28-145">Elements on this layer can break the bounds of the app window, they can scale, and they automatically get a drop shadow.</span></span>

<p><span data-ttu-id="78c28-146">Beispielelemente: fotografische Elemente, das aktuell ausgewählte Element.</span><span class="sxs-lookup"><span data-stu-id="78c28-146">Example elements: photographic elements, the currently selected item.</span></span></p>  
  </div>
  <div class="side-by-side-content-right">
    <a href="images/content-as-objects/elements-forward-backward.png"><span data-ttu-id="78c28-147">Die Hero-Ebene einer App</span><span class="sxs-lookup"><span data-stu-id="78c28-147">The hero layer of an app</span></span></a>
    
  </div>
</div>
</div>



<!--
Depth is meaningful; it establishes visual and interactive hierarchy for users to efficiently complete tasks. Depth orients users in our system. 
-->

## <a name="example-tbd"></a><span data-ttu-id="78c28-148">Beispiel: TBD</span><span class="sxs-lookup"><span data-stu-id="78c28-148">Example: TBD</span></span>
> <span data-ttu-id="78c28-149">TODO: Zeigen, wie man ein gemeinsames UI-Muster für die Verwendung der z-Reihenfolge anpasst.</span><span class="sxs-lookup"><span data-stu-id="78c28-149">TODO: Show how to adapt a common UI pattern to use z-ordering.</span></span> <span data-ttu-id="78c28-150">Wir sollten Illustrationen und Code zeigen.</span><span class="sxs-lookup"><span data-stu-id="78c28-150">We should show illustrations and code.</span></span> 

## <a name="download-the-code-samples"></a><span data-ttu-id="78c28-151">Codebeispiele herunterladen</span><span class="sxs-lookup"><span data-stu-id="78c28-151">Download the code samples</span></span>
><span data-ttu-id="78c28-152">TODO: Link zu Beispielen, die diese Funktion demonstrieren.</span><span class="sxs-lookup"><span data-stu-id="78c28-152">TODO: Link to samples that demonstrate this feature.</span></span> 


## <a name="related-articles"></a><span data-ttu-id="78c28-153">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="78c28-153">Related articles</span></span>
* [<span data-ttu-id="78c28-154">Inhaltsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="78c28-154">Content basics</span></span>](../basics/content-basics.md)
