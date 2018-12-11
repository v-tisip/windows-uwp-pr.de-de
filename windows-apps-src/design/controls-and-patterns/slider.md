---
Description: Lets the user set a value in a given range.
title: Schieberegler
ms.assetid: 7EC7EA33-BE7E-4FD5-B205-B8FA7B729ACC
label: Sliders
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
pm-contact: kisai
design-contact: ksulliv
dev-contact: mitra
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: e13f28d9b82bca04d108bac818faa873567d77f7
ms.sourcegitcommit: 231065c899d0de285584d41e6335251e0c2c4048
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8825326"
---
# <a name="sliders"></a><span data-ttu-id="2e416-103">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="2e416-103">Sliders</span></span>

 

<span data-ttu-id="2e416-104">Ein Schieberegler ist ein Steuerelement, über das der Benutzer aus einer Reihe von Werten auswählen kann, indem er ein Schiebereglersteuerelement über einen Bereich verschiebt.</span><span class="sxs-lookup"><span data-stu-id="2e416-104">A slider is a control that lets the user select from a range of values by moving a thumb control along a track.</span></span>

> <span data-ttu-id="2e416-105">**Wichtige APIs**: [Slider-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.slider.aspx), [Value-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.rangebase.value.aspx), [ValueChanged-Ereignis](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.rangebase.valuechanged.aspx)</span><span class="sxs-lookup"><span data-stu-id="2e416-105">**Important APIs**: [Slider class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.slider.aspx), [Value property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.rangebase.value.aspx), [ValueChanged event](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.rangebase.valuechanged.aspx)</span></span>

![Schieberegler-Steuerelement](images/controls/slider.png)


## <a name="is-this-the-right-control"></a><span data-ttu-id="2e416-107">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="2e416-107">Is this the right control?</span></span>

<span data-ttu-id="2e416-108">Verwenden Sie einen Schieberegler, wenn Sie Benutzern ermöglichen möchten, definierte, zusammenhängende Werte (z. B. Lautstärke oder Helligkeit) oder einen Bereich von separaten Werten (z. B. Einstellungen für die Bildschirmauflösung) festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2e416-108">Use a slider when you want your users to be able to set defined, contiguous values (such as volume or brightness) or a range of discrete values (such as screen resolution settings).</span></span>

<span data-ttu-id="2e416-109">Eine Schieberegler ist eine gute Wahl, wenn Sie wissen, dass Benutzer den Wert als relative Anzahl betrachten und nicht als numerischen Wert.</span><span class="sxs-lookup"><span data-stu-id="2e416-109">A slider is a good choice when you know that users think of the value as a relative quantity, not a numeric value.</span></span> <span data-ttu-id="2e416-110">So denken Benutzer beispielsweise beim Festlegen der Audiolautstärke an "niedrig" oder "mittel", aber nicht an Werte wie "2" oder "5".</span><span class="sxs-lookup"><span data-stu-id="2e416-110">For example, users think about setting their audio volume to low or medium—not about setting the value to 2 or 5.</span></span>

<span data-ttu-id="2e416-111">Verwenden Sie einen Schieberegler nicht für binäre Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="2e416-111">Don't use a slider for binary settings.</span></span> <span data-ttu-id="2e416-112">Verwenden Sie stattdessen einen [Umschalter](toggles.md).</span><span class="sxs-lookup"><span data-stu-id="2e416-112">Use a [toggle switch](toggles.md) instead.</span></span>

<span data-ttu-id="2e416-113">Hier sind einige weitere Faktoren, die Sie bei der Entscheidung für oder gegen die Verwendung eines Schiebereglers berücksichtigen sollten:</span><span class="sxs-lookup"><span data-stu-id="2e416-113">Here are some additional factors to consider when deciding whether to use a slider:</span></span>

