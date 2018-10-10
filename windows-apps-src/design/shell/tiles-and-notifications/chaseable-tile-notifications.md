---
author: andrewleader
Description: Use chaseable tile notifications to find out what your app displayed on its Live Tile when the user clicked it.
title: Verfolgbare Kachelbenachrichtigungen
ms.assetid: E9AB7156-A29E-4ED7-B286-DA4A6E683638
label: Chaseable tile notifications
template: detail.hbs
ms.author: mijacobs
ms.date: 06/13/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, verfolgbare Kacheln, Live-Kacheln, verfolgbare Kachelbenachrichtigungen
ms.localizationpriority: medium
ms.openlocfilehash: b6d86d8881e0027a28f0f2a737e5f3fcb46a6ab5
ms.sourcegitcommit: 8e30651fd691378455ea1a57da10b2e4f50e66a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "4501437"
---
# <a name="chaseable-tile-notifications"></a><span data-ttu-id="08e2c-103">Verfolgbare Kachelbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="08e2c-103">Chaseable tile notifications</span></span>

<span data-ttu-id="08e2c-104">Mit den verfolgbaren Kachelbenachrichtigungen können Sie festlegen, welche Kachelbenachrichtigungen die Live-Kachel Ihrer App anzeigen sollte, wenn der Benutzer auf die Kachel geklickt hat.</span><span class="sxs-lookup"><span data-stu-id="08e2c-104">Chaseable tile notifications let you determine which tile notifications your app's Live Tile was displaying when the user clicked the tile.</span></span>  
<span data-ttu-id="08e2c-105">Beispielsweise könnte eine Nachrichtenanwendung diese Funktion verwenden, um herauszufinden, welche Nachrichtenstory ihre Live-Kachel angezeigt hat. Sie könnte sicherstellen, dass die Story prominent angezeigt wird, damit der Benutzer sie finden kann.</span><span class="sxs-lookup"><span data-stu-id="08e2c-105">For example, a news app could use this feature to determine which news story the its Live Tile was displaying when the user launched it; it could that ensure that the story is prominently displayed so that the user can find it.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="08e2c-106">**Erfordert das Anniversary Update**: Um verfolgbare Kachelbenachrichtigungen mit C#, C++ oder VB-basierte UWP-Apps zu verwenden, müssen Sie SDK 14393 als Zielobjekt auswählen und Build 14393 oder höher ausführen.</span><span class="sxs-lookup"><span data-stu-id="08e2c-106">**Requires Anniversary Update**: To use chaseable tile notifications with C#, C++, or VB-based UWP apps, you must target SDK 14393 and be running build 14393 or higher.</span></span> <span data-ttu-id="08e2c-107">Für JavaScript-basierte UWP-Apps müssen Sie SDK 17134 als Zielobjekt auswählen und Build 17134 oder höher verwenden.</span><span class="sxs-lookup"><span data-stu-id="08e2c-107">For JavaScript-based UWP apps, you must target SDK 17134 and be running build 17134 or higher.</span></span> 


> <span data-ttu-id="08e2c-108">**Wichtige APIs**: [LaunchActivatedEventArgs.TileActivatedInfo-Eigenschaft](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.launchactivatedeventargs.TileActivatedInfo), [TileActivatedInfo-Klasse](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.tileactivatedinfo)</span><span class="sxs-lookup"><span data-stu-id="08e2c-108">**Important APIs**: [LaunchActivatedEventArgs.TileActivatedInfo property](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.launchactivatedeventargs.TileActivatedInfo), [TileActivatedInfo class](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.tileactivatedinfo)</span></span>


## <a name="how-it-works"></a><span data-ttu-id="08e2c-109">Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="08e2c-109">How it works</span></span>

<span data-ttu-id="08e2c-110">Um verfolgbare Kachelbenachrichtigungen zu aktivieren, verwenden Sie die **Argumente**-Eigenschaft auf den Kachelbenachrichtigungs-Payload, ähnlich der Launch-Eigenschaft auf den Toast-Benachrichtigungs-Payload, um Informationen über den Inhalt in die Kachelbenachrichtigung einzubetten.</span><span class="sxs-lookup"><span data-stu-id="08e2c-110">To enable chaseable tile notifications, you use the **Arguments** property on the tile notification payload, similar to the launch property on the toast notification payload, to embed info about the content in the tile notification.</span></span>

