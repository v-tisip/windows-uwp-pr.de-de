---
author: andrewleader
Description: Learn how to use notification mirroring on your toast notifications.
title: Spiegelung der Benachrichtigung
label: Notification mirroring
template: detail.hbs
ms.author: mijacobs
ms.date: 12/15/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Popup, Info-Center in der Cloud, Spiegelung der Benachrichtigung, Benachrichtigung, geräteübergreifend
ms.localizationpriority: medium
ms.openlocfilehash: eb8e2ceb16add551f3c8e3a71a69d36b99f21c62
ms.sourcegitcommit: d10fb9eb5f75f2d10e1c543a177402b50fe4019e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "4567690"
---
# <a name="notification-mirroring"></a><span data-ttu-id="1f620-103">Spiegelung der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="1f620-103">Notification mirroring</span></span>

<span data-ttu-id="1f620-104">Mit der Spiegelung der Benachrichtigung, die vom Info-Center in der Cloud unterstützt wird, können Sie auf Ihrem Telefon Benachrichtigungen auf Ihrem PC anzeigen.</span><span class="sxs-lookup"><span data-stu-id="1f620-104">Notification mirroring, powered by Action Center in the Cloud, allows you to see your phone's notifications on your PC.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f620-105">**Benötigt Anniversary Update**: Sie müssen Build 14393 oder höher ausführen, um die Spiegelung der Benachrichtigung verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="1f620-105">**Requires Anniversary Update**: You must be running build 14393 or higher to see notification mirroring work.</span></span> <span data-ttu-id="1f620-106">Wenn Sie die Spiegelung der Benachrichtigung aus Ihrer App entfernen möchten, müssen Sie als Ziel die SDK-Version 14393 für den Zugriff auf die gespiegelten APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="1f620-106">If you would like to opt your app out of notification mirroring, you must target SDK 14393 to access the mirroring APIs.</span></span>

<span data-ttu-id="1f620-107">Benutzer können mit der Spiegelung Benachrichtigung und Cortana Handy-Benachrichtigungen empfangen und darauf reagieren (Windows Mobile und Android) und zwar bequem von ihrem PC aus.</span><span class="sxs-lookup"><span data-stu-id="1f620-107">With notification mirroring and Cortana, users can receive and act on their phone's notifications (Windows Mobile and Android) from the convenience of their PC.</span></span> <span data-ttu-id="1f620-108">Als Entwickler müssen Sie nichts unternehmen, um Benachrichtigung der Spiegelung zu aktivieren, die Spiegelung funktioniert automatisch!</span><span class="sxs-lookup"><span data-stu-id="1f620-108">As a developer, you don't have to do anything to enable notification mirroring, mirroring automatically works!</span></span> <span data-ttu-id="1f620-109">Wenn Sie Schaltflächen auf dem gespiegelten Popup anklicken, z. B. Schnellantworten, werden diese zurück an das Telefon geleitet, und rufen eine Hintergrundaufgabe hervor oder starten die Vordergrund-App.</span><span class="sxs-lookup"><span data-stu-id="1f620-109">Clicking buttons on the mirrored toast, like message quick replies, will be routed back to the phone, invoking you background task or launching your foreground app.</span></span>

<img alt="Notification mirroring diagram" src="images/toast-mirroring.gif" width="350"/>

<span data-ttu-id="1f620-110">Entwickler haben zwei Vorteile von Spiegelung der Benachrichtigung: die gespiegelten Benachrichtigungen führen weitere Nutzer an Ihren Dienst, und darüber hinaus ermöglichen Sie Benutzern, Ihre Microsoft Store-desktop-app zu entdecken!</span><span class="sxs-lookup"><span data-stu-id="1f620-110">Developers get two great benefits from notification mirroring: The mirrored notifications result in more user engagement with your service, and they also help users discover your Microsoft Store desktop app!</span></span> <span data-ttu-id="1f620-111">Ihre Benutzer wissen möglicherweise nicht einmal, was für eine bemerkenswerte UWP-App für ihren Windows10-Desktop verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="1f620-111">Your users might not even know that you have an awesome UWP app available for their Windows 10 desktop.</span></span> <span data-ttu-id="1f620-112">Wenn Benutzer die gespiegelte Benachrichtigung auf dem Handy empfangen, können Benutzer klicken Sie auf die Popupbenachrichtigung, die an den Microsoft Store ausgeführt werden, in denen sie Ihre UWP-desktop-app installieren können.</span><span class="sxs-lookup"><span data-stu-id="1f620-112">When users receive the mirrored notification from their phone, users can click the toast notification to be taken to the Microsoft Store, where they can install your UWP desktop app.</span></span>

