---
Description: You can use a RichEditBox control to enter and edit rich text documents that contain formatted text, hyperlinks, and images. You can make a RichEditBox read-only by setting its IsReadOnly property to true.
title: RichEditBox
ms.assetid: 4AFC0DFA-3B89-434D-9F86-4309CCFF7839
label: Rich edit box
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
pm-contact: miguelrb
design-contact: ksulliv
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: fea636f78f4430d5bf8917c1ed720faeac7c4017
ms.sourcegitcommit: a60ab85e9f2f9690e0141050ec3aa51f18ec61ec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "9036932"
---
# <a name="rich-edit-box"></a><span data-ttu-id="7e5f3-103">Rich-Edit-Feld</span><span class="sxs-lookup"><span data-stu-id="7e5f3-103">Rich edit box</span></span>

 

<span data-ttu-id="7e5f3-104">Sie können ein RichEditBox-Steuerelement verwenden, um Rich-Text-Dokumente zu bearbeiten, die formatierten Text, Hyperlinks und Bilder enthalten.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-104">You can use a RichEditBox control to enter and edit rich text documents that contain formatted text, hyperlinks, and images.</span></span> <span data-ttu-id="7e5f3-105">Sie können den Schreibschutz für ein RichEditBox-Steuerelement aktivieren, indem Sie die IsReadOnly-Eigenschaft des Steuerelements auf **true** festlegen.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-105">You can make a RichEditBox read-only by setting its IsReadOnly property to **true**.</span></span>

> <span data-ttu-id="7e5f3-106">**Wichtige APIs**: [RichEditBox-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx), [Document-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.document.aspx), [IsReadOnly-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isreadonly.aspx), [IsSpellCheckEnabled-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isspellcheckenabled.aspx)</span><span class="sxs-lookup"><span data-stu-id="7e5f3-106">**Important APIs**: [RichEditBox class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx), [Document property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.document.aspx), [IsReadOnly property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isreadonly.aspx), [IsSpellCheckEnabled property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isspellcheckenabled.aspx)</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="7e5f3-107">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="7e5f3-107">Is this the right control?</span></span>

<span data-ttu-id="7e5f3-108">Verwenden Sie **RichEditBox** zum Anzeigen und Bearbeiten von Textdateien.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-108">Use a **RichEditBox** to display and edit text files.</span></span> <span data-ttu-id="7e5f3-109">RichEditBox wird nicht verwendet, um wie bei anderen Standard-Texteingabefeldern Benutzereingaben in der App abzurufen.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-109">You don't use a RichEditBox to get user input into you app the way you use other standard text input boxes.</span></span> <span data-ttu-id="7e5f3-110">Es wird vielmehr dazu verwendet, mit Textdateien zu arbeiten, die von Ihrer App getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-110">Rather, you use it to work with text files that are separate from your app.</span></span> <span data-ttu-id="7e5f3-111">Normalerweise speichern Sie Text, der in einer RichEditBox eingegeben wird, in einer RTF-Datei.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-111">You typically save text entered into a RichEditBox to a .rtf file.</span></span>
-   <span data-ttu-id="7e5f3-112">Wenn der Hauptzweck des mehrzeiligen Textfelds darin besteht, Dokumente zu erstellen (z. B. Blogeinträge oder die Inhalte einer E-Mail-Nachricht) und diese Dokumente Rich-Text erfordern, verwenden Sie ein Rich-Text-Feld.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-112">If the primary purpose of the multi-line text box is for creating documents (such as blog entries or the contents of an email message), and those documents require rich text, use a rich text box.</span></span>
-   <span data-ttu-id="7e5f3-113">Wenn die Benutzer in der Lage sein sollen, ihre Texte zu formatieren, verwenden Sie ein Rich-Text-Feld.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-113">If you want users to be able to format their text, use a rich text box.</span></span>
-   <span data-ttu-id="7e5f3-114">Wenn Texte erfasst werden, die nur genutzt und nicht für die Benutzer erneut angezeigt werden, verwenden Sie ein Nur-Text-Eingabesteuerelement.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-114">When capturing text that will only be consumed and not redisplayed to users, use a plain text input control.</span></span>
-   <span data-ttu-id="7e5f3-115">Verwenden Sie in allen anderen Szenarien ein Nur-Text-Eingabesteuerelement.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-115">For all other scenarios, use a plain text input control.</span></span>

