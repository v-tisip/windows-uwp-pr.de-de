---
author: mijacobs
Description: The universal design features included in every UWP app help you build apps that scale beautifully across a range of devices.
title: Einführung in das App-Design (Windows-Apps) für die Universelle Windows-Plattform (UWP)
ms.assetid: 50A5605E-3A91-41DB-800A-9180717C1E86
ms.author: mijacobs
ms.date: 05/05/2018
ms.topic: article
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 0168ae8d5058b6dde7cd137e95560008d2a4973d
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7162155"
---
# <a name="introduction-to-uwp-app-design"></a><span data-ttu-id="1f6c8-103">Einführung in das UWP-App-Design</span><span class="sxs-lookup"><span data-stu-id="1f6c8-103">Introduction to UWP app design</span></span>

![Beispiel für eine Beleuchtungs-App](images/introUWP-header.jpg)

<span data-ttu-id="1f6c8-105">Der Designleitfaden für die Universelle Windows-Plattform (UWP) ist eine Ressource, um ansprechende, optimierte Apps zu entwerfen und erstellen.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-105">The Universal Windows Platform (UWP) design guidance is a resource to help you design and build beautiful, polished apps.</span></span>

<span data-ttu-id="1f6c8-106">Es ist keine Liste von Vorschriften, sondern ein lebendiges Dokument, das entwickelt wurde, um sich entsprechend unseres [Fluent Design-Systems](../fluent-design-system/index.md) sowie der Bedürfnisse unserer App-Entwicklungs-Community zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-106">It's not a list of prescriptive rules - it's a living document, designed to adapt to our evolving [Fluent Design System](../fluent-design-system/index.md) as well as the needs of our app-building community.</span></span>

<span data-ttu-id="1f6c8-107">Diese Einführung bietet einen Überblick über die universellen Designfunktionen, die in jeder UWP-Apps enthalten sind. Es hilft Ihnen, Benutzeroberflächen (UIs) zu erstellen, die sich über eine Vielzahl von Geräten wunderbar skalieren lassen.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-107">This introduction provides an overview of the universal design features that are included in every UWP app, helping you build user interfaces (UI) that scale beautifully across a range of devices.</span></span>

## <a name="effective-pixels-and-scaling"></a><span data-ttu-id="1f6c8-108">Effektive Pixel und Skalierung</span><span class="sxs-lookup"><span data-stu-id="1f6c8-108">Effective pixels and scaling</span></span>

<span data-ttu-id="1f6c8-109">UWP-apps, die auf allen [Windows 10-Geräten](../devices/index.md)aus Ihrem Fernsehgerät, Tablets oder PCs ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-109">UWP apps run on all [Windows 10 devices](../devices/index.md), from your TV to your tablet or PC.</span></span> <span data-ttu-id="1f6c8-110">Wie also entwerfen Sie eine Benutzeroberfläche, die auf einer Vielzahl von Geräten und Bildschirmgrößen gut aussieht?</span><span class="sxs-lookup"><span data-stu-id="1f6c8-110">So how do you design a UI that looks good on a wide variety of devices and screen sizes?</span></span>

![Dieselbe App auf verschiedenen Geräten](images/universal-image-1.jpg)

<span data-ttu-id="1f6c8-112">UWP hilft durch UI-Elemente automatisch anpassen, sodass sie lesbar und leicht zu interagieren auf allen Geräten und Bildschirmgrößen stehen.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-112">UWP helps by automatically adjusting UI elements so that they're legible and easy to interact with on all devices and screen sizes.</span></span>

