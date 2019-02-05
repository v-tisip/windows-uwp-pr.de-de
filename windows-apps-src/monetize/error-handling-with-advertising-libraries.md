---
ms.assetid: cb7380d0-bc14-4936-aa1c-206304b3dc70
description: Hier erfahren Sie, wie Sie mit Fehlern umgehen, die in den Microsoft Advertising-Bibliotheken von der AdControl-Klasse generiert werden.
title: Behandeln von Fehlern bei Anzeigen
ms.date: 05/11/2018
ms.topic: article
keywords: Windows10, UWP, Anzeige, Werbung, Fehlerbehandlung, Javascript, XAML, C#
ms.localizationpriority: medium
ms.openlocfilehash: d0e2e1c019497fc22e8d922ba5f0a02a30034b65
ms.sourcegitcommit: bf600a1fb5f7799961914f638061986d55f6ab12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "9050663"
---
# <a name="handle-ad-errors"></a><span data-ttu-id="0560b-104">Behandeln von Fehlern bei Anzeigen</span><span class="sxs-lookup"><span data-stu-id="0560b-104">Handle ad errors</span></span>

<span data-ttu-id="0560b-105">Die einzelnen Klassen [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol), [InterstitialAd](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.interstitialad) und [NativeAdsManagerV2](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.nativeadsmanagerv2) verfügen über ein **ErrorOccurred**-Ereignis, das ausgelöst wird, wenn ein Fehler im Zusammenhang mit Anzeigen auftritt.</span><span class="sxs-lookup"><span data-stu-id="0560b-105">The [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol),  [InterstitialAd](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.interstitialad), and [NativeAdsManagerV2](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.nativeadsmanagerv2) classes each have an **ErrorOccurred** event that is raised if an ad-related error occurs.</span></span> <span data-ttu-id="0560b-106">Der App-Code kann dieses Ereignis behandeln und die Eigenschaften von [ErrorCode](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.aderroreventargs.errorcode) und [ErrorMessage](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.aderroreventargs.errormessage) des Ereignisarguments untersuchen, um die Ursache des Fehlers zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="0560b-106">Your app code can handle this event and examine the [ErrorCode](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.aderroreventargs.errorcode) and [ErrorMessage](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.aderroreventargs.errormessage) properties of the event args object to help determine the cause of the error.</span></span>

<span id="bkmk-dotnet"/>

## <a name="xaml-apps"></a><span data-ttu-id="0560b-107">XAML-Apps</span><span class="sxs-lookup"><span data-stu-id="0560b-107">XAML apps</span></span>

<span data-ttu-id="0560b-108">So behandeln Sie Anzeigen-bezogene Fehler in einer XAML-App:</span><span class="sxs-lookup"><span data-stu-id="0560b-108">To handle ad-related errors in a XAML app:</span></span>

1. <span data-ttu-id="0560b-109">Weisen Sie das **ErrorOccurred**-Ereignis des Objekts **AdControl**, **InterstitialAd** oder **NativeAdsManagerV2** dem Namen eines Ereignishandlerdelegaten zu.</span><span class="sxs-lookup"><span data-stu-id="0560b-109">Assign the **ErrorOccurred** event of your **AdControl**, **InterstitialAd**, or **NativeAdsManagerV2** object to the name of an event handler delegate.</span></span>

2. <span data-ttu-id="0560b-110">Codieren Sie den Ereignishandlerdelegaten so, dass er zwei Parameter verwendet: ein **Objekt** für den Absender und ein [AdErrorEventArgs](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.aderroreventargs)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="0560b-110">Code the error event handling delegate so that it takes two parameters: an **Object** for the sender and an [AdErrorEventArgs](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.aderroreventargs) object.</span></span>

<span data-ttu-id="0560b-111">Hier ist ein Beispiel, das einen Delegaten mit dem Namen **OnAdError**dem Ereignis **ErrorOccurred** des **AdControl**-Objekts mit Namen *myBannerAdControl* zuweist.</span><span class="sxs-lookup"><span data-stu-id="0560b-111">Here is an example that assigns a delegate named **OnAdError** to the **ErrorOccurred** event of an **AdControl** object named *myBannerAdControl*.</span></span>

> [!div class="tabbedCodeSnippets"]
``` csharp
myBannerAdControl.ErrorOccurred = OnAdError;
```

<span data-ttu-id="0560b-112">Hier ist eine Beispieldefinition des **OnAdError**-Delegaten, die Fehlerinformationen in das Ausgabefenster in Visual Studio schreibt.</span><span class="sxs-lookup"><span data-stu-id="0560b-112">Here is an example definition of the **OnAdError** delegate that writes error information to the output window in Visual Studio.</span></span>

> [!div class="tabbedCodeSnippets"]
``` csharp
private void OnAdError(object sender, AdErrorEventArgs e)
{
    System.Diagnostics.Debug.WriteLine("AdControl error (" + ((AdControl)sender).Name + "): " + e.Error +
        " ErrorCode: " + e.ErrorCode.ToString());
}
```

