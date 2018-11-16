---
author: Xansky
ms.assetid: 7a61c328-77be-4614-b117-a32a592c9efe
description: Erfahren Sie mehr über Lösungen für allgemeine Entwicklungsprobleme mit den Microsoft Advertising-Bibliotheken in JavaScript/HTML-Apps.
title: Anleitung zur Problembehandlung für HTML und JavaScript
ms.author: mhopkins
ms.date: 08/23/2017
ms.topic: article
keywords: Windows10, UWP, Anzeigen, Werbung, AdControl, Problembehandlung, HTML, Javascript
ms.localizationpriority: medium
ms.openlocfilehash: 38f0b36769d13d119965e7d15c5812b9ba1d6ecd
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "6996237"
---
# <a name="html-and-javascript-troubleshooting-guide"></a><span data-ttu-id="83671-104">Anleitung zur Problembehandlung für HTML und JavaScript</span><span class="sxs-lookup"><span data-stu-id="83671-104">HTML and JavaScript troubleshooting guide</span></span>

<span data-ttu-id="83671-105">Dieses Thema enthält Lösungen für allgemeine Entwicklungsprobleme mit den Microsoft Advertising-Bibliotheken in JavaScript/HTML-Apps.</span><span class="sxs-lookup"><span data-stu-id="83671-105">This topic contains solutions to common development issues with the Microsoft advertising libraries in JavaScript/HTML apps.</span></span>

