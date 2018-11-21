---
author: drewbatgit
ms.assetid: 05E418B4-5A62-42BD-BF66-A0762216D033
description: In diesem Thema wird das Abrufen eines einzelnen Vorschauframes aus dem Vorschaustream der Medienaufnahme beschrieben.
title: Abrufen eines Vorschauframes
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 211bd4ce660726030f8b90d29c4ea4d8a14564de
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7429663"
---
# <a name="get-a-preview-frame"></a><span data-ttu-id="9322c-104">Abrufen eines Vorschauframes</span><span class="sxs-lookup"><span data-stu-id="9322c-104">Get a preview frame</span></span>


<span data-ttu-id="9322c-105">In diesem Thema wird das Abrufen eines einzelnen Vorschauframes aus dem Vorschaustream der Medienaufnahme beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9322c-105">This topic shows you how to get a single preview frame from the media capture preview stream.</span></span>

> [!NOTE] 
> <span data-ttu-id="9322c-106">Dieser Artikel baut auf Konzepten und Codebeispielen auf, die unter [Allgemeine Foto-, Video- und Audioaufnahme mit „MediaCapture“](basic-photo-video-and-audio-capture-with-MediaCapture.md) erläutert werden. Dort werden die Schritte für die Implementierung einer grundlegenden Foto- und Videoaufnahme beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9322c-106">This article builds on concepts and code discussed in [Basic photo, video, and audio capture with MediaCapture](basic-photo-video-and-audio-capture-with-MediaCapture.md), which describes the steps for implementing basic photo and video capture.</span></span> <span data-ttu-id="9322c-107">Wir empfehlen Ihnen, sich mit dem grundlegenden Medienaufnahmemuster in diesem Artikel vertraut zu machen, bevor Sie sich komplexeren Aufnahmeszenarien zuwenden.</span><span class="sxs-lookup"><span data-stu-id="9322c-107">We recommend that you familiarize yourself with the basic media capture pattern in that article before moving on to more advanced capture scenarios.</span></span> <span data-ttu-id="9322c-108">Voraussetzung für den Code in diesem Artikel ist, dass Ihre App bereits über eine Instanz von MediaCapture verfügt, die ordnungsgemäß initialisiert wurde, und Sie ein [**CaptureElement**](https://msdn.microsoft.com/library/windows/apps/br209278) mit einem aktiven Videovorschaustream besitzen.</span><span class="sxs-lookup"><span data-stu-id="9322c-108">The code in this article assumes that your app already has an instance of MediaCapture that has been properly initialized, and that you have a [**CaptureElement**](https://msdn.microsoft.com/library/windows/apps/br209278) with an active video preview stream.</span></span>

<span data-ttu-id="9322c-109">Neben den Namespaces, die für eine einfache Medienaufzeichnung erforderlich sind, erfordert das Aufzeichnen eines Vorschauframes den folgenden Namespace.</span><span class="sxs-lookup"><span data-stu-id="9322c-109">In addition to the namespaces required for basic media capture, capturing a preview frame requires the following namespace.</span></span>

[!code-cs[PreviewFrameUsing](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetPreviewFrameUsing)]

<span data-ttu-id="9322c-110">Wenn Sie einen Vorschauframe anfordern, können Sie das Format angeben, in dem Sie den Frame empfangen möchten, indem Sie ein [**VideoFrame**](https://msdn.microsoft.com/library/windows/apps/dn930917)-Objekt im gewünschten Format erstellen.</span><span class="sxs-lookup"><span data-stu-id="9322c-110">When you request a preview frame, you can specify the format in which you would like to receive the frame by creating a [**VideoFrame**](https://msdn.microsoft.com/library/windows/apps/dn930917) object with the format you desire.</span></span> <span data-ttu-id="9322c-111">Dieses Beispiel erstellt einen Videoframe mit der gleichen Auflösung wie der Vorschaustream durch Aufrufen von [**VideoDeviceController.GetMediaStreamProperties**](https://msdn.microsoft.com/library/windows/apps/br211995) und Angeben von [**MediaStreamType.VideoPreview**](https://msdn.microsoft.com/library/windows/apps/br226640) zum Anfordern der Eigenschaften für den Vorschaustream.</span><span class="sxs-lookup"><span data-stu-id="9322c-111">This example creates a video frame that is the same resolution as the preview stream by calling [**VideoDeviceController.GetMediaStreamProperties**](https://msdn.microsoft.com/library/windows/apps/br211995) and specifying [**MediaStreamType.VideoPreview**](https://msdn.microsoft.com/library/windows/apps/br226640) to request the properties for the preview stream.</span></span> <span data-ttu-id="9322c-112">Die Breite und Höhe des Vorschaustreams werden zum Erstellen des neuen Videoframes verwendet.</span><span class="sxs-lookup"><span data-stu-id="9322c-112">The width and height of the preview stream is used to create the new video frame.</span></span>

[!code-cs[CreateFormatFrame](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetCreateFormatFrame)]

<span data-ttu-id="9322c-113">Wenn das [**MediaCapture**](https://msdn.microsoft.com/library/windows/apps/br241124)-Objekt initialisiert ist, und Sie einen aktiven Vorschaustream besitzen, rufen Sie [**GetPreviewFrameAsync**](https://msdn.microsoft.com/library/windows/apps/dn926711) auf, um einen Vorschauframe abzurufen.</span><span class="sxs-lookup"><span data-stu-id="9322c-113">If your [**MediaCapture**](https://msdn.microsoft.com/library/windows/apps/br241124) object is initialized and you have an active preview stream, call [**GetPreviewFrameAsync**](https://msdn.microsoft.com/library/windows/apps/dn926711) to get a preview stream.</span></span> <span data-ttu-id="9322c-114">Übergeben Sie den Videoframe, den Sie im letzten Schritt erstellt haben, um das Format des zurückgegebenen Frames anzugeben.</span><span class="sxs-lookup"><span data-stu-id="9322c-114">Pass in the video frame created in the last step to specify the format of the returned frame.</span></span>

[!code-cs[GetPreviewFrameAsync](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetGetPreviewFrameAsync)]

<span data-ttu-id="9322c-115">Rufen Sie eine [**SoftwareBitmap**](https://msdn.microsoft.com/library/windows/apps/dn887358)-Darstellung des Vorschauframes durch Zugriff auf die [**SoftwareBitmap**](https://msdn.microsoft.com/library/windows/apps/dn930926)-Eigenschaft des [**VideoFrame**](https://msdn.microsoft.com/library/windows/apps/dn930917)-Objekts ab.</span><span class="sxs-lookup"><span data-stu-id="9322c-115">Get a [**SoftwareBitmap**](https://msdn.microsoft.com/library/windows/apps/dn887358) representation of the preview frame by accessing the [**SoftwareBitmap**](https://msdn.microsoft.com/library/windows/apps/dn930926) property of the [**VideoFrame**](https://msdn.microsoft.com/library/windows/apps/dn930917) object.</span></span> <span data-ttu-id="9322c-116">Informationen zum Speichern, Laden und Ändern von Softwarebitmaps finden Sie unter [Imaging](imaging.md).</span><span class="sxs-lookup"><span data-stu-id="9322c-116">For information about saving, loading, and modifying software bitmaps, see [Imaging](imaging.md).</span></span>

[!code-cs[GetPreviewBitmap](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetGetPreviewBitmap)]

<span data-ttu-id="9322c-117">Sie können auch eine [**IDirect3DSurface**](https://msdn.microsoft.com/library/windows/apps/dn965505)-Darstellung des Vorschauframes abrufen, wenn Sie das Bild mit Direct3D-APIs verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="9322c-117">You can also get a [**IDirect3DSurface**](https://msdn.microsoft.com/library/windows/apps/dn965505) representation of the preview frame if you want to use the image with Direct3D APIs.</span></span>

[!code-cs[GetPreviewSurface](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetGetPreviewSurface)]

> [!IMPORTANT]
> <span data-ttu-id="9322c-118">Die Eigenschaft [**SoftwareBitmap**](https://msdn.microsoft.com/library/windows/apps/dn930926) oder die Eigenschaft [**Direct3DSurface**](https://msdn.microsoft.com/library/windows/apps/dn930920) des zurückgegebenen **VideoFrame** ist möglicherweise Null, abhängig davon, wie Sie **GetPreviewFrameAsync** aufrufen, und von dem Gerät, auf dem Ihre App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9322c-118">Either the [**SoftwareBitmap**](https://msdn.microsoft.com/library/windows/apps/dn930926) property or the [**Direct3DSurface**](https://msdn.microsoft.com/library/windows/apps/dn930920) property of the returned **VideoFrame** may be null depending on how you call **GetPreviewFrameAsync** and also depending on the device on which your app is running.</span></span>

> - <span data-ttu-id="9322c-119">Wenn Sie die Überladung von [**GetPreviewFrameAsync**](https://msdn.microsoft.com/library/windows/apps/dn926713) aufrufen, die ein **VideoFrame**-Argument akzeptiert, dann ist für den zurückgegebenen **VideoFrame** der **SoftwareBitmap**-Wert nicht Null, und die Eigenschaft **Direct3DSurface** ist Null.</span><span class="sxs-lookup"><span data-stu-id="9322c-119">If you call the overload of [**GetPreviewFrameAsync**](https://msdn.microsoft.com/library/windows/apps/dn926713) that accepts a **VideoFrame** argument, the returned **VideoFrame** will have a non-null **SoftwareBitmap** and the **Direct3DSurface** property will be null.</span></span>
> - <span data-ttu-id="9322c-120">Wenn Sie auf einem Gerät, das eine Direct3D-Oberfläche verwendet, um den Frame intern darzustellen, die Überladung von [**GetPreviewFrameAsync**](https://msdn.microsoft.com/library/windows/apps/dn926712) aufrufen, das keine Argumente besitzt, ist die Eigenschaft **Direct3DSurface** nicht Null und die Eigenschaft **SoftwareBitmap** ist Null.</span><span class="sxs-lookup"><span data-stu-id="9322c-120">If you call the overload of [**GetPreviewFrameAsync**](https://msdn.microsoft.com/library/windows/apps/dn926712) that has no arguments on a device that uses a Direct3D surface to represent the frame internally, the **Direct3DSurface** property will be non-null and the **SoftwareBitmap** property will be null.</span></span>
> - <span data-ttu-id="9322c-121">Wenn Sie auf einem Gerät, das keine Direct3D-Oberfläche verwendet, um den Frame intern darzustellen, die Überladung von [**GetPreviewFrameAsync**](https://msdn.microsoft.com/library/windows/apps/dn926712) aufrufen, das keine Argumente besitzt, ist die Eigenschaft **SoftwareBitmap** nicht Null und die Eigenschaft **Direct3DSurface** ist Null.</span><span class="sxs-lookup"><span data-stu-id="9322c-121">If you call the overload of [**GetPreviewFrameAsync**](https://msdn.microsoft.com/library/windows/apps/dn926712) that has no arguments on a device that does not use a Direct3D surface to represent the frame internally, the **SoftwareBitmap** property will be non-null and the **Direct3DSurface** property will be null.</span></span>

<span data-ttu-id="9322c-122">Ihre App sollte stets nach einem Null-Wert suchen, bevor versucht wird, Vorgänge für Objekte auszuführen, die von den Eigenschaften **SoftwareBitmap** oder **Direct3DSurface** zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="9322c-122">Your app should always check for a null value before trying to operate on the objects returned by the **SoftwareBitmap** or **Direct3DSurface** properties.</span></span>

<span data-ttu-id="9322c-123">Wenn Sie den Vorschauframe nicht mehr benötigen, rufen Sie auf jeden Fall die zugehörige [**Close**](https://msdn.microsoft.com/library/windows/apps/dn930918)-Methode auf (Dispose-Methode in C#), um die vom Frame verwendeten Ressourcen freizugeben.</span><span class="sxs-lookup"><span data-stu-id="9322c-123">When you are done using the preview frame, be sure to call its [**Close**](https://msdn.microsoft.com/library/windows/apps/dn930918) method (projected to Dispose in C#) to free the resources used by the frame.</span></span> <span data-ttu-id="9322c-124">Alternativ können Sie auch das Muster **using** verwenden, durch das das Objekt automatisch entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="9322c-124">Or, use the **using** pattern, which automatically disposes of the object.</span></span>

[!code-cs[CleanUpPreviewFrame](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetCleanUpPreviewFrame)]

## <a name="related-topics"></a><span data-ttu-id="9322c-125">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9322c-125">Related topics</span></span>

* [<span data-ttu-id="9322c-126">Kamera</span><span class="sxs-lookup"><span data-stu-id="9322c-126">Camera</span></span>](camera.md)
* [<span data-ttu-id="9322c-127">Allgemeine Foto-, Video- und Audioaufnahme mit „MediaCapture“</span><span class="sxs-lookup"><span data-stu-id="9322c-127">Basic photo, video, and audio capture with MediaCapture</span></span>](basic-photo-video-and-audio-capture-with-MediaCapture.md)
 

 




