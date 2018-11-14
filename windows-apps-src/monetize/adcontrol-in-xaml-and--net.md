---
author: Xansky
ms.assetid: 4e7c2388-b94e-4828-a104-14fa33f6eb2d
description: Hier erfahren Sie, wie Sie die AdControl-Klasse nutzen können, um Werbebanner in einer XAML-App für Windows 10 (UWP) anzuzeigen.
title: „AdControl“ in XAML und .NET
ms.author: mhopkins
ms.date: 03/22/2018
ms.topic: article
keywords: Windows10, UWP, Anzeigen, Werbung, AdControl, Anzeigensteuerelement, XAML, .NET, exemplarische Vorgehensweise
ms.localizationpriority: medium
ms.openlocfilehash: b2346fceaae3996de8aa54640c206b5fcd8c4a87
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "6669659"
---
# <a name="adcontrol-in-xaml-and-net"></a><span data-ttu-id="5e9a0-104">„AdControl“ in XAML und .NET</span><span class="sxs-lookup"><span data-stu-id="5e9a0-104">AdControl in XAML and .NET</span></span>


<span data-ttu-id="5e9a0-105">In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie die [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol)-Klasse nutzen können, um Werbebanner in einer Universellen Windows-Plattform-, XAML-App für Windows 10 anzuzeigen, die in C++ implementiert wurden.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-105">This walkthrough shows how to use the [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) class to display banner ads in a Universal Windows Platform (UWP) XAML app for Windows 10 that is implemented using C#.</span></span>

