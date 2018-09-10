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
ms.sourcegitcommit: f5cf806a595969ecbb018c3f7eea86c7a34940f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "3823124"
---
# <a name="connected-animation-for-uwp-apps"></a><span data-ttu-id="ee397-104">Verbundene Animation für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="ee397-104">Connected animation for UWP apps</span></span>

## <a name="what-is-connected-animation"></a><span data-ttu-id="ee397-105">Was ist eine verbundene Animation?</span><span class="sxs-lookup"><span data-stu-id="ee397-105">What is connected animation?</span></span>

<span data-ttu-id="ee397-106">Mit verbundenen Animationen können Sie eine dynamische und ansprechende Navigationsfunktionalität erstellen, indem Sie den Übergang eines Elements zwischen zwei verschiedenen Ansichten animieren.</span><span class="sxs-lookup"><span data-stu-id="ee397-106">Connected animations let you create a dynamic and compelling navigation experience by animating the transition of an element between two different views.</span></span> <span data-ttu-id="ee397-107">So können Benutzer den Kontext beibehalten, und es entsteht Kontinuität zwischen den Ansichten.</span><span class="sxs-lookup"><span data-stu-id="ee397-107">This helps the user maintain their context and provides continuity between the views.</span></span>
<span data-ttu-id="ee397-108">In einer verbundenen Animation scheint ein Element zwischen zwei Ansichten weiterzubestehen, während sich der UI-Inhalt ändert. Dabei fliegt das Element von seinem Standort in der Quellansicht über den Bildschirm zu seinem Ziel in der neuen Ansicht herüber.</span><span class="sxs-lookup"><span data-stu-id="ee397-108">In a connected animation, an element appears to “continue” between two views during a change in UI content, flying across the screen from its location in the source view to its destination in the new view.</span></span> <span data-ttu-id="ee397-109">Dadurch wird der gemeinsame Inhalt zwischen den beiden Ansichten unterstrichen, und es entsteht ein schöner, dynamischer Effekt als Teil eines Übergangs.</span><span class="sxs-lookup"><span data-stu-id="ee397-109">This emphasizes the common content in between the views and creates a beautiful and dynamic effect as part of a transition.</span></span>

## <a name="see-it-in-action"></a><span data-ttu-id="ee397-110">Sehen Sie es in Aktion</span><span class="sxs-lookup"><span data-stu-id="ee397-110">See it in action</span></span>

<span data-ttu-id="ee397-111">In diesem kurzen Video verwendet eine App eine verbundene Animation, um ein Elementbild zu animieren, wenn es als Teil der Überschrift der nächsten Seite weiterbesteht.</span><span class="sxs-lookup"><span data-stu-id="ee397-111">In this short video, an app uses a connected animation to animate an item image as it “continues” to become part of the header of the next page.</span></span> <span data-ttu-id="ee397-112">Dieser Effekt trägt dazu bei, Benutzerkontext beim Übergang beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="ee397-112">The effect helps maintain user context across the transition.</span></span>

![UI-Beispiel für kontinuierliche Bewegung](images/continuous3.gif)

<!-- 
<iframe width=640 height=360 src='https://microsoft.sharepoint.com/portals/hub/_layouts/15/VideoEmbedHost.aspx?chId=552c725c%2De353%2D4118%2Dbd2b%2Dc2d0584c9848&amp;vId=b2daa5ee%2Dbe15%2D4503%2Db541%2D1328a6587c36&amp;width=640&amp;height=360&amp;autoPlay=false&amp;showInfo=true' allowfullscreen></iframe>
-->

## <a name="video-summary"></a><span data-ttu-id="ee397-114">Video-Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="ee397-114">Video summary</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev005/player]

