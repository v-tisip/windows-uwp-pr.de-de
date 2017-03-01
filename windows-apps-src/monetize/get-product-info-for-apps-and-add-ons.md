---
author: mcleanbyron
ms.assetid: 89178FD9-850B-462F-9016-1AD86D1F6F7F
description: "Erfahren Sie, wie Sie den Windows.Services.Store-Namespace verwenden, um Store-bezogene Produktinformationen für die aktuelle App oder eines ihrer Add-Ons abzurufen."
title: Abrufen von Produktinformationen zu Apps und deren Add-Ons
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, In-App-Einkäufe, IAPs, Add-Ons, Windows.Services.Store"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 7e486c451174cd24429dc35cda07d22fe2b28745
ms.lasthandoff: 02/07/2017

---

# <a name="get-product-info-for-apps-and-add-ons"></a>Abrufen von Produktinformationen zu Apps und deren Add-Ons

Apps für Windows 10, Version 1607 oder höher, können Methoden der [StoreContext](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.aspx)-Klasse im [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx)-Namespace verwenden, um auf Store-bezogene Informationen für die aktuelle App oder eines ihrer Add-Ons (auch als In-App-Produkte oder IAPs bezeichnet) zuzugreifen. Die folgenden Beispiele in diesem Artikel zeigen, wie dies für verschiedene Szenarien durchgeführt wird. Eine vollständige Beispielanwendung finden Sie im [Store-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Store).

>**Hinweis**&nbsp;&nbsp;Dieser Artikel bezieht sich auf Apps für Windows 10, Version 1607 oder höher. Wenn Ihre App für eine frühere Version von Windows 10 geeignet ist, müssen Sie den [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.aspx)-Namespace anstelle des **Windows.Services.Store**-Namespace verwenden. Weitere Informationen finden Sie unter [In-App-Käufe und Testversionen mit dem Windows.ApplicationModel.Store-Namespace](in-app-purchases-and-trials-using-the-windows-applicationmodel-store-namespace.md).

## <a name="prerequisites"></a>Voraussetzungen