<span data-ttu-id="1f620-113">Die Spiegelung funktioniert mit den Windows Phone und Android.</span><span class="sxs-lookup"><span data-stu-id="1f620-113">Mirroring works with both Windows Phone and Android.</span></span> <span data-ttu-id="1f620-114">Benutzer müssen bei Cortana und auf ihrem Handy und dem Desktop angemeldet sein, damit die Spiegelung der Benachrichtigung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="1f620-114">Users need to be logged into Cortana on both their phone and desktop for notification mirroring to work.</span></span>


## <a name="what-if-the-app-is-installed-on-both-devices"></a><span data-ttu-id="1f620-115">Was geschieht, wenn die App auf beiden Geräten installiert ist?</span><span class="sxs-lookup"><span data-stu-id="1f620-115">What if the app is installed on both devices?</span></span>

<span data-ttu-id="1f620-116">Wenn der Benutzer Ihre App bereits auf dem PC installiert hat, werden wir die gespiegelte Phone-Benachrichtigung automatisch stumm schalten, damit keine doppelte Benachrichtigung nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1f620-116">If the user already has your app on their PC, we will automatically mute the mirrored phone notification so that they don't see duplicate notifications.</span></span> <span data-ttu-id="1f620-117">Gespiegelte Benachrichtigungen werden automatisch anhand der folgenden Kriterien stummgeschaltet...</span><span class="sxs-lookup"><span data-stu-id="1f620-117">Mirrored notifications will be auto-muted based on the following criteria...</span></span>

1. <span data-ttu-id="1f620-118">Eine App auf dem PC existiert entweder mit dem **gleichen Anzeigenamen oder dem gleichen PFN** (Paketfamilienname)</span><span class="sxs-lookup"><span data-stu-id="1f620-118">An app on the PC exists with either the **same display name or the same PFN** (Package Family Name)</span></span>
2. <span data-ttu-id="1f620-119">Diese PC-App hat eine Popupbenachrichtigung gesendet.</span><span class="sxs-lookup"><span data-stu-id="1f620-119">That PC app has sent a toast notification</span></span>

<span data-ttu-id="1f620-120">Wenn die PC-App noch kein Popup gesendet hat, zeigen wir weiterhin die Phone-Benachrichtigungen, dass sind, da der Benutzer wahrscheinlich die PC-App noch nicht gestartet hat.</span><span class="sxs-lookup"><span data-stu-id="1f620-120">If the PC app hasn't sent a toast yet, we'll still show the phone notifications, since chances are, the user hasn't actually launched the PC app yet).</span></span>


## <a name="how-to-opt-out-of-mirroring"></a><span data-ttu-id="1f620-121">Deaktivieren der Spiegelung</span><span class="sxs-lookup"><span data-stu-id="1f620-121">How to opt out of mirroring</span></span>

<span data-ttu-id="1f620-122">UWP-App-Entwickler, Unternehmen und Benutzer können die Benachrichtigung der Spiegelung deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="1f620-122">UWP app developers, enterprises, and users can choose to disable notification mirroring.</span></span>

> [!NOTE]
> <span data-ttu-id="1f620-123">Das Deaktivieren der Spiegelung deaktiviert außerdem [Universal Dismiss](universal-dismiss.md).</span><span class="sxs-lookup"><span data-stu-id="1f620-123">Disabling mirroring will also disable [Universal Dismiss](universal-dismiss.md).</span></span>


### <a name="as-a-developer-opt-out-an-individual-notification"></a><span data-ttu-id="1f620-124">Deaktivieren Sie als Entwickler eine einzelne Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="1f620-124">As a developer, opt out an individual notification</span></span>

<span data-ttu-id="1f620-125">Sie haben möglicherweise gelegentlich eine Benachrichtigung für bestimmte Geräte, die nicht auf anderen Geräten gespiegelt werden soll.</span><span class="sxs-lookup"><span data-stu-id="1f620-125">You occasionally might have a device-specific notification that you don't want to be mirrored to other devices.</span></span> <span data-ttu-id="1f620-126">Sie können verhindern, dass eine Benachrichtigung gespiegelt wird, indem Sie die **Spiegelungs**-Eigenschaft für die Popupbenachrichtigung festlegen.</span><span class="sxs-lookup"><span data-stu-id="1f620-126">You can prevent a specific notification from being mirrored by setting the **Mirroring** property on the toast notification.</span></span> <span data-ttu-id="1f620-127">Diese Eigenschaft der Spiegelung kann derzeit nur auf lokale Benachrichtigungen festgelegt werden (es kann nicht angegeben werden, wenn eine WNS-Pushbenachrichtigung gesendet wird).</span><span class="sxs-lookup"><span data-stu-id="1f620-127">Currently, this mirroring property can only be set on local notifications (it can not be specified when sending a WNS push notification).</span></span>