## <a name="connected-animation-and-the-fluent-design-system"></a><span data-ttu-id="ee397-115">Verbundene Animationen und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="ee397-115">Connected animation and the Fluent Design System</span></span>

 <span data-ttu-id="ee397-116">Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten.</span><span class="sxs-lookup"><span data-stu-id="ee397-116">The Fluent Design System helps you create modern, bold UI that incorporates light, depth, motion, material, and scale.</span></span> <span data-ttu-id="ee397-117">Verbundene Animation ist eine Komponente des Fluent Design-Systems, die Bewegung in Ihre App bringt.</span><span class="sxs-lookup"><span data-stu-id="ee397-117">Connected animation is a Fluent Design System component that adds motion to your app.</span></span> <span data-ttu-id="ee397-118">Weitere Informationen finden Sie in der [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).</span><span class="sxs-lookup"><span data-stu-id="ee397-118">To learn more, see the [Fluent Design for UWP overview](../fluent-design-system/index.md).</span></span>

## <a name="why-connected-animation"></a><span data-ttu-id="ee397-119">Warum eine verbundene Animation?</span><span class="sxs-lookup"><span data-stu-id="ee397-119">Why connected animation?</span></span>

<span data-ttu-id="ee397-120">Beim Navigieren zwischen Seiten ist es wichtig, dass der Benutzer versteht, welcher neue Inhalt nach der Navigation dargestellt wird und in welcher Beziehung dieser zu seiner Absicht beim Navigieren steht.</span><span class="sxs-lookup"><span data-stu-id="ee397-120">When navigating between pages, it’s important for the user to understand what new content is being presented after the navigation and how it relates to their intent when navigating.</span></span> <span data-ttu-id="ee397-121">Verbundene Animationen bieten eine leistungsstarke visuelle Metapher, die die Beziehung zwischen zwei Ansichten hervorhebt, indem sie den Fokus des Benutzers auf den gemeinsamen Inhalt zwischen diesen beiden lenkt.</span><span class="sxs-lookup"><span data-stu-id="ee397-121">Connected animations provide a powerful visual metaphor that emphasizes the relationship between two views by drawing the user’s focus to the content shared between them.</span></span> <span data-ttu-id="ee397-122">Darüber hinaus fügen verbundene Animationen der Seitennavigation visuelle Spannung und einen Feinschliff hinzu, die dazu beitragen können, dass sich die Bewegungsgestaltung Ihrer App von anderen unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="ee397-122">Additionally, connected animations add visual interest and polish to page navigation that can help differentiate the motion design of your app.</span></span>

## <a name="when-to-use-connected-animation"></a><span data-ttu-id="ee397-123">Verwendungsszenarien für verbundene Animationen</span><span class="sxs-lookup"><span data-stu-id="ee397-123">When to use connected animation</span></span>

<span data-ttu-id="ee397-124">Verbundene Animationen werden in der Regel bei einem Seitenwechsel verwendet, sie können jedoch immer verwendet werden, wenn Sie Inhalt in einer UI ändern und möchten, dass der Benutzerkontext beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="ee397-124">Connected animations are generally used when changing pages, though they can be applied to any experience where you are changing content in a UI and want the user to maintain context.</span></span> <span data-ttu-id="ee397-125">Sie sollten es in Betracht ziehen, eine verbundene Animation anstelle eines [Drills in einem Navigationsübergangs](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.animation.navigationthemetransition.aspx) zu verwenden, wenn die Quell- und die Zielansicht ein gemeinsames Bild oder ein anderes gemeinsames UI-Element aufweisen.</span><span class="sxs-lookup"><span data-stu-id="ee397-125">You should consider using a connected animation instead of a [drill in navigation transition](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.animation.navigationthemetransition.aspx) whenever there is an image or other piece of UI shared between the source and destination views.</span></span>

## <a name="how-to-implement"></a><span data-ttu-id="ee397-126">Implementierung</span><span class="sxs-lookup"><span data-stu-id="ee397-126">How to implement</span></span>

<span data-ttu-id="ee397-127">Das Einrichten einer verbundenen Animation besteht aus zwei Schritten:</span><span class="sxs-lookup"><span data-stu-id="ee397-127">Setting up a connected animation involves two steps:</span></span>

