---
author: mijacobs
Description: "Gut gestaltete Bewegungen machen Apps lebhaft und lassen sie realistisch und perfekt erscheinen. Helfen Sie Benutzern dabei, Kontextänderungen zu verstehen, und verbinden Sie Interaktionen mit visuellen Übergängen."
title: Bewegung und Animation in UWP-Apps
ms.assetid: 21AA1335-765E-433A-85D8-560B340AE966
label: Motion
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: jeffarn
doc-status: Published
ms.openlocfilehash: d24edf5eaacb65ca28f2f2727f441cb833141dcf
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="motion-for-uwp-apps"></a><span data-ttu-id="5f1e8-105">Bewegung für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="5f1e8-105">Motion for UWP apps</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="5f1e8-106">Gut gestaltete Bewegungen machen Apps lebhaft und lassen sie realistisch und perfekt erscheinen.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-106">Purposeful, well-designed motion brings your app to life and makes the experience feel crafted and polished.</span></span> <span data-ttu-id="5f1e8-107">Bewegung hilft Benutzern dabei, Kontextänderungen zu verstehen, und sie zeigt Benutzern auch an, wo diese sich in der App befinden.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-107">Motion helps your users understand context changes and where they are within your app’s navigation hierarchy.</span></span> <span data-ttu-id="5f1e8-108">Interaktionen werden mit visuellen Übergängen verbunden.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-108">It ties experiences together with visual transitions.</span></span> <span data-ttu-id="5f1e8-109">Bewegung fügt der Oberfläche Geschwindigkeit und Mehrdimensionalität hinzu.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-109">Motion adds a sense of pacing and dimensionality to the experience.</span></span>

## <a name="benefits-of-motion"></a><span data-ttu-id="5f1e8-110">Vorteile von Bewegung</span><span class="sxs-lookup"><span data-stu-id="5f1e8-110">Benefits of motion</span></span>

<span data-ttu-id="5f1e8-111">Bewegung bedeutet mehr, als nur Dinge beweglich zu machen.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-111">Motion is more than making things move.</span></span> <span data-ttu-id="5f1e8-112">Bewegung ist ein Tool zum Erstellen eines physischen Ökosystems, das Benutzer mithilfe verschiedener Eingabetypen wie Maus, Tastatur, Toucheingabe und Stift aktiv bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-112">Motion is a tool for creating a physical ecosystem for the user to live inside and manipulate through a variety of input types, like mouse, keyboard, touch, and pen.</span></span> <span data-ttu-id="5f1e8-113">Die Qualität der Erfahrung hängt davon ab, wie gut die App auf den Benutzer reagiert und welche Art von Persönlichkeit die Benutzeroberfläche vermittelt.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-113">The quality of the experience depends on how well the app responds to the user, and what kind of personality the UI communicates.</span></span>

<span data-ttu-id="5f1e8-114">Stellen Sie sicher, dass die Bewegung einem Zweck in Ihrer App dient.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-114">Make sure motion serves a purpose in your app.</span></span> <span data-ttu-id="5f1e8-115">Die besten UWP-Apps (Universelle Windows-Plattform) verwenden Bewegung, um die Benutzeroberfläche zum Leben zu erwecken.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-115">The best Universal Windows Platform (UWP) apps use motion to bring the UI to life.</span></span> <span data-ttu-id="5f1e8-116">Bewegung sollte:</span><span class="sxs-lookup"><span data-stu-id="5f1e8-116">Motion should:</span></span>

- <span data-ttu-id="5f1e8-117">Feedback basierend auf dem Verhalten des Benutzers geben.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-117">Give feedback based on the user's behavior.</span></span>
- <span data-ttu-id="5f1e8-118">Dem Benutzer beibringen, wie er mit der Benutzeroberfläche interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-118">Teach the user how to interact with the UI.</span></span>
- <span data-ttu-id="5f1e8-119">Angeben, wie zu vorherigen oder folgenden Ansichten navigiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-119">Indicate how to navigate to previous or succeeding views.</span></span>

