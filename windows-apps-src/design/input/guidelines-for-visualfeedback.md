---
author: Karl-Bridge-Microsoft
Description: Use visual feedback to show users when their interactions with a UWP app are detected, interpreted, and handled.
title: Visuelles Feedback
ms.assetid: bf2f3672-95f0-4c8c-9a72-0934f2d3b767
label: Visual feedback
template: detail.hbs
keywords: Visuelles Feedback, Fokus-Feedback, Touch-Feedback, Kontaktvisualisierung, Eingabe, Interaktion
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: baf23062595d5d81fc59a2d757dcbada685c0f97
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5969000"
---
# <a name="guidelines-for-visual-feedback"></a><span data-ttu-id="d3cc3-103">Richtlinien für visuelles Feedback</span><span class="sxs-lookup"><span data-stu-id="d3cc3-103">Guidelines for visual feedback</span></span>

<span data-ttu-id="d3cc3-104">Zeigen Sie Benutzern durch visuelles Feedback, wenn ihre Interaktionen ermittelt, interpretiert und behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-104">Use visual feedback to show users when their interactions are detected, interpreted, and handled.</span></span> <span data-ttu-id="d3cc3-105">Visuelles Feedback ist hilfreich für Benutzer und kann sie zur Interaktion ermutigen.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-105">Visual feedback can help users by encouraging interaction.</span></span> <span data-ttu-id="d3cc3-106">Es weist auf erfolgreiche Interaktionen hin, was für den Benutzer das Gefühl der Kontrolle verstärkt.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-106">It indicates the success of an interaction, which improves the user's sense of control.</span></span> <span data-ttu-id="d3cc3-107">Darüber hinaus informiert es über den Systemstatus und verringert die Fehlerzahl.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-107">It also relays system status and reduces errors.</span></span>

