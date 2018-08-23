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
ms.openlocfilehash: f0bf7731a8480fb4f6d81368227ad6259780381b
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2817124"
---
# <a name="buttons"></a><span data-ttu-id="29b69-103">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="29b69-103">Buttons</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29b69-104">In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. geändert werden.</span><span class="sxs-lookup"><span data-stu-id="29b69-104">This article describes functionality that hasn’t been released yet and may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="29b69-105">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="29b69-105">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span> <span data-ttu-id="29b69-106">Preview-Features erfordern die [aktuellsten Windows 10 Insider Preview Build und SDK](https://insider.windows.com/for-developers/) oder der [Bibliothek für Windows-Benutzeroberfläche](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="29b69-106">Preview features require the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="29b69-107">Eine Schaltfläche ermöglicht dem Benutzer das unmittelbare Auslösen einer Aktion.</span><span class="sxs-lookup"><span data-stu-id="29b69-107">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="29b69-108">Einige Schaltflächen sind für bestimmte Aufgaben wie das Navigation, wiederholte Aktionen oder einer Präsentation Menüs spezialisierten.</span><span class="sxs-lookup"><span data-stu-id="29b69-108">Some buttons are specialized for particular tasks, such as navigation, repeated actions, or presenting menus.</span></span>

![Beispiel für Schaltflächen](images/controls/button.png)

<span data-ttu-id="29b69-110">Das Verwendung von XAML-Framework bietet ein standard Button-Steuerelement als auch mehrere spezielle Button-Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="29b69-110">The XAML framework provides a standard button control as well as several specialized button controls.</span></span>

<span data-ttu-id="29b69-111">Steuerelement</span><span class="sxs-lookup"><span data-stu-id="29b69-111">Control</span></span> | <span data-ttu-id="29b69-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="29b69-112">Description</span></span>
------- | -----------
[<span data-ttu-id="29b69-113">Button</span><span class="sxs-lookup"><span data-stu-id="29b69-113">Button</span></span>](/uwp/api/windows.ui.xaml.controls.button) | <span data-ttu-id="29b69-114">Initiiert eine sofortige Aktion an.</span><span class="sxs-lookup"><span data-stu-id="29b69-114">Initiates an immediate action.</span></span> <span data-ttu-id="29b69-115">Kann mit einem Click-Ereignis oder den Befehl Bindung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="29b69-115">Can be used with a Click event or Command binding.</span></span>
[<span data-ttu-id="29b69-116">RepeatButton</span><span class="sxs-lookup"><span data-stu-id="29b69-116">RepeatButton</span></span>](/uwp/api/windows.ui.xaml.controls.primitives.repeatbutton) | <span data-ttu-id="29b69-117">Eine Schaltfläche, die gedrückte kontinuierlich ein Click-Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="29b69-117">A button that raises a Click event continuously while pressed.</span></span>
[<span data-ttu-id="29b69-118">HyperlinkButton</span><span class="sxs-lookup"><span data-stu-id="29b69-118">HyperlinkButton</span></span>](/uwp/api/windows.ui.xaml.controls.hyperlinkbutton) | <span data-ttu-id="29b69-119">Eine Schaltfläche, die formatiert wurde, wie ein Hyperlink, für die Navigation.</span><span class="sxs-lookup"><span data-stu-id="29b69-119">A button that's styled like a hyperlink, used for navigation.</span></span> <span data-ttu-id="29b69-120">Weitere Informationen finden Sie unter [Hyperlinks](hyperlinks.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-120">See [Hyperlinks](hyperlinks.md) for more info.</span></span>
[<span data-ttu-id="29b69-121">DropDownButton</span><span class="sxs-lookup"><span data-stu-id="29b69-121">DropDownButton</span></span>](/uwp/api/windows.ui.xaml.controls.dropdownbutton) | <span data-ttu-id="29b69-122">(Vorschau) Eine Schaltfläche mit ein Chevron festgelegt, um eine angefügte flyoutmenü zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="29b69-122">(Preview) A button with a chevron to open an attached flyout.</span></span>
[<span data-ttu-id="29b69-123">SplitButton</span><span class="sxs-lookup"><span data-stu-id="29b69-123">SplitButton</span></span>](/uwp/api/windows.ui.xaml.controls.splitbutton) | <span data-ttu-id="29b69-124">(Vorschau) Eine Schaltfläche mit zwei Seiten.</span><span class="sxs-lookup"><span data-stu-id="29b69-124">(Preview) A button with two sides.</span></span> <span data-ttu-id="29b69-125">Andererseits initiiert eine Aktion, und die anderen Seite wird ein Menü geöffnet.</span><span class="sxs-lookup"><span data-stu-id="29b69-125">One side initiates an action, and the other side opens a menu.</span></span>
[<span data-ttu-id="29b69-126">ToggleSplitButton</span><span class="sxs-lookup"><span data-stu-id="29b69-126">ToggleSplitButton</span></span>](/uwp/api/windows.ui.xaml.controls.togglesplitbutton) | <span data-ttu-id="29b69-127">(Vorschau) Eine Umschaltfläche mit zwei Seiten.</span><span class="sxs-lookup"><span data-stu-id="29b69-127">(Preview) A toggle button with two sides.</span></span> <span data-ttu-id="29b69-128">Andererseits ein-/ausschalten umgeschaltet, und die anderen Seite wird ein Menü geöffnet.</span><span class="sxs-lookup"><span data-stu-id="29b69-128">One side toggles on/off, and the other side opens a menu.</span></span>

