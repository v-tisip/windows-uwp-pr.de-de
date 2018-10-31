---
author: Karl-Bridge-Microsoft
Description: UWP apps that support Windows Ink can serialize and deserialize ink strokes to an Ink Serialized Format (ISF) file. The ISF file is a GIF image with additional metadata for all ink stroke properties and behaviors. Apps that are not ink-enabled, can view the static GIF image, including alpha-channel background transparency.
title: Speichern und Abrufen der Daten zu Windows Ink-Strichen
ms.assetid: C96C9D2F-DB69-4883-9809-4A0DF7CEC506
label: Store and retrieve Windows Ink stroke data
template: detail.hbs
keywords: Windows Ink, Windows-Freihandeingabe, DirectInk, InkPresenter, InkCanvas, ISF, serialisiertes Freihandformat, Benutzerinteraktion, Eingabe
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 946e8421cf21c37c929e7a9f9687117c3d7aca92
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5833260"
---
# <a name="store-and-retrieve-windows-ink-stroke-data"></a><span data-ttu-id="aef6c-103">Speichern und Abrufen der Daten zu Windows Ink-Strichen</span><span class="sxs-lookup"><span data-stu-id="aef6c-103">Store and retrieve Windows Ink stroke data</span></span>


<span data-ttu-id="aef6c-104">UWP-Apps, die Windows Ink unterstützen, können Freihandstriche in eine serialisierte Freihandformatdatei (Ink Serialized Format-Datei, ISF-Datei) serialisieren und aus dieser deserialisieren.</span><span class="sxs-lookup"><span data-stu-id="aef6c-104">UWP apps that support Windows Ink can serialize and deserialize ink strokes to an Ink Serialized Format (ISF) file.</span></span> <span data-ttu-id="aef6c-105">Die ISF-Datei ist eine GIF-Bild mit zusätzlichen Metadaten für alle Eigenschaften und Verhaltensweisen von Freihandstrichen.</span><span class="sxs-lookup"><span data-stu-id="aef6c-105">The ISF file is a GIF image with additional metadata for all ink stroke properties and behaviors.</span></span> <span data-ttu-id="aef6c-106">Apps ohne Unterstützung der Freihandeingabe können das statische GIF-Bild, einschließlich Alphakanal-Hintergrundtransparenz, anzeigen.</span><span class="sxs-lookup"><span data-stu-id="aef6c-106">Apps that are not ink-enabled, can view the static GIF image, including alpha-channel background transparency.</span></span>

> [!NOTE]
> <span data-ttu-id="aef6c-107">Bei ISF handelt es sich um die kompakteste permanente Freihanddarstellung.</span><span class="sxs-lookup"><span data-stu-id="aef6c-107">ISF is the most compact persistent representation of ink.</span></span> <span data-ttu-id="aef6c-108">Sie kann in ein binäres Dokumentformat, z.B. in eine GIF-Datei, eingebettet oder direkt in der Zwischenablage platziert werden.</span><span class="sxs-lookup"><span data-stu-id="aef6c-108">It can be embedded within a binary document format, such as a GIF file, or placed directly on the Clipboard.</span></span>

> <span data-ttu-id="aef6c-109">**Wichtige APIs**: [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535), [**Windows.UI.Input.Inking**](https://msdn.microsoft.com/library/windows/apps/br208524)</span><span class="sxs-lookup"><span data-stu-id="aef6c-109">**Important APIs**: [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535), [**Windows.UI.Input.Inking**](https://msdn.microsoft.com/library/windows/apps/br208524)</span></span>

## <a name="save-ink-strokes-to-a-file"></a><span data-ttu-id="aef6c-110">Speichern von Freihandstrichen in einer Datei</span><span class="sxs-lookup"><span data-stu-id="aef6c-110">Save ink strokes to a file</span></span>

<span data-ttu-id="aef6c-111">Hier wird veranschaulicht, wie Sie in einem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement gezeichnete Freihandstriche speichern.</span><span class="sxs-lookup"><span data-stu-id="aef6c-111">Here, we demonstrate how to save ink strokes drawn on an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span>

**<span data-ttu-id="aef6c-112">Laden Sie dieses Beispiel unter [Speichern und Laden von Freihandstrichen aus einer ISF-Datei (Ink Serialized Format)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="aef6c-112">Download this sample from [Save and load ink strokes from an Ink Serialized Format (ISF) file](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store.zip)</span></span>**

1.  <span data-ttu-id="aef6c-113">Zuerst wird die Benutzeroberfläche eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="aef6c-113">First, we set up the UI.</span></span>

    <span data-ttu-id="aef6c-114">Die Benutzeroberfläche enthält die Schaltflächen „Speichern“, „Laden“ und „Löschen“ sowie den [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535).</span><span class="sxs-lookup"><span data-stu-id="aef6c-114">The UI includes "Save", "Load", and "Clear" buttons, and the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535).</span></span>
```    XAML
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <StackPanel x:Name="HeaderPanel" Orientation="Horizontal" Grid.Row="0">
            <TextBlock x:Name="Header" 
                       Text="Basic ink store sample" 
                       Style="{ThemeResource HeaderTextBlockStyle}" 
                       Margin="10,0,0,0" />
            <Button x:Name="btnSave" 
                    Content="Save" 
                    Margin="50,0,10,0"/>
            <Button x:Name="btnLoad" 
                    Content="Load" 
                    Margin="50,0,10,0"/>
            <Button x:Name="btnClear" 
                    Content="Clear" 
                    Margin="50,0,10,0"/>
        </StackPanel>
        <Grid Grid.Row="1">
            <InkCanvas x:Name="inkCanvas" />
        </Grid>
    </Grid>
```

2.  <span data-ttu-id="aef6c-115">Dann werden einige grundlegende Verhalten für Freihandeingaben festgelegt.</span><span class="sxs-lookup"><span data-stu-id="aef6c-115">We then set some basic ink input behaviors.</span></span>

    <span data-ttu-id="aef6c-116">Der [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) ist so konfiguriert, dass die Eingabedaten von Stift und Maus als Freihandstriche ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)) interpretiert werden, und es werden Listener für die Klickereignisse der Schaltflächen deklariert.</span><span class="sxs-lookup"><span data-stu-id="aef6c-116">The [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) is configured to interpret input data from both pen and mouse as ink strokes ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)), and listeners for the click events on the buttons are declared.</span></span>
