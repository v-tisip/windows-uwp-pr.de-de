---
Description: Learn how to define and use custom constraints for speech recognition.
title: Festlegen von benutzerdefinierten Erkennungseinschränkungen
ms.assetid: 26289DE5-6AC9-42C3-A160-E522AE62D2FC
label: Define custom recognition constraints
template: detail.hbs
keywords: Sprache, Stimme, Spracherkennung, natürliche Sprache, diktieren, Eingabe, Benutzerinteraktion
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 53539c73137b40d154db00fa9e340d81412764da
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8942179"
---
# <a name="define-custom-recognition-constraints"></a><span data-ttu-id="29a64-103">Festlegen von benutzerdefinierten Erkennungseinschränkungen</span><span class="sxs-lookup"><span data-stu-id="29a64-103">Define custom recognition constraints</span></span>



<span data-ttu-id="29a64-104">Erfahren Sie, wie Sie benutzerdefinierte Einschränkungen für die Spracherkennung festlegen und verwenden können.</span><span class="sxs-lookup"><span data-stu-id="29a64-104">Learn how to define and use custom constraints for speech recognition.</span></span>

> <span data-ttu-id="29a64-105">**Wichtige APIs**: [**SpeechRecognitionTopicConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631446), [**SpeechRecognitionListConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631421), [**SpeechRecognitionGrammarFileConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631412)</span><span class="sxs-lookup"><span data-stu-id="29a64-105">**Important APIs**: [**SpeechRecognitionTopicConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631446), [**SpeechRecognitionListConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631421), [**SpeechRecognitionGrammarFileConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631412)</span></span>


<span data-ttu-id="29a64-106">Die Spracherkennung benötigt mindestens eine Einschränkung, um erkennbares Vokabular zu definieren.</span><span class="sxs-lookup"><span data-stu-id="29a64-106">Speech recognition requires at least one constraint to define a recognizable vocabulary.</span></span> <span data-ttu-id="29a64-107">Wenn Sie keine Einschränkung angeben, wird die vordefinierte Diktiergrammatik der universellen Windows-Apps verwendet.</span><span class="sxs-lookup"><span data-stu-id="29a64-107">If no constraint is specified, the predefined dictation grammar of Universal Windows apps is used.</span></span> <span data-ttu-id="29a64-108">Siehe [Spracherkennung](speech-recognition.md).</span><span class="sxs-lookup"><span data-stu-id="29a64-108">See [Speech recognition](speech-recognition.md).</span></span>


## <a name="add-constraints"></a><span data-ttu-id="29a64-109">Hinzufügen von Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="29a64-109">Add constraints</span></span>


