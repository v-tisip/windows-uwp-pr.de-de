---
author: mcleanbyron
ms.assetid: 9F0A59A1-FAD7-4AD5-B78B-C1280F215D23
description: "Verwenden Sie die Windows Store-API für gezielte Angebote, um die gezielten Angebote in Anspruch zu nehmen, die für eine App verfügbar sind."
title: Verwalten von gezielten Angeboten mithilfe von Store-Diensten
ms.author: mcleans
ms.date: 05/11/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Store-Dienste, Windows Store-API für gezielte Angebote, gezielte Angebote"
ms.openlocfilehash: 684c37d4439f415ad607b7f3e6a166966cc9f835
ms.sourcegitcommit: eaacc472317eef343b764d17e57ef24389dd1cc3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2017
---
# <a name="manage-targeted-offers-using-store-services"></a>Verwalten von gezielten Angeboten mithilfe von Store-Diensten

Wenn Sie auf der Seite **Interaktion > Zielgerichtete Angebote** zu Ihrer App im Windows Dev Center-Dashboard ein *gezieltes Angebot* erstellen, verwenden Sie die *Windows Store-API für gezielte Angebote* in Ihrem App-Code, um die In-App-Umgebung für das gezielte Angebot zu implementieren. Weitere Informationen zu gezielten Angeboten und Anleitungen zu deren Erstellung im Dashboard finden Sie unter [Verwenden Sie gezielte Angebote, um Interaktionen und Abschlüsse zu maximieren.](../publish/use-targeted-offers-to-maximize-engagement-and-conversions.md).

Die API für gezielte Angebote ist eine REST-API, die Sie zum Ausführen dieser Aufgaben verwenden können:

* Rufen Sie die gezielten Angebote ab, die für den aktuellen Benutzer verfügbar sind– basierend darauf, ob der Benutzer zum Kundensegment für das gezielte Angebot gehört.
* Wenn der Benutzer das gezielte Angebot erwirbt, können Sie einen entsprechenden Anspruch an den Store übermitteln, um Bonuspunkte erhalten zu können, die mit dem gezielten Angebot verknüpft sind. Dies ist nur erforderlich, wenn das gezielte Angebot mit einer von Microsoft gesponserten Werbung verknüpft ist, bei der Entwickler für jede erfolgreiche Konvertierung einen Bonus erhalten.

Gehen Sie folgendermaßen vor, um diese API in Ihrem App-Code zu verwenden:

