---
author: mijacobs
Description: Learn how to use tiles, badges, toasts, and notifications to provide entry points into your app and keep users up-to-date.
title: Signalbenachrichtigungen für UWP-Apps
ms.assetid: 48ee4328-7999-40c2-9354-7ea7d488c538
label: Tiles, badges, and notifications
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 667efeb67c956f8d4378b0e7e4011f7e06977519
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6027740"
---
# <a name="badge-notifications-for-uwp-apps"></a><span data-ttu-id="9011a-103">Signalbenachrichtigungen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="9011a-103">Badge notifications for UWP apps</span></span>

 

<div style="float:left; font-size:80%; text-align:left; margin: 0px 15px 15px 0px;">
<img src="images/badge-example.png" alt="A tile with a numeric badge displaying the number 63 to indicate 63 unread mails." style="padding-bottom:0.0em; margin-bottom: 2px" /><br/><span data-ttu-id="9011a-104">Eine Kachel, die mit dem numerischen Signal „63“</span><span class="sxs-lookup"><span data-stu-id="9011a-104">A tile with a numeric badge displaying</span></span><br/> <span data-ttu-id="9011a-105">auf 63 ungelesene E-Mails hinweist.</span><span class="sxs-lookup"><span data-stu-id="9011a-105">the number 63 to indicate 63 unread mails.</span></span></div>

<span data-ttu-id="9011a-106">Ein Benachrichtigungssignal enthält eine Zusammenfassung oder Statusinformationen für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="9011a-106">A notification badge conveys summary or status information specific to your app.</span></span> <span data-ttu-id="9011a-107">Diese Informationen können numerisch (1–99) oder eine Gruppe der vom System bereitgestellten Glyphen sein.</span><span class="sxs-lookup"><span data-stu-id="9011a-107">They can be numeric (1-99) or one of a set of system-provided glyphs.</span></span> <span data-ttu-id="9011a-108">Beispiele für Informationen, die am besten über ein Signal vermittelt werden, sind der Netzwerkverbindungsstatus in einem Onlinespiel, der Benutzerstatus in einer Nachrichten-App, die Anzahl ungelesener Nachrichten in einer E-Mail-App und die Anzahl neuer Beiträge in einer Social-Media-App.</span><span class="sxs-lookup"><span data-stu-id="9011a-108">Examples of information best conveyed through a badge include network connection status in an online game, user status in a messaging app, number of unread mails in a mail app, and number of new posts in a social media app.</span></span> 

<span data-ttu-id="9011a-109">Benachrichtigungssignale werden unabhängig davon, ob die App gerade ausgeführt wird, auf dem Taskleisten-Symbol Ihrer App und in der unteren rechten Ecke der zugehörigen Kachel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9011a-109">Notification badges appear on your app's taskbar icon and in the lower-right corner of its start tile, regardless of whether the app is running.</span></span> <span data-ttu-id="9011a-110">Signale können auf allen Kachelgrößen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="9011a-110">Badges can be displayed on all tile sizes.</span></span>  

> [!NOTE]
> <span data-ttu-id="9011a-111">Es ist nicht möglich, ein eigenes Signalbild bereitzustellen. Sie können nur die vom System bereitgestellten Signalbilder verwenden.</span><span class="sxs-lookup"><span data-stu-id="9011a-111">You cannot provide your own badge image; only system-provided badge images can be used.</span></span>


## <a name="numeric-badges"></a><span data-ttu-id="9011a-112">Numerische Signale</span><span class="sxs-lookup"><span data-stu-id="9011a-112">Numeric badges</span></span>

<table>
    <tr>
        <th><span data-ttu-id="9011a-113">Wert</span><span class="sxs-lookup"><span data-stu-id="9011a-113">Value</span></span></th>
        <th><span data-ttu-id="9011a-114">Signal</span><span class="sxs-lookup"><span data-stu-id="9011a-114">Badge</span></span></th>
        <th><span data-ttu-id="9011a-115">XML</span><span class="sxs-lookup"><span data-stu-id="9011a-115">XML</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="9011a-116">Eine Zahl zwischen 1 und 99</span><span class="sxs-lookup"><span data-stu-id="9011a-116">A number from 1 to 99.</span></span> <span data-ttu-id="9011a-117">Ein Nullwert entspricht dem Glyphenwert "none" und führt dazu, dass das Signal gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="9011a-117">A value of 0 is equivalent to the glyph value "none" and will clear the badge.</span></span></td>
        <td><img src="images/badges/badge-numeric.png" alt="A numeric badge less than 100." /></td>
        <td>`<badge value="1"/>`</td>
    </tr>
    <tr>
        <td><span data-ttu-id="9011a-118">Eine beliebige Zahl über 99</span><span class="sxs-lookup"><span data-stu-id="9011a-118">Any number greater than 99.</span></span></td>
        <td><img src="images/badges/badge-numeric-greater.png" alt="A numeric badge greater than 99." /></td></td>
        <td>`<badge value="100"/>`</td>
    </tr>    
