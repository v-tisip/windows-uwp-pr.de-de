---
author: jnHs
Description: "Wählen Sie den Grundpreis für eine App, und planen Sie Preisänderungen. Sie können diese Optionen auch für bestimmte Märkte anpassen."
title: Festlegen und Planen von App-Preisen
ms.author: wdg-dev-content
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 65d2fa64e4d442da42b8c546693c61eda817aa18
ms.sourcegitcommit: 968187e803a866b60cda0528718a3d31f07dc54c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="set-and-schedule-app-pricing"></a>Festlegen und Planen von App-Preisen

Im Abschnitt **Preise** der Seite [Preise und Verfügbarkeit](set-app-pricing-and-availability.md) können Sie den Grundpreis für eine App auswählen. Sie können auch [Preisänderungen planen](#schedule-price-changes), um Datum und Uhrzeit anzugeben, an dem bzw. zu der sich der Preis der App ändern soll. Darüber hinaus haben Sie die Möglichkeit, [diese Änderungen für bestimmte Märkte anzupassen](#customize-pricing-for-specific-markets). 

> [!NOTE]
> Obwohl dieses Thema auf Apps verweist, verwendet die Preisauswahl für die Add-On-Übermittlungen das gleiche Verfahren.

## <a name="base-price"></a>Grundpreis

Wenn Sie den **Grundpreis** für Ihre App auswählen, wird dieser Preis in sämtlichen Märkten verwendet, in denen Ihre App verkauft wird, es sei denn, Sie legen für einen bestimmten Markt bzw. Märkte einen angepassten Preis fest.

Sie können den **Grundpreis** auf **Kostenlos** festlegen oder ein verfügbares Preisniveau festlegen. Dadurch wird der Verkaufspreis in allen Ländern festgelegt, in denen Sie Ihre App verteilen möchten. Das Preisniveau beginnt bei 0,99USD und steigt schrittweise an (1,10 US-Dollar, 1,29 USD usw.). Die Schritte werden mit steigender Preishöhe größer. 

> [!NOTE]
> Diese Preisniveaus gelten auch für Add-Ons. 

Jedes Preisniveau hat einen entsprechenden Wert in jeder der über 60vom Store angebotenen Währungen. Diese Werte sollten Ihnen helfen, Ihre Apps weltweit zu vergleichbaren Preisen zu verkaufen. Sie können den Grundpreis in einer beliebigen Währung auswählen, für verschiedene Märkte wird automatisch der entsprechende Wert verwendet.

Klicken Sie im Abschnitt **Preise** auf **Tabelle anzeigen**, um die entsprechenden Preise in allen Währungen anzuzeigen. Hier wird für jedes Preisniveau auch eine ID-Nummer angezeigt, die Sie bei Verwendung der [Windows Store-Übermittlungs-API](../monetize/manage-app-submissions.md#price-tiers) benötigen. Sie können auf **Herunterladen** klicken, um eine Kopie der Tabelle mit den Preisniveaus als CSV-Datei herunterzuladen.

Beachten Sie, dass das von Ihnen ausgewählte Preisniveau u. U. eine Verkaufs- oder Mehrwertsteuer enthält, die Kunden bezahlen müssen. Weitere Informationen über Ihre steuerlichen Verpflichtungen in ausgewählten Märkten finden Sie in den [Steuerinformationen zu kostenpflichtigen Apps](tax-details-for-paid-apps.md). Lesen Sie außerdem die [Überlegungen zu Preisen für die einzelnen Märkte](define-pricing-and-market-selection.md#price-considerations-for-specific-markets).

## <a name="schedule-price-changes"></a>Planen von Preisänderungen

Sie können optional eine oder mehrere Preisänderungen planen, wenn sich der Grundpreis Ihrer App an einem bestimmten Datum und zu einer bestimmten Uhrzeit ändern soll. 

> [!IMPORTANT]
> Preisänderungen werden nur für Kunden mit Windows10 angezeigt. Wenn Ihre App frühere Betriebssystemversionen unterstützt, werden die Preisänderungen nicht angewendet. 
>
> - Für Kunden unter Windows8 wird die App immer zum **Grundpreis** (und nicht zum marktspezifischen Preis) angeboten, auch wenn Sie zusätzliche Preisänderungen planen. 
> - Für Kunden unter Windows8.1 und Windows Phone8.1 und früheren Versionen wird die App immer zum ursprünglichen Preis für den Markt des Kunden angeboten, auch wenn Sie zusätzliche Preisänderungen in diesem Markt planen.
> 
> Berücksichtigen Sie dies beim Planen von Preisänderungen. Wenn Sie beispielsweise die App zunächst zu einem geringeren Preis veröffentlichen und dann ein Datum planen, an dem der Preis erhöht werden soll, würden Kunden mit älteren Betriebssystemversionen, die die App kaufen, den niedrigeren (ursprünglichen) Preis bezahlen.

Klicken Sie auf **Schedule a price change**, um die Optionen für Preisänderungen anzuzeigen. Wählen Sie das Preisniveau, das Sie verwenden möchten, und wählen Sie dann Datum, Uhrzeit und Zeitzone.

Sie können auf **Schedule a price change again** klicken, um beliebig viele nachfolgende Änderungen zu planen.

> [!NOTE]
> Geplante Preisänderungen funktionieren anders als [Sonderpreise](put-apps-and-add-ons-on-sale.md). Wenn Sie eine App als Sonderangebot bereitstellen, können Kunden im Store-Eintrag sehen, dass der Preis reduziert wurde, und die App während des von Ihnen ausgewählten Zeitraums zum reduzierten Preis kaufen. Nach Ablauf des Angebotszeitraums wird wieder der Grundpreis verwendet.
>
> Mit einer geplanten Preisänderung können Sie den Preis nach oben oder unten anpassen. Die Änderung erfolgt am angegebenen Datum, wird jedoch nicht als Angebot im Store angezeigt. Die App hat nur einen neuen Grundpreis. 

## <a name="customize-pricing-for-specific-markets"></a>Anpassen der Preise für bestimmte Märkte

Die oben ausgewählten Optionen gelten standardmäßig für alle Märkte, in denen Ihre App angeboten wird. Wenn Sie den Preis für die einzelnen Märkte anpassen möchten, wählen Sie **Customize for specific markets**. Das Popupfenster **Market selection** wird mit allen Märkten angezeigt, in denen Sie Ihre App verfügbar machen möchten. Wenn Sie Märkte im AbschnittMärkte ausgeschlossen haben, werden diese Märkte hier nicht angezeigt. 

> [!IMPORTANT]
> Kunden mit Windows8 wird die App immer zum **Grundpreis** angezeigt, auch wenn Sie einen anderen Preis für ihren Markt auswählen.

Zum Hinzufügen von benutzerdefinierten Preisen für einen Markt wählen Sie ihn aus, und klicken Sie auf **Speichern**. Sie sehen dann die gleichen Optionen für **Grundpreis** und **Schedule a price change** wie oben beschrieben, aber die getroffene Auswahl gilt spezifisch für diesen Markt.

Zum Hinzufügen von benutzerdefinierten Preisen für mehrere Märkte erstellen Sie eine *Marktgruppe*. Dazu wählen Sie die Märkte aus, die Sie aufnehmen möchten, und geben einen Namen für die Gruppe ein. (Dieser Name dient nur zu Referenzzwecken und ist nicht für alle Kunden sichtbar.) Wenn Sie fertig sind, klicken Sie auf **Speichern**. Sie sehen dann die gleichen Optionen für **Grundpreis** und **Schedule a price change** wie oben beschrieben, aber die getroffene Auswahl gilt spezifisch für diese Marktgruppe.

> [!NOTE]
> Ein Markt kann nicht zu mehr als einer der Marktgruppen gehören, die Sie im Abschnitt Preise verwenden.

Um benutzerdefinierte Preise für einen zusätzlichen Markt oder eine weitere Marktgruppe hinzuzufügen, wählen Sie erneut **Customize for specific markets**, und wiederholen Sie diese Schritte. Wählen Sie zum Ändern der in einer Marktgruppe enthaltenen Märkte den Namen aus. Um den Preis für eine Marktgruppe (oder einen einzelnen Markt) zu entfernen, klicken Sie auf **Entfernen**.



