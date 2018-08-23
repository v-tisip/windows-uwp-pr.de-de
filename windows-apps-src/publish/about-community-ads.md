---
author: jnHs
Description: You can cross-promote your app with apps published by other developers. We call this feature community ads.
title: Informationen zu Community-Anzeigen
ms.assetid: F55CE478-99AF-4B70-90D1-D16419562136
ms.author: wdg-dev-content
ms.date: 10/04/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: ada2e0610e81e986deba3ddab5e87547e05fe108
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2811840"
---
# <a name="about-community-ads"></a>Informationen zu Community-Anzeigen

Wenn Ihre app [zeigt Banner oder Banner interstitielles Ads](../monetize/display-ads-in-your-app.md)Sie Cross-Ihrer app mit anderen Entwicklern mit apps im Microsoft Store für kostenlose heraufstufen können. Dieses Feature wird *Community-Anzeigen* genannt.  

Das funktioniert wie folgt:

* Nachdem Sie Community anzeigen, wie unten beschrieben Teilnahme, können Sie [Erstellen Sie eine kostenlose Community Ad Kampagne](create-an-ad-campaign-for-your-app.md). Ihre app freigeben Werbe Ad Speicherplatz klicken Sie dann mit anderen Entwicklern, die auch für Community anzeigen zu bestätigen. In Ihrer App werden Anzeigen für Apps anderer Entwickler angezeigt, die an Community-Anzeigen teilnehmen. Im Gegenzug werden in deren Apps Anzeigen für Ihre App angezeigt.
* Durch die Anzeige von Community-Anzeigen in Ihrer App erwerben Sie Guthaben für Werbefläche in anderen Apps. Das Guthaben wird wie folgt berechnet:
  * Für jedes Land bzw. jede Region, in dem bzw. in der eine App verfügbar ist, die Community-Anzeigen bereitstellt, wird der jeweils aktuelle eCPM-Wert (effektive Kosten pro tausend Anzeigenaufrufe) für das Land oder die Region mit der Anzahl von Anforderungen für Community-Anzeigen multipliziert, die von Ihrer App im betreffenden Land oder in der betreffenden Region gestellt wurden. Dieser Wert entspricht dem Guthaben, das Sie im betreffenden Land oder in der betreffenden Region für Ihre App erworben haben.
  * Ihr gesamtes erworbenes Guthaben für einen bestimmten Zeitraum entspricht der Summe sämtlicher Guthaben, die mit allen Ihren Apps, die Community-Anzeigen bereitstellen, in allen Ländern oder Regionen erwirtschaftet wurden.
* Ihr Guthaben wird gleichmäßig auf alle aktiven Community-Anzeigenkampagnen verteilt und auf der Grundlage der jeweils aktuellen eCPM-Werte der Länder, auf die Ihre Community-Anzeigenkampagnen ausgerichtet sind, in Anzeigenaufrufe für Ihre App umgewandelt.
* Informationen zum Nachverfolgen der Performance der Community-Anzeigen in Ihrer App finden Sie im [Bericht zur Anzeigen-Performance](advertising-performance-report.md).

### <a name="opt-in-to-community-ads"></a>Melden Sie sich für Community-Anzeigen an

Bevor Sie eine Ad-Kampagne Community für einen Ihrer Apps erstellen können, Sie müssen entscheiden Sie sich auf die **Monetize** &gt; **Ads - app-** Seite im Windows-Entwicklungscenter Dashboard.

Zum Anzeigen der Community für eine app UWP zu abonnieren:

1. Wählen Sie im Abschnitt **Mediation Einstellungen** auf der Seite **innerhalb der app anzeigen** eine Ad-Komponente, die Sie in der app verwenden.
2. Wenn die Option **Microsoft Let wählen Sie die besten Mediation Einstellungen für Ihre app** ausgewählt ist, werden automatisch die Community Ads für Ihr Gerät Ad aktiviert. Anderenfalls wählen Sie die Basiskonfiguration oder einer Markt-spezifische Konfiguration in der Dropdownliste **Ziel** aus, und klicken Sie dann das Kontrollkästchen Sie **Microsoft-Community anzeigen** in der Liste **andere Ad-Netzwerke** .

    > [!NOTE]
    > Die **Gewichtung** Felder können Sie das Verhältnis der Ads angeben, den Sie aus den kostenpflichtigen Netzen und andere Ad-Netzwerke, einschließlich Community Ads anzeigen möchten.

Zur Community Werbung für eine Windows Anmeldung 8.x oder Windows Phone-app 8.x

1. Auf der Seite **innerhalb der app anzeigen** das Kontrollkästchen Sie **Community Werbung in Meine app anzuzeigen** .

Sie müssen Ihre App nicht noch einmal veröffentlichen, nachdem Sie Ihre Auswahl getroffen haben. Wenn Sie sich angemeldet haben, werden Sie feststellen, dass Sie **Community-Anzeige (kostenlos)** als Kampagnentyp angeben können, wenn Sie eine [Anzeigenkampagne erstellen](create-an-ad-campaign-for-your-app.md).

### <a name="related-topics"></a>Verwandte Themen

* [In-App-Anzeigen](in-app-ads.md)
* [Erstellen einer Anzeigenkampagne für Ihre App](create-an-ad-campaign-for-your-app.md)
