---
author: stevewhims
description: Mithilfe von Fremdanbieterfeeds, die entsprechend den RSS- und Atom-Standards mit Features im Windows.Web.Syndication-Namespace generiert werden, können Sie die neuesten und beliebtesten Webinhalte abrufen oder erstellen.
title: RSS-/Atom-Feeds
ms.assetid: B196E19B-4610-4EFA-8FDF-AF9B10D78843
ms.author: stwhi
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 309dd2aedb2195362652da93c13648d07e5ea9f8
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "6452871"
---
# <a name="rssatom-feeds"></a><span data-ttu-id="95e8d-104">RSS-/Atom-Feeds</span><span class="sxs-lookup"><span data-stu-id="95e8d-104">RSS/Atom feeds</span></span>


**<span data-ttu-id="95e8d-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="95e8d-105">Important APIs</span></span>**

-   [**<span data-ttu-id="95e8d-106">Windows.Data.Xml.Dom</span><span class="sxs-lookup"><span data-stu-id="95e8d-106">Windows.Data.Xml.Dom</span></span>**](https://msdn.microsoft.com/library/windows/apps/br240819)
-   [**<span data-ttu-id="95e8d-107">Windows.Web.AtomPub</span><span class="sxs-lookup"><span data-stu-id="95e8d-107">Windows.Web.AtomPub</span></span>**](https://msdn.microsoft.com/library/windows/apps/br210609)
-   [**<span data-ttu-id="95e8d-108">Windows.Web.Syndication</span><span class="sxs-lookup"><span data-stu-id="95e8d-108">Windows.Web.Syndication</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243632)

<span data-ttu-id="95e8d-109">Mithilfe von Fremdanbieterfeeds, die entsprechend den RSS- und Atom-Standards mit Features im [**Windows.Web.Syndication**](https://msdn.microsoft.com/library/windows/apps/br243632)-Namespace generiert werden, können Sie die aktuellsten und beliebtesten Webinhalte abrufen oder erstellen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-109">Retrieve or create the most current and popular Web content using syndicated feeds generated according to the RSS and Atom standards using features in the [**Windows.Web.Syndication**](https://msdn.microsoft.com/library/windows/apps/br243632) namespace.</span></span>

## <a name="what-is-a-feed"></a><span data-ttu-id="95e8d-110">Was ist ein Feed?</span><span class="sxs-lookup"><span data-stu-id="95e8d-110">What is a feed?</span></span>

<span data-ttu-id="95e8d-111">Ein Webfeed ist ein Dokument, das eine Reihe von Einzeleinträgen enthält, die sich aus Text, Links und Bildern zusammensetzen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-111">A web feed is a document that contains any number of individual entries made up of text, links, and images.</span></span> <span data-ttu-id="95e8d-112">Aktualisierungen von Feeds werden in Form neuer Einträge vorgenommen, mit denen aktuelle Inhalte im Web verbreitet werden.</span><span class="sxs-lookup"><span data-stu-id="95e8d-112">Updates made to a feed are in the form of new entries used to promote the latest content across the Web.</span></span> <span data-ttu-id="95e8d-113">Nutzer von Inhalten können mithilfe einer Feedleser-App Feeds einer beliebigen Anzahl einzelner Inhaltsautoren zusammenfassen und verfolgen. Sie erhalten damit schnell und bequem Zugang zu den jeweils aktuellen Inhalten.</span><span class="sxs-lookup"><span data-stu-id="95e8d-113">Content consumers can use a feed reader app to aggregate and monitor feeds from any number of individual content authors, gaining access to the latest content quickly and conveniently.</span></span>

## <a name="which-feed-format-standards-are-supported"></a><span data-ttu-id="95e8d-114">Welche Feed-Formatstandards werden unterstützt?</span><span class="sxs-lookup"><span data-stu-id="95e8d-114">Which feed format standards are supported?</span></span>

<span data-ttu-id="95e8d-115">Die universelle Windows-Plattform (UWP) unterstützt das Abrufen von Feeds für RSS-Formatstandards von 0.91 bis RSS 2.0 sowie für Atom-Standards von 0.3 bis 1.0.</span><span class="sxs-lookup"><span data-stu-id="95e8d-115">The Universal Windows Platform (UWP) supports feed retrieval for RSS format standards from 0.91 to RSS 2.0, and Atom standards from 0.3 to 1.0.</span></span> <span data-ttu-id="95e8d-116">Klassen im [**Windows.Web.Syndication**](https://msdn.microsoft.com/library/windows/apps/br243632)-Namespace können Feeds und Feedelemente definieren, die sowohl RSS- als auch Atom-Elemente darstellen können.</span><span class="sxs-lookup"><span data-stu-id="95e8d-116">Classes in the [**Windows.Web.Syndication**](https://msdn.microsoft.com/library/windows/apps/br243632) namespace can define feeds and feed items capable of representing both RSS and Atom elements.</span></span>

<span data-ttu-id="95e8d-117">Zudem können Feeddokumente in den Atom1.0- und RSS2.0-Formaten Elemente oder Attribute enthalten, die nicht in den offiziellen Spezifikationen definiert sind.</span><span class="sxs-lookup"><span data-stu-id="95e8d-117">Additionally, Atom 1.0 and RSS 2.0 formats both allow their feed documents to contain elements or attributes not defined in the official specifications.</span></span> <span data-ttu-id="95e8d-118">Mit der Zeit haben sich diese benutzerdefinierten Elemente und Attribute zu einer Möglichkeit entwickelt, domänenspezifische Informationen zu definieren, die von anderen Webdienst-Datenformaten wie GData und OData genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="95e8d-118">Over time, these custom elements and attributes have become a way to define domain-specific information consumed by other web service data formats like GData and OData.</span></span> <span data-ttu-id="95e8d-119">Zur Unterstützung dieses zusätzlichen Features stellt die [**SyndicationNode**](https://msdn.microsoft.com/library/windows/apps/br243585)-Klasse generische XML-Elemente dar.</span><span class="sxs-lookup"><span data-stu-id="95e8d-119">To support this added feature, the [**SyndicationNode**](https://msdn.microsoft.com/library/windows/apps/br243585) class represents generic XML elements.</span></span> <span data-ttu-id="95e8d-120">Durch die Verwendung von **SyndicationNode** mit Klassen im [**Windows.Data.Xml.Dom**](https://msdn.microsoft.com/library/windows/apps/br240819)-Namespace können Apps auf Attribute, Erweiterungen und beliebige verwendbare Inhalte zugreifen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-120">Using **SyndicationNode** with classes in the [**Windows.Data.Xml.Dom**](https://msdn.microsoft.com/library/windows/apps/br240819) namespace, allows apps to access attributes, extensions, and any content that they may contain.</span></span>

<span data-ttu-id="95e8d-121">Beachten Sie, dass die UWP-Implementierung des Atom Publication Protocol ([**Windows.Web.AtomPub**](https://msdn.microsoft.com/library/windows/apps/br210609)) für die Veröffentlichung der Inhalte von Fremdanbietern lediglich Feedinhaltsvorgänge gemäß den Standards Atom und Atom Publication unterstützt.</span><span class="sxs-lookup"><span data-stu-id="95e8d-121">Note that, for publication of syndicated content, the UWP implementation of the Atom Publication Protocol ([**Windows.Web.AtomPub**](https://msdn.microsoft.com/library/windows/apps/br210609)) only supports feed content operations according to the Atom and Atom Publication standards.</span></span>

## <a name="using-syndicated-content-with-network-isolation"></a><span data-ttu-id="95e8d-122">Verwenden von Fremdanbieterinhalt mit der Netzwerkisolation</span><span class="sxs-lookup"><span data-stu-id="95e8d-122">Using syndicated content with network isolation</span></span>

<span data-ttu-id="95e8d-123">Das Netzwerkisolationsfeature der UWP ermöglicht es Entwicklern, den Netzwerkzugriff einer UWP-App zu steuern und zu begrenzen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-123">The network isolation feature in the UWP enables a developer to control and limit network access by a UWP app.</span></span> <span data-ttu-id="95e8d-124">Nicht jede App muss Zugriff auf das Netzwerk haben.</span><span class="sxs-lookup"><span data-stu-id="95e8d-124">Not all apps may require access to the network.</span></span> <span data-ttu-id="95e8d-125">Ist dies für eine App jedoch erforderlich, bietet die UWP verschiedene Ebenen des Netzwerkzugriffs, die durch Auswahl der entsprechenden Funktionen aktiviert werden können.</span><span class="sxs-lookup"><span data-stu-id="95e8d-125">However for those apps that do, UWP provides different levels of access to the network that can be enabled by selecting appropriate capabilities.</span></span>

<span data-ttu-id="95e8d-126">Mit der Netzwerkisolation kann ein Entwickler für jede App den Umfang des erforderlichen Netzwerkzugriffs definieren.</span><span class="sxs-lookup"><span data-stu-id="95e8d-126">Network isolation allows a developer to define for each app the scope of required network access.</span></span> <span data-ttu-id="95e8d-127">Eine App, für die der geeignete Umfang nicht definiert wurde, wird am Zugriff auf den angegebenen Netzwerktyp und an bestimmten Netzwerkanforderungstypen (ausgehende, vom Client initiierte Anforderungen oder sowohl eingehende, unaufgeforderte Anforderungen als auch ausgehende, vom Client initiierte Anforderungen) gehindert.</span><span class="sxs-lookup"><span data-stu-id="95e8d-127">An app without the appropriate scope defined is prevented from accessing the specified type of network, and specific type of network request (outbound client-initiated requests or both inbound unsolicited requests and outbound client-initiated requests).</span></span> <span data-ttu-id="95e8d-128">Durch die Möglichkeit, die Netzwerkisolation festzulegen und zu erzwingen, wird sichergestellt, dass eine App im Falle ihres Missbrauchs nur auf Netzwerke zugreifen kann, für die der App explizit der Zugriff gestattet wurde.</span><span class="sxs-lookup"><span data-stu-id="95e8d-128">The ability to set and enforce network isolation ensures that if an app does get compromised, it can only access networks where the app has explicitly been granted access.</span></span> <span data-ttu-id="95e8d-129">Hierdurch wird das Ausmaß der Auswirkungen auf andere Anwendungen und auf Windows erheblich reduziert.</span><span class="sxs-lookup"><span data-stu-id="95e8d-129">This significantly reduces the scope of the impact on other applications and on Windows.</span></span>

<span data-ttu-id="95e8d-130">Die Netzwerkisolation wirkt sich auf alle Klassenelemente in den [**Windows.Web.Syndication**](https://msdn.microsoft.com/library/windows/apps/br243632)-Namespace und im [**Windows.Web.AtomPub**](https://msdn.microsoft.com/library/windows/apps/br210609)-Namespace aus, die versuchen, auf das Netzwerk zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-130">Network isolation affects any class elements in the [**Windows.Web.Syndication**](https://msdn.microsoft.com/library/windows/apps/br243632) and [**Windows.Web.AtomPub**](https://msdn.microsoft.com/library/windows/apps/br210609) namespaces that try to access the network.</span></span> <span data-ttu-id="95e8d-131">Die Netzwerkisolation wird unter Windows aktiv erzwungen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-131">Windows actively enforces network isolation.</span></span> <span data-ttu-id="95e8d-132">Ein Aufruf eines Klassenelements im **Windows.Web.Syndication**-Namespace oder **Windows.Web.AtomPub**-Namespace, der zu einem Netzwerkzugriff führt, kann aufgrund der Netzwerkisolation einen Fehler verursachen, falls die geeignete Netzwerkfunktion nicht aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="95e8d-132">A call to a class element in the **Windows.Web.Syndication** or **Windows.Web.AtomPub** namespace that results in network access may fail because of network isolation if the appropriate network capability has not been enabled.</span></span>

<span data-ttu-id="95e8d-133">Die Netzwerkfunktionen für eine App werden beim Erstellen der App im App-Manifest konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="95e8d-133">The network capabilities for an app are configured in the app manifest when the app is built.</span></span> <span data-ttu-id="95e8d-134">Netzwerkfunktionen werden normalerweise hinzugefügt mithilfe von Microsoft Visual Studio2015 bei der Entwicklung der app.</span><span class="sxs-lookup"><span data-stu-id="95e8d-134">Network capabilities are usually added using Microsoft Visual Studio2015 when developing the app.</span></span> <span data-ttu-id="95e8d-135">Sie können aber auch manuell mit einem Texteditor in der App-Manifestdatei festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="95e8d-135">Network capabilities may also be set manually in the app manifest file using a text editor.</span></span>

<span data-ttu-id="95e8d-136">Ausführlichere Informationen zu Netzwerkisolation und Netzwerkfunktionen finden Sie im Abschnitt „Funktionen“ des Themas [Grundlagen zum Netzwerk](networking-basics.md).</span><span class="sxs-lookup"><span data-stu-id="95e8d-136">For more detailed information on network isolation and networking capabilities, see the "Capabilities" section in the [Networking basics](networking-basics.md) topic.</span></span>

## <a name="how-to-access-a-web-feed"></a><span data-ttu-id="95e8d-137">So wird's gemacht: Zugreifen auf einen Webfeed</span><span class="sxs-lookup"><span data-stu-id="95e8d-137">How to access a web feed</span></span>

<span data-ttu-id="95e8d-138">In diesem Abschnitt wird beschrieben, wie Sie einen Webfeed mithilfe von Klassen im [**Windows.Web.Syndication**](https://msdn.microsoft.com/library/windows/apps/br243632)-Namespace der in C# oder Javascript geschriebenen UWP-App abrufen und anzeigen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-138">This section shows how to retrieve and display a web feed using classes in the [**Windows.Web.Syndication**](https://msdn.microsoft.com/library/windows/apps/br243632) namespace in your UWP app written in C# or Javascript.</span></span>

**<span data-ttu-id="95e8d-139">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="95e8d-139">Prerequisites</span></span>**

<span data-ttu-id="95e8d-140">Damit die UWP-App im Netzwerk verwendet werden kann, müssen Sie alle erforderlichen Netzwerkfunktionen in der Projektdatei **Package.appxmanifest** festlegen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-140">To ensure your UWP app is network ready, you must set any network capabilities that are needed in the project **Package.appxmanifest** file.</span></span> <span data-ttu-id="95e8d-141">Wenn Ihre App als Client eine Verbindung mit Remotediensten im Internet herstellen muss, ist die Funktion **internetClient** erforderlich.</span><span class="sxs-lookup"><span data-stu-id="95e8d-141">If your app needs to connect as a client to remote services on the Internet, then the **internetClient** capability is needed.</span></span> <span data-ttu-id="95e8d-142">Weitere Informationen finden Sie im Abschnitt „Funktionen“ des Themas [Grundlagen zum Netzwerk](networking-basics.md).</span><span class="sxs-lookup"><span data-stu-id="95e8d-142">For more information, see the "Capabilities" section in the [Networking basics](networking-basics.md) topic.</span></span>

**<span data-ttu-id="95e8d-143">Abrufen von Fremdinhalten aus einem Webfeed</span><span class="sxs-lookup"><span data-stu-id="95e8d-143">Retrieving syndicated content from a web feed</span></span>**

<span data-ttu-id="95e8d-144">Nun sehen wir uns etwas Code an, der demonstriert, wie ein Feed abgerufen werden kann und anschließend die einzelnen Elemente des Feeds angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="95e8d-144">Now we will review some code that demonstrates how to retrieve a feed, and then display each individual item that the feed contains.</span></span> <span data-ttu-id="95e8d-145">Bevor wir die Anforderung konfigurieren und senden können, definieren wir einige Variablen, die wir während des Vorgangs verwenden werden, und initialisieren eine Instanz von [**SyndicationClient**](https://msdn.microsoft.com/library/windows/apps/br243456), die die Methoden und Eigenschaften definiert, die wir zum Abrufen und Anzeigen des Feeds verwenden.</span><span class="sxs-lookup"><span data-stu-id="95e8d-145">Before we can configure and send the request, we'll define a few variables we'll be using during the operation, and initialize an instance of [**SyndicationClient**](https://msdn.microsoft.com/library/windows/apps/br243456), which defines the methods and properties we'll use to retrieve and display the feed.</span></span>

<span data-ttu-id="95e8d-146">Der [**Uri**](https://msdn.microsoft.com/library/windows/apps/br226017)-Konstruktor löst eine Ausnahme aus, wenn das an den Konstruktor übergebene *uriString*-Element kein gültiger URI ist.</span><span class="sxs-lookup"><span data-stu-id="95e8d-146">The [**Uri**](https://msdn.microsoft.com/library/windows/apps/br226017) constructor throws an exception if the *uriString* passed to the constructor is not a valid URI.</span></span> <span data-ttu-id="95e8d-147">Daher überprüfen wir das *uriString*-Element mithilfe eines try/catch-Blocks.</span><span class="sxs-lookup"><span data-stu-id="95e8d-147">So we validate the *uriString* using a try/catch block.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
Windows.Web.Syndication.SyndicationClient client = new Windows.Web.Syndication.SyndicationClient();
Windows.Web.Syndication.SyndicationFeed feed;
// The URI is validated by catching exceptions thrown by the Uri constructor.
Uri uri = null;
// Use your own uriString for the feed you are connecting to.
string uriString = "";
try
{
    uri = new Uri(uriString);
}
catch (Exception ex)
{
    // Handle the invalid URI here.
}
```
```javascript
var currentFeed = null;
var currentItemIndex = 0;
var client = new Windows.Web.Syndication.SyndicationClient();
// The URI is validated by catching exceptions thrown by the Uri constructor.
var uri = null;
try {
    uri = new Windows.Foundation.Uri(uriString);
} catch (error) {
    WinJS.log && WinJS.log("Error: Invalid URI");
    return;
}
```

<span data-ttu-id="95e8d-148">Anschließend konfigurieren wir die Anforderung, indem wir alle erforderlichen Serveranmeldeinformationen (die [**ServerCredential**](https://msdn.microsoft.com/library/windows/apps/br243461)-Eigenschaft), Proxyanmeldeinformationen (die [**ProxyCredential**](https://msdn.microsoft.com/library/windows/apps/br243459)-Eigenschaft) und HTTP-Header (die [**SetRequestHeader**](https://msdn.microsoft.com/library/windows/apps/br243462)-Methode) festlegen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-148">Next we configure the request by setting any Server credentials (the [**ServerCredential**](https://msdn.microsoft.com/library/windows/apps/br243461) property), proxy credentials (the [**ProxyCredential**](https://msdn.microsoft.com/library/windows/apps/br243459) property), and HTTP headers (the [**SetRequestHeader**](https://msdn.microsoft.com/library/windows/apps/br243462) method) needed.</span></span> <span data-ttu-id="95e8d-149">Da die grundlegenden Anforderungsparameter nun konfiguriert sind, haben wir ein gültiges, mit einer von der App bereitgestellten Feed-URI-Zeichenfolge erstelltes [**Uri**](https://msdn.microsoft.com/library/windows/apps/br226017)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="95e8d-149">With the basic request parameters configured, a valid [**Uri**](https://msdn.microsoft.com/library/windows/apps/br226017) object, created using a feed URI string provided by the app.</span></span> <span data-ttu-id="95e8d-150">Das **Uri**-Objekt wird anschließend an die [**RetrieveFeedAsync**](https://msdn.microsoft.com/library/windows/apps/br243460)-Funktion übergeben, um den Feed anzufordern.</span><span class="sxs-lookup"><span data-stu-id="95e8d-150">The **Uri** object is then passed to the [**RetrieveFeedAsync**](https://msdn.microsoft.com/library/windows/apps/br243460) function to request the feed.</span></span>

<span data-ttu-id="95e8d-151">In der Annahme, dass die gewünschten Feedinhalte zurückgegeben wurden, durchläuft der Beispielcode jedes Feedelement, wobei er **displayCurrentItem** aufruft (was wir als Nächstes definieren), um Elemente und ihre Inhalte über die UI als Liste anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-151">Assuming the desired feed content was returned, the example code iterates through each feed item, calling **displayCurrentItem** (which we define next), to display items and their contents as a list through the UI.</span></span>

<span data-ttu-id="95e8d-152">Beim Aufrufen der meisten asynchronen Netzwerkmethoden müssen Sie Code zum Behandeln von Ausnahmen schreiben.</span><span class="sxs-lookup"><span data-stu-id="95e8d-152">You must write code to handle exceptions when you call most asynchronous network methods.</span></span> <span data-ttu-id="95e8d-153">Ihr Ausnahmehandler kann detailliertere Informationen zur Ursache abrufen, um die Ausnahme besser verstehen und entsprechende Entscheidungen treffen zu können.</span><span class="sxs-lookup"><span data-stu-id="95e8d-153">Your exception handler can retrieve more detailed information on the cause of the exception to better understand the failure and make appropriate decisions.</span></span>

<span data-ttu-id="95e8d-154">Die [**RetrieveFeedAsync**](https://msdn.microsoft.com/library/windows/apps/br243460)-Methode löst eine Ausnahme aus, wenn keine Verbindung mit dem HTTP-Server hergestellt werden kann oder wenn das [**Uri**](https://msdn.microsoft.com/library/windows/apps/br226017)-Objekt nicht auf einen gültigen AtomPub- oder RSS-Feed verweist.</span><span class="sxs-lookup"><span data-stu-id="95e8d-154">The [**RetrieveFeedAsync**](https://msdn.microsoft.com/library/windows/apps/br243460) method throws an exception if a connection could not be established with the HTTP server or the [**Uri**](https://msdn.microsoft.com/library/windows/apps/br226017) object does not point to a valid AtomPub or RSS feed.</span></span> <span data-ttu-id="95e8d-155">Im JavaScript-Beispielcode wird eine **onError**-Funktion verwendet, um etwaige Ausnahmen abzufangen und ausführlichere Informationen zur Ausnahme auszugeben, wenn ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="95e8d-155">The Javascript sample code uses an **onError** function to catch any exceptions and print out more detailed information on the exception if an error occurs.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
try
{
    // Although most HTTP servers do not require User-Agent header, 
    // others will reject the request or return a different response if this header is missing.
    // Use the setRequestHeader() method to add custom headers.
    client.SetRequestHeader("User-Agent", "Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.2; WOW64; Trident/6.0)");
    feed = await client.RetrieveFeedAsync(uri);
    // Retrieve the title of the feed and store it in a string.
    string title = feed.Title.Text;
    // Iterate through each feed item.
    foreach (Windows.Web.Syndication.SyndicationItem item in feed.Items)
    {
        displayCurrentItem(item);
    }
}
catch (Exception ex)
{
    // Handle the exception here.
}
```
```javascript
function onError(err) {
    WinJS.log && WinJS.log(err, "sample", "error");
    // Match error number with a ErrorStatus value.
    // Use Windows.Web.WebErrorStatus.getStatus() to retrieve HTTP error status codes.
    var errorStatus = Windows.Web.Syndication.SyndicationError.getStatus(err.number);
    if (errorStatus === Windows.Web.Syndication.SyndicationErrorStatus.invalidXml) {
        displayLog("An invalid XML exception was thrown. Please make sure to use a URI that points to a RSS or Atom feed.");
    }
}
// Retrieve and display feed at given feed address.
function retreiveFeed(uri) {
    // Although most HTTP servers do not require User-Agent header, 
    // others will reject the request or return a different response if this header is missing.
    // Use the setRequestHeader() method to add custom headers.
    client.setRequestHeader("User-Agent", "Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.2; WOW64; Trident/6.0)");
    client.retrieveFeedAsync(uri).done(function (feed) {
        currentFeed = feed;
        WinJS.log && WinJS.log("Feed download complete.", "sample", "status");
        var title = "(no title)";
        if (currentFeed.title) {
            title = currentFeed.title.text;
        }
        document.getElementById("CurrentFeedTitle").innerText = title;
        currentItemIndex = 0;
        if (currentFeed.items.size > 0) {
            displayCurrentItem();
        }
        // List the items.
        displayLog("Items: " + currentFeed.items.size);
     }, onError);
}
```

<span data-ttu-id="95e8d-156">Im vorherigen Schritt hat [**RetrieveFeedAsync**](https://msdn.microsoft.com/library/windows/apps/br243460) die angeforderten Feedinhalte zurückgegeben, und der Beispielcode hat damit begonnen, die verfügbaren Feedelemente zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-156">In the previous step, [**RetrieveFeedAsync**](https://msdn.microsoft.com/library/windows/apps/br243460) returned the requested feed content and the example code got to work iterating through available feed items.</span></span> <span data-ttu-id="95e8d-157">Jedes dieser Elemente wird mithilfe eines [**SyndicationItem**](https://msdn.microsoft.com/library/windows/apps/br243533)-Objekts dargestellt, das alle vom jeweiligen Veröffentlichungsstandard (RSS oder Atom) bereitgestellten Eigenschaften und Inhalte des Elements enthält.</span><span class="sxs-lookup"><span data-stu-id="95e8d-157">Each of these items is represented using a [**SyndicationItem**](https://msdn.microsoft.com/library/windows/apps/br243533) object that contains all of the item properties and content afforded by the relevant syndication standard (RSS or Atom).</span></span> <span data-ttu-id="95e8d-158">Im folgenden Beispiel beobachten wir die **displayCurrentItem**-Funktion dabei, wie sie die einzelnen Elemente durchgeht und ihre Inhalte über verschiedene benannte UI-Elemente ausgibt.</span><span class="sxs-lookup"><span data-stu-id="95e8d-158">In the following example we observe the **displayCurrentItem** function working through each item and displaying its content through various named UI elements.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
private void displayCurrentItem(Windows.Web.Syndication.SyndicationItem item)
{
    string itemTitle = item.Title == null ? "No title" : item.Title.Text;
    string itemLink = item.Links == null ? "No link" : item.Links.FirstOrDefault().ToString();
    string itemContent = item.Content == null ? "No content" : item.Content.Text;
    //displayCurrentItem is continued below.
```
```javascript
function displayCurrentItem() {
    var item = currentFeed.items[currentItemIndex];
    // Display item number.
    document.getElementById("Index").innerText = (currentItemIndex + 1) + " of " + currentFeed.items.size;
    // Display title.
    var title = "(no title)";
    if (item.title) {
        title = item.title.text;
    }
    document.getElementById("ItemTitle").innerText = title;
    // Display the main link.
    var link = "";
    if (item.links.size > 0) {
        link = item.links[0].uri.absoluteUri;
    }
    var link = document.getElementById("Link");
    link.innerText = link;
    link.href = link;
    // Display the body as HTML.
    var content = "(no content)";
    if (item.content) {
        content = item.content.text;
    }
    else if (item.summary) {
        content = item.summary.text;
    }
    document.getElementById("WebView").innerHTML = window.toStaticHTML(content);
                //displayCurrentItem is continued below.
```

<span data-ttu-id="95e8d-159">Wie bereits angesprochen, unterscheidet sich der Inhaltstyp, der durch ein [**SyndicationItem**](https://msdn.microsoft.com/library/windows/apps/br243533)-Objekt dargestellt wird, in Abhängigkeit vom Feedstandard (RSS oder Atom), der für die Veröffentlichung des Feeds genutzt wird.</span><span class="sxs-lookup"><span data-stu-id="95e8d-159">As suggested earlier, the type of content represented by a [**SyndicationItem**](https://msdn.microsoft.com/library/windows/apps/br243533) object will differ depending on the feed standard (RSS or Atom) employed to publish the feed.</span></span> <span data-ttu-id="95e8d-160">Im Gegensatz zu einem RSS-Feed kann ein Atom-Feed beispielsweise eine Liste mit [**Contributors**](https://msdn.microsoft.com/library/windows/apps/br243540)-Elementen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="95e8d-160">For example, an Atom feed is capable of providing a list of [**Contributors**](https://msdn.microsoft.com/library/windows/apps/br243540), but an RSS feed is not.</span></span> <span data-ttu-id="95e8d-161">Auf Erweiterungselemente in einem Feedelement, die von keinem der Standards unterstützt werden (etwa Dublin Core-Erweiterungselemente), kann jedoch mithilfe der [**SyndicationItem.ElementExtensions**](https://msdn.microsoft.com/library/windows/apps/br243543)-Eigenschaft zugegriffen werden, um sie anschließend wie im folgenden Beispielcode dargestellt anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="95e8d-161">However, extension elements included in a feed item that are not supported by either standard (e.g., Dublin Core extension elements) can be accessed using the [**SyndicationItem.ElementExtensions**](https://msdn.microsoft.com/library/windows/apps/br243543) property and then displayed as demonstrated in the following example code.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
    //displayCurrentItem continued.
    string extensions = "";
    foreach (Windows.Web.Syndication.SyndicationNode node in item.ElementExtensions)
    {
        string nodeName = node.NodeName;
        string nodeNamespace = node.NodeNamespace;
        string nodeValue = node.NodeValue;
        extensions += nodeName + "\n" + nodeNamespace + "\n" + nodeValue + "\n";
    }
    this.listView.Items.Add(itemTitle + "\n" + itemLink + "\n" + itemContent + "\n" + extensions);
}
```
```javascript
    // displayCurrentItem function continued.
    var bindableNodes = [];
    for (var i = 0; i < item.elementExtensions.size; i++) {
        var bindableNode = {
            nodeName: item.elementExtensions[i].nodeName,
             nodeNamespace: item.elementExtensions[i].nodeNamespace,
             nodeValue: item.elementExtensions[i].nodeValue,
        };
        bindableNodes.push(bindableNode);
    }
    var dataList = new WinJS.Binding.List(bindableNodes);
    var listView = document.getElementById("extensionsListView").winControl;
    WinJS.UI.setOptions(listView, {
        itemDataSource: dataList.dataSource
    });
}
```
