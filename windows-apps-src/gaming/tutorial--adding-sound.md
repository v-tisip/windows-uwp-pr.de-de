---
author: mtoepke
title: Hinzufügen von Sound
description: In diesem Schritt untersuchen wir, wie das Beispiel-Shooterspiel mit den XAudio2-APIs ein Objekt für die Soundwiedergabe erstellt.
ms.assetid: aa05efe2-2baa-8b9f-7418-23f5b6cd2266
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Sound
ms.openlocfilehash: 11553a22274a36094a3e839e8fda648f78cfaaf8
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "233792"
---
# <a name="add-sound"></a><span data-ttu-id="50da4-104">Hinzufügen von Sound</span><span class="sxs-lookup"><span data-stu-id="50da4-104">Add sound</span></span>


<span data-ttu-id="50da4-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="50da4-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="50da4-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="50da4-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="50da4-107">In diesem Schritt untersuchen wir, wie das Beispielshooterspiel mit den [XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415813)-APIs ein Objekt für die Soundwiedergabe erstellt.</span><span class="sxs-lookup"><span data-stu-id="50da4-107">In this step, we examine how the shooting game sample creates an object for sound playback using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415813) APIs.</span></span>

## <a name="objective"></a><span data-ttu-id="50da4-108">Ziel</span><span class="sxs-lookup"><span data-stu-id="50da4-108">Objective</span></span>


-   <span data-ttu-id="50da4-109">So fügen Sie mit [XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415813) eine Soundausgabe hinzu.</span><span class="sxs-lookup"><span data-stu-id="50da4-109">To add sound output using [XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415813).</span></span>

<span data-ttu-id="50da4-110">Im Beispielspiel sind die Audio-Objekte und -Verhalten in drei Dateien definiert:</span><span class="sxs-lookup"><span data-stu-id="50da4-110">In the game sample, the audio objects and behaviors are defined in three files:</span></span>

-   <span data-ttu-id="50da4-111">**Audio.h/.cpp**.</span><span class="sxs-lookup"><span data-stu-id="50da4-111">**Audio.h/.cpp**.</span></span> <span data-ttu-id="50da4-112">Diese Codedatei definiert das **Audio**-Objekt, das die XAudio2-Ressourcen für die Soundwiedergabe enthält.</span><span class="sxs-lookup"><span data-stu-id="50da4-112">This code file defines the **Audio** object, which contains the XAudio2 resources for sound playback.</span></span> <span data-ttu-id="50da4-113">Außerdem definiert sie die Methode zum Anhalten und Fortsetzen der Audiowiedergabe, wenn das Spiel angehalten oder deaktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="50da4-113">It also defines the method for suspending and resuming audio playback if the game is paused or deactivated.</span></span>
-   <span data-ttu-id="50da4-114">**MediaReader.h/.cpp**.</span><span class="sxs-lookup"><span data-stu-id="50da4-114">**MediaReader.h/.cpp**.</span></span> <span data-ttu-id="50da4-115">Dieser Code definiert die Methoden zum Lesen von WAV-Audiodateien aus einem lokalen Speicher.</span><span class="sxs-lookup"><span data-stu-id="50da4-115">This code defines the methods for reading audio .wav files from local storage.</span></span>
-   <span data-ttu-id="50da4-116">**SoundEffect.h/.cpp**.</span><span class="sxs-lookup"><span data-stu-id="50da4-116">**SoundEffect.h/.cpp**.</span></span> <span data-ttu-id="50da4-117">Dieser Code definiert ein Objekt für die Soundwiedergabe im Spiel.</span><span class="sxs-lookup"><span data-stu-id="50da4-117">This code defines an object for in-game sound playback.</span></span>

## <a name="defining-the-audio-engine"></a><span data-ttu-id="50da4-118">Definieren des Audiomoduls</span><span class="sxs-lookup"><span data-stu-id="50da4-118">Defining the audio engine</span></span>


