---
author: QuinnRadich
Description: The toggle switch represents a physical switch that allows users to turn things on or off.
title: Richtlinien für Umschaltersteuerelemente
ms.assetid: 753CFEA4-80D3-474C-B4A9-555F872A3DEF
label: Toggle switches
template: detail.hbs
ms.author: quradic
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
pm-contact: kisai
design-contact: kimsea
dev-contact: mitra
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: daffbc5ff74adc234ac6c2b414a7e1b85763849d
ms.sourcegitcommit: 72710baeee8c898b5ab77ceb66d884eaa9db4cb8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2018
ms.locfileid: "3846274"
---
# <a name="toggle-switches"></a><span data-ttu-id="4292d-103">Umschalter</span><span class="sxs-lookup"><span data-stu-id="4292d-103">Toggle switches</span></span>

<span data-ttu-id="4292d-104">Der Umschalter stellt einen physischen Schalter dar, mit dem Benutzer Dinge ein- oder ausschalten können, wie ein Lichtschalter.</span><span class="sxs-lookup"><span data-stu-id="4292d-104">The toggle switch represents a physical switch that allows users to turn things on or off, like a light switch.</span></span> <span data-ttu-id="4292d-105">Mit Umschalter-Steuerelementen können Sie Benutzern zwei Optionen anbieten, die sich gegenseitig ausschließen (wie Ein/Aus), wobei eine Option mit der Auswahl unmittelbare Ergebnisse liefert.</span><span class="sxs-lookup"><span data-stu-id="4292d-105">Use toggle switch controls to present users with two mutually exclusive options (such as on/off), where choosing an option provides immediate results.</span></span>

<span data-ttu-id="4292d-106">Um ein Umschalter-Steuerelement zu erstellen, verwenden Sie die  [ToggleSwitch-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch).</span><span class="sxs-lookup"><span data-stu-id="4292d-106">To create a toggle switch control, you use the  [ToggleSwitch class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch).</span></span>

> <span data-ttu-id="4292d-107">**Wichtige APIs**: [ToggleSwitch-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch), [IsOn-Eigenschaft](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.ison), [Toggled-Ereignis](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.toggled)</span><span class="sxs-lookup"><span data-stu-id="4292d-107">**Important APIs**: [ToggleSwitch class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch), [IsOn property](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.ison), [Toggled event](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.toggled)</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="4292d-108">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="4292d-108">Is this the right control?</span></span>

<span data-ttu-id="4292d-109">Verwenden Sie einen Umschalter für binäre Vorgänge, die wirksam werden, sobald der Benutzer den Umschalter umstellt.</span><span class="sxs-lookup"><span data-stu-id="4292d-109">Use a toggle switch for binary operations that take effect right after the user flips the toggle switch.</span></span>

![WLAN-Umschalter ein- und ausgeschaltet](images/toggleswitches01.png)

<span data-ttu-id="4292d-111">Stellen Sie sich den Umschalter als physischen Netzschalter für ein Gerät vor: Sie schalten ihn ein oder aus, wenn Sie die vom Gerät ausgeführte Aktion aktivieren oder deaktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="4292d-111">Think of the toggle switch as a physical power switch for a device: you flip it on or off when you want to enable or disable the action performed by the device.</span></span>

<span data-ttu-id="4292d-112">Um den Umschalter leicht verständlich zu machen, kennzeichnen Sie ihn mit einem oder zwei Wörtern, vorzugsweise Substantiven, welche die von ihm gesteuerten Funktionen beschreiben,</span><span class="sxs-lookup"><span data-stu-id="4292d-112">To make the toggle switch easy to understand, label it with one or two words, preferably nouns, that describe the functionality it controls.</span></span> <span data-ttu-id="4292d-113">beispielsweise „WLAN“ oder „Küchenlicht“.</span><span class="sxs-lookup"><span data-stu-id="4292d-113">For example, "WiFi" or "Kitchen lights."</span></span> 

## <a name="examples"></a><span data-ttu-id="4292d-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="4292d-114">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="4292d-115">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="4292d-115">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="4292d-116">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um die App zu öffnen und <a href="xamlcontrolsgallery:/item/ToggleSwitch">ToggleSwitch</a> oder <a href="xamlcontrolsgallery:/item/ToggleButton">ToggleButton</a> in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="4292d-116">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to open the app and see the <a href="xamlcontrolsgallery:/item/ToggleSwitch">ToggleSwitch</a> or <a href="xamlcontrolsgallery:/item/ToggleButton">ToggleButton</a> in action.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="4292d-117">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="4292d-117">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="4292d-118">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="4292d-118">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="choosing-between-toggle-switch-and-check-box"></a><span data-ttu-id="4292d-119">Wählen zwischen Umschalter und Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="4292d-119">Choosing between toggle switch and check box</span></span>