<span data-ttu-id="1f6c8-113">Wenn Ihre App auf einem Gerät ausgeführt wird, verwendet das System einen Algorithmus, um die Art der Anzeige der UI-Elemente auf dem Bildschirm zu normalisieren.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-113">When your app runs on a device, the system uses an algorithm to normalize the way UI elements display on the screen.</span></span> <span data-ttu-id="1f6c8-114">Dieser Skalierungsalgorithmus berücksichtigt den Abstand zum Bildschirm und die Bildschirmdichte (Pixel pro Zoll), um die wahrgenommene Größe (anstelle der physischen Größe) zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-114">This scaling algorithm takes into account viewing distance and screen density (pixels per inch) to optimize for perceived size (rather than physical size).</span></span> <span data-ttu-id="1f6c8-115">Mit dem Skalierungsalgorithmus wird sichergestellt, dass der Schriftgrad 24 Pixel auf einem 3 Meter entfernten Surface Hub genauso für den Benutzer lesbar ist wie der Schriftgrad 24 Pixel auf einem 5-Zoll-Smartphone, das nur einige Zentimeter entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-115">The scaling algorithm ensures that a 24 px font on Surface Hub 10 feet away is just as legible to the user as a 24 px font on 5" phone that's a few inches away.</span></span>

![Sichtabstände für verschiedene Geräte](images/scaling-chart.png)

<span data-ttu-id="1f6c8-117">Aufgrund der Funktionsweise des Skalierungssystems beim Entwerfen Ihrer UWP-App, verwenden Sie effektive Pixeln, und nicht die tatsächlichen physischen Pixel.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-117">Because of how the scaling system works, when you design your UWP app, you're designing in effective pixels, not actual physical pixels.</span></span> <span data-ttu-id="1f6c8-118">Effektive Pixel (epx) sind eine virtuelle Maßeinheit und werden verwendet, um Layoutabmessungen und -abstände unabhängig von der Pixeldichte auszudrücken.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-118">Effective pixels (epx) are a virtual unit of measurement, and they're used to express layout dimensions and spacing, independent of screen density.</span></span> <span data-ttu-id="1f6c8-119">(In unseren Richtlinien werden epx, ep und px austauschbar verwendet.)</span><span class="sxs-lookup"><span data-stu-id="1f6c8-119">(In our guidelines, epx, ep, and px are used interchangeably.)</span></span>

<span data-ttu-id="1f6c8-120">Sie können die Pixeldichte und die tatsächliche Bildschirmauflösung beim Entwerfen ignorieren.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-120">You can ignore the pixel density and the actual screen resolution when designing.</span></span> <span data-ttu-id="1f6c8-121">Entwerfen Sie stattdessen für die effektive Auflösung (die Auflösung in effektiven Pixeln) für eine Größenklasse (Details finden Sie im Artikel [Bildschirmgrößen und Haltepunkte](../layout/screen-sizes-and-breakpoints-for-responsive-design.md)).</span><span class="sxs-lookup"><span data-stu-id="1f6c8-121">Instead, design for the effective resolution (the resolution in effective pixels) for a size class (for details, see the [Screen sizes and breakpoints article](../layout/screen-sizes-and-breakpoints-for-responsive-design.md)).</span></span>

> [!TIP]
> <span data-ttu-id="1f6c8-122">Legen Sie beim Erstellen von Bildschirmmodellen in Bildbearbeitungsprogrammen die DPI auf 72 und die Bildgröße auf effektive Auflösung für die Zielgrößenklasse fest.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-122">When creating screen mockups in image editing programs, set the DPI to 72 and set the image dimensions to the effective resolution for the size class you're targeting.</span></span> <span data-ttu-id="1f6c8-123">Eine Liste der Größenklassen und effektiven Auflösungen finden Sie in dem Artikel [Bildschirmgrößen und Breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span><span class="sxs-lookup"><span data-stu-id="1f6c8-123">For a list of size classes and effective resolutions, see the [Screen sizes and breakpoints article](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span></span>

### <a name="multiples-of-four"></a><span data-ttu-id="1f6c8-124">Vielfache von vier</span><span class="sxs-lookup"><span data-stu-id="1f6c8-124">Multiples of four</span></span>

:::row:::
    :::column span:::
        The sizes, margins, and positions of UI elements should always be in **multiples of 4 epx** in your UWP apps.

        UWP scales across a range of devices with scaling plateaus of 100%, 125%, 150%, 175%, 200%, 225%, 250%, 300%, 350%, and 400%. The base unit is 4 because it's the only integer that can be scaled by non-whole numbers (e.g. 4*1.5 = 6). Using multiples of four aligns all UI elements with whole pixels and ensures UI elements have crisp, sharp edges. (Note that text doesn't have this requirement; text can have any size and position.)
    :::column-end:::
    :::column:::
        ![grid](images/4epx.svg)
    :::column-end:::
