---
Description: A password box is a text input box that conceals the characters typed into it for the purpose of privacy.
title: Richtlinien für Kennwortfelder
ms.assetid: 332B04D6-4FFE-42A4-8B3D-ABE8266C7C18
dev.assetid: 4BFDECC6-9BC5-4FF5-8C63-BB36F6DDF2EF
label: Password box
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
pm-contact: miguelrb
design-contact: ksulliv
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 981fc39cf724e4153dba18d6d23a0e8607f83fc8
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8793613"
---
# <a name="password-box"></a><span data-ttu-id="e553e-103">Kennwortfeld</span><span class="sxs-lookup"><span data-stu-id="e553e-103">Password box</span></span>

 

<span data-ttu-id="e553e-104">Bei einem Kennwortfeld handelt es sich um ein Texteingabefeld, das die darin eingegebenen Zeichen zu Datenschutzzwecken verdeckt.</span><span class="sxs-lookup"><span data-stu-id="e553e-104">A password box is a text input box that conceals the characters typed into it for the purpose of privacy.</span></span> <span data-ttu-id="e553e-105">Ein Kennwortfeld sieht wie eine Textfeld aus. Die einzige Ausnahme besteht darin, dass anstelle des eingegebenen Texts Platzhalterzeichen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e553e-105">A password box looks like a text box, except that it renders placeholder characters in place of the text that has been entered.</span></span> <span data-ttu-id="e553e-106">Sie können das Platzhalterzeichen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e553e-106">You can configure the placeholder character.</span></span>

> <span data-ttu-id="e553e-107">**Wichtige APIs**: [PasswordBox-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.aspx), [Kennworteigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.password.aspx), [PasswordChar-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchar.aspx), [PasswordRevealMode-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordrevealmode.aspx), [PasswordChanged-Ereignis](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchanged.aspx)</span><span class="sxs-lookup"><span data-stu-id="e553e-107">**Important APIs**: [PasswordBox class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.aspx), [Password property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.password.aspx), [PasswordChar property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchar.aspx), [PasswordRevealMode property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordrevealmode.aspx), [PasswordChanged event](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchanged.aspx)</span></span>

<span data-ttu-id="e553e-108">Standardmäßig ermöglicht das Kennwortfeld dem Benutzer, durch Gedrückthalten einer Schaltfläche zum Anzeigen des Kennworts sein Kennwort anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e553e-108">By default, the password box provides a way for the user to view their password by holding down a reveal button.</span></span> <span data-ttu-id="e553e-109">Sie können die Schaltfläche zum Anzeigen des Kennworts deaktivieren oder einen alternativen Mechanismus zum Anzeigen des Kennworts, z. B. ein Kontrollkästchen, bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e553e-109">You can disable the reveal button, or provide an alternate mechanism to reveal the password, such as a check box.</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="e553e-110">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="e553e-110">Is this the right control?</span></span>

<span data-ttu-id="e553e-111">Verwenden Sie ein **PasswordBox**-Steuerelement, um Kennwörter oder andere private Daten wie Sozialversicherungsnummern zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="e553e-111">Use a **PasswordBox** control to collect a password or other private data, such as a Social Security number.</span></span>

