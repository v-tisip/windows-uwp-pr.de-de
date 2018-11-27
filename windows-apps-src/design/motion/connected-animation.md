---
description: Mit verbundenen Animationen können Sie eine dynamische und ansprechende Navigationsfunktionalität erstellen, indem Sie den Übergang eines Elements zwischen zwei verschiedenen Ansichten animieren.
title: Verbundene Animationen
template: detail.hbs
ms.date: 10/04/2018
ms.topic: article
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: conrwi
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: ce639faac66e93b65a398e6d9cdc700546fc68ab
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7855458"
---
# <a name="connected-animation-for-uwp-apps"></a>Verbundene Animation für UWP-Apps

Mit verbundenen Animationen können Sie eine dynamische und ansprechende Navigationsfunktionalität erstellen, indem Sie den Übergang eines Elements zwischen zwei verschiedenen Ansichten animieren. So können Benutzer den Kontext beibehalten, und es entsteht Kontinuität zwischen den Ansichten.

In einer verbundenen Animation scheint ein Element zwischen zwei Ansichten weiterzubestehen, während sich die UI-Inhalte, Quellansicht über den Bildschirm von seinem Standort in der Quellansicht zu seinem Ziel in der neuen Ansicht "fortsetzen". Dies den gemeinsamen Inhalt zwischen den Ansichten hervorhebt und entsteht ein schönen, dynamischen Effekt als Teil eines Übergangs.

> **Wichtige APIs**: [ConnectedAnimation-Klasse](/uwp/api/windows.ui.xaml.media.animation.connectedanimation), [ConnectedAnimationService-Klasse](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice)

## <a name="see-it-in-action"></a>Sehen Sie es in Aktion

In diesem kurzen Video verwendet eine app eine verbundene Animation, um ein Element animieren, als es "Weiter" Teil der Überschrift der nächsten Seite weiterbesteht. Dieser Effekt trägt dazu bei, Benutzerkontext beim Übergang beizubehalten.

![Verbundene Animationen](images/connected-animations/example.gif)

<!-- 
<iframe width=640 height=360 src='https://microsoft.sharepoint.com/portals/hub/_layouts/15/VideoEmbedHost.aspx?chId=552c725c%2De353%2D4118%2Dbd2b%2Dc2d0584c9848&amp;vId=b2daa5ee%2Dbe15%2D4503%2Db541%2D1328a6587c36&amp;width=640&amp;height=360&amp;autoPlay=false&amp;showInfo=true' allowfullscreen></iframe>
-->

## <a name="video-summary"></a>Video-Zusammenfassung

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev005/player]

## <a name="connected-animation-and-the-fluent-design-system"></a>Verbundene Animationen und das Fluent Design-System

 Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten. Verbundene Animation ist eine Komponente des Fluent Design-Systems, die Bewegung in Ihre App bringt. Weitere Informationen finden Sie in der [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).

## <a name="why-connected-animation"></a>Warum eine verbundene Animation?

Beim Navigieren zwischen Seiten ist es wichtig, dass der Benutzer versteht, welcher neue Inhalt nach der Navigation dargestellt wird und in welcher Beziehung dieser zu seiner Absicht beim Navigieren steht. Verbundene Animationen bieten eine leistungsstarke visuelle Metapher, die die Beziehung zwischen zwei Ansichten hervorhebt, indem sie den Fokus des Benutzers auf den gemeinsamen Inhalt zwischen diesen beiden lenkt. Darüber hinaus fügen verbundene Animationen der Seitennavigation visuelle Spannung und einen Feinschliff hinzu, die dazu beitragen können, dass sich die Bewegungsgestaltung Ihrer App von anderen unterscheidet.

## <a name="when-to-use-connected-animation"></a>Verwendungsszenarien für verbundene Animationen

Verbundene Animationen werden in der Regel bei einem Seitenwechsel verwendet, sie können jedoch immer verwendet werden, wenn Sie Inhalt in einer UI ändern und möchten, dass der Benutzerkontext beibehalten wird. Sie sollten es in Betracht ziehen, eine verbundene Animation anstelle eines [Drills in einem Navigationsübergangs](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.animation.navigationthemetransition.aspx) zu verwenden, wenn die Quell- und die Zielansicht ein gemeinsames Bild oder ein anderes gemeinsames UI-Element aufweisen.

