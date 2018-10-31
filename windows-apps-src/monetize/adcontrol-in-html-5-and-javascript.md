---
author: Xansky
ms.assetid: adb2fa45-e18f-4254-bd8b-a749a386e3b4
description: Hier erfahren Sie, wie Sie die AdControl-Klasse nutzen können, um Werbebanner in einer JavaScript/HTML-App für Windows 10 (UWP) anzuzeigen.
title: AdControl in HTML 5 und JavaScript
ms.author: mhopkins
ms.date: 03/22/2018
ms.topic: article
keywords: Windows10, UWP, Anzeigen, Werbung, AdControl, Anzeigen-Steuerelement, HTML, Javascript
ms.localizationpriority: medium
ms.openlocfilehash: de3ffa9e82687e31c7f91548be953f224975d09a
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5835743"
---
# <a name="adcontrol-in-html-5-and-javascript"></a><span data-ttu-id="c71de-104">„AdControl“ in HTML 5 und JavaScript</span><span class="sxs-lookup"><span data-stu-id="c71de-104">AdControl in HTML 5 and JavaScript</span></span>

<span data-ttu-id="c71de-105">In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie die [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol)-Klasse nutzen können, um Werbebanner in einer Universellen Windows-Plattform-, JavaScript-/HTML-App für Windows 10 anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c71de-105">This walkthrough shows how to use the [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) class to display banner ads in a Universal Windows Platform (UWP) JavaScript/HTML app for Windows 10.</span></span>

