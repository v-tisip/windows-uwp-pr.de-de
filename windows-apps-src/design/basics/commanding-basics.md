---
author: mijacobs
Description: In a Universal Windows Platform (UWP) app, command elements are the interactive UI elements that enable the user to perform actions, such as sending an email, deleting an item, or submitting a form.
title: Befehlsdesigngrundlagen für Apps der universellen Windows-Plattform (UWP)
ms.assetid: 1DB48285-07B7-4952-80EF-02B57D4469F2
label: Command design basics
template: detail.hbs
op-migration-status: ready
ms.author: mijacobs
ms.date: 10/01/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 5cf3b107ad24b34ed5eeb836fbab5b83d6d2f80b
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5690548"
---
#  <a name="command-design-basics-for-uwp-apps"></a><span data-ttu-id="590c4-103">Befehlsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="590c4-103">Command design basics for UWP apps</span></span>

<span data-ttu-id="590c4-104">Bei den *Befehlselementen* in einer Universellen Windows-Plattform (UWP)-App handelt es sich um die interaktiven Benutzeroberflächenelemente, mit denen der Benutzer Aktionen durchführen kann, um beispielsweise eine E-Mail zu senden, ein Element zu löschen oder ein Formular zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="590c4-104">In a Universal Windows Platform (UWP) app, *command elements* are interactive UI elements that enable users to perform actions, such as sending an email, deleting an item, or submitting a form.</span></span> <span data-ttu-id="590c4-105">Dieser Artikel beschreibt allgemeine Befehlselemente, die von ihnen unterstützten Interaktionen und die Befehlsoberflächen für ihr Hosting.</span><span class="sxs-lookup"><span data-stu-id="590c4-105">This article describes common command elements, the interactions they support, and the command surfaces for hosting them.</span></span>

## <a name="provide-the-right-type-of-interactions"></a><span data-ttu-id="590c4-106">Bereitstellen geeigneter Interaktionen</span><span class="sxs-lookup"><span data-stu-id="590c4-106">Provide the right type of interactions</span></span>

<span data-ttu-id="590c4-107">Die wichtigste Entscheidung bei der Gestaltung einer Befehlsschnittstelle ist die Wahl der möglichen Benutzeraktionen.</span><span class="sxs-lookup"><span data-stu-id="590c4-107">When designing a command interface, the most important decision is choosing what users should be able to do.</span></span> <span data-ttu-id="590c4-108">Um die richtige Art Interaktionen zu planen, konzentrieren Sie sich auf Ihre App – denken Sie daran, welche Benutzererfahrungen Sie ermöglichen möchten und welche Schritte die Benutzer unternehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="590c4-108">To plan the right type of interactions, focus on your app - consider the user experiences you want to enable, and what steps users will need to take.</span></span> <span data-ttu-id="590c4-109">Sobald Sie entscheiden, was die Benutzer erreichen sollen, können Sie ihnen die entsprechenden Werkzeuge zur Verfügung stellen.</span><span class="sxs-lookup"><span data-stu-id="590c4-109">Once you decide what you want users to accomplish, then you can provide them the tools to do so.</span></span>

<span data-ttu-id="590c4-110">Einige Interaktionen für Ihre App sind:</span><span class="sxs-lookup"><span data-stu-id="590c4-110">Some interactions you might want to provide your app include:</span></span>

- <span data-ttu-id="590c4-111">Senden oder Übermitteln von Informationen</span><span class="sxs-lookup"><span data-stu-id="590c4-111">Sending or submiting information</span></span> 
- <span data-ttu-id="590c4-112">Auswählen von Einstellungen und Auswahlmöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="590c4-112">Selecting settings and choices</span></span>
- <span data-ttu-id="590c4-113">Suchen und Filtern von Inhalten</span><span class="sxs-lookup"><span data-stu-id="590c4-113">Searching and filtering content</span></span>
- <span data-ttu-id="590c4-114">Öffnen, Speichern und Löschen von Dateien</span><span class="sxs-lookup"><span data-stu-id="590c4-114">Opening, saving, and deleting files</span></span>
- <span data-ttu-id="590c4-115">Inhalte bearbeiten oder erstellen</span><span class="sxs-lookup"><span data-stu-id="590c4-115">Editing or creating content</span></span>

## <a name="use-the-right-command-element-for-the-interaction"></a><span data-ttu-id="590c4-116">Verwenden Sie das richtige Befehlselement für die Interaktion</span><span class="sxs-lookup"><span data-stu-id="590c4-116">Use the right command element for the interaction</span></span>

