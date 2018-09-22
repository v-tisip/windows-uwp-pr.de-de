---
author: andrewleader
Description: Learn how to create multi-step interactions in your notifications.
title: Popups mit ausstehenden Updates in Aktion
label: Toast with pending update activation
template: detail.hbs
ms.author: mijacobs
ms.date: 12/14/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Popup, ausstehende Updates, ausstehendes Update, Interaktivität aus mehreren Schritten, Interaktivitäten aus mehreren Schritten
ms.localizationpriority: medium
ms.openlocfilehash: f5efccbb73758d0e6541e59812801c22a22c87b5
ms.sourcegitcommit: a160b91a554f8352de963d9fa37f7df89f8a0e23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4121863"
---
# <a name="toast-with-pending-update-activation"></a><span data-ttu-id="96c04-103">Popups mit ausstehenden Updates in Aktion</span><span class="sxs-lookup"><span data-stu-id="96c04-103">Toast with pending update activation</span></span>

<span data-ttu-id="96c04-104">Verwenden Sie das **PendingUpdate** zum Erstellen der Interaktivität aus mehreren Schritten innerhalb Ihrer Popups.</span><span class="sxs-lookup"><span data-stu-id="96c04-104">You can use **PendingUpdate** to create multi-step interactions in your toast notifications.</span></span> <span data-ttu-id="96c04-105">Beispielsweise können Sie, wie unten dargestellt, eine Reihe von Popups erstellen, deren Antworten von den vorherigen Popups der nachfolgenden Popupbenachrichtigungen abhängt.</span><span class="sxs-lookup"><span data-stu-id="96c04-105">For example, as seen below, you can create a series of toasts where the subsequent toasts depend on responses from the previous toasts.</span></span>

![Popup mit ausstehendem Update](images/toast-pendingupdate.gif)

> [!IMPORTANT]
> <span data-ttu-id="96c04-107">**Erfordert Desktop Creators Update und 2.0.0 der Benachrichtigungsbibliothek**: Sie müssen Desktop Build 16299 oder höher ausführen, um ausstehende Updates zu sehen.</span><span class="sxs-lookup"><span data-stu-id="96c04-107">**Requires Desktop Fall Creators Update and 2.0.0 of Notifications library**: You must be running Desktop build 16299 or higher to see pending update work.</span></span> <span data-ttu-id="96c04-108">Sie müssen Version 2.0.0 oder höher der [UWP Community Toolkit Benachrichtigungen NuGet-Bibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) verwenden, um **PendingUpdate** auf Ihre Schaltflächen anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="96c04-108">You must use version 2.0.0 or higher of the [UWP Community Toolkit Notifications NuGet library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) to assign **PendingUpdate** on your buttons.</span></span> <span data-ttu-id="96c04-109">**PendingUpdate** wird nur auf Desktop unterstützt und auf anderen Geräten ignoriert.</span><span class="sxs-lookup"><span data-stu-id="96c04-109">**PendingUpdate** is only supported on Desktop and will be ignored on other devices.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="96c04-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="96c04-110">Prerequisites</span></span>

<span data-ttu-id="96c04-111">Dieser Artikel erfordert Grundkenntnisse in...</span><span class="sxs-lookup"><span data-stu-id="96c04-111">This article assumes a working knowledge of...</span></span>

- [<span data-ttu-id="96c04-112">Erstellen von Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="96c04-112">Constructing toast content</span></span>](adaptive-interactive-toasts.md)
- [<span data-ttu-id="96c04-113">Senden von Popups und behandeln der Hintergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="96c04-113">Sending a toast and handling background activation</span></span>](send-local-toast.md)


## <a name="overview"></a><span data-ttu-id="96c04-114">Übersicht</span><span class="sxs-lookup"><span data-stu-id="96c04-114">Overview</span></span>

<span data-ttu-id="96c04-115">Um ein Popup zu implementieren, das „ausstehende Updates” als Verhalten nach der Aktivierung verwendet...</span><span class="sxs-lookup"><span data-stu-id="96c04-115">To implement a toast that uses pending update as its after activation behavior...</span></span>

1. <span data-ttu-id="96c04-116">Geben Sie auf den Schaltflächen für die Hintergrundaktivierung ein **AfterActivationBehavior** des **PendingUpdate** an</span><span class="sxs-lookup"><span data-stu-id="96c04-116">On your toast background activation buttons, specify an **AfterActivationBehavior** of **PendingUpdate**</span></span>

2. <span data-ttu-id="96c04-117">Weisen Sie beim Senden Ihrer Popups einen **Tag** (und optional eine **Gruppe**) hinzu</span><span class="sxs-lookup"><span data-stu-id="96c04-117">Assign a **Tag** (and optionally **Group**) when sending your toast</span></span>

3. <span data-ttu-id="96c04-118">Wenn der Benutzer die Schaltfläche anklickt, wird die Hintergrundaufgabe aktiviert und das Popup auf dem Bildschirm in einem Zustand des ausstehenden Updates beibehalten</span><span class="sxs-lookup"><span data-stu-id="96c04-118">When the user clicks your button, your background task will be activated, and the toast will be kept on-screen in a pending update state</span></span>