<span data-ttu-id="7e5f3-116">Weitere Informationen zur Auswahl des passenden Textsteuerelements finden Sie im Artikel über [Textsteuerelemente](text-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7e5f3-116">For more info about choosing the right text control, see the [Text controls](text-controls.md) article.</span></span>

## <a name="examples"></a><span data-ttu-id="7e5f3-117">Beispiele</span><span class="sxs-lookup"><span data-stu-id="7e5f3-117">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="7e5f3-118">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="7e5f3-118">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="7e5f3-119">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/RichEditBox">die App zu öffnen und RichEditBox in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-119">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/RichEditBox">open the app and see the RichEditBox in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="7e5f3-120">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="7e5f3-120">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Xaml-Controls-Gallery"><span data-ttu-id="7e5f3-121">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="7e5f3-121">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="7e5f3-122">In diesem Rich-Edit-Feld ist ein Rich-Text-Dokument geöffnet.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-122">This rich edit box has a rich text document open in it.</span></span> <span data-ttu-id="7e5f3-123">Die Formatierungs- und Dateischaltflächen sind nicht Teil des Rich-Edit-Felds, Sie sollten aber zumindest grundlegende Formatierungsschaltflächen bereitstellen und ihre Aktionen implementieren.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-123">The formatting and file buttons aren't part of the rich edit box, but you should provide at least a minimal set of styling buttons and implement their actions.</span></span>

![Ein Rich-Text-Feld mit einem geöffneten Dokument](images/rich-edit-box.png)

## <a name="create-a-rich-edit-box"></a><span data-ttu-id="7e5f3-125">Erstellen eines Rich-Edit-Felds</span><span class="sxs-lookup"><span data-stu-id="7e5f3-125">Create a rich edit box</span></span>

<span data-ttu-id="7e5f3-126">RichEditBox unterstützt standardmäßig die Rechtschreibprüfung.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-126">By default, the RichEditBox supports spell checking.</span></span> <span data-ttu-id="7e5f3-127">Um die Rechtschreibprüfung zu deaktivieren, legen Sie die [IsSpellCheckEnabled](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isspellcheckenabled.aspx)-Eigenschaft auf **false** fest.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-127">To disable the spell checker, set the [IsSpellCheckEnabled](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.isspellcheckenabled.aspx) property to **false**.</span></span> <span data-ttu-id="7e5f3-128">Weitere Informationen finden Sie im Artikel [Richtlinien für die Rechtschreibprüfung](text-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7e5f3-128">For more info, see the [Guidelines for spell checking](text-controls.md) article.</span></span>

<span data-ttu-id="7e5f3-129">Mit der [Document](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.document.aspx)-Eigenschaft von RichEditBox können Sie den Inhalt des Steuerelements abrufen.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-129">You use the [Document](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.document.aspx) property of the RichEditBox to get its content.</span></span> <span data-ttu-id="7e5f3-130">Der Inhalt eines RichEditBox ist anders als das RichTextBlock-Steuerelement ein [Windows.UI.Text.ITextDocument](https://msdn.microsoft.com/library/windows/apps/xaml/bb774052.aspx)-Objekt, das [Windows.UI.Xaml.Documents.Block](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.block.aspx)-Objekte als Inhalte verwendet.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-130">The content of a RichEditBox is a [Windows.UI.Text.ITextDocument](https://msdn.microsoft.com/library/windows/apps/xaml/bb774052.aspx) object, unlike the RichTextBlock control, which uses [Windows.UI.Xaml.Documents.Block](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.block.aspx) objects as its content.</span></span> <span data-ttu-id="7e5f3-131">Die ITextDocument-Schnittstelle bietet unter anderem folgende Möglichkeiten: Dokumente in einen Datenstrom laden und speichern, Textbereiche abrufen, die aktive Auswahl abrufen, Änderungen rückgängig machen und wiederholen, Standardformatierungsattribute festlegen usw.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-131">The ITextDocument interface provides a way to load and save the document to a stream, retrieve text ranges, get the active selection, undo and redo changes, set default formatting attributes, and so on.</span></span>

<span data-ttu-id="7e5f3-132">Dieses Beispiel zeigt, wie Sie eine RTF-Datei (Rich Text Format) bearbeiten, sie in ein RichEditBox laden und speichern.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-132">This example shows how to edit, load, and save a Rich Text Format (.rtf) file in a RichEditBox.</span></span>

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

## <a name="choose-the-right-keyboard-for-your-text-control"></a><span data-ttu-id="7e5f3-133">Auswählen der richtigen Tastatur für das Textsteuerelement</span><span class="sxs-lookup"><span data-stu-id="7e5f3-133">Choose the right keyboard for your text control</span></span>

<span data-ttu-id="7e5f3-134">Um Benutzern die Eingabe von Daten mit der Bildschirmtastatur oder dem Soft Input Panel (SIP) zu erleichtern, können Sie den Eingabeumfang des Textsteuerelements an die Art der Daten anpassen, die der Benutzer vermutlich eingeben wird.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-134">To help users to enter data using the touch keyboard, or Soft Input Panel (SIP), you can set the input scope of the text control to match the kind of data the user is expected to enter.</span></span> <span data-ttu-id="7e5f3-135">Das Standardtastaturlayout ist in der Regel für die Arbeit mit Rich-Text-Dokumenten geeignet.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-135">The default keyboard layout is usually appropriate for working with rich text documents.</span></span>

<span data-ttu-id="7e5f3-136">Weitere Informationen zur Verwendung von Eingabeumfängen finden Sie unter [Verwenden des Eingabeumfangs zum Ändern der Bildschirmtastatur](https://msdn.microsoft.com/library/windows/apps/mt280229).</span><span class="sxs-lookup"><span data-stu-id="7e5f3-136">For more info about how to use input scopes, see [Use input scope to change the touch keyboard](https://msdn.microsoft.com/library/windows/apps/mt280229).</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="7e5f3-137">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="7e5f3-137">Do's and don'ts</span></span>

- <span data-ttu-id="7e5f3-138">Wenn Sie ein Rich-Text-Feld erstellen, sollten Sie Stilschaltflächen bereitstellen und die entsprechenden Aktionen implementieren.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-138">When you create a rich text box, provide styling buttons and implement their actions.</span></span>
- <span data-ttu-id="7e5f3-139">Verwenden Sie eine Schriftart, die mit dem Stil der App konsistent ist.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-139">Use a font that's consistent with the style of your app.</span></span>
- <span data-ttu-id="7e5f3-140">Legen Sie die Höhe des Textsteuerelements so fest, dass genügend Platz für typische Einträge vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-140">Make the height of the text control tall enough to accommodate typical entries.</span></span>
- <span data-ttu-id="7e5f3-141">Die Höhe der Texteingabesteuerelemente sollte sich während der Benutzereingabe nicht verändern.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-141">Don't let your text input controls grow in height while users type.</span></span>
- <span data-ttu-id="7e5f3-142">Verwenden Sie kein mehrzeiliges Textfeld, wenn die Benutzer nur eine Zeile benötigen.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-142">Don't use a multi-line text box when users only need a single line.</span></span>
- <span data-ttu-id="7e5f3-143">Verwenden Sie kein Rich-Text-Steuerelement, wenn ein Nur-Text-Steuerelement ausreicht.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-143">Don't use a rich text control if a plain text control is adequate.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="7e5f3-144">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="7e5f3-144">Get the sample code</span></span>

- <span data-ttu-id="7e5f3-145">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Xaml-Controls-Gallery) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="7e5f3-145">[XAML Controls Gallery sample](https://github.com/Microsoft/Xaml-Controls-Gallery) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="7e5f3-146">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="7e5f3-146">Related articles</span></span>

- [<span data-ttu-id="7e5f3-147">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="7e5f3-147">Text controls</span></span>](text-controls.md)
- [<span data-ttu-id="7e5f3-148">Richtlinien für die Rechtschreibprüfung</span><span class="sxs-lookup"><span data-stu-id="7e5f3-148">Guidelines for spell checking</span></span>](text-controls.md)
- [<span data-ttu-id="7e5f3-149">Hinzufügen von Suchfunktionen</span><span class="sxs-lookup"><span data-stu-id="7e5f3-149">Adding search</span></span>](search.md)
- [<span data-ttu-id="7e5f3-150">Richtlinien für die Texteingabe</span><span class="sxs-lookup"><span data-stu-id="7e5f3-150">Guidelines for text input</span></span>](text-controls.md)
- [<span data-ttu-id="7e5f3-151">TextBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="7e5f3-151">TextBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209683)
- [<span data-ttu-id="7e5f3-152">Windows.UI.Xaml.Controls PasswordBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="7e5f3-152">Windows.UI.Xaml.Controls PasswordBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227519)
