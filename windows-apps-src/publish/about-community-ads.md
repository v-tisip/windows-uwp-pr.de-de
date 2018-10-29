---
author: jnHs
Description: You can cross-promote your app with apps published by other developers. We call this feature community ads.
title: Informationen zu Community-Anzeigen
ms.assetid: F55CE478-99AF-4B70-90D1-D16419562136
ms.author: wdg-dev-content
ms.date: 10/04/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 20f0f06d0927d61c062a0514d84bef993da6e932
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "5748476"
---
# <a name="about-community-ads"></a>Informationen zu Community-Anzeigen

Wenn Ihre app [zeigt Banneranzeigen oder Banner-interstitialwerbung](../monetize/display-ads-in-your-app.md)Sie Ihre app mit anderen Entwicklern mit apps im Microsoft Store für kostenlose bewerben können. Dieses Feature wird *Community-Anzeigen* genannt.  

Das funktioniert wie folgt:

* Nachdem Sie für Community-anzeigen, wie unten beschrieben Teilnahme, können Sie [eine kostenlose Community-Anzeigenkampagne erstellen](create-an-ad-campaign-for-your-app.md). Ihre app wird dann Werbefläche mit anderen Entwicklern freigeben, die ebenfalls für Community-anzeigen entschieden haben. In Ihrer App werden Anzeigen für Apps anderer Entwickler angezeigt, die an Community-Anzeigen teilnehmen. Im Gegenzug werden in deren Apps Anzeigen für Ihre App angezeigt.
* Durch die Anzeige von Community-Anzeigen in Ihrer App erwerben Sie Guthaben für Werbefläche in anderen Apps. Das Guthaben wird wie folgt berechnet:
  * Für jedes Land bzw. jede Region, in dem bzw. in der eine App verfügbar ist, die Community-Anzeigen bereitstellt, wird der jeweils aktuelle eCPM-Wert (effektive Kosten pro tausend Anzeigenaufrufe) für das Land oder die Region mit der Anzahl von Anforderungen für Community-Anzeigen multipliziert, die von Ihrer App im betreffenden Land oder in der betreffenden Region gestellt wurden. Dieser Wert entspricht dem Guthaben, das Sie im betreffenden Land oder in der betreffenden Region für Ihre App erworben haben.
  * Ihr gesamtes erworbenes Guthaben für einen bestimmten Zeitraum entspricht der Summe sämtlicher Guthaben, die mit allen Ihren Apps, die Community-Anzeigen bereitstellen, in allen Ländern oder Regionen erwirtschaftet wurden.
* Ihr Guthaben wird gleichmäßig auf alle aktiven Community-Anzeigenkampagnen verteilt und auf der Grundlage der jeweils aktuellen eCPM-Werte der Länder, auf die Ihre Community-Anzeigenkampagnen ausgerichtet sind, in Anzeigenaufrufe für Ihre App umgewandelt.
* Informationen zum Nachverfolgen der Performance der Community-Anzeigen in Ihrer App finden Sie im [Bericht zur Anzeigen-Performance](advertising-performance-report.md).

### <a name="opt-in-to-community-ads"></a>Melden Sie sich für Community-Anzeigen an

Bevor Sie eine Community-Anzeigenkampagne für eine Ihrer apps erstellen können, Sie müssen entscheiden Sie sich auf die **Monetarisierung** &gt; **In-app-Werbung** Seite im Windows Dev Center-Dashboard.

Melden Sie sich für Community-anzeigen für eine UWP-app an:

1. Wählen Sie im Abschnitt **vermittlungseinstellungen** auf der Seite " **In-app-anzeigen** " eine anzeigeneinheit, die Sie in der app verwenden.
2. Wenn die Option **ermöglichen Microsoft auswählen die besten anzeigenvermittlungseinstellungen für Ihre app** aktiviert ist, werden automatisch die Community-anzeigen für Ihre anzeigeneinheit aktiviert. Andernfalls wählen Sie die Basiskonfiguration oder eine marktspezifische Konfiguration in der **Ziel** -Dropdown-Liste, und klicken Sie dann das Kontrollkästchen Sie **Microsoft Community-anzeigen** in der Liste **Weitere anzeigennetzwerke** .

    > [!NOTE]
    > Die Felder, die **Gewichtung** können Sie das Verhältnis der anzeigen angeben, die von kostenpflichtigen Netzwerken und anderen Anzeigennetzwerken, einschließlich der Community-anzeigen angezeigt werden sollen.

Um an Community-anzeigen für eine Windows beteiligen 8.x oder Windows Phone 8.x-app

1. Überprüfen Sie auf der Seite **In-app-Werbung** das **Community-anzeigen in meiner app anzeigen** .

Sie müssen Ihre App nicht noch einmal veröffentlichen, nachdem Sie Ihre Auswahl getroffen haben. Wenn Sie sich angemeldet haben, werden Sie feststellen, dass Sie **Community-Anzeige (kostenlos)** als Kampagnentyp angeben können, wenn Sie eine [Anzeigenkampagne erstellen](create-an-ad-campaign-for-your-app.md).

### <a name="related-topics"></a>Verwandte Themen

* [In-App-Anzeigen](in-app-ads.md)
* [Erstellen einer Anzeigenkampagne für Ihre App](create-an-ad-campaign-for-your-app.md)
