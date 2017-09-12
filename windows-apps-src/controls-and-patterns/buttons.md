---
author: Jwmsft
Description: "Eine Schaltfläche ermöglicht dem Benutzer das unmittelbare Auslösen einer Aktion."
title: "Schaltflächen"
label: Buttons
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: f04d1a3c-7dcd-4bc8-9586-3396923b312e
pm-contact: kisai
design-contact: kimsea
dev-contact: mitra
doc-status: Published
ms.openlocfilehash: 2cb15d21496c080002411849682278df7f927e41
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="buttons"></a><span data-ttu-id="c6bcb-104">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="c6bcb-104">Buttons</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="c6bcb-105">Eine Schaltfläche ermöglicht dem Benutzer das unmittelbare Auslösen einer Aktion.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-105">A button gives the user a way to trigger an immediate action.</span></span>

> <span data-ttu-id="c6bcb-106">**Wichtige APIs:** [Klasse „Button“](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx), [Klasse „RepeatButton“](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx), [Ereignis „Click“](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)</span><span class="sxs-lookup"><span data-stu-id="c6bcb-106">**Important APIs**: [Button class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx), [RepeatButton class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx), [Click event](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)</span></span>

![Beispiel für Schaltflächen](images/controls/button.png)

## <a name="is-this-the-right-control"></a><span data-ttu-id="c6bcb-108">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="c6bcb-108">Is this the right control?</span></span>

<span data-ttu-id="c6bcb-109">Mit einer Schaltfläche kann ein Benutzer unmittelbar eine Aktion auslösen. Beispiel: Absenden eines Formulars.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-109">A button lets the user initiate an immediate action, such as submitting a form.</span></span>

<span data-ttu-id="c6bcb-110">Schaltflächen sollten nicht verwendet werden, um zu anderen Seiten zu navigieren. Links sind für diesen Zweck besser geeignet.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-110">Don't use a button when the action is to navigate to another page; use a link instead.</span></span> <span data-ttu-id="c6bcb-111">Weitere Informationen finden Sie unter [Hyperlinks](hyperlinks.md).</span><span class="sxs-lookup"><span data-stu-id="c6bcb-111">See [Hyperlinks](hyperlinks.md) for more info.</span></span>

> <span data-ttu-id="c6bcb-112">Ausnahme: Für die Navigation in einem Assistenten können die Schaltflächen „Zurück“ und „Weiter“ verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-112">Exception: For wizard navigation, use buttons labeled "Back" and "Next".</span></span> <span data-ttu-id="c6bcb-113">Für andere Arten der Rückwärtsnavigation oder der Navigation zu einer übergeordneten Ebene sollte stattdessen eine Zurück-Schaltfläche verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-113">For other types of backwards navigation or navigation to an upper level, use a back button.</span></span>

## <a name="example"></a><span data-ttu-id="c6bcb-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c6bcb-114">Example</span></span>

<span data-ttu-id="c6bcb-115">In diesem Beispiel werden zwei Schaltflächen („Zulassen“ und „Blockieren“) in einem Dialogfeld verwendet, über das Zugriff auf den Standort des Benutzers angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-115">This example uses two buttons, Allow and Block, in a dialog requesting location access.</span></span>

![Beispiel für Schaltflächen in einem Dialogfeld](images/dialogs/dialog_RS2_two_button.png)

## <a name="create-a-button"></a><span data-ttu-id="c6bcb-117">Erstellen einer Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="c6bcb-117">Create a button</span></span>

<span data-ttu-id="c6bcb-118">Dieses Beispiel zeigt eine Schaltfläche, die auf einen Mausklick reagiert.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-118">This example shows a button that responds to a click.</span></span>

<span data-ttu-id="c6bcb-119">Erstellen Sie die Schaltfläche in XAML.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-119">Create the button in XAML.</span></span>

```xaml
<Button Content="Subscribe" Click="SubscribeButton_Click"/>
```

<span data-ttu-id="c6bcb-120">Sie können die Schaltfläche auch in Code erstellen.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-120">Or create the button in code.</span></span>

```csharp
Button subscribeButton = new Button();
subscribeButton.Content = "Subscribe";
subscribeButton.Click += SubscribeButton_Click;

// Add the button to a parent container in the visual tree.
stackPanel1.Children.Add(subscribeButton);
```

