---
author: Jwmsft
Description: Use the pull-to-refresh control to get new content into a list.
title: Aktualisieren durch Ziehen
label: Pull-to-refresh
template: detail.hbs
ms.author: jimwalk
ms.date: 03/07/2018
ms.topic: article
keywords: Windows10, UWP
ms.assetid: aaeb1e74-b795-4015-bf41-02cb1d6f467e
pm-contact: predavid
design-contact: kimsea
dev-contact: stpete
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 8b1dd6bd1bc165a79ba123c94e63e1dcfa58ec21
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5593464"
---
# <a name="pull-to-refresh"></a><span data-ttu-id="b7dde-103">Aktualisieren durch Ziehen</span><span class="sxs-lookup"><span data-stu-id="b7dde-103">Pull to refresh</span></span>

<span data-ttu-id="b7dde-104">Mithilfe der Aktion „Aktualisieren durch Ziehen“ können Benutzer eine Datenliste per Touchgeste nach unten ziehen, um weitere Daten abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b7dde-104">Pull-to-refresh lets a user pull down on a list of data using touch in order to retrieve more data.</span></span> <span data-ttu-id="b7dde-105">Die Aktion „Aktualisieren durch Ziehen“ wird häufig auf Geräten mit Touchscreen verwendet.</span><span class="sxs-lookup"><span data-stu-id="b7dde-105">Pull-to-refresh is widely used on devices with a touch screen.</span></span> <span data-ttu-id="b7dde-106">Sie können die hier gezeigten APIs zum Implementieren von „Aktualisieren durch Ziehen“ in Ihre App verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7dde-106">You can use the APIs shown here to implement pull-to-refresh in your app.</span></span>

> <span data-ttu-id="b7dde-107">**Wichtige APIs**: [RefreshContainer](/uwp/api/windows.ui.xaml.controls.refreshcontainer), [RefreshVisualizer](/uwp/api/windows.ui.xaml.controls.refreshvisualizer)</span><span class="sxs-lookup"><span data-stu-id="b7dde-107">**Important APIs**: [RefreshContainer](/uwp/api/windows.ui.xaml.controls.refreshcontainer), [RefreshVisualizer](/uwp/api/windows.ui.xaml.controls.refreshvisualizer)</span></span>

![GIF zu „Aktualisieren durch Ziehen“](images/Pull-To-Refresh.gif)

## <a name="is-this-the-right-control"></a><span data-ttu-id="b7dde-109">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="b7dde-109">Is this the right control?</span></span>

<span data-ttu-id="b7dde-110">Verwenden Sie „Aktualisieren durch Ziehen“ für Datenlisten oder -raster, die vom Benutzer regelmäßig aktualisiert werden, vor allem, wenn die App hauptsächlich auf Geräten mit Touchscreen ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="b7dde-110">Use pull-to-refresh when you have a list or grid of data that the user might want to refresh regularly, and your app is likely to be running on touch-first devices.</span></span>

<span data-ttu-id="b7dde-111">Sie können auch den [RefreshVisualizer](/uwp/api/windows.ui.xaml.controls.refreshvisualizer) verwenden, um eine konsistente Aktualisierungsoption zu erstellen, die auf andere Weise, wie z.B. durch eine Aktualisierungsschaltfläche aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b7dde-111">You can also use the [RefreshVisualizer](/uwp/api/windows.ui.xaml.controls.refreshvisualizer) to create a consistent refresh experience that is invoked in other ways, such as by a refresh button.</span></span>

## <a name="refresh-controls"></a><span data-ttu-id="b7dde-112">Aktualisierungssteuerelemente</span><span class="sxs-lookup"><span data-stu-id="b7dde-112">Refresh controls</span></span>

<span data-ttu-id="b7dde-113">„Aktualisieren durch Ziehen“ wird durch zwei Steuerelemente aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b7dde-113">Pull-to-refresh is enabled by 2 controls.</span></span>

- <span data-ttu-id="b7dde-114">**RefreshContainer** – Ein ContentControl, das einen Wrapper für das Pull-to-Refresh-Erlebnis bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="b7dde-114">**RefreshContainer** - a ContentControl that provides a wrapper for the pull-to-refresh experience.</span></span> <span data-ttu-id="b7dde-115">Es verarbeitet die Interaktionen per Fingereingabe und verwaltet den Zustand des internen Visualizers für Aktualisierungen.</span><span class="sxs-lookup"><span data-stu-id="b7dde-115">It handles the touch interactions and manages the state of its internal refresh visualizer.</span></span>
- <span data-ttu-id="b7dde-116">**RefreshVisualizer** – Kapselt die Aktualisierungsvisualisierung, die im nächsten Abschnitterläutert wird.</span><span class="sxs-lookup"><span data-stu-id="b7dde-116">**RefreshVisualizer** - encapsulates the refresh visualization explained in the next section.</span></span>

