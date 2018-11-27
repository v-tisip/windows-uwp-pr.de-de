---
ms.assetid: 141900dd-f1d3-4432-ac8b-b98eaa0b0da2
description: Hier finden Sie Lösungen für allgemeine Entwicklungsprobleme mit den Microsoft Advertising-Bibliotheken in XAML-Apps.
title: XAML- und C#-Handbuch zur Problembehandlung
ms.date: 08/23/2017
ms.topic: article
keywords: Windows10, UWP, Werbung, Advertising, AdControl, Problembehandlung, XAML, c#
ms.localizationpriority: medium
ms.openlocfilehash: 4d92795ac7de2ab09fd0b3b86e05aa33669c54dd
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7707987"
---
# <a name="xaml-and-c-troubleshooting-guide"></a><span data-ttu-id="06d6a-104">XAML- und C#-Handbuch zur Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="06d6a-104">XAML and C# troubleshooting guide</span></span>

<span data-ttu-id="06d6a-105">Dieses Thema enthält Lösungen für allgemeine Entwicklungsprobleme mit den Microsoft Advertising-Bibliotheken in XAML-Apps.</span><span class="sxs-lookup"><span data-stu-id="06d6a-105">This topic contains solutions to common development issues with the Microsoft advertising libraries in XAML apps.</span></span>

