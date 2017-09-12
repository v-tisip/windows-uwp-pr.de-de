---
author: Jwmsft
Description: Bei einem Kennwortfeld handelt es sich um ein Texteingabefeld, das die darin eingegebenen Zeichen zu Datenschutzzwecken verdeckt.
title: "Richtlinien für Kennwortfelder"
ms.assetid: 332B04D6-4FFE-42A4-8B3D-ABE8266C7C18
dev.assetid: 4BFDECC6-9BC5-4FF5-8C63-BB36F6DDF2EF
label: Password box
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: miguelrb
design-contact: ksulliv
doc-status: Published
ms.openlocfilehash: 742d72d1d62cdb1bc2cd0397589d167cd6d3cfe2
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="password-box"></a><span data-ttu-id="1297e-104">Kennwortfeld</span><span class="sxs-lookup"><span data-stu-id="1297e-104">Password box</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="1297e-105">Bei einem Kennwortfeld handelt es sich um ein Texteingabefeld, das die darin eingegebenen Zeichen zu Datenschutzzwecken verdeckt.</span><span class="sxs-lookup"><span data-stu-id="1297e-105">A password box is a text input box that conceals the characters typed into it for the purpose of privacy.</span></span> <span data-ttu-id="1297e-106">Ein Kennwortfeld sieht wie eine Textfeld aus. Die einzige Ausnahme besteht darin, dass anstelle des eingegebenen Texts Platzhalterzeichen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1297e-106">A password box looks like a text box, except that it renders placeholder characters in place of the text that has been entered.</span></span> <span data-ttu-id="1297e-107">Sie können das Platzhalterzeichen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="1297e-107">You can configure the placeholder character.</span></span>

> <span data-ttu-id="1297e-108">**Wichtige APIs**: [PasswordBox-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.aspx), [Kennworteigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.password.aspx), [PasswordChar-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchar.aspx), [PasswordRevealMode-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordrevealmode.aspx), [PasswordChanged-Ereignis](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchanged.aspx)</span><span class="sxs-lookup"><span data-stu-id="1297e-108">**Important APIs**: [PasswordBox class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.aspx), [Password property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.password.aspx), [PasswordChar property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchar.aspx), [PasswordRevealMode property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordrevealmode.aspx), [PasswordChanged event](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchanged.aspx)</span></span>

<span data-ttu-id="1297e-109">Standardmäßig ermöglicht das Kennwortfeld dem Benutzer, durch Gedrückthalten einer Schaltfläche zum Anzeigen des Kennworts sein Kennwort anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1297e-109">By default, the password box provides a way for the user to view their password by holding down a reveal button.</span></span> <span data-ttu-id="1297e-110">Sie können die Schaltfläche zum Anzeigen des Kennworts deaktivieren oder einen alternativen Mechanismus zum Anzeigen des Kennworts, z. B. ein Kontrollkästchen, bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1297e-110">You can disable the reveal button, or provide an alternate mechanism to reveal the password, such as a check box.</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="1297e-111">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="1297e-111">Is this the right control?</span></span>

<span data-ttu-id="1297e-112">Verwenden Sie ein **PasswordBox**-Steuerelement, um Kennwörter oder andere private Daten wie Sozialversicherungsnummern zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="1297e-112">Use a **PasswordBox** control to collect a password or other private data, such as a Social Security number.</span></span>