<span data-ttu-id="b7dde-117">Das wichtigste Steuerelement ist **RefreshContainer**, das Sie als Wrapper um den Inhalt platzieren, den der Benutzer abruft, um eine Aktualisierung auszulösen.</span><span class="sxs-lookup"><span data-stu-id="b7dde-117">The main control is the **RefreshContainer**, which you place as a wrapper around the content that the user pulls to trigger a refresh.</span></span> <span data-ttu-id="b7dde-118">Da RefreshContainer nur mit Toucheingabe funktioniert, wird empfohlen, dass Sie auch eine Aktualisierungsschaltfläche für Benutzer bereitstellen, die über keinen Touchscreen verfügen.</span><span class="sxs-lookup"><span data-stu-id="b7dde-118">RefreshContainer works only with touch, so we recommend that you also have a refresh button available for users who don't have a touch interface.</span></span> <span data-ttu-id="b7dde-119">Sie können die Aktualisierungsschaltfläche an einer geeigneten Stelle in der App positionieren, entweder auf einer Befehlsleiste oder in der Nähe der Oberfläche, die aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="b7dde-119">You can position the refresh button at a suitable location in the app, either on a command bar or at a location close to the surface being refreshed.</span></span>

## <a name="refresh-visualization"></a><span data-ttu-id="b7dde-120">Visualisierung aktualisieren</span><span class="sxs-lookup"><span data-stu-id="b7dde-120">Refresh visualization</span></span>

<span data-ttu-id="b7dde-121">Die Visualisierung der Standardaktualisierung ist ein kreisförmiges Fortschritts-Drehfeld, das über den Zeitpunkt einer Aktualisierung und deren Fortschritt informiert, nachdem diese gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="b7dde-121">The default refresh visualization is a circular progress spinner that is used to communicate when a refresh will happen and the progress of the refresh after it is initiated.</span></span> <span data-ttu-id="b7dde-122">Der Aktualisierungs-Visualizer verfügt über 5 Zustände.</span><span class="sxs-lookup"><span data-stu-id="b7dde-122">The refresh visualizer has 5 states.</span></span>

 <span data-ttu-id="b7dde-123">Der Abstand, den der Benutzer benötigt, um eine Liste zum Initiieren einer Aktualisierung nach unten zu ziehen, wird als _Schwellenwert_ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="b7dde-123">The distance the user needs to pull down on a list to initiate a refresh is called the _threshold_.</span></span> <span data-ttu-id="b7dde-124">Der Visualizer [Zustand](/uwp/api/windows.ui.xaml.controls.refreshvisualizer.State) wird anhand des Ziehstatus im Zusammenhang mit diesen Schwellenwert bestimmt.</span><span class="sxs-lookup"><span data-stu-id="b7dde-124">The visualizer [State](/uwp/api/windows.ui.xaml.controls.refreshvisualizer.State) is determined by the pull state as it relates to this threshold.</span></span> <span data-ttu-id="b7dde-125">Die möglichen Werte sind in der [RefreshVisualizerState](/uwp/api/windows.ui.xaml.controls.refreshvisualizerstate)-Enumeration enthalten.</span><span class="sxs-lookup"><span data-stu-id="b7dde-125">The possible values are contained in the [RefreshVisualizerState](/uwp/api/windows.ui.xaml.controls.refreshvisualizerstate) enumeration.</span></span>

### <a name="idle"></a><span data-ttu-id="b7dde-126">Leerlauf</span><span class="sxs-lookup"><span data-stu-id="b7dde-126">Idle</span></span>

<span data-ttu-id="b7dde-127">Der Standardzustand des Visualizers ist **Leerlauf**.</span><span class="sxs-lookup"><span data-stu-id="b7dde-127">The visualizer's default state is **Idle**.</span></span> <span data-ttu-id="b7dde-128">Der Benutzer interagiert nicht per Toucheingabe mit dem RefreshContainer, und es wird gerade keine Aktualisierung ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b7dde-128">The user is not interacting with the RefreshContainer via touch, and there is not a refresh in progress.</span></span>

<span data-ttu-id="b7dde-129">Visuell gibt es keinen Nachweis für den Aktualisierungs-Visualizer.</span><span class="sxs-lookup"><span data-stu-id="b7dde-129">Visually, there is no evidence of the refresh visualizer.</span></span>

