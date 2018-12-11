---
description: In diesem Artikel wird erläutert, wie Sie die LowLightFusion-Klasse zum Verarbeiten von Bitmaps nutzen.
title: Verarbeitung von Bitmaps mit der Low Light Fusion-API
ms.date: 03/22/2018
ms.topic: article
keywords: Windows10, Uwp, low light Fusion, Bitmaps, bildbearbeitung
ms.localizationpriority: medium
ms.openlocfilehash: e0677d2e4ce5e412c158b8a00da3a6338bae6c46
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8895900"
---
# <a name="process-bitmaps-with-the-lowlightfusion-api"></a><span data-ttu-id="99091-104">Verarbeitung von Bitmaps mit der LowLightFusion-API</span><span class="sxs-lookup"><span data-stu-id="99091-104">Process bitmaps with the LowLightFusion API</span></span>

<span data-ttu-id="99091-105">Bilder bei schwachem Licht lassen sich nur schwer mit guter Bildqualität aufnehmen, vor allem auf mobilen Geräten mit fester Blende und Sensorgröße.</span><span class="sxs-lookup"><span data-stu-id="99091-105">Low-light images are difficult to capture with good image quality, especially on mobile devices with fixed aperture and sensor size.</span></span> <span data-ttu-id="99091-106">Zur Kompensation von schlechten Lichtverhältnissen können Geräte die Belichtungszeit oder Sensorverstärkung erhöhen, was zu Bewegungsunschärfe und erhöhtem Bildrauschen führen kann.</span><span class="sxs-lookup"><span data-stu-id="99091-106">To compensate for low-lighting, devices may increase exposure time or sensor gain, which can lead to motion blur and increased noise in images.</span></span> 

