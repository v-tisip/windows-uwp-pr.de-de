---
author: mcleanbyron
ms.assetid: 4e7c2388-b94e-4828-a104-14fa33f6eb2d
description: "Hier erfahren Sie, wie Sie die AdControl-Klasse nutzen können, um Werbebanner in einer XAML-App für Windows 10 (UWP), Windows 8.1 oder Windows Phone 8.1 anzuzeigen."
title: "„AdControl“ in XAML und .NET"
ms.author: mcleans
ms.date: 06/26/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, AdControl, Anzeigensteuerelement, XAML, .NET, exemplarische Vorgehensweise
ms.openlocfilehash: be273ca4c17edb4affa5e0abb4b3317b03893280
ms.sourcegitcommit: 8c4d50ef819ed1a2f8cac4eebefb5ccdaf3fa898
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2017
---
# <a name="adcontrol-in-xaml-and-net"></a><span data-ttu-id="e942d-104">„AdControl“ in XAML und .NET</span><span class="sxs-lookup"><span data-stu-id="e942d-104">AdControl in XAML and .NET</span></span>


<span data-ttu-id="e942d-105">In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie die [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Klasse nutzen können, um Werbebanner in einer XAML-App für Windows 10 (UWP), Windows 8.1 oder Windows Phone 8.1 anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e942d-105">This walkthrough shows how to use the [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) class to display banner ads in a XAML app for Windows 10 (UWP), Windows 8.1, or Windows Phone 8.1.</span></span>

<span data-ttu-id="e942d-106">Ein vollständiges Beispiel-Projekt, das veranschaulicht, wie Sie einer XAML-App mithilfe von C# und C++ Werbebanner hinzufügen, finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).</span><span class="sxs-lookup"><span data-stu-id="e942d-106">For a complete sample project that demonstrates how to add banner ads to a XAML app using C# and C++, see the [advertising samples on GitHub](http://aka.ms/githubads).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e942d-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e942d-107">Prerequisites</span></span>

* <span data-ttu-id="e942d-108">Für UWP-Apps: Installieren Sie das [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) mit Visual Studio2015 oder einer neueren Version.</span><span class="sxs-lookup"><span data-stu-id="e942d-108">For UWP apps: install the [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp) with Visual Studio 2015 or a later release.</span></span>
* <span data-ttu-id="e942d-109">Für Windows8.1- oder Windows Phone8.1-Apps: Installieren Sie das [Microsoft Advertising SDK für Windows und Windows Phone8.x](http://aka.ms/store-8-sdk) mit Visual Studio2015 oder Visual Studio2013.</span><span class="sxs-lookup"><span data-stu-id="e942d-109">For Windows 8.1 or Windows Phone 8.1 apps: install the [Microsoft Advertising SDK for Windows and Windows Phone 8.x](http://aka.ms/store-8-sdk) with Visual Studio 2015 or Visual Studio 2013.</span></span>

## <a name="code-development"></a><span data-ttu-id="e942d-110">Codeentwicklung</span><span class="sxs-lookup"><span data-stu-id="e942d-110">Code development</span></span>

1. <span data-ttu-id="e942d-111">Öffnen Sie in Visual Studio Ihr Projekt oder erstellen Sie ein neues Projekt.</span><span class="sxs-lookup"><span data-stu-id="e942d-111">In Visual Studio, open your project or create a new project.</span></span>

2. <span data-ttu-id="e942d-112">Sollte in Ihrem Projekt die Zielplattform **ANYCPU** definiert sein, müssen Sie eine architekturspezifische Buildausgabe verwenden (z. B. **X86**) und das Projekt entsprechend aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="e942d-112">If your project targets **Any CPU**, update your project to use an architecture-specific build output (for example, **x86**).</span></span> <span data-ttu-id="e942d-113">Sollte in Ihrem Projekt die Zielplattform **ANYCPU** definiert sein, können Sie bei den folgenden Schritten keinen Verweis auf die Microsoft Advertising-Bibliotheken hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e942d-113">If your project targets **Any CPU**, you will not be able to successfully add a reference to the Microsoft advertising library in the following steps.</span></span> <span data-ttu-id="e942d-114">Weitere Informationen finden Sie unter [Referenzfehler, die durch die Ausrichtung auf eine beliebige CPU (Any CPU) in Ihrem Projekt verursacht werden](known-issues-for-the-advertising-libraries.md#reference_errors).</span><span class="sxs-lookup"><span data-stu-id="e942d-114">For more information, see [Reference errors caused by targeting Any CPU in your project](known-issues-for-the-advertising-libraries.md#reference_errors).</span></span>

1.  <span data-ttu-id="e942d-115">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen...** aus.</span><span class="sxs-lookup"><span data-stu-id="e942d-115">From the **Solution Explorer** window, right click **References**, and select **Add Reference…**</span></span>

2.  <span data-ttu-id="e942d-116">Wählen Sie im **Verweis-Manager** je nach Projekttyp einen der folgenden Verweise aus:</span><span class="sxs-lookup"><span data-stu-id="e942d-116">In **Reference Manager**, select one of the following references depending on your project type:</span></span>

    -   <span data-ttu-id="e942d-117">Für ein Projekt für die Universelle Windows-Plattform (UWP): Erweitern Sie **Universelles Windows**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Microsoft Advertising SDK für XAML** (Version 10.0).</span><span class="sxs-lookup"><span data-stu-id="e942d-117">For a Universal Windows Platform (UWP) project: Expand **Universal Windows**, click **Extensions**, and then select the check box next to **Microsoft Advertising SDK for XAML** (Version 10.0).</span></span>

    -   <span data-ttu-id="e942d-118">Für ein Windows 8.1-Projekt: Erweitern Sie **Windows 8.1**, klicken Sie auf **Erweiterungen**, und aktivieren Sie anschließend das Kontrollkästchen neben **Ad Mediator SDK für Windows 8.1 XAML**.</span><span class="sxs-lookup"><span data-stu-id="e942d-118">For a Windows 8.1 project: Expand **Windows 8.1**, click **Extensions**, and then select the check box next to **Ad Mediator SDK for Windows 8.1 XAML**.</span></span> <span data-ttu-id="e942d-119">Mit dieser Option werden die Microsoft Advertising- und Ad Mediator-Bibliotheken dem Projekt hinzugefügt. Die Ad Mediator-Bibliotheken können Sie jedoch außer Acht lassen.</span><span class="sxs-lookup"><span data-stu-id="e942d-119">This option will add both the Microsoft advertising and ad mediator libraries to your project, but you can ignore the ad mediator libraries.</span></span>

    -   <span data-ttu-id="e942d-120">Für ein Windows Phone 8.1-Projekt: Erweitern Sie **Windows Phone 8.1**, klicken Sie auf **Erweiterungen** und aktivieren Sie anschließend das Kontrollkästchen neben **Ad Mediator SDK für Windows Phone 8.1 XAML**.</span><span class="sxs-lookup"><span data-stu-id="e942d-120">For a Windows Phone 8.1 project: Expand **Windows Phone 8.1**, click **Extensions**, and then select the check box next to **Ad Mediator SDK for Windows Phone 8.1 XAML**.</span></span> <span data-ttu-id="e942d-121">Mit dieser Option werden die Microsoft Advertising- und Ad Mediator-Bibliotheken dem Projekt hinzugefügt. Die Ad Mediator-Bibliotheken können Sie jedoch außer Acht lassen.</span><span class="sxs-lookup"><span data-stu-id="e942d-121">This option will add both the Microsoft advertising and ad mediator libraries to your project, but you can ignore the ad mediator libraries.</span></span>

    ![addreferences](images/13-a84c026e-b283-44f2-8816-f950a1ef89aa.png)

3.  <span data-ttu-id="e942d-123">Klicken Sie im **Verweis-Manager** auf „OK“.</span><span class="sxs-lookup"><span data-stu-id="e942d-123">In **Reference Manager**, click OK.</span></span>

4.  <span data-ttu-id="e942d-124">Ändern Sie das XAML für die Seite, in die Sie Werbung einbetten möchten, um den **Microsoft.Advertising.WinRT.UI**-Namespace miteinzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="e942d-124">Modify the XAML for the page where you are embedding advertising to include the **Microsoft.Advertising.WinRT.UI** namespace.</span></span> <span data-ttu-id="e942d-125">Beispiel: Bei der Standard-Beispiel-App, die von Visual Studio generiert wird (in dieser App mit MyAdFundedWindows10AppXAML bezeichnet), heißt die XAML-Seite **"MainPage.xaml"**.</span><span class="sxs-lookup"><span data-stu-id="e942d-125">For example, in the default sample app generated by Visual Studio (named, in this app, MyAdFundedWindows10AppXAML), the XAML page is **MainPage.XAML**.</span></span>

    <span data-ttu-id="e942d-126">Der Bereich **Seite** der von Visual Studio generierten Datei „MainPage.xaml“ hat den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="e942d-126">The **Page** section of the MainPage.xaml file generated by Visual Studio has the following code.</span></span>

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

    <span data-ttu-id="e942d-127">Fügen Sie den Namespace-Verweis **Microsoft.Advertising.WinRT.UI** ein, sodass der Abschnitt **Seite** der Datei „MainPage.xaml“ den folgenden Code hat.</span><span class="sxs-lookup"><span data-stu-id="e942d-127">Add the namespace reference **Microsoft.Advertising.WinRT.UI** so the **Page** section of the MainPage.xaml file has the following code.</span></span>

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

5. <span data-ttu-id="e942d-128">Fügen Sie im **Raster**-Tag den Code für die **AdControl** ein.</span><span class="sxs-lookup"><span data-stu-id="e942d-128">In the **Grid** tag, add the code for the **AdControl**.</span></span> <span data-ttu-id="e942d-129">Weisen Sie den Eigenschaften [AdUnitId](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.adunitid.aspx) und [ApplicationId](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.applicationid.aspx) Eigenschaften auf der **Seite** die unter [Testmoduswerte](test-mode-values.md) bereitgestellten Testwerte zu.</span><span class="sxs-lookup"><span data-stu-id="e942d-129">Assign the  [AdUnitId](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.adunitid.aspx) and [ApplicationId](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.applicationid.aspx) properties in the **Page** to the test values provided in [Test mode values](test-mode-values.md).</span></span> <span data-ttu-id="e942d-130">Passen Sie zudem Höhe und Breite des Steuerelements an, damit es einer der [unterstützten Anzeigengrößen für Werbebanner](supported-ad-sizes-for-banner-ads.md) entspricht.</span><span class="sxs-lookup"><span data-stu-id="e942d-130">Also adjust the height and width of the control so it is one of the [supported ad sizes for banner ads](supported-ad-sizes-for-banner-ads.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="e942d-131">Jedes **AdControl** verfügt über ein entsprechendes *Anzeigeneinheit*, die von unseren Diensten verwendet wird, um Werbung auf das Steuerelement zu übertragen, und jede Anzeigeneinheit besteht aus einer *Anzeigeneinheits-ID* und *Anwendungs-ID*.</span><span class="sxs-lookup"><span data-stu-id="e942d-131">Every **AdControl** has a corresponding *ad unit* that is used by our services to serve ads to the control, and every ad unit consists of an *ad unit ID* and *application ID*.</span></span> <span data-ttu-id="e942d-132">In den folgenden Schrittenweisen Sie eine Test Anzeigeneinheits-ID und Anwendungs-ID für Ihr Steuerelement zu.</span><span class="sxs-lookup"><span data-stu-id="e942d-132">In these steps, you assign test ad unit ID and application ID values to your control.</span></span> <span data-ttu-id="e942d-133">Diese Testwerte können nur in einer Testversion Ihrer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e942d-133">These test values can only be used in a test version of your app.</span></span> <span data-ttu-id="e942d-134">Bevor Sie Ihre App im Store veröffentlichen, müssen Sie die [Testwerte mit den Livewerten aus dem Windows Dev Center ersetzen](#release).</span><span class="sxs-lookup"><span data-stu-id="e942d-134">Before you publish your app to the Store, you must [replace these test values with live values](#release) from Windows Dev Center.</span></span>

    <span data-ttu-id="e942d-135">Das vollständige **Raster**-Tag sieht aus wie dieser Code.</span><span class="sxs-lookup"><span data-stu-id="e942d-135">The complete **Grid** tag looks like this code.</span></span>

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

    <span data-ttu-id="e942d-136">Der vollständige Code für die Datei „MainPage.xaml“ sollte wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="e942d-136">The complete code for the MainPage.xaml file should look like this.</span></span>

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

6.  <span data-ttu-id="e942d-137">Kompilieren und Ausführen der App, um sie mit einer Anzeige zu sehen</span><span class="sxs-lookup"><span data-stu-id="e942d-137">Compile and run the app to see it with an ad.</span></span>

<span id="release" />
## <a name="release-your-app-with-live-ads-using-windows-dev-center"></a><span data-ttu-id="e942d-138">Veröffentlichen der App mit Live-Werbung mithilfe von Windows Dev Center</span><span class="sxs-lookup"><span data-stu-id="e942d-138">Release your app with live ads using Windows Dev Center</span></span>

1.  <span data-ttu-id="e942d-139">Rufen Sie im Dev Center-Dashboard die Seite [Monetarisierung mit Anzeigen](../publish/monetize-with-ads.md) für Ihre App auf, und [erstellen Sie eine Anzeigeneinheit](../monetize/set-up-ad-units-in-your-app.md).</span><span class="sxs-lookup"><span data-stu-id="e942d-139">In the Dev Center dashboard, go to the [Monetize with ads](../publish/monetize-with-ads.md) page for your app and [create an ad unit](../monetize/set-up-ad-units-in-your-app.md).</span></span> <span data-ttu-id="e942d-140">Geben Sie als Einheitentyp **Banner** an.</span><span class="sxs-lookup"><span data-stu-id="e942d-140">For the ad unit type, specify **Banner**.</span></span> <span data-ttu-id="e942d-141">Notieren Sie sich die Anzeigeeinheits-ID und die Anwendungs-ID.</span><span class="sxs-lookup"><span data-stu-id="e942d-141">Make note of both the ad unit ID and the application ID.</span></span>

2. <span data-ttu-id="e942d-142">Wenn Ihre App eine UWP-App für Windows10 ist, können Sie optional die Anzeigenvermittlung für **AdControl** aktivieren, indem Sie im Abschnitt [Anzeigenvermittlung](../publish/monetize-with-ads.md#mediation) auf der Seite [Monetarisierung durch Anzeigen](../publish/monetize-with-ads.md) die Einstellungen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e942d-142">If your app is a UWP app for Windows 10, you can optionally enable ad mediation for the **AdControl** by configuring the settings in the [Ad mediation](../publish/monetize-with-ads.md#mediation) section on the [Monetize with ads](../publish/monetize-with-ads.md) page.</span></span> <span data-ttu-id="e942d-143">Mit der Anzeigenvermittlung können Sie Ihre Anzeigenumsätze maximieren und Werbefunktionen optimal nutzen, indem Sie Anzeigen aus mehreren Anzeigennetzwerken anzeigen, einschließlich Anzeigen aus anderen kostenpflichtigen Anzeigennetzwerken wie Taboola und Smaato sowie Anzeigen zu Werbekampagnen für Microsoft-Apps.</span><span class="sxs-lookup"><span data-stu-id="e942d-143">Ad mediation enables you to maximize your ad revenue and app promotion capabilities by displaying ads from multiple ad networks, including ads from other paid ad networks such as Taboola and Smaato and ads for Microsoft app promotion campaigns.</span></span>

3.  <span data-ttu-id="e942d-144">Ersetzen Sie in Ihrem Code die Testwerte der Anzeigeneinheit (**ApplicationId** und **AdUnitId**) mit den Live-Werten, die Sie in Dev Center generiert haben.</span><span class="sxs-lookup"><span data-stu-id="e942d-144">In your code, replace the test ad unit values (**ApplicationId** and **AdUnitId**) with the live values you generated in Dev Center.</span></span>

4.  <span data-ttu-id="e942d-145">[Übermitteln Sie Ihre App](../publish/app-submissions.md) mithilfe des Dev Center-Dashboards an den Store.</span><span class="sxs-lookup"><span data-stu-id="e942d-145">[Submit your app](../publish/app-submissions.md) to the Store using the Dev Center dashboard.</span></span>

5.  <span data-ttu-id="e942d-146">Überprüfen Sie die [Anzeigenvermittlungsberichte](../publish/advertising-performance-report.md) im Dev Center-Dashboard.</span><span class="sxs-lookup"><span data-stu-id="e942d-146">Review your [advertising performance reports](../publish/advertising-performance-report.md) in the Dev Center dashboard.</span></span>

<span id="manage" />
## <a name="manage-ad-units-for-multiple-ad-controls-in-your-app"></a><span data-ttu-id="e942d-147">Verwalten von Anzeigeeinheiten für mehrere Steuerelemente von Anzeigen in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="e942d-147">Manage ad units for multiple ad controls in your app</span></span>

<span data-ttu-id="e942d-148">Sie können mehrere **AdControl** Objekte in einer einzelnen App nutzen (z.B. jede Seite in Ihrer App hostet ein anderes **AdControl** Objekt).</span><span class="sxs-lookup"><span data-stu-id="e942d-148">You can use multiple **AdControl** objects in a single app (for example, each page in your app might host a different **AdControl** object).</span></span> <span data-ttu-id="e942d-149">In diesem Fall wird empfohlen, dass Sie jedem Steuerelement eine andere Anzeigeneinheit zuweisen.</span><span class="sxs-lookup"><span data-stu-id="e942d-149">In this scenario, we recommend that you assign a different ad unit to each control.</span></span> <span data-ttu-id="e942d-150">Durch das Verwenden verschiedener Anzeigeeinheiten für jedes Steuerelement können Sie für jedes Steuerelement [die Einstellungen für die Anzeigenvermittlung konfigurieren](../publish/monetize-with-ads.md#mediation) und diskrete [Berichtsdaten](../publish/advertising-performance-report.md).</span><span class="sxs-lookup"><span data-stu-id="e942d-150">Using different ad units for each control enables you to separately [configure the mediation settings](../publish/monetize-with-ads.md#mediation) and get discrete [reporting data](../publish/advertising-performance-report.md) for each control.</span></span> <span data-ttu-id="e942d-151">Außerdem können unsere Dienste so die Werbung optimieren, die wir in Ihrer App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e942d-151">This also enables our services to better optimize the ads we serve to your app.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e942d-152">Sie können jede Anzeigeneinheit in nur einer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="e942d-152">You can use each ad unit in only one app.</span></span> <span data-ttu-id="e942d-153">Wenn Sie eine Anzeigeneinheit in mehr als einer App verwenden, werden für die Ad-Einheit keine Anzeigen platziert.</span><span class="sxs-lookup"><span data-stu-id="e942d-153">If you use an ad unit in more than one app, ads will not be served for that ad unit.</span></span>

## <a name="notes"></a><span data-ttu-id="e942d-154">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e942d-154">Notes</span></span>

* <span data-ttu-id="e942d-155">C#: Unter [Beispiel für XAML-Eigenschaften](xaml-properties-example.md) finden Sie ein Beispiel dafür, wie Sie **AdControl**-Ereignissen Ereignishandler zuweisen.</span><span class="sxs-lookup"><span data-stu-id="e942d-155">C#: See [XAML properties example](xaml-properties-example.md) for an example of how to assign event handlers to **AdControl** events.</span></span> <span data-ttu-id="e942d-156">Sehen Sie sich daraufhin [AdControl-Ereignisse in C#](adcontrol-events-in-c.md) an. Hier finden Sie Beispielcode, der in C# geschriebene Ereignishandler zeigt.</span><span class="sxs-lookup"><span data-stu-id="e942d-156">Then see [AdControl events in C#](adcontrol-events-in-c.md) for sample code that shows event handlers written in C#.</span></span>

* <span data-ttu-id="e942d-157">C++: Die aktuelle Version der Microsoft Advertising-Bibliotheken unterstützt C++.</span><span class="sxs-lookup"><span data-stu-id="e942d-157">C++: The current release of the Microsoft advertising libraries support C++.</span></span> <span data-ttu-id="e942d-158">Die **AdControl**-Klasse wird in systemeigenem C++ implementiert und bewirkt nicht, dass die .NET CLR geladen wird.</span><span class="sxs-lookup"><span data-stu-id="e942d-158">The **AdControl** class is implemented in native C++, and does not load the .NET CLR.</span></span> <span data-ttu-id="e942d-159">Codebeispiele, die die Verwendung von **AdControl** in C++ veranschaulichen, finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).</span><span class="sxs-lookup"><span data-stu-id="e942d-159">For code examples that demonstrate how to use **AdControl** in C++, see the [advertising samples on GitHub](http://aka.ms/githubads).</span></span>

* <span data-ttu-id="e942d-160">Visual Basic: Unter [Beispiel für XAML-Eigenschaften](xaml-properties-example.md) finden Sie ein Beispiel dafür, wie Sie **AdControl**-Ereignissen Ereignishandler zuweisen.</span><span class="sxs-lookup"><span data-stu-id="e942d-160">Visual Basic: See [XAML properties example](xaml-properties-example.md) for an example of how to assign event handlers to **AdControl** events.</span></span>

* <span data-ttu-id="e942d-161">Fehlerbehandlung: Weitere Informationen zum Behandeln von Fehlern erhalten Sie unter [AdControl-Fehlerbehandlung](adcontrol-error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="e942d-161">Error Handling: To learn about how to handle errors, see [AdControl error handling](adcontrol-error-handling.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="e942d-162">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e942d-162">Related topics</span></span>

* [<span data-ttu-id="e942d-163">Anzeigenbeispiele auf GitHub</span><span class="sxs-lookup"><span data-stu-id="e942d-163">Advertising samples on GitHub</span></span>](http://aka.ms/githubads)
* [<span data-ttu-id="e942d-164">Einrichten von Anzeigenblöcken für die App</span><span class="sxs-lookup"><span data-stu-id="e942d-164">Set up ad units for your app</span></span>](../monetize/set-up-ad-units-in-your-app.md)