<span data-ttu-id="4292d-120">Für einige Aktionen kann entweder ein Umschalter oder ein Kontrollkästchen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4292d-120">For some actions, either a toggle switch or a check box might work.</span></span> <span data-ttu-id="4292d-121">Berücksichtigen Sie bei der Entscheidung zwischen den beiden Steuerelementen folgende Überlegungen:</span><span class="sxs-lookup"><span data-stu-id="4292d-121">To decide which control would work better, follow these tips:</span></span>

- <span data-ttu-id="4292d-122">Verwenden Sie einen Umschalter für binäre Einstellungen, wenn Änderungen direkt wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="4292d-122">Use a toggle switch for binary settings when changes become effective immediately after the user changes them.</span></span>

    ![Umschalter im Vergleich zum Kontrollkästchen](images/toggleswitches02.png)

    <span data-ttu-id="4292d-124">In diesem Beispiel ist durch den Umschalter klar, dass das „Küchenlicht“ aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="4292d-124">In this example, it's clear with the toggle switch that the kitchen lights are set to "On."</span></span> <span data-ttu-id="4292d-125">Im Falle eines Kontrollkästchens muss der Benutzer erst überlegen, ob das Licht derzeit aktiviert ist oder ob er das Kontrollkästchen aktivieren muss, um das Licht zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4292d-125">But with the checkbox, the user needs to think about whether the lights are on now or whether they need to check the box to turn the lights on.</span></span>

- <span data-ttu-id="4292d-126">Verwenden Sie Kontrollkästchen für optionale („nützliche“) Elemente.</span><span class="sxs-lookup"><span data-stu-id="4292d-126">Use check boxes for optional ("nice to have") items.</span></span>
- <span data-ttu-id="4292d-127">Verwenden Sie ein Kontrollkästchen, wenn der Benutzer zusätzliche Schritte ausführen muss, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="4292d-127">Use a checkbox when the user has to perform extra steps for changes to be effective.</span></span> <span data-ttu-id="4292d-128">Verwenden Sie beispielsweise ein Kontrollkästchen, wenn der Benutzer auf die Schaltfläche „Übermitteln“ oder „Weiter“ klicken muss, damit Änderungen übernommen werden.</span><span class="sxs-lookup"><span data-stu-id="4292d-128">For example, if the user must click a "submit" or "next" button to apply changes, use a check box.</span></span>
- <span data-ttu-id="4292d-129">Verwenden Sie Kontrollkästchen, wenn der Benutzer mehrere Elemente auswählen kann, die sich auf eine einzelne Einstellung oder ein einzelnes Feature beziehen.</span><span class="sxs-lookup"><span data-stu-id="4292d-129">Use check boxes when the user can select multiple items that are related to a single setting or feature.</span></span>

## <a name="toggle-switches-in-the-the-windows-ui"></a><span data-ttu-id="4292d-130">Umschalter in der Windows-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="4292d-130">Toggle switches in the the Windows UI</span></span>

<span data-ttu-id="4292d-131">Diese Bilder zeigen, wie Umschalter in der Windows-Benutzeroberfläche verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4292d-131">These images show how the Windows UI uses toggle switches.</span></span> <span data-ttu-id="4292d-132">Hier sehen Sie, wie Umschalter auf der Seite für intelligente Speichereinstellungen verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="4292d-132">Here's how the Smart Storage Settings screen uses toggle switches:</span></span>

![Umschalter in intelligentem Speicher](images/SmartStorageToggle.png)

<span data-ttu-id="4292d-134">Dieses Beispiel stammt aus der Seite für Nachtlichteinstellungen:</span><span class="sxs-lookup"><span data-stu-id="4292d-134">This example is from the Night Light Settings page:</span></span>

![Umschalter in den Einstellungen für das Menü „Start” in Windows](images/NightLightToggle.png)

## <a name="create-a-toggle-switch"></a><span data-ttu-id="4292d-136">Erstellen von Umschaltern</span><span class="sxs-lookup"><span data-stu-id="4292d-136">Create a toggle switch</span></span>

