---
author: Jwmsft
Description: "Der Umschalter stellt einen physischen Schalter dar, mit dem Benutzer Dinge ein- oder ausschalten können."
title: "Richtlinien für Umschaltersteuerelemente"
ms.assetid: 753CFEA4-80D3-474C-B4A9-555F872A3DEF
label: Toggle switches
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
pm-contact: kisai
design-contact: kimsea
dev-contact: mitra
doc-status: Published
ms.openlocfilehash: 7cc1d11035d072fdd52bdfa4a1d0c6e66926ba9f
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="toggle-switches"></a><span data-ttu-id="607e0-104">Umschalter</span><span class="sxs-lookup"><span data-stu-id="607e0-104">Toggle switches</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="607e0-105">Der [Umschalter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx) stellt einen physischen Schalter dar, mit dem Benutzer Dinge ein- oder ausschalten können, wie ein Lichtschalter.</span><span class="sxs-lookup"><span data-stu-id="607e0-105">The [toggle switch](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx) represents a physical switch that allows users to turn things on or off, like a light switch.</span></span> <span data-ttu-id="607e0-106">Mit Umschalter-Steuerelementen können Sie Benutzern zwei Optionen anbieten, die sich gegenseitig ausschließen (wie Ein/Aus), wobei eine Option mit der Auswahl unmittelbare Ergebnisse liefert.</span><span class="sxs-lookup"><span data-stu-id="607e0-106">Use toggle switch controls to present users with two mutually exclusive options (such as on/off), where choosing an option provides immediate results.</span></span> 

<span data-ttu-id="607e0-107">Um ein Umschalter-Steuerelement zu erstellen, verwenden Sie die  [ToggleSwitch-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx).</span><span class="sxs-lookup"><span data-stu-id="607e0-107">To create a toggle switch control, you use the  [ToggleSwitch class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx).</span></span>

> <span data-ttu-id="607e0-108">**Wichtige APIs**: [ToggleSwitch-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx), [IsOn-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.ison.aspx), [Toggled-Ereignis](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.toggled.aspx)</span><span class="sxs-lookup"><span data-stu-id="607e0-108">**Important APIs**: [ToggleSwitch class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.aspx), [IsOn property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.ison.aspx), [Toggled event](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.toggled.aspx)</span></span>


## <a name="is-this-the-right-control"></a><span data-ttu-id="607e0-109">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="607e0-109">Is this the right control?</span></span>

<span data-ttu-id="607e0-110">Verwenden Sie einen Umschalter für binäre Vorgänge, die wirksam werden, sobald der Benutzer den Umschalter umstellt.</span><span class="sxs-lookup"><span data-stu-id="607e0-110">Use a toggle switch for binary operations that take effect right after the user flips the toggle switch.</span></span>

![WLAN-Umschalter ein- und ausgeschaltet](images/toggleswitches01.png)

<span data-ttu-id="607e0-112">Stellen Sie sich den Umschalter als physischen Netzschalter für ein Gerät vor: Sie schalten ihn ein oder aus, wenn Sie die vom Gerät ausgeführte Aktion aktivieren oder deaktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="607e0-112">Think of the toggle switch as a physical power switch for a device: you flip it on or off when you want to enable or disable the action performed by the device.</span></span>

<span data-ttu-id="607e0-113">Um den Umschalter leicht verständlich zu machen, kennzeichnen Sie ihn mit einem oder zwei Wörtern, vorzugsweise Substantiven, welche die von ihm gesteuerten Funktionen beschreiben,</span><span class="sxs-lookup"><span data-stu-id="607e0-113">To make the toggle switch easy to understand, label it with one or two words, preferably nouns, that describe the functionality it controls.</span></span> <span data-ttu-id="607e0-114">beispielsweise „WLAN“ oder „Küchenlicht“.</span><span class="sxs-lookup"><span data-stu-id="607e0-114">For example, "WiFi" or "Kitchen lights."</span></span>  


### <a name="choosing-between-toggle-switch-and-check-box"></a><span data-ttu-id="607e0-115">Wählen zwischen Umschalter und Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="607e0-115">Choosing between toggle switch and check box</span></span>

