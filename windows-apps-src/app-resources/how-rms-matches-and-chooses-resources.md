---
Description: When a resource is requested, there may be several candidates that match the current resource context to some degree. The Resource Management System will analyze all of the candidates and determine the best candidate to return. This topic describes that process in detail and gives examples.
title: Wie das Ressourcenverwaltungssystem Ressourcen zuordnet und auswählt
template: detail.hbs
ms.date: 10/23/2017
ms.topic: article
keywords: Windows10, uwp, Ressourcen, Bild, Element, MRT, Qualifizierer
ms.localizationpriority: medium
ms.openlocfilehash: de34411d9c7d226857214472e691dd6b41f10a18
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8943460"
---
# <a name="how-the-resource-management-system-matches-and-chooses-resources"></a><span data-ttu-id="0495e-103">Wie das Ressourcenverwaltungssystem Ressourcen zuordnet und auswählt</span><span class="sxs-lookup"><span data-stu-id="0495e-103">How the Resource Management System matches and chooses resources</span></span>
<span data-ttu-id="0495e-104">Wenn eine Ressource angefordert wird, kann es mehrere Kandidaten geben, für die sich in einem gewissen Maße eine Übereinstimmung mit dem aktuellen Ressourcenkontext ergibt.</span><span class="sxs-lookup"><span data-stu-id="0495e-104">When a resource is requested, there may be several candidates that match the current resource context to some degree.</span></span> <span data-ttu-id="0495e-105">Vom Ressourcenverwaltungssystem werden alle Kandidaten analysiert, und der beste Kandidat für die Rückgabe wird ermittelt.</span><span class="sxs-lookup"><span data-stu-id="0495e-105">The Resource Management System will analyze all of the candidates and determine the best candidate to return.</span></span> <span data-ttu-id="0495e-106">Dazu werden alle Qualifizierer einbezogen, um eine Einstufung aller Kandidaten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="0495e-106">This is done by taking all qualifiers into consideration to rank all of the candidates.</span></span>

<span data-ttu-id="0495e-107">Bei diesem Einstufungsvorgang werden den unterschiedlichen Qualifizierern unterschiedliche Prioritäten zugewiesen: Die Sprache hat die größte Auswirkung auf die Gesamteinstufung, gefolgt von Kontrast, Skalierung usw.</span><span class="sxs-lookup"><span data-stu-id="0495e-107">In this ranking process, the different qualifiers are given different priorities: language has the greatest impact on the overall ranking, followed by contrast, then scale, and so on.</span></span> <span data-ttu-id="0495e-108">Für jeden Qualifizierer werden Kandidatenqualifizierer mit dem Kontextqualifiziererwert verglichen, um eine Übereinstimmungsqualität zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="0495e-108">For each qualifier, candidate qualifiers are compared with the context qualifier value to determine a quality of match.</span></span> <span data-ttu-id="0495e-109">Die Durchführung des Vergleichs hängt dabei vom Qualifizierer ab.</span><span class="sxs-lookup"><span data-stu-id="0495e-109">How the comparison is done depends upon the qualifier.</span></span>

<span data-ttu-id="0495e-110">Bestimmte Informationen zur Funktionsweise des Vergleichs von Sprachtags finden Sie unter [Wie das Ressourcenverwaltungssystem Sprachtags zuordnet](how-rms-matches-lang-tags.md).</span><span class="sxs-lookup"><span data-stu-id="0495e-110">For specific details on how language tag matching is done, see [How the Resource Management System matches language tags](how-rms-matches-lang-tags.md).</span></span>

<span data-ttu-id="0495e-111">Für einige Qualifizierer, wie Skalierung und Kontrast, ergibt sich immer ein Mindestgrad an Übereinstimmung.</span><span class="sxs-lookup"><span data-stu-id="0495e-111">For some qualifiers, such as scale and contrast, there is always some minimal degree of match.</span></span> <span data-ttu-id="0495e-112">Beispielsweise weist ein Kandidat für "Scale-100"entspricht einen Kontext von "Scale-400", ergibt sich, wenn auch nicht sowie eine Qualifizierung für"Scale-200"oder (für ein identisches)"Scale-400".</span><span class="sxs-lookup"><span data-stu-id="0495e-112">For example, a candidate qualified for"scale-100"matches a context of"scale-400"to some small degree, albeit not as well as a candidate qualified for"scale-200"or (for a perfect match)"scale-400".</span></span>

