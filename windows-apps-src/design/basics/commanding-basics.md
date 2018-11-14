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
ms.openlocfilehash: 028cc9586180f2d94337282c3ed0cd58317b539b
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6653855"
---
# <a name="command-design-basics-for-uwp-apps"></a><span data-ttu-id="c189b-103">Befehlsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="c189b-103">Command design basics for UWP apps</span></span>

<span data-ttu-id="c189b-104">In einer app (universelle Windows Plattform) sind *Befehl* interaktive UI-Elemente, mit denen Benutzer Aktionen wie eine e-Mail zu senden, ein Element zu löschen oder ein Formular zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="c189b-104">In a Universal Windows Platform (UWP) app, *command elements* are interactive UI elements that let users perform actions such as sending an email, deleting an item, or submitting a form.</span></span> <span data-ttu-id="c189b-105">*Befehl Schnittstellen* bestehen aus allgemeine Befehlselemente, die befehlsoberflächen, die sie hosten, die Interaktionen, die sie unterstützen und die Umgebungen, die sie bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c189b-105">*Command interfaces* are composed of common command elements, the command surfaces that host them, the interactions they support, and the experiences they provide.</span></span>

## <a name="provide-the-best-command-experience"></a><span data-ttu-id="c189b-106">Bieten Sie eine optimale-Befehl</span><span class="sxs-lookup"><span data-stu-id="c189b-106">Provide the best command experience</span></span>

<span data-ttu-id="c189b-107">Der wichtigste Aspekt der Befehlsschnittstelle ist, welche die versuchen, die Benutzer erreichen können.</span><span class="sxs-lookup"><span data-stu-id="c189b-107">The most important aspect of a command interface is what your trying to let a user accomplish.</span></span> <span data-ttu-id="c189b-108">Wie Sie die Funktionen Ihrer app planen, sollten Sie die erforderlichen Schritte zum Erreichen dieser Vorgänge und die Benutzeroberflächen, die Sie aktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c189b-108">As you plan the functionality of your app, consider the steps required to accomplish those tasks and the user experiences you want to enable.</span></span> <span data-ttu-id="c189b-109">Nachdem Sie einen ersten Entwurf dieser diese Funktionen abgeschlossen haben, können Sie Entscheidungen über die Tools und Interaktionen zu deren Implementierung vornehmen.</span><span class="sxs-lookup"><span data-stu-id="c189b-109">Once you've completed an initial draft of these experiences, then you can make decisions on the tools and interactions to implement them.</span></span>

<span data-ttu-id="c189b-110">Hier sind einige allgemeine Anwendung-Funktionen:</span><span class="sxs-lookup"><span data-stu-id="c189b-110">Here are some common application experiences:</span></span>

- <span data-ttu-id="c189b-111">Senden oder Übermitteln von Informationen</span><span class="sxs-lookup"><span data-stu-id="c189b-111">Sending or submiting information</span></span>
- <span data-ttu-id="c189b-112">Auswählen von Einstellungen und Auswahlmöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="c189b-112">Selecting settings and choices</span></span>
- <span data-ttu-id="c189b-113">Suchen und Filtern von Inhalten</span><span class="sxs-lookup"><span data-stu-id="c189b-113">Searching and filtering content</span></span>
- <span data-ttu-id="c189b-114">Öffnen, Speichern und Löschen von Dateien</span><span class="sxs-lookup"><span data-stu-id="c189b-114">Opening, saving, and deleting files</span></span>
- <span data-ttu-id="c189b-115">Inhalte bearbeiten oder erstellen</span><span class="sxs-lookup"><span data-stu-id="c189b-115">Editing or creating content</span></span>

<span data-ttu-id="c189b-116">Seien Sie kreativ bei der Entwicklung Ihrer Befehl Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="c189b-116">Be creative with the design of your command experiences.</span></span> <span data-ttu-id="c189b-117">Wählen Sie die Eingabegeräte Ihrer app Reaktionsweise Ihrer app auf jedem Gerät, und unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c189b-117">Choose which input devices your app supports, and how your app responds to each device.</span></span> <span data-ttu-id="c189b-118">Durch die Unterstützung der breiten Palette an Funktionen und Einstellungen können Sie Ihre app als verwendbaren, tragbaren und wie möglich.</span><span class="sxs-lookup"><span data-stu-id="c189b-118">By supporting the broadest range of capabilities and preferences you make your app as usable, portable, and accessible as possible.</span></span>



