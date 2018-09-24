---
author: andrewleader
Description: Secondary tiles allow users to pin specific content and deep links from your app onto their Start menu, providing easy future access to the content within your app.
title: Sekundäre Kacheln
label: Secondary tiles
template: detail.hbs
ms.author: wdg-dev-content
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, sekundäre Kacheln
ms.localizationpriority: medium
ms.openlocfilehash: 7f11ca4d29f22daf953ce03436c3b786c70a9e04
ms.sourcegitcommit: 194ab5aa395226580753869c6b66fce88be83522
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "4154775"
---
# <a name="secondary-tiles"></a><span data-ttu-id="dafd3-103">Sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="dafd3-103">Secondary tiles</span></span>


<span data-ttu-id="dafd3-104">Mit sekundären Kacheln können Benutzer für den einfachen zukünftigen Zugriff auf den Inhalt Ihrer App bestimmte Inhalte und Deep-Links von der App an das Startmenü heften.</span><span class="sxs-lookup"><span data-stu-id="dafd3-104">Secondary tiles allow users to pin specific content and deep links from your app onto their Start menu, providing easy future access to the content within your app.</span></span>

![Screenshot von sekundären Kacheln](images/secondarytiles.png)

<span data-ttu-id="dafd3-106">Benutzer können z.B. das Wetter für verschiedene Orte an das Startmenü anheften, um (1) einfache, auf einen Blick erkennbare Live-Informationen über das aktuelle Wetter dank Live-Kachel und (2) einen schnellen Einstiegspunkt für die bestimmte Stadt Wetter, u. a. zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="dafd3-106">For example, users can pin the weather for numerous specific locations on their Start menu, which provides (1) easy live glanceable information about the current weather thanks to Live Tiles, and (2) a quick entry point to the specific city's weather they care about.</span></span> <span data-ttu-id="dafd3-107">Benutzer können auch bestimmte Aktien, Nachrichtenartikel und weitere Elemente anheften, die Ihnen wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="dafd3-107">Users can also pin specific stocks, news articles, and more items that are important to them.</span></span>

<span data-ttu-id="dafd3-108">Durch das Hinzufügen von sekundären Kacheln zur App, kann der Benutzer schnell und effizient erneut Kontakt mit Ihrer App aufnehmen, und ihm den einfachen Zugriff ermöglichen, den sekundäre Kacheln bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="dafd3-108">By adding secondary tiles to your app, you help the user re-engage quickly and efficiently with your app, encouraging them to return more often thanks to the easy access that secondary tiles provides.</span></span>

<span data-ttu-id="dafd3-109">**Sekundäre Kacheln können nur vom Benutzer auf der Startseite angeheftet werden. Von Apps können sekundäre Kacheln nicht programmgesteuert ohne Zustimmung des Anwenders angeheftet werden.**</span><span class="sxs-lookup"><span data-stu-id="dafd3-109">**Only users can pin a secondary tile; apps cannot pin secondary tiles programmatically without user approval**.</span></span> <span data-ttu-id="dafd3-110">Der Benutzer muss explizit auf eine Schaltfläche "Anheften" in der App klicken, worauf Sie die API verwenden, um die Anforderung an eine sekundäre Kachel zu erstellen. Das System zeigt anschließend ein Dialogfeld an, das den Benutzer auffordert, zu bestätigen, ob die die Kachel angeheftet werden soll.</span><span class="sxs-lookup"><span data-stu-id="dafd3-110">The user must explicitly click a "Pin" button within your app, at which point you then use the API to request to create a secondary tile, and then the system displays a dialog box asking the user to confirm whether they would like the tile pinned.</span></span>

## <a name="quick-links"></a><span data-ttu-id="dafd3-111">Quicklinks</span><span class="sxs-lookup"><span data-stu-id="dafd3-111">Quick links</span></span>

| <span data-ttu-id="dafd3-112">Artikel</span><span class="sxs-lookup"><span data-stu-id="dafd3-112">Article</span></span> | <span data-ttu-id="dafd3-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dafd3-113">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="dafd3-114">Anleitung für sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="dafd3-114">Guidance on secondary tiles</span></span>](secondary-tiles-guidance.md) | <span data-ttu-id="dafd3-115">Hier erfahren Sie, wann und wo sekundäre Kacheln verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="dafd3-115">Learn about when and where you should use secondary tiles.</span></span> |
| [<span data-ttu-id="dafd3-116">Sekundäre Kacheln anheften</span><span class="sxs-lookup"><span data-stu-id="dafd3-116">Pin secondary tiles</span></span>](secondary-tiles-pinning.md) | <span data-ttu-id="dafd3-117">Hier erfahren Sie, wie Sie eine sekundäre Kachel anheften.</span><span class="sxs-lookup"><span data-stu-id="dafd3-117">Learn how to pin a secondary tile.</span></span> |
| [<span data-ttu-id="dafd3-118">Anheften ab einer Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="dafd3-118">Pin from desktop application</span></span>](secondary-tiles-desktop-pinning.md) | <span data-ttu-id="dafd3-119">Windows-Desktopanwendungen können sekundäre Kacheln dank der Desktop-Brücke anheften!</span><span class="sxs-lookup"><span data-stu-id="dafd3-119">Windows desktop applications can pin secondary tiles thanks to the Desktop Bridge!</span></span> |