<span data-ttu-id="1f620-128">**Bekanntes Problem**: Das Abrufen der Spiegelungseigenschaften über die `ToastNotificationHistory.GetHistory()`-API gibt immer den Standardwert zurück (**Zugelassen**) und nicht die Option, die Sie angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="1f620-128">**Known Issue**: Retrieving the Mirroring property via the `ToastNotificationHistory.GetHistory()` API's will always return the default value (**Allowed**) rather than the option you specified.</span></span> <span data-ttu-id="1f620-129">Keine Sorge, alles funktioniert – es wird nur der Wert abgerufen, der beschädigt ist.</span><span class="sxs-lookup"><span data-stu-id="1f620-129">Don't worry, everything is functional - it's only retrieving the value that's broken.</span></span>

```csharp
var toast = new ToastNotification(xml)
{
    // Disable mirroring of this notification
    Mirroring = NotificationMirroring.Disabled
};
  
ToastNotificationManager.CreateToastNotifier().Show(toast);
```


### <a name="as-a-developer-opt-out-completely"></a><span data-ttu-id="1f620-130">Als Entwickler sollten Sie diese Option vollkommen ablehnen</span><span class="sxs-lookup"><span data-stu-id="1f620-130">As a developer, opt out completely</span></span>

<span data-ttu-id="1f620-131">Entwickler können die Spiegelung der Benachrichtigung vollständig in der App deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="1f620-131">Some developers might choose to completely opt their app out of notification mirroring.</span></span> <span data-ttu-id="1f620-132">Während wir glauben, dass alle Apps von der Spiegelung profitieren würde, ist ein Deaktivieren ganz einfach. Rufen Sie die folgende Methode nur einmal auf, damit die Option in Ihrer App deaktiviert wird. Sie können z.B. diesen Aufruf im App-Konstruktor in `App.xaml.cs` platzieren...</span><span class="sxs-lookup"><span data-stu-id="1f620-132">While we believe that all apps would benefit from mirroring, we make it easy to opt out. Just call the following method once, and your app will be opted out. For example, you can place this call in your app's constructor inside `App.xaml.cs`...</span></span>

```csharp
public App()
{
    this.InitializeComponent();
    this.Suspending += OnSuspending;
 
    // Disable notification mirroring for entire app
    ToastNotificationManager.ConfigureNotificationMirroring(NotificationMirroring.Disabled);
}
```


### <a name="as-an-enterprise-how-do-i-opt-out"></a><span data-ttu-id="1f620-133">Wie entferne ich die Option als Unternehmen?</span><span class="sxs-lookup"><span data-stu-id="1f620-133">As an enterprise, how do I opt out?</span></span>

<span data-ttu-id="1f620-134">Unternehmen können die Spiegelung der Benachrichtigung vollständig deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="1f620-134">Enterprises can choose to completely disable notification mirroring.</span></span> <span data-ttu-id="1f620-135">Bearbeiten sie einfach die Gruppenrichtlinie, um die zu spiegelnde Benachrichtigungen zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="1f620-135">To do so, they simply edit the Group Policy to turn off notification mirroring.</span></span>


### <a name="as-a-user-how-do-i-opt-out"></a><span data-ttu-id="1f620-136">Wie entferne ich die Option als Benutzer?</span><span class="sxs-lookup"><span data-stu-id="1f620-136">As a user, how do I opt out?</span></span>

<span data-ttu-id="1f620-137">Benutzer können eine einzelne App vollständig deaktivieren, indem Sie das Feature deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="1f620-137">Users are able to opt out on individual apps, or completely opt out by disabling the feature.</span></span> <span data-ttu-id="1f620-138">Wenn keine bestimmten App-Benachrichtigungen auf Ihren Desktop gespiegelt werden sollen, können Sie einfach diese bestimmte App deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="1f620-138">You may not want a specific app's notifications mirrored to your desktop, so you can simply disable that specific app.</span></span> <span data-ttu-id="1f620-139">Diese Optionen finden Sie in den Cortana Einstellungen auf dem Handy und dem PC.</span><span class="sxs-lookup"><span data-stu-id="1f620-139">You can find these options in Cortana's settings on both your phone and PC.</span></span>