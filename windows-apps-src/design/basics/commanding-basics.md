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
#  <a name="command-design-basics-for-uwp-apps"></a>Befehlsdesigngrundlagen für UWP-Apps

Bei den *Befehlselementen* in einer Universellen Windows-Plattform (UWP)-App handelt es sich um die interaktiven Benutzeroberflächenelemente, mit denen der Benutzer Aktionen durchführen kann, um beispielsweise eine E-Mail zu senden, ein Element zu löschen oder ein Formular zu übermitteln. Dieser Artikel beschreibt allgemeine Befehlselemente, die von ihnen unterstützten Interaktionen und die Befehlsoberflächen für ihr Hosting.

## <a name="provide-the-right-type-of-interactions"></a>Bereitstellen geeigneter Interaktionen

Die wichtigste Entscheidung bei der Gestaltung einer Befehlsschnittstelle ist die Wahl der möglichen Benutzeraktionen. Um die richtige Art Interaktionen zu planen, konzentrieren Sie sich auf Ihre App – denken Sie daran, welche Benutzererfahrungen Sie ermöglichen möchten und welche Schritte die Benutzer unternehmen müssen. Sobald Sie entscheiden, was die Benutzer erreichen sollen, können Sie ihnen die entsprechenden Werkzeuge zur Verfügung stellen.

Einige Interaktionen für Ihre App sind:

- Senden oder Übermitteln von Informationen 
- Auswählen von Einstellungen und Auswahlmöglichkeiten
- Suchen und Filtern von Inhalten
- Öffnen, Speichern und Löschen von Dateien
- Inhalte bearbeiten oder erstellen

## <a name="use-the-right-command-element-for-the-interaction"></a>Verwenden Sie das richtige Befehlselement für die Interaktion

Die Verwendung der richtigen Elemente zur Befehlsinteraktionen kann den Unterschied zwischen einer intuitiven, benutzerfreundlichen App und einer schwierigen, verwirrenden App ausmachen. Die Universelle Windows-Plattform (UWP) bietet eine große Anzahl von Befehlselementen, die Sie in Ihrer App verwenden können. Die folgende Liste enthält einige der gängigsten Steuerelemente sowie eine Zusammenfassung der jeweils möglichen Interaktionen:

:::row::: :::column::: ![Bild mit Schaltfläche](images/commanding/thumbnail-button.svg) :::column-end::: :::column span="2"::: <b>Schaltflächen</b>

        <a href="../controls-and-patterns/buttons.md" style="text-decoration:none">Buttons</a> trigger an immediate action. Examples include sending an email, submitting form data, or confirming an action in a dialog.
:::row-end:::

:::row::: :::column::: ![Bild mit Liste](images/commanding/thumbnail-list.svg) :::column-end::: :::column span="2"::: <b>Listen</b>

        <a href="../controls-and-patterns/lists.md" style="text-decoration:none">Lists</a> present items in a interactive list or a grid. Usually used for many options or display items. Examples include drop-down list, list box, list view and grid view.
:::row-end:::

:::row::: :::column::: ![Bild mit Auswahlsteuerelement](images/commanding/thumbnail-selection.svg) :::column-end::: :::column span="2"::: <b>Auswahlsteuerelemente</b>

        Lets users choose from a few options, such as when completing a survey or configuring app settings. Examples include <a href="../controls-and-patterns/checkbox.md">check box</a>, <a href="../controls-and-patterns/radio-button.md">radio button</a>, and <a href="../controls-and-patterns/toggles.md">toggle switch</a>.
:::row-end:::

:::row::: :::column::: ![Bild mit Kalender](images/commanding/thumbnail-calendar.svg) :::column-end::: :::column span="2"::: <b>Kalender-, Datums- und Uhrzeitsteuerelemente</b>

        <a href="../controls-and-patterns/date-and-time.md">Calendar, date and time pickers</a> enable users to view and modify date and time info, such as when creating an event or setting an alarm. Examples include calendar date picker, calendar view, date picker, time picker.
:::row-end:::

:::row::: :::column::: ![Bild mit Feld mit automatischen Vorschläge](images/commanding/thumbnail-autosuggest.svg) :::column-end::: :::column span="2"::: <b>Eingabefeld mit automatischen Vorschlägen</b>

        Provides suggestions as users type, such as when entering data or performing queries. Examples include <a href="../controls-and-patterns/auto-suggest-box.md">auto-suggest box</a>.<br>
:::row-end:::

Eine vollständige Liste finden Sie unter [Steuerelemente und UI-Elemente](../controls-and-patterns/index.md).

##  <a name="place-commands-on-the-right-surface"></a>Platzieren von Befehlen auf der passenden Oberfläche
Sie können Befehlselemente auf einer Reihe von Oberflächen in Ihrer App platzieren, einschließlich der App-Canvas oder spezieller Befehlscontainer, wie Befehlsleisten, Menüs, Dialoge und Flyouts.

Beachten Sie, dass Sie den Benutzern möglichst erlauben sollten, Inhalte direkt zu manipulieren, anstatt Befehle zu verwenden, die auf den Inhalt wirken. Beispielsweise können Benutzer Listen durch Ziehen und Ablegen von Listenelementen neu anordnen, anstatt die Befehlsschaltflächen nach oben und unten zu verwenden.