-   **<span data-ttu-id="2e416-114">Handelt es sich bei der Einstellung um eine relative Anzahl?</span><span class="sxs-lookup"><span data-stu-id="2e416-114">Does the setting seem like a relative quantity?</span></span>** <span data-ttu-id="2e416-115">Ist dies nicht der Fall, verwenden Sie stattdessen [Optionsfelder](radio-button.md) oder ein [Listenfeld](lists.md).</span><span class="sxs-lookup"><span data-stu-id="2e416-115">If not, use [radio buttons](radio-button.md) or a [list box](lists.md).</span></span>
-   **<span data-ttu-id="2e416-116">Handelt es sich bei der Einstellung um einen exakten, bekannten numerischen Wert?</span><span class="sxs-lookup"><span data-stu-id="2e416-116">Is the setting an exact, known numeric value?</span></span>** <span data-ttu-id="2e416-117">Wenn ja, verwenden Sie ein numerisches [Textfeld](text-box.md).</span><span class="sxs-lookup"><span data-stu-id="2e416-117">If so, use a numeric [text box](text-box.md).</span></span>
-   **<span data-ttu-id="2e416-118">Wäre es für Benutzer hilfreich, sofort Feedback zur Auswirkung von Einstellungsänderungen zu erhalten?</span><span class="sxs-lookup"><span data-stu-id="2e416-118">Would a user benefit from instant feedback on the effect of setting changes?</span></span>** <span data-ttu-id="2e416-119">Wenn ja, verwenden Sie einen Schieberegler.</span><span class="sxs-lookup"><span data-stu-id="2e416-119">If so, use a slider.</span></span> <span data-ttu-id="2e416-120">Beispielsweise können Benutzer eine Farbe leichter auswählen, wenn sie sofort sehen, wie sich Änderungen an den Werten für Farbton, Sättigung oder Leuchtdichte auswirken.</span><span class="sxs-lookup"><span data-stu-id="2e416-120">For example, users can choose a color more easily by immediately seeing the effect of changes to hue, saturation, or luminosity values.</span></span>
-   **<span data-ttu-id="2e416-121">Weist die Einstellung einen Bereich aus vier oder mehr Werten auf?</span><span class="sxs-lookup"><span data-stu-id="2e416-121">Does the setting have a range of four or more values?</span></span>** <span data-ttu-id="2e416-122">Ist dies nicht der Fall, verwenden Sie stattdessen [Optionsfelder](radio-button.md).</span><span class="sxs-lookup"><span data-stu-id="2e416-122">If not, use [radio buttons](radio-button.md).</span></span>
-   **<span data-ttu-id="2e416-123">Können Benutzer den Wert ändern?</span><span class="sxs-lookup"><span data-stu-id="2e416-123">Can the user change the value?</span></span>** <span data-ttu-id="2e416-124">Schieberegler dienen zur Benutzerinteraktion.</span><span class="sxs-lookup"><span data-stu-id="2e416-124">Sliders are for user interaction.</span></span> <span data-ttu-id="2e416-125">Wenn der Wert in keinem Fall von Benutzern geändert werden kann, verwenden Sie stattdessen schreibgeschützten Text.</span><span class="sxs-lookup"><span data-stu-id="2e416-125">If a user can't ever change the value, use read-only text instead.</span></span>

<span data-ttu-id="2e416-126">Wenn Sie zwischen einem Schieberegler und einem numerischen Textfeld entscheiden, verwenden Sie in folgenden Fällen ein numerisches Textfeld:</span><span class="sxs-lookup"><span data-stu-id="2e416-126">If you are deciding between a slider and a numeric text box, use a numeric text box if:</span></span>

-   <span data-ttu-id="2e416-127">Der auf dem Bildschirm verfügbare Platz ist knapp.</span><span class="sxs-lookup"><span data-stu-id="2e416-127">Screen space is tight.</span></span>
-   <span data-ttu-id="2e416-128">Benutzer möchten wahrscheinlich lieber die Tastatur verwenden.</span><span class="sxs-lookup"><span data-stu-id="2e416-128">The user is likely to prefer using the keyboard.</span></span>

<span data-ttu-id="2e416-129">Verwenden Sie in folgenden Fällen einen Schieberegler:</span><span class="sxs-lookup"><span data-stu-id="2e416-129">Use a slider if:</span></span>

-   <span data-ttu-id="2e416-130">Benutzer profitieren von sofortigem Feedback.</span><span class="sxs-lookup"><span data-stu-id="2e416-130">Users will benefit from instant feedback.</span></span>

## <a name="examples"></a><span data-ttu-id="2e416-131">Beispiele</span><span class="sxs-lookup"><span data-stu-id="2e416-131">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="2e416-132">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="2e416-132">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="2e416-133">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/Slider">die App zu öffnen und den Schieberegler in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="2e416-133">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/Slider">open the app and see the Slider in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="2e416-134">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="2e416-134">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="2e416-135">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="2e416-135">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="2e416-136">Ein Schieberegler zum Steuern der Lautstärke auf Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="2e416-136">A slider to control the volume on Windows Phone.</span></span>