## <a name="configure-connected-animation"></a>Konfigurieren von verbundene Animationen

> [!IMPORTANT]
> Dieses Feature erfordert, dass die Ziel Version Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher. Die Konfiguration-Eigenschaft ist nicht in frühere SDKs verfügbar. Sie können eine minimale niedrigere Version als SDK 17763 Ziel mit adaptivem Code oder bedingten XAML. Weitere Informationen finden Sie unter [versionsadaptive apps](/debug-test-perf/version-adaptive-apps).

Ab Windows 10, Version 1809, weitere verbundene Animationen Benutzeroberflächenelement Fluent Design durch die Bereitstellung der Animation Konfigurationen zugeschnitten sind speziell für Vorwärts und rückwärts Navigation zwischen Seiten.

Durch Festlegen der Konfiguration-Eigenschaft auf die ConnectedAnimation Geben Sie eine Animation-Konfiguration. (Wir zeigen Beispiele hierfür im nächsten Abschnitt.)

Diese Tabelle beschreibt die verfügbaren Varianten. Weitere Informationen über die Bewegung Prinzipien in diese Animationen angewendet finden Sie unter [Direktionalität und Schwerkraft](index.md).

| [GravityConnectedAnimationConfiguration]() |
| - |
| Dies ist die Standardkonfiguration und wird für die Vorwärtsnavigation empfohlen. |
Wie der Benutzer in der app (A zu B) in vorwärtsrichtung navigiert, wird das verbundene Element sollen physisch "auf der Seite" angezeigt. Dabei wird das Element angezeigt wird, um vorwärts in Z-Bereich zu verschieben und löscht etwas als eine Auswirkung der Schwerkraft Teilnahme an halten. Um die Effekte der Schwerkraft zu umgehen, wird das Element erhält Geschwindigkeit und in die endgültige Position beschleunigt. Das Ergebnis ist eine Animation "Skalierung und Dip". |

| [DirectConnectedAnimationConfiguration]() |
| - |
| Wenn der Benutzer in der app (B nach A) Rückwärtsnavigation navigiert, ist die Animation direkter. Das verbundene Element übersetzt linear B in ein mit einer Decelerate kubische Bézierkurven-Beschleunigungsfunktion. Die Rückwärtsnavigation visuell gibt den Benutzer in den vorherigen Zustand so schnell wie möglich und gleichzeitig den Kontext für den Ablauf der Navigation. |

| [BasicConnectedAnimationConfiguration]() |
| - |
| Dies ist der Standardwert (nur und) Animation in Versionen vor Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) verwendet. |

### <a name="connectedanimationservice-configuration"></a>ConnectedAnimationService-Konfiguration

Die [ConnectedAnimationService](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice) -Klasse hat zwei Eigenschaften, die für die einzelnen Animationen anstelle der Dienst gelten.

- [DefaultDuration](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.defaultduration)
- [DefaultEasingFunction](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.defaulteasingfunction)

Um die verschiedenen Effekte zu erzielen, einige Konfigurationen ignorieren diese Eigenschaften auf ConnectedAnimationService und ihren eigenen Werte verwenden, wie in dieser Tabelle beschrieben.

| Konfiguration | Hinsicht DefaultDuration? | Hinsicht DefaultEasingFunction? |
| - | - | - |
| Schwerkraft | Ja | Ja* <br/> **Die grundlegende Übersetzung von A zu B verwendet diese Beschleunigungsfunktion, aber "Schwerkraft Dip" verfügt über einen eigenen Beschleunigungsfunktion.*  |
| Direkte | Nein <br/> *Über 150 ms animiert.*| Nein <br/> *Die Beschleunigungsfunktion Decelerate verwendet.* |
| Einfach | Ja | Ja |

## <a name="how-to-implement-connected-animation"></a>Verbundene Animationen Implementierung

Das Einrichten einer verbundenen Animation besteht aus zwei Schritten:

1. *Vorbereiten* eines Animationsobjekts auf der Quellseite, die das System anzeigt, dass das Quellelement der verbundenen Animation teilnimmt.
1. *Starten* der Animation auf der Seite "Ziel" einen Verweis auf das Zielelement übergeben.

