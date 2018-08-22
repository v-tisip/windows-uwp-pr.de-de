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
keywords: Windows 10, Uwp, Veröffentlichung, vorverarbeitung, Zertifizierung, freigeben, ausstehende, übermitteln, veröffentlichen, Status, Zeit
ms.localizationpriority: medium
ms.openlocfilehash: 8372f316786d83d72dff8ef7a0a8fd53e5390743
ms.sourcegitcommit: f2f4820dd2026f1b47a2b1bf2bc89d7220a79c1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "2788856"
---
# <a name="the-app-certification-process"></a>Der App-Zertifizierungsprozess

Nachdem Sie die App-Einreichung fertig gestellt haben und auf **An Store übermitteln** klicken, tritt die Übermittlung in die Zertifizierungsphase ein. Dieser Vorgang ist in der Regel innerhalb weniger Stunden abgeschlossen, kann in Einzelfällen aber bis zu drei Arbeitstage dauern. Nach Ihrer Übermittlung Zertifizierung übergibt, können Kunden auf die app-Auflistung für eine neue Übermittlung oder für eine aktualisierte Übermittlung mit Änderungen an Pakete finden Sie unter bis zu 24 Stunden dauern. Wenn die Aktualisierung nur Shop-Details geändert wird, wird in weniger als einer Stunde der Veröffentlichungsvorgang abgeschlossen werden.  Sie werden benachrichtigt, wenn Ihre Bereitstellung veröffentlicht wird, und die app-Status in das Dashboard wird **In der Store**sein.

## <a name="preprocessing"></a>Vorverarbeitung

Nach dem erfolgreichen Hochladen der App-Pakete und dem Übermitteln der App zur Zertifizierung werden die Pakete zum Testen in die Warteschlange eingereiht. Es wird eine Meldung angezeigt, wenn während der Vorverarbeitung Fehler erkannt werden. Weitere Informationen zu möglichen Fehlern finden Sie unter [Fehler bei der Einreichung](resolve-submission-errors.md).

## <a name="certification"></a>Zertifizierung

Während dieser Phase werden mehrere Tests durchgeführt:

-   **Sicherheitstests:** Dieser erste Test überprüft die Pakete Ihrer App auf Viren und Schadsoftware. Besteht Ihre App diesen Test nicht, müssen Sie Ihr Entwicklungssystem überprüfen, indem Sie die aktuelle Antivirensoftware ausführen und Ihr App-Paket anschließend in einem bereinigten System neu erstellen.
-   **Tests bezgl. der Erfüllung technischer Anforderungen:** Die Erfüllung technischer Anforderungen wird mithilfe des Zertifizierungskits für Windows-Apps getestet. (Achten Sie immer darauf, [Ihre App mit dem Zertifizierungskit für Windows-Apps zu testen](../debug-test-perf/windows-app-certification-kit.md), bevor Sie sie im Store einreichen.)
-   **Erfüllung inhaltlicher Anforderungen:** Die dafür benötigte Zeit hängt von der Komplexität Ihrer App, der Menge von visuellem Inhalt sowie der Anzahl von kürzlich übermittelten Apps ab. Achten Sie darauf, auf der Seite [Hinweise für Zertifizierung](notes-for-certification.md) alle für Tester erforderlichen Informationen bereitzustellen.

Nach Abschluss des Zertifizierungsprozesses erhalten Sie einen Zertifizierungsbericht, der Aufschluss darüber gibt, ob Ihre App die Zertifizierung bestanden hat. War die Zertifizierung nicht erfolgreich, ist im Bericht angegeben, welcher Test nicht bestanden bzw. welche [Richtlinie](https://docs.microsoft.com/legal/windows/agreements/store-policies) nicht erfüllt wurde. Nachdem Sie das Problem behoben haben, können Sie eine neue Einreichung für Ihre App erstellen, um den Zertifizierungsprozess erneut einzuleiten.

## <a name="release"></a>Version

Wenn Ihre app Zertifizierung übergibt, ist es bereit, um **den Veröffentlichungsvorgang** zu verschieben.

- Wenn Sie angegeben haben, dass Ihre Bereitstellung so bald wie möglich (Standardoption) veröffentlicht werden soll, wird der Veröffentlichungsvorgang sofort gestartet.
- Hierbei handelt es sich beim ersten haben Sie die app veröffentlicht und angegebenen ein **Veröffentlichungsdatum** im Abschnitt [Zeitplan](configure-precise-release-scheduling.md#release) , die app aufgrund Ihrer Auswahl **Veröffentlichungsdatum** zur Verfügung stehen.
- Wenn Sie [Veröffentlichung halten Optionen](manage-submission-options.md#publishing-hold-options) verwendet haben, um anzugeben, dass es bis zu einem bestimmten Datum nicht freigegeben werden sollen, warten wir bis zu diesem Zeitpunkt beginnen der Veröffentlichungsvorgang ab, oder wählen Sie **Veröffentlichungsdatum ändern**.
- Wenn Sie [Veröffentlichung halten Optionen](manage-submission-options.md#publishing-hold-options) verwendet haben, um anzugeben, dass Sie die Übermittlung manuell veröffentlichen möchten, startet wir nicht den Veröffentlichungsvorgang zu beenden, bis **Jetzt veröffentlichen** (oder wählen Sie **Veröffentlichungsdatum ändern** und wählen Sie ein bestimmtes Datum).


## <a name="publishing"></a>Veröffentlichung

Die Pakete Ihrer App werden digital signiert, damit sie nach ihrer Veröffentlichung nicht manipuliert werden können. Nach Beginn dieser Phase ist ein Abbruch der Einreichung oder eine Änderung des Veröffentlichungsdatums nicht mehr möglich.

Neue apps und Updates die Änderungen an der app-Pakete enthalten, wird der Veröffentlichungsvorgang innerhalb von 24 Stunden abgeschlossen werden. Updates, die nur Optionen wie Shop-Details zu ändern, aber nicht die app-Pakete ändern, dauert der Veröffentlichungsvorgang weniger als eine Stunde.

Während der Phase der Veröffentlichung Ihrer app wird, können der Link **Details einblenden** in der Spalte Status für die Übermittlung Ihrer app, wenn Ihre neue Pakete und Shop-Details für Kunden auf jedem Ihrer unterstützten Betriebssystemversionen verfügbar sind. Schritte, die noch nicht abgeschlossenen wurden, werden als **Ausstehend** angezeigt. Ihre app bleibt in der Veröffentlichung Phase, bis der Vorgang abgeschlossen ist, bedeutet, dass die neuen Pakete und/oder Auflisten von Details zu allen potenziellen Kunden Ihre app verfügbar sind.

## <a name="in-the-store"></a>Im Store 

Nach erfolgreicher Absolvierung der obigen Schritte ändert sich der Status der Übermittlung von **Veröffentlichung** in **Im Store**. Ihre Übermittlung steht den Kunden nun im Microsoft Store zum Download zur Verfügung (sofern Sie unter [Erkennbarkeit](choose-visibility-options.md#discoverability) keine andere Option ausgewählt haben). 

> [!NOTE]
> Außerdem führen wir Stichprobenkontrollen für bereits veröffentlichte Apps durch, um potenzielle Probleme zu ermitteln und sicherzustellen, dass Ihre App alle [Microsoft Store-Richtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies) erfüllt. Falls Probleme gefunden werden, werden Sie benachrichtigt, dass ein Problem aufgetreten ist und wie Sie es ggf. beheben können, oder dass die App aus dem Store entfernt wurde.

 

 

 




