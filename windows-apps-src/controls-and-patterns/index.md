---
description: "Hier finden Sie einen Designleitfaden und Codierungsanweisungen für das Hinzufügen von Steuerelementen und Mustern zu Ihrer UWP-App. Sie finden mehr als 45leistungsstarke Steuerelemente für die Verwendung mit Ihrer App."
title: "UWP-Steuerelemente und -Muster – Entwicklung von Windows-Apps"
author: mijacobs
keywords: "UWP-Steuerelemente, Benutzeroberfläche, App-Steuerelemente"
label: Controls & patterns
template: detail.hbs
ms.author: mijacobs
ms.date: 09/09/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.assetid: ce2e611c-c419-4a14-9095-b88ac711d1b8
ms.openlocfilehash: 0946a32df990f08f00f07ad0094125709b45dcaf
ms.sourcegitcommit: 0d5b3daddb3ae74f91178c58e35cbab33854cb7f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="controls-and-patterns-for-uwp-apps"></a><span data-ttu-id="aa3b4-105">Steuerelemente und Muster für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="aa3b4-105">Controls and patterns for UWP apps</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="aa3b4-106">In der UWP-App-Entwicklung ist ein <i>Steuerelement</i> ein UI-Element, das Inhalte anzeigt oder Interaktionen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-106">In UWP app development, a <i>control</i> is a UI element that displays content or enables interaction.</span></span> <span data-ttu-id="aa3b4-107">Steuerelemente sind die Bausteine der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-107">Controls are the building blocks of the user interface.</span></span> <span data-ttu-id="aa3b4-108">Ein <i>Muster</i> ist eine Anleitung zum Kombinieren verschiedener Steuerelemente, um etwas Neues zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-108">A <i>pattern</i> is a recipe for combining several controls to make something new.</span></span>

<span data-ttu-id="aa3b4-109">Wir stellen Ihnen mehr als 45Steuerelemente bereit, angefangen bei einfachen Schaltflächen bis hin zu leistungsstarken Datensteuerelementen wie der Rasteransicht.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-109">We provide 45+ controls for you to use, ranging from simple buttons to powerful data controls like the grid view.</span></span>  <span data-ttu-id="aa3b4-110">Diese Steuerelemente sind Teil des Fluent Design-Systems und können Ihnen bei der Erstellung einer ansprechenden, skalierbaren UI helfen, die auf allen Geräten und Bildschirmgrößen großartig aussieht.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-110">These controls are a part of the Fluent Design System and can help you create a bold, scalable UI that looks great on all devices and screen sizes.</span></span> 

<span data-ttu-id="aa3b4-111">Die Artikel in diesem Abschnitt enthalten Designrichtlinien und Codierungsanweisungen für das Hinzufügen von Steuerelementen und Mustern zu Ihrer UWP-App.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-111">The articles in this section provide design guidance and coding instructions for adding controls & patterns to your UWP app.</span></span> 

## <a name="intro"></a><span data-ttu-id="aa3b4-112">Einführung</span><span class="sxs-lookup"><span data-stu-id="aa3b4-112">Intro</span></span>

<span data-ttu-id="aa3b4-113">Allgemeine Anweisungen und Codebeispiele für das Hinzufügen und Formatieren von Steuerelementen in XAML und C#.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-113">General instructions and code examples for adding and styling controls in XAML and C#.</span></span>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
   <p><b>[<span data-ttu-id="aa3b4-114">Hinzufügen von Steuerelementen und Verarbeiten von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="aa3b4-114">Add controls and handle events</span></span>](controls-and-events-intro.md)</b> <br/>
<span data-ttu-id="aa3b4-115">Es gibt 3 wichtige Schritte, die Sie ausführen müssen, um Ihrer App Steuerelemente hinzuzufügen: das Hinzufügen eines Steuerelements zu Ihrer App-UI, das Festlegen der Eigenschaften für das Steuerelement und das Hinzufügen von Code zu den Ereignishandlern des Steuerelements, sodass dieses eine Aktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-115">There are 3 key steps to adding controls to your app: Add a control to your app UI, set properties on the control, and add code to the control's event handlers so that it does something.</span></span></li>
</ul> 
</p>
  </div>
  <div class="side-by-side-content-right">
   <p><b>[<span data-ttu-id="aa3b4-116">Formatieren von Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="aa3b4-116">Styling controls</span></span>](styling-controls.md)</b> <br/>
