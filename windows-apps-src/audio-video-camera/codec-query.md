---
author: drewbatgit
ms.assetid: 0A360481-B649-4E90-9BC4-4449BA7445EF
description: Führen Sie eine Abfrage nach Audio- und Video-Encodern und -Decodern durch, die auf einem Gerät installiert ist.
title: Abfrage nach installierten Codecs
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, Uwp, Codecs, Encoder, Decoder, Abfrage
ms.localizationpriority: medium
ms.openlocfilehash: b74ac269bcba6d15e7c4f5dcb4c34d53573deb5e
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7295082"
---
# <a name="query-for-codecs-installed-on-a-device"></a><span data-ttu-id="d758e-104">Abfrage installierter Codecs auf einem Gerät</span><span class="sxs-lookup"><span data-stu-id="d758e-104">Query for codecs installed on a device</span></span>
<span data-ttu-id="d758e-105">Mit der **[CodecQuery](https://docs.microsoft.com/uwp/api/windows.media.core.codecquery)**-Klasse können Sie auf dem aktuellen Gerät installierte Codecs abfragen.</span><span class="sxs-lookup"><span data-stu-id="d758e-105">The **[CodecQuery](https://docs.microsoft.com/uwp/api/windows.media.core.codecquery)** class allows you to query for codecs installed on the current device.</span></span> <span data-ttu-id="d758e-106">Die Liste der Codecs, die in Windows10 für andere Gerätefamilien enthalten sind, finden Sie im Artikel [Unterstützte Codecs](supported-codecs.md). Da aber Benutzer und Apps zusätzliche Codecs auf einem Gerät installieren können, sollten Sie zur Laufzeit die Codec-Unterstützung abfragen, um festzustellen, welche Codecs auf dem aktuellen Gerät verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="d758e-106">The list of codecs that are included with Windows 10 for different device families are listed in the article [Supported codecs](supported-codecs.md), but since users and apps can install additional codecs on a device, you may want to query for codec support at runtime to determine what codecs are available on the current device.</span></span>

<span data-ttu-id="d758e-107">Die CodecQuery-API ist ein Mitglied des **[Windows.Media.Core](https://docs.microsoft.com/uwp/api/windows.media.core)**-Namespace, daher müssen Sie diesen Namespace in Ihre App einbeziehen.</span><span class="sxs-lookup"><span data-stu-id="d758e-107">The CodecQuery API is a member of the **[Windows.Media.Core](https://docs.microsoft.com/uwp/api/windows.media.core)** namespace, so you will need to include this namespace in your app.</span></span>

<span data-ttu-id="d758e-108">Die CodecQuery-API ist ein Mitglied des **[Windows.Media.Core](https://docs.microsoft.com/uwp/api/windows.media.core)**-Namespace, daher müssen Sie diesen Namespace in Ihre App einbeziehen.</span><span class="sxs-lookup"><span data-stu-id="d758e-108">The CodecQuery API is a member of the **[Windows.Media.Core](https://docs.microsoft.com/uwp/api/windows.media.core)** namespace, so you will need to include this namespace in your app.</span></span>

[!code-cs[CodecQueryUsing](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetCodecQueryUsing)]

<span data-ttu-id="d758e-109">Initialisieren Sie eine neue Instanz der **CodecQuery**-Klasse, indem Sie den Konstruktor aufrufen.</span><span class="sxs-lookup"><span data-stu-id="d758e-109">Initialize a new instance of the **CodecQuery** class by calling the constructor.</span></span>

[!code-cs[NewCodecQuery](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetNewCodecQuery)]

<span data-ttu-id="d758e-110">Die **[FindAllAsync](https://docs.microsoft.com/uwp/api/windows.media.core.codecquery.findallasync)**-Methode gibt alle installierten Codecs zurück, die den angegebenen Parametern entsprechen.</span><span class="sxs-lookup"><span data-stu-id="d758e-110">The **[FindAllAsync](https://docs.microsoft.com/uwp/api/windows.media.core.codecquery.findallasync)** method returns all installed codecs that match the supplied parameters.</span></span> <span data-ttu-id="d758e-111">Diese Parameter umfassen einen **[CodecKind](https://docs.microsoft.com/uwp/api/windows.media.core.codeckind)**-Wert, der angibt, ob Sie Audio- oder Video-Codecs oder beide abfragen, einen **[CodecCategory](https://docs.microsoft.com/uwp/api/windows.media.core.codeccategory)**-Wert, der angibt, ob Sie Encoder oder Decoder abfragen, und eine Zeichenfolge, die den Untertyp der abgefragten Mediencodierung, z.B. H.264-Video oder MP3-Audio, angibt.</span><span class="sxs-lookup"><span data-stu-id="d758e-111">These parameters include a **[CodecKind](https://docs.microsoft.com/uwp/api/windows.media.core.codeckind)** value specifying whether you are querying for audio or video codecs or both, a **[CodecCategory](https://docs.microsoft.com/uwp/api/windows.media.core.codeccategory)** value specifying whether you are querying for encoders or decoders, and a string that represents the media encoding subtype for which you are querying, such as H.264 video or MP3 audio.</span></span>

<span data-ttu-id="d758e-112">Geben Sie eine leere Zeichenfolge oder null für den Untertypwert an, um Codecs für alle Untertypen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="d758e-112">Specify empty string or null for the subtype value to return codecs for all subtypes.</span></span> <span data-ttu-id="d758e-113">Im folgenden Beispiel werden alle auf dem Gerät installierten Video-Encoder aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="d758e-113">The following example lists all of the video encoders installed on the device.</span></span>

[!code-cs[FindAllEncoders](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetFindAllEncoders)]

<span data-ttu-id="d758e-114">Die Untertypzeichenfolge, die Sie an **FindAllAsync** übergeben, kann entweder eine Zeichenfolgendarstellung des Untertyps GUID, die vom System definiert wird, oder ein FOURCC-Code für den Untertyp sein.</span><span class="sxs-lookup"><span data-stu-id="d758e-114">The subtype string you pass into **FindAllAsync** can either be a string representation of the subtype GUID which is defined by the system or a FOURCC code for the subtype.</span></span> <span data-ttu-id="d758e-115">Die unterstützten [Medienuntertyp-GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa372553(v=vs.85).aspx) sind in den Artikeln [Videountertyp-GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa370819(v=vs.85).aspx) und Videountertyp-GUIDs aufgeführt, die **[CodecSubtypes](https://docs.microsoft.com/uwp/api/windows.media.core.codecsubtypes)**-Klasse stellt aber Eigenschaften bereit, die die GUID-Werte für jeden unterstützten Untertyp zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="d758e-115">The set of supported media subtype GUIDs are listed in the articles [Audio Subtype GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa372553(v=vs.85).aspx) and [Video Subtype GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa370819(v=vs.85).aspx), but the **[CodecSubtypes](https://docs.microsoft.com/uwp/api/windows.media.core.codecsubtypes)** class provides properties that return the GUID values for each supported subtype.</span></span> <span data-ttu-id="d758e-116">Weitere Informationen zu FOURCC-Codes finden Sie unter [FOURCC-Codes](https://msdn.microsoft.com/library/windows/desktop/dd375802(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="d758e-116">For more information on FOURCC codes, see [FOURCC Codes](https://msdn.microsoft.com/library/windows/desktop/dd375802(v=vs.85).aspx)</span></span> 

<span data-ttu-id="d758e-117">Im folgenden Beispiel wird der FOURCC-Code „H264“ festgelegt, um zu ermitteln, ob ein H.264-Video-Decoder auf dem Gerät installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d758e-117">The following example specifies the FOURCC code "H264" to determine if there is an H.264 video decoder installed on the device.</span></span> <span data-ttu-id="d758e-118">Sie können diese Abfrage ausführen, bevor Sie versuchen, H.264-Video-Inhalte wiederzugeben.</span><span class="sxs-lookup"><span data-stu-id="d758e-118">You could perform this query before attempting to play back H.264 video content.</span></span> <span data-ttu-id="d758e-119">Sie können auch nicht unterstützte Codecs bei der Wiedergabe behandeln.</span><span class="sxs-lookup"><span data-stu-id="d758e-119">You can also handle unsupported codecs at playback time.</span></span> <span data-ttu-id="d758e-120">Weitere Informationen finden Sie unter [Behandeln von nicht unterstützten Codecs und unbekannten Fehlern beim Öffnen von Medienelementen](https://docs.microsoft.com/windows/uwp/audio-video-camera/media-playback-with-mediasource#handle-unsupported-codecs-and-unknown-errors-when-opening-media-items).</span><span class="sxs-lookup"><span data-stu-id="d758e-120">For more information, see [Handle unsupported codecs and unknown errors when opening media items](https://docs.microsoft.com/windows/uwp/audio-video-camera/media-playback-with-mediasource#handle-unsupported-codecs-and-unknown-errors-when-opening-media-items).</span></span>

[!code-cs[IsH264Supported](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetIsH264Supported)]

<span data-ttu-id="d758e-121">Im folgenden Beispiel wird abgefragt, ob ein FLAC-Audio-Encoder auf dem aktuellen Gerät installiert ist. Wenn ja, wird ein **[MediaEncodingProfile](https://docs.microsoft.com/uwp/api/Windows.Media.MediaProperties.MediaEncodingProfile)** für den Untertyp erstellt, mit dem Audioinhalt in eine Datei aufgenommen oder Audioinhalt aus einem anderen Format in eine FLAC-Audiodatei transkodiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="d758e-121">The following example queries to determine if a FLAC audio encoder is installed on the current device and, if so, a **[MediaEncodingProfile](https://docs.microsoft.com/uwp/api/Windows.Media.MediaProperties.MediaEncodingProfile)** is created for the subtype which could be used for capturing audio to a file or transcoding audio from another format to a FLAC audio file.</span></span>

[!code-cs[IsFLACSupported](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetIsFLACSupported)]

## <a name="related-topics"></a><span data-ttu-id="d758e-122">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d758e-122">Related topics</span></span>

* [<span data-ttu-id="d758e-123">Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="d758e-123">Media playback</span></span>](media-playback.md)
* [<span data-ttu-id="d758e-124">Allgemeine Foto-, Video- und Audioaufnahme mit MediaCapture</span><span class="sxs-lookup"><span data-stu-id="d758e-124">Basic photo, video, and audio capture with MediaCapture</span></span>](basic-photo-video-and-audio-capture-with-MediaCapture.md)
* [<span data-ttu-id="d758e-125">Transkodieren von Mediendateien</span><span class="sxs-lookup"><span data-stu-id="d758e-125">Transcode media files</span></span>](transcode-media-files.md)
* [<span data-ttu-id="d758e-126">Unterstützte Codecs</span><span class="sxs-lookup"><span data-stu-id="d758e-126">Supported codecs</span></span>](supported-codecs.md)
 

 




