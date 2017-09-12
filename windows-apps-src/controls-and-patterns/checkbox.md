---
author: Jwmsft
Description: "Dient zum Aktivieren oder Deaktivieren von Aktionselementen. Kann für einzelne oder mehrere Listenelemente verwendet werden."
title: "Kontrollkästchen"
ms.assetid: 6231A806-287D-43EE-BD8D-39D2FF761914
label: Check boxes
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: kisai
design-contact: kimsea
dev-contact: mitra
doc-status: Published
ms.openlocfilehash: 13ca87313835541abffe6190d8a3bc07e67b40f8
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="check-boxes"></a><span data-ttu-id="82ff4-105">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="82ff4-105">Check boxes</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="82ff4-106">Ein Kontrollkästchen dient zum Aktivieren oder Deaktivieren von Aktionselementen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-106">A check box is used to select or deselect action items.</span></span> <span data-ttu-id="82ff4-107">Es kann für einzelne oder mehrere Listenelemente verwendet werden, die dem Benutzer zur Auswahl stehen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-107">It can be used for a single item or for a list of multiple items that a user can choose from.</span></span> <span data-ttu-id="82ff4-108">Das Steuerelement verfügt über drei Auswahlzustände: „Deaktiviert“, „Aktiviert“ und „Unbestimmt“.</span><span class="sxs-lookup"><span data-stu-id="82ff4-108">The control has three selection states: unselected, selected, and indeterminate.</span></span> <span data-ttu-id="82ff4-109">Verwenden Sie den unbestimmten Zustand, wenn für eine Sammlung von Unteroptionen eine Mischung aus deaktivierten als aktivierten Zuständen vorliegt.</span><span class="sxs-lookup"><span data-stu-id="82ff4-109">Use the indeterminate state when a collection of sub-choices have both unselected and selected states.</span></span>

