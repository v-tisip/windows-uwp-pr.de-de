---
author: Karl-Bridge-Microsoft
Description: Learn how to manage issues with speech-recognition accuracy caused by audio-input quality.
title: Verwalten von Problemen bei der Audioeingabe
ms.assetid: 3E36C683-C96A-4FEE-AD52-FDB87E0CC299
label: Manage audio input issues
template: detail.hbs
keywords: Sprache, Stimme, Spracherkennung, natürliche Sprache, diktieren, Eingabe, Benutzerinteraktion
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 094acdbcb5c5b3bf45bad757344be5187ae37cbc
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2018
ms.locfileid: "5994656"
---
# <a name="manage-issues-with-audio-input"></a><span data-ttu-id="5a42e-103">Verwalten von Problemen bei der Audioeingabe</span><span class="sxs-lookup"><span data-stu-id="5a42e-103">Manage issues with audio input</span></span>


<span data-ttu-id="5a42e-104">Erfahren Sie, wie Sie Probleme mit der Genauigkeit der Spracherkennung behandeln, die auf die Qualität der Audioeingabe zurückzuführen sind.</span><span class="sxs-lookup"><span data-stu-id="5a42e-104">Learn how to manage issues with speech-recognition accuracy caused by audio-input quality.</span></span>

> <span data-ttu-id="5a42e-105">**Wichtige APIs**: [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226), [**RecognitionQualityDegrading**](https://msdn.microsoft.com/library/windows/apps/dn653243), [**SpeechRecognitionAudioProblem**](https://msdn.microsoft.com/library/windows/apps/dn631406)</span><span class="sxs-lookup"><span data-stu-id="5a42e-105">**Important APIs**: [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226), [**RecognitionQualityDegrading**](https://msdn.microsoft.com/library/windows/apps/dn653243), [**SpeechRecognitionAudioProblem**](https://msdn.microsoft.com/library/windows/apps/dn631406)</span></span>


## <a name="assess-audio-input-quality"></a><span data-ttu-id="5a42e-106">Bewerten der Qualität der Audioeingabe</span><span class="sxs-lookup"><span data-stu-id="5a42e-106">Assess audio-input quality</span></span>


<span data-ttu-id="5a42e-107">Wenn die Spracherkennung aktiviert ist, verwenden Sie das [**RecognitionQualityDegrading**](https://msdn.microsoft.com/library/windows/apps/dn653243)-Ereignis Ihrer Spracherkennung, um festzustellen, ob Audioprobleme die Spracheingabe stören.</span><span class="sxs-lookup"><span data-stu-id="5a42e-107">When speech recognition is active, use the [**RecognitionQualityDegrading**](https://msdn.microsoft.com/library/windows/apps/dn653243) event of your speech recognizer to determine whether one or more audio issues might be interfering with speech input.</span></span> <span data-ttu-id="5a42e-108">Das Ereignisargument ([**SpeechRecognitionQualityDegradingEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn631430)) enthält die [**Problem**](https://msdn.microsoft.com/library/windows/apps/dn631431)-Eigenschaft, die die Probleme mit der Audioeingabe aufzeigt.</span><span class="sxs-lookup"><span data-stu-id="5a42e-108">The event argument ([**SpeechRecognitionQualityDegradingEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn631430)) provides the [**Problem**](https://msdn.microsoft.com/library/windows/apps/dn631431) property, which describes the issues detected with the audio input.</span></span>

<span data-ttu-id="5a42e-109">Die Erkennung kann durch zu viele Hintergrundgeräusche, eine Stummschaltung des Mikrofons und die Lautstärke oder Geschwindigkeit des Lautsprechers beeinflusst werden.</span><span class="sxs-lookup"><span data-stu-id="5a42e-109">Recognition can be affected by too much background noise, a muted microphone, and the volume or speed of the speaker.</span></span>

<span data-ttu-id="5a42e-110">Hier konfigurieren wir eine Spracherkennung und beginnen, auf das [**RecognitionQualityDegrading**](https://msdn.microsoft.com/library/windows/apps/dn653243)-Ereignis zu lauschen.</span><span class="sxs-lookup"><span data-stu-id="5a42e-110">Here, we configure a speech recognizer and start listening for the [**RecognitionQualityDegrading**](https://msdn.microsoft.com/library/windows/apps/dn653243) event.</span></span>

```CSharp
private async void WeatherSearch_Click(object sender, RoutedEventArgs e)
{
    // Create an instance of SpeechRecognizer.
    var speechRecognizer = new Windows.Media.SpeechRecognition.SpeechRecognizer();

    // Listen for audio input issues.
    speechRecognizer.RecognitionQualityDegrading += speechRecognizer_RecognitionQualityDegrading;

    // Add a web search grammar to the recognizer.
    var webSearchGrammar = new Windows.Media.SpeechRecognition.SpeechRecognitionTopicConstraint(Windows.Media.SpeechRecognition.SpeechRecognitionScenario.WebSearch, "webSearch");


    speechRecognizer.UIOptions.AudiblePrompt = "Say what you want to search for...";
    speechRecognizer.UIOptions.ExampleText = "Ex. 'weather for London'";
    speechRecognizer.Constraints.Add(webSearchGrammar);

    // Compile the constraint.
    await speechRecognizer.CompileConstraintsAsync();

    // Start recognition.
    Windows.Media.SpeechRecognition.SpeechRecognitionResult speechRecognitionResult = await speechRecognizer.RecognizeWithUIAsync();
    //await speechRecognizer.RecognizeWithUIAsync();

    // Do something with the recognition result.
    var messageDialog = new Windows.UI.Popups.MessageDialog(speechRecognitionResult.Text, "Text spoken");
    await messageDialog.ShowAsync();
}
```

## <a name="manage-the-speech-recognition-experience"></a><span data-ttu-id="5a42e-111">Verwalten der Spracherkennungsfunktion</span><span class="sxs-lookup"><span data-stu-id="5a42e-111">Manage the speech-recognition experience</span></span>


<span data-ttu-id="5a42e-112">Mit der bereitgestellten Beschreibung der [**Problem**](https://msdn.microsoft.com/library/windows/apps/dn631431)-Eigenschaft können die Benutzer die Bedingungen für die Spracherkennung verbessern.</span><span class="sxs-lookup"><span data-stu-id="5a42e-112">Use the description provided by the [**Problem**](https://msdn.microsoft.com/library/windows/apps/dn631431) property to help the user improve conditions for recognition.</span></span>

<span data-ttu-id="5a42e-113">Hier erstellen wir einen Handler für das [**RecognitionQualityDegrading**](https://msdn.microsoft.com/library/windows/apps/dn653243)-Ereignis, der überprüft, ob die Lautstärke niedrig ist.</span><span class="sxs-lookup"><span data-stu-id="5a42e-113">Here, we create a handler for the [**RecognitionQualityDegrading**](https://msdn.microsoft.com/library/windows/apps/dn653243) event that checks for a low volume level.</span></span> <span data-ttu-id="5a42e-114">Anschließend verwenden wir ein [**SpeechSynthesizer**](https://msdn.microsoft.com/library/windows/apps/dn298152)-Objekt, um den Benutzer aufzufordern, lauter zu sprechen.</span><span class="sxs-lookup"><span data-stu-id="5a42e-114">We then use a [**SpeechSynthesizer**](https://msdn.microsoft.com/library/windows/apps/dn298152) object to suggest that the user try speaking louder.</span></span>

```CSharp
private async void speechRecognizer_RecognitionQualityDegrading(
    Windows.Media.SpeechRecognition.SpeechRecognizer sender,
    Windows.Media.SpeechRecognition.SpeechRecognitionQualityDegradingEventArgs args)
{
    // Create an instance of a speech synthesis engine (voice).
    var speechSynthesizer =
        new Windows.Media.SpeechSynthesis.SpeechSynthesizer();

    // If input speech is too quiet, prompt the user to speak louder.
    if (args.Problem == Windows.Media.SpeechRecognition.SpeechRecognitionAudioProblem.TooQuiet)
    {
        // Generate the audio stream from plain text.
        Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream;
        try
        {
            stream = await speechSynthesizer.SynthesizeTextToStreamAsync("Try speaking louder");
            stream.Seek(0);
        }
        catch (Exception)
        {
            stream = null;
        }

        // Send the stream to the MediaElement declared in XAML.
        await CoreApplication.MainView.CoreWindow.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.High, () =>
        {
            this.media.SetSource(stream, stream.ContentType);
        });
    }
}
```

## <a name="related-articles"></a><span data-ttu-id="5a42e-115">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="5a42e-115">Related articles</span></span>


* [<span data-ttu-id="5a42e-116">Sprachinteraktionen</span><span class="sxs-lookup"><span data-stu-id="5a42e-116">Speech interactions</span></span>](speech-interactions.md)

**<span data-ttu-id="5a42e-117">Beispiele</span><span class="sxs-lookup"><span data-stu-id="5a42e-117">Samples</span></span>**
* [<span data-ttu-id="5a42e-118">Beispiel zu Spracherkennung und Sprachsynthese</span><span class="sxs-lookup"><span data-stu-id="5a42e-118">Speech recognition and speech synthesis sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619897)
 

 




