---
author: jnHs
Description: When submitting an add-on, the options on the Pricing and availability page determine what to charge for your add-on and how it should be offered to customers.
title: Festlegen der Preise und Verfügbarkeit von Add-Ons
ms.assetid: B3D4B753-716B-460B-A3B1-ED5712ECD694
ms.author: wdg-dev-content
ms.date: 10/31/2018
ms.topic: article
keywords: Windows10, UWP, Add-Ons, IAP, Preis
ms.localizationpriority: medium
ms.openlocfilehash: 6dc557306fe2e5e24ce1210e75ac5f29628306ae
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7170968"
---
# <a name="set-add-on-pricing-and-availability"></a>Festlegen der Preise und Verfügbarkeit von Add-Ons

Beim Übermitteln eines Add-Ons im [Partner Center](https://partner.microsoft.com/dashboard)bestimmen die Optionen auf der Seite " **Preise und Verfügbarkeit** " wie viel, Aufladen Kunden für Ihr Add-on und wie es Kunden angeboten werden soll.

## <a name="markets"></a>Märkte

Ihr Add-On wird standardmäßig in allen möglichen Märkten, einschließlich zukünftigen Märkten, die möglicherweise später hinzukommen, zum Grundpreis eingetragen.

Allerdings können Sie genauso wie bei einer App bestimmen, in welchen Märkten Ihr Add-On angeboten werden soll. In den meisten Fällen werden Sie dieselben Märkte wie für die App auswählen, haben aber die Flexibilität, nach Bedarf Änderungen vorzunehmen. 

Weitere Informationen und eine vollständige Liste der verfügbaren Märkte finden Sie unter [Festlegen der Märkte](define-pricing-and-market-selection.md).

## <a name="visibility"></a>Sichtbarkeit

Sie können festlegen, ob Ihr Add-On Kunden zum Kauf angeboten werden soll. 

Die Standardoption ist **Can be displayed in the parent product’s Store listing**. Lassen Sie diese Option für Add-Ons aktiviert, die für alle Kunden verfügbar gemacht werden. 

Wählen Sie für Add-Ons, die Sie nicht allgemein verfügbar machen möchten, **Hidden in the Store** und eine der folgenden Optionen aus:

-   **Zum Kauf von nur innerhalb des übergeordneten Produkts erhältlich**: Auswahl dieser Option können Kunden das Add-on innerhalb Ihrer app kaufen, jedoch das Add-on nicht im Store-Eintrag Ihrer app angezeigten oder im Store sichtbar. Verwenden Sie diese Option nur, wenn das Angebot nicht allgemein verfügbar ist, z.B. im Anfangszeitraum interner Tests.
-   **Beenden des Erwerbs: Alle Kunden mit einem direkten Link können den Produkt-Store-Eintrag sehen, aber sie können ihn nur herunterladen, wenn sie das Produkts vorher erworben haben oder einen Werbecode und ein Windows10-Gerät verwenden. Dieses Add-On wird nicht im übergeordneten Produkteintrag angezeigt**: Wenn Sie diese Option auswählen, wird das Add-On nicht im App Eintrag angezeigt, und neuen Kunden können das Add-On nicht erwerben. Jedoch, **diese Option wird für Kunden mit Windows8.1 oder früher nicht unterstützt**. Wenn Ihre app zuvor veröffentlichten auf Windows8.1 oder früheren Versionen ist, kann das Add-on weiterhin verfügbar für diesen Kunden erworben werden. Um das Add-on Kunden anbieten auf Windows8.1 oder einer früheren Version, müssen Sie Ihre app, um den Code zu entfernen, der den Add-on-Angebote zu aktualisieren und dann eine neue Übermittlung für die app veröffentlichen. Dies wird empfohlen, auch wenn Ihre app Windows8.1 als Ziel nicht oder frühere Versionen Es ist besser für Ihre Kunden, wenn Sie noch nie ein Add-on, die Sie sich entschieden haben anbieten, um nicht verfügbar zu machen.
    
 > [!NOTE] 
 > Das Auswählen der Option **Beenden des Erwerbs** und/oder das Übermitteln eines App-Updates, durch das das Add-On aus dem Code der App entfernt wird, wirkt sich nicht auf Kunden aus, die das Add-On bereits erworben haben, und zwar unabhängig von ihrem Betriebssystem.


## <a name="schedule"></a>Zeitplan

Standardmäßig (es sei denn, Sie haben eine der Optionen für **Hidden in the Store** im Abschnitt **Sichtbarkeit** ausgewählt) wird Ihre Add-On für Kunden zur Verfügung gestellt, sobald sie die Zertifizierung bestanden und den Veröffentlichungsprozess abgeschlossen hat. Um ein anderes Datum auszuwählen, wählen Sie **Optionen anzeigen**, um diesen Abschnittzu erweitern. 

Weitere Informationen finden Sie unter [Konfigurieren des genauen Veröffentlichungszeitplans](configure-precise-release-scheduling.md).


## <a name="pricing"></a>Preise

Sie müssen einen Grundpreis für Ihr Add-on auswählen (es sei denn, Sie die **Beenden des Erwerbs** Option im Abschnitt **Sichtbarkeit** ausgewählt haben). Die Standardeinstellung ist **kostenlos**, also wenn Sie Geld für das Add-on erheben möchten, müssen Sie eine der verfügbaren Preisniveaus auswählen (beginnend mit.99 US-Dollar) auswählen.

Sie können auch Preisänderungen planen, um das Datum und die Uhrzeit anzugeben, an dem bzw. zu der sich der Preis Ihrer Add-On ändern soll. Darüber hinaus haben Sie die Möglichkeit, diese Änderungen für bestimmte Märkte anzupassen. 

> [!TIP]
> Sie können nicht für Abonnement-Add-Ons den Preis auslösen, nach der Veröffentlichung des Add-Ons, durch einen höheren Grundpreis in einer späteren Übermittlung auswählen oder durch einen Preis ändern, die den Preis erhöht Planung. Sie können einen geringeren Preis mit einer dieser Methoden auswählen, aber sobald der Preis gesenkt wird nicht mehr es über diese neue Preis ausgelöst werden. Aus diesem Grund ist es besonders wichtig, um sicherzustellen, dass Sie die entsprechenden Preisstufe für Abonnement-Add-Ons auswählen. 

Weitere Informationen finden Sie unter [Festlegen und Planen von App-Preisen](set-and-schedule-app-pricing.md).


## <a name="sale-pricing"></a>Sonderpreise

Wenn Sie Ihr Add-On zu einem reduzierten Preis für einen begrenzten Zeitraum anbieten möchten, können Sie ein Sonderangebot erstellen und planen. Weitere Informationen finden Sie unter [Anbieten von Apps und Add-Ons](put-apps-and-add-ons-on-sale.md).



