---
author: drewbatgit
ms.assetid: A1A0D99A-DCBF-4A14-80B9-7106BEF045EC
description: "Mit den Windows.Media.Transcoding-APIs können Sie Videodateien von einem Format in ein anderes transkodieren."
title: Transkodieren von Mediendateien
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: bcf9532f65b9f0574942d1fb4dd23f5a63613ec9
ms.lasthandoff: 02/07/2017

---

# <a name="transcode-media-files"></a>Transkodieren von Mediendateien

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]


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

-   WAV
-   AAC-Audio (M4A)
-   MP3-Audio
-   Windows Media Audio (WMA)
-   AVI
-   MP4-Video (H.264-Video und AAC-Audio)
-   Windows Media Video (WMV)

Die ersten vier Profile in der Liste enthalten nur Audio. Die anderen drei Profile enthalten Video und Audio.

Der folgende Code erstellt ein Profil für MP4-Video:

[!code-cs[TranscodeMediaProfile](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetTranscodeMediaProfile)]

Die statische [**CreateMp4**](https://msdn.microsoft.com/library/windows/apps/hh701078)-Methode erstellt ein MP4-Codierungsprofil. Der Parameter für diese Methode gibt die Zielauflösung für das Video an. In diesem Fall bedeutet [**VideoEncodingQuality.hd720p**](https://msdn.microsoft.com/library/windows/apps/hh701290): 1280 x 720 Pixel mit 30 Bildern pro Sekunde. („720p“ steht für 720 progressive Scanlinien pro Frame.) Dieses Muster gilt auch für die anderen Methoden zum Erstellen vordefinierter Profile.

Alternativ können Sie mit der [**MediaEncodingProfile.CreateFromFileAsync**](https://msdn.microsoft.com/library/windows/apps/hh701047)-Methode ein Profil erstellen, das einer vorhandenen Mediendatei entspricht. Wenn Sie die genauen gewünschten Codierungseinstellungen kennen, können Sie auch ein neues [**MediaEncodingProfile**](https://msdn.microsoft.com/library/windows/apps/hh701026)-Objekt erstellen und die Profildetails ausfüllen.

## <a name="transcode-the-file"></a>Transcodieren der Datei

Erstellen Sie zum Transcodieren der Datei ein neues [**MediaTranscoder**](https://msdn.microsoft.com/library/windows/apps/br207080)-Objekt, und rufen Sie die [**MediaTranscoder.PrepareFileTranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700936)-Methode auf. Übergeben Sie die Quelldatei, die Zieldatei und das Codierungsprofil. Rufen Sie dann die [**TranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700946)-Methode für das [**PrepareTranscodeResult**](https://msdn.microsoft.com/library/windows/apps/hh700941)-Objekt auf, das mit dem asynchronen Transcodierungsvorgang zurückgegeben wurde.

[!code-cs[TranscodeTranscodeFile](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetTranscodeTranscodeFile)]

## <a name="respond-to-transcoding-progress"></a>Reaktion auf Transcodierungsfortschritt

Sie können Reaktionsereignisse registrieren, wenn sich der Fortschritt der asynchronen [**TranscodeAsync**](https://msdn.microsoft.com/library/windows/apps/hh700946)-Klasse ändert. Diese Ereignisse sind Teil des asynchronen Programmierungsframeworks für Apps für die universelle Windows-Plattform (UWP) und nicht für die Transcodierungs-API spezifisch.

[!code-cs[TranscodeCallbacks](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetTranscodeCallbacks)]

 

 





