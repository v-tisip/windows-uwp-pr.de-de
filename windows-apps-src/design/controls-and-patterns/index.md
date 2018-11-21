---
description: Hier finden Sie einen Designleitfaden und Codierungsanweisungen für das Hinzufügen von Steuerelementen und Mustern zu Ihrer UWP-App. Sie finden mehr als 45leistungsstarke Steuerelemente für die Verwendung mit Ihrer App.
title: UWP-Steuerelemente und -Muster – Entwicklung von Windows-Apps
author: mijacobs
keywords: UWP-Steuerelemente, Benutzeroberfläche, App-Steuerelemente
label: Controls & patterns
template: detail.hbs
ms.author: mijacobs
ms.date: 11/16/2017
ms.topic: article
ms.assetid: ce2e611c-c419-4a14-9095-b88ac711d1b8
ms.localizationpriority: medium
ms.openlocfilehash: e28d557280ab253a09d5697f369c694e490d3c7d
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7430919"
---
# <a name="controls-and-patterns-for-uwp-apps"></a><span data-ttu-id="43a0e-105">Steuerelemente und Muster für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="43a0e-105">Controls and patterns for UWP apps</span></span>
 

<span data-ttu-id="43a0e-106">In der UWP-App-Entwicklung ist ein <i>Steuerelement</i> ein UI-Element, das Inhalte anzeigt oder Interaktionen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="43a0e-106">In UWP app development, a <i>control</i> is a UI element that displays content or enables interaction.</span></span> <span data-ttu-id="43a0e-107">Steuerelemente sind die Bausteine der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="43a0e-107">Controls are the building blocks of the user interface.</span></span> <span data-ttu-id="43a0e-108">Ein <i>Muster</i> ist eine Anleitung zum Kombinieren verschiedener Steuerelemente, um etwas Neues zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="43a0e-108">A <i>pattern</i> is a recipe for combining several controls to make something new.</span></span>

<span data-ttu-id="43a0e-109">Wir stellen Ihnen mehr als 45Steuerelemente bereit, angefangen bei einfachen Schaltflächen bis hin zu leistungsstarken Datensteuerelementen wie der Rasteransicht.</span><span class="sxs-lookup"><span data-stu-id="43a0e-109">We provide 45+ controls for you to use, ranging from simple buttons to powerful data controls like the grid view.</span></span>  <span data-ttu-id="43a0e-110">Diese Steuerelemente sind Teil des Fluent Design-Systems und können Ihnen bei der Erstellung einer ansprechenden, skalierbaren UI helfen, die auf allen Geräten und Bildschirmgrößen großartig aussieht.</span><span class="sxs-lookup"><span data-stu-id="43a0e-110">These controls are a part of the Fluent Design System and can help you create a bold, scalable UI that looks great on all devices and screen sizes.</span></span> 

<span data-ttu-id="43a0e-111">Die Artikel in diesem Abschnitt enthalten Designrichtlinien und Codierungsanweisungen für das Hinzufügen von Steuerelementen und Mustern zu Ihrer UWP-App.</span><span class="sxs-lookup"><span data-stu-id="43a0e-111">The articles in this section provide design guidance and coding instructions for adding controls & patterns to your UWP app.</span></span> 

## <a name="intro"></a><span data-ttu-id="43a0e-112">Einführung</span><span class="sxs-lookup"><span data-stu-id="43a0e-112">Intro</span></span>

<span data-ttu-id="43a0e-113">Allgemeine Anweisungen und Codebeispiele für das Hinzufügen und Formatieren von Steuerelementen in XAML und C#.</span><span class="sxs-lookup"><span data-stu-id="43a0e-113">General instructions and code examples for adding and styling controls in XAML and C#.</span></span>

:::row:::
    :::column:::
      <p><b><a href="controls-and-events-intro.md"><span data-ttu-id="43a0e-114">Hinzufügen von Steuerelementen und Verarbeiten von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="43a0e-114">Add controls and handle events</span></span></a></b> <br/>
<span data-ttu-id="43a0e-115">Es gibt 3 wichtige Schritte, die Sie ausführen müssen, um Ihrer App Steuerelemente hinzuzufügen: das Hinzufügen eines Steuerelements zu Ihrer App-UI, das Festlegen der Eigenschaften für das Steuerelement und das Hinzufügen von Code zu den Ereignishandlern des Steuerelements, sodass dieses eine Aktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="43a0e-115">There are 3 key steps to adding controls to your app: Add a control to your app UI, set properties on the control, and add code to the control's event handlers so that it does something.</span></span></p>
    :::column-end:::
    :::column:::
      <p><b><a href="xaml-styles.md"><span data-ttu-id="43a0e-116">Formatieren von Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="43a0e-116">Styling controls</span></span></a></b> <br/>