<span data-ttu-id="29a64-110">Verwenden Sie die [**SpeechRecognizer.Constraints**](https://msdn.microsoft.com/library/windows/apps/dn653241)-Eigenschaft, um Einschränkungen für die Spracherkennung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="29a64-110">Use the [**SpeechRecognizer.Constraints**](https://msdn.microsoft.com/library/windows/apps/dn653241) property to add constraints to a speech recognizer.</span></span>

<span data-ttu-id="29a64-111">Im Folgenden behandeln wir die drei Arten der Spracherkennungseinschränkungen, die in einer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="29a64-111">Here, we cover the three kinds of speech recognition constraints used from within an app.</span></span> <span data-ttu-id="29a64-112">(Informationen zu Einschränkungen bei Sprachbefehlen finden Sie unter [Starten einer Vordergrund-App mit Sprachbefehlen in Cortana](https://msdn.microsoft.com/cortana/voicecommands/launch-a-foreground-app-with-voice-commands-in-cortana).)</span><span class="sxs-lookup"><span data-stu-id="29a64-112">(For voice command constraints, see [Launch a foreground app with voice commands in Cortana](https://msdn.microsoft.com/cortana/voicecommands/launch-a-foreground-app-with-voice-commands-in-cortana).)</span></span>

-   <span data-ttu-id="29a64-113">[**SpeechRecognitionTopicConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631446) – Eine Einschränkung auf der Grundlage einer vordefinierten Grammatik (Diktat oder Websuche).</span><span class="sxs-lookup"><span data-stu-id="29a64-113">[**SpeechRecognitionTopicConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631446)—A constraint based on a predefined grammar (dictation or web search).</span></span>
-   <span data-ttu-id="29a64-114">[**SpeechRecognitionListConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631421) – Eine Einschränkung auf der Grundlage einer Liste von Wörtern oder Ausdrücken.</span><span class="sxs-lookup"><span data-stu-id="29a64-114">[**SpeechRecognitionListConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631421)—A constraint based on a list of words or phrases.</span></span>
-   <span data-ttu-id="29a64-115">[**SpeechRecognitionGrammarFileConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631412) – Eine Einschränkung, die in einer SRGS (Speech Recognition Grammar Specification)-Datei definiert ist.</span><span class="sxs-lookup"><span data-stu-id="29a64-115">[**SpeechRecognitionGrammarFileConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631412)—A constraint defined in a Speech Recognition Grammar Specification (SRGS) file.</span></span>

<span data-ttu-id="29a64-116">Jedes Spracherkennungsmodul kann über eine Einschränkungssammlung verfügen.</span><span class="sxs-lookup"><span data-stu-id="29a64-116">Each speech recognizer can have one constraint collection.</span></span> <span data-ttu-id="29a64-117">Nur die folgenden Einschränkungskombinationen sind gültig:</span><span class="sxs-lookup"><span data-stu-id="29a64-117">Only these combinations of constraints are valid:</span></span>

- <span data-ttu-id="29a64-118">Eine Einschränkung zu einem Thema (Diktat oder Websuche)</span><span class="sxs-lookup"><span data-stu-id="29a64-118">A single-topic constraint (dictation or web search)</span></span>
- <span data-ttu-id="29a64-119">Für das Windows10 Fall Creators Update (10.0.16299.15) und höher kann eine Einschränkung zu einem Thema mit einer Listeneinschränkung kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="29a64-119">For Windows 10 Fall Creators Update (10.0.16299.15) and newer, a single topic constraint can be combined with a list constraint</span></span>
- <span data-ttu-id="29a64-120">Eine Kombination aus Listeneinschränkungen und/oder Grammatikdatei-Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="29a64-120">A combination of list constraints and/or grammar-file constraints.</span></span>

> [!Important]
> <span data-ttu-id="29a64-121">Rufen Sie die Methode **[SpeechRecognizer.CompileConstraintsAsync](https://msdn.microsoft.com/library/windows/apps/dn653240)** auf, um die Einschränkungen zu kompilieren, bevor Sie den Erkennungsprozess starten.</span><span class="sxs-lookup"><span data-stu-id="29a64-121">Call the **[SpeechRecognizer.CompileConstraintsAsync](https://msdn.microsoft.com/library/windows/apps/dn653240)** method to compile the constraints before starting the recognition process.</span></span>

## <a name="specify-a-web-search-grammar-speechrecognitiontopicconstraint"></a><span data-ttu-id="29a64-122">Angeben einer Grammatik für die Websuche (SpeechRecognitionTopicConstraint)</span><span class="sxs-lookup"><span data-stu-id="29a64-122">Specify a web-search grammar (SpeechRecognitionTopicConstraint)</span></span>

<span data-ttu-id="29a64-123">Themeneinschränkungen (Diktier- oder Websuchengrammatik) müssen der Einschränkungssammlung einer Spracherkennung hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="29a64-123">Topic constraints (dictation or web-search grammar) must be added to the constraints collection of a speech recognizer.</span></span>

> [!NOTE]
> <span data-ttu-id="29a64-124">Sie können eine [SpeechRecognitionListConstraint](https://docs.microsoft.com/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint) in Verbindung mit [SpeechRecognitionTopicConstraint](https://docs.microsoft.com/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionTopicConstraint) verwenden, um die Genauigkeit des Diktats zu erhöhen, indem Sie einen Satz an domänenspezifischen Stichwörtern während des Diktats verwenden.</span><span class="sxs-lookup"><span data-stu-id="29a64-124">You can use a [SpeechRecognitionListConstraint](https://docs.microsoft.com/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint) in conjunction with a [SpeechRecognitionTopicConstraint](https://docs.microsoft.com/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionTopicConstraint) to increase dictation accuracy by providing a set of domain-specific keywords that you think are likely to be used during dictation.</span></span>

<span data-ttu-id="29a64-125">Hier fügen wir der Einschränkungssammlung eine Grammatik für die Websuche hinzu.</span><span class="sxs-lookup"><span data-stu-id="29a64-125">Here, we add a web-search grammar to the constraints collection.</span></span>

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

## <a name="specify-a-programmatic-list-constraint-speechrecognitionlistconstraint"></a><span data-ttu-id="29a64-126">Angeben einer programmgesteuerten Listeneinschränkung (SpeechRecognitionListConstraint)</span><span class="sxs-lookup"><span data-stu-id="29a64-126">Specify a programmatic list constraint (SpeechRecognitionListConstraint)</span></span>


<span data-ttu-id="29a64-127">Listeneinschränkungen müssen der Einschränkungssammlung einer Spracherkennung hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="29a64-127">List constraints must be added to the constraints collection of a speech recognizer.</span></span>

<span data-ttu-id="29a64-128">Beachten Sie folgende Punkte:</span><span class="sxs-lookup"><span data-stu-id="29a64-128">Keep the following points in mind:</span></span>

-   <span data-ttu-id="29a64-129">Sie können der Einschränkungssammlung mehrere Listeneinschränkungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="29a64-129">You can add multiple list constraints to a constraints collection.</span></span>
-   <span data-ttu-id="29a64-130">Sie können eine beliebige Sammlung verwenden, die **IIterable&lt;String&gt;** für die Zeichenfolgenwerte implementiert.</span><span class="sxs-lookup"><span data-stu-id="29a64-130">You can use any collection that implements **IIterable&lt;String&gt;** for the string values.</span></span>

<span data-ttu-id="29a64-131">Hier geben wir programmgesteuert ein Array von Wörtern als Listeneinschränkung an und fügen es der Einschränkungssammlung einer Spracherkennung hinzu.</span><span class="sxs-lookup"><span data-stu-id="29a64-131">Here, we programmatically specify an array of words as a list constraint and add it to the constraints collection of a speech recognizer.</span></span>

```CSharp
private async void YesOrNo_Click(object sender, RoutedEventArgs e)
{
    // Create an instance of SpeechRecognizer.
    var speechRecognizer = new Windows.Media.SpeechRecognition.SpeechRecognizer();

    // You could create this array dynamically.
    string[] responses = { "Yes", "No" };


    // Add a list constraint to the recognizer.
    var listConstraint = new Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint(responses, "yesOrNo");

    speechRecognizer.UIOptions.ExampleText = @"Ex. 'yes', 'no'";
    speechRecognizer.Constraints.Add(listConstraint);

    // Compile the constraint.
    await speechRecognizer.CompileConstraintsAsync();

    // Start recognition.
    Windows.Media.SpeechRecognition.SpeechRecognitionResult speechRecognitionResult = await speechRecognizer.RecognizeWithUIAsync();

    // Do something with the recognition result.
    var messageDialog = new Windows.UI.Popups.MessageDialog(speechRecognitionResult.Text, "Text spoken");
    await messageDialog.ShowAsync();
}
```

## <a name="specify-an-srgs-grammar-constraint-speechrecognitiongrammarfileconstraint"></a><span data-ttu-id="29a64-132">Angeben einer SRGS-(SpeechRecognitionGrammarFileConstraint-)Grammatikeinschränkung</span><span class="sxs-lookup"><span data-stu-id="29a64-132">Specify an SRGS grammar constraint (SpeechRecognitionGrammarFileConstraint)</span></span>


<span data-ttu-id="29a64-133">SRGS-Grammatikdateien müssen der Einschränkungssammlung eines Spracherkennungsmoduls hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="29a64-133">SRGS grammar files must be added to the constraints collection of a speech recognizer.</span></span>

<span data-ttu-id="29a64-134">SRGS, Version1.0, ist die branchenübliche Markupsprache zum Erstellen von Grammatik für die Spracherkennung im XML-Format.</span><span class="sxs-lookup"><span data-stu-id="29a64-134">The SRGS Version 1.0 is the industry-standard markup language for creating XML-format grammars for speech recognition.</span></span> <span data-ttu-id="29a64-135">Universelle Windows-Apps bieten über SRGS hinaus auch Alternativen zur Erstellung von Grammatik für die Spracherkennung. Sie stellen aber möglicherweise fest, dass Sie beim Erstellen von Grammatik mit SRGS die besten Ergebnisse erzielen. Dies gilt besonders für komplexere Spracherkennungsszenarien.</span><span class="sxs-lookup"><span data-stu-id="29a64-135">Although Universal Windows apps provide alternatives to using SRGS for creating speech-recognition grammars, you might find that using SRGS to create grammars produces the best results, particularly for more involved speech recognition scenarios.</span></span>

<span data-ttu-id="29a64-136">SRGS-Grammatik bietet einen umfassenden Featuresatz, den Sie zum Erstellen komplexer Sprachinteraktionen für Ihre Apps nutzen können.</span><span class="sxs-lookup"><span data-stu-id="29a64-136">SRGS grammars provide a full set of features to help you architect complex voice interaction for your apps.</span></span> <span data-ttu-id="29a64-137">Mit SRGS haben Sie beispielsweise folgende Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="29a64-137">For example, with SRGS grammars you can:</span></span>

-   <span data-ttu-id="29a64-138">Geben Sie die Reihenfolge an, in der Wörter und Wortgruppen gesprochen werden müssen, um erkannt zu werden.</span><span class="sxs-lookup"><span data-stu-id="29a64-138">Specify the order in which words and phrases must be spoken to be recognized.</span></span>
-   <span data-ttu-id="29a64-139">Kombinieren Sie Wörter mehrerer Listen und Wortgruppen für die Erkennung.</span><span class="sxs-lookup"><span data-stu-id="29a64-139">Combine words from multiple lists and phrases to be recognized.</span></span>
-   <span data-ttu-id="29a64-140">Verlinken Sie zu anderen Grammatiken.</span><span class="sxs-lookup"><span data-stu-id="29a64-140">Link to other grammars.</span></span>
-   <span data-ttu-id="29a64-141">Weisen Sie einem alternativen Wort oder einer Wortgruppe eine Gewichtung zu, um die Wahrscheinlichkeit der Verwendung zu erhöhen oder zu verringern und für die Spracheingabe so bessere Übereinstimmungen zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="29a64-141">Assign a weight to an alternative word or phrase to increase or decrease the likelihood that it will be used to match speech input.</span></span>
-   <span data-ttu-id="29a64-142">Binden Sie optionale Wörter oder Wortgruppen ein.</span><span class="sxs-lookup"><span data-stu-id="29a64-142">Include optional words or phrases.</span></span>
-   <span data-ttu-id="29a64-143">Verwenden Sie spezielle Regeln zum Herausfiltern nicht angegebener oder unerwarteter Eingaben, z.B. ungewollte Spracheingaben, die keine Übereinstimmung mit der Grammatik ergeben, oder Hintergrundgeräusche.</span><span class="sxs-lookup"><span data-stu-id="29a64-143">Use special rules that help filter out unspecified or unanticipated input, such as random speech that doesn't match the grammar, or background noise.</span></span>
-   <span data-ttu-id="29a64-144">Verwenden Sie Semantik, um zu definieren, was Spracherkennung für Ihre App bedeutet.</span><span class="sxs-lookup"><span data-stu-id="29a64-144">Use semantics to define what speech recognition means to your app.</span></span>
-   <span data-ttu-id="29a64-145">Geben Sie verschiedene Aussprachen an, entweder direkt in einer Grammatik oder über einen Link zu einem Lexikon.</span><span class="sxs-lookup"><span data-stu-id="29a64-145">Specify pronunciations, either inline in a grammar or via a link to a lexicon.</span></span>

<span data-ttu-id="29a64-146">Weitere Informationen zu SRGS-Elementen und -Attributen finden Sie unter [SRGS-Grammatik – XML-Referenz](http://go.microsoft.com/fwlink/p/?LinkID=269886).</span><span class="sxs-lookup"><span data-stu-id="29a64-146">For more info about SRGS elements and attributes, see the [SRGS Grammar XML Reference](http://go.microsoft.com/fwlink/p/?LinkID=269886) .</span></span> <span data-ttu-id="29a64-147">Informationen zu den ersten Schritten zur Erstellung einer SRGS-Grammatik finden Sie unter [So wird's gemacht: Erstellen einer einfachen XML-Grammatik](http://go.microsoft.com/fwlink/p/?LinkID=269887).</span><span class="sxs-lookup"><span data-stu-id="29a64-147">To get started creating an SRGS grammar, see [How to Create a Basic XML Grammar](http://go.microsoft.com/fwlink/p/?LinkID=269887).</span></span>

<span data-ttu-id="29a64-148">Beachten Sie folgende Punkte:</span><span class="sxs-lookup"><span data-stu-id="29a64-148">Keep the following points in mind:</span></span>

-   <span data-ttu-id="29a64-149">Sie können der Einschränkungssammlung mehrere Grammatikdatei-Einschränkungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="29a64-149">You can add multiple grammar-file constraints to a constraints collection.</span></span>
-   <span data-ttu-id="29a64-150">Sie können die GRXML-Dateierweiterung für XML-basierte Grammatikdokumente verwenden, die den SRGS-Regeln entsprechen.</span><span class="sxs-lookup"><span data-stu-id="29a64-150">Use the .grxml file extension for XML-based grammar documents that conform to SRGS rules.</span></span>

<span data-ttu-id="29a64-151">In diesem Beispiel wird eine SRGS-Grammatik verwendet, die in einer Datei namens „srgs.grxml“ (später beschrieben) definiert ist.</span><span class="sxs-lookup"><span data-stu-id="29a64-151">This example uses an SRGS grammar defined in a file named srgs.grxml (described later).</span></span> <span data-ttu-id="29a64-152">In den Dateieigenschaften ist die **Paketaktion** auf **Inhalt** und **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** gesetzt:</span><span class="sxs-lookup"><span data-stu-id="29a64-152">In the file properties, the **Package Action** is set to **Content** with **Copy to Output Directory** set to **Copy always**:</span></span>

```CSharp
private async void Colors_Click(object sender, RoutedEventArgs e)
{
    // Create an instance of SpeechRecognizer.
    var speechRecognizer = new Windows.Media.SpeechRecognition.SpeechRecognizer();

    // Add a grammar file constraint to the recognizer.
    var storageFile = await Windows.Storage.StorageFile.GetFileFromApplicationUriAsync(new Uri("ms-appx:///Colors.grxml"));
    var grammarFileConstraint = new Windows.Media.SpeechRecognition.SpeechRecognitionGrammarFileConstraint(storageFile, "colors");

    speechRecognizer.UIOptions.ExampleText = @"Ex. 'blue background', 'green text'";
    speechRecognizer.Constraints.Add(grammarFileConstraint);

    // Compile the constraint.
    await speechRecognizer.CompileConstraintsAsync();

    // Start recognition.
    Windows.Media.SpeechRecognition.SpeechRecognitionResult speechRecognitionResult = await speechRecognizer.RecognizeWithUIAsync();

    // Do something with the recognition result.
    var messageDialog = new Windows.UI.Popups.MessageDialog(speechRecognitionResult.Text, "Text spoken");
    await messageDialog.ShowAsync();
}
```

<span data-ttu-id="29a64-153">Diese SRGS-Datei (srgs.grxml) enthält Tags für die semantische Interpretation.</span><span class="sxs-lookup"><span data-stu-id="29a64-153">This SRGS file (srgs.grxml) includes semantic interpretation tags.</span></span> <span data-ttu-id="29a64-154">Diese Tags liefern einen Mechanismus, mit dem übereinstimmende Grammatikdaten an Ihre App zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="29a64-154">These tags provide a mechanism for returning grammar match data to your app.</span></span> <span data-ttu-id="29a64-155">Die Grammatik muss der [Semantic Interpretation for Speech Recognition (SISR)1.0](http://go.microsoft.com/fwlink/p/?LinkID=201765)-Spezifikation des World Wide Web Consortium (W3C) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="29a64-155">Grammars must conform to the World Wide Web Consortium (W3C)[Semantic Interpretation for Speech Recognition (SISR) 1.0](http://go.microsoft.com/fwlink/p/?LinkID=201765) specification.</span></span>

<span data-ttu-id="29a64-156">Hier horchen wir auf Varianten von „Ja“ und „Nein“.</span><span class="sxs-lookup"><span data-stu-id="29a64-156">Here, we listen for variants of "yes" and "no".</span></span>

```CSharp
<grammar xml:lang="en-US" 
         root="yesOrNo"
         version="1.0" 
         tag-format="semantics/1.0"
         xmlns="http://www.w3.org/2001/06/grammar">

    <!-- The following rules recognize variants of yes and no. -->
      <rule id="yesOrNo">
         <one-of>
            <item>
              <one-of>
                 <item>yes</item>
                 <item>yeah</item>
                 <item>yep</item>
                 <item>yup</item>
                 <item>un huh</item>
                 <item>yay yus</item>
              </one-of>
              <tag>out="yes";</tag>
            </item>
            <item>
              <one-of>
                 <item>no</item>
                 <item>nope</item>
                 <item>nah</item>
                 <item>uh uh</item>
               </one-of>
               <tag>out="no";</tag>
            </item>
         </one-of>
      </rule>
</grammar>
```

## <a name="manage-constraints"></a><span data-ttu-id="29a64-157">Verwalten von Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="29a64-157">Manage constraints</span></span>


<span data-ttu-id="29a64-158">Nachdem eine Einschränkungssammlung für die Erkennung geladen wurde, kann Ihre App verwalten, welche Einschränkungen für Erkennungsvorgänge aktiviert sind. Dazu wird für die [**IsEnabled**](https://msdn.microsoft.com/library/windows/apps/dn631402)-Eigenschaft einer Einschränkung **true** oder **false** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="29a64-158">After a constraint collection is loaded for recognition, your app can manage which constraints are enabled for recognition operations by setting the [**IsEnabled**](https://msdn.microsoft.com/library/windows/apps/dn631402) property of a constraint to **true** or **false**.</span></span> <span data-ttu-id="29a64-159">Die Standardeinstellung lautet **true**.</span><span class="sxs-lookup"><span data-stu-id="29a64-159">The default setting is **true**.</span></span>

<span data-ttu-id="29a64-160">Meist ist es effizienter, Einschränkungen einmal zu laden und dann bei Bedarf zu aktivieren bzw. zu deaktivieren, als Einschränkungen für jeden Erkennungsvorgang zu laden, zu entladen und zu kompilieren.</span><span class="sxs-lookup"><span data-stu-id="29a64-160">It's usually more efficient to load constraints once, enabling and disabling them as needed, rather than to load, unload, and compile constraints for each recognition operation.</span></span> <span data-ttu-id="29a64-161">Verwenden Sie die [**IsEnabled**](https://msdn.microsoft.com/library/windows/apps/dn631402)-Eigenschaft nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="29a64-161">Use the [**IsEnabled**](https://msdn.microsoft.com/library/windows/apps/dn631402) property, as required.</span></span>

<span data-ttu-id="29a64-162">Durch Begrenzung der Anzahl der Einschränkungen wird die Datenmenge beschränkt, die die Spracherkennung zum Suchen und Abgleichen mit der Spracheingabe benötigt.</span><span class="sxs-lookup"><span data-stu-id="29a64-162">Restricting the number of constraints serves to limit the amount of data that the speech recognizer needs to search and match against the speech input.</span></span> <span data-ttu-id="29a64-163">So können die Leistung und die Genauigkeit der Spracherkennung verbessert werden.</span><span class="sxs-lookup"><span data-stu-id="29a64-163">This can improve both the performance and the accuracy of speech recognition.</span></span>

<span data-ttu-id="29a64-164">Entscheiden Sie, welche Einschränkungen aktiviert sind. Dies richtet sich nach den Wörtern, die für die App im Kontext des jeweiligen Erkennungsvorgangs zu erwarten sind.</span><span class="sxs-lookup"><span data-stu-id="29a64-164">Decide which constraints are enabled based on the phrases that your app can expect in the context of the current recognition operation.</span></span> <span data-ttu-id="29a64-165">Wenn es in der App beispielsweise gerade darum geht, eine Farbe anzuzeigen, müssen Sie wahrscheinlich keine Einschränkung aktivieren, bei der die Bezeichnungen von Tieren erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="29a64-165">For example, if the current app context is to display a color, you probably don't need to enable a constraint that recognizes the names of animals.</span></span>

<span data-ttu-id="29a64-166">Mit den Eigenschaften [**SpeechRecognizerUIOptions.AudiblePrompt**](https://msdn.microsoft.com/library/windows/apps/dn653235) und [**SpeechRecognizerUIOptions.ExampleText**](https://msdn.microsoft.com/library/windows/apps/dn653236) können Sie Benutzern mitteilen, was gesagt werden kann. Diese Eigenschaften werden mithilfe der [**SpeechRecognizer.UIOptions**](https://msdn.microsoft.com/library/windows/apps/dn653254)-Eigenschaft festgelegt.</span><span class="sxs-lookup"><span data-stu-id="29a64-166">To prompt the user for what can be spoken, use the [**SpeechRecognizerUIOptions.AudiblePrompt**](https://msdn.microsoft.com/library/windows/apps/dn653235) and [**SpeechRecognizerUIOptions.ExampleText**](https://msdn.microsoft.com/library/windows/apps/dn653236) properties, which are set by means of the [**SpeechRecognizer.UIOptions**](https://msdn.microsoft.com/library/windows/apps/dn653254) property.</span></span> <span data-ttu-id="29a64-167">Wenn Sie Benutzer im Voraus darüber informieren, was sie bei einem Erkennungsvorgang sagen können, erhöht sich die Wahrscheinlichkeit, dass die Benutzer etwas sagen, was einer aktiven Einschränkung zugeordnet werden kann.</span><span class="sxs-lookup"><span data-stu-id="29a64-167">Preparing users for what they can say during the recognition operation increases the likelihood that they will speak a phrase that can be matched to an active constraint.</span></span>

## <a name="related-articles"></a><span data-ttu-id="29a64-168">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="29a64-168">Related articles</span></span>


* [<span data-ttu-id="29a64-169">Sprachinteraktionen</span><span class="sxs-lookup"><span data-stu-id="29a64-169">Speech interactions</span></span>](speech-interactions.md)

**<span data-ttu-id="29a64-170">Beispiele</span><span class="sxs-lookup"><span data-stu-id="29a64-170">Samples</span></span>**
* [<span data-ttu-id="29a64-171">Beispiel zu Spracherkennung und Sprachsynthese</span><span class="sxs-lookup"><span data-stu-id="29a64-171">Speech recognition and speech synthesis sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619897)
 

 