<span data-ttu-id="4292d-137">Hier sehen Sie, wie Sie einen einfachen Umschalter erstellen.</span><span class="sxs-lookup"><span data-stu-id="4292d-137">Here's how to create a simple toggle switch.</span></span> <span data-ttu-id="4292d-138">Mit diesem XAML-Code wird der oben gezeigte Umschalter erstellt.</span><span class="sxs-lookup"><span data-stu-id="4292d-138">This XAML creates the toggle switch shown previously.</span></span>

```xaml
<ToggleSwitch x:Name="lightToggle" Header="Kitchen Lights"/>
```

<span data-ttu-id="4292d-139">An dieser Stelle wird beschrieben, wie derselbe Umschalter im Code erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="4292d-139">Here's how to create the same toggle switch in code.</span></span>

```csharp
ToggleSwitch lightToggle = new ToggleSwitch();
lightToggle.Header = "Kitchen Lights";

// Add the toggle switch to a parent container in the visual tree.
stackPanel1.Children.Add(lightToggle);
```

### <a name="ison"></a><span data-ttu-id="4292d-140">IsOn</span><span class="sxs-lookup"><span data-stu-id="4292d-140">IsOn</span></span>

<span data-ttu-id="4292d-141">Der Schalter kann entweder ein- oder ausgeschaltet sein.</span><span class="sxs-lookup"><span data-stu-id="4292d-141">The switch can be either on or off.</span></span> <span data-ttu-id="4292d-142">Verwenden Sie die [IsOn](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.ison)-Eigenschaft, um den Zustand des Schalters zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="4292d-142">Use the [IsOn](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.ison) property to determine the state of the switch.</span></span> <span data-ttu-id="4292d-143">Wenn der Schalter zur Steuerung des Zustands einer anderen binären Eigenschaft verwendet wird, können Sie wie hier gezeigt eine Bindung verwenden.</span><span class="sxs-lookup"><span data-stu-id="4292d-143">When the switch is used to control the state of another binary property, you can use a binding as shown here.</span></span>

```xaml
<StackPanel Orientation="Horizontal">
    <ToggleSwitch x:Name="ToggleSwitch1" IsOn="True"/>
    <ProgressRing IsActive="{x:Bind ToggleSwitch1.IsOn, Mode=OneWay}" Width="130"/>
</StackPanel>
```

### <a name="toggled"></a><span data-ttu-id="4292d-144">Toggled</span><span class="sxs-lookup"><span data-stu-id="4292d-144">Toggled</span></span>

<span data-ttu-id="4292d-145">In anderen Fällen können Sie das [Toggled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.toggled)-Ereignis zur Reaktion auf Zustandsänderungen behandeln.</span><span class="sxs-lookup"><span data-stu-id="4292d-145">In other cases, you can handle the [Toggled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.toggled) event to respond to changes in the state.</span></span>

<span data-ttu-id="4292d-146">In diesem Beispiel wird veranschaulicht, wie in XAML und im Code ein Toggled-Ereignis hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="4292d-146">This example shows how to add a Toggled event handler in XAML and in code.</span></span> <span data-ttu-id="4292d-147">Das Toggled-Ereignis wird behandelt, um einen Statusring ein- oder auszuschalten oder seine Sichtbarkeit zu ändern.</span><span class="sxs-lookup"><span data-stu-id="4292d-147">The Toggled event is handled to turn a progress ring on or off, and change its visibility.</span></span>

```xaml
<ToggleSwitch x:Name="toggleSwitch1" IsOn="True"
              Toggled="ToggleSwitch_Toggled"/>
```

<span data-ttu-id="4292d-148">An dieser Stelle wird beschrieben, wie derselbe Umschalter im Code erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="4292d-148">Here's how to create the same toggle switch in code.</span></span>

```csharp
// Create a new toggle switch and add a Toggled event handler.
ToggleSwitch toggleSwitch1 = new ToggleSwitch();
toggleSwitch1.Toggled += ToggleSwitch_Toggled;

// Add the toggle switch to a parent container in the visual tree.
stackPanel1.Children.Add(toggleSwitch1);
```

<span data-ttu-id="4292d-149">Hier sehen Sie den Handler für das Toggled-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="4292d-149">Here's the handler for the Toggled event.</span></span>

```csharp
private void ToggleSwitch_Toggled(object sender, RoutedEventArgs e)
{
    ToggleSwitch toggleSwitch = sender as ToggleSwitch;
    if (toggleSwitch != null)
    {
        if (toggleSwitch.IsOn == true)
        {
            progress1.IsActive = true;
            progress1.Visibility = Visibility.Visible;
        }
        else
        {
            progress1.IsActive = false;
            progress1.Visibility = Visibility.Collapsed;
        }
    }
}
```

