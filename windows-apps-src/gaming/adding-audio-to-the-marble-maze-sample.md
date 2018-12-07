---
title: Hinzufügen von Audio zum Marble Maze-Beispiel
description: In diesem Dokument werden die wichtigsten Methoden beschrieben, die Sie berücksichtigen sollten, wenn Sie mit Audio arbeiten. Außerdem erfahren Sie, wie diese Methoden in Marble Maze angewendet werden.
ms.assetid: 77c23d0a-af6d-17b5-d69e-51d9885b0d44
ms.date: 10/18/2017
ms.topic: article
keywords: Windows10, UWP, Audio, Spiele, Beispiel
ms.localizationpriority: medium
ms.openlocfilehash: 666ea75f1d4f18121b7ae9fa3def3b455ae3e7a3
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8786317"
---
# <a name="adding-audio-to-the-marble-maze-sample"></a><span data-ttu-id="b2716-104">Hinzufügen von Audiodaten zum Marble Maze-Beispiel</span><span class="sxs-lookup"><span data-stu-id="b2716-104">Adding audio to the Marble Maze sample</span></span>

<span data-ttu-id="b2716-105">In diesem Dokument werden die wichtigsten Methoden beschrieben, die Sie berücksichtigen sollten, wenn Sie mit Audio arbeiten. Außerdem erfahren Sie, wie diese Methoden in Marble Maze angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="b2716-105">This document describes the key practices to consider when you work with audio and shows how Marble Maze applies these practices.</span></span> <span data-ttu-id="b2716-106">Marble Maze verwendet [MicrosoftMedia Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197), um Audioressourcen aus einer Datei zu laden, und [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049), um Audio zu mischen und wiederzugeben und Effekte auf Audio anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="b2716-106">Marble Maze uses [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) to load audio resources from files, and [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049) to mix and play audio and to apply effects to audio.</span></span>

<span data-ttu-id="b2716-107">Marble Maze gibt Musik im Hintergrund wieder und verwendet außerdem Spielsounds, die auf Spielereignisse hinweisen, beispielsweise wenn die Murmel an eine Wand prallt.</span><span class="sxs-lookup"><span data-stu-id="b2716-107">Marble Maze plays music in the background, and also uses gameplay sounds to indicate game events, such as when the marble hits a wall.</span></span> <span data-ttu-id="b2716-108">Wichtig ist bei der Implementierung, dass Marble Maze einen Hall- oder Echoeffekt verwendet, um den Klang einer aufprallenden Murmel zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="b2716-108">An important part of the implementation is that Marble Maze uses a reverb, or echo, effect to simulate the sound of a marble when it bounces.</span></span> <span data-ttu-id="b2716-109">Die Implementierung des Halleffekts bewirkt, dass Sie Echos in kleineren Räumen schneller und lauter hören. In größeren Räumen dagegen sind die Echos leiser und nicht so schnell zu hören.</span><span class="sxs-lookup"><span data-stu-id="b2716-109">The reverb effect implementation causes echoes to reach you more quickly and loudly in small rooms; echoes are quieter and reach you more slowly in larger rooms.</span></span>

