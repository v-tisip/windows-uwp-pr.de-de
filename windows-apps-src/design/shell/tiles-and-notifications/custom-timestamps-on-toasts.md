---
author: andrewleader
Description: Learn how to use custom timestamps on your toast notifications.
title: Popup mit benutzerdefiniertem Zeitstempel
label: Custom timestamps on toasts
template: detail.hbs
ms.author: mijacobs
ms.date: 12/15/2017
ms.topic: article
keywords: Windows10, UWP, Popup, benutzerdefinierte Zeitstempel, Zeitstempel, Benachrichtigungen, Info-Center
ms.localizationpriority: medium
ms.openlocfilehash: 290825fa079052b79fb2feaec8af928f8da93f95
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7291436"
---
# <a name="custom-timestamps-on-toasts"></a><span data-ttu-id="1f72d-103">Popup mit benutzerdefiniertem Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="1f72d-103">Custom timestamps on toasts</span></span>

<span data-ttu-id="1f72d-104">Standardmäßig wird der Zeitstempel in Popupbenachrichtigungen (im Info-Center sichtbar) auf die Zeit festgelegt, an der die Benachrichtigung gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="1f72d-104">By default, the timestamp on toast notifications (visible within Action Center) is set to the time that the notification was sent.</span></span>

<img alt="Toast with custom timestamp" src="images/toast-customtimestamp.jpg" width="396"/>

<span data-ttu-id="1f72d-105">Sie können optional den Zeitstempel durch Ihr eigenes benutzerdefiniertes Datum und Uhrzeit überschreiben, sodass der Zeitstempel die Zeit darstellt, zu der die Meldung/Informationen/Inhalt erstellt wurde, anstatt der Zeit, zu der die Benachrichtigung gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="1f72d-105">You can optionally override the timestamp with your own custom date and time, so that the timestamp represents the time the message/information/content was actually created, rather than the time that the notification was sent.</span></span> <span data-ttu-id="1f72d-106">Dadurch wird auch sichergestellt, dass Ihre Benachrichtigungen in der richtigen Reihenfolge im Info-Center angezeigt werden (nach Zeit sortiert).</span><span class="sxs-lookup"><span data-stu-id="1f72d-106">This also ensures that your notifications appear in the correct order within Action Center (which are sorted by time).</span></span> <span data-ttu-id="1f72d-107">Es wird empfohlen, dass die meisten Apps einen benutzerdefinierten Zeitstempel angeben.</span><span class="sxs-lookup"><span data-stu-id="1f72d-107">We recommend that most apps specify a custom timestamp.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f72d-108">**Erfordert Creators Update und 1.4.0 der Benachrichtigungsbibliothek**: Sie müssen Build 15063 oder höher ausführen, um benutzerdefinierte Zeitstempel zu sehen.</span><span class="sxs-lookup"><span data-stu-id="1f72d-108">**Requires Creators Update and 1.4.0 of Notifications library**: You must be running build 15063 or higher to see custom timestamps.</span></span> <span data-ttu-id="1f72d-109">Sie müssen Version 1.4.0 oder höher der [UWP Community Toolkit Benachrichtigungen NuGet-Bibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)verwenden, um Zeitstempel auf Popup-Inhalte anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="1f72d-109">You must use version 1.4.0 or higher of the [UWP Community Toolkit Notifications NuGet library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) to assign the timestamp on your toast's content.</span></span>

<span data-ttu-id="1f72d-110">Um einen benutzerdefinierten Zeitstempel zu verwenden, weisen Sie einfach die **DisplayTimestamp**-Eigenschaft auf Ihren **ToastContent** zu.</span><span class="sxs-lookup"><span data-stu-id="1f72d-110">To use a custom timestamp, simply assign the **DisplayTimestamp** property on your **ToastContent**.</span></span>

```csharp
ToastContent toastContent = new ToastContent()
{
    DisplayTimestamp = new DateTime(2017, 04, 15, 19, 45, 00, DateTimeKind.Utc),
    ...
};
```

```xml
<toast displayTimestamp="2017-04-15T19:45:00Z">
  ...
</toast>
```

<span data-ttu-id="1f72d-111">Wenn Sie XML verwenden, muss das Datum nach [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) formatiert sein.</span><span class="sxs-lookup"><span data-stu-id="1f72d-111">If you are using XML, the date must be formatted in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601).</span></span>