<span data-ttu-id="607e0-116">Für einige Aktionen kann entweder ein Umschalter oder ein Kontrollkästchen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="607e0-116">For some actions, either a toggle switch or a check box might work.</span></span> <span data-ttu-id="607e0-117">Berücksichtigen Sie bei der Entscheidung zwischen den beiden Steuerelementen folgende Überlegungen:</span><span class="sxs-lookup"><span data-stu-id="607e0-117">To decide which control would work better, follow these tips:</span></span>

-   <span data-ttu-id="607e0-118">Verwenden Sie einen Umschalter für binäre Einstellungen, wenn Änderungen direkt wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="607e0-118">Use a toggle switch for binary settings when changes become effective immediately after the user changes them.</span></span>

    ![Umschalter im Vergleich zum Kontrollkästchen](images/toggleswitches02.png)

    <span data-ttu-id="607e0-120">In diesem Beispiel ist durch den Umschalter klar, dass das WLAN aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="607e0-120">In this example, it's clear with the toggle switch that the wireless is set to "On."</span></span> <span data-ttu-id="607e0-121">Im Falle eines Kontrollkästchens muss der Benutzer erst überlegen, ob das WLAN derzeit aktiviert ist oder ob er das Kontrollkästchen aktivieren muss, um es zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="607e0-121">But with the checkbox, the user needs to think about whether the wireless is on now or whether they need to check the box to turn wireless on.</span></span>

-   <span data-ttu-id="607e0-122">Verwenden Sie Kontrollkästchen für optionale („nützliche“) Elemente.</span><span class="sxs-lookup"><span data-stu-id="607e0-122">Use check boxes for optional ("nice to have") items.</span></span> 
-   <span data-ttu-id="607e0-123">Verwenden Sie ein Kontrollkästchen, wenn der Benutzer zusätzliche Schritte ausführen muss, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="607e0-123">Use a checkbox when the user has to perform extra steps for changes to be effective.</span></span> <span data-ttu-id="607e0-124">Verwenden Sie beispielsweise ein Kontrollkästchen, wenn der Benutzer auf die Schaltfläche „Übermitteln“ oder „Weiter“ klicken muss, damit Änderungen übernommen werden.</span><span class="sxs-lookup"><span data-stu-id="607e0-124">For example, if the user must click a "submit" or "next" button to apply changes, use a check box.</span></span>
-   <span data-ttu-id="607e0-125">Verwenden Sie Kontrollkästchen, wenn der Benutzer mehrere Elemente auswählen kann, die sich auf eine einzelne Einstellung oder ein einzelnes Feature beziehen.</span><span class="sxs-lookup"><span data-stu-id="607e0-125">Use check boxes when the user can select multiple items that are related to a single setting or feature.</span></span> 

## <a name="toggle-switches-in-the-the-windows-ui"></a><span data-ttu-id="607e0-126">Umschalter in der Windows-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="607e0-126">Toggle switches in the the Windows UI</span></span>

<span data-ttu-id="607e0-127">Diese Bilder zeigen, wie Umschalter in der Windows-Benutzeroberfläche verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="607e0-127">These images show how the Windows UI uses toggle switches.</span></span> <span data-ttu-id="607e0-128">Hier sehen Sie, wie Umschalter auf der Seite für intelligente Speichereinstellungen verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="607e0-128">Here's how the Smart Storage Settings screen uses toggle switches:</span></span>

![Umschalter in intelligentem Speicher](images/SmartStorageToggle.png)

<span data-ttu-id="607e0-130">Dieses Beispiel stammt aus der Seite für Nachtlichteinstellungen:</span><span class="sxs-lookup"><span data-stu-id="607e0-130">This example is from the Night Light Settings page:</span></span>

![Umschalter in den Einstellungen für das Menü „Start” in Windows](images/NightLightToggle.png)

## <a name="create-a-toggle-switch"></a><span data-ttu-id="607e0-132">Erstellen von Umschaltern</span><span class="sxs-lookup"><span data-stu-id="607e0-132">Create a toggle switch</span></span>

<span data-ttu-id="607e0-133">Hier sehen Sie, wie Sie einen einfachen Umschalter erstellen.</span><span class="sxs-lookup"><span data-stu-id="607e0-133">Here's how to create a simple toggle switch.</span></span> <span data-ttu-id="607e0-134">Mit diesem XAML-Code wird der oben gezeigte WLAN-Umschalter erstellt.</span><span class="sxs-lookup"><span data-stu-id="607e0-134">This XAML creates the WiFi toggle switch shown previously.</span></span>

