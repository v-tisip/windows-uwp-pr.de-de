---
description: Lernen Sie das Fluent Design und dessen Integration in Ihre Apps kennen.
title: Fluent Design System für Windows
author: mijacobs
keywords: Layout von UWP-Apps, universelle Windows-Plattform, App-Design, Schnittstelle, fluent design system
ms.author: mijacobs
ms.date: 3/7/2018
ms.topic: article
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: c61eb71a82234a1339295536140121d80f83a033
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7570797"
---
# <a name="the-fluent-design-system-for-windows-app-creators"></a><span data-ttu-id="7b896-104">Das Fluent Design System für Windows-app-creators</span><span class="sxs-lookup"><span data-stu-id="7b896-104">The Fluent Design System for Windows app creators</span></span>

![Fluent Design-header](images/fluentdesign-app-header.jpg)

## <a name="introduction"></a><span data-ttu-id="7b896-106">Einführung</span><span class="sxs-lookup"><span data-stu-id="7b896-106">Introduction</span></span>

<span data-ttu-id="7b896-107">Das Fluent Design System ist unser System zur Erstellung adaptiver, empathischer und schöner Benutzeroberflächen.</span><span class="sxs-lookup"><span data-stu-id="7b896-107">The Fluent Design System is our system for creating adaptive, empathetic, and beautiful user interfaces.</span></span>

## <a name="principles"></a><span data-ttu-id="7b896-108">Prinzipien</span><span class="sxs-lookup"><span data-stu-id="7b896-108">Principles</span></span>

**<span data-ttu-id="7b896-109">Adaptiv: Fluent-Erlebnisse fühlen sich auf jedem Gerät natürlich an.</span><span class="sxs-lookup"><span data-stu-id="7b896-109">Adaptive: Fluent experiences feel natural on each device</span></span>**

<span data-ttu-id="7b896-110">Fluent-Erlebnisse passen sich an die Umgebung an.</span><span class="sxs-lookup"><span data-stu-id="7b896-110">Fluent experiences adapt to the environment.</span></span> <span data-ttu-id="7b896-111">Ein Fluent-Erlebnis fühlt sich auf einem Tablet, desktop-PCs und einer Xbox – es funktioniert sogar hervorragend auf einem Mixed Reality-Kopfhörer.</span><span class="sxs-lookup"><span data-stu-id="7b896-111">A Fluent experience feels comfortable on a tablet, a desktop PC, and an Xbox—it even works great on a Mixed Reality headset.</span></span> <span data-ttu-id="7b896-112">Und wenn Sie mehr Hardware hinzufügen, wie z. B. einen zusätzlichen Monitor für Ihren PC, nutzt ein Fluent-Erlebnis diese Vorteile.</span><span class="sxs-lookup"><span data-stu-id="7b896-112">And when you add more hardware, like an additional monitor for your PC, a Fluent experience takes advantage of it.</span></span>

**<span data-ttu-id="7b896-113">Empathisch: Fluent-Erlebnisse sind intuitiv und kraftvoll.</span><span class="sxs-lookup"><span data-stu-id="7b896-113">Empathetic: Fluent experiences are intuitive and powerful</span></span>**

<span data-ttu-id="7b896-114">Fluent-Erlebnisse passen sich dem Verhalten und der Absicht an – sie verstehen und antizipieren, was nötig ist.</span><span class="sxs-lookup"><span data-stu-id="7b896-114">Fluent experiences adjust to behavior and intent&mdash;they understand and anticipate what’s needed.</span></span> <span data-ttu-id="7b896-115">Sie vereinen Menschen und Ideen, egal ob sie sich auf gegenüberliegenden Seiten der Welt befinden oder direkt nebeneinander stehen.</span><span class="sxs-lookup"><span data-stu-id="7b896-115">They unite people and ideas, whether they’re on opposite sides of the globe or standing right next to each other.</span></span>

**<span data-ttu-id="7b896-116">Wunderschön: Fluent-Erlebnisse sind einnehmend und immersiv.</span><span class="sxs-lookup"><span data-stu-id="7b896-116">Beautiful: Fluent experiences are engaging and immersive</span></span>**

