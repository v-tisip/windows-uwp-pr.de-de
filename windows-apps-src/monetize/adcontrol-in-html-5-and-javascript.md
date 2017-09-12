---
author: mcleanbyron
ms.assetid: adb2fa45-e18f-4254-bd8b-a749a386e3b4
description: "Hier erfahren Sie, wie Sie die AdControl-Klasse nutzen können, um Werbebanner in einer JavaScript/HTML-App für Windows 10 (UWP), Windows 8.1 oder Windows Phone 8.1 anzuzeigen."
title: AdControl in HTML 5 und JavaScript
ms.author: mcleans
ms.date: 06/26/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, AdControl, Anzeigen-Steuerelement, HTML, Javascript
ms.openlocfilehash: 44417516d773ea4faf103f6d4cdaf0bc8f290921
ms.sourcegitcommit: 8c4d50ef819ed1a2f8cac4eebefb5ccdaf3fa898
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2017
---
# <a name="adcontrol-in-html-5-and-javascript"></a><span data-ttu-id="fea8f-104">„AdControl“ in HTML 5 und JavaScript</span><span class="sxs-lookup"><span data-stu-id="fea8f-104">AdControl in HTML 5 and JavaScript</span></span>

<span data-ttu-id="fea8f-105">In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie die [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Klasse nutzen können, um Werbebanner in einer JavaScript/HTML-App für Windows 10 (UWP), Windows 8.1 oder Windows Phone 8.1 anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fea8f-105">This walkthrough shows how to use the [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) class to display banner ads in a JavaScript/HTML app for Windows 10 (UWP), Windows 8.1, or Windows Phone 8.1.</span></span>

<span data-ttu-id="fea8f-106">Ein vollständiges Beispiel-Projekt mit einer Veranschaulichung, wie Sie Werbebanner einer JavaScript/HTML-App hinzufügen, finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).</span><span class="sxs-lookup"><span data-stu-id="fea8f-106">For a complete sample project that demonstrates how to add banner ads to a JavaScript/HTML app, see the [advertising samples on GitHub](http://aka.ms/githubads).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fea8f-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="fea8f-107">Prerequisites</span></span>


* <span data-ttu-id="fea8f-108">Für UWP-Apps: Installieren Sie das [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) mit Visual Studio2015 oder einer neueren Version.</span><span class="sxs-lookup"><span data-stu-id="fea8f-108">For UWP apps: install the [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp) with Visual Studio 2015 or a later release.</span></span>
* <span data-ttu-id="fea8f-109">Für Windows8.1- oder Windows Phone8.1-Apps: Installieren Sie das [Microsoft Advertising SDK für Windows und Windows Phone8.x](http://aka.ms/store-8-sdk) mit Visual Studio2015 oder Visual Studio2013.</span><span class="sxs-lookup"><span data-stu-id="fea8f-109">For Windows 8.1 or Windows Phone 8.1 apps: install the [Microsoft Advertising SDK for Windows and Windows Phone 8.x](http://aka.ms/store-8-sdk) with Visual Studio 2015 or Visual Studio 2013.</span></span>

> [!NOTE]
> <span data-ttu-id="fea8f-110">Wenn Sie Banneranzeigen in einer UWP-App hinzufügen, und Sie das Windows10 SDK Version 10.0.14393 (Anniversary Update) oder eine höhere Version des Windows SDKs installiert haben, müssen Sie auch die WinJS-Bibliothek installieren.</span><span class="sxs-lookup"><span data-stu-id="fea8f-110">If you are adding banner ads to a UWP app and you have installed the Windows 10 SDK version 10.0.14393 (Anniversary Update) or a later version of the Windows SDK, you must also install the WinJS library.</span></span> <span data-ttu-id="fea8f-111">Diese Bibliothek war in den früheren Versionen von Windows SDK für Windows 10 enthalten, aber ab Windows 10 Anniversary SDK Version 10.0.14393 (Anniversary Update) muss diese Bibliothek separat installiert werden.</span><span class="sxs-lookup"><span data-stu-id="fea8f-111">This library used to be included in previous versions of the Windows SDK for Windows 10, but starting with the Windows 10 SDK version 10.0.14393 (Anniversary Update) this library must be installed separately.</span></span> <span data-ttu-id="fea8f-112">Informationen zur Installation von WinJS finden Sie unter [WinJS herunterladen](http://try.buildwinjs.com/download/GetWinJS/).</span><span class="sxs-lookup"><span data-stu-id="fea8f-112">To install WinJS, see [Get WinJS](http://try.buildwinjs.com/download/GetWinJS/).</span></span>

## <a name="code-development"></a><span data-ttu-id="fea8f-113">Codeentwicklung</span><span class="sxs-lookup"><span data-stu-id="fea8f-113">Code development</span></span>

1. <span data-ttu-id="fea8f-114">Öffnen Sie in Visual Studio Ihr Projekt oder erstellen Sie ein neues Projekt.</span><span class="sxs-lookup"><span data-stu-id="fea8f-114">In Visual Studio, open your project or create a new project.</span></span>

2. <span data-ttu-id="fea8f-115">Sollte in Ihrem Projekt die Zielplattform **ANYCPU** definiert sein, müssen Sie eine architekturspezifische Buildausgabe verwenden (z. B. **X86**) und das Projekt entsprechend aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="fea8f-115">If your project targets **Any CPU**, update your project to use an architecture-specific build output (for example, **x86**).</span></span> <span data-ttu-id="fea8f-116">Sollte in Ihrem Projekt die Zielplattform **ANYCPU** definiert sein, können Sie bei den folgenden Schritten keinen Verweis auf die Microsoft Advertising-Bibliotheken hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="fea8f-116">If your project targets **Any CPU**, you will not be able to successfully add a reference to the Microsoft advertising library in the following steps.</span></span> <span data-ttu-id="fea8f-117">Weitere Informationen finden Sie unter [Referenzfehler, die durch die Ausrichtung auf eine beliebige CPU (Any CPU) in Ihrem Projekt verursacht werden](known-issues-for-the-advertising-libraries.md#reference_errors).</span><span class="sxs-lookup"><span data-stu-id="fea8f-117">For more information, see [Reference errors caused by targeting Any CPU in your project](known-issues-for-the-advertising-libraries.md#reference_errors).</span></span>

3.  <span data-ttu-id="fea8f-118">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen...** aus.</span><span class="sxs-lookup"><span data-stu-id="fea8f-118">From the **Solution Explorer** window, right click **References**, and select **Add Reference…**</span></span>

4.  <span data-ttu-id="fea8f-119">Wählen Sie im **Verweis-Manager** je nach Projekttyp einen der folgenden Verweise aus:</span><span class="sxs-lookup"><span data-stu-id="fea8f-119">In **Reference Manager**, select one of the following references depending on your project type:</span></span>

    -   <span data-ttu-id="fea8f-120">Für ein Projekt für die Universelle Windows-Plattform (UWP): Erweitern Sie **Universelles Windows**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Microsoft Advertising SDK für JavaScript** (Version 10.0).</span><span class="sxs-lookup"><span data-stu-id="fea8f-120">For a Universal Windows Platform (UWP) project: Expand **Universal Windows**, click **Extensions**, and then select the check box next to **Microsoft Advertising SDK for JavaScript** (Version 10.0).</span></span>

    -   <span data-ttu-id="fea8f-121">Für ein Windows 8.1-Projekt: Erweitern Sie **Windows 8.1**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Microsoft Advertising SDK für Windows 8.1 Native (JS)**.</span><span class="sxs-lookup"><span data-stu-id="fea8f-121">For a Windows 8.1 project: Expand **Windows 8.1**, click **Extensions**, and then select the check box next to **Microsoft Advertising SDK for Windows 8.1 Native (JS)**.</span></span>

    -   <span data-ttu-id="fea8f-122">Für ein Windows Phone 8.1-Projekt: Erweitern Sie **Windows Phone 8.1**, klicken Sie auf **Erweiterungen**, und aktivieren Sie anschließend das Kontrollkästchen neben **Microsoft Advertising-SDK for Windows Phone 8.1 Native (JS)**.</span><span class="sxs-lookup"><span data-stu-id="fea8f-122">For a Windows Phone 8.1 project: Expand **Windows Phone 8.1**, click **Extensions**, and then select the check box next to **Microsoft Advertising SDK for Windows Phone 8.1 Native (JS)**.</span></span>

    ![javascriptaddreference](images/13-f7f6d6a6-161e-4f17-995d-1236d0b5d9f2.png)

5.  <span data-ttu-id="fea8f-124">Klicken Sie im **Verweis-Manager** auf „OK“.</span><span class="sxs-lookup"><span data-stu-id="fea8f-124">In **Reference Manager**, click OK.</span></span>

6.  <span data-ttu-id="fea8f-125">Öffnen Sie die Datei „index.html“ (oder je nach Projekt eine andere HTML-Datei).</span><span class="sxs-lookup"><span data-stu-id="fea8f-125">Open the index.html file (or other html file as appropriate for your project).</span></span>

7.  <span data-ttu-id="fea8f-126">Fügen Sie im Abschnitt **&lt;Head&gt;** nach den JavaScript-Verweisen auf default.css und main.js des Projekts den Verweis auf ad.js ein.</span><span class="sxs-lookup"><span data-stu-id="fea8f-126">In the **&lt;head&gt;** section, after the project’s JavaScript references of default.css and main.js, add the reference to ad.js.</span></span>

    <span data-ttu-id="fea8f-127">Fügen Sie im UWP-Projekt den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="fea8f-127">In a UWP project, add the following code.</span></span>

    ``` HTML
    <!-- Advertising required references -->
    <script src="//Microsoft.Advertising.JavaScript/ad.js"></script>
    ```

    <span data-ttu-id="fea8f-128">Fügen Sie bei einem Windows 8.1- oder Windows Phone 8.1-Projekt den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="fea8f-128">In a Windows 8.1 or Windows Phone 8.1 project, add the following code.</span></span>

    ``` HTML
    <!-- Advertising required references -->
    <script src="/MSAdvertisingJS/ads/ad.js"></script>
    ```

    > [!NOTE]
    > <span data-ttu-id="fea8f-129">Diese Zeile muss im Abschnitt **&lt;Head&gt;** nach der Datei „main.js“ platziert werden. Andernfalls tritt bei der Erstellung des Projekts ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="fea8f-129">This line must be placed in the **&lt;head&gt;** section after the include of main.js; otherwise, you will encounter an error when you build your project.</span></span> <span data-ttu-id="fea8f-130">Wenn Ihr Projekt auf Windows8.1 oder Windows Phone8.1 ausgerichtet ist, ist die standardmäßige HTML-Datei in Ihrem Projekt default.html und nicht index.html, und die standardmäßige JavaScript-Datei in Ihrem Projekt ist default.js anstelle von main.js.</span><span class="sxs-lookup"><span data-stu-id="fea8f-130">If your project targets Windows 8.1 or Windows Phone 8.1, the default HTML file in your project is named default.html instead of index.html, and the default JavaScript file in your project is named default.js instead of main.js.</span></span>

8.  <span data-ttu-id="fea8f-131">Ändern Sie den Bereich **&lt;Body&gt;** in der Datei „default.HTML“ (oder je nach Projekt einer anderen html-Datei), sodass sie das DIV-Element für die **AdControl** enthält.</span><span class="sxs-lookup"><span data-stu-id="fea8f-131">Modify the **&lt;body&gt;** section in the default.html file (or other html file as appropriate for your project) to include the div for the **AdControl**.</span></span> <span data-ttu-id="fea8f-132">Weisen Sie den Eigenschaften **applicationId** und **adUnitId** Eigenschaften dem **AdControl** unter [Testmoduswerte](test-mode-values.md) bereitgestellten Testwerte zu.</span><span class="sxs-lookup"><span data-stu-id="fea8f-132">Assign the **applicationId** and **adUnitId** properties in the **AdControl** to the test values provided in [Test mode values](test-mode-values.md).</span></span> <span data-ttu-id="fea8f-133">Passen Sie zudem Höhe und Breite des Steuerelements an, damit es einer der [unterstützten Anzeigengrößen für Werbebanner](supported-ad-sizes-for-banner-ads.md) entspricht.</span><span class="sxs-lookup"><span data-stu-id="fea8f-133">Also adjust the height and width of the control so it is one of the [supported ad sizes for banner ads](supported-ad-sizes-for-banner-ads.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="fea8f-134">Jedes **AdControl** verfügt über ein entsprechendes *Anzeigeneinheit*, die von unseren Diensten verwendet wird, um Werbung auf das Steuerelement zu übertragen, und jede Anzeigeneinheit besteht aus einer *Anzeigeneinheits-ID* und *Anwendungs-ID*.</span><span class="sxs-lookup"><span data-stu-id="fea8f-134">Every **AdControl** has a corresponding *ad unit* that is used by our services to serve ads to the control, and every ad unit consists of an *ad unit ID* and *application ID*.</span></span> <span data-ttu-id="fea8f-135">In den folgenden Schrittenweisen Sie eine Test Anzeigeneinheits-ID und Anwendungs-ID für Ihr Steuerelement zu.</span><span class="sxs-lookup"><span data-stu-id="fea8f-135">In these steps, you assign test ad unit ID and application ID values to your control.</span></span> <span data-ttu-id="fea8f-136">Diese Testwerte können nur in einer Testversion Ihrer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="fea8f-136">These test values can only be used in a test version of your app.</span></span> <span data-ttu-id="fea8f-137">Bevor Sie Ihre App im Store veröffentlichen, müssen Sie die [Testwerte mit den Livewerten aus dem Windows Dev Center ersetzen](#release).</span><span class="sxs-lookup"><span data-stu-id="fea8f-137">Before you publish your app to the Store, you must [replace these test values with live values](#release) from Windows Dev Center.</span></span>

    ``` HTML
    <div id="myAd" style="position: absolute; top: 50px; left: 0px; width: 300px; height: 250px; z-index: 1"
        data-win-control="MicrosoftNSJS.Advertising.AdControl"
        data-win-options="{applicationId: '3f83fe91-d6be-434d-a0ae-7351c5a997f1', adUnitId: 'test'}">
    </div>
    ```

9.  <span data-ttu-id="fea8f-138">Kompilieren Sie die App, und führen Sie sie aus, um sie mit einer Anzeige zu sehen.</span><span class="sxs-lookup"><span data-stu-id="fea8f-138">Compile and run the app to see it with an ad.</span></span>

<span data-ttu-id="fea8f-139">Das folgende Beispiel zeigt die vollständige index.html für eine einfache UWP-App.</span><span class="sxs-lookup"><span data-stu-id="fea8f-139">The following example shows the complete index.html for a simple UWP app.</span></span>

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

<span id="release" />
## <a name="release-your-app-with-live-ads-using-windows-dev-center"></a><span data-ttu-id="fea8f-140">Veröffentlichen von Apps mit Live-Anzeigen mithilfe von Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="fea8f-140">Release your app with live ads using Windows Dev Center</span></span>

1.  <span data-ttu-id="fea8f-141">Rufen Sie im Dev Center-Dashboard die Seite [Monetarisierung mit Anzeigen](../publish/monetize-with-ads.md) für Ihre App auf, und [erstellen Sie eine Anzeigeneinheit](../monetize/set-up-ad-units-in-your-app.md).</span><span class="sxs-lookup"><span data-stu-id="fea8f-141">In the Dev Center dashboard, go to the [Monetize with ads](../publish/monetize-with-ads.md) page for your app and [create an ad unit](../monetize/set-up-ad-units-in-your-app.md).</span></span> <span data-ttu-id="fea8f-142">Geben Sie als Anzeigeneinheitentyp **Banner** an.</span><span class="sxs-lookup"><span data-stu-id="fea8f-142">For the ad unit type, specify **Banner**.</span></span> <span data-ttu-id="fea8f-143">Notieren Sie die Anzeigeneinheits-ID und die Anwendungs-ID.</span><span class="sxs-lookup"><span data-stu-id="fea8f-143">Make note of both the ad unit ID and the application ID.</span></span>

2. <span data-ttu-id="fea8f-144">Wenn Ihre App eine UWP-App für Windows10 ist, können Sie optional die Anzeigenvermittlung für **AdControl** aktivieren, indem Sie im Abschnitt [Anzeigenvermittlung](../publish/monetize-with-ads.md#mediation) auf der Seite [Monetarisierung durch Anzeigen](../publish/monetize-with-ads.md) die Einstellungen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="fea8f-144">If your app is a UWP app for Windows 10, you can optionally enable ad mediation for the **AdControl** by configuring the settings in the [Ad mediation](../publish/monetize-with-ads.md#mediation) section on the [Monetize with ads](../publish/monetize-with-ads.md) page.</span></span> <span data-ttu-id="fea8f-145">Mit der Anzeigenvermittlung können Sie Ihre Anzeigenumsätze maximieren und Werbefunktionen optimal nutzen, indem Sie Anzeigen aus mehreren Anzeigennetzwerken anzeigen, einschließlich Anzeigen aus anderen kostenpflichtigen Anzeigennetzwerken wie Taboola und Smaato sowie Anzeigen zu Werbekampagnen für Microsoft-Apps.</span><span class="sxs-lookup"><span data-stu-id="fea8f-145">Ad mediation enables you to maximize your ad revenue and app promotion capabilities by displaying ads from multiple ad networks, including ads from other paid ad networks such as Taboola and Smaato and ads for Microsoft app promotion campaigns.</span></span>

3.  <span data-ttu-id="fea8f-146">Ersetzen Sie in Ihrem Code die Testwerte der Anzeigeneinheit (**applicationId** und **adUnitId**) mit den Live-Werten, die Sie in Dev Center generiert haben.</span><span class="sxs-lookup"><span data-stu-id="fea8f-146">In your code, replace the test ad unit values (**applicationId** and **adUnitId**) with the live values you generated in Dev Center.</span></span>

4.  <span data-ttu-id="fea8f-147">[Übermitteln Sie Ihre App](../publish/app-submissions.md) mithilfe des Dev Center-Dashboards an den Store.</span><span class="sxs-lookup"><span data-stu-id="fea8f-147">[Submit your app](../publish/app-submissions.md) to the Store using the Dev Center dashboard.</span></span>

5.  <span data-ttu-id="fea8f-148">Überprüfen Sie die [Anzeigenvermittlungsberichte](../publish/advertising-performance-report.md) im Dev Center-Dashboard.</span><span class="sxs-lookup"><span data-stu-id="fea8f-148">Review your [advertising performance reports](../publish/advertising-performance-report.md) in the Dev Center dashboard.</span></span>             

<span id="manage" />
## <a name="manage-ad-units-for-multiple-ad-controls-in-your-app"></a><span data-ttu-id="fea8f-149">Verwalten von Anzeigeeinheiten für mehrere Steuerelemente von Anzeigen in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="fea8f-149">Manage ad units for multiple ad controls in your app</span></span>

<span data-ttu-id="fea8f-150">Sie können mehrere **AdControl** Objekte in einer einzelnen App nutzen (z.B. jede Seite in Ihrer App hostet ein anderes **AdControl** Objekt).</span><span class="sxs-lookup"><span data-stu-id="fea8f-150">You can use multiple **AdControl** objects in a single app (for example, each page in your app might host a different **AdControl** object).</span></span> <span data-ttu-id="fea8f-151">In diesem Fall wird empfohlen, dass Sie jedem Steuerelement eine andere Anzeigeneinheit zuweisen.</span><span class="sxs-lookup"><span data-stu-id="fea8f-151">In this scenario, we recommend that you assign a different ad unit to each control.</span></span> <span data-ttu-id="fea8f-152">Durch das Verwenden verschiedener Anzeigeeinheiten für jedes Steuerelement können Sie für jedes Steuerelement [die Einstellungen für die Anzeigenvermittlung konfigurieren](../publish/monetize-with-ads.md#mediation) und diskrete [Berichtsdaten](../publish/advertising-performance-report.md).</span><span class="sxs-lookup"><span data-stu-id="fea8f-152">Using different ad units for each control enables you to separately [configure the mediation settings](../publish/monetize-with-ads.md#mediation) and get discrete [reporting data](../publish/advertising-performance-report.md) for each control.</span></span> <span data-ttu-id="fea8f-153">Außerdem können unsere Dienste so die Werbung optimieren, die wir in Ihrer App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="fea8f-153">This also enables our services to better optimize the ads we serve to your app.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fea8f-154">Sie können jede Anzeigeneinheit in nur einer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="fea8f-154">You can use each ad unit in only one app.</span></span> <span data-ttu-id="fea8f-155">Wenn Sie eine Anzeigeneinheit in mehr als einer App verwenden, werden für die Ad-Einheit keine Anzeigen platziert.</span><span class="sxs-lookup"><span data-stu-id="fea8f-155">If you use an ad unit in more than one app, ads will not be served for that ad unit.</span></span>

## <a name="related-topics"></a><span data-ttu-id="fea8f-156">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="fea8f-156">Related topics</span></span>

* [<span data-ttu-id="fea8f-157">Anzeigenbeispiele auf GitHub</span><span class="sxs-lookup"><span data-stu-id="fea8f-157">Advertising samples on GitHub</span></span>](http://aka.ms/githubads)
* [<span data-ttu-id="fea8f-158">Einrichten von Anzeigenblöcken für die App</span><span class="sxs-lookup"><span data-stu-id="fea8f-158">Set up ad units for your app</span></span>](../monetize/set-up-ad-units-in-your-app.md)
