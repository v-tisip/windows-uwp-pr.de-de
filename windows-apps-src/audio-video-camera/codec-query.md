---
author: drewbatgit
ms.assetid: 0A360481-B649-4E90-9BC4-4449BA7445EF
description: "Führen Sie eine Abfrage nach Audio- und Video-Encodern und -Decodern durch, die auf einem Gerät installiert ist."
title: Abfrage nach installierten Codecs
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Codecs, Encoder, Decoder, Abfrage
ms.openlocfilehash: 1bde2c24db6faa843d9118f330867e7f66b22e7e
ms.sourcegitcommit: 64cfb79fd27b09d49df99e8c9c46792c884593a7
translationtype: HT
---
# <a name="query-for-installed-codecs"></a>Abfrage nach installierten Codecs
In diesem Artikel wird gezeigt, wie Sie eine Abfrage nach Audio- und Video-Encodern und -Decodern durchführen, die auf einem Gerät installiert sind. Der Artikel [Unterstützte Codecs](supported-codecs.md) listet die Codecs auf, die im Betriebssystem für jede Gerätefamilie enthalten sind. Auf einem einzelnen Gerät kann der Benutzer oder eine App zusätzliche Codecs installieren. Die [CodecQuery](https://docs.microsoft.com/en-us/uwp/api/windows.media.core.codecquery)-Klasse kann zum Auflisten der aktuellen Encoder und Decoder verwendet werden, die auf dem Gerät installiert sind, auf dem Ihre App ausgeführt wird.

Die **CodecQuery**-Klasse befindet sich im [windows.media.core](https://docs.microsoft.com/en-us/uwp/api/windows.media.core)-Namespace und stellt einen Konstruktor bereit, der keine Argumente annimmt.

[!code-cs[CodecQueryUsing](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetCodecQueryUsing)]

[!code-cs[NewCodecQuery](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetNewCodecQuery)]

Die [FindAllAsync](https://docs.microsoft.com/en-us/uwp/api/windows.media.core.codecquery#Windows_Media_Core_CodecQuery_FindAllAsync_Windows_Media_Core_CodecKind_Windows_Media_Core_CodecCategory_System_String_)-Methode der **CodecQuery**-Klasse gibt alle installierten Codecs zurück, die die angegebenen Parameter erfüllen. Diese Parameter enthalten einen Wert aus der [CodecKind](https://docs.microsoft.com/en-us/uwp/api/windows.media.core.codeckind)-Enumeration, die angibt, ob Audio- oder Video-Codecs zurückgegeben werden sollen, und einen [CodecCategory](https://docs.microsoft.com/en-us/uwp/api/windows.media.core.codeccategory)-Wert, der angibt, ob Audio- oder Video-Codecs zurückgegeben werden sollen.

Der letzte Parameter ist eine Zeichenfolge, die für einen Medienuntertyp steht, wie z.B. H264 Video- oder FLAC Audio, der von einem vom beliebigen Codec unterstützt werden muss, der von **FindAllAsync** zurückgegeben wird. Sie können null oder eine leere Zeichenfolge für diesen Parameter angeben, um Codecs für alle Medien-Untertypen zurückzugeben. Im folgenden Beispiel werden alle Video-Encoder aufgeführt, die auf dem aktuellen Gerät installiert sind.

[!code-cs[FindAllEncoders](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetFindAllEncoders)]

Wenn Sie einen Medien-Untertyp angeben, müssen Sie die Zeichenfolgendarstellung einer der Untertypen-GUIDs verwenden, die in [Audio-Untertyp-GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa372553(v=vs.85).aspx) oder [Video-Untertyp-GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa370819(v=vs.85).aspx) aufgeführt sind. Die [CodecSubtypes](https://docs.microsoft.com/en-us/uwp/api/windows.media.core.codecsubtypes)-Klasse stellt Eigenschaften für die meisten unterstützten Medien-Untertypen bereit, die die Zeichenfolgendarstellung der Untertyp-GUID zurückgeben. Sie können auch einen FOURCC-Code für den Medien-Untertyp-Parameter angeben. Weitere Informationen finden Sie unter [FOURCC-Codes](https://msdn.microsoft.com/library/windows/desktop/dd375802(v=vs.85).aspx). 

Im folgenden Beispiel wird der FOURCC-Code zur Abfrage nach Video-Decodern verwendet, die H.264 Video unterstützen. Ein Beispielszenario für diesen Vorgang ist das Überprüfen, ob ein Videoformat unterstützt wird, bevor Sie versuchen, eine Videodatei wiederzugeben.

[!code-cs[IsH264Supported](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetIsH264Supported)]

Das folgende Beispiel fragt nach Audio-Encodern, die den FLAC-Medien-Untertyp unterstützen. Dieses Beispiel erstellt dann ein AudioEncodinAudioEncodingProperties-Objekt und ein MediaEncodingProfile für den Medien-Untertyp. Dies könnte zum Aufzeichnen von Audio im angegebenen Format oder zum Transcodieren von Audio aus einem anderen Format verwendet werden. Weitere Informationen finden Sie unter [Allgemeine Foto-, Video- und Audioaufnahme mit MediaCapture](basic-photo-video-and-audio-capture-with-MediaCapture.md) und unter [Transkodieren von Mediendateien](transcode-media-files.md).

[!code-cs[IsFLACSupported](./code/TranscodeWin10/cs/MainPage.xaml.cs#SnippetIsFLACSupported)]

## <a name="related-topics"></a>Verwandte Themen

* [Unterstützte Codecs](supported-codecs.md)
* [Allgemeine Foto-, Video- und Audioaufnahme mit MediaCapture](basic-photo-video-and-audio-capture-with-MediaCapture.md)
* [Transkodieren von Mediendateien](transcode-media-files.md)
 

 