<span data-ttu-id="50da4-119">Wenn das Beispielspiel gestartet wird, erstellt es ein **Audio**-Objekt, das die Audioressourcen für das Spiel zuordnet.</span><span class="sxs-lookup"><span data-stu-id="50da4-119">When the game sample starts, it creates an **Audio** object that allocates the audio resources for the game.</span></span> <span data-ttu-id="50da4-120">Der Code zum Deklarieren dieses Objekts sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="50da4-120">The code that declares this object looks like this:</span></span>

```cpp
public:
    Audio();

    void Initialize();
    void CreateDeviceIndependentResources();
    IXAudio2* MusicEngine();
    IXAudio2* SoundEffectEngine();
    void SuspendAudio();
    void ResumeAudio();

protected:
    bool                                m_audioAvailable;
    Microsoft::WRL::ComPtr<IXAudio2>    m_musicEngine;
    Microsoft::WRL::ComPtr<IXAudio2>    m_soundEffectEngine;
    IXAudio2MasteringVoice*             m_musicMasteringVoice;
    IXAudio2MasteringVoice*             m_soundEffectMasteringVoice;
};
```

<span data-ttu-id="50da4-121">Die Methoden **Audio::MusicEngine** und **Audio::SoundEffectEngine** geben Verweise auf [**IXAudio2**](https://msdn.microsoft.com/library/windows/desktop/ee415908)-Objekte zurück, die die Mastering Voice für jeden Audiotyp festlegen.</span><span class="sxs-lookup"><span data-stu-id="50da4-121">The **Audio::MusicEngine** and **Audio::SoundEffectEngine** methods return references to [**IXAudio2**](https://msdn.microsoft.com/library/windows/desktop/ee415908) objects that define the mastering voice for each audio type.</span></span> <span data-ttu-id="50da4-122">Eine Mastering Voice ist das für die Wiedergabe verwendete Audiogerät.</span><span class="sxs-lookup"><span data-stu-id="50da4-122">A mastering voice is the audio device used for playback.</span></span> <span data-ttu-id="50da4-123">Sounddatenpuffer können nicht direkt an Mastering Voices übermittelt werden, an andere Voice-Typen übermittelte Daten müssen aber an eine Mastering Voice umgeleitet werden, damit sie gehört werden können.</span><span class="sxs-lookup"><span data-stu-id="50da4-123">Sound data buffers cannot be submitted directly to mastering voices, but data submitted to other types of voices must be directed to a mastering voice to be heard.</span></span>

## <a name="initializing-the-audio-resources"></a><span data-ttu-id="50da4-124">Initialisieren der Audioressourcen</span><span class="sxs-lookup"><span data-stu-id="50da4-124">Initializing the audio resources</span></span>


<span data-ttu-id="50da4-125">Im Beispiel werden die [**IXAudio2**](https://msdn.microsoft.com/library/windows/desktop/ee415908)-Objekte für die Musik- und Soundeffektmodule mit [**XAudio2Create**](https://msdn.microsoft.com/library/windows/desktop/ee419212)-Aufrufen initialisiert.</span><span class="sxs-lookup"><span data-stu-id="50da4-125">The sample initializes the [**IXAudio2**](https://msdn.microsoft.com/library/windows/desktop/ee415908) objects for the music and sound effect engines with calls to [**XAudio2Create**](https://msdn.microsoft.com/library/windows/desktop/ee419212).</span></span> <span data-ttu-id="50da4-126">Nachdem die Module instanziiert wurden, wird wie hier gezeigt mit [**IXAudio2::CreateMasteringVoice**](https://msdn.microsoft.com/library/windows/desktop/hh405048)-Aufrufen eine Mastering Voice für jedes Modul erstellt:</span><span class="sxs-lookup"><span data-stu-id="50da4-126">After the engines have been instantiated, it creates a mastering voice for each with calls to [**IXAudio2::CreateMasteringVoice**](https://msdn.microsoft.com/library/windows/desktop/hh405048), as here:</span></span>

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

<span data-ttu-id="50da4-127">Wenn eine Musik- oder Soundeffekt-Audiodatei geladen wird, ruft diese Methode [**IXAudio2::CreateSourceVoice**](https://msdn.microsoft.com/library/windows/desktop/ee418607) für die Mastering Voice auf, die eine Instanz der Source Voice für die Wiedergabe erstellt.</span><span class="sxs-lookup"><span data-stu-id="50da4-127">As a music or sound effect audio file is loaded, this method calls [**IXAudio2::CreateSourceVoice**](https://msdn.microsoft.com/library/windows/desktop/ee418607) on the mastering voice, which creates an instance of a source voice for playback.</span></span> <span data-ttu-id="50da4-128">Diesen Code werden wir uns ansehen, nachdem wir uns damit befasst haben, wie das Spiel Audiodateien lädt.</span><span class="sxs-lookup"><span data-stu-id="50da4-128">We look at the code for this as soon as we finish reviewing how the game sample loads audio files.</span></span>

## <a name="reading-an-audio-file"></a><span data-ttu-id="50da4-129">Lesen einer Audiodatei</span><span class="sxs-lookup"><span data-stu-id="50da4-129">Reading an audio file</span></span>


<span data-ttu-id="50da4-130">Im Beispielspiel ist der Code zum Lesen von Dateien im Audioformat in **MediaReader.cpp** definiert.</span><span class="sxs-lookup"><span data-stu-id="50da4-130">In the game sample, the code for reading audio format files is defined in **MediaReader.cpp**.</span></span> <span data-ttu-id="50da4-131">Die spezifische Methode zum Lesen einer codierten WAV-Audiodatei (**MediaReader::LoadMedia**) sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="50da4-131">The specific method that reads in an encoded .wav audio file, **MediaReader::LoadMedia**, looks like this:</span></span>

```cpp
Platform::Array<byte>^  MediaReader::LoadMedia(_In_ Platform::String^ filename)
{
    DX::ThrowIfFailed(
        MFStartup(MF_VERSION)
        );

    ComPtr<IMFSourceReader> reader;
    DX::ThrowIfFailed(
        MFCreateSourceReaderFromURL(
            Platform::String::Concat(m_installedLocationPath, filename)->Data(),
            nullptr,
            &reader
            )
        );

    // Set the decoded output format as PCM
    // XAudio2 on Windows can process PCM and ADPCM-encoded buffers.
    // When using MediaFoundation, this sample always decodes into PCM.
    Microsoft::WRL::ComPtr<IMFMediaType> mediaType;
    DX::ThrowIfFailed(
        MFCreateMediaType(&mediaType)
        );

    DX::ThrowIfFailed(
        mediaType->SetGUID(MF_MT_MAJOR_TYPE, MFMediaType_Audio)
        );

    DX::ThrowIfFailed(
        mediaType->SetGUID(MF_MT_SUBTYPE, MFAudioFormat_PCM)
        );

    DX::ThrowIfFailed(
        reader->SetCurrentMediaType(MF_SOURCE_READER_FIRST_AUDIO_STREAM, 0, mediaType.Get())
        );

    // Get the complete WAVEFORMAT from the Media Type.
    Microsoft::WRL::ComPtr<IMFMediaType> outputMediaType;
    DX::ThrowIfFailed(
        reader->GetCurrentMediaType(MF_SOURCE_READER_FIRST_AUDIO_STREAM, &outputMediaType)
        );

    UINT32 size = 0;
    WAVEFORMATEX* waveFormat;
    DX::ThrowIfFailed(
        MFCreateWaveFormatExFromMFMediaType(outputMediaType.Get(), &waveFormat, &size)
        );

    CopyMemory(&m_waveFormat, waveFormat, sizeof(m_waveFormat));
    CoTaskMemFree(waveFormat);

    // Get the total length of the stream in bytes.
    PROPVARIANT propVariant;
    DX::ThrowIfFailed(
        reader->GetPresentationAttribute(MF_SOURCE_READER_MEDIASOURCE, MF_PD_DURATION, &propVariant)
        );
    LONGLONG duration = propVariant.uhVal.QuadPart;
    unsigned int maxStreamLengthInBytes;

    double durationInSeconds = (duration / static_cast<double>(10000 * 1000));
    maxStreamLengthInBytes = static_cast<unsigned int>(durationInSeconds * m_waveFormat.nAvgBytesPerSec);

    // Make the length a multiple of 4 bytes.
    maxStreamLengthInBytes = (maxStreamLengthInBytes + 3) / 4 * 4;

    Platform::Array<byte>^ fileData = ref new Platform::Array<byte>(maxStreamLengthInBytes);

    ComPtr<IMFSample> sample;
    ComPtr<IMFMediaBuffer> mediaBuffer;
    DWORD flags = 0;

    int positionInData = 0;
    bool done = false;
    while (!done)
    {
        DX::ThrowIfFailed(
            reader->ReadSample(MF_SOURCE_READER_FIRST_AUDIO_STREAM, 0, nullptr, &flags, nullptr, &sample)
            );

        if (sample != nullptr)
        {
            DX::ThrowIfFailed(
                sample->ConvertToContiguousBuffer(&mediaBuffer)
                );

            BYTE *audioData = nullptr;
            DWORD sampleBufferLength = 0;
            DX::ThrowIfFailed(
                mediaBuffer->Lock(&audioData, nullptr, &sampleBufferLength)
                );

            for (DWORD i = 0; i < sampleBufferLength; i++)
            {
                fileData[positionInData++] = audioData[i];
            }
        }
        if (flags & MF_SOURCE_READERF_ENDOFSTREAM)
        {
            done = true;
        }
    }

    // Fix up the array size on match the actual length.
    Platform::Array<byte>^ realfileData = ref new Platform::Array<byte>((positionInData + 3) / 4 * 4);
    memcpy(realfileData->Data, fileData->Data, positionInData);
    return realfileData;
}
```

<span data-ttu-id="50da4-132">Diese Methode verwendet die [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)-APIs, um die WAV-Audiodatei als Pulse Code Modulation (PCM)-Puffer einzulesen.</span><span class="sxs-lookup"><span data-stu-id="50da4-132">This method uses the [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) APIs to read in the .wav audio file as a Pulse Code Modulation (PCM) buffer.</span></span>

1.  <span data-ttu-id="50da4-133">Sie erstellt einen Medienquellenleser ([**IMFSourceReader**](https://msdn.microsoft.com/library/windows/desktop/dd374655)), indem sie [**MFCreateSourceReaderFromURL**](https://msdn.microsoft.com/library/windows/desktop/dd388110) aufruft.</span><span class="sxs-lookup"><span data-stu-id="50da4-133">Creates a media source reader ([**IMFSourceReader**](https://msdn.microsoft.com/library/windows/desktop/dd374655)) object by calling [**MFCreateSourceReaderFromURL**](https://msdn.microsoft.com/library/windows/desktop/dd388110).</span></span>
2.  <span data-ttu-id="50da4-134">Sie erstellt einen Medientyp ([**IMFMediaType**](https://msdn.microsoft.com/library/windows/desktop/ms704850)) für die Decodierung der Audiodatei, indem sie [**MFCreateMediaType**](https://msdn.microsoft.com/library/windows/desktop/ms693861) aufruft.</span><span class="sxs-lookup"><span data-stu-id="50da4-134">Creates a media type ([**IMFMediaType**](https://msdn.microsoft.com/library/windows/desktop/ms704850)) for the decoding of the audio file by calling [**MFCreateMediaType**](https://msdn.microsoft.com/library/windows/desktop/ms693861).</span></span> <span data-ttu-id="50da4-135">Diese Methode legt fest, dass es sich bei der decodierten Ausgabe um PCM-Audio handelt – ein von XAudio2 unterstützter Audiotyp.</span><span class="sxs-lookup"><span data-stu-id="50da4-135">This method specifies that the decoded output is PCM audio, which is an audio type that XAudio2 can use.</span></span>
3.  <span data-ttu-id="50da4-136">Sie legt den decodierten Ausgabemedientyp für den Leser fest, indem sie [**IMFSourceReader::SetCurrentMediaType**](https://msdn.microsoft.com/library/windows/desktop/bb970432) aufruft.</span><span class="sxs-lookup"><span data-stu-id="50da4-136">Sets the decoded output media type for the reader by calling [**IMFSourceReader::SetCurrentMediaType**](https://msdn.microsoft.com/library/windows/desktop/bb970432).</span></span>
4.  <span data-ttu-id="50da4-137">Sie erstellt einen [**WAVEFORMATEX**](https://msdn.microsoft.com/library/windows/hardware/ff538799)-Puffer und kopiert die Ergebnisse eines [**IMFMediaType::MFCreateWaveFormatExFromMFMediaType**](https://msdn.microsoft.com/library/windows/desktop/ms702177)-Aufrufs für das [**IMFMediaType**](https://msdn.microsoft.com/library/windows/desktop/ms704850)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="50da4-137">Creates a [**WAVEFORMATEX**](https://msdn.microsoft.com/library/windows/hardware/ff538799) buffer and copies the results of a call to [**IMFMediaType::MFCreateWaveFormatExFromMFMediaType**](https://msdn.microsoft.com/library/windows/desktop/ms702177) on the [**IMFMediaType**](https://msdn.microsoft.com/library/windows/desktop/ms704850) object.</span></span> <span data-ttu-id="50da4-138">Dadurch wird der Puffer formatiert, der die Audiodatei nach dem Laden enthält.</span><span class="sxs-lookup"><span data-stu-id="50da4-138">This formats the buffer that holds the audio file after it is loaded.</span></span>
5.  <span data-ttu-id="50da4-139">Sie ruft die Dauer (in Sekunden) des Audiodatenstroms ab, indem sie [**IMFSourceReader::GetPresentationAttribute**](https://msdn.microsoft.com/library/windows/desktop/dd374662) aufruft, und konvertiert die Dauer dann in Bytes.</span><span class="sxs-lookup"><span data-stu-id="50da4-139">Gets the duration, in seconds, of the audio stream by calling [**IMFSourceReader::GetPresentationAttribute**](https://msdn.microsoft.com/library/windows/desktop/dd374662) and then converts the duration to bytes.</span></span>
6.  <span data-ttu-id="50da4-140">Sie liest die Audiodatei als Datenstrom, indem sie [**IMFSourceReader::ReadSample**](https://msdn.microsoft.com/library/windows/desktop/dd374665) aufruft.</span><span class="sxs-lookup"><span data-stu-id="50da4-140">Reads the audio file in as a stream by calling [**IMFSourceReader::ReadSample**](https://msdn.microsoft.com/library/windows/desktop/dd374665).</span></span>
7.  <span data-ttu-id="50da4-141">Sie kopiert den Inhalt des Audiosample-Puffers in ein von der Methode zurückgegebenes Array.</span><span class="sxs-lookup"><span data-stu-id="50da4-141">Copies the contents of the audio sample buffer into an array returned by the method.</span></span>

<span data-ttu-id="50da4-142">Das Wichtigste bei **SoundEffect::Initialize** ist die Erstellung des SourceVoice-Objekts (**m\_sourceVoice**) auf der Grundlage der Mastering Voice.</span><span class="sxs-lookup"><span data-stu-id="50da4-142">The most important thing in **SoundEffect::Initialize** is the creation of the source voice object, **m\_sourceVoice**, from the mastering voice.</span></span> <span data-ttu-id="50da4-143">Die Source Voice wird für die eigentliche Wiedergabe des von **MediaReader::LoadMedia** abgerufenen Sounddatenpuffers verwendet.</span><span class="sxs-lookup"><span data-stu-id="50da4-143">We use the source voice for the actual play back of the sound data buffer obtained from **MediaReader::LoadMedia**.</span></span>

<span data-ttu-id="50da4-144">Im Beispielspiel wird die Methode beim Initialisieren des **SoundEffect**-Objekts wie folgt aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="50da4-144">The sample game calls this method when it initializes the **SoundEffect** object, like this:</span></span>

```cpp
void SoundEffect::Initialize(
    _In_ IXAudio2 *masteringEngine,
    _In_ WAVEFORMATEX *sourceFormat,
    _In_ Platform::Array<byte>^ soundData)
{
    m_soundData = soundData;

    if (masteringEngine == nullptr)
    {
        // Audio is not available, so return.
        m_audioAvailable = false;
        return;
    }

    // Create and reuse a single source voice for the single sound effect in this sample.
    DX::ThrowIfFailed(
        masteringEngine->CreateSourceVoice(
            &m_sourceVoice,
            sourceFormat
            )
        );
    m_audioAvailable = true;
}
```

<span data-ttu-id="50da4-145">Wie Sie sehen, werden an diese Methode die Ergebnisse der Aufrufe von **Audio::SoundEffectEngine** (oder **Audio::MusicEngine**), **MediaReader::GetOutputWaveFormatEx** und der von einem **MediaReader::LoadMedia**-Aufruf zurückgegebene Puffer übergeben.</span><span class="sxs-lookup"><span data-stu-id="50da4-145">This method is passed the results of calls to **Audio::SoundEffectEngine** (or **Audio::MusicEngine**), **MediaReader::GetOutputWaveFormatEx**, and the buffer returned by a call to **MediaReader::LoadMedia**, as seen here.</span></span>

```cpp
MediaReader^ mediaReader = ref new MediaReader;
auto targetHitSound = mediaReader->LoadMedia("hit.wav");
```

```cpp
myTarget->HitSound(ref new SoundEffect());
myTarget->HitSound()->Initialize(
                m_audioController->SoundEffectEngine(),
                mediaReader->GetOutputWaveFormatEx(),
                targetHitSound);
```

<span data-ttu-id="50da4-146">**SoundEffect::Initialize** wird von der **Simple3DGame:Initialize**-Methode aufgerufen, die das Hauptspielobjekt initialisiert.</span><span class="sxs-lookup"><span data-stu-id="50da4-146">**SoundEffect::Initialize** is called from the **Simple3DGame:Initialize** method that initializes the main game object.</span></span>

<span data-ttu-id="50da4-147">Nachdem der Speicher des Beispielspiels nun eine Audiodatei enthält, können wir uns ansehen, wie die Datei während des Spiels wiedergegeben wird.</span><span class="sxs-lookup"><span data-stu-id="50da4-147">Now that the sample game has an audio file in memory, let's see how it plays it back during game play!</span></span>

## <a name="playing-back-an-audio-file"></a><span data-ttu-id="50da4-148">Wiedergeben einer Audiodatei</span><span class="sxs-lookup"><span data-stu-id="50da4-148">Playing back an audio file</span></span>


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

<span data-ttu-id="50da4-149">Für die Soundwiedergabe verwendet diese Methode das SourceVoice-Objekt **m\_sourceVoice**, um die Wiedergabe des Sounddatenpuffers **m\_soundData** zu starten.</span><span class="sxs-lookup"><span data-stu-id="50da4-149">To play the sound, this method uses the source voice object **m\_sourceVoice** to start the playback of the sound data buffer **m\_soundData**.</span></span> <span data-ttu-id="50da4-150">Sie erstellt einen [**XAUDIO2\_BUFFER**](https://msdn.microsoft.com/library/windows/desktop/ee419228), für den sie einen Verweis auf den Sounddatenpuffer bereitstellt, und übermittelt ihn dann mit einem Aufruf von [**IXAudio2SourceVoice::SubmitSourceBuffer**](https://msdn.microsoft.com/library/windows/desktop/ee418473).</span><span class="sxs-lookup"><span data-stu-id="50da4-150">It creates an [**XAUDIO2\_BUFFER**](https://msdn.microsoft.com/library/windows/desktop/ee419228), to which it provides a reference to the sound data buffer, and then submits it with a call to [**IXAudio2SourceVoice::SubmitSourceBuffer**](https://msdn.microsoft.com/library/windows/desktop/ee418473).</span></span> <span data-ttu-id="50da4-151">Wenn die Sounddaten in die Warteschlange eingereiht sind, startet **SoundEffect::PlaySound** die Wiedergabe durch einen Aufruf von [**IXAudio2SourceVoice::Start**](https://msdn.microsoft.com/library/windows/desktop/ee418471).</span><span class="sxs-lookup"><span data-stu-id="50da4-151">With the sound data queued up, **SoundEffect::PlaySound** starts play back by calling [**IXAudio2SourceVoice::Start**](https://msdn.microsoft.com/library/windows/desktop/ee418471).</span></span>

<span data-ttu-id="50da4-152">Wenn die Munition jetzt ein Ziel trifft, wird durch einen Aufruf von **SoundEffect::PlaySound** ein Geräusch wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="50da4-152">Now, whenever a collision between the ammo and a target occurs, a call to **SoundEffect::PlaySound** causes a noise to play.</span></span>

## <a name="next-steps"></a><span data-ttu-id="50da4-153">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="50da4-153">Next steps</span></span>


<span data-ttu-id="50da4-154">Das war eine Blitzeinführung in die Entwicklung von DirectX-Spielen für die universelle Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="50da4-154">That was a whirlwind tour of Universal Windows Platform (UWP) DirectX game development!</span></span> <span data-ttu-id="50da4-155">Sie sollten nun wissen, was Sie tun müssen, um selbst ein großartiges Spiel für Windows8 zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="50da4-155">At this point, you have an idea of what you need to do to make your own game for Windows 8 a great experience.</span></span> <span data-ttu-id="50da4-156">Denken Sie daran, dass Ihr Spiel auf vielen unterschiedlichen Windows8-Geräten und -Plattformen gespielt werden kann. Entwerfen Sie daher alle Komponenten – Grafik, Steuerelemente, Benutzeroberfläche und Sound – für so viele Konfigurationen wie möglich.</span><span class="sxs-lookup"><span data-stu-id="50da4-156">Remember, your game can be played on a wide variety of Windows 8 devices and platforms, so design your components: your graphics, your controls, your user interface, and your audio for as wide a set of configurations as you can!</span></span>

<span data-ttu-id="50da4-157">Weitere Informationen zum Ändern des Beispielspiels in diesen Dokumenten finden Sie unter [Erweitern des Beispielspiels](tutorial-resources.md).</span><span class="sxs-lookup"><span data-stu-id="50da4-157">For more info about ways to modify the game sample provided in these documents, see [Extending the game sample](tutorial-resources.md).</span></span>

## <a name="complete-sample-code-for-this-section"></a><span data-ttu-id="50da4-158">Vollständiger Beispielcode für diesen Abschnitt</span><span class="sxs-lookup"><span data-stu-id="50da4-158">Complete sample code for this section</span></span>


<span data-ttu-id="50da4-159">Audio.h</span><span class="sxs-lookup"><span data-stu-id="50da4-159">Audio.h</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

ref class Audio
{
public:
    Audio();

    void Initialize();
    void CreateDeviceIndependentResources();
    IXAudio2* MusicEngine();
    IXAudio2* SoundEffectEngine();
    void SuspendAudio();
    void ResumeAudio();

protected:
    bool                                m_audioAvailable;
    Microsoft::WRL::ComPtr<IXAudio2>    m_musicEngine;
    Microsoft::WRL::ComPtr<IXAudio2>    m_soundEffectEngine;
    IXAudio2MasteringVoice*             m_musicMasteringVoice;
    IXAudio2MasteringVoice*             m_soundEffectMasteringVoice;
};
```

<span data-ttu-id="50da4-160">Audio.cpp</span><span class="sxs-lookup"><span data-stu-id="50da4-160">Audio.cpp</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#include "pch.h"
#include "Audio.h"
#include "DirectXSample.h"

using namespace Microsoft::WRL;
using namespace Windows::Foundation;
using namespace Windows::UI::Core;
using namespace Windows::Graphics::Display;

Audio::Audio():
    m_audioAvailable(false)
{
}

void Audio::Initialize()
{
}

void Audio::CreateDeviceIndependentResources()
{
    UINT32 flags = 0;

    DX::ThrowIfFailed(
        XAudio2Create(&m_musicEngine, flags)
        );

#if defined(_DEBUG)
    XAUDIO2_DEBUG_CONFIGURATION debugConfiguration = {0};
    debugConfiguration.BreakMask = XAUDIO2_LOG_ERRORS;
    debugConfiguration.TraceMask = XAUDIO2_LOG_ERRORS;
    m_musicEngine->SetDebugConfiguration(&debugConfiguration);
#endif


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

#if defined(_DEBUG)
    m_soundEffectEngine->SetDebugConfiguration(&debugConfiguration);
#endif

    DX::ThrowIfFailed(
        m_soundEffectEngine->CreateMasteringVoice(&m_soundEffectMasteringVoice)
        );

    m_audioAvailable = true;
}

IXAudio2* Audio::MusicEngine()
{
    return m_musicEngine.Get();
}

IXAudio2* Audio::SoundEffectEngine()
{
    return m_soundEffectEngine.Get();
}

void Audio::SuspendAudio()
{
    if (m_audioAvailable)
    {
        m_musicEngine->StopEngine();
        m_soundEffectEngine->StopEngine();
    }
}

void Audio::ResumeAudio()
{
    if (m_audioAvailable)
    {
        DX::ThrowIfFailed(m_musicEngine->StartEngine());
        DX::ThrowIfFailed(m_soundEffectEngine->StartEngine());
    }
}
```

<span data-ttu-id="50da4-161">SoundEffect.h</span><span class="sxs-lookup"><span data-stu-id="50da4-161">SoundEffect.h</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

ref class SoundEffect
{
public:
    SoundEffect();

    void Initialize(
        _In_ IXAudio2*              masteringEngine,
        _In_ WAVEFORMATEX*          sourceFormat,
        _In_ Platform::Array<byte>^ soundData
        );

    void PlaySound(_In_ float volume);

protected:
    bool                    m_audioAvailable;
    IXAudio2SourceVoice*    m_sourceVoice;
    Platform::Array<byte>^  m_soundData;
};
```

<span data-ttu-id="50da4-162">SoundEffect.cpp</span><span class="sxs-lookup"><span data-stu-id="50da4-162">SoundEffect.cpp</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#include "pch.h"
#include "SoundEffect.h"
#include "DirectXSample.h"

SoundEffect::SoundEffect():
    m_audioAvailable(false)
{
}
//----------------------------------------------------------------------
void SoundEffect::Initialize(
    _In_ IXAudio2 *masteringEngine,
    _In_ WAVEFORMATEX *sourceFormat,
    _In_ Platform::Array<byte>^ soundData)
{
    m_soundData = soundData;

    if (masteringEngine == nullptr)
    {
        // Audio is not available, so return.
        m_audioAvailable = false;
        return;
    }

    // Create and reuse a single source voice for the single sound effect in this sample.
    DX::ThrowIfFailed(
        masteringEngine->CreateSourceVoice(
            &m_sourceVoice,
            sourceFormat
            )
        );
    m_audioAvailable = true;
}
//----------------------------------------------------------------------
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

 

 