<span data-ttu-id="e553e-112">Weitere Informationen zur Auswahl des passenden Textsteuerelements finden Sie im Artikel über [Textsteuerelemente](text-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e553e-112">For more info about choosing the right text control, see the [Text controls](text-controls.md) article.</span></span>

## <a name="examples"></a><span data-ttu-id="e553e-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="e553e-113">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="e553e-114">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="e553e-114">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="e553e-115">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/PasswordBox">die App zu öffnen und PasswordBox in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="e553e-115">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/PasswordBox">open the app and see the PasswordBox in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="e553e-116">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="e553e-116">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="e553e-117">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="e553e-117">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="e553e-118">Das Kennwortfeld verfügt über mehrere Zustände, wichtig sind insbesondere die folgenden.</span><span class="sxs-lookup"><span data-stu-id="e553e-118">The password box has several states, including these notable ones.</span></span>

<span data-ttu-id="e553e-119">Bei Inaktivität kann zu einem Kennwortfeld Hinweistext angezeigt werden, um dem Benutzer seinen Zweck mitzuteilen:</span><span class="sxs-lookup"><span data-stu-id="e553e-119">A password box at rest can show hint text so that the user knows its purpose:</span></span>

![Kennwortfeld im Ruhezustand mit Hinweistext](images/passwordbox-rest-hinttext.png)

<span data-ttu-id="e553e-121">Wenn der Benutzer Zeichen in ein Kennwortfeld eingibt, werden standardmäßig Aufzählungszeichen angezeigt, die den eingegebenen Text verbergen:</span><span class="sxs-lookup"><span data-stu-id="e553e-121">When the user types in a password box, the default behavior is to show bullets that hide the text being entered:</span></span>

![Kennwortfeld im Fokuszustand bei Texteingabe](images/passwordbox-focus-typing.png)

<span data-ttu-id="e553e-123">Durch Drücken der Schaltfläche zur Offenlegung des Kennworts auf der rechten Seite wird das eingegebene Kennwort angezeigt:</span><span class="sxs-lookup"><span data-stu-id="e553e-123">Pressing the "reveal" button on the right gives a peek at the password text being entered:</span></span>

![Kennwortfeld mit angezeigtem Text](images/passwordbox-text-reveal.png)

## <a name="create-a-password-box"></a><span data-ttu-id="e553e-125">Erstellen eines Kennwortfelds</span><span class="sxs-lookup"><span data-stu-id="e553e-125">Create a password box</span></span>

<span data-ttu-id="e553e-126">Verwenden Sie die [Password](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.password.aspx)-Eigenschaft, um den Inhalt des Kennwortfelds abzurufen oder festzulegen.</span><span class="sxs-lookup"><span data-stu-id="e553e-126">Use the [Password](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.password.aspx) property to get or set the contents of the PasswordBox.</span></span> <span data-ttu-id="e553e-127">Dies kann im Handler für das [PasswordChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchanged.aspx)-Ereignis erfolgen, um die Überprüfung durchzuführen, während der Benutzer das Kennwort eingibt.</span><span class="sxs-lookup"><span data-stu-id="e553e-127">You can do this in the handler for the [PasswordChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchanged.aspx) event to perform validation while the user enters the password.</span></span> <span data-ttu-id="e553e-128">Oder Sie können ein weiteres Ereignis, z. B. ein [Click](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)-Ereignis der Schaltfläche, verwenden, um die Überprüfung durchzuführen, nachdem der Benutzer die Texteingabe abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="e553e-128">Or, you can use another event, like a button [Click](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.buttonbase.click.aspx), to perform validation after the user completes the text entry.</span></span>

<span data-ttu-id="e553e-129">Dieser XAML-Code für ein Kennwortfeld-Steuerelement zeigt das Standardaussehen des Kennwortfelds.</span><span class="sxs-lookup"><span data-stu-id="e553e-129">Here's the XAML for a password box control that demonstrates the default look of the PasswordBox.</span></span> <span data-ttu-id="e553e-130">Wenn der Benutzer ein Kennwort eingibt, wird überprüft, ob es dem Literalwert „Password“ entspricht.</span><span class="sxs-lookup"><span data-stu-id="e553e-130">When the user enters a password, you check to see if it's the literal value, "Password".</span></span> <span data-ttu-id="e553e-131">In diesem Fall wird dem Benutzer eine Meldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e553e-131">If it is, you display a message to the user.</span></span>

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
<span data-ttu-id="e553e-132">Dies ist das Ergebnis, wenn der Code ausgeführt und als Kennwort „Password“ eingegeben wird.</span><span class="sxs-lookup"><span data-stu-id="e553e-132">Here's the result when this code runs and the user enters "Password".</span></span>

![Kennwortfeld mit Überprüfungshinweis](images/passwordbox-revealed-validation.png)

### <a name="password-character"></a><span data-ttu-id="e553e-134">Kennwortzeichen</span><span class="sxs-lookup"><span data-stu-id="e553e-134">Password character</span></span>

<span data-ttu-id="e553e-135">Durch Festlegen der [PasswordChar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchar.aspx)-Eigenschaft können Sie das zum Maskieren des Kennworts verwendete Zeichen ändern.</span><span class="sxs-lookup"><span data-stu-id="e553e-135">You can change the character used to mask the password by setting the [PasswordChar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordchar.aspx) property.</span></span> <span data-ttu-id="e553e-136">Hier wird das standardmäßige Aufzählungszeichen durch ein Sternchen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="e553e-136">Here, the default bullet is replaced with an asterisk.</span></span>

```xaml
<PasswordBox x:Name="passwordBox" Width="200" PasswordChar="*"/>
```

<span data-ttu-id="e553e-137">Das Ergebnis sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="e553e-137">The result looks like this.</span></span>

![Kennwortfeld mit einem benutzerdefinierten Maskierungszeichen](images/passwordbox-custom-char.png)

### <a name="headers-and-placeholder-text"></a><span data-ttu-id="e553e-139">Kopf- und Platzhaltertext</span><span class="sxs-lookup"><span data-stu-id="e553e-139">Headers and placeholder text</span></span>

<span data-ttu-id="e553e-140">Mit den Eigenschaften [Header](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.header.aspx) und [PlaceholderText](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.placeholdertext.aspx) können Sie den Kontext für das Kennwortfeld angeben.</span><span class="sxs-lookup"><span data-stu-id="e553e-140">You can use the [Header](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.header.aspx) and [PlaceholderText](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.placeholdertext.aspx) properties to provide context for the PasswordBox.</span></span> <span data-ttu-id="e553e-141">Dies ist besonders hilfreich, wenn mehrere Felder vorhanden sind, z. B. in einem Formular zum Ändern des Kennworts.</span><span class="sxs-lookup"><span data-stu-id="e553e-141">This is especially useful when you have multiple boxes, such as on a form to change a password.</span></span>

```xaml
<PasswordBox x:Name="passwordBox" Width="200" Header="Password" PlaceholderText="Enter your password"/>
```

![Kennwortfeld im Ruhezustand mit Hinweistext](images/passwordbox-rest-hinttext.png)

### <a name="maximum-length"></a><span data-ttu-id="e553e-143">Maximale Länge</span><span class="sxs-lookup"><span data-stu-id="e553e-143">Maximum length</span></span>

<span data-ttu-id="e553e-144">Geben Sie die maximale Anzahl von Zeichen an, die der Benutzer eingeben darf, indem Sie die [MaxLength](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.maxlength.aspx)-Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="e553e-144">Specify the maximum number of characters that the user can enter by setting the [MaxLength](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.maxlength.aspx) property.</span></span> <span data-ttu-id="e553e-145">Es gibt keine Eigenschaft zum Festlegen einer Mindestlänge. Sie können jedoch im App-Code die Kennwortlänge überprüfen und weitere Überprüfungen durchführen.</span><span class="sxs-lookup"><span data-stu-id="e553e-145">There is no property to specify a minimum length, but you can check the password length, and perform any other validation, in your app code.</span></span>

## <a name="password-reveal-mode"></a><span data-ttu-id="e553e-146">Kennwortanzeigemodus</span><span class="sxs-lookup"><span data-stu-id="e553e-146">Password reveal mode</span></span>

<span data-ttu-id="e553e-147">Das Kennwortfeld verfügt über eine integrierte Schaltfläche, mit der Benutzer das eingegebene Kennwort anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="e553e-147">The PasswordBox has a built-in button that the user can press to display the password text.</span></span> <span data-ttu-id="e553e-148">Hier ist das Ergebnis der Benutzeraktion.</span><span class="sxs-lookup"><span data-stu-id="e553e-148">Here's the result of the user's action.</span></span> <span data-ttu-id="e553e-149">Lässt der Benutzer die Schaltfläche los, wird das Kennwort automatisch wieder ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="e553e-149">When the user releases it, the password is automatically hidden again.</span></span>

![Kennwortfeld mit angezeigtem Text](images/passwordbox-text-reveal.png)

### <a name="peek-mode"></a><span data-ttu-id="e553e-151">Vorschaumodus</span><span class="sxs-lookup"><span data-stu-id="e553e-151">Peek mode</span></span>

<span data-ttu-id="e553e-152">Standardmäßig wird die Schaltfläche zum Anzeigen des Kennworts (oder die Vorschau-Schaltfläche) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e553e-152">By default, the password reveal button (or "peek" button) is shown.</span></span> <span data-ttu-id="e553e-153">Der Benutzer muss die Schaltfläche gedrückt halten, um das Kennwort anzuzeigen, sodass ein hohes Maß an Sicherheit gewährleistet ist.</span><span class="sxs-lookup"><span data-stu-id="e553e-153">The user must continuously press the button to view the password, so that a high level of security is maintained.</span></span>

<span data-ttu-id="e553e-154">Der Wert der [PasswordRevealMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordrevealmode.aspx)-Eigenschaft ist nicht der einzige Faktor, der bestimmt, ob eine Schaltfläche zum Anzeigen des Kennworts für den Benutzer sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="e553e-154">The value of the [PasswordRevealMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.passwordrevealmode.aspx) property is not the only factor that determines whether a password reveal button is visible to the user.</span></span> <span data-ttu-id="e553e-155">Weitere Faktoren sind, ob das Steuerelement mit einer größeren Breite als der Mindestbreite angezeigt wird, ob das Kennwortfeld den Fokus hat und ob das Texteingabefeld mindestens ein Zeichen enthält.</span><span class="sxs-lookup"><span data-stu-id="e553e-155">Other factors include whether the control is displayed above a minimum width, whether the PasswordBox has focus, and whether the text entry field contains at least one character.</span></span> <span data-ttu-id="e553e-156">Die Schaltfläche zum Anzeigen des Kennworts wird nur angezeigt, wenn das Kennwortfeld zum ersten Mal den Fokus erhält und ein Zeichen eingegeben wird.</span><span class="sxs-lookup"><span data-stu-id="e553e-156">The password reveal button is shown only when the PasswordBox receives focus for the first time and a character is entered.</span></span> <span data-ttu-id="e553e-157">Wenn PasswordBox den Fokus verliert und ihn anschließend wieder erhält, wird die Schaltfläche zum Anzeigen des Kennworts nicht angezeigt, es sei denn, das Kennwort wird gelöscht und die Zeichen werden erneut eingegeben.</span><span class="sxs-lookup"><span data-stu-id="e553e-157">If the PasswordBox loses focus and then regains focus, the reveal button is not shown again unless the password is cleared and character entry starts over.</span></span>

> <span data-ttu-id="e553e-158">**Achtung**&nbsp;&nbsp;Vor Windows 10 wurde die Schaltfläche zum Anzeigen des Kennworts nicht standardmäßig angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e553e-158">**Caution**&nbsp;&nbsp;Prior to Windows 10, the password reveal button was not shown by default.</span></span> <span data-ttu-id="e553e-159">Wenn die Sicherheit Ihrer App erfordert, dass das Kennwort immer verdeckt ist, muss „PasswordRevealMode“ auf „Hidden“ festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="e553e-159">If the security of your app requires that the password is always obscured, be sure to set PasswordRevealMode to Hidden.</span></span>

### <a name="hidden-and-visible-modes"></a><span data-ttu-id="e553e-160">Ausblendungs- und Anzeigemodus</span><span class="sxs-lookup"><span data-stu-id="e553e-160">Hidden and Visible modes</span></span>

<span data-ttu-id="e553e-161">Mit den weiteren [PasswordRevealMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordrevealmode.aspx)-Aufzählungswerten **Hidden** und **Visible** blenden Sie die Schaltfläche zum Anzeigen des Kennworts aus. Sie können programmgesteuert festlegen, ob das Kennwort verdeckt wird.</span><span class="sxs-lookup"><span data-stu-id="e553e-161">The other [PasswordRevealMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordrevealmode.aspx) enumeration values, **Hidden** and **Visible**, hide the password reveal button and let you programmatically manage whether the password is obscured.</span></span>

<span data-ttu-id="e553e-162">Um das Kennwort immer zu verdecken, legen Sie „PasswordRevealMode“ auf „Hide“ fest.</span><span class="sxs-lookup"><span data-stu-id="e553e-162">To always obscure the password, set PasswordRevealMode to Hidden.</span></span> <span data-ttu-id="e553e-163">Wenn das Kennwort nicht immer verdeckt sein muss, können Sie eine benutzerdefinierte Benutzeroberfläche bereitstellen, die dem Benutzer das Umschalten von „PasswordRevealMode“ zwischen „Hidden“ and „Visible“ ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="e553e-163">Unless you need the password to be always obscured, you can provide a custom UI to let the user toggle the PasswordRevealMode between Hidden and Visible.</span></span>

<span data-ttu-id="e553e-164">In früheren Versionen von Windows Phone wurde für das Kennwortfeld eine Kontrollkästchen verwendet, um zwischen Anzeigen und Verdecken des Kennworts umzuschalten.</span><span class="sxs-lookup"><span data-stu-id="e553e-164">In previous versions of Windows Phone, PasswordBox used a check box to toggle whether the password was obscured.</span></span> <span data-ttu-id="e553e-165">Sie können eine ähnliche Benutzeroberfläche für Ihre App erstellen, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e553e-165">You can create a similar UI for your app, as shown in the following example.</span></span> <span data-ttu-id="e553e-166">Sie können auch andere Steuerelemente wie [ToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.togglebutton.aspx) verwenden, damit der Benutzer zwischen den Modi wechseln kann.</span><span class="sxs-lookup"><span data-stu-id="e553e-166">You can also use other controls, like [ToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.togglebutton.aspx), to let the user switch modes.</span></span>

<span data-ttu-id="e553e-167">In diesem Beispiel wird gezeigt, wie Sie mit einem [CheckBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.checkbox.aspx)-Steuerelement dem Benutzer das Wechseln des Anzeigemodus eines Kennwortfelds ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e553e-167">This example shows how to use a [CheckBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.checkbox.aspx) to let a user switch the reveal mode of a PasswordBox.</span></span>

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

<span data-ttu-id="e553e-168">Dieses Kennwortfeld sieht in etwa so aus.</span><span class="sxs-lookup"><span data-stu-id="e553e-168">This PasswordBox looks like this.</span></span>

![Kennwortfeld mit einer benutzerdefinierten Schaltfläche zum Anzeigen des Kennworts](images/passwordbox-custom-reveal.png)

## <a name="choose-the-right-keyboard-for-your-text-control"></a><span data-ttu-id="e553e-170">Auswählen der richtigen Tastatur für Ihr Textsteuerelement</span><span class="sxs-lookup"><span data-stu-id="e553e-170">Choose the right keyboard for your text control</span></span>

<span data-ttu-id="e553e-171">Um Benutzern die Eingabe von Daten mit der Bildschirmtastatur oder dem Soft Input Panel (SIP) zu erleichtern, können Sie den Eingabeumfang des Textsteuerelements an die Art der Daten anpassen, die der Benutzer vermutlich eingeben wird.</span><span class="sxs-lookup"><span data-stu-id="e553e-171">To help users to enter data using the touch keyboard, or Soft Input Panel (SIP), you can set the input scope of the text control to match the kind of data the user is expected to enter.</span></span> <span data-ttu-id="e553e-172">Das Kennwortfeld unterstützt nur die Eingabeumfangwerte **Password** und **NumericPin**.</span><span class="sxs-lookup"><span data-stu-id="e553e-172">PasswordBox supports only the **Password** and **NumericPin** input scope values.</span></span> <span data-ttu-id="e553e-173">Andere Werte werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e553e-173">Any other value is ignored.</span></span>

<span data-ttu-id="e553e-174">Weitere Informationen zur Verwendung von Eingabeumfängen finden Sie unter [Verwenden des Eingabeumfangs zum Ändern der Bildschirmtastatur](https://msdn.microsoft.com/library/windows/apps/mt280229).</span><span class="sxs-lookup"><span data-stu-id="e553e-174">For more info about how to use input scopes, see [Use input scope to change the touch keyboard](https://msdn.microsoft.com/library/windows/apps/mt280229).</span></span>

## <a name="recommendations"></a><span data-ttu-id="e553e-175">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="e553e-175">Recommendations</span></span>

-   <span data-ttu-id="e553e-176">Verwenden Sie eine Beschriftung oder Platzhaltertext, wenn der Zweck des Kennwortfelds nicht eindeutig ist.</span><span class="sxs-lookup"><span data-stu-id="e553e-176">Use a label or placeholder text if the purpose of the password box isn't clear.</span></span> <span data-ttu-id="e553e-177">Eine Beschriftung ist sichtbar, unabhängig davon, ob das Texteingabefeld über einen Wert verfügt.</span><span class="sxs-lookup"><span data-stu-id="e553e-177">A label is visible whether or not the text input box has a value.</span></span> <span data-ttu-id="e553e-178">Platzhaltertext wird im Texteingabefeld angezeigt und wird erst ausgeblendet, wenn der Benutzer einen Wert eingibt.</span><span class="sxs-lookup"><span data-stu-id="e553e-178">Placeholder text is displayed inside the text input box and disappears once a value has been entered.</span></span>
-   <span data-ttu-id="e553e-179">Weisen Sie dem Kennwortfeld eine entsprechende Breite für den Bereich der Werte zu, die eingegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="e553e-179">Give the password box an appropriate width for the range of values that can be entered.</span></span> <span data-ttu-id="e553e-180">Die Wortlänge variiert zwischen den einzelnen Sprachen. Sie sollten also die Lokalisierung berücksichtigen, wenn Ihre App global verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="e553e-180">Word length varies between languages, so take localization into account if you want your app to be world-ready.</span></span>
-   <span data-ttu-id="e553e-181">Platzieren Sie kein anderes Steuerelement neben einem Eingabefeld für Kennwörter.</span><span class="sxs-lookup"><span data-stu-id="e553e-181">Don't put another control right next to a password input box.</span></span> <span data-ttu-id="e553e-182">Das Kennwortfeld weist eine Schaltfläche zum Anzeigen des Kennworts auf, damit Benutzer die eingegebenen Kennwörter überprüfen können. Wenn ein anderes Steuerelement direkt daneben vorhanden ist, zeigen Benutzer möglicherweise versehentlich ihre Kennwörter an, wenn sie versuchen, mit dem anderen Steuerelement zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="e553e-182">The password box has a password reveal button for users to verify the passwords they have typed, and having another control right next to it might make users accidentally reveal their passwords when they try to interact with the other control.</span></span> <span data-ttu-id="e553e-183">Um dies zu verhindern, achten Sie auf einen gewissen Abstand zwischen dem Eingabefeld für Kennwörter und dem anderen Steuerelement. Sie können das andere Steuerelement auch in der nächsten Zeile platzieren.</span><span class="sxs-lookup"><span data-stu-id="e553e-183">To prevent this from happening, put some spacing between the password in put box and the other control, or put the other control on the next line.</span></span>
-   <span data-ttu-id="e553e-184">Ziehen Sie für die Kontenerstellung die Anzeige von zwei Kennwortfeldern in Erwägung: eins für das neue Kennwort und ein zweites zum Bestätigen des neuen Kennworts.</span><span class="sxs-lookup"><span data-stu-id="e553e-184">Consider presenting two password boxes for account creation: one for the new password, and a second to confirm the new password.</span></span>
-   <span data-ttu-id="e553e-185">Zeigen Sie für Benutzernamen nur ein einzelnes Kennwortfeld an.</span><span class="sxs-lookup"><span data-stu-id="e553e-185">Only show a single password box for logins.</span></span>
-   <span data-ttu-id="e553e-186">Wenn ein Kennwortfeld zur PIN-Eingabe verwendet wird, sollten Sie möglicherweise statt einer Bestätigungsschaltfläche eine sofortige Reaktion nach der Eingabe der letzten Zahl vorsehen.</span><span class="sxs-lookup"><span data-stu-id="e553e-186">When a password box is used to enter a PIN, consider providing an instant response as soon as the last number is entered instead of using a confirmation button.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="e553e-187">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="e553e-187">Get the sample code</span></span>

- <span data-ttu-id="e553e-188">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e553e-188">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="e553e-189">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="e553e-189">Related articles</span></span>

[<span data-ttu-id="e553e-190">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="e553e-190">Text controls</span></span>](text-controls.md)

- [<span data-ttu-id="e553e-191">Richtlinien für die Rechtschreibprüfung</span><span class="sxs-lookup"><span data-stu-id="e553e-191">Guidelines for spell checking</span></span>](text-controls.md)
- [<span data-ttu-id="e553e-192">Hinzufügen von Suchfunktionen</span><span class="sxs-lookup"><span data-stu-id="e553e-192">Adding search</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465231)
- [<span data-ttu-id="e553e-193">Richtlinien für die Texteingabe</span><span class="sxs-lookup"><span data-stu-id="e553e-193">Guidelines for text input</span></span>](text-controls.md)
- [<span data-ttu-id="e553e-194">TextBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="e553e-194">TextBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209683)
- [<span data-ttu-id="e553e-195">Windows.UI.Xaml.Controls PasswordBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="e553e-195">Windows.UI.Xaml.Controls PasswordBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227519)
- [<span data-ttu-id="e553e-196">StringLength-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="e553e-196">String.Length property</span></span>](https://msdn.microsoft.com/library/system.string.length(v=vs.110).aspx)
