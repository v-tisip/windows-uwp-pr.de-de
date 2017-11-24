---
author: stevewhims
Description: "Wenn eine Ressource angefordert wird, kann es mehrere Kandidaten geben, für die sich in einem gewissen Maße eine Übereinstimmung mit dem aktuellen Ressourcenkontext ergibt. Vom Ressourcenverwaltungssystem werden alle Kandidaten analysiert, und der beste Kandidat für die Rückgabe wird ermittelt. In diesem Thema wird dieser Prozess ausführlich und anhand von Beispielen beschrieben."
title: "Wie das Ressourcenverwaltungssystem Ressourcen zuordnet und auswählt"
template: detail.hbs
ms.author: stwhi
ms.date: 10/23/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, uwp, Ressourcen, Bild, Element, MRT, Qualifizierer
localizationpriority: medium
ms.openlocfilehash: 4731ae7add7d5b969ab98da60b3f6740dbbbee1b
ms.sourcegitcommit: 44a24b580feea0f188c7eae36e72e4a4f412802b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

# <a name="how-the-resource-management-system-matches-and-chooses-resources"></a><span data-ttu-id="0b893-106">Wie das Ressourcenverwaltungssystem Ressourcen zuordnet und auswählt</span><span class="sxs-lookup"><span data-stu-id="0b893-106">How the Resource Management System matches and chooses resources</span></span>

<span data-ttu-id="0b893-107">Wenn eine Ressource angefordert wird, kann es mehrere Kandidaten geben, für die sich in einem gewissen Maße eine Übereinstimmung mit dem aktuellen Ressourcenkontext ergibt.</span><span class="sxs-lookup"><span data-stu-id="0b893-107">When a resource is requested, there may be several candidates that match the current resource context to some degree.</span></span> <span data-ttu-id="0b893-108">Vom Ressourcenverwaltungssystem werden alle Kandidaten analysiert, und der beste Kandidat für die Rückgabe wird ermittelt.</span><span class="sxs-lookup"><span data-stu-id="0b893-108">The Resource Management System will analyze all of the candidates and determine the best candidate to return.</span></span> <span data-ttu-id="0b893-109">Dazu werden alle Qualifizierer einbezogen, um eine Einstufung aller Kandidaten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="0b893-109">This is done by taking all qualifiers into consideration to rank all of the candidates.</span></span>

<span data-ttu-id="0b893-110">Bei diesem Einstufungsvorgang werden den unterschiedlichen Qualifizierern unterschiedliche Prioritäten zugewiesen: Die Sprache hat die größte Auswirkung auf die Gesamteinstufung, gefolgt von Kontrast, Skalierung usw.</span><span class="sxs-lookup"><span data-stu-id="0b893-110">In this ranking process, the different qualifiers are given different priorities: language has the greatest impact on the overall ranking, followed by contrast, then scale, and so on.</span></span> <span data-ttu-id="0b893-111">Für jeden Qualifizierer werden Kandidatenqualifizierer mit dem Kontextqualifiziererwert verglichen, um eine Übereinstimmungsqualität zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="0b893-111">For each qualifier, candidate qualifiers are compared with the context qualifier value to determine a quality of match.</span></span> <span data-ttu-id="0b893-112">Die Durchführung des Vergleichs hängt dabei vom Qualifizierer ab.</span><span class="sxs-lookup"><span data-stu-id="0b893-112">How the comparison is done depends upon the qualifier.</span></span>

<span data-ttu-id="0b893-113">Für einige Qualifizierer, wie Skalierung und Kontrast, ergibt sich immer ein Mindestgrad an Übereinstimmung.</span><span class="sxs-lookup"><span data-stu-id="0b893-113">For some qualifiers, such as scale and contrast, there is always some minimal degree of match.</span></span> <span data-ttu-id="0b893-114">Für einen Kandidaten, der über eine Qualifizierung für „scale-100” verfügt, ergibt sich eine Teilübereinstimmung mit einen Kontext von „scale-400”, jedoch nicht in so hohem Maße wie für einen Kandidaten, die über eine Qualifizierung für „scale-200” oder „scale-400” (genaue Übereinstimmung) verfügen.</span><span class="sxs-lookup"><span data-stu-id="0b893-114">For example, a candidate qualified for "scale-100" matches a context of "scale-400" to some small degree, albeit not as well as a candidate qualified for "scale-200" or (for a perfect match) "scale-400".</span></span>

