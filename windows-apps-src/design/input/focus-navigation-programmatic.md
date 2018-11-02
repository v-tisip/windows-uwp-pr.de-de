---
author: Karl-Bridge-Microsoft
Description: Learn how to programmatically manage focus navigation with keyboard, gamepad, and accessibility tools in a UWP app.
title: Programmgesteuerte Fokusnavigation mit Tastatur, Gamepad und Bedienungshilfen
label: Programmatic focus navigation
keywords: Tastatur, Gamecontroller, Fernbedienung, Navigation, Navigationsstrategie, Eingabe, Benutzerinteraktion, Bedienungshilfen, Verwendbarkeit
ms.author: kbridge
ms.date: 03/19/2018
ms.topic: article
pm-contact: miguelrb
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: d2317b419a2679d13e846690bbaca0eb212a245e
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5938827"
---
# <a name="programmatic-focus-navigation"></a><span data-ttu-id="bea45-103">Programmgesteuerte Fokusnavigation</span><span class="sxs-lookup"><span data-stu-id="bea45-103">Programmatic focus navigation</span></span>

![Tastatur, Fernbedienung und Steuerkreuz](images/dpad-remote/dpad-remote-keyboard.png)

<span data-ttu-id="bea45-105">Verwenden Sie die [FocusManager.TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_)-Methode oder die [FindNextElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextElement_Windows_UI_Xaml_Input_FocusNavigationDirection_)-Methode, um den Fokus in Ihrer UWP-Anwendung programmgesteuert zu verlagern.</span><span class="sxs-lookup"><span data-stu-id="bea45-105">To move focus programmatically in your UWP application, you can use either the [FocusManager.TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_) method or the [FindNextElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextElement_Windows_UI_Xaml_Input_FocusNavigationDirection_) method.</span></span>

