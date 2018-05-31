---
description: Lernen Sie das Fluent Design und dessen Integration in Ihre Apps kennen.
title: Fluent Design System für UWP-Apps
author: mijacobs
keywords: Layout von UWP-Apps, universelle Windows-Plattform, App-Design, Schnittstelle, fluent design system
ms.author: mijacobs
ms.date: 3/7/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: high
ms.openlocfilehash: 5b57dc2ddae4c6e260df663097db5649866b96aa
ms.sourcegitcommit: ef5a1e1807313a2caa9c9b35ea20b129ff7155d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
ms.locfileid: "1638788"
---
# <a name="the-fluent-design-system-for-uwp-apps"></a><span data-ttu-id="57f67-104">Das Fluent Design System für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="57f67-104">The Fluent Design System for UWP apps</span></span>

## <a name="introduction"></a><span data-ttu-id="57f67-105">Einführung</span><span class="sxs-lookup"><span data-stu-id="57f67-105">Introduction</span></span>

<img src="images/fluentdesign-app-header.jpg" alt=" " />

<span data-ttu-id="57f67-106">Die Benutzeroberfläche entwickelt sich weiter.</span><span class="sxs-lookup"><span data-stu-id="57f67-106">The user interface is evolving.</span></span> <span data-ttu-id="57f67-107">Sie wird erweitert, um neue Dimensionen und Schnittstellen (2D, 3D, Tastatur, Maus, Blick, Stift, Touch etc.) abzudecken.</span><span class="sxs-lookup"><span data-stu-id="57f67-107">It's expanding to include new dimensions and interfaces, from 2D to 3D and beyond, from keyboard and mouse to gaze, pen, and touch.</span></span>  

<span data-ttu-id="57f67-108">Das Fluent Design System stellt eine Reihe von innovativen UWP-Funktionen in Kombination mit bewährten Verfahrensweisen für die Erstellung von Apps dar, die auf allen Arten von Windows-basierten Geräten hervorragend funktionieren.</span><span class="sxs-lookup"><span data-stu-id="57f67-108">The Fluent Design System is a set of innovative UWP features combined with best practices for creating apps that perform beautifully on all types of Windows-powered devices.</span></span>

<span data-ttu-id="57f67-109">Das Fluent Design System ist unser System zur Erstellung adaptiver, empathischer und schöner Benutzeroberflächen.</span><span class="sxs-lookup"><span data-stu-id="57f67-109">It's our system for creating adaptive, empathetic, and beautiful user interfaces.</span></span> 

**<span data-ttu-id="57f67-110">Adaptiv: Fluent-Erlebnisse fühlen sich auf jedem Gerät natürlich an.</span><span class="sxs-lookup"><span data-stu-id="57f67-110">Adaptive: Fluent experiences feel natural on each device</span></span>**

<span data-ttu-id="57f67-111">Fluent-Erlebnisse passen sich an die Umgebung an.</span><span class="sxs-lookup"><span data-stu-id="57f67-111">Fluent experiences adapt to the environment.</span></span> <span data-ttu-id="57f67-112">Ein Fluent-Erlebnis fühlt sich auf einem Tablet, einem Desktop-PC und einer Xbox gut an. Es funktioniert sogar mit einem Mixed Reality-Headset hervorragend.</span><span class="sxs-lookup"><span data-stu-id="57f67-112">A Fluent experience feels comfortable on a tablet, a desktop PC, and an Xbox&mdash;it even works great on a Mixed Reality headset.</span></span> <span data-ttu-id="57f67-113">Und wenn Sie mehr Hardware hinzufügen, wie z. B. einen zusätzlichen Monitor für Ihren PC, nutzt ein Fluent-Erlebnis diese Vorteile.</span><span class="sxs-lookup"><span data-stu-id="57f67-113">And when you add more hardware, like an additional monitor for your PC, a Fluent experience takes advantage of it.</span></span> 

**<span data-ttu-id="57f67-114">Empathisch: Fluent-Erlebnisse sind intuitiv und kraftvoll.</span><span class="sxs-lookup"><span data-stu-id="57f67-114">Empathetic: Fluent experiences are intuitive and powerful</span></span>**

