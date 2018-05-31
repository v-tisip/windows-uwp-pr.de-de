---
author: serenaz
Description: The Universal Windows Platform (UWP) provides a consistent back navigation system for traversing the user's navigation history within an app and, depending on the device, from app to app.
title: Navigationsverlauf und Rückwärtsnavigation (Windows-Apps)
ms.assetid: e9876b4c-242d-402d-a8ef-3487398ed9b3
isNew: true
label: History and backwards navigation
template: detail.hbs
op-migration-status: ready
ms.author: sezhen
ms.date: 11/22/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: cefcefc9df85b512456c5fb2e556ad95e56d4999
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1831984"
---
#  <a name="navigation-history-and-backwards-navigation-for-uwp-apps"></a>Navigationsverlauf und Rückwärtsnavigation für UWP-Apps

> **Wichtige APIs**: [BackRequested event](https://docs.microsoft.com/uwp/api/Windows.UI.Core.SystemNavigationManager.BackRequested), [SystemNavigationManager class](https://docs.microsoft.com/uwp/api/Windows.UI.Core.SystemNavigationManager), [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto#Windows_UI_Xaml_Controls_Page_OnNavigatedTo_Windows_UI_Xaml_Navigation_NavigationEventArgs_)

Die universelle Windows-Plattform (UWP) enthält ein einheitliches System zur Rückwärtsnavigation, mit dem der Navigationsverlauf des Benutzers innerhalb einer App und je nach Gerät von App zu App durchlaufen werden kann.

Um die Rückwärtsnavigation in Ihrer App zu implementieren, platzieren Sie einen [Zurück](#Back-button)-Button in der oberen linken Ecke der Benutzeroberfläche Ihrer App. Wenn Ihre App das [NavigationView](../controls-and-patterns/navigationview.md)-Steuerelement verwendet, können Sie die integrierte [Zurück-Schaltfläche von NavigationView](../controls-and-patterns/navigationview.md#backwards-navigation) verwenden. 

Der Benutzer erwartet, dass durch Drücken der Zurück-Schaltfläche die vorherige Seite im Navigationsverlauf der App aufgerufen wird. Sie können entscheiden, welche Navigationsaktionen dem Navigationsverlauf hinzugefügt werden sollen und wie auf das Drücken der Zurück-Schaltfläche reagiert werden soll.

## <a name="back-button"></a>Zurück-Schaltfläche

Um einen Zurück-Schaltfläche zu erstellen, verwenden Sie das [Button](../controls-and-patterns/buttons.md)-Steuerelement mit dem `NavigationBackButtonNormalStyle`-Stil, und platzieren Sie die Schaltfläche in der oberen linken Ecke der Benutzeroberfläche Ihrer App.

![Zurück-Schaltfläche oben links in der App-Oberfläche](images/back-nav/BackEnabled.png)

```xaml
<Button Style="{StaticResource NavigationBackButtonNormalStyle}"/>
```

Wenn Ihre App eine obere [CommandBar](../controls-and-patterns/app-bars.md) hat, wird das 44 Pixel hohe Button-Steuerelement nicht sehr gut neben 48 Pixel hohe AppBarButtons passen. Um jedoch Inkonsistenzen zu vermeiden, richten Sie den oberen Teil der Schaltfläche innerhalb der 48 Pixel-Grenzen aus.

![Zurück-Schaltfläche in der oberen Befehlsleiste](images/back-nav/CommandBar.png)

```xaml
<Button VerticalAlignment="Top" HorizontalAlignment="Left" 
Style="{StaticResource NavigationBackButtonNormalStyle}"/>
```

Um UI-Elemente zu minimieren, die sich in Ihrer App bewegen, zeigen Sie eine deaktivierte Zurück-Schaltfläche an, wenn sich nichts im Backstack befindet (siehe Codebeispiel unten).

![Zustände der Zurück-Schaltfläche](images/back-nav/BackDisabled.png)

## <a name="code-example"></a>Codebeispiel

Das folgende Codebeispiel demonstriert, wie man das Rückwärtsnavigationsverhalten mit einer Zurück-Schaltfläche implementiert. Der Code reagiert auf das Button-Ereignis [**Click**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.Click) und deaktiviert/aktiviert die Sichtbarkeit der Schaltfläche in [**OnNavigatedTo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto#Windows_UI_Xaml_Controls_Page_OnNavigatedTo_Windows_UI_Xaml_Navigation_NavigationEventArgs_), das beim Navigieren zu einer neuen Seite aufgerufen wird. Das Codebeispiel behandelt auch Eingaben von Hardware- und Softwaresystem-Zurück-Schaltflächen, indem es einen Listener für das [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.core.systemnavigationmanager.BackRequested)-Ereignis registriert.

```xaml
<Page x:Class="AppName.MainPage">
...
<Button x:Name="BackButton" Click="Back_Click" Style="{StaticResource NavigationBackButtonNormalStyle}"/>
...
<Page/>
```

Code-Behind:

```csharp
public MainPage()
{
    KeyboardAccelerator GoBack = new KeyboardAccelerator();
    GoBack.Key = VirtualKey.GoBack;
    GoBack.Invoked += BackInvoked;
    KeyboardAccelerator AltLeft = new KeyboardAccelerator();
    AltLeft.Key = VirtualKey.Left;
    AltLeft.Invoked += BackInvoked;
    this.KeyboardAccelerators.Add(GoBack);
    this.KeyboardAccelerators.Add(AltLeft);
    // ALT routes here
    AltLeft.Modifiers = VirtualKeyModifiers.Menu;
}

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    BackButton.IsEnabled = this.Frame.CanGoBack;
}

private void Back_Click(object sender, RoutedEventArgs e)
{
    On_BackRequested();
}

// Handles system-level BackRequested events and page-level back button Click events
private bool On_BackRequested()
{
    if (this.Frame.CanGoBack)
    {
        this.Frame.GoBack();
        return true;
    }
    return false;
}

private void BackInvoked (KeyboardAccelerator sender, KeyboardAcceleratorInvokedEventArgs args)
{
    On_BackRequested();
    args.Handled = true;
}
```

Hier registrieren wir einen globalen Listener für das [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.core.systemnavigationmanager.BackRequested)-Ereignis in der Code-Behind-Datei für `App.xaml`. Sie können sich für dieses Ereignis auf jeder Seite registrieren, wenn Sie bestimmte Seiten aus der Rückwärtsnavigation ausschließen oder vor dem Anzeigen der Seite Seitenebenencode ausführen möchten.

App.xaml Code-Behind:

```csharp
Windows.UI.Core.SystemNavigationManager.GetForCurrentView().BackRequested += App_BackRequested;
Frame rootFrame = Window.Current.Content;
rootFrame.PointerPressed += On_PointerPressed;

private void App_BackRequested(object sender, Windows.UI.Core.BackRequestedEventArgs e)
{
    e.Handled = On_BackRequested();
}

private void On_PointerPressed(object sender, PointerRoutedEventArgs e)
{
    bool isXButton1Pressed = e.GetCurrentPoint(sender as UIElement).Properties.PointerUpdateKind == PointerUpdateKind.XButton1Pressed;

    if (isXButton1Pressed)
    {
        e.Handled = On_BackRequested();
    }
}
```

## <a name="optimizing-for-different-device-and-form-factors"></a>Optimierung für unterschiedliche Geräte- und Formfaktoren

Diese Anleitung für das Rückwärtsnavigationsdesign gilt für alle Geräte. Verschiedene Geräte und Formfaktoren können jedoch von der Optimierung profitieren. Dies hängt auch von der Hardware-Zurück-Taste ab, der von verschiedenen Shells unterstützt wird.

- **Smartphone/Tablet**: Ein Hardware- oder Software-Zurück-Schaltfläche ist auf jedem Smartphone und Tablet vorhanden, aber wir empfehlen, einen In-App-Zurück-Schaltfläche zu verwenden, um die Übersichtlichkeit zu erhöhen.
- **Desktop/Hub**: Stellen Sie den In-App-Button in der linken oberen Ecke der Benutzeroberfläche Ihrer App dar.
- **Xbox/TV**: Nutzen Sie keinen Zurück-Schaltfläche. Er macht das UI unnötigerweise unübersichtlich. Verlassen Sie sich stattdessen auf die Gamepad-Taste B, um rückwärts zu navigieren.

Wenn Ihre App auf mehreren Geräten läuft, [erstellen Sie einen benutzerdefinierten visuellen Trigger für die Xbox](../devices/designing-for-tv.md#custom-visual-state-trigger-for-xbox), um die Sichtbarkeit der Schaltfläche umzuschalten. Das NavigationView-Steuerelement schaltet automatisch die Sichtbarkeit der Schaltfläche „Zurück” um, wenn Ihre App auf der Xbox läuft. 

Wir empfehlen, die folgenden Eingaben für die Rückwärtsnavigation zu unterstützen. (Beachten Sie, dass einige dieser Eingaben vom System-BackRequested nicht unterstützt werden und durch separate Ereignisse behandelt werden müssen.

| Eingabe | Ereignis |
| --- | --- |
| Windows-Rücktaste | BackRequested |
| Hardware-Zurück-Taste | BackRequested |
| Shell-Tablet-Modus Zurück-Schaltfläche | BackRequested |
| VirtualKey.XButton1 | PointerPressed |
| VirtualKey.GoBack | KeyboardAccelerator.BackInvoked |
| ALT + NACH-LINKS | KeyboardAccelerator.BackInvoked |

Die oben aufgeführten Codebeispiele zeigen, wie man mit diesen Eingaben umgeht.

## <a name="system-back-behavior-for-backward-compatibilities"></a>System-Rückwärtsverhalten für Rückwärtskompatibilitäten

Bisher nutzten UWP-Apps [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility) für die Rückwärtsnavigation. Die API wird aus Gründen der Abwärtskompatibilität weiterhin unterstützt, aber wir empfehlen nicht mehr, sich auf die Schaltfläche „Zurück” in der Titelleiste zu verlassen. Stattdessen sollte Ihre App eine eigene Zurück-Schaltfläche in der App darstellen.

Wenn Ihre App weiterhin [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility) verwendet, wird die Zurück-Schaltfläche wie gewohnt in der Titelleiste angezeigt.

![Zurück-Schaltfläche in der Titelleiste](images/nav-back-pc.png)

## <a name="guidelines-for-custom-back-navigation-behavior"></a>Richtlinien für das benutzerdefinierte Verhalten der Rückwärtsnavigation

Wenn Sie Ihre eigene Zurück-Stapelnavigation bereitstellen möchten, sollte die Benutzeroberfläche mit anderen Apps konsistent sein. Wir empfehlen, die folgenden Muster für Navigationsaktionen zu verwenden:

<div class="mx-responsive-img">
<table>
<thead>
<tr class="header">
<th align="left">Navigationsaktion</th>
<th align="left">Zum Navigationsverlauf hinzufügen?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top;"><strong>Seite zu Seite, verschiedene Peer-Gruppen</strong></td>
<td style="vertical-align:top;"><strong>Ja</strong>
<p>In der folgenden Abbildung navigiert der Benutzer von Ebene 1 der App zu Ebene 2. Dabei werden Peer-Gruppen durchlaufen, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</p>
<p><img src="images/back-nav/nav-pagetopage-diffpeers-imageonly1.png" alt="Navigation across peer groups" /></p>
<p>In der nächsten Abbildung navigiert der Benutzer zwischen zwei Peer-Gruppen derselben Ebene. Er durchläuft erneut Peer-Gruppen, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</p>
<p><img src="images/back-nav/nav-pagetopage-diffpeers-imageonly2.png" alt="Navigation across peer groups" /></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><strong>Seite zu Seite, gleiche Peer-Gruppe, kein Bildschirmnavigationselement</strong>
<p>Der Benutzer navigiert von einer Seite zu einer anderen mit derselben Peer-Gruppe. Es gibt kein Navigationselement, das immer vorhanden ist (wie Registerkarten/Pivots oder ein angedockter Navigationsbereich) und das eine direkte Navigation zu beiden Seiten ermöglicht.</p></td>
<td style="vertical-align:top;"><strong>Ja</strong>
<p>In der folgenden Abbildung navigiert der Benutzer zwischen zwei Seiten in derselben Peer-Gruppe. Die Seiten verwenden keine Registerkarten oder angedockten Navigationsbereich, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</p>
<p><img src="images/back-nav/nav-pagetopage-samepeer-noosnavelement.png" alt="Navigation within a peer group" /></p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><strong>Seite zu Seite, gleiche Peer-Gruppe, mit einem Bildschirmnavigationselement</strong>
<p>Der Benutzer navigiert von einer Seite zu einer anderen in derselben Peer-Gruppe. Beide Seiten werden im gleichen Navigationselement angezeigt. Beide Seiten verwenden beispielsweise das gleiche Registerkarten/Pivots-Element, oder beide Seiten werden in einem angedockten Navigationsbereich angezeigt.</p></td>
<td style="vertical-align:top;"><strong>Nein</strong>
<p>Wenn der Benutzer die Zurück-Schaltfläche drückt, wird wieder die letzte Seite aufgerufen, die geöffnet war, bevor der Benutzer zur aktuellen Peer-Gruppe navigierte.</p>
<p><img src="images/back-nav/nav-pagetopage-samepeer-yesosnavelement.png" alt="Navigation across peer groups when a navigation element is present" /></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><strong>Anzeigen einer vorübergehenden Benutzeroberfläche</strong>
<p>Die App zeigt ein Popupfenster oder ein untergeordnetes Fenster an, z. B. ein Dialogfeld, einen Begrüßungsbildschirm oder eine Bildschirmtastatur. Anderenfalls wechselt die App in einen speziellen Modus, z. B. den Mehrfachauswahlmodus.</p></td>
<td style="vertical-align:top;"><strong>Nein</strong>
<p>Wenn der Benutzer die Zurück-Schaltfläche drückt, sollte die vorübergehende Benutzeroberfläche geschlossen werden (durch Ausblenden der Bildschirmtastatur, Abbrechen des Dialogfelds usw.) und zur Seite zurückgekehrt werden, die die vorübergehende Benutzeroberfläche aufgerufen hat.</p>
<p><img src="images/back-nav/back-transui.png" alt="Showing a transient UI" /></p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><strong>Aufzählen von Elementen</strong>
<p>Die App zeigt die Inhalte für ein Bildschirmelement an, z. B. die Details für das ausgewählte Element in der Master/Details-Liste.</p></td>
<td style="vertical-align:top;"><strong>Nein</strong>
<p>Das Aufzählen von Elementen ist mit der Navigation innerhalb einer Peer-Gruppe vergleichbar. Wenn der Benutzer die Zurück-Schaltfläche drückt, sollte zu der Seite navigiert werden, die vor der aktuellen Seite angezeigt wurde, die die Elementenaufzählung enthält.</p>
<p><img src="images/back-nav/nav-enumerate.png" alt="Iterm enumeration" /></p></td>
</tr>
</tbody>
</table>
</div>

### <a name="resuming"></a>Fortsetzen

Wenn der Benutzer zu einer anderen App wechselt und zu Ihrer App zurückkehrt, wird empfohlen, zur letzten Seite im Navigationsverlauf zurückzukehren.

## <a name="related-articles"></a>Verwandte Artikel

- [Navigationsgrundlagen](navigation-basics.md)