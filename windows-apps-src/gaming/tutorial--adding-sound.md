---
title: Hinzufügen von Sound
description: Entwickeln Sie eine einfache sound-Engine, die mit XAudio2-APIs können Wiedergabe Spiel Musik und Soundeffekte.
ms.assetid: aa05efe2-2baa-8b9f-7418-23f5b6cd2266
ms.date: 10/24/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Sound
ms.localizationpriority: medium
ms.openlocfilehash: 94044e3d10df15cb1cb256d86ced798395e6af6f
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7848972"
---
# <a name="add-sound"></a><span data-ttu-id="61a67-104">Hinzufügen von Sound</span><span class="sxs-lookup"><span data-stu-id="61a67-104">Add sound</span></span>

<span data-ttu-id="61a67-105">In diesem Thema erstellen wir eine einfache sound-Engine, die Verwendung von [XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415813) APIs.</span><span class="sxs-lookup"><span data-stu-id="61a67-105">In this topic, we create a simple sound engine using [XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415813) APIs.</span></span> <span data-ttu-id="61a67-106">Wenn Sie mit __XAudio2__vertraut sind, haben wir eine kurze Einführung unter [Audio-Konzepte](#audio-concepts)enthalten.</span><span class="sxs-lookup"><span data-stu-id="61a67-106">If you are new to __XAudio2__, we have included a short intro under [Audio concepts](#audio-concepts).</span></span>

>[!Note]
><span data-ttu-id="61a67-107">Wenn Sie den neuesten Code für dieses Beispiel noch nicht heruntergeladen haben, wechseln Sie zu [Direct3D-Spielbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span><span class="sxs-lookup"><span data-stu-id="61a67-107">If you haven't downloaded the latest game code for this sample, go to [Direct3D game sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span></span> <span data-ttu-id="61a67-108">Dieses Beispiel gehört zu einer großen Sammlung von UWP-Featurebeispielen.</span><span class="sxs-lookup"><span data-stu-id="61a67-108">This sample is part of a large collection of UWP feature samples.</span></span> <span data-ttu-id="61a67-109">Anweisungen zum Herunterladen des Beispiels finden Sie unter [Abrufen der UWP-Beispiele von GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span><span class="sxs-lookup"><span data-stu-id="61a67-109">For instructions on how to download the sample, see [Get the UWP samples from GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span></span>

## <a name="objective"></a><span data-ttu-id="61a67-110">Ziel</span><span class="sxs-lookup"><span data-stu-id="61a67-110">Objective</span></span>

<span data-ttu-id="61a67-111">Fügen Sie das Beispielspiel mit [XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415813)mit Sounds.</span><span class="sxs-lookup"><span data-stu-id="61a67-111">Add sounds into the sample game using [XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415813).</span></span>

## <a name="define-the-audio-engine"></a><span data-ttu-id="61a67-112">Definieren Sie das Audiomodul</span><span class="sxs-lookup"><span data-stu-id="61a67-112">Define the audio engine</span></span>

<span data-ttu-id="61a67-113">Im Beispielspiel sind die Audio-Objekte und -Verhalten in drei Dateien definiert:</span><span class="sxs-lookup"><span data-stu-id="61a67-113">In the game sample, the audio objects and behaviors are defined in three files:</span></span>

* <span data-ttu-id="61a67-114">__["Audio.h"](#audioh)/.cpp__: definiert das __Audio__ -Objekt, das die __XAudio2__ -Ressourcen für die Soundwiedergabe enthält.</span><span class="sxs-lookup"><span data-stu-id="61a67-114">__[Audio.h](#audioh)/.cpp__: Defines the __Audio__ object, which contains the __XAudio2__ resources for sound playback.</span></span> <span data-ttu-id="61a67-115">Außerdem definiert sie die Methode zum Anhalten und Fortsetzen der Audiowiedergabe, wenn das Spiel angehalten oder deaktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="61a67-115">It also defines the method for suspending and resuming audio playback if the game is paused or deactivated.</span></span>
* <span data-ttu-id="61a67-116">__ [MediaReader.h](#mediareaderh)/.cpp__: definiert die Methoden zum Lesen von WAV-Audiodateien aus dem lokalen Speicher.</span><span class="sxs-lookup"><span data-stu-id="61a67-116">__[MediaReader.h](#mediareaderh)/.cpp__: Defines the methods for reading audio .wav files from local storage.</span></span>
* <span data-ttu-id="61a67-117">__ [SoundEffect.h](#soundeffecth)/.cpp__: definiert ein Objekt für die Soundwiedergabe im Spiel.</span><span class="sxs-lookup"><span data-stu-id="61a67-117">__[SoundEffect.h](#soundeffecth)/.cpp__: Defines an object for in-game sound playback.</span></span>

## <a name="overview"></a><span data-ttu-id="61a67-118">Übersicht</span><span class="sxs-lookup"><span data-stu-id="61a67-118">Overview</span></span>

<span data-ttu-id="61a67-119">Es gibt drei wichtige Teile in die Vorbereitung für die Audiowiedergabe in Ihrem Spiel.</span><span class="sxs-lookup"><span data-stu-id="61a67-119">There are three main parts in getting set up for audio playback into your game.</span></span>

1. [<span data-ttu-id="61a67-120">Erstellen und Initialisieren der Audioressourcen</span><span class="sxs-lookup"><span data-stu-id="61a67-120">Create and initialize the audio resources</span></span>](#create-and-initialize-the-audio-resources)
2. [<span data-ttu-id="61a67-121">Load-Audiodatei</span><span class="sxs-lookup"><span data-stu-id="61a67-121">Load audio file</span></span>](#load-audio-file)
3. [<span data-ttu-id="61a67-122">Zuordnen von Sound-Objekt</span><span class="sxs-lookup"><span data-stu-id="61a67-122">Associate sound to object</span></span>](#associate-sound-to-object)

<span data-ttu-id="61a67-123">Sie sind alle in der Methode [Simple3DGame::Initialize](#simple3dgameinitialize-method) definiert.</span><span class="sxs-lookup"><span data-stu-id="61a67-123">They are all defined in the [Simple3DGame::Initialize](#simple3dgameinitialize-method) method.</span></span> <span data-ttu-id="61a67-124">Befassen wir uns also zuerst untersuchen Sie diese Methode und Beschäftigten Sie sich dann mit mehr Details in den Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="61a67-124">So let's first examine this method and then dive into more details in each of the sections.</span></span>

<span data-ttu-id="61a67-125">Nach dem einrichten, erfahren wir die Soundeffekte zum Wiedergeben von auslösen.</span><span class="sxs-lookup"><span data-stu-id="61a67-125">After setting up, we learn how to trigger the sound effects to play.</span></span> <span data-ttu-id="61a67-126">Weitere Informationen finden Sie unter [der Sound wiedergegeben](#play-the-sound).</span><span class="sxs-lookup"><span data-stu-id="61a67-126">For more info, go to [Play the sound](#play-the-sound).</span></span>

### <a name="simple3dgameinitialize-method"></a><span data-ttu-id="61a67-127">Simple3DGame::Initialize-Methode</span><span class="sxs-lookup"><span data-stu-id="61a67-127">Simple3DGame::Initialize method</span></span>

<span data-ttu-id="61a67-128">In __Simple3DGame::Initialize__, wobei __M\_controller__ und __M\_renderer__ auch initialisiert wurden, müssen wir das Audiomodul eingerichtet und Vorbereitungen für die Soundwiedergabe.</span><span class="sxs-lookup"><span data-stu-id="61a67-128">In __Simple3DGame::Initialize__, where __m\_controller__ and __m\_renderer__ are also initialized, we set up the audio engine and get it ready to play sounds.</span></span>

 * <span data-ttu-id="61a67-129">Erstellen Sie __M\_audioController__, dabei handelt es sich um eine Instanz der [Audio](#audioh) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="61a67-129">Create __m\_audioController__, which is an instance of the [Audio](#audioh) class.</span></span>
 * <span data-ttu-id="61a67-130">Erstellen Sie die Audioressourcen erforderlich, die mit der [Audio::CreateDeviceIndependentResources](#audiocreatedeviceindependentresources-method) -Methode.</span><span class="sxs-lookup"><span data-stu-id="61a67-130">Create the audio resources needed using the [Audio::CreateDeviceIndependentResources](#audiocreatedeviceindependentresources-method) method.</span></span> <span data-ttu-id="61a67-131">Hier, dass zwei __XAudio2__ -Objekte &mdash; eine Musik-Engine-Objekt und ein sound Modulobjekt und eine mastering Voice für jedes von ihnen erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="61a67-131">Here, two __XAudio2__ objects &mdash; a music engine object and a sound engine object, and a mastering voice for each of them were created.</span></span> <span data-ttu-id="61a67-132">Das Musik-Engine-Objekt kann zum Wiedergeben von Hintergrundmusik für Ihr Spiel verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="61a67-132">The music engine object can be used to play background music for your game.</span></span> <span data-ttu-id="61a67-133">Das sound-Modul kann verwendet werden, um in Ihrem Spiel Soundeffekte.</span><span class="sxs-lookup"><span data-stu-id="61a67-133">The sound engine can be used to play sound effects in your game.</span></span> <span data-ttu-id="61a67-134">Weitere Informationen finden Sie unter [Erstellen und initialisieren die Audioressourcen](#create-and-initialize-the-audio-resources).</span><span class="sxs-lookup"><span data-stu-id="61a67-134">For more info, see [Create and initialize the audio resources](#create-and-initialize-the-audio-resources).</span></span>
 * <span data-ttu-id="61a67-135">Erstellen Sie __MediaReader__, dabei handelt es sich um eine Instanz der [MediaReader](#mediareaderh) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="61a67-135">Create __mediaReader__, which is an instance of [MediaReader](#mediareaderh) class.</span></span> <span data-ttu-id="61a67-136">[MediaReader](#mediareaderh), die eine Hilfsklasse für die [SoundEffect](#soundeffecth) -Klasse ist, kleine Audiodateien synchron aus Speicherort liest und gibt die Sounddaten als Byte-Array zurück.</span><span class="sxs-lookup"><span data-stu-id="61a67-136">[MediaReader](#mediareaderh), which is a helper class for the [SoundEffect](#soundeffecth) class, reads small audio files synchronously from file location and returns sound data as a byte array.</span></span>
 * <span data-ttu-id="61a67-137">Verwenden Sie [Mediareader](#mediareaderloadmedia-method) , zum Laden von Audiodateien von seinem Standort und erstellen Sie eine Variable __TargetHitSound__ der geladenen WAV-sound Daten.</span><span class="sxs-lookup"><span data-stu-id="61a67-137">Use [MediaReader::LoadMedia](#mediareaderloadmedia-method) to load sound files from its location and create a __targetHitSound__ variable to hold the loaded .wav sound data.</span></span> <span data-ttu-id="61a67-138">Weitere Informationen finden Sie in der [Load-Audiodatei](#load-audio).</span><span class="sxs-lookup"><span data-stu-id="61a67-138">For more info, see [Load audio file](#load-audio).</span></span> 

<span data-ttu-id="61a67-139">Soundeffekte sind das spielobjekt zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="61a67-139">Sound effects are associated with the game object.</span></span> <span data-ttu-id="61a67-140">Wenn eine mit diesem Spiel Objekt Kollision löst also den Soundeffekt wiedergegeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="61a67-140">So when a collision occurs with that game object, it triggers the sound effect to be played.</span></span> <span data-ttu-id="61a67-141">In diesem Beispielspiel haben wir Soundeffekte für die Munition (was wir verwenden, um Ziele anvisiert) und das Ziel.</span><span class="sxs-lookup"><span data-stu-id="61a67-141">In this game sample, we have sound effects for the ammo (what we use to shoot targets with) and for the target.</span></span> 
    
* <span data-ttu-id="61a67-142">In der __Render__ -Klasse besteht eine __HitSound__ -Eigenschaft, die verwendet wird, um den Soundeffekt auf das Objekt zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="61a67-142">In the __GameObject__ class, there's a __HitSound__ property that is used to associate the sound effect to the object.</span></span>
* <span data-ttu-id="61a67-143">Erstellen Sie eine neue Instanz der Klasse [SoundEffect](#soundeffecth) und initialisieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="61a67-143">Create a new instance of the [SoundEffect](#soundeffecth) class and initialize it.</span></span> <span data-ttu-id="61a67-144">Während der Initialisierung wird eine quellstimme für die Soundeffekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="61a67-144">During initialization, a source voice for the sound effect is created.</span></span> 
* <span data-ttu-id="61a67-145">Diese Klasse spielt eine Audiodatei, die über eine mastering Voice von der " [Audio](#audioh) "-Klasse bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="61a67-145">This class plays a sound using a mastering voice provided from the [Audio](#audioh) class.</span></span> <span data-ttu-id="61a67-146">Sounddaten werden mithilfe der Klasse [MediaReader](#mediareaderh) Speicherort der Datei gelesen werden.</span><span class="sxs-lookup"><span data-stu-id="61a67-146">Sound data is read from file location using the [MediaReader](#mediareaderh) class.</span></span> <span data-ttu-id="61a67-147">Weitere Informationen finden Sie in der [Sound-Objekt zuzuordnen](#associate-sound-to-object).</span><span class="sxs-lookup"><span data-stu-id="61a67-147">For more info, see [Associate sound to object](#associate-sound-to-object).</span></span>

>[!Note]
><span data-ttu-id="61a67-148">Der tatsächliche Trigger wiedergegeben wird durch die Bewegung und Kollision dieser Objekte Spiel bestimmt.</span><span class="sxs-lookup"><span data-stu-id="61a67-148">The actual trigger to play the sound is determined by the movement and collision of these game objects.</span></span> <span data-ttu-id="61a67-149">Der Aufruf tatsächlich diese Sounds wiedergegeben werden daher in der Methode [Simple3DGame::UpdateDynamics](#simple3dgameupdatedynamics-method) definiert.</span><span class="sxs-lookup"><span data-stu-id="61a67-149">Hence, the call to actually play these sounds are defined in the [Simple3DGame::UpdateDynamics](#simple3dgameupdatedynamics-method) method.</span></span> <span data-ttu-id="61a67-150">Weitere Informationen finden Sie unter [der Sound wiedergegeben](#play-the-sound).</span><span class="sxs-lookup"><span data-stu-id="61a67-150">For more info, go to [Play the sound](#play-the-sound).</span></span>

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

## <a name="create-and-initialize-the-audio-resources"></a><span data-ttu-id="61a67-151">Erstellen und Initialisieren der Audioressourcen</span><span class="sxs-lookup"><span data-stu-id="61a67-151">Create and initialize the audio resources</span></span>

* <span data-ttu-id="61a67-152">Verwenden Sie [XAudio2Create](https://msdn.microsoft.com/library/windows/desktop/ee419212), eine XAudio2-API, um zwei neue XAudio2-Objekte erstellt, die die Musik und Sound Effekt-Engines zu definieren.</span><span class="sxs-lookup"><span data-stu-id="61a67-152">Use [XAudio2Create](https://msdn.microsoft.com/library/windows/desktop/ee419212), an XAudio2 API, to create two new XAudio2 objects which define the music and sound effect engines.</span></span> <span data-ttu-id="61a67-153">Diese Methode gibt einen Zeiger auf das Objekt [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908) -Schnittstelle, die alle Audiomodul Zustände, die audioverarbeitung Thread, der Stimme Graph und mehr verwaltet.</span><span class="sxs-lookup"><span data-stu-id="61a67-153">This method returns a pointer to the object's [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908) interface that manages all audio engine states, the audio processing thread, the voice graph, and more.</span></span>
* <span data-ttu-id="61a67-154">Nachdem die Module instanziiert wurden, verwenden Sie [IXAudio2::CreateMasteringVoice](https://msdn.microsoft.com/library/windows/desktop/hh405048) , um eine mastering Voice für jedes der sound Modulobjekte erstellen.</span><span class="sxs-lookup"><span data-stu-id="61a67-154">After the engines have been instantiated, use [IXAudio2::CreateMasteringVoice](https://msdn.microsoft.com/library/windows/desktop/hh405048) to create a mastering voice for each of the sound engine objects.</span></span>

<span data-ttu-id="61a67-155">Weitere Informationen finden Sie unter [So: Initialisieren von XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415779.aspx).</span><span class="sxs-lookup"><span data-stu-id="61a67-155">For more info, go to [How to: Initialize XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415779.aspx).</span></span>

### <a name="audiocreatedeviceindependentresources-method"></a><span data-ttu-id="61a67-156">Audio::CreateDeviceIndependentResources-Methode</span><span class="sxs-lookup"><span data-stu-id="61a67-156">Audio::CreateDeviceIndependentResources method</span></span>

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

## <a name="load-audio-file"></a><span data-ttu-id="61a67-157">Load-Audiodatei</span><span class="sxs-lookup"><span data-stu-id="61a67-157">Load audio file</span></span>

<span data-ttu-id="61a67-158">Im Beispielspiel wird der Code zum Lesen von Audioformat Dateien in [MediaReader.h](#mediareaderh)/cpp__ definiert.</span><span class="sxs-lookup"><span data-stu-id="61a67-158">In the game sample, the code for reading audio format files is defined in [MediaReader.h](#mediareaderh)/cpp__.</span></span>  <span data-ttu-id="61a67-159">Rufen Sie zum Lesen einer codierten WAV-Audiodatei [Mediareader](#mediareaderloadmedia-method), und übergeben Sie den Dateinamen der die WAV-Datei als Eingabeparameter.</span><span class="sxs-lookup"><span data-stu-id="61a67-159">To read an encoded .wav audio file, call [MediaReader::LoadMedia](#mediareaderloadmedia-method), passing in the filename of the .wav as the input parameter.</span></span>

### <a name="mediareaderloadmedia-method"></a><span data-ttu-id="61a67-160">Mediareader-Methode</span><span class="sxs-lookup"><span data-stu-id="61a67-160">MediaReader::LoadMedia method</span></span>

<span data-ttu-id="61a67-161">Diese Methode verwendet die [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)-APIs, um die WAV-Audiodatei als Pulse Code Modulation (PCM)-Puffer einzulesen.</span><span class="sxs-lookup"><span data-stu-id="61a67-161">This method uses the [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) APIs to read in the .wav audio file as a Pulse Code Modulation (PCM) buffer.</span></span>

#### <a name="set-up-the-source-reader"></a><span data-ttu-id="61a67-162">Einrichten der Source-Reader</span><span class="sxs-lookup"><span data-stu-id="61a67-162">Set up the Source Reader</span></span>

1. <span data-ttu-id="61a67-163">Verwenden Sie [MFCreateSourceReaderFromURL](https://msdn.microsoft.com/library/windows/desktop/dd388110) , um ein Medium Quellenreader ([IMFSourceReader](https://msdn.microsoft.com/library/windows/desktop/dd374655)) erstellen.</span><span class="sxs-lookup"><span data-stu-id="61a67-163">Use [MFCreateSourceReaderFromURL](https://msdn.microsoft.com/library/windows/desktop/dd388110) to create a media source reader ([IMFSourceReader](https://msdn.microsoft.com/library/windows/desktop/dd374655)).</span></span>
2. <span data-ttu-id="61a67-164">Verwenden Sie [MFCreateMediaType](https://msdn.microsoft.com/library/windows/desktop/ms693861) zum Erstellen eines Media-Typ ([IMFMediaType](https://msdn.microsoft.com/library/windows/desktop/ms704850))-Objekts (_MediaType_).</span><span class="sxs-lookup"><span data-stu-id="61a67-164">Use [MFCreateMediaType](https://msdn.microsoft.com/library/windows/desktop/ms693861) to create a media type ([IMFMediaType](https://msdn.microsoft.com/library/windows/desktop/ms704850)) object (_mediaType_).</span></span> <span data-ttu-id="61a67-165">Es steht eine Beschreibung der Media-Format.</span><span class="sxs-lookup"><span data-stu-id="61a67-165">It represents a description of a media format.</span></span> 
3. <span data-ttu-id="61a67-166">Geben Sie, dass die _MediaType_decodierten Ausgabe PCM-Audio, die ein audio-Typ ist, den __XAudio2__ verwenden können.</span><span class="sxs-lookup"><span data-stu-id="61a67-166">Specify that the _mediaType_'s decoded output is PCM audio, which is an audio type that __XAudio2__ can use.</span></span>
4. <span data-ttu-id="61a67-167">Legt Medientyp decodierten Ausgabe für die Quelle Leser durch Aufrufen von [imfsourcereader:: Setcurrentmediatype](https://msdn.microsoft.com/library/windows/desktop/dd374667.aspx).</span><span class="sxs-lookup"><span data-stu-id="61a67-167">Sets the decoded output media type for the source reader by calling [IMFSourceReader::SetCurrentMediaType](https://msdn.microsoft.com/library/windows/desktop/dd374667.aspx).</span></span>

<span data-ttu-id="61a67-168">Weitere Informationen dazu, warum wir der Quellenreader verwendet werden finden Sie unter [Quellenreader](https://msdn.microsoft.com/library/windows/desktop/dd940436.aspx).</span><span class="sxs-lookup"><span data-stu-id="61a67-168">For more info on why we use the Source Reader, go to [Source Reader](https://msdn.microsoft.com/library/windows/desktop/dd940436.aspx).</span></span>

#### <a name="describe-the-data-format-of-the-audio-stream"></a><span data-ttu-id="61a67-169">Das Format des Audiostreams zu beschreiben</span><span class="sxs-lookup"><span data-stu-id="61a67-169">Describe the data format of the audio stream</span></span>

1. <span data-ttu-id="61a67-170">Verwenden Sie [Getcurrentmediatype](https://msdn.microsoft.com/library/windows/desktop/dd374660) , um den aktuellen Medientyp für den Stream abzurufen.</span><span class="sxs-lookup"><span data-stu-id="61a67-170">Use [IMFSourceReader::GetCurrentMediaType](https://msdn.microsoft.com/library/windows/desktop/dd374660) to get the current media type for the stream.</span></span>
2. <span data-ttu-id="61a67-171">Verwenden Sie [imfmediatype:: Mfcreatewaveformatexfrommfmediatype](https://msdn.microsoft.com/library/windows/desktop/ms702177) , um den aktuellen audio Medientyp werden einem Puffer [WAVEFORMATEX](https://msdn.microsoft.com/library/windows/hardware/ff538799) , verwenden die Ergebnisse des vorherigen Vorgangs als Eingabe zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="61a67-171">Use [IMFMediaType::MFCreateWaveFormatExFromMFMediaType](https://msdn.microsoft.com/library/windows/desktop/ms702177) to convert the current audio media type to a [WAVEFORMATEX](https://msdn.microsoft.com/library/windows/hardware/ff538799) buffer, using the results of the earlier operation as input.</span></span> <span data-ttu-id="61a67-172">Diese Struktur gibt das Format des Audiostreams wiegen, die nach dem Laden Audiodaten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="61a67-172">This structure specifies the data format of the wave audio stream that is used after audio is loaded.</span></span> 

<span data-ttu-id="61a67-173">Das __WAVEFORMATEX__ -Format kann verwendet werden, um den PCM-Puffer zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="61a67-173">The __WAVEFORMATEX__ format can be used to describe the PCM buffer.</span></span> <span data-ttu-id="61a67-174">Im Vergleich zu der [WAVEFORMATEXTENSIBLE](https://msdn.microsoft.com/library/windows/hardware/ff538802) -Struktur kann er nur verwendet werden eine Teilmenge der audio wiegen Formate zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="61a67-174">As compared to the [WAVEFORMATEXTENSIBLE](https://msdn.microsoft.com/library/windows/hardware/ff538802) structure, it can only be used to describe a subset of audio wave formats.</span></span> <span data-ttu-id="61a67-175">Weitere Informationen zu den Unterschieden zwischen __WAVEFORMATEX__ und __WAVEFORMATEXTENSIBLE__finden Sie in [Extensible wiegen-Format-Deskriptoren](https://docs.microsoft.com/windows-hardware/drivers/audio/extensible-wave-format-descriptors).</span><span class="sxs-lookup"><span data-stu-id="61a67-175">For more info about the differences between __WAVEFORMATEX__ and __WAVEFORMATEXTENSIBLE__, see [Extensible Wave-Format Descriptors](https://docs.microsoft.com/windows-hardware/drivers/audio/extensible-wave-format-descriptors).</span></span>

#### <a name="read-the-audio-stream"></a><span data-ttu-id="61a67-176">Lesen Sie den Audiostream</span><span class="sxs-lookup"><span data-stu-id="61a67-176">Read the audio stream</span></span>

1.  <span data-ttu-id="61a67-177">Rufen Sie die Dauer in Sekunden des Audiostreams zu durch Aufrufen von [Getpresentationattribute](https://msdn.microsoft.com/library/windows/desktop/dd374662) und dann konvertiert die Dauer in Bytes.</span><span class="sxs-lookup"><span data-stu-id="61a67-177">Get the duration, in seconds, of the audio stream by calling [IMFSourceReader::GetPresentationAttribute](https://msdn.microsoft.com/library/windows/desktop/dd374662) and then converts the duration to bytes.</span></span>
2.  <span data-ttu-id="61a67-178">Lesen Sie die Audiodatei als Datenstrom, durch den Aufruf [Readsample](https://msdn.microsoft.com/library/windows/desktop/dd374665).</span><span class="sxs-lookup"><span data-stu-id="61a67-178">Read the audio file in as a stream by calling [IMFSourceReader::ReadSample](https://msdn.microsoft.com/library/windows/desktop/dd374665).</span></span> <span data-ttu-id="61a67-179">__ReadSample__ liest das nächste Beispiel aus der Medienquelle.</span><span class="sxs-lookup"><span data-stu-id="61a67-179">__ReadSample__ reads the next sample from the media source.</span></span>
3.  <span data-ttu-id="61a67-180">Verwenden Sie [IMFSample::ConvertToContiguousBuffer](https://msdn.microsoft.com/library/windows/desktop/ms698917.aspx) zum Kopieren von Inhalt des audiosample-Puffers (_Beispiel_) in einem Array (_MediaBuffer_).</span><span class="sxs-lookup"><span data-stu-id="61a67-180">Use [IMFSample::ConvertToContiguousBuffer](https://msdn.microsoft.com/library/windows/desktop/ms698917.aspx) to copy contents of the audio sample buffer (_sample_) into an array (_mediaBuffer_).</span></span>

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
## <a name="associate-sound-to-object"></a><span data-ttu-id="61a67-181">Zuordnen von Sound-Objekt</span><span class="sxs-lookup"><span data-stu-id="61a67-181">Associate sound to object</span></span>

<span data-ttu-id="61a67-182">Zuordnen von Sounds für das Objekt findet statt, wenn das Spiel in der [Simple3DGame::Initialize](#simple3dgameinitialize-method) -Methode initialisiert.</span><span class="sxs-lookup"><span data-stu-id="61a67-182">Associating sounds to the object takes place when the game initializes, in the [Simple3DGame::Initialize](#simple3dgameinitialize-method) method.</span></span>

<span data-ttu-id="61a67-183">Zusammenfassung:</span><span class="sxs-lookup"><span data-stu-id="61a67-183">Recap:</span></span>
* <span data-ttu-id="61a67-184">In der __Render__ -Klasse besteht eine __HitSound__ -Eigenschaft, die verwendet wird, um den Soundeffekt auf das Objekt zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="61a67-184">In the __GameObject__ class, there's a __HitSound__ property that is used to associate the sound effect to the object.</span></span>
* <span data-ttu-id="61a67-185">Erstellen Sie eine neue Instanz des Klassenobjekts [SoundEffect](#soundeffecth) , und ordnen Sie sie der Spielobjekte.</span><span class="sxs-lookup"><span data-stu-id="61a67-185">Create a new instance of the [SoundEffect](#soundeffecth) class object and associate it with the game object.</span></span> <span data-ttu-id="61a67-186">Diese Klasse spielt eine Audiodatei, die Verwendung von __XAudio2__ APIs.</span><span class="sxs-lookup"><span data-stu-id="61a67-186">This class plays a sound using __XAudio2__ APIs.</span></span>  <span data-ttu-id="61a67-187">Es verwendet eine mastering Voice durch die " [Audio](#audioh) "-Klasse bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="61a67-187">It uses a mastering voice provided by the [Audio](#audioh) class.</span></span> <span data-ttu-id="61a67-188">Die Sounddaten können aus den Speicherort der Datei mit der Klasse [MediaReader](#mediareaderh) gelesen werden.</span><span class="sxs-lookup"><span data-stu-id="61a67-188">The sound data can be read from file location using the [MediaReader](#mediareaderh) class.</span></span>

<span data-ttu-id="61a67-189">[SoundEffect:: Initialize](#soundeffectinitialize-method) dient zum Initialisieren der __SoundEffect__ -Instanz mit den folgenden Eingabeparameter: Zeiger auf sound Modulobjekt (IXAudio2-Objekte in der [Audio::CreateDeviceIndependentResources](#audiocreatedeviceindependentresources-method) -Methode erstellt) Zeiger zum Formatieren der WAV-Datei mit __mediareader:: Getoutputwaveformatex__und die Sounddaten mithilfe [mediareader:: Loadmedia](#mediareaderloadmedia-method) -Methode geladen.</span><span class="sxs-lookup"><span data-stu-id="61a67-189">[SoundEffect::Initialize](#soundeffectinitialize-method) is used to initalize the __SoundEffect__ instance with the following input parameters: pointer to sound engine object (IXAudio2 objects created in the [Audio::CreateDeviceIndependentResources](#audiocreatedeviceindependentresources-method) method), pointer to format of the .wav file using __MediaReader::GetOutputWaveFormatEx__, and the sound data loaded using [MediaReader::LoadMedia](#mediareaderloadmedia-method) method.</span></span> <span data-ttu-id="61a67-190">Während der Initialisierung wird auch die quellstimme für die Soundeffekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="61a67-190">During initialization, the source voice for the sound effect is also created.</span></span>

### <a name="soundeffectinitialize-method"></a><span data-ttu-id="61a67-191">SoundEffect:: Initialize-Methode</span><span class="sxs-lookup"><span data-stu-id="61a67-191">SoundEffect::Initialize method</span></span>

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

## <a name="play-the-sound"></a><span data-ttu-id="61a67-192">Den Sound</span><span class="sxs-lookup"><span data-stu-id="61a67-192">Play the sound</span></span>

<span data-ttu-id="61a67-193">Trigger Soundeffekte sind in [Simple3DGame::UpdateDynamics](#simple3dgameupdatedynamics-method) Methode definiert, da es sich handelt, in denen Bewegung der Objekte werden aktualisiert und Kollisionen zwischen Objekten wird bestimmt.</span><span class="sxs-lookup"><span data-stu-id="61a67-193">Triggers to play sound effects are defined in [Simple3DGame::UpdateDynamics](#simple3dgameupdatedynamics-method) method because this is where movement of the objects are updated and collision between objects is determined.</span></span>

<span data-ttu-id="61a67-194">Da die Interaktion zwischen Objekten erheblich, je nachdem, das Spiel unterscheidet sich werden nicht wir die Dynamik der hier die Spielobjekte zu erläutern.</span><span class="sxs-lookup"><span data-stu-id="61a67-194">Since interaction of between objects differs greatly, depending on the game, we are not going to discuss the dynamics of the game objects here.</span></span> <span data-ttu-id="61a67-195">Wenn Sie ihre Implementierung verstehen interessiert sind, wechseln Sie zu [Simple3DGame::UpdateDynamics](#simple3dgameupdatedynamics-method) -Methode.</span><span class="sxs-lookup"><span data-stu-id="61a67-195">If you're interested to understand its implementation, go to [Simple3DGame::UpdateDynamics](#simple3dgameupdatedynamics-method) method.</span></span>

<span data-ttu-id="61a67-196">Im Prinzip Wenn eine Kollision auftritt, löst den Soundeffekt zum Wiedergeben von durch Aufrufen von [SoundEffect::PlaySound]((soundeffectplaysound-method).</span><span class="sxs-lookup"><span data-stu-id="61a67-196">In principle, when a collision occurs, it triggers the sound effect to play by calling [SoundEffect::PlaySound]((soundeffectplaysound-method).</span></span> <span data-ttu-id="61a67-197">Diese Methode werden keine Soundeffekte, die gerade wiedergegeben und den Puffer im Arbeitsspeicher mit der gewünschten Sounddaten in die Warteschlange beendet.</span><span class="sxs-lookup"><span data-stu-id="61a67-197">This method stops any sound effects that's currently playing and queues the in-memory buffer with the desired sound data.</span></span> <span data-ttu-id="61a67-198">Quellstimme verwendet, um das Volume festlegen, übermitteln Sounddaten und starten Sie die Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="61a67-198">It uses source voice to set the volume, submit sound data, and start the playback.</span></span>

### <a name="soundeffectplaysound-method"></a><span data-ttu-id="61a67-199">SoundEffect::-Methode</span><span class="sxs-lookup"><span data-stu-id="61a67-199">SoundEffect::PlaySound method</span></span>

* <span data-ttu-id="61a67-200">Source Voice-Objekt **M\_sourceVoice** verwendet, um die Wiedergabe von die Sounddaten Puffer **M\_soundData** zu starten</span><span class="sxs-lookup"><span data-stu-id="61a67-200">Uses the source voice object **m\_sourceVoice** to start the playback of the sound data buffer **m\_soundData**</span></span>
* <span data-ttu-id="61a67-201">Erstellt eine [XAUDIO2\_BUFFER](https://msdn.microsoft.com/library/windows/desktop/ee419228), zu dem sie einen Verweis auf den sounddatenpuffer bereitstellt, und übermittelt ihn dann mit einem Aufruf von [IXAudio2SourceVoice::SubmitSourceBuffer](https://msdn.microsoft.com/library/windows/desktop/ee418473).</span><span class="sxs-lookup"><span data-stu-id="61a67-201">Creates an [XAUDIO2\_BUFFER](https://msdn.microsoft.com/library/windows/desktop/ee419228), to which it provides a reference to the sound data buffer, and then submits it with a call to [IXAudio2SourceVoice::SubmitSourceBuffer](https://msdn.microsoft.com/library/windows/desktop/ee418473).</span></span> 
* <span data-ttu-id="61a67-202">Wenn die Sounddaten in die Warteschlange eingereiht sind, startet **SoundEffect::PlaySound** die Wiedergabe durch einen Aufruf von [IXAudio2SourceVoice::Start](https://msdn.microsoft.com/library/windows/desktop/ee418471).</span><span class="sxs-lookup"><span data-stu-id="61a67-202">With the sound data queued up, **SoundEffect::PlaySound** starts play back by calling [IXAudio2SourceVoice::Start](https://msdn.microsoft.com/library/windows/desktop/ee418471).</span></span>

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

### <a name="simple3dgameupdatedynamics-method"></a><span data-ttu-id="61a67-203">Simple3DGame::UpdateDynamics-Methode</span><span class="sxs-lookup"><span data-stu-id="61a67-203">Simple3DGame::UpdateDynamics method</span></span>

<span data-ttu-id="61a67-204">Die Methode __Simple3DGame::UpdateDynamics__ kümmert sich um die Interaktion und den Konflikt zwischen Spielobjekte.</span><span class="sxs-lookup"><span data-stu-id="61a67-204">The __Simple3DGame::UpdateDynamics__ method takes care the interaction and collision between game objects.</span></span> <span data-ttu-id="61a67-205">Wenn Objekte kollidieren (oder schneiden), löst den zugehörigen Soundeffekt wiedergegeben wird.</span><span class="sxs-lookup"><span data-stu-id="61a67-205">When objects collide (or intersect), it triggers the associated sound effect to play.</span></span>

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
## <a name="next-steps"></a><span data-ttu-id="61a67-206">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="61a67-206">Next steps</span></span>

<span data-ttu-id="61a67-207">Wir haben das UWP Framework, Grafiken, Steuerelemente, Benutzeroberfläche und Audio eines Windows 10-Spiels behandelt.</span><span class="sxs-lookup"><span data-stu-id="61a67-207">We have covered the UWP framework, graphics, controls, user interface, and audio of a Windows 10 game.</span></span> <span data-ttu-id="61a67-208">Der nächste Teil des Lernprogramms [Erweitern des beispielspiels](tutorial-resources.md)wird erläutert, andere Optionen, die bei der Entwicklung eines Spiels verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="61a67-208">The next part of this tutorial, [Extending the game sample](tutorial-resources.md), explains other options that can be used when developing a game.</span></span>

## <a name="audio-concepts"></a><span data-ttu-id="61a67-209">Audio-Konzepte</span><span class="sxs-lookup"><span data-stu-id="61a67-209">Audio concepts</span></span>

<span data-ttu-id="61a67-210">Verwenden Sie für die Entwicklung für Windows 10-Spiele XAudio2-Version 2.9.</span><span class="sxs-lookup"><span data-stu-id="61a67-210">For Windows 10 games development, use XAudio2 version 2.9.</span></span> <span data-ttu-id="61a67-211">Diese Version wird mit Windows 10 geliefert.</span><span class="sxs-lookup"><span data-stu-id="61a67-211">This version is shipped with Windows 10.</span></span> <span data-ttu-id="61a67-212">Weitere Informationen finden Sie unter [XAudio2-Versionen](https://msdn.microsoft.com/library/windows/desktop/ee415802.aspx).</span><span class="sxs-lookup"><span data-stu-id="61a67-212">For more info, go to [XAudio2 Versions](https://msdn.microsoft.com/library/windows/desktop/ee415802.aspx).</span></span>

<span data-ttu-id="61a67-213">__AudioX2__ ist eine Low-Level-API, die signalverarbeitung und -abmischung bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="61a67-213">__AudioX2__ is a low-level API that provides signal processing and mixing foundation.</span></span> <span data-ttu-id="61a67-214">Weitere Informationen finden Sie unter [XAudio2 Schlüssel Konzepte](https://msdn.microsoft.com/library/windows/desktop/ee415764.aspx).</span><span class="sxs-lookup"><span data-stu-id="61a67-214">For more info, see [XAudio2 Key Concepts](https://msdn.microsoft.com/library/windows/desktop/ee415764.aspx).</span></span>

### <a name="xaudio2-voices"></a><span data-ttu-id="61a67-215">XAudio2-stimmen</span><span class="sxs-lookup"><span data-stu-id="61a67-215">XAudio2 voices</span></span>

<span data-ttu-id="61a67-216">Es gibt drei Arten von XAudio2 Voice Objekte: quellstimme, submixstimme und masterstimme.</span><span class="sxs-lookup"><span data-stu-id="61a67-216">There are three types of XAudio2 voice objects: source, submix, and mastering voices.</span></span> <span data-ttu-id="61a67-217">Stimmen sind, dass die XAudio2-Objekte verarbeitet, bearbeiten und zum Wiedergeben von Audiodaten verwenden.</span><span class="sxs-lookup"><span data-stu-id="61a67-217">Voices are the objects XAudio2 use to process, to manipulate, and to play audio data.</span></span> 
* <span data-ttu-id="61a67-218">Quellstimmen verarbeiten die vom Client bereitgestellten Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="61a67-218">Source voices operate on audio data provided by the client.</span></span> 
* <span data-ttu-id="61a67-219">Quell- und Submixstimmen senden ihre Ausgabe an mindestens eine Submix- oder Masterstimme.</span><span class="sxs-lookup"><span data-stu-id="61a67-219">Source and submix voices send their output to one or more submix or mastering voices.</span></span> 
* <span data-ttu-id="61a67-220">Submix- und Masterstimmen mischen die Audiodaten aller Stimmen, von denen sie Daten erhalten, und verarbeiten das Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="61a67-220">Submix and mastering voices mix the audio from all voices feeding them, and operate on the result.</span></span> 
* <span data-ttu-id="61a67-221">Masterstimmen empfangen von Daten aus quellstimmen und submixstimmen und sendet Daten an die Audiohardware.</span><span class="sxs-lookup"><span data-stu-id="61a67-221">Mastering voices receive data from source voices and submix voices, and sends that data to the audio hardware.</span></span>

<span data-ttu-id="61a67-222">Weitere Informationen finden Sie unter [XAudio2-stimmen](https://msdn.microsoft.com/library/windows/desktop/ee415824.aspx).</span><span class="sxs-lookup"><span data-stu-id="61a67-222">For more info, go to [XAudio2 voices](https://msdn.microsoft.com/library/windows/desktop/ee415824.aspx).</span></span>

### <a name="audio-graph"></a><span data-ttu-id="61a67-223">Audiodiagramm</span><span class="sxs-lookup"><span data-stu-id="61a67-223">Audio graph</span></span>

<span data-ttu-id="61a67-224">Audiodiagramm ist eine Sammlung von [XAudio2-stimmen](#xaudio2-voice-objects).</span><span class="sxs-lookup"><span data-stu-id="61a67-224">Audio graph is a collection of [XAudio2 voices](#xaudio2-voice-objects).</span></span> <span data-ttu-id="61a67-225">Audio auf einer Seite des ein audiodiagramm in quellstimmen beginnt, durchläuft optional ein oder mehrere submixstimmen und endet mit eine mastering Voice.</span><span class="sxs-lookup"><span data-stu-id="61a67-225">Audio starts at one side of an audio graph in source voices, optionally passes through one or more submix voices, and ends at a mastering voice.</span></span> <span data-ttu-id="61a67-226">Ein audiodiagramm enthält eine quellstimme für jeden Sound aktuell wiedergegebenen, NULL oder mehr submixstimmen und eine masterstimme.</span><span class="sxs-lookup"><span data-stu-id="61a67-226">An audio graph will contain a source voice for each sound currently playing, zero or more submix voices, and one mastering voice.</span></span> <span data-ttu-id="61a67-227">Das einfachste audiodiagramm und die Mindestanzahl der benötigten ein Geräusch in XAudio2 ist eine einzelne quellstimme direkt an eine mastering Voice ausgeben.</span><span class="sxs-lookup"><span data-stu-id="61a67-227">The simplest audio graph, and the minimum needed to make a noise in XAudio2, is a single source voice outputting directly to a mastering voice.</span></span> <span data-ttu-id="61a67-228">Weitere Informationen finden Sie unter [audiodiagramme](https://msdn.microsoft.com/library/windows/desktop/ee415739.aspx).</span><span class="sxs-lookup"><span data-stu-id="61a67-228">For more info, go to [Audio graphs](https://msdn.microsoft.com/library/windows/desktop/ee415739.aspx).</span></span>

### <a name="additional-reading"></a><span data-ttu-id="61a67-229">Zusätzliche lesen</span><span class="sxs-lookup"><span data-stu-id="61a67-229">Additional reading</span></span>

* [<span data-ttu-id="61a67-230">So wird's gemacht: Initialisieren von XAudio2</span><span class="sxs-lookup"><span data-stu-id="61a67-230">How to: Initialize XAudio2</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee415779.aspx)
* [<span data-ttu-id="61a67-231">So wird's gemacht: Laden von Datendateien in XAudio2</span><span class="sxs-lookup"><span data-stu-id="61a67-231">How to: Load Audio Data Files in XAudio2</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee415781(v=vs.85).aspx)
* [<span data-ttu-id="61a67-232">So wird's gemacht: Wiedergeben von Ton mit XAudio2</span><span class="sxs-lookup"><span data-stu-id="61a67-232">How to: Play a Sound with XAudio2</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee415787.aspx)

## <a name="key-audio-h-files"></a><span data-ttu-id="61a67-233">Wichtige audio h-Dateien</span><span class="sxs-lookup"><span data-stu-id="61a67-233">Key audio .h files</span></span>

### <a name="audioh"></a><span data-ttu-id="61a67-234">Audio.h</span><span class="sxs-lookup"><span data-stu-id="61a67-234">Audio.h</span></span>

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
### <a name="mediareaderh"></a><span data-ttu-id="61a67-235">MediaReader.h</span><span class="sxs-lookup"><span data-stu-id="61a67-235">MediaReader.h</span></span>

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
### <a name="soundeffecth"></a><span data-ttu-id="61a67-236">SoundEffect.h</span><span class="sxs-lookup"><span data-stu-id="61a67-236">SoundEffect.h</span></span>

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


