---
author: serenaz
Description: A button gives the user a way to trigger an immediate action.
title: Schaltflächen
label: Buttons
template: detail.hbs
ms.author: sezhen
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
ms.localizationpriority: medium
ms.openlocfilehash: f663ce9da6453922e35f850a8cd039f33770f434
ms.sourcegitcommit: 4b522af988273946414a04fbbd1d7fde40f8ba5e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2018
ms.locfileid: "1494167"
---
# <a name="buttons"></a><span data-ttu-id="962e3-103">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="962e3-103">Buttons</span></span>


<span data-ttu-id="962e3-104">Eine Schaltfläche ermöglicht dem Benutzer das unmittelbare Auslösen einer Aktion.</span><span class="sxs-lookup"><span data-stu-id="962e3-104">A button gives the user a way to trigger an immediate action.</span></span>

> <span data-ttu-id="962e3-105">**Wichtige APIs:** [Klasse „Button“](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx), [Klasse „RepeatButton“](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx), [Ereignis „Click“](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)</span><span class="sxs-lookup"><span data-stu-id="962e3-105">**Important APIs**: [Button class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx), [RepeatButton class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx), [Click event](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)</span></span>

![Beispiel für Schaltflächen](images/controls/button.png)

## <a name="is-this-the-right-control"></a><span data-ttu-id="962e3-107">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="962e3-107">Is this the right control?</span></span>

<span data-ttu-id="962e3-108">Mit einer Schaltfläche kann ein Benutzer unmittelbar eine Aktion auslösen. Beispiel: Absenden eines Formulars.</span><span class="sxs-lookup"><span data-stu-id="962e3-108">A button lets the user initiate an immediate action, such as submitting a form.</span></span>

<span data-ttu-id="962e3-109">Schaltflächen sollten nicht verwendet werden, um zu anderen Seiten zu navigieren. Links sind für diesen Zweck besser geeignet.</span><span class="sxs-lookup"><span data-stu-id="962e3-109">Don't use a button when the action is to navigate to another page; use a link instead.</span></span> <span data-ttu-id="962e3-110">Weitere Informationen finden Sie unter [Hyperlinks](hyperlinks.md).</span><span class="sxs-lookup"><span data-stu-id="962e3-110">See [Hyperlinks](hyperlinks.md) for more info.</span></span>
> <span data-ttu-id="962e3-111">Ausnahme: Für die Navigation in einem Assistenten können die Schaltflächen „Zurück“ und „Weiter“ verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="962e3-111">Exception: For wizard navigation, use buttons labeled "Back" and "Next".</span></span> <span data-ttu-id="962e3-112">Für andere Arten der Rückwärtsnavigation oder der Navigation zu einer übergeordneten Ebene sollte stattdessen eine Zurück-Schaltfläche verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="962e3-112">For other types of backwards navigation or navigation to an upper level, use a back button.</span></span>

## <a name="examples"></a><span data-ttu-id="962e3-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="962e3-113">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="962e3-114">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="962e3-114">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="962e3-115">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/Button">die App zu öffnen und die Schaltfläche in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="962e3-115">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/Button">open the app and see the Button in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="962e3-116">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="962e3-116">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="962e3-117">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="962e3-117">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="962e3-118">In diesem Beispiel werden zwei Schaltflächen („Zulassen“ und „Blockieren“) in einem Dialogfeld verwendet, über das Zugriff auf den Standort des Benutzers angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="962e3-118">This example uses two buttons, Allow and Block, in a dialog requesting location access.</span></span>

![Beispiel für Schaltflächen in einem Dialogfeld](images/dialogs/dialog_RS2_two_button.png)

## <a name="create-a-button"></a><span data-ttu-id="962e3-120">Erstellen einer Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="962e3-120">Create a button</span></span>

<span data-ttu-id="962e3-121">Dieses Beispiel zeigt eine Schaltfläche, die auf einen Mausklick reagiert.</span><span class="sxs-lookup"><span data-stu-id="962e3-121">This example shows a button that responds to a click.</span></span>

<span data-ttu-id="962e3-122">Erstellen Sie die Schaltfläche in XAML.</span><span class="sxs-lookup"><span data-stu-id="962e3-122">Create the button in XAML.</span></span>

