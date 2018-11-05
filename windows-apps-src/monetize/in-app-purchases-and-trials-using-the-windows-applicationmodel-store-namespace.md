---
author: Xansky
ms.assetid: 32572890-26E3-4FBB-985B-47D61FF7F387
description: Erfahren Sie, wie Sie In-App-Käufe und Testversionen in UWP-Apps aktivieren, die für Versionen vor Windows10, Version 1607 bestimmt sind.
title: In-App-Käufe und Testversionen mit dem Windows.ApplicationModel.Store-Namespace
ms.author: mhopkins
ms.date: 08/25/2017
ms.topic: article
keywords: uwp, in-app-käufe, IAPs, add-ons, testversionen, Windows.ApplicationModel.Store
ms.localizationpriority: medium
ms.openlocfilehash: 28fe27cc4464598414fec11d6812e2e9ea377aff
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6036360"
---
# <a name="in-app-purchases-and-trials-using-the-windowsapplicationmodelstore-namespace"></a><span data-ttu-id="5f7b7-104">In-App-Käufe und Testversionen mit dem Windows.ApplicationModel.Store-Namespace</span><span class="sxs-lookup"><span data-stu-id="5f7b7-104">In-app purchases and trials using the Windows.ApplicationModel.Store namespace</span></span>

<span data-ttu-id="5f7b7-105">Sie können Mitglieder des [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.aspx) verwenden, um Ihrer Universal Windows Platform (UWP)-App In-App-Käufe und Testfunktionen hinzuzufügen und die Monetarisierung Ihrer App zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-105">You can use members in the [Windows.ApplicationModel.Store](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.aspx) namespace to add in-app purchases and trial functionality to your Universal Windows Platform (UWP) app to help monetize your app.</span></span> <span data-ttu-id="5f7b7-106">Diese APIs ermöglichen auch den Zugriff auf die Lizenzinformationen für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-106">These APIs also provide access to the license info for your app.</span></span>

