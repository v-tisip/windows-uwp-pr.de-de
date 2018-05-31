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
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 0a986d6de680a3024ae252ba640871f9c5d22141
ms.sourcegitcommit: 346b5c9298a6e9e78acf05944bfe13624ea7062e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2018
ms.locfileid: "1707045"
---
# <a name="guidelines-for-visual-feedback"></a><span data-ttu-id="571a0-103">Richtlinien für visuelles Feedback</span><span class="sxs-lookup"><span data-stu-id="571a0-103">Guidelines for visual feedback</span></span>


<span data-ttu-id="571a0-104">Zeigen Sie Benutzern durch visuelles Feedback, wenn ihre Interaktionen ermittelt, interpretiert und behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="571a0-104">Use visual feedback to show users when their interactions are detected, interpreted, and handled.</span></span> <span data-ttu-id="571a0-105">Visuelles Feedback ist hilfreich für Benutzer und kann sie zur Interaktion ermutigen.</span><span class="sxs-lookup"><span data-stu-id="571a0-105">Visual feedback can help users by encouraging interaction.</span></span> <span data-ttu-id="571a0-106">Es weist auf erfolgreiche Interaktionen hin, was für den Benutzer das Gefühl der Kontrolle verstärkt.</span><span class="sxs-lookup"><span data-stu-id="571a0-106">It indicates the success of an interaction, which improves the user's sense of control.</span></span> <span data-ttu-id="571a0-107">Darüber hinaus informiert es über den Systemstatus und verringert die Fehlerzahl.</span><span class="sxs-lookup"><span data-stu-id="571a0-107">It also relays system status and reduces errors.</span></span>

