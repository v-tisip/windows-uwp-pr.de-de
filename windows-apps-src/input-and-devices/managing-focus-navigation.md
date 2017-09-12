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
# <a name="managing-focus-navigation"></a>Verwalten der Fokusnavigation

Viele Eingabegeräte wie Tastatur, Eingabehilfen (z.B. Windows-Sprachausgabe), Gamepad und Fernbedienung teilen einen gemeinsamen zugrunde liegenden Mechanismus, um die Fokusanzeige in der UI der Anwendung zu verlagern. Weitere Informationen zur Fokusanzeige und Navigation erhalten Sie im Dokument [Tastaturinteraktion](keyboard-interactions.md) sowie im Dokument [Entwerfen für Xbox und Fernsehgeräte](designing-for-tv.md#xy-focus-navigation-and-interaction).

Im Folgenden ist eine eingabeunabhängige Methode aufgeführt, mit der die Anwendung den Fokus in der UI der Anwendung verlagern kann. Dies ermöglicht es Ihnen, mit einem einzelnen Code für Ihre Anwendung mit mehreren Eingabetypen zu arbeiten.

## <a name="navigation-strategies-properties-to-fine-tune-focus-movements"></a>Eigenschaften für Navigationsstrategien zum Optimieren von Fokusverlagerungen

Verwenden Sie die Eigenschaften der XYFocus-Navigationsstrategie, um anzugeben, welches Steuerelement den Fokus basierend auf der gedrückten Pfeiltaste erhalten soll. Diese Eigenschaften sind:

-   XYFocusUpNavigationStrategy
-   XYFocusDownNavigationStrategy
-   XYFocusLeftNavigationStrategy
-   XYFocusRightNavigationStrategy

Diese Eigenschaften haben den Wert **XYFocusNavigationStrategy**. Wenn **Auto** festgelegt wird, basiert das Verhalten des Elements auf den Vorgängern des Elements. Wenn alle Elemente auf **Auto** festgelegt werden, wird **Projection** verwendet.

Diese Navigationsstrategien gelten für Tastatur, Gamepad und Fernbedienung.

### <a name="projection"></a>Projection

Die Projection-Strategie verlagert den Fokus auf das erste Element, das beim Projizieren des Rands des aktuell fokussierten Elements in der Navigationsrichtung aufgefunden wird.

> [!NOTE]
> Andere Faktoren, wie das zuvor fokussierte Element und Nähe zur Achse der Navigationsrichtung, können das Ergebnis beeinflussen.

![Projection](images/keyboard/projection.png)

*Je nach Projektion des unteren Rands von A wird der Fokus von A auf D in der Navigation verlagert*

### <a name="navigationdirectiondistance"></a>Distanz der Navigationsrichtung

Die Distanz der Navigationsrichtungsstrategie verlagert den Fokus auf das Element, das sich am nächsten zur Achse der Navigationsrichtung befindet.

Der Rand des umgebenden Rechtecks, das der Richtung der Navigation entspricht, wird erweitert und projiziert, um Kandidatenziele zu identifizieren. Das erste gefundene Element wird als Ziel identifiziert. Wenn mehrere Kandidaten vorhanden sind, wird das nächste Element als Ziel identifiziert. Sind weiterhin mehrere Kandidaten vorhanden, wird das oberste/ganz linke Element als der Kandidat identifiziert.

![Distanz der Navigationsrichtung](images/keyboard/navigation-direction-distance.png)

*Der Fokus wird von A auf C und dann von C auf B bei der Navigation nach unten verlagert*


### <a name="rectilineardistance"></a>RectilinearDistance

Die RectilinearDistance-Strategie verlagert den Fokus zum nächsten Element basierend auf dem kürzesten 2D-Abstand (Manhattan-Metrik). Dieser Abstand wird durch Hinzufügen des primären und sekundären Abstands jedes möglichen Kandidaten berechnet. Bei einer Verknüpfung wird das erste Element links ausgewählt, wenn die Richtung oben oder unten ist, oder das erste Element oben ausgewählt, wenn die Richtung links oder rechts ist.

In der folgenden Abbildungzeigen wir, dass wenn A den Fokus hat, der Fokus zu B verlagert wird, da:

-   Abstand (A, B, Nach unten) = 10 + 0 = 10
-   Abstand (A, C, Nach unten) = 0 + 30 = 30
-   Abstand (A, D, Nach unten) 30 + 0 = 30

![RectilinearDistance](images/keyboard/rectilinear-distance.png)

*Wenn A den Fokus hat, wird der Fokus zu B verlagert, wenn Sie die RectilinearDistance-Strategie verwenden.*

Die folgende Abbildungzeigt, wie die Navigationsstrategie auf das Element selbst, aber nicht die untergeordneten Elemente angewendet wird (im Gegensatz zu XYFocusKeyboardNavigation).

Wenn beispielsweise E den Fokus hat, wird bei Verwendung der RectilinearDistance-Strategie durch Drücken des Nach-rechts-Pfeils der Fokus zu F verlagert, aber wenn D den Fokus hat, wird bei Verwendung der Projection-Strategie durch Drücken des Nach-rechts-Pfeils der Fokus auf H verlagert.

Beachten Sie, dass die Hauptcontainerstrategie (NavigationDirectionDistance) nicht angewendet wird. Sie wird nur verwendet, wenn der Fokus auf H, F oder G liegt.

![unterschiedliche Navigationsstrategien](images/keyboard/different-navigation-strategies.png)

*Unterschiedliche Fokusverhaltensweisen auf Grundlage der Navigationsstrategie angewendet*

Im folgenden Beispiel wird das Verhalten des Kachelbereichs im Windows10-Startmenü simuliert. In diesem Fall wird durch Drücken des Nach-oben- und Nach-unten-Pfeils die NavigationDirectionDistance-Strategie und durch Drücken des Nach-links- und Nach-rechts-Pfeils die Projection-Strategie verwendet.

```XAML
<start:TileGridView
        XYFocusKeyboardNavigation ="Default"
        XYFocusUpNavigationStrategy=" NavigationDirectionDistance "
        XYFocusDownNavigationStrategy=" NavigationDirectionDistance "
        XYFocusLeftNavigationStrategy="Projection"
        XYFocusRightNavigationStrategy="Projection"
/>
```

## <a name="move-focus-programmatically"></a>Programmgesteuertes Verschieben des Fokus

Verwenden Sie entweder die [FocusManager.TryMoveFocus](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Input.FocusManager.TryMoveFocus)-Methode oder die [FocusManager.FindNextElement](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.Input.FocusManager.FindNextFocusableElement)-Methode, um den Fokus programmgesteuert zu verlagern.

TryMoveFocus legt den Fokus wie eine Navigationstaste.
FindNextElement gibt das Element (DependencyObject) zurück, auf das TryMoveFocus verlagert werden würde.

**HINWEIS** Wir empfehlen die Verwendung der **FindNextElement**-Methode anstelle von **FindNextFocusableElement**. FindNextFocusableElement versucht, ein UIElement zurückzugeben. Wenn das nächste fokussierbare Element jedoch ein Hyperlink ist, wird NULL zurückgegeben, da ein Hyperlink kein UIElement ist. Die FindNextElement-Methode gibt stattdessen ein DependencyObject zurück.

### <a name="find-a-focus-candidate-in-a-scope"></a>Suchen eines Fokuskandidaten in einem Bereich

Mit FocusManager.FindNextElement und FocusManager.TryMoveFocus können Sie das nächste fokussierbare Elementsuchverhalten anpassen. Sie können in einer bestimmten UI-Struktur suchen oder Elemente in einem bestimmten Navigationsbereich ausschließen.

Dieses Beispiel stammt aus einer Implementierung des Spiels TicTacToe und veranschaulicht, wie Sie die Methoden FindNextElement und TryMoveFocus verwenden:

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

**HINWEIS** FocusNavigationDirection.Left und FocusNavigationDirection.Right sind logisch (nah und fern), um RTL-Szenarios zu unterstützen. (Dies entspricht dem restlichen XAML-Code.)

Die Suche nach den Fokuskandidaten kann mit der FindNextElementOptions-Klasse angepasst werden. Dieses Objekt besitzt folgende Eigenschaften:

-   **SearchRoot** DependencyObject: Zum Begrenzen der Suche von Kandidaten auf die untergeordneten Elemente dieses DependencyObject. Ein NULL-Wert gibt die gesamte visuelle Struktur der App an.
-   **ExclusionRect** Rect: Zum Ausschließen der Elemente aus der Suche, die beim Rendern mindestens ein Pixel von diesem Rechteck überlappen.
-   **HintRect** Rect: Mögliche Kandidaten werden mit dem fokussierten Element als Referenz berechnet. Mit diesem Rechteck können Entwickler eine andere Referenz als das fokussierte Element angeben. Das Rechteck ist ein „fiktives“ Rechteck, das nur für Berechnungen verwendet wird. Es wird nicht in ein echtes Rechteck konvertiert und der visuellen Struktur hinzugefügt.
-   **XYFocusNavigationStrategyOverride** XYFocusNavigationStrategyOverride: Navigationsstrategie zum Verlagern des Fokus. Der Typ ist eine Enumeration mit den Werten „None“ (0), „Auto“, „RectilinearDistance“, „NavigationDirectionDistance“ und „Projection“.
    **Wichtig** **SearchRoot** wird nicht verwendet, um den gerenderten (geometrischen) Bereich zu berechnen oder die Kandidaten im Bereich zu platzieren. Wenn Transformationen auf die Nachfolgerelemente von DependencyObject angewendet werden, die sie außerhalb des direktionalen Bereichs platzieren, werden diese Elemente daher weiterhin als Kandidaten betrachtet.

Die Optionsüberladung von FindNextElement kann nicht mit der Tab-Navigation verwendet werden, sie unterstützt nur die direktionale Navigation.

Die folgende Abbildungzeigt diese Optionen.

Wenn beispielsweise B den Fokus hat, wird durch Aufrufen von FindNextElement (mit verschiedenen Optionen zur Angabe, dass der Fokus auf die rechte Seite verlagert wird) der Fokus auf I verlagert. Gründe dafür sind:

1.  Die Referenz ist nicht B, sondern A (aufgrund von HintRect).
2.  C wird ausgeschlossen, da der potenzielle Kandidat sich in MyPanel (SearchRoot) befinden sollte.
3.  F wird ausgeschlossen, da es mit dem Ausschlussrechteck überlappt.

![Navigationshinweise](images/keyboard/navigation-hints.png)

*Fokusverhalten basierend auf Navigationshinweisen*

### <a name="no-focus-candidate-available"></a>Kein Fokuskandidat verfügbar

Das UIElement.NoFocusCandidateFound-Ereignis wird ausgelöst, wenn der Benutzer versucht, den Fokus mit der TAB-Taste oder den Pfeiltasten zu verlagern, jedoch kein möglicher Kandidat in der angegebenen Richtung vorhanden ist. Dieses Ereignis wird nicht für FocusManager.TryMoveFocus() ausgelöst.

Da dies ein Routingereignis ist, erfolgt Bubbling vom fokussierten Element über die einzelnen übergeordneten Objekte zum Stamm der Objektstruktur nach oben. Auf diese Weise können Sie das Ereignis verarbeiten, sofern angebracht.

<a name="split-view-code-sample"></a>Das folgende Beispiel zeigt ein Raster, das eine geteilten Ansicht öffnet, wenn der Benutzer versucht, den Fokus auf die linke Seite des fokussierbaren Steuerelements ganz links zu verlagern, wie unter [Entwerfen für TV-Dokumentation](designing-for-tv.md#navigation-pane) beschrieben.

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

## <a name="focus-events"></a>Fokusereignisse

Die Ereignisse [UIElement.GotFocus](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/Windows.UI.Xaml.UIElement.GotFocus) und UIElement.LostFocus werden ausgelöst, wenn ein Steuerelement den Fokus erhält oder verliert. Dieses Ereignis wird nicht für FocusManager.TryMoveFocus() ausgelöst.

Da dies ein Routingereignis ist, erfolgt Bubbling vom fokussierten Element über die einzelnen übergeordneten Objekte zum Stamm der Objektstruktur nach oben. Auf diese Weise können Sie das Ereignis verarbeiten, sofern angebracht.

Für die Ereignisse **UIElement.GettingFocus** und **UIElement.LosingFocus** erfolgt Bubbling auch vom Steuerelement, aber *vor* der Fokusänderung. Dadurch kann die App die Fokusänderung umleiten oder abbrechen.

Beachten Sie, dass die Ereignisse GettingFocus und LosingFocus synchron sind, während die Ereignisse GotFocus und LostFocus asynchron sind. Wenn der Fokus verlagert wird, da die App die Control.Focus()-Methode aufruft, wird z.B. GettingFocus während des Aufrufs ausgelöst, GotFocus wird jedoch nach dem Aufruf ausgelöst.

UIElements können mit den Ereignissen GettingFocus und LosingFocus verknüpft werden und das Ziel (mithilfe der NewFocusedElement-Eigenschaft) ändern, bevor der Fokus verlagert wird. Selbst wenn das Ziel geändert wurde, erfolgt weiterhin Ereignis-Bubbling und ein anderes übergeordnetes Element kann das Ziel erneut ändern.

Um Eintrittsvarianzprobleme zu vermeiden, werden Ausnahmen ausgegeben, wenn Sie versuchen, den Fokus zu verlagern (mit FocusManager.TryMoveFocus oder Control.Focus), während für diese Ereignisse Bubbling erfolgt.

Diese Ereignisse werden unabhängig vom Grund der Fokusverlagerung ausgelöst (z.B. Tab-Navigation, XYFocus-Navigation, programmgesteuert).

Die folgende Abbildungzeigt, wie beim Verschieben von A nach rechts XYFocus LVI4 als Kandidat auswählt. LVI4 löst dann das GettingFocus-Ereignis aus, wobei ListView die Möglichkeit hat, den Fokus erneut zu LVI3 zuzuweisen.

![Fokusereignisse](images/keyboard/focus-events.png)

*Fokusereignisse*

In diesem Codebeispiel wird veranschaulicht, wie das OnGettingFocus-Ereignis verarbeitet und der Fokus basierend auf dem zuvor festgelegten Fokus umgeleitet wird.

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

In diesem Codebeispiel wird veranschaulicht, wie Sie das OnLosingFocus-Ereignis für ein CommandBar-Objekt verarbeiten und darauf warten, den Fokus zu legen, bis das DropDown-Menü geschlossen wird.

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

### <a name="losingfocus-and-gettingfocus-event-order"></a>LosingFocus und GettingFocus – Ereignisreihenfolge

LosingFocus und GettingFocus sind synchrone Ereignisse. Das heißt, der Fokus wird nicht verlagert, während für diese Ereignisse Bubbling erfolgt. Da LostFocus und GotFocus asynchrone Ereignisse sind, kann jedoch nicht garantiert werden, dass der Fokus vor der Ausführung des Handlers nicht erneut verlagert wird. Es ist nur sichergestellt, dass der LostFocus-Handler vor dem GotFocus-Handler ausgeführt wird.

Die Reihenfolge der Ausführung ist wie folgt festgelegt;

1.  Sync LosingFocus: Wenn LosingFocus den Fokus zurück auf das Element zurücksetzt, das den Fokus verloren oder Cancel=true festgelegt hat, finden keine weiteren Ereignisse statt.
2.  Sync GettingFocus: Wenn GettingFocus den Fokus zurück auf das Element zurücksetzt, das den Fokus verloren oder Cancel=true festgelegt hat, finden keine weiteren Ereignisse statt.
3.  Async LostFocus
4.  Async GotFocus

## <a name="find-the-first-and-last-focusable-element-a-namefindfirstfocusableelement"></a>Suchen des ersten und letzten fokussierbaren Elements <a name="findfirstfocusableelement">

Die Methoden **FocusManager.FindFirstFocusableElement** und **FocusManager.FindLastFocusableElement** ermöglichen das Verlagern des Fokus auf das erste oder letzte fokussierbare Element im Bereich eines Objekts (UIElement-Elementstruktur oder TextElement-Textstruktur). Wenn Sie diese Methoden aufrufen, geben Sie den Bereich an. Wenn das Argument NULL ist, ist der Bereich das aktuelle Fenster.

**Hinweis** Diese Methoden können NULL zurückgeben, wenn keine fokussierbaren Elemente im Bereich vorhanden sind.

<a name="popup-ui-code-sample"></a>Im folgenden Codebeispiel wird veranschaulicht, wie Sie angeben, dass die Schaltflächen einer CommandBar ein direktionales Verhalten (Umbruch) aufweisen, wie im Artikel [Tastaturinteraktionen](keyboard-interactions.md#popup-ui) beschrieben.

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
