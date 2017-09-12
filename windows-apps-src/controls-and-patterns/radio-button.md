---
author: Jwmsft
Description: "Mit Optionsfeldern können Benutzer eine oder mehrere Optionen auswählen."
title: "Richtlinien für Optionsfelder"
ms.assetid: 41E3F928-AA55-42A2-9281-EC3907C4F898
label: Radio buttons
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
ms.openlocfilehash: 370c5266277ff442f26c9aeb951d869ec70b31c5
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="radio-buttons"></a><span data-ttu-id="695d4-104">Optionsfelder</span><span class="sxs-lookup"><span data-stu-id="695d4-104">Radio buttons</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="695d4-105">Mit Optionsfeldern können Benutzer eine oder mehrere Optionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="695d4-105">Radio buttons let users select one option from two or more choices.</span></span> <span data-ttu-id="695d4-106">Jede Option wird durch ein Optionsfeld dargestellt. Benutzer können nur ein einziges Optionsfeld in einer Gruppe von Optionsfeldern auswählen.</span><span class="sxs-lookup"><span data-stu-id="695d4-106">Each option is represented by one radio button; a user can select only one radio button in a radio button group.</span></span>

> <span data-ttu-id="695d4-107">**Wichtige APIs**: [RadioButton-Klasse](https://msdn.microsoft.com/library/windows/apps/br227544), [Checked-Ereignis](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.checked.aspx), [IsChecked-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.ischecked.aspx)</span><span class="sxs-lookup"><span data-stu-id="695d4-107">**Important APIs**: [RadioButton class](https://msdn.microsoft.com/library/windows/apps/br227544), [Checked event](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.checked.aspx), [IsChecked property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.ischecked.aspx)</span></span>

<span data-ttu-id="695d4-108">(Falls Sie sich über die englische Bezeichnung „Radio Button” wundern: Optionsfelder sind im Englischen nach den Tasten mit voreingestellten Sendern an einem Radio benannt.)</span><span class="sxs-lookup"><span data-stu-id="695d4-108">(If you're curious about the name, radio buttons are named for the channel preset buttons on a radio.)</span></span>

![Optionsfelder](images/controls/radio-button.png)

## <a name="is-this-the-right-control"></a><span data-ttu-id="695d4-110">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="695d4-110">Is this the right control?</span></span>

<span data-ttu-id="695d4-111">Verwenden Sie Optionsfelder, um den Benutzern zwei oder mehr Optionen bereitzustellen, die sich gegenseitig ausschließen, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="695d4-111">Use radio buttons to present users with two or more mutually exclusive options, as here.</span></span>

![Eine Gruppe von Optionsfeldern](images/radiobutton_basic.png)

<span data-ttu-id="695d4-113">Optionsfelder verleihen wichtigen Optionen in Ihrer App Klarheit und Gewichtung.</span><span class="sxs-lookup"><span data-stu-id="695d4-113">Radio buttons add clarity and weight to very important options in your app.</span></span> <span data-ttu-id="695d4-114">Verwenden Sie Optionsfelder, wenn die angezeigten Optionen wichtig genug sind, um mehr Bildschirmplatz in Anspruch zu nehmen, und in den Fällen, wenn die Klarheit der Auswahl äußerst explizite Optionen erfordert.</span><span class="sxs-lookup"><span data-stu-id="695d4-114">Use radio buttons when the options being presented are important enough to command more screen space and where the clarity of the choice demands very explicit options.</span></span>

<span data-ttu-id="695d4-115">Optionsfelder heben alle Optionen gleichermaßen hervor, sodass Benutzer den Optionen möglicherweise mehr Aufmerksamkeit schenken, als eigentlich erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="695d4-115">Radio buttons emphasize all options equally, and that may draw more attention to the options than necessary.</span></span> <span data-ttu-id="695d4-116">Ziehen Sie in Betracht, andere Steuerelemente zu verwenden, es sei denn, die Optionen erfordern zusätzliche Aufmerksamkeit seitens des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="695d4-116">Consider using other controls, unless the options deserve extra attention from the user.</span></span> <span data-ttu-id="695d4-117">Verwenden Sie beispielsweise demgegenüber eine [Dropdownliste](lists.md), wenn die standardmäßige Option für die meisten Benutzer in den meisten Situationen empfohlen ist.</span><span class="sxs-lookup"><span data-stu-id="695d4-117">For example, if the default option is recommended for most users in most situations, use a [drop-down list](lists.md) instead.</span></span>

<span data-ttu-id="695d4-118">Wenn nur zwei sich gegenseitig ausschließende Optionen vorhanden sind, kombinieren Sie sie in einem einzelnen [Kontrollkästchen](checkbox.md) oder [Umschalter](toggles.md).</span><span class="sxs-lookup"><span data-stu-id="695d4-118">If there are only two mutually exclusive options, combine them into a single [checkbox](checkbox.md) or [toggle switch](toggles.md).</span></span> <span data-ttu-id="695d4-119">Verwenden Sie beispielsweise ein Kontrollkästchen für "Ich stimme zu" anstelle von zwei Optionsfeldern für "Ich stimme zu" und "Ich stimme nicht zu".</span><span class="sxs-lookup"><span data-stu-id="695d4-119">For example, use a checkbox for "I agree" instead of two radio buttons for "I agree" and "I don't agree."</span></span>

![Zwei Möglichkeiten für die Darstellung einer binären Auswahl](images/radiobutton_vs_checkbox.png)

<span data-ttu-id="695d4-121">Wenn der Benutzer mehrere Optionen auswählen kann, verwenden Sie stattdessen ein [Kontrollkästchen](checkbox.md) oder [Listenfeldsteuerelement](lists.md).</span><span class="sxs-lookup"><span data-stu-id="695d4-121">When the user can select multiple options, use a [checkbox](checkbox.md) or [list box](lists.md) control instead.</span></span>

![Auswählen mehrerer Optionen mit Kontrollkästchen](images/checkbox2.png)

<span data-ttu-id="695d4-123">Verwenden Sie Optionsfelder nicht, wenn es sich bei den Optionen um Zahlen mit festen Schritten handelt, beispielsweise 10, 20, 30.</span><span class="sxs-lookup"><span data-stu-id="695d4-123">Don't use radio buttons when the options are numbers that have fixed steps, like 10, 20, 30.</span></span> <span data-ttu-id="695d4-124">Verwenden Sie stattdessen ein [Schiebereglersteuerelement](slider.md).</span><span class="sxs-lookup"><span data-stu-id="695d4-124">Use a [slider](slider.md) control instead.</span></span>

<span data-ttu-id="695d4-125">Wenn mehr als acht Optionen vorhanden sind, verwenden Sie stattdessen eine [Dropdownliste](lists.md), ein [Listenfeld](lists.md) für die Einfachauswahl oder eine [Listenfeld](lists.md).</span><span class="sxs-lookup"><span data-stu-id="695d4-125">If there are more than 8 options, use a [drop-down list](lists.md), a single-select [list box](lists.md), or a [list box](lists.md) instead.</span></span>

<span data-ttu-id="695d4-126">Wenn die verfügbaren Optionen auf dem aktuellen Kontext der App basieren oder andernfalls dynamisch variieren können, verwenden Sie stattdessen ein [Listenfeld](lists.md) für die Einfachauswahl.</span><span class="sxs-lookup"><span data-stu-id="695d4-126">If the available options are based on the app’s current context, or can otherwise vary dynamically, use a single-select [list box](lists.md) instead.</span></span>

## <a name="example"></a><span data-ttu-id="695d4-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="695d4-127">Example</span></span>
<span data-ttu-id="695d4-128">Optionsfelder in den Microsoft Edge-Browsereinstellungen.</span><span class="sxs-lookup"><span data-stu-id="695d4-128">Radio buttons in the Microsoft Edge browser settings.</span></span>

![Optionsfelder in den Microsoft Edge-Browsereinstellungen](images/control-examples/radio-buttons-edge.png)

## <a name="create-a-radio-button"></a><span data-ttu-id="695d4-130">Erstellen eines Optionsfelds</span><span class="sxs-lookup"><span data-stu-id="695d4-130">Create a radio button</span></span>

<span data-ttu-id="695d4-131">Optionsfelder funktionieren in Gruppen.</span><span class="sxs-lookup"><span data-stu-id="695d4-131">Radio buttons work in groups.</span></span> <span data-ttu-id="695d4-132">Es gibt zwei Arten zur Gruppierung von Optionsfeld-Steuerelementen:</span><span class="sxs-lookup"><span data-stu-id="695d4-132">There are 2 ways you can group radio button controls:</span></span>
- <span data-ttu-id="695d4-133">Platzieren Sie sie im gleichen übergeordneten Container.</span><span class="sxs-lookup"><span data-stu-id="695d4-133">Put them inside the same parent container.</span></span>
- <span data-ttu-id="695d4-134">Legen Sie die [GroupName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.radiobutton.groupname.aspx)-Eigenschaft für jedes Optionsfeld auf denselben Wert fest.</span><span class="sxs-lookup"><span data-stu-id="695d4-134">Set the [GroupName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.radiobutton.groupname.aspx) property on each radio button to the same value.</span></span>

> <span data-ttu-id="695d4-135">**Hinweis**
            &nbsp;&nbsp;Eine Gruppe von Optionsfeldern verhält sich wie ein einzelnes Steuerelement, wenn der Zugriff darauf über die Tastatur erfolgt.</span><span class="sxs-lookup"><span data-stu-id="695d4-135">**Note**&nbsp;&nbsp;A group of radio buttons behaves like a single control when accessed via the keyboard.</span></span> <span data-ttu-id="695d4-136">Der Benutzer kann mit der TAB-TASTE nur auf die jeweils ausgewählte Option zugreifen, mithilfe der Pfeiltasten kann der Benutzer jedoch in der Gruppe navigieren.</span><span class="sxs-lookup"><span data-stu-id="695d4-136">Only the selected choice is accessible using the Tab key but users can cycle through the group using arrow keys.</span></span>

<span data-ttu-id="695d4-137">In diesem Beispiel wird die erste Gruppe von Optionsfeldern implizit gruppiert, da die Felder im selben StackPanel-Element enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="695d4-137">In this example, the first group of radio buttons is implicitly grouped by being in the same stack panel.</span></span> <span data-ttu-id="695d4-138">Die zweite Gruppe ist auf zwei StackPanel-Elemente aufgeteilt, damit sie explizit nach GroupName gruppiert werden.</span><span class="sxs-lookup"><span data-stu-id="695d4-138">The second group is divided between 2 stack panels, so they're explicitly grouped by GroupName.</span></span>

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

<span data-ttu-id="695d4-139">Die Optionsfeldgruppen sehen wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="695d4-139">The radio button groups look like this.</span></span>

![Optionsfelder in zwei Gruppen](images/radio-button-groups.png)

<span data-ttu-id="695d4-141">Ein Optionsfeld hat zwei Zustände: *aktiviert* und *deaktiviert*.</span><span class="sxs-lookup"><span data-stu-id="695d4-141">A radio button has two states: *selected* or *cleared*.</span></span> <span data-ttu-id="695d4-142">Wenn ein Optionsfeld aktiviert ist, lautet die [IsChecked](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.ischecked.aspx)-Eigenschaft **true**.</span><span class="sxs-lookup"><span data-stu-id="695d4-142">When a radio button is selected, its [IsChecked](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.togglebutton.ischecked.aspx) property is **true**.</span></span> <span data-ttu-id="695d4-143">Wenn ein Optionsfeld deaktiviert ist, lautet die **IsChecked**-Eigenschaft **false**.</span><span class="sxs-lookup"><span data-stu-id="695d4-143">When a radio button is cleared, its **IsChecked** property is **false**.</span></span> <span data-ttu-id="695d4-144">Ein Optionsfeld kann durch Klicken auf ein anderes Optionsfeld in derselben Gruppe deaktiviert werden, jedoch nicht durch erneutes Klicken auf das Optionsfeld selbst.</span><span class="sxs-lookup"><span data-stu-id="695d4-144">A radio button can be cleared by clicking another radio button in the same group, but it cannot be cleared by clicking it again.</span></span> <span data-ttu-id="695d4-145">Sie können ein Optionsfeld jedoch programmgesteuert durch Festlegen der IsChecked-Eigenschaft auf **false** deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="695d4-145">However, you can clear a radio button programmatically by setting its IsChecked property to **false**.</span></span>

## <a name="recommendations"></a><span data-ttu-id="695d4-146">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="695d4-146">Recommendations</span></span>

-   <span data-ttu-id="695d4-147">Stellen Sie sicher, dass der Zweck und der aktuelle Status eines Satzes an Optionsfeldern nachvollziehbar ist.</span><span class="sxs-lookup"><span data-stu-id="695d4-147">Make sure that the purpose and current state of a set of radio buttons is clear.</span></span>
-   <span data-ttu-id="695d4-148">Sorgen Sie immer für ein visuelles Feedback, wenn der Benutzer auf ein Optionsfeld tippt.</span><span class="sxs-lookup"><span data-stu-id="695d4-148">Always give visual feedback when the user taps a radio button.</span></span>
-   <span data-ttu-id="695d4-149">Sorgen Sie für visuelles Feedback, sobald der Benutzer mit Optionsfeldern interagiert.</span><span class="sxs-lookup"><span data-stu-id="695d4-149">Give visual feedback as the user interacts with radio buttons.</span></span> <span data-ttu-id="695d4-150">"Normal", "pressed" "checked" und "disabled" sind Beispiele für Optionsfeldstatus.</span><span class="sxs-lookup"><span data-stu-id="695d4-150">Normal, pressed, checked, and disabled are examples of radio button states.</span></span> <span data-ttu-id="695d4-151">Ein Benutzer tippt auf ein Optionsfeld, um die zugehörige Option zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="695d4-151">A user taps a radio button to activate the related option.</span></span> <span data-ttu-id="695d4-152">Durch das Tippen auf eine aktivierte Option wird sie nicht deaktiviert, aber das Tippen auf eine andere Option überträgt die Aktivierung auf diese Option.</span><span class="sxs-lookup"><span data-stu-id="695d4-152">Tapping an activated option doesn’t deactivate it, but tapping another option transfers activation to that option.</span></span>
-   <span data-ttu-id="695d4-153">Reservieren Sie visuelle Effekte und Animationen für Berührungsfeedback und für den aktivierten Status. Im nicht aktivierten Status sollten Optionsfeldsteuerelemente als nicht verwendet oder inaktiv (aber nicht deaktiviert) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="695d4-153">Reserve visual effects and animations for touch feedback, and for the checked state; in the unchecked state, radio button controls should appear unused or inactive (but not disabled).</span></span>
-   <span data-ttu-id="695d4-154">Begrenzen Sie den Text des Optionsfelds auf eine einzelne Zeile.</span><span class="sxs-lookup"><span data-stu-id="695d4-154">Limit the radio button’s text content to a single line.</span></span> <span data-ttu-id="695d4-155">Sie können die visuellen Effekte des Optionsfelds anpassen, um eine Beschreibung der Option in kleinerer Schriftgröße unter dem Haupttext anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="695d4-155">You can customize the radio button’s visuals to display a description of the option in smaller font size below the main line of text.</span></span>
-   <span data-ttu-id="695d4-156">Wenn der Textinhalt dynamisch ist, bedenken Sie die Größenänderung der Schaltfläche und die visuellen Effekte herum.</span><span class="sxs-lookup"><span data-stu-id="695d4-156">If the text content is dynamic, consider how the button will resize and what will happen to visuals around it.</span></span>
-   <span data-ttu-id="695d4-157">Verwenden Sie die standardmäßige Schriftart, es sei denn, Sie müssen gemäß Ihren Markenrichtlinien eine andere verwenden.</span><span class="sxs-lookup"><span data-stu-id="695d4-157">Use the default font unless your brand guidelines tell you to use another.</span></span>
-   <span data-ttu-id="695d4-158">Schließen Sie das Optionsfeld in ein Bezeichnungselement ein, sodass das Optionsfeld durch Tippen auf die Bezeichnung ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="695d4-158">Enclose the radio button in a label element so that tapping the label selects the radio button.</span></span>
-   <span data-ttu-id="695d4-159">Platzieren Sie den Bezeichnungstext hinter dem Optionsfeldsteuerelement und nicht davor oder darüber.</span><span class="sxs-lookup"><span data-stu-id="695d4-159">Place the label text after the radio button control, not before or above it.</span></span>
-   <span data-ttu-id="695d4-160">Ziehen Sie in Erwägung, Ihre Schaltflächen anzupassen.</span><span class="sxs-lookup"><span data-stu-id="695d4-160">Consider customizing your radio buttons.</span></span> <span data-ttu-id="695d4-161">Standardmäßig besteht ein Optionsfeld aus zwei konzentrischen Kreisen– der innere ist ausgefüllt (und wird gezeigt, wenn das Optionsfeld aktiviert wird), und der äußere ist gestrichelt– und einigem Textinhalt.</span><span class="sxs-lookup"><span data-stu-id="695d4-161">By default, a radio button consists of two concentric circles—the inner one filled (and shown when the radio button is checked), the outer one stroked—and some text content.</span></span> <span data-ttu-id="695d4-162">Wir ermutigen Sie jedoch, kreativ zu sein.</span><span class="sxs-lookup"><span data-stu-id="695d4-162">But we encourage you to be creative.</span></span> <span data-ttu-id="695d4-163">Benutzer mögen es, direkt mit dem Inhalt einer App zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="695d4-163">Users are comfortable interacting directly with the content of an app.</span></span> <span data-ttu-id="695d4-164">Daher können Sie auswählen, den tatsächlichen Inhalt als Angebot anzuzeigen, unabhängig davon, ob er mit Grafiken oder als unauffälliger Textumschalter präsentiert wird.</span><span class="sxs-lookup"><span data-stu-id="695d4-164">So you may choose to show the actual content on offer, whether that’s presented with graphics or as subtle textual toggle buttons.</span></span>
-   <span data-ttu-id="695d4-165">Eine Optionsfeldgruppe sollte nicht mehr als acht Optionen beinhalten.</span><span class="sxs-lookup"><span data-stu-id="695d4-165">Don't put more than 8 options in a radio button group.</span></span> <span data-ttu-id="695d4-166">Wenn Sie mehr Optionen verwenden müssen, verwenden Sie stattdessen eine [Dropdownliste](lists.md), ein [Listenfeld](lists.md)oder eine [Listenansicht](lists.md).</span><span class="sxs-lookup"><span data-stu-id="695d4-166">When you need to present more options, use a [drop-down list](lists.md), [list box](lists.md), or a [list view](lists.md) instead.</span></span>
-   <span data-ttu-id="695d4-167">Zwei Optionsfeldgruppen sollten nicht direkt nebeneinander platziert werden.</span><span class="sxs-lookup"><span data-stu-id="695d4-167">Don't put two radio button groups next to each other.</span></span> <span data-ttu-id="695d4-168">Wenn sich zwei Optionsfeldgruppen direkt nebeneinander befinden, ist es schwierig, festzustellen, welche Schaltflächen zu welcher Gruppe gehören.</span><span class="sxs-lookup"><span data-stu-id="695d4-168">When two radio button groups are right next to each other, it's difficult to determine which buttons belong to which group.</span></span> <span data-ttu-id="695d4-169">Verwenden Sie Gruppenbeschriftungen, um sie zu trennen.</span><span class="sxs-lookup"><span data-stu-id="695d4-169">Use group labels to separate them.</span></span>

## <a name="additional-usage-guidance"></a><span data-ttu-id="695d4-170">Weitere Hinweise zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="695d4-170">Additional usage guidance</span></span>

<span data-ttu-id="695d4-171">Diese Abbildung zeigt die richtige Vorgehensweise zum Platzieren und Anordnen von Optionsfeldern in geeignetem Abstand.</span><span class="sxs-lookup"><span data-stu-id="695d4-171">This illustration shows the proper way to position and space radio buttons.</span></span>

![Gruppe von Optionsfeldern](images/radiobutton_layout1.png)
## <a name="related-topics"></a><span data-ttu-id="695d4-173">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="695d4-173">Related topics</span></span>

**<span data-ttu-id="695d4-174">Für Designer</span><span class="sxs-lookup"><span data-stu-id="695d4-174">For designers</span></span>**
- [<span data-ttu-id="695d4-175">Richtlinien für Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="695d4-175">Guidelines for buttons</span></span>](buttons.md)
- [<span data-ttu-id="695d4-176">Richtlinien für Umschalter</span><span class="sxs-lookup"><span data-stu-id="695d4-176">Guidelines for toggle switches</span></span>](toggles.md)
- [<span data-ttu-id="695d4-177">Richtlinien für Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="695d4-177">Guidelines for checkboxes</span></span>](checkbox.md)
- [<span data-ttu-id="695d4-178">Richtlinien für Dropdownlisten</span><span class="sxs-lookup"><span data-stu-id="695d4-178">Guidelines for drop-down lists</span></span>](lists.md)
- [<span data-ttu-id="695d4-179">Richtlinien für Listenansicht- und Rasteransichtsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="695d4-179">Guidelines for list view and grid view controls</span></span>](lists.md)
- [<span data-ttu-id="695d4-180">Richtlinien für Schieberegler</span><span class="sxs-lookup"><span data-stu-id="695d4-180">Guidelines for sliders</span></span>](slider.md)
- [<span data-ttu-id="695d4-181">Richtlinien für das Auswahlsteuerelement</span><span class="sxs-lookup"><span data-stu-id="695d4-181">Guidelines for the select control</span></span>](lists.md)


**<span data-ttu-id="695d4-182">Für Entwickler (XAML)</span><span class="sxs-lookup"><span data-stu-id="695d4-182">For developers (XAML)</span></span>**
- [<span data-ttu-id="695d4-183">Windows.UI.Xaml.Controls RadioButton-Klasse</span><span class="sxs-lookup"><span data-stu-id="695d4-183">Windows.UI.Xaml.Controls RadioButton class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227544)