![Ein Schieberegler zum Steuern der Lautstärke auf Windows Phone](images/control-examples/slider-phone.png)

<span data-ttu-id="2e416-138">Ein Schieberegler zum Ändern der Textgröße in den Windows-Anzeigeeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="2e416-138">A slider to change text size in Windows display settings.</span></span>

![Ein Schieberegler zum Ändern der Textgröße in den Windows-Anzeigeeinstellungen](images/control-examples/slider-display-settings.png)

## <a name="create-a-slider"></a><span data-ttu-id="2e416-140">Erstellen Sie einen Schieberegler</span><span class="sxs-lookup"><span data-stu-id="2e416-140">Create a slider</span></span>

<span data-ttu-id="2e416-141">So erstellen Sie einen Schieberegler in XAML.</span><span class="sxs-lookup"><span data-stu-id="2e416-141">Here's how to create a slider in XAML.</span></span>

```xaml
<Slider x:Name="volumeSlider" Header="Volume" Width="200"
        ValueChanged="Slider_ValueChanged"/>
```

<span data-ttu-id="2e416-142">So erstellen Sie einen Schieberegler im Code.</span><span class="sxs-lookup"><span data-stu-id="2e416-142">Here's how to create a slider in code.</span></span>

```csharp
Slider volumeSlider = new Slider();
volumeSlider.Header = "Volume";
volumeSlider.Width = 200;
volumeSlider.ValueChanged += Slider_ValueChanged;

// Add the slider to a parent container in the visual tree.
stackPanel1.Children.Add(volumeSlider);
```

<span data-ttu-id="2e416-143">Den Wert des Schiebereglers können Sie aus der [Value](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.rangebase.value.aspx)-Eigenschaft abrufen und festlegen.</span><span class="sxs-lookup"><span data-stu-id="2e416-143">You get and set the value of the slider from the [Value](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.rangebase.value.aspx) property.</span></span> <span data-ttu-id="2e416-144">Zum Reagieren auf Werteänderungen können Sie die Value-Eigenschaft mithilfe der Datenbindung binden oder das [ValueChanged](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.rangebase.valuechanged.aspx)-Ereignis behandeln.</span><span class="sxs-lookup"><span data-stu-id="2e416-144">To respond to value changes, you can use data binding to bind to the Value property, or handle the [ValueChanged](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.rangebase.valuechanged.aspx) event.</span></span>

```csharp
private void Slider_ValueChanged(object sender, RangeBaseValueChangedEventArgs e)
{
    Slider slider = sender as Slider;
    if (slider != null)
    {
        media.Volume = slider.Value;
    }
}
```

## <a name="recommendations"></a><span data-ttu-id="2e416-145">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="2e416-145">Recommendations</span></span>

