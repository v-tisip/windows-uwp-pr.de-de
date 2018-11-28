---
Description: When submitting an add-on, the options on the Pricing and availability page determine what to charge for your add-on and how it should be offered to customers.
title: Festlegen der Preise und Verfügbarkeit von Add-Ons
ms.assetid: B3D4B753-716B-460B-A3B1-ED5712ECD694
ms.date: 10/31/2018
ms.topic: article
keywords: Windows10, UWP, Add-Ons, IAP, Preis
ms.localizationpriority: medium
ms.openlocfilehash: 062337c82d2567d15b0eff1767ab157618da257e
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7845246"
---
# <a name="set-add-on-pricing-and-availability"></a>Festlegen der Preise und Verfügbarkeit von Add-Ons

Beim Übermitteln eines Add-Ons im [Partner Center](https://partner.microsoft.com/dashboard), bestimmen die Optionen auf der Seite " **Preise und Verfügbarkeit** ", wie oft die Kosten für Ihr Add-on Kunden und wie es Kunden angeboten werden soll.

## <a name="markets"></a>Märkte

Ihr Add-On wird standardmäßig in allen möglichen Märkten, einschließlich zukünftigen Märkten, die möglicherweise später hinzukommen, zum Grundpreis eingetragen.

Allerdings können Sie genauso wie bei einer App bestimmen, in welchen Märkten Ihr Add-On angeboten werden soll. In den meisten Fällen werden Sie dieselben Märkte wie für die App auswählen, haben aber die Flexibilität, nach Bedarf Änderungen vorzunehmen. 

Weitere Informationen und eine vollständige Liste der verfügbaren Märkte finden Sie unter [Festlegen der Märkte](define-pricing-and-market-selection.md).

## <a name="visibility"></a>Sichtbarkeit

Sie können festlegen, ob Ihr Add-On Kunden zum Kauf angeboten werden soll. 

Die Standardoption ist **Can be displayed in the parent product’s Store listing**. Lassen Sie diese Option für Add-Ons aktiviert, die für alle Kunden verfügbar gemacht werden. 

Wählen Sie für Add-Ons, die Sie nicht allgemein verfügbar machen möchten, **Hidden in the Store** und eine der folgenden Optionen aus:

-   **Zum Kauf von nur innerhalb des übergeordneten Produkts erhältlich**: Auswahl dieser Option können Kunden das Add-on innerhalb Ihrer app kaufen, jedoch das Add-on nicht im Store sichtbar oder in Ihrer app Store-Eintrag angezeigt. Verwenden Sie diese Option nur, wenn das Angebot nicht allgemein verfügbar ist, z.B. im Anfangszeitraum interner Tests.
-   **Beenden des Erwerbs: Alle Kunden mit einem direkten Link können den Produkt-Store-Eintrag sehen, aber sie können ihn nur herunterladen, wenn sie das Produkts vorher erworben haben oder einen Werbecode und ein Windows10-Gerät verwenden. Dieses Add-On wird nicht im übergeordneten Produkteintrag angezeigt**: Wenn Sie diese Option auswählen, wird das Add-On nicht im App Eintrag angezeigt, und neuen Kunden können das Add-On nicht erwerben. Jedoch, **diese Option wird für Kunden auf Windows8.1 oder früher nicht unterstützt**. Wenn Ihre app zuvor veröffentlichten auf Windows8.1 oder früheren Versionen ist, kann das Add-on weiterhin verfügbar für diesen Kunden erworben werden. Um das Add-on Kunden anbieten auf Windows8.1 oder einer früheren Version, müssen Sie Ihre app, um den Code zu entfernen, der das Add-on-Angebote zu aktualisieren, und klicken Sie dann eine neue Übermittlung für die app veröffentlichen. Dies wird empfohlen, auch wenn Ihre app Windows8.1 Ziel nicht oder frühere Versionen Es ist besser für Ihre Kunden, wenn Sie erst ein Add-on, das Sie sich entschieden haben anbieten, um nicht mehr verfügbar sein.
    
 > [!NOTE] 
 > Das Auswählen der Option **Beenden des Erwerbs** und/oder das Übermitteln eines App-Updates, durch das das Add-On aus dem Code der App entfernt wird, wirkt sich nicht auf Kunden aus, die das Add-On bereits erworben haben, und zwar unabhängig von ihrem Betriebssystem.


## <a name="schedule"></a>Zeitplan

Standardmäßig (es sei denn, Sie haben eine der Optionen für **Hidden in the Store** im Abschnitt **Sichtbarkeit** ausgewählt) wird Ihre Add-On für Kunden zur Verfügung gestellt, sobald sie die Zertifizierung bestanden und den Veröffentlichungsprozess abgeschlossen hat. Um ein anderes Datum auszuwählen, wählen Sie **Optionen anzeigen**, um diesen Abschnittzu erweitern. 

Weitere Informationen finden Sie unter [Konfigurieren des genauen Veröffentlichungszeitplans](configure-precise-release-scheduling.md).


## <a name="pricing"></a>Preise

Sie müssen einen Grundpreis für Ihr Add-on auswählen (es sei denn, Sie die **Beenden des Erwerbs** Option im Abschnitt **Sichtbarkeit** ausgewählt haben). Die Standardeinstellung ist **frei**, wenn Sie Geld für das Add-on erheben möchten, werden Sie eine der verfügbaren Preisniveaus auswählen (beginnend mit.99 US-Dollar) auswählen.

Sie können auch Preisänderungen planen, um das Datum und die Uhrzeit anzugeben, an dem bzw. zu der sich der Preis Ihrer Add-On ändern soll. Darüber hinaus haben Sie die Möglichkeit, diese Änderungen für bestimmte Märkte anzupassen. 

> [!TIP]
> Sie können nicht für Abonnement-Add-Ons den Preis auslösen, nach der Veröffentlichung des Add-Ons, durch einen höheren Grundpreis in einer späteren Übermittlung auswählen oder durch einen Preis ändern, der den Preis erhöht planen. Sie können einen geringeren Preis mit einer der folgenden Methoden auswählen, aber sobald der Preis gesenkt wird Sie nicht über diese neue Preis auslösen. Aus diesem Grund ist es besonders wichtig, um sicherzustellen, dass Sie die entsprechenden Preisstufe für Abonnement-Add-Ons auswählen. 

Weitere Informationen finden Sie unter [Festlegen und Planen von App-Preisen](set-and-schedule-app-pricing.md).


## <a name="sale-pricing"></a>Sonderpreise

Wenn Sie Ihr Add-On zu einem reduzierten Preis für einen begrenzten Zeitraum anbieten möchten, können Sie ein Sonderangebot erstellen und planen. Weitere Informationen finden Sie unter [Anbieten von Apps und Add-Ons](put-apps-and-add-ons-on-sale.md).



