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

# <a name="how-the-resource-management-system-matches-and-chooses-resources"></a>Wie das Ressourcenverwaltungssystem Ressourcen zuordnet und auswählt

Wenn eine Ressource angefordert wird, kann es mehrere Kandidaten geben, für die sich in einem gewissen Maße eine Übereinstimmung mit dem aktuellen Ressourcenkontext ergibt. Vom Ressourcenverwaltungssystem werden alle Kandidaten analysiert, und der beste Kandidat für die Rückgabe wird ermittelt. Dazu werden alle Qualifizierer einbezogen, um eine Einstufung aller Kandidaten zu erhalten.

Bei diesem Einstufungsvorgang werden den unterschiedlichen Qualifizierern unterschiedliche Prioritäten zugewiesen: Die Sprache hat die größte Auswirkung auf die Gesamteinstufung, gefolgt von Kontrast, Skalierung usw. Für jeden Qualifizierer werden Kandidatenqualifizierer mit dem Kontextqualifiziererwert verglichen, um eine Übereinstimmungsqualität zu ermitteln. Die Durchführung des Vergleichs hängt dabei vom Qualifizierer ab.

Für einige Qualifizierer, wie Skalierung und Kontrast, ergibt sich immer ein Mindestgrad an Übereinstimmung. Für einen Kandidaten, der über eine Qualifizierung für „scale-100” verfügt, ergibt sich eine Teilübereinstimmung mit einen Kontext von „scale-400”, jedoch nicht in so hohem Maße wie für einen Kandidaten, die über eine Qualifizierung für „scale-200” oder „scale-400” (genaue Übereinstimmung) verfügen.

Für andere Qualifizierer, wie die Sprache oder den Wohnort, ist ein Vergleich ohne Übereinstimmung möglich (und auch mit Übereinstimmungsgrad). Beispielsweise ergibt sich für einen Kandidaten, der für die Sprache als „en-US” qualifiziert wurde, zumindest bis zu einem gewissen Grad eine Übereinstimmung mit dem Kontext „en-GB”, während sich für einen als „fr” qualifizierten Kandidaten keinerlei Übereinstimmung ergibt. Ebenso weist ein Kandidat, der für den Wohnort über die Qualifizierung „155” (Westeuropa) verfügt, eine recht gute Übereinstimmung mit einem Kontext für einen Benutzer mit der Wohnorteinstellung „FR” auf, während sich für einen Kandidaten mit der Qualifizierung „US” keinerlei Übereinstimmung ergibt.

Wenn beim Auswerten eines Kandidaten für einen Qualifizierer ein Vergleich ohne Übereinstimmung vorhanden ist, erhält der Kandidat eine Gesamteinstufung ohne Übereinstimmung und wird nicht ausgewählt. Auf diese Weise können die Qualifizierer mit höheren Prioritäten beim Auswählen der besten Übereinstimmung die höchste Gewichtung erhalten, aber auch ein Qualifizierer mit einer niedrigen Priorität kann einen Kandidaten aufgrund einer fehlenden Übereinstimmung eliminieren.

Ein Kandidat gilt in Bezug auf einen Qualifizierer als neutral, wenn er für den jeweiligen Qualifizierer keine Markierung erhält. Für alle Qualifizierer ergibt ein neutraler Kandidat immer eine Übereinstimmung für den Kontextqualifiziererwert. Dies ist jedoch immer eine niedrigere Übereinstimmungsqualität als für Kandidaten, die für diesen Qualifizierer bewertet wurden und einen bestimmten Übereinstimmungsgrad aufweisen (genau oder partiell). Falls beispielsweise Kandidaten für „en-US”, „en” und „fr” qualifiziert wurden und außerdem ein sprachneutraler Kandidat vorhanden ist, werden die Kandidaten für einen Kontext mit dem Sprachqualifiziererwert „en-GB” in der folgenden Reihenfolge eingestuft: „en”, „en-US”, neutral und „fr”. Mit „fr” besteht in diesem Fall keinerlei Übereinstimmung, während die anderen Kandidaten teilweise übereinstimmen.

Danach beginnt der Vorgang für die Gesamteinstufung, indem Kandidaten in Bezug auf den Qualifizierer mit der höchsten Priorität (Sprache) ausgewertet werden. Kandidaten ohne Übereinstimmung werden eliminiert. Die verbleibenden Kandidaten werden nach ihrer Übereinstimmungsqualität für die Sprache eingestuft. Falls es zu Gleichständen kommt, wird der Qualifizierer mit der nächsthöheren Priorität (Kontrast) herangezogen, um anhand der Übereinstimmungsqualität für den Kontrast zwischen Kandidaten mit der gleichen Einstufung zu entscheiden. Nach dem Kontrast werden die verbleibenden Gleichstände mithilfe des Skalierungsqualifizierers und danach unter Verwendung so vieler Qualifizierer entschieden, wie für die Erreichung einer gut sortierten Einstufung erforderlich sind.