<span data-ttu-id="0560b-113">Unter [Exemplarische Vorgehensweise zur Fehlerbehandlung in XAML/C#](error-handling-in-xamlc-walkthrough.md) finden Sie eine exemplarische Vorgehensweise zur Veranschaulichung der **AdControl**-Fehlerbehandlung in XAML und C#.</span><span class="sxs-lookup"><span data-stu-id="0560b-113">See [Error handling in XAML/C# walkthrough](error-handling-in-xamlc-walkthrough.md) for a walkthrough that demonstrates **AdControl** error handling in XAML and C#.</span></span>

<span id="bkmk-javascript"/>

## <a name="javascripthtml-apps"></a><span data-ttu-id="0560b-114">JavaScript/HTML-Apps</span><span class="sxs-lookup"><span data-stu-id="0560b-114">JavaScript/HTML apps</span></span>

<span data-ttu-id="0560b-115">So behandeln Sie **ErrorOccur** Fehler in einer JavaScript-App:</span><span class="sxs-lookup"><span data-stu-id="0560b-115">To handle **ErrorOccur** errors in a JavaScript app:</span></span>

1.  <span data-ttu-id="0560b-116">Weisen Sie das **OnErrorOccurred**-Ereignis einem Ereignishandler zu.</span><span class="sxs-lookup"><span data-stu-id="0560b-116">Assign the **onErrorOccurred** event to an event handler.</span></span>

2.  <span data-ttu-id="0560b-117">Codieren Sie den Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="0560b-117">Code the event handler.</span></span>

<span data-ttu-id="0560b-118">Hier ist ein Beispiel, das einen Ereignishandler mit dem Namen **errorLogger** dem Ereignis **ErrorOccurred** des **AdControl**-Objekts zuweist.</span><span class="sxs-lookup"><span data-stu-id="0560b-118">Here is an example that assigns an event handler named **errorLogger** to the **ErrorOccurred** event of an **AdControl** object.</span></span>

> [!div class="tabbedCodeSnippets"]
``` html
<div id="myAd" style="position: absolute; top: 53px; left: 0px; width: 250px; height: 250px; z-index: 1"
     data-win-control="MicrosoftNSJS.Advertising.AdControl"
     data-win-options="{applicationId: '3f83fe91-d6be-434d-a0ae-7351c5a997f1', adUnitId: 'test', onErrorOccurred: errorLogger}">
</div>
```

<span data-ttu-id="0560b-119">Die Fehlerbehandlungsfunktion ist deklarativ und muss in die Funktion [MarkSupportedForProcessing](https://msdn.microsoft.com/library/windows/apps/Hh967819.aspx) eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="0560b-119">The error handling function is declarative and must be enclosed in the [markSupportedForProcessing](https://msdn.microsoft.com/library/windows/apps/Hh967819.aspx) function.</span></span>

<span data-ttu-id="0560b-120">Der Fehlerhandler fängt das JavaScript-Fehlerobjekt auf, wenn ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="0560b-120">The error handler catches the JavaScript error object when an error occurs.</span></span> <span data-ttu-id="0560b-121">Das Fehlerobjekt liefert dem Fehlerhandler zwei Argumente.</span><span class="sxs-lookup"><span data-stu-id="0560b-121">The error object provides two arguments to the error handler.</span></span> <span data-ttu-id="0560b-122">Weitere Informationen finden Sie unter [Eigenschaften spezieller Fehler von asynchronen Methoden von Windows-Runtime](https://msdn.microsoft.com/library/windows/apps/hh994690.aspx).</span><span class="sxs-lookup"><span data-stu-id="0560b-122">For more information, see [Special Error Properties from Asynchronous Windows Runtime Methods](https://msdn.microsoft.com/library/windows/apps/hh994690.aspx).</span></span>

<span data-ttu-id="0560b-123">Hier ist ein Beispiel für eine Fehlerbehandlungsfunktion mit dem Namen **ErrorLogger**, die das Ereignis **OnErrorOccurred** behandelt.</span><span class="sxs-lookup"><span data-stu-id="0560b-123">Here is an example of an error handling function named **errorLogger** that handles the **onErrorOccurred** event.</span></span>

> [!div class="tabbedCodeSnippets"]
``` javascript
WinJS.Utilities.markSupportedForProcessing(
window.errorLogger = function (sender, evt) {
    console.log(new Date()).toLocaleTimeString() + ": " + sender.element.id + " error: " + evt.errorMessage +
    " error code: " + evt.errorCode + \n");
});
```

<span data-ttu-id="0560b-124">Unter [Exemplarische Vorgehensweise zur Fehlerbehandlung in JavaScript](error-handling-in-javascript-walkthrough.md) finden Sie eine exemplarische Vorgehensweise zur Veranschaulichung der **AdControl**-Fehlerbehandlung in JavaScript.</span><span class="sxs-lookup"><span data-stu-id="0560b-124">See [Error Handling in JavaScript walkthrough](error-handling-in-javascript-walkthrough.md) for a walkthrough that demonstrates **AdControl** error handling in JavaScript.</span></span>
