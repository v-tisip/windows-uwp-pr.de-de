---
author: v-angraf
title: Neuigkeiten für UWP auf Xbox One
description: Vorstellung neuer Features für UWP-Apps auf Xbox One.
ms.author: v-angraf
ms.date: 03/29/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: fe63c527-8f06-43a5-868f-de909f5664b3
ms.localizationpriority: medium
ms.openlocfilehash: cc2168014e714de0b43b6ffffe84126764f0a4a3
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6837106"
---
# <a name="whats-new-for-developers-in-the-latest-update-of-uwp-on-xbox-one"></a><span data-ttu-id="1ee3f-104">Neuigkeiten für Entwickler in der neuesten Aktualisierung von UWP auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="1ee3f-104">What's new for developers in the latest update of UWP on Xbox One</span></span>

<span data-ttu-id="1ee3f-105">Das neueste Update für universelle Windows-Plattform (UWP) auf Xbox One enthält die folgenden neuen Features, Updates für vorhandene Features und Fehlerbehebungen.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-105">The latest update of Universal Windows Platform (UWP) on Xbox One contains the following new features, updates to existing features, and bug fixes.</span></span>

## <a name="x86-apps-and-games-are-no-longer-supported-on-xbox"></a><span data-ttu-id="1ee3f-106">X86 apps und Spiele werden nicht mehr auf Xbox unterstützt</span><span class="sxs-lookup"><span data-stu-id="1ee3f-106">x86 apps and games are no longer supported on Xbox</span></span>  
<span data-ttu-id="1ee3f-107">Xbox unterstützt die Entwicklung von x86 Apps oder deren Übermittlung an den Store nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-107">Xbox no longer supports x86 app development or x86 app submissions to the store.</span></span>

## <a name="apps-can-now-support-navigating-back-to-the-previous-app"></a><span data-ttu-id="1ee3f-108">Apps unterstützen jetzt Navigieren zurück zum vorherigen app</span><span class="sxs-lookup"><span data-stu-id="1ee3f-108">Apps can now support navigating back to the previous app</span></span> 
<span data-ttu-id="1ee3f-109">UWP auf Xbox One-apps unterstützen jetzt das Navigieren zurück zum vorherigen app.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-109">UWP on Xbox One apps can now support navigating back to the previous app.</span></span> <span data-ttu-id="1ee3f-110">Zu diesem Zweck das [**Windows.UI.Core.SystemNavigationManager.BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893595) -Ereignis abonnieren Sie, und legen Sie die **Handled** -Eigenschaft auf **"false"** im Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-110">To do this, subscribe to the [**Windows.UI.Core.SystemNavigationManager.BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893595) event and set the **Handled** property to **false** in your event handler.</span></span>

> [!NOTE]
> <span data-ttu-id="1ee3f-111">Aus Gründen der Kompatibilität ist diese Funktionalität nur für apps, die mit der neuesten Version von UWP auf Xbox One integriert sind verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-111">For compatibility reasons, this functionality is available only to apps that are built with the most recent release of UWP on Xbox One.</span></span> 

## <a name="dev-home-is-now-the-default-home-experience-on-development-consoles"></a><span data-ttu-id="1ee3f-112">Dev Home ist jetzt die Standard-startoberfläche auf Entwicklungskonsolen</span><span class="sxs-lookup"><span data-stu-id="1ee3f-112">Dev Home is now the default home experience on development consoles</span></span>
<span data-ttu-id="1ee3f-113">Entwicklungskonsolen starten Sie Dev Home jetzt als der Standard-startoberfläche.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-113">Development consoles now launch Dev Home as the default home experience.</span></span> <span data-ttu-id="1ee3f-114">Auf diese Weise können Sie richtig zu funktionieren, ohne dass die Notwendigkeit aus dem Einzelhandel-Startbildschirm durch klicken.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-114">This lets you get right to work without the need to click through from the retail Home screen.</span></span> <span data-ttu-id="1ee3f-115">Dev Home enthält jetzt eine schnelle Aktion dem Einzelhandel-Startbildschirm starten.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-115">Dev Home now includes a quick action to launch the retail Home screen.</span></span> <span data-ttu-id="1ee3f-116">Darüber hinaus können mit eine neue Einstellung Sie stellen die Standardoberfläche retail Home.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-116">Also, a new setting allows you to make retail Home the default experience.</span></span> 

