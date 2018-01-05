---
author: drewbatgit
ms.assetid: 
description: "Dieser Artikel zeigt Ihnen, wie Sie Videos aus mehreren Quellen gleichzeitig in eine einzige Datei mit mehreren eingebetteten Videospuren aufnehmen können."
title: Erfassen von mehreren Quellen mit MediaFrameSourceGroup
ms.author: drewbat
ms.date: 09/12/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Aufnahme, Video
ms.localizationpriority: medium
ms.openlocfilehash: 56996cf9edb5aef317421e5ca8eef05153328bf9
ms.sourcegitcommit: f9a4854b6aecfda472fb3f8b4a2d3b271b327800
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="capture-from-multiple-sources-using-mediaframesourcegroup"></a>Erfassen von mehreren Quellen mit MediaFrameSourceGroup

Dieser Artikel zeigt Ihnen, wie Sie Videos aus mehreren Quellen gleichzeitig in eine einzige Datei mit mehreren eingebetteten Videospuren aufnehmen können. Ab RS3 können Sie mehrere **[VideoStreamDescriptor](https://docs.microsoft.com/uwp/api/windows.media.core.videostreamdescriptor)**-Objekte für ein einzelnes **[MediaEncodingProfile](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile)** angeben. Dadurch können Sie mehrere Streams gleichzeitig in eine einzige Datei kodieren. Die Videoströme, die in diesem Vorgang kodiert werden, müssen in einer einzigen **[MediaFrameSourceGroup](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.mediaframesourcegroup)** enthalten sein, die eine Reihe von Kameras auf dem aktuellen Gerät angibt, die gleichzeitig verwendet werden können. 

Weitere Informationen zur Verwendung von **[MediaFrameSourceGroup](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.mediaframesourcegroup)** in Verbindung mit der **[MediaFrameReader](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.mediaframereader)**-Klasse zur Aktivierung von Echtzeit-Szenarien für Computer-Vision, die mehrere Kameras verwenden, finden Sie unter [Verarbeiten von Medienframes mit MediaFrameReader](process-media-frames-with-mediaframereader.md).

Der Rest dieses Artikels wird Sie durch die Schritte der Aufnahme von Videos von zwei Farbkameras zu einer einzigen Datei mit mehreren Videospuren führen.

## <a name="find-available-sensor-groups"></a>Verfügbare Sensorgruppen finden
Eine **MediaFrameSourceGroup** stellt eine Sammlung von Bildquellen, typischerweise Kameras, dar, auf die gleichzeitig zugegriffen werden kann. Der erste Schritt in diesem Beispiel besteht also darin, die Liste der verfügbaren Bildquellengruppen zu erhalten und eine zu finden, die die notwendigen Kameras für das Szenario enthält, das in diesem Fall zwei Farbkameras benötigt.

Die Methode **[MediaFrameSourceGroup.FindAllAsync](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.mediaframesourcegroup#Windows_Media_Capture_Frames_MediaFrameSourceGroup_FindAllAsync)** liefert alle auf dem aktuellen Gerät verfügbaren Quellgruppen zurück. Jede zurückgegebene **MediaFrameSourceGroup** hat eine Liste von **[MediaFrameSourceInfo](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.mediaframesourceinfo)**-Objekten, die jede Frame-Quelle in der Gruppe beschreibt. Eine Linq-Abfrage wird verwendet, um eine Quellengruppe zu finden, die zwei Farbkameras enthält, eine auf der Vorderseite und eine auf der Rückseite. Für jede Farbkamera wird ein anonymes Objekt zurückgegeben, das die ausgewählte **MediaFrameSourceGroup** und die **MediaFrameSourceInfo** enthält. Anstatt den Linq-Syntax zu verwenden, können Sie jede Gruppe und dann jede **MediaFrameSourceInfo** durchgehen, um nach einer Gruppe zu suchen, die Ihren Anforderungen entspricht.

Beachten Sie, dass nicht jedes Gerät eine Quellgruppe mit zwei Farbkameras enthält. Überprüfen Sie daher, ob eine Quellgruppe gefunden wurde, bevor Sie versuchen, ein Video aufzunehmen.

[!code-cs[MultiRecordFindSensorGroups](./code/SimpleCameraPreview_Win10/cs/MainPage.MultiRecord.xaml.cs#SnippetMultiRecordFindSensorGroups)]

## <a name="initialize-the-mediacapture-object"></a>Initialisieren des MediaCapture-Objekts
Die **[MediaCapture](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture)**-Klasse ist die primäre Klasse, die für die meisten Audio-, Video- und Foto-Capture-Operationen in UWP-Anwendungen verwendet wird. Initialisieren Sie das Objekt durch Aufruf von **[InitializeAsync](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture#Windows_Media_Capture_MediaCapture_InitializeAsync)**, indem Sie ein **[MediaCaptureInitializationSettings](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings)**-Objekt übergeben, das Initialisierungsparameter enthält. In diesem Beispiel ist die einzige angegebene Einstellung die **[SourceGroup](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings#Windows_Media_Capture_MediaCaptureInitializationSettings_SourceGroup)**-Eigenschaft, die auf die **MediaFrameSourceGroup** gesetzt ist, die im vorherigen Code-Beispiel abgerufen wurde.

Weitere Informationen zu anderen Operationen, die Sie mit **MediaCapture** und anderen UWP-Funktionen für das Capturing von Medien durchführen können, finden Sie unter [Kamera](camera.md).

[!code-cs[MultiRecordInitMediaCapture](./code/SimpleCameraPreview_Win10/cs/MainPage.MultiRecord.xaml.cs#SnippetMultiRecordInitMediaCapture)]

## <a name="create-a-mediaencodingprofile"></a>Erstellen eines MediaEncodingProfiles
Die Klasse **[MediaEncodingProfil](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile)** gibt der Pipeline für die Medienerfassung an, wie Audio- und Video-Captures beim Schreiben in eine Datei kodiert werden sollen. Für typische Capture- und Transcoding-Szenarien bietet diese Klasse eine Reihe statischer Methoden zur Erstellung gemeinsamer Profile, wie **[CreateAvi](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile#Windows_Media_MediaProperties_MediaEncodingProfile_CreateAvi_Windows_Media_MediaProperties_VideoEncodingQuality_)** und **[CreateMp3](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile#Windows_Media_MediaProperties_MediaEncodingProfile_CreateMp3_Windows_Media_MediaProperties_AudioEncodingQuality_)**. Für dieses Beispiel wird manuell ein Kodierungsprofil mit einem Mpeg4-Container und H264-Videokodierung erstellt. Die Videocodierungseinstellungen werden über ein **[VideoEncodingProperties](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.videoencodingproperties)**-Objekt festgelegt. Für jede in diesem Szenario verwendete Farbkamera wird ein **VideoStreamDescriptor**-Objekt konfiguriert. Der Deskriptor wird mit dem **VideoEncodingProperties**-Objekt konstruiert, das die Kodierung angibt. Die **[Label](https://docs.microsoft.com/uwp/api/windows.media.core.videostreamdescriptor#Windows_Media_Core_VideoStreamDescriptor_Label)**-Eigenschaft des **VideoStreamDescriptors** muss auf die ID der Medien-Frame-Quelle gesetzt werden, die in den Stream aufgenommen wird. So weiß die Capture-Pipeline, welche Stream-Deskriptor- und Encoding-Eigenschaften für jede Kamera verwendet werden sollten. Die ID der Bildquelle wird von den **[MediaFrameSourceInfo](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.mediaframesourceinfo)**-Objekten, die im vorherigen Abschnitt gefunden wurden, angezeigt, wenn eine **MediaFrameSourceGroup** ausgewählt wurde.


Ab RS3 können Sie mehrere Encoding-Eigenschaften auf einem **MediaEncodingProfil** einstellen, indem Sie **[SetVideoTracks](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile#Windows_Media_MediaProperties_MediaEncodingProfile_SetVideoTracks_Windows_Foundation_Collections_IIterable_Windows_Media_Core_VideoStreamDescriptor__)** aufrufen. Sie können die Liste der Videostream-Deskriptoren abrufen, indem Sie **[GetVideoTracks](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile#Windows_Media_MediaProperties_MediaEncodingProfile_GetVideoTracks)** aufrufen. Beachten Sie, dass beim Festlegen der **[Video](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile#Windows_Media_MediaProperties_MediaEncodingProfile_Video)**-Eigenschaft, die einen einzelnen Stream-Deskriptor speichert, die von Ihnen über das Aufrufen von **SetVideoTracks** festgelegt Deskriptor-Liste durch eine Liste mit dem einzelnen angegebenen Deskriptor ersetzt wird.


[!code-cs[MultiRecordMediaEncodingProfile](./code/SimpleCameraPreview_Win10/cs/MainPage.MultiRecord.xaml.cs#SnippetMultiRecordMediaEncodingProfile)]

## <a name="record-using-the-multi-stream-mediaencodingprofile"></a>Aufzeichnung mit dem Multi-Stream-MediaEncodingProfil
Der letzte Schritt in diesem Beispiel ist es, die Videoaufnahme zu initiieren, indem Sie **[StartRecordToStorageFileAsync](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture#Windows_Media_Capture_MediaCapture_StartRecordToStorageFileAsync_Windows_Media_MediaProperties_MediaEncodingProfile_Windows_Storage_IStorageFile_)** aufrufen, **StorageFile** übergeben, das in die das aufgenommene Medium geschrieben wird, und das **MediaEncodingProfil**, das im vorherigen Code-Beispiel erstellt wurde. Nach einigen Sekunden Wartezeit wird die Aufnahme mit einem Anruf bei **[StopRecordAsync](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture#Windows_Media_Capture_MediaCapture_StopRecordAsync)** gestoppt.

[!code-cs[MultiRecordToFile](./code/SimpleCameraPreview_Win10/cs/MainPage.MultiRecord.xaml.cs#SnippetMultiRecordToFile)]

Wenn der Vorgang abgeschlossen ist, wurde eine Videodatei erstellt, die das von jeder Kamera aufgenommene Video als separaten Stream in der Datei enthält. Informationen zur Wiedergabe von Mediendateien mit mehreren Videospuren finden Sie unter [Medienelemente, Wiedergabelisten und Tracks](media-playback-with-mediasource.md).

## <a name="related-topics"></a>Verwandte Themen

* [Kamera](camera.md)
* [Allgemeine Foto-, Video- und Audioaufnahme mit MediaCapture](basic-photo-video-and-audio-capture-with-MediaCapture.md)
* [Verarbeiten von Medienframes mit „MediaFrameReader“](process-media-frames-with-mediaframereader.md)
* [Medienelemente, Wiedergabelisten und Titel](media-playback-with-mediasource.md)


 

 




