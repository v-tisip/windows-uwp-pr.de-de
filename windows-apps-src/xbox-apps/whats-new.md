---
author: v-angraf
title: Neuigkeiten für UWP auf Xbox One
description: Vorstellung neuer Features für UWP-Apps auf Xbox One.
ms.author: v-angraf
ms.date: 03/29/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: fe63c527-8f06-43a5-868f-de909f5664b3
ms.localizationpriority: medium
ms.openlocfilehash: cbabe9d31b5b9762320df8e4a92d19ae4e33497d
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "301460"
---
# <a name="whats-new-for-developers-in-the-latest-update-of-uwp-on-xbox-one"></a><span data-ttu-id="3437c-104">Neuigkeiten für Entwickler in der neuesten Aktualisierung von UWP auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="3437c-104">What's new for developers in the latest update of UWP on Xbox One</span></span>

<span data-ttu-id="3437c-105">Das neueste Update von universellen Windows Plattform (UWP) auf einem Xbox enthält die folgenden neuen Features auf vorhandenen Features und Fehlerbehebungen Updates.</span><span class="sxs-lookup"><span data-stu-id="3437c-105">The latest update of Universal Windows Platform (UWP) on Xbox One contains the following new features, updates to existing features, and bug fixes.</span></span>

## <a name="x86-apps-and-games-are-no-longer-supported-on-xbox"></a><span data-ttu-id="3437c-106">X86 apps und Spiele werden auf der Xbox nicht mehr unterstützt</span><span class="sxs-lookup"><span data-stu-id="3437c-106">x86 apps and games are no longer supported on Xbox</span></span>  
<span data-ttu-id="3437c-107">Xbox unterstützt die Entwicklung von x86 Apps oder deren Übermittlung an den Store nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="3437c-107">Xbox no longer supports x86 app development or x86 app submissions to the store.</span></span>

## <a name="apps-can-now-support-navigating-back-to-the-previous-app"></a><span data-ttu-id="3437c-108">Apps unterstützen nun wieder zur vorherigen app navigieren</span><span class="sxs-lookup"><span data-stu-id="3437c-108">Apps can now support navigating back to the previous app</span></span> 
<span data-ttu-id="3437c-109">UWP auf eine Xbox apps unterstützen jetzt wieder auf den vorherigen app navigieren.</span><span class="sxs-lookup"><span data-stu-id="3437c-109">UWP on Xbox One apps can now support navigating back to the previous app.</span></span> <span data-ttu-id="3437c-110">Zu diesem Zweck abonnieren Sie das [**Windows.UI.Core.SystemNavigationManager.BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893595) -Ereignis, und legen Sie die **bearbeitete** -Eigenschaft auf **false** im Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="3437c-110">To do this, subscribe to the [**Windows.UI.Core.SystemNavigationManager.BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893595) event and set the **Handled** property to **false** in your event handler.</span></span>

> [!NOTE]
> <span data-ttu-id="3437c-111">Diese Funktion ist aus Gründen der Kompatibilität nur für apps, die mit der neuesten Version von UWP auf Xbox One integriert sind verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3437c-111">For compatibility reasons, this functionality is available only to apps that are built with the most recent release of UWP on Xbox One.</span></span> 

## <a name="dev-home-is-now-the-default-home-experience-on-development-consoles"></a><span data-ttu-id="3437c-112">Dev Home ist jetzt standardmäßig die private auf Entwicklung Konsolen</span><span class="sxs-lookup"><span data-stu-id="3437c-112">Dev Home is now the default home experience on development consoles</span></span>
<span data-ttu-id="3437c-113">Entwicklung Konsolen starten Dev Home jetzt als die standardmäßige home Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="3437c-113">Development consoles now launch Dev Home as the default home experience.</span></span> <span data-ttu-id="3437c-114">Auf diese Weise können Sie rechts, ohne die Notwendigkeit, die im Einzelhandel Startbildschirm durch Klicken arbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="3437c-114">This lets you get right to work without the need to click through from the retail Home screen.</span></span> <span data-ttu-id="3437c-115">Dev Home enthält nun eine schnelle Aktion um im Einzelhandel Startbildschirm zu starten.</span><span class="sxs-lookup"><span data-stu-id="3437c-115">Dev Home now includes a quick action to launch the retail Home screen.</span></span> <span data-ttu-id="3437c-116">Darüber hinaus kann eine neue Einstellung Sie standardmäßig Einzelhandel (privat).</span><span class="sxs-lookup"><span data-stu-id="3437c-116">Also, a new setting allows you to make retail Home the default experience.</span></span> 