> [!NOTE]
> <span data-ttu-id="b2716-110">Den Beispielcode für dieses Dokument finden Sie im [DirectX-Beispielspiel Marble Maze](http://go.microsoft.com/fwlink/?LinkId=624011).</span><span class="sxs-lookup"><span data-stu-id="b2716-110">The sample code that corresponds to this document is found in the [DirectX Marble Maze game sample](http://go.microsoft.com/fwlink/?LinkId=624011).</span></span>

<span data-ttu-id="b2716-111">Hier sind einige der wichtigsten in diesem Dokument erörterten Punkte für das Arbeiten mit Audio in Ihrem Spiel:</span><span class="sxs-lookup"><span data-stu-id="b2716-111">Here are some of the key points that this document discusses for when you work with audio in your game:</span></span>

- <span data-ttu-id="b2716-112">Ziehen Sie die Verwendung von Media Foundation zum Decodieren von Audioressourcen und XAudio2 zum Wiedergeben von Audio in Betracht.</span><span class="sxs-lookup"><span data-stu-id="b2716-112">Consider using Media Foundation to decode audio assets and XAudio2 to play audio.</span></span> <span data-ttu-id="b2716-113">Wenn Sie aber bereits einen Mechanismus zum Laden von Audioressourcen haben, der in einer UWP-App funktioniert, können Sie diesen Mechanismus verwenden.</span><span class="sxs-lookup"><span data-stu-id="b2716-113">However, if you have an existing audio asset-loading mechanism that works in a Universal Windows Platform (UWP) app, you can use it.</span></span>

- <span data-ttu-id="b2716-114">Ein Audiodiagramm enthält eine Quellstimme für jeden aktiven Sound, null oder mehr Submixstimmen und eine Masterstimme.</span><span class="sxs-lookup"><span data-stu-id="b2716-114">An audio graph contains one source voice for each active sound, zero or more submix voices, and one mastering voice.</span></span> <span data-ttu-id="b2716-115">Quellstimmen können in Submixstimmen und/oder die Masterstimme eingespeist werden.</span><span class="sxs-lookup"><span data-stu-id="b2716-115">Source voices can feed into submix voices and/or the mastering voice.</span></span> <span data-ttu-id="b2716-116">Submixstimmen können in andere Submixstimmen oder die Masterstimme eingespeist werden.</span><span class="sxs-lookup"><span data-stu-id="b2716-116">Submix voices feed into other submix voices or the mastering voice.</span></span>

- <span data-ttu-id="b2716-117">Wenn die Dateien für die Hintergrundmusik groß sind, können Sie die Musik in kleinere Puffer streamen, damit weniger Arbeitsspeicher verbraucht wird.</span><span class="sxs-lookup"><span data-stu-id="b2716-117">If your background music files are large, consider streaming your music into smaller buffers so that less memory is used.</span></span>

- <span data-ttu-id="b2716-118">Halten Sie gegebenenfalls die Audiowiedergabe an, wenn die App nicht mehr den Fokus hat, nicht mehr sichtbar ist oder angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="b2716-118">If it makes sense to do so, pause audio playback when the app loses focus or visibility, or is suspended.</span></span> <span data-ttu-id="b2716-119">Setzen Sie die Wiedergabe fort, wenn Ihre App wieder den Fokus erhält, wieder sichtbar wird oder fortgesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="b2716-119">Resume playback when your app regains focus, becomes visible, or is resumed.</span></span>

- <span data-ttu-id="b2716-120">Legen Sie Audiokategorien fest, die den Rollen der einzelnen Sounds entsprechen.</span><span class="sxs-lookup"><span data-stu-id="b2716-120">Set audio categories to reflect the role of each sound.</span></span> <span data-ttu-id="b2716-121">Zum Beispiel verwenden Sie in der Regel **AudioCategory\_GameMedia** für Hintergrundaudio im Spiel und **AudioCategory\_GameEffects** für Soundeffekte.</span><span class="sxs-lookup"><span data-stu-id="b2716-121">For example, you typically use **AudioCategory\_GameMedia** for game background audio and **AudioCategory\_GameEffects** for sound effects.</span></span>

- <span data-ttu-id="b2716-122">Behandeln Sie Geräteänderungen, einschließlich Kopfhörern, in dem Sie alle Audioressourcen und -schnittstellen freigeben und erneut erstellen.</span><span class="sxs-lookup"><span data-stu-id="b2716-122">Handle device changes, including headphones, by releasing and recreating all audio resources and interfaces.</span></span>

- <span data-ttu-id="b2716-123">Komprimieren Sie gegebenenfalls Audiodateien, wenn Sie den Speicherplatz und die Streamingkosten minimieren müssen.</span><span class="sxs-lookup"><span data-stu-id="b2716-123">Consider whether to compress audio files when minimizing disk space and streaming costs is a requirement.</span></span> <span data-ttu-id="b2716-124">Anderenfalls können Sie die Audiodateien unkomprimiert lassen, damit sie schneller geladen werden.</span><span class="sxs-lookup"><span data-stu-id="b2716-124">Otherwise, you can leave audio uncompressed so that it loads faster.</span></span>

## <a name="introducing-xaudio2-and-microsoft-media-foundation"></a><span data-ttu-id="b2716-125">Einführung in XAudio2 und MicrosoftMedia Foundation</span><span class="sxs-lookup"><span data-stu-id="b2716-125">Introducing XAudio2 and Microsoft Media Foundation</span></span>

<span data-ttu-id="b2716-126">XAudio2 ist eine Low-Level-Audiobibliothek für Windows, die speziell Audio in Spielen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b2716-126">XAudio2 is a low-level audio library for Windows that specifically supports game audio.</span></span> <span data-ttu-id="b2716-127">Sie enthält eine digitale Signalverarbeitung (Digital Signal Processing, DSP) und ein Audiodiagrammmodul für Spiele.</span><span class="sxs-lookup"><span data-stu-id="b2716-127">It provides a digital signal processing (DSP) and audio-graph engine for games.</span></span> <span data-ttu-id="b2716-128">Als Erweiterung der Vorgänger DirectSound und XAudio unterstützt XAudio2 Computertrends wie zum Beispiel SIMD-Gleitkommaarchitekturen und HD-Audio.</span><span class="sxs-lookup"><span data-stu-id="b2716-128">XAudio2 expands on its predecessors, DirectSound and XAudio, by supporting computing trends such as SIMD floating-point architectures and HD audio.</span></span> <span data-ttu-id="b2716-129">Außerdem werden die komplexeren Soundverarbeitungsanforderungen aktueller Spiele unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b2716-129">It also supports the more complex sound processing demands of today’s games.</span></span>

<span data-ttu-id="b2716-130">Im [Dokument zu den wichtigsten Konzepten von XAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415764) werden die wichtigsten Konzepte für die Verwendung von XAudio2 erläutert.</span><span class="sxs-lookup"><span data-stu-id="b2716-130">The document [XAudio2 Key Concepts](https://msdn.microsoft.com/library/windows/desktop/ee415764) explains the key concepts for using XAudio2.</span></span> <span data-ttu-id="b2716-131">Die Konzepte im Kurzüberblick:</span><span class="sxs-lookup"><span data-stu-id="b2716-131">In brief, the concepts are:</span></span>

- <span data-ttu-id="b2716-132">Die [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908)-Schnittstelle bildet den Kern des XAudio2-Moduls.</span><span class="sxs-lookup"><span data-stu-id="b2716-132">The [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908) interface is the core of the XAudio2 engine.</span></span> <span data-ttu-id="b2716-133">Marble Maze verwendet diese Schnittstelle, um Stimmen zu erstellen und Benachrichtigungen zu empfangen, wenn sich das Ausgabegerät ändert oder Fehler auftreten.</span><span class="sxs-lookup"><span data-stu-id="b2716-133">Marble Maze uses this interface to create voices and to receive notification when the output device changes or fails.</span></span>

- <span data-ttu-id="b2716-134">Eine **Stimme** verarbeitet Audiodaten, passt sie an und gibt sie wieder.</span><span class="sxs-lookup"><span data-stu-id="b2716-134">A **voice** processes, adjusts, and plays audio data.</span></span>

- <span data-ttu-id="b2716-135">Eine **Quellstimme** ist eine Sammlung von Audiokanälen (Mono, 5.1 usw.) und stellt einen Audiodatenstream dar.</span><span class="sxs-lookup"><span data-stu-id="b2716-135">A **source voice** is a collection of audio channels (mono, 5.1, and so on) and represents one stream of audio data.</span></span> <span data-ttu-id="b2716-136">In XAudio2 ist eine Quellstimme der Ausgangspunkt der Audioverarbeitung.</span><span class="sxs-lookup"><span data-stu-id="b2716-136">In XAudio2, a source voice is where audio processing begins.</span></span> <span data-ttu-id="b2716-137">Normalerweise werden die Sounddaten aus einer externen Quelle wie beispielsweise einer Datei oder einem Netzwerk geladen und an eine Quellstimme gesendet.</span><span class="sxs-lookup"><span data-stu-id="b2716-137">Typically, sound data is loaded from an external source, such as a file or a network, and is sent to a source voice.</span></span> <span data-ttu-id="b2716-138">In Marble Maze werden Sounddaten mithilfe von [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) aus Dateien geladen.</span><span class="sxs-lookup"><span data-stu-id="b2716-138">Marble Maze uses [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) to load sound data from files.</span></span> <span data-ttu-id="b2716-139">Media Foundation wird weiter unten in diesem Dokument vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="b2716-139">Media Foundation is introduced later in this document.</span></span>

- <span data-ttu-id="b2716-140">Eine **Submixstimme** verarbeitet Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="b2716-140">A **submix voice** processes audio data.</span></span> <span data-ttu-id="b2716-141">Bei dieser Verarbeitung kann zum Beispiel der Audiostream geändert werden oder mehrere Streams werden zu einem Stream kombiniert.</span><span class="sxs-lookup"><span data-stu-id="b2716-141">This processing can include changing the audio stream or combining multiple streams into one.</span></span> <span data-ttu-id="b2716-142">Marble Maze verwendet Submixe, um den Halleffekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b2716-142">Marble Maze uses submixes to create the reverb effect.</span></span>

- <span data-ttu-id="b2716-143">Eine **Masterstimme** kombiniert Daten aus Quell- und Submixstimmen und sendet Daten an die Audiohardware.</span><span class="sxs-lookup"><span data-stu-id="b2716-143">A **mastering voice** combines data from source and submix voices and sends that data to the audio hardware.</span></span>

- <span data-ttu-id="b2716-144">Ein **Audiodiagramm** enthält eine Quellstimme für jeden aktiven Sound, null oder mehrere Submixstimmen und nur eine Masterstimme .</span><span class="sxs-lookup"><span data-stu-id="b2716-144">An **audio graph** contains one source voice for each active sound, zero or more submix voices, and only one mastering voice.</span></span>

- <span data-ttu-id="b2716-145">Der Clientcode wird über einen **Rückruf** informiert, dass in einer Stimme oder in einem Modulobjekt ein Ereignis aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="b2716-145">A **callback** informs client code that some event has occurred in a voice or in an engine object.</span></span> <span data-ttu-id="b2716-146">Mithilfe von Rückrufen können Sie den Arbeitsspeicher wiederverwenden, wenn XAudio2 mit einem Puffer fertig ist, reagieren, wenn sich das Audiogerät ändert (z.B. wenn Sie Kopfhörer anschließen oder trennen) usw.</span><span class="sxs-lookup"><span data-stu-id="b2716-146">By using callbacks, you can reuse memory when XAudio2 is finished with a buffer, react when the audio device changes (for example, when you connect or disconnect headphones), and more.</span></span> <span data-ttu-id="b2716-147">Im Abschnitt [Behandeln von Kopfhörern und Geräteänderungen](#handling-headphones-and-device-changes) weiter unten in diesem Dokument erfahren Sie, wie Marble Maze diesen Mechanismus für die Behandlung von Geräteänderungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="b2716-147">[Handling headphones and device changes](#handling-headphones-and-device-changes) later in this document explains how Marble Maze uses this mechanism to handle device changes.</span></span>

<span data-ttu-id="b2716-148">Marble Maze verwendet zwei Audiomodule (mit anderen Worten: zwei [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908)-Objekte) zum Verarbeiten von Audio.</span><span class="sxs-lookup"><span data-stu-id="b2716-148">Marble Maze uses two audio engines (in other words, two [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908) objects) to process audio.</span></span> <span data-ttu-id="b2716-149">Ein Modul verarbeitet die Hintergrundmusik und das andere verarbeitet Spielsounds.</span><span class="sxs-lookup"><span data-stu-id="b2716-149">One engine processes the background music, and the other engine processes gameplay sounds.</span></span>

<span data-ttu-id="b2716-150">Außerdem muss Marble Maze für jedes Modul eine Masterstimme erstellen.</span><span class="sxs-lookup"><span data-stu-id="b2716-150">Marble Maze must also create one mastering voice for each engine.</span></span> <span data-ttu-id="b2716-151">Denken Sie daran, dass ein Mastermodul Audiostreams in einem Stream kombiniert und diesen Stream an die Audiohardware sendet.</span><span class="sxs-lookup"><span data-stu-id="b2716-151">Recall that a mastering engine combines audio streams into one stream and sends that stream to the audio hardware.</span></span> <span data-ttu-id="b2716-152">Der Stream für die Hintergrundmusik, eine Quellstimme, gibt Daten an eine Masterstimme und an zwei Submixstimmen aus.</span><span class="sxs-lookup"><span data-stu-id="b2716-152">The background music stream, a source voice, outputs data to a mastering voice and to two submix voices.</span></span> <span data-ttu-id="b2716-153">Die Submixstimmen führen den Halleffekt aus.</span><span class="sxs-lookup"><span data-stu-id="b2716-153">The submix voices perform the reverb effect.</span></span>

<span data-ttu-id="b2716-154">Media Foundation ist eine Multimediabibliothek, die viele Audio- und Videoformate unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b2716-154">Media Foundation is a multimedia library that supports many audio and video formats.</span></span> <span data-ttu-id="b2716-155">XAudio2 und Media Foundation ergänzen sich gegenseitig.</span><span class="sxs-lookup"><span data-stu-id="b2716-155">XAudio2 and Media Foundation complement each other.</span></span> <span data-ttu-id="b2716-156">Marble Maze verwendet Media Foundation zum Laden von Audioressourcen aus Dateien und XAudio2 zum Wiedergeben von Audio.</span><span class="sxs-lookup"><span data-stu-id="b2716-156">Marble Maze uses Media Foundation to load audio assets from files and uses XAudio2 to play audio.</span></span> <span data-ttu-id="b2716-157">Sie müssen Media Foundation nicht verwenden, um Audioressourcen zu laden.</span><span class="sxs-lookup"><span data-stu-id="b2716-157">You don't have to use Media Foundation to load audio assets.</span></span> <span data-ttu-id="b2716-158">Wenn Sie bereits einen Mechanismus zum Laden von Audioressourcen haben, der in einer UWP-App funktioniert, verwenden Sie diesen Mechanismus.</span><span class="sxs-lookup"><span data-stu-id="b2716-158">If you have an existing audio asset loading mechanism that works in Universal Windows Platform (UWP) apps, use it.</span></span> <span data-ttu-id="b2716-159">[Audio, Video und Kamera](../audio-video-camera/index.md) beschreibt verschiedene Methoden zur Implementierung von Audio in einer UWP-App.</span><span class="sxs-lookup"><span data-stu-id="b2716-159">[Audio, video, and camera](../audio-video-camera/index.md) discusses several ways of implementing audio in a UWP app.</span></span>

<span data-ttu-id="b2716-160">Weitere Informationen zu XAudio2 finden Sie im [Programmierhandbuch](https://msdn.microsoft.com/library/windows/desktop/ee415737).</span><span class="sxs-lookup"><span data-stu-id="b2716-160">For more information about XAudio2, see [Programming Guide](https://msdn.microsoft.com/library/windows/desktop/ee415737).</span></span> <span data-ttu-id="b2716-161">Weitere Informationen zu Media Foundation finden Sie unter [MicrosoftMedia Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="b2716-161">For more information about Media Foundation, see [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span>

## <a name="initializing-audio-resources"></a><span data-ttu-id="b2716-162">Initialisieren von Audioressourcen</span><span class="sxs-lookup"><span data-stu-id="b2716-162">Initializing audio resources</span></span>

<span data-ttu-id="b2716-163">Marble Maze verwendet eine WMA-Datei (Windows Media Audio) für die Hintergrundmusik und WAV-Dateien für Spielsounds.</span><span class="sxs-lookup"><span data-stu-id="b2716-163">Marble Mazes uses a Windows Media Audio (.wma) file for the background music, and WAV (.wav) files for gameplay sounds.</span></span> <span data-ttu-id="b2716-164">Diese Formate werden von Media Foundation unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b2716-164">These formats are supported by Media Foundation.</span></span> <span data-ttu-id="b2716-165">Obwohl das WAV-Dateiformat nativ von XAudio2 unterstützt wird, muss das Dateiformat von einem Spiel manuell analysiert werden, um die entsprechenden XAudio2-Datenstrukturen auszufüllen.</span><span class="sxs-lookup"><span data-stu-id="b2716-165">Although the .wav file format is natively supported by XAudio2, a game has to parse the file format manually to fill out the appropriate XAudio2 data structures.</span></span> <span data-ttu-id="b2716-166">Marble Maze verwendet Media Foundation, um die Arbeit mit WAV-Dateien zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="b2716-166">Marble Maze uses Media Foundation to more easily work with .wav files.</span></span> <span data-ttu-id="b2716-167">Die vollständige Liste der von Media Foundation unterstützten Medienformate finden Sie unter [Unterstützte Medienformate in Media Foundation](https://msdn.microsoft.com/library/windows/desktop/dd757927).</span><span class="sxs-lookup"><span data-stu-id="b2716-167">For the complete list of the media formats that are supported by Media Foundation, see [Supported Media Formats in Media Foundation](https://msdn.microsoft.com/library/windows/desktop/dd757927).</span></span> <span data-ttu-id="b2716-168">Marble Maze verwendet keine getrennten Entwurfszeit- und Laufzeit-Audioformate und keine Unterstützung für XAudio2-ADPCM-Komprimierung.</span><span class="sxs-lookup"><span data-stu-id="b2716-168">Marble Maze does not use separate design-time and run-time audio formats, and does not use XAudio2 ADPCM compression support.</span></span> <span data-ttu-id="b2716-169">Weitere Informationen zur ADPCM-Komprimierung in XAudio2 finden Sie in der Übersicht über [ADPCM](https://msdn.microsoft.com/library/windows/desktop/ee415711).</span><span class="sxs-lookup"><span data-stu-id="b2716-169">For more information about ADPCM compression in XAudio2, see [ADPCM Overview](https://msdn.microsoft.com/library/windows/desktop/ee415711).</span></span>

<span data-ttu-id="b2716-170">Die **Audio::CreateResources**-Methode, die von **MarbleMazeMain::LoadDeferredResources** aufgerufen wird, lädt die Audiostreams aus den Dateien, initialisiert die XAudio2-Modulobjekte und erstellt die Quell-, Submix- und Masterstimmen.</span><span class="sxs-lookup"><span data-stu-id="b2716-170">The **Audio::CreateResources** method, which is called from **MarbleMazeMain::LoadDeferredResources**, loads the audio streams from the files, initializes the XAudio2 engine objects, and creates the source, submix, and mastering voices.</span></span>

### <a name="creating-the-xaudio2-engines"></a><span data-ttu-id="b2716-171">Erstellen der XAudio2-Module</span><span class="sxs-lookup"><span data-stu-id="b2716-171">Creating the XAudio2 engines</span></span>

<span data-ttu-id="b2716-172">Bedenken Sie, dass Marble Maze für jedes verwendete Audiomodul ein [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908)-Objekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="b2716-172">Recall that Marble Maze creates one [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908) object to represent each audio engine that it uses.</span></span> <span data-ttu-id="b2716-173">Rufen Sie die [XAudio2Create](https://msdn.microsoft.com/library/windows/desktop/ee419212)-Methode auf, um ein Audiomodul zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b2716-173">To create an audio engine, call the [XAudio2Create](https://msdn.microsoft.com/library/windows/desktop/ee419212) method.</span></span> <span data-ttu-id="b2716-174">Das folgende Beispiel zeigt, wie Marble Maze das Audiomodul für die Verarbeitung der Hintergrundmusik erstellt.</span><span class="sxs-lookup"><span data-stu-id="b2716-174">The following example shows how Marble Maze creates the audio engine that processes background music.</span></span>

```cpp
// In Audio.h
class Audio
{
private:
    IXAudio2*                   m_musicEngine;
// ...
}

// In Audio.cpp
void Audio::CreateResources()
{
    try
    {
        // ...
        DX::ThrowIfFailed(
            XAudio2Create(&m_musicEngine)
            );
        // ...
    }
    // ...
}
```

<span data-ttu-id="b2716-175">Einen ähnlichen Schritt führt Marble Maze aus, um das Audiomodul zu erstellen, das die Spielsounds wiedergibt.</span><span class="sxs-lookup"><span data-stu-id="b2716-175">Marble Maze performs a similar step to create the audio engine that plays gameplay sounds.</span></span>

<span data-ttu-id="b2716-176">Zwischen der Arbeit mit der [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908)-Schnittstelle in einer UWP-App und der Arbeit mit einer Desktop-App gibt es zwei Unterschiede.</span><span class="sxs-lookup"><span data-stu-id="b2716-176">How to work with the [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908) interface in a UWP app differs from a desktop app in two ways.</span></span> <span data-ttu-id="b2716-177">Erstens ist es nicht erforderlich, [CoInitializeEx](https://msdn.microsoft.com/library/windows/desktop/ms695279) vor dem Aufrufen von [XAudio2Create](https://msdn.microsoft.com/library/windows/desktop/ee419212) aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="b2716-177">First, you don't have to call [CoInitializeEx](https://msdn.microsoft.com/library/windows/desktop/ms695279) before you call [XAudio2Create](https://msdn.microsoft.com/library/windows/desktop/ee419212).</span></span> <span data-ttu-id="b2716-178">Außerdem unterstützt **IXAudio2** die Geräteaufzählung nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="b2716-178">In addition, **IXAudio2** no longer supports device enumeration.</span></span> <span data-ttu-id="b2716-179">Weitere Informationen zum Aufzählen von Audiogeräten finden Sie unter [Enumerieren von Geräten](https://msdn.microsoft.com/library/windows/apps/hh464977).</span><span class="sxs-lookup"><span data-stu-id="b2716-179">For information about how to enumerate audio devices, see [Enumerating devices](https://msdn.microsoft.com/library/windows/apps/hh464977).</span></span>

### <a name="creating-the-mastering-voices"></a><span data-ttu-id="b2716-180">Erstellen der Masterstimmen</span><span class="sxs-lookup"><span data-stu-id="b2716-180">Creating the mastering voices</span></span>

<span data-ttu-id="b2716-181">Das folgende Beispiel zeigt, wie die **Audio::CreateResources**-Methode mithilfe der [IXAudio2::CreateMasteringVoice](https://msdn.microsoft.com/library/windows/desktop/hh405048)-Methode die Masterstimme für die Hintergrundmusik erstellt.</span><span class="sxs-lookup"><span data-stu-id="b2716-181">The following example shows how the **Audio::CreateResources** method creates the mastering voice for the background music using the [IXAudio2::CreateMasteringVoice](https://msdn.microsoft.com/library/windows/desktop/hh405048) method.</span></span> <span data-ttu-id="b2716-182">In diesem Beispiel ist **m\_musicMasteringVoice** ein [IXAudio2MasteringVoice](https://msdn.microsoft.com/library/windows/desktop/ee415912)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b2716-182">In this example, **m\_musicMasteringVoice** is an [IXAudio2MasteringVoice](https://msdn.microsoft.com/library/windows/desktop/ee415912) object.</span></span> <span data-ttu-id="b2716-183">Wir verwenden zwei Eingabekanäle, um die Logik für den Halleffekt zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="b2716-183">We specify two input channels; this simplifies the logic for the reverb effect.</span></span> 

<span data-ttu-id="b2716-184">Wir geben 48000 als Eingabebeispielrate an.</span><span class="sxs-lookup"><span data-stu-id="b2716-184">We specify 48000 as the input sample rate.</span></span> <span data-ttu-id="b2716-185">Diese Abtastrate wurde ausgewählt, da sie ein ausgewogenes Verhältnis von Audioqualität und Umfang der erforderlichen CPU-Verarbeitung darstellt.</span><span class="sxs-lookup"><span data-stu-id="b2716-185">We chose this sample rate because it represented a balance between audio quality and the amount of required CPU processing.</span></span> <span data-ttu-id="b2716-186">Eine höhere Abtastrate würde mehr CPU-Verarbeitung erfordern, ohne eine merkliche Qualitätssteigerung zu bewirken.</span><span class="sxs-lookup"><span data-stu-id="b2716-186">A greater sample rate would have required more CPU processing without having a noticeable quality benefit.</span></span> 

<span data-ttu-id="b2716-187">Wir geben danach **AudioCategory\_GameMedia** als Audiostreamkategorie an, damit Benutzer bei der Verwendung des Spiels Musik aus einer anderen Anwendung hören können.</span><span class="sxs-lookup"><span data-stu-id="b2716-187">Finally, we specify **AudioCategory_GameMedia** as the audio stream category so that users can listen to music from a different application as they play the game.</span></span> <span data-ttu-id="b2716-188">Bei der Wiedergabe aus einer Musik-App schaltet Windows alle mit der Option **AudioCategory\_GameMedia** erstellten Stimmen stumm.</span><span class="sxs-lookup"><span data-stu-id="b2716-188">When a music app is playing, Windows mutes any voices that are created by the **AudioCategory\_GameMedia** option.</span></span> <span data-ttu-id="b2716-189">Der Benutzer hört dennoch die Sounds im Spiel, da diese mit der Option **AudioCategory\_GameEffects** erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="b2716-189">The user still hears gameplay sounds because they are created by the **AudioCategory\_GameEffects** option.</span></span> <span data-ttu-id="b2716-190">Weitere Informationen zu Audiokategorien finden Sie unter [AUDIO\_STREAM\_CATEGORY](https://msdn.microsoft.com/library/windows/desktop/hh404178).</span><span class="sxs-lookup"><span data-stu-id="b2716-190">For more info about audio categories, see [AUDIO\_STREAM\_CATEGORY](https://msdn.microsoft.com/library/windows/desktop/hh404178).</span></span>

```cpp
// This sample plays the equivalent of background music, which we tag on the  
// mastering voice as AudioCategory_GameMedia. In ordinary usage, if we were  
// playing the music track with no effects, we could route it entirely through 
// Media Foundation. Here, we are using XAudio2 to apply a reverb effect to the 
// music, so we use Media Foundation to decode the data then we feed it through 
// the XAudio2 pipeline as a separate Mastering Voice, so that we can tag it 
// as Game Media. We default the mastering voice to 2 channels to simplify  
// the reverb logic.
DX::ThrowIfFailed(
    m_musicEngine->CreateMasteringVoice(
        &m_musicMasteringVoice,
        2,
        48000,
        0,
        nullptr,
        nullptr,
        AudioCategory_GameMedia
        )
);
```

<span data-ttu-id="b2716-191">Die **Audio::CreateResources**-Methode führt einen ähnlichen Schritt aus, um die Masterstimme für die Spielsounds zu erstellen. Allerdings wird dabei der Standardwert **AudioCategory\_GameEffects** für den *StreamCategory*-Parameter angegeben.</span><span class="sxs-lookup"><span data-stu-id="b2716-191">The **Audio::CreateResources** method performs a similar step to create the mastering voice for the gameplay sounds, except that it specifies **AudioCategory\_GameEffects** for the *StreamCategory* parameter, which is the default.</span></span>

### <a name="creating-the-reverb-effect"></a><span data-ttu-id="b2716-192">Erstellen des Halleffekts</span><span class="sxs-lookup"><span data-stu-id="b2716-192">Creating the reverb effect</span></span>

<span data-ttu-id="b2716-193">Sie können für jede Stimme mit XAudio2 Effektsequenzen erstellen, die Audio verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="b2716-193">For each voice, you can use XAudio2 to create sequences of effects that process audio.</span></span> <span data-ttu-id="b2716-194">Eine solche Sequenz wird als Effektkette bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="b2716-194">Such a sequence is known as an effect chain.</span></span> <span data-ttu-id="b2716-195">Verwenden Sie Effektketten, wenn Sie mindestens einen Effekt auf eine Stimme anwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="b2716-195">Use effect chains when you want to apply one or more effects to a voice.</span></span> <span data-ttu-id="b2716-196">Effektketten können destruktiv sein, d.h., jeder Effekt in der Kette kann den Audiopuffer überschreiben.</span><span class="sxs-lookup"><span data-stu-id="b2716-196">Effect chains can be destructive; that is, each effect in the chain can overwrite the audio buffer.</span></span> <span data-ttu-id="b2716-197">Diese Eigenschaft ist wichtig, da XAudio2 nicht garantiert, dass Ausgabepuffer lautlos initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="b2716-197">This property is important because XAudio2 makes no guarantee that output buffers are initialized with silence.</span></span> <span data-ttu-id="b2716-198">Effektobjekte werden in XAudio2 durch plattformübergreifende Audioverarbeitungsobjekte (Audio Processing Object, XAPO) dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b2716-198">Effect objects are represented in XAudio2 by cross-platform audio processing objects (XAPO).</span></span> <span data-ttu-id="b2716-199">Weitere Informationen zu XAPO finden Sie in der [XAPO-Übersicht](https://msdn.microsoft.com/library/windows/desktop/ee415735).</span><span class="sxs-lookup"><span data-stu-id="b2716-199">For more information about XAPO, see [XAPO Overview](https://msdn.microsoft.com/library/windows/desktop/ee415735).</span></span>

<span data-ttu-id="b2716-200">Führen Sie beim Erstellen einer Effektkette die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="b2716-200">When you create an effect chain, follow these steps:</span></span>

1. <span data-ttu-id="b2716-201">Erstellen Sie das Effektobjekt.</span><span class="sxs-lookup"><span data-stu-id="b2716-201">Create the effect object.</span></span>

2. <span data-ttu-id="b2716-202">Füllen Sie eine [XAUDIO2\_EFFECT\_DESCRIPTOR](https://msdn.microsoft.com/library/windows/desktop/ee419236)-Struktur mit Effektdaten auf.</span><span class="sxs-lookup"><span data-stu-id="b2716-202">Populate an [XAUDIO2\_EFFECT\_DESCRIPTOR](https://msdn.microsoft.com/library/windows/desktop/ee419236) structure with effect data.</span></span>

3. <span data-ttu-id="b2716-203">Füllen Sie eine [XAUDIO2\_EFFECT\_CHAIN](https://msdn.microsoft.com/library/windows/desktop/ee419235)-Struktur mit Effektdaten auf.</span><span class="sxs-lookup"><span data-stu-id="b2716-203">Populate an [XAUDIO2\_EFFECT\_CHAIN](https://msdn.microsoft.com/library/windows/desktop/ee419235) structure with data.</span></span>

4. <span data-ttu-id="b2716-204">Wenden Sie die Effektkette auf eine Stimme an.</span><span class="sxs-lookup"><span data-stu-id="b2716-204">Apply the effect chain to a voice.</span></span>

5. <span data-ttu-id="b2716-205">Füllen Sie eine Effektparameterstruktur auf und wenden Sie sie auf den Effekt an.</span><span class="sxs-lookup"><span data-stu-id="b2716-205">Populate an effect parameter structure and apply it to the effect.</span></span>

6. <span data-ttu-id="b2716-206">Deaktivieren oder aktivieren Sie den Effekt nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="b2716-206">Disable or enable the effect whenever appropriate.</span></span>

<span data-ttu-id="b2716-207">Die **Audio**-Klasse definiert die **CreateReverb**-Methode, um die Effektkette zu erstellen, die den Halleffekt implementiert.</span><span class="sxs-lookup"><span data-stu-id="b2716-207">The **Audio** class defines the **CreateReverb** method to create the effect chain that implements reverb.</span></span> <span data-ttu-id="b2716-208">Diese Methode ruft die [XAudio2CreateReverb](https://msdn.microsoft.com/library/windows/desktop/ee419213)-Methode auf, um ein **ComPtr&lt;IUnknown&gt;**-Objekt, **soundEffectXAPO** zu erstellen, das als Submixstimme für den Halleffekt fungiert.</span><span class="sxs-lookup"><span data-stu-id="b2716-208">This method calls the [XAudio2CreateReverb](https://msdn.microsoft.com/library/windows/desktop/ee419213) method to create a **ComPtr&lt;IUnknown&gt;** object, **soundEffectXAPO**, which acts as the submix voice for the reverb effect.</span></span>

```cpp
Microsoft::WRL::ComPtr<IUnknown> soundEffectXAPO;

DX::ThrowIfFailed(
    XAudio2CreateReverb(&soundEffectXAPO)
    );
```

<span data-ttu-id="b2716-209">Die [XAUDIO2\_EFFECT\_DESCRIPTOR](https://msdn.microsoft.com/library/windows/desktop/ee419236)-Struktur enthält Informationen zu einem XAPO, das in einer Effektkette verwendet werden soll, zum Beispiel die Zielanzahl der Ausgabekanäle.</span><span class="sxs-lookup"><span data-stu-id="b2716-209">The [XAUDIO2\_EFFECT\_DESCRIPTOR](https://msdn.microsoft.com/library/windows/desktop/ee419236) structure contains information about an XAPO for use in an effect chain, for example, the target number of output channels.</span></span> <span data-ttu-id="b2716-210">Die **Audio::CreateReverb**-Methode erstellt ein **XAUDIO2\_EFFECT\_DESCRIPTOR**-Objekt, , **soundEffectdescriptor**, das auf den deaktivierten Zustand festgelegt wird, verwendet zwei Ausgabekanäle und verweist auf das **soundEffectXAPO** für den Halleffekt.</span><span class="sxs-lookup"><span data-stu-id="b2716-210">The **Audio::CreateReverb** method creates an **XAUDIO2\_EFFECT\_DESCRIPTOR** object, **soundEffectdescriptor**, that is set to the disabled state, uses two output channels, and references **soundEffectXAPO** for the reverb effect.</span></span> <span data-ttu-id="b2716-211">**soundEffectdescriptor** beginnt mit dem deaktivierten Zustand, da das Spiel Parameter festlegen muss, bevor der Effekt mit dem Ändern der Spielsounds beginnt.</span><span class="sxs-lookup"><span data-stu-id="b2716-211">**soundEffectdescriptor** starts in the disabled state because the game must set parameters before the effect starts modifying game sounds.</span></span> <span data-ttu-id="b2716-212">Marble Maze verwendet zwei Ausgabekanäle, um die Logik für den Halleffekt zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="b2716-212">Marble Maze uses two output channels to simplify the logic for the reverb effect.</span></span>

```cpp
soundEffectdescriptor.InitialState = false;
soundEffectdescriptor.OutputChannels = 2;
soundEffectdescriptor.pEffect = soundEffectXAPO.Get();
```

<span data-ttu-id="b2716-213">Wenn Ihre Effektkette mehrere Effekte enthält, benötigen Sie für jeden Effekt ein Objekt.</span><span class="sxs-lookup"><span data-stu-id="b2716-213">If your effect chain has multiple effects, each effect requires an object.</span></span> <span data-ttu-id="b2716-214">Die [XAUDIO2\_EFFECT\_CHAIN](https://msdn.microsoft.com/library/windows/desktop/ee419235)-Struktur enthält das Array der am Effekt beteiligten [XAUDIO2\_EFFECT\_DESCRIPTOR](https://msdn.microsoft.com/library/windows/desktop/ee419236)-Objekte.</span><span class="sxs-lookup"><span data-stu-id="b2716-214">The [XAUDIO2\_EFFECT\_CHAIN](https://msdn.microsoft.com/library/windows/desktop/ee419235) structure holds the array of [XAUDIO2\_EFFECT\_DESCRIPTOR](https://msdn.microsoft.com/library/windows/desktop/ee419236) objects that participate in the effect.</span></span> <span data-ttu-id="b2716-215">Das folgende Beispiel zeigt, wie die **Audio::CreateReverb**-Methode den einen Effekt für die Implementierung des Halleffekts angibt.</span><span class="sxs-lookup"><span data-stu-id="b2716-215">The following example shows how the **Audio::CreateReverb** method specifies the one effect to implement reverb.</span></span>

```cpp
XAUDIO2_EFFECT_CHAIN soundEffectChain;

// ...

soundEffectChain.EffectCount = 1;
soundEffectChain.pEffectDescriptors = &soundEffectdescriptor;
```

<span data-ttu-id="b2716-216">Die **Audio::CreateReverb**-Methode ruft die [IXAudio2::CreateSubmixVoice](https://msdn.microsoft.com/library/windows/desktop/ee418608)-Methode auf, um die Submixstimme für den Effekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b2716-216">The **Audio::CreateReverb** method calls the [IXAudio2::CreateSubmixVoice](https://msdn.microsoft.com/library/windows/desktop/ee418608) method to create the submix voice for the effect.</span></span> <span data-ttu-id="b2716-217">Sie gibt das [XAUDIO2\_EFFECT\_CHAIN](https://msdn.microsoft.com/library/windows/desktop/ee419235)-Objekt, **soundEffectChain**, für den *pEffectChain*-Parameter an, um die Effektkette der Stimme zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="b2716-217">It specifies the [XAUDIO2\_EFFECT\_CHAIN](https://msdn.microsoft.com/library/windows/desktop/ee419235) object, **soundEffectChain**, for the *pEffectChain* parameter to associate the effect chain with the voice.</span></span> <span data-ttu-id="b2716-218">Außerdem gibt Marble Maze zwei Ausgabekanäle und eine Abtastrate von 48 Kilohertz an.</span><span class="sxs-lookup"><span data-stu-id="b2716-218">Marble Maze also specifies two output channels and a sample rate of 48 kilohertz.</span></span>

```cpp
DX::ThrowIfFailed(
    engine->CreateSubmixVoice(newSubmix, 2, 48000, 0, 0, nullptr, &soundEffectChain)
    );
```

> [!TIP]
> <span data-ttu-id="b2716-219">Verwenden Sie die [IXAudio2Voice::SetEffectChain](https://msdn.microsoft.com/library/windows/desktop/ee418594)-Methode, wenn Sie eine vorhandene Effektkette an eine vorhandene Submixstimme anfügen oder die aktuelle Effektkette ersetzen möchten.</span><span class="sxs-lookup"><span data-stu-id="b2716-219">If you want to attach an existing effect chain to an existing submix voice, or you want to replace the current effect chain, use the [IXAudio2Voice::SetEffectChain](https://msdn.microsoft.com/library/windows/desktop/ee418594) method.</span></span>

<span data-ttu-id="b2716-220">Die **Audio::CreateReverb**-Methode ruft [IXAudio2Voice::SetEffectParameters](https://msdn.microsoft.com/library/windows/desktop/ee418595) auf, um zusätzliche dem Effekt zugeordnete Parameter festzulegen.</span><span class="sxs-lookup"><span data-stu-id="b2716-220">The **Audio::CreateReverb** method calls [IXAudio2Voice::SetEffectParameters](https://msdn.microsoft.com/library/windows/desktop/ee418595) to set additional parameters that are associated with the effect.</span></span> <span data-ttu-id="b2716-221">Diese Methode akzeptiert eine für den Effekt spezifische Parameterstruktur.</span><span class="sxs-lookup"><span data-stu-id="b2716-221">This method takes a parameter structure that is specific to the effect.</span></span> <span data-ttu-id="b2716-222">Ein [XAUDIO2FX\_REVERB\_PARAMETERS](https://msdn.microsoft.com/library/windows/desktop/ee419224)-Objekt, **m_reverbParametersSmall**, das die Effektparameter für den Halleffekt enthält, wird in der **Audio::Initialize**-Methode initialisiert, da alle Halleffekte die gleichen Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="b2716-222">An [XAUDIO2FX\_REVERB\_PARAMETERS](https://msdn.microsoft.com/library/windows/desktop/ee419224) object, **m_reverbParametersSmall**, which contains the effect parameters for reverb, is initialized in the **Audio::Initialize** method because every reverb effect shares the same parameters.</span></span> <span data-ttu-id="b2716-223">Das folgende Beispiel zeigt, wie die **Audio::Initialize**-Methode die Hallparameter für Nahfeld-Halleffekte initialisiert.</span><span class="sxs-lookup"><span data-stu-id="b2716-223">The following example shows how the **Audio::Initialize** method initializes the reverb parameters for near-field reverb.</span></span>

```cpp
m_reverbParametersSmall.ReflectionsDelay = XAUDIO2FX_REVERB_DEFAULT_REFLECTIONS_DELAY;
m_reverbParametersSmall.ReverbDelay = XAUDIO2FX_REVERB_DEFAULT_REVERB_DELAY;
m_reverbParametersSmall.RearDelay = XAUDIO2FX_REVERB_DEFAULT_REAR_DELAY;
m_reverbParametersSmall.PositionLeft = XAUDIO2FX_REVERB_DEFAULT_POSITION;
m_reverbParametersSmall.PositionRight = XAUDIO2FX_REVERB_DEFAULT_POSITION;
m_reverbParametersSmall.PositionMatrixLeft = XAUDIO2FX_REVERB_DEFAULT_POSITION_MATRIX;
m_reverbParametersSmall.PositionMatrixRight = XAUDIO2FX_REVERB_DEFAULT_POSITION_MATRIX;
m_reverbParametersSmall.EarlyDiffusion = 4;
m_reverbParametersSmall.LateDiffusion = 15;
m_reverbParametersSmall.LowEQGain = XAUDIO2FX_REVERB_DEFAULT_LOW_EQ_GAIN;
m_reverbParametersSmall.LowEQCutoff = XAUDIO2FX_REVERB_DEFAULT_LOW_EQ_CUTOFF;
m_reverbParametersSmall.HighEQGain = XAUDIO2FX_REVERB_DEFAULT_HIGH_EQ_GAIN;
m_reverbParametersSmall.HighEQCutoff = XAUDIO2FX_REVERB_DEFAULT_HIGH_EQ_CUTOFF;
m_reverbParametersSmall.RoomFilterFreq = XAUDIO2FX_REVERB_DEFAULT_ROOM_FILTER_FREQ;
m_reverbParametersSmall.RoomFilterMain = XAUDIO2FX_REVERB_DEFAULT_ROOM_FILTER_MAIN;
m_reverbParametersSmall.RoomFilterHF = XAUDIO2FX_REVERB_DEFAULT_ROOM_FILTER_HF;
m_reverbParametersSmall.ReflectionsGain = XAUDIO2FX_REVERB_DEFAULT_REFLECTIONS_GAIN;
m_reverbParametersSmall.ReverbGain = XAUDIO2FX_REVERB_DEFAULT_REVERB_GAIN;
m_reverbParametersSmall.DecayTime = XAUDIO2FX_REVERB_DEFAULT_DECAY_TIME;
m_reverbParametersSmall.Density = XAUDIO2FX_REVERB_DEFAULT_DENSITY;
m_reverbParametersSmall.RoomSize = XAUDIO2FX_REVERB_DEFAULT_ROOM_SIZE;
m_reverbParametersSmall.WetDryMix = XAUDIO2FX_REVERB_DEFAULT_WET_DRY_MIX;
m_reverbParametersSmall.DisableLateField = TRUE;
```

<span data-ttu-id="b2716-224">Dieses Beispiel verwendet die Standardwerte für die meisten Hallparameter, legt aber **DisableLateField** auf TRUE fest, um den Nahfeld-Halleffekt anzugeben, **EarlyDiffusion** auf 4, um flache Oberflächen in der Nähe zu simulieren, und **LateDiffusion** auf 15, um sehr diffuse entfernte Oberflächen zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="b2716-224">This example uses the default values for most of the reverb parameters, but it sets **DisableLateField** to TRUE to specify near-field reverb, **EarlyDiffusion** to 4 to simulate flat near surfaces, and **LateDiffusion** to 15 to simulate very diffuse distant surfaces.</span></span> <span data-ttu-id="b2716-225">Flache Oberflächen in der Nähe verursachen Echos, die Sie schneller und lauter hören. Diffuse entfernte Oberflächen verursachen leisere und nicht so schnell hörbare Echos.</span><span class="sxs-lookup"><span data-stu-id="b2716-225">Flat near surfaces cause echoes to reach you more quickly and loudly; diffuse distant surfaces cause echoes to be quieter and reach you more slowly.</span></span> <span data-ttu-id="b2716-226">Sie können mit den Halleffektwerten experimentieren, um in Ihrem Spiel den gewünschten Effekt zu erzielen, oder die **ReverbConvertI3DL2ToNative**-Methode verwenden, um I3DL2-Parameter (Interactive 3D Audio Rendering Guidelines Level 2.0) nach Branchenstandard zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b2716-226">You can experiment with reverb values to get the desired effect in your game or use the **ReverbConvertI3DL2ToNative** method to use industry-standard I3DL2 (Interactive 3D Audio Rendering Guidelines Level 2.0) parameters.</span></span>

<span data-ttu-id="b2716-227">Das folgende Beispiel zeigt, wie **Audio::CreateReverb** die Hallparameter festlegt.</span><span class="sxs-lookup"><span data-stu-id="b2716-227">The following example shows how **Audio::CreateReverb** sets the reverb parameters.</span></span> <span data-ttu-id="b2716-228">**NewSubmix** ist ein [IXAudio2SubmixVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2submixvoice.ixaudio2submixvoice)\*\*-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b2716-228">**newSubmix** is an [IXAudio2SubmixVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2submixvoice.ixaudio2submixvoice)\*\* object.</span></span> <span data-ttu-id="b2716-229">Der **parameters**-Parameter ist ein [XAUDIO2FX\_REVERB\_PARAMETERS](https://msdn.microsoft.com/library/windows/desktop/ee419224)\*-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b2716-229">**parameters** is an [XAUDIO2FX\_REVERB\_PARAMETERS](https://msdn.microsoft.com/library/windows/desktop/ee419224)\* object.</span></span>

```cpp
DX::ThrowIfFailed(
    (*newSubmix)->SetEffectParameters(0, parameters, sizeof(m_reverbParametersSmall))
    );
```

<span data-ttu-id="b2716-230">Die **Audio::CreateReverb**-Methode aktiviert zum Schluss den Effekt mithilfe von [IXAudio2Voice::EnableEffect](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2voice.ixaudio2voice.enableeffect) fest, wenn das **enableEffect**-Kennzeichen festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="b2716-230">The **Audio::CreateReverb** method finishes by enabling the effect using [IXAudio2Voice::EnableEffect](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2voice.ixaudio2voice.enableeffect) if the **enableEffect** flag is set.</span></span> <span data-ttu-id="b2716-231">Es legt ebenfalls die Lautstärke mit [IXAudio2Voice::SetVolume](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2voice.ixaudio2voice.setvolume) und unter Verwendung der Matrix [IXAudio2Voice::SetOutputMatrix](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2voice.ixaudio2voice.setoutputmatrix) fest.</span><span class="sxs-lookup"><span data-stu-id="b2716-231">It also sets its volume using [IXAudio2Voice::SetVolume](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2voice.ixaudio2voice.setvolume) and output matrix using [IXAudio2Voice::SetOutputMatrix](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2voice.ixaudio2voice.setoutputmatrix).</span></span> <span data-ttu-id="b2716-232">Mit diesem Teil wird die volle Lautstärke (1.0) festgelegt und dann die Lautstärkematrix so angegeben, dass die linke und die rechte Eingabe sowie der linke und der rechte Ausgabelautsprecher stumm sind.</span><span class="sxs-lookup"><span data-stu-id="b2716-232">This part sets the volume to full (1.0) and then specifies the volume matrix to be silence for both left and right inputs and left and right output speakers.</span></span> <span data-ttu-id="b2716-233">Dies geschieht, da später anderer Code zwischen den beiden Halleffekten überblendet (und dabei den Übergang von der Nähe zu einer Wand zu einem großen Raum simuliert) oder bei Bedarf beide Halleffekte stummschaltet.</span><span class="sxs-lookup"><span data-stu-id="b2716-233">We do this because other code later cross-fades between the two reverbs (simulating the transition from being near a wall to being in a large room), or mutes both reverbs if required.</span></span> <span data-ttu-id="b2716-234">Wenn die Stummschaltung des Hallpfads später aufgehoben wird, legt das Spiel die Matrix {1.0f, 0.0f, 0.0f, 1.0f} fest, um die linke Hallausgabe an die linke Eingabe der Masterstimme und die rechte Hallausgabe an die rechte Eingabe der Masterstimme weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="b2716-234">When the reverb path is later unmuted, the game sets a matrix of {1.0f, 0.0f, 0.0f, 1.0f} to route left reverb output to the left input of the mastering voice and right reverb output to the right input of the mastering voice.</span></span>

```cpp
if (enableEffect)
{
    DX::ThrowIfFailed(
        (*newSubmix)->EnableEffect(0)
        );    
}

DX::ThrowIfFailed(
    (*newSubmix)->SetVolume (1.0f)
    );

float outputMatrix[4] = {0, 0, 0, 0};
DX::ThrowIfFailed(
    (*newSubmix)->SetOutputMatrix(masteringVoice, 2, 2, outputMatrix)
    );
```

<span data-ttu-id="b2716-235">Marble Maze ruft die **Audio::CreateReverb**-Methode viermal auf: zweimal für die Hintergrundmusik und zweimal für die Spielsounds.</span><span class="sxs-lookup"><span data-stu-id="b2716-235">Marble Maze calls the **Audio::CreateReverb** method four times: two times for the background music and two times for the gameplay sounds.</span></span> <span data-ttu-id="b2716-236">Das folgende Beispiel zeigt, wie Marble Maze die **CreateReverb**-Methode für die Hintergrundmusik aufruft.</span><span class="sxs-lookup"><span data-stu-id="b2716-236">The following shows how Marble Maze calls the **CreateReverb** method for the background music.</span></span>

```cpp
CreateReverb(
    m_musicEngine, 
    m_musicMasteringVoice, 
    &m_reverbParametersSmall, 
    &m_musicReverbVoiceSmallRoom, 
    true
    );
CreateReverb(
    m_musicEngine, 
    m_musicMasteringVoice, 
    &m_reverbParametersLarge, 
    &m_musicReverbVoiceLargeRoom, 
    true
    );
```

<span data-ttu-id="b2716-237">Eine Liste der möglichen Quellen für Effekte, die Sie mit XAudio2 verwenden können, finden Sie unter [XAudio2-Audioeffekte](https://msdn.microsoft.com/library/windows/desktop/ee415756).</span><span class="sxs-lookup"><span data-stu-id="b2716-237">For a list of possible sources of effects for use with XAudio2, see [XAudio2 Audio Effects](https://msdn.microsoft.com/library/windows/desktop/ee415756).</span></span>

### <a name="loading-audio-data-from-file"></a><span data-ttu-id="b2716-238">Laden von Audiodaten aus einer Datei</span><span class="sxs-lookup"><span data-stu-id="b2716-238">Loading audio data from file</span></span>

<span data-ttu-id="b2716-239">Marble Maze definiert die **MediaStreamer**-Klasse, die Media Foundation zum Laden von Audioressourcen aus den Dateien verwendet.</span><span class="sxs-lookup"><span data-stu-id="b2716-239">Marble Maze defines the **MediaStreamer** class, which uses Media Foundation to load audio resources from files.</span></span> <span data-ttu-id="b2716-240">Marble Maze verwendet zum Laden jeder Audiodatei ein **MediaStreamer**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b2716-240">Marble Maze uses one **MediaStreamer** object to load each audio file.</span></span>

<span data-ttu-id="b2716-241">Marble Maze ruft die **MediaStreamer::Initialize**-Methode auf, um die einzelnen Audiostreams zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="b2716-241">Marble Maze calls the **MediaStreamer::Initialize** method to initialize each audio stream.</span></span> <span data-ttu-id="b2716-242">So ruft die **Audio::CreateResources**-Methode **MediaStreamer::Initialize** auf, um den Audiostream für die Hintergrundmusik zu initialisieren:</span><span class="sxs-lookup"><span data-stu-id="b2716-242">Here's how the **Audio::CreateResources** method calls **MediaStreamer::Initialize** to initialize the audio stream for the background music:</span></span>

```cpp
// Media Foundation is a convenient way to get both file I/O and format decode for 
// audio assets. You can replace the streamer in this sample with your own file I/O 
// and decode routines.
m_musicStreamer.Initialize(L"Media\\Audio\\background.wma");
```

<span data-ttu-id="b2716-243">Die **MediaStreamer::Initialize**-Methode ruft zunächst die [MFStartup](https://msdn.microsoft.com/library/windows/desktop/ms702238)-Funktion auf, um Media Foundation zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="b2716-243">The **MediaStreamer::Initialize** method starts by calling the [MFStartup](https://msdn.microsoft.com/library/windows/desktop/ms702238) method to initialize Media Foundation.</span></span> <span data-ttu-id="b2716-244">**MF_VERSION** ist eine im **mfapi.h** definierte Makro, die wir als die empfohlene Version von Media Foundation verwenden.</span><span class="sxs-lookup"><span data-stu-id="b2716-244">**MF_VERSION** is a macro defined in **mfapi.h**, and is what we specify as the version of Media Foundation to use.</span></span>

```cpp
DX::ThrowIfFailed(
    MFStartup(MF_VERSION)
    );
```

<span data-ttu-id="b2716-245">**MediaStreamer::Initialize** ruft dann [MFCreateSourceReaderFromURL](https://msdn.microsoft.com/library/windows/desktop/dd388110) auf, um ein [IMFSourceReader](https://msdn.microsoft.com/library/windows/desktop/dd374655)-Objekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b2716-245">**MediaStreamer::Initialize** then calls [MFCreateSourceReaderFromURL](https://msdn.microsoft.com/library/windows/desktop/dd388110) to create an [IMFSourceReader](https://msdn.microsoft.com/library/windows/desktop/dd374655) object.</span></span> <span data-ttu-id="b2716-246">Ein **IMFSourceReader**-Objekt, **m_reader**, liest Mediendaten aus der Datei, die mit **url** angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="b2716-246">An **IMFSourceReader** object, **m_reader**, reads media data from the file that is specified by **url**.</span></span>

```cpp
DX::ThrowIfFailed(
    MFCreateSourceReaderFromURL(url, nullptr, &m_reader)
    );
```

<span data-ttu-id="b2716-247">Dann erstellt die **MediaStreamer::Initialize**-Methode ein [IMFMediaType](https://msdn.microsoft.com/library/windows/desktop/ms704850)-Objekt mithilfe von [MFCreateMediaType](https://msdn.microsoft.com/library/windows/desktop/ms693861), um das Format des Audiostreams zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="b2716-247">The **MediaStreamer::Initialize** method then creates an [IMFMediaType](https://msdn.microsoft.com/library/windows/desktop/ms704850) object using [MFCreateMediaType](https://msdn.microsoft.com/library/windows/desktop/ms693861) to describe the format of the audio stream.</span></span> <span data-ttu-id="b2716-248">Ein Audioformat hat zwei Typen: einen Haupttyp und einen Untertyp.</span><span class="sxs-lookup"><span data-stu-id="b2716-248">An audio format has two types: a major type and a subtype.</span></span> <span data-ttu-id="b2716-249">Der Haupttyp definiert das allgemeine Format der Medien, zum Beispiel Video, Audio, Skript usw.</span><span class="sxs-lookup"><span data-stu-id="b2716-249">The major type defines the overall format of the media, such as video, audio, script, and so on.</span></span> <span data-ttu-id="b2716-250">Der Untertyp definiert das Format, zum Beispiel PCM, ADPCM oder WMA.</span><span class="sxs-lookup"><span data-stu-id="b2716-250">The subtype defines the format, such as PCM, ADPCM, or WMA.</span></span>

<span data-ttu-id="b2716-251">Die **MediaStreamer::Initialize**-Methode verwendet die [IMFAttributes::SetGUID](https://msdn.microsoft.com/library/windows/desktop/bb970530)-Methode, um den Haupttyp ([MF_MT_MAJOR_TYPE](https://msdn.microsoft.com/library/windows/desktop/ms702272)) als Audio (**MFMediaType\_Audio**) und den Untertyp ([MF_MT_SUBTYPE](https://msdn.microsoft.com/library/windows/desktop/ms700208)) als nicht komprimiertes PCM-Audio (**MFAudioFormat\_PCM**) anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b2716-251">The **MediaStreamer::Initialize** method uses the [IMFAttributes::SetGUID](https://msdn.microsoft.com/library/windows/desktop/bb970530) method to specify the major type ([MF_MT_MAJOR_TYPE](https://msdn.microsoft.com/library/windows/desktop/ms702272)) as audio (**MFMediaType\_Audio**) and the minor type ([MF_MT_SUBTYPE](https://msdn.microsoft.com/library/windows/desktop/ms700208)) as uncompressed PCM audio (**MFAudioFormat\_PCM**).</span></span> <span data-ttu-id="b2716-252">**MF_MT_MAJOR_TYPE** und **MF_MT_SUBTYPE** sind [Media Foundation-Attribute](https://msdn.microsoft.com/library/windows/desktop/ms696989).</span><span class="sxs-lookup"><span data-stu-id="b2716-252">**MF_MT_MAJOR_TYPE** and **MF_MT_SUBTYPE** are [Media Foundation Attributes](https://msdn.microsoft.com/library/windows/desktop/ms696989).</span></span> <span data-ttu-id="b2716-253">**MFMediaType_Audio** und **MFAudioFormat_PCM** sind Typ- und Untertyp-GUIDs; Weitere Informationen finden Sie unter [Audio-Medientypen](https://msdn.microsoft.com/library/windows/desktop/bb530108).</span><span class="sxs-lookup"><span data-stu-id="b2716-253">**MFMediaType_Audio** and **MFAudioFormat_PCM** are type and subtype GUIDs; see [Audio Media Types](https://msdn.microsoft.com/library/windows/desktop/bb530108) for more information.</span></span> <span data-ttu-id="b2716-254">Die [IMFSourceReader::SetCurrentMediaType](https://msdn.microsoft.com/library/windows/desktop/dd374667)-Methode ordnet den Medientyp dem StreamReader zu.</span><span class="sxs-lookup"><span data-stu-id="b2716-254">The [IMFSourceReader::SetCurrentMediaType](https://msdn.microsoft.com/library/windows/desktop/dd374667) method associates the media type with the stream reader.</span></span>

```cpp
// Set the decoded output format as PCM. 
// XAudio2 on Windows can process PCM and ADPCM-encoded buffers. 
// When this sample uses Media Foundation, it always decodes into PCM.

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
    m_reader->SetCurrentMediaType(MF_SOURCE_READER_FIRST_AUDIO_STREAM, 0, mediaType.Get())
    );
```

<span data-ttu-id="b2716-255">Die **MediaStreamer::Initialize**-Methode ruft dann das vollständige Ausgabemedienformat von Media Foundation mithilfe von [IMFSourceReader::GetCurrentMediaType](https://msdn.microsoft.com/library/windows/desktop/dd374660) ab und ruft die [MFCreateWaveFormatExFromMFMediaType](https://msdn.microsoft.com/library/windows/desktop/ms702177)-Funktion auf, um den Media Foundation-Audiomedientyp in eine [WAVEFORMATEX](https://msdn.microsoft.com/library/windows/hardware/ff538799)-Struktur zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="b2716-255">The **MediaStreamer::Initialize** method then obtains the complete output media format from Media Foundation using [IMFSourceReader::GetCurrentMediaType](https://msdn.microsoft.com/library/windows/desktop/dd374660) and calls the [MFCreateWaveFormatExFromMFMediaType](https://msdn.microsoft.com/library/windows/desktop/ms702177) method to convert the Media Foundation audio media type to a [WAVEFORMATEX](https://msdn.microsoft.com/library/windows/hardware/ff538799) structure.</span></span> <span data-ttu-id="b2716-256">Die **WAVEFORMATEX**-Struktur definiert das Format von Waveform-Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="b2716-256">The **WAVEFORMATEX** structure defines the format of waveform-audio data.</span></span> <span data-ttu-id="b2716-257">Marble Maze erstellt mithilfe dieser Struktur die Quellstimmen und wendet den Tiefpassfilter auf den Sound für das Rollen der Murmel an.</span><span class="sxs-lookup"><span data-stu-id="b2716-257">Marble Maze uses this structure to create the source voices and to apply the low-pass filter to the marble rolling sound.</span></span>

```cpp
// Get the complete WAVEFORMAT from the Media Type.
DX::ThrowIfFailed(
    m_reader->GetCurrentMediaType(MF_SOURCE_READER_FIRST_AUDIO_STREAM, &outputMediaType)
    );

uint32 formatSize = 0;
WAVEFORMATEX* waveFormat;
DX::ThrowIfFailed(
    MFCreateWaveFormatExFromMFMediaType(outputMediaType.Get(), &waveFormat, &formatSize)
    );
CopyMemory(&m_waveFormat, waveFormat, sizeof(m_waveFormat));
CoTaskMemFree(waveFormat);
```

> [!IMPORTANT]
> <span data-ttu-id="b2716-258">Die [MFCreateWaveFormatExFromMFMediaType](https://msdn.microsoft.com/library/windows/desktop/ms702177)-Methode verwendet **CoTaskMemAlloc** zum Zuordnen des [WAVEFORMATEX](https://msdn.microsoft.com/library/windows/hardware/ff538799)-Objekts.</span><span class="sxs-lookup"><span data-stu-id="b2716-258">The [MFCreateWaveFormatExFromMFMediaType](https://msdn.microsoft.com/library/windows/desktop/ms702177) method uses **CoTaskMemAlloc** to allocate the [WAVEFORMATEX](https://msdn.microsoft.com/library/windows/hardware/ff538799) object.</span></span> <span data-ttu-id="b2716-259">Rufen Sie daher unbedingt **CoTaskMemFree** auf, wenn Sie dieses Objekt nicht mehr verwenden.</span><span class="sxs-lookup"><span data-stu-id="b2716-259">Therefore, make sure that you call **CoTaskMemFree** when you are finished using this object.</span></span>

 

<span data-ttu-id="b2716-260">Die **MediaStreamer::Initialize**-Methode wird beendet, indem die Länge des Streams **m\_maxStreamLengthInBytes**,“ in Byte berechnet wird.</span><span class="sxs-lookup"><span data-stu-id="b2716-260">The **MediaStreamer::Initialize** method finishes by computing the length of the stream, **m\_maxStreamLengthInBytes**, in bytes.</span></span> <span data-ttu-id="b2716-261">Dazu ruft sie die [IMFSourceReader::IMFSourceReader::GetPresentationAttribute](https://msdn.microsoft.com/library/windows/desktop/dd374662)-Methode auf, um die Dauer des Audiostreams in Einheiten von jeweils 100 Nanosekunden abzurufen, konvertiert die Dauer in Abschnitte und multipliziert dann diese Zahl mit der durchschnittlichen Datenübertragungsrate in Bytes pro Sekunde.</span><span class="sxs-lookup"><span data-stu-id="b2716-261">To do so, it calls the [IMFSourceReader::GetPresentationAttribute](https://msdn.microsoft.com/library/windows/desktop/dd374662) method to get the duration of the audio stream in 100-nanosecond units, converts the duration to sections, and then multiplies by the average data transfer rate in bytes per second.</span></span> <span data-ttu-id="b2716-262">Diesen Wert verwendet Marble Maze später, um den Puffer zuzuordnen, in dem sich die einzelnen Spielsounds befinden.</span><span class="sxs-lookup"><span data-stu-id="b2716-262">Marble Maze later uses this value to allocate the buffer that holds each gameplay sound.</span></span>

```cpp
// Get the total length of the stream, in bytes.
PROPVARIANT var;
DX::ThrowIfFailed(
    m_reader->
        GetPresentationAttribute(MF_SOURCE_READER_MEDIASOURCE, MF_PD_DURATION, &var)
    );

// duration is in 100ns units; convert to seconds, and round up
// to the nearest whole byte.
ULONGLONG duration = var.uhVal.QuadPart;
m_maxStreamLengthInBytes =
    static_cast<unsigned int>(
        ((duration * static_cast<ULONGLONG>(m_waveFormat.nAvgBytesPerSec)) + 10000000)
        / 10000000
        );
```

### <a name="creating-the-source-voices"></a><span data-ttu-id="b2716-263">Erstellen der Quellstimmen</span><span class="sxs-lookup"><span data-stu-id="b2716-263">Creating the source voices</span></span>

<span data-ttu-id="b2716-264">Marble Maze erstellt XAudio2-Quellstimmen für die Wiedergabe der einzelnen Spielsounds und der Musik in Quellstimmen.</span><span class="sxs-lookup"><span data-stu-id="b2716-264">Marble Maze creates XAudio2 source voices to play each of its game sounds and music in source voices.</span></span> <span data-ttu-id="b2716-265">Die **Audio**-Klasse definiert ein [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/ee415914)-Objekt für die Hintergrundmusik und ein Array mit **SoundEffectData**-Objekten für die Spielsounds.</span><span class="sxs-lookup"><span data-stu-id="b2716-265">The **Audio** class defines an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/ee415914) object for the background music and an array of **SoundEffectData** objects to hold the gameplay sounds.</span></span> <span data-ttu-id="b2716-266">Die **SoundEffectData**-Struktur enthält das **IXAudio2SourceVoice**-Objekt für einen Effekt und definiert außerdem andere Daten im Zusammenhang mit Effekten, beispielsweise den Audiopuffer.</span><span class="sxs-lookup"><span data-stu-id="b2716-266">The **SoundEffectData** structure holds the **IXAudio2SourceVoice** object for an effect and also defines other effect-related data, such as the audio buffer.</span></span> <span data-ttu-id="b2716-267">**Audio.h** definiert die **SoundEvent**-Enumeration.</span><span class="sxs-lookup"><span data-stu-id="b2716-267">**Audio.h** defines the **SoundEvent** enumeration.</span></span> <span data-ttu-id="b2716-268">Mithilfe dieser Enumeration identifiziert Marble Maze die einzelnen Sounds im Spiel.</span><span class="sxs-lookup"><span data-stu-id="b2716-268">Marble Maze uses this enumeration to identify each gameplay sound.</span></span> <span data-ttu-id="b2716-269">Außerdem verwendet die **Audio**-Klasse diese Enumeration zum Indizieren des Arrays mit **SoundEffectData**-Objekten.</span><span class="sxs-lookup"><span data-stu-id="b2716-269">The **Audio** class also uses this enumeration to index the array of **SoundEffectData** objects.</span></span>

```cpp
enum SoundEvent
{
    RollingEvent        = 0,
    FallingEvent        = 1,
    CollisionEvent      = 2,
    CheckpointEvent     = 3,
    MenuChangeEvent     = 4,
    MenuSelectedEvent   = 5,
    LastSoundEvent,
};
```

<span data-ttu-id="b2716-270">Die folgende Tabelle zeigt die Beziehung zwischen den einzelnen Werten, die Datei, in der sich die zugeordneten Sounddaten befinden, und eine kurze Beschreibung der einzelnen Sounds.</span><span class="sxs-lookup"><span data-stu-id="b2716-270">The following table shows the relationship between each of these values, the file that contains the associated sound data, and a brief description of what each sound represents.</span></span> <span data-ttu-id="b2716-271">Die Audiodateien befinden sich im Ordner **\\Media\\Audio**.</span><span class="sxs-lookup"><span data-stu-id="b2716-271">The audio files are located in the **\\Media\\Audio** folder.</span></span>

| <span data-ttu-id="b2716-272">SoundEvent-Wert</span><span class="sxs-lookup"><span data-stu-id="b2716-272">SoundEvent value</span></span>  | <span data-ttu-id="b2716-273">Dateiname</span><span class="sxs-lookup"><span data-stu-id="b2716-273">File name</span></span>      | <span data-ttu-id="b2716-274">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b2716-274">Description</span></span>                                              |
|-------------------|----------------|----------------------------------------------------------|
| <span data-ttu-id="b2716-275">RollingEvent</span><span class="sxs-lookup"><span data-stu-id="b2716-275">RollingEvent</span></span>      | <span data-ttu-id="b2716-276">MarbleRoll.wav</span><span class="sxs-lookup"><span data-stu-id="b2716-276">MarbleRoll.wav</span></span> | <span data-ttu-id="b2716-277">Wird wiedergegeben, wenn die Murmel rollt.</span><span class="sxs-lookup"><span data-stu-id="b2716-277">Played as the marble rolls.</span></span>                              |
| <span data-ttu-id="b2716-278">FallingEvent</span><span class="sxs-lookup"><span data-stu-id="b2716-278">FallingEvent</span></span>      | <span data-ttu-id="b2716-279">MarbleFall.wav</span><span class="sxs-lookup"><span data-stu-id="b2716-279">MarbleFall.wav</span></span> | <span data-ttu-id="b2716-280">Wird wiedergegeben, wenn die Murmel aus dem Labyrinth fällt.</span><span class="sxs-lookup"><span data-stu-id="b2716-280">Played when the marble falls off the maze.</span></span>               |
| <span data-ttu-id="b2716-281">CollisionEvent</span><span class="sxs-lookup"><span data-stu-id="b2716-281">CollisionEvent</span></span>    | <span data-ttu-id="b2716-282">MarbleHit.wav</span><span class="sxs-lookup"><span data-stu-id="b2716-282">MarbleHit.wav</span></span>  | <span data-ttu-id="b2716-283">Wird wiedergegeben, wenn die Murmel mit dem Labyrinth kollidiert.</span><span class="sxs-lookup"><span data-stu-id="b2716-283">Played when the marble collides with the maze.</span></span>           |
| <span data-ttu-id="b2716-284">CheckpointEvent</span><span class="sxs-lookup"><span data-stu-id="b2716-284">CheckpointEvent</span></span>   | <span data-ttu-id="b2716-285">Checkpoint.wav</span><span class="sxs-lookup"><span data-stu-id="b2716-285">Checkpoint.wav</span></span> | <span data-ttu-id="b2716-286">Wird wiedergegeben, wenn die Murmel über einen Prüfpunkt rollt.</span><span class="sxs-lookup"><span data-stu-id="b2716-286">Played when the marble passes over a checkpoint.</span></span>         |
| <span data-ttu-id="b2716-287">MenuChangeEvent</span><span class="sxs-lookup"><span data-stu-id="b2716-287">MenuChangeEvent</span></span>   | <span data-ttu-id="b2716-288">MenuChange.wav</span><span class="sxs-lookup"><span data-stu-id="b2716-288">MenuChange.wav</span></span> | <span data-ttu-id="b2716-289">Wird wiedergegeben, wenn der Benutzer das aktuelle Menüelement ändert.</span><span class="sxs-lookup"><span data-stu-id="b2716-289">Played when the user changes the current menu item.</span></span> |
| <span data-ttu-id="b2716-290">MenuSelectedEvent</span><span class="sxs-lookup"><span data-stu-id="b2716-290">MenuSelectedEvent</span></span> | <span data-ttu-id="b2716-291">MenuSelect.wav</span><span class="sxs-lookup"><span data-stu-id="b2716-291">MenuSelect.wav</span></span> | <span data-ttu-id="b2716-292">Wird wiedergegeben, wenn der Benutzer ein Menüelement auswählt.</span><span class="sxs-lookup"><span data-stu-id="b2716-292">Played when the user selects a menu item.</span></span>           |

 

<span data-ttu-id="b2716-293">Das folgende Beispiel zeigt, wie die **Audio::CreateResources**-Methode die Quellstimme für die Hintergrundmusik erstellt.</span><span class="sxs-lookup"><span data-stu-id="b2716-293">The following example shows how the **Audio::CreateResources** method creates the source voice for the background music.</span></span> <span data-ttu-id="b2716-294">Die [XAUDIO2\_SEND\_DESCRIPTOR](https://msdn.microsoft.com/library/windows/desktop/ee419244)-Struktur definiert die Zielstimme einer anderen Stimme und gibt an, ob ein Filter verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b2716-294">The [XAUDIO2\_SEND\_DESCRIPTOR](https://msdn.microsoft.com/library/windows/desktop/ee419244) structure defines the target destination voice from another voice and specifies whether a filter should be used.</span></span> <span data-ttu-id="b2716-295">Marble Maze ruft die **Audio::SetSoundEffectFilter**-Methode auf, um mit den Filtern den Sound der rollenden Murmel zu ändern.</span><span class="sxs-lookup"><span data-stu-id="b2716-295">Marble Maze calls the **Audio::SetSoundEffectFilter** method to use the filters to change the sound of the ball as it rolls.</span></span> <span data-ttu-id="b2716-296">Die [XAUDIO2\_VOICE\_SENDS](https://msdn.microsoft.com/library/windows/desktop/ee419246)-Struktur definiert die Stimmen, die Daten von einer einzelnen Ausgabestimme empfangen sollen.</span><span class="sxs-lookup"><span data-stu-id="b2716-296">The [XAUDIO2\_VOICE\_SENDS](https://msdn.microsoft.com/library/windows/desktop/ee419246) structure defines the set of voices to receive data from a single output voice.</span></span> <span data-ttu-id="b2716-297">Marble Maze sendet Daten von der Quellstimme an die Masterstimme (für den direkten oder unveränderten Teil eines wiedergegebenen Sounds) und an die zwei Submixstimmen, die den mit einem Effekt versehenen oder hallenden Teil eines wiedergegebenen Sounds implementieren.</span><span class="sxs-lookup"><span data-stu-id="b2716-297">Marble Maze sends data from the source voice to the mastering voice (for the dry, or unaltered, portion of a playing sound) and to the two submix voices that implement the wet, or reverberant, portion of a playing sound.</span></span>

<span data-ttu-id="b2716-298">Die [IXAudio2::CreateSourceVoice](https://msdn.microsoft.com/library/windows/desktop/ee418607)-Methode erstellt und konfiguriert eine Quellstimme.</span><span class="sxs-lookup"><span data-stu-id="b2716-298">The [IXAudio2::CreateSourceVoice](https://msdn.microsoft.com/library/windows/desktop/ee418607) method creates and configures a source voice.</span></span> <span data-ttu-id="b2716-299">Sie akzeptiert eine [WAVEFORMATEX](https://msdn.microsoft.com/library/windows/hardware/ff538799)-Struktur, die das Format der an die Stimme gesendeten Audiopuffer definiert.</span><span class="sxs-lookup"><span data-stu-id="b2716-299">It takes a [WAVEFORMATEX](https://msdn.microsoft.com/library/windows/hardware/ff538799) structure that defines the format of the audio buffers that are sent to the voice.</span></span> <span data-ttu-id="b2716-300">Wie bereits erwähnt verwendet Marble Maze das PCM-Format.</span><span class="sxs-lookup"><span data-stu-id="b2716-300">As mentioned previously, Marble Maze uses the PCM format.</span></span>

```cpp
XAUDIO2_SEND_DESCRIPTOR descriptors[3];
descriptors[0].pOutputVoice = m_musicMasteringVoice;
descriptors[0].Flags = 0;
descriptors[1].pOutputVoice = m_musicReverbVoiceSmallRoom;
descriptors[1].Flags = 0;
descriptors[2].pOutputVoice = m_musicReverbVoiceLargeRoom;
descriptors[2].Flags = 0;
XAUDIO2_VOICE_SENDS sends = {0};
sends.SendCount = 3;
sends.pSends = descriptors;
WAVEFORMATEX& waveFormat = m_musicStreamer.GetOutputWaveFormatEx();

DX::ThrowIfFailed(
    m_musicEngine->CreateSourceVoice(&m_musicSourceVoice, &waveFormat, 0, 1.0f, &m_voiceContext, &sends, nullptr)
    );

DX::ThrowIfFailed(
    m_musicMasteringVoice->SetVolume(0.4f)
    );
```

## <a name="playing-background-music"></a><span data-ttu-id="b2716-301">Wiedergeben von Hintergrundmusik</span><span class="sxs-lookup"><span data-stu-id="b2716-301">Playing background music</span></span>


<span data-ttu-id="b2716-302">Eine Quellstimme wird im angehaltenen Zustand erstellt.</span><span class="sxs-lookup"><span data-stu-id="b2716-302">A source voice is created in the stopped state.</span></span> <span data-ttu-id="b2716-303">Marble Maze startet die Hintergrundmusik in der Spielschleife.</span><span class="sxs-lookup"><span data-stu-id="b2716-303">Marble Maze starts the background music in the game loop.</span></span> <span data-ttu-id="b2716-304">Beim ersten Aufruf von **MarbleMazeMain::Update** wird **Audio::Start** aufgerufen, um die Hintergrundmusik zu starten.</span><span class="sxs-lookup"><span data-stu-id="b2716-304">The first call to **MarbleMazeMain::Update** calls **Audio::Start** to start the background music.</span></span>

```cpp
if (!m_audio.m_isAudioStarted)
{
    m_audio.Start();
}
```

<span data-ttu-id="b2716-305">Die **Audio::Start**-Methode ruft [IXAudio2SourceVoice::Start](https://msdn.microsoft.com/library/windows/desktop/ee418471) auf, um die Verarbeitung der Quellstimme für die Hintergrundmusik zu starten.</span><span class="sxs-lookup"><span data-stu-id="b2716-305">The **Audio::Start** method calls [IXAudio2SourceVoice::Start](https://msdn.microsoft.com/library/windows/desktop/ee418471) to start to process the source voice for the background music.</span></span>

```cpp
void Audio::Start()
{     
    if (m_engineExperiencedCriticalError)
    {
        return;
    }

    HRESULT hr = m_musicSourceVoice->Start(0);

    if SUCCEEDED(hr) {
        m_isAudioStarted = true;
    }
    else
    {
        m_engineExperiencedCriticalError = true;
    }
}
```

<span data-ttu-id="b2716-306">Die Quellstimme gibt diese Audiodaten an die nächste Phase des Audiodiagramms weiter.</span><span class="sxs-lookup"><span data-stu-id="b2716-306">The source voice passes that audio data to the next stage of the audio graph.</span></span> <span data-ttu-id="b2716-307">Im Fall von Marble Maze enthält die nächste Phase zwei Submixstimmen, die die beiden Halleffekte auf die Audiodaten anwenden.</span><span class="sxs-lookup"><span data-stu-id="b2716-307">In the case of Marble Maze, the next stage contains two submix voices that apply the two reverb effects to the audio.</span></span> <span data-ttu-id="b2716-308">Eine Submixstimme wendet einen nah klingenden, spät hörbaren Halleffekt an, die zweite wendet einen entfernt klingenden, spät hörbaren Halleffekt an.</span><span class="sxs-lookup"><span data-stu-id="b2716-308">One submix voice applies a close late-field reverb; the second applies a far late-field reverb.</span></span>

<span data-ttu-id="b2716-309">In welchem Umfang die einzelnen Submixstimmen zur endgültigen Mischung beitragen, hängt von der Größe und Form des Raums ab.</span><span class="sxs-lookup"><span data-stu-id="b2716-309">The amount that each submix voice contributes to the final mix is determined by the size and shape of the room.</span></span> <span data-ttu-id="b2716-310">Der nah klingende Halleffekt trägt mehr bei, wenn sich die Murmel in der Nähe einer Wand oder in einem kleinen Raum befindet, und der spät hörbare Halleffekt trägt mehr bei, wenn sich die Murmel in einem großen Raum befindet.</span><span class="sxs-lookup"><span data-stu-id="b2716-310">The near-field reverb contributes more when the ball is near a wall or in a small room, and the late-field reverb contributes more when the ball is in a large space.</span></span> <span data-ttu-id="b2716-311">Durch diese Vorgehensweise entsteht ein realistischerer Echoeffekt, wenn sich die Murmel durch das Labyrinth bewegt.</span><span class="sxs-lookup"><span data-stu-id="b2716-311">This technique produces a more realistic echo effect as the marble moves through the maze.</span></span> <span data-ttu-id="b2716-312">Weitere Informationen zur Implementierung dieses Effekts in Marble Maze finden Sie im Marble Maze-Quellcode unter **Audio::SetRoomSize** und **Physics::CalculateCurrentRoomSize**.</span><span class="sxs-lookup"><span data-stu-id="b2716-312">To learn more about how Marble Maze implements this effect, see **Audio::SetRoomSize** and **Physics::CalculateCurrentRoomSize** in the Marble Maze source code.</span></span>

> [!NOTE]
> <span data-ttu-id="b2716-313">In einem Spiel mit relativ gleichen Raumgrößen können Sie ein einfacheres Hallmodell verwenden.</span><span class="sxs-lookup"><span data-stu-id="b2716-313">In a game in which most room sizes are relatively the same, you can use a more basic reverb model.</span></span> <span data-ttu-id="b2716-314">Zum Beispiel können Sie eine Halleinstellung für alle Räume verwenden oder für jeden Raum eine vordefinierte Halleinstellung erstellen.</span><span class="sxs-lookup"><span data-stu-id="b2716-314">For example, you can use one reverb setting for all rooms or you can create a predefined reverb setting for each room.</span></span>

<span data-ttu-id="b2716-315">Die **Audio::CreateResources**-Methode verwendet Media Foundation zum Laden der Hintergrundmusik.</span><span class="sxs-lookup"><span data-stu-id="b2716-315">The **Audio::CreateResources** method uses Media Foundation to load the background music.</span></span> <span data-ttu-id="b2716-316">An dieser Stelle hat die Quellstimme aber noch keine Audiodaten, mit denen sie arbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="b2716-316">At this point, however, the source voice does not have audio data to work with.</span></span> <span data-ttu-id="b2716-317">Darüber hinaus muss die Quellstimme regelmäßig mit Daten aktualisiert werden, damit die Wiedergabe der Hintergrundmusik, die in einer Schleife wiedergegeben wird, fortgesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="b2716-317">In addition, because the background music loops, the source voice must be regularly updated with data so that the music continues to play.</span></span>

<span data-ttu-id="b2716-318">Damit die Quellstimme immer mit Daten gefüllt ist, aktualisiert die Spielschleife die Audiopuffer in jedem Frame.</span><span class="sxs-lookup"><span data-stu-id="b2716-318">To keep the source voice filled with data, the game loop updates the audio buffers every frame.</span></span> <span data-ttu-id="b2716-319">Die **MarbleMazeMain::Render**-Methode ruft **Audio::Render** auf, um den Audiopuffer der Hintergrundmusik zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="b2716-319">The **MarbleMazeMain::Render** method calls **Audio::Render** to process the background music audio buffer.</span></span> <span data-ttu-id="b2716-320">Durch **Audio**-Klasse wird ein Array mit drei Audiopuffern definiert: **m\_audioBuffers**.</span><span class="sxs-lookup"><span data-stu-id="b2716-320">The **Audio** class defines an array of three audio buffers, **m\_audioBuffers**.</span></span> <span data-ttu-id="b2716-321">Jeder Puffer enthält 64 KB (65536 Byte) an Daten.</span><span class="sxs-lookup"><span data-stu-id="b2716-321">Each buffer holds 64 KB (65536 bytes) of data.</span></span> <span data-ttu-id="b2716-322">Die Schleife liest Daten aus dem Media Foundation-Objekt und schreibt diese Daten in die Quellstimme, bis die Warteschlange drei Puffer enthält.</span><span class="sxs-lookup"><span data-stu-id="b2716-322">The loop reads data from the Media Foundation object and writes that data to the source voice until the source voice has three queued buffers.</span></span>

> [!CAUTION]
> <span data-ttu-id="b2716-323">Obwohl Marble Maze einen 64KB großen Puffer für Musikdaten verwendet, müssen Sie möglicherweise einen größeren oder kleineren Puffer verwenden.</span><span class="sxs-lookup"><span data-stu-id="b2716-323">Although Marble Maze uses a 64 KB buffer to hold music data, you may need to use a larger or smaller buffer.</span></span> <span data-ttu-id="b2716-324">Die Größe hängt von den Anforderungen Ihres Spiels ab.</span><span class="sxs-lookup"><span data-stu-id="b2716-324">This amount depends on the requirements of your game.</span></span>

```cpp
// This sample processes audio buffers during the render cycle of the application.
// As long as the sample maintains a high-enough frame rate, this approach should
// not glitch audio. In game code, it is best for audio buffers to be processed
// on a separate thread that is not synced to the main render loop of the game.
void Audio::Render()
{
    if (m_engineExperiencedCriticalError)
    {
        m_engineExperiencedCriticalError = false;
        ReleaseResources();
        Initialize();
        CreateResources();
        Start();
        if (m_engineExperiencedCriticalError)
        {
            return;
        }
    }

    try
    {
        bool streamComplete;
        XAUDIO2_VOICE_STATE state;
        uint32 bufferLength;
        XAUDIO2_BUFFER buf = {0};

        // Use MediaStreamer to stream the buffers.
        m_musicSourceVoice->GetState(&state);
        while (state.BuffersQueued <= MAX_BUFFER_COUNT - 1)
        {
            streamComplete = m_musicStreamer.GetNextBuffer(
                m_audioBuffers[m_currentBuffer],
                STREAMING_BUFFER_SIZE,
                &bufferLength
                );

            if (bufferLength > 0)
            {
                buf.AudioBytes = bufferLength;
                buf.pAudioData = m_audioBuffers[m_currentBuffer];
                buf.Flags = (streamComplete) ? XAUDIO2_END_OF_STREAM : 0;
                buf.pContext = 0;
                DX::ThrowIfFailed(
                    m_musicSourceVoice->SubmitSourceBuffer(&buf)
                    );

                m_currentBuffer++;
                m_currentBuffer %= MAX_BUFFER_COUNT;
            }

            if (streamComplete)
            {
                // Loop the stream.
                m_musicStreamer.Restart();
                break;
            }

            m_musicSourceVoice->GetState(&state);
        }
    }
    catch (...)
    {
        m_engineExperiencedCriticalError = true;
    }
}
```

<span data-ttu-id="b2716-325">Die Schleife ist auch zuständig, wenn das Media Foundation-Objekt das Ende des Streams erreicht.</span><span class="sxs-lookup"><span data-stu-id="b2716-325">The loop also handles when the Media Foundation object reaches the end of the stream.</span></span> <span data-ttu-id="b2716-326">In diesem Fall ruft sie die [IMFSourceReader::SetCurrentPosition](https://msdn.microsoft.com/library/windows/desktop/dd374668)-Methode auf, um die Position der Audioquelle zurückzusetzen.</span><span class="sxs-lookup"><span data-stu-id="b2716-326">In this case, it calls the [IMFSourceReader::SetCurrentPosition](https://msdn.microsoft.com/library/windows/desktop/dd374668) method to reset the position of the audio source.</span></span>

```cpp
void MediaStreamer::Restart()
{
    if (m_reader == nullptr)
    {
        return;
    }

    PROPVARIANT var = {0};
    var.vt = VT_I8;

    DX::ThrowIfFailed(
        m_reader->SetCurrentPosition(GUID_NULL, var)
        );
}
```

<span data-ttu-id="b2716-327">Um Audioschleifen für einen einzelnen Puffer (oder für einen vollständigen in den Arbeitsspeicher geladenen Sound) zu implementieren, können Sie das [XAUDIO2_BUFFER](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.xaudio2.xaudio2_buffer)::LoopCount-Feld auf **XAUDIO2\_LOOP\_INFINITE** festlegen, wenn Sie den Sound initialisieren.</span><span class="sxs-lookup"><span data-stu-id="b2716-327">To implement audio looping for a single buffer (or for an entire sound that is fully loaded into memory), you can set the [XAUDIO2_BUFFER](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.xaudio2.xaudio2_buffer)::LoopCount field to **XAUDIO2\_LOOP\_INFINITE** when you initialize the sound.</span></span> <span data-ttu-id="b2716-328">Marble Maze verwendet diese Technik, um den Rollsound der Murmel wiederzugeben.</span><span class="sxs-lookup"><span data-stu-id="b2716-328">Marble Maze uses this technique to play the rolling sound for the marble.</span></span>

```cpp
if (sound == RollingEvent)
{
    m_soundEffects[sound].m_audioBuffer.LoopCount = XAUDIO2_LOOP_INFINITE;
}
```

<span data-ttu-id="b2716-329">Für die Hintergrundmusik verwaltet Marble Maze aber die Puffer direkt, sodass es die Menge des verwendeten Arbeitsspeichers besser steuern kann.</span><span class="sxs-lookup"><span data-stu-id="b2716-329">However, for the background music, Marble Maze manages the buffers directly so that it can better control the amount of memory that is used.</span></span> <span data-ttu-id="b2716-330">Wenn Ihre Musikdateien zu groß sind, können Sie die Musikdaten in kleinere Puffer streamen.</span><span class="sxs-lookup"><span data-stu-id="b2716-330">When your music files are large, you can stream the music data into smaller buffers.</span></span> <span data-ttu-id="b2716-331">Dadurch können Sie die Größe des Arbeitsspeichers besser auf die Verarbeitung und das Streamen von Audiodaten im Spiel abstimmen.</span><span class="sxs-lookup"><span data-stu-id="b2716-331">Doing so can help balance memory size with the frequency of the game’s ability to process and stream audio data.</span></span>

> [!TIP]
> <span data-ttu-id="b2716-332">Wenn Ihr Spiel eine niedrige oder veränderliche Framerate hat, kann die Verarbeitung von Audio im Hauptthread zu unerwarteten Pausen oder zu Knacken im Audio führen. Das kommt daher, dass dem Audiomodul nicht genug gepufferte Audiodaten zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="b2716-332">If your game has a low or varying frame rate, processing audio on the main thread can produce unexpected pauses or pops in the audio because the audio engine has insufficient buffered audio data to work with.</span></span> <span data-ttu-id="b2716-333">Wenn dieses Problem bei Ihrem Spiel zu erwarten ist, denken Sie darüber nach, Audio in einem getrennten Thread zu verarbeiten, in dem kein Rendering ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b2716-333">If your game is sensitive to this issue, consider processing audio on a separate thread that does not perform rendering.</span></span> <span data-ttu-id="b2716-334">Dieser Ansatz ist besonders hilfreich auf Computern mit mehreren Prozessoren, da Ihr Spiel die Prozessoren verwenden kann, die sich im Leerlauf befinden.</span><span class="sxs-lookup"><span data-stu-id="b2716-334">This approach is especially useful on computers that have multiple processors because your game can use idle processors.</span></span>

## <a name="reacting-to-game-events"></a><span data-ttu-id="b2716-335">Reagieren auf Spielereignisse</span><span class="sxs-lookup"><span data-stu-id="b2716-335">Reacting to game events</span></span>

<span data-ttu-id="b2716-336">Die **Audio**-Klasse stellt Methoden wie **PlaySoundEffect**, **IsSoundEffectStarted**, **StopSoundEffect**, **SetSoundEffectVolume**, **SetSoundEffectPitch** und **SetSoundEffectFilter** bereit, damit vom Spiel gesteuert werden kann, wann Sounds wiedergegeben und beendet werden. Außerdem werden damit Soundeigenschaften wie Lautstärke und Tonhöhe gesteuert.</span><span class="sxs-lookup"><span data-stu-id="b2716-336">The **Audio** class provides methods such as **PlaySoundEffect**, **IsSoundEffectStarted**, **StopSoundEffect**, **SetSoundEffectVolume**, **SetSoundEffectPitch**, and **SetSoundEffectFilter** to enable the game to control when sounds play and stop, and to control sound properties such as volume and pitch.</span></span> <span data-ttu-id="b2716-337">Falls die Murmel beispielsweise aus dem Labyrinth herausfällt, ruft **MarbleMazeMain::Update** die **Audio::PlaySoundEffect**-Methode auf, um den **FallingEvent**-Sound wiederzugeben.</span><span class="sxs-lookup"><span data-stu-id="b2716-337">For example, if the marble falls off the maze, **MarbleMazeMain::Update** calls the **Audio::PlaySoundEffect** method to play the **FallingEvent** sound.</span></span>

```cpp
m_audio.PlaySoundEffect(FallingEvent);
```

<span data-ttu-id="b2716-338">Die **Audio::PlaySoundEffect**-Methode ruft die [IXAudio2SourceVoice::Start](https://msdn.microsoft.com/library/windows/desktop/ee418471)-Methode auf, um die Wiedergabe des Sounds zu starten.</span><span class="sxs-lookup"><span data-stu-id="b2716-338">The **Audio::PlaySoundEffect** method calls the [IXAudio2SourceVoice::Start](https://msdn.microsoft.com/library/windows/desktop/ee418471) method to begin playback of the sound.</span></span> <span data-ttu-id="b2716-339">Wenn die **IXAudio2SourceVoice::Start**-Methode bereits aufgerufen wurde, wird sie nicht erneut gestartet.</span><span class="sxs-lookup"><span data-stu-id="b2716-339">If the **IXAudio2SourceVoice::Start** method has already been called, it is not started again.</span></span> <span data-ttu-id="b2716-340">**Audio::PlaySoundEffect** führt anschließend eine benutzerdefinierte Logik für bestimmte Sounds aus.</span><span class="sxs-lookup"><span data-stu-id="b2716-340">**Audio::PlaySoundEffect** then performs custom logic for certain sounds.</span></span>

```cpp
void Audio::PlaySoundEffect(SoundEvent sound)
{
    XAUDIO2_BUFFER buf = {0};
    XAUDIO2_VOICE_STATE state = {0};

    if (m_engineExperiencedCriticalError)
    {
        // If there's an error, then we'll recreate the engine on the next
        // render pass.
        return;
    }

    SoundEffectData* soundEffect = &m_soundEffects[sound];
    HRESULT hr = soundEffect->m_soundEffectSourceVoice->Start();

    if FAILED(hr)
    {
        m_engineExperiencedCriticalError = true;
        return;
    }

    // For one-off voices, submit a new buffer if there's none queued up,
    // and allow up to two collisions to be queued up. 
    if (sound != RollingEvent)
    {
        XAUDIO2_VOICE_STATE state = {0};

        soundEffect->m_soundEffectSourceVoice->
            GetState(&state, XAUDIO2_VOICE_NOSAMPLESPLAYED);

        if (state.BuffersQueued == 0)
        {
            soundEffect->m_soundEffectSourceVoice->
                SubmitSourceBuffer(&soundEffect->m_audioBuffer);
        }
        else if (state.BuffersQueued < 2 && sound == CollisionEvent)
        {
            soundEffect->m_soundEffectSourceVoice->
                SubmitSourceBuffer(&soundEffect->m_audioBuffer);
        }

        // For the menu clicks, we want to stop the voice and replay the click
        // right away.
        // Note that stopping and then flushing could cause a glitch due to the
        // waveform not being at a zero-crossing, but due to the nature of the 
        // sound (fast and 'clicky'), we don't mind.
        if (state.BuffersQueued > 0 && sound == MenuChangeEvent)
        {
            soundEffect->m_soundEffectSourceVoice->Stop();
            soundEffect->m_soundEffectSourceVoice->FlushSourceBuffers();

            soundEffect->m_soundEffectSourceVoice->
                SubmitSourceBuffer(&soundEffect->m_audioBuffer);

            soundEffect->m_soundEffectSourceVoice->Start();
        }
    }

    m_soundEffects[sound].m_soundEffectStarted = true;
}
```

<span data-ttu-id="b2716-341">Für andere Sounds als den Rollsound ruft die **Audio::PlaySoundEffect**-Methode [IXAudio2SourceVoice::GetState](https://msdn.microsoft.com/library/windows/desktop/hh405047) auf, um die Anzahl der Puffer zu ermitteln, die die Quellstimme wiedergibt.</span><span class="sxs-lookup"><span data-stu-id="b2716-341">For sounds other than rolling, the **Audio::PlaySoundEffect** method calls [IXAudio2SourceVoice::GetState](https://msdn.microsoft.com/library/windows/desktop/hh405047) to determine the number of buffers that the source voice is playing.</span></span> <span data-ttu-id="b2716-342">Sie ruft [IXAudio2SourceVoice::SubmitSourceBuffer](https://msdn.microsoft.com/library/windows/desktop/ee418473) auf, um die Audiodaten für den Sound der Eingabewarteschlange der Stimme hinzuzufügen, wenn keine Puffer aktiv sind.</span><span class="sxs-lookup"><span data-stu-id="b2716-342">It calls [IXAudio2SourceVoice::SubmitSourceBuffer](https://msdn.microsoft.com/library/windows/desktop/ee418473) to add the audio data for the sound to the voice’s input queue if no buffers are active.</span></span> <span data-ttu-id="b2716-343">Mit der **Audio::PlaySoundEffect**-Methode kann der Kollisionssound auch zweimal hintereinander wiedergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="b2716-343">The **Audio::PlaySoundEffect** method also enables the collision sound to be played two times in sequence.</span></span> <span data-ttu-id="b2716-344">Dies ist beispielsweise der Fall, wenn die Murmel mit einer Ecke des Labyrinths kollidiert.</span><span class="sxs-lookup"><span data-stu-id="b2716-344">This occurs, for example, when the marble collides with a corner of the maze.</span></span>

<span data-ttu-id="b2716-345">Wie bereits beschrieben verwendet die Audio-Klasse das **XAUDIO2\_LOOP\_INFINITE**-Kennzeichen, wenn sie den Sound für das Rollereignis initialisiert.</span><span class="sxs-lookup"><span data-stu-id="b2716-345">As already described, the Audio class uses the **XAUDIO2\_LOOP\_INFINITE** flag when it initializes the sound for the rolling event.</span></span> <span data-ttu-id="b2716-346">Der Sound wird in einer Schleife wiedergegeben, wenn **Audio::PlaySoundEffect** erstmals für dieses Ereignis aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b2716-346">The sound starts looped playback the first time that **Audio::PlaySoundEffect** is called for this event.</span></span> <span data-ttu-id="b2716-347">Um die Wiedergabelogik für den Rollsound zu vereinfachen, schaltet Marble Maze den Sound stumm, anstatt ihn anzuhalten.</span><span class="sxs-lookup"><span data-stu-id="b2716-347">To simplify the playback logic for the rolling sound, Marble Maze mutes the sound instead of stopping it.</span></span> <span data-ttu-id="b2716-348">Wenn sich die Geschwindigkeit der Murmel ändert, werden Tonhöhe und Lautstärke des Sounds geändert, damit er realistischer klingt.</span><span class="sxs-lookup"><span data-stu-id="b2716-348">As the marble changes velocity, Marble Maze changes the pitch and volume of the sound to give it a more realistic effect.</span></span> <span data-ttu-id="b2716-349">Unten wird gezeigt, wie die **MarbleMazeMain::Update**-Methode die Tonhöhe und Lautstärke der Murmel aktualisiert, wenn sich die Geschwindigkeit ändert, und wie sie beim Anhalten der Murmel den Sound stummschaltet, indem sie die Lautstärke auf Null festlegt.</span><span class="sxs-lookup"><span data-stu-id="b2716-349">The following shows how the **MarbleMazeMain::Update** method updates the pitch and volume of the marble as its velocity changes and how it mutes the sound by setting its volume to zero when the marble stops.</span></span>

```cpp
// Play the roll sound only if the marble is actually rolling.
if (ci.isRollingOnFloor && volume > 0)
{
    if (!m_audio.IsSoundEffectStarted(RollingEvent))
    {
        m_audio.PlaySoundEffect(RollingEvent);
    }

    // Update the volume and pitch by the velocity.
    m_audio.SetSoundEffectVolume(RollingEvent, volume);
    m_audio.SetSoundEffectPitch(RollingEvent, pitch);

    // The rolling sound has at most 8000Hz sounds, so we linearly
    // ramp up the low-pass filter the faster we go.
    // We also reduce the Q-value of the filter, starting with a
    // relatively broad cutoff and get progressively tighter.
    m_audio.SetSoundEffectFilter(
        RollingEvent,
        600.0f + 8000.0f * volume,
        XAUDIO2_MAX_FILTER_ONEOVERQ - volume*volume
        );
}
else
{
    m_audio.SetSoundEffectVolume(RollingEvent, 0);
}
```

## <a name="reacting-to-suspend-and-resume-events"></a><span data-ttu-id="b2716-350">Reagieren auf Anhalte- und Fortsetzungsereignisse</span><span class="sxs-lookup"><span data-stu-id="b2716-350">Reacting to suspend and resume events</span></span>

<span data-ttu-id="b2716-351">In [Marble Maze-Anwendungsstruktur](marble-maze-application-structure.md) wird beschrieben, wie Marble Maze Anhalten und Fortsetzen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b2716-351">[Marble Maze application structure](marble-maze-application-structure.md) describes how Marble Maze supports suspend and resume.</span></span> <span data-ttu-id="b2716-352">Wenn das Spiel angehalten wird, wird auch die Audiowiedergabe angehalten.</span><span class="sxs-lookup"><span data-stu-id="b2716-352">When the game is suspended, the game pauses the audio.</span></span> <span data-ttu-id="b2716-353">Wenn das Spiel fortgesetzt wird, wird die Audiowiedergabe an der Stelle fortgesetzt, an der sie unterbrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="b2716-353">When the game resumes, the game resumes the audio where it left off.</span></span> <span data-ttu-id="b2716-354">Damit orientieren wir uns an der bewährten Methode, keine Ressourcen zu verwenden, die nicht benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="b2716-354">We do so to follow the best practice of not using resources when you know they’re not needed.</span></span>

<span data-ttu-id="b2716-355">Wenn das Spiel angehalten wird, wird die **Audio::SuspendAudio**-Methode aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="b2716-355">The **Audio::SuspendAudio** method is called when the game is suspended.</span></span> <span data-ttu-id="b2716-356">Diese Methode ruft die [IXAudio2::StopEngine](https://msdn.microsoft.com/library/windows/desktop/ee418628)-Methode auf, um die gesamte Audiowiedergabe anzuhalten.</span><span class="sxs-lookup"><span data-stu-id="b2716-356">This method calls the [IXAudio2::StopEngine](https://msdn.microsoft.com/library/windows/desktop/ee418628) method to stop all audio.</span></span> <span data-ttu-id="b2716-357">Obwohl **IXAudio2::StopEngine** sofort die gesamte Audioausgabe anhält, bleiben das Audiodiagramm und die Effektparameter erhalten (z. B. der Halleffekt, der beim Aufprallen der Murmel angewendet wird).</span><span class="sxs-lookup"><span data-stu-id="b2716-357">Although **IXAudio2::StopEngine** stops all audio output immediately, it preserves the audio graph and its effect parameters (for example, the reverb effect that’s applied when the marble bounces).</span></span>

```cpp
// Uses the IXAudio2::StopEngine method to stop all audio immediately.  
// It leaves the audio graph untouched, which preserves all effect parameters   
// and effect histories (like reverb effects) voice states, pending buffers,  
// cursor positions and so on. 
// When the engines are restarted, the resulting audio will sound as if it had  
// never been stopped except for the period of silence. 
void Audio::SuspendAudio()
{
    if (m_engineExperiencedCriticalError)
    {
        return;
    }

    if (m_isAudioStarted)
    {
        m_musicEngine->StopEngine();
        m_soundEffectEngine->StopEngine();
    }

    m_isAudioStarted = false;
}
```

<span data-ttu-id="b2716-358">Wenn das Spiel fortgesetzt wird, wird die **Audio::ResumeAudio**-Methode aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="b2716-358">The **Audio::ResumeAudio** method is called when the game is resumed.</span></span> <span data-ttu-id="b2716-359">Diese Methode verwendet die [IXAudio2::StartEngine](https://msdn.microsoft.com/library/windows/desktop/ee418626)-Methode, um die Audiowiedergabe neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="b2716-359">This method uses the [IXAudio2::StartEngine](https://msdn.microsoft.com/library/windows/desktop/ee418626) method to restart the audio.</span></span> <span data-ttu-id="b2716-360">Da beim Aufruf von [IXAudio2::StopEngine](https://msdn.microsoft.com/library/windows/desktop/ee418628) das Audiodiagramm und die Effektparameter erhalten bleiben, wird die Audioausgabe an der Stelle fortgesetzt, an der sie unterbrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="b2716-360">Because the call to [IXAudio2::StopEngine](https://msdn.microsoft.com/library/windows/desktop/ee418628) preserves the audio graph and its effect parameters, the audio output resumes where it left off.</span></span>

```cpp
// Restarts the audio streams. A call to this method must match a previous call
// to SuspendAudio. This method causes audio to continue where it left off.
// If there is a problem with the restart, the m_engineExperiencedCriticalError
// flag is set. The next call to Render will recreate all the resources and
// reset the audio pipeline.
void Audio::ResumeAudio()
{
    if (m_engineExperiencedCriticalError)
    {
        return;
    }

    HRESULT hr = m_musicEngine->StartEngine();
    HRESULT hr2 = m_soundEffectEngine->StartEngine();

    if (FAILED(hr) || FAILED(hr2))
    {
        m_engineExperiencedCriticalError = true;
    }
}
```

## <a name="handling-headphones-and-device-changes"></a><span data-ttu-id="b2716-361">Behandeln von Kopfhörern und Geräteänderungen</span><span class="sxs-lookup"><span data-stu-id="b2716-361">Handling headphones and device changes</span></span>

<span data-ttu-id="b2716-362">Marble Maze behandelt Fehler des XAudio2-Moduls wie zum Beispiel eine Änderung des Audiogeräts mithilfe von Modulrückrufen.</span><span class="sxs-lookup"><span data-stu-id="b2716-362">Marble Maze uses engine callbacks to handle XAudio2 engine failures, such as when the audio device changes.</span></span> <span data-ttu-id="b2716-363">Zu einer Geräteänderung kommt es meist, wenn der Benutzer des Spiels die Kopfhörer anschließt oder trennt.</span><span class="sxs-lookup"><span data-stu-id="b2716-363">A likely cause of a device change is when the game user connects or disconnects the headphones.</span></span> <span data-ttu-id="b2716-364">Sie sollten den Modulrückruf implementieren, der Geräteänderungen behandelt.</span><span class="sxs-lookup"><span data-stu-id="b2716-364">We recommend that you implement the engine callback that handles device changes.</span></span> <span data-ttu-id="b2716-365">Ansonsten wird die Soundwiedergabe im Spiel bis zum Neustart angehalten, wenn der Benutzer Kopfhörer anschließt oder entfernt.</span><span class="sxs-lookup"><span data-stu-id="b2716-365">Otherwise, your game will stop playing sound when the user plugs in or removes headphones, until the game is restarted.</span></span>

<span data-ttu-id="b2716-366">**Audio.h** definiert die **AudioEngineCallbacks**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b2716-366">**Audio.h** defines the **AudioEngineCallbacks** class.</span></span> <span data-ttu-id="b2716-367">Diese Klasse implementiert die [IXAudio2EngineCallback](https://msdn.microsoft.com/library/windows/desktop/ee415910)-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="b2716-367">This class implements the [IXAudio2EngineCallback](https://msdn.microsoft.com/library/windows/desktop/ee415910) interface.</span></span>

```cpp
class AudioEngineCallbacks: public IXAudio2EngineCallback
{
private:
    Audio* m_audio;

public :
    AudioEngineCallbacks(){};
    void Initialize(Audio* audio);

    // Called by XAudio2 just before an audio processing pass begins.
    void _stdcall OnProcessingPassStart(){};

    // Called just after an audio processing pass ends.
    void  _stdcall OnProcessingPassEnd(){};

    // Called when a critical system error causes XAudio2
    // to be closed and restarted. The error code is given in Error.
    void  _stdcall OnCriticalError(HRESULT Error);
};
```

<span data-ttu-id="b2716-368">Über die [IXAudio2EngineCallback](https://msdn.microsoft.com/library/windows/desktop/ee415910)-Schnittstelle kann Ihr Code benachrichtigt werden, wenn Audioverarbeitungsereignisse auftreten und im Modul ein schwerwiegender Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="b2716-368">The [IXAudio2EngineCallback](https://msdn.microsoft.com/library/windows/desktop/ee415910) interface enables your code to be notified when audio processing events occur and when the engine encounters a critical error.</span></span> <span data-ttu-id="b2716-369">Um sich für Rückrufe zu registrieren, ruft Marble Maze nach der Erstellung des [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908)-Objekts für das Musikmodul die [IXAudio2::RegisterForCallbacks](https://msdn.microsoft.com/library/windows/desktop/ee418620)-Methode in **Audio::CreateResources** auf.</span><span class="sxs-lookup"><span data-stu-id="b2716-369">To register for callbacks, Marble Maze calls the [IXAudio2::RegisterForCallbacks](https://msdn.microsoft.com/library/windows/desktop/ee418620) method in **Audio::CreateResources**, after it creates the [IXAudio2](https://msdn.microsoft.com/library/windows/desktop/ee415908) object for the music engine.</span></span>

```cpp
m_musicEngineCallback.Initialize(this);
m_musicEngine->RegisterForCallbacks(&m_musicEngineCallback);
```

<span data-ttu-id="b2716-370">Marble Maze muss nicht benachrichtigt werden, wenn die Audioverarbeitung gestartet oder beendet wird.</span><span class="sxs-lookup"><span data-stu-id="b2716-370">Marble Maze does not require notification when audio processing starts or ends.</span></span> <span data-ttu-id="b2716-371">Daher implementiert es die Methoden [IXAudio2EngineCallback::OnProcessingPassStart](https://msdn.microsoft.com/library/windows/desktop/ee418463) und [IXAudio2EngineCallback::OnProcessingPassEnd](https://msdn.microsoft.com/library/windows/desktop/ee418462) so, dass sie keine Aktion ausführen.</span><span class="sxs-lookup"><span data-stu-id="b2716-371">Therefore, it implements the [IXAudio2EngineCallback::OnProcessingPassStart](https://msdn.microsoft.com/library/windows/desktop/ee418463) and [IXAudio2EngineCallback::OnProcessingPassEnd](https://msdn.microsoft.com/library/windows/desktop/ee418462) methods to do nothing.</span></span> <span data-ttu-id="b2716-372">Für die [IXAudio2EngineCallback::OnCriticalError](https://msdn.microsoft.com/library/windows/desktop/ee418461)-Methode ruft Marble Maze die **SetEngineExperiencedCriticalError**-Methode auf, die das **m\_engineExperiencedCriticalError**-Kennzeichen festlegt.</span><span class="sxs-lookup"><span data-stu-id="b2716-372">For the [IXAudio2EngineCallback::OnCriticalError](https://msdn.microsoft.com/library/windows/desktop/ee418461) method, Marble Maze calls the **SetEngineExperiencedCriticalError** method, which sets the **m\_engineExperiencedCriticalError** flag.</span></span>

```cpp
// Audio.cpp

// Called when a critical system error causes XAudio2 
// to be closed and restarted. The error code is given in Error. 
void  _stdcall AudioEngineCallbacks::OnCriticalError(HRESULT Error)
{
    m_audio->SetEngineExperiencedCriticalError();
}
```

```cpp
// Audio.h (Audio class)

// This flag can be used to tell when the audio system 
// is experiencing critial errors.
// XAudio2 gives a critical error when the user unplugs
// the headphones and a new speaker configuration is generated.
void SetEngineExperiencedCriticalError()
{
    m_engineExperiencedCriticalError = true;
}
```

<span data-ttu-id="b2716-373">Wenn ein schwerwiegender Fehler auftritt, wird die Audioverarbeitung beendet, und alle weiteren Aufrufe an XAudio2 schlagen fehl.</span><span class="sxs-lookup"><span data-stu-id="b2716-373">When a critical error occurs, audio processing stops and all additional calls to XAudio2 fail.</span></span> <span data-ttu-id="b2716-374">Um diese Situation zu beheben, müssen Sie die XAudio2-Instanz freigeben und eine neue erstellen.</span><span class="sxs-lookup"><span data-stu-id="b2716-374">To recover from this situation, you must release the XAudio2 instance and create a new one.</span></span> <span data-ttu-id="b2716-375">Die **Audio::Render**-Methode, die in jedem Frame über die Spielschleife aufgerufen wird, überprüft zuerst das **m\_engineExperiencedCriticalError**-Kennzeichen.</span><span class="sxs-lookup"><span data-stu-id="b2716-375">The **Audio::Render** method, which is called from the game loop every frame, first checks the **m\_engineExperiencedCriticalError** flag.</span></span> <span data-ttu-id="b2716-376">Wenn das Kennzeichen festgelegt ist, löscht die Methode das Kennzeichen, gibt die aktuelle XAudio2-Instanz frei, initialisiert Ressourcen und startet dann die Hintergrundmusik.</span><span class="sxs-lookup"><span data-stu-id="b2716-376">If this flag is set, it clears the flag, releases the current XAudio2 instance, initializes resources, and then starts the background music.</span></span>

```cpp
if (m_engineExperiencedCriticalError)
{
    m_engineExperiencedCriticalError = false;
    ReleaseResources();
    Initialize();
    CreateResources();
    Start();
    if (m_engineExperiencedCriticalError)
    {
        return;
    }
}
```

<span data-ttu-id="b2716-377">Marble Maze verwendet außerdem das **m\_engineExperiencedCriticalError**-Kennzeichen, damit XAudio2 nicht aufgerufen wird, wenn kein Audiogerät verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="b2716-377">Marble Maze also uses the **m\_engineExperiencedCriticalError** flag to guard against calling into XAudio2 when no audio device is available.</span></span> <span data-ttu-id="b2716-378">Wenn dieses Kennzeichen festgelegt ist, verarbeitet die **MarbleMazeMain::Update**-Methode zum Beispiel kein Audio für Roll- oder Kollisionsereignisse.</span><span class="sxs-lookup"><span data-stu-id="b2716-378">For example, the **MarbleMazeMain::Update** method does not process audio for rolling or collision events when this flag is set.</span></span> <span data-ttu-id="b2716-379">Die App versucht, das Audiomodul in jedem Frame zu reparieren, wenn dies notwendig ist. Das **m\_engineExperiencedCriticalError**-Kennzeichen ist aber möglicherweise festgelegt, wenn der Computer nicht über ein Audiogerät verfügt oder wenn die Kopfhörer getrennt werden und kein anderes Audiogerät verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="b2716-379">The app attempts to repair the audio engine every frame if it is required; however, the **m\_engineExperiencedCriticalError** flag might always be set if the computer does not have an audio device or the headphones are unplugged and there is no other available audio device.</span></span>

> [!CAUTION]
> <span data-ttu-id="b2716-380">Sie sollten grundsätzlich im Hauptteil eines Modulrückrufs keine Blockierungsvorgänge ausführen.</span><span class="sxs-lookup"><span data-stu-id="b2716-380">As a rule, do not perform blocking operations in the body of an engine callback.</span></span> <span data-ttu-id="b2716-381">Diese können zu Leistungsproblemen führen.</span><span class="sxs-lookup"><span data-stu-id="b2716-381">Doing so can cause performance issues.</span></span> <span data-ttu-id="b2716-382">Marble Maze legt im **OnCriticalError**-Rückruf ein Kennzeichen fest und behandelt später den Fehler in der normalen Audioverarbeitungsphase.</span><span class="sxs-lookup"><span data-stu-id="b2716-382">Marble Maze sets a flag in the **OnCriticalError** callback and later handles the error during the regular audio processing phase.</span></span> <span data-ttu-id="b2716-383">Weitere Informationen zu XAudio2-Rückrufen finden Sie unter [XAudio2-Rückrufe](https://msdn.microsoft.com/library/windows/desktop/ee415745).</span><span class="sxs-lookup"><span data-stu-id="b2716-383">For more information about XAudio2 callbacks, see [XAudio2 Callbacks](https://msdn.microsoft.com/library/windows/desktop/ee415745).</span></span>

## <a name="conclusion"></a><span data-ttu-id="b2716-384">Fazit</span><span class="sxs-lookup"><span data-stu-id="b2716-384">Conclusion</span></span>

<span data-ttu-id="b2716-385">Hier endet das Spielebeispiel für Marble Maze!</span><span class="sxs-lookup"><span data-stu-id="b2716-385">That wraps up the Marble Maze game sample!</span></span> <span data-ttu-id="b2716-386">Obwohl es sich um ein relativ einfaches Spiel handelt, enthält es viele wichtige Teile, die in jedem UWP-DirectX-Spiel enthalten sind, und ist ein gutes Beispiel, wenn Sie Ihr eigenes Spiel erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="b2716-386">Though it is a relatively simple game, it contains many of the important parts that go into any UWP DirectX game, and is a good example to follow when making your own game.</span></span>

<span data-ttu-id="b2716-387">Nachdem Sie fertig sind, versuchen Sie mit dem Quellcode zu spielen und sehen Sie, was passiert.</span><span class="sxs-lookup"><span data-stu-id="b2716-387">Now that you've finished following along, try tinkering around with the source code and seeing what happens.</span></span> <span data-ttu-id="b2716-388">Oder lesen Sie [Erstellen eines einfachen UWP-Spiels mit DirectX](tutorial--create-your-first-uwp-directx-game.md), ein anderes UWP-DirectX-Beispielspiel.</span><span class="sxs-lookup"><span data-stu-id="b2716-388">Or check out [Create a simple UWP game with DirectX](tutorial--create-your-first-uwp-directx-game.md), another UWP DirectX game sample.</span></span>

<span data-ttu-id="b2716-389">Möchten Sie mit DirectX fortfahren?</span><span class="sxs-lookup"><span data-stu-id="b2716-389">Ready to go further with DirectX?</span></span> <span data-ttu-id="b2716-390">Dann sehen Sie sich unsere Leitfäden auf [DirectX-Programmierung](directx-programming.md) an.</span><span class="sxs-lookup"><span data-stu-id="b2716-390">Then check out our guides at [DirectX programming](directx-programming.md).</span></span>

<span data-ttu-id="b2716-391">Wenn Sie die Entwicklung von Spielen auf UWP im Allgemeinen interessiert sind, finden Sie in der Dokumentation zur [Spieleprogrammierung](index.md) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="b2716-391">If you're interested in game development on UWP in general, see the documentation at [Game programming](index.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="b2716-392">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b2716-392">Related topics</span></span>

* [<span data-ttu-id="b2716-393">Hinzufügen von Eingaben und Interaktivität zum Marble Maze-Beispiel</span><span class="sxs-lookup"><span data-stu-id="b2716-393">Adding input and interactivity to the Marble Maze sample</span></span>](adding-input-and-interactivity-to-the-marble-maze-sample.md)
* [<span data-ttu-id="b2716-394">Entwickeln von Marble Maze, einem UWP-Spiel in C++ und DirectX</span><span class="sxs-lookup"><span data-stu-id="b2716-394">Developing Marble Maze, a UWP game in C++ and DirectX</span></span>](developing-marble-maze-a-windows-store-game-in-cpp-and-directx.md)