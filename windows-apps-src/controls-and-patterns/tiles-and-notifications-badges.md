---
author: mijacobs
Description: "Erfahren Sie, wie Sie mithilfe von Kacheln, Signalen, Popups und Benachrichtigungen Einstiegspunkte in Ihre App bereitstellen und Benutzer auf dem neuesten Stand halten können."
title: "Signalbenachrichtigungen für UWP-Apps"
ms.assetid: 48ee4328-7999-40c2-9354-7ea7d488c538
label: Tiles, badges, and notifications
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 73866ab5ef6001ccac96d2b9d782477fbe18156a
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="badge-notifications-for-uwp-apps"></a><span data-ttu-id="6ac83-104">Signalbenachrichtigungen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="6ac83-104">Badge notifications for UWP apps</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<div style="float:left; font-size:80%; text-align:left; margin: 0px 15px 15px 0px;">
<img src="images/badge-example.png" alt="A tile with a numeric badge displaying the number 63 to indicate 63 unread mails." style="padding-bottom:0.0em; margin-bottom: 2px" /><br/><span data-ttu-id="6ac83-105">Eine Kachel, die mit dem numerischen Signal „63“</span><span class="sxs-lookup"><span data-stu-id="6ac83-105">A tile with a numeric badge displaying</span></span><br/> <span data-ttu-id="6ac83-106">auf 63 ungelesene E-Mails hinweist.</span><span class="sxs-lookup"><span data-stu-id="6ac83-106">the number 63 to indicate 63 unread mails.</span></span></div>

<span data-ttu-id="6ac83-107">Ein Benachrichtigungssignal enthält eine Zusammenfassung oder Statusinformationen für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="6ac83-107">A notification badge conveys summary or status information specific to your app.</span></span> <span data-ttu-id="6ac83-108">Diese Informationen können numerisch (1–99) oder eine Gruppe der vom System bereitgestellten Glyphen sein.</span><span class="sxs-lookup"><span data-stu-id="6ac83-108">They can be numeric (1-99) or one of a set of system-provided glyphs.</span></span> <span data-ttu-id="6ac83-109">Beispiele für Informationen, die am besten über ein Signal vermittelt werden, sind der Netzwerkverbindungsstatus in einem Onlinespiel, der Benutzerstatus in einer Nachrichten-App, die Anzahl ungelesener Nachrichten in einer E-Mail-App und die Anzahl neuer Beiträge in einer Social-Media-App.</span><span class="sxs-lookup"><span data-stu-id="6ac83-109">Examples of information best conveyed through a badge include network connection status in an online game, user status in a messaging app, number of unread mails in a mail app, and number of new posts in a social media app.</span></span> 

<span data-ttu-id="6ac83-110">Benachrichtigungssignale werden unabhängig davon, ob die App gerade ausgeführt wird, auf dem Taskleisten-Symbol Ihrer App und in der unteren rechten Ecke der zugehörigen Kachel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6ac83-110">Notification badges appear on your app's taskbar icon and in the lower-right corner of its start tile, regardless of whether the app is running.</span></span> <span data-ttu-id="6ac83-111">Signale können auf allen Kachelgrößen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6ac83-111">Badges can be displayed on all tile sizes.</span></span>  

> [!NOTE]
> <span data-ttu-id="6ac83-112">Es ist nicht möglich, ein eigenes Signalbild bereitzustellen. Sie können nur die vom System bereitgestellten Signalbilder verwenden.</span><span class="sxs-lookup"><span data-stu-id="6ac83-112">You cannot provide your own badge image; only system-provided badge images can be used.</span></span>


## <a name="numeric-badges"></a><span data-ttu-id="6ac83-113">Numerische Signale</span><span class="sxs-lookup"><span data-stu-id="6ac83-113">Numeric badges</span></span>