<span data-ttu-id="43a0e-117">Das XAML-Framework bietet zahlreiche Anpassungsmöglichkeiten für die App-Darstellung.</span><span class="sxs-lookup"><span data-stu-id="43a0e-117">You can customize the appearance of your apps in many ways by using the XAML framework.</span></span> <span data-ttu-id="43a0e-118">Sie können mit Formaten die Steuerelementeigenschaften festlegen und diese Einstellungen dann für andere Steuerelemente wiederverwenden, um ein einheitliches Erscheinungsbild zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="43a0e-118">Styles let you set control properties and reuse those settings for a consistent appearance across multiple controls.</span></span></p>
    :::column-end:::
:::row-end:::

## <a name="get-the-windows-ui-library"></a><span data-ttu-id="43a0e-119">Abrufen der Windows-UI-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="43a0e-119">Get the Windows UI Library</span></span>
<span data-ttu-id="43a0e-120">Einige Steuerelemente sind nur verfügbar, in der Windows-UI-Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="43a0e-120">Some controls are only available in the Windows UI Library.</span></span> <span data-ttu-id="43a0e-121">Um es zu erhalten, finden Sie in der [Windows-UI-Bibliothek Übersicht und Installation Anweisungen](/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="43a0e-121">To get it, see the [Windows UI Library overview and installation instructions](/uwp/toolkits/winui/).</span></span>

## <a name="alphabetical-index"></a><span data-ttu-id="43a0e-122">Alphabetischer Index</span><span class="sxs-lookup"><span data-stu-id="43a0e-122">Alphabetical index</span></span> 

<span data-ttu-id="43a0e-123">Detaillierte Informationen zu bestimmten Steuerelementen und Mustern.</span><span class="sxs-lookup"><span data-stu-id="43a0e-123">Detailed information about specific controls and patterns.</span></span> <span data-ttu-id="43a0e-124">(Eine nach Funktionen sortierte Liste finden Sie unter <a href="controls-by-function.md">Index der Steuerelemente nach Funktion</a>.)</span><span class="sxs-lookup"><span data-stu-id="43a0e-124">(For a list sorted by function, see <a href="controls-by-function.md">Index of controls by function</a>.)</span></span>

<div style="column-count: 2; column-gap: 40px; margin-top: 40px;" >
<ul style="margin-top: 0px; padding-top: 0px; list-style-type: none;">
<li style="list-style-type: none;"><a href="auto-suggest-box.md"><span data-ttu-id="43a0e-125">Feld mit automatischen Vorschlägen</span><span class="sxs-lookup"><span data-stu-id="43a0e-125">Auto-suggest box</span></span></a></li>

<li style="list-style-type: none;"><a href="app-bars.md"><span data-ttu-id="43a0e-126">Balken</span><span class="sxs-lookup"><span data-stu-id="43a0e-126">Bars</span></span></a></li>

<li style="list-style-type: none;"><a href="buttons.md"><span data-ttu-id="43a0e-127">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="43a0e-127">Buttons</span></span></a></li>

<li style="list-style-type: none;"><a href="checkbox.md"><span data-ttu-id="43a0e-128">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="43a0e-128">Checkbox</span></span> </a></li>

<li style="list-style-type: none;"><a href="color-picker.md"><span data-ttu-id="43a0e-129">Farbwähler</span><span class="sxs-lookup"><span data-stu-id="43a0e-129">Color picker</span></span></a></li>

<li style="list-style-type: none;"><a href="contact-card.md"><span data-ttu-id="43a0e-130">Visitenkarte</span><span class="sxs-lookup"><span data-stu-id="43a0e-130">Contact card</span></span></a></li>

<li style="list-style-type: none;"><a href="date-and-time.md"><span data-ttu-id="43a0e-131">Datums- und Uhrzeitsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="43a0e-131">Date and time controls</span></span></a></li>

<li style="list-style-type: none;"><a href="dialogs-and-flyouts/index.md"><span data-ttu-id="43a0e-132">Dialogfelder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="43a0e-132">Dialogs and flyouts</span></span></a></li>

<li style="list-style-type: none;"><a href="flipview.md"><span data-ttu-id="43a0e-133">Flip-Ansicht</span><span class="sxs-lookup"><span data-stu-id="43a0e-133">Flip view</span></span></a></li>

<li style="list-style-type: none;"><a href="forms.md"><span data-ttu-id="43a0e-134">Formulare</span><span class="sxs-lookup"><span data-stu-id="43a0e-134">Forms</span></span></a></li>

<li style="list-style-type: none;"><a href="hub.md"><span data-ttu-id="43a0e-135">Hub</span><span class="sxs-lookup"><span data-stu-id="43a0e-135">Hub</span></span></a></li>

<li style="list-style-type: none;"><a href="hyperlinks.md"><span data-ttu-id="43a0e-136">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="43a0e-136">Hyperlinks</span></span></a></li>

<li style="list-style-type: none;"><a href="images-imagebrushes.md"><span data-ttu-id="43a0e-137">Bilder und Bildpinsel</span><span class="sxs-lookup"><span data-stu-id="43a0e-137">Images and image brushes</span></span></a></li>

<li style="list-style-type: none;"><a href="inking-controls.md"><span data-ttu-id="43a0e-138">Steuerelemente für Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="43a0e-138">Inking controls</span></span></a></li>

<li style="list-style-type: none;"><a href="lists.md"><span data-ttu-id="43a0e-139">Listen</span><span class="sxs-lookup"><span data-stu-id="43a0e-139">Lists</span></span></a></li>

<li style="list-style-type: none;"><a href="../../maps-and-location/controls-map.md"><span data-ttu-id="43a0e-140">Kartensteuerelement</span><span class="sxs-lookup"><span data-stu-id="43a0e-140">Map control</span></span></a></li>

<li style="list-style-type: none;"><a href="master-details.md"><span data-ttu-id="43a0e-141">Master/Details</span><span class="sxs-lookup"><span data-stu-id="43a0e-141">Master/details</span></span></a></li>

<li style="list-style-type: none;"><a href="media-playback.md"><span data-ttu-id="43a0e-142">Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="43a0e-142">Media playback</span></span></a></li>

<li style="list-style-type: none;"><a href="menus.md"><span data-ttu-id="43a0e-143">Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="43a0e-143">Menus and context menus</span></span></a></li>

<li style="list-style-type: none;"><a href="navigationview.md"><span data-ttu-id="43a0e-144">Navigationsansicht</span><span class="sxs-lookup"><span data-stu-id="43a0e-144">Navigation view</span></span></a></li>

<li style="list-style-type: none;"><a href="person-picture.md"><span data-ttu-id="43a0e-145">Bild einer Person</span><span class="sxs-lookup"><span data-stu-id="43a0e-145">Person picture</span></span></a></li>

<li style="list-style-type: none;"><a href="pivot.md"><span data-ttu-id="43a0e-146">Pivot</span><span class="sxs-lookup"><span data-stu-id="43a0e-146">Pivot</span></span></a></li>

<li style="list-style-type: none;"><a href="progress-controls.md"><span data-ttu-id="43a0e-147">Statussteuerelemente</span><span class="sxs-lookup"><span data-stu-id="43a0e-147">Progress controls</span></span></a></li>

<li style="list-style-type: none;"><a href="radio-button.md"><span data-ttu-id="43a0e-148">Optionsschaltfläche</span><span class="sxs-lookup"><span data-stu-id="43a0e-148">Radio button</span></span></a></li>

<li style="list-style-type: none;"><a href="rating.md"><span data-ttu-id="43a0e-149">Bewertungssteuerelement</span><span class="sxs-lookup"><span data-stu-id="43a0e-149">Rating control</span></span></a></li>

<li style="list-style-type: none;"><a href="scroll-controls.md"><span data-ttu-id="43a0e-150">Steuerelemente für Bildlauf und Schwenken</span><span class="sxs-lookup"><span data-stu-id="43a0e-150">Scrolling and panning controls</span></span></a></li>

<li style="list-style-type: none;"><a href="search.md"><span data-ttu-id="43a0e-151">Suche</span><span class="sxs-lookup"><span data-stu-id="43a0e-151">Search</span></span></a></li>

<li style="list-style-type: none;"><a href="semantic-zoom.md"><span data-ttu-id="43a0e-152">Semantischer Zoom</span><span class="sxs-lookup"><span data-stu-id="43a0e-152">Semantic zoom</span></span></a></li>

<li style="list-style-type: none;"><a href="shapes.md"><span data-ttu-id="43a0e-153">Formen</span><span class="sxs-lookup"><span data-stu-id="43a0e-153">Shapes</span></span></a></li>

<li style="list-style-type: none;"><a href="slider.md"><span data-ttu-id="43a0e-154">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="43a0e-154">Slider</span></span></a></li>

<li style="list-style-type: none;"><a href="split-view.md"><span data-ttu-id="43a0e-155">Geteilte Ansicht</span><span class="sxs-lookup"><span data-stu-id="43a0e-155">Split view</span></span></a></li>

<li style="list-style-type: none;"><a href="text-controls.md"><span data-ttu-id="43a0e-156">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="43a0e-156">Text controls</span></span></a></li>


<li style="list-style-type: none;"><a href="toggles.md"><span data-ttu-id="43a0e-157">Umschalten</span><span class="sxs-lookup"><span data-stu-id="43a0e-157">Toggle</span></span></a></li>
<li style="list-style-type: none;"><a href="tooltips.md"><span data-ttu-id="43a0e-158">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="43a0e-158">Tooltips</span></span></a></li>

<li style="list-style-type: none;"><a href="tree-view.md"><span data-ttu-id="43a0e-159">Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="43a0e-159">Tree view</span></span></a></li>

<li style="list-style-type: none;"><a href="web-view.md"><span data-ttu-id="43a0e-160">Webansicht</span><span class="sxs-lookup"><span data-stu-id="43a0e-160">Web view</span></span></a></li>
</ul>
</div>

## <a name="xaml-controls-gallery"></a><span data-ttu-id="43a0e-161">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="43a0e-161">XAML Controls Gallery</span></span>

<span data-ttu-id="43a0e-162">Rufen Sie die _XAML-Steuerelementekatalog_-App aus dem Microsoft Store ab, um diese Steuerelemente und das Fluent Design-System in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="43a0e-162">Get the _XAML Controls Gallery_ app from the Microsoft Store to see these controls and the Fluent Design System in action.</span></span> <span data-ttu-id="43a0e-163">Die App ist eine interaktive Ergänzung zu dieser Website.</span><span class="sxs-lookup"><span data-stu-id="43a0e-163">The app is an interactive companion to this website.</span></span> <span data-ttu-id="43a0e-164">Wenn Sie sie installiert haben, können Sie Links auf einzelnen Steuerungsseiten verwenden, um die App zu starten und das Steuerelement in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="43a0e-164">When you have it installed, you can use links on individual control pages to launch the app and see the control in action.</span></span>

<a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="43a0e-165">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="43a0e-165">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a>

<a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="43a0e-166">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="43a0e-166">Get the source code (GitHub)</span></span></a>

<img src="images/xaml-controls-gallery.png" alt="XAML Controls Gallery screen" />

## <a name="additional-controls"></a><span data-ttu-id="43a0e-167">Zusätzliche Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="43a0e-167">Additional controls</span></span>

<span data-ttu-id="43a0e-168">Zusätzliche Steuerelemente für die UWP-Entwicklung werden von Unternehmen wie <a href="http://www.telerik.com/">Telerik</a>, <a href="https://www.syncfusion.com/products/uwp">SyncFusion</a>, <a href="https://www.devexpress.com/Products/NET/Controls/Win10Apps/">DevExpress</a>, <a href="http://www.infragistics.com/products/universal-windows-platform">Infragistics</a>, <a href="https://www.componentone.com/Studio/Platform/UWP">ComponentOne</a> und <a href="http://www.actiprosoftware.com/products/controls/universal">ActiPro</a> bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="43a0e-168">Additional controls for UWP development are available from companies such as <a href="http://www.telerik.com/">Telerik</a>, <a href="https://www.syncfusion.com/products/uwp">SyncFusion</a>, <a href="https://www.devexpress.com/Products/NET/Controls/Win10Apps/">DevExpress</a>, <a href="http://www.infragistics.com/products/universal-windows-platform">Infragistics</a>, <a href="https://www.componentone.com/Studio/Platform/UWP">ComponentOne</a>, and <a href="http://www.actiprosoftware.com/products/controls/universal">ActiPro</a>.</span></span> <span data-ttu-id="43a0e-169">Diese Steuerelemente bieten zusätzliche Unterstützung für Unternehmen und .NET-Entwickler, indem sie die Steuerelemente des Standardsystem mit benutzerdefinierten Steuerelementen und Diensten erweitern.</span><span class="sxs-lookup"><span data-stu-id="43a0e-169">These controls provide additional support for enterprise and .NET developers by augmenting the standard system controls with custom controls and services.</span></span>  

<span data-ttu-id="43a0e-170">Wenn Sie mehr über diese Steuerelemente erfahren möchten, sehen Sie sich das Beispiel <a href="https://github.com/Microsoft/Windows-appsample-customers-orders-database">Customer Orders Database</a> in GitHub an.</span><span class="sxs-lookup"><span data-stu-id="43a0e-170">If you're interested in learning more about these controls, check out the <a href="https://github.com/Microsoft/Windows-appsample-customers-orders-database">Customer orders database</a> sample on GitHub.</span></span> <span data-ttu-id="43a0e-171">In diesem Beispiel werden die Steuerelemente Datenrasten und Dateneingabe von Telerik verwendet, die Teil der UI für die UWP-Suite sind.</span><span class="sxs-lookup"><span data-stu-id="43a0e-171">This sample makes use of the data grid control and data entry validation from Telerik, which is part of their UI for UWP suite.</span></span> <span data-ttu-id="43a0e-172">Die UI für die UWP-Suite besteht aus einer Sammlung von über 20 Steuerelementen, die als Open Source-Projekt über die .NET-Foundation verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="43a0e-172">The UI for UWP suite is a collection of over 20 controls that is available as an open source project through the .NET foundation.</span></span>