<span data-ttu-id="7b896-117">Durch das Einbeziehen von Elementen der physischen Welt erschließt sich ein Fluent-Erlebniss etwas Grundsätzliches.</span><span class="sxs-lookup"><span data-stu-id="7b896-117">By incorporating elements of the physical world, a Fluent experience taps into something fundamental.</span></span> <span data-ttu-id="7b896-118">Es nutzt Licht, Schatten, Bewegung, Tiefe und Textur, um Informationen intuitiv und instinktiv zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="7b896-118">It uses light, shadow, motion, depth, and texture to organize information in a way that feels intuitive and instinctual.</span></span>


## <a name="applying-fluent-design-to-your-app-with-uwp"></a><span data-ttu-id="7b896-119">Umsetzung des Fluent Designs für Ihre app mit UWP</span><span class="sxs-lookup"><span data-stu-id="7b896-119">Applying Fluent Design to your app with UWP</span></span>

![Fluent Design-logo](images/fluentdesign_header.png)

<span data-ttu-id="7b896-121">Unseren Designrichtlinien wird erläutert, wie Fluent-Entwurfsprinzipien auf apps anwenden.</span><span class="sxs-lookup"><span data-stu-id="7b896-121">Our design guidelines explain how to apply Fluent Design principles to apps.</span></span> <span data-ttu-id="7b896-122">Welche Art von apps?</span><span class="sxs-lookup"><span data-stu-id="7b896-122">What type of apps?</span></span> <span data-ttu-id="7b896-123">Obwohl viele unserer Richtlinien auf jeder Plattform angewendet werden können, haben wir Windows-Plattform (der universellen) zur Unterstützung der Fluent Design erstellt.</span><span class="sxs-lookup"><span data-stu-id="7b896-123">While many of our guidelines can be applied to any platform, we created UWP (the Universal Windows Platform) to support Fluent Design.</span></span>

<span data-ttu-id="7b896-124">Fluent Design-Features sind in UWP integriert.</span><span class="sxs-lookup"><span data-stu-id="7b896-124">Fluent Design features are built into UWP.</span></span> <span data-ttu-id="7b896-125">Einige dieser Funktionen – wie effektive Pixel und das universelle Eingabesystem – arbeiten automatisch.</span><span class="sxs-lookup"><span data-stu-id="7b896-125">Some of these features&mdash;such as effective pixels and the universal input system&mdash;are automatic.</span></span> <span data-ttu-id="7b896-126">Sie müssen keinen zusätzlichen Code schreiben, um sie zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="7b896-126">You don't have to write any extra code to take advantage of them.</span></span> <span data-ttu-id="7b896-127">Andere Funktionen, wie z. B. Acryl, sind optional. Sie nehmen sie in Ihre Anwendung auf, indem Sie Code schreiben.</span><span class="sxs-lookup"><span data-stu-id="7b896-127">Other features, like acrylic, are optional; you add them to your app by writing code to include them.</span></span>

> <span data-ttu-id="7b896-128">Wir bringen UWP-Steuerelemente auf den Desktop, damit Sie das Aussehen, Verhalten und die Funktionalität Ihrer vorhandenen WPF- oder Windows-Anwendungen mit Fluent Design-Features verbessern können.</span><span class="sxs-lookup"><span data-stu-id="7b896-128">We're bringing UWP controls to the desktop so that you can enhance the look, feel, and functionality of your existing WPF or Windows applications with Fluent Design features.</span></span> <span data-ttu-id="7b896-129">Weitere Informationen hierzu finden Sie in der [Host-UWP-Steuerelemente in WPF- oder Windows Forms-Anwendung](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="7b896-129">To learn more, see [Host UWP controls in WPF and Windows Forms applications](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<!-- To apply Fluent Design to your app, follow our guidelines and use UWP (Universal Windows Platform) you can use UWP UI features combined with best practices for creating apps that perform beautifully on all types of Windows-powered devices. -->