| **<span data-ttu-id="29b69-129">Abrufen der Windows-UI-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="29b69-129">Get the Windows UI Library</span></span>** |
| - |
| <span data-ttu-id="29b69-130">DropDownButton, SplitButton und ToggleSplitButton sind Bestandteil der Windows-UI-Bibliothek, ein NuGet-Paket, das neue Steuerelemente und Features der Benutzeroberfläche für apps UWP enthält.</span><span class="sxs-lookup"><span data-stu-id="29b69-130">DropDownButton, SplitButton, and ToggleSplitButton are included as part of the Windows UI Library, a NuGet package that contains new controls and UI features for UWP apps.</span></span> <span data-ttu-id="29b69-131">Weitere Informationen, einschließlich Installationshinweise finden Sie unter [Übersicht über die Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="29b69-131">For more info, including installation instructions, see the [Windows UI Library overview](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span> |

| **<span data-ttu-id="29b69-132">Plattform-APIs</span><span class="sxs-lookup"><span data-stu-id="29b69-132">Platform APIs</span></span>** | **<span data-ttu-id="29b69-133">Windows-UI Library-APIs</span><span class="sxs-lookup"><span data-stu-id="29b69-133">Windows UI Library APIs</span></span>** |
| - | - |
| <span data-ttu-id="29b69-134">Haben [click-Ereignis](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click), [Command-Eigenschaft](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.command)</span><span class="sxs-lookup"><span data-stu-id="29b69-134">[Click event](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click), [Command property](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.command)</span></span> | <span data-ttu-id="29b69-135">[DropDownButton-Klasse](/uwp/api/microsoft.ui.xaml.controls.dropdownbutton), [SplitButton-Klasse](/uwp/api/microsoft.ui.xaml.controls.splitbutton), [ToggleSplitButton-Klasse](/uwp/api/microsoft.ui.xaml.controls.togglesplitbutton)</span><span class="sxs-lookup"><span data-stu-id="29b69-135">[DropDownButton class](/uwp/api/microsoft.ui.xaml.controls.dropdownbutton), [SplitButton class](/uwp/api/microsoft.ui.xaml.controls.splitbutton), [ToggleSplitButton class](/uwp/api/microsoft.ui.xaml.controls.togglesplitbutton)</span></span> |

## <a name="is-this-the-right-control"></a><span data-ttu-id="29b69-136">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="29b69-136">Is this the right control?</span></span>

<span data-ttu-id="29b69-137">Verwenden Sie eine **Schaltfläche** ermöglichen den Benutzer eine sofortige Aktion, wie etwa Absenden eines Formulars zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="29b69-137">Use a **Button** to let the user initiate an immediate action, such as submitting a form.</span></span>

<span data-ttu-id="29b69-138">Verwenden Sie eine Schaltfläche nicht, wenn die Aktion zum Navigieren zu einer anderen Seite; Verwenden Sie stattdessen eine [HyperlinkButton](/uwp/api/windows.ui.xaml.controls.hyperlinkbutton) .</span><span class="sxs-lookup"><span data-stu-id="29b69-138">Don't use a button when the action is to navigate to another page; use a [HyperlinkButton](/uwp/api/windows.ui.xaml.controls.hyperlinkbutton) instead.</span></span> <span data-ttu-id="29b69-139">Weitere Informationen finden Sie unter [Hyperlinks](hyperlinks.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-139">See [Hyperlinks](hyperlinks.md) for more info.</span></span>
> <span data-ttu-id="29b69-140">Ausnahme: Für die Navigation in einem Assistenten können die Schaltflächen „Zurück“ und „Weiter“ verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="29b69-140">Exception: For wizard navigation, use buttons labeled "Back" and "Next".</span></span> <span data-ttu-id="29b69-141">Für andere Arten von verwenden Abwärtskompatibilität Navigation oder die Navigation zu einer oberen Ebene, Sie eine [Schaltfläche "zurück"](../basics/navigation-history-and-backwards-navigation.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-141">For other types of backwards navigation or navigation to an upper level, use a [back button](../basics/navigation-history-and-backwards-navigation.md).</span></span>

<span data-ttu-id="29b69-142">Verwenden Sie eine **RepeatButton** , wenn der Benutzer eine Aktion wiederholt auslösen möchten.</span><span class="sxs-lookup"><span data-stu-id="29b69-142">Use a **RepeatButton** when the user might want to trigger an action repeatedly.</span></span> <span data-ttu-id="29b69-143">Verwenden Sie beispielsweise eine RepeatButton erhöhen oder verringern eines Wertes in einen Leistungsindikator.</span><span class="sxs-lookup"><span data-stu-id="29b69-143">For example, use a RepeatButton to increment or decrement a value in a counter.</span></span>

<span data-ttu-id="29b69-144">Verwenden Sie eine **DropDownButton** , wenn die Schaltfläche ein flyoutmenü verfügt, weitere Optionen enthält.</span><span class="sxs-lookup"><span data-stu-id="29b69-144">Use a **DropDownButton** when the button has a flyout that contains more options.</span></span> <span data-ttu-id="29b69-145">Das standardmäßige Chevron bietet einen visuellen Hinweis, dass die Schaltfläche ein flyoutmenü enthält.</span><span class="sxs-lookup"><span data-stu-id="29b69-145">The default chevron provides a visual indication that the button includes a flyout.</span></span>

<span data-ttu-id="29b69-146">Verwenden Sie eine **SplitButton** , wenn Sie möchten den Benutzer können sofortige eine Aktion zu initiieren, oder wählen unabhängig voneinander zusätzliche Optionen.</span><span class="sxs-lookup"><span data-stu-id="29b69-146">Use a **SplitButton** when you want the user to be able to initiate an immediate action or choose from additional options independently.</span></span>

## <a name="examples"></a><span data-ttu-id="29b69-147">Beispiele</span><span class="sxs-lookup"><span data-stu-id="29b69-147">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="29b69-148">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="29b69-148">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="29b69-149">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/Button">die App zu öffnen und die Schaltfläche in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="29b69-149">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/Button">open the app and see the Button in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="29b69-150">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="29b69-150">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="29b69-151">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="29b69-151">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="29b69-152">In diesem Beispiel werden zwei Schaltflächen („Zulassen“ und „Blockieren“) in einem Dialogfeld verwendet, über das Zugriff auf den Standort des Benutzers angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="29b69-152">This example uses two buttons, Allow and Block, in a dialog requesting location access.</span></span>

![Beispiel für Schaltflächen in einem Dialogfeld](images/dialogs/dialog_RS2_two_button.png)

## <a name="create-a-button"></a><span data-ttu-id="29b69-154">Erstellen einer Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="29b69-154">Create a button</span></span>

<span data-ttu-id="29b69-155">Dieses Beispiel zeigt eine Schaltfläche, die auf einen Mausklick reagiert.</span><span class="sxs-lookup"><span data-stu-id="29b69-155">This example shows a button that responds to a click.</span></span>

<span data-ttu-id="29b69-156">Erstellen Sie die Schaltfläche in XAML.</span><span class="sxs-lookup"><span data-stu-id="29b69-156">Create the button in XAML.</span></span>

```xaml
<Button Content="Subscribe" Click="SubscribeButton_Click"/>
```

<span data-ttu-id="29b69-157">Sie können die Schaltfläche auch in Code erstellen.</span><span class="sxs-lookup"><span data-stu-id="29b69-157">Or create the button in code.</span></span>

```csharp
Button subscribeButton = new Button();
subscribeButton.Content = "Subscribe";
subscribeButton.Click += SubscribeButton_Click;

// Add the button to a parent container in the visual tree.
stackPanel1.Children.Add(subscribeButton);
```

<span data-ttu-id="29b69-158">Behandeln Sie das Click-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="29b69-158">Handle the Click event.</span></span>

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

### <a name="button-interaction"></a><span data-ttu-id="29b69-159">Interaktion mit Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="29b69-159">Button interaction</span></span>

<span data-ttu-id="29b69-160">Wenn Sie mit einem Finger oder Stift auf eine Schaltfläche tippen oder mit der linken Maustaste darauf klicken, löst die Schaltfläche das [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="29b69-160">When you tap a Button with a finger or stylus, or press a left mouse button while the pointer is over it, the button raises the [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx) event.</span></span> <span data-ttu-id="29b69-161">Bei einer Schaltfläche mit Tastaturfokus wird das Click-Ereignis auch durch Drücken der Eingabe- oder Leertaste ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="29b69-161">If a button has keyboard focus, pressing the Enter key or the Spacebar key also raises the Click event.</span></span>

<span data-ttu-id="29b69-162">Sie können für eine Schaltfläche generell keine Low-Level-Ereignisse des Typs [PointerPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.pointerpressed.aspx) behandeln, da sie stattdessen mit dem Click-Verhalten konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="29b69-162">You generally can't handle low-level [PointerPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.pointerpressed.aspx) events on a Button because it has the Click behavior instead.</span></span> <span data-ttu-id="29b69-163">Weitere Informationen finden Sie unter [Übersicht über Ereignisse und Routingereignisse](https://msdn.microsoft.com/library/windows/apps/mt185584.aspx).</span><span class="sxs-lookup"><span data-stu-id="29b69-163">For more info, see [Events and routed events overview](https://msdn.microsoft.com/library/windows/apps/mt185584.aspx).</span></span>

<span data-ttu-id="29b69-164">Durch Änderung der Eigenschaft [ClickMode](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.clickmode) können Sie anpassen, wie eine Schaltfläche Click-Ereignisse auslöst.</span><span class="sxs-lookup"><span data-stu-id="29b69-164">You can change how a button raises the Click event by changing the [ClickMode](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.clickmode) property.</span></span> <span data-ttu-id="29b69-165">Der ClickMode-Standardwert ist **Version**, Sie können den ClickMode einer Schaltfläche jedoch auch auf **Zeigen** oder **Drücken** festlegen.</span><span class="sxs-lookup"><span data-stu-id="29b69-165">The default ClickMode value is **Release**, but you also can set a button's ClickMode to **Hover** or **Press**.</span></span> <span data-ttu-id="29b69-166">Wenn als ClickMode-Wert **Hover** festgelegt ist, kann das Click-Event nicht über die Tastatur oder durch Berührung ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="29b69-166">If ClickMode is **Hover**, the Click event can't be raised with the keyboard or touch.</span></span>


### <a name="button-content"></a><span data-ttu-id="29b69-167">Inhalt von Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="29b69-167">Button content</span></span>

<span data-ttu-id="29b69-168">„Button“ ist ein Element des Typs [ContentControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.aspx).</span><span class="sxs-lookup"><span data-stu-id="29b69-168">Button is a [ContentControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.aspx).</span></span> <span data-ttu-id="29b69-169">Die zugehörige XAML-Inhaltseigenschaft ist [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx). Mit ihr lässt sich in XAML folgende Syntax nutzen: `<Button>A button's content</Button>`.</span><span class="sxs-lookup"><span data-stu-id="29b69-169">Its XAML content property is [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx), which enables a syntax like this for XAML: `<Button>A button's content</Button>`.</span></span> <span data-ttu-id="29b69-170">Sie können jedes Objekt als Inhalt der Schaltfläche festlegen.</span><span class="sxs-lookup"><span data-stu-id="29b69-170">You can set any object as the button's content.</span></span> <span data-ttu-id="29b69-171">Wenn der Inhalt ein [UIElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.aspx) ist, wird er in der Schaltfläche gerendert.</span><span class="sxs-lookup"><span data-stu-id="29b69-171">If the content is a [UIElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.aspx), it is rendered in the button.</span></span> <span data-ttu-id="29b69-172">Wenn es sich beim Inhalt um einen anderen Objekttyp handelt, wird die entsprechende Zeichenfolgendarstellung in der Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="29b69-172">If the content is another type of object, its string representation is shown in the button.</span></span>

<span data-ttu-id="29b69-173">Der Inhalt einer Schaltfläche ist für gewöhnlich Text.</span><span class="sxs-lookup"><span data-stu-id="29b69-173">A button's content is usually text.</span></span> <span data-ttu-id="29b69-174">Nachstehend finden Sie Entwurfsempfehlungen für Schaltflächen mit Textinhalt:</span><span class="sxs-lookup"><span data-stu-id="29b69-174">Here are design recommendations for buttons with text content:</span></span>
-   <span data-ttu-id="29b69-175">Verwenden Sie kurze, spezifische und selbsterklärende Texte, aus denen die Funktion einer Schaltfläche eindeutig hervorgeht.</span><span class="sxs-lookup"><span data-stu-id="29b69-175">Use a concise, specific, self-explanatory text that clearly describes the action that the button performs.</span></span> <span data-ttu-id="29b69-176">In der Regel umfasst der Schaltflächen-Textinhalt ein einzelnes Wort: ein Verb.</span><span class="sxs-lookup"><span data-stu-id="29b69-176">Usually button text content is a single word, a verb.</span></span>
-   <span data-ttu-id="29b69-177">Verwenden Sie die standardmäßige Schriftart, es sei denn, Sie müssen entsprechend Ihren Markenrichtlinien eine andere verwenden.</span><span class="sxs-lookup"><span data-stu-id="29b69-177">Use the default font unless your brand guidelines tell you to use something different.</span></span>
-   <span data-ttu-id="29b69-178">Vermeiden Sie für kürzeren Text schmale Befehlsschaltflächen, indem Sie eine Schaltflächen-Mindestbreite von 120Pixel verwenden.</span><span class="sxs-lookup"><span data-stu-id="29b69-178">For shorter text, avoid narrow command buttons by using a minimum button width of 120px.</span></span>
- <span data-ttu-id="29b69-179">Vermeiden Sie für längeren Text breite Befehlsschaltflächen, indem Sie Text auf eine maximale Länge von 26Zeichen beschränken.</span><span class="sxs-lookup"><span data-stu-id="29b69-179">For longer text, avoid wide command buttons by limiting text to a maximum length of 26 characters.</span></span>
-   <span data-ttu-id="29b69-180">Wenn der Textinhalt der Schaltfläche dynamisch ist (beispielsweise wenn er [lokalisiert](../globalizing/globalizing-portal.md) ist), ziehen Sie die Größenänderung der Schaltfläche und das in Betracht, was mit den Steuerelementen herum passiert.</span><span class="sxs-lookup"><span data-stu-id="29b69-180">If the button's text content is dynamic (i.e., it is [localized](../globalizing/globalizing-portal.md)), consider how the button will resize and what will happen to controls around it.</span></span>

<table>
<tr>
<td> <b><span data-ttu-id="29b69-181">Folgendes muss geändert werden:</span><span class="sxs-lookup"><span data-stu-id="29b69-181">Need to fix:</span></span></b><br> <span data-ttu-id="29b69-182">Schaltflächen mit überlaufendem Text.</span><span class="sxs-lookup"><span data-stu-id="29b69-182">Buttons with overflowing text.</span></span> </td>
<td> <img src="images/button-wraptext.png"/> </td>
</tr>
<tr>
<td> <b><span data-ttu-id="29b69-183">Option 1:</span><span class="sxs-lookup"><span data-stu-id="29b69-183">Option 1:</span></span></b><br> <span data-ttu-id="29b69-184">Vergrößern Sie die Breite der Schaltflächen, stapeln Sie Schaltflächen und brechen Sie Text um, wenn er mehr als 26Zeichen umfasst.</span><span class="sxs-lookup"><span data-stu-id="29b69-184">Increase button width, stack buttons, and wrap if text length is greater than 26 characters.</span></span> </td>
<td> <img src="images/button-wraptext1.png"> </td>
</tr>
<tr>
<td> <b><span data-ttu-id="29b69-185">Option 2:</span><span class="sxs-lookup"><span data-stu-id="29b69-185">Option 2:</span></span></b><br> <span data-ttu-id="29b69-186">Erhöhen Sie die Schaltflächenhöhe und brechen Sie Text um.</span><span class="sxs-lookup"><span data-stu-id="29b69-186">Increase button height, and wrap text.</span></span> </td>
<td> <img src="images/button-wraptext2.png"> </td>
</tr>
</table>

<span data-ttu-id="29b69-187">Sie können auch die visuellen Elemente anpassen, die die Darstellung der Schaltfläche ausmachen.</span><span class="sxs-lookup"><span data-stu-id="29b69-187">You can also customize visuals that make up the button's appearance.</span></span> <span data-ttu-id="29b69-188">Sie können beispielsweise den Text durch ein Symbol ersetzen oder ein Symbol und Text verwenden.</span><span class="sxs-lookup"><span data-stu-id="29b69-188">For example, you could replace the text with an icon, or use an icon plus text.</span></span>

<span data-ttu-id="29b69-189">Im folgenden Beispiel wird ein **StackPanel**-Element, das ein Bild und Text enthält, als Inhalt einer Schaltfläche festgelegt.</span><span class="sxs-lookup"><span data-stu-id="29b69-189">Here, a **StackPanel** that contains an image and text is set as the content of a button.</span></span>

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

<span data-ttu-id="29b69-190">Die Schaltfläche sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="29b69-190">The button looks like this.</span></span>

![Eine Schaltfläche mit Bild- und Textinhalt](images/button-orange.png)

## <a name="create-a-repeat-button"></a><span data-ttu-id="29b69-192">Erstellen einer Wiederholungsschaltfläche</span><span class="sxs-lookup"><span data-stu-id="29b69-192">Create a repeat button</span></span>

<span data-ttu-id="29b69-193">Eine Schaltfläche des Typs [RepeatButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx) ist eine Schaltfläche, die das [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)-Ereignis ab dem Moment des Klickens oder Drückens auf die Schaltfläche solange wiederholt auslöst, bis der Benutzer die Maustaste loslässt oder nicht mehr auf die Schaltfläche drückt.</span><span class="sxs-lookup"><span data-stu-id="29b69-193">A [RepeatButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx) is a button that raises [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx) events repeatedly from the time it's pressed until it's released.</span></span> <span data-ttu-id="29b69-194">Über die Eigenschaft [Delay](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.delay.aspx) können Sie festlegen, wie lange eine Schaltfläche des Typs„RepeatButton“ nach dem Klicken oder Drücken wartet, bevor sie mit der Wiederholung der Click-Aktion beginnt.</span><span class="sxs-lookup"><span data-stu-id="29b69-194">Set the [Delay](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.delay.aspx) property to specify the time that the RepeatButton waits after it is pressed before it starts repeating the click action.</span></span> <span data-ttu-id="29b69-195">Über die Eigenschaft [Interval](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.interval.aspx) können Sie den Zeitintervall zwischen den einzelnen Wiederholungen der Click-Aktion definieren.</span><span class="sxs-lookup"><span data-stu-id="29b69-195">Set the [Interval](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.interval.aspx) property to specify the time between repetitions of the click action.</span></span> <span data-ttu-id="29b69-196">Die Zeiten beider Eigenschaften werden in Millisekunden angegeben.</span><span class="sxs-lookup"><span data-stu-id="29b69-196">Times for both properties are specified in milliseconds.</span></span>

<span data-ttu-id="29b69-197">Das folgende Beispiel zeigt zwei „RepeatButton“-Steuerelemente. Ihre jeweiligen Click-Ereignisse dienen dazu, den Wert in einem Textblock zu erhöhen oder zu verringern.</span><span class="sxs-lookup"><span data-stu-id="29b69-197">The following example shows two RepeatButton controls whose respective Click events are used to increase and decrease the value shown in a text block.</span></span>

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

## <a name="create-a-drop-down-button"></a><span data-ttu-id="29b69-198">Erstellen Sie ein Dropdown-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="29b69-198">Create a drop down button</span></span>

> <span data-ttu-id="29b69-199">**Vorschau**: DropDownButton erfordert die [aktuellsten Windows 10 Insider Preview Build und SDK](https://insider.windows.com/for-developers/) oder der [Bibliothek für Windows-Benutzeroberfläche](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="29b69-199">**Preview**: DropDownButton requires the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="29b69-200">Eine [DropDownButton](/uwp/api/windows.ui.xaml.controls.dropdownbutton) ist eine Schaltfläche, die einem Chevron festgelegt als ein optischer Indikator zeigt an, dass es eine angefügte flyoutmenü verfügt, weitere Optionen enthält.</span><span class="sxs-lookup"><span data-stu-id="29b69-200">A [DropDownButton](/uwp/api/windows.ui.xaml.controls.dropdownbutton) is a button that shows a chevron as a visual indicator that it has an attached flyout that contains more options.</span></span> <span data-ttu-id="29b69-201">Es hat die gleiche Wirkung wie einer Standardschaltfläche mit einem Dropdown; nur die Darstellung unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="29b69-201">It has the same behavior as a standard Button with a flyout; only the appearance is different.</span></span>

<span data-ttu-id="29b69-202">Die Dropdown-Schaltfläche erbt das Click-Ereignis, aber in der Regel verwenden Sie es.</span><span class="sxs-lookup"><span data-stu-id="29b69-202">The drop down button inherits the Click event, but you typically don't use it.</span></span> <span data-ttu-id="29b69-203">Verwenden Sie die Dropdown-Eigenschaft zum Anfügen einer flyoutmenü und Aufrufen von Aktionen mithilfe von Menüoptionen in der Dropdown.</span><span class="sxs-lookup"><span data-stu-id="29b69-203">Instead, you use the Flyout property to attach a flyout and invoke actions using menu options in the flyout.</span></span> <span data-ttu-id="29b69-204">Das Flyout wird beim Klicken auf die Schaltfläche automatisch geöffnet.</span><span class="sxs-lookup"><span data-stu-id="29b69-204">The flyout opens automatically when the button is clicked.</span></span>

> [!TIP]
> <span data-ttu-id="29b69-205">Weitere Informationen zu Flyouts finden Sie unter [Menüs und Kontextmenüs](menus.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-205">For more info about flyouts, see [Menus and context menus](menus.md).</span></span>

### <a name="example---drop-down-button"></a><span data-ttu-id="29b69-206">Beispiel - Dropdown-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="29b69-206">Example - Drop down button</span></span>

<span data-ttu-id="29b69-207">In diesem Beispiel wird gezeigt, wie eine Dropdown-Schaltfläche mit einer flyoutmenü erstellen, Befehle für die Ausrichtung von Absätzen in einem RichEditBox enthält.</span><span class="sxs-lookup"><span data-stu-id="29b69-207">This example shows how to create a drop down button with a flyout that contains commands for paragraph alignment in a RichEditBox.</span></span> <span data-ttu-id="29b69-208">(Weitere Informationen und Code finden Sie unter [Rich Eingabefelds](rich-edit-box.md)).</span><span class="sxs-lookup"><span data-stu-id="29b69-208">(For more info and code, see [Rich edit box](rich-edit-box.md)).</span></span>

![Ein Dropdown-Schaltfläche mit Befehle für das Ausrichten](images/drop-down-button-align.png)

```xaml
<DropDownButton ToolTipService.ToolTip="Alignment">
    <TextBlock FontFamily="Segoe MDL2 Assets" FontSize="16" Text="&#xE8E4;"/>
    <DropDownButton.Flyout>
        <MenuFlyout Placement="BottomEdgeAlignedLeft">
            <MenuFlyoutItem Text="Left" Icon="AlignLeft" Tag="left"
                            Click="AlignmentMenuFlyoutItem_Click"/>
            <MenuFlyoutItem Text="Center" Icon="AlignCenter" Tag="center"
                            Click="AlignmentMenuFlyoutItem_Click"/>
            <MenuFlyoutItem Text="Right" Icon="AlignRight" Tag="right"
                            Click="AlignmentMenuFlyoutItem_Click"/>
        </MenuFlyout>
    </DropDownButton.Flyout>
</DropDownButton>
```

```csharp
private void AlignmentMenuFlyoutItem_Click(object sender, RoutedEventArgs e)
{
    var option = ((MenuFlyoutItem)sender).Tag.ToString();

    Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
    if (selectedText != null)
    {
        // Apply the alignment to the selected paragraphs.
        var paragraphFormatting = selectedText.ParagraphFormat;
        if (option == "left")
        {
            paragraphFormatting.Alignment = Windows.UI.Text.ParagraphAlignment.Left;
        }
        else if (option == "center")
        {
            paragraphFormatting.Alignment = Windows.UI.Text.ParagraphAlignment.Center;
        }
        else if (option == "right")
        {
            paragraphFormatting.Alignment = Windows.UI.Text.ParagraphAlignment.Right;
        }
    }
}
```

## <a name="create-a-split-button"></a><span data-ttu-id="29b69-210">Erstellen Sie eine Trennschaltfläche</span><span class="sxs-lookup"><span data-stu-id="29b69-210">Create a split button</span></span>

> <span data-ttu-id="29b69-211">**Vorschau**: SplitButton erfordert die [aktuellsten Windows 10 Insider Preview Build und SDK](https://insider.windows.com/for-developers/) oder der [Bibliothek für Windows-Benutzeroberfläche](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="29b69-211">**Preview**: SplitButton requires the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="29b69-212">Ein [SplitButton](/uwp/api/windows.ui.xaml.controls.splitbutton) besteht aus zwei Teilen, die separat aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="29b69-212">A [SplitButton](/uwp/api/windows.ui.xaml.controls.splitbutton) has two parts that can be invoked separately.</span></span> <span data-ttu-id="29b69-213">Ein Teil einer Standardschaltfläche Verhalten und sofortige eine Aktion aufruft.</span><span class="sxs-lookup"><span data-stu-id="29b69-213">One part behaves like a standard button and invokes an immediate action.</span></span> <span data-ttu-id="29b69-214">Andererseits Ruft ein flyoutmenü, die zusätzliche Optionen, mit denen der Benutzer auswählen können.</span><span class="sxs-lookup"><span data-stu-id="29b69-214">The other part invokes a flyout that contains additional options that the user can choose from.</span></span>

> [!NOTE]
> <span data-ttu-id="29b69-215">Wenn mit Touch aufgerufen, verhält sich wie ein Dropdown-Schaltfläche Trennschaltfläche; Beide Hälften der Schaltfläche Aufrufen der Dropdown.</span><span class="sxs-lookup"><span data-stu-id="29b69-215">When invoked with touch, the split button behaves as a drop down button; both halves of the button invoke the flyout.</span></span> <span data-ttu-id="29b69-216">Mit anderen Methoden der Eingabe kann Benutzer entweder Hälfte der Schaltfläche separat aufrufen.</span><span class="sxs-lookup"><span data-stu-id="29b69-216">With other methods of input, a user can invoke either half of the button separately.</span></span>

<span data-ttu-id="29b69-217">Das normale Verhalten für eine Trennschaltfläche ist:</span><span class="sxs-lookup"><span data-stu-id="29b69-217">The typical behavior for a split button is:</span></span>

- <span data-ttu-id="29b69-218">Wenn der Benutzer auf das Schaltfläche Webpart klickt, behandeln Sie das Click-Ereignis, um die Option aufrufen, die derzeit in der Dropdownliste ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="29b69-218">When the user clicks the button part, handle the Click event to invoke the option that's currently selected in the drop down.</span></span>
- <span data-ttu-id="29b69-219">Die Dropdownliste geöffnet ist, Handle Aufruf der Elemente in der Dropdown-Liste beide ändern die option ausgewählt ist, und rufen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="29b69-219">When the drop down is open, handle invocation of the items in the drop down to both change which option is selected, and then invoke it.</span></span> <span data-ttu-id="29b69-220">Es ist wichtig, die das Dropdown-Element aufgerufen werden, da die Schaltfläche Click-Ereignis tritt nicht auf, wenn die Verwendung von Touch.</span><span class="sxs-lookup"><span data-stu-id="29b69-220">It's important to invoke the flyout item because the button Click event doesn't occur when using touch.</span></span>

> [!TIP]
> <span data-ttu-id="29b69-221">Es gibt viele Methoden, um Elemente in der Dropdownliste nach unten zu platzieren und deren Aufruf behandeln.</span><span class="sxs-lookup"><span data-stu-id="29b69-221">There are many ways to put items in the drop down and handle their invocation.</span></span> <span data-ttu-id="29b69-222">Wenn Sie eine ListView oder GridView verwenden, ist eine Möglichkeit, das SelectionChanged-Ereignis behandeln.</span><span class="sxs-lookup"><span data-stu-id="29b69-222">If you use a ListView or GridView, one way is to handle the SelectionChanged event.</span></span> <span data-ttu-id="29b69-223">Wenn Sie dies tun, [SingleSelectionFollowsFocus](/uwp/api/windows.ui.xaml.controls.listviewbase.singleselectionfollowsfocus) auf **false**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="29b69-223">If you do this, set [SingleSelectionFollowsFocus](/uwp/api/windows.ui.xaml.controls.listviewbase.singleselectionfollowsfocus) to **false**.</span></span> <span data-ttu-id="29b69-224">Auf diese Weise können Benutzer die Optionen über die Tastatur ohne das Element auf jeder Änderung aufrufen zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="29b69-224">This lets users navigate the options using a keyboard without invoking the item on each change.</span></span>

### <a name="example---split-button"></a><span data-ttu-id="29b69-225">Beispiel - Trennschaltfläche</span><span class="sxs-lookup"><span data-stu-id="29b69-225">Example - Split button</span></span>

<span data-ttu-id="29b69-226">In diesem Beispiel wird gezeigt, wie eine Trennschaltfläche erstellen, die verwendet wird, um die Vordergrundfarbe des ausgewählten Texts in einem RichEditBox ändern.</span><span class="sxs-lookup"><span data-stu-id="29b69-226">This example shows how to create a split button that is used to change the foreground color of selected text in a RichEditBox.</span></span> <span data-ttu-id="29b69-227">(Weitere Informationen und Code finden Sie unter [Rich Eingabefelds](rich-edit-box.md)).</span><span class="sxs-lookup"><span data-stu-id="29b69-227">(For more info and code, see [Rich edit box](rich-edit-box.md)).</span></span>

![Eine Trennschaltfläche für die Auswahl von Vordergrundfarbe](images/split-button-rtb.png)

```xaml
<SplitButton ToolTipService.ToolTip="Foreground color"
             Click="BrushButtonClick">
    <Border x:Name="SelectedColorBorder" Width="20" Height="20"/>
    <SplitButton.Flyout>
        <Flyout x:Name="BrushFlyout" Placement="BottomEdgeAlignedLeft">
            <!-- Set SingleSelectionFollowsFocus="False"
                 so that keyboard navigation works correctly. -->
            <GridView ItemsSource="{x:Bind ColorOptions}" 
                      SelectionChanged="BrushSelectionChanged"
                      SingleSelectionFollowsFocus="False"
                      SelectedIndex="0" Padding="0">
                <GridView.ItemTemplate>
                    <DataTemplate>
                        <Rectangle Fill="{Binding}" Width="20" Height="20"/>
                    </DataTemplate>
                </GridView.ItemTemplate>
                <GridView.ItemContainerStyle>
                    <Style TargetType="GridViewItem">
                        <Setter Property="Margin" Value="2"/>
                        <Setter Property="MinWidth" Value="0"/>
                        <Setter Property="MinHeight" Value="0"/>
                    </Style>
                </GridView.ItemContainerStyle>
            </GridView>
        </Flyout>
    </SplitButton.Flyout>
</SplitButton>
```

```csharp
public sealed partial class MainPage : Page
{
    // Color options that are bound to the grid in the split button flyout.
    private List<SolidColorBrush> ColorOptions = new List<SolidColorBrush>();
    private SolidColorBrush CurrentColorBrush = null;

    public MainPage()
    {
        this.InitializeComponent();

        // Add color brushes to the collection.
        ColorOptions.Add(new SolidColorBrush(Colors.Black));
        ColorOptions.Add(new SolidColorBrush(Colors.Red));
        ColorOptions.Add(new SolidColorBrush(Colors.Orange));
        ColorOptions.Add(new SolidColorBrush(Colors.Yellow));
        ColorOptions.Add(new SolidColorBrush(Colors.Green));
        ColorOptions.Add(new SolidColorBrush(Colors.Blue));
        ColorOptions.Add(new SolidColorBrush(Colors.Indigo));
        ColorOptions.Add(new SolidColorBrush(Colors.Violet));
        ColorOptions.Add(new SolidColorBrush(Colors.White));
    }

    private void BrushButtonClick(object sender, object e)
    {
        // When the button part of the split button is clicked,
        // apply the selected color.
        ChangeColor();
    }

    private void BrushSelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        // When the flyout part of the split button is opened and the user selects
        // an option, set their choice as the current color, apply it, then close the flyout.
        CurrentColorBrush = (SolidColorBrush)e.AddedItems[0];
        SelectedColorBorder.Background = CurrentColorBrush;
        ChangeColor();
        BrushFlyout.Hide();
    }

    private void ChangeColor()
    {
        // Apply the color to the selected text in a RichEditBox.
        Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
        if (selectedText != null)
        {
            Windows.UI.Text.ITextCharacterFormat charFormatting = selectedText.CharacterFormat;
            charFormatting.ForegroundColor = CurrentColorBrush.Color;
            selectedText.CharacterFormat = charFormatting;
        }
    }
}
```

## <a name="create-a-toggle-split-button"></a><span data-ttu-id="29b69-229">Erstellen Sie eine geteilte Umschaltfläche</span><span class="sxs-lookup"><span data-stu-id="29b69-229">Create a toggle split button</span></span>

> <span data-ttu-id="29b69-230">**Vorschau**: ToggleSplitButton erfordert die [aktuellsten Windows 10 Insider Preview Build und SDK](https://insider.windows.com/for-developers/) oder der [Bibliothek für Windows-Benutzeroberfläche](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="29b69-230">**Preview**: ToggleSplitButton requires the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="29b69-231">Eine [ToggleSplitButton](/uwp/api/windows.ui.xaml.controls.togglesplitbutton) besteht aus zwei Teilen, die separat aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="29b69-231">A [ToggleSplitButton](/uwp/api/windows.ui.xaml.controls.togglesplitbutton) has two parts that can be invoked separately.</span></span> <span data-ttu-id="29b69-232">Einerseits verhält sich wie eine Umschaltfläche, die aktiviert oder deaktiviert werden können.</span><span class="sxs-lookup"><span data-stu-id="29b69-232">One part behaves like a toggle button that can be on or off.</span></span> <span data-ttu-id="29b69-233">Andererseits Ruft ein flyoutmenü, die zusätzliche Optionen, mit denen der Benutzer auswählen können.</span><span class="sxs-lookup"><span data-stu-id="29b69-233">The other part invokes a flyout that contains additional options that the user can choose from.</span></span>

<span data-ttu-id="29b69-234">Eine Umschaltfläche Teilen wird in der Regel verwendet, aktivieren oder Deaktivieren eines Features, wenn das Feature für mehrere Optionen wurde, denen der Benutzer auswählen können.</span><span class="sxs-lookup"><span data-stu-id="29b69-234">A toggle split button is typically used to enable or disable a feature when the feature has multiple options that the user can choose from.</span></span> <span data-ttu-id="29b69-235">Beispielsweise könnte in einem Dokument-Editor Hiermit Listen aktivieren oder deaktivieren, während die Dropdownliste verwendet wird, um den Stil der Liste wählen.</span><span class="sxs-lookup"><span data-stu-id="29b69-235">For example, in a document editor, it could be used to turn lists on or off, while the drop down is used to choose the style of the list.</span></span>

> [!NOTE]
> <span data-ttu-id="29b69-236">Wenn mit Touch aufgerufen, verhält sich wie ein Dropdown-Schaltfläche Trennschaltfläche.</span><span class="sxs-lookup"><span data-stu-id="29b69-236">When invoked with touch, the split button behaves as a drop down button.</span></span> <span data-ttu-id="29b69-237">Mit anderen Methoden der Eingabe kann Benutzer entweder Hälfte der Schaltfläche separat aufrufen.</span><span class="sxs-lookup"><span data-stu-id="29b69-237">With other methods of input, a user can invoke either half of the button separately.</span></span> <span data-ttu-id="29b69-238">Touchscreens aufrufen, beide Hälften der Schaltfläche für die flyoutmenü.</span><span class="sxs-lookup"><span data-stu-id="29b69-238">With touch, both halves of the button invoke the flyout.</span></span> <span data-ttu-id="29b69-239">Daher müssen Sie eine Option in den Inhalt der flyoutmenü in aktiviert oder deaktiviert die Umschaltfläche einbeziehen.</span><span class="sxs-lookup"><span data-stu-id="29b69-239">Therefore, you must include an option in your flyout content to toggle the button on or off.</span></span>

### <a name="differences-with-togglebutton"></a><span data-ttu-id="29b69-240">Unterschiede mit ToggleButton-Objekt</span><span class="sxs-lookup"><span data-stu-id="29b69-240">Differences with ToggleButton</span></span>

<span data-ttu-id="29b69-241">Im Gegensatz zu [ToggleButton](/uwp/api/windows.ui.xaml.controls.primitives.togglebutton)verfügt ToggleSplitButton nicht unbestimmten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="29b69-241">Unlike [ToggleButton](/uwp/api/windows.ui.xaml.controls.primitives.togglebutton), ToggleSplitButton does not have an indeterminate state.</span></span> <span data-ttu-id="29b69-242">Daher sollten Sie diese Unterschiede bedenken:</span><span class="sxs-lookup"><span data-stu-id="29b69-242">As a result, you should keep in mind these differences:</span></span>

- <span data-ttu-id="29b69-243">ToggleSplitButton muss sich nicht auf einem **IsThreeState** -Eigenschaft oder **Indeterminate** -Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="29b69-243">ToggleSplitButton does not have an **IsThreeState** property or **Indeterminate** event.</span></span>
- <span data-ttu-id="29b69-244">Die [ToggleSplitButton.IsChecked](/uwp/api/windows.ui.xaml.controls.togglesplitbutton.ischecked) -Eigenschaft ist nur ein **Bool**, nicht **NULL-Werte zulässt Bool**.</span><span class="sxs-lookup"><span data-stu-id="29b69-244">The [ToggleSplitButton.IsChecked](/uwp/api/windows.ui.xaml.controls.togglesplitbutton.ischecked) property is just a **bool**, not a **nullable bool**.</span></span>
- <span data-ttu-id="29b69-245">ToggleSplitButton hat nur das [IsCheckedChanged](/uwp/api/windows.ui.xaml.controls.togglesplitbutton.ischeckedchanged) -Ereignis. Es hat keine separate **aktiviert** und **deaktiviert** Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="29b69-245">ToggleSplitButton has only the [IsCheckedChanged](/uwp/api/windows.ui.xaml.controls.togglesplitbutton.ischeckedchanged) event; it does not have separate **Checked** and **Unchecked** events.</span></span>

### <a name="example---toggle-split-button"></a><span data-ttu-id="29b69-246">Beispiel - Umschaltfläche unterteilte Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="29b69-246">Example - Toggle split button</span></span>

<span data-ttu-id="29b69-247">Das folgende Beispiel zeigt, wie eine Umschaltfläche Trennschaltfläche listenformatierung ein- oder ausschalten aktivieren verwendet werden, und Ändern des Stils eines der Liste in einem RichEditBox.</span><span class="sxs-lookup"><span data-stu-id="29b69-247">The following example shows how a toggle split button could be used to turn list formatting on or off, and change the style of the list, in a RichEditBox.</span></span> <span data-ttu-id="29b69-248">(Weitere Informationen und Code finden Sie unter [Rich Eingabefelds](rich-edit-box.md)).</span><span class="sxs-lookup"><span data-stu-id="29b69-248">(For more info and code, see [Rich edit box](rich-edit-box.md)).</span></span>

![Eine Umschaltfläche geteilten für die Auswahl von Listenformaten](images/toggle-split-button-open.png)

```xaml
<ToggleSplitButton x:Name="ListButton"
                   ToolTipService.ToolTip="List style"
                   Click="ListButton_Click"
                   IsCheckedChanged="ListStyleButton_IsCheckedChanged">
    <TextBlock FontFamily="Segoe MDL2 Assets" FontSize="16" Text="&#xE8FD;"/>
    <ToggleSplitButton.Flyout>
        <Flyout Placement="BottomEdgeAlignedLeft">
            <ListView x:Name="ListStylesListView"
                      SelectionChanged="ListStylesListView_SelectionChanged" 
                      SingleSelectionFollowsFocus="False">
                <StackPanel Tag="bullet" Orientation="Horizontal">
                    <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xE7C8;"/>
                    <TextBlock Text="Bullet" Margin="8,0"/>
                </StackPanel>
                <StackPanel Tag="alpha" Orientation="Horizontal">
                    <TextBlock Text="A" FontSize="24" Margin="2,0"/>
                    <TextBlock Text="Alpha" Margin="8"/>
                </StackPanel>
                <StackPanel Tag="numeric" Orientation="Horizontal">
                    <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xF146;"/>
                    <TextBlock Text="Numeric" Margin="8,0"/>
                </StackPanel>
                <TextBlock Tag="none" Text="None" Margin="28,0"/>
            </ListView>
        </Flyout>
    </ToggleSplitButton.Flyout>
</ToggleSplitButton>
```

```csharp
private void ListStyleButton_IsCheckedChanged(ToggleSplitButton sender, ToggleSplitButtonIsCheckedChangedEventArgs args)
{
    // Use the toggle button to turn the selected list style on or off.
    if (((ToggleSplitButton)sender).IsChecked == true)
    {
        // On. Apply the list style selected in the drop down to the selected text.
        var listStyle = ((FrameworkElement)(ListStylesListView.SelectedItem)).Tag.ToString();
        ApplyListStyle(listStyle);
    }
    else
    {
        // Off. Make the selected text not a list,
        // but don't change the list style selected in the drop down.
        ApplyListStyle("none");
    }
}

private void ListStylesListView_SelectionChanged(object sender, SelectionChangedEventArgs e)
{
    var listStyle = ((FrameworkElement)(e.AddedItems[0])).Tag.ToString();

    if (ListButton.IsChecked == true)
    {
        // Toggle button is on. Turn it off...
        if (listStyle == "none")
        {
            ListButton.IsChecked = false;
        }
        else
        {
            // or apply the new selection.
            ApplyListStyle(listStyle);
        }
    }
    else
    {
        // Toggle button is off. Turn it on, which will apply the selection
        // in the IsCheckedChanged event handler.
        ListButton.IsChecked = true;
    }
}

private void ApplyListStyle(string listStyle)
{
    Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
    if (selectedText != null)
    {
        // Apply the list style to the selected text.
        var paragraphFormatting = selectedText.ParagraphFormat;
        if (listStyle == "none")
        {  
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.None;
        }
        else if (listStyle == "bullet")
        {
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.Bullet;
        }
        else if (listStyle == "numeric")
        {
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.Arabic;
        }
        else if (listStyle == "alpha")
        {
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.UppercaseEnglishLetter;
        }
        selectedText.ParagraphFormat = paragraphFormatting;
    }
}
```

## <a name="recommendations"></a><span data-ttu-id="29b69-250">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="29b69-250">Recommendations</span></span>

- <span data-ttu-id="29b69-251">Der Zweck und Status einer Schaltfläche müssen für den Benutzer eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="29b69-251">Make sure the purpose and state of a button are clear to the user.</span></span>
- <span data-ttu-id="29b69-252">Wenn mehrere Schaltflächen für die gleiche Entscheidung (z.B. in einem Bestätigungsdialogfeld) vorhanden sind, stellen Sie die Schaltflächen für den Commit in der folgenden Reihenfolge dar, wobei [Ausführen] und [Nicht ausführen] bestimmte Antworten auf die Hauptanweisung sind:</span><span class="sxs-lookup"><span data-stu-id="29b69-252">When there are multiple buttons for the same decision (such as in a confirmation dialog), present the commit buttons in this order, where [Do it] and [Don't do it] are specific responses to the main instruction:</span></span>
    - <span data-ttu-id="29b69-253">OK/[Ausführen]/Ja</span><span class="sxs-lookup"><span data-stu-id="29b69-253">OK/[Do it]/Yes</span></span>
    - <span data-ttu-id="29b69-254">[Nicht ausführen]/Nein</span><span class="sxs-lookup"><span data-stu-id="29b69-254">[Don't do it]/No</span></span>
    - <span data-ttu-id="29b69-255">Abbrechen</span><span class="sxs-lookup"><span data-stu-id="29b69-255">Cancel</span></span>
- <span data-ttu-id="29b69-256">Stellen Sie dem Benutzer jeweils nur zwei Schaltflächen zur Verfügung, beispielsweise „Akzeptieren“ und „Abbrechen“.</span><span class="sxs-lookup"><span data-stu-id="29b69-256">Expose only one or two buttons to the user at a time, for example, Accept and Cancel.</span></span> <span data-ttu-id="29b69-257">Wenn Sie dem Benutzer mehr Aktionen zur Verfügung stellen möchten, sollten Sie [Kontrollkästchen](checkbox.md) oder [Optionsfelder](radio-button.md) verwenden, über die der Benutzer Aktionen mit einer einzelnen Befehlsschaltfläche auslösen kann.</span><span class="sxs-lookup"><span data-stu-id="29b69-257">If you need to expose more actions to the user, consider using [checkboxes](checkbox.md) or [radio buttons](radio-button.md) from which the user can select actions, with a single command button to trigger those actions.</span></span>
- <span data-ttu-id="29b69-258">Für eine Aktion, die auf mehreren Seiten in Ihrer App verfügbar sein muss, sollten Sie die Verwendung einer [unteren App-Leiste](app-bars.md) in Erwägung ziehen, anstatt eine Schaltfläche auf mehreren Seiten zu duplizieren.</span><span class="sxs-lookup"><span data-stu-id="29b69-258">For an action that needs to be available across multiple pages within your app, instead of duplicating a button on multiple pages, consider using a [bottom app bar](app-bars.md).</span></span>

### <a name="recommended-single-button-layout"></a><span data-ttu-id="29b69-259">Empfehlungen für Layouts mit einer einzigen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="29b69-259">Recommended single button layout</span></span>

<span data-ttu-id="29b69-260">Wenn in Ihrem Layout nur eine einzige Schaltfläche benötigt wird, sollten Sie diese je nach ihrem Containerkontext entweder linksbündig oder rechtsbündig ausrichten.</span><span class="sxs-lookup"><span data-stu-id="29b69-260">If your layout requires only one button, it should be either left- or right-aligned based on its container context.</span></span>

- <span data-ttu-id="29b69-261">In Dialogfeldern mit nur einer einzigen Schaltfläche sollte die Schaltfläche **rechtsbündig** ausgerichtet sein.</span><span class="sxs-lookup"><span data-stu-id="29b69-261">Dialogs with only one button should **right-align** the button.</span></span> <span data-ttu-id="29b69-262">Stellen Sie bei Dialogfeldern mit nur einer einzigen Schaltfläche sicher, dass die Schaltfläche die sichere, nicht destruktive Aktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="29b69-262">If your dialog contains only one button, ensure that the button performs the safe, nondestructive action.</span></span> <span data-ttu-id="29b69-263">Wenn Sie die Klasse [ContentDialog](dialogs.md) verwenden und nur eine einzige Schaltfläche definieren, wird diese Schaltfläche automatisch rechtsbündig ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="29b69-263">If you use [ContentDialog](dialogs.md) and specify a single button, it will automatically right-align.</span></span>

![Schaltfläche in einem Dialogfeld](images/pushbutton_doc_dialog.png)

- <span data-ttu-id="29b69-265">Wird die Schaltfläche als Teil einer Containerbenutzeroberfläche angezeigt (z.B. innerhalb einer Popupbenachrichtigung, eines Flyouts oder eines Listenansicht-Elements), sollten Sie die Schaltfläche innerhalb des Containers **rechtsbündig** ausrichten.</span><span class="sxs-lookup"><span data-stu-id="29b69-265">If your button appears within a container UI (for example, within a toast notification, a flyout, or a list view item), you should **right-align** the button within the container.</span></span>

![Eine Schaltfläche in einem Container](images/pushbutton_doc_container.png)

- <span data-ttu-id="29b69-267">Auf Seiten mit einer einzigen Schaltfläche (z.B. einer Einstellungsseite mit einer „Anwenden“-Schaltfläche am unteren Rand) sollten Sie die Schaltfläche **linksbündig** ausrichten.</span><span class="sxs-lookup"><span data-stu-id="29b69-267">In pages that contain a single button (for example, an "Apply" button at the bottom of a settings page), you should **left-align** the button.</span></span> <span data-ttu-id="29b69-268">Das gewährleistet, dass die Schaltfläche passend zum übrigen Seiteninhalt ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="29b69-268">This ensures that the button aligns with the rest of the page content.</span></span>

![Eine Schaltfläche auf einer Seite](images/pushbutton_doc_page.png)

## <a name="back-buttons"></a><span data-ttu-id="29b69-270">„Zurück“-Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="29b69-270">Back buttons</span></span>

<span data-ttu-id="29b69-271">Die Zurück-Schaltfläche ist ein durch das System bereitgestelltes UI-Element, das die Rückwärtsnavigation über den Back-Stapel oder den Navigationsverlauf des Benutzers ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="29b69-271">The back button is a system-provided UI element that enables backward navigation through either the back stack or navigation history of the user.</span></span> <span data-ttu-id="29b69-272">Sie müssen keine eigene Zurück-Schaltfläche erstellen, aber unter Umständen ist etwas Aufwand erforderlich, um eine gute Rückwärtsnavigation zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="29b69-272">You don't have to create your own back button, but you might have to do some work to enable a good backwards navigation experience.</span></span> <span data-ttu-id="29b69-273">Weitere Informationen finden Sie unter [Verlauf und Rückwärtsnavigation](../basics/navigation-history-and-backwards-navigation.md).</span><span class="sxs-lookup"><span data-stu-id="29b69-273">For more info, see [History and backwards navigation](../basics/navigation-history-and-backwards-navigation.md)</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="29b69-274">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="29b69-274">Get the sample code</span></span>

- <span data-ttu-id="29b69-275">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="29b69-275">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="29b69-276">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="29b69-276">Related articles</span></span>

- [<span data-ttu-id="29b69-277">Button-Klasse</span><span class="sxs-lookup"><span data-stu-id="29b69-277">Button class</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx)
- [<span data-ttu-id="29b69-278">Optionsfelder</span><span class="sxs-lookup"><span data-stu-id="29b69-278">Radio buttons</span></span>](radio-button.md)
- [<span data-ttu-id="29b69-279">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="29b69-279">Check boxes</span></span>](checkbox.md)
- [<span data-ttu-id="29b69-280">Umschalter</span><span class="sxs-lookup"><span data-stu-id="29b69-280">Toggle switches</span></span>](toggles.md)
