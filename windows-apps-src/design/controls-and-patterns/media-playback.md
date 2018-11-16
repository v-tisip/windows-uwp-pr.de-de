---
author: Jwmsft
Description: The media player is used to view and listen to video, audio, and images.
title: Media Player
ms.assetid: 9AABB5DE-1D81-4791-AB47-7F058F64C491
dev.assetid: AF2F2008-9B53-430C-BBC3-8888F631B0B0
label: Media player
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 6df7d7dc7d35ed46f3f741bd1783b5af2755f0a2
ms.sourcegitcommit: 9f8010fe67bb3372db1840de9f0be36097ed6258
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7100663"
---
# <a name="media-player"></a><span data-ttu-id="52f1b-103">Media Player</span><span class="sxs-lookup"><span data-stu-id="52f1b-103">Media player</span></span>



<span data-ttu-id="52f1b-104">Der Media Player wird verwendet, um Videos und Audio anzuzeigen und zu hören.</span><span class="sxs-lookup"><span data-stu-id="52f1b-104">The media player is used to view and listen to video and audio.</span></span> <span data-ttu-id="52f1b-105">Die Medienwiedergabe kann inline (eingebettet auf einer Seite oder mit einer Gruppe von anderen Steuerelementen) oder in einer dedizierten Vollbildansicht erfolgen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-105">Media playback can be inline (embedded in a page or with a group of other controls) or in a dedicated full-screen view.</span></span> <span data-ttu-id="52f1b-106">Sie können die Schaltflächen des Players ändern, den Hintergrund der Steuerelementleiste ändern und Layouts wie gewünscht anordnen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-106">You can modify the player's button set, change the background of the control bar, and arrange layouts as you see fit.</span></span> <span data-ttu-id="52f1b-107">Beachten Sie jedoch, dass Benutzer eine Reihe grundlegender Steuerelemente (Wiedergabe/Pause, Zurückspringen, Vorwärts springen) erwarten.</span><span class="sxs-lookup"><span data-stu-id="52f1b-107">Just keep in mind that users expect a basic control set (play/pause, skip back, skip forward).</span></span>

![Media Player-Element mit Transportsteuerelementen](images/controls/mtc_double_video_inprod.png)

> <span data-ttu-id="52f1b-109">**Wichtige APIs**: [MediaPlayerElement-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx), [MediaTransportControls-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediatransportcontrols)</span><span class="sxs-lookup"><span data-stu-id="52f1b-109">**Important APIs**: [MediaPlayerElement class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx), [MediaTransportControls class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediatransportcontrols)</span></span>