<span data-ttu-id="7b896-130">Zusätzlich zur designanleitungen zeigen unserer Fluent Design-Artikel auch Ihnen, wie Sie Code schreiben, der Ihre Entwürfe passieren erheblich vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="7b896-130">In addition to design guidance, our Fluent Design articles also show you how to write the code that makes your designs happen.</span></span> <span data-ttu-id="7b896-131">UWP verwendet XAML, eine Markup-basierte Sprache, die zum Erstellen von Benutzeroberflächen erleichtert.</span><span class="sxs-lookup"><span data-stu-id="7b896-131">UWP uses XAML, a markup-based language that makes it easier to create user interfaces.</span></span> <span data-ttu-id="7b896-132">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7b896-132">Here's an example:</span></span>

```xaml
<Grid BorderBrush="Blue" BorderThickness="4">
    <TextBox Text="Design with XAML" Margin="20" Padding="24,16"/>
</Grid>
```

![](images/xaml-example.png)


> <span data-ttu-id="7b896-133">Wenn Sie die Entwicklung für UWP sind, sehen Sie sich unsere [Erste Schritte mit UWP-Seite](https://developer.microsoft.com/windows/apps/getstarted).</span><span class="sxs-lookup"><span data-stu-id="7b896-133">If you're new to UWP development, check out our [Get started with UWP page](https://developer.microsoft.com/windows/apps/getstarted).</span></span>

## <a name="find-a-natural-fit"></a><span data-ttu-id="7b896-134">Eine natürliche Form finden</span><span class="sxs-lookup"><span data-stu-id="7b896-134">Find a natural fit</span></span>

<span data-ttu-id="7b896-135">Wie gestaltet man eine App auf einer Vielzahl von Geräten natürlich?</span><span class="sxs-lookup"><span data-stu-id="7b896-135">How do you make an app feel natural on a variety of devices?</span></span> <span data-ttu-id="7b896-136">Indem sie sich so anfühlt, als wäre sie für jedes einzelne Gerät entwickelt worden.</span><span class="sxs-lookup"><span data-stu-id="7b896-136">By making it feel as though it were designed with each specific device in mind.</span></span> <span data-ttu-id="7b896-137">Ein UI-Layout, das sich an verschiedene Bildschirmgrößen anpasst (ohne vergeudeten Platz oder Überladung) schafft ein natürliches Erlebnis – als ob es für dieses Gerät entwickelt wurde.</span><span class="sxs-lookup"><span data-stu-id="7b896-137">A UI layout that adapts to different screen sizes&mdash;so there's no wasted space (but no crowding either)&mdash;makes an experience feel natural, as though it were designed for that device.</span></span>

:::row:::
    :::column:::
        ![fpo image](images/thumbnail-size-classes.jpg)
    :::column-end:::
    :::column span="2":::
        **Design for the right breakpoints**

        Instead of designing for every individual screen size, focusing on a few key widths (also called "breakpoints") can greatly simplify your designs and code while still making your app look great on small to large screens.

        [Learn about screen sizes and breakpoints](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](images/rspd-resize.gif)
    :::column-end:::
    :::column span="2":::
        **Create a responsive layout**

        For an app to feel natural, it should adapt its layout to different screen sizes and devices. You can use automatic sizing, layout panels, visual states, and even separate UI definitions in XAML to create a responsive UI.

        [Learn about responsive design](/windows/uwp/design/layout/responsive-design)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](images/devices.jpg)
    :::column-end:::
    :::column span="2":::
        **Design for a spectrum of devices**

        UWP apps can run on a wide variety of Windows-powered devices. It's helpful to understand which devices are available, what they're made for, and how users interact with them.

        [Learn about UWP devices](/windows/uwp/design/devices/)
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](images/keyboard-shortcuts.jpg)
    :::column-end:::
    :::column span="2":::
        **Optimize for the right input**

        UWP apps automatically support common mouse, keyboard, pen, and touch interactions&mdash;there's nothing extra you have to do. But you can enhance your app with optimized support for specific inputs, like pen and the Surface Dial.

        [Learn about inputs and interactions](/windows/uwp/design/input/input-primer)
