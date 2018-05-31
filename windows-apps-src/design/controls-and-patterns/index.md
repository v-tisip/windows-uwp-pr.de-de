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
ms.prod: windows
ms.technology: uwp
ms.assetid: ce2e611c-c419-4a14-9095-b88ac711d1b8
ms.localizationpriority: medium
ms.openlocfilehash: ad1ba185e70a34a4e7bfed0609412ac7bbca2d4a
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
ms.locfileid: "1653689"
---
# <a name="controls-and-patterns-for-uwp-apps"></a><span data-ttu-id="f28f7-105">Steuerelemente und Muster für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="f28f7-105">Controls and patterns for UWP apps</span></span>
 

<span data-ttu-id="f28f7-106">In der UWP-App-Entwicklung ist ein <i>Steuerelement</i> ein UI-Element, das Inhalte anzeigt oder Interaktionen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="f28f7-106">In UWP app development, a <i>control</i> is a UI element that displays content or enables interaction.</span></span> <span data-ttu-id="f28f7-107">Steuerelemente sind die Bausteine der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="f28f7-107">Controls are the building blocks of the user interface.</span></span> <span data-ttu-id="f28f7-108">Ein <i>Muster</i> ist eine Anleitung zum Kombinieren verschiedener Steuerelemente, um etwas Neues zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f28f7-108">A <i>pattern</i> is a recipe for combining several controls to make something new.</span></span>

<span data-ttu-id="f28f7-109">Wir stellen Ihnen mehr als 45Steuerelemente bereit, angefangen bei einfachen Schaltflächen bis hin zu leistungsstarken Datensteuerelementen wie der Rasteransicht.</span><span class="sxs-lookup"><span data-stu-id="f28f7-109">We provide 45+ controls for you to use, ranging from simple buttons to powerful data controls like the grid view.</span></span>  <span data-ttu-id="f28f7-110">Diese Steuerelemente sind Teil des Fluent Design-Systems und können Ihnen bei der Erstellung einer ansprechenden, skalierbaren UI helfen, die auf allen Geräten und Bildschirmgrößen großartig aussieht.</span><span class="sxs-lookup"><span data-stu-id="f28f7-110">These controls are a part of the Fluent Design System and can help you create a bold, scalable UI that looks great on all devices and screen sizes.</span></span> 

<span data-ttu-id="f28f7-111">Die Artikel in diesem Abschnitt enthalten Designrichtlinien und Codierungsanweisungen für das Hinzufügen von Steuerelementen und Mustern zu Ihrer UWP-App.</span><span class="sxs-lookup"><span data-stu-id="f28f7-111">The articles in this section provide design guidance and coding instructions for adding controls & patterns to your UWP app.</span></span> 

## <a name="intro"></a><span data-ttu-id="f28f7-112">Einführung</span><span class="sxs-lookup"><span data-stu-id="f28f7-112">Intro</span></span>

<span data-ttu-id="f28f7-113">Allgemeine Anweisungen und Codebeispiele für das Hinzufügen und Formatieren von Steuerelementen in XAML und C#.</span><span class="sxs-lookup"><span data-stu-id="f28f7-113">General instructions and code examples for adding and styling controls in XAML and C#.</span></span>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
   <p><b><a href="controls-and-events-intro.md"><span data-ttu-id="f28f7-114">Hinzufügen von Steuerelementen und Verarbeiten von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="f28f7-114">Add controls and handle events</span></span></a></b> <br/>
<span data-ttu-id="f28f7-115">Es gibt 3 wichtige Schritte, die Sie ausführen müssen, um Ihrer App Steuerelemente hinzuzufügen: das Hinzufügen eines Steuerelements zu Ihrer App-UI, das Festlegen der Eigenschaften für das Steuerelement und das Hinzufügen von Code zu den Ereignishandlern des Steuerelements, sodass dieses eine Aktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="f28f7-115">There are 3 key steps to adding controls to your app: Add a control to your app UI, set properties on the control, and add code to the control's event handlers so that it does something.</span></span></li>
</ul> 
</p>
  </div>
  <div class="side-by-side-content-right">
   <p><b><a href="xaml-styles.md"><span data-ttu-id="f28f7-116">Formatieren von Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="f28f7-116">Styling controls</span></span></a></b> <br/>