<table>
    <tr>
        <th><span data-ttu-id="6ac83-114">Wert</span><span class="sxs-lookup"><span data-stu-id="6ac83-114">Value</span></span></th>
        <th><span data-ttu-id="6ac83-115">Signal</span><span class="sxs-lookup"><span data-stu-id="6ac83-115">Badge</span></span></th>
        <th><span data-ttu-id="6ac83-116">XML</span><span class="sxs-lookup"><span data-stu-id="6ac83-116">XML</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="6ac83-117">Eine Zahl zwischen 1 und 99</span><span class="sxs-lookup"><span data-stu-id="6ac83-117">A number from 1 to 99.</span></span> <span data-ttu-id="6ac83-118">Ein Nullwert entspricht dem Glyphenwert "none" und führt dazu, dass das Signal gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="6ac83-118">A value of 0 is equivalent to the glyph value "none" and will clear the badge.</span></span></td>
        <td>![Ein numerisches Signal unter 100](images/badges/badge-numeric.png)</td>
        <td>`<badge value="1"/>`</td>
    </tr>
    <tr>
        <td><span data-ttu-id="6ac83-120">Eine beliebige Zahl über 99</span><span class="sxs-lookup"><span data-stu-id="6ac83-120">Any number greater than 99.</span></span></td>
        <td>![Ein numerisches Signal über 99](images/badges/badge-numeric-greater.png)</td></td>
        <td>`<badge value="100"/>`</td>
    </tr>    
</table>

## <a name="glyph-badges"></a><span data-ttu-id="6ac83-122">Glyphensignale</span><span class="sxs-lookup"><span data-stu-id="6ac83-122">Glyph badges</span></span>
<span data-ttu-id="6ac83-123">Anstelle einer Zahl kann in einem Signal eine der nicht erweiterbaren Statusglyphen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6ac83-123">Instead of a number, a badge can display one of a non-extensible set of status glyphs.</span></span> 