<span data-ttu-id="1297e-113">Weitere Informationen zur Auswahl des passenden Textsteuerelements finden Sie im Artikel über [Textsteuerelemente](text-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1297e-113">For more info about choosing the right text control, see the [Text controls](text-controls.md) article.</span></span>

## <a name="examples"></a><span data-ttu-id="1297e-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1297e-114">Examples</span></span>

<span data-ttu-id="1297e-115">Das Kennwortfeld verfügt über mehrere Zustände, wichtig sind insbesondere die folgenden.</span><span class="sxs-lookup"><span data-stu-id="1297e-115">The password box has several states, including these notable ones.</span></span>

<span data-ttu-id="1297e-116">Bei Inaktivität kann zu einem Kennwortfeld Hinweistext angezeigt werden, um dem Benutzer seinen Zweck mitzuteilen:</span><span class="sxs-lookup"><span data-stu-id="1297e-116">A password box at rest can show hint text so that the user knows its purpose:</span></span>

![Kennwortfeld im Ruhezustand mit Hinweistext](images/passwordbox-rest-hinttext.png)

<span data-ttu-id="1297e-118">Wenn der Benutzer Zeichen in ein Kennwortfeld eingibt, werden standardmäßig Aufzählungszeichen angezeigt, die den eingegebenen Text verbergen:</span><span class="sxs-lookup"><span data-stu-id="1297e-118">When the user types in a password box, the default behavior is to show bullets that hide the text being entered:</span></span>

![Kennwortfeld im Fokuszustand bei Texteingabe](images/passwordbox-focus-typing.png)

<span data-ttu-id="1297e-120">Durch Drücken der Schaltfläche zur Offenlegung des Kennworts auf der rechten Seite wird das eingegebene Kennwort angezeigt:</span><span class="sxs-lookup"><span data-stu-id="1297e-120">Pressing the "reveal" button on the right gives a peek at the password text being entered:</span></span>

![Kennwortfeld mit angezeigtem Text](images/passwordbox-text-reveal.png)

## <a name="create-a-password-box"></a><span data-ttu-id="1297e-122">Erstellen eines Kennwortfelds</span><span class="sxs-lookup"><span data-stu-id="1297e-122">Create a password box</span></span>

<span data-ttu-id="1297e-123">Verwenden Sie die [Password](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.password.aspx)-Eigenschaft, um den Inhalt des Kennwortfelds abzurufen oder festzulegen.</span><span class="sxs-lookup"><span data-stu-id="1297e-123">Use the [Password](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.password.aspx) property to get or set the contents of the PasswordBox.</span></span> <span data-ttu-id="1297e-124">Dies kann im Handler für das [PasswordChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchanged.aspx)-Ereignis erfolgen, um die Überprüfung durchzuführen, während der Benutzer das Kennwort eingibt.</span><span class="sxs-lookup"><span data-stu-id="1297e-124">You can do this in the handler for the [PasswordChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchanged.aspx) event to perform validation while the user enters the password.</span></span> <span data-ttu-id="1297e-125">Oder Sie können ein weiteres Ereignis, z. B. ein [Click](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)-Ereignis der Schaltfläche, verwenden, um die Überprüfung durchzuführen, nachdem der Benutzer die Texteingabe abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="1297e-125">Or, you can use another event, like a button [Click](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.buttonbase.click.aspx), to perform validation after the user completes the text entry.</span></span>

<span data-ttu-id="1297e-126">Dieser XAML-Code für ein Kennwortfeld-Steuerelement zeigt das Standardaussehen des Kennwortfelds.</span><span class="sxs-lookup"><span data-stu-id="1297e-126">Here's the XAML for a password box control that demonstrates the default look of the PasswordBox.</span></span> <span data-ttu-id="1297e-127">Wenn der Benutzer ein Kennwort eingibt, wird überprüft, ob es dem Literalwert „Password“ entspricht.</span><span class="sxs-lookup"><span data-stu-id="1297e-127">When the user enters a password, you check to see if it's the literal value, "Password".</span></span> <span data-ttu-id="1297e-128">In diesem Fall wird dem Benutzer eine Meldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1297e-128">If it is, you display a message to the user.</span></span>

```xaml
<StackPanel>  
  <PasswordBox x:Name="passwordBox" Width="200" MaxLength="16"
             PasswordChanged="passwordBox_PasswordChanged"/>

  <TextBlock x:Name="statusText" Margin="10" HorizontalAlignment="Center" />
</StackPanel>   
```

```csharp
private void passwordBox_PasswordChanged(object sender, RoutedEventArgs e)
{
    if (passwordBox.Password == "Password")
    {
        statusText.Text = "'Password' is not allowed as a password.";
    }
    else
    {
        statusText.Text = string.Empty;
    }
}
```
<span data-ttu-id="1297e-129">Dies ist das Ergebnis, wenn der Code ausgeführt und als Kennwort „Password“ eingegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1297e-129">Here's the result when this code runs and the user enters "Password".</span></span>

![Kennwortfeld mit Überprüfungshinweis](images/passwordbox-revealed-validation.png)

### <a name="password-character"></a><span data-ttu-id="1297e-131">Kennwortzeichen</span><span class="sxs-lookup"><span data-stu-id="1297e-131">Password character</span></span>

<span data-ttu-id="1297e-132">Durch Festlegen der [PasswordChar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchar.aspx)-Eigenschaft können Sie das zum Maskieren des Kennworts verwendete Zeichen ändern.</span><span class="sxs-lookup"><span data-stu-id="1297e-132">You can change the character used to mask the password by setting the [PasswordChar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchar.aspx) property.</span></span> <span data-ttu-id="1297e-133">Hier wird das standardmäßige Aufzählungszeichen durch ein Sternchen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="1297e-133">Here, the default bullet is replaced with an asterisk.</span></span>

```xaml
<PasswordBox x:Name="passwordBox" Width="200" PasswordChar="*"/>
```

<span data-ttu-id="1297e-134">Das Ergebnis sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="1297e-134">The result looks like this.</span></span>

![Kennwortfeld mit einem benutzerdefinierten Maskierungszeichen](images/passwordbox-custom-char.png)

### <a name="headers-and-placeholder-text"></a><span data-ttu-id="1297e-136">Kopf- und Platzhaltertext</span><span class="sxs-lookup"><span data-stu-id="1297e-136">Headers and placeholder text</span></span>

<span data-ttu-id="1297e-137">Mit den Eigenschaften [Header](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.header.aspx) und [PlaceholderText](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.placeholdertext.aspx) können Sie den Kontext für das Kennwortfeld angeben.</span><span class="sxs-lookup"><span data-stu-id="1297e-137">You can use the [Header](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.header.aspx) and [PlaceholderText](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.placeholdertext.aspx) properties to provide context for the PasswordBox.</span></span> <span data-ttu-id="1297e-138">Dies ist besonders hilfreich, wenn mehrere Felder vorhanden sind, z. B. in einem Formular zum Ändern des Kennworts.</span><span class="sxs-lookup"><span data-stu-id="1297e-138">This is especially useful when you have multiple boxes, such as on a form to change a password.</span></span>

```xaml
<PasswordBox x:Name="passwordBox" Width="200" Header="Password" PlaceholderText="Enter your password"/>
```

![Kennwortfeld im Ruhezustand mit Hinweistext](images/passwordbox-rest-hinttext.png)

### <a name="maximum-length"></a><span data-ttu-id="1297e-140">Maximale Länge</span><span class="sxs-lookup"><span data-stu-id="1297e-140">Maximum length</span></span>

<span data-ttu-id="1297e-141">Geben Sie die maximale Anzahl von Zeichen an, die der Benutzer eingeben darf, indem Sie die [MaxLength](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.maxlength.aspx)-Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="1297e-141">Specify the maximum number of characters that the user can enter by setting the [MaxLength](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.maxlength.aspx) property.</span></span> <span data-ttu-id="1297e-142">Es gibt keine Eigenschaft zum Festlegen einer Mindestlänge. Sie können jedoch im App-Code die Kennwortlänge überprüfen und weitere Überprüfungen durchführen.</span><span class="sxs-lookup"><span data-stu-id="1297e-142">There is no property to specify a minimum length, but you can check the password length, and perform any other validation, in your app code.</span></span>

## <a name="password-reveal-mode"></a><span data-ttu-id="1297e-143">Kennwortanzeigemodus</span><span class="sxs-lookup"><span data-stu-id="1297e-143">Password reveal mode</span></span>

<span data-ttu-id="1297e-144">Das Kennwortfeld verfügt über eine integrierte Schaltfläche, mit der Benutzer das eingegebene Kennwort anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="1297e-144">The PasswordBox has a built-in button that the user can press to display the password text.</span></span> <span data-ttu-id="1297e-145">Hier ist das Ergebnis der Benutzeraktion.</span><span class="sxs-lookup"><span data-stu-id="1297e-145">Here's the result of the user's action.</span></span> <span data-ttu-id="1297e-146">Lässt der Benutzer die Schaltfläche los, wird das Kennwort automatisch wieder ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="1297e-146">When the user releases it, the password is automatically hidden again.</span></span>

![Kennwortfeld mit angezeigtem Text](images/passwordbox-text-reveal.png)

### <a name="peek-mode"></a><span data-ttu-id="1297e-148">Vorschaumodus</span><span class="sxs-lookup"><span data-stu-id="1297e-148">Peek mode</span></span>

<span data-ttu-id="1297e-149">Standardmäßig wird die Schaltfläche zum Anzeigen des Kennworts (oder die Vorschau-Schaltfläche) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1297e-149">By default, the password reveal button (or "peek" button) is shown.</span></span> <span data-ttu-id="1297e-150">Der Benutzer muss die Schaltfläche gedrückt halten, um das Kennwort anzuzeigen, sodass ein hohes Maß an Sicherheit gewährleistet ist.</span><span class="sxs-lookup"><span data-stu-id="1297e-150">The user must continuously press the button to view the password, so that a high level of security is maintained.</span></span>

<span data-ttu-id="1297e-151">Der Wert der [PasswordRevealMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordrevealmode.aspx)-Eigenschaft ist nicht der einzige Faktor, der bestimmt, ob eine Schaltfläche zum Anzeigen des Kennworts für den Benutzer sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="1297e-151">The value of the [PasswordRevealMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordrevealmode.aspx) property is not the only factor that determines whether a password reveal button is visible to the user.</span></span> <span data-ttu-id="1297e-152">Weitere Faktoren sind, ob das Steuerelement mit einer größeren Breite als der Mindestbreite angezeigt wird, ob das Kennwortfeld den Fokus hat und ob das Texteingabefeld mindestens ein Zeichen enthält.</span><span class="sxs-lookup"><span data-stu-id="1297e-152">Other factors include whether the control is displayed above a minimum width, whether the PasswordBox has focus, and whether the text entry field contains at least one character.</span></span> <span data-ttu-id="1297e-153">Die Schaltfläche zum Anzeigen des Kennworts wird nur angezeigt, wenn das Kennwortfeld zum ersten Mal den Fokus erhält und ein Zeichen eingegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1297e-153">The password reveal button is shown only when the PasswordBox receives focus for the first time and a character is entered.</span></span> <span data-ttu-id="1297e-154">Wenn PasswordBox den Fokus verliert und ihn anschließend wieder erhält, wird die Schaltfläche zum Anzeigen des Kennworts nicht angezeigt, es sei denn, das Kennwort wird gelöscht und die Zeichen werden erneut eingegeben.</span><span class="sxs-lookup"><span data-stu-id="1297e-154">If the PasswordBox loses focus and then regains focus, the reveal button is not shown again unless the password is cleared and character entry starts over.</span></span>

> <span data-ttu-id="1297e-155">**Achtung**&nbsp;&nbsp;Vor Windows 10 wurde die Schaltfläche zum Anzeigen des Kennworts nicht standardmäßig angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1297e-155">**Caution**&nbsp;&nbsp;Prior to Windows 10, the password reveal button was not shown by default.</span></span> <span data-ttu-id="1297e-156">Wenn die Sicherheit Ihrer App erfordert, dass das Kennwort immer verdeckt ist, muss „PasswordRevealMode“ auf „Hidden“ festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="1297e-156">If the security of your app requires that the password is always obscured, be sure to set PasswordRevealMode to Hidden.</span></span>

### <a name="hidden-and-visible-modes"></a><span data-ttu-id="1297e-157">Ausblendungs- und Anzeigemodus</span><span class="sxs-lookup"><span data-stu-id="1297e-157">Hidden and Visible modes</span></span>

<span data-ttu-id="1297e-158">Mit den weiteren [PasswordRevealMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordrevealmode.aspx)-Aufzählungswerten **Hidden** und **Visible** blenden Sie die Schaltfläche zum Anzeigen des Kennworts aus. Sie können programmgesteuert festlegen, ob das Kennwort verdeckt wird.</span><span class="sxs-lookup"><span data-stu-id="1297e-158">The other [PasswordRevealMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordrevealmode.aspx) enumeration values, **Hidden** and **Visible**, hide the password reveal button and let you programmatically manage whether the password is obscured.</span></span>

<span data-ttu-id="1297e-159">Um das Kennwort immer zu verdecken, legen Sie „PasswordRevealMode“ auf „Hide“ fest.</span><span class="sxs-lookup"><span data-stu-id="1297e-159">To always obscure the password, set PasswordRevealMode to Hidden.</span></span> <span data-ttu-id="1297e-160">Wenn das Kennwort nicht immer verdeckt sein muss, können Sie eine benutzerdefinierte Benutzeroberfläche bereitstellen, die dem Benutzer das Umschalten von „PasswordRevealMode“ zwischen „Hidden“ and „Visible“ ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="1297e-160">Unless you need the password to be always obscured, you can provide a custom UI to let the user toggle the PasswordRevealMode between Hidden and Visible.</span></span>

<span data-ttu-id="1297e-161">In früheren Versionen von Windows Phone wurde für das Kennwortfeld eine Kontrollkästchen verwendet, um zwischen Anzeigen und Verdecken des Kennworts umzuschalten.</span><span class="sxs-lookup"><span data-stu-id="1297e-161">In previous versions of Windows Phone, PasswordBox used a check box to toggle whether the password was obscured.</span></span> <span data-ttu-id="1297e-162">Sie können eine ähnliche Benutzeroberfläche für Ihre App erstellen, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="1297e-162">You can create a similar UI for your app, as shown in the following example.</span></span> <span data-ttu-id="1297e-163">Sie können auch andere Steuerelemente wie [ToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.togglebutton.aspx) verwenden, damit der Benutzer zwischen den Modi wechseln kann.</span><span class="sxs-lookup"><span data-stu-id="1297e-163">You can also use other controls, like [ToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.togglebutton.aspx), to let the user switch modes.</span></span>

<span data-ttu-id="1297e-164">In diesem Beispiel wird gezeigt, wie Sie mit einem [CheckBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.checkbox.aspx)-Steuerelement dem Benutzer das Wechseln des Anzeigemodus eines Kennwortfelds ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="1297e-164">This example shows how to use a [CheckBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.checkbox.aspx) to let a user switch the reveal mode of a PasswordBox.</span></span>

```xaml
<StackPanel Width="200">
    <PasswordBox Name="passwordBox1"
                 PasswordRevealMode="Hidden"/>
    <CheckBox Name="revealModeCheckBox" Content="Show password"
              IsChecked="False"
              Checked="CheckBox_Changed" Unchecked="CheckBox_Changed"/>
</StackPanel>
```

```csharp
private void CheckBox_Changed(object sender, RoutedEventArgs e)
{
    if (revealModeCheckBox.IsChecked == true)
    {
        passwordBox1.PasswordRevealMode = PasswordRevealMode.Visible;
    }
    else
    {
        passwordBox1.PasswordRevealMode = PasswordRevealMode.Hidden;
    }
}
```

<span data-ttu-id="1297e-165">Dieses Kennwortfeld sieht in etwa so aus.</span><span class="sxs-lookup"><span data-stu-id="1297e-165">This PasswordBox looks like this.</span></span>

![Kennwortfeld mit einer benutzerdefinierten Schaltfläche zum Anzeigen des Kennworts](images/passwordbox-custom-reveal.png)

## <a name="choose-the-right-keyboard-for-your-text-control"></a><span data-ttu-id="1297e-167">Auswählen der richtigen Tastatur für Ihr Textsteuerelement</span><span class="sxs-lookup"><span data-stu-id="1297e-167">Choose the right keyboard for your text control</span></span>

<span data-ttu-id="1297e-168">Um Benutzern die Eingabe von Daten mit der Bildschirmtastatur oder dem Soft Input Panel (SIP) zu erleichtern, können Sie den Eingabeumfang des Textsteuerelements an die Art der Daten anpassen, die der Benutzer vermutlich eingeben wird.</span><span class="sxs-lookup"><span data-stu-id="1297e-168">To help users to enter data using the touch keyboard, or Soft Input Panel (SIP), you can set the input scope of the text control to match the kind of data the user is expected to enter.</span></span> <span data-ttu-id="1297e-169">Das Kennwortfeld unterstützt nur die Eingabeumfangwerte **Password** und **NumericPin**.</span><span class="sxs-lookup"><span data-stu-id="1297e-169">PasswordBox supports only the **Password** and **NumericPin** input scope values.</span></span> <span data-ttu-id="1297e-170">Andere Werte werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="1297e-170">Any other value is ignored.</span></span>

<span data-ttu-id="1297e-171">Weitere Informationen zur Verwendung von Eingabeumfängen finden Sie unter [Verwenden des Eingabeumfangs zum Ändern der Bildschirmtastatur](https://msdn.microsoft.com/library/windows/apps/mt280229).</span><span class="sxs-lookup"><span data-stu-id="1297e-171">For more info about how to use input scopes, see [Use input scope to change the touch keyboard](https://msdn.microsoft.com/library/windows/apps/mt280229).</span></span>

## <a name="recommendations"></a><span data-ttu-id="1297e-172">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="1297e-172">Recommendations</span></span>

-   <span data-ttu-id="1297e-173">Verwenden Sie eine Beschriftung oder Platzhaltertext, wenn der Zweck des Kennwortfelds nicht eindeutig ist.</span><span class="sxs-lookup"><span data-stu-id="1297e-173">Use a label or placeholder text if the purpose of the password box isn't clear.</span></span> <span data-ttu-id="1297e-174">Eine Beschriftung ist sichtbar, unabhängig davon, ob das Texteingabefeld über einen Wert verfügt.</span><span class="sxs-lookup"><span data-stu-id="1297e-174">A label is visible whether or not the text input box has a value.</span></span> <span data-ttu-id="1297e-175">Platzhaltertext wird im Texteingabefeld angezeigt und wird erst ausgeblendet, wenn der Benutzer einen Wert eingibt.</span><span class="sxs-lookup"><span data-stu-id="1297e-175">Placeholder text is displayed inside the text input box and disappears once a value has been entered.</span></span>
-   <span data-ttu-id="1297e-176">Weisen Sie dem Kennwortfeld eine entsprechende Breite für den Bereich der Werte zu, die eingegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="1297e-176">Give the password box an appropriate width for the range of values that can be entered.</span></span> <span data-ttu-id="1297e-177">Die Wortlänge variiert zwischen den einzelnen Sprachen. Sie sollten also die Lokalisierung berücksichtigen, wenn Ihre App global verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="1297e-177">Word length varies between languages, so take localization into account if you want your app to be world-ready.</span></span>
-   <span data-ttu-id="1297e-178">Platzieren Sie kein anderes Steuerelement neben einem Eingabefeld für Kennwörter.</span><span class="sxs-lookup"><span data-stu-id="1297e-178">Don't put another control right next to a password input box.</span></span> <span data-ttu-id="1297e-179">Das Kennwortfeld weist eine Schaltfläche zum Anzeigen des Kennworts auf, damit Benutzer die eingegebenen Kennwörter überprüfen können. Wenn ein anderes Steuerelement direkt daneben vorhanden ist, zeigen Benutzer möglicherweise versehentlich ihre Kennwörter an, wenn sie versuchen, mit dem anderen Steuerelement zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="1297e-179">The password box has a password reveal button for users to verify the passwords they have typed, and having another control right next to it might make users accidentally reveal their passwords when they try to interact with the other control.</span></span> <span data-ttu-id="1297e-180">Um dies zu verhindern, achten Sie auf einen gewissen Abstand zwischen dem Eingabefeld für Kennwörter und dem anderen Steuerelement. Sie können das andere Steuerelement auch in der nächsten Zeile platzieren.</span><span class="sxs-lookup"><span data-stu-id="1297e-180">To prevent this from happening, put some spacing between the password in put box and the other control, or put the other control on the next line.</span></span>
-   <span data-ttu-id="1297e-181">Ziehen Sie für die Kontenerstellung die Anzeige von zwei Kennwortfeldern in Erwägung: eins für das neue Kennwort und ein zweites zum Bestätigen des neuen Kennworts.</span><span class="sxs-lookup"><span data-stu-id="1297e-181">Consider presenting two password boxes for account creation: one for the new password, and a second to confirm the new password.</span></span>
-   <span data-ttu-id="1297e-182">Zeigen Sie für Benutzernamen nur ein einzelnes Kennwortfeld an.</span><span class="sxs-lookup"><span data-stu-id="1297e-182">Only show a single password box for logins.</span></span>
-   <span data-ttu-id="1297e-183">Wenn ein Kennwortfeld zur PIN-Eingabe verwendet wird, sollten Sie möglicherweise statt einer Bestätigungsschaltfläche eine sofortige Reaktion nach der Eingabe der letzten Zahl vorsehen.</span><span class="sxs-lookup"><span data-stu-id="1297e-183">When a password box is used to enter a PIN, consider providing an instant response as soon as the last number is entered instead of using a confirmation button.</span></span>



## <a name="related-articles"></a><span data-ttu-id="1297e-184">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="1297e-184">Related articles</span></span>

[<span data-ttu-id="1297e-185">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="1297e-185">Text controls</span></span>](text-controls.md)

- [<span data-ttu-id="1297e-186">Richtlinien für die Rechtschreibprüfung</span><span class="sxs-lookup"><span data-stu-id="1297e-186">Guidelines for spell checking</span></span>](spell-checking-and-prediction.md)
- [<span data-ttu-id="1297e-187">Hinzufügen von Suchfunktionen</span><span class="sxs-lookup"><span data-stu-id="1297e-187">Adding search</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465231)
- [<span data-ttu-id="1297e-188">Richtlinien für die Texteingabe</span><span class="sxs-lookup"><span data-stu-id="1297e-188">Guidelines for text input</span></span>](text-controls.md)
- [<span data-ttu-id="1297e-189">TextBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="1297e-189">TextBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209683)
- [<span data-ttu-id="1297e-190">Windows.UI.Xaml.Controls PasswordBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="1297e-190">Windows.UI.Xaml.Controls PasswordBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227519)
- [<span data-ttu-id="1297e-191">StringLength-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="1297e-191">String.Length property</span></span>](https://msdn.microsoft.com/library/system.string.length(v=vs.110).aspx)
