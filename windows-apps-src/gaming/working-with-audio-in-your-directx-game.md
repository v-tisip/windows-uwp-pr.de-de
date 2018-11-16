---
author: mtoepke
title: Audio für Spiele
description: Hier erfahren Sie, wie Sie Musik und Sound entwickeln und in Ihr DirectX-Spiel integrieren. Außerdem erfahren Sie, wie Sie Audiosignale verarbeiten, um dynamischen und positionsbezogenen Sound zu erzeugen.
ms.assetid: ab29297a-9588-c79b-24c5-3b94b85e74a8
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Audio, DirectX
ms.localizationpriority: medium
ms.openlocfilehash: a0b0ae219ea7fd014b39eb8eb7a09049f7c632a2
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "6992447"
---
# <a name="audio-for-games"></a><span data-ttu-id="87ff5-104">Audio für Spiele</span><span class="sxs-lookup"><span data-stu-id="87ff5-104">Audio for games</span></span>



<span data-ttu-id="87ff5-105">Hier erfahren Sie, wie Sie Musik und Sound entwickeln und in Ihr DirectX-Spiel integrieren. Außerdem erfahren Sie, wie Sie Audiosignale verarbeiten, um dynamischen und positionsbezogenen Sound zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-105">Learn how to develop and incorporate music and sounds into your DirectX game, and how to process the audio signals to create dynamic and positional sounds.</span></span>

<span data-ttu-id="87ff5-106">Für die Audioprogrammierung empfehlen wir die Verwendung der XAudio2-Bibliothek in DirectX, die auch hier zur Anwendung kommt.</span><span class="sxs-lookup"><span data-stu-id="87ff5-106">For audio programming, we recommend using the XAudio2 library in DirectX, and we use it here.</span></span> <span data-ttu-id="87ff5-107">XAudio2 ist eine untergeordnete Audiobibliothek, die eine grundlegende Signalverarbeitung und -abmischung für Spiele bereitstellt und eine Vielzahl von Formaten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="87ff5-107">XAudio2 is a low-level audio library that provides a signal processing and mixing foundation for games, and it supports a variety of formats.</span></span>