</table>

## <a name="glyph-badges"></a><span data-ttu-id="9011a-119">Glyphensignale</span><span class="sxs-lookup"><span data-stu-id="9011a-119">Glyph badges</span></span>
<span data-ttu-id="9011a-120">Anstelle einer Zahl kann in einem Signal eine der nicht erweiterbaren Statusglyphen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="9011a-120">Instead of a number, a badge can display one of a non-extensible set of status glyphs.</span></span> 

<table>
<tr>
    <th><span data-ttu-id="9011a-121">Status</span><span class="sxs-lookup"><span data-stu-id="9011a-121">Status</span></span></th>
    <th><span data-ttu-id="9011a-122">Glyphe</span><span class="sxs-lookup"><span data-stu-id="9011a-122">Glyph</span></span></th>
    <th><span data-ttu-id="9011a-123">XML</span><span class="sxs-lookup"><span data-stu-id="9011a-123">XML</span></span></th>
</tr>
<tr>
    <td><span data-ttu-id="9011a-124">keine</span><span class="sxs-lookup"><span data-stu-id="9011a-124">none</span></span></td>
    <td><span data-ttu-id="9011a-125">(Es wird kein Signal angezeigt.)</span><span class="sxs-lookup"><span data-stu-id="9011a-125">(No badge shown.)</span></span></td>
    <td>`<badge value="none"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-126">Aktivität</span><span class="sxs-lookup"><span data-stu-id="9011a-126">activity</span></span></td>
    <td><img src="images/badges/badge-activity.png" alt="Glyph" /></td>
    <td>`<badge value="activity"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-127">Alarm</span><span class="sxs-lookup"><span data-stu-id="9011a-127">alarm</span></span></td>
    <td><img src="images/badges/badge-alarm.png" alt="Glyph" /></td>
    <td>`<badge value="alarm"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-128">Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="9011a-128">alert</span></span></td>
    <td><img src="images/badges/badge-alert.png" alt="Glyph" /></td>
    <td>`<badge value="alert"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-129">Achtung</span><span class="sxs-lookup"><span data-stu-id="9011a-129">attention</span></span></td>
    <td><img src="images/badges/badge-attention.png" alt="Glyph" /></td>
    <td>`<badge value="attention"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-130">verfügbar</span><span class="sxs-lookup"><span data-stu-id="9011a-130">available</span></span></td>
    <td><img src="images/badges/badge-available.png" alt="Glyph" /></td>
    <td>`<badge value="available"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-131">abwesend</span><span class="sxs-lookup"><span data-stu-id="9011a-131">away</span></span></td>
    <td><img src="images/badges/badge-away.png" alt="Glyph" /></td>
    <td>`<badge value="away"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-132">beschäftigt</span><span class="sxs-lookup"><span data-stu-id="9011a-132">busy</span></span></td>
    <td><img src="images/badges/badge-busy.png" alt="Glyph" /></td>
    <td>`<badge value="busy"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-133">Fehler</span><span class="sxs-lookup"><span data-stu-id="9011a-133">error</span></span></td>
    <td><img src="images/badges/badge-error.png" alt="Glyph" /></td>
    <td>`<badge value="error"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-134">newMessage</span><span class="sxs-lookup"><span data-stu-id="9011a-134">newMessage</span></span></td>
    <td><img src="images/badges/badge-newMessage.png" alt="Glyph" /></td>
    <td>`<badge value="newMessage"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-135">angehalten</span><span class="sxs-lookup"><span data-stu-id="9011a-135">paused</span></span></td>
    <td><img src="images/badges/badge-paused.png" alt="Glyph" /></td>
    <td>`<badge value="paused"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-136">Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="9011a-136">playing</span></span></td>
    <td><img src="images/badges/badge-playing.png" alt="Glyph" /></td>
    <td>`<badge value="playing"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="9011a-137">nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="9011a-137">unavailable</span></span></td>
    <td><img src="images/badges/badge-unavailable.png" alt="Glyph" /></td>
    <td>`<badge value="unavailable"/>`</td>
