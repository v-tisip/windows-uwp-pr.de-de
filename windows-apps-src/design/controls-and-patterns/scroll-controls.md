---
author: muhsinking
Description: Panning and scrolling allows users to reach content that extends beyond the bounds of the screen.
title: Bildlaufanzeige-Steuerelemente
ms.assetid: 1BFF0E81-BF9C-43F7-95F6-EFC6BDD5EC31
label: Scrollbars
template: detail.hbs
ms.author: mukin
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
pm-contact: Abarlow, pagildea
design-contact: ksulliv
dev-contact: regisb
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 983f80c705aba44fe096f9dfa05b71b0cf28f294
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6983875"
---
# <a name="scroll-viewer-controls"></a><span data-ttu-id="d44c7-103">Bildlaufanzeige-Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="d44c7-103">Scroll viewer controls</span></span>



<span data-ttu-id="d44c7-104">Wenn mehr UI-Inhalte anzuzeigen sind, als in einen Bereich passen, verwenden Sie das Bildlaufanzeige-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="d44c7-104">When there is more UI content to show than you can fit in an area, use the scroll viewer control.</span></span>

> <span data-ttu-id="d44c7-105">**Wichtige APIs**: [ScrollViewer-Klasse](https://msdn.microsoft.com/library/windows/apps/br209527), [ScrollBar-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.scrollbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="d44c7-105">**Important APIs**: [ScrollViewer class](https://msdn.microsoft.com/library/windows/apps/br209527), [ScrollBar class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.scrollbar.aspx)</span></span>

<span data-ttu-id="d44c7-106">Mithilfe von Bildlaufanzeigen kann Inhalt über die Grenzen des Anzeigebereichs (sichtbarer Bereich) hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="d44c7-106">Scroll viewers enable content to extend beyond the bounds of the viewport (visible area).</span></span> <span data-ttu-id="d44c7-107">Benutzer können diesen Inhalt durch Bedienen der Bildlaufanzeigenoberfläche über Toucheingabe, Mausrad, Tastatur oder ein Gamepad oder mithilfe des Maus- oder Stiftcursors anzeigen, um mit der Bildlaufleiste der Bildlaufanzeige zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="d44c7-107">Users reach this content by manipulating the scroll viewer surface through touch, mousewheel, keyboard, or a gamepad, or by using the mouse or pen cursor to interact with the scroll viewer's scrollbar.</span></span> <span data-ttu-id="d44c7-108">Diese Abbildungzeigt mehrere Beispiele für Bildlaufanzeige-Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="d44c7-108">This image shows several examples of scroll viewer controls.</span></span>

![Screenshot mit einem standardmäßigen Bildlaufleisten-Steuerelement](images/ScrollBar_Standard.jpg)

<span data-ttu-id="d44c7-110">Abhängig von der Situation verwendet die Bildlaufleiste der Bildlaufanzeige zwei verschiedene Visualisierungen, die in der folgenden Abbildunggezeigt werden: den Verschiebungsindikator (links) und die herkömmliche Bildlaufleiste (rechts).</span><span class="sxs-lookup"><span data-stu-id="d44c7-110">Depending on the situation, the scroll viewer's scrollbar uses two different visualizations, shown in the following illustration: the panning indicator (left) and the traditional scrollbar (right).</span></span>

![Beispiel für standardmäßige Bildlaufleisten- und Verschiebungsindikatoren-Steuerelemente](images/SCROLLBAR.png)

<span data-ttu-id="d44c7-112">Die Bildlaufanzeige erkennt die Eingabemethode des Benutzers und ermittelt damit die anzuzeigende Visualisierung.</span><span class="sxs-lookup"><span data-stu-id="d44c7-112">The scroll viewer is conscious of the user’s input method and uses it to determine which visualization to display.</span></span>

* <span data-ttu-id="d44c7-113">Wenn in einem Bereich ein Bildlauf durchgeführt wird, ohne die Bildlaufleiste direkt zu benutzen, z.B. durch Berühren, wird der Verschiebungsindikator eingeblendet, welcher die aktuelle Bildlaufposition anzeigt.</span><span class="sxs-lookup"><span data-stu-id="d44c7-113">When the region is scrolled without manipulating the scrollbar directly, for example, by touch, the panning indicator appears, displaying the current scroll position.</span></span>
* <span data-ttu-id="d44c7-114">Wenn der Maus- oder Stiftcursor über den Verschiebungsindikator bewegt wird, verwandelt sich dieser in eine herkömmliche Bildlaufleiste.</span><span class="sxs-lookup"><span data-stu-id="d44c7-114">When the mouse or pen cursor moves over the panning indicator, it morphs into the traditional scrollbar.</span></span>  <span data-ttu-id="d44c7-115">Durch Ziehen des Ziehpunkts der Bildlaufleiste wird der Bildlaufbereich verändert.</span><span class="sxs-lookup"><span data-stu-id="d44c7-115">Dragging the scrollbar thumb manipulates the scrolling region.</span></span>

<!--
<div class="microsoft-internal-note">
See complete redlines in [UNI]http://uni/DesignDepot.FrontEnd/#/ProductNav/3378/0/dv/?t=Windows|Controls|ScrollControls&f=RS2
</div>
-->

![Bildlaufleisten in Aktion](images/conscious-scroll.gif)

> [!NOTE]
> <span data-ttu-id="d44c7-117">Wenn die Bildlaufleiste sichtbar ist, überlagert sie mit 16px den Inhalt innerhalb des ScrollViewer.</span><span class="sxs-lookup"><span data-stu-id="d44c7-117">When the scrollbar is visible it is overlaid as 16px on top of the content inside your ScrollViewer.</span></span> <span data-ttu-id="d44c7-118">Für ein gutes Benutzeroberflächendesign sollten Sie sicherstellen, dass durch diese Überlagerung keine interaktiven Inhalte verdeckt werden.</span><span class="sxs-lookup"><span data-stu-id="d44c7-118">In order to ensure good UX design you will want to ensure that no interactive content is obscured by this overlay.</span></span> <span data-ttu-id="d44c7-119">Wenn sich Benutzeroberflächen lieber nicht überlappen sollen, lassen Sie vom Rand des Anzeigebereichs 16px Abstand für die Bildlaufleiste.</span><span class="sxs-lookup"><span data-stu-id="d44c7-119">Additionally if you would prefer not to have UX overlap, leave 16px of padding on the edge of the viewport to allow for the scrollbar.</span></span>

## <a name="examples"></a><span data-ttu-id="d44c7-120">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d44c7-120">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="d44c7-121">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="d44c7-121">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="d44c7-122">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/ScrollViewer">die App zu öffnen und ScrollViewer in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="d44c7-122">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/ScrollViewer">open the app and see the ScrollViewer in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="d44c7-123">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="d44c7-123">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="d44c7-124">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d44c7-124">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="create-a-scroll-viewer"></a><span data-ttu-id="d44c7-125">Erstellen einer Bildlaufanzeige</span><span class="sxs-lookup"><span data-stu-id="d44c7-125">Create a scroll viewer</span></span>

<span data-ttu-id="d44c7-126">Um Ihrer Seite einen vertikalen Bildlauf hinzuzufügen, umschließen Sie den Seiteninhalt in einer Bildlaufanzeige.</span><span class="sxs-lookup"><span data-stu-id="d44c7-126">To add vertical scrolling to your page, wrap the page content in a scroll viewer.</span></span>

```xaml
<Page
    x:Class="App1.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:App1">

    <ScrollViewer>
        <StackPanel>
            <TextBlock Text="My Page Title" Style="{StaticResource TitleTextBlockStyle}"/>
            <!-- more page content -->
        </StackPanel>
    </ScrollViewer>
</Page>
```

<span data-ttu-id="d44c7-127">Dieser XAML-Code veranschaulicht das Einfügen eines Bilds in einer Bildlaufanzeige und das Aktivieren des Zooms.</span><span class="sxs-lookup"><span data-stu-id="d44c7-127">This XAML shows how to place an image in a scroll viewer and enable zooming.</span></span>

```xaml
<ScrollViewer ZoomMode="Enabled" MaxZoomFactor="10"
              HorizontalScrollMode="Enabled" HorizontalScrollBarVisibility="Visible"
              Height="200" Width="200">
    <Image Source="Assets/Logo.png" Height="400" Width="400"/>
</ScrollViewer>
```

## <a name="scrollviewer-in-a-control-template"></a><span data-ttu-id="d44c7-128">ScrollViewer in einer Steuerelementvorlage</span><span class="sxs-lookup"><span data-stu-id="d44c7-128">ScrollViewer in a control template</span></span>

<span data-ttu-id="d44c7-129">Normalerweise ist das ScrollViewer-Steuerelement Teil von anderen Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="d44c7-129">It's typical for a ScrollViewer control to exist as a composite part of other controls.</span></span> <span data-ttu-id="d44c7-130">Eine ScrollViewer-Komponente zeigt zusammen mit der [ScrollContentPresenter](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollcontentpresenter.aspx)-Klasse zur Unterstützung nur dann einen Viewport sowie Bildlaufleisten an, wenn der Layoutbereich des Hoststeuerelements einschränkt wird und kleiner als die Größe des erweiterten Inhalts ist.</span><span class="sxs-lookup"><span data-stu-id="d44c7-130">A ScrollViewer part, along with the [ScrollContentPresenter](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollcontentpresenter.aspx) class for support, will display a viewport along with scrollbars only when the host control's layout space is being constrained smaller than the expanded content size.</span></span> <span data-ttu-id="d44c7-131">Dies ist häufig bei Listen der Fall, daher enthalten [ListView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listview.aspx)- und [GridView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridview.aspx)-Vorlagen immer ScrollViewer.</span><span class="sxs-lookup"><span data-stu-id="d44c7-131">This is often the case for lists, so [ListView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listview.aspx) and [GridView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridview.aspx) templates always include a ScrollViewer.</span></span> <span data-ttu-id="d44c7-132">[TextBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textbox.aspx) und [RichEditBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx) enthalten ebenfalls ScrollViewer in ihren Vorlagen.</span><span class="sxs-lookup"><span data-stu-id="d44c7-132">[TextBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textbox.aspx) and [RichEditBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx) also include a ScrollViewer in their templates.</span></span>

<span data-ttu-id="d44c7-133">Wenn eine **ScrollViewer**-Komponente in einem Steuerelement vorhanden ist, ist im Hoststeuerelement häufig die Ereignisbehandlung für bestimmte Eingabeereignisse und Bearbeitungen integriert, mit denen ein Bildlauf für den Inhalt durchgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="d44c7-133">When a **ScrollViewer** part exists in a control, the host control often has built-in event handling for certain input events and manipulations that enable the content to scroll.</span></span> <span data-ttu-id="d44c7-134">GridView interpretiert z. B. eine Wischbewegung, wodurch für den Inhalt ein horizontaler Bildlauf durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d44c7-134">For example, a GridView interprets a swipe gesture and this causes the content to scroll horizontally.</span></span> <span data-ttu-id="d44c7-135">Die Eingabeereignisse und Manipulationen von Rohdaten, die das Hoststeuerelement empfängt, werden als durch das Steuerelement behandelt betrachtet, und untergeordnete Ereignisse wie [PointerPressed](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.pointerpressed.aspx) werden nicht ausgelöst oder per Bubbling an übergeordnete Container weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="d44c7-135">The input events and raw manipulations that the host control receives are considered handled by the control, and lower-level events such as [PointerPressed](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.pointerpressed.aspx) won't be raised and won't bubble to any parent containers either.</span></span> <span data-ttu-id="d44c7-136">Sie können das integrierte Verhalten des Steuerelements teilweise ändern, indem Sie eine Steuerelementklasse und die virtuellen \*\*On\*\*\*-Methoden für Ereignisse überschreiben oder eine neue Vorlage für das Steuerelement verwenden.</span><span class="sxs-lookup"><span data-stu-id="d44c7-136">You can change some of the built-in control handling by overriding a control class and the **On**\* virtual methods for events, or by retemplating the control.</span></span> <span data-ttu-id="d44c7-137">In beiden Fällen ist es allerdings nicht unkompliziert, das ursprüngliche Standardverhalten zu reproduzieren, das in der Regel vorhanden ist, damit das Steuerelement wie erwartet auf Ereignisse und Eingabeaktionen und -gesten des Benutzers reagiert.</span><span class="sxs-lookup"><span data-stu-id="d44c7-137">But in either case it's not trivial to reproduce the original default behavior, which is typically there so that the control reacts in expected ways to events and to a user's input actions and gestures.</span></span> <span data-ttu-id="d44c7-138">Sie sollten daher genau überlegen, ob das Eingabeereignis wirklich ausgelöst werden soll.</span><span class="sxs-lookup"><span data-stu-id="d44c7-138">So you should consider whether you really need that input event to fire.</span></span> <span data-ttu-id="d44c7-139">Sie sollten überprüfen, ob andere Eingabeereignisse oder Gesten vorhanden sind, die nicht von dem Steuerelement behandelt werden, und diese im Entwurf für die App oder die Steuerelementinteraktion verwenden.</span><span class="sxs-lookup"><span data-stu-id="d44c7-139">You might want to investigate whether there are other input events or gestures that are not being handled by the control, and use those in your app or control interaction design.</span></span>

<span data-ttu-id="d44c7-140">Damit Steuerelemente, die einen ScrollViewer enthalten, einige Verhaltensweisen und Eigenschaften innerhalb der ScrollViewer-Komponente steuern können, definiert ScrollViewer eine Reihe von angefügten XAML-Eigenschaften, die in Stilen festgelegt und in Vorlagenbindungen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="d44c7-140">To make it possible for controls that include a ScrollViewer to influence some of the behavior and properties that are from within the ScrollViewer part, ScrollViewer defines a number of XAML attached properties that can be set in styles and used in template bindings.</span></span> <span data-ttu-id="d44c7-141">Weitere Informationen zu angefügten Eigenschaften finden Sie unter [Übersicht über angefügte Eigenschaften](../../xaml-platform/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d44c7-141">For more info about attached properties, see [Attached properties overview](../../xaml-platform/attached-properties-overview.md).</span></span>

**<span data-ttu-id="d44c7-142">Angefügte XAML-Eigenschaften für ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="d44c7-142">ScrollViewer XAML attached properties</span></span>**

<span data-ttu-id="d44c7-143">ScrollViewer definiert die folgenden angefügten XAML-Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="d44c7-143">ScrollViewer defines the following XAML attached properties:</span></span>

- [<span data-ttu-id="d44c7-144">ScrollViewer.BringIntoViewOnFocusChange</span><span class="sxs-lookup"><span data-stu-id="d44c7-144">ScrollViewer.BringIntoViewOnFocusChange</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.bringintoviewonfocuschange.aspx)
- [<span data-ttu-id="d44c7-145">ScrollViewer.HorizontalScrollBarVisibility</span><span class="sxs-lookup"><span data-stu-id="d44c7-145">ScrollViewer.HorizontalScrollBarVisibility</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.horizontalscrollbarvisibility.aspx)
- [<span data-ttu-id="d44c7-146">ScrollViewer.HorizontalScrollMode</span><span class="sxs-lookup"><span data-stu-id="d44c7-146">ScrollViewer.HorizontalScrollMode</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.horizontalscrollmode.aspx)
- [<span data-ttu-id="d44c7-147">ScrollViewer.IsDeferredScrollingEnabled</span><span class="sxs-lookup"><span data-stu-id="d44c7-147">ScrollViewer.IsDeferredScrollingEnabled</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.isdeferredscrollingenabled.aspx)
- [<span data-ttu-id="d44c7-148">ScrollViewer.IsHorizontalRailEnabled</span><span class="sxs-lookup"><span data-stu-id="d44c7-148">ScrollViewer.IsHorizontalRailEnabled</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.ishorizontalrailenabled.aspx)
- [<span data-ttu-id="d44c7-149">ScrollViewer.IsHorizontalScrollChainingEnabled</span><span class="sxs-lookup"><span data-stu-id="d44c7-149">ScrollViewer.IsHorizontalScrollChainingEnabled</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.ishorizontalscrollchainingenabled.aspx)
- [<span data-ttu-id="d44c7-150">ScrollViewer.IsScrollInertiaEnabled</span><span class="sxs-lookup"><span data-stu-id="d44c7-150">ScrollViewer.IsScrollInertiaEnabled</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.isscrollinertiaenabled.aspx)
- [<span data-ttu-id="d44c7-151">ScrollViewer.IsVerticalRailEnabled</span><span class="sxs-lookup"><span data-stu-id="d44c7-151">ScrollViewer.IsVerticalRailEnabled</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.isverticalrailenabled.aspx)
- [<span data-ttu-id="d44c7-152">ScrollViewer.IsVerticalScrollChainingEnabled</span><span class="sxs-lookup"><span data-stu-id="d44c7-152">ScrollViewer.IsVerticalScrollChainingEnabled</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.isverticalscrollchainingenabled.aspx)
- [<span data-ttu-id="d44c7-153">ScrollViewer.IsZoomChainingEnabled</span><span class="sxs-lookup"><span data-stu-id="d44c7-153">ScrollViewer.IsZoomChainingEnabled</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.iszoominertiaenabled.aspx)
- [<span data-ttu-id="d44c7-154">ScrollViewer.IsZoomInertiaEnabled</span><span class="sxs-lookup"><span data-stu-id="d44c7-154">ScrollViewer.IsZoomInertiaEnabled</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.iszoominertiaenabled.aspx)
- [<span data-ttu-id="d44c7-155">ScrollViewer.VerticalScrollBarVisibility</span><span class="sxs-lookup"><span data-stu-id="d44c7-155">ScrollViewer.VerticalScrollBarVisibility</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.verticalscrollbarvisibilityproperty.aspx)
- [<span data-ttu-id="d44c7-156">ScrollViewer.VerticalScrollMode</span><span class="sxs-lookup"><span data-stu-id="d44c7-156">ScrollViewer.VerticalScrollMode</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.verticalscrollmode.aspx)
- [<span data-ttu-id="d44c7-157">ScrollViewer.ZoomMode</span><span class="sxs-lookup"><span data-stu-id="d44c7-157">ScrollViewer.ZoomMode</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.zoommode.aspx)

<span data-ttu-id="d44c7-158">Diese angefügten XAML-Eigenschaften sind für Fälle vorgesehen, in denen ScrollViewer implizit ist, z. B. wenn der ScrollViewer in der Standardvorlage für ListView oder GridView vorhanden ist und Sie das Bildlaufverhalten des Steuerelements ohne Zugriff auf Vorlagenelemente steuern möchten.</span><span class="sxs-lookup"><span data-stu-id="d44c7-158">These XAML attached properties are intended for cases where the ScrollViewer is implicit, such as when the ScrollViewer exists in the default template for a ListView or GridView, and you want to be able to influence the scrolling behavior of the control without accessing template parts.</span></span>

<span data-ttu-id="d44c7-159">Im Folgenden wird z. B. erläutert, wie Sie die vertikalen Bildlaufleisten für die integrierte Bildlaufanzeige einer ListView immer sichtbar machen.</span><span class="sxs-lookup"><span data-stu-id="d44c7-159">For example, here's how to make the vertical scrollbars always visible for a ListView's built in scroll viewer.</span></span>

```xaml
<ListView ScrollViewer.VerticalScrollBarVisibility="Visible"/>
```

<span data-ttu-id="d44c7-160">In Fällen, in denen im XAML-Code wie im Beispielcode gezeigt ein ScrollViewer explizit vorhanden ist, müssen Sie keine Syntax mit angefügten Eigenschaften verwenden.</span><span class="sxs-lookup"><span data-stu-id="d44c7-160">For cases where a ScrollViewer is explicit in your XAML, as is shown in the example code, you don't need to use attached property syntax.</span></span> <span data-ttu-id="d44c7-161">Verwenden Sie einfach eine Attributsyntax, z.B. `<ScrollViewer VerticalScrollBarVisibility="Visible"/>`.</span><span class="sxs-lookup"><span data-stu-id="d44c7-161">Just use attribute syntax, for example `<ScrollViewer VerticalScrollBarVisibility="Visible"/>`.</span></span>


## <a name="dos-and-donts"></a><span data-ttu-id="d44c7-162">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="d44c7-162">Do's and don'ts</span></span>

- <span data-ttu-id="d44c7-163">Verwenden Sie möglichst ein Design für einen vertikalen Bildlauf und nicht für einen horizontalen Bildlauf.</span><span class="sxs-lookup"><span data-stu-id="d44c7-163">Whenever possible, design for vertical scrolling rather than horizontal.</span></span>
- <span data-ttu-id="d44c7-164">Verwenden Sie die Verschiebung entlang einer Achse für Inhaltsbereiche, die über eine Viewportgrenze (vertikal oder horizontal) hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="d44c7-164">Use one-axis panning for content regions that extend beyond one viewport boundary (vertical or horizontal).</span></span> <span data-ttu-id="d44c7-165">Verwenden Sie die Verschiebung entlang zweier Achsen für Inhaltsbereiche, die über beide Viewportgrenzen (vertikal und horizontal) hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="d44c7-165">Use two-axis panning for content regions that extend beyond both viewport boundaries (vertical and horizontal).</span></span>
- <span data-ttu-id="d44c7-166">Verwenden Sie in der Listen- und Rasteransicht sowie im Kombinationsfeld, Listenfeld, Texteingabefeld und für Hubsteuerelemente die integrierte Bildlauffunktionalität.</span><span class="sxs-lookup"><span data-stu-id="d44c7-166">Use the built-in scroll functionality in the list view, grid view, combo box, list box, text input box, and hub controls.</span></span> <span data-ttu-id="d44c7-167">Wenn die Anzahl von Elementen so groß ist, dass sie nicht alle gleichzeitig angezeigt werden können, hat der Benutzer mit diesen Steuerelementen die Möglichkeit, einen vertikalen oder horizontalen Bildlauf durch die Elementliste durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="d44c7-167">With those controls, if there are too many items to show all at once, the user is able to scroll either horizontally or vertically over the list of items.</span></span>
- <span data-ttu-id="d44c7-168">Wenn der Benutzer die Verschiebung in beide Richtungen um einen größeren Bereich herum ausführen und möglicherweise auch zoomen soll (wenn Sie dem Benutzer beispielsweise das Verschieben und Zoomen über ein Bild in voller Größe ermöglichen möchten, anstatt ein Bild mit an den Bildschirm angepasster Größe zu verwenden), positionieren Sie das Bild in einer Bildlaufanzeige.</span><span class="sxs-lookup"><span data-stu-id="d44c7-168">If you want the user to pan in both directions around a larger area, and possibly to zoom, too, for example, if you want to allow the user to pan and zoom over a full-sized image (rather than an image sized to fit the screen) then place the image inside a scroll viewer.</span></span>
- <span data-ttu-id="d44c7-169">Wenn der Benutzer in einer langen Textpassage einen Bildlauf ausführen wird, konfigurieren Sie die Bildlaufanzeige ausschließlich für den vertikalen Bildlauf.</span><span class="sxs-lookup"><span data-stu-id="d44c7-169">If the user will scroll through a long passage of text, configure the scroll viewer to scroll vertically only.</span></span>
- <span data-ttu-id="d44c7-170">Bei Verwendung einer Bildlaufanzeige darf diese nur ein Objekt umfassen.</span><span class="sxs-lookup"><span data-stu-id="d44c7-170">Use a scroll viewer to contain one object only.</span></span> <span data-ttu-id="d44c7-171">Beachten Sie, dass es sich bei dem einen Objekt um einen Layoutbereich handeln kann, der wiederum eine beliebige Anzahl eigener Objekte enthält.</span><span class="sxs-lookup"><span data-stu-id="d44c7-171">Note that the one object can be a layout panel, in turn containing any number of objects of its own.</span></span>
- <span data-ttu-id="d44c7-172">Platzieren Sie kein [Pivot](tabs-pivot.md)-Steuerelement in einer Bildlaufanzeige, um Konflikte mit der Pivot-Bildlauflogik zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="d44c7-172">Don't place a [Pivot](tabs-pivot.md) control inside a scroll viewer to avoid conflicts with pivot's scrolling logic.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="d44c7-173">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="d44c7-173">Get the sample code</span></span>

- <span data-ttu-id="d44c7-174">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d44c7-174">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-topics"></a><span data-ttu-id="d44c7-175">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d44c7-175">Related topics</span></span>

**<span data-ttu-id="d44c7-176">Für Entwickler (XAML)</span><span class="sxs-lookup"><span data-stu-id="d44c7-176">For developers (XAML)</span></span>**

* [<span data-ttu-id="d44c7-177">ScrollViewer-Klasse</span><span class="sxs-lookup"><span data-stu-id="d44c7-177">ScrollViewer class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209527)
