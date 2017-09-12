---
author: jnHs
Description: "Beim Übermitteln eines Add-Ons bestimmen die Optionen auf der Seite „Preise und Verfügbarkeit“, zu welchem Preis und wie das Add-On Kunden angeboten werden soll."
title: "Festlegen der Preise und Verfügbarkeit von Add-Ons"
ms.assetid: B3D4B753-716B-460B-A3B1-ED5712ECD694
ms.author: wdg-dev-content
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 09671148e670acbfdbc944558a2738712f848dd5
ms.sourcegitcommit: de6bc8acec2cd5ebc36bb21b2ce1a9980c3e78b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="set-add-on-pricing-and-availability"></a>Festlegen der Preise und Verfügbarkeit von Add-Ons


Beim Übermitteln eines Add-Ons bestimmen die Optionen auf der Seite **Preise und Verfügbarkeit**, zu welchem Preis und wie das Add-On Kunden angeboten werden soll.

> [!NOTE]
> Wir haben vor kurzem die verfügbaren Optionen auf dieser Seite aktualisiert. Wenn Sie laufende Übermittlungen hatten, bevor diese neueren Optionen verfügbar waren, zeigen diese Übermittlung immer noch die älteren Optionen an. Sie können diese Übermittlung löschen und dann eine neue erstellen, wenn Sie die neusten Optionen für diese App verwenden möchten. Andernfalls werden die neusten Optionen mit dem nächsten Update nach der Veröffentlichung der laufenden Übermittlung verfügbar.

## <a name="markets"></a>Märkte

Ihr Add-On wird standardmäßig in allen möglichen Märkten, einschließlich zukünftigen Märkten, die möglicherweise später hinzukommen, zum Grundpreis eingetragen.

Allerdings können Sie genauso wie bei einer App bestimmen, in welchen Märkten Ihr Add-On angeboten werden soll. In den meisten Fällen werden Sie dieselben Märkte wie für die App auswählen, haben aber die Flexibilität, nach Bedarf Änderungen vorzunehmen. 

Weitere Informationen und eine vollständige Liste der verfügbaren Märkte finden Sie unter [Festlegen der Märkte](define-pricing-and-market-selection.md).

## <a name="visibility"></a>Sichtbarkeit

Sie können festlegen, ob Ihr Add-On Kunden zum Kauf angeboten werden soll. 

Die Standardoption ist **Can be displayed in the parent product’s Store listing**. Lassen Sie diese Option für Add-Ons aktiviert, die für alle Kunden verfügbar gemacht werden. 

Wählen Sie für Add-Ons, die Sie nicht allgemein verfügbar machen möchten, **Hidden in the Store** und eine der folgenden Optionen aus:

-   **Nur innerhalb des übergeordneten Produkts zum Kauf erhältlich:** Bei Auswahl dieser Option können Kunden das Add-On innerhalb Ihrer App kaufen, es wird aber im Store-Eintrag Ihrer App nicht aufgeführt. Verwenden Sie diese Option nur, wenn das Angebot nicht allgemein verfügbar ist, z.B. im Anfangszeitraum interner Tests.
-   **Beenden des Erwerbs: Alle Kunden mit einem direkten Link können den Produkt-Store-Eintrag sehen, aber sie können ihn nur herunterladen, wenn sie das Produkts vorher erworben haben oder einen Werbecode und ein Windows10-Gerät verwenden. Dieses Add-On wird nicht im übergeordneten Produkteintrag angezeigt**: Wenn Sie diese Option auswählen, wird das Add-On nicht im App Eintrag angezeigt, und neuen Kunden können das Add-On nicht erwerben. Allerdings wird **diese Option für Kunden mit Windows8.1 oder einer früheren Version nicht unterstützt**. Wenn Ihre App für Windows8.1 oder eine frühere Version verfügbar ist, kann das Add-On von diesen Kunden erworben werden. Um das Add-On-Angebot für Kunden mit Windows8.1 oder einer früheren Version einzustellen, müssen Sie die App aktualisieren, indem Sie den Code entfernen, durch den das Add-On angeboten wird, und eine neue Übermittlung für die App veröffentlichen. Dieser Schritt wird selbst dann empfohlen, wenn Ihre App keine Unterstützung für Windows8.1 oder frühere Versionen bietet, da die Kundenerfahrung beeinträchtigt werden könnte, wenn Sie erst ein Add-On anbieten, das Sie später zurückziehen.
    
 > [!NOTE] 
 > Das Auswählen der Option **Beenden des Erwerbs** und/oder das Übermitteln eines App-Updates, durch das das Add-On aus dem Code der App entfernt wird, wirkt sich nicht auf Kunden aus, die das Add-On bereits erworben haben, und zwar unabhängig von ihrem Betriebssystem.