## <a name="secondary-tiles-in-relation-to-primary-tiles"></a><span data-ttu-id="dafd3-120">Verhältnis zwischen sekundären Kacheln und primären Kacheln</span><span class="sxs-lookup"><span data-stu-id="dafd3-120">Secondary tiles in relation to primary tiles</span></span>

<span data-ttu-id="dafd3-121">Sekundäre Kacheln sind einer einzigen übergeordneten App zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="dafd3-121">Secondary tiles are associated with a single parent app.</span></span> <span data-ttu-id="dafd3-122">Sie sind auf dem Startmenü angeheftet. Der Benutzer kann dadurch auf einheitliche und effiziente Weise direkt auf einen häufig verwendeten Bereich der übergeordneten App zugreifen.</span><span class="sxs-lookup"><span data-stu-id="dafd3-122">They are pinned to the Start menu to provide a user with a consistent and efficient way to launch directly into a frequently used area of the parent app.</span></span> <span data-ttu-id="dafd3-123">Das kann ein allgemeiner Unterbereich der übergeordneten App mit häufig aktualisierten Inhalten sein oder ein Deep-Link zu einem bestimmten Bereich der App.</span><span class="sxs-lookup"><span data-stu-id="dafd3-123">This can be either a general subsection of the parent app that contains frequently updated content, or a deep link to a specific area in the app.</span></span>

<span data-ttu-id="dafd3-124">Beispielszenarien für sekundäre Kacheln:</span><span class="sxs-lookup"><span data-stu-id="dafd3-124">Examples of secondary tile scenarios include:</span></span>

* <span data-ttu-id="dafd3-125">Aktuelle Wetterinformationen in einer Wetter-App</span><span class="sxs-lookup"><span data-stu-id="dafd3-125">Weather updates for a specific city in a weather app</span></span>
* <span data-ttu-id="dafd3-126">Eine Zusammenfassung anstehender Termine in einer Kalender-App</span><span class="sxs-lookup"><span data-stu-id="dafd3-126">A summary of upcoming events in a calendar app</span></span>
* <span data-ttu-id="dafd3-127">Status und Updates eines wichtigen Kontakts in einer sozialen App</span><span class="sxs-lookup"><span data-stu-id="dafd3-127">Status and updates from an important contact in a social app</span></span>
* <span data-ttu-id="dafd3-128">Bestimmte Feeds in einem RSS-Reader</span><span class="sxs-lookup"><span data-stu-id="dafd3-128">Specific feeds in an RSS reader</span></span>
* <span data-ttu-id="dafd3-129">Eine Musikwiedergabeliste</span><span class="sxs-lookup"><span data-stu-id="dafd3-129">A music playlist</span></span>
* <span data-ttu-id="dafd3-130">Ein Blog</span><span class="sxs-lookup"><span data-stu-id="dafd3-130">A blog</span></span>

<span data-ttu-id="dafd3-131">Sich häufig ändernde Inhalte, die ein Benutzer im Blick behalten möchte, können hervorragend als sekundäre Kachel dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="dafd3-131">Any frequently changing content that a user wants to monitor is a good candidate for a secondary tile.</span></span> <span data-ttu-id="dafd3-132">Nachdem die sekundäre Kachel angeheftet wurde, sieht der Benutzer daran sofort jede Änderung und kann damit direkt die übergeordnete App starten.</span><span class="sxs-lookup"><span data-stu-id="dafd3-132">After the secondary tile is pinned, users can receive at-a-glance updates through the tile and use it to launch directly into the parent app.</span></span>

<span data-ttu-id="dafd3-133">Sekundäre Kacheln sind in vielen Punkten mit primären Kacheln vergleichbar:</span><span class="sxs-lookup"><span data-stu-id="dafd3-133">Secondary tiles are similar to primary tiles in many ways:</span></span>

* <span data-ttu-id="dafd3-134">Sie verwenden Kachelbenachrichtigungen, um umfangreichen Inhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="dafd3-134">They use tile notifications to display rich content.</span></span>
* <span data-ttu-id="dafd3-135">Für den Standardinhalt der Kachel muss ein 150x150 Pixel großes Logo vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="dafd3-135">They must include a 150 x 150 pixel logo for the default tile content.</span></span>
* <span data-ttu-id="dafd3-136">Sie können optional die anderen Logo-Größen enthalten, um größere Kachel zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="dafd3-136">They can optionally include the other logo sizes to enable larger tile sizes.</span></span>
* <span data-ttu-id="dafd3-137">Sie können Benachrichtigungen und Signale anzeigen.</span><span class="sxs-lookup"><span data-stu-id="dafd3-137">They can show notifications and badges.</span></span>
* <span data-ttu-id="dafd3-138">Sie können auf dem Startmenü neu angeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="dafd3-138">They can be rearranged on the Start menu.</span></span>
* <span data-ttu-id="dafd3-139">Sie werden beim Deinstallieren der App automatisch gelöscht.</span><span class="sxs-lookup"><span data-stu-id="dafd3-139">They are automatically deleted when the app is uninstalled.</span></span>
* <span data-ttu-id="dafd3-140">Ausführliche Statusinfos für Signale und die Sperre können auf dem Sperrbildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="dafd3-140">Their badge and lock detailed status text can be shown on lock.</span></span>