<span data-ttu-id="f28f7-117">Das XAML-Framework bietet zahlreiche Anpassungsmöglichkeiten für die App-Darstellung.</span><span class="sxs-lookup"><span data-stu-id="f28f7-117">You can customize the appearance of your apps in many ways by using the XAML framework.</span></span> <span data-ttu-id="f28f7-118">Sie können mit Formaten die Steuerelementeigenschaften festlegen und diese Einstellungen dann für andere Steuerelemente wiederverwenden, um ein einheitliches Erscheinungsbild zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="f28f7-118">Styles let you set control properties and reuse those settings for a consistent appearance across multiple controls.</span></span></p>
  </div>
</div>
</div>

## <a name="alphabetical-index"></a><span data-ttu-id="f28f7-119">Alphabetischer Index</span><span class="sxs-lookup"><span data-stu-id="f28f7-119">Alphabetical index</span></span> 

<span data-ttu-id="f28f7-120">Detaillierte Informationen zu bestimmten Steuerelementen und Mustern.</span><span class="sxs-lookup"><span data-stu-id="f28f7-120">Detailed information about specific controls and patterns.</span></span> <span data-ttu-id="f28f7-121">(Eine nach Funktionen sortierte Liste finden Sie unter <a href="controls-by-function.md">Index der Steuerelemente nach Funktion</a>.)</span><span class="sxs-lookup"><span data-stu-id="f28f7-121">(For a list sorted by function, see <a href="controls-by-function.md">Index of controls by function</a>.)</span></span>

<div style="column-count: 2; column-gap: 40px; margin-top: 40px;" >
<ul style="margin-top: 0px; padding-top: 0px; list-style-type: none;">
<li style="list-style-type: none;"><a href="auto-suggest-box.md"><span data-ttu-id="f28f7-122">Feld mit automatischen Vorschlägen</span><span class="sxs-lookup"><span data-stu-id="f28f7-122">Auto-suggest box</span></span></a></li>

<li style="list-style-type: none;"><a href="app-bars.md"><span data-ttu-id="f28f7-123">Balken</span><span class="sxs-lookup"><span data-stu-id="f28f7-123">Bars</span></span></a></li>

<li style="list-style-type: none;"><a href="buttons.md"><span data-ttu-id="f28f7-124">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="f28f7-124">Buttons</span></span></a></li>

<li style="list-style-type: none;"><a href="checkbox.md"><span data-ttu-id="f28f7-125">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="f28f7-125">Checkbox</span></span> </a></li>

<li style="list-style-type: none;"><a href="color-picker.md"><span data-ttu-id="f28f7-126">Farbwähler</span><span class="sxs-lookup"><span data-stu-id="f28f7-126">Color picker</span></span></a></li>

<li style="list-style-type: none;"><a href="contact-card.md"><span data-ttu-id="f28f7-127">Visitenkarte</span><span class="sxs-lookup"><span data-stu-id="f28f7-127">Contact card</span></span></a></li>

<li style="list-style-type: none;"><a href="date-and-time.md"><span data-ttu-id="f28f7-128">Datums- und Uhrzeitsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="f28f7-128">Date and time controls</span></span></a></li>

<li style="list-style-type: none;"><a href="dialogs.md"><span data-ttu-id="f28f7-129">Dialogfelder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="f28f7-129">Dialogs and flyouts</span></span></a></li>

<li style="list-style-type: none;"><a href="flipview.md"><span data-ttu-id="f28f7-130">Flip-Ansicht</span><span class="sxs-lookup"><span data-stu-id="f28f7-130">Flip view</span></span></a></li>

<li style="list-style-type: none;"><a href="forms.md"><span data-ttu-id="f28f7-131">Formulare</span><span class="sxs-lookup"><span data-stu-id="f28f7-131">Forms</span></span></a></li>

<li style="list-style-type: none;"><a href="hub.md"><span data-ttu-id="f28f7-132">Hub</span><span class="sxs-lookup"><span data-stu-id="f28f7-132">Hub</span></span></a></li>

<li style="list-style-type: none;"><a href="hyperlinks.md"><span data-ttu-id="f28f7-133">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="f28f7-133">Hyperlinks</span></span></a></li>

<li style="list-style-type: none;"><a href="images-imagebrushes.md"><span data-ttu-id="f28f7-134">Bilder und Bildpinsel</span><span class="sxs-lookup"><span data-stu-id="f28f7-134">Images and image brushes</span></span></a></li>

<li style="list-style-type: none;"><a href="inking-controls.md"><span data-ttu-id="f28f7-135">Steuerelemente für Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="f28f7-135">Inking controls</span></span></a></li>

<li style="list-style-type: none;"><a href="lists.md"><span data-ttu-id="f28f7-136">Listen</span><span class="sxs-lookup"><span data-stu-id="f28f7-136">Lists</span></span></a></li>