-   <span data-ttu-id="2e416-146">Passen Sie das Steuerelement an, sodass Benutzer den Wert einfach anpassen können.</span><span class="sxs-lookup"><span data-stu-id="2e416-146">Size the control so that users can easily set the value they want.</span></span> <span data-ttu-id="2e416-147">Stellen Sie für Einstellungen mit separaten Werten sicher, dass der Benutzer jeden Wert einfach mithilfe der Maus auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="2e416-147">For settings with discrete values, make sure the user can easily select any value using the mouse.</span></span> <span data-ttu-id="2e416-148">Stellen Sie sicher, dass die Endpunkte des Schiebereglers immer in die Bereiche einer Ansicht passen.</span><span class="sxs-lookup"><span data-stu-id="2e416-148">Make sure the endpoints of the slider always fit within the bounds of a view.</span></span>
-   <span data-ttu-id="2e416-149">Geben Sie während oder nach der Benutzerauswahl ein sofortiges Feedback (sofern umsetzbar).</span><span class="sxs-lookup"><span data-stu-id="2e416-149">Give immediate feedback while or after a user makes a selection (when practical).</span></span> <span data-ttu-id="2e416-150">Beispielsweise gibt die Windows-Lautstärkeregelung einen Signalton aus, um die ausgewählte Audiolautstärke anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2e416-150">For example, the Windows volume control beeps to indicate the selected audio volume.</span></span>
-   <span data-ttu-id="2e416-151">Verwenden Sie Bezeichnungen, um den Wertebereich anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2e416-151">Use labels to show the range of values.</span></span> <span data-ttu-id="2e416-152">Eine Ausnahme liegt vor, wenn der Schieberegler vertikal ausgerichtet ist und die obere Beschriftung „Maximum”, „Hoch”, „Mehr” oder ähnlich lautet, ist die Bedeutung klar, und Sie können die anderen Beschriftungen weglassen.</span><span class="sxs-lookup"><span data-stu-id="2e416-152">Exception: If the slider is vertically oriented and the top label is Maximum, High, More, or equivalent, you can omit the other labels because the meaning is clear.</span></span>
-   <span data-ttu-id="2e416-153">Deaktivieren Sie alle zugeordneten Beschriftungen und das visuelle Feedback, wenn Sie den Schieberegler deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="2e416-153">Disable all associated labels or feedback visuals when you disable the slider.</span></span>
-   <span data-ttu-id="2e416-154">Bedenken Sie beim Festlegen der Flussrichtung bzw. Ausrichtung Ihres Schiebereglers die Textrichtung.</span><span class="sxs-lookup"><span data-stu-id="2e416-154">Consider the direction of text when setting the flow direction and/or orientation of your slider.</span></span> <span data-ttu-id="2e416-155">In einigen Sprachen fließt das Skript von links nach rechts, und in anderen von rechts nach links.</span><span class="sxs-lookup"><span data-stu-id="2e416-155">Script flows from left to right in some languages, and from right to left in others.</span></span>
-   <span data-ttu-id="2e416-156">Verwenden Sie einen Schieberegler nicht als Statusanzeige.</span><span class="sxs-lookup"><span data-stu-id="2e416-156">Don't use a slider as a progress indicator.</span></span>
-   <span data-ttu-id="2e416-157">Legen Sie für die Miniaturansicht des Schiebereglers keine andere Größe als die Standardgröße fest.</span><span class="sxs-lookup"><span data-stu-id="2e416-157">Don't change the size of the slider thumb from the default size.</span></span>
-   <span data-ttu-id="2e416-158">Erstellen Sie keinen fortlaufenden Schieberegler, wenn der Wertebereich groß ist und die Benutzer mit hoher Wahrscheinlichkeit einen von mehreren repräsentativen Werten aus dem Bereich auswählen.</span><span class="sxs-lookup"><span data-stu-id="2e416-158">Don't create a continuous slider if the range of values is large and users will most likely select one of several representative values from the range.</span></span> <span data-ttu-id="2e416-159">Verwenden Sie diese Werte stattdessen als einzige zulässige Schritte.</span><span class="sxs-lookup"><span data-stu-id="2e416-159">Instead, use those values as the only steps allowed.</span></span> <span data-ttu-id="2e416-160">Wenn der Höchstwert für einen Zeitwert beispielsweise 1Monat ist, die Benutzer aber nur zwischen 1Minute, 1Stunde, 1Tag oder 1Monat auswählen sollen, erstellen Sie einen Schieberegler mit 4Schrittpunkten.</span><span class="sxs-lookup"><span data-stu-id="2e416-160">For example if time value might be up to 1 month but users only need to pick from 1 minute, 1 hour, 1 day or 1 month, then create a slider with only 4 step points.</span></span>

## <a name="additional-usage-guidance"></a><span data-ttu-id="2e416-161">Weitere Hinweise zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="2e416-161">Additional usage guidance</span></span>

### <a name="choosing-the-right-layout-horizontal-or-vertical"></a><span data-ttu-id="2e416-162">Auswählen des richtigen Layouts: horizontal oder vertikal</span><span class="sxs-lookup"><span data-stu-id="2e416-162">Choosing the right layout: horizontal or vertical</span></span>

<span data-ttu-id="2e416-163">Sie können den Schieberegler horizontal oder vertikal ausrichten.</span><span class="sxs-lookup"><span data-stu-id="2e416-163">You can orient your slider horizontally or vertically.</span></span> <span data-ttu-id="2e416-164">Bestimmen Sie anhand dieser Richtlinien das geeignete Layout.</span><span class="sxs-lookup"><span data-stu-id="2e416-164">Use these guidelines to determine which layout to use.</span></span>