```csharp
public MainPage()
    {
        this.InitializeComponent();

        // Set supported inking device types.
        inkCanvas.InkPresenter.InputDeviceTypes =
            Windows.UI.Core.CoreInputDeviceTypes.Mouse |
            Windows.UI.Core.CoreInputDeviceTypes.Pen;

        // Listen for button click to initiate save.
        btnSave.Click += btnSave_Click;
        // Listen for button click to initiate load.
        btnLoad.Click += btnLoad_Click;
        // Listen for button click to clear ink canvas.
        btnClear.Click += btnClear_Click;
    }
```

3.  <span data-ttu-id="aef6c-117">Schließlich werden die Freihanddaten im Click-Ereignishandler der Schaltfläche **Speichern** gespeichert.</span><span class="sxs-lookup"><span data-stu-id="aef6c-117">Finally, we save the ink in the click event handler of the **Save** button.</span></span>

    <span data-ttu-id="aef6c-118">Mit einem [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871) kann der Benutzer die Datei und den Speicherort der Freihanddaten auswählen.</span><span class="sxs-lookup"><span data-stu-id="aef6c-118">A [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871) lets the user select both the file and the location where the ink data is saved.</span></span>

    <span data-ttu-id="aef6c-119">Wenn eine Datei ausgewählt ist, wird ein auf [**ReadWrite**](https://msdn.microsoft.com/library/windows/apps/br241731) festgelegter [**IRandomAccessStream**](https://msdn.microsoft.com/library/windows/apps/br241635)-Datenstrom geöffnet.</span><span class="sxs-lookup"><span data-stu-id="aef6c-119">Once a file is selected, we open an [**IRandomAccessStream**](https://msdn.microsoft.com/library/windows/apps/br241731) stream set to [**ReadWrite**](https://msdn.microsoft.com/library/windows/apps/br241635).</span></span>

    <span data-ttu-id="aef6c-120">Anschließend wird [**SaveAsync**](https://msdn.microsoft.com/library/windows/apps/br242114) aufgerufen, um die vom [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) verwalteten Freihandstriche in den Datenstrom zu serialisieren.</span><span class="sxs-lookup"><span data-stu-id="aef6c-120">We then call [**SaveAsync**](https://msdn.microsoft.com/library/windows/apps/br242114) to serialize the ink strokes managed by the [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) to the stream.</span></span>

```csharp
// Save ink data to a file.
    private async void btnSave_Click(object sender, RoutedEventArgs e)
    {
        // Get all strokes on the InkCanvas.
        IReadOnlyList<InkStroke> currentStrokes = inkCanvas.InkPresenter.StrokeContainer.GetStrokes();

        // Strokes present on ink canvas.
        if (currentStrokes.Count > 0)
        {
            // Let users choose their ink file using a file picker.
            // Initialize the picker.
            Windows.Storage.Pickers.FileSavePicker savePicker = 
                new Windows.Storage.Pickers.FileSavePicker();
            savePicker.SuggestedStartLocation = 
                Windows.Storage.Pickers.PickerLocationId.DocumentsLibrary;
            savePicker.FileTypeChoices.Add(
                "GIF with embedded ISF", 
                new List<string>() { ".gif" });
            savePicker.DefaultFileExtension = ".gif";
            savePicker.SuggestedFileName = "InkSample";

            // Show the file picker.
            Windows.Storage.StorageFile file = 
                await savePicker.PickSaveFileAsync();
            // When chosen, picker returns a reference to the selected file.
            if (file != null)
            {
                // Prevent updates to the file until updates are 
                // finalized with call to CompleteUpdatesAsync.
                Windows.Storage.CachedFileManager.DeferUpdates(file);
                // Open a file stream for writing.
                IRandomAccessStream stream = await file.OpenAsync(Windows.Storage.FileAccessMode.ReadWrite);
                // Write the ink strokes to the output stream.
                using (IOutputStream outputStream = stream.GetOutputStreamAt(0))
                {
                    await inkCanvas.InkPresenter.StrokeContainer.SaveAsync(outputStream);
                    await outputStream.FlushAsync();
                }
                stream.Dispose();

                // Finalize write so other apps can update file.
                Windows.Storage.Provider.FileUpdateStatus status =
                    await Windows.Storage.CachedFileManager.CompleteUpdatesAsync(file);

                if (status == Windows.Storage.Provider.FileUpdateStatus.Complete)
                {
                    // File saved.
                }
                else
                {
                    // File couldn't be saved.
                }
            }
            // User selects Cancel and picker returns null.
            else
            {
                // Operation cancelled.
            }
        }
    }
```

> [!NOTE]
> <span data-ttu-id="aef6c-121">Zum Speichern von Freihanddaten wird nur das Format GIF unterstützt.</span><span class="sxs-lookup"><span data-stu-id="aef6c-121">GIF is the only file format supported for saving ink data.</span></span> <span data-ttu-id="aef6c-122">Aus Gründen der Abwärtskompatibilität werden allerdings von der [**LoadAsync**](https://msdn.microsoft.com/library/windows/apps/hh701607)-Methode (im nächsten Abschnitt veranschaulicht) weitere Formate unterstützt.</span><span class="sxs-lookup"><span data-stu-id="aef6c-122">However, the [**LoadAsync**](https://msdn.microsoft.com/library/windows/apps/hh701607) method (demonstrated in the next section) does support additional formats for backward compatibility.</span></span>

## <a name="load-ink-strokes-from-a-file"></a><span data-ttu-id="aef6c-123">Laden von Freihanddaten aus einer Datei</span><span class="sxs-lookup"><span data-stu-id="aef6c-123">Load ink strokes from a file</span></span>

<span data-ttu-id="aef6c-124">Hier wird veranschaulicht, wie Freihandstriche aus einer Datei geladen und in einem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535)-Steuerelement gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="aef6c-124">Here, we demonstrate how to load ink strokes from a file and render them on an [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) control.</span></span>

**<span data-ttu-id="aef6c-125">Laden Sie dieses Beispiel unter [Speichern und Laden von Freihandstrichen aus einer ISF-Datei (Ink Serialized Format)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="aef6c-125">Download this sample from [Save and load ink strokes from an Ink Serialized Format (ISF) file](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store.zip)</span></span>**

1.  <span data-ttu-id="aef6c-126">Zuerst wird die Benutzeroberfläche eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="aef6c-126">First, we set up the UI.</span></span>

    <span data-ttu-id="aef6c-127">Die Benutzeroberfläche enthält die Schaltflächen „Speichern“, „Laden“ und „Löschen“ sowie den [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535).</span><span class="sxs-lookup"><span data-stu-id="aef6c-127">The UI includes "Save", "Load", and "Clear" buttons, and the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535).</span></span>
```    XAML
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <StackPanel x:Name="HeaderPanel" Orientation="Horizontal" Grid.Row="0">
            <TextBlock x:Name="Header" 
                       Text="Basic ink store sample" 
                       Style="{ThemeResource HeaderTextBlockStyle}" 
                       Margin="10,0,0,0" />
            <Button x:Name="btnSave" 
                    Content="Save" 
                    Margin="50,0,10,0"/>
            <Button x:Name="btnLoad" 
                    Content="Load" 
                    Margin="50,0,10,0"/>
            <Button x:Name="btnClear" 
                    Content="Clear" 
                    Margin="50,0,10,0"/>
        </StackPanel>
        <Grid Grid.Row="1">
            <InkCanvas x:Name="inkCanvas" />
        </Grid>
    </Grid>
```

2.  <span data-ttu-id="aef6c-128">Dann werden einige grundlegende Verhalten für Freihandeingaben festgelegt.</span><span class="sxs-lookup"><span data-stu-id="aef6c-128">We then set some basic ink input behaviors.</span></span>

    <span data-ttu-id="aef6c-129">Der [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) ist so konfiguriert, dass die Eingabedaten von Stift und Maus als Freihandstriche ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)) interpretiert werden, und es werden Listener für die Klickereignisse der Schaltflächen deklariert.</span><span class="sxs-lookup"><span data-stu-id="aef6c-129">The [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) is configured to interpret input data from both pen and mouse as ink strokes ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)), and listeners for the click events on the buttons are declared.</span></span>