<span data-ttu-id="590c4-117">Die Verwendung der richtigen Elemente zur Befehlsinteraktionen kann den Unterschied zwischen einer intuitiven, benutzerfreundlichen App und einer schwierigen, verwirrenden App ausmachen.</span><span class="sxs-lookup"><span data-stu-id="590c4-117">Using the right elements to enable command interactions can make the difference between an intuitive, easy-to-use app and a difficult, confusing app.</span></span> <span data-ttu-id="590c4-118">Die Universelle Windows-Plattform (UWP) bietet eine große Anzahl von Befehlselementen, die Sie in Ihrer App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="590c4-118">The Universal Windows Platform (UWP) provides a large set of command elements that you can use in your app.</span></span> <span data-ttu-id="590c4-119">Die folgende Liste enthält einige der gängigsten Steuerelemente sowie eine Zusammenfassung der jeweils möglichen Interaktionen:</span><span class="sxs-lookup"><span data-stu-id="590c4-119">Here's a list of some of the most common controls and a summary of the interactions they can enable.</span></span>

:::row:::
    :::column:::
        ![button image](images/commanding/thumbnail-button.svg)
    :::column-end:::
    :::column span="2":::
        <b>Buttons</b>

        <a href="../controls-and-patterns/buttons.md" style="text-decoration:none">Buttons</a> trigger an immediate action. Examples include sending an email, submitting form data, or confirming an action in a dialog.
:::row-end:::

:::row:::
    :::column:::
        ![list image](images/commanding/thumbnail-list.svg)
    :::column-end:::
    :::column span="2":::
        <b>Lists</b>

        <a href="../controls-and-patterns/lists.md" style="text-decoration:none">Lists</a> present items in a interactive list or a grid. Usually used for many options or display items. Examples include drop-down list, list box, list view and grid view.
:::row-end:::

:::row:::
    :::column:::
        ![selection control image](images/commanding/thumbnail-selection.svg)
    :::column-end:::
    :::column span="2":::
        <b>Selection controls</b>

        Lets users choose from a few options, such as when completing a survey or configuring app settings. Examples include <a href="../controls-and-patterns/checkbox.md">check box</a>, <a href="../controls-and-patterns/radio-button.md">radio button</a>, and <a href="../controls-and-patterns/toggles.md">toggle switch</a>.
:::row-end:::

:::row:::
    :::column:::
        ![Calendar  image](images/commanding/thumbnail-calendar.svg)
    :::column-end:::
    :::column span="2":::
        <b>Calendar, date and time pickers</b>

        <a href="../controls-and-patterns/date-and-time.md">Calendar, date and time pickers</a> enable users to view and modify date and time info, such as when creating an event or setting an alarm. Examples include calendar date picker, calendar view, date picker, time picker.
:::row-end:::

:::row:::
    :::column:::
        ![Predictive text entry image](images/commanding/thumbnail-autosuggest.svg)
    :::column-end:::
    :::column span="2":::
        <b>Predictive text entry</b>

        Provides suggestions as users type, such as when entering data or performing queries. Examples include <a href="../controls-and-patterns/auto-suggest-box.md">auto-suggest box</a>.<br>
:::row-end:::

<span data-ttu-id="590c4-120">Eine vollständige Liste finden Sie unter [Steuerelemente und UI-Elemente](../controls-and-patterns/index.md).</span><span class="sxs-lookup"><span data-stu-id="590c4-120">For a complete list, see [Controls and UI elements](../controls-and-patterns/index.md)</span></span>

## <a name="place-commands-on-the-right-surface"></a><span data-ttu-id="590c4-121">Platzieren von Befehlen auf der passenden Oberfläche</span><span class="sxs-lookup"><span data-stu-id="590c4-121">Place commands on the right surface</span></span>

<span data-ttu-id="590c4-122">Sie können Befehlselemente auf einer Reihe von Oberflächen in Ihrer app, einschließlich der app-Canvas oder spezieller befehlscontainer, wie z. B. eine Befehlsleiste, Befehlsleisten-Flyout, Menüleiste und Dialogfeld platzieren.</span><span class="sxs-lookup"><span data-stu-id="590c4-122">You can place command elements on a number of surfaces in your app, including the app canvas or special command containers, such as a command bar, command bar flyout, menu bar, and dialog.</span></span>