> <span data-ttu-id="571a0-108">**Wichtige APIs**:  [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648), [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Core**](https://msdn.microsoft.com/library/windows/apps/br208383)</span><span class="sxs-lookup"><span data-stu-id="571a0-108">**Important APIs**:  [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648), [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Core**](https://msdn.microsoft.com/library/windows/apps/br208383)</span></span>

## <a name="recommendations"></a><span data-ttu-id="571a0-109">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="571a0-109">Recommendations</span></span>

-   <span data-ttu-id="571a0-110">Versuchen Sie, so eng wie möglich an der ursprünglichen Steuerelementvorlage zu bleiben, um eine optimale Steuerung und Leistung der Anwendung sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="571a0-110">Try to remain as close to the original control template as possible, for optimal control and application performance.</span></span>
-   <span data-ttu-id="571a0-111">Verwenden Sie keine Toucheingabevisualisierungen in Situationen, in denen diese die Verwendung der App beeinträchtigen könnten.</span><span class="sxs-lookup"><span data-stu-id="571a0-111">Don't use touch visualizations in situations where they might interfere with the use of the app.</span></span> <span data-ttu-id="571a0-112">Weitere Informationen finden Sie unter [**ShowGestureFeedback**](https://msdn.microsoft.com/library/windows/apps/br241969).</span><span class="sxs-lookup"><span data-stu-id="571a0-112">For more info, see [**ShowGestureFeedback**](https://msdn.microsoft.com/library/windows/apps/br241969).</span></span>
-   <span data-ttu-id="571a0-113">Zeigen Sie nur dann Feedback an, wenn dies absolut notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="571a0-113">Don't display feedback unless it is absolutely necessary.</span></span> <span data-ttu-id="571a0-114">Sorgen Sie dafür, dass die Benutzeroberfläche übersichtlich bleibt. Zeigen Sie nur dann visuelles Feedback an, wenn die darin enthaltenen Informationen sonst nirgends verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="571a0-114">Keep the UI clean and uncluttered by not showing visual feedback unless you are adding value that is not available elsewhere.</span></span>
-   <span data-ttu-id="571a0-115">Versuchen Sie, die Verhaltensweisen der integrierten Windows-Gesten für visuelles Feedback nicht in erheblichem Umfang anzupassen, da dies eine inkonsistente und verwirrende Benutzerumgebung zur Folge haben kann.</span><span class="sxs-lookup"><span data-stu-id="571a0-115">Try not to dramatically customize the visual feedback behaviors of the built-in Windows gestures, as this can create an inconsistent and confusing user experience.</span></span>

## <a name="additional-usage-guidance"></a><span data-ttu-id="571a0-116">Weitere Hinweise zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="571a0-116">Additional usage guidance</span></span>

<span data-ttu-id="571a0-117">Kontaktvisualisierungen sind besonders für Touchinteraktionen wichtig, bei denen Genauigkeit und Präzision gefragt sind.</span><span class="sxs-lookup"><span data-stu-id="571a0-117">Contact visualizations are especially critical for touch interactions that require accuracy and precision.</span></span> <span data-ttu-id="571a0-118">Ihre App sollte beispielsweise die Position, auf die getippt wurde, genau anzeigen, damit der Benutzer erkennen kann, ob er das Ziel verfehlt hat, wie weit er danebenliegt und welche Korrekturen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="571a0-118">For example, your app should clearly indicate the location of a tap to let a user know if they missed their target, how much they missed it by, and what adjustments they must make.</span></span>

<span data-ttu-id="571a0-119">Durch die Verwendung der Standardsteuerelemente für die XAML-Plattform stellen Sie sicher, dass Ihre App auf allen Geräten und in allen Eingabesituationen ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="571a0-119">Using the default XAML platform controls available ensures that your app works correctly on all devices and in all input situations.</span></span> <span data-ttu-id="571a0-120">Wenn Ihre App benutzerdefinierte Interaktionen enthält, die angepasstes Feedback erfordern, müssen Sie sicherstellen, dass sich das Feedback für die jeweiligen Zwecke eignet, für alle unterstützten Eingabegeräte verfügbar ist und den Benutzer nicht von seiner eigentlichen Arbeit ablenkt.</span><span class="sxs-lookup"><span data-stu-id="571a0-120">If your app features custom interactions that require customized feedback, you should ensure the feedback is appropriate, spans input devices, and doesn't distract a user from their task.</span></span> <span data-ttu-id="571a0-121">Dies kann insbesondere bei Spiel- oder Zeichnungs-Apps ein Problem sein, bei denen das visuelle Feedback mit wichtigen UI-Elementen kollidieren oder diese verdecken kann.</span><span class="sxs-lookup"><span data-stu-id="571a0-121">This can be a particular issue in game or drawing apps, where the visual feedback might conflict with or obscure critical UI.</span></span>

> [!Important] 
> <span data-ttu-id="571a0-122">Das Interaktionsverhalten der integrierten Gesten sollte nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="571a0-122">We don't recommend changing the interaction behavior of the built-in gestures.</span></span> 

**<span data-ttu-id="571a0-123">Feedback auf allen Geräten</span><span class="sxs-lookup"><span data-stu-id="571a0-123">Feedback Across Devices</span></span>**

<span data-ttu-id="571a0-124">Das visuelle Feedback ist im Allgemeinen vom Eingabegerät abhängig (Toucheingabe, Touchpad, Maus, Stift, Tastatur usw.).</span><span class="sxs-lookup"><span data-stu-id="571a0-124">Visual feedback is generally dependent on the input device (touch, touchpad, mouse, pen/stylus, keyboard, and so on).</span></span> <span data-ttu-id="571a0-125">Das integrierte Feedback für die Maus z.B. beinhaltet normalerweise eine Bewegung und Änderung des Cursors, während für Touch- und Stifteingabe Berührungsvisualisierungen erforderlich sind und für die Eingabe und Navigation per Tastatur Fokusrechtecke und Hervorhebung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="571a0-125">For example, the built-in feedback for a mouse usually involves moving and changing the cursor, while touch and pen require contact visualizations, and keyboard input and navigation uses focus rectangles and highlighting.</span></span>

<span data-ttu-id="571a0-126">Verwenden Sie [**ShowGestureFeedback**](https://msdn.microsoft.com/library/windows/apps/br241969), um das Feedbackverhalten für die Plattformgesten festzulegen.</span><span class="sxs-lookup"><span data-stu-id="571a0-126">Use [**ShowGestureFeedback**](https://msdn.microsoft.com/library/windows/apps/br241969) to set feedback behavior for the platform gestures.</span></span>

<span data-ttu-id="571a0-127">Wenn Sie Anpassungen an der Feedback-UI vornehmen, muss das Feedback alle Eingabemodi unterstützen und für alle Modi geeignet sein.</span><span class="sxs-lookup"><span data-stu-id="571a0-127">If customizing feedback UI, ensure you provide feedback that supports, and is suitable for, all input modes.</span></span>

<span data-ttu-id="571a0-128">Im Folgenden finden Sie einige Beispiele für integrierte Kontaktvisualisierungen in Windows.</span><span class="sxs-lookup"><span data-stu-id="571a0-128">Here are some examples of built-in contact visualizations in Windows.</span></span>

| ![Touchfeedback](images/TouchFeedback.png) | ![Mausfeedback](images/MouseFeedback.png) | ![Stiftfeedback](images/PenFeedback.png) | ![Tastaturfeedback](images/KeyboardFeedback.png) |
| --- | --- | --- | --- |
| <span data-ttu-id="571a0-133">Touchvisualisierung</span><span class="sxs-lookup"><span data-stu-id="571a0-133">Touch visualization</span></span> | <span data-ttu-id="571a0-134">Maus-/Touchpadvisualisierung</span><span class="sxs-lookup"><span data-stu-id="571a0-134">Mouse/touchpad visualization</span></span> | <span data-ttu-id="571a0-135">Stiftvisualisierung</span><span class="sxs-lookup"><span data-stu-id="571a0-135">Pen visualization</span></span> | <span data-ttu-id="571a0-136">Tastaturvisualisierung</span><span class="sxs-lookup"><span data-stu-id="571a0-136">Keyboard visualization</span></span> |

## <a name="high-visibility-focus-visuals"></a><span data-ttu-id="571a0-137">Visuelle Fokuselemente mit hoher Sichtbarkeit</span><span class="sxs-lookup"><span data-stu-id="571a0-137">High Visibility Focus Visuals</span></span>

<span data-ttu-id="571a0-138">Alle Windows-Apps zeigen ein stärker definiertes visuelles Fokuselement um interaktive Steuerelemente innerhalb der Anwendung herum.</span><span class="sxs-lookup"><span data-stu-id="571a0-138">All Windows apps sport a more defined focus visual around interactable controls within the application.</span></span> <span data-ttu-id="571a0-139">Diese neuen visuellen Fokuselemente können vollständig angepasst und auch gelöscht werden, wenn nötig.</span><span class="sxs-lookup"><span data-stu-id="571a0-139">These new focus visuals are fully customizable as well as disableable when needed.</span></span>

## <a name="color-branding--customizing"></a><span data-ttu-id="571a0-140">Farbbranding und -anpassung</span><span class="sxs-lookup"><span data-stu-id="571a0-140">Color Branding & Customizing</span></span>

**<span data-ttu-id="571a0-141">Rahmeneigenschaften</span><span class="sxs-lookup"><span data-stu-id="571a0-141">Border Properties</span></span>**

<span data-ttu-id="571a0-142">Es gibt zwei Elemente bei den visuellen Fokuselementen mit hoher Sichtbarkeit: der primäre und der sekundäre Rahmen.</span><span class="sxs-lookup"><span data-stu-id="571a0-142">There are two parts to the high visibility focus visuals: the primary border and the secondary border.</span></span> <span data-ttu-id="571a0-143">Der primäre Rahmen ist **2Pixel** breit und verläuft an der *Außenseite* des sekundären Rahmens.</span><span class="sxs-lookup"><span data-stu-id="571a0-143">The primary border is **2px** thick, and runs around the *outside* of the secondary border.</span></span> <span data-ttu-id="571a0-144">Der sekundäre Rahmen ist **1Pixel** breit und verläuft an der *Innenseite* des primären Rahmens.</span><span class="sxs-lookup"><span data-stu-id="571a0-144">The secondary border is **1px** thick and runs around the *inside* of the primary border.</span></span>
![Redlines visueller Fokuselemente mit hoher Sichtbarkeit](images/FocusRectRedlines.png)

<span data-ttu-id="571a0-146">Um die Breite der beiden Rahmentypen (primär oder sekundär) zu ändern, verwenden Sie **FocusVisualPrimaryThickness** bzw. **FocusVisualSecondaryThickness**:</span><span class="sxs-lookup"><span data-stu-id="571a0-146">To change the thickness of either border type (primary or secondary) use the **FocusVisualPrimaryThickness** or **FocusVisualSecondaryThickness**, respectively:</span></span>
```XAML
<Slider Width="200" FocusVisualPrimaryThickness="5" FocusVisualSecondaryThickness="2"/>
```
![Randbreiten visueller Fokuselemente mit hoher Sichtbarkeit](images/FocusMargin.png)

<span data-ttu-id="571a0-148">Der Rand ist eine Eigenschaft des Typs [**Thickness**](https://msdn.microsoft.com/library/system.windows.thickness) und kann daher so angepasst werden, dass er nur an bestimmten Seiten des Steuerelements angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="571a0-148">The margin is a property of type [**Thickness**](https://msdn.microsoft.com/library/system.windows.thickness), and therefore the margin can be customized to appear only on certain sides of the control.</span></span> <span data-ttu-id="571a0-149">Weitere Informationen siehe unten: ![Randbreite visueller Fokuselemente mit hoher Sichtbarkeit nur unten</span><span class="sxs-lookup"><span data-stu-id="571a0-149">See below: ![High visibility focus visual margin thickness bottom only</span></span>](images/FocusThicknessSide.png)

<span data-ttu-id="571a0-150">Der Rand ist der Abstand zwischen den visuellen Grenzen des Steuerelements und dem Beginn des *sekundären Rahmens* der visuellen Fokuselemente.</span><span class="sxs-lookup"><span data-stu-id="571a0-150">The margin is the space between the control's visual bounds and the start of the focus visuals *secondary border*.</span></span> <span data-ttu-id="571a0-151">Der standardmäßige Rand hat eine Breite von **1Pixel** außerhalb der Grenzen des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="571a0-151">The default margin is **1px** away from the control bounds.</span></span> <span data-ttu-id="571a0-152">Sie können diesen Rand pro Steuerelement bearbeiten, indem Sie die Eigenschaft **FocusVisualMargin** ändern:</span><span class="sxs-lookup"><span data-stu-id="571a0-152">You can edit this margin on a per-control basis, by changing the **FocusVisualMargin** property:</span></span>
```XAML
<Slider Width="200" FocusVisualMargin="-5"/>
```
![Randunterschiede visueller Fokuselemente mit hoher Sichtbarkeit](images/FocusPlusMinusMargin.png)

*<span data-ttu-id="571a0-154">Ein negativer Rand verschiebt den Rahmen weiter weg von der Mitte des Steuerelements. Ein positiver Rand verschiebt den Rahmen näher zur Mitte des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="571a0-154">A negative margin will push the border away from the center of the control, and a positive margin will move the border closer to the center of the control.</span></span>*

<span data-ttu-id="571a0-155">Um die visuellen Fokuselemente für ein Steuerelement vollständig zu deaktivieren, deaktivieren Sie einfach **UseSystemFocusVisuals**:</span><span class="sxs-lookup"><span data-stu-id="571a0-155">To turn off focus visuals on the control entirely, simply disabled **UseSystemFocusVisuals**:</span></span>
```XAML
<Slider Width="200" UseSystemFocusVisuals="False"/>
```

<span data-ttu-id="571a0-156">Die Breite, der Rand oder die vollständige Entfernung der visuellen Fokuselemente durch den App-Entwickler werden pro Steuerelement festgelegt.</span><span class="sxs-lookup"><span data-stu-id="571a0-156">The thickness, margin, or whether or not the app-developer wishes to have the focus visuals at all, is determined on a per-control basis.</span></span>

**<span data-ttu-id="571a0-157">Farbeigenschaften</span><span class="sxs-lookup"><span data-stu-id="571a0-157">Color Properties</span></span>**

<span data-ttu-id="571a0-158">Es gibt nur zwei Farbeigenschaften für die visuellen Fokuselemente; die primäre Rahmenfarbe und die sekundäre Rahmenfarbe.</span><span class="sxs-lookup"><span data-stu-id="571a0-158">There are only two color properties for the focus visuals: the primary border color, and the secondary border color.</span></span> <span data-ttu-id="571a0-159">Diese Rahmenfarben für visuelle Fokuselemente können pro Steuerelement auf Seitenebene und global auf App-Ebene geändert werden:</span><span class="sxs-lookup"><span data-stu-id="571a0-159">These focus visual border colors can be changed per-control on an page level, and globally on an app-wide level:</span></span>

<span data-ttu-id="571a0-160">Um App-weites Branding visueller Fokuselemente durchzuführen, überschreiben Sie die Systempinsel:</span><span class="sxs-lookup"><span data-stu-id="571a0-160">To brand focus visuals app-wide, override the system brushes:</span></span>
```XAML
<SolidColorBrush x:Key="SystemControlFocusVisualPrimaryBrush" Color="DarkRed"/>
<SolidColorBrush x:Key="SystemControlFocusVisualSecondaryBrush" Color="Pink"/>
```
![Änderungen der Farbe visueller Fokuselemente mit hoher Sichtbarkeit](images/FocusRectColorChanges.png)

<span data-ttu-id="571a0-162">Um die Farben pro Steuerelement zu ändern, bearbeiten Sie einfach die Eigenschaften der visuellen Fokuselemente für das gewünschte Steuerelement:</span><span class="sxs-lookup"><span data-stu-id="571a0-162">To change the colors on a per-control basis, just edit the focus visual properties on the desired control:</span></span>
```XAML
<Slider Width="200" FocusVisualPrimaryBrush="DarkRed" FocusVisualSecondaryBrush="Pink"/>
```

## <a name="related-articles"></a><span data-ttu-id="571a0-163">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="571a0-163">Related articles</span></span>

**<span data-ttu-id="571a0-164">Für Designer</span><span class="sxs-lookup"><span data-stu-id="571a0-164">For designers</span></span>**
* [<span data-ttu-id="571a0-165">Anleitungen für das Verschieben</span><span class="sxs-lookup"><span data-stu-id="571a0-165">Guidelines for panning</span></span>](guidelines-for-panning.md)

**<span data-ttu-id="571a0-166">Für Entwickler</span><span class="sxs-lookup"><span data-stu-id="571a0-166">For developers</span></span>**
* [<span data-ttu-id="571a0-167">Benutzerdefinierte Benutzerinteraktionen</span><span class="sxs-lookup"><span data-stu-id="571a0-167">Custom user interactions</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185599)

**<span data-ttu-id="571a0-168">Beispiele</span><span class="sxs-lookup"><span data-stu-id="571a0-168">Samples</span></span>**
* [<span data-ttu-id="571a0-169">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="571a0-169">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="571a0-170">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="571a0-170">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="571a0-171">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="571a0-171">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="571a0-172">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="571a0-172">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="571a0-173">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="571a0-173">Archive samples</span></span>**
* [<span data-ttu-id="571a0-174">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="571a0-174">Input: XAML user input events sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="571a0-175">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="571a0-175">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="571a0-176">Eingabe: Beispiel für Fingereingabe-Treffertests</span><span class="sxs-lookup"><span data-stu-id="571a0-176">Input: Touch hit testing sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231590)
* [<span data-ttu-id="571a0-177">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="571a0-177">XAML scrolling, panning, and zooming sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="571a0-178">Eingabe: vereinfachtes Freihandbeispiel</span><span class="sxs-lookup"><span data-stu-id="571a0-178">Input: Simplified ink sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=246570)
* [<span data-ttu-id="571a0-179">Eingabe: Beispiel für Windows8-Bewegungen</span><span class="sxs-lookup"><span data-stu-id="571a0-179">Input: Windows 8 gestures sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=264995)
* [<span data-ttu-id="571a0-180">Eingabe: Beispiel für Manipulationen und Gesten (C++)</span><span class="sxs-lookup"><span data-stu-id="571a0-180">Input: Manipulations and gestures (C++) sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231605)
* [<span data-ttu-id="571a0-181">Beispiel für die DirectX-Fingereingabe</span><span class="sxs-lookup"><span data-stu-id="571a0-181">DirectX touch input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231627)
 

 