### <a name="interacting"></a><span data-ttu-id="b7dde-130">Interaktion</span><span class="sxs-lookup"><span data-stu-id="b7dde-130">Interacting</span></span>

<span data-ttu-id="b7dde-131">Wenn der Benutzer die Liste in die von der PullDirection-Eigenschaft angegebene Richtung zieht und der Visualizer sich im Zustand **Interaktion** befindet, bevor der Schwellenwert erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="b7dde-131">When the user pulls the list in the direction specified by the PullDirection property, and before the threshold is reached, the visualizer is in the **Interacting** state.</span></span>

- <span data-ttu-id="b7dde-132">Wenn der Benutzer das Steuerelement loslässt, während es sich in diesem Zustand befindet, kehrt das Steuerelement in den **Leerlauf** zurück.</span><span class="sxs-lookup"><span data-stu-id="b7dde-132">If the user releases the control while in this state, the control returns to **Idle**.</span></span>

    ![Aktualisierung durch Ziehen vor dem Schwellenwert](images/ptr-prethreshold.png)

    <span data-ttu-id="b7dde-134">Das Symbol wird visuell als deaktiviert (60% undurchsichtig) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7dde-134">Visually, the icon is displayed as disabled (60% opacity).</span></span> <span data-ttu-id="b7dde-135">Darüber hinaus wird das Symbol mit der Aktion „Bildlauf“ einmal vollständig gedreht.</span><span class="sxs-lookup"><span data-stu-id="b7dde-135">In addition, the icon spins one full rotation with the scroll action.</span></span>

- <span data-ttu-id="b7dde-136">Wenn der Benutzer die Liste über den Schwellenwert hinaus zieht, wechselt der Visualizer von **Interaktion** in **Ausstehend**.</span><span class="sxs-lookup"><span data-stu-id="b7dde-136">If the user pulls the list past the threshold, the visualizer transitions from **Interacting** to **Pending**.</span></span>

    ![Aktualisierung durch Ziehen am Schwellenwert](images/ptr-atthreshold.png)

    <span data-ttu-id="b7dde-138">Das Symbol wechselt während des Übergangs zu einer Deckkraft von 100% visuell und pulsiert bis zu einer Größe von 150% und wieder zurück zu einer Größe von 100%.</span><span class="sxs-lookup"><span data-stu-id="b7dde-138">Visually, the icon switches to 100% opacity and pulses in size up to 150% and then back to 100% size during the transition.</span></span>

### <a name="pending"></a><span data-ttu-id="b7dde-139">Ausstehend</span><span class="sxs-lookup"><span data-stu-id="b7dde-139">Pending</span></span>

<span data-ttu-id="b7dde-140">Wenn der Benutzer die Liste über den Schwellenwert hinaus gezogen hat, befindet sich der Visualizer im Zustand **Ausstehend**.</span><span class="sxs-lookup"><span data-stu-id="b7dde-140">When the user has pulled the list past the threshold, the visualizer is in the **Pending** state.</span></span>

- <span data-ttu-id="b7dde-141">Wenn der Benutzer die Liste wieder über den Schwellenwert hinaus zieht, ohne sie loszulassen, kehrt sie in den Zustand **Interaktion** zurück.</span><span class="sxs-lookup"><span data-stu-id="b7dde-141">If the user moves the list back above the threshold without releasing it, it returns to the **Interacting** state.</span></span>
- <span data-ttu-id="b7dde-142">Wenn der Benutzer die Liste loslässt, wird eine Aktualisierungsanforderung initiiert und sie wechselt in den Zustand **Aktualisierung**.</span><span class="sxs-lookup"><span data-stu-id="b7dde-142">If the user releases the list, a refresh request is initiated and it transitions to the **Refreshing** state.</span></span>

![Aktualisierung durch Ziehen nach dem Schwellenwert](images/ptr-postthreshold.png)

<span data-ttu-id="b7dde-144">Visuell weist das Symbol eine Größe und Deckkraft von 100% auf.</span><span class="sxs-lookup"><span data-stu-id="b7dde-144">Visually, the icon is 100% in both size and opacity.</span></span> <span data-ttu-id="b7dde-145">In diesem Zustand bewegt sich das Symbol mit der Aktion „Bildlauf“ weiterhin nach unten, dreht sich jedoch nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="b7dde-145">In this state, the icon continues to move down with the scroll action but no longer spins.</span></span>