<span data-ttu-id="5f1e8-120">Wenn ein Benutzer mehr Zeit in Ihrer App verbringt oder Aufgaben in Ihrer App komplexer werden, wird qualitativ hochwertige Bewegung immer wichtiger: Mit Bewegung kann die Art und Weise verändert werden, wie der Benutzer die kognitive Belastung und die Benutzerfreundlichkeit Ihrer App wahrnimmt.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-120">As a user spends more time inside your app, or as tasks in your app become more sophisticated, high-quality motion becomes increasingly important: it can be used to change how the user perceives their cognitive load and your app's ease of use.</span></span> <span data-ttu-id="5f1e8-121">Bewegung bringt viele weitere direkte Vorteile mit sich:</span><span class="sxs-lookup"><span data-stu-id="5f1e8-121">Motion has many other direct benefits:</span></span>

- **<span data-ttu-id="5f1e8-122">Bewegung unterstützt die Interaktion und trägt dazu bei, dass sich Benutzer zurechtfinden.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-122">Motion supports interaction and wayfinding.</span></span>**

    <span data-ttu-id="5f1e8-123">Bewegung ist direktional: Sie bewegt sich vor und zurück, in den Inhalt hinein und aus ihm hinaus und hinterlässt gleichzeitig mentale „Brotkrümel“-Hinweise, wie der Benutzer zur aktuellen Ansicht gelangt ist.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-123">Motion is directional: it moves forward and backward, in and out of content, leaving mental "breadcrumb" clues as to how the user arrived at the present view.</span></span> <span data-ttu-id="5f1e8-124">Übergänge können Benutzern beim Erlernen der Bedienung neuer Apps helfen, indem Analogien mit Aufgaben hergestellt werden, mit denen der Benutzer bereits vertraut ist.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-124">Transitions can help users learn how to operate new applications by drawing analogies to tasks that the user is already familiar with.</span></span>

- **<span data-ttu-id="5f1e8-125">Bewegung kann den Eindruck verbesserter Leistung vermitteln.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-125">Motion can give the impression of enhanced performance.</span></span>**

    <span data-ttu-id="5f1e8-126">Wenn die Netzwerkgeschwindigkeit langsamer wird oder das System nicht reagiert, können Animationen dem Benutzer die Wartezeit kürzer erscheinen lassen.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-126">When network speeds lag or the system pauses to work, animations can make the user's wait feel shorter.</span></span> <span data-ttu-id="5f1e8-127">Durch Animationen kann dem Benutzer mitgeteilt werden, dass die App noch mit der Verarbeitung beschäftigt und nicht eingefroren ist, und es können passiv neue Informationen angezeigt werden, die den Benutzer möglicherweise interessieren.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-127">Animations can be used to let the user know that the app is processing, not frozen, and it can passively surface new information that the user may be interested in.</span></span>

- **<span data-ttu-id="5f1e8-128">Bewegung schafft Persönlichkeit.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-128">Motion adds personality.</span></span>**

    <span data-ttu-id="5f1e8-129">Bewegung ist häufig der allgemeine Thread, der die Persönlichkeit der Apps abbildet, wenn Benutzer durch eine Oberfläche navigieren.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-129">Motion is often the common thread that communicates your apps personality as a user moves through an experience.</span></span>

- **<span data-ttu-id="5f1e8-130">Bewegung schafft Eleganz.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-130">Motion adds elegance.</span></span>**

    <span data-ttu-id="5f1e8-131">Durch fließende, reaktionsfähige Bewegungen wirken Benutzeroberflächen natürlich, und sie sorgen dafür, dass emotionale Verbindungen mit der Oberfläche entstehen.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-131">Fluid, responsive, motion makes experiences feel natural, creating emotional connections to the experience.</span></span>

## <a name="examples-of-motion"></a><span data-ttu-id="5f1e8-132">Beispiele für Bewegung</span><span class="sxs-lookup"><span data-stu-id="5f1e8-132">Examples of motion</span></span>

<span data-ttu-id="5f1e8-133">Im Folgenden finden Sie einige Beispiele für Bewegung in einer App.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-133">Here are some examples of motion in an app.</span></span>

