---
author: andrewleader
Description: Learn how to use custom audio on your toast notifications.
title: Benutzerdefiniertes Audio auf Popups
label: Custom audio on toasts
template: detail.hbs
ms.author: mijacobs
ms.date: 12/15/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Popup, benutzerdefiniertes Audio, Benachrichtigungen, Audio, Sound
ms.localizationpriority: medium
ms.openlocfilehash: 24be148340366163fcab00ec75f7f26fac6c2d80
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2018
ms.locfileid: "3928120"
---
# <a name="custom-audio-on-toasts"></a><span data-ttu-id="6c462-103">Benutzerdefiniertes Audio auf Popups</span><span class="sxs-lookup"><span data-stu-id="6c462-103">Custom audio on toasts</span></span>

<span data-ttu-id="6c462-104">Popupbenachrichtigungen können benutzerdefiniertes Audio verwenden, wodurch Ihre App Ihrer Marke eindeutige Soundeffekte hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="6c462-104">Toast notifications can use custom audio, which lets your app express your brand's unique sound effects.</span></span> <span data-ttu-id="6c462-105">Z.B. kann eine Nachrichten-App ihren eigenen Nachrichten-Sound in deren Popupbenachrichtigungen haben, damit der Benutzer sofort ermitteln kann, dass eine Benachrichtigung von der App erhalten wurde, anstatt die generische Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="6c462-105">For example, a messaging app can use their own messaging sound on their Toast notifications, so that the user can instantly know that they received a notification from the app, rather than hearing the generic notification sound.</span></span>

## <a name="install-uwp-community-toolkit-nuget-package"></a><span data-ttu-id="6c462-106">Installieren des UWP Community Toolkit NuGet-Pakets</span><span class="sxs-lookup"><span data-stu-id="6c462-106">Install UWP Community Toolkit NuGet package</span></span>

<span data-ttu-id="6c462-107">Um Benachrichtigungen über Code zu erstellen, empfehlen wir die Verwendung der UWP Community Toolkit Benachrichtigungsbibliothek, die ein Objektmodell für die Benachrichtigung von XML-Inhalten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="6c462-107">In order to create notifications via code, we strongly recommend using the UWP Community Toolkit Notifications library, which provides an object model for the notification XML content.</span></span> <span data-ttu-id="6c462-108">Sie können die Benachrichtigungs-XML manuell erstellen, jedoch ist diese fehleranfällig und unübersichtlich.</span><span class="sxs-lookup"><span data-stu-id="6c462-108">You could manually construct the notification XML, but that is error-prone and messy.</span></span> <span data-ttu-id="6c462-109">Die Benachrichtigungsbibliothek im UWP Community Toolkit wird vom Team erstellt und verwaltet, das die Benachrichtigungen bei Microsoft besitzt.</span><span class="sxs-lookup"><span data-stu-id="6c462-109">The Notifications library inside UWP Community Toolkit is built and maintained by the team that owns notifications at Microsoft.</span></span>

