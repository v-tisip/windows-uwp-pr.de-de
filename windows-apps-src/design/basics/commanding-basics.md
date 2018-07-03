---
author: mijacobs
Description: In a Universal Windows Platform (UWP) app, command elements are the interactive UI elements that enable the user to perform actions, such as sending an email, deleting an item, or submitting a form.
title: Befehlsdesigngrundlagen für Apps der universellen Windows-Plattform (UWP)
ms.assetid: 1DB48285-07B7-4952-80EF-02B57D4469F2
label: Command design basics
template: detail.hbs
op-migration-status: ready
ms.author: mijacobs
ms.date: 05/04/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 09f775ad0ba596379b6d3ddf158285849520111f
ms.sourcegitcommit: 517c83baffd344d4c705bc644d7c6d2b1a4c7e1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "1842567"
---
#  <a name="command-design-basics-for-uwp-apps"></a><span data-ttu-id="57cde-103">Befehlsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="57cde-103">Command design basics for UWP apps</span></span>

<span data-ttu-id="57cde-104">Bei den *Befehlselementen* in einer Universellen Windows-Plattform (UWP)-App handelt es sich um die interaktiven Benutzeroberflächenelemente, mit denen der Benutzer Aktionen durchführen kann, um beispielsweise eine E-Mail zu senden, ein Element zu löschen oder ein Formular zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="57cde-104">In a Universal Windows Platform (UWP) app, *command elements* are interactive UI elements that enable users to perform actions, such as sending an email, deleting an item, or submitting a form.</span></span> <span data-ttu-id="57cde-105">Dieser Artikel beschreibt allgemeine Befehlselemente, die von ihnen unterstützten Interaktionen und die Befehlsoberflächen für ihr Hosting.</span><span class="sxs-lookup"><span data-stu-id="57cde-105">This article describes common command elements, the interactions they support, and the command surfaces for hosting them.</span></span>

## <a name="provide-the-right-type-of-interactions"></a><span data-ttu-id="57cde-106">Bereitstellen geeigneter Interaktionen</span><span class="sxs-lookup"><span data-stu-id="57cde-106">Provide the right type of interactions</span></span>

<span data-ttu-id="57cde-107">Die wichtigste Entscheidung bei der Gestaltung einer Befehlsschnittstelle ist die Wahl der möglichen Benutzeraktionen.</span><span class="sxs-lookup"><span data-stu-id="57cde-107">When designing a command interface, the most important decision is choosing what users should be able to do.</span></span> <span data-ttu-id="57cde-108">Um die richtige Art Interaktionen zu planen, konzentrieren Sie sich auf Ihre App – denken Sie daran, welche Benutzererfahrungen Sie ermöglichen möchten und welche Schritte die Benutzer unternehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="57cde-108">To plan the right type of interactions, focus on your app - consider the user experiences you want to enable, and what steps users will need to take.</span></span> <span data-ttu-id="57cde-109">Sobald Sie entscheiden, was die Benutzer erreichen sollen, können Sie ihnen die entsprechenden Werkzeuge zur Verfügung stellen.</span><span class="sxs-lookup"><span data-stu-id="57cde-109">Once you decide what you want users to accomplish, then you can provide them the tools to do so.</span></span>

<span data-ttu-id="57cde-110">Einige Interaktionen für Ihre App sind:</span><span class="sxs-lookup"><span data-stu-id="57cde-110">Some interactions you might want to provide your app include:</span></span>

- <span data-ttu-id="57cde-111">Senden oder Übermitteln von Informationen</span><span class="sxs-lookup"><span data-stu-id="57cde-111">Sending or submiting information</span></span> 
- <span data-ttu-id="57cde-112">Auswählen von Einstellungen und Auswahlmöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="57cde-112">Selecting settings and choices</span></span>
- <span data-ttu-id="57cde-113">Suchen und Filtern von Inhalten</span><span class="sxs-lookup"><span data-stu-id="57cde-113">Searching and filtering content</span></span>
- <span data-ttu-id="57cde-114">Öffnen, Speichern und Löschen von Dateien</span><span class="sxs-lookup"><span data-stu-id="57cde-114">Opening, saving, and deleting files</span></span>
- <span data-ttu-id="57cde-115">Inhalte bearbeiten oder erstellen</span><span class="sxs-lookup"><span data-stu-id="57cde-115">Editing or creating content</span></span>

