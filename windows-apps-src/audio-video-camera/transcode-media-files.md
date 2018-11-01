---
author: drewbatgit
ms.assetid: A1A0D99A-DCBF-4A14-80B9-7106BEF045EC
description: Mit den Windows.Media.Transcoding-APIs können Sie Videodateien von einem Format in ein anderes transcodieren.
title: Transkodieren von Mediendateien
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: babf91e681004942bb3b66eb43622742fa183125
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5869421"
---
# <a name="transcode-media-files"></a>Transkodieren von Mediendateien



Mit den [**Windows.Media.Transcoding**](https://msdn.microsoft.com/library/windows/apps/br207105)-APIs können Sie Videodateien in ein anderes Format transcodieren.

Beim *Transcodieren* wird eine digitale Mediendatei (etwa eine Video- oder Audiodatei) in ein anderes Format konvertiert. Dies geschieht in der Regel durch Decodieren und erneutes Codieren der Datei. Beispiel: Sie konvertieren eine Windows Media-Datei in MP4, um sie auf einem Gerät wiederzugeben, das das MP4-Format unterstützt. Oder Sie können eine Videodatei mit hoher Auflösung in eine niedrigere Auflösung konvertieren. In diesem Fall kann die neu codierte Datei den gleichen Codec wie die Originaldatei verwenden, sie besitzt jedoch ein anderes Codierungsprofil.

## <a name="set-up-your-project-for-transcoding"></a>Einrichten des Projekts für die Transcodierung

Zusätzlich zu den Namespaces, auf die von der Standardprojektvorlage verwiesen wird, müssen Sie auf die folgenden Namespaces verweisen, um Mediendateien mit dem Code in diesem Artikel transcodieren zu können:

[!code-cs[Using](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetUsing)]

## <a name="select-source-and-destination-files"></a>Auswählen der Quell- und Zieldateien

Die Art, wie Ihre App die Quell- und Zieldateien für die Transcodierung ermittelt, hängt von der Implementierung ab. In diesem Beispiel werden eine [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847)-Klasse und eine [**FileSavePicker**](https://msdn.microsoft.com/library/windows/apps/br207871)-Klasse verwendet, um Benutzern die Auswahl einer Quell- und Zieldatei zu ermöglichen.

[!code-cs[TranscodeGetFile](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetTranscodeGetFile)]

## <a name="create-a-media-encoding-profile"></a>Erstellen eines Mediencodierungsprofils

Das Codierungsprofil enthält die Einstellungen, die die Codierungsart der Zieldatei festlegen. Hier stehen die meisten Optionen zum Transcodieren einer Datei zur Verfügung.

Die [**MediaEncodingProfile**](https://msdn.microsoft.com/library/windows/apps/hh701026)-Klasse stellt statische Methoden zum Erstellen vordefinierter Codierungsprofile bereit:

### <a name="methods-for-creating-audio-only-encoding-profiles"></a>Methoden zum Erstellen von Codierungsprofilen, die nur Audio enthalten

Methode  |Profil  |
---------|---------|
[**CreateAlac**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createalac)     |Apple Lossless Audio Codec (ALAC)-Audio         |
[**CreateFlac**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createflac)     |Free Lossless Audio Codec (FLAC)-Audio.         |
[**CreateM4a**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createm4a)     |AAC-Audio (M4A)         |
[**CreateMp3**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createmp3)     |MP3-Audio         |
[**CreateWav**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createwav)     |WAV-Audio         |
[**CreateWmv**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createwmv)     |Windows Media Audio (WMA)         |

### <a name="methods-for-creating-audio--video-encoding-profiles"></a>Methoden zum Erstellen von Audio-/Videocodierungsprofilen

Methode  |Profil  |
---------|---------|
[**CreateAvi**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createavi) |AVI |
[**CreateHevc**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createhevc) |High Efficiency Video Coding (HEVC)-Video, auch als H.265-Video bezeichnet |
[**CreateMp4**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createmp4) |MP4-Video (H.264-Video und AAC-Audio) |
[**CreateWmv**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createwmv) |Windows Media Video (WMV) |


Der folgende Code erstellt ein Profil für MP4-Video:

[!code-cs[TranscodeMediaProfile](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetTranscodeMediaProfile)]

Die statische [**CreateMp4**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createmp4)-Methode erstellt ein MP4-Codierungsprofil. Der Parameter für diese Methode gibt die Zielauflösung für das Video an. In diesem Fall bedeutet [**VideoEncodingQuality.hd720p**](https://msdn.microsoft.com/library/windows/apps/hh701290): 1280x720Pixel mit 30Bildern pro Sekunde. („720p“ steht für 720progressive Scanlinien pro Frame.) Dieses Muster gilt auch für die anderen Methoden zum Erstellen vordefinierter Profile.

Alternativ können Sie mit der [**MediaEncodingProfile.CreateFromFileAsync**](https://msdn.microsoft.com/library/windows/apps/hh701047)-Methode ein Profil erstellen, das einer vorhandenen Mediendatei entspricht. Wenn Sie die genauen gewünschten Codierungseinstellungen kennen, können Sie auch ein neues [**MediaEncodingProfile**](https://msdn.microsoft.com/library/windows/apps/hh701026)-Objekt erstellen und die Profildetails ausfüllen.

## <a name="transcode-the-file"></a>Transcodieren der Datei

Erstellen Sie zum Transcodieren der Datei ein neues [**MediaTranscoder**](https://msdn.microsoft.com/library/windows/apps/br207080)-Objekt, und rufen Sie die [**MediaTranscoder.PrepareFileTranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700936)-Methode auf. Übergeben Sie die Quelldatei, die Zieldatei und das Codierungsprofil. Rufen Sie dann die [**TranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700946)-Methode für das [**PrepareTranscodeResult**](https://msdn.microsoft.com/library/windows/apps/hh700941)-Objekt auf, das mit dem asynchronen Transcodierungsvorgang zurückgegeben wurde.

[!code-cs[TranscodeTranscodeFile](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetTranscodeTranscodeFile)]

## <a name="respond-to-transcoding-progress"></a>Reaktion auf Transcodierungsfortschritt

Sie können Reaktionsereignisse registrieren, wenn sich der Fortschritt der asynchronen [**TranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700946)-Klasse ändert. Diese Ereignisse sind Teil des asynchronen Programmierungsframeworks für Apps für die universelle Windows-Plattform (UWP) und nicht für die Transcodierungs-API spezifisch.

[!code-cs[TranscodeCallbacks](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetTranscodeCallbacks)]


## <a name="encode-a-metadata-stream"></a>Codieren Sie einen Metadatenstrom
Ab Windows 10, Version 1803, können Sie zeitgesteuerten Metadaten einschließen beim Transcodieren von Mediendateien. Im Gegensatz zu den oben genannten video transcodieren Beispielen müssen verwenden den integrierten Media-Codierung Erstellungsmethoden Profil, z. B. [**MediaEncodingProfile.CreateMp4**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.mediaencodingprofile.createmp4), Sie manuell erstellen das Codierungsprofil Metadaten zur Unterstützung von des Typs der Metadaten, die Sie codieren .

Dieser erste Schritt beim Erstellen eines Profils Metadaten Incoding ist die Erstellung ein Objekts [**TimedMetadataEncodingProperties**], das beschreibt die Codierung der Metadaten, die transcodiert werden soll. Die Untertyp-Eigenschaft ist eine GUID, die den Typ der Metadaten angibt. Die Codierung Details für jeden Metadatentyp ist proprietäre und wird nicht von Windows bereitgestellt. In diesem Beispiel wird die GUID für GoPro-Metadaten (Gprs) verwendet. Als Nächstes wird [**SetFormatUserData**](https://docs.microsoft.com/uwp/api/windows.media.mediaproperties.timedmetadataencodingproperties.setformatuserdata) aufgerufen, um das Festlegen eines binären BLOBs von Daten, die den Stream-Format, die speziell für das Metadatenformat beschreiben. Anschließend wird ein **TimedMetadataStreamDescriptor**(https://docs.microsoft.com/uwp/api/windows.media.core.timedmetadatastreamdescriptor) aus der codieren Eigenschaften erstellt und einen Titel Bezeichnung und einen Namen zu ermöglichen einer Anwendung Lesen des Streams Endcoded, um den Metadatenstream identifizieren und optional der Name des Streams in der Benutzeroberfläche angezeigt werden. 
 
[!code-cs[GetStreamDescriptor](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetGetStreamDescriptor)]

Nach dem Erstellen der **TimedMetadataStreamDescriptor**, können Sie ein **MediaEncodingProfile** erstellen, die das Video, Audio und Metadaten in der Datei codiert werden beschreibt. Die **TimedMetadataStreamDescriptor** im letzten Beispiel erstellt wird in diesem Beispiel Helper-Funktion übergeben und ist die **MediaEncodingProfile** durch Aufrufen von [**SetTimedMetadataTracks**](https://docs.microsoft.com/en-us/uwp/api/windows.media.mediaproperties.mediaencodingprofile.settimedmetadatatracks)hinzugefügt.

[!code-cs[GetMediaEncodingProfile](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetGetMediaEncodingProfile)]
 

 




