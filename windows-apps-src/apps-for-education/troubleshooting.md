---
author: TylerMSFT
Description: "Problembehandlung bei Ereignissen und Fehlern der Microsoft-Prüfung mithilfe der Ereignisanzeige."
title: "Problembehandlung bei Microsoft Prüfung mithilfe der Ereignisanzeige."
ms.openlocfilehash: 1b99b959cfdde997f7995c1bdf40d51921b2f1d5
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
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
