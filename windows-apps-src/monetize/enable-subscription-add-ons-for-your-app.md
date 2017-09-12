---
author: mcleanbyron
description: Erfahren Sie, wie Sie den Windows.Services.Store-Namespace verwenden, um mit abonnementbasierte Add-Ons zu implementieren.
title: "Aktivieren von Abonnements für Add-Ons für Ihre App"
keywords: "Windows10, UWP, Abonnements, Lizenzen, Apps, Add-Ons, In-App-Einkäufe, IAPs, Windows.Services.Store"
ms.author: mcleans
ms.date: 08/01/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: 16e2e8d160ad2236220dc6f19f578bbaa82c9dc0
ms.sourcegitcommit: de6bc8acec2cd5ebc36bb21b2ce1a9980c3e78b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="enable-subscription-add-ons-for-your-app"></a>Aktivieren von Abonnements für Add-Ons für Ihre App

> [!IMPORTANT]
> Die Fähigkeit zum Erstellen von Abonnement-Add-Ons ist derzeit nur für eine Gruppe von Entwicklerkonten verfügbar, die am frühen Adoption-Programm teilnehmen. Wir stellen Abonnement-Add-Ons für alle Entwicklerkonten in Zukunft zur Verfügung und wir stellen Ihnen diese vorläufige Dokumentation jetzt zur Verfügung, um Entwicklern eine Vorschau dieser Funktion zu ermöglichen.

Wenn Ihre UWP-App für Windows10, Version 1607, oder höher vorgesehen ist, können Sie In-App-Käufen von *abonnementbasierte* Add-Ons für Ihre Kunden anbieten. Sie können Abonnements nutzen, um digitale Produkte in Ihrer App zu verkaufen (z.B. App-Features oder digitale Inhalte), die mit einer automatisierten wiederkehrenden Abrechnung arbeiten.

## <a name="feature-highlights"></a>Wichtigste Features

Abonnement-Add-Ons für UWP-Apps unterstützen die folgenden Features:

