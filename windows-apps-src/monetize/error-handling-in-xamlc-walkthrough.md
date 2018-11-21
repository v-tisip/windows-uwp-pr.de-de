---
author: Xansky
ms.assetid: cf0d2709-21a1-4d56-9341-d4897e405f5d
description: Hier erfahren Sie, wie AdControl-Fehler in Ihrer App aufgefangen werden.
title: Exemplarische Vorgehensweise zur Fehlerbehandlung in XAML/C#
ms.author: mhopkins
ms.date: 05/11/2018
ms.topic: article
keywords: Windows10, UWP, Anzeige, Werbung, Fehlerbehandlung, XAML, C#
ms.localizationpriority: medium
ms.openlocfilehash: be101f5ec189d822bc9704b435f4a098b61f57ac
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7582380"
---
# <a name="error-handling-in-xamlc-walkthrough"></a><span data-ttu-id="d4ce6-104">Exemplarische Vorgehensweise zur Fehlerbehandlung in XAML/C#</span><span class="sxs-lookup"><span data-stu-id="d4ce6-104">Error handling in XAML/C# walkthrough</span></span>

<span data-ttu-id="d4ce6-105">In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Anzeigen-bezogene Fehler in Ihrer App erfasst werden können.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-105">This walkthrough demonstrates how to catch ad-related errors in your app.</span></span> <span data-ttu-id="d4ce6-106">In dieser exemplarischen Vorgehensweise wird ein [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) verwendet, um eine Banneranzeige anzuzeigen, die allgemeinen Konzepte gelten jedoch auch für Interstitialwerbung und native Anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-106">This walkthrough uses an [AdControl](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol) to display a banner ad, but the general concepts in it also apply to interstitial ads and native ads.</span></span>

<span data-ttu-id="d4ce6-107">In diesen Beispielen wird davon ausgegangen, dass Sie eine XAML/C#-App haben, die ein **AdControl** enthält.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-107">These examples assume that you have a XAML/C# app that contains an **AdControl**.</span></span> <span data-ttu-id="d4ce6-108">Schritt-für-Schritt-Anleitungen, die zeigen, wie ein **AdControl** zu Ihrer App hinzugefügt wird, finden Sie unter [AdControl in XAML und .NET](adcontrol-in-xaml-and--net.md).</span><span class="sxs-lookup"><span data-stu-id="d4ce6-108">For step-by-step instructions that demonstrate how to add an **AdControl** to your app, see [AdControl in XAML and .NET](adcontrol-in-xaml-and--net.md).</span></span> 

1.  <span data-ttu-id="d4ce6-109">Suchen Sie in der Datei "MainPage.xaml" nach der Definition für das **AdControl**.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-109">In your MainPage.xaml file, locate the definition for the **AdControl**.</span></span> <span data-ttu-id="d4ce6-110">Dieser Code sieht folgendermaßen aus.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-110">That code looks like this.</span></span>
    ``` xml
    <UI:AdControl
      ApplicationId="3f83fe91-d6be-434d-a0ae-7351c5a997f1"
      AdUnitId="test"
      HorizontalAlignment="Left"
      Height="250"
      Margin="10,10,0,0"
      VerticalAlignment="Top"
      Width="300" />
    ```

2.   <span data-ttu-id="d4ce6-111">Weisen Sie nach der Eigenschaft **Width**, jedoch vor dem Endtag, dem Ereignis [ErrorOccurred](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.erroroccurred) den Namen eines Fehlerereignishandlers zu.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-111">After the **Width** property, but before the closing tag, assign a name of an error event handler to the [ErrorOccurred](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.erroroccurred) event.</span></span> <span data-ttu-id="d4ce6-112">In dieser exemplarischen Vorgehensweise ist der Name des Fehlerereignishandlers **OnAdError**.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-112">In this walkthrough, the name of the error event handler is **OnAdError**.</span></span>
    ``` xml
    <UI:AdControl
      ApplicationId="3f83fe91-d6be-434d-a0ae-7351c5a997f1"
      AdUnitId="test"
      HorizontalAlignment="Left"
      Height="250"
      Margin="10,10,0,0"
      VerticalAlignment="Top"
      Width="300"
      ErrorOccurred="OnAdError"/>
    ```

3.  <span data-ttu-id="d4ce6-113">Um einen Fehler zur Laufzeit zu generieren, erstellen Sie ein zweites **AdControl**-Element mit einer anderen Anwendungs-ID.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-113">To generate an error at runtime, create a second **AdControl** with a different application ID.</span></span> <span data-ttu-id="d4ce6-114">Da alle **AdControl**-Objekte in einer Anwendung die gleiche Anwendungs-ID verwenden müssen, wird durch das Erstellen eines zusätzlichen **AdControl** mit einer anderen Anwendungs-ID ein Fehler ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-114">Because all **AdControl** objects in an app must use the same application ID, creating an additional **AdControl** with a different application id will throw an error.</span></span>

    <span data-ttu-id="d4ce6-115">Definieren Sie ein zweites **AdControl** in der Datei "MainPage.xaml" direkt nach dem ersten **AdControl**, und legen Sie für die Eigenschaft [ApplicationId](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.applicationid) den Wert "0" fest.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-115">Define a second **AdControl** in MainPage.xaml just after the first **AdControl**, and set the [ApplicationId](https://docs.microsoft.com/uwp/api/microsoft.advertising.winrt.ui.adcontrol.applicationid) property to zero (“0”).</span></span>
    ``` xml
    <UI:AdControl
        ApplicationId="0"
        AdUnitId="test"
        HorizontalAlignment="Left"
        Height="250"
        Margin="10,265,0,0"
        VerticalAlignment="Top"
        Width="300"
        ErrorOccurred="OnAdError" />
    ```

4.  <span data-ttu-id="d4ce6-116">Fügen Sie in der Datei "MainPage.xaml.cs" den folgenden Ereignishandler **OnAdError** der **MainPage**-Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-116">In MainPage.xaml.cs, add the following **OnAdError** event handler to the **MainPage** class.</span></span> <span data-ttu-id="d4ce6-117">Dieser Ereignishandler schreibt Informationen in das Visual Studio **Ausgabe**-Fenster.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-117">This event handler writes information to the Visual Studio **Output** window.</span></span>
    ``` csharp
    private void OnAdError(object sender, AdErrorEventArgs e)
    {
        System.Diagnostics.Debug.WriteLine("AdControl error (" + ((AdControl)sender).Name +
            "): " + e.ErrorMessage + " ErrorCode: " + e.ErrorCode.ToString());
    }
    ```

4.  <span data-ttu-id="d4ce6-118">Erstellen Sie das Projekt, und führen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-118">Build and run the project.</span></span> <span data-ttu-id="d4ce6-119">Nach Ausführen der Anwendung wird eine Meldung ähnlich der Meldung unten im **Ausgabe**-Fenster von Visual Studio angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d4ce6-119">After the app is running, you will see a message similar to the one below in the **Output** window of Visual Studio.</span></span>
    ```
    AdControl error (): MicrosoftAdvertising.Shared.AdException: all ad requests must use the same application ID within a single application (0, d25517cb-12d4-4699-8bdc-52040c712cab) ErrorCode: ClientConfiguration
    ```

## <a name="related-topics"></a><span data-ttu-id="d4ce6-120">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d4ce6-120">Related topics</span></span>

* [<span data-ttu-id="d4ce6-121">Anzeigenbeispiele bei GitHub</span><span class="sxs-lookup"><span data-stu-id="d4ce6-121">Advertising samples on GitHub</span></span>](http://aka.ms/githubads)
