---
author: Xansky
ms.assetid: 08b4ae43-69e8-4424-b3c0-a07c93d275c3
description: Hier erfahren Sie, wie AdControl-Fehler in Ihrer App aufgefangen werden.
title: Exemplarische Vorgehensweise zur Fehlerbehandlung in JavaScript
ms.author: mhopkins
ms.date: 05/11/2018
ms.topic: article
keywords: Windows10, UWP, Anzeige, Werbung, Fehlerbehandlung, JavaScript
ms.localizationpriority: medium
ms.openlocfilehash: 65887bba125d8d7db1b224c1842da8c9ab34f117
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6668897"
---
# <a name="error-handling-in-javascript-walkthrough"></a><span data-ttu-id="9e981-104">Exemplarische Vorgehensweise zur Fehlerbehandlung in JavaScript</span><span class="sxs-lookup"><span data-stu-id="9e981-104">Error handling in JavaScript walkthrough</span></span>

<span data-ttu-id="9e981-105">In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Anzeigen-bezogene Fehler in Ihrer JavaScript-App erfasst werden können.</span><span class="sxs-lookup"><span data-stu-id="9e981-105">This walkthrough demonstrates how to catch ad-related errors in your JavaScript app.</span></span> <span data-ttu-id="9e981-106">In dieser exemplarischen Vorgehensweise wird ein [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) verwendet, um eine Banneranzeige anzuzeigen, die allgemeinen Konzepte gelten jedoch auch für Interstitialwerbung und native Anzeigen.</span><span class="sxs-lookup"><span data-stu-id="9e981-106">This walkthrough uses an [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) to display a banner ad, but the general concepts in it also apply to interstitial ads and native ads.</span></span>

<span data-ttu-id="9e981-107">In diesen Beispielen wird davon ausgegangen, dass Sie eine JavaScript-App haben, die ein **AdControl** enthält.</span><span class="sxs-lookup"><span data-stu-id="9e981-107">These examples assume that you have a JavaScript app that contains an **AdControl**.</span></span> <span data-ttu-id="9e981-108">Schritt-für-Schritt-Anleitungen, die zeigen, wie ein **AdControl** zu Ihrer App hinzugefügt wird, finden Sie unter [AdControl in HTML 5 und Javascript](adcontrol-in-html-5-and-javascript.md).</span><span class="sxs-lookup"><span data-stu-id="9e981-108">For step-by-step instructions that demonstrate how to add an **AdControl** to your app, see [AdControl in HTML 5 and Javascript](adcontrol-in-html-5-and-javascript.md).</span></span> <span data-ttu-id="9e981-109">Ein vollständiges Beispiel-Projekt, das veranschaulicht, wie Sie mithilfe von C# und C++ Werbebanner zu einer JavaScript/HTML-App hinzufügen, finden Sie unter den [Anzeigenbeispielen auf GitHub](http://aka.ms/githubads).</span><span class="sxs-lookup"><span data-stu-id="9e981-109">For a complete sample project that demonstrates how to add banner ads to a JavaScript/HTML app, see the [advertising samples on GitHub](http://aka.ms/githubads).</span></span>

1.  <span data-ttu-id="9e981-110">Fügen Sie in der Datei "default.html" einen Wert für das Ereignis **OnErrorOccurred** hinzu, wo Sie die **data-win-options** in **div** für das **AdControl** definieren.</span><span class="sxs-lookup"><span data-stu-id="9e981-110">In the default.html file, add a value for the **onErrorOccurred** event where you define the **data-win-options** in the **div** for the **AdControl**.</span></span> <span data-ttu-id="9e981-111">Suchen Sie den folgenden Code in der Datei „default.html“.</span><span class="sxs-lookup"><span data-stu-id="9e981-111">Find the following code in the default.html file.</span></span>
    ``` HTML
    <div id="myAd" style="position: absolute; top: 53px; left: 0px; width: 300px; height: 250px; z-index: 1"
      data-win-control="MicrosoftNSJS.Advertising.AdControl"
      data-win-options="{applicationId: '3f83fe91-d6be-434d-a0ae-7351c5a997f1', adUnitId: 'test'}">
    </div>
    ```
    <span data-ttu-id="9e981-112">Fügen Sie nach dem **adUnitId**-Attribut den Wert für das Ereignis **OnErrorOccurred** hinzu.</span><span class="sxs-lookup"><span data-stu-id="9e981-112">Following the **adUnitId** attribute, add the value for the **onErrorOccurred** event.</span></span>
    ``` HTML
    <div id="myAd" style="position: absolute; top: 53px; left: 0px; width: 300px; height: 250px; z-index: 1"
      data-win-control="MicrosoftNSJS.Advertising.AdControl"
      data-win-options="{applicationId: '3f83fe91-d6be-434d-a0ae-7351c5a997f1', adUnitId: 'test', onErrorOccurred: errorLogger}">
  </div>
  ```