<span data-ttu-id="6c462-110">Installieren Sie [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) von NuGet (wir verwenden Version 1.0.0 in dieser Dokumentation).</span><span class="sxs-lookup"><span data-stu-id="6c462-110">Install [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) from NuGet (we're using version 1.0.0 in this documentation).</span></span>


## <a name="add-namespace-declarations"></a><span data-ttu-id="6c462-111">Hinzufügen von Namespacedeklarationen</span><span class="sxs-lookup"><span data-stu-id="6c462-111">Add namespace declarations</span></span>

`Windows.UI.Notifications` <span data-ttu-id="6c462-112">Enthält die Kachel- und Popup-API.</span><span class="sxs-lookup"><span data-stu-id="6c462-112">includes the Tile and Toast API's.</span></span> `Microsoft.Toolkit.Uwp.Notifications` <span data-ttu-id="6c462-113">enthält die Benachrichtigungsbibliothek.</span><span class="sxs-lookup"><span data-stu-id="6c462-113">includes the Notifications library.</span></span>

```csharp
using Microsoft.Toolkit.Uwp.Notifications;
using Windows.UI.Notifications;
```


## <a name="construct-the-notification"></a><span data-ttu-id="6c462-114">Erstellen der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="6c462-114">Construct the notification</span></span>

<span data-ttu-id="6c462-115">Der Popupbenachrichtigungsinhalt umfasst Text und Bilder, sowie Schaltflächen und Eingaben.</span><span class="sxs-lookup"><span data-stu-id="6c462-115">The toast notification content includes text and images, and also buttons and inputs.</span></span> <span data-ttu-id="6c462-116">Weitere Informationen finden Sie unter [lokale Popupbenachrichtigungen senden](send-local-toast.md), um einen vollständigen Codeausschnitt zu sehen.</span><span class="sxs-lookup"><span data-stu-id="6c462-116">Please see [send local toast](send-local-toast.md) to see a full code snippet.</span></span>

```csharp
ToastContent toastContent = new ToastContent()
{
    Visual = new ToastVisual()
    {
        ... (omitted)
    }
};
```


## <a name="add-the-custom-audio"></a><span data-ttu-id="6c462-117">Hinzufügen von benutzerdefiniertem Audio</span><span class="sxs-lookup"><span data-stu-id="6c462-117">Add the custom audio</span></span>

<span data-ttu-id="6c462-118">Windows Mobile unterstützt jederzeit benutzerdefinierte Audio-Popupbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="6c462-118">Windows Mobile has always supported custom audio in Toast notifications.</span></span> <span data-ttu-id="6c462-119">Allerdings wurde dem Desktop die Unterstützung für benutzerdefiniertes Audio erst in Version 1511 (Build 10586) hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6c462-119">However, Desktop only added support for custom audio in Version 1511 (build 10586).</span></span> <span data-ttu-id="6c462-120">Wenn Sie eine Popupbenachrichtigung senden, die benutzerdefinierte Audiodaten auf einem Desktopgerät vor der Version 1511 enthält, wird das Popup lautlos ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="6c462-120">If you send a Toast that contains custom audio to a Desktop device before Version 1511, the toast will be silent.</span></span> <span data-ttu-id="6c462-121">Aus diesem Grund sollten Sie für Desktop vor der Version 1511 kein benutzerdefiniertes Audio für Ihre Popupbenachrichtigung enthalten, damit die Benachrichtigung mindestens den Standard-Benachrichtigungssound verwenden.</span><span class="sxs-lookup"><span data-stu-id="6c462-121">Therefore, for Desktop pre-Version 1511, you should NOT include the custom audio in your Toast notification, so that the notification will at least use the default notification sound.</span></span>

<span data-ttu-id="6c462-122">**Bekanntes Problem**: Wenn Sie Desktop-Version 1511 verwenden, funktioniert die benutzerdefinierte Audiooptionen nur, wenn Ihre App über den Store installiert ist.</span><span class="sxs-lookup"><span data-stu-id="6c462-122">**Known Issue**: If you're using Desktop Version 1511, the custom toast audio will only work if your app is installed via the Store.</span></span> <span data-ttu-id="6c462-123">Dies bedeutet, dass die Ihr benutzerdefiniertes Audio vor der Übermittlung an den Store nicht auf Desktop lokal testen können - die Audiowiedergabe funktioniert allerdings einwandfrei nach der Installation aus dem Store.</span><span class="sxs-lookup"><span data-stu-id="6c462-123">That means you cannot locally test your custom audio on Desktop before submitting to the Store - but the audio will work fine once installed from the Store.</span></span> <span data-ttu-id="6c462-124">Wir haben dieses Problem im Anniversary Update behoben, damit benutzerdefiniertes Audio über die lokal bereitgestellte App ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="6c462-124">We fixed this in the Anniversary Update, so that custom audio from your locally deployed app will work correctly.</span></span>

```csharp
?
bool supportsCustomAudio = true;
 
// If we're running on Desktop before Version 1511, do NOT include custom audio
// since it was not supported until Version 1511, and would result in a silent toast.
if (AnalyticsInfo.VersionInfo.DeviceFamily.Equals("Windows.Desktop")
    && !ApiInformation.IsApiContractPresent("Windows.Foundation.UniversalApiContract", 2))
{
    supportsCustomAudio = false;
}
 
if (supportsCustomAudio)
{
    toastContent.Audio = new ToastAudio()
    {
        Src = new Uri("ms-appx:///Assets/Audio/CustomToastAudio.m4a")
    };
}
```

<span data-ttu-id="6c462-125">Dazu gehören folgende Audiodateitypen...</span><span class="sxs-lookup"><span data-stu-id="6c462-125">Supported audio file types include...</span></span>

- <span data-ttu-id="6c462-126">.aac</span><span class="sxs-lookup"><span data-stu-id="6c462-126">.aac</span></span>
- <span data-ttu-id="6c462-127">.flac</span><span class="sxs-lookup"><span data-stu-id="6c462-127">.flac</span></span>
- <span data-ttu-id="6c462-128">.m4a</span><span class="sxs-lookup"><span data-stu-id="6c462-128">.m4a</span></span>
- <span data-ttu-id="6c462-129">.mp3</span><span class="sxs-lookup"><span data-stu-id="6c462-129">.mp3</span></span>
- <span data-ttu-id="6c462-130">.wav</span><span class="sxs-lookup"><span data-stu-id="6c462-130">.wav</span></span>
- <span data-ttu-id="6c462-131">.wma</span><span class="sxs-lookup"><span data-stu-id="6c462-131">.wma</span></span>


## <a name="send-the-notification"></a><span data-ttu-id="6c462-132">Senden der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="6c462-132">Send the notification</span></span>

<span data-ttu-id="6c462-133">Wenn Ihr Popupinhalt abgeschlossen ist, ist das Senden der Benachrichtigung ganz einfach.</span><span class="sxs-lookup"><span data-stu-id="6c462-133">Now that your toast content is complete, sending the notification is quite simple.</span></span>

```csharp
// Create the toast notification from the previous toast content
ToastNotification notification = new ToastNotification(toastContent.GetXml());
             
// And then send the toast
ToastNotificationManager.CreateToastNotifier().Show(notification);
```


## <a name="related-topics"></a><span data-ttu-id="6c462-134">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6c462-134">Related topics</span></span>

- [<span data-ttu-id="6c462-135">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="6c462-135">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/quickstart-toast-with-custom-audio)
- [<span data-ttu-id="6c462-136">Lokale Popups senden</span><span class="sxs-lookup"><span data-stu-id="6c462-136">Send a local toast</span></span>](send-local-toast.md)
- [<span data-ttu-id="6c462-137">Dokumentation zu Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="6c462-137">Toast content documentation</span></span>](adaptive-interactive-toasts.md)