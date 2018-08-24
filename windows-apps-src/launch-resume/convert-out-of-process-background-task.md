---
author: TylerMSFT
title: Konvertieren einer Out-of-Process-Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe
description: Konvertieren Sie eine Out-of-Process-Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe, die innerhalb Ihres Vordergrund-App-Prozesses ausgeführt wird.
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Hintergrund, app-Dienst
ms.assetid: 5327e966-b78d-4859-9b97-5a61c362573e
ms.localizationpriority: medium
ms.openlocfilehash: 1144443f943f134991d050dea1457f252eaaf36d
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2829726"
---
# <a name="convert-an-out-of-process-background-task-to-an-in-process-background-task"></a><span data-ttu-id="67c22-104">Konvertieren einer Out-of-Process-Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="67c22-104">Convert an out-of-process background task to an in-process background task</span></span>

<span data-ttu-id="67c22-105">Die einfachste Möglichkeit, Ihre Out-of-Process-Hintergrundaktivität in eine in-Process-Aktivität zu konvertieren, besteht darin, Ihren [IBackgroundTask.Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx?f=255&MSPPError=-2147217396)-Methodencode in Ihre Anwendung zu verschieben und über [OnBackgroundActivated](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx) zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="67c22-105">The simplest way to convert your out-of-process background activity into in-process activity is to bring your [IBackgroundTask.Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx?f=255&MSPPError=-2147217396) method code inside your application and initiate it from [OnBackgroundActivated](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx).</span></span>

<span data-ttu-id="67c22-106">Wenn Ihre App mehrere Hintergrundaufgaben aufweist, wird in [Hintergrundaktivierungsbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BackgroundActivation) beschrieben, wie Sie mithilfe von `BackgroundActivatedEventArgs.TaskInstance.Task.Name` ermitteln können, welche Aufgabe initiiert wird.</span><span class="sxs-lookup"><span data-stu-id="67c22-106">If your app has multiple background tasks, the [Background Activation Sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BackgroundActivation) shows how you can use `BackgroundActivatedEventArgs.TaskInstance.Task.Name` to identify which task is being initiated.</span></span>

<span data-ttu-id="67c22-107">Wenn Sie derzeit zwischen Vordergrund- und Hintergrundprozessen kommunizieren, können Sie diesen Zustandverwaltungs- und Kommunikationscode entfernen.</span><span class="sxs-lookup"><span data-stu-id="67c22-107">If you are currently communicating between background and foreground processes, you can remove that state management and communication code.</span></span>

## <a name="background-tasks-and-trigger-types-that-cannot-be-converted"></a><span data-ttu-id="67c22-108">Hintergrundaufgaben und Triggertypen, die nicht konvertiert werden können</span><span class="sxs-lookup"><span data-stu-id="67c22-108">Background tasks and trigger types that cannot be converted</span></span>

* <span data-ttu-id="67c22-109">In-Process-Hintergrundaufgaben unterstützen nicht die Aktivierung einer VoIP-Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="67c22-109">In-process background tasks don't support activating a VoIP background task.</span></span>
* <span data-ttu-id="67c22-110">In-Process-Hintergrundaufgaben unterstützen nicht die folgenden Trigger: [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx?f=255&MSPPError=-2147217396), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) und **IoTStartupTask**</span><span class="sxs-lookup"><span data-stu-id="67c22-110">In-process background tasks don't support the following triggers:  [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx?f=255&MSPPError=-2147217396), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) and **IoTStartupTask**</span></span>