<span data-ttu-id="0495e-113">Für andere Qualifizierer, wie die Sprache oder den Wohnort, ist ein Vergleich ohne Übereinstimmung möglich (und auch mit Übereinstimmungsgrad).</span><span class="sxs-lookup"><span data-stu-id="0495e-113">For other qualifiers, however, such as language or home region, it is possible to have a non-match comparison (as well as degrees of matching).</span></span> <span data-ttu-id="0495e-114">Beispielsweise ergibt sich für einen Kandidaten, der für die Sprache als „en-US” qualifiziert wurde, zumindest bis zu einem gewissen Grad eine Übereinstimmung mit dem Kontext „en-GB”, während sich für einen als „fr” qualifizierten Kandidaten keinerlei Übereinstimmung ergibt.</span><span class="sxs-lookup"><span data-stu-id="0495e-114">For example, a candidate qualified for language as "en-US" is a partial match for a context of "en-GB", but a candidate qualified as "fr" is not a match at all.</span></span> <span data-ttu-id="0495e-115">Ebenso weist ein Kandidat, der für den Wohnort über die Qualifizierung „155” (Westeuropa) verfügt, eine recht gute Übereinstimmung mit einem Kontext für einen Benutzer mit der Wohnorteinstellung „FR” auf, während sich für einen Kandidaten mit der Qualifizierung „US” keinerlei Übereinstimmung ergibt.</span><span class="sxs-lookup"><span data-stu-id="0495e-115">Similarly, a candidate qualified for home region as "155" (Western Europe) matches a context for a user with a home region setting of "FR" somewhat well, but a candidate qualified as "US" does not match at all.</span></span>

<span data-ttu-id="0495e-116">Wenn beim Auswerten eines Kandidaten für einen Qualifizierer ein Vergleich ohne Übereinstimmung vorhanden ist, erhält der Kandidat eine Gesamteinstufung ohne Übereinstimmung und wird nicht ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="0495e-116">When a candidate is evaluated, if there is a non-match comparison for any qualifier, then that candidate will get an overall non-match ranking and will not be selected.</span></span> <span data-ttu-id="0495e-117">Auf diese Weise können die Qualifizierer mit höheren Prioritäten beim Auswählen der besten Übereinstimmung die höchste Gewichtung erhalten, aber auch ein Qualifizierer mit einer niedrigen Priorität kann einen Kandidaten aufgrund einer fehlenden Übereinstimmung eliminieren.</span><span class="sxs-lookup"><span data-stu-id="0495e-117">In this way, the higher-priority qualifiers can have the greatest weight in selecting the best match, but even a low-priority qualifier can eliminate a candidate due to a non-match.</span></span>

<span data-ttu-id="0495e-118">Ein Kandidat gilt in Bezug auf einen Qualifizierer als neutral, wenn er für den jeweiligen Qualifizierer keine Markierung erhält.</span><span class="sxs-lookup"><span data-stu-id="0495e-118">A candidate is neutral in relation to a qualifier if it is not marked for that qualifier at all.</span></span> <span data-ttu-id="0495e-119">Für alle Qualifizierer ergibt ein neutraler Kandidat immer eine Übereinstimmung für den Kontextqualifiziererwert. Dies ist jedoch immer eine niedrigere Übereinstimmungsqualität als für Kandidaten, die für diesen Qualifizierer bewertet wurden und einen bestimmten Übereinstimmungsgrad aufweisen (genau oder partiell).</span><span class="sxs-lookup"><span data-stu-id="0495e-119">For any qualifier, a neutral candidate is always a match for the context qualifier value, but only with a lower quality of match than any candidate that was marked for that qualifier and has some degree of match (exact or partial).</span></span> <span data-ttu-id="0495e-120">Falls beispielsweise Kandidaten für „en-US”, „en” und „fr” qualifiziert wurden und außerdem ein sprachneutraler Kandidat vorhanden ist, werden die Kandidaten für einen Kontext mit dem Sprachqualifiziererwert „en-GB” in der folgenden Reihenfolge eingestuft: „en”, „en-US”, neutral und „fr”.</span><span class="sxs-lookup"><span data-stu-id="0495e-120">For example, if we have candidates qualified for "en-US", "en", "fr", and also a language-neutral candidate, then for a context with a language qualifier value of "en-GB", the candidates will be ranked in the following order: "en", "en-US", neutral, and "fr".</span></span> <span data-ttu-id="0495e-121">Mit „fr” besteht in diesem Fall keinerlei Übereinstimmung, während die anderen Kandidaten teilweise übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0495e-121">In this case, "fr" does not match at all, while the other candidates match to some degree.</span></span>

