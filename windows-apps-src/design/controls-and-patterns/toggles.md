---
author: serenaz
Description: The toggle switch represents a physical switch that allows users to turn things on or off.
title: Richtlinien für Umschaltersteuerelemente
ms.assetid: 753CFEA4-80D3-474C-B4A9-555F872A3DEF
label: Toggle switches
template: detail.hbs
ms.author: sezhen
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
ms.openlocfilehash: a62adf816ece7217de6f2f6cb0ccd505f0a5ad56
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1816365"
---
# <a name="toggle-switches"></a><span data-ttu-id="4f2b5-103">Umschalter</span><span class="sxs-lookup"><span data-stu-id="4f2b5-103">Toggle switches</span></span>

<span data-ttu-id="4f2b5-104">Der [Umschalter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx) stellt einen physischen Schalter dar, mit dem Benutzer Dinge ein- oder ausschalten können, wie ein Lichtschalter.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-104">The [toggle switch](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx) represents a physical switch that allows users to turn things on or off, like a light switch.</span></span> <span data-ttu-id="4f2b5-105">Mit Umschalter-Steuerelementen können Sie Benutzern zwei Optionen anbieten, die sich gegenseitig ausschließen (wie Ein/Aus), wobei eine Option mit der Auswahl unmittelbare Ergebnisse liefert.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-105">Use toggle switch controls to present users with two mutually exclusive options (such as on/off), where choosing an option provides immediate results.</span></span>

<span data-ttu-id="4f2b5-106">Um ein Umschalter-Steuerelement zu erstellen, verwenden Sie die  [ToggleSwitch-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx).</span><span class="sxs-lookup"><span data-stu-id="4f2b5-106">To create a toggle switch control, you use the  [ToggleSwitch class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx).</span></span>

> <span data-ttu-id="4f2b5-107">**Wichtige APIs**: [ToggleSwitch-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx), [IsOn-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.ison.aspx), [Toggled-Ereignis](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.toggled.aspx)</span><span class="sxs-lookup"><span data-stu-id="4f2b5-107">**Important APIs**: [ToggleSwitch class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx), [IsOn property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.ison.aspx), [Toggled event](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.toggled.aspx)</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="4f2b5-108">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="4f2b5-108">Is this the right control?</span></span>

<span data-ttu-id="4f2b5-109">Verwenden Sie einen Umschalter für binäre Vorgänge, die wirksam werden, sobald der Benutzer den Umschalter umstellt.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-109">Use a toggle switch for binary operations that take effect right after the user flips the toggle switch.</span></span>

![WLAN-Umschalter ein- und ausgeschaltet](images/toggleswitches01.png)

<span data-ttu-id="4f2b5-111">Stellen Sie sich den Umschalter als physischen Netzschalter für ein Gerät vor: Sie schalten ihn ein oder aus, wenn Sie die vom Gerät ausgeführte Aktion aktivieren oder deaktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-111">Think of the toggle switch as a physical power switch for a device: you flip it on or off when you want to enable or disable the action performed by the device.</span></span>

<span data-ttu-id="4f2b5-112">Um den Umschalter leicht verständlich zu machen, kennzeichnen Sie ihn mit einem oder zwei Wörtern, vorzugsweise Substantiven, welche die von ihm gesteuerten Funktionen beschreiben,</span><span class="sxs-lookup"><span data-stu-id="4f2b5-112">To make the toggle switch easy to understand, label it with one or two words, preferably nouns, that describe the functionality it controls.</span></span> <span data-ttu-id="4f2b5-113">beispielsweise „WLAN“ oder „Küchenlicht“.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-113">For example, "WiFi" or "Kitchen lights."</span></span> 

## <a name="examples"></a><span data-ttu-id="4f2b5-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="4f2b5-114">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="4f2b5-115">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="4f2b5-115">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="4f2b5-116">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um die App zu öffnen und <a href="xamlcontrolsgallery:/item/ToggleSwitch">ToggleSwitch</a> oder <a href="xamlcontrolsgallery:/item/ToggleButton">ToggleButton</a> in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-116">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to open the app and see the <a href="xamlcontrolsgallery:/item/ToggleSwitch">ToggleSwitch</a> or <a href="xamlcontrolsgallery:/item/ToggleButton">ToggleButton</a> in action.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="4f2b5-117">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="4f2b5-117">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="4f2b5-118">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="4f2b5-118">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="choosing-between-toggle-switch-and-check-box"></a><span data-ttu-id="4f2b5-119">Wählen zwischen Umschalter und Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="4f2b5-119">Choosing between toggle switch and check box</span></span>

