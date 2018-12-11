---
Description: Dialogs and flyouts display transient UI elements that appear when the user requests them or when something happens that requires notification or approval.
title: Flyout-Steuerelementen
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: ad6affd9-a3c0-481f-a237-9a1ecd561be8
pm-contact: yulikl
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 8ce3222ed13cf82a9f235a592b5830ab96384664
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8899175"
---
# <a name="flyouts"></a><span data-ttu-id="7d021-103">Flyouts</span><span class="sxs-lookup"><span data-stu-id="7d021-103">Flyouts</span></span>

<span data-ttu-id="7d021-104">Ein Flyout ist ein einfach ausblendbarer Container, der beliebige UI als Inhalt anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="7d021-104">A flyout is a light dismiss container that can show arbitrary UI as its content.</span></span> <span data-ttu-id="7d021-105">Flyouts können andere Flyouts oder Kontextmenüs enthalten, um eine geschachtelte Umgebung zu kreieren.</span><span class="sxs-lookup"><span data-stu-id="7d021-105">Flyouts can contain other flyouts or context menus to create a nested experience.</span></span>

![Kontextmenü geschachtelt in einem Flyout](../images/flyout-nested.png)

> <span data-ttu-id="7d021-107">**Wichtige APIs**: [Flyout-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Flyout)</span><span class="sxs-lookup"><span data-stu-id="7d021-107">**Important APIs**: [Flyout class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Flyout)</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="7d021-108">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="7d021-108">Is this the right control?</span></span>

* <span data-ttu-id="7d021-109">Verwenden Sie Flyouts nicht anstelle von [QuickInfos](../tooltips.md) oder [Kontextmenüs](../menus.md).</span><span class="sxs-lookup"><span data-stu-id="7d021-109">Don't use a flyout instead of [tooltip](../tooltips.md) or [context menu](../menus.md).</span></span> <span data-ttu-id="7d021-110">Verwenden Sie QuickInfos, um kurze Beschreibungen anzuzeigen, die nach einer festgelegten Zeit ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="7d021-110">Use a tooltip to show a short description that hides after a specified time.</span></span> <span data-ttu-id="7d021-111">Verwenden Sie ein Kontextmenü für kontextbezogene Aktionen im Zusammenhang mit UI-Elementen (beispielsweise Kopieren und Einfügen).</span><span class="sxs-lookup"><span data-stu-id="7d021-111">Use a context menu for contextual actions related to a UI element, such as copy and paste.</span></span>

<span data-ttu-id="7d021-112">Empfehlungen dazu, wann Sie ein Flyout verwendet werden und wann ein Dialogfeld (ähnlich wie Steuerelement), finden Sie unter [Dialogfelder und Flyouts](index.md).</span><span class="sxs-lookup"><span data-stu-id="7d021-112">For recommendations on when to use a flyout vs. when to use a dialog (a similar control), see [Dialogs and flyouts](index.md).</span></span> 

## <a name="examples"></a><span data-ttu-id="7d021-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="7d021-113">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="7d021-114">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="7d021-114">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="../images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="7d021-115">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um die App zu öffnen und <a href="xamlcontrolsgallery:/item/ContentDialog">ContentDialog</a> oder <a href="xamlcontrolsgallery:/item/Flyout">Flyout</a> in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="7d021-115">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to open the app and see the <a href="xamlcontrolsgallery:/item/ContentDialog">ContentDialog</a> or <a href="xamlcontrolsgallery:/item/Flyout">Flyout</a> in action.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="7d021-116">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="7d021-116">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="7d021-117">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="7d021-117">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

##  <a name="how-to-create-a-flyout"></a><span data-ttu-id="7d021-118">So erstellen Sie ein flyout</span><span class="sxs-lookup"><span data-stu-id="7d021-118">How to create a flyout</span></span>