<!--
When designing a command interface, the most important decision is choosing what a user can do. To plan the right type of interactions, focus on your app - consider the user experiences you want to enable, and what steps users will need to take. Once you decide what you want users to accomplish, then you can provide them the tools to do so.
-->

## <a name="choose-the-right-command-elements"></a><span data-ttu-id="c189b-119">Wählen Sie die richtigen Befehlselemente</span><span class="sxs-lookup"><span data-stu-id="c189b-119">Choose the right command elements</span></span>

<span data-ttu-id="c189b-120">Verwendung der richtigen Elemente in einer Befehlsschnittstelle kann den Unterschied zwischen einer intuitiven, leicht zu bedienende app und einer schwierigen, verwirrenden app ausmachen.</span><span class="sxs-lookup"><span data-stu-id="c189b-120">Using the right elements in a command interface can make the difference between an intuitive, easy-to-use app and a difficult, confusing app.</span></span> <span data-ttu-id="c189b-121">Ein umfassender Satz von befehlselementen sind in die universelle Windows-Plattform (UWP) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c189b-121">A comprehensive set of command elements are available in the Universal Windows Platform (UWP).</span></span> <span data-ttu-id="c189b-122">Hier ist eine Liste mit einigen der am häufigsten verwendeten UWP Befehlselemente.</span><span class="sxs-lookup"><span data-stu-id="c189b-122">Here's a list of some of the most common UWP command elements.</span></span>

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

<span data-ttu-id="c189b-123">Eine vollständige Liste finden Sie unter [Steuerelemente und UI-Elemente](../controls-and-patterns/index.md).</span><span class="sxs-lookup"><span data-stu-id="c189b-123">For a complete list, see [Controls and UI elements](../controls-and-patterns/index.md)</span></span>

## <a name="place-commands-on-the-right-surface"></a><span data-ttu-id="c189b-124">Platzieren von Befehlen auf der passenden Oberfläche</span><span class="sxs-lookup"><span data-stu-id="c189b-124">Place commands on the right surface</span></span>

<span data-ttu-id="c189b-125">Sie können Befehlselemente auf einer Reihe von Oberflächen in Ihrer app, einschließlich der app-Canvas oder spezieller befehlscontainer, wie z. B. eine Befehlsleiste, Befehlsleisten-Flyout, Menüleiste oder Dialogfeld platzieren.</span><span class="sxs-lookup"><span data-stu-id="c189b-125">You can place command elements on a number of surfaces in your app, including the app canvas or special command containers, such as a command bar, command bar flyout, menu bar, or dialog.</span></span>

<span data-ttu-id="c189b-126">Immer versuchen, damit Benutzer Inhalte nicht direkt manipulieren können, anstatt Befehle Sie über diese Handlung auf den Inhalt, z. B. ziehen und Ablegen Listenelementen Neuanordnen anstatt nach oben und unten Befehlsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="c189b-126">Always try to let users manipulate content directly rather than through commands that act on the content, such as dragging and dropping to rearrange list items rather than up and down command buttons.</span></span> 

<span data-ttu-id="c189b-127">Jedoch möglicherweise diese nicht möglich, mit der bestimmte Eingabegeräte oder bei bestimmten Benutzer Fähigkeiten und Voreinstellungen Berücksichtigung.</span><span class="sxs-lookup"><span data-stu-id="c189b-127">However, this might not be possible with certain input devices, or when accommodating specific user abilities and preferences.</span></span> <span data-ttu-id="c189b-128">Stellen Sie in diesen Fällen möglichst viele Steuerungselemente Angebote wie möglich bereit, und platzieren Sie diese Befehlselemente auf einer Befehlsoberfläche in Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="c189b-128">In these cases, provide as many commanding affordances as possible, and place these command elements on a command surface in your app.</span></span>

<span data-ttu-id="c189b-129">Hier eine Liste mit einigen der gängigsten Befehlsoberflächen.</span><span class="sxs-lookup"><span data-stu-id="c189b-129">Here's a list of some of the most common command surfaces.</span></span>

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

## <a name="provide-command-feedback"></a><span data-ttu-id="c189b-130">Befehl Feedback bereitstellen</span><span class="sxs-lookup"><span data-stu-id="c189b-130">Provide command feedback</span></span> 

