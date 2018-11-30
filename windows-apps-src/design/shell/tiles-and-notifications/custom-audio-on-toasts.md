---
Description: Learn how to use custom audio on your toast notifications.
title: Benutzerdefiniertes Audio auf Popups
label: Custom audio on toasts
template: detail.hbs
ms.date: 12/15/2017
ms.topic: article
keywords: Windows10, UWP, Popup, benutzerdefiniertes Audio, Benachrichtigungen, Audio, Sound
ms.localizationpriority: medium
ms.openlocfilehash: 982340901d13f17945c1e7ffa11099f52732f619
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8208703"
---
# <a name="custom-audio-on-toasts"></a><span data-ttu-id="a65aa-103">Benutzerdefiniertes Audio auf Popups</span><span class="sxs-lookup"><span data-stu-id="a65aa-103">Custom audio on toasts</span></span>

<span data-ttu-id="a65aa-104">Popupbenachrichtigungen können benutzerdefiniertes Audio verwenden, wodurch Ihre App Ihrer Marke eindeutige Soundeffekte hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="a65aa-104">Toast notifications can use custom audio, which lets your app express your brand's unique sound effects.</span></span> <span data-ttu-id="a65aa-105">Z.B. kann eine Nachrichten-App ihren eigenen Nachrichten-Sound in deren Popupbenachrichtigungen haben, damit der Benutzer sofort ermitteln kann, dass eine Benachrichtigung von der App erhalten wurde, anstatt die generische Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="a65aa-105">For example, a messaging app can use their own messaging sound on their Toast notifications, so that the user can instantly know that they received a notification from the app, rather than hearing the generic notification sound.</span></span>

## <a name="install-uwp-community-toolkit-nuget-package"></a><span data-ttu-id="a65aa-106">Installieren des UWP Community Toolkit NuGet-Pakets</span><span class="sxs-lookup"><span data-stu-id="a65aa-106">Install UWP Community Toolkit NuGet package</span></span>

<span data-ttu-id="a65aa-107">Um Benachrichtigungen über Code zu erstellen, empfehlen wir die Verwendung der UWP Community Toolkit Benachrichtigungsbibliothek, die ein Objektmodell für die Benachrichtigung von XML-Inhalten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="a65aa-107">In order to create notifications via code, we strongly recommend using the UWP Community Toolkit Notifications library, which provides an object model for the notification XML content.</span></span> <span data-ttu-id="a65aa-108">Sie können die Benachrichtigungs-XML manuell erstellen, jedoch ist diese fehleranfällig und unübersichtlich.</span><span class="sxs-lookup"><span data-stu-id="a65aa-108">You could manually construct the notification XML, but that is error-prone and messy.</span></span> <span data-ttu-id="a65aa-109">Die Benachrichtigungsbibliothek im UWP Community Toolkit wird vom Team erstellt und verwaltet, das die Benachrichtigungen bei Microsoft besitzt.</span><span class="sxs-lookup"><span data-stu-id="a65aa-109">The Notifications library inside UWP Community Toolkit is built and maintained by the team that owns notifications at Microsoft.</span></span>