<li style="list-style-type: none;"><a href="../../maps-and-location/controls-map.md"><span data-ttu-id="f28f7-137">Kartensteuerelement</span><span class="sxs-lookup"><span data-stu-id="f28f7-137">Map control</span></span></a></li>

<li style="list-style-type: none;"><a href="master-details.md"><span data-ttu-id="f28f7-138">Master/Details</span><span class="sxs-lookup"><span data-stu-id="f28f7-138">Master/details</span></span></a></li>

<li style="list-style-type: none;"><a href="media-playback.md"><span data-ttu-id="f28f7-139">Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="f28f7-139">Media playback</span></span></a></li>

<li style="list-style-type: none;"><a href="menus.md"><span data-ttu-id="f28f7-140">Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="f28f7-140">Menus and context menus</span></span></a></li>

<li style="list-style-type: none;"><a href="navigationview.md"><span data-ttu-id="f28f7-141">Navigationsansicht</span><span class="sxs-lookup"><span data-stu-id="f28f7-141">Nav view</span></span></a></li>

<li style="list-style-type: none;"><a href="person-picture.md"><span data-ttu-id="f28f7-142">Bild der Person</span><span class="sxs-lookup"><span data-stu-id="f28f7-142">Person picture</span></span></a></li>

<li style="list-style-type: none;"><a href="progress-controls.md"><span data-ttu-id="f28f7-143">Statussteuerelemente</span><span class="sxs-lookup"><span data-stu-id="f28f7-143">Progress controls</span></span></a></li>

<li style="list-style-type: none;"><a href="radio-button.md"><span data-ttu-id="f28f7-144">Optionsschaltfläche</span><span class="sxs-lookup"><span data-stu-id="f28f7-144">Radio button</span></span></a></li>

<li style="list-style-type: none;"><a href="rating.md"><span data-ttu-id="f28f7-145">Bewertungssteuerelement</span><span class="sxs-lookup"><span data-stu-id="f28f7-145">Rating control</span></span></a></li>

<li style="list-style-type: none;"><a href="scroll-controls.md"><span data-ttu-id="f28f7-146">Steuerelemente für Bildlauf und Schwenken</span><span class="sxs-lookup"><span data-stu-id="f28f7-146">Scrolling and panning controls</span></span></a></li>

<li style="list-style-type: none;"><a href="search.md"><span data-ttu-id="f28f7-147">Suche</span><span class="sxs-lookup"><span data-stu-id="f28f7-147">Search</span></span></a></li>

<li style="list-style-type: none;"><a href="semantic-zoom.md"><span data-ttu-id="f28f7-148">Semantischer Zoom</span><span class="sxs-lookup"><span data-stu-id="f28f7-148">Semantic zoom</span></span></a></li>

<li style="list-style-type: none;"><a href="shapes.md"><span data-ttu-id="f28f7-149">Formen</span><span class="sxs-lookup"><span data-stu-id="f28f7-149">Shapes</span></span></a></li>

<li style="list-style-type: none;"><a href="slider.md"><span data-ttu-id="f28f7-150">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="f28f7-150">Slider</span></span></a></li>

<li style="list-style-type: none;"><a href="split-view.md"><span data-ttu-id="f28f7-151">Geteilte Ansicht</span><span class="sxs-lookup"><span data-stu-id="f28f7-151">Split view</span></span></a></li>

<li style="list-style-type: none;"><a href="tabs-pivot.md"><span data-ttu-id="f28f7-152">Registerkarten und Pivots</span><span class="sxs-lookup"><span data-stu-id="f28f7-152">Tabs and pivots</span></span></a></li>

<li style="list-style-type: none;"><a href="text-controls.md"><span data-ttu-id="f28f7-153">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="f28f7-153">Text controls</span></span></a></li>

<li style="list-style-type: none;"><a href="index.md"><span data-ttu-id="f28f7-154">Kacheln, Signale und Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="f28f7-154">Tiles, badges, and notifications</span></span></a></li>


<li style="list-style-type: none;"><a href="toggles.md"><span data-ttu-id="f28f7-155">Umschalten</span><span class="sxs-lookup"><span data-stu-id="f28f7-155">Toggle</span></span></a></li>
<li style="list-style-type: none;"><a href="tooltips.md"><span data-ttu-id="f28f7-156">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="f28f7-156">Tooltips</span></span></a></li>

<li style="list-style-type: none;"><a href="tree-view.md"><span data-ttu-id="f28f7-157">Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="f28f7-157">Tree view</span></span></a></li>

