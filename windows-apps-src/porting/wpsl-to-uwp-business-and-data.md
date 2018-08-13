---
author: mcleblanc
description: Im Hintergrund Ihrer Benutzeroberfläche befinden sich Ihre Geschäfts- und Datenebenen.
title: Portieren von Windows Phone Silverlight-Geschäfts- und -Datenebenen zu UWP
ms.assetid: 27c66759-2b35-41f5-9f7a-ceb97f4a0e3f
ms.author: markl
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 860b42ca05c95768ca694d13971da278e2129142
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "234901"
---
#  <a name="porting-windows-phone-silverlight-business-and-data-layers-to-uwp"></a><span data-ttu-id="12116-104">Portieren von Windows Phone Silverlight-Geschäfts- und -Datenebenen zu UWP</span><span class="sxs-lookup"><span data-stu-id="12116-104">Porting Windows Phone Silverlight business and data layers to UWP</span></span>

<span data-ttu-id="12116-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="12116-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="12116-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="12116-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="12116-107">Das vorherige Thema war [Portieren: E/A, Gerät und App-Modell](wpsl-to-uwp-input-and-sensors.md).</span><span class="sxs-lookup"><span data-stu-id="12116-107">The previous topic was [Porting for I/O, device, and app model](wpsl-to-uwp-input-and-sensors.md).</span></span>

<span data-ttu-id="12116-108">Im Hintergrund Ihrer UI befinden sich Ihre Geschäfts- und Datenebenen.</span><span class="sxs-lookup"><span data-stu-id="12116-108">Behind your UI are your business and data layers.</span></span> <span data-ttu-id="12116-109">Der Code auf diesen Ebenen ruft Betriebssystem- und .NETFramework-APIs auf (z.B. Hintergrundverarbeitung, Position, Kamera, Dateisystem, Netzwerk und andere Datenzugriffsfunktionen).</span><span class="sxs-lookup"><span data-stu-id="12116-109">The code in these layers calls operating system and .NET Framework APIs (for example, background processing, location, the camera, the file system, network, and other data access).</span></span> <span data-ttu-id="12116-110">Die meisten dieser APIs sind [für eine UWP (Universelle Windows-Plattform)-App verfügbar](https://msdn.microsoft.com/library/windows/apps/br211369). Sie können also davon ausgehen, dass sich ein Großteil dieses Codes ohne Änderungen portieren lässt.</span><span class="sxs-lookup"><span data-stu-id="12116-110">The vast majority of those are [available to a Universal Windows Platform (UWP) app](https://msdn.microsoft.com/library/windows/apps/br211369), so you can expect to be able to port much of this code without change.</span></span>

## <a name="asynchronous-methods"></a><span data-ttu-id="12116-111">Asynchrone Methoden</span><span class="sxs-lookup"><span data-stu-id="12116-111">Asynchronous methods</span></span>

<span data-ttu-id="12116-112">Einer der Hauptvorteile der universellen Windows-Plattform (UWP) besteht darin, das sie Ihnen die Erstellung von Apps ermöglicht, die wirklich und durchgehend reaktionsfähig sind.</span><span class="sxs-lookup"><span data-stu-id="12116-112">One of the priorities of the Universal Windows Platform (UWP) is to enable you to build apps that are truly, and consistently, responsive.</span></span> <span data-ttu-id="12116-113">Animationen sind immer reibungslos, und Touchinteraktionen wie Verschieben und Wischen erfolgen sofort und ohne Verzögerung, wodurch der Eindruck entsteht, dass die UI quasi an Ihrem Finger „klebt“.</span><span class="sxs-lookup"><span data-stu-id="12116-113">Animations are always smooth, and touch interactions such as panning and swiping are instantaneous and free of lag, making it feel like the UI is glued to your finger.</span></span> <span data-ttu-id="12116-114">Um dies zu erreichen, wurden alle UWP-APIs, deren Ausführung innerhalb von 50Millisekunden nicht garantiert werden kann, als asynchron konzipiert und mit dem Namenssuffix **Async** versehen.</span><span class="sxs-lookup"><span data-stu-id="12116-114">To achieve this, any UWP API that can't guarantee to complete within 50ms has been made asynchronous and its name suffixed with **Async**.</span></span> <span data-ttu-id="12116-115">Die Rückgabe Ihres UI-Threads nach dem Aufruf einer **Async**-Methode erfolgt sofort, und die Arbeit wird in einem anderen Thread ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="12116-115">Your UI thread will return immediately from calling an **Async** method, and the work will take place on another thread.</span></span> <span data-ttu-id="12116-116">Die Nutzung einer **Async**-Methode ist in Bezug auf die Syntax mit dem C#-Operator **await**, JavaScript-Promise-Objekten und C++-Fortsetzungen sehr einfach.</span><span class="sxs-lookup"><span data-stu-id="12116-116">Consuming an **Async** method is made very easy, syntactically, using the C# **await** operator, JavaScript promise objects, and C++ continuations.</span></span> <span data-ttu-id="12116-117">Weitere Informationen finden Sie unter [Asynchrone Programmierung](https://msdn.microsoft.com/library/windows/apps/mt187335).</span><span class="sxs-lookup"><span data-stu-id="12116-117">For more info, see [Asynchronous programming](https://msdn.microsoft.com/library/windows/apps/mt187335).</span></span>

## <a name="background-processing"></a><span data-ttu-id="12116-118">Hintergrundverarbeitung</span><span class="sxs-lookup"><span data-stu-id="12116-118">Background processing</span></span>

<span data-ttu-id="12116-119">Eine WindowsPhone Silverlight-App kann ein verwaltetes **ScheduledTaskAgent**-Objekt verwenden, um eine Aufgabe auszuführen, während sich die App nicht im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="12116-119">A Windows Phone Silverlight app can use a managed **ScheduledTaskAgent** object to perform a task while the app is not in the foreground.</span></span> <span data-ttu-id="12116-120">UWP-Apps verwenden auf ähnliche Weise die [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)-Klasse zum Erstellen und Registrieren von Hintergrundaufgaben.</span><span class="sxs-lookup"><span data-stu-id="12116-120">A UWP app uses the [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) class to create and register a background task in a similar way.</span></span> <span data-ttu-id="12116-121">Sie definieren eine Klasse, die die Arbeit Ihrer Hintergrundaufgabe implementiert.</span><span class="sxs-lookup"><span data-stu-id="12116-121">You define a class that implements the work of your background task.</span></span> <span data-ttu-id="12116-122">Das System führt die Hintergrundaufgabe regelmäßig aus, indem die [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811)-Methode der Klasse zum Ausführen der Arbeit aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="12116-122">The system runs your background task periodically, calling the [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811) method of your class to execute the work.</span></span> <span data-ttu-id="12116-123">Denken Sie bei einer UWP-App daran, die Deklaration **Hintergrundaufgaben** im App-Paketmanifest festzulegen.</span><span class="sxs-lookup"><span data-stu-id="12116-123">In a UWP app, remember to set the **Background Tasks** declaration in the app package manifest.</span></span> <span data-ttu-id="12116-124">Weitere Informationen finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](https://msdn.microsoft.com/library/windows/apps/mt299103).</span><span class="sxs-lookup"><span data-stu-id="12116-124">For more info, see [Support your app with background tasks](https://msdn.microsoft.com/library/windows/apps/mt299103).</span></span>

<span data-ttu-id="12116-125">Um große Datendateien im Hintergrund zu übertragen, verwendet eine WindowsPhone Silverlight-App die **BackgroundTransferService**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="12116-125">To transfer large data files in the background, a Windows Phone Silverlight app uses the **BackgroundTransferService** class.</span></span> <span data-ttu-id="12116-126">Eine UWP-App verwendet zu diesem Zweck APIs im [**Windows.Networking.BackgroundTransfer**](https://msdn.microsoft.com/library/windows/apps/br207242)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="12116-126">A UWP app uses APIs in the [**Windows.Networking.BackgroundTransfer**](https://msdn.microsoft.com/library/windows/apps/br207242) namespace to do this.</span></span> <span data-ttu-id="12116-127">Die Features initiieren Übertragungen anhand eines ähnlichen Musters, die neue API verfügt aber über verbesserte Funktionen und eine höhere Leistung.</span><span class="sxs-lookup"><span data-stu-id="12116-127">The features use a similar pattern to initiate transfers, but the new API has improved capabilities and performance.</span></span> <span data-ttu-id="12116-128">Weitere Informationen finden Sie unter [Übertragen von Daten im Hintergrund](https://msdn.microsoft.com/library/windows/apps/xaml/hh452975).</span><span class="sxs-lookup"><span data-stu-id="12116-128">For more info, see [Transferring data in the background](https://msdn.microsoft.com/library/windows/apps/xaml/hh452975).</span></span>

<span data-ttu-id="12116-129">Eine WindowsPhone Silverlight-App verwendet die verwalteten Klassen im **Microsoft.Phone.BackgroundAudio**-Namespace zum Wiedergeben von Audio, während sich die App nicht im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="12116-129">A Windows Phone Silverlight app uses the managed classes in the **Microsoft.Phone.BackgroundAudio** namespace to play audio while the app is not in the foreground.</span></span> <span data-ttu-id="12116-130">Die UWP verwendet das Windows Phone Store-App-Modell. Weitere Informationen finden Sie unter [Hintergrundaudio](https://msdn.microsoft.com/library/windows/apps/mt282140) und im [Hintergrundaudio](http://go.microsoft.com/fwlink/p/?linkid=619997)-Beispiel.</span><span class="sxs-lookup"><span data-stu-id="12116-130">The UWP uses the Windows Phone Store app model, see [Background Audio](https://msdn.microsoft.com/library/windows/apps/mt282140) and the [Background audio](http://go.microsoft.com/fwlink/p/?linkid=619997) sample.</span></span>

## <a name="cloud-services-networking-and-databases"></a><span data-ttu-id="12116-131">Clouddienste, Netzwerk und Datenbanken</span><span class="sxs-lookup"><span data-stu-id="12116-131">Cloud services, networking, and databases</span></span>

<span data-ttu-id="12116-132">Das Hosten von Daten und App-Diensten in der Cloud ist mit Azure möglich.</span><span class="sxs-lookup"><span data-stu-id="12116-132">Hosting data and app services in the cloud is possible using Azure.</span></span> <span data-ttu-id="12116-133">Weitere Informationen finden Sie unter [Erste Schritte mit Mobile Services](http://go.microsoft.com/fwlink/p/?LinkID=403138).</span><span class="sxs-lookup"><span data-stu-id="12116-133">See [Getting Started with Mobile Services](http://go.microsoft.com/fwlink/p/?LinkID=403138).</span></span> <span data-ttu-id="12116-134">Für Lösungen, die sowohl Online- als auch Offlinedaten erfordern: [Verwendung der Offlinedatensynchronisierung in Mobile Services](http://azure.microsoft.com/documentation/articles/mobile-services-windows-store-dotnet-get-started-offline-data/).</span><span class="sxs-lookup"><span data-stu-id="12116-134">For solutions that require both online and offline data see: [Using offline data sync in Mobile Services](http://azure.microsoft.com/documentation/articles/mobile-services-windows-store-dotnet-get-started-offline-data/).</span></span>

<span data-ttu-id="12116-135">Die UWP verfügt über eine Teilunterstützung für die **System.Net.HttpWebRequest**-Klasse, aber die **System.Net.WebClient**-Klasse wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="12116-135">The UWP has partial support for the **System.Net.HttpWebRequest** class, but the **System.Net.WebClient** class is not supported.</span></span> <span data-ttu-id="12116-136">Die empfohlene modernere Alternative ist die [**Windows.Web.Http.HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639)-Klasse (oder [System.Net.Http.HttpClient](https://msdn.microsoft.com/library/system.net.http.httpclient(v=vs.118).aspx), wenn Ihr Code auf andere Plattformen mit .NET-Unterstützung portierbar sein soll).</span><span class="sxs-lookup"><span data-stu-id="12116-136">The recommended, forward-looking alternative is the [**Windows.Web.Http.HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) class (or [System.Net.Http.HttpClient](https://msdn.microsoft.com/library/system.net.http.httpclient(v=vs.118).aspx) if you need your code to be portable to other platforms that support .NET).</span></span> <span data-ttu-id="12116-137">Für diese APIs wird [System.Net.Http.HttpRequestMessage](https://msdn.microsoft.com/library/system.net.http.httprequestmessage.aspx) verwendet, um eine HTTP-Anforderung darzustellen.</span><span class="sxs-lookup"><span data-stu-id="12116-137">These APIs use [System.Net.Http.HttpRequestMessage](https://msdn.microsoft.com/library/system.net.http.httprequestmessage.aspx) to represent an HTTP request.</span></span>

<span data-ttu-id="12116-138">UWP-Apps bieten zurzeit keine integrierte Unterstützung für datenintensive Szenarien wie beispielsweise Branchenszenarien.</span><span class="sxs-lookup"><span data-stu-id="12116-138">UWP apps do not currently include built-in support for data-intensive scenarios such as line of business (LOB) scenarios.</span></span> <span data-ttu-id="12116-139">Sie können jedoch SQLite für lokale Transaktionsdatenbankdienste verwenden.</span><span class="sxs-lookup"><span data-stu-id="12116-139">However, you can make use SQLite for local transactional database services.</span></span> <span data-ttu-id="12116-140">Weitere Informationen finden Sie unter [SQLite](https://visualstudiogallery.msdn.microsoft.com/4913e7d5-96c9-4dde-a1a1-69820d615936).</span><span class="sxs-lookup"><span data-stu-id="12116-140">For more info, see [SQLite](https://visualstudiogallery.msdn.microsoft.com/4913e7d5-96c9-4dde-a1a1-69820d615936).</span></span>

<span data-ttu-id="12116-141">Übergeben Sie absolute URIs, keine relativen URIs, an Windows-Runtime-Typen.</span><span class="sxs-lookup"><span data-stu-id="12116-141">Pass absolute URIs, not relative URIs, to Windows Runtime types.</span></span> <span data-ttu-id="12116-142">Weitere Informationen finden Sie unter [Übergeben eines URI an die Windows-Runtime](https://msdn.microsoft.com/library/hh763341.aspx).</span><span class="sxs-lookup"><span data-stu-id="12116-142">See [Passing a URI to the Windows Runtime](https://msdn.microsoft.com/library/hh763341.aspx).</span></span>

## <a name="launchers-and-choosers"></a><span data-ttu-id="12116-143">Launcher und Chooser</span><span class="sxs-lookup"><span data-stu-id="12116-143">Launchers and Choosers</span></span>

<span data-ttu-id="12116-144">Mit Launchern und Choosern (im **Microsoft.Phone.Tasks**-Namespace) kann eine WindowsPhone Silverlight-App mit dem Betriebssystem interagieren, um allgemeine Vorgänge auszuführen (z.B. Erstellen einer E-Mail, Auswählen eines Fotos oder Teilen bestimmter Arten von Daten mit einer anderen App).</span><span class="sxs-lookup"><span data-stu-id="12116-144">With Launchers and Choosers (found in the **Microsoft.Phone.Tasks** namespace), a Windows Phone Silverlight app can interact with the operating system to perform common operations such as composing an email, choosing a photo, or sharing certain kinds of data with another app.</span></span> <span data-ttu-id="12116-145">Den entsprechenden UWP-Typ finden Sie unter **Microsoft.Phone.Tasks** im Thema [Windows Phone Silverlight zu Windows10: Namespace- und Klassenzuordnungen](wpsl-to-uwp-namespace-and-class-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="12116-145">Search for **Microsoft.Phone.Tasks** in the topic [Windows Phone Silverlight to Windows 10 namespace and class mappings](wpsl-to-uwp-namespace-and-class-mappings.md) to find the equivalent UWP type.</span></span> <span data-ttu-id="12116-146">Diese reichen von ähnlichen Mechanismen (so genannten Launchern und Pickern) bis zur Implementierung eines Vertrags zum Teilen von Daten zwischen Apps.</span><span class="sxs-lookup"><span data-stu-id="12116-146">These range from similar mechanisms, called launchers and pickers, to implementing a contract for sharing data between apps.</span></span>

<span data-ttu-id="12116-147">Wenn z. B. die Fotoauswahlaufgabe verwendet wird, kann eine Windows Phone Silverlight-App in einen Ruhezustand versetzt oder sogar als veraltet markiert werden.</span><span class="sxs-lookup"><span data-stu-id="12116-147">A Windows Phone Silverlight app can be put into a dormant state or even tombstoned when using, for example, the photo Chooser task.</span></span> <span data-ttu-id="12116-148">Eine UWP-App bleibt aktiv und wird weiter ausgeführt, wenn die [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847)-Klasse verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="12116-148">A UWP app remains active and running while using the [**FileOpenPicker**](https://msdn.microsoft.com/library/windows/apps/br207847) class.</span></span>

## <a name="monetization-trial-mode-and-in-app-purchases"></a><span data-ttu-id="12116-149">Monetisierung (Testmodus und In-App-Einkäufe)</span><span class="sxs-lookup"><span data-stu-id="12116-149">Monetization (trial mode and in-app purchases)</span></span>

<span data-ttu-id="12116-150">Für den Großteil der Funktionen, die im Testmodus und für In-App-Einkäufe verwendet werden, kann eine WindowsPhone Silverlight-App die UWP [**CurrentApp**](https://msdn.microsoft.com/library/windows/apps/hh779765)-Klasse verwenden. Daher muss kein Code portiert werden.</span><span class="sxs-lookup"><span data-stu-id="12116-150">A Windows Phone Silverlight app can use the UWP [**CurrentApp**](https://msdn.microsoft.com/library/windows/apps/hh779765) class for most of its trial mode and in-app purchase functionality, so that code doesn't need to be ported.</span></span> <span data-ttu-id="12116-151">Eine WindowsPhone Silverlight-App ruft jedoch **MarketplaceDetailTask.Show** auf, um die App zum Kauf anzubieten:</span><span class="sxs-lookup"><span data-stu-id="12116-151">But, a Windows Phone Silverlight app calls **MarketplaceDetailTask.Show** to offer the app for purchase:</span></span>

```csharp
    private void Buy()
    {
        MarketplaceDetailTask marketplaceDetailTask = new MarketplaceDetailTask();
        marketplaceDetailTask.ContentType = MarketplaceContentType.Applications;
        marketplaceDetailTask.Show();
    }
```

<span data-ttu-id="12116-152">Portieren Sie diesen Code zum Aufrufen der UWP [**RequestAppPurchaseAsync**](https://msdn.microsoft.com/library/windows/apps/hh967813)-Methode:</span><span class="sxs-lookup"><span data-stu-id="12116-152">Port that code to call the UWP [**RequestAppPurchaseAsync**](https://msdn.microsoft.com/library/windows/apps/hh967813) method:</span></span>

```csharp
    private async void Buy()
    {
        await Windows.ApplicationModel.Store.CurrentApp.RequestAppPurchaseAsync(false);
    }
```

<span data-ttu-id="12116-153">Falls Sie über Code verfügen, der Ihre Features für App-Kauf und In-App-Einkäufe zu Testzwecken simuliert, können Sie ihn portieren, um stattdessen die [**CurrentAppSimulator**](https://msdn.microsoft.com/library/windows/apps/hh779766)-Klasse zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="12116-153">If you have code that simulates your app purchase and in-app purchase features for testing purposes, then you can port that to use the [**CurrentAppSimulator**](https://msdn.microsoft.com/library/windows/apps/hh779766) class instead.</span></span>

## <a name="notifications-for-tile-or-toast-updates"></a><span data-ttu-id="12116-154">Benachrichtigungen für Kachel- oder Popupaktualisierungen</span><span class="sxs-lookup"><span data-stu-id="12116-154">Notifications for tile or toast updates</span></span>

<span data-ttu-id="12116-155">Benachrichtigungen sind eine Erweiterung des Pushbenachrichtigungsmodells für Windows Phone Silverlight-Apps.</span><span class="sxs-lookup"><span data-stu-id="12116-155">Notifications are an extension of the push notification model for Windows Phone Silverlight apps.</span></span> <span data-ttu-id="12116-156">Wenn Sie eine Benachrichtigung vom Windows-Pushbenachrichtigungsdienst (WNS) empfangen, können Sie die Informationen mit einer Kachelaktualisierung oder einem Popup in der Benutzeroberfläche anzeigen.</span><span class="sxs-lookup"><span data-stu-id="12116-156">When you receive a notification from the Windows Push Notification Service (WNS), you can surface the info to the UI with a tile update or with a toast.</span></span> <span data-ttu-id="12116-157">Informationen zum Portieren des Benutzeroberflächenteils Ihrer Benachrichtigungsfeatures finden Sie unter [Kacheln und Popups](w8x-to-uwp-porting-xaml-and-ui.md).</span><span class="sxs-lookup"><span data-stu-id="12116-157">For porting the UI side of your notification features, see [Tiles and toasts](w8x-to-uwp-porting-xaml-and-ui.md).</span></span>

<span data-ttu-id="12116-158">Ausführlichere Informationen zur Verwendung von Benachrichtigungen in UWP-Apps finden Sie unter [Senden von Popupbenachrichtigungen](https://msdn.microsoft.com/library/windows/apps/xaml/hh868266).</span><span class="sxs-lookup"><span data-stu-id="12116-158">For more details on the use of notifications in a UWP app, see [Sending toast notifications](https://msdn.microsoft.com/library/windows/apps/xaml/hh868266).</span></span>

<span data-ttu-id="12116-159">Informationen und Lernprogramme zur Verwendung von Kacheln, Popups, Signalen, Bannern und Benachrichtigungen in einer Windows-Runtime-App mit C++, C# oder Visual Basic finden Sie unter [Verwenden von Kacheln, Signalen und Popupbenachrichtigungen](https://msdn.microsoft.com/library/windows/apps/xaml/hh868259).</span><span class="sxs-lookup"><span data-stu-id="12116-159">For info and tutorials on using tiles, toasts, badges, banners, and notifications in a Windows Runtime app using C++, C#, or Visual Basic, see [Working with tiles, badges, and toast notifications](https://msdn.microsoft.com/library/windows/apps/xaml/hh868259).</span></span>

## <a name="storage-file-access"></a><span data-ttu-id="12116-160">Speicher (Dateizugriff)</span><span class="sxs-lookup"><span data-stu-id="12116-160">Storage (file access)</span></span>

<span data-ttu-id="12116-161">Windows Phone Silverlight-Code, der App-Einstellungen als Schlüssel-Wert-Paare in isoliertem Speicher speichert, kann problemlos portiert werden.</span><span class="sxs-lookup"><span data-stu-id="12116-161">Windows Phone Silverlight code that stores app settings as key-value pairs in isolated storage is easily ported.</span></span> <span data-ttu-id="12116-162">Hier sehen Sie ein Vorher-Nachher-Beispiel, und zwar zuerst die Windows Phone Silverlight-Version:</span><span class="sxs-lookup"><span data-stu-id="12116-162">Here is a before-and-after example, first the Windows Phone Silverlight version:</span></span>

```csharp
    var propertySet = IsolatedStorageSettings.ApplicationSettings;
    const string key = "favoriteAuthor";
    propertySet[key] = "Charles Dickens";
    propertySet.Save();
    string myFavoriteAuthor = propertySet.Contains(key) ? (string)propertySet[key] : "<none>";
```

<span data-ttu-id="12116-163">Und hier die UWP-Entsprechung:</span><span class="sxs-lookup"><span data-stu-id="12116-163">And the UWP equivalent:</span></span>

```csharp
    var propertySet = Windows.Storage.ApplicationData.Current.LocalSettings.Values;
    const string key = "favoriteAuthor";
    propertySet[key] = "Charles Dickens";
    string myFavoriteAuthor = propertySet.ContainsKey(key) ? (string)propertySet[key] : "<none>";
```

<span data-ttu-id="12116-164">Obwohl eine Teilmenge des **Windows.Storage**-Namespaces für sie verfügbar ist, führen viele WindowsPhone Silverlight-Apps E/A-Dateivorgänge mit der **IsolatedStorageFile**-Klasse aus, da diese schon länger unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="12116-164">Although a subset of the **Windows.Storage** namespace is available to them, many Windows Phone Silverlight apps perform file i/o with the **IsolatedStorageFile** class because it has been supported for longer.</span></span> <span data-ttu-id="12116-165">Hier sehen Sie ein Vorher-Nachher-Beispiel für das Schreiben und Lesen einer Datei unter Verwendung von **IsolatedStorageFile**, und zwar zuerst die WindowsPhone Silverlight-Version:</span><span class="sxs-lookup"><span data-stu-id="12116-165">Assuming that **IsolatedStorageFile** is being used, here's a before-and-after example of writing and reading a file, first the Windows Phone Silverlight version:</span></span>

```csharp
    const string filename = "FavoriteAuthor.txt";
    using (var store = IsolatedStorageFile.GetUserStoreForApplication())
    {
        using (var streamWriter = new StreamWriter(store.CreateFile(filename)))
        {
            streamWriter.Write("Charles Dickens");
        }
        using (var StreamReader = new StreamReader(store.OpenFile(filename, FileMode.Open, FileAccess.Read)))
        {
            string myFavoriteAuthor = StreamReader.ReadToEnd();
        }
    }
```

<span data-ttu-id="12116-166">Und hier die gleiche Funktionalität mit der UWP:</span><span class="sxs-lookup"><span data-stu-id="12116-166">And the same functionality using the UWP:</span></span>

```csharp
    const string filename = "FavoriteAuthor.txt";
    var store = Windows.Storage.ApplicationData.Current.LocalFolder;
    Windows.Storage.StorageFile file = await store.CreateFileAsync(filename, Windows.Storage.CreationCollisionOption.ReplaceExisting);
    await Windows.Storage.FileIO.WriteTextAsync(file, "Charles Dickens");
    file = await store.GetFileAsync(filename);
    string myFavoriteAuthor = await Windows.Storage.FileIO.ReadTextAsync(file);
```

<span data-ttu-id="12116-167">Eine Windows Phone Silverlight-App hat schreibgeschützten Zugriff auf die optionale SD-Karte.</span><span class="sxs-lookup"><span data-stu-id="12116-167">A Windows Phone Silverlight app has read-only access to the optional SD card.</span></span> <span data-ttu-id="12116-168">Eine UWP-App hat Lese-/Schreibzugriff auf die SD-Karte.</span><span class="sxs-lookup"><span data-stu-id="12116-168">A UWP app has read-write access to the SD card.</span></span> <span data-ttu-id="12116-169">Weitere Informationen finden Sie unter [Zugreifen auf die SD-Karte](https://msdn.microsoft.com/library/windows/apps/mt188699).</span><span class="sxs-lookup"><span data-stu-id="12116-169">For more info, see [Access the SD card](https://msdn.microsoft.com/library/windows/apps/mt188699).</span></span>

<span data-ttu-id="12116-170">Informationen zum Zugriff auf Fotos, Musik und Videodateien in einer UWP-App finden Sie unter [Dateien und Ordner in den Musik-, Bild- und Videobibliotheken](https://msdn.microsoft.com/library/windows/apps/mt188703).</span><span class="sxs-lookup"><span data-stu-id="12116-170">For info about accessing photos, music, and video files in a UWP app, see [Files and folders in the Music, Pictures, and Videos libraries](https://msdn.microsoft.com/library/windows/apps/mt188703).</span></span>

<span data-ttu-id="12116-171">Weitere Informationen finden Sie unter [Dateien, Ordner und Bibliotheken](https://msdn.microsoft.com/library/windows/apps/mt185399).</span><span class="sxs-lookup"><span data-stu-id="12116-171">For more info, see [Files, folders, and libraries](https://msdn.microsoft.com/library/windows/apps/mt185399).</span></span>

<span data-ttu-id="12116-172">Das nächste Thema ist [Portieren für Formfaktor und Benutzerfreundlichkeit](wpsl-to-uwp-form-factors-and-ux.md).</span><span class="sxs-lookup"><span data-stu-id="12116-172">The next topic is [Porting for form factor and UX](wpsl-to-uwp-form-factors-and-ux.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="12116-173">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="12116-173">Related topics</span></span>

* [<span data-ttu-id="12116-174">Namespace- und Klassenzuordnungen</span><span class="sxs-lookup"><span data-stu-id="12116-174">Namespace and class mappings</span></span>](wpsl-to-uwp-namespace-and-class-mappings.md)
 