1.  <span data-ttu-id="ee397-128">Dem *Vorbereiten* eines Animationsobjekts auf der Quellseite, wodurch dem System angezeigt wird, dass das Quellelement Teil der verbundenen Animation ist</span><span class="sxs-lookup"><span data-stu-id="ee397-128">*Prepare* an animation object on the source page, which indicates to the system that the source element will participate in the connected animation</span></span> 
2.  <span data-ttu-id="ee397-129">Dem *Starten* der Animation auf der Zielseite, wobei ein Verweis auf das Zielelement übergeben wird</span><span class="sxs-lookup"><span data-stu-id="ee397-129">*Start* the animation on the destination page, passing a reference to the destination element</span></span>

<span data-ttu-id="ee397-130">Zwischen diesen beiden Schritten wird das Quellelement eingefroren über anderen UI-Elementen in der App angezeigt, sodass sich gleichzeitig weitere Übergangsanimationen ausführen lassen.</span><span class="sxs-lookup"><span data-stu-id="ee397-130">In between the two steps, the source element will appear frozen above other UI in the app, allowing you to perform any other transition animations simultaneously.</span></span> <span data-ttu-id="ee397-131">Aus diesem Grund sollten nicht Sie länger als ~250Millisekunden zwischen den beiden Schritten warten, da die Anzeige des Quellelements stören kann.</span><span class="sxs-lookup"><span data-stu-id="ee397-131">For this reason, you shouldn’t wait more than ~250 milliseconds in between the two steps since the presence of the source element may become distracting.</span></span> <span data-ttu-id="ee397-132">Wenn Sie eine Animation vorbereiten und diese nicht innerhalb von drei Sekunden starten, wird sie vom System gelöscht und alle folgenden Aufrufe von **TryStart** schlagen fehl.</span><span class="sxs-lookup"><span data-stu-id="ee397-132">If you prepare an animation and do not start it within three seconds, the system will dispose of the animation and any subsequent calls to **TryStart** will fail.</span></span>

<span data-ttu-id="ee397-133">Zugriff auf die aktuelle ConnectedAnimationService-Instanz erhalten Sie, indem Sie **ConnectedAnimationService.GetForCurrentView** aufrufen.</span><span class="sxs-lookup"><span data-stu-id="ee397-133">You can get access to the current ConnectedAnimationService instance by calling **ConnectedAnimationService.GetForCurrentView**.</span></span> <span data-ttu-id="ee397-134">Rufen Sie zum Vorbereiten einer Animation **PrepareToAnimate** in dieser Instanz auf, um einen Verweis auf einen eindeutigen Schlüssel und das UI-Element zu übergeben, das Sie für den Übergang verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="ee397-134">To prepare an animation, call **PrepareToAnimate** on this instance, passing a reference to a unique key and the UI element you want to use in the transition.</span></span> <span data-ttu-id="ee397-135">Mithilfe des eindeutigen Schlüssels können Sie die Animation später abrufen, z.B. auf einer anderen Seite.</span><span class="sxs-lookup"><span data-stu-id="ee397-135">The unique key allows you to retrieve the animation later, for example on a different page.</span></span>

```csharp
ConnectedAnimationService.GetForCurrentView().PrepareToAnimate("image", SourceImage);
```

<span data-ttu-id="ee397-136">Rufen Sie zum Starten der Animation **ConnectedAnimation.TryStart** auf.</span><span class="sxs-lookup"><span data-stu-id="ee397-136">To start the animation, call **ConnectedAnimation.TryStart**.</span></span> <span data-ttu-id="ee397-137">Sie können die richtige Animationsinstanz abrufen, indem Sie mit dem eindeutigen Schlüssel, den Sie beim Erstellen der Animation angegeben haben, **ConnectedAnimationService.GetAnimation** aufrufen.</span><span class="sxs-lookup"><span data-stu-id="ee397-137">You can retrieve the right animation instance by calling **ConnectedAnimationService.GetAnimation** with the unique key you provided when creating the animation.</span></span>

