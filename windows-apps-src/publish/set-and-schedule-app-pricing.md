---
author: jnHs
Description: Select the base price for an app and schedule price changes. You can also customize these options for specific markets.
title: Festlegen und Planen von App-Preisen
ms.author: wdg-dev-content
ms.date: 05/08/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Preise, App-Preise, App-Preis, Apps verkaufen, Preis ändern, benutzerdefinierter Preis, Preis, Preise, Kosten, Grundpreise überschreiben, formfreier Preis, formfrei
ms.localizationpriority: medium
ms.openlocfilehash: ca37d0b360679a878cff3aeabd96f82016c36fde
ms.sourcegitcommit: 914b38559852aaefe7e9468f6f53a7465bf36e30
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "3393336"
---
# <a name="set-and-schedule-app-pricing"></a>Festlegen und Planen von App-Preisen

Im Abschnitt **Preise** der Seite [Preise und Verfügbarkeit](set-app-pricing-and-availability.md) können Sie den Grundpreis für eine App auswählen. Sie können auch [Preisänderungen planen](#schedule-price-changes), um Datum und Uhrzeit anzugeben, an dem bzw. zu der sich der Preis der App ändern soll. Darüber hinaus haben Sie die Option, den [Grundpreis für den angegebenen Markt zu überschreiben](#override-base-price-for-specific-markets), indem Sie ein neues Preisniveau oder einen formfreien Preis in der lokalen Währung des Markts auswählen.

> [!NOTE]
> Obwohl dieses Thema auf Apps verweist, verwendet die Preisauswahl für die Add-On-Übermittlungen das gleiche Verfahren. Beachten Sie, dass für [Abonnement-Add-Ons](../monetize/enable-subscription-add-ons-for-your-app.md), der Basispreis, den Sie auswählen jemals (durch Ändern des Basispreis oder indem Sie eine Preisänderung planen) erhöht werden kann nicht Obwohl es beeinträchtigt werden kann.

## <a name="base-price"></a>Grundpreis

Wenn Sie den **Grundpreis** für Ihre App auswählen, wird dieser Preis in sämtlichen Märkten verwendet, in denen Ihre App verkauft wird, es sei denn, Sie überschreiben den Grundpreis für jeden Markt.

Sie können den **Grundpreis** auf **Kostenlos** festlegen oder ein verfügbares Preisniveau festlegen. Dadurch wird der Preis in allen Ländern festgelegt, in denen Sie Ihre App verteilen möchten. Das Preisniveau beginnt bei 0,99USD und steigt schrittweise an (1,10 US-Dollar, 1,29 USD usw.). Die Schritte werden mit steigender Preishöhe größer. 

> [!NOTE]
> Diese Preisniveaus gelten auch für Add-Ons. 

Jedes Preisniveau hat einen entsprechenden Wert in jeder der über 60vom Store angebotenen Währungen. Diese Werte sollten Ihnen helfen, Ihre Apps weltweit zu vergleichbaren Preisen zu verkaufen. Sie können den Grundpreis in einer beliebigen Währung auswählen, für verschiedene Märkte wird automatisch der entsprechende Wert verwendet. Beachten Sie, dass wir gelegentlich den entsprechenden Wert für einen bestimmten Markt aufgrund der Änderungen der Umrechnungskurse der Währung anpassen.

Klicken Sie im Abschnitt **Preise** auf **Umrechnungstabelle anzeigen**, um die entsprechenden Preise in allen Währungen anzuzeigen. Hier wird für jedes Preisniveau auch eine ID-Nummer angezeigt, die Sie bei Verwendung der [Microsoft Store-Übermittlungs-API](../monetize/manage-app-submissions.md#price-tiers) benötigen. Sie können auf **Herunterladen** klicken, um eine Kopie der Tabelle mit den Preisniveaus als CSV-Datei herunterzuladen.

Beachten Sie, dass das von Ihnen ausgewählte Preisniveau u. U. eine Verkaufs- oder Mehrwertsteuer enthält, die Kunden bezahlen müssen. Weitere Informationen über Ihre steuerlichen Verpflichtungen in ausgewählten Märkten finden Sie in den [Steuerinformationen zu kostenpflichtigen Apps](tax-details-for-paid-apps.md). Lesen Sie außerdem die [Überlegungen zu Preisen für die einzelnen Märkte](define-pricing-and-market-selection.md#price-considerations-for-specific-markets).

> [!NOTE]
> Wenn Sie die Option **Beenden des Erwerbs** unter **Make this product available but not discoverable in the Store** im Abschnitt [Sichtbarkeit](choose-visibility-options.md#discoverability) wählen), können Sie den Preis für Ihre Übermittlung nicht festlegen (da niemand die App kaufen kann, es sei denn, durch einen Werbecode, um die App umsonst zu erhalten).

## <a name="schedule-price-changes"></a>Planen von Preisänderungen

Sie können optional eine oder mehrere Preisänderungen planen, wenn sich der Grundpreis Ihrer App an einem bestimmten Datum und zu einer bestimmten Uhrzeit ändern soll. 

> [!IMPORTANT]
> Preisänderungen werden nur für Kunden mit Windows 10-Geräten, (einschließlich Xbox One), angezeigt. Wenn Ihre App frühere Betriebssystemversionen unterstützt, werden die Preisänderungen nicht angewendet. 
>
> - Für Kunden unter Windows8 wird die App immer zum **Grundpreis** (und nicht zum marktspezifischen Preis) angeboten, auch wenn Sie zusätzliche Preisänderungen planen. 
> - Für Kunden unter Windows8.1 und Windows Phone8.1 und früheren Versionen wird die App immer zum ersten Preisniveau für den Markt des Kunden angeboten, auch wenn Sie zusätzliche Preisänderungen in diesem Markt planen.
> 
> Berücksichtigen Sie dies beim Planen von Preisänderungen. Wenn Sie beispielsweise die App zunächst zu einem geringeren Preisniveau veröffentlichen und dann ein Datum planen, an dem der Preis erhöht werden soll, würden Kunden mit älteren Betriebssystemversionen, die die App kaufen, den niedrigeren (ursprünglichen) Preis bezahlen.

Klicken Sie auf **Schedule a price change**, um die Optionen für Preisänderungen anzuzeigen. Wählen Sie das Preisniveau aus, das Sie verwenden möchten (oder geben einen formfreien Preis für die Außerkraftsetzungen des Grundpreises für Einzelmärkte an), und wählen Sie anschließend das Datum, die Uhrzeit und die Zeitzone aus.

Sie können auf **Schedule a price change again** klicken, um beliebig viele nachfolgende Änderungen zu planen.

> [!NOTE]
> Geplante Preisänderungen funktionieren anders als [Sonderpreise](put-apps-and-add-ons-on-sale.md). Wenn Sie eine App als Sonderangebot bereitstellen, wird der Preis durchgestrichen im Store angezeigt, und Kunden sind in der Lage, die App zum Verkaufspreis während des Zeitraums zu kaufen, den Sie ausgewählt haben. Nachdem das Sonderangebot abgelaufen ist, gilt der Verkaufspreises nicht mehr und die App ist erneut zum Grundpreis erhältlich (oder einem anderen Preis, den Sie für diese Markt angegeben haben, falls zutreffend).
>
> Mit einer geplanten Preisänderung können Sie den Preis nach oben oder unten anpassen. Die Änderung erfolgt am angegebenen Datum, wird jedoch nicht als Angebot im Store oder in einem bestimmten Format angezeigt. Die App hat nur einen neuen Grundpreis. 


## <a name="override-base-price-for-specific-markets"></a>Außerkraftsetzung für Grundpreise für die einzelnen Märkte

Die oben ausgewählten Optionen gelten standardmäßig für alle Märkte, in denen Ihre App angeboten wird. Sie können optional den Preis für einen oder mehrere Märkte ändern, entweder durch die Auswahl eines anderen Preisniveaus oder die Angabe eines formfreien Preises in der lokalen Währung des Markts.

> [!IMPORTANT]
> Kunden mit Windows8 wird die App immer zum **Grundpreis** angezeigt, auch wenn Sie einen anderen Preis für ihren Markt auswählen.

Um den Preis für die einzelnen Märkte zu ändern, klicken Sie auf **Select markets for base price override**. Das Popupfenster **Market selection** wird mit allen Märkten angezeigt, in denen Sie Ihre App verfügbar machen möchten. (Wenn Sie Märkte im Abschnitt **Märkte** ausgeschlossen haben, sind diese Märkte nicht verfügbar.) 

Sie können den Grundpreis für einen Markt zu einem bestimmten Zeitpunkt oder für eine Gruppe von Märkten zusammen überschreiben. Danach können Sie den Grundpreis für einen zusätzlichen Markt (oder eine Gruppe zusätzlicher Märkte) überschreiben, indem Sie **Select markets for base price override** erneut auswählen und die unten beschriebene Schritte wiederholen. Um den neuen Preis für einen ausgewählten Markt (oder eine Marktgruppe) zu entfernen, klicken Sie auf **Entfernen**.


### <a name="override-the-base-price-for-a-single-market"></a>Überschreiben des Grundpreises für einen einzelnen Markt

Um den Preis für einen einzigen Markt zu ändern, wählen Sie diesen aus und klicken Sie auf **Erstellen**. Sie sehen dann die gleichen Optionen für **Grundpreis** und **Schedule a price change** wie oben beschrieben, aber die getroffene Auswahl gilt spezifisch für diesen Markt. Da Sie den Grundpreise nur für einen Markt überschrieben, werden die Preisniveaus in der lokalen Währung des Markts angezeigt. Klicken Sie im Abschnitt Preise auf **Umrechnungstabelle anzeigen**, um die entsprechenden Preise in allen Währungen anzuzeigen. 

Das Überschreiben des Grundpreises für einen einzelnen Markt gibt Ihnen außerdem die Möglichkeit, einen formfreien Preis Ihrer Wahl in der lokalen Währung des Markts einzugeben. Auch wenn es nicht den standardmäßigen Preisniveaus entspricht, können Sie jeden gewünschten Preis angeben (in einem minimalen und maximalen Bereich). Dieser Preis wird nur für Kunden unter Windows10 (einschließlich Xbox) auf dem ausgewählten Markt verwendet. 

> [!IMPORTANT]
> Durch einen formfreien Preis wird der Preis nur angepasst (auch wenn sich der Umrechnungskurs ändert), wenn Sie ein Update mit einem neuen Preis übermitteln. 

### <a name="override-the-base-price-for-a-market-group"></a>Überschreiben des Grundpreises für eine Marktgruppe

Um den Grundpreise für mehrere Märkte zu überschreiben, erstellen Sie eine *Marktgruppe*. Dazu wählen Sie die Märkte aus, die Sie aufnehmen möchten, und geben Sie optional einen Namen für die Gruppe ein. (Dieser Name dient nur zu Referenzzwecken und ist nicht für alle Kunden sichtbar.) Wenn Sie fertig sind, klicken Sie auf **Erstellen**. Sie sehen dann die gleichen Optionen für **Grundpreis** und **Schedule a price change** wie oben beschrieben, aber die getroffene Auswahl gilt spezifisch für diese Marktgruppe. Beachten Sie, dass formfreie Preise nicht mit Marktgruppen verwendet werden können. Sie müssen ein verfügbares Preisniveau auswählen.

Um die Märkte, die in einer Marktgruppe enthalten sind zu ändern, klicken Sie auf den Namen der Marktgruppe und fügen Sie alle Märkte hinzu oder entfernen Sie diese und klicken Sie auf **OK**, um Ihre Änderungen zu speichern. 

> [!NOTE]
> Ein Markt kann nicht Mitglied mehrerer Marktgruppen innerhalb des Abschnitts **Preise** sein.