1.  [Rufen Sie ein Microsoft-Kontotoken](#obtain-a-microsoft-account-token) für den aktuell angemeldeten Benutzer Ihrer App ab.
2.  [Rufen Sie die gezielten Angebote für den aktuellen Benutzer ab](#get-targeted-offers).
3.  [Kaufen Sie das Add-On, das mit einem gezielten Angebot verknüpft ist](#purchase-add-on).
3.  [Nehmen Sie ein gezieltes Angebot in Anspruch](#claim-targeted-offer) (wenn das gezielte Angebot mit einer von Microsoft gesponserten Werbung verknüpft ist, bei der Entwickler für jede erfolgreiche Konvertierung einen Bonus erhalten).

> [!NOTE]
> Die Option zur Verknüpfung eines gezielten Angebots mit einer von Microsoft gesponserten Werbung und die anschließende Übermittlung ist derzeit nicht für alle Entwicklerkonten verfügbar.

Ein vollständiges Codebeispiel, das alle diese Schritteveranschaulicht, finden Sie unter der [Codebeispiel](#code-example) am Ende dieses Artikels. Die folgenden Abschnitte enthalten weitere Details zu den einzelnen Schritten.

<span id="obtain-a-microsoft-account-token" />
## <a name="get-a-microsoft-account-token-for-the-current-user"></a>Abrufen eines Microsoft-Kontotokens für den aktuellen Benutzer

Rufen Sie in Ihrem App-Code ein Microsoft-Konto (MSA)-Token für den aktuell angemeldeten Benutzer ab. Sie müssen dieses Token im ```Authorization```-Anforderungsheader für jede Methode in der Windows Store-API für gezielte Angebote übergeben. Dieses Token wird vom Store verwendet, um die gezielten Angebote abzurufen, die für den aktuellen Benutzer verfügbar sind.

Um das MSA-Token abzurufen, verwenden Sie die [WebAuthenticationCoreManager](https://docs.microsoft.com/uwp/api/windows.security.authentication.web.core.webauthenticationcoremanager)-Klasse, um ein Token unter Angabe des Bereichs anzufordern ```devcenter_implicit.basic,wl.basic```. Das folgende Beispiel veranschaulicht die Vorgehensweise. In diesem Beispiel wird ein Auszug aus dem [vollständige Beispiel](#code-example) verwendet. Es erfordert **using**-Anweisungen, die im vollständigen Beispiel bereitgestellt werden.

[!code-cs[TargetedOffers](./code/StoreServicesExamples_TargetedOffers/cs/TargetedOffers.cs#GetMSAToken)]

Weitere Informationen zum Abrufen von MSA-Token finden Sie unter [Web Account Manager](../security/web-account-manager.md).

<span id="get-targeted-offers" />
## <a name="get-the-targeted-offers-for-the-current-user"></a>Abrufen der gezielten Angebote für den aktuellen Benutzer

Rufen Sie nach Erhalt des MSA-Tokens für den aktuellen Benutzer die GET-Methode zum ```https://manage.devcenter.microsoft.com/v2.0/my/storeoffers/user```-URI auf, um die für den aktuellen Benutzer verfügbaren Angebote abzurufen. Weitere Informationen zu dieser REST-Methode finden Sie unter [Abrufen gezielter Angebote](get-targeted-offers.md).

Bei dieser Methode wird ein Array mit Produkt-IDs für die Add-Ons zurückgegeben, die den gezielten Angeboten zugeordnet sind, die für den aktuellen Benutzer verfügbar sind. Mit diesen Informationen können Sie ein oder mehrere gezielte Angebote als In-App-Einkauf für den Benutzer erstellen. Bei dieser Methode wird außerdem eine Tracking-ID zur [Übermittlung eines Anspruchs](#claim-targeted-offer) an den Store zurückgegeben, damit Sie alle Boni erhalten können, die mit einem der gezielten Angebote verknüpft sind.

Im folgenden Beispiel wird veranschaulicht, wie Sie die entsprechenden Angebote für den aktuellen Benutzer erhalten. Dieses Beispiel ist ein Auszug aus dem [vollständige Beispiel](#code-example). Erfordert die [Json.NET](http://www.newtonsoft.com/json)-Bibliothek von Newtonsoft und zusätzliche Klassen und **using**-Anweisungen, die im vollständigen Beispiel bereitgestellt werden.

[!code-cs[TargetedOffers](./code/StoreServicesExamples_TargetedOffers/cs/TargetedOffers.cs#GetTargetedOffers)]

<span id="purchase-add-on" />
## <a name="purchase-the-add-on-that-is-associated-with-a-targeted-offer"></a>Kaufen des Add-Ons, das mit einem gezielten Angebot verknüpft ist

Bieten Sie als Nächstes dem Benutzer ein gezieltes Angebot zum Kauf an. Wenn der Benutzer dem Kauf des gezielten Angebots zustimmt, verwenden Sie eine der folgenden Methoden, um das mit dem gezielten Angebot verknüpfte Add-On programmgesteuert zu erwerben. Verwenden Sie die Produkt-ID-Werte, die Sie im vorherigen Schritt zu Identifizierung des Add-Ons abgerufen haben, das Sie kaufen möchten.

* Wenn Ihre App auf Windows10 ab Version1607 ausgerichtet ist, wird empfohlen, eine der **RequestPurchaseAsync**-Methoden im [Windows.Services.Store](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store)-Namespace zu verwenden. Weitere Informationen zur Verwendung dieser Methoden finden Sie unter [Unterstützen von In-App-Einkäufen von Apps und Add-Ons](enable-in-app-purchases-of-apps-and-add-ons.md).

* Wenn Ihre App auf eine frühere Version von Windows10 ausgerichtet ist, verwenden Sie die [RequestProductPurchaseAsync](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store.CurrentApp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)-Methode im [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.aspx)-Namespace, um das Add-On zu erwerben. Weitere Informationen zur Verwendung dieser Methode finden Sie unter [Unterstützen von In-App-Produktkäufen](enable-in-app-product-purchases.md).

Codebeispiel, die jede Option veranschaulicht, finden Sie unter der [Codebeispiel](#code-example) am Ende dieses Artikels.

> [!NOTE]
> Es gibt zwei verschiedene Namespaces für die Implementierung von In-App-Einkäufen in einer UWP-App: [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx) (eingeführt in Windows10, Version 1607) und [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.aspx) (in allen Versionen von Windows10 verfügbar). Weitere Informationen zu den Unterschieden zwischen diesen Namespaces finden Sie unter [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md).

<span id="claim-targeted-offer" />
## <a name="submit-a-claim-for-a-targeted-offer"></a>Übermitteln eines Anspruchs für ein gezieltes Angebot

Wenn der Benutzer ein gezieltes Angebot erwirbt, das mit einer von Microsoft gesponserten Werbung verknüpft ist, bei der Entwickler für jeden erfolgreichen Abschluss einen Bonus erhalten, müssen Sie einen Anspruch an den Store übermitteln, um Ihre Boni zu erhalten. Wenn Sie Ihren Anspruch übermitteln, müssen Sie einen Wert angeben, der den Kaufbeleg darstellt. Wie Sie diese Kaufbestätigung erhalten, hängt davon ab, ob Ihre App die APIs im **Windows.ApplicationModel.Store** Namespace oder im **Windows.Services.Store** Namespace verwendet, um das Add-On kaufen.

> [!NOTE]
> Die Option zur Verknüpfung eines gezielten Angebots mit einer von Microsoft gesponserten Werbung und die anschließende Übermittlung ist derzeit nicht für alle Entwicklerkonten verfügbar.

### <a name="apps-that-use-the-windowsapplicationmodelstore-namespace"></a>Apps, die den Windows.ApplicationModel.Store-Namespace verwenden

1. Wenn Sie das Add-On über die [RequestProductPurchaseAsync](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store.CurrentApp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)-Methode im **Windows.ApplicationModel.Store**-Namespace gekauft haben, achten Sie darauf, einen [Kaufbeleg](use-receipts-to-verify-product-purchases.md) abzurufen. Diesen Beleg finden Sie im [PurchaseResults.ReceiptXml](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.purchaseresults#Windows_ApplicationModel_Store_PurchaseResults_ReceiptXml_)-Objekt, das mittels der **RequestProductPurchaseAsync**-Methode zurückgegeben wird. Dieser Beleg stellt die Kaufbestätigung dar, die Sie im nächsten Schritt verwendet.

2. Senden Sie eine POST-Nachricht an den ```https://manage.devcenter.microsoft.com/v2.0/my/storeoffers/user```-URI, um einen Anspruch zur Konvertierung des gezielten Angebots zu übermitteln. Weitere Informationen zu dieser REST-Methode finden Sie unter [Inanspruchnahme eines gezielten Angebots](claim-a-targeted-offer.md). Der Anforderungstext übergeben Sie die folgenden Daten:

  * *storeOffer*-Feld: Übergeben Sie im Anforderungstext eines der JSON-Objekte, die Sie über die Methode zum [Abrufen gezielter Angebote](get-targeted-offers.md) erhalten haben (dieses Objekt sollte die Felder *offers* und *trackingId* enthalten).

  * *receipt*-Feld: Übergeben Sie die Beleg-Zeichenfolge, die Sie im vorherigen Schrittabgerufen haben (diese Option ist im **PurchaseResults.ReceiptXml**-Objekt verfügbar, das von der **RequestProductPurchaseAsync** Methode zurückgegeben wird).

Im folgende Beispiel wird veranschaulicht, wie Sie ein gezieltes Angebot mithilfe der APIs im **Windows.ApplicationModel.Store** Namespace erwerben und in und in Anspruch nehmen. Dieses Beispiel ist ein Auszug aus dem [vollständige Beispiel](#code-example). Erfordert die [Json.NET](http://www.newtonsoft.com/json)-Bibliothek von Newtonsoft und zusätzliche Klassen und **using**-Anweisungen, die im vollständigen Beispiel bereitgestellt werden.

[!code-cs[TargetedOffers](./code/StoreServicesExamples_TargetedOffers/cs/TargetedOffers.cs#ClaimOfferOnAnyVersionWindows10)]

### <a name="apps-that-use-the-windowsservicesstore-namespace"></a>Apps, die den Windows.Services.Store-Namespace verwenden

1. Nachdem Sie das Add-On über eine der **RequestPurchaseAsync**-Methoden im [Windows.Services.Store](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store)-Namespace verwendet haben, nutzen Sie die *order-ID* für den Erwerb des Add-Ons über die folgenden Schritte. Dieser Wert stellt die Kaufbestätigung dar.

  1. Rufen Sie die [GetUserCollectionAsync](https://docs.microsoft.com/uwp/api/Windows.Services.Store.StoreContext#Windows_Services_Store_StoreContext_GetUserCollectionAsync_Windows_Foundation_Collections_IIterable_System_String__) Methode auf, um die Sammlung der [StoreProduct](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storeproduct.aspx) Objekte zu erhalten, die die Add-Ons darstellen, die der Benutzer erworben hat.

  2. In dieser Sammlung rufen Sie das **StoreProduct**-Objekt ab, das das Add-On darstellt, die für das gezielte Angebot gekauft wurde.

  3. Rufen Sie den Wert der [ExtendedJsonData](https://docs.microsoft.com/uwp/api/Windows.Services.Store.StoreProduct#Windows_Services_Store_StoreProduct_ExtendedJsonData_)-Eigenschaft dieses **StoreProduct** Objekts ab. Diese Eigenschaft gibt eine JSON-formatierte Zeichenfolge zurück, die die vollständigen Store-Daten für das Add-On enthält.

  4. Analysieren Sie diese JSON-Zeichenfolge und rufen Sie den Wert des *Bestellnr* Felds in der Zeichenfolge ab.

2. Senden Sie eine POST-Nachricht an den ```https://manage.devcenter.microsoft.com/v2.0/my/storeoffers/user```-URI, um einen Anspruch zur Konvertierung des gezielten Angebots zu übermitteln. Weitere Informationen zu dieser REST-Methode finden Sie unter [Inanspruchnahme eines gezielten Angebots](claim-a-targeted-offer.md). Im Anforderungstext übergeben Sie die folgenden Objekte:

  * *storeOffer*-Feld: Übergeben Sie im Anforderungstext eines der JSON-Objekte, die Sie über die Methode zum [Abrufen gezielter Angebote](get-targeted-offers.md) erhalten haben (dieses Objekt sollte die Felder *offers* und *trackingId* enthalten).

  * *receipt* Feld: Übergeben den *orderId* Wert, den Sie im vorherigen Schrittabgerufen haben.

Im folgende Beispiel wird veranschaulicht, wie Sie ein gezieltes Angebot mithilfe der APIs im **Windows.Services.Store** Namespace erwerben und in und in Anspruch nehmen. Dieses Beispiel ist ein Auszug aus dem [vollständige Beispiel](#code-example). Erfordert die [Json.NET](http://www.newtonsoft.com/json)-Bibliothek von Newtonsoft und zusätzliche Klassen und **using**-Anweisungen, die im vollständigen Beispiel bereitgestellt werden.

[!code-cs[TargetedOffers](./code/StoreServicesExamples_TargetedOffers/cs/TargetedOffers.cs#ClaimOfferOnWindows1607AndLater)]

<span id="code-example" />
## <a name="complete-code-example"></a>Vollständiger Beispielcode

Das folgende Codebeispiel veranschaulicht die folgenden Aufgaben:

* Abrufen eines MSA-Tokens für den aktuellen Benutzer
* Abrufen aller gezielten Angebote für den aktuellen Benutzer mithilfe der Methode zum [Abrufen gezielter Angebote](get-targeted-offers.md)
* Kaufen Sie das Add-On, das mit einem gezielten Angebot verknüpft ist.
* Inanspruchnahme des gezielten Angebots mithilfe der Methode zur [Inanspruchnahme eines gezielten Angebots](claim-a-targeted-offer.md).

Dieses Beispiel erfordert die [Json.NET](http://www.newtonsoft.com/json)-Bibliothek von Newtonsoft. Im Beispiel wird diese Bibliothek verwendet, um Daten im JSON-Format zu serialisieren bzw. deserialisieren.

> [!NOTE]
> Es gibt zwei verschiedene Namespaces für die Implementierung von In-App-Einkäufen in einer UWP-App: [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx) (eingeführt in Windows10, Version 1607) und [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.aspx) (in allen Versionen von Windows10 verfügbar). Dieses Beispiel verwendet [versionsadaptiven Code](../debug-test-perf/version-adaptive-code.md), um beide Namespaces in derselben App zu verwenden, um ein Add-On zu kaufen und einen Anspruch für das gezielte Angebot zu senden. Um diesen Code zu verwenden, muss mit die Ziel-Betriebssystemversion des Projekts **Windows 10 Anniversary Edition (10.0; Build 14394)** oder höher sein, auch wenn die minimale Betriebssystemversion eine frühere Version sein kann (falls Sie Ihre App auch unter älteren Versionen von Windows 10 ausführen möchten). Weitere Informationen zu den Unterschieden zwischen diesen Namespaces finden Sie unter [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md).

[!code-cs[TargetedOffers](./code/StoreServicesExamples_TargetedOffers/cs/TargetedOffers.cs#GetTargetedOffersSample)]

## <a name="related-topics"></a>Verwandte Themen

* [Verwenden Sie zielgerichtete Angebote, um Interaktionen und Abschlüsse zu maximieren.](../publish/use-targeted-offers-to-maximize-engagement-and-conversions.md)
* [Abrufen gezielter Angebote](get-targeted-offers.md)
* [Inanspruchnahme eines gezielten Angebots](claim-a-targeted-offer.md)
