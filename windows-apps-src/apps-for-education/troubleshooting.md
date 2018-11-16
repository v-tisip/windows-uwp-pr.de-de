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
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6854288"
---
# <a name="troubleshoot-microsoft-take-a-test-with-the-event-viewer"></a>Problembehandlung bei Microsoft Prüfung mithilfe der Ereignisanzeige.

Sie können die Ereignisanzeige nutzen um sich Ereignisse und Fehler der Prüfung anzeigen zu lassen. Prüfung protokolliert Ereignisse, wenn eine Sperrmodus-Anforderung empfangen wurde, wenn eine Geräteregistrierung erfolgreich war, die Sperrmodusrichtlinien erfolgreich angewendet wurden und vieles mehr.

So aktivieren Sie Ereignisse in der Ereignisanzeige
1. Öffnen Sie `Event Viewer`
2. Navigieren Sie zu `Applications and Services Logs > Microsoft > Windows > Management-SecureAssessment`
3. Klicken Sie mit der rechten Maustaste auf `Operational` und wählen Sie `Enable Log`

So speichern Sie die Ereignisprotokolle
1. Rechtsklick `Operational`
2. Klick `Save All Events As…`
