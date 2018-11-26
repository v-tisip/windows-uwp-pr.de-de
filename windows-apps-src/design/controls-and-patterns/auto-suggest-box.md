---
Description: A text entry box that provides suggestions as the user types.
title: Richtlinien für Felder mit automatischen Vorschlägen
ms.assetid: 1F608477-F795-4F33-92FA-F200CC243B6B
dev.assetid: 54F8DB8A-120A-4D79-8B5A-9315A3764C2F
label: Auto-suggest box
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
pm-contact: miguelrb
design-contact: ksulliv
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: b68b3480ac81a445551a070eaf0a1454ff22a9e7
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7695264"
---
# <a name="auto-suggest-box"></a><span data-ttu-id="821eb-103">Feld mit automatischen Vorschlägen</span><span class="sxs-lookup"><span data-stu-id="821eb-103">Auto-suggest box</span></span>

<span data-ttu-id="821eb-104">Verwenden Sie ein AutoSuggestBox-Element, um eine Liste mit Vorschlägen bereitzustellen, aus der Benutzer bei der Eingabe auswählen können.</span><span class="sxs-lookup"><span data-stu-id="821eb-104">Use an AutoSuggestBox to provide a list of suggestions for a user to select from as they type.</span></span>

> <span data-ttu-id="821eb-105">**Wichtige APIs:** [Klasse „AutoSuggestBox“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.aspx), [Ereignis „TextChanged“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.textchanged.aspx), [Ereignis „SuggestionChose“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.suggestionchosen.aspx), [Ereignis „QuerySubmitted“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.querysubmitted.aspx)</span><span class="sxs-lookup"><span data-stu-id="821eb-105">**Important APIs**: [AutoSuggestBox class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.aspx), [TextChanged event](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.textchanged.aspx), [SuggestionChose event](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.suggestionchosen.aspx), [QuerySubmitted event](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.querysubmitted.aspx)</span></span>

![Ein Feld mit automatischen Vorschlägen](images/controls/auto-suggest-box-open.png)

## <a name="is-this-the-right-control"></a><span data-ttu-id="821eb-107">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="821eb-107">Is this the right control?</span></span>

<span data-ttu-id="821eb-108">Wenn Sie ein einfaches, anpassbares Steuerelement verwenden möchten, das die Textsuche mit einer Liste von Vorschlägen ermöglicht, verwenden Sie ein Feld mit automatischen Vorschlägen.</span><span class="sxs-lookup"><span data-stu-id="821eb-108">If you'd like a simple, customizable control that allows text search with a list of suggestions, then choose an auto-suggest box.</span></span>

<span data-ttu-id="821eb-109">Weitere Informationen zum Auswählen des passenden Textsteuerelements finden Sie im Artikel über [Textsteuerelemente](text-controls.md).</span><span class="sxs-lookup"><span data-stu-id="821eb-109">For more info about choosing the right text control, see the [Text controls](text-controls.md) article.</span></span>

## <a name="examples"></a><span data-ttu-id="821eb-110">Beispiele</span><span class="sxs-lookup"><span data-stu-id="821eb-110">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="821eb-111">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="821eb-111">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="821eb-112">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/AutoSuggestBox">die App zu öffnen und AutoSuggestBox in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="821eb-112">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/AutoSuggestBox">open the app and see the AutoSuggestBox in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="821eb-113">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="821eb-113">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="821eb-114">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="821eb-114">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="821eb-115">Ein Feld mit automatischen Vorschlägen in der Groove-Musik-App.</span><span class="sxs-lookup"><span data-stu-id="821eb-115">An auto suggest box in the Groove Music app.</span></span>

![Ein Feld mit automatischen Vorschlägen in der Groove-Musik-App](images/control-examples/auto-suggest-box-groove.png)

## <a name="anatomy"></a><span data-ttu-id="821eb-117">Aufbau</span><span class="sxs-lookup"><span data-stu-id="821eb-117">Anatomy</span></span>
<span data-ttu-id="821eb-118">Der Einstiegspunkt für das Feld mit automatischen Vorschlägen besteht aus einem optionalen Header und einem Feld mit optionalem Hinweistext:</span><span class="sxs-lookup"><span data-stu-id="821eb-118">The entry point for the auto-suggest box consists of an optional header and a text box with optional hint text:</span></span>

![Beispiel für den Einstiegspunkt für das Steuerelement für automatische Vorschläge](images/controls_autosuggest_entrypoint.png)

<span data-ttu-id="821eb-120">Die Ergebnisliste für automatische Vorschläge wird automatisch ausgefüllt, sobald der Benutzer mit der Texteingabe beginnt.</span><span class="sxs-lookup"><span data-stu-id="821eb-120">The auto-suggest results list populates automatically once the user starts to enter text.</span></span> <span data-ttu-id="821eb-121">Die Ergebnisliste kann oberhalb oder unterhalb des Texteingabefelds angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="821eb-121">The results list can appear above or below the text entry box.</span></span> <span data-ttu-id="821eb-122">Eine Schaltfläche „Alles löschen” wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="821eb-122">A "clear all" button appears:</span></span>

![Beispiel für das erweiterte Steuerelement für automatische Vorschläge](images/controls_autosuggest_expanded01.png)

## <a name="create-an-auto-suggest-box"></a><span data-ttu-id="821eb-124">Erstellen eines Felds mit automatischen Vorschlägen</span><span class="sxs-lookup"><span data-stu-id="821eb-124">Create an auto-suggest box</span></span>

<span data-ttu-id="821eb-125">Zum Verwenden eines AutoSuggestBox-Elements müssen Sie auf drei Benutzeraktionen reagieren.</span><span class="sxs-lookup"><span data-stu-id="821eb-125">To use an AutoSuggestBox, you need to respond to 3 user actions.</span></span>

- <span data-ttu-id="821eb-126">Text geändert: Aktualisieren Sie die Vorschlagsliste, wenn der Benutzer Text eingibt.</span><span class="sxs-lookup"><span data-stu-id="821eb-126">Text changed - When the user enters text, update the suggestion list.</span></span>
- <span data-ttu-id="821eb-127">Vorschlag ausgewählt: Aktualisieren Sie das Textfeld, wenn der Benutzer in der Vorschlagsliste einen Vorschlag auswählt.</span><span class="sxs-lookup"><span data-stu-id="821eb-127">Suggestion chosen - When the user chooses a suggestion in the suggestion list, update the text box.</span></span>
- <span data-ttu-id="821eb-128">Abfrage gesendet: Zeigen Sie die Abfrageergebnisse an, wenn der Benutzer eine Abfrage sendet.</span><span class="sxs-lookup"><span data-stu-id="821eb-128">Query submitted - When the user submits a query, show the query results.</span></span>

### <a name="text-changed"></a><span data-ttu-id="821eb-129">Text geändert</span><span class="sxs-lookup"><span data-stu-id="821eb-129">Text changed</span></span>

<span data-ttu-id="821eb-130">Das Ereignis [TextChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.textchanged.aspx) tritt ein, sobald der Inhalt des Textfelds aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="821eb-130">The [TextChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.textchanged.aspx) event occurs whenever the content of the text box is updated.</span></span> <span data-ttu-id="821eb-131">Verwenden Sie die [Reason](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestboxtextchangedeventargs.reason.aspx)-Eigenschaft für die Ereignisargumente, um zu ermitteln, ob die Änderung aufgrund einer Benutzereingabe erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="821eb-131">Use the event args [Reason](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestboxtextchangedeventargs.reason.aspx) property to determine whether the change was due to user input.</span></span> <span data-ttu-id="821eb-132">Wenn der Grund für die Änderung **UserInput** lautet, filtern Sie Ihre Daten basierend auf der Eingabe.</span><span class="sxs-lookup"><span data-stu-id="821eb-132">If the change reason is **UserInput**, filter your data based on the input.</span></span> <span data-ttu-id="821eb-133">Legen Sie die gefilterten Daten anschließend als [ItemsSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) des AutoSuggestBox-Elements fest, um die Vorschlagsliste zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="821eb-133">Then, set the filtered data as the [ItemsSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) of the AutoSuggestBox to update the suggestion list.</span></span>

<span data-ttu-id="821eb-134">Um zu steuern, wie Elemente in der Vorschlagsliste angezeigt werden, können Sie [DisplayMemberPath](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.displaymemberpath.aspx) oder [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) verwenden.</span><span class="sxs-lookup"><span data-stu-id="821eb-134">To control how items are displayed in the suggestion list, you can use [DisplayMemberPath](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.displaymemberpath.aspx) or [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx).</span></span>

- <span data-ttu-id="821eb-135">Wenn Sie den Text einer einzelnen Eigenschaft des Datenelements anzeigen möchten, legen Sie die DisplayMemberPath-Eigenschaft fest, um auszuwählen, welche Eigenschaft Ihres Objekts in der Vorschlagsliste angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="821eb-135">To display the text of a single property of your data item, set the DisplayMemberPath property to choose which property from your object to display in the suggestion list.</span></span>
- <span data-ttu-id="821eb-136">Verwenden Sie zum Definieren einer benutzerdefinierten Darstellung für jedes Element in der Liste die ItemTemplate-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="821eb-136">To define a custom look for each item in the list, use the ItemTemplate property.</span></span>

### <a name="suggestion-chosen"></a><span data-ttu-id="821eb-137">Vorschlag ausgewählt</span><span class="sxs-lookup"><span data-stu-id="821eb-137">Suggestion chosen</span></span>

<span data-ttu-id="821eb-138">Wenn ein Benutzer mit der Tastatur durch die Vorschlagsliste navigiert, müssen Sie den Text im Textfeld entsprechend aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="821eb-138">When a user navigates through the suggestion list using the keyboard, you need to update the text in the text box to match.</span></span>

<span data-ttu-id="821eb-139">Sie können die [TextMemberPath](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.textmemberpath.aspx)-Eigenschaft festlegen, um auszuwählen, welche Eigenschaft des Datenobjekts im Textfeld angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="821eb-139">You can set the [TextMemberPath](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.textmemberpath.aspx) property to choose which property from your data object to display in the text box.</span></span> <span data-ttu-id="821eb-140">Wenn Sie ein TextMemberPath-Element angeben, wird das Textfeld automatisch aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="821eb-140">If you specify a TextMemberPath, the text box is updated automatically.</span></span> <span data-ttu-id="821eb-141">Sie sollten in der Regel den gleichen Wert für DisplayMemberPath and TextMemberPath angeben, damit der Text in der Vorschlagsliste und im Textfeld identisch ist.</span><span class="sxs-lookup"><span data-stu-id="821eb-141">You should typically specify the same value for DisplayMemberPath and TextMemberPath so the text is the same in the suggestion list and the text box.</span></span>

<span data-ttu-id="821eb-142">Wenn Sie mehr als eine einfache Eigenschaft anzeigen müssen, behandeln Sie das [SuggestionChosen](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.suggestionchosen.aspx)-Ereignis, um das Textfeld mit benutzerdefiniertem Text basierend auf dem ausgewählten Element zu füllen.</span><span class="sxs-lookup"><span data-stu-id="821eb-142">If you need to show more than a simple property, handle the [SuggestionChosen](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.suggestionchosen.aspx) event to populate the text box with custom text based on the selected item.</span></span>

### <a name="query-submitted"></a><span data-ttu-id="821eb-143">Abfrage gesendet</span><span class="sxs-lookup"><span data-stu-id="821eb-143">Query submitted</span></span>

<span data-ttu-id="821eb-144">Behandeln Sie das [QuerySubmitted](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.querysubmitted.aspx) -Ereignis, um eine passende Abfrageaktion für die App durchzuführen und das Ergebnis dem Benutzer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="821eb-144">Handle the [QuerySubmitted](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.querysubmitted.aspx) event to perform a query action appropriate to your app and show the result to the user.</span></span>

<span data-ttu-id="821eb-145">Das QuerySubmitted-Ereignis tritt ein, wenn ein Benutzer eine Abfragezeichenfolge absendet.</span><span class="sxs-lookup"><span data-stu-id="821eb-145">The QuerySubmitted event occurs when a user commits a query string.</span></span> <span data-ttu-id="821eb-146">Der Benutzer kann diesen Schritt wie folgt ausführen:</span><span class="sxs-lookup"><span data-stu-id="821eb-146">The user can commit a query in one of these ways:</span></span>
- <span data-ttu-id="821eb-147">Mit dem Fokus auf dem Textfeld EINGABETASTE drücken oder auf das Abfragesymbol klicken.</span><span class="sxs-lookup"><span data-stu-id="821eb-147">While the focus is in the text box, press Enter or click the query icon.</span></span> <span data-ttu-id="821eb-148">Die [ChosenSuggestion](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestboxquerysubmittedeventargs.chosensuggestion.aspx)-Eigenschaft für die Ereignisargumente lautet **null**.</span><span class="sxs-lookup"><span data-stu-id="821eb-148">The event args [ChosenSuggestion](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestboxquerysubmittedeventargs.chosensuggestion.aspx) property is **null**.</span></span>
- <span data-ttu-id="821eb-149">Mit dem Fokus auf der Vorschlagsliste EINGABETASTE drücken oder auf ein Element klicken oder tippen.</span><span class="sxs-lookup"><span data-stu-id="821eb-149">While the focus is in the suggestion list, press Enter, click, or tap an item.</span></span> <span data-ttu-id="821eb-150">Die ChosenSuggestion-Eigenschaft für die Ereignisargumente enthält das Element, das in der Liste ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="821eb-150">The event args ChosenSuggestion property contains the item that was selected from the list.</span></span>

<span data-ttu-id="821eb-151">In allen Fällen enthält die [QueryText](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestboxquerysubmittedeventargs.querytext.aspx)-Eigenschaft für die Ereignisargumente den Text aus dem Textfeld.</span><span class="sxs-lookup"><span data-stu-id="821eb-151">In all cases, the event args [QueryText](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestboxquerysubmittedeventargs.querytext.aspx) property contains the text from the text box.</span></span>

<span data-ttu-id="821eb-152">Dies ist ein einfaches AutoSuggestBox-Element mit den erforderlichen Ereignishandlern.</span><span class="sxs-lookup"><span data-stu-id="821eb-152">Here is a simple AutoSuggestBox with the required event handlers.</span></span>

```xaml
<AutoSuggestBox PlaceholderText="Search" QueryIcon="Find" Width="200"
                TextChanged="AutoSuggestBox_TextChanged"
                QuerySubmitted="AutoSuggestBox_QuerySubmitted"
                SuggestionChosen="AutoSuggestBox_SuggestionChosen"/>
```

```csharp
private void AutoSuggestBox_TextChanged(AutoSuggestBox sender, AutoSuggestBoxTextChangedEventArgs args)
{
    // Only get results when it was a user typing,
    // otherwise assume the value got filled in by TextMemberPath
    // or the handler for SuggestionChosen.
    if (args.Reason == AutoSuggestionBoxTextChangeReason.UserInput)
    {
        //Set the ItemsSource to be your filtered dataset
        //sender.ItemsSource = dataset;
    }
}


private void AutoSuggestBox_SuggestionChosen(AutoSuggestBox sender, AutoSuggestBoxSuggestionChosenEventArgs args)
{
    // Set sender.Text. You can use args.SelectedItem to build your text string.
}


private void AutoSuggestBox_QuerySubmitted(AutoSuggestBox sender, AutoSuggestBoxQuerySubmittedEventArgs args)
{
    if (args.ChosenSuggestion != null)
    {
        // User selected an item from the suggestion list, take an action on it here.
    }
    else
    {
        // Use args.QueryText to determine what to do.
    }
}
```

## <a name="use-autosuggestbox-for-search"></a><span data-ttu-id="821eb-153">Verwenden von AutoSuggestBox für die Suche</span><span class="sxs-lookup"><span data-stu-id="821eb-153">Use AutoSuggestBox for search</span></span>

<span data-ttu-id="821eb-154">Verwenden Sie ein AutoSuggestBox-Element, um eine Liste mit Vorschlägen bereitzustellen, aus der Benutzer während der Eingabe auswählen können.</span><span class="sxs-lookup"><span data-stu-id="821eb-154">Use an AutoSuggestBox to provide a list of suggestions for a user to select from as they type.</span></span>

<span data-ttu-id="821eb-155">Standardmäßig wird für das Texteingabefeld keine Abfrageschaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="821eb-155">By default, the text entry box doesn’t have a query button shown.</span></span> <span data-ttu-id="821eb-156">Sie können die [QueryIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.queryicon.aspx) -Eigenschaft festlegen, um eine Schaltfläche mit dem angegebenen Symbol rechts vom Textfeld hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="821eb-156">You can set the [QueryIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.queryicon.aspx) property to add a button with the specified icon on the right side of the text box.</span></span> <span data-ttu-id="821eb-157">Wenn das AutoSuggestBox-Element wie ein typisches Suchfeld aussehen soll, fügen Sie beispielsweise wie folgt ein Suchsymbol hinzu.</span><span class="sxs-lookup"><span data-stu-id="821eb-157">For example, to make the AutoSuggestBox look like a typical search box, add a ‘find’ icon, like this.</span></span>

```xaml
<AutoSuggestBox QueryIcon="Find"/>
```

<span data-ttu-id="821eb-158">Hier ist ein AutoSuggestBox-Element mit einem Suchsymbol dargestellt.</span><span class="sxs-lookup"><span data-stu-id="821eb-158">Here's an AutoSuggestBox with a 'find' icon.</span></span>

![Beispiel für den Einstiegspunkt für das Steuerelement für automatische Vorschläge](images/controls_autosuggest_entrypoint.png)

## <a name="dos-and-donts"></a><span data-ttu-id="821eb-160">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="821eb-160">Do's and don'ts</span></span>

-   <span data-ttu-id="821eb-161">Zeigen Sie die einzeilige Meldung „Keine Ergebnisse” an, wenn Sie das Feld mit automatischen Vorschlägen zum Durchführen von Suchen verwenden und keine Suchergebnisse für den eingegebenen Text vorhanden sind, damit Benutzer wissen, dass ihre Suchanfrage ausgeführt wurde:</span><span class="sxs-lookup"><span data-stu-id="821eb-161">When using the auto-suggest box to perform searches and no search results exist for the entered text, display a single-line "No results" message as the result so that users know their search request executed:</span></span>

    ![Beispiel für ein Feld mit automatischen Vorschlägen ohne Suchergebnisse](images/controls_autosuggest_noresults.png)

<!--
<div class="microsoft-internal-note">
**Globalization and localization checklist**

<table>
<tr>
<th>Vertical spacing</th><td>Use non-Latin characters for vertical spacing to ensure non-Latin scripts will display properly, including numbers.</td>
</tr>
<tr>
<th>Scrolling</th><td>When auto suggest text is selected, user should be able to scroll to end of string.</td>
</tr>
</table>
</div>
-->

## <a name="get-the-sample-code"></a><span data-ttu-id="821eb-163">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="821eb-163">Get the sample code</span></span>

- <span data-ttu-id="821eb-164">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="821eb-164">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>
- [<span data-ttu-id="821eb-165">Beispiel für AutoSuggestBox</span><span class="sxs-lookup"><span data-stu-id="821eb-165">AutoSuggestBox sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlAutoSuggestBox)

## <a name="related-articles"></a><span data-ttu-id="821eb-166">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="821eb-166">Related articles</span></span>

- [<span data-ttu-id="821eb-167">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="821eb-167">Text controls</span></span>](text-controls.md)
- [<span data-ttu-id="821eb-168">Rechtschreibprüfung</span><span class="sxs-lookup"><span data-stu-id="821eb-168">Spell checking</span></span>](text-controls.md)
- [<span data-ttu-id="821eb-169">Suche</span><span class="sxs-lookup"><span data-stu-id="821eb-169">Search</span></span>](search.md)
- [<span data-ttu-id="821eb-170">TextBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="821eb-170">TextBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209683)
- [<span data-ttu-id="821eb-171">Windows.UI.Xaml.Controls PasswordBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="821eb-171">Windows.UI.Xaml.Controls PasswordBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227519)
- [<span data-ttu-id="821eb-172">StringLength-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="821eb-172">String.Length property</span></span>](https://msdn.microsoft.com/library/system.string.length.aspx)