<span data-ttu-id="08e2c-111">Wenn Ihre App über die Live-Kachel gestartet wird, gibt das System eine Liste der Argumente aus den aktuell/zuletzt angezeigten Kachelbenachrichtigungen zurück.</span><span class="sxs-lookup"><span data-stu-id="08e2c-111">When your app is launched via the Live Tile, the system returns a list of arguments from the current/recently displayed tile notifications.</span></span>


## <a name="when-to-use-chaseable-tile-notifications"></a><span data-ttu-id="08e2c-112">Wann werden Benachrichtigungen über verfolgbare Kacheln verwendet?</span><span class="sxs-lookup"><span data-stu-id="08e2c-112">When to use chaseable tile notifications</span></span>

<span data-ttu-id="08e2c-113">Verfolgbare Kachelbenachrichtigungen werden normalerweise verwendet, wenn Sie die Benachrichtigungswarteschlange für Ihrer Live-Kachel verwenden (was bedeutet, dass Sie bis zu 5 verschiedene Benachrichtigungen durchlaufen).</span><span class="sxs-lookup"><span data-stu-id="08e2c-113">Chaseable tile notifications are typically used when you're using the notification queue on your Live Tile (which means you are cycling through up to 5 different notifications).</span></span> <span data-ttu-id="08e2c-114">Sie sind auch dann von Vorteil, wenn die Inhalte in Live-Kacheln möglicherweise nicht mit den neuesten Inhalten in der App synchronisiert sind.</span><span class="sxs-lookup"><span data-stu-id="08e2c-114">They're also beneficial when the content on your Live Tile is potentially out of sync with the latest content in the app.</span></span> <span data-ttu-id="08e2c-115">Zum Beispiel aktualisiert die Nachrichtenanwendung ihre Live-Kachel alle 30 Minuten. Aber wenn die Anwendung gestartet wird, lädt sie die neuesten Nachrichten (die möglicherweise etwas nicht enthalten, das sich auf der Kachel aus dem letzten Polling-Intervall befand).</span><span class="sxs-lookup"><span data-stu-id="08e2c-115">For example, the News app refreshes its Live Tile every 30 minutes, but when the app is launched, it loads the latest news (which may not include something that was on the tile from the last polling interval).</span></span> <span data-ttu-id="08e2c-116">Wenn das passiert, könnte der Benutzer frustriert darüber sein, dass er die Story, die er auf der Live-Kachel gesehen hat, nicht finden kann.</span><span class="sxs-lookup"><span data-stu-id="08e2c-116">When this happens, the user might get frustrated about not being able to find the story they saw on their Live Tile.</span></span> <span data-ttu-id="08e2c-117">Hier helfen Ihnen verfolgbare Kachelbenachrichtigungen, indem Sie sicherstellen können, dass das, was der Benutzer auf der Kachel gesehen hat, leicht erkennbar ist.</span><span class="sxs-lookup"><span data-stu-id="08e2c-117">That's where chaseable tile notifications can help, by allowing you to make sure that what the user saw on their Tile is easily discoverable.</span></span>

## <a name="what-to-do-with-a-chaseable-tile-notifications"></a><span data-ttu-id="08e2c-118">Was tun mit einer verfolgbaren Kachelbenachrichtigung?</span><span class="sxs-lookup"><span data-stu-id="08e2c-118">What to do with a chaseable tile notifications</span></span>

<span data-ttu-id="08e2c-119">Der wichtigste Aspekt ist, dass Sie in den meisten Szenarien **NICHT direkt zu der spezifischen Benachrichtigung navigieren sollten**, die sich auf der Kachel befand, als der Benutzer darauf geklickt hat.</span><span class="sxs-lookup"><span data-stu-id="08e2c-119">The most important thing to note is that in most scenarios, **you should NOT directly navigate to the specific notification** that was on the Tile when the user clicked it.</span></span> <span data-ttu-id="08e2c-120">Ihr Live-Kachel wird als Einstiegspunkt in Ihre Anwendung verwendet.</span><span class="sxs-lookup"><span data-stu-id="08e2c-120">Your Live Tile is used as an entry point to your application.</span></span> <span data-ttu-id="08e2c-121">Es kann zwei Szenarien geben, wenn ein Benutzer auf Ihr Live-Kachel klickt: (1) Er will Ihre Anwendung normal starten, oder (2) er will mehr Informationen über eine bestimmte Benachrichtigung sehen, die auf der Live-Kachel war.</span><span class="sxs-lookup"><span data-stu-id="08e2c-121">There can be two scenarios when a user clicks your Live Tile: (1) they wanted to launch your app normally, or (2) they wanted to see more information about a specific notification that was on the Live Tile.</span></span> <span data-ttu-id="08e2c-122">Da es für den Benutzer keine Möglichkeit gibt, explizit anzugeben, welches Verhalten er wünscht, ist es das ideale Erlebnis, **Ihre Anwendung normal zu starten und gleichzeitig sicherzustellen, dass die Benachrichtigung, die der Benutzer gesehen hat, leicht erkennbar ist**.</span><span class="sxs-lookup"><span data-stu-id="08e2c-122">Since there's no way for the user to explicitly say which behavior they want, the ideal experience is to **launch your app normally, while making sure that the notification the user saw is easily discoverable**.</span></span>