```csharp
ConnectedAnimation imageAnimation = 
    ConnectedAnimationService.GetForCurrentView().GetAnimation("image");
if (imageAnimation != null)
{
    imageAnimation.TryStart(DestinationImage);
}
```

<span data-ttu-id="ee397-138">Es folgt ein vollständiges Beispiel für die Verwendung von ConnectedAnimationService zum Erstellen eines Übergangs zwischen zwei Seiten.</span><span class="sxs-lookup"><span data-stu-id="ee397-138">Here is a full example of using ConnectedAnimationService to create a transition between two pages.</span></span>

*<span data-ttu-id="ee397-139">SourcePage.xaml</span><span class="sxs-lookup"><span data-stu-id="ee397-139">SourcePage.xaml</span></span>*

```xaml
<Image x:Name="SourceImage"
       Width="200"
       Height="200"
       Stretch="Fill"
       Source="Assets/StoreLogo.png" />
```

*<span data-ttu-id="ee397-140">SourcePage.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="ee397-140">SourcePage.xaml.cs</span></span>*

```csharp
private void NavigateToDestinationPage()
{
    ConnectedAnimationService.GetForCurrentView().PrepareToAnimate("image", SourceImage);
    Frame.Navigate(typeof(DestinationPage));
}
```

*<span data-ttu-id="ee397-141">DestinationPage.xaml</span><span class="sxs-lookup"><span data-stu-id="ee397-141">DestinationPage.xaml</span></span>*

```xaml
<Image x:Name="DestinationImage"
       Width="400"
       Height="400"
       Stretch="Fill"
       Source="Assets/StoreLogo.png" />
```

*<span data-ttu-id="ee397-142">DestinationPage.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="ee397-142">DestinationPage.xaml.cs</span></span>*

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

## <a name="connected-animation-in-list-and-grid-experiences"></a><span data-ttu-id="ee397-143">Verbundene Animationen in Listen- und Rasterumgebungen</span><span class="sxs-lookup"><span data-stu-id="ee397-143">Connected animation in list and grid experiences</span></span>

<span data-ttu-id="ee397-144">Sie werden wahrscheinlich häufig verbundene Animationen aus einem Listen- oder Rastersteuerelement erstellen wollen.</span><span class="sxs-lookup"><span data-stu-id="ee397-144">Often, you will want to create a connected animation from or to a list or grid control.</span></span> <span data-ttu-id="ee397-145">Um diesen Prozess zu vereinfachen, können Sie zwei neue Methoden von **ListView** und **GridView** verwenden: **PrepareConnectedAnimation** und **TryStartConnectedAnimationAsync**.</span><span class="sxs-lookup"><span data-stu-id="ee397-145">You can use two new methods of **ListView** and **GridView**, **PrepareConnectedAnimation** and **TryStartConnectedAnimationAsync**, to simplify this process.</span></span>
<span data-ttu-id="ee397-146">Nehmen wir beispielsweise an, Sie haben eine **ListView**, die ein Element mit dem Namen „PortraitEllipse” in der Datenvorlage enthält.</span><span class="sxs-lookup"><span data-stu-id="ee397-146">For example, say you have a **ListView** that contains an element with the name "PortraitEllipse" in its data template.</span></span>

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

<span data-ttu-id="ee397-147">Rufen Sie zum Vorbereiten einer verbundenen Animation mit der Ellipse für ein bestimmtes Element die Methode **PrepareConnectedAnimation** mit einem eindeutigen Schlüssel, dem Element und dem Namen „PortraitEllipse” auf.</span><span class="sxs-lookup"><span data-stu-id="ee397-147">To prepare a connected animation with the ellipse corresponding to a given list item, call the **PrepareConnectedAnimation** method with a unique key, the item, and the name “PortraitEllipse”.</span></span>

```csharp
void PrepareAnimationWithItem(ContactsItem item)
{
     ContactsListView.PrepareConnectedAnimation("portrait", item, "PortraitEllipse");
}
```