## <a name="use-the-right-command-element-for-the-interaction"></a><span data-ttu-id="57cde-116">Verwenden Sie das richtige Befehlselement für die Interaktion</span><span class="sxs-lookup"><span data-stu-id="57cde-116">Use the right command element for the interaction</span></span>

<span data-ttu-id="57cde-117">Die Verwendung der richtigen Elemente zur Befehlsinteraktionen kann den Unterschied zwischen einer intuitiven, benutzerfreundlichen App und einer schwierigen, verwirrenden App ausmachen.</span><span class="sxs-lookup"><span data-stu-id="57cde-117">Using the right elements to enable command interactions can make the difference between an intuitive, easy-to-use app and a difficult, confusing app.</span></span> <span data-ttu-id="57cde-118">Die Universelle Windows-Plattform (UWP) bietet eine große Anzahl von Befehlselementen, die Sie in Ihrer App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="57cde-118">The Universal Windows Platform (UWP) provides a large set of command elements that you can use in your app.</span></span> <span data-ttu-id="57cde-119">Die folgende Liste enthält einige der gängigsten Steuerelemente sowie eine Zusammenfassung der jeweils möglichen Interaktionen:</span><span class="sxs-lookup"><span data-stu-id="57cde-119">Here's a list of some of the most common controls and a summary of the interactions they can enable.</span></span>

<span data-ttu-id="57cde-120">:::row::: :::column::: ![Bild mit Schaltfläche](images/commanding/thumbnail-button.svg) :::column-end::: :::column span="2"::: <b>Schaltflächen</b></span><span class="sxs-lookup"><span data-stu-id="57cde-120">:::row::: :::column::: ![button image](images/commanding/thumbnail-button.svg) :::column-end::: :::column span="2"::: <b>Buttons</b></span></span>

        <a href="../controls-and-patterns/buttons.md" style="text-decoration:none">Buttons</a> trigger an immediate action. Examples include sending an email, submitting form data, or confirming an action in a dialog.
<span data-ttu-id="57cde-121">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-121">:::row-end:::</span></span>

<span data-ttu-id="57cde-122">:::row::: :::column::: ![Bild mit Liste](images/commanding/thumbnail-list.svg) :::column-end::: :::column span="2"::: <b>Listen</b></span><span class="sxs-lookup"><span data-stu-id="57cde-122">:::row::: :::column::: ![list image](images/commanding/thumbnail-list.svg) :::column-end::: :::column span="2"::: <b>Lists</b></span></span>

        <a href="../controls-and-patterns/lists.md" style="text-decoration:none">Lists</a> present items in a interactive list or a grid. Usually used for many options or display items. Examples include drop-down list, list box, list view and grid view.
<span data-ttu-id="57cde-123">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-123">:::row-end:::</span></span>

<span data-ttu-id="57cde-124">:::row::: :::column::: ![Bild mit Auswahlsteuerelement](images/commanding/thumbnail-selection.svg) :::column-end::: :::column span="2"::: <b>Auswahlsteuerelemente</b></span><span class="sxs-lookup"><span data-stu-id="57cde-124">:::row::: :::column::: ![selection control image](images/commanding/thumbnail-selection.svg) :::column-end::: :::column span="2"::: <b>Selection controls</b></span></span>

        Lets users choose from a few options, such as when completing a survey or configuring app settings. Examples include <a href="../controls-and-patterns/checkbox.md">check box</a>, <a href="../controls-and-patterns/radio-button.md">radio button</a>, and <a href="../controls-and-patterns/toggles.md">toggle switch</a>.
<span data-ttu-id="57cde-125">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-125">:::row-end:::</span></span>

<span data-ttu-id="57cde-126">:::row::: :::column::: ![Bild mit Kalender](images/commanding/thumbnail-calendar.svg) :::column-end::: :::column span="2"::: <b>Kalender-, Datums- und Uhrzeitsteuerelemente</b></span><span class="sxs-lookup"><span data-stu-id="57cde-126">:::row::: :::column::: ![Calendar  image](images/commanding/thumbnail-calendar.svg) :::column-end::: :::column span="2"::: <b>Calendar, date and time pickers</b></span></span>

        <a href="../controls-and-patterns/date-and-time.md">Calendar, date and time pickers</a> enable users to view and modify date and time info, such as when creating an event or setting an alarm. Examples include calendar date picker, calendar view, date picker, time picker.
