---
author: jnHs
Description: When submitting an add-on, the options on the Pricing and availability page determine what to charge for your add-on and how it should be offered to customers.
title: Festlegen der Preise und Verfügbarkeit von Add-Ons
ms.assetid: B3D4B753-716B-460B-A3B1-ED5712ECD694
ms.author: wdg-dev-content
ms.date: 05/08/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Add-Ons, IAP, Preis
ms.localizationpriority: medium
ms.openlocfilehash: b5b7a6424fea3d62849e992f56b0b40ab72a55f5
ms.sourcegitcommit: e6daa7ff878f2f0c7015aca9787e7f2730abcfbf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "4313356"
---
# <a name="set-add-on-pricing-and-availability"></a>Festlegen der Preise und Verfügbarkeit von Add-Ons


Beim Übermitteln eines Add-Ons bestimmen die Optionen auf der Seite **Preise und Verfügbarkeit**, zu welchem Preis und wie das Add-On Kunden angeboten werden soll.

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

Sie müssen einen Grundpreis für Ihr Add-on auswählen (es sei denn, Sie die **Beenden des Erwerbs** Option im Abschnitt **Sichtbarkeit** ausgewählt haben). Die Standardeinstellung ist **kostenlos**, also wenn Sie Geld für das Add-on erheben möchten, müssen Sie eine der verfügbaren Preisniveaus auswählen (beginnend mit.99 US-Dollar) auswählen.

Sie können auch Preisänderungen planen, um das Datum und die Uhrzeit anzugeben, an dem bzw. zu der sich der Preis Ihrer Add-On ändern soll. Darüber hinaus haben Sie die Möglichkeit, diese Änderungen für bestimmte Märkte anzupassen. 

> [!TIP]
> Sie können nicht für Abonnement-Add-Ons den Preis auslösen, nach der Veröffentlichung des Add-Ons, durch einen höheren Grundpreis in einer späteren Übermittlung auswählen oder durch die Planung einer Preisänderung, die den Preis erhöht. Sie können einen geringeren Preis mithilfe der folgenden Methoden auswählen, aber sobald der Preis gesenkt wird Sie nicht über die neuen Preis auslösen. Aus diesem Grund ist es besonders wichtig, um sicherzustellen, dass Sie die entsprechenden Preisstufe für Abonnement-Add-Ons auswählen. 

Weitere Informationen finden Sie unter [Festlegen und Planen von App-Preisen](set-and-schedule-app-pricing.md).


## <a name="sale-pricing"></a>Sonderpreise

Wenn Sie Ihr Add-On zu einem reduzierten Preis für einen begrenzten Zeitraum anbieten möchten, können Sie ein Sonderangebot erstellen und planen. Weitere Informationen finden Sie unter [Anbieten von Apps und Add-Ons](put-apps-and-add-ons-on-sale.md).



