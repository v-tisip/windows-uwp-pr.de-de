---
author: drewbatgit
ms.assetid: A1A0D99A-DCBF-4A14-80B9-7106BEF045EC
description: Mit den Windows.Media.Transcoding-APIs können Sie Videodateien von einem Format in ein anderes transcodieren.
title: Transkodieren von Mediendateien
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: 20c13471d67033790c01a07e53af667c2a078894
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1831974"
---
# <a name="transcode-media-files"></a><span data-ttu-id="b7cf2-104">Transkodieren von Mediendateien</span><span class="sxs-lookup"><span data-stu-id="b7cf2-104">Transcode media files</span></span>



<span data-ttu-id="b7cf2-105">Mit den [**Windows.Media.Transcoding**](https://msdn.microsoft.com/library/windows/apps/br207105)-APIs können Sie Videodateien in ein anderes Format transcodieren.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-105">You can use the [**Windows.Media.Transcoding**](https://msdn.microsoft.com/library/windows/apps/br207105) APIs to transcode video files from one format to another.</span></span>

<span data-ttu-id="b7cf2-106">Beim *Transcodieren* wird eine digitale Mediendatei (etwa eine Video- oder Audiodatei) in ein anderes Format konvertiert.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-106">*Transcoding* is the conversion of a digital media file, such as a video or audio file, from one format to another.</span></span> <span data-ttu-id="b7cf2-107">Dies geschieht in der Regel durch Decodieren und erneutes Codieren der Datei.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-107">This is usually done by decoding and then re-encoding the file.</span></span> <span data-ttu-id="b7cf2-108">Beispiel: Sie konvertieren eine Windows Media-Datei in MP4, um sie auf einem Gerät wiederzugeben, das das MP4-Format unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-108">For example, you might convert a Windows Media file to MP4 so that it can be played on a portable device that supports MP4 format.</span></span> <span data-ttu-id="b7cf2-109">Oder Sie können eine Videodatei mit hoher Auflösung in eine niedrigere Auflösung konvertieren.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-109">Or, you might convert a high-definition video file to a lower resolution.</span></span> <span data-ttu-id="b7cf2-110">In diesem Fall kann die neu codierte Datei den gleichen Codec wie die Originaldatei verwenden, sie besitzt jedoch ein anderes Codierungsprofil.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-110">In that case, the re-encoded file might use the same codec as the original file, but it would have a different encoding profile.</span></span>

## <a name="set-up-your-project-for-transcoding"></a><span data-ttu-id="b7cf2-111">Einrichten des Projekts für die Transcodierung</span><span class="sxs-lookup"><span data-stu-id="b7cf2-111">Set up your project for transcoding</span></span>

<span data-ttu-id="b7cf2-112">Zusätzlich zu den Namespaces, auf die von der Standardprojektvorlage verwiesen wird, müssen Sie auf die folgenden Namespaces verweisen, um Mediendateien mit dem Code in diesem Artikel transcodieren zu können:</span><span class="sxs-lookup"><span data-stu-id="b7cf2-112">In addition to the namespaces referenced by the default project template, you will need to reference these namespaces in order to transcode media files using the code in this article.</span></span>

[!code-cs[Using](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetUsing)]

## <a name="select-source-and-destination-files"></a><span data-ttu-id="b7cf2-113">Auswählen der Quell- und Zieldateien</span><span class="sxs-lookup"><span data-stu-id="b7cf2-113">Select source and destination files</span></span>

<span data-ttu-id="b7cf2-114">Die Art, wie Ihre App die Quell- und Zieldateien für die Transcodierung ermittelt, hängt von der Implementierung ab.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-114">The way that your app determines the source and destination files for transcoding depends on your implementation.</span></span> <span data-ttu-id="b7cf2-115">In diesem Beispiel werden eine [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847)-Klasse und eine [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871)-Klasse verwendet, um Benutzern die Auswahl einer Quell- und Zieldatei zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-115">This example uses a [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) and a [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871) to allow the user to pick a source and a destination file.</span></span>

[!code-cs[TranscodeGetFile](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetTranscodeGetFile)]

## <a name="create-a-media-encoding-profile"></a><span data-ttu-id="b7cf2-116">Erstellen eines Mediencodierungsprofils</span><span class="sxs-lookup"><span data-stu-id="b7cf2-116">Create a media encoding profile</span></span>

<span data-ttu-id="b7cf2-117">Das Codierungsprofil enthält die Einstellungen, die die Codierungsart der Zieldatei festlegen.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-117">The encoding profile contains the settings that determine how the destination file will be encoded.</span></span> <span data-ttu-id="b7cf2-118">Hier stehen die meisten Optionen zum Transcodieren einer Datei zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-118">This is where you have the greatest number of options when you transcode a file.</span></span>

<span data-ttu-id="b7cf2-119">Die [**MediaEncodingProfile**](https://msdn.microsoft.com/library/windows/apps/hh701026)-Klasse stellt statische Methoden zum Erstellen vordefinierter Codierungsprofile bereit:</span><span class="sxs-lookup"><span data-stu-id="b7cf2-119">The [**MediaEncodingProfile**](https://msdn.microsoft.com/library/windows/apps/hh701026) class provides static methods for creating predefined encoding profiles:</span></span>

### <a name="methods-for-creating-audio-only-encoding-profiles"></a><span data-ttu-id="b7cf2-120">Methoden zum Erstellen von Codierungsprofilen, die nur Audio enthalten</span><span class="sxs-lookup"><span data-stu-id="b7cf2-120">Methods for creating Audio-only encoding profiles</span></span>

<span data-ttu-id="b7cf2-121">Methode</span><span class="sxs-lookup"><span data-stu-id="b7cf2-121">Method</span></span>  |<span data-ttu-id="b7cf2-122">Profil</span><span class="sxs-lookup"><span data-stu-id="b7cf2-122">Profile</span></span>  |
---------|---------|
[**<span data-ttu-id="b7cf2-123">CreateAlac</span><span class="sxs-lookup"><span data-stu-id="b7cf2-123">CreateAlac</span></span>**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createalac)     |<span data-ttu-id="b7cf2-124">Apple Lossless Audio Codec (ALAC)-Audio</span><span class="sxs-lookup"><span data-stu-id="b7cf2-124">Apple Lossless Audio Codec (ALAC) audio</span></span>         |
[**<span data-ttu-id="b7cf2-125">CreateFlac</span><span class="sxs-lookup"><span data-stu-id="b7cf2-125">CreateFlac</span></span>**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createflac)     |<span data-ttu-id="b7cf2-126">Free Lossless Audio Codec (FLAC)-Audio.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-126">Free Lossless Audio Codec (FLAC) audio.</span></span>         |
[**<span data-ttu-id="b7cf2-127">CreateM4a</span><span class="sxs-lookup"><span data-stu-id="b7cf2-127">CreateM4a</span></span>**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createm4a)     |<span data-ttu-id="b7cf2-128">AAC-Audio (M4A)</span><span class="sxs-lookup"><span data-stu-id="b7cf2-128">AAC audio (M4A)</span></span>         |
[**<span data-ttu-id="b7cf2-129">CreateMp3</span><span class="sxs-lookup"><span data-stu-id="b7cf2-129">CreateMp3</span></span>**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createmp3)     |<span data-ttu-id="b7cf2-130">MP3-Audio</span><span class="sxs-lookup"><span data-stu-id="b7cf2-130">MP3 audio</span></span>         |
[**<span data-ttu-id="b7cf2-131">CreateWav</span><span class="sxs-lookup"><span data-stu-id="b7cf2-131">CreateWav</span></span>**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createwav)     |<span data-ttu-id="b7cf2-132">WAV-Audio</span><span class="sxs-lookup"><span data-stu-id="b7cf2-132">WAV audio</span></span>         |
[**<span data-ttu-id="b7cf2-133">CreateWmv</span><span class="sxs-lookup"><span data-stu-id="b7cf2-133">CreateWmv</span></span>**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createwmv)     |<span data-ttu-id="b7cf2-134">Windows Media Audio (WMA)</span><span class="sxs-lookup"><span data-stu-id="b7cf2-134">Windows Media Audio (WMA)</span></span>         |

### <a name="methods-for-creating-audio--video-encoding-profiles"></a><span data-ttu-id="b7cf2-135">Methoden zum Erstellen von Audio-/Videocodierungsprofilen</span><span class="sxs-lookup"><span data-stu-id="b7cf2-135">Methods for creating audio / video encoding profiles</span></span>

<span data-ttu-id="b7cf2-136">Methode</span><span class="sxs-lookup"><span data-stu-id="b7cf2-136">Method</span></span>  |<span data-ttu-id="b7cf2-137">Profil</span><span class="sxs-lookup"><span data-stu-id="b7cf2-137">Profile</span></span>  |
---------|---------|
[**<span data-ttu-id="b7cf2-138">CreateAvi</span><span class="sxs-lookup"><span data-stu-id="b7cf2-138">CreateAvi</span></span>**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createavi) |<span data-ttu-id="b7cf2-139">AVI</span><span class="sxs-lookup"><span data-stu-id="b7cf2-139">AVI</span></span> |
[**<span data-ttu-id="b7cf2-140">CreateHevc</span><span class="sxs-lookup"><span data-stu-id="b7cf2-140">CreateHevc</span></span>**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createhevc) |<span data-ttu-id="b7cf2-141">High Efficiency Video Coding (HEVC)-Video, auch als H.265-Video bezeichnet</span><span class="sxs-lookup"><span data-stu-id="b7cf2-141">High Efficiency Video Coding (HEVC) video, also known as H.265 video</span></span> |
[**<span data-ttu-id="b7cf2-142">CreateMp4</span><span class="sxs-lookup"><span data-stu-id="b7cf2-142">CreateMp4</span></span>**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createmp4) |<span data-ttu-id="b7cf2-143">MP4-Video (H.264-Video und AAC-Audio)</span><span class="sxs-lookup"><span data-stu-id="b7cf2-143">MP4 video (H.264 video plus AAC audio)</span></span> |
[**<span data-ttu-id="b7cf2-144">CreateWmv</span><span class="sxs-lookup"><span data-stu-id="b7cf2-144">CreateWmv</span></span>**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createwmv) |<span data-ttu-id="b7cf2-145">Windows Media Video (WMV)</span><span class="sxs-lookup"><span data-stu-id="b7cf2-145">Windows Media Video (WMV)</span></span> |


<span data-ttu-id="b7cf2-146">Der folgende Code erstellt ein Profil für MP4-Video:</span><span class="sxs-lookup"><span data-stu-id="b7cf2-146">The following code creates a profile for MP4 video.</span></span>

[!code-cs[TranscodeMediaProfile](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetTranscodeMediaProfile)]

<span data-ttu-id="b7cf2-147">Die statische [**CreateMp4**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createmp4)-Methode erstellt ein MP4-Codierungsprofil.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-147">The static [**CreateMp4**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createmp4) method creates an MP4 encoding profile.</span></span> <span data-ttu-id="b7cf2-148">Der Parameter für diese Methode gibt die Zielauflösung für das Video an.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-148">The parameter for this method gives the target resolution for the video.</span></span> <span data-ttu-id="b7cf2-149">In diesem Fall bedeutet [**VideoEncodingQuality.hd720p**](https://msdn.microsoft.com/library/windows/apps/hh701290): 1280x720Pixel mit 30Bildern pro Sekunde.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-149">In this case, [**VideoEncodingQuality.hd720p**](https://msdn.microsoft.com/library/windows/apps/hh701290) means 1280 x 720 pixels at 30 frames per second.</span></span> <span data-ttu-id="b7cf2-150">(„720p“ steht für 720progressive Scanlinien pro Frame.) Dieses Muster gilt auch für die anderen Methoden zum Erstellen vordefinierter Profile.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-150">("720p" stands for 720 progressive scan lines per frame.) The other methods for creating predefined profiles all follow this pattern.</span></span>

<span data-ttu-id="b7cf2-151">Alternativ können Sie mit der [**MediaEncodingProfile.CreateFromFileAsync**](https://msdn.microsoft.com/library/windows/apps/hh701047)-Methode ein Profil erstellen, das einer vorhandenen Mediendatei entspricht.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-151">Alternatively, you can create a profile that matches an existing media file by using the [**MediaEncodingProfile.CreateFromFileAsync**](https://msdn.microsoft.com/library/windows/apps/hh701047) method.</span></span> <span data-ttu-id="b7cf2-152">Wenn Sie die genauen gewünschten Codierungseinstellungen kennen, können Sie auch ein neues [**MediaEncodingProfile**](https://msdn.microsoft.com/library/windows/apps/hh701026)-Objekt erstellen und die Profildetails ausfüllen.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-152">Or, if you know the exact encoding settings that you want, you can create a new [**MediaEncodingProfile**](https://msdn.microsoft.com/library/windows/apps/hh701026) object and fill in the profile details.</span></span>

## <a name="transcode-the-file"></a><span data-ttu-id="b7cf2-153">Transcodieren der Datei</span><span class="sxs-lookup"><span data-stu-id="b7cf2-153">Transcode the file</span></span>

<span data-ttu-id="b7cf2-154">Erstellen Sie zum Transcodieren der Datei ein neues [**MediaTranscoder**](https://msdn.microsoft.com/library/windows/apps/br207080)-Objekt, und rufen Sie die [**MediaTranscoder.PrepareFileTranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700936)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-154">To transcode the file, create a new [**MediaTranscoder**](https://msdn.microsoft.com/library/windows/apps/br207080) object and call the [**MediaTranscoder.PrepareFileTranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700936) method.</span></span> <span data-ttu-id="b7cf2-155">Übergeben Sie die Quelldatei, die Zieldatei und das Codierungsprofil.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-155">Pass in the source file, the destination file, and the encoding profile.</span></span> <span data-ttu-id="b7cf2-156">Rufen Sie dann die [**TranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700946)-Methode für das [**PrepareTranscodeResult**](https://msdn.microsoft.com/library/windows/apps/hh700941)-Objekt auf, das mit dem asynchronen Transcodierungsvorgang zurückgegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-156">Then call the [**TranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700946) method on the [**PrepareTranscodeResult**](https://msdn.microsoft.com/library/windows/apps/hh700941) object that was returned from the async transcode operation.</span></span>

[!code-cs[TranscodeTranscodeFile](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetTranscodeTranscodeFile)]

## <a name="respond-to-transcoding-progress"></a><span data-ttu-id="b7cf2-157">Reaktion auf Transcodierungsfortschritt</span><span class="sxs-lookup"><span data-stu-id="b7cf2-157">Respond to transcoding progress</span></span>

<span data-ttu-id="b7cf2-158">Sie können Reaktionsereignisse registrieren, wenn sich der Fortschritt der asynchronen [**TranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700946)-Klasse ändert.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-158">You can register events to respond when the progress of the asynchronous [**TranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700946) changes.</span></span> <span data-ttu-id="b7cf2-159">Diese Ereignisse sind Teil des asynchronen Programmierungsframeworks für Apps für die universelle Windows-Plattform (UWP) und nicht für die Transcodierungs-API spezifisch.</span><span class="sxs-lookup"><span data-stu-id="b7cf2-159">These events are part of the async programming framework for Universal Windows Platform (UWP) apps and are not specific to the transcoding API.</span></span>

[!code-cs[TranscodeCallbacks](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetTranscodeCallbacks)]


## <a name="encode-a-metadata-stream"></a><span data-ttu-id="b7cf2-160">Codieren Sie einen Metadatenstrom</span><span class="sxs-lookup"><span data-stu-id="b7cf2-160">Encode a metadata stream</span></span>


 

 