<span data-ttu-id="57cde-127">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-127">:::row-end:::</span></span>

<span data-ttu-id="57cde-128">:::row::: :::column::: ![Bild mit Feld mit automatischen Vorschläge](images/commanding/thumbnail-autosuggest.svg) :::column-end::: :::column span="2"::: <b>Eingabefeld mit automatischen Vorschlägen</b></span><span class="sxs-lookup"><span data-stu-id="57cde-128">:::row::: :::column::: ![Predictive text entry image](images/commanding/thumbnail-autosuggest.svg) :::column-end::: :::column span="2"::: <b>Predictive text entry</b></span></span>

        Provides suggestions as users type, such as when entering data or performing queries. Examples include <a href="../controls-and-patterns/auto-suggest-box.md">auto-suggest box</a>.<br>
<span data-ttu-id="57cde-129">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-129">:::row-end:::</span></span>

<span data-ttu-id="57cde-130">Eine vollständige Liste finden Sie unter [Steuerelemente und UI-Elemente](../controls-and-patterns/index.md).</span><span class="sxs-lookup"><span data-stu-id="57cde-130">For a complete list, see [Controls and UI elements](../controls-and-patterns/index.md)</span></span>

##  <a name="place-commands-on-the-right-surface"></a><span data-ttu-id="57cde-131">Platzieren von Befehlen auf der passenden Oberfläche</span><span class="sxs-lookup"><span data-stu-id="57cde-131">Place commands on the right surface</span></span>
<span data-ttu-id="57cde-132">Sie können Befehlselemente auf einer Reihe von Oberflächen in Ihrer App platzieren, einschließlich der App-Canvas oder spezieller Befehlscontainer, wie Befehlsleisten, Menüs, Dialoge und Flyouts.</span><span class="sxs-lookup"><span data-stu-id="57cde-132">You can place command elements on a number of surfaces in your app, including the app canvas or special command containers, such as command bars, menus, dialogs, and flyouts.</span></span>

<span data-ttu-id="57cde-133">Beachten Sie, dass Sie den Benutzern möglichst erlauben sollten, Inhalte direkt zu manipulieren, anstatt Befehle zu verwenden, die auf den Inhalt wirken.</span><span class="sxs-lookup"><span data-stu-id="57cde-133">Note that, whenever possible, you should allow users to manipulate content directly rather than use commands that act on the content.</span></span> <span data-ttu-id="57cde-134">Beispielsweise können Benutzer Listen durch Ziehen und Ablegen von Listenelementen neu anordnen, anstatt die Befehlsschaltflächen nach oben und unten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="57cde-134">For example, allow users to rearrange lists by dragging and dropping list items, rather than using up and down command buttons.</span></span>

<span data-ttu-id="57cde-135">Wenn Benutzer Inhalte aber nicht direkt manipulieren können, platzieren Sie Befehlselemente auf einer Befehlsoberfläche in Ihrer App:</span><span class="sxs-lookup"><span data-stu-id="57cde-135">Otherwise, if users can't manipulate content directly, then place command elements on a command surface in your app.</span></span> <span data-ttu-id="57cde-136">Hier eine Liste mit einigen der gängigsten Befehlsoberflächen.</span><span class="sxs-lookup"><span data-stu-id="57cde-136">Here's a list of some of the most common command surfaces.</span></span>

<span data-ttu-id="57cde-137">:::row::: :::column::: ![Bild mit App-Inhaltsbereich](images/commanding/thumbnail-canvas.svg) :::column-end::: :::column span="2"::: <b>App-Inhaltsbereich</b></span><span class="sxs-lookup"><span data-stu-id="57cde-137">:::row::: :::column::: ![app canvas image](images/commanding/thumbnail-canvas.svg) :::column-end::: :::column span="2"::: <b>App canvas (content area)</b></span></span>

        If a command is constantly needed for users to complete core scenarios, put it on the canvas. Because you can put commands near (or on) the objects they affect, putting commands on the canvas makes them easy and obvious to use. However, choose the commands you put on the canvas carefully. Too many commands on the app canvas take up valuable screen space and can overwhelm the user. If the command won't be frequently used, consider putting it in another command surface.
<span data-ttu-id="57cde-138">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-138">:::row-end:::</span></span>

