---
title: Hosting-Vorschau für Kamera-Strichcodescanner
description: Hier erfahren Sie, wie Sie die Vorschau für Kamera-Strichcodescanner in Ihrer Anwendung hosten
ms.date: 05/02/2018
ms.topic: article
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 49d531ea2e699afaf7cfb6872fe0287c6d6a8f85
ms.sourcegitcommit: 079801609165bc7eb69670d771a05bffe236d483
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2019
ms.locfileid: "9116119"
---
# <a name="hosting-a-camera-barcode-scanner-preview-in-your-application"></a>Die Vorschau für Kamera-Strichcodescanner in Ihrer Anwendung hosten
## <a name="step-1-setup-your-camera-preview"></a>Schritt1: Einrichten der Kameravorschau
Der erste Schrittbeim Hinzufügen einer Vorschau Ihrer Anwendung für Kamera-Strichcodescanner kann mithilfe der Anweisungen im Thema [Anzeigen der Kameravorschau](../audio-video-camera/simple-camera-preview-access.md) erreicht werden.  Nachdem Sie diesen Schrittabgeschlossen haben, kehren Sie zu diesem Thema zurück, um Änderungen am Kamera-Strichcodescanner vorzunehmen.

## <a name="step-2-update-capability-declarations"></a>Schritt 2: Aktualisieren der Deklarationen der Funktionen
Um zu verhindern, dass Ihre Benutzer die Zustimmungsaufforderung für das Mikrofon erhalten, können Sie dies von den aufgeführten Funktionen im App-Manifest ausschließen.

1. Öffnen Sie in MicrosoftVisual Studio im **Projektmappen-Explorer** den Designer für das Anwendungsmanifest, indem Sie auf das Element **package.appxmanifest** doppelklicken.
2. Wählen Sie die Registerkarte **Funktionen** aus.
3. Deaktivieren Sie das Kontrollkästchen für **Mikrofon**.

 ## <a name="step-3-add-additional-using-directive-for-media-capture"></a>Schritt 3: Hinzufügen von zusätzlichen using-Direktiven für Medienaufnahme

```Csharp
using Windows.Media.Capture;
```

## <a name="step-4-set-up-your-mediacapture-initialization-settings"></a>Schritt4: Einrichten der Einstellungen für die MediaCapture-Initialisierung
Die folgende Beispiel wird [**MediaCaptureInitializationSettings**](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings) initialisiert. 

```Csharp
 private void InitCaptureSettings()
{
    _captureInitSettings = new MediaCaptureInitializationSettings();
    _captureInitSettings.VideoDeviceId = BarcodeScanner.VideoDeviceId;
    _captureInitSettings.StreamingCaptureMode = StreamingCaptureMode.Video;
    _captureInitSettings.PhotoCaptureSource = PhotoCaptureSource.VideoPreview;
}
```
## <a name="step-5-associate-your-mediacapture-object-with-the-camera-barcode-scanner"></a>Schritt5: Ordnen Sie den Kamera-Strichcodescanner dem MediaCapture-Objekt zu
Ersetzen Sie den vorhandenen mediaCapture.InitializeAsync() in *StartPreviewAsync()* durch:

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
> Unter [Anzeigen der Kameravorschau](https://docs.microsoft.com/windows/uwp/audio-video-camera/simple-camera-preview-access#add-capability-declarations-to-the-app-manifest) finden Sie weitere Informationen und erweiterte Themen zum Hosten einer Kameravorschau in Ihrer Anwendung.