<span data-ttu-id="0b893-115">Für andere Qualifizierer, wie die Sprache oder den Wohnort, ist ein Vergleich ohne Übereinstimmung möglich (und auch mit Übereinstimmungsgrad).</span><span class="sxs-lookup"><span data-stu-id="0b893-115">For other qualifiers, however, such as language or home region, it is possible to have a non-match comparison (as well as degrees of matching).</span></span> <span data-ttu-id="0b893-116">Beispielsweise ergibt sich für einen Kandidaten, der für die Sprache als „en-US” qualifiziert wurde, zumindest bis zu einem gewissen Grad eine Übereinstimmung mit dem Kontext „en-GB”, während sich für einen als „fr” qualifizierten Kandidaten keinerlei Übereinstimmung ergibt.</span><span class="sxs-lookup"><span data-stu-id="0b893-116">For example, a candidate qualified for language as "en-US" is a partial match for a context of "en-GB", but a candidate qualified as "fr" is not a match at all.</span></span> <span data-ttu-id="0b893-117">Ebenso weist ein Kandidat, der für den Wohnort über die Qualifizierung „155” (Westeuropa) verfügt, eine recht gute Übereinstimmung mit einem Kontext für einen Benutzer mit der Wohnorteinstellung „FR” auf, während sich für einen Kandidaten mit der Qualifizierung „US” keinerlei Übereinstimmung ergibt.</span><span class="sxs-lookup"><span data-stu-id="0b893-117">Similarly, a candidate qualified for home region as "155" (Western Europe) matches a context for a user with a home region setting of "FR" somewhat well, but a candidate qualified as "US" does not match at all.</span></span>

<span data-ttu-id="0b893-118">Wenn beim Auswerten eines Kandidaten für einen Qualifizierer ein Vergleich ohne Übereinstimmung vorhanden ist, erhält der Kandidat eine Gesamteinstufung ohne Übereinstimmung und wird nicht ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="0b893-118">When a candidate is evaluated, if there is a non-match comparison for any qualifier, then that candidate will get an overall non-match ranking and will not be selected.</span></span> <span data-ttu-id="0b893-119">Auf diese Weise können die Qualifizierer mit höheren Prioritäten beim Auswählen der besten Übereinstimmung die höchste Gewichtung erhalten, aber auch ein Qualifizierer mit einer niedrigen Priorität kann einen Kandidaten aufgrund einer fehlenden Übereinstimmung eliminieren.</span><span class="sxs-lookup"><span data-stu-id="0b893-119">In this way, the higher-priority qualifiers can have the greatest weight in selecting the best match, but even a low-priority qualifier can eliminate a candidate due to a non-match.</span></span>

<span data-ttu-id="0b893-120">Ein Kandidat gilt in Bezug auf einen Qualifizierer als neutral, wenn er für den jeweiligen Qualifizierer keine Markierung erhält.</span><span class="sxs-lookup"><span data-stu-id="0b893-120">A candidate is neutral in relation to a qualifier if it is not marked for that qualifier at all.</span></span> <span data-ttu-id="0b893-121">Für alle Qualifizierer ergibt ein neutraler Kandidat immer eine Übereinstimmung für den Kontextqualifiziererwert. Dies ist jedoch immer eine niedrigere Übereinstimmungsqualität als für Kandidaten, die für diesen Qualifizierer bewertet wurden und einen bestimmten Übereinstimmungsgrad aufweisen (genau oder partiell).</span><span class="sxs-lookup"><span data-stu-id="0b893-121">For any qualifier, a neutral candidate is always a match for the context qualifier value, but only with a lower quality of match than any candidate that was marked for that qualifier and has some degree of match (exact or partial).</span></span> <span data-ttu-id="0b893-122">Falls beispielsweise Kandidaten für „en-US”, „en” und „fr” qualifiziert wurden und außerdem ein sprachneutraler Kandidat vorhanden ist, werden die Kandidaten für einen Kontext mit dem Sprachqualifiziererwert „en-GB” in der folgenden Reihenfolge eingestuft: „en”, „en-US”, neutral und „fr”.</span><span class="sxs-lookup"><span data-stu-id="0b893-122">For example, if we have candidates qualified for "en-US", "en", "fr", and also a language-neutral candidate, then for a context with a language qualifier value of "en-GB", the candidates will be ranked in the following order: "en", "en-US", neutral, and "fr".</span></span> <span data-ttu-id="0b893-123">Mit „fr” besteht in diesem Fall keinerlei Übereinstimmung, während die anderen Kandidaten teilweise übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0b893-123">In this case, "fr" does not match at all, while the other candidates match to some degree.</span></span>