```xaml
<ToggleSwitch x:Name="wiFiToggle" Header="Wifi"/>
```
<span data-ttu-id="607e0-135">An dieser Stelle wird beschrieben, wie derselbe Umschalter im Code erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="607e0-135">Here's how to create the same toggle switch in code.</span></span>

```csharp
ToggleSwitch wiFiToggle = new ToggleSwitch();
wiFiToggle.Header = "WiFi";

// Add the toggle switch to a parent container in the visual tree.
stackPanel1.Children.Add(wiFiToggle);
```

### <a name="ison"></a><span data-ttu-id="607e0-136">IsOn</span><span class="sxs-lookup"><span data-stu-id="607e0-136">IsOn</span></span>

<span data-ttu-id="607e0-137">Der Schalter kann entweder ein- oder ausgeschaltet sein.</span><span class="sxs-lookup"><span data-stu-id="607e0-137">The switch can be either on or off.</span></span> <span data-ttu-id="607e0-138">Verwenden Sie die [IsOn](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.ison.aspx)-Eigenschaft, um den Zustand des Schalters zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="607e0-138">Use the [IsOn](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.ison.aspx) property to determine the state of the switch.</span></span> <span data-ttu-id="607e0-139">Wenn der Schalter zur Steuerung des Zustands einer anderen binären Eigenschaft verwendet wird, können Sie wie hier gezeigt eine Bindung verwenden.</span><span class="sxs-lookup"><span data-stu-id="607e0-139">When the switch is used to control the state of another binary property, you can use a binding as shown here.</span></span>

```
<StackPanel Orientation="Horizontal">
    <ToggleSwitch x:Name="ToggleSwitch1" IsOn="True"/>
    <ProgressRing IsActive="{x:Bind ToggleSwitch1.IsOn, Mode=OneWay}" Width="130"/>
</StackPanel>
```

### <a name="toggled"></a><span data-ttu-id="607e0-140">Toggled</span><span class="sxs-lookup"><span data-stu-id="607e0-140">Toggled</span></span>

<span data-ttu-id="607e0-141">In anderen Fällen können Sie das [Toggled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.toggled.aspx)-Ereignis zur Reaktion auf Zustandsänderungen behandeln.</span><span class="sxs-lookup"><span data-stu-id="607e0-141">In other cases, you can handle the [Toggled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.toggled.aspx) event to respond to changes in the state.</span></span>

<span data-ttu-id="607e0-142">In diesem Beispiel wird veranschaulicht, wie in XAML und im Code ein Toggled-Ereignis hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="607e0-142">This example shows how to add a Toggled event handler in XAML and in code.</span></span> <span data-ttu-id="607e0-143">Das Toggled-Ereignis wird behandelt, um einen Statusring ein- oder auszuschalten oder seine Sichtbarkeit zu ändern.</span><span class="sxs-lookup"><span data-stu-id="607e0-143">The Toggled event is handled to turn a progress ring on or off, and change its visibility.</span></span>

```xaml
<ToggleSwitch x:Name="toggleSwitch1" IsOn="True"
              Toggled="ToggleSwitch_Toggled"/>
```

<span data-ttu-id="607e0-144">An dieser Stelle wird beschrieben, wie derselbe Umschalter im Code erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="607e0-144">Here's how to create the same toggle switch in code.</span></span>

```csharp
// Create a new toggle switch and add a Toggled event handler.
ToggleSwitch toggleSwitch1 = new ToggleSwitch();
toggleSwitch1.Toggled += ToggleSwitch_Toggled;

// Add the toggle switch to a parent container in the visual tree.
stackPanel1.Children.Add(toggleSwitch1);
```

<span data-ttu-id="607e0-145">Hier sehen Sie den Handler für das Toggled-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="607e0-145">Here's the handler for the Toggled event.</span></span>

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

### <a name="onoff-labels"></a><span data-ttu-id="607e0-146">Beschriftungen „Ein”/„Aus”</span><span class="sxs-lookup"><span data-stu-id="607e0-146">On/Off labels</span></span>