<span data-ttu-id="7d021-119">Flyouts sind an bestimmte Steuerelemente angefügt.</span><span class="sxs-lookup"><span data-stu-id="7d021-119">Flyouts are attached to specific controls.</span></span> <span data-ttu-id="7d021-120">Sie können mit der [Placement](/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase.Placement)-Eigenschaft angeben, wo das Flyout angezeigt werden soll: oben, links, unten, rechts oder als Vollbild.</span><span class="sxs-lookup"><span data-stu-id="7d021-120">You can use the [Placement](/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase.Placement) property to specify where a flyout appears: Top, Left, Bottom, Right, or Full.</span></span> <span data-ttu-id="7d021-121">Wenn Sie den [vollständigen Platzierungsmodus](/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutPlacementMode) auswählen, streckt die App das Flyout und zentriert es innerhalb des App-Fensters.</span><span class="sxs-lookup"><span data-stu-id="7d021-121">If you select the [Full placement mode](/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutPlacementMode), the app stretches the flyout and centers it inside the app window.</span></span> <span data-ttu-id="7d021-122">Einige Steuerelemente wie z.B. [Schaltflächen](/uwp/api/Windows.UI.Xaml.Controls.Button), verfügen über eine [Flyout](/uwp/api/Windows.UI.Xaml.Controls.Button.Flyout)-Eigenschaft, mit der Sie ein Flyout oder [Kontextmenü](../menus.md) zuordnen können.</span><span class="sxs-lookup"><span data-stu-id="7d021-122">Some controls, such as [Button](/uwp/api/Windows.UI.Xaml.Controls.Button), provide a [Flyout](/uwp/api/Windows.UI.Xaml.Controls.Button.Flyout) property that you can use to associate a flyout or [context menu](../menus.md).</span></span>

<span data-ttu-id="7d021-123">In diesem Beispiel wird ein einfaches Flyout erstellt, das Text anzeigt, wenn die Schaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="7d021-123">This example creates a simple flyout that displays some text when the button is pressed.</span></span>
````xaml
<Button Content="Click me">
  <Button.Flyout>
     <Flyout>
        <TextBlock Text="This is a flyout!"/>
     </Flyout>
  </Button.Flyout>
</Button>
````

<span data-ttu-id="7d021-124">Wenn das Steuerelement nicht über eine Flyout-Eigenschaft verfügt, können Sie stattdessen die angefügte Eigenschaft [FlyoutBase.AttachedFlyout](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.AttachedFlyoutProperty) verwenden.</span><span class="sxs-lookup"><span data-stu-id="7d021-124">If the control doesn't have a flyout property, you can use the [FlyoutBase.AttachedFlyout](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.AttachedFlyoutProperty) attached property instead.</span></span> <span data-ttu-id="7d021-125">In diesem Fall müssen Sie zudem die [FlyoutBase.ShowAttachedFlyout](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase#Windows_UI_Xaml_Controls_Primitives_FlyoutBase_ShowAttachedFlyout_Windows_UI_Xaml_FrameworkElement_)-Methode aufrufen, um das Flyout anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7d021-125">When you do this, you also need to call the [FlyoutBase.ShowAttachedFlyout](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase#Windows_UI_Xaml_Controls_Primitives_FlyoutBase_ShowAttachedFlyout_Windows_UI_Xaml_FrameworkElement_) method to show the flyout.</span></span>

<span data-ttu-id="7d021-126">In diesem Beispiel wird einem Bild ein einfaches Flyout hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7d021-126">This example adds a simple flyout to an image.</span></span> <span data-ttu-id="7d021-127">Wenn der Benutzer auf das Bild tippt, zeigt die App das Flyout an.</span><span class="sxs-lookup"><span data-stu-id="7d021-127">When the user taps the image, the app shows the flyout.</span></span>

````xaml
<Image Source="Assets/cliff.jpg" Width="50" Height="50"
  Margin="10" Tapped="Image_Tapped">
  <FlyoutBase.AttachedFlyout>
    <Flyout>
      <TextBlock Text="This is some text in a flyout."  />
    </Flyout>        
  </FlyoutBase.AttachedFlyout>
</Image>
````

````csharp
private void Image_Tapped(object sender, TappedRoutedEventArgs e)
{
    FlyoutBase.ShowAttachedFlyout((FrameworkElement)sender);
}
````

<span data-ttu-id="7d021-128">In den vorherigen Beispielen wurden die Flyouts inline definiert.</span><span class="sxs-lookup"><span data-stu-id="7d021-128">The previous examples defined their flyouts inline.</span></span> <span data-ttu-id="7d021-129">Sie können ein Flyout auch als statische Ressource definieren und sie dann mit mehreren Elementen verwenden.</span><span class="sxs-lookup"><span data-stu-id="7d021-129">You can also define a flyout as a static resource and then use it with multiple elements.</span></span> <span data-ttu-id="7d021-130">In diesem Beispiel wird ein komplizierteres Flyout erstellt, mit dem eine größere Version eines Bilds angezeigt wird, wenn auf die Miniaturansicht getippt wird.</span><span class="sxs-lookup"><span data-stu-id="7d021-130">This example creates a more complicated flyout that displays a larger version of an image when its thumbnail is tapped.</span></span>