<span data-ttu-id="0b893-124">Danach beginnt der Vorgang für die Gesamteinstufung, indem Kandidaten in Bezug auf den Qualifizierer mit der höchsten Priorität (Sprache) ausgewertet werden.</span><span class="sxs-lookup"><span data-stu-id="0b893-124">The overall ranking process begins by evaluating candidates in relation to the highest-priority qualifier, which is language.</span></span> <span data-ttu-id="0b893-125">Kandidaten ohne Übereinstimmung werden eliminiert.</span><span class="sxs-lookup"><span data-stu-id="0b893-125">Non-matches are eliminated.</span></span> <span data-ttu-id="0b893-126">Die verbleibenden Kandidaten werden nach ihrer Übereinstimmungsqualität für die Sprache eingestuft.</span><span class="sxs-lookup"><span data-stu-id="0b893-126">The remaining candidates are ranked in relation to their quality of match for language.</span></span> <span data-ttu-id="0b893-127">Falls es zu Gleichständen kommt, wird der Qualifizierer mit der nächsthöheren Priorität (Kontrast) herangezogen, um anhand der Übereinstimmungsqualität für den Kontrast zwischen Kandidaten mit der gleichen Einstufung zu entscheiden.</span><span class="sxs-lookup"><span data-stu-id="0b893-127">If there are any ties, then the next-highest-priority qualifier, contrast, is considered, using the quality of match for contrast to differentiate among tied candidates.</span></span> <span data-ttu-id="0b893-128">Nach dem Kontrast werden die verbleibenden Gleichstände mithilfe des Skalierungsqualifizierers und danach unter Verwendung so vieler Qualifizierer entschieden, wie für die Erreichung einer gut sortierten Einstufung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="0b893-128">After contrast, the scale qualifier is used to differentiate remaining ties, and so on through as many qualifiers as are needed to arrive at a well-ordered ranking.</span></span>

<span data-ttu-id="0b893-129">Wird aufgrund nicht mit dem Kontext übereinstimmender Qualifizierer keine der infrage kommenden Ressourcen in Betracht gezogen, sucht das Ressourcenladeprogramm in einem zweiten Durchlauf nach einer infrage kommenden Standardressource für die Anzeige.</span><span class="sxs-lookup"><span data-stu-id="0b893-129">If all candidates are removed from consideration due to qualifiers that don't match the context, the resource loader goes through a second pass looking for a default candidate to display.</span></span> <span data-ttu-id="0b893-130">Standardkandidaten werden während der Erstellung der PRI-Datei ermittelt. Mit ihrer Hilfe wird sichergestellt, dass für alle Laufzeitkontexte immer ein Kandidat ausgewählt werden kann.</span><span class="sxs-lookup"><span data-stu-id="0b893-130">Default candidates are determined during creation of the PRI file and are required to ensure there is always some candidate to select for any runtime context.</span></span> <span data-ttu-id="0b893-131">Stimmen Qualifizierer einer infrage kommenden Ressource nicht überein und sind auch nicht als Standard festgelegt, wird die betreffende Ressource gar nicht mehr in Betracht gezogen.</span><span class="sxs-lookup"><span data-stu-id="0b893-131">If a candidate has any qualifiers that don't match and aren't a default, that resource candidate is thrown permanently out of consideration.</span></span>