### <a name="refreshing"></a><span data-ttu-id="b7dde-146">Wird aktualisiert</span><span class="sxs-lookup"><span data-stu-id="b7dde-146">Refreshing</span></span>

<span data-ttu-id="b7dde-147">Wenn der Benutzer den Visualizer in einer über den Schwellenwert hinausgehenden Position freigibt, befindet er sich im Zustand **Aktualisierung**.</span><span class="sxs-lookup"><span data-stu-id="b7dde-147">When the user releases the visualiser past the threshold, it's in the **Refreshing** state.</span></span>

<span data-ttu-id="b7dde-148">Wenn dieser Zustand erreicht ist, wird das **RefreshRequested**-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="b7dde-148">When this state is entered, the **RefreshRequested** event is raised.</span></span> <span data-ttu-id="b7dde-149">Dies ist das Signal für den Start der Aktualisierung des App-Inhalts.</span><span class="sxs-lookup"><span data-stu-id="b7dde-149">This is the signal to start the app's content refresh.</span></span> <span data-ttu-id="b7dde-150">Die Ereignisargumente ([RefreshRequestedEventArgs](/uwp/api/windows.ui.xaml.controls.refreshrequestedeventargs)) enthalten das Objekt [Verzögerung](/uwp/api/windows.foundation.deferral), für das Sie ein Handle im Ereignishandler verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="b7dde-150">The event args ([RefreshRequestedEventArgs](/uwp/api/windows.ui.xaml.controls.refreshrequestedeventargs)) contain a [Deferral](/uwp/api/windows.foundation.deferral) object, which you should take a handle to in the event handler.</span></span> <span data-ttu-id="b7dde-151">Anschließend sollten Sie die Verzögerung als abgeschlossen markieren, wenn der Code zum Ausführen der Aktualisierung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="b7dde-151">Then, you should mark the deferral as completed when your code to perform the refresh has completed.</span></span>

<span data-ttu-id="b7dde-152">Wenn die Aktualisierung abgeschlossen ist, kehrt der Visualizer in den Zustand **Leerlauf** zurück.</span><span class="sxs-lookup"><span data-stu-id="b7dde-152">When the refresh is complete, the visualizer returns to the **Idle** state.</span></span>

<span data-ttu-id="b7dde-153">Visuell kehrt das Symbol zur Schwellenwertposition zurück und dreht sich für die Dauer der Aktualisierung.</span><span class="sxs-lookup"><span data-stu-id="b7dde-153">Visually, the icon settles back to the threshold location and spins for the duration of the refresh.</span></span> <span data-ttu-id="b7dde-154">Diese Drehung dient dazu, den Fortschritt der Aktualisierung anzuzeigen, und wird durch die Animation des eingehenden Inhalts ersetzt.</span><span class="sxs-lookup"><span data-stu-id="b7dde-154">This spinning is used to show progress of the refresh and is replaced by the animation of the incoming content.</span></span>

### <a name="peeking"></a><span data-ttu-id="b7dde-155">Einsehen</span><span class="sxs-lookup"><span data-stu-id="b7dde-155">Peeking</span></span>

<span data-ttu-id="b7dde-156">Wenn der Benutzer von einer Startposition, an der eine Aktualisierung unzulässig ist, in die Aktualisierungsrichtung zieht, wechselt der Visualizer in den Zustand **Einsehen**.</span><span class="sxs-lookup"><span data-stu-id="b7dde-156">When the user pulls in the refresh direction from a start position where a refresh is not allowed, the visualizer enters the **Peeking** state.</span></span> <span data-ttu-id="b7dde-157">Dies geschieht in der Regel auf, wenn der ScrollViewer sich nicht an der Position 0 befindet, wenn der Benutzer den Ziehvorgang startet.</span><span class="sxs-lookup"><span data-stu-id="b7dde-157">This typically happens when the ScrollViewer is not at position 0 when the user starts to pull.</span></span>

- <span data-ttu-id="b7dde-158">Wenn der Benutzer das Steuerelement loslässt, während es sich in diesem Zustand befindet, kehrt das Steuerelement in den **Leerlauf** zurück.</span><span class="sxs-lookup"><span data-stu-id="b7dde-158">If the user releases the control while in this state, the control returns to **Idle**.</span></span>

## <a name="pull-direction"></a><span data-ttu-id="b7dde-159">Ziehrichtung</span><span class="sxs-lookup"><span data-stu-id="b7dde-159">Pull direction</span></span>