<span data-ttu-id="0495e-122">Danach beginnt der Vorgang für die Gesamteinstufung, indem Kandidaten in Bezug auf den Qualifizierer mit der höchsten Priorität (Sprache) ausgewertet werden.</span><span class="sxs-lookup"><span data-stu-id="0495e-122">The overall ranking process begins by evaluating candidates in relation to the highest-priority qualifier, which is language.</span></span> <span data-ttu-id="0495e-123">Kandidaten ohne Übereinstimmung werden eliminiert.</span><span class="sxs-lookup"><span data-stu-id="0495e-123">Non-matches are eliminated.</span></span> <span data-ttu-id="0495e-124">Die verbleibenden Kandidaten werden nach ihrer Übereinstimmungsqualität für die Sprache eingestuft.</span><span class="sxs-lookup"><span data-stu-id="0495e-124">The remaining candidates are ranked in relation to their quality of match for language.</span></span> <span data-ttu-id="0495e-125">Falls es zu Gleichständen kommt, wird der Qualifizierer mit der nächsthöheren Priorität (Kontrast) herangezogen, um anhand der Übereinstimmungsqualität für den Kontrast zwischen Kandidaten mit der gleichen Einstufung zu entscheiden.</span><span class="sxs-lookup"><span data-stu-id="0495e-125">If there are any ties, then the next-highest-priority qualifier, contrast, is considered, using the quality of match for contrast to differentiate among tied candidates.</span></span> <span data-ttu-id="0495e-126">Nach dem Kontrast werden die verbleibenden Gleichstände mithilfe des Skalierungsqualifizierers und danach unter Verwendung so vieler Qualifizierer entschieden, wie für die Erreichung einer gut sortierten Einstufung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="0495e-126">After contrast, the scale qualifier is used to differentiate remaining ties, and so on through as many qualifiers as are needed to arrive at a well-ordered ranking.</span></span>

<span data-ttu-id="0495e-127">Wird aufgrund nicht mit dem Kontext übereinstimmender Qualifizierer keine der infrage kommenden Ressourcen in Betracht gezogen, sucht das Ressourcenladeprogramm in einem zweiten Durchlauf nach einer infrage kommenden Standardressource für die Anzeige.</span><span class="sxs-lookup"><span data-stu-id="0495e-127">If all candidates are removed from consideration due to qualifiers that don't match the context, the resource loader goes through a second pass looking for a default candidate to display.</span></span> <span data-ttu-id="0495e-128">Standardkandidaten werden während der Erstellung der PRI-Datei ermittelt. Mit ihrer Hilfe wird sichergestellt, dass für alle Laufzeitkontexte immer ein Kandidat ausgewählt werden kann.</span><span class="sxs-lookup"><span data-stu-id="0495e-128">Default candidates are determined during creation of the PRI file and are required to ensure there is always some candidate to select for any runtime context.</span></span> <span data-ttu-id="0495e-129">Stimmen Qualifizierer einer infrage kommenden Ressource nicht überein und sind auch nicht als Standard festgelegt, wird die betreffende Ressource gar nicht mehr in Betracht gezogen.</span><span class="sxs-lookup"><span data-stu-id="0495e-129">If a candidate has any qualifiers that don't match and aren't a default, that resource candidate is thrown permanently out of consideration.</span></span>

