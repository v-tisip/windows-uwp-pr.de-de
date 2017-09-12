---
author: mcleanbyron
ms.assetid: c0450f7b-5c81-4d8c-92ef-2b1190d18af7
description: "Hier erfahren Sie, wie Sie die AdControl-Klasse nutzen können, um Werbebanner in einer Silverlight-App für Windows Phone 8.1 oder Windows Phone 8.0 anzuzeigen."
title: "„AdControl“ in Windows Phone Silverlight"
ms.author: mcleans
ms.date: 07/20/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, AdControl, Silverlight, Windows Phone
ms.openlocfilehash: f1582639757abfb6de156bf88ce8af71ba3eaacd
ms.sourcegitcommit: a9e4be98688b3a6125fd5dd126190fcfcd764f95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2017
---
# <a name="adcontrol-in-windows-phone-silverlight"></a><span data-ttu-id="e128c-104">„AdControl“ in Windows Phone Silverlight</span><span class="sxs-lookup"><span data-stu-id="e128c-104">AdControl in Windows Phone Silverlight</span></span>

<span data-ttu-id="e128c-105">In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie die [AdControl](https://msdn.microsoft.com/library/windows/apps/hh524191.aspx)-Klasse nutzen können, um Werbebanner in einer Silverlight-App für Windows Phone8.1 oder Windows Phone8.0 anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e128c-105">This walkthrough shows how to use the [AdControl](https://msdn.microsoft.com/library/windows/apps/hh524191.aspx) class to display banner ads in a Silverlight app for Windows Phone 8.1 or Windows Phone 8.0.</span></span>

<span id="silverlight_support"/>
## <a name="advertising-support-for-windows-phone-8x-silverlight-projects"></a><span data-ttu-id="e128c-106">Anzeigenunterstützung für Windows Phone8.x Silverlight-Projekte</span><span class="sxs-lookup"><span data-stu-id="e128c-106">Advertising support for Windows Phone 8.x Silverlight projects</span></span>

<span data-ttu-id="e128c-107">Einige Entwicklerszenarien werden für Windows Phone8.x Silverlight-Projekte nicht mehr unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e128c-107">Some developer scenarios are no longer supported in Windows Phone 8.x Silverlight projects.</span></span> <span data-ttu-id="e128c-108">Weitere Informationen finden Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="e128c-108">For more information, see the following table.</span></span>

|  <span data-ttu-id="e128c-109">Plattformversion</span><span class="sxs-lookup"><span data-stu-id="e128c-109">Platform version</span></span>  |  <span data-ttu-id="e128c-110">Vorhandene Projekte</span><span class="sxs-lookup"><span data-stu-id="e128c-110">Existing projects</span></span>    |   <span data-ttu-id="e128c-111">Neue Projekte</span><span class="sxs-lookup"><span data-stu-id="e128c-111">New projects</span></span>  |
|-----------------|----------------|--------------|
| <span data-ttu-id="e128c-112">Windows Phone8.0 Silverlight</span><span class="sxs-lookup"><span data-stu-id="e128c-112">Windows Phone 8.0 Silverlight</span></span>     |  <span data-ttu-id="e128c-113">Wenn Sie über ein vorhandenes Windows Phone8.0 Silverlight-Projekt verfügen, das bereits eine **AdControl** bzw. **AdMediatorControl** einer früheren Version des Universal Ad Client SDK oder Microsoft Advertising SDK verwendet, und die App bereits im Windows Store veröffentlicht wurde, können Sie das Projekt bearbeiten und neu erstellen. Zudem können Sie Ihre Änderungen auf einem Gerät debuggen oder testen.</span><span class="sxs-lookup"><span data-stu-id="e128c-113">If you have an existing Windows Phone 8.0 Silverlight project that already uses an **AdControl** or **AdMediatorControl** from an earlier release of the Universal Ad Client SDK or Microsoft Advertising SDK and this app is already published in the Windows Store, you can modify and rebuild the project, and you can debug or test your changes on a device.</span></span> <span data-ttu-id="e128c-114">Das Debuggen und Testen des Projekts im Emulator wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e128c-114">Debugging or testing the project in the emulator is not supported.</span></span>  |  <span data-ttu-id="e128c-115">Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="e128c-115">Not supported.</span></span>  |
| <span data-ttu-id="e128c-116">Windows Phone8.1 Silverlight</span><span class="sxs-lookup"><span data-stu-id="e128c-116">Windows Phone 8.1 Silverlight</span></span>    |  <span data-ttu-id="e128c-117">Wenn Sie über ein vorhandenes Windows Phone8.1 Silverlight-Projekt verfügen, das ein **AdControl** oder **AdMediatorControl** einer früheren SDK verwendet, können Sie es ändern und neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e128c-117">If you have an existing Windows Phone 8.1 Silverlight project that uses an **AdControl** or **AdMediatorControl** from an earlier SDK, you can modify and rebuild the project.</span></span> <span data-ttu-id="e128c-118">Zum Debuggen oder Testen der App müssen Sie die App jedoch im Emulator ausführen und für die Anwendungs- und Anzeigeneinheits-ID die [Testmoduswerte](test-mode-values.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="e128c-118">However, to debug or test the app, you must run the app in the emulator and use [test mode values](test-mode-values.md) for the application ID and ad unit ID.</span></span> <span data-ttu-id="e128c-119">Das Debuggen oder Testen der App auf einem Gerät wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e128c-119">Debugging or testing the app on a device is not supported.</span></span>  |   <span data-ttu-id="e128c-120">Sie können ein **AdControl** oder **AdMediatorControl** zu einem neuen Windows Phone8.1 Silverlight-Projekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e128c-120">You can add an **AdControl** or **AdMediatorControl** to a new Windows Phone 8.1 Silverlight project.</span></span> <span data-ttu-id="e128c-121">Zum Debuggen oder Testen der App müssen Sie die App jedoch im Emulator ausführen und für die Anwendungs- und Anzeigeneinheits-ID die [Testmoduswerte](test-mode-values.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="e128c-121">However, to debug or test the app, you must run the app in the emulator and use [test mode values](test-mode-values.md) for the application ID and ad unit ID.</span></span> <span data-ttu-id="e128c-122">Das Debuggen oder Testen der App auf einem Gerät wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e128c-122">Debugging or testing the app on a device is not supported.</span></span> |

## <a name="add-the-advertising-assemblies-to-your-project"></a><span data-ttu-id="e128c-123">Hinzufügen der Advertising-Assemblys zum Projekt</span><span class="sxs-lookup"><span data-stu-id="e128c-123">Add the advertising assemblies to your project</span></span>

<span data-ttu-id="e128c-124">Laden Sie zuerst das NuGet-Paket mit den Microsoft Advertising-Assemblys für Windows Phone Silverlight herunter, und installieren Sie es für Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="e128c-124">To get started, download and install the NuGet package that contains the Microsoft advertising assemblies for Windows Phone Silverlight to your project.</span></span>

1.  <span data-ttu-id="e128c-125">Öffnen Sie das Projekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e128c-125">Open your project in Visual Studio.</span></span>

2.  <span data-ttu-id="e128c-126">Klicken Sie auf **Extras**, zeigen Sie auf **NuGet-Paket-Manager**, und klicken Sie auf **Paket-Manager-Konsole**.</span><span class="sxs-lookup"><span data-stu-id="e128c-126">Click **Tools**, point to **NuGet Package Manager**, and click **Package Manager Console**.</span></span>

3.  <span data-ttu-id="e128c-127">Geben Sie im Fenster **Paket-Manager-Konsole** einen dieser Befehle ein.</span><span class="sxs-lookup"><span data-stu-id="e128c-127">In the **Package Manager Console** window, enter one of these commands.</span></span>

  * <span data-ttu-id="e128c-128">Geben Sie diesen Befehl ein, wenn Ihr Projekt für Windows Phone8.0 bestimmt ist.</span><span class="sxs-lookup"><span data-stu-id="e128c-128">If your project targets Windows Phone 8.0, enter this command.</span></span>

      ```syntax
      Install-Package Microsoft.Advertising.WindowsPhone.SL80 -Version 6.2.40501.1
      ```

  * <span data-ttu-id="e128c-129">Geben Sie diesen Befehl ein, wenn Ihr Projekt für Windows Phone8.1 bestimmt ist.</span><span class="sxs-lookup"><span data-stu-id="e128c-129">If your project targets Windows Phone 8.1, enter this command.</span></span>

      ```syntax
      Install-Package Microsoft.Advertising.WindowsPhone.SL81 -Version 8.1.50112
      ```

    <span data-ttu-id="e128c-130">Nach der Eingabe des Befehls werden alle erforderlichen Microsoft Advertising-Assemblys für Silverlight für Ihr lokales Projekt als NuGet-Pakete heruntergeladen. Verweise auf diese Assemblys werden dem Projekt automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e128c-130">After entering the command, all the necessary Microsoft advertising assemblies for Silverlight are downloaded to your local project via NuGet packages, and references to these assemblies are automatically added to your project.</span></span>

## <a name="code-your-app"></a><span data-ttu-id="e128c-131">Ihr App-Code</span><span class="sxs-lookup"><span data-stu-id="e128c-131">Code your app</span></span>


1.  <span data-ttu-id="e128c-132">Füge Sie in Ihrer Datei „WMAppManifest.xml“ dem Knoten **Funktionen** die folgenden Funktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="e128c-132">Add the following capabilities to the in the **Capabilities** node in your WMAppManifest.xml file.</span></span>

  ``` syntax
  <Capability Name="ID_CAP_IDENTITY_USER"/>
  <Capability Name="ID_CAP_MEDIALIB_PHOTO"/>
  <Capability Name="ID_CAP_PHONEDIALER"/>
  ```

  <span data-ttu-id="e128c-133">In diesem Beispiel sieht Ihr Knoten **Funktionen** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e128c-133">For this example, your **Capabilities** node looks like:</span></span>

  ``` syntax
  <Capabilities>
      <Capability Name="ID_CAP_NETWORKING"/>
      <Capability Name="ID_CAP_MEDIALIB_AUDIO"/>
      <Capability Name="ID_CAP_MEDIALIB_PLAYBACK"/>
      <Capability Name="ID_CAP_SENSORS"/>
      <Capability Name="ID_CAP_WEBBROWSERCOMPONENT"/>
      <Capability Name="ID_CAP_IDENTITY_USER"/>
      <Capability Name="ID_CAP_MEDIALIB_PHOTO"/>
      <Capability Name="ID_CAP_PHONEDIALER"/>
  </Capabilities>
  ```

2.  <span data-ttu-id="e128c-134">Optional: Speichern Sie Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="e128c-134">(Optional) Save your project.</span></span> <span data-ttu-id="e128c-135">Klicken Sie auf das Symbol **Alles speichern** oder klicken Sie im Menü **Datei** auf **Alles speichern**.</span><span class="sxs-lookup"><span data-stu-id="e128c-135">Click on the **Save All** icon or under the **File** menu click **Save All**.</span></span>

3.  <span data-ttu-id="e128c-136">Fügen Sie die Funktion **Internet (Client und Server)**zur Package.appxmanifest-Datei in Ihrem Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="e128c-136">Add the **Internet (Client & Server)** capability to the Package.appxmanifest file in your project.</span></span> <span data-ttu-id="e128c-137">Doppelklicken Sie im **Projektmappen-Explorer** auf die Datei **appxmanifest**.</span><span class="sxs-lookup"><span data-stu-id="e128c-137">In **Solution Explorer**, double click **Package.appxmanifest**.</span></span>

    ![wp81silverlightmarkup\-Solutionexplorer\-packageappxmanifest](images/13-b98c2a1a-69c3-4018-be0a-6ce010e703e7.jpg)

    <span data-ttu-id="e128c-139">Klicken Sie im **Editor** auf die Registerkarte **Funktionen**.</span><span class="sxs-lookup"><span data-stu-id="e128c-139">In the **Editor**, click the **Capabilities** tab.</span></span> <span data-ttu-id="e128c-140">Überprüfen Sie das Feld **Internet (Client und Server)**.</span><span class="sxs-lookup"><span data-stu-id="e128c-140">Check the **Internet (Client & Server)** box.</span></span>

4.  <span data-ttu-id="e128c-141">Optional: Speichern Sie Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="e128c-141">(Optional) Save your project.</span></span> <span data-ttu-id="e128c-142">Klicken Sie auf das Symbol **Alles speichern** oder klicken Sie im Menü **Datei** auf **Alles speichern**.</span><span class="sxs-lookup"><span data-stu-id="e128c-142">Click on the **Save All** icon or under the **File** menu click **Save All**.</span></span>

5.  <span data-ttu-id="e128c-143">Ändern Sie das Silverlight-Markup in der Datei „MainPage.xaml“, sodass es den **Microsoft.Advertising.Mobile.UI**- Namespace enthält.</span><span class="sxs-lookup"><span data-stu-id="e128c-143">Modify the Silverlight markup in the MainPage.xaml file to include the **Microsoft.Advertising.Mobile.UI** namespace.</span></span>

  ``` xml
  xmlns:UI="clr-namespace:Microsoft.Advertising.Mobile.UI;assembly=Microsoft.Advertising.Mobile.UI"
  ```

  <span data-ttu-id="e128c-144">Die Kopfzeile Ihrer Seite enthält den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="e128c-144">The header of your page will have the following code:</span></span>

  ``` xml
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
  xmlns:UI="clr-namespace:Microsoft.Advertising.Mobile.UI;assembly=Microsoft.Advertising.Mobile.UI"
  x:Class="PhoneApp1.MainPage"
  ```

6.  <span data-ttu-id="e128c-145">Fügen Sie im **Raster**-Tag den folgenden Code für die **AdControl** ein.</span><span class="sxs-lookup"><span data-stu-id="e128c-145">In the **Grid** tag, add the following code for the **AdControl**.</span></span> <span data-ttu-id="e128c-146">Weisen Sie den Eigenschaften **ApplicationId** und **AdUnitId** die unter [Testmoduswerte](test-mode-values.md) bereitgestellten Testwerte zu und passen Sie die Eigenschaften **Höhe** und **Breite** auf eines der [unterstützten Anzeigengrößen für Werbebanner](supported-ad-sizes-for-banner-ads.md) an.</span><span class="sxs-lookup"><span data-stu-id="e128c-146">Assign the **ApplicationId** and **AdUnitId** properties to the test values provided in [Test mode values](test-mode-values.md), and adjust the **Height** and **Width** properties to one of the [supported ad sizes for banner ads](supported-ad-sizes-for-banner-ads.md).</span></span>

  > <span data-ttu-id="e128c-147">**Hinweis**&nbsp;&nbsp;Sie ersetzen die Testwerte **ApplicationId** und **AdUnitId** durch Livewerte, bevor Sie Ihre App übermitteln.</span><span class="sxs-lookup"><span data-stu-id="e128c-147">**Note**&nbsp;&nbsp;You will replace the test **ApplicationId** and **AdUnitId** values with live values before submitting your app for submission.</span></span>

  ``` xml
  <Grid x:Name="ContentPanel" Grid.Row="1">
      <UI:AdControl
          ApplicationId="3f83fe91-d6be-434d-a0ae-7351c5a997f1"
          AdUnitId="10865270"
          HorizontalAlignment="Left"
          Height="80"
          VerticalAlignment="Top"
          Width="480"/>
  </Grid>
  ```

7.  <span data-ttu-id="e128c-148">Erstellen und Ausführen des Projekts</span><span class="sxs-lookup"><span data-stu-id="e128c-148">Build and run your project.</span></span> <span data-ttu-id="e128c-149">Stellen Sie sicher, dass Ihre App eine Anzeige zeigt, die in etwa wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="e128c-149">Confirm that your app displays an ad, similar to the following:</span></span>

  ![wp81silverlight\-emulatorwithad](images/13-8db1492f-ae1d-439b-9b78-bed8e22fe996.jpg)

## <a name="release-your-app-with-live-ads-using-dev-center"></a><span data-ttu-id="e128c-151">Veröffentlichen der App mit Live-Werbung mithilfe von Dev Center</span><span class="sxs-lookup"><span data-stu-id="e128c-151">Release your app with live ads using Dev Center</span></span>

1.  <span data-ttu-id="e128c-152">Rufen Sie für Ihre App im Dev Center-Dashboard die Seite **Monetarisierung** &gt; **Gewinnbringende Nutzung mit Anzeigen** auf, und [erstellen Sie eine eigenständige Anzeigeneinheit](../publish/monetize-with-ads.md).</span><span class="sxs-lookup"><span data-stu-id="e128c-152">In the Dev Center dashboard, go to the **Monetization** &gt; **Monetize with ads** page for your app, and [create a standalone ad unit](../publish/monetize-with-ads.md).</span></span> <span data-ttu-id="e128c-153">Geben Sie als Einheitentyp **Banner** an.</span><span class="sxs-lookup"><span data-stu-id="e128c-153">For the ad unit type, specify **Banner**.</span></span> <span data-ttu-id="e128c-154">Notieren Sie sich die Anzeigeeinheits-ID und die Anwendungs-ID.</span><span class="sxs-lookup"><span data-stu-id="e128c-154">Make note of both the ad unit ID and the application ID.</span></span>

2.  <span data-ttu-id="e128c-155">Ersetzen Sie in Ihrem Code die Testwerte der Anzeigenheit (**applicationId** und **adUnitId**) mit den Live-Werten, die Sie in Dev Center generiert haben.</span><span class="sxs-lookup"><span data-stu-id="e128c-155">In your code, replace the test ad unit values (**applicationId** and **adUnitId**) with the live values you generated in Dev Center.</span></span>

3.  <span data-ttu-id="e128c-156">[Übermitteln Sie Ihre App](../publish/app-submissions.md) mithilfe des Dev Center-Dashboards an den Store.</span><span class="sxs-lookup"><span data-stu-id="e128c-156">[Submit your app](../publish/app-submissions.md) to the Store using the Dev Center dashboard.</span></span>

4.  <span data-ttu-id="e128c-157">Überprüfen Sie die [Anzeigenvermittlungsberichte](../publish/advertising-performance-report.md) auf dem Dev Center-Dashboard.</span><span class="sxs-lookup"><span data-stu-id="e128c-157">Review your [advertising performance reports](../publish/advertising-performance-report.md) in the Dev Center dashboard.</span></span>


 