-   <span data-ttu-id="2e416-165">Verwenden Sie eine natürliche Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="2e416-165">Use a natural orientation.</span></span> <span data-ttu-id="2e416-166">Wenn der Schieberegler beispielsweise einen echten Wert darstellt, der normalerweise vertikal angezeigt wird (z.B. eine Temperatur), verwenden Sie die vertikale Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="2e416-166">For example, if the slider represents a real-world value that is normally shown vertically (such as temperature), use a vertical orientation.</span></span>
-   <span data-ttu-id="2e416-167">Wenn das Steuerelement für die Suche in Medien verwendet wird, beispielsweise in einer Video-App, verwenden Sie die horizontale Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="2e416-167">If the control is used to seek within media, like in a video app, use a horizontal orientation.</span></span>
-   <span data-ttu-id="2e416-168">Wenn Sie einen Schieberegler auf einer Seite verwenden, die in eine Richtung geschwenkt werden kann (horizontal oder vertikal), verwenden Sie für den Schieberegler eine andere Ausrichtung als die Schwenkrichtung.</span><span class="sxs-lookup"><span data-stu-id="2e416-168">When using a slider in page that can be panned in one direction (horizontally or vertically), use a different orientation for the slider than the panning direction.</span></span> <span data-ttu-id="2e416-169">Anderenfalls streifen Benutzer möglicherweise beim Schwenken der Seite den Schieberegler und ändern versehentlich den Wert.</span><span class="sxs-lookup"><span data-stu-id="2e416-169">Otherwise, users might swipe the slider and change its value accidentally when they try to pan the page.</span></span>
-   <span data-ttu-id="2e416-170">Wenn Sie noch nicht sicher sind, welche Ausrichtung Sie verwenden sollen, nehmen Sie die, die am besten zum Seitenlayout passt.</span><span class="sxs-lookup"><span data-stu-id="2e416-170">If you're still not sure which orientation to use, use the one that best fits your page layout.</span></span>

### <a name="range-direction"></a><span data-ttu-id="2e416-171">Bereichsrichtung</span><span class="sxs-lookup"><span data-stu-id="2e416-171">Range direction</span></span>

<span data-ttu-id="2e416-172">Die Bereichsrichtung ist die Richtung, in der Sie den Schieberegler bewegen, wenn Sie ihn vom aktuellen Wert zu seinem maximalen Wert verschieben.</span><span class="sxs-lookup"><span data-stu-id="2e416-172">The range direction is the direction you move the slider when you slide it from its current value to its max value.</span></span>

-   <span data-ttu-id="2e416-173">Platzieren Sie bei einem vertikalen Schieberegler den höchsten Wert am oberen Ende des Schiebereglers, unabhängig von der Leserichtung.</span><span class="sxs-lookup"><span data-stu-id="2e416-173">For vertical slider, put the largest value at the top of the slider, regardless of reading direction.</span></span> <span data-ttu-id="2e416-174">Platzieren Sie beispielsweise bei einem Schieberegler für die Lautstärke immer die Einstellung für die maximale Lautstärke am oberen Ende des Schiebereglers.</span><span class="sxs-lookup"><span data-stu-id="2e416-174">For example, for a volume slider, always put the maximum volume setting at the top of the slider.</span></span> <span data-ttu-id="2e416-175">Bei anderen Arten von Werten (beispielsweise bei Wochentagen) orientieren Sie sich an der Leserichtung der Seite.</span><span class="sxs-lookup"><span data-stu-id="2e416-175">For other types of values (such as days of the week), follow the reading direction of the page.</span></span>
-   <span data-ttu-id="2e416-176">Platzieren Sie bei horizontalen Stilen den niedrigeren Wert auf der linken Seite des Schiebereglers (bei einem Seitenlayout von links nach rechts ) bzw. auf der rechten Seite (bei einem Seitenlayout von rechts nach links).</span><span class="sxs-lookup"><span data-stu-id="2e416-176">For horizontal styles, put the lower value on the left side of the slider for left-to-right page layout, and on the right for right-to-left page layout.</span></span>
-   <span data-ttu-id="2e416-177">Die einzige Ausnahme für die oben genannte Richtlinie sind Mediensuchleisten: Platzieren Sie immer den niedrigeren Wert auf der linken Seite des Schiebereglers.</span><span class="sxs-lookup"><span data-stu-id="2e416-177">The one exception to the previous guideline is for media seek bars: always put the lower value on the left side of the slider.</span></span>

### <a name="steps-and-tick-marks"></a><span data-ttu-id="2e416-178">Schritte und Teilstriche</span><span class="sxs-lookup"><span data-stu-id="2e416-178">Steps and tick marks</span></span>