<span data-ttu-id="0495e-130">Alle weiterhin infrage kommenden Ressourcen werden vom Ressourcenladeprogramm anhand des Werts für den Kontextqualifizierer mit der höchsten Priorität ermittelt. Ausgewählt wird die Ressource mit der größten Übereinstimmung oder dem besten Standardwert.</span><span class="sxs-lookup"><span data-stu-id="0495e-130">For all the resource candidates still in consideration, the resource loader looks at the highest-priority context qualifier value and chooses the one that has the best match or best default score.</span></span> <span data-ttu-id="0495e-131">Jede tatsächliche Übereinstimmung wird höher als ein Standardwert bewertet.</span><span class="sxs-lookup"><span data-stu-id="0495e-131">Any actual match is considered better than a default score.</span></span>

<span data-ttu-id="0495e-132">Bei gleichrangigen Ressourcen wird der Wert für den Kontextqualifizierer mit der nächsthöchsten Priorität inspiziert. Dieser Vorgang wird solange fortgesetzt, bis die größtmögliche Übereinstimmung ermittelt ist.</span><span class="sxs-lookup"><span data-stu-id="0495e-132">If there is a tie, the next-highest priority context qualifier value is inspected and the process continues, until a best match is found.</span></span>

## <a name="example-of-choosing-a-resource-candidate"></a><span data-ttu-id="0495e-133">Beispiel für das Auswählen eines Ressourcenkandidaten</span><span class="sxs-lookup"><span data-stu-id="0495e-133">Example of choosing a resource candidate</span></span>
<span data-ttu-id="0495e-134">Berücksichtigen Sie diese Dateien.</span><span class="sxs-lookup"><span data-stu-id="0495e-134">Consider these files.</span></span>

```console
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/logo.scale-100.jpg
fr/images/contrast-high/logo.scale-400.jpg
fr/images/contrast-high/logo.scale-100.jpg
de/images/logo.jpg
```

<span data-ttu-id="0495e-135">Und gehen Sie davon aus, das dies die Einstellungen im aktuellen Kontext sind.</span><span class="sxs-lookup"><span data-stu-id="0495e-135">And suppose that these are the settings in the current context.</span></span>

```console
Application language: en-US; fr-FR;
Scale: 400
Contrast: Standard
```

<span data-ttu-id="0495e-136">Drei Dateien werden vom Ressourcenverwaltungssystem aussortiert. Der Grund hierfür ist, dass der hohe Kontrast und die Sprache Deutsch nicht mit dem in den Einstellungen festgelegten Kontext übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0495e-136">The Resource Management System eliminates three of the files, because high contrast and the German language do not match the context defined by the settings.</span></span> <span data-ttu-id="0495e-137">Diese Kandidaten verbleiben.</span><span class="sxs-lookup"><span data-stu-id="0495e-137">That leaves these candidates.</span></span>

```console
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/logo.scale-100.jpg
```

<span data-ttu-id="0495e-138">Für die verbleibenden Kandidaten verwendet das Ressourcenverwaltungssystem den Kontextqualifizierer mit der höchsten Priorität: Sprache.</span><span class="sxs-lookup"><span data-stu-id="0495e-138">For those remaining candidates, the Resource Management System uses the highest-priority context qualifier, which is language.</span></span> <span data-ttu-id="0495e-139">Die englischen Ressourcen stimmen besser überein als die französischen, da Englisch in den Einstellungen vor Französisch aufgeführt ist.</span><span class="sxs-lookup"><span data-stu-id="0495e-139">The English resources are a closer match than the French ones because English is listed before French in the settings.</span></span>

```console
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
```

<span data-ttu-id="0495e-140">Als Nächstes wird vom Ressourcenverwaltungssystem der Kontextqualifizierer mit der zweithöchsten Priorität verwendet: Skalierung.</span><span class="sxs-lookup"><span data-stu-id="0495e-140">Next, the Resource Management System uses the next-highest priority context qualifier, scale.</span></span> <span data-ttu-id="0495e-141">Das ist diese also die zurückgegebene Ressource.</span><span class="sxs-lookup"><span data-stu-id="0495e-141">So this is the resource returned.</span></span>

```console
en/images/logo.scale-400.jpg
```