Beim Navigieren von der Quellseite, rufen Sie [ConnectedAnimationService.GetForCurrentView](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.getforcurrentview) um eine Instanz des ConnectedAnimationService abzurufen. Eine Animation vorbereiten, rufen Sie [PrepareToAnimate](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.preparetoanimate) in dieser Instanz auf und übergeben Sie einen eindeutigen Schlüssel und das Element der Benutzeroberfläche, die, das Sie in den Übergang verwenden möchten. Mithilfe des eindeutigen Schlüssels können Sie die Animation später auf der Seite "Ziel" abrufen.

```csharp
ConnectedAnimationService.GetForCurrentView()
    .PrepareToAnimate("forwardAnimation", SourceImage);
```

Bei die Navigation, starten Sie die Animation in der Seite "Ziel". Rufen Sie zum Starten der Animation [ConnectedAnimation.TryStart](/uwp/api/windows.ui.xaml.media.animation.connectedanimation.trystart) auf. Sie können die richtige Animationsinstanz abrufen, indem Sie mit dem eindeutigen Schlüssel, den Sie beim Erstellen der Animation angegeben haben, [ConnectedAnimationService.GetAnimation](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.getanimation) aufrufen.

```csharp
ConnectedAnimation animation =
    ConnectedAnimationService.GetForCurrentView().GetAnimation("forwardAnimation");
if (animation != null)
{
    animation.TryStart(DestinationImage);
}
```

### <a name="forward-navigation"></a>Navigationsverlauf

In diesem Beispiel wird veranschaulicht, wie ConnectedAnimationService zum Erstellen eines Übergangs für Vorwärts Navigation zwischen zwei Seiten (Page_A, Page_B) verwenden.

Die empfohlene Animation-Konfiguration für Vorwärtsnavigation ist [GravityConnectedAnimationConfiguration](). Dies ist die Standardeinstellung, damit Sie nicht die [Konfiguration](/uwp/api/windows.ui.xaml.media.animation.connectedanimation.configuration) Eigenschaft festgelegt, es sei denn, Sie eine andere Konfiguration angeben möchten, müssen.

Richten Sie die Animation auf der Quellseite.

```xaml
<!-- Page_A.xaml -->

<Image x:Name="SourceImage"
       HorizontalAlignment="Left" VerticalAlignment="Top"
       Width="200" Height="200"
       Stretch="Fill"
       Source="Assets/StoreLogo.png"
       PointerPressed="SourceImage_PointerPressed"/>
```

```csharp
// Page_A.xaml.cs

private void SourceImage_PointerPressed(object sender, PointerRoutedEventArgs e)
{
    // Navigate to detail page.
    // Suppress the default animation to avoid conflict with the connected animation.
    Frame.Navigate(typeof(Page_B), null, new SuppressNavigationTransitionInfo());
}

protected override void OnNavigatingFrom(NavigatingCancelEventArgs e)
{
    ConnectedAnimationService.GetForCurrentView()
        .PrepareToAnimate("forwardAnimation", SourceImage);
    // You don't need to explicitly set the Configuration property because
    // the recommended Gravity configuration is default.
    // For custom animation, use:
    // animation.Configuration = new BasicConnectedAnimationConfiguration();
}
```

Starten Sie die Animation in der Seite "Ziel".

```xaml
<!-- Page_B.xaml -->

<Image x:Name="DestinationImage"
       Width="400" Height="400"
       Stretch="Fill"
       Source="Assets/StoreLogo.png" />
```

```csharp
// Page_B.xaml.cs

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    base.OnNavigatedTo(e);

    ConnectedAnimation animation =
        ConnectedAnimationService.GetForCurrentView().GetAnimation("forwardAnimation");
    if (animation != null)
    {
        animation.TryStart(DestinationImage);
    }
}
```

### <a name="back-navigation"></a>Rückwärtsnavigation

Für die Rückwärtsnavigation (Page_B, Page_A), führen Sie die gleichen Schritte, aber die Quell- und Zieldatenträger Seiten rückgängig gemacht werden.

Wenn der Benutzer zurück navigiert, erwarten sie die app so schnell wie möglich in den vorherigen Zustand zurückgegeben werden. Aus diesem Grund ist die empfohlene Konfiguration [DirectConnectedAnimationConfiguration](). Diese Animation ist schneller und direkter und Decelerate geschwindigkeitsverlauf verwendet.

Richten Sie die Animation auf der Quellseite.