Für diese Beispiele gelten die folgenden Voraussetzungen:
* Ein Visual Studio-Projekt für eine UWP (Universelle Windows-Plattform)-App, die für Windows 10, Version 1607 oder höher, geeignet ist.
* Sie haben eine App im Windows Dev Center-Dashboard erstellt. Diese App wird veröffentlicht und ist im Store verfügbar. Dies kann eine App sein, die Sie für Kunden freigeben möchten, oder es kann eine einfache App sein, die den Mindestanforderungen gemäß dem [Zertifizierungskit für Windows-Apps](https://developer.microsoft.com/windows/develop/app-certification-kit) entspricht und nur zu Testzwecken verwendet wird. Weitere Informationen finden Sie unter [Hinweise für Tests](in-app-purchases-and-trials.md#testing).

Der Code in diesen Beispielen geht von Folgendem aus:
* Die Ausführung des Codes erfolgt im Kontext einer [Seite](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.aspx), die einen [ProgressRing](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.progressring.aspx) mit dem Namen ```workingProgressRing``` und einen [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) mit dem Namen ```textBlock``` enthält. Diese Objekte werden verwendet, um anzugeben, dass ein asynchroner Vorgang ausgeführt wird, bzw. um Ausgabemeldungen anzuzeigen.
* Die Codedatei enthält eine **using**-Anweisung für den **Windows.Services.Store**-Namespace.
* Die App ist eine Einzelbenutzer-App, die nur im Kontext des Benutzers ausgeführt wird, der die App gestartet hat. Weitere Informationen finden Sie unter [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md#api_intro).

Eine vollständige Beispielanwendung finden Sie im [Store-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Store).

>**Hinweis**&nbsp;&nbsp;Wenn Sie über eine Desktopanwendung verfügen, die die [Desktop-Brücke](https://developer.microsoft.com/windows/bridges/desktop) verwendet, müssen Sie möglicherweise zusätzlichen, in diesen Beispielen nicht aufgeführten Code hinzufügen, um das [StoreContext](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.aspx)-Objekt zu konfigurieren. Weitere Informationen finden Sie unter [Verwenden der StoreContext-Klasse in einer Desktopanwendung, die die Desktop-Brücke verwendet](in-app-purchases-and-trials.md#desktop).

## <a name="get-info-for-the-current-app"></a>Abrufen von Informationen für die aktuelle App

Verwenden Sie zum Abrufen von Store-Produktinformationen zur aktuellen App die [GetStoreProductForCurrentAppAsync](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.getstoreproductforcurrentappasync.aspx)-Methode. Dies ist eine asynchrone Methode, die ein [StoreProduct](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storeproduct.aspx)-Objekt zurückgibt, das Sie verwenden können, um Informationen wie den Preis abzurufen.

> [!div class="tabbedCodeSnippets"]
[!code-cs[GetProductInfo](./code/InAppPurchasesAndLicenses_RS1/cs/GetAppInfoPage.xaml.cs#GetAppInfo)]

## <a name="get-info-for-products-with-known-store-ids"></a>Abrufen von Informationen zu Produkten mit bekannten Store-IDs

Verwenden Sie zum Abrufen von Store-Produktinformationen für Apps oder Add-Ons, deren [Store-IDs](in-app-purchases-and-trials.md#store_ids) Sie kennen, die [GetStoreProductsAsync](https://msdn.microsoft.com/library/windows/apps/mt706579.aspx)-Methode. Hierbei handelt es sich um eine asynchrone Methode, die eine Sammlung von [StoreProduct](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storeproduct.aspx)-Objekten zurück gibt, die alle Apps oder Add-Ons darstellen. Zusätzlich zu den Store-IDs müssen Sie eine Liste mit Zeichenfolgen an diese Methode übergeben, welche die Typen der Add-Ons identifizieren. Eine Liste der unterstützten Zeichenfolgenwerte finden Sie in der [ProductKind](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storeproduct.productkind.aspx)-Eigenschaft.

Im folgenden Beispiel werden Informationen für dauerhafte Add-Ons mit den angegebenen Store-IDs abgerufen.

> [!div class="tabbedCodeSnippets"]
[!code-cs[GetProductInfo](./code/InAppPurchasesAndLicenses_RS1/cs/GetProductInfoPage.xaml.cs#GetProductInfo)]

## <a name="get-info-for-add-ons-that-are-available-for-the-current-app"></a>Abrufen von Informationen für Add-Ons, die für die aktuelle App verfügbar sind

Verwenden Sie zum Abrufen von Store-Produktinformationen für die Add-Ons, die für die aktuelle App verfügbar sind, die [GetAssociatedStoreProductsAsync](https://msdn.microsoft.com/library/windows/apps/mt706571.aspx)-Methode. Hierbei handelt es sich um eine asynchrone Methode, die eine Sammlung von [StoreProduct](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storeproduct.aspx)-Objekten zurück gibt, die alle verfügbaren Add-Ons darstellen. Sie müssen eine Liste mit Zeichenfolgen an diese Methode übergeben, welche die Typen von Add-Ons identifizieren, die Sie abrufen möchten. Eine Liste der unterstützten Zeichenfolgenwerte finden Sie in der [ProductKind](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storeproduct.productkind.aspx)-Eigenschaft.

>**Hinweis**&nbsp;&nbsp;Wenn die App über viele Add-Ons verfügt, können Sie alternativ die [GetAssociatedStoreProductsWithPagingAsync](https://msdn.microsoft.com/library/windows/apps/mt706572.aspx)-Methode verwenden, um für die Rückgabe der Add-On-Ergebnisse Paging zu verwenden.

Im folgenden Beispiel werden Informationen für alle dauerhaften Add-Ons, vom Store verwalteten Endverbraucher-Add-Ons und von Entwicklern verwalteten Endverbraucher-Add-Ons abgerufen.

> [!div class="tabbedCodeSnippets"]
[!code-cs[GetProductInfo](./code/InAppPurchasesAndLicenses_RS1/cs/GetAddOnInfoPage.xaml.cs#GetAddOnInfo)]


## <a name="get-info-for-add-ons-for-the-current-app-that-the-current-user-is-entitled-to-use"></a>Abrufen von Informationen zu Add-Ons für die aktuelle App, zu deren Verwendung der Benutzer berechtigt ist

Verwenden Sie zum Abrufen von Store-Produktinformationen für Add-Ons, zu deren Verwendung der Benutzer berechtigt ist, die [GetUserCollectionAsync](https://msdn.microsoft.com/library/windows/apps/mt706580.aspx)-Methode. Hierbei handelt es sich um eine asynchrone Methode, die eine Sammlung von [StoreProduct](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storeproduct.aspx)-Objekten zurück gibt, die alle Add-Ons darstellen. Sie müssen eine Liste mit Zeichenfolgen an diese Methode übergeben, welche die Typen von Add-Ons identifizieren, die Sie abrufen möchten. Eine Liste der unterstützten Zeichenfolgenwerte finden Sie in der [ProductKind](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storeproduct.productkind.aspx)-Eigenschaft.

>**Hinweis**&nbsp;&nbsp;Wenn die App über viele Add-Ons verfügt, können Sie alternativ die [GetUserCollectionWithPagingAsync](https://msdn.microsoft.com/library/windows/apps/mt706581.aspx)-Methode verwenden, um für die Rückgabe der Add-On-Ergebnisse Paging zu verwenden.

Im folgenden Beispiel werden Informationen für dauerhafte Add-Ons mit den angegebenen Store-IDs abgerufen.

> [!div class="tabbedCodeSnippets"]
[!code-cs[GetProductInfo](./code/InAppPurchasesAndLicenses_RS1/cs/GetUserCollectionPage.xaml.cs#GetUserCollection)]

## <a name="related-topics"></a>Verwandte Themen

* [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md)
* [Abrufen von Lizenzinformationen zu Apps und Add-Ons](get-license-info-for-apps-and-add-ons.md)
* [Aktivieren von In-App-Käufen von Apps und Add-Ons](enable-in-app-purchases-of-apps-and-add-ons.md)
* [Unterstützen von Endverbraucher-Add-On-Käufen](enable-consumable-add-on-purchases.md)
* [Implementieren einer Testversion der App](implement-a-trial-version-of-your-app.md)
* [Store-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Store)