<span data-ttu-id="590c4-123">Beachten Sie, dass, wenn möglich, Sie sollten Benutzer mit den Befehlen, die auf den Inhalt zugreifen, anstatt Inhalte direkt zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="590c4-123">Note that, whenever possible, you should let users manipulate content directly rather than use commands that act on the content.</span></span> <span data-ttu-id="590c4-124">Beispielsweise können Benutzer Listen durch Ziehen und Ablegen von Listenelementen neu anordnen, anstatt die Befehlsschaltflächen nach oben und unten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="590c4-124">For example, allow users to rearrange lists by dragging and dropping list items, rather than using up and down command buttons.</span></span>

<span data-ttu-id="590c4-125">Wenn Benutzer Inhalte aber nicht direkt manipulieren können, platzieren Sie Befehlselemente auf einer Befehlsoberfläche in Ihrer App:</span><span class="sxs-lookup"><span data-stu-id="590c4-125">Otherwise, if users can't manipulate content directly, then place command elements on a command surface in your app.</span></span> <span data-ttu-id="590c4-126">Hier eine Liste mit einigen der gängigsten Befehlsoberflächen.</span><span class="sxs-lookup"><span data-stu-id="590c4-126">Here's a list of some of the most common command surfaces.</span></span>

:::row:::
    :::column:::
        ![app canvas image](images/commanding/thumbnail-canvas.svg)
    :::column-end:::
    :::column span="2":::
        <b>App canvas (content area)</b>

        If a command is constantly needed for users to complete core scenarios, put it on the canvas. Because you can put commands near (or on) the objects they affect, putting commands on the canvas makes them easy and obvious to use. However, choose the commands you put on the canvas carefully. Too many commands on the app canvas take up valuable screen space and can overwhelm the user. If the command won't be frequently used, consider putting it in another command surface.
:::row-end:::

:::row:::
    :::column:::
        ![commandbar image](images/commanding/thumbnail-commandbar.svg)
    :::column-end:::
    :::column span="2":::
        <b>Command bars and menu bars</b>

        <a href="../controls-and-patterns/app-bars.md">Command bars</a> help organize commands and make them easy to access. Command bars can be placed at the top of the screen, at the bottom of the screen, or at both the top and bottom of the screen (a <a href="../controls-and-patterns/menus.md#create-a-menu-bar">MenuBar</a> can also be used when the functionality in your app is too complex for a command bar).
:::row-end:::

:::row:::
    :::column:::
        ![context menu image](images/commanding/thumbnail-contextmenu.svg)
    :::column-end:::
    :::column span="2":::
        <b>Menus and context menus</b>

        <p>Menus and context menus save space by organizing commands and hiding them until the user needs them. Users typically access a menu or context menu by clicking a button or right-clicking a control.</p> 

        <p>The <a href="../controls-and-patterns/command-bar-flyout.md">command bar flyout </a> is a type of contextual menu that combines the benefits of a command bar and a context menu into a single control. It can provide shortcuts to commonly-used actions and provide access to secondary commands that are only relevant in certain contexts, such as clipboard or custom commands.</p>

        <p>UWP also provides a set of traditional menus and context menus; for more info, see the <a href="../controls-and-patterns/menus.md">menus and context menus overview</a>.</p>
:::row-end:::

## <a name="provide-feedback-for-interactions"></a><span data-ttu-id="590c4-127">Reagieren auf Interaktionen durch Feedback</span><span class="sxs-lookup"><span data-stu-id="590c4-127">Provide feedback for interactions</span></span>

<span data-ttu-id="590c4-128">Feedback kommuniziert die Ergebnisse von Befehlen und ermöglicht dem Benutzer zu verstehen, was er getan hat und was er als nächstes tun kann.</span><span class="sxs-lookup"><span data-stu-id="590c4-128">Feedback communicates the results of commands and allows users to understand what they've done, and what they can do next.</span></span> <span data-ttu-id="590c4-129">Im Idealfall sollte das Feedback natürlich in Ihre Benutzeroberfläche integriert werden, so dass Benutzer nicht unterbrochen werden müssen oder zusätzliche Maßnahmen ergreifen müssen, es sei denn, dies ist absolut notwendig.</span><span class="sxs-lookup"><span data-stu-id="590c4-129">Ideally, feedback should be integrated naturally in your UI, so users don't have to be interrupted, or take additional action unless absolutely necessary.</span></span> 