<span data-ttu-id="b7dde-160">Der Benutzer zieht eine Liste standardmäßig von oben nach unten, um eine Aktualisierung zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="b7dde-160">By default, the user pulls a list from top to bottom to initiate a refresh.</span></span> <span data-ttu-id="b7dde-161">Wenn Sie über eine Liste oder ein Raster mit einer anderen Ausrichtung verfügen, sollten Sie die Ziehrichtung des Aktualisierungs-Containers entsprechend ändern.</span><span class="sxs-lookup"><span data-stu-id="b7dde-161">If you have a list or grid with a different orientation, you should change the pull direction of the refresh container to match.</span></span>

<span data-ttu-id="b7dde-162">Die [PullDirection](/uwp/api/windows.ui.xaml.controls.refreshcontainer.PullDirection)-Eigenschaft verwendet einen der folgenden [RefreshPullDirection](/uwp/api/windows.ui.xaml.controls.refreshpulldirection)-Werte: **BottomToTop**, **TopToBottom**, **RightToLeft** oder **LeftToRight**.</span><span class="sxs-lookup"><span data-stu-id="b7dde-162">The [PullDirection](/uwp/api/windows.ui.xaml.controls.refreshcontainer.PullDirection) property takes one of these [RefreshPullDirection](/uwp/api/windows.ui.xaml.controls.refreshpulldirection) values: **BottomToTop**, **TopToBottom**, **RightToLeft**, or **LeftToRight**.</span></span>

<span data-ttu-id="b7dde-163">Wenn Sie die Ziehrichtung ändern, dreht sich die Startposition des Fortschritts-Drehfelds des Visualizers automatisch, sodass der Pfeil in der entsprechenden Position für die Ziehrichtung startet.</span><span class="sxs-lookup"><span data-stu-id="b7dde-163">When you change the pull dircetion, the starting position of the visualizer's progress spinner automatically rotates so the arrow starts in the appropriate position for the pull direction.</span></span> <span data-ttu-id="b7dde-164">Bei Bedarf können Sie die [RefreshVisualizer.Orientation](/uwp/api/windows.ui.xaml.controls.refreshvisualizer.Orientation)-Eigenschaft ändern, um das automatische Verhalten außer Kraft zu setzen.</span><span class="sxs-lookup"><span data-stu-id="b7dde-164">If needed, you can change the [RefreshVisualizer.Orientation](/uwp/api/windows.ui.xaml.controls.refreshvisualizer.Orientation) property to override the automatic behavior.</span></span> <span data-ttu-id="b7dde-165">In den meisten Fällen empfiehlt es sich, den Standardwert **Auto** beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="b7dde-165">In most cases, we recommend leaving the default value of **Auto**.</span></span>

## <a name="implement-pull-to-refresh"></a><span data-ttu-id="b7dde-166">Implementieren von Aktualisierung durch Ziehen</span><span class="sxs-lookup"><span data-stu-id="b7dde-166">Implement pull-to-refresh</span></span>

<span data-ttu-id="b7dde-167">Um einer Liste die Funktionalität „Aktualisierung durch Ziehen“ hinzuzufügen, müssen nur wenige Schritte ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b7dde-167">To add pull-to-refresh functionality to a list requires just a few steps.</span></span>

1. <span data-ttu-id="b7dde-168">Umschließen Sie Ihre Liste in einem **RefreshContainer**-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="b7dde-168">Wrap your list in a **RefreshContainer** control.</span></span>
1. <span data-ttu-id="b7dde-169">Behandeln Sie das **RefreshRequested**-Ereignis, um Ihre Inhalte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="b7dde-169">Handle the **RefreshRequested** event to refresh your content.</span></span>
1. <span data-ttu-id="b7dde-170">Initiieren Sie optional eine Aktualisierung durch Aufrufen von **RequestRefresh** (z.B. durch Klicken auf eine Schaltfläche).</span><span class="sxs-lookup"><span data-stu-id="b7dde-170">Optionally, initiate a refresh by calling **RequestRefresh** (for example, from a button click).</span></span>

> [!NOTE]
> <span data-ttu-id="b7dde-171">Sie können einen eigenständigen RefreshVisualizer instanziieren.</span><span class="sxs-lookup"><span data-stu-id="b7dde-171">You can instantiate a RefreshVisualizer on its own.</span></span> <span data-ttu-id="b7dde-172">Es empfiehlt sich jedoch, Ihre Inhalte in einem RefreshContainer zu umschließen und den von der RefreshContainer.Visualizer-Eigenschaft bereitgestellten RefreshVisualizer auch für Szenarien ohne Touchscreen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7dde-172">However, we recommend that you wrap your content in a RefreshContainer and use the RefreshVisualizer provided by the RefreshContainer.Visualizer property, even for non-touch scenarios.</span></span> <span data-ttu-id="b7dde-173">In diesem Artikel wird davon ausgegangen, dass der Visualizer immer aus dem Aktualisierungs-Container abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b7dde-173">In this article, we assume that the visualizer is always obtained from the refresh container.</span></span>

