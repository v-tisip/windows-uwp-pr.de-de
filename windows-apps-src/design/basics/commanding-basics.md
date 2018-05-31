---
author: mijacobs
Description: In a Universal Windows Platform (UWP) app, command elements are the interactive UI elements that enable the user to perform actions, such as sending an email, deleting an item, or submitting a form.
title: Befehlsdesigngrundlagen für Apps der universellen Windows-Plattform (UWP)
ms.assetid: 1DB48285-07B7-4952-80EF-02B57D4469F2
label: Command design basics
template: detail.hbs
op-migration-status: ready
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 07b9ce7b5a57f6dc1ba202ed57e8b2d4d93e583f
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
ms.locfileid: "1654389"
---
#  <a name="command-design-basics-for-uwp-apps"></a><span data-ttu-id="74fd5-103">Befehlsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="74fd5-103">Command design basics for UWP apps</span></span>

<span data-ttu-id="74fd5-104">Bei den *Befehlselementen* in einer Universellen Windows-Plattform (UWP)-App handelt es sich um die interaktiven Benutzeroberflächenelemente, mit denen der Benutzer Aktionen durchführen kann, um beispielsweise eine E-Mail zu senden, ein Element zu löschen oder ein Formular zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="74fd5-104">In a Universal Windows Platform (UWP) app, *command elements* are interactive UI elements that enable users to perform actions, such as sending an email, deleting an item, or submitting a form.</span></span> 

<span data-ttu-id="74fd5-105">Dieser Artikel beschreibt allgemeine Befehlselemente, die von ihnen unterstützten Interaktionen und die Befehlsoberflächen für ihr Hosting.</span><span class="sxs-lookup"><span data-stu-id="74fd5-105">This article describes common command elements, the interactions they support, and the command surfaces for hosting them.</span></span>

![Befehlselemente in der Maps-App](images/maps.png)

<span data-ttu-id="74fd5-107">Oben finden Sie Beispiele für Befehlselemente in der Maps-App.</span><span class="sxs-lookup"><span data-stu-id="74fd5-107">Above, see examples of command elements in the Maps app.</span></span>

## <a name="provide-the-right-type-of-interactions"></a><span data-ttu-id="74fd5-108">Bereitstellen geeigneter Interaktionen</span><span class="sxs-lookup"><span data-stu-id="74fd5-108">Provide the right type of interactions</span></span>

<span data-ttu-id="74fd5-109">Die wichtigste Entscheidung bei der Gestaltung einer Befehlsschnittstelle ist die Wahl der möglichen Benutzeraktionen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-109">When designing a command interface, the most important decision is choosing what users should be able to do.</span></span> <span data-ttu-id="74fd5-110">Um die richtige Art Interaktionen zu planen, konzentrieren Sie sich auf Ihre App – denken Sie daran, welche Benutzererfahrungen Sie ermöglichen möchten und welche Schritte die Benutzer unternehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-110">To plan the right type of interactions, focus on your app - consider the user experiences you want to enable, and what steps users will need to take.</span></span> <span data-ttu-id="74fd5-111">Sobald Sie entscheiden, was die Benutzer erreichen sollen, können Sie ihnen die entsprechenden Werkzeuge zur Verfügung stellen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-111">Once you decide what you want users to accomplish, then you can provide them the tools to do so.</span></span>

<span data-ttu-id="74fd5-112">Einige Interaktionen für Ihre App sind:</span><span class="sxs-lookup"><span data-stu-id="74fd5-112">Some interactions you might want to provide your app include:</span></span>

- <span data-ttu-id="74fd5-113">Senden oder Übermitteln von Informationen</span><span class="sxs-lookup"><span data-stu-id="74fd5-113">Sending or submiting information</span></span> 
- <span data-ttu-id="74fd5-114">Auswählen von Einstellungen und Auswahlmöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="74fd5-114">Selecting settings and choices</span></span>
- <span data-ttu-id="74fd5-115">Suchen und Filtern von Inhalten</span><span class="sxs-lookup"><span data-stu-id="74fd5-115">Searching and filtering content</span></span>
- <span data-ttu-id="74fd5-116">Öffnen, Speichern und Löschen von Dateien</span><span class="sxs-lookup"><span data-stu-id="74fd5-116">Opening, saving, and deleting files</span></span>
- <span data-ttu-id="74fd5-117">Inhalte bearbeiten oder erstellen</span><span class="sxs-lookup"><span data-stu-id="74fd5-117">Editing or creating content</span></span>