<span data-ttu-id="0495e-142">Mit der erweiterten Methode [**NamedResource.ResolveAll**](/uwp/api/windows.applicationmodel.resources.core.namedresource.resolveall?branch=live) können Sie alle Kandidaten in der Reihenfolge abrufen, in der sie mit den Kontexteinstellungen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0495e-142">You can use the advanced [**NamedResource.ResolveAll**](/uwp/api/windows.applicationmodel.resources.core.namedresource.resolveall?branch=live) method to retrieve all of the candidates in the order that they match the context settings.</span></span> <span data-ttu-id="0495e-143">Für das Beispiel, das wir gerade erläutert haben, gibt **ResolveAll** Kandidaten in dieser Reihenfolge zurück.</span><span class="sxs-lookup"><span data-stu-id="0495e-143">For the example we just walked through, **ResolveAll** returns candidates in this order.</span></span>

```console
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/logo.scale-100.jpg
```

## <a name="example-of-producing-a-fallback-choice"></a><span data-ttu-id="0495e-144">Beispiel für das Erzeugen einer Fallbackauswahl</span><span class="sxs-lookup"><span data-stu-id="0495e-144">Example of producing a fallback choice</span></span>
<span data-ttu-id="0495e-145">Gehen Sie von diesen Dateien aus.</span><span class="sxs-lookup"><span data-stu-id="0495e-145">Consider these files.</span></span>

```console
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/contrast-standard/logo.scale-400.jpg
fr/images/contrast-standard/logo.scale-100.jpg
de/images/contrast-standard/logo.jpg
```

<span data-ttu-id="0495e-146">Und gehen Sie davon aus, das dies die Einstellungen im aktuellen Kontext sind.</span><span class="sxs-lookup"><span data-stu-id="0495e-146">And suppose that these are the settings in the current context.</span></span>

```console
User language: de-DE;
Scale: 400
Contrast: High
```

<span data-ttu-id="0495e-147">Alle Dateien werden gelöscht, da sie nicht mit dem Kontext übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0495e-147">All the files are eliminated because they do not match the context.</span></span> <span data-ttu-id="0495e-148">Nun wird ein Standarddurchlauf durchgeführt. Beim Erstellen der PRI-Datei wurde folgende Standardeinstellung (siehe [Manuelles Kompilieren von Ressourcen mit MakePRI.exe](compile-resources-manually-with-makepri.md)) verwendet:</span><span class="sxs-lookup"><span data-stu-id="0495e-148">So we enter a default pass, where the default (see [Compile resources manually with MakePri.exe](compile-resources-manually-with-makepri.md)) during creation of the PRI file was this.</span></span>

```console
Language: fr-FR;
Scale: 400
Contrast: Standard
```

<span data-ttu-id="0495e-149">Übrig bleiben alle Ressourcen, die entweder mit dem aktuellen Benutzer oder mit der Standardeinstellung übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0495e-149">This leaves all the resources that match either the current user or the default.</span></span>

```console
fr/images/contrast-standard/logo.scale-400.jpg
fr/images/contrast-standard/logo.scale-100.jpg
de/images/contrast-standard/logo.jpg
```

<span data-ttu-id="0495e-150">Das Ressourcenverwaltungssystem verwendet den Kontextqualifizierer mit der höchsten Priorität (Sprache), um die benannte Ressource mit dem höchsten Wert zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="0495e-150">The Resource Management System uses the highest-priority context qualifier, language, to return the named resource with the highest score.</span></span>

```console
de/images/contrast-standard/logo.jpg
```

## <a name="important-apis"></a><span data-ttu-id="0495e-151">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="0495e-151">Important APIs</span></span>
* [<span data-ttu-id="0495e-152">NamedResource.ResolveAll</span><span class="sxs-lookup"><span data-stu-id="0495e-152">NamedResource.ResolveAll</span></span>](/uwp/api/windows.applicationmodel.resources.core.namedresource.resolveall?branch=live)

## <a name="related-topics"></a><span data-ttu-id="0495e-153">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="0495e-153">Related topics</span></span>
* [<span data-ttu-id="0495e-154">Manuelles Kompilieren von Ressourcen mit MakePri.exe</span><span class="sxs-lookup"><span data-stu-id="0495e-154">Compile resources manually with MakePri.exe</span></span>](compile-resources-manually-with-makepri.md)