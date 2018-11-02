---
author: mijacobs
Description: Dialogs and flyouts display transient UI elements that appear when the user requests them or when something happens that requires notification or approval.
title: Dialogfeld-Steuerelemente
label: Dialogs
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
keywords: windows 10, uwp
ms.assetid: ad6affd9-a3c0-481f-a237-9a1ecd561be8
pm-contact: yulikl
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 9ba4bfcd38acba2bcd7c8399b8b17184edacc15a
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5947317"
---
## <a name="dialog-controls"></a><span data-ttu-id="b0a61-103">Dialogfeld-Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="b0a61-103">Dialog controls</span></span>

<span data-ttu-id="b0a61-104">Dialogfelder sind modale benutzeroberflächenüberlagerungen, die kontextbezogene app-Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="b0a61-104">Dialog controls are modal UI overlays that provide contextual app information.</span></span> <span data-ttu-id="b0a61-105">Sie blockieren Interaktionen mit dem app-Fenster, bis Sie explizit geschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="b0a61-105">They block interactions with the app window until being explicitly dismissed.</span></span> <span data-ttu-id="b0a61-106">Sie verlangen häufig eine Aktion vom Benutzer.</span><span class="sxs-lookup"><span data-stu-id="b0a61-106">They often request some kind of action from the user.</span></span>

![Beispiel für ein Dialogfeld](../images/dialogs/dialog_RS2_delete_file.png)


> <span data-ttu-id="b0a61-108">**Wichtige APIs**: [ContentDialog-Klasse](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog)</span><span class="sxs-lookup"><span data-stu-id="b0a61-108">**Important APIs**: [ContentDialog class](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog)</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="b0a61-109">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="b0a61-109">Is this the right control?</span></span>

<span data-ttu-id="b0a61-110">Verwenden Sie Dialogfelder und Flyouts, um Benutzern wichtige Informationen mitzuteilen oder deren Bestätigung bzw. zusätzliche Informationen anzufordern, bevor eine Aktion abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="b0a61-110">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>

<span data-ttu-id="b0a61-111">Empfehlungen zur Verwendung von einem Dialogfeld im Vergleich zu wann ein Flyout (ein ähnliches Steuerelement) verwenden, finden Sie unter [Dialogfelder und Flyouts](index.md).</span><span class="sxs-lookup"><span data-stu-id="b0a61-111">For recommendations on when to use a dialog vs. when to use a flyout (a similar control), see [Dialogs and flyouts](index.md).</span></span> 

## <a name="examples"></a><span data-ttu-id="b0a61-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b0a61-112">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="b0a61-113">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="b0a61-113">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="../images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="b0a61-114">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um die App zu öffnen und <a href="xamlcontrolsgallery:/item/ContentDialog">ContentDialog</a> oder <a href="xamlcontrolsgallery:/item/Flyout">Flyout</a> in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-114">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to open the app and see the <a href="xamlcontrolsgallery:/item/ContentDialog">ContentDialog</a> or <a href="xamlcontrolsgallery:/item/Flyout">Flyout</a> in action.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="b0a61-115">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="b0a61-115">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="b0a61-116">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b0a61-116">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="general-guidelines"></a><span data-ttu-id="b0a61-117">Allgemeine Richtlinien</span><span class="sxs-lookup"><span data-stu-id="b0a61-117">General guidelines</span></span>

-   <span data-ttu-id="b0a61-118">Sie sollten das Problem oder das Ziel des Benutzers in der ersten Zeile des Dialogfeldtexts deutlich benennen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-118">Clearly identify the issue or the user's objective in the first line of the dialog's text.</span></span>
-   <span data-ttu-id="b0a61-119">Der Dialogfeldtitel ist die Hauptanweisung und optional.</span><span class="sxs-lookup"><span data-stu-id="b0a61-119">The dialog title is the main instruction and is optional.</span></span>
    -   <span data-ttu-id="b0a61-120">Verwenden Sie einen kurzen Titel, um dem Benutzer die erforderlichen Aktionen im Dialogfeld zu erklären.</span><span class="sxs-lookup"><span data-stu-id="b0a61-120">Use a short title to explain what people need to do with the dialog.</span></span>
    -   <span data-ttu-id="b0a61-121">Wenn Sie mit dem Dialogfeld eine einfache Meldung, einen Fehler oder eine Frage anzeigen möchten, können Sie den Titel optional auslassen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-121">If you're using the dialog to deliver a simple message, error or question, you can optionally omit the title.</span></span> <span data-ttu-id="b0a61-122">Vermitteln Sie dann im Inhalt die wichtigsten Informationen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-122">Rely on the content text to deliver that core information.</span></span>
    -   <span data-ttu-id="b0a61-123">Stellen Sie sicher, dass sich der Titel direkt auf die Auswahlmöglichkeiten der Schaltflächen bezieht.</span><span class="sxs-lookup"><span data-stu-id="b0a61-123">Make sure that the title relates directly to the button choices.</span></span>