```csharp
// Page_B.xaml.cs

protected override void OnNavigatingFrom(NavigatingCancelEventArgs e)
{
    if (e.NavigationMode == NavigationMode.Back)
    {
        ConnectedAnimationService.GetForCurrentView()
            .PrepareToAnimate("backAnimation", DestinationImage);

        // Use the recommended configuration for back animation.
        animation.Configuration = new DirectConnectedAnimationConfiguration();
    }
}
```

Starten Sie die Animation in der Seite "Ziel".

```csharp
// Page_A.xaml.cs

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    base.OnNavigatedTo(e);

    ConnectedAnimation animation =
        ConnectedAnimationService.GetForCurrentView().GetAnimation("backAnimation");
    if (animation != null)
    {
        animation.TryStart(SourceImage);
    }
}
```

Zwischen dem Zeitpunkt, die die Animation eingerichtet ist und wenn sie gestartet wird wird das Quellelement eingefroren über anderen UI in der app angezeigt. Auf diese Weise können Sie gleichzeitig weitere Übergangsanimationen ausführen. Aus diesem Grund sollten nicht Sie länger als ~ 250 Millisekunden zwischen den beiden Schritten warten, da das Vorhandensein des Quellelements Quellelements stören kann. Wenn Sie eine Animation vorbereiten und diese nicht innerhalb von drei Sekunden starten, wird sie vom System gelöscht und alle folgenden Aufrufe von [TryStart](/uwp/api/windows.ui.xaml.media.animation.connectedanimation.trystart) schlagen fehl.

## <a name="connected-animation-in-list-and-grid-experiences"></a>Verbundene Animationen in Listen- und Rasterumgebungen

Sie werden wahrscheinlich häufig verbundene Animationen aus einem Listen- oder Rastersteuerelement erstellen wollen. Die beiden Methoden können auf [ListView](/uwp/api/windows.ui.xaml.controls.listview) und [GridView](/uwp/api/windows.ui.xaml.controls.gridview), [PrepareConnectedAnimation](/uwp/api/windows.ui.xaml.controls.listviewbase.prepareconnectedanimation) und [TryStartConnectedAnimationAsync](/uwp/api/windows.ui.xaml.controls.listviewbase.trystartconnectedanimationasync), Sie um diesen Prozess zu vereinfachen.

Nehmen wir beispielsweise an, Sie haben eine **ListView**, die ein Element mit dem Namen „PortraitEllipse” in der Datenvorlage enthält.

```xaml
<ListView x:Name="ContactsListView" Loaded="ContactsListView_Loaded">
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="vm:ContactsItem">
            <Grid>
                …
                <Ellipse x:Name="PortraitEllipse" … />
            </Grid>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

Rufen Sie zum Vorbereiten einer verbundenen Animation mit der Ellipse für ein bestimmtes Element die [PrepareConnectedAnimation](/uwp/api/windows.ui.xaml.controls.listviewbase.prepareconnectedanimation) Methode mit einem eindeutigen Schlüssel, das Element und den Namen "PortraitEllipse" ein.

```csharp
void PrepareAnimationWithItem(ContactsItem item)
{
     ContactsListView.PrepareConnectedAnimation("portrait", item, "PortraitEllipse");
}
```

Verwenden Sie zum Starten einer Animation mit diesem Element als Ziel, z. B. wenn aus einer Detailansicht zurück navigiert [TryStartConnectedAnimationAsync](/uwp/api/windows.ui.xaml.controls.listviewbase.trystartconnectedanimationasync). Wenn Sie die Datenquelle für die ListView gerade geladen haben, wartet TryStartConnectedAnimationAsync mit dem Start der Animation, bis der entsprechende Elementcontainer erstellt wurde.

```csharp
private void ContactsListView_Loaded(object sender, RoutedEventArgs e)
{
    ContactsItem item = GetPersistedItem(); // Get persisted item
    if (item != null)
    {
        ContactsListView.ScrollIntoView(item);
        ConnectedAnimation animation =
            ConnectedAnimationService.GetForCurrentView().GetAnimation("portrait");
        if (animation != null)
        {
            await ContactsListView.TryStartConnectedAnimationAsync(
                animation, item, "PortraitEllipse");
        }
    }
}
```

## <a name="coordinated-animation"></a>Koordinierte Animation

![Koordinierte Animation](images/connected-animations/coordinated_example.gif)

<!--
<iframe width=640 height=360 src='https://microsoft.sharepoint.com/portals/hub/_layouts/15/VideoEmbedHost.aspx?chId=552c725c%2De353%2D4118%2Dbd2b%2Dc2d0584c9848&amp;vId=9066bbbe%2Dcf58%2D4ab4%2Db274%2D595616f5d0a0&amp;width=640&amp;height=360&amp;autoPlay=false&amp;showInfo=true' allowfullscreen></iframe>
-->

Eine *koordinierte Animation* besteht eine besondere Art von Eingangsanimation, bei denen ein Element zusammen mit dem verbundenen Animationsziel zusammen mit dem verbundenen Animationselement über den Bildschirm bewegt. Koordinierte Animationen können einem Übergang weitere visuelle Spannung hinzufügen und die Aufmerksamkeit des Benutzers auf den Kontext lenken, den die Quell- und die Zielansicht teilen. In diesen Bildern wird die Beschriftungs-UI für das Element mithilfe einer koordinierten Animation animiert.

Wenn eine koordinierte Animation die Schwerkraft Konfiguration verwendet, wird auf dem verbundenen Animationselement und die koordinierte Elemente Schwerkraft angewendet. Die koordinierte Elemente werden zusammen mit dem verbundenen Element "swoop" werden, damit die Elemente wirklich koordiniert.

Verwenden Sie die Überladung von **TryStart** mit zwei Parametern, um koordinierte Elemente zu einer verbundenen Animation hinzuzufügen. Dieses Beispiel zeigt eine koordinierte Animation von einem Rasterlayout mit dem Namen "DescriptionRoot", die zusammen mit einem verbundenen Animationselement mit dem Namen "coverimage gestartet" eingibt.

```xaml
<!-- DestinationPage.xaml -->
<Grid>
    <Image x:Name="CoverImage" />
    <Grid x:Name="DescriptionRoot" />