<span data-ttu-id="dafd3-141">In einigen entscheidenden Punkten unterscheiden sich sekundäre Kacheln jedoch von primären Kacheln:</span><span class="sxs-lookup"><span data-stu-id="dafd3-141">However, secondary tiles differ from primary tiles in some noticeable ways:</span></span>

* <span data-ttu-id="dafd3-142">Benutzer können ihre sekundären Kacheln jederzeit löschen, ohne dabei die übergeordnete App zu löschen.</span><span class="sxs-lookup"><span data-stu-id="dafd3-142">Users can delete their secondary tiles at any time without deleting the parent app.</span></span>
* <span data-ttu-id="dafd3-143">Sekundäre Kacheln können zur Laufzeit erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="dafd3-143">Secondary tiles can be created at run time.</span></span> <span data-ttu-id="dafd3-144">App-Kacheln können nur bei der Installation erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="dafd3-144">App tiles can be created only during installation.</span></span>
* <span data-ttu-id="dafd3-145">Vom Benutzer wird in einem Flyout eine Bestätigung angefordert, bevor eine sekundäre Kachel hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="dafd3-145">A flyout prompts the user for confirmation before adding a secondary tile.</span></span>
* <span data-ttu-id="dafd3-146">Sie können für den Sperrbildschirm nicht programmgesteuert über eine Anfrage an den Benutzer ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="dafd3-146">They cannot be programmatically selected for the lock screen through a request to the user.</span></span> <span data-ttu-id="dafd3-147">Sekundäre Kacheln muss der Benutzer unter PC-Einstellungen auf der Seite Personalisieren manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="dafd3-147">The user must manually add the the secondary tile through the Personalize page in PC Settings.</span></span>

<span data-ttu-id="dafd3-148">Für Kachel- und Signalupdater und Pushbenachrichtigungskanäle für sekundäre Kacheln gibt es besondere Methoden, um Benachrichtigungen zu senden.</span><span class="sxs-lookup"><span data-stu-id="dafd3-148">For sending notifications, specific methods are provided for tile and badge updaters and push notification channels used with secondary tiles.</span></span> <span data-ttu-id="dafd3-149">Sie entsprechen den Versionen, die mit primären Kacheln verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="dafd3-149">These parallel the versions used with primary tiles.</span></span> <span data-ttu-id="dafd3-150">Beispiel: CreateBadgeUpdaterForApplication und CreateBadgeUpdaterForSecondaryTile.</span><span class="sxs-lookup"><span data-stu-id="dafd3-150">For instance, CreateBadgeUpdaterForApplication vs. CreateBadgeUpdaterForSecondaryTile.</span></span>


## <a name="guidance-on-secondary-tiles"></a><span data-ttu-id="dafd3-151">Anleitung für sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="dafd3-151">Guidance on secondary tiles</span></span>
<span data-ttu-id="dafd3-152">Informationen darüber, wann und wo Sie sekundäre Kacheln verwenden sollten und weitere Hinweise zur Verwendung finden Sie unter [Anleitung für sekundäre Kacheln](secondary-tiles-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="dafd3-152">To learn about when and where you should use secondary tiles, and other usage guidance, please see [Guidance on secondary tiles](secondary-tiles-guidance.md)</span></span>


## <a name="pinning-secondary-tiles"></a><span data-ttu-id="dafd3-153">Anheften von Sekundärkacheln</span><span class="sxs-lookup"><span data-stu-id="dafd3-153">Pinning secondary tiles</span></span>
<span data-ttu-id="dafd3-154">Weitere Informationen zum Anheften von sekundärer Kacheln finden Sie unter [Sekundäre Kacheln anheften](secondary-tiles-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="dafd3-154">To learn how to pin secondary tiles, please see [Pin secondary tiles](secondary-tiles-pinning.md).</span></span>


## <a name="desktop-applications-and-secondary-tiles"></a><span data-ttu-id="dafd3-155">Desktop-Apps und sekundäre Kacheln</span><span class="sxs-lookup"><span data-stu-id="dafd3-155">Desktop applications and secondary tiles</span></span>
<span data-ttu-id="dafd3-156">Weitere Informationen darüber, wie Sie zu sekundären Kacheln von Ihrer Desktopanwendung über die Desktop-Brücke verwenden können finden Sie unter [Sekundäre Kacheln von Desktop-Anwendung anheften](secondary-tiles-desktop-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="dafd3-156">To learn how to use secondary tiles from your desktop application via the Desktop Bridge, please see [Pin secondary tiles from desktop application](secondary-tiles-desktop-pinning.md).</span></span>