> <span data-ttu-id="d3cc3-108">**Wichtige APIs**: [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648), [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Core**](https://msdn.microsoft.com/library/windows/apps/br208383)</span><span class="sxs-lookup"><span data-stu-id="d3cc3-108">**Important APIs**:  [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648), [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Core**](https://msdn.microsoft.com/library/windows/apps/br208383)</span></span>

## <a name="recommendations"></a><span data-ttu-id="d3cc3-109">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="d3cc3-109">Recommendations</span></span>

- <span data-ttu-id="d3cc3-110">Versuchen Sie, Änderungen an einer Steuerelementvorlage auf ein Minimum zu beschränken, die direkt im Zusammenhang mit Ihrem Designziel stehen, da sich umfangreiche Änderungen auf die Leistung und Zugänglichkeit des Steuerelements und der Anwendung auswirken können.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-110">Try to limit modifcations of a control template to those directly related to your design intent, as extensive changes can impact the performance and accessibility of both the control and your application.</span></span> 
    - <span data-ttu-id="d3cc3-111">Unter [XAML-Formatvorlagen](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/xaml-styles) finden Sie weitere Informationen zum Anpassen der Eigenschaften eines Steuerelements, einschließlich der visuellen Zustandseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-111">See [XAML styles](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/xaml-styles) for more info on customizing the properties of a control, including visual state properties.</span></span>
    - <span data-ttu-id="d3cc3-112">Unter [UserControl-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.usercontrol) finden Sie weitere Informationen zu Änderungen an einer Steuerelementvorlage.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-112">See the [UserControl Class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.usercontrol) for details on making changes to a control template</span></span>
    - <span data-ttu-id="d3cc3-113">Erwägen Sie, eine eigene benutzerdefinierte Steuerelementvorlage zu erstellen, wenn Sie umfangreiche Änderungen an einer Steuerelementvorlage vornehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-113">Consider creating your own custom templated control if you need to make significant changes to a control template.</span></span> <span data-ttu-id="d3cc3-114">Ein Beispiel für eine benutzerdefinierte Steuerelementvorlage finden Sie unter [Beispiel für ein benutzerdefiniertes Bearbeitungssteuerelement](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="d3cc3-114">For an example of a custom templated control, see the [Custom Edit Control sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>
- <span data-ttu-id="d3cc3-115">Verwenden Sie keine Toucheingabevisualisierungen in Situationen, in denen diese die Verwendung der App beeinträchtigen könnten.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-115">Don't use touch visualizations in situations where they might interfere with the use of the app.</span></span> <span data-ttu-id="d3cc3-116">Weitere Informationen finden Sie unter [**ShowGestureFeedback**](https://msdn.microsoft.com/library/windows/apps/br241969).</span><span class="sxs-lookup"><span data-stu-id="d3cc3-116">For more info, see [**ShowGestureFeedback**](https://msdn.microsoft.com/library/windows/apps/br241969).</span></span>
- <span data-ttu-id="d3cc3-117">Zeigen Sie nur dann Feedback an, wenn dies absolut notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-117">Don't display feedback unless it is absolutely necessary.</span></span> <span data-ttu-id="d3cc3-118">Sorgen Sie dafür, dass die Benutzeroberfläche übersichtlich bleibt. Zeigen Sie nur dann visuelles Feedback an, wenn die darin enthaltenen Informationen sonst nirgends verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-118">Keep the UI clean and uncluttered by not showing visual feedback unless you are adding value that is not available elsewhere.</span></span>
- <span data-ttu-id="d3cc3-119">Versuchen Sie, die Verhaltensweisen der integrierten Windows-Gesten für visuelles Feedback nicht in erheblichem Umfang anzupassen, da dies eine inkonsistente und verwirrende Benutzerumgebung zur Folge haben kann.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-119">Try not to dramatically customize the visual feedback behaviors of the built-in Windows gestures, as this can create an inconsistent and confusing user experience.</span></span>

## <a name="additional-usage-guidance"></a><span data-ttu-id="d3cc3-120">Weitere Hinweise zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="d3cc3-120">Additional usage guidance</span></span>

<span data-ttu-id="d3cc3-121">Kontaktvisualisierungen sind besonders für Touchinteraktionen wichtig, bei denen Genauigkeit und Präzision gefragt sind.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-121">Contact visualizations are especially critical for touch interactions that require accuracy and precision.</span></span> <span data-ttu-id="d3cc3-122">Ihre App sollte beispielsweise die Position, auf die getippt wurde, genau anzeigen, damit der Benutzer erkennen kann, ob er das Ziel verfehlt hat, wie weit er danebenliegt und welche Korrekturen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-122">For example, your app should clearly indicate the location of a tap to let a user know if they missed their target, how much they missed it by, and what adjustments they must make.</span></span>

<span data-ttu-id="d3cc3-123">Durch die Verwendung der Standardsteuerelemente für die XAML-Plattform stellen Sie sicher, dass Ihre App auf allen Geräten und in allen Eingabesituationen ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-123">Using the default XAML platform controls available ensures that your app works correctly on all devices and in all input situations.</span></span> <span data-ttu-id="d3cc3-124">Wenn Ihre App benutzerdefinierte Interaktionen enthält, die angepasstes Feedback erfordern, müssen Sie sicherstellen, dass sich das Feedback für die jeweiligen Zwecke eignet, für alle unterstützten Eingabegeräte verfügbar ist und den Benutzer nicht von seiner eigentlichen Arbeit ablenkt.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-124">If your app features custom interactions that require customized feedback, you should ensure the feedback is appropriate, spans input devices, and doesn't distract a user from their task.</span></span> <span data-ttu-id="d3cc3-125">Dies kann insbesondere bei Spiel- oder Zeichnungs-Apps ein Problem sein, bei denen das visuelle Feedback mit wichtigen UI-Elementen kollidieren oder diese verdecken kann.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-125">This can be a particular issue in game or drawing apps, where the visual feedback might conflict with or obscure critical UI.</span></span>

> [!Important]
> <span data-ttu-id="d3cc3-126">Das Interaktionsverhalten der integrierten Gesten sollte nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-126">We don't recommend changing the interaction behavior of the built-in gestures.</span></span>

**<span data-ttu-id="d3cc3-127">Feedback auf allen Geräten</span><span class="sxs-lookup"><span data-stu-id="d3cc3-127">Feedback Across Devices</span></span>**

<span data-ttu-id="d3cc3-128">Das visuelle Feedback ist im Allgemeinen vom Eingabegerät abhängig (Toucheingabe, Touchpad, Maus, Stift, Tastatur usw.).</span><span class="sxs-lookup"><span data-stu-id="d3cc3-128">Visual feedback is generally dependent on the input device (touch, touchpad, mouse, pen/stylus, keyboard, and so on).</span></span> <span data-ttu-id="d3cc3-129">Das integrierte Feedback für die Maus z.B. beinhaltet normalerweise eine Bewegung und Änderung des Cursors, während für Touch- und Stifteingabe Berührungsvisualisierungen erforderlich sind und für die Eingabe und Navigation per Tastatur Fokusrechtecke und Hervorhebung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-129">For example, the built-in feedback for a mouse usually involves moving and changing the cursor, while touch and pen require contact visualizations, and keyboard input and navigation uses focus rectangles and highlighting.</span></span>

<span data-ttu-id="d3cc3-130">Verwenden Sie [**ShowGestureFeedback**](https://msdn.microsoft.com/library/windows/apps/br241969), um das Feedbackverhalten für die Plattformgesten festzulegen.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-130">Use [**ShowGestureFeedback**](https://msdn.microsoft.com/library/windows/apps/br241969) to set feedback behavior for the platform gestures.</span></span>

<span data-ttu-id="d3cc3-131">Wenn Sie Anpassungen an der Feedback-UI vornehmen, muss das Feedback alle Eingabemodi unterstützen und für alle Modi geeignet sein.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-131">If customizing feedback UI, ensure you provide feedback that supports, and is suitable for, all input modes.</span></span>

<span data-ttu-id="d3cc3-132">Im Folgenden finden Sie einige Beispiele für integrierte Kontaktvisualisierungen in Windows.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-132">Here are some examples of built-in contact visualizations in Windows.</span></span>

| ![Touchfeedback](images/TouchFeedback.png) | ![Mausfeedback](images/MouseFeedback.png) | ![Stiftfeedback](images/PenFeedback.png) | ![Tastaturfeedback](images/KeyboardFeedback.png) |
| --- | --- | --- | --- |
| <span data-ttu-id="d3cc3-137">Touchvisualisierung</span><span class="sxs-lookup"><span data-stu-id="d3cc3-137">Touch visualization</span></span> | <span data-ttu-id="d3cc3-138">Maus-/Touchpadvisualisierung</span><span class="sxs-lookup"><span data-stu-id="d3cc3-138">Mouse/touchpad visualization</span></span> | <span data-ttu-id="d3cc3-139">Stiftvisualisierung</span><span class="sxs-lookup"><span data-stu-id="d3cc3-139">Pen visualization</span></span> | <span data-ttu-id="d3cc3-140">Tastaturvisualisierung</span><span class="sxs-lookup"><span data-stu-id="d3cc3-140">Keyboard visualization</span></span> |

## <a name="high-visibility-focus-visuals"></a><span data-ttu-id="d3cc3-141">Visuelle Fokuselemente mit hoher Sichtbarkeit</span><span class="sxs-lookup"><span data-stu-id="d3cc3-141">High Visibility Focus Visuals</span></span>

<span data-ttu-id="d3cc3-142">Alle Windows-Apps zeigen ein stärker definiertes visuelles Fokuselement um interaktive Steuerelemente innerhalb der Anwendung herum.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-142">All Windows apps sport a more defined focus visual around interactable controls within the application.</span></span> <span data-ttu-id="d3cc3-143">Diese neuen visuellen Fokuselemente können vollständig angepasst und auch gelöscht werden, wenn nötig.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-143">These new focus visuals are fully customizable as well as disableable when needed.</span></span>

<span data-ttu-id="d3cc3-144">Für das **10-Fuß-TV-Erlebnis**, das typisch für die Xbox und TV-Nutzung ist, unterstützt Windows **Einblendungen mit Fokus**, einen Lichteffekt, der den Rahmen fokussierbarer Elemente wie z.B. eine Schaltfläche animiert, wenn sie über Gamepads oder Tastatureingaben anfokussiert werden.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-144">For the **10-foot experience** typical of Xbox and TV usage, Windows supports **Reveal focus**, a lighting effect that animates the border of focusable elements, such as a button, when they get focus through gamepad or keyboard input.</span></span> <span data-ttu-id="d3cc3-145">Weitere Informationen finden Sie unter [Entwerfen für Xbox und Fernsehgeräte](https://docs.microsoft.com/windows/uwp/design/devices/designing-for-tv#reveal-focus).</span><span class="sxs-lookup"><span data-stu-id="d3cc3-145">For more info, see [Designing for Xbox and TV](https://docs.microsoft.com/windows/uwp/design/devices/designing-for-tv#reveal-focus).</span></span>

## <a name="color-branding--customizing"></a><span data-ttu-id="d3cc3-146">Farbbranding und -anpassung</span><span class="sxs-lookup"><span data-stu-id="d3cc3-146">Color Branding & Customizing</span></span>

**<span data-ttu-id="d3cc3-147">Rahmeneigenschaften</span><span class="sxs-lookup"><span data-stu-id="d3cc3-147">Border Properties</span></span>**

<span data-ttu-id="d3cc3-148">Es gibt zwei Elemente bei den visuellen Fokuselementen mit hoher Sichtbarkeit: der primäre und der sekundäre Rahmen.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-148">There are two parts to the high visibility focus visuals: the primary border and the secondary border.</span></span> <span data-ttu-id="d3cc3-149">Der primäre Rahmen ist **2Pixel** breit und verläuft an der *Außenseite* des sekundären Rahmens.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-149">The primary border is **2px** thick, and runs around the *outside* of the secondary border.</span></span> <span data-ttu-id="d3cc3-150">Der sekundäre Rahmen ist **1Pixel** breit und verläuft an der *Innenseite* des primären Rahmens.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-150">The secondary border is **1px** thick and runs around the *inside* of the primary border.</span></span>
![Redlines visueller Fokuselemente mit hoher Sichtbarkeit](images/FocusRectRedlines.png)

<span data-ttu-id="d3cc3-152">Um die Breite der beiden Rahmentypen (primär oder sekundär) zu ändern, verwenden Sie **FocusVisualPrimaryThickness** bzw. **FocusVisualSecondaryThickness**:</span><span class="sxs-lookup"><span data-stu-id="d3cc3-152">To change the thickness of either border type (primary or secondary) use the **FocusVisualPrimaryThickness** or **FocusVisualSecondaryThickness**, respectively:</span></span>
```XAML
<Slider Width="200" FocusVisualPrimaryThickness="5" FocusVisualSecondaryThickness="2"/>
```
![Randbreiten visueller Fokuselemente mit hoher Sichtbarkeit](images/FocusMargin.png)

<span data-ttu-id="d3cc3-154">Der Rand ist eine Eigenschaft des Typs [**Thickness**](https://msdn.microsoft.com/library/system.windows.thickness) und kann daher so angepasst werden, dass er nur an bestimmten Seiten des Steuerelements angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-154">The margin is a property of type [**Thickness**](https://msdn.microsoft.com/library/system.windows.thickness), and therefore the margin can be customized to appear only on certain sides of the control.</span></span> <span data-ttu-id="d3cc3-155">Weitere Informationen siehe unten: ![Randbreite visueller Fokuselemente mit hoher Sichtbarkeit nur unten</span><span class="sxs-lookup"><span data-stu-id="d3cc3-155">See below: ![High visibility focus visual margin thickness bottom only</span></span>](images/FocusThicknessSide.png)

<span data-ttu-id="d3cc3-156">Der Rand ist der Abstand zwischen den visuellen Grenzen des Steuerelements und dem Beginn des *sekundären Rahmens* der visuellen Fokuselemente.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-156">The margin is the space between the control's visual bounds and the start of the focus visuals *secondary border*.</span></span> <span data-ttu-id="d3cc3-157">Der standardmäßige Rand hat eine Breite von **1Pixel** außerhalb der Grenzen des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-157">The default margin is **1px** away from the control bounds.</span></span> <span data-ttu-id="d3cc3-158">Sie können diesen Rand pro Steuerelement bearbeiten, indem Sie die Eigenschaft **FocusVisualMargin** ändern:</span><span class="sxs-lookup"><span data-stu-id="d3cc3-158">You can edit this margin on a per-control basis, by changing the **FocusVisualMargin** property:</span></span>
```XAML
<Slider Width="200" FocusVisualMargin="-5"/>
```
![Randunterschiede visueller Fokuselemente mit hoher Sichtbarkeit](images/FocusPlusMinusMargin.png)

*<span data-ttu-id="d3cc3-160">Ein negativer Rand verschiebt den Rahmen weiter weg von der Mitte des Steuerelements. Ein positiver Rand verschiebt den Rahmen näher zur Mitte des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-160">A negative margin will push the border away from the center of the control, and a positive margin will move the border closer to the center of the control.</span></span>*

<span data-ttu-id="d3cc3-161">Um die visuellen Fokuselemente für ein Steuerelement vollständig zu deaktivieren, deaktivieren Sie einfach **UseSystemFocusVisuals**:</span><span class="sxs-lookup"><span data-stu-id="d3cc3-161">To turn off focus visuals on the control entirely, simply disabled **UseSystemFocusVisuals**:</span></span>
```XAML
<Slider Width="200" UseSystemFocusVisuals="False"/>
```

<span data-ttu-id="d3cc3-162">Die Breite, der Rand oder die vollständige Entfernung der visuellen Fokuselemente durch den App-Entwickler werden pro Steuerelement festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-162">The thickness, margin, or whether or not the app-developer wishes to have the focus visuals at all, is determined on a per-control basis.</span></span>

**<span data-ttu-id="d3cc3-163">Farbeigenschaften</span><span class="sxs-lookup"><span data-stu-id="d3cc3-163">Color Properties</span></span>**

<span data-ttu-id="d3cc3-164">Es gibt nur zwei Farbeigenschaften für die visuellen Fokuselemente; die primäre Rahmenfarbe und die sekundäre Rahmenfarbe.</span><span class="sxs-lookup"><span data-stu-id="d3cc3-164">There are only two color properties for the focus visuals: the primary border color, and the secondary border color.</span></span> <span data-ttu-id="d3cc3-165">Diese Rahmenfarben für visuelle Fokuselemente können pro Steuerelement auf Seitenebene und global auf App-Ebene geändert werden:</span><span class="sxs-lookup"><span data-stu-id="d3cc3-165">These focus visual border colors can be changed per-control on an page level, and globally on an app-wide level:</span></span>

<span data-ttu-id="d3cc3-166">Um App-weites Branding visueller Fokuselemente durchzuführen, überschreiben Sie die Systempinsel:</span><span class="sxs-lookup"><span data-stu-id="d3cc3-166">To brand focus visuals app-wide, override the system brushes:</span></span>
```XAML
<SolidColorBrush x:Key="SystemControlFocusVisualPrimaryBrush" Color="DarkRed"/>
<SolidColorBrush x:Key="SystemControlFocusVisualSecondaryBrush" Color="Pink"/>
```
![Änderungen der Farbe visueller Fokuselemente mit hoher Sichtbarkeit](images/FocusRectColorChanges.png)

<span data-ttu-id="d3cc3-168">Um die Farben pro Steuerelement zu ändern, bearbeiten Sie einfach die Eigenschaften der visuellen Fokuselemente für das gewünschte Steuerelement:</span><span class="sxs-lookup"><span data-stu-id="d3cc3-168">To change the colors on a per-control basis, just edit the focus visual properties on the desired control:</span></span>
```XAML
<Slider Width="200" FocusVisualPrimaryBrush="DarkRed" FocusVisualSecondaryBrush="Pink"/>
```

## <a name="related-articles"></a><span data-ttu-id="d3cc3-169">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="d3cc3-169">Related articles</span></span>

**<span data-ttu-id="d3cc3-170">Für Designer</span><span class="sxs-lookup"><span data-stu-id="d3cc3-170">For designers</span></span>**
* [<span data-ttu-id="d3cc3-171">Anleitungen für das Verschieben</span><span class="sxs-lookup"><span data-stu-id="d3cc3-171">Guidelines for panning</span></span>](guidelines-for-panning.md)

**<span data-ttu-id="d3cc3-172">Für Entwickler</span><span class="sxs-lookup"><span data-stu-id="d3cc3-172">For developers</span></span>**
* [<span data-ttu-id="d3cc3-173">Benutzerdefinierte Benutzerinteraktionen</span><span class="sxs-lookup"><span data-stu-id="d3cc3-173">Custom user interactions</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185599)

**<span data-ttu-id="d3cc3-174">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d3cc3-174">Samples</span></span>**
* [<span data-ttu-id="d3cc3-175">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="d3cc3-175">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="d3cc3-176">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="d3cc3-176">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="d3cc3-177">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="d3cc3-177">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="d3cc3-178">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="d3cc3-178">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="d3cc3-179">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="d3cc3-179">Archive samples</span></span>**
* [<span data-ttu-id="d3cc3-180">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="d3cc3-180">Input: XAML user input events sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="d3cc3-181">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="d3cc3-181">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="d3cc3-182">Eingabe: Beispiel für Fingereingabe-Treffertests</span><span class="sxs-lookup"><span data-stu-id="d3cc3-182">Input: Touch hit testing sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231590)
* [<span data-ttu-id="d3cc3-183">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="d3cc3-183">XAML scrolling, panning, and zooming sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="d3cc3-184">Eingabe: vereinfachtes Freihandbeispiel</span><span class="sxs-lookup"><span data-stu-id="d3cc3-184">Input: Simplified ink sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=246570)
* [<span data-ttu-id="d3cc3-185">Eingabe: Beispiel für Windows8-Bewegungen</span><span class="sxs-lookup"><span data-stu-id="d3cc3-185">Input: Windows 8 gestures sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=264995)
* [<span data-ttu-id="d3cc3-186">Eingabe: Beispiel für Manipulationen und Gesten (C++)</span><span class="sxs-lookup"><span data-stu-id="d3cc3-186">Input: Manipulations and gestures (C++) sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231605)
* [<span data-ttu-id="d3cc3-187">Beispiel für die DirectX-Fingereingabe</span><span class="sxs-lookup"><span data-stu-id="d3cc3-187">DirectX touch input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231627)
 

 