<span data-ttu-id="57cde-139">:::row::: :::column::: ![Bild mit Befehlsleiste](images/commanding/thumbnail-commandbar.svg) :::column-end::: :::column span="2"::: <b>Befehlsleisten</b></span><span class="sxs-lookup"><span data-stu-id="57cde-139">:::row::: :::column::: ![commandbar image](images/commanding/thumbnail-commandbar.svg) :::column-end::: :::column span="2"::: <b>Command bars</b></span></span>

        <a href="../controls-and-patterns/app-bars.md">Command bars</a> help organize commands and make them easy to access. Command bars can be placed at the top of the screen, at the bottom of the screen, or at both the top and bottom of the screen.
<span data-ttu-id="57cde-140">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-140">:::row-end:::</span></span>

<span data-ttu-id="57cde-141">:::row::: :::column::: ![Bild mit Kontextmenü](images/commanding/thumbnail-contextmenu.svg) :::column-end::: :::column span="2"::: <b>Menüs und Kontextmenüs</b></span><span class="sxs-lookup"><span data-stu-id="57cde-141">:::row::: :::column::: ![context menu image](images/commanding/thumbnail-contextmenu.svg) :::column-end::: :::column span="2"::: <b>Menus and context menus</b></span></span>

        Sometimes it is more efficient to group multiple commands into a command menu to save space. <a href="../controls-and-patterns/menus.md">Menus and context menus</a> display a list of commands or options when the user requests them. Context menus can provide shortcuts to commonly-used actions and provide access to secondary commands that are only relevant in certain contexts, such as clipboard or custom commands. Context menus are usually prompted by a user right-clicking.
<span data-ttu-id="57cde-142">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-142">:::row-end:::</span></span>

## <a name="provide-feedback-for-interactions"></a><span data-ttu-id="57cde-143">Reagieren auf Interaktionen durch Feedback</span><span class="sxs-lookup"><span data-stu-id="57cde-143">Provide feedback for interactions</span></span>

<span data-ttu-id="57cde-144">Feedback kommuniziert die Ergebnisse von Befehlen und ermöglicht dem Benutzer zu verstehen, was er getan hat und was er als nächstes tun kann.</span><span class="sxs-lookup"><span data-stu-id="57cde-144">Feedback communicates the results of commands and allows users to understand what they've done, and what they can do next.</span></span> <span data-ttu-id="57cde-145">Im Idealfall sollte das Feedback natürlich in Ihre Benutzeroberfläche integriert werden, so dass Benutzer nicht unterbrochen werden müssen oder zusätzliche Maßnahmen ergreifen müssen, es sei denn, dies ist absolut notwendig.</span><span class="sxs-lookup"><span data-stu-id="57cde-145">Ideally, feedback should be integrated naturally in your UI, so users don't have to be interrupted, or take additional action unless absolutely necessary.</span></span> 

<span data-ttu-id="57cde-146">Hier sind einige Möglichkeiten, um Feedback in Ihrer App bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="57cde-146">Here are some ways to provide feedback in your app.</span></span>

<span data-ttu-id="57cde-147">:::row::: :::column::: ![Bild mit Befehlsleisten-Inhaltsbereich](images/commanding/thumbnail-commandbar2.svg) :::column-end::: :::column span="2"::: <b>Befehlsleiste</b></span><span class="sxs-lookup"><span data-stu-id="57cde-147">:::row::: :::column::: ![commandbar content area image](images/commanding/thumbnail-commandbar2.svg) :::column-end::: :::column span="2"::: <b>Command bar</b></span></span>

        The content area of the <a href="../controls-and-patterns/app-bars.md">command bar</a> is an intuitive place to communicate status to users if they'd like to see feedback.
<span data-ttu-id="57cde-148">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-148">:::row-end:::</span></span>

<span data-ttu-id="57cde-149">:::row::: :::column::: ![Bild mit Flyout](images/commanding/thumbnail-flyout.svg) :::column-end::: :::column span="2"::: <b>Flyouts</b></span><span class="sxs-lookup"><span data-stu-id="57cde-149">:::row::: :::column::: ![Flyout image](images/commanding/thumbnail-flyout.svg) :::column-end::: :::column span="2"::: <b>Flyouts</b></span></span>

       <a href="../controls-and-patterns/dialogs.md">Flyouts</a> are lightweight contextual popups that can be dismissed by tapping or clicking somewhere outside the flyout.
<span data-ttu-id="57cde-150">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-150">:::row-end:::</span></span>