## <a name="use-the-right-command-element-for-the-interaction"></a><span data-ttu-id="74fd5-118">Verwenden Sie das richtige Befehlselement für die Interaktion</span><span class="sxs-lookup"><span data-stu-id="74fd5-118">Use the right command element for the interaction</span></span>

<span data-ttu-id="74fd5-119">Die Verwendung der richtigen Elemente zur Befehlsinteraktionen kann den Unterschied zwischen einer intuitiven, benutzerfreundlichen App und einer schwierigen, verwirrenden App ausmachen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-119">Using the right elements to enable command interactions can make the difference between an intuitive, easy-to-use app and a difficult, confusing app.</span></span> <span data-ttu-id="74fd5-120">Die Universelle Windows-Plattform (UWP) bietet eine große Anzahl von Befehlselementen, die Sie in Ihrer App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="74fd5-120">The Universal Windows Platform (UWP) provides a large set of command elements that you can use in your app.</span></span> <span data-ttu-id="74fd5-121">Die folgende Liste enthält einige der gängigsten Steuerelemente sowie eine Zusammenfassung der jeweils möglichen Interaktionen:</span><span class="sxs-lookup"><span data-stu-id="74fd5-121">Here's a list of some of the most common controls and a summary of the interactions they can enable.</span></span>

<div class="mx-responsive-img">
<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="74fd5-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="74fd5-122">Category</span></span></th>
<th align="left"><span data-ttu-id="74fd5-123">Elemente</span><span class="sxs-lookup"><span data-stu-id="74fd5-123">Elements</span></span></th>
<th align="left"><span data-ttu-id="74fd5-124">Interaktion</span><span class="sxs-lookup"><span data-stu-id="74fd5-124">Interaction</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><b><span data-ttu-id="74fd5-125">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="74fd5-125">Buttons</span></span></b><br/><br/>
    <img src="../controls-and-patterns/images/controls/button.png" alt="button" /></td>
<td align="left"><a href="../controls-and-patterns/buttons.md"><span data-ttu-id="74fd5-126">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="74fd5-126">Button</span></span></a></td>
<td align="left"><span data-ttu-id="74fd5-127">Löst eine sofortige Aktion aus.</span><span class="sxs-lookup"><span data-stu-id="74fd5-127">Triggers an immediate action.</span></span> <span data-ttu-id="74fd5-128">Beispiele hierfür sind das Versenden einer E-Mail, das Senden von Formulardaten oder das Bestätigen einer Aktion in einem Dialog.</span><span class="sxs-lookup"><span data-stu-id="74fd5-128">Examples include sending an email, submitting form data, or confirming an action in a dialog.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="74fd5-129">Listen</span><span class="sxs-lookup"><span data-stu-id="74fd5-129">Lists</span></span><br/><br/>
    <img src="../controls-and-patterns/images/controls/combo-box-open.png" alt="drop down list" /></td>
<td align="left"><a href="../controls-and-patterns/lists.md"><span data-ttu-id="74fd5-130">Dropdownliste, Listenfeld, Listen- und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="74fd5-130">drop-down list, list box, list view and grid view</span></span></a></td>
<td align="left"><span data-ttu-id="74fd5-131">Stellt Elemente in einer interaktiven Liste oder in einem Raster dar.</span><span class="sxs-lookup"><span data-stu-id="74fd5-131">Presents items in a interactive list or a grid.</span></span> <span data-ttu-id="74fd5-132">Wird normalerweise für viele Optionen oder Anzeigeelemente verwendet.</span><span class="sxs-lookup"><span data-stu-id="74fd5-132">Usually used for many options or display items.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="74fd5-133">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="74fd5-133">Selection controls</span></span><br/><br/>
    <img src="../controls-and-patterns/images/controls/radio-button.png" alt="radio button" /></td>