* [<span data-ttu-id="06d6a-106">XAML</span><span class="sxs-lookup"><span data-stu-id="06d6a-106">XAML</span></span>](#xaml)
  * [<span data-ttu-id="06d6a-107">AdControl wird nicht angezeigt</span><span class="sxs-lookup"><span data-stu-id="06d6a-107">AdControl not appearing</span></span>](#xaml-notappearing)
  * [<span data-ttu-id="06d6a-108">Blackbox blinkt und wird ausgeblendet</span><span class="sxs-lookup"><span data-stu-id="06d6a-108">Black box blinks and disappears</span></span>](#xaml-blackboxblinksdisappears)
  * [<span data-ttu-id="06d6a-109">Anzeigen werden nicht aktualisiert</span><span class="sxs-lookup"><span data-stu-id="06d6a-109">Ads not refreshing</span></span>](#xaml-adsnotrefreshing)

* [<span data-ttu-id="06d6a-110">C#</span><span class="sxs-lookup"><span data-stu-id="06d6a-110">C#</span></span>](#csharp)
  * [<span data-ttu-id="06d6a-111">AdControl wird nicht angezeigt</span><span class="sxs-lookup"><span data-stu-id="06d6a-111">AdControl not appearing</span></span>](#csharp-adcontrolnotappearing)
  * [<span data-ttu-id="06d6a-112">Blackbox blinkt und wird ausgeblendet</span><span class="sxs-lookup"><span data-stu-id="06d6a-112">Black box blinks and disappears</span></span>](#csharp-blackboxblinksdisappears)
  * [<span data-ttu-id="06d6a-113">Anzeigen werden nicht aktualisiert</span><span class="sxs-lookup"><span data-stu-id="06d6a-113">Ads not refreshing</span></span>](#csharp-adsnotrefreshing)

<span id="xaml"/>

## <a name="xaml"></a><span data-ttu-id="06d6a-114">XAML</span><span class="sxs-lookup"><span data-stu-id="06d6a-114">XAML</span></span>

<span id="xaml-notappearing"/>

### <a name="adcontrol-not-appearing"></a><span data-ttu-id="06d6a-115">AdControl wird nicht angezeigt</span><span class="sxs-lookup"><span data-stu-id="06d6a-115">AdControl not appearing</span></span>

1.  <span data-ttu-id="06d6a-116">Stellen Sie sicher, dass die **Internet (Client)**-Funktion in „Package.appxmanifest“ ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="06d6a-116">Ensure that the **Internet (Client)** capability is selected in Package.appxmanifest.</span></span>

2.  <span data-ttu-id="06d6a-117">Überprüfen Sie die ID der Anwendung und der Anzeigeneinheit.</span><span class="sxs-lookup"><span data-stu-id="06d6a-117">Check the application ID and ad unit ID.</span></span> <span data-ttu-id="06d6a-118">Diese IDs müssen übereinstimmen, die Anwendungs-ID und anzeigeneinheits-ID, die Sie in Partner Center erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="06d6a-118">These IDs must match the application ID and ad unit ID that you obtained in Partner Center.</span></span> <span data-ttu-id="06d6a-119">Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in Ihrer App](set-up-ad-units-in-your-app.md#live-ad-units).</span><span class="sxs-lookup"><span data-stu-id="06d6a-119">For more information, see [Set up ad units in your app](set-up-ad-units-in-your-app.md#live-ad-units).</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` xml
    <UI:AdControl AdUnitId="{AdUnitID}" ApplicationId="{ApplicationID}"
                  Width="728" Height="90" />
    ```

3.  <span data-ttu-id="06d6a-120">Überprüfen Sie die **Height**-Eigenschaft und **Width**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="06d6a-120">Check the **Height** and **Width** properties.</span></span> <span data-ttu-id="06d6a-121">Diese müssen auf eine der [unterstützten Anzeigengrößen für Werbebanner](supported-ad-sizes-for-banner-ads.md) festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-121">These must be set to one of the [Supported ad sizes for banner ads](supported-ad-sizes-for-banner-ads.md).</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` xml
    <UI:AdControl AdUnitId="{AdUnitID}"
                  ApplicationId="{ApplicationID}"
                  Width="728" Height="90" />
    ```

4.  <span data-ttu-id="06d6a-122">Überprüfen Sie die Elementposition.</span><span class="sxs-lookup"><span data-stu-id="06d6a-122">Check the element position.</span></span> <span data-ttu-id="06d6a-123">[AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) muss sich im sichtbaren Bereich befinden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-123">The [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) must be inside the viewable area.</span></span>

5.  <span data-ttu-id="06d6a-124">Überprüfen Sie die **Visibility**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="06d6a-124">Check the **Visibility** property.</span></span> <span data-ttu-id="06d6a-125">Die optionale **Visibility**-Eigenschaft darf nicht auf „collapsed“ oder „hidden“ festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-125">The optional **Visibility** property must not be set to collapsed or hidden.</span></span> <span data-ttu-id="06d6a-126">Diese Eigenschaft kann als Inlineeigenschaft (wie unten dargestellt) oder in einem externen Stylesheet festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-126">This property can be set inline (as shown below) or in an external style sheet.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` xml
    <UI:AdControl AdUnitId="{AdUnitID}"
                  ApplicationId="{ApplicationID}"
                  Visibility="Visible"
                  Width="728" Height="90" />
    ```

6.  <span data-ttu-id="06d6a-127">Überprüfen Sie das übergeordnete Element von **AdControl**.</span><span class="sxs-lookup"><span data-stu-id="06d6a-127">Check the parent of the **AdControl**.</span></span> <span data-ttu-id="06d6a-128">Wenn sich das **AdControl**-Element in einem übergeordneten Element befindet, muss das übergeordnete Element aktiv und sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="06d6a-128">If the **AdControl** element resides in a parent element, the parent must be active and visible.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` xml
    <StackPanel>
        <UI:AdControl AdUnitId="{AdUnitID}"
                      ApplicationId="{ApplicationID}"
                      Width="728" Height="90" />
    </StackPanel>
    ```

7.  <span data-ttu-id="06d6a-129">Stellen Sie sicher, dass **AdControl** im Viewport nicht ausgeblendet ist.</span><span class="sxs-lookup"><span data-stu-id="06d6a-129">Ensure the **AdControl** is not hidden from the viewport.</span></span> <span data-ttu-id="06d6a-130">**AdControl** muss sichtbar sein, damit Anzeigen ordnungsgemäß dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-130">The **AdControl** must be visible for ads to display properly.</span></span>

8.  <span data-ttu-id="06d6a-131">Echte Werte für **ApplicationId** und **AdUnitId** sollten nicht im Emulator getestet werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-131">Live values for **ApplicationId** and **AdUnitId** should not be tested in the emulator.</span></span> <span data-ttu-id="06d6a-132">Um sicherzustellen, dass **AdControl** erwartungsgemäß funktioniert, verwenden Sie [test values](set-up-ad-units-in-your-app.md#test-ad-units) sowohl für **ApplicationId** und **AdUnitId**.</span><span class="sxs-lookup"><span data-stu-id="06d6a-132">To ensure the **AdControl** is functioning as expected, use the [test values](set-up-ad-units-in-your-app.md#test-ad-units) for both **ApplicationId** and **AdUnitId**.</span></span>

<span id="xaml-blackboxblinksdisappears"/>

### <a name="black-box-blinks-and-disappears"></a><span data-ttu-id="06d6a-133">Blackbox blinkt und wird ausgeblendet</span><span class="sxs-lookup"><span data-stu-id="06d6a-133">Black box blinks and disappears</span></span>

1.  <span data-ttu-id="06d6a-134">Überprüfen Sie noch einmal alle Schritte im vorherigen Abschnitt [AdControl wird nicht angezeigt](#xaml-notappearing).</span><span class="sxs-lookup"><span data-stu-id="06d6a-134">Double-check all steps in the previous [AdControl not appearing](#xaml-notappearing) section.</span></span>

2.  <span data-ttu-id="06d6a-135">Behandeln Sie das **ErrorOccurred**-Ereignis, und bestimmen Sie anhand der an den Ereignishandler übergebenen Meldung, ob ein Fehler aufgetreten ist und welche Art von Fehler ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="06d6a-135">Handle the **ErrorOccurred** event, and use the message that is passed to the event handler to determine whether an error occurred and what type of error was thrown.</span></span> <span data-ttu-id="06d6a-136">Weitere Informationen finden Sie unter [Fehlerbehandlung in XAML/Exemplarische Vorgehensweise für C#](error-handling-in-xamlc-walkthrough.md).</span><span class="sxs-lookup"><span data-stu-id="06d6a-136">See [Error handling in XAML/C# walkthrough](error-handling-in-xamlc-walkthrough.md) for more information.</span></span>

    <span data-ttu-id="06d6a-137">Dieses Beispiel veranschaulicht einen **ErrorOccurred**-Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="06d6a-137">This example demonstrates an **ErrorOccurred** event handler.</span></span> <span data-ttu-id="06d6a-138">Der erste Ausschnitt ist das XAML-UI-Markup.</span><span class="sxs-lookup"><span data-stu-id="06d6a-138">The first snippet is the XAML UI markup.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` xml
    <UI:AdControl AdUnitId="{AdUnitID}"
                  ApplicationId="{ApplicationID}"
                  Width="728" Height="90"
                  ErrorOccurred="adControl_ErrorOccurred" />
    <TextBlock x:Name="TextBlock1" TextWrapping="Wrap" Width="500" Height="250" />
    ```

    <span data-ttu-id="06d6a-139">Dieses Beispiel veranschaulicht den entsprechenden C#-Code.</span><span class="sxs-lookup"><span data-stu-id="06d6a-139">This example demonstrates the corresponding C# code.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` cs
    private void adControl_ErrorOccurred(object sender,               
        Microsoft.Advertising.WinRT.UI.AdErrorEventArgs e)
    {
        TextBlock1.Text = e.ErrorMessage;
    }
    ```

    <span data-ttu-id="06d6a-140">Eine Blackbox wird am häufigsten dadurch verursacht, dass keine Anzeige verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="06d6a-140">The most common error that causes a black box is “No ad available.”</span></span> <span data-ttu-id="06d6a-141">Dieser Fehler bedeutet, dass durch die Anforderung keine Anzeige zurückgegeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="06d6a-141">This error means there is no ad available to return from the request.</span></span>

3.  <span data-ttu-id="06d6a-142">[AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) verhält sich normal.</span><span class="sxs-lookup"><span data-stu-id="06d6a-142">The [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) is behaving normally.</span></span>

    <span data-ttu-id="06d6a-143">**AdControl** wird standardmäßig reduziert, wenn keine Anzeige dargestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="06d6a-143">By default, the **AdControl** will collapse when it cannot display an ad.</span></span> <span data-ttu-id="06d6a-144">Wenn andere Elemente demselben übergeordneten Element untergeordnet sind, können sie verschoben werden, um den freien Platz des reduzierten **AdControl**-Elements zu füllen, und bei der nächsten Anforderung erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-144">If other elements are children of the same parent they may move to fill the gap of the collapsed **AdControl** and expand when the next request is made.</span></span>

<span id="xaml-adsnotrefreshing"/>

### <a name="ads-not-refreshing"></a><span data-ttu-id="06d6a-145">Anzeigen werden nicht aktualisiert</span><span class="sxs-lookup"><span data-stu-id="06d6a-145">Ads not refreshing</span></span>

1.  <span data-ttu-id="06d6a-146">Überprüfen Sie die [IsAutoRefreshEnabled](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.isautorefreshenabled)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="06d6a-146">Check the [IsAutoRefreshEnabled](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.isautorefreshenabled) property.</span></span> <span data-ttu-id="06d6a-147">Diese optionale Eigenschaft ist standardmäßig auf **True** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="06d6a-147">By default, this optional property is set to **True**.</span></span> <span data-ttu-id="06d6a-148">Beim Wert **False** muss die [Refresh](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.refresh)-Methode verwendet werden, um eine weitere Anzeige abzurufen.</span><span class="sxs-lookup"><span data-stu-id="06d6a-148">When set to **False**, the [Refresh](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.refresh) method must be used to retrieve another ad.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` xml
    <UI:AdControl AdUnitId="{AdUnitID}"
                  ApplicationId="{ApplicationID}"
                  Width="728" Height="90"
                  IsAutoRefreshEnabled="True" />
    ```

2.  <span data-ttu-id="06d6a-149">Überprüfen Sie Aufrufe der **Refresh**-Methode.</span><span class="sxs-lookup"><span data-stu-id="06d6a-149">Check calls to the **Refresh** method.</span></span> <span data-ttu-id="06d6a-150">Bei Verwendung der automatischen Aktualisierung kann **Refresh** nicht verwendet werden, um eine weitere Anzeige abzurufen.</span><span class="sxs-lookup"><span data-stu-id="06d6a-150">When using automatic refresh, **Refresh** cannot be used to retrieve another ad.</span></span> <span data-ttu-id="06d6a-151">Bei Verwendung der manuellen Aktualisierung sollte **Refresh** abhängig von der aktuellen Datenverbindung des Geräts erst nach mindestens 30 bis 60 Sekunden aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-151">When using manual refresh, **Refresh** should be called only after a minimum of 30 to 60 seconds depending on the device’s current data connection.</span></span>

    <span data-ttu-id="06d6a-152">In den folgenden Codeausschnitten wird die Verwendung der **Refresh**-Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="06d6a-152">The following code snippets show an example of how to use the **Refresh** method.</span></span> <span data-ttu-id="06d6a-153">Der erste Ausschnitt ist das XAML-UI-Markup.</span><span class="sxs-lookup"><span data-stu-id="06d6a-153">The first snippet is the XAML UI markup.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` xml
    <UI:AdControl x:Name="adControl1"
                  AdUnitId="{AdUnit_ID}"
                  ApplicationId="{ApplicationID}"
                  Width="728" Height="90"
                  IsAutoRefreshEnabled="False" />
    ```

    <span data-ttu-id="06d6a-154">Dieser Codeausschnitt zeigt ein Beispiel für den C#-CodeBehind-Code des UI-Markups.</span><span class="sxs-lookup"><span data-stu-id="06d6a-154">This code snippet shows an example of the C# code behind the UI markup.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` cs
    public RefreshAds()
    {
        var timer = new DispatcherTimer() { Interval = TimeSpan.FromSeconds(60) };
        timer.Tick += (s, e) => adControl1.Refresh();
        timer.Start();
    }
    ```

3.  <span data-ttu-id="06d6a-155">**AdControl** verhält sich normal.</span><span class="sxs-lookup"><span data-stu-id="06d6a-155">The **AdControl** is behaving normally.</span></span> <span data-ttu-id="06d6a-156">In einigen Fällen wird dieselbe Anzeige mehrmals in Folge angezeigt, wodurch der Eindruck entsteht, dass Anzeigen nicht aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-156">Sometimes the same ad will appear more than once in a row giving the appearance that ads are not refreshing.</span></span>

<span id="csharp"/>

## <a name="c"></a><span data-ttu-id="06d6a-157">C\#</span><span class="sxs-lookup"><span data-stu-id="06d6a-157">C\#</span></span> #

<span id="csharp-adcontrolnotappearing"/>

### <a name="adcontrol-not-appearing"></a><span data-ttu-id="06d6a-158">AdControl wird nicht angezeigt</span><span class="sxs-lookup"><span data-stu-id="06d6a-158">AdControl not appearing</span></span>

1.  <span data-ttu-id="06d6a-159">Stellen Sie sicher, dass die **Internet (Client)**-Funktion in „Package.appxmanifest“ ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="06d6a-159">Ensure that the **Internet (Client)** capability is selected in Package.appxmanifest.</span></span>

2.  <span data-ttu-id="06d6a-160">Stellen Sie sicher, dass **AdControl** instanziiert ist.</span><span class="sxs-lookup"><span data-stu-id="06d6a-160">Ensure the **AdControl** is instantiated.</span></span> <span data-ttu-id="06d6a-161">Wenn **AdControl** nicht instanziiert wird, ist es nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="06d6a-161">If the **AdControl** is not instantiated it will not be available.</span></span>

    > [!div class="tabbedCodeSnippets"]
    [!code-cs[AdControl](./code/AdvertisingSamples/AdControlSamples/cs/MiscellaneousSnippets.cs#Snippet1)]

3.  <span data-ttu-id="06d6a-162">Überprüfen Sie die ID der Anwendung und der Anzeigeneinheit.</span><span class="sxs-lookup"><span data-stu-id="06d6a-162">Check the application ID and ad unit ID.</span></span> <span data-ttu-id="06d6a-163">Diese IDs müssen übereinstimmen, die Anwendungs-ID und anzeigeneinheits-ID, die Sie in Partner Center erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="06d6a-163">These IDs must match the application ID and ad unit ID that you obtained in Partner Center.</span></span> <span data-ttu-id="06d6a-164">Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in Ihrer App](set-up-ad-units-in-your-app.md#live-ad-units).</span><span class="sxs-lookup"><span data-stu-id="06d6a-164">For more information, see [Set up ad units in your app](set-up-ad-units-in-your-app.md#live-ad-units).</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` cs
    adControl = new AdControl();
    adControl.ApplicationId = "{ApplicationID}";adControl.AdUnitId = "{AdUnitID}";
    adControl.Height = 90;
    adControl.Width = 728;
    ```

4.  <span data-ttu-id="06d6a-165">Überprüfen Sie den **Height**-Parameter und **Width**-Parameter.</span><span class="sxs-lookup"><span data-stu-id="06d6a-165">Check the **Height** and **Width** parameters.</span></span> <span data-ttu-id="06d6a-166">Diese müssen auf eine der [unterstützten Anzeigengrößen für Werbebanner](supported-ad-sizes-for-banner-ads.md) festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-166">These must be set to one of the [supported ad sizes for banner ads](supported-ad-sizes-for-banner-ads.md).</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` cs
    adControl = new AdControl();
    adControl.ApplicationId = "{ApplicationID}";
    adControl.AdUnitId = "{AdUnitID}";
    adControl.Height = 90;adControl.Width = 728;
    ```

5.  <span data-ttu-id="06d6a-167">Stellen Sie sicher, dass **AdControl** einem übergeordneten Element hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="06d6a-167">Ensure the **AdControl** is added to a parent element.</span></span> <span data-ttu-id="06d6a-168">Damit **AdControl** angezeigt wird, muss es einem übergeordneten Steuerelement (z. B. **StackPanel** oder **Grid**) als untergeordnetes Element hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-168">To display, the **AdControl** must be added as a child to a parent control (for example, a **StackPanel** or **Grid**).</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` cs
    ContentPanel.Children.Add(adControl);
    ```

6.  <span data-ttu-id="06d6a-169">Überprüfen Sie den **Margin**-Parameter.</span><span class="sxs-lookup"><span data-stu-id="06d6a-169">Check the **Margin** parameter.</span></span> <span data-ttu-id="06d6a-170">**AdControl** muss sich im sichtbaren Bereich befinden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-170">The **AdControl** must be inside the viewable area.</span></span>

7.  <span data-ttu-id="06d6a-171">Überprüfen Sie die **Visibility**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="06d6a-171">Check the **Visibility** property.</span></span> <span data-ttu-id="06d6a-172">Die optionale **Visibility**-Eigenschaft muss auf **Visible** festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="06d6a-172">The optional **Visibility** property must be set to **Visible**.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` cs
    adControl = new AdControl();
    adControl.ApplicationId = "{ApplicationID}";
    adControl.AdUnitId = "{AdUnitID}";
    adControl.Height = 90;
    adControl.Width = 728;
    adControl.Visibility = System.Windows.Visibility.Visible;
    ```

8.  <span data-ttu-id="06d6a-173">Überprüfen Sie das übergeordnete Element von **AdControl**.</span><span class="sxs-lookup"><span data-stu-id="06d6a-173">Check the parent of the **AdControl**.</span></span> <span data-ttu-id="06d6a-174">Das übergeordnete Element muss aktiv und sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="06d6a-174">The parent must be active and visible.</span></span>

9. <span data-ttu-id="06d6a-175">Echte Werte für **ApplicationId** und **AdUnitId** sollten nicht im Emulator getestet werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-175">Live values for **ApplicationId** and **AdUnitId** should not be tested in the emulator.</span></span> <span data-ttu-id="06d6a-176">Um sicherzustellen, dass **AdControl** erwartungsgemäß funktioniert, verwenden Sie [test values](set-up-ad-units-in-your-app.md#test-ad-units) sowohl für **ApplicationId** und **AdUnitId**.</span><span class="sxs-lookup"><span data-stu-id="06d6a-176">To ensure the **AdControl** is functioning as expected, use the [test values](set-up-ad-units-in-your-app.md#test-ad-units) for both **ApplicationId** and **AdUnitId**.</span></span>

<span id="csharp-blackboxblinksdisappears"/>

### <a name="black-box-blinks-and-disappears"></a><span data-ttu-id="06d6a-177">Blackbox blinkt und wird ausgeblendet</span><span class="sxs-lookup"><span data-stu-id="06d6a-177">Black box blinks and disappears</span></span>

1.  <span data-ttu-id="06d6a-178">Überprüfen Sie noch einmal alle Schritte im Abschnitt oben [AdControl wird nicht angezeigt](#csharp-adcontrolnotappearing).</span><span class="sxs-lookup"><span data-stu-id="06d6a-178">Double-check all steps in the [AdControl not appearing](#csharp-adcontrolnotappearing) section above.</span></span>

2.  <span data-ttu-id="06d6a-179">Behandeln Sie das **ErrorOccurred**-Ereignis, und bestimmen Sie anhand der an den Ereignishandler übergebenen Meldung, ob ein Fehler aufgetreten ist und welche Art von Fehler ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="06d6a-179">Handle the **ErrorOccurred** event, and use the message that is passed to the event handler to determine whether an error occurred and what type of error was thrown.</span></span> <span data-ttu-id="06d6a-180">Weitere Informationen finden Sie unter [Fehlerbehandlung in XAML/Exemplarische Vorgehensweise für C#](error-handling-in-xamlc-walkthrough.md).</span><span class="sxs-lookup"><span data-stu-id="06d6a-180">See [Error handling in XAML/C# walkthrough](error-handling-in-xamlc-walkthrough.md) for more information.</span></span>

    <span data-ttu-id="06d6a-181">Die folgenden Beispiele veranschaulichen den grundlegenden Code zum Implementieren eines Fehleraufrufs.</span><span class="sxs-lookup"><span data-stu-id="06d6a-181">The following examples show the basic code needed to implement an error call.</span></span> <span data-ttu-id="06d6a-182">Durch diesen XAML-Code wird ein **TextBlock**-Element definiert, mit dem die Fehlermeldung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="06d6a-182">This XAML code defines a **TextBlock** that is used to display the error message.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` xml
    <TextBlock x:Name="TextBlock1" TextWrapping="Wrap" Width="500" Height="250" />
    ```

    <span data-ttu-id="06d6a-183">Durch diesen C#-Code wird die Fehlermeldung abgerufen und in **TextBlock** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="06d6a-183">This C# code retrieves the error message and displays it in the **TextBlock**.</span></span>

    > [!div class="tabbedCodeSnippets"]
    [!code-cs[AdControl](./code/AdvertisingSamples/AdControlSamples/cs/MiscellaneousSnippets.cs#Snippet2)]

    <span data-ttu-id="06d6a-184">Eine Blackbox wird am häufigsten dadurch verursacht, dass keine Anzeige verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="06d6a-184">The most common error that causes a black box is “No ad available.”</span></span> <span data-ttu-id="06d6a-185">Dieser Fehler bedeutet, dass durch die Anforderung keine Anzeige zurückgegeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="06d6a-185">This error means there is no ad available to return from the request.</span></span>

3.  <span data-ttu-id="06d6a-186">**AdControl** verhält sich normal.</span><span class="sxs-lookup"><span data-stu-id="06d6a-186">**AdControl** is behaving normally.</span></span> <span data-ttu-id="06d6a-187">In einigen Fällen wird dieselbe Anzeige mehrmals in Folge angezeigt, wodurch der Eindruck entsteht, dass Anzeigen nicht aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-187">Sometimes the same ad will appear more than once in a row giving the appearance that ads are not refreshing.</span></span>

<span id="csharp-adsnotrefreshing"/>

### <a name="ads-not-refreshing"></a><span data-ttu-id="06d6a-188">Anzeigen werden nicht aktualisiert</span><span class="sxs-lookup"><span data-stu-id="06d6a-188">Ads not refreshing</span></span>

1.  <span data-ttu-id="06d6a-189">Überprüfen Sie, ob in der [IsAutoRefreshEnabled](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.isautorefreshenabled.aspx)-Eigenschaft **AdControl** auf „false“ festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="06d6a-189">Check whether the [IsAutoRefreshEnabled](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.isautorefreshenabled.aspx) property of your **AdControl** is set to false.</span></span> <span data-ttu-id="06d6a-190">Diese optionale Eigenschaft ist standardmäßig auf **true** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="06d6a-190">By default, this optional property is set to **true**.</span></span> <span data-ttu-id="06d6a-191">Wenn sie auf **false** festgelegt ist, muss die Methode **Refresh** verwendet werden, um eine weitere Anzeige abzurufen.</span><span class="sxs-lookup"><span data-stu-id="06d6a-191">When set to **false**, the **Refresh** method must be used to retrieve another ad.</span></span>

2.  <span data-ttu-id="06d6a-192">Überprüfen Sie Aufrufe der [Refresh](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.refresh.aspx)-Methode.</span><span class="sxs-lookup"><span data-stu-id="06d6a-192">Check calls to the [Refresh](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.refresh.aspx) method.</span></span> <span data-ttu-id="06d6a-193">Bei Verwendung der automatischen Aktualisierung ((**IsAutoRefreshEnabled** ist **true**)) kann **Refresh** nicht verwendet werden, um eine weitere Anzeige abzurufen.</span><span class="sxs-lookup"><span data-stu-id="06d6a-193">When using automatic refresh (**IsAutoRefreshEnabled** is **true**), **Refresh** cannot be used to retrieve another ad.</span></span> <span data-ttu-id="06d6a-194">Bei Verwendung der manuellen Aktualisierung (**IsAutoRefreshEnabled** ist **false**) sollte **Refresh** abhängig von der aktuellen Datenverbindung des Geräts erst nach mindestens 30 bis 60 Sekunden aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-194">When using manual refresh (**IsAutoRefreshEnabled** is **false**), **Refresh** should be called only after a minimum of 30 to 60 seconds depending on the device’s current data connection.</span></span>

    <span data-ttu-id="06d6a-195">Das folgende Beispiel veranschaulicht, wie die **Refresh**-Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="06d6a-195">The following example demonstrates how to call the **Refresh** method.</span></span>

    > [!div class="tabbedCodeSnippets"]
    [!code-cs[AdControl](./code/AdvertisingSamples/AdControlSamples/cs/MiscellaneousSnippets.cs#Snippet3)]

3.  <span data-ttu-id="06d6a-196">**AdControl** verhält sich normal.</span><span class="sxs-lookup"><span data-stu-id="06d6a-196">The **AdControl** is behaving normally.</span></span> <span data-ttu-id="06d6a-197">In einigen Fällen wird dieselbe Anzeige mehrmals in Folge angezeigt, wodurch der Eindruck entsteht, dass Anzeigen nicht aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="06d6a-197">Sometimes the same ad will appear more than once in a row giving the appearance that ads are not refreshing.</span></span>

 

 