Wenn Benutzer Inhalte aber nicht direkt manipulieren können, platzieren Sie Befehlselemente auf einer Befehlsoberfläche in Ihrer App: Hier eine Liste mit einigen der gängigsten Befehlsoberflächen.

:::row::: :::column::: ![Bild mit App-Inhaltsbereich](images/commanding/thumbnail-canvas.svg) :::column-end::: :::column span="2"::: <b>App-Inhaltsbereich</b>

        If a command is constantly needed for users to complete core scenarios, put it on the canvas. Because you can put commands near (or on) the objects they affect, putting commands on the canvas makes them easy and obvious to use. However, choose the commands you put on the canvas carefully. Too many commands on the app canvas take up valuable screen space and can overwhelm the user. If the command won't be frequently used, consider putting it in another command surface.
:::row-end:::

:::row::: :::column::: ![Bild mit Befehlsleiste](images/commanding/thumbnail-commandbar.svg) :::column-end::: :::column span="2"::: <b>Befehlsleisten</b>

        <a href="../controls-and-patterns/app-bars.md">Command bars</a> help organize commands and make them easy to access. Command bars can be placed at the top of the screen, at the bottom of the screen, or at both the top and bottom of the screen.
:::row-end:::

:::row::: :::column::: ![Bild mit Kontextmenü](images/commanding/thumbnail-contextmenu.svg) :::column-end::: :::column span="2"::: <b>Menüs und Kontextmenüs</b>

        Sometimes it is more efficient to group multiple commands into a command menu to save space. <a href="../controls-and-patterns/menus.md">Menus and context menus</a> display a list of commands or options when the user requests them. Context menus can provide shortcuts to commonly-used actions and provide access to secondary commands that are only relevant in certain contexts, such as clipboard or custom commands. Context menus are usually prompted by a user right-clicking.
:::row-end:::

## <a name="provide-feedback-for-interactions"></a>Reagieren auf Interaktionen durch Feedback

Feedback kommuniziert die Ergebnisse von Befehlen und ermöglicht dem Benutzer zu verstehen, was er getan hat und was er als nächstes tun kann. Im Idealfall sollte das Feedback natürlich in Ihre Benutzeroberfläche integriert werden, so dass Benutzer nicht unterbrochen werden müssen oder zusätzliche Maßnahmen ergreifen müssen, es sei denn, dies ist absolut notwendig. 

Hier sind einige Möglichkeiten, um Feedback in Ihrer App bereitzustellen.

:::row::: :::column::: ![Bild mit Befehlsleisten-Inhaltsbereich](images/commanding/thumbnail-commandbar2.svg) :::column-end::: :::column span="2"::: <b>Befehlsleiste</b>

        The content area of the <a href="../controls-and-patterns/app-bars.md">command bar</a> is an intuitive place to communicate status to users if they'd like to see feedback.
:::row-end:::

:::row::: :::column::: ![Bild mit Flyout](images/commanding/thumbnail-flyout.svg) :::column-end::: :::column span="2"::: <b>Flyouts</b>

       <a href="../controls-and-patterns/dialogs.md">Flyouts</a> are lightweight contextual popups that can be dismissed by tapping or clicking somewhere outside the flyout.
:::row-end:::

:::row::: :::column::: ![Bild mit Dialogfeld](images/commanding/thumbnail-dialog.svg) :::column-end::: :::column span="2"::: <b>Dialogfelder</b>

        <a href="../controls-and-patterns/dialogs.md">Dialog controls</a> are modal UI overlays that provide contextual app information. In most cases, dialogs block interactions with the app window until being explicitly dismissed, and often request some kind of action from the user. Dialogs can be disruptive and should only be used in certain situations. For more info, see the [When to confirm or undo actions](#when-to-confirm-or-undo-actions) section.
    :::column-end:::
:::row-end:::

> [!TIP]
> Verwenden Sie nicht zu viele Bestätigungsdialogfelder. Diese können zwar sehr hilfreich sein, wenn dem Benutzer ein Fehler unterläuft, bei bewusst durchgeführten Aktionen sind sie jedoch eher hinderlich.

### <a name="when-to-confirm-or-undo-actions"></a>Bestätigen oder Rückgängigmachen von Aktionen

Ganz gleich, wie gut die Benutzeroberfläche gestaltet ist und wie vorsichtig der Benutzer vorgeht: Irgendwann wird jeder Benutzer eine Aktion ausführen, die er lieber nicht ausgeführt hätte. In einer solchen Situation kann Ihre App dem Benutzer helfen, indem sie eine Aktionsbestätigung anfordert oder eine Möglichkeit zum Rückgängigmachen der kürzlich durchgeführten Aktionen anbietet.

:::row::: :::column::: ![Beispiel für „Richtig”](images/do.svg)

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

##  <a name="optimize-for-specific-input-types"></a>Optimieren für bestimmte Eingabearten

Ausführliche Informationen zum Optimieren der Benutzerfreundlichkeit bei einem bestimmten Eingabetyp oder -gerät finden Sie unter [Einführung in die Interaktion](../input/index.md).