<span data-ttu-id="590c4-130">Hier sind einige Möglichkeiten, um Feedback in Ihrer App bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="590c4-130">Here are some ways to provide feedback in your app.</span></span>

:::row:::
    :::column:::
        ![commandbar content area image](images/commanding/thumbnail-commandbar2.svg)
    :::column-end:::
    :::column span="2":::
        <b>Command bar</b>

        The content area of the <a href="../controls-and-patterns/app-bars.md">command bar</a> is an intuitive place to communicate status to users if they'd like to see feedback.
:::row-end:::

:::row:::
    :::column:::
        ![Flyout image](images/commanding/thumbnail-flyout.svg)
    :::column-end:::
    :::column span="2":::
        <b>Flyouts</b>

       <span data-ttu-id="590c4-131"><a href="../controls-and-patterns/dialogs-and-flyouts/index.md">Flyouts</a> sind lightweight kontextbezogene-Popups, die durch Antippen oder klicken außerhalb des Flyouts verworfen werden können.</span><span class="sxs-lookup"><span data-stu-id="590c4-131"><a href="../controls-and-patterns/dialogs-and-flyouts/index.md">Flyouts</a> are lightweight contextual popups that can be dismissed by tapping or clicking somewhere outside the flyout.</span></span>
:::row-end:::

:::row:::
    :::column:::
        ![Dialog image](images/commanding/thumbnail-dialog.svg)
    :::column-end:::
    :::column span="2":::
        <b>Dialog controls</b>

        <a href="../controls-and-patterns/dialogs-and-flyouts/index.md">Dialog controls</a> are modal UI overlays that provide contextual app information. In most cases, dialogs block interactions with the app window until being explicitly dismissed, and often request some kind of action from the user. Dialogs can be disruptive and should only be used in certain situations. For more info, see the [When to confirm or undo actions](#when-to-confirm-or-undo-actions) section.
    :::column-end:::
:::row-end:::

> [!TIP]
> <span data-ttu-id="590c4-132">Verwenden Sie nicht zu viele Bestätigungsdialogfelder. Diese können zwar sehr hilfreich sein, wenn dem Benutzer ein Fehler unterläuft, bei bewusst durchgeführten Aktionen sind sie jedoch eher hinderlich.</span><span class="sxs-lookup"><span data-stu-id="590c4-132">Be careful of how much your app uses confirmation dialogs; they can be very helpful when the user makes a mistake, but they are a hindrance whenever the user is trying to perform an action intentionally.</span></span>

### <a name="when-to-confirm-or-undo-actions"></a><span data-ttu-id="590c4-133">Bestätigen oder Rückgängigmachen von Aktionen</span><span class="sxs-lookup"><span data-stu-id="590c4-133">When to confirm or undo actions</span></span>

<span data-ttu-id="590c4-134">Ganz gleich, wie gut die Benutzeroberfläche gestaltet ist und wie vorsichtig der Benutzer vorgeht: Irgendwann wird jeder Benutzer eine Aktion ausführen, die er lieber nicht ausgeführt hätte.</span><span class="sxs-lookup"><span data-stu-id="590c4-134">No matter how well-designed the user interface is and no matter how careful the user is, at some point, all users will perform an action they wish they hadn't.</span></span> <span data-ttu-id="590c4-135">In einer solchen Situation kann Ihre App dem Benutzer helfen, indem sie eine Aktionsbestätigung anfordert oder eine Möglichkeit zum Rückgängigmachen der kürzlich durchgeführten Aktionen anbietet.</span><span class="sxs-lookup"><span data-stu-id="590c4-135">Your app can help in these situations by requiring the user to confirm an action, or by providing a way of undoing recent actions.</span></span>

:::row:::
    :::column:::
        ![do image](images/do.svg)

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
:::row-end:::

##  <a name="optimize-for-specific-input-types"></a><span data-ttu-id="590c4-136">Optimieren für bestimmte Eingabearten</span><span class="sxs-lookup"><span data-stu-id="590c4-136">Optimize for specific input types</span></span>

<span data-ttu-id="590c4-137">Ausführliche Informationen zum Optimieren der Benutzerfreundlichkeit bei einem bestimmten Eingabetyp oder -gerät finden Sie unter [Einführung in die Interaktion](../input/index.md).</span><span class="sxs-lookup"><span data-stu-id="590c4-137">See the [Interaction primer](../input/index.md) for more detail on optimizing user experiences around a specific input type or device.</span></span>