2.  <span data-ttu-id="9e981-113">Erstellen Sie ein **div**-Element, das Text anzeigt, damit Sie die generierte Nachrichten sehen können.</span><span class="sxs-lookup"><span data-stu-id="9e981-113">Create a **div** that will display text so you can see the messages being generated.</span></span> <span data-ttu-id="9e981-114">Fügen Sie dazu den folgenden Code nach **div** für **MyAd** hinzu.</span><span class="sxs-lookup"><span data-stu-id="9e981-114">To do this, add the following code after the **div** for **myAd**.</span></span>
    ``` HTML
    <div style="position:absolute; width:100%; height:130px; top:300px; left:0px">
        <b>Ad Events</b><br />
        <div id="adEvents" style="width:100%; height:110px; overflow:auto"></div>
    </div>
    ```

3.  <span data-ttu-id="9e981-115">Erstellen Sie ein **AdControl**, das ein Fehlerereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="9e981-115">Create an **AdControl** that will trigger an error event.</span></span> <span data-ttu-id="9e981-116">Es kann nur eine Anwendungs-ID für alle **AdControl**-Objekte in einer App vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="9e981-116">There can only be one application id for all **AdControl** objects in an app.</span></span> <span data-ttu-id="9e981-117">Das Erstellen eines zusätzlichen AdControl-Objekts mit einer anderen Anwendungs-ID löst einen Fehler zur Laufzeit aus.</span><span class="sxs-lookup"><span data-stu-id="9e981-117">So creating an additional one with a different application id will trigger an error at runtime.</span></span> <span data-ttu-id="9e981-118">Fügen Sie dazu nach den vorherigen **div**-Abschnitten, die Sie hinzugefügt haben, den folgenden Code im "body"-Abschnitt der Seite "default.html" hinzu.</span><span class="sxs-lookup"><span data-stu-id="9e981-118">To do this, after the previous **div** sections you have added, add the following code to the body of the default.html page.</span></span>
    ``` HTML
    <!-- Because only one applicationId can be used, the following ad control will fire an error event. -->
    <div id="liveAd" style="position: absolute; top:500px; left:0px; width:480px; height:80px"
      data-win-control="MicrosoftNSJS.Advertising.AdControl"
      data-win-options="{applicationId: '00000000-0000-0000-0000-000000000000', adUnitId: 'test', onErrorOccurred: errorLogger }" >
    </div>
    ```

4.  <span data-ttu-id="9e981-119">In der Datei "default.js" des Projekts fügen nach der Standardinitialisierungsfunktion den Ereignishandler für **ErrorLogger** hinzu.</span><span class="sxs-lookup"><span data-stu-id="9e981-119">In the project’s default.js file, after the default initialization function, you will add the event handler for **errorLogger**.</span></span> <span data-ttu-id="9e981-120">Führen Sie einen Bildlauf bis zum Ende der Datei durch. Nach dem letzten Semikolon fügen Sie den folgenden Code ein.</span><span class="sxs-lookup"><span data-stu-id="9e981-120">Scroll to the end of the file and after the last semi-colon is where you will put the following code.</span></span>
    ``` javascript
    WinJS.Utilities.markSupportedForProcessing(
    window.errorLogger = function (sender, evt) {
        adEvents.innerHTML = (new Date()).toLocaleTimeString() + ": " +
        sender.element.id + " error: " + evt.errorMessage + " error code: " +
        evt.errorCode + "<br>" + adEvents.innerHTML;
        console.log("errorhandler hit. \n");
    });
    ```

5.  <span data-ttu-id="9e981-121">Erstellen Sie die Datei, und führen Sie diese aus.</span><span class="sxs-lookup"><span data-stu-id="9e981-121">Build and run the file.</span></span> <span data-ttu-id="9e981-122">Sie sehen die ursprüngliche Anzeige aus der Beispiel-App, die Sie zuvor erstellt haben, und der Text unter dieser Anzeige, die den Fehler beschreibt.</span><span class="sxs-lookup"><span data-stu-id="9e981-122">You will see the original ad from the sample app you built previously and text under that ad describing the error.</span></span> <span data-ttu-id="9e981-123">Sie sehen die Anzeige nicht mit der ID **liveAd**.</span><span class="sxs-lookup"><span data-stu-id="9e981-123">You will not see the ad with the id of **liveAd**.</span></span>

## <a name="related-topics"></a><span data-ttu-id="9e981-124">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9e981-124">Related topics</span></span>

* [<span data-ttu-id="9e981-125">Anzeigenbeispiele bei GitHub</span><span class="sxs-lookup"><span data-stu-id="9e981-125">Advertising samples on GitHub</span></span>](http://aka.ms/githubads)