> [!NOTE]
> <span data-ttu-id="1f72d-112">Sie können nur maximal 3 Dezimalstellen pro Sekunden verwenden (obwohl diese Details realistisch gesehen unwichtig sind).</span><span class="sxs-lookup"><span data-stu-id="1f72d-112">You can only use at most 3 decimal places on the seconds (although realistically there's no value in providing anything that granular).</span></span> <span data-ttu-id="1f72d-113">Wenn Sie mehr bereitstellen, wird die Nutzlast ungültig, und Sie erhalten die Benachrichtigung "neue Benachrichtigung".</span><span class="sxs-lookup"><span data-stu-id="1f72d-113">If you provide more, the payload will be invalid and you will receive the "New notification" notification.</span></span>


## <a name="usage-guidance"></a><span data-ttu-id="1f72d-114">Informationen zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="1f72d-114">Usage guidance</span></span>

<span data-ttu-id="1f72d-115">Es wird generell empfohlen, dass die meisten Apps einen benutzerdefinierten Zeitstempel angeben.</span><span class="sxs-lookup"><span data-stu-id="1f72d-115">In general, we recommend that most apps specify a custom timestamp.</span></span> <span data-ttu-id="1f72d-116">Dadurch wird sichergestellt, dass der Zeitstempel der Benachrichtigung das exakte Erstellen der Nachricht/Informationen/Inhalt angibt, unabhängig von Verzögerungen im Netzwerk, Flugzeugmodus oder der festen Intervallen von regelmäßigen Hintergrundaufgaben.</span><span class="sxs-lookup"><span data-stu-id="1f72d-116">This ensures that the notification's timestamp accurately represents when the message/information/content was generated, regardless of network delays, airplane mode, or the fixed interval of periodic background tasks.</span></span>

<span data-ttu-id="1f72d-117">Eine Nachrichten-App kann z. B. eine Hintergrundaufgabe alle 15Minuten ausführen, die nach neuen Artikeln sucht und Benachrichtigungen anzeigt.</span><span class="sxs-lookup"><span data-stu-id="1f72d-117">For example, a news app might run a background task every 15 minutes that checks for new articles and displays notifications.</span></span> <span data-ttu-id="1f72d-118">Vor benutzerdefinierten Zeitstempeln entsprach der Zeitstempel dem Moment, wenn die Popupbenachrichtigung generiert wurde (daher ist der Intervall alle 15 Minuten).</span><span class="sxs-lookup"><span data-stu-id="1f72d-118">Before custom timestamps, the timestamp corresponded to when the toast notification was generated (therefore always in 15 minute intervals).</span></span> <span data-ttu-id="1f72d-119">Jetzt kann die App jedoch den Zeitstempel auf die Zeit festlegen, an der der Artikel tatsächlich veröffentlicht wurde.</span><span class="sxs-lookup"><span data-stu-id="1f72d-119">However, now the app can set the timestamp to the time the article was actually published.</span></span> <span data-ttu-id="1f72d-120">Auf ähnliche Weise können E-Mail-Apps und soziale Netzwerk-Apps von dieser Funktion profitieren, wenn ein ähnliches Muster mit regelmäßigem Ziehen für ihre Benachrichtigungen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1f72d-120">Similarly, email apps and social network apps can benefit from this feature if a similar pattern of periodic pulling is used for their notifications.</span></span>

<span data-ttu-id="1f72d-121">Durch das Bereitstellen eines benutzerdefinierten Zeitstempels wird außerdem sichergestellt, dass der Zeitstempel richtig ist, auch wenn der Benutzer vom Internet getrennt wurde.</span><span class="sxs-lookup"><span data-stu-id="1f72d-121">Additionally, providing a custom timestamp ensures that the timestamp is correct even if the user was disconnected from the internet.</span></span> <span data-ttu-id="1f72d-122">Wenn der Benutzer seinen Computer einschaltet und die Hintergrundaufgabe ausgeführt wird, stellt der Zeitstempel Ihrer Benachrichtigungen die Zeit dar, als der Benutzer die Benachrichtigung gesendet hat, anstatt dem Einschalten des Computers.</span><span class="sxs-lookup"><span data-stu-id="1f72d-122">For example, when the user turns their computer on and your background task runs, you can finally ensure that the timestamp on your notifications represents the time that the messages were sent, rather than the time the user turned on their computer.</span></span>


## <a name="default-timestamp"></a><span data-ttu-id="1f72d-123">Standard-Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="1f72d-123">Default timestamp</span></span>

<span data-ttu-id="1f72d-124">Wenn Sie keinen benutzerdefinierten Zeitstempel bereitstellen, verwenden wir die Zeit, zu der die Benachrichtigung gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="1f72d-124">If you don't provide a custom timestamp, we use the time that your notification was sent.</span></span>

<span data-ttu-id="1f72d-125">Wenn Sie eine Pushbenachrichtigungen über WNS senden, verwenden wir die Zeit, zu der die Benachrichtigung vom WNS-Server empfangen wurde, (damit eine Verzögerung der Benachrichtigung den Zeitstempel auf dem Gerät nicht beeinträchtigt).</span><span class="sxs-lookup"><span data-stu-id="1f72d-125">If you sent a push notification through WNS, we use the time when the notification was received by WNS server (so any latency on delivering the notification to the device won't impact the timestamp).</span></span>

<span data-ttu-id="1f72d-126">Wenn Sie eine lokale Benachrichtigung senden, verwenden wir die Uhrzeit, zu der die Benachrichtigungsplattform die Benachrichtigung erhalten hat (die sofort sein sollte).</span><span class="sxs-lookup"><span data-stu-id="1f72d-126">If you sent a local notification, we use the time when the notification platform received the notification (which should be immediately).</span></span>


## <a name="related-topics"></a><span data-ttu-id="1f72d-127">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1f72d-127">Related topics</span></span>

- [<span data-ttu-id="1f72d-128">Lokale Popups senden</span><span class="sxs-lookup"><span data-stu-id="1f72d-128">Send a local toast</span></span>](send-local-toast.md)
- [<span data-ttu-id="1f72d-129">Dokumentation zu Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="1f72d-129">Toast content documentation</span></span>](adaptive-interactive-toasts.md)