---
author: QuinnRadich
Description: Command bars give users easy access to your app's most common tasks.
title: Befehlsleiste
label: App bars/command bars
template: detail.hbs
op-migration-status: ready
ms.author: quradic
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: 868b4145-319b-4a97-82bd-c98d966144db
pm-contact: yulikl
design-contact: ksulliv
dev-contact: niallm
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: ce64e6002bd71bd0806fb5574dc404ac4df856a9
ms.sourcegitcommit: 4f6dc806229a8226894c55ceb6d6eab391ec8ab6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "4086025"
---
# <a name="command-bar"></a><span data-ttu-id="c1f27-103">Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="c1f27-103">Command bar</span></span>

<span data-ttu-id="c1f27-104">Über Befehlsleisten können Benutzer komfortabel auf häufig verwendete Befehle in Ihrer App zugreifen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-104">Command bars provide users with easy access to your app's most common tasks.</span></span> <span data-ttu-id="c1f27-105">Befehlsleisten ermöglichen den Zugriff auf App-Ebene oder seitenspezifische Befehle und können mit jedem Navigationsmuster verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-105">Command bars can provide access to app-level or page-specific commands and can be used with any navigation pattern.</span></span>

> <span data-ttu-id="c1f27-106">**Wichtige APIs:** [CommandBar-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.aspx), [AppBarButton-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbartogglebutton.aspx), [AppBarSeparator-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbarseparator.aspx)</span><span class="sxs-lookup"><span data-stu-id="c1f27-106">**Important APIs**: [CommandBar class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.aspx), [AppBarButton class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbartogglebutton.aspx), [AppBarSeparator class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbarseparator.aspx)</span></span>

![Beispiel für eine Befehlsleiste mit Symbolen](images/controls_appbar_icons.png)

## <a name="is-this-the-right-control"></a><span data-ttu-id="c1f27-108">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="c1f27-108">Is this the right control?</span></span>

<span data-ttu-id="c1f27-109">Das CommandBar-Steuerelement ist ein allgemeines, flexibles und kleines Steuerelement, mit dem komplexe Inhalte wie Bilder oder Textblöcke sowie einfache Befehle wie [AppBarButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbarbutton.aspx)-, [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbartogglebutton.aspx)- und [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbarseparator.aspx)-Steuerelemente angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="c1f27-109">The CommandBar control is a general-purpose, flexible, light-weight control that can display both complex content, such as images or text blocks, as well as simple commands such as [AppBarButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbartogglebutton.aspx), and [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.appbarseparator.aspx) controls.</span></span>

> [!NOTE]
<span data-ttu-id="c1f27-110">XAML stellt das [AppBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbar)-Steuerelement und das [CommandBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbar)-Steuerelement bereit.</span><span class="sxs-lookup"><span data-stu-id="c1f27-110">XAML provides both the [AppBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbar) control and the [CommandBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbar) control.</span></span> <span data-ttu-id="c1f27-111">Sie sollten AppBar nur verwenden, wenn Sie eine universelle Windows 8-App aktualisieren, in der AppBar verwendet wird, und möglichst wenige Änderungen vornehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="c1f27-111">You should use the AppBar only when you are upgrading a Universal Windows 8 app that uses the AppBar, and need to minimize changes.</span></span> <span data-ttu-id="c1f27-112">Für neue Apps in Windows 10 sollten Sie stattdessen das CommandBar-Steuerelement verwenden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-112">For new apps in Windows 10, we recommend using the CommandBar control instead.</span></span> <span data-ttu-id="c1f27-113">In diesem Dokument wird davon ausgegangen, dass Sie das CommandBar-Steuerelement verwenden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-113">This document assumes you are using the CommandBar control.</span></span>

## <a name="examples"></a><span data-ttu-id="c1f27-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c1f27-114">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="c1f27-115">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="c1f27-115">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="c1f27-116">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/CommandBar">die App zu öffnen und CommandBar in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="c1f27-116">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/CommandBar">open the app and see the CommandBar in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="c1f27-117">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="c1f27-117">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="c1f27-118">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="c1f27-118">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="c1f27-119">Eine erweiterte Befehlsleiste in der MicrosoftFotos-App.</span><span class="sxs-lookup"><span data-stu-id="c1f27-119">An expanded command bar in the Microsoft Photos app.</span></span>

![Befehlsleiste in der MicrosoftFotos-App](images/control-examples/command-bar-photos.png)

<span data-ttu-id="c1f27-121">Eine Befehlsleiste im Outlook-Kalender auf einem Windows Phone:</span><span class="sxs-lookup"><span data-stu-id="c1f27-121">A command bar in the Outlook Calendar on Windows Phone.</span></span>

![Befehlsleiste in der Outlook-Kalender-App](images/control-examples/command-bar-calendar-phone.png)

## <a name="anatomy"></a><span data-ttu-id="c1f27-123">Aufbau</span><span class="sxs-lookup"><span data-stu-id="c1f27-123">Anatomy</span></span>

<span data-ttu-id="c1f27-124">Standardmäßig werden auf der Befehlsleiste eine Reihe von Symbolschaltflächen und eine optionale, durch drei Punkte (\[•••\]) dargestellte Schaltfläche für weitere Optionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1f27-124">By default, the command bar shows a row of icon buttons and an optional "see more" button, which is represented by an ellipsis \[•••\].</span></span> <span data-ttu-id="c1f27-125">Dies ist die Befehlsleiste, die mit dem weiter unten gezeigten Beispielcode erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="c1f27-125">Here's the command bar created by the example code shown later.</span></span> <span data-ttu-id="c1f27-126">Hier ist der geschlossene, kompakte Zustand zu sehen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-126">It's shown in its closed compact state.</span></span>

