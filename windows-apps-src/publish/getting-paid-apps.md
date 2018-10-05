---
author: jnHs
Description: Here’s some important info you’ll need to ensure that you receive payment for your apps, in-app products (IAPs), and advertising earnings.
title: Bezahlung
ms.assetid: 37D1EF45-C4A8-4849-8819-3D4A4898215C
ms.author: wdg-dev-content
ms.date: 02/05/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Bezahlung, App-Verkäufe, App-Erlöse, Auszahlung, Store-Gebühr, Auszahlungssperre, Prozentsatz
ms.localizationpriority: medium
ms.openlocfilehash: 0c128bedd1c889f4c2dcf0565c7c10575eb75013
ms.sourcegitcommit: 63cef0a7805f1594984da4d4ff2f76894f12d942
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2018
ms.locfileid: "4383616"
---
# <a name="getting-paid"></a>Bezahlung
Im Folgenden finden Sie wichtige Informationen, mit deren Hilfe Sie sicherstellen können, dass Sie für Ihre Apps, Add-Ons und Ihren Advertising-Verdienst bezahlt werden.

> [!IMPORTANT]
> Bevor Sie Geld aus App-Verkäufen im MicrosoftStore erhalten können, müssen Sie [Ihr Auszahlungskonto einrichten und die erforderlichen Steuerformulare ausfüllen](setting-up-your-payout-account-and-tax-forms.md).

## <a name="store-fee"></a>Store-Gebühr

Wenn Sie sich [für ein Entwicklerkonto registrieren](http://go.microsoft.com/fwlink/p/?LinkID=615100), akzeptieren Sie die [Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement). In dieser Vereinbarung ist die Geschäftsbeziehung zwischen Ihnen und Microsoft in Bezug auf den Verkauf von Apps im MicrosoftStore erläutert, einschließlich der Store-Gebühr, die Microsoft für jeden Verkauf erhebt.

In den meisten Fällen beträgt die Store-Gebühr 30%. Die Gebühren sind in der [Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement) offiziell definiert. Lesen Sie bei Fragen immer in diesem Dokument nach.

Die MicrosoftStore-Gebühr gilt für alle vom MicrosoftStore erfassten App-Verkäufe einschließlich Add-Ons.


## <a name="price-tiers"></a>Preisniveaus

Das Preisniveau bestimmt den [Verkaufspreis](set-and-schedule-app-pricing.md#base-price) in allen Ländern, in denen Sie Ihre App vertreiben möchten. Sie können auch zusätzliche Preis-Features verwenden, wie z.B. [um in verschiedenen Märkten unterschiedliche Preise zu verlangen](set-and-schedule-app-pricing.md#override-base-price-for-specific-markets) oder [Ihre App zum Erwerb anbieten](put-apps-and-add-ons-on-sale.md).

Sie können die App kostenlos anbieten oder einen Preis auswählen, den Kunden zahlen müssen, um die App zu erwerben. Das Preisniveau beginnt bei 0,99USD und steigen schrittweise (1,09USD, 1,19USD, usw.). Die Schritte zwischen den Preisniveaus werden mit der Höhe des Preises größer.

> [!NOTE] 
> Diese Preisniveaus gelten auch für alle Add-Ons, die Sie in der App anbieten.

Jedes Preisniveau hat einen entsprechenden Wert in jeder vom Store angebotenen Währungen. Diese Werte sollten Ihnen helfen, Ihre Apps weltweit zu vergleichbaren Preisen zu verkaufen. Aufgrund von Wechselkursschwankungen kann der genaue Verkaufsbetrag von Währung zu Währung jedoch geringfügig abweichen.

Sie haben auch die Möglichkeit, einen formfreien Preis Ihrer Wahl in der lokalen Währung für einen bestimmten Markt anzugeben. Dadurch wird der Preis nur angepasst (auch wenn sich der Umrechnungskurs ändert), wenn Sie ein Update mit einem neuen Preis übermitteln. 

Beachten Sie, dass der von Ihnen ausgewählte Preis u. U. eine Verkaufs- oder Mehrwertsteuer enthält, die Kunden bezahlen müssen. Weitere Informationen finden Sie unter [Steuerinformationen zu kostenpflichtigen Apps](tax-details-for-paid-apps.md).


## <a name="payout-reporting"></a>Auszahlungsberichte

Sie haben Zugriff auf ausführliche Auszahlungsinformationen und können die Berichte in die **Auszahlungszusammenfassung** des Windows Dev Center-Dashboards herunterladen. Weitere Informationen zu den aufgeführten Details und zu den Kategorien, in die wir Ihre Erlöse einteilen, finden Sie unter [Auszahlungszusammenfassung](payout-summary.md).


## <a name="payout-timeframe"></a>Auszahlungszeitraum

Zahlungen erfolgen monatlich (vorausgesetzt, der entsprechende Zahlungsschwellenwert wurde erreicht, und Sie haben die Auszahlung nicht gesperrt, wie unten beschrieben). In der Regel senden wir Zahlungen, die in einem bestimmten Monat fällig sind, bis zum 15. Tag dieses Monats. Beachten Sie, dass Zahlungen in der Regel zwischen drei und zehn zusätzliche Werktage benötigen, um Ihr Konto zu erreichen. Weitere Informationen finden Sie unter [Auszahlungsschwellenwerte, Methoden und Zeiträume](payment-thresholds-methods-and-timeframes.md).


##  <a name="payout-hold-status"></a>Auszahlungssperre

Standardmäßig senden wir Zahlungen monatlich, wie oben beschrieben. Sie haben jedoch die Möglichkeit, Ihre Auszahlungen zu sperren, sodass wir keine Zahlungen an Ihr Konto senden können. Wenn Sie Ihre Auszahlungen sperren, zeichnen wir weiterhin alle Ihre Umsätze auf und geben die Details in Ihrer **Auszahlungszusammenfassung** an. Allerdings senden wir so lange keine Zahlungen an Ihr Konto, bis Sie die Sperre entfernen. 

Um Ihre Zahlungen zu sperren, wechseln Sie zu **Kontoeinstellungen**. Setzen Sie den Schieberegler unter **Finanzielle Details** im Bereich **Payout hold status** auf **Ein**. Sie können die Auszahlungssperre jederzeit ändern. Beachten Sie jedoch, dass sich Ihre Auswahl auf die nächste monatliche Auszahlung auswirkt. Wenn Sie beispielsweise die April-Auszahlung sperren möchten, sollten Sie die Auszahlungssperre schon vor Ende März auf **Ein** festlegen.

Nachdem Sie die Auszahlungssperre auf **Ein** festgelegt haben, werden alle Auszahlungen gesperrt, bis Sie den Schieberegler wieder auf **Aus** setzen. Dann werden Sie im nächsten monatlichen Auszahlungszyklus berücksichtigt (vorausgesetzt, der entsprechende Zahlungsschwellenwert wurde erreicht). Wenn Sie zum Beispiel Ihre Auszahlungen gesperrt haben, aber eine Auszahlung im Juni generieren möchten, sollten Sie die Auszahlungssperre noch vor Ende Mai auf **Aus** setzen.

> [!NOTE]
> Die festgelegte Option für **Auszahlungssperre** gilt für **alle** Umsatzquellen, die über Windows Dev Center (Microsoft Store, Microsoft Advertising, Azure Marketplace usw.) bezahlt werden. Es ist nicht möglich, für jede Umsatzquelle eine separate Option für die Auszahlungssperre festzulegen.


 

 




