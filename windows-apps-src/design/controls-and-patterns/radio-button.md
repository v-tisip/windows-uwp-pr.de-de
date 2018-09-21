---
author: QuinnRadich
Description: Radio buttons let users select one option from two or more choices.
title: Richtlinien für Optionsfelder
ms.assetid: 41E3F928-AA55-42A2-9281-EC3907C4F898
label: Radio buttons
template: detail.hbs
ms.author: quradic
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: kisai
design-contact: kimsea
dev-contact: mitra
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 48d830b388fee8a0007447a66aa58e3794cfaae0
ms.sourcegitcommit: a160b91a554f8352de963d9fa37f7df89f8a0e23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4124795"
---
# <a name="radio-buttons"></a><span data-ttu-id="53e4b-103">Optionsfelder</span><span class="sxs-lookup"><span data-stu-id="53e4b-103">Radio buttons</span></span>

> <span data-ttu-id="53e4b-104">**Wichtige APIs**: [RadioButton-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.RadioButton), [Checked-Ereignis](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.ToggleButton.Checked), [IsChecked-Eigenschaft](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.ToggleButton.IsChecked)</span><span class="sxs-lookup"><span data-stu-id="53e4b-104">**Important APIs**: [RadioButton class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.RadioButton), [Checked event](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.ToggleButton.Checked), [IsChecked property](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.ToggleButton.IsChecked)</span></span>

<span data-ttu-id="53e4b-105">Mithilfe von Optionsfeldern können Benutzer eine Option aus einer Gruppe von Optionsfeldern auswählen.</span><span class="sxs-lookup"><span data-stu-id="53e4b-105">Radio buttons allow users to select one option from a set.</span></span> <span data-ttu-id="53e4b-106">Jede Option wird durch ein Optionsfeld dargestellt, und Benutzer können nur ein Optionsfeld in einer Gruppe von Optionsfeldern auswählen.</span><span class="sxs-lookup"><span data-stu-id="53e4b-106">Each option is represented by one radio button, and users can only select one radio button in a radio button group.</span></span>