> [!NOTE]
> <span data-ttu-id="5e9a0-106">Das Microsoft Advertising-SDK unterstützt auch XAML-Apps, die mit C++ implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-106">The Microsoft Advertising SDK also supports XAML apps that are implemented using C++.</span></span> <span data-ttu-id="5e9a0-107">Ein vollständiges Beispielprojekt finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-107">For a complete sample project, see the [advertising samples on GitHub](http://aka.ms/githubads).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e9a0-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="5e9a0-108">Prerequisites</span></span>

* <span data-ttu-id="5e9a0-109">Installieren Sie das [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) mit Visual Studio2015 oder einer neueren Version von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-109">Install the [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp) with Visual Studio 2015 or a later release of Visual Studio.</span></span> <span data-ttu-id="5e9a0-110">Installationsanweisungen finden Sie in [diesem Artikel](install-the-microsoft-advertising-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-110">For installation instructions, see [this article](install-the-microsoft-advertising-libraries.md).</span></span>

## <a name="integrate-a-banner-ad-into-your-app"></a><span data-ttu-id="5e9a0-111">Banneranzeige in Ihrer App integrieren</span><span class="sxs-lookup"><span data-stu-id="5e9a0-111">Integrate a banner ad into your app</span></span>

1. <span data-ttu-id="5e9a0-112">Öffnen Sie in Visual Studio Ihr Projekt oder erstellen Sie ein neues Projekt.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-112">In Visual Studio, open your project or create a new project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5e9a0-113">Wenn Sie ein vorhandenes Projekt verwenden, öffnen Sie die Datei "Package.appxmanifest" in Ihrem Projekt, und stellen sicher, dass die **Internet (Client)**-Funktion aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-113">If you're using an existing project, open the Package.appxmanifest file in your project and ensure that the **Internet (Client)** capability is selected.</span></span> <span data-ttu-id="5e9a0-114">Ihre App benötigt diese Funktion, um Testanzeigen und Live-Werbung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-114">Your app needs this capability to receive test ads and live ads.</span></span>

2. <span data-ttu-id="5e9a0-115">Sollte in Ihrem Projekt die Zielplattform **Any CPU** definiert sein, müssen Sie eine architekturspezifische Buildausgabe verwenden (z.B. **x86**) und das Projekt entsprechend aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-115">If your project targets **Any CPU**, update your project to use an architecture-specific build output (for example, **x86**).</span></span> <span data-ttu-id="5e9a0-116">Sollte in Ihrem Projekt die Zielplattform **ANYCPU** definiert sein, können Sie bei den folgenden Schritten keinen Verweis auf die Microsoft Advertising-Bibliotheken hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-116">If your project targets **Any CPU**, you will not be able to successfully add a reference to the Microsoft advertising library in the following steps.</span></span> <span data-ttu-id="5e9a0-117">Weitere Informationen finden Sie unter [Referenzfehler, die durch die Ausrichtung auf eine beliebige CPU (Any CPU) in Ihrem Projekt verursacht werden](known-issues-for-the-advertising-libraries.md#reference_errors).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-117">For more information, see [Reference errors caused by targeting Any CPU in your project](known-issues-for-the-advertising-libraries.md#reference_errors).</span></span>

3. <span data-ttu-id="5e9a0-118">Hinzufügen eines Verweises auf die Microsoft Advertising-SDK in Ihrem Projekt:</span><span class="sxs-lookup"><span data-stu-id="5e9a0-118">Add a reference to the Microsoft Advertising SDK in your project:</span></span>

    1. <span data-ttu-id="5e9a0-119">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen...** aus.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-119">From the **Solution Explorer** window, right click **References**, and select **Add Reference…**</span></span>
    2.  <span data-ttu-id="5e9a0-120">Erweitern Sie im **Verweis-Manager** den Knoten **Universal Windows**, klicken Sie auf **Erweiterungen**, und wählen Sie dann das Kontrollkästchen neben **Microsoft Advertising-SDK für XAML** (Version 10.0).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-120">In **Reference Manager**, expand **Universal Windows**, click **Extensions**, and then select the check box next to **Microsoft Advertising SDK for XAML** (Version 10.0).</span></span>
    3.  <span data-ttu-id="5e9a0-121">Klicken Sie im **Verweis-Manager** auf „OK“.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-121">In **Reference Manager**, click OK.</span></span>

4.  <span data-ttu-id="5e9a0-122">Ändern Sie das XAML für die Seite, in die Sie Werbung einbetten möchten, um den **Microsoft.Advertising.WinRT.UI**-Namespace miteinzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-122">Modify the XAML for the page where you are embedding advertising to include the **Microsoft.Advertising.WinRT.UI** namespace.</span></span> <span data-ttu-id="5e9a0-123">Beispiel: Bei der Standard-Beispiel-App, die von Visual Studio generiert wird (in dieser App mit MyAdFundedWindows10AppXAML bezeichnet), heißt die XAML-Seite **"MainPage.xaml"**.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-123">For example, in the default sample app generated by Visual Studio (named, in this app, MyAdFundedWindows10AppXAML), the XAML page is **MainPage.XAML**.</span></span>

    <span data-ttu-id="5e9a0-124">Der Bereich **Seite** der von Visual Studio generierten Datei „MainPage.xaml“ hat den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-124">The **Page** section of the MainPage.xaml file generated by Visual Studio has the following code.</span></span>

    ``` xml
    <Page
      x:Class="MyAdFundedWindows10AppXAML.MainPage"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:local="using:MyAdFundedWindows10AppXAML"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      mc:Ignorable="d">
      <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
      </Grid>
    </Page>
    ```

    <span data-ttu-id="5e9a0-125">Fügen Sie den Namespace-Verweis **Microsoft.Advertising.WinRT.UI** ein, sodass der Abschnitt **Seite** der Datei „MainPage.xaml“ den folgenden Code hat.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-125">Add the namespace reference **Microsoft.Advertising.WinRT.UI** so the **Page** section of the MainPage.xaml file has the following code.</span></span>

    ``` xml
    <Page
      x:Class="MyAdFundedWindows10AppXAML.MainPage"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:local="using:MyAdFundedWindows10AppXAML"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:UI="using:Microsoft.Advertising.WinRT.UI"
      mc:Ignorable="d">
      <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
      </Grid>
    </Page>
    ```

5. <span data-ttu-id="5e9a0-126">Fügen Sie im **Raster**-Tag den Code für die **AdControl** ein.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-126">In the **Grid** tag, add the code for the **AdControl**.</span></span> <span data-ttu-id="5e9a0-127">Weisen Sie die Eigenschaften [AdUnitId](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.adunitid) und [ApplicationId](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.applicationid) dem [Testanzeigen-Einheitenwert](set-up-ad-units-in-your-app.md#test-ad-units) hinzu.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-127">Assign the  [AdUnitId](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.adunitid) and [ApplicationId](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.applicationid) properties to the [test ad unit values](set-up-ad-units-in-your-app.md#test-ad-units).</span></span> <span data-ttu-id="5e9a0-128">Passen Sie zudem **Höhe** und **Breite** des Steuerelements an, damit es einer der [unterstützten Anzeigengrößen für Werbebanner](supported-ad-sizes-for-banner-ads.md) entspricht.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-128">Also adjust the **Height** and **Width** of the control so it is one of the [supported ad sizes for banner ads](supported-ad-sizes-for-banner-ads.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="5e9a0-129">Jedes **AdControl** verfügt über ein entsprechendes *Anzeigeneinheit*, die von unseren Diensten verwendet wird, um Werbung auf das Steuerelement zu übertragen, und jede Anzeigeneinheit besteht aus einer *Anzeigeneinheits-ID* und *Anwendungs-ID*.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-129">Every **AdControl** has a corresponding *ad unit* that is used by our services to serve ads to the control, and every ad unit consists of an *ad unit ID* and *application ID*.</span></span> <span data-ttu-id="5e9a0-130">In den folgenden Schrittenweisen Sie eine Test Anzeigeneinheits-ID und Anwendungs-ID für Ihr Steuerelement zu.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-130">In these steps, you assign test ad unit ID and application ID values to your control.</span></span> <span data-ttu-id="5e9a0-131">Dieser Test Werte können nur in einer Testversion Ihrer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-131">These test values can only be used in a test version of your app.</span></span> <span data-ttu-id="5e9a0-132">Bevor Sie Ihre app im Store veröffentlichen, müssen Sie [Ersetzen Testwerte mit den live-Werten](#release) aus dem Partner Center.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-132">Before you publish your app to the Store, you must [replace these test values with live values](#release) from Partner Center.</span></span>

    <span data-ttu-id="5e9a0-133">Das vollständige **Raster**-Tag sieht aus wie dieser Code.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-133">The complete **Grid** tag looks like this code.</span></span>

    ``` xml
    <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
        <UI:AdControl ApplicationId="3f83fe91-d6be-434d-a0ae-7351c5a997f1"
            AdUnitId="test"
            HorizontalAlignment="Left"
            Height="250"
            VerticalAlignment="Top"
            Width="300"/>
    </Grid>
    ```

    <span data-ttu-id="5e9a0-134">Der vollständige Code für die Datei „MainPage.xaml“ sollte wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-134">The complete code for the MainPage.xaml file should look like this.</span></span>

    ``` xml
    <Page
      x:Class="MyAdFundedWindows10AppXAML.MainPage"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:local="using:MyAdFundedWindows10AppXAML"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:UI="using:Microsoft.Advertising.WinRT.UI"
      mc:Ignorable="d">
      <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <UI:AdControl ApplicationId="3f83fe91-d6be-434d-a0ae-7351c5a997f1"
                  AdUnitId="test"
                  HorizontalAlignment="Left"
                  Height="250"
                  VerticalAlignment="Top"
                  Width="300"/>
      </Grid>
    </Page>
    ```

6.  <span data-ttu-id="5e9a0-135">Kompilieren Sie die App, und führen Sie sie aus, um sie mit einer Anzeige zu sehen.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-135">Compile and run the app to see it with an ad.</span></span>

<span id="release" />

## <a name="release-your-app-with-live-ads"></a><span data-ttu-id="5e9a0-136">Veröffentlichen Ihrer App mit Live-Anzeigen</span><span class="sxs-lookup"><span data-stu-id="5e9a0-136">Release your app with live ads</span></span>

1. <span data-ttu-id="5e9a0-137">Stellen Sie sicher, dass die Verwendung von Werbebannern in Ihrer App unseren [Richtlinien für das Anzeigen von Werbebannern](ui-and-user-experience-guidelines.md#guidelines-for-banner-ads) entspricht.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-137">Make sure your use of banner ads in your app follows our [guidelines for banner ads](ui-and-user-experience-guidelines.md#guidelines-for-banner-ads).</span></span>

2.  <span data-ttu-id="5e9a0-138">Im Partner Center wechseln Sie zu der Seite [In-app-anzeigen](../publish/in-app-ads.md) und [eine anzeigeneinheit erstellen](set-up-ad-units-in-your-app.md#live-ad-units).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-138">In Partner Center, go to the [In-app ads](../publish/in-app-ads.md) page and [create an ad unit](set-up-ad-units-in-your-app.md#live-ad-units).</span></span> <span data-ttu-id="5e9a0-139">Geben Sie als Typ für die Anzeigeneinheit **Banner** an.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-139">For the ad unit type, specify **Banner**.</span></span> <span data-ttu-id="5e9a0-140">Notieren Sie die Anzeigeneinheits-ID und die Anwendungs-ID.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-140">Make note of both the ad unit ID and the application ID.</span></span>
    > [!NOTE]
    > <span data-ttu-id="5e9a0-141">Die Anwendungs-IDs für Test-Anzeigeneinheiten und Live-UWP-Anzeigeneinheiten besitzen unterschiedliche Formate.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-141">The application ID values for test ad units and live UWP ad units have different formats.</span></span> <span data-ttu-id="5e9a0-142">Testanwendungs-ID sind GUIDs.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-142">Test application ID values are GUIDs.</span></span> <span data-ttu-id="5e9a0-143">Wenn Sie eine live-UWP-anzeigeneinheit im Partner Center erstellen, entspricht die Anwendungs-ID-Wert für die anzeigeneinheit immer der Store-ID für Ihre app (der ein Beispiel für Store-ID-Wert ist 9nblggh4r315).).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-143">When you create a live UWP ad unit in Partner Center, the application ID value for the ad unit always matches the Store ID for your app (an example Store ID value looks like 9NBLGGH4R315).</span></span>

3. <span data-ttu-id="5e9a0-144">Sie können optional die Anzeigenvermittlung für **AdControl** durch Konfigurieren der [Vermittlungseinstellungen](../publish/in-app-ads.md#mediation) auf der Seite [In-App-Anzeigen](../publish/in-app-ads.md) aktivieren.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-144">You can optionally enable ad mediation for the **AdControl** by configuring the settings in the [Mediation settings](../publish/in-app-ads.md#mediation) section on the [In-app ads](../publish/in-app-ads.md) page.</span></span> <span data-ttu-id="5e9a0-145">Mit der Anzeigenvermittlung können Sie Ihre Anzeigenumsätze maximieren und Werbefunktionen optimal nutzen, indem Sie Anzeigen aus mehreren Anzeigennetzwerken anzeigen, einschließlich Anzeigen aus anderen kostenpflichtigen Anzeigennetzwerken wie Taboola und Smaato sowie Anzeigen zu Werbekampagnen für Microsoft-Apps.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-145">Ad mediation enables you to maximize your ad revenue and app promotion capabilities by displaying ads from multiple ad networks, including ads from other paid ad networks such as Taboola and Smaato and ads for Microsoft app promotion campaigns.</span></span>

4.  <span data-ttu-id="5e9a0-146">Ersetzen Sie in Ihrem Code die Testwerte der anzeigeneinheit (**ApplicationId** und **AdUnitId**) mit den live-Werten, die Sie im Partner Center generiert.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-146">In your code, replace the test ad unit values (**ApplicationId** and **AdUnitId**) with the live values you generated in Partner Center.</span></span>

5.  <span data-ttu-id="5e9a0-147">[Übermitteln Ihrer app](../publish/app-submissions.md) mithilfe der Partner Center an den Store.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-147">[Submit your app](../publish/app-submissions.md) to the Store using Partner Center.</span></span>

6.  <span data-ttu-id="5e9a0-148">Überprüfen Sie Ihre [Berichte zur anzeigenleistung](../publish/advertising-performance-report.md) im Partner Center.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-148">Review your [advertising performance reports](../publish/advertising-performance-report.md) in Partner Center.</span></span>

<span id="manage" />

## <a name="manage-ad-units-for-multiple-ad-controls-in-your-app"></a><span data-ttu-id="5e9a0-149">Verwalten von Anzeigeeinheiten für mehrere Steuerelemente von Anzeigen in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="5e9a0-149">Manage ad units for multiple ad controls in your app</span></span>

<span data-ttu-id="5e9a0-150">Sie können mehrere **AdControl** Objekte in einer einzelnen App nutzen (z.B. jede Seite in Ihrer App hostet ein anderes **AdControl** Objekt).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-150">You can use multiple **AdControl** objects in a single app (for example, each page in your app might host a different **AdControl** object).</span></span> <span data-ttu-id="5e9a0-151">In diesem Fall wird empfohlen, dass Sie jedem Steuerelement eine andere Anzeigeneinheit zuweisen.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-151">In this scenario, we recommend that you assign a different ad unit to each control.</span></span> <span data-ttu-id="5e9a0-152">Durch das Verwenden verschiedener Anzeigeeinheiten für jedes Steuerelement können Sie für jedes Steuerelement [die Einstellungen für die Anzeigenvermittlung konfigurieren](../publish/in-app-ads.md#mediation) und diskrete [Berichtsdaten](../publish/advertising-performance-report.md).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-152">Using different ad units for each control enables you to separately [configure the mediation settings](../publish/in-app-ads.md#mediation) and get discrete [reporting data](../publish/advertising-performance-report.md) for each control.</span></span> <span data-ttu-id="5e9a0-153">Außerdem können unsere Dienste so die Werbung optimieren, die wir in Ihrer App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-153">This also enables our services to better optimize the ads we serve to your app.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e9a0-154">Sie können jede Anzeigeneinheit in nur einer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-154">You can use each ad unit in only one app.</span></span> <span data-ttu-id="5e9a0-155">Wenn Sie eine Anzeigeneinheit in mehr als einer App verwenden, werden für die Ad-Einheit keine Anzeigen platziert.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-155">If you use an ad unit in more than one app, ads will not be served for that ad unit.</span></span>

## <a name="related-topics"></a><span data-ttu-id="5e9a0-156">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5e9a0-156">Related topics</span></span>

* [<span data-ttu-id="5e9a0-157">Richtlinien für Banneranzeigen</span><span class="sxs-lookup"><span data-stu-id="5e9a0-157">Guidelines for banner ads</span></span>](ui-and-user-experience-guidelines.md#guidelines-for-banner-ads)
* <span data-ttu-id="5e9a0-158">[Exemplarische Vorgehensweise zur Fehlerbehandlung in XAML/C#](error-handling-in-xamlc-walkthrough.md).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-158">[Error handling in XAML/C# walkthrough](error-handling-in-xamlc-walkthrough.md).</span></span>
* [<span data-ttu-id="5e9a0-159">Anzeigenbeispiele auf GitHub</span><span class="sxs-lookup"><span data-stu-id="5e9a0-159">Advertising samples on GitHub</span></span>](http://aka.ms/githubads)
* [<span data-ttu-id="5e9a0-160">Einrichten von Anzeigeneinheiten für die App</span><span class="sxs-lookup"><span data-stu-id="5e9a0-160">Set up ad units for your app</span></span>](set-up-ad-units-in-your-app.md)