<span data-ttu-id="607e0-147">Standardmäßig beinhaltet der Umschalter literalen Beschriftungen „Ein” und „Aus”, die automatisch lokalisiert werden.</span><span class="sxs-lookup"><span data-stu-id="607e0-147">By default, the toggle switch includes literal On and Off labels, which are localized automatically.</span></span> <span data-ttu-id="607e0-148">Sie können diese Beschriftungen durch Festlegen der Eigenschaften [OnContent](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.oncontent.aspx) und [OffContent](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.offcontent.aspx) ersetzen.</span><span class="sxs-lookup"><span data-stu-id="607e0-148">You can replace these labels by setting the [OnContent](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.oncontent.aspx), and [OffContent](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.offcontent.aspx) properties.</span></span>

<span data-ttu-id="607e0-149">In diesem Beispiel werden die Beschriftungen „Ein”/„Aus” durch die Beschriftungen „Einblenden”/„Ausblenden” ersetzt.</span><span class="sxs-lookup"><span data-stu-id="607e0-149">This example replaces the On/Off labels with Show/Hide labels.</span></span>  

```xaml
<ToggleSwitch x:Name="imageToggle" Header="Show images"
              OffContent="Show" OnContent="Hide"
              Toggled="ToggleSwitch_Toggled"/>
```

<span data-ttu-id="607e0-150">Sie können auch komplexeren Inhalt verwenden, indem Sie die Eigenschaften [OnContentTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.oncontenttemplate.aspx) und [OffContentTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.offcontenttemplate.aspx) verwenden.</span><span class="sxs-lookup"><span data-stu-id="607e0-150">You can also use more complex content by setting the [OnContentTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.oncontenttemplate.aspx) and [OffContentTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.toggleswitch.offcontenttemplate.aspx) properties.</span></span>

## <a name="recommendations"></a><span data-ttu-id="607e0-151">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="607e0-151">Recommendations</span></span>

-    <span data-ttu-id="607e0-152">Verwenden Sie möglichst die Standardeinstellung „Ein“ und „Aus“; ersetzen Sie diese, wenn dies erforderlich ist, damit der Umschalter Sinn ergibt.</span><span class="sxs-lookup"><span data-stu-id="607e0-152">Use the default On and Off labels when you can; only replace them when it's necessary for the toggle switch to make sense.</span></span> <span data-ttu-id="607e0-153">Wenn Sie sie ersetzen, verwenden Sie ein einzelnes Wort, das die Umschaltfläche genauer beschreibt.</span><span class="sxs-lookup"><span data-stu-id="607e0-153">If you replace them, use a single word that more accurately describes the toggle.</span></span> <span data-ttu-id="607e0-154">In der Regel gilt, dass Sie möglicherweise ein anderes Steuerelement benötigen, wenn die Wörter „Ein“ und „Aus“ die mit einem Umschalter verknüpfte Aktion nicht beschreiben.</span><span class="sxs-lookup"><span data-stu-id="607e0-154">In general, if the words "On" and "Off" don't describe the action tied to a toggle switch, you might need a different control.</span></span>
-    <span data-ttu-id="607e0-155">Die Beschriftungen „Ein“ und „Aus“ sollten nur ersetzt werden, falls unbedingt nötig. Behalten Sie die Standardbeschriftungen bei, sofern keine benutzerdefinierten Beschriftungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="607e0-155">Avoid replacing the On and Off labels unless you must; stick with the default labels unless the situation calls for custom ones.</span></span>


## <a name="related-articles"></a><span data-ttu-id="607e0-156">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="607e0-156">Related articles</span></span>

- [<span data-ttu-id="607e0-157">ToggleSwitch-Klasse</span><span class="sxs-lookup"><span data-stu-id="607e0-157">ToggleSwitch class</span></span>](https://msdn.microsoft.com/library/windows/apps/hh701411)
- [<span data-ttu-id="607e0-158">Optionsfelder</span><span class="sxs-lookup"><span data-stu-id="607e0-158">Radio buttons</span></span>](radio-button.md)
- [<span data-ttu-id="607e0-159">Umschalter</span><span class="sxs-lookup"><span data-stu-id="607e0-159">Toggle switches</span></span>](toggles.md)
- [<span data-ttu-id="607e0-160">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="607e0-160">Check boxes</span></span>](checkbox.md)
