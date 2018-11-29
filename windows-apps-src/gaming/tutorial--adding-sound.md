---
title: Hinzufügen von Sound
description: Entwickeln Sie eine einfache sound-Engine, die mit XAudio2-APIs können Wiedergabe Spiel Musik und Soundeffekte.
ms.assetid: aa05efe2-2baa-8b9f-7418-23f5b6cd2266
ms.date: 10/24/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Sound
ms.localizationpriority: medium
ms.openlocfilehash: 94044e3d10df15cb1cb256d86ced798395e6af6f
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7973915"
---
# <a name="add-sound"></a>Hinzufügen von Sound

In diesem Thema erstellen wir eine einfache sound-Engine, die Verwendung von [XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415813) APIs. Wenn Sie mit __XAudio2__vertraut sind, haben wir eine kurze Einführung unter [Audio-Konzepte](#audio-concepts)enthalten.

>[!Note]
>Wenn Sie den neuesten Code für dieses Beispiel noch nicht heruntergeladen haben, wechseln Sie zu [Direct3D-Spielbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX). Dieses Beispiel gehört zu einer großen Sammlung von UWP-Featurebeispielen. Anweisungen zum Herunterladen des Beispiels finden Sie unter [Abrufen der UWP-Beispiele von GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).

## <a name="objective"></a>Ziel

Fügen Sie das Beispielspiel mit [XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415813)mit Sounds.

## <a name="define-the-audio-engine"></a>Definieren Sie das Audiomodul

Im Beispielspiel sind die Audio-Objekte und -Verhalten in drei Dateien definiert:

* __["Audio.h"](#audioh)/.cpp__: definiert das __Audio__ -Objekt, das die __XAudio2__ -Ressourcen für die Soundwiedergabe enthält. Außerdem definiert sie die Methode zum Anhalten und Fortsetzen der Audiowiedergabe, wenn das Spiel angehalten oder deaktiviert wurde.
* __ [MediaReader.h](#mediareaderh)/.cpp__: definiert die Methoden zum Lesen von WAV-Audiodateien aus dem lokalen Speicher.
* __ [SoundEffect.h](#soundeffecth)/.cpp__: definiert ein Objekt für die Soundwiedergabe im Spiel.

## <a name="overview"></a>Übersicht

Es gibt drei wichtige Teile in die Vorbereitung für die Audiowiedergabe in Ihrem Spiel.

1. [Erstellen und Initialisieren der Audioressourcen](#create-and-initialize-the-audio-resources)
2. [Load-Audiodatei](#load-audio-file)
3. [Zuordnen von Sound-Objekt](#associate-sound-to-object)

Sie sind alle in der Methode [Simple3DGame::Initialize](#simple3dgameinitialize-method) definiert. Befassen wir uns also zuerst untersuchen Sie diese Methode und Beschäftigten Sie sich dann mit mehr Details in den Abschnitten.

Nach dem einrichten, erfahren wir die Soundeffekte zum Wiedergeben von auslösen. Weitere Informationen finden Sie unter [der Sound wiedergegeben](#play-the-sound).

### <a name="simple3dgameinitialize-method"></a>Simple3DGame::Initialize-Methode

In __Simple3DGame::Initialize__, wobei __M\_controller__ und __M\_renderer__ auch initialisiert wurden, müssen wir das Audiomodul eingerichtet und Vorbereitungen für die Soundwiedergabe.

 * Erstellen Sie __M\_audioController__, dabei handelt es sich um eine Instanz der [Audio](#audioh) -Klasse.
 * Erstellen Sie die Audioressourcen erforderlich, die mit der [Audio::CreateDeviceIndependentResources](#audiocreatedeviceindependentresources-method) -Methode. Hier, dass zwei __XAudio2__ -Objekte &mdash; eine Musik-Engine-Objekt und ein sound Modulobjekt und eine mastering Voice für jedes von ihnen erstellt wurden. Das Musik-Engine-Objekt kann zum Wiedergeben von Hintergrundmusik für Ihr Spiel verwendet werden. Das sound-Modul kann verwendet werden, um in Ihrem Spiel Soundeffekte. Weitere Informationen finden Sie unter [Erstellen und initialisieren die Audioressourcen](#create-and-initialize-the-audio-resources).
 * Erstellen Sie __MediaReader__, dabei handelt es sich um eine Instanz der [MediaReader](#mediareaderh) -Klasse. [MediaReader](#mediareaderh), die eine Hilfsklasse für die [SoundEffect](#soundeffecth) -Klasse ist, kleine Audiodateien synchron aus Speicherort liest und gibt die Sounddaten als Byte-Array zurück.
 * Verwenden Sie [Mediareader](#mediareaderloadmedia-method) , zum Laden von Audiodateien von seinem Standort und erstellen Sie eine Variable __TargetHitSound__ der geladenen WAV-sound Daten. Weitere Informationen finden Sie in der [Load-Audiodatei](#load-audio). 

Soundeffekte sind das spielobjekt zugeordnet. Wenn eine mit diesem Spiel Objekt Kollision löst also den Soundeffekt wiedergegeben werden soll. In diesem Beispielspiel haben wir Soundeffekte für die Munition (was wir verwenden, um Ziele anvisiert) und das Ziel. 
    
* In der __Render__ -Klasse besteht eine __HitSound__ -Eigenschaft, die verwendet wird, um den Soundeffekt auf das Objekt zu verknüpfen.
* Erstellen Sie eine neue Instanz der Klasse [SoundEffect](#soundeffecth) und initialisieren Sie es. Während der Initialisierung wird eine quellstimme für die Soundeffekt erstellt. 
* Diese Klasse spielt eine Audiodatei, die über eine mastering Voice von der " [Audio](#audioh) "-Klasse bereitgestellt werden. Sounddaten werden mithilfe der Klasse [MediaReader](#mediareaderh) Speicherort der Datei gelesen werden. Weitere Informationen finden Sie in der [Sound-Objekt zuzuordnen](#associate-sound-to-object).

>[!Note]
>Der tatsächliche Trigger wiedergegeben wird durch die Bewegung und Kollision dieser Objekte Spiel bestimmt. Der Aufruf tatsächlich diese Sounds wiedergegeben werden daher in der Methode [Simple3DGame::UpdateDynamics](#simple3dgameupdatedynamics-method) definiert. Weitere Informationen finden Sie unter [der Sound wiedergegeben](#play-the-sound).

```cpp
void Simple3DGame::Initialize(
    _In_ MoveLookController^ controller,
    _In_ GameRenderer^ renderer
    )
{
    // ...
    // Create a new Audio class object.
    m_audioController = ref new Audio;

    // Create the audio resources needed.
    // Two XAudio2 objects are created - one for music engine,
    // the other for sound engine. A mastering voice is also
    // created for each of the objects.
    m_audioController->CreateDeviceIndependentResources();

    m_ammo = std::vector<Sphere^>(GameConstants::MaxAmmo);

    // ..
    // Create a media reader which is used to read audio files from its file location.
    MediaReader^ mediaReader = ref new MediaReader;
    auto targetHitSound = mediaReader->LoadMedia("Assets\\hit.wav");

    // Instantiate the targets for use in the game.
    // Each target has a different initial position, size, and orientation.
    // But share a common set of material properties.
    for (int a = 1; a < GameConstants::MaxTargets; a++)
    {
        // ...
        // Create a new sound effect object and associate it
        // with the game object's (target) HitSound property.
        target->HitSound(ref new SoundEffect());

        // Initialize the sound effect object with
        // the sound effect engine, format of the audio wave, and audio data
        // During initialization, source voice of this sound effect is also created.
        target->HitSound()->Initialize(
            m_audioController->SoundEffectEngine(),
            mediaReader->GetOutputWaveFormatEx(),
            targetHitSound
            );
        // ...
    }

    // Instantiate a set of spheres to be used as ammunition for the game
    // and set the material properties of the spheres.
    auto ammoHitSound = mediaReader->LoadMedia("Assets\\bounce.wav");

    for (int a = 0; a < GameConstants::MaxAmmo; a++)
    {
        m_ammo[a] = ref new Sphere;
        m_ammo[a]->Radius(GameConstants::AmmoRadius);
        m_ammo[a]->HitSound(ref new SoundEffect());
        m_ammo[a]->HitSound()->Initialize(
            m_audioController->SoundEffectEngine(),
            mediaReader->GetOutputWaveFormatEx(),
            ammoHitSound
            );
        m_ammo[a]->Active(false);
        m_renderObjects.push_back(m_ammo[a]);
    }
    // ...
}
```

## <a name="create-and-initialize-the-audio-resources"></a>Erstellen und Initialisieren der Audioressourcen

* Verwenden Sie [XAudio2Create](https://msdn.microsoft.com/library/windows/desktop/ee419212), eine XAudio2-API, um zwei neue XAudio2-Objekte erstellt, die die Musik und Sound Effekt-Engines zu definieren. Diese Methode gibt einen Zeiger auf das Objekt [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908) -Schnittstelle, die alle Audiomodul Zustände, die audioverarbeitung Thread, der Stimme Graph und mehr verwaltet.
* Nachdem die Module instanziiert wurden, verwenden Sie [IXAudio2::CreateMasteringVoice](https://msdn.microsoft.com/library/windows/desktop/hh405048) , um eine mastering Voice für jedes der sound Modulobjekte erstellen.

Weitere Informationen finden Sie unter [So: Initialisieren von XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415779.aspx).

### <a name="audiocreatedeviceindependentresources-method"></a>Audio::CreateDeviceIndependentResources-Methode

```cpp

void Audio::CreateDeviceIndependentResources()
{
    UINT32 flags = 0;

    DX::ThrowIfFailed(
        XAudio2Create(&m_musicEngine, flags)
        );

    HRESULT hr = m_musicEngine->CreateMasteringVoice(&m_musicMasteringVoice);
    if (FAILED(hr))
    {
        // Unable to create an audio device
        m_audioAvailable = false;
        return;
    }

    DX::ThrowIfFailed(
        XAudio2Create(&m_soundEffectEngine, flags)
        );

    DX::ThrowIfFailed(
        m_soundEffectEngine->CreateMasteringVoice(&m_soundEffectMasteringVoice)
        );

    m_audioAvailable = true;
}
```

## <a name="load-audio-file"></a>Load-Audiodatei

Im Beispielspiel wird der Code zum Lesen von Audioformat Dateien in [MediaReader.h](#mediareaderh)/cpp__ definiert.  Rufen Sie zum Lesen einer codierten WAV-Audiodatei [Mediareader](#mediareaderloadmedia-method), und übergeben Sie den Dateinamen der die WAV-Datei als Eingabeparameter.

### <a name="mediareaderloadmedia-method"></a>Mediareader-Methode

Diese Methode verwendet die [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)-APIs, um die WAV-Audiodatei als Pulse Code Modulation (PCM)-Puffer einzulesen.

#### <a name="set-up-the-source-reader"></a>Einrichten der Source-Reader

1. Verwenden Sie [MFCreateSourceReaderFromURL](https://msdn.microsoft.com/library/windows/desktop/dd388110) , um ein Medium Quellenreader ([IMFSourceReader](https://msdn.microsoft.com/library/windows/desktop/dd374655)) erstellen.
2. Verwenden Sie [MFCreateMediaType](https://msdn.microsoft.com/library/windows/desktop/ms693861) zum Erstellen eines Media-Typ ([IMFMediaType](https://msdn.microsoft.com/library/windows/desktop/ms704850))-Objekts (_MediaType_). Es steht eine Beschreibung der Media-Format. 
3. Geben Sie, dass die _MediaType_decodierten Ausgabe PCM-Audio, die ein audio-Typ ist, den __XAudio2__ verwenden können.
4. Legt Medientyp decodierten Ausgabe für die Quelle Leser durch Aufrufen von [imfsourcereader:: Setcurrentmediatype](https://msdn.microsoft.com/library/windows/desktop/dd374667.aspx).

Weitere Informationen dazu, warum wir der Quellenreader verwendet werden finden Sie unter [Quellenreader](https://msdn.microsoft.com/library/windows/desktop/dd940436.aspx).

#### <a name="describe-the-data-format-of-the-audio-stream"></a>Das Format des Audiostreams zu beschreiben

1. Verwenden Sie [Getcurrentmediatype](https://msdn.microsoft.com/library/windows/desktop/dd374660) , um den aktuellen Medientyp für den Stream abzurufen.
2. Verwenden Sie [imfmediatype:: Mfcreatewaveformatexfrommfmediatype](https://msdn.microsoft.com/library/windows/desktop/ms702177) , um den aktuellen audio Medientyp werden einem Puffer [WAVEFORMATEX](https://msdn.microsoft.com/library/windows/hardware/ff538799) , verwenden die Ergebnisse des vorherigen Vorgangs als Eingabe zu konvertieren. Diese Struktur gibt das Format des Audiostreams wiegen, die nach dem Laden Audiodaten verwendet wird. 

Das __WAVEFORMATEX__ -Format kann verwendet werden, um den PCM-Puffer zu beschreiben. Im Vergleich zu der [WAVEFORMATEXTENSIBLE](https://msdn.microsoft.com/library/windows/hardware/ff538802) -Struktur kann er nur verwendet werden eine Teilmenge der audio wiegen Formate zu beschreiben. Weitere Informationen zu den Unterschieden zwischen __WAVEFORMATEX__ und __WAVEFORMATEXTENSIBLE__finden Sie in [Extensible wiegen-Format-Deskriptoren](https://docs.microsoft.com/windows-hardware/drivers/audio/extensible-wave-format-descriptors).

#### <a name="read-the-audio-stream"></a>Lesen Sie den Audiostream

1.  Rufen Sie die Dauer in Sekunden des Audiostreams zu durch Aufrufen von [Getpresentationattribute](https://msdn.microsoft.com/library/windows/desktop/dd374662) und dann konvertiert die Dauer in Bytes.
2.  Lesen Sie die Audiodatei als Datenstrom, durch den Aufruf [Readsample](https://msdn.microsoft.com/library/windows/desktop/dd374665). __ReadSample__ liest das nächste Beispiel aus der Medienquelle.
3.  Verwenden Sie [IMFSample::ConvertToContiguousBuffer](https://msdn.microsoft.com/library/windows/desktop/ms698917.aspx) zum Kopieren von Inhalt des audiosample-Puffers (_Beispiel_) in einem Array (_MediaBuffer_).

```cpp
Platform::Array<byte>^ MediaReader::LoadMedia(_In_ Platform::String^ filename)
{
    DX::ThrowIfFailed(
        MFStartup(MF_VERSION)
        );

    // Creates a media source reader.
    ComPtr<IMFSourceReader> reader;
    DX::ThrowIfFailed(
        MFCreateSourceReaderFromURL(
            Platform::String::Concat(m_installedLocationPath, filename)->Data(),
            nullptr,
            &reader
            )
        );

    // Set the decoded output format as PCM.
    // XAudio2 on Windows can process PCM and ADPCM-encoded buffers.
    // When using MediaFoundation, this sample always decodes into PCM.
    Microsoft::WRL::ComPtr<IMFMediaType> mediaType;
    DX::ThrowIfFailed(
        MFCreateMediaType(&mediaType)
        );

    // Define the major category of the media as audio. For more info about major media types,
    // go to: https://msdn.microsoft.com/library/windows/desktop/aa367377.aspx
    DX::ThrowIfFailed(
        mediaType->SetGUID(MF_MT_MAJOR_TYPE, MFMediaType_Audio)
        );

    // Define the sub-type of the media as uncompressed PCM audio. For more info about audio sub-types,
    // go to: https://msdn.microsoft.com/library/windows/desktop/aa372553.aspx
    DX::ThrowIfFailed(
        mediaType->SetGUID(MF_MT_SUBTYPE, MFAudioFormat_PCM)
        );
    
    // Sets the media type for a stream. This media type defines that format that the Source Reader 
    // produces as output. It can differ from the native format provided by the media source.
    // For more info, go to https://msdn.microsoft.com/library/windows/desktop/dd374667.aspx
    DX::ThrowIfFailed(
        reader->SetCurrentMediaType(static_cast<uint32>(MF_SOURCE_READER_FIRST_AUDIO_STREAM), 0, mediaType.Get())
        );

    // Get the current media type for the stream.
    // For more info, go to:
    // https://msdn.microsoft.com/library/windows/desktop/dd374660.aspx
        Microsoft::WRL::ComPtr<IMFMediaType> outputMediaType;
    DX::ThrowIfFailed(
        reader->GetCurrentMediaType(static_cast<uint32>(MF_SOURCE_READER_FIRST_AUDIO_STREAM), &outputMediaType)
        );

    // Converts the current media type into the WaveFormatEx buffer structure.
    UINT32 size = 0;
    WAVEFORMATEX* waveFormat;
    DX::ThrowIfFailed(
        MFCreateWaveFormatExFromMFMediaType(outputMediaType.Get(), &waveFormat, &size)
        );

    // Copies the waveFormat's block of memory to the starting address of the m_waveFormat variable in MediaReader.
    // Then free the waveFormat memory block.
    // For more info, go to https://msdn.microsoft.com/library/windows/desktop/aa366535.aspx and
    // https://msdn.microsoft.com/library/windows/desktop/ms680722.aspx
    CopyMemory(&m_waveFormat, waveFormat, sizeof(m_waveFormat));
    CoTaskMemFree(waveFormat);

    PROPVARIANT propVariant;
    DX::ThrowIfFailed(
        reader->GetPresentationAttribute(static_cast<uint32>(MF_SOURCE_READER_MEDIASOURCE), MF_PD_DURATION, &propVariant)
        );

    // 'duration' is in 100ns units; convert to seconds, and round up
    // to the nearest whole byte.
    LONGLONG duration = propVariant.uhVal.QuadPart;
    unsigned int maxStreamLengthInBytes =
        static_cast<unsigned int>(
            ((duration * static_cast<ULONGLONG>(m_waveFormat.nAvgBytesPerSec)) + 10000000) /
            10000000
            );

    Platform::Array<byte>^ fileData = ref new Platform::Array<byte>(maxStreamLengthInBytes);

    ComPtr<IMFSample> sample;
    ComPtr<IMFMediaBuffer> mediaBuffer;
    DWORD flags = 0;

    int positionInData = 0;
    bool done = false;
    while (!done)
    {
        //...
        // Read audio data.
    }

    return fileData;
}
```
## <a name="associate-sound-to-object"></a>Zuordnen von Sound-Objekt

Zuordnen von Sounds für das Objekt findet statt, wenn das Spiel in der [Simple3DGame::Initialize](#simple3dgameinitialize-method) -Methode initialisiert.

Zusammenfassung:
* In der __Render__ -Klasse besteht eine __HitSound__ -Eigenschaft, die verwendet wird, um den Soundeffekt auf das Objekt zu verknüpfen.
* Erstellen Sie eine neue Instanz des Klassenobjekts [SoundEffect](#soundeffecth) , und ordnen Sie sie der Spielobjekte. Diese Klasse spielt eine Audiodatei, die Verwendung von __XAudio2__ APIs.  Es verwendet eine mastering Voice durch die " [Audio](#audioh) "-Klasse bereitgestellt. Die Sounddaten können aus den Speicherort der Datei mit der Klasse [MediaReader](#mediareaderh) gelesen werden.

[SoundEffect:: Initialize](#soundeffectinitialize-method) dient zum Initialisieren der __SoundEffect__ -Instanz mit den folgenden Eingabeparameter: Zeiger auf sound Modulobjekt (IXAudio2-Objekte in der [Audio::CreateDeviceIndependentResources](#audiocreatedeviceindependentresources-method) -Methode erstellt) Zeiger zum Formatieren der WAV-Datei mit __mediareader:: Getoutputwaveformatex__und die Sounddaten mithilfe [mediareader:: Loadmedia](#mediareaderloadmedia-method) -Methode geladen. Während der Initialisierung wird auch die quellstimme für die Soundeffekt erstellt.

### <a name="soundeffectinitialize-method"></a>SoundEffect:: Initialize-Methode

```cpp
void SoundEffect::Initialize(
    _In_ IXAudio2 *masteringEngine,
    _In_ WAVEFORMATEX *sourceFormat,
    _In_ Platform::Array<byte>^ soundData)
{
    m_soundData = soundData;

    if (masteringEngine == nullptr)
    {
        // Audio is not available so just return.
        m_audioAvailable = false;
        return;
    }

    // Create a source voice for this sound effect.
    DX::ThrowIfFailed(
        masteringEngine->CreateSourceVoice(
            &m_sourceVoice,
            sourceFormat
            )
        );
    m_audioAvailable = true;
}
```

## <a name="play-the-sound"></a>Den Sound

Trigger Soundeffekte sind in [Simple3DGame::UpdateDynamics](#simple3dgameupdatedynamics-method) Methode definiert, da es sich handelt, in denen Bewegung der Objekte werden aktualisiert und Kollisionen zwischen Objekten wird bestimmt.

Da die Interaktion zwischen Objekten erheblich, je nachdem, das Spiel unterscheidet sich werden nicht wir die Dynamik der hier die Spielobjekte zu erläutern. Wenn Sie ihre Implementierung verstehen interessiert sind, wechseln Sie zu [Simple3DGame::UpdateDynamics](#simple3dgameupdatedynamics-method) -Methode.

Im Prinzip Wenn eine Kollision auftritt, löst den Soundeffekt zum Wiedergeben von durch Aufrufen von [SoundEffect::PlaySound]((soundeffectplaysound-method). Diese Methode werden keine Soundeffekte, die gerade wiedergegeben und den Puffer im Arbeitsspeicher mit der gewünschten Sounddaten in die Warteschlange beendet. Quellstimme verwendet, um das Volume festlegen, übermitteln Sounddaten und starten Sie die Wiedergabe.

### <a name="soundeffectplaysound-method"></a>SoundEffect::-Methode

* Source Voice-Objekt **M\_sourceVoice** verwendet, um die Wiedergabe von die Sounddaten Puffer **M\_soundData** zu starten
* Erstellt eine [XAUDIO2\_BUFFER](https://msdn.microsoft.com/library/windows/desktop/ee419228), zu dem sie einen Verweis auf den sounddatenpuffer bereitstellt, und übermittelt ihn dann mit einem Aufruf von [IXAudio2SourceVoice::SubmitSourceBuffer](https://msdn.microsoft.com/library/windows/desktop/ee418473). 
* Wenn die Sounddaten in die Warteschlange eingereiht sind, startet **SoundEffect::PlaySound** die Wiedergabe durch einen Aufruf von [IXAudio2SourceVoice::Start](https://msdn.microsoft.com/library/windows/desktop/ee418471).

```cpp
void SoundEffect::PlaySound(_In_ float volume)
{
    XAUDIO2_BUFFER buffer = {0};
    XAUDIO2_VOICE_STATE state = {0};

    if (!m_audioAvailable)
    {
        // Audio is not available, so just return.
        return;
    }

    // Interrupt sound effect if currently playing.
    DX::ThrowIfFailed(
        m_sourceVoice->Stop()
        );
    DX::ThrowIfFailed(
        m_sourceVoice->FlushSourceBuffers()
        );

    // Queue in-memory buffer for playback and start the voice.
    buffer.AudioBytes = m_soundData->Length;
    buffer.pAudioData = m_soundData->Data;
    buffer.Flags = XAUDIO2_END_OF_STREAM;

    m_sourceVoice->SetVolume(volume);
    DX::ThrowIfFailed(
        m_sourceVoice->SubmitSourceBuffer(&buffer)
        );
    DX::ThrowIfFailed(
        m_sourceVoice->Start()
        );
}
```

### <a name="simple3dgameupdatedynamics-method"></a>Simple3DGame::UpdateDynamics-Methode

Die Methode __Simple3DGame::UpdateDynamics__ kümmert sich um die Interaktion und den Konflikt zwischen Spielobjekte. Wenn Objekte kollidieren (oder schneiden), löst den zugehörigen Soundeffekt wiedergegeben wird.

```cpp
void Simple3DGame::UpdateDynamics()
{
    // ...
    // Check for collisions between ammo.
#pragma region inter-ammo collision detection
    if (m_ammoCount > 1)
    {
       // ...
       // Check collision between instances One and Two.
       // ...
       if (distanceSquared < (GameConstants::AmmoSize * GameConstants::AmmoSize))
       {
           // The two ammo are intersecting.
           // ...
           // Start playing the sounds for the impact between the two balls.
              m_ammo[one]->PlaySound(impact, m_player->Position());
              m_ammo[two]->PlaySound(impact, m_player->Position());

       }
    }
#pragma endregion

#pragma region Ammo-Object intersections
    // Check for intersections between the ammo and the other objects in the scene.
    // ...
    // Ball is in contact with Object.
    // ...

    // Make sure that the ball is actually headed towards the object. At grazing angles there
    // could appear to be an impact when the ball is actually already hit and moving away.
    if (impact > 0.0f)
    {
        // ...
        // Play the sound associated with the Ammo hitting something.
           m_ammo[one]->PlaySound(impact, m_player->Position());

        if (m_objects[i]->Target() && !m_objects[i]->Hit())
        {
            // The object is a target and isn't currently hit, so mark it as hit and
            // play the sound associated with the impact.
             m_objects[i]->Hit(true);
             m_objects[i]->HitTime(timeTotal);
             m_totalHits++;

             m_objects[i]->PlaySound(impact, m_player->Position());
        }
        // ...
    }
#pragma endregion

#pragma region Apply Gravity and world intersection
    // Apply gravity and check for collision against enclosing volume.
    // ...
    if (position.z < limit)
    {
        // The ammo instance hit the a wall in the min Z direction.
        // Align the ammo instance to the wall, invert the Z component of the velocity and
        // play the impact sound.
           position.z = limit;
           m_ammo[i]->PlaySound(-velocity.z, m_player->Position());
           velocity.z = -velocity.z * GameConstants::Physics::GroundRestitution;
    }
    // ...
#pragma endregion
}
```
## <a name="next-steps"></a>Nächste Schritte

Wir haben das UWP Framework, Grafiken, Steuerelemente, Benutzeroberfläche und Audio eines Windows 10-Spiels behandelt. Der nächste Teil des Lernprogramms [Erweitern des beispielspiels](tutorial-resources.md)wird erläutert, andere Optionen, die bei der Entwicklung eines Spiels verwendet werden können.

## <a name="audio-concepts"></a>Audio-Konzepte

Verwenden Sie für die Entwicklung für Windows 10-Spiele XAudio2-Version 2.9. Diese Version wird mit Windows 10 geliefert. Weitere Informationen finden Sie unter [XAudio2-Versionen](https://msdn.microsoft.com/library/windows/desktop/ee415802.aspx).

__AudioX2__ ist eine Low-Level-API, die signalverarbeitung und -abmischung bereitstellt. Weitere Informationen finden Sie unter [XAudio2 Schlüssel Konzepte](https://msdn.microsoft.com/library/windows/desktop/ee415764.aspx).

### <a name="xaudio2-voices"></a>XAudio2-stimmen

Es gibt drei Arten von XAudio2 Voice Objekte: quellstimme, submixstimme und masterstimme. Stimmen sind, dass die XAudio2-Objekte verarbeitet, bearbeiten und zum Wiedergeben von Audiodaten verwenden. 
* Quellstimmen verarbeiten die vom Client bereitgestellten Audiodaten. 
* Quell- und Submixstimmen senden ihre Ausgabe an mindestens eine Submix- oder Masterstimme. 
* Submix- und Masterstimmen mischen die Audiodaten aller Stimmen, von denen sie Daten erhalten, und verarbeiten das Ergebnis. 
* Masterstimmen empfangen von Daten aus quellstimmen und submixstimmen und sendet Daten an die Audiohardware.

Weitere Informationen finden Sie unter [XAudio2-stimmen](https://msdn.microsoft.com/library/windows/desktop/ee415824.aspx).

### <a name="audio-graph"></a>Audiodiagramm

Audiodiagramm ist eine Sammlung von [XAudio2-stimmen](#xaudio2-voice-objects). Audio auf einer Seite des ein audiodiagramm in quellstimmen beginnt, durchläuft optional ein oder mehrere submixstimmen und endet mit eine mastering Voice. Ein audiodiagramm enthält eine quellstimme für jeden Sound aktuell wiedergegebenen, NULL oder mehr submixstimmen und eine masterstimme. Das einfachste audiodiagramm und die Mindestanzahl der benötigten ein Geräusch in XAudio2 ist eine einzelne quellstimme direkt an eine mastering Voice ausgeben. Weitere Informationen finden Sie unter [audiodiagramme](https://msdn.microsoft.com/library/windows/desktop/ee415739.aspx).

### <a name="additional-reading"></a>Zusätzliche lesen

* [So wird's gemacht: Initialisieren von XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415779.aspx)
* [So wird's gemacht: Laden von Datendateien in XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415781(v=vs.85).aspx)
* [So wird's gemacht: Wiedergeben von Ton mit XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415787.aspx)

## <a name="key-audio-h-files"></a>Wichtige audio h-Dateien

### <a name="audioh"></a>Audio.h

```cpp
// Audio:
// This class uses XAudio2 to provide sound output.  It creates two
// engines - one for music and the other for sound effects - each as
// a separate mastering voice.
// The SuspendAudio and ResumeAudio methods can be used to stop
// and start all audio playback.
public:
    Audio();

    void Initialize();
    void CreateDeviceIndependentResources();
    IXAudio2* MusicEngine();
    IXAudio2* SoundEffectEngine();
    void SuspendAudio();
    void ResumeAudio();

protected:
    // ...
};
```
### <a name="mediareaderh"></a>MediaReader.h

```cpp
// MediaReader:
// This is a helper class for the SoundEffect class.  It reads small audio files
// synchronously from the package installed folder and returns sound data as a
// byte array.

ref class MediaReader
{
internal:
    MediaReader();

    Platform::Array<byte>^          LoadMedia(_In_ Platform::String^ filename);
    WAVEFORMATEX*                   GetOutputWaveFormatEx();

protected private:
    Windows::Storage::StorageFolder^ m_installedLocation;
    Platform::String^               m_installedLocationPath;
    WAVEFORMATEX                    m_waveFormat;
};
```
### <a name="soundeffecth"></a>SoundEffect.h

```cpp
// SoundEffect:
// This class plays a sound using XAudio2.  It uses a mastering voice provided
// from the Audio class.  The sound data can be read from disk using the MediaReader
// class.

ref class SoundEffect
{
internal:
    SoundEffect();

    void Initialize(
        _In_ IXAudio2*              masteringEngine,
        _In_ WAVEFORMATEX*          sourceFormat,
        _In_ Platform::Array<byte>^ soundData
        );

    void PlaySound(_In_ float volume);

protected private:
    //...

};
```