<span data-ttu-id="ee397-148">Alternativ können Sie **TryStartConnectedAnimationAsync** verwenden, um eine Animation mit diesem Element als Ziel zu starten, beispielsweise beim Zurücknavigieren aus einer Detailansicht.</span><span class="sxs-lookup"><span data-stu-id="ee397-148">Alternatively, to start an animation with this element as the destination, for example when navigating back from a detail view, use **TryStartConnectedAnimationAsync**.</span></span> <span data-ttu-id="ee397-149">Wenn Sie die Datenquelle für die **ListView** gerade geladen haben, wartet **TryStartConnectedAnimationAsync** mit dem Start der Animation, bis der entsprechende Elementcontainer erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="ee397-149">If you have just loaded the data source for the **ListView**, **TryStartConnectedAnimationAsync** will wait to start the animation until the corresponding item container has been created.</span></span>

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

## <a name="coordinated-animation"></a><span data-ttu-id="ee397-150">Koordinierte Animation</span><span class="sxs-lookup"><span data-stu-id="ee397-150">Coordinated animation</span></span>

![Koordinierte Animation](images/connected-animations/coordinated_example.gif)

<!--
<iframe width=640 height=360 src='https://microsoft.sharepoint.com/portals/hub/_layouts/15/VideoEmbedHost.aspx?chId=552c725c%2De353%2D4118%2Dbd2b%2Dc2d0584c9848&amp;vId=9066bbbe%2Dcf58%2D4ab4%2Db274%2D595616f5d0a0&amp;width=640&amp;height=360&amp;autoPlay=false&amp;showInfo=true' allowfullscreen></iframe>
-->

<span data-ttu-id="ee397-152">Eine *koordinierte Animation* ist eine besondere Art von Eingangsanimation, bei der ein Element zusammen mit dem verbundenen Animationsziel angezeigt wird. Dabei wird es zusammen mit dem verbundenen Animationselement animiert, wenn es sich über den Bildschirm bewegt.</span><span class="sxs-lookup"><span data-stu-id="ee397-152">A *coordinated animation* is a special type of entrance animation where an element will appear alongside the connected animation target, animating in tandem with the connected animation element as it moves across the screen.</span></span> <span data-ttu-id="ee397-153">Koordinierte Animationen können einem Übergang weitere visuelle Spannung hinzufügen und die Aufmerksamkeit des Benutzers auf den Kontext lenken, den die Quell- und die Zielansicht teilen.</span><span class="sxs-lookup"><span data-stu-id="ee397-153">Coordinated animations can add more visual interest to a transition and further draw the user’s attention to the context that is shared between the source and destination views.</span></span> <span data-ttu-id="ee397-154">In diesen Bildern wird die Beschriftungs-UI für das Element mithilfe einer koordinierten Animation animiert.</span><span class="sxs-lookup"><span data-stu-id="ee397-154">In these images, the caption UI for the item is animating using a coordinated animation.</span></span>

<span data-ttu-id="ee397-155">Verwenden Sie die Überladung von **TryStart** mit zwei Parametern, um koordinierte Elemente zu einer verbundenen Animation hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ee397-155">Use the two-parameter overload of **TryStart** to add coordinated elements to a connected animation.</span></span> <span data-ttu-id="ee397-156">Dieses Beispiel zeigt eine koordinierte Animation von einem Rasterlayout mit dem Namen „DescriptionRoot”, das zusammen mit einem verbundenen Animationselement mit dem Namen „CoverImage” gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="ee397-156">This example demonstrates a coordinated animation of a Grid layout named “DescriptionRoot” that will enter in tandem with a connected animation element named “CoverImage”.</span></span>

*<span data-ttu-id="ee397-157">DestinationPage.xaml</span><span class="sxs-lookup"><span data-stu-id="ee397-157">DestinationPage.xaml</span></span>*

```xaml
<Grid>
    <Image x:Name="CoverImage" />
    <Grid x:Name="DescriptionRoot" />
</Grid>
```

*<span data-ttu-id="ee397-158">DestinationPage.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="ee397-158">DestinationPage.xaml.cs</span></span>*

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

## <a name="dos-and-donts"></a><span data-ttu-id="ee397-159">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="ee397-159">Do’s and don’ts</span></span>

- <span data-ttu-id="ee397-160">Verwenden Sie eine verbundene Animation bei Seitenübergängen, bei denen ein Element zwischen der Quell- und der Zielseite geteilt wird.</span><span class="sxs-lookup"><span data-stu-id="ee397-160">Use a connected animation in page transitions where an element is shared between the source and destination pages.</span></span>
- <span data-ttu-id="ee397-161">Warten Sie zwischen dem Vorbereiten und dem Starten einer verbundenen Animation nicht auf Netzwerkanfragen oder andere zeitaufwendige asynchrone Vorgänge.</span><span class="sxs-lookup"><span data-stu-id="ee397-161">Don’t wait on network requests or other long-running asynchronous operations in between preparing and starting a connected animation.</span></span> <span data-ttu-id="ee397-162">Möglicherweise müssen Sie die erforderlichen Informationen laden, um den Übergang vorab auszuführen, oder ein Platzhalterbild mit niedriger Auflösung verwenden, während ein Bild mit hoher Auflösung in der Zielansicht geladen wird.</span><span class="sxs-lookup"><span data-stu-id="ee397-162">You may need to pre-load the necessary information to run the transition ahead of time, or use a low-resolution placeholder image while a high-resolution image loads in the destination view.</span></span>
- <span data-ttu-id="ee397-163">Verwenden Sie [SuppressNavigationTransitionInfo](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.media.animation.suppressnavigationtransitioninfo), um eine Übergangsanimation in einem **Frame** bei Verwendung von **ConnectedAnimationService** zu verhindern, da verbundene Animationen nicht gleichzeitig mit den Standard-Navigationsübergängen verwendet werden sollten.</span><span class="sxs-lookup"><span data-stu-id="ee397-163">Use [SuppressNavigationTransitionInfo](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.media.animation.suppressnavigationtransitioninfo) to prevent a transition animation in a **Frame** if you are using **ConnectedAnimationService**, since connected animations aren’t meant to be used simultaneously with the default navigation transitions.</span></span> <span data-ttu-id="ee397-164">Weitere Informationen zur Verwendung von Navigationsübergängen finden Sie unter [NavigationThemeTransition](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.animation.navigationthemetransition.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee397-164">See [NavigationThemeTransition](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.animation.navigationthemetransition.aspx) for more info on how to use navigation transitions.</span></span>


## <a name="download-the-code-samples"></a><span data-ttu-id="ee397-165">Codebeispiele herunterladen</span><span class="sxs-lookup"><span data-stu-id="ee397-165">Download the code samples</span></span>

<span data-ttu-id="ee397-166">Ein [Beispiel für eine verbundene Animation](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2014393/ConnectedAnimationSample) finden Sie in der [WindowsUIDevLabs](https://github.com/Microsoft/WindowsUIDevLabs)-Beispielgalerie.</span><span class="sxs-lookup"><span data-stu-id="ee397-166">See the [Connected Animation sample](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2014393/ConnectedAnimationSample) in the [WindowsUIDevLabs](https://github.com/Microsoft/WindowsUIDevLabs) sample gallery.</span></span>

## <a name="related-articles"></a><span data-ttu-id="ee397-167">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="ee397-167">Related articles</span></span>

- [<span data-ttu-id="ee397-168">ConnectedAnimation</span><span class="sxs-lookup"><span data-stu-id="ee397-168">ConnectedAnimation</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.animation.connectedanimation)
- [<span data-ttu-id="ee397-169">ConnectedAnimationService</span><span class="sxs-lookup"><span data-stu-id="ee397-169">ConnectedAnimationService</span></span>](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.media.animation.connectedanimation.aspx)
- [<span data-ttu-id="ee397-170">NavigationThemeTransition</span><span class="sxs-lookup"><span data-stu-id="ee397-170">NavigationThemeTransition</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.animation.navigationthemetransition.aspx)