:::row-end:::

## <a name="layout"></a><span data-ttu-id="1f6c8-125">Layout</span><span class="sxs-lookup"><span data-stu-id="1f6c8-125">Layout</span></span>

<span data-ttu-id="1f6c8-126">Da UWP-Apps automatisch für alle Geräte skaliert werden, folgt das Entwerfen einer UWP-App für jedes Gerät derselben Struktur.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-126">Since UWP apps automatically scale to all devices, designing a UWP app for any device follows the same structure.</span></span> <span data-ttu-id="1f6c8-127">Beginnen wir mit den Grundlagen der Benutzeroberfläche einer UWP-App.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-127">Let's start from the very beginning of your UWP app's UI.</span></span>

### <a name="windows-frames-and-pages"></a><span data-ttu-id="1f6c8-128">Fenster, Rahmen und Seiten</span><span class="sxs-lookup"><span data-stu-id="1f6c8-128">Windows, Frames, and Pages</span></span>

:::row:::
    :::column:::
        When a UWP app is launched on any Windows 10 device, it launches in a [Window](/uwp/api/Windows.UI.Xaml.Controls.Window) with a [Frame](/uwp/api/Windows.UI.Xaml.Controls.Frame), which can navigate between [Page](/uwp/api/Windows.UI.Xaml.Controls.Page) instances.
    :::column-end:::
    :::column:::
        ![Frame](images/frame.svg)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        You can think of your app's UI as a collection of pages. It's up to you to decide what should go on each page, and the relationships between pages.

        To learn how you can organize your pages, see [Navigation basics](navigation-basics.md).
    :::column-end:::
    :::column:::
        ![Frame](images/collection-pages.svg)
    :::column-end:::
:::row-end:::

### <a name="page-layout"></a><span data-ttu-id="1f6c8-129">Seitenlayout</span><span class="sxs-lookup"><span data-stu-id="1f6c8-129">Page layout</span></span>

<span data-ttu-id="1f6c8-130">Wie sollten diese Seiten aussehen?</span><span class="sxs-lookup"><span data-stu-id="1f6c8-130">What should those pages look like?</span></span> <span data-ttu-id="1f6c8-131">Meistens besitzen die Seiten eine gemeinsame Struktur, um Konsistenz bereitzustellen, sodass Benutzer problemlos zwischen und auf App-Seiten navigieren können.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-131">Well, most pages follow a common structure to provide consistency, so users can easily navigate between and within pages of your app.</span></span> <span data-ttu-id="1f6c8-132">Seiten enthalten in der Regel drei Arten von UI-Elementen:</span><span class="sxs-lookup"><span data-stu-id="1f6c8-132">Pages typically contain three types of UI elements:</span></span>

- <span data-ttu-id="1f6c8-133">[Navigationselemente](navigation-basics.md) ermöglichen dem Benutzer, die Inhalte auszuwählen, die er anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-133">[Navigation](navigation-basics.md) elements help users choose the content they want to display.</span></span>
- <span data-ttu-id="1f6c8-134">[Befehlselemente](commanding-basics.md) initiieren Aktionen wie etwa das Bearbeiten, Speichern oder Freigeben von Inhalten.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-134">[Command](commanding-basics.md) elements initiate actions, such as manipulating, saving, or sharing content.</span></span>
- <span data-ttu-id="1f6c8-135">[Inhaltselemente](content-basics.md) zeigen die Inhalte der App an.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-135">[Content](content-basics.md) elements display the app's content.</span></span>

![Ein allgemeines Layoutmuster](../layout/images/page-components.svg)

<span data-ttu-id="1f6c8-137">Weitere Informationen zum Implementieren allgemeiner UWP-App Muster finden Sie im [Seitenlayout](../layout/page-layout.md).</span><span class="sxs-lookup"><span data-stu-id="1f6c8-137">To learn more about how to implement common UWP app patterns, see the [Page layout](../layout/page-layout.md) article.</span></span>

