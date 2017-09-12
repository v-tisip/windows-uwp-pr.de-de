---
author: anbare
Description: "Mit sekundären Kacheln können Benutzer für den einfachen zukünftigen Zugriff auf den Inhalt Ihrer App bestimmte Inhalte und Deep-Links von der App an das Startmenü heften."
title: "Sekundäre Kacheln"
label: Secondary tiles
template: detail.hbs
ms.author: wdg-dev-content
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, sekundäre Kacheln"
ms.openlocfilehash: b5f81f27c1e042f45882f026ff6d20e0e5f5456b
ms.sourcegitcommit: 6396a69aab081f5c7a9a59739c83538616d3b1c7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2017
---
# <a name="secondary-tiles"></a><span data-ttu-id="28766-104">Sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="28766-104">Secondary tiles</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="28766-105">Mit sekundären Kacheln können Benutzer für den einfachen zukünftigen Zugriff auf den Inhalt Ihrer App bestimmte Inhalte und Deep-Links von der App an das Startmenü heften.</span><span class="sxs-lookup"><span data-stu-id="28766-105">Secondary tiles allow users to pin specific content and deep links from your app onto their Start menu, providing easy future access to the content within your app.</span></span>

![Screenshot von sekundären Kacheln](images/secondarytiles.png)

<span data-ttu-id="28766-107">Benutzer können z.B. das Wetter für verschiedene Orte an das Startmenü anheften, um (1) einfache, auf einen Blick erkennbare Live-Informationen über das aktuelle Wetter dank Live-Kachel und (2) einen schnellen Einstiegspunkt für die bestimmte Stadt Wetter, u. a. zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="28766-107">For example, users can pin the weather for numerous specific locations on their Start menu, which provides (1) easy live glanceable information about the current weather thanks to Live Tiles, and (2) a quick entry point to the specific city's weather they care about.</span></span> <span data-ttu-id="28766-108">Benutzer können auch bestimmte Aktien, Nachrichtenartikel und weitere Elemente anheften, die Ihnen wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="28766-108">Users can also pin specific stocks, news articles, and more items that are important to them.</span></span>

<span data-ttu-id="28766-109">Durch das Hinzufügen von sekundären Kacheln zur App, kann der Benutzer schnell und effizient erneut Kontakt mit Ihrer App aufnehmen, und ihm den einfachen Zugriff ermöglichen, den sekundäre Kacheln bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="28766-109">By adding secondary tiles to your app, you help the user re-engage quickly and efficiently with your app, encouraging them to return more often thanks to the easy access that secondary tiles provides.</span></span>

<span data-ttu-id="28766-110">**Sekundäre Kacheln können nur vom Benutzer auf der Startseite angeheftet werden. Von Apps können sekundäre Kacheln nicht programmgesteuert ohne Zustimmung des Anwenders angeheftet werden.**</span><span class="sxs-lookup"><span data-stu-id="28766-110">**Only users can pin a secondary tile; apps cannot pin secondary tiles programmatically without user approval**.</span></span> <span data-ttu-id="28766-111">Der Benutzer muss explizit auf eine Schaltfläche "Anheften" in der App klicken, worauf Sie die API verwenden, um die Anforderung an eine sekundäre Kachel zu erstellen. Das System zeigt anschließend ein Dialogfeld an, das den Benutzer auffordert, zu bestätigen, ob die die Kachel angeheftet werden soll.</span><span class="sxs-lookup"><span data-stu-id="28766-111">The user must explicitly click a "Pin" button within your app, at which point you then use the API to request to create a secondary tile, and then the system displays a dialog box asking the user to confirm whether they would like the tile pinned.</span></span>

## <a name="quick-links"></a><span data-ttu-id="28766-112">Quicklinks</span><span class="sxs-lookup"><span data-stu-id="28766-112">Quick links</span></span>

| <span data-ttu-id="28766-113">Artikel</span><span class="sxs-lookup"><span data-stu-id="28766-113">Article</span></span> | <span data-ttu-id="28766-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="28766-114">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="28766-115">Anleitung für sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="28766-115">Guidance on secondary tiles</span></span>](tiles-and-notifications-secondary-tiles-guidance.md) | <span data-ttu-id="28766-116">Hier erfahren Sie, wann und wo sekundäre Kacheln verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="28766-116">Learn about when and where you should use secondary tiles.</span></span> |
| [<span data-ttu-id="28766-117">Sekundäre Kacheln anheften</span><span class="sxs-lookup"><span data-stu-id="28766-117">Pin secondary tiles</span></span>](tiles-and-notifications-secondary-tiles-pinning.md) | <span data-ttu-id="28766-118">Hier erfahren Sie, wie Sie eine sekundäre Kachel anheften.</span><span class="sxs-lookup"><span data-stu-id="28766-118">Learn how to pin a secondary tile.</span></span> |
| [<span data-ttu-id="28766-119">Anheften ab einer Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="28766-119">Pin from desktop application</span></span>](tiles-and-notifications-secondary-tiles-desktop-pinning.md) | <span data-ttu-id="28766-120">Windows-Desktopanwendungen können sekundäre Kacheln dank der Desktop-Brücke anheften!</span><span class="sxs-lookup"><span data-stu-id="28766-120">Windows desktop applications can pin secondary tiles thanks to the Desktop Bridge!</span></span> |