> <span data-ttu-id="b7dde-174">Verwenden Sie außerdem der Einfachheit halber die RequestRefresh- und RefreshRequested-Elemente des Containers.</span><span class="sxs-lookup"><span data-stu-id="b7dde-174">In addition, use the refresh container's RequestRefresh and RefreshRequested members for convenience.</span></span> `refreshContainer.RequestRefresh()` <span data-ttu-id="b7dde-175">entspricht `refreshContainer.Visualizer.RequestRefresh()` und löst sowohl das RefreshContainer.RefreshRequested-Ereignis als auch die RefreshVisualizer.RefreshRequested-Ereignisse aus.</span><span class="sxs-lookup"><span data-stu-id="b7dde-175">is equivalent to `refreshContainer.Visualizer.RequestRefresh()`, and either will raise both the RefreshContainer.RefreshRequested event and the RefreshVisualizer.RefreshRequested events.</span></span>

### <a name="request-a-refresh"></a><span data-ttu-id="b7dde-176">Anfordern einer Aktualisierung</span><span class="sxs-lookup"><span data-stu-id="b7dde-176">Request a refresh</span></span>

<span data-ttu-id="b7dde-177">Der Aktualisierungs-Container verarbeitet Touchinteraktionen, damit Benutzer Inhalte per Toucheingabe aktualisieren können.</span><span class="sxs-lookup"><span data-stu-id="b7dde-177">The refresh container handles touch interactions to let a user refresh content via touch.</span></span> <span data-ttu-id="b7dde-178">Es wird empfohlen, dass Sie andere Angebote für Schnittstellen bereitstellen, die keine Toucheingabe unterstützen, z.B. eine Aktualisierungsschaltfläche oder Sprachsteuerung.</span><span class="sxs-lookup"><span data-stu-id="b7dde-178">We recommend that you provide other affordances for non-touch interfaces, like a refresh button or voice control.</span></span>

<span data-ttu-id="b7dde-179">Rufen Sie zum Initiieren einer Aktualisierung die [RequestRefresh](/uwp/api/windows.ui.xaml.controls.refreshcontainer.RequestRefresh)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="b7dde-179">To initiate a refresh, call the [RequestRefresh](/uwp/api/windows.ui.xaml.controls.refreshcontainer.RequestRefresh) method.</span></span>

```csharp
// See the Examples section for the full code.
private void RefreshButtonClick(object sender, RoutedEventArgs e)
{
    RefreshContainer.RequestRefresh();
}
```

<span data-ttu-id="b7dde-180">Beim Aufruf von RequestRefresh wechselt der Visualizer-Zustand direkt von **Leerlauf** zu **Aktualisierung**.</span><span class="sxs-lookup"><span data-stu-id="b7dde-180">When you call RequestRefresh, the visualizer state goes directly from **Idle** to **Refreshing**.</span></span>

### <a name="handle-a-refresh-request"></a><span data-ttu-id="b7dde-181">Verarbeiten einer Aktualisierungsanforderung</span><span class="sxs-lookup"><span data-stu-id="b7dde-181">Handle a refresh request</span></span>

<span data-ttu-id="b7dde-182">Behandeln Sie das RefreshRequested-Ereignis, um aktualisierte Inhalte abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b7dde-182">To get fresh content when needed, handle the RefreshRequested event.</span></span> <span data-ttu-id="b7dde-183">Im Ereignishandler benötigen Sie Code, der für Ihre App spezifisch ist, um die aktualisierten Inhalte abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b7dde-183">In the event handler, you'll need code specific to your app to get the fresh content.</span></span>

<span data-ttu-id="b7dde-184">Die Ereignisargumente ([RefreshRequestedEventArgs](/uwp/api/windows.ui.xaml.controls.refreshrequestedeventargs)) enthalten ein [Verzögerung](/uwp/api/windows.foundation.deferral)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b7dde-184">The event args ([RefreshRequestedEventArgs](/uwp/api/windows.ui.xaml.controls.refreshrequestedeventargs)) contain a [Deferral](/uwp/api/windows.foundation.deferral) object.</span></span> <span data-ttu-id="b7dde-185">Rufen Sie im Ereignishandler einen Handle für die Verzögerung ab.</span><span class="sxs-lookup"><span data-stu-id="b7dde-185">Get a handle to the deferral in the event handler.</span></span> <span data-ttu-id="b7dde-186">Markieren Sie die Verzögerung anschließend als abgeschlossen, wenn der Code zum Ausführen der Aktualisierung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="b7dde-186">Then, mark the deferral as completed when your code to perform the refresh has completed.</span></span>

