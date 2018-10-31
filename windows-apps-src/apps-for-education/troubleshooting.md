---
Description: Troubleshoot Microsoft Take a Test events and errors with the event viewer.
title: Problembehandlung bei Microsoft Prüfung mithilfe der Ereignisanzeige.
author: PatrickFarley
ms.author: pafarley
ms.assetid: 9218e542-f520-4616-98fc-b113d5a08e0f
ms.date: 10/06/2017
ms.topic: article
keywords: Windows 10, Uwp, education
ms.localizationpriority: medium
ms.openlocfilehash: eaf4c8e2641359e6d9a92444f66a1b6d4e5e5881
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5830596"
---
# <a name="troubleshoot-microsoft-take-a-test-with-the-event-viewer"></a><span data-ttu-id="7da55-103">Problembehandlung bei Microsoft Prüfung mithilfe der Ereignisanzeige.</span><span class="sxs-lookup"><span data-stu-id="7da55-103">Troubleshoot Microsoft Take a Test with the event viewer</span></span>

<span data-ttu-id="7da55-104">Sie können die Ereignisanzeige nutzen um sich Ereignisse und Fehler der Prüfung anzeigen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="7da55-104">You can use the Event Viewer to view Take a Test events and errors.</span></span> <span data-ttu-id="7da55-105">Prüfung protokolliert Ereignisse, wenn eine Sperrmodus-Anforderung empfangen wurde, wenn eine Geräteregistrierung erfolgreich war, die Sperrmodusrichtlinien erfolgreich angewendet wurden und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="7da55-105">Take a Test logs events when a lockdown request has been received, device enrollment has succeeded, lockdown policies were successfully applied, and more.</span></span>

<span data-ttu-id="7da55-106">So aktivieren Sie Ereignisse in der Ereignisanzeige</span><span class="sxs-lookup"><span data-stu-id="7da55-106">To enable viewing events in the Event Viewer:</span></span>
1. <span data-ttu-id="7da55-107">Öffnen Sie</span><span class="sxs-lookup"><span data-stu-id="7da55-107">Open the</span></span> `Event Viewer`
2. <span data-ttu-id="7da55-108">Navigieren Sie zu</span><span class="sxs-lookup"><span data-stu-id="7da55-108">Navigate to</span></span> `Applications and Services Logs > Microsoft > Windows > Management-SecureAssessment`
3. <span data-ttu-id="7da55-109">Klicken Sie mit der rechten Maustaste auf `Operational` und wählen Sie</span><span class="sxs-lookup"><span data-stu-id="7da55-109">Right-click `Operational` and select</span></span> `Enable Log`

<span data-ttu-id="7da55-110">So speichern Sie die Ereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="7da55-110">To save the event logs:</span></span>
1. <span data-ttu-id="7da55-111">Rechtsklick</span><span class="sxs-lookup"><span data-stu-id="7da55-111">Right-click</span></span> `Operational`
2. <span data-ttu-id="7da55-112">Klick</span><span class="sxs-lookup"><span data-stu-id="7da55-112">Click</span></span> `Save All Events As…`