<span data-ttu-id="99091-107">Die [LowLightFusion](https://docs.microsoft.com/uwp/api/windows.media.core.lowlightfusion)-Klasse verbessert die Qualität von Bildern bei schwachem Licht durch Abtastung von Pixelinformationen aus mehreren Bildern in unmittelbarer zeitlicher Nähe, d. h. kurze Burst-Bilder, um Rauschen und Bewegungsunschärfe zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="99091-107">The [LowLightFusion class](https://docs.microsoft.com/uwp/api/windows.media.core.lowlightfusion) improves the quality of low-light images by sampling pixel information from multiple frames in close temporal proximity, i.e., short burst images, to reduce noise and motion blur.</span></span> <span data-ttu-id="99091-108">Dies ist z. B. nützlich, um eine Fotobearbeitungsanwendung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="99091-108">This is useful capability to add to a photo editing app, for example.</span></span>

<span data-ttu-id="99091-109">Diese Funktion wird auch durch die [AdvancedPhotoCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AdvancedPhotoCapture)-Klasse zur Verfügung gestellt, die den Low Light Fusion-Algorithmus bei Bedarf auf eine Reihe von Bildern direkt nach der Aufnahme anwendet.</span><span class="sxs-lookup"><span data-stu-id="99091-109">This feature is also made available through the [AdvancedPhotoCapture class](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AdvancedPhotoCapture), which applies the Low Light Fusion algorithm to a sequence of images directly after the images are captured, if needed.</span></span> <span data-ttu-id="99091-110">Weitere Informationen zur Implementierung dieser Funktion finden Sie unter [Fotoaufnahme bei schlechten Lichtverhältnissen](https://docs.microsoft.com/windows/uwp/audio-video-camera/high-dynamic-range-hdr-photo-capture#low-light-photo-capture).</span><span class="sxs-lookup"><span data-stu-id="99091-110">See [Low-light photo](https://docs.microsoft.com/windows/uwp/audio-video-camera/high-dynamic-range-hdr-photo-capture#low-light-photo-capture) capture to learn how to implement this feature.</span></span>

## <a name="prepare-the-images-for-processing"></a><span data-ttu-id="99091-111">Vorbereiten von Bildern für die Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="99091-111">Prepare the images for processing</span></span>

<span data-ttu-id="99091-112">In diesem Beispiel zeigen wir Ihnen, wie Sie die [LowLightFusion](https://docs.microsoft.com/uwp/api/windows.media.core.lowlightfusion)-Klasse und den [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) verwenden können, damit ein Benutzer mehrere Bilder auswählen kann, um Low Light Fusion-durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="99091-112">In this example, we'll demonstrate how to use the [LowLightFusion class](https://docs.microsoft.com/uwp/api/windows.media.core.lowlightfusion), as well as the [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) to allow a user to select multiple images to perform Low Light Fusion on.</span></span>

<span data-ttu-id="99091-113">Zuerst müssen wir herausfinden, wie viele Bilder (auch als Frames bekannt) der Algorithmus akzeptiert, und eine Liste erstellen, um diese Frames zu halten.</span><span class="sxs-lookup"><span data-stu-id="99091-113">First, we'll need to determine how many images (also known as frames) the algorithm accepts, and create a list to hold these frames.</span></span>

[!code-cs[SnippetGetMaxLLFFrames](./code/LowLightFusionSample/cs/MainPage.xaml.cs#SnippetGetMaxLLFFrames)]

<span data-ttu-id="99091-114">Sobald wir festgelegt haben, wie viele Frames der Low Light Fusion-Algorithmus akzeptiert, können wir [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) verwenden, um den Benutzer auswählen zu lassen, welche Bilder im Algorithmus verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="99091-114">Once we determine how many frames the Low Light Fusion algorithm accepts, we can use the [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) to allow the user to choose which images should be used in the algorithm.</span></span>

[!code-cs[SnippetGetFrames](./code/LowLightFusionSample/cs/MainPage.xaml.cs#SnippetGetFrames)]

<span data-ttu-id="99091-115">Nachdem wir nun die richtige Anzahl von Frames ausgewählt haben, müssen wir die Frames in [SoftwareBitmaps](https://docs.microsoft.com/uwp/api/Windows.Graphics.Imaging.SoftwareBitmap) dekodieren und sicherstellen, dass die SoftwareBitmaps im richtigen Format für LowLightFusion vorliegen.</span><span class="sxs-lookup"><span data-stu-id="99091-115">Now that we have the correct number of frames selected, we need to decode the frames into [SoftwareBitmaps](https://docs.microsoft.com/uwp/api/Windows.Graphics.Imaging.SoftwareBitmap) and ensure that the SoftwareBitmaps are in the correct format for LowLightFusion.</span></span>

[!code-cs[SnippetDecodeFrames](./code/LowLightFusionSample/cs/MainPage.xaml.cs#SnippetDecodeFrames)]


## <a name="fuse-the-bitmaps-into-a-single-bitmap"></a><span data-ttu-id="99091-116">Verarbeiten der Bitmaps zu einer einzigen Bitmap</span><span class="sxs-lookup"><span data-stu-id="99091-116">Fuse the bitmaps into a single bitmap</span></span>

<span data-ttu-id="99091-117">Da wir nun eine korrekte Anzahl von Frames in einem akzeptablen Format haben, können wir die **[FuseAsync](https://docs.microsoft.com/uwp/api/windows.media.core.lowlightfusion.fuseasync)**-Methode verwenden, um den Low Light Fusion-Algorithmus anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="99091-117">Now that we have a correct number of frames in an acceptable format, we can use the **[FuseAsync](https://docs.microsoft.com/uwp/api/windows.media.core.lowlightfusion.fuseasync)** method to apply the Low Light Fusion algorithm.</span></span> <span data-ttu-id="99091-118">Unser Ergebnis wird das bearbeitete Bild mit verbesserter Klarheit in Form einer SoftwareBitmap sein.</span><span class="sxs-lookup"><span data-stu-id="99091-118">Our result will be the processed image, with improved clarity, in the form of a SoftwareBitmap.</span></span> 

[!code-cs[SnippetFuseFrames](./code/LowLightFusionSample/cs/MainPage.xaml.cs#SnippetFuseFrames)]

<span data-ttu-id="99091-119">Schließlich bereinigen wir die resultierende SoftwareBitmap, indem wir sie kodieren und in ein benutzerfreundliches, „normales“ Bild speichern, ähnlich den Eingangsbildern, mit denen wir begonnen haben.</span><span class="sxs-lookup"><span data-stu-id="99091-119">Finally, we'll clean up the resulting SoftwareBitmap by encoding and saving it into a user friendly, "regular" image, similar to the input images that we started with.</span></span>

[!code-cs[SnippetEncodeFrame](./code/LowLightFusionSample/cs/MainPage.xaml.cs#SnippetEncodeFrame)]


## <a name="before-and-after"></a><span data-ttu-id="99091-120">Vorher und nachher</span><span class="sxs-lookup"><span data-stu-id="99091-120">Before and after</span></span>

<span data-ttu-id="99091-121">Hier ist ein Beispiel für zwei Eingangsbilder und das resultierende Ausgangsbild nach Anwendung des Low Light Fusion Algorithmus.</span><span class="sxs-lookup"><span data-stu-id="99091-121">Here's an example of an input image and the resulting output image after applying the Low Light Fusion algorithm.</span></span>

> [!div class="mx-tableFixed"] 
| <span data-ttu-id="99091-122">Eingabeframe</span><span class="sxs-lookup"><span data-stu-id="99091-122">Input Frame</span></span> | <span data-ttu-id="99091-123">Low Light Fusion-Ausgabe</span><span class="sxs-lookup"><span data-stu-id="99091-123">Low Light Fusion Output</span></span> | 
|-------------|-------------------------|
| ![Eingabeframe für den Low Light Fusion Algorithmus](./images/LLF-Input.png) | ![Ergebnisframe des Low Light Fusion Algorithmus](./images/LLF-Output.png) |

<span data-ttu-id="99091-126">Die Eingabeframe zeigt, dass die Beleuchtung und die Klarheit des das Banner umgebenen Schattens verbessert wurde.</span><span class="sxs-lookup"><span data-stu-id="99091-126">You can see from the input frame that the lighting and the clarity of the shadows surrounding the banner have been improved.</span></span>

## <a name="related-topics"></a><span data-ttu-id="99091-127">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="99091-127">Related topics</span></span> 
[<span data-ttu-id="99091-128">LowLightFusion-Klasse</span><span class="sxs-lookup"><span data-stu-id="99091-128">LowLightFusion Class</span></span>](https://docs.microsoft.com/uwp/api/windows.media.core.lowlightfusion)  
[<span data-ttu-id="99091-129">LowLightFusionResult-Klasse</span><span class="sxs-lookup"><span data-stu-id="99091-129">LowLightFusionResult Class</span></span>](https://docs.microsoft.com/uwp/api/windows.media.core.lowlightfusionresult)