---
author: jnHs
Description: When you finish creating your app's submission and click Submit to the Store, the submission enters the certification step.
title: Der App-Zertifizierungsprozess
ms.assetid: 0DCB4344-224D-4E5A-899F-FF7A89F23DBC
ms.author: wdg-dev-content
ms.date: 07/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, veröffentlichen, vorverarbeitung, Zertifizierung, freigeben, Ausstehend, übermitteln, veröffentlichen, Status, Zeit
ms.localizationpriority: medium
ms.openlocfilehash: 8372f316786d83d72dff8ef7a0a8fd53e5390743
ms.sourcegitcommit: 72835733ec429a5deb6a11da4112336746e5e9cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5157755"
---
# <a name="the-app-certification-process"></a>Der App-Zertifizierungsprozess

Nachdem Sie die App-Einreichung fertig gestellt haben und auf **An Store übermitteln** klicken, tritt die Übermittlung in die Zertifizierungsphase ein. Dieser Vorgang ist in der Regel innerhalb weniger Stunden abgeschlossen, kann in Einzelfällen aber bis zu drei Arbeitstage dauern. Nach der Zertifizierung der Übermittlung kann es bis finden in der app Eintrag für eine neue Übermittlung oder für eine aktualisierte Übermittlung mit Änderungen auf Pakete für Kunden bis zu 24 Stunden dauern. Wenn Ihre Update nur Store-Eintrag anzeigen ändert, wird der Veröffentlichungsprozess in weniger als einer Stunde abgeschlossen werden.  Sie werden benachrichtigt, wenn Ihre Übermittlung veröffentlicht wird, und der app Status im Dashboard **Im Store werden**.

## <a name="preprocessing"></a>Vorverarbeitung

Nach dem erfolgreichen Hochladen der App-Pakete und dem Übermitteln der App zur Zertifizierung werden die Pakete zum Testen in die Warteschlange eingereiht. Es wird eine Meldung angezeigt, wenn während der Vorverarbeitung Fehler erkannt werden. Weitere Informationen zu möglichen Fehlern finden Sie unter [Fehler bei der Einreichung](resolve-submission-errors.md).

## <a name="certification"></a>Zertifizierung

Während dieser Phase werden mehrere Tests durchgeführt:

-   **Sicherheitstests:** Dieser erste Test überprüft die Pakete Ihrer App auf Viren und Schadsoftware. Besteht Ihre App diesen Test nicht, müssen Sie Ihr Entwicklungssystem überprüfen, indem Sie die aktuelle Antivirensoftware ausführen und Ihr App-Paket anschließend in einem bereinigten System neu erstellen.
-   **Tests bezgl. der Erfüllung technischer Anforderungen:** Die Erfüllung technischer Anforderungen wird mithilfe des Zertifizierungskits für Windows-Apps getestet. (Achten Sie immer darauf, [Ihre App mit dem Zertifizierungskit für Windows-Apps zu testen](../debug-test-perf/windows-app-certification-kit.md), bevor Sie sie im Store einreichen.)
-   **Erfüllung inhaltlicher Anforderungen:** Die dafür benötigte Zeit hängt von der Komplexität Ihrer App, der Menge von visuellem Inhalt sowie der Anzahl von kürzlich übermittelten Apps ab. Achten Sie darauf, auf der Seite [Hinweise für Zertifizierung](notes-for-certification.md) alle für Tester erforderlichen Informationen bereitzustellen.

