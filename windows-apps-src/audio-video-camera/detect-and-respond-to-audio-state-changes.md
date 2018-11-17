---
author: drewbatgit
ms.assetid: EE0C1B28-EF9C-4BD9-A3C0-BDF11E75C752
description: In diesem Artikel wird erläutert, wie UWP-Apps vom System initiierte Änderungen der Audiodatenstromebene erkennen und darauf reagieren können
title: Erkennen und reagieren auf Änderungen der Audiodatenstromebene
ms.author: drewbat
ms.date: 04/03/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f7b4addf2a7bdc2d93cbcf64f13a640a4ef5b12a
ms.sourcegitcommit: 9f8010fe67bb3372db1840de9f0be36097ed6258
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7104242"
---
# <a name="detect-and-respond-to-audio-state-changes"></a>Erkennen und reagieren auf Änderungen der Audiodatenstromebene
Ab Windows10, Version 1803, erkennt Ihre App, wenn das System die Lautstärke der Audioaufnahme Ihrer App oder des Audiodatenstroms reduziert oder stummschaltet. Sie können Benachrichtigungen für die Erfassung und die Wiedergabe von Datenströmen erhalten, für ein bestimmtes Audio-Gerät und eine Audiokategorie oder für eine [**MediaPlayer**](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Playback.MediaPlayer)-Objekt, das ist Ihrer App für die Medienwiedergabe verwendet. Beispielsweise kann das System die Audiowiedergabe-Ebene reduzieren, wenn ein Alarm klingelt. Das System schaltet Ihre App stumm, wenn sie in den Hintergrund wechselt, falls Ihre App die *BackgroundMediaPlayback*-Funktion im App-Manifest nicht aktiviert hat. 

Das Muster für die Behandlung von Audio-Zustandsänderungen ist für alle unterstützten Audiostreams identisch. Erstellen Sie zuerst eine Instanz der [**AudioStateMonitor**](https://docs.microsoft.com/uwp/api/windows.media.audio.audiostatemonitor)-Klasse. Im folgenden Beispiel verwendet die App die [**MediaCapture**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCapture)-Klasse zum Aufnehmen von Audio für Spiele-Chats. Es wird eine Factorymethode aufgerufen, um den Audiostatus-Monitor für den Spiel-Chat-Auidioaufnahmedatenstrom des standardmäßigen Kommunikationsgeräts zugeordnet zu erhalten.  Danach wird ein Handler für das [**SoundLevelChanged**](https://docs.microsoft.com/uwp/api/windows.media.audio.audiostatemonitor.soundlevelchanged)-Ereignis registriert, das ausgelöst wird, wenn die Audiowiedergabe für die entsprechende Streamkategorie vom System geändert wird.

[!code-cs[DeviceIdCategoryVars](./code/SimpleCameraPreview_Win10/cs/MainPage.xaml.cs#SnippetDeviceIdCategoryVars)]

[!code-cs[SoundLevelDeviceIdCategory](./code/SimpleCameraPreview_Win10/cs/MainPage.xaml.cs#SnippetSoundLevelDeviceIdCategory)]

Überprüfen Sie im Ereignishandler **SoundLevelChanged** [**SoundLevel**](https://docs.microsoft.com/uwp/api/windows.media.audio.audiostatemonitor.soundlevel) -Eigenschaft des an den Handler übergebenen **AudioStateMonitor** Absenders zu ermitteln, welche die neue Soundebene für den Stream. In diesem Beispiel wird die Aufzeichnung von Audio von der App beendet, wenn die Lautstärke stumm geschaltet ist, und fortgesetzt, wenn die volle Lautstärke wieder eingeschaltet wird.

[!code-cs[GameChatSoundLevelChanged](./code/SimpleCameraPreview_Win10/cs/MainPage.xaml.cs#SnippetGameChatSoundLevelChanged)]

Weitere Informationen über die Aufnahme von Audio mit **MediaCapture** finden Sie unter [Allgemeine Foto-, Video- und Audioaufnahme mit MediaCapture](basic-photo-video-and-audio-capture-with-MediaCapture.md).

Jede Instanz der [**MediaPlayer**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Playback.MediaPlayer)-Klasse verfügt über einen zugeordneten **AudioStateMonitor**, den Sie verwenden können, um festzustellen, ob das System die Lautstärke des aktuell wiedergegebenen Inhalts ändert. Sie können auch entscheiden, Audio-Zustandsänderungen unterschiedlich zu behandeln, je nach Art der wiedergegeben Inhalte. Möglicherweise möchten Sie z.B. die Wiedergabe eines Podcasts anhalten, wenn die Audiowiedergabe leiser ist, und die Wiedergabe fortsetzen, wenn der Inhalt Musik ist. 

[!code-cs[AudioStateVars](./code/MediaPlayer_RS1/cs/MainPage.xaml.cs#SnippetAudioStateVars)]

[!code-cs[SoundLevelChanged](./code/MediaPlayer_RS1/cs/MainPage.xaml.cs#SnippetSoundLevelChanged)]

Weitere Informationen zur Verwendung des **MediaPlayer** finden Sie unter [Wiedergeben von Audio- und Videoinhalten mit MediaPlayer](play-audio-and-video-with-mediaplayer.md). 

## <a name="related-topics"></a>Verwandte Themen