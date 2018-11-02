---
author: TylerMSFT
title: Starten einer App für Ergebnisse
description: Erfahren Sie, wie Sie eine App über eine andere App starten und Daten zwischen den beiden Apps austauschen. Dieser Vorgang wird als Starten einer App für Ergebnisse bezeichnet.
ms.assetid: AFC53D75-B3DD-4FF6-9FC0-9335242EE327
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 0fbbe1978cc59afcc7d681331dadc9a06e3eb2d0
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5974422"
---
# <a name="launch-an-app-for-results"></a><span data-ttu-id="c2cd1-105">Starten einer App für Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="c2cd1-105">Launch an app for results</span></span>




**<span data-ttu-id="c2cd1-106">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="c2cd1-106">Important APIs</span></span>**

-   [**<span data-ttu-id="c2cd1-107">LaunchUriForResultsAsync</span><span class="sxs-lookup"><span data-stu-id="c2cd1-107">LaunchUriForResultsAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn956686)
-   [**<span data-ttu-id="c2cd1-108">ValueSet</span><span class="sxs-lookup"><span data-stu-id="c2cd1-108">ValueSet</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn636131)

<span data-ttu-id="c2cd1-109">Hier erfahren Sie, wie Sie eine App aus einer anderen App heraus starten und Daten zwischen den beiden Apps austauschen.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-109">Learn how to launch an app from another app and exchange data between the two.</span></span> <span data-ttu-id="c2cd1-110">Dieser Vorgang wird als *Starten einer App für Ergebnisse* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-110">This is called *launching an app for results*.</span></span> <span data-ttu-id="c2cd1-111">Dieses Beispiel veranschaulicht die Verwendung von [**LaunchUriForResultsAsync**](https://msdn.microsoft.com/library/windows/apps/dn956686) zum Starten einer App für Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-111">The example here shows you how to use [**LaunchUriForResultsAsync**](https://msdn.microsoft.com/library/windows/apps/dn956686) to launch an app for results.</span></span>

<span data-ttu-id="c2cd1-112">Neuen APIs in Windows 10-app-zu-app-Kommunikation ermöglichen es für Windows-apps (und Windows-Web-apps) zum Starten einer app und Exchange-Daten und Dateien.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-112">New app-to-app communication APIs in Windows10 make it possible for Windows apps (and Windows Web apps) to launch an app and exchange data and files.</span></span> <span data-ttu-id="c2cd1-113">Dies ermöglicht Ihnen das Erstellen kombinierter Lösungen aus mehreren Apps.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-113">This enables you to build mash-up solutions from multiple apps.</span></span> <span data-ttu-id="c2cd1-114">Dank dieser neuen APIs können komplexe Aufgaben, für die Benutzer bisher mehrere Apps nutzen mussten, jetzt nahtlos durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-114">Using these new APIs, complex tasks that would have required the user to use multiple apps can now be handled seamlessly.</span></span> <span data-ttu-id="c2cd1-115">Ihrer App kann z.B. eine App für ein soziales Netzwerk starten, um einen Kontakt auszuwählen, oder eine Kassen-App, um einen Bezahlvorgang durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-115">For example, your app could launch a social networking app to choose a contact, or launch a checkout app to complete a payment process.</span></span>

<span data-ttu-id="c2cd1-116">Die App, die für Ergebnisse geöffnet wird, wird als gestartete App bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-116">The app that you'll launch for results will be referred to as the launched app.</span></span> <span data-ttu-id="c2cd1-117">Die App, die die App startet, wird als aufrufende App bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-117">The app that launches the app will be referred to as the calling app.</span></span> <span data-ttu-id="c2cd1-118">In diesem Beispiel schreiben Sie die aufrufende App und die gestartete App.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-118">For this example you will write both the calling app and the launched app.</span></span>

## <a name="step-1-register-the-protocol-to-be-handled-in-the-app-that-youll-launch-for-results"></a><span data-ttu-id="c2cd1-119">Schritt 1: Registrieren des Protokolls, das in der App verarbeitet wird, die Sie für Ergebnisse starten</span><span class="sxs-lookup"><span data-stu-id="c2cd1-119">Step 1: Register the protocol to be handled in the app that you'll launch for results</span></span>


<span data-ttu-id="c2cd1-120">Fügen Sie in der Datei „Package.appxmanifest“ der gestarteten App dem Abschnitt **&lt;Application&gt;** eine Protokollerweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-120">In the Package.appxmanifest file of the launched app, add a protocol extension to the **&lt;Application&gt;** section.</span></span> <span data-ttu-id="c2cd1-121">Im folgenden Beispiel wird ein fiktives Protokoll mit dem Namen **test-app2app** verwendet.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-121">The example here uses a fictional protocol named **test-app2app**.</span></span>

<span data-ttu-id="c2cd1-122">Das **ReturnResults**-Attribut in der Protokollerweiterung akzeptiert einen der folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-122">The **ReturnResults** attribute in the protocol extension accepts one of these values:</span></span>

-   <span data-ttu-id="c2cd1-123">**optional**: Die App kann mit der [**LaunchUriForResultsAsync**](https://msdn.microsoft.com/library/windows/apps/dn956686)-Methode für Ergebnisse oder mit der [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476)-Methode nicht für Ergebnisse gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-123">**optional**—The app can be launched for results by using the [**LaunchUriForResultsAsync**](https://msdn.microsoft.com/library/windows/apps/dn956686) method, or not for results by using [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476).</span></span> <span data-ttu-id="c2cd1-124">Bei der Verwendung von **optional** muss die gestartete App ermitteln, ob sie für Ergebnisse gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-124">When you use **optional**, the launched app must determine whether it was launched for results.</span></span> <span data-ttu-id="c2cd1-125">Sie überprüft dazu das [**OnActivated**](https://msdn.microsoft.com/library/windows/apps/br242330)-Ereignisargument.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-125">It can do that by checking the [**OnActivated**](https://msdn.microsoft.com/library/windows/apps/br242330) event argument.</span></span> <span data-ttu-id="c2cd1-126">Wenn die [**IActivatedEventArgs.Kind**](https://msdn.microsoft.com/library/windows/apps/br224728)-Eigenschaft des Arguments[**ActivationKind.ProtocolForResults**](https://msdn.microsoft.com/library/windows/apps/br224693) zurückgibt oder der Typ des Ereignisarguments [**ProtocolActivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224742) ist, wurde die App über **LaunchUriForResultsAsync** gestartet.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-126">If the argument's [**IActivatedEventArgs.Kind**](https://msdn.microsoft.com/library/windows/apps/br224728) property returns [**ActivationKind.ProtocolForResults**](https://msdn.microsoft.com/library/windows/apps/br224693), or if the type of the event argument is [**ProtocolActivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224742), the app was launched via **LaunchUriForResultsAsync**.</span></span>
-   <span data-ttu-id="c2cd1-127">**always**: Die App kann nur für Ergebnisse gestartet werden, d.h. sie kann nur auf [**LaunchUriForResultsAsync**](https://msdn.microsoft.com/library/windows/apps/dn956686) reagieren.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-127">**always**—The app can be launched only for results; that is, it can respond only to [**LaunchUriForResultsAsync**](https://msdn.microsoft.com/library/windows/apps/dn956686).</span></span>
-   <span data-ttu-id="c2cd1-128">**none**: Die App kann nicht für Ergebnisse gestartet werden, d.h. sie kann nur auf [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) reagieren.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-128">**none**—The app cannot be launched for results; it can respond only to [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476).</span></span>

<span data-ttu-id="c2cd1-129">Im folgenden Beispiel für eine Protokollerweiterung kann die App nur für Ergebnisse gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-129">In this protocol-extension example, the app can be launched only for results.</span></span> <span data-ttu-id="c2cd1-130">Dadurch wird die im Folgenden erläuterte Logik innerhalb der **OnActivated**-Methode vereinfacht, da wir nur das „Starten für Ergebnisse“ behandeln müssen und nicht die anderen Möglichkeiten zum Aktivieren der App.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-130">This simplifies the logic inside the **OnActivated** method, discussed below, because we have to handle only the "launched for results" case and not the other ways that the app could be activated.</span></span>

```xml
<Applications>
   <Application ...>

     <Extensions>
       <uap:Extension Category="windows.protocol">
         <uap:Protocol Name="test-app2app" ReturnResults="always">
           <uap:DisplayName>Test app-2-app</uap:DisplayName>
         </uap:Protocol>
       </uap:Extension>
     </Extensions>

   </Application>
</Applications>
```

## <a name="step-2-override-applicationonactivated-in-the-app-that-youll-launch-for-results"></a><span data-ttu-id="c2cd1-131">Schritt 2: Außerkraftsetzen von „Application.OnActivated“ in der App, die Sie für Ergebnisse starten</span><span class="sxs-lookup"><span data-stu-id="c2cd1-131">Step 2: Override Application.OnActivated in the app that you'll launch for results</span></span>


<span data-ttu-id="c2cd1-132">Wenn diese Methode in der gestarteten App noch nicht vorhanden ist, erstellen Sie sie innerhalb der in „App.xaml.cs“ definierten `App`-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-132">If this method does not already exist in the launched app, create it within the `App` class defined in App.xaml.cs.</span></span>

<span data-ttu-id="c2cd1-133">In einer App, in der Sie Freunde in einem sozialen Netzwerk auswählen können, wird mit dieser Funktion beispielsweise die Seite für die Kontaktauswahl geöffnet.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-133">In an app that lets you pick your friends in a social network, this function could be where you open the people-picker page.</span></span> <span data-ttu-id="c2cd1-134">Im folgenden Beispiel wird eine Seite mit dem Namen **LaunchedForResultsPage** angezeigt, wenn die App für Ergebnisse aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-134">In this next example, a page named **LaunchedForResultsPage** is displayed when the app is activated for results.</span></span> <span data-ttu-id="c2cd1-135">Stellen Sie sicher, dass die folgende **using**-Anweisung oben in der Datei vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-135">Ensure that the **using** statement is included at the top of the file.</span></span>

```cs
using Windows.ApplicationModel.Activation;
...
protected override void OnActivated(IActivatedEventArgs args)
{
    // Window management
    Frame rootFrame = Window.Current.Content as Frame;
    if (rootFrame == null)
    {
        rootFrame = new Frame();
        Window.Current.Content = rootFrame;
    }

    // Code specific to launch for results
    var protocolForResultsArgs = (ProtocolForResultsActivatedEventArgs)args;
    // Open the page that we created to handle activation for results.
    rootFrame.Navigate(typeof(LaunchedForResultsPage), protocolForResultsArgs);

    // Ensure the current window is active.
    Window.Current.Activate();
}
```

<span data-ttu-id="c2cd1-136">Da die Protokollerweiterung in der Datei „Package.appxmanifest“ **ReturnResults** als **always** angibt, kann der eben gezeigte Code `args` direkt in [**ProtocolForResultsActivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn906905) umwandeln. Dabei wird sichergestellt, dass für diese App nur **ProtocolForResultsActivatedEventArgs** an **OnActivated** gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-136">Because the protocol extension in the Package.appxmanifest file specifies **ReturnResults** as **always**, the code just shown can cast `args` directly to [**ProtocolForResultsActivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/dn906905) with confidence that only **ProtocolForResultsActivatedEventArgs** will be sent to **OnActivated** for this app.</span></span> <span data-ttu-id="c2cd1-137">Wenn für Ihre App andere Aktivierungsoptionen als „Starten für Ergebnisse“ verfügbar sind, können Sie überprüfen, ob die [**IActivatedEventArgs.Kind**](https://msdn.microsoft.com/library/windows/apps/br224728)-Eigenschaft [**ActivationKind.ProtocolForResults**](https://msdn.microsoft.com/library/windows/apps/br224693) zurückgibt, um festzustellen, ob die App für Ergebnisse gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-137">If your app can be activated in ways other than launching for results, you can check whether [**IActivatedEventArgs.Kind**](https://msdn.microsoft.com/library/windows/apps/br224728) property returns [**ActivationKind.ProtocolForResults**](https://msdn.microsoft.com/library/windows/apps/br224693) to tell whether the app was launched for results.</span></span>

## <a name="step-3-add-a-protocolforresultsoperation-field-to-the-app-you-launch-for-results"></a><span data-ttu-id="c2cd1-138">Schritt 3: Hinzufügen eines ProtocolForResultsOperation-Felds zur App, die Sie für Ergebnisse starten</span><span class="sxs-lookup"><span data-stu-id="c2cd1-138">Step 3: Add a ProtocolForResultsOperation field to the app you launch for results</span></span>


```cs
private Windows.System.ProtocolForResultsOperation _operation = null;
```

<span data-ttu-id="c2cd1-139">Sie verwenden das [**ProtocolForResultsOperation**](https://msdn.microsoft.com/library/windows/apps/dn906913)-Feld, um zu signalisieren, wenn die gestartete App zur Zurückgabe des Ergebnisses an die aufrufende App bereit ist.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-139">You'll use the [**ProtocolForResultsOperation**](https://msdn.microsoft.com/library/windows/apps/dn906913) field to signal when the launched app is ready to return the result to the calling app.</span></span> <span data-ttu-id="c2cd1-140">In diesem Beispiel wird das Feld der **LaunchedForResultsPage**-Klasse hinzugefügt, da wir den Vorgang zum Starten für Ergebnisse auf dieser Seite durchführen und Zugriff darauf benötigen.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-140">In this example, the field is added to the **LaunchedForResultsPage** class because you'll complete the launch-for-results operation from that page and will need access to it.</span></span>

## <a name="step-4-override-onnavigatedto-in-the-app-you-launch-for-results"></a><span data-ttu-id="c2cd1-141">Schritt 4: Außerkraftsetzen von „Override OnNavigatedTo()“ in der App, die Sie für Ergebnisse starten</span><span class="sxs-lookup"><span data-stu-id="c2cd1-141">Step 4: Override OnNavigatedTo() in the app you launch for results</span></span>


<span data-ttu-id="c2cd1-142">Überschreiben Sie die [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508)-Methode auf der Seite, die Sie anzeigen, wenn die App für Ergebnisse gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-142">Override the [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508) method on the page that you'll display when your app is launched for results.</span></span> <span data-ttu-id="c2cd1-143">Wenn diese Methode in der App noch nicht vorhanden ist, erstellen Sie sie innerhalb der in &lt;Seitenname&gt;.xaml.cs“ definierten Klasse.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-143">If this method does not already exist, create it within the class for the page defined in &lt;pagename&gt;.xaml.cs.</span></span> <span data-ttu-id="c2cd1-144">Stellen Sie sicher, dass die folgende **using**-Anweisung oben in der Datei vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-144">Ensure that the following **using** statement is included at the top of the file:</span></span>

```cs
using Windows.ApplicationModel.Activation
```

<span data-ttu-id="c2cd1-145">Das [**NavigationEventArgs**](https://msdn.microsoft.com/library/windows/apps/br243285)-Objekt in der [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508)-Methode enthält die von der aufrufenden Anwendung übergebenen Daten.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-145">The [**NavigationEventArgs**](https://msdn.microsoft.com/library/windows/apps/br243285) object in the [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508) method contains the data passed from the calling app.</span></span> <span data-ttu-id="c2cd1-146">Die Daten sind auf 100KB begrenzt und werden in einem [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131)-Objekt gespeichert.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-146">The data may not exceed 100KB and is stored in a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) object.</span></span>

<span data-ttu-id="c2cd1-147">Im folgenden Beispielcode erwartet die gestartete App, dass sich die von der aufrufenden Anwendung gesendeten Daten in einem [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) unter einem Schlüssel mit dem Namen **TestData** befinden, da das Startprogramm der Beispiel-App entsprechend codiert ist.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-147">In this example code, the launched app expects the data sent from the calling app to be in a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) under a key named **TestData**, because that's what the example's calling app is coded to send.</span></span>

```cs
using Windows.ApplicationModel.Activation;
...
protected override void OnNavigatedTo(NavigationEventArgs e)
{
    var protocolForResultsArgs = e.Parameter as ProtocolForResultsActivatedEventArgs;
    // Set the ProtocolForResultsOperation field.
    _operation = protocolForResultsArgs.ProtocolForResultsOperation;

    if (protocolForResultsArgs.Data.ContainsKey("TestData"))
    {
        string dataFromCaller = protocolForResultsArgs.Data["TestData"] as string;
    }
}
...
private Windows.System.ProtocolForResultsOperation _operation = null;
```

## <a name="step-5-write-code-to-return-data-to-the-calling-app"></a><span data-ttu-id="c2cd1-148">Schritt 5: Schreiben von Code zum Zurückgeben von Daten an die aufrufende App</span><span class="sxs-lookup"><span data-stu-id="c2cd1-148">Step 5: Write code to return data to the calling app</span></span>


<span data-ttu-id="c2cd1-149">In der für Ergebnisse gestarteten App verwenden Sie [**ProtocolForResultsOperation**](https://msdn.microsoft.com/library/windows/apps/dn906913), um Daten an die aufrufende App zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-149">In the launched app, use [**ProtocolForResultsOperation**](https://msdn.microsoft.com/library/windows/apps/dn906913) to return data to the calling app.</span></span> <span data-ttu-id="c2cd1-150">Im folgenden Beispielcode wird ein [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131)-Objekt erstellt, das den Wert enthält, der an die aufrufende App zurückgegeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-150">In this example code, a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) object is created that contains the value to return to the calling app.</span></span> <span data-ttu-id="c2cd1-151">Anschließend wird das **ProtocolForResultsOperation**-Feld verwendet, um den Wert an die aufrufende App zu senden.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-151">The **ProtocolForResultsOperation** field is then used to send the value to the calling app.</span></span>

```cs
    ValueSet result = new ValueSet();
    result["ReturnedData"] = "The returned result";
    _operation.ReportCompleted(result);
```

## <a name="step-6-write-code-to-launch-the-app-for-results-and-get-the-returned-data"></a><span data-ttu-id="c2cd1-152">Schritt 6: Schreiben von Code zum Starten der App für Ergebnisse und zum Abrufen der zurückgegebenen Daten</span><span class="sxs-lookup"><span data-stu-id="c2cd1-152">Step 6: Write code to launch the app for results and get the returned data</span></span>


<span data-ttu-id="c2cd1-153">Starten Sie die App aus einer asynchronen Methode in der aufrufenden App, wie in diesem Beispielcode dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-153">Launch the app from within an async method in your calling app as shown in this example code.</span></span> <span data-ttu-id="c2cd1-154">Beachten Sie die **using**-Anweisungen, die zum Kompilieren des Codes erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-154">Note the **using** statements, which are necessary for the code to compile:</span></span>

```cs
using System.Threading.Tasks;
using Windows.System;
...

async Task<string> LaunchAppForResults()
{
    var testAppUri = new Uri("test-app2app:"); // The protocol handled by the launched app
    var options = new LauncherOptions();
    options.TargetApplicationPackageFamilyName = "67d987e1-e842-4229-9f7c-98cf13b5da45_yd7nk54bq29ra";

    var inputData = new ValueSet();
    inputData["TestData"] = "Test data";

    string theResult = "";
    LaunchUriResult result = await Windows.System.Launcher.LaunchUriForResultsAsync(testAppUri, options, inputData);
    if (result.Status == LaunchUriStatus.Success &&
        result.Result != null &&
        result.Result.ContainsKey("ReturnedData"))
    {
        ValueSet theValues = result.Result;
        theResult = theValues["ReturnedData"] as string;
    }
    return theResult;
}
```

<span data-ttu-id="c2cd1-155">In diesem Beispiel wird ein [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) mit dem Schlüssel **TestData** an die gestartete App übergeben.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-155">In this example, a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) containing the key **TestData** is passed to the launched app.</span></span> <span data-ttu-id="c2cd1-156">Die gestartete App erstellt einen **ValueSet** mit einem Schlüssel mit dem Namen **ReturnedData**, der das Ergebnis enthält, das an den Aufrufer zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-156">The launched app creates a **ValueSet** with a key named **ReturnedData** that contains the result returned to the caller.</span></span>

<span data-ttu-id="c2cd1-157">Sie müssen die App, die Sie für Ergebnisse starten, erstellen und bereitstellen, bevor Sie die aufrufende App ausführen können.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-157">You must build and deploy the app that you'll launch for results before running your calling app.</span></span> <span data-ttu-id="c2cd1-158">Andernfalls wird von [**LaunchUriResult.Status**](https://msdn.microsoft.com/library/windows/apps/dn906892) der Status **LaunchUriStatus.AppUnavailable** gemeldet.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-158">Otherwise, [**LaunchUriResult.Status**](https://msdn.microsoft.com/library/windows/apps/dn906892) will report **LaunchUriStatus.AppUnavailable**.</span></span>

<span data-ttu-id="c2cd1-159">Sie benötigen den Familiennamen der gestarteten App beim Festlegen von [**TargetApplicationPackageFamilyName**](https://msdn.microsoft.com/library/windows/apps/dn893511).</span><span class="sxs-lookup"><span data-stu-id="c2cd1-159">You'll need the family name of the launched app when you set the [**TargetApplicationPackageFamilyName**](https://msdn.microsoft.com/library/windows/apps/dn893511).</span></span> <span data-ttu-id="c2cd1-160">Eine Möglichkeit, den Familiennamen abzurufen besteht darin, folgenden Aufruf in der gestarteten App auszuführen:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-160">One way to get the family name is to make the following call from within the launched app:</span></span>

```cs
string familyName = Windows.ApplicationModel.Package.Current.Id.FamilyName;
```

## <a name="remarks"></a><span data-ttu-id="c2cd1-161">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="c2cd1-161">Remarks</span></span>


<span data-ttu-id="c2cd1-162">Das Beispiel in dieser Anleitung bietet eine Einführung in das Starten einer App für Ergebnisse anhand von „Hello World“.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-162">The example in this how-to provides a "hello world" introduction to launching an app for results.</span></span> <span data-ttu-id="c2cd1-163">Als wichtigster Punkt ist zu beachten, dass die neue [**LaunchUriForResultsAsync**](https://msdn.microsoft.com/library/windows/apps/dn956686)-API Ihnen das asynchrone Starten einer App und die Kommunikation über die [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131)-Klasse ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-163">The key things to note are that the new [**LaunchUriForResultsAsync**](https://msdn.microsoft.com/library/windows/apps/dn956686) API lets you asynchronously launch an app and communicate via the [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) class.</span></span> <span data-ttu-id="c2cd1-164">Das Übergeben von Daten über einen **ValueSet** ist auf 100KB begrenzt.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-164">Passing data via a **ValueSet** is limited to 100KB.</span></span> <span data-ttu-id="c2cd1-165">Wenn Sie größere Datenmengen übergeben müssen, können Sie Dateien mithilfe der [**SharedStorageAccessManager**](https://msdn.microsoft.com/library/windows/apps/dn889985)-Klasse freigeben, um Dateitoken zu erstellen, die zwischen Apps ausgetauscht werden können.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-165">If you need to pass larger amounts of data, you can share files by using the [**SharedStorageAccessManager**](https://msdn.microsoft.com/library/windows/apps/dn889985) class to create file tokens that you can pass between apps.</span></span> <span data-ttu-id="c2cd1-166">Wenn Sie beispielsweise über **ValueSet** mit dem Namen `inputData` verfügen, könnten Sie das Token in einer Datei speichern, die Sie für die gestartete App freigeben möchten:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-166">For example, given a **ValueSet** named `inputData`, you could store the token to a file that you want to share with the launched app:</span></span>

```cs
inputData["ImageFileToken"] = SharedStorageAccessManager.AddFile(myFile);
```

<span data-ttu-id="c2cd1-167">Anschließend übergeben Sie sie über **LaunchUriForResultsAsync** an die gestartete App.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-167">Then pass it to the launched app via **LaunchUriForResultsAsync**.</span></span>

## <a name="related-topics"></a><span data-ttu-id="c2cd1-168">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c2cd1-168">Related topics</span></span>


* [**<span data-ttu-id="c2cd1-169">LaunchUri</span><span class="sxs-lookup"><span data-stu-id="c2cd1-169">LaunchUri</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701476)
* [**<span data-ttu-id="c2cd1-170">LaunchUriForResultsAsync</span><span class="sxs-lookup"><span data-stu-id="c2cd1-170">LaunchUriForResultsAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn956686)
* [**<span data-ttu-id="c2cd1-171">ValueSet</span><span class="sxs-lookup"><span data-stu-id="c2cd1-171">ValueSet</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn636131)

 

 
