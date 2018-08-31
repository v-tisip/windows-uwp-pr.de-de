---
Description: Troubleshoot Microsoft Take a Test events and errors with the event viewer.
title: Problembehandlung bei Microsoft Prüfung mithilfe der Ereignisanzeige.
author: PatrickFarley
ms.author: pafarley
ms.assetid: 9218e542-f520-4616-98fc-b113d5a08e0f
ms.date: 10/06/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, education
ms.localizationpriority: medium
ms.openlocfilehash: 3193525316d085e56244d6f03da99e3e07c6539f
ms.sourcegitcommit: 1e5590dd10d606a910da6deb67b6a98f33235959
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2018
ms.locfileid: "3236485"
---
# <a name="troubleshoot-microsoft-take-a-test-with-the-event-viewer"></a><span data-ttu-id="16c86-103">Problembehandlung bei Microsoft Prüfung mithilfe der Ereignisanzeige.</span><span class="sxs-lookup"><span data-stu-id="16c86-103">Troubleshoot Microsoft Take a Test with the event viewer</span></span>

<span data-ttu-id="16c86-104">Sie können die Ereignisanzeige nutzen um sich Ereignisse und Fehler der Prüfung anzeigen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="16c86-104">You can use the Event Viewer to view Take a Test events and errors.</span></span> <span data-ttu-id="16c86-105">Prüfung protokolliert Ereignisse, wenn eine Sperrmodus-Anforderung empfangen wurde, wenn eine Geräteregistrierung erfolgreich war, die Sperrmodusrichtlinien erfolgreich angewendet wurden und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="16c86-105">Take a Test logs events when a lockdown request has been received, device enrollment has succeeded, lockdown policies were successfully applied, and more.</span></span>

<span data-ttu-id="16c86-106">So aktivieren Sie Ereignisse in der Ereignisanzeige</span><span class="sxs-lookup"><span data-stu-id="16c86-106">To enable viewing events in the Event Viewer:</span></span>
1. <span data-ttu-id="16c86-107">Öffnen Sie</span><span class="sxs-lookup"><span data-stu-id="16c86-107">Open the</span></span> `Event Viewer`
2. <span data-ttu-id="16c86-108">Navigieren Sie zu</span><span class="sxs-lookup"><span data-stu-id="16c86-108">Navigate to</span></span> `Applications and Services Logs > Microsoft > Windows > Management-SecureAssessment`
3. <span data-ttu-id="16c86-109">Klicken Sie mit der rechten Maustaste auf `Operational` und wählen Sie</span><span class="sxs-lookup"><span data-stu-id="16c86-109">Right-click `Operational` and select</span></span> `Enable Log`

<span data-ttu-id="16c86-110">So speichern Sie die Ereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="16c86-110">To save the event logs:</span></span>
1. <span data-ttu-id="16c86-111">Rechtsklick</span><span class="sxs-lookup"><span data-stu-id="16c86-111">Right-click</span></span> `Operational`
2. <span data-ttu-id="16c86-112">Klick</span><span class="sxs-lookup"><span data-stu-id="16c86-112">Click</span></span> `Save All Events As…`
