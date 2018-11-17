---
author: Xansky
Description: Offer consumable in-app products&\#8212;items that can be purchased, used, and purchased again&\#8212;through the Store commerce platform to provide your customers with a purchase experience that is both robust and reliable.
title: Aktivieren der Möglichkeit, konsumierbare In-App-Produkte zu kaufen
ms.assetid: F79EE369-ACFC-4156-AF6A-72D1C7D3BDA4
keywords: UWP, konsumierbar, Add-Ons, In-App-Käufe, IAPs Windows.ApplicationModel.Store
ms.author: mhopkins
ms.date: 08/25/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: c41801362a03bb8d1d5e06b3ada876014237b1f7
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7158710"
---
# <a name="enable-consumable-in-app-product-purchases"></a>Unterstützen von Käufen konsumierbarer In-App-Produkte

Sie können In-App-Käufe von konsumierbaren Produkten – Artikel, die gekauft, verwendet und wieder gekauft werden können – über die Store-Handelsplattform anbieten, um den Kunden beim Kauf Stabilität und Zuverlässigkeit zu bieten. Dies ist besonders nützlich für Dinge wie spielinterne Währungen (Gold, Münzen usw.), die gekauft und dann zum Erwerben bestimmter Power-Ups verwendet werden können.

> [!IMPORTANT]
> Dieser Artikel beschreibt, wie Sie Mitglieder des [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.aspx)-Namespace verwenden, um konsumierbare In-App-Produktkäufe zu ermöglichen. Dieser Namespace wird nicht mehr mit neuen Funktionen aktualisiert, daher wird empfohlen, dass Sie stattdessen den [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx) Namespace verwenden. Der **Windows.Services.Store** -Namespace unterstützt die neuesten Add-on-Typen, z. B. Store verwalteten Endverbraucher-Add-Ons und Abonnements, und wurde entwickelt, um die Kompatibilität mit künftigen Arten von Produkten und Features von Partner Center und dem Store unterstützt werden. Der **Windows.Services.Store**-Namespace wurde in Windows10, Version 1607, eingeführt und kann nur in Projekten für die **Windows10 Anniversary Edition (10.0; Build 14393)** oder einer neueren Version in Visual Studio verwendet werden. Weitere Informationen zu konsumierbaren In-App-Produkten mithilfe des **Windows.Services.Store**-Namespace finden Sie in [diesem Artikel](enable-consumable-add-on-purchases.md).

## <a name="prerequisites"></a>Voraussetzungen

