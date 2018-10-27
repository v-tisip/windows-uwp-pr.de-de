---
author: Karl-Bridge-Microsoft
Description: Learn how to capture and recognize long-form, continuous dictation speech input.
title: Aktivieren des kontinuierlichen Diktierens
ms.assetid: 383B3E23-1678-4FBB-B36E-6DE2DA9CA9DC
label: Continuous dictation
template: detail.hbs
keywords: Sprache, Stimme, Spracherkennung, natürliche Sprache, diktieren, Eingabe, Benutzerinteraktion
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: ea7c0b92c5900e468023dd5b972942a89c2833c3
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5686915"
---
# <a name="continuous-dictation"></a><span data-ttu-id="214cf-103">Kontinuierliches Diktieren</span><span class="sxs-lookup"><span data-stu-id="214cf-103">Continuous dictation</span></span>

<span data-ttu-id="214cf-104">Hier erfahren Sie, wie Sie die Erfassung und Erkennung langer Spracheingaben für kontinuierliches Diktieren ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="214cf-104">Learn how to capture and recognize long-form, continuous dictation speech input.</span></span>

> <span data-ttu-id="214cf-105">**Wichtige APIs**: [**SpeechContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913896), [**ContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913913)</span><span class="sxs-lookup"><span data-stu-id="214cf-105">**Important APIs**: [**SpeechContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913896), [**ContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913913)</span></span>

