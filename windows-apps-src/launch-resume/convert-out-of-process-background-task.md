---
author: TylerMSFT
title: Portieren einer Out-of-Process Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe
description: Portieren einer Out-of-Process-Hintergrundaufgabe in eine in-Process-Hintergrundaufgabe, die innerhalb Ihres Vordergrund-app-Prozesses ausgeführt wird.
ms.author: twhitney
ms.date: 09/19/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Hintergrundaufgabe, app-Diensts
ms.assetid: 5327e966-b78d-4859-9b97-5a61c362573e
ms.localizationpriority: medium
ms.openlocfilehash: b9010f82b0460bd46757bc1e0d58c01dec459104
ms.sourcegitcommit: 72835733ec429a5deb6a11da4112336746e5e9cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5164184"
---
# <a name="port-an-out-of-process-background-task-to-an-in-process-background-task"></a>Portieren einer Out-of-Process Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe

Die einfachste Möglichkeit, Ihre Out-of-Process (OOP) von Hintergrundaktivitäten für in-Aktivität Process Portieren ist das Portieren Ihres Codes [IBackgroundTask.Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx?f=255&MSPPError=-2147217396) Methode in Ihrer Anwendung und von [OnBackgroundActivated](/uwp/api/windows.ui.xaml.application.onbackgroundactivated)zu initiieren. Das wird hier beschriebene Verfahren ist nicht zum Erstellen eines Shims aus einer OOP-Hintergrundaufgabe in eine in-Process-Hintergrundaufgabe. die Informationen zum Umschreiben (oder Portieren) eine OOP-Version auf eine in-Process-Version.

Wenn Ihre App mehrere Hintergrundaufgaben aufweist, wird in [Hintergrundaktivierungsbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BackgroundActivation) beschrieben, wie Sie mithilfe von `BackgroundActivatedEventArgs.TaskInstance.Task.Name` ermitteln können, welche Aufgabe initiiert wird.

Wenn Sie derzeit zwischen Vordergrund- und Hintergrundprozessen kommunizieren, können Sie diesen Zustandverwaltungs- und Kommunikationscode entfernen.

## <a name="background-tasks-and-trigger-types-that-cannot-be-converted"></a>Hintergrundaufgaben und Triggertypen, die nicht konvertiert werden können

* In-Process-Hintergrundaufgaben unterstützen nicht die Aktivierung einer VoIP-Hintergrundaufgabe.
* In-Process-Hintergrundaufgaben unterstützen nicht die folgenden Trigger: [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx?f=255&MSPPError=-2147217396), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) und **IoTStartupTask**