## <a name="secondary-tiles-in-relation-to-primary-tiles"></a><span data-ttu-id="28766-121">Verhältnis zwischen sekundären Kacheln und primären Kacheln</span><span class="sxs-lookup"><span data-stu-id="28766-121">Secondary tiles in relation to primary tiles</span></span>

<span data-ttu-id="28766-122">Sekundäre Kacheln sind einer einzigen übergeordneten App zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="28766-122">Secondary tiles are associated with a single parent app.</span></span> <span data-ttu-id="28766-123">Sie sind auf dem Startmenü angeheftet. Der Benutzer kann dadurch auf einheitliche und effiziente Weise direkt auf einen häufig verwendeten Bereich der übergeordneten App zugreifen.</span><span class="sxs-lookup"><span data-stu-id="28766-123">They are pinned to the Start menu to provide a user with a consistent and efficient way to launch directly into a frequently used area of the parent app.</span></span> <span data-ttu-id="28766-124">Das kann ein allgemeiner Unterbereich der übergeordneten App mit häufig aktualisierten Inhalten sein oder ein Deep-Link zu einem bestimmten Bereich der App.</span><span class="sxs-lookup"><span data-stu-id="28766-124">This can be either a general subsection of the parent app that contains frequently updated content, or a deep link to a specific area in the app.</span></span>

<span data-ttu-id="28766-125">Beispielszenarien für sekundäre Kacheln:</span><span class="sxs-lookup"><span data-stu-id="28766-125">Examples of secondary tile scenarios include:</span></span>

* <span data-ttu-id="28766-126">Aktuelle Wetterinformationen in einer Wetter-App</span><span class="sxs-lookup"><span data-stu-id="28766-126">Weather updates for a specific city in a weather app</span></span>
* <span data-ttu-id="28766-127">Eine Zusammenfassung anstehender Termine in einer Kalender-App</span><span class="sxs-lookup"><span data-stu-id="28766-127">A summary of upcoming events in a calendar app</span></span>
* <span data-ttu-id="28766-128">Status und Updates eines wichtigen Kontakts in einer sozialen App</span><span class="sxs-lookup"><span data-stu-id="28766-128">Status and updates from an important contact in a social app</span></span>
* <span data-ttu-id="28766-129">Bestimmte Feeds in einem RSS-Reader</span><span class="sxs-lookup"><span data-stu-id="28766-129">Specific feeds in an RSS reader</span></span>
* <span data-ttu-id="28766-130">Eine Musikwiedergabeliste</span><span class="sxs-lookup"><span data-stu-id="28766-130">A music playlist</span></span>
* <span data-ttu-id="28766-131">Ein Blog</span><span class="sxs-lookup"><span data-stu-id="28766-131">A blog</span></span>

<span data-ttu-id="28766-132">Sich häufig ändernde Inhalte, die ein Benutzer im Blick behalten möchte, können hervorragend als sekundäre Kachel dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="28766-132">Any frequently changing content that a user wants to monitor is a good candidate for a secondary tile.</span></span> <span data-ttu-id="28766-133">Nachdem die sekundäre Kachel angeheftet wurde, sieht der Benutzer daran sofort jede Änderung und kann damit direkt die übergeordnete App starten.</span><span class="sxs-lookup"><span data-stu-id="28766-133">After the secondary tile is pinned, users can receive at-a-glance updates through the tile and use it to launch directly into the parent app.</span></span>

<span data-ttu-id="28766-134">Sekundäre Kacheln sind in vielen Punkten mit primären Kacheln vergleichbar:</span><span class="sxs-lookup"><span data-stu-id="28766-134">Secondary tiles are similar to primary tiles in many ways:</span></span>

* <span data-ttu-id="28766-135">Sie verwenden Kachelbenachrichtigungen, um umfangreichen Inhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="28766-135">They use tile notifications to display rich content.</span></span>
* <span data-ttu-id="28766-136">Für den Standardinhalt der Kachel muss ein 150x150 Pixel großes Logo vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="28766-136">They must include a 150 x 150 pixel logo for the default tile content.</span></span>
* <span data-ttu-id="28766-137">Sie können optional die anderen Logo-Größen enthalten, um größere Kachel zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="28766-137">They can optionally include the other logo sizes to enable larger tile sizes.</span></span>
* <span data-ttu-id="28766-138">Sie können Benachrichtigungen und Signale anzeigen.</span><span class="sxs-lookup"><span data-stu-id="28766-138">They can show notifications and badges.</span></span>
* <span data-ttu-id="28766-139">Sie können auf dem Startmenü neu angeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="28766-139">They can be rearranged on the Start menu.</span></span>
* <span data-ttu-id="28766-140">Sie werden beim Deinstallieren der App automatisch gelöscht.</span><span class="sxs-lookup"><span data-stu-id="28766-140">They are automatically deleted when the app is uninstalled.</span></span>
* <span data-ttu-id="28766-141">Ausführliche Statusinfos für Signale und die Sperre können auf dem Sperrbildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="28766-141">Their badge and lock detailed status text can be shown on lock.</span></span>

