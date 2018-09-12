---
author: TylerMSFT
title: Konvertieren einer Out-of-Process-Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe
description: Konvertieren Sie eine Out-of-Process-Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe, die innerhalb Ihres Vordergrund-App-Prozesses ausgeführt wird.
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Hintergrundaufgabe, app-Dienst
ms.assetid: 5327e966-b78d-4859-9b97-5a61c362573e
ms.localizationpriority: medium
ms.openlocfilehash: 1144443f943f134991d050dea1457f252eaaf36d
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2018
ms.locfileid: "3928098"
---
# <a name="convert-an-out-of-process-background-task-to-an-in-process-background-task"></a>Konvertieren einer Out-of-Process-Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe

Die einfachste Möglichkeit, Ihre Out-of-Process-Hintergrundaktivität in eine in-Process-Aktivität zu konvertieren, besteht darin, Ihren [IBackgroundTask.Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx?f=255&MSPPError=-2147217396)-Methodencode in Ihre Anwendung zu verschieben und über [OnBackgroundActivated](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx) zu initiieren.

Wenn Ihre App mehrere Hintergrundaufgaben aufweist, wird in [Hintergrundaktivierungsbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BackgroundActivation) beschrieben, wie Sie mithilfe von `BackgroundActivatedEventArgs.TaskInstance.Task.Name` ermitteln können, welche Aufgabe initiiert wird.

Wenn Sie derzeit zwischen Vordergrund- und Hintergrundprozessen kommunizieren, können Sie diesen Zustandverwaltungs- und Kommunikationscode entfernen.

## <a name="background-tasks-and-trigger-types-that-cannot-be-converted"></a>Hintergrundaufgaben und Triggertypen, die nicht konvertiert werden können

* In-Process-Hintergrundaufgaben unterstützen nicht die Aktivierung einer VoIP-Hintergrundaufgabe.
* In-Process-Hintergrundaufgaben unterstützen nicht die folgenden Trigger: [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx?f=255&MSPPError=-2147217396), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) und **IoTStartupTask**
