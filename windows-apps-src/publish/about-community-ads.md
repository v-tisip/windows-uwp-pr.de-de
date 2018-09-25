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
ms.sourcegitcommit: 232543fba1fb30bb1489b053310ed6bd4b8f15d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2018
ms.locfileid: "4178539"
---
# <a name="about-community-ads"></a>Informationen zu Community-Anzeigen

Wenn Ihre app [zeigt Banneranzeigen oder Banner-interstitialwerbung](../monetize/display-ads-in-your-app.md)Sie Ihre app mit anderen Entwicklern mit apps im Microsoft Store kostenlos bewerben können. Dieses Feature wird *Community-Anzeigen* genannt.  

Das funktioniert wie folgt:

* Nachdem Sie für Community-anzeigen, wie unten beschrieben Teilnahme, können Sie [eine kostenlose Community-Anzeigenkampagne erstellen](create-an-ad-campaign-for-your-app.md). Ihre app wird dann Werbefläche für andere Entwickler freigeben, die ebenfalls für Community-anzeigen entschieden haben. In Ihrer App werden Anzeigen für Apps anderer Entwickler angezeigt, die an Community-Anzeigen teilnehmen. Im Gegenzug werden in deren Apps Anzeigen für Ihre App angezeigt.
* Durch die Anzeige von Community-Anzeigen in Ihrer App erwerben Sie Guthaben für Werbefläche in anderen Apps. Das Guthaben wird wie folgt berechnet:
  * Für jedes Land bzw. jede Region, in dem bzw. in der eine App verfügbar ist, die Community-Anzeigen bereitstellt, wird der jeweils aktuelle eCPM-Wert (effektive Kosten pro tausend Anzeigenaufrufe) für das Land oder die Region mit der Anzahl von Anforderungen für Community-Anzeigen multipliziert, die von Ihrer App im betreffenden Land oder in der betreffenden Region gestellt wurden. Dieser Wert entspricht dem Guthaben, das Sie im betreffenden Land oder in der betreffenden Region für Ihre App erworben haben.
  * Ihr gesamtes erworbenes Guthaben für einen bestimmten Zeitraum entspricht der Summe sämtlicher Guthaben, die mit allen Ihren Apps, die Community-Anzeigen bereitstellen, in allen Ländern oder Regionen erwirtschaftet wurden.
* Ihr Guthaben wird gleichmäßig auf alle aktiven Community-Anzeigenkampagnen verteilt und auf der Grundlage der jeweils aktuellen eCPM-Werte der Länder, auf die Ihre Community-Anzeigenkampagnen ausgerichtet sind, in Anzeigenaufrufe für Ihre App umgewandelt.
* Informationen zum Nachverfolgen der Performance der Community-Anzeigen in Ihrer App finden Sie im [Bericht zur Anzeigen-Performance](advertising-performance-report.md).

### <a name="opt-in-to-community-ads"></a>Melden Sie sich für Community-Anzeigen an

Bevor Sie eine Community-Anzeigenkampagne für eine Ihrer apps erstellen können, Sie müssen entscheiden Sie sich auf die **Monetarisierung** &gt; **In-app-Werbung** Seite im Windows Dev Center-Dashboard.

Melden Sie sich für Community-anzeigen für eine UWP-app an:

1. Wählen Sie im Abschnitt **vermittlungseinstellungen** auf der Seite **In-app anzeigen** eine anzeigeneinheit, die Sie in der app verwenden.
2. Wenn die Option **ermöglichen Microsoft auswählen die besten anzeigenvermittlungseinstellungen für Ihre app** aktiviert ist, werden automatisch Community-anzeigen für Ihre anzeigeneinheit aktiviert. Andernfalls wählen Sie die Basiskonfiguration oder eine marktspezifische Konfiguration in der **Ziel** -Dropdown-Liste, und klicken Sie dann das Kontrollkästchen Sie **Microsoft Community-anzeigen** in der Liste **Weitere anzeigennetzwerke** .

    > [!NOTE]
    > Sie können die **Gewichtung** Felder verwenden, das Verhältnis der anzeigen an, die Sie Anzeigen von kostenpflichtigen Netzwerken und weitere anzeigennetzwerke, einschließlich der Community-anzeigen möchten.

Melden Sie sich für Community-anzeigen für eine Windows an 8.x oder Windows Phone 8.x-app

1. Aktivieren Sie das Kontrollkästchen **Community-anzeigen in meiner app** , auf der Seite **In-app anzeigen** .

Sie müssen Ihre App nicht noch einmal veröffentlichen, nachdem Sie Ihre Auswahl getroffen haben. Wenn Sie sich angemeldet haben, werden Sie feststellen, dass Sie **Community-Anzeige (kostenlos)** als Kampagnentyp angeben können, wenn Sie eine [Anzeigenkampagne erstellen](create-an-ad-campaign-for-your-app.md).

### <a name="related-topics"></a>Verwandte Themen

* [In-App-Anzeigen](in-app-ads.md)
* [Erstellen einer Anzeigenkampagne für Ihre App](create-an-ad-campaign-for-your-app.md)