<span data-ttu-id="5f1e8-134">Hier verwendet eine App eine verbundene Animation, um ein Elementbild zu animieren, wenn es als Teil der Überschrift der nächsten Seite weiterbesteht.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-134">Here, an app uses a connected animation to animate an item image as it “continues” to become part of the header of the next page.</span></span> <span data-ttu-id="5f1e8-135">Dieser Effekt trägt dazu bei, Benutzerkontext beim Übergang beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-135">The effect helps maintain user context across the transition.</span></span>

![Verbundene Animation](images/connected-animations/example.gif)

<span data-ttu-id="5f1e8-137">Hier werden bei einem Bildlauf oder Schwenken der UI verschiedene Objekte mithilfe eines Parallax-Effekts unterschiedlich schnell verschoben. Dadurch entsteht ein Gefühl von Tiefe, Perspektive und Bewegung.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-137">Here, a visual parallax effect moves different objects at different rates when the UI scrolls or pans to create a feeling of depth, perspective, and movement.</span></span>

![Beispiel für Parallax mit einer Liste und einem Hintergrundbild](images/_Parallax_v2.gif)


## <a name="types-of-motion"></a><span data-ttu-id="5f1e8-139">Arten von Bewegung</span><span class="sxs-lookup"><span data-stu-id="5f1e8-139">Types of motion</span></span>