<td align="left"><span data-ttu-id="74fd5-134"><a href="../controls-and-patterns/checkbox.md">Kontrollkästchen</a>, <a href="../controls-and-patterns/radio-button.md">Optionsfeld</a>, <a href="../controls-and-patterns/toggles.md">Umschalter</a></span><span class="sxs-lookup"><span data-stu-id="74fd5-134"><a href="../controls-and-patterns/checkbox.md">check box</a>, <a href="../controls-and-patterns/radio-button.md">radio button</a>, <a href="../controls-and-patterns/toggles.md">toggle switch</a></span></span></td>
<td align="left"><span data-ttu-id="74fd5-135">Ermöglicht die Auswahl einiger Optionen, z. B. beim Ausfüllen einer Umfrage oder beim Konfigurieren von App-Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-135">Lets users choose from a few options, such as when completing a survey or configuring app settings.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="74fd5-136">Datums- und Zeitauswahl</span><span class="sxs-lookup"><span data-stu-id="74fd5-136">Date and time pickers</span></span><br/><br/>
    <img src="../controls-and-patterns/images/controls/calendar-date-picker-open.png" alt="date picker" /></td>
<td align="left"><a href="../controls-and-patterns/date-and-time.md"><span data-ttu-id="74fd5-137">Kalenderdatumsauswahl, Kalenderansicht, Datumsauswahl, Zeitauswahl</span><span class="sxs-lookup"><span data-stu-id="74fd5-137">calendar date picker, calendar view, date picker, time picker</span></span></a></td>
<td align="left"><span data-ttu-id="74fd5-138">Ermöglicht die Anzeige und Änderung von Datum und Uhrzeit, z. B. beim Erstellen eines Ereignisses oder beim Einstellen eines Alarms.</span><span class="sxs-lookup"><span data-stu-id="74fd5-138">Enables users to view and modify date and time info, such as when creating an event or setting an alarm.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="74fd5-139">Textvorhersage</span><span class="sxs-lookup"><span data-stu-id="74fd5-139">Predictive text entry</span></span><br/><br/>
    <img src="../controls-and-patterns/images/controls/auto-suggest-box.png" alt="autosuggest box" /></td>
<td align="left"><a href="../controls-and-patterns/auto-suggest-box.md"><span data-ttu-id="74fd5-140">Feld mit automatischen Vorschlägen</span><span class="sxs-lookup"><span data-stu-id="74fd5-140">Auto-suggest box</span></span></a></td>
<td align="left"><span data-ttu-id="74fd5-141">Bietet Vorschläge als Benutzertyp, z. B. bei der Eingabe von Daten oder beim Ausführen von Abfragen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-141">Provides suggestions as users type, such as when entering data or performing queries.</span></span></td>
</tr>
</tbody>
</table>
</div>

