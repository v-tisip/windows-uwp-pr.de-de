---
author: Jwmsft
Description: "Sie können ein RichEditBox-Steuerelement verwenden, um Rich-Text-Dokumente zu bearbeiten, die formatierten Text, Hyperlinks und Bilder enthalten. Sie können den Schreibschutz für ein RichEditBox-Steuerelement aktivieren, indem Sie die IsReadOnly-Eigenschaft des Steuerelements auf „true“ festlegen."
title: RichEditBox
ms.assetid: 4AFC0DFA-3B89-434D-9F86-4309CCFF7839
label: Rich edit box
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
ms.openlocfilehash: 457e61426214b64d8b17f7b750f9d19b44a49018
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="rich-edit-box"></a><span data-ttu-id="e5175-105">Rich-Edit-Feld</span><span class="sxs-lookup"><span data-stu-id="e5175-105">Rich edit box</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="e5175-106">Sie können ein RichEditBox-Steuerelement verwenden, um Rich-Text-Dokumente zu bearbeiten, die formatierten Text, Hyperlinks und Bilder enthalten.</span><span class="sxs-lookup"><span data-stu-id="e5175-106">You can use a RichEditBox control to enter and edit rich text documents that contain formatted text, hyperlinks, and images.</span></span> <span data-ttu-id="e5175-107">Sie können den Schreibschutz für ein RichEditBox-Steuerelement aktivieren, indem Sie die IsReadOnly-Eigenschaft des Steuerelements auf **true** festlegen.</span><span class="sxs-lookup"><span data-stu-id="e5175-107">You can make a RichEditBox read-only by setting its IsReadOnly property to **true**.</span></span>

> <span data-ttu-id="e5175-108">**Wichtige APIs**: [RichEditBox-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx), [Document-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.document.aspx), [IsReadOnly-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isreadonly.aspx), [IsSpellCheckEnabled-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isspellcheckenabled.aspx)</span><span class="sxs-lookup"><span data-stu-id="e5175-108">**Important APIs**: [RichEditBox class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx), [Document property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.document.aspx), [IsReadOnly property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isreadonly.aspx), [IsSpellCheckEnabled property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isspellcheckenabled.aspx)</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="e5175-109">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="e5175-109">Is this the right control?</span></span>

<span data-ttu-id="e5175-110">Verwenden Sie **RichEditBox** zum Anzeigen und Bearbeiten von Textdateien.</span><span class="sxs-lookup"><span data-stu-id="e5175-110">Use a **RichEditBox** to display and edit text files.</span></span> <span data-ttu-id="e5175-111">RichEditBox wird nicht verwendet, um wie bei anderen Standard-Texteingabefeldern Benutzereingaben in der App abzurufen.</span><span class="sxs-lookup"><span data-stu-id="e5175-111">You don't use a RichEditBox to get user input into you app the way you use other standard text input boxes.</span></span> <span data-ttu-id="e5175-112">Es wird vielmehr dazu verwendet, mit Textdateien zu arbeiten, die von Ihrer App getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="e5175-112">Rather, you use it to work with text files that are separate from your app.</span></span> <span data-ttu-id="e5175-113">Normalerweise speichern Sie Text, der in einer RichEditBox eingegeben wird, in einer RTF-Datei.</span><span class="sxs-lookup"><span data-stu-id="e5175-113">You typically save text entered into a RichEditBox to a .rtf file.</span></span>
-   <span data-ttu-id="e5175-114">Wenn der Hauptzweck des mehrzeiligen Textfelds darin besteht, Dokumente zu erstellen (z. B. Blogeinträge oder die Inhalte einer E-Mail-Nachricht) und diese Dokumente Rich-Text erfordern, verwenden Sie ein Rich-Text-Feld.</span><span class="sxs-lookup"><span data-stu-id="e5175-114">If the primary purpose of the multi-line text box is for creating documents (such as blog entries or the contents of an email message), and those documents require rich text, use a rich text box.</span></span>
-   <span data-ttu-id="e5175-115">Wenn die Benutzer in der Lage sein sollen, ihre Texte zu formatieren, verwenden Sie ein Rich-Text-Feld.</span><span class="sxs-lookup"><span data-stu-id="e5175-115">If you want users to be able to format their text, use a rich text box.</span></span>
-   <span data-ttu-id="e5175-116">Wenn Texte erfasst werden, die nur genutzt und nicht für die Benutzer erneut angezeigt werden, verwenden Sie ein Nur-Text-Eingabesteuerelement.</span><span class="sxs-lookup"><span data-stu-id="e5175-116">When capturing text that will only be consumed and not redisplayed to users, use a plain text input control.</span></span>
-   <span data-ttu-id="e5175-117">Verwenden Sie in allen anderen Szenarien ein Nur-Text-Eingabesteuerelement.</span><span class="sxs-lookup"><span data-stu-id="e5175-117">For all other scenarios, use a plain text input control.</span></span>