<span data-ttu-id="214cf-106">In [Spracherkennung](speech-recognition.md) haben Sie gelernt, wie Sie mithilfe der Methoden [**RecognizeAsync**](https://msdn.microsoft.com/library/windows/apps/dn653244) oder [**RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245) eines [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226)-Objekts verhältnismäßig kurze Spracheingaben erfassen und erkennen. Beispiele hierfür sind das Verfassen einer SMS oder das Stellen einer Frage.</span><span class="sxs-lookup"><span data-stu-id="214cf-106">In [Speech recognition](speech-recognition.md), you learned how to capture and recognize relatively short speech input using the [**RecognizeAsync**](https://msdn.microsoft.com/library/windows/apps/dn653244) or [**RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245) methods of a [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) object, for example, when composing a short message service (SMS) message or when asking a question.</span></span>

<span data-ttu-id="214cf-107">Bei längeren, kontinuierlichen Spracherkennungssitzungen (z.B. für Diktate oder E-Mails) wird hingegen die [**ContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913913)-Eigenschaft eines [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226)-Objekts verwendet, um ein [**SpeechContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913896)-Objekt zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="214cf-107">For longer, continuous speech recognition sessions, such as dictation or email, use the [**ContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913913) property of a [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) to obtain a [**SpeechContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913896) object.</span></span>

> [!NOTE]
> <span data-ttu-id="214cf-108">Diktat sprachunterstützung hängt davon ab, auf dem [Gerät](https://docs.microsoft.com/windows/uwp/design/devices/) , in denen Ihre app ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="214cf-108">Dictation language support depends on the [device](https://docs.microsoft.com/windows/uwp/design/devices/) where your app is running.</span></span> <span data-ttu-id="214cf-109">Für PCs und Laptops wird nur "En-US" erkannt, während die Xbox und Telefone alle von der Spracherkennung unterstützte Sprachen erkennen können.</span><span class="sxs-lookup"><span data-stu-id="214cf-109">For PCs and laptops, only en-US is recognized, while Xbox and phones can recognize all languages supported by speech recognition.</span></span> <span data-ttu-id="214cf-110">Weitere Informationen finden Sie unter [der Spracherkennungssprache angeben](specify-the-speech-recognizer-language.md).</span><span class="sxs-lookup"><span data-stu-id="214cf-110">For more info, see [Specify the speech recognizer language](specify-the-speech-recognizer-language.md).</span></span>

## <a name="set-up"></a><span data-ttu-id="214cf-111">Einrichtung</span><span class="sxs-lookup"><span data-stu-id="214cf-111">Set up</span></span>

<span data-ttu-id="214cf-112">Zum Verwalten einer kontinuierlichen Diktiersitzung benötigt Ihre App einige Objekte:</span><span class="sxs-lookup"><span data-stu-id="214cf-112">Your app needs a few objects to manage a continuous dictation session:</span></span>

- <span data-ttu-id="214cf-113">Eine Instanz eines [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226)-Objekts.</span><span class="sxs-lookup"><span data-stu-id="214cf-113">An instance of a [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) object.</span></span>
- <span data-ttu-id="214cf-114">Einen Verweis auf einen UI-Verteiler zum Aktualisieren der Benutzeroberfläche während des Diktierens.</span><span class="sxs-lookup"><span data-stu-id="214cf-114">A reference to a UI dispatcher to update the UI during dictation.</span></span>
- <span data-ttu-id="214cf-115">Eine Möglichkeit zum Nachverfolgen der kumulierten, vom Benutzer gesprochenen Wörter.</span><span class="sxs-lookup"><span data-stu-id="214cf-115">A way to track the accumulated words spoken by the user.</span></span>

<span data-ttu-id="214cf-116">Hier wird eine [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226)-Instanz als privates Feld der CodeBehind-Klasse deklariert.</span><span class="sxs-lookup"><span data-stu-id="214cf-116">Here, we declare a [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) instance as a private field of the code-behind class.</span></span> <span data-ttu-id="214cf-117">Ihre App muss an einem anderen Ort einen Verweis speichern, wenn das fortlaufende Diktat nicht nur auf einer einzelnen XAML-Seite (Extensible Application Markup Language) Bestand haben soll.</span><span class="sxs-lookup"><span data-stu-id="214cf-117">Your app needs to store a reference elsewhere if you want continuous dictation to persist beyond a single Extensible Application Markup Language (XAML) page.</span></span>

```CSharp
private SpeechRecognizer speechRecognizer;
```

<span data-ttu-id="214cf-118">Während des Diktats löst die Erkennung über einen Hintergrundthread Ereignisse aus.</span><span class="sxs-lookup"><span data-stu-id="214cf-118">During dictation, the recognizer raises events from a background thread.</span></span> <span data-ttu-id="214cf-119">Da die Benutzeroberfläche in XAML nicht direkt von einem Hintergrundthread aktualisiert werden kann, muss Ihre App die Benutzeroberfläche mithilfe eines Verteilers auf der Grundlage von Erkennungsereignissen aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="214cf-119">Because a background thread cannot directly update the UI in XAML, your app must use a dispatcher to update the UI in response to recognition events.</span></span>

<span data-ttu-id="214cf-120">Hier deklarieren wir ein privates Feld, das später mit dem UI-Verteiler initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="214cf-120">Here, we declare a private field that will be initialized later with the UI dispatcher.</span></span>

```CSharp
// Speech events may originate from a thread other than the UI thread.
// Keep track of the UI thread dispatcher so that we can update the
// UI in a thread-safe manner.
private CoreDispatcher dispatcher;
```

<span data-ttu-id="214cf-121">Zur Nachverfolgung der Spracheingaben des Benutzers müssen die von der Spracherkennung ausgelösten Erkennungsereignisse behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="214cf-121">To track what the user is saying, you need to handle recognition events raised by the speech recognizer.</span></span> <span data-ttu-id="214cf-122">Diese Ereignisse liefern die Erkennungsergebnisse für die einzelnen Äußerungen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="214cf-122">These events provide the recognition results for chunks of user utterances.</span></span>

<span data-ttu-id="214cf-123">Hier wird ein [**StringBuilder**](https://msdn.microsoft.com/library/system.text.stringbuilder.aspx)-Objekt zum Speichern aller Erkennungsergebnisse der Sitzung verwendet.</span><span class="sxs-lookup"><span data-stu-id="214cf-123">Here, we use a [**StringBuilder**](https://msdn.microsoft.com/library/system.text.stringbuilder.aspx) object to hold all the recognition results obtained during the session.</span></span> <span data-ttu-id="214cf-124">Neue Ergebnisse werden während der Verarbeitung an das **StringBuilder**-Objekt angehängt.</span><span class="sxs-lookup"><span data-stu-id="214cf-124">New results are appended to the **StringBuilder** as they are processed.</span></span>

```CSharp
private StringBuilder dictatedTextBuilder;
```

## <a name="initialization"></a><span data-ttu-id="214cf-125">Initialisierung</span><span class="sxs-lookup"><span data-stu-id="214cf-125">Initialization</span></span>

<span data-ttu-id="214cf-126">Während der Initialisierung der kontinuierlichen Spracherkennung müssen folgende Schritte ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="214cf-126">During the initialization of continuous speech recognition, you must:</span></span>

- <span data-ttu-id="214cf-127">Abrufen des Verteilers für den UI-Thread, wenn Sie die Benutzeroberfläche Ihrer App in den Ereignishandlern für die kontinuierliche Erkennung aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="214cf-127">Fetch the dispatcher for the UI thread if you update the UI of your app in the continuous recognition event handlers.</span></span>
- <span data-ttu-id="214cf-128">Initialisieren der Spracherkennung.</span><span class="sxs-lookup"><span data-stu-id="214cf-128">Initialize the speech recognizer.</span></span>
- <span data-ttu-id="214cf-129">Kompilieren der integrierten Diktiergrammatik.</span><span class="sxs-lookup"><span data-stu-id="214cf-129">Compile the built-in dictation grammar.</span></span>
    <span data-ttu-id="214cf-130">**Hinweis:**  die Spracherkennung benötigt mindestens eine Einschränkung, um erkennbares Vokabular zu definieren.</span><span class="sxs-lookup"><span data-stu-id="214cf-130">**Note** Speech recognition requires at least one constraint to define a recognizable vocabulary.</span></span> <span data-ttu-id="214cf-131">Wenn Sie keine Einschränkung angeben, wird eine vordefinierte Diktiergrammatik verwendet.</span><span class="sxs-lookup"><span data-stu-id="214cf-131">If no constraint is specified, a predefined dictation grammar is used.</span></span> <span data-ttu-id="214cf-132">Siehe [Spracherkennung](speech-recognition.md).</span><span class="sxs-lookup"><span data-stu-id="214cf-132">See [Speech recognition](speech-recognition.md).</span></span>
- <span data-ttu-id="214cf-133">Einrichten der Listener für Erkennungsereignisse.</span><span class="sxs-lookup"><span data-stu-id="214cf-133">Set up the event listeners for recognition events.</span></span>

<span data-ttu-id="214cf-134">In diesem Beispiel wird die Spracherkennung im [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508)-Seitenereignis initialisiert.</span><span class="sxs-lookup"><span data-stu-id="214cf-134">In this example, we initialize speech recognition in the [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508) page event.</span></span>

1. <span data-ttu-id="214cf-135">Da die von der Spracherkennung ausgelösten Ereignisse in einem Hintergrundthread auftreten, muss für die Aktualisierung des UI-Threads ein Verweis auf den Verteiler erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="214cf-135">Because events raised by the speech recognizer occur on a background thread, create a reference to the dispatcher for updates to the UI thread.</span></span> <span data-ttu-id="214cf-136">[**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508) wird stets im UI-Thread aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="214cf-136">[**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508) is always invoked on the UI thread.</span></span>
```csharp
this.dispatcher = CoreWindow.GetForCurrentThread().Dispatcher;
```

2.  <span data-ttu-id="214cf-137">Anschließend wird die [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226)-Instanz initialisiert.</span><span class="sxs-lookup"><span data-stu-id="214cf-137">We then initialize the [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) instance.</span></span>
```csharp
this.speechRecognizer = new SpeechRecognizer();
```

3.  <span data-ttu-id="214cf-138">Anschließend wird die Grammatik hinzugefügt, die alle Wörter und Ausdrücke definiert, die von [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) erkannt werden können, und kompiliert.</span><span class="sxs-lookup"><span data-stu-id="214cf-138">We then add and compile the grammar that defines all of the words and phrases that can be recognized by the [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226).</span></span>

    <span data-ttu-id="214cf-139">Wenn Sie nicht explizit eine Grammatik angeben, wird standardmäßig eine vordefinierte Grammatik verwendet.</span><span class="sxs-lookup"><span data-stu-id="214cf-139">If you don't specify a grammar explicitly, a predefined dictation grammar is used by default.</span></span> <span data-ttu-id="214cf-140">Die Standardgrammatik eignet sich in der Regel am besten für allgemeines Diktieren.</span><span class="sxs-lookup"><span data-stu-id="214cf-140">Typically, the default grammar is best for general dictation.</span></span>

    <span data-ttu-id="214cf-141">Hier wird [**CompileConstraintsAsync**](https://msdn.microsoft.com/library/windows/apps/dn653240) direkt aufgerufen, ohne eine Grammatik hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="214cf-141">Here, we call [**CompileConstraintsAsync**](https://msdn.microsoft.com/library/windows/apps/dn653240) immediately without adding a grammar.</span></span>

    
```csharp
SpeechRecognitionCompilationResult result =
      await speechRecognizer.CompileConstraintsAsync();
```

## <a name="handle-recognition-events"></a><span data-ttu-id="214cf-142">Behandeln von Erkennungsereignissen</span><span class="sxs-lookup"><span data-stu-id="214cf-142">Handle recognition events</span></span>

<span data-ttu-id="214cf-143">Sie können durch Aufrufen von [**RecognizeAsync**](https://msdn.microsoft.com/library/windows/apps/dn653244) oder [**RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245) eine einzelne kurze Äußerung oder Phrase erfassen.</span><span class="sxs-lookup"><span data-stu-id="214cf-143">You can capture a single, brief utterance or phrase by calling [**RecognizeAsync**](https://msdn.microsoft.com/library/windows/apps/dn653244) or [**RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245).</span></span> 

<span data-ttu-id="214cf-144">Um jedoch eine längere, kontinuierliche Erkennungssitzung zu erfassen, werden Ereignislistener angegeben, die im Hintergrund ausgeführt werden, während der Benutzer spricht, und Handler für die Erstellung der Diktatzeichenfolge definiert.</span><span class="sxs-lookup"><span data-stu-id="214cf-144">However, to capture a longer, continuous recognition session, we specify event listeners to run in the background as the user speaks and define handlers to build the dictation string.</span></span>

<span data-ttu-id="214cf-145">Anschließend wird die [**ContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913913)-Eigenschaft unserer Erkennung verwendet, um ein [**SpeechContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913896)-Objekt zu erhalten, das Methoden und Ereignisse für die Verwaltung einer kontinuierlichen Erkennungssitzung bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="214cf-145">We then use the [**ContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913913) property of our recognizer to obtain a [**SpeechContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913896) object that provides methods and events for managing a continuous recognition session.</span></span>

<span data-ttu-id="214cf-146">Zwei Ereignisse sind besonders wichtig:</span><span class="sxs-lookup"><span data-stu-id="214cf-146">Two events in particular are critical:</span></span>

- <span data-ttu-id="214cf-147">[**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) tritt ein, wenn die Erkennung Ergebnisse generiert hat.</span><span class="sxs-lookup"><span data-stu-id="214cf-147">[**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900), which occurs when the recognizer has generated some results.</span></span>
- <span data-ttu-id="214cf-148">[**Completed**](https://msdn.microsoft.com/library/windows/apps/dn913899) tritt ein, wenn die kontinuierliche Erkennungssitzung beendet ist.</span><span class="sxs-lookup"><span data-stu-id="214cf-148">[**Completed**](https://msdn.microsoft.com/library/windows/apps/dn913899), which occurs when the continuous recognition session has ended.</span></span>

<span data-ttu-id="214cf-149">Das [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900)-Ereignis wird ausgelöst, während der Benutzer spricht.</span><span class="sxs-lookup"><span data-stu-id="214cf-149">The [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) event is raised as the user speaks.</span></span> <span data-ttu-id="214cf-150">Die Erkennung hört kontinuierlich auf den Benutzer und löst in regelmäßigen Abständen ein Ereignis aus, das einen Teil der Spracheingabe übergibt.</span><span class="sxs-lookup"><span data-stu-id="214cf-150">The recognizer continuously listens to the user and periodically raises an event that passes a chunk of speech input.</span></span> <span data-ttu-id="214cf-151">Die Spracheingabe muss mit der [**Result**](https://msdn.microsoft.com/library/windows/apps/dn913895)-Eigenschaft des Ereignisarguments untersucht werden. Außerdem muss im Ereignishandler eine geeignete Aktion ausgeführt werden, um den Text beispielsweise einem StringBuilder-Objekt anzufügen.</span><span class="sxs-lookup"><span data-stu-id="214cf-151">You must examine the speech input, using the [**Result**](https://msdn.microsoft.com/library/windows/apps/dn913895) property of the event argument, and take appropriate action in the event handler, such as appending the text to a StringBuilder object.</span></span>

<span data-ttu-id="214cf-152">Als Instanz von [**SpeechRecognitionResult**](https://msdn.microsoft.com/library/windows/apps/dn631432) ist die Eigenschaft [**Result**](https://msdn.microsoft.com/library/windows/apps/dn913895) nützlich, um zu ermitteln, ob die Spracheingabe akzeptiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="214cf-152">As an instance of [**SpeechRecognitionResult**](https://msdn.microsoft.com/library/windows/apps/dn631432), the [**Result**](https://msdn.microsoft.com/library/windows/apps/dn913895) property is useful for determining whether you want to accept the speech input.</span></span> <span data-ttu-id="214cf-153">[**SpeechRecognitionResult**](https://msdn.microsoft.com/library/windows/apps/dn631432) stellt hierfür zwei Eigenschaften bereit:</span><span class="sxs-lookup"><span data-stu-id="214cf-153">A [**SpeechRecognitionResult**](https://msdn.microsoft.com/library/windows/apps/dn631432) provides two properties for this:</span></span>

- <span data-ttu-id="214cf-154">[**Status**](https://msdn.microsoft.com/library/windows/apps/dn631440) gibt an, ob die Erkennung erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="214cf-154">[**Status**](https://msdn.microsoft.com/library/windows/apps/dn631440) indicates whether the recognition was successful.</span></span> <span data-ttu-id="214cf-155">Die Erkennung kann aus unterschiedlichen Gründen scheitern.</span><span class="sxs-lookup"><span data-stu-id="214cf-155">Recognition can fail for a variety of reasons.</span></span>
- <span data-ttu-id="214cf-156">[**Confidence**](https://msdn.microsoft.com/library/windows/apps/dn631434) gibt die relative Wahrscheinlichkeit dafür an, dass die Wörter von der Erkennung korrekt verstanden wurden.</span><span class="sxs-lookup"><span data-stu-id="214cf-156">[**Confidence**](https://msdn.microsoft.com/library/windows/apps/dn631434) indicates the relative confidence that the recognizer understood the correct words.</span></span>

<span data-ttu-id="214cf-157">Dies sind die grundlegenden Schritte für die kontinuierliche Erkennung:</span><span class="sxs-lookup"><span data-stu-id="214cf-157">Here are the basic steps for supporting continuous recognition:</span></span>  

1. <span data-ttu-id="214cf-158">Hier wird der Handler für das kontinuierliche [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900)-Erkennungsereignis im [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508)-Seitenereignis registriert.</span><span class="sxs-lookup"><span data-stu-id="214cf-158">Here, we register the handler for the [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) continuous recognition event in the [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508) page event.</span></span>
```csharp
speechRecognizer.ContinuousRecognitionSession.ResultGenerated +=
        ContinuousRecognitionSession_ResultGenerated;
```

2.  <span data-ttu-id="214cf-159">Anschließend wird die Eigenschaft [**Confidence**](https://msdn.microsoft.com/library/windows/apps/dn631434) überprüft.</span><span class="sxs-lookup"><span data-stu-id="214cf-159">We then check the [**Confidence**](https://msdn.microsoft.com/library/windows/apps/dn631434) property.</span></span> <span data-ttu-id="214cf-160">Wenn der Wert von Confidence [**Medium**](https://msdn.microsoft.com/library/windows/apps/dn631409) oder besser ist, wird der Text an das StringBuilder-Objekt angefügt.</span><span class="sxs-lookup"><span data-stu-id="214cf-160">If the value of Confidence is [**Medium**](https://msdn.microsoft.com/library/windows/apps/dn631409) or better, we append the text to the StringBuilder.</span></span> <span data-ttu-id="214cf-161">Während der Eingabeerfassung wird auch die Benutzeroberfläche aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="214cf-161">We also update the UI as we collect input.</span></span>

    <span data-ttu-id="214cf-162">**Hinweis:** das [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) -Ereignis wird ausgelöst, in einem Hintergrundthread, die die Benutzeroberfläche nicht direkt aktualisieren kann.</span><span class="sxs-lookup"><span data-stu-id="214cf-162">**Note**the [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) event is raised on a background thread that cannot update the UI directly.</span></span> <span data-ttu-id="214cf-163">Wenn ein Handler die UI aktualisieren muss (wie dies beim \[Sprach- und TTS-Beispiel\] der Fall ist), müssen die Aktualisierungen über die [**RunAsync**](https://msdn.microsoft.com/library/windows/apps/hh750317)-Methode des Verteilers an den UI-Thread übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="214cf-163">If a handler needs to update the UI (as the \[Speech and TTS sample\] does), you must dispatch the updates to the UI thread through the [**RunAsync**](https://msdn.microsoft.com/library/windows/apps/hh750317) method of the dispatcher.</span></span>
```csharp
private async void ContinuousRecognitionSession_ResultGenerated(
      SpeechContinuousRecognitionSession sender,
      SpeechContinuousRecognitionResultGeneratedEventArgs args)
      {

        if (args.Result.Confidence == SpeechRecognitionConfidence.Medium ||
          args.Result.Confidence == SpeechRecognitionConfidence.High)
          {
            dictatedTextBuilder.Append(args.Result.Text + " ");

            await dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
            {
              dictationTextBox.Text = dictatedTextBuilder.ToString();
              btnClearText.IsEnabled = true;
            });
          }
        else
        {
          await dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
            {
              dictationTextBox.Text = dictatedTextBuilder.ToString();
            });
        }
      }
```

3.  <span data-ttu-id="214cf-164">Anschließend wird das [**Completed**](https://msdn.microsoft.com/library/windows/apps/dn913899)-Ereignis behandelt, das das Ende des kontinuierlichen Diktierens angibt.</span><span class="sxs-lookup"><span data-stu-id="214cf-164">We then handle the [**Completed**](https://msdn.microsoft.com/library/windows/apps/dn913899) event, which indicates the end of continuous dictation.</span></span>

    <span data-ttu-id="214cf-165">Die Sitzung endet durch Aufrufen der Methoden [**StopAsync**](https://msdn.microsoft.com/library/windows/apps/dn913908) oder [**CancelAsync**](https://msdn.microsoft.com/library/windows/apps/dn913898) (wie im nächsten Abschnitt beschrieben).</span><span class="sxs-lookup"><span data-stu-id="214cf-165">The session ends when you call the [**StopAsync**](https://msdn.microsoft.com/library/windows/apps/dn913908) or [**CancelAsync**](https://msdn.microsoft.com/library/windows/apps/dn913898) methods (described the next section).</span></span> <span data-ttu-id="214cf-166">Die Sitzung kann auch beendet werden, wenn ein Fehler auftritt oder der Benutzer nicht mehr spricht.</span><span class="sxs-lookup"><span data-stu-id="214cf-166">The session can also end when an error occurs, or when the user has stopped speaking.</span></span> <span data-ttu-id="214cf-167">Überprüfen Sie die [**Status**](https://msdn.microsoft.com/library/windows/apps/dn631440)-Eigenschaft des Ereignisarguments, um den Grund für die Sitzungsbeendigung zu ermitteln ([**SpeechRecognitionResultStatus**](https://msdn.microsoft.com/library/windows/apps/dn631433)).</span><span class="sxs-lookup"><span data-stu-id="214cf-167">Check the [**Status**](https://msdn.microsoft.com/library/windows/apps/dn631440) property of the event argument to determine why the session ended ([**SpeechRecognitionResultStatus**](https://msdn.microsoft.com/library/windows/apps/dn631433)).</span></span>

    <span data-ttu-id="214cf-168">Hier wird der Handler für das kontinuierliche [**Completed**](https://msdn.microsoft.com/library/windows/apps/dn913899)-Erkennungsereignis im [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508)-Seitenereignis registriert.</span><span class="sxs-lookup"><span data-stu-id="214cf-168">Here, we register the handler for the [**Completed**](https://msdn.microsoft.com/library/windows/apps/dn913899) continuous recognition event in the [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508) page event.</span></span>
```csharp
speechRecognizer.ContinuousRecognitionSession.Completed +=
      ContinuousRecognitionSession_Completed;
```

4.  <span data-ttu-id="214cf-169">Der Ereignishandler überprüft die Status-Eigenschaft, um zu ermitteln, ob die Erkennung erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="214cf-169">The event handler checks the Status property to determine whether the recognition was successful.</span></span> <span data-ttu-id="214cf-170">Er behandelt auch den Fall, dass ein Benutzer nicht mehr spricht.</span><span class="sxs-lookup"><span data-stu-id="214cf-170">It also handles the case where the user has stopped speaking.</span></span> <span data-ttu-id="214cf-171">Häufig wird [**TimeoutExceeded**](https://msdn.microsoft.com/library/windows/apps/dn631433) als erfolgreiche Erkennung betrachtet, da der Benutzer aufgehört hat, zu sprechen.</span><span class="sxs-lookup"><span data-stu-id="214cf-171">Often, a [**TimeoutExceeded**](https://msdn.microsoft.com/library/windows/apps/dn631433) is considered successful recognition as it means the user has finished speaking.</span></span> <span data-ttu-id="214cf-172">Behandeln Sie diesen Fall in Ihrem Code, um die Benutzerfreundlichkeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="214cf-172">You should handle this case in your code for a good experience.</span></span>

    <span data-ttu-id="214cf-173">**Hinweis:** das [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) -Ereignis wird ausgelöst, in einem Hintergrundthread, die die Benutzeroberfläche nicht direkt aktualisieren kann.</span><span class="sxs-lookup"><span data-stu-id="214cf-173">**Note**the [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) event is raised on a background thread that cannot update the UI directly.</span></span> <span data-ttu-id="214cf-174">Wenn ein Handler die UI aktualisieren muss (wie dies beim \[Sprach- und TTS-Beispiel\] der Fall ist), müssen die Aktualisierungen über die [**RunAsync**](https://msdn.microsoft.com/library/windows/apps/hh750317)-Methode des Verteilers an den UI-Thread übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="214cf-174">If a handler needs to update the UI (as the \[Speech and TTS sample\] does), you must dispatch the updates to the UI thread through the [**RunAsync**](https://msdn.microsoft.com/library/windows/apps/hh750317) method of the dispatcher.</span></span>
```csharp
private async void ContinuousRecognitionSession_Completed(
      SpeechContinuousRecognitionSession sender,
      SpeechContinuousRecognitionCompletedEventArgs args)
      {
        if (args.Status != SpeechRecognitionResultStatus.Success)
        {
          if (args.Status == SpeechRecognitionResultStatus.TimeoutExceeded)
          {
            await dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
            {
              rootPage.NotifyUser(
                "Automatic Time Out of Dictation",
                NotifyType.StatusMessage);

              DictationButtonText.Text = " Continuous Recognition";
              dictationTextBox.Text = dictatedTextBuilder.ToString();
            });
          }
          else
          {
            await dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
            {
              rootPage.NotifyUser(
                "Continuous Recognition Completed: " + args.Status.ToString(),
                NotifyType.StatusMessage);

              DictationButtonText.Text = " Continuous Recognition";
            });
          }
        }
      }
```

## <a name="provide-ongoing-recognition-feedback"></a><span data-ttu-id="214cf-175">Bereitstellen von Erkennungsfeedback</span><span class="sxs-lookup"><span data-stu-id="214cf-175">Provide ongoing recognition feedback</span></span>


<span data-ttu-id="214cf-176">Beim Sprechen wird häufig Kontext benötigt, um das Gesagte zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="214cf-176">When people converse, they often rely on context to fully understand what is being said.</span></span> <span data-ttu-id="214cf-177">Auch die Spracherkennung benötigt häufig Kontext, um Erkennungsergebnisse mit hoher Trefferwahrscheinlichkeit bereitstellen zu können.</span><span class="sxs-lookup"><span data-stu-id="214cf-177">Similarly, the speech recognizer often needs context to provide high-confidence recognition results.</span></span> <span data-ttu-id="214cf-178">So sind beispielsweise die Wörter „seid“ und „seit“ ohne den Kontext anderer Wörter nicht voneinander zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="214cf-178">For example, by themselves, the words "weight" and "wait" are indistinguishable until more context can be gleaned from surrounding words.</span></span> <span data-ttu-id="214cf-179">Das [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900)-Ereignis wird erst ausgelöst, wenn die Erkennung zu einem gewissen Grad davon überzeugt ist, ein Wort oder eine Formulierung korrekt erkannt zu haben.</span><span class="sxs-lookup"><span data-stu-id="214cf-179">Until the recognizer has some confidence that a word, or words, have been recognized correctly, it will not raise the [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) event.</span></span>

<span data-ttu-id="214cf-180">Dies kann zu einer nichtoptimalen Benutzererfahrung führen, wenn der Benutzer weiterspricht und von der Erkennung keine Ergebnisse bereitgestellt werden, bis die Erkennungswahrscheinlichkeit hoch genug ist, um das [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900)-Ereignis auszulösen.</span><span class="sxs-lookup"><span data-stu-id="214cf-180">This can result in a less than ideal experience for the user as they continue speaking and no results are provided until the recognizer has high enough confidence to raise the [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) event.</span></span>

<span data-ttu-id="214cf-181">Behandeln Sie das [**HypothesisGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913914)-Ereignis, um dieses scheinbare Ausbleiben einer Reaktion zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="214cf-181">Handle the [**HypothesisGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913914) event to improve this apparent lack of responsiveness.</span></span> <span data-ttu-id="214cf-182">Dieses Ereignis wird ausgelöst, wenn die Erkennung einen neuen Satz potenzieller Übereinstimmungen für das verarbeitete Wort generiert.</span><span class="sxs-lookup"><span data-stu-id="214cf-182">This event is raised whenever the recognizer generates a new set of potential matches for the word being processed.</span></span> <span data-ttu-id="214cf-183">Das Ereignisargument stellt eine [**Hypothesis**](https://msdn.microsoft.com/library/windows/apps/dn913911)-Eigenschaft mit den aktuellen Übereinstimmungen bereit.</span><span class="sxs-lookup"><span data-stu-id="214cf-183">The event argument provides an [**Hypothesis**](https://msdn.microsoft.com/library/windows/apps/dn913911) property that contains the current matches.</span></span> <span data-ttu-id="214cf-184">Zeigen Sie diese dem Benutzer an, während dieser weiterspricht, um deutlich zu machen, dass die Verarbeitung weiterhin aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="214cf-184">Show these to the user as they continue speaking and reassure them that processing is still active.</span></span> <span data-ttu-id="214cf-185">Sobald eine hohe Trefferwahrscheinlichkeit erreicht und ein Erkennungsergebnis ermittelt wurde, ersetzen Sie die vorläufigen **Hypothesis**-Ergebnisse durch das endgültige [**Result**](https://msdn.microsoft.com/library/windows/apps/dn913895), das im Ereignis [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="214cf-185">Once confidence is high and a recognition result has been determined, replace the interim **Hypothesis** results with the final [**Result**](https://msdn.microsoft.com/library/windows/apps/dn913895) provided in the [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) event.</span></span>

<span data-ttu-id="214cf-186">Hier werden der hypothetische Text sowie Auslassungspunkte („...“) an den aktuellen Wert der [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683)-Ausgabe angefügt.</span><span class="sxs-lookup"><span data-stu-id="214cf-186">Here, we append the hypothetical text and an ellipsis ("…") to the current value of the output [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683).</span></span> <span data-ttu-id="214cf-187">Der Inhalt des Textfelds wird so lange mit neu generierten Hypothesen aktualisiert, bis die endgültigen Ergebnisse aus dem [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900)-Ereignis abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="214cf-187">The contents of the text box are updated as new hypotheses are generated and until the final results are obtained from the [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) event.</span></span>

```CSharp
private async void SpeechRecognizer_HypothesisGenerated(
  SpeechRecognizer sender,
  SpeechRecognitionHypothesisGeneratedEventArgs args)
  {

    string hypothesis = args.Hypothesis.Text;
    string textboxContent = dictatedTextBuilder.ToString() + " " + hypothesis + " ...";

    await dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
    {
      dictationTextBox.Text = textboxContent;
      btnClearText.IsEnabled = true;
    });
  }
```

## <a name="start-and-stop-recognition"></a><span data-ttu-id="214cf-188">Starten und Beenden der Erkennung</span><span class="sxs-lookup"><span data-stu-id="214cf-188">Start and stop recognition</span></span>


<span data-ttu-id="214cf-189">Überprüfen Sie vor dem Starten einer Erkennungssitzung den Wert der [**State**](https://msdn.microsoft.com/library/windows/apps/dn913915)-Eigenschaft der Spracherkennung.</span><span class="sxs-lookup"><span data-stu-id="214cf-189">Before starting a recognition session, check the value of the speech recognizer [**State**](https://msdn.microsoft.com/library/windows/apps/dn913915) property.</span></span> <span data-ttu-id="214cf-190">Die Spracherkennung muss sich im Zustand [**Idle**](https://msdn.microsoft.com/library/windows/apps/dn653227) befinden.</span><span class="sxs-lookup"><span data-stu-id="214cf-190">The speech recognizer must be in an [**Idle**](https://msdn.microsoft.com/library/windows/apps/dn653227) state.</span></span>

<span data-ttu-id="214cf-191">Nach der Überprüfung des Zustands der Spracherkennung wird die Sitzung durch Aufrufen der [**StartAsync**](https://msdn.microsoft.com/library/windows/apps/dn913901)-Methode der [**ContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913913)-Spracherkennungseigenschaft gestartet.</span><span class="sxs-lookup"><span data-stu-id="214cf-191">After checking the state of the speech recognizer, we start the session by calling the [**StartAsync**](https://msdn.microsoft.com/library/windows/apps/dn913901) method of the speech recognizer's [**ContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913913) property.</span></span>

```CSharp
if (speechRecognizer.State == SpeechRecognizerState.Idle)
{
  await speechRecognizer.ContinuousRecognitionSession.StartAsync();
}
```

<span data-ttu-id="214cf-192">Die Erkennung kann auf zwei Arten beendet werden:</span><span class="sxs-lookup"><span data-stu-id="214cf-192">Recognition can be stopped in two ways:</span></span>

-   <span data-ttu-id="214cf-193">[**StopAsync**](https://msdn.microsoft.com/library/windows/apps/dn913908) wartet, bis alle ausstehenden Erkennungsereignisse abgeschlossen sind. ([**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) wird weiter ausgelöst, bis alle ausstehenden Erkennungsvorgänge abgeschlossen wurden).</span><span class="sxs-lookup"><span data-stu-id="214cf-193">[**StopAsync**](https://msdn.microsoft.com/library/windows/apps/dn913908) lets any pending recognition events complete ([**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) continues to be raised until all pending recognition operations are complete).</span></span>
-   <span data-ttu-id="214cf-194">[**CancelAsync**](https://msdn.microsoft.com/library/windows/apps/dn913898) beendet die Erkennungssitzung umgehend und verwirft alle ausstehenden Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="214cf-194">[**CancelAsync**](https://msdn.microsoft.com/library/windows/apps/dn913898) terminates the recognition session immediately and discards any pending results.</span></span>

<span data-ttu-id="214cf-195">Nach der Überprüfung des Zustands der Spracherkennung wird die Sitzung durch Aufrufen der [**CancelAsync**](https://msdn.microsoft.com/library/windows/apps/dn913898)-Methode der [**ContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913913)-Spracherkennungseigenschaft beendet.</span><span class="sxs-lookup"><span data-stu-id="214cf-195">After checking the state of the speech recognizer, we stop the session by calling the [**CancelAsync**](https://msdn.microsoft.com/library/windows/apps/dn913898) method of the speech recognizer's [**ContinuousRecognitionSession**](https://msdn.microsoft.com/library/windows/apps/dn913913) property.</span></span>

```CSharp
if (speechRecognizer.State != SpeechRecognizerState.Idle)
{
  await speechRecognizer.ContinuousRecognitionSession.CancelAsync();
}
```

> [!NOTE]
> <span data-ttu-id="214cf-196">Ein [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900)-Ereignis kann nach dem Aufrufen von [**CancelAsync**](https://msdn.microsoft.com/library/windows/apps/dn913898) auftreten.</span><span class="sxs-lookup"><span data-stu-id="214cf-196">A [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) event can occur after a call to [**CancelAsync**](https://msdn.microsoft.com/library/windows/apps/dn913898).</span></span>  
> <span data-ttu-id="214cf-197">Aufgrund des Multithreadings befindet sich unter Umständen noch ein [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900)-Ereignis im Stapel, wenn [**CancelAsync**](https://msdn.microsoft.com/library/windows/apps/dn913898) aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="214cf-197">Because of multithreading, a [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) event might still remain on the stack when [**CancelAsync**](https://msdn.microsoft.com/library/windows/apps/dn913898) is called.</span></span> <span data-ttu-id="214cf-198">In diesem Fall wird dennoch das **ResultGenerated**-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="214cf-198">If so, the **ResultGenerated** event still fires.</span></span>  
> <span data-ttu-id="214cf-199">Wenn Sie beim Abbrechen der Erkennungssitzung private Felder festlegen, müssen deren Werte immer im [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900)-Handler bestätigt werden.</span><span class="sxs-lookup"><span data-stu-id="214cf-199">If you set any private fields when canceling the recognition session, always confirm their values in the [**ResultGenerated**](https://msdn.microsoft.com/library/windows/apps/dn913900) handler.</span></span> <span data-ttu-id="214cf-200">Gehen Sie beispielsweise nicht davon aus, dass ein Feld in Ihrem Handler initialisiert wird, wenn Sie es beim Abbrechen der Sitzung auf Null festlegen.</span><span class="sxs-lookup"><span data-stu-id="214cf-200">For example, don't assume a field is initialized in your handler if you set them to null when you cancel the session.</span></span>

 

## <a name="related-articles"></a><span data-ttu-id="214cf-201">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="214cf-201">Related articles</span></span>


* [<span data-ttu-id="214cf-202">Sprachinteraktionen</span><span class="sxs-lookup"><span data-stu-id="214cf-202">Speech interactions</span></span>](speech-interactions.md)

**<span data-ttu-id="214cf-203">Beispiele</span><span class="sxs-lookup"><span data-stu-id="214cf-203">Samples</span></span>**
* [<span data-ttu-id="214cf-204">Beispiel zu Spracherkennung und Sprachsynthese</span><span class="sxs-lookup"><span data-stu-id="214cf-204">Speech recognition and speech synthesis sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619897)
 

 




