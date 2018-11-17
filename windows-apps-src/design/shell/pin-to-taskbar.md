---
author: mijacobs
Description: You can programmatically pin your app to the taskbar,  bnd you can check if it's currently pinned.
title: Anheften Ihrer App an die Taskleiste
template: detail.hbs
ms.author: mijacobs
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Taskleiste, Taskleiste-Manager an primäre Kachel-Taskleiste anheften
ms.localizationpriority: medium
ms.openlocfilehash: 47fcd1f9d090c49ecbd49e05696b33f789973160
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7167216"
---
# <a name="pin-your-app-to-the-taskbar"></a><span data-ttu-id="e97c9-103">Anheften Ihrer App an die Taskleiste</span><span class="sxs-lookup"><span data-stu-id="e97c9-103">Pin your app to the taskbar</span></span>

<span data-ttu-id="e97c9-104">Sie können Ihrer eigene App programmgesteuert an die Taskleiste anheften und [Ihre App an das Startmenü anheften](tiles-and-notifications/primary-tile-apis.md).</span><span class="sxs-lookup"><span data-stu-id="e97c9-104">You can programmatically pin your own app to the taskbar, just like you can [pin your app to the Start menu](tiles-and-notifications/primary-tile-apis.md).</span></span> <span data-ttu-id="e97c9-105">Sie können ebenfalls überprüfen, ob Ihre App derzeit angeheftet ist, und ob die Taskleiste ein Anheften ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="e97c9-105">And you can check whether your app is currently pinned, and whether the taskbar allows pinning.</span></span> 

![Taskleiste](images/taskbar/taskbar.png)

> [!IMPORTANT]
> <span data-ttu-id="e97c9-107">\*\*\*\* Erfordert das Fall Creators Update: Sie müssen als Ziel Insider SDK 16299 angeben und Insider-Builds 16299 oder höher ausführen, um die Taskleisten-API zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e97c9-107">**Requires Fall Creators Update**: You must target SDK 16299 and be running build 16299 or higher to use the taskbar APIs.</span></span>

> <span data-ttu-id="e97c9-108">**Wichtige APIs**: [TaskbarManager-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager)</span><span class="sxs-lookup"><span data-stu-id="e97c9-108">**Important APIs**: [TaskbarManager class](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager)</span></span> 


## <a name="when-should-you-ask-the-user-to-pin-your-app-to-the-taskbar"></a><span data-ttu-id="e97c9-109">Wenn bitten Sie den Benutzer Ihre App an die Taskleiste anzuheften?</span><span class="sxs-lookup"><span data-stu-id="e97c9-109">When should you ask the user to pin your app to the taskbar?</span></span> 

<span data-ttu-id="e97c9-110">Mit der [TaskbarManager-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager) können Sie die Benutzer auffordern, Ihre App an die Taskleiste anzuheften; der Benutzer muss die Anforderung genehmigen.</span><span class="sxs-lookup"><span data-stu-id="e97c9-110">The [TaskbarManager class](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager) lets you ask the user to pin your app to the taskbar; the user must approve the request.</span></span> <span data-ttu-id="e97c9-111">Sie haben unter großem Aufwand eine herausragende App erstellt und haben jetzt die Möglichkeit, den Benutzer aufzufordern, diese an die Taskleiste anzuheften.</span><span class="sxs-lookup"><span data-stu-id="e97c9-111">You put a lot of effort into building a stellar app, and now you have the opportunity to ask the user to pin it to taskbar.</span></span> <span data-ttu-id="e97c9-112">Bevor wir uns den Code genauer ansehen, sollten Sie beim Entwurf der Oberfläche aber noch Folgendes bedenken:</span><span class="sxs-lookup"><span data-stu-id="e97c9-112">But before we dive into the code, here are some things to keep in mind as you are designing your experience:</span></span>