<table>
    <tr>
        <th align="left"><span data-ttu-id="5f1e8-140">Bewegungsart</span><span class="sxs-lookup"><span data-stu-id="5f1e8-140">Motion type</span></span></th>
        <th align="left"><span data-ttu-id="5f1e8-141">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f1e8-141">Description</span></span></th>
    </tr>
    <tr>
        <td>[<span data-ttu-id="5f1e8-142">Hinzufügen und Löschen</span><span class="sxs-lookup"><span data-stu-id="5f1e8-142">Add and delete</span></span>](motion-list.md)
        </td>
        <td><span data-ttu-id="5f1e8-143">Mit Listenanimationen können Sie einzelne oder mehrere Elemente in einer Sammlung wie z. B. einem Fotoalbum oder einer Liste mit Suchergebnissen einfügen oder entfernen.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-143">List animations let you insert or remove single or multiple items from a collection, such as a photo album or a list of search results.</span></span>
        </td>
    </tr>
    <tr>
        <td>[<span data-ttu-id="5f1e8-144">Verbundene Animation</span><span class="sxs-lookup"><span data-stu-id="5f1e8-144">Connected animation</span></span>](connected-animation.md)
        </td>
        <td><span data-ttu-id="5f1e8-145">Mit verbundenen Animationen können Sie eine dynamische und ansprechende Navigationsfunktionalität erstellen, indem Sie den Übergang eines Elements zwischen zwei verschiedenen Ansichten animieren.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-145">Connected animations let you create a dynamic and compelling navigation experience by animating the transition of an element between two different views.</span></span> <span data-ttu-id="5f1e8-146">So können Benutzer den Kontext beibehalten, und es entsteht Kontinuität zwischen den Ansichten.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-146">This helps the user maintain their context and provides continuity between the views.</span></span> <span data-ttu-id="5f1e8-147">In einer verbundenen Animation scheint ein Element zwischen zwei Ansichten weiterzubestehen, während sich der UI-Inhalt ändert. Dabei fliegt das Element von seinem Standort in der Quellansicht über den Bildschirm zu seinem Ziel in der neuen Ansicht herüber.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-147">In a connected animation, an element appears to “continue” between two views during a change in UI content, flying across the screen from its location in the source view to its destination in the new view.</span></span> <span data-ttu-id="5f1e8-148">Dadurch wird der gemeinsame Inhalt zwischen den beiden Ansichten unterstrichen, und es entsteht ein schöner, dynamischer Effekt als Teil eines Übergangs.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-148">This emphasizes the common content in between the views and creates a beautiful and dynamic effect as part of a transition.</span></span> 
        </td>
    </tr>
    <tr>
        <td>[<span data-ttu-id="5f1e8-149">Inhaltsübergang</span><span class="sxs-lookup"><span data-stu-id="5f1e8-149">Content transition</span></span>](content-transition-animations.md)
        </td>
        <td><span data-ttu-id="5f1e8-150">Mithilfe von Inhaltsübergangsanimationen können Sie den Inhalt eines Bildschirmbereichs ändern und gleichzeitig den Container oder Hintergrund unverändert lassen.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-150">Content transition animations let you change the content of an area of the screen while keeping the container or background constant.</span></span> <span data-ttu-id="5f1e8-151">Neuer Inhalt wird eingeblendet.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-151">New content fades in.</span></span> <span data-ttu-id="5f1e8-152">Muss vorhandener Inhalt ersetzt werden, wird dieser Inhalt ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-152">If there is existing content to be replaced, that content fades out.</span></span>
        </td>
    </tr>
    <tr>
        <td>[<span data-ttu-id="5f1e8-153">Drill</span><span class="sxs-lookup"><span data-stu-id="5f1e8-153">Drill</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.drillinthemeanimation)
        </td>
        <td><span data-ttu-id="5f1e8-154">Verwenden Sie eine Drill-in-Animation, wenn ein Benutzer in einer logischen Hierarchie in Vorwärtsrichtung navigiert, beispielsweise von einer Masterliste zu einer Detailseite.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-154">Use a drill-in animation when a user navigates forward in a logical hierarchy, like from a master list to a detail page.</span></span> <span data-ttu-id="5f1e8-155">Verwenden Sie eine Drill-out-Animation, wenn ein Benutzer in einer logischen Hierarchie in Rückwärtsrichtung navigiert, wie von einer Detailseite zu einer Masterseite.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-155">Use a drill-out animation when a user navigates backward in a logical hierarchy, like from a detail page to a master page.</span></span>
        </td>
    </tr>
    <tr>
        <td>[<span data-ttu-id="5f1e8-156">Ein- und Ausblenden</span><span class="sxs-lookup"><span data-stu-id="5f1e8-156">Fade</span></span>](motion-fade.md)
        </td>
        <td><span data-ttu-id="5f1e8-157">Verwenden Sie Ein- und Ausblendungsanimationen, um Elemente anzuzeigen oder nicht anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-157">Use fade animations to bring items into a view or to take items out of a view.</span></span> <span data-ttu-id="5f1e8-158">Die beiden üblichen Animationen dieser Art sind das Einblenden und das Ausblenden.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-158">The two common fade animations are fade-in and fade-out.</span></span>
        </td>
    </tr>
        <tr>
        <td>[<span data-ttu-id="5f1e8-159">Parallax</span><span class="sxs-lookup"><span data-stu-id="5f1e8-159">Parallax</span></span>](parallax.md)
        </td>
        <td><span data-ttu-id="5f1e8-160">Ein visueller Parallax-Effekt hilft dabei, ein Gefühl von Tiefe, Perspektive und Bewegung zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-160">A visual parallax effect helps create a feeling of depth, perspective, and movement.</span></span> <span data-ttu-id="5f1e8-161">Dieser Effekt wird erzielt, indem bei einem Bildlauf oder Schwenken der UI verschiedene Objekte unterschiedlich schnell verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-161">It achieves this effect by moving different objects at different rates when the UI scrolls or pans.</span></span>
        </td>
    </tr> 
    <tr>
        <td>[<span data-ttu-id="5f1e8-162">Feedback durch Drücken</span><span class="sxs-lookup"><span data-stu-id="5f1e8-162">Press feedback</span></span>](motion-pointer.md)
        </td>
        <td><span data-ttu-id="5f1e8-163">Zeigerdruckanimationen stellen visuelles Feedback für Benutzer bereit, wenn diese auf ein Element tippen.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-163">Pointer press animations provide users with visual feedback when the user taps on an item.</span></span> <span data-ttu-id="5f1e8-164">Bei der Animation für „Zeiger nach unten“ wird das gedrückte Element leicht verkleinert und geneigt. Sie wird wiedergegeben, wenn erstmalig auf ein Element getippt wird.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-164">The pointer down animation slightly shrinks and tilts the pressed item, and plays when an item is first tapped.</span></span> <span data-ttu-id="5f1e8-165">Die Animation für „Zeiger nach oben“, mit der der ursprüngliche Zustand des Elements wiederhergestellt wird, wird beim Loslassen des Zeigers wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="5f1e8-165">The pointer up animation, which restores the item to its original position, is played when the user releases the pointer.</span></span>
        </td>
    </tr>
</table>