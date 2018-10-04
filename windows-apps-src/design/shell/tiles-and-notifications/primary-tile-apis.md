---
author: andrewleader
Description: You can programmatically pin your own app's primary tile to Start, just like you can pin secondary tiles. And you can check whether it's currently pinned.
title: Primäre Kachel-APIs
label: Primary tile API's
template: detail.hbs
ms.author: wdg-dev-content
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, StartScreenManager, primäre Kachel anheften, primäre Kachel-APIs, überprüfen, ob die Kachel angeheftet ist, Live-Kachel
ms.localizationpriority: medium
ms.openlocfilehash: 42b4c014dfd49c42497b8846e37e37af53cc3885
ms.sourcegitcommit: 5c9a47b135c5f587214675e39c1ac058c0380f4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "4357225"
---
# <a name="primary-tile-apis"></a><span data-ttu-id="799d8-103">Primärkachel-APIs</span><span class="sxs-lookup"><span data-stu-id="799d8-103">Primary tile APIs</span></span>
 

<span data-ttu-id="799d8-104">Mit Primärkachel-APIs können Sie überprüfen, ob die App auf der Startseite angeheftet ist und anfragen, ob Ihre App an die primäre Kachel der App angeheftet werden kann.</span><span class="sxs-lookup"><span data-stu-id="799d8-104">Primary tile APIs let you check whether your app is currently pinned to Start, and request to pin your app's primary tile.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="799d8-105">\*\*\*\* Erfordert das Fall Creators Update: Sie müssen als Ziel Insider SDK 15063 angeben und Insider-Builds 15063 oder höher ausführen, um die Primärkachel-API zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="799d8-105">**Requires Creators Update**: You must target SDK 15063 and be running build 15063 or higher to use the primary tile APIs.</span></span>

> <span data-ttu-id="799d8-106">**Wichtige APIs**: [**StartScreenManager Klasse**](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager), [ContainsAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_ContainsAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_), [RequestAddAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_RequestAddAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_)</span><span class="sxs-lookup"><span data-stu-id="799d8-106">**Important APIs**: [**StartScreenManager class**](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager), [ContainsAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_ContainsAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_), [RequestAddAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_RequestAddAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_)</span></span>


## <a name="when-to-use-primary-tile-apis"></a><span data-ttu-id="799d8-107">Verwendung von Primärkachel-APIs</span><span class="sxs-lookup"><span data-stu-id="799d8-107">When to use primary tile APIs</span></span>

<span data-ttu-id="799d8-108">Sie haben großen Aufwand betrieben, um die primäre Kachel Ihrer App benutzerfreundlich zu gestalten, und jetzt haben Sie die Möglichkeit, den Benutzer aufzufordern, sie an die Startseite anzuheften.</span><span class="sxs-lookup"><span data-stu-id="799d8-108">You put a lot of effort into designing a great experience for your app’s primary tile, and now you have the opportunity to ask the user to pin it to Start.</span></span> <span data-ttu-id="799d8-109">Bevor wir uns den Code genauer ansehen, sollten Sie beim Entwurf der Oberfläche aber noch Folgendes bedenken:</span><span class="sxs-lookup"><span data-stu-id="799d8-109">But before we dive into the code, here are some things to keep in mind as you’re designing your experience:</span></span>

* <span data-ttu-id="799d8-110">**Wir empfehlen**, eine unterbrechungsfreie und leicht ausblendbare UX in Ihrer App mit dem deutlichen Handlungsaufruf „Live-Kachel anheften“ zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="799d8-110">**Do** craft a non-disruptive and easily dismissible UX in your app with a clear "Pin Live Tile" call to action.</span></span>
* <span data-ttu-id="799d8-111">**Wir empfehlen**, die Vorteile der Live-Kachel Ihrer App deutlich zu erläutern, bevor Sie den Benutzer auffordern, sie anzuheften.</span><span class="sxs-lookup"><span data-stu-id="799d8-111">**Do** clearly explain the value of your app’s Live Tile before asking the user to pin it.</span></span>
* <span data-ttu-id="799d8-112">**Wir raten davon ab**, einen Benutzer zum Anheften der Kachel Ihrer App aufzufordern, wenn die Kachel bereits angeheftet ist oder sie vom Gerät nicht unterstützt wird (weitere Informationen folgen).</span><span class="sxs-lookup"><span data-stu-id="799d8-112">**Don't** ask a user to pin your app’s tile if the tile is already pinned or the device doesn’t support it (more info follows).</span></span>
* <span data-ttu-id="799d8-113">**Wir raten davon ab**, den Benutzer wiederholt zum Anheften der Kachel Ihrer App aufzufordern (es wird ihm wahrscheinlich lästig).</span><span class="sxs-lookup"><span data-stu-id="799d8-113">**Don't** repeatedly ask the user to pin your app’s tile (they will probably get annoyed).</span></span>
* <span data-ttu-id="799d8-114">**Wir raten davon ab**, die Anheften-API ohne explizite Benutzerinteraktion aufzurufen, oder wenn die App minimiert/nicht geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="799d8-114">**Don't** call the pin API without explicit user interaction or when your app is minimized/not open.</span></span>


