---
author: Jwmsft
Description: "Verwenden Sie das Muster „Aktualisierung durch Ziehen“ mit einer Listenansicht."
title: Aktualisieren durch Ziehen
label: Pull-to-refresh
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: aaeb1e74-b795-4015-bf41-02cb1d6f467e
pm-contact: predavid
design-contact: kimsea
dev-contact: stpete
doc-status: Published
ms.openlocfilehash: 51a8c9a2e4618e054374308918a74cf2095119ef
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="pull-to-refresh"></a><span data-ttu-id="0397f-104">Aktualisierung durch Ziehen</span><span class="sxs-lookup"><span data-stu-id="0397f-104">Pull to refresh</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="0397f-105">Dank des Musters „Aktualisierung durch Ziehen“ können Benutzer aktuelle Daten in einer Liste durch das Ausführen einer Ziehbewegung von oben nach unten auf der Liste abrufen.</span><span class="sxs-lookup"><span data-stu-id="0397f-105">The pull-to-refresh pattern lets a user pull down on a list of data using touch in order to retrieve more data.</span></span> <span data-ttu-id="0397f-106">Die Aktualisierung durch Ziehen wird häufig in mobilen Apps verwendet, eignet sich jedoch für alle Geräte mit Touchscreen.</span><span class="sxs-lookup"><span data-stu-id="0397f-106">Pull-to-refresh is widely used on mobile apps, but is useful on any device with a touch screen.</span></span> <span data-ttu-id="0397f-107">Durch die Behandlung von [Manipulationsereignissen](../input-and-devices/touch-interactions.md#manipulation-events) können Sie die Aktualisierung durch Ziehen in eine App implementieren.</span><span class="sxs-lookup"><span data-stu-id="0397f-107">You can handle [manipulation events](../input-and-devices/touch-interactions.md#manipulation-events) to implement pull-to-refresh in your app.</span></span>

> <span data-ttu-id="0397f-108">**Wichtige APIs**: [ListView-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), [GridView-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx)</span><span class="sxs-lookup"><span data-stu-id="0397f-108">**Important APIs**: [ListView class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), [GridView class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx)</span></span>

<span data-ttu-id="0397f-109">Im [Beispiel für die Aktualisierung durch Ziehen](http://go.microsoft.com/fwlink/p/?LinkId=620635) wird die Erweiterung eines [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx)-Steuerelements zur Unterstützung dieses Musters dargestellt.</span><span class="sxs-lookup"><span data-stu-id="0397f-109">The [pull-to-refresh sample](http://go.microsoft.com/fwlink/p/?LinkId=620635) shows how to extend a [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx) control to support this pattern.</span></span> <span data-ttu-id="0397f-110">In diesem Artikel werden mithilfe dieses Beispiels die wichtigsten Aspekte der Implementierung des „Aktualisierung durch Ziehen“-Musters erläutert.</span><span class="sxs-lookup"><span data-stu-id="0397f-110">In this article, we use this sample to explain the key points of implementing pull-to-refresh.</span></span>

![Beispiel für die Aktualisierung durch Ziehen](images/ptr-phone-1.png)

## <a name="is-this-the-right-pattern"></a><span data-ttu-id="0397f-112">Für welche Szenarien eignet sich dieses Muster?</span><span class="sxs-lookup"><span data-stu-id="0397f-112">Is this the right pattern?</span></span>

<span data-ttu-id="0397f-113">Das „Aktualisierung durch Ziehen“-Muster eignet sich für Datenlisten oder -raster, die vom Benutzer regelmäßig aktualisiert werden, vor allem, wenn die App hauptsächlich auf mobilen Geräten mit Touchscreen ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="0397f-113">Use the pull-to-refresh pattern when you have a list or grid of data that the user might want to refresh regularly, and your app is likely to be running on mobile, touch-first devices.</span></span>

## <a name="implement-pull-to-refresh"></a><span data-ttu-id="0397f-114">Implementieren von Aktualisierung durch Ziehen</span><span class="sxs-lookup"><span data-stu-id="0397f-114">Implement pull-to-refresh</span></span>

<span data-ttu-id="0397f-115">Für die Implementierung der Aktualisierung durch Ziehen ist die Behandlung von Manipulationsereignissen erforderlich, um zu ermitteln, wann der Benutzer die Liste nach unten zieht, visuelles Feedback bereitzustellen und die Daten zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="0397f-115">To implement pull-to-refresh, you need to handle manipulation events to detect when a user has pulled the list down, provide visual feedback, and refresh the data.</span></span> <span data-ttu-id="0397f-116">Wie dies funktioniert, wird in diesem [Beispiel für die Aktualisierung durch Ziehen](http://go.microsoft.com/fwlink/p/?LinkId=620635) gezeigt.</span><span class="sxs-lookup"><span data-stu-id="0397f-116">Here, we look at how this is done in the [pull-to-refresh sample](http://go.microsoft.com/fwlink/p/?LinkId=620635).</span></span> <span data-ttu-id="0397f-117">Für eine vollständige Darstellung des Codes laden Sie das Beispiel herunter, oder zeigen Sie den Code auf GitHub an.</span><span class="sxs-lookup"><span data-stu-id="0397f-117">We don't show all the code here, so you should download the sample or view the code on GitHub.</span></span>

<span data-ttu-id="0397f-118">Im Beispiel für die Aktualisierung durch Ziehen wird ein benutzerdefiniertes Steuerelement namens `RefreshableListView` als Erweiterung des **ListView**-Steuerelements erstellt.</span><span class="sxs-lookup"><span data-stu-id="0397f-118">The pull-to-refresh sample creates a custom control called `RefreshableListView` that extends the **ListView** control.</span></span> <span data-ttu-id="0397f-119">Dieses Steuerelement behandelt die Manipulationsereignisse in der internen Bildlaufanzeige der Listenansicht und liefert visuelles Feedback mithilfe einer Aktualisierungsanzeige.</span><span class="sxs-lookup"><span data-stu-id="0397f-119">This control adds a refresh indicator to provide visual feedback and handles the manipulation events on the list view's internal scroll viewer.</span></span> <span data-ttu-id="0397f-120">Durch zwei zusätzliche Ereignisse werden Sie zudem informiert, wenn die Liste gezogen wird und die Daten aktualisiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="0397f-120">It also adds 2 events to notify you when the list is pulled and when the data should be refreshed.</span></span> <span data-ttu-id="0397f-121">RefreshableListView bietet lediglich die Benachrichtigung, dass Daten zu aktualisieren sind.</span><span class="sxs-lookup"><span data-stu-id="0397f-121">RefreshableListView only provides notification that the data should be refreshed.</span></span> <span data-ttu-id="0397f-122">Die Aktualisierung der Daten erfordert eine Behandlung des Ereignisses in Ihrer App. Der entsprechende Code hierfür unterscheidet sich je nach App.</span><span class="sxs-lookup"><span data-stu-id="0397f-122">You need to handle the event in your app to update the data, and that code will be different for every app.</span></span>

<span data-ttu-id="0397f-123">RefreshableListView verfügt über einen automatischen Aktualisierungsmodus, mit dem der Zeitpunkt der Aktualisierungsanforderung und die Ausblendung der Aktualisierungsanzeige bestimmt werden können.</span><span class="sxs-lookup"><span data-stu-id="0397f-123">RefreshableListView provides an 'auto refresh' mode that determines when the refresh is requested and how the refresh indicator goes out of view.</span></span> <span data-ttu-id="0397f-124">Die automatische Aktualisierung kann aktiviert oder deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="0397f-124">Auto refresh can be on or off.</span></span>
- <span data-ttu-id="0397f-125">Deaktiviert: Eine Aktualisierung wird nur dann angefordert, wenn die Liste bei Überschreitung von `PullThreshold` losgelassen wird.</span><span class="sxs-lookup"><span data-stu-id="0397f-125">Off: A refresh is requested only if the list is released while the `PullThreshold` is exceded.</span></span> <span data-ttu-id="0397f-126">Wenn der Benutzer den Scroller loslässt, wird die Anzeige ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="0397f-126">The indicator animates out of view when the user releases the scroller.</span></span> <span data-ttu-id="0397f-127">Die Statusleisten-Anzeige wird bei Verfügbarkeit angezeigt (gilt für Smartphone).</span><span class="sxs-lookup"><span data-stu-id="0397f-127">The status bar indicator is shown if it's available (on phone).</span></span>
- <span data-ttu-id="0397f-128">Aktiviert: Die Aktualisierung wird, unabhängig vom Loslassen, bei Überschreitung von `PullThreshold` angefordert.</span><span class="sxs-lookup"><span data-stu-id="0397f-128">On: A refresh is requested as soon as the `PullThreshold` is exceded, whether released or not.</span></span> <span data-ttu-id="0397f-129">Die Anzeige wird erst nach abgeschlossenem Abruf der Daten ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="0397f-129">The indicator remains in view until the new data is retrieved, then animates out of view.</span></span> <span data-ttu-id="0397f-130">Zur Benachrichtigung der App über den abgeschlossenen Abruf der Daten wird eine **Verzögerung** eingesetzt.</span><span class="sxs-lookup"><span data-stu-id="0397f-130">A **Deferral** is used to notify the app when fetching the data is complete.</span></span>

> <span data-ttu-id="0397f-131">**Hinweis**&nbsp;&nbsp;Der im Beispiel dargestellte Code lässt sich auch auf [GridView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx) anwenden.</span><span class="sxs-lookup"><span data-stu-id="0397f-131">**Note**&nbsp;&nbsp;The code in sample is also applicable to a [GridView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx).</span></span> <span data-ttu-id="0397f-132">Zum Ändern von GridView leiten Sie die benutzerdefinierte Klasse von GridView anstelle von ListView ab und nehmen Änderungen an der GridView-Standardvorlage vor.</span><span class="sxs-lookup"><span data-stu-id="0397f-132">To modify a GridView, derive the custom class from GridView instead of ListView and modify the default GridView template.</span></span>

## <a name="add-a-refresh-indicator"></a><span data-ttu-id="0397f-133">Hinzufügen einer Aktualisierungsanzeige</span><span class="sxs-lookup"><span data-stu-id="0397f-133">Add a refresh indicator</span></span>

<span data-ttu-id="0397f-134">Es ist wichtig, den Benutzern durch visuelles Feedback mitzuteilen, dass Ihre App die Aktualisierung durch Ziehen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0397f-134">It's important to provide visual feedback to the user so they know that your app supports pull-to-refresh.</span></span> <span data-ttu-id="0397f-135">RefreshableListView verfügt über eine `RefreshIndicatorContent` -Eigenschaft, mit der Sie die Ansicht der Anzeige in Ihrer XAML festlegen können.</span><span class="sxs-lookup"><span data-stu-id="0397f-135">RefreshableListView has a `RefreshIndicatorContent` property that lets you set the indicator visual in your XAML.</span></span> <span data-ttu-id="0397f-136">RefreshableListView beinhaltet auch eine Standardtextanzeige für den Fall, dass Sie die `RefreshIndicatorContent`-Eigenschaft nicht festlegen.</span><span class="sxs-lookup"><span data-stu-id="0397f-136">It also includes a default text indicator that it falls back to if you don't set the `RefreshIndicatorContent`.</span></span>

<span data-ttu-id="0397f-137">Im Folgenden finden Sie empfohlene Richtlinien für die Aktualisierungsanzeige.</span><span class="sxs-lookup"><span data-stu-id="0397f-137">Here are recommended guidelines for the refresh indicator.</span></span>

![Rote Markierungen der Aktualisierungsanzeige](images/ptr-redlines-1.png)

**<span data-ttu-id="0397f-139">Ändern der Vorlage für die Listenansicht</span><span class="sxs-lookup"><span data-stu-id="0397f-139">Modify the list view template</span></span>**

<span data-ttu-id="0397f-140">Im Beispiel für die Aktualisierung durch Ziehen erweitert die `RefreshableListView`-Steuerelementvorlage die standardmäßige **ListView**-Vorlage um eine Aktualisierungsanzeige.</span><span class="sxs-lookup"><span data-stu-id="0397f-140">In the pull-to-refresh sample, the `RefreshableListView` control template modifies the standard **ListView** template by adding a refresh indicator.</span></span> <span data-ttu-id="0397f-141">Die Aktualisierungsanzeige befindet sich in einem [Raster](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) oberhalb des [ItemsPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemspresenter.aspx), der die Listenelemente anzeigt.</span><span class="sxs-lookup"><span data-stu-id="0397f-141">The refresh indicator is placed in a [Grid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) above the [ItemsPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemspresenter.aspx), which is the part that shows the list items.</span></span>

> <span data-ttu-id="0397f-142">**Hinweis**&nbsp;&nbsp;Das `DefaultRefreshIndicatorContent`-Textfeld stellt eine Standardtextanzeige bereit, die nur bei fehlender Festlegung der `RefreshIndicatorContent` -Eigenschaft angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0397f-142">**Note**&nbsp;&nbsp;The `DefaultRefreshIndicatorContent` text box provides a text fallback indicator that is shown only if the `RefreshIndicatorContent` property is not set.</span></span>

<span data-ttu-id="0397f-143">Im Folgenden finden Sie den Teil der Steuerelementvorlage, die auf Grundlage der ListView-Standardvorlage erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="0397f-143">Here's the part of the control template that's modified from the default ListView template.</span></span>

**<span data-ttu-id="0397f-144">XAML</span><span class="sxs-lookup"><span data-stu-id="0397f-144">XAML</span></span>**
```xaml
<!-- Styles/Styles.xaml -->
<Grid x:Name="ScrollerContent" VerticalAlignment="Top">
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*"/>
        <RowDefinition Height="Auto"/>
    </Grid.RowDefinitions>
    <Border x:Name="RefreshIndicator" VerticalAlignment="Top" Grid.Row="1">
        <Grid>
            <TextBlock x:Name="DefaultRefreshIndicatorContent" HorizontalAlignment="Center" 
                       Foreground="White" FontSize="20" Margin="20, 35, 20, 20"/>
            <ContentPresenter Content="{TemplateBinding RefreshIndicatorContent}"></ContentPresenter>
        </Grid>
    </Border>
    <ItemsPresenter FooterTransitions="{TemplateBinding FooterTransitions}" 
                    FooterTemplate="{TemplateBinding FooterTemplate}" 
                    Footer="{TemplateBinding Footer}" 
                    HeaderTemplate="{TemplateBinding HeaderTemplate}" 
                    Header="{TemplateBinding Header}" 
                    HeaderTransitions="{TemplateBinding HeaderTransitions}" 
                    Padding="{TemplateBinding Padding}"
                    Grid.Row="1"
                    x:Name="ItemsPresenter"/>
</Grid>
```

**<span data-ttu-id="0397f-145">Inhalt in XAML festlegen</span><span class="sxs-lookup"><span data-stu-id="0397f-145">Set the content in XAML</span></span>**

<span data-ttu-id="0397f-146">Der Inhalt der Aktualisierungsanzeige wird in der XAML für Ihre Listenansicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0397f-146">You set the content of the refresh indicator in the XAML for your list view.</span></span> <span data-ttu-id="0397f-147">Die von Ihnen festgelegten XAML-Inhalte werden über den [ContentPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentpresenter.aspx) (`<ContentPresenter Content="{TemplateBinding RefreshIndicatorContent}">`) der Aktualisierungsanzeige angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0397f-147">The XAML content you set is displayed by the refresh indicator's [ContentPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentpresenter.aspx) (`<ContentPresenter Content="{TemplateBinding RefreshIndicatorContent}">`).</span></span> <span data-ttu-id="0397f-148">Wenn Sie diese Inhalte nicht festlegen, wird stattdessen die Standardtextanzeige eingeblendet.</span><span class="sxs-lookup"><span data-stu-id="0397f-148">If you don't set this content, the default text indicator is shown instead.</span></span>

**<span data-ttu-id="0397f-149">XAML</span><span class="sxs-lookup"><span data-stu-id="0397f-149">XAML</span></span>**
```xaml
<!-- MainPage.xaml -->
<c:RefreshableListView
    <!-- ... See sample for removed code. -->
    AutoRefresh="{x:Bind Path=UseAutoRefresh, Mode=OneWay}"
    ItemsSource="{x:Bind Items}"
    PullProgressChanged="listView_PullProgressChanged"
    RefreshRequested="listView_RefreshRequested">

    <c:RefreshableListView.RefreshIndicatorContent>
        <Grid Height="100" Background="Transparent">
            <FontIcon
                Margin="0,0,0,30"
                HorizontalAlignment="Center"
                VerticalAlignment="Bottom"
                FontFamily="Segoe MDL2 Assets"
                FontSize="20"
                Glyph="&#xE72C;"
                RenderTransformOrigin="0.5,0.5">
                <FontIcon.RenderTransform>
                    <RotateTransform x:Name="SpinnerTransform" Angle="0" />
                </FontIcon.RenderTransform>
            </FontIcon>
        </Grid>
    </c:RefreshableListView.RefreshIndicatorContent>
    
    <!-- ... See sample for removed code. -->

</c:RefreshableListView>
```

**<span data-ttu-id="0397f-150">Animieren des Drehfelds</span><span class="sxs-lookup"><span data-stu-id="0397f-150">Animate the spinner</span></span>**

<span data-ttu-id="0397f-151">Wird die Liste nach unten gezogen, wird das `PullProgressChanged` -Ereignis von RefreshableListView ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="0397f-151">When the list is pulled down, RefreshableListView's `PullProgressChanged` event occurs.</span></span> <span data-ttu-id="0397f-152">Sie können dieses Ereignis in Ihrer App behandeln, um die Aktualisierungsanzeige zu steuern.</span><span class="sxs-lookup"><span data-stu-id="0397f-152">You handle this event in your app to control the refresh indicator.</span></span> <span data-ttu-id="0397f-153">Im Beispiel wird durch dieses Storyboard das [RotateTransform](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.rotatetransform.aspx)-Element animiert und die Aktualisierungsanzeige gedreht.</span><span class="sxs-lookup"><span data-stu-id="0397f-153">In the sample, this storyboard is started to animate the indicator's [RotateTransform](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.rotatetransform.aspx) and spin the refresh indicator.</span></span> 

**<span data-ttu-id="0397f-154">XAML</span><span class="sxs-lookup"><span data-stu-id="0397f-154">XAML</span></span>**
```xaml
<!-- MainPage.xaml -->
<Storyboard x:Name="SpinnerStoryboard">
    <DoubleAnimation
        Duration="00:00:00.5"
        FillBehavior="HoldEnd"
        From="0"
        RepeatBehavior="Forever"
        Storyboard.TargetName="SpinnerTransform"
        Storyboard.TargetProperty="Angle"
        To="360" />
</Storyboard>
```

## <a name="handle-scroll-viewer-manipulation-events"></a><span data-ttu-id="0397f-155">Behandeln von Manipulationsereignissen der Bildlaufanzeige</span><span class="sxs-lookup"><span data-stu-id="0397f-155">Handle scroll viewer manipulation events</span></span>

<span data-ttu-id="0397f-156">Die Steuerelementvorlage der Listenansicht enthält einen integrierten [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx), mit dem der Benutzer durch die Listenelemente scrollen kann.</span><span class="sxs-lookup"><span data-stu-id="0397f-156">The list view control template includes a built-in [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx) that lets a user scroll through the list items.</span></span> <span data-ttu-id="0397f-157">Zum Implementieren der Aktualisierung durch Ziehen müssen sowohl die Manipulationsereignisse in der integrierten Bildlaufanzeige als auch mehrere verwandte Ereignisse behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="0397f-157">To implement pull-to-refresh, you have to handle the manipulation events on the built-in scroll viewer, as well as several related events.</span></span> <span data-ttu-id="0397f-158">Weitere Informationen zu Manipulationsereignissen finden Sie unter [Toucheingabe-Interaktionen](../input-and-devices/touch-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="0397f-158">For more info about manipulation events, see [Touch interactions](../input-and-devices/touch-interactions.md).</span></span>

<span data-ttu-id="0397f-159">** OnApplyTemplate**</span><span class="sxs-lookup"><span data-stu-id="0397f-159">** OnApplyTemplate**</span></span>

<span data-ttu-id="0397f-160">Um auf die Bildlaufanzeige und andere Bereiche der Vorlage zuzugreifen sowie Ereignishandler hinzufügen und später im Code aufrufen zu können, müssen Sie die [OnApplyTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.onapplytemplate.aspx)-Methode überschreiben.</span><span class="sxs-lookup"><span data-stu-id="0397f-160">To get access to the scroll viewer and other template parts so that you can add event handlers and call them later in your code, you must override the [OnApplyTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.onapplytemplate.aspx) method.</span></span> <span data-ttu-id="0397f-161">In OnApplyTemplate rufen Sie [GetTemplateChild](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.gettemplatechild.aspx) auf, um einen Verweis auf einen benannten Teil der Steuerelementvorlage zu erhalten, den Sie speichern und später im Code verwenden können.</span><span class="sxs-lookup"><span data-stu-id="0397f-161">In OnApplyTemplate, you call [GetTemplateChild](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.gettemplatechild.aspx) to get a reference to a named part in the control template, which you can save to use later in your code.</span></span>

<span data-ttu-id="0397f-162">Im Beispiel werden die zum Speichern der Vorlagenteile verwendeten Variablen im Bereich „Private Variables“ deklariert.</span><span class="sxs-lookup"><span data-stu-id="0397f-162">In the sample, the variables used to store the template parts are declared in the Private Variables region.</span></span> <span data-ttu-id="0397f-163">Nachdem sie in der OnApplyTemplate-Methode abgerufen wurden, werden Handler für die Ereignisse [DirectManipulationStarted](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.directmanipulationstarted.aspx), [DirectManipulationCompleted](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.directmanipulationcompleted.aspx), [ViewChanged](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.viewchanged.aspx) und [PointerPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.pointerpressed.aspx) hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0397f-163">After they are retrieved in the OnApplyTemplate method, event handlers are added for the [DirectManipulationStarted](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.directmanipulationstarted.aspx), [DirectManipulationCompleted](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.directmanipulationcompleted.aspx), [ViewChanged](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.viewchanged.aspx), and [PointerPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.pointerpressed.aspx) events.</span></span>

**<span data-ttu-id="0397f-164">DirectManipulationStarted</span><span class="sxs-lookup"><span data-stu-id="0397f-164">DirectManipulationStarted</span></span>**

<span data-ttu-id="0397f-165">Zum Initiieren einer „Aktualisierung durch Ziehen“-Aktion muss der Inhalt an das obere Ende der Bildlaufanzeige gescrollt sein, wenn der Benutzer den Finger auf dem Bildschirm nach unten zieht.</span><span class="sxs-lookup"><span data-stu-id="0397f-165">In order to initiate a pull-to-refresh action, the content has to be scrolled to the top of the scroll viewer when the user starts to pull down.</span></span> <span data-ttu-id="0397f-166">Andernfalls wird davon ausgegangen, dass der Benutzer über den Touchscreen auf der Liste nach oben scrollt.</span><span class="sxs-lookup"><span data-stu-id="0397f-166">Otherwise, it's assumed that the user is pulling in order to pan up in the list.</span></span> <span data-ttu-id="0397f-167">Der Code in diesem Handler bestimmt, ob die Manipulation am oberen Rand der Bildlaufanzeige beginnt, und kann die Aktualisierung der Liste auslösen.</span><span class="sxs-lookup"><span data-stu-id="0397f-167">The code in this handler determines whether the manipulation started with the content at the top of the scroll viewer, and can result in the list being refreshed.</span></span> <span data-ttu-id="0397f-168">Der Status der Aktualisierbarkeit des Steuerelements wird entsprechend festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0397f-168">The control's 'refreshable' status is set accordingly.</span></span> 

<span data-ttu-id="0397f-169">Wenn eine Aktualisierung des Steuerelements möglich ist, werden die Ereignishandler für Animationen ebenfalls hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0397f-169">If the control can be refreshed, event handlers for animations are also added.</span></span>

**<span data-ttu-id="0397f-170">DirectManipulationCompleted</span><span class="sxs-lookup"><span data-stu-id="0397f-170">DirectManipulationCompleted</span></span>**

<span data-ttu-id="0397f-171">Sobald der Benutzer das Ziehen der Liste nach unten beendet, prüft der Code dieses Handlers, ob während der Manipulation eine Aktualisierung aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="0397f-171">When the user stops pulling the list down, the code in this handler checks whether a refresh was activated during the manipulation.</span></span> <span data-ttu-id="0397f-172">Ist dies der Fall, wird das `RefreshRequested` -Ereignis ausgelöst und der `RefreshCommand` Befehl ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="0397f-172">If a refresh was activated, the `RefreshRequested` event is raised and the `RefreshCommand` command is executed.</span></span>

<span data-ttu-id="0397f-173">Die Ereignishandler für Animationen werden ebenfalls entfernt.</span><span class="sxs-lookup"><span data-stu-id="0397f-173">The event handlers for animations are also removed.</span></span>

<span data-ttu-id="0397f-174">Basierend auf dem Wert der `AutoRefresh` -Eigenschaft kann die Liste per Animation entweder sofort oder erst nach abgeschlossener Aktualisierung an ihren Anfang zurückgeblättert werden.</span><span class="sxs-lookup"><span data-stu-id="0397f-174">Based on the value of the `AutoRefresh` property, the list can animate back up immediately, or wait until the refresh is complete and then animate back up.</span></span> <span data-ttu-id="0397f-175">Zur Kennzeichnung der abgeschlossenen Aktualisierung wird ein [Verzögerungs](https://msdn.microsoft.com/library/windows/apps/windows.foundation.deferral.aspx)-Objekt verwendet.</span><span class="sxs-lookup"><span data-stu-id="0397f-175">A [Deferral](https://msdn.microsoft.com/library/windows/apps/windows.foundation.deferral.aspx) object is used to to mark the completion of the refresh.</span></span> <span data-ttu-id="0397f-176">An diesem Punkt ist die Aktualisierungsanzeige ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="0397f-176">At that point the refresh indicator UI is hidden.</span></span>

<span data-ttu-id="0397f-177">Dieser Teil des „DirectManipulationCompleted“-Ereignishandlers löst das `RefreshRequested`-Ereignis aus und ruft bei Bedarf die Verzögerung ab.</span><span class="sxs-lookup"><span data-stu-id="0397f-177">This part of the DirectManipulationCompleted event handler raises the `RefreshRequested` event and get's the Deferral if needed.</span></span>

**<span data-ttu-id="0397f-178">C#</span><span class="sxs-lookup"><span data-stu-id="0397f-178">C#</span></span>**
```csharp
if (this.RefreshRequested != null)
{
    RefreshRequestedEventArgs refreshRequestedEventArgs = new RefreshRequestedEventArgs(
        this.AutoRefresh ? new DeferralCompletedHandler(RefreshCompleted) : null);
    this.RefreshRequested(this, refreshRequestedEventArgs);
    if (this.AutoRefresh)
    {
        m_scrollerContent.ManipulationMode = ManipulationModes.None;
        if (!refreshRequestedEventArgs.WasDeferralRetrieved)
        {
            // The Deferral object was not retrieved in the event handler.
            // Animate the content up right away.
            this.RefreshCompleted();
        }
    }
}
```

**<span data-ttu-id="0397f-179">ViewChanged</span><span class="sxs-lookup"><span data-stu-id="0397f-179">ViewChanged</span></span>**

<span data-ttu-id="0397f-180">Im „ViewChanged“-Ereignishandler werden zwei Fälle behandelt.</span><span class="sxs-lookup"><span data-stu-id="0397f-180">Two cases are handled in the ViewChanged event handler.</span></span>

<span data-ttu-id="0397f-181">Erstens wird im Fall einer durch die Zoombildlaufanzeige geänderten Ansicht der Status der Aktualisierbarkeit des Steuerelements widerrufen.</span><span class="sxs-lookup"><span data-stu-id="0397f-181">First, if the view changed due to the scroll viewer zooming, the control's 'refreshable' status is canceled.</span></span>

<span data-ttu-id="0397f-182">Zweitens werden, sobald sich der Inhalt am Ende einer automatischen Aktualisierung wieder nach oben bewegt hat, die Rechtecke für den Abstand ausgeblendet, Touchinteraktionen mit der Bildlaufanzeige wieder aktiviert und der [VerticalOffset](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.verticaloffset.aspx) auf 0 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0397f-182">Second, if the content finished animating up at the end of an auto refresh, the padding rectangles are hidden, touch interactions with the scroll viewer are re-anabled, the [VerticalOffset](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.verticaloffset.aspx) is set to 0.</span></span>

**<span data-ttu-id="0397f-183">PointerPressed</span><span class="sxs-lookup"><span data-stu-id="0397f-183">PointerPressed</span></span>**

<span data-ttu-id="0397f-184">Die Aktualisierung durch Ziehen wird nur dann ausgelöst, wenn die Liste durch eine Touchmanipulation nach unten gezogen wird.</span><span class="sxs-lookup"><span data-stu-id="0397f-184">Pull-to-refresh happens only when the list is pulled down by a touch manipulation.</span></span> <span data-ttu-id="0397f-185">Mit dem Code des „PointerPressed“-Ereignishandlers wird überprüft, welche Art von Zeiger das Ereignis ausgelöst hat und eine Variable (`m_pointerPressed`) zur Indikation eines Touchzeigers festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0397f-185">In the PointerPressed event handler, the code checks what kind of pointer caused the event and sets a variable (`m_pointerPressed`) to indicate whether it was a touch pointer.</span></span> <span data-ttu-id="0397f-186">Diese Variable wird im „DirectManipulationStarted“-Handler verwendet.</span><span class="sxs-lookup"><span data-stu-id="0397f-186">This variable is used in the DirectManipulationStarted handler.</span></span> <span data-ttu-id="0397f-187">Wenn der Zeiger kein Touchzeiger ist, wird der „DirectManipulationStarted“-Handler ohne Ausführung einer Aktion zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="0397f-187">If the pointer is not a touch pointer, the DirectManipulationStarted handler returns without doing anything.</span></span>

## <a name="add-pull-and-refresh-events"></a><span data-ttu-id="0397f-188">Hinzufügen von „Aktualisierung durch Ziehen“-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="0397f-188">Add pull and refresh events</span></span>

<span data-ttu-id="0397f-189">„RefreshableListView“ fügt zwei Ereignisse hinzu, die Sie in Ihrer App behandeln können. Mit diesen lassen sich die Daten aktualisieren und die Aktualisierungsanzeige verwalten.</span><span class="sxs-lookup"><span data-stu-id="0397f-189">'RefreshableListView' adds 2 events that you can handle in your app to refresh the data and manage the refresh indicator.</span></span>

<span data-ttu-id="0397f-190">Weitere Informationen zu Ereignissen finden Sie unter [Übersicht über Ereignisse und Routingereignisse](https://msdn.microsoft.com/windows/uwp/xaml-platform/events-and-routed-events-overview).</span><span class="sxs-lookup"><span data-stu-id="0397f-190">For more info about events, see [Events and routed events overview](https://msdn.microsoft.com/windows/uwp/xaml-platform/events-and-routed-events-overview).</span></span>

**<span data-ttu-id="0397f-191">RefreshRequested</span><span class="sxs-lookup"><span data-stu-id="0397f-191">RefreshRequested</span></span>**

<span data-ttu-id="0397f-192">Das „RefreshRequested“-Ereignis benachrichtigt Ihre App, wenn der Benutzer die Liste für eine Aktualisierung nach unten zieht.</span><span class="sxs-lookup"><span data-stu-id="0397f-192">The 'RefreshRequested' event notifies your app that the user has pulled the list to refresh it.</span></span> <span data-ttu-id="0397f-193">Sie behandeln dieses Ereignis zum Abrufen neuer Daten und zum Aktualisieren der Liste.</span><span class="sxs-lookup"><span data-stu-id="0397f-193">You handle this event to fetch new data and update your list.</span></span>

<span data-ttu-id="0397f-194">Hier sehen Sie den Ereignishandler aus dem Beispiel.</span><span class="sxs-lookup"><span data-stu-id="0397f-194">Here's the event handler from the sample.</span></span> <span data-ttu-id="0397f-195">Entscheidend ist, dass die `AutoRefresh`-Eigenschaft der Listenansicht überprüft und eine Verzögerung abgerufen wird, wenn die Eigenschaft auf **true** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="0397f-195">The important thing to notice is that it check's the list view's `AutoRefresh` property and get's a Deferral if it's **true**.</span></span> <span data-ttu-id="0397f-196">Durch eine Verzögerung wird die Aktualisierungsanzeige weiterhin angezeigt, bis die Aktualisierung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="0397f-196">With a Deferral, the refresh indicator is not stopped and hidden until the refresh is complete.</span></span>

**<span data-ttu-id="0397f-197">C#</span><span class="sxs-lookup"><span data-stu-id="0397f-197">C#</span></span>**
```csharp
private async void listView_RefreshRequested(object sender, RefreshableListView.RefreshRequestedEventArgs e)
{
    using (Deferral deferral = listView.AutoRefresh ? e.GetDeferral() : null)
    {
        await FetchAndInsertItemsAsync(_rand.Next(1, 5));

        if (SpinnerStoryboard.GetCurrentState() != Windows.UI.Xaml.Media.Animation.ClockState.Stopped)
        {
            SpinnerStoryboard.Stop();
        }
    }
}
```

**<span data-ttu-id="0397f-198">PullProgressChanged</span><span class="sxs-lookup"><span data-stu-id="0397f-198">PullProgressChanged</span></span>**

<span data-ttu-id="0397f-199">In diesem Beispiel werden Inhalte für die Aktualisierungsanzeige bereitgestellt und durch die App gesteuert.</span><span class="sxs-lookup"><span data-stu-id="0397f-199">In the sample, content for the refresh indicator is provided and controlled by the app.</span></span> <span data-ttu-id="0397f-200">Das „PullProgressChanged“-Ereignis benachrichtigt Ihre App, wenn der Benutzer die Liste herunterzieht. So kann die Aktualisierungsanzeige gestartet, beendet und zurückgesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="0397f-200">The 'PullProgressChanged' event notifies your app when the use is pulling the list so that you can start, stop, and reset the refresh indicator.</span></span> 

## <a name="composition-animations"></a><span data-ttu-id="0397f-201">Kompositionsanimationen</span><span class="sxs-lookup"><span data-stu-id="0397f-201">Composition animations</span></span>

<span data-ttu-id="0397f-202">Standardmäßig wird die Scrollbewegung des Inhalts in einer Bildlaufanzeige beim Erreichen des oberen Endes der Scrollleiste beendet.</span><span class="sxs-lookup"><span data-stu-id="0397f-202">By default, content in a scroll viewer stops when the scrollbar reaches the top.</span></span> <span data-ttu-id="0397f-203">Um dem Benutzer das Herunterziehen der Liste zu ermöglichen, muss auf die visuelle Ebene zugegriffen und der Listeninhalt animiert werden.</span><span class="sxs-lookup"><span data-stu-id="0397f-203">To let the user continue to pull the list down, you need to access the visual layer and animate the list content.</span></span> <span data-ttu-id="0397f-204">Im Beispiel werden hierfür [Kompositionsanimationen](https://msdn.microsoft.com/windows/uwp/composition/composition-animation), genauer [Ausdrucksanimationen](https://msdn.microsoft.com/windows/uwp/composition/composition-animation#expression-animations), verwendet.</span><span class="sxs-lookup"><span data-stu-id="0397f-204">The sample uses [composition animations](https://msdn.microsoft.com/windows/uwp/composition/composition-animation) for this; specifically, [expression animations](https://msdn.microsoft.com/windows/uwp/composition/composition-animation#expression-animations).</span></span>

<span data-ttu-id="0397f-205">Diese Vorgänge werden im Beispiel hauptsächlich mit dem `CompositionTarget_Rendering` -Ereignishandler und der `UpdateCompositionAnimations` -Methode ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="0397f-205">In the sample, this work is done primarily in the `CompositionTarget_Rendering` event handler and the `UpdateCompositionAnimations` method.</span></span>

## <a name="related-articles"></a><span data-ttu-id="0397f-206">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="0397f-206">Related articles</span></span>

- [<span data-ttu-id="0397f-207">Formatieren von Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="0397f-207">Styling controls</span></span>](styling-controls.md)
- [<span data-ttu-id="0397f-208">Toucheingabe-Interaktionen</span><span class="sxs-lookup"><span data-stu-id="0397f-208">Touch interactions</span></span>](../input-and-devices/touch-interactions.md)
- [<span data-ttu-id="0397f-209">Listenansicht und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="0397f-209">List view and grid view</span></span>](listview-and-gridview.md)
- [<span data-ttu-id="0397f-210">Vorlagen für Listenansichtselemente</span><span class="sxs-lookup"><span data-stu-id="0397f-210">List view item templates</span></span>](listview-item-templates.md)
- [<span data-ttu-id="0397f-211">Ausdrucksanimationen</span><span class="sxs-lookup"><span data-stu-id="0397f-211">Expression animations</span></span>](https://msdn.microsoft.com/windows/uwp/composition/composition-animation#expression-animations)