* <span data-ttu-id="e97c9-113">**Wir empfehlen**, eine unterbrechungsfreie und leicht ausblendbare UX in Ihrer App mit dem deutlichen Handlungsaufruf „An Taskleiste anheften“ zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="e97c9-113">**Do** craft a non-disruptive and easily dismissible UX in your app with a clear "Pin to taskbar" call to action.</span></span> <span data-ttu-id="e97c9-114">Verwenden Sie zu diesem Zweck keine Dialogfelder und Flyouts.</span><span class="sxs-lookup"><span data-stu-id="e97c9-114">Avoid using dialogs and flyouts for this purpose.</span></span> 
* <span data-ttu-id="e97c9-115">**Wir empfehlen**, die Vorteile Ihrer App deutlich zu erläutern, bevor Sie den Benutzer auffordern, sie anzuheften.</span><span class="sxs-lookup"><span data-stu-id="e97c9-115">**Do** clearly explain the value of your app before asking the user to pin it.</span></span>
* <span data-ttu-id="e97c9-116">**Wir raten davon ab**, einen Benutzer zum Anheften Ihrer App aufzufordern, wenn die Kachel bereits angeheftet ist oder sie vom Gerät nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="e97c9-116">**Don't** ask a user to pin your app if the tile is already pinned or the device doesn’t support it.</span></span> <span data-ttu-id="e97c9-117">(In diesem Artikel wird erläutert, wie festgelegt wird, ob ein Anheften unterstützt wird oder nicht).</span><span class="sxs-lookup"><span data-stu-id="e97c9-117">(This article explains how to determine whether pinning is supported.)</span></span>
* <span data-ttu-id="e97c9-118">**Wir raten davon ab**, den Benutzer wiederholt zum Anheften Ihrer App aufzufordern (es wird ihm wahrscheinlich lästig).</span><span class="sxs-lookup"><span data-stu-id="e97c9-118">**Don't** repeatedly ask the user to pin your app (they will probably get annoyed).</span></span>
* <span data-ttu-id="e97c9-119">**Wir raten davon ab**, die Anheften-API ohne explizite Benutzerinteraktion aufzurufen, oder wenn die App minimiert/nicht geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="e97c9-119">**Don't** call the pin API without explicit user interaction or when your app is minimized/not open.</span></span>


## <a name="1-check-whether-the-required-apis-exist"></a><span data-ttu-id="e97c9-120">1. Überprüfen Sie, ob die erforderlichen APIs vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="e97c9-120">1. Check whether the required APIs exist</span></span>

<span data-ttu-id="e97c9-121">Wenn Ihre App ältere Versionen von Windows10 unterstützt, müssen Sie überprüfen, ob die TaskbarManager-Klasse verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e97c9-121">If your app supports older versions of Windows 10, you need to check whether the TaskbarManager class is available.</span></span> <span data-ttu-id="e97c9-122">Sie können die [ApiInformation.IsTypePresent Methode](https://docs.microsoft.com/en-us/uwp/api/windows.foundation.metadata.apiinformation#Windows_Foundation_Metadata_ApiInformation_IsTypePresent_System_String_) zur Überprüfung verwenden.</span><span class="sxs-lookup"><span data-stu-id="e97c9-122">You can use the  [ApiInformation.IsTypePresent method](https://docs.microsoft.com/en-us/uwp/api/windows.foundation.metadata.apiinformation#Windows_Foundation_Metadata_ApiInformation_IsTypePresent_System_String_) to perform this check.</span></span> <span data-ttu-id="e97c9-123">Wenn die TaskbarManager-Klasse nicht verfügbar sind, vermeiden Sie, Aufrufe an die APIs durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="e97c9-123">If the TaskbarManager class isn't available, avoid executing any calls to the APIs.</span></span>

```csharp
if (ApiInformation.IsTypePresent("Windows.UI.Shell.TaskbarManager"))
{
    // Taskbar APIs exist!
}

else
{
    // Older version of Windows, no taskbar APIs
}
```


## <a name="2-check-whether-taskbar-is-present-and-allows-pinning"></a><span data-ttu-id="e97c9-124">2. Überprüfen Sie, ob die Taskleiste vorhanden ist und ein Anheften ermöglicht</span><span class="sxs-lookup"><span data-stu-id="e97c9-124">2. Check whether taskbar is present and allows pinning</span></span>