## <a name="schedule"></a>Zeitplan

Standardmäßig (es sei denn, Sie haben eine der Optionen für **Hidden in the Store** im Abschnitt **Sichtbarkeit** ausgewählt) wird Ihre Add-On für Kunden zur Verfügung gestellt, sobald sie die Zertifizierung bestanden und den Veröffentlichungsprozess abgeschlossen hat. Um ein anderes Datum auszuwählen, wählen Sie **Optionen anzeigen**, um diesen Abschnittzu erweitern. 

Weitere Informationen finden Sie unter [Konfigurieren des genauen Veröffentlichungszeitplans](configure-precise-release-scheduling.md).


## <a name="pricing"></a>Preise

Müssen Sie einen Grundpreis für Ihre Add-On festsetzen (es sei denn, Sie haben die Option **Erwerb beenden** im Abschnitt **Sichtbarkeit** ausgewählt), indem Sie entweder **Umsonst** oder eine der verfügbaren Preisniveaus auswählen (beginnend mit 0,99USD).

Sie können auch Preisänderungen planen, um das Datum und die Uhrzeit anzugeben, an dem bzw. zu der sich der Preis Ihrer Add-On ändern soll. Darüber hinaus haben Sie die Möglichkeit, diese Änderungen für bestimmte Märkte anzupassen. 

Weitere Informationen finden Sie unter [Festlegen und Planen von App-Preisen](set-and-schedule-app-pricing.md).


## <a name="sale-pricing"></a>Sonderpreise

Wenn Sie Ihr Add-On zu einem reduzierten Preis für einen begrenzten Zeitraum anbieten möchten, können Sie ein Sonderangebot erstellen und planen. Weitere Informationen finden Sie unter [Anbieten von Apps und Add-Ons](put-apps-and-add-ons-on-sale.md).


## <a name="publish-date"></a>Veröffentlichungsdatum

Standardmäßig beginnt Ihre Übermittlung den Veröffentlichungsprozess direkt nach der Zertifizierung, es sei denn, Sie haben Datumsangaben im [Abschnitt **Zeitplan**](#schedule) (oben beschrieben) konfiguriert. 

Um zu steuern, wann Ihre Add-On im Store veröffentlicht werden soll, verwenden Sie den Abschnitt **Zeitplan**. Für die meisten Übermittlungen sollten Sie diesen Abschnittverwenden, um die Veröffentlichung zu planen. Behalten Sie für den Abschnitt **Veröffentlichungsdatum** die Standardoption **Publish this submission as soon as it passes certification** bei. Dadurch wird die Übermittlung nicht vor dem Datum veröffentlicht, das Sie im Abschnitt **Zeitplan** festgelegt haben. Das Datum, das Sie im Abschnitt **Zeitplan** ausgewählt haben, bestimmt, wann Ihre Add-On für Kunden im Store verfügbar gemacht wird.

Wenn Sie noch kein Veröffentlichungsdatum festlegen möchten und Ihre Übermittlung unveröffentlicht bleiben soll, bis Sie manuell mit dem Veröffentlichungsprozess beginnen möchten, können Sie **Publish this submission manually** auswählen. Die Auswahl dieser Option bedeutet, dass Ihre Auswahl erst veröffentlicht wird, wenn Sie es angeben. Nachdem Ihre Add-On die Zertifizierung bestanden hat, können Sie sie veröffentlichen, indem Sie auf der Seite mit dem Zertifizierungsstatus **Jetzt veröffentlichen** oder wie nachfolgend beschrieben ein bestimmtes Datum auswählen.

Wählen Sie **Nicht vor \[Datum\]**, um sicherzustellen, dass die Übermittlung nicht vor einem bestimmten Datum veröffentlicht wird. Mit dieser Option wird Ihre Übermittlung möglichst zum oder nach dem angegebenen Datum veröffentlicht. Das Datum muss mindestens 24Stunden in der Zukunft liegen. Zusammen mit dem Datum können Sie auch die Uhrzeit angeben, zu der die Veröffentlichung der Übermittlung beginnen soll.
 
> [!NOTE]
> Aufgrund von Verzögerungen bei der Zertifizierung oder Veröffentlichung kann das gewünschte Veröffentlichungsdatum unter Umständen nicht eingehalten werden. Es kann nicht garantiert werden, dass Ihr Add-On (oder das Update) an einem bestimmten Datum im Windows Store zur Verfügung steht.  



 