<span data-ttu-id="4f2b5-120">Für einige Aktionen kann entweder ein Umschalter oder ein Kontrollkästchen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-120">For some actions, either a toggle switch or a check box might work.</span></span> <span data-ttu-id="4f2b5-121">Berücksichtigen Sie bei der Entscheidung zwischen den beiden Steuerelementen folgende Überlegungen:</span><span class="sxs-lookup"><span data-stu-id="4f2b5-121">To decide which control would work better, follow these tips:</span></span>

- <span data-ttu-id="4f2b5-122">Verwenden Sie einen Umschalter für binäre Einstellungen, wenn Änderungen direkt wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-122">Use a toggle switch for binary settings when changes become effective immediately after the user changes them.</span></span>

    ![Umschalter im Vergleich zum Kontrollkästchen](images/toggleswitches02.png)

    <span data-ttu-id="4f2b5-124">In diesem Beispiel ist durch den Umschalter klar, dass das „Küchenlicht“ aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-124">In this example, it's clear with the toggle switch that the kitchen lights are set to "On."</span></span> <span data-ttu-id="4f2b5-125">Im Falle eines Kontrollkästchens muss der Benutzer erst überlegen, ob das Licht derzeit aktiviert ist oder ob er das Kontrollkästchen aktivieren muss, um das Licht zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-125">But with the checkbox, the user needs to think about whether the lights are on now or whether they need to check the box to turn the lights on.</span></span>

- <span data-ttu-id="4f2b5-126">Verwenden Sie Kontrollkästchen für optionale („nützliche“) Elemente.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-126">Use check boxes for optional ("nice to have") items.</span></span>
- <span data-ttu-id="4f2b5-127">Verwenden Sie ein Kontrollkästchen, wenn der Benutzer zusätzliche Schritte ausführen muss, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-127">Use a checkbox when the user has to perform extra steps for changes to be effective.</span></span> <span data-ttu-id="4f2b5-128">Verwenden Sie beispielsweise ein Kontrollkästchen, wenn der Benutzer auf die Schaltfläche „Übermitteln“ oder „Weiter“ klicken muss, damit Änderungen übernommen werden.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-128">For example, if the user must click a "submit" or "next" button to apply changes, use a check box.</span></span>
- <span data-ttu-id="4f2b5-129">Verwenden Sie Kontrollkästchen, wenn der Benutzer mehrere Elemente auswählen kann, die sich auf eine einzelne Einstellung oder ein einzelnes Feature beziehen.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-129">Use check boxes when the user can select multiple items that are related to a single setting or feature.</span></span>

## <a name="toggle-switches-in-the-the-windows-ui"></a><span data-ttu-id="4f2b5-130">Umschalter in der Windows-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="4f2b5-130">Toggle switches in the the Windows UI</span></span>

<span data-ttu-id="4f2b5-131">Diese Bilder zeigen, wie Umschalter in der Windows-Benutzeroberfläche verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-131">These images show how the Windows UI uses toggle switches.</span></span> <span data-ttu-id="4f2b5-132">Hier sehen Sie, wie Umschalter auf der Seite für intelligente Speichereinstellungen verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="4f2b5-132">Here's how the Smart Storage Settings screen uses toggle switches:</span></span>

![Umschalter in intelligentem Speicher](images/SmartStorageToggle.png)

<span data-ttu-id="4f2b5-134">Dieses Beispiel stammt aus der Seite für Nachtlichteinstellungen:</span><span class="sxs-lookup"><span data-stu-id="4f2b5-134">This example is from the Night Light Settings page:</span></span>

![Umschalter in den Einstellungen für das Menü „Start” in Windows](images/NightLightToggle.png)