<span data-ttu-id="e97c9-125">UWP-Apps können auf einer Vielzahl von Geräten ausgeführt werden. Nicht alle Geräte unterstützen die Taskleiste.</span><span class="sxs-lookup"><span data-stu-id="e97c9-125">UWP apps can run on a wide variety of devices; not all of them support the taskbar.</span></span> <span data-ttu-id="e97c9-126">Derzeit unterstützen nur Desktop-Geräte die Taskleiste.</span><span class="sxs-lookup"><span data-stu-id="e97c9-126">Right now, only Desktop devices support the taskbar.</span></span> 

<span data-ttu-id="e97c9-127">Auch wenn die Taskleiste verfügbar ist, kann eine Gruppenrichtlinie auf dem Computer des Benutzers das Anheften an die Taskleiste deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="e97c9-127">Even if the taskbar is available, a group policy on the user's machine might disable taskbar pinning.</span></span> <span data-ttu-id="e97c9-128">Bevor Sie versuchen, Ihre App anzuheften, müssen Sie daher überprüfen, ob das Anheften an die Taskleiste unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="e97c9-128">So, before you attempt to pin your app, you need to check whether pinning to the taskbar is supported.</span></span> <span data-ttu-id="e97c9-129">Die [TaskbarManager.IsPinningAllowed-Eigenschaft](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.IsPinningAllowed) gibt „true” zurück, wenn die Taskleiste vorhanden ist ein Anheften ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="e97c9-129">The [TaskbarManager.IsPinningAllowed property](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.IsPinningAllowed) returns true if the taskbar is present and allows pinning.</span></span> 

```csharp
// Check if taskbar allows pinning (Group Policy can disable it, or some device families don't have taskbar)
bool isPinningAllowed = TaskbarManager.GetDefault().IsPinningAllowed;
```

> [!NOTE]
> <span data-ttu-id="e97c9-130">Wenn Sie die App nicht an die Taskleiste anheften möchten und nur wissen möchten, ob die Taskleiste verfügbar ist, verwenden Sie die [TaskbarManager.IsSupported-Eigenschaft](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.IsSupported).</span><span class="sxs-lookup"><span data-stu-id="e97c9-130">If you don't want to pin your app to the taskbar and just want to find out whether the taskbar is available, use the [TaskbarManager.IsSupported property](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.IsSupported).</span></span>


## <a name="3-check-whether-your-app-is-currently-pinned-to-the-taskbar"></a><span data-ttu-id="e97c9-131">3. Überprüfen Sie, ob Ihre App derzeit an die Taskleiste angeheftet ist</span><span class="sxs-lookup"><span data-stu-id="e97c9-131">3. Check whether your app is currently pinned to the taskbar</span></span>

<span data-ttu-id="e97c9-132">Natürlich besteht kein Grund dafür, den Benutzer aufzufordern, die App an die Taskleiste anzuheften, wenn diese bereits angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="e97c9-132">Obviously, there's no point in asking the user to let you pin the app to the taskbar if it's already pinned there.</span></span> <span data-ttu-id="e97c9-133">Verwenden Sie die [TaskbarManager.IsCurrentAppPinnedAsync-Methode](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.IsCurrentAppPinnedAsync), um zu überprüfen, ob die App bereits angeheftet ist, bevor Sie den Benutzer auffordern.</span><span class="sxs-lookup"><span data-stu-id="e97c9-133">You can use the [TaskbarManager.IsCurrentAppPinnedAsync method](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.IsCurrentAppPinnedAsync) to check whether the app is already pinned before asking the user.</span></span>

```csharp
// Check whether your app is currently pinned
bool isPinned = await TaskbarManager.GetDefault().IsCurrentAppPinnedAsync();

if (isPinned)
{
    // The app is already pinned--no point in asking to pin it again!
}
else 
{
    //The app is not pinned. 
}
```


##  <a name="4-pin-your-app"></a><span data-ttu-id="e97c9-134">4. Die App anheften</span><span class="sxs-lookup"><span data-stu-id="e97c9-134">4. Pin your app</span></span>