-   In diesem Thema erfahren Sie, wie In-App-Produktkäufe von Consumables erfüllt und gemeldet werden. Wenn Sie mit In-App-Produkten noch nicht vertraut sind, lesen Sie [Aktivieren von In-App-Produktkäufen](enable-in-app-product-purchases.md). Dort finden Sie Lizenzinformationen und eine Anleitung zur richtigen Eintragung Ihrer In-App-Produkte im Store.
-   Wenn Sie zum ersten Mal Code für neue In-App-Produkte schreiben und testen, müssen Sie anstelle des [CurrentAppSimulator](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store.CurrentAppSimulator)-Objekts das [CurrentApp](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store.CurrentApp)-Objekt verwenden. Auf diese Weise können Sie überprüfen, ob die Lizenzlogik simulierte Aufrufe an den Lizenzserver und nicht an den Liveserver verwendet. Dazu müssen Sie die Datei mit dem Namen „WindowsStoreProxy.xml“ in %userprofile%\\AppData\\local\\packages\\&lt;Paketname&gt;\\LocalState\\Microsoft\\Windows Store\\ApiData anpassen. Diese Datei wird vom Simulator in Microsoft Visual Studio erstellt, wenn Sie Ihre App zum ersten Mal ausführen. Sie können jedoch auch eine benutzerdefinierte Version dieser Datei zur Laufzeit laden. Weitere Informationen finden Sie unter [Verwenden der Datei „WindowsStoreProxy.xml“ mit CurrentAppSimulator](in-app-purchases-and-trials-using-the-windows-applicationmodel-store-namespace.md#proxy).
-   In diesem Thema wird auch auf Codebeispiele verwiesen, die im [Store-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/win10-1507/Samples/Store) zu finden sind. Dieses Beispiel bietet eine hervorragende Möglichkeit, die verschiedenen Monetarisierungsoptionen zu testen, die für Universelle Windows-Plattform (UWP)-Apps verfügbar sind.

## <a name="step-1-making-the-purchase-request"></a>Schritt 1: Durchführen der Kaufanforderung

Die erste Kaufanforderung wird wie bei jedem Kauf über den Store mit [RequestProductPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.requestproductpurchaseasync) durchgeführt. Der Unterschied bei konsumierbaren In-App-Produkten besteht darin, dass ein Kunde nach einem erfolgreichen Kauf das gleiche Produkt erst dann erneut kaufen kann, wenn die App den Store benachrichtigt hat, dass der vorige Kauf des Produkts erfolgreich erfüllt wurde. Ihre App ist dafür verantwortlich, gekaufte Consumables zu erfüllen und den Store über die Erfüllung in Kenntnis zu setzen.

Im nächsten Beispiel wird eine In-App-Kaufanforderung für ein Consumable gezeigt. Sie sehen Codekommentare, die angeben, wann Ihre App den Kauf des konsumierbaren In-App-Produkts lokal erfüllen sollte, und zwar für zwei verschiedene Szenarien – eine erfolgreiche Kaufanforderung und eine nicht erfolgreiche Kaufanforderung aufgrund eines nicht erfüllten Kaufs desselben Produkts.

> [!div class="tabbedCodeSnippets"]
[!code-cs[EnableConsumablePurchases](./code/InAppPurchasesAndLicenses/cs/EnableConsumablePurchases.cs#MakePurchaseRequest)]

## <a name="step-2-tracking-local-fulfillment-of-the-consumable"></a>Schritt 2: Verfolgen der lokalen Kauferfüllung des Verbrauchsartikels

Wenn Sie dem Kunden Zugriff auf das konsumierbare In-App-Produkt gewähren, müssen Sie dokumentieren, für welches Produkt der Kauf erfüllt wird (*productId*) und mit welcher Transaktion diese Erfüllung verbunden ist (*transactionId*).

> [!IMPORTANT]
> Ihre App ist verantwortlich dafür, dass der Store ordnungsgemäß von der Erfüllung in Kenntnis gesetzt wird. Dieser Schritt ist die Grundlage dafür, dass der Kauf von den Kunden als fair und zuverlässig wahrgenommen wird.

Im folgenden Beispiel wird die Verwendung von [PurchaseResults](https://msdn.microsoft.com/library/windows/apps/dn263392)-Eigenschaften aus dem [RequestProductPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.requestproductpurchaseasync)-Aufruf im vorangehenden Schritt zum Identifizieren des Produktkaufs gezeigt, der erfüllt werden muss. Es wird eine Sammlung verwendet, um die Produktinformationen an einem Ort zu speichern, auf den später verwiesen werden kann, um zu bestätigen, dass die lokale Erfüllung erfolgreich war.

> [!div class="tabbedCodeSnippets"]
[!code-cs[EnableConsumablePurchases](./code/InAppPurchasesAndLicenses/cs/EnableConsumablePurchases.cs#GrantFeatureLocally)]

Im folgenden Beispiel wird die Verwendung des Arrays aus dem vorhergehenden Beispiel gezeigt, um auf Produkt-ID/Transaktions-ID-Paare zuzugreifen, die später beim Melden der Erfüllung an den Store verwendet werden.

> [!IMPORTANT]
> Ganz gleich, welche Methode Ihre App verwendet, um die Erfüllung nachzuverfolgen und zu bestätigen – die App muss gebührende Sorgfalt demonstrieren, um sicherzustellen, dass Ihren Kunden keine Produkte in Rechnung gestellt werden, die sie nicht erhalten haben.

> [!div class="tabbedCodeSnippets"]
[!code-cs[EnableConsumablePurchases](./code/InAppPurchasesAndLicenses/cs/EnableConsumablePurchases.cs#IsLocallyFulfilled)]

## <a name="step-3-reporting-product-fulfillment-to-the-store"></a>Schritt 3: Melden der Produkterfüllung an den Store

Nachdem die lokale Erfüllung abgeschlossen wurde, muss Ihre App einen [ReportConsumableFulfillmentAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.reportconsumablefulfillmentasync)-Aufruf ausführen, der die *productId* und die Transaktion des Produktkaufs enthält.

> [!IMPORTANT]
> Wenn erfüllte Käufe konsumierbarer In-App-Produkte nicht an den Store gemeldet werden, kann der Benutzer das Produkt erst dann erneut kaufen, wenn die Erfüllung des vorangehenden Kaufs gemeldet wird.

> [!div class="tabbedCodeSnippets"]
[!code-cs[EnableConsumablePurchases](./code/InAppPurchasesAndLicenses/cs/EnableConsumablePurchases.cs#ReportFulfillment)]

## <a name="step-4-identifying-unfulfilled-purchases"></a>Schritt 4: Identifizieren nicht erfüllter Einkäufe

Ihre App kann jederzeit mithilfe der [GetUnfulfilledConsumablesAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.getunfulfilledconsumablesasync)-Methode eine Überprüfung auf nicht erfüllte Käufe konsumierbarer In-App-Produkte durchführen. Diese Methode sollte regelmäßig aufgerufen werden, um nicht erfüllte Käufe konsumierbarer Produkte zu ermitteln, die aufgrund unerwarteter Ereignisse in der App aufgetreten sind, beispielsweise Unterbrechungen der Netzwerkverbindung oder Beenden der App.

Im folgenden Beispiel wird gezeigt, auf welche Weise [GetUnfulfilledConsumablesAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.getunfulfilledconsumablesasync) verwendet werden kann, um nicht erfüllte Käufe konsumierbarer Produkte aufzuzählen, und wie Ihre App diese Liste iterieren kann, um die lokale Erfüllung abzuschließen.

> [!div class="tabbedCodeSnippets"]
[!code-cs[EnableConsumablePurchases](./code/InAppPurchasesAndLicenses/cs/EnableConsumablePurchases.cs#GetUnfulfilledConsumables)]

## <a name="related-topics"></a>Verwandte Themen

* [Unterstützen des Kaufs von In-App-Produkten](enable-in-app-product-purchases.md)
* [Store-Beispiel (zeigt Testversionen und In-App-Käufe)](https://github.com/Microsoft/Windows-universal-samples/tree/win10-1507/Samples/Store)
* [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/br225197)
 

 
