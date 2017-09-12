---
author: jnHs
Description: "Sie können Ihre App mit Apps von anderen Entwicklern bewerben. Dieses Feature wird Community-Anzeigen genannt."
title: Informationen zu Community-Anzeigen
ms.assetid: F55CE478-99AF-4B70-90D1-D16419562136
ms.author: wdg-dev-content
ms.date: 07/05/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: c16f474fe8242e2994350f5261c26c7148aea5e4
ms.sourcegitcommit: 10f8dcf69d37cdb61562fc9f4d268ccb499c368f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2017
---
# <a name="about-community-ads"></a>Informationen zu Community-Anzeigen

Wenn Ihre App [Banneranzeigen oder Banner-Interstitialwerbung anzeigt](../monetize/display-ads-in-your-app.md), können Sie Ihre App mit anderen Entwicklern mit Apps im WindowsStore kostenlos bewerben. Dieses Feature wird *Community-Anzeigen* genannt.  

Das funktioniert wie folgt:

* Nachdem Sie sich für die [Teilnahme an Community-Anzeigen](#how-to-opt-in-to-community-ads) entschieden und eine [kostenlose Community-Anzeigenkampagne](create-an-ad-campaign-for-your-app.md) erstellt haben, teilt sich Ihre App den Platz für Werbeanzeigen mit anderen Entwicklern, die sich ebenfalls für die Nutzung von Community-Anzeigen entschieden haben. In Ihrer App werden Anzeigen für Apps anderer Entwickler angezeigt, die an Community-Anzeigen teilnehmen. Im Gegenzug werden in deren Apps Anzeigen für Ihre App angezeigt.
* Durch die Anzeige von Community-Anzeigen in Ihrer App erwerben Sie Guthaben für Werbefläche in anderen Apps. Das Guthaben wird wie folgt berechnet:
  * Für jedes Land bzw. jede Region, in dem bzw. in der eine App verfügbar ist, die Community-Anzeigen bereitstellt, wird der jeweils aktuelle eCPM-Wert (effektive Kosten pro tausend Anzeigenaufrufe) für das Land oder die Region mit der Anzahl von Anforderungen für Community-Anzeigen multipliziert, die von Ihrer App im betreffenden Land oder in der betreffenden Region gestellt wurden. Dieser Wert entspricht dem Guthaben, das Sie im betreffenden Land oder in der betreffenden Region für Ihre App erworben haben.
  * Ihr gesamtes erworbenes Guthaben für einen bestimmten Zeitraum entspricht der Summe sämtlicher Guthaben, die mit allen Ihren Apps, die Community-Anzeigen bereitstellen, in allen Ländern oder Regionen erwirtschaftet wurden.
* Ihr Guthaben wird gleichmäßig auf alle aktiven Community-Anzeigenkampagnen verteilt und auf der Grundlage der jeweils aktuellen eCPM-Werte der Länder, auf die Ihre Community-Anzeigenkampagnen ausgerichtet sind, in Anzeigenaufrufe für Ihre App umgewandelt.
* Informationen zum Nachverfolgen der Performance der Community-Anzeigen in Ihrer App finden Sie im [Bericht zur Anzeigen-Performance](advertising-performance-report.md).

### <a name="opt-in-to-community-ads"></a>Melden Sie sich für Community-Anzeigen an

Bevor Sie eine Community-Anzeigenkampagne für eine Ihrer Apps erstellen können, müssen Sie sich auf der Seite **Monetisierung** &gt; **Gewinnbringende Nutzung mit Anzeigen** für die App im Windows Dev Center-Dashboard anmelden.

Gehen Sie zum Anmelden wie folgt vor:
  * Wenn Ihre App eine UWP-App für Windows10 ist, wechseln Sie zum Abschnitt **Anzeigenvermittlung** auf der Seite, und aktivieren Sie das Kästchen **MicrosoftCommunity-Anzeigen** in der Liste **Weitere Anzeigennetzwerke**.
  * Wenn Ihre App für Windows 8.x oder Windows Phone 8.x gilt, wechseln Sie zum Abschnitt **Community-Anzeigen** auf der Seite, und aktivieren Sie das Kästchen **Show community ads in my app**.

Sie müssen Ihre App nicht noch einmal veröffentlichen, nachdem Sie Ihre Auswahl getroffen haben. Wenn Sie sich angemeldet haben, werden Sie feststellen, dass Sie **Community-Anzeige (kostenlos)** als Kampagnentyp angeben können, wenn Sie eine [Anzeigenkampagne erstellen](create-an-ad-campaign-for-your-app.md).

### <a name="related-topics"></a>Verwandte Themen

* [Monetisierung durch Werbeanzeigen](monetize-with-ads.md)
* [Erstellen einer Anzeigenkampagne für Ihre App](create-an-ad-campaign-for-your-app.md)