<span data-ttu-id="e97c9-135">Wenn die Taskleiste vorhanden ist und ein Anheften zugelassen wird und Ihre App derzeit nicht angeheftet ist, sollten Sie einen Tipp anzeigen, damit Benutzer wissen, dass Ihre App angeheftet werden kann.</span><span class="sxs-lookup"><span data-stu-id="e97c9-135">If the taskbar is present and pinning is allowed and your app currently isn't pinned, you might want to show a subtle tip to let users know that they can pin your app.</span></span> <span data-ttu-id="e97c9-136">Sie können Sie z.B. irgendwo ein Pinsymbol in der Benutzeroberfläche anzeigen, das die Benutzer anklicken können.</span><span class="sxs-lookup"><span data-stu-id="e97c9-136">For example, you might show a pin icon somewhere in your UI that the user can click.</span></span> 

<span data-ttu-id="e97c9-137">Wenn der Benutzer auf Ihren Pin-Vorschlag klickt, rufen Sie die [TaskbarManager.RequestPinCurrentAppAsync-Methode](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.RequestPinCurrentAppAsync) auf.</span><span class="sxs-lookup"><span data-stu-id="e97c9-137">If the user clicks your pin suggestion UI, you would then call the [TaskbarManager.RequestPinCurrentAppAsync method](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager.RequestPinCurrentAppAsync).</span></span> <span data-ttu-id="e97c9-138">Diese Methode zeigt ein Dialogfeld an, das den Benutzer auffordert, zu bestätigen, dass sie Ihre App an die Taskleiste anheften möchten.</span><span class="sxs-lookup"><span data-stu-id="e97c9-138">This method displays a dialog that asks the user to confirm that they want your app pinned to the taskbar.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e97c9-139">Dies muss durch einen Vordergrund-UI-Thread aufgerufen werden, andernfalls wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="e97c9-139">This must be called from a foreground UI thread, otherwise an exception will be thrown.</span></span>

```csharp
// Request to be pinned to the taskbar
bool isPinned = await TaskbarManager.GetDefault().RequestPinCurrentAppAsync();
```

![PIN-Dialogfeld](images/taskbar/pin-dialog.png)

<span data-ttu-id="e97c9-141">Diese Methode gibt einen booleschen Wert zurück, der angibt, ob Ihre App jetzt an die Taskleiste angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="e97c9-141">This method returns a boolean value that indicates whether your app is now pinned to the taskbar.</span></span> <span data-ttu-id="e97c9-142">Wenn die App bereits angeheftet war, wird die Methode sofort „true“ zurückgegeben, ohne dass dem Benutzer das Dialogfeld angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e97c9-142">If your app was already pinned, the method immediately returns true without showing the dialog to the user.</span></span> <span data-ttu-id="e97c9-143">Wenn der Benutzer im Dialogfeld auf "Nein" klickt oder Ihre App nicht an die Taskleiste angeheftet werden kann, wird die Methode "false" zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="e97c9-143">If the user clicks "no" on the dialog, or pinning your app to the taskbar isn't allowed, the method returns false.</span></span> <span data-ttu-id="e97c9-144">Andernfalls hat der Benutzer auf „Ja“ geklickt und die App wurde angeheftet, und die API gibt „true“ zurück.</span><span class="sxs-lookup"><span data-stu-id="e97c9-144">Otherwise, the user clicked yes and the app was pinned, and the API will return true.</span></span>


## <a name="resources"></a><span data-ttu-id="e97c9-145">Resources</span><span class="sxs-lookup"><span data-stu-id="e97c9-145">Resources</span></span>

* [<span data-ttu-id="e97c9-146">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="e97c9-146">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/quickstart-pin-to-taskbar)
* [<span data-ttu-id="e97c9-147">TaskbarManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="e97c9-147">TaskbarManager class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.shell.taskbarmanager)
* [<span data-ttu-id="e97c9-148">Anheften einer App an das Startmenü</span><span class="sxs-lookup"><span data-stu-id="e97c9-148">Pin an app to the Start menu</span></span>](tiles-and-notifications/primary-tile-apis.md)