<span data-ttu-id="bea45-106">[TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_) versucht, den Fokus von dem Element mit Fokus auf das nächste fokussierbare Element in der angegebenen Richtung zu ändern, während [FindNextElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextElement_Windows_UI_Xaml_Input_FocusNavigationDirection_) das Element abruft (als [DependencyObject](https://docs.microsoft.com/uwp/api/windows.ui.xaml.dependencyobject)), das den Fokus basierend auf der angegebenen Navigationsrichtung erhalten wird (nur direktionale Navigation, kann nicht verwendet werden, um die TAB-Navigation zu emulieren).</span><span class="sxs-lookup"><span data-stu-id="bea45-106">[TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_) attempts to change focus from the element with focus to the next focusable element in the specified direction, while [FindNextElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextElement_Windows_UI_Xaml_Input_FocusNavigationDirection_) retrieves the element (as a [DependencyObject](https://docs.microsoft.com/uwp/api/windows.ui.xaml.dependencyobject)) that will receive focus based on the specified navigation direction (directional navigation only, cannot be used to emulate tab navigation).</span></span>

> [!NOTE]
> <span data-ttu-id="bea45-107">Wir empfehlen die Verwendung der [FindNextElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextElement_Windows_UI_Xaml_Input_FocusNavigationDirection_)-Methode anstelle von [FindNextFocusableElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextFocusableElement_Windows_UI_Xaml_Input_FocusNavigationDirection_), da FindNextFocusableElement ein UIElement abruft, das Null zurückgibt, wenn das nächste fokussierbare Element kein UIElement ist (z.B. ein Hyperlink-Objekt).</span><span class="sxs-lookup"><span data-stu-id="bea45-107">We recommend using the [FindNextElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextElement_Windows_UI_Xaml_Input_FocusNavigationDirection_) method instead of [FindNextFocusableElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextFocusableElement_Windows_UI_Xaml_Input_FocusNavigationDirection_) because FindNextFocusableElement retrieves a UIElement, which returns null if the next focusable element is not a UIElement (such as a Hyperlink object).</span></span> 

## <a name="find-a-focus-candidate-within-a-scope"></a><span data-ttu-id="bea45-108">Suche nach einem Fokuskandidaten in einem Bereich</span><span class="sxs-lookup"><span data-stu-id="bea45-108">Find a focus candidate within a scope</span></span>

<span data-ttu-id="bea45-109">Sie können das Verhalten der Fokusnavigation für [TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_) und [FindNextElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextElement_Windows_UI_Xaml_Input_FocusNavigationDirection_) anpassen, einschließlich der Suche nach dem nächsten Fokuskandidaten in einer bestimmten UI-Struktur oder dem Ausschließen bestimmter Elemente, sodass diese nicht in Betracht gezogen werden.</span><span class="sxs-lookup"><span data-stu-id="bea45-109">You can customize the focus navigation behavior for both [TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_) and [FindNextElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextElement_Windows_UI_Xaml_Input_FocusNavigationDirection_), including searching for the next focus candidate within a specific UI tree or excluding specific elements from consideration.</span></span>

<span data-ttu-id="bea45-110">In diesem Beispiel wird ein TicTacToe-Spiel verwendet, um die Methoden [TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_) und [FindNextElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextElement_Windows_UI_Xaml_Input_FocusNavigationDirection_) zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="bea45-110">This example uses a TicTacToe game to demonstrate the [TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_) and [FindNextElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindNextElement_Windows_UI_Xaml_Input_FocusNavigationDirection_) methods.</span></span>

```xaml
<StackPanel Orientation="Horizontal"
                VerticalAlignment="Center"
                HorizontalAlignment="Center" >
    <Button Content="Start Game" />
    <Button Content="Undo Movement" />
    <Grid x:Name="TicTacToeGrid" KeyDown="OnKeyDown">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="50" />
            <ColumnDefinition Width="50" />
            <ColumnDefinition Width="50" />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="50" />
            <RowDefinition Height="50" />
            <RowDefinition Height="50" />
        </Grid.RowDefinitions>
        <myControls:TicTacToeCell 
            Grid.Column="0" Grid.Row="0" 
            x:Name="Cell00" />
        <myControls:TicTacToeCell 
            Grid.Column="1" Grid.Row="0" 
            x:Name="Cell10"/>
        <myControls:TicTacToeCell 
            Grid.Column="2" Grid.Row="0" 
            x:Name="Cell20"/>
        <myControls:TicTacToeCell 
            Grid.Column="0" Grid.Row="1" 
            x:Name="Cell01"/>
        <myControls:TicTacToeCell 
            Grid.Column="1" Grid.Row="1" 
            x:Name="Cell11"/>
        <myControls:TicTacToeCell 
            Grid.Column="2" Grid.Row="1" 
            x:Name="Cell21"/>
        <myControls:TicTacToeCell 
            Grid.Column="0" Grid.Row="2" 
            x:Name="Cell02"/>
        <myControls:TicTacToeCell 
            Grid.Column="1" Grid.Row="2" 
            x:Name="Cell22"/>
        <myControls:TicTacToeCell 
            Grid.Column="2" Grid.Row="2" 
            x:Name="Cell32"/>
    </Grid>
</StackPanel>
```

```csharp
private void OnKeyDown(object sender, KeyRoutedEventArgs e)
{
    DependencyObject candidate = null;

    var options = new FindNextElementOptions ()
    {
        SearchRoot = TicTacToeGrid,
        NavigationStrategy = NavigationStrategyMode.Heuristic
    };

    switch (e.Key)
    {
        case Windows.System.VirtualKey.Up:
            candidate = 
                FocusManager.FindNextElement(
                    FocusNavigationDirection.Up, options);
            break;
        case Windows.System.VirtualKey.Down:
            candidate = 
                FocusManager.FindNextElement(
                    FocusNavigationDirection.Down, options);
            break;
        case Windows.System.VirtualKey.Left:
            candidate = FocusManager.FindNextElement(
                FocusNavigationDirection.Left, options);
            break;
        case Windows.System.VirtualKey.Right:
            candidate = 
                FocusManager.FindNextElement(
                    FocusNavigationDirection.Right, options);
            break;
    }
    // Also consider whether candidate is a Hyperlink, WebView, or TextBlock.
    if (candidate != null && candidate is Control)
    {
        (candidate as Control).Focus(FocusState.Keyboard);
    }
}
```

<span data-ttu-id="bea45-111">Verwenden Sie [FindNextElementOptions](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.input.findnextelementoptions), um weiter anzupassen, wie Fokuskandidaten identifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="bea45-111">Use [FindNextElementOptions](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.input.findnextelementoptions) to further customize how focus candidates are identified.</span></span> <span data-ttu-id="bea45-112">Dieses -Objekt stellt die folgenden Eigenschaften bereit:</span><span class="sxs-lookup"><span data-stu-id="bea45-112">This object provides the following properties:</span></span>

- <span data-ttu-id="bea45-113">[SearchRoot](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_SearchRoot): Legen Sie den Bereich für die Suche nach Fokusnavigationskandidaten auf die untergeordneten Elemente dieses DependencyObject fest.</span><span class="sxs-lookup"><span data-stu-id="bea45-113">[SearchRoot](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_SearchRoot) - Scope the search for focus navigation candidates to the children of this DependencyObject.</span></span> <span data-ttu-id="bea45-114">Null gibt an, dass die Suche im Stamm der visuellen Struktur beginnt.</span><span class="sxs-lookup"><span data-stu-id="bea45-114">Null indicates to start the search from the root of the visual tree.</span></span>

> [!Important] 
> <span data-ttu-id="bea45-115">Wenn eine oder mehrere Transformationen auf die Nachfolgerelemente von **SearchRoot** angewendet werden, die sie außerhalb des direktionalen Bereichs platzieren, werden diese Elemente weiterhin als Kandidaten betrachtet.</span><span class="sxs-lookup"><span data-stu-id="bea45-115">If one or more transforms are applied to the descendants of **SearchRoot** that place them outside of the directional area, these elements are still considered candidates.</span></span>

- <span data-ttu-id="bea45-116">[ExclusionRect](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_ExclusionRect): Fokusnavigationskandidaten werden mit einem „fiktiven“ umgebenden Rechteck identifiziert, und dabei werden alle überlappenden Objekte aus dem Navigationsfokus ausgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="bea45-116">[ExclusionRect](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_ExclusionRect) - Focus navigation candidates are identified using a "fictitious" bounding rectangle where all overlapping objects are excluded from navigation focus.</span></span> <span data-ttu-id="bea45-117">Dieses Rechteck dient nur zur Berechnung und wird nicht der visuellen Struktur hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="bea45-117">This rectangle is used only for calculations and is never added to the visual tree.</span></span>
- <span data-ttu-id="bea45-118">[HintRect](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_HintRect): Fokusnavigationskandidaten werden mit einem „fiktiven“ umgebenden Rechteck identifiziert, das Elemente ermittelt, die am ehesten den Fokus erhalten.</span><span class="sxs-lookup"><span data-stu-id="bea45-118">[HintRect](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_HintRect) - Focus navigation candidates are identified using a "fictitious" bounding rectangle that identifies the elements most likely to receive focus.</span></span> <span data-ttu-id="bea45-119">Dieses Rechteck dient nur zur Berechnung und wird nicht der visuellen Struktur hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="bea45-119">This rectangle is used only for calculations and is never added to the visual tree.</span></span>
- <span data-ttu-id="bea45-120">[XYFocusNavigationStrategyOverride](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_XYFocusNavigationStrategyOverride): Navigationsstrategie, die verwendet wird, um das beste Kandidatenelement zum Verlagern des Fokus zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="bea45-120">[XYFocusNavigationStrategyOverride](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_XYFocusNavigationStrategyOverride) - The focus navigation strategy used to identify the best candidate element to receive focus.</span></span>

<span data-ttu-id="bea45-121">In dieser folgenden Abbildung sind einige dieser Konzepte veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="bea45-121">The following image illustrates some of these concepts.</span></span> 

<span data-ttu-id="bea45-122">Wenn der Fokus auf Element B liegt, identifiziert FindNextElement bei der Navigation nach rechts I als Fokuskandidaten.</span><span class="sxs-lookup"><span data-stu-id="bea45-122">When element B has focus, FindNextElement identifies I as the focus candidate when navigating to the right.</span></span> <span data-ttu-id="bea45-123">Dafür gibt es folgende Gründe:</span><span class="sxs-lookup"><span data-stu-id="bea45-123">The reasons for this are:</span></span>
- <span data-ttu-id="bea45-124">Da [HintRect](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_HintRect) bei A liegt, ist die erste Referenz A, nicht B.</span><span class="sxs-lookup"><span data-stu-id="bea45-124">Because of the [HintRect](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_HintRect) on A, the starting reference is A, not B</span></span>
- <span data-ttu-id="bea45-125">C ist kein Kandidat, da MyPanel als [SearchRoot](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_SearchRoot) angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="bea45-125">C is not a candidate because MyPanel has been specified as the [SearchRoot](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_SearchRoot)</span></span>
- <span data-ttu-id="bea45-126">F ist kein Kandidat, da eine Überlappung mit [ExclusionRect](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_ExclusionRect) vorliegt.</span><span class="sxs-lookup"><span data-stu-id="bea45-126">F is not a candidate because the [ExclusionRect](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.findnextelementoptions#Windows_UI_Xaml_Input_FindNextElementOptions_ExclusionRect) overlaps it</span></span>

![Benutzerdefiniertes Fokusnavigationsverhalten mithilfe von Navigationshinweisen](images/keyboard/navigation-hints.png)

*<span data-ttu-id="bea45-128">Benutzerdefiniertes Fokusnavigationsverhalten mithilfe von Navigationshinweisen</span><span class="sxs-lookup"><span data-stu-id="bea45-128">Custom focus navigation behavior using navigation hints</span></span>*

## <a name="navigation-focus-events"></a><span data-ttu-id="bea45-129">Navigationsfokusereignisse</span><span class="sxs-lookup"><span data-stu-id="bea45-129">Navigation focus events</span></span>

### <a name="nofocuscandidatefound-event"></a><span data-ttu-id="bea45-130">NoFocusCandidateFound-Ereignis</span><span class="sxs-lookup"><span data-stu-id="bea45-130">NoFocusCandidateFound event</span></span>

<span data-ttu-id="bea45-131">Das Ereignis [UIElement.NoFocusCandidateFound](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_NoFocusCandidateFound) wird ausgelöst, wenn die TAB-Taste oder die Pfeiltasten gedrückt werden und kein Fokuskandidat in der angegebenen Richtung vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="bea45-131">The [UIElement.NoFocusCandidateFound](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement#Windows_UI_Xaml_UIElement_NoFocusCandidateFound) event is fired when the tab or arrow keys are pressed and there is no focus candidate in the specified direction.</span></span> <span data-ttu-id="bea45-132">Dieses Ereignis wird nicht für [TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_) ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="bea45-132">This event is not fired for [TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_).</span></span>

<span data-ttu-id="bea45-133">Da dies ein Routingereignis ist, erfolgt Bubbling vom fokussierten Element über die einzelnen übergeordneten Objekte zum Stamm der Objektstruktur nach oben.</span><span class="sxs-lookup"><span data-stu-id="bea45-133">Because this is a routed event, it bubbles from the focused element up through successive parent objects to the root of the object tree.</span></span> <span data-ttu-id="bea45-134">So können Sie das Ereignis verarbeiten, sofern angebracht.</span><span class="sxs-lookup"><span data-stu-id="bea45-134">This lets you handle the event wherever appropriate.</span></span>

<a name="split-view-code-sample"></a>

<span data-ttu-id="bea45-135">Das folgende Beispiel zeigt, wie ein Raster die geteilte Ansicht [SplitView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.splitview) öffnet, wenn der Benutzer versucht, den Fokus auf die ganz linke Seite des fokussierbaren Steuerelements zu verlagern (siehe [Entwerfen für Xbox und Fernsehgeräte](../devices/designing-for-tv.md#navigation-pane)).</span><span class="sxs-lookup"><span data-stu-id="bea45-135">Here, we show how a Grid opens a [SplitView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.splitview) when the user attempts to move focus to the left of the left-most focusable control (see [Designing for Xbox and TV](../devices/designing-for-tv.md#navigation-pane)).</span></span>

```xaml
<Grid NoFocusCandidateFound="OnNoFocusCandidateFound">
...
</Grid>
```

```csharp
private void OnNoFocusCandidateFound (
    UIElement sender, NoFocusCandidateFoundEventArgs args)
{
    if(args.NavigationDirection == FocusNavigationDirection.Left)
    {
        if(args.InputDevice == FocusInputDeviceKind.Keyboard ||
        args.InputDevice == FocusInputDeviceKind.GameController )
            {
                OpenSplitPaneView();
            }
        args.Handled = true;
    }
}
```

### <a name="gotfocus-and-lostfocus-events"></a><span data-ttu-id="bea45-136">GotFocus- und LostFocus-Ereignisse</span><span class="sxs-lookup"><span data-stu-id="bea45-136">GotFocus and LostFocus events</span></span>
<span data-ttu-id="bea45-137">Die Ereignisse [UIElement.GotFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GotFocus) und [UIElement.LostFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LostFocus) werden ausgelöst, wenn ein Element den Fokus erhält bzw. verliert.</span><span class="sxs-lookup"><span data-stu-id="bea45-137">The [UIElement.GotFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GotFocus) and [UIElement.LostFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LostFocus) events are fired when an element gets focus or loses focus, respectively.</span></span> <span data-ttu-id="bea45-138">Dieses Ereignis wird nicht für [TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_) ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="bea45-138">This event is not fired for [TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_).</span></span>

<span data-ttu-id="bea45-139">Da es sich hier um Routingereignisse handelt, erfolgt ein Bubbling vom fokussierten Element über die einzelnen übergeordneten Objekte zum Stamm der Objektstruktur nach oben.</span><span class="sxs-lookup"><span data-stu-id="bea45-139">Because these are routed events, they bubble from the focused element up through successive parent objects to the root of the object tree.</span></span> <span data-ttu-id="bea45-140">So können Sie das Ereignis verarbeiten, sofern angebracht.</span><span class="sxs-lookup"><span data-stu-id="bea45-140">This lets you handle the event wherever appropriate.</span></span>

### <a name="gettingfocus-and-losingfocus-events"></a><span data-ttu-id="bea45-141">GettingFocus- und LosingFocus-Ereignisse</span><span class="sxs-lookup"><span data-stu-id="bea45-141">GettingFocus and LosingFocus events</span></span>

<span data-ttu-id="bea45-142">Die Ereignisse [UIElement.GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus) und [UIElement.LosingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LosingFocus) werden vor den entsprechenden [UIElement.GotFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GotFocus)- und [UIElement.LostFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LostFocus)-Ereignissen ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="bea45-142">The [UIElement.GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus) and [UIElement.LosingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LosingFocus) events fire before the respective [UIElement.GotFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GotFocus) and [UIElement.LostFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LostFocus) events.</span></span> 

<span data-ttu-id="bea45-143">Da es sich hier um Routingereignisse handelt, erfolgt ein Bubbling vom fokussierten Element über die einzelnen übergeordneten Objekte zum Stamm der Objektstruktur nach oben.</span><span class="sxs-lookup"><span data-stu-id="bea45-143">Because these are routed events, they bubble from the focused element up through successive parent objects to the root of the object tree.</span></span> <span data-ttu-id="bea45-144">Da dies vor einer Änderung des Fokus stattfindet, können Sie die Fokusänderung umleiten oder abbrechen.</span><span class="sxs-lookup"><span data-stu-id="bea45-144">As this happens before a focus change takes place, you can redirect or cancel the focus change.</span></span>

<span data-ttu-id="bea45-145">[GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus) und [LosingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LosingFocus) sind synchrone Ereignisse, was heißt, dass der Fokus nicht verlagert wird, während das Bubbling für diese Ereignisse erfolgt.</span><span class="sxs-lookup"><span data-stu-id="bea45-145">[GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus) and [LosingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LosingFocus) are synchronous events so focus won’t be moved while these events are bubbling.</span></span> <span data-ttu-id="bea45-146">Da [GotFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GotFocus) und [LostFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LostFocus) asynchrone Ereignisse sind, kann jedoch nicht garantiert werden, dass der Fokus vor der Ausführung des Handlers nicht erneut verlagert wird.</span><span class="sxs-lookup"><span data-stu-id="bea45-146">However, [GotFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GotFocus) and [LostFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LostFocus) are asynchronous events, which means there is no guarantee that focus won’t move again before the handler is executed.</span></span>

<span data-ttu-id="bea45-147">Wenn der Fokus über einen Aufruf an [Control.Focus](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_Focus_Windows_UI_Xaml_FocusState_) verlagert wird, wird [GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus) während des Aufrufs ausgelöst, während [GotFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GotFocus) nach dem Aufruf ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="bea45-147">If focus moves through a call to [Control.Focus](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_Focus_Windows_UI_Xaml_FocusState_), [GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus) is raised during the call, while [GotFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GotFocus) is raised after the call.</span></span>

<span data-ttu-id="bea45-148">Das Ziel der Fokusnavigation kann während der Ereignisse [GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus) und [LosingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LosingFocus) (vor der Verlagerung des Fokus) über die [GettingFocusEventArgs.NewFocusedElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.gettingfocuseventargs#Windows_UI_Xaml_Input_GettingFocusEventArgs_NewFocusedElement) geändert werden.</span><span class="sxs-lookup"><span data-stu-id="bea45-148">The focus navigation target can be changed during the [GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus) and [LosingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LosingFocus) events (before focus moves) through the [GettingFocusEventArgs.NewFocusedElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.gettingfocuseventargs#Windows_UI_Xaml_Input_GettingFocusEventArgs_NewFocusedElement) property.</span></span> <span data-ttu-id="bea45-149">Selbst wenn das Ziel geändert wird, erfolgt weiterhin ein Ereignis-Bubbling, und das Ziel kann erneut geändert werden.</span><span class="sxs-lookup"><span data-stu-id="bea45-149">Even if the target is changed, the event still bubbles and the target can be changed again.</span></span>

<span data-ttu-id="bea45-150">Um Eintrittsvarianzprobleme zu vermeiden, wird eine Ausnahme ausgegeben, wenn Sie versuchen, den Fokus zu verlagern (mit [TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_) oder [Control.Focus](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_Focus_Windows_UI_Xaml_FocusState_)), während für diese Ereignisse das Bubbling erfolgt.</span><span class="sxs-lookup"><span data-stu-id="bea45-150">To avoid reentrancy issues, an exception is thrown if you try to move focus (using [TryMoveFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_TryMoveFocus_Windows_UI_Xaml_Input_FocusNavigationDirection_) or [Control.Focus](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control#Windows_UI_Xaml_Controls_Control_Focus_Windows_UI_Xaml_FocusState_)) while these events are bubbling.</span></span>

<span data-ttu-id="bea45-151">Diese Ereignisse werden unabhängig vom Grund der Fokusverlagerung ausgelöst (z. B. TAB-Navigation, direktionale Navigation und programmgesteuerte Navigation).</span><span class="sxs-lookup"><span data-stu-id="bea45-151">These events are fired regardless of the reason for the focus moving (including tab navigation, directional navigation, and programmatic navigation).</span></span>

<span data-ttu-id="bea45-152">Fokusereignisse werden in der folgenden Reihenfolge ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="bea45-152">Here is the order of execution for the focus events:</span></span>

1.  <span data-ttu-id="bea45-153">[LosingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LosingFocus) Wenn der Fokus auf das Fokuselement zurückgesetzt wird, das den Fokus verloren hat, oder [TryCancel](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.losingfocuseventargs#Windows_UI_Xaml_Input_LosingFocusEventArgs_TryCancel) erfolgreich ist, werden keine weiteren Ereignisse ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="bea45-153">[LosingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LosingFocus) If focus is reset back to the losing focus element or [TryCancel](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.losingfocuseventargs#Windows_UI_Xaml_Input_LosingFocusEventArgs_TryCancel) is successful, no further events are fired.</span></span>
2.  <span data-ttu-id="bea45-154">[GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus) Wenn der Fokus auf das Fokuselement zurückgesetzt wird, das den Fokus verloren hat, oder [TryCancel](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.gettingfocuseventargs#Windows_UI_Xaml_Input_GettingFocusEventArgs_TryCancel) erfolgreich ist, werden keine weiteren Ereignisse ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="bea45-154">[GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus) If focus is reset back to the losing focus element or [TryCancel](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.gettingfocuseventargs#Windows_UI_Xaml_Input_GettingFocusEventArgs_TryCancel) is successful, no further events are fired.</span></span>
3.  [<span data-ttu-id="bea45-155">LostFocus</span><span class="sxs-lookup"><span data-stu-id="bea45-155">LostFocus</span></span>](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LostFocus)
4.  [<span data-ttu-id="bea45-156">GotFocus</span><span class="sxs-lookup"><span data-stu-id="bea45-156">GotFocus</span></span>](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GotFocus)

<span data-ttu-id="bea45-157">Die folgende Abbildung zeigt, wie beim Verschieben nach rechts von A XYFocus B4 als Kandidat auswählt.</span><span class="sxs-lookup"><span data-stu-id="bea45-157">The following image shows how, when moving to the right from A, the XYFocus chooses B4 as a candidate.</span></span> <span data-ttu-id="bea45-158">B4 löst dann das GettingFocus-Ereignis aus, wobei ListView die Möglichkeit hat, den Fokus erneut zu B3 zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="bea45-158">B4 then fires the GettingFocus event where the ListView has the opportunity to reassign focus to B3.</span></span>

![Ändern des Fokusnavigationsziels bei einem GettingFocus-Ereignis](images/keyboard/focus-events.png)

*<span data-ttu-id="bea45-160">Ändern des Fokusnavigationsziels bei einem GettingFocus-Ereignis</span><span class="sxs-lookup"><span data-stu-id="bea45-160">Changing focus navigation target on GettingFocus event</span></span>*

<span data-ttu-id="bea45-161">Im Folgenden erfahren Sie, wie Sie das [GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus)-Ereignis verarbeiten und den Fokus umleiten.</span><span class="sxs-lookup"><span data-stu-id="bea45-161">Here, we show how to handle the [GettingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_GettingFocus) event and redirect focus.</span></span>

```XAML
<StackPanel Orientation="Horizontal">
    <Button Content="A" />
    <ListView x:Name="MyListView" SelectedIndex="2" GettingFocus="OnGettingFocus">
        <ListViewItem>LV1</ListViewItem>
        <ListViewItem>LV2</ListViewItem>
        <ListViewItem>LV3</ListViewItem>
        <ListViewItem>LV4</ListViewItem>
        <ListViewItem>LV5</ListViewItem>
    </ListView>
</StackPanel>
```

```csharp
private void OnGettingFocus(UIElement sender, GettingFocusEventArgs args)
{
    //Redirect the focus only when the focus comes from outside of the ListView.
    // move the focus to the selected item
    if (MyListView.SelectedIndex != -1 && 
        IsNotAChildOf(MyListView, args.OldFocusedElement))
    {
        var selectedContainer = 
            MyListView.ContainerFromItem(MyListView.SelectedItem);
        if (args.FocusState == 
            FocusState.Keyboard && 
            args.NewFocusedElement != selectedContainer)
        {
            args.TryRedirect(
                MyListView.ContainerFromItem(MyListView.SelectedItem));
            args.Handled = true;
        }
    }
}
```

<span data-ttu-id="bea45-162">Im Folgenden erfahren Sie, wie Sie das [LosingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LosingFocus)-Ereignis für [CommandBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbar) verarbeiten und den Fokus festlegen, wenn das Menü geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="bea45-162">Here, we show how to handle the [LosingFocus](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_LosingFocus) event for a [CommandBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbar) and set focus when the menu is closed.</span></span>

```XAML
<CommandBar x:Name="MyCommandBar" LosingFocus="OnLosingFocus">
     <AppBarButton Icon="Back" Label="Back" />
     <AppBarButton Icon="Stop" Label="Stop" />
     <AppBarButton Icon="Play" Label="Play" />
     <AppBarButton Icon="Forward" Label="Forward" />

     <CommandBar.SecondaryCommands>
         <AppBarButton Icon="Like" Label="Like" />
         <AppBarButton Icon="Share" Label="Share" />
     </CommandBar.SecondaryCommands>
 </CommandBar>
```

```csharp
private void OnLosingFocus(UIElement sender, LosingFocusEventArgs args)
{
    if (MyCommandBar.IsOpen == true && 
        IsNotAChildOf(MyCommandBar, args.NewFocusedElement))
    {
        if (args.TryCancel())
        {
            args.Handled = true;
        }
    }
}
```

## <a name="find-the-first-and-last-focusable-element"></a><span data-ttu-id="bea45-163">Suchen des ersten und letzten fokussierbaren Elements</span><span class="sxs-lookup"><span data-stu-id="bea45-163">Find the first and last focusable element</span></span>

<span data-ttu-id="bea45-164">Die Methoden [FocusManager.FindFirstFocusableElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindFirstFocusableElement_Windows_UI_Xaml_DependencyObject_) und [FocusManager.FindLastFocusableElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindLastFocusableElement_Windows_UI_Xaml_DependencyObject_) ermöglichen das Verlagern des Fokus auf das erste oder letzte fokussierbare Element im Bereich eines Objekts ([UIElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement)-Elementstruktur oder [TextElement](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.documents.textelement)-Textstruktur).</span><span class="sxs-lookup"><span data-stu-id="bea45-164">The [FocusManager.FindFirstFocusableElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindFirstFocusableElement_Windows_UI_Xaml_DependencyObject_) and [FocusManager.FindLastFocusableElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.input.focusmanager#Windows_UI_Xaml_Input_FocusManager_FindLastFocusableElement_Windows_UI_Xaml_DependencyObject_) methods move focus to the first or last focusable element within the scope of an object (the element tree of a [UIElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement) or the text tree of a [TextElement](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.documents.textelement)).</span></span> <span data-ttu-id="bea45-165">Der Bereich wird im Aufruf angegeben (wenn das Argument null ist, ist der Bereich das aktuelle Fenster).</span><span class="sxs-lookup"><span data-stu-id="bea45-165">The scope is specified in the call (if the argument is null, the scope is the current window).</span></span>

<span data-ttu-id="bea45-166">Wenn keine Fokuskandidaten im Bereich identifiziert werden können, wird Null zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="bea45-166">If no focus candidates can be identified in the scope, null is returned.</span></span>

<span data-ttu-id="bea45-167">Im Folgenden wird veranschaulicht, wie Sie angeben, dass die Schaltflächen einer CommandBar ein direktionales Verhalten (Umbruch) aufweisen (siehe [Tastaturinteraktionen](keyboard-interactions.md#popup-ui)).</span><span class="sxs-lookup"><span data-stu-id="bea45-167">Here, we show how to specify that the buttons of a CommandBar have a wrap-around directional behavior (see [Keyboard Interactions](keyboard-interactions.md#popup-ui)).</span></span>

```XAML
<CommandBar x:Name="MyCommandBar" LosingFocus="OnLosingFocus">
    <AppBarButton Icon="Back" Label="Back" />
    <AppBarButton Icon="Stop" Label="Stop" />
    <AppBarButton Icon="Play" Label="Play" />
    <AppBarButton Icon="Forward" Label="Forward" />

    <CommandBar.SecondaryCommands>
        <AppBarButton Icon="Like" Label="Like" />
        <AppBarButton Icon="ReShare" Label="Share" />
    </CommandBar.SecondaryCommands>
</CommandBar>
```

```csharp
private void OnLosingFocus(UIElement sender, LosingFocusEventArgs args)
{
    if (IsNotAChildOf(MyCommandBar, args.NewFocussedElement))
    {
        DependencyObject candidate = null;
        if (args.Direction == FocusNavigationDirection.Left)
        {
            candidate = FocusManager.FindLastFocusableElement(MyCommandBar);
        }
        else if (args.Direction == FocusNavigationDirection.Right)
        {
            candidate = FocusManager.FindFirstFocusableElement(MyCommandBar);
        }
        if (candidate != null)
        {
            args.NewFocusedElement = candidate;
            args.Handled = true;
        }
    }
}
```

## <a name="related-articles"></a><span data-ttu-id="bea45-168">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="bea45-168">Related articles</span></span>

- [<span data-ttu-id="bea45-169">Fokusnavigation für Tastatur, Gamepad, Fernbedienung und Bedienungshilfen</span><span class="sxs-lookup"><span data-stu-id="bea45-169">Focus navigation for keyboard, gamepad, remote control, and accessibility tools</span></span>](focus-navigation.md)
- [<span data-ttu-id="bea45-170">Tastaturinteraktionen</span><span class="sxs-lookup"><span data-stu-id="bea45-170">Keyboard interactions</span></span>](keyboard-interactions.md)
- [<span data-ttu-id="bea45-171">Barrierefreiheit der Tastaturnavigation</span><span class="sxs-lookup"><span data-stu-id="bea45-171">Keyboard accessibility</span></span>](../accessibility/keyboard-accessibility.md)