<li style="list-style-type: none;"><a href="web-view.md"><span data-ttu-id="f28f7-158">Webansicht</span><span class="sxs-lookup"><span data-stu-id="f28f7-158">Web view</span></span></a></li>
</ul>
</div>

## <a name="xaml-controls-gallery"></a><span data-ttu-id="f28f7-159">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="f28f7-159">XAML Controls Gallery</span></span>

<span data-ttu-id="f28f7-160">Rufen Sie die _XAML-Steuerelementekatalog_-App aus dem Microsoft Store ab, um diese Steuerelemente und das Fluent Design-System in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="f28f7-160">Get the _XAML Controls Gallery_ app from the Microsoft Store to see these controls and the Fluent Design System in action.</span></span> <span data-ttu-id="f28f7-161">Die App ist eine interaktive Ergänzung zu dieser Website.</span><span class="sxs-lookup"><span data-stu-id="f28f7-161">The app is an interactive companion to this website.</span></span> <span data-ttu-id="f28f7-162">Wenn Sie sie installiert haben, können Sie Links auf einzelnen Steuerungsseiten verwenden, um die App zu starten und das Steuerelement in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="f28f7-162">When you have it installed, you can use links on individual control pages to launch the app and see the control in action.</span></span>

<a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="f28f7-163">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="f28f7-163">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a>

<a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="f28f7-164">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="f28f7-164">Get the source code (GitHub)</span></span></a>

<img src="images/xaml-controls-gallery.png" alt="XAML Controls Gallery screen" />

## <a name="additional-controls"></a><span data-ttu-id="f28f7-165">Zusätzliche Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="f28f7-165">Additional controls</span></span>

<span data-ttu-id="f28f7-166">Zusätzliche Steuerelemente für die UWP-Entwicklung werden von Unternehmen wie <a href="http://www.telerik.com/">Telerik</a>, <a href="https://www.syncfusion.com/products/uwp">SyncFusion</a>, <a href="https://www.devexpress.com/Products/NET/Controls/Win10Apps/">DevExpress</a>, <a href="http://www.infragistics.com/products/universal-windows-platform">Infragistics</a>, <a href="https://www.componentone.com/Studio/Platform/UWP">ComponentOne</a> und <a href="http://www.actiprosoftware.com/products/controls/universal">ActiPro</a> bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f28f7-166">Additional controls for UWP development are available from companies such as <a href="http://www.telerik.com/">Telerik</a>, <a href="https://www.syncfusion.com/products/uwp">SyncFusion</a>, <a href="https://www.devexpress.com/Products/NET/Controls/Win10Apps/">DevExpress</a>, <a href="http://www.infragistics.com/products/universal-windows-platform">Infragistics</a>, <a href="https://www.componentone.com/Studio/Platform/UWP">ComponentOne</a>, and <a href="http://www.actiprosoftware.com/products/controls/universal">ActiPro</a>.</span></span> <span data-ttu-id="f28f7-167">Diese Steuerelemente bieten zusätzliche Unterstützung für Unternehmen und .NET-Entwickler, indem sie die Steuerelemente des Standardsystem mit benutzerdefinierten Steuerelementen und Diensten erweitern.</span><span class="sxs-lookup"><span data-stu-id="f28f7-167">These controls provide additional support for enterprise and .NET developers by augmenting the standard system controls with custom controls and services.</span></span>  

<span data-ttu-id="f28f7-168">Wenn Sie mehr über diese Steuerelemente erfahren möchten, sehen Sie sich das Beispiel <a href="https://github.com/Microsoft/Windows-appsample-customers-orders-database">Customer Orders Database</a> in GitHub an.</span><span class="sxs-lookup"><span data-stu-id="f28f7-168">If you're interested in learning more about these controls, check out the <a href="https://github.com/Microsoft/Windows-appsample-customers-orders-database">Customer orders database</a> sample on GitHub.</span></span> <span data-ttu-id="f28f7-169">In diesem Beispiel werden die Steuerelemente Datenrasten und Dateneingabe von Telerik verwendet, die Teil der UI für die UWP-Suite sind.</span><span class="sxs-lookup"><span data-stu-id="f28f7-169">This sample makes use of the data grid control and data entry validation from Telerik, which is part of their UI for UWP suite.</span></span> <span data-ttu-id="f28f7-170">Die UI für die UWP-Suite besteht aus einer Sammlung von über 20 Steuerelementen, die als Open Source-Projekt über die .NET-Foundation verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="f28f7-170">The UI for UWP suite is a collection of over 20 controls that is available as an open source project through the .NET foundation.</span></span>