</tr>
</table>

## <a name="create-a-badge"></a><span data-ttu-id="9011a-138">Erstellen eines Signals</span><span class="sxs-lookup"><span data-stu-id="9011a-138">Create a badge</span></span>

<span data-ttu-id="9011a-139">Diese Beispiele zeigen, wie eine signalaktualisierung erstellt.</span><span class="sxs-lookup"><span data-stu-id="9011a-139">These examples show you how to create a badge update.</span></span>

### <a name="create-a-numeric-badge"></a><span data-ttu-id="9011a-140">Erstellen eines numerischen Signals</span><span class="sxs-lookup"><span data-stu-id="9011a-140">Create a numeric badge</span></span>

````csharp
private void setBadgeNumber(int num)
{

    // Get the blank badge XML payload for a badge number
    XmlDocument badgeXml = 
        BadgeUpdateManager.GetTemplateContent(BadgeTemplateType.BadgeNumber);

    // Set the value of the badge in the XML to our number
    XmlElement badgeElement = badgeXml.SelectSingleNode("/badge") as XmlElement;
    badgeElement.SetAttribute("value", num.ToString());

    // Create the badge notification
    BadgeNotification badge = new BadgeNotification(badgeXml);

    // Create the badge updater for the application
    BadgeUpdater badgeUpdater = 
        BadgeUpdateManager.CreateBadgeUpdaterForApplication();

    // And update the badge
    badgeUpdater.Update(badge);

}
````

### <a name="create-a-glyph-badge"></a><span data-ttu-id="9011a-141">Erstellen eines Glyphensignals</span><span class="sxs-lookup"><span data-stu-id="9011a-141">Create a glyph badge</span></span>
````csharp
private void updateBadgeGlyph()
{
    string badgeGlyphValue = "alert";

    // Get the blank badge XML payload for a badge glyph
    XmlDocument badgeXml = 
        BadgeUpdateManager.GetTemplateContent(BadgeTemplateType.BadgeGlyph);

    // Set the value of the badge in the XML to our glyph value
    Windows.Data.Xml.Dom.XmlElement badgeElement = 
        badgeXml.SelectSingleNode("/badge") as Windows.Data.Xml.Dom.XmlElement;
    badgeElement.SetAttribute("value", badgeGlyphValue);

    // Create the badge notification
    BadgeNotification badge = new BadgeNotification(badgeXml);

    // Create the badge updater for the application
    BadgeUpdater badgeUpdater = 
        BadgeUpdateManager.CreateBadgeUpdaterForApplication();

    // And update the badge
    badgeUpdater.Update(badge);

}
````

### <a name="clear-a-badge"></a><span data-ttu-id="9011a-142">Löschen eines Signals</span><span class="sxs-lookup"><span data-stu-id="9011a-142">Clear a badge</span></span>

````csharp
private void clearBadge()
{
    BadgeUpdateManager.CreateBadgeUpdaterForApplication().Clear();
}
````

## <a name="get-the-sample-code"></a><span data-ttu-id="9011a-143">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="9011a-143">Get the sample code</span></span>

* [<span data-ttu-id="9011a-144">Benachrichtigungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="9011a-144">Notifications sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/Notifications)<br/> <span data-ttu-id="9011a-145">Zeigt, wie Sie Live-Kacheln erstellen, Signalupdates senden und Popupbenachrichtigungen anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="9011a-145">Shows how to create live tiles, send badge updates, and display toast notifications.</span></span> 

## <a name="related-articles"></a><span data-ttu-id="9011a-146">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="9011a-146">Related articles</span></span>

* [<span data-ttu-id="9011a-147">Adaptive und interaktive Popupbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="9011a-147">Adaptive and interactive toast notifications</span></span>](adaptive-interactive-toasts.md)
* [<span data-ttu-id="9011a-148">Erstellen von Kacheln</span><span class="sxs-lookup"><span data-stu-id="9011a-148">Create tiles</span></span>](creating-tiles.md)
* [<span data-ttu-id="9011a-149">Erstellen adaptiver Kacheln</span><span class="sxs-lookup"><span data-stu-id="9011a-149">Create adaptive tiles</span></span>](create-adaptive-tiles.md)
