---
author: mijacobs
description: Mit verbundenen Animationen können Sie eine dynamische und ansprechende Navigationsfunktionalität erstellen, indem Sie den Übergang eines Elements zwischen zwei verschiedenen Ansichten animieren.
title: Verbundene Animationen
template: detail.hbs
ms.author: jimwalk
ms.date: 10/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: conrwi
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: a789a8f082192b79b3e96990827f9a4f6a0eacbc
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2815302"
---
# <a name="connected-animation-for-uwp-apps"></a>Verbundene Animation für UWP-Apps

## <a name="what-is-connected-animation"></a>Was ist eine verbundene Animation?

Mit verbundenen Animationen können Sie eine dynamische und ansprechende Navigationsfunktionalität erstellen, indem Sie den Übergang eines Elements zwischen zwei verschiedenen Ansichten animieren. So können Benutzer den Kontext beibehalten, und es entsteht Kontinuität zwischen den Ansichten.
In einer verbundenen Animation scheint ein Element zwischen zwei Ansichten weiterzubestehen, während sich der UI-Inhalt ändert. Dabei fliegt das Element von seinem Standort in der Quellansicht über den Bildschirm zu seinem Ziel in der neuen Ansicht herüber. Dadurch wird der gemeinsame Inhalt zwischen den beiden Ansichten unterstrichen, und es entsteht ein schöner, dynamischer Effekt als Teil eines Übergangs.

## <a name="see-it-in-action"></a>Sehen Sie es in Aktion

In diesem kurzen Video verwendet eine App eine verbundene Animation, um ein Elementbild zu animieren, wenn es als Teil der Überschrift der nächsten Seite weiterbesteht. Dieser Effekt trägt dazu bei, Benutzerkontext beim Übergang beizubehalten.

![UI-Beispiel für kontinuierliche Bewegung](images/continuous3.gif)

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

## <a name="how-to-implement"></a>Implementierung

Das Einrichten einer verbundenen Animation besteht aus zwei Schritten:

1.  Dem *Vorbereiten* eines Animationsobjekts auf der Quellseite, wodurch dem System angezeigt wird, dass das Quellelement Teil der verbundenen Animation ist 
2.  Dem *Starten* der Animation auf der Zielseite, wobei ein Verweis auf das Zielelement übergeben wird

Zwischen diesen beiden Schritten wird das Quellelement eingefroren über anderen UI-Elementen in der App angezeigt, sodass sich gleichzeitig weitere Übergangsanimationen ausführen lassen. Aus diesem Grund sollten nicht Sie länger als ~250Millisekunden zwischen den beiden Schritten warten, da die Anzeige des Quellelements stören kann. Wenn Sie eine Animation vorbereiten und diese nicht innerhalb von drei Sekunden starten, wird sie vom System gelöscht und alle folgenden Aufrufe von **TryStart** schlagen fehl.

Zugriff auf die aktuelle ConnectedAnimationService-Instanz erhalten Sie, indem Sie **ConnectedAnimationService.GetForCurrentView** aufrufen. Rufen Sie zum Vorbereiten einer Animation **PrepareToAnimate** in dieser Instanz auf, um einen Verweis auf einen eindeutigen Schlüssel und das UI-Element zu übergeben, das Sie für den Übergang verwenden möchten. Mithilfe des eindeutigen Schlüssels können Sie die Animation später abrufen, z.B. auf einer anderen Seite.

```csharp
ConnectedAnimationService.GetForCurrentView().PrepareToAnimate("image", SourceImage);
```

Rufen Sie zum Starten der Animation **ConnectedAnimation.TryStart** auf. Sie können die richtige Animationsinstanz abrufen, indem Sie mit dem eindeutigen Schlüssel, den Sie beim Erstellen der Animation angegeben haben, **ConnectedAnimationService.GetAnimation** aufrufen.

```csharp
ConnectedAnimation imageAnimation = 
    ConnectedAnimationService.GetForCurrentView().GetAnimation("image");
if (imageAnimation != null)
{
    imageAnimation.TryStart(DestinationImage);
}
```

Es folgt ein vollständiges Beispiel für die Verwendung von ConnectedAnimationService zum Erstellen eines Übergangs zwischen zwei Seiten.

*SourcePage.xaml*

```xaml
<Image x:Name="SourceImage"
       Width="200"
       Height="200"
       Stretch="Fill"
       Source="Assets/StoreLogo.png" />
```

*SourcePage.xaml.cs*

```csharp
private void NavigateToDestinationPage()
{
    ConnectedAnimationService.GetForCurrentView().PrepareToAnimate("image", SourceImage);
    Frame.Navigate(typeof(DestinationPage));
}
```

