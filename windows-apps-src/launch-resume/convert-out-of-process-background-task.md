---
author: TylerMSFT
title: Eine Out-of-Process Hintergrundaufgabe eine prozessinterne Hintergrundtask Port
description: Anschluss einer Out-of-Process Hintergrundaufgabe eine prozessinterne Hintergrundtasks, die innerhalb der app Vordergrundprozess ausgeführt wird.
ms.author: twhitney
ms.date: 09/19/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10 Uwp Hintergrund, app service
ms.assetid: 5327e966-b78d-4859-9b97-5a61c362573e
ms.localizationpriority: medium
ms.openlocfilehash: b9010f82b0460bd46757bc1e0d58c01dec459104
ms.sourcegitcommit: 5dda01da4702cbc49c799c750efe0e430b699502
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4114416"
---
# <a name="port-an-out-of-process-background-task-to-an-in-process-background-task"></a><span data-ttu-id="768fe-104">Eine Out-of-Process Hintergrundaufgabe eine prozessinterne Hintergrundtask Port</span><span class="sxs-lookup"><span data-stu-id="768fe-104">Port an out-of-process background task to an in-process background task</span></span>

<span data-ttu-id="768fe-105">Die einfachste Möglichkeit, Ihre Out-of-Process (OOP) Hintergrundaktivität um prozessinterne Aktivität port ist zu Ihrem [IBackgroundTask.Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx?f=255&MSPPError=-2147217396) Code in Ihrer Anwendung, ausgehend von der [OnBackgroundActivated](/uwp/api/windows.ui.xaml.application.onbackgroundactivated).</span><span class="sxs-lookup"><span data-stu-id="768fe-105">The simplest way to port your out-of-process (OOP) background activity to in-process activity is to bring your [IBackgroundTask.Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx?f=255&MSPPError=-2147217396) method code inside your application, and initiate it from [OnBackgroundActivated](/uwp/api/windows.ui.xaml.application.onbackgroundactivated).</span></span> <span data-ttu-id="768fe-106">Das hier beschriebene Verfahren ist nicht über einen Shim aus einer Hintergrundaufgabe OOP ein Vorgang in Bearbeitung Hintergrund erstellen. die zum Umschreiben (oder Portieren) einer OOP Version einer in Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="768fe-106">The technique being described here is not about creating a shim from an OOP background task to an in-process background task; it's about rewriting (or porting) an OOP version to an in-process version.</span></span>

<span data-ttu-id="768fe-107">Wenn Ihre App mehrere Hintergrundaufgaben aufweist, wird in [Hintergrundaktivierungsbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BackgroundActivation) beschrieben, wie Sie mithilfe von `BackgroundActivatedEventArgs.TaskInstance.Task.Name` ermitteln können, welche Aufgabe initiiert wird.</span><span class="sxs-lookup"><span data-stu-id="768fe-107">If your app has multiple background tasks, the [Background Activation Sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BackgroundActivation) shows how you can use `BackgroundActivatedEventArgs.TaskInstance.Task.Name` to identify which task is being initiated.</span></span>

<span data-ttu-id="768fe-108">Wenn Sie derzeit zwischen Vordergrund- und Hintergrundprozessen kommunizieren, können Sie diesen Zustandverwaltungs- und Kommunikationscode entfernen.</span><span class="sxs-lookup"><span data-stu-id="768fe-108">If you are currently communicating between background and foreground processes, you can remove that state management and communication code.</span></span>

## <a name="background-tasks-and-trigger-types-that-cannot-be-converted"></a><span data-ttu-id="768fe-109">Hintergrundaufgaben und Triggertypen, die nicht konvertiert werden können</span><span class="sxs-lookup"><span data-stu-id="768fe-109">Background tasks and trigger types that cannot be converted</span></span>

* <span data-ttu-id="768fe-110">In-Process-Hintergrundaufgaben unterstützen nicht die Aktivierung einer VoIP-Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="768fe-110">In-process background tasks don't support activating a VoIP background task.</span></span>
* <span data-ttu-id="768fe-111">In-Process-Hintergrundaufgaben unterstützen nicht die folgenden Trigger: [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx?f=255&MSPPError=-2147217396), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) und **IoTStartupTask**</span><span class="sxs-lookup"><span data-stu-id="768fe-111">In-process background tasks don't support the following triggers:  [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx?f=255&MSPPError=-2147217396), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) and **IoTStartupTask**</span></span>