````xaml
<!-- Declare the shared flyout as a resource. -->
<Page.Resources>
    <Flyout x:Key="ImagePreviewFlyout" Placement="Right">
        <!-- The flyout's DataContext must be the Image Source
             of the image the flyout is attached to. -->
        <Image Source="{Binding Path=Source}"
            MaxHeight="400" MaxWidth="400" Stretch="Uniform"/>
    </Flyout>
</Page.Resources>
````

````xaml
<!-- Assign the flyout to each element that shares it. -->
<StackPanel>
    <Image Source="Assets/cliff.jpg" Width="50" Height="50"
           Margin="10" Tapped="Image_Tapped"
           FlyoutBase.AttachedFlyout="{StaticResource ImagePreviewFlyout}"
           DataContext="{Binding RelativeSource={RelativeSource Mode=Self}}"/>
    <Image Source="Assets/grapes.jpg" Width="50" Height="50"
           Margin="10" Tapped="Image_Tapped"
           FlyoutBase.AttachedFlyout="{StaticResource ImagePreviewFlyout}"
           DataContext="{Binding RelativeSource={RelativeSource Mode=Self}}"/>
    <Image Source="Assets/rainier.jpg" Width="50" Height="50"
           Margin="10" Tapped="Image_Tapped"
           FlyoutBase.AttachedFlyout="{StaticResource ImagePreviewFlyout}"
           DataContext="{Binding RelativeSource={RelativeSource Mode=Self}}"/>
</StackPanel>
````

````csharp
private void Image_Tapped(object sender, TappedRoutedEventArgs e)
{
    FlyoutBase.ShowAttachedFlyout((FrameworkElement)sender);  
}
````

## <a name="style-a-flyout"></a><span data-ttu-id="7d021-131">Gestalten eines Flyouts</span><span class="sxs-lookup"><span data-stu-id="7d021-131">Style a flyout</span></span>
<span data-ttu-id="7d021-132">Um ein Flyout zu formatieren, ändern Sie den [FlyoutPresenterStyle](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Flyout.FlyoutPresenterStyle).</span><span class="sxs-lookup"><span data-stu-id="7d021-132">To style a Flyout, modify its [FlyoutPresenterStyle](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Flyout.FlyoutPresenterStyle).</span></span> <span data-ttu-id="7d021-133">In diesem Beispiel wird ein Absatz mit Textumbruch dargestellt, was den Textblock für Bildschirmleseprogramme zugänglich gemacht.</span><span class="sxs-lookup"><span data-stu-id="7d021-133">This example shows a paragraph of wrapping text and makes the text block accessible to a screen reader.</span></span>

![Zugängliches Flyout mit Textumbruch](../images/flyout-wrapping-text.png)

````xaml
<Flyout>
  <Flyout.FlyoutPresenterStyle>
    <Style TargetType="FlyoutPresenter">
      <Setter Property="ScrollViewer.HorizontalScrollMode"
          Value="Disabled"/>
      <Setter Property="ScrollViewer.HorizontalScrollBarVisibility" Value="Disabled"/>
      <Setter Property="IsTabStop" Value="True"/>
      <Setter Property="TabNavigation" Value="Cycle"/>
    </Style>
  </Flyout.FlyoutPresenterStyle>
  <TextBlock Style="{StaticResource BodyTextBlockStyle}" Text="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."/>
</Flyout>
````

## <a name="styling-flyouts-for-10-foot-experiences"></a><span data-ttu-id="7d021-135">Formatieren von Flyouts für 10-Fuß-Umgebungen</span><span class="sxs-lookup"><span data-stu-id="7d021-135">Styling flyouts for 10-foot experiences</span></span>