<span data-ttu-id="e5175-118">Weitere Informationen zur Auswahl des passenden Textsteuerelements finden Sie im Artikel über [Textsteuerelemente](text-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e5175-118">For more info about choosing the right text control, see the [Text controls](text-controls.md) article.</span></span>

## <a name="examples"></a><span data-ttu-id="e5175-119">Beispiele</span><span class="sxs-lookup"><span data-stu-id="e5175-119">Examples</span></span>

<span data-ttu-id="e5175-120">In diesem Rich-Edit-Feld ist ein Rich-Text-Dokument geöffnet.</span><span class="sxs-lookup"><span data-stu-id="e5175-120">This rich edit box has a rich text document open in it.</span></span> <span data-ttu-id="e5175-121">Die Formatierungs- und Dateischaltflächen sind nicht Teil des Rich-Edit-Felds, Sie sollten aber zumindest grundlegende Formatierungsschaltflächen bereitstellen und ihre Aktionen implementieren.</span><span class="sxs-lookup"><span data-stu-id="e5175-121">The formatting and file buttons aren't part of the rich edit box, but you should provide at least a minimal set of styling buttons and implement their actions.</span></span>

![Ein Rich-Text-Feld mit einem geöffneten Dokument](images/rich-edit-box.png)

## <a name="create-a-rich-edit-box"></a><span data-ttu-id="e5175-123">Erstellen eines Rich-Edit-Felds</span><span class="sxs-lookup"><span data-stu-id="e5175-123">Create a rich edit box</span></span>

<span data-ttu-id="e5175-124">RichEditBox unterstützt standardmäßig die Rechtschreibprüfung.</span><span class="sxs-lookup"><span data-stu-id="e5175-124">By default, the RichEditBox supports spell checking.</span></span> <span data-ttu-id="e5175-125">Um die Rechtschreibprüfung zu deaktivieren, legen Sie die [IsSpellCheckEnabled](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isspellcheckenabled.aspx)-Eigenschaft auf **false** fest.</span><span class="sxs-lookup"><span data-stu-id="e5175-125">To disable the spell checker, set the [IsSpellCheckEnabled](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isspellcheckenabled.aspx) property to **false**.</span></span> <span data-ttu-id="e5175-126">Weitere Informationen finden Sie im Artikel [Richtlinien für die Rechtschreibprüfung](spell-checking-and-prediction.md).</span><span class="sxs-lookup"><span data-stu-id="e5175-126">For more info, see the [Guidelines for spell checking](spell-checking-and-prediction.md) article.</span></span>

<span data-ttu-id="e5175-127">Mit der [Document](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.document.aspx)-Eigenschaft von RichEditBox können Sie den Inhalt des Steuerelements abrufen.</span><span class="sxs-lookup"><span data-stu-id="e5175-127">You use the [Document](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.document.aspx) property of the RichEditBox to get its content.</span></span> <span data-ttu-id="e5175-128">Der Inhalt eines RichEditBox ist anders als das RichTextBlock-Steuerelement ein [Windows.UI.Text.ITextDocument](https://msdn.microsoft.com/library/windows/apps/xaml/bb774052.aspx)-Objekt, das [Windows.UI.Xaml.Documents.Block](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.block.aspx)-Objekte als Inhalte verwendet.</span><span class="sxs-lookup"><span data-stu-id="e5175-128">The content of a RichEditBox is a [Windows.UI.Text.ITextDocument](https://msdn.microsoft.com/library/windows/apps/xaml/bb774052.aspx) object, unlike the RichTextBlock control, which uses [Windows.UI.Xaml.Documents.Block](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.block.aspx) objects as its content.</span></span> <span data-ttu-id="e5175-129">Die ITextDocument-Schnittstelle bietet unter anderem folgende Möglichkeiten: Dokumente in einen Datenstrom laden und speichern, Textbereiche abrufen, die aktive Auswahl abrufen, Änderungen rückgängig machen und wiederholen, Standardformatierungsattribute festlegen usw.</span><span class="sxs-lookup"><span data-stu-id="e5175-129">The ITextDocument interface provides a way to load and save the document to a stream, retrieve text ranges, get the active selection, undo and redo changes, set default formatting attributes, and so on.</span></span>

<span data-ttu-id="e5175-130">Dieses Beispiel zeigt, wie Sie eine RTF-Datei (Rich Text Format) bearbeiten, sie in ein RichEditBox laden und speichern.</span><span class="sxs-lookup"><span data-stu-id="e5175-130">This example shows how to edit, load, and save a Rich Text Format (.rtf) file in a RichEditBox.</span></span>

```xaml
<RelativePanel Margin="20" HorizontalAlignment="Stretch">
    <RelativePanel.Resources>
        <Style TargetType="AppBarButton">
            <Setter Property="IsCompact" Value="True"/>
        </Style>
    </RelativePanel.Resources>
    <AppBarButton x:Name="openFileButton" Icon="OpenFile"
                  Click="OpenButton_Click" ToolTipService.ToolTip="Open file"/>
    <AppBarButton Icon="Save" Click="SaveButton_Click"
                  ToolTipService.ToolTip="Save file"
                  RelativePanel.RightOf="openFileButton" Margin="8,0,0,0"/>

    <AppBarButton Icon="Bold" Click="BoldButton_Click" ToolTipService.ToolTip="Bold"
                  RelativePanel.LeftOf="italicButton" Margin="0,0,8,0"/>
    <AppBarButton x:Name="italicButton" Icon="Italic" Click="ItalicButton_Click"
                  ToolTipService.ToolTip="Italic" RelativePanel.LeftOf="underlineButton" Margin="0,0,8,0"/>
    <AppBarButton x:Name="underlineButton" Icon="Underline" Click="UnderlineButton_Click"
                  ToolTipService.ToolTip="Underline" RelativePanel.AlignRightWithPanel="True"/>

    <RichEditBox x:Name="editor" Height="200" RelativePanel.Below="openFileButton"
                 RelativePanel.AlignLeftWithPanel="True" RelativePanel.AlignRightWithPanel="True"/>
</RelativePanel>
```


```csharp
private async void OpenButton_Click(object sender, RoutedEventArgs e)
{
    // Open a text file.
    Windows.Storage.Pickers.FileOpenPicker open =
        new Windows.Storage.Pickers.FileOpenPicker();
    open.SuggestedStartLocation =
        Windows.Storage.Pickers.PickerLocationId.DocumentsLibrary;
    open.FileTypeFilter.Add(".rtf");

    Windows.Storage.StorageFile file = await open.PickSingleFileAsync();

    if (file != null)
    {
        try
        {
            Windows.Storage.Streams.IRandomAccessStream randAccStream =
        await file.OpenAsync(Windows.Storage.FileAccessMode.Read);

            // Load the file into the Document property of the RichEditBox.
            editor.Document.LoadFromStream(Windows.UI.Text.TextSetOptions.FormatRtf, randAccStream);
        }
        catch (Exception)
        {
            ContentDialog errorDialog = new ContentDialog()
            {
                Title = "File open error",
                Content = "Sorry, I couldn't open the file.",
                PrimaryButtonText = "Ok"
            };

            await errorDialog.ShowAsync();
        }
    }
}

private async void SaveButton_Click(object sender, RoutedEventArgs e)
{
    Windows.Storage.Pickers.FileSavePicker savePicker = new Windows.Storage.Pickers.FileSavePicker();
    savePicker.SuggestedStartLocation = Windows.Storage.Pickers.PickerLocationId.DocumentsLibrary;

    // Dropdown of file types the user can save the file as
    savePicker.FileTypeChoices.Add("Rich Text", new List<string>() { ".rtf" });

    // Default file name if the user does not type one in or select a file to replace
    savePicker.SuggestedFileName = "New Document";

    Windows.Storage.StorageFile file = await savePicker.PickSaveFileAsync();
    if (file != null)
    {
        // Prevent updates to the remote version of the file until we
        // finish making changes and call CompleteUpdatesAsync.
        Windows.Storage.CachedFileManager.DeferUpdates(file);
        // write to file
        Windows.Storage.Streams.IRandomAccessStream randAccStream =
            await file.OpenAsync(Windows.Storage.FileAccessMode.ReadWrite);

        editor.Document.SaveToStream(Windows.UI.Text.TextGetOptions.FormatRtf, randAccStream);

        // Let Windows know that we're finished changing the file so the
        // other app can update the remote version of the file.
        Windows.Storage.Provider.FileUpdateStatus status = await Windows.Storage.CachedFileManager.CompleteUpdatesAsync(file);
        if (status != Windows.Storage.Provider.FileUpdateStatus.Complete)
        {
            Windows.UI.Popups.MessageDialog errorBox =
                new Windows.UI.Popups.MessageDialog("File " + file.Name + " couldn't be saved.");
            await errorBox.ShowAsync();
        }
    }
}

private void BoldButton_Click(object sender, RoutedEventArgs e)
{
    Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
    if (selectedText != null)
    {
        Windows.UI.Text.ITextCharacterFormat charFormatting = selectedText.CharacterFormat;
        charFormatting.Bold = Windows.UI.Text.FormatEffect.Toggle;
        selectedText.CharacterFormat = charFormatting;
    }
}

private void ItalicButton_Click(object sender, RoutedEventArgs e)
{
    Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
    if (selectedText != null)
    {
        Windows.UI.Text.ITextCharacterFormat charFormatting = selectedText.CharacterFormat;
        charFormatting.Italic = Windows.UI.Text.FormatEffect.Toggle;
        selectedText.CharacterFormat = charFormatting;
    }
}

private void UnderlineButton_Click(object sender, RoutedEventArgs e)
{
    Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
    if (selectedText != null)
    {
        Windows.UI.Text.ITextCharacterFormat charFormatting = selectedText.CharacterFormat;
        if (charFormatting.Underline == Windows.UI.Text.UnderlineType.None)
        {
            charFormatting.Underline = Windows.UI.Text.UnderlineType.Single;
        }
        else {
            charFormatting.Underline = Windows.UI.Text.UnderlineType.None;
        }
        selectedText.CharacterFormat = charFormatting;
    }
}
```

## <a name="choose-the-right-keyboard-for-your-text-control"></a><span data-ttu-id="e5175-131">Auswählen der richtigen Tastatur für das Textsteuerelement</span><span class="sxs-lookup"><span data-stu-id="e5175-131">Choose the right keyboard for your text control</span></span>

<span data-ttu-id="e5175-132">Um Benutzern die Eingabe von Daten mit der Bildschirmtastatur oder dem Soft Input Panel (SIP) zu erleichtern, können Sie den Eingabeumfang des Textsteuerelements an die Art der Daten anpassen, die der Benutzer vermutlich eingeben wird.</span><span class="sxs-lookup"><span data-stu-id="e5175-132">To help users to enter data using the touch keyboard, or Soft Input Panel (SIP), you can set the input scope of the text control to match the kind of data the user is expected to enter.</span></span> <span data-ttu-id="e5175-133">Das Standardtastaturlayout ist in der Regel für die Arbeit mit Rich-Text-Dokumenten geeignet.</span><span class="sxs-lookup"><span data-stu-id="e5175-133">The default keyboard layout is usually appropriate for working with rich text documents.</span></span>

<span data-ttu-id="e5175-134">Weitere Informationen zur Verwendung von Eingabeumfängen finden Sie unter [Verwenden des Eingabeumfangs zum Ändern der Bildschirmtastatur](https://msdn.microsoft.com/library/windows/apps/mt280229).</span><span class="sxs-lookup"><span data-stu-id="e5175-134">For more info about how to use input scopes, see [Use input scope to change the touch keyboard](https://msdn.microsoft.com/library/windows/apps/mt280229).</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="e5175-135">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="e5175-135">Do's and don'ts</span></span>

-   <span data-ttu-id="e5175-136">Wenn Sie ein Rich-Text-Feld erstellen, sollten Sie Stilschaltflächen bereitstellen und die entsprechenden Aktionen implementieren.</span><span class="sxs-lookup"><span data-stu-id="e5175-136">When you create a rich text box, provide styling buttons and implement their actions.</span></span>
-   <span data-ttu-id="e5175-137">Verwenden Sie eine Schriftart, die mit dem Stil der App konsistent ist.</span><span class="sxs-lookup"><span data-stu-id="e5175-137">Use a font that's consistent with the style of your app.</span></span>
-   <span data-ttu-id="e5175-138">Legen Sie die Höhe des Textsteuerelements so fest, dass genügend Platz für typische Einträge vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="e5175-138">Make the height of the text control tall enough to accommodate typical entries.</span></span>
-   <span data-ttu-id="e5175-139">Die Höhe der Texteingabesteuerelemente sollte sich während der Benutzereingabe nicht verändern.</span><span class="sxs-lookup"><span data-stu-id="e5175-139">Don't let your text input controls grow in height while users type.</span></span>
-   <span data-ttu-id="e5175-140">Verwenden Sie kein mehrzeiliges Textfeld, wenn die Benutzer nur eine Zeile benötigen.</span><span class="sxs-lookup"><span data-stu-id="e5175-140">Don't use a multi-line text box when users only need a single line.</span></span>
-   <span data-ttu-id="e5175-141">Verwenden Sie kein Rich-Text-Steuerelement, wenn ein Nur-Text-Steuerelement ausreicht.</span><span class="sxs-lookup"><span data-stu-id="e5175-141">Don't use a rich text control if a plain text control is adequate.</span></span>


## <a name="related-articles"></a><span data-ttu-id="e5175-142">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="e5175-142">Related articles</span></span>

* [<span data-ttu-id="e5175-143">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="e5175-143">Text controls</span></span>](text-controls.md)
- [<span data-ttu-id="e5175-144">Richtlinien für die Rechtschreibprüfung</span><span class="sxs-lookup"><span data-stu-id="e5175-144">Guidelines for spell checking</span></span>](spell-checking-and-prediction.md)
- [<span data-ttu-id="e5175-145">Hinzufügen von Suchfunktionen</span><span class="sxs-lookup"><span data-stu-id="e5175-145">Adding search</span></span>](search.md)
- [<span data-ttu-id="e5175-146">Richtlinien für die Texteingabe</span><span class="sxs-lookup"><span data-stu-id="e5175-146">Guidelines for text input</span></span>](text-controls.md)
- [<span data-ttu-id="e5175-147">TextBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="e5175-147">TextBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209683)
- [<span data-ttu-id="e5175-148">Windows.UI.Xaml.Controls PasswordBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="e5175-148">Windows.UI.Xaml.Controls PasswordBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227519)
