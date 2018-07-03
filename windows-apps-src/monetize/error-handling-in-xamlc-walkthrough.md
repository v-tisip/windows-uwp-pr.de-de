---
author: mcleanbyron
ms.assetid: cf0d2709-21a1-4d56-9341-d4897e405f5d
description: Hier erfahren Sie, wie AdControl-Fehler in Ihrer App aufgefangen werden.
title: Exemplarische Vorgehensweise zur Fehlerbehandlung in XAML/C#
ms.author: mcleans
ms.date: 05/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeige, Werbung, Fehlerbehandlung, XAML, C#
ms.localizationpriority: medium
ms.openlocfilehash: 5bb793e5ca9bb44e888581f1d5dd3142d0b09ee8
ms.sourcegitcommit: 834992ec14a8a34320c96e2e9b887a2be5477a53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2018
ms.locfileid: "1880791"
---
# <a name="error-handling-in-xamlc-walkthrough"></a><span data-ttu-id="1b108-104">Exemplarische Vorgehensweise zur Fehlerbehandlung in XAML/C#</span><span class="sxs-lookup"><span data-stu-id="1b108-104">Error handling in XAML/C# walkthrough</span></span>

<span data-ttu-id="1b108-105">In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Anzeigen-bezogene Fehler in Ihrer App erfasst werden können.</span><span class="sxs-lookup"><span data-stu-id="1b108-105">This walkthrough demonstrates how to catch ad-related errors in your app.</span></span> <span data-ttu-id="1b108-106">In dieser exemplarischen Vorgehensweise wird ein [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) verwendet, um eine Banneranzeige anzuzeigen, die allgemeinen Konzepte gelten jedoch auch für Interstitialwerbung und native Anzeigen.</span><span class="sxs-lookup"><span data-stu-id="1b108-106">This walkthrough uses an [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) to display a banner ad, but the general concepts in it also apply to interstitial ads and native ads.</span></span>

<span data-ttu-id="1b108-107">In diesen Beispielen wird davon ausgegangen, dass Sie eine XAML/C#-App haben, die ein **AdControl** enthält.</span><span class="sxs-lookup"><span data-stu-id="1b108-107">These examples assume that you have a XAML/C# app that contains an **AdControl**.</span></span> <span data-ttu-id="1b108-108">Schritt-für-Schritt-Anleitungen, die zeigen, wie ein **AdControl** zu Ihrer App hinzugefügt wird, finden Sie unter [AdControl in XAML und .NET](adcontrol-in-xaml-and--net.md).</span><span class="sxs-lookup"><span data-stu-id="1b108-108">For step-by-step instructions that demonstrate how to add an **AdControl** to your app, see [AdControl in XAML and .NET](adcontrol-in-xaml-and--net.md).</span></span> 

1.  <span data-ttu-id="1b108-109">Suchen Sie in der Datei "MainPage.xaml" nach der Definition für das **AdControl**.</span><span class="sxs-lookup"><span data-stu-id="1b108-109">In your MainPage.xaml file, locate the definition for the **AdControl**.</span></span> <span data-ttu-id="1b108-110">Dieser Code sieht folgendermaßen aus.</span><span class="sxs-lookup"><span data-stu-id="1b108-110">That code looks like this.</span></span>
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

2.   <span data-ttu-id="1b108-111">Weisen Sie nach der Eigenschaft **Width**, jedoch vor dem Endtag, dem Ereignis [ErrorOccurred](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.erroroccurred.aspx) den Namen eines Fehlerereignishandlers zu.</span><span class="sxs-lookup"><span data-stu-id="1b108-111">After the **Width** property, but before the closing tag, assign a name of an error event handler to the [ErrorOccurred](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.erroroccurred.aspx) event.</span></span> <span data-ttu-id="1b108-112">In dieser exemplarischen Vorgehensweise ist der Name des Fehlerereignishandlers **OnAdError**.</span><span class="sxs-lookup"><span data-stu-id="1b108-112">In this walkthrough, the name of the error event handler is **OnAdError**.</span></span>
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

3.  <span data-ttu-id="1b108-113">Um einen Fehler zur Laufzeit zu generieren, erstellen Sie ein zweites **AdControl**-Element mit einer anderen Anwendungs-ID.</span><span class="sxs-lookup"><span data-stu-id="1b108-113">To generate an error at runtime, create a second **AdControl** with a different application ID.</span></span> <span data-ttu-id="1b108-114">Da alle **AdControl**-Objekte in einer Anwendung die gleiche Anwendungs-ID verwenden müssen, wird durch das Erstellen eines zusätzlichen **AdControl** mit einer anderen Anwendungs-ID ein Fehler ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="1b108-114">Because all **AdControl** objects in an app must use the same application ID, creating an additional **AdControl** with a different application id will throw an error.</span></span>

    <span data-ttu-id="1b108-115">Definieren Sie ein zweites **AdControl** in der Datei "MainPage.xaml" direkt nach dem ersten **AdControl**, und legen Sie für die Eigenschaft [ApplicationId](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.applicationid.aspx) den Wert "0" fest.</span><span class="sxs-lookup"><span data-stu-id="1b108-115">Define a second **AdControl** in MainPage.xaml just after the first **AdControl**, and set the [ApplicationId](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.applicationid.aspx) property to zero (“0”).</span></span>
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

4.  <span data-ttu-id="1b108-116">Fügen Sie in der Datei "MainPage.xaml.cs" den folgenden Ereignishandler **OnAdError** der **MainPage**-Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="1b108-116">In MainPage.xaml.cs, add the following **OnAdError** event handler to the **MainPage** class.</span></span> <span data-ttu-id="1b108-117">Dieser Ereignishandler schreibt Informationen in das Visual Studio **Ausgabe**-Fenster.</span><span class="sxs-lookup"><span data-stu-id="1b108-117">This event handler writes information to the Visual Studio **Output** window.</span></span>
    ``` csharp
    private void OnAdError(object sender, AdErrorEventArgs e)
    {
        System.Diagnostics.Debug.WriteLine("AdControl error (" + ((AdControl)sender).Name +
            "): " + e.ErrorMessage + " ErrorCode: " + e.ErrorCode.ToString());
    }
    ```

4.  <span data-ttu-id="1b108-118">Erstellen Sie das Projekt, und führen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="1b108-118">Build and run the project.</span></span> <span data-ttu-id="1b108-119">Nach Ausführen der Anwendung wird eine Meldung ähnlich der Meldung unten im **Ausgabe**-Fenster von Visual Studio angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1b108-119">After the app is running, you will see a message similar to the one below in the **Output** window of Visual Studio.</span></span>
    ```
    AdControl error (): MicrosoftAdvertising.Shared.AdException: all ad requests must use the same application ID within a single application (0, d25517cb-12d4-4699-8bdc-52040c712cab) ErrorCode: ClientConfiguration
    ```

## <a name="related-topics"></a><span data-ttu-id="1b108-120">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1b108-120">Related topics</span></span>

* [<span data-ttu-id="1b108-121">Anzeigenbeispiele bei GitHub</span><span class="sxs-lookup"><span data-stu-id="1b108-121">Advertising samples on GitHub</span></span>](http://aka.ms/githubads)