### <a name="onoff-labels"></a><span data-ttu-id="4292d-150">Beschriftungen „Ein”/„Aus”</span><span class="sxs-lookup"><span data-stu-id="4292d-150">On/Off labels</span></span>

<span data-ttu-id="4292d-151">Standardmäßig beinhaltet der Umschalter literalen Beschriftungen „Ein” und „Aus”, die automatisch lokalisiert werden.</span><span class="sxs-lookup"><span data-stu-id="4292d-151">By default, the toggle switch includes literal On and Off labels, which are localized automatically.</span></span> <span data-ttu-id="4292d-152">Sie können diese Beschriftungen durch Festlegen der Eigenschaften [OnContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.oncontent) und [OffContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.offcontent) ersetzen.</span><span class="sxs-lookup"><span data-stu-id="4292d-152">You can replace these labels by setting the [OnContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.oncontent), and [OffContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.offcontent) properties.</span></span>

<span data-ttu-id="4292d-153">In diesem Beispiel werden die Beschriftungen „Ein”/„Aus” durch die Beschriftungen „Einblenden”/„Ausblenden” ersetzt.</span><span class="sxs-lookup"><span data-stu-id="4292d-153">This example replaces the On/Off labels with Show/Hide labels.</span></span>

```xaml
<ToggleSwitch x:Name="imageToggle" Header="Show images"
              OffContent="Show" OnContent="Hide"
              Toggled="ToggleSwitch_Toggled"/>
```

<span data-ttu-id="4292d-154">Sie können auch komplexeren Inhalt verwenden, indem Sie die Eigenschaften [OnContentTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.oncontenttemplate) und [OffContentTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.offcontenttemplate) verwenden.</span><span class="sxs-lookup"><span data-stu-id="4292d-154">You can also use more complex content by setting the [OnContentTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.oncontenttemplate) and [OffContentTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch.offcontenttemplate) properties.</span></span>

## <a name="recommendations"></a><span data-ttu-id="4292d-155">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4292d-155">Recommendations</span></span>

- <span data-ttu-id="4292d-156">Verwenden Sie möglichst die Standardeinstellung „Ein“ und „Aus“; ersetzen Sie diese, wenn dies erforderlich ist, damit der Umschalter Sinn ergibt.</span><span class="sxs-lookup"><span data-stu-id="4292d-156">Use the default On and Off labels when you can; only replace them when it's necessary for the toggle switch to make sense.</span></span> <span data-ttu-id="4292d-157">Wenn Sie sie ersetzen, verwenden Sie ein einzelnes Wort, das die Umschaltfläche genauer beschreibt.</span><span class="sxs-lookup"><span data-stu-id="4292d-157">If you replace them, use a single word that more accurately describes the toggle.</span></span> <span data-ttu-id="4292d-158">In der Regel gilt, dass Sie möglicherweise ein anderes Steuerelement benötigen, wenn die Wörter „Ein“ und „Aus“ die mit einem Umschalter verknüpfte Aktion nicht beschreiben.</span><span class="sxs-lookup"><span data-stu-id="4292d-158">In general, if the words "On" and "Off" don't describe the action tied to a toggle switch, you might need a different control.</span></span>
- <span data-ttu-id="4292d-159">Die Beschriftungen „Ein“ und „Aus“ sollten nur ersetzt werden, falls unbedingt nötig. Behalten Sie die Standardbeschriftungen bei, sofern keine benutzerdefinierten Beschriftungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="4292d-159">Avoid replacing the On and Off labels unless you must; stick with the default labels unless the situation calls for custom ones.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="4292d-160">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="4292d-160">Get the sample code</span></span>

- <span data-ttu-id="4292d-161">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="4292d-161">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="4292d-162">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="4292d-162">Related articles</span></span>

- [<span data-ttu-id="4292d-163">ToggleSwitch-Klasse</span><span class="sxs-lookup"><span data-stu-id="4292d-163">ToggleSwitch class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.toggleswitch)
- [<span data-ttu-id="4292d-164">Optionsfelder</span><span class="sxs-lookup"><span data-stu-id="4292d-164">Radio buttons</span></span>](radio-button.md)
- [<span data-ttu-id="4292d-165">Umschalter</span><span class="sxs-lookup"><span data-stu-id="4292d-165">Toggle switches</span></span>](toggles.md)
- [<span data-ttu-id="4292d-166">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="4292d-166">Check boxes</span></span>](checkbox.md)
