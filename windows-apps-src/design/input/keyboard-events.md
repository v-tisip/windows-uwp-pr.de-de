---
author: Karl-Bridge-Microsoft
Description: Respond to keystroke actions from hardware or software keyboards in your apps using both keyboard and class event handlers.
title: Tastaturereignisse
ms.assetid: ac500772-d6ed-4a3a-825b-210a9c3c8f59
label: Keyboard events
template: detail.hbs
keywords: Tastatur, Gamepad, Fernbedienung, Barrierefreiheit, Navigation, Fokus, Text, Eingabe, Benutzerinteraktionen, NACH-OBEN-TASTE, NACH-UNTEN-TASTE
ms.author: kbridge
ms.date: 03/29/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
pm-contact: chigy
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 78448081b81e7e28c4b97fcfdd7aa71ae32aeb0c
ms.sourcegitcommit: e16c9845b52d5bd43fc02bbe92296a9682d96926
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "4957575"
---
# <a name="keyboard-events"></a><span data-ttu-id="56ded-103">Tastaturereignisse</span><span class="sxs-lookup"><span data-stu-id="56ded-103">Keyboard events</span></span>

## <a name="keyboard-events-and-focus"></a><span data-ttu-id="56ded-104">Tastaturereignisse und Fokus</span><span class="sxs-lookup"><span data-stu-id="56ded-104">Keyboard events and focus</span></span>

<span data-ttu-id="56ded-105">Die folgenden Tastaturereignisse können sowohl für Hardware- als auch für Touch-Bildschirmtastaturen eintreten.</span><span class="sxs-lookup"><span data-stu-id="56ded-105">The following keyboard events can occur for both hardware and touch keyboards.</span></span>