<span data-ttu-id="57f67-115">Fluent-Erlebnisse passen sich dem Verhalten und der Absicht an – sie verstehen und antizipieren, was nötig ist.</span><span class="sxs-lookup"><span data-stu-id="57f67-115">Fluent experiences adjust to behavior and intent&mdash;they understand and anticipate what’s needed.</span></span> <span data-ttu-id="57f67-116">Sie vereinen Menschen und Ideen, egal ob sie sich auf gegenüberliegenden Seiten der Welt befinden oder direkt nebeneinander stehen.</span><span class="sxs-lookup"><span data-stu-id="57f67-116">They unite people and ideas, whether they’re on opposite sides of the globe or standing right next to each other.</span></span> 

<span data-ttu-id="57f67-117">Empathie bedeutet, das Richtige zur richtigen Zeit zu tun.</span><span class="sxs-lookup"><span data-stu-id="57f67-117">Demonstrating empathy is about doing the right thing at the right time.</span></span> 

<span data-ttu-id="57f67-118">Fluent-Erlebnisse verwenden Steuerelement und Muster konsequent, sodass sie sich so verhalten, wie es der Benutzer erwartet hat.</span><span class="sxs-lookup"><span data-stu-id="57f67-118">Fluent experiences use controls and patterns consistently, so they behave in ways the user has learned to expect.</span></span> <span data-ttu-id="57f67-119">Fluent-Erlebnisse sind für Menschen mit einem breiten Spektrum an körperlichen Fähigkeiten zugänglich und umfassen Globalisierungsfunktionen für Menschen auf der ganzen Welt.</span><span class="sxs-lookup"><span data-stu-id="57f67-119">Fluent experiences are accessible to people with a wide range of physical abilities, and incorporate globalization features so people around the world can use them.</span></span> 

**<span data-ttu-id="57f67-120">Wunderschön: Fluent-Erlebnisse sind einnehmend und immersiv.</span><span class="sxs-lookup"><span data-stu-id="57f67-120">Beautiful: Fluent experiences are engaging and immersive</span></span>** 

<span data-ttu-id="57f67-121">Durch das Einbeziehen von Elementen der physischen Welt erschließt sich ein Fluent-Erlebniss etwas Grundsätzliches.</span><span class="sxs-lookup"><span data-stu-id="57f67-121">By incorporating elements of the physical world, a Fluent experience taps into something fundamental.</span></span> <span data-ttu-id="57f67-122">Es nutzt Licht, Schatten, Bewegung, Tiefe und Textur, um Informationen intuitiv und instinktiv zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="57f67-122">It uses light, shadow, motion, depth, and texture to organize information in a way that feels intuitive and instinctual.</span></span> 

<span data-ttu-id="57f67-123">Beim Fluent Design geht es nicht um auffällige Effekte.</span><span class="sxs-lookup"><span data-stu-id="57f67-123">Fluent Design isn't about flashy effects.</span></span> <span data-ttu-id="57f67-124">Es beinhaltet physikalische Effekte, die das Benutzererlebnis wirklich verbessern. Es emuliert Erlebnisse, die unser Gehirn effizient verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="57f67-124">It incorporates physical effects that truly enhance the user experience, because they emulate experiences that our brains are programmed to process efficiently.</span></span> 

## <a name="applying-fluent-design-to-your-app"></a><span data-ttu-id="57f67-125">Umsetzung des Fluent Designs für Ihre App</span><span class="sxs-lookup"><span data-stu-id="57f67-125">Applying Fluent Design to your app</span></span>

<span data-ttu-id="57f67-126">Fluent Design-Features sind in UWP integriert.</span><span class="sxs-lookup"><span data-stu-id="57f67-126">Fluent Design features are built into UWP.</span></span> <span data-ttu-id="57f67-127">Einige dieser Funktionen – wie effektive Pixel und das universelle Eingabesystem – arbeiten automatisch.</span><span class="sxs-lookup"><span data-stu-id="57f67-127">Some of these features&mdash;such as effective pixels and the universal input system&mdash;are automatic.</span></span> <span data-ttu-id="57f67-128">Sie müssen keinen zusätzlichen Code schreiben, um sie zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="57f67-128">You don't have to write any extra code to take advantage of them.</span></span> <span data-ttu-id="57f67-129">Andere Funktionen, wie z. B. Acryl, sind optional. Sie nehmen sie in Ihre Anwendung auf, indem Sie Code schreiben.</span><span class="sxs-lookup"><span data-stu-id="57f67-129">Other features, like acrylic, are optional; you add them to your app by writing code to include them.</span></span> 

> <span data-ttu-id="57f67-130">Um mehr über die grundlegenden Funktionen zu erfahren, die automatisch in jeder UWP-Applikation enthalten sind, lesen Sie bitte den Artikel [Einführung in UWP-Apps](../basics/design-and-ui-intro.md).</span><span class="sxs-lookup"><span data-stu-id="57f67-130">To learn more about the basic features that are automatically included in every UWP app, see the [Intro to UWP app design article](../basics/design-and-ui-intro.md).</span></span> <span data-ttu-id="57f67-131">Wenn Sie völlig neu in der UWP-Entwicklung sind, sollten Sie sich zuerst unsere Seite [Erste Schritte mit UWP](https://developer.microsoft.com/windows/apps/getstarted) ansehen.</span><span class="sxs-lookup"><span data-stu-id="57f67-131">If you're completely new to UWP development, you might want to check out our [Get started with UWP page](https://developer.microsoft.com/windows/apps/getstarted) first.</span></span> 

<span data-ttu-id="57f67-132">Um mehr über die neuen Funktionen zu erfahren, mit denen Sie Fluent Design in Ihre App integrieren können, lesen Sie weiter.</span><span class="sxs-lookup"><span data-stu-id="57f67-132">To learn more about the new features that help you incorporate Fluent Design into your app, keep reading.</span></span>

## <a name="find-a-natural-fit"></a><span data-ttu-id="57f67-133">Eine natürliche Form finden</span><span class="sxs-lookup"><span data-stu-id="57f67-133">Find a natural fit</span></span>

<span data-ttu-id="57f67-134">Wie gestaltet man eine App auf einer Vielzahl von Geräten natürlich?</span><span class="sxs-lookup"><span data-stu-id="57f67-134">How do you make an app feel natural on a variety of devices?</span></span> <span data-ttu-id="57f67-135">Indem sie sich so anfühlt, als wäre sie für jedes einzelne Gerät entwickelt worden.</span><span class="sxs-lookup"><span data-stu-id="57f67-135">By making it feel as though it were designed with each specific device in mind.</span></span> <span data-ttu-id="57f67-136">Ein UI-Layout, das sich an verschiedene Bildschirmgrößen anpasst (ohne vergeudeten Platz oder Überladung) schafft ein natürliches Erlebnis – als ob es für dieses Gerät entwickelt wurde.</span><span class="sxs-lookup"><span data-stu-id="57f67-136">A UI layout that adapts to different screen sizes&mdash;so there's no wasted space (but no crowding either)&mdash;makes an experience feel natural, as though it were designed for that device.</span></span> 

*  **<span data-ttu-id="57f67-137">Design der richtigen Breakpoints</span><span class="sxs-lookup"><span data-stu-id="57f67-137">Design for the right breakpoints</span></span>**

    <span data-ttu-id="57f67-138">Anstatt das Design für jede einzelne Bildschirmgröße anzupassen, kann die Konzentration auf einige wenige aber wichtige Größen („Breakpoints”) Ihre Designs und Ihren Code stark vereinfachen und Ihre App gleichzeitig auf kleinen und großen Bildschirmen großartig darstellen.</span><span class="sxs-lookup"><span data-stu-id="57f67-138">Instead of designing for every individual screen size, focusing on a few key widths (also called "breakpoints") can greatly simplify your designs and code while still making your app look great on small to large screens.</span></span>

    [<span data-ttu-id="57f67-139">Mehr über Bildschirmgrößen und Breakpoints</span><span class="sxs-lookup"><span data-stu-id="57f67-139">Learn about screen sizes and breakpoints</span></span>](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design)

*  **<span data-ttu-id="57f67-140">Erstellen eines dynamischen Layouts</span><span class="sxs-lookup"><span data-stu-id="57f67-140">Create a responsive layout</span></span>**

    <span data-ttu-id="57f67-141">Damit sich eine App natürlich anfühlt, muss sie den verfügbaren Anzeigeraum füllen, ohne überfüllt zu wirken.</span><span class="sxs-lookup"><span data-stu-id="57f67-141">For an app to feel natural, it needs to fill the available display space without seeming too crowded.</span></span> <span data-ttu-id="57f67-142">UWP stellt Panels bereit, die Inhalte in Rastern, Stapeln und Flüssen (Grid, Stack, Flow) anordnen und ineinander verschachteln können.</span><span class="sxs-lookup"><span data-stu-id="57f67-142">UWP provides panels that arrange content in grids, stacks, and flows, and you can nest them inside each other.</span></span>

    [<span data-ttu-id="57f67-143">Mehr über die UWP-Layout-Panels</span><span class="sxs-lookup"><span data-stu-id="57f67-143">Learn about UWP's layout panels</span></span>](/windows/uwp/design/layout/layout-panels)

* **<span data-ttu-id="57f67-144">Design für ein Gerätespektrum</span><span class="sxs-lookup"><span data-stu-id="57f67-144">Design for a spectrum of devices</span></span>**

    <span data-ttu-id="57f67-145">UWP-Apps können auf einer Vielzahl von Windows-basierten Geräten ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="57f67-145">UWP apps can run on a wide variety of Windows-powered devices.</span></span> <span data-ttu-id="57f67-146">Es ist hilfreich zu wissen, welche Geräte verfügbar sind, wofür sie gemacht sind und wie Benutzer mit ihnen interagieren.</span><span class="sxs-lookup"><span data-stu-id="57f67-146">It's helpful to understand which devices are available, what they're made for, and how users interact with them.</span></span>

    [<span data-ttu-id="57f67-147">Mehr über UWP-Geräte</span><span class="sxs-lookup"><span data-stu-id="57f67-147">Learn about UWP devices</span></span>](/windows/uwp/design/devices/)

* **<span data-ttu-id="57f67-148">Optimierung für die passende Eingabe</span><span class="sxs-lookup"><span data-stu-id="57f67-148">Optimize for the right input</span></span>**

    <span data-ttu-id="57f67-149">UWP-Apps unterstützen automatisch gängige Maus-, Tastatur-, Stift- und Touch-Interaktionen. Sie müssen sich nicht extra darum kümmern.</span><span class="sxs-lookup"><span data-stu-id="57f67-149">UWP apps automatically support common mouse, keyboard, pen, and touch interactions&mdash;there's nothing extra you have to do.</span></span> <span data-ttu-id="57f67-150">Aber Sie können Ihre Apps um einer optimierte Unterstützung für bestimmte Eingabemöglichkeiten (z. B. Stift und Surface Dial) erweitern.</span><span class="sxs-lookup"><span data-stu-id="57f67-150">But you can enhance your app with optimized support for specific inputs, like pen and the Surface Dial.</span></span>

    [<span data-ttu-id="57f67-151">Mehr über Eingaben und Interaktionen</span><span class="sxs-lookup"><span data-stu-id="57f67-151">Learn about inputs and interactions</span></span>](/windows/uwp/design/input/input-primer)


## <a name="make-it-intuitive-and-powerful"></a><span data-ttu-id="57f67-152">Intuitiv und leistungsstark</span><span class="sxs-lookup"><span data-stu-id="57f67-152">Make it intuitive and powerful</span></span>

<span data-ttu-id="57f67-153">Ein Erlebnis fühlt sich intuitiv an, wenn es sich so verhält, wie der Benutzer es erwartet.</span><span class="sxs-lookup"><span data-stu-id="57f67-153">An experience feels intuitive when it behaves that way the user expects it to.</span></span> <span data-ttu-id="57f67-154">Durch die Verwendung etablierter Steuerelemente und Muster und die Nutzung der Plattformunterstützung für die Zugänglichkeit und Globalisierung schaffen Sie eine reibungsloses Erlebnis, mit dem die Benutzer produktiver sind.</span><span class="sxs-lookup"><span data-stu-id="57f67-154">By using established controls and patterns and taking advantage of platform support for accessibility and globalization, you create an effortless experience that helps users be more productive.</span></span> 

* **<span data-ttu-id="57f67-155">Das passende Steuerelement für eine Aufgabe</span><span class="sxs-lookup"><span data-stu-id="57f67-155">Use the right control for the job</span></span>**

    <span data-ttu-id="57f67-156">Steuerelemente sind die Bausteine der Benutzeroberfläche. Mit dem richtigen Steuerelement können Sie eine Benutzeroberfläche erstellen, die sich so verhält, wie es die Benutzer erwarten.</span><span class="sxs-lookup"><span data-stu-id="57f67-156">Controls are the building blocks of the user interface; using the right control helps you create a user interface that behaves the way users expect it to.</span></span>  <span data-ttu-id="57f67-157">UWP bietet mehr als 45 Steuerelemente – von einfachen Schaltflüchen bis hin zu leistungsstarken Daten-Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="57f67-157">UWP provides more than 45 controls, ranging from simple buttons to powerful data controls.</span></span> 

    [<span data-ttu-id="57f67-158">Mehr über UWP-Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="57f67-158">Learn about UWP controls</span></span>](/windows/uwp/design/controls-and-patterns/)

* **<span data-ttu-id="57f67-159">Gestalten Sie inklusiv</span><span class="sxs-lookup"><span data-stu-id="57f67-159">Be inclusive</span></span>** 

    <span data-ttu-id="57f67-160">Eine gut gestaltete App ist für Menschen mit Behinderungen zugänglich.</span><span class="sxs-lookup"><span data-stu-id="57f67-160">A well-design app is accessible to people with disabilities.</span></span> <span data-ttu-id="57f67-161">Mit zusätzlichem Code können Sie Ihre Apps mit anderen Menschen auf der ganzen Welt teilen.</span><span class="sxs-lookup"><span data-stu-id="57f67-161">With some extra coding, you can share your app with people around the world.</span></span>

    [<span data-ttu-id="57f67-162">Mehr über Usability</span><span class="sxs-lookup"><span data-stu-id="57f67-162">Learn about Usability</span></span>](/windows/uwp/design/usability/)


## <a name="be-engaging-and-immersive"></a><span data-ttu-id="57f67-163">Gestalten Sie ansprechend und immersiv</span><span class="sxs-lookup"><span data-stu-id="57f67-163">Be engaging and immersive</span></span> 

<span data-ttu-id="57f67-164">Gestalten Sie Ihre App ansprechend, indem Sie physische Elemente wie Licht und Bewegung integrieren.</span><span class="sxs-lookup"><span data-stu-id="57f67-164">Make your app engaging by incorporating physical elements, like light and motion.</span></span> 

## <a name="use-light"></a><span data-ttu-id="57f67-165">Verwendung von Licht</span><span class="sxs-lookup"><span data-stu-id="57f67-165">Use light</span></span>

<span data-ttu-id="57f67-166">Licht kann unsere Aufmerksamkeit auf sich ziehen.</span><span class="sxs-lookup"><span data-stu-id="57f67-166">Light has a way of drawing our attention.</span></span> <span data-ttu-id="57f67-167">Es schafft Atmosphäre und Raumgefühl und ist ein praktisches Werkzeug, um Informationen zu beleuchten.</span><span class="sxs-lookup"><span data-stu-id="57f67-167">It creates atmosphere and a sense of place, and it’s a practical tool to illuminate information.</span></span>
        
<span data-ttu-id="57f67-168">Bringen Sie Licht in Ihre UWP-App:</span><span class="sxs-lookup"><span data-stu-id="57f67-168">Add light to your UWP app:</span></span>
        
* <span data-ttu-id="57f67-169">[Reveal-Highlight](../style/reveal.md) setzt Licht ein, um interaktive Elemente hervorzuheben. Licht beleuchtet das Element, mit dem der Benutzer interagieren kann und zeigt verborgene Grenzen auf.</span><span class="sxs-lookup"><span data-stu-id="57f67-169">[Reveal highlight](../style/reveal.md) uses light to make interactive elements stand out. Light illuminates the elements the user can interact with, revealing hidden borders.</span></span> <span data-ttu-id="57f67-170">Reveal ist bei einigen Steuerelementen, wie z. B. der List-Ansicht und der Grid-Ansicht, automatisch aktiviert.</span><span class="sxs-lookup"><span data-stu-id="57f67-170">Reveal is automatically enabled on some controls, such as list view and grid view.</span></span> <span data-ttu-id="57f67-171">Sie können es für andere Steuerelementen aktivieren, indem Sie unsere vordefinierten Reveal-Highlight-Stile verwenden.</span><span class="sxs-lookup"><span data-stu-id="57f67-171">You can enable it on other controls by applying our predefined Reveal highlight styles.</span></span> 

* <span data-ttu-id="57f67-172">[Reveal-Focus](../style/reveal-focus.md) verwendet Licht, um die Aufmerksamkeit auf das Element zu lenken, das aktuell den Eingabefokus hat.</span><span class="sxs-lookup"><span data-stu-id="57f67-172">[Reveal focus](../style/reveal-focus.md) uses light to call attention to the element that currently has input focus.</span></span>  

## <a name="create-a-sense-of-depth"></a><span data-ttu-id="57f67-173">Schaffen Sie ein Gefühl von Tiefe</span><span class="sxs-lookup"><span data-stu-id="57f67-173">Create a sense of depth</span></span>

<span data-ttu-id="57f67-174">Wir leben in einer dreidimensionalen Welt.</span><span class="sxs-lookup"><span data-stu-id="57f67-174">We live in a three-dimensional world.</span></span> <span data-ttu-id="57f67-175">Durch die gezielte Integration von Tiefe in das UI verwandeln wir eine flache, 2D-Schnittstelle in etwas, das Informationen und Konzepte durch eine visuelle Hierarchie effizient präsentiert.</span><span class="sxs-lookup"><span data-stu-id="57f67-175">By purposefully incorporating depth into the UI, we transform a flat, 2-D interface into something more&mdash;something that efficiently presents information and concepts by creating a visual hierarchy.</span></span> <span data-ttu-id="57f67-176">Es erfindet neu, wie sich die Dinge in einer geschichteten, physikalischen Umgebung zueinander verhalten.</span><span class="sxs-lookup"><span data-stu-id="57f67-176">It reinvents how things relate to each other within a layered, physical environment</span></span>

<span data-ttu-id="57f67-177">Bringen Sie Tiefe in Ihre UWP-App:</span><span class="sxs-lookup"><span data-stu-id="57f67-177">Add depth to your UWP app:</span></span>

* <span data-ttu-id="57f67-178">[Acrylic](../style/acrylic.md) Ein transparentes Material, das dem Benutzer Ebenen von Inhalten anzeigt und eine Hierarchie von Oberflächenelementen aufbaut.</span><span class="sxs-lookup"><span data-stu-id="57f67-178">[Acrylic](../style/acrylic.md) is a translucent material that lets the user see layers of content, establishing a hierarchy of UI elements.</span></span>

* <span data-ttu-id="57f67-179">[Parallax](../motion/parallax.md) Erzeugt die Illusion der Tiefe, indem es Gegenstände im Vordergrund schneller als Gegenstände im Hintergrund erscheinen lässt.</span><span class="sxs-lookup"><span data-stu-id="57f67-179">[Parallax](../motion/parallax.md) creates the illusion of depth by making items in the foreground appear to move more quickly than items in the background.</span></span>

## <a name="incorporate-motion"></a><span data-ttu-id="57f67-180">Integrieren von Bewegung</span><span class="sxs-lookup"><span data-stu-id="57f67-180">Incorporate motion</span></span>

<span data-ttu-id="57f67-181">Stellen Sie sich Motion-Design wie einen Film vor.</span><span class="sxs-lookup"><span data-stu-id="57f67-181">Think of motion design like a movie.</span></span> <span data-ttu-id="57f67-182">Nahtlose Übergänge halten Sie auf die Geschichte konzentriert und erwecken Erlebnisse zum Leben.</span><span class="sxs-lookup"><span data-stu-id="57f67-182">Seamless transitions keep you focused on the story, and bring experiences to life.</span></span> <span data-ttu-id="57f67-183">Wir können dieses Gefühl in unsere Entwürfe einbringen und Menschen von einer Aufgabe zur nächsten führen.</span><span class="sxs-lookup"><span data-stu-id="57f67-183">We can invite those feelings into our designs, leading people from one task to the next with cinematic ease.</span></span>

<span data-ttu-id="57f67-184">Bringen Sie Bewegung in Ihre UWP-App:</span><span class="sxs-lookup"><span data-stu-id="57f67-184">Add motion to your UWP app:</span></span>

* <span data-ttu-id="57f67-185">[Connected-Animations](../motion/connected-animation.md) helfen dem Benutzer, den Kontext zu behalten, indem sie einen nahtlosen Übergang zwischen den Szenen herstellen.</span><span class="sxs-lookup"><span data-stu-id="57f67-185">[Connected animations](../motion/connected-animation.md) help the user maintain context by creating a seamless transition between scenes.</span></span> 

## <a name="build-it-with-the-right-material"></a><span data-ttu-id="57f67-186">Verwenden Sie das richtige Material</span><span class="sxs-lookup"><span data-stu-id="57f67-186">Build it with the right material</span></span>

<span data-ttu-id="57f67-187">Die Dinge, die uns in der realen Welt umgeben, sind sinnlich und belebend.</span><span class="sxs-lookup"><span data-stu-id="57f67-187">The things that surround us in the real world are sensory and invigorating.</span></span> <span data-ttu-id="57f67-188">Sie biegen, strecken, prallen, zerspringen und gleiten.</span><span class="sxs-lookup"><span data-stu-id="57f67-188">They bend, stretch, bounce, shatter, and glide.</span></span> <span data-ttu-id="57f67-189">Diese materiellen Qualitäten übersetzen sich in digitale Umgebungen, die Menschen dazu bringen, unsere Entwürfe zu berühren und zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="57f67-189">Those material qualities translate to digital environments, making people want to reach out and touch our designs.</span></span>

<span data-ttu-id="57f67-190">Bringen Sie Material in Ihre UWP-App:</span><span class="sxs-lookup"><span data-stu-id="57f67-190">Add material to your UWP app:</span></span> 
        
* <span data-ttu-id="57f67-191">[Acrylic](../style/acrylic.md) Ein transparentes Material, das dem Benutzer Ebenen von Inhalten anzeigt und eine Hierarchie von Oberflächenelementen aufbaut.</span><span class="sxs-lookup"><span data-stu-id="57f67-191">[Acrylic](../style/acrylic.md)  is a translucent material that lets the user see layers of content, establishing a hierarchy of UI elements.</span></span> 

## <a name="design-toolkits-and-code-samples"></a><span data-ttu-id="57f67-192">Design-Toolkits und Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="57f67-192">Design toolkits and code samples</span></span>

<span data-ttu-id="57f67-193">Sie möchten Ihre eigenen Apps mit Fluent Design erstellen?</span><span class="sxs-lookup"><span data-stu-id="57f67-193">Want to get started creating your own apps with Fluent Design?</span></span> <span data-ttu-id="57f67-194">Unsere Toolkits für Adobe XD, Adobe Illustrator, Adobe Photoshop, Framer und Sketch helfen Ihnen, Ihre Entwürfe zu beschleunigen. Mit unseren Beispielen können Sie schneller entwickeln.</span><span class="sxs-lookup"><span data-stu-id="57f67-194">Our toolkits for Adobe XD, Adobe Illustrator, Adobe Photoshop, Framer, and Sketch will help jumpstart your designs, and our samples will help get you coding faster.</span></span>

* <span data-ttu-id="57f67-195">Schauen Sie sich unsere [Seite zu Design-Toolkits und Beispielen](/windows/uwp/design/downloads/) an.</span><span class="sxs-lookup"><span data-stu-id="57f67-195">Check out our [Design toolkits and samples page](/windows/uwp/design/downloads/)</span></span>

<img src="images/fluentdesign_header.png" alt=" " />