-   <span data-ttu-id="2e416-179">Verwenden Sie Schrittpunkte, wenn der Schieberegler keine beliebigen Werte zwischen minimalen und maximalen Werten zulassen soll. Wenn Sie beispielsweise einen Schieberegler verwenden, um die Anzahl der zu kaufenden Kinotickets anzugeben, lassen Sie keine Gleitkommawerte zu.</span><span class="sxs-lookup"><span data-stu-id="2e416-179">Use step points if you don't want the slider to allow arbitrary values between min and max. For example, if you use a slider to specify the number of movie tickets to buy, don't allow floating point values.</span></span> <span data-ttu-id="2e416-180">Verwenden Sie den Schrittwert "1".</span><span class="sxs-lookup"><span data-stu-id="2e416-180">Give it a step value of 1.</span></span>
-   <span data-ttu-id="2e416-181">Wenn Sie Schritte (auch als Andockpunkte bezeichnet) angeben, stellen Sie sicher, dass der letzte Schritt am Maximalwert des Schiebereglers ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="2e416-181">If you specify steps (also known as snap points), make sure that the final step aligns to the slider's max value.</span></span>
-   <span data-ttu-id="2e416-182">Verwenden Sie Teilstriche, wenn Sie Benutzern die Position wichtiger Werte zeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="2e416-182">Use tick marks when you want to show users the location of major or significant values.</span></span> <span data-ttu-id="2e416-183">So kann beispielsweise ein Schieberegler für die Zoomsteuerung Teilstriche für 50%, 100% und 200% haben.</span><span class="sxs-lookup"><span data-stu-id="2e416-183">For example, a slider that controls a zoom might have tick marks for 50%, 100%, and 200%.</span></span>
-   <span data-ttu-id="2e416-184">Zeigen Sie Teilstriche an, wenn Benutzer den ungefähren Wert der Einstellung wissen müssen.</span><span class="sxs-lookup"><span data-stu-id="2e416-184">Show tick marks when users need to know the approximate value of the setting.</span></span>
-   <span data-ttu-id="2e416-185">Zeigen Sie Teilstriche und eine Wertbeschriftung an, wenn die Benutzer den genauen Wert der ausgewählten Einstellung erfahren sollen, ohne mit dem Steuerelement zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="2e416-185">Show tick marks and a value label when users need to know the exact value of the setting they choose, without interacting with the control.</span></span> <span data-ttu-id="2e416-186">Andernfalls können Sie die QuickInfo für den Wert verwenden, um den genauen Wert anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2e416-186">Otherwise, they can use the value tooltip to see the exact value.</span></span>
-   <span data-ttu-id="2e416-187">Zeigen Sie immer Teilstriche an, wenn Schrittpunkte nicht offensichtlich sind.</span><span class="sxs-lookup"><span data-stu-id="2e416-187">Always show tick marks when step points aren't obvious.</span></span> <span data-ttu-id="2e416-188">Wenn der Schieberegler beispielsweise 200Pixel breit ist und 200Andockpunkte hat, können Sie die Teilstriche ausblenden, da die Benutzer das Andockverhalten nicht bemerken.</span><span class="sxs-lookup"><span data-stu-id="2e416-188">For example, if the slider is 200 pixels wide and has 200 snap points, you can hide the tick marks because users won't notice the snapping behavior.</span></span> <span data-ttu-id="2e416-189">Wenn aber nur zehn Andockpunkte vorhanden sind, zeigen Sie Teilstriche an.</span><span class="sxs-lookup"><span data-stu-id="2e416-189">But if there are only 10 snap points, show tick marks.</span></span>

### <a name="labels"></a><span data-ttu-id="2e416-190">Beschriftungen</span><span class="sxs-lookup"><span data-stu-id="2e416-190">Labels</span></span>