| <span data-ttu-id="56ded-106">Ereignis</span><span class="sxs-lookup"><span data-stu-id="56ded-106">Event</span></span>                                      | <span data-ttu-id="56ded-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="56ded-107">Description</span></span>                    |
|--------------------------------------------|--------------------------------|
| [**<span data-ttu-id="56ded-108">KeyDown</span><span class="sxs-lookup"><span data-stu-id="56ded-108">KeyDown</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208941) | <span data-ttu-id="56ded-109">Tritt auf, wenn eine Taste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="56ded-109">Occurs when a key is pressed.</span></span>  |
| [**<span data-ttu-id="56ded-110">KeyUp</span><span class="sxs-lookup"><span data-stu-id="56ded-110">KeyUp</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208942)     | <span data-ttu-id="56ded-111">Tritt auf, wenn eine Taste losgelassen wird.</span><span class="sxs-lookup"><span data-stu-id="56ded-111">Occurs when a key is released.</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="56ded-112">Einige Windows-Runtime-Steuerelemente verarbeiten Eingabeereignisse intern.</span><span class="sxs-lookup"><span data-stu-id="56ded-112">Some Windows Runtime controls handle input events internally.</span></span> <span data-ttu-id="56ded-113">In diesen Fällen tritt ein Eingabeereignis möglicherweise nicht ein, weil der Ereignislistener den zugehörigen Handler nicht aufruft.</span><span class="sxs-lookup"><span data-stu-id="56ded-113">In these cases, it might appear that an input event doesn't occur because your event listener doesn't invoke the associated handler.</span></span> <span data-ttu-id="56ded-114">Normalerweise wird diese Tastenteilmenge vom Klassenhandler verarbeitet, um eine integrierte Unterstützung für die Barrierefreiheit des einfachen Tastaturzugriffs bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="56ded-114">Typically, this subset of keys is processed by the class handler to provide built in support of basic keyboard accessibility.</span></span> <span data-ttu-id="56ded-115">Die Klasse [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265) setzt beispielsweise die [**OnKeyDown**](https://msdn.microsoft.com/library/windows/apps/hh967982)-Ereignisse für die LEERTASTE und die EINGABETASTE (sowie für [**OnPointerPressed**](https://msdn.microsoft.com/library/windows/apps/hh967989)) außer Kraft und leitet sie an das Ereignis [**Click**](https://msdn.microsoft.com/library/windows/apps/br227737) des Steuerelements weiter.</span><span class="sxs-lookup"><span data-stu-id="56ded-115">For example, the [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265) class overrides the [**OnKeyDown**](https://msdn.microsoft.com/library/windows/apps/hh967982) events for both the Space key and the Enter key (as well as [**OnPointerPressed**](https://msdn.microsoft.com/library/windows/apps/hh967989)) and routes them to the [**Click**](https://msdn.microsoft.com/library/windows/apps/br227737) event of the control.</span></span> <span data-ttu-id="56ded-116">Wenn von der Steuerelementklasse ein Tastendruck verarbeitet wird, werden die Ereignisse [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) und [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) nicht ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="56ded-116">When a key press is handled by the control class, the [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) and [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) events are not raised.</span></span>  
> <span data-ttu-id="56ded-117">Dadurch wird ein integriertes Tastaturäquivalent zum Aufrufen der Schaltfläche bereitgestellt, das dem Tippen mit dem Finger oder Klicken mit einer Maus ähnelt.</span><span class="sxs-lookup"><span data-stu-id="56ded-117">This provides a built-in keyboard equivalent for invoking the button, similar to tapping it with a finger or clicking it with a mouse.</span></span> <span data-ttu-id="56ded-118">Andere Tasten als die LEER- oder EINGABETASTE lösen die Ereignisse [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) und [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) trotzdem aus.</span><span class="sxs-lookup"><span data-stu-id="56ded-118">Keys other than Space or Enter still fire [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) and [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) events.</span></span> <span data-ttu-id="56ded-119">Weitere Informationen zur Funktionsweise der klassenbasierten Verarbeitung von Ereignissen (insbesondere den Abschnitt „Eingabe-Ereignishandler in Steuerelementen“) finden Sie unter [Übersicht über Ereignisse und Routingereignisse](https://msdn.microsoft.com/library/windows/apps/mt185584).</span><span class="sxs-lookup"><span data-stu-id="56ded-119">For more info about how class-based handling of events works (specifically, the "Input event handlers in controls" section), see [Events and routed events overview](https://msdn.microsoft.com/library/windows/apps/mt185584).</span></span>


<span data-ttu-id="56ded-120">Die Steuerelemente der UI generieren nur dann Tastaturereignisse, wenn sie den Eingabefokus aufweisen.</span><span class="sxs-lookup"><span data-stu-id="56ded-120">Controls in your UI generate keyboard events only when they have input focus.</span></span> <span data-ttu-id="56ded-121">Ein einzelnes Steuerelement steht im Fokus, wenn Benutzer im Layout auf das Steuerelement klicken oder tippen oder mit der TAB-Taste im Inhaltsbereich eine Aktivierreihenfolge durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="56ded-121">An individual control gains focus when the user clicks or taps directly on that control in the layout, or uses the Tab key to step into a tab sequence within the content area.</span></span>

<span data-ttu-id="56ded-122">Sie können auch die [**Focus**](https://msdn.microsoft.com/library/windows/apps/hh702161)-Methode eines Steuerelements aufrufen, um den Fokus zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="56ded-122">You can also call a control's [**Focus**](https://msdn.microsoft.com/library/windows/apps/hh702161) method to force focus.</span></span> <span data-ttu-id="56ded-123">Dies ist notwendig, wenn Sie Tastenkombinationen implementieren, da der Tastaturfokus beim Laden der UI nicht standardmäßig festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="56ded-123">This is necessary when you implement shortcut keys, because keyboard focus is not set by default when your UI loads.</span></span> <span data-ttu-id="56ded-124">Weitere Informationen finden Sie weiter unten in diesem Thema unter **Beispiel für Tastenkombinationen**.</span><span class="sxs-lookup"><span data-stu-id="56ded-124">For more info, see the **Shortcut keys example** later in this topic.</span></span>

<span data-ttu-id="56ded-125">Damit ein Steuerelement den Eingabefokus erhält, muss es aktiviert und sichtbar sein. Außerdem müssen die Eigenschaften [**IsTabStop**](https://msdn.microsoft.com/library/windows/apps/br209422) und [**HitTestVisible**](https://msdn.microsoft.com/library/windows/apps/br208933) den Wert **true** haben.</span><span class="sxs-lookup"><span data-stu-id="56ded-125">For a control to receive input focus, it must be enabled, visible, and have [**IsTabStop**](https://msdn.microsoft.com/library/windows/apps/br209422) and [**HitTestVisible**](https://msdn.microsoft.com/library/windows/apps/br208933) property values of **true**.</span></span> <span data-ttu-id="56ded-126">Dies ist der Standardzustand der meisten Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="56ded-126">This is the default state for most controls.</span></span> <span data-ttu-id="56ded-127">Wenn ein Steuerelement den Eingabefokus aufweist, kann es Tastatureingabeereignisse auslösen und auf diese reagieren. Dies wird weiter unten in diesem Thema beschrieben.</span><span class="sxs-lookup"><span data-stu-id="56ded-127">When a control has input focus, it can raise and respond to keyboard input events as described later in this topic.</span></span> <span data-ttu-id="56ded-128">Mit den Ereignissen [**GotFocus**](https://msdn.microsoft.com/library/windows/apps/br208927) und [**LostFocus**](https://msdn.microsoft.com/library/windows/apps/br208943) können Sie außerdem reagieren, wenn ein Steuerelement den Fokus erhält oder verliert.</span><span class="sxs-lookup"><span data-stu-id="56ded-128">You can also respond to a control that is receiving or losing focus by handling the [**GotFocus**](https://msdn.microsoft.com/library/windows/apps/br208927) and [**LostFocus**](https://msdn.microsoft.com/library/windows/apps/br208943) events.</span></span>

<span data-ttu-id="56ded-129">Standardmäßig entspricht die Aktivierreihenfolge von Steuerelementen der Reihenfolge, in der sie in der Extensible Application Markup Language (XAML) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="56ded-129">By default, the tab sequence of controls is the order in which they appear in the Extensible Application Markup Language (XAML).</span></span> <span data-ttu-id="56ded-130">Mit der Eigenschaft [**TabIndex**](https://msdn.microsoft.com/library/windows/apps/br209461) können Sie diese Reihenfolge jedoch ändern.</span><span class="sxs-lookup"><span data-stu-id="56ded-130">However, you can modify this order by using the [**TabIndex**](https://msdn.microsoft.com/library/windows/apps/br209461) property.</span></span> <span data-ttu-id="56ded-131">Weitere Informationen finden Sie unter [Implementieren von Barrierefreiheit für den Tastaturzugriff](https://msdn.microsoft.com/library/windows/apps/hh868161).</span><span class="sxs-lookup"><span data-stu-id="56ded-131">For more info, see [Implementing keyboard accessibility](https://msdn.microsoft.com/library/windows/apps/hh868161).</span></span>

## <a name="keyboard-event-handlers"></a><span data-ttu-id="56ded-132">Tastaturereignishandler</span><span class="sxs-lookup"><span data-stu-id="56ded-132">Keyboard event handlers</span></span>


<span data-ttu-id="56ded-133">Ein Eingabe-Ereignishandler implementiert einen Delegaten, der die folgenden Informationen bereitstellt:</span><span class="sxs-lookup"><span data-stu-id="56ded-133">An input event handler implements a delegate that provides the following information:</span></span>

-   <span data-ttu-id="56ded-134">Den Sender des Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="56ded-134">The sender of the event.</span></span> <span data-ttu-id="56ded-135">Der Sender meldet das Objekt, dem der Ereignishandler angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="56ded-135">The sender reports the object where the event handler is attached.</span></span>
-   <span data-ttu-id="56ded-136">Ereignisdaten.</span><span class="sxs-lookup"><span data-stu-id="56ded-136">Event data.</span></span> <span data-ttu-id="56ded-137">Bei Tastaturereignissen sind diese Daten eine Instanz von [**KeyRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943072).</span><span class="sxs-lookup"><span data-stu-id="56ded-137">For keyboard events, that data will be an instance of [**KeyRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943072).</span></span> <span data-ttu-id="56ded-138">[**KeyEventHandler**](https://msdn.microsoft.com/library/windows/apps/br227904) ist der Delegat für Handler.</span><span class="sxs-lookup"><span data-stu-id="56ded-138">The delegate for handlers is [**KeyEventHandler**](https://msdn.microsoft.com/library/windows/apps/br227904).</span></span> <span data-ttu-id="56ded-139">Die wichtigsten Eigenschaften von **KeyRoutedEventArgs** für die meisten Handler-Szenarien sind [**Key**](https://msdn.microsoft.com/library/windows/apps/hh943074) und möglicherweise [**KeyStatus**](https://msdn.microsoft.com/library/windows/apps/hh943075).</span><span class="sxs-lookup"><span data-stu-id="56ded-139">The most relevant properties of **KeyRoutedEventArgs** for most handler scenarios are [**Key**](https://msdn.microsoft.com/library/windows/apps/hh943074) and possibly [**KeyStatus**](https://msdn.microsoft.com/library/windows/apps/hh943075).</span></span>
-   <span data-ttu-id="56ded-140">[**OriginalSource**](https://msdn.microsoft.com/library/windows/apps/br208810).</span><span class="sxs-lookup"><span data-stu-id="56ded-140">[**OriginalSource**](https://msdn.microsoft.com/library/windows/apps/br208810).</span></span> <span data-ttu-id="56ded-141">Da es sich bei Tastaturereignissen um Routingereignisse handelt, stellen die Ereignisdaten **OriginalSource** bereit.</span><span class="sxs-lookup"><span data-stu-id="56ded-141">Because the keyboard events are routed events, the event data provides **OriginalSource**.</span></span> <span data-ttu-id="56ded-142">Wenn Sie bewusst das Bubbling von Ereignissen in der Objektstruktur zulassen, ist **OriginalSource** manchmal eher das fragliche Objekt als der Sender.</span><span class="sxs-lookup"><span data-stu-id="56ded-142">If you deliberately allow events to bubble up through an object tree, **OriginalSource** is sometimes the object of concern rather than sender.</span></span> <span data-ttu-id="56ded-143">Das hängt jedoch vom Design ab.</span><span class="sxs-lookup"><span data-stu-id="56ded-143">However, that depends on your design.</span></span> <span data-ttu-id="56ded-144">Weitere Informationen dazu, wie Sie **OriginalSource** anstelle des Senders verwenden können, finden Sie im Abschnitt „Routingereignisse der Tastatur“ in diesem Thema oder unter [Übersicht über Ereignisse und Routingereignisse](https://msdn.microsoft.com/library/windows/apps/mt185584).</span><span class="sxs-lookup"><span data-stu-id="56ded-144">For more information about how you might use **OriginalSource** rather than sender, see the "Keyboard Routed Events" section of this topic, or [Events and routed events overview](https://msdn.microsoft.com/library/windows/apps/mt185584).</span></span>

### <a name="attaching-a-keyboard-event-handler"></a><span data-ttu-id="56ded-145">Anfügen eines Tastaturereignishandlers</span><span class="sxs-lookup"><span data-stu-id="56ded-145">Attaching a keyboard event handler</span></span>

<span data-ttu-id="56ded-146">Sie können Funktionen von Tastatur-Ereignishandlern für jedes Objekt anfügen, das das Ereignis als Member einschließt.</span><span class="sxs-lookup"><span data-stu-id="56ded-146">You can attach keyboard event-handler functions for any object that includes the event as a member.</span></span> <span data-ttu-id="56ded-147">Dazu gehört jede von [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) abgeleitete Klasse.</span><span class="sxs-lookup"><span data-stu-id="56ded-147">This includes any [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) derived class.</span></span> <span data-ttu-id="56ded-148">Das folgende XAML-Beispiel zeigt, wie Sie Handler für das Ereignis [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) für [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704) anfügen.</span><span class="sxs-lookup"><span data-stu-id="56ded-148">The following XAML example shows how to attach handlers for the [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) event for a [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704).</span></span>

```xaml
<Grid KeyUp="Grid_KeyUp">
  ...
</Grid>
```

<span data-ttu-id="56ded-149">Sie können einen Ereignishandler auch manuell im Code anfügen.</span><span class="sxs-lookup"><span data-stu-id="56ded-149">You can also attach an event handler in code.</span></span> <span data-ttu-id="56ded-150">Weitere Informationen finden Sie unter [Übersicht über Ereignisse und Routingereignisse](https://msdn.microsoft.com/library/windows/apps/mt185584).</span><span class="sxs-lookup"><span data-stu-id="56ded-150">For more info, see [Events and routed events overview](https://msdn.microsoft.com/library/windows/apps/mt185584).</span></span>

### <a name="defining-a-keyboard-event-handler"></a><span data-ttu-id="56ded-151">Definieren eines Tastaturereignishandlers</span><span class="sxs-lookup"><span data-stu-id="56ded-151">Defining a keyboard event handler</span></span>

<span data-ttu-id="56ded-152">Das folgende Beispiel zeigt eine unvollständige Ereignishandler-Definition für den im vorherigen Beispiel hinzugefügten Ereignishandler [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942).</span><span class="sxs-lookup"><span data-stu-id="56ded-152">The following example shows the incomplete event handler definition for the [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) event handler that was attached in the preceding example.</span></span>

```csharp
void Grid_KeyUp(object sender, KeyRoutedEventArgs e)
{
    //handling code here
}
```

```vb
Private Sub Grid_KeyUp(ByVal sender As Object, ByVal e As KeyRoutedEventArgs)
    ' handling code here
End Sub
```

```c++
void MyProject::MainPage::Grid_KeyUp(
  Platform::Object^ sender,
  Windows::UI::Xaml::Input::KeyRoutedEventArgs^ e)
  {
      //handling code here
  }
```

### <a name="using-keyroutedeventargs"></a><span data-ttu-id="56ded-153">Verwenden von KeyRoutedEventArgs</span><span class="sxs-lookup"><span data-stu-id="56ded-153">Using KeyRoutedEventArgs</span></span>

<span data-ttu-id="56ded-154">Alle Tastaturereignisse verwenden [**KeyRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943072) für Ereignisdaten. **KeyRoutedEventArgs** enthält die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="56ded-154">All keyboard events use [**KeyRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943072) for event data, and **KeyRoutedEventArgs** contains the following properties:</span></span>

-   [**<span data-ttu-id="56ded-155">Key</span><span class="sxs-lookup"><span data-stu-id="56ded-155">Key</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh943074)
-   [**<span data-ttu-id="56ded-156">KeyStatus</span><span class="sxs-lookup"><span data-stu-id="56ded-156">KeyStatus</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh943075)
-   [**<span data-ttu-id="56ded-157">Handled</span><span class="sxs-lookup"><span data-stu-id="56ded-157">Handled</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh943073)
-   <span data-ttu-id="56ded-158">[**OriginalSource**](https://msdn.microsoft.com/library/windows/apps/br208810) (geerbt von [**RoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br208809))</span><span class="sxs-lookup"><span data-stu-id="56ded-158">[**OriginalSource**](https://msdn.microsoft.com/library/windows/apps/br208810) (inherited from [**RoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br208809))</span></span>

### <a name="key"></a><span data-ttu-id="56ded-159">Key</span><span class="sxs-lookup"><span data-stu-id="56ded-159">Key</span></span>

<span data-ttu-id="56ded-160">Das Ereignis [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) wird ausgelöst, wenn eine Taste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="56ded-160">The [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) event is raised if a key is pressed.</span></span> <span data-ttu-id="56ded-161">Entsprechend wird das Ereignis [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) ausgelöst, wenn eine Taste losgelassen wird.</span><span class="sxs-lookup"><span data-stu-id="56ded-161">Likewise, [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) is raised if a key is released.</span></span> <span data-ttu-id="56ded-162">In der Regel lauschen Sie auf Ereignisse, um einen bestimmten Tastenwert zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="56ded-162">Usually, you listen to the events to process a specific key value.</span></span> <span data-ttu-id="56ded-163">Überprüfen Sie den Wert [**Key**](https://msdn.microsoft.com/library/windows/apps/hh943074) in den Ereignisdaten, um die gedrückte oder losgelassene Taste zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="56ded-163">To determine which key is pressed or released, check the [**Key**](https://msdn.microsoft.com/library/windows/apps/hh943074) value in the event data.</span></span> <span data-ttu-id="56ded-164">**Key** gibt einen [**VirtualKey**](https://msdn.microsoft.com/library/windows/apps/br241812)-Wert zurück.</span><span class="sxs-lookup"><span data-stu-id="56ded-164">**Key** returns a [**VirtualKey**](https://msdn.microsoft.com/library/windows/apps/br241812) value.</span></span> <span data-ttu-id="56ded-165">Die **VirtualKey**-Enumeration umfasst alle unterstützten Tasten.</span><span class="sxs-lookup"><span data-stu-id="56ded-165">The **VirtualKey** enumeration includes all the supported keys.</span></span>

### <a name="modifier-keys"></a><span data-ttu-id="56ded-166">Zusatztasten</span><span class="sxs-lookup"><span data-stu-id="56ded-166">Modifier keys</span></span>

<span data-ttu-id="56ded-167">Zusatztasten sind Tasten wie beispielsweise STRG oder UMSCHALT, die Benutzer normalerweise in Kombination mit anderen Tasten drücken.</span><span class="sxs-lookup"><span data-stu-id="56ded-167">Modifier keys are keys such as Ctrl or Shift that users typically press in combination with other keys.</span></span> <span data-ttu-id="56ded-168">Ihre App kann diese Kombinationen als Tastenkombinationen zum Aufrufen von App-Befehlen nutzen.</span><span class="sxs-lookup"><span data-stu-id="56ded-168">Your app can use these combinations as keyboard shortcuts to invoke app commands.</span></span>

<span data-ttu-id="56ded-169">Sie erkennen Tastenkombinationen mithilfe des Codes in den Ereignishandlern [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) und [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942).</span><span class="sxs-lookup"><span data-stu-id="56ded-169">You detect shortcut key combinations by using code in your [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) and [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) event handlers.</span></span> <span data-ttu-id="56ded-170">Sie können dann den Zustand "Gedrückt" der Zusatztasten überwachen, die für Sie von Interesse sind.</span><span class="sxs-lookup"><span data-stu-id="56ded-170">You can then track the pressed state of the modifier keys you are interested in.</span></span> <span data-ttu-id="56ded-171">Wenn für eine Nichtzusatztaste ein Tastaturereignis auftritt, können Sie überprüfen, ob gleichzeitig eine Zusatztaste gedrückt wurde.</span><span class="sxs-lookup"><span data-stu-id="56ded-171">When a keyboard event occurs for a non-modifier key, you can check whether a modifier key is in the pressed state at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="56ded-172">Die ALT-Taste wird durch den Wert **VirtualKey.Menu** dargestellt.</span><span class="sxs-lookup"><span data-stu-id="56ded-172">The Alt key is represented by the **VirtualKey.Menu** value.</span></span>

 

### <a name="shortcut-keys-example"></a><span data-ttu-id="56ded-173">Beispiel für Tastenkombinationen</span><span class="sxs-lookup"><span data-stu-id="56ded-173">Shortcut keys example</span></span>


<span data-ttu-id="56ded-174">Im folgenden Beispiel wird die Implementierung von Tastenkombinationen gezeigt.</span><span class="sxs-lookup"><span data-stu-id="56ded-174">The following example demonstrates how to implement shortcut keys.</span></span> <span data-ttu-id="56ded-175">In diesem Beispiel können Benutzer die Medienwiedergabe mit den Schaltflächen „Play“, „Pause“ und „Stop“ oder mit den Tastenkombinationen STRG+P, STRG+A und STRG+S steuern.</span><span class="sxs-lookup"><span data-stu-id="56ded-175">In this example, users can control media playback using Play, Pause, and Stop buttons or Ctrl+P, Ctrl+A, and Ctrl+S keyboard shortcuts.</span></span> <span data-ttu-id="56ded-176">Das Schaltflächen-XAML zeigt die Tastenkombinationen in Form von QuickInfos und [**AutomationProperties**](https://msdn.microsoft.com/library/windows/apps/br209081)-Eigenschaften in den Schaltflächenbeschriftungen.</span><span class="sxs-lookup"><span data-stu-id="56ded-176">The button XAML shows the shortcuts by using tooltips and [**AutomationProperties**](https://msdn.microsoft.com/library/windows/apps/br209081) properties in the button labels.</span></span> <span data-ttu-id="56ded-177">Diese Selbstdokumentation ist wichtig, um die Benutzerfreundlichkeit und Barrierefreiheit der App zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="56ded-177">This self-documentation is important to increase the usability and accessibility of your app.</span></span> <span data-ttu-id="56ded-178">Weitere Informationen finden Sie unter [Barrierefreiheit für den Tastaturzugriff](https://msdn.microsoft.com/library/windows/apps/mt244347).</span><span class="sxs-lookup"><span data-stu-id="56ded-178">For more info, see [Keyboard accessibility](https://msdn.microsoft.com/library/windows/apps/mt244347).</span></span>

<span data-ttu-id="56ded-179">Beachten Sie auch, dass die Seite den Eingabefokus auf sich selbst festlegt, wenn sie geladen wird.</span><span class="sxs-lookup"><span data-stu-id="56ded-179">Note also that the page sets input focus to itself when it is loaded.</span></span> <span data-ttu-id="56ded-180">Ohne diesen Schritt hat kein Steuerelement anfangs den Eingabefokus, und die App löst erst Eingabeereignisse aus, wenn Benutzer den Eingabefokus manuell festlegen (beispielsweise durch Drücken der TAB-TASTE oder Klicken auf ein Steuerelement).</span><span class="sxs-lookup"><span data-stu-id="56ded-180">Without this step, no control has initial input focus, and the app does not raise input events until the user sets the input focus manually (for example, by tabbing to or clicking a control).</span></span>

```xaml
<Grid KeyDown="Grid_KeyDown">

  <Grid.RowDefinitions>
    <RowDefinition Height="Auto" />
    <RowDefinition Height="Auto" />
  </Grid.RowDefinitions>

  <MediaElement x:Name="DemoMovie" Source="xbox.wmv"
    Width="500" Height="500" Margin="20" HorizontalAlignment="Center" />

  <StackPanel Grid.Row="1" Margin="10"
    Orientation="Horizontal" HorizontalAlignment="Center">

    <Button x:Name="PlayButton" Click="MediaButton_Click"
      ToolTipService.ToolTip="Shortcut key: Ctrl+P"
      AutomationProperties.AcceleratorKey="Control P">
      <TextBlock>Play</TextBlock>
    </Button>

    <Button x:Name="PauseButton" Click="MediaButton_Click"
      ToolTipService.ToolTip="Shortcut key: Ctrl+A"
      AutomationProperties.AcceleratorKey="Control A">
      <TextBlock>Pause</TextBlock>
    </Button>

    <Button x:Name="StopButton" Click="MediaButton_Click"
      ToolTipService.ToolTip="Shortcut key: Ctrl+S"
      AutomationProperties.AcceleratorKey="Control S">
      <TextBlock>Stop</TextBlock>
    </Button>

  </StackPanel>

</Grid>
```

```c++
//showing implementations but not header definitions
void MainPage::OnNavigatedTo(NavigationEventArgs^ e)
{
    (void) e;    // Unused parameter
    this->Loaded+=ref new RoutedEventHandler(this,&amp;MainPage::ProgrammaticFocus);
}
void MainPage::ProgrammaticFocus(Object^ sender, RoutedEventArgs^ e) {
    this->Focus(Windows::UI::Xaml::FocusState::Programmatic);
}

void KeyboardSupport::MainPage::MediaButton_Click(Platform::Object^ sender, Windows::UI::Xaml::RoutedEventArgs^ e)
{
    FrameworkElement^ fe = safe_cast<FrameworkElement^>(sender);
    if (fe->Name == "PlayButton") {DemoMovie->Play();}
    if (fe->Name == "PauseButton") {DemoMovie->Pause();}
    if (fe->Name == "StopButton") {DemoMovie->Stop();}
}


bool KeyboardSupport::MainPage::IsCtrlKeyPressed()
{
    auto ctrlState = CoreWindow::GetForCurrentThread()->GetKeyState(VirtualKey::Control);
    return (ctrlState & CoreVirtualKeyStates::Down) == CoreVirtualKeyStates::Down;
}

void KeyboardSupport::MainPage::Grid_KeyDown(Platform::Object^ sender, Windows::UI::Xaml::Input::KeyRoutedEventArgs^ e)
{
    if (e->Key == VirtualKey::Control) isCtrlKeyPressed = true;
}


void KeyboardSupport::MainPage::Grid_KeyUp(Platform::Object^ sender, Windows::UI::Xaml::Input::KeyRoutedEventArgs^ e)
{
    if (IsCtrlKeyPressed()) {
        if (e->Key==VirtualKey::P) { DemoMovie->Play(); }
        if (e->Key==VirtualKey::A) { DemoMovie->Pause(); }
        if (e->Key==VirtualKey::S) { DemoMovie->Stop(); }
    }
}
```

```csharp
protected override void OnNavigatedTo(NavigationEventArgs e)
{
    // Set the input focus to ensure that keyboard events are raised.
    this.Loaded += delegate { this.Focus(FocusState.Programmatic); };
}

private void MediaButton_Click(object sender, RoutedEventArgs e)
{
    switch ((sender as Button).Name)
    {
        case "PlayButton": DemoMovie.Play(); break;
        case "PauseButton": DemoMovie.Pause(); break;
        case "StopButton": DemoMovie.Stop(); break;
    }
}

private static bool IsCtrlKeyPressed()
{
    var ctrlState = CoreWindow.GetForCurrentThread().GetKeyState(VirtualKey.Control);
    return (ctrlState & CoreVirtualKeyStates.Down) == CoreVirtualKeyStates.Down;
}

private void Grid_KeyDown(object sender, KeyRoutedEventArgs e)
{
    if (IsCtrlKeyPressed())
    {
        switch (e.Key)
        {
            case VirtualKey.P: DemoMovie.Play(); break;
            case VirtualKey.A: DemoMovie.Pause(); break;
            case VirtualKey.S: DemoMovie.Stop(); break;
        }
    }
}
```

```VisualBasic
Private isCtrlKeyPressed As Boolean
Protected Overrides Sub OnNavigatedTo(e As Navigation.NavigationEventArgs)

End Sub

Private Function IsCtrlKeyPressed As Boolean
    Dim ctrlState As CoreVirtualKeyStates = CoreWindow.GetForCurrentThread().GetKeyState(VirtualKey.Control);
    Return (ctrlState & CoreVirtualKeyStates.Down) == CoreVirtualKeyStates.Down;
End Function

Private Sub Grid_KeyDown(sender As Object, e As KeyRoutedEventArgs)
    If IsCtrlKeyPressed() Then
        Select Case e.Key
            Case Windows.System.VirtualKey.P
                DemoMovie.Play()
            Case Windows.System.VirtualKey.A
                DemoMovie.Pause()
            Case Windows.System.VirtualKey.S
                DemoMovie.Stop()
        End Select
    End If
End Sub

Private Sub MediaButton_Click(sender As Object, e As RoutedEventArgs)
    Dim fe As FrameworkElement = CType(sender, FrameworkElement)
    Select Case fe.Name
        Case "PlayButton"
            DemoMovie.Play()
        Case "PauseButton"
            DemoMovie.Pause()
        Case "StopButton"
            DemoMovie.Stop()
    End Select
End Sub
```

> [!NOTE]
> <span data-ttu-id="56ded-181">Durch das Festlegen der [**AutomationProperties.AcceleratorKey**](https://msdn.microsoft.com/library/windows/apps/hh759762)- oder [**AutomationProperties.AccessKey**](https://msdn.microsoft.com/library/windows/apps/hh759763)-Eigenschaft in XAML werden Zeichenfolgeninformationen zum Dokumentieren der Tastenkombination zum Auslösen der jeweiligen Aktion bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="56ded-181">Setting [**AutomationProperties.AcceleratorKey**](https://msdn.microsoft.com/library/windows/apps/hh759762) or [**AutomationProperties.AccessKey**](https://msdn.microsoft.com/library/windows/apps/hh759763) in XAML provides string information, which documents the shortcut key for invoking that particular action.</span></span> <span data-ttu-id="56ded-182">Die Informationen werden von Microsoft-Benutzeroberflächenautomatisierungsclients wie der Sprachausgabe erfasst und normalerweise direkt für den Benutzer bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="56ded-182">The information is captured by Microsoft UI Automation clients such as Narrator, and is typically provided directly to the user.</span></span>
>
> <span data-ttu-id="56ded-183">Mit dem Festlegen der Eigenschaft **AutomationProperties.AcceleratorKey** oder **AutomationProperties.AccessKey** ist keine eigene Aktion verknüpft.</span><span class="sxs-lookup"><span data-stu-id="56ded-183">Setting **AutomationProperties.AcceleratorKey** or **AutomationProperties.AccessKey** does not have any action on its own.</span></span> <span data-ttu-id="56ded-184">Sie müssen weiterhin Handler für [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941)- oder [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942)-Ereignisse anhängen, um das Verhalten der Tastenkombination tatsächlich in die App zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="56ded-184">You will still need to attach handlers for [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) or [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) events in order to actually implement the keyboard shortcut behavior in your app.</span></span> <span data-ttu-id="56ded-185">Außerdem wird der Unterstrichzusatz für eine Zugriffstaste nicht automatisch bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="56ded-185">Also, the underline text decoration for an access key is not provided automatically.</span></span> <span data-ttu-id="56ded-186">Sie müssen den Text für die jeweilige Taste in Ihrem mnemonischen Zeichen explizit als [**Underline**](https://msdn.microsoft.com/library/windows/apps/br209982)-Formatierung unterstreichen, wenn in der UI unterstrichener Text angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="56ded-186">You must explicitly underline the text for the specific key in your mnemonic as inline [**Underline**](https://msdn.microsoft.com/library/windows/apps/br209982) formatting if you wish to show underlined text in the UI.</span></span>

 

## <a name="keyboard-routed-events"></a><span data-ttu-id="56ded-187">Routingereignisse der Tastatur</span><span class="sxs-lookup"><span data-stu-id="56ded-187">Keyboard routed events</span></span>


<span data-ttu-id="56ded-188">Bestimmte Ereignisse gelten als Routingereignisse, wie z.B. [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) und [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942).</span><span class="sxs-lookup"><span data-stu-id="56ded-188">Certain events are routed events, including [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) and [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942).</span></span> <span data-ttu-id="56ded-189">Routingereignisse verwenden die Bubbling-Routingstrategie.</span><span class="sxs-lookup"><span data-stu-id="56ded-189">Routed events use the bubbling routing strategy.</span></span> <span data-ttu-id="56ded-190">Bei der Bubbling-Routingstrategie geht ein Ereignis von einem untergeordneten Objekt aus und wird jeweils an die übergeordneten Objekte in der Struktur weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="56ded-190">The bubbling routing strategy means that an event originates from a child object and is then routed up to successive parent objects in the object tree.</span></span> <span data-ttu-id="56ded-191">Dadurch ergibt sich eine weitere Möglichkeit, dasselbe Ereignis zu behandeln und mit denselben Ereignisdaten zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="56ded-191">This presents another opportunity to handle the same event and interact with the same event data.</span></span>

<span data-ttu-id="56ded-192">Im folgenden XAML-Beispiel werden [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942)-Ereignisse für ein [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267)-Objekt und zwei [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265)-Objekte definiert.</span><span class="sxs-lookup"><span data-stu-id="56ded-192">Consider the following XAML example, which handles [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) events for a [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267) and two [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265) objects.</span></span> <span data-ttu-id="56ded-193">Wenn Sie in diesem Fall eine Taste loslassen, während der Fokus auf einem der **Button**-Objekte liegt, wird das Ereignis **KeyUp** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="56ded-193">In this case, if you release a key while focus is held by either **Button** object, it raises the **KeyUp** event.</span></span> <span data-ttu-id="56ded-194">Das Ereignis wird per Bubbling an die übergeordnete **Canvas** weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="56ded-194">The event is then bubbled up to the parent **Canvas**.</span></span>

```xaml
<StackPanel KeyUp="StackPanel_KeyUp">
  <Button Name="ButtonA" Content="Button A"/>
  <Button Name="ButtonB" Content="Button B"/>
  <TextBlock Name="statusTextBlock"/>
</StackPanel>
```

<span data-ttu-id="56ded-195">Das folgende Beispiel zeigt, wie der Ereignishandler [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) für den entsprechenden XAML-Inhalt im vorherigen Beispiel implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="56ded-195">The following example shows how to implement the [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) event handler for the corresponding XAML content in the preceding example.</span></span>

```csharp
void StackPanel_KeyUp(object sender, KeyRoutedEventArgs e)
{
    statusTextBlock.Text = String.Format(
        "The key {0} was pressed while focus was on {1}",
        e.Key.ToString(), (e.OriginalSource as FrameworkElement).Name);
}
```

<span data-ttu-id="56ded-196">Beachten Sie die Verwendung der Eigenschaft [**OriginalSource**](https://msdn.microsoft.com/library/windows/apps/br208810) im vorherigen Handler.</span><span class="sxs-lookup"><span data-stu-id="56ded-196">Notice the use of the [**OriginalSource**](https://msdn.microsoft.com/library/windows/apps/br208810) property in the preceding handler.</span></span> <span data-ttu-id="56ded-197">Hier meldet **OriginalSource** das Objekt, das das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="56ded-197">Here, **OriginalSource** reports the object that raised the event.</span></span> <span data-ttu-id="56ded-198">Bei dem Objekt kann es sich nicht um [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/br209635) handeln, da **StackPanel** kein Steuerelement ist und nicht im Fokus stehen kann.</span><span class="sxs-lookup"><span data-stu-id="56ded-198">The object could not be the [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/br209635) because the **StackPanel** is not a control and cannot have focus.</span></span> <span data-ttu-id="56ded-199">Nur eine der beiden Schaltflächen in **StackPanel** kann das Ereignis ausgelöst haben. Die Frage ist, welche?</span><span class="sxs-lookup"><span data-stu-id="56ded-199">Only one of the two buttons within the **StackPanel** could possibly have raised the event, but which one?</span></span> <span data-ttu-id="56ded-200">Mit **OriginalSource** können Sie das tatsächliche Quellobjekt des Ereignisses unterscheiden, wenn Sie das Ereignis für ein übergeordnetes Objekt verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="56ded-200">You use **OriginalSource** to distinguish the actual event source object, if you are handling the event on a parent object.</span></span>

### <a name="the-handled-property-in-event-data"></a><span data-ttu-id="56ded-201">Die Handled-Eigenschaft in Ereignisdaten</span><span class="sxs-lookup"><span data-stu-id="56ded-201">The Handled property in event data</span></span>

<span data-ttu-id="56ded-202">Je nach Ihrer Strategie für die Ereignisverarbeitung empfiehlt sich vielleicht nur ein Ereignishandler, der auf ein Bubbling-Ereignis reagiert.</span><span class="sxs-lookup"><span data-stu-id="56ded-202">Depending on your event handling strategy, you might want only one event handler to react to a bubbling event.</span></span> <span data-ttu-id="56ded-203">Wenn beispielsweise ein bestimmter [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942)-Handler an eines der [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265)-Steuerelemente angefügt ist, hat dieses zuerst Gelegenheit, das Ereignis zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="56ded-203">For instance, if you have a specific [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) handler attached to one of the [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265) controls, it would have the first opportunity to handle that event.</span></span> <span data-ttu-id="56ded-204">In diesem Fall ist es nicht sinnvoll, dass auch das übergeordnete Panel das Ereignis behandelt.</span><span class="sxs-lookup"><span data-stu-id="56ded-204">In this case, you might not want the parent panel to also handle the event.</span></span> <span data-ttu-id="56ded-205">Verwenden Sie in diesem Szenario die Eigenschaft [**Handled**](https://msdn.microsoft.com/library/windows/apps/hh943073) in den Ereignisdaten.</span><span class="sxs-lookup"><span data-stu-id="56ded-205">For this scenario, you can use the [**Handled**](https://msdn.microsoft.com/library/windows/apps/hh943073) property in the event data.</span></span>

<span data-ttu-id="56ded-206">Der Zweck der Eigenschaft [**Handled**](https://msdn.microsoft.com/library/windows/apps/hh943073) in der Datenklasse eines Routingereignisses besteht darin, zu melden, dass ein anderer Handler, den Sie an früherer Stelle in der Ereignisroute registriert haben, bereits tätig war.</span><span class="sxs-lookup"><span data-stu-id="56ded-206">The purpose of the [**Handled**](https://msdn.microsoft.com/library/windows/apps/hh943073) property in a routed event data class is to report that another handler you registered earlier on the event route has already acted.</span></span> <span data-ttu-id="56ded-207">Dies beeinflusst das Verhalten des Routingereignissystems.</span><span class="sxs-lookup"><span data-stu-id="56ded-207">This influences the behavior of the routed event system.</span></span> <span data-ttu-id="56ded-208">Wenn Sie **Handled** in einem Ereignishandler auf **true** festlegen, ist das Routing eines Ereignisses beendet, und das Ereignis wird nicht mehr an nachfolgende übergeordnete Elemente gesendet.</span><span class="sxs-lookup"><span data-stu-id="56ded-208">When you set **Handled** to **true** in an event handler, that event stops routing and is not sent to successive parent elements.</span></span>

### <a name="addhandler-and-already-handled-keyboard-events"></a><span data-ttu-id="56ded-209">"AddHandler " und bereits behandelte Tastaturereignisse</span><span class="sxs-lookup"><span data-stu-id="56ded-209">AddHandler and already-handled keyboard events</span></span>

<span data-ttu-id="56ded-210">Sie können eine spezielle Technik verwenden, um Handler anzufügen, die auf bereits als verarbeitet markierte Ereignisse reagieren können.</span><span class="sxs-lookup"><span data-stu-id="56ded-210">You can use a special technique for attaching handlers that can act on events that you already marked as handled.</span></span> <span data-ttu-id="56ded-211">Bei dieser Technik wird mit der Methode [**AddHandler**](https://msdn.microsoft.com/library/windows/apps/hh702399) ein Handler registriert, und es werden keine XAML-Attribute und keine sprachspezifische Syntax verwendet, die Handler wie „+=“ in C\# hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="56ded-211">This technique uses the [**AddHandler**](https://msdn.microsoft.com/library/windows/apps/hh702399) method to register a handler, rather than using XAML attributes or language-specific syntax for adding handlers, such as += in C\#.</span></span>

<span data-ttu-id="56ded-212">Eine generelle Einschränkung dieser Technik besteht darin, dass die API **AddHandler** einen Parameter vom Typ [**RoutedEvent**](https://msdn.microsoft.com/library/windows/apps/br208808) verwendet, der das fragliche Routingereignis identifiziert.</span><span class="sxs-lookup"><span data-stu-id="56ded-212">A general limitation of this technique is that the **AddHandler** API takes a parameter of type [**RoutedEvent**](https://msdn.microsoft.com/library/windows/apps/br208808) idnentifying the routed event in question.</span></span> <span data-ttu-id="56ded-213">Nicht alle Routingereignisse bieten einen **RoutedEvent**-Bezeichner. Dieser Umstand wirkt sich somit darauf aus, welche Routingereignisse im Fall [**Handled**](https://msdn.microsoft.com/library/windows/apps/hh943073) noch verarbeitet werden können.</span><span class="sxs-lookup"><span data-stu-id="56ded-213">Not all routed events provide a **RoutedEvent** identifier, and this consideration thus affects which routed events can still be handled in the [**Handled**](https://msdn.microsoft.com/library/windows/apps/hh943073) case.</span></span> <span data-ttu-id="56ded-214">Die Ereignisse [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) und [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) haben Routingereignisbezeichner ([**KeyDownEvent**](https://msdn.microsoft.com/library/windows/apps/hh702416) und [**KeyUpEvent**](https://msdn.microsoft.com/library/windows/apps/hh702418)) in [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911).</span><span class="sxs-lookup"><span data-stu-id="56ded-214">The [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) and [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) events have routed event identifiers ([**KeyDownEvent**](https://msdn.microsoft.com/library/windows/apps/hh702416) and [**KeyUpEvent**](https://msdn.microsoft.com/library/windows/apps/hh702418)) on [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911).</span></span> <span data-ttu-id="56ded-215">Andere Texteingabe-Ereignisse, wie [**TextBox.TextChanged**](https://msdn.microsoft.com/library/windows/apps/br209706), besitzen jedoch keine Routingereignisbezeichner und können deshalb für die Technik **AddHandler** nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="56ded-215">However, other events such as [**TextBox.TextChanged**](https://msdn.microsoft.com/library/windows/apps/br209706) do not have routed event identifiers and thus cannot be used with the **AddHandler** technique.</span></span>

### <a name="overriding-keyboard-events-and-behavior"></a><span data-ttu-id="56ded-216">Überschreiben von Tastaturereignissen und Verhalten</span><span class="sxs-lookup"><span data-stu-id="56ded-216">Overriding keyboard events and behavior</span></span>

<span data-ttu-id="56ded-217">Sie können die wichtigsten Ereignisse für bestimmte Steuerelemente überschreiben (z.B. [**GridView**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.GridView)), um eine konsistente Fokusnavigation für verschiedene Eingabegeräte (darunter Tastatur und Gamepad) bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="56ded-217">You can override key events for specific controls (such as [**GridView**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.GridView)) to provide consistent focus navigation for various input devices, including keyboard and gamepad.</span></span>

<span data-ttu-id="56ded-218">Im folgenden Beispiel wird das Steuerelement und überschreiben das KeyDown-Verhalten Fokus zum GridView Inhalte, wenn eine Pfeiltaste betätigt wird.</span><span class="sxs-lookup"><span data-stu-id="56ded-218">In the following example, we subclass the control and override the KeyDown behavior to move focus to the GridView content when any arrow key is pressed.</span></span>

```csharp
public class CustomGridView : GridView
  {
    protected override void OnKeyDown(KeyRoutedEventArgs e)
    {
      // Override arrow key behaviors.
      if (e.Key != Windows.System.VirtualKey.Left && e.Key !=
        Windows.System.VirtualKey.Right && e.Key !=
          Windows.System.VirtualKey.Down && e.Key !=
            Windows.System.VirtualKey.Up)
              base.OnKeyDown(e);
      else
        FocusManager.TryMoveFocus(FocusNavigationDirection.Down);
    }
  }
```

> [!NOTE]
> <span data-ttu-id="56ded-219">Wenn ein GridView nur für Layoutzwecke verwendet wird, sollten Sie möglicherweise andere Steuerelemente verwenden, wie z.B. [**ItemsControl**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.ItemsControl) mit [**ItemsWrapGrid**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.ItemsWrapGrid).</span><span class="sxs-lookup"><span data-stu-id="56ded-219">If using a GridView for layout only, consider using other controls such as [**ItemsControl**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.ItemsControl) with [**ItemsWrapGrid**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.ItemsWrapGrid).</span></span>

## <a name="commanding"></a><span data-ttu-id="56ded-220">Befehle</span><span class="sxs-lookup"><span data-stu-id="56ded-220">Commanding</span></span>

<span data-ttu-id="56ded-221">Eine geringe Anzahl von UI-Elementen verfügt über integrierte Unterstützung für die Steuerung.</span><span class="sxs-lookup"><span data-stu-id="56ded-221">A small number of UI elements provide built-in support for commanding.</span></span> <span data-ttu-id="56ded-222">Die Steuerung verwendet eingabebezogene Routingereignisse in der zugrundeliegenden Implementierung.</span><span class="sxs-lookup"><span data-stu-id="56ded-222">Commanding uses input-related routed events in its underlying implementation.</span></span> <span data-ttu-id="56ded-223">Sie ermöglicht die Verarbeitung verwandter UI-Eingaben (eine bestimmte Zeigeraktion oder Zugriffstaste) durch das Aufrufen eines einzelnen Befehlshandlers.</span><span class="sxs-lookup"><span data-stu-id="56ded-223">It enables processing of related UI input, such as a certain pointer action or a specific accelerator key, by invoking a single command handler.</span></span>

<span data-ttu-id="56ded-224">Wenn die Steuerung für ein UI-Element verfügbar ist, sollten Sie dessen Steuerungs-APIs anstelle einzelner Eingabeereignisse verwenden.</span><span class="sxs-lookup"><span data-stu-id="56ded-224">If commanding is available for a UI element, consider using its commanding APIs instead of any discrete input events.</span></span> <span data-ttu-id="56ded-225">Weitere Informationen finden Sie unter [**ButtonBase.Command**](https://msdn.microsoft.com/library/windows/apps/br227740).</span><span class="sxs-lookup"><span data-stu-id="56ded-225">For more info, see [**ButtonBase.Command**](https://msdn.microsoft.com/library/windows/apps/br227740).</span></span>

<span data-ttu-id="56ded-226">Sie können auch [**ICommand**](https://msdn.microsoft.com/library/windows/apps/br227885) implementieren, um die Befehlsfunktionalität zu kapseln, die Sie über normale Ereignishandler aufrufen.</span><span class="sxs-lookup"><span data-stu-id="56ded-226">You can also implement [**ICommand**](https://msdn.microsoft.com/library/windows/apps/br227885) to encapsulate command functionality that you invoke from ordinary event handlers.</span></span> <span data-ttu-id="56ded-227">Auf diese Weise können Sie die Steuerung auch verwenden, wenn keine **Command**-Eigenschaft verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="56ded-227">This enables you to use commanding even when there is no **Command** property available.</span></span>

## <a name="text-input-and-controls"></a><span data-ttu-id="56ded-228">Texteingabe und Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="56ded-228">Text input and controls</span></span>

<span data-ttu-id="56ded-229">Bestimmte Steuerelemente reagieren mit einer eigenen Verarbeitung auf Tastaturereignisse.</span><span class="sxs-lookup"><span data-stu-id="56ded-229">Certain controls react to keyboard events with their own handling.</span></span> <span data-ttu-id="56ded-230">So ist beispielsweise das Steuerelement [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683) dazu gedacht, über die Tastatur eingegebenen Text zu erfassen und visuell darzustellen.</span><span class="sxs-lookup"><span data-stu-id="56ded-230">For instance, [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683) is a control that is designed to capture and then visually represent text that was entered by using the keyboard.</span></span> <span data-ttu-id="56ded-231">Es verwendet in seiner eigenen Logik [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) und [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) zum Erfassen von Tastaturanschlägen und löst dann auch sein eigenes [**TextChanged**](https://msdn.microsoft.com/library/windows/apps/br209706)-Ereignis aus, wenn der Text tatsächlich geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="56ded-231">It uses [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) and [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) in its own logic to capture keystrokes, then also raises its own [**TextChanged**](https://msdn.microsoft.com/library/windows/apps/br209706) event if the text actually changed.</span></span>

<span data-ttu-id="56ded-232">Trotzdem können Sie generell einer [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br208942) oder einem verwandten Steuerelement, das der Verarbeitung von Texteingaben dient, Handler für [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208941) und [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br209683) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="56ded-232">You can still generally add handlers for [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) and [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) to a [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683), or any related control that is intended to process text input.</span></span> <span data-ttu-id="56ded-233">Jedoch reagiert ein Steuerelement möglicherweise im Rahmen seines Designs nicht auf alle Tastenwerte, die es über Tastaturereignisse empfängt.</span><span class="sxs-lookup"><span data-stu-id="56ded-233">However, as part of its intended design, a control might not respond to all key values that are directed to it through key events.</span></span> <span data-ttu-id="56ded-234">Das Verhalten hängt ganz vom jeweiligen Steuerelement ab.</span><span class="sxs-lookup"><span data-stu-id="56ded-234">Behavior is specific to each control.</span></span>

<span data-ttu-id="56ded-235">Beispielsweise verarbeitet [**ButtonBase**](https://msdn.microsoft.com/library/windows/apps/br227736) (die Basisklasse von [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265)) [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) so, dass eine Überprüfung für die LEERTASTE oder für die EINGABETASTE durchgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="56ded-235">As an example, [**ButtonBase**](https://msdn.microsoft.com/library/windows/apps/br227736) (the base class for [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265)) processes [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) so that it can check for the Spacebar or Enter key.</span></span> <span data-ttu-id="56ded-236">**ButtonBase** verarbeitet **KeyUp** analog zu einem Ereignis für das Drücken der linken Maustaste, um ein [**Click**](https://msdn.microsoft.com/library/windows/apps/br227737)-Ereignis auszulösen.</span><span class="sxs-lookup"><span data-stu-id="56ded-236">**ButtonBase** considers **KeyUp** equivalent to a mouse left button down for purposes of raising a [**Click**](https://msdn.microsoft.com/library/windows/apps/br227737) event.</span></span> <span data-ttu-id="56ded-237">Diese Verarbeitung des Ereignisses wird beim Überschreiben der virtuellen Methode [**OnKeyUp**](https://msdn.microsoft.com/library/windows/apps/hh967983) durch **ButtonBase** erreicht.</span><span class="sxs-lookup"><span data-stu-id="56ded-237">This processing of the event is accomplished when **ButtonBase** overrides the virtual method [**OnKeyUp**](https://msdn.microsoft.com/library/windows/apps/hh967983).</span></span> <span data-ttu-id="56ded-238">In der Implementierung wird [**Handled**](https://msdn.microsoft.com/library/windows/apps/hh943073) auf **true** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="56ded-238">In its implementation, it sets [**Handled**](https://msdn.microsoft.com/library/windows/apps/hh943073) to **true**.</span></span> <span data-ttu-id="56ded-239">Als Ergebnis empfängt kein übergeordnetes Element einer Schaltfläche, die bei der LEERTASTE auf ein Tastaturereignis lauscht, das bereits verarbeitete Element für seine eigenen Handler.</span><span class="sxs-lookup"><span data-stu-id="56ded-239">The result is that any parent of a button that is listening for a key event, in the case of a Spacebar, would not receive the already-handled event for its own handlers.</span></span>

<span data-ttu-id="56ded-240">[**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683) ist ein weiteres Beispiel.</span><span class="sxs-lookup"><span data-stu-id="56ded-240">Another example is [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683).</span></span> <span data-ttu-id="56ded-241">Einige Tasten, wie die Pfeiltasten, werden von **TextBox** nicht als Text angesehen und gelten stattdessen als spezifisch für das UI-Steuerelementverhalten</span><span class="sxs-lookup"><span data-stu-id="56ded-241">Some keys, such as the ARROW keys, are not considered text by **TextBox** and are instead considered specific to the control UI behavior.</span></span> <span data-ttu-id="56ded-242">**TextBox** markiert diese Ereignisse als verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="56ded-242">The **TextBox** marks these event cases as handled.</span></span>

<span data-ttu-id="56ded-243">Benutzerdefinierte Steuerelemente können ein ähnliches eigenes Überschreibungsverhalten für Tastaturereignisse implementieren und [**OnKeyDown**](https://msdn.microsoft.com/library/windows/apps/hh967982) / [**OnKeyUp**](https://msdn.microsoft.com/library/windows/apps/hh967983) überschreiben.</span><span class="sxs-lookup"><span data-stu-id="56ded-243">Custom controls can implement their own similar override behavior for key events by overriding [**OnKeyDown**](https://msdn.microsoft.com/library/windows/apps/hh967982) / [**OnKeyUp**](https://msdn.microsoft.com/library/windows/apps/hh967983).</span></span> <span data-ttu-id="56ded-244">Wenn Ihr benutzerdefiniertes Steuerelement bestimmte Zugriffstasten verarbeitet oder ein Steuerelement- oder Fokusverhalten besitzt, das mit dem für [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683) geschilderten Szenario vergleichbar ist, sollten Sie diese Logik in Ihre eigenen **OnKeyDown** / **OnKeyUp**-Überschreibungen aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="56ded-244">If your custom control processes specific accelerator keys, or has control or focus behavior that is similar to the scenario described for [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683), you should place this logic in your own **OnKeyDown** / **OnKeyUp** overrides.</span></span>

## <a name="the-touch-keyboard"></a><span data-ttu-id="56ded-245">Die Touch-Bildschirmtastatur</span><span class="sxs-lookup"><span data-stu-id="56ded-245">The touch keyboard</span></span>

<span data-ttu-id="56ded-246">Steuerelemente für die Texteingabe bieten automatische Unterstützung für die Touch-Bildschirmtastatur.</span><span class="sxs-lookup"><span data-stu-id="56ded-246">Text input controls provide automatic support for the touch keyboard.</span></span> <span data-ttu-id="56ded-247">Wenn Benutzer den Eingabefokus per Fingereingabe auf ein Textsteuerelement festlegen, wird automatisch die Bildschirmtastatur angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56ded-247">When the user sets the input focus to a text control by using touch input, the touch keyboard appears automatically.</span></span> <span data-ttu-id="56ded-248">Wenn sich der Eingabefokus nicht auf einem Textsteuerelement befindet, ist die Bildschirmtastatur ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="56ded-248">When the input focus is not on a text control, the touch keyboard is hidden.</span></span>

<span data-ttu-id="56ded-249">Wenn die Bildschirmtastatur angezeigt wird, wird Ihre UI automatisch umpositioniert, um sicherzustellen, dass das Element mit dem Fokus sichtbar bleibt.</span><span class="sxs-lookup"><span data-stu-id="56ded-249">When the touch keyboard appears, it automatically repositions your UI to ensure that the focused element remains visible.</span></span> <span data-ttu-id="56ded-250">Dies kann dazu führen, dass andere wichtige Bereiche der UI nicht mehr auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="56ded-250">This can cause other important areas of your UI to move off screen.</span></span> <span data-ttu-id="56ded-251">Sie können das Standardverhalten jedoch deaktivieren und eigene UI-Anpassungen vornehmen, wenn die Bildschirmtastatur eingeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="56ded-251">However, you can disable the default behavior and make your own UI adjustments when the touch keyboard appears.</span></span> <span data-ttu-id="56ded-252">Weitere Informationen finden Sie im [Beispiel für die Bildschirmtastatur](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/TouchKeyboard).</span><span class="sxs-lookup"><span data-stu-id="56ded-252">For more info, see the [Touch keyboard sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/TouchKeyboard).</span></span>

<span data-ttu-id="56ded-253">Wenn Sie ein benutzerdefiniertes Steuerelement erstellen, das zwar Texteingabe erfordert, aber nicht von einem Standardsteuerelement für die Texteingabe abgeleitet ist, können Sie Unterstützung für die Touch-Bildschirmtastatur hinzufügen, indem Sie die richtigen Steuerelementmuster der Benutzeroberflächenautomatisierung implementieren.</span><span class="sxs-lookup"><span data-stu-id="56ded-253">If you create a custom control that requires text input, but does not derive from a standard text input control, you can add touch keyboard support by implementing the correct UI Automation control patterns.</span></span> <span data-ttu-id="56ded-254">Weitere Informationen finden Sie im [Beispiel für die Bildschirmtastatur](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/TouchKeyboard).</span><span class="sxs-lookup"><span data-stu-id="56ded-254">For more info, see the [Touch keyboard sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/TouchKeyboard).</span></span>

<span data-ttu-id="56ded-255">Durch Drücken von Tasten auf der Touch-Bildschirmtastatur werden genau wie beim Drücken von Tasten auf Hardwaretastaturen die Ereignisse [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) und [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="56ded-255">Key presses on the touch keyboard raise [**KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208941) and [**KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208942) events just like key presses on hardware keyboards.</span></span> <span data-ttu-id="56ded-256">Die Touch-Bildschirmtastatur löst jedoch keine Eingabeereignisse für STRG+A, STRG+Z, STRG+X, STRG+C und STRG+V aus, da diese Tastenkombinationen für Textänderungen im Eingabesteuerelement reserviert sind.</span><span class="sxs-lookup"><span data-stu-id="56ded-256">However, the touch keyboard will not raise input events for Ctrl+A, Ctrl+Z, Ctrl+X, Ctrl+C, and Ctrl+V, which are reserved for text manipulation in the input control.</span></span>

<span data-ttu-id="56ded-257">Benutzer können Daten in Ihre App schneller und einfacher eingeben, wenn Sie den Eingabeumfang des Textsteuerelements an die Art der Daten anpassen, die der Benutzer vermutlich eingeben wird.</span><span class="sxs-lookup"><span data-stu-id="56ded-257">You can make it much faster and easier for users to enter data in your app by setting the input scope of the text control to match the kind of data you expect the user to enter.</span></span> <span data-ttu-id="56ded-258">Der Eingabeumfang bietet einen Hinweis auf die Art von Text, die vermutlich über das Steuerelement eingegeben wird. Auf diese Weise kann das System ein spezielles Bildschirmtastaturlayout für den Eingabetyp bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="56ded-258">The input scope provides a hint at the type of text input expected by the control so the system can provide a specialized touch keyboard layout for the input type.</span></span> <span data-ttu-id="56ded-259">Wird ein Textfeld beispielsweise nur verwendet, um eine vierstellige PIN einzugeben, legen Sie die Eigenschaft [**InputScope**](https://msdn.microsoft.com/library/windows/apps/hh702632) auf [**Number**](https://msdn.microsoft.com/library/windows/apps/hh702028) fest.</span><span class="sxs-lookup"><span data-stu-id="56ded-259">For example, if a text box is used only to enter a 4-digit PIN, set the [**InputScope**](https://msdn.microsoft.com/library/windows/apps/hh702632) property to [**Number**](https://msdn.microsoft.com/library/windows/apps/hh702028).</span></span> <span data-ttu-id="56ded-260">Dies weist das System an, das Layout der Zehnertastatur anzuzeigen, das dem Benutzer die Eingabe der PIN erleichtert.</span><span class="sxs-lookup"><span data-stu-id="56ded-260">This tells the system to show the numeric keypad layout, which makes it easier for the user to enter the PIN.</span></span> <span data-ttu-id="56ded-261">Weitere Informationen finden Sie unter [Verwenden des Eingabeumfangs zum Ändern der Bildschirmtastatur](https://msdn.microsoft.com/library/windows/apps/mt280229).</span><span class="sxs-lookup"><span data-stu-id="56ded-261">For more detail, see [Use input scope to change the touch keyboard](https://msdn.microsoft.com/library/windows/apps/mt280229).</span></span>

## <a name="related-articles"></a><span data-ttu-id="56ded-262">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="56ded-262">Related articles</span></span>

**<span data-ttu-id="56ded-263">Entwickler</span><span class="sxs-lookup"><span data-stu-id="56ded-263">Developers</span></span>**
* [<span data-ttu-id="56ded-264">Tastaturinteraktionen</span><span class="sxs-lookup"><span data-stu-id="56ded-264">Keyboard interactions</span></span>](keyboard-interactions.md)
* [<span data-ttu-id="56ded-265">Identifizieren von Eingabegeräten</span><span class="sxs-lookup"><span data-stu-id="56ded-265">Identify input devices</span></span>](identify-input-devices.md)
* [<span data-ttu-id="56ded-266">Reagieren auf das Vorhandensein der Bildschirmtastatur</span><span class="sxs-lookup"><span data-stu-id="56ded-266">Respond to the presence of the touch keyboard</span></span>](respond-to-the-presence-of-the-touch-keyboard.md)

**<span data-ttu-id="56ded-267">Designer</span><span class="sxs-lookup"><span data-stu-id="56ded-267">Designers</span></span>**
* [<span data-ttu-id="56ded-268">Tastaturentwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="56ded-268">Keyboard design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/hh972345)

**<span data-ttu-id="56ded-269">Beispiele</span><span class="sxs-lookup"><span data-stu-id="56ded-269">Samples</span></span>**
* [<span data-ttu-id="56ded-270">Beispiel für die Bildschirmtastatur</span><span class="sxs-lookup"><span data-stu-id="56ded-270">Touch keyboard sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/TouchKeyboard)
* [<span data-ttu-id="56ded-271">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="56ded-271">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="56ded-272">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="56ded-272">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="56ded-273">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="56ded-273">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="56ded-274">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="56ded-274">Archive Samples</span></span>**
* [<span data-ttu-id="56ded-275">Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="56ded-275">Input sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="56ded-276">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="56ded-276">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="56ded-277">Eingabe: Beispiel für die Bildschirmtastatur</span><span class="sxs-lookup"><span data-stu-id="56ded-277">Input: Touch keyboard sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=246019)
* [<span data-ttu-id="56ded-278">Beispiel für die Reaktion auf die Anzeige der Bildschirmtastatur</span><span class="sxs-lookup"><span data-stu-id="56ded-278">Responding to the appearance of the on-screen keyboard sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231633)
* [<span data-ttu-id="56ded-279">Beispiel für die XAML-Textbearbeitung</span><span class="sxs-lookup"><span data-stu-id="56ded-279">XAML text editing sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=251417)
 

 