<span data-ttu-id="c71de-106">Ein vollständiges Beispiel-Projekt mit einer Veranschaulichung, wie Sie Werbebanner einer JavaScript/HTML-App hinzufügen, finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).</span><span class="sxs-lookup"><span data-stu-id="c71de-106">For a complete sample project that demonstrates how to add banner ads to a JavaScript/HTML app, see the [advertising samples on GitHub](http://aka.ms/githubads).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c71de-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c71de-107">Prerequisites</span></span>

* <span data-ttu-id="c71de-108">Installieren Sie das [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) mit Visual Studio2015 oder einer neueren Version von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c71de-108">Install the [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp) with Visual Studio 2015 or a later release of Visual Studio.</span></span> <span data-ttu-id="c71de-109">Installationsanweisungen finden Sie in [diesem Artikel](install-the-microsoft-advertising-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="c71de-109">For installation instructions, see [this article](install-the-microsoft-advertising-libraries.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c71de-110">Wenn Sie das Windows 10 SDK Version 10.0.14393 (Anniversary Update) oder eine höhere Version des Windows SDKS installiert haben, müssen Sie auch die [WinJS](https://github.com/winjs/winjs) -Bibliothek installieren.</span><span class="sxs-lookup"><span data-stu-id="c71de-110">If you have installed the Windows 10 SDK version 10.0.14393 (Anniversary Update) or a later version of the Windows SDK, you must also install the [WinJS](https://github.com/winjs/winjs) library.</span></span> <span data-ttu-id="c71de-111">Diese Bibliothek war in den früheren Versionen von Windows SDK für Windows 10 enthalten, aber ab Windows 10 Anniversary SDK Version 10.0.14393 (Anniversary Update) muss diese Bibliothek separat installiert werden.</span><span class="sxs-lookup"><span data-stu-id="c71de-111">This library used to be included in previous versions of the Windows SDK for Windows 10, but starting with the Windows 10 SDK version 10.0.14393 (Anniversary Update) this library must be installed separately.</span></span> 

## <a name="integrate-a-banner-ad-into-your-app"></a><span data-ttu-id="c71de-112">Banneranzeige in Ihrer App integrieren</span><span class="sxs-lookup"><span data-stu-id="c71de-112">Integrate a banner ad into your app</span></span>

1. <span data-ttu-id="c71de-113">Öffnen Sie in Visual Studio Ihr Projekt oder erstellen Sie ein neues Projekt.</span><span class="sxs-lookup"><span data-stu-id="c71de-113">In Visual Studio, open your project or create a new project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c71de-114">Wenn Sie ein vorhandenes Projekt verwenden, öffnen Sie die Datei "Package.appxmanifest" in Ihrem Projekt, und stellen sicher, dass die **Internet (Client)**-Funktion aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="c71de-114">If you're using an existing project, open the Package.appxmanifest file in your project and ensure that the **Internet (Client)** capability is selected.</span></span> <span data-ttu-id="c71de-115">Ihre App benötigt diese Funktion, um Testanzeigen und Live-Werbung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c71de-115">Your app needs this capability to receive test ads and live ads.</span></span>

2. <span data-ttu-id="c71de-116">Sollte in Ihrem Projekt die Zielplattform **Any CPU** definiert sein, müssen Sie eine architekturspezifische Buildausgabe verwenden (z.B. **x86**) und das Projekt entsprechend aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c71de-116">If your project targets **Any CPU**, update your project to use an architecture-specific build output (for example, **x86**).</span></span> <span data-ttu-id="c71de-117">Sollte in Ihrem Projekt die Zielplattform **ANYCPU** definiert sein, können Sie bei den folgenden Schritten keinen Verweis auf die Microsoft Advertising-Bibliotheken hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c71de-117">If your project targets **Any CPU**, you will not be able to successfully add a reference to the Microsoft advertising library in the following steps.</span></span> <span data-ttu-id="c71de-118">Weitere Informationen finden Sie unter [Referenzfehler, die durch die Ausrichtung auf eine beliebige CPU (Any CPU) in Ihrem Projekt verursacht werden](known-issues-for-the-advertising-libraries.md#reference_errors).</span><span class="sxs-lookup"><span data-stu-id="c71de-118">For more information, see [Reference errors caused by targeting Any CPU in your project](known-issues-for-the-advertising-libraries.md#reference_errors).</span></span>

3. <span data-ttu-id="c71de-119">Hinzufügen eines Verweises auf die Microsoft Advertising-SDK in Ihrem Projekt:</span><span class="sxs-lookup"><span data-stu-id="c71de-119">Add a reference to the Microsoft Advertising SDK in your project:</span></span>

    1. <span data-ttu-id="c71de-120">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen...** aus.</span><span class="sxs-lookup"><span data-stu-id="c71de-120">From the **Solution Explorer** window, right click **References**, and select **Add Reference…**</span></span>
    2.  <span data-ttu-id="c71de-121">Erweitern Sie im **Verweis-Manager** den Knoten **Universal Windows**, klicken Sie auf **Erweiterungen**, und wählen Sie dann das Kontrollkästchen neben **Microsoft Advertising-SDK für JavaScript** (Version 10.0).</span><span class="sxs-lookup"><span data-stu-id="c71de-121">In **Reference Manager**, expand **Universal Windows**, click **Extensions**, and then select the check box next to **Microsoft Advertising SDK for JavaScript** (Version 10.0).</span></span>
    3.  <span data-ttu-id="c71de-122">Klicken Sie im **Verweis-Manager** auf „OK“.</span><span class="sxs-lookup"><span data-stu-id="c71de-122">In **Reference Manager**, click OK.</span></span>

6.  <span data-ttu-id="c71de-123">Öffnen Sie die Datei „index.html“ (oder je nach Projekt eine andere HTML-Datei).</span><span class="sxs-lookup"><span data-stu-id="c71de-123">Open the index.html file (or other html file as appropriate for your project).</span></span>

7.  <span data-ttu-id="c71de-124">Fügen Sie im Abschnitt **&lt;head&gt;** nach den JavaScript-Verweisen auf default.css und main.js des Projekts den Verweis auf ad.js ein.</span><span class="sxs-lookup"><span data-stu-id="c71de-124">In the **&lt;head&gt;** section, after the project’s JavaScript references of default.css and main.js, add the reference to ad.js.</span></span>

    ``` HTML
    <!-- Advertising required references -->
    <script src="//Microsoft.Advertising.JavaScript/ad.js"></script>
    ```

    > [!NOTE]
    > <span data-ttu-id="c71de-125">Diese Zeile muss im Abschnitt **&lt;Head&gt;** nach der Datei „main.js“ platziert werden. Andernfalls tritt bei der Erstellung des Projekts ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="c71de-125">This line must be placed in the **&lt;head&gt;** section after the include of main.js; otherwise, you will encounter an error when you build your project.</span></span>

8.  <span data-ttu-id="c71de-126">Ändern Sie den Bereich **&lt;body&gt;** in der Datei „default.HTML“ (oder je nach Projekt einer anderen html-Datei), sodass sie das **DIV**-Element für die **AdControl** enthält.</span><span class="sxs-lookup"><span data-stu-id="c71de-126">Modify the **&lt;body&gt;** section in the default.html file (or other html file as appropriate for your project) to include the **div** for the **AdControl**.</span></span> <span data-ttu-id="c71de-127">Weisen Sie den Eigenschaften **applicationId** und **adUnitId** Eigenschaften dem **AdControl** unter [Testanzeigen-Einheitenwerte](set-up-ad-units-in-your-app.md#test-ad-units) bereitgestellten Testwerte zu.</span><span class="sxs-lookup"><span data-stu-id="c71de-127">Assign the **applicationId** and **adUnitId** properties of the **AdControl** to the [test ad unit values](set-up-ad-units-in-your-app.md#test-ad-units).</span></span> <span data-ttu-id="c71de-128">Passen Sie zudem **Höhe** und **Breite** des Steuerelements an, damit es einer der [unterstützten Anzeigengrößen für Werbebanner](supported-ad-sizes-for-banner-ads.md) entspricht.</span><span class="sxs-lookup"><span data-stu-id="c71de-128">Also adjust the **height** and **width** so the control is one of the [supported ad sizes for banner ads](supported-ad-sizes-for-banner-ads.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c71de-129">Jedes **AdControl** verfügt über ein entsprechendes *Anzeigeneinheit*, die von unseren Diensten verwendet wird, um Werbung auf das Steuerelement zu übertragen, und jede Anzeigeneinheit besteht aus einer *Anzeigeneinheits-ID* und *Anwendungs-ID*.</span><span class="sxs-lookup"><span data-stu-id="c71de-129">Every **AdControl** has a corresponding *ad unit* that is used by our services to serve ads to the control, and every ad unit consists of an *ad unit ID* and *application ID*.</span></span> <span data-ttu-id="c71de-130">In den folgenden Schrittenweisen Sie eine Test Anzeigeneinheits-ID und Anwendungs-ID für Ihr Steuerelement zu.</span><span class="sxs-lookup"><span data-stu-id="c71de-130">In these steps, you assign test ad unit ID and application ID values to your control.</span></span> <span data-ttu-id="c71de-131">Dieser Test Werte können nur in einer Testversion Ihrer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c71de-131">These test values can only be used in a test version of your app.</span></span> <span data-ttu-id="c71de-132">Bevor Sie Ihre App im Store veröffentlichen, müssen Sie die [Testwerte mit den Livewerten aus dem Windows Dev Center ersetzen](#release).</span><span class="sxs-lookup"><span data-stu-id="c71de-132">Before you publish your app to the Store, you must [replace these test values with live values](#release) from Windows Dev Center.</span></span>

    ``` HTML
    <div id="myAd" style="position: absolute; top: 50px; left: 0px; width: 300px; height: 250px; z-index: 1"
        data-win-control="MicrosoftNSJS.Advertising.AdControl"
        data-win-options="{applicationId: '3f83fe91-d6be-434d-a0ae-7351c5a997f1', adUnitId: 'test'}">
    </div>
    ```

9.  <span data-ttu-id="c71de-133">Kompilieren Sie die App, und führen Sie sie aus, um sie mit einer Anzeige zu sehen.</span><span class="sxs-lookup"><span data-stu-id="c71de-133">Compile and run the app to see it with an ad.</span></span>

<span data-ttu-id="c71de-134">Das folgende Beispiel zeigt die vollständige index.html für eine einfache App.</span><span class="sxs-lookup"><span data-stu-id="c71de-134">The following example shows the complete index.html for a simple app.</span></span>

``` HTML
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>AdControlExampleApp</title>
    <!-- WinJS references -->
    <link href="lib/winjs-4.0.1/css/ui-light.css" rel="stylesheet" />
    <script src="lib/winjs-4.0.1/js/base.js"></script>
    <script src="lib/winjs-4.0.1/js/ui.js"></script>
    <!-- AdControlExampleApp references -->
    <link href="css/default.css" rel="stylesheet" />
    <script src="js/main.js"></script>
    <!-- Required reference for AdControl -->
    <script src="//Microsoft.Advertising.JavaScript/ad.js"></script>
</head>
<body>
    <div id="myAd" style="position: absolute; top: 50px; left: 0px; width: 300px; height: 250px; z-index: 1"
      data-win-control="MicrosoftNSJS.Advertising.AdControl"
      data-win-options="{applicationId: '3f83fe91-d6be-434d-a0ae-7351c5a997f1', adUnitId: 'test'}">
    </div>
    <p>Content goes here</p>
</body>
</html>
```

### <a name="create-an-adcontrol-programmatically-in-javascript"></a><span data-ttu-id="c71de-135">Erstellen eines programmgesteuerten AdControl-Elements in JavaScript</span><span class="sxs-lookup"><span data-stu-id="c71de-135">Create an AdControl programmatically in Javascript</span></span>

<span data-ttu-id="c71de-136">Die vorherigen Schritte zeigen das Deklarieren einer **AdControl** in Ihrem HTML-Markup.</span><span class="sxs-lookup"><span data-stu-id="c71de-136">The previous steps show how to declare an **AdControl** in your HTML markup.</span></span> <span data-ttu-id="c71de-137">Alternativ können Sie programmgesteuert ein **AdControl** (Anzeigensteuerelement) mit JavaScript erstellen.</span><span class="sxs-lookup"><span data-stu-id="c71de-137">Alternatively, you can programmatically create an **AdControl** using JavaScript.</span></span> <span data-ttu-id="c71de-138">In diesem Beispiel wird davon ausgegangen, dass Sie in Ihrem HTML-Code ein vorhandenes **div**-Element mit der ID **MyAd** verwenden.</span><span class="sxs-lookup"><span data-stu-id="c71de-138">This example assumes that you are using an existing **div** in your HTML with the ID **myAd**.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-javascript[AdControl](./code/AdvertisingSamples/AdControlSamples/js/main.js#DeclareAdControl)]

<span data-ttu-id="c71de-139">In diesem Beispiel wird davon ausgegangen, dass Sie die Ereignishandlermethoden **myAdError**, **myAdRefreshed** und **myAdEngagedChanged** bereits deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="c71de-139">This example assumes that you have already declared event handler methods named **myAdError**, **myAdRefreshed**, and **myAdEngagedChanged**.</span></span>

<span data-ttu-id="c71de-140">Wenn Sie diesen Code verwenden und keine Anzeigen angezeigt werden, können Sie versuchen, ein **position:relativ**-Attribut im **div**-Element einzufügen, das das **AdControl** enthält.</span><span class="sxs-lookup"><span data-stu-id="c71de-140">If you use this code and do not see ads, you can try inserting an attribute of **position:relative** in the **div** that contains the **AdControl**.</span></span> <span data-ttu-id="c71de-141">Dadurch wird die Standardeinstellung von **IFrame** überschrieben.</span><span class="sxs-lookup"><span data-stu-id="c71de-141">This will override the default setting of the **IFrame**.</span></span> <span data-ttu-id="c71de-142">Anzeigen werden ordnungsgemäß angezeigt, sofern sie nicht aufgrund des Werts dieses Attributs nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c71de-142">Ads will be displayed correctly, unless they are not being shown due to the value of this attribute.</span></span> <span data-ttu-id="c71de-143">Beachten Sie, dass neue Anzeigeeinheiten unter Umständen bis zu 30 Minuten nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="c71de-143">Note that new ad units may not be available for up to 30 minutes.</span></span>

> [!NOTE]
> <span data-ttu-id="c71de-144">Die in diesem Beispiel angezeigten Werte *applicationId* und *adUnitId* sind [Testmoduswerte](set-up-ad-units-in-your-app.md#test-ad-units).</span><span class="sxs-lookup"><span data-stu-id="c71de-144">The *applicationId* and *adUnitId* values shown in this example are [test mode values](set-up-ad-units-in-your-app.md#test-ad-units).</span></span> <span data-ttu-id="c71de-145">Sie müssen [diese Werte mit Livewerten aus Windows Dev Center ersetzen](set-up-ad-units-in-your-app.md#live-ad-units), bevor Sie Ihre App für die Übermittlung einreichen.</span><span class="sxs-lookup"><span data-stu-id="c71de-145">You must [replace these values with live values](set-up-ad-units-in-your-app.md#live-ad-units) from Windows Dev Center before submitting your app for submission.</span></span>

<span id="release" />

## <a name="release-your-app-with-live-ads"></a><span data-ttu-id="c71de-146">Veröffentlichen Ihrer App mit Live-Anzeigen</span><span class="sxs-lookup"><span data-stu-id="c71de-146">Release your app with live ads</span></span>

1. <span data-ttu-id="c71de-147">Stellen Sie sicher, dass die Verwendung von Werbebannern in Ihrer App unseren [Richtlinien für das Anzeigen von Werbebannern](ui-and-user-experience-guidelines.md#guidelines-for-banner-ads) entspricht.</span><span class="sxs-lookup"><span data-stu-id="c71de-147">Make sure your use of banner ads in your app follows our [guidelines for banner ads](ui-and-user-experience-guidelines.md#guidelines-for-banner-ads).</span></span>

1.  <span data-ttu-id="c71de-148">Wechseln Sie im Dev Center-Dashboard auf die Seite [In-App-Anzeigen](../publish/in-app-ads.md) und [erstellen Sie eine Anzeigeneinheit](set-up-ad-units-in-your-app.md#live-ad-units).</span><span class="sxs-lookup"><span data-stu-id="c71de-148">In the Dev Center dashboard, go to the [In-app ads](../publish/in-app-ads.md) page and [create an ad unit](set-up-ad-units-in-your-app.md#live-ad-units).</span></span> <span data-ttu-id="c71de-149">Geben Sie als Typ für die Anzeigeneinheit **Banner** an.</span><span class="sxs-lookup"><span data-stu-id="c71de-149">For the ad unit type, specify **Banner**.</span></span> <span data-ttu-id="c71de-150">Notieren Sie die Anzeigeneinheits-ID und die Anwendungs-ID.</span><span class="sxs-lookup"><span data-stu-id="c71de-150">Make note of both the ad unit ID and the application ID.</span></span>
    > [!NOTE]
    > <span data-ttu-id="c71de-151">Die Anwendungs-IDs für Test-Anzeigeneinheiten und Live-UWP-Anzeigeneinheiten besitzen unterschiedliche Formate.</span><span class="sxs-lookup"><span data-stu-id="c71de-151">The application ID values for test ad units and live UWP ad units have different formats.</span></span> <span data-ttu-id="c71de-152">Testanwendungs-ID sind GUIDs.</span><span class="sxs-lookup"><span data-stu-id="c71de-152">Test application ID values are GUIDs.</span></span> <span data-ttu-id="c71de-153">Wenn Sie eine Live-UWP-Anzeigeneinheit im Dashboard erstellen, entspricht die Anwendungs-ID für die Anzeigeneinheit immer der Store-ID Ihrer App (ein Beispiel für einen Store-ID-Wert ist 9NBLGGH4R315).</span><span class="sxs-lookup"><span data-stu-id="c71de-153">When you create a live UWP ad unit in the dashboard, the application ID value for the ad unit always matches the Store ID for your app (an example Store ID value looks like 9NBLGGH4R315).</span></span>

2. <span data-ttu-id="c71de-154">Sie können optional die Anzeigenvermittlung für **AdControl** durch Konfigurieren der [Vermittlungseinstellungen](../publish/in-app-ads.md#mediation) auf der Seite [In-App-Anzeigen](../publish/in-app-ads.md) aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c71de-154">You can optionally enable ad mediation for the **AdControl** by configuring the settings in the [Mediation settings](../publish/in-app-ads.md#mediation) section on the [In-app ads](../publish/in-app-ads.md) page.</span></span> <span data-ttu-id="c71de-155">Mit der Anzeigenvermittlung können Sie Ihre Anzeigenumsätze maximieren und Werbefunktionen optimal nutzen, indem Sie Anzeigen aus mehreren Anzeigennetzwerken anzeigen, einschließlich Anzeigen aus anderen kostenpflichtigen Anzeigennetzwerken wie Taboola und Smaato sowie Anzeigen zu Werbekampagnen für Microsoft-Apps.</span><span class="sxs-lookup"><span data-stu-id="c71de-155">Ad mediation enables you to maximize your ad revenue and app promotion capabilities by displaying ads from multiple ad networks, including ads from other paid ad networks such as Taboola and Smaato and ads for Microsoft app promotion campaigns.</span></span>

3.  <span data-ttu-id="c71de-156">Ersetzen Sie in Ihrem Code die Testwerte der Anzeigeneinheit (**applicationId** und **adUnitId**) mit den Live-Werten, die Sie in Dev Center generiert haben.</span><span class="sxs-lookup"><span data-stu-id="c71de-156">In your code, replace the test ad unit values (**applicationId** and **adUnitId**) with the live values you generated in Dev Center.</span></span>

4.  <span data-ttu-id="c71de-157">[Übermitteln Sie Ihre App](../publish/app-submissions.md) mithilfe des Dev Center-Dashboards an den Store.</span><span class="sxs-lookup"><span data-stu-id="c71de-157">[Submit your app](../publish/app-submissions.md) to the Store using the Dev Center dashboard.</span></span>

5.  <span data-ttu-id="c71de-158">Überprüfen Sie die [Anzeigenvermittlungsberichte](../publish/advertising-performance-report.md) im Dev Center-Dashboard.</span><span class="sxs-lookup"><span data-stu-id="c71de-158">Review your [advertising performance reports](../publish/advertising-performance-report.md) in the Dev Center dashboard.</span></span>             

<span id="manage" />

## <a name="manage-ad-units-for-multiple-ad-controls-in-your-app"></a><span data-ttu-id="c71de-159">Verwalten von Anzeigeeinheiten für mehrere Steuerelemente von Anzeigen in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="c71de-159">Manage ad units for multiple ad controls in your app</span></span>

<span data-ttu-id="c71de-160">Sie können mehrere **AdControl** Objekte in einer einzelnen App nutzen (z.B. jede Seite in Ihrer App hostet ein anderes **AdControl** Objekt).</span><span class="sxs-lookup"><span data-stu-id="c71de-160">You can use multiple **AdControl** objects in a single app (for example, each page in your app might host a different **AdControl** object).</span></span> <span data-ttu-id="c71de-161">In diesem Fall wird empfohlen, dass Sie jedem Steuerelement eine andere Anzeigeneinheit zuweisen.</span><span class="sxs-lookup"><span data-stu-id="c71de-161">In this scenario, we recommend that you assign a different ad unit to each control.</span></span> <span data-ttu-id="c71de-162">Durch das Verwenden verschiedener Anzeigeeinheiten für jedes Steuerelement können Sie für jedes Steuerelement [die Einstellungen für die Anzeigenvermittlung konfigurieren](../publish/in-app-ads.md#mediation) und diskrete [Berichtsdaten](../publish/advertising-performance-report.md).</span><span class="sxs-lookup"><span data-stu-id="c71de-162">Using different ad units for each control enables you to separately [configure the mediation settings](../publish/in-app-ads.md#mediation) and get discrete [reporting data](../publish/advertising-performance-report.md) for each control.</span></span> <span data-ttu-id="c71de-163">Außerdem können unsere Dienste so die Werbung optimieren, die wir in Ihrer App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c71de-163">This also enables our services to better optimize the ads we serve to your app.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c71de-164">Sie können jede Anzeigeneinheit in nur einer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="c71de-164">You can use each ad unit in only one app.</span></span> <span data-ttu-id="c71de-165">Wenn Sie eine Anzeigeneinheit in mehr als einer App verwenden, werden für die Ad-Einheit keine Anzeigen platziert.</span><span class="sxs-lookup"><span data-stu-id="c71de-165">If you use an ad unit in more than one app, ads will not be served for that ad unit.</span></span>

## <a name="related-topics"></a><span data-ttu-id="c71de-166">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c71de-166">Related topics</span></span>

* [<span data-ttu-id="c71de-167">Richtlinien für Banneranzeigen</span><span class="sxs-lookup"><span data-stu-id="c71de-167">Guidelines for banner ads</span></span>](ui-and-user-experience-guidelines.md#guidelines-for-banner-ads)
* [<span data-ttu-id="c71de-168">Anzeigenbeispiele auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c71de-168">Advertising samples on GitHub</span></span>](http://aka.ms/githubads)
* [<span data-ttu-id="c71de-169">Einrichten von Anzeigeneinheiten für die App</span><span class="sxs-lookup"><span data-stu-id="c71de-169">Set up ad units for your app</span></span>](set-up-ad-units-in-your-app.md)
* [<span data-ttu-id="c71de-170">Exemplarische Vorgehensweise zur Fehlerbehandlung in JavaScript</span><span class="sxs-lookup"><span data-stu-id="c71de-170">Error handling in JavaScript walkthrough</span></span>](error-handling-in-javascript-walkthrough.md)