<span data-ttu-id="53e4b-107">(Falls Sie sich über die englische Bezeichnung „Radio Button” wundern: Optionsfelder sind im Englischen nach den Tasten mit voreingestellten Sendern an einem Radio benannt.)</span><span class="sxs-lookup"><span data-stu-id="53e4b-107">(If you're curious about the name, radio buttons are named after the channel preset buttons on a radio.)</span></span>

![Optionsfelder](images/controls/radio-button.png)

## <a name="is-this-the-right-control"></a><span data-ttu-id="53e4b-109">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="53e4b-109">Is this the right control?</span></span>

<span data-ttu-id="53e4b-110">Verwenden Sie Optionsfelder, um Benutzern mindestens zwei Optionen bereitzustellen, die sich gegenseitig ausschließen.</span><span class="sxs-lookup"><span data-stu-id="53e4b-110">Use radio buttons to present users with two or more mutually exclusive options.</span></span>

![Eine Gruppe von Optionsfeldern](images/radiobutton_basic.png)

<span data-ttu-id="53e4b-112">Verwenden Sie Optionsfelder, wenn Benutzer alle Optionen sehen müssen, um eine Auswahl treffen zu können.</span><span class="sxs-lookup"><span data-stu-id="53e4b-112">Use radio buttons when users need to see all options to make a selection.</span></span> <span data-ttu-id="53e4b-113">Da Optionsfelder alle Optionen gleichermaßen hervorheben, schenken Benutzer den Optionen möglicherweise mehr Aufmerksamkeit, als eigentlich erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="53e4b-113">Since radio buttons emphasize all options equally, they may draw more attention to the options than necessary.</span></span> <span data-ttu-id="53e4b-114">Sie können auch andere Steuerelemente verwenden, es sei denn, die Optionen erfordern zusätzliche Aufmerksamkeit seitens des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="53e4b-114">Unless the options deserve extra attention from the user, consider using other controls.</span></span> <span data-ttu-id="53e4b-115">Verwenden Sie stattdessen beispielsweise eine [Dropdownliste](lists.md), wenn die standardmäßige Option für die meisten Benutzer in den meisten Situationen empfohlen ist.</span><span class="sxs-lookup"><span data-stu-id="53e4b-115">For example, if the default option is recommended for most users in most situations, use a [drop-down list](lists.md) instead.</span></span>

![Dropdownliste](images/combo_box_collapsed.png)

<span data-ttu-id="53e4b-117">Wenn nur zwei sich gegenseitig ausschließende Optionen vorhanden sind, kombinieren Sie sie in einem einzelnen [Kontrollkästchen](checkbox.md) oder [Umschalter](toggles.md).</span><span class="sxs-lookup"><span data-stu-id="53e4b-117">If there are only two mutually exclusive options, combine them into a single [checkbox](checkbox.md) or [toggle switch](toggles.md).</span></span> <span data-ttu-id="53e4b-118">Verwenden Sie beispielsweise ein Kontrollkästchen für "Ich stimme zu" anstelle von zwei Optionsfeldern für "Ich stimme zu" und "Ich stimme nicht zu".</span><span class="sxs-lookup"><span data-stu-id="53e4b-118">For example, use a checkbox for "I agree" instead of two radio buttons for "I agree" and "I don't agree."</span></span>

![Zwei Möglichkeiten für die Darstellung einer binären Auswahl](images/radiobutton_vs_checkbox.png)

<span data-ttu-id="53e4b-120">Wenn der Benutzer mehrere Optionen auswählen kann, verwenden Sie ein [Kontrollkästchen](checkbox.md).</span><span class="sxs-lookup"><span data-stu-id="53e4b-120">When the user can select multiple options, use a [checkbox](checkbox.md).</span></span>

![Auswählen mehrerer Optionen mit Kontrollkästchen](images/checkbox2.png)

<span data-ttu-id="53e4b-122">Wenn Optionen Zahlen mit festgelegten Schritten (10, 20, 30) sind, verwenden Sie ein [Schieberegler](slider.md)-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="53e4b-122">When options are numbers that have fixed steps (10, 20, 30), use a [slider](slider.md) control.</span></span>

![Schiebereglersteuerelement](images/controls/slider.png)

<span data-ttu-id="53e4b-124">Wenn mehr als 8Optionen vorhanden sind, verwenden Sie eine [Dropdownliste](lists.md) oder ein [Listenfeld](lists.md).</span><span class="sxs-lookup"><span data-stu-id="53e4b-124">If there are more than 8 options, use a [drop-down list](lists.md) or [list box](lists.md).</span></span>

![Kombinationsfeld](images/combo_box_scroll.png)

<span data-ttu-id="53e4b-126">Wenn die verfügbaren Optionen auf dem aktuellen Kontext der App basieren oder andernfalls dynamisch variieren können, verwenden Sie ein [Listenfeld](lists.md) für die Einfachauswahl.</span><span class="sxs-lookup"><span data-stu-id="53e4b-126">If the available options are based on the app’s current context, or can otherwise vary dynamically, use a single-select [list box](lists.md).</span></span>

## <a name="examples"></a><span data-ttu-id="53e4b-127">Beispiele</span><span class="sxs-lookup"><span data-stu-id="53e4b-127">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="53e4b-128">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="53e4b-128">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="53e4b-129">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/RadioButton">die App zu öffnen und RadioButton in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="53e4b-129">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/RadioButton">open the app and see the RadioButton in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="53e4b-130">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="53e4b-130">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="53e4b-131">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="53e4b-131">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="53e4b-132">Optionsfelder in den Microsoft Edge-Browsereinstellungen.</span><span class="sxs-lookup"><span data-stu-id="53e4b-132">Radio buttons in the Microsoft Edge browser settings.</span></span>

![Optionsfelder in den Microsoft Edge-Browsereinstellungen](images/control-examples/radio-buttons-edge.png)

## <a name="create-a-radio-button"></a><span data-ttu-id="53e4b-134">Erstellen eines Optionsfelds</span><span class="sxs-lookup"><span data-stu-id="53e4b-134">Create a radio button</span></span>

<span data-ttu-id="53e4b-135">Optionsfelder funktionieren in Gruppen.</span><span class="sxs-lookup"><span data-stu-id="53e4b-135">Radio buttons work in groups.</span></span> <span data-ttu-id="53e4b-136">Es gibt zwei Arten zur Gruppierung von Optionsfeld-Steuerelementen:</span><span class="sxs-lookup"><span data-stu-id="53e4b-136">There are 2 ways you can group radio button controls:</span></span>
- <span data-ttu-id="53e4b-137">Platzieren Sie sie im gleichen übergeordneten Container.</span><span class="sxs-lookup"><span data-stu-id="53e4b-137">Put them inside the same parent container.</span></span>
- <span data-ttu-id="53e4b-138">Legen Sie die [GroupName](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.RadioButton.GroupName)-Eigenschaft für jedes Optionsfeld auf denselben Wert fest.</span><span class="sxs-lookup"><span data-stu-id="53e4b-138">Set the [GroupName](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.RadioButton.GroupName) property on each radio button to the same value.</span></span>

<span data-ttu-id="53e4b-139">In diesem Beispiel wird die erste Gruppe von Optionsfeldern implizit gruppiert, da die Felder im selben StackPanel-Element enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="53e4b-139">In this example, the first group of radio buttons is implicitly grouped by being in the same stack panel.</span></span> <span data-ttu-id="53e4b-140">Die zweite Gruppe ist auf zwei StackPanel-Elemente aufgeteilt, damit sie explizit nach GroupName gruppiert werden.</span><span class="sxs-lookup"><span data-stu-id="53e4b-140">The second group is divided between 2 stack panels, so they're explicitly grouped by GroupName.</span></span>

```xaml
<StackPanel>
    <StackPanel>
        <TextBlock Text="Background" Style="{ThemeResource BaseTextBlockStyle}"/>
        <StackPanel Orientation="Horizontal">
            <RadioButton Content="Green" Tag="Green" Checked="BGRadioButton_Checked"/>
            <RadioButton Content="Yellow" Tag="Yellow" Checked="BGRadioButton_Checked"/>
            <RadioButton Content="Blue" Tag="Blue" Checked="BGRadioButton_Checked"/>
            <RadioButton Content="White" Tag="White" Checked="BGRadioButton_Checked" IsChecked="True"/>
        </StackPanel>
    </StackPanel>
    <StackPanel>
        <TextBlock Text="BorderBrush" Style="{ThemeResource BaseTextBlockStyle}"/>
        <StackPanel Orientation="Horizontal">
            <StackPanel>
                <RadioButton Content="Green" GroupName="BorderBrush" Tag="Green" Checked="BorderRadioButton_Checked"/>
                <RadioButton Content="Yellow" GroupName="BorderBrush" Tag="Yellow" Checked="BorderRadioButton_Checked" IsChecked="True"/>
            </StackPanel>
            <StackPanel>
                <RadioButton Content="Blue" GroupName="BorderBrush" Tag="Blue" Checked="BorderRadioButton_Checked"/>
                <RadioButton Content="White" GroupName="BorderBrush" Tag="White"  Checked="BorderRadioButton_Checked"/>
            </StackPanel>
        </StackPanel>
    </StackPanel>
    <Border x:Name="BorderExample1" BorderThickness="10" BorderBrush="#FFFFD700" Background="#FFFFFFFF" Height="50" Margin="0,10,0,10"/>
</StackPanel>
```

```csharp
private void BGRadioButton_Checked(object sender, RoutedEventArgs e)
{
    RadioButton rb = sender as RadioButton;

    if (rb != null && BorderExample1 != null)
    {
        string colorName = rb.Tag.ToString();
        switch (colorName)
        {
            case "Yellow":
                BorderExample1.Background = new SolidColorBrush(Colors.Yellow);
                break;
            case "Green":
                BorderExample1.Background = new SolidColorBrush(Colors.Green);
                break;
            case "Blue":
                BorderExample1.Background = new SolidColorBrush(Colors.Blue);
                break;
            case "White":
                BorderExample1.Background = new SolidColorBrush(Colors.White);
                break;
        }
    }
}

private void BorderRadioButton_Checked(object sender, RoutedEventArgs e)
{
    RadioButton rb = sender as RadioButton;

    if (rb != null && BorderExample1 != null)
    {
        string colorName = rb.Tag.ToString();
        switch (colorName)
        {
            case "Yellow":
                BorderExample1.BorderBrush = new SolidColorBrush(Colors.Gold);
                break;
            case "Green":
                BorderExample1.BorderBrush = new SolidColorBrush(Colors.DarkGreen);
                break;
            case "Blue":
                BorderExample1.BorderBrush = new SolidColorBrush(Colors.DarkBlue);
                break;
            case "White":
                BorderExample1.BorderBrush = new SolidColorBrush(Colors.White);
                break;
        }
    }
}
```

<span data-ttu-id="53e4b-141">Die Optionsfeldgruppen sehen wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="53e4b-141">The radio button groups look like this.</span></span>

![Optionsfelder in zwei Gruppen](images/radio-button-groups.png)

<span data-ttu-id="53e4b-143">Ein Optionsfeld hat zwei Zustände: *aktiviert* und *deaktiviert*.</span><span class="sxs-lookup"><span data-stu-id="53e4b-143">A radio button has two states: *selected* or *cleared*.</span></span> <span data-ttu-id="53e4b-144">Wenn ein Optionsfeld aktiviert ist, lautet die [IsChecked](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.ToggleButton.IsChecked)-Eigenschaft **true**.</span><span class="sxs-lookup"><span data-stu-id="53e4b-144">When a radio button is selected, its [IsChecked](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Primitives.ToggleButton.IsChecked) property is **true**.</span></span> <span data-ttu-id="53e4b-145">Wenn ein Optionsfeld deaktiviert ist, lautet die **IsChecked**-Eigenschaft **false**.</span><span class="sxs-lookup"><span data-stu-id="53e4b-145">When a radio button is cleared, its **IsChecked** property is **false**.</span></span> <span data-ttu-id="53e4b-146">Ein Optionsfeld kann durch Klicken auf ein anderes Optionsfeld in derselben Gruppe deaktiviert werden, jedoch nicht durch erneutes Klicken auf das Optionsfeld selbst.</span><span class="sxs-lookup"><span data-stu-id="53e4b-146">A radio button can be cleared by clicking another radio button in the same group, but it cannot be cleared by clicking it again.</span></span> <span data-ttu-id="53e4b-147">Sie können ein Optionsfeld jedoch programmgesteuert durch Festlegen der IsChecked-Eigenschaft auf **false** deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="53e4b-147">However, you can clear a radio button programmatically by setting its IsChecked property to **false**.</span></span> <span data-ttu-id="53e4b-148">Sie können die **IsChecked**-Eigenschaft tatsächlich mit einem booleschen Wert vergleichen, indem Sie die **Wert** der **IsChecked**-Eigenschaft abrufen.</span><span class="sxs-lookup"><span data-stu-id="53e4b-148">You can actually compare the **IsChecked** property with a bool by getting the **Value** of the **IsChecked** property</span></span>

## <a name="recommendations"></a><span data-ttu-id="53e4b-149">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="53e4b-149">Recommendations</span></span>

-   <span data-ttu-id="53e4b-150">Stellen Sie sicher, dass der Zweck und der aktuelle Status einer Gruppe von Optionsfeldern nachvollziehbar ist.</span><span class="sxs-lookup"><span data-stu-id="53e4b-150">Make sure the purpose and current state of a set of radio buttons is clear.</span></span>
-   <span data-ttu-id="53e4b-151">Begrenzen Sie den Text des Optionsfelds auf eine einzelne Zeile.</span><span class="sxs-lookup"><span data-stu-id="53e4b-151">Limit the radio button’s text content to a single line.</span></span>
-   <span data-ttu-id="53e4b-152">Wenn der Textinhalt dynamisch ist, bedenken Sie die Größenänderung der Schaltfläche und die visuellen Effekte herum.</span><span class="sxs-lookup"><span data-stu-id="53e4b-152">If the text content is dynamic, consider how the button will resize and what will happen to visuals around it.</span></span>
-   <span data-ttu-id="53e4b-153">Verwenden Sie die Standardschriftart, es sei denn, Sie müssen gemäß Ihren Markenrichtlinien eine andere Schriftart verwenden.</span><span class="sxs-lookup"><span data-stu-id="53e4b-153">Use the default font unless your brand guidelines tell you to use another.</span></span>
-   <span data-ttu-id="53e4b-154">Platzieren Sie keine zwei Optionsfeldgruppen nebeneinander.</span><span class="sxs-lookup"><span data-stu-id="53e4b-154">Don't put two radio button groups side by side.</span></span> <span data-ttu-id="53e4b-155">Wenn sich zwei Optionsfeldgruppen direkt nebeneinander befinden, ist es schwierig, festzustellen, welche Schaltflächen zu welcher Gruppe gehören.</span><span class="sxs-lookup"><span data-stu-id="53e4b-155">When two radio button groups are right next to each other, it's difficult to determine which buttons belong to which group.</span></span>

## <a name="additional-usage-guidance"></a><span data-ttu-id="53e4b-156">Weitere Hinweise zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="53e4b-156">Additional usage guidance</span></span>

<span data-ttu-id="53e4b-157">Diese Abbildung zeigt die richtige Vorgehensweise zum Platzieren und Anordnen von Optionsfeldern in geeignetem Abstand.</span><span class="sxs-lookup"><span data-stu-id="53e4b-157">This illustration shows the proper way to position and space radio buttons.</span></span>

![Gruppe von Optionsfeldern](images/radiobutton-layout.png)

![Abstandsrichtlinien für Optionsfelder](images/radiobutton-redlines.png)

## <a name="related-topics"></a><span data-ttu-id="53e4b-160">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="53e4b-160">Related topics</span></span>

**<span data-ttu-id="53e4b-161">Für Designer</span><span class="sxs-lookup"><span data-stu-id="53e4b-161">For designers</span></span>**
- [<span data-ttu-id="53e4b-162">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="53e4b-162">Buttons</span></span>](buttons.md)
- [<span data-ttu-id="53e4b-163">Umschalter</span><span class="sxs-lookup"><span data-stu-id="53e4b-163">Toggle switches</span></span>](toggles.md)
- [<span data-ttu-id="53e4b-164">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="53e4b-164">Checkboxes</span></span>](checkbox.md)
- [<span data-ttu-id="53e4b-165">Listen und Kombinationsfelder</span><span class="sxs-lookup"><span data-stu-id="53e4b-165">Lists and combo boxes</span></span>](lists.md)
- [<span data-ttu-id="53e4b-166">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="53e4b-166">Sliders</span></span>](slider.md)

**<span data-ttu-id="53e4b-167">Für Entwickler (XAML)</span><span class="sxs-lookup"><span data-stu-id="53e4b-167">For developers (XAML)</span></span>**
- [<span data-ttu-id="53e4b-168">RadioButton-Klasse</span><span class="sxs-lookup"><span data-stu-id="53e4b-168">RadioButton class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.radiobutton)