-   **<span data-ttu-id="2e416-191">Schiebereglerbeschriftungen</span><span class="sxs-lookup"><span data-stu-id="2e416-191">Slider labels</span></span>**

    <span data-ttu-id="2e416-192">Aus der Schiebereglerbeschriftung geht hervor, wofür der Schieberegler verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2e416-192">The slider label indicates what the slider is used for.</span></span>

    -   <span data-ttu-id="2e416-193">Verwenden Sie eine Beschriftung ohne Interpunktion am Ende (diese Konvention gilt für alle Beschriftungen für Steuerelemente).</span><span class="sxs-lookup"><span data-stu-id="2e416-193">Use a label with no ending punctuation (this is the convention for all control labels).</span></span>
    -   <span data-ttu-id="2e416-194">Platzieren Sie Beschriftungen über dem Schieberegler, wenn er sich in einem Formular befindet, in dem die meisten Beschriftungen über den Steuerelementen positioniert sind.</span><span class="sxs-lookup"><span data-stu-id="2e416-194">Position labels above the slider when the slider is in a form that places most of its labels above their controls.</span></span>
    -   <span data-ttu-id="2e416-195">Platzieren Sie Beschriftungen an der Seite, wenn sich der Schieberegler in einer Umgebung befindet, in der die meisten Beschriftungen neben den Steuerelementen positioniert sind.</span><span class="sxs-lookup"><span data-stu-id="2e416-195">Position labels to the sides when the slider is in a form that places most of its labels to the side of their controls.</span></span>
    -   <span data-ttu-id="2e416-196">Platzieren Sie Beschriftungen nach Möglichkeit nicht unter dem Schieberegler, da der Benutzer die Beschriftung mit dem Finger verdecken könnte, wenn er den Schieberegler berührt.</span><span class="sxs-lookup"><span data-stu-id="2e416-196">Avoid placing labels below the slider because the user's finger might occlude the label when the user touches the slider.</span></span>
-   **<span data-ttu-id="2e416-197">Bereichsbeschriftungen</span><span class="sxs-lookup"><span data-stu-id="2e416-197">Range labels</span></span>**

    <span data-ttu-id="2e416-198">Die Bereichs- oder Füllungsbeschriftungen beschreiben den minimalen und den maximalen Wert des Schiebereglers.</span><span class="sxs-lookup"><span data-stu-id="2e416-198">The range, or fill, labels describe the slider's minimum and maximum values.</span></span>

    -   <span data-ttu-id="2e416-199">Beschriften Sie die beiden Enden des Schiebereglerbereichs, sofern dies nicht aufgrund einer vertikalen Ausrichtung unnötig ist.</span><span class="sxs-lookup"><span data-stu-id="2e416-199">Label the two ends of the slider range, unless a vertical orientation makes this unnecessary.</span></span>
    -   <span data-ttu-id="2e416-200">Verwenden Sie nach Möglichkeit für jede Beschriftung nur ein Wort.</span><span class="sxs-lookup"><span data-stu-id="2e416-200">Use only one word, if possible, for each label.</span></span>
    -   <span data-ttu-id="2e416-201">Verwenden Sie keine Interpunktion am Ende.</span><span class="sxs-lookup"><span data-stu-id="2e416-201">Don't use ending punctuation.</span></span>
    -   <span data-ttu-id="2e416-202">Stellen Sie sicher, dass die Beschriftungen aussagekräftig und parallel sind.</span><span class="sxs-lookup"><span data-stu-id="2e416-202">Make sure these labels are descriptive and parallel.</span></span> <span data-ttu-id="2e416-203">Beispiele: "Maximum/Minimum", "Mehr/Weniger", "Niedrig/Hoch", "Leise/Laut".</span><span class="sxs-lookup"><span data-stu-id="2e416-203">Examples: Maximum/Minimum, More/Less, Low/High, Soft/Loud.</span></span>
-   **<span data-ttu-id="2e416-204">Wertbeschriftungen</span><span class="sxs-lookup"><span data-stu-id="2e416-204">Value labels</span></span>**

    <span data-ttu-id="2e416-205">Eine Wertbeschriftung zeigt den aktuellen Wert des Schiebereglers an.</span><span class="sxs-lookup"><span data-stu-id="2e416-205">A value label displays the current value of the slider.</span></span>

    -   <span data-ttu-id="2e416-206">Wenn Sie eine Wertbeschriftung benötigen, zeigen Sie sie unter dem Schieberegler an.</span><span class="sxs-lookup"><span data-stu-id="2e416-206">If you need a value label, display it below the slider.</span></span>
    -   <span data-ttu-id="2e416-207">Zentrieren Sie den Text relativ zum Steuerelement, und schließen Sie die Einheiten ein (beispielsweise Pixel).</span><span class="sxs-lookup"><span data-stu-id="2e416-207">Center the text relative to the control and include the units (such as pixels).</span></span>
    -   <span data-ttu-id="2e416-208">Da der Schiebereglerziehpunkt beim Streichen verdeckt ist, sollten Sie in Erwägung ziehen, den aktuellen Wert auf andere Art und Weise anzuzeigen, und zwar mit einer Beschriftung oder einem anderen visuellen Effekt.</span><span class="sxs-lookup"><span data-stu-id="2e416-208">Since the slider’s thumb is covered during scrubbing, consider showing the current value some other way, with a label or other visual.</span></span> <span data-ttu-id="2e416-209">Eine Schieberegler-Einstellungstextgröße könnte einigen Beispieltext auf die richtige Größe neben dem Schieberegler rendern.</span><span class="sxs-lookup"><span data-stu-id="2e416-209">A slider setting text size could render some sample text of the right size beside the slider.</span></span>