```csharp
public MainPage()
    {
        this.InitializeComponent();

        // Set supported inking device types.
        inkCanvas.InkPresenter.InputDeviceTypes =
            Windows.UI.Core.CoreInputDeviceTypes.Mouse |
            Windows.UI.Core.CoreInputDeviceTypes.Pen;

        // Listen for button click to initiate save.
        btnSave.Click += btnSave_Click;
        // Listen for button click to initiate load.
        btnLoad.Click += btnLoad_Click;
        // Listen for button click to clear ink canvas.
        btnClear.Click += btnClear_Click;
    }
```

3.  <span data-ttu-id="aef6c-130">Schließlich werden die Freihanddaten im Click-Ereignishandler der Schaltfläche **Laden** geladen.</span><span class="sxs-lookup"><span data-stu-id="aef6c-130">Finally, we load the ink in the click event handler of the **Load** button.</span></span>

    <span data-ttu-id="aef6c-131">Mit einem [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) kann der Benutzer die Datei und den Speicherort auswählen, aus der bzw. dem die gespeicherten Freihanddaten abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="aef6c-131">A [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) lets the user select both the file and the location from where to retrieve the saved ink data.</span></span>

    <span data-ttu-id="aef6c-132">Wenn eine Datei ausgewählt ist, wird ein auf [**Read**](https://msdn.microsoft.com/library/windows/apps/br241635) festgelegter [**IRandomAccessStream**](https://msdn.microsoft.com/library/windows/apps/br241731)-Datenstrom geöffnet.</span><span class="sxs-lookup"><span data-stu-id="aef6c-132">Once a file is selected, we open an [**IRandomAccessStream**](https://msdn.microsoft.com/library/windows/apps/br241731) stream set to [**Read**](https://msdn.microsoft.com/library/windows/apps/br241635).</span></span>

    <span data-ttu-id="aef6c-133">Anschließend wird [**LoadAsync**](https://msdn.microsoft.com/library/windows/apps/hh701607) aufgerufen, um die gespeicherten Freihandstriche zu lesen, zu serialisieren und in den [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) zu laden.</span><span class="sxs-lookup"><span data-stu-id="aef6c-133">We then call [**LoadAsync**](https://msdn.microsoft.com/library/windows/apps/hh701607) to read, de-serialize, and load the saved ink strokes into the [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492).</span></span> <span data-ttu-id="aef6c-134">Das Laden der Striche in den **InkStrokeContainer** bewirkt, dass sie sofort vom [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) auf dem [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="aef6c-134">Loading the strokes into the **InkStrokeContainer** causes the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) to immediately render them to the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535).</span></span>

    > [!NOTE]
    > <span data-ttu-id="aef6c-135">Alle vorhandenen Striche im InkStrokeContainer werden gelöscht, bevor neue Striche geladen werden.</span><span class="sxs-lookup"><span data-stu-id="aef6c-135">All existing strokes in the InkStrokeContainer are cleared before new strokes are loaded.</span></span>

``` csharp
// Load ink data from a file.
private async void btnLoad_Click(object sender, RoutedEventArgs e)
{
    // Let users choose their ink file using a file picker.
    // Initialize the picker.
    Windows.Storage.Pickers.FileOpenPicker openPicker =
        new Windows.Storage.Pickers.FileOpenPicker();
    openPicker.SuggestedStartLocation =
        Windows.Storage.Pickers.PickerLocationId.DocumentsLibrary;
    openPicker.FileTypeFilter.Add(".gif");
    // Show the file picker.
    Windows.Storage.StorageFile file = await openPicker.PickSingleFileAsync();
    // User selects a file and picker returns a reference to the selected file.
    if (file != null)
    {
        // Open a file stream for reading.
        IRandomAccessStream stream = await file.OpenAsync(Windows.Storage.FileAccessMode.Read);
        // Read from file.
        using (var inputStream = stream.GetInputStreamAt(0))
        {
            await inkCanvas.InkPresenter.StrokeContainer.LoadAsync(inputStream);
        }
        stream.Dispose();
    }
    // User selects Cancel and picker returns null.
    else
    {
        // Operation cancelled.
    }
}
```

> [!NOTE]
> <span data-ttu-id="aef6c-136">Zum Speichern von Freihanddaten wird nur das Format GIF unterstützt.</span><span class="sxs-lookup"><span data-stu-id="aef6c-136">GIF is the only file format supported for saving ink data.</span></span> <span data-ttu-id="aef6c-137">Aus Gründen der Abwärtskompatibilität werden allerdings von der [**LoadAsync**](https://msdn.microsoft.com/library/windows/apps/hh701607)-Methode die folgenden Formate unterstützt.</span><span class="sxs-lookup"><span data-stu-id="aef6c-137">However, the [**LoadAsync**](https://msdn.microsoft.com/library/windows/apps/hh701607) method does support the following formats for backward compatibility.</span></span>

| <span data-ttu-id="aef6c-138">Format</span><span class="sxs-lookup"><span data-stu-id="aef6c-138">Format</span></span>                    | <span data-ttu-id="aef6c-139">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aef6c-139">Description</span></span> |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="aef6c-140">InkSerializedFormat</span><span class="sxs-lookup"><span data-stu-id="aef6c-140">InkSerializedFormat</span></span>       | <span data-ttu-id="aef6c-141">Gibt Freihandeingaben an, die mithilfe des ISF beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="aef6c-141">Specifies ink that is persisted using ISF.</span></span> <span data-ttu-id="aef6c-142">Dabei handelt es sich um die kompakteste permanente Freihanddarstellung.</span><span class="sxs-lookup"><span data-stu-id="aef6c-142">This is the most compact persistent representation of ink.</span></span> <span data-ttu-id="aef6c-143">Sie kann in ein binäres Dokumentformat eingebettet oder direkt in der Zwischenablage platziert werden.</span><span class="sxs-lookup"><span data-stu-id="aef6c-143">It can be embedded within a binary document format or placed directly on the Clipboard.</span></span>                                                                                                                                                                                                         |
| <span data-ttu-id="aef6c-144">Base64InkSerializedFormat</span><span class="sxs-lookup"><span data-stu-id="aef6c-144">Base64InkSerializedFormat</span></span> | <span data-ttu-id="aef6c-145">Gibt Freihandeingaben an, die durch Codieren von ISF als Base64-Datenstrom beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="aef6c-145">Specifies ink that is persisted by encoding the ISF as a base64 stream.</span></span> <span data-ttu-id="aef6c-146">Dieses Format wird bereitgestellt, damit Freihandeingaben direkt in einer XML-Datei oder HTML-Datei codiert werden können.</span><span class="sxs-lookup"><span data-stu-id="aef6c-146">This format is provided so ink can be encoded directly in an XML or HTML file.</span></span>                                                                                                                                                                                                                                                |
| <span data-ttu-id="aef6c-147">Gif</span><span class="sxs-lookup"><span data-stu-id="aef6c-147">Gif</span></span>                       | <span data-ttu-id="aef6c-148">Dieses Format definiert Freihandeingaben, die mithilfe einer GIF-Datei beibehalten werden, die ISF in Form von Metadaten enthält, die in die Datei eingebettet sind.</span><span class="sxs-lookup"><span data-stu-id="aef6c-148">Specifies ink that is persisted by using a GIF file that contains ISF as metadata embedded within the file.</span></span> <span data-ttu-id="aef6c-149">So ist es möglich, Freihandeingaben in Anwendungen anzuzeigen, die nicht über die Funktion zur Freihandeingabe verfügen, während die Eingaben beim Wechsel zu einer Anwendung mit Freihandeingabe in vollem Umfang erhalten bleiben.</span><span class="sxs-lookup"><span data-stu-id="aef6c-149">This enables ink to be viewed in applications that are not ink-enabled and maintain its full ink fidelity when it returns to an ink-enabled application.</span></span> <span data-ttu-id="aef6c-150">Das Format ermöglicht nicht nur die Verwendung in Anwendungen mit und ohne Freihandfunktion, sondern ist bestens geeignet für den Transport von Freihandinhalt innerhalb einer HTML-Datei.</span><span class="sxs-lookup"><span data-stu-id="aef6c-150">This format is ideal when transporting ink content within an HTML file and for making it usable by ink and non-ink applications.</span></span> |
| <span data-ttu-id="aef6c-151">Base64Gif</span><span class="sxs-lookup"><span data-stu-id="aef6c-151">Base64Gif</span></span>                 | <span data-ttu-id="aef6c-152">Dieses Format definiert Freihandeingaben, die mithilfe einer Base64-codierten verstärkten GIF-Datei beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="aef6c-152">Specifies ink that is persisted by using a base64-encoded fortified GIF.</span></span> <span data-ttu-id="aef6c-153">Dieses Format wird bereitgestellt, wenn Freihandeingaben direkt in einer XML- oder HTML-Datei codiert werden müssen, um sie später in ein Bild zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="aef6c-153">This format is provided when ink is to be encoded directly in an XML or HTML file for later conversion into an image.</span></span> <span data-ttu-id="aef6c-154">Dieses Format kann beispielsweise in einem XML-Format verwendet werden, das erstellt wurde, um alle Freihandinformationen zu speichern, und das verwendet wird, um HTML über XSLT (Extensible Stylesheet Language Transformations) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="aef6c-154">A possible use of this is in an XML format generated to contain all ink information and used to generate HTML through Extensible Stylesheet Language Transformations (XSLT).</span></span> 

## <a name="copy-and-paste-ink-strokes-with-the-clipboard"></a><span data-ttu-id="aef6c-155">Kopieren und Einfügen von Freihandstrichen mit der Zwischenablage</span><span class="sxs-lookup"><span data-stu-id="aef6c-155">Copy and paste ink strokes with the clipboard</span></span>

<span data-ttu-id="aef6c-156">Hier wird veranschaulicht, wie Sie mit der Zwischenablage Freihandstriche zwischen Apps übertragen.</span><span class="sxs-lookup"><span data-stu-id="aef6c-156">Here, we demonstrate how to use the clipboard to transfer ink strokes between apps.</span></span>

<span data-ttu-id="aef6c-157">Damit die Zwischenablagefunktion unterstützt wird, müssen für die integrierten Befehle zum Ausschneiden und Kopieren von [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492)-Inhalten ein oder mehrere Freihandstriche ausgewählt sein.</span><span class="sxs-lookup"><span data-stu-id="aef6c-157">To support clipboard functionality, the built-in [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) cut and copy commands require one or more ink strokes be selected.</span></span>

<span data-ttu-id="aef6c-158">In diesem Beispiel wird die Strichauswahl aktiviert, wenn die Eingabe mit einer Zeichenstift-Drucktaste (oder der rechten Maustaste) geändert wird.</span><span class="sxs-lookup"><span data-stu-id="aef6c-158">For this example, we enable stroke selection when input is modified with a pen barrel button (or right mouse button).</span></span> <span data-ttu-id="aef6c-159">Ein vollständiges Beispiel für das Implementieren der Strichauswahl finden Sie unter „Weitergabe der Eingabe für die erweiterte Verarbeitung“ in [Zeichen- und Eingabestiftinteraktionen](pen-and-stylus-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="aef6c-159">For a complete example of how to implement stroke selection, see Pass-through input for advanced processing in [Pen and stylus interactions](pen-and-stylus-interactions.md).</span></span>

**<span data-ttu-id="aef6c-160">Laden Sie dieses Beispiel unter [Speichern und Laden von Freihandstrichen aus der Zwischenablage](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store-clipboard.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="aef6c-160">Download this sample from [Save and load ink strokes from the clipboard](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store-clipboard.zip)</span></span>**

1.  <span data-ttu-id="aef6c-161">Zuerst wird die Benutzeroberfläche eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="aef6c-161">First, we set up the UI.</span></span>

    <span data-ttu-id="aef6c-162">Die Benutzeroberfläche enthält die Schaltflächen „Ausschneiden“, „Kopiere“, „Einfügen“ und „Löschen“ sowie den [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) und einen Auswahlzeichenbereich.</span><span class="sxs-lookup"><span data-stu-id="aef6c-162">The UI includes "Cut", "Copy", "Paste", and "Clear" buttons, along with the [**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/dn858535) and a selection canvas.</span></span>
```    XAML
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <StackPanel x:Name="HeaderPanel" Orientation="Horizontal" Grid.Row="0">
            <TextBlock x:Name="tbHeader" 
                       Text="Basic ink store sample" 
                       Style="{ThemeResource HeaderTextBlockStyle}" 
                       Margin="10,0,0,0" />
            <Button x:Name="btnCut" 
                    Content="Cut" 
                    Margin="20,0,10,0"/>
            <Button x:Name="btnCopy" 
                    Content="Copy" 
                    Margin="20,0,10,0"/>
            <Button x:Name="btnPaste" 
                    Content="Paste" 
                    Margin="20,0,10,0"/>
            <Button x:Name="btnClear" 
                    Content="Clear" 
                    Margin="20,0,10,0"/>
        </StackPanel>
        <Grid x:Name="gridCanvas" Grid.Row="1">
            <!-- Canvas for displaying selection UI. -->
            <Canvas x:Name="selectionCanvas"/>
            <!-- Inking area -->
            <InkCanvas x:Name="inkCanvas"/>
        </Grid>
    </Grid>
```

2.  <span data-ttu-id="aef6c-163">Dann werden einige grundlegende Verhalten für Freihandeingaben festgelegt.</span><span class="sxs-lookup"><span data-stu-id="aef6c-163">We then set some basic ink input behaviors.</span></span>

    <span data-ttu-id="aef6c-164">Die [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081)-Eigenschaft wird für die Interpretation von Eingabedaten von Stift oder Maus als Freihandstriche ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)) konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="aef6c-164">The [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn899081) is configured to interpret input data from both pen and mouse as ink strokes ([**InputDeviceTypes**](https://msdn.microsoft.com/library/windows/apps/dn922019)).</span></span> <span data-ttu-id="aef6c-165">Hier werden außerdem Listener für die Click-Ereignisse der Schaltflächen sowie Zeiger- und Strichereignisse für die Auswahlfunktion deklariert.</span><span class="sxs-lookup"><span data-stu-id="aef6c-165">Listeners for the click events on the buttons as well as pointer and stroke events for selection functionality are also declared here.</span></span>

    <span data-ttu-id="aef6c-166">Ein vollständiges Beispiel für das Implementieren der Strichauswahl finden Sie unter „Weitergabe der Eingabe für die erweiterte Verarbeitung“ in [Zeichen- und Eingabestiftinteraktionen](pen-and-stylus-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="aef6c-166">For a complete example of how to implement stroke selection, see Pass-through input for advanced processing in [Pen and stylus interactions](pen-and-stylus-interactions.md).</span></span>
```csharp
public MainPage()
    {
        this.InitializeComponent();

        // Set supported inking device types.
        inkCanvas.InkPresenter.InputDeviceTypes =
            Windows.UI.Core.CoreInputDeviceTypes.Mouse |
            Windows.UI.Core.CoreInputDeviceTypes.Pen;

        // Listen for button click to cut ink strokes.
        btnCut.Click += btnCut_Click;
        // Listen for button click to copy ink strokes.
        btnCopy.Click += btnCopy_Click;
        // Listen for button click to paste ink strokes.
        btnPaste.Click += btnPaste_Click;
        // Listen for button click to clear ink canvas.
        btnClear.Click += btnClear_Click;

        // By default, the InkPresenter processes input modified by 
        // a secondary affordance (pen barrel button, right mouse 
        // button, or similar) as ink.
        // To pass through modified input to the app for custom processing 
        // on the app UI thread instead of the background ink thread, set 
        // InputProcessingConfiguration.RightDragAction to LeaveUnprocessed.
        inkCanvas.InkPresenter.InputProcessingConfiguration.RightDragAction =
            InkInputRightDragAction.LeaveUnprocessed;

        // Listen for unprocessed pointer events from modified input.
        // The input is used to provide selection functionality.
        inkCanvas.InkPresenter.UnprocessedInput.PointerPressed +=
            UnprocessedInput_PointerPressed;
        inkCanvas.InkPresenter.UnprocessedInput.PointerMoved +=
            UnprocessedInput_PointerMoved;
        inkCanvas.InkPresenter.UnprocessedInput.PointerReleased +=
            UnprocessedInput_PointerReleased;

        // Listen for new ink or erase strokes to clean up selection UI.
        inkCanvas.InkPresenter.StrokeInput.StrokeStarted +=
            StrokeInput_StrokeStarted;
        inkCanvas.InkPresenter.StrokesErased +=
            InkPresenter_StrokesErased;
    }
```

3.  <span data-ttu-id="aef6c-167">Nachdem die Unterstützung für die Strichauswahl hinzugefügt wurde, wird schließlich die Zwischenablagefunktion in den Click-Ereignishandlern der Schaltflächen **Ausschneiden**, **Kopieren** und **Einfügen** implementiert.</span><span class="sxs-lookup"><span data-stu-id="aef6c-167">Finally, after adding stroke selection support, we implement clipboard functionality in the click event handlers of the **Cut**, **Copy**, and **Paste** buttons.</span></span>

    <span data-ttu-id="aef6c-168">Für die Schaltfläche „Ausschneiden“ wird zunächst [**CopySelectedToClipboard**](https://msdn.microsoft.com/library/windows/apps/br244232) für den [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) des [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="aef6c-168">For cut, we first call [**CopySelectedToClipboard**](https://msdn.microsoft.com/library/windows/apps/br244232) on the [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) of the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011).</span></span>

    <span data-ttu-id="aef6c-169">Anschließend wird [**DeleteSelected**](https://msdn.microsoft.com/library/windows/apps/br244233) aufgerufen, um die Striche aus dem Freihandeingabe-Zeichenbereich zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="aef6c-169">We then call [**DeleteSelected**](https://msdn.microsoft.com/library/windows/apps/br244233) to remove the strokes from the ink canvas.</span></span>

    <span data-ttu-id="aef6c-170">Schließlich werden alle Auswahlstriche aus dem Auswahlzeichenbereich gelöscht.</span><span class="sxs-lookup"><span data-stu-id="aef6c-170">Finally, we delete all selection strokes from the selection canvas.</span></span>
    
```csharp
private void btnCut_Click(object sender, RoutedEventArgs e)
    {
        inkCanvas.InkPresenter.StrokeContainer.CopySelectedToClipboard();
        inkCanvas.InkPresenter.StrokeContainer.DeleteSelected();
        ClearSelection();
    }
```
```csharp
// Clean up selection UI.
    private void ClearSelection()
    {
        var strokes = inkCanvas.InkPresenter.StrokeContainer.GetStrokes();
        foreach (var stroke in strokes)
        {
            stroke.Selected = false;
        }
        ClearDrawnBoundingRect();
    }

    private void ClearDrawnBoundingRect()
    {
        if (selectionCanvas.Children.Any())
        {
            selectionCanvas.Children.Clear();
            boundingRect = Rect.Empty;
        }
    }
```

<span data-ttu-id="aef6c-171">Zum Kopieren wird einfach [**CopySelectedToClipboard**](https://msdn.microsoft.com/library/windows/apps/br244232) für den [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) des [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="aef6c-171">For copy, we simply call [**CopySelectedToClipboard**](https://msdn.microsoft.com/library/windows/apps/br244232) on the [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) of the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011).</span></span>


```csharp
private void btnCopy_Click(object sender, RoutedEventArgs e)
    {
        inkCanvas.InkPresenter.StrokeContainer.CopySelectedToClipboard();
    }
```

<span data-ttu-id="aef6c-172">Zum Einfügen wird [**CanPasteFromClipboard**](https://msdn.microsoft.com/library/windows/apps/br208495) aufgerufen, um sicherzustellen, dass der Inhalt in der Zwischenablage in den Freihandeingabe-Zeichenbereich eingefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="aef6c-172">For paste, we call [**CanPasteFromClipboard**](https://msdn.microsoft.com/library/windows/apps/br208495) to ensure that the content on the clipboard can be pasted to the ink canvas.</span></span>

<span data-ttu-id="aef6c-173">Ist dies der Fall, wird [**PasteFromClipboard**](https://msdn.microsoft.com/library/windows/apps/br208503) aufgerufen, um die Freihandstriche aus der Zwischenablage in den [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) des [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011) einzufügen, der die Striche dann auf dem Zeichenbereich für die Freihandeingabe rendert.</span><span class="sxs-lookup"><span data-stu-id="aef6c-173">If so, we call [**PasteFromClipboard**](https://msdn.microsoft.com/library/windows/apps/br208503) to insert the clipboard ink strokes into the [**InkStrokeContainer**](https://msdn.microsoft.com/library/windows/apps/br208492) of the [**InkPresenter**](https://msdn.microsoft.com/library/windows/apps/dn922011), which then renders the strokes to the ink canvas.</span></span>

```csharp
private void btnPaste_Click(object sender, RoutedEventArgs e)
    {
        if (inkCanvas.InkPresenter.StrokeContainer.CanPasteFromClipboard())
        {
            inkCanvas.InkPresenter.StrokeContainer.PasteFromClipboard(
                new Point(0, 0));
        }
        else
        {
            // Cannot paste from clipboard.
        }
    }
```

## <a name="related-articles"></a><span data-ttu-id="aef6c-174">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="aef6c-174">Related articles</span></span>

* [<span data-ttu-id="aef6c-175">Zeichen- und Eingabestiftinteraktionen</span><span class="sxs-lookup"><span data-stu-id="aef6c-175">Pen and stylus interactions</span></span>](pen-and-stylus-interactions.md)

**<span data-ttu-id="aef6c-176">Themenbeispiele</span><span class="sxs-lookup"><span data-stu-id="aef6c-176">Topic samples</span></span>**
* [<span data-ttu-id="aef6c-177">Speichern und Laden von Freihandstrichen aus einer ISF-Datei (Ink Serialized Format)</span><span class="sxs-lookup"><span data-stu-id="aef6c-177">Save and load ink strokes from an Ink Serialized Format (ISF) file</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store.zip)
* [<span data-ttu-id="aef6c-178">Speichern und Laden von Freihandstrichen aus der Zwischenablage</span><span class="sxs-lookup"><span data-stu-id="aef6c-178">Save and load ink strokes from the clipboard</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store-clipboard.zip)

**<span data-ttu-id="aef6c-179">Andere Beispiele</span><span class="sxs-lookup"><span data-stu-id="aef6c-179">Other samples</span></span>**
* [<span data-ttu-id="aef6c-180">Einfaches Freihandbeispiel (C#/C++)</span><span class="sxs-lookup"><span data-stu-id="aef6c-180">Simple ink sample (C#/C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620312)
* [<span data-ttu-id="aef6c-181">Komplexes Freihandbeispiel (C++)</span><span class="sxs-lookup"><span data-stu-id="aef6c-181">Complex ink sample (C++)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620314)
* [<span data-ttu-id="aef6c-182">Freihandbeispiel (JavaScript)</span><span class="sxs-lookup"><span data-stu-id="aef6c-182">Ink sample (JavaScript)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620308)
* [<span data-ttu-id="aef6c-183">Lernprogramm „Erste Schritte:” Unterstützen von Freihandeingaben in Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="aef6c-183">Get Started Tutorial: Support ink in your UWP app</span></span>](https://aka.ms/appsample-ink)
* [<span data-ttu-id="aef6c-184">Malbuchbeispiel</span><span class="sxs-lookup"><span data-stu-id="aef6c-184">Coloring book sample</span></span>](https://aka.ms/cpubsample-coloringbook)
* [<span data-ttu-id="aef6c-185">Familiennotizbeispiel</span><span class="sxs-lookup"><span data-stu-id="aef6c-185">Family notes sample</span></span>](https://aka.ms/cpubsample-familynotessample)