```csharp
// See the Examples section for the full code.
private async void RefreshContainer_RefreshRequested(RefreshContainer sender, RefreshRequestedEventArgs args)
{
    // Respond to a request by performing a refresh and using the deferral object.
    using (var RefreshCompletionDeferral = args.GetDeferral())
    {
        // Do some async operation to refresh the content

         await FetchAndInsertItemsAsync(3);

        // The 'using' statement ensures the deferral is marked as complete.
        // Otherwise, you'd call
        // RefreshCompletionDeferral.Complete();
        // RefreshCompletionDeferral.Dispose();
    }
}
```

### <a name="respond-to-state-changes"></a><span data-ttu-id="b7dde-187">Reagieren auf Zustandsänderungen</span><span class="sxs-lookup"><span data-stu-id="b7dde-187">Respond to state changes</span></span>

<span data-ttu-id="b7dde-188">Sie können bei Bedarf auf Änderungen des Visualizer-Zustands reagieren.</span><span class="sxs-lookup"><span data-stu-id="b7dde-188">You can respond to changes in the visualizer's state, if needed.</span></span> <span data-ttu-id="b7dde-189">Um mehrere Aktualisierungsanforderungen zu verhindern, können Sie eine Aktualisierungsschaltfläche während der Aktualisierung des Visualizers deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="b7dde-189">For example, to prevent multiple refresh requests, you can disable a refresh button while the visualizer is refreshing.</span></span>

```csharp
// See the Examples section for the full code.
private void Visualizer_RefreshStateChanged(RefreshVisualizer sender, RefreshStateChangedEventArgs args)
{
    // Respond to visualizer state changes.
    // Disable the refresh button if the visualizer is refreshing.
    if (args.NewState == RefreshVisualizerState.Refreshing)
    {
        RefreshButton.IsEnabled = false;
    }
    else
    {
        RefreshButton.IsEnabled = true;
    }
}
```

## <a name="examples"></a><span data-ttu-id="b7dde-190">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b7dde-190">Examples</span></span>

### <a name="using-a-scrollviewer-in-a-refreshcontainer"></a><span data-ttu-id="b7dde-191">Verwenden von ScrollViewer in einem RefreshContainer</span><span class="sxs-lookup"><span data-stu-id="b7dde-191">Using a ScrollViewer in a RefreshContainer</span></span>

<span data-ttu-id="b7dde-192">Anhand dieses Beispiels wird veranschaulicht, wie Sie „Aktualisierung durch Ziehen“ mit einer Bildlaufanzeige verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7dde-192">This example shows how to use pull-to-refresh with a scroll viewer.</span></span>

```xaml
<RefreshContainer>
    <ScrollViewer VerticalScrollMode="Enabled"
                  VerticalScrollBarVisibility="Auto"
                  HorizontalScrollBarVisibility="Auto">
 
        <!-- Scrollviewer content -->

    </ScrollViewer>
</RefreshContainer>
```

### <a name="adding-pull-to-refresh-to-a-listview"></a><span data-ttu-id="b7dde-193">Hinzufügen von „Aktualisierung durch Ziehen“ zu einer ListView</span><span class="sxs-lookup"><span data-stu-id="b7dde-193">Adding pull-to-refresh to a ListView</span></span>

<span data-ttu-id="b7dde-194">Anhand dieses Beispiels wird veranschaulicht, wie Sie „Aktualisierung durch Ziehen“ mit einer Listenansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7dde-194">This example shows how to use pull-to-refresh with a list view.</span></span>

