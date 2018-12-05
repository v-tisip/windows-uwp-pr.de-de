---
description: ''
title: Inhalte als Objekte
template: detail.hbs
ms.localizationpriority: medium
ms.openlocfilehash: 37ba5093f2d7cfe268be40413b889801daf00967
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8689030"
---
# <a name="content-as-objects"></a><span data-ttu-id="ccf90-102">Inhalte als Objekte</span><span class="sxs-lookup"><span data-stu-id="ccf90-102">Content as objects</span></span>

 

<span data-ttu-id="ccf90-103">Sie können die Tiefe oder z-Reihenfolge von Elementen manipulieren, um eine visuelle Hierarchie zu erstellen, die die Bedienung Ihrer Anwendung erleichtert.</span><span class="sxs-lookup"><span data-stu-id="ccf90-103">You can manipulating the depth, or z-order, of elements to create a visual hierarchy that helps makes your app easier to use.</span></span>  

> <span data-ttu-id="ccf90-104">Hinweis: Dieser Artikel ist ein früher Entwurf für eine neue Funktion von Windows 10 RS2.</span><span class="sxs-lookup"><span data-stu-id="ccf90-104">Note: This article is an early draft for a new feature of Windows 10 RS2.</span></span> <span data-ttu-id="ccf90-105">Featurenamen, Terminologie und Funktionen sind nicht endgültig.</span><span class="sxs-lookup"><span data-stu-id="ccf90-105">Feature names, terminology, and functionality are not final.</span></span> 

## <a name="why-visual-hierarchy-is-important"></a><span data-ttu-id="ccf90-106">Warum visuelle Hierarchie wichtig ist</span><span class="sxs-lookup"><span data-stu-id="ccf90-106">Why visual hierarchy is important</span></span>

<span data-ttu-id="ccf90-107">Die Benutzer werden ständig mit Anfragen nach ihrer Aufmerksamkeit bombardiert.</span><span class="sxs-lookup"><span data-stu-id="ccf90-107">Users are constantly being bombarded with requests for their attention.</span></span> <span data-ttu-id="ccf90-108">Jedes Element auf dem Bildschirm bittet darum, betrachtet zu werden, jeder Text will gelesen werden, jeder Button angeklickt werden.</span><span class="sxs-lookup"><span data-stu-id="ccf90-108">Every element on the screen begs to be looked at, every string of text wants to be read, every button clicked.</span></span> <span data-ttu-id="ccf90-109">Da die visuelle Umgebung immer chaotischer und chaotischer wird, erfordert es mehr Mühe, die Szene zu analysieren und herauszufinden, was vor sich geht.</span><span class="sxs-lookup"><span data-stu-id="ccf90-109">As the visual environment grows more jumbled and chaotic, it takes more effort to parse the scene and figure out what's going on.</span></span>  

<span data-ttu-id="ccf90-110">Deshalb ist es so wichtig, die Elemente Ihrer Benutzeroberfläche sorgfältig auszuwählen und ein Layout zu erstellen, das eine klare visuelle Hierarchie zwischen Ihren UI-Elementen herstellt.</span><span class="sxs-lookup"><span data-stu-id="ccf90-110">That's why it's so important to carefully select the elements of your user interface, and why it's important to create a layout that establishes a clear visual hierarchy among your UI elements.</span></span> <!-- Every element is competing for the user's attention, and every time you add an element, you add a mental tax to the user. -->

<span data-ttu-id="ccf90-111">Eine klare visuelle Hierarchie sagt dem Benutzer, welche Elemente am wichtigsten sind und schafft Beziehungen zwischen den Elementen.</span><span class="sxs-lookup"><span data-stu-id="ccf90-111">A clear visual hierarchy tells users which elements are the most important and creates relationships between the elements.</span></span> <span data-ttu-id="ccf90-112">Mit einer guten visuellen Hierarchie versteht der Benutzer das Layout der Seite auf einen Blick und kann sich auf seine Aufgabe konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="ccf90-112">With a good visual hierarchy, users understand the layout of the page at a glance and can focus on the task they're trying to accomplish.</span></span> 

<p></p>


<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  <p><span data-ttu-id="ccf90-113">Wie schafft man also eine klare visuelle Hierarchie?</span><span class="sxs-lookup"><span data-stu-id="ccf90-113">So, how do you create a clear visual hierarchy?</span></span> <span data-ttu-id="ccf90-114">In früheren Versionen von Windows 10 konnten Sie Leerraum, Position und Typografie verwenden, um eine visuelle Hierarchie zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ccf90-114">With earlier versions of Windows 10, you could use white space, position, and typography to define a visual hierarchy.</span></span> </p>
  </div>
  <div class="side-by-side-content-right">
    ![Ein flaches Layout](images/content-as-objects/flat-layout.png)
    
  </div>
</div>
</div>

<span data-ttu-id="ccf90-116">Mit Windows 10 RS2 haben wir buchstäblich eine weitere Dimension hinzugefügt: die Tiefe.</span><span class="sxs-lookup"><span data-stu-id="ccf90-116">With Windows 10 RS2, we literally added another dimension: depth.</span></span> 

![Tiefe im Layout](images/content-as-objects/depth-in-layout2.png)


## <a name="use-depth-to-establish-a-hierarchy"></a><span data-ttu-id="ccf90-118">Aufbau einer Hierarchie über Tiefe</span><span class="sxs-lookup"><span data-stu-id="ccf90-118">Use depth to establish a hierarchy</span></span> 

<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
     <p><span data-ttu-id="ccf90-119">Sie können die Tiefe (z-Reihenfolge) zusammen mit Ihren anderen Designtools (Leerraum, Position, Typografie) verwenden, um eine Hierarchie aufzubauen.</span><span class="sxs-lookup"><span data-stu-id="ccf90-119">You can use depth (z-order), along with your other design tools (whitespace, position, typography) to establish a hierarchy.</span></span> <span data-ttu-id="ccf90-120">Heben Sie Ihre wichtigsten Elemente auf die vorderste Ebene; verwenden Sie die unteren Ebenen, um eine weniger kritische Benutzeroberfläche anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ccf90-120">Elevate your most important elements to the forward-most layer; use lower layers to display less critical UI.</span></span> 

    The relative importance of an element can change throughout an experience, so you can bring elements forward as they become more important and backward as they become less important. 
    </p>
  </div>
  <div class="side-by-side-content-right">
    ![Tiefe im Layout](images/content-as-objects/elements-forward-backward.png) 
    
  </div>
</div>
</div>

## <a name="how-does-it-work"></a><span data-ttu-id="ccf90-122">Wie funktioniert das?</span><span class="sxs-lookup"><span data-stu-id="ccf90-122">How does it work?</span></span>
> <span data-ttu-id="ccf90-123">TODO: Kurze Beschreibung, wie Sie die z-Reihenfolge der Elemente steuern können.</span><span class="sxs-lookup"><span data-stu-id="ccf90-123">TODO: Brief description of how you can control the z-order of elements.</span></span> <span data-ttu-id="ccf90-124">Ist die z-Reihenfolge explizit fest implementiert, oder gibt es ein semantisches Ranking-System?</span><span class="sxs-lookup"><span data-stu-id="ccf90-124">To you explicitly hard-code the z-order, or is there a semantic ranking system?</span></span> <span data-ttu-id="ccf90-125">Wie bewegen sich Objekte von einer Ebene zur anderen?</span><span class="sxs-lookup"><span data-stu-id="ccf90-125">How do items move from one layer to another?</span></span> <span data-ttu-id="ccf90-126">Was macht das System automatisch, und worüber müssen sich Designer/Entwickler Gedanken machen?</span><span class="sxs-lookup"><span data-stu-id="ccf90-126">What does the system do automatically, and what do designers/developers need to worry about?</span></span> 

## <a name="the-four-layers-of-a-typical-app-layers"></a><span data-ttu-id="ccf90-127">Die vier Ebenen einer typischen App</span><span class="sxs-lookup"><span data-stu-id="ccf90-127">The four layers of a typical app layers</span></span>

<p><span data-ttu-id="ccf90-128">Eine typische App besteht aus 4 Ebenen.</span><span class="sxs-lookup"><span data-stu-id="ccf90-128">A typical app has 4 layers.</span></span></p>
<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  **<span data-ttu-id="ccf90-129">Hinter dem Hintergrund</span><span class="sxs-lookup"><span data-stu-id="ccf90-129">Beyond background</span></span>** <br/>
<span data-ttu-id="ccf90-130">Diese Ebene liegt hinter der App.</span><span class="sxs-lookup"><span data-stu-id="ccf90-130">This layer lives behind the app.</span></span>  <span data-ttu-id="ccf90-131">Wenn Elemente auf diese Ebene verschoben werden, empfehlen wir, sie nicht interaktiv zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="ccf90-131">When elements move to this layer, we recommend making them non-interactive.</span></span> <span data-ttu-id="ccf90-132">Elemente auf dieser Ebene haben den langsamsten Parallax-Effekt und werden auf das App-Fenster beschnitten.</span><span class="sxs-lookup"><span data-stu-id="ccf90-132">Elements at this layer has the slowest parallax and are clipped to the app window.</span></span> <span data-ttu-id="ccf90-133">TODO: Ist diese Ebene skalierbar?</span><span class="sxs-lookup"><span data-stu-id="ccf90-133">TODO: Does this layer scale?</span></span> 

<p><span data-ttu-id="ccf90-134">Beispiele für Hintergrundelemente sind das Bild hinter dem Inhalt, TODO: Beispiel, TODO: Beispiel.</span><span class="sxs-lookup"><span data-stu-id="ccf90-134">Example background elements include image behind content, TODO: Example, TODO: Example.</span></span></p>
  </div>
  <div class="side-by-side-content-right">
    ![Die Hintergrundebene einer App](images/content-as-objects/elements-forward-backward.png)
    
  </div>
</div>
</div>

<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  **<span data-ttu-id="ccf90-136">Passive Ebene</span><span class="sxs-lookup"><span data-stu-id="ccf90-136">Passive layer</span></span>** <br/>
<span data-ttu-id="ccf90-137">Dies ist die Basisebene der App, in der sich standardmäßig die UI-Elemente befinden.</span><span class="sxs-lookup"><span data-stu-id="ccf90-137">This is the base layer of the app, where UI elements live by default.</span></span>  <span data-ttu-id="ccf90-138">Elemente bewegen sich auf dieser Ebene in Echtzeit (keine Parallax-Effekt). Sie werden auf das App-Fenster beschnitten und auf 100 % skaliert.</span><span class="sxs-lookup"><span data-stu-id="ccf90-138">Elements move in real-time on this layer (no parallax), are clipped to the app window, and are rendered at 100% scale.</span></span> 

<p><span data-ttu-id="ccf90-139">Beispielelemente: Der App-Hintergrund, der Text, das sekundäre UI, wie z. B. das App-Navigations-UI.</span><span class="sxs-lookup"><span data-stu-id="ccf90-139">Example elements: The app background, text, secondary UI, such as app navigation UI.</span></span></p>
  </div>
  <div class="side-by-side-content-right">
    ![Die passive Ebene einer App](images/content-as-objects/elements-forward-backward.png)
    
  </div>
</div>
</div>

<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  **<span data-ttu-id="ccf90-141">Handlungsaufforderungen</span><span class="sxs-lookup"><span data-stu-id="ccf90-141">Calls to action</span></span>** <br/>
<span data-ttu-id="ccf90-142">Diese Ebene ist für interaktive Elemente bestimmt, die Sie über Elemente auf der passiven Ebene priorisieren.</span><span class="sxs-lookup"><span data-stu-id="ccf90-142">This layer is for interactive items that you prioritize above passive layer elements.</span></span> <span data-ttu-id="ccf90-143">Elemente auf dieser Ebene haben einen mittleren Parallax-Effekt und werden auf das App-Fenster beschnitten.</span><span class="sxs-lookup"><span data-stu-id="ccf90-143">Elements on this layer have medium parallax and are clipped to the app window.</span></span> <span data-ttu-id="ccf90-144">TODO: Skalieren Elemente auf dieser Ebene oder haben sie einen Schlagschatten?</span><span class="sxs-lookup"><span data-stu-id="ccf90-144">TODO: Do elements at this layer scale or have a drop shadow?</span></span>

<p><span data-ttu-id="ccf90-145">Beispielelemente: Listen, Raster, primäre Befehle (TODO: z.B.....).</span><span class="sxs-lookup"><span data-stu-id="ccf90-145">Example elements: lists, grids, primary commands (TODO: Such as...).</span></span></p> 
  </div>
  <div class="side-by-side-content-right">
    ![Die Call-to-Action-Schicht einer App](images/content-as-objects/elements-forward-backward.png)
    
  </div>
</div>
</div>

<p></p>
<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  **<span data-ttu-id="ccf90-147">Hero-Ebene</span><span class="sxs-lookup"><span data-stu-id="ccf90-147">Hero layer</span></span>** <br/>
<span data-ttu-id="ccf90-148">Diese Ebene ist für das Element mit der höchsten Priorität auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="ccf90-148">This layer is for the highest priority element on the screen at the time.</span></span>  <span data-ttu-id="ccf90-149">Elemente auf dieser Ebene können die Grenzen des App-Fensters sprengen, sie können skalieren, und sie erhalten automatisch einen Schlagschatten.</span><span class="sxs-lookup"><span data-stu-id="ccf90-149">Elements on this layer can break the bounds of the app window, they can scale, and they automatically get a drop shadow.</span></span>

<p><span data-ttu-id="ccf90-150">Beispielelemente: fotografische Elemente, das aktuell ausgewählte Element.</span><span class="sxs-lookup"><span data-stu-id="ccf90-150">Example elements: photographic elements, the currently selected item.</span></span></p>  
  </div>
  <div class="side-by-side-content-right">
    ![Die Hero-Ebene einer App](images/content-as-objects/elements-forward-backward.png)
    
  </div>
</div>
</div>



<!--
Depth is meaningful; it establishes visual and interactive hierarchy for users to efficiently complete tasks. Depth orients users in our system. 
-->

## <a name="example-tbd"></a><span data-ttu-id="ccf90-152">Beispiel: TBD</span><span class="sxs-lookup"><span data-stu-id="ccf90-152">Example: TBD</span></span>
> <span data-ttu-id="ccf90-153">TODO: Zeigen, wie man ein gemeinsames UI-Muster für die Verwendung der z-Reihenfolge anpasst.</span><span class="sxs-lookup"><span data-stu-id="ccf90-153">TODO: Show how to adapt a common UI pattern to use z-ordering.</span></span> <span data-ttu-id="ccf90-154">Wir sollten Illustrationen und Code zeigen.</span><span class="sxs-lookup"><span data-stu-id="ccf90-154">We should show illustrations and code.</span></span> 

## <a name="download-the-code-samples"></a><span data-ttu-id="ccf90-155">Codebeispiele herunterladen</span><span class="sxs-lookup"><span data-stu-id="ccf90-155">Download the code samples</span></span>
><span data-ttu-id="ccf90-156">TODO: Link zu Beispielen, die diese Funktion demonstrieren.</span><span class="sxs-lookup"><span data-stu-id="ccf90-156">TODO: Link to samples that demonstrate this feature.</span></span> 


## <a name="related-articles"></a><span data-ttu-id="ccf90-157">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="ccf90-157">Related articles</span></span>
* [<span data-ttu-id="ccf90-158">Inhaltsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="ccf90-158">Content basics</span></span>](../basics/content-basics.md)