![Geschlossene Befehlsleiste](images/command-bar-compact.png)

<span data-ttu-id="c1f27-128">Die Befehlsleiste kann auch im geschlossenen, minimierten Zustand angezeigt werden, die wie folgt aussieht.</span><span class="sxs-lookup"><span data-stu-id="c1f27-128">The command bar can also be shown in a closed minimal state that looks like this.</span></span> <span data-ttu-id="c1f27-129">Weitere Informationen finden Sie im Abschnitt [Geöffneter und geschlossener Zustand](#open-and-closed-states).</span><span class="sxs-lookup"><span data-stu-id="c1f27-129">See the [Open and closed states](#open-and-closed-states) section for more info.</span></span>

![Geschlossene Befehlsleiste](images/command-bar-minimal.png)

<span data-ttu-id="c1f27-131">Dies ist die gleiche Befehlsleiste im geöffneten Zustand.</span><span class="sxs-lookup"><span data-stu-id="c1f27-131">Here's the same command bar in its open state.</span></span> <span data-ttu-id="c1f27-132">Die Beschriftungen zeigen die wichtigsten Elemente des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="c1f27-132">The labels identify the main parts of the control.</span></span>

![Geschlossene Befehlsleiste](images/commandbar_anatomy_open.png)

<span data-ttu-id="c1f27-134">Die Befehlsleiste ist in 4 Hauptbereiche unterteilt:</span><span class="sxs-lookup"><span data-stu-id="c1f27-134">The command bar is divided into 4 main areas:</span></span>
- <span data-ttu-id="c1f27-135">Der Inhaltsbereich wird an der linken Seite der Leiste ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="c1f27-135">The content area is aligned to the left side of the bar.</span></span> <span data-ttu-id="c1f27-136">Er wird angezeigt, wenn die Eigenschaft [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx) gefüllt ist.</span><span class="sxs-lookup"><span data-stu-id="c1f27-136">It is shown if the [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx) property is populated.</span></span>
- <span data-ttu-id="c1f27-137">Der Bereich für primäre Befehle wird an der rechten Seite der Leiste ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="c1f27-137">The primary command area is aligned to the right side of the bar.</span></span> <span data-ttu-id="c1f27-138">Er wird angezeigt, wenn die Eigenschaft [PrimaryCommands](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.primarycommands.aspx) gefüllt ist.</span><span class="sxs-lookup"><span data-stu-id="c1f27-138">It is shown if the [PrimaryCommands](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.primarycommands.aspx) property is populated.</span></span>  
- <span data-ttu-id="c1f27-139">Die Schaltfläche für weitere Optionen (\[•••\]) wird rechts auf der Leiste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1f27-139">The "see more" \[•••\] button is shown on the right of the bar.</span></span> <span data-ttu-id="c1f27-140">Durch Klicken auf die Schaltfläche „Weitere Informationen“ (\[• • •]) werden primäre Befehlsbezeichnungen angezeigt und wird das Überlaufmenü geöffnet, wenn sekundäre Befehle vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="c1f27-140">Pressing the "see more" \[•••\] button reveals primary command labels and opens the overflow menu if there are secondary commands.</span></span> <span data-ttu-id="c1f27-141">Die Schaltfläche wird nicht angezeigt, wenn keine primären oder sekundären Befehlsbezeichnungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="c1f27-141">The button will not be visible when no primary command labels or secondary labels are present.</span></span> <span data-ttu-id="c1f27-142">Dieses Standardverhalten können Sie mit der [OverflowButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.overflowbuttonvisibility.aspx)-Eigenschaft ändern.</span><span class="sxs-lookup"><span data-stu-id="c1f27-142">To change default behavior, use the [OverflowButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.overflowbuttonvisibility.aspx) property.</span></span>
- <span data-ttu-id="c1f27-143">Das Überlaufmenü wird nur angezeigt, wenn die Befehlsleiste geöffnet ist und die Eigenschaft [SecondaryCommands](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.secondarycommands.aspx) befüllt ist.</span><span class="sxs-lookup"><span data-stu-id="c1f27-143">The overflow menu is shown only when the command bar is open and the [SecondaryCommands](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.secondarycommands.aspx) property is populated.</span></span> <span data-ttu-id="c1f27-144">Wenn der Platz begrenzt ist, werden primäre Befehle in den SecondaryCommands-Bereich verschoben.</span><span class="sxs-lookup"><span data-stu-id="c1f27-144">When space is limited, primary commands will move into the SecondaryCommands area.</span></span> <span data-ttu-id="c1f27-145">Dieses Standardverhalten können Sie mit der [IsDynamicOverflowEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.isdynamicoverflowenabled.aspx)-Eigenschaft ändern.</span><span class="sxs-lookup"><span data-stu-id="c1f27-145">To change default behavior, use the [IsDynamicOverflowEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.isdynamicoverflowenabled.aspx) property.</span></span>

<span data-ttu-id="c1f27-146">Das Layout wird umgekehrt, wenn [FlowDirection](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.flowdirection.aspx) auf **RightToLeft** festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="c1f27-146">The layout is reversed when the [FlowDirection](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.flowdirection.aspx) is **RightToLeft**.</span></span>

## <a name="create-a-command-bar"></a><span data-ttu-id="c1f27-147">Erstellen einer Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="c1f27-147">Create a command bar</span></span>
<span data-ttu-id="c1f27-148">Mit folgendem Beispiel wird die oben gezeigte Befehlsleiste erstellt.</span><span class="sxs-lookup"><span data-stu-id="c1f27-148">This example creates the command bar shown previously.</span></span>

```xaml
<CommandBar>
    <AppBarToggleButton Icon="Shuffle" Label="Shuffle" Click="AppBarButton_Click" />
    <AppBarToggleButton Icon="RepeatAll" Label="Repeat" Click="AppBarButton_Click"/>
    <AppBarSeparator/>
    <AppBarButton Icon="Back" Label="Back" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Stop" Label="Stop" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Play" Label="Play" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Forward" Label="Forward" Click="AppBarButton_Click"/>

    <CommandBar.SecondaryCommands>
        <AppBarButton Label="Like" Click="AppBarButton_Click"/>
        <AppBarButton Label="Dislike" Click="AppBarButton_Click"/>
    </CommandBar.SecondaryCommands>

    <CommandBar.Content>
        <TextBlock Text="Now playing..." Margin="12,14"/>
    </CommandBar.Content>
</CommandBar>
```

## <a name="commands-and-content"></a><span data-ttu-id="c1f27-149">Befehle und Inhalt</span><span class="sxs-lookup"><span data-stu-id="c1f27-149">Commands and content</span></span>
<span data-ttu-id="c1f27-150">Das Steuerelement „CommandBar“ verfügt über drei Eigenschaften, mit denen Sie Befehle und Inhalte hinzufügen können: [PrimaryCommands](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.primarycommands.aspx), [SecondaryCommands](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.secondarycommands.aspx) und [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx).</span><span class="sxs-lookup"><span data-stu-id="c1f27-150">The CommandBar control has 3 properties you can use to add commands and content: [PrimaryCommands](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.primarycommands.aspx), [SecondaryCommands](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.secondarycommands.aspx), and [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx).</span></span>


### <a name="commands"></a><span data-ttu-id="c1f27-151">Befehle</span><span class="sxs-lookup"><span data-stu-id="c1f27-151">Commands</span></span>

<span data-ttu-id="c1f27-152">Befehlsleistenelemente werden standardmäßig der **PrimaryCommands**-Sammlung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c1f27-152">By default, command bar items are added to the **PrimaryCommands** collection.</span></span> <span data-ttu-id="c1f27-153">Sie sollten Befehle nach ihrer Wichtigkeit hinzufügen, damit die wichtigsten Befehle immer sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="c1f27-153">You should add commands in order of their importance so that the most important commands are always visible.</span></span> <span data-ttu-id="c1f27-154">Wenn die Breite der Befehlsleiste geändert wird, z.B. wenn Benutzer die Größe des App-Fensters ändern, werden primäre Befehle dynamisch zwischen der Befehlsleiste und dem Überlaufmenü an Haltepunkten verschoben.</span><span class="sxs-lookup"><span data-stu-id="c1f27-154">When the command bar width changes, such as when users resize their app window, primary commands dynamically move between the command bar and the overflow menu at breakpoints.</span></span> <span data-ttu-id="c1f27-155">Dieses Standardverhalten können Sie mit der [IsDynamicOverflowEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.isdynamicoverflowenabled.aspx)-Eigenschaft ändern.</span><span class="sxs-lookup"><span data-stu-id="c1f27-155">To change this default behavior, use the [IsDynamicOverflowEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.isdynamicoverflowenabled.aspx) property.</span></span> 

<span data-ttu-id="c1f27-156">Auf sehr kleinen Bildschirmen (Breite: 320epx) passen maximal vier primäre Befehle in die Befehlsleiste.</span><span class="sxs-lookup"><span data-stu-id="c1f27-156">On the smallest screens (320 epx width), a maximum of 4 primary commands fit in the command bar.</span></span> 

<span data-ttu-id="c1f27-157">Sie können der **SecondaryCommands**-Sammlung auch Befehle hinzufügen, die im Überlaufmenü angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-157">You can also add commands to the **SecondaryCommands** collection, which are shown in the overflow menu.</span></span>

![Beispiel für eine Befehlsleiste mit einem Bereich für weitere Optionen inklusive Symbolen](images/appbar_rs2_overflow_icons.png)

<span data-ttu-id="c1f27-159">Bei Bedarf können Befehle programmgesteuert zwischen „PrimaryCommands“ und „SecondaryCommands“ verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-159">You can programmatically move commands between the PrimaryCommands and SecondaryCommands as needed.</span></span>

- *<span data-ttu-id="c1f27-160">Ein Befehl, der für mehrere Seiten einheitlich angezeigt wird, sollte immer an der gleichen Stelle platziert werden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-160">If there is a command that would appear consistently across pages, it's best to keep that command in a consistent location.</span></span>*
- *<span data-ttu-id="c1f27-161">Es wird empfohlen, die Befehle „Akzeptieren“, „Ja“ und „OK“ links von den Befehlen „Ablehnen“, „Nein“ und „Abbrechen“ zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="c1f27-161">We recommended placing Accept, Yes, and OK commands to the left of Reject, No, and Cancel.</span></span> <span data-ttu-id="c1f27-162">Konsistenz trägt dazu bei, dass Benutzern die App vertraut ist und sie ihre App-Navigationskenntnisse von einer App auf andere Apps übertragen können.</span><span class="sxs-lookup"><span data-stu-id="c1f27-162">Consistency gives users the confidence to move around the system and helps them transfer their knowledge of app navigation from app to app.</span></span>*

### <a name="app-bar-buttons"></a><span data-ttu-id="c1f27-163">App-Leistenschaltflächen</span><span class="sxs-lookup"><span data-stu-id="c1f27-163">App bar buttons</span></span>

<span data-ttu-id="c1f27-164">„PrimaryCommands“ und „SecondaryCommands“ können nur mit Befehlselementen vom Typ [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx), and [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) gefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-164">Both the PrimaryCommands and SecondaryCommands can be populated only with [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx), and [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) command elements.</span></span> 

<span data-ttu-id="c1f27-165">Die Steuerelemente für die App-Leistenschaltfläche zeichnen sich durch ein Symbol und eine Textbeschriftung aus.</span><span class="sxs-lookup"><span data-stu-id="c1f27-165">The app bar button controls are characterized by an icon and text label.</span></span> <span data-ttu-id="c1f27-166">Diese Steuerelemente sind für die Verwendung in Befehlsleisten optimiert, und ihr Erscheinungsbild verändert sich abhängig davon, ob das Steuerelement in der Befehlsleiste oder im Überlaufmenü verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c1f27-166">These controls are optimized for use in a command bar, and their appearance changes depending on whether the control is used in the command bar or the overflow menu.</span></span>

<span data-ttu-id="c1f27-167">Die Symbole im Überlaufmenü sind 16×16px groß und damit kleiner als die Symbole im Bereich für primäre Befehle (20×20px).</span><span class="sxs-lookup"><span data-stu-id="c1f27-167">The size of the icons in the overflow menu is 16x16px, which is smaller than the icons in the primary command area (which are 20x20px).</span></span> <span data-ttu-id="c1f27-168">Wenn Sie „SymbolIcon“, „FontIcon“ oder „PathIcon“ verwenden, wird das Symbol automatisch und ohne Qualitätsverlust auf die richtige Größe skaliert, sobald der Befehl in den Bereich für sekundäre Befehle verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="c1f27-168">If you use SymbolIcon, FontIcon, or PathIcon, the icon will automatically scale to the correct size with no loss of fidelity when the command enters the secondary command area.</span></span> 

### <a name="button-labels"></a><span data-ttu-id="c1f27-169">Schaltflächenbeschriftungen</span><span class="sxs-lookup"><span data-stu-id="c1f27-169">Button labels</span></span>
<span data-ttu-id="c1f27-170">Mithilfe der Appbarbutton- Eigenschaft [IsCompact](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton.IsCompact) wird festgelegt, ob die Bezeichnung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c1f27-170">The AppBarButton [IsCompact](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.appbarbutton.IsCompact) property determines whether the label is shown.</span></span> <span data-ttu-id="c1f27-171">In einem CommandBar-Steuerelement überschreibt die Befehlsleiste automatisch die IsCompact-Eigenschaft der Schaltfläche, wenn die Befehlsleiste geöffnet und geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="c1f27-171">In a CommandBar control, the command bar overwrites the button's IsCompact property automatically as the command bar is opened and closed.</span></span>

<span data-ttu-id="c1f27-172">Verwenden Sie zum Positionieren von App-Leistenschaltflächen die [DefaultLabelPosition](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.defaultlabelposition.aspx)-Eigenschaft von CommandBar.</span><span class="sxs-lookup"><span data-stu-id="c1f27-172">To position app bar button labels, use CommandBar's [DefaultLabelPosition](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.defaultlabelposition.aspx) property.</span></span>

```xaml
<CommandBar DefaultLabelPosition="Right">
    <AppBarToggleButton Icon="Shuffle" Label="Shuffle"/>
    <AppBarToggleButton Icon="RepeatAll" Label="Repeat"/>
</CommandBar>
```

![Befehlsleiste mit Beschriftungen auf der rechten Seite](images/app-bar-labels-on-right.png)

<span data-ttu-id="c1f27-174">In größeren Fenstern können Sie zur Verbesserung der Lesbarkeit Beschriftungen rechts neben die Symbole der App-Leistenschaltflächen verschieben.</span><span class="sxs-lookup"><span data-stu-id="c1f27-174">On larger windows, consider moving labels to the right of app bar button icons to improve legibility.</span></span> <span data-ttu-id="c1f27-175">Bei Beschriftungen, die sich unten befinden, müssen Benutzer die Befehlsleiste öffnen, um die Beschriftungen anzuzeigen. Beschriftungen auf der rechten Seite werden auch angezeigt, wenn die Befehlsleiste geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="c1f27-175">Labels on the bottom require users to open the command bar to reveal labels, while labels on the right are visible even when command bar is closed.</span></span>

<span data-ttu-id="c1f27-176">In Überlaufmenüs werden Beschriftungen standardmäßig rechts von Symbolen positioniert und **LabelPosition** wird ignoriert.</span><span class="sxs-lookup"><span data-stu-id="c1f27-176">In overflow menus, labels are positioned to the right of icons by default, and **LabelPosition** is ignored.</span></span> <span data-ttu-id="c1f27-177">Sie können das Format anpassen, indem Sie in der Eigenschaft [CommandBarOverflowPresenterStyle](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.CommandBar.CommandBarOverflowPresenterStyle) ein Format für die Klasse [CommandBarOverflowPresenter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbaroverflowpresenter) angeben.</span><span class="sxs-lookup"><span data-stu-id="c1f27-177">You can adjust the styling by setting the [CommandBarOverflowPresenterStyle](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.CommandBar.CommandBarOverflowPresenterStyle) property to a Style that targets the [CommandBarOverflowPresenter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbaroverflowpresenter).</span></span> 

<span data-ttu-id="c1f27-178">Schaltflächenbeschriftungen sollten kurz sein (vorzugsweise ein einzelnes Wort).</span><span class="sxs-lookup"><span data-stu-id="c1f27-178">Button labels should be short, preferably a single word.</span></span> <span data-ttu-id="c1f27-179">Längere Beschriftungen unter einem Symbol werden auf mehrere Zeilen umgebrochen, wodurch die geöffnete Befehlsleiste insgesamt höher wird.</span><span class="sxs-lookup"><span data-stu-id="c1f27-179">Longer labels below an icon will wrap to multiple lines, increasing the overall height of the opened command bar.</span></span> <span data-ttu-id="c1f27-180">Sie können im Text für eine Beschriftung einen bedingten Trennstrich (0x00AD) einfügen, um die Stelle anzugeben, an der der Zeilenumbruch erfolgen soll.</span><span class="sxs-lookup"><span data-stu-id="c1f27-180">You can include a soft-hyphen character (0x00AD) in the text for a label to hint at the character boundary where a word break should occur.</span></span> <span data-ttu-id="c1f27-181">In XAML können Sie dies wie folgt mit einer Escapesequenz ausdrücken:</span><span class="sxs-lookup"><span data-stu-id="c1f27-181">In XAML, you express this using an escape sequence, like this:</span></span>

```xaml
<AppBarButton Icon="Back" Label="Areally&#x00AD;longlabel"/>
```

<span data-ttu-id="c1f27-182">Wenn die Beschriftung an der angegebenen Stelle umgebrochen wird, sieht dies wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="c1f27-182">When the label wraps at the hinted location, it looks like this.</span></span>

![App-Leistenschaltfläche mit umgebrochener Beschriftung](images/app-bar-button-label-wrap.png)

### <a name="command-bar-flyouts"></a><span data-ttu-id="c1f27-184">Flyouts auf einer Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="c1f27-184">Command bar flyouts</span></span>

<span data-ttu-id="c1f27-185">Ziehen Sie logische Gruppierungen für die Befehle in Erwägung. Platzieren Sie z.B. die Befehle „Antworten“, „Allen antworten“ und „Weiterleiten“ im Menü „Antworten“.</span><span class="sxs-lookup"><span data-stu-id="c1f27-185">Consider logical groupings for the commands, such as placing Reply, Reply All, and Forward in a Respond menu.</span></span> <span data-ttu-id="c1f27-186">Mit einer App-Leistenschaltfläche wird zwar üblicherweise ein einzelner Befehl aktiviert, sie kann jedoch auch zum Anzeigen eines [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.menuflyout.aspx)- oder [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flyout.aspx)-Elements mit benutzerdefiniertem Inhalt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-186">While typically an app bar button activates a single command, an app bar button can be used to show a [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.menuflyout.aspx) or [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flyout.aspx) with custom content.</span></span>

![Beispiel für Flyouts auf einer Befehlsleiste](images/AppbarGuidelines_Flyouts.png)

### <a name="other-content"></a><span data-ttu-id="c1f27-188">Andere Inhalte</span><span class="sxs-lookup"><span data-stu-id="c1f27-188">Other content</span></span>

<span data-ttu-id="c1f27-189">Sie können dem Inhaltsbereich beliebige XAML-Elemente hinzufügen, indem Sie die **Content**-Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-189">You can add any XAML elements to the content area by setting the **Content** property.</span></span> <span data-ttu-id="c1f27-190">Wenn Sie mehrere Elemente hinzufügen möchten, müssen Sie sie in einem Panel-Container platzieren und das Panel als einziges untergeordnetes Element der Content-Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-190">If you want to add more than one element, you need to place them in a panel container and make the panel the single child of the Content property.</span></span>

<span data-ttu-id="c1f27-191">Wenn der dynamische Überlauf aktiviert ist, wird der Inhalt nicht abgeschnitten, da die primären Befehle in das Überlaufmenü verschoben werden können.</span><span class="sxs-lookup"><span data-stu-id="c1f27-191">When dynamic overflow is enabled, content will not clip because primary commands can move into the overflow menu.</span></span> <span data-ttu-id="c1f27-192">Andernfalls haben primäre Befehle Vorrang und können dazu führen, dass der Inhalt abgeschnitten wird.</span><span class="sxs-lookup"><span data-stu-id="c1f27-192">Otherwise, primary commands take precedence and may cause the content to be clipped.</span></span>

<span data-ttu-id="c1f27-193">Wenn [ClosedDisplayMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.closeddisplaymode.aspx) auf **Compact** festgelegt wurde, kann der Inhalt abgeschnitten werden, wenn er größer als die kompakte Größe der Befehlsleiste ist.</span><span class="sxs-lookup"><span data-stu-id="c1f27-193">When the [ClosedDisplayMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.closeddisplaymode.aspx) is **Compact**, the content can be clipped if it is larger than the compact size of the command bar.</span></span> <span data-ttu-id="c1f27-194">Behandeln Sie das [Opening](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.opening.aspx)-Ereignis und das [Closed](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.closed.aspx)-Ereignis, um Teile der Benutzeroberfläche im Inhaltsbereich anzuzeigen oder auszublenden, damit sie nicht beschnitten werden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-194">You should handle the [Opening](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.opening.aspx) and [Closed](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.closed.aspx) events to show or hide parts of the UI in the content area so that they aren't clipped.</span></span> <span data-ttu-id="c1f27-195">Weitere Informationen finden Sie im Abschnitt [Geöffneter und geschlossener Zustand](#open-and-closed-states).</span><span class="sxs-lookup"><span data-stu-id="c1f27-195">See the [Open and closed states](#open-and-closed-states) section for more info.</span></span>


## <a name="open-and-closed-states"></a><span data-ttu-id="c1f27-196">Geöffneter und geschlossener Zustand</span><span class="sxs-lookup"><span data-stu-id="c1f27-196">Open and closed states</span></span>

<span data-ttu-id="c1f27-197">Die Befehlsleiste kann geöffnet oder geschlossen sein.</span><span class="sxs-lookup"><span data-stu-id="c1f27-197">The command bar can be open or closed.</span></span> <span data-ttu-id="c1f27-198">Im geöffneten Zustand werden die primären Befehlsschaltflächen mit Beschriftungen angezeigt, und das Überlaufmenü ist geöffnet, wenn sekundäre Befehle vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="c1f27-198">When open, the primary command buttons are shown with text labels, and the overflow menu is open if secondary commands are present.</span></span>

<span data-ttu-id="c1f27-199">Der Benutzer kann mit der Schaltfläche für weitere Optionen (\[•••\]) zwischen diesen Zuständen wechseln.</span><span class="sxs-lookup"><span data-stu-id="c1f27-199">A user can switch between these states by pressing the "see more" \[•••\] button.</span></span> <span data-ttu-id="c1f27-200">Sie können programmgesteuert zwischen den Zuständen wechseln, indem Sie einen Wert für die Eigenschaft [IsOpen](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.isopen.aspx) festlegen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-200">You can switch between them programmatically by setting the [IsOpen](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.isopen.aspx) property.</span></span> 

<span data-ttu-id="c1f27-201">Sie können die Ereignisse [Opening](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.opening.aspx), [Opened](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.opened.aspx), [Closing](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.closing.aspx) und [Closed](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.closed.aspx) nutzen, um auf das Öffnen und Schließen der Befehlsleiste zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="c1f27-201">You can use the [Opening](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.opening.aspx), [Opened](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.opened.aspx), [Closing](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.closing.aspx), and [Closed](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.closed.aspx) events to respond to the command bar being opened or closed.</span></span>  
- <span data-ttu-id="c1f27-202">Das Opening-Ereignis und das Closing-Ereignis treten vor Beginn der Übergangsanimation ein.</span><span class="sxs-lookup"><span data-stu-id="c1f27-202">The Opening and Closing events occur before the transition animation begins.</span></span>
- <span data-ttu-id="c1f27-203">Das Opened-Ereignis und das Closed-Ereignis treten nach Abschluss des Übergangs ein.</span><span class="sxs-lookup"><span data-stu-id="c1f27-203">The Opened and Closed events occur after the transition completes.</span></span>

<span data-ttu-id="c1f27-204">In diesem Beispiel wird mit dem Opening-Ereignis und dem Closing-Ereignis die Deckkraft der Befehlsleiste geändert.</span><span class="sxs-lookup"><span data-stu-id="c1f27-204">In this example, the Opening and Closing events are used to change the opacity of the command bar.</span></span> <span data-ttu-id="c1f27-205">Im geschlossenen Zustand ist die Befehlsleiste halbtransparent, sodass der Hintergrund der App durchscheint.</span><span class="sxs-lookup"><span data-stu-id="c1f27-205">When the command bar is closed, it's semi-transparent so the app background shows through.</span></span> <span data-ttu-id="c1f27-206">Wenn die Befehlsleiste geöffnet wird, wird sie undurchsichtig, damit der Benutzer sich auf die Befehle konzentrieren kann.</span><span class="sxs-lookup"><span data-stu-id="c1f27-206">When the command bar is opened, the command bar is made opaque so the user can focus on the commands.</span></span>

```xaml
<CommandBar Opening="CommandBar_Opening"
            Closing="CommandBar_Closing">
    <AppBarButton Icon="Accept" Label="Accept"/>
    <AppBarButton Icon="Edit" Label="Edit"/>
    <AppBarButton Icon="Save" Label="Save"/>
    <AppBarButton Icon="Cancel" Label="Cancel"/>
</CommandBar>
```

```csharp
private void CommandBar_Opening(object sender, object e)
{
    CommandBar cb = sender as CommandBar;
    if (cb != null) cb.Background.Opacity = 1.0;
}

private void CommandBar_Closing(object sender, object e)
{
    CommandBar cb = sender as CommandBar;
    if (cb != null) cb.Background.Opacity = 0.5;
}

```

### <a name="issticky"></a><span data-ttu-id="c1f27-207">IsSticky</span><span class="sxs-lookup"><span data-stu-id="c1f27-207">IsSticky</span></span>

<span data-ttu-id="c1f27-208">Wenn ein Benutzer bei geöffneter Befehlsleiste mit anderen Teilen einer App interagiert, wird die Befehlsleiste automatisch geschlossen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-208">If a user interacts with other parts of an app when a command bar is open, then the command bar will automatically close.</span></span> <span data-ttu-id="c1f27-209">Dies wird als *einfaches Ausblenden* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c1f27-209">This is called *light dismiss*.</span></span> <span data-ttu-id="c1f27-210">Sie können das Verhalten für einfaches Ausblenden steuern, indem Sie einen Wert für die Eigenschaft [IsSticky](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.issticky.aspx) festlegen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-210">You can control light dismiss behavior by setting the [IsSticky](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.issticky.aspx) property.</span></span> <span data-ttu-id="c1f27-211">Bei `IsSticky="true"` bleibt die Leiste geöffnet, bis der Benutzer auf die Schaltfläche für weitere Optionen (\[•••\]) klickt oder ein Menüelement im Überlaufmenü auswählt.</span><span class="sxs-lookup"><span data-stu-id="c1f27-211">When `IsSticky="true"`, the bar remains open until the user presses the "see more" \[•••\] button or selects an item from the overflow menu.</span></span> 

<span data-ttu-id="c1f27-212">Es wird empfohlen, eingerastete Befehlsleisten zu vermeiden, da sie nicht den Benutzererwartungen an das einfache Ausblenden entsprechen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-212">We recommend avoiding sticky command bars because they don't conform to users' expectations around light dismiss.</span></span>

### <a name="display-mode"></a><span data-ttu-id="c1f27-213">Anzeigemodus</span><span class="sxs-lookup"><span data-stu-id="c1f27-213">Display Mode</span></span>

<span data-ttu-id="c1f27-214">Sie können steuern, wie die Befehlsleiste im geschlossenen Zustand angezeigt wird, indem Sie einen Wert für die Eigenschaft [ClosedDisplayMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.closeddisplaymode.aspx) festlegen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-214">You can control how the command bar is shown in its closed state by setting the [ClosedDisplayMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.closeddisplaymode.aspx) property.</span></span> <span data-ttu-id="c1f27-215">Sie können aus drei Anzeigemodi für den geschlossenen Zustand auswählen:</span><span class="sxs-lookup"><span data-stu-id="c1f27-215">There are 3 closed display modes to choose from:</span></span>
- <span data-ttu-id="c1f27-216">**Kompakt**: Standardmodus.</span><span class="sxs-lookup"><span data-stu-id="c1f27-216">**Compact**: The default mode.</span></span> <span data-ttu-id="c1f27-217">Hiermit werden der Inhalt, primäre Befehlssymbole ohne Beschriftungen und die Schaltfläche für weitere Optionen (\[•••\]) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1f27-217">Shows content, primary command icons without labels, and the "see more" \[•••\] button.</span></span>
- <span data-ttu-id="c1f27-218">**Minimal**: Hiermit wird nur eine dünne Leiste angezeigt, die als Schaltfläche für weitere Optionen (\[•••\]) fungiert.</span><span class="sxs-lookup"><span data-stu-id="c1f27-218">**Minimal**: Shows only a thin bar that acts as the "see more" \[•••\] button.</span></span> <span data-ttu-id="c1f27-219">Der Benutzer kann auf eine beliebige Stelle auf der Leiste tippen, um sie zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-219">The user can press anywhere on the bar to open it.</span></span>
- <span data-ttu-id="c1f27-220">**Ausgeblendet**: Die Befehlsleiste wird nicht angezeigt, wenn sie geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="c1f27-220">**Hidden**: The command bar is not shown when it's closed.</span></span> <span data-ttu-id="c1f27-221">Dies kann hilfreich beim Anzeigen von Kontextbefehlen mit einer Inlinebefehlsleiste sein.</span><span class="sxs-lookup"><span data-stu-id="c1f27-221">This can be useful for showing contextual commands with an inline command bar.</span></span> <span data-ttu-id="c1f27-222">In diesem Fall müssen Sie die Befehlsleiste programmgesteuert öffnen, indem Sie die **IsOpen**-Eigenschaft festlegen oder ClosedDisplayMode auf **Minimal** oder **Compact** festlegen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-222">In this case, you must open the command bar programmatically by setting the **IsOpen** property or changing the ClosedDisplayMode to **Minimal** or **Compact**.</span></span>

<span data-ttu-id="c1f27-223">Hier enthält eine Befehlsleiste einfache Formatierungsbefehle für eine [RichEditBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx).</span><span class="sxs-lookup"><span data-stu-id="c1f27-223">Here, a command bar is used to hold simple formatting commands for a [RichEditBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx).</span></span> <span data-ttu-id="c1f27-224">Wenn das Bearbeitungsfeld nicht den Fokus besitzt, können die Formatierungsbefehle störend sein, daher werden sie ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="c1f27-224">When the edit box doesn't have focus, the formatting commands can be distracting, so they're hidden.</span></span> <span data-ttu-id="c1f27-225">Wenn das Bearbeitungsfeld verwendet wird, wird ClosedDisplayMode für die Befehlsleiste in „Compact“ geändert, sodass die Formatierungsbefehle angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-225">When the edit box is being used, the command bar's ClosedDisplayMode is changed to Compact so the formatting commands are visible.</span></span>

```xaml
<StackPanel Width="300"
            GotFocus="EditStackPanel_GotFocus"
            LostFocus="EditStackPanel_LostFocus">
    <CommandBar x:Name="FormattingCommandBar" ClosedDisplayMode="Hidden">
        <AppBarButton Icon="Bold" Label="Bold" ToolTipService.ToolTip="Bold"/>
        <AppBarButton Icon="Italic" Label="Italic" ToolTipService.ToolTip="Italic"/>
        <AppBarButton Icon="Underline" Label="Underline" ToolTipService.ToolTip="Underline"/>
    </CommandBar>
    <RichEditBox Height="200"/>
</StackPanel>
```

```csharp
private void EditStackPanel_GotFocus(object sender, RoutedEventArgs e)
{
    FormattingCommandBar.ClosedDisplayMode = AppBarClosedDisplayMode.Compact;
}

private void EditStackPanel_LostFocus(object sender, RoutedEventArgs e)
{
    FormattingCommandBar.ClosedDisplayMode = AppBarClosedDisplayMode.Hidden;
}
```

><span data-ttu-id="c1f27-226">**Hinweis**&nbsp;&nbsp;Die Implementierung von Bearbeitungsbefehlen geht über den Rahmen dieses Beispiels hinaus.</span><span class="sxs-lookup"><span data-stu-id="c1f27-226">**Note**&nbsp;&nbsp;The implementation of the editing commands is beyond the scope of this example.</span></span> <span data-ttu-id="c1f27-227">Weitere Informationen finden Sie im Artikel zu [RichEditBox](rich-edit-box.md).</span><span class="sxs-lookup"><span data-stu-id="c1f27-227">For more info, see the [RichEditBox](rich-edit-box.md) article.</span></span>

<span data-ttu-id="c1f27-228">Auch wenn die Modi „Minimal“ und „Hidden“ in einigen Situationen nützlich sind, beachten Sie, dass es für die Benutzer verwirrend sein kann, wenn alle Aktionen ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-228">Although the Minimal and Hidden modes are useful in some situations, keep in mind that hiding all actions could confuse users.</span></span>

<span data-ttu-id="c1f27-229">Das Ändern von ClosedDisplayMode, um mehr oder weniger Informationen für die Benutzer bereitzustellen, hat Auswirkungen auf das Layout der umgebenden Elemente.</span><span class="sxs-lookup"><span data-stu-id="c1f27-229">Changing the ClosedDisplayMode to provide more or less of a hint to the user affects the layout of surrounding elements.</span></span> <span data-ttu-id="c1f27-230">Das Wechseln zwischen dem geschlossenen und geöffneten Zustand von CommandBar hat hingegen keine Auswirkungen auf das Layout von anderen Elementen.</span><span class="sxs-lookup"><span data-stu-id="c1f27-230">In contrast, when the CommandBar transitions between closed and open, it does not affect the layout of other elements.</span></span>

## <a name="placement"></a><span data-ttu-id="c1f27-231">Platzierung</span><span class="sxs-lookup"><span data-stu-id="c1f27-231">Placement</span></span>
<span data-ttu-id="c1f27-232">Befehlsleisten können am oberen Rand des App-Fensters, am unteren Rand des App-Fensters und inline platziert werden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-232">Command bars can be placed at the top of the app window, at the bottom of the app window, and inline.</span></span>

![Beispiel1 für die Platzierung der App-Leiste](images/AppbarGuidelines_Placement1.png)

-   <span data-ttu-id="c1f27-234">Bei kleinen Handheld-Geräten empfiehlt es sich, Befehlsleisten am unteren Bildschirmrand zu platzieren, da sie dort besser erreichbar sind.</span><span class="sxs-lookup"><span data-stu-id="c1f27-234">For small handheld devices, we recommend positioning command bars at the bottom of the screen for easy reachability.</span></span>
-   <span data-ttu-id="c1f27-235">Bei Geräten mit größeren Bildschirmen hat es sich bewährt, Befehlsleisten im oberen Bereich des Fensters zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="c1f27-235">For devices with larger screens, placing command bars near the top of the window makes them more noticeable and discoverable.</span></span>

<span data-ttu-id="c1f27-236">Zur Ermittlung der Größe des physischen Bildschirms können Sie die API [DiagonalSizeInInches](https://msdn.microsoft.com/library/windows/apps/windows.graphics.display.displayinformation.diagonalsizeininches.aspx) verwenden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-236">Use the [DiagonalSizeInInches](https://msdn.microsoft.com/library/windows/apps/windows.graphics.display.displayinformation.diagonalsizeininches.aspx) API to determine physical screen size.</span></span>

<span data-ttu-id="c1f27-237">Befehlsleisten können auf Bildschirmen mit einzelner Ansicht (linkes Beispiel) und auf Bildschirmen mit mehreren Ansichten (rechtes Beispiel) in folgenden Bildschirmbereichen platziert werden:</span><span class="sxs-lookup"><span data-stu-id="c1f27-237">Command bars can be placed in the following screen regions on single-view screens (left example) and on multi-view screens (right example).</span></span> <span data-ttu-id="c1f27-238">Inlinebefehlsleisten können überall im Aktionsbereich platziert werden.</span><span class="sxs-lookup"><span data-stu-id="c1f27-238">Inline command bars can be placed anywhere in the action space.</span></span>

![Beispiel2 für die Platzierung der App-Leiste](images/AppbarGuidelines_Placement2.png)

><span data-ttu-id="c1f27-240">**Fingereingabegeräte**: Wenn die Befehlsleiste für den Benutzer sichtbar bleiben muss, während die Bildschirmtastatur (oder ein Soft Input Panel, SIP) angezeigt wird, können Sie die Befehlsleiste der [BottomAppBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.bottomappbar.aspx)-Eigenschaft einer Seite zuweisen. Sie wird dann verschoben und bleibt sichtbar, wenn die Bildschirmtastatur eingeblendet ist.</span><span class="sxs-lookup"><span data-stu-id="c1f27-240">**Touch devices**: If the command bar must remain visible to a user when the touch keyboard, or Soft Input Panel (SIP), appears then you can assign the command bar to the [BottomAppBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.bottomappbar.aspx) property of a Page and it will move to remain visible when the SIP is present.</span></span> <span data-ttu-id="c1f27-241">Andernfalls müssen Sie die Befehlsleiste inline relativ zum App-Inhalt platzieren.</span><span class="sxs-lookup"><span data-stu-id="c1f27-241">Otherwise, you should place the command bar inline and positioned relative to your app content.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="c1f27-242">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="c1f27-242">Get the sample code</span></span>

- <span data-ttu-id="c1f27-243">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c1f27-243">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>
- [<span data-ttu-id="c1f27-244">Beispiel für XAML-Befehle</span><span class="sxs-lookup"><span data-stu-id="c1f27-244">XAML Commanding sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620019)

## <a name="related-articles"></a><span data-ttu-id="c1f27-245">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="c1f27-245">Related articles</span></span>

* [<span data-ttu-id="c1f27-246">Befehlsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="c1f27-246">Command design basics for UWP apps</span></span>](../basics/commanding-basics.md)
* [<span data-ttu-id="c1f27-247">CommandBar-Klasse</span><span class="sxs-lookup"><span data-stu-id="c1f27-247">CommandBar class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn279427)