<span data-ttu-id="7d021-136">Einfach ausblendbare Steuerelemente wie Flyouts erhalten den Tastatur- bzw. Gamepad-Fokus, bis sie nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7d021-136">Light dismiss controls like flyout trap keyboard and gamepad focus inside their transient UI until dismissed.</span></span> <span data-ttu-id="7d021-137">Um dieses Verhalten optisch zu kennzeichnen, werden diese einfach ausblendbaren Steuerelemente auf der Xbox als Überlagerung gezeichnet, wobei der Kontrast und die Helligkeit bzw. Sichtbarkeit der umgebenden Benutzeroberfläche reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="7d021-137">To provide a visual cue for this behavior, light dismiss controls on Xbox draw an overlay that dims the contrast and visibility of out of scope UI.</span></span> <span data-ttu-id="7d021-138">Dieses Verhalten kann mit der Eigenschaft [`LightDismissOverlayMode`](/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase.LightDismissOverlayMode) geändert werden.</span><span class="sxs-lookup"><span data-stu-id="7d021-138">This behavior can be modified with the [`LightDismissOverlayMode`](/uwp/api/Windows.UI.Xaml.Controls.Primitives.FlyoutBase.LightDismissOverlayMode) property.</span></span> <span data-ttu-id="7d021-139">Standardmäßig erhalten Flyouts auf der Xbox (jedoch nicht auf anderen Gerätefamilien) die einfach ausblendbare Überlagerung. Apps können jedoch durchsetzen, dass die Überlagerung stets **An** oder stets **Aus** ist.</span><span class="sxs-lookup"><span data-stu-id="7d021-139">By default, flyouts will draw the light dismiss overlay on Xbox but not other device families, but apps can choose to force the overlay to be always **On** or always **Off**.</span></span>

![Flyout mit Abblend-Überlagerung](../images/flyout-smoke.png)

```xaml
<MenuFlyout LightDismissOverlayMode="On">
```

## <a name="light-dismiss-behavior"></a><span data-ttu-id="7d021-141">Verhalten für einfaches Ausblenden</span><span class="sxs-lookup"><span data-stu-id="7d021-141">Light dismiss behavior</span></span>
<span data-ttu-id="7d021-142">Flyouts können schnell mit einer einfachen Ausblend-Aktion geschlossen werden. Dazu zählen:</span><span class="sxs-lookup"><span data-stu-id="7d021-142">Flyouts can be closed with a quick light dismiss action, including</span></span>
-   <span data-ttu-id="7d021-143">Tippen außerhalb des Flyouts</span><span class="sxs-lookup"><span data-stu-id="7d021-143">Tap outside the flyout</span></span>
-   <span data-ttu-id="7d021-144">Drücken der ESC-Taste auf der Tastatur</span><span class="sxs-lookup"><span data-stu-id="7d021-144">Press the Escape keyboard key</span></span>
-   <span data-ttu-id="7d021-145">Drücken der Zurück-Taste des Systems (Hardware oder Software)</span><span class="sxs-lookup"><span data-stu-id="7d021-145">Press the hardware or software system Back button</span></span>
-   <span data-ttu-id="7d021-146">Drücken der B-Taste auf dem Gamepad</span><span class="sxs-lookup"><span data-stu-id="7d021-146">Press the gamepad B button</span></span>

<span data-ttu-id="7d021-147">Wird das Ausblenden durch Tippen vorgenommen, wird die Geste in der Regel absorbiert und nicht an die UI unterhalb weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="7d021-147">When dismissing with a tap, this gesture is typically absorbed and not passed on to the UI underneath.</span></span> <span data-ttu-id="7d021-148">Ist beispielsweise hinter einem geöffneten Flyout eine Schaltfläche sichtbar, wird durch einfaches Antippen durch den Benutzer das Flyout ausgeblendet, ohne jedoch diese Schaltfläche zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="7d021-148">For example, if there’s a button visible behind an open flyout, the user’s first tap dismisses the flyout but does not activate this button.</span></span> <span data-ttu-id="7d021-149">Um die Schaltfläche zu drücken, ist ein weiteres Antippen nötig.</span><span class="sxs-lookup"><span data-stu-id="7d021-149">Pressing the button requires a second tap.</span></span>