<span data-ttu-id="28766-142">In einigen entscheidenden Punkten unterscheiden sich sekundäre Kacheln jedoch von primären Kacheln:</span><span class="sxs-lookup"><span data-stu-id="28766-142">However, secondary tiles differ from primary tiles in some noticeable ways:</span></span>

* <span data-ttu-id="28766-143">Benutzer können ihre sekundären Kacheln jederzeit löschen, ohne dabei die übergeordnete App zu löschen.</span><span class="sxs-lookup"><span data-stu-id="28766-143">Users can delete their secondary tiles at any time without deleting the parent app.</span></span>
* <span data-ttu-id="28766-144">Sekundäre Kacheln können zur Laufzeit erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="28766-144">Secondary tiles can be created at run time.</span></span> <span data-ttu-id="28766-145">App-Kacheln können nur bei der Installation erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="28766-145">App tiles can be created only during installation.</span></span>
* <span data-ttu-id="28766-146">Vom Benutzer wird in einem Flyout eine Bestätigung angefordert, bevor eine sekundäre Kachel hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="28766-146">A flyout prompts the user for confirmation before adding a secondary tile.</span></span>
* <span data-ttu-id="28766-147">Sie können für den Sperrbildschirm nicht programmgesteuert über eine Anfrage an den Benutzer ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="28766-147">They cannot be programmatically selected for the lock screen through a request to the user.</span></span> <span data-ttu-id="28766-148">Sekundäre Kacheln muss der Benutzer unter PC-Einstellungen auf der Seite Personalisieren manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="28766-148">The user must manually add the the secondary tile through the Personalize page in PC Settings.</span></span>

<span data-ttu-id="28766-149">Für Kachel- und Signalupdater und Pushbenachrichtigungskanäle für sekundäre Kacheln gibt es besondere Methoden, um Benachrichtigungen zu senden.</span><span class="sxs-lookup"><span data-stu-id="28766-149">For sending notifications, specific methods are provided for tile and badge updaters and push notification channels used with secondary tiles.</span></span> <span data-ttu-id="28766-150">Sie entsprechen den Versionen, die mit primären Kacheln verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="28766-150">These parallel the versions used with primary tiles.</span></span> <span data-ttu-id="28766-151">Beispiel: CreateBadgeUpdaterForApplication und CreateBadgeUpdaterForSecondaryTile.</span><span class="sxs-lookup"><span data-stu-id="28766-151">For instance, CreateBadgeUpdaterForApplication vs. CreateBadgeUpdaterForSecondaryTile.</span></span>


## <a name="guidance-on-secondary-tiles"></a><span data-ttu-id="28766-152">Anleitung für sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="28766-152">Guidance on secondary tiles</span></span>
<span data-ttu-id="28766-153">Informationen darüber, wann und wo Sie sekundäre Kacheln verwenden sollten und weitere Hinweise zur Verwendung finden Sie unter [Anleitung für sekundäre Kacheln](tiles-and-notifications-secondary-tiles-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="28766-153">To learn about when and where you should use secondary tiles, and other usage guidance, please see [Guidance on secondary tiles](tiles-and-notifications-secondary-tiles-guidance.md)</span></span>


## <a name="pinning-secondary-tiles"></a><span data-ttu-id="28766-154">Anheften von Sekundärkacheln</span><span class="sxs-lookup"><span data-stu-id="28766-154">Pinning secondary tiles</span></span>
<span data-ttu-id="28766-155">Weitere Informationen zum Anheften von sekundärer Kacheln finden Sie unter [Sekundäre Kacheln anheften](tiles-and-notifications-secondary-tiles-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="28766-155">To learn how to pin secondary tiles, please see [Pin secondary tiles](tiles-and-notifications-secondary-tiles-pinning.md).</span></span>


## <a name="desktop-applications-and-secondary-tiles"></a><span data-ttu-id="28766-156">Desktop-Apps und sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="28766-156">Desktop applications and secondary tiles</span></span>
<span data-ttu-id="28766-157">Weitere Informationen darüber, wie Sie zu sekundären Kacheln von Ihrer Desktopanwendung über die Desktop-Brücke verwenden können finden Sie unter [Sekundäre Kacheln von Desktop-Anwendung anheften](tiles-and-notifications-secondary-tiles-desktop-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="28766-157">To learn how to use secondary tiles from your desktop application via the Desktop Bridge, please see [Pin secondary tiles from desktop application](tiles-and-notifications-secondary-tiles-desktop-pinning.md).</span></span>