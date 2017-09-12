---
author: mcleanbyron
description: "Beschreibt das erweiterte JSON-Datenschema für Store-Produkte im Windows.Services.Store-Namespace."
title: "Datenschemata für Store-Produkte"
ms.author: mcleans
ms.date: 07/20/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: 
ms.openlocfilehash: 2a294dc490a0b7bed5e426ff26dfed948f337dfa
ms.sourcegitcommit: a9e4be98688b3a6125fd5dd126190fcfcd764f95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2017
---
# <a name="data-schemas-for-store-products"></a>Datenschemata für Store-Produkte

Wenn Sie ein Produkt wie z.B. eine App oder ein Add-On im Store einreichen, verwaltet der Informationsspeicher einen umfassenden Satz von Daten für das Produkt und dessen Lizenzen. In Ihrem App-Code können Sie programmgesteuerten Zugriff auf einige dieser Daten mithilfe der Eigenschaften im [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx) Namespace nutzen. Zum Beispiel können Sie die Beschreibung und den Preis für die aktuelle App oder ein Add-On für die aktuelle App mithilfe der [StoreProduct.Description](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_Description) und [StoreProduct.Price](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_Price) Eigenschaften abrufen.

Viele Daten für Produkte im Store sind jedoch ist nicht über vordefinierte Eigenschaften im [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx) Namespace verfügbar. Um auf die vollständigen Daten für ein Produkt in Ihrem Code zuzugreifen, können Sie die folgenden allgemeinen Eigenschaften verwenden:

* [StoreProduct.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_ExtendedJsonData_)
* [StoreSku.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storesku#Windows_Services_Store_StoreSku_ExtendedJsonData_)
* [StoreAvailability.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storeavailability#Windows_Services_Store_StoreAvailability_ExtendedJsonData_)
*   [StoreCollectionData.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storecollectiondata#Windows_Services_Store_StoreCollectionData_ExtendedJsonData_)
*   [StoreAppLicense.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storeapplicense#Windows_Services_Store_StoreAppLicense_ExtendedJsonData_)
* [StoreLicense.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storelicense#Windows_Services_Store_StoreLicense_ExtendedJsonData_)
*   [StorePurchaseProperties.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storepurchaseproperties#Windows_Services_Store_StorePurchaseProperties_ExtendedJsonData_)

Diese Eigenschaften geben die vollständigen Daten für das entsprechende Objekt als JSON-formatierte Zeichenfolge zurück. Dieser Artikel enthält das vollständige Schema für die Daten von diesen Eigenschaften zurückgegeben werden.

> [!NOTE]
> Produkte im Store sind in einer Hierarchie von [Produkt](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct), [SKU](https://docs.microsoft.com/uwp/api/windows.services.store.storesku) und [Verfügbarkeit](https://docs.microsoft.com/uwp/api/windows.services.store.storeavailability) Objekten organisiert. Weitere Informationen finden Sie unter [Produkte, SKUs und Verfügbarkeiten](in-app-purchases-and-trials.md#products-skus).

## <a name="schema-for-storeproduct-storesku-storeavailability-and-storecollectiondata"></a>Schema für StoreProduct, StoreSku, StoreAvailability und StoreCollectionData

Das folgende Schema beschreibt die JSON-formatierte Zeichenfolge die von [StoreProduct.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_ExtendedJsonData_) zurückgegeben wird. Die [StoreSku.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storesku#Windows_Services_Store_StoreSku_ExtendedJsonData_), [StoreAvailability.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storeavailability#Windows_Services_Store_StoreAvailability_ExtendedJsonData_), und [StoreCollectionData.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storecollectiondata#Windows_Services_Store_StoreCollectionData_ExtendedJsonData_) Eigenschaften geben nur die Teile des Schemas zurück, die unter den Pfaden ```DisplaySkuAvailabilities\Sku```, ```DisplaySkuAvailabilities\Availabilities``` und ```DisplaySkuAvailabilities\Sku\CollectionData``` definiert sind.

Ein Beispiel für eine JSON-formatierte Zeichenfolge von [StoreProduct.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_ExtendedJsonData_) finden Sie [in diesem Abschnitt](#product-example).

[!code[ExtendedJsonDataSchema](./code/InAppPurchasesAndLicenses_RS1/json/StoreProduct.ExtendedJsonData.json#L1-L603)]

<span id="product-example" />
### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine JSON-formatierte Zeichenfolge von der [StoreProduct.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_ExtendedJsonData_) Eigenschaft für die App.

[!code[ExtendedJsonDataSchema](./code/InAppPurchasesAndLicenses_RS1/json/StoreProduct.ExtendedJsonDataExample.json#L1-L268)]

## <a name="schema-for-storeapplicense-and-storelicense"></a>Schema für StoreAppLicense und StoreLicense

Das folgende Schema beschreibt die JSON-formatierte Zeichenfolge die von [StoreAppLicense.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storeavailability#Windows_Services_Store_StoreAppLicense_ExtendedJsonData_) zurückgegeben wird. Die [StoreLicense.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storeavailability#Windows_Services_Store_StoreLicense_ExtendedJsonData_) Eigenschaft gibt nur die Teile des Schemas zurück, die unter dem ```productAddOns``` Pfad definiert sind.

Ein Beispiel für eine JSON-formatierte Zeichenfolge von [StoreAppLicense.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storeavailability#Windows_Services_Store_StoreAppLicense_ExtendedJsonData_) finden Sie [in diesem Abschnitt](#license-example).

[!code[ExtendedJsonDataSchema](./code/InAppPurchasesAndLicenses_RS1/json/StoreAppLicense.ExtendedJsonData.json#L1-L80)]

<span id="license-example" />
### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine JSON-formatierte Zeichenfolge von der [StoreAppLicense.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storeavailability#Windows_Services_Store_StoreAppLicense_ExtendedJsonData_) Eigenschaft für die App.

[!code[ExtendedJsonDataSchema](./code/InAppPurchasesAndLicenses_RS1/json/StoreAppLicense.ExtendedJsonDataExample.json#L1-L28)]

## <a name="schema-for-storepurchaseproperties"></a>Schema für StorePurchaseProperties

Das folgende Schema beschreibt die JSON-formatierte Zeichenfolge die von [StorePurchaseProperties.ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storepurchaseproperties#Windows_Services_Store_StorePurchaseProperties_ExtendedJsonData_) zurückgegeben wird.

[!code[ExtendedJsonDataSchema](./code/InAppPurchasesAndLicenses_RS1/json/StorePurchaseProperties.ExtendedJsonData.json#L1-L12)]

## <a name="related-topics"></a>Verwandte Themen

* [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md)
* [Abrufen von Produktinformationen zu Apps und Add-Ons](get-product-info-for-apps-and-add-ons.md)
* [Abrufen von Lizenzinformationen zu Apps und Add-Ons](get-license-info-for-apps-and-add-ons.md)
* [Aktivieren von In-App-Käufen von Apps und Add-Ons](enable-in-app-purchases-of-apps-and-add-ons.md)
* [Unterstützen von Endverbraucher-Add-On-Käufen](enable-consumable-add-on-purchases.md)
* [Implementieren einer Testversion Ihrer App](implement-a-trial-version-of-your-app.md)