<span data-ttu-id="a65aa-110">Installieren Sie [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) von NuGet (wir verwenden Version 1.0.0 in dieser Dokumentation).</span><span class="sxs-lookup"><span data-stu-id="a65aa-110">Install [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) from NuGet (we're using version 1.0.0 in this documentation).</span></span>


## <a name="add-namespace-declarations"></a><span data-ttu-id="a65aa-111">Hinzufügen von Namespacedeklarationen</span><span class="sxs-lookup"><span data-stu-id="a65aa-111">Add namespace declarations</span></span>

`Windows.UI.Notifications` <span data-ttu-id="a65aa-112">Enthält die Kachel- und Popup-API.</span><span class="sxs-lookup"><span data-stu-id="a65aa-112">includes the Tile and Toast API's.</span></span> `Microsoft.Toolkit.Uwp.Notifications` <span data-ttu-id="a65aa-113">enthält die Benachrichtigungsbibliothek.</span><span class="sxs-lookup"><span data-stu-id="a65aa-113">includes the Notifications library.</span></span>

```csharp
using Microsoft.Toolkit.Uwp.Notifications;
using Windows.UI.Notifications;
```


## <a name="construct-the-notification"></a><span data-ttu-id="a65aa-114">Erstellen der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="a65aa-114">Construct the notification</span></span>

<span data-ttu-id="a65aa-115">Der Popupbenachrichtigungsinhalt umfasst Text und Bilder, sowie Schaltflächen und Eingaben.</span><span class="sxs-lookup"><span data-stu-id="a65aa-115">The toast notification content includes text and images, and also buttons and inputs.</span></span> <span data-ttu-id="a65aa-116">Weitere Informationen finden Sie unter [lokale Popupbenachrichtigungen senden](send-local-toast.md), um einen vollständigen Codeausschnitt zu sehen.</span><span class="sxs-lookup"><span data-stu-id="a65aa-116">Please see [send local toast](send-local-toast.md) to see a full code snippet.</span></span>

```csharp
ToastContent toastContent = new ToastContent()
{
    Visual = new ToastVisual()
    {
        ... (omitted)
    }
};
```


## <a name="add-the-custom-audio"></a><span data-ttu-id="a65aa-117">Hinzufügen von benutzerdefiniertem Audio</span><span class="sxs-lookup"><span data-stu-id="a65aa-117">Add the custom audio</span></span>

<span data-ttu-id="a65aa-118">Windows Mobile unterstützt jederzeit benutzerdefinierte Audio-Popupbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="a65aa-118">Windows Mobile has always supported custom audio in Toast notifications.</span></span> <span data-ttu-id="a65aa-119">Allerdings wurde dem Desktop die Unterstützung für benutzerdefiniertes Audio erst in Version 1511 (Build 10586) hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a65aa-119">However, Desktop only added support for custom audio in Version 1511 (build 10586).</span></span> <span data-ttu-id="a65aa-120">Wenn Sie eine Popupbenachrichtigung senden, die benutzerdefinierte Audiodaten auf einem Desktopgerät vor der Version 1511 enthält, wird das Popup lautlos ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="a65aa-120">If you send a Toast that contains custom audio to a Desktop device before Version 1511, the toast will be silent.</span></span> <span data-ttu-id="a65aa-121">Aus diesem Grund sollten Sie für Desktop vor der Version 1511 kein benutzerdefiniertes Audio für Ihre Popupbenachrichtigung enthalten, damit die Benachrichtigung mindestens den Standard-Benachrichtigungssound verwenden.</span><span class="sxs-lookup"><span data-stu-id="a65aa-121">Therefore, for Desktop pre-Version 1511, you should NOT include the custom audio in your Toast notification, so that the notification will at least use the default notification sound.</span></span>

<span data-ttu-id="a65aa-122">**Bekanntes Problem**: Wenn Sie Desktop-Version 1511 verwenden, funktioniert die benutzerdefinierte Audiooptionen nur, wenn Ihre App über den Store installiert ist.</span><span class="sxs-lookup"><span data-stu-id="a65aa-122">**Known Issue**: If you're using Desktop Version 1511, the custom toast audio will only work if your app is installed via the Store.</span></span> <span data-ttu-id="a65aa-123">Dies bedeutet, dass die Ihr benutzerdefiniertes Audio vor der Übermittlung an den Store nicht auf Desktop lokal testen können - die Audiowiedergabe funktioniert allerdings einwandfrei nach der Installation aus dem Store.</span><span class="sxs-lookup"><span data-stu-id="a65aa-123">That means you cannot locally test your custom audio on Desktop before submitting to the Store - but the audio will work fine once installed from the Store.</span></span> <span data-ttu-id="a65aa-124">Wir haben dieses Problem im Anniversary Update behoben, damit benutzerdefiniertes Audio über die lokal bereitgestellte App ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="a65aa-124">We fixed this in the Anniversary Update, so that custom audio from your locally deployed app will work correctly.</span></span>

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

<span data-ttu-id="a65aa-125">Dazu gehören folgende Audiodateitypen...</span><span class="sxs-lookup"><span data-stu-id="a65aa-125">Supported audio file types include...</span></span>

- <span data-ttu-id="a65aa-126">.aac</span><span class="sxs-lookup"><span data-stu-id="a65aa-126">.aac</span></span>
- <span data-ttu-id="a65aa-127">.flac</span><span class="sxs-lookup"><span data-stu-id="a65aa-127">.flac</span></span>
- <span data-ttu-id="a65aa-128">.m4a</span><span class="sxs-lookup"><span data-stu-id="a65aa-128">.m4a</span></span>
- <span data-ttu-id="a65aa-129">.mp3</span><span class="sxs-lookup"><span data-stu-id="a65aa-129">.mp3</span></span>
- <span data-ttu-id="a65aa-130">.wav</span><span class="sxs-lookup"><span data-stu-id="a65aa-130">.wav</span></span>
- <span data-ttu-id="a65aa-131">.wma</span><span class="sxs-lookup"><span data-stu-id="a65aa-131">.wma</span></span>


## <a name="send-the-notification"></a><span data-ttu-id="a65aa-132">Senden der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="a65aa-132">Send the notification</span></span>

<span data-ttu-id="a65aa-133">Wenn Ihr Popupinhalt abgeschlossen ist, ist das Senden der Benachrichtigung ganz einfach.</span><span class="sxs-lookup"><span data-stu-id="a65aa-133">Now that your toast content is complete, sending the notification is quite simple.</span></span>

```csharp
// Create the toast notification from the previous toast content
ToastNotification notification = new ToastNotification(toastContent.GetXml());
             
// And then send the toast
ToastNotificationManager.CreateToastNotifier().Show(notification);
```


## <a name="related-topics"></a><span data-ttu-id="a65aa-134">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a65aa-134">Related topics</span></span>

- [<span data-ttu-id="a65aa-135">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a65aa-135">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/quickstart-toast-with-custom-audio)
- [<span data-ttu-id="a65aa-136">Lokale Popups senden</span><span class="sxs-lookup"><span data-stu-id="a65aa-136">Send a local toast</span></span>](send-local-toast.md)
- [<span data-ttu-id="a65aa-137">Dokumentation zu Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="a65aa-137">Toast content documentation</span></span>](adaptive-interactive-toasts.md)