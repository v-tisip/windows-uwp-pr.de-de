---
title: Portieren einer Out-of-Process Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe
description: Portieren einer Out-of-Process-Hintergrundaufgabe in eine in-Process-Hintergrundaufgabe, die innerhalb Ihres Vordergrund-app-Prozesses ausgeführt wird.
ms.date: 09/19/2018
ms.topic: article
keywords: Windows 10, Uwp, Hintergrundaufgabe, app-Dienst
ms.assetid: 5327e966-b78d-4859-9b97-5a61c362573e
ms.localizationpriority: medium
ms.openlocfilehash: 97dd249165877591743892a136d51e0969dd902a
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8202414"
---
# <a name="port-an-out-of-process-background-task-to-an-in-process-background-task"></a>Portieren einer Out-of-Process Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe

Die einfachste Möglichkeit, Ihre Out-of-Process (OOP)-Hintergrundaktivitäten für in-Aktivität Process Portieren ist das Portieren Ihres [IBackgroundTask.Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx?f=255&MSPPError=-2147217396) Methode Codes in Ihrer Anwendung, und von [OnBackgroundActivated](/uwp/api/windows.ui.xaml.application.onbackgroundactivated)zu initiieren. Das wird hier beschriebene Verfahren ist nicht zum Erstellen eines Shims aus einer OOP-Hintergrundaufgabe in eine in-Process-Hintergrundaufgabe. die Informationen zum Umschreiben (oder Portieren) eine OOP-Version auf eine in-Process-Version.

Wenn Ihre App mehrere Hintergrundaufgaben aufweist, wird in [Hintergrundaktivierungsbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BackgroundActivation) beschrieben, wie Sie mithilfe von `BackgroundActivatedEventArgs.TaskInstance.Task.Name` ermitteln können, welche Aufgabe initiiert wird.

Wenn Sie derzeit zwischen Vordergrund- und Hintergrundprozessen kommunizieren, können Sie diesen Zustandverwaltungs- und Kommunikationscode entfernen.

## <a name="background-tasks-and-trigger-types-that-cannot-be-converted"></a>Hintergrundaufgaben und Triggertypen, die nicht konvertiert werden können

* In-Process-Hintergrundaufgaben unterstützen nicht die Aktivierung einer VoIP-Hintergrundaufgabe.
* In-Process-Hintergrundaufgaben unterstützen nicht die folgenden Trigger: [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx?f=255&MSPPError=-2147217396), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) und **IoTStartupTask**