-   <span data-ttu-id="b0a61-124">Der Inhalt des Dialogfelds enthält den beschreibenden Text und ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b0a61-124">The dialog content contains the descriptive text and is required.</span></span>
    -   <span data-ttu-id="b0a61-125">Stellen Sie die Meldung, den Fehler oder die blockierende Frage so einfach wie möglich dar.</span><span class="sxs-lookup"><span data-stu-id="b0a61-125">Present the message, error, or blocking question as simply as possible.</span></span>
    -   <span data-ttu-id="b0a61-126">Stellen Sie bei Verwendung eines Dialogfeldtitels mithilfe des Inhaltsbereichs weitere Details bereit, oder definieren Sie Terminologie.</span><span class="sxs-lookup"><span data-stu-id="b0a61-126">If a dialog title is used, use the content area to provide more detail or define terminology.</span></span> <span data-ttu-id="b0a61-127">Wiederholen Sie nicht den Titel mit anderen Worten.</span><span class="sxs-lookup"><span data-stu-id="b0a61-127">Don't repeat the title with slightly different wording.</span></span>
-   <span data-ttu-id="b0a61-128">Mindestens eine Dialogfeldschaltfläche muss angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b0a61-128">At least one dialog button must appear.</span></span>
    -   <span data-ttu-id="b0a61-129">Stellen Sie sicher, dass Ihr Dialogfeld mindestens eine Schaltfläche aufweist, die eine sichere, nicht-destruktive Aktion wie „Alles klar!“, „Schließen“ oder „Abbrechen“ auslöst.</span><span class="sxs-lookup"><span data-stu-id="b0a61-129">Ensure that your dialog has at least one button corresponding to a safe, nondestructive action like "Got it!", "Close", or "Cancel".</span></span> <span data-ttu-id="b0a61-130">Verwenden Sie die CloseButton-API, um diese Schaltfläche hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-130">Use the CloseButton API to add this button.</span></span>
    -   <span data-ttu-id="b0a61-131">Verwenden Sie für den Schaltflächentext konkrete Antworten auf die Hauptanweisung oder den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="b0a61-131">Use specific responses to the main instruction or content as button text.</span></span> <span data-ttu-id="b0a61-132">Beispiel: „Möchten Sie AppName den Zugriff auf Ihren Standort erlauben?“, gefolgt von den Schaltflächen „Zulassen“ und „Blockieren“.</span><span class="sxs-lookup"><span data-stu-id="b0a61-132">An example is, "Do you want to allow AppName to access your location?", followed by "Allow" and "Block" buttons.</span></span> <span data-ttu-id="b0a61-133">Konkrete Antworten erleichtern das Verständnis und ermöglichen somit eine schnelle Entscheidungsfindung.</span><span class="sxs-lookup"><span data-stu-id="b0a61-133">Specific responses can be understood more quickly, resulting in efficient decision making.</span></span>
    - <span data-ttu-id="b0a61-134">Stellen Sie sicher, dass der Text der Aktionsschaltflächen kurz ist.</span><span class="sxs-lookup"><span data-stu-id="b0a61-134">Ensure that the text of the action buttons is concise.</span></span> <span data-ttu-id="b0a61-135">Kurze Anweisungen ermöglichen dem Benutzer, schnell und zuverlässig eine Entscheidung zu treffen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-135">Short strings enable the user to make a choice quickly and confidently.</span></span>
    - <span data-ttu-id="b0a61-136">Zusätzlich zur sicheren, nicht-destruktiven Aktion können Sie dem Benutzer optional ein oder zwei Aktionsschaltflächen anzeigen, die im Zusammenhang mit der Hauptanweisung stehen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-136">In addition to the safe, nondestructive action, you may optionally present the user with one or two action buttons related to the main instruction.</span></span> <span data-ttu-id="b0a61-137">Diese „bestätigenden“ Aktionsschaltflächen unterstreichen den Hauptgrund des Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="b0a61-137">These "do it" action buttons confirm the main point of the dialog.</span></span> <span data-ttu-id="b0a61-138">Verwenden Sie die PrimaryButton- und SecondaryButton-APIs, um diese „bestätigenden“ Aktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-138">Use the PrimaryButton and SecondaryButton APIs to add these "do it" actions.</span></span>
    - <span data-ttu-id="b0a61-139">Die „bestätigenden“ Aktionsschaltflächen sollten als die am weitesten links stehenden Schaltflächen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b0a61-139">The "do it" action button(s) should appears as the leftmost buttons.</span></span> <span data-ttu-id="b0a61-140">Die sichere, nicht-destruktive Aktion sollte als die am weitesten rechts stehende Schaltfläche angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b0a61-140">The safe, nondestructive action should appear as the rightmost button.</span></span>
    - <span data-ttu-id="b0a61-141">Sie können optional eine der drei Schaltflächen als Standardschaltfläche des Dialogfelds festlegen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-141">You may optionally choose to differentiate one of the three buttons as the dialog's default button.</span></span> <span data-ttu-id="b0a61-142">Verwenden Sie die DefaultButton-API, um eine der Schaltflächen abzugrenzen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-142">Use the DefaultButton API to differentiate one of the buttons.</span></span>  
-   <span data-ttu-id="b0a61-143">Verwenden Sie Dialogfelder nicht für kontextbezogene Fehler, die sich auf eine bestimmte Stelle auf der Seite beziehen, beispielsweise Validierungsfehler (wie in Kennwortfeldern). Verwenden Sie die Canvas der App selbst zum Anzeigen von Inlinefehlern.</span><span class="sxs-lookup"><span data-stu-id="b0a61-143">Don't use dialogs for errors that are contextual to a specific place on the page, such as validation errors (in password fields, for example), use the app's canvas itself to show inline errors.</span></span>
- <span data-ttu-id="b0a61-144">Verwenden Sie die [ContentDialog-Klasse](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog), um Ihre Dialogfeldumgebung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-144">Use the [ContentDialog class](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog) to build your dialog experience.</span></span> <span data-ttu-id="b0a61-145">Verwenden Sie nicht die veraltete MessageDialog-API.</span><span class="sxs-lookup"><span data-stu-id="b0a61-145">Don't use the deprecated MessageDialog API.</span></span>

## <a name="how-to-create-a-dialog"></a><span data-ttu-id="b0a61-146">So erstellen Sie ein Dialogfeld</span><span class="sxs-lookup"><span data-stu-id="b0a61-146">How to create a dialog</span></span>
<span data-ttu-id="b0a61-147">Um ein Dialogfeld zu erstellen, verwenden Sie die [ContentDialog-Klasse](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog).</span><span class="sxs-lookup"><span data-stu-id="b0a61-147">To create a dialog, you use the [ContentDialog class](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog).</span></span> <span data-ttu-id="b0a61-148">Sie können ein Dialogfeld im Code oder Markup erstellen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-148">You can create a dialog in code or markup.</span></span> <span data-ttu-id="b0a61-149">Obwohl es in der Regel leichter ist, UI-Elemente in XAML zu definieren, ist es bei einem einfachen Dialogfeld unkomplizierter, Code zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0a61-149">Although its usually easier to define UI elements in XAML, in the case of a simple dialog, it's actually easier to just use code.</span></span> <span data-ttu-id="b0a61-150">In diesem Beispiel wird ein Dialogfeld erstellt, um dem Benutzer mitzuteilen, dass keine WLAN-Verbindung vorhanden ist. Für die Anzeige wird die Methode [ShowAsync](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) verwendet.</span><span class="sxs-lookup"><span data-stu-id="b0a61-150">This example creates a dialog to notify the user that there's no WiFi connection, and then uses the [ShowAsync](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) method to display it.</span></span>

```csharp
private async void DisplayNoWifiDialog()
{
    ContentDialog noWifiDialog = new ContentDialog
    {
        Title = "No wifi connection",
        Content = "Check your connection and try again.",
        CloseButtonText = "Ok"
    };

    ContentDialogResult result = await noWifiDialog.ShowAsync();
}
```

<span data-ttu-id="b0a61-151">Wenn der Benutzer auf eine Dialogfeldschaltfläche klickt, gibt die Methode [ShowAsync](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) ein [ContentDialogResult](/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult) zurück, damit Sie wissen, auf welche Schaltfläche der Benutzer klickt.</span><span class="sxs-lookup"><span data-stu-id="b0a61-151">When the user clicks a dialog button, the [ShowAsync](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) method returns a [ContentDialogResult](/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult) to let you know which button the user clicks.</span></span>

<span data-ttu-id="b0a61-152">Das Dialogfeld in diesem Beispiel stellt eine Frage und verwendet das zurückgegebene [ContentDialogResult](/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult), um die Antwort des Benutzers zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="b0a61-152">The dialog in this example asks a question and uses the returned [ContentDialogResult](/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult) to determine the user's response.</span></span>

```csharp
private async void DisplayDeleteFileDialog()
{
    ContentDialog deleteFileDialog = new ContentDialog
    {
        Title = "Delete file permanently?",
        Content = "If you delete this file, you won't be able to recover it. Do you want to delete it?",
        PrimaryButtonText = "Delete",
        CloseButtonText = "Cancel"
    };

    ContentDialogResult result = await deleteFileDialog.ShowAsync();

    // Delete the file if the user clicked the primary button.
    /// Otherwise, do nothing.
    if (result == ContentDialogResult.Primary)
    {
        // Delete the file.
    }
    else
    {
        // The user clicked the CLoseButton, pressed ESC, Gamepad B, or the system back button.
        // Do nothing.
    }
}
```

## <a name="provide-a-safe-action"></a><span data-ttu-id="b0a61-153">Bieten Sie eine sichere Aktion</span><span class="sxs-lookup"><span data-stu-id="b0a61-153">Provide a safe action</span></span>
<span data-ttu-id="b0a61-154">Da Dialogfelder Benutzerinteraktion blockieren, und Schaltflächen für die Benutzer das primäre Mittel sind, ein Dialogfeld zu schließen, sollten Sie sicherstellen, dass Ihr Dialogfeld mindestens eine „sichere“, nicht-destruktive Schaltfläche wie z.B. „Schließen“ oder „Alles klar!“ enthält.</span><span class="sxs-lookup"><span data-stu-id="b0a61-154">Because dialogs block user interaction, and because buttons are the primary mechanism for users to dismiss the dialog, ensure that your dialog contains at least one "safe" and nondestructive button such as "Close" or "Got it!".</span></span> **<span data-ttu-id="b0a61-155">Alle Dialogfelder sollten mindestens eine sichere Aktionsschaltfläche enthalten, um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-155">All dialogs should contain at least one safe action button to close the dialog.</span></span>** <span data-ttu-id="b0a61-156">Dadurch wird sichergestellt, dass der Benutzer das Dialogfeld zuverlässig schließen kann, ohne eine Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-156">This ensures that the user can confidently close the dialog without performing an action.</span></span><br>![Dialogfeld mit einer Schaltfläche](../images/dialogs/dialog_RS2_one_button.png)

```csharp
private async void DisplayNoWifiDialog()
{
    ContentDialog noWifiDialog = new ContentDialog
    {
        Title = "No wifi connection",
        Content = "Check your connection and try again.",
        CloseButtonText = "Ok"
    };

    ContentDialogResult result = await noWifiDialog.ShowAsync();
}
```

<span data-ttu-id="b0a61-158">Wenn Dialogfelder dazu verwendet werden, eine blockierende Frage anzuzeigen, sollte Ihr Dialogfeld dem Benutzer Aktionsschaltflächen bieten, die im Zusammenhang mit der Frage stehen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-158">When dialogs are used to display a blocking question, your dialog should present the user with action buttons related to the question.</span></span> <span data-ttu-id="b0a61-159">Die „sichere“, nicht-destruktive Schaltfläche kann durch ein oder zwei „bestätigende“ Aktionsschaltflächen ergänzt werden.</span><span class="sxs-lookup"><span data-stu-id="b0a61-159">The "safe" and nondestructive button may be accompanied by one or two "do it" action buttons.</span></span> <span data-ttu-id="b0a61-160">Wenn dem Benutzer mehrere Optionen angezeigt werden, stellen Sie sicher, dass die Schaltflächen für die „bestätigende“ und die sichere/„ablehnende“ Aktion den Bezug zur Frage eindeutig darstellen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-160">When presenting the user with multiple options, ensure that the buttons clearly explain the "do it" and safe/"don’t do it" actions related to the question proposed.</span></span>

![Dialogfeld mit zwei Schaltflächen](../images/dialogs/dialog_RS2_two_button.png)

```csharp
private async void DisplayLocationPromptDialog()
{
    ContentDialog locationPromptDialog = new ContentDialog
    {
        Title = "Allow AppName to access your location?",
        Content = "AppName uses this information to help you find places, connect with friends, and more.",
        CloseButtonText = "Block",
        PrimaryButtonText = "Allow"
    };

    ContentDialogResult result = await locationPromptDialog.ShowAsync();
}
```

<span data-ttu-id="b0a61-162">Dialogfelder mit drei Schaltflächen werden verwendet, wenn Sie dem Benutzer zwei „bestätigende“ und eine „ablehnende“ Aktion präsentierten möchten.</span><span class="sxs-lookup"><span data-stu-id="b0a61-162">Three button dialogs are used when you present the user with two "do it" actions and a "don’t do it" action.</span></span> <span data-ttu-id="b0a61-163">Dialogfelder mit drei Schaltflächen sollten sparsam verwendet werden und eine klare Unterscheidung zwischen der Sekundäraktion und der sicheren/ablehnenden Aktion enthalten.</span><span class="sxs-lookup"><span data-stu-id="b0a61-163">Three button dialogs should be used sparingly with clear distinctions between the secondary action and the safe/close action.</span></span>

![Dialogfeld mit drei Schaltflächen](../images/dialogs/dialog_RS2_three_button.png)

```csharp
private async void DisplaySubscribeDialog()
{
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

## <a name="the-three-dialog-buttons"></a><span data-ttu-id="b0a61-165">Die drei Schaltflächen des Dialogfelds</span><span class="sxs-lookup"><span data-stu-id="b0a61-165">The three dialog buttons</span></span>
<span data-ttu-id="b0a61-166">Der ContentDialog umfasst drei unterschiedliche Arten von Schaltflächen, die Sie zur Erstellung einer Dialogfeldumgebung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="b0a61-166">ContentDialog has three different types of buttons that you can use to build a dialog experience.</span></span>

- <span data-ttu-id="b0a61-167">**CloseButton** – erforderlich – Stellt die sichere, nicht-destruktive Aktion dar, die es dem Benutzer ermöglicht, das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-167">**CloseButton** - Required - Represents the safe, nondestructive action that enables the user to exit the dialog.</span></span> <span data-ttu-id="b0a61-168">Wird als die am weitesten rechts stehende Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b0a61-168">Appears as the rightmost button.</span></span>
- <span data-ttu-id="b0a61-169">**PrimaryButton** – optional – Stellt die erste „bestätigende“ Aktion dar.</span><span class="sxs-lookup"><span data-stu-id="b0a61-169">**PrimaryButton** - Optional - Represents the first "do it" action.</span></span> <span data-ttu-id="b0a61-170">Wird als die am weitesten links stehende Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b0a61-170">Appears as the leftmost button.</span></span>
- <span data-ttu-id="b0a61-171">**SecondaryButton** – optional – Stellt die zweite „bestätigende“ Aktion dar.</span><span class="sxs-lookup"><span data-stu-id="b0a61-171">**SecondaryButton** - Optional - Represents the second "do it" action.</span></span> <span data-ttu-id="b0a61-172">Wird als mittlere Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b0a61-172">Appears as the middle button.</span></span>

<span data-ttu-id="b0a61-173">Mithilfe der integrierten Schaltflächen kann das Dialogfeld optisch an andere Dialogfelder angepasst werden sowie die Position der Schaltflächen passend ausgerichtet werden. Stellen Sie sicher, dass die Schaltflächen entsprechend auf Tastaturbefehle reagieren und der Befehlsbereich sichtbar bleibt, auch wenn die Bildschirmtastatur aufgerufen ist.</span><span class="sxs-lookup"><span data-stu-id="b0a61-173">Using the built-in buttons will position the buttons appropriately, ensure that they correctly respond to keyboard events, ensure that the command area remains visible even when the on-screen keyboard is up, and will make the dialog look consistent with other dialogs.</span></span>

### <a name="closebutton"></a><span data-ttu-id="b0a61-174">CloseButton</span><span class="sxs-lookup"><span data-stu-id="b0a61-174">CloseButton</span></span>
<span data-ttu-id="b0a61-175">Jedes Dialogfeld sollte eine sichere, nicht-destruktive Aktionsschaltfläche aufweisen, die dem Benutzer das zuverlässige Beenden des Dialogfelds ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="b0a61-175">Every dialog should contain a safe, nondestructive action button that enables the user to confidently exit the dialog.</span></span>

<span data-ttu-id="b0a61-176">Verwenden Sie die ContentDialog.CloseButton-API, um diese Schaltfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-176">Use the ContentDialog.CloseButton API to create this button.</span></span> <span data-ttu-id="b0a61-177">Dadurch schaffen Sie die jeweils richtige Benutzerumgebung für alle Eingabemöglichkeiten wie z.B. Maus, Tastatur, Fingereingabe und Gamepad.</span><span class="sxs-lookup"><span data-stu-id="b0a61-177">This allows you to create the right user experience for all inputs including mouse, keyboard, touch, and gamepad.</span></span> <span data-ttu-id="b0a61-178">Dies ist nötig, wenn:</span><span class="sxs-lookup"><span data-stu-id="b0a61-178">This experience will happen when:</span></span>
<ol>
    <li><span data-ttu-id="b0a61-179">Der Benutzer auf CloseButton klickt oder tippt</span><span class="sxs-lookup"><span data-stu-id="b0a61-179">The user clicks or taps on the CloseButton</span></span> </li>
    <li><span data-ttu-id="b0a61-180">Der Benutzer die Zurück-Taste des Systems betätigt</span><span class="sxs-lookup"><span data-stu-id="b0a61-180">The user presses the system back button</span></span> </li>
    <li><span data-ttu-id="b0a61-181">Der Benutzer auf der Tastatur die ESC-Taste betätigt</span><span class="sxs-lookup"><span data-stu-id="b0a61-181">The user presses the ESC button on the keyboard</span></span> </li>
    <li><span data-ttu-id="b0a61-182">Der Benutzer auf dem Gamepad die B-Taste betätigt</span><span class="sxs-lookup"><span data-stu-id="b0a61-182">The user presses Gamepad B</span></span> </li>
</ol>

<span data-ttu-id="b0a61-183">Wenn der Benutzer auf eine Dialogfeldschaltfläche klickt, gibt die Methode [ShowAsync](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) ein [ContentDialogResult](/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult) zurück, damit Sie wissen, auf welche Schaltfläche der Benutzer klickt.</span><span class="sxs-lookup"><span data-stu-id="b0a61-183">When the user clicks a dialog button, the [ShowAsync](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) method returns a [ContentDialogResult](/uwp/api/Windows.UI.Xaml.Controls.ContentDialogResult) to let you know which button the user clicks.</span></span> <span data-ttu-id="b0a61-184">Klicken auf CloseButton resultiert in ContentDialogResult.None.</span><span class="sxs-lookup"><span data-stu-id="b0a61-184">Pressing on the CloseButton returns ContentDialogResult.None.</span></span>

### <a name="primarybutton-and-secondarybutton"></a><span data-ttu-id="b0a61-185">PrimaryButton und SecondaryButton</span><span class="sxs-lookup"><span data-stu-id="b0a61-185">PrimaryButton and SecondaryButton</span></span>
<span data-ttu-id="b0a61-186">Zusätzlich zu CloseButton können Sie dem Benutzer optional ein oder zwei Aktionsschaltflächen anbieten, die im Zusammenhang mit der Hauptanweisung stehen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-186">In addition to the CloseButton, you may optionally present the user with one or two action buttons related to the main instruction.</span></span>
<span data-ttu-id="b0a61-187">Nutzen Sie PrimaryButton für die erste „bestätigende“ Aktion und SecondaryButton für die zweite „bestätigende“ Aktion.</span><span class="sxs-lookup"><span data-stu-id="b0a61-187">Leverage PrimaryButton for the first "do it" action, and SecondaryButton for the second "do it" action.</span></span> <span data-ttu-id="b0a61-188">Bei Dialogfeldern mit drei Schaltflächen stellt PrimaryButton in der Regel eine eindeutig „bestätigende“ Aktion dar, während SecondaryButton in der Regel eine neutrale oder sekundäre, „bestätigende“ Aktion darstellt.</span><span class="sxs-lookup"><span data-stu-id="b0a61-188">In three-button dialogs, the PrimaryButton generally represents the affirmative "do it" action, while the SecondaryButton generally represents a neutral or secondary "do it" action.</span></span>
<span data-ttu-id="b0a61-189">Beispielsweise kann eine App den Benutzer dazu auffordern, einen Dienst zu abonnieren.</span><span class="sxs-lookup"><span data-stu-id="b0a61-189">For example, an app may prompt the user to subscribe to a service.</span></span> <span data-ttu-id="b0a61-190">In diesem Fall ist PrimaryButton die eindeutig „bestätigende“ Aktion und enthält den Text „Abonnieren“, während SecondaryButton als neutrale, „bestätigende“ Aktion den Text „Testen“ aufweist.</span><span class="sxs-lookup"><span data-stu-id="b0a61-190">The PrimaryButton as the affirmative "do it" action would host the Subscribe text, while the SecondaryButton as the neutral "do it" action would host the Try it text.</span></span> <span data-ttu-id="b0a61-191">CloseButton ermöglicht dem Benutzer in diesem Fall, die Aktion ohne Interaktion abzubrechen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-191">The CloseButton would allow the user to cancel without performing either action.</span></span>

<span data-ttu-id="b0a61-192">Klickt der Benutzer auf PrimaryButton, wird von der Methode [ShowAsync](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) ContentDialogResult.Primary zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b0a61-192">When the user clicks on the PrimaryButton, the [ShowAsync](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) method returns ContentDialogResult.Primary.</span></span>
<span data-ttu-id="b0a61-193">Klickt der Benutzer auf die SecondaryButton, wird von der Methode [ShowAsync](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) ContentDialogResult.Primary zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b0a61-193">When the user clicks on the SecondaryButton, the [ShowAsync](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog.ShowAsync) method returns ContentDialogResult.Secondary.</span></span>

![Dialogfeld mit drei Schaltflächen](../images/dialogs/dialog_RS2_three_button.png)

### <a name="defaultbutton"></a><span data-ttu-id="b0a61-195">DefaultButton</span><span class="sxs-lookup"><span data-stu-id="b0a61-195">DefaultButton</span></span>
<span data-ttu-id="b0a61-196">Sie können optional eine der drei Schaltflächen als Standardschaltfläche festlegen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-196">You may optionally choose to differentiate one of the three buttons as the default button.</span></span> <span data-ttu-id="b0a61-197">Das Festlegen einer Standardschaltfläche hat zur Folge, dass:</span><span class="sxs-lookup"><span data-stu-id="b0a61-197">Specifying the default button causes the following to happen:</span></span>
- <span data-ttu-id="b0a61-198">die Schaltfläche optisch als Akzentschaltfläche behandelt wird</span><span class="sxs-lookup"><span data-stu-id="b0a61-198">The button receives the Accent Button visual treatment</span></span>
- <span data-ttu-id="b0a61-199">die Schaltfläche automatisch auf die EINGABETASTE reagiert</span><span class="sxs-lookup"><span data-stu-id="b0a61-199">The button will respond to the ENTER key automatically</span></span>
    - <span data-ttu-id="b0a61-200">Drückt der Benutzer auf der Tastatur die EINGABETASTE, wird der mit der Standardschaltfläche verknüpfte Click-Handler ausgelöst und das ContentDialogResult gibt den mit der Standardschaltfläche verknüpften Wert zurück</span><span class="sxs-lookup"><span data-stu-id="b0a61-200">When the user presses the ENTER key on the keyboard, the click handler associated with the Default Button will fire and the ContentDialogResult will return the value associated with the Default Button</span></span>
    - <span data-ttu-id="b0a61-201">Wenn der Benutzer den Tastaturfokus auf ein Steuerelement gelegt hat, das die EINGABETASTE handhabt, reagiert die Standardschaltfläche nicht auf Drücken der EINGABETASTE</span><span class="sxs-lookup"><span data-stu-id="b0a61-201">If the user has placed Keyboard Focus on a control that handles ENTER, the Default Button will not respond to ENTER presses</span></span>
- <span data-ttu-id="b0a61-202">Die Schaltfläche erhält den Fokus automatisch, wenn das Dialogfeld geöffnet wird, es sei denn, der Inhalt des Dialogfelds enthält fokussierbare UI</span><span class="sxs-lookup"><span data-stu-id="b0a61-202">The button will receive focus automatically when the Dialog is opened unless the dialog’s content contains focusable UI</span></span>

<span data-ttu-id="b0a61-203">Verwenden Sie die ContentDialog.DefaultButton-Eigenschaft, um die Standardschaltfläche anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b0a61-203">Use the ContentDialog.DefaultButton property to indicate the default button.</span></span> <span data-ttu-id="b0a61-204">Standardmäßig wird keine Standardschaltfläche festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b0a61-204">By default, no default button is set.</span></span>

![Ein Dialogfeld mit drei Schaltflächen mit einer Standardschaltfläche](../images/dialogs/dialog_RS2_three_button_default.png)

```csharp
private async void DisplaySubscribeDialog()
{
    ContentDialog subscribeDialog = new ContentDialog
    {
        Title = "Subscribe to App Service?",
        Content = "Listen, watch, and play in high definition for only $9.99/month. Free to try, cancel anytime.",
        CloseButtonText = "Not Now",
        PrimaryButtonText = "Subscribe",
        SecondaryButtonText = "Try it",
        DefaultButton = ContentDialogButton.Primary
    };

    ContentDialogResult result = await subscribeDialog.ShowAsync();
}
```

## <a name="confirmation-dialogs-okcancel"></a><span data-ttu-id="b0a61-206">Bestätigungsdialogfelder (OK/Abbrechen)</span><span class="sxs-lookup"><span data-stu-id="b0a61-206">Confirmation dialogs (OK/Cancel)</span></span>
<span data-ttu-id="b0a61-207">In einem Bestätigungsdialogfeld können Benutzer bestätigen, dass sie eine Aktion ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="b0a61-207">A confirmation dialog gives users the chance to confirm that they want to perform an action.</span></span> <span data-ttu-id="b0a61-208">Sie können die Aktion bestätigen oder den Vorgang abbrechen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-208">They can affirm the action, or choose to cancel.</span></span>  
<span data-ttu-id="b0a61-209">Ein typisches Bestätigungsdialogfeld verfügt über zwei Schaltflächen: eine Schaltfläche zur Bestätigung („OK“) und eine Schaltfläche zum Abbrechen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-209">A typical confirmation dialog has two buttons: an affirmation ("OK") button and a cancel button.</span></span>  

<ul>
    <li>
        <p><span data-ttu-id="b0a61-210">Die Bestätigungsschaltfläche sollte sich im Allgemeinen auf der linken Seite (die primäre Schaltfläche) und die Abbruchschaltfläche (die sekundäre Schaltfläche) auf der rechten Seite befinden.</span><span class="sxs-lookup"><span data-stu-id="b0a61-210">In general, the affirmation button should be on the left (the primary button) and the cancel button (the secondary button) should be on the right.</span></span></p>
        <img alt="An OK/cancel dialog" src="../images/dialogs/dialog_RS2_delete_file.png" />
    </li>
    <li><span data-ttu-id="b0a61-211">Wie in den allgemeinen Empfehlungen erwähnt, sollten Sie Schaltflächen mit Text verwenden, der konkrete Antworten auf die Hauptanweisung bzw. den Hauptinhalt bietet.</span><span class="sxs-lookup"><span data-stu-id="b0a61-211">As noted in the general recommendations section, use buttons with text that identifies specific responses to the main instruction or content.</span></span>
    </li>
</ul>

> <span data-ttu-id="b0a61-212">Auf einigen Plattformen befindet sich die Bestätigungsschaltfläche auf der rechten anstatt auf der linken Seite.</span><span class="sxs-lookup"><span data-stu-id="b0a61-212">Some platforms put the affirmation button on the right instead of the left.</span></span> <span data-ttu-id="b0a61-213">Warum empfehlen wir die Platzierung auf der linken Seite?</span><span class="sxs-lookup"><span data-stu-id="b0a61-213">So why do we recommend putting it on the left?</span></span>  <span data-ttu-id="b0a61-214">Wenn Sie davon ausgehen, dass die meisten Benutzer Rechtshänder sind und ihr Telefon in dieser Hand halten, ist es bequemer, eine Bestätigungsschaltfläche zu drücken, die sich auf der linken Seite befindet, weil sie für den Benutzer wahrscheinlich einfacher mit dem Daumen erreichbar ist. Bei Schaltflächen auf der rechten Bildschirmseite muss der Benutzer seinen Daumen in eine weniger bequeme Position nach innen bewegen.</span><span class="sxs-lookup"><span data-stu-id="b0a61-214">If you assume that the majority of users are right-handed and they hold their phone with that hand, it's actually more comfortable to press the affirmation button when it's on the left, because the button is more likely to be within the user's thumb-arc. Buttons on the right-side of the screen require the user to pull their thumb inward into a less-comfortable position.</span></span>





## <a name="get-the-sample-code"></a><span data-ttu-id="b0a61-215">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="b0a61-215">Get the sample code</span></span>

- <span data-ttu-id="b0a61-216">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b0a61-216">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="b0a61-217">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="b0a61-217">Related articles</span></span>
- [<span data-ttu-id="b0a61-218">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="b0a61-218">Tooltips</span></span>](../tooltips.md)
- [<span data-ttu-id="b0a61-219">Menüs und Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="b0a61-219">Menus and context menu</span></span>](../menus.md)
- [<span data-ttu-id="b0a61-220">Flyout-Klasse</span><span class="sxs-lookup"><span data-stu-id="b0a61-220">Flyout class</span></span>](/uwp/api/Windows.UI.Xaml.Controls.Flyout)
- [<span data-ttu-id="b0a61-221">ContentDialog-Klasse</span><span class="sxs-lookup"><span data-stu-id="b0a61-221">ContentDialog class</span></span>](/uwp/api/Windows.UI.Xaml.Controls.ContentDialog)