* [<span data-ttu-id="83671-106">HTML</span><span class="sxs-lookup"><span data-stu-id="83671-106">HTML</span></span>](#html)
  * [<span data-ttu-id="83671-107">AdControl wird nicht angezeigt</span><span class="sxs-lookup"><span data-stu-id="83671-107">AdControl not appearing</span></span>](#html-notappearing)
  * [<span data-ttu-id="83671-108">Blackbox blinkt und wird ausgeblendet</span><span class="sxs-lookup"><span data-stu-id="83671-108">Black box blinks and disappears</span></span>](#html-blackboxblinksdisappears)
  * [<span data-ttu-id="83671-109">Anzeigen werden nicht aktualisiert</span><span class="sxs-lookup"><span data-stu-id="83671-109">Ads not refreshing</span></span>](#html-adsnotrefreshing)

* [<span data-ttu-id="83671-110">JavaScript</span><span class="sxs-lookup"><span data-stu-id="83671-110">JavaScript</span></span>](#js)
  * [<span data-ttu-id="83671-111">AdControl wird nicht angezeigt</span><span class="sxs-lookup"><span data-stu-id="83671-111">AdControl not appearing</span></span>](#js-adcontrolnotappearing)
  * [<span data-ttu-id="83671-112">Blackbox blinkt und wird ausgeblendet</span><span class="sxs-lookup"><span data-stu-id="83671-112">Black box blinks and disappears</span></span>](#js-blackboxblinksdisappears)
  * [<span data-ttu-id="83671-113">Anzeigen werden nicht aktualisiert</span><span class="sxs-lookup"><span data-stu-id="83671-113">Ads not refreshing</span></span>](#js-adsnotrefreshing)

## <a name="html"></a><span data-ttu-id="83671-114">HTML</span><span class="sxs-lookup"><span data-stu-id="83671-114">HTML</span></span>

<span id="html-notappearing"/>

### <a name="adcontrol-not-appearing"></a><span data-ttu-id="83671-115">AdControl wird nicht angezeigt</span><span class="sxs-lookup"><span data-stu-id="83671-115">AdControl not appearing</span></span>

1.  <span data-ttu-id="83671-116">Stellen Sie sicher, dass die **Internet (Client)**-Funktion in „Package.appxmanifest“ ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="83671-116">Ensure that the **Internet (Client)** capability is selected in Package.appxmanifest.</span></span>

2.  <span data-ttu-id="83671-117">Stellen Sie sicher, dass der JavaScript-Verweis vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="83671-117">Ensure the JavaScript reference is present.</span></span> <span data-ttu-id="83671-118">Ohne den Verweis ad.js im Abschnitt &lt;head&gt; (nach dem Verweis default.js) kann **AdControl** nicht angezeigt werden, und während der Erstellung tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="83671-118">Without the ad.js reference in the &lt;head&gt; section (after the default.js reference) the **AdControl** will be unable to display and an error will occur during build.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <head>
        ...
        <script src="//Microsoft.Advertising.JavaScript/ad.js"></script>
        ...
    </head>
    ```

3.  <span data-ttu-id="83671-119">Überprüfen Sie die ID der Anwendung und der Anzeigeneinheit.</span><span class="sxs-lookup"><span data-stu-id="83671-119">Check the application ID and ad unit ID.</span></span> <span data-ttu-id="83671-120">Diese IDs müssen übereinstimmen, die Anwendungs-ID und anzeigeneinheits-ID, die Sie in Partner Center erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="83671-120">These IDs must match the application ID and ad unit ID that you obtained in Partner Center.</span></span> <span data-ttu-id="83671-121">Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in der App](set-up-ad-units-in-your-app.md#live-ad-units).</span><span class="sxs-lookup"><span data-stu-id="83671-121">For more information, see [Set up ad units in your app](set-up-ad-units-in-your-app.md#live-ad-units).</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div id="myAd" style="position: absolute; top: 50px; left: 0px;
                          width: 250px; height: 250px; z-index: 1"
         data-win-control="MicrosoftNSJS.Advertising.AdControl"
         data-win-options="{applicationId: 'ApplicationID',
                            adUnitId: 'AdUnitID'}">
    </div>
    ```

4.  <span data-ttu-id="83671-122">Überprüfen Sie die Eigenschaften **height** und **width**.</span><span class="sxs-lookup"><span data-stu-id="83671-122">Check the **height** and **width** properties.</span></span> <span data-ttu-id="83671-123">Diese müssen auf eine der [unterstützten Anzeigengrößen für Werbebanner](supported-ad-sizes-for-banner-ads.md) festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="83671-123">These must be set to one of the [supported ad sizes for banner ads](supported-ad-sizes-for-banner-ads.md).</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div id="myAd" style="position: absolute; top: 50px; left: 0px;
                          width: 250px; height: 250px; z-index: 1"
         data-win-control="MicrosoftNSJS.Advertising.AdControl"
         data-win-options="{applicationId: 'ApplicationID',
                            adUnitId: 'AdUnitID'}">
    </div>
    ```

5.  <span data-ttu-id="83671-124">Überprüfen Sie die Elementpositionierung.</span><span class="sxs-lookup"><span data-stu-id="83671-124">Check the element positioning.</span></span> <span data-ttu-id="83671-125">[AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) muss sich im sichtbaren Bereich befinden.</span><span class="sxs-lookup"><span data-stu-id="83671-125">The [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) must be inside the viewable area.</span></span>

6.  <span data-ttu-id="83671-126">Überprüfen Sie die Eigenschaft **visibility**.</span><span class="sxs-lookup"><span data-stu-id="83671-126">Check the **visibility** property.</span></span> <span data-ttu-id="83671-127">Diese Eigenschaft darf nicht auf reduziert oder ausgeblendet festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="83671-127">This property must not be set to collapsed or hidden.</span></span> <span data-ttu-id="83671-128">Diese Eigenschaft kann als Inlineeigenschaft (wie unten dargestellt) oder in einem externen Stylesheet festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="83671-128">This property can be set inline (as shown below) or in an external style sheet.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div id="myAd" style="visibility: visible; position: absolute; top: 1025px;
                          left: 500px; width: 250px; height: 250px; z-index: 1"
         data-win-control="MicrosoftNSJS.Advertising.AdControl"
         data-win-options="{applicationId: 'ApplicationID',
                            adUnitId: 'AdUnitID'}">
    </div>
    ```

7.  <span data-ttu-id="83671-129">Überprüfen Sie die Eigenschaft **position**.</span><span class="sxs-lookup"><span data-stu-id="83671-129">Check the **position** property.</span></span> <span data-ttu-id="83671-130">Die Eigenschaft „position“ muss auf einen geeigneten Wert abhängig von den anderen Eigenschaften des Elements festgelegt werden (beispielsweise Rändern im übergeordneten Element und z-index).</span><span class="sxs-lookup"><span data-stu-id="83671-130">The position property must be set to an appropriate value depending on the element’s other properties (for example, margins in parent element and z-index).</span></span> <span data-ttu-id="83671-131">Diese Eigenschaft kann als Inlineeigenschaft (wie unten dargestellt) oder in einem externen Stylesheet festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="83671-131">This property can be set inline (as shown below) or in an external style sheet.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div id="myAd" style="visibility: visible; position: absolute; top: 1025px;
                          left: 500px; width: 250px; height: 250px; z-index: 1"
         data-win-control="MicrosoftNSJS.Advertising.AdControl"
         data-win-options="{applicationId: 'ApplicationID',
                            adUnitId: 'AdUnitID'}">
    </div>
    ```

8.  <span data-ttu-id="83671-132">Überprüfen Sie die Eigenschaft **z-index**.</span><span class="sxs-lookup"><span data-stu-id="83671-132">Check the **z-index** property.</span></span> <span data-ttu-id="83671-133">Die Eigenschaft **z-index** muss hoch genug festgelegt werden, sodass **AdControl** stets oberhalb anderer Elemente angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="83671-133">The **z-index** property must be set high enough so the **AdControl** always appears on top of other elements.</span></span> <span data-ttu-id="83671-134">Diese Eigenschaft kann als Inlineeigenschaft (wie unten dargestellt) oder in einem externen Stylesheet festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="83671-134">This property can be set inline (as shown below) or in an external style sheet.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div id="myAd" style="visibility: visible; position: absolute; top: 1025px;
                          left: 500px; width: 250px; height: 250px; z-index: 1"
         data-win-control="MicrosoftNSJS.Advertising.AdControl"
         data-win-options="{applicationId: 'ApplicationID',
                            adUnitId: 'AdUnitID'}">
    </div>
    ```

9.  <span data-ttu-id="83671-135">Überprüfen Sie die externen Stylesheets.</span><span class="sxs-lookup"><span data-stu-id="83671-135">Check external style sheets.</span></span> <span data-ttu-id="83671-136">Wenn im Element **AdControl** Eigenschaften über ein externes Stylesheet festgelegt werden, müssen alle oben genannten Eigenschaften ordnungsgemäß festgelegt worden sein.</span><span class="sxs-lookup"><span data-stu-id="83671-136">If properties are set on the **AdControl** element through an external style sheet, ensure all of the above properties are correctly set.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div id="myAd" style="visibility: visible; position: absolute; top: 1025px;
                          left: 500px; width: 250px; height: 250px; z-index: 1"
         data-win-control="MicrosoftNSJS.Advertising.AdControl"
         data-win-options="{applicationId: 'ApplicationID',
                            adUnitId: 'AdUnitID'}">
    </div>
    ```

10. <span data-ttu-id="83671-137">Überprüfen Sie das übergeordnete Element von **AdControl**.</span><span class="sxs-lookup"><span data-stu-id="83671-137">Check the parent of the **AdControl**.</span></span> <span data-ttu-id="83671-138">Wenn sich **AdControl** in einem übergeordneten Element befindet, muss das übergeordnete Element aktiv und sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="83671-138">If the **AdControl** resides in a parent element, the parent must be active and visible.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div style="position: absolute; width: 500px; height: 500px;">
        <div id="myAd" style="position: relative; top: 0px; left: 100px;
                              width: 250px; height: 250px; z-index: 1"
             data-win-control="MicrosoftNSJS.Advertising.AdControl"
             data-win-options="{applicationId: 'ApplicationID',
                                adUnitId: 'AdUnitID'}">
        </div>
    </div>
    ```

11. <span data-ttu-id="83671-139">Stellen Sie sicher, dass **AdControl** im Viewport nicht ausgeblendet ist.</span><span class="sxs-lookup"><span data-stu-id="83671-139">Ensure the **AdControl** is not hidden from the viewport.</span></span> <span data-ttu-id="83671-140">**AdControl** muss sichtbar sein, damit Anzeigen ordnungsgemäß dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="83671-140">The **AdControl** must be visible for ads to display properly.</span></span>

12. <span data-ttu-id="83671-141">Echte Werte für [ApplicationId](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.applicationid) und [AdUnitId](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.adunitid) sollten nicht im Emulator getestet werden.</span><span class="sxs-lookup"><span data-stu-id="83671-141">Live values for [ApplicationId](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.applicationid) and [AdUnitId](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.adunitid) should not be tested in the emulator.</span></span> <span data-ttu-id="83671-142">Um sicherzustellen, dass **AdControl** erwartungsgemäß funktioniert, verwenden Sie [test values](set-up-ad-units-in-your-app.md#test-ad-units) sowohl für **ApplicationId** und **AdUnitId**.</span><span class="sxs-lookup"><span data-stu-id="83671-142">To ensure the **AdControl** is functioning as expected, use the [test values](set-up-ad-units-in-your-app.md#test-ad-units) for both **ApplicationId** and **AdUnitId**.</span></span>

<span id="html-blackboxblinksdisappears"/>

### <a name="black-box-blinks-and-disappears"></a><span data-ttu-id="83671-143">Blackbox blinkt und wird ausgeblendet</span><span class="sxs-lookup"><span data-stu-id="83671-143">Black box blinks and disappears</span></span>

1.  <span data-ttu-id="83671-144">Überprüfen Sie noch einmal alle Schritte im vorherigen Abschnitt [AdControl wird nicht angezeigt](#html-notappearing).</span><span class="sxs-lookup"><span data-stu-id="83671-144">Double-check all steps in the previous [AdControl not appearing](#html-notappearing) section.</span></span>

2.  <span data-ttu-id="83671-145">Behandeln Sie das Ereignis **onErrorOccurred**, und bestimmen Sie anhand der an den Ereignishandler übergebenen Meldung, ob ein Fehler aufgetreten ist und welche Art von Fehler ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="83671-145">Handle the **onErrorOccurred** event, and use the message that is passed to the event handler to determine whether an error occurred and what type of error was thrown.</span></span> <span data-ttu-id="83671-146">Weitere Informationen finden Sie in [Exemplarische Vorgehensweise zur Fehlerbehandlung in JavaScript](error-handling-in-javascript-walkthrough.md).</span><span class="sxs-lookup"><span data-stu-id="83671-146">More details can be found in [Error handling in JavaScript walkthrough](error-handling-in-javascript-walkthrough.md).</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div id="myAd" style="position: absolute; top: 0px; left: 0px;
                          width: 728px; height: 90px; z-index: 1"
         data-win-control="MicrosoftNSJS.Advertising.AdControl"
         data-win-options="{applicationId: 'ApplicationID',
                            adUnitId: 'AdUnitID',
                            onErrorOccurred: errorLogger}">
    </div>
    <div style="position:absolute; width:100%; height:130px; top:300px; left:0px">
        <b>Ad Events</b><br />
        <div id="adEvents" style="width:100%; height:110px; overflow:auto"></div>
    </div>
    ```

    <span data-ttu-id="83671-147">Eine Blackbox wird am häufigsten dadurch verursacht, dass keine Anzeige verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="83671-147">The most common error that causes a black box is “No ad available.”</span></span> <span data-ttu-id="83671-148">Dieser Fehler bedeutet, dass durch die Anforderung keine Anzeige zurückgegeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="83671-148">This error means there is no ad available to return from the request.</span></span>

3.  <span data-ttu-id="83671-149">**AdControl** verhält sich normal.</span><span class="sxs-lookup"><span data-stu-id="83671-149">The **AdControl** is behaving normally.</span></span> <span data-ttu-id="83671-150">**AdControl** wird standardmäßig reduziert, wenn keine Anzeige dargestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="83671-150">By default, the **AdControl** will collapse when it cannot display an ad.</span></span> <span data-ttu-id="83671-151">Wenn andere Elemente demselben übergeordneten Element untergeordnet sind, können sie verschoben werden, um den freien Platz des reduzierten **AdControl**-Elements zu füllen, und bei der nächsten Anforderung erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="83671-151">If other elements are children of the same parent they may move to fill the gap of the collapsed **AdControl** and expand when the next request is made.</span></span>

<span id="html-adsnotrefreshing"/>

### <a name="ads-not-refreshing"></a><span data-ttu-id="83671-152">Anzeigen werden nicht aktualisiert</span><span class="sxs-lookup"><span data-stu-id="83671-152">Ads not refreshing</span></span>

1.  <span data-ttu-id="83671-153">Überprüfen Sie die Eigenschaft **isAutoRefreshEnabled**.</span><span class="sxs-lookup"><span data-stu-id="83671-153">Check the **isAutoRefreshEnabled** property.</span></span> <span data-ttu-id="83671-154">Diese optionale Eigenschaft ist standardmäßig auf true festgelegt.</span><span class="sxs-lookup"><span data-stu-id="83671-154">By default, this optional property is set to true.</span></span> <span data-ttu-id="83671-155">Wenn sie auf false festgelegt ist, muss die **refresh**-Methode verwendet werden, um eine weitere Anzeige abzurufen.</span><span class="sxs-lookup"><span data-stu-id="83671-155">When set to false, the **refresh** method must be used to retrieve another ad.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div id="myAd" style="position: absolute; top: 0px; left: 0px;
                          width: 250px; height: 250px; z-index: 1"
         data-win-control="MicrosoftNSJS.Advertising.AdControl"
         data-win-options="{ applicationId: 'ApplicationID',
                            adUnitId: 'AdUnitID',
                            onErrorOccurred: errorLogger,
                            isAutoRefreshEnabled: true}">
    </div>
    ```

2.  <span data-ttu-id="83671-156">Überprüfen Sie Aufrufe der Methode **refresh**.</span><span class="sxs-lookup"><span data-stu-id="83671-156">Check calls to the **refresh** method.</span></span> <span data-ttu-id="83671-157">Bei Verwendung der automatischen Aktualisierung kann **refresh** nicht verwendet werden, um eine weitere Anzeige abzurufen.</span><span class="sxs-lookup"><span data-stu-id="83671-157">When using automatic refresh, **refresh** cannot be used to retrieve another ad.</span></span> <span data-ttu-id="83671-158">Bei Verwendung der manuellen Aktualisierung sollte **refresh** abhängig von der aktuellen Datenverbindung des Geräts erst nach mindestens 30 bis 60 Sekunden aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="83671-158">When using manual refresh, **refresh** should be called only after a minimum of 30 to 60 seconds depending on the device’s current data connection.</span></span>

    <span data-ttu-id="83671-159">In diesem Beispiel wird die Verwendung der Methode **refresh** gezeigt.</span><span class="sxs-lookup"><span data-stu-id="83671-159">This example demonstrates how to use the **refresh** method.</span></span> <span data-ttu-id="83671-160">Der folgende HTML-Code zeigt ein Beispiel für die Instanziierung von **AdControl**, wenn **isAutoRefreshEnabled** auf false festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="83671-160">The following HTML code shows an example of how to instantiate the **AdControl** with **isAutoRefreshEnabled** set to false.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div id="myAd" style="position: absolute; top: 0px; left: 0px;
                          width: 250px; height: 250px; z-index: 1"
         data-win-control="MicrosoftNSJS.Advertising.AdControl"
         data-win-options="{ applicationId: 'ApplicationID',
                            adUnitId: 'AdUnitID',
                            onErrorOccurred: errorLogger,
                            isAutoRefreshEnabled: false}">
    </div>
    ```

    <span data-ttu-id="83671-161">Dieses Beispiel zeigt die Verwendung der Funktion **refresh**.</span><span class="sxs-lookup"><span data-stu-id="83671-161">Theis example demonstrates how to use the **refresh** function.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` javascript
    args.setPromise(WinJS.UI.processAll()
        .then(function (args) {
            window.setInterval(function()
            {
                document.getElementById("myAd").winControl.refresh();
            }, 60000)
        })
    );
    ```

3.  <span data-ttu-id="83671-162">**AdControl** verhält sich normal.</span><span class="sxs-lookup"><span data-stu-id="83671-162">The **AdControl** is behaving normally.</span></span> <span data-ttu-id="83671-163">In einigen Fällen wird dieselbe Anzeige mehrmals in Folge angezeigt, wodurch der Eindruck entsteht, dass Anzeigen nicht aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="83671-163">Sometimes the same ad will appear more than once in a row giving the appearance that ads are not refreshing.</span></span>

<span id="js"/>

## <a name="javascript"></a><span data-ttu-id="83671-164">JavaScript</span><span class="sxs-lookup"><span data-stu-id="83671-164">JavaScript</span></span>

<span id="js-adcontrolnotappearing"/>

### <a name="adcontrol-not-appearing"></a><span data-ttu-id="83671-165">AdControl wird nicht angezeigt</span><span class="sxs-lookup"><span data-stu-id="83671-165">AdControl not appearing</span></span>

1.  <span data-ttu-id="83671-166">Stellen Sie sicher, dass die **Internet (Client)**-Funktion in „Package.appxmanifest“ ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="83671-166">Ensure that the **Internet (Client)** capability is selected in Package.appxmanifest.</span></span>

2.  <span data-ttu-id="83671-167">Stellen Sie sicher, dass **AdControl** instanziiert ist.</span><span class="sxs-lookup"><span data-stu-id="83671-167">Ensure the **AdControl** is instantiated.</span></span> <span data-ttu-id="83671-168">Wenn **AdControl** nicht instanziiert ist,</span><span class="sxs-lookup"><span data-stu-id="83671-168">If the **AdControl** is not instantiated.</span></span> <span data-ttu-id="83671-169">ist es nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="83671-169">it will not be available.</span></span>

    <span data-ttu-id="83671-170">Die folgenden Codeausschnitte zeigen ein Beispiel für die Instanziierung von **AdControl**.</span><span class="sxs-lookup"><span data-stu-id="83671-170">The following snippets show an example of instantiating the **AdControl**.</span></span> <span data-ttu-id="83671-171">Dieser HTML-Code zeigt ein Beispiel für das Einrichten der Benutzeroberfläche für **AdControl**.</span><span class="sxs-lookup"><span data-stu-id="83671-171">This HTML code shows an example of setting up the UI for the **AdControl**</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div id="myAd" style="position: absolute; top: 0px; left: 0px;
                          width: 250px; height: 250px; z-index: 1"
         data-win-control="MicrosoftNSJS.Advertising.AdControl">
    </div>
    ```

    <span data-ttu-id="83671-172">Der folgende JavaScript-Code zeigt ein Beispiel für die Instanziierung von **AdControl**.</span><span class="sxs-lookup"><span data-stu-id="83671-172">The following JavaScript code shows an example of instantiating the **AdControl**</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` javascript
    app.onactivated = function (args) {
        if (args.detail.kind === activation.ActivationKind.launch) {
            if (args.detail.previousExecutionState !==
                    activation.ApplicationExecutionState.terminated)
            {
                var adDiv = document.getElementById("myAd");
                var myAdControl = new MicrosoftNSJS.Advertising.AdControl(adDiv,
                {
                    applicationId: "{ApplicationID}",
                    adUnitId: "{AdUnitID}"
                 });                
                 myAdControl.onErrorOccurred = myAdError;
            } else {
                ...
            }
        }
    }
    ```

3.  <span data-ttu-id="83671-173">Überprüfen Sie das übergeordnete Element.</span><span class="sxs-lookup"><span data-stu-id="83671-173">Check the parent element.</span></span> <span data-ttu-id="83671-174">Das übergeordnete Element **&lt;div&gt;** muss richtig zugewiesen, aktiv und sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="83671-174">The parent **&lt;div&gt;** must be correctly assigned, active, and visible.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` javascript
    var adDiv = document.getElementById("myAd");
    var myAdControl = new MicrosoftNSJS.Advertising.AdControl(adDiv, {
        applicationId: "{ApplicationID}",
        adUnitId: "{AdUnitID}"
    });  
    ```

4.  <span data-ttu-id="83671-175">Überprüfen Sie die ID der Anwendung und der Anzeigeneinheit.</span><span class="sxs-lookup"><span data-stu-id="83671-175">Check the application ID and ad unit ID.</span></span> <span data-ttu-id="83671-176">Diese IDs müssen übereinstimmen, die Anwendungs-ID und anzeigeneinheits-ID, die Sie in Partner Center erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="83671-176">These IDs must match the application ID and ad unit ID that you obtained in Partner Center.</span></span> <span data-ttu-id="83671-177">Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in der App](set-up-ad-units-in-your-app.md#live-ad-units).</span><span class="sxs-lookup"><span data-stu-id="83671-177">For more information, see [Set up ad units in your app](set-up-ad-units-in-your-app.md#live-ad-units).</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` javascript
    var myAdControl = new MicrosoftNSJS.Advertising.AdControl(adDiv, {
        applicationId: "{ApplicationID}",
        adUnitId: "{AdUnitID}"
    });  
    ```

5.  <span data-ttu-id="83671-178">Überprüfen Sie das übergeordnete Element von **AdControl**.</span><span class="sxs-lookup"><span data-stu-id="83671-178">Check the parent element of the **AdControl**.</span></span> <span data-ttu-id="83671-179">Das übergeordnete Element muss aktiv und sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="83671-179">The parent must be active and visible.</span></span>

6.  <span data-ttu-id="83671-180">Echte Werte für **ApplicationId** und **AdUnitId** sollten nicht im Emulator getestet werden.</span><span class="sxs-lookup"><span data-stu-id="83671-180">Live values for **ApplicationId** and **AdUnitId** should not be tested in the emulator.</span></span> <span data-ttu-id="83671-181">Um sicherzustellen, dass **AdControl** erwartungsgemäß funktioniert, verwenden Sie [test values](set-up-ad-units-in-your-app.md#test-ad-units) sowohl für **ApplicationId** und **AdUnitId**.</span><span class="sxs-lookup"><span data-stu-id="83671-181">To ensure the **AdControl** is functioning as expected, use the [test values](set-up-ad-units-in-your-app.md#test-ad-units) for both **ApplicationId** and **AdUnitId**.</span></span>

<span id="js-blackboxblinksdisappears"/>

### <a name="black-box-blinks-and-disappears"></a><span data-ttu-id="83671-182">Blackbox blinkt und wird ausgeblendet</span><span class="sxs-lookup"><span data-stu-id="83671-182">Black box blinks and disappears</span></span>

1.  <span data-ttu-id="83671-183">Überprüfen Sie noch einmal alle Schritte im Abschnitt [AdControl wird nicht angezeigt](#js-adcontrolnotappearing).</span><span class="sxs-lookup"><span data-stu-id="83671-183">Double-check all steps in the [AdControl not appearing](#js-adcontrolnotappearing) section.</span></span>

2.  <span data-ttu-id="83671-184">Behandeln Sie das Ereignis **onErrorOccurred**, und bestimmen Sie anhand der an den Ereignishandler übergebenen Meldung, ob ein Fehler aufgetreten ist und welche Art von Fehler ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="83671-184">Handle the **onErrorOccurred** event, and use the message that is passed to the event handler to determine whether an error occurred and what type of error was thrown.</span></span> <span data-ttu-id="83671-185">Weitere Informationen finden Sie in [Exemplarische Vorgehensweise zur Fehlerbehandlung in JavaScript](error-handling-in-javascript-walkthrough.md).</span><span class="sxs-lookup"><span data-stu-id="83671-185">More details can be found in [Error handling in JavaScript walkthrough](error-handling-in-javascript-walkthrough.md).</span></span>

    <span data-ttu-id="83671-186">In diesem Beispiel wird die Implementierung eines Fehlerhandlers gezeigt, der Fehlermeldungen meldet.</span><span class="sxs-lookup"><span data-stu-id="83671-186">This example demonstrates how to implement an error handler that reports error messages.</span></span> <span data-ttu-id="83671-187">Der folgende HTML-Codeausschnitt enthält ein Beispiel für das Einrichten der Benutzeroberfläche zum Anzeigen von Fehlermeldungen.</span><span class="sxs-lookup"><span data-stu-id="83671-187">This snippet of HTML code provides an example of how to set up the UI to display error messages.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div style="position:absolute; width:100%; height:130px; top:300px">
        <b>Ad Events</b><br />
        <div id="adEvents" style="width:100%; height:110px; overflow:auto"></div>
    </div>
    ```

    <span data-ttu-id="83671-188">In diesem Beispiel wird die Instanziierung von **AdControl** gezeigt.</span><span class="sxs-lookup"><span data-stu-id="83671-188">This example demonstrates how to instantiate the **AdControl**.</span></span> <span data-ttu-id="83671-189">Diese Funktion würde in der Datei app.onactivated eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="83671-189">This function would be inserted in the app.onactivated file.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` javascript
    var myAdControl = new MicrosoftNSJS.Advertising.AdControl(adDiv,
    {
        applicationId: "{ApplicationID}",
        adUnitId: "{AdUnitID}"
    });                
    myAdControl.onErrorOccurred = myAdError;
    ```

    <span data-ttu-id="83671-190">In diesem Beispiel wird die Meldung von Fehlern gezeigt.</span><span class="sxs-lookup"><span data-stu-id="83671-190">This example demonstrates how to report errors.</span></span> <span data-ttu-id="83671-191">Diese Funktion würde unterhalb der selbstausführenden Funktion in der Datei default.js eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="83671-191">This function would be inserted below the self-running function in the default.js file.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` javascript
    WinJS.Utilities.markSupportedForProcessing
    (
        window.errorLogger = function (sender, evt)
        {
            adEvents.innerHTML = (new Date()).toLocaleTimeString() + ": " +
            sender.element.id + " error: " + evt.errorMessage + " error code: " +
            evt.errorCode + "<br>" + adEvents.innerHTML;
        }
    );
    ```

    <span data-ttu-id="83671-192">Eine Blackbox wird am häufigsten dadurch verursacht, dass keine Anzeige verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="83671-192">The most common error that causes a black box is “No ad available.”</span></span> <span data-ttu-id="83671-193">Dieser Fehler bedeutet, dass durch die Anforderung keine Anzeige zurückgegeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="83671-193">This error means there is no ad available to return from the request.</span></span>

3.  <span data-ttu-id="83671-194">**AdControl** verhält sich normal.</span><span class="sxs-lookup"><span data-stu-id="83671-194">The **AdControl** is behaving normally.</span></span> <span data-ttu-id="83671-195">In einigen Fällen wird dieselbe Anzeige mehrmals in Folge angezeigt, wodurch der Eindruck entsteht, dass Anzeigen nicht aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="83671-195">Sometimes the same ad will appear more than once in a row giving the appearance that ads are not refreshing.</span></span>

<span id="js-adsnotrefreshing"/>

### <a name="ads-not-refreshing"></a><span data-ttu-id="83671-196">Anzeigen werden nicht aktualisiert</span><span class="sxs-lookup"><span data-stu-id="83671-196">Ads not refreshing</span></span>

1.  <span data-ttu-id="83671-197">Überprüfen Sie, ob in der [IsAutoRefreshEnabled](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.isautorefreshenabled.aspx)-Eigenschaft **AdControl** auf „false“ festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="83671-197">Check whether the [IsAutoRefreshEnabled](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.isautorefreshenabled.aspx) property of your **AdControl** is set to false.</span></span> <span data-ttu-id="83671-198">Diese optionale Eigenschaft ist standardmäßig auf **true** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="83671-198">By default, this optional property is set to **true**.</span></span> <span data-ttu-id="83671-199">Wenn sie auf **false** festgelegt ist, muss die Methode **Refresh** verwendet werden, um eine weitere Anzeige abzurufen.</span><span class="sxs-lookup"><span data-stu-id="83671-199">When set to **false**, the **Refresh** method must be used to retrieve another ad.</span></span>

2.  <span data-ttu-id="83671-200">Überprüfen Sie Aufrufe der [Refresh](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.refresh.aspx)-Methode.</span><span class="sxs-lookup"><span data-stu-id="83671-200">Check calls to the [Refresh](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.refresh.aspx) method.</span></span> <span data-ttu-id="83671-201">Bei Verwendung der automatischen Aktualisierung ((**IsAutoRefreshEnabled** ist **true**)) kann **Refresh** nicht verwendet werden, um eine weitere Anzeige abzurufen.</span><span class="sxs-lookup"><span data-stu-id="83671-201">When using automatic refresh (**IsAutoRefreshEnabled** is **true**), **Refresh** cannot be used to retrieve another ad.</span></span> <span data-ttu-id="83671-202">Bei Verwendung der manuellen Aktualisierung (**IsAutoRefreshEnabled** ist **false**) sollte **Refresh** abhängig von der aktuellen Datenverbindung des Geräts erst nach mindestens 30 bis 60 Sekunden aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="83671-202">When using manual refresh (**IsAutoRefreshEnabled** is **false**), **Refresh** should be called only after a minimum of 30 to 60 seconds depending on the device’s current data connection.</span></span>

    <span data-ttu-id="83671-203">Dieses Beispiel zeigt das Erstellen von **div** für **AdControl**.</span><span class="sxs-lookup"><span data-stu-id="83671-203">This example demonstrates how to create the **div** for the **AdControl**.</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` html
    <div id="myAd" style="position: absolute; top: 0px; left: 0px;
                          width: 250px; height: 250px; z-index: 1"
         data-win-control="MicrosoftNSJS.Advertising.AdControl">
    </div>
    ```

    <span data-ttu-id="83671-204">In diesem Beispiel wird die Verwendung der **Refresh**-Funktion gezeigt.</span><span class="sxs-lookup"><span data-stu-id="83671-204">This example shows how to use the **Refresh** function</span></span>

    > [!div class="tabbedCodeSnippets"]
    ``` javascript
    var myAdControl = new MicrosoftNSJS.Advertising.AdControl(adDiv,
    {
      applicationId: "{ApplicationID}",
      adUnitId: "{AdUnitID}",
      isAutoRefreshEnabled: false
    });
    ...
    args.setPromise(WinJS.UI.processAll()
        .then(function (args) {
            window.setInterval(function()
            {
                document.getElementById("myAd").winControl.refresh();
            }, 60000)
        })
    );
    ```

3.  <span data-ttu-id="83671-205">**AdControl** verhält sich normal.</span><span class="sxs-lookup"><span data-stu-id="83671-205">The **AdControl** is behaving normally.</span></span> <span data-ttu-id="83671-206">In einigen Fällen wird dieselbe Anzeige mehrmals in Folge angezeigt, wodurch der Eindruck entsteht, dass Anzeigen nicht aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="83671-206">Sometimes the same ad will appear more than once in a row giving the appearance that ads are not refreshing.</span></span>

 

 