<table>
<tr>
    <th><span data-ttu-id="6ac83-124">Status</span><span class="sxs-lookup"><span data-stu-id="6ac83-124">Status</span></span></th>
    <th><span data-ttu-id="6ac83-125">Glyphe</span><span class="sxs-lookup"><span data-stu-id="6ac83-125">Glyph</span></span></th>
    <th><span data-ttu-id="6ac83-126">XML</span><span class="sxs-lookup"><span data-stu-id="6ac83-126">XML</span></span></th>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-127">keine</span><span class="sxs-lookup"><span data-stu-id="6ac83-127">none</span></span></td>
    <td><span data-ttu-id="6ac83-128">(Es wird kein Signal angezeigt.)</span><span class="sxs-lookup"><span data-stu-id="6ac83-128">(No badge shown.)</span></span></td>
    <td>`<badge value="none"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-129">Aktivität</span><span class="sxs-lookup"><span data-stu-id="6ac83-129">activity</span></span></td>
    <td>![Glyphe](images/badges/badge-activity.png)</td>
    <td>`<badge value="activity"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-131">Alarm</span><span class="sxs-lookup"><span data-stu-id="6ac83-131">alarm</span></span></td>
    <td>![Glyphe](images/badges/badge-alarm.png)</td>
    <td>`<badge value="alarm"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-133">Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="6ac83-133">alert</span></span></td>
    <td>![Glyphe](images/badges/badge-alert.png)</td>
    <td>`<badge value="alert"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-135">Achtung</span><span class="sxs-lookup"><span data-stu-id="6ac83-135">attention</span></span></td>
    <td>![Glyphe](images/badges/badge-attention.png)</td>
    <td>`<badge value="attention"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-137">verfügbar</span><span class="sxs-lookup"><span data-stu-id="6ac83-137">available</span></span></td>
    <td>![Glyphe](images/badges/badge-available.png)</td>
    <td>`<badge value="available"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-139">abwesend</span><span class="sxs-lookup"><span data-stu-id="6ac83-139">away</span></span></td>
    <td>![Glyphe](images/badges/badge-away.png)</td>
    <td>`<badge value="away"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-141">beschäftigt</span><span class="sxs-lookup"><span data-stu-id="6ac83-141">busy</span></span></td>
    <td>![Glyphe](images/badges/badge-busy.png)</td>
    <td>`<badge value="busy"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-143">Fehler</span><span class="sxs-lookup"><span data-stu-id="6ac83-143">error</span></span></td>
    <td>![Glyphe](images/badges/badge-error.png)</td>
    <td>`<badge value="error"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-145">newMessage</span><span class="sxs-lookup"><span data-stu-id="6ac83-145">newMessage</span></span></td>
    <td>![Glyphe](images/badges/badge-newMessage.png)</td>
    <td>`<badge value="newMessage"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-147">angehalten</span><span class="sxs-lookup"><span data-stu-id="6ac83-147">paused</span></span></td>
    <td>![Glyphe](images/badges/badge-paused.png)</td>
    <td>`<badge value="paused"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-149">Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="6ac83-149">playing</span></span></td>
    <td>![Glyphe](images/badges/badge-playing.png)</td>
    <td>`<badge value="playing"/>`</td>
</tr>
<tr>
    <td><span data-ttu-id="6ac83-151">nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="6ac83-151">unavailable</span></span></td>
    <td>![Glyphe](images/badges/badge-unavailable.png)</td>
    <td>`<badge value="unavailable"/>`</td>
</tr>
</table>

## <a name="create-a-badge"></a><span data-ttu-id="6ac83-153">Erstellen eines Signals</span><span class="sxs-lookup"><span data-stu-id="6ac83-153">Create a badge</span></span>

<span data-ttu-id="6ac83-154">Diese Beispiele zeigen, wie eine Signalaktualisierung erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="6ac83-154">These examples show you how to to create a badge update.</span></span>

### <a name="create-a-numeric-badge"></a><span data-ttu-id="6ac83-155">Erstellen eines numerischen Signals</span><span class="sxs-lookup"><span data-stu-id="6ac83-155">Create a numeric badge</span></span>

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

### <a name="create-a-glyph-badge"></a><span data-ttu-id="6ac83-156">Erstellen eines Glyphensignals</span><span class="sxs-lookup"><span data-stu-id="6ac83-156">Create a glyph badge</span></span>
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

### <a name="clear-a-badge"></a><span data-ttu-id="6ac83-157">Löschen eines Signals</span><span class="sxs-lookup"><span data-stu-id="6ac83-157">Clear a badge</span></span>

````csharp
private void clearBadge()
{
    BadgeUpdateManager.CreateBadgeUpdaterForApplication().Clear();
}
````

## <a name="get-the-sample-code"></a><span data-ttu-id="6ac83-158">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="6ac83-158">Get the sample code</span></span>

* [<span data-ttu-id="6ac83-159">Benachrichtigungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="6ac83-159">Notifications sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/Notifications)<br/> <span data-ttu-id="6ac83-160">Zeigt, wie Sie Live-Kacheln erstellen, Signalupdates senden und Popupbenachrichtigungen anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="6ac83-160">Shows how to create live tiles, send badge updates, and display toast notifications.</span></span> 

## <a name="related-articles"></a><span data-ttu-id="6ac83-161">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="6ac83-161">Related articles</span></span>

* [<span data-ttu-id="6ac83-162">Adaptive und interaktive Popupbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="6ac83-162">Adaptive and interactive toast notifications</span></span>](tiles-and-notifications-adaptive-interactive-toasts.md)
* [<span data-ttu-id="6ac83-163">Erstellen von Kacheln</span><span class="sxs-lookup"><span data-stu-id="6ac83-163">Create tiles</span></span>](tiles-and-notifications-creating-tiles.md)
* [<span data-ttu-id="6ac83-164">Erstellen adaptiver Kacheln</span><span class="sxs-lookup"><span data-stu-id="6ac83-164">Create adaptive tiles</span></span>](tiles-and-notifications-create-adaptive-tiles.md)