<span data-ttu-id="0b893-132">Alle weiterhin infrage kommenden Ressourcen werden vom Ressourcenladeprogramm anhand des Werts für den Kontextqualifizierer mit der höchsten Priorität ermittelt. Ausgewählt wird die Ressource mit der größten Übereinstimmung oder dem besten Standardwert.</span><span class="sxs-lookup"><span data-stu-id="0b893-132">For all the resource candidates still in consideration, the resource loader looks at the highest-priority context qualifier value and chooses the one that has the best match or best default score.</span></span> <span data-ttu-id="0b893-133">Jede tatsächliche Übereinstimmung wird höher als ein Standardwert bewertet.</span><span class="sxs-lookup"><span data-stu-id="0b893-133">Any actual match is considered better than a default score.</span></span>

<span data-ttu-id="0b893-134">Bei gleichrangigen Ressourcen wird der Wert für den Kontextqualifizierer mit der nächsthöchsten Priorität inspiziert. Dieser Vorgang wird solange fortgesetzt, bis die größtmögliche Übereinstimmung ermittelt ist.</span><span class="sxs-lookup"><span data-stu-id="0b893-134">If there is a tie, the next-highest priority context qualifier value is inspected and the process continues, until a best match is found.</span></span>

## <a name="example-of-choosing-a-resource-candidate"></a><span data-ttu-id="0b893-135">Beispiel für das Auswählen eines Ressourcenkandidaten</span><span class="sxs-lookup"><span data-stu-id="0b893-135">Example of choosing a resource candidate</span></span>

<span data-ttu-id="0b893-136">Berücksichtigen Sie diese Dateien.</span><span class="sxs-lookup"><span data-stu-id="0b893-136">Consider these files.</span></span>

```
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/logo.scale-100.jpg
fr/images/contrast-high/logo.scale-400.jpg
fr/images/contrast-high/logo.scale-100.jpg
de/images/logo.jpg
```

<span data-ttu-id="0b893-137">Und gehen Sie davon aus, das dies die Einstellungen im aktuellen Kontext sind.</span><span class="sxs-lookup"><span data-stu-id="0b893-137">And suppose that these are the settings in the current context.</span></span>

```
Application language: en-US; fr-FR;
Scale: 400
Contrast: Standard
```

<span data-ttu-id="0b893-138">Drei Dateien werden vom Ressourcenverwaltungssystem aussortiert. Der Grund hierfür ist, dass der hohe Kontrast und die Sprache Deutsch nicht mit dem in den Einstellungen festgelegten Kontext übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0b893-138">The Resource Management System eliminates three of the files, because high contrast and the German language do not match the context defined by the settings.</span></span> <span data-ttu-id="0b893-139">Diese Kandidaten verbleiben.</span><span class="sxs-lookup"><span data-stu-id="0b893-139">That leaves these candidates.</span></span>

```
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/logo.scale-100.jpg
```

<span data-ttu-id="0b893-140">Für die verbleibenden Kandidaten verwendet das Ressourcenverwaltungssystem den Kontextqualifizierer mit der höchsten Priorität: Sprache.</span><span class="sxs-lookup"><span data-stu-id="0b893-140">For those remaining candidates, the Resource Management System uses the highest-priority context qualifier, which is language.</span></span> <span data-ttu-id="0b893-141">Die englischen Ressourcen stimmen besser überein als die französischen, da Englisch in den Einstellungen vor Französisch aufgeführt ist.</span><span class="sxs-lookup"><span data-stu-id="0b893-141">The English resources are a closer match than the French ones because English is listed before French in the settings.</span></span>

```
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
```

<span data-ttu-id="0b893-142">Als Nächstes wird vom Ressourcenverwaltungssystem der Kontextqualifizierer mit der zweithöchsten Priorität verwendet: Skalierung.</span><span class="sxs-lookup"><span data-stu-id="0b893-142">Next, the Resource Management System uses the next-highest priority context qualifier, scale.</span></span> <span data-ttu-id="0b893-143">Das ist diese also die zurückgegebene Ressource.</span><span class="sxs-lookup"><span data-stu-id="0b893-143">So this is the resource returned.</span></span>

```
en/images/logo.scale-400.jpg
```