<span data-ttu-id="5f7b7-107">Die Artikel in diesem Abschnitt enthalten ausführliche Anleitungen und Codebeispiele für die Verwendung der Mitgliedern des **Windows.ApplicationModel.Store**-Namespace für verschiedene häufige Szenarien.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-107">The articles in this section provide in-depth guidance and code examples for using the members in the **Windows.ApplicationModel.Store** namespace for several common scenarios.</span></span> <span data-ttu-id="5f7b7-108">Eine Übersicht über die Basiskonzepte im Zusammenhang mit In-App-Käufen in UWP-Apps finden Sie unter [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md).</span><span class="sxs-lookup"><span data-stu-id="5f7b7-108">For an overview of basic concepts related to in-app purchases in UWP apps, see [In-app purchases and trials](in-app-purchases-and-trials.md).</span></span> <span data-ttu-id="5f7b7-109">Ein vollständiges Beispiel, das zeigt, wie Sie Testversionen und In-App-Käufe mithilfe des **Windows.ApplicationModel.Store**-Namespace implementieren, finden Sie im [Store-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/win10-1507/Samples/Store).</span><span class="sxs-lookup"><span data-stu-id="5f7b7-109">For a complete sample that demonstrates how to implement trials and in-app purchases using the **Windows.ApplicationModel.Store** namespace, see the [Store sample](https://github.com/Microsoft/Windows-universal-samples/tree/win10-1507/Samples/Store).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f7b7-110">Der **Windows.ApplicationModel.Store**-Namespace wird nicht mehr mit neuen Funktionen aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-110">The **Windows.ApplicationModel.Store** namespace is no longer being updated with new features.</span></span> <span data-ttu-id="5f7b7-111">Wenn Ihr Projekt **Windows 10 Anniversary Edition (10.0; Build 14393)** oder eine höhere Version in Visual Studio verwendet (d. h. Sie verwenden Windows10, Version 1607 oder höher), wird stattdessen die Verwendung des [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx)-Namespace empfohlen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-111">If your project targets **Windows 10 Anniversary Edition (10.0; Build 14393)** or a later release in Visual Studio (that is, you are targeting Windows 10, version 1607, or later), we recommend that you use the [Windows.Services.Store](https://msdn.microsoft.com/library/windows/apps/windows.services.store.aspx) namespace instead.</span></span> <span data-ttu-id="5f7b7-112">Weitere Informationen finden Sie unter [In-App-Käufe und Testversionen](https://msdn.microsoft.com/windows/uwp/monetize/in-app-purchases-and-trials).</span><span class="sxs-lookup"><span data-stu-id="5f7b7-112">For more information, see [In-app purchases and trials](https://msdn.microsoft.com/windows/uwp/monetize/in-app-purchases-and-trials).</span></span> <span data-ttu-id="5f7b7-113">Der **Windows.ApplicationModel.Store** -Namespace wird nicht unterstützt, auf Windows-desktopanwendungen, die die [Desktop-Brücke](https://developer.microsoft.com/windows/bridges/desktop) verwenden oder in apps oder Spiele, die eine Sandbox-Entwicklung im Partner Center verwenden (z. B. Dies ist der Fall für alle, die von Spielen integriert mit Xbox Live).</span><span class="sxs-lookup"><span data-stu-id="5f7b7-113">The **Windows.ApplicationModel.Store** namespace is not supported in Windows desktop applications that use the [Desktop Bridge](https://developer.microsoft.com/windows/bridges/desktop) or in apps or games that use a development sandbox in Partner Center (for example, this is the case for any game that integrates with Xbox Live).</span></span> <span data-ttu-id="5f7b7-114">Diese Produkte müssen zum Implementieren von In-App-Käufen und Testversionen den **Windows.Services.Store**-Namespace verwenden.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-114">These products must use the **Windows.Services.Store** namespace to implement in-app purchases and trials.</span></span>

## <a name="get-started-with-the-currentapp-and-currentappsimulator-classes"></a><span data-ttu-id="5f7b7-115">Erste Schrittemit den Klassen CurrentApp und CurrentAppSimulator</span><span class="sxs-lookup"><span data-stu-id="5f7b7-115">Get started with the CurrentApp and CurrentAppSimulator classes</span></span>

<span data-ttu-id="5f7b7-116">Den Haupteinstiegspunkt in den **Windows.ApplicationModel.Store**-Namespace stellt die Klasse [CurrentApp](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentapp.aspx) dar.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-116">The main entry point to the **Windows.ApplicationModel.Store** namespace is the [CurrentApp](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentapp.aspx) class.</span></span> <span data-ttu-id="5f7b7-117">Diese Klasse stellt statische Eigenschaften und Methoden bereit, mit denen Sie Informationen für die aktuelle App und die verfügbaren Add-Ons abrufen, eine App oder ein Add-On für den aktuellen Benutzer kaufen, Lizenzinformationen für die aktuelle App oder die Add-Ons abrufen und weitere Aufgaben durchführen können.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-117">This class provides static properties and methods you can use to get info for the current app and its available add-ons, get license info for the current app or its add-ons, purchase an app or add-on for the current user, and perform other tasks.</span></span>

<span data-ttu-id="5f7b7-118">Die Klasse [CurrentApp](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentapp.aspx) erhält ihre Daten aus dem Microsoft Store. Daher benötigen Sie ein Entwicklerkonto, und die App muss im Store veröffentlicht werden, bevor Sie diese Klasse erfolgreich in Ihrer App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-118">The [CurrentApp](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentapp.aspx) class obtains its data from the Microsoft Store, so you must have a developer account and the app must be published in the Store before you can successfully use this class in your app.</span></span> <span data-ttu-id="5f7b7-119">Vor dem Übermitteln Ihrer App an den Store können Sie den Code mit einer simulierten Version dieser Klasse mit dem Namen [CurrentAppSimulator](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentappsimulator.aspx) testen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-119">Before you submit your app to the Store, you can test your code with a simulated version of this class called [CurrentAppSimulator](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentappsimulator.aspx).</span></span> <span data-ttu-id="5f7b7-120">Nachdem Sie Ihre App getestet haben, und bevor Sie diese an den Microsoft Store übermitteln, müssen Sie die Instanzen von **CurrentAppSimulator** durch **CurrentApp** ersetzen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-120">After you test your app, and before you submit it to the Microsoft Store, you must replace the instances of **CurrentAppSimulator** with **CurrentApp**.</span></span> <span data-ttu-id="5f7b7-121">Ihre App wird nicht zertifiziert, wenn sie **CurrentAppSimulator** verwendet.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-121">Your app will fail certification if it uses **CurrentAppSimulator**.</span></span>

<span data-ttu-id="5f7b7-122">Wenn **CurrentAppSimulator** verwendet wird, wird der ursprünglichen Status der Lizenzierung Ihrer App und In-App-Produkte in einer lokalen Datei mit dem Namen WindowsStoreProxy.xml auf Ihrem Entwicklungscomputer beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-122">When the **CurrentAppSimulator** is used, the initial state of your app's licensing and in-app products is described in a local file on your development computer named WindowsStoreProxy.xml.</span></span> <span data-ttu-id="5f7b7-123">Weitere Informationen zu dieser Datei finden Sie unter [Verwenden der Datei „WindowsStoreProxy.xml“ mit CurrentAppSimulator](#proxy).</span><span class="sxs-lookup"><span data-stu-id="5f7b7-123">For more information about this file, see [Using the WindowsStoreProxy.xml file with CurrentAppSimulator](#proxy).</span></span>

<span data-ttu-id="5f7b7-124">Weitere Informationen zu den allgemeinen Aufgaben, die Sie mit **CurrentApp** und **CurrentAppSimulator** ausführen können, finden Sie in den folgenden Artikeln.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-124">For more information about common tasks you can perform using **CurrentApp** and **CurrentAppSimulator**, see the following articles.</span></span>

| <span data-ttu-id="5f7b7-125">Thema</span><span class="sxs-lookup"><span data-stu-id="5f7b7-125">Topic</span></span>       | <span data-ttu-id="5f7b7-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-126">Description</span></span>                 |
|----------------------------|-----------------------------|
| [<span data-ttu-id="5f7b7-127">Ausschließen oder Einschränken von Features in einer Testversion</span><span class="sxs-lookup"><span data-stu-id="5f7b7-127">Exclude or limit features in a trial version</span></span>](exclude-or-limit-features-in-a-trial-version-of-your-app.md) | <span data-ttu-id="5f7b7-128">Durch einen kostenlose, zeitlich begrenzte Testversion Ihrer App mit eingeschränkten Features können Sie Ihre Kunden motivieren, auf die Vollversion Ihrer App zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-128">If you enable customers to use your app for free during a trial period, you can entice your customers to upgrade to the full version of your app by excluding or limiting some features during the trial period.</span></span> |
| [<span data-ttu-id="5f7b7-129">Unterstützen des Kaufs von In-App-Produkten</span><span class="sxs-lookup"><span data-stu-id="5f7b7-129">Enable in-app product purchases</span></span>](enable-in-app-product-purchases.md)      |  <span data-ttu-id="5f7b7-130">Sie können unabhängig davon, ob Ihre App kostenlos oder kostenpflichtig ist, Inhalte, andere Apps oder neue App-Funktionen (wie das Freischalten des nächsten Levels eines Spiels) direkt in der App verkaufen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-130">Whether your app is free or not, you can sell content, other apps, or new app functionality (such as unlocking the next level of a game) from right within the app.</span></span> <span data-ttu-id="5f7b7-131">Hier zeigen wir Ihnen, wie Sie diese Produkte in Ihrer App aktivieren können.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-131">Here we show you how to enable these products in your app.</span></span>  |
| [<span data-ttu-id="5f7b7-132">Unterstützen von Endverbraucher-Add-On-Käufen</span><span class="sxs-lookup"><span data-stu-id="5f7b7-132">Enable consumable in-app product purchases</span></span>](enable-consumable-in-app-product-purchases.md)      | <span data-ttu-id="5f7b7-133">Sie können In-App-Käufe von konsumierbaren Produkten – Artikel, die gekauft, verwendet und wieder gekauft werden können – über die Store-Handelsplattform anbieten, um den Kunden beim Kauf Stabilität und Zuverlässigkeit zu bieten.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-133">Offer consumable in-app products—items that can be purchased, used, and purchased again—through the Store commerce platform to provide your customers with a purchase experience that is both robust and reliable.</span></span> <span data-ttu-id="5f7b7-134">Dies ist besonders nützlich für Dinge wie spielinterne Währungen (Gold, Münzen usw.), die gekauft und dann zum Erwerben bestimmter Power-Ups verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-134">This is especially useful for things like in-game currency (gold, coins, etc.) that can be purchased and then used to purchase specific power-ups.</span></span> |
| [<span data-ttu-id="5f7b7-135">Verwalten eines großen Katalogs von In-App-Produkten</span><span class="sxs-lookup"><span data-stu-id="5f7b7-135">Manage a large catalog of in-app products</span></span>](manage-a-large-catalog-of-in-app-products.md)      |   <span data-ttu-id="5f7b7-136">Wenn Ihre App einen großen In-App-Produktkatalog enthält, können Sie optional das in diesem Thema beschriebene Verfahren zum Verwalten des Katalogs ausführen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-136">If your app offers a large in-app product catalog, you can optionally follow the process described in this topic to help manage your catalog.</span></span>    |
| [<span data-ttu-id="5f7b7-137">Überprüfen von Produktkäufen anhand von Belegen</span><span class="sxs-lookup"><span data-stu-id="5f7b7-137">Use receipts to verify product purchases</span></span>](use-receipts-to-verify-product-purchases.md)      |   <span data-ttu-id="5f7b7-138">Jede Microsoft Store-Transaktion, die zu einem erfolgreichen Produktkauf führt, kann optional einen Transaktionsbeleg zurückgeben, der dem Kunden Informationen zum aufgelisteten Produkt und zu den Kosten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-138">Each Microsoft Store transaction that results in a successful product purchase can optionally return a transaction receipt that provides information about the listed product and monetary cost to the customer.</span></span> <span data-ttu-id="5f7b7-139">Der Zugriff auf diese Informationen unterstützt Szenarien, in denen Ihre App überprüfen muss, ob ein Benutzer Ihre App erworben oder im MicrosoftStore In-App-Produkte gekauft hat.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-139">Having access to this information supports scenarios where your app needs to verify that a user purchased your app, or has made in-app product purchases from the Microsoft Store.</span></span> |

<span id="proxy" />

## <a name="using-the-windowsstoreproxyxml-file-with-currentappsimulator"></a><span data-ttu-id="5f7b7-140">Verwenden der Datei WindowsStoreProxy.xml mit CurrentAppSimulator</span><span class="sxs-lookup"><span data-stu-id="5f7b7-140">Using the WindowsStoreProxy.xml file with CurrentAppSimulator</span></span>

<span data-ttu-id="5f7b7-141">Wenn **CurrentAppSimulator** verwendet wird, wird der ursprünglichen Status der Lizenzierung Ihrer App und In-App-Produkte in einer lokalen Datei mit dem Namen WindowsStoreProxy.xml auf Ihrem Entwicklungscomputer beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-141">When the **CurrentAppSimulator** is used, the initial state of your app's licensing and in-app products is described in a local file on your development computer named WindowsStoreProxy.xml.</span></span> <span data-ttu-id="5f7b7-142">Durch **CurrentAppSimulator**-Methoden, die den Status der App verändern, beispielsweise durch den Kauf einer Lizenz oder die Verarbeitung eines In-App-Kaufs, wird lediglich der Status des **CurrentAppSimulator**-Objekts im Speicher aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-142">**CurrentAppSimulator** methods that alter the app's state, for example by buying a license or handling an in-app purchase, only update the state of the **CurrentAppSimulator** object in memory.</span></span> <span data-ttu-id="5f7b7-143">Der Inhalt von WindowsStoreProxy.xml wird nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-143">The contents of WindowsStoreProxy.xml are not changed.</span></span> <span data-ttu-id="5f7b7-144">Wenn die App erneut gestartet wird, wird der Lizenzstatus auf den Status zurückgesetzt, der in WindowsStoreProxy.xml beschrieben ist.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-144">When the app starts again, the license state reverts to what is described in WindowsStoreProxy.xml.</span></span>

<span data-ttu-id="5f7b7-145">Standardmäßig wird eine WindowsStoreProxy.xml-Datei unter folgendem Pfad erstellt: %UserProfile%\AppData\Local\Packages\\&lt;App-Paket-Ordner&gt;\LocalState\Microsoft\Windows Store\ApiData.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-145">A WindowsStoreProxy.xml file is created by default at the following location: %UserProfile%\AppData\Local\Packages\\&lt;app package folder&gt;\LocalState\Microsoft\Windows Store\ApiData.</span></span> <span data-ttu-id="5f7b7-146">Sie können diese Datei bearbeiten, um das Szenario zu definieren, das Sie in den **CurrentAppSimulator**-Eigenschaften simulieren möchten.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-146">You can edit this file to define the scenario that you want to simulate in the **CurrentAppSimulator** properties.</span></span>

<span data-ttu-id="5f7b7-147">Auch wenn Sie die Werte in dieser Datei ändern können, wird empfohlen, dass Sie eine eigene WindowsStoreProxy.xml-Datei (in einem Datenordner des Visual Studio-Projekts) zur Verwendung durch **CurrentAppSimulator** erstellen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-147">Although you can modify the values in this file, we recommend that you create your own WindowsStoreProxy.xml file (in a data folder of your Visual Studio project) for **CurrentAppSimulator** to use instead.</span></span> <span data-ttu-id="5f7b7-148">Rufen Sie [ReloadSimulatorAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentappsimulator.reloadsimulatorasync) auf, um Ihre Datei zu laden, wenn Sie die Transaktion simulieren.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-148">When simulating the transaction, call [ReloadSimulatorAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentappsimulator.reloadsimulatorasync) to load your file.</span></span> <span data-ttu-id="5f7b7-149">Wenn Sie **ReloadSimulatorAsync** nicht aufrufen, um Ihre eigene WindowsStoreProxy.xml-Datei zu laden, erstellt/lädt **CurrentAppSimulator** die standardmäßige WindowsStoreProxy.xml-Datei (überschreibt sie jedoch nicht).</span><span class="sxs-lookup"><span data-stu-id="5f7b7-149">If you do not call **ReloadSimulatorAsync** to load your own WindowsStoreProxy.xml file, **CurrentAppSimulator** will create/load (but not overwrite) the default WindowsStoreProxy.xml file.</span></span>

> [!NOTE]
> <span data-ttu-id="5f7b7-150">Beachten Sie, dass **CurrentAppSimulator** nicht vollständig initialisiert ist, bis **ReloadSimulatorAsync** abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-150">Be aware that **CurrentAppSimulator** is not fully initialized until **ReloadSimulatorAsync** completes.</span></span> <span data-ttu-id="5f7b7-151">Und da **ReloadSimulatorAsync** eine asynchrone Methode ist, müssen Sie darauf achten, eine Racebedingung zu vermeiden, in der **CurrentAppSimulator** in einem Thread abgefragt und gleichzeitig in einem anderen Thread initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-151">And, since **ReloadSimulatorAsync** is an asynchronous method, care should be taken to avoid the race condition of querying **CurrentAppSimulator** on one thread while it is being initialized on another.</span></span> <span data-ttu-id="5f7b7-152">Eine Möglichkeit besteht darin, ein Flag verwenden, um anzugeben, dass die Initialisierung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-152">One technique is to use a flag to indicate that initialization is complete.</span></span> <span data-ttu-id="5f7b7-153">Eine App, die aus dem Microsoft Store installiert wird, muss **CurrentApp** anstelle von **CurrentAppSimulator** verwenden. In diesem Fall wird **ReloadSimulatorAsync** nicht aufgerufen, und die eben erwähnte Racebedingung tritt nicht ein.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-153">An app that is installed from the Microsoft Store must use **CurrentApp** instead of **CurrentAppSimulator**, and in that case **ReloadSimulatorAsync** is not called and therefore the race condition just mentioned does not apply.</span></span> <span data-ttu-id="5f7b7-154">Aus diesem Grund sollten Sie Ihren Code so entwerfen, dass er in beiden Fällen funktioniert, asynchron und synchron.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-154">For this reason, design your code so that it will work in both cases, both asychronously and synchronously.</span></span>


<span id="proxy-examples" />

### <a name="examples"></a><span data-ttu-id="5f7b7-155">Beispiele</span><span class="sxs-lookup"><span data-stu-id="5f7b7-155">Examples</span></span>

<span data-ttu-id="5f7b7-156">In diesem Beispiel wird eine WindowsStoreProxy.xml-Datei (UTF-16-codiert) gezeigt, die eine App mit einem Testmodus beschreibt, der am 19.Januar2015 um 05:00 Uhr (UTC) abläuft.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-156">This example is a WindowsStoreProxy.xml file (UTF-16 encoded) that describes an app with a trial mode that expires at 05:00 (UTC) on Jan. 19, 2015.</span></span>

> [!div class="tabbedCodeSnippets"]
```xml
<?xml version="1.0" encoding="UTF-16"?>
<CurrentApp>
  <ListingInformation>
    <App>
      <AppId>2B14D306-D8F8-4066-A45B-0FB3464C67F2</AppId>
      <LinkUri>http://apps.windows.microsoft.com/app/2B14D306-D8F8-4066-A45B-0FB3464C67F2</LinkUri>
      <CurrentMarket>en-US</CurrentMarket>
      <AgeRating>3</AgeRating>
      <MarketData xml:lang="en-us">
        <Name>App with a trial license</Name>
        <Description>Sample app for demonstrating trial license management</Description>
        <Price>4.99</Price>
        <CurrencySymbol>$</CurrencySymbol>
      </MarketData>
    </App>
  </ListingInformation>
  <LicenseInformation>
    <App>
      <IsActive>true</IsActive>
      <IsTrial>true</IsTrial>
      <ExpirationDate>2015-01-19T05:00:00.00Z</ExpirationDate>
    </App>
  </LicenseInformation>
  <Simulation SimulationMode="Automatic">
    <DefaultResponse MethodName="LoadListingInformationAsync_GetResult" HResult="E_FAIL"/>
  </Simulation>
</CurrentApp>
```

<span data-ttu-id="5f7b7-157">Im nächsten Beispiel wird eine WindowsStoreProxy.xml-Datei (UTF-16-codiert) gezeigt, die eine App beschreibt, die gekauft wurde, ein Feature besitzt, das am 19.Januar2015 um 05:00 (UTC) abläuft und über einen konsumierbaren In-App-Kauf verfügt.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-157">The next example is a WindowsStoreProxy.xml file (UTF-16 encoded) that describes an app that has been purchased, has a feature that expires at 05:00 (UTC) on Jan. 19, 2015, and has a consumable in-app purchase.</span></span>

> [!div class="tabbedCodeSnippets"]
```xml
<?xml version="1.0" encoding="utf-16" ?>
<CurrentApp>
  <ListingInformation>
    <App>
      <AppId>988b90e4-5d4d-4dea-99d0-e423e414ffbc</AppId>
      <LinkUri>http://apps.windows.microsoft.com/app/988b90e4-5d4d-4dea-99d0-e423e414ffbc</LinkUri>
      <CurrentMarket>en-us</CurrentMarket>
      <AgeRating>3</AgeRating>
      <MarketData xml:lang="en-us">
        <Name>App with several in-app products</Name>
        <Description>Sample app for demonstrating an expiring in-app product and a consumable in-app product</Description>
        <Price>5.99</Price>
        <CurrencySymbol>$</CurrencySymbol>
      </MarketData>
    </App>
    <Product ProductId="feature1" LicenseDuration="10" ProductType="Durable">
      <MarketData xml:lang="en-us">
        <Name>Expiring Item</Name>
        <Price>1.99</Price>
        <CurrencySymbol>$</CurrencySymbol>
      </MarketData>
    </Product>
    <Product ProductId="consumable1" LicenseDuration="0" ProductType="Consumable">
      <MarketData xml:lang="en-us">
        <Name>Consumable Item</Name>
        <Price>2.99</Price>
        <CurrencySymbol>$</CurrencySymbol>
      </MarketData>
    </Product>
  </ListingInformation>
  <LicenseInformation>
    <App>
      <IsActive>true</IsActive>
      <IsTrial>false</IsTrial>
    </App>
    <Product ProductId="feature1">
      <IsActive>true</IsActive>
      <ExpirationDate>2015-01-19T00:00:00.00Z</ExpirationDate>
    </Product>
  </LicenseInformation>
  <ConsumableInformation>
    <Product ProductId="consumable1" TransactionId="00000001-0000-0000-0000-000000000000" Status="Active"/>
  </ConsumableInformation>
</CurrentApp>
```


<span id="proxy-schema" />

### <a name="schema"></a><span data-ttu-id="5f7b7-158">Schema</span><span class="sxs-lookup"><span data-stu-id="5f7b7-158">Schema</span></span>

<span data-ttu-id="5f7b7-159">In diesem Abschnitt wird die XSD-Datei aufgelistet, die die Struktur der WindowsStoreProxy.xml-Datei definiert.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-159">This section lists the XSD file that defines the structure of the WindowsStoreProxy.xml file.</span></span> <span data-ttu-id="5f7b7-160">Um dieses Schema beim Arbeiten mit Ihrer WindowsStoreProxy.xml-Datei auf den XML-Editor in Visual Studio anzuwenden, führen Sie folgende Schritteaus:</span><span class="sxs-lookup"><span data-stu-id="5f7b7-160">To apply this schema to the XML editor in Visual Studio when working with your WindowsStoreProxy.xml file, do the following:</span></span>

1. <span data-ttu-id="5f7b7-161">Öffnen Sie die WindowsStoreProxy.xml-Datei in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-161">Open the WindowsStoreProxy.xml file in Visual Studio.</span></span>
2. <span data-ttu-id="5f7b7-162">Klicken Sie im Menü **XML** auf **Schema erstellen**.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-162">On the **XML** menu, click **Create Schema**.</span></span> <span data-ttu-id="5f7b7-163">Hierdurch wird eine temporäre WindowsStoreProxy.xsd-Datei auf Grundlage des Inhalts der XML-Datei erstellt.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-163">This will create a temporary WindowsStoreProxy.xsd file based on the contents of the XML file.</span></span>
3. <span data-ttu-id="5f7b7-164">Ersetzen Sie den Inhalt dieser XSD-Datei durch das folgende Schema.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-164">Replace the contents of that .xsd file with the schema below.</span></span>
4. <span data-ttu-id="5f7b7-165">Speichern Sie die Datei an einem Ort, an dem Sie sie auf mehrere App-Projekte anwenden können.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-165">Save the file to a location where you can apply it to multiple app projects.</span></span>
5. <span data-ttu-id="5f7b7-166">Wechseln Sie zur WindowsStoreProxy.xml-Datei in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-166">Switch to your WindowsStoreProxy.xml file in Visual Studio.</span></span>
6. <span data-ttu-id="5f7b7-167">Klicken Sie im Menü **XML** auf **Schemas**, und suchen Sie die Zeile in der Liste für die WindowsStoreProxy.xsd-Datei.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-167">On the **XML** menu, click **Schemas**, then locate the row in the list for the WindowsStoreProxy.xsd file.</span></span> <span data-ttu-id="5f7b7-168">Wenn der Speicherort der Datei nicht der gewünschte ist (wenn beispielsweise die temporäre Datei weiterhin angezeigt wird), klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-168">If the location for the file is not the one you want (for example, if the temporary file is still shown), click **Add**.</span></span> <span data-ttu-id="5f7b7-169">Navigieren Sie zur richtigen Datei, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-169">Navigate to the right file, then click **OK**.</span></span> <span data-ttu-id="5f7b7-170">Nun sollte Ihnen diese Datei in der Liste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-170">You should now see that file in the list.</span></span> <span data-ttu-id="5f7b7-171">Stellen Sie sicher, dass in der Spalte **Verwenden** für dieses Schema ein Häkchen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-171">Make sure a checkmark appears in the **Use** column for that schema.</span></span>

<span data-ttu-id="5f7b7-172">Anschließend unterliegen Ihre Bearbeitungen der WindowsStoreProxy.xml-Datei dem Schema.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-172">Once you've done this, edits you make to WindowsStoreProxy.xml will be subject to the schema.</span></span> <span data-ttu-id="5f7b7-173">Weitere Informationen finden Sie unter [So wählen Sie die zu verwendenden XML-Schemas aus](http://go.microsoft.com/fwlink/p/?LinkId=403014).</span><span class="sxs-lookup"><span data-stu-id="5f7b7-173">For more information, see [How to: Select the XML Schemas to Use](http://go.microsoft.com/fwlink/p/?LinkId=403014).</span></span>

> [!div class="tabbedCodeSnippets"]
```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:import namespace="http://www.w3.org/XML/1998/namespace"/>
  <xs:element name="CurrentApp" type="CurrentAppDefinition"></xs:element>
  <xs:complexType name="CurrentAppDefinition">
    <xs:sequence>
      <xs:element name="ListingInformation" type="ListingDefinition" minOccurs="1" maxOccurs="1"/>
      <xs:element name="LicenseInformation" type="LicenseDefinition" minOccurs="1" maxOccurs="1"/>
      <xs:element name="ConsumableInformation" type="ConsumableDefinition" minOccurs="0" maxOccurs="1"/>
      <xs:element name="Simulation" type="SimulationDefinition" minOccurs="0" maxOccurs="1"/>
    </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="ResponseCodes">
    <xs:restriction base="xs:string">
      <xs:enumeration value="S_OK">
        <xs:annotation>
          <xs:documentation>0x00000000</xs:documentation>
        </xs:annotation>
      </xs:enumeration>
      <xs:enumeration value="E_INVALIDARG">
        <xs:annotation>
          <xs:documentation>0x80070057</xs:documentation>
        </xs:annotation>
      </xs:enumeration>
      <xs:enumeration value="E_CANCELLED">
        <xs:annotation>
          <xs:documentation>0x800704C7</xs:documentation>
        </xs:annotation>
      </xs:enumeration>
      <xs:enumeration value="E_FAIL">
        <xs:annotation>
          <xs:documentation>0x80004005</xs:documentation>
        </xs:annotation>
      </xs:enumeration>
      <xs:enumeration value="E_OUTOFMEMORY">
        <xs:annotation>
          <xs:documentation>0x8007000E</xs:documentation>
        </xs:annotation>
      </xs:enumeration>
      <xs:enumeration value="ERROR_ALREADY_EXISTS">
        <xs:annotation>
          <xs:documentation>0x800700B7</xs:documentation>
        </xs:annotation>
      </xs:enumeration>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="ConsumableStatus">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Active"/>
      <xs:enumeration value="PurchaseReverted"/>
      <xs:enumeration value="PurchasePending"/>
      <xs:enumeration value="ServerError"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="StoreMethodName">
    <xs:restriction base="xs:string">
      <xs:enumeration value="RequestAppPurchaseAsync_GetResult" id="RPPA"/>
      <xs:enumeration value="RequestProductPurchaseAsync_GetResult" id="RFPA"/>
      <xs:enumeration value="LoadListingInformationAsync_GetResult" id="LLIA"/>
      <xs:enumeration value="ReportConsumableFulfillmentAsync_GetResult" id="RPFA"/>
      <xs:enumeration value="LoadListingInformationByKeywordsAsync_GetResult" id="LLIKA"/>
      <xs:enumeration value="LoadListingInformationByProductIdAsync_GetResult" id="LLIPA"/>
      <xs:enumeration value="GetUnfulfilledConsumablesAsync_GetResult" id="GUC"/>
      <xs:enumeration value="GetAppReceiptAsync_GetResult" id="GARA"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="SimulationMode">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Interactive"/>
      <xs:enumeration value="Automatic"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="ListingDefinition">
    <xs:sequence>
      <xs:element name="App" type="AppListingDefinition"/>
      <xs:element name="Product" type="ProductListingDefinition" minOccurs="0" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="ConsumableDefinition">
    <xs:sequence>
      <xs:element name="Product" type="ConsumableProductDefinition" minOccurs="0" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="AppListingDefinition">
    <xs:sequence>
      <xs:element name="AppId" type="xs:string" minOccurs="1" maxOccurs="1"/>
      <xs:element name="LinkUri" type="xs:anyURI" minOccurs="1" maxOccurs="1"/>
      <xs:element name="CurrentMarket" type="xs:language" minOccurs="1" maxOccurs="1"/>
      <xs:element name="AgeRating" type="xs:unsignedInt" minOccurs="1" maxOccurs="1"/>
      <xs:element name="MarketData" type="MarketSpecificAppData" minOccurs="1" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="MarketSpecificAppData">
    <xs:sequence>
      <xs:element name="Name" type="xs:string" minOccurs="1" maxOccurs="1"/>
      <xs:element name="Description" type="xs:string" minOccurs="1" maxOccurs="1"/>
      <xs:element name="Price" type="xs:float" minOccurs="1" maxOccurs="1"/>
      <xs:element name="CurrencySymbol" type="xs:string" minOccurs="1" maxOccurs="1"/>
      <xs:element name="CurrencyCode" type="xs:string" minOccurs="0" maxOccurs="1"/>
    </xs:sequence>
    <xs:attribute ref="xml:lang" use="required"/>
  </xs:complexType>
  <xs:complexType name="MarketSpecificProductData">
    <xs:sequence>
      <xs:element name="Name" type="xs:string" minOccurs="1" maxOccurs="1"/>
      <xs:element name="Price" type="xs:float" minOccurs="1" maxOccurs="1"/>
      <xs:element name="CurrencySymbol" type="xs:string" minOccurs="1" maxOccurs="1"/>
      <xs:element name="CurrencyCode" type="xs:string" minOccurs="0" maxOccurs="1"/>
      <xs:element name="Description" type="xs:string" minOccurs="0" maxOccurs="1"/>
      <xs:element name="Tag" type="xs:string" minOccurs="0" maxOccurs="1"/>
      <xs:element name="Keywords" type="KeywordDefinition" minOccurs="0" maxOccurs="1"/>
      <xs:element name="ImageUri" type="xs:anyURI" minOccurs="0" maxOccurs="1"/>
    </xs:sequence>
    <xs:attribute ref="xml:lang" use="required"/>
  </xs:complexType>
  <xs:complexType name="ProductListingDefinition">
    <xs:sequence>
      <xs:element name="MarketData" type="MarketSpecificProductData" minOccurs="1" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="ProductId" use="required">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:maxLength value="100"/>
          <xs:pattern value="[^,]*"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
    <xs:attribute name="LicenseDuration" type="xs:integer" use="optional"/>
    <xs:attribute name="ProductType" type="xs:string" use="optional"/>
  </xs:complexType>
  <xs:simpleType name="guid">
    <xs:restriction base="xs:string">
      <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="ConsumableProductDefinition">
    <xs:attribute name="ProductId" use="required">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:maxLength value="100"/>
          <xs:pattern value="[^,]*"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
    <xs:attribute name="TransactionId" type="guid" use="required"/>
    <xs:attribute name="Status" type="ConsumableStatus" use="required"/>
    <xs:attribute name="OfferId" type="xs:string" use="optional"/>
  </xs:complexType>
  <xs:complexType name="LicenseDefinition">
    <xs:sequence>
      <xs:element name="App" type="AppLicenseDefinition"/>
      <xs:element name="Product" type="ProductLicenseDefinition" minOccurs="0" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="AppLicenseDefinition">
    <xs:sequence>
      <xs:element name="IsActive" type="xs:boolean" minOccurs="1" maxOccurs="1"/>
      <xs:element name="IsTrial" type="xs:boolean" minOccurs="1" maxOccurs="1"/>
      <xs:element name="ExpirationDate" type="xs:dateTime" minOccurs="0" maxOccurs="1"/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="ProductLicenseDefinition">
    <xs:sequence>
      <xs:element name="IsActive" type="xs:boolean" minOccurs="1" maxOccurs="1"/>
      <xs:element name="ExpirationDate" type="xs:dateTime" minOccurs="0" maxOccurs="1"/>
    </xs:sequence>
    <xs:attribute name="ProductId" type="xs:string" use="required"/>
    <xs:attribute name="OfferId" type="xs:string" use="optional"/>
  </xs:complexType>
  <xs:complexType name="SimulationDefinition" >
    <xs:sequence>
      <xs:element name="DefaultResponse" type="DefaultResponseDefinition" minOccurs="0" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="SimulationMode" type="SimulationMode" use="optional"/>
  </xs:complexType>
  <xs:complexType name="DefaultResponseDefinition">
    <xs:attribute name="MethodName" type="StoreMethodName" use="required"/>
    <xs:attribute name="HResult" type="ResponseCodes" use="required"/>
  </xs:complexType>
  <xs:complexType name="KeywordDefinition">
    <xs:sequence>
      <xs:element name="Keyword" type="xs:string" minOccurs="0" maxOccurs="10"/>
    </xs:sequence>
  </xs:complexType>
</xs:schema>
```


<span id="proxy-descriptions" />

### <a name="element-and-attribute-descriptions"></a><span data-ttu-id="5f7b7-174">Element- und Attributbeschreibungen</span><span class="sxs-lookup"><span data-stu-id="5f7b7-174">Element and attribute descriptions</span></span>

<span data-ttu-id="5f7b7-175">In diesem Abschnitt werden die Elemente und Attribute in der WindowsStoreProxy.xml-Datei beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-175">This section describes the elements and attributes in the WindowsStoreProxy.xml file.</span></span>

<span data-ttu-id="5f7b7-176">Das Stammelement dieser Datei ist das **CurrentApp**-Element, das die aktuelle App darstellt.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-176">The root element of this file is the **CurrentApp** element, which represents the current app.</span></span> <span data-ttu-id="5f7b7-177">Dieses Element enthält die folgenden untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-177">This element contains the following child elements.</span></span>

|  <span data-ttu-id="5f7b7-178">Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-178">Element</span></span>  |  <span data-ttu-id="5f7b7-179">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-179">Required</span></span>  |  <span data-ttu-id="5f7b7-180">Menge</span><span class="sxs-lookup"><span data-stu-id="5f7b7-180">Quantity</span></span>  |  <span data-ttu-id="5f7b7-181">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-181">Description</span></span>   |
|-------------|------------|--------|--------|
|  [<span data-ttu-id="5f7b7-182">ListingInformation</span><span class="sxs-lookup"><span data-stu-id="5f7b7-182">ListingInformation</span></span>](#listinginformation)  |    <span data-ttu-id="5f7b7-183">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-183">Yes</span></span>        |  <span data-ttu-id="5f7b7-184">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-184">1</span></span>  |  <span data-ttu-id="5f7b7-185">Enthält Daten aus dem App Eintrag.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-185">Contains data from the app's listing.</span></span>            |
|  [<span data-ttu-id="5f7b7-186">LicenseInformation</span><span class="sxs-lookup"><span data-stu-id="5f7b7-186">LicenseInformation</span></span>](#licenseinformation)  |     <span data-ttu-id="5f7b7-187">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-187">Yes</span></span>       |   <span data-ttu-id="5f7b7-188">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-188">1</span></span>    |   <span data-ttu-id="5f7b7-189">Beschreibt die Lizenzen, die für diese App verfügbar sind, und ihre dauerhaften Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-189">Describes the licenses available for this app and its durable add-ons.</span></span>     |
|  [<span data-ttu-id="5f7b7-190">ConsumableInformation</span><span class="sxs-lookup"><span data-stu-id="5f7b7-190">ConsumableInformation</span></span>](#consumableinformation)  |      <span data-ttu-id="5f7b7-191">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-191">No</span></span>      |   <span data-ttu-id="5f7b7-192">0 oder 1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-192">0 or 1</span></span>   |   <span data-ttu-id="5f7b7-193">Beschreibt die konsumierbaren Add-Ons, die für diese App verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-193">Describes the consumable add-ons that are available for this app.</span></span>      |
|  [<span data-ttu-id="5f7b7-194">Simulation</span><span class="sxs-lookup"><span data-stu-id="5f7b7-194">Simulation</span></span>](#simulation)  |     <span data-ttu-id="5f7b7-195">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-195">No</span></span>       |      <span data-ttu-id="5f7b7-196">0 oder 1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-196">0 or 1</span></span>      |   <span data-ttu-id="5f7b7-197">Beschreibt, wie Aufrufe verschiedener [CurrentAppSimulator](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentappsimulator.aspx)-Methoden während der Testphase in der App funktionieren.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-197">Describes how calls to various [CurrentAppSimulator](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentappsimulator.aspx) methods will work in the app during testing.</span></span>    |

<span id="listinginformation" />

#### <a name="listinginformation-element"></a><span data-ttu-id="5f7b7-198">ListingInformation-Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-198">ListingInformation element</span></span>

<span data-ttu-id="5f7b7-199">Dieses Element enthält Daten aus dem App Eintrag.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-199">This element contains data from the app's listing.</span></span> <span data-ttu-id="5f7b7-200">**ListingInformation** ist ein erforderliches untergeordnetes Element des **CurrentApp**-Elements.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-200">**ListingInformation** is a required child of the **CurrentApp** element.</span></span>

<span data-ttu-id="5f7b7-201">**ListingInformation** enthält die folgenden untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-201">**ListingInformation** contains the following child elements.</span></span>

|  <span data-ttu-id="5f7b7-202">Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-202">Element</span></span>  |  <span data-ttu-id="5f7b7-203">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-203">Required</span></span>  |  <span data-ttu-id="5f7b7-204">Menge</span><span class="sxs-lookup"><span data-stu-id="5f7b7-204">Quantity</span></span>  |  <span data-ttu-id="5f7b7-205">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-205">Description</span></span>   |
|-------------|------------|--------|--------|
|  [<span data-ttu-id="5f7b7-206">App</span><span class="sxs-lookup"><span data-stu-id="5f7b7-206">App</span></span>](#app-child-of-listinginformation)  |    <span data-ttu-id="5f7b7-207">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-207">Yes</span></span>   |  <span data-ttu-id="5f7b7-208">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-208">1</span></span>   |    <span data-ttu-id="5f7b7-209">Stellt Daten zur App bereit.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-209">Provides data about the app.</span></span>         |
|  [<span data-ttu-id="5f7b7-210">Product</span><span class="sxs-lookup"><span data-stu-id="5f7b7-210">Product</span></span>](#product-child-of-listinginformation)  |    <span data-ttu-id="5f7b7-211">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-211">No</span></span>  |  <span data-ttu-id="5f7b7-212">0 oder mehr</span><span class="sxs-lookup"><span data-stu-id="5f7b7-212">0 or more</span></span>   |      <span data-ttu-id="5f7b7-213">Beschreibt ein Add-On für die App.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-213">Describes an add-on for the app.</span></span>     |     |

<span id="app-child-of-listinginformation"/>

#### <a name="app-element-child-of-listinginformation"></a><span data-ttu-id="5f7b7-214">App-Element (untergeordnetes Element von ListingInformation)</span><span class="sxs-lookup"><span data-stu-id="5f7b7-214">App element (child of ListingInformation)</span></span>

<span data-ttu-id="5f7b7-215">Dieses Element beschreibt die App-Lizenz.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-215">This element describes the app's license.</span></span> <span data-ttu-id="5f7b7-216">**App** ist ein erforderliches untergeordnetes Element des [ListingInformation](#listinginformation)-Elements.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-216">**App** is a required child of the [ListingInformation](#listinginformation) element.</span></span>

<span data-ttu-id="5f7b7-217">**App** enthält die folgenden untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-217">**App** contains the following child elements.</span></span>

|  <span data-ttu-id="5f7b7-218">Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-218">Element</span></span>  |  <span data-ttu-id="5f7b7-219">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-219">Required</span></span>  |  <span data-ttu-id="5f7b7-220">Menge</span><span class="sxs-lookup"><span data-stu-id="5f7b7-220">Quantity</span></span>  | <span data-ttu-id="5f7b7-221">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-221">Description</span></span>   |
|-------------|------------|--------|--------|
|  **<span data-ttu-id="5f7b7-222">AppId</span><span class="sxs-lookup"><span data-stu-id="5f7b7-222">AppId</span></span>**  |    <span data-ttu-id="5f7b7-223">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-223">Yes</span></span>   |  <span data-ttu-id="5f7b7-224">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-224">1</span></span>   |   <span data-ttu-id="5f7b7-225">Die GUID, die die App im Store identifiziert.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-225">The GUID that identifies the app in the Store.</span></span> <span data-ttu-id="5f7b7-226">Dies kann eine beliebige GUID für Tests sein.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-226">This can be any GUID for testing.</span></span>        |
|  **<span data-ttu-id="5f7b7-227">LinkUri</span><span class="sxs-lookup"><span data-stu-id="5f7b7-227">LinkUri</span></span>**  |    <span data-ttu-id="5f7b7-228">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-228">Yes</span></span>  |  <span data-ttu-id="5f7b7-229">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-229">1</span></span>   |    <span data-ttu-id="5f7b7-230">Der URI der Eintragsseite im Store.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-230">The URI of the listing page in the store.</span></span> <span data-ttu-id="5f7b7-231">Dies kann ein beliebiger URI für Tests sein.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-231">This can be any valid URI for testing.</span></span>         |
|  **<span data-ttu-id="5f7b7-232">CurrentMarket</span><span class="sxs-lookup"><span data-stu-id="5f7b7-232">CurrentMarket</span></span>**  |    <span data-ttu-id="5f7b7-233">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-233">Yes</span></span>  |  <span data-ttu-id="5f7b7-234">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-234">1</span></span>   |    <span data-ttu-id="5f7b7-235">Das Land/die Region des Kunden.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-235">The customer's country/region.</span></span>         |
|  **<span data-ttu-id="5f7b7-236">AgeRating</span><span class="sxs-lookup"><span data-stu-id="5f7b7-236">AgeRating</span></span>**  |    <span data-ttu-id="5f7b7-237">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-237">Yes</span></span>  |  <span data-ttu-id="5f7b7-238">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-238">1</span></span>   |     <span data-ttu-id="5f7b7-239">Eine ganze Zahl, die die Mindestaltersfreigabe der App darstellt.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-239">An integer that represents the minimum age rating of the app.</span></span> <span data-ttu-id="5f7b7-240">Dies ist derselbe Wert, den Sie im Partner Center angeben würden, wenn Sie die app übermitteln.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-240">This is the same value you would specify in Partner Center when you submit the app.</span></span> <span data-ttu-id="5f7b7-241">Die vom Store verwendeten Werte sind: 3, 7, 12 und 16.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-241">The values used by the Store are: 3, 7, 12, and 16.</span></span> <span data-ttu-id="5f7b7-242">Weitere Informationen zu diesen Bewertungen finden Sie unter [Altersfreigaben](../publish/age-ratings.md).</span><span class="sxs-lookup"><span data-stu-id="5f7b7-242">For more info on these ratings, see [Age ratings](../publish/age-ratings.md).</span></span>        |
|  [<span data-ttu-id="5f7b7-243">MarketData</span><span class="sxs-lookup"><span data-stu-id="5f7b7-243">MarketData</span></span>](#marketdata-child-of-app)  |    <span data-ttu-id="5f7b7-244">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-244">Yes</span></span>  |  <span data-ttu-id="5f7b7-245">1 oder mehr</span><span class="sxs-lookup"><span data-stu-id="5f7b7-245">1 or more</span></span>      |    <span data-ttu-id="5f7b7-246">Enthält Informationen über die App für ein bestimmtes Land oder eine bestimmte Region.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-246">Contains info about the app for a given country/region.</span></span> <span data-ttu-id="5f7b7-247">Für jedes Land/jede Region, in denen die App eingetragen ist, müssen Sie ein **MarketData**-Element einschließen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-247">For each country/region in which the app is listed, you must include a **MarketData** element.</span></span>       |    |

<span id="marketdata-child-of-app"/>

#### <a name="marketdata-element-child-of-app"></a><span data-ttu-id="5f7b7-248">MarketData-Element (untergeordnetes Element von App)</span><span class="sxs-lookup"><span data-stu-id="5f7b7-248">MarketData element (child of App)</span></span>

<span data-ttu-id="5f7b7-249">Dieses Element stellt Informationen zur App für ein bestimmtes Land oder eine bestimmte Region bereit.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-249">This element provides info about the app for a given country/region.</span></span> <span data-ttu-id="5f7b7-250">Für jedes Land/jede Region, in denen die App eingetragen ist, müssen Sie ein **MarketData**-Element einschließen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-250">For each country/region in which the app is listed, you must include a **MarketData** element.</span></span> <span data-ttu-id="5f7b7-251">**MarketData** ist ein erforderliches untergeordnetes Element des [App](#app-child-of-listinginformation)-Elements.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-251">**MarketData** is a required child of the [App](#app-child-of-listinginformation) element.</span></span>

<span data-ttu-id="5f7b7-252">**MarketData** enthält die folgenden untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-252">**MarketData** contains the following child elements.</span></span>

|  <span data-ttu-id="5f7b7-253">Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-253">Element</span></span>  |  <span data-ttu-id="5f7b7-254">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-254">Required</span></span>  |  <span data-ttu-id="5f7b7-255">Menge</span><span class="sxs-lookup"><span data-stu-id="5f7b7-255">Quantity</span></span>  | <span data-ttu-id="5f7b7-256">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-256">Description</span></span>   |
|-------------|------------|--------|--------|
|  **<span data-ttu-id="5f7b7-257">Name</span><span class="sxs-lookup"><span data-stu-id="5f7b7-257">Name</span></span>**  |    <span data-ttu-id="5f7b7-258">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-258">Yes</span></span>   |  <span data-ttu-id="5f7b7-259">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-259">1</span></span>   |   <span data-ttu-id="5f7b7-260">Der Name der App in diesem Land/dieser Region.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-260">The name of the app in this country/region.</span></span>        |
|  **<span data-ttu-id="5f7b7-261">Description</span><span class="sxs-lookup"><span data-stu-id="5f7b7-261">Description</span></span>**  |    <span data-ttu-id="5f7b7-262">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-262">Yes</span></span>  |  <span data-ttu-id="5f7b7-263">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-263">1</span></span>   |      <span data-ttu-id="5f7b7-264">Die Beschreibung der App für dieses Land/diese Region.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-264">The description of the app for this country/region.</span></span>       |
|  **<span data-ttu-id="5f7b7-265">Price</span><span class="sxs-lookup"><span data-stu-id="5f7b7-265">Price</span></span>**  |    <span data-ttu-id="5f7b7-266">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-266">Yes</span></span>  |  <span data-ttu-id="5f7b7-267">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-267">1</span></span>   |     <span data-ttu-id="5f7b7-268">Der Preis der App in diesem Land/dieser Region.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-268">The price of the app in this country/region.</span></span>        |
|  **<span data-ttu-id="5f7b7-269">CurrencySymbol</span><span class="sxs-lookup"><span data-stu-id="5f7b7-269">CurrencySymbol</span></span>**  |    <span data-ttu-id="5f7b7-270">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-270">Yes</span></span>  |  <span data-ttu-id="5f7b7-271">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-271">1</span></span>   |     <span data-ttu-id="5f7b7-272">Das Währungssymbol, das in diesem Land/dieser Region verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-272">The currency symbol used in this country/region.</span></span>        |
|  **<span data-ttu-id="5f7b7-273">CurrencyCode</span><span class="sxs-lookup"><span data-stu-id="5f7b7-273">CurrencyCode</span></span>**  |    <span data-ttu-id="5f7b7-274">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-274">No</span></span>  |  <span data-ttu-id="5f7b7-275">0 oder 1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-275">0 or 1</span></span>      |      <span data-ttu-id="5f7b7-276">Der Währungscode, der in diesem Land/dieser Region verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-276">The currency code used in this country/region.</span></span>         |  |

<span data-ttu-id="5f7b7-277">**MarketData** hat die folgenden Attribute.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-277">**MarketData** has the following attributes.</span></span>

|  <span data-ttu-id="5f7b7-278">Attribut</span><span class="sxs-lookup"><span data-stu-id="5f7b7-278">Attribute</span></span>  |  <span data-ttu-id="5f7b7-279">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-279">Required</span></span>  |  <span data-ttu-id="5f7b7-280">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-280">Description</span></span>   |
|-------------|------------|----------------|
|  **<span data-ttu-id="5f7b7-281">xml:lang</span><span class="sxs-lookup"><span data-stu-id="5f7b7-281">xml:lang</span></span>**  |    <span data-ttu-id="5f7b7-282">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-282">Yes</span></span>        |     <span data-ttu-id="5f7b7-283">Gibt das Land/die Region an, für das/die die Marktdateninformationen gelten.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-283">Specifies the country/region for which the market data info applies.</span></span>          |  |

<span id="product-child-of-listinginformation"/>

#### <a name="product-element-child-of-listinginformation"></a><span data-ttu-id="5f7b7-284">Produktelement (untergeordnetes Element von ListingInformation.)</span><span class="sxs-lookup"><span data-stu-id="5f7b7-284">Product element (child of ListingInformation)</span></span>

<span data-ttu-id="5f7b7-285">Dieses Element beschreibt ein Add-On für die App.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-285">This element describes an add-on for the app.</span></span> <span data-ttu-id="5f7b7-286">**Product** ist ein optionales untergeordnetes Element des [ListingInformation](#listinginformation) -Elements und enthält mindestens ein [MarketData](#marketdata-child-of-product)-Element.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-286">**Product** is an optional child of the [ListingInformation](#listinginformation) element, and it contains one or more [MarketData](#marketdata-child-of-product) elements.</span></span>

<span data-ttu-id="5f7b7-287">**Product** hat die folgenden Attribute.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-287">**Product** has the following attributes.</span></span>

|  <span data-ttu-id="5f7b7-288">Attribut</span><span class="sxs-lookup"><span data-stu-id="5f7b7-288">Attribute</span></span>  |  <span data-ttu-id="5f7b7-289">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-289">Required</span></span>  |  <span data-ttu-id="5f7b7-290">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-290">Description</span></span>   |
|-------------|------------|----------------|
|  **<span data-ttu-id="5f7b7-291">ProductId</span><span class="sxs-lookup"><span data-stu-id="5f7b7-291">ProductId</span></span>**  |    <span data-ttu-id="5f7b7-292">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-292">Yes</span></span>        |    <span data-ttu-id="5f7b7-293">Enthält die Zeichenfolge, die von der App zur Identifizierung des Add-Ons verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-293">Contains the string used by the app to identify the add-on.</span></span>           |
|  **<span data-ttu-id="5f7b7-294">LicenseDuration</span><span class="sxs-lookup"><span data-stu-id="5f7b7-294">LicenseDuration</span></span>**  |    <span data-ttu-id="5f7b7-295">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-295">No</span></span>        |    <span data-ttu-id="5f7b7-296">Gibt die Anzahl der Tage an, für die die Lizenz gültig sein wird, nachdem der Artikel gekauft wurde.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-296">Indicates the number of days for which the license will be valid after the item has been purchased.</span></span> <span data-ttu-id="5f7b7-297">Das Ablaufdatum der neuen, durch einen Produktkauf erstellten Lizenz ist das Kaufdatum plus Lizenzdauer.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-297">The expiration date of the new license created by a product purchase is the purchase date plus the license duration.</span></span> <span data-ttu-id="5f7b7-298">Dieses Attribut wird nur verwendet, wenn das **ProductType**-Attribut **Durable** ist. Dieses Attribut wird für konsumierbare Add-Ons ignoriert.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-298">This attribute is used only if the **ProductType** attribute is **Durable**; this attribute is ignored for consumable add-ons.</span></span>           |
|  **<span data-ttu-id="5f7b7-299">ProductType</span><span class="sxs-lookup"><span data-stu-id="5f7b7-299">ProductType</span></span>**  |    <span data-ttu-id="5f7b7-300">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-300">No</span></span>        |    <span data-ttu-id="5f7b7-301">Enthält einen Wert für die Identifizierung der Persistenz des In-App-Produkts.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-301">Contains a value to identify the persistence of the in-app product.</span></span> <span data-ttu-id="5f7b7-302">Die unterstützten Werte sind **Durable** (Standard) und **Consumable**.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-302">The supported values are **Durable** (the default) and **Consumable**.</span></span> <span data-ttu-id="5f7b7-303">Zusätzliche Informationen zu Typen dauerhafter Add-Ons werden durch ein [Product](#product-child-of-licenseinformation)-Element unter [LicenseInformation](#licenseinformation) beschrieben. Zusätzliche Informationen zu Typen konsumierbarer Add-Ons werden durch ein [Product](#product-child-of-consumableinformation)-Element unter [ConsumableInformation](#consumableinformation) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-303">For durable types, additional information is described by a [Product](#product-child-of-licenseinformation) element under [LicenseInformation](#licenseinformation); for consumable types, additional information is described by a [Product](#product-child-of-consumableinformation) element under [ConsumableInformation](#consumableinformation).</span></span>           |  |

<span id="marketdata-child-of-product"/>

#### <a name="marketdata-element-child-of-product"></a><span data-ttu-id="5f7b7-304">MarketData-Element (untergeordnetes Element von Product)</span><span class="sxs-lookup"><span data-stu-id="5f7b7-304">MarketData element (child of Product)</span></span>

<span data-ttu-id="5f7b7-305">Dieses Element stellt Informationen zum Add-On für ein bestimmtes Land oder eine bestimmte Region bereit.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-305">This element provides info about the add-on for a given country/region.</span></span> <span data-ttu-id="5f7b7-306">Für jedes Land/jede Region, in denen das Add-On eingetragen ist, müssen Sie ein **MarketData**-Element einschließen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-306">For each country/region in which the add-on is listed, you must include a **MarketData** element.</span></span> <span data-ttu-id="5f7b7-307">**MarketData** ist ein erforderliches untergeordnetes Element des [Product](#product-child-of-listinginformation)-Elements.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-307">**MarketData** is a required child of the [Product](#product-child-of-listinginformation) element.</span></span>

<span data-ttu-id="5f7b7-308">**MarketData** enthält die folgenden untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-308">**MarketData** contains the following child elements.</span></span>

|  <span data-ttu-id="5f7b7-309">Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-309">Element</span></span>  |  <span data-ttu-id="5f7b7-310">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-310">Required</span></span>  |  <span data-ttu-id="5f7b7-311">Menge</span><span class="sxs-lookup"><span data-stu-id="5f7b7-311">Quantity</span></span>  | <span data-ttu-id="5f7b7-312">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-312">Description</span></span>   |
|-------------|------------|--------|--------|
|  **<span data-ttu-id="5f7b7-313">Name</span><span class="sxs-lookup"><span data-stu-id="5f7b7-313">Name</span></span>**  |    <span data-ttu-id="5f7b7-314">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-314">Yes</span></span>   |  <span data-ttu-id="5f7b7-315">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-315">1</span></span>   |   <span data-ttu-id="5f7b7-316">Der Name des Add-Ons in diesem Land/dieser Region.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-316">The name of the add-on in this country/region.</span></span>        |
|  **<span data-ttu-id="5f7b7-317">Price</span><span class="sxs-lookup"><span data-stu-id="5f7b7-317">Price</span></span>**  |    <span data-ttu-id="5f7b7-318">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-318">Yes</span></span>  |  <span data-ttu-id="5f7b7-319">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-319">1</span></span>   |     <span data-ttu-id="5f7b7-320">Der Preis des Add-Ons in diesem Land/dieser Region.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-320">The price of the add-on in this country/region.</span></span>        |
|  **<span data-ttu-id="5f7b7-321">CurrencySymbol</span><span class="sxs-lookup"><span data-stu-id="5f7b7-321">CurrencySymbol</span></span>**  |    <span data-ttu-id="5f7b7-322">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-322">Yes</span></span>  |  <span data-ttu-id="5f7b7-323">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-323">1</span></span>   |     <span data-ttu-id="5f7b7-324">Das Währungssymbol, das in diesem Land/dieser Region verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-324">The currency symbol used in this country/region.</span></span>        |
|  **<span data-ttu-id="5f7b7-325">CurrencyCode</span><span class="sxs-lookup"><span data-stu-id="5f7b7-325">CurrencyCode</span></span>**  |    <span data-ttu-id="5f7b7-326">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-326">No</span></span>  |  <span data-ttu-id="5f7b7-327">0 oder 1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-327">0 or 1</span></span>      |      <span data-ttu-id="5f7b7-328">Der Währungscode, der in diesem Land/dieser Region verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-328">The currency code used in this country/region.</span></span>         |  
|  **<span data-ttu-id="5f7b7-329">Description</span><span class="sxs-lookup"><span data-stu-id="5f7b7-329">Description</span></span>**  |    <span data-ttu-id="5f7b7-330">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-330">No</span></span>  |   <span data-ttu-id="5f7b7-331">0 oder 1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-331">0 or 1</span></span>   |      <span data-ttu-id="5f7b7-332">Die Beschreibung des Add-Ons für dieses Land/diese Region.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-332">The description of the add-on for this country/region.</span></span>       |
|  **<span data-ttu-id="5f7b7-333">Tag</span><span class="sxs-lookup"><span data-stu-id="5f7b7-333">Tag</span></span>**  |    <span data-ttu-id="5f7b7-334">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-334">No</span></span>  |   <span data-ttu-id="5f7b7-335">0 oder 1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-335">0 or 1</span></span>   |      <span data-ttu-id="5f7b7-336">Die [benutzerdefinierten Daten](../publish/enter-add-on-properties.md#custom-developer-data) (auch als „Tag“ bezeichnet) für das Add-On.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-336">The [custom developer data](../publish/enter-add-on-properties.md#custom-developer-data) (also called tag) for the add-on.</span></span>       |
|  **<span data-ttu-id="5f7b7-337">Keywords</span><span class="sxs-lookup"><span data-stu-id="5f7b7-337">Keywords</span></span>**  |    <span data-ttu-id="5f7b7-338">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-338">No</span></span>  |   <span data-ttu-id="5f7b7-339">0 oder 1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-339">0 or 1</span></span>   |      <span data-ttu-id="5f7b7-340">Enthält bis zu 10 **Keyword**-Elemente, die die [Schlüsselwörter](../publish/enter-add-on-properties.md#keywords) für das Add-On enthalten.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-340">Contains up to 10 **Keyword** elements that contain the [keywords](../publish/enter-add-on-properties.md#keywords) for the add-on.</span></span>       |
|  **<span data-ttu-id="5f7b7-341">ImageUri</span><span class="sxs-lookup"><span data-stu-id="5f7b7-341">ImageUri</span></span>**  |    <span data-ttu-id="5f7b7-342">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-342">No</span></span>  |   <span data-ttu-id="5f7b7-343">0 oder 1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-343">0 or 1</span></span>   |      <span data-ttu-id="5f7b7-344">Der [URI für das Bild](../publish/create-add-on-store-listings.md#icon) im Add-On-Eintrag.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-344">The [URI for the image](../publish/create-add-on-store-listings.md#icon) in the add-on's listing.</span></span>           |  |

<span data-ttu-id="5f7b7-345">**MarketData** hat die folgenden Attribute.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-345">**MarketData** has the following attributes.</span></span>

|  <span data-ttu-id="5f7b7-346">Attribut</span><span class="sxs-lookup"><span data-stu-id="5f7b7-346">Attribute</span></span>  |  <span data-ttu-id="5f7b7-347">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-347">Required</span></span>  |  <span data-ttu-id="5f7b7-348">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-348">Description</span></span>   |
|-------------|------------|----------------|
|  **<span data-ttu-id="5f7b7-349">xml:lang</span><span class="sxs-lookup"><span data-stu-id="5f7b7-349">xml:lang</span></span>**  |    <span data-ttu-id="5f7b7-350">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-350">Yes</span></span>        |     <span data-ttu-id="5f7b7-351">Gibt das Land/die Region an, für das/die die Marktdateninformationen gelten.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-351">Specifies the country/region for which the market data info applies.</span></span>          |  |

<span id="licenseinformation"/>

#### <a name="licenseinformation-element"></a><span data-ttu-id="5f7b7-352">LicenseInformation-Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-352">LicenseInformation element</span></span>

<span data-ttu-id="5f7b7-353">Dieses Element beschreibt die Lizenzen, die für diese App und deren dauerhafte In-App-Produkte verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-353">This element describes the licenses available for this app and its durable in-app products.</span></span> <span data-ttu-id="5f7b7-354">**LicenseInformation** ist ein erforderliches untergeordnetes Element des **CurrentApp**-Elements.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-354">**LicenseInformation** is a required child of the **CurrentApp** element.</span></span>

<span data-ttu-id="5f7b7-355">**LicenseInformation** enthält die folgenden untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-355">**LicenseInformation** contains the following child elements.</span></span>

|  <span data-ttu-id="5f7b7-356">Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-356">Element</span></span>  |  <span data-ttu-id="5f7b7-357">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-357">Required</span></span>  |  <span data-ttu-id="5f7b7-358">Menge</span><span class="sxs-lookup"><span data-stu-id="5f7b7-358">Quantity</span></span>  | <span data-ttu-id="5f7b7-359">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-359">Description</span></span>   |
|-------------|------------|--------|--------|
|  [<span data-ttu-id="5f7b7-360">App</span><span class="sxs-lookup"><span data-stu-id="5f7b7-360">App</span></span>](#app-child-of-licenseinformation)  |    <span data-ttu-id="5f7b7-361">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-361">Yes</span></span>   |  <span data-ttu-id="5f7b7-362">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-362">1</span></span>   |    <span data-ttu-id="5f7b7-363">Beschreibt die App-Lizenz.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-363">Describes the app's license.</span></span>         |
|  [<span data-ttu-id="5f7b7-364">Product</span><span class="sxs-lookup"><span data-stu-id="5f7b7-364">Product</span></span>](#product-child-of-licenseinformation)  |    <span data-ttu-id="5f7b7-365">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-365">No</span></span>  |  <span data-ttu-id="5f7b7-366">0 oder mehr</span><span class="sxs-lookup"><span data-stu-id="5f7b7-366">0 or more</span></span>   |      <span data-ttu-id="5f7b7-367">Beschreibt den Lizenzstatus eines dauerhaften Add-Ons in der App.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-367">Describes the license status of a durable add-on in the app.</span></span>         |   |

<span data-ttu-id="5f7b7-368">Die folgende Tabelle zeigt, wie Sie einige häufige Bedingungen simulieren, indem Sie Werte unter den Elementen **App** und **Product** kombinieren.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-368">The following table shows how to simulate some common conditions by combining values under the **App** and **Product** elements.</span></span>

|  <span data-ttu-id="5f7b7-369">Zu simulierende Bedingung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-369">Condition to simulate</span></span>  |  <span data-ttu-id="5f7b7-370">IsActive</span><span class="sxs-lookup"><span data-stu-id="5f7b7-370">IsActive</span></span>  |  <span data-ttu-id="5f7b7-371">IsTrial</span><span class="sxs-lookup"><span data-stu-id="5f7b7-371">IsTrial</span></span>  | <span data-ttu-id="5f7b7-372">ExpirationDate</span><span class="sxs-lookup"><span data-stu-id="5f7b7-372">ExpirationDate</span></span>   |
|-------------|------------|--------|--------|
|  <span data-ttu-id="5f7b7-373">Vollständig lizenziert</span><span class="sxs-lookup"><span data-stu-id="5f7b7-373">Fully licensed</span></span>  |    <span data-ttu-id="5f7b7-374">true</span><span class="sxs-lookup"><span data-stu-id="5f7b7-374">true</span></span>   |  <span data-ttu-id="5f7b7-375">false</span><span class="sxs-lookup"><span data-stu-id="5f7b7-375">false</span></span>  |    <span data-ttu-id="5f7b7-376">Nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-376">Absent.</span></span> <span data-ttu-id="5f7b7-377">Es kann vorhanden sein und ein späteres Datum angeben. Es wird jedoch empfohlen, das Element nicht in die XML-Datei einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-377">It actually may be present and specify a future date, but you're advised to omit the element from the XML file.</span></span> <span data-ttu-id="5f7b7-378">Wenn es vorhanden ist und ein Datum in der Vergangenheit angibt, wird **IsActive** ignoriert und als „false“ bewertet.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-378">If it is present and specifies a date in the past, then **IsActive** will be ignored and taken to be false.</span></span>          |
|  <span data-ttu-id="5f7b7-379">Im Testzeitraum</span><span class="sxs-lookup"><span data-stu-id="5f7b7-379">In trial period</span></span>  |    <span data-ttu-id="5f7b7-380">true</span><span class="sxs-lookup"><span data-stu-id="5f7b7-380">true</span></span>  |  <span data-ttu-id="5f7b7-381">true</span><span class="sxs-lookup"><span data-stu-id="5f7b7-381">true</span></span>   |      <span data-ttu-id="5f7b7-382">&lt;Datum/Uhrzeit in der Zukunft&gt; Dieses Element muss vorhanden sein, da **IsTrial** Wahr ist.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-382">&lt;a datetime in the future&gt; This element must be present because **IsTrial** is true.</span></span> <span data-ttu-id="5f7b7-383">Sie können eine Website aufrufen, die die aktuelle koordinierte Weltzeit (UTC) anzeigt, um festzustellen, auf wie weit in der Zukunft dies festgelegt werden muss, um den gewünschten verbleibenden Testzeitraum zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-383">You can visit a website showing the current Coordinated Universal Time (UTC) to know how far in the future to set this to get the remaining trial period you want.</span></span>         |
|  <span data-ttu-id="5f7b7-384">Abgelaufene Testversion</span><span class="sxs-lookup"><span data-stu-id="5f7b7-384">Expired trial</span></span>  |    <span data-ttu-id="5f7b7-385">false</span><span class="sxs-lookup"><span data-stu-id="5f7b7-385">false</span></span>  |  <span data-ttu-id="5f7b7-386">true</span><span class="sxs-lookup"><span data-stu-id="5f7b7-386">true</span></span>   |      <span data-ttu-id="5f7b7-387">&lt;Datum/Uhrzeit in der Vergangenheit&gt; Dieses Element muss vorhanden sein, da **IsTrial** Wahr ist.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-387">&lt;a datetime in the past&gt; This element must be present because **IsTrial** is true.</span></span> <span data-ttu-id="5f7b7-388">Sie können eine Website aufrufen, die die aktuelle koordinierte Weltzeit (UTC) anzeigt, um festzustellen, was in UTC Vergangenheit ist.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-388">You can visit a website showing the current Coordinated Universal Time (UTC) to know when "the past" is in UTC.</span></span>         |
|  <span data-ttu-id="5f7b7-389">Ungültig</span><span class="sxs-lookup"><span data-stu-id="5f7b7-389">Invalid</span></span>  |    <span data-ttu-id="5f7b7-390">false</span><span class="sxs-lookup"><span data-stu-id="5f7b7-390">false</span></span>  | <span data-ttu-id="5f7b7-391">false</span><span class="sxs-lookup"><span data-stu-id="5f7b7-391">false</span></span>       |     <span data-ttu-id="5f7b7-392">&lt;Jeder Wert oder ausgelassen&gt;</span><span class="sxs-lookup"><span data-stu-id="5f7b7-392">&lt;any value or omitted&gt;</span></span>          |  |

<span id="app-child-of-licenseinformation"/>

#### <a name="app-element-child-of-licenseinformation"></a><span data-ttu-id="5f7b7-393">App-Element (untergeordnetes Element von LicenseInformation)</span><span class="sxs-lookup"><span data-stu-id="5f7b7-393">App element (child of LicenseInformation)</span></span>

<span data-ttu-id="5f7b7-394">Dieses Element beschreibt die App-Lizenz.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-394">This element describes the app's license.</span></span> <span data-ttu-id="5f7b7-395">**App** ist ein erforderliches untergeordnetes Element des [LicenseInformation](#licenseinformation)-Elements.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-395">**App** is a required child of the [LicenseInformation](#licenseinformation) element.</span></span>

<span data-ttu-id="5f7b7-396">**App** enthält die folgenden untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-396">**App** contains the following child elements.</span></span>

|  <span data-ttu-id="5f7b7-397">Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-397">Element</span></span>  |  <span data-ttu-id="5f7b7-398">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-398">Required</span></span>  |  <span data-ttu-id="5f7b7-399">Menge</span><span class="sxs-lookup"><span data-stu-id="5f7b7-399">Quantity</span></span>  | <span data-ttu-id="5f7b7-400">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-400">Description</span></span>   |
|-------------|------------|--------|--------|
|  **<span data-ttu-id="5f7b7-401">IsActive</span><span class="sxs-lookup"><span data-stu-id="5f7b7-401">IsActive</span></span>**  |    <span data-ttu-id="5f7b7-402">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-402">Yes</span></span>   |  <span data-ttu-id="5f7b7-403">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-403">1</span></span>   |    <span data-ttu-id="5f7b7-404">Beschreibt den aktuellen Lizenzstatus der App.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-404">Describes the current license state of this app.</span></span> <span data-ttu-id="5f7b7-405">Der Wert **true** gibt an, dass die Lizenz gültig ist. Der Wert **false** gibt an, dass die Lizenz ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-405">The value **true** indicates the license is valid; **false** indicates an invalid license.</span></span> <span data-ttu-id="5f7b7-406">Normalerweise lautet dieser Wert **true**, unabhängig davon, ob die App einen Testmodus hat oder nicht.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-406">Normally this value is **true**, whether the app has a trial mode or not.</span></span>  <span data-ttu-id="5f7b7-407">Legen Sie diesen Wert auf **false** fest, um zu testen, wie sich Ihre App verhält, wenn die Lizenz ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-407">Set this value to **false** to test how your app behaves when it has an invalid license.</span></span>           |
|  **<span data-ttu-id="5f7b7-408">IsTrial</span><span class="sxs-lookup"><span data-stu-id="5f7b7-408">IsTrial</span></span>**  |    <span data-ttu-id="5f7b7-409">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-409">Yes</span></span>  |  <span data-ttu-id="5f7b7-410">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-410">1</span></span>   |      <span data-ttu-id="5f7b7-411">Beschreibt den aktuellen Testversionsstatus der App.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-411">Describes the current trial state of this app.</span></span> <span data-ttu-id="5f7b7-412">Der Wert **true** gibt an, dass die App während des Testzeitraums verwendet wird. Der Wert **false** gibt an, dass die App keine Testversion ist, entweder weil die App gekauft wurde oder weil der Testzeitraum abgelaufen ist.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-412">The value **true** indicates the app is being used during the trial period; **false** indicates the app is not in a trial, either because the app has been purchased or the trial period has expired.</span></span>         |
|  **<span data-ttu-id="5f7b7-413">ExpirationDate</span><span class="sxs-lookup"><span data-stu-id="5f7b7-413">ExpirationDate</span></span>**  |    <span data-ttu-id="5f7b7-414">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-414">No</span></span>  |  <span data-ttu-id="5f7b7-415">0 oder 1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-415">0 or 1</span></span>       |     <span data-ttu-id="5f7b7-416">Das Datum, an dem der Testzeitraum für diese App abläuft, angegeben in der koordinierten Weltzeit (UTC).</span><span class="sxs-lookup"><span data-stu-id="5f7b7-416">The date the trial period for this app expires, in Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="5f7b7-417">Das Datum muss ausgedrückt werden als: yyyy-mm-ddThh:mm:ss.ssZ.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-417">The date must be expressed as: yyyy-mm-ddThh:mm:ss.ssZ.</span></span> <span data-ttu-id="5f7b7-418">Beispielsweise würde 05:00Uhr am 19.Januar2015 als 2015-01-19T05:00:00.00Z angegeben.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-418">For example, 05:00 on January 19, 2015 would be specified as 2015-01-19T05:00:00.00Z.</span></span> <span data-ttu-id="5f7b7-419">Dieses Element ist erforderlich, wenn **IsTrial** **true** ist.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-419">This element is required when **IsTrial** is **true**.</span></span> <span data-ttu-id="5f7b7-420">Andernfalls ist es nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-420">Otherwise, it is not required.</span></span>          |  |

<span id="product-child-of-licenseinformation"/>

#### <a name="product-element-child-of-licenseinformation"></a><span data-ttu-id="5f7b7-421">Product-Element (untergeordnetes Element von LicenseInformation.)</span><span class="sxs-lookup"><span data-stu-id="5f7b7-421">Product element (child of LicenseInformation)</span></span>

<span data-ttu-id="5f7b7-422">Dieses Element beschreibt den Lizenzstatus eines dauerhaften Add-Ons in der App.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-422">This element describes the license status of a durable add-on in the app.</span></span> <span data-ttu-id="5f7b7-423">**Product** ist ein optionales untergeordnetes Element des [LicenseInformation](#licenseinformation)-Elements.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-423">**Product** is an optional child of the [LicenseInformation](#licenseinformation) element.</span></span>

<span data-ttu-id="5f7b7-424">**Product** enthält die folgenden untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-424">**Product** contains the following child elements.</span></span>

|  <span data-ttu-id="5f7b7-425">Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-425">Element</span></span>  |  <span data-ttu-id="5f7b7-426">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-426">Required</span></span>  |  <span data-ttu-id="5f7b7-427">Menge</span><span class="sxs-lookup"><span data-stu-id="5f7b7-427">Quantity</span></span>  | <span data-ttu-id="5f7b7-428">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-428">Description</span></span>   |
|-------------|------------|--------|--------|
|  **<span data-ttu-id="5f7b7-429">IsActive</span><span class="sxs-lookup"><span data-stu-id="5f7b7-429">IsActive</span></span>**  |    <span data-ttu-id="5f7b7-430">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-430">Yes</span></span>   |  <span data-ttu-id="5f7b7-431">1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-431">1</span></span>     |    <span data-ttu-id="5f7b7-432">Beschreibt den aktuellen Lizenzstatus des Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-432">Describes the current license state of this add-on.</span></span> <span data-ttu-id="5f7b7-433">Der Wert **true** gibt an, dass das Add-On verwendet werden kann. Der Wert **false** gibt an, dass das Add-On nicht verwendet werden kann oder nicht gekauft wurde.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-433">The value **true** indicates the add-on can be used; **false** indicates the add-on cannot be used or has not been purchased</span></span>           |
|  **<span data-ttu-id="5f7b7-434">ExpirationDate</span><span class="sxs-lookup"><span data-stu-id="5f7b7-434">ExpirationDate</span></span>**  |    <span data-ttu-id="5f7b7-435">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-435">No</span></span>   |  <span data-ttu-id="5f7b7-436">0 oder 1</span><span class="sxs-lookup"><span data-stu-id="5f7b7-436">0 or 1</span></span>     |     <span data-ttu-id="5f7b7-437">Das Datum, an dem das Add-On abläuft, angegeben in der koordinierten Weltzeit (UTC).</span><span class="sxs-lookup"><span data-stu-id="5f7b7-437">The date the add-on expires, in Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="5f7b7-438">Das Datum muss ausgedrückt werden als: yyyy-mm-ddThh:mm:ss.ssZ.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-438">The date must be expressed as: yyyy-mm-ddThh:mm:ss.ssZ.</span></span> <span data-ttu-id="5f7b7-439">Beispielsweise würde 05:00Uhr am 19.Januar2015 als 2015-01-19T05:00:00.00Z angegeben.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-439">For example, 05:00 on January 19, 2015 would be specified as 2015-01-19T05:00:00.00Z.</span></span> <span data-ttu-id="5f7b7-440">Wenn dieses Element vorhanden ist, hat das Add-On ein Ablaufdatum.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-440">If this element is present, the add-on has an expiration date.</span></span> <span data-ttu-id="5f7b7-441">Wenn es nicht vorhanden ist, läuft das Add-On nicht ab.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-441">If it's not present, the add-on does not expire.</span></span>  |  

<span data-ttu-id="5f7b7-442">**Product** hat die folgenden Attribute.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-442">**Product** has the following attributes.</span></span>

|  <span data-ttu-id="5f7b7-443">Attribut</span><span class="sxs-lookup"><span data-stu-id="5f7b7-443">Attribute</span></span>  |  <span data-ttu-id="5f7b7-444">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-444">Required</span></span>  |  <span data-ttu-id="5f7b7-445">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-445">Description</span></span>   |
|-------------|------------|----------------|
|  **<span data-ttu-id="5f7b7-446">ProductId</span><span class="sxs-lookup"><span data-stu-id="5f7b7-446">ProductId</span></span>**  |    <span data-ttu-id="5f7b7-447">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-447">Yes</span></span>        |   <span data-ttu-id="5f7b7-448">Enthält die Zeichenfolge, die von der App zur Identifizierung des Add-Ons verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-448">Contains the string used by the app to identify the add-on.</span></span>            |
|  **<span data-ttu-id="5f7b7-449">OfferId</span><span class="sxs-lookup"><span data-stu-id="5f7b7-449">OfferId</span></span>**  |     <span data-ttu-id="5f7b7-450">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-450">No</span></span>       |   <span data-ttu-id="5f7b7-451">Enthält die Zeichenfolge, die von der App zur Identifizierung der Kategorie verwendet wird, zu der das Add-On gehört.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-451">Contains the string used by the app to identify the category in which the add-on belongs.</span></span> <span data-ttu-id="5f7b7-452">Dies stellt Unterstützung für große Artikelkataloge bereit, wie unter [Verwalten eines großen Katalogs mit In-App-Produkten](manage-a-large-catalog-of-in-app-products.md) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-452">This provides support for large item catalogs, as described in [Manage a large catalog of in-app products](manage-a-large-catalog-of-in-app-products.md).</span></span>           |

<span id="simulation"/>

#### <a name="simulation-element"></a><span data-ttu-id="5f7b7-453">Simulation-Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-453">Simulation element</span></span>

<span data-ttu-id="5f7b7-454">Dieses Element beschreibt, wie Aufrufe verschiedener [CurrentAppSimulator](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentappsimulator.aspx)-Methoden während der Testphase in der App funktionieren.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-454">This element describes how calls to various [CurrentAppSimulator](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentappsimulator.aspx) methods will work in the app during testing.</span></span> <span data-ttu-id="5f7b7-455">**Simulation** ist ein optionales untergeordnetes Element des **CurrentApp**-Elements und enthält keine oder mehr [DefaultResponse](#defaultresponse)-Elemente.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-455">**Simulation** is an optional child of the **CurrentApp** element, and it contains zero or more [DefaultResponse](#defaultresponse) elements.</span></span>

<span data-ttu-id="5f7b7-456">**Simulation** hat die folgenden Attribute.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-456">**Simulation** has the following attributes.</span></span>

|  <span data-ttu-id="5f7b7-457">Attribut</span><span class="sxs-lookup"><span data-stu-id="5f7b7-457">Attribute</span></span>  |  <span data-ttu-id="5f7b7-458">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-458">Required</span></span>  |  <span data-ttu-id="5f7b7-459">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-459">Description</span></span>   |
|-------------|------------|----------------|
|  **<span data-ttu-id="5f7b7-460">SimulationMode</span><span class="sxs-lookup"><span data-stu-id="5f7b7-460">SimulationMode</span></span>**  |    <span data-ttu-id="5f7b7-461">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-461">No</span></span>        |      <span data-ttu-id="5f7b7-462">Werte können **Interactive** oder **Automatic** sein.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-462">Values can be **Interactive** or **Automatic**.</span></span> <span data-ttu-id="5f7b7-463">Wenn dieses Attribut auf **Automatic** festgelegt ist, geben die Methoden automatisch die angegebenen HRESULT-Fehlercodes zurück.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-463">When this attribute is set to **Automatic**, the methods will automatically return the specified HRESULT error codes.</span></span> <span data-ttu-id="5f7b7-464">Dies kann während der Ausführung automatisierter Testfälle verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-464">This can be used when running automated test cases.</span></span>       |

<span id="defaultresponse"/>

#### <a name="defaultresponse-element"></a><span data-ttu-id="5f7b7-465">DefaultResponse-Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-465">DefaultResponse element</span></span>

<span data-ttu-id="5f7b7-466">Dieses Element beschreibt den Standardfehlercode, der von einer **CurrentAppSimulator**-Methode zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-466">This element describes the default error code returned by a **CurrentAppSimulator** method.</span></span> <span data-ttu-id="5f7b7-467">**DefaultResponse** ist ein optionales untergeordnetes Element des [Simulation](#simulation)-Elements.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-467">**DefaultResponse** is an optional child of the [Simulation](#simulation) element.</span></span>

<span data-ttu-id="5f7b7-468">**DefaultResponse** hat die folgenden Attribute.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-468">**DefaultResponse** has the following attributes.</span></span>

|  <span data-ttu-id="5f7b7-469">Attribut</span><span class="sxs-lookup"><span data-stu-id="5f7b7-469">Attribute</span></span>  |  <span data-ttu-id="5f7b7-470">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-470">Required</span></span>  |  <span data-ttu-id="5f7b7-471">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-471">Description</span></span>   |
|-------------|------------|----------------|
|  **<span data-ttu-id="5f7b7-472">MethodName</span><span class="sxs-lookup"><span data-stu-id="5f7b7-472">MethodName</span></span>**  |    <span data-ttu-id="5f7b7-473">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-473">Yes</span></span>        |   <span data-ttu-id="5f7b7-474">Weisen Sie dieses Attribut einem der Enumerationswerte für den Typ **StoreMethodName** im [Schema](#schema) zu.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-474">Assign this attribute to one of the enum values shown for the **StoreMethodName** type in the [schema](#schema).</span></span> <span data-ttu-id="5f7b7-475">Jede dieser Enumerationswerte stellt eine **CurrentAppSimulator**-Methode dar, für die Sie während der Testphase in Ihrer App einen Fehlercode-Rückgabewert simulieren möchten.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-475">Each of these enum values represents a **CurrentAppSimulator** method for which you want to simulate an error code return value in your app during testing.</span></span> <span data-ttu-id="5f7b7-476">Beispielsweise gibt der Wert **RequestAppPurchaseAsync_GetResult** an, dass Sie den Fehlercode-Rückgabewert der [RequestAppPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentappsimulator.requestapppurchaseasync)-Methode simulieren möchten.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-476">For example, the value **RequestAppPurchaseAsync_GetResult** indicates you want to simulate the error code return value of the [RequestAppPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentappsimulator.requestapppurchaseasync) method.</span></span>            |
|  **<span data-ttu-id="5f7b7-477">HResult</span><span class="sxs-lookup"><span data-stu-id="5f7b7-477">HResult</span></span>**  |     <span data-ttu-id="5f7b7-478">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-478">Yes</span></span>       |   <span data-ttu-id="5f7b7-479">Weisen Sie dieses Attribut einem der Enumerationswerte für den Typ **ResponseCodes** im [Schema](#schema) zu.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-479">Assign this attribute to one of the enum values shown for the **ResponseCodes** type in the [schema](#schema).</span></span> <span data-ttu-id="5f7b7-480">Jeder dieser Enumerationswerte stellt den Fehlercode dar, den Sie für die Methode zurückgeben möchten, die Sie dem **MethodName**-Attribut für dieses **DefaultResponse**-Element zugewiesen haben.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-480">Each of these enum values represents the error code you want to return for the method that is assigned to the **MethodName** attribute for this **DefaultResponse** element.</span></span>           |

<span id="consumableinformation"/>

#### <a name="consumableinformation-element"></a><span data-ttu-id="5f7b7-481">ConsumableInformation-Element</span><span class="sxs-lookup"><span data-stu-id="5f7b7-481">ConsumableInformation element</span></span>

<span data-ttu-id="5f7b7-482">Dieses Element beschreibt die konsumierbaren Add-Ons, die für diese App verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-482">This element describes the consumable add-ons available for this app.</span></span> <span data-ttu-id="5f7b7-483">**ConsumableInformation** ist ein optionales untergeordnetes Element des **CurrentApp**-Elements und kann keine oder mehr [Product](#product-child-of-consumableinformation)-Elemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-483">**ConsumableInformation** is an optional child of the **CurrentApp** element, and it can contain zero or more [Product](#product-child-of-consumableinformation) elements.</span></span>

<span id="product-child-of-consumableinformation"/>

#### <a name="product-element-child-of-consumableinformation"></a><span data-ttu-id="5f7b7-484">Product-Element (untergeordnetes Element von ConsumableInformation)</span><span class="sxs-lookup"><span data-stu-id="5f7b7-484">Product element (child of ConsumableInformation)</span></span>

<span data-ttu-id="5f7b7-485">Dieses Element beschreibt ein konsumierbares Add-On.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-485">This element describes a consumable add-on.</span></span> <span data-ttu-id="5f7b7-486">**Product** ist ein optionales untergeordnetes Element des [ConsumableInformation](#consumableinformation)-Elements.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-486">**Product** is an optional child of the [ConsumableInformation](#consumableinformation) element.</span></span>

<span data-ttu-id="5f7b7-487">**Product** hat die folgenden Attribute.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-487">**Product** has the following attributes.</span></span>

|  <span data-ttu-id="5f7b7-488">Attribut</span><span class="sxs-lookup"><span data-stu-id="5f7b7-488">Attribute</span></span>  |  <span data-ttu-id="5f7b7-489">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="5f7b7-489">Required</span></span>  |  <span data-ttu-id="5f7b7-490">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f7b7-490">Description</span></span>   |
|-------------|------------|----------------|
|  **<span data-ttu-id="5f7b7-491">ProductId</span><span class="sxs-lookup"><span data-stu-id="5f7b7-491">ProductId</span></span>**  |    <span data-ttu-id="5f7b7-492">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-492">Yes</span></span>        |   <span data-ttu-id="5f7b7-493">Enthält die Zeichenfolge, die von der App zur Identifizierung des konsumierbaren Add-Ons verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-493">Contains the string used by the app to identify the consumable add-on.</span></span>            |
|  **<span data-ttu-id="5f7b7-494">TransactionId</span><span class="sxs-lookup"><span data-stu-id="5f7b7-494">TransactionId</span></span>**  |     <span data-ttu-id="5f7b7-495">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-495">Yes</span></span>       |   <span data-ttu-id="5f7b7-496">Enthält eine GUID (als Zeichenfolge), die von der App verwendet wird, um die Kauftransaktion für ein konsumierbares Add-On während der Ausführung nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-496">Contains a GUID (as a string) used by the app to track the purchase transaction of a consumable through the process of fulfillment.</span></span> <span data-ttu-id="5f7b7-497">Weitere Informationen finden Sie unter [Käufe von konsumierbaren In-App-Produkten aktivieren](enable-consumable-in-app-product-purchases.md).</span><span class="sxs-lookup"><span data-stu-id="5f7b7-497">See [Enable consumable in-app product purchases](enable-consumable-in-app-product-purchases.md).</span></span>            |
|  **<span data-ttu-id="5f7b7-498">Status</span><span class="sxs-lookup"><span data-stu-id="5f7b7-498">Status</span></span>**  |      <span data-ttu-id="5f7b7-499">Ja</span><span class="sxs-lookup"><span data-stu-id="5f7b7-499">Yes</span></span>      |  <span data-ttu-id="5f7b7-500">Enthält die Zeichenfolge, die von der App verwendet wird, um den Ausführungsstatus eines konsumierbaren Add-Ons anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-500">Contains the string used by the app to indicate the fulfillment status of a consumable.</span></span> <span data-ttu-id="5f7b7-501">Werte können **Active**, **PurchaseReverted**, **PurchasePending** oder **ServerError** sein.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-501">Values can be **Active**, **PurchaseReverted**, **PurchasePending**, or **ServerError**.</span></span>             |
|  **<span data-ttu-id="5f7b7-502">OfferId</span><span class="sxs-lookup"><span data-stu-id="5f7b7-502">OfferId</span></span>**  |     <span data-ttu-id="5f7b7-503">Nein</span><span class="sxs-lookup"><span data-stu-id="5f7b7-503">No</span></span>       |    <span data-ttu-id="5f7b7-504">Enthält die Zeichenfolge, die von der App zur Identifizierung der Kategorie verwendet wird, zu der das konsumierbare Add-On gehört.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-504">Contains the string used by the app to identify the category in which the consumable belongs.</span></span> <span data-ttu-id="5f7b7-505">Dies stellt Unterstützung für große Artikelkataloge bereit, wie unter [Verwalten eines großen Katalogs mit In-App-Produkten](manage-a-large-catalog-of-in-app-products.md) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5f7b7-505">This provides support for large item catalogs, as described in [Manage a large catalog of in-app products](manage-a-large-catalog-of-in-app-products.md).</span></span>           |