<span data-ttu-id="aa3b4-117">Das XAML-Framework bietet zahlreiche Anpassungsmöglichkeiten für die App-Darstellung.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-117">You can customize the appearance of your apps in many ways by using the XAML framework.</span></span> <span data-ttu-id="aa3b4-118">Sie können mit Formaten die Steuerelementeigenschaften festlegen und diese Einstellungen dann für andere Steuerelemente wiederverwenden, um ein einheitliches Erscheinungsbild zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-118">Styles let you set control properties and reuse those settings for a consistent appearance across multiple controls.</span></span></p>
  </div>
</div>
</div>

## <a name="alphabetical-index"></a><span data-ttu-id="aa3b4-119">Alphabetischer Index</span><span class="sxs-lookup"><span data-stu-id="aa3b4-119">Alphabetical index</span></span> 

<span data-ttu-id="aa3b4-120">Detaillierte Informationen zu bestimmten Steuerelementen und Mustern.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-120">Detailed information about specific controls and patterns.</span></span> <span data-ttu-id="aa3b4-121">(Eine nach Funktionen sortierte Liste finden Sie unter [Index der Steuerelemente nach Funktion](controls-by-function.md).)</span><span class="sxs-lookup"><span data-stu-id="aa3b4-121">(For a list sorted by function, see [Index of controls by function](controls-by-function.md).)</span></span>

<div style="column-count: 2; column-gap: 40px; margin-top: 40px;" >
<ul style="margin-top: 0px; padding-top: 0px; list-style-type: none;">
<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-122">Feld mit automatischen Vorschlägen</span><span class="sxs-lookup"><span data-stu-id="aa3b4-122">Auto-suggest box</span></span>](auto-suggest-box.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-123">Balken</span><span class="sxs-lookup"><span data-stu-id="aa3b4-123">Bars</span></span>](app-bars.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-124">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="aa3b4-124">Buttons</span></span>](buttons.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-125">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="aa3b4-125">Checkbox</span></span> ](checkbox.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-126">Farbauswahl</span><span class="sxs-lookup"><span data-stu-id="aa3b4-126">Color picker</span></span>](color-picker.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-127">Datums- und Uhrzeitsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="aa3b4-127">Date and time controls</span></span>](date-and-time.md)</li>


<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-128">Dialogfelder und Flyouts</span><span class="sxs-lookup"><span data-stu-id="aa3b4-128">Dialogs and flyouts</span></span>](dialogs.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-129">Flip-Ansicht</span><span class="sxs-lookup"><span data-stu-id="aa3b4-129">Flip view</span></span>](flipview.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-130">Hub</span><span class="sxs-lookup"><span data-stu-id="aa3b4-130">Hub</span></span>](hub.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-131">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="aa3b4-131">Hyperlinks</span></span>](hyperlinks.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-132">Bilder und Bildpinsel</span><span class="sxs-lookup"><span data-stu-id="aa3b4-132">Images and image brushes</span></span>](images-imagebrushes.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-133">Steuerelemente für Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="aa3b4-133">Inking controls</span></span>](inking-controls.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-134">Listen</span><span class="sxs-lookup"><span data-stu-id="aa3b4-134">Lists</span></span>](lists.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-135">Kartensteuerelement</span><span class="sxs-lookup"><span data-stu-id="aa3b4-135">Map control</span></span>](../maps-and-location/controls-map.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-136">Master/Details</span><span class="sxs-lookup"><span data-stu-id="aa3b4-136">Master/details</span></span>](master-details.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-137">Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="aa3b4-137">Media playback</span></span>](media-playback.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-138">Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="aa3b4-138">Menus and context menus</span></span>](menus.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-139">Navigationsansicht</span><span class="sxs-lookup"><span data-stu-id="aa3b4-139">Nav view</span></span>](navigationview.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-140">Bild der Person</span><span class="sxs-lookup"><span data-stu-id="aa3b4-140">Person picture</span></span>](person-picture.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-141">Statussteuerelemente</span><span class="sxs-lookup"><span data-stu-id="aa3b4-141">Progress controls</span></span>](progress-controls.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-142">Optionsschaltfläche</span><span class="sxs-lookup"><span data-stu-id="aa3b4-142">Radio button</span></span>](radio-button.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-143">Bewertungssteuerelement</span><span class="sxs-lookup"><span data-stu-id="aa3b4-143">Rating control</span></span>](rating.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-144">Steuerelemente für Bildlauf und Schwenken</span><span class="sxs-lookup"><span data-stu-id="aa3b4-144">Scrolling and panning controls</span></span>](scroll-controls.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-145">Suche</span><span class="sxs-lookup"><span data-stu-id="aa3b4-145">Search</span></span>](search.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-146">Semantischer Zoom</span><span class="sxs-lookup"><span data-stu-id="aa3b4-146">Semantic zoom</span></span>](semantic-zoom.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-147">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="aa3b4-147">Slider</span></span>](slider.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-148">Geteilte Ansicht</span><span class="sxs-lookup"><span data-stu-id="aa3b4-148">Split view</span></span>](split-view.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-149">Registerkarten und Pivots</span><span class="sxs-lookup"><span data-stu-id="aa3b4-149">Tabs and pivots</span></span>](tabs-pivot.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-150">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="aa3b4-150">Text controls</span></span>](text-controls.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-151">Kacheln, Signale und Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="aa3b4-151">Tiles, badges, and notifications</span></span>](tiles-badges-notifications.md)</li>