</Grid>
```

```csharp
// DestinationPage.xaml.cs
void OnNavigatedTo(NavigationEventArgs e)
{
    var animationService = ConnectedAnimationService.GetForCurrentView();
    var animation = animationService.GetAnimation("coverImage");

    if (animation != null)
    {
        // Don’t need to capture the return value as we are not scheduling any subsequent
        // animations
        animation.TryStart(CoverImage, new UIElement[] { DescriptionRoot });
     }
}
```

## <a name="dos-and-donts"></a>Empfohlene und nicht empfohlene Vorgehensweisen

- Verwenden Sie eine verbundene Animation bei Seitenübergängen, bei denen ein Element zwischen der Quell- und der Zielseite geteilt wird.
- Verwenden Sie [GravityConnectedAnimationConfiguration]() für Navigationsverlauf.
- Verwenden Sie [DirectConnectedAnimationConfiguration]() für die Rückwärtsnavigation.
- Warten Sie nicht auf Netzwerkanfragen oder andere zeitaufwendige asynchrone Vorgänge zwischen vorbereiten und dem Starten einer verbundenen Animation. Möglicherweise müssen Sie die erforderlichen Informationen laden, um den Übergang vorab auszuführen, oder ein Platzhalterbild mit niedriger Auflösung verwenden, während ein Bild mit hoher Auflösung in der Zielansicht geladen wird.
- Verwenden Sie [SuppressNavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.suppressnavigationtransitioninfo) , um zu verhindern, dass eine übergangsanimation in einem **Frame** bei Verwendung **ConnectedAnimationService**, da verbundene Animationen werden nicht gleichzeitig mit der Standardnavigation verwendet werden soll wechselt. Weitere Informationen zur Verwendung von Navigationsübergängen finden Sie unter [NavigationThemeTransition](/uwp/api/Windows.UI.Xaml.Media.Animation.NavigationThemeTransition).

## <a name="download-the-code-samples"></a>Codebeispiele herunterladen

Ein [Beispiel für eine verbundene Animation](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2014393/ConnectedAnimationSample) finden Sie in der [WindowsUIDevLabs](https://github.com/Microsoft/WindowsUIDevLabs)-Beispielgalerie.

## <a name="related-articles"></a>Verwandte Artikel

[ConnectedAnimation](/uwp/api/windows.ui.xaml.media.animation.connectedanimation)

[ConnectedAnimationService](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice)

[NavigationThemeTransition](/uwp/api/Windows.UI.Xaml.Media.Animation.NavigationThemeTransition)