### <a name="appearance-and-interaction"></a><span data-ttu-id="2e416-210">Erscheinungsbild und Interaktion</span><span class="sxs-lookup"><span data-stu-id="2e416-210">Appearance and interaction</span></span>

<span data-ttu-id="2e416-211">Eine Schieberegler besteht aus einer Spur und einem Ziehpunkt.</span><span class="sxs-lookup"><span data-stu-id="2e416-211">A slider is composed of a track and a thumb.</span></span> <span data-ttu-id="2e416-212">Bei der Spur handelt es sich um eine Leiste (welche optional verschiedene Teilstrichstile anzeigen kann), die den Bereich der Werte darstellt, die eingegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="2e416-212">The track is a bar (which can optionally show various styles of tick marks) representing the range of values that can be input.</span></span> <span data-ttu-id="2e416-213">Der Ziehpunkt ist ein Wahlschalter, den der Benutzer positionieren kann, indem er entweder auf die Spur tippt oder zurück oder noch vorn streicht.</span><span class="sxs-lookup"><span data-stu-id="2e416-213">The thumb is a selector, which the user can position by either tapping the track or by scrubbing back and forth on it.</span></span>

<span data-ttu-id="2e416-214">Ein Schieberegler weist ein großes Berührungsziel auf.</span><span class="sxs-lookup"><span data-stu-id="2e416-214">A slider has a large touch target.</span></span> <span data-ttu-id="2e416-215">Ein Schieberegler sollte möglichst weit genug vom Rand des Displays positioniert werden, um eine zugängliche Berührung zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="2e416-215">To maintain touch accessibility, a slider should be positioned far enough away from the edge of the display.</span></span>

<span data-ttu-id="2e416-216">Ziehen Sie beim Entwerfen eines benutzerdefinierten Schiebereglers Möglichkeiten zum übersichtlichen Darstellen aller für den Benutzer erforderlichen Informationen in Betracht.</span><span class="sxs-lookup"><span data-stu-id="2e416-216">When you’re designing a custom slider, consider ways to present all the necessary info to the user with as little clutter as possible.</span></span> <span data-ttu-id="2e416-217">Verwenden Sie eine Wertbeschriftung, wenn der Benutzer die Einheiten verstehen muss, um die Einstellung nachvollziehen zu können. Suchen Sie nach kreativen Möglichkeiten, um diese Werte grafisch darzustellen.</span><span class="sxs-lookup"><span data-stu-id="2e416-217">Use a value label if a user needs to know the units in order to understand the setting; find creative ways to represent these values graphically.</span></span> <span data-ttu-id="2e416-218">Beispielsweise könnte ein Schieberegler, über den die Lautstärke geregelt wird, am Minimum-Ende des Schiebereglers eine Lautsprechergrafik ohne Schallwellen und am Maximum-Ende eine Lautsprechergrafik mit Schallwellen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2e416-218">A slider that controls volume, for example, could display a speaker graphic without sound waves at the minimum end of the slider, and a speaker graphic with sound waves at the maximum end.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="2e416-219">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="2e416-219">Get the sample code</span></span>

- <span data-ttu-id="2e416-220">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2e416-220">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-topics"></a><span data-ttu-id="2e416-221">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2e416-221">Related topics</span></span>
- [<span data-ttu-id="2e416-222">Umschalter</span><span class="sxs-lookup"><span data-stu-id="2e416-222">Toggle switches</span></span>](toggles.md)
- [<span data-ttu-id="2e416-223">Slider-Klasse</span><span class="sxs-lookup"><span data-stu-id="2e416-223">Slider class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209614)
