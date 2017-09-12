---
author: jnHs
Description: Wenn Ihre App die Anzeigenvermittlung verwendet oder Banner- bzw. Interstitialwerbungen mit dem Microsoft Store Services SDK anzeigt, verwalten Sie die Verwendung Ihrer Anzeigen auf der Seite "Gewinnbringende Nutzung mit Anzeigen".
title: Monetisierung durch Anzeigen
ms.assetid: 09970DE3-461A-4E2A-88E3-68F2399BBCC8
ms.author: wdg-dev-content
ms.date: 07/06/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 6ecd37e54de266764570606ceaa575614dfb050c
ms.sourcegitcommit: 10f8dcf69d37cdb61562fc9f4d268ccb499c368f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2017
---
# <a name="monetize-with-ads"></a>Monetisierung durch Anzeigen

Jede App im Dashboard enthält die Seite **Monetisierung** &gt; **Monetarisierung durch Anzeigen**. Verwenden Sie diese Seite, um die Verwendung Ihrer Anzeigen für die folgenden Entwicklungsszenarios in Ihrer App zu verwalten:

* Ihre UWP-App verwendet ein [AdControl](https://msdn.microsoft.com/en-us/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx), [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx) oder [NativeAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.aspx)-Steuerelement aus dem [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp).
* Ihre Windows8.x- oder WindowsPhone8.x-App verwendet ein **AdControl**- oder **InterstitialAd**-Steuerelement aus dem [Microsoft Advertising-SDK für Windows und Windows Phone8.x](http://aka.ms/store-8-sdk).
* Ihre Windows8.x- oder Windows Phone8.x-App verwendet ein **AdMediatorControl**-Element aus dem [Microsoft Advertising-SDK für Windows und Windows Phone8.x](http://aka.ms/store-8-sdk).

Weitere Informationen zu diesen Entwicklungsszenarien finden Sie unter [Anzeigen von Werbung in Ihrer App mit dem Microsoft Advertising SDK](../monetize/display-ads-in-your-app.md).

<span id="create-ad-unit" />
## <a name="create-ad-units"></a>Erstellen von Anzeigeneinheiten

Verwenden Sie diesen Abschnitt, um eine Anzeigeneinheit für die folgenden Szenarien zu erstellen:

* Ihre App zeigt Banneranzeigen mithilfe von **AdControl** an. Weitere Informationen finden Sie unter [AdControl in XAML und .NET](../monetize/adcontrol-in-xaml-and--net.md) und [AdControl in HTML5 und JavaScript](../monetize/adcontrol-in-html-5-and-javascript.md).
* Ihre App zeigt Videointerstitialwerbungen oder Bannerintersititalwerbungen mithilfe von **InterstitialAd** an. Weitere Informationen finden Sie unter [Interstitialwerbungen](../monetize/interstitial-ads.md).
* Ihre App zeigt native Anzeigen mithilfe von **NativeAd** an. Weitere Informationen finden Sie unter [Native Anzeigen](../monetize/native-ads.md).

So erstellen Sie eine Anzeigenkampagne:

1.  Geben Sie im Feld **Name der Anzeigeneinheit** einen Namen für die Anzeigeneinheit ein. Dies kann eine beliebige beschreibende Zeichenfolge sein, die Sie verwenden, um die Anzeigeneinheit zu Berichterstellungszwecken zu identifizieren.
2.  Wählen Sie in der Dropdownliste **Art der Anzeigeneinheit** den Typ einer Anzeigeneinheit aus, der den in Ihrem Steuerelement angezeigten Anzeigen entspricht. Folgende Optionen sind verfügbar: **Banner**, **Interstitialbanner**, **Interstitialvideo** und **Native Anzeigen**.
    > [!NOTE]
    > Die Möglichkeit zum Erstellen von **nativen** Anzeigeeinheiten steht derzeit nur für Entwickler zur Verfügung, die an einem Pilotprogramm teilnehmen, wir möchten dieses Feature allerdings bald für alle Entwickler zur Verfügung stellen. Wenn Sie an unserem Pilotprogramms teilnehmen möchten, wenden Sie sich an aiacare@microsoft.com.

3.  Wählen Sie in der Dropdownliste **Gerätefamilie** die Gerätefamilie aus, auf die Ihre App ausgerichtet ist, in der die Anzeigeneinheit verwendet werden. Folgende Optionen sind verfügbar: **UWP (Windows 10)**, **PC/Tablet (Windows 8.1)** oder **Mobile (Windows Phone 8.x)**.
4.  Klicken Sie auf **Anzeigeneinheit erstellen**.

Die neue Anzeigeneinheit wird oben in der Liste des Abschnitts **Verfügbare Anzeigeneinheiten** auf dieser Seite angezeigt. Weitere Informationen für die Arbeit mit Anzeigeeinheiten in Ihrer App finden Sie unter [Einrichten von Anzeigeneinheiten in Ihrer App](../monetize/set-up-ad-units-in-your-app.md).

> [!NOTE]
> Wenn Ihre Windows 8.x- oder Windows Phone 8.x-App **AdMediatorControl** zum Anzeigen von Banneranzeigen verwendet, müssen Sie hier keine Anzeigeneinheiten anfordern. In diesem Szenario werden die Anzeigeneinheiten automatisch für Sie generiert.

<span id="available-ad-units" />
## <a name="available-ad-units"></a>Verfügbare Anzeigeneinheiten

Ihre Anzeigeneinheiten werden in einer Tabelle am Ende dieses Abschnitts angezeigt. Für jede Anzeigeneinheit werden eine **Anwendungs-ID** und eine **Anzeigeneinheits-ID** angezeigt. Zum Einblenden von Anzeigen in Ihrer App müssen Sie diese Werte in Ihrem Code verwenden:

-   Wenn Ihre App Werbebanner anzeigt, weisen Sie diese Werte den Eigenschaften [ApplicationId](https://msdn.microsoft.com/library/mt313174.aspx) und [AdUnitId](https://msdn.microsoft.com/library/mt313171.aspx) Ihres [AdControl](https://msdn.microsoft.com/library/mt313154.aspx)-Objekts hinzu. Weitere Informationen finden Sie unter [AdControl in XAML und .NET](../monetize/adcontrol-in-xaml-and--net.md) und [AdControl in HTML5 und JavaScript](../monetize/adcontrol-in-html-5-and-javascript.md).
-   Wenn Ihre App Interstitialanzeigen anzeigt, übergeben Sie diese Werte an die [RequestAd](https://msdn.microsoft.com/library/mt313192.aspx)-Methode Ihres [InterstitialAd](https://msdn.microsoft.com/library/mt313189.aspx)-Objekts. Weitere Informationen finden Sie unter [Interstitialwerbungen](../monetize/interstitial-ads.md).
-   Wenn Ihre App native Anzeigen anzeigt, weisen Sie diese Werte die Parameter *applicationId* und *adUnitId* des [NativeAdsManager](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.nativeadsmanager.aspx)-Konstruktors zu. Weitere Informationen finden Sie unter [Native Anzeigen](../monetize/native-ads.md).

> [!IMPORTANT]
> Sie können jede Anzeigeneinheit in nur einer App verwenden. Wenn Sie eine Anzeigeneinheit in mehr als einer App verwenden, werden für die Ad-Einheit keine Anzeigen platziert.

> [!NOTE]
> Können mehrere Steuerelemente für Banner-, Interstitialwerbungen und native Anzeigen in einer einzelnen App verwenden. In diesem Fall wird empfohlen, dass Sie jedem Steuerelement eine andere Anzeigeneinheit zuweisen. Durch das Verwenden verschiedener Anzeigeeinheiten für jedes Steuerelement können Sie für jedes Steuerelement [die Einstellungen für die Anzeigenvermittlung konfigurieren](../publish/monetize-with-ads.md#mediation) und diskrete [Berichtsdaten](../publish/advertising-performance-report.md). Außerdem können unsere Dienste so die Werbung optimieren, die wir in Ihrer App anzeigen.

<span id="mediation" />
## <a name="ad-mediation"></a>Anzeigenvermittlung

Wenn Ihre App eine UWP-App für Windows10 ist, können Sie die Optionen in diesem Abschnitt verwenden, um die Anzeigenvermittlung für eine UWP-Anzeigeneinheit zu aktivieren, die mit einer Banner-, Interstitialwerbungen oder nativen Anzeige in Ihrer App. Mit der Anzeigenvermittlung können Sie Ihre Anzeigenumsätze maximieren und Werbefunktionen optimal nutzen, indem Sie Anzeigen aus mehreren Anzeigennetzwerken anzeigen, einschließlich Anzeigen aus anderen kostenpflichtigen Anzeigennetzwerken und Anzeigen ohne Umsatzgenerierung zu Werbekampagnen für Microsoft-Apps. Wir kümmern uns um die Vermittlung von Banneranzeigenanforderungen von den gewählten Anzeigennetzwerken.

Wenn Sie eine UWP-Anzeigeneinheit haben, die bereits mit einer Banner-, Interstitial oder nativen Anzeige in Ihrer App verbunden ist, erfordert das Aktivieren der Anzeigenvermittlung keine Codeänderungen in Ihrer App.

> [!NOTE]
> In diesem Abschnitt werden die Optionen für die **Anzeigenvermittlung** für UWP-App-Pakete beschrieben. Wenn Ihr App-Paket auf Windows 8.x oder Windows Phone 8.x ausgerichtet ist und **AdMediatorControl** aus dem [Microsoft Advertising-SDK für Windows und Windows Phone 8.x](http://aka.ms/store-8-sdk) verwendet, werden im Abschnitt **Anzeigenvermittlung** auf dem Dashboard andere Optionen angezeigt. Weitere Informationen zum Konfigurieren der Anzeigenvermittlungseinstellungen für ein Windows8.x- oder Windows Phone8.x-App-Paket, das **AdMediatorControl** verwendet, finden Sie [in diesem Artikel](https://msdn.microsoft.com/library/windows/apps/mt219689).

So konfigurieren Sie die Anzeigenvermittlung für eine UWP-Anzeigeneinheit in Ihrer App:

1. Wählen Sie im Dropdownfeld **Konfigurieren der Vermittlung** für das UWP-App-Paket aus, das die zu konfigurierenden Banner-, Interstitialwerbungen und native Anzeigeneinheiten enthält.

2. Wählen Sie aus der Dropdownliste **Art der Anzeigeneinheit** die Art der Anzeigeneinheit aus, die Sie konfigurieren möchten (**Banneranzeigen**, **Banner-Interstitialwerbungen**, **Video-Interstitialanzeigen** oder **native Anzeigen**).

3. Wählen Sie in der Dropdownliste **Anzeigeneinheit** den zu konfigurierenden Namen der UWP-Anzeigeneinheit aus.
    > [!NOTE]
    > Wenn Sie die Anzeigenvermittlung für eine UWP-Anzeigeneinheit aktivieren, müssen Sie keine Anzeigeneinheit von Drittanbieter-Anzeigennetzwerken erhalten. Unser Anzeigenvermittlungsdienst erstellt automatisch alle erforderlichen Drittanbieter-Anzeigeneinheiten.

4. Standardmäßig ist das Kontrollkästchen **Let Microsoft choose the best mediation settings for your app** aktiviert. Diese Option verwendet Machine Learning-Algorithmen, um automatisch die Anzeigenvermittlungseinstellungen für Ihre App auszuwählen, um Ihnen beim Optimieren der Anzeigenumsätze in den verschiedenen Märkten zu helfen, die Ihre App unterstützt. Es wird empfohlen, diese Option zu verwenden. Wenn Sie Ihre eigenen Anzeigenvermittlungseinstellungen auswählen möchten, deaktivieren Sie das Kontrollkästchen.
    > [!NOTE]
    > Die verbleibenden Schrittein diesem Abschnittgelten nur, wenn Sie dieses Kontrollkästchen deaktivieren und eigene Anzeigenvermittlungseinstellungen auswählen.

5. Wählen Sie in der Dropdownliste **Ziel** die Option **Basisplan**, um die Standardkonfiguration für Ihre Anzeigenvermittlungseinstellungen zu konfigurieren. Diese Standardkonfiguration wird auf alle Märkte angewendet, mit Ausnahme von Märkten, für die Sie marktspezifische Konfigurationen definieren.

6. Geben Sie dann das Verhältnis der Anzeigen an, die Sie auf dem Steuerelement von kostenpflichtigen Netzwerken (die Sie für Aufrufe bezahlen) und anderen Anzeigennetzwerken (die Sie nicht für Aufrufe bezahlen) anzeigen möchten. Geben Sie hierzu einen Wert zwischen 0 und 100 im Feld **Gewichtung** für **Paid ad networks** und **Weitere Anzeigennetzwerke** ein.  

7. Aktivieren Sie im Abschnitt **Paid ad networks** das Kontrollkästchen in der Spalte **Aktiv** für jedes kostenpflichtige Netzwerk, das Sie verwenden möchten, und sortieren Sie die Netzwerke dann mithilfe der Pfeile in der Spalte **Rang** nach Rang. (Dies gibt an,wie oft jedes Netzwerk von Ihrem Steuerelement verwendet werden soll.)

    Die folgenden kostenpflichtigen Netzwerke werden derzeit unterstützt. Beachten Sie, dass einige dieser Netzwerke [nicht in allen Märkten verfügbar](#network-markets) sind.

    -   **AOL und AppNexus**. Dies ist ein von Microsoft verwaltetes Anzeigennetzwerk, das Anzeigen über unsere Partnernetzwerke AOL und AppNexus bereitstellt. Dieses Netzwerk wird für **Banner-** und **Video-Interstitial**-Anzeigeneinheiten unterstützt.
        > [!NOTE]
        > **AOL und AppNexus** haben in der Liste **Paid ad networks** für **Banner**-Anzeigeneinheiten stets den Rang 1. Für diese Art von Anzeigen kann kein niedrigerer Rang festgelegt werden.

    -   **AppNexus (direkt)**: Wählen Sie diese Option, um Video-Interstitialanzeigen von [AppNexus](https://www.appnexus.com) anzuzeigen. Dieses Netzwerk wird für **Video-Interstitial-** und **native** Anzeigeneinheiten unterstützt.

    -   **Microsoft-Anzeigen für die App-Installation**. Wählen Sie diese Option, um Anzeigen für die App-Installation oder das Wiedereinschalten von Anzeigen in Apps anzuzeigen, die von anderen Entwicklern im Windows-Ökosystem erstellt wurden, die [Werbeanzeigenkampagnen für ihre Apps erstellen](create-an-ad-campaign-for-your-app.md). Dieses Netzwerk wird für **Banner**, **Banner-Interstitialwerbungen** und **native** -Anzeigeneinheiten unterstützt.

    -   **Smaato**: Wählen Sie diese Option zum Bereitstellen von Anzeigen von [Smaato](https://www.smaato.com/). Dieses Netzwerk wird für **Banner**-Anzeigeneinheiten unterstützt.

    -   **smartclip**: Wählen Sie diese Option zum Bereitstellen von Anzeigen von [smartclip](http://www.smartclip.com/). Dieses Netzwerk wird für **Video-Interstitial**-Anzeigeneinheiten unterstützt.

    -   **SpotX**: Wählen Sie diese Option zum Bereitstellen von Anzeigen von [SpotX](https://www.spotx.tv/). Dieses Netzwerk wird für **Video-Interstitial**-Anzeigeneinheiten unterstützt.

    -   **Taboola**: Wählen Sie diese Option zum Bereitstellen von Anzeigen von [Taboola](https://www.taboola.com/). Dieses Netzwerk wird für **Banner**-Anzeigeneinheiten unterstützt.

8. Wenn Sie eine **Banner** oder **Interstitialwerbung**-Anzeigeneinheit ausgewählt haben, sehen Sie außerdem einen Abschnitt namens **Weitere Anzeigennetzwerke **. Mit den Netzwerken in diesem Abschnitt erzielen Sie keine Einnahmen für Anzeigenaufrufe. Stattdessen zeigen diese Netzwerke Werbung aus Quellen wie Werbekampagnen für Apps an. 

    Aktivieren Sie im Abschnitt **Weitere Anzeigennetzwerke** das Kontrollkästchen in der Spalte **Aktiv** für jedes weitere Netzwerk, das Sie verwenden möchten, und sortieren Sie die Netzwerke dann mithilfe der Pfeile in der Spalte **Rang** nach Rang. (Dies gibt an,wie oft jedes Netzwerk von Ihrem Steuerelement verwendet werden soll.) Die folgenden weiteren Netzwerke werden derzeit unterstützt:

    -   **MicrosoftCommunity-Anzeigen**. Wenn Sie [eine Anzeigenkampagne für eine Ihrer Apps erstellen](create-an-ad-campaign-for-your-app.md) und diese Kampagne als [Kampagne für Community-Anzeigen](about-community-ads.md) konfigurieren, wählen Sie diese Optionen, um Anzeigen aus dieser Kampagne anzuzeigen. 

    -   **Microsoft-Eigenwerbung**. Wenn Sie [eine Anzeigenkampagne für eine Ihrer Apps erstellen](create-an-ad-campaign-for-your-app.md) und diese Kampagne als [Kampagne für Eigenwerbung](about-house-ads.md) konfigurieren, wählen Sie diese Optionen, um Anzeigen aus dieser Kampagne anzuzeigen.

9. Für jeden Markt, in dem Sie die Standardvermittlungskonfiguration außer Kraft setzen möchten, wählen Sie den Markt in der Dropdownliste **Ziel**, und aktualisieren Sie die Anzeigennetzwerkauswahl und den Rang.

10. Klicken Sie auf **Speichern**.

<span id="network-markets" />
### <a name="supported-markets-for-ad-networks"></a>Unterstützte Märkte für Anzeigennetzwerke

Die verfügbaren Anzeigennetzwerke schalten Anzeigen in allen [unterstützten Märkten](define-pricing-and-market-selection.md#windows-store-consumer-markets) für UWP-Apps mit den folgenden Ausnahmen.

|  Anzeigennetzwerk  |  Unterstützte Märkte  |
|--------------|---------------------|
| Smaato | Brasilien, Kanada, Frankreich, Deutschland, Italien, Japan, Spanien, Großbritannien, USA |
| smartclip | Österreich, Belgien, Dänemark, Finnland, Deutschland, Italien, Niederlande, Norwegen, Schweden, Schweiz  |


## <a name="microsoft-affiliate-ads"></a>Microsoft-Partneranzeigen

Aktivieren Sie das Kontrollkästchen in diesem Abschnitt, wenn Sie Microsoft-Partneranzeigen in Ihrer App anzeigen möchten. Wenn Sie dieses Kontrollkästchen aktivieren, werden für Ihre App Anzeigen für Produkte im Store bereitgestellt, u. a. Musik, Spiele, Filme, Apps, Hardware und Software, wenn keine Anzeigen von anderen Anzeigennetzwerken verfügbar sind. Wenn Kunden auf die Anzeigen klicken und innerhalb eines bestimmten Attributionsfensters Produkte im Store kaufen, verdienen Sie bei jedem Verkauf eine Provision.

Wenn Sie diese Auswahl ändern, müssen Sie Ihre App nicht neu veröffentlichen, damit die Änderungen wirksam werden. Weitere Informationen zu Microsoft-Partneranzeigen finden Sie unter [Informationen zu Partneranzeigen](about-affiliate-ads.md).

## <a name="coppa-compliance"></a>COPPA-Compliance

Um die Einhaltung der Richtlinien des Children's Online Privacy Protection Act („COPPA“) sicherzustellen, müssen Sie Microsoft benachrichtigen, wenn Ihre App an Kinder unter 13 Jahren gerichtet ist. Wenn unter Verwendung von Dev Center Microsoft mitteilen, dass Ihre App an Kinder unter 13 Jahren gerichtet ist, deaktiviert Microsoft die verhaltensorientierten Werbedienste bei der Übermittlung von Werbung an Ihre App. Wenn Ihre App an Kinder unter 13 Jahren gerichtet ist, ergeben sich aus COPPA bestimmte Verpflichtungen für Sie.

Weitere Informationen über Ihre Verpflichtungen im Rahmen von COPPA finden Sie [auf dieser Seite](http://go.microsoft.com/fwlink/p/?linkid=536558).
