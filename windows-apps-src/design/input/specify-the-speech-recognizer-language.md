---
Description: Learn how to select an installed language to use for speech recognition.
title: Festlegen der Sprache für die Spracherkennung
ms.assetid: 4C463A1B-AF6A-46FD-A839-5D6724955B38
label: Specify the speech recognizer language
template: detail.hbs
keywords: Sprache, Stimme, Spracherkennung, natürliche Sprache, diktieren, Eingabe, Benutzerinteraktion
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: acd8b06c98c95750b6d047cda96b8c2884a9d7a9
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8735454"
---
# <a name="specify-the-speech-recognizer-language"></a><span data-ttu-id="f09e4-103">Festlegen der Sprache für die Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="f09e4-103">Specify the speech recognizer language</span></span>


<span data-ttu-id="f09e4-104">Hier erfahren Sie, wie Sie eine installierte Sprache für die Spracherkennung auswählen.</span><span class="sxs-lookup"><span data-stu-id="f09e4-104">Learn how to select an installed language to use for speech recognition.</span></span>

> <span data-ttu-id="f09e4-105">**Wichtige APIs**: [**SupportedTopicLanguages**](https://msdn.microsoft.com/library/windows/apps/dn653251), [**SupportedGrammarLanguages**](https://msdn.microsoft.com/library/windows/apps/dn653250), [**Language**](https://msdn.microsoft.com/library/windows/apps/br206804)</span><span class="sxs-lookup"><span data-stu-id="f09e4-105">**Important APIs**: [**SupportedTopicLanguages**](https://msdn.microsoft.com/library/windows/apps/dn653251), [**SupportedGrammarLanguages**](https://msdn.microsoft.com/library/windows/apps/dn653250), [**Language**](https://msdn.microsoft.com/library/windows/apps/br206804)</span></span>


<span data-ttu-id="f09e4-106">Im Folgenden listen wir die auf einem System installierten Sprachen auf, ermitteln die Standardsprache und wählen eine andere Sprache für die Spracherkennung aus.</span><span class="sxs-lookup"><span data-stu-id="f09e4-106">Here, we enumerate the languages installed on a system, identify which is the default language, and select a different language for recognition.</span></span>

**<span data-ttu-id="f09e4-107">Voraussetzungen:</span><span class="sxs-lookup"><span data-stu-id="f09e4-107">Prerequisites:</span></span>**

<span data-ttu-id="f09e4-108">Dieses Thema baut auf dem Thema [Spracherkennung](speech-recognition.md) auf.</span><span class="sxs-lookup"><span data-stu-id="f09e4-108">This topic builds on [Speech recognition](speech-recognition.md).</span></span>

<span data-ttu-id="f09e4-109">Sie sollten über Grundkenntnisse in den Bereichen Spracherkennung und Erkennungseinschränkungen verfügen.</span><span class="sxs-lookup"><span data-stu-id="f09e4-109">You should have a basic understanding of speech recognition and recognition constraints.</span></span>

<span data-ttu-id="f09e4-110">Wenn Sie noch keine Erfahrung mit der Entwicklung von UWP-Apps (Universelle Windows-Plattform) haben, sollten Sie sich in den folgenden Themen zunächst mit den hier besprochenen Technologien vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="f09e4-110">If you're new to developing Universal Windows Platform (UWP) apps, have a look through these topics to get familiar with the technologies discussed here.</span></span>

-   [<span data-ttu-id="f09e4-111">Erstellen Ihrer ersten App</span><span class="sxs-lookup"><span data-stu-id="f09e4-111">Create your first app</span></span>](https://msdn.microsoft.com/library/windows/apps/bg124288)
-   <span data-ttu-id="f09e4-112">Informationen zu Ereignissen finden Sie unter [Übersicht über Ereignisse und Routingereignisse](https://msdn.microsoft.com/library/windows/apps/mt185584).</span><span class="sxs-lookup"><span data-stu-id="f09e4-112">Learn about events with [Events and routed events overview](https://msdn.microsoft.com/library/windows/apps/mt185584)</span></span>

**<span data-ttu-id="f09e4-113">Richtlinien für die Benutzerfreundlichkeit:</span><span class="sxs-lookup"><span data-stu-id="f09e4-113">User experience guidelines:</span></span>**

<span data-ttu-id="f09e4-114">Nützliche Tipps zum Entwerfen einer hilfreichen und ansprechenden App mit Sprachfunktion finden Sie unter [Entwurfsrichtlinien für die Spracherkennung](https://msdn.microsoft.com/library/windows/apps/dn596121).</span><span class="sxs-lookup"><span data-stu-id="f09e4-114">For helpful tips about designing a useful and engaging speech-enabled app, see [Speech design guidelines](https://msdn.microsoft.com/library/windows/apps/dn596121) .</span></span>

## <a name="identify-the-default-language"></a><span data-ttu-id="f09e4-115">Ermitteln der Standardsprache</span><span class="sxs-lookup"><span data-stu-id="f09e4-115">Identify the default language</span></span>


<span data-ttu-id="f09e4-116">Die Spracherkennung verwendet die Systemsprache als Standardsprache für die Erkennung.</span><span class="sxs-lookup"><span data-stu-id="f09e4-116">A speech recognizer uses the system speech language as its default recognition language.</span></span> <span data-ttu-id="f09e4-117">Diese Sprache wird vom Benutzer auf dem Gerät unter „Einstellungen &gt; System &gt; Spracherkennung &gt; Spracherkennungssprache” festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f09e4-117">This language is set by the user on the device Settings &gt; System &gt; Speech &gt; Speech Language screen.</span></span>

<span data-ttu-id="f09e4-118">Zum Ermitteln der Standardsprache überprüfen wir die statische [**SystemSpeechLanguage**](https://msdn.microsoft.com/library/windows/apps/dn653252)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="f09e4-118">We identify the default language by checking the [**SystemSpeechLanguage**](https://msdn.microsoft.com/library/windows/apps/dn653252) static property.</span></span>

```CSharp
var language = SpeechRecognizer.SystemSpeechLanguage; 
```

## <a name="confirm-an-installed-language"></a><span data-ttu-id="f09e4-119">Bestätigen einer installierten Sprache</span><span class="sxs-lookup"><span data-stu-id="f09e4-119">Confirm an installed language</span></span>


<span data-ttu-id="f09e4-120">Die installierten Sprachen können sich von Gerät zu Gerät unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="f09e4-120">Installed languages can vary between devices.</span></span> <span data-ttu-id="f09e4-121">Überprüfen Sie, ob eine Sprache vorhanden ist, wenn diese für eine bestimmte Einschränkung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="f09e4-121">You should verify the existence of a language if you depend on it for a particular constraint.</span></span>

<span data-ttu-id="f09e4-122">**Hinweis:** nach der Installation eines neues Sprachpakets ist ein Neustart erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f09e4-122">**Note**A reboot is required after a new language pack is installed.</span></span> <span data-ttu-id="f09e4-123">Eine Ausnahme mit dem Fehlercode SPERR\_NOT\_FOUND (0x8004503a) wird ausgelöst, wenn die angegebene Sprache nicht unterstützt wird oder nicht vollständig installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="f09e4-123">An exception with error code SPERR\_NOT\_FOUND (0x8004503a) is raised if the specified language is not supported or has not finished installing.</span></span>

 

<span data-ttu-id="f09e4-124">Zum Ermitteln der auf einem Gerät unterstützten Sprachen überprüfen Sie eine von zwei statischen Eigenschaften der [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226)-Klasse:</span><span class="sxs-lookup"><span data-stu-id="f09e4-124">Determine the supported languages on a device by checking one of two static properties of the [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) class:</span></span>

-   <span data-ttu-id="f09e4-125">[**SupportedTopicLanguages**](https://msdn.microsoft.com/library/windows/apps/dn653251) – Die Sammlung von [**Language**](https://msdn.microsoft.com/library/windows/apps/br206804)-Objekten, die mit vordefinierten Diktier- und Websuchgrammatiken verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f09e4-125">[**SupportedTopicLanguages**](https://msdn.microsoft.com/library/windows/apps/dn653251)—The collection of [**Language**](https://msdn.microsoft.com/library/windows/apps/br206804) objects used with predefined dictation and web search grammars.</span></span>

-   <span data-ttu-id="f09e4-126">[**SupportedGrammarLanguages**](https://msdn.microsoft.com/library/windows/apps/dn653250) – Die Sammlung von [**Language**](https://msdn.microsoft.com/library/windows/apps/br206804)-Objekten, die mit einer Einschränkungsliste oder einer Speech Recognition Grammar Specification (SRGS)-Datei verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f09e4-126">[**SupportedGrammarLanguages**](https://msdn.microsoft.com/library/windows/apps/dn653250)—The collection of [**Language**](https://msdn.microsoft.com/library/windows/apps/br206804) objects used with a list constraint or a Speech Recognition Grammar Specification (SRGS) file.</span></span>

## <a name="specify-a-language"></a><span data-ttu-id="f09e4-127">Angeben einer Sprache</span><span class="sxs-lookup"><span data-stu-id="f09e4-127">Specify a language</span></span>


<span data-ttu-id="f09e4-128">Übergeben Sie zum Angeben einer Sprache ein [**Language**](https://msdn.microsoft.com/library/windows/apps/br206804)-Objekt im [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226)-Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="f09e4-128">To specify a language, pass a [**Language**](https://msdn.microsoft.com/library/windows/apps/br206804) object in the [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) constructor.</span></span>

<span data-ttu-id="f09e4-129">Hier geben wir "En-US" als Sprache für die Spracherkennung an.</span><span class="sxs-lookup"><span data-stu-id="f09e4-129">Here, we specify "en-US" as the recognition language.</span></span>


```CSharp
var language = new Windows.Globalization.Language(“en-US”); 
var recognizer = new SpeechRecognizer(language); 
```

## <a name="remarks"></a><span data-ttu-id="f09e4-130">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="f09e4-130">Remarks</span></span>


<span data-ttu-id="f09e4-131">Sie können eine Themeneinschränkung konfigurieren, indem Sie [**SpeechRecognitionTopicConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631446) zur [**Constraints**](https://msdn.microsoft.com/library/windows/apps/dn653241)-Sammlung der [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) hinzufügen und anschließend [**CompileConstraintsAsync**](https://msdn.microsoft.com/library/windows/apps/dn653240) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="f09e4-131">A topic constraint can be configured by adding a [**SpeechRecognitionTopicConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631446) to the [**Constraints**](https://msdn.microsoft.com/library/windows/apps/dn653241) collection of the [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) and then calling [**CompileConstraintsAsync**](https://msdn.microsoft.com/library/windows/apps/dn653240).</span></span> <span data-ttu-id="f09e4-132">Der [**SpeechRecognitionResultStatus**](https://msdn.microsoft.com/library/windows/apps/dn631433)-Wert **TopicLanguageNotSupported** wird zurückgegeben, wenn die Erkennung nicht mit einer unterstützten Themensprache initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="f09e4-132">A [**SpeechRecognitionResultStatus**](https://msdn.microsoft.com/library/windows/apps/dn631433) of **TopicLanguageNotSupported** is returned if the recognizer is not initialized with a supported topic language.</span></span>

<span data-ttu-id="f09e4-133">Sie können eine Einschränkungsliste konfigurieren, indem Sie [**SpeechRecognitionListConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631421) zur [**Constraints**](https://msdn.microsoft.com/library/windows/apps/dn653241)-Sammlung der [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) hinzufügen und anschließend [**CompileConstraintsAsync**](https://msdn.microsoft.com/library/windows/apps/dn653240) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="f09e4-133">A list constraint is configured by adding a [**SpeechRecognitionListConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631421) to the [**Constraints**](https://msdn.microsoft.com/library/windows/apps/dn653241) collection of the [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) and then calling [**CompileConstraintsAsync**](https://msdn.microsoft.com/library/windows/apps/dn653240).</span></span> <span data-ttu-id="f09e4-134">Die Sprache einer benutzerdefinierten Liste kann nicht direkt angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f09e4-134">You cannot specify the language of a custom list directly.</span></span> <span data-ttu-id="f09e4-135">Stattdessen wird die Liste mit der Sprache der Erkennung verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="f09e4-135">Instead, the list will be processed using the language of the recognizer.</span></span>

<span data-ttu-id="f09e4-136">Bei einer SRGS-Grammatik handelt es sich um ein offenes XML-Standardformat, das durch die [**SpeechRecognitionGrammarFileConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631412)-Klasse dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="f09e4-136">An SRGS grammar is an open-standard XML format represented by the [**SpeechRecognitionGrammarFileConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631412) class.</span></span> <span data-ttu-id="f09e4-137">Anders als bei benutzerdefinierten Listen können Sie die Sprache der Grammatik im SRGS-Markup angeben.</span><span class="sxs-lookup"><span data-stu-id="f09e4-137">Unlike custom lists, you can specify the language of the grammar in the SRGS markup.</span></span> <span data-ttu-id="f09e4-138">[**CompileConstraintsAsync**](https://msdn.microsoft.com/library/windows/apps/dn653240) verursacht einen [**SpeechRecognitionResultStatus**](https://msdn.microsoft.com/library/windows/apps/dn631433)-Fehler **TopicLanguageNotSupported**, wenn die Erkennung nicht mit der gleichen Sprache initialisiert wird wie das SRGS-Markup.</span><span class="sxs-lookup"><span data-stu-id="f09e4-138">[**CompileConstraintsAsync**](https://msdn.microsoft.com/library/windows/apps/dn653240) fails with a [**SpeechRecognitionResultStatus**](https://msdn.microsoft.com/library/windows/apps/dn631433) of **TopicLanguageNotSupported** if the recognizer is not initialized to the same language as the SRGS markup.</span></span>

## <a name="related-articles"></a><span data-ttu-id="f09e4-139">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="f09e4-139">Related articles</span></span>

**<span data-ttu-id="f09e4-140">Entwickler</span><span class="sxs-lookup"><span data-stu-id="f09e4-140">Developers</span></span>**

* [<span data-ttu-id="f09e4-141">Spracherkennungsinteraktionen</span><span class="sxs-lookup"><span data-stu-id="f09e4-141">Speech interactions</span></span>](speech-interactions.md)

**<span data-ttu-id="f09e4-142">Designer</span><span class="sxs-lookup"><span data-stu-id="f09e4-142">Designers</span></span>**

* [<span data-ttu-id="f09e4-143">Entwurfsrichtlinien für die Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="f09e4-143">Speech design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596121)

**<span data-ttu-id="f09e4-144">Beispiele</span><span class="sxs-lookup"><span data-stu-id="f09e4-144">Samples</span></span>**

* [<span data-ttu-id="f09e4-145">Beispiel zu Spracherkennung und Sprachsynthese</span><span class="sxs-lookup"><span data-stu-id="f09e4-145">Speech recognition and speech synthesis sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619897)
 

 