<span data-ttu-id="87ff5-108">Einfache Sounds sowie eine einfache Musikwiedergabe können auch mithilfe von [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="87ff5-108">You can also implement simple sounds and music playback with [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> <span data-ttu-id="87ff5-109">Microsoft Media Foundation ist eigentlich für die Wiedergabe von Mediendateien und Datenströmen (sowohl Audio als auch Video) konzipiert, kann aber auch in Spielen eingesetzt werden und ist besonders hilfreich bei Filmszenen oder Spielkomponenten ohne Interaktionsmöglichkeit.</span><span class="sxs-lookup"><span data-stu-id="87ff5-109">Microsoft Media Foundation is designed for the playback of media files and streams, both audio and video, but can also be used in games, and is particularly useful for cinematic scenes or non-interactive components of your game.</span></span>

## <a name="concepts-at-a-glance"></a><span data-ttu-id="87ff5-110">Konzepte auf einen Blick</span><span class="sxs-lookup"><span data-stu-id="87ff5-110">Concepts at a glance</span></span>


<span data-ttu-id="87ff5-111">Im Anschluss finden Sie einige Konzepte für die Audioprogrammierung, die in diesem Abschnitt zur Anwendung kommen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-111">Here are a few audio programming concepts we use in this section.</span></span>

-   <span data-ttu-id="87ff5-112">Signale bilden die Grundeinheit der Soundprogrammierung (vergleichbar mit Pixeln bei der Grafik).</span><span class="sxs-lookup"><span data-stu-id="87ff5-112">Signals are the basic unit of sound programming, analogous to pixels in graphics.</span></span> <span data-ttu-id="87ff5-113">Die digitalen Signalprozessoren (Digital Signal Processors, DSPs), von denen sie verarbeitet werden, sind gewissermaßen die Pixelshader für den Sound des Spiels.</span><span class="sxs-lookup"><span data-stu-id="87ff5-113">The digital signal processors (DSPs) that process them are like the pixel shaders of game audio.</span></span> <span data-ttu-id="87ff5-114">Sie können Signale transformieren, kombinieren oder filtern.</span><span class="sxs-lookup"><span data-stu-id="87ff5-114">They can transform signals, or combine them, or filter them.</span></span> <span data-ttu-id="87ff5-115">Mithilfe der DSP-Programmierung können Sie die Soundeffekte und die Musik Ihres Spiels ganz flexibel und mit der gewünschten Komplexität verändern.</span><span class="sxs-lookup"><span data-stu-id="87ff5-115">By programming to the DSPs, you can alter your game's sound effects and music with as little or as much complexity as you need.</span></span>
-   <span data-ttu-id="87ff5-116">Bei Stimmen handelt es sich um einen Submix aus mindestens zwei Signalen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-116">Voices are the submixed composites of two or more signals.</span></span> <span data-ttu-id="87ff5-117">XAudio2 bietet drei Arten von Stimmobjekten: Quellstimme, Submixstimme und Masterstimme.</span><span class="sxs-lookup"><span data-stu-id="87ff5-117">There are 3 types of XAudio2 voice objects: source, submix, and mastering voices.</span></span> <span data-ttu-id="87ff5-118">Quellstimmen verarbeiten die vom Client bereitgestellten Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="87ff5-118">Source voices operate on audio data provided by the client.</span></span> <span data-ttu-id="87ff5-119">Quell- und Submixstimmen senden ihre Ausgabe an mindestens eine Submix- oder Masterstimme.</span><span class="sxs-lookup"><span data-stu-id="87ff5-119">Source and submix voices send their output to one or more submix or mastering voices.</span></span> <span data-ttu-id="87ff5-120">Submix- und Masterstimmen mischen die Audiodaten aller Stimmen, von denen sie Daten erhalten, und verarbeiten das Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="87ff5-120">Submix and mastering voices mix the audio from all voices feeding them, and operate on the result.</span></span> <span data-ttu-id="87ff5-121">Masterstimmen schreiben Audiodaten auf ein Audiogerät.</span><span class="sxs-lookup"><span data-stu-id="87ff5-121">Mastering voices write audio data to an audio device.</span></span>
-   <span data-ttu-id="87ff5-122">Beim Mixing werden mehrere getrennte Stimmen – beispielsweise die Soundeffekte und die Hintergrundgeräusche einer Szene – in einem einzelnen Stream miteinander kombiniert.</span><span class="sxs-lookup"><span data-stu-id="87ff5-122">Mixing is the process of combining several discrete voices, such as the sound effects and the background audio that are played back in a scene, into a single stream.</span></span> <span data-ttu-id="87ff5-123">Beim Submixing werden mehrere getrennte Signale – beispielsweise die Soundkomponenten eines Motorengeräuschs – zu einer Stimme kombiniert.</span><span class="sxs-lookup"><span data-stu-id="87ff5-123">Submixing is the process of combining several discrete signals, such as the component sounds of an engine noise, and creating a voice.</span></span>
-   <span data-ttu-id="87ff5-124">Audioformate.</span><span class="sxs-lookup"><span data-stu-id="87ff5-124">Audio formats.</span></span> <span data-ttu-id="87ff5-125">Musik und Soundeffekte für Ihr Spiel können in vielen unterschiedlichen digitalen Formaten gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="87ff5-125">Music and sound effects can be stored in a variety of digital formats for your game.</span></span> <span data-ttu-id="87ff5-126">Zur Auswahl stehen unkomprimierte Formate wie WAV sowie komprimierte Formate wie MP3 und OGG.</span><span class="sxs-lookup"><span data-stu-id="87ff5-126">There are uncompressed formats, like WAV, and compressed formats like MP3 and OGG.</span></span> <span data-ttu-id="87ff5-127">Je stärker die Komprimierung eines Audiosamples (üblicherweise abzulesen an der Bitrate), desto schlechter die Klangtreue, da die Verringerung der Bitrate höhere Verluste nach sich zieht.</span><span class="sxs-lookup"><span data-stu-id="87ff5-127">The more a sample is compressed -- typically designated by its bit rate, where the lower the bit rate is, the more lossy the compression -- the worse fidelity it has.</span></span> <span data-ttu-id="87ff5-128">Aufgrund der Klangtreueunterschiede bei verschiedenen Komprimierungsschemas und Bitraten empfiehlt es sich, ein wenig zu experimentieren, um eine möglichst gute Lösung für Ihr Spiel zu finden.</span><span class="sxs-lookup"><span data-stu-id="87ff5-128">Fidelity can vary across compression schemes and bit rates, so experiment with them to find what works best for your game.</span></span>
-   <span data-ttu-id="87ff5-129">Samplingrate und Qualität.</span><span class="sxs-lookup"><span data-stu-id="87ff5-129">Sample rate and quality.</span></span> <span data-ttu-id="87ff5-130">Sound kann unterschiedliche Samplingraten haben. Mit abnehmender Samplingrate verschlechtert sich die Klangtreue allerdings erheblich.</span><span class="sxs-lookup"><span data-stu-id="87ff5-130">Sounds can be sampled at different rates, and sounds sampled at a lower rate have much poorer fidelity.</span></span> <span data-ttu-id="87ff5-131">Die Samplingrate für Sound in CD-Qualität beträgt 44,1kHz (44.100Hz).</span><span class="sxs-lookup"><span data-stu-id="87ff5-131">The sample rate for CD quality is 44.1 Khz (44100 Hz).</span></span> <span data-ttu-id="87ff5-132">Wenn es bei Ihrem Sound nicht auf hohe Klangtreue ankommt, können Sie eine geringere Samplingrate wählen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-132">If you don't need high fidelity for a sound, you can choose a lower sample rate.</span></span> <span data-ttu-id="87ff5-133">Eine höhere Samplingrate empfiehlt sich unter Umständen für professionelle Audioanwendungen, bei einem Spiel ist sie dagegen nicht unbedingt erforderlich – es sei denn, das Spiel benötigt Sound mit professioneller Klangtreue.</span><span class="sxs-lookup"><span data-stu-id="87ff5-133">Higher rates may be appropriate for professional audio applications, but you probably don't need them unless your game demands professional fidelity sound.</span></span>
-   <span data-ttu-id="87ff5-134">Soundquellen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-134">Sound emitters (or sources).</span></span> <span data-ttu-id="87ff5-135">Soundquellen in XAudio2 sind Punkte, von denen Sound ausgeht – ganz gleich, ob es sich dabei um einen Piepton im Hintergrund oder um einen fetzigen Rocksong aus einer Stereoanlage im Spiel handelt.</span><span class="sxs-lookup"><span data-stu-id="87ff5-135">In XAudio2, sound emitters are locations that emit a sound, be it a mere blip of a background noise or a snarling rock track played by an in-game jukebox.</span></span> <span data-ttu-id="87ff5-136">Die Quellen werden anhand von Weltkoordinaten angegeben.</span><span class="sxs-lookup"><span data-stu-id="87ff5-136">You specify emitters by world coordinates.</span></span>
-   <span data-ttu-id="87ff5-137">Soundempfänger.</span><span class="sxs-lookup"><span data-stu-id="87ff5-137">Sound listeners.</span></span> <span data-ttu-id="87ff5-138">Beim Soundempfänger handelt es sich häufig um den Spieler, in aufwendigeren Spielen möglicherweise auch um eine Entität mit künstlicher Intelligenz, die den von einer Soundquelle stammenden Sound verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="87ff5-138">A sound listener is often the player, or perhaps an AI entity in a more advanced game, that processes the sounds received from a listener.</span></span> <span data-ttu-id="87ff5-139">Dieser Sound kann per Submixing dem Audiodatenstrom zugeführt und so für den Spieler wiedergegeben werden. Alternativ können Sie den Sound aber auch verwenden, um eine bestimmte Aktion im Spiel (beispielsweise die Alarmierung einer als Empfänger markierten KI-Wache) auszulösen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-139">You can submix that sound into the audio stream for playback to the player, or you can use it to take a specific in-game action, like awakening an AI guard marked as a listener.</span></span>

## <a name="design-considerations"></a><span data-ttu-id="87ff5-140">Überlegungen bei der Entwicklung</span><span class="sxs-lookup"><span data-stu-id="87ff5-140">Design considerations</span></span>


<span data-ttu-id="87ff5-141">Audio spielt beim Entwerfen und Entwickeln von Spielen eine immens wichtige Rolle.</span><span class="sxs-lookup"><span data-stu-id="87ff5-141">Audio is a tremendously important part of game design and development.</span></span> <span data-ttu-id="87ff5-142">Viele Spieler erinnern sich noch an eher durchschnittliche Spiele, die allein dank ihres einprägsamen Soundtracks, dank großartiger Sprecher und einer tollen Soundabmischung oder allgemein dank einer herausragenden Audioproduktion Kultstatus erreicht haben.</span><span class="sxs-lookup"><span data-stu-id="87ff5-142">Many gamers can recall a mediocre game elevated to legendary status just because of a memorable soundtrack, or great voice work and sound mixing, or overall stellar audio production.</span></span> <span data-ttu-id="87ff5-143">Musik und Sound definieren die Persönlichkeit eines Spiels. Sie liefern auch das Hauptmotiv, das das Spiel definiert und von ähnlichen Spielen abhebt.</span><span class="sxs-lookup"><span data-stu-id="87ff5-143">Music and sound define a game's personality, and establish the main motive that defines the game and makes it stand apart from other similar games.</span></span> <span data-ttu-id="87ff5-144">Der Aufwand, den Sie für die Ausarbeitung und Entwicklung des Audioprofils Ihres Spiel betreiben, zahlt sich in jedem Fall aus.</span><span class="sxs-lookup"><span data-stu-id="87ff5-144">The effort you spend designing and developing your game's audio profile will be well worth it.</span></span>

<span data-ttu-id="87ff5-145">Mit positionsbezogenem 3D-Sound können Sie die 3D-Grafik Ihres Spiels um ein zusätzliches immersives Element erweitern.</span><span class="sxs-lookup"><span data-stu-id="87ff5-145">Positional 3D audio can add a level of immersion beyond that provided by 3D graphics.</span></span> <span data-ttu-id="87ff5-146">Falls Sie ein komplexes Spiel entwickeln, das eine Welt simuliert oder einen filmähnlichen Stil erfordert, sollten Sie die Verwendung von Techniken für positionsbezogenen 3D-Sound in Betracht ziehen, um den Spieler voll und ganz in die Spielwelt eintauchen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-146">If you are developing a complex game that simulates a world, or which demands a cinematic style, consider using 3D positional audio techniques to really draw the player in.</span></span>

## <a name="directx-audio-development-roadmap"></a><span data-ttu-id="87ff5-147">Roadmap für DirectX-Audioentwicklung</span><span class="sxs-lookup"><span data-stu-id="87ff5-147">DirectX audio development roadmap</span></span>


### <a name="xaudio2-conceptual-resources"></a><span data-ttu-id="87ff5-148">Konzeptionelle Ressourcen zu XAudio2</span><span class="sxs-lookup"><span data-stu-id="87ff5-148">XAudio2 conceptual resources</span></span>

<span data-ttu-id="87ff5-149">XAudio2 ist die Audiomixingbibliothek für DirectX, die in erster Linie zum Entwickeln von Audiomodulen mit hoher Leistung für Spiele gedacht ist.</span><span class="sxs-lookup"><span data-stu-id="87ff5-149">XAudio2 is the audio mixing library for DirectX, and is primarily intended for developing high performance audio engines for games.</span></span> <span data-ttu-id="87ff5-150">Spieleentwicklern, die Soundeffekte und Hintergrundmusik zu ihren modernen Spielen hinzufügen möchten, bietet XAudio2 ein Modul für Audiodiagramme und zum Mischen mit geringer Latenz und Unterstützung für dynamische Puffer, synchrone Wiedergabe genau nach Beispiel und implizite Quellratenumwandlung.</span><span class="sxs-lookup"><span data-stu-id="87ff5-150">For game developers who want to add sound effects and background music to their modern games, XAudio2 offers an audio graph and mixing engine with low-latency and support for dynamic buffers, synchronous sample-accurate playback, and implicit source rate conversion.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="87ff5-151">Thema</span><span class="sxs-lookup"><span data-stu-id="87ff5-151">Topic</span></span></th>
<th align="left"><span data-ttu-id="87ff5-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="87ff5-152">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415813"><span data-ttu-id="87ff5-153">Einführung in XAudio2</span><span class="sxs-lookup"><span data-stu-id="87ff5-153">Introduction to XAudio2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-154">Dieses Thema enthält eine Liste der von XAudio2 unterstützten Audioprogrammierfeatures.</span><span class="sxs-lookup"><span data-stu-id="87ff5-154">The topic provides a list of the audio programming features supported by XAudio2.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415762"><span data-ttu-id="87ff5-155">Erste Schritte mit XAudio2</span><span class="sxs-lookup"><span data-stu-id="87ff5-155">Getting Started with XAudio2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-156">Dieses Thema enthält Informationen zu wichtigen XAudio2-Konzepten, XAudio2-Versionen und zum RIFF-Audioformat.</span><span class="sxs-lookup"><span data-stu-id="87ff5-156">This topic provides information on key XAudio2 concepts, XAudio2 versions, and the RIFF audio format.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415692"><span data-ttu-id="87ff5-157">Allgemeine Konzepte für die Audioprogrammierung</span><span class="sxs-lookup"><span data-stu-id="87ff5-157">Common Audio Programming Concepts</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-158">Dieses Thema bietet einen Überblick über allgemeine Audiokonzepte, mit denen ein Audioentwickler vertraut sein sollte.</span><span class="sxs-lookup"><span data-stu-id="87ff5-158">This topic provides an overview of common audio concepts with which an audio developer should be familiar.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415825"><span data-ttu-id="87ff5-159">XAudio2-Stimmen</span><span class="sxs-lookup"><span data-stu-id="87ff5-159">XAudio2 Voices</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-160">Dieses Thema bietet einen Überblick über XAudio2-Stimmen, die für Submixing und das Verarbeiten und Mastern von Audiodaten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="87ff5-160">This topic contains an overview of XAudio2 voices, which are used to submix, operate on, and master audio data.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415745"><span data-ttu-id="87ff5-161">XAudio2-Rückrufe</span><span class="sxs-lookup"><span data-stu-id="87ff5-161">XAudio2 Callbacks</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-162">In diesem Thema werden die XAudio2-Rückrufe behandelt, mit denen Unterbrechungen bei der Audiowiedergabe verhindert werden.</span><span class="sxs-lookup"><span data-stu-id="87ff5-162">This topic covers the XAudio 2 callbacks, which are used to prevent breaks in the audio playback.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415739"><span data-ttu-id="87ff5-163">XAudio2-Audiodiagramme</span><span class="sxs-lookup"><span data-stu-id="87ff5-163">XAudio2 Audio Graphs</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-164">In diesem Thema werden die XAudio2-Audioverarbeitungsdiagramme behandelt. Diese empfangen eine Reihe von Audiostreams vom Client als Eingabe, verarbeiten sie und übergeben das Endergebnis an ein Audiogerät.</span><span class="sxs-lookup"><span data-stu-id="87ff5-164">This topic covers the XAudio2 audio processing graphs, which take a set of audio streams from the client as input, process them, and deliver the final result to an audio device.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415756"><span data-ttu-id="87ff5-165">XAudio2-Audioeffekte</span><span class="sxs-lookup"><span data-stu-id="87ff5-165">XAudio2 Audio Effects</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-166">In diesem Thema werden XAudio2-Audioeffekte behandelt, die eingehende Audiodaten empfangen und vor der Weitergabe bestimmte Vorgänge für die Daten (z.B. einen Halleffekt) ausführen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-166">The topic covers XAudio2 audio effects, which take incoming audio data and perform some operation on the data (such as a reverb effect) before passing it on.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415821"><span data-ttu-id="87ff5-167">Streamen von Audiodaten mit XAudio2</span><span class="sxs-lookup"><span data-stu-id="87ff5-167">Streaming Audio Data with XAudio2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-168">In diesem Thema wird das Audiostreaming mit XAudio2 behandelt.</span><span class="sxs-lookup"><span data-stu-id="87ff5-168">This topic covers audio streaming with XAudio2.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415714"><span data-ttu-id="87ff5-169">X3DAudio</span><span class="sxs-lookup"><span data-stu-id="87ff5-169">X3DAudio</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-170">In diesem Thema wird X3DAudio vorgestellt. Dabei handelt es sich um eine API, die in Verbindung mit XAudio2 verwendet wird, um die Illusion eines 3D-Klangeffekts zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-170">this topic covers X3DAudio, an API used in conjunction with XAudio2 to create the illusion of a sound coming from a point in 3D space.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415899"><span data-ttu-id="87ff5-171">XAudio2-Programmierreferenz</span><span class="sxs-lookup"><span data-stu-id="87ff5-171">XAudio2 Programming Reference</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-172">Dieser Abschnitt enthält die vollständige Referenz für die XAudio2-APIs.</span><span class="sxs-lookup"><span data-stu-id="87ff5-172">This section contains the complete reference for the XAudio2 APIs.</span></span></p></td>
</tr>
</tbody>
</table>

 

### <a name="xaudio2-how-to-resources"></a><span data-ttu-id="87ff5-173">XAudio2-Anleitungsressourcen</span><span class="sxs-lookup"><span data-stu-id="87ff5-173">XAudio2 "how to" resources</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="87ff5-174">Thema</span><span class="sxs-lookup"><span data-stu-id="87ff5-174">Topic</span></span></th>
<th align="left"><span data-ttu-id="87ff5-175">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="87ff5-175">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415779"><span data-ttu-id="87ff5-176">So wird's gemacht: Initialisieren von XAudio2</span><span class="sxs-lookup"><span data-stu-id="87ff5-176">How to: Initialize XAudio2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-177">Hier erfahren Sie, wie Sie XAudio2 für die Audiowiedergabe initialisieren, indem Sie eine Instanz des XAudio2-Moduls und eine Masterstimme erstellen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-177">Learn how to initialize XAudio2 for audio playback by creating an instance of the XAudio2 engine, and creating a mastering voice.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415781"><span data-ttu-id="87ff5-178">So wird's gemacht: Laden von Datendateien in XAudio2</span><span class="sxs-lookup"><span data-stu-id="87ff5-178">How to: Load Audio Data Files in XAudio2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-179">Hier erfahren Sie, wie Sie die zur Wiedergabe von Audiodaten in XAudio2 erforderlichen Strukturen füllen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-179">Learn how to populate the structures required to play audio data in XAudio2.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415787"><span data-ttu-id="87ff5-180">So wird's gemacht: Wiedergeben von Ton mit XAudio2</span><span class="sxs-lookup"><span data-stu-id="87ff5-180">How to: Play a Sound with XAudio2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-181">Hier erfahren Sie, wie Sie zuvor geladene Audiodaten in XAudio2 wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="87ff5-181">Learn how to play previously-loaded audio data in XAudio2.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415794"><span data-ttu-id="87ff5-182">So wird's gemacht: Verwenden von Submixstimmen</span><span class="sxs-lookup"><span data-stu-id="87ff5-182">How to: Use Submix Voices</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-183">Hier erfahren Sie, wie Sie Gruppen von Stimmen festlegen, um ihre Ausgabe an dieselbe Submixstimme zu senden.</span><span class="sxs-lookup"><span data-stu-id="87ff5-183">Learn how to set groups of voices to send their output to the same submix voice.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415769"><span data-ttu-id="87ff5-184">So wird's gemacht: Verwenden der Rückrufe für Quellstimmen</span><span class="sxs-lookup"><span data-stu-id="87ff5-184">How to: Use Source Voice Callbacks</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-185">Hier erfahren Sie, wie Sie die XAudio2-Quellstimmrückrufe verwenden.</span><span class="sxs-lookup"><span data-stu-id="87ff5-185">Learn how to use XAudio2 source voice callbacks.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415774"><span data-ttu-id="87ff5-186">So wird's gemacht: Verwenden der Modulrückrufe</span><span class="sxs-lookup"><span data-stu-id="87ff5-186">How to: Use Engine Callbacks</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-187">Hier erfahren Sie, wie Sie die XAudio2-Modulrückrufe verwenden.</span><span class="sxs-lookup"><span data-stu-id="87ff5-187">Learn how to use XAudio2 engine callbacks.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415767"><span data-ttu-id="87ff5-188">So wird's gemacht: Erstellen eines grundlegenden Audioverarbeitungsdiagramms</span><span class="sxs-lookup"><span data-stu-id="87ff5-188">How to: Build a Basic Audio Processing Graph</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-189">Hier erfahren Sie, wie Sie ein Audioverarbeitungsdiagramm erstellen, das sich aus einer Masterstimme und einer Quellstimme zusammensetzt.</span><span class="sxs-lookup"><span data-stu-id="87ff5-189">Learn how to create an audio processing graph, constructed from a single mastering voice and a single source voice.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415772"><span data-ttu-id="87ff5-190">So wird's gemacht: Dynamisches Hinzufügen und Entfernen von Stimmen zu bzw. aus einem Audiodiagramm</span><span class="sxs-lookup"><span data-stu-id="87ff5-190">How to: Dynamically Add or Remove Voices From an Audio Graph</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-191">Hier erfahren Sie, wie Sie Submixstimmen zu einem Diagramm hinzufügen oder daraus entfernen, das anhand der Schritte unter <a href="https://msdn.microsoft.com/library/windows/desktop/ee415767">So wird's gemacht: Erstellen eines grundlegenden Audioverarbeitungsdiagramms</a> erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="87ff5-191">Learn how to add or remove submix voices from a graph that has been created following the steps in <a href="https://msdn.microsoft.com/library/windows/desktop/ee415767">How to: Build a Basic Audio Processing Graph</a>.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415789"><span data-ttu-id="87ff5-192">So wird's gemacht: Erstellen einer Effektkette</span><span class="sxs-lookup"><span data-stu-id="87ff5-192">How to: Create an Effect Chain</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-193">Hier erfahren Sie, wie Sie eine Effektkette auf eine Stimme anwenden, um die benutzerdefinierte Verarbeitung der Audiodaten für diese Stimme zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-193">Learn how to apply an effect chain to a voice to allow custom processing of the audio data for that voice.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415730"><span data-ttu-id="87ff5-194">So wird's gemacht: Erstellen eines XAPOs</span><span class="sxs-lookup"><span data-stu-id="87ff5-194">How to: Create an XAPO</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-195">Hier erfahren Sie, wie Sie <a href="https://msdn.microsoft.com/library/windows/desktop/ee415893"><strong>IXAPO</strong></a> zum Erstellen eines XAudio2-Audioverarbeitungsobjekts (XAudio2 Audio Processing Object, XAPO) implementieren.</span><span class="sxs-lookup"><span data-stu-id="87ff5-195">Learn how to implement <a href="https://msdn.microsoft.com/library/windows/desktop/ee415893"><strong>IXAPO</strong></a> to create an XAudio2 audio processing object (XAPO).</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415728"><span data-ttu-id="87ff5-196">So wird's gemacht: Hinzufügen der Laufzeitparameterunterstützung zu einem XAPO</span><span class="sxs-lookup"><span data-stu-id="87ff5-196">How to: Add Run-time Parameter Support to an XAPO</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-197">Hier erfahren Sie, wie Sie einem XAPO durch Implementieren der <a href="https://msdn.microsoft.com/library/windows/desktop/ee415896"><strong>IXAPOParameters</strong></a>-Schnittstelle die Laufzeitparameterunterstützung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-197">Learn how to add run-time parameter support to an XAPO by implementing the <a href="https://msdn.microsoft.com/library/windows/desktop/ee415896"><strong>IXAPOParameters</strong></a> interface.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415733"><span data-ttu-id="87ff5-198">So wird's gemacht: Verwenden eines XAPOs in XAudio2</span><span class="sxs-lookup"><span data-stu-id="87ff5-198">How to: Use an XAPO in XAudio2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-199">Hier erfahren Sie, wie Sie einen Effekt verwenden, der als XAPO in einer XAudio2-Effektkette implementiert wurde.</span><span class="sxs-lookup"><span data-stu-id="87ff5-199">Learn how to use an effect implemented as an XAPO in an XAudio2 effect chain.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415723"><span data-ttu-id="87ff5-200">So wird's gemacht: Verwenden von XAPOFX in XAudio2</span><span class="sxs-lookup"><span data-stu-id="87ff5-200">How to: Use XAPOFX in XAudio2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-201">Hier erfahren Sie, wie Sie einen der Effekte in XAPOFX in einer XAudio2-Effektkette verwenden.</span><span class="sxs-lookup"><span data-stu-id="87ff5-201">Learn how to use one of the effects included in XAPOFX in an XAudio2 effect chain.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415791"><span data-ttu-id="87ff5-202">So wird's gemacht: Streamen von Sound von einem Datenträger</span><span class="sxs-lookup"><span data-stu-id="87ff5-202">How to: Stream a Sound from Disk</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-203">Hier erfahren Sie, wie Sie Audiodaten in XAudio2 streamen, indem Sie einen separaten Thread zum Lesen eines Audiopuffers erstellen und diesen Thread mithilfe von Rückrufen steuern.</span><span class="sxs-lookup"><span data-stu-id="87ff5-203">Learn how to stream audio data in XAudio2 by creating a separate thread to read an audio buffer, and to use callbacks to control that thread.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415798"><span data-ttu-id="87ff5-204">So wird's gemacht: Integrieren von X3DAudio in XAudio2</span><span class="sxs-lookup"><span data-stu-id="87ff5-204">How to: Integrate X3DAudio with XAudio2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-205">Hier erfahren Sie, wie Sie mit X3DAudio die Lautstärke- und Tonhöhenwerte für XAudio2-Stimmen sowie die Parameter für den integrierten XAudio2-Halleffekt bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-205">Learn how to use X3DAudio to provide the volume and pitch values for XAudio2 voices as well as the parameters for the XAudio2 built-in reverb effect.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415783"><span data-ttu-id="87ff5-206">So wird's gemacht: Gruppieren von Audiomethoden als Vorgangssatz</span><span class="sxs-lookup"><span data-stu-id="87ff5-206">How to: Group Audio Methods as an Operation Set</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-207">Hier erfahren Sie, wie Sie XAudio2-Vorgangssätze verwenden, damit eine Gruppe von Methodenaufrufen gleichzeitig wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="87ff5-207">Learn how to use XAudio2 operation sets to make a group of method calls take effect at the same time.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee415765"><span data-ttu-id="87ff5-208">Debuggen von Audiostörungen in XAudio2</span><span class="sxs-lookup"><span data-stu-id="87ff5-208">Debugging Audio Glitches in XAudio2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-209">Hier erfahren Sie, wie der Debuggingprotokolliergrad für XAudio2 festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="87ff5-209">Learn how to set the debug logging level for XAudio2.</span></span></p></td>
</tr>
</tbody>
</table>

 

### <a name="media-foundation-resources"></a><span data-ttu-id="87ff5-210">MediaFoundation-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="87ff5-210">Media Foundation resources</span></span>

<span data-ttu-id="87ff5-211">Media Foundation (MF) ist eine Medienplattform zum Streamen von Audio- und Videodaten.</span><span class="sxs-lookup"><span data-stu-id="87ff5-211">Media Foundation (MF) is a media platform for streaming audio and video playback.</span></span> <span data-ttu-id="87ff5-212">Mithilfe der MediaFoundation-APIs können Sie mit verschiedenen Algorithmen codierte und komprimierte Audio- und Videodaten streamen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-212">You can use the Media Foundation APIs to stream audio and video encoded and compressed with a variety of algorithms.</span></span> <span data-ttu-id="87ff5-213">Die Plattform ist nicht für Echtzeitspielszenarien konzipiert. Stattdessen bietet sie leistungsstarke Tools und breite Codec-Unterstützung für eine lineare Aufnahme und Präsentation von Audio- und Videokomponenten.</span><span class="sxs-lookup"><span data-stu-id="87ff5-213">It is not designed for real-time gameplay scenarios; instead, it provides powerful tools and broad codec support for more linear capture and presentation of audio and video components.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="87ff5-214">Thema</span><span class="sxs-lookup"><span data-stu-id="87ff5-214">Topic</span></span></th>
<th align="left"><span data-ttu-id="87ff5-215">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="87ff5-215">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ms696274"><span data-ttu-id="87ff5-216">Info über Media Foundation</span><span class="sxs-lookup"><span data-stu-id="87ff5-216">About Media Foundation</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-217">Dieser Abschnitt enthält allgemeine Informationen zu den MediaFoundation-APIs und die verfügbaren Tools zu ihrer Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="87ff5-217">This section contains general information about the Media Foundation APIs, and the tools available to support them.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ee663601"><span data-ttu-id="87ff5-218">MediaFoundation: Grundlegende Konzepte</span><span class="sxs-lookup"><span data-stu-id="87ff5-218">Media Foundation: Essential Concepts</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-219">In diesem Thema werden einige Konzepte vorgestellt, die Sie vor dem Schreiben einer MediaFoundation-Anwendung kennen müssen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-219">This topic introduces some concepts that you will need to understand before writing a Media Foundation application.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ms696219"><span data-ttu-id="87ff5-220">Media Foundation-Architektur</span><span class="sxs-lookup"><span data-stu-id="87ff5-220">Media Foundation Architecture</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-221">In diesem Abschnitt werden das allgemeine Design von Microsoft Media Foundation sowie die Mediengrundtypen und die verwendete Verarbeitungspipeline beschrieben.</span><span class="sxs-lookup"><span data-stu-id="87ff5-221">This section describes the general design of Microsoft Media Foundation, as well as the media primitives and processing pipeline it uses.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/dd317910"><span data-ttu-id="87ff5-222">Audio-/Videoaufzeichnung</span><span class="sxs-lookup"><span data-stu-id="87ff5-222">Audio/Video Capture</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-223">In diesem Thema wird die Verwendung von Microsoft Media Foundation zum Aufzeichnen von Audio- und Videodaten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="87ff5-223">This topic describes how to use Microsoft Media Foundation to perform audio and video capture.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/dd317914"><span data-ttu-id="87ff5-224">Audio-/Videowiedergabe</span><span class="sxs-lookup"><span data-stu-id="87ff5-224">Audio/Video Playback</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-225">In diesem Thema wird die Implementierung der Audio- oder Videowiedergabe in Ihrer App beschrieben.</span><span class="sxs-lookup"><span data-stu-id="87ff5-225">This topic describes how to implement audio/video playback in your app.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/dd757927"><span data-ttu-id="87ff5-226">Unterstützte Medienformate in MediaFoundation</span><span class="sxs-lookup"><span data-stu-id="87ff5-226">Supported Media Formats in Media Foundation</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-227">In diesem Thema sind die Medienformate aufgeführt, für die Microsoft Media Foundation systemeigene Unterstützung bietet.</span><span class="sxs-lookup"><span data-stu-id="87ff5-227">This topic lists the media formats that Microsoft Media Foundation supports natively.</span></span> <span data-ttu-id="87ff5-228">(Drittanbieter können zusätzliche Formate durch Erstellung benutzerdefinierter Plug-Ins unterstützen.)</span><span class="sxs-lookup"><span data-stu-id="87ff5-228">(Third parties can support additional formats by writing custom plug-ins.)</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/dd318778"><span data-ttu-id="87ff5-229">Codierung und Dateierstellung</span><span class="sxs-lookup"><span data-stu-id="87ff5-229">Encoding and File Authoring</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-230">In diesem Thema wird die Verwendung von Microsoft Media Foundation zum Codieren von Audio- und Videodaten und zum Erstellen von Mediendateien beschrieben.</span><span class="sxs-lookup"><span data-stu-id="87ff5-230">This topic describes how to use Microsoft Media Foundation to perform audio and video encoding, and author media files.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ff819508"><span data-ttu-id="87ff5-231">WindowsMedia-Codecs</span><span class="sxs-lookup"><span data-stu-id="87ff5-231">Windows Media Codecs</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-232">In diesem Thema wird beschrieben, wie Sie mit den Features der WindowsMedia-Codecs für Audio- und Videodaten komprimierte Datenströme erzeugen und wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="87ff5-232">This topic describes how to use the features of the Windows Media Audio and Video codecs to produce and consume compressed data streams.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ms704847"><span data-ttu-id="87ff5-233">MediaFoundation-Programmierreferenz</span><span class="sxs-lookup"><span data-stu-id="87ff5-233">Media Foundation Programming Reference</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-234">Dieser Abschnitt enthält Referenzinformationen für die MediaFoundation-APIs.</span><span class="sxs-lookup"><span data-stu-id="87ff5-234">This section contains reference information for the Media Foundation APIs.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/aa371827"><span data-ttu-id="87ff5-235">MediaFoundation-SDK-Beispiele</span><span class="sxs-lookup"><span data-stu-id="87ff5-235">Media Foundation SDK Samples</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-236">In diesem Abschnitt sind Beispiel-Apps aufgeführt, die die Verwendung von MediaFoundation veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-236">This section lists sample apps that demonstrate how to use Media Foundation.</span></span></p></td>
</tr>
</tbody>
</table>

 

### <a name="windows-runtime-xaml-media-types"></a><span data-ttu-id="87ff5-237">Medientypen der Windows-Runtime-XAML</span><span class="sxs-lookup"><span data-stu-id="87ff5-237">Windows Runtime XAML media types</span></span>

<span data-ttu-id="87ff5-238">Bei Verwendung der [DirectX-XAML-Interoperabilität](https://msdn.microsoft.com/library/windows/apps/hh825871) können die Windows-Runtime-XAML-Medien-APIs für einfachere Spielszenarien mithilfe von DirectX mit C++ in die UWP-Apps integriert werden.</span><span class="sxs-lookup"><span data-stu-id="87ff5-238">If you are using [DirectX-XAML interop](https://msdn.microsoft.com/library/windows/apps/hh825871), you can incorporate the Windows Runtime XAML media APIs into your UWP apps using DirectX with C++ for simpler game scenarios.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="87ff5-239">Thema</span><span class="sxs-lookup"><span data-stu-id="87ff5-239">Topic</span></span></th>
<th align="left"><span data-ttu-id="87ff5-240">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="87ff5-240">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/br242926"><strong><span data-ttu-id="87ff5-241">Windows.UI.Xaml.Controls.MediaElement</span><span class="sxs-lookup"><span data-stu-id="87ff5-241">Windows.UI.Xaml.Controls.MediaElement</span></span></strong></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-242">XAML-Element, das ein Objekt darstellt, das Audio- oder Videodaten oder beide Datentypen enthält.</span><span class="sxs-lookup"><span data-stu-id="87ff5-242">XAML element that represents an object that contains audio, video, or both.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/mt203788"><span data-ttu-id="87ff5-243">Audio, Video und Kamera</span><span class="sxs-lookup"><span data-stu-id="87ff5-243">Audio, video, and camera</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-244">Hier erfahren Sie, wie Sie grundlegende Audio- und Videoinhalte in Ihrer UWP-App (Universelle Windows-Plattform) integrieren.</span><span class="sxs-lookup"><span data-stu-id="87ff5-244">Learn how to incorporate basic audio and video in your Universal Windows Platform (UWP) app.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/mt187272"><span data-ttu-id="87ff5-245">MediaElement</span><span class="sxs-lookup"><span data-stu-id="87ff5-245">MediaElement</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-246">Hier erfahren Sie, wie Sie in Ihrer UWP-App eine lokal gespeicherte Mediendatei wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="87ff5-246">Learn how to play a locally-stored media file in your UWP app.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/mt187272"><span data-ttu-id="87ff5-247">MediaElement</span><span class="sxs-lookup"><span data-stu-id="87ff5-247">MediaElement</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-248">Hier erfahren Sie, wie Sie in Ihrer UWP-App eine Mediendatei mit geringer Wartezeit streamen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-248">Learn how to stream a media file with low-latency in your UWP app.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/mt282143"><span data-ttu-id="87ff5-249">Medienumwandlung</span><span class="sxs-lookup"><span data-stu-id="87ff5-249">Media casting</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="87ff5-250">Hier erfahren Sie, wie Sie mit dem Vertrag für "Wiedergeben auf" Medien aus Ihrer UWP-App auf anderen Geräten streamen.</span><span class="sxs-lookup"><span data-stu-id="87ff5-250">Learn how to use the Play To contract to stream media from your UWP app to another device.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="reference"></a><span data-ttu-id="87ff5-251">Referenz</span><span class="sxs-lookup"><span data-stu-id="87ff5-251">Reference</span></span>


-   [<span data-ttu-id="87ff5-252">XAudio2-Einführung</span><span class="sxs-lookup"><span data-stu-id="87ff5-252">XAudio2 Introduction</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee415813)
-   [<span data-ttu-id="87ff5-253">XAudio2-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="87ff5-253">XAudio2 Programming Guide</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee415737)
-   [<span data-ttu-id="87ff5-254">Übersicht über Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="87ff5-254">Microsoft Media Foundation overview</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)

 

## <a name="related-topics"></a><span data-ttu-id="87ff5-255">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="87ff5-255">Related topics</span></span>


-   [<span data-ttu-id="87ff5-256">XAudio2-Programmieranleitung</span><span class="sxs-lookup"><span data-stu-id="87ff5-256">XAudio2 Programming Guide</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee415737)

 

 