## <a name="create-a-toggle-switch"></a><span data-ttu-id="4f2b5-136">Erstellen von Umschaltern</span><span class="sxs-lookup"><span data-stu-id="4f2b5-136">Create a toggle switch</span></span>

<span data-ttu-id="4f2b5-137">Hier sehen Sie, wie Sie einen einfachen Umschalter erstellen.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-137">Here's how to create a simple toggle switch.</span></span> <span data-ttu-id="4f2b5-138">Mit diesem XAML-Code wird der oben gezeigte Umschalter erstellt.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-138">This XAML creates the toggle switch shown previously.</span></span>

```xaml
<ToggleSwitch x:Name="lightToggle" Header="Kitchen Lights"/>
```

<span data-ttu-id="4f2b5-139">An dieser Stelle wird beschrieben, wie derselbe Umschalter im Code erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-139">Here's how to create the same toggle switch in code.</span></span>

```csharp
ToggleSwitch lightToggle = new ToggleSwitch();
lightToggle.Header = "Kitchen Lights";

// Add the toggle switch to a parent container in the visual tree.
stackPanel1.Children.Add(lightToggle);
```

### <a name="ison"></a><span data-ttu-id="4f2b5-140">IsOn</span><span class="sxs-lookup"><span data-stu-id="4f2b5-140">IsOn</span></span>

<span data-ttu-id="4f2b5-141">Der Schalter kann entweder ein- oder ausgeschaltet sein.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-141">The switch can be either on or off.</span></span> <span data-ttu-id="4f2b5-142">Verwenden Sie die [IsOn](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.ison.aspx)-Eigenschaft, um den Zustand des Schalters zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-142">Use the [IsOn](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.ison.aspx) property to determine the state of the switch.</span></span> <span data-ttu-id="4f2b5-143">Wenn der Schalter zur Steuerung des Zustands einer anderen binären Eigenschaft verwendet wird, können Sie wie hier gezeigt eine Bindung verwenden.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-143">When the switch is used to control the state of another binary property, you can use a binding as shown here.</span></span>

```xaml
<StackPanel Orientation="Horizontal">
    <ToggleSwitch x:Name="ToggleSwitch1" IsOn="True"/>
    <ProgressRing IsActive="{x:Bind ToggleSwitch1.IsOn, Mode=OneWay}" Width="130"/>
</StackPanel>
```

### <a name="toggled"></a><span data-ttu-id="4f2b5-144">Toggled</span><span class="sxs-lookup"><span data-stu-id="4f2b5-144">Toggled</span></span>

<span data-ttu-id="4f2b5-145">In anderen Fällen können Sie das [Toggled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.toggled.aspx)-Ereignis zur Reaktion auf Zustandsänderungen behandeln.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-145">In other cases, you can handle the [Toggled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.toggled.aspx) event to respond to changes in the state.</span></span>

<span data-ttu-id="4f2b5-146">In diesem Beispiel wird veranschaulicht, wie in XAML und im Code ein Toggled-Ereignis hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-146">This example shows how to add a Toggled event handler in XAML and in code.</span></span> <span data-ttu-id="4f2b5-147">Das Toggled-Ereignis wird behandelt, um einen Statusring ein- oder auszuschalten oder seine Sichtbarkeit zu ändern.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-147">The Toggled event is handled to turn a progress ring on or off, and change its visibility.</span></span>

```xaml
<ToggleSwitch x:Name="toggleSwitch1" IsOn="True"
              Toggled="ToggleSwitch_Toggled"/>
```

<span data-ttu-id="4f2b5-148">An dieser Stelle wird beschrieben, wie derselbe Umschalter im Code erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-148">Here's how to create the same toggle switch in code.</span></span>

```csharp
// Create a new toggle switch and add a Toggled event handler.
ToggleSwitch toggleSwitch1 = new ToggleSwitch();
toggleSwitch1.Toggled += ToggleSwitch_Toggled;

// Add the toggle switch to a parent container in the visual tree.
stackPanel1.Children.Add(toggleSwitch1);
```

<span data-ttu-id="4f2b5-149">Hier sehen Sie den Handler für das Toggled-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-149">Here's the handler for the Toggled event.</span></span>

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

