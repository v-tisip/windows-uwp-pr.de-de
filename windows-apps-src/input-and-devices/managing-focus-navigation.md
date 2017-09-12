---
author: Karl-Bridge-Microsoft
pm-contact: miguelrb
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.openlocfilehash: 8389d1f089d507a087693879a793b95572d7860b
ms.sourcegitcommit: 5ece992c31870df4c089360ef47501bd4ce14fa9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2017
---
# <a name="managing-focus-navigation"></a><span data-ttu-id="35efc-101">Verwalten der Fokusnavigation</span><span class="sxs-lookup"><span data-stu-id="35efc-101">Managing focus navigation</span></span>

<span data-ttu-id="35efc-102">Viele Eingabegeräte wie Tastatur, Eingabehilfen (z.B. Windows-Sprachausgabe), Gamepad und Fernbedienung teilen einen gemeinsamen zugrunde liegenden Mechanismus, um die Fokusanzeige in der UI der Anwendung zu verlagern.</span><span class="sxs-lookup"><span data-stu-id="35efc-102">Many input namely keyboard, accessibility tools such as Windows Narrator, gamepad, and remote control share common underling mechanism to move focus visual around your applications’ UI.</span></span> <span data-ttu-id="35efc-103">Weitere Informationen zur Fokusanzeige und Navigation erhalten Sie im Dokument [Tastaturinteraktion](keyboard-interactions.md) sowie im Dokument [Entwerfen für Xbox und Fernsehgeräte](designing-for-tv.md#xy-focus-navigation-and-interaction).</span><span class="sxs-lookup"><span data-stu-id="35efc-103">Read more about focus visual and navigation at [Keyboard Interaction](keyboard-interactions.md) document as well as [Designing for Xbox and TV](designing-for-tv.md#xy-focus-navigation-and-interaction) document.</span></span>

<span data-ttu-id="35efc-104">Im Folgenden ist eine eingabeunabhängige Methode aufgeführt, mit der die Anwendung den Fokus in der UI der Anwendung verlagern kann. Dies ermöglicht es Ihnen, mit einem einzelnen Code für Ihre Anwendung mit mehreren Eingabetypen zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="35efc-104">Following provide input agnostic way for application to move focus around the application’s UI which enable you to write single code that make your application work great with multiple input types.</span></span>

## <a name="navigation-strategies-properties-to-fine-tune-focus-movements"></a><span data-ttu-id="35efc-105">Eigenschaften für Navigationsstrategien zum Optimieren von Fokusverlagerungen</span><span class="sxs-lookup"><span data-stu-id="35efc-105">Navigation Strategies properties to fine tune focus movements</span></span>

<span data-ttu-id="35efc-106">Verwenden Sie die Eigenschaften der XYFocus-Navigationsstrategie, um anzugeben, welches Steuerelement den Fokus basierend auf der gedrückten Pfeiltaste erhalten soll.</span><span class="sxs-lookup"><span data-stu-id="35efc-106">Use the XYFocus navigation strategy properties to specify which control should receive focus based on the arrow key pressed.</span></span> <span data-ttu-id="35efc-107">Diese Eigenschaften sind:</span><span class="sxs-lookup"><span data-stu-id="35efc-107">These properties are:</span></span>

-   <span data-ttu-id="35efc-108">XYFocusUpNavigationStrategy</span><span class="sxs-lookup"><span data-stu-id="35efc-108">XYFocusUpNavigationStrategy</span></span>
-   <span data-ttu-id="35efc-109">XYFocusDownNavigationStrategy</span><span class="sxs-lookup"><span data-stu-id="35efc-109">XYFocusDownNavigationStrategy</span></span>
-   <span data-ttu-id="35efc-110">XYFocusLeftNavigationStrategy</span><span class="sxs-lookup"><span data-stu-id="35efc-110">XYFocusLeftNavigationStrategy</span></span>
-   <span data-ttu-id="35efc-111">XYFocusRightNavigationStrategy</span><span class="sxs-lookup"><span data-stu-id="35efc-111">XYFocusRightNavigationStrategy</span></span>

<span data-ttu-id="35efc-112">Diese Eigenschaften haben den Wert **XYFocusNavigationStrategy**.</span><span class="sxs-lookup"><span data-stu-id="35efc-112">These properties have a value of type value of type **XYFocusNavigationStrategy**.</span></span> <span data-ttu-id="35efc-113">Wenn **Auto** festgelegt wird, basiert das Verhalten des Elements auf den Vorgängern des Elements.</span><span class="sxs-lookup"><span data-stu-id="35efc-113">If set to **Auto**, the behavior of the element is based on the ancestors of the element.</span></span> <span data-ttu-id="35efc-114">Wenn alle Elemente auf **Auto** festgelegt werden, wird **Projection** verwendet.</span><span class="sxs-lookup"><span data-stu-id="35efc-114">If all elements are set to **Auto**, **Projection** is used.</span></span>

<span data-ttu-id="35efc-115">Diese Navigationsstrategien gelten für Tastatur, Gamepad und Fernbedienung.</span><span class="sxs-lookup"><span data-stu-id="35efc-115">These navigation strategies are applicable to keyboard, gamepad, and remote control.</span></span>

### <a name="projection"></a><span data-ttu-id="35efc-116">Projection</span><span class="sxs-lookup"><span data-stu-id="35efc-116">Projection</span></span>

<span data-ttu-id="35efc-117">Die Projection-Strategie verlagert den Fokus auf das erste Element, das beim Projizieren des Rands des aktuell fokussierten Elements in der Navigationsrichtung aufgefunden wird.</span><span class="sxs-lookup"><span data-stu-id="35efc-117">The Projection strategy moves focus to the first element encountered when projecting the edge of the currently focused element in the  direction of navigation.</span></span>

> [!NOTE]
> <span data-ttu-id="35efc-118">Andere Faktoren, wie das zuvor fokussierte Element und Nähe zur Achse der Navigationsrichtung, können das Ergebnis beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="35efc-118">Other factors, such as the previously focused element and proximity to the axis of the navigation direction, can influence the result.</span></span>

![Projection](images/keyboard/projection.png)

*<span data-ttu-id="35efc-120">Je nach Projektion des unteren Rands von A wird der Fokus von A auf D in der Navigation verlagert</span><span class="sxs-lookup"><span data-stu-id="35efc-120">Focus moves from A to D on down navigation based on projection of the bottom edge of A</span></span>*

### <a name="navigationdirectiondistance"></a><span data-ttu-id="35efc-121">Distanz der Navigationsrichtung</span><span class="sxs-lookup"><span data-stu-id="35efc-121">NavigationDirectionDistance</span></span>

<span data-ttu-id="35efc-122">Die Distanz der Navigationsrichtungsstrategie verlagert den Fokus auf das Element, das sich am nächsten zur Achse der Navigationsrichtung befindet.</span><span class="sxs-lookup"><span data-stu-id="35efc-122">The NavigationDirectionDistance strategy moves focus to the element closest to the axis of the navigation direction.</span></span>

<span data-ttu-id="35efc-123">Der Rand des umgebenden Rechtecks, das der Richtung der Navigation entspricht, wird erweitert und projiziert, um Kandidatenziele zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="35efc-123">The edge of the bounding rect corresponding to the navigation direction is extended and projected to identify candidate targets.</span></span> <span data-ttu-id="35efc-124">Das erste gefundene Element wird als Ziel identifiziert.</span><span class="sxs-lookup"><span data-stu-id="35efc-124">The first element encountered is identified as the target.</span></span> <span data-ttu-id="35efc-125">Wenn mehrere Kandidaten vorhanden sind, wird das nächste Element als Ziel identifiziert.</span><span class="sxs-lookup"><span data-stu-id="35efc-125">In the case of multiple candidates, the closest element is identified as the target.</span></span> <span data-ttu-id="35efc-126">Sind weiterhin mehrere Kandidaten vorhanden, wird das oberste/ganz linke Element als der Kandidat identifiziert.</span><span class="sxs-lookup"><span data-stu-id="35efc-126">If there are still multiple candidates, the topmost/leftmost element is identified as the candidate.</span></span>

![Distanz der Navigationsrichtung](images/keyboard/navigation-direction-distance.png)

*<span data-ttu-id="35efc-128">Der Fokus wird von A auf C und dann von C auf B bei der Navigation nach unten verlagert</span><span class="sxs-lookup"><span data-stu-id="35efc-128">Focus moves from A to C and then from C to B on down navigation</span></span>*


### <a name="rectilineardistance"></a><span data-ttu-id="35efc-129">RectilinearDistance</span><span class="sxs-lookup"><span data-stu-id="35efc-129">RectilinearDistance</span></span>

<span data-ttu-id="35efc-130">Die RectilinearDistance-Strategie verlagert den Fokus zum nächsten Element basierend auf dem kürzesten 2D-Abstand (Manhattan-Metrik).</span><span class="sxs-lookup"><span data-stu-id="35efc-130">The RectilinearDistance strategy moves focus to the closest element based on the shortest 2D distance (Manhattan metric).</span></span> <span data-ttu-id="35efc-131">Dieser Abstand wird durch Hinzufügen des primären und sekundären Abstands jedes möglichen Kandidaten berechnet.</span><span class="sxs-lookup"><span data-stu-id="35efc-131">This distance is calculated by adding the primary distance and the secondary distance of each potential candidate.</span></span> <span data-ttu-id="35efc-132">Bei einer Verknüpfung wird das erste Element links ausgewählt, wenn die Richtung oben oder unten ist, oder das erste Element oben ausgewählt, wenn die Richtung links oder rechts ist.</span><span class="sxs-lookup"><span data-stu-id="35efc-132">In a tie, the first element to the left is selected if the direction is up or down, or the first element to the top is selected if the direction is left or right.</span></span>

<span data-ttu-id="35efc-133">In der folgenden Abbildungzeigen wir, dass wenn A den Fokus hat, der Fokus zu B verlagert wird, da:</span><span class="sxs-lookup"><span data-stu-id="35efc-133">In the following image, we show that when A has focus, focus is moved to B because:</span></span>

-   <span data-ttu-id="35efc-134">Abstand (A, B, Nach unten) = 10 + 0 = 10</span><span class="sxs-lookup"><span data-stu-id="35efc-134">Distance (A, B, Down) = 10 + 0 = 10</span></span>
-   <span data-ttu-id="35efc-135">Abstand (A, C, Nach unten) = 0 + 30 = 30</span><span class="sxs-lookup"><span data-stu-id="35efc-135">Distance (A, C, Down) = 0 + 30 = 30</span></span>
-   <span data-ttu-id="35efc-136">Abstand (A, D, Nach unten) 30 + 0 = 30</span><span class="sxs-lookup"><span data-stu-id="35efc-136">Distance (A, D, Down) 30 + 0 = 30</span></span>

![RectilinearDistance](images/keyboard/rectilinear-distance.png)

*<span data-ttu-id="35efc-138">Wenn A den Fokus hat, wird der Fokus zu B verlagert, wenn Sie die RectilinearDistance-Strategie verwenden.</span><span class="sxs-lookup"><span data-stu-id="35efc-138">When A has focus, focus is moved to B when using the RectilinearDistance strategy</span></span>*

<span data-ttu-id="35efc-139">Die folgende Abbildungzeigt, wie die Navigationsstrategie auf das Element selbst, aber nicht die untergeordneten Elemente angewendet wird (im Gegensatz zu XYFocusKeyboardNavigation).</span><span class="sxs-lookup"><span data-stu-id="35efc-139">The following image shows how the navigation strategy is applied to the element itself, not the child elements (unlike XYFocusKeyboardNavigation).</span></span>

<span data-ttu-id="35efc-140">Wenn beispielsweise E den Fokus hat, wird bei Verwendung der RectilinearDistance-Strategie durch Drücken des Nach-rechts-Pfeils der Fokus zu F verlagert, aber wenn D den Fokus hat, wird bei Verwendung der Projection-Strategie durch Drücken des Nach-rechts-Pfeils der Fokus auf H verlagert.</span><span class="sxs-lookup"><span data-stu-id="35efc-140">For example, when E has focus, pressing right moves focus to F using the RectilinearDistance strategy, but when D has focus, pressing right moves focus to H when using the Projection strategy.</span></span>

<span data-ttu-id="35efc-141">Beachten Sie, dass die Hauptcontainerstrategie (NavigationDirectionDistance) nicht angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="35efc-141">Notice that main container strategy (Navigation Direction Distance) is not applied.</span></span> <span data-ttu-id="35efc-142">Sie wird nur verwendet, wenn der Fokus auf H, F oder G liegt.</span><span class="sxs-lookup"><span data-stu-id="35efc-142">It is only used when the focus is on H, F, or G.</span></span>

![unterschiedliche Navigationsstrategien](images/keyboard/different-navigation-strategies.png)

*<span data-ttu-id="35efc-144">Unterschiedliche Fokusverhaltensweisen auf Grundlage der Navigationsstrategie angewendet</span><span class="sxs-lookup"><span data-stu-id="35efc-144">Different focus behaviors based on navigation strategy applied</span></span>*

<span data-ttu-id="35efc-145">Im folgenden Beispiel wird das Verhalten des Kachelbereichs im Windows10-Startmenü simuliert.</span><span class="sxs-lookup"><span data-stu-id="35efc-145">The following example simulates the behavior of the Tiles panel from the Windows 10 Start menu.</span></span> <span data-ttu-id="35efc-146">In diesem Fall wird durch Drücken des Nach-oben- und Nach-unten-Pfeils die NavigationDirectionDistance-Strategie und durch Drücken des Nach-links- und Nach-rechts-Pfeils die Projection-Strategie verwendet.</span><span class="sxs-lookup"><span data-stu-id="35efc-146">In this case, pressing the up and down arrow uses the NavigationDirectionDistance strategy, and pressing the left and right arrow uses the Projection strategy.</span></span>

```XAML
<start:TileGridView
        XYFocusKeyboardNavigation ="Default"
        XYFocusUpNavigationStrategy=" NavigationDirectionDistance "
        XYFocusDownNavigationStrategy=" NavigationDirectionDistance "
        XYFocusLeftNavigationStrategy="Projection"
        XYFocusRightNavigationStrategy="Projection"
/>
```

## <a name="move-focus-programmatically"></a><span data-ttu-id="35efc-147">Programmgesteuertes Verschieben des Fokus</span><span class="sxs-lookup"><span data-stu-id="35efc-147">Move focus programmatically</span></span>

<span data-ttu-id="35efc-148">Verwenden Sie entweder die [FocusManager.TryMoveFocus](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Input.FocusManager.TryMoveFocus)-Methode oder die [FocusManager.FindNextElement](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Input.FocusManager.FindNextFocusableElement)-Methode, um den Fokus programmgesteuert zu verlagern.</span><span class="sxs-lookup"><span data-stu-id="35efc-148">Use either the [FocusManager.TryMoveFocus](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Input.FocusManager.TryMoveFocus) method or the [FocusManager.FindNextElement](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Input.FocusManager.FindNextFocusableElement) method to programmatically move focus.</span></span>

<span data-ttu-id="35efc-149">TryMoveFocus legt den Fokus wie eine Navigationstaste.</span><span class="sxs-lookup"><span data-stu-id="35efc-149">TryMoveFocus sets focus as if a navigation key was pressed.</span></span>
<span data-ttu-id="35efc-150">FindNextElement gibt das Element (DependencyObject) zurück, auf das TryMoveFocus verlagert werden würde.</span><span class="sxs-lookup"><span data-stu-id="35efc-150">FindNextElement returns the element (a DependencyObject) that TryMoveFocus would move to.</span></span>

<span data-ttu-id="35efc-151">**HINWEIS** Wir empfehlen die Verwendung der **FindNextElement**-Methode anstelle von **FindNextFocusableElement**.</span><span class="sxs-lookup"><span data-stu-id="35efc-151">**NOTE** We recommend using the **FindNextElement** method instead of **FindNextFocusableElement**.</span></span> <span data-ttu-id="35efc-152">FindNextFocusableElement versucht, ein UIElement zurückzugeben. Wenn das nächste fokussierbare Element jedoch ein Hyperlink ist, wird NULL zurückgegeben, da ein Hyperlink kein UIElement ist.</span><span class="sxs-lookup"><span data-stu-id="35efc-152">FindNextFocusableElement tries to return a UIElement, but if the next focusable element is a Hyperlink, it returns null because a Hyperlink is not a UIElement.</span></span> <span data-ttu-id="35efc-153">Die FindNextElement-Methode gibt stattdessen ein DependencyObject zurück.</span><span class="sxs-lookup"><span data-stu-id="35efc-153">FindNextElement method returns a DependencyObject instead.</span></span>

### <a name="find-a-focus-candidate-in-a-scope"></a><span data-ttu-id="35efc-154">Suchen eines Fokuskandidaten in einem Bereich</span><span class="sxs-lookup"><span data-stu-id="35efc-154">Find a focus candidate in a scope</span></span>

<span data-ttu-id="35efc-155">Mit FocusManager.FindNextElement und FocusManager.TryMoveFocus können Sie das nächste fokussierbare Elementsuchverhalten anpassen.</span><span class="sxs-lookup"><span data-stu-id="35efc-155">FocusManager.FindNextElement and FocusManager.TryMoveFocus both let you customize the next focusable element search behavior.</span></span> <span data-ttu-id="35efc-156">Sie können in einer bestimmten UI-Struktur suchen oder Elemente in einem bestimmten Navigationsbereich ausschließen.</span><span class="sxs-lookup"><span data-stu-id="35efc-156">You can search within a specific UI tree, or exclude elements in a specific navigation area.</span></span>

<span data-ttu-id="35efc-157">Dieses Beispiel stammt aus einer Implementierung des Spiels TicTacToe und veranschaulicht, wie Sie die Methoden FindNextElement und TryMoveFocus verwenden:</span><span class="sxs-lookup"><span data-stu-id="35efc-157">This example is taken from an implementation of a TicTacToe game and demonstrates how to use the FindNextElement and TryMoveFocus methods:</span></span>

```XAML
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
            <myControls:TicTacToeCell Grid.Column="0" Grid.Row="0" x:Name="Cell00" />
            <myControls:TicTacToeCell Grid.Column="1" Grid.Row="0" x:Name="Cell10"/>
            <myControls:TicTacToeCell Grid.Column="2" Grid.Row="0" x:Name="Cell20"/>
            <myControls:TicTacToeCell Grid.Column="0" Grid.Row="1" x:Name="Cell01"/>
            <myControls:TicTacToeCell Grid.Column="1" Grid.Row="1" x:Name="Cell11"/>
            <myControls:TicTacToeCell Grid.Column="2" Grid.Row="1" x:Name="Cell21"/>
            <myControls:TicTacToeCell Grid.Column="0" Grid.Row="2" x:Name="Cell02"/>
            <myControls:TicTacToeCell Grid.Column="1" Grid.Row="2" x:Name="Cell22"/>
            <myControls:TicTacToeCell Grid.Column="2" Grid.Row="2" x:Name="Cell32"/>
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
                    candidate = FocusManager.FindNextElement(FocusNavigationDirection.Up, options);
                    break;
                case Windows.System.VirtualKey.Down:
                    candidate = FocusManager.FindNextElement(FocusNavigationDirection.Down, options);
                    break;
                case Windows.System.VirtualKey.Left:
                    candidate = FocusManager.FindNextElement(FocusNavigationDirection.Left, options);
                    break;
                case Windows.System.VirtualKey.Right:
                    candidate = FocusManager.FindNextElement(FocusNavigationDirection.Right, options);
                    break;
            }
         //Note you should also consider whether is a Hyperlink, WebView, or TextBlock.
            if (candidate != null && candidate is Control)
            {
                (candidate as Control).Focus(FocusState.Keyboard);
            }
        }
```

<span data-ttu-id="35efc-158">**HINWEIS** FocusNavigationDirection.Left und FocusNavigationDirection.Right sind logisch (nah und fern), um RTL-Szenarios zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="35efc-158">**NOTE** FocusNavigationDirection.Left and FocusNavigationDirection.Right are logical (near and far) to support RTL scenarios.</span></span> <span data-ttu-id="35efc-159">(Dies entspricht dem restlichen XAML-Code.)</span><span class="sxs-lookup"><span data-stu-id="35efc-159">(This matches the rest of Xaml.)</span></span>

<span data-ttu-id="35efc-160">Die Suche nach den Fokuskandidaten kann mit der FindNextElementOptions-Klasse angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="35efc-160">The search for focus candidates can be adjusted using the FindNextElementOptions class.</span></span> <span data-ttu-id="35efc-161">Dieses Objekt besitzt folgende Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="35efc-161">This object has the following properties:</span></span>

-   <span data-ttu-id="35efc-162">**SearchRoot** DependencyObject: Zum Begrenzen der Suche von Kandidaten auf die untergeordneten Elemente dieses DependencyObject.</span><span class="sxs-lookup"><span data-stu-id="35efc-162">**SearchRoot** DependencyObject: To scope the search of candidates to the children of this DependencyObject.</span></span> <span data-ttu-id="35efc-163">Ein NULL-Wert gibt die gesamte visuelle Struktur der App an.</span><span class="sxs-lookup"><span data-stu-id="35efc-163">Null value indicates the entire visual tree of the app.</span></span>
-   <span data-ttu-id="35efc-164">**ExclusionRect** Rect: Zum Ausschließen der Elemente aus der Suche, die beim Rendern mindestens ein Pixel von diesem Rechteck überlappen.</span><span class="sxs-lookup"><span data-stu-id="35efc-164">**ExclusionRect** Rect: To exclude from the search the items that, when are rendered, overlap at least one pixel from this rectangle.</span></span>
-   <span data-ttu-id="35efc-165">**HintRect** Rect: Mögliche Kandidaten werden mit dem fokussierten Element als Referenz berechnet.</span><span class="sxs-lookup"><span data-stu-id="35efc-165">**HintRect** Rect: Potential candidates are calculated using the focused item as reference.</span></span> <span data-ttu-id="35efc-166">Mit diesem Rechteck können Entwickler eine andere Referenz als das fokussierte Element angeben.</span><span class="sxs-lookup"><span data-stu-id="35efc-166">This rectangle lets developers specify another reference instead of the focused element.</span></span> <span data-ttu-id="35efc-167">Das Rechteck ist ein „fiktives“ Rechteck, das nur für Berechnungen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="35efc-167">The rectangle is a “fictitious” rectangle used only for calculations.</span></span> <span data-ttu-id="35efc-168">Es wird nicht in ein echtes Rechteck konvertiert und der visuellen Struktur hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="35efc-168">It is never converted to a real rectangle and added to the visual tree.</span></span>
-   <span data-ttu-id="35efc-169">**XYFocusNavigationStrategyOverride** XYFocusNavigationStrategyOverride: Navigationsstrategie zum Verlagern des Fokus.</span><span class="sxs-lookup"><span data-stu-id="35efc-169">**XYFocusNavigationStrategyOverride** XYFocusNavigationStrategyOverride: The navigation strategy used to move the focus.</span></span> <span data-ttu-id="35efc-170">Der Typ ist eine Enumeration mit den Werten „None“ (0), „Auto“, „RectilinearDistance“, „NavigationDirectionDistance“ und „Projection“.</span><span class="sxs-lookup"><span data-stu-id="35efc-170">The type is an enum with the values None (which is the zero value), Auto, RectilinearDistance, NavigationDirectionDistance and Projection.</span></span>
    <span data-ttu-id="35efc-171">**Wichtig** **SearchRoot** wird nicht verwendet, um den gerenderten (geometrischen) Bereich zu berechnen oder die Kandidaten im Bereich zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="35efc-171">**Important** **SearchRoot** is not used to calculate the rendered (geometric) area or to get the candidates inside the area.</span></span> <span data-ttu-id="35efc-172">Wenn Transformationen auf die Nachfolgerelemente von DependencyObject angewendet werden, die sie außerhalb des direktionalen Bereichs platzieren, werden diese Elemente daher weiterhin als Kandidaten betrachtet.</span><span class="sxs-lookup"><span data-stu-id="35efc-172">As a consequence, if transforms are applied to the descendants of the DependencyObject that place them outside of the directional area, these elements are still considered candidates.</span></span>

<span data-ttu-id="35efc-173">Die Optionsüberladung von FindNextElement kann nicht mit der Tab-Navigation verwendet werden, sie unterstützt nur die direktionale Navigation.</span><span class="sxs-lookup"><span data-stu-id="35efc-173">The options overload of FindNextElement cannot be used with tab navigation, it only supports directional navigation.</span></span>

<span data-ttu-id="35efc-174">Die folgende Abbildungzeigt diese Optionen.</span><span class="sxs-lookup"><span data-stu-id="35efc-174">The following image illustrates these options.</span></span>

<span data-ttu-id="35efc-175">Wenn beispielsweise B den Fokus hat, wird durch Aufrufen von FindNextElement (mit verschiedenen Optionen zur Angabe, dass der Fokus auf die rechte Seite verlagert wird) der Fokus auf I verlagert. Gründe dafür sind:</span><span class="sxs-lookup"><span data-stu-id="35efc-175">For example, when B has focus, calling FindNextElement (with various options set to indicate that focus moves to the right) sets focus on I. The reasons for this are:</span></span>

1.  <span data-ttu-id="35efc-176">Die Referenz ist nicht B, sondern A (aufgrund von HintRect).</span><span class="sxs-lookup"><span data-stu-id="35efc-176">The reference is not B, it is A due to the HintRect</span></span>
2.  <span data-ttu-id="35efc-177">C wird ausgeschlossen, da der potenzielle Kandidat sich in MyPanel (SearchRoot) befinden sollte.</span><span class="sxs-lookup"><span data-stu-id="35efc-177">C is excluded because the potential candidate should be on MyPanel (the SearchRoot)</span></span>
3.  <span data-ttu-id="35efc-178">F wird ausgeschlossen, da es mit dem Ausschlussrechteck überlappt.</span><span class="sxs-lookup"><span data-stu-id="35efc-178">F is excluded because it overlaps the exclusions rectangle</span></span>

![Navigationshinweise](images/keyboard/navigation-hints.png)

*<span data-ttu-id="35efc-180">Fokusverhalten basierend auf Navigationshinweisen</span><span class="sxs-lookup"><span data-stu-id="35efc-180">Focus behavior based on navigation hints</span></span>*

### <a name="no-focus-candidate-available"></a><span data-ttu-id="35efc-181">Kein Fokuskandidat verfügbar</span><span class="sxs-lookup"><span data-stu-id="35efc-181">No focus candidate available</span></span>

<span data-ttu-id="35efc-182">Das UIElement.NoFocusCandidateFound-Ereignis wird ausgelöst, wenn der Benutzer versucht, den Fokus mit der TAB-Taste oder den Pfeiltasten zu verlagern, jedoch kein möglicher Kandidat in der angegebenen Richtung vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="35efc-182">The UIElement.NoFocusCandidateFound event is fired when the user attempts to move focus with tab or arrow keys, but there is no possible candidate in the specified direction.</span></span> <span data-ttu-id="35efc-183">Dieses Ereignis wird nicht für FocusManager.TryMoveFocus() ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="35efc-183">This event is not fired for FocusManager.TryMoveFocus().</span></span>

<span data-ttu-id="35efc-184">Da dies ein Routingereignis ist, erfolgt Bubbling vom fokussierten Element über die einzelnen übergeordneten Objekte zum Stamm der Objektstruktur nach oben.</span><span class="sxs-lookup"><span data-stu-id="35efc-184">Because this is a routed event, it bubbles from the focused element up through successive parent objects to the root of the object tree.</span></span> <span data-ttu-id="35efc-185">Auf diese Weise können Sie das Ereignis verarbeiten, sofern angebracht.</span><span class="sxs-lookup"><span data-stu-id="35efc-185">In this way, you can handle the event wherever appropriate.</span></span>

<span data-ttu-id="35efc-186"><a name="split-view-code-sample"></a>Das folgende Beispiel zeigt ein Raster, das eine geteilten Ansicht öffnet, wenn der Benutzer versucht, den Fokus auf die linke Seite des fokussierbaren Steuerelements ganz links zu verlagern, wie unter [Entwerfen für TV-Dokumentation](designing-for-tv.md#navigation-pane) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="35efc-186"><a name="split-view-code-sample"></a> The following example shows a Grid that opens a split view when the user attempts to move focus to the left of the left-most focusable control as described in [Designing for TV documentation](designing-for-tv.md#navigation-pane).</span></span>

```XAML
<Grid NoFocusCandidateFound="OnNoFocusCandidateFound">  ...</Grid>
```

```csharp
private void OnNoFocusCandidateFound (UIElement sender, NoFocusCandidateFoundEventArgs args)
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

## <a name="focus-events"></a><span data-ttu-id="35efc-187">Fokusereignisse</span><span class="sxs-lookup"><span data-stu-id="35efc-187">Focus events</span></span>

<span data-ttu-id="35efc-188">Die Ereignisse [UIElement.GotFocus](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.UIElement.GotFocus) und UIElement.LostFocus werden ausgelöst, wenn ein Steuerelement den Fokus erhält oder verliert.</span><span class="sxs-lookup"><span data-stu-id="35efc-188">The [UIElement.GotFocus](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.UIElement.GotFocus) and UIElement.LostFocus events are fired when a control gets focus or loses focus, respectively.</span></span> <span data-ttu-id="35efc-189">Dieses Ereignis wird nicht für FocusManager.TryMoveFocus() ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="35efc-189">This event is not fired for FocusManager.TryMoveFocus().</span></span>

<span data-ttu-id="35efc-190">Da dies ein Routingereignis ist, erfolgt Bubbling vom fokussierten Element über die einzelnen übergeordneten Objekte zum Stamm der Objektstruktur nach oben.</span><span class="sxs-lookup"><span data-stu-id="35efc-190">Because this is a routed event, it bubbles from the focused element up through successive parent objects to the root of the object tree.</span></span> <span data-ttu-id="35efc-191">Auf diese Weise können Sie das Ereignis verarbeiten, sofern angebracht.</span><span class="sxs-lookup"><span data-stu-id="35efc-191">In this way, you can handle the event wherever appropriate.</span></span>

<span data-ttu-id="35efc-192">Für die Ereignisse **UIElement.GettingFocus** und **UIElement.LosingFocus** erfolgt Bubbling auch vom Steuerelement, aber *vor* der Fokusänderung.</span><span class="sxs-lookup"><span data-stu-id="35efc-192">The **UIElement.GettingFocus** and **UIElement.LosingFocus** events also bubble from the control, but *before* the focus change takes place.</span></span> <span data-ttu-id="35efc-193">Dadurch kann die App die Fokusänderung umleiten oder abbrechen.</span><span class="sxs-lookup"><span data-stu-id="35efc-193">This gives the app an opportunity to redirect or cancel the focus change.</span></span>

<span data-ttu-id="35efc-194">Beachten Sie, dass die Ereignisse GettingFocus und LosingFocus synchron sind, während die Ereignisse GotFocus und LostFocus asynchron sind.</span><span class="sxs-lookup"><span data-stu-id="35efc-194">Note that the GettingFocus and LosingFocus events are synchronous, while the GotFocus and LostFocus events are asynchronous.</span></span> <span data-ttu-id="35efc-195">Wenn der Fokus verlagert wird, da die App die Control.Focus()-Methode aufruft, wird z.B. GettingFocus während des Aufrufs ausgelöst, GotFocus wird jedoch nach dem Aufruf ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="35efc-195">For example, if focus moves because the app calls the Control.Focus() method, GettingFocus is raised during the call, but GotFocus is raised sometime after the call.</span></span>

<span data-ttu-id="35efc-196">UIElements können mit den Ereignissen GettingFocus und LosingFocus verknüpft werden und das Ziel (mithilfe der NewFocusedElement-Eigenschaft) ändern, bevor der Fokus verlagert wird.</span><span class="sxs-lookup"><span data-stu-id="35efc-196">UIElements can hook onto the GettingFocus and LosingFocus events and change the target (using the NewFocusedElement property) before the focus is moved.</span></span> <span data-ttu-id="35efc-197">Selbst wenn das Ziel geändert wurde, erfolgt weiterhin Ereignis-Bubbling und ein anderes übergeordnetes Element kann das Ziel erneut ändern.</span><span class="sxs-lookup"><span data-stu-id="35efc-197">Even if the target has changed, the event still bubbles and another parent can change the target again.</span></span>

<span data-ttu-id="35efc-198">Um Eintrittsvarianzprobleme zu vermeiden, werden Ausnahmen ausgegeben, wenn Sie versuchen, den Fokus zu verlagern (mit FocusManager.TryMoveFocus oder Control.Focus), während für diese Ereignisse Bubbling erfolgt.</span><span class="sxs-lookup"><span data-stu-id="35efc-198">To avoid reentrancy issues, exceptions are thrown if you try to move focus (using FocusManager.TryMoveFocus or the Control.Focus) while these events are bubbling.</span></span>

<span data-ttu-id="35efc-199">Diese Ereignisse werden unabhängig vom Grund der Fokusverlagerung ausgelöst (z.B. Tab-Navigation, XYFocus-Navigation, programmgesteuert).</span><span class="sxs-lookup"><span data-stu-id="35efc-199">These events are fired regardless of the reason for the focus moving (for example, tab navigation, XYFocus navigation, programmatic).</span></span>

<span data-ttu-id="35efc-200">Die folgende Abbildungzeigt, wie beim Verschieben von A nach rechts XYFocus LVI4 als Kandidat auswählt.</span><span class="sxs-lookup"><span data-stu-id="35efc-200">The following image shows how, when moving from A to the right, the XYFocus chooses LVI4 as a candidate.</span></span> <span data-ttu-id="35efc-201">LVI4 löst dann das GettingFocus-Ereignis aus, wobei ListView die Möglichkeit hat, den Fokus erneut zu LVI3 zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="35efc-201">LVI4 then fires the GettingFocus event where the ListView has the opportunity to reassign focus to LVI3.</span></span>

![Fokusereignisse](images/keyboard/focus-events.png)

*<span data-ttu-id="35efc-203">Fokusereignisse</span><span class="sxs-lookup"><span data-stu-id="35efc-203">Focus events</span></span>*

<span data-ttu-id="35efc-204">In diesem Codebeispiel wird veranschaulicht, wie das OnGettingFocus-Ereignis verarbeitet und der Fokus basierend auf dem zuvor festgelegten Fokus umgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="35efc-204">This code example shows how to handle the OnGettingFocus event and redirect focus based on where focus was previously set.</span></span>

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
            if (MyListView.SelectedIndex != -1 && IsNotAChildOf(MyListView, args.OldFocusedElement))
            {
                var selectedContainer = MyListView.ContainerFromItem(MyListView.SelectedItem);
                if (args.FocusState == FocusState.Keyboard && args.NewFocusedElement != selectedContainer)
                {
                    args.NewFocusedElement = MyListView.ContainerFromItem(MyListView.SelectedItem);
                    args.Handled = true;
                }
            }        
  }
```

<span data-ttu-id="35efc-205">In diesem Codebeispiel wird veranschaulicht, wie Sie das OnLosingFocus-Ereignis für ein CommandBar-Objekt verarbeiten und darauf warten, den Fokus zu legen, bis das DropDown-Menü geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="35efc-205">This code example shows how to handle the OnLosingFocus event for a CommandBar object and wait to set focus until the DropDown menu is closed.</span></span>

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
          if (MyCommandBar.IsOpen == true && IsNotAChildOf(MyCommandBar, args.NewFocusedElement))
          {
              args.Cancel = true;
              args.Handled = true;
          }
}
```

### <a name="losingfocus-and-gettingfocus-event-order"></a><span data-ttu-id="35efc-206">LosingFocus und GettingFocus – Ereignisreihenfolge</span><span class="sxs-lookup"><span data-stu-id="35efc-206">LosingFocus and GettingFocus event order</span></span>

<span data-ttu-id="35efc-207">LosingFocus und GettingFocus sind synchrone Ereignisse. Das heißt, der Fokus wird nicht verlagert, während für diese Ereignisse Bubbling erfolgt.</span><span class="sxs-lookup"><span data-stu-id="35efc-207">LosingFocus and GettingFocus are synchronous events, so focus won’t be moved while these events are bubbling.</span></span> <span data-ttu-id="35efc-208">Da LostFocus und GotFocus asynchrone Ereignisse sind, kann jedoch nicht garantiert werden, dass der Fokus vor der Ausführung des Handlers nicht erneut verlagert wird.</span><span class="sxs-lookup"><span data-stu-id="35efc-208">However, because LostFocus and GotFocus are asynchronous events, there is no guarantee that focus won’t move again before the handler is executed.</span></span> <span data-ttu-id="35efc-209">Es ist nur sichergestellt, dass der LostFocus-Handler vor dem GotFocus-Handler ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="35efc-209">The only guarantee is that the LostFocus handler is executed before the GotFocus handler.</span></span>

<span data-ttu-id="35efc-210">Die Reihenfolge der Ausführung ist wie folgt festgelegt;</span><span class="sxs-lookup"><span data-stu-id="35efc-210">Here is the order of execution:</span></span>

1.  <span data-ttu-id="35efc-211">Sync LosingFocus: Wenn LosingFocus den Fokus zurück auf das Element zurücksetzt, das den Fokus verloren oder Cancel=true festgelegt hat, finden keine weiteren Ereignisse statt.</span><span class="sxs-lookup"><span data-stu-id="35efc-211">Sync LosingFocus: If LosingFocus resets focus back to the element that was losing focus or setting the Cancel=true, no further events</span></span>
2.  <span data-ttu-id="35efc-212">Sync GettingFocus: Wenn GettingFocus den Fokus zurück auf das Element zurücksetzt, das den Fokus verloren oder Cancel=true festgelegt hat, finden keine weiteren Ereignisse statt.</span><span class="sxs-lookup"><span data-stu-id="35efc-212">Sync GettingFocus: If GettingFocus resets focus back to the element that was losing focus or setting the Cancel=true, no further events</span></span>
3.  <span data-ttu-id="35efc-213">Async LostFocus</span><span class="sxs-lookup"><span data-stu-id="35efc-213">Async LostFocus</span></span>
4.  <span data-ttu-id="35efc-214">Async GotFocus</span><span class="sxs-lookup"><span data-stu-id="35efc-214">Async GotFocus</span></span>

## <a name="find-the-first-and-last-focusable-element-a-namefindfirstfocusableelement"></a><span data-ttu-id="35efc-215">Suchen des ersten und letzten fokussierbaren Elements <a name="findfirstfocusableelement"></span><span class="sxs-lookup"><span data-stu-id="35efc-215">Find the first and last focusable element <a name="findfirstfocusableelement"></span></span>

<span data-ttu-id="35efc-216">Die Methoden **FocusManager.FindFirstFocusableElement** und **FocusManager.FindLastFocusableElement** ermöglichen das Verlagern des Fokus auf das erste oder letzte fokussierbare Element im Bereich eines Objekts (UIElement-Elementstruktur oder TextElement-Textstruktur).</span><span class="sxs-lookup"><span data-stu-id="35efc-216">The **FocusManager.FindFirstFocusableElement** and the **FocusManager.FindLastFocusableElement** methods let you move focus to the first or last focusable element within the scope of an object (the element tree of a UIElement or the text tree of a TextElement).</span></span> <span data-ttu-id="35efc-217">Wenn Sie diese Methoden aufrufen, geben Sie den Bereich an.</span><span class="sxs-lookup"><span data-stu-id="35efc-217">You specify the scope when you call these methods.</span></span> <span data-ttu-id="35efc-218">Wenn das Argument NULL ist, ist der Bereich das aktuelle Fenster.</span><span class="sxs-lookup"><span data-stu-id="35efc-218">If the argument is null, the scope will be the current window.</span></span>

<span data-ttu-id="35efc-219">**Hinweis** Diese Methoden können NULL zurückgeben, wenn keine fokussierbaren Elemente im Bereich vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="35efc-219">**Note** These methods can return null if there are no focusable items in the scope.</span></span>

<span data-ttu-id="35efc-220"><a name="popup-ui-code-sample"></a>Im folgenden Codebeispiel wird veranschaulicht, wie Sie angeben, dass die Schaltflächen einer CommandBar ein direktionales Verhalten (Umbruch) aufweisen, wie im Artikel [Tastaturinteraktionen](keyboard-interactions.md#popup-ui) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="35efc-220"><a name="popup-ui-code-sample"></a> The following code example shows how to specify that the buttons of a CommandBar have a wrap-around directional behavior described in [Keyboard Interactions](keyboard-interactions.md#popup-ui) article.</span></span>

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