<span data-ttu-id="c6bcb-121">Behandeln Sie das Click-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-121">Handle the Click event.</span></span>

```csharp
private async void SubscribeButton_Click(object sender, RoutedEventArgs e)
{
    // Call app specific code to subscribe to the service. For example:
    ContentDialog subscribeDialog = new ContentDialog
    {
        Title = "Subscribe to App Service?",
        Content = "Listen, watch, and play in high definition for only $9.99/month. Free to try, cancel anytime.",
        CloseButtonText = "Not Now",
        PrimaryButtonText = "Subscribe",
        SecondaryButtonText = "Try it"
    };

    ContentDialogResult result = await subscribeDialog.ShowAsync();
}
```

### <a name="button-interaction"></a><span data-ttu-id="c6bcb-122">Interaktion mit Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="c6bcb-122">Button interaction</span></span>

<span data-ttu-id="c6bcb-123">Wenn Sie mit einem Finger oder Stift auf eine Schaltfläche tippen oder mit der linken Maustaste darauf klicken, löst die Schaltfläche das [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-123">When you tap a Button with a finger or stylus, or press a left mouse button while the pointer is over it, the button raises the [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx) event.</span></span> <span data-ttu-id="c6bcb-124">Bei einer Schaltfläche mit Tastaturfokus wird das Click-Ereignis auch durch Drücken der Eingabe- oder Leertaste ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-124">If a button has keyboard focus, pressing the Enter key or the Spacebar key also raises the Click event.</span></span>

<span data-ttu-id="c6bcb-125">Sie können für eine Schaltfläche generell keine Low-Level-Ereignisse des Typs [PointerPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.pointerpressed.aspx) behandeln, da sie stattdessen mit dem Click-Verhalten konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-125">You generally can't handle low-level [PointerPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.pointerpressed.aspx) events on a Button because it has the Click behavior instead.</span></span> <span data-ttu-id="c6bcb-126">Weitere Informationen finden Sie unter [Übersicht über Ereignisse und Routingereignisse](https://msdn.microsoft.com/library/windows/apps/mt185584.aspx).</span><span class="sxs-lookup"><span data-stu-id="c6bcb-126">For more info, see [Events and routed events overview](https://msdn.microsoft.com/library/windows/apps/mt185584.aspx).</span></span>

<span data-ttu-id="c6bcb-127">Durch Änderung der Eigenschaft [ClickMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.clickmode.aspx) können Sie anpassen, wie eine Schaltfläche Click-Ereignisse auslöst.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-127">You can change how a button raises the Click event by changing the [ClickMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.clickmode.aspx) property.</span></span> <span data-ttu-id="c6bcb-128">Der ClickMode-Standardwert lautet **Release**.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-128">The default ClickMode value is **Release**.</span></span> <span data-ttu-id="c6bcb-129">Wenn als ClickMode-Wert **Hover** festgelegt ist, kann das Click-Event nicht über die Tastatur oder durch Berührung ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-129">If ClickMode is **Hover**, the Click event can't be raised with the keyboard or touch.</span></span>


### <a name="button-content"></a><span data-ttu-id="c6bcb-130">Inhalt von Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="c6bcb-130">Button content</span></span>

<span data-ttu-id="c6bcb-131">„Button“ ist ein Element des Typs [ContentControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.aspx).</span><span class="sxs-lookup"><span data-stu-id="c6bcb-131">Button is a [ContentControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.aspx).</span></span> <span data-ttu-id="c6bcb-132">Die zugehörige XAML-Inhaltseigenschaft ist [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx). Mit ihr lässt sich in XAML folgende Syntax nutzen: `<Button>A button's content</Button>`.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-132">Its XAML content property is [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx), which enables a syntax like this for XAML: `<Button>A button's content</Button>`.</span></span> <span data-ttu-id="c6bcb-133">Sie können jedes Objekt als Inhalt der Schaltfläche festlegen.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-133">You can set any object as the button's content.</span></span> <span data-ttu-id="c6bcb-134">Wenn der Inhalt ein [UIElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.aspx) ist, wird er in der Schaltfläche gerendert.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-134">If the content is a [UIElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.aspx), it is rendered in the button.</span></span> <span data-ttu-id="c6bcb-135">Wenn es sich beim Inhalt um einen anderen Objekttyp handelt, wird die entsprechende Zeichenfolgendarstellung in der Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-135">If the content is another type of object, its string representation is shown in the button.</span></span>

<span data-ttu-id="c6bcb-136">Im folgenden Beispiel wird ein **StackPanel**-Element, das das Bild einer Orange und Text enthält, als Inhalt einer Schaltfläche festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-136">Here, a **StackPanel** that contains an image of an orange and text is set as the content of a button.</span></span>

```xaml
<Button Click="Button_Click"
        Background="LightGray"
        Height="100" Width="80">
    <StackPanel>
        <Image Source="Assets/Photo.png" Height="62"/>
        <TextBlock Text="Photos" Foreground="Black"
                   HorizontalAlignment="Center"/>
    </StackPanel>
</Button>
```

<span data-ttu-id="c6bcb-137">Die Schaltfläche sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-137">The button looks like this.</span></span>

![Eine Schaltfläche mit Bild- und Textinhalt](images/button-orange.png)

## <a name="create-a-repeat-button"></a><span data-ttu-id="c6bcb-139">Erstellen einer Wiederholungsschaltfläche</span><span class="sxs-lookup"><span data-stu-id="c6bcb-139">Create a repeat button</span></span>

<span data-ttu-id="c6bcb-140">Eine Schaltfläche des Typs [RepeatButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx) ist eine Schaltfläche, die das [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)-Ereignis ab dem Moment des Klickens oder Drückens auf die Schaltfläche solange wiederholt auslöst, bis der Benutzer die Maustaste loslässt oder nicht mehr auf die Schaltfläche drückt.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-140">A [RepeatButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx) is a button that raises [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx) events repeatedly from the time it's pressed until it's released.</span></span> <span data-ttu-id="c6bcb-141">Über die Eigenschaft [Delay](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.delay.aspx) können Sie festlegen, wie lange eine Schaltfläche des Typs„RepeatButton“ nach dem Klicken oder Drücken wartet, bevor sie mit der Wiederholung der Click-Aktion beginnt.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-141">Set the [Delay](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.delay.aspx) property to specify the time that the RepeatButton waits after it is pressed before it starts repeating the click action.</span></span> <span data-ttu-id="c6bcb-142">Über die Eigenschaft [Interval](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.interval.aspx) können Sie den Zeitintervall zwischen den einzelnen Wiederholungen der Click-Aktion definieren.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-142">Set the [Interval](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.interval.aspx) property to specify the time between repetitions of the click action.</span></span> <span data-ttu-id="c6bcb-143">Die Zeiten beider Eigenschaften werden in Millisekunden angegeben.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-143">Times for both properties are specified in milliseconds.</span></span>

<span data-ttu-id="c6bcb-144">Das folgende Beispiel zeigt zwei „RepeatButton“-Steuerelemente. Ihre jeweiligen Click-Ereignisse dienen dazu, den Wert in einem Textblock zu erhöhen oder zu verringern.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-144">The following example shows two RepeatButton controls whose respective Click events are used to increase and decrease the value shown in a text block.</span></span>

```xaml
<StackPanel>
    <RepeatButton Width="100" Delay="500" Interval="100" Click="Increase_Click">Increase</RepeatButton>
    <RepeatButton Width="100" Delay="500" Interval="100" Click="Decrease_Click">Decrease</RepeatButton>
    <TextBlock x:Name="clickTextBlock" Text="Number of Clicks:" />
</StackPanel>
```

```csharp
private static int _clicks = 0;
private void Increase_Click(object sender, RoutedEventArgs e)
{
    _clicks += 1;
    clickTextBlock.Text = "Number of Clicks: " + _clicks;
}

private void Decrease_Click(object sender, RoutedEventArgs e)
{
    if(_clicks > 0)
    {
        _clicks -= 1;
        clickTextBlock.Text = "Number of Clicks: " + _clicks;
    }
}
```

## <a name="recommendations"></a><span data-ttu-id="c6bcb-145">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="c6bcb-145">Recommendations</span></span>

-   <span data-ttu-id="c6bcb-146">Der Zweck und Status einer Schaltfläche müssen für den Benutzer eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-146">Make sure the purpose and state of a button are clear to the user.</span></span>
-   <span data-ttu-id="c6bcb-147">Verwenden Sie kurze, spezifische und selbsterklärende Texte, aus denen die Funktion einer Schaltfläche eindeutig hervorgeht.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-147">Use a concise, specific, self-explanatory text that clearly describes the action that the button performs.</span></span> <span data-ttu-id="c6bcb-148">In der Regel umfasst der Schaltflächen-Textinhalt ein einzelnes Wort: ein Verb.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-148">Usually button text content is a single word, a verb.</span></span>
-   <span data-ttu-id="c6bcb-149">Wenn mehrere Schaltflächen für die gleiche Entscheidung vorhanden sind (wie etwa in einem Bestätigungsdialogfeld) geben Sie die Schaltflächen für den Commit in der folgenden Reihenfolge an:</span><span class="sxs-lookup"><span data-stu-id="c6bcb-149">When there are multiple buttons for the same decision (such as in a confirmation dialog), present the commit buttons in this order:</span></span>
    -   <span data-ttu-id="c6bcb-150">OK/[Ausführen]/Ja</span><span class="sxs-lookup"><span data-stu-id="c6bcb-150">OK/[Do it]/Yes</span></span>
    -   <span data-ttu-id="c6bcb-151">[Nicht ausführen]/Nein</span><span class="sxs-lookup"><span data-stu-id="c6bcb-151">[Don't do it]/No</span></span>
    -   <span data-ttu-id="c6bcb-152">Abbrechen</span><span class="sxs-lookup"><span data-stu-id="c6bcb-152">Cancel</span></span>

    <span data-ttu-id="c6bcb-153">(Dabei stellen [Ausführen] und [Nicht ausführen] bestimmte Antworten auf die Hauptanweisung dar.)</span><span class="sxs-lookup"><span data-stu-id="c6bcb-153">(where [Do it] and [Don't do it] are specific responses to the main instruction.)</span></span>

-   <span data-ttu-id="c6bcb-154">Wenn der Textinhalt der Schaltfläche dynamisch ist, beispielsweise wenn er lokalisiert ist, ziehen Sie die Größenänderung der Schaltfläche und das in Betracht, was mit den Steuerelementen herum passiert.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-154">If the button's text content is dynamic, for example, it is localized, consider how the button will resize and what will happen to controls around it.</span></span>
-   <span data-ttu-id="c6bcb-155">Verwenden Sie für Befehlsschaltflächen mit Textinhalt eine Schaltflächen-Mindestbreite.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-155">For command buttons with text content, use a minimum button width.</span></span>
-   <span data-ttu-id="c6bcb-156">Vermeiden Sie es, für Textinhalt schmale, kurze oder hohe Befehlsschaltflächen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-156">Avoid narrow, short, or tall command buttons with text content.</span></span>
-   <span data-ttu-id="c6bcb-157">Verwenden Sie die standardmäßige Schriftart, es sei denn, Sie müssen entsprechend Ihren Markenrichtlinien eine andere verwenden.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-157">Use the default font unless your brand guidelines tell you to use something different.</span></span>
-   <span data-ttu-id="c6bcb-158">Für eine Aktion, die auf mehreren Seiten in Ihrer App verfügbar sein muss, sollten Sie die Verwendung einer [unteren App-Leiste](app-bars.md) in Erwägung ziehen, anstatt eine Schaltfläche auf mehreren Seiten zu duplizieren.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-158">For an action that needs to be available across multiple pages within your app, instead of duplicating a button on multiple pages, consider using a [bottom app bar](app-bars.md).</span></span>
-   <span data-ttu-id="c6bcb-159">Stellen Sie dem Benutzer jeweils nur zwei Schaltflächen zur Verfügung, beispielsweise „Akzeptieren“ und „Abbrechen“.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-159">Expose only one or two buttons to the user at a time, for example, Accept and Cancel.</span></span> <span data-ttu-id="c6bcb-160">Wenn Sie dem Benutzer mehr Aktionen zur Verfügung stellen möchten, sollten Sie [Kontrollkästchen](checkbox.md) oder [Optionsfelder](radio-button.md) verwenden, über die der Benutzer Aktionen mit einer einzelnen Befehlsschaltfläche auslösen kann.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-160">If you need to expose more actions to the user, consider using [checkboxes](checkbox.md) or [radio buttons](radio-button.md) from which the user can select actions, with a single command button to trigger those actions.</span></span>
-   <span data-ttu-id="c6bcb-161">Verwenden Sie die standardmäßige Befehlsschaltfläche, um die häufigste oder empfohlene Aktion anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-161">Use the default command button to indicate the most common or recommended action.</span></span>
-   <span data-ttu-id="c6bcb-162">Ziehen Sie in Erwägung, Ihre Schaltflächen anzupassen.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-162">Consider customizing your buttons.</span></span> <span data-ttu-id="c6bcb-163">Schaltfläche sind standardmäßig rechteckig. Sie können aber die visuellen Effekte anpassen, die das Erscheinungsbild der Schaltfläche ausmachen.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-163">A button's shape is rectangular by default, but you can customize the visuals that make up the button's appearance.</span></span> <span data-ttu-id="c6bcb-164">Der Inhalt einer Schaltfläche ist für gewöhnlich Text (beispielsweise „Akzeptieren“ oder „Abbrechen“). Sie könnten den Text aber auch durch ein Symbol ersetzen oder ein Symbol und Text kombinieren.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-164">A button's content is usually text—for example, Accept or Cancel—but you could replace the text with an icon, or use an icon plus text.</span></span>
-   <span data-ttu-id="c6bcb-165">Stellen Sie sicher, dass sich, sobald der Benutzer eine Schaltfläche betätigt, der Status und das Erscheinungsbild der Schaltfläche ändern, um dem Benutzer ein Rückmeldung zu geben.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-165">Make sure that as the user interacts with a button, the button changes state and appearance to provide feedback to the user.</span></span> <span data-ttu-id="c6bcb-166">„Normal“, „pressed“ und „disabled“ sind Beispiele von Schaltflächenstatus.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-166">Normal, pressed, and disabled are examples of button states.</span></span>
-   <span data-ttu-id="c6bcb-167">Lösen Sie die Aktion der Schaltfläche aus, wenn der Benutzer auf die Schaltfläche tippt oder drückt.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-167">Trigger the button's action when the user taps or presses the button.</span></span> <span data-ttu-id="c6bcb-168">Die Aktion wird für gewöhnlich ausgelöst, wenn der Benutzer die Schaltfläche loslässt. Sie können aber auch festlegen, dass die Aktion einer Schaltfläche durch Berühren mit dem Finger ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-168">Usually the action is triggered when the user releases the button, but you also can set a button's action to trigger when a finger first presses it.</span></span>
-   <span data-ttu-id="c6bcb-169">Tauschen Sie nicht die standardmäßigen Stile „submit“, „reset“ und „button“.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-169">Don't swap the default submit, reset, and button styles.</span></span>
-   <span data-ttu-id="c6bcb-170">Überfrachten Sie eine Schaltfläche nicht mit Inhalt.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-170">Don't put too much content inside a button.</span></span> <span data-ttu-id="c6bcb-171">Formulieren Sie den Inhalt kurz und verständlich.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-171">Make the content concise and easy to understand.</span></span>

### <a name="recommended-single-button-layout"></a><span data-ttu-id="c6bcb-172">Empfehlungen für Layouts mit einer einzigen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="c6bcb-172">Recommended single button layout</span></span>

<span data-ttu-id="c6bcb-173">Wenn in Ihrem Layout nur eine einzige Schaltfläche benötigt wird, sollten Sie diese je nach ihrem Containerkontext entweder linksbündig oder rechtsbündig ausrichten.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-173">If your layout requires only one button, it should be either left- or right-aligned based on its container context.</span></span>

-   <span data-ttu-id="c6bcb-174">In Dialogfeldern mit nur einer einzigen Schaltfläche sollte die Schaltfläche **rechtsbündig** ausgerichtet sein.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-174">Dialogs with only one button should **right-align** the button.</span></span> <span data-ttu-id="c6bcb-175">Stellen Sie bei Dialogfeldern mit nur einer einzigen Schaltfläche sicher, dass die Schaltfläche die sichere, nicht destruktive Aktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-175">If your dialog contains only one button, ensure that the button performs the safe, nondestructive action.</span></span> <span data-ttu-id="c6bcb-176">Wenn Sie die Klasse [ContentDialog](dialogs.md) verwenden und nur eine einzige Schaltfläche definieren, wird diese Schaltfläche automatisch rechtsbündig ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-176">If you use [ContentDialog](dialogs.md) and specify a single button, it will automatically right-align.</span></span>

![Schaltfläche in einem Dialogfeld](images/pushbutton_doc_dialog.png)

-   <span data-ttu-id="c6bcb-178">Wird die Schaltfläche als Teil einer Containerbenutzeroberfläche angezeigt (z.B. innerhalb einer Popupbenachrichtigung, eines Flyouts oder eines Listenansicht-Elements), sollten Sie die Schaltfläche innerhalb des Containers **rechtsbündig** ausrichten.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-178">If your button appears within a container UI (for example, within a toast notification, a flyout, or a list view item), you should **right-align** the button within the container.</span></span>

![Eine Schaltfläche in einem Container](images/pushbutton_doc_container.png)

-   <span data-ttu-id="c6bcb-180">Auf Seiten mit einer einzigen Schaltfläche (z.B. einer Einstellungsseite mit einer „Anwenden“-Schaltfläche am unteren Rand) sollten Sie die Schaltfläche **linksbündig** ausrichten.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-180">In pages that contain a single button (for example, an "Apply" button at the bottom of a settings page), you should **left-align** the button.</span></span> <span data-ttu-id="c6bcb-181">Das gewährleistet, dass die Schaltfläche passend zum übrigen Seiteninhalt ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-181">This ensures that the button aligns with the rest of the page content.</span></span>

![Eine Schaltfläche auf einer Seite](images/pushbutton_doc_page.png)

## <a name="back-buttons"></a><span data-ttu-id="c6bcb-183">„Zurück“-Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="c6bcb-183">Back buttons</span></span>

<span data-ttu-id="c6bcb-184">Die Zurück-Schaltfläche ist ein durch das System bereitgestelltes UI-Element, das die Rückwärtsnavigation über den Back-Stapel oder den Navigationsverlauf des Benutzers ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-184">The back button is a system-provided UI element that enables backward navigation through either the back stack or navigation history of the user.</span></span> <span data-ttu-id="c6bcb-185">Sie müssen keine eigene Zurück-Schaltfläche erstellen, aber unter Umständen ist etwas Aufwand erforderlich, um eine gute Rückwärtsnavigation zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-185">You don't have to create your own back button, but you might have to do some work to enable a good backwards navigation experience.</span></span> <span data-ttu-id="c6bcb-186">Weitere Informationen finden Sie unter [Verlauf und Rückwärtsnavigation](../layout/navigation-history-and-backwards-navigation.md).</span><span class="sxs-lookup"><span data-stu-id="c6bcb-186">For more info, see [History and backwards navigation](../layout/navigation-history-and-backwards-navigation.md)</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="c6bcb-187">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="c6bcb-187">Get the sample code</span></span>
*   [<span data-ttu-id="c6bcb-188">Beispiel für XAML-UI-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="c6bcb-188">XAML UI basics sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/XamlUIBasics)<br/>
    <span data-ttu-id="c6bcb-189">Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-189">See all of the XAML controls in an interactive format.</span></span>


## <a name="related-articles"></a><span data-ttu-id="c6bcb-190">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="c6bcb-190">Related articles</span></span>

- [<span data-ttu-id="c6bcb-191">Optionsfelder</span><span class="sxs-lookup"><span data-stu-id="c6bcb-191">Radio buttons</span></span>](radio-button.md)
- [<span data-ttu-id="c6bcb-192">Umschalter</span><span class="sxs-lookup"><span data-stu-id="c6bcb-192">Toggle switches</span></span>](toggles.md)
- [<span data-ttu-id="c6bcb-193">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="c6bcb-193">Check boxes</span></span>](checkbox.md)
- [<span data-ttu-id="c6bcb-194">Button-Klasse</span><span class="sxs-lookup"><span data-stu-id="c6bcb-194">Button class</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx)
