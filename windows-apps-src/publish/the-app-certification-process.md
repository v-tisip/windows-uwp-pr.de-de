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
keywords: Windows 10 Uwp veröffentlichen vorverarbeiten, Zertifizierung, freigeben, Ausstehend, senden, Veröffentlichungsstatus Zeit
ms.localizationpriority: medium
ms.openlocfilehash: 8372f316786d83d72dff8ef7a0a8fd53e5390743
ms.sourcegitcommit: 3727445c1d6374401b867c78e4ff8b07d92b7adc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "2918861"
---
# <a name="the-app-certification-process"></a>Der App-Zertifizierungsprozess

Nachdem Sie die App-Einreichung fertig gestellt haben und auf **An Store übermitteln** klicken, tritt die Übermittlung in die Zertifizierungsphase ein. Dieser Vorgang ist in der Regel innerhalb weniger Stunden abgeschlossen, kann in Einzelfällen aber bis zu drei Arbeitstage dauern. Nach dem Absenden zertifiziert wurde, dauert es bis zu 24 Stunden für Kunden der app-Eintrag für eine neue Vorlage oder eine aktualisierte Vorlage mit Paketen. Wenn Ihre Aktualisierung ändert nur Shop-Details wird der Veröffentlichungsprozess in weniger als einer Stunde abgeschlossen.  Sie werden benachrichtigt, wenn Ihre Einsendung veröffentlicht und Status der app im Dashboard **Im Speicher werden**.

## <a name="preprocessing"></a>Vorverarbeitung

Nach dem erfolgreichen Hochladen der App-Pakete und dem Übermitteln der App zur Zertifizierung werden die Pakete zum Testen in die Warteschlange eingereiht. Es wird eine Meldung angezeigt, wenn während der Vorverarbeitung Fehler erkannt werden. Weitere Informationen zu möglichen Fehlern finden Sie unter [Fehler bei der Einreichung](resolve-submission-errors.md).

## <a name="certification"></a>Zertifizierung

Während dieser Phase werden mehrere Tests durchgeführt:

-   **Sicherheitstests:** Dieser erste Test überprüft die Pakete Ihrer App auf Viren und Schadsoftware. Besteht Ihre App diesen Test nicht, müssen Sie Ihr Entwicklungssystem überprüfen, indem Sie die aktuelle Antivirensoftware ausführen und Ihr App-Paket anschließend in einem bereinigten System neu erstellen.
-   **Tests bezgl. der Erfüllung technischer Anforderungen:** Die Erfüllung technischer Anforderungen wird mithilfe des Zertifizierungskits für Windows-Apps getestet. (Achten Sie immer darauf, [Ihre App mit dem Zertifizierungskit für Windows-Apps zu testen](../debug-test-perf/windows-app-certification-kit.md), bevor Sie sie im Store einreichen.)
-   **Erfüllung inhaltlicher Anforderungen:** Die dafür benötigte Zeit hängt von der Komplexität Ihrer App, der Menge von visuellem Inhalt sowie der Anzahl von kürzlich übermittelten Apps ab. Achten Sie darauf, auf der Seite [Hinweise für Zertifizierung](notes-for-certification.md) alle für Tester erforderlichen Informationen bereitzustellen.

Nach Abschluss des Zertifizierungsprozesses erhalten Sie einen Zertifizierungsbericht, der Aufschluss darüber gibt, ob Ihre App die Zertifizierung bestanden hat. War die Zertifizierung nicht erfolgreich, ist im Bericht angegeben, welcher Test nicht bestanden bzw. welche [Richtlinie](https://docs.microsoft.com/legal/windows/agreements/store-policies) nicht erfüllt wurde. Nachdem Sie das Problem behoben haben, können Sie eine neue Einreichung für Ihre App erstellen, um den Zertifizierungsprozess erneut einzuleiten.

## <a name="release"></a>Version

Wenn Ihre app zertifiziert wurde, kann **der Veröffentlichungsvorgang** verschieben.

- Wenn Sie angegeben haben, Ihre Einsendung (Standardeinstellung) möglichst bald veröffentlicht werden sollen, beginnt der Veröffentlichungsprozess sofort.
- Zum ersten Mal die Anwendung veröffentlicht haben und angegebenen **Veröffentlichungsdatum** im Bereich [Zeitplan](configure-precise-release-scheduling.md#release) , die app nach **Veröffentlichungsdatum** Auswahl zur Verfügung stehen.
- Wenn Sie [Veröffentlichen enthalten Optionen](manage-submission-options.md#publishing-hold-options) verwendet haben, um anzugeben, dass es nicht vor einem bestimmten Datum freigegeben werden sollen, warten wir bis zu diesem Datum der Veröffentlichung beginnen, **Version Datum**auswählen.
- Wenn Sie [Veröffentlichen enthalten Optionen](manage-submission-options.md#publishing-hold-options) verwendet haben, um anzugeben, dass Sie die Vorlage manuell veröffentlichen möchten, wird nicht den Veröffentlichungsprozess zunächst bis **Jetzt veröffentlichen** (oder **Release** -ändern Datum und wählen Sie ein bestimmtes Datum).


## <a name="publishing"></a>Veröffentlichung

Die Pakete Ihrer App werden digital signiert, damit sie nach ihrer Veröffentlichung nicht manipuliert werden können. Nach Beginn dieser Phase ist ein Abbruch der Einreichung oder eine Änderung des Veröffentlichungsdatums nicht mehr möglich.

Neue apps und Updates die Änderungen des app Pakete enthalten, wird der Veröffentlichungsprozess innerhalb von 24 Stunden abgeschlossen. Updates, die nur Optionen wie Shop-Details ändern, aber nicht die app Pakete, wird der Veröffentlichungsprozess weniger als eine Stunde dauern.

Ist Ihre Anwendung in der Veröffentlichung kann in der Spalte Status der app-Einsendung Link **Details anzeigen** , wenn die neuen Pakete und Shop-Details auf jeder unterstützten Betriebssystemversionen verfügbar sind. Schritte, die noch nicht abgeschlossenen wurden, werden als **Ausstehend** angezeigt. Ihre app bleibt in der Veröffentlichung erst abgeschlossen, bedeutet, dass die neuen Pakete oder Angebotsdetails stehen allen Kunden Ihre app.

## <a name="in-the-store"></a>Im Store 

Nach erfolgreicher Absolvierung der obigen Schritte ändert sich der Status der Übermittlung von **Veröffentlichung** in **Im Store**. Ihre Übermittlung steht den Kunden nun im Microsoft Store zum Download zur Verfügung (sofern Sie unter [Erkennbarkeit](choose-visibility-options.md#discoverability) keine andere Option ausgewählt haben). 

> [!NOTE]
> Außerdem führen wir Stichprobenkontrollen für bereits veröffentlichte Apps durch, um potenzielle Probleme zu ermitteln und sicherzustellen, dass Ihre App alle [Microsoft Store-Richtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies) erfüllt. Falls Probleme gefunden werden, werden Sie benachrichtigt, dass ein Problem aufgetreten ist und wie Sie es ggf. beheben können, oder dass die App aus dem Store entfernt wurde.

 

 

 




