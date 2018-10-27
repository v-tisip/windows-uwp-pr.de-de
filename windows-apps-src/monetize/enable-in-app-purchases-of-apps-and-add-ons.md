---
author: Xansky
ms.assetid: B356C442-998F-4B2C-B550-70070C5E4487
description: Erfahren Sie, wie Sie den Windows.Services.Store-Namespace verwenden, um eine App oder ein Add-on zu erwerben.
title: Aktivieren von In-App-Käufen von Apps und Add-Ons
keywords: windows10, uwp, add-ons, in-app-käufe, IAPs, Windows.Services.Store
ms.author: mhopkins
ms.date: 08/25/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 6c5a5536ef1853a726421bdc75269f0cb5c1a84b
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5689579"
---
# <a name="enable-in-app-purchases-of-apps-and-add-ons"></a>Aktivieren von In-App-Käufen von Apps und Add-Ons

In diesem Artikel wird veranschaulicht, wie Sie Mitglieder im [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx)-Namespace verwenden, um für den Benutzer den Kauf der aktuellen App oder eines ihrer Add-Ons anzufordern. Wenn der Benutzer beispielsweise aktuell über eine Testversion der App verfügt, können Sie diesen Vorgang verwenden, um für den Benutzer eine Volllizenz zu erwerben. Alternativ können Sie diesen Prozess auch verwenden, um für den Benutzer ein Add-On wie z.B. ein neues Gamelevel zu erwerben.

Um den Kauf einer App oder eines Add-Ons anzufordern, bietet der [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx)-Namespace verschiedene Methoden:
* Wenn Sie die [Store-ID](in-app-purchases-and-trials.md#store_ids) der App bzw. des Add-Ons kennen, verwenden Sie die [RequestPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestpurchaseasync)-Methode der [StoreContext](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.aspx)-Klasse.
* Wenn Sie bereits über ein [**StoreProduct**](in-app-purchases-and-trials.md#products-skus)-, **StoreSku**- oder **StoreAvailability**-Objekt verfügen, das die App bzw. das Add-On darstellt, können Sie die **RequestPurchaseAsync**-Methoden dieser Objekte verwenden. Beispiele für die verschiedenen Methoden zum Abrufen einer **StoreProduct** in Ihrem Code finden Sie unter [Abrufen von Produktinformationen für Apps und Add-Ons](get-product-info-for-apps-and-add-ons.md).

Jede Methode zeigt dem Benutzer eine Standardbenutzeroberfläche für den Einkauf an und führt den Vorgang nach Abschluss der Transaktion asynchron aus. Die Methode gibt ein Objekt zurück, das angibt, ob die Transaktion erfolgreich war.

> [!NOTE]
> Der **Windows.Services.Store**-Namespace wurde in Windows10, Version 1607, eingeführt und kann nur in Projekten für die **Windows10 Anniversary Edition (10.0; Build 14393)** oder einer neueren Version in Visual Studio verwendet werden. Wenn Ihre App für eine frühere Version von Windows 10 geeignet ist, müssen Sie den [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.aspx)-Namespace anstelle des **Windows.Services.Store**-Namespace verwenden. Weitere Informationen finden Sie in [diesem Artikel](in-app-purchases-and-trials-using-the-windows-applicationmodel-store-namespace.md).

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Beispiel gelten die folgenden Voraussetzungen:
* Ein Visual Studio-Projekt für eine UWP (Universelle Windows-Plattform)-App, die für **Windows 10 Anniversary Edition (10.0; Build 14393)** oder höher, geeignet ist.
* Sie haben eine [App-Übermittlung](https://msdn.microsoft.com/windows/uwp/publish/app-submissions) im Windows Dev Center-Dashboard erstellt. Diese App wird veröffentlicht und ist im Store verfügbar. Optional können Sie die App so konfigurieren, daher sie während der Tests im Store nicht auffindbar ist. Weitere Informationen finden Sie unter [Hinweise für Tests](in-app-purchases-and-trials.md#testing).
* Wenn Sie In-App-Käufe für ein Add-On für die App aktivieren möchten, müssen Sie [das Add-On im Dev Center-Dashboard erstellen](../publish/add-on-submissions.md).

Der Code in diesem Beispiel geht von folgenden Voraussetzungen aus:
* Die Ausführung des Codes erfolgt im Kontext einer [Seite](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.aspx), die einen [ProgressRing](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.progressring.aspx) mit dem Namen ```workingProgressRing``` und einen [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) mit dem Namen ```textBlock``` enthält. Diese Objekte werden verwendet, um anzugeben, dass ein asynchroner Vorgang ausgeführt wird, bzw. um Ausgabemeldungen anzuzeigen.
* Die Codedatei enthält eine **using**-Anweisung für den **Windows.Services.Store**-Namespace.
* Die App ist eine Einzelbenutzer-App, die nur im Kontext des Benutzers ausgeführt wird, der die App gestartet hat. Weitere Informationen finden Sie unter [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md#api_intro).

> [!NOTE]
> Wenn Sie über eine Desktopanwendung verfügen, die die [Desktop-Brücke](https://developer.microsoft.com/windows/bridges/desktop) verwendet, müssen Sie möglicherweise zusätzlichen, in diesem Beispiel nicht aufgeführten Code hinzufügen, um das [StoreContext](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.aspx)-Objekt zu konfigurieren. Weitere Informationen finden Sie unter [Verwenden der StoreContext-Klasse in einer Desktopanwendung, die die Desktop-Brücke verwendet](in-app-purchases-and-trials.md#desktop).

## <a name="code-example"></a>Codebeispiel

In diesem Beispiel wird die Verwendung der [RequestPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestpurchaseasync)-Methode der [StoreContext](https://msdn.microsoft.com/library/windows/apps/windows.services.store.storecontext.aspx)-Klasse veranschaulicht, um eine App oder ein Add-On mit bekannter [Store-ID](in-app-purchases-and-trials.md#store-ids) zu erwerben. Eine vollständige Beispielanwendung finden Sie im [Store-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Store).

> [!div class="tabbedCodeSnippets"]
[!code-cs[EnablePurchases](./code/InAppPurchasesAndLicenses_RS1/cs/PurchaseAddOnPage.xaml.cs#PurchaseAddOn)]

## <a name="video"></a>Video

Sehen Sie sich das folgende Video mit einer Übersicht über In-App-Käufe in Ihrer App an.
<br/>
<br/>
> [!VIDEO https://channel9.msdn.com/Blogs/One-Dev-Minute/Adding-In-App-Purchases-to-Your-UWP-App/player]

## <a name="related-topics"></a>Verwandte Themen

* [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md)
* [Abrufen von Produktinformationen zu Apps und Add-Ons](get-product-info-for-apps-and-add-ons.md)
* [Abrufen von Lizenzinformationen zu Apps und Add-Ons](get-license-info-for-apps-and-add-ons.md)
* [Unterstützen von Käufen konsumierbarer Add-Ons](enable-consumable-add-on-purchases.md)
* [Implementieren einer Testversion der App](implement-a-trial-version-of-your-app.md)
* [Store-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Store)