* Sie können Abonnementszeiträume von 1Monat, 3Monaten, 6Monaten, 1 Jahr bzw. 2Jahren auswählen. Einige Apps können auch einen Abonnementzeitraum von 6 Stunden für Testzwecke nutzen.
* Sie können die kostenlose Testversionzeiträume von 1 Woche oder 1Monat zu Ihrem Abonnement hinzufügen.
* Das Windows SDK [bietet APIs](#code-examples), die Sie in Ihrer App zum Abrufen von Informationen zu verfügbaren Abonnement-Add-Ons für die App und zum aktivieren des Kaufs eines Abonnement-Add-Ons nutzen können. Wir bieten außerdem REST-APIs, die Sie aus Ihren Diensten zum [Verwalten von Abonnements für einen Benutzer](#manage-subscriptions) aufrufen können.
* Sie können Analyseberichte anzeigen, die die Anzahl der Abonnement-Käufe, aktiven Abonnenten und stornierte Abonnements in einem bestimmten Zeitraum anzeigen.
* Die Kunden können ihr Abonnement auf der Seite [http://account.microsoft.com/services](http://account.microsoft.com/services) für ihr Microsoft-Konto verwalten. Die Kunden können diese Seite verwenden, um alle Abonnements anzeigen, die sie erworben haben, ein Abonnement zu kündigen und die Zahlungsmethode für ihr Abonnement zu ändern.

> [!NOTE]
> Um den Kauf von Abonnement-Add-Ons in Ihrer App zu aktivieren, muss Ihre App für Windows10, Version 1607, oder höher entwickelt sein. Sie muss die APIs im **Windows.Services.Store**-Namespace statt im **Windows.ApplicationModel.Store**-Namespace verwenden, um die In-App Käufe zu implementieren. Weitere Informationen zu den Unterschieden zwischen diesen Namespaces finden Sie unter [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md).

## <a name="steps-to-enable-a-subscription-add-on-for-your-app"></a>Schritte zum Aktivieren von Abonnements für Add-Ons für Ihre App

Gehen Sie folgendermaßen vor, um den Kauf von Abonnement-Add-Ons in Ihrer App zu aktivieren.

1. [Erstellen Sie eine Add-On-Übermittlung](../publish/add-on-submissions.md) für Ihr Abonnement im Dev Center-Dashboard und veröffentlichen Sie die Übermittlung. Beachten Sie im Rahmen des Add-On-Übermittlungsprozesses die folgenden Eigenschaften:

  * [Produkttyp](../publish/set-your-add-on-product-id.md#product-type): Stellen Sie sicher, dass Sie **Abonnement** ausgewählt haben.

  * [Abonnementzeitraum](../publish/enter-add-on-properties.md#subscription-period): Wählen Sie den wiederholte Abrechnungszeitraum für Ihr Abonnement aus. Der können den Abonnementszeitraum nach der Veröffentlichung des Add-Ons nicht mehr ändern.

    Jedes Abonnement-Add-On unterstützt einen einzelnen Abonnementzeitraum und einen Testzeitraum. Sie müssen ein anderes Abonnement-Add-On für jedes Abonnement erstellen, das Sie in Ihrer App anbieten möchten. Wenn Sie z. B. ein monatliches Abonnement ohne Teste, ein monatliches Abonnement mit einmonatigem Test, ein Jahresabonnement ohne Test und ein Jahresabonnement mit einem einmonatigen Test anbieten möchten, benötigen Sie vier Abonnement-Add-Ons.
        > [!NOTE]
        > If you are in the process of implementing the in-app purchase experience for your subscription, we recommend that you create a test add-on with the **For testing only – 6 hours** subscription period to help you test the experience. You can choose this test period only if you select one of the **Hidden in the Store** [visibility options](../publish/set-add-on-pricing-and-availability.md#visibility) for your test add-on.

  * [Testzeitraum](../publish/enter-add-on-properties.md#free-trial): Wählen Sie einen 1 Woche oder 1Monat Testzeitraum für Ihr Abonnement, damit Benutzer Ihre Abonnement testen können, bevor sie dieses kaufen. Der können den Abonnementszeitraum und den Testzeitraum nach der Veröffentlichung des Abonnement-Add-Ons nicht mehr ändern.

    Um eine kostenlose Testversion Ihres Abonnements zu erwerben, muss der Benutzer Ihr Abonnement über den Standard-In-App-Einkauf-(inkl. gültiger Zahlungsmethode) erwerben. Während der Testphase wird nichts in Rechnung gestellt. Am Ende des Testzeitraums wandelt sich das Abonnement automatisch in ein vollständiges Abonnement um und die Zahlungsmittel des Benutzers werden für den ersten kostenpflichtigen Zeitraum des Abonnements belastet. Wenn der Benutzer das Abonnement während des Testzeitraums abbricht, bleibt das Abonnement bis zum Ende des Testzeitraums aktiv.
        > [!NOTE]
        > Some trial durations are not available for all subscription periods.

  * [Sichtbarkeit](../publish/set-add-on-pricing-and-availability.md#visibility): Wenn Sie ein Test-Add-On erstellen, das Sie nur verwendet, um die In-App-Einkaufserfahrung für Ihr Abonnement zu testen, empfehlen wir, eine der **Im Store ausgeblendet**-Optionen zu verwenden. Andernfalls können Sie die beste Sichtbarkeitsoption für Ihr Szenario auswählen.

  * [Preise](../publish/set-add-on-pricing-and-availability.md?#pricing): Wählen Sie in diesem Abschnitt den Preis für Ihr Abonnement aus. Den Preis des Abonnements kann nicht heraufgestuft werden, nachdem Sie das Add-On veröffentlicht haben (allerdings können Sie später den Preis reduzieren).
      > [!IMPORTANT]
      > Standardmäßig wird der Preis bei der Erstellung des Add-Ons auf **Kostenlos** festgelegt. Da Sie den Preis nach Abschluss der Add-On-Übermittlung nicht anheben können, stellen Sie sicher, dass Sie hier den gewünschten Preis für Ihr Abonnement auswählen.

2. Verwenden Sie in Ihrer App die APIs im [**Windows.Services.Store**](https://docs.microsoft.com/uwp/api/windows.services.store)-Namespace, um zu überprüfen, ob der aktuelle Benutzer bereits Ihr Abonnement-Add-On erworben hat, und um es als In-App-Kauf anzubieten. In den [Codebeispielen](#code-examples) in diesem Artikel erhalten Sie weitere Informationen.

3. Testen Sie die In-App-Kauf-Implementierung Ihres Abonnements in Ihrer App. Sie müssen die App aus dem Store auf Ihr Entwicklungsgerät herunterladen, um dessen Lizenz zum Testen zu verwenden. Weitere Informationen finden Sie unter [Anweisungen zum Testen](in-app-purchases-and-trials.md#testing) für In-App-Käufe.  
    > [!NOTE]
    > Wenn Ihre App Zugriff auf den **Nur für Tests – 6 Stunden**-Abonnementzeitraum hat, empfehlen wir, dass Sie ein Add-On Test mit diesem Zeitraum erstellen, um die Umgebung testen. Sie können diesen Testzeitraum nur dann wählen, wenn Sie eine der **Im Store ausgeblendet** [Sichtbarkeitsoptionen](../publish/set-add-on-pricing-and-availability.md#visibility) für Ihr Test-Add-On auswählen.

4. Erstellen und Veröffentlichen Sie eine App-Übermittlung, die das aktualisierte App-Paket inkl. des getesteten Codes enthält. Weitere Informationen finden Sie unter [App-Übermittlungen](../publish/app-submissions.md).

<span id="code-examples"/>
## <a name="code-examples"></a>Codebeispiele

Die Codebeispiele in diesem Abschnittzeigen, wie Sie die APIs im [**Windows.Services.Store**](https://docs.microsoft.com/uwp/api/windows.services.store)-Namespace zum Abrufen von Informationen zu Abonnement-Add-Ons für die aktuelle App nutzen und den Kauf eines Abonnement-Add-Ons im Namen des aktuellen Benutzers anfordern.

Für diese Beispiele gelten die folgenden Voraussetzungen:
* Ein Visual Studio-Projekt für eine App für die universelle Windows-Plattform (UWP), die für Windows10, Version1607 oder höher, geeignet ist.
* Sie haben eine [App-Übermittlung](https://msdn.microsoft.com/windows/uwp/publish/app-submissions) im Windows Dev Center-Dashboard erstellt. Diese App ist im Store verfügbar. Optional können Sie die App so konfigurieren, daher sie während der Tests im Store nicht auffindbar ist. Weitere Informationen finden Sie unter [Hinweise für Tests](in-app-purchases-and-trials.md#testing).
* Sie haben [ein Abonnement-Add-On für die App](../publish/add-on-submissions.md) im Dev Center-Dashboard erstellt.

Der Code in diesen Beispielen geht von Folgendem aus:
* Die Ausführung des Codes erfolgt im Kontext einer [**Seite**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.aspx), die einen [**ProgressRing**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.progressring.aspx) mit dem Namen ```workingProgressRing``` und einen [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) mit dem Namen ```textBlock``` enthält. Diese Objekte werden verwendet, um anzugeben, dass ein asynchroner Vorgang ausgeführt wird, bzw. um Ausgabemeldungen anzuzeigen.
* Die Codedatei enthält eine **using**-Anweisung für den **Windows.Services.Store**-Namespace.
* Die App ist eine Einzelbenutzer-App, die nur im Kontext des Benutzers ausgeführt wird, der die App gestartet hat. Weitere Informationen finden Sie unter [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md#api_intro).

> [!NOTE]
> Wenn Sie über eine Desktopanwendung verfügen, die die [Desktop-Brücke](https://developer.microsoft.com/windows/bridges/desktop) verwendet, müssen Sie möglicherweise zusätzlichen, in diesen Beispielen nicht aufgeführten Code hinzufügen, um das [**StoreContext**](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.aspx)-Objekt zu konfigurieren. Weitere Informationen finden Sie unter [Verwenden der StoreContext-Klasse in einer Desktopanwendung, die die Desktop-Brücke verwendet](in-app-purchases-and-trials.md#desktop).

### <a name="get-info-about-subscription-add-ons-for-the-current-app"></a>Abrufen von Informationen zu Abonnement-Add-Ons für die aktuelle App

In diesem Codebeispiel wird veranschaulicht, wie Sie Informationen für Abonnement-Add-Ons abrufen, die in Ihrer App verfügbar sind. Um diese Informationen zu erhalten, verwenden Sie zunächst die [**GetAssociatedStoreProductsAsync**](https://docs.microsoft.com/uwp/api/Windows.Services.Store.StoreContext#Windows_Services_Store_StoreContext_GetAssociatedStoreProductsAsync_)-Methode, um eine Sammlung der [**StoreProduct**](https://docs.microsoft.com/uwp/api/Windows.Services.Store.StoreProduct)-Objekte für alle in der App verfügbaren Add-Ons abzurufen. Rufen Sie dann die [**StoreSku**](https://docs.microsoft.com/uwp/api/windows.services.store.storesku) für jedes Produkt und ab und verwenden Sie die Eigenschaften [**IsSubscription**](https://docs.microsoft.com/uwp/api/windows.services.store.storesku#Windows_Services_Store_StoreSku_IsSubscription_) und [**SubscriptionInfo**](https://docs.microsoft.com/uwp/api/windows.services.store.storesku#Windows_Services_Store_StoreSku_SubscriptionInfo_), um auf die Abonnementinformationen zuzugreifen.

> [!div class="tabbedCodeSnippets"]
[!code-cs[Abonnements](./code/InAppPurchasesAndLicenses_RS1/cs/GetSubscriptionAddOnsPage.xaml.cs#GetSubscriptions)]

### <a name="purchase-a-subscription-add-on"></a>Ein Abonnement-Add-On erwerben

In diesem Beispiel wird die Verwendung der [**RequestPurchaseAsync**](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_RequestPurchaseAsync_)-Methode der [**StoreContext**](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct)-Klasse veranschaulicht, um ein Abonnement-Add-On zu erwerben. In diesem Beispiel wird davon ausgegangen, dass Sie die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Abonnement-Add-Ons, das Sie erwerben möchten, bereits kennen.

> [!div class="tabbedCodeSnippets"]
[!code-cs[Abonnements](./code/InAppPurchasesAndLicenses_RS1/cs/PurchaseSubscriptionAddOnPage.xaml.cs#PurchaseSubscription)]

<span id="manage-subscriptions" />
## <a name="manage-subscriptions-from-your-services"></a>Verwalten von Abonnements über Ihre Dienste

Nachdem die aktualisierte App im Store verfügbar ist und die Kunden Ihr Abonnement-Add-On erwerben können, gibt es möglicherweise Szenarien, in denen Sie das Abonnement für einen Kunden verwalten müssen. Wir bieten REST-APIs, die Sie aus Ihren Diensten zum Ausführen der folgenden Abonnement Verwaltungsaufgaben aufrufen können:

* [Rufen Sie die Abonnements ab, für die ein Benutzer berechtigt ist](get-subscriptions-for-a-user.md). Wenn Ihr Abonnement Teil eines plattformübergreifende Dienstes ist, können Sie diese API nutzen, um zu bestimmen, ob der angegebene Benutzer eine Berechtigung für Ihr Abonnement hat, und den Status ihrer Abonnements im Kontext Ihrer UWP-App abrufen. Diese Informationen können dann zum Aktualisieren des Status des Abonnements auf anderen von Ihrem Dienst unterstützten Plattformen nutzen.

* [Ändern des Abrechnungszustands eines Abonnements für einen bestimmten Benutzer](change-the-billing-state-of-a-subscription-for-a-user.md). Verwenden Sie diese API, um die automatische Verlängerung für ein Abonnement zu stornieren, zu verlängern oder zu deaktivieren.

<span id="cancellations" />
## <a name="cancellations"></a>Stornierungen

Die Kunden können die Seite [http://account.microsoft.com/services](http://account.microsoft.com/services) für ihr Microsoft-Konto verwenden, um alle Abonnements anzeigen, die sie erworben haben, ein Abonnement zu kündigen und die Zahlungsmethode für ihr Abonnement zu ändern. Wenn ein Kunde ein Abonnement auf dieser Seite abbricht, kann er für die Dauer des aktuellen Abrechnungszyklus weiterhin auf das Abonnement zugreifen. Er erhält keine Rückerstattung für einen Teil des aktuellen Abrechnungszeitraums. Am Ende des aktuellen Abrechnungszeitraums wird das Abonnement deaktiviert.

Sie können ein Abonnement auch im Auftrag eines Benutzers mithilfe unserer REST-API stornieren, um [Abrechnungszustand eines Abonnements für einen bestimmten Benutzer zu ändern](change-the-billing-state-of-a-subscription-for-a-user.md).

## <a name="unsupported-scenarios"></a>Nicht unterstützte Szenarien

Die folgenden Szenarien werden für die Abonnement-Add-Ons derzeit nicht unterstützt.

* Das Verkaufen von Abonnements direkt an Kunden über den Store wird zu diesem Zeitpunkt nicht unterstützt. Abonnements sind für In-App-Käufe von digitalen Produkte verfügbar.
* Die Kunden können die Abonnementszeiträumen auf der Seite [http://account.microsoft.com/services](http://account.microsoft.com/services) für ihr Microsoft-Konto nicht wechseln. Um zu einem anderen Abonnementszeitraum zu wechseln, müssen die Kunden das aktuelle Abonnement kündigen und ein Abonnement mit einem anderen Abonnementzeitraum in Ihrer App erwerben.
* Das Wechseln von Ebenen wird aktuell nicht für Abonnement-Add-Ons unterstützt (z.B., wenn ein Kunde aus einem einfachen Abonnement in ein Premium-Abonnement mit mehr Features wechseln will).
* [Verkäufe](../publish/put-apps-and-add-ons-on-sale.md) und [Werbecodes](../publish/generate-promotional-codes.md) für die Abonnement-Add-Ons werden derzeit nicht unterstützt.


## <a name="related-topics"></a>Verwandte Themen

* [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md)
* [Abrufen von Produktinformationen zu Apps und Add-Ons](get-product-info-for-apps-and-add-ons.md)