```xaml
<Button Content="Subscribe" Click="SubscribeButton_Click"/>
```

<span data-ttu-id="962e3-123">Sie können die Schaltfläche auch in Code erstellen.</span><span class="sxs-lookup"><span data-stu-id="962e3-123">Or create the button in code.</span></span>

```csharp
Button subscribeButton = new Button();
subscribeButton.Content = "Subscribe";
subscribeButton.Click += SubscribeButton_Click;

// Add the button to a parent container in the visual tree.
stackPanel1.Children.Add(subscribeButton);
```

<span data-ttu-id="962e3-124">Behandeln Sie das Click-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="962e3-124">Handle the Click event.</span></span>

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

### <a name="button-interaction"></a><span data-ttu-id="962e3-125">Interaktion mit Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="962e3-125">Button interaction</span></span>

<span data-ttu-id="962e3-126">Wenn Sie mit einem Finger oder Stift auf eine Schaltfläche tippen oder mit der linken Maustaste darauf klicken, löst die Schaltfläche das [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="962e3-126">When you tap a Button with a finger or stylus, or press a left mouse button while the pointer is over it, the button raises the [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx) event.</span></span> <span data-ttu-id="962e3-127">Bei einer Schaltfläche mit Tastaturfokus wird das Click-Ereignis auch durch Drücken der Eingabe- oder Leertaste ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="962e3-127">If a button has keyboard focus, pressing the Enter key or the Spacebar key also raises the Click event.</span></span>

<span data-ttu-id="962e3-128">Sie können für eine Schaltfläche generell keine Low-Level-Ereignisse des Typs [PointerPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.pointerpressed.aspx) behandeln, da sie stattdessen mit dem Click-Verhalten konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="962e3-128">You generally can't handle low-level [PointerPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.pointerpressed.aspx) events on a Button because it has the Click behavior instead.</span></span> <span data-ttu-id="962e3-129">Weitere Informationen finden Sie unter [Übersicht über Ereignisse und Routingereignisse](https://msdn.microsoft.com/library/windows/apps/mt185584.aspx).</span><span class="sxs-lookup"><span data-stu-id="962e3-129">For more info, see [Events and routed events overview](https://msdn.microsoft.com/library/windows/apps/mt185584.aspx).</span></span>

<span data-ttu-id="962e3-130">Durch Änderung der Eigenschaft [ClickMode](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.clickmode) können Sie anpassen, wie eine Schaltfläche Click-Ereignisse auslöst.</span><span class="sxs-lookup"><span data-stu-id="962e3-130">You can change how a button raises the Click event by changing the [ClickMode](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.clickmode) property.</span></span> <span data-ttu-id="962e3-131">Der ClickMode-Standardwert ist **Version**, Sie können den ClickMode einer Schaltfläche jedoch auch auf **Zeigen** oder **Drücken** festlegen.</span><span class="sxs-lookup"><span data-stu-id="962e3-131">The default ClickMode value is **Release**, but you also can set a button's ClickMode to **Hover** or **Press**.</span></span> <span data-ttu-id="962e3-132">Wenn als ClickMode-Wert **Hover** festgelegt ist, kann das Click-Event nicht über die Tastatur oder durch Berührung ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="962e3-132">If ClickMode is **Hover**, the Click event can't be raised with the keyboard or touch.</span></span>


### <a name="button-content"></a><span data-ttu-id="962e3-133">Inhalt von Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="962e3-133">Button content</span></span>

<span data-ttu-id="962e3-134">„Button“ ist ein Element des Typs [ContentControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.aspx).</span><span class="sxs-lookup"><span data-stu-id="962e3-134">Button is a [ContentControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.aspx).</span></span> <span data-ttu-id="962e3-135">Die zugehörige XAML-Inhaltseigenschaft ist [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx). Mit ihr lässt sich in XAML folgende Syntax nutzen: `<Button>A button's content</Button>`.</span><span class="sxs-lookup"><span data-stu-id="962e3-135">Its XAML content property is [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx), which enables a syntax like this for XAML: `<Button>A button's content</Button>`.</span></span> <span data-ttu-id="962e3-136">Sie können jedes Objekt als Inhalt der Schaltfläche festlegen.</span><span class="sxs-lookup"><span data-stu-id="962e3-136">You can set any object as the button's content.</span></span> <span data-ttu-id="962e3-137">Wenn der Inhalt ein [UIElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.aspx) ist, wird er in der Schaltfläche gerendert.</span><span class="sxs-lookup"><span data-stu-id="962e3-137">If the content is a [UIElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.aspx), it is rendered in the button.</span></span> <span data-ttu-id="962e3-138">Wenn es sich beim Inhalt um einen anderen Objekttyp handelt, wird die entsprechende Zeichenfolgendarstellung in der Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="962e3-138">If the content is another type of object, its string representation is shown in the button.</span></span>

<span data-ttu-id="962e3-139">Der Inhalt einer Schaltfläche ist für gewöhnlich Text.</span><span class="sxs-lookup"><span data-stu-id="962e3-139">A button's content is usually text.</span></span> <span data-ttu-id="962e3-140">Nachstehend finden Sie Entwurfsempfehlungen für Schaltflächen mit Textinhalt:</span><span class="sxs-lookup"><span data-stu-id="962e3-140">Here are design recommendations for buttons with text content:</span></span>
-   <span data-ttu-id="962e3-141">Verwenden Sie kurze, spezifische und selbsterklärende Texte, aus denen die Funktion einer Schaltfläche eindeutig hervorgeht.</span><span class="sxs-lookup"><span data-stu-id="962e3-141">Use a concise, specific, self-explanatory text that clearly describes the action that the button performs.</span></span> <span data-ttu-id="962e3-142">In der Regel umfasst der Schaltflächen-Textinhalt ein einzelnes Wort: ein Verb.</span><span class="sxs-lookup"><span data-stu-id="962e3-142">Usually button text content is a single word, a verb.</span></span>
-   <span data-ttu-id="962e3-143">Verwenden Sie die standardmäßige Schriftart, es sei denn, Sie müssen entsprechend Ihren Markenrichtlinien eine andere verwenden.</span><span class="sxs-lookup"><span data-stu-id="962e3-143">Use the default font unless your brand guidelines tell you to use something different.</span></span>
-   <span data-ttu-id="962e3-144">Vermeiden Sie für kürzeren Text schmale Befehlsschaltflächen, indem Sie eine Schaltflächen-Mindestbreite von 120Pixel verwenden.</span><span class="sxs-lookup"><span data-stu-id="962e3-144">For shorter text, avoid narrow command buttons by using a minimum button width of 120px.</span></span>
- <span data-ttu-id="962e3-145">Vermeiden Sie für längeren Text breite Befehlsschaltflächen, indem Sie Text auf eine maximale Länge von 26Zeichen beschränken.</span><span class="sxs-lookup"><span data-stu-id="962e3-145">For longer text, avoid wide command buttons by limiting text to a maximum length of 26 characters.</span></span>
-   <span data-ttu-id="962e3-146">Wenn der Textinhalt der Schaltfläche dynamisch ist (beispielsweise wenn er [lokalisiert](../globalizing/globalizing-portal.md) ist), ziehen Sie die Größenänderung der Schaltfläche und das in Betracht, was mit den Steuerelementen herum passiert.</span><span class="sxs-lookup"><span data-stu-id="962e3-146">If the button's text content is dynamic (i.e., it is [localized](../globalizing/globalizing-portal.md)), consider how the button will resize and what will happen to controls around it.</span></span>

<table>
<tr>
<td> <b><span data-ttu-id="962e3-147">Folgendes muss geändert werden:</span><span class="sxs-lookup"><span data-stu-id="962e3-147">Need to fix:</span></span></b><br> <span data-ttu-id="962e3-148">Schaltflächen mit überlaufendem Text.</span><span class="sxs-lookup"><span data-stu-id="962e3-148">Buttons with overflowing text.</span></span> </td>
<td> <img src="images/button-wraptext.png"/> </td>
</tr>
<tr>
<td> <b><span data-ttu-id="962e3-149">Option 1:</span><span class="sxs-lookup"><span data-stu-id="962e3-149">Option 1:</span></span></b><br> <span data-ttu-id="962e3-150">Vergrößern Sie die Breite der Schaltflächen, stapeln Sie Schaltflächen und brechen Sie Text um, wenn er mehr als 26Zeichen umfasst.</span><span class="sxs-lookup"><span data-stu-id="962e3-150">Increase button width, stack buttons, and wrap if text length is greater than 26 characters.</span></span> </td>
<td> <img src="images/button-wraptext1.png"> </td>
</tr>
<tr>
<td> <b><span data-ttu-id="962e3-151">Option 2:</span><span class="sxs-lookup"><span data-stu-id="962e3-151">Option 2:</span></span></b><br> <span data-ttu-id="962e3-152">Erhöhen Sie die Schaltflächenhöhe und brechen Sie Text um.</span><span class="sxs-lookup"><span data-stu-id="962e3-152">Increase button height, and wrap text.</span></span> </td>
<td> <img src="images/button-wraptext2.png"> </td>
</tr>
</table>

<span data-ttu-id="962e3-153">Sie können auch die visuellen Elemente anpassen, die die Darstellung der Schaltfläche ausmachen.</span><span class="sxs-lookup"><span data-stu-id="962e3-153">You can also customize visuals that make up the button's appearance.</span></span> <span data-ttu-id="962e3-154">Sie können beispielsweise den Text durch ein Symbol ersetzen oder ein Symbol und Text verwenden.</span><span class="sxs-lookup"><span data-stu-id="962e3-154">For example, you could replace the text with an icon, or use an icon plus text.</span></span>

<span data-ttu-id="962e3-155">Im folgenden Beispiel wird ein **StackPanel**-Element, das ein Bild und Text enthält, als Inhalt einer Schaltfläche festgelegt.</span><span class="sxs-lookup"><span data-stu-id="962e3-155">Here, a **StackPanel** that contains an image and text is set as the content of a button.</span></span>

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

<span data-ttu-id="962e3-156">Die Schaltfläche sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="962e3-156">The button looks like this.</span></span>

![Eine Schaltfläche mit Bild- und Textinhalt](images/button-orange.png)

## <a name="create-a-repeat-button"></a><span data-ttu-id="962e3-158">Erstellen einer Wiederholungsschaltfläche</span><span class="sxs-lookup"><span data-stu-id="962e3-158">Create a repeat button</span></span>

<span data-ttu-id="962e3-159">Eine Schaltfläche des Typs [RepeatButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx) ist eine Schaltfläche, die das [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)-Ereignis ab dem Moment des Klickens oder Drückens auf die Schaltfläche solange wiederholt auslöst, bis der Benutzer die Maustaste loslässt oder nicht mehr auf die Schaltfläche drückt.</span><span class="sxs-lookup"><span data-stu-id="962e3-159">A [RepeatButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx) is a button that raises [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx) events repeatedly from the time it's pressed until it's released.</span></span> <span data-ttu-id="962e3-160">Über die Eigenschaft [Delay](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.delay.aspx) können Sie festlegen, wie lange eine Schaltfläche des Typs„RepeatButton“ nach dem Klicken oder Drücken wartet, bevor sie mit der Wiederholung der Click-Aktion beginnt.</span><span class="sxs-lookup"><span data-stu-id="962e3-160">Set the [Delay](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.delay.aspx) property to specify the time that the RepeatButton waits after it is pressed before it starts repeating the click action.</span></span> <span data-ttu-id="962e3-161">Über die Eigenschaft [Interval](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.interval.aspx) können Sie den Zeitintervall zwischen den einzelnen Wiederholungen der Click-Aktion definieren.</span><span class="sxs-lookup"><span data-stu-id="962e3-161">Set the [Interval](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.interval.aspx) property to specify the time between repetitions of the click action.</span></span> <span data-ttu-id="962e3-162">Die Zeiten beider Eigenschaften werden in Millisekunden angegeben.</span><span class="sxs-lookup"><span data-stu-id="962e3-162">Times for both properties are specified in milliseconds.</span></span>

<span data-ttu-id="962e3-163">Das folgende Beispiel zeigt zwei „RepeatButton“-Steuerelemente. Ihre jeweiligen Click-Ereignisse dienen dazu, den Wert in einem Textblock zu erhöhen oder zu verringern.</span><span class="sxs-lookup"><span data-stu-id="962e3-163">The following example shows two RepeatButton controls whose respective Click events are used to increase and decrease the value shown in a text block.</span></span>

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

## <a name="recommendations"></a><span data-ttu-id="962e3-164">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="962e3-164">Recommendations</span></span>
-   <span data-ttu-id="962e3-165">Der Zweck und Status einer Schaltfläche müssen für den Benutzer eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="962e3-165">Make sure the purpose and state of a button are clear to the user.</span></span>
-   <span data-ttu-id="962e3-166">Wenn mehrere Schaltflächen für die gleiche Entscheidung (z.B. in einem Bestätigungsdialogfeld) vorhanden sind, stellen Sie die Schaltflächen für den Commit in der folgenden Reihenfolge dar, wobei [Ausführen] und [Nicht ausführen] bestimmte Antworten auf die Hauptanweisung sind:</span><span class="sxs-lookup"><span data-stu-id="962e3-166">When there are multiple buttons for the same decision (such as in a confirmation dialog), present the commit buttons in this order, where [Do it] and [Don't do it] are specific responses to the main instruction:</span></span>
    -   <span data-ttu-id="962e3-167">OK/[Ausführen]/Ja</span><span class="sxs-lookup"><span data-stu-id="962e3-167">OK/[Do it]/Yes</span></span>
    -   <span data-ttu-id="962e3-168">[Nicht ausführen]/Nein</span><span class="sxs-lookup"><span data-stu-id="962e3-168">[Don't do it]/No</span></span>
    -   <span data-ttu-id="962e3-169">Abbrechen</span><span class="sxs-lookup"><span data-stu-id="962e3-169">Cancel</span></span>
-   <span data-ttu-id="962e3-170">Stellen Sie dem Benutzer jeweils nur zwei Schaltflächen zur Verfügung, beispielsweise „Akzeptieren“ und „Abbrechen“.</span><span class="sxs-lookup"><span data-stu-id="962e3-170">Expose only one or two buttons to the user at a time, for example, Accept and Cancel.</span></span> <span data-ttu-id="962e3-171">Wenn Sie dem Benutzer mehr Aktionen zur Verfügung stellen möchten, sollten Sie [Kontrollkästchen](checkbox.md) oder [Optionsfelder](radio-button.md) verwenden, über die der Benutzer Aktionen mit einer einzelnen Befehlsschaltfläche auslösen kann.</span><span class="sxs-lookup"><span data-stu-id="962e3-171">If you need to expose more actions to the user, consider using [checkboxes](checkbox.md) or [radio buttons](radio-button.md) from which the user can select actions, with a single command button to trigger those actions.</span></span>
-   <span data-ttu-id="962e3-172">Für eine Aktion, die auf mehreren Seiten in Ihrer App verfügbar sein muss, sollten Sie die Verwendung einer [unteren App-Leiste](app-bars.md) in Erwägung ziehen, anstatt eine Schaltfläche auf mehreren Seiten zu duplizieren.</span><span class="sxs-lookup"><span data-stu-id="962e3-172">For an action that needs to be available across multiple pages within your app, instead of duplicating a button on multiple pages, consider using a [bottom app bar](app-bars.md).</span></span>

### <a name="recommended-single-button-layout"></a><span data-ttu-id="962e3-173">Empfehlungen für Layouts mit einer einzigen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="962e3-173">Recommended single button layout</span></span>

<span data-ttu-id="962e3-174">Wenn in Ihrem Layout nur eine einzige Schaltfläche benötigt wird, sollten Sie diese je nach ihrem Containerkontext entweder linksbündig oder rechtsbündig ausrichten.</span><span class="sxs-lookup"><span data-stu-id="962e3-174">If your layout requires only one button, it should be either left- or right-aligned based on its container context.</span></span>

-   <span data-ttu-id="962e3-175">In Dialogfeldern mit nur einer einzigen Schaltfläche sollte die Schaltfläche **rechtsbündig** ausgerichtet sein.</span><span class="sxs-lookup"><span data-stu-id="962e3-175">Dialogs with only one button should **right-align** the button.</span></span> <span data-ttu-id="962e3-176">Stellen Sie bei Dialogfeldern mit nur einer einzigen Schaltfläche sicher, dass die Schaltfläche die sichere, nicht destruktive Aktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="962e3-176">If your dialog contains only one button, ensure that the button performs the safe, nondestructive action.</span></span> <span data-ttu-id="962e3-177">Wenn Sie die Klasse [ContentDialog](dialogs.md) verwenden und nur eine einzige Schaltfläche definieren, wird diese Schaltfläche automatisch rechtsbündig ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="962e3-177">If you use [ContentDialog](dialogs.md) and specify a single button, it will automatically right-align.</span></span>

![Schaltfläche in einem Dialogfeld](images/pushbutton_doc_dialog.png)

-   <span data-ttu-id="962e3-179">Wird die Schaltfläche als Teil einer Containerbenutzeroberfläche angezeigt (z.B. innerhalb einer Popupbenachrichtigung, eines Flyouts oder eines Listenansicht-Elements), sollten Sie die Schaltfläche innerhalb des Containers **rechtsbündig** ausrichten.</span><span class="sxs-lookup"><span data-stu-id="962e3-179">If your button appears within a container UI (for example, within a toast notification, a flyout, or a list view item), you should **right-align** the button within the container.</span></span>

![Eine Schaltfläche in einem Container](images/pushbutton_doc_container.png)

-   <span data-ttu-id="962e3-181">Auf Seiten mit einer einzigen Schaltfläche (z.B. einer Einstellungsseite mit einer „Anwenden“-Schaltfläche am unteren Rand) sollten Sie die Schaltfläche **linksbündig** ausrichten.</span><span class="sxs-lookup"><span data-stu-id="962e3-181">In pages that contain a single button (for example, an "Apply" button at the bottom of a settings page), you should **left-align** the button.</span></span> <span data-ttu-id="962e3-182">Das gewährleistet, dass die Schaltfläche passend zum übrigen Seiteninhalt ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="962e3-182">This ensures that the button aligns with the rest of the page content.</span></span>

![Eine Schaltfläche auf einer Seite](images/pushbutton_doc_page.png)

## <a name="back-buttons"></a><span data-ttu-id="962e3-184">„Zurück“-Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="962e3-184">Back buttons</span></span>

<span data-ttu-id="962e3-185">Die Zurück-Schaltfläche ist ein durch das System bereitgestelltes UI-Element, das die Rückwärtsnavigation über den Back-Stapel oder den Navigationsverlauf des Benutzers ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="962e3-185">The back button is a system-provided UI element that enables backward navigation through either the back stack or navigation history of the user.</span></span> <span data-ttu-id="962e3-186">Sie müssen keine eigene Zurück-Schaltfläche erstellen, aber unter Umständen ist etwas Aufwand erforderlich, um eine gute Rückwärtsnavigation zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="962e3-186">You don't have to create your own back button, but you might have to do some work to enable a good backwards navigation experience.</span></span> <span data-ttu-id="962e3-187">Weitere Informationen finden Sie unter [Verlauf und Rückwärtsnavigation](../basics/navigation-history-and-backwards-navigation.md).</span><span class="sxs-lookup"><span data-stu-id="962e3-187">For more info, see [History and backwards navigation](../basics/navigation-history-and-backwards-navigation.md)</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="962e3-188">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="962e3-188">Get the sample code</span></span>

- <span data-ttu-id="962e3-189">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="962e3-189">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>


## <a name="related-articles"></a><span data-ttu-id="962e3-190">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="962e3-190">Related articles</span></span>
- [<span data-ttu-id="962e3-191">Button-Klasse</span><span class="sxs-lookup"><span data-stu-id="962e3-191">Button class</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx)
- [<span data-ttu-id="962e3-192">Optionsfelder</span><span class="sxs-lookup"><span data-stu-id="962e3-192">Radio buttons</span></span>](radio-button.md)
- [<span data-ttu-id="962e3-193">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="962e3-193">Check boxes</span></span>](checkbox.md)
- [<span data-ttu-id="962e3-194">Umschalter</span><span class="sxs-lookup"><span data-stu-id="962e3-194">Toggle switches</span></span>](toggles.md)
