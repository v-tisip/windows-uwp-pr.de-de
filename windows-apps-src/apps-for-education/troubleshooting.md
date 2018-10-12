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
ms.sourcegitcommit: d10fb9eb5f75f2d10e1c543a177402b50fe4019e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "4575339"
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