## <a name="new-dev-home-user-interface"></a><span data-ttu-id="1ee3f-117">Neue Dev Home-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="1ee3f-117">New Dev Home user interface</span></span>
<span data-ttu-id="1ee3f-118">Die Dev Home-Benutzeroberfläche enthält jetzt die folgenden erweiterten Funktionen:</span><span class="sxs-lookup"><span data-stu-id="1ee3f-118">The Dev Home user interface now includes the following productivity enhancements:</span></span>
 - <span data-ttu-id="1ee3f-119">Wichtige Daten wie IP-Adresse und Recovery-Version wird nun am oberen Rand des Bildschirms für Sichtbarkeit angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-119">Important data like IP address and recovery version is now displayed at the top of the screen for visibility.</span></span> 
 - <span data-ttu-id="1ee3f-120">Dev Home verfügt nun über eine Benutzeroberfläche mit Registerkarten, die Tools in logischen Sätze gruppiert ermöglicht die schnelle Navigation.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-120">Dev Home now has a tabbed UI that groups tools into logical sets, allowing quick navigation.</span></span>
 - <span data-ttu-id="1ee3f-121">Quick-Aktionsschaltflächen auf der ersten Registerkarte des Dev Home ermöglichen schnellen Zugriff auf die am häufigsten verwendeten Aktionen.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-121">Quick-action buttons on the first tab of Dev Home allow fast access to the most commonly used actions.</span></span> 

## <a name="wdp-for-xbox-enhancements"></a><span data-ttu-id="1ee3f-122">WDP für Xbox-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="1ee3f-122">WDP for Xbox enhancements</span></span>
<span data-ttu-id="1ee3f-123">Die Windows-Geräteportal (WDP) bietet jetzt zusätzliche Unterstützung für konsoleneinstellungen.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-123">The Windows Device Portal (WDP) now includes additional support for console settings.</span></span> 

## <a name="you-can-now-switch-the-type-of-your-uwp-title-between-app-and-game"></a><span data-ttu-id="1ee3f-124">Sie können jetzt den Typ der Titel Ihrer UWP zwischen "App" und "Game" wechseln.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-124">You can now switch the type of your UWP title between "App" and "Game"</span></span>
<span data-ttu-id="1ee3f-125">Wechseln zwischen den Typ der Titel Ihrer UWP zwischen "App" und "Spiel" können Sie Spiele Szenarios ohne Veröffentlichung an den Store zu testen.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-125">Switching the type of your UWP title between "App" and "Game" allows you to test game scenarios without publishing to the store.</span></span> <span data-ttu-id="1ee3f-126">Klicken Sie in Dev Home wählen Sie die app im Bereich **Spiele und Apps** , drücken Sie die Ansicht-Taste auf dem Controller, wählen Sie **Details zur App** , und ändern Sie den Typ "App" oder "Game".</span><span class="sxs-lookup"><span data-stu-id="1ee3f-126">In Dev Home, select the app in the **Games & Apps** pane, press the View button on the controller, select **App details** and then change the type to "App" or "Game".</span></span>

## <a name="see-also"></a><span data-ttu-id="1ee3f-127">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="1ee3f-127">See also</span></span>
- [<span data-ttu-id="1ee3f-128">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="1ee3f-128">Known issues</span></span>](known-issues.md)
- [<span data-ttu-id="1ee3f-129">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="1ee3f-129">UWP on Xbox One</span></span>](index.md)
 - <span data-ttu-id="1ee3f-130">Sie können jetzt einen Screenshot der Konsole erstellen.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-130">You can now capture a screenshot of the console.</span></span> <span data-ttu-id="1ee3f-131">Weitere Informationen zum Erstellen eines Screenshots finden Sie im Referenzthema [/ext/screenshot](wdp-media-capture-api.md).</span><span class="sxs-lookup"><span data-stu-id="1ee3f-131">For more information about taking a screenshot, see the [/ext/screenshot](wdp-media-capture-api.md) reference topic.</span></span>
 - <span data-ttu-id="1ee3f-132">Das Tool kann einen losen Dateibuild Ihrer App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-132">The tool can deploy a loose file build of your app.</span></span> <span data-ttu-id="1ee3f-133">Weitere Informationen zu losen Dateibuilds finden Sie im Referenzthema [/api/app/packagemanager/register](wdp-loose-folder-register-api.md).</span><span class="sxs-lookup"><span data-stu-id="1ee3f-133">For more information about loose file builds, see the [/api/app/packagemanager/register](wdp-loose-folder-register-api.md) reference topic.</span></span>
 - <span data-ttu-id="1ee3f-134">Sie können auf Entwicklerdateien auf der Konsole über einen Datei-Explorer auf Ihrem Entwicklungscomputer zugreifen.</span><span class="sxs-lookup"><span data-stu-id="1ee3f-134">Developer files on your console can be accessed from File Explorer on your development PC.</span></span> <span data-ttu-id="1ee3f-135">Weitere Informationen zum Zugreifen auf Dateien über einen Datei-Explorer finden Sie im Referenzthema [/ext/smb/developerfolder](wdp-smb-api.md).</span><span class="sxs-lookup"><span data-stu-id="1ee3f-135">For more information about accessing files through File Explorer, see the [/ext/smb/developerfolder](wdp-smb-api.md) reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ee3f-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1ee3f-136">See also</span></span>
- [<span data-ttu-id="1ee3f-137">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="1ee3f-137">Known issues</span></span>](known-issues.md)
- [<span data-ttu-id="1ee3f-138">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="1ee3f-138">UWP on Xbox One</span></span>](index.md)