:::row-end:::

## <a name="make-it-intuitive"></a><span data-ttu-id="7b896-138">Stellen sie intuitiv</span><span class="sxs-lookup"><span data-stu-id="7b896-138">Make it intuitive</span></span>

<span data-ttu-id="7b896-139">Ein Erlebnis fühlt sich intuitiv, wenn es sich um die Art und Weise verhält, wie der Benutzer es erwartet.</span><span class="sxs-lookup"><span data-stu-id="7b896-139">An experience feels intuitive when it behaves the way the user expects it to.</span></span> <span data-ttu-id="7b896-140">Durch die Verwendung etablierter Steuerelemente und Muster und die Nutzung der Plattformunterstützung für die Zugänglichkeit und Globalisierung schaffen Sie eine reibungsloses Erlebnis, mit dem die Benutzer produktiver sind.</span><span class="sxs-lookup"><span data-stu-id="7b896-140">By using established controls and patterns and taking advantage of platform support for accessibility and globalization, you create an effortless experience that helps users be more productive.</span></span>

<span data-ttu-id="7b896-141">Empathie bedeutet, das Richtige zur richtigen Zeit zu tun.</span><span class="sxs-lookup"><span data-stu-id="7b896-141">Demonstrating empathy is about doing the right thing at the right time.</span></span>

<span data-ttu-id="7b896-142">Fluent-Erlebnisse verwenden Steuerelement und Muster konsequent, sodass sie sich so verhalten, wie es der Benutzer erwartet hat.</span><span class="sxs-lookup"><span data-stu-id="7b896-142">Fluent experiences use controls and patterns consistently, so they behave in ways the user has learned to expect.</span></span> <span data-ttu-id="7b896-143">Fluent-Erlebnisse sind für Menschen mit einem breiten Spektrum an körperlichen Fähigkeiten zugänglich und umfassen Globalisierungsfunktionen für Menschen auf der ganzen Welt.</span><span class="sxs-lookup"><span data-stu-id="7b896-143">Fluent experiences are accessible to people with a wide range of physical abilities, and incorporate globalization features so people around the world can use them.</span></span>

:::row:::
    :::column:::
        ![fpo image](images/thumbnail-navview.png)
    :::column-end:::
    :::column span="2":::
        **Provide the right navigation**

        Create an effortless experience by using the right app structure and navigation components.

        [Learn about navigation](/windows/uwp/design/basics/navigation-basics/)
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](images/thumbnail-commanding.png)
    :::column-end:::
    :::column span="2":::
        **Be interactive**

        Buttons, command bars, keyboard shortcuts, and context menus enable users to interact with your app; they're the tools that change a static experience into something dynamic.

        [Learn about commanding](/windows/uwp/design/basics/commanding-basics/)
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](images/thumbnail-controls-2.jpg)
    :::column-end:::
    :::column span="2":::
        **Use the right control for the job**

        Controls are the building blocks of the user interface; using the right control helps you create a user interface that behaves the way users expect it to.  UWP provides more than 45 controls,ranging from simple buttons to powerful data controls.

        [Learn about UWP controls](/windows/uwp/design/controls-and-patterns/)
:::row-end:::

:::row:::
    :::column:::
        ![inclusive image](images/thumbnail-inclusive.png)
    :::column-end:::
    :::column span="2":::
        **Be inclusive**
        A well-design app is accessible to people with disabilities. With some extra coding, you can share your app with people around the world.

        [Learn about Usability](/windows/uwp/design/usability/)
:::row-end:::

## <a name="be-engaging-and-immersive"></a><span data-ttu-id="7b896-144">Gestalten Sie ansprechend und immersiv</span><span class="sxs-lookup"><span data-stu-id="7b896-144">Be engaging and immersive</span></span>