> [!NOTE]
> <span data-ttu-id="52f1b-110">Das **MediaPlayerElement** steht erst ab Windows10, Version1607, zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="52f1b-110">**MediaPlayerElement** is only available in Windows 10, version 1607 and up.</span></span> <span data-ttu-id="52f1b-111">Bei der Entwicklung von Apps für Vorgängerversionen von Windows10 muss stattdessen das [MediaElement](https://msdn.microsoft.com/library/windows/apps/br242926) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="52f1b-111">If you are developing an app for an earlier version of Windows 10 you will need to use [MediaElement](https://msdn.microsoft.com/library/windows/apps/br242926) instead.</span></span> <span data-ttu-id="52f1b-112">Alle Empfehlungen auf dieser Seite gelten auch für das MediaElement.</span><span class="sxs-lookup"><span data-stu-id="52f1b-112">All of the recommendations on this page apply to MediaElement as well.</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="52f1b-113">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="52f1b-113">Is this the right control?</span></span>

<span data-ttu-id="52f1b-114">Verwenden Sie einen Mediaplayer, wenn Sie Audio- oder Videodateien in Ihrer App wiedergeben möchten.</span><span class="sxs-lookup"><span data-stu-id="52f1b-114">Use a media player when you want to play audio or video in your app.</span></span> <span data-ttu-id="52f1b-115">Verwenden Sie zum Anzeigen einer Sammlung von Bildern die [Flip-Ansicht](flipview.md).</span><span class="sxs-lookup"><span data-stu-id="52f1b-115">To display a collection of images, use a [Flip view](flipview.md).</span></span>

## <a name="examples"></a><span data-ttu-id="52f1b-116">Beispiele</span><span class="sxs-lookup"><span data-stu-id="52f1b-116">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="52f1b-117">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="52f1b-117">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="52f1b-118">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um die App zu öffnen und <a href="xamlcontrolsgallery:/item/MediaPlayerElement">MediaPlayerElement</a> oder <a href="xamlcontrolsgallery:/item/MediaPlayer">MediaPlayer</a> in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-118">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to open the app and see the <a href="xamlcontrolsgallery:/item/MediaPlayerElement">MediaPlayerElement</a> or <a href="xamlcontrolsgallery:/item/MediaPlayer">MediaPlayer</a> in action.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="52f1b-119">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="52f1b-119">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="52f1b-120">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="52f1b-120">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="52f1b-121">Ein Media Player in der Windows10-Erste Schritte-App.</span><span class="sxs-lookup"><span data-stu-id="52f1b-121">A media player in the Windows 10 Get Started app.</span></span>

![Ein Medienelement in der Windows 10-Erste Schritte-App.](images/control-examples/mtc_getstarted_example.png)

## <a name="create-a-media-player"></a><span data-ttu-id="52f1b-123">Erstellen eines Media Players</span><span class="sxs-lookup"><span data-stu-id="52f1b-123">Create a media player</span></span>
<span data-ttu-id="52f1b-124">Sie fügen Ihrer App Medien hinzu, indem Sie ein [MediaElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx)-Objekt in XAML erstellen und die [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) auf eine [MediaSource](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.aspx) festlegen, die auf eine Audio- oder Videodatei verweist.</span><span class="sxs-lookup"><span data-stu-id="52f1b-124">Add media to your app by creating a [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) object in XAML and set the [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) to a [MediaSource](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.aspx) that points to an audio or video file.</span></span>

<span data-ttu-id="52f1b-125">Mit diesem XAML-Code wird ein [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) erstellt, dessen [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx)-Eigenschaft auf den URI einer Videodatei festgelegt wird, bei der es sich um eine lokale Datei der App handelt.</span><span class="sxs-lookup"><span data-stu-id="52f1b-125">This XAML creates a [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) and sets its [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) property to the URI of a video file that's local to the app.</span></span> <span data-ttu-id="52f1b-126">Das **MediaPlayerElement** beginnt mit der Wiedergabe, wenn die Seite geladen wird.</span><span class="sxs-lookup"><span data-stu-id="52f1b-126">The **MediaPlayerElement** begins playing when the page loads.</span></span> <span data-ttu-id="52f1b-127">Um zu verhindern, dass die Medienwiedergabe sofort beginnt, können Sie die [Automatische Wiedergabe](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.autoplay.aspx) auf **false** setzen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-127">To suppress media from starting right away, you can set the [AutoPlay](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.autoplay.aspx) property to **false**.</span></span>

```xaml
<MediaPlayerElement x:Name="mediaSimple"
                    Source="Videos/video1.mp4"
                    Width="400" AutoPlay="True"/>
```

<span data-ttu-id="52f1b-128">Mit diesem XAML-Code wird ein [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) -Objekt mit aktivierten integrierten Transportsteuerelementen und mit einer [AutoPlay](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.autoplay.aspx)-Eigenschaft, die auf **false** festgelegt ist, erstellt.</span><span class="sxs-lookup"><span data-stu-id="52f1b-128">This XAML creates a [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) with the built in transport controls enabled and the [AutoPlay](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.autoplay.aspx) property set to **false.**</span></span>


```xaml
<MediaPlayerElement x:Name="mediaPlayer"
                    Source="Videos/video1.mp4"
                    Width="400"
                    AutoPlay="False"
                    AreTransportControlsEnabled="True"/>
```

### <a name="media-transport-controls"></a><span data-ttu-id="52f1b-129">Steuerelemente für den Medientransport</span><span class="sxs-lookup"><span data-stu-id="52f1b-129">Media transport controls</span></span>
<span data-ttu-id="52f1b-130">[MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) verfügt über integrierte Transportsteuerelemente für Wiedergabe, Beenden, Anhalten, Lautstärke, Stummschaltung, Suche/Status, Untertitel und Audiotitelauswahl.</span><span class="sxs-lookup"><span data-stu-id="52f1b-130">[MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) has built in transport controls that handle play, stop, pause, volume, mute, seeking/progress, closed captions, and audio track selection.</span></span> <span data-ttu-id="52f1b-131">Um diese Steuerelemente zu aktivieren, muss [AreTransportControlsEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.AreTransportControlsEnabled.aspx) auf **true** gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="52f1b-131">To enable these controls, set [AreTransportControlsEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.AreTransportControlsEnabled.aspx) to **true**.</span></span> <span data-ttu-id="52f1b-132">Um sie zu deaktivieren, setzen Sie **AreTransportControlsEnabled** auf **false**.</span><span class="sxs-lookup"><span data-stu-id="52f1b-132">To disable them, set **AreTransportControlsEnabled** to **false**.</span></span> <span data-ttu-id="52f1b-133">Die Mediensteuerungselemente werden durch die Klasse [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/dn831962) dargestellt.</span><span class="sxs-lookup"><span data-stu-id="52f1b-133">The transport controls are represented by the [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/dn831962) class.</span></span> <span data-ttu-id="52f1b-134">Sie können die Mediensteuerung unverändert verwenden oder auf verschiedene Weise anpassen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-134">You can use the transport controls as-is, or customize them in various ways.</span></span> <span data-ttu-id="52f1b-135">Weitere Informationen finden Sie in der Referenz zur Klasse [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/dn831962) und unter [Erstellen einer benutzerdefinierten Mediensteuerung](custom-transport-controls.md).</span><span class="sxs-lookup"><span data-stu-id="52f1b-135">For more info, see the [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/dn831962) class reference and [Create custom transport controls](custom-transport-controls.md).</span></span>

<span data-ttu-id="52f1b-136">Die Mediensteuerung unterstützt sowohl ein ein- als auch zweizeiliges Layout.</span><span class="sxs-lookup"><span data-stu-id="52f1b-136">The transport controls support single- and double-row layouts.</span></span> <span data-ttu-id="52f1b-137">Im ersten Beispiel sehen Sie ein einzeiliges-Layout mit der Wiedergabe/Pause-Schaltfläche links von der Medienzeitachse.</span><span class="sxs-lookup"><span data-stu-id="52f1b-137">The first example here is a single-row layout, with the play/pause button located to the left of the media timeline.</span></span> <span data-ttu-id="52f1b-138">Dieses Layout wird am besten für die Wiedergabe von Inlinemedien und kompakte Bildschirme reserviert.</span><span class="sxs-lookup"><span data-stu-id="52f1b-138">This layout is best reserved for inline media playback and compact screens.</span></span>

![Beispiel für MTC-Steuerelemente, einzelne Zeile](images/controls/mtc_single_inprod_02.png)

<span data-ttu-id="52f1b-140">Das Layout mit doppelzeiligen Steuerelementen (siehe unten) wird für die meisten Nutzungsszenarien empfohlen, insbesondere für größere Bildschirme.</span><span class="sxs-lookup"><span data-stu-id="52f1b-140">The double-row controls layout (below) is recommended for most usage scenarios, especially on larger screens.</span></span> <span data-ttu-id="52f1b-141">Dieses Layout bietet mehr Platz für Steuerelemente und erleichtert dem Benutzer die Bedienung der Zeitachse.</span><span class="sxs-lookup"><span data-stu-id="52f1b-141">This layout provides more space for controls and makes the timeline easier for the user to operate.</span></span>

![Beispiel für MTC-Steuerelemente, Doppelzeile](images/controls/mtc_double_inprod.png)

**<span data-ttu-id="52f1b-143">Mediensteuerung des Systems</span><span class="sxs-lookup"><span data-stu-id="52f1b-143">System media transport controls</span></span>**

<span data-ttu-id="52f1b-144">Das [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) wird automatisch in die Mediensteuerung des Systems integriert.</span><span class="sxs-lookup"><span data-stu-id="52f1b-144">[MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) is automatically integrated with the system media transport controls.</span></span> <span data-ttu-id="52f1b-145">Die Medientransportsteuerelemente des Systems sind die Steuerelemente, die angezeigt werden, wenn Hardwaretasten für Medien betätigt werden, z.B. die Medientasten auf Tastaturen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-145">The system media transport controls are the controls that pop up when hardware media keys are pressed, such as the media buttons on keyboards.</span></span> <span data-ttu-id="52f1b-146">Weitere Informationen finden Sie unter [SystemMediaTransportControls](https://msdn.microsoft.com/library/windows/apps/dn278677).</span><span class="sxs-lookup"><span data-stu-id="52f1b-146">For more info, see [SystemMediaTransportControls](https://msdn.microsoft.com/library/windows/apps/dn278677).</span></span>

> <span data-ttu-id="52f1b-147">**Hinweis**&nbsp;&nbsp; Das [MediaElement](https://msdn.microsoft.com/library/windows/apps/br242926) wird nicht automatisch in die Mediensteuerung des Systems integriert. Sie müssen diese Verbindung selbst herstellen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-147">**Note**&nbsp;&nbsp; [MediaElement](https://msdn.microsoft.com/library/windows/apps/br242926) does not automatically integrate with the system media transport controls so you must connect them yourself.</span></span> <span data-ttu-id="52f1b-148">Weitere Informationen finden Sie unter [Mediensteuerung des Systems](https://msdn.microsoft.com/library/windows/apps/mt228338).</span><span class="sxs-lookup"><span data-stu-id="52f1b-148">For more information, see [System Media Transport Controls](https://msdn.microsoft.com/library/windows/apps/mt228338).</span></span>


### <a name="set-the-media-source"></a><span data-ttu-id="52f1b-149">Festlegen der Medienquelle</span><span class="sxs-lookup"><span data-stu-id="52f1b-149">Set the media source</span></span>
<span data-ttu-id="52f1b-150">Um Dateien im Netzwerk oder in die App eingebettete Dateien wiederzugeben, legen Sie die [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx)-Eigenschaft auf eine [MediaSource](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.aspx) mit dem Pfad der Datei fest.</span><span class="sxs-lookup"><span data-stu-id="52f1b-150">To play files on the network or files embedded with the app, set the [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) property to a [MediaSource](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.aspx) with the path of the file.</span></span>

<span data-ttu-id="52f1b-151">**Tipp:** zum Öffnen von Dateien aus dem Internet müssen Sie die Funktion **Internet (Client)** in Ihrer app Manifest (Package.appxmanifest) deklarieren.</span><span class="sxs-lookup"><span data-stu-id="52f1b-151">**Tip**To open files from the internet, you need to declare the **Internet (Client)** capability in your app's manifest (Package.appxmanifest).</span></span> <span data-ttu-id="52f1b-152">Weitere Informationen zum Deklarieren von Funktionen finden Sie unter [Deklarieren von App-Funktionen](https://msdn.microsoft.com/library/windows/apps/mt270968).</span><span class="sxs-lookup"><span data-stu-id="52f1b-152">For more info about declaring capabilities, see [App capability declarations](https://msdn.microsoft.com/library/windows/apps/mt270968).</span></span>

 

<span data-ttu-id="52f1b-153">Dieser Code versucht, die [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx)-Eigenschaft des im XAML-Code definierten [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) auf den Pfad einer Datei festzulegen, der in ein [TextBox](https://msdn.microsoft.com/library/windows/apps/br209683)-Element eingegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="52f1b-153">This code attempts to set the [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) property of the [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) defined in XAML to the path of a file entered into a [TextBox](https://msdn.microsoft.com/library/windows/apps/br209683).</span></span>

```xaml
<TextBox x:Name="txtFilePath" Width="400"
         FontSize="20"
         KeyUp="TxtFilePath_KeyUp"
         Header="File path"
         PlaceholderText="Enter file path"/>
```

```csharp
private void TxtFilePath_KeyUp(object sender, KeyRoutedEventArgs e)
{
    if (e.Key == Windows.System.VirtualKey.Enter)
    {
        TextBox tbPath = sender as TextBox;

        if (tbPath != null)
        {
            LoadMediaFromString(tbPath.Text);
        }
    }
}

private void LoadMediaFromString(string path)
{
    try
    {
        Uri pathUri = new Uri(path);
        mediaPlayer.Source = MediaSource.CreateFromUri(pathUri);
    }
    catch (Exception ex)
    {
        if (ex is FormatException)
        {
            // handle exception.
            // For example: Log error or notify user problem with file
        }
    }
}
```

<span data-ttu-id="52f1b-154">Um die Medienquelle auf eine in die App eingebettete Mediendatei festzulegen, initialisieren Sie einen [Uri](https://msdn.microsoft.com/library/windows/apps/br226017) mit dem Pfadpräfix **ms-appx:///**, erstellen anschließend eine [MediaSource](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.aspx) mit dem URI und legen anschließend die [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) auf den URI fest.</span><span class="sxs-lookup"><span data-stu-id="52f1b-154">To set the media source to a media file embedded in the app, initialize a [Uri](https://msdn.microsoft.com/library/windows/apps/br226017) with the path prefixed with **ms-appx:///**, create a [MediaSource](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.aspx) with the Uri and then set the [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) to the Uri.</span></span> <span data-ttu-id="52f1b-155">Für eine Datei mit dem Namen **video1.mp4**, die sich in dem Unterordner **Videos** befindet, würde der Pfad beispielsweise wie folgt aussehen: **ms-appx:///Videos/video1.mp4**.</span><span class="sxs-lookup"><span data-stu-id="52f1b-155">For example, for a file called **video1.mp4** that is in a **Videos** subfolder, the path would look like: **ms-appx:///Videos/video1.mp4**</span></span>

<span data-ttu-id="52f1b-156">Mit diesem Code wird die [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx)-Eigenschaft des [MediaPlayerElements](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) definiert, das zuvor in XAML auf **ms-appx:///Videos/video1.mp4** festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="52f1b-156">This code sets the [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) property of the [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) defined previously in XAML to **ms-appx:///Videos/video1.mp4**.</span></span>

```csharp
private void LoadEmbeddedAppFile()
{
    try
    {
        Uri pathUri = new Uri("ms-appx:///Videos/video1.mp4");
        mediaPlayer.Source = MediaSource.CreateFromUri(pathUri);
    }
    catch (Exception ex)
    {
        if (ex is FormatException)
        {
            // handle exception.
            // For example: Log error or notify user problem with file
        }
    }
}
```

### <a name="open-local-media-files"></a><span data-ttu-id="52f1b-157">Öffnen von lokalen Mediendateien</span><span class="sxs-lookup"><span data-stu-id="52f1b-157">Open local media files</span></span>
<span data-ttu-id="52f1b-158">Zum Öffnen von Dateien im lokalen System oder aus OneDrive können Sie das [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847)-Element verwenden, um die Datei abzurufen, und [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx), um die Medienquelle festzulegen; alternativ können Sie programmgesteuert auf die Benutzermedienordner zugreifen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-158">To open files on the local system or from OneDrive, you can use the [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847) to get the file and [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) to set the media source, or you can programmatically access the user media folders.</span></span>

<span data-ttu-id="52f1b-159">Falls für Ihre App jedoch der Zugriff auf die **Musik**- oder **Videoordner** ohne Benutzerinteraktion erforderlich ist (wenn Sie beispielsweise sämtliche Musik- oder Videodateien einer Sammlung des Benutzers aufzählen und in Ihrer App anzeigen), müssen Sie die Funktionen der **Musik-** und **Videobibliothek** deklarieren.</span><span class="sxs-lookup"><span data-stu-id="52f1b-159">If your app needs access without user interaction to the **Music** or **Video** folders, for example, if you are enumerating all the music or video files in the user's collection and displaying them in your app, then you need to declare the **Music Library** and **Video Library** capabilities.</span></span> <span data-ttu-id="52f1b-160">Weitere Informationen finden Sie unter [Dateien und Ordner in den Musik-, Bild- und Videobibliotheken](https://msdn.microsoft.com/library/windows/apps/mt188703).</span><span class="sxs-lookup"><span data-stu-id="52f1b-160">For more info, see [Files and folders in the Music, Pictures, and Videos libraries](https://msdn.microsoft.com/library/windows/apps/mt188703).</span></span>

<span data-ttu-id="52f1b-161">Das [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847)-Element benötigt keine besonderen Funktionen für den Zugriff auf Dateien im lokalen Dateisystem (etwa die Ordner **Musik** oder **Video** des Benutzers), da Benutzer die vollständige Kontrolle darüber haben, auf welche Datei zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="52f1b-161">The [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847) does not require special capabilities to access files on the local file system, such as the user's **Music** or **Video** folders, since the user has complete control over which file is being accessed.</span></span> <span data-ttu-id="52f1b-162">Aus Sicherheits- und Datenschutzgründen ist es sinnvoll, die Anzahl der von der App verwendeten Funktionen möglichst gering zu halten.</span><span class="sxs-lookup"><span data-stu-id="52f1b-162">From a security and privacy standpoint, it is best to minimize the number of capabilities your app uses.</span></span>

**<span data-ttu-id="52f1b-163">Öffnen lokaler Medien mit FileOpenPicker</span><span class="sxs-lookup"><span data-stu-id="52f1b-163">To open local media using FileOpenPicker</span></span>**

1.  <span data-ttu-id="52f1b-164">Rufen Sie [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847) auf, um dem Benutzer die Auswahl einer Mediendatei zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-164">Call [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847) to let the user pick a media file.</span></span>

    <span data-ttu-id="52f1b-165">Verwenden Sie die Klasse [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847), um eine Mediendatei auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-165">Use the [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847) class to select a media file.</span></span> <span data-ttu-id="52f1b-166">Legen Sie den [FileTypeFilter](https://msdn.microsoft.com/library/windows/apps/br207850) fest, um zu bestimmen, welche Dateitypen von **FileOpenPicker** angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="52f1b-166">Set the [FileTypeFilter](https://msdn.microsoft.com/library/windows/apps/br207850) to specify which file types the **FileOpenPicker** displays.</span></span> <span data-ttu-id="52f1b-167">Rufen Sie [PickSingleFileAsync](https://msdn.microsoft.com/library/windows/apps/jj635275) auf, um die Dateiauswahl zu starten und die Datei abzurufen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-167">Call [PickSingleFileAsync](https://msdn.microsoft.com/library/windows/apps/jj635275) to launch the file picker and get the file.</span></span>

2.  <span data-ttu-id="52f1b-168">Verwenden Sie eine [MediaSource](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.aspx), um die ausgewählte Mediendatei als [MediaPlayerElement.Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) festzulegen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-168">Use a [MediaSource](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.aspx) to set the chosen media file as the [MediaPlayerElement.Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx).</span></span>

    <span data-ttu-id="52f1b-169">Um die [StorageFile](https://msdn.microsoft.com/library/windows/apps/br227171) zu verwenden, die vom [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847) zurückgegeben wurde, müssen Sie die [CreateFromStorageFile](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.createfromstoragefile.aspx)-Methode für [MediaSource](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.aspx) aufrufen und diese als [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) von [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) festlegen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-169">To use the [StorageFile](https://msdn.microsoft.com/library/windows/apps/br227171) returned from the [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847), you need to call the [CreateFromStorageFile](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.createfromstoragefile.aspx) method on [MediaSource](https://msdn.microsoft.com/library/windows/apps/windows.media.core.mediasource.aspx) and set it as the [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) of [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx).</span></span> <span data-ttu-id="52f1b-170">Rufen Sie anschließend [Play](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.play.aspx) für das [MediaPlayerElement.MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.mediaplayer.aspx) auf, um die Medien zu starten.</span><span class="sxs-lookup"><span data-stu-id="52f1b-170">Then call [Play](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.play.aspx) on the [MediaPlayerElement.MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.mediaplayer.aspx) to start the media.</span></span>


<span data-ttu-id="52f1b-171">Dieses Beispiel erläutert, wie Sie [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847) dazu verwenden, eine Datei auszuwählen und diese als [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) eines [MediaPlayerElements](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) festlegen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-171">This example shows how to use the [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/br207847) to choose a file and set the file as the [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) of a [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx).</span></span>

```xaml
<MediaPlayerElement x:Name="mediaPlayer"/>
...
<Button Content="Choose file" Click="Button_Click"/>
```

```csharp
private async void Button_Click(object sender, RoutedEventArgs e)
{
    await SetLocalMedia();
}

async private System.Threading.Tasks.Task SetLocalMedia()
{
    var openPicker = new Windows.Storage.Pickers.FileOpenPicker();

    openPicker.FileTypeFilter.Add(".wmv");
    openPicker.FileTypeFilter.Add(".mp4");
    openPicker.FileTypeFilter.Add(".wma");
    openPicker.FileTypeFilter.Add(".mp3");

    var file = await openPicker.PickSingleFileAsync();

    // mediaPlayer is a MediaPlayerElement defined in XAML
    if (file != null)
    {
        mediaPlayer.Source = MediaSource.CreateFromStorageFile(file);

        mediaPlayer.MediaPlayer.Play();
    }
}
```

### <a name="set-the-poster-source"></a><span data-ttu-id="52f1b-172">Festlegen der Posterquelle</span><span class="sxs-lookup"><span data-stu-id="52f1b-172">Set the poster source</span></span>
<span data-ttu-id="52f1b-173">Mit der Eigenschaft [PosterSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.PosterSource.aspx) können Sie eine visuelle Darstellung für Ihr [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) bereitstellen, bevor die Medien geladen werden.</span><span class="sxs-lookup"><span data-stu-id="52f1b-173">You can use the [PosterSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.PosterSource.aspx) property to provide your [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) with a visual representation before the media is loaded.</span></span> <span data-ttu-id="52f1b-174">Eine **PosterSource** ist ein Bild, z.B. ein Bildschirmfoto oder Filmplakat, das anstelle der Medien angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="52f1b-174">A **PosterSource** is an image, such as a screen shot or movie poster, that is displayed in place of the media.</span></span> <span data-ttu-id="52f1b-175">Die **PosterSource** wird in folgenden Fällen angezeigt:</span><span class="sxs-lookup"><span data-stu-id="52f1b-175">The **PosterSource** is displayed in the following situations:</span></span>

-   <span data-ttu-id="52f1b-176">Wenn keine gültige Quelle festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="52f1b-176">When a valid source is not set.</span></span> <span data-ttu-id="52f1b-177">Beispiel: [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) ist nicht festgelegt, **Source** wurde auf **Null** festgelegt, oder die Quelle ist ungültig (z.B. wenn ein [MediaFailed](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.mediafailed.aspx)-Ereignis eintritt).</span><span class="sxs-lookup"><span data-stu-id="52f1b-177">For example, [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) is not set, **Source** was set to **Null**, or the source is invalid (as is the case when a [MediaFailed](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.mediafailed.aspx) event occurs).</span></span>
-   <span data-ttu-id="52f1b-178">Während Medien geladen werden.</span><span class="sxs-lookup"><span data-stu-id="52f1b-178">While media is loading.</span></span> <span data-ttu-id="52f1b-179">Beispiel: Es ist eine gültige Source festgelegt, das Ereignis [MediaOpened](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.mediaopened.aspx) ist jedoch noch nicht eingetreten.</span><span class="sxs-lookup"><span data-stu-id="52f1b-179">For example, a valid source is set, but the [MediaOpened](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.mediaopened.aspx) event has not occurred yet.</span></span>
-   <span data-ttu-id="52f1b-180">Beim Streamen von Medien auf ein anderes Gerät.</span><span class="sxs-lookup"><span data-stu-id="52f1b-180">When media is streaming to another device.</span></span>
-   <span data-ttu-id="52f1b-181">Wenn die Medien nur Audio enthalten.</span><span class="sxs-lookup"><span data-stu-id="52f1b-181">When the media is audio only.</span></span>

<span data-ttu-id="52f1b-182">Nachfolgend ein Beispiel für ein [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx), dessen [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) auf einen Albumtitel festgelegt ist und dessen [PosterSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.PosterSource.aspx) eine Abbildung des Albumcovers enthält.</span><span class="sxs-lookup"><span data-stu-id="52f1b-182">Here's a [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) with its [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) set to an album track, and it's [PosterSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.PosterSource.aspx) set to an image of the album cover.</span></span>

```xaml
<MediaPlayerElement Source="Media/Track1.mp4" PosterSource="Media/AlbumCover.png"/>
```

### <a name="keep-the-devices-screen-active"></a><span data-ttu-id="52f1b-183">Abdunkeln/Ausschalten des Gerätebildschirms verhindern</span><span class="sxs-lookup"><span data-stu-id="52f1b-183">Keep the device's screen active</span></span>
<span data-ttu-id="52f1b-184">Normalerweise wird bei einem Gerät das Display abgeblendet (und schließlich ausgeschaltet), um bei Abwesenheit des Benutzers den Akku zu schonen. Bei Video-Apps muss der Bildschirm jedoch eingeschaltet bleiben, damit der Benutzer das Video sehen kann.</span><span class="sxs-lookup"><span data-stu-id="52f1b-184">Typically, a device dims the display (and eventually turns it off) to save battery life when the user is away, but video apps need to keep the screen on so the user can see the video.</span></span> <span data-ttu-id="52f1b-185">Um ein Deaktivieren der Anzeige zu verhindern, wenn keine Benutzeraktion mehr festgestellt werden kann (z.B. bei der Wiedergabe eines Videos in einer App), können Sie [DisplayRequest.RequestActive](https://msdn.microsoft.com/library/windows/apps/br241818) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-185">To prevent the display from being deactivated when user action is no longer detected, such as when an app is playing video, you can call [DisplayRequest.RequestActive](https://msdn.microsoft.com/library/windows/apps/br241818).</span></span> <span data-ttu-id="52f1b-186">Mithilfe der Klasse [DisplayRequest](https://msdn.microsoft.com/library/windows/apps/br241816) können Sie Windows anweisen, das Display eingeschaltet zu lassen, damit der Benutzer das Video sehen kann.</span><span class="sxs-lookup"><span data-stu-id="52f1b-186">The [DisplayRequest](https://msdn.microsoft.com/library/windows/apps/br241816) class lets you tell Windows to keep the display turned on so the user can see the video.</span></span>

<span data-ttu-id="52f1b-187">Um Energie zu sparen und den Akku zu schonen, sollten Sie [DisplayRequest.RequestRelease](https://msdn.microsoft.com/library/windows/apps/br241819) aufrufen, um die Displayanfrage freizugeben, wenn diese nicht mehr benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="52f1b-187">To conserve power and battery life, you should call [DisplayRequest.RequestRelease](https://msdn.microsoft.com/library/windows/apps/br241819) to release the display request when it is no longer required.</span></span> <span data-ttu-id="52f1b-188">Windows deaktiviert automatisch die aktiven Displayanforderungen der App, wenn die App vom Bildschirm entfernt wird, und aktiviert die Displayanforderungen wieder, wenn Ihre App wieder in den Vordergrund gesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="52f1b-188">Windows automatically deactivates your app's active display requests when your app moves off screen, and re-activates them when your app comes back to the foreground.</span></span>

<span data-ttu-id="52f1b-189">Im Anschluss sind einige Situationen aufgeführt, in denen Sie die Displayanforderung freigeben sollten:</span><span class="sxs-lookup"><span data-stu-id="52f1b-189">Here are some situations when you should release the display request:</span></span>

-   <span data-ttu-id="52f1b-190">Die Videowiedergabe wird angehalten (beispielsweise durch eine Benutzeraktion, zum Puffern oder für eine Anpassung aufgrund von begrenzter Bandbreite).</span><span class="sxs-lookup"><span data-stu-id="52f1b-190">Video playback is paused, for example, by user action, buffering, or adjustment due to limited bandwidth.</span></span>
-   <span data-ttu-id="52f1b-191">Die Wiedergabe wird gestoppt.</span><span class="sxs-lookup"><span data-stu-id="52f1b-191">Playback stops.</span></span> <span data-ttu-id="52f1b-192">Beispielsweise ist die Wiedergabe des Videos beendet oder die Darstellung vorüber.</span><span class="sxs-lookup"><span data-stu-id="52f1b-192">For example, the video is done playing or the presentation is over.</span></span>
-   <span data-ttu-id="52f1b-193">Ein Wiedergabefehler ist aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="52f1b-193">A playback error has occurred.</span></span> <span data-ttu-id="52f1b-194">(beispielsweise bei Problemen mit der Netzwerkverbindung oder mit einer beschädigten Datei).</span><span class="sxs-lookup"><span data-stu-id="52f1b-194">For example, network connectivity issues or a corrupted file.</span></span>

> <span data-ttu-id="52f1b-195">**Hinweis**&nbsp;&nbsp; Wenn [MediaPlayerElement.IsFullWindow](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.IsFullWindow.aspx) auf „true“ gesetzt ist und Medien wiedergegeben werden, wird die Deaktivierung der Anzeige automatisch verhindert.</span><span class="sxs-lookup"><span data-stu-id="52f1b-195">**Note**&nbsp;&nbsp; If [MediaPlayerElement.IsFullWindow](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.IsFullWindow.aspx) is set to true and media is playing, the display will automatically be prevented from deactivating.</span></span>

**<span data-ttu-id="52f1b-196">Abdunkeln/Ausschalten des Bildschirms verhindern</span><span class="sxs-lookup"><span data-stu-id="52f1b-196">To keep the screen active</span></span>**

1.  <span data-ttu-id="52f1b-197">Erstellen einer globalen [DisplayRequest](https://msdn.microsoft.com/library/windows/apps/br241816)-Variable.</span><span class="sxs-lookup"><span data-stu-id="52f1b-197">Create a global [DisplayRequest](https://msdn.microsoft.com/library/windows/apps/br241816) variable.</span></span> <span data-ttu-id="52f1b-198">Initialisieren Sie diese mit dem Wert Null.</span><span class="sxs-lookup"><span data-stu-id="52f1b-198">Initialize it to null.</span></span>
```csharp
// Create this variable at a global scope. Set it to null.
private DisplayRequest appDisplayRequest = null;
```

2.  <span data-ttu-id="52f1b-199">Rufen Sie [RequestActive](https://msdn.microsoft.com/library/windows/apps/br241818) auf, um Windows mitzuteilen, dass für die App das Display eingeschaltet bleiben muss.</span><span class="sxs-lookup"><span data-stu-id="52f1b-199">Call [RequestActive](https://msdn.microsoft.com/library/windows/apps/br241818) to notify Windows that the app requires the display to remain on.</span></span>

3.  <span data-ttu-id="52f1b-200">Rufen Sie [RequestRelease](https://msdn.microsoft.com/library/windows/apps/br241819) auf, um die Displayanfrage freizugeben, wenn die Videowiedergabe beendet, angehalten oder durch einen Wiedergabefehler unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="52f1b-200">Call [RequestRelease](https://msdn.microsoft.com/library/windows/apps/br241819) to release the display request whenever video playback is stopped, paused, or interrupted by a playback error.</span></span> <span data-ttu-id="52f1b-201">Falls für die App keine aktiven Displayanforderungen mehr vorhanden sind, schont Windows den Akku, indem das Display abgeblendet (und schließlich ausgeschaltet) wird, wenn das Gerät nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="52f1b-201">When your app no longer has any active display requests, Windows saves battery life by dimming the display (and eventually turning it off) when the device is not being used.</span></span>

    <span data-ttu-id="52f1b-202">Jedes [MediaPlayerElement.MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.mediaplayer.aspx) hat eine [PlaybackSession](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.playbacksession.aspx) vom Typ [MediaPlaybackSession](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.aspx), die verschiedene Aspekte der Medienwiedergabe steuert wie [PlaybackRate](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.playbackrate.aspx), [PlaybackState](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.playbackstate.aspx) und [Position](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.position.aspx).</span><span class="sxs-lookup"><span data-stu-id="52f1b-202">Each [MediaPlayerElement.MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.mediaplayer.aspx) has a [PlaybackSession](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.playbacksession.aspx) of type [MediaPlaybackSession](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.aspx) that controls various aspects of media playback such as [PlaybackRate](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.playbackrate.aspx), [PlaybackState](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.playbackstate.aspx) and [Position](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.position.aspx).</span></span> <span data-ttu-id="52f1b-203">Hier wenden Sie das Ereignis [PlaybackStateChanged](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.playbackstatechanged.aspx) auf  [MediaPlayer.PlaybackSession](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.playbacksession.aspx) an, um Situationen zu erkennen, in denen die Displayanfrage freigeben werden sollte.</span><span class="sxs-lookup"><span data-stu-id="52f1b-203">Here, you use the [PlaybackStateChanged](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.playbackstatechanged.aspx) event on  [MediaPlayer.PlaybackSession](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.playbacksession.aspx) to detect situations when you should release the display request.</span></span> <span data-ttu-id="52f1b-204">Verwenden Sie dann die [NaturalVideoHeight](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.naturalvideoheight.aspx)-Eigenschaft, um festzustellen, ob eine Audio- oder Videodatei wiedergegeben wird, und lassen Sie den Bildschirm nur eingeschaltet, wenn eine Videodatei wiedergegeben wird.</span><span class="sxs-lookup"><span data-stu-id="52f1b-204">Then, use the [NaturalVideoHeight](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacksession.naturalvideoheight.aspx) property to determine whether an audio or video file is playing, and keep the screen active only if video is playing.</span></span>
    ```xaml
<MediaPlayerElement x:Name="mpe" Source="Media/video1.mp4"/>
    ```

    ```csharp
    protected override void OnNavigatedTo(NavigationEventArgs e)
    {
        mpe.MediaPlayer.PlaybackSession.PlaybackStateChanged += MediaPlayerElement_CurrentStateChanged;
        base.OnNavigatedTo(e);
    }

    private void MediaPlayerElement_CurrentStateChanged(object sender, RoutedEventArgs e)
    {
        MediaPlaybackSession playbackSession = sender as MediaPlaybackSession;
        if (playbackSession != null && playbackSession.NaturalVideoHeight != 0)
        {
            if(playbackSession.PlaybackState == MediaPlaybackState.Playing)
            {
                if(appDisplayRequest == null)
                {
                    // This call creates an instance of the DisplayRequest object
                    appDisplayRequest = new DisplayRequest();
                    appDisplayRequest.RequestActive();
                }
            }
            else // PlaybackState is Buffering, None, Opening or Paused
            {
                if(appDisplayRequest != null)
                {
                      // Deactivate the displayr request and set the var to null
                      appDisplayRequest.RequestRelease();
                      appDisplayRequest = null;
                }
            }
        }

    }
    ```

### <a name="control-the-media-player-programmatically"></a><span data-ttu-id="52f1b-205">Programmatische Steuerung des Media Players</span><span class="sxs-lookup"><span data-stu-id="52f1b-205">Control the media player programmatically</span></span>
<span data-ttu-id="52f1b-206">Das [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) bietet zahlreiche Eigenschaften, Methoden und Ereignisse zur Steuerung der Audio- und Videowiedergabe über die Eigenschaft [MediaPlayerElement.MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.mediaplayer.aspx).</span><span class="sxs-lookup"><span data-stu-id="52f1b-206">[MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) provides numerous properties, methods, and events for controlling audio and video playback through the [MediaPlayerElement.MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.mediaplayer.aspx) property.</span></span> <span data-ttu-id="52f1b-207">Eine vollständige Liste der Eigenschaften, Methoden und Ereignisse finden Sie auf der Referenzseite zum [MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.aspx) .</span><span class="sxs-lookup"><span data-stu-id="52f1b-207">For a full listing of properties, methods, and events, see the [MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.aspx) reference page.</span></span>

### <a name="advanced-media-playback-scenarios"></a><span data-ttu-id="52f1b-208">Erweiterte Medienwiedergabeszenarien</span><span class="sxs-lookup"><span data-stu-id="52f1b-208">Advanced media playback scenarios</span></span>
<span data-ttu-id="52f1b-209">Für komplexere Medienwiedergabeszenarien, z.B. die Wiedergabe einer Playlist, Umschalten zwischen Audiosprachen oder Erstellen benutzerdefinierter Metadatentracks, legen Sie [MediaPlayerElement.Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) auf eine [MediaPlaybackItem](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybackitem.aspx) oder eine [MediaPlaybackList](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacklist.aspx) fest.</span><span class="sxs-lookup"><span data-stu-id="52f1b-209">For more complex media playback scenarios like playing a playlist, switching between audio languages or creating custom metadata tracks set the [MediaPlayerElement.Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.source.aspx) to a [MediaPlaybackItem](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybackitem.aspx) or a [MediaPlaybackList](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplaybacklist.aspx).</span></span> <span data-ttu-id="52f1b-210">So aktivieren Sie verschiedene erweiterte Medienfunktionen finden Sie auf der [Medienwiedergabe](https://msdn.microsoft.com/windows/uwp/audio-video-camera/media-playback-with-mediasource) Seite Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-210">See the [Media playback](https://msdn.microsoft.com/windows/uwp/audio-video-camera/media-playback-with-mediasource) page for more information on how to enable various advanced media functionality.</span></span>

### <a name="enable-full-window-video-rendering"></a><span data-ttu-id="52f1b-211">Aktivieren des Videorenderings im Vollbildmodus</span><span class="sxs-lookup"><span data-stu-id="52f1b-211">Enable full window video rendering</span></span>

<span data-ttu-id="52f1b-212">Legen Sie die Eigenschaft [IsFullWindow](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.isfullwindow.aspx) fest, um das Rendering im Vollbildmodus zu aktivieren und zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="52f1b-212">Set the [IsFullWindow](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.isfullwindow.aspx) property to enable and disable full window rendering.</span></span> <span data-ttu-id="52f1b-213">Wenn Sie das Rendering im Vollbildmodus in Ihrer App programmatisch festlegen, sollten Sie stets die Eigenschaft **IsFullWindow** verwenden, anstatt diese Einstellung manuell vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-213">When you programmatically set full window rendering in your app, you should always use **IsFullWindow** instead of doing it manually.</span></span> <span data-ttu-id="52f1b-214">**IsFullWindow** stellt sicher, dass Optimierungen auf Systemebene zum Verbessern der Leistung und Akkulaufzeit durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="52f1b-214">**IsFullWindow** insures that system level optimizations are performed that improve performance and battery life.</span></span> <span data-ttu-id="52f1b-215">Wird das Rendering im Vollbildmodus nicht korrekt eingerichtet, werden diese Optimierungen möglicherweise nicht angewendet.</span><span class="sxs-lookup"><span data-stu-id="52f1b-215">If full window rendering is not set up correctly, these optimizations may not be enabled.</span></span>

<span data-ttu-id="52f1b-216">Der folgende Code erstellt einen [AppBarButton](https://msdn.microsoft.com/library/windows/apps/dn279244) zum Umschalten des Renderings im Vollbildmodus.</span><span class="sxs-lookup"><span data-stu-id="52f1b-216">Here is some code that creates an [AppBarButton](https://msdn.microsoft.com/library/windows/apps/dn279244) that toggles full window rendering.</span></span>

```xaml
<AppBarButton Icon="FullScreen"
              Label="Full Window"
              Click="FullWindow_Click"/>>
```

```csharp
private void FullWindow_Click(object sender, object e)
{
    mediaPlayer.IsFullWindow = !media.IsFullWindow;
}
```

### <a name="resize-and-stretch-video"></a><span data-ttu-id="52f1b-217">Größenänderung und Strecken von Videos</span><span class="sxs-lookup"><span data-stu-id="52f1b-217">Resize and stretch video</span></span>

<span data-ttu-id="52f1b-218">Verwenden Sie die Eigenschaft [Stretch](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.stretch.aspx), um die Art und Weise zu ändern, wie der Videoinhalt und/oder die [PosterSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.postersource.aspx) den Container ausfüllt, in dem sich diese/dieser befindet.</span><span class="sxs-lookup"><span data-stu-id="52f1b-218">Use the [Stretch](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.stretch.aspx) property to change how the video content and/or the [PosterSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.postersource.aspx) fills the container it's in.</span></span> <span data-ttu-id="52f1b-219">Die Größe des Videos wird dabei entsprechend dem [Stretch](https://msdn.microsoft.com/library/windows/apps/br242968)-Wert geändert bzw. gestreckt.</span><span class="sxs-lookup"><span data-stu-id="52f1b-219">This resizes and stretches the video depending on the [Stretch](https://msdn.microsoft.com/library/windows/apps/br242968) value.</span></span> <span data-ttu-id="52f1b-220">Die **Stretch**-Zustände sind mit den Bildformateinstellungen zahlreicher Fernsehgeräte vergleichbar.</span><span class="sxs-lookup"><span data-stu-id="52f1b-220">The **Stretch** states are similar to picture size settings on many TV sets.</span></span> <span data-ttu-id="52f1b-221">Sie können dieses Verhalten mit einer Schaltfläche verknüpfen und dem Benutzer die Auswahl der gewünschten Einstellung ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-221">You can hook this up to a button and allow the user to choose which setting they prefer.</span></span>

-   <span data-ttu-id="52f1b-222">[None](https://msdn.microsoft.com/library/windows/apps/br242968) zeigt die native Auflösung des Inhalts in dessen Originalgröße an.</span><span class="sxs-lookup"><span data-stu-id="52f1b-222">[None](https://msdn.microsoft.com/library/windows/apps/br242968) displays the native resolution of the content in its original size.</span></span>
-   <span data-ttu-id="52f1b-223">[Uniform](https://msdn.microsoft.com/library/windows/apps/br242968) füllt unter Beibehaltung des Seitenverhältnisses und des Bildinhalts den größtmöglichen Platz aus.</span><span class="sxs-lookup"><span data-stu-id="52f1b-223">[Uniform](https://msdn.microsoft.com/library/windows/apps/br242968) fills up as much of the space as possible while preserving the aspect ratio and the image content.</span></span> <span data-ttu-id="52f1b-224">Dies kann zu horizontalen oder vertikalen schwarzen Balken an den Rändern des Videos führen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-224">This can result in horizontal or vertical black bars at the edges of the video.</span></span> <span data-ttu-id="52f1b-225">Dieser Zustand ist mit Breitbildmodi vergleichbar.</span><span class="sxs-lookup"><span data-stu-id="52f1b-225">This is similar to wide-screen modes.</span></span>
-   <span data-ttu-id="52f1b-226">[UniformToFill](https://msdn.microsoft.com/library/windows/apps/br242968) füllt den gesamten Platz unter Beibehaltung des Seitenverhältnisses aus.</span><span class="sxs-lookup"><span data-stu-id="52f1b-226">[UniformToFill](https://msdn.microsoft.com/library/windows/apps/br242968) fills up the entire space while preserving the aspect ratio.</span></span> <span data-ttu-id="52f1b-227">Dies kann dazu führen, dass ein Teil des Bilds abgeschnitten wird.</span><span class="sxs-lookup"><span data-stu-id="52f1b-227">This can result in some of the image being cropped.</span></span> <span data-ttu-id="52f1b-228">Dieser Zustand ist mit Vollbildmodi vergleichbar.</span><span class="sxs-lookup"><span data-stu-id="52f1b-228">This is similar to full-screen modes.</span></span>
-   <span data-ttu-id="52f1b-229">[Fill](https://msdn.microsoft.com/library/windows/apps/br242968) füllt den gesamten Platz aus, ohne das Seitenverhältnis beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="52f1b-229">[Fill](https://msdn.microsoft.com/library/windows/apps/br242968) fills up the entire space, but does not preserve the aspect ratio.</span></span> <span data-ttu-id="52f1b-230">Das Bild wird nicht zugeschnitten, kann aber gestreckt werden.</span><span class="sxs-lookup"><span data-stu-id="52f1b-230">None of image is cropped, but stretching may occur.</span></span> <span data-ttu-id="52f1b-231">Dieser Zustand ist mit Streckmodi vergleichbar.</span><span class="sxs-lookup"><span data-stu-id="52f1b-231">This is similar to stretch modes.</span></span>

![Stretch-Aufzählungswerte](images/Image_Stretch.jpg)

<span data-ttu-id="52f1b-233">In diesem Beispiel werden die [Stretch](https://msdn.microsoft.com/library/windows/apps/br242968)-Optionen mit einem [AppBarButton](https://msdn.microsoft.com/library/windows/apps/dn279244) durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-233">Here, an [AppBarButton](https://msdn.microsoft.com/library/windows/apps/dn279244) is used to cycle through the [Stretch](https://msdn.microsoft.com/library/windows/apps/br242968) options.</span></span> <span data-ttu-id="52f1b-234">Eine **switch**-Anweisung überprüft den aktuellen Zustand der [Stretch](https://msdn.microsoft.com/library/windows/apps/br227422)-Eigenschaft und legt diese auf den nächsten Wert in der **Stretch**-Aufzählung fest.</span><span class="sxs-lookup"><span data-stu-id="52f1b-234">A **switch** statement checks the current state of the [Stretch](https://msdn.microsoft.com/library/windows/apps/br227422) property and sets it to the next value in the **Stretch** enumeration.</span></span> <span data-ttu-id="52f1b-235">So kann der Benutzer zwischen verschiedenen Streckungszuständen wechseln.</span><span class="sxs-lookup"><span data-stu-id="52f1b-235">This lets the user cycle through the different stretch states.</span></span>

```xaml
<AppBarButton Icon="Switch"
              Label="Resize Video"
              Click="PictureSize_Click" />
```

```csharp
private void PictureSize_Click(object sender, RoutedEventArgs e)
{
    switch (mediaPlayer.Stretch)
    {
        case Stretch.Fill:
            mediaPlayer.Stretch = Stretch.None;
            break;
        case Stretch.None:
            mediaPlayer.Stretch = Stretch.Uniform;
            break;
        case Stretch.Uniform:
            mediaPlayer.Stretch = Stretch.UniformToFill;
            break;
        case Stretch.UniformToFill:
            mediaPlayer.Stretch = Stretch.Fill;
            break;
        default:
            break;
    }
}
```

### <a name="enable-low-latency-playback"></a><span data-ttu-id="52f1b-236">Aktivieren der Wiedergabe mit geringer Wartezeit</span><span class="sxs-lookup"><span data-stu-id="52f1b-236">Enable low-latency playback</span></span>

<span data-ttu-id="52f1b-237">Setzen Sie die Eigenschaft [RealTimePlayback](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.realtimeplayback.aspx) für ein [MediaPlayerElement.MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.mediaplayer.aspx) auf **true**, damit das Media Player-Element die anfängliche Wartezeit für die Wiedergabe reduzieren kann.</span><span class="sxs-lookup"><span data-stu-id="52f1b-237">Set the [RealTimePlayback](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.realtimeplayback.aspx) property to **true** on a [MediaPlayerElement.MediaPlayer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.mediaplayer.aspx) to enable the media player element to reduce the initial latency for playback.</span></span> <span data-ttu-id="52f1b-238">Dies ist von entscheidender Bedeutung für Apps mit bidirektionaler Kommunikation und kann für einige Gaming-Szenarien erforderlich sein.</span><span class="sxs-lookup"><span data-stu-id="52f1b-238">This is critical for two-way communications apps, and can be applicable to some gaming scenarios.</span></span> <span data-ttu-id="52f1b-239">Beachten Sie, dass dieser Modus anspruchsvoller ist und weniger stromsparend arbeitet.</span><span class="sxs-lookup"><span data-stu-id="52f1b-239">Be aware that this mode is more resource intensive and less power-efficient.</span></span>

<span data-ttu-id="52f1b-240">Das folgende Beispiel erstellt ein [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) uns setzt [RealTimePlayback](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.realtimeplayback.aspx) auf **true**.</span><span class="sxs-lookup"><span data-stu-id="52f1b-240">This example creates a [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) and sets [RealTimePlayback](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.realtimeplayback.aspx) to **true**.</span></span>


```csharp
MediaPlayerElement mp = new MediaPlayerElement();
mp.MediaPlayer.RealTimePlayback = true;
```

## <a name="recommendations"></a><span data-ttu-id="52f1b-241">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="52f1b-241">Recommendations</span></span>

<span data-ttu-id="52f1b-242">MediaPlayer unterstützt helle und dunkle Designs. Dunkle Designs bieten für die Mehrzahl der Unterhaltungsszenarien jedoch eine bessere Umgebung.</span><span class="sxs-lookup"><span data-stu-id="52f1b-242">The media player supports both light and dark themes, but dark theme provides a better experience for most entertainment scenarios.</span></span> <span data-ttu-id="52f1b-243">Der dunkle Hintergrund bietet einen besseren Kontrast, insbesondere bei schwierigen Lichtbedingungen, und verhindert Beeinträchtigungen der Steuerleiste auf der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="52f1b-243">The dark background provides better contrast, in particular for low-light conditions, and limits the control bar from interfering in the viewing experience.</span></span>

<span data-ttu-id="52f1b-244">Unterstützen Sie beim Abspielen von Videoinhalten eine dedizierte Anzeigeumgebung, indem Sie den Vollbildmodus gegenüber dem Inlinemodus bevorzugen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-244">When playing video content, encourage a dedicated viewing experience by promoting full-screen mode over inline mode.</span></span> <span data-ttu-id="52f1b-245">Die Vollbildansicht ist optimal. Die Optionen sind im Inlinemodus eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="52f1b-245">The full-screen viewing experience is optimal, and options are restricted in the inline mode.</span></span>

<span data-ttu-id="52f1b-246">Wenn Sie die nötige Bildschirmfläche haben oder für 10 Fuß-Umgebungen entwerfen, sollten Sie sich für das Layout mit Doppelzeile entscheiden.</span><span class="sxs-lookup"><span data-stu-id="52f1b-246">If you have the screen real estate or are designing for the 10-foot experience, go with the double-row layout.</span></span> <span data-ttu-id="52f1b-247">Es bietet mehr Platz für Steuerelemente als das kompakte einzeilige Layout, und die Navigation mit dem Gamepad in 10-Fuß-Szenarien ist einfacher.</span><span class="sxs-lookup"><span data-stu-id="52f1b-247">It provides more space for controls than the compact single-row layout and it is easier to navigate using gamepad for 10-foot.</span></span>

> <span data-ttu-id="52f1b-248">**Hinweis**&nbsp;&nbsp; Im Artikel [Designing for Xbox and TV](../devices/designing-for-tv.md) finden Sie weitere Informationen zur Optimierung Ihrer Anwendung für 10-Fuß-Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-248">**Note**&nbsp;&nbsp; Visit the [Designing for Xbox and TV](../devices/designing-for-tv.md) article for more information on optimizing your application for the 10-foot experience.</span></span>

<span data-ttu-id="52f1b-249">Die Standardsteuerelemente wurden für die Medienwiedergabe optimiert. Sie können jedoch benutzerdefinierte Optionen hinzufügen, die Sie für den Media Player benötigen, um für Ihre App eine optimale Umgebung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="52f1b-249">The default controls have been optimized for media playback, however you have the ability to add custom options you need to the media player in order to provide the best experience for you app.</span></span> <span data-ttu-id="52f1b-250">Weitere Informationen zum Hinzufügen von benutzerdefinierten Steuerelementen finden Sie unter [Erstellen benutzerdefinierter Transportsteuerelemente](custom-transport-controls.md).</span><span class="sxs-lookup"><span data-stu-id="52f1b-250">Visit [Create custom transport controls](custom-transport-controls.md) to learn more about adding custom controls.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="52f1b-251">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="52f1b-251">Get the sample code</span></span>

- <span data-ttu-id="52f1b-252">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="52f1b-252">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="52f1b-253">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="52f1b-253">Related articles</span></span>

- [<span data-ttu-id="52f1b-254">Befehlsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="52f1b-254">Command design basics for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn958433)
- [<span data-ttu-id="52f1b-255">Grundlagen des Inhaltsdesigns für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="52f1b-255">Content design basics for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn958434)