<span data-ttu-id="08e2c-123">Wenn Sie beispielsweise auf die Live-Kachel der MSN News-App klicken, wird die Anwendung normal gestartet: Sie zeigt die Startseite oder den Artikel an, den der Benutzer zuvor gelesen hat.</span><span class="sxs-lookup"><span data-stu-id="08e2c-123">For example, clicking the MSN News app's Live Tile launches the app normally: it displays the home page, or whichever article the user was previously reading.</span></span> <span data-ttu-id="08e2c-124">Auf der Startseite sorgt die App jedoch dafür, dass die Story aus der Live-Kachel leicht auffindbar ist.</span><span class="sxs-lookup"><span data-stu-id="08e2c-124">However, on the home page, the app ensures that the story from the Live Tile is easily discoverable.</span></span> <span data-ttu-id="08e2c-125">Auf diese Weise werden beide Szenarien unterstützt: das Szenario, in dem Sie einfach nur die Anwendung starten/fortsetzen möchten, und das Szenario, in dem Sie die spezifische Story anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="08e2c-125">That way, both scenarios are supported: the scenario where you simply want to launch/resume the app, and the scenario where you want to view the specific story.</span></span>


## <a name="how-to-include-the-arguments-property-in-your-tile-notification-payload"></a><span data-ttu-id="08e2c-126">Einbeziehen der Argumente-Eigenschaft in Ihren Kachelbenachrichtigungs-Payload</span><span class="sxs-lookup"><span data-stu-id="08e2c-126">How to include the Arguments property in your tile notification payload</span></span>

<span data-ttu-id="08e2c-127">Bei einem Benachrichtigungs-Payload ermöglicht die Eigenschaft „Arguments“ Ihrer App, Daten zur Verfügung zu stellen, mit denen Sie die Benachrichtigung später identifizieren können.</span><span class="sxs-lookup"><span data-stu-id="08e2c-127">In a notification payload, the arguments property enables your app to provide data you can use to later identify the notification.</span></span> <span data-ttu-id="08e2c-128">Ihre Argumente könnten z. B. die ID der Story enthalten, so dass Sie beim Start die Story abrufen und anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="08e2c-128">For example, your arguments might include the story's id, so that when launched, you can retrieve and display the story.</span></span> <span data-ttu-id="08e2c-129">Die Eigenschaft akzeptiert eine Zeichenfolge, die nach Belieben serialisiert werden kann (Abfrage, JSON etc.), aber wir empfehlen in der Regel eine Abfrage, da diese klein und von XML codierbar ist.</span><span class="sxs-lookup"><span data-stu-id="08e2c-129">The property accepts a string, which can be serialized however you like (query string, JSON, etc), but we typically recommend query string format, since it's lightweight and XML-encodes nicely.</span></span>

<span data-ttu-id="08e2c-130">Die Eigenschaft kann sowohl auf die Elemente **TileVisual** als auch **TileBinding** festgelegt werden und wird nach unten hin kaskadiert.</span><span class="sxs-lookup"><span data-stu-id="08e2c-130">The property can be set on both the **TileVisual** and the **TileBinding** elements, and will cascade down.</span></span> <span data-ttu-id="08e2c-131">Wenn Sie die gleichen Argumente für jede Kachelgröße möchten, setzen Sie einfach die Argumente auf **TileVisual**.</span><span class="sxs-lookup"><span data-stu-id="08e2c-131">If you want the same arguments on every tile size, simply set the arguments on the **TileVisual**.</span></span> <span data-ttu-id="08e2c-132">Wenn Sie spezifische Argumente für bestimmte Kachelgrößen benötigen, können Sie die Argumente auf einzelne **TileBinding**-Elemente setzen.</span><span class="sxs-lookup"><span data-stu-id="08e2c-132">If you need specific arguments for specific tile sizes, you can set the arguments on individual **TileBinding** elements.</span></span>

