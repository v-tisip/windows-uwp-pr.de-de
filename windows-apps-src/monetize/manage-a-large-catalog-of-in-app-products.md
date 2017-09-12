---
author: mcleanbyron
ms.assetid: 5E722AFF-539D-456E-8C4A-ADE90CF7674A
description: "Wenn Ihre App einen großen In-App-Produktkatalog enthält, können Sie optional das in diesem Thema beschriebene Verfahren zum Verwalten des Katalogs ausführen."
title: "Verwalten eines großen Katalogs von In-App-Produkten"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, In-App-Käufe, IAPs, Add-Ons, Katalog, Windows.ApplicationModel.Store"
ms.openlocfilehash: 264db118c3d9f84cffcc966f017ddab4c14e28fb
ms.sourcegitcommit: 6c6f3c265498d7651fcc4081c04c41fafcbaa5e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="manage-a-large-catalog-of-in-app-products"></a>Verwalten eines großen Katalogs von In-App-Produkten


> [!NOTE]
> In diesem Artikel wird veranschaulicht, wie Mitglieder des [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.aspx)-Namespace verwendet werden. Wenn Ihre App für Windows10, Version 1607, oder höher entwickelt wurde, empfehlen wir Ihnen, Member des [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx)-Namespace und nicht des **Windows.ApplicationModel.Store**-Namespace zur Verwaltung von Add-Ons zu verwenden. Weitere Informationen finden Sie unter [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md).

Wenn Ihre App einen großen In-App-Produktkatalog enthält, können Sie optional das in diesem Thema beschriebene Verfahren zum Verwalten des Katalogs ausführen. In Versionen vor Windows10 galt eine Store-Einschränkung von 200Produkteinträgen pro Entwicklerkonto. Das in diesem Thema beschriebene Verfahren kann zur Umgehung dieser Einschränkung verwendet werden. Ab Windows10 gibt es keine Einschränkung der Anzahl von Produkteinträgen pro Entwicklerkonto im Store. Das in diesem Artikel beschriebene Verfahren ist nicht mehr erforderlich.