<span data-ttu-id="57cde-151">:::row::: :::column::: ![Bild mit Dialogfeld](images/commanding/thumbnail-dialog.svg) :::column-end::: :::column span="2"::: <b>Dialogfelder</b></span><span class="sxs-lookup"><span data-stu-id="57cde-151">:::row::: :::column::: ![Dialog image](images/commanding/thumbnail-dialog.svg) :::column-end::: :::column span="2"::: <b>Dialog controls</b></span></span>

        <a href="../controls-and-patterns/dialogs.md">Dialog controls</a> are modal UI overlays that provide contextual app information. In most cases, dialogs block interactions with the app window until being explicitly dismissed, and often request some kind of action from the user. Dialogs can be disruptive and should only be used in certain situations. For more info, see the [When to confirm or undo actions](#when-to-confirm-or-undo-actions) section.
    :::column-end:::
<span data-ttu-id="57cde-152">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-152">:::row-end:::</span></span>

> [!TIP]
> <span data-ttu-id="57cde-153">Verwenden Sie nicht zu viele Bestätigungsdialogfelder. Diese können zwar sehr hilfreich sein, wenn dem Benutzer ein Fehler unterläuft, bei bewusst durchgeführten Aktionen sind sie jedoch eher hinderlich.</span><span class="sxs-lookup"><span data-stu-id="57cde-153">Be careful of how much your app uses confirmation dialogs; they can be very helpful when the user makes a mistake, but they are a hindrance whenever the user is trying to perform an action intentionally.</span></span>

### <a name="when-to-confirm-or-undo-actions"></a><span data-ttu-id="57cde-154">Bestätigen oder Rückgängigmachen von Aktionen</span><span class="sxs-lookup"><span data-stu-id="57cde-154">When to confirm or undo actions</span></span>

<span data-ttu-id="57cde-155">Ganz gleich, wie gut die Benutzeroberfläche gestaltet ist und wie vorsichtig der Benutzer vorgeht: Irgendwann wird jeder Benutzer eine Aktion ausführen, die er lieber nicht ausgeführt hätte.</span><span class="sxs-lookup"><span data-stu-id="57cde-155">No matter how well-designed the user interface is and no matter how careful the user is, at some point, all users will perform an action they wish they hadn't.</span></span> <span data-ttu-id="57cde-156">In einer solchen Situation kann Ihre App dem Benutzer helfen, indem sie eine Aktionsbestätigung anfordert oder eine Möglichkeit zum Rückgängigmachen der kürzlich durchgeführten Aktionen anbietet.</span><span class="sxs-lookup"><span data-stu-id="57cde-156">Your app can help in these situations by requiring the user to confirm an action, or by providing a way of undoing recent actions.</span></span>

<span data-ttu-id="57cde-157">:::row::: :::column::: ![Beispiel für „Richtig”</span><span class="sxs-lookup"><span data-stu-id="57cde-157">:::row::: :::column::: ![do image</span></span>](images/do.svg)

        For actions that can't be undone and have major consequences, we recommend using a confirmation dialog. Examples of such actions include:
        -   Overwriting a file
        -   Not saving a file before closing
        -   Confirming permanent deletion of a file or data
        -   Making a purchase (unless the user opts out of requiring a confirmation)
        -   Submitting a form, such as signing up for something
    :::column-end:::
    :::column:::
        ![do image](images/do.svg)

        For actions that can be undone, offering a simple undo command is usually enough. Examples of such actions include:
        -   Deleting a file
        -   Deleting an email (not permanently)
        -   Modifying content or editing text
        -   Renaming a file
<span data-ttu-id="57cde-158">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="57cde-158">:::row-end:::</span></span>

##  <a name="optimize-for-specific-input-types"></a><span data-ttu-id="57cde-159">Optimieren für bestimmte Eingabearten</span><span class="sxs-lookup"><span data-stu-id="57cde-159">Optimize for specific input types</span></span>

<span data-ttu-id="57cde-160">Ausführliche Informationen zum Optimieren der Benutzerfreundlichkeit bei einem bestimmten Eingabetyp oder -gerät finden Sie unter [Einführung in die Interaktion](../input/index.md).</span><span class="sxs-lookup"><span data-stu-id="57cde-160">See the [Interaction primer](../input/index.md) for more detail on optimizing user experiences around a specific input type or device.</span></span>