4. <span data-ttu-id="96c04-119">Senden Sie in Ihrer Hintergrundaufgabe eine neue Popupbenachrichtigung mit dem neuen Inhalt, mit dem gleichen **Tag** und der **Gruppe**</span><span class="sxs-lookup"><span data-stu-id="96c04-119">In your background task, send a new toast with your new content, using the same **Tag** and **Group**</span></span>


## <a name="assign-pendingupdate"></a><span data-ttu-id="96c04-120">Zuweisen von PendingUpdate</span><span class="sxs-lookup"><span data-stu-id="96c04-120">Assign PendingUpdate</span></span>

<span data-ttu-id="96c04-121">Setzen Sie auf den Schaltflächen für die Hintergrundaktivierung das **AfterActivationBehavior** auf **PendingUpdate**.</span><span class="sxs-lookup"><span data-stu-id="96c04-121">On your background activation buttons, set the **AfterActivationBehavior** to **PendingUpdate**.</span></span> <span data-ttu-id="96c04-122">Beachten Sie, dass dies nur für Schaltflächen funktioniert, die einen **ActivationType** im **Hintergrund** habe.</span><span class="sxs-lookup"><span data-stu-id="96c04-122">Note that this only works for buttons that have an **ActivationType** of **Background**.</span></span>

```csharp
new ToastButton("Yes", "action=orderLunch")
{
    ActivationType = ToastActivationType.Background,

    ActivationOptions = new ToastActivationOptions()
    {
        AfterActivationBehavior = ToastAfterActivationBehavior.PendingUpdate
    }
}
```

```xml
<action
    content='Yes'
    arguments='action=orderLunch'
    activationType='background'
    afterActivationBehavior='pendingUpdate' />
```


## <a name="use-a-tag-on-the-notification"></a><span data-ttu-id="96c04-123">Verwenden Sie ein Tag auf der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="96c04-123">Use a Tag on the notification</span></span>

<span data-ttu-id="96c04-124">Um die Benachrichtigung später zu ersetzen, müssen wir den **Tag** (und optional die **Gruppe**) auf die Benachrichtigung zuweisen.</span><span class="sxs-lookup"><span data-stu-id="96c04-124">In order to later replace the notification, we have to assign the **Tag** (and optionally the **Group**) on the notification.</span></span>

```csharp
// Create the notification
var notif = new ToastNotification(content.GetXml())
{
    Tag = "lunch"
};

// And show it
ToastNotificationManager.CreateToastNotifier().Show(notif);
```


## <a name="replace-the-toast-with-new-content"></a><span data-ttu-id="96c04-125">Ersetzen Sie das Popup mit neuem Inhalt</span><span class="sxs-lookup"><span data-stu-id="96c04-125">Replace the toast with new content</span></span>

<span data-ttu-id="96c04-126">Wenn der Benutzer auf die Schaltfläche klickt, wird die Hintergrundaufgabe ausgelöst, und das Popup muss durch neuen Inhalt ersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="96c04-126">In response to the user clicking your button, your background task gets triggered and you need to replace the toast with new content.</span></span> <span data-ttu-id="96c04-127">Ersetzen Sie das Popup durch Senden einer neuen Popupbenachrichtigung mit den gleichen **Tag** und der gleichen **Gruppe**.</span><span class="sxs-lookup"><span data-stu-id="96c04-127">You replace the toast by simply sending a new toast with the same **Tag** and **Group**.</span></span>

<span data-ttu-id="96c04-128">Es wird dringend empfohlen, als Antwort auf eine angeklickte Schaltfläche die **Audiowiedergabe auf lautlos festzulegen**, da der Benutzer bereits mit Ihrem Popup interagiert.</span><span class="sxs-lookup"><span data-stu-id="96c04-128">We strongly recommend **setting the audio to silent** on replacements in response to a button click, since the user is already interacting with your toast.</span></span>

```csharp
// Generate new content
ToastContent content = new ToastContent()
{
    ...

    // We disable audio on all subsequent toasts since they appear right after the user
    // clicked something, so the user's attention is already captured
    Audio = new ToastAudio() { Silent = true }
};

// Create the new notification
var notif = new ToastNotification(content.GetXml())
{
    Tag = "lunch"
};

// And replace the old one with this one
ToastNotificationManager.CreateToastNotifier().Show(notif);
```


## <a name="related-topics"></a><span data-ttu-id="96c04-129">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="96c04-129">Related topics</span></span>

- [<span data-ttu-id="96c04-130">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="96c04-130">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/quickstart-toast-pending-update)
- [<span data-ttu-id="96c04-131">Senden einer lokalen Popupbenachrichtigung und Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="96c04-131">Send a local toast and handle activation</span></span>](send-local-toast.md)
- [<span data-ttu-id="96c04-132">Dokumentation zu Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="96c04-132">Toast content documentation</span></span>](adaptive-interactive-toasts.md)
- [<span data-ttu-id="96c04-133">Popup-Statusanzeige</span><span class="sxs-lookup"><span data-stu-id="96c04-133">Toast progress bar</span></span>](toast-progress-bar.md)