<span data-ttu-id="c189b-131">Befehl Feedback kommuniziert für Benutzer, dass einer Interaktion oder eines Befehls erkannt wurde, wie es interpretiert und behandelt wurde, und gibt an, ob er erfolgreich oder nicht war.</span><span class="sxs-lookup"><span data-stu-id="c189b-131">Command feedback communicates to users that an interaction or command was detected, how it was interpreted and handled, and whether it was successful or not.</span></span> <span data-ttu-id="c189b-132">Dies hilft Benutzern, die wissen, was er getan hat und was er als Nächstes tun können.</span><span class="sxs-lookup"><span data-stu-id="c189b-132">This helps users understand what they've done, and what they can do next.</span></span> <span data-ttu-id="c189b-133">Im Idealfall sollte das Feedback natürlich in Ihre Benutzeroberfläche integriert werden, so dass Benutzer nicht unterbrochen werden müssen oder zusätzliche Maßnahmen ergreifen müssen, es sei denn, dies ist absolut notwendig.</span><span class="sxs-lookup"><span data-stu-id="c189b-133">Ideally, feedback should be integrated naturally in your UI, so users don't have to be interrupted, or take additional action unless absolutely necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="c189b-134">Geben Sie Feedback nicht, es sei denn, es absolut notwendig ist und das Feedback an anderer Stelle nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="c189b-134">Don't provide feedback unless it is absolutely necessary and the feedback is not available elsewhere.</span></span> <span data-ttu-id="c189b-135">Halten Sie die Benutzeroberfläche Ihrer Anwendung sauber und aufgeräumt, es sei denn, Sie Wert hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c189b-135">Keep your application UI clean and uncluttered unless you are adding value.</span></span>

<span data-ttu-id="c189b-136">Hier sind einige Möglichkeiten, um Feedback in Ihrer App bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="c189b-136">Here are some ways to provide feedback in your app.</span></span>

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

       <span data-ttu-id="c189b-137"><a href="../controls-and-patterns/dialogs-and-flyouts/index.md">Flyouts</a> sind einfache kontextbezogene Popups, die durch Antippen oder klicken außerhalb des Flyouts verworfen werden können.</span><span class="sxs-lookup"><span data-stu-id="c189b-137"><a href="../controls-and-patterns/dialogs-and-flyouts/index.md">Flyouts</a> are lightweight contextual popups that can be dismissed by tapping or clicking somewhere outside the flyout.</span></span>
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
> <span data-ttu-id="c189b-138">Verwenden Sie nicht zu viele Bestätigungsdialogfelder. Diese können zwar sehr hilfreich sein, wenn dem Benutzer ein Fehler unterläuft, bei bewusst durchgeführten Aktionen sind sie jedoch eher hinderlich.</span><span class="sxs-lookup"><span data-stu-id="c189b-138">Be careful of how much your app uses confirmation dialogs; they can be very helpful when the user makes a mistake, but they are a hindrance whenever the user is trying to perform an action intentionally.</span></span>

### <a name="when-to-confirm-or-undo-actions"></a><span data-ttu-id="c189b-139">Bestätigen oder Rückgängigmachen von Aktionen</span><span class="sxs-lookup"><span data-stu-id="c189b-139">When to confirm or undo actions</span></span>

<span data-ttu-id="c189b-140">Unabhängig davon, wie gut durchdachte ist der Benutzeroberfläche Ihrer Anwendung, alle Benutzer eine Aktion, die sie aufnehmen, dass sie hadn't ausführen.</span><span class="sxs-lookup"><span data-stu-id="c189b-140">No matter how well-designed your application's UI is, all users perform an action they wish they hadn't.</span></span> <span data-ttu-id="c189b-141">Durch die Verwendung der Bestätigung einer Aktion oder durch die Möglichkeit durchgeführten Aktionen rückgängig machen kann Ihre app in diesen Situationen helfen.</span><span class="sxs-lookup"><span data-stu-id="c189b-141">Your app can help in these situations by requiring confirmation of an action, or by providing a way to undo recent actions.</span></span>

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

##  <a name="optimize-for-specific-input-types"></a><span data-ttu-id="c189b-142">Optimieren für bestimmte Eingabearten</span><span class="sxs-lookup"><span data-stu-id="c189b-142">Optimize for specific input types</span></span>

<span data-ttu-id="c189b-143">Ausführliche Informationen zum Optimieren der Benutzerfreundlichkeit bei einem bestimmten Eingabetyp oder -gerät finden Sie unter [Einführung in die Interaktion](../input/index.md).</span><span class="sxs-lookup"><span data-stu-id="c189b-143">See the [Interaction primer](../input/index.md) for more detail on optimizing user experiences around a specific input type or device.</span></span>