## <a name="checking-whether-the-apis-exist"></a><span data-ttu-id="799d8-115">Überprüfen, ob die APIs vorhanden sind</span><span class="sxs-lookup"><span data-stu-id="799d8-115">Checking whether the API's exist</span></span>

<span data-ttu-id="799d8-116">Wenn Ihre App ältere Versionen von Windows10 unterstützt, müssen Sie überprüfen, ob diese Primärkachel-APIs verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="799d8-116">If your app supports older versions of Windows 10, you need to check whether these primary tile APIs are available.</span></span> <span data-ttu-id="799d8-117">Verwenden Sie dazu ApiInformation.</span><span class="sxs-lookup"><span data-stu-id="799d8-117">You do this by using ApiInformation.</span></span> <span data-ttu-id="799d8-118">Wenn die Primärkachel-APIs nicht verfügbar sind, vermeiden Sie, Aufrufe an die APIs durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="799d8-118">If the primary tile APIs aren't available, avoid executing any calls to the APIs.</span></span>

```csharp
if (ApiInformation.IsTypePresent("Windows.UI.StartScreen.StartScreenManager"))
{
    // Primary tile API's supported!
}
else
{
    // Older version of Windows, no primary tile API's
}
```


## <a name="check-if-start-supports-your-app"></a><span data-ttu-id="799d8-119">Überprüfen, ob Start die App unterstützt</span><span class="sxs-lookup"><span data-stu-id="799d8-119">Check if Start supports your app</span></span>

<span data-ttu-id="799d8-120">Abhängig vom aktuellen Startmenü und dem Typ Ihrer App wird das Anheften Ihrer App an die aktuelle Startseite möglicherweise nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="799d8-120">Depending on the current Start menu, and your type of app, pinning your app to the current Start screen might not be supported.</span></span> <span data-ttu-id="799d8-121">Nur Desktop und Mobile unterstützen das Anheften der primären Kachel an die Startseite.</span><span class="sxs-lookup"><span data-stu-id="799d8-121">Only Desktop and Mobile support pinning the primary tile to Start.</span></span> <span data-ttu-id="799d8-122">Bevor Sie eine Anheften-UI anzeigen oder Anheften-Code ausführen, müssen Sie daher zunächst prüfen, ob Ihre App für die aktuelle Startseite überhaupt unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="799d8-122">Therefore, before showing any pin UI or executing any pin code, you first need to check if your app is even supported for the current Start screen.</span></span> <span data-ttu-id="799d8-123">Wenn sie nicht unterstützt wird, fordern Sie den Benutzer nicht zum Anheften der Kachel auf.</span><span class="sxs-lookup"><span data-stu-id="799d8-123">If it's not supported, don't prompt the user to pin the tile.</span></span>

```csharp
// Get your own app list entry
// (which is always the first app list entry assuming you are not a multi-app package)
AppListEntry entry = (await Package.Current.GetAppListEntriesAsync())[0];

// Check if Start supports your app
bool isSupported = StartScreenManager.GetDefault().SupportsAppListEntry(entry);
```


## <a name="check-whether-youre-currently-pinned"></a><span data-ttu-id="799d8-124">Überprüfen, ob die primäre Kachel derzeit angeheftet ist</span><span class="sxs-lookup"><span data-stu-id="799d8-124">Check whether you're currently pinned</span></span>

<span data-ttu-id="799d8-125">Um festzustellen, ob die primäre Kachel derzeit an die Startseite angeheftet ist, verwenden Sie die Methode [ContainsAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_ContainsAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_).</span><span class="sxs-lookup"><span data-stu-id="799d8-125">To find out if your primary tile is currently pinned to Start, use the [ContainsAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_ContainsAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_) method.</span></span>

```csharp
// Get your own app list entry
AppListEntry entry = (await Package.Current.GetAppListEntriesAsync())[0];

// Check if your app is currently pinned
bool isPinned = await StartScreenManager.GetDefault().ContainsAppListEntryAsync(entry);
```


