---
author: jnHs
Description: "Beim Übermitteln eines Add-Ons bestimmen die Optionen auf der Seite „Preise und Verfügbarkeit“, zu welchem Preis und wie das Add-On Kunden angeboten werden soll."
title: "Festlegen der Preise und Verfügbarkeit von Add-Ons"
ms.assetid: B3D4B753-716B-460B-A3B1-ED5712ECD694
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 2902b81e777662e0d71bf10553ed82087c5cee9a
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="set-add-on-pricing-and-availability"></a>Festlegen der Preise und Verfügbarkeit von Add-Ons


Beim Übermitteln eines Add-Ons bestimmen die Optionen auf der Seite **Preise und Verfügbarkeit**, zu welchem Preis und wie das Add-On Kunden angeboten werden soll.

## <a name="base-price"></a>Grundpreis


Sie müssen einen Grundpreis für Ihr Add-On auswählen. Diese Preisniveaus sind identisch mit denen für Apps und beginnen bei 0,99USD. Sie können Ihr Add-On auch kostenlos zur Verfügung stellen.

## <a name="markets-and-custom-prices"></a>Märkte und angepasste Preise


Ihr Add-On wird standardmäßig in allen möglichen Märkten, einschließlich zukünftigen Märkten, die möglicherweise später hinzukommen, zum Grundpreis eingetragen.

Allerdings können Sie genauso wie bei einer App bestimmen, in welchen Märkten Ihr Add-On angeboten werden soll. In den meisten Fällen werden Sie dieselben Märkte wie für die App auswählen, haben aber die Flexibilität, nach Bedarf Änderungen vorzunehmen. Sie können auch angepasste Preise festlegen, um in verschiedenen Märkten unterschiedliche Preise für das Add-On zu verlangen.

Weitere Informationen und eine vollständige Liste der verfügbaren Märkte finden Sie unter [Festlegen des Preises und Auswählen der Märkte](define-pricing-and-market-selection.md).

## <a name="sale-pricing"></a>Sonderpreise


Wenn Sie Ihr Add-On zu einem reduzierten Preis für einen begrenzten Zeitraum anbieten möchten, können Sie ein Sonderangebot erstellen und planen. Weitere Informationen finden Sie unter [Anbieten von Apps und Add-Ons](put-apps-and-add-ons-on-sale.md).

## <a name="distribution-and-visibility"></a>Verteilung und Sichtbarkeit


Sie können festlegen, ob Ihr Add-On Kunden zum Kauf angeboten werden soll. Wählen Sie eine der folgenden Optionen:

-   **Zum Kauf erhältlich. Wird u.U. in Ihrer App-Liste angezeigt:** Dies ist die Standardeinstellung. Sie wird empfohlen, sofern der Zugriff auf das Add-On nicht eingeschränkt werden soll. Lassen Sie diese Option für Add-Ons aktiviert, die für alle Kunden verfügbar gemacht werden.
-   **Zum Kauf erhältlich. Wird nicht in Ihrer App-Liste angezeigt:** Bei Auswahl dieser Option können Kunden das Add-On innerhalb Ihrer App kaufen, es wird aber im Store-Eintrag Ihrer App nicht aufgeführt. Verwenden Sie diese Option nur, wenn das Angebot nicht allgemein verfügbar ist, z.B. im Anfangszeitraum interner Tests.
-   **Nicht mehr zum Kauf erhältlich. Wird nicht im App-Eintrag angezeigt.** Diese Option bedeutet, dass das Add-On nicht im App-Eintrag angezeigt wird und nicht von neuen Kunden erworben werden kann. Allerdings wird **diese Option für Kunden mit Windows8.1 oder einer früheren Version nicht unterstützt**. Wenn Ihre App für Windows8.1 oder eine frühere Version verfügbar ist, kann das Add-On von diesen Kunden erworben werden. Um das Add-On-Angebot für Kunden mit Windows8.1 oder einer früheren Version einzustellen, müssen Sie die App aktualisieren, indem Sie den Code entfernen, durch den das Add-On angeboten wird, und eine neue Übermittlung für die App veröffentlichen. Dieser Schritt wird selbst dann empfohlen, wenn Ihre App keine Unterstützung für Windows8.1 oder frühere Versionen bietet, da die Kundenerfahrung beeinträchtigt werden könnte, wenn Sie erst ein Add-On anbieten, das Sie später zurückziehen.
    
 > **Hinweis:** Das Auswählen dieser Einstellung und/oder Übermitteln eines App-Updates, durch das das Add-On aus dem Code der App entfernt wird, wirkt sich nicht auf Kunden aus, die das Add-On bereits erworben haben, und zwar unabhängig von ihrem Betriebssystem.


## <a name="publish-date"></a>Veröffentlichungsdatum

Mithilfe der Optionen im Abschnitt **Veröffentlichungsdatum** können Sie angeben, wann die Add-On-Übermittlung veröffentlicht wird.

-   Wählen Sie **Mein Add-On sofort nach erfolgreicher Zertifizierung veröffentlichen** aus, um die Übermittlung so schnell wie möglich im Store verfügbar zu machen.
-   Wählen Sie **Dieses Add-On manuell veröffentlichen** aus, wenn Sie den Veröffentlichungszeitpunkt Ihrer Übermittlung selbst angeben möchten. Dazu können Sie auf der Seite mit dem Zertifizierungsstatus auf **Jetzt veröffentlichen** klicken oder ein bestimmtes Datum auswählen, wie unten beschrieben.
-   Wählen Sie **Nicht vor \[Datum\]**, um sicherzustellen, dass die Übermittlung nicht vor einem bestimmten Datum veröffentlicht wird. Mit dieser Option wird Ihre Übermittlung möglichst zum oder nach dem angegebenen Datum veröffentlicht. Das Datum muss mindestens 24Stunden in der Zukunft liegen. Zusammen mit dem Datum können Sie auch die Uhrzeit angeben, zu der die Veröffentlichung der Übermittlung beginnen soll.

 > **Hinweis:** Aufgrund von Verzögerungen bei der Zertifizierung oder Veröffentlichung kann das gewünschte Veröffentlichungsdatum unter Umständen nicht eingehalten werden. Es kann nicht garantiert werden, dass Ihr Add-On (oder das Update) an einem bestimmten Datum im Windows Store zur Verfügung steht.
 

 