<span data-ttu-id="7b896-145">Beim Fluent Design geht es nicht um auffällige Effekte.</span><span class="sxs-lookup"><span data-stu-id="7b896-145">Fluent Design isn't about flashy effects.</span></span> <span data-ttu-id="7b896-146">Es beinhaltet physikalische Effekte, die das Benutzererlebnis wirklich verbessern. Es emuliert Erlebnisse, die unser Gehirn effizient verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="7b896-146">It incorporates physical effects that truly enhance the user experience, because they emulate experiences that our brains are programmed to process efficiently.</span></span>

## <a name="use-light"></a><span data-ttu-id="7b896-147">Verwendung von Licht</span><span class="sxs-lookup"><span data-stu-id="7b896-147">Use light</span></span>

<span data-ttu-id="7b896-148">Licht kann unsere Aufmerksamkeit auf sich ziehen.</span><span class="sxs-lookup"><span data-stu-id="7b896-148">Light has a way of drawing our attention.</span></span> <span data-ttu-id="7b896-149">Es schafft Atmosphäre und Raumgefühl und ist ein praktisches Werkzeug, um Informationen zu beleuchten.</span><span class="sxs-lookup"><span data-stu-id="7b896-149">It creates atmosphere and a sense of place, and it’s a practical tool to illuminate information.</span></span>

<span data-ttu-id="7b896-150">Bringen Sie Licht in Ihre UWP-App:</span><span class="sxs-lookup"><span data-stu-id="7b896-150">Add light to your UWP app:</span></span>

:::row:::
    :::column:::
        ![fpo image](../style/images/Nav_Reveal_Animation.gif)
    :::column-end:::
    :::column span="2":::
        **Reveal highlight**

        [Reveal highlight](../style/reveal.md) uses light to make interactive elements stand out. Light illuminates the elements the user can interact with, revealing hidden borders. Reveal is automatically enabled on some controls, such as list view and grid view. You can enable it on other controls by applying our predefined Reveal highlight styles.
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](../style/images/traveling-focus-fullscreen-light-rf.gif)
    :::column-end:::
    :::column span="2":::
        **Reveal focus**

        [Reveal focus](../style/reveal-focus.md) uses light to call attention to the element that currently has input focus.
:::row-end:::

## <a name="create-a-sense-of-depth"></a><span data-ttu-id="7b896-151">Schaffen Sie ein Gefühl von Tiefe</span><span class="sxs-lookup"><span data-stu-id="7b896-151">Create a sense of depth</span></span>

<span data-ttu-id="7b896-152">Wir leben in einer dreidimensionalen Welt.</span><span class="sxs-lookup"><span data-stu-id="7b896-152">We live in a three-dimensional world.</span></span> <span data-ttu-id="7b896-153">Durch die gezielte Integration von Tiefe in das UI verwandeln wir eine flache, 2D-Schnittstelle in etwas, das Informationen und Konzepte durch eine visuelle Hierarchie effizient präsentiert.</span><span class="sxs-lookup"><span data-stu-id="7b896-153">By purposefully incorporating depth into the UI, we transform a flat, 2-D interface into something more&mdash;something that efficiently presents information and concepts by creating a visual hierarchy.</span></span> <span data-ttu-id="7b896-154">Es erfindet neu, wie sich die Dinge in einer geschichteten, physikalischen Umgebung zueinander verhalten.</span><span class="sxs-lookup"><span data-stu-id="7b896-154">It reinvents how things relate to each other within a layered, physical environment</span></span>

<span data-ttu-id="7b896-155">Bringen Sie Tiefe in Ihre UWP-App:</span><span class="sxs-lookup"><span data-stu-id="7b896-155">Add depth to your UWP app:</span></span>

:::row:::
    :::column:::
        ![fpo image](../motion/images/_parallax_v2.gif)
    :::column-end:::
    :::column span="2":::
        **Parallax**

        [Parallax](../motion/parallax.md) creates the illusion of depth by making items in the foreground appear to move more quickly than items in the background.
:::row-end:::

## <a name="incorporate-motion"></a><span data-ttu-id="7b896-156">Integrieren von Bewegung</span><span class="sxs-lookup"><span data-stu-id="7b896-156">Incorporate motion</span></span>