Nach Abschluss des Zertifizierungsprozesses erhalten Sie einen Zertifizierungsbericht, der Aufschluss darüber gibt, ob Ihre App die Zertifizierung bestanden hat. War die Zertifizierung nicht erfolgreich, ist im Bericht angegeben, welcher Test nicht bestanden bzw. welche [Richtlinie](https://docs.microsoft.com/legal/windows/agreements/store-policies) nicht erfüllt wurde. Nachdem Sie das Problem behoben haben, können Sie eine neue Einreichung für Ihre App erstellen, um den Zertifizierungsprozess erneut einzuleiten.

## <a name="release"></a>Version

Wenn Ihre app die Zertifizierung bestanden hat, ist es **den Veröffentlichungsprozess** eintreten.

- Wenn Sie angegeben haben, dass Ihre Übermittlung so früh wie möglich (die Standardoption) veröffentlicht werden soll, wird der Veröffentlichungsprozess sofort gestartet.
- Ist dies das erste Mal haben Sie die app veröffentlicht und Sie ein **Veröffentlichungsdatum unter Umständen** im Abschnitt [Zeitplans](configure-precise-release-scheduling.md#release) angegeben, die app werden gemäß Ihrer **Veröffentlichungsdatum** Auswahl zur Verfügung gestellt.
- Wenn Sie [Optionen zum Anhalten der Veröffentlichung](manage-submission-options.md#publishing-hold-options) verwendet haben, um anzugeben, dass sie nicht vor einem bestimmten Datum veröffentlicht werden soll, warten wir bis zu diesem Zeitpunkt den Veröffentlichungsprozess beginnen ab, sofern Sie **Veröffentlichungsdatum ändern**auswählen.
- Wenn Sie [Optionen zum Anhalten der Veröffentlichung](manage-submission-options.md#publishing-hold-options) verwendet haben, um anzugeben, dass Sie die Übermittlung manuell veröffentlichen möchten, startet wir den Veröffentlichungsprozess nicht bis **Jetzt veröffentlichen** (oder wählen Sie **Veröffentlichungsdatum ändern** und wählen Sie ein bestimmtes Datum).


## <a name="publishing"></a>Veröffentlichung

Die Pakete Ihrer App werden digital signiert, damit sie nach ihrer Veröffentlichung nicht manipuliert werden können. Nach Beginn dieser Phase ist ein Abbruch der Einreichung oder eine Änderung des Veröffentlichungsdatums nicht mehr möglich.

Für neue apps und Updates, die Änderungen an der app Pakete enthalten, wird der Veröffentlichungsprozess innerhalb von 24 Stunden abgeschlossen werden. Für Updates, die nur ändern Optionen wie z. B. Store-Eintrag anzeigen, jedoch nicht die app-Pakete, wird der Veröffentlichungsprozess weniger als einer Stunde dauern.

Während Sie sich in der Veröffentlichungsphase befindet, können mit der **Details anzeigen** Link in der Statusspalte für Ihre app-Übermittlung wissen, wann Ihre neuen Pakete und Details des Eintrags Store auf jedem der unterstützten Betriebssystemversionen für Kunden verfügbar sind. Schritte, die noch nicht abgeschlossenen wurden, werden als **Ausstehend** angezeigt. Ihre app bleibt in der Veröffentlichungsphase, bis der Prozess abgeschlossen ist, was bedeutet, dass die neuen Pakete und/oder Details des Eintrags für alle potenziellen Kunden Ihrer app verfügbar sind.

## <a name="in-the-store"></a>Im Store 

Nach erfolgreicher Absolvierung der obigen Schritte ändert sich der Status der Übermittlung von **Veröffentlichung** in **Im Store**. Ihre Übermittlung steht den Kunden nun im Microsoft Store zum Download zur Verfügung (sofern Sie unter [Erkennbarkeit](choose-visibility-options.md#discoverability) keine andere Option ausgewählt haben). 

> [!NOTE]
> Außerdem führen wir Stichprobenkontrollen für bereits veröffentlichte Apps durch, um potenzielle Probleme zu ermitteln und sicherzustellen, dass Ihre App alle [Microsoft Store-Richtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies) erfüllt. Falls Probleme gefunden werden, werden Sie benachrichtigt, dass ein Problem aufgetreten ist und wie Sie es ggf. beheben können, oder dass die App aus dem Store entfernt wurde.

 

 

 




