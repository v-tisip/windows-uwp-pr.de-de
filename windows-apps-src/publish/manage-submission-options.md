---
author: jnHs
Description: Manage submission options such as publishing hold options, notes for certification, and more.
title: Verwalten der Übermittlungsoptionen
ms.author: wdg-dev-content
ms.date: 04/03/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anhalten der Veröffentlichung, Veröffentlichungsdatum, Übermittlung zur Veröffentlichung senden
ms.localizationpriority: high
ms.openlocfilehash: 4f18a4cae88f78b16ea43856cc6166c67a228c2c
ms.sourcegitcommit: 9f059b37e45099b4314c96a0b604449e966d3c3c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2018
---
# <a name="manage-submission-options"></a>Verwalten der Übermittlungsoptionen

Auf der Seite **Übermittlungsoptionen** des App-Übermittlungsprozesses können Sie weitere Informationen angeben, damit wir Ihr Produkt ordnungsgemäß testen können. Dies ist ein optionaler Schritt, der für viele Übermittlungen empfohlen wird. Sie können ebenfalls optional das Anhalten der Veröffentlichungsoptionen festlegen, wenn Sie den Veröffentlichungsprozess verzögern möchten.


## <a name="publishing-hold-options"></a>Optionen zum Anhalten der Veröffentlichung

Standardmäßig wird Ihre Übermittlung veröffentlicht, sobald sie die Zertifizierung bestanden hat (oder je nach Datum im angegebenen [Zeitplan](configure-precise-release-scheduling.md) auf der Seite **Preise und Verfügbarkeit**). Sie können optional auswählen, die Veröffentlichung der Übermittlung vor einem bestimmten Datum anzuhalten oder bis Sie manuell angeben, dass diese veröffentlicht werden soll. Die Optionen in diesem Abschnitt werden im Anschluss beschrieben.


### <a name="publish-your-submission-as-soon-as-it-passes-certification-or-per-dates-you-specify"></a>Veröffentlichen Sie Ihre Übermittlung, sobald sie Zertifizierung bestanden hat (oder am angegebenen Datum)

**Veröffentlichen Sie diese Übermittlung, sobald die Zertifizierung abgeschlossen ist (oder ab einem im Abschnitt des Zeitplans ausgewählten Datum)** ist die Standardeinstellung. Dies bedeutet, dass Ihre Übermittlung veröffentlicht wird, sobald der Zertifizierungsprozess abgeschlossen ist, es sei denn, sie haben das Datum anderweitig im [Zeitplan](configure-precise-release-scheduling.md) auf der Seite **Preise und Verfügbarkeit** festgelegt.   

Für die meisten Übermittlungen empfehlen wir den Abschnitt **Optionen zum Anhalten der Veröffentlichung** auf diese Option festzulegen. Wenn Sie ein spezifisches Datum für die Veröffentlichung der Übermittlung festlegen möchten, verwenden Sie die Option **Veröffentlichen Sie diese Übermittlung, sobald die Zertifizierung abgeschlossen ist (oder ab einem im Abschnitt des Zeitplans ausgewählten Datum)**. Wenn Sie diesen Abschnitt als Standardoption festlegen, wird die Übermittlung nicht vor dem Datum veröffentlicht, das Sie im Abschnitt **Zeitplan** festgelegt haben. Das Datum, das Sie im Abschnitt **Zeitplan** ausgewählt haben, bestimmt, wann Ihre App für Kunden im Store verfügbar gemacht wird.


### <a name="publish-your-submission-manually"></a>Übermittlung manuell veröffentlichen

Wenn Sie noch kein Veröffentlichungsdatum festlegen möchten und Ihre Übermittlung unveröffentlicht bleiben soll, bis Sie manuell mit dem Veröffentlichungsprozess beginnen möchten, können Sie **Don't publish this submission until I select Publish now** auswählen. Die Auswahl dieser Option bedeutet, dass Ihre Auswahl erst veröffentlicht wird, wenn Sie es angeben. Nachdem Ihre App die Zertifizierung bestanden hat, können Sie sie veröffentlichen, indem Sie auf der Seite mit dem Zertifizierungsstatus **Jetzt veröffentlichen** oder wie nachfolgend beschrieben ein bestimmtes Datum auswählen.


### <a name="start-publishing-your-submission-on-a-certain-date"></a>Starten Sie die Veröffentlichung der Übermittlung an einem bestimmten Datum

Wählen Sie **Start publishing this submission on**, um sicherzustellen, dass die Übermittlung nicht vor einem bestimmten Datum veröffentlicht wird. Mit dieser Option wird Ihre Übermittlung möglichst zum oder nach dem angegebenen Datum veröffentlicht. Das Datum muss mindestens 24Stunden in der Zukunft liegen. Zusammen mit dem Datum können Sie auch die Uhrzeit angeben, zu der die Veröffentlichung der Übermittlung beginnen soll. 

Sie können das Veröffentlichungsdatum nach dem Einreichen der App ändern, solange sie noch nicht in die Phase Veröffentlichen eingetreten ist. 
 
Wenn Sie bestimmte Daten für die Veröffentlichung der Übermittlung festlegen möchten, verwenden Sie ** Veröffentlichen Sie diese Übermittlung, sobald die Zertifizierung abgeschlossen ist (oder ab einem im Abschnitt des Zeitplans ausgewählten Datum)** und lassen Sie die **Optionen zum Anhalten der Veröffentlichung** auf der Standardeinstellung. Die Option **Start publishing this submission on** bedeutet, dass Ihre Übermittlung den Veröffentlichungsprozess nicht vor diesem Datum beginnt, wobei Verzögerungen bei der Zertifizierung oder der Veröffentlichung dazu führen können, dass das gewünschte Veröffentlichungsdatum nach dem ausgewählten Datum beginnt. 


## <a name="notes-for-certification"></a>Hinweise für Zertifizierung

Beim Einreichen der App haben Sie die Möglichkeit, auf der Seite **Hinweise für Zertifizierung** zusätzliche Informationen für Zertifizierungstester bereitzustellen. Mit diesen Informationen kann sichergestellt werden, dass die App richtig getestet wird. 

Weitere Informationen finden Sie unter [Hinweise zur Zertifizierung](notes-for-certification.md).