<span data-ttu-id="74fd5-142">Eine vollständige Liste finden Sie unter [Steuerelemente und UI-Elemente](https://dev.windows.com/design/controls-patterns).</span><span class="sxs-lookup"><span data-stu-id="74fd5-142">For a complete list, see [Controls and UI elements](https://dev.windows.com/design/controls-patterns)</span></span>

##  <a name="place-commands-on-the-right-surface"></a><span data-ttu-id="74fd5-143">Platzieren von Befehlen auf der passenden Oberfläche</span><span class="sxs-lookup"><span data-stu-id="74fd5-143">Place commands on the right surface</span></span>
<span data-ttu-id="74fd5-144">Sie können Befehlselemente auf einer Reihe von Oberflächen in Ihrer App platzieren, einschließlich der App-Canvas oder spezieller Befehlscontainer, wie Befehlsleisten, Menüs, Dialoge und Flyouts.</span><span class="sxs-lookup"><span data-stu-id="74fd5-144">You can place command elements on a number of surfaces in your app, including the app canvas or special command containers, such as command bars, menus, dialogs, and flyouts.</span></span>

<span data-ttu-id="74fd5-145">Beachten Sie, dass Sie den Benutzern möglichst erlauben sollten, Inhalte direkt zu manipulieren, anstatt Befehle zu verwenden, die auf den Inhalt wirken.</span><span class="sxs-lookup"><span data-stu-id="74fd5-145">Note that, whenever possible, you should allow users to manipulate content directly rather than use commands that act on the content.</span></span> <span data-ttu-id="74fd5-146">Beispielsweise können Benutzer Listen durch Ziehen und Ablegen von Listenelementen neu anordnen, anstatt die Befehlsschaltflächen nach oben und unten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="74fd5-146">For example, allow users to rearrange lists by dragging and dropping list items, rather than using up and down command buttons.</span></span>
  
<span data-ttu-id="74fd5-147">Wenn Benutzer Inhalte nicht direkt manipulieren können, platzieren Sie Befehlselemente auf einer Befehlsoberfläche in Ihrer App:</span><span class="sxs-lookup"><span data-stu-id="74fd5-147">Otherwise, if users can't manipulate content directly, then place command elements on a command surface in your app:</span></span>

<div class="mx-responsive-img">
<table class="uwpd-top-aligned-table">

<tr class="header">
<th align="left"><span data-ttu-id="74fd5-148">Oberfläche</span><span class="sxs-lookup"><span data-stu-id="74fd5-148">Surface</span></span></th>
<th align="left"><span data-ttu-id="74fd5-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74fd5-149">Description</span></span></th>
<th align="left"><span data-ttu-id="74fd5-150">Beispiel</span><span class="sxs-lookup"><span data-stu-id="74fd5-150">Example</span></span></th>
</tr>

<tr class="odd">
<td align="left" style="vertical-align: top"><span data-ttu-id="74fd5-151">App-Canvas (Inhaltsbereich)</span><span class="sxs-lookup"><span data-stu-id="74fd5-151">App canvas (content area)</span></span>
<p><img src="images/content-area.png" alt="The content area of an app" /></p></td>

<td align="left" style="vertical-align: top;"><span data-ttu-id="74fd5-152">Wenn ein Befehl ständig für Kernszenarien benötigt wird, legen Sie ihn auf die Canvas.</span><span class="sxs-lookup"><span data-stu-id="74fd5-152">If a command is constantly needed for users to complete core scenarios, put it on the canvas.</span></span> <span data-ttu-id="74fd5-153">Da Sie Befehle in der Nähe von (oder auf) Objekten platzieren können, die durch den Befehl beeinflusst werden, sind auf der Canvas platzierte Befehle besonders komfortabel und intuitiv.</span><span class="sxs-lookup"><span data-stu-id="74fd5-153">Because you can put commands near (or on) the objects they affect, putting commands on the canvas makes them easy and obvious to use.</span></span>
<p><span data-ttu-id="74fd5-154">Wählen Sie die Befehle für die Canvas aber mit Bedacht.</span><span class="sxs-lookup"><span data-stu-id="74fd5-154">However, choose the commands you put on the canvas carefully.</span></span> <span data-ttu-id="74fd5-155">Wenn Sie zu viele Befehle auf der App-Canvas positionieren, geht wertvoller Platz und die Übersichtlichkeit für den Benutzer verloren.</span><span class="sxs-lookup"><span data-stu-id="74fd5-155">Too many commands on the app canvas take up valuable screen space and can overwhelm the user.</span></span> <span data-ttu-id="74fd5-156">Wenn der Befehl nicht häufig verwendet wird, sollten Sie ihn in eine andere Befehlsoberfläche einfügen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-156">If the command won't be frequently used, consider putting it in another command surface.</span></span></p> 
</td><td>
<span data-ttu-id="74fd5-157">Ein Vorschlagsfeld auf der Maps-App-Canvas.</span><span class="sxs-lookup"><span data-stu-id="74fd5-157">An autosuggest box on the Maps app canvas.</span></span>
<br></br>
  <img src="images/maps-canvas.png" alt="autosuggest box on Maps app canvas"/>
</td>
</tr>

<tr class="even">
<td align="left" style="vertical-align: top;"><a href="../controls-and-patterns/app-bars.md"><span data-ttu-id="74fd5-158">Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="74fd5-158">Command bar</span></span></a>
<p><img src="../controls-and-patterns/images/controls_appbar_icons.png" alt="Example of a command bar with icons" /></p></td>
<td align="left" style="vertical-align: top;"> <span data-ttu-id="74fd5-159">Befehlsleisten helfen beim Organisieren von Befehlen und machen sie leicht zugänglich.</span><span class="sxs-lookup"><span data-stu-id="74fd5-159">Command bars help organize commands and make them easy to access.</span></span> <span data-ttu-id="74fd5-160">Befehlsleisten können am oberen Bildschirmrand, am unteren Bildschirmrand oder sowohl am oberen als auch am unteren Bildschirmrand platziert werden.</span><span class="sxs-lookup"><span data-stu-id="74fd5-160">Command bars can be placed at the top of the screen, at the bottom of the screen, or at both the top and bottom of the screen.</span></span> 
</td>
<td>
<span data-ttu-id="74fd5-161">Eine Befehlsleiste am oberen Rand der Maps-App.</span><span class="sxs-lookup"><span data-stu-id="74fd5-161">A command bar at the top of the Maps app.</span></span>
<br></br>
<img src="images/maps-commandbar.png" alt="command bar in Maps app"/>
</td>
</tr>

<tr class="odd">
<td align="left" style="vertical-align: top;"><a href="../controls-and-patterns/menus.md"><span data-ttu-id="74fd5-162">Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="74fd5-162">Menus and context menus</span></span></a>
<p><img src="images/controls-contextmenu-singlepane.png" alt="Example of a single-pane context menu" /></p></td>
<td align="left" style="vertical-align: top;"><span data-ttu-id="74fd5-163">Mitunter ist es effektiver, mehrere Befehle in einem Befehlsmenü zu gruppieren, um Platz zu sparen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-163">Sometimes it is more efficient to group multiple commands into a command menu to save space.</span></span> <span data-ttu-id="74fd5-164">Menüs und Kontextmenüs zeigen auf Anforderung des Benutzers eine Liste von Befehlen oder Optionen an.</span><span class="sxs-lookup"><span data-stu-id="74fd5-164">Menus and context menus display a list of commands or options when the user requests them.</span></span>
<p><span data-ttu-id="74fd5-165">Kontextmenüs eignen sich für Verknüpfungen mit häufig verwendeten Aktionen und ermöglichen den Zugriff auf sekundäre Befehle, die nur in bestimmten Kontexten relevant sind (z. B. die Zwischenablage oder spezielle Befehle).</span><span class="sxs-lookup"><span data-stu-id="74fd5-165">Context menus can provide shortcuts to commonly-used actions and provide access to secondary commands that are only relevant in certain contexts, such as clipboard or custom commands.</span></span> <span data-ttu-id="74fd5-166">Kontextmenüs werden in der Regel durch einen Rechtsklick des Benutzers aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-166">Context menus are usually prompted by a user right-clicking.</span></span></p>
</td><td>
<span data-ttu-id="74fd5-167">Ein Kontextmenü erscheint, wenn der Benutzer mit der rechten Maustaste in der App-Maps klickt.</span><span class="sxs-lookup"><span data-stu-id="74fd5-167">A context menu appears when users right-click in the Maps app.</span></span>
<br></br>
  <img src="images/maps-contextmenu.png" alt="context menu in Maps app"/>
</td>
</tr>
</table>
</div>

## <a name="provide-feedback-for-interactions"></a><span data-ttu-id="74fd5-168">Geben Sie Ihr Feedback zu Interaktionen</span><span class="sxs-lookup"><span data-stu-id="74fd5-168">Provide feedback for interactions</span></span>

<span data-ttu-id="74fd5-169">Feedback kommuniziert die Ergebnisse von Befehlen und ermöglicht dem Benutzer zu verstehen, was er getan hat und was er als nächstes tun kann.</span><span class="sxs-lookup"><span data-stu-id="74fd5-169">Feedback communicates the results of commands and allows users to understand what they've done, and what they can do next.</span></span> <span data-ttu-id="74fd5-170">Im Idealfall sollte das Feedback natürlich in Ihre Benutzeroberfläche integriert werden, so dass Benutzer nicht unterbrochen werden müssen oder zusätzliche Maßnahmen ergreifen müssen, es sei denn, dies ist absolut notwendig.</span><span class="sxs-lookup"><span data-stu-id="74fd5-170">Ideally, feedback should be integrated naturally in your UI, so users don't have to be interrupted, or take additional action unless absolutely necessary.</span></span> 

<span data-ttu-id="74fd5-171">Hier sind einige Möglichkeiten, um Feedback in Ihrer App bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-171">Here are some ways to provide feedback in your app.</span></span>

<div class="mx-responsive-img">
<table class="uwpd-top-aligned-table">

<tr class="header">
<th align="left"><span data-ttu-id="74fd5-172">Oberfläche</span><span class="sxs-lookup"><span data-stu-id="74fd5-172">Surface</span></span></th>
<th align="left"><span data-ttu-id="74fd5-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74fd5-173">Description</span></span></th>
</tr>

<tr class="odd">
<td align="left" style="vertical-align: top;"> <a href="../controls-and-patterns/app-bars.md"><span data-ttu-id="74fd5-174">Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="74fd5-174">Command bar</span></span></a>
<p><img src="../controls-and-patterns/images/controls_appbar_icons.png" alt="Example of a command bar with icons" /></p>
</td>
<td align="left" style="vertical-align: top;"> <span data-ttu-id="74fd5-175">Der Inhaltsbereich der Befehlsleiste ist ein intuitiver Ort, um Benutzern einen Status mitzuteilen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-175">The content area of the command bar is an intuative place to communicate status to users if they'd like to see feedback.</span></span>
<p>
  <img src="images/commandbar_anatomy.png" alt="Command bar content area for feedback"/>
  </p>
</td>
</tr>

<tr class="even">
<td align="left" style="vertical-align: top;"><a href="../controls-and-patterns/dialogs.md"><span data-ttu-id="74fd5-176">Flyout</span><span class="sxs-lookup"><span data-stu-id="74fd5-176">Flyout</span></span></a>
<p><img src="images/controls-flyout-default-200.png" alt="Image of default flyout" /></p></td>
<td align="left" style="vertical-align: top;">
<span data-ttu-id="74fd5-177">Ein einfaches, kontextbezogenes Popup, das durch Antippen oder Klicken außerhalb des Flyouts verworfen werden kann.</span><span class="sxs-lookup"><span data-stu-id="74fd5-177">A lightweight contextual popup that can be dismissed by tapping or clicking somewhere outside the flyout.</span></span>
<p>
  <img src="../controls-and-patterns/images/controls/flyout.png" alt="Flyout above button"/>
  </p>
</td>
</tr>

<tr class="odd">
<td align="left" style="vertical-align: top;"><a href="../controls-and-patterns/dialogs.md"><span data-ttu-id="74fd5-178">Dialogfeld-Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="74fd5-178">Dialog controls</span></span></a>
<p><img src="images/controls-dialog-twobutton-200.png" alt="Example of a simple two-button dialog" /></p></td>
<td align="left" style="vertical-align: top;"><span data-ttu-id="74fd5-179">Dialogfelder sind modale Benutzeroberflächenüberlagerungen, die kontextbezogene App-Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="74fd5-179">Dialogs are modal UI overlays that provide contextual app information.</span></span> <span data-ttu-id="74fd5-180">Die meisten Dialogfelder blockieren die Interaktion mit dem App-Fenster, bis sie explizit geschlossen werden, und erfordern häufig eine Aktion des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="74fd5-180">In most cases, dialogs block interactions with the app window until being explicitly dismissed, and often request some kind of action from the user.</span></span>
<p><span data-ttu-id="74fd5-181">Dialogfelder können als störend empfunden werden und sollten daher nur in bestimmten Situationen zum Einsatz kommen.</span><span class="sxs-lookup"><span data-stu-id="74fd5-181">Dialogs can be disruptive and should only be used in certain situations.</span></span> <span data-ttu-id="74fd5-182">Weitere Informationen finden Sie unter [Bestätigen oder Rückgängigmachen von Aktionen](#when-to-confirm-or-undo-actions)</span><span class="sxs-lookup"><span data-stu-id="74fd5-182">For more info, see the [When to confirm or undo actions](#when-to-confirm-or-undo-actions) section.</span></span></p>
<p>
  <img src="../controls-and-patterns/images/dialogs/dialog_RS2_delete_file.png" alt="dialog delete file"/></p>
</td>
</tr>

</table>
</div>

> [!TIP]
> <span data-ttu-id="74fd5-183">Verwenden Sie nicht zu viele Bestätigungsdialogfelder. Diese können zwar sehr hilfreich sein, wenn dem Benutzer ein Fehler unterläuft, bei bewusst durchgeführten Aktionen sind sie jedoch eher hinderlich.</span><span class="sxs-lookup"><span data-stu-id="74fd5-183">Be careful of how much your app uses confirmation dialogs; they can be very helpful when the user makes a mistake, but they are a hindrance whenever the user is trying to perform an action intentionally.</span></span>

### <a name="when-to-confirm-or-undo-actions"></a><span data-ttu-id="74fd5-184">Bestätigen oder Rückgängigmachen von Aktionen</span><span class="sxs-lookup"><span data-stu-id="74fd5-184">When to confirm or undo actions</span></span>

<span data-ttu-id="74fd5-185">Ganz gleich, wie gut die Benutzeroberfläche gestaltet ist und wie vorsichtig der Benutzer vorgeht: Irgendwann wird jeder Benutzer eine Aktion ausführen, die er lieber nicht ausgeführt hätte.</span><span class="sxs-lookup"><span data-stu-id="74fd5-185">No matter how well-designed the user interface is and no matter how careful the user is, at some point, all users will perform an action they wish they hadn't.</span></span> <span data-ttu-id="74fd5-186">In einer solchen Situation kann Ihre App dem Benutzer helfen, indem sie eine Aktionsbestätigung anfordert oder eine Möglichkeit zum Rückgängigmachen der kürzlich durchgeführten Aktionen anbietet.</span><span class="sxs-lookup"><span data-stu-id="74fd5-186">Your app can help in these situations by requiring the user to confirm an action, or by providing a way of undoing recent actions.</span></span>

-   <span data-ttu-id="74fd5-187">Für Aktionen, die nicht rückgängig gemacht werden können und schwerwiegende Auswirkungen haben, empfehlen wir die Verwendung eines Bestätigungsdialogfelds.</span><span class="sxs-lookup"><span data-stu-id="74fd5-187">For actions that can't be undone and have major consequences, we recommend using a confirmation dialog.</span></span> <span data-ttu-id="74fd5-188">Beispiele für solche Aktionen:</span><span class="sxs-lookup"><span data-stu-id="74fd5-188">Examples of such actions include:</span></span>
    -   <span data-ttu-id="74fd5-189">Überschreiben einer Datei</span><span class="sxs-lookup"><span data-stu-id="74fd5-189">Overwriting a file</span></span>
    -   <span data-ttu-id="74fd5-190">Schließen einer Datei ohne Speichern</span><span class="sxs-lookup"><span data-stu-id="74fd5-190">Not saving a file before closing</span></span>
    -   <span data-ttu-id="74fd5-191">Bestätigen der endgültigen Löschung einer Datei oder von Daten</span><span class="sxs-lookup"><span data-stu-id="74fd5-191">Confirming permanent deletion of a file or data</span></span>
    -   <span data-ttu-id="74fd5-192">Einkaufen (es sei denn, der Benutzer lehnt eine Bestätigungsanforderung ab)</span><span class="sxs-lookup"><span data-stu-id="74fd5-192">Making a purchase (unless the user opts out of requiring a confirmation)</span></span>
    -   <span data-ttu-id="74fd5-193">Senden eines Formulars, z. B. bei Registrierungen</span><span class="sxs-lookup"><span data-stu-id="74fd5-193">Submitting a form, such as signing up for something</span></span>
-   <span data-ttu-id="74fd5-194">Für Aktionen, die rückgängig gemacht werden können, ist ein einfacher „Rückgängig“-Befehl in der Regel ausreichend.</span><span class="sxs-lookup"><span data-stu-id="74fd5-194">For actions that can be undone, offering a simple undo command is usually enough.</span></span> <span data-ttu-id="74fd5-195">Beispiele für solche Aktionen:</span><span class="sxs-lookup"><span data-stu-id="74fd5-195">Examples of such actions include:</span></span>
    -   <span data-ttu-id="74fd5-196">Löschen einer Datei</span><span class="sxs-lookup"><span data-stu-id="74fd5-196">Deleting a file</span></span>
    -   <span data-ttu-id="74fd5-197">Löschen einer E-Mail (nicht endgültig)</span><span class="sxs-lookup"><span data-stu-id="74fd5-197">Deleting an email (not permanently)</span></span>
    -   <span data-ttu-id="74fd5-198">Ändern des Inhalts oder Bearbeiten von Text</span><span class="sxs-lookup"><span data-stu-id="74fd5-198">Modifying content or editing text</span></span>
    -   <span data-ttu-id="74fd5-199">Umbenennen einer Datei</span><span class="sxs-lookup"><span data-stu-id="74fd5-199">Renaming a file</span></span>

##  <a name="optimize-for-specific-input-types"></a><span data-ttu-id="74fd5-200"> Optimieren für bestimmte Eingabearten</span><span class="sxs-lookup"><span data-stu-id="74fd5-200">Optimize for specific input types</span></span>

<span data-ttu-id="74fd5-201">Ausführliche Informationen zum Optimieren der Benutzerfreundlichkeit bei einem bestimmten Eingabetyp oder -gerät finden Sie unter [Einführung in die Interaktion](../input/index.md).</span><span class="sxs-lookup"><span data-stu-id="74fd5-201">See the [Interaction primer](../input/index.md) for more detail on optimizing user experiences around a specific input type or device.</span></span>