<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-152">Umschalten</span><span class="sxs-lookup"><span data-stu-id="aa3b4-152">Toggle</span></span>](toggles.md)</li>
<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-153">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="aa3b4-153">Tooltips</span></span>](tooltips.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-154">Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="aa3b4-154">Tree view</span></span>](tree-view.md)</li>

<li style="list-style-type: none;">[<span data-ttu-id="aa3b4-155">Webansicht</span><span class="sxs-lookup"><span data-stu-id="aa3b4-155">Web view</span></span>](web-view.md)</li>
</ul>
</div>

## <a name="additional-controls"></a><span data-ttu-id="aa3b4-156">Zusätzliche Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="aa3b4-156">Additional controls</span></span>

<span data-ttu-id="aa3b4-157">Zusätzliche Steuerelemente für die UWP-Entwicklung werden von Unternehmen wie [Telerik](http://www.telerik.com/), [SyncFusion](https://www.syncfusion.com/products/uwp), [DevExpress](https://www.devexpress.com/Products/NET/Controls/Win10Apps/), [Infragistics](http://www.infragistics.com/products/universal-windows-platform), [ComponentOne](https://www.componentone.com/Studio/Platform/UWP) und [ActiPro](http://www.actiprosoftware.com/products/controls/universal) bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-157">Additional controls for UWP development are available from companies such as [Telerik](http://www.telerik.com/), [SyncFusion](https://www.syncfusion.com/products/uwp), [DevExpress](https://www.devexpress.com/Products/NET/Controls/Win10Apps/), [Infragistics](http://www.infragistics.com/products/universal-windows-platform), [ComponentOne](https://www.componentone.com/Studio/Platform/UWP), and [ActiPro](http://www.actiprosoftware.com/products/controls/universal).</span></span> <span data-ttu-id="aa3b4-158">Diese Steuerelemente bieten zusätzliche Unterstützung für Unternehmen und .NET-Entwickler, indem sie die Steuerelemente des Standardsystem mit benutzerdefinierten Steuerelementen und Diensten erweitern.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-158">These controls provide additional support for enterprise and .NET developers by augmenting the standard system controls with custom controls and services.</span></span>  

<span data-ttu-id="aa3b4-159">Wenn Sie mehr über diese Steuerelemente erfahren möchten, sehen Sie sich das Beispiel [Customer Orders Database](https://github.com/Microsoft/Windows-appsample-customers-orders-database) in GitHub an.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-159">If you're interested in learning more about these controls, check out the [Customer orders database](https://github.com/Microsoft/Windows-appsample-customers-orders-database) sample on GitHub.</span></span> <span data-ttu-id="aa3b4-160">In diesem Beispiel werden die Steuerelemente Datenrasten und Dateneingabe von Telerik verwendet, die Teil der UI für die UWP-Suite sind.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-160">This sample makes use of the data grid control and data entry validation from Telerik, which is part of their UI for UWP suite.</span></span> <span data-ttu-id="aa3b4-161">Die UI für die UWP-Suite besteht aus einer Sammlung von über 20 Steuerelementen, die als Open Source-Projekt über die .NET-Foundation verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="aa3b4-161">The UI for UWP suite is a collection of over 20 controls that is available as an open source project through the .NET foundation.</span></span>