<span data-ttu-id="08e2c-133">In diesem Beispiel wird ein Payload für Benachrichtigungen erstellt, de die Arguments-Eigenschaft verwendet, damit Benachrichtigungen später identifiziert werden können.</span><span class="sxs-lookup"><span data-stu-id="08e2c-133">This example creates a notification payload that uses the arguments property so that notification can be identified later.</span></span> 

```csharp
// Uses the following NuGet packages
// - Microsoft.Toolkit.Uwp.Notifications
// - QueryString.NET
 
TileContent content = new TileContent()
{
    Visual = new TileVisual()
    {
        // These arguments cascade down to Medium and Wide
        Arguments = new QueryString()
        {
            { "action", "storyClicked" },
            { "story", "201c9b1" }
        }.ToString(),
 
 
        // Medium tile
        TileMedium = new TileBinding()
        {
            Content = new TileBindingContentAdaptive()
            {
                // Omitted
            }
        },
 
 
        // Wide tile is same as Medium
        TileWide = new TileBinding() { /* Omitted */ },
 
 
        // Large tile is an aggregate of multiple stories
        // and therefore needs different arguments
        TileLarge = new TileBinding()
        {
            Arguments = new QueryString()
            {
                { "action", "storiesClicked" },
                { "story", "43f939ag" },
                { "story", "201c9b1" },
                { "story", "d9481ca" }
            }.ToString(),
 
            Content = new TileBindingContentAdaptive() { /* Omitted */ }
        }
    }
};
```


## <a name="how-to-check-for-the-arguments-property-when-your-app-launches"></a><span data-ttu-id="08e2c-134">So überprüfen Sie die Arguments-Eigenschaft, wenn Ihre Anwendung startet</span><span class="sxs-lookup"><span data-stu-id="08e2c-134">How to check for the arguments property when your app launches</span></span>

<span data-ttu-id="08e2c-135">Die meisten Apps haben eine Datei App.xaml.cs, die eine Überschreibung der [OnLaunched](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_)-Methode enthält.</span><span class="sxs-lookup"><span data-stu-id="08e2c-135">Most apps have an App.xaml.cs file that contains an override for the [OnLaunched](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_) method.</span></span> <span data-ttu-id="08e2c-136">Wie der Name schon sagt, ruft Ihre App diese Methode beim Start auf.</span><span class="sxs-lookup"><span data-stu-id="08e2c-136">As its name suggests, your app calls this method when it's launched.</span></span> <span data-ttu-id="08e2c-137">Sie benötigt ein einziges Argument, ein [LaunchActivatedEventArgs](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.launchactivatedeventargs)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="08e2c-137">It takes a single argument, a [LaunchActivatedEventArgs](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.launchactivatedeventargs) object.</span></span>

<span data-ttu-id="08e2c-138">Das LaunchActivatedEventArgs-Objekt hat eine Eigenschaft, die verfolgbare Benachrichtigungen ermöglicht: die [TileActivatedInfo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.launchactivatedeventargs.TileActivatedInfo)-Eigenschaft, die den Zugriff auf ein [TileActivatedInfo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.tileactivatedinfo)-Objekt ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="08e2c-138">The LaunchActivatedEventArgs object has a property that enables chaseable notifications: the [TileActivatedInfo property](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.launchactivatedeventargs.TileActivatedInfo), which provides access to a [TileActivatedInfo object](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.tileactivatedinfo).</span></span> <span data-ttu-id="08e2c-139">Wenn der Benutzer Ihre Anwendung startet, wird diese Eigenschaft initialisiert, wenn Sie Ihre Anwendung aus ihrer Kachel starten (anstatt aus der App-Liste, der Suche oder einem anderen Eingabepunkt).</span><span class="sxs-lookup"><span data-stu-id="08e2c-139">When the user launches your app from its tile (rather than the app list, search, or any other entry point), your app initializes this property.</span></span>