<span data-ttu-id="7b896-157">Stellen Sie sich Motion-Design wie einen Film vor.</span><span class="sxs-lookup"><span data-stu-id="7b896-157">Think of motion design like a movie.</span></span> <span data-ttu-id="7b896-158">Nahtlose Übergänge halten Sie auf die Geschichte konzentriert und erwecken Erlebnisse zum Leben.</span><span class="sxs-lookup"><span data-stu-id="7b896-158">Seamless transitions keep you focused on the story, and bring experiences to life.</span></span> <span data-ttu-id="7b896-159">Wir können dieses Gefühl in unsere Entwürfe einbringen und Menschen von einer Aufgabe zur nächsten führen.</span><span class="sxs-lookup"><span data-stu-id="7b896-159">We can invite those feelings into our designs, leading people from one task to the next with cinematic ease.</span></span>

<span data-ttu-id="7b896-160">Bringen Sie Bewegung in Ihre UWP-App:</span><span class="sxs-lookup"><span data-stu-id="7b896-160">Add motion to your UWP app:</span></span>

:::row:::
    :::column:::
        ![continuity gif](images/continuityXbox.gif)
    :::column-end:::
    :::column span="2":::
        **Connected animations**

        [Connected animations](../motion/connected-animation.md) help the user maintain context by creating a seamless transition between scenes.
:::row-end:::

## <a name="build-it-with-the-right-material"></a><span data-ttu-id="7b896-161">Verwenden Sie das richtige Material</span><span class="sxs-lookup"><span data-stu-id="7b896-161">Build it with the right material</span></span>

<span data-ttu-id="7b896-162">Die Dinge, die uns in der realen Welt umgeben, sind sinnlich und belebend.</span><span class="sxs-lookup"><span data-stu-id="7b896-162">The things that surround us in the real world are sensory and invigorating.</span></span> <span data-ttu-id="7b896-163">Sie biegen, strecken, prallen, zerspringen und gleiten.</span><span class="sxs-lookup"><span data-stu-id="7b896-163">They bend, stretch, bounce, shatter, and glide.</span></span> <span data-ttu-id="7b896-164">Diese materiellen Qualitäten übersetzen sich in digitale Umgebungen, die Menschen dazu bringen, unsere Entwürfe zu berühren und zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="7b896-164">Those material qualities translate to digital environments, making people want to reach out and touch our designs.</span></span>

<span data-ttu-id="7b896-165">Bringen Sie Material in Ihre UWP-App:</span><span class="sxs-lookup"><span data-stu-id="7b896-165">Add material to your UWP app:</span></span>

:::row:::
    :::column:::
        ![fpo image](../style/images/acrylic_lighttheme_base.png)
    :::column-end:::
    :::column span="2":::
        **Acrylic**

        [Acrylic](../style/acrylic.md) is a translucent material that lets the user see layers of content, establishing a hierarchy of UI elements.
:::row-end:::

## <a name="design-toolkits-and-code-samples"></a><span data-ttu-id="7b896-166">Design-Toolkits und Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="7b896-166">Design toolkits and code samples</span></span>

<span data-ttu-id="7b896-167">Sie möchten Ihre eigenen Apps mit Fluent Design erstellen?</span><span class="sxs-lookup"><span data-stu-id="7b896-167">Want to get started creating your own apps with Fluent Design?</span></span> <span data-ttu-id="7b896-168">Unsere Toolkits für Adobe XD, Adobe Illustrator, Adobe Photoshop, Framer und Sketch helfen Ihnen, Ihre Entwürfe zu beschleunigen. Mit unseren Beispielen können Sie schneller entwickeln.</span><span class="sxs-lookup"><span data-stu-id="7b896-168">Our toolkits for Adobe XD, Adobe Illustrator, Adobe Photoshop, Framer, and Sketch will help jumpstart your designs, and our samples will help get you coding faster.</span></span>

:::row:::
    :::column:::
        ![fpo image](images/thumbnail-toolkits.jpg)
    :::column-end:::
    :::column span="2":::
        **Design toolkits and samples page**

        Check out our [Design toolkits and samples page](/windows/uwp/design/downloads/)
:::row-end:::