<span data-ttu-id="0b893-144">Mit der erweiterten Methode [**NamedResource.ResolveAll**](/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResource?branch=live#Windows_ApplicationModel_Resources_Core_NamedResource_ResolveAll_Windows_ApplicationModel_Resources_Core_ResourceContext_) können Sie alle Kandidaten in der Reihenfolge abrufen, in der sie mit den Kontexteinstellungen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0b893-144">You can use the advanced [**NamedResource.ResolveAll**](/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResource?branch=live#Windows_ApplicationModel_Resources_Core_NamedResource_ResolveAll_Windows_ApplicationModel_Resources_Core_ResourceContext_) method to retrieve all of the candidates in the order that they match the context settings.</span></span> <span data-ttu-id="0b893-145">Für das Beispiel, das wir gerade erläutert haben, gibt **ResolveAll** Kandidaten in dieser Reihenfolge zurück.</span><span class="sxs-lookup"><span data-stu-id="0b893-145">For the example we just walked through, **ResolveAll** returns candidates in this order.</span></span>

```
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/logo.scale-100.jpg
```

## <a name="example-of-producing-a-fallback-choice"></a><span data-ttu-id="0b893-146">Beispiel für das Erzeugen einer Fallbackauswahl</span><span class="sxs-lookup"><span data-stu-id="0b893-146">Example of producing a fallback choice</span></span>

<span data-ttu-id="0b893-147">Gehen Sie von diesen Dateien aus.</span><span class="sxs-lookup"><span data-stu-id="0b893-147">Consider these files.</span></span>

```
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/contrast-standard/logo.scale-400.jpg
fr/images/contrast-standard/logo.scale-100.jpg
de/images/contrast-standard/logo.jpg
```

<span data-ttu-id="0b893-148">Und gehen Sie davon aus, das dies die Einstellungen im aktuellen Kontext sind.</span><span class="sxs-lookup"><span data-stu-id="0b893-148">And suppose that these are the settings in the current context.</span></span>

```
User language: de-DE;
Scale: 400
Contrast: High
```

<span data-ttu-id="0b893-149">Alle Dateien werden gelöscht, da sie nicht mit dem Kontext übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0b893-149">All the files are eliminated because they do not match the context.</span></span> <span data-ttu-id="0b893-150">Nun wird ein Standarddurchlauf durchgeführt. Beim Erstellen der PRI-Datei wurde folgende Standardeinstellung (siehe [Manuelles Kompilieren von Ressourcen mit MakePRI.exe](compile-resources-manually-with-makepri.md)) verwendet:</span><span class="sxs-lookup"><span data-stu-id="0b893-150">So we enter a default pass, where the default (see [Compile resources manually with MakePri.exe](compile-resources-manually-with-makepri.md)) during creation of the PRI file was this.</span></span>

```
Language: fr-FR;
Scale: 400
Contrast: Standard
```

<span data-ttu-id="0b893-151">Übrig bleiben alle Ressourcen, die entweder mit dem aktuellen Benutzer oder mit der Standardeinstellung übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0b893-151">This leaves all the resources that match either the current user or the default.</span></span>

```
fr/images/contrast-standard/logo.scale-400.jpg
fr/images/contrast-standard/logo.scale-100.jpg
de/images/contrast-standard/logo.jpg
```

<span data-ttu-id="0b893-152">Das Ressourcenverwaltungssystem verwendet den Kontextqualifizierer mit der höchsten Priorität (Sprache), um die benannte Ressource mit dem höchsten Wert zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="0b893-152">The Resource Management System uses the highest-priority context qualifier, language, to return the named resource with the highest score.</span></span>

```
de/images/contrast-standard/logo.jpg
```

## <a name="important-apis"></a><span data-ttu-id="0b893-153">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="0b893-153">Important APIs</span></span>

* [<span data-ttu-id="0b893-154">NamedResource.ResolveAll</span><span class="sxs-lookup"><span data-stu-id="0b893-154">NamedResource.ResolveAll</span></span>](/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResource?branch=live#Windows_ApplicationModel_Resources_Core_NamedResource_ResolveAll_Windows_ApplicationModel_Resources_Core_ResourceContext_)

## <a name="related-topics"></a><span data-ttu-id="0b893-155">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="0b893-155">Related topics</span></span>

* [<span data-ttu-id="0b893-156">Manuelles Kompilieren von Ressourcen mit MakePri.exe</span><span class="sxs-lookup"><span data-stu-id="0b893-156">Compile resources manually with MakePri.exe</span></span>](compile-resources-manually-with-makepri.md)