<span data-ttu-id="08e2c-140">Das [TileActivatedInfo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.tileactivatedinfo)-Objekt enthält eine Eigenschaft namens [RecentlyShownNotifications](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.tileactivatedinfo.RecentlyShownNotifications), die eine Liste von Benachrichtigungen enthält, die innerhalb der letzten 15 Minuten auf der Kachel angezeigt wurden.</span><span class="sxs-lookup"><span data-stu-id="08e2c-140">The [TileActivatedInfo object](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.tileactivatedinfo) contains a property called [RecentlyShownNotifications](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.tileactivatedinfo.RecentlyShownNotifications), which contains a list of notifications that have been shown on the tile within the last 15 minutes.</span></span> <span data-ttu-id="08e2c-141">Das erste Element in der Liste stellt die Benachrichtigung dar, die gerade auf de Kachel angezeigt wird, und die folgenden Elemente stellen die Benachrichtigungen dar, die der Benutzer vor dem aktuellen Element gesehen hat.</span><span class="sxs-lookup"><span data-stu-id="08e2c-141">The first item in the list represents the notification currently on the tile, and the subsequent items represent the notifications that the user saw before the current one.</span></span> <span data-ttu-id="08e2c-142">Wenn Ihre Kachel gelöscht wurde, ist diese Liste leer.</span><span class="sxs-lookup"><span data-stu-id="08e2c-142">If your tile has been cleared, this list is empty.</span></span>

<span data-ttu-id="08e2c-143">Jede ShownTileNotification hat eine Arguments-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="08e2c-143">Each ShownTileNotification has an Arguments property.</span></span> <span data-ttu-id="08e2c-144">Die Arguments-Eigenschaft wird mit der Arguments-Zeichenfolge aus dem Kachelbenachrichtigungs-Payload oder Null (wenn der Payload nicht die Arguments-Zeichenfolge enthält) initialisiert.</span><span class="sxs-lookup"><span data-stu-id="08e2c-144">The Arguments property will be initialized with the arguments string from your tile notification payload, or null if your payload didn't include the arguments string.</span></span>

```csharp
protected override void OnLaunched(LaunchActivatedEventArgs args)
{
    // If the API is present (doesn't exist on 10240 and 10586)
    if (ApiInformation.IsPropertyPresent(typeof(LaunchActivatedEventArgs).FullName, nameof(LaunchActivatedEventArgs.TileActivatedInfo)))
    {
        // If clicked on from tile
        if (args.TileActivatedInfo != null)
        {
            // If tile notification(s) were present
            if (args.TileActivatedInfo.RecentlyShownNotifications.Count > 0)
            {
                // Get arguments from the notifications that were recently displayed
                string[] allArgs = args.TileActivatedInfo.RecentlyShownNotifications
                .Select(i => i.Arguments)
                .ToArray();
 
                // TODO: Highlight each story in the app
            }
        }
    }
 
    // TODO: Initialize app
}
```


## <a name="raw-xml-example"></a><span data-ttu-id="08e2c-145">Beispiel mit unformatiertem XML</span><span class="sxs-lookup"><span data-stu-id="08e2c-145">Raw XML example</span></span>

<span data-ttu-id="08e2c-146">Wenn Sie mit unformatiertes XML anstatt der Notifications-Bibliothek verwenden, finden Sie hier den XML-Code.</span><span class="sxs-lookup"><span data-stu-id="08e2c-146">If you're using raw XML instead of the Notifications library, here's the XML.</span></span>

```xml
<tile>
  <visual arguments="action=storyClicked&amp;story=201c9b1">
 
    <binding template="TileMedium">
       
      <text>Kitten learns how to drive a car...</text>
      ... (omitted)
     
    </binding>
 
    <binding template="TileWide">
      ... (same as Medium)
    </binding>
     
    <!--Large tile is an aggregate of multiple stories-->
    <binding
      template="TileLarge"
      arguments="action=storiesClicked&amp;story=43f939ag&amp;story=201c9b1&amp;story=d9481ca">
   
      <text>Can your dog understand what you're saying?</text>
      ... (another story)
      ... (one more story)
   
    </binding>
 
  </visual>
</tile>
```



## <a name="related-articles"></a><span data-ttu-id="08e2c-147">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="08e2c-147">Related articles</span></span>

- [<span data-ttu-id="08e2c-148">LaunchActivatedEventArgs.TileActivatedInfo-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="08e2c-148">LaunchActivatedEventArgs.TileActivatedInfo property</span></span>](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.launchactivatedeventargs#Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_TileActivatedInfo_)
- [<span data-ttu-id="08e2c-149">TileActivatedInfo-Klasse</span><span class="sxs-lookup"><span data-stu-id="08e2c-149">TileActivatedInfo class</span></span>](https://docs.microsoft.com/uwp/api/windows.applicationmodel.activation.tileactivatedinfo)