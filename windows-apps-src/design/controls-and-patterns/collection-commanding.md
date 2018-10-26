---
author: mijacobs
description: Hier wird beschrieben, wie Sie mithilfe von Kontextbefehlen derartige Aktionen so implementieren können, dass bei allen Eingabearten die jeweils bestmögliche Benutzererfahrung gewährleistet ist.
title: Kontextbefehle
ms.assetid: ''
label: Contextual commanding in collections
template: detail.hbs
ms.author: mijacobs
ms.date: 10/25/2017
ms.topic: article
keywords: Windows 10, UWP
pm-contact: chigy
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: f06d7015fcb208b55fe0cb57b96eaecbc99317cc
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5567523"
---
# <a name="contextual-commanding-for-collections-and-lists"></a><span data-ttu-id="db224-104">Kontextbefehle für Sammlungen und Listen</span><span class="sxs-lookup"><span data-stu-id="db224-104">Contextual commanding for collections and lists</span></span>



<span data-ttu-id="db224-105">Viele Apps enthalten Sammlungen von Inhalten in Form von Listen, Rastern und Strukturen, auf die der Benutzer Aktionen anwenden kann.</span><span class="sxs-lookup"><span data-stu-id="db224-105">Many apps contain collections of content in the form of lists, grids, and trees that users can manipulate.</span></span> <span data-ttu-id="db224-106">Beispielsweise kann er Elemente löschen, umbenennen, kennzeichnen oder aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="db224-106">For example, users might be able to delete, rename, flag, or refresh items.</span></span> <span data-ttu-id="db224-107">In diesem Artikel wird beschrieben, wie Sie mithilfe von Kontextbefehlen derartige Aktionen so implementieren können, dass bei allen Eingabearten die jeweils bestmögliche Benutzererfahrung gewährleistet ist.</span><span class="sxs-lookup"><span data-stu-id="db224-107">This article shows you how to use contextual commands to implement these sorts of actions in a way that provides the best possible experience for all input types.</span></span>  