<span data-ttu-id="1f6c8-138">Sie können auch das [Windows Template Studio](https://github.com/Microsoft/WindowsTemplateStudio/tree/master) in Visual Studio verwenden, um mit einem Layout für Ihre App zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-138">You can also use the [Windows Template Studio](https://github.com/Microsoft/WindowsTemplateStudio/tree/master) in Visual Studio to get started with a layout for your app.</span></span>

## <a name="controls"></a><span data-ttu-id="1f6c8-139">Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="1f6c8-139">Controls</span></span>

<span data-ttu-id="1f6c8-140">Die UWP-Designplattform bietet eine Reihe von allgemeinen Steuerelementen, die auf allen Windows-Geräten funktionieren und den Prinzipien für unser [Fluent Design-System](../fluent-design-system/index.md) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-140">UWP's design platform provides a set of common controls that are guaranteed to work well on all Windows-powered devices, and they adhere to our [Fluent Design System](../fluent-design-system/index.md) principles.</span></span> <span data-ttu-id="1f6c8-141">Diese Steuerelemente reichen von einfachen Steuerelementen wie Schaltflächen und Textelementen bis hin zu ausgeklügelten Steuerelementen, die Listen aus einem Datensatz und einer Vorlage erzeugen können.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-141">These controls include everything from simple controls, like buttons and text elements, to sophisticated controls that can generate lists from a set of data and a template.</span></span>

![UWP-Steuerelemente](../style/images/color/windows-controls.svg)

<span data-ttu-id="1f6c8-143">Eine vollständige Liste der UWP-Steuerelemente und der -Muster, die Sie aus ihnen erstellen können, finden Sie im Abschnitt [Steuerelemente und Muster](../controls-and-patterns/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f6c8-143">For a complete list of UWP controls and the patterns you can make from them, see the [controls and patterns section](../controls-and-patterns/index.md).</span></span>

## <a name="style"></a><span data-ttu-id="1f6c8-144">Stil</span><span class="sxs-lookup"><span data-stu-id="1f6c8-144">Style</span></span>

<span data-ttu-id="1f6c8-145">Die allgemeinen Steuerelemente übernehmen automatisch das Systemdesign und die Akzentfarbe, arbeiten mit allen Eingabetypen und skalieren auf allen Geräten.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-145">Common controls automatically reflect the system theme and accent color, work with all input types, and scale to all devices.</span></span> <span data-ttu-id="1f6c8-146">Auf diese Weise spiegeln sie das Fluent Design System wider – sie sind anpassungsfähig, einfühlsam und schön.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-146">In that way, they reflect the Fluent Design System - they're adaptive, empathetic, and beautiful.</span></span> <span data-ttu-id="1f6c8-147">Allgemeine Steuerelemente verwenden Licht, Bewegung und Tiefe in ihren Standarddesigns. Durch die Verwendung dieser Steuerelemente integrieren Sie also unser Fluent Design-System in Ihre App.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-147">Common controls use light, motion, and depth in their default styles, so by using them, you're incorporating our Fluent Design System in your app.</span></span>

<span data-ttu-id="1f6c8-148">Allgemeine Steuerelemente sind zudem sehr anpassbar. Sie können die Vordergrundfarbe eines Steuerelements ändern oder sein Aussehen komplett anpassen.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-148">Common controls are highly customizable, too--you can change the foreground color of a control or completely customize it's appearance.</span></span> <span data-ttu-id="1f6c8-149">Um die standardmäßigen Stile in Steuerelementen zu überschreiben, verwenden Sie [einfache Formatierung](../controls-and-patterns/xaml-styles.md#lightweight-styling) oder erstellen [benutzerdefinierte Steuerelemente](../controls-and-patterns/control-templates.md) in XAML.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-149">To override the default styles in controls, use [lightweight styling](../controls-and-patterns/xaml-styles.md#lightweight-styling) or create [custom controls](../controls-and-patterns/control-templates.md) in XAML.</span></span>

![Akzentfarben-Gif](images/intro-style.gif)

## <a name="shell"></a><span data-ttu-id="1f6c8-151">Shell</span><span class="sxs-lookup"><span data-stu-id="1f6c8-151">Shell</span></span>

:::row:::
    :::column:::
        Your UWP app will interact with the broader Windows experience with tiles and notifications in the Windows [Shell](../shell/tiles-and-notifications/creating-tiles.md).

        Tiles are displayed in the Start menu and when your app launches, and they provide a glimpse of what's going on in your app. Their power comes from the content behind them, and the intelligence and craft with which they're offered up.

        UWP apps have four tile sizes (small, medium, wide, and large) that can be customized with the app's icon and identity. For guidance on designing tiles for your UWP app, see [Guidelines for tile and icon assets](../shell/tiles-and-notifications/app-assets.md).
    :::column-end:::
    :::column:::
        ![tiles on start menu](images/shell.svg)
    :::column-end:::
:::row-end:::

## <a name="inputs"></a><span data-ttu-id="1f6c8-152">Eingaben</span><span class="sxs-lookup"><span data-stu-id="1f6c8-152">Inputs</span></span>

:::row:::
    :::column:::
        UWP apps rely on smart interactions. You can design around a click interaction without having to know or define whether the click comes from a mouse, a stylus, or a tap of a finger. However, you can also design your apps for [specific input modes](../input/input-primer.md).
    :::column-end:::
    :::column:::
        ![inputs](images/inputs.svg)
    :::column-end:::
:::row-end:::

## <a name="devices"></a><span data-ttu-id="1f6c8-153">Geräte</span><span class="sxs-lookup"><span data-stu-id="1f6c8-153">Devices</span></span>

![Geräte](../layout/images/size-classes.svg)

<span data-ttu-id="1f6c8-155">Obwohl UWP Ihre App automatisch auf verschiedene Geräte skaliert, können Sie Ihre [UWP-App trotzdem für bestimmte Geräte optimieren](../devices/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f6c8-155">Similarly, while UWP automatically scales your app to different devices, you can also [optimize your UWP app for specific devices](../devices/index.md).</span></span>

## <a name="usability"></a><span data-ttu-id="1f6c8-156">Benutzerfreundlichkeit</span><span class="sxs-lookup"><span data-stu-id="1f6c8-156">Usability</span></span>

<img src="https://img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REYaAb?ver=727c">

<span data-ttu-id="1f6c8-157">Bei der Benutzerfreundlichkeit geht es darum, die App für alle Benutzer zugänglich zu machen.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-157">Last but not least, usability is about making your app's experience open to all users.</span></span> <span data-ttu-id="1f6c8-158">Jeder kann von einer wirklich umfassenden Benutzererfahrung profitieren. In [Benutzerfreundlichkeit von UWP-Apps](../usability/index.md) erfahren Sie, wie Sie Ihre App für jedermann benutzerfreundlich gestalten können.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-158">Everyone can benefit from truly inclusive user experiences - see [usability for UWP apps](../usability/index.md) to see how to make your app easy to use for everyone.</span></span>

<span data-ttu-id="1f6c8-159">Wenn Sie für ein internationales Publikum entwerfen, sollten Sie sich mit [Globalisierung und Lokalisierung](../globalizing/globalizing-portal.md) vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-159">If you're designing for international audiences, you might want to check out [Globalization and localization](../globalizing/globalizing-portal.md).</span></span>

<span data-ttu-id="1f6c8-160">Und Sie sollten [Features für Bedienungshilfen](../accessibility/accessibility-overview.md) für Benutzer mit eingeschränkter Seh-, Hör- und Bewegungsfreiheit in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-160">You might also want to consider [accessibility features](../accessibility/accessibility-overview.md) for users with limited sight, hearing, and mobility.</span></span> <span data-ttu-id="1f6c8-161">Wenn die Barrierefreiheit von Anfang an in Ihr Design integriert ist, sollte die [Umsetzung der Barrierefeiheit](../accessibility/accessibility-in-the-store.md) Ihrer App nur sehr wenig Zeit und Mühe in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-161">If accessibility is built into your design from the start, then [making your app accessible](../accessibility/accessibility-in-the-store.md) should take very little extra time and effort.</span></span>

## <a name="tools-and-design-toolkits"></a><span data-ttu-id="1f6c8-162">Tools und Design-Toolkits</span><span class="sxs-lookup"><span data-stu-id="1f6c8-162">Tools and design toolkits</span></span>

<span data-ttu-id="1f6c8-163">Da Sie nun über die grundlegenden Designfunktionen Bescheid wissen, sollten Sie die ersten Schritte beim Design Ihrer UWP-App unternehmen.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-163">Now that you know about the basic design features, how about getting started with designing your UWP app?</span></span>

<span data-ttu-id="1f6c8-164">Wir bieten eine Vielzahl von Werkzeugen zur Unterstützung Ihres Designprozesses:</span><span class="sxs-lookup"><span data-stu-id="1f6c8-164">We provide a variety of tools to help your design process:</span></span>

- <span data-ttu-id="1f6c8-165">Weitere Informationen für XD, Illustrator, Photoshop, Framer und Sketch-Toolkits sowie zusätzliche Entwicklungstools und Downloads für Schriftarten finden Sie auf der [Design-Toolkits-Seite](../downloads/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f6c8-165">See our [Design toolkits page](../downloads/index.md) for XD, Illustrator, Photoshop, Framer, and Sketch toolkits, as well as additional design tools and font downloads.</span></span>

- <span data-ttu-id="1f6c8-166">Um Ihren Computer so einzurichten, dass er das Codieren von UWP-Apps ermöglicht, lesen Sie den Artikel [Erste Schritte &gt;Vorbereiten](../../get-started/get-set-up.md).</span><span class="sxs-lookup"><span data-stu-id="1f6c8-166">To get your machine set up to write code for UWP apps, see our [Get started &gt; Get set up](../../get-started/get-set-up.md) article.</span></span>

- <span data-ttu-id="1f6c8-167">Für Anregungen zur Implementierung von Benutzeroberflächen für die UWP werfen Sie einen Blick auf unsere umfassenden [UWP-Beispiel-Apps](https://developer.microsoft.com/windows/samples).</span><span class="sxs-lookup"><span data-stu-id="1f6c8-167">For inspiration on how to implement UI for UWP, take a look at our end-to-end [sample UWP apps](https://developer.microsoft.com/windows/samples).</span></span>

## <a name="video-summary"></a><span data-ttu-id="1f6c8-168">Video-Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="1f6c8-168">Video summary</span></span>

> [!VIDEO https://channel9.msdn.com/Blogs/One-Dev-Minute/Designing-Universal-Windows-Platform-apps/player]

## <a name="next-fluent-design-system"></a><span data-ttu-id="1f6c8-169">Nächstes Thema: Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="1f6c8-169">Next: Fluent Design System</span></span>

<span data-ttu-id="1f6c8-170">Wenn Sie weitere Informationen zu der Prinzipien hinter Fluent Design (das Design-System von Microsoft) und weitere Features für Ihre UWP-App kennenlernen möchten, fahren Sie mit dem Artikel [Fluent Design-System](../fluent-design-system/index.md) fort.</span><span class="sxs-lookup"><span data-stu-id="1f6c8-170">If you'd like to learn about the principles behind Fluent Design (Microsoft's design system) and see more features you can incorporate into your UWP app, continue on to [Fluent Design System](../fluent-design-system/index.md).</span></span>

## <a name="related-articles"></a><span data-ttu-id="1f6c8-171">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="1f6c8-171">Related articles</span></span>

- [<span data-ttu-id="1f6c8-172">Was ist eine UWP-App?</span><span class="sxs-lookup"><span data-stu-id="1f6c8-172">What's a UWP app?</span></span>](../../get-started/universal-application-platform-guide.md)
- [<span data-ttu-id="1f6c8-173">Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="1f6c8-173">Fluent Design System</span></span>](../fluent-design-system/index.md)
- [<span data-ttu-id="1f6c8-174">XAML-Plattformübersicht</span><span class="sxs-lookup"><span data-stu-id="1f6c8-174">XAML platform overview</span></span>](../../xaml-platform/index.md)