*DestinationPage.xaml*

```xaml
<Image x:Name="DestinationImage"
       Width="400"
       Height="400"
       Stretch="Fill"
       Source="Assets/StoreLogo.png" />
```

*DestinationPage.xaml.cs*

```csharp
protected override void OnNavigatedTo(NavigationEventArgs e)
{
    base.OnNavigatedTo(e);

    ConnectedAnimation imageAnimation = 
        ConnectedAnimationService.GetForCurrentView().GetAnimation("image");
    if (imageAnimation != null)
    {
        imageAnimation.TryStart(DestinationImage);
    }
}
```

## <a name="connected-animation-in-list-and-grid-experiences"></a>Verbundene Animationen in Listen- und Rasterumgebungen

Sie werden wahrscheinlich häufig verbundene Animationen aus einem Listen- oder Rastersteuerelement erstellen wollen. Um diesen Prozess zu vereinfachen, können Sie zwei neue Methoden von **ListView** und **GridView** verwenden: **PrepareConnectedAnimation** und **TryStartConnectedAnimationAsync**.
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

Rufen Sie zum Vorbereiten einer verbundenen Animation mit der Ellipse für ein bestimmtes Element die Methode **PrepareConnectedAnimation** mit einem eindeutigen Schlüssel, dem Element und dem Namen „PortraitEllipse” auf.

```csharp
void PrepareAnimationWithItem(ContactsItem item)
{
     ContactsListView.PrepareConnectedAnimation("portrait", item, "PortraitEllipse");
}
```

Alternativ können Sie **TryStartConnectedAnimationAsync** verwenden, um eine Animation mit diesem Element als Ziel zu starten, beispielsweise beim Zurücknavigieren aus einer Detailansicht. Wenn Sie die Datenquelle für die **ListView** gerade geladen haben, wartet **TryStartConnectedAnimationAsync** mit dem Start der Animation, bis der entsprechende Elementcontainer erstellt wurde.

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

Eine *koordinierte Animation* ist eine besondere Art von Eingangsanimation, bei der ein Element zusammen mit dem verbundenen Animationsziel angezeigt wird. Dabei wird es zusammen mit dem verbundenen Animationselement animiert, wenn es sich über den Bildschirm bewegt. Koordinierte Animationen können einem Übergang weitere visuelle Spannung hinzufügen und die Aufmerksamkeit des Benutzers auf den Kontext lenken, den die Quell- und die Zielansicht teilen. In diesen Bildern wird die Beschriftungs-UI für das Element mithilfe einer koordinierten Animation animiert.

Verwenden Sie die Überladung von **TryStart** mit zwei Parametern, um koordinierte Elemente zu einer verbundenen Animation hinzuzufügen. Dieses Beispiel zeigt eine koordinierte Animation von einem Rasterlayout mit dem Namen „DescriptionRoot”, das zusammen mit einem verbundenen Animationselement mit dem Namen „CoverImage” gestartet wird.

*DestinationPage.xaml*

```xaml
<Grid>
    <Image x:Name="CoverImage" />
    <Grid x:Name="DescriptionRoot" />
</Grid>
```

*DestinationPage.xaml.cs*

```csharp
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
- Warten Sie zwischen dem Vorbereiten und dem Starten einer verbundenen Animation nicht auf Netzwerkanfragen oder andere zeitaufwendige asynchrone Vorgänge. Möglicherweise müssen Sie die erforderlichen Informationen laden, um den Übergang vorab auszuführen, oder ein Platzhalterbild mit niedriger Auflösung verwenden, während ein Bild mit hoher Auflösung in der Zielansicht geladen wird.
- Verwenden Sie [SuppressNavigationTransitionInfo](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.media.animation.suppressnavigationtransitioninfo), um eine Übergangsanimation in einem **Frame** bei Verwendung von **ConnectedAnimationService** zu verhindern, da verbundene Animationen nicht gleichzeitig mit den Standard-Navigationsübergängen verwendet werden sollten. Weitere Informationen zur Verwendung von Navigationsübergängen finden Sie unter [NavigationThemeTransition](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.animation.navigationthemetransition.aspx).


## <a name="download-the-code-samples"></a>Codebeispiele herunterladen

Ein [Beispiel für eine verbundene Animation](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2014393/ConnectedAnimationSample) finden Sie in der [WindowsUIDevLabs](https://github.com/Microsoft/WindowsUIDevLabs)-Beispielgalerie.

## <a name="related-articles"></a>Verwandte Artikel

- [ConnectedAnimation](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.animation.connectedanimation)
- [ConnectedAnimationService](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.media.animation.connectedanimation.aspx)
- [NavigationThemeTransition](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.animation.navigationthemetransition.aspx)
