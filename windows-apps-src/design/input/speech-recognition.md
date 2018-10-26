---
author: Karl-Bridge-Microsoft
Description: Use speech recognition to provide input, specify an action or command, and accomplish tasks.
title: Spracherkennung
ms.assetid: 553C0FB7-35BC-4894-9EF1-906139E17552
label: Speech recognition
template: detail.hbs
keywords: Sprache, Stimme, Spracherkennung, natürliche Sprache, diktieren, Eingabe, Benutzerinteraktion
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 7ce8146cc952d22eb0aa365be707cbd2cef7aabf
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5567790"
---
# <a name="speech-recognition"></a><span data-ttu-id="2d81a-103">Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="2d81a-103">Speech recognition</span></span>


<span data-ttu-id="2d81a-104">Nutzen Sie die Spracherkennung als Eingabemöglichkeit oder zum Ausführen einer Aktion, eines Befehls oder einer Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="2d81a-104">Use speech recognition to provide input, specify an action or command, and accomplish tasks.</span></span>

> <span data-ttu-id="2d81a-105">**Wichtige APIs**: [**Windows.Media.SpeechRecognition**](https://msdn.microsoft.com/library/windows/apps/dn653262)</span><span class="sxs-lookup"><span data-stu-id="2d81a-105">**Important APIs**: [**Windows.Media.SpeechRecognition**](https://msdn.microsoft.com/library/windows/apps/dn653262)</span></span>

<span data-ttu-id="2d81a-106">Die Spracherkennung besteht aus einer Sprachlaufzeit, Erkennungs-APIs zum Programmieren der Laufzeit, einsatzfähiger Grammatik für das Diktieren und die Websuche und einer Standard-UI, die Benutzern das Auffinden und Verwenden der Spracherkennungsfeatures erleichtert.</span><span class="sxs-lookup"><span data-stu-id="2d81a-106">Speech recognition is made up of a speech runtime, recognition APIs for programming the runtime, ready-to-use grammars for dictation and web search, and a default system UI that helps users discover and use speech recognition features.</span></span>


## <a name="set-up-the-audio-feed"></a><span data-ttu-id="2d81a-107">Einrichten des Audiofeeds</span><span class="sxs-lookup"><span data-stu-id="2d81a-107">Set up the audio feed</span></span>


<span data-ttu-id="2d81a-108">Stellen Sie sicher, dass Ihr Gerät über ein Mikrofon oder Ähnliches verfügt.</span><span class="sxs-lookup"><span data-stu-id="2d81a-108">Ensure that your device has a microphone or the equivalent.</span></span>

<span data-ttu-id="2d81a-109">Legen Sie die Gerätefunktion **Mikrofon** ([**DeviceCapability**](https://msdn.microsoft.com/library/windows/apps/br211430)) im [App-Paket](https://msdn.microsoft.com/library/windows/apps/br211474)manifest (**package.appxmanifest**-Datei) fest, um Zugriff auf den Audiofeed des Mikrofons zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2d81a-109">Set the **Microphone** device capability ([**DeviceCapability**](https://msdn.microsoft.com/library/windows/apps/br211430)) in the [App package manifest](https://msdn.microsoft.com/library/windows/apps/br211474) (**package.appxmanifest** file) to get access to the microphone’s audio feed.</span></span> <span data-ttu-id="2d81a-110">Mit dieser Funktion kann die App Audio von angeschlossenen Mikrofonen aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="2d81a-110">This allows the app to record audio from connected microphones.</span></span>

<span data-ttu-id="2d81a-111">Informationen finden Sie unter [Deklaration der App-Funktionen](https://msdn.microsoft.com/library/windows/apps/mt270968).</span><span class="sxs-lookup"><span data-stu-id="2d81a-111">See [App capability declarations](https://msdn.microsoft.com/library/windows/apps/mt270968).</span></span>

## <a name="recognize-speech-input"></a><span data-ttu-id="2d81a-112">Erkennen von Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="2d81a-112">Recognize speech input</span></span>


<span data-ttu-id="2d81a-113">Mit einer *Einschränkung* werden die Wörter und Wortgruppen (Vokabular) definiert, die eine App bei der Spracheingabe erkennt.</span><span class="sxs-lookup"><span data-stu-id="2d81a-113">A *constraint* defines the words and phrases (vocabulary) that an app recognizes in speech input.</span></span> <span data-ttu-id="2d81a-114">Einschränkungen sind der Kern der Spracherkennung und verleihen Ihrer App mehr Kontrolle über die Genauigkeit der Spracherkennung.</span><span class="sxs-lookup"><span data-stu-id="2d81a-114">Constraints are at the core of speech recognition and give your app greater over the accuracy of speech recognition.</span></span>

<span data-ttu-id="2d81a-115">Sie können verschiedene Arten von Einschränkungen bei der Spracherkennung nutzen:</span><span class="sxs-lookup"><span data-stu-id="2d81a-115">You can use various types of constraints when performing speech recognition:</span></span>

1.  <span data-ttu-id="2d81a-116">**Vordefinierte Grammatiken** ([**SpeechRecognitionTopicConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631446)).</span><span class="sxs-lookup"><span data-stu-id="2d81a-116">**Predefined grammars** ([**SpeechRecognitionTopicConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631446)).</span></span>

    <span data-ttu-id="2d81a-117">Mit vordefinierten Diktier- und Websuchgrammatiken können Sie eine Spracherkennung für Ihre App bereitstellen, ohne eine Grammatik erstellen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="2d81a-117">Predefined dictation and web-search grammars provide speech recognition for your app without requiring you to author a grammar.</span></span> <span data-ttu-id="2d81a-118">Bei Verwendung dieser Grammatiken wird die Spracherkennung von einem Remotewebdienst durchgeführt, und die Ergebnisse werden an das Gerät zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="2d81a-118">When using these grammars, speech recognition is performed by a remote web service and the results are returned to the device.</span></span>

    <span data-ttu-id="2d81a-119">Die Standardgrammatik der Freitext-Diktierfunktion erkennt die meisten Wörter und Ausdrücke, die Benutzer in einer bestimmten Sprache sagen können, und ist für die Erkennung kurzer Ausdrücke optimiert.</span><span class="sxs-lookup"><span data-stu-id="2d81a-119">The default free-text dictation grammar can recognize most words and phrases that a user can say in a particular language, and is optimized to recognize short phrases.</span></span> <span data-ttu-id="2d81a-120">Die vordefinierte Grammatik für das Diktieren kommt dann zum Einsatz, wenn Sie keine Einschränkungen für Ihr [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226)-Objekt festlegen.</span><span class="sxs-lookup"><span data-stu-id="2d81a-120">The predefined dictation grammar is used if you don't specify any constraints for your [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) object.</span></span> <span data-ttu-id="2d81a-121">Die Freitext-Diktierfunktion ist nützlich, wenn Sie nicht einschränken möchten, was Benutzer sagen können.</span><span class="sxs-lookup"><span data-stu-id="2d81a-121">Free-text dictation is useful when you don't want to limit the kinds of things a user can say.</span></span> <span data-ttu-id="2d81a-122">Typische Verwendungsmöglichkeiten sind das Erstellen von Notizen oder das Diktieren eines Nachrichtentexts.</span><span class="sxs-lookup"><span data-stu-id="2d81a-122">Typical uses include creating notes or dictating the content for a message.</span></span>

    <span data-ttu-id="2d81a-123">Die Grammatik für die Websuche enthält wie die Diktiergrammatik eine große Anzahl von Wörtern und Ausdrücken, die Benutzer sagen können.</span><span class="sxs-lookup"><span data-stu-id="2d81a-123">The web-search grammar, like a dictation grammar, contains a large number of words and phrases that a user might say.</span></span> <span data-ttu-id="2d81a-124">Sie ist allerdings für die Erkennung von Begriffen optimiert, die beim Suchen im Web häufig verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2d81a-124">However, it is optimized to recognize terms that people typically use when searching the web.</span></span>

    <span data-ttu-id="2d81a-125">**Hinweis:** da vordefinierte Diktier- und Websuche Grammatiken groß sein können und diese online sind (nicht auf dem Gerät), Leistung ist möglicherweise nicht so gut wie bei einer lokal auf dem Gerät installierten benutzerdefinierten Grammatik.</span><span class="sxs-lookup"><span data-stu-id="2d81a-125">**Note**Because predefined dictation and web-search grammars can be large, and because they are online (not on the device), performance might not be as fast as with a custom grammar installed on the device.</span></span>     

    <span data-ttu-id="2d81a-126">Diese vordefinierten Grammatiken können zum Erkennen von bis zu zehn Sekunden Spracheingabe verwendet werden. Sie müssen dazu keinen Code selbst erstellen.</span><span class="sxs-lookup"><span data-stu-id="2d81a-126">These predefined grammars can be used to recognize up to 10 seconds of speech input and require no authoring effort on your part.</span></span> <span data-ttu-id="2d81a-127">Sie erfordern jedoch eine Netzwerkverbindung.</span><span class="sxs-lookup"><span data-stu-id="2d81a-127">However, they do require a connection to a network.</span></span>

    <span data-ttu-id="2d81a-128">Zum Verwenden der Webdiensteinschränkungen muss die Unterstützung für die Spracheingabe und das Diktieren unter **Einstellungen** **-> Datenschutz -> Datenschutzeinstellungen für Sprache, Freihand, Eingabe** aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="2d81a-128">To use web-service constraints, speech input and dictation support must be enabled in **Settings** by turning on the "Get to know me" option in  **Settings -> Privacy -> Speech, inking, and typing**.</span></span>

    <span data-ttu-id="2d81a-129">Hier wird erläutert, wie Sie testen, ob die Spracheingabe aktiviert ist, und wie Sie die Seite „Einstellungen -> Datenschutz -> Datenschutzeinstellungen für Sprache, Freihand und Eingabe“ öffnen.</span><span class="sxs-lookup"><span data-stu-id="2d81a-129">Here, we show how to test whether speech input is enabled and open the Settings -> Privacy -> Speech, inking, and typing page, if not.</span></span>

    <span data-ttu-id="2d81a-130">Zuerst initialisieren wir eine globale Variable (HResultPrivacyStatementDeclined) für den HResult-Wert 0x80045509.</span><span class="sxs-lookup"><span data-stu-id="2d81a-130">First, we initialize a global variable (HResultPrivacyStatementDeclined) to the HResult value of 0x80045509.</span></span> <span data-ttu-id="2d81a-131">Weitere Informationen finden Sie unter [Ausnahmebehandlung in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/dn532194).</span><span class="sxs-lookup"><span data-stu-id="2d81a-131">See [Exception handling for in C\# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/dn532194).</span></span>

    ```csharp
    private static uint HResultPrivacyStatementDeclined = 0x80045509;
    ```

    <span data-ttu-id="2d81a-132">Anschließend fangen wir während der Erkennung alle standardmäßigen Ausnahmen ab und testen, ob der [**HResult**](https://msdn.microsoft.com/library/windows/apps/br206579)-Wert dem Wert der HResultPrivacyStatementDeclined-Variablen entspricht.</span><span class="sxs-lookup"><span data-stu-id="2d81a-132">We then catch any standard exceptions during recogntion and test if the [**HResult**](https://msdn.microsoft.com/library/windows/apps/br206579) value is equal to the value of the HResultPrivacyStatementDeclined variable.</span></span> <span data-ttu-id="2d81a-133">Wenn ja, zeigen wir eine Warnung an und rufen `await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-settings:privacy-accounts"));` auf, um die Seite „Einstellungen“ zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2d81a-133">If so, we display a warning and call `await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-settings:privacy-accounts"));` to open the Settings page.</span></span>
    
    ```csharp
    catch (Exception exception)
    {
      // Handle the speech privacy policy error.
      if ((uint)exception.HResult == HResultPrivacyStatementDeclined)
      {
        resultTextBlock.Visibility = Visibility.Visible;
        resultTextBlock.Text = "The privacy statement was declined." + 
          "Go to Settings -> Privacy -> Speech, inking and typing, and ensure you" +
          "have viewed the privacy policy, and 'Get To Know You' is enabled.";
        // Open the privacy/speech, inking, and typing settings page.
        await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-settings:privacy-accounts")); 
      }
      else
      {
        var messageDialog = new Windows.UI.Popups.MessageDialog(exception.Message, "Exception");
        await messageDialog.ShowAsync();
      }
    }
    ```

2.  <span data-ttu-id="2d81a-134">**Einschränkungen per programmgesteuerter Liste** ([**SpeechRecognitionListConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631421))</span><span class="sxs-lookup"><span data-stu-id="2d81a-134">**Programmatic list constraints** ([**SpeechRecognitionListConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631421)).</span></span>

    <span data-ttu-id="2d81a-135">Einschränkungen per programmgesteuerter Liste sind eine unkomplizierte Methode für die Erstellung einfacher Grammatiken in Form einer Liste von Wörtern und Ausdrücken.</span><span class="sxs-lookup"><span data-stu-id="2d81a-135">Programmatic list constraints provide a lightweight approach to creating simple grammars using a list of words or phrases.</span></span> <span data-ttu-id="2d81a-136">Eine Einschränkungsliste eignet sich gut für die Erkennung kurzer, einzelner Ausdrücke.</span><span class="sxs-lookup"><span data-stu-id="2d81a-136">A list constraint works well for recognizing short, distinct phrases.</span></span> <span data-ttu-id="2d81a-137">Das explizite Angeben aller Wörter in einer Grammatik verbessert auch die Erkennungsgenauigkeit, da das Spracherkennungsmodul nur eine Übereinstimmung bestätigen muss.</span><span class="sxs-lookup"><span data-stu-id="2d81a-137">Explicitly specifying all words in a grammar also improves recognition accuracy, as the speech recognition engine must only process speech to confirm a match.</span></span> <span data-ttu-id="2d81a-138">Die Liste kann auch programmgesteuert aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="2d81a-138">The list can also be programmatically updated.</span></span>

    <span data-ttu-id="2d81a-139">Eine Einschränkungsliste besteht aus einem Array von Zeichenfolgen, die die Spracheingaben darstellen, die von Ihrer App für einen Erkennungsvorgang akzeptiert werden.</span><span class="sxs-lookup"><span data-stu-id="2d81a-139">A list constraint consists of an array of strings that represents speech input that your app will accept for a recognition operation.</span></span> <span data-ttu-id="2d81a-140">Sie können in Ihrer App eine Einschränkungsliste einrichten, indem Sie ein Einschränkungslistenobjekt für die Spracherkennung erstellen und ein Array mit Zeichenfolgen übergeben.</span><span class="sxs-lookup"><span data-stu-id="2d81a-140">You can create a list constraint in your app by creating a speech-recognition list-constraint object and passing an array of strings.</span></span> <span data-ttu-id="2d81a-141">Fügen Sie dieses Objekt dann der Einschränkungsauflistung der Erkennung hinzu.</span><span class="sxs-lookup"><span data-stu-id="2d81a-141">Then, add that object to the constraints collection of the recognizer.</span></span> <span data-ttu-id="2d81a-142">Die Erkennung ist erfolgreich, wenn die Spracherkennung die Zeichenfolgen des Arrays erkennt.</span><span class="sxs-lookup"><span data-stu-id="2d81a-142">Recognition is successful when the speech recognizer recognizes any one of the strings in the array.</span></span>

3.  <span data-ttu-id="2d81a-143">**SRGS-Grammatiken** ([**SpeechRecognitionGrammarFileConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631412))</span><span class="sxs-lookup"><span data-stu-id="2d81a-143">**SRGS grammars** ([**SpeechRecognitionGrammarFileConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631412)).</span></span>

    <span data-ttu-id="2d81a-144">Eine Speech Recognition Grammar Specification (SRGS)-Grammatik ist ein statisches Dokument, das im Gegensatz zu einer Einschränkung per programmgesteuerter Liste das in [SRGS Version1.0](http://go.microsoft.com/fwlink/p/?LinkID=262302) definierte XML-Format verwendet.</span><span class="sxs-lookup"><span data-stu-id="2d81a-144">An Speech Recognition Grammar Specification (SRGS) grammar is a static document that, unlike a programmatic list constraint, uses the XML format defined by the [SRGS Version 1.0](http://go.microsoft.com/fwlink/p/?LinkID=262302).</span></span> <span data-ttu-id="2d81a-145">Eine SRGS-Grammatik bietet die höchstmögliche Kontrolle über die Spracherkennungsfunktion, da Sie mehrere semantische Bedeutungen in einem einzigen Erkennungsvorgang erfassen können.</span><span class="sxs-lookup"><span data-stu-id="2d81a-145">An SRGS grammar provides the greatest control over the speech recognition experience by letting you capture multiple semantic meanings in a single recognition.</span></span>

4.  <span data-ttu-id="2d81a-146">**Einschränkungen für Sprachbefehle** ([**SpeechRecognitionVoiceCommandDefinitionConstraint**](https://msdn.microsoft.com/library/windows/apps/dn653220))</span><span class="sxs-lookup"><span data-stu-id="2d81a-146">**Voice command constraints** ([**SpeechRecognitionVoiceCommandDefinitionConstraint**](https://msdn.microsoft.com/library/windows/apps/dn653220))</span></span>

    <span data-ttu-id="2d81a-147">Verwenden Sie eine Voice Command Definition-(VCD-)XML-Datei, um die Befehle zu definieren, mit denen der Benutzer Aktionen initiieren kann, wenn er Ihre App aktiviert.</span><span class="sxs-lookup"><span data-stu-id="2d81a-147">Use a Voice Command Definition (VCD) XML file to define the commands that the user can say to initiate actions when activating your app.</span></span> <span data-ttu-id="2d81a-148">Weitere Details finden Sie unter [Starten einer Vordergrund-App mit Sprachbefehlen in Cortana](https://msdn.microsoft.com/cortana/voicecommands/launch-a-foreground-app-with-voice-commands-in-cortana).</span><span class="sxs-lookup"><span data-stu-id="2d81a-148">For more detail, see [Launch a foreground app with voice commands in Cortana](https://msdn.microsoft.com/cortana/voicecommands/launch-a-foreground-app-with-voice-commands-in-cortana).</span></span>

<span data-ttu-id="2d81a-149">**Hinweis:** welche Art von Einschränkungstyp Ihnen richtet sich nach der Komplexität der Erkennungsfunktion, die Sie erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="2d81a-149">**Note**Which type of constraint type you use depends on the complexity of the recognition experience you want to create.</span></span> <span data-ttu-id="2d81a-150">Für eine bestimmte Erkennungsaufgabe kann jeweils einer der Ansätze am besten geeignet sein, und vielleicht haben Sie in Ihrer App sogar für alle Einschränkungsarten Verwendung.</span><span class="sxs-lookup"><span data-stu-id="2d81a-150">Any could be the best choice for a specific recognition task, and you might find uses for all types of constraints in your app.</span></span>
<span data-ttu-id="2d81a-151">Informationen zu den ersten Schritten mit Einschränkungen finden Sie unter [Definieren von benutzerdefinierten Erkennungseinschränkungen](define-custom-recognition-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="2d81a-151">To get started with constraints, see [Define custom recognition constraints](define-custom-recognition-constraints.md).</span></span>

 

<span data-ttu-id="2d81a-152">Die vordefinierte Diktiergrammatik von universellen Windows-Apps erkennt die meisten Wörter und kurzen Wortgruppen einer Sprache.</span><span class="sxs-lookup"><span data-stu-id="2d81a-152">The predefined Universal Windows app dictation grammar recognizes most words and short phrases in a language.</span></span> <span data-ttu-id="2d81a-153">Sie wird standardmäßig aktiviert, wenn ein Spracherkennungsobjekt ohne benutzerdefinierte Einschränkungen instanziiert wird.</span><span class="sxs-lookup"><span data-stu-id="2d81a-153">It is activated by default when a speech recognizer object is instantiated without custom constraints.</span></span>

<span data-ttu-id="2d81a-154">In diesem Beispiel zeigen wir Ihnen, wie Sie:</span><span class="sxs-lookup"><span data-stu-id="2d81a-154">In this example, we show how to:</span></span>

-   <span data-ttu-id="2d81a-155">eine Spracherkennung erstellen,</span><span class="sxs-lookup"><span data-stu-id="2d81a-155">Create a speech recognizer.</span></span>
-   <span data-ttu-id="2d81a-156">die standardmäßigen Einschränkungen von universellen Windows-Apps kompilieren (es wurde keine Grammatik zum Grammatiksatz der Spracherkennung hinzugefügt) und</span><span class="sxs-lookup"><span data-stu-id="2d81a-156">Compile the default Universal Windows app constraints (no grammars have been added to the speech recognizer's grammar set).</span></span>
-   <span data-ttu-id="2d81a-157">die Spracherkennung starten, indem Sie die einfache Erkennungs-UI und das TTS-Feedback der [**RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245)-Methode verwenden.</span><span class="sxs-lookup"><span data-stu-id="2d81a-157">Start listening for speech by using the basic recognition UI and TTS feedback provided by the [**RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245) method.</span></span> <span data-ttu-id="2d81a-158">Verwenden Sie die [**RecognizeAsync**](https://msdn.microsoft.com/library/windows/apps/dn653244)-Methode, wenn die Standard-UI nicht benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="2d81a-158">Use the [**RecognizeAsync**](https://msdn.microsoft.com/library/windows/apps/dn653244) method if the default UI is not required.</span></span>

```CSharp
private async void StartRecognizing_Click(object sender, RoutedEventArgs e)
{
    // Create an instance of SpeechRecognizer.
    var speechRecognizer = new Windows.Media.SpeechRecognition.SpeechRecognizer();

    // Compile the dictation grammar by default.
    await speechRecognizer.CompileConstraintsAsync();

    // Start recognition.
    Windows.Media.SpeechRecognition.SpeechRecognitionResult speechRecognitionResult = await speechRecognizer.RecognizeWithUIAsync();

    // Do something with the recognition result.
    var messageDialog = new Windows.UI.Popups.MessageDialog(speechRecognitionResult.Text, "Text spoken");
    await messageDialog.ShowAsync();
}
```

## <a name="customize-the-recognition-ui"></a><span data-ttu-id="2d81a-159">Anpassen der Erkennungs-UI</span><span class="sxs-lookup"><span data-stu-id="2d81a-159">Customize the recognition UI</span></span>


<span data-ttu-id="2d81a-160">Wenn Ihre App die Spracherkennung durch Aufruf von [**SpeechRecognizer.RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245) zu leisten versucht, werden mehrere Bildschirme in der folgenden Reihenfolge angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2d81a-160">When your app attempts speech recognition by calling [**SpeechRecognizer.RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245), several screens are shown in the following order.</span></span>

<span data-ttu-id="2d81a-161">Wenn Sie eine Einschränkung auf der Grundlage einer vordefinierten Grammatik (Diktat oder Websuche) verwenden:</span><span class="sxs-lookup"><span data-stu-id="2d81a-161">If you're using a constraint based on a predefined grammar (dictation or web search):</span></span>

-   <span data-ttu-id="2d81a-162">Der Bildschirm **Spracherkennung**</span><span class="sxs-lookup"><span data-stu-id="2d81a-162">The **Listening** screen.</span></span>
-   <span data-ttu-id="2d81a-163">Der Bildschirm **Verarbeitung**</span><span class="sxs-lookup"><span data-stu-id="2d81a-163">The **Thinking** screen.</span></span>
-   <span data-ttu-id="2d81a-164">Der Bildschirm **Gehört** oder der Fehlerbildschirm</span><span class="sxs-lookup"><span data-stu-id="2d81a-164">The **Heard you say** screen or the error screen.</span></span>

<span data-ttu-id="2d81a-165">Wenn Sie eine Einschränkung auf der Grundlage von Wörtern oder Ausdrücken oder eine Einschränkung auf der Grundlage einer SRGS-Grammatikdatei verwenden:</span><span class="sxs-lookup"><span data-stu-id="2d81a-165">If you're using a constraint based on a list of words or phrases, or a constraint based on a SRGS grammar file:</span></span>

-   <span data-ttu-id="2d81a-166">Der Bildschirm **Spracherkennung**</span><span class="sxs-lookup"><span data-stu-id="2d81a-166">The **Listening** screen.</span></span>
-   <span data-ttu-id="2d81a-167">Der Bildschirm **Sagten Sie** , falls die vom Benutzer ausgesprochenen Wörter als mehrere potenzielle Ergebnisse interpretiert werden können.</span><span class="sxs-lookup"><span data-stu-id="2d81a-167">The **Did you say** screen, if what the user said could be interpreted as more than one potential result.</span></span>
-   <span data-ttu-id="2d81a-168">Der Bildschirm **Gehört** oder der Fehlerbildschirm</span><span class="sxs-lookup"><span data-stu-id="2d81a-168">The **Heard you say** screen or the error screen.</span></span>

<span data-ttu-id="2d81a-169">Die folgende Abbildung zeigt ein Beispiel für den Fluss zwischen Bildschirmen für die Spracherkennung mit einer Einschränkung auf der Grundlage einer SRGS-Grammatikdatei.</span><span class="sxs-lookup"><span data-stu-id="2d81a-169">The following image shows an example of the flow between screens for a speech recognizer that uses a constraint based on a SRGS grammar file.</span></span> <span data-ttu-id="2d81a-170">In diesem Beispiel war die Spracherkennung erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="2d81a-170">In this example, speech recognition was successful.</span></span>

![initial Erkennung screen for a constraint based on a sgrs grammar file](images/speech-listening-initial.png)

![intermediate Erkennung screen for a constraint based on a sgrs grammar file](images/speech-listening-intermediate.png)

![final Erkennung screen for a constraint based on a sgrs grammar file](images/speech-listening-complete.png)

<span data-ttu-id="2d81a-174">Der **Spracherkennung**-Bildschirm kann Beispiele für Wörter oder Ausdrücke zur Erkennung durch die App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2d81a-174">The **Listening** screen can provide examples of words or phrases that the app can recognize.</span></span> <span data-ttu-id="2d81a-175">Hier zeigen wir, wie Sie die Eigenschaften der [**SpeechRecognizerUIOptions**](https://msdn.microsoft.com/library/windows/apps/dn653234)-Klasse (abgerufen durch Aufrufen der [**SpeechRecognizer.UIOptions**](https://msdn.microsoft.com/library/windows/apps/dn653254)-Eigenschaft) zur Anpassung von Inhalten auf dem **Spracherkennung**-Bildschirm verwenden.</span><span class="sxs-lookup"><span data-stu-id="2d81a-175">Here, we show how to use the properties of the [**SpeechRecognizerUIOptions**](https://msdn.microsoft.com/library/windows/apps/dn653234) class (obtained by calling the [**SpeechRecognizer.UIOptions**](https://msdn.microsoft.com/library/windows/apps/dn653254) property) to customize content on the **Listening** screen.</span></span>

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
    speechRecognizer.UIOptions.ExampleText = @"Ex. 'weather for London'";
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

## <a name="related-articles"></a><span data-ttu-id="2d81a-176">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="2d81a-176">Related articles</span></span>


**<span data-ttu-id="2d81a-177">Entwickler</span><span class="sxs-lookup"><span data-stu-id="2d81a-177">Developers</span></span>**
* <span data-ttu-id="2d81a-178">[Interaktionen mit der Spracherkennung](speech-interactions.md)
**Designer**</span><span class="sxs-lookup"><span data-stu-id="2d81a-178">[Speech interactions](speech-interactions.md)
**Designers**</span></span>
* <span data-ttu-id="2d81a-179">[Entwicklungsrichtlinien für die Spracherkennung](https://msdn.microsoft.com/library/windows/apps/dn596121)
**Beispiele**</span><span class="sxs-lookup"><span data-stu-id="2d81a-179">[Speech design guidelines](https://msdn.microsoft.com/library/windows/apps/dn596121)
**Samples**</span></span>
* [<span data-ttu-id="2d81a-180">Beispiel zu Spracherkennung und Sprachsynthese</span><span class="sxs-lookup"><span data-stu-id="2d81a-180">Speech recognition and speech synthesis sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619897)
 

 