##  <a name="pin-your-primary-tile"></a><span data-ttu-id="799d8-126">Anheften Ihrer primären Kachel</span><span class="sxs-lookup"><span data-stu-id="799d8-126">Pin your primary tile</span></span>

<span data-ttu-id="799d8-127">Wenn die primäre Kachel aktuell nicht angeheftet ist und die Kachel von der Startseite unterstützt wird, sollten Sie Benutzern den Tipp anzeigen, dass die primäre Kachel angeheftet werden kann.</span><span class="sxs-lookup"><span data-stu-id="799d8-127">If your primary tile currently isn't pinned, and your tile is supported by Start, you might want to show a tip to users that they can pin your primary tile.</span></span>

> [!NOTE]
> <span data-ttu-id="799d8-128">Sie müssen diese API über einen UI-Thread aufrufen, während Ihre App im Vordergrund ausgeführt wird, und Sie sollten diese API erst aufrufen, nachdem der Benutzer das Anheften der primären Kachel explizit angefordert hat (z.B. nachdem der Benutzer in Ihrem Tipp zum Anheften der Kachel auf „Ja“ geklickt hat).</span><span class="sxs-lookup"><span data-stu-id="799d8-128">You must call this API from a UI thread while your app is in the foreground, and you should only call this API after the user has intentionally requested the primary tile be pinned (for example, after the user clicked yes to your tip about pinning the tile).</span></span>

<span data-ttu-id="799d8-129">Klickt der Benutzer auf Ihre Schaltfläche, um die primäre Kachel anzuheften, würden Sie dann die Methode [RequestAddAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_RequestAddAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_) aufrufen, um anzufordern, dass die Kachel an die Startseite angeheftet wird.</span><span class="sxs-lookup"><span data-stu-id="799d8-129">If the user clicks your button to pin the primary tile, you would then call the [RequestAddAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_RequestAddAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_) method to request that your tile be pinned to Start.</span></span> <span data-ttu-id="799d8-130">Dadurch wird ein Dialogfeld angezeigt, das den Benutzer auffordert zu bestätigen, dass Ihre Kachel an die Startseite angeheftet werden soll.</span><span class="sxs-lookup"><span data-stu-id="799d8-130">This will display a dialog asking the user to confirm that they want your tile pinned to Start.</span></span>

<span data-ttu-id="799d8-131">Dadurch wird ein boolescher Wert zurückgegeben, der angibt, ob die Kachel jetzt an die Startseite angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="799d8-131">This will return a boolean representing whether your tile is now pinned to Start.</span></span> <span data-ttu-id="799d8-132">Wenn die Kachel bereits angeheftet war, wird sofort „true“ zurückgegeben, ohne dass dem Benutzer das Dialogfeld angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="799d8-132">If your tile was already pinned, this will immediately return true without showing the dialog to the user.</span></span> <span data-ttu-id="799d8-133">Wenn der Benutzer im Dialogfeld auf „Nein“ klickt oder das Anheften Ihrer Kachel an die Startseite nicht unterstützt wird, wird „false“ zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="799d8-133">If the user clicks no on the dialog, or pinning your tile to Start isn't supported, this will return false.</span></span> <span data-ttu-id="799d8-134">Andernfalls hat der Benutzer auf „Ja“ geklickt und die Kachel wurde angeheftet, und die API gibt „true“ zurück.</span><span class="sxs-lookup"><span data-stu-id="799d8-134">Otherwise, the user clicked yes and the tile was pinned, and the API will return true.</span></span>

```csharp
// Get your own app list entry
AppListEntry entry = (await Package.Current.GetAppListEntriesAsync())[0];

// And pin it to Start
bool isPinned = await StartScreenManager.GetDefault().RequestAddAppListEntryAsync(entry);
```


## <a name="resources"></a><span data-ttu-id="799d8-135">Resources</span><span class="sxs-lookup"><span data-stu-id="799d8-135">Resources</span></span>

* [<span data-ttu-id="799d8-136">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="799d8-136">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/quickstart-pin-primary-tile)
* [<span data-ttu-id="799d8-137">An Taskleiste anheften</span><span class="sxs-lookup"><span data-stu-id="799d8-137">Pin to taskbar</span></span>](../pin-to-taskbar.md)
* [<span data-ttu-id="799d8-138">Kacheln, Badges und Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="799d8-138">Tiles, badges, and notifications</span></span>](index.md)
* [<span data-ttu-id="799d8-139">Dokumentation zu adaptiven Kacheln</span><span class="sxs-lookup"><span data-stu-id="799d8-139">Adaptive Tile Documentation</span></span>](create-adaptive-tiles.md)