Um diese Funktionalität zu aktivieren, erstellen Sie einige wenige Produkteinträge für bestimmte Preisniveaus. Jeder kann Hunderte von Produkten innerhalb eines Katalogs repräsentieren. Sie verwenden die [RequestProductPurchaseAsync](https://msdn.microsoft.com/library/windows/apps/dn263382)-Methodenüberladung, die ein App-definiertes Angebot angibt, das mit einem im Store aufgelisteten In-App-Produkt verknüpft ist. Zusätzlich zur Angabe einer Verknüpfung von Angebot und Produkt während des Aufrufs sollte Ihre App auch ein [ProductPurchaseDisplayProperties](https://msdn.microsoft.com/library/windows/apps/dn263384)-Objekt übergeben, das die Angebotsdetails des großen Katalogs enthält. Wenn diese Details nicht angegeben sind, werden stattdessen die Details für das gelistete Produkt verwendet.

Der Store verwendet nur die *offerId* aus der Kaufanforderung im entsprechenden [PurchaseResults](https://msdn.microsoft.com/library/windows/apps/dn263392). Mit diesem Verfahren werden die Informationen, die ursprünglich bei der [Eintragung des In-App-Produkts im Store](https://msdn.microsoft.com/library/windows/apps/mt148551) bereitgestellt wurden, nicht direkt geändert.

## <a name="prerequisites"></a>Voraussetzungen

-   In diesem Thema wird die Store-Unterstützung für die Darstellung mehrerer In-App-Angebote mithilfe eines einzelnen im Store aufgeführten In-App-Produkts erläutert. Wenn Sie mit In-App-Käufen noch nicht vertraut sind, lesen Sie [Aktivieren von In-App-Produktkäufen](enable-in-app-product-purchases.md). Dort finden Sie Lizenzinformationen und eine Anleitung zur richtigen Eintragung Ihres In-App-Kaufs im Store.
-   Wenn Sie zum ersten Mal Code für neue In-App-Angebote schreiben und testen, müssen Sie anstelle des [CurrentApp](https://msdn.microsoft.com/library/windows/apps/hh779766)-Objekts das [CurrentAppSimulator](https://msdn.microsoft.com/library/windows/apps/hh779765)-Objekt verwenden. Auf diese Weise können Sie überprüfen, ob die Lizenzlogik simulierte Aufrufe an den Lizenzserver und nicht an den Liveserver verwendet. Dazu müssen Sie die Datei mit dem Namen „WindowsStoreProxy.xml“ in %userprofile%\\AppData\\local\\packages\\&lt;Paketname&gt;\\LocalState\\Microsoft\\Windows Store\\ApiData anpassen. Diese Datei wird vom Simulator in Microsoft Visual Studio erstellt, wenn Sie Ihre App zum ersten Mal ausführen. Sie können jedoch auch eine benutzerdefinierte Version dieser Datei zur Laufzeit laden. Weitere Informationen finden Sie unter [Verwenden der Datei „WindowsStoreProxy.xml“ mit CurrentAppSimulator](in-app-purchases-and-trials-using-the-windows-applicationmodel-store-namespace.md#proxy).
-   In diesem Thema wird auch auf Codebeispiele verwiesen, die im [Store-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/win10-1507/Samples/Store) zu finden sind. Dieses Beispiel bietet eine hervorragende Möglichkeit, die verschiedenen Monetarisierungsoptionen zu testen, die für universelle Windows-Plattform (UWP)-Apps verfügbar sind.

## <a name="make-the-purchase-request-for-the-in-app-product"></a>Durchführen der Kaufanforderung für das In-App-Produkt

Die Kaufanforderung für ein bestimmtes Produkt in einem umfangreichen Katalog wird ähnlich gehandhabt wie andere In-App-Kaufanforderungen. Wenn Ihre App die neue [RequestProductPurchaseAsync](https://msdn.microsoft.com/library/windows/apps/dn263382)-Methodenüberladung aufruft, stellt die App sowohl ein *OfferId*- als auch ein [ProductPurchaseDisplayProperties](https://msdn.microsoft.com/library/windows/apps/dn263390)-Objekt bereit, aufgefüllt mit dem Namen des In-App-Produkts.

> [!div class="tabbedCodeSnippets"]
[!code-cs[ManageCatalog](./code/InAppPurchasesAndLicenses/cs/ManageCatalog.cs#MakePurchaseRequest)]

## <a name="report-fulfillment-of-the-in-app-offer"></a>Melden der Erfüllung des In-App-Angebots

Die App muss die Produkterfüllung an den Store melden, sobald die lokale Erfüllung für das Angebot abgeschlossen ist. Wenn die App die Erfüllung des Angebots bei Verwendung eines großen Katalogs nicht meldet, kann der Benutzer keine In-App-Angebote erwerben, für die der gleiche Store-Produkteintrag genutzt wird.

Wie bereits erwähnt, verwendet der Store nur bereitgestellte Angebotsinformationen zum Auffüllen von [PurchaseResults](https://msdn.microsoft.com/library/windows/apps/dn263392) und erstellt keine persistente Verknüpfung zwischen einem Angebot aus einem großen Katalog und einem Produkteintrag im Store. Daher müssen Sie die Benutzerberechtigungen für Produkte aus großen Katalogen nachverfolgen und dem Benutzer produktspezifischen Kontext (wie den Namen des gekauften Artikels oder Details zu diesem) außerhalb des [RequestProductPurchaseAsync](https://msdn.microsoft.com/library/windows/apps/dn263382)-Vorgangs zur Verfügung stellen.

Der folgende Code veranschaulicht den Erfüllungsaufruf sowie ein Muster für Meldungen auf der Benutzeroberfläche, in das die angebotsspezifischen Informationen eingefügt werden. Da keine produktspezifischen Informationen vorhanden sind, werden im Beispiel Informationen aus [ListingInformation](https://msdn.microsoft.com/library/windows/apps/br225163) des Produkts verwendet.

> [!div class="tabbedCodeSnippets"]
[!code-cs[ManageCatalog](./code/InAppPurchasesAndLicenses/cs/ManageCatalog.cs#ReportFulfillment)]

## <a name="related-topics"></a>Verwandte Themen

* [Unterstützen des Kaufs von In-App-Produkten](enable-in-app-product-purchases.md)
* [Käufe von konsumierbaren In-App-Produkten aktivieren](enable-consumable-in-app-product-purchases.md)
* [Store-Beispiel (zeigt Testversionen und In-App-Einkäufe)](https://github.com/Microsoft/Windows-universal-samples/tree/win10-1507/Samples/Store)
* [RequestProductPurchaseAsync](https://msdn.microsoft.com/library/windows/apps/dn263382)
* [ProductPurchaseDisplayProperties](https://msdn.microsoft.com/library/windows/apps/dn263384)