### <a name="onoff-labels"></a><span data-ttu-id="4f2b5-150">Beschriftungen „Ein”/„Aus”</span><span class="sxs-lookup"><span data-stu-id="4f2b5-150">On/Off labels</span></span>

<span data-ttu-id="4f2b5-151">Standardmäßig beinhaltet der Umschalter literalen Beschriftungen „Ein” und „Aus”, die automatisch lokalisiert werden.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-151">By default, the toggle switch includes literal On and Off labels, which are localized automatically.</span></span> <span data-ttu-id="4f2b5-152">Sie können diese Beschriftungen durch Festlegen der Eigenschaften [OnContent](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.oncontent.aspx) und [OffContent](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.offcontent.aspx) ersetzen.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-152">You can replace these labels by setting the [OnContent](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.oncontent.aspx), and [OffContent](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.offcontent.aspx) properties.</span></span>

<span data-ttu-id="4f2b5-153">In diesem Beispiel werden die Beschriftungen „Ein”/„Aus” durch die Beschriftungen „Einblenden”/„Ausblenden” ersetzt.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-153">This example replaces the On/Off labels with Show/Hide labels.</span></span>

```xaml
<ToggleSwitch x:Name="imageToggle" Header="Show images"
              OffContent="Show" OnContent="Hide"
              Toggled="ToggleSwitch_Toggled"/>
```

<span data-ttu-id="4f2b5-154">Sie können auch komplexeren Inhalt verwenden, indem Sie die Eigenschaften [OnContentTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.oncontenttemplate.aspx) und [OffContentTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.offcontenttemplate.aspx) verwenden.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-154">You can also use more complex content by setting the [OnContentTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.oncontenttemplate.aspx) and [OffContentTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.offcontenttemplate.aspx) properties.</span></span>

## <a name="recommendations"></a><span data-ttu-id="4f2b5-155">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4f2b5-155">Recommendations</span></span>

- <span data-ttu-id="4f2b5-156">Verwenden Sie möglichst die Standardeinstellung „Ein“ und „Aus“; ersetzen Sie diese, wenn dies erforderlich ist, damit der Umschalter Sinn ergibt.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-156">Use the default On and Off labels when you can; only replace them when it's necessary for the toggle switch to make sense.</span></span> <span data-ttu-id="4f2b5-157">Wenn Sie sie ersetzen, verwenden Sie ein einzelnes Wort, das die Umschaltfläche genauer beschreibt.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-157">If you replace them, use a single word that more accurately describes the toggle.</span></span> <span data-ttu-id="4f2b5-158">In der Regel gilt, dass Sie möglicherweise ein anderes Steuerelement benötigen, wenn die Wörter „Ein“ und „Aus“ die mit einem Umschalter verknüpfte Aktion nicht beschreiben.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-158">In general, if the words "On" and "Off" don't describe the action tied to a toggle switch, you might need a different control.</span></span>
- <span data-ttu-id="4f2b5-159">Die Beschriftungen „Ein“ und „Aus“ sollten nur ersetzt werden, falls unbedingt nötig. Behalten Sie die Standardbeschriftungen bei, sofern keine benutzerdefinierten Beschriftungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-159">Avoid replacing the On and Off labels unless you must; stick with the default labels unless the situation calls for custom ones.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="4f2b5-160">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="4f2b5-160">Get the sample code</span></span>

- <span data-ttu-id="4f2b5-161">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="4f2b5-161">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="4f2b5-162">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="4f2b5-162">Related articles</span></span>

- [<span data-ttu-id="4f2b5-163">ToggleSwitch-Klasse</span><span class="sxs-lookup"><span data-stu-id="4f2b5-163">ToggleSwitch class</span></span>](https://msdn.microsoft.com/library/windows/apps/hh701411)
- [<span data-ttu-id="4f2b5-164">Optionsfelder</span><span class="sxs-lookup"><span data-stu-id="4f2b5-164">Radio buttons</span></span>](radio-button.md)
- [<span data-ttu-id="4f2b5-165">Umschalter</span><span class="sxs-lookup"><span data-stu-id="4f2b5-165">Toggle switches</span></span>](toggles.md)
- [<span data-ttu-id="4f2b5-166">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="4f2b5-166">Check boxes</span></span>](checkbox.md)