> <span data-ttu-id="82ff4-110">**Wichtige APIs:** [Klasse „CheckBox“](https://msdn.microsoft.com/library/windows/apps/br209316), [Ereignis „Checked“](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.checked.aspx), [Eigenschaft „IsChecked“](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.ischecked.aspx)</span><span class="sxs-lookup"><span data-stu-id="82ff4-110">**Important APIs**: [CheckBox class](https://msdn.microsoft.com/library/windows/apps/br209316), [Checked event](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.checked.aspx), [IsChecked property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.ischecked.aspx)</span></span>

![Beispiel für Kontrollkästchenzustände](images/templates-checkbox-states-default.png)


## <a name="is-this-the-right-control"></a><span data-ttu-id="82ff4-112">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="82ff4-112">Is this the right control?</span></span>

<span data-ttu-id="82ff4-113">Verwenden Sie ein **einzelnes Kontrollkästchen** für eine binäre Ja/Nein-Auswahl – beispielsweise für ein Anmeldeszenario vom Typ „E-Mail-Adresse speichern?”</span><span class="sxs-lookup"><span data-stu-id="82ff4-113">Use a **single check box** for a binary yes/no choice, such as with a "Remember me?"</span></span> <span data-ttu-id="82ff4-114">oder für Vertragsbedingungen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-114">login scenario or with a terms of service agreement.</span></span>

![Ein einzelnes Kontrollkästchen für eine einzelne Auswahl](images/checkbox1.png)

<span data-ttu-id="82ff4-116">Bei einer binären Auswahl besteht der Hauptunterschied zwischen einem **Kontrollkästchen** und einem [Umschalter](toggles.md) darin, dass das Kontrollkästchen für einen Zustand und der Umschalter für eine Aktion verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="82ff4-116">For a binary choice, the main difference between a **check box** and a [toggle switch](toggles.md) is that the check box is for status and the toggle switch is for action.</span></span> <span data-ttu-id="82ff4-117">Sie können das Commit einer Kontrollkästcheninteraktion (etwa im Rahmen der Übermittlung eines Formulars) verzögern, während für die Interaktion eines Umschalters sofort ein Commit ausgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="82ff4-117">You can delay committing a check box interaction (as part of a form submit, for example), while you should immediately commit a toggle switch interaction.</span></span> <span data-ttu-id="82ff4-118">Eine Mehrfachauswahl ist nur mit Kontrollkästchen möglich.</span><span class="sxs-lookup"><span data-stu-id="82ff4-118">Also, only check boxes allow for multi-selection.</span></span>

<span data-ttu-id="82ff4-119">Verwenden Sie **mehrere Kontrollkästchen** für Mehrfachauswahlszenarien, in denen der Benutzer einzelne oder mehrere Elemente aus einer Gruppe von Optionen auswählt, die sich nicht gegenseitig ausschließen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-119">Use **multiple check boxes** for multi-select scenarios in which a user chooses one or more items from a group of choices that are not mutually exclusive.</span></span>

<span data-ttu-id="82ff4-120">Erstellen Sie eine Kontrollkästchengruppe, wenn die Benutzer eine beliebige Kombination von Optionen auswählen können.</span><span class="sxs-lookup"><span data-stu-id="82ff4-120">Create a group of check boxes when users can select any combination of options.</span></span>

![Auswählen mehrerer Optionen mit Kontrollkästchen](images/checkbox2.png)

<span data-ttu-id="82ff4-122">Bei gruppierbaren Optionen kann die gesamte Gruppe durch ein unbestimmtes Kontrollkästchen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="82ff4-122">When options can be grouped, you can use an indeterminate check box to represent the whole group.</span></span> <span data-ttu-id="82ff4-123">Verwenden Sie den unbestimmten Zustand des Kontrollkästchens, wenn ein Benutzer nur einige untergeordneten Elemente der Gruppe aktiviert.</span><span class="sxs-lookup"><span data-stu-id="82ff4-123">Use the check box's indeterminate state when a user selects some, but not all, sub-items in the group.</span></span>

![Kontrollkästchen für die Anzeige einer gemischten Auswahl](images/checkbox3.png)

<span data-ttu-id="82ff4-125">Benutzer können sowohl über **Kontrollkästchen** als auch über **Optionsfelder** eine Auswahl in einer Liste von Optionen treffen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-125">Both **check box** and **radio button** controls let the user select from a list of options.</span></span> <span data-ttu-id="82ff4-126">Mit Kontrollkästchen können Benutzer eine Kombination von Optionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-126">Check boxes let the user select a combination of options.</span></span> <span data-ttu-id="82ff4-127">Bei Optionsfeldern kann der Benutzer dagegen nur eine der (sich gegenseitig ausschließenden) Optionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-127">In contrast, radio buttons let the user make a single choice from mutually exclusive options.</span></span> <span data-ttu-id="82ff4-128">Wenn mehrere Optionen verfügbar sind, aber nur eine ausgewählt werden kann, sollten Sie ein Optionsfeld verwenden.</span><span class="sxs-lookup"><span data-stu-id="82ff4-128">When there is more than one option but only one can be selected, use a radio button instead.</span></span>


## <a name="create-a-checkbox"></a><span data-ttu-id="82ff4-129">Erstellen eines Kontrollkästchens</span><span class="sxs-lookup"><span data-stu-id="82ff4-129">Create a checkbox</span></span>

<span data-ttu-id="82ff4-130">Legen Sie einen Wert für die Eigenschaft [Content](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentcontrol.content.aspx) fest, um dem Kontrollkästchen eine Beschriftung zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-130">To assign a label to the checkbox, set the [Content](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentcontrol.content.aspx) property.</span></span> <span data-ttu-id="82ff4-131">Die Beschriftung wird neben dem Kontrollkästchen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="82ff4-131">The label displays next to the checkbox.</span></span>

<span data-ttu-id="82ff4-132">Der folgende XAML-Code erstellt ein einzelnes Kontrollkästchen, mit dem vor dem Übermitteln eines Formulars den Servicebedingungen zugestimmt werden muss:</span><span class="sxs-lookup"><span data-stu-id="82ff4-132">This XAML creates a single check box that is used to agree to terms of service before a form can be submitted.</span></span> 

```xaml
<CheckBox x:Name="termsOfServiceCheckBox" 
          Content="I agree to the terms of service."/>
```

<span data-ttu-id="82ff4-133">Hier sehen Sie das gleiche Kontrollkästchen im Code:</span><span class="sxs-lookup"><span data-stu-id="82ff4-133">Here's the same check box created in code.</span></span>

```csharp
CheckBox checkBox1 = new CheckBox();
checkBox1.Content = "I agree to the terms of service.";
```

### <a name="bind-to-ischecked"></a><span data-ttu-id="82ff4-134">Binden an „IsChecked“</span><span class="sxs-lookup"><span data-stu-id="82ff4-134">Bind to IsChecked</span></span>

<span data-ttu-id="82ff4-135">Über die Eigenschaft [IsChecked](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.ischecked.aspx) können Sie den Aktivierungszustand des Kontrollkästchens ermitteln.</span><span class="sxs-lookup"><span data-stu-id="82ff4-135">Use the [IsChecked](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.ischecked.aspx) property to determine whether the check box is checked or cleared.</span></span> <span data-ttu-id="82ff4-136">Der Wert der IsChecked-Eigenschaft kann an einen anderen binären Wert gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="82ff4-136">You can bind the value of the IsChecked property to another binary value.</span></span> <span data-ttu-id="82ff4-137">Da es sich bei „IsChecked“ aber um einen booleschen Wert vom Typ [Nullable](https://msdn.microsoft.com/library/windows/apps/b3h38hb0.aspx) handelt, müssen Sie einen Wertkonverter verwenden, um sie an einen booleschen Wert zu binden.</span><span class="sxs-lookup"><span data-stu-id="82ff4-137">However, because IsChecked is a [nullable](https://msdn.microsoft.com/library/windows/apps/b3h38hb0.aspx) boolean value, you must use a value converter to bind it to a boolean value.</span></span>

<span data-ttu-id="82ff4-138">In diesem Beispiel wird die **IsChecked**-Eigenschaft des Kontrollkästchens zum Akzeptieren der Servicebedingungen an die [IsEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.isenabled.aspx)-Eigenschaft der Schaltfläche zum Absenden gebunden.</span><span class="sxs-lookup"><span data-stu-id="82ff4-138">In this example, the **IsChecked** property of the check box to agree to terms of service is bound to the [IsEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.isenabled.aspx) property of a Submit button.</span></span> <span data-ttu-id="82ff4-139">Die Schaltfläche zum Absenden wird nur aktiviert, wenn die Vertragsbedingungen akzeptiert werden.</span><span class="sxs-lookup"><span data-stu-id="82ff4-139">The Submit button is enabled only if the terms of service are agreed to.</span></span>

> <span data-ttu-id="82ff4-140">Hinweis&nbsp;&nbsp;Wir zeigen hier nur den relevanten Code.</span><span class="sxs-lookup"><span data-stu-id="82ff4-140">Note&nbsp;&nbsp;We only show the relevant code here.</span></span> <span data-ttu-id="82ff4-141">Weitere Informationen zu Datenbindungen und Wertkonvertern finden Sie unter [Übersicht "Datenbindung"](../data-binding/data-binding-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="82ff4-141">For more info about data binding and value converters, see [Data binding overview](../data-binding/data-binding-quickstart.md).</span></span>

```xaml
...
<Page.Resources>
    <local:NullableBooleanToBooleanConverter x:Key="NullableBooleanToBooleanConverter"/>
</Page.Resources>

...

<StackPanel Grid.Column="2" Margin="40">
    <CheckBox x:Name="termsOfServiceCheckBox" Content="I agree to the terms of service."/>
    <Button Content="Submit" 
            IsEnabled="{x:Bind termsOfServiceCheckBox.IsChecked, 
                        Converter={StaticResource NullableBooleanToBooleanConverter}, Mode=OneWay}"/>
</StackPanel>
```

```csharp
public class NullableBooleanToBooleanConverter : IValueConverter
{
    public object Convert(object value, Type targetType, object parameter, string language)
    {
        if (value is bool?)
        {
            return (bool)value;
        }
        return false;
    }

    public object ConvertBack(object value, Type targetType, object parameter, string language)
    {
        if (value is bool)
            return (bool)value;
        return false;
    }
}
```

### <a name="handle-click-and-checked-events"></a><span data-ttu-id="82ff4-142">Behandeln von Click- und Checked-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="82ff4-142">Handle Click and Checked events</span></span>

<span data-ttu-id="82ff4-143">Damit bei einer Änderung des Kontrollkästchenzustands eine Aktion ausgeführt wird, können Sie entweder das Ereignis [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx) behandeln oder die Ereignisse [Checked](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.checked.aspx) und [Unchecked](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.unchecked.aspx).</span><span class="sxs-lookup"><span data-stu-id="82ff4-143">To perform an action when the check box state changes, you can handle either the [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx) event, or the [Checked](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.checked.aspx) and [Unchecked](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.unchecked.aspx) events.</span></span> 

<span data-ttu-id="82ff4-144">Das **Click**-Ereignis tritt bei jeder Änderung des Aktivierungszustands auf.</span><span class="sxs-lookup"><span data-stu-id="82ff4-144">The **Click** event occurs whenever the checked state changes.</span></span> <span data-ttu-id="82ff4-145">Verwenden Sie beim Behandeln des Click-Ereignisses die **IsChecked**-Eigenschaft, um den Zustand des Kontrollkästchens zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="82ff4-145">If you handle the Click event, use the **IsChecked** property to determine the state of the check box.</span></span>

<span data-ttu-id="82ff4-146">Die Ereignisse **Checked** und **Unchecked** treten unabhängig voneinander auf.</span><span class="sxs-lookup"><span data-stu-id="82ff4-146">The **Checked** and **Unchecked** events occur independently.</span></span> <span data-ttu-id="82ff4-147">Daher müssen immer beide Ereignisse behandelt werden, um auf Zustandsänderungen des Kontrollkästchens zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="82ff4-147">If you handle these events, you should handle both of them to repsond to state changes in the check box.</span></span>

<span data-ttu-id="82ff4-148">In den folgenden Beispielen wird die Behandlung des Click-Ereignis und der Ereignisse „Checked“ und „Unchecked“ gezeigt.</span><span class="sxs-lookup"><span data-stu-id="82ff4-148">In the following examples, we show handling the Click event, and the Checked and Unchecked events.</span></span> 

<span data-ttu-id="82ff4-149">Mehrere Kontrollkästchen können den gleichen Ereignishandler verwenden.</span><span class="sxs-lookup"><span data-stu-id="82ff4-149">Multiple checkboxes can share the same event handler.</span></span> <span data-ttu-id="82ff4-150">Im folgenden Beispiel werden vier Kontrollkästchen zum Auswählen von Pizzabelägen erstellt.</span><span class="sxs-lookup"><span data-stu-id="82ff4-150">This example creates four checkboxes for selecting pizza toppings.</span></span> <span data-ttu-id="82ff4-151">Die vier Kontrollkästchen verwenden den gleichen **Click**-Ereignishandler, um die Liste mit den gewählten Belägen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="82ff4-151">The four checkboxes share the same **Click** event handler to update the list of selected toppings.</span></span>

```XAML
<StackPanel Margin="40">
    <TextBlock Text="Pizza Toppings"/>
    <CheckBox Content="Pepperoni" x:Name="pepperoniCheckbox"
              Click="toppingsCheckbox_Click"/>
    <CheckBox Content="Beef" x:Name="beefCheckbox" 
              Click="toppingsCheckbox_Click"/>
    <CheckBox Content="Mushrooms" x:Name="mushroomsCheckbox"
              Click="toppingsCheckbox_Click"/>
    <CheckBox Content="Onions" x:Name="onionsCheckbox"
              Click="toppingsCheckbox_Click"/>

    <!-- Display the selected toppings. -->
    <TextBlock Text="Toppings selected:"/>
    <TextBlock x:Name="toppingsList"/>
</StackPanel>
```

<span data-ttu-id="82ff4-152">Hier sehen Sie den Ereignishandler für das Click-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="82ff4-152">Here's the event handler for the Click event.</span></span> <span data-ttu-id="82ff4-153">Bei jedem Klick auf ein Kontrollkästchen wird der Aktivierungszustand der Kontrollkästchen überprüft und die Liste mit den gewählten Belägen aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="82ff4-153">Every time a checkbox is clicked, it examines the checkboxes to see which ones are checked and update list of selected toppings.</span></span>

```csharp
private void toppingsCheckbox_Click(object sender, RoutedEventArgs e)
{
    string selectedToppingsText = string.Empty;
    CheckBox[] checkboxes = new CheckBox[] { pepperoniCheckbox, beefCheckbox,
                                             mushroomsCheckbox, onionsCheckbox };
    foreach (CheckBox c in checkboxes)
    {
        if (c.IsChecked == true)
        {
            if (selectedToppingsText.Length > 1)
            {
                selectedToppingsText += ", ";
            }
            selectedToppingsText += c.Content;
        }
    }
    toppingsList.Text = selectedToppingsText;
}
```

### <a name="use-the-indeterminate-state"></a><span data-ttu-id="82ff4-154">Verwenden des unbestimmten Zustands</span><span class="sxs-lookup"><span data-stu-id="82ff4-154">Use the indeterminate state</span></span>

<span data-ttu-id="82ff4-155">Das CheckBox-Steuerelement erbt von [ToggleButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.aspx) und kann über drei Zustände verfügen:</span><span class="sxs-lookup"><span data-stu-id="82ff4-155">The CheckBox control inherits from [ToggleButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.aspx) and can have three states:</span></span> 

<span data-ttu-id="82ff4-156">Zustand</span><span class="sxs-lookup"><span data-stu-id="82ff4-156">State</span></span> | <span data-ttu-id="82ff4-157">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="82ff4-157">Property</span></span> | <span data-ttu-id="82ff4-158">Wert</span><span class="sxs-lookup"><span data-stu-id="82ff4-158">Value</span></span>
------|----------|------
<span data-ttu-id="82ff4-159">Aktiviert</span><span class="sxs-lookup"><span data-stu-id="82ff4-159">checked</span></span> | <span data-ttu-id="82ff4-160">IsChecked</span><span class="sxs-lookup"><span data-stu-id="82ff4-160">IsChecked</span></span> | **<span data-ttu-id="82ff4-161">true</span><span class="sxs-lookup"><span data-stu-id="82ff4-161">true</span></span>** 
<span data-ttu-id="82ff4-162">Deaktiviert</span><span class="sxs-lookup"><span data-stu-id="82ff4-162">unchecked</span></span> | <span data-ttu-id="82ff4-163">IsChecked</span><span class="sxs-lookup"><span data-stu-id="82ff4-163">IsChecked</span></span> | **<span data-ttu-id="82ff4-164">false</span><span class="sxs-lookup"><span data-stu-id="82ff4-164">false</span></span>** 
<span data-ttu-id="82ff4-165">Unbestimmt</span><span class="sxs-lookup"><span data-stu-id="82ff4-165">indeterminate</span></span> | <span data-ttu-id="82ff4-166">IsChecked</span><span class="sxs-lookup"><span data-stu-id="82ff4-166">IsChecked</span></span> | **<span data-ttu-id="82ff4-167">NULL</span><span class="sxs-lookup"><span data-stu-id="82ff4-167">null</span></span>** 

<span data-ttu-id="82ff4-168">Damit das Kontrollkästchen einen unbestimmten Zustand meldet, müssen Sie die Eigenschaft [IsThreeState](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.isthreestate.aspx) auf **true** setzen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-168">For the check box to report the indeterminate state, you must set the [IsThreeState](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.isthreestate.aspx) property to **true**.</span></span> 

<span data-ttu-id="82ff4-169">Bei gruppierbaren Optionen kann die gesamte Gruppe durch ein unbestimmtes Kontrollkästchen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="82ff4-169">When options can be grouped, you can use an indeterminate check box to represent the whole group.</span></span> <span data-ttu-id="82ff4-170">Verwenden Sie den unbestimmten Zustand des Kontrollkästchens, wenn ein Benutzer nur einige untergeordneten Elemente der Gruppe aktiviert.</span><span class="sxs-lookup"><span data-stu-id="82ff4-170">Use the check box's indeterminate state when a user selects some, but not all, sub-items in the group.</span></span>

<span data-ttu-id="82ff4-171">Im folgenden Beispiel ist die IsThreeState-Eigenschaft des Kontrollkästchens „Alle auswählen“ auf **true** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="82ff4-171">In the following example, the "Select all" checkbox has its IsThreeState property set to **true**.</span></span> <span data-ttu-id="82ff4-172">Das Kontrollkästchen „Alle auswählen“ ist aktiviert, wenn alle untergeordneten Elemente ausgewählt sind, und deaktiviert, wenn alle untergeordneten Elemente deaktiviert sind. Andernfalls ist der Zustand unbestimmt.</span><span class="sxs-lookup"><span data-stu-id="82ff4-172">The "Select all" checkbox is checked if all child elements are checked, unchecked if all child elements are unchecked, and indeterminate otherwise.</span></span>

```xaml
<StackPanel>
    <CheckBox x:Name="OptionsAllCheckBox" Content="Select all" IsThreeState="True" 
              Checked="SelectAll_Checked" Unchecked="SelectAll_Unchecked" 
              Indeterminate="SelectAll_Indeterminate"/>
    <CheckBox x:Name="Option1CheckBox" Content="Option 1" Margin="24,0,0,0" 
              Checked="Option_Checked" Unchecked="Option_Unchecked" />
    <CheckBox x:Name="Option2CheckBox" Content="Option 2" Margin="24,0,0,0" 
              Checked="Option_Checked" Unchecked="Option_Unchecked" IsChecked="True"/>
    <CheckBox x:Name="Option3CheckBox" Content="Option 3" Margin="24,0,0,0"
              Checked="Option_Checked" Unchecked="Option_Unchecked" />
</StackPanel>
```

```csharp
private void Option_Checked(object sender, RoutedEventArgs e)
{
    SetCheckedState();
}

private void Option_Unchecked(object sender, RoutedEventArgs e)
{
    SetCheckedState();
}

private void SelectAll_Checked(object sender, RoutedEventArgs e)
{
    Option1CheckBox.IsChecked = Option2CheckBox.IsChecked = Option3CheckBox.IsChecked = true;
}

private void SelectAll_Unchecked(object sender, RoutedEventArgs e)
{
    Option1CheckBox.IsChecked = Option2CheckBox.IsChecked = Option3CheckBox.IsChecked = false;
}

private void SelectAll_Indeterminate(object sender, RoutedEventArgs e)
{
    // If the SelectAll box is checked (all options are selected), 
    // clicking the box will change it to its indeterminate state.
    // Instead, we want to uncheck all the boxes,
    // so we do this programatically. The indeterminate state should
    // only be set programatically, not by the user.

    if (Option1CheckBox.IsChecked == true &&
        Option2CheckBox.IsChecked == true &&
        Option3CheckBox.IsChecked == true)
    {
        // This will cause SelectAll_Unchecked to be executed, so
        // we don't need to uncheck the other boxes here.
        OptionsAllCheckBox.IsChecked = false;
    }
}

private void SetCheckedState()
{
    // Controls are null the first time this is called, so we just 
    // need to perform a null check on any one of the controls.
    if (Option1CheckBox != null)
    {
        if (Option1CheckBox.IsChecked == true &&
            Option2CheckBox.IsChecked == true &&
            Option3CheckBox.IsChecked == true)
        {
            OptionsAllCheckBox.IsChecked = true;
        }
        else if (Option1CheckBox.IsChecked == false &&
            Option2CheckBox.IsChecked == false &&
            Option3CheckBox.IsChecked == false)
        {
            OptionsAllCheckBox.IsChecked = false;
        }
        else
        {
            // Set third state (indeterminate) by setting IsChecked to null.
            OptionsAllCheckBox.IsChecked = null;
        }
    }
}
```

## <a name="dos-and-donts"></a><span data-ttu-id="82ff4-173">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="82ff4-173">Do's and don'ts</span></span>

-   <span data-ttu-id="82ff4-174">Stellen Sie sicher, dass der Zweck und der aktuelle Zustand des Kontrollkästchens eindeutig sind.</span><span class="sxs-lookup"><span data-stu-id="82ff4-174">Verify that the purpose and current state of the check box is clear.</span></span>
-   <span data-ttu-id="82ff4-175">Geben Sie nicht mehr als zwei Zeilen für den Text von Kontrollkästchen an.</span><span class="sxs-lookup"><span data-stu-id="82ff4-175">Limit check box text content to no more than two lines.</span></span>
-   <span data-ttu-id="82ff4-176">Formulieren Sie die Beschriftung des Kontrollkästchens als Aussage, die bei aktiviertem Kontrollkästchen wahr ist und bei deaktiviertem Kontrollkästchen falsch.</span><span class="sxs-lookup"><span data-stu-id="82ff4-176">Word the checkbox label as a statement that the check mark makes true and the absence of a check mark makes false.</span></span>
-   <span data-ttu-id="82ff4-177">Verwenden Sie die Standardschriftart – es sei denn, Sie müssen gemäß Ihren Markenrichtlinien eine andere Schriftart verwenden.</span><span class="sxs-lookup"><span data-stu-id="82ff4-177">Use the default font unless your brand guidelines tell you to use another.</span></span>
-   <span data-ttu-id="82ff4-178">Bei dynamischem Text müssen Sie die Skalierung des Steuerelements und die Auswirkungen auf visuelle Elemente in der Nähe bedenken.</span><span class="sxs-lookup"><span data-stu-id="82ff4-178">If the text content is dynamic, consider how the control will resize and what will happen to visuals around it.</span></span>
-   <span data-ttu-id="82ff4-179">Bei mindestens zwei Auswahloptionen, die sich gegenseitig ausschließen, können Sie die Verwendung von [Optionsfeldern](radio-button.md) in Erwägung ziehen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-179">If there are two or more mutually exclusive options from which to choose, consider using [radio buttons](radio-button.md).</span></span>
-   <span data-ttu-id="82ff4-180">Zwei Kontrollkästchengruppen sollten nicht direkt nebeneinander platziert werden.</span><span class="sxs-lookup"><span data-stu-id="82ff4-180">Don't put two check box groups next to each other.</span></span> <span data-ttu-id="82ff4-181">Verwenden Sie Gruppenbeschriftungen zum Trennen der Gruppen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-181">Use group labels to separate the groups.</span></span>
-   <span data-ttu-id="82ff4-182">Verwenden Sie kein Kontrollkästchen als Ein/Aus-Steuerelement oder zum Ausführen eines Befehls. Verwenden Sie stattdessen einen Umschalter.</span><span class="sxs-lookup"><span data-stu-id="82ff4-182">Don't use a check box as an on/off control or to perform a command; instead, use a toggle switch.</span></span>
-   <span data-ttu-id="82ff4-183">Verwenden Sie kein Kontrollkästchen, um andere Steuerelemente (etwa ein Dialogfeld) anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-183">Don't use a check box to display other controls, such as a dialog box.</span></span>
-   <span data-ttu-id="82ff4-184">Mit dem unbestimmten Zustand können Sie angeben, dass eine Option für einige, aber nicht für alle Unteroptionen festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="82ff4-184">Use the indeterminate state to indicate that an option is set for some, but not all, sub-choices.</span></span>
-   <span data-ttu-id="82ff4-185">Geben Sie bei Verwendung des unbestimmten Zustands mithilfe untergeordneter Kontrollkästchen an, welche Optionen aktiviert sind und welche nicht.</span><span class="sxs-lookup"><span data-stu-id="82ff4-185">When using indeterminate state, use subordinate check boxes to show which options are selected and which are not.</span></span> <span data-ttu-id="82ff4-186">Gestalten Sie die Benutzeroberfläche so, dass der Benutzer die Unteroptionen sehen kann.</span><span class="sxs-lookup"><span data-stu-id="82ff4-186">Design the UI so that the user can get see the sub-choices.</span></span>
-   <span data-ttu-id="82ff4-187">Verwenden Sie den unbestimmten Zustand nicht, um einen dritten Zustand darzustellen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-187">Don't use the indeterminate state to represent a third state.</span></span> <span data-ttu-id="82ff4-188">Mit dem unbestimmten Zustand wird angezeigt, dass eine Option für einige, aber nicht für alle Unteroptionen gilt.</span><span class="sxs-lookup"><span data-stu-id="82ff4-188">The indeterminate state is used to indicate that an option is set for some, but not all, sub-choices.</span></span> <span data-ttu-id="82ff4-189">Benutzer dürfen daher nicht in der Lage sein, einen unbestimmten Zustand direkt festzulegen.</span><span class="sxs-lookup"><span data-stu-id="82ff4-189">So, don't allow users to set an indeterminate state directly.</span></span> <span data-ttu-id="82ff4-190">In diesem Negativbeispiel wird der unbestimmte Zustand eines Kontrollkästchens verwendet, um eine mittlere Schärfe anzugeben:</span><span class="sxs-lookup"><span data-stu-id="82ff4-190">For an example of what not to do, this check box uses the indeterminate state to indicate medium spiciness:</span></span>

    ![Ein unbestimmtes Kontrollkästchen](images/checkbox4_spicy.png)

    <span data-ttu-id="82ff4-192">Verwenden Sie stattdessen eine Optionsfeldgruppe mit drei Optionen: Nicht scharf, Scharf, Besonders scharf.</span><span class="sxs-lookup"><span data-stu-id="82ff4-192">Instead, use a radio button group that has three options: Not spicy, Spicy, and Extra spicy.</span></span>

    ![Optionsfeldgruppe mit drei Optionen: Nicht scharf, Scharf, Besonders scharf](images/spicyoptions.png)


## <a name="related-articles"></a><span data-ttu-id="82ff4-194">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="82ff4-194">Related articles</span></span>

-   [<span data-ttu-id="82ff4-195">CheckBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="82ff4-195">CheckBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209316) 
-   [<span data-ttu-id="82ff4-196">Optionsfelder</span><span class="sxs-lookup"><span data-stu-id="82ff4-196">Radio buttons</span></span>](radio-button.md)
-   [<span data-ttu-id="82ff4-197">Umschalter</span><span class="sxs-lookup"><span data-stu-id="82ff4-197">Toggle switch</span></span>](toggles.md)


