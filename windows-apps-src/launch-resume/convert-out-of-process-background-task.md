---
author: TylerMSFT
title: Portieren einer Out-of-Process Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe
description: Portieren einer Out-of-Process-Hintergrundaufgabe in eine in-Process-Hintergrundaufgabe, die innerhalb Ihres Vordergrund-app-Prozesses ausgeführt wird.
ms.author: twhitney
ms.date: 09/19/2018
ms.topic: article
keywords: Windows 10, Uwp, Hintergrundaufgabe, app-Dienst
ms.assetid: 5327e966-b78d-4859-9b97-5a61c362573e
ms.localizationpriority: medium
ms.openlocfilehash: 47008fd7ba0b7724aa8fbdc2dd6cbd55288faea0
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7290972"
---
# <a name="port-an-out-of-process-background-task-to-an-in-process-background-task"></a><span data-ttu-id="0a1f7-104">Portieren einer Out-of-Process Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="0a1f7-104">Port an out-of-process background task to an in-process background task</span></span>

<span data-ttu-id="0a1f7-105">Die einfachste Möglichkeit, Ihre Out-of-Process (OOP)-Hintergrundaktivitäten für in-Aktivität Process Portieren ist das Portieren Ihres [IBackgroundTask.Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx?f=255&MSPPError=-2147217396) Methode Codes in Ihrer Anwendung, und von [OnBackgroundActivated](/uwp/api/windows.ui.xaml.application.onbackgroundactivated)zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="0a1f7-105">The simplest way to port your out-of-process (OOP) background activity to in-process activity is to bring your [IBackgroundTask.Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx?f=255&MSPPError=-2147217396) method code inside your application, and initiate it from [OnBackgroundActivated](/uwp/api/windows.ui.xaml.application.onbackgroundactivated).</span></span> <span data-ttu-id="0a1f7-106">Die hier beschriebenen Techniken ist nicht zum Erstellen eines Shims aus einer OOP-Hintergrundaufgabe in eine in-Process-Hintergrundaufgabe. die Informationen zum Umschreiben (oder Portieren) eine OOP-Version auf eine in-Process-Version.</span><span class="sxs-lookup"><span data-stu-id="0a1f7-106">The technique being described here is not about creating a shim from an OOP background task to an in-process background task; it's about rewriting (or porting) an OOP version to an in-process version.</span></span>

<span data-ttu-id="0a1f7-107">Wenn Ihre App mehrere Hintergrundaufgaben aufweist, wird in [Hintergrundaktivierungsbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BackgroundActivation) beschrieben, wie Sie mithilfe von `BackgroundActivatedEventArgs.TaskInstance.Task.Name` ermitteln können, welche Aufgabe initiiert wird.</span><span class="sxs-lookup"><span data-stu-id="0a1f7-107">If your app has multiple background tasks, the [Background Activation Sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BackgroundActivation) shows how you can use `BackgroundActivatedEventArgs.TaskInstance.Task.Name` to identify which task is being initiated.</span></span>

<span data-ttu-id="0a1f7-108">Wenn Sie derzeit zwischen Vordergrund- und Hintergrundprozessen kommunizieren, können Sie diesen Zustandverwaltungs- und Kommunikationscode entfernen.</span><span class="sxs-lookup"><span data-stu-id="0a1f7-108">If you are currently communicating between background and foreground processes, you can remove that state management and communication code.</span></span>

## <a name="background-tasks-and-trigger-types-that-cannot-be-converted"></a><span data-ttu-id="0a1f7-109">Hintergrundaufgaben und Triggertypen, die nicht konvertiert werden können</span><span class="sxs-lookup"><span data-stu-id="0a1f7-109">Background tasks and trigger types that cannot be converted</span></span>

* <span data-ttu-id="0a1f7-110">In-Process-Hintergrundaufgaben unterstützen nicht die Aktivierung einer VoIP-Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="0a1f7-110">In-process background tasks don't support activating a VoIP background task.</span></span>
* <span data-ttu-id="0a1f7-111">In-Process-Hintergrundaufgaben unterstützen nicht die folgenden Trigger: [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx?f=255&MSPPError=-2147217396), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) und **IoTStartupTask**</span><span class="sxs-lookup"><span data-stu-id="0a1f7-111">In-process background tasks don't support the following triggers:  [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx?f=255&MSPPError=-2147217396), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) and **IoTStartupTask**</span></span>