> <span data-ttu-id="db224-108">**Wichtige APIs:** [Schnittstelle „ICommand“](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand), [Eigenschaft „UIElement.ContextFlyout“](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.ContextFlyout), [Schnittstelle „INotifyPropertyChanged“](https://docs.microsoft.com/uwp/api/windows.ui.xaml.data.inotifypropertychanged)</span><span class="sxs-lookup"><span data-stu-id="db224-108">**Important APIs**: [ICommand interface](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand), [UIElement.ContextFlyout property](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.ContextFlyout), [INotifyPropertyChanged interface](https://docs.microsoft.com/uwp/api/windows.ui.xaml.data.inotifypropertychanged)</span></span>

![Ausführen des Befehls „Als Favorit speichern“ mittels verschiedener Eingabearten](images/ContextualCommand_AddFavorites.png)

## <a name="creating-commands-for-all-input-types"></a><span data-ttu-id="db224-110">Erstellen von Befehlen für alle Eingabearten</span><span class="sxs-lookup"><span data-stu-id="db224-110">Creating commands for all input types</span></span>

<span data-ttu-id="db224-111">Benutzer können zur Interaktion mit UWP-Apps eine [Vielzahl unterschiedlicher Geräte und Eingabearten](../devices/index.md) verwenden. Daher sollte Ihre App Befehle sowohl über von der Eingabeart unabhängige Kontextmenüs als auch über eingabeartspezifische Beschleuniger verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="db224-111">Because users can interact with a UWP app using [a broad range of devices and inputs](../devices/index.md), your app should expose commands though both input-agnostic context menus and input-specific accelerators.</span></span> <span data-ttu-id="db224-112">Wenn Sie beide Optionen integrieren, können Benutzer Befehle schnell auf Inhalte anwenden, unabhängig von Eingabeart und Gerätetyp.</span><span class="sxs-lookup"><span data-stu-id="db224-112">Including both lets the user quickly invoke commands on content, regardless of input or device type.</span></span>

<span data-ttu-id="db224-113">In der Tabelle unten sind einige typische Befehle für Sammlungen aufgeführt sowie Möglichkeiten, diese Befehle verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="db224-113">This table shows some typical collection commands and ways to expose those commands.</span></span> 

| <span data-ttu-id="db224-114">Befehl</span><span class="sxs-lookup"><span data-stu-id="db224-114">Command</span></span>          | <span data-ttu-id="db224-115">Eingabeartunabhängig</span><span class="sxs-lookup"><span data-stu-id="db224-115">Input-agnostic</span></span> | <span data-ttu-id="db224-116">Beschleuniger für die Mauseingabe</span><span class="sxs-lookup"><span data-stu-id="db224-116">Mouse accelerator</span></span> | <span data-ttu-id="db224-117">Beschleuniger für die Tastatureingabe</span><span class="sxs-lookup"><span data-stu-id="db224-117">Keyboard accelerator</span></span> | <span data-ttu-id="db224-118">Beschleuniger für die Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="db224-118">Touch accelerator</span></span> |
| ---------------- | -------------- | ----------------- | -------------------- | ----------------- |
| <span data-ttu-id="db224-119">Element löschen</span><span class="sxs-lookup"><span data-stu-id="db224-119">Delete item</span></span>      | <span data-ttu-id="db224-120">Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="db224-120">Context menu</span></span>   | <span data-ttu-id="db224-121">Hoverschaltfläche</span><span class="sxs-lookup"><span data-stu-id="db224-121">Hover button</span></span>      | <span data-ttu-id="db224-122">ENTF-Taste</span><span class="sxs-lookup"><span data-stu-id="db224-122">DEL key</span></span>              | <span data-ttu-id="db224-123">Löschen per Wischen</span><span class="sxs-lookup"><span data-stu-id="db224-123">Swipe to delete</span></span>   |
| <span data-ttu-id="db224-124">Element kennzeichnen</span><span class="sxs-lookup"><span data-stu-id="db224-124">Flag item</span></span>        | <span data-ttu-id="db224-125">Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="db224-125">Context menu</span></span>   | <span data-ttu-id="db224-126">Hoverschaltfläche</span><span class="sxs-lookup"><span data-stu-id="db224-126">Hover button</span></span>      | <span data-ttu-id="db224-127">STRG+UMSCHALT+G</span><span class="sxs-lookup"><span data-stu-id="db224-127">Ctrl+Shift+G</span></span>         | <span data-ttu-id="db224-128">Kennzeichnen per Wischen</span><span class="sxs-lookup"><span data-stu-id="db224-128">Swipe to flag</span></span>     |
| <span data-ttu-id="db224-129">Daten aktualisieren</span><span class="sxs-lookup"><span data-stu-id="db224-129">Refresh data</span></span>     | <span data-ttu-id="db224-130">Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="db224-130">Context menu</span></span>   | <span data-ttu-id="db224-131">–</span><span class="sxs-lookup"><span data-stu-id="db224-131">N/A</span></span>               | <span data-ttu-id="db224-132">F5-Taste</span><span class="sxs-lookup"><span data-stu-id="db224-132">F5 key</span></span>               | <span data-ttu-id="db224-133">Aktualisieren durch Ziehen</span><span class="sxs-lookup"><span data-stu-id="db224-133">Pull to refresh</span></span>   |
| <span data-ttu-id="db224-134">Element als Favorit speichern</span><span class="sxs-lookup"><span data-stu-id="db224-134">Favorite an item</span></span> | <span data-ttu-id="db224-135">Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="db224-135">Context menu</span></span>   | <span data-ttu-id="db224-136">Hoverschaltfläche</span><span class="sxs-lookup"><span data-stu-id="db224-136">Hover button</span></span>      | <span data-ttu-id="db224-137">F-Taste, STRG+S</span><span class="sxs-lookup"><span data-stu-id="db224-137">F, Ctrl+S</span></span>            | <span data-ttu-id="db224-138">Als Favorit speichern per Wischen</span><span class="sxs-lookup"><span data-stu-id="db224-138">Swipe to favorite</span></span> |


* **<span data-ttu-id="db224-139">Grundsätzlich sollten Sie sämtliche Befehle für ein Element im [Kontextmenü](menus.md) des Elements verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="db224-139">In general, you should make all commands for an item available in the item's [context menu](menus.md).</span></span>** <span data-ttu-id="db224-140">Kontextmenüs sind für den Benutzer bei jeder Eingabeart verfügbar und sollten alle Kontextbefehle enthalten, die er ausführen darf.</span><span class="sxs-lookup"><span data-stu-id="db224-140">Context menus are accessible to users regardless of input type, and should contain all of the contextual commands that user can perform.</span></span>

* **<span data-ttu-id="db224-141">Für häufig verwendete Befehle empfiehlt sich die Implementierung von Eingabebeschleunigern.</span><span class="sxs-lookup"><span data-stu-id="db224-141">For frequently accessed commands, consider using input accelerators.</span></span>** <span data-ttu-id="db224-142">Eingabebeschleuniger basieren auf dem jeweiligen Eingabegerät und erlauben es dem Benutzer, Aktionen schnell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="db224-142">Input accelerators let the user perform actions quickly, based on their input device.</span></span> <span data-ttu-id="db224-143">Zu den Eingabebeschleunigern gehören:</span><span class="sxs-lookup"><span data-stu-id="db224-143">Input accelerators include:</span></span>
    - <span data-ttu-id="db224-144">Aktionsausführung per Wischen (Beschleuniger für die Toucheingabe)</span><span class="sxs-lookup"><span data-stu-id="db224-144">Swipe-to-action (touch accelerator)</span></span>
    - <span data-ttu-id="db224-145">Datenaktualisierung per Ziehen (Beschleuniger für die Toucheingabe)</span><span class="sxs-lookup"><span data-stu-id="db224-145">Pull to refresh data (touch accelerator)</span></span>
    - <span data-ttu-id="db224-146">Tastenkombinationen (Beschleuniger für die Tastatureingabe)</span><span class="sxs-lookup"><span data-stu-id="db224-146">Keyboard shortcuts (keyboard accelerator)</span></span>
    - <span data-ttu-id="db224-147">Zugriffstasten (Beschleuniger für die Tastatureingabe)</span><span class="sxs-lookup"><span data-stu-id="db224-147">Access keys (keyboard accelerator)</span></span>
    - <span data-ttu-id="db224-148">Hoverschaltflächen für Maus und Stift (Beschleuniger für die Eingabe per Zeigegerät)</span><span class="sxs-lookup"><span data-stu-id="db224-148">Mouse & Pen hover buttons (pointer accelerator)</span></span>

> [!NOTE]
> <span data-ttu-id="db224-149">Benutzer sollten immer auf sämtliche Befehle zugreifen können, ganz gleich, welches Gerät sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="db224-149">Users should be able to access all commands from any type of device.</span></span> <span data-ttu-id="db224-150">Wenn Sie die Befehle Ihrer App beispielsweise nur in Form von Hoverschaltflächen für eine beschleunigte Eingabe über Zeigegeräte verfügbar machen, haben Benutzer von Touchsystemen keinen Zugriff auf sie.</span><span class="sxs-lookup"><span data-stu-id="db224-150">For example, if your app’s commands are only exposed through hover button pointer accelerators, touch users won't be able to access them.</span></span> <span data-ttu-id="db224-151">Implementieren Sie zumindest ein Kontextmenü, in dem alle Befehle verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="db224-151">At a minimum, use a context menu to provide access to all commands.</span></span>  

## <a name="example-the-podcastobject-data-model"></a><span data-ttu-id="db224-152">Beispiel: Datenmodell „PodcastObject“</span><span class="sxs-lookup"><span data-stu-id="db224-152">Example: The PodcastObject data model</span></span>

<span data-ttu-id="db224-153">Zur Verdeutlichung unserer Empfehlungen für die Befehlsimplementierung erstellen wir im Rahmen dieses Artikels eine Liste von Podcasts für eine Podcast-App.</span><span class="sxs-lookup"><span data-stu-id="db224-153">To demonstrate our commanding recommendations, this article creates a list of podcasts for a podcast app.</span></span> <span data-ttu-id="db224-154">Der Beispielcode demonstriert, wie Sie es Benutzern ermöglichen können, bestimmte Podcasts aus der Liste als Favoriten zu speichern.</span><span class="sxs-lookup"><span data-stu-id="db224-154">The example code demonstrate how to enable the user to "favorite" a particular podcast from a list.</span></span>

<span data-ttu-id="db224-155">Hier die Definition des Podcast-Objekts, mit dem Sie in diesem Beispiel arbeiten:</span><span class="sxs-lookup"><span data-stu-id="db224-155">Here's the definition for the podcast object we'll be working with:</span></span> 

```csharp
public class PodcastObject : INotifyPropertyChanged
{
    // The title of the podcast
    public String Title { get; set; }

    // The podcast's description
    public String Description { get; set; }

    // Describes if the user has set this podcast as a favorite
    public bool IsFavorite
    {
        get
        {
            return _isFavorite;
        }
        set
        {
            _isFavorite = value;
            OnPropertyChanged("IsFavorite");
        }
    }
    private bool _isFavorite = false;

    public event PropertyChangedEventHandler PropertyChanged;

    private void OnPropertyChanged(String property)
    {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(property));
    }
}
```

<span data-ttu-id="db224-156">Beachten Sie: Das Objekt „PodcastObject“ implementiert die Schnittstelle [INotifyPropertyChanged](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Data.INotifyPropertyChanged), um reagieren zu können, sobald der Benutzer die Eigenschaft „IsFavorite“ ändert.</span><span class="sxs-lookup"><span data-stu-id="db224-156">Notice that the PodcastObject implements [INotifyPropertyChanged](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Data.INotifyPropertyChanged) to respond to property changes when the user toggles the IsFavorite property.</span></span>

## <a name="defining-commands-with-the-icommand-interface"></a><span data-ttu-id="db224-157">Definieren von Befehlen mit der Schnittstelle „ICommand“</span><span class="sxs-lookup"><span data-stu-id="db224-157">Defining commands with the ICommand interface</span></span>

<span data-ttu-id="db224-158">Über die [Schnittstelle „ICommand“](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand) können Sie Befehle definieren, die für mehrere Eingabearten verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="db224-158">The [ICommand interface](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand) helps you to define a command that's  available for multiple input types.</span></span> <span data-ttu-id="db224-159">Ein Beispiel: Statt den Code eines Löschbefehls in identischer Form in zwei unterschiedliche Ereignishandler zu schreiben (einmal in einen Handler für das Drücken der ENTF-Taste und einmal in einen Handler für das Rechtsklicken auf „Löschen“ in einem Kontextmenü), können Sie Ihre Löschlogik einmalig als Schnittstelle des Typs [ICommand](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand) implementieren und anschließend für verschiedene Eingabearten verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="db224-159">For example, instead of writing the same code for a delete command in two different event handlers, one for when the user presses the Delete key and one for when the user right clicks "Delete" in a context menu, you can implement your delete logic once, as an [ICommand](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand),  and then make it available to different input types.</span></span>

<span data-ttu-id="db224-160">Dazu müssen Sie die Schnittstelle „ICommand“ definieren, die die Aktion „Als Favorit speichern“ darstellt.</span><span class="sxs-lookup"><span data-stu-id="db224-160">We need to define the ICommand that represents the "Favorite" action.</span></span> <span data-ttu-id="db224-161">In diesem Beispiel verwenden Sie die Methode [Execute](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand.Execute) des Befehls, um einen Podcast als Favorit zu speichern.</span><span class="sxs-lookup"><span data-stu-id="db224-161">We will use the command's [Execute](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand.Execute) method to favorite a podcast.</span></span> <span data-ttu-id="db224-162">Der betreffende Podcast wird über den Parameter des Befehls an die Methode „Execute“ übergeben. Dieser Parameter kann mithilfe der Eigenschaft „CommandParameter“ gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="db224-162">The particular podcast will be provided to the execute method via the command's parameter, which can be bound using the CommandParameter property.</span></span>

```csharp
public class FavoriteCommand: ICommand
{
    public event EventHandler CanExecuteChanged;

    public bool CanExecute(object parameter)
    {
        return true;
    }
    public void Execute(object parameter)
    {
        // Perform the logic to "favorite" an item.
        (parameter as PodcastObject).IsFavorite = true;
    }
}
```

<span data-ttu-id="db224-163">Wenn Sie einen Befehl für mehrere Sammlungen und Elemente verwenden möchten, können Sie ihn als Ressource auf der Seite oder in der App speichern.</span><span class="sxs-lookup"><span data-stu-id="db224-163">To use the same command with multiple collections and elements, you can store the command as a resource on the page or on the app.</span></span>

```xaml
<Application.Resources>
    <local:FavoriteCommand x:Key="favoriteCommand" />
</Application.Resources>
```

<span data-ttu-id="db224-164">Zur Ausführung des Befehls rufen Sie seine Methode [Execute](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand.Execute) auf.</span><span class="sxs-lookup"><span data-stu-id="db224-164">To execute the command, you call its [Execute](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand.Execute) method.</span></span>

```csharp
// Favorite the item using the defined command
var favoriteCommand = Application.Current.Resources["favoriteCommand"] as ICommand;
favoriteCommand.Execute(PodcastObject);
```


## <a name="creating-a-usercontrol-to-respond-to-a-variety-of-inputs"></a><span data-ttu-id="db224-165">Erstellen eines „UserControl“-Steuerelements zur Reaktion auf verschiedene Eingabearten</span><span class="sxs-lookup"><span data-stu-id="db224-165">Creating a UserControl to respond to a variety of inputs</span></span>

<span data-ttu-id="db224-166">Wenn Sie eine Liste von Elementen implementieren und jedes dieser Elemente auf verschiedene Eingabearten reagieren können soll, können Sie zur Vereinfachung des Codes jeweils ein [UserControl](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.UserControl)-Steuerelement für die einzelnen Elemente definieren. In diesem Steuerelement wiederum definieren Sie das Kontextmenü und die Ereignishandler des jeweiligen Elements.</span><span class="sxs-lookup"><span data-stu-id="db224-166">When you have a list of items and each of those items should respond to multiple inputs, you can simplify your code by defining a [UserControl](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.UserControl) for the item and using it to define your items' context menu and event handlers.</span></span> 

<span data-ttu-id="db224-167">So erstellen Sie ein „UserControl“-Steuerelement in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="db224-167">To create a UserControl in Visual Studio:</span></span>
1. <span data-ttu-id="db224-168">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt.</span><span class="sxs-lookup"><span data-stu-id="db224-168">In the Solution Explorer, right click the project.</span></span> <span data-ttu-id="db224-169">Es wird ein Kontextmenü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db224-169">A context menu appears.</span></span>
2. <span data-ttu-id="db224-170">Klicken Sie auf **Hinzufügen > Neues Element...**.</span><span class="sxs-lookup"><span data-stu-id="db224-170">Select **Add > New Item...**</span></span> <br /><span data-ttu-id="db224-171">Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db224-171">The **Add New Item** dialog appears.</span></span> 
3. <span data-ttu-id="db224-172">Wählen Sie aus der Liste der Elemente die Option „UserControl“ aus.</span><span class="sxs-lookup"><span data-stu-id="db224-172">Select UserControl from the list of items.</span></span> <span data-ttu-id="db224-173">Geben Sie dem Element einen Namen, und klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="db224-173">Give it the name you want and click **Add**.</span></span> <span data-ttu-id="db224-174">Visual Studio generiert nun einen „UserControl“-Stub.</span><span class="sxs-lookup"><span data-stu-id="db224-174">Visual Studio will generate a stub UserControl for you.</span></span> 

<span data-ttu-id="db224-175">In unserem Podcast-Beispiel werden alle Podcasts in einer Liste angezeigt. In dieser Liste gibt es verschiedene Möglichkeiten, wie der Benutzer einen Podcast als Favorit speichern kann.</span><span class="sxs-lookup"><span data-stu-id="db224-175">In our podcast example, each podcast will be displayed in a list, which will expose a variety of ways to "Favorite" a podcast.</span></span> <span data-ttu-id="db224-176">Konkret kann der Benutzer folgende Aktionen ausführen, um einen Podcast als Favorit zu speichern:</span><span class="sxs-lookup"><span data-stu-id="db224-176">The user will be able to perform the following actions to "Favorite" the podcast:</span></span>
- <span data-ttu-id="db224-177">Aufrufen eines Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="db224-177">Invoke a context menu</span></span>
- <span data-ttu-id="db224-178">Drücken einer Tastenkombination</span><span class="sxs-lookup"><span data-stu-id="db224-178">Perform keyboard shortcuts</span></span>
- <span data-ttu-id="db224-179">Anzeigen einer Hoverschaltfläche</span><span class="sxs-lookup"><span data-stu-id="db224-179">Show a hover button</span></span>
- <span data-ttu-id="db224-180">Durchführen einer Wischgeste</span><span class="sxs-lookup"><span data-stu-id="db224-180">Perform a swipe gesture</span></span>

<span data-ttu-id="db224-181">Um diese Verhaltensweisen zu kapseln und den Befehl „FavoriteCommand“ anwenden zu können, erstellen Sie nun ein neues [UserControl](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.UserControl)-Steuerelement namens „PodcastUserControl“, das einen Podcast in der Liste darstellt.</span><span class="sxs-lookup"><span data-stu-id="db224-181">In order to encapsulate these behaviors and use the FavoriteCommand, let's create a new [UserControl](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.UserControl) named "PodcastUserControl" to represent a podcast in the list.</span></span>

<span data-ttu-id="db224-182">„PodcastUserControl“ zeigt die Felder des Objekts „PodcastObject“ als „TextBlock“-Objekte an und kann auf verschiedene Benutzerinteraktionen reagieren.</span><span class="sxs-lookup"><span data-stu-id="db224-182">The PodcastUserControl displays the fields of the PodcastObject as TextBlocks, and responds to various user interactions.</span></span> <span data-ttu-id="db224-183">Im weiteren Verlauf des Artikels wird das „PodcastUserControl“-Steuerelement referenziert und erweitert.</span><span class="sxs-lookup"><span data-stu-id="db224-183">We will reference and expand upon the PodcastUserControl throughout this article.</span></span>

**<span data-ttu-id="db224-184">PodcastUserControl.xaml</span><span class="sxs-lookup"><span data-stu-id="db224-184">PodcastUserControl.xaml</span></span>**
```xaml
<UserControl
    x:Class="ContextCommanding.PodcastUserControl"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    IsTabStop="True" UseSystemFocusVisuals="True"
    >
    <Grid Margin="12,0,12,0">
        <StackPanel>
            <TextBlock Text="{x:Bind PodcastObject.Title, Mode=OneWay}" Style="{StaticResource TitleTextBlockStyle}" />
            <TextBlock Text="{x:Bind PodcastObject.Description, Mode=OneWay}" Style="{StaticResource SubtitleTextBlockStyle}" />
            <TextBlock Text="{x:Bind PodcastObject.IsFavorite, Mode=OneWay}" Style="{StaticResource SubtitleTextBlockStyle}"/>
        </StackPanel>
    </Grid>
</UserControl>
```

**<span data-ttu-id="db224-185">PodcastUserControl.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="db224-185">PodcastUserControl.xaml.cs</span></span>**
```csharp
public sealed partial class PodcastUserControl : UserControl
{
    public static readonly DependencyProperty PodcastObjectProperty =
        DependencyProperty.Register(
            "PodcastObject",
            typeof(PodcastObject),
            typeof(PodcastUserControl),
            new PropertyMetadata(null));

    public PodcastObject PodcastObject
    {
        get { return (PodcastObject)GetValue(PodcastObjectProperty); }
        set { SetValue(PodcastObjectProperty, value); }
    }

    public PodcastUserControl()
    {
        this.InitializeComponent();

        // TODO: We will add event handlers here.
    }
}
```

<span data-ttu-id="db224-186">Beachten Sie: „PodcastUserControl“ enthält einen Verweis auf „PodcastObject“ in Gestalt von „DependencyProperty“.</span><span class="sxs-lookup"><span data-stu-id="db224-186">Notice that the PodcastUserControl maintains a reference to the PodcastObject as a DependencyProperty.</span></span> <span data-ttu-id="db224-187">So lassen sich Objekte des Typs „PodcastObject“ an das „PodcastUserControl“-Steuerelement binden.</span><span class="sxs-lookup"><span data-stu-id="db224-187">This enables us to bind PodcastObjects to the PodcastUserControl.</span></span>

<span data-ttu-id="db224-188">Nun erstellen Sie einige Objekte des Typs „PodcastObject“ und binden diese Objekte an ein „ListView“-Element, um eine Podcast-Liste zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="db224-188">After you have generated some PodcastObjects, you can create a list of podcasts by binding the PodcastObjects to a ListView.</span></span> <span data-ttu-id="db224-189">Die „PodcastUserControl“-Objekte beschreiben die Visualisierung der „PodcastObject“-Objekte und werden daher über die Eigenschaft „ItemTemplate“ von „ListView“ festgelegt.</span><span class="sxs-lookup"><span data-stu-id="db224-189">The PodcastUserControl objects describe the visualization of the PodcastObjects, and are therefore set using the ListView's ItemTemplate.</span></span>

**<span data-ttu-id="db224-190">MainPage.xaml</span><span class="sxs-lookup"><span data-stu-id="db224-190">MainPage.xaml</span></span>**
```xaml
<ListView x:Name="ListOfPodcasts"
            ItemsSource="{x:Bind podcasts}">
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="local:PodcastObject">
            <local:PodcastUserControl PodcastObject="{x:Bind Mode=OneWay}" />
        </DataTemplate>
    </ListView.ItemTemplate>
    <ListView.ItemContainerStyle>
        <!-- The PodcastUserControl will entirely fill the ListView item and handle tabbing within itself. -->
        <Style TargetType="ListViewItem" BasedOn="{StaticResource ListViewItemRevealStyle}">
            <Setter Property="HorizontalContentAlignment" Value="Stretch" />
            <Setter Property="Padding" Value="0"/>
            <Setter Property="IsTabStop" Value="False"/>
        </Style>
    </ListView.ItemContainerStyle>
</ListView>
```

## <a name="creating-context-menus"></a><span data-ttu-id="db224-191">Erstellen von Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="db224-191">Creating context menus</span></span>

<span data-ttu-id="db224-192">Kontextmenüs zeigen bei Aufruf durch den Benutzer eine Liste von Befehlen oder Optionen an.</span><span class="sxs-lookup"><span data-stu-id="db224-192">Context menus display a list of commands or options when the user requests them.</span></span> <span data-ttu-id="db224-193">Sie stellen Kontextbefehle für das ihnen zugeordnete Element bereit und sind in der Regel für sekundäre Aktionen reserviert, die nur für dieses Element verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="db224-193">Context menus provide contextual commands related to their attached element, and are generally reserved for secondary actions specific to that item.</span></span>

![Anzeigen eines Kontextmenüs für ein Element](images/ContextualCommand_RightClick.png)

<span data-ttu-id="db224-195">Benutzer können Kontextmenüs über die folgenden „Kontextaktionen“ aufrufen:</span><span class="sxs-lookup"><span data-stu-id="db224-195">The user can invoke context menus using these "context actions":</span></span>

| <span data-ttu-id="db224-196">Eingabeart</span><span class="sxs-lookup"><span data-stu-id="db224-196">Input</span></span>    | <span data-ttu-id="db224-197">Kontextaktion</span><span class="sxs-lookup"><span data-stu-id="db224-197">Context action</span></span>                          |
| -------- | --------------------------------------- |
| <span data-ttu-id="db224-198">Maus</span><span class="sxs-lookup"><span data-stu-id="db224-198">Mouse</span></span>    | <span data-ttu-id="db224-199">Rechtsklick</span><span class="sxs-lookup"><span data-stu-id="db224-199">Right click</span></span>                             |
| <span data-ttu-id="db224-200">Tastatur</span><span class="sxs-lookup"><span data-stu-id="db224-200">Keyboard</span></span> | <span data-ttu-id="db224-201">UMSCHALT+F10, Menütaste</span><span class="sxs-lookup"><span data-stu-id="db224-201">Shift+F10, Menu button</span></span>                  |
| <span data-ttu-id="db224-202">Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="db224-202">Touch</span></span>    | <span data-ttu-id="db224-203">Langes Drücken auf das Element</span><span class="sxs-lookup"><span data-stu-id="db224-203">Long press on item</span></span>                      |
| <span data-ttu-id="db224-204">Stift</span><span class="sxs-lookup"><span data-stu-id="db224-204">Pen</span></span>      | <span data-ttu-id="db224-205">Drücken der Drucktaste, langes Drücken auf das Element</span><span class="sxs-lookup"><span data-stu-id="db224-205">Barrel button press, long press on item</span></span> |
| <span data-ttu-id="db224-206">Gamepad</span><span class="sxs-lookup"><span data-stu-id="db224-206">Gamepad</span></span>  | <span data-ttu-id="db224-207">Menütaste</span><span class="sxs-lookup"><span data-stu-id="db224-207">Menu button</span></span>                             |

**<span data-ttu-id="db224-208">Da Kontextmenüs über jede Eingabeart geöffnet werden können, sollten sie sämtliche Kontextbefehle enthalten, die für das jeweilige Listenelement verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="db224-208">Since the user can open a context menu regardless of input type, your context menu should contain all of the contextual commands available for the list item.</span></span>**

### <a name="contextflyout"></a><span data-ttu-id="db224-209">ContextFlyout</span><span class="sxs-lookup"><span data-stu-id="db224-209">ContextFlyout</span></span>

<span data-ttu-id="db224-210">Über die in der Klasse „UIElement“ definierte [Eigenschaft „ContextFlyout“](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.ContextFlyout) können Sie ganz einfach ein Kontextmenü erstellen, das bei allen Eingabearten funktioniert.</span><span class="sxs-lookup"><span data-stu-id="db224-210">The [ContextFlyout property](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.ContextFlyout), defined by the UIElement class, makes it easy to create a context menu that works with all input types.</span></span> <span data-ttu-id="db224-211">Über die Klasse „MenuFlyout“ stellen Sie ein Flyout bereit, das Ihr Kontextmenü darstellt. Sobald der Benutzer eine der oben aufgeführten „Kontextaktionen“ durchführt, wird das dem Element zugeordnete „MenuFlyout“-Objekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db224-211">You provide a flyout representing your context menu using MenuFlyout, and when the user performs a “context action” as defined above, the MenuFlyout corresponding to the item will be displayed.</span></span>

<span data-ttu-id="db224-212">In diesem Beispiel fügen Sie „PodcastUserControl“ eine Eigenschaft „ContextFlyout“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="db224-212">We will add a ContextFlyout to the PodcastUserControl.</span></span> <span data-ttu-id="db224-213">Das in der Eigenschaft „ContextFlyout“ definierte „MenuFlyout“-Objekt enthält ein einziges Element, über das sich Podcasts als Favorit speichern lassen.</span><span class="sxs-lookup"><span data-stu-id="db224-213">The MenuFlyout specified as the ContextFlyout contains a single item to favorite a podcast.</span></span> <span data-ttu-id="db224-214">Beachten Sie: „MenuFlyoutItem“ verwendet den oben definierten Befehl „favoriteCommand“, wobei „CommandParameter“ an „PodcastObject“ gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="db224-214">Notice that this MenuFlyoutItem uses the favoriteCommand defined above, with the CommandParamter bound to the PodcastObject.</span></span>

**<span data-ttu-id="db224-215">PodcastUserControl.xaml</span><span class="sxs-lookup"><span data-stu-id="db224-215">PodcastUserControl.xaml</span></span>**
```xaml
<UserControl>
    <UserControl.ContextFlyout>
        <MenuFlyout>
            <MenuFlyoutItem Text="Favorite" Command="{StaticResource favoriteCommand}" CommandParameter="{x:Bind PodcastObject, Mode=OneWay}" />
        </MenuFlyout>
    </UserControl.ContextFlyout>
    <Grid Margin="12,0,12,0">
        <!-- ... -->
    </Grid>
</UserControl>

```

<span data-ttu-id="db224-216">Sie können auch das [Ereignis „ContextRequested“](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.ContextRequested) verwenden, um auf Kontextaktionen zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="db224-216">Note that you can also use the [ContextRequested event](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.ContextRequested) to respond to context actions.</span></span> <span data-ttu-id="db224-217">Das Ereignis „ContextRequested“ wird nicht ausgelöst, wenn die Eigenschaft „ContextFlyout“ definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="db224-217">The ContextRequested event will not fire if a ContextFlyout has been specified.</span></span>

## <a name="creating-input-accelerators"></a><span data-ttu-id="db224-218">Erstellen von Eingabebeschleunigern</span><span class="sxs-lookup"><span data-stu-id="db224-218">Creating input accelerators</span></span>

<span data-ttu-id="db224-219">Für jedes Element in einer Sammlung sollte ein Kontextmenü mit allen verfügbaren Kontextbefehlen implementiert sein. Vielleicht möchten Sie jedoch, dass Benutzer eine kleinere Gruppe häufig verwendeter Befehle schnell ausführen können.</span><span class="sxs-lookup"><span data-stu-id="db224-219">Although each item in the collection should have a context menu containing all contextual commands, you might want to enable users to quickly perform a smaller set of frequently performed commands.</span></span> <span data-ttu-id="db224-220">Beispiel: In einer E-Mail-App gibt es die sekundären Befehle „Antworten“, „Archivieren“, „In Ordner verschieben“, „Kennzeichnen“ und „Löschen“. Am häufigsten verwendet werden jedoch die Befehle „Löschen“ und „Kennzeichnen“.</span><span class="sxs-lookup"><span data-stu-id="db224-220">For example, a mailing app may have secondary commands like Reply, Archive, Move to Folder, Set Flag, and Delete which appear in a context menu, but the most common commands are Delete and Flag.</span></span> <span data-ttu-id="db224-221">Sobald Sie wissen, welche Befehle am häufigsten verwendet werden, können Sie eingabeartbasierte Beschleuniger implementieren, damit Ihre Benutzer diese Befehle einfacher ausführen können.</span><span class="sxs-lookup"><span data-stu-id="db224-221">After you have identified which commands are most common, you can use input-based accelerators to make these commands easier for a user to perform.</span></span>

<span data-ttu-id="db224-222">In unserer Podcast-App ist der Befehl „Als Favorit speichern“ einer der am häufigsten ausgeführten Befehle.</span><span class="sxs-lookup"><span data-stu-id="db224-222">In the podcast app, the frequently performed command is the "Favorite" command.</span></span>

### <a name="keyboard-accelerators"></a><span data-ttu-id="db224-223">Beschleuniger für die Tastatureingabe</span><span class="sxs-lookup"><span data-stu-id="db224-223">Keyboard accelerators</span></span>

#### <a name="shortcuts-and-direct-key-handling"></a><span data-ttu-id="db224-224">Behandeln von Tastenkombinationen und Einzeltasten</span><span class="sxs-lookup"><span data-stu-id="db224-224">Shortcuts and direct key handling</span></span>

![Aktionsausführung per STRG oder F-Taste](images/ContextualCommand_Keyboard.png)

<span data-ttu-id="db224-226">Je nach Art des Inhalts können Sie bestimmte Tastenkombinationen für die Ausführung einer Aktion festlegen.</span><span class="sxs-lookup"><span data-stu-id="db224-226">Depending on the type of content, you may identify certain key combinations that should perform an action.</span></span> <span data-ttu-id="db224-227">In einer E-Mail-App beispielsweise könnten sich ausgewählte E-Mails über die ENTF-Taste löschen lassen.</span><span class="sxs-lookup"><span data-stu-id="db224-227">In an email app, for example, the DEL key may be used to delete the email that is selected.</span></span> <span data-ttu-id="db224-228">In einer Podcast-App könnte die Tastenkombination STRG+S oder eine der F-Tasten einen Podcast als Favorit zur späteren Wiedergabe speichern.</span><span class="sxs-lookup"><span data-stu-id="db224-228">In a podcast app, the Ctrl+S or F keys could favorite a podcast for later.</span></span> <span data-ttu-id="db224-229">Obwohl einige Befehle allgemein bekannte Standardtasten bzw. Standardtastenkombinationen haben (z.B. ENTF zum Löschen), sind die Tasten und Tastenkombinationen anderer Befehle jeweils App-spezifisch oder domänenspezifisch.</span><span class="sxs-lookup"><span data-stu-id="db224-229">Although some commands have common, well-known keyboard shortcuts like DEL to delete, other commands have app- or domain-specific shortcuts.</span></span> <span data-ttu-id="db224-230">Verwenden Sie falls möglich allgemein bekannte Tasten und Tastenkombinationen, oder zeigen Sie für den Benutzer eine kurze QuickInfo mit der Taste oder Tastenkombination für den jeweiligen Befehl an.</span><span class="sxs-lookup"><span data-stu-id="db224-230">Use well-known shortcuts if possible, or consider providing reminder text in a tooltip to teach the user about the shortcut command.</span></span>

<span data-ttu-id="db224-231">Über das Ereignis [KeyDown](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.KeyDownEvent) kann Ihre App auf einen Tastendruck des Benutzers reagieren.</span><span class="sxs-lookup"><span data-stu-id="db224-231">Your app can respond when the user presses a key using the [KeyDown](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.KeyDownEvent) event.</span></span> <span data-ttu-id="db224-232">In der Regel gehen die Benutzer davon aus, dass die App beim ersten Tastendruck reagiert, nicht erst, wenn sie die Taste wieder loslassen.</span><span class="sxs-lookup"><span data-stu-id="db224-232">In general, users expect that the app will respond when they first press the key down, rather than waiting until they release the key.</span></span>

<span data-ttu-id="db224-233">In diesem Beispiel zeigen wir Ihnen, wie Sie den Handler „KeyDown“ zu „PodcastUserControl“ hinzufügen können, damit ein Podcast als Favorit gespeichert wird, wenn der Benutzer STRG+S oder eine der F-Tasten drückt. Dabei verwenden Sie denselben Befehl wie zuvor.</span><span class="sxs-lookup"><span data-stu-id="db224-233">This example walks through how to add the KeyDown handler to the PodcastUserControl to favorite a podcast when the user presses Ctrl+S or F. It uses the same command as before.</span></span>

**<span data-ttu-id="db224-234">PodcastUserControl.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="db224-234">PodcastUserControl.xaml.cs</span></span>**
```csharp
// Respond to the F and Ctrl+S keys to favorite the focused item.
protected override void OnKeyDown(KeyRoutedEventArgs e)
{
    var ctrlState = CoreWindow.GetForCurrentThread().GetKeyState(VirtualKey.Control);
    var isCtrlPressed = (ctrlState & CoreVirtualKeyStates.Down) == CoreVirtualKeyStates.Down || (ctrlState & CoreVirtualKeyStates.Locked) == CoreVirtualKeyStates.Locked;

    if (e.Key == Windows.System.VirtualKey.F || (e.Key == Windows.System.VirtualKey.S && isCtrlPressed))
    {
        // Favorite the item using the defined command
        var favoriteCommand = Application.Current.Resources["favoriteCommand"] as ICommand;
        favoriteCommand.Execute(PodcastObject);
    }
}
```

### <a name="mouse-accelerators"></a><span data-ttu-id="db224-235">Beschleuniger für die Mauseingabe</span><span class="sxs-lookup"><span data-stu-id="db224-235">Mouse accelerators</span></span>

![Anzeigen einer Schaltfläche durch Platzieren des Mauszeigers auf einem Element](images/ContextualCommand_HovertoReveal.png)

<span data-ttu-id="db224-237">Benutzer sind vertraut mit per Rechtsklick aufrufbaren Kontextmenüs. Möglicherweise möchten Sie jedoch, dass sie häufig verwendete Befehle mit nur einem einzigen Mausklick ausführen können.</span><span class="sxs-lookup"><span data-stu-id="db224-237">Users are familiar with right-click context menus, but you may wish to empower users to perform common commands using only a single click of the mouse.</span></span> <span data-ttu-id="db224-238">Zu diesem Zweck können Sie der Canvas Ihres Sammlungselements dedizierte Schaltflächen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="db224-238">To enable this experience, you can include dedicated buttons on your collection item's canvas.</span></span> <span data-ttu-id="db224-239">Damit Ihre Benutzer schnell mithilfe der Maus Aktionen durchführen können, die Benutzeroberfläche aber dennoch übersichtlich bleibt, können Sie festlegen, dass diese Schaltflächen nur angezeigt werden, wenn der Benutzer den Zeiger auf einem bestimmten Listenelement platziert.</span><span class="sxs-lookup"><span data-stu-id="db224-239">To both empower users to act quickly using mouse, and to minimize visual clutter, you can choose to only reveal these buttons when the user has their pointer within a particular list item.</span></span>

<span data-ttu-id="db224-240">In unserem Beispiel wird der Befehl „Als Favorit speichern“ durch eine Schaltfläche dargestellt, die direkt in „PodcastUserControl“ definiert ist.</span><span class="sxs-lookup"><span data-stu-id="db224-240">In this example, the Favorite command is represented by a button defined directly in the PodcastUserControl.</span></span> <span data-ttu-id="db224-241">Beachten Sie: Die Schaltfläche in diesem Beispiel verwendet denselben Befehl wie zuvor, „favoriteCommand“.</span><span class="sxs-lookup"><span data-stu-id="db224-241">Note that the button in this example uses the same command, FavoriteCommand, as before.</span></span> <span data-ttu-id="db224-242">Die Sichtbarkeit der Schaltfläche können Sie über „VisualStateManager“ steuern. Diese Klasse schaltet zwischen den verschiedenen visuellen Zuständen um, sobald der Zeiger auf dem Steuerelement platziert wird oder vom Steuerelement entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="db224-242">To toggle visibility of this button, you can use the VisualStateManager to switch between visual states when the pointer enters and exits the control.</span></span>

**<span data-ttu-id="db224-243">PodcastUserControl.xaml</span><span class="sxs-lookup"><span data-stu-id="db224-243">PodcastUserControl.xaml</span></span>**
```xaml
<UserControl>
    <UserControl.ContextFlyout>
        <!-- ... -->
    </UserControl.ContextFlyout>
    <Grid Margin="12,0,12,0">
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup x:Name="HoveringStates">
                <VisualState x:Name="HoverButtonsShown">
                    <VisualState.Setters>
                        <Setter Target="hoverArea.Visibility" Value="Visible" />
                    </VisualState.Setters>
                </VisualState>
                <VisualState x:Name="HoverButtonsHidden" />
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <StackPanel>
            <TextBlock Text="{x:Bind PodcastObject.Title, Mode=OneWay}" Style="{StaticResource TitleTextBlockStyle}" />
            <TextBlock Text="{x:Bind PodcastObject.Description, Mode=OneWay}" Style="{StaticResource SubtitleTextBlockStyle}" />
            <TextBlock Text="{x:Bind PodcastObject.IsFavorite, Mode=OneWay}" Style="{StaticResource SubtitleTextBlockStyle}"/>
        </StackPanel>
        <Grid Grid.Column="1" x:Name="hoverArea" Visibility="Collapsed" VerticalAlignment="Stretch">
            <AppBarButton Icon="OutlineStar" Label="Favorite" Command="{StaticResource favoriteCommand}" CommandParameter="{x:Bind PodcastObject, Mode=OneWay}" IsTabStop="False" VerticalAlignment="Stretch"  />
        </Grid>
    </Grid>
</UserControl>
```

<span data-ttu-id="db224-244">Die Hoverschaltflächen sollten angezeigt bzw. ausgeblendet werden, sobald der Mauszeiger auf dem Element platziert oder von ihm entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="db224-244">The hover buttons should appear and disappear when the mouse enters and exits the item.</span></span> <span data-ttu-id="db224-245">Zur Reaktion auf Mausereignisse können Sie die Ereignisse [PointerEntered](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.PointerEnteredEvent) und [PointerExited](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.PointerExitedEvent) in „PodcastUserControl“ verwenden.</span><span class="sxs-lookup"><span data-stu-id="db224-245">To respond to mouse events, you can use the [PointerEntered](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.PointerEnteredEvent) and [PointerExited](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement.PointerExitedEvent) events on the PodcastUserControl.</span></span>

**<span data-ttu-id="db224-246">PodcastUserControl.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="db224-246">PodcastUserControl.xaml.cs</span></span>**
```csharp
protected override void OnPointerEntered(PointerRoutedEventArgs e)
{
    base.OnPointerEntered(e);

    // Only show hover buttons when the user is using mouse or pen.
    if (e.Pointer.PointerDeviceType == Windows.Devices.Input.PointerDeviceType.Mouse || e.Pointer.PointerDeviceType == Windows.Devices.Input.PointerDeviceType.Pen)
    {
        VisualStateManager.GoToState(this, "HoverButtonsShown", true);
    }
}

protected override void OnPointerExited(PointerRoutedEventArgs e)
{
    base.OnPointerExited(e);

    VisualStateManager.GoToState(this, "HoverButtonsHidden", true);
}
```

<span data-ttu-id="db224-247">Die im Hoverzustand angezeigten Schaltflächen sind nur bei der Eingabe über Zeigegeräte verfügbar.</span><span class="sxs-lookup"><span data-stu-id="db224-247">The buttons displayed in the hover state will only be accessible via the pointer input type.</span></span> <span data-ttu-id="db224-248">Da diese Schaltflächen ausschließlich für die Eingabe über Zeigegeräte zur Verfügung stehen, möchten Sie zur Optimierung der Zeigereingabe möglicherweise den Abstand um das jeweilige Schaltflächensymbol minimieren oder vollständig entfernen.</span><span class="sxs-lookup"><span data-stu-id="db224-248">Because these buttons are limited to pointer input, you may choose to minimize or remove the padding around the icon of the button to optimize for pointer input.</span></span> <span data-ttu-id="db224-249">Wenn Sie sich dazu entscheiden, muss die Schaltfläche mindestens 20×20px groß sein, damit sie mit Stift und Maus noch gut bedienbar ist.</span><span class="sxs-lookup"><span data-stu-id="db224-249">If you choose to do so, ensure that the button footprint is at least 20x20px to remain usable with pen and mouse.</span></span>

### <a name="touch-accelerators"></a><span data-ttu-id="db224-250">Beschleuniger für die Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="db224-250">Touch accelerators</span></span>

#### <a name="swipe"></a><span data-ttu-id="db224-251">Wischgesten</span><span class="sxs-lookup"><span data-stu-id="db224-251">Swipe</span></span>

![Aufrufen eines Befehls per Wischgeste](images/ContextualCommand_Swipe.png)

<span data-ttu-id="db224-253">Wischgestenbasierte Befehle sind ein Beschleuniger für die Toucheingabe. Sie ermöglichen es Benutzern von Touchgeräten, häufig verwendete sekundäre Aktionen per Touchgeste auszuführen.</span><span class="sxs-lookup"><span data-stu-id="db224-253">Swipe commanding is a touch accelerator that enables users on touch devices to perform common secondary actions using touch.</span></span> <span data-ttu-id="db224-254">Mithilfe von Wischgesten können Benutzer auf Touchgeräten schnell und natürlich mit Inhalten interagieren. So können sie beispielsweise gängige Aktionen wie „Löschen per Wischen“ oder „Aufrufen per Wischen“ durchführen.</span><span class="sxs-lookup"><span data-stu-id="db224-254">Swipe empowers touch users to quickly and naturally interact with content, using common actions like Swipe-to-Delete or Swipe-to-Invoke.</span></span> <span data-ttu-id="db224-255">Weitere Informationen finden Sie im Artikel zum Thema [Wischgestenbasierte Befehle](swipe.md).</span><span class="sxs-lookup"><span data-stu-id="db224-255">See the [swipe commanding](swipe.md) article to learn more.</span></span>

<span data-ttu-id="db224-256">Zur Integration von Wischgesten in Ihre Sammlung sind zwei Komponenten erforderlich: „SwipeItems" als Host für die Befehle und „SwipeControl“ als Element-Wrapper, der Interaktionen per Wischgeste möglich macht.</span><span class="sxs-lookup"><span data-stu-id="db224-256">In order to integrate swipe into your collection, you need two components: SwipeItems, which hosts the commands; and a SwipeControl, which wraps the item and allows for swipe interaction.</span></span>

<span data-ttu-id="db224-257">„SwipeItems“ kann als Ressource in „PodcastUserControl“ definiert werden.</span><span class="sxs-lookup"><span data-stu-id="db224-257">The SwipeItems can be defined as a Resource in the PodcastUserControl.</span></span> <span data-ttu-id="db224-258">In diesem Beispiel enthält „SwipeItems" einen Befehl, über den sich ein Element als Favorit speichern lässt.</span><span class="sxs-lookup"><span data-stu-id="db224-258">In this example, SwipeItems contains a command to Favorite an item.</span></span>

```xaml
<UserControl.Resources>
    <SymbolIconSource x:Key="FavoriteIcon" Symbol="Favorite"/>
    <SwipeItems x:Key="RevealOtherCommands" Mode="Reveal">
        <SwipeItem IconSource="{StaticResource FavoriteIcon}" Text="Favorite" Background="Yellow" Invoked="SwipeItem_Invoked"/>
    </SwipeItems>
</UserControl.Resources>
```

<span data-ttu-id="db224-259">„SwipeControl“ fungiert als Wrapper für das Element und erlaubt es dem Benutzer, per Wischgesten mit ihm zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="db224-259">The SwipeControl wraps the item and allows the user to interact with it using the swipe gesture.</span></span> <span data-ttu-id="db224-260">Beachten Sie, dass „SwipeControl“ einen Verweis auf „SwipeItems“ in seiner Eigenschaft „RightItems“ enthält.</span><span class="sxs-lookup"><span data-stu-id="db224-260">Notice that the SwipeControl contains a reference to the SwipeItems as its RightItems.</span></span> <span data-ttu-id="db224-261">Das Element „Als Favorit speichern“ wird angezeigt, wenn der Benutzer von rechts nach links wischt.</span><span class="sxs-lookup"><span data-stu-id="db224-261">The Favorite item will show when the user swipes from right to left.</span></span>

```xaml
<SwipeControl x:Name="swipeContainer" RightItems="{StaticResource RevealOtherCommands}">
   <!-- The visual state groups moved from the Grid to the SwipeControl, since the SwipeControl wraps the Grid. -->
   <VisualStateManager.VisualStateGroups>
       <VisualStateGroup x:Name="HoveringStates">
           <VisualState x:Name="HoverButtonsShown">
               <VisualState.Setters>
                   <Setter Target="hoverArea.Visibility" Value="Visible" />
               </VisualState.Setters>
           </VisualState>
           <VisualState x:Name="HoverButtonsHidden" />
       </VisualStateGroup>
   </VisualStateManager.VisualStateGroups>
   <Grid Margin="12,0,12,0">
       <Grid.ColumnDefinitions>
           <ColumnDefinition Width="*" />
           <ColumnDefinition Width="Auto" />
       </Grid.ColumnDefinitions>
       <StackPanel>
           <TextBlock Text="{x:Bind PodcastObject.Title, Mode=OneWay}" Style="{StaticResource TitleTextBlockStyle}" />
           <TextBlock Text="{x:Bind PodcastObject.Description, Mode=OneWay}" Style="{StaticResource SubtitleTextBlockStyle}" />
           <TextBlock Text="{x:Bind PodcastObject.IsFavorite, Mode=OneWay}" Style="{StaticResource SubtitleTextBlockStyle}"/>
       </StackPanel>
       <Grid Grid.Column="1" x:Name="hoverArea" Visibility="Collapsed" VerticalAlignment="Stretch">
           <AppBarButton Icon="OutlineStar" Command="{StaticResource favoriteCommand}" CommandParameter="{x:Bind PodcastObject, Mode=OneWay}" IsTabStop="False" LabelPosition="Collapsed" VerticalAlignment="Stretch"  />
       </Grid>
   </Grid>
</SwipeControl>
```

<span data-ttu-id="db224-262">Sobald der Benutzer über das Display wischt, um den Befehl „Als Favorit speichern“ aufzurufen, wird die Methode „Invoked“ aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="db224-262">When the user swipes to invoke the Favorite command, the Invoked method is called.</span></span>

```csharp
private void SwipeItem_Invoked(SwipeItem sender, SwipeItemInvokedEventArgs args)
{
    // Favorite the item using the defined command
    var favoriteCommand = Application.Current.Resources["favoriteCommand"] as ICommand;
    favoriteCommand.Execute(PodcastObject);
}
```

#### <a name="pull-to-refresh"></a><span data-ttu-id="db224-263">Aktualisieren durch Ziehen</span><span class="sxs-lookup"><span data-stu-id="db224-263">Pull to refresh</span></span>

<span data-ttu-id="db224-264">Mithilfe der Aktion „Aktualisieren durch Ziehen“ können Benutzer eine Datensammlung per Touchgeste nach unten ziehen, um weitere Daten abzurufen.</span><span class="sxs-lookup"><span data-stu-id="db224-264">Pull to refresh lets a user pull down on a collection of data using touch in order to retrieve more data.</span></span> <span data-ttu-id="db224-265">Weitere Informationen finden Sie im Artikel zum Thema [Aktualisieren durch Ziehen](pull-to-refresh.md).</span><span class="sxs-lookup"><span data-stu-id="db224-265">See the [pull to refresh](pull-to-refresh.md) article to learn more.</span></span>

### <a name="pen-accelerators"></a><span data-ttu-id="db224-266">Beschleuniger für die Stifteingabe</span><span class="sxs-lookup"><span data-stu-id="db224-266">Pen accelerators</span></span>

<span data-ttu-id="db224-267">Die Eingabe per Stift ist ebenso präzise wie die Eingabe per Zeigegerät.</span><span class="sxs-lookup"><span data-stu-id="db224-267">The pen input type provides the precision of pointer input.</span></span> <span data-ttu-id="db224-268">Mit stiftbasierten Beschleunigern können Benutzer gängige Aktionen wie beispielsweise das Öffnen von Kontextmenüs durchführen.</span><span class="sxs-lookup"><span data-stu-id="db224-268">Users can perform common actions such as opening context menus using pen-based accelerators.</span></span> <span data-ttu-id="db224-269">Zum Öffnen eines Kontextmenüs kann der Benutzer mit gedrückter Drucktaste auf das Display tippen oder alternativ lange auf den Inhalt drücken.</span><span class="sxs-lookup"><span data-stu-id="db224-269">To open a context menu, users can tap the screen with the barrel button pressed, or long press on the content.</span></span> <span data-ttu-id="db224-270">Er kann den Stift auch über Inhalten platzieren, um ähnlich wie mit der Maus Details zur Benutzeroberfläche (z.B. QuickInfos) aufzurufen oder sekundäre Hoveraktionen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="db224-270">Users can also use the pen to hover over content to get a deeper understanding of the UI like displaying tooltips, or to reveal secondary hover actions, similar to mouse.</span></span>

<span data-ttu-id="db224-271">Wie Sie Ihre App für die Stifteingabe optimieren können, erfahren Sie im Artikel zum Thema [Interaktion per Eingabestift](../input/pen-and-stylus-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="db224-271">To optimize your app for pen input, see the [pen and stylus interaction](../input/pen-and-stylus-interactions.md) article.</span></span>


## <a name="dos-and-donts"></a><span data-ttu-id="db224-272">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="db224-272">Do's and don'ts</span></span>

* <span data-ttu-id="db224-273">Stellen Sie sicher, dass Ihre Benutzer auf sämtliche Befehle zugreifen können, und zwar über alle Typen von UWP-Geräten.</span><span class="sxs-lookup"><span data-stu-id="db224-273">Do make sure that users can access all commands from all types of UWP devices.</span></span>
* <span data-ttu-id="db224-274">Integrieren Sie ein Kontextmenü, das alle für ein Sammlungselement verfügbaren Befehle bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="db224-274">Do include a context menu that provides access to all the commands available for a collection item.</span></span> 
* <span data-ttu-id="db224-275">Implementieren Sie Eingabebeschleuniger für häufig verwendete Befehle.</span><span class="sxs-lookup"><span data-stu-id="db224-275">Do provide input accelerators for frequently-used commands.</span></span> 
* <span data-ttu-id="db224-276">Verwenden Sie zur Implementierung von Befehlen die [Schnittstelle „ICommand“](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand).</span><span class="sxs-lookup"><span data-stu-id="db224-276">Do use the [ICommand interface](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand) to implement commands.</span></span> 

## <a name="related-topics"></a><span data-ttu-id="db224-277">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="db224-277">Related topics</span></span>
* [<span data-ttu-id="db224-278">Schnittstelle „ICommand“</span><span class="sxs-lookup"><span data-stu-id="db224-278">ICommand Interface</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.ICommand)
* [<span data-ttu-id="db224-279">Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="db224-279">Menus and Context Menus</span></span>](menus.md)
* [<span data-ttu-id="db224-280">Wischgesten</span><span class="sxs-lookup"><span data-stu-id="db224-280">Swipe</span></span>](swipe.md)
* [<span data-ttu-id="db224-281">Aktualisieren durch Ziehen</span><span class="sxs-lookup"><span data-stu-id="db224-281">Pull to refresh</span></span>](pull-to-refresh.md)
* [<span data-ttu-id="db224-282">Interaktion per Eingabestift</span><span class="sxs-lookup"><span data-stu-id="db224-282">Pen and stylus interaction</span></span>](../input/pen-and-stylus-interactions.md)
* [<span data-ttu-id="db224-283">App-Optimierung für Gamepads und Xbox</span><span class="sxs-lookup"><span data-stu-id="db224-283">Tailor your app for gamepad and Xbox</span></span>](../devices/designing-for-tv.md)