## <a name="new-dev-home-user-interface"></a><span data-ttu-id="3437c-117">Neue Dev Home-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="3437c-117">New Dev Home user interface</span></span>
<span data-ttu-id="3437c-118">Die Benutzeroberfläche Dev Home enthält nun die folgenden erweiterten Funktionen:</span><span class="sxs-lookup"><span data-stu-id="3437c-118">The Dev Home user interface now includes the following productivity enhancements:</span></span>
 - <span data-ttu-id="3437c-119">Wichtige Daten wie IP-Adresse und Recovery Version nun am oberen Rand des Bildschirms für Sichtbarkeit angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3437c-119">Important data like IP address and recovery version is now displayed at the top of the screen for visibility.</span></span> 
 - <span data-ttu-id="3437c-120">Dev zu Hause bereits jetzt eine Benutzeroberfläche mit Registerkarten, die Tools in logischen Gruppen gruppiert Navigation über den zulassen.</span><span class="sxs-lookup"><span data-stu-id="3437c-120">Dev Home now has a tabbed UI that groups tools into logical sets, allowing quick navigation.</span></span>
 - <span data-ttu-id="3437c-121">Quick-Aktionsschaltflächen auf der ersten Registerkarte Dev Home ermöglichen schnellen Zugriff auf die am häufigsten verwendeten Aktionen.</span><span class="sxs-lookup"><span data-stu-id="3437c-121">Quick-action buttons on the first tab of Dev Home allow fast access to the most commonly used actions.</span></span> 

## <a name="wdp-for-xbox-enhancements"></a><span data-ttu-id="3437c-122">WDP für Xbox Verbesserungen</span><span class="sxs-lookup"><span data-stu-id="3437c-122">WDP for Xbox enhancements</span></span>
<span data-ttu-id="3437c-123">Windows Gerät Portal (WDP) enthält nun zusätzliche Unterstützung für die Konsole-Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="3437c-123">The Windows Device Portal (WDP) now includes additional support for console settings.</span></span> 

## <a name="you-can-now-switch-the-type-of-your-uwp-title-between-app-and-game"></a><span data-ttu-id="3437c-124">Sie können nun den Typ des Ihr Titel UWP zwischen "App" und "Spiel" wechseln.</span><span class="sxs-lookup"><span data-stu-id="3437c-124">You can now switch the type of your UWP title between "App" and "Game"</span></span>
<span data-ttu-id="3437c-125">Wechseln den Typ des Ihr Titel UWP zwischen "App" und "Gamecontroller" können Sie Spiel Szenarios ohne Veröffentlichung im Speicher zu testen.</span><span class="sxs-lookup"><span data-stu-id="3437c-125">Switching the type of your UWP title between "App" and "Game" allows you to test game scenarios without publishing to the store.</span></span> <span data-ttu-id="3437c-126">Wählen Sie in Dev Ihnen zu Hause die app im Bereich **Spiele & Apps** , drücken Sie die Schaltfläche Ansicht auf dem Domänencontroller, wählen Sie **App-Details** aus, und ändern Sie den Typ "App" oder "Spiel".</span><span class="sxs-lookup"><span data-stu-id="3437c-126">In Dev Home, select the app in the **Games & Apps** pane, press the View button on the controller, select **App details** and then change the type to "App" or "Game".</span></span>

## <a name="see-also"></a><span data-ttu-id="3437c-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3437c-127">See also</span></span>
- [<span data-ttu-id="3437c-128">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="3437c-128">Known issues</span></span>](known-issues.md)
- [<span data-ttu-id="3437c-129">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="3437c-129">UWP on Xbox One</span></span>](index.md)
 - <span data-ttu-id="3437c-130">Sie können jetzt einen Screenshot der Konsole erstellen.</span><span class="sxs-lookup"><span data-stu-id="3437c-130">You can now capture a screenshot of the console.</span></span> <span data-ttu-id="3437c-131">Weitere Informationen zum Erstellen eines Screenshots finden Sie im Referenzthema [/ext/screenshot](wdp-media-capture-api.md).</span><span class="sxs-lookup"><span data-stu-id="3437c-131">For more information about taking a screenshot, see the [/ext/screenshot](wdp-media-capture-api.md) reference topic.</span></span>
 - <span data-ttu-id="3437c-132">Das Tool kann einen losen Dateibuild Ihrer App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3437c-132">The tool can deploy a loose file build of your app.</span></span> <span data-ttu-id="3437c-133">Weitere Informationen zu losen Dateibuilds finden Sie im Referenzthema [/api/app/packagemanager/register](wdp-loose-folder-register-api.md).</span><span class="sxs-lookup"><span data-stu-id="3437c-133">For more information about loose file builds, see the [/api/app/packagemanager/register](wdp-loose-folder-register-api.md) reference topic.</span></span>
 - <span data-ttu-id="3437c-134">Sie können auf Entwicklerdateien auf der Konsole über einen Datei-Explorer auf Ihrem Entwicklungscomputer zugreifen.</span><span class="sxs-lookup"><span data-stu-id="3437c-134">Developer files on your console can be accessed from File Explorer on your development PC.</span></span> <span data-ttu-id="3437c-135">Weitere Informationen zum Zugreifen auf Dateien über einen Datei-Explorer finden Sie im Referenzthema [/ext/smb/developerfolder](wdp-smb-api.md).</span><span class="sxs-lookup"><span data-stu-id="3437c-135">For more information about accessing files through File Explorer, see the [/ext/smb/developerfolder](wdp-smb-api.md) reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="3437c-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3437c-136">See also</span></span>
- [<span data-ttu-id="3437c-137">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="3437c-137">Known issues</span></span>](known-issues.md)
- [<span data-ttu-id="3437c-138">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="3437c-138">UWP on Xbox One</span></span>](index.md)