```xaml
<StackPanel Margin="0,40" Width="280">
    <CommandBar OverflowButtonVisibility="Collapsed">
        <AppBarButton x:Name="RefreshButton" Click="RefreshButtonClick"
                      Icon="Refresh" Label="Refresh"/>
        <CommandBar.Content>
            <TextBlock Text="List of items" 
                       Style="{StaticResource TitleTextBlockStyle}"
                       Margin="12,8"/>
        </CommandBar.Content>
    </CommandBar>

    <RefreshContainer x:Name="RefreshContainer">
        <ListView x:Name="ListView1" Height="400">
            <ListView.ItemTemplate>
                <DataTemplate x:DataType="local:ListItemData">
                    <Grid Height="80">
                        <Grid.RowDefinitions>
                            <RowDefinition Height="Auto" />
                            <RowDefinition Height="Auto" />
                            <RowDefinition Height="*" />
                        </Grid.RowDefinitions>
                        <TextBlock Text="{x:Bind Path=Header}"
                                   Style="{StaticResource SubtitleTextBlockStyle}"
                                   Grid.Row="0"/>
                        <TextBlock Text="{x:Bind Path=Date}"
                                   Style="{StaticResource CaptionTextBlockStyle}"
                                   Grid.Row="1"/>
                        <TextBlock Text="{x:Bind Path=Body}"
                                   Style="{StaticResource BodyTextBlockStyle}"
                                   Grid.Row="2"
                                   Margin="0,4,0,0" />
                    </Grid>
                </DataTemplate>
            </ListView.ItemTemplate>
        </ListView>
    </RefreshContainer>
</StackPanel>
```

```csharp
public sealed partial class MainPage : Page
{
    public ObservableCollection<ListItemData> Items { get; set; } 
        = new ObservableCollection<ListItemData>();

    public MainPage()
    {
        this.InitializeComponent();

        Loaded += MainPage_Loaded;
        ListView1.ItemsSource = Items;
    }

    private async void MainPage_Loaded(object sender, RoutedEventArgs e)
    {
        Loaded -= MainPage_Loaded;
        RefreshContainer.RefreshRequested += RefreshContainer_RefreshRequested;
        RefreshContainer.Visualizer.RefreshStateChanged += Visualizer_RefreshStateChanged;

        // Add some initial content to the list.
        await FetchAndInsertItemsAsync(2);
    }

    private void RefreshButtonClick(object sender, RoutedEventArgs e)
    {
        RefreshContainer.RequestRefresh();
    }

    private async void RefreshContainer_RefreshRequested(RefreshContainer sender, RefreshRequestedEventArgs args)
    {
        // Respond to a request by performing a refresh and using the deferral object.
        using (var RefreshCompletionDeferral = args.GetDeferral())
        {
            // Do some async operation to refresh the content

            await FetchAndInsertItemsAsync(3);

            // The 'using' statement ensures the deferral is marked as complete.
            // Otherwise, you'd call
            // RefreshCompletionDeferral.Complete();
            // RefreshCompletionDeferral.Dispose();
        }
    }

    private void Visualizer_RefreshStateChanged(RefreshVisualizer sender, RefreshStateChangedEventArgs args)
    {
        // Respond to visualizer state changes.
        // Disable the refresh button if the visualizer is refreshing.
        if (args.NewState == RefreshVisualizerState.Refreshing)
        {
            RefreshButton.IsEnabled = false;
        }
        else
        {
            RefreshButton.IsEnabled = true;
        }
    }

    // App specific code to get fresh data.
    private async Task FetchAndInsertItemsAsync(int updateCount)
    {
        for (int i = 0; i < updateCount; ++i)
        {
            // Simulate delay while we go fetch new items.
            await Task.Delay(1000);
            Items.Insert(0, GetNextItem());
        }
    }

    private ListItemData GetNextItem()
    {
        return new ListItemData()
        {
            Header = "Header " + DateTime.Now.Second.ToString(),
            Date = DateTime.Now.ToLongDateString(),
            Body = DateTime.Now.ToLongTimeString()
        };
    }
}

public class ListItemData
{
    public string Header { get; set; }
    public string Date { get; set; }
    public string Body { get; set; }
}
```

## <a name="related-articles"></a><span data-ttu-id="b7dde-195">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="b7dde-195">Related articles</span></span>

- [<span data-ttu-id="b7dde-196">Interaktionen per Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="b7dde-196">Touch interactions</span></span>](../input/touch-interactions.md)
- [<span data-ttu-id="b7dde-197">Listenansicht und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="b7dde-197">List view and grid view</span></span>](listview-and-gridview.md)
- [<span data-ttu-id="b7dde-198">Elementcontainer und Vorlagen</span><span class="sxs-lookup"><span data-stu-id="b7dde-198">Item containers and templates</span></span>](item-containers-templates.md)
- [<span data-ttu-id="b7dde-199">Ausdrucksanimationen</span><span class="sxs-lookup"><span data-stu-id="b7dde-199">Expression animations</span></span>](../../composition/composition-animation.md)