Wird aufgrund nicht mit dem Kontext übereinstimmender Qualifizierer keine der infrage kommenden Ressourcen in Betracht gezogen, sucht das Ressourcenladeprogramm in einem zweiten Durchlauf nach einer infrage kommenden Standardressource für die Anzeige. Standardkandidaten werden während der Erstellung der PRI-Datei ermittelt. Mit ihrer Hilfe wird sichergestellt, dass für alle Laufzeitkontexte immer ein Kandidat ausgewählt werden kann. Stimmen Qualifizierer einer infrage kommenden Ressource nicht überein und sind auch nicht als Standard festgelegt, wird die betreffende Ressource gar nicht mehr in Betracht gezogen.

Alle weiterhin infrage kommenden Ressourcen werden vom Ressourcenladeprogramm anhand des Werts für den Kontextqualifizierer mit der höchsten Priorität ermittelt. Ausgewählt wird die Ressource mit der größten Übereinstimmung oder dem besten Standardwert. Jede tatsächliche Übereinstimmung wird höher als ein Standardwert bewertet.

Bei gleichrangigen Ressourcen wird der Wert für den Kontextqualifizierer mit der nächsthöchsten Priorität inspiziert. Dieser Vorgang wird solange fortgesetzt, bis die größtmögliche Übereinstimmung ermittelt ist.

## <a name="example-of-choosing-a-resource-candidate"></a>Beispiel für das Auswählen eines Ressourcenkandidaten

Berücksichtigen Sie diese Dateien.

```
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/logo.scale-100.jpg
fr/images/contrast-high/logo.scale-400.jpg
fr/images/contrast-high/logo.scale-100.jpg
de/images/logo.jpg
```

Und gehen Sie davon aus, das dies die Einstellungen im aktuellen Kontext sind.

```
Application language: en-US; fr-FR;
Scale: 400
Contrast: Standard
```

Drei Dateien werden vom Ressourcenverwaltungssystem aussortiert. Der Grund hierfür ist, dass der hohe Kontrast und die Sprache Deutsch nicht mit dem in den Einstellungen festgelegten Kontext übereinstimmen. Diese Kandidaten verbleiben.

```
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/logo.scale-100.jpg
```

Für die verbleibenden Kandidaten verwendet das Ressourcenverwaltungssystem den Kontextqualifizierer mit der höchsten Priorität: Sprache. Die englischen Ressourcen stimmen besser überein als die französischen, da Englisch in den Einstellungen vor Französisch aufgeführt ist.

```
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
```

Als Nächstes wird vom Ressourcenverwaltungssystem der Kontextqualifizierer mit der zweithöchsten Priorität verwendet: Skalierung. Das ist diese also die zurückgegebene Ressource.

```
en/images/logo.scale-400.jpg
```

Mit der erweiterten Methode [**NamedResource.ResolveAll**](/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResource?branch=live#Windows_ApplicationModel_Resources_Core_NamedResource_ResolveAll_Windows_ApplicationModel_Resources_Core_ResourceContext_) können Sie alle Kandidaten in der Reihenfolge abrufen, in der sie mit den Kontexteinstellungen übereinstimmen. Für das Beispiel, das wir gerade erläutert haben, gibt **ResolveAll** Kandidaten in dieser Reihenfolge zurück.

```
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/logo.scale-100.jpg
```

## <a name="example-of-producing-a-fallback-choice"></a>Beispiel für das Erzeugen einer Fallbackauswahl

Gehen Sie von diesen Dateien aus.

```
en/images/logo.scale-400.jpg
en/images/logo.scale-200.jpg
en/images/logo.scale-100.jpg  
fr/images/contrast-standard/logo.scale-400.jpg
fr/images/contrast-standard/logo.scale-100.jpg
de/images/contrast-standard/logo.jpg
```

Und gehen Sie davon aus, das dies die Einstellungen im aktuellen Kontext sind.

```
User language: de-DE;
Scale: 400
Contrast: High
```

Alle Dateien werden gelöscht, da sie nicht mit dem Kontext übereinstimmen. Nun wird ein Standarddurchlauf durchgeführt. Beim Erstellen der PRI-Datei wurde folgende Standardeinstellung (siehe [Manuelles Kompilieren von Ressourcen mit MakePRI.exe](compile-resources-manually-with-makepri.md)) verwendet:

```
Language: fr-FR;
Scale: 400
Contrast: Standard
```

Übrig bleiben alle Ressourcen, die entweder mit dem aktuellen Benutzer oder mit der Standardeinstellung übereinstimmen.

```
fr/images/contrast-standard/logo.scale-400.jpg
fr/images/contrast-standard/logo.scale-100.jpg
de/images/contrast-standard/logo.jpg
```

Das Ressourcenverwaltungssystem verwendet den Kontextqualifizierer mit der höchsten Priorität (Sprache), um die benannte Ressource mit dem höchsten Wert zurückzugeben.

```
de/images/contrast-standard/logo.jpg
```

## <a name="important-apis"></a>Wichtige APIs

* [NamedResource.ResolveAll](/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResource?branch=live#Windows_ApplicationModel_Resources_Core_NamedResource_ResolveAll_Windows_ApplicationModel_Resources_Core_ResourceContext_)

## <a name="related-topics"></a>Verwandte Themen

* [Manuelles Kompilieren von Ressourcen mit MakePri.exe](compile-resources-manually-with-makepri.md)