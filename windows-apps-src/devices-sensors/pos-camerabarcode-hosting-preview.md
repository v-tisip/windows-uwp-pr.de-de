---
title: Hosting-Vorschau für Kamera-Strichcodescanner
description: Hier erfahren Sie, wie Sie die Vorschau für Kamera-Strichcodescanner in Ihrer Anwendung hosten
ms.date: 05/1/2018
ms.topic: article
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 0eb7b1b620fcfa16576d84eaa2564408394d59de
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7826273"
---
# <a name="hosting-a-camera-barcode-scanner-preview-in-your-application"></a><span data-ttu-id="d377a-104">Die Vorschau für Kamera-Strichcodescanner in Ihrer Anwendung hosten</span><span class="sxs-lookup"><span data-stu-id="d377a-104">Hosting a camera barcode scanner preview in your application</span></span>
## <a name="step-1-setup-your-camera-preview"></a><span data-ttu-id="d377a-105">Schritt1: Einrichten der Kameravorschau</span><span class="sxs-lookup"><span data-stu-id="d377a-105">Step 1: Setup your camera preview</span></span>
<span data-ttu-id="d377a-106">Der erste Schrittbeim Hinzufügen einer Vorschau Ihrer Anwendung für Kamera-Strichcodescanner kann mithilfe der Anweisungen im Thema [Anzeigen der Kameravorschau](../audio-video-camera/simple-camera-preview-access.md) erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="d377a-106">The first step in adding a preview to your application for camera barcode scanner can be accomplished by following the instructions in the [Display the camera preview](../audio-video-camera/simple-camera-preview-access.md) topic.</span></span>  <span data-ttu-id="d377a-107">Nachdem Sie diesen Schrittabgeschlossen haben, kehren Sie zu diesem Thema zurück, um Änderungen am Kamera-Strichcodescanner vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="d377a-107">Once you have completed this step, return to this topic for camera barcode scanner specific modifications.</span></span>

## <a name="step-2-update-capability-declarations"></a><span data-ttu-id="d377a-108">Schritt 2: Aktualisieren der Deklarationen der Funktionen</span><span class="sxs-lookup"><span data-stu-id="d377a-108">Step 2: Update capability declarations</span></span>
<span data-ttu-id="d377a-109">Um zu verhindern, dass Ihre Benutzer die Zustimmungsaufforderung für das Mikrofon erhalten, können Sie dies von den aufgeführten Funktionen im App-Manifest ausschließen.</span><span class="sxs-lookup"><span data-stu-id="d377a-109">To prevent your users from receiving the consent prompt for microphone you can exclude this from the capabilities listed in your app manifest.</span></span>

1. <span data-ttu-id="d377a-110">Öffnen Sie in MicrosoftVisual Studio im **Projektmappen-Explorer** den Designer für das Anwendungsmanifest, indem Sie auf das Element **package.appxmanifest** doppelklicken.</span><span class="sxs-lookup"><span data-stu-id="d377a-110">In Microsoft Visual Studio, in **Solution Explorer**, open the designer for the application manifest by double-clicking the **package.appxmanifest** item.</span></span>
2. <span data-ttu-id="d377a-111">Wählen Sie die Registerkarte **Funktionen** aus.</span><span class="sxs-lookup"><span data-stu-id="d377a-111">Select the **Capabilities** tab.</span></span>
3. <span data-ttu-id="d377a-112">Deaktivieren Sie das Kontrollkästchen für **Mikrofon**.</span><span class="sxs-lookup"><span data-stu-id="d377a-112">Uncheck the box for **Microphone**</span></span>

 ## <a name="step-3-add-additional-using-directive-for-media-capture"></a><span data-ttu-id="d377a-113">Schritt 3: Hinzufügen von zusätzlichen using-Direktiven für Medienaufnahme</span><span class="sxs-lookup"><span data-stu-id="d377a-113">Step 3: Add additional using directive for media capture</span></span>

```Csharp
using Windows.Media.Capture;
```

## <a name="step-4-set-up-your-mediacapture-initialization-settings"></a><span data-ttu-id="d377a-114">Schritt4: Einrichten der Einstellungen für die MediaCapture-Initialisierung</span><span class="sxs-lookup"><span data-stu-id="d377a-114">Step 4: Set up your MediaCapture initialization settings</span></span>
<span data-ttu-id="d377a-115">Die folgende Beispiel wird [**MediaCaptureInitializationSettings**](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings) initialisiert.</span><span class="sxs-lookup"><span data-stu-id="d377a-115">The following example initializes the [**MediaCaptureInitializationSettings**](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings).</span></span> 

```Csharp
 private void InitCaptureSettings()
{
    _captureInitSettings = new MediaCaptureInitializationSettings();
    _captureInitSettings.VideoDeviceId = BarcodeScanner.VideoDeviceId;
    _captureInitSettings.StreamingCaptureMode = StreamingCaptureMode.Video;
    _captureInitSettings.PhotoCaptureSource = PhotoCaptureSource.VideoPreview;
}
```
## <a name="step-5-associate-your-mediacapture-object-with-the-camera-barcode-scanner"></a><span data-ttu-id="d377a-116">Schritt5: Ordnen Sie den Kamera-Strichcodescanner dem MediaCapture-Objekt zu</span><span class="sxs-lookup"><span data-stu-id="d377a-116">Step 5: Associate your MediaCapture object with the camera barcode scanner</span></span>
<span data-ttu-id="d377a-117">Ersetzen Sie den vorhandenen mediaCapture.InitializeAsync() in *StartPreviewAsync()* durch:</span><span class="sxs-lookup"><span data-stu-id="d377a-117">Replace the existing mediaCapture.InitializeAsync() in *StartPreviewAsync()* with the following:</span></span>

```Csharp
try
    {

        mediaCapture = new MediaCapture();
        await mediaCapture.InitializeAsync(InitCaptureSettings());

        displayRequest.RequestActive();
        DisplayInformation.AutoRotationPreferences = DisplayOrientations.Landscape;
    }
```

> [!TIP]
> <span data-ttu-id="d377a-118">Unter [Anzeigen der Kameravorschau](https://docs.microsoft.com/windows/uwp/audio-video-camera/simple-camera-preview-access#add-capability-declarations-to-the-app-manifest) finden Sie weitere Informationen und erweiterte Themen zum Hosten einer Kameravorschau in Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="d377a-118">See [Display the camera preview](https://docs.microsoft.com/windows/uwp/audio-video-camera/simple-camera-preview-access#add-capability-declarations-to-the-app-manifest) for more advanced topics on hosting a camera preview in your application.</span></span>