<span data-ttu-id="7d021-150">Sie können dieses Verhalten ändern, indem Sie die Schaltfläche als Pass-Through-Eingabeelement für das Flyout gestalten.</span><span class="sxs-lookup"><span data-stu-id="7d021-150">You can change this behavior by designating the button as an input pass-through element for the flyout.</span></span> <span data-ttu-id="7d021-151">Das Flyout wird wie oben beschriebenen durch die einfache Ausblend-Aktion geschlossen, gibt den Antipp-Vorgang aber gleichzeitig an das entsprechende `OverlayInputPassThroughElement` weiter.</span><span class="sxs-lookup"><span data-stu-id="7d021-151">The flyout will close as a result of the light dismiss actions described above and will also pass the tap event to its designated `OverlayInputPassThroughElement`.</span></span> <span data-ttu-id="7d021-152">Erwägen Sie, dieses Verhalten zu übernehmen, um Interaktionen des Benutzers bei ähnlich funktionierenden Elementen zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="7d021-152">Consider adopting this behavior to speed up user interactions on functionally similar items.</span></span> <span data-ttu-id="7d021-153">Wenn Ihre App eine Sammlung von Favoriten beinhaltet und jedes Element der Sammlung ein angefügtes Flyout enthält, kann man davon auszugehen, dass die Benutzer mehrere Flyouts in schneller Abfolge abarbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="7d021-153">If your app has a favorites collection and each item in the collection includes an attached flyout, it's reasonable to expect that users may want to interact with multiple flyouts in rapid succession.</span></span>

[!NOTE] <span data-ttu-id="7d021-154">Achten Sie darauf, kein Überlagerungseingabeelement mit Pass-Through festzulegen, da dies in einer destruktiven Aktion resultiert.</span><span class="sxs-lookup"><span data-stu-id="7d021-154">Be careful not to designate an overlay input pass-through element which results in a destructive action.</span></span> <span data-ttu-id="7d021-155">Die Benutzer sind an diskrete, einfach ausblendbare Aktionen gewöhnt, die die Primär-UI nicht aktivieren.</span><span class="sxs-lookup"><span data-stu-id="7d021-155">Users have become habituated to discreet light dismiss actions which do not activate primary UI.</span></span> <span data-ttu-id="7d021-156">Schließen, Löschen oder ähnlich destruktive Schaltflächen sollten nicht über einfach ausblendbare Elemente aktiviert werden, um unerwartetes und störendes Verhalten zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="7d021-156">Close, Delete or similarly destructive buttons should not activate on light dismiss to avoid unexpected and disruptive behavior.</span></span>

<span data-ttu-id="7d021-157">Im folgenden Beispiel werden alle drei Schaltflächen in der Favoritenleiste durch einfaches Antippen aktiviert.</span><span class="sxs-lookup"><span data-stu-id="7d021-157">In the following example, all three buttons inside FavoritesBar will be activated on the first tap.</span></span>

````xaml
<Page>
    <Page.Resources>
        <Flyout x:Name="TravelFlyout" x:Key="TravelFlyout"
                OverlayInputPassThroughElement="{x:Bind FavoritesBar}">
            <StackPanel>
                <HyperlinkButton Content="Washington Trails Association"/>
                <HyperlinkButton Content="Washington Cascades - Go Northwest! A Travel Guide"/>  
            </StackPanel>
        </Flyout>
    </Page.Resources>

    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <StackPanel x:Name="FavoritesBar" Orientation="Horizontal">
            <HyperlinkButton x:Name="PageLinkBtn">Bing</HyperlinkButton>  
            <Button x:Name="Folder1" Content="Travel" Flyout="{StaticResource TravelFlyout}"/>
            <Button x:Name="Folder2" Content="Entertainment" Click="Folder2_Click"/>
        </StackPanel>
        <ScrollViewer Grid.Row="1">
            <WebView x:Name="WebContent"/>
        </ScrollViewer>
    </Grid>
</Page>
````
````csharp
private void Folder2_Click(object sender, RoutedEventArgs e)
{
     Flyout flyout = new Flyout();
     flyout.OverlayInputPassThroughElement = FavoritesBar;
     ...
     flyout.ShowAt(sender as FrameworkElement);
{
````

## <a name="get-the-sample-code"></a><span data-ttu-id="7d021-158">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="7d021-158">Get the sample code</span></span>

- <span data-ttu-id="7d021-159">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="7d021-159">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="7d021-160">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="7d021-160">Related articles</span></span>
- [<span data-ttu-id="7d021-161">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="7d021-161">Tooltips</span></span>](../tooltips.md)
- [<span data-ttu-id="7d021-162">Menüs und Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="7d021-162">Menus and context menu</span></span>](../menus.md)
- [<span data-ttu-id="7d021-163">Flyout-Klasse</span><span class="sxs-lookup"><span data-stu-id="7d021-163">Flyout class</span></span>](/uwp/api/Windows.UI.Xaml.Controls.Flyout)
- [<span data-ttu-id="7d021-164">ContentDialog-Klasse</span><span class="sxs-lookup"><span data-stu-id="7d021-164">ContentDialog class</span></span>](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog)