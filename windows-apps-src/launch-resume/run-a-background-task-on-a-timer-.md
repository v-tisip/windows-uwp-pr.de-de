---
author: TylerMSFT
title: Ausführen einer Hintergrundaufgabe für einen Timer
description: Hier erfahren Sie, wie Sie eine einmalige Hintergrundaufgabe planen oder eine regelmäßige Hintergrundaufgabe ausführen.
ms.assetid: 0B7F0BFF-535A-471E-AC87-783C740A61E9
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Hintergrundaufgabe, für die
ms.localizationpriority: medium
ms.openlocfilehash: 25e3c76ae09ed6835f89f0d98c308f11c7a99624
ms.sourcegitcommit: 82c3fc0b06ad490c3456ad18180a6b23ecd9c1a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "5469258"
---
# <a name="run-a-background-task-on-a-timer"></a>Ausführen einer Hintergrundaufgabe für einen Timer

Erfahren Sie, wie Sie die [**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843) verwenden, um eine einmalige Hintergrundaufgabe planen oder eine regelmäßige Hintergrundaufgabe ausführen.

Finden Sie unter **Scenario4** in der [hintergrundaktivierungsbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BackgroundActivation) sehen Sie ein Beispiel zum Implementieren der Hintergrundaufgabe ausgelösten beschriebene Zeit in diesem Thema.

In diesem Thema wird davon ausgegangen, dass Sie eine Hintergrundaufgabe verfügen, die regelmäßig oder zu einem bestimmten Zeitpunkt ausgeführt werden muss. Wenn Sie bereits über eine Hintergrundaufgabe besitzen, wird eine Hintergrundaufgabe Beispiel am [BackgroundActivity.cs](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackgroundActivation/cs/BackgroundActivity.cs). Oder führen Sie die Schritte in [Erstellen und Registrieren einer in-Process-Hintergrundaufgabe](create-and-register-an-inproc-background-task.md) oder [Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe](create-and-register-a-background-task.md) zu erstellen.

## <a name="create-a-time-trigger"></a>Erstellen eines Zeitauslösers

Erstellen Sie einen neuen Zeitauslöser ([**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843)). Der zweite Parameter (*OneShot*) gibt an, ob die Hintergrundaufgabe einmalig oder regelmäßig ausgeführt wird. Wenn *OneShot* auf „true“ festgelegt ist, gibt der erste Parameter (*FreshnessTime*) an, wie lange mit der Planung der Hintergrundaufgabe gewartet werden soll (in Minuten). Wenn *OneShot* auf „false“ festgelegt ist, gibt *FreshnessTime* die Häufigkeit an, mit der die Hintergrundaufgabe ausgeführt wird.

Der integrierte Timer für auf Desktop- oder Mobilgeräte ausgerichtete UWP-Apps führt Hintergrundaufgaben in einem 15-Minuten-Intervall aus. (Der Zeitgeber führt alle 15 Minuten, sodass das System muss nur einmal alle 15 Minuten reaktiviert werden Reaktivieren von apps, die Energie sparen TimerTriggers – angefordert haben.)

- Wenn *FreshnessTime* auf 15Minuten und *OneShot* auf „true“ festgelegt ist, wird die Aufgabe einmalig innerhalb der ersten 15 und 30Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant. Wenn sie auf 25Minuten und *OneShot* auf „true“ festgelegt ist, wird die Aufgabe einmalig innerhalb der ersten 25 und 40Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant.

- Wenn *FreshnessTime* auf 15Minuten und *OneShot* auf „false“ festgelegt ist, wird die Aufgabe alle 15Minuten innerhalb der ersten 15 und 30Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant. Wenn sie auf „n” Minuten und *OneShot* auf „false“ festgelegt ist, wird die Aufgabe alle „n” Minuten innerhalb der ersten „n” und „n+15” Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant.

> [!NOTE]
> Wenn *FreshnessTime* auf weniger als 15 Minuten festgelegt ist, wird eine Ausnahme ausgelöst, wenn Sie versuchen, die Hintergrundaufgabe zu registrieren.
 
Dieser Auslöser veranlasst beispielsweise, eine Hintergrundaufgabe einmal pro Stunde ausgeführt wird.

```cs
TimeTrigger hourlyTrigger = new TimeTrigger(60, false);
```

```cppwinrt
Windows::ApplicationModel::Background::TimeTrigger hourlyTrigger{ 60, false };
```

```cpp
TimeTrigger ^ hourlyTrigger = ref new TimeTrigger(60, false);
```

## <a name="optional-add-a-condition"></a>(Optional) Hinzufügen einer Bedingung

Sie können eine Bedingung für Hintergrundaufgaben Steuerelement erstellen, wenn die Aufgabe ausgeführt wird. Eine Bedingung wird verhindert, dass die Hintergrundaufgabe ausgeführt wird, bis die Bedingung erfüllt ist. Weitere Informationen finden Sie unter [Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md).

In diesem Beispiel ist die Bedingung auf **UserPresent** festgelegt, damit die ausgelöste Aufgabe nur ausgeführt wird, wenn der Benutzer aktiv ist. Eine Liste mit möglichen Bedingungen finden Sie in [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).

```cs
SystemCondition userCondition = new SystemCondition(SystemConditionType.UserPresent);
```

```cppwinrt
Windows::ApplicationModel::Background::SystemCondition userCondition{
    Windows::ApplicationModel::Background::SystemConditionType::UserPresent };
```

```cpp
SystemCondition ^ userCondition = ref new SystemCondition(SystemConditionType::UserPresent);
```

Ausführlichere Informationen zu Bedingungen und Hintergrund Triggertypen finden Sie unter [Unterstützung Ihrer app mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).

##  <a name="call-requestaccessasync"></a>Aufrufen von RequestAccessAsync()

Rufen Sie vor der Registrierung der Hintergrundaufgabe **ApplicationTrigger** [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700494) , um die Ebene der Hintergrundaktivität zu ermitteln, die dem Benutzer ermöglicht, da der Benutzer Hintergrundaktivitäten für Ihre app deaktiviert haben kann. Sehen Sie, dass die Einstellungen für Hintergrundaktivitäten [Optimieren von Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen über die Möglichkeiten Benutzer gesteuert werden können.

```cs
var requestStatus = await Windows.ApplicationModel.Background.BackgroundExecutionManager.RequestAccessAsync();
if (requestStatus != BackgroundAccessStatus.AlwaysAllowed)
{
    // Depending on the value of requestStatus, provide an appropriate response
    // such as notifying the user which functionality won't work as expected
}
```

## <a name="register-the-background-task"></a>Registrieren der Hintergrundaufgabe

Registrieren Sie die Hintergrundaufgabe, indem Sie die Funktion zum Registrieren der Hintergrundaufgabe aufrufen. Weitere Informationen zum Registrieren von Hintergrundaufgaben und die Definition der **RegisterBackgroundTask()** -Methode in der nachfolgende Beispielcode anzuzeigen finden Sie unter [Registrieren einer Hintergrundaufgabe](register-a-background-task.md).

> [!IMPORTANT]
> Für, die im gleichen Prozess wie Ihre app ausführen Hintergrundaufgaben, stellen Sie keine `entryPoint`. Legen Sie für, die von Ihrer app in einem separaten Prozess ausgeführt Hintergrundaufgaben, `entryPoint` auf den Namespace '.', und den Namen der Klasse, die Implementierung der Hintergrundaufgabe enthält.

```cs
string entryPoint = "Tasks.ExampleBackgroundTaskClass";
string taskName   = "Example hourly background task";

BackgroundTaskRegistration task = RegisterBackgroundTask(entryPoint, taskName, hourlyTrigger, userCondition);
```

```cppwinrt
std::wstring entryPoint{ L"Tasks.ExampleBackgroundTaskClass" };
std::wstring taskName{ L"Example hourly background task" };

Windows::ApplicationModel::Background::BackgroundTaskRegistration task{
    RegisterBackgroundTask(entryPoint, taskName, hourlyTrigger, userCondition) };
```

```cpp
String ^ entryPoint = "Tasks.ExampleBackgroundTaskClass";
String ^ taskName   = "Example hourly background task";

BackgroundTaskRegistration ^ task = RegisterBackgroundTask(entryPoint, taskName, hourlyTrigger, userCondition);
```

Parameter für die Registrierung von Hintergrundaufgaben werden zum Zeitpunkt der Registrierung überprüft. Bei ungültigen Registrierungsparametern wird ein Fehler zurückgegeben. Stellen Sie sicher, dass Ihre App problemlos mit Szenarien ohne erfolgreiche Registrierung von Hintergrundaufgaben zurechtkommt. Andernfalls stürzt die App unter Umständen ab, wenn sie so konzipiert ist, dass nach dem Versuch, eine Aufgabe zu registrieren, ein gültiges Registrierungsobjekt vorhanden sein muss.

## <a name="manage-resources-for-your-background-task"></a>Verwalten von Ressourcen für die Hintergrundaufgabe.

Um zu ermitteln, ob der Benutzer die Hintergrundaktivität Ihrer App begrenzt hat, verwenden Sie [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx). Achten Sie auf die Akkunutzung, und führen Sie Ihre App nur dann im Hintergrund aus, wenn dies zum Ausführen einer vom Benutzer gewünschten Aktion notwendig ist. Sehen Sie, dass die Einstellungen für Hintergrundaktivitäten [Optimieren von Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen über die Möglichkeiten Benutzer gesteuert werden können.

- Arbeitsspeicher: Optimieren Ihrer app Arbeitsspeicher und Energieverbrauch ist Schlüssel, um sicherzustellen, dass das Betriebssystem die Hintergrundaufgabe ausgeführt werden kann. Verwenden Sie die [Speicherverwaltungs-APIs](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) zu ermitteln, wie viel Arbeitsspeicher Ihre Hintergrundaufgabe verwendet wird. Je mehr Arbeitsspeicher Ihre Hintergrundaufgabe verwendet, desto schwieriger wird es für das Betriebssystem, weiter ausgeführt, wenn eine andere app im Vordergrund befindet. Der Benutzer hat letztendlich die Kontrolle über alle Hintergrundaktivitäten, die Ihre App ausführen kann, und kann die Auswirkungen Ihrer App auf den Akkuverbrauch erkennen.  
- CPU-Zeit: Hintergrundaufgaben sind durch die gesamtbetrachtungszeit-Nutzung Zeit sie auf Triggertyp basierend erhalten eingeschränkt.

Die für Hintergrundaufgaben geltenden Ressourcenbeschränkungen finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).

## <a name="remarks"></a>Hinweise

Ab Windows 10, ist es nicht mehr erforderlich ist, damit der Benutzer Ihre app zum Sperrbildschirm hinzufügen, um Hintergrundaufgaben zu nutzen.

Eine Hintergrundaufgabe läuft nur eine **TimeTrigger** verwenden, wenn Sie vorher [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufgerufen haben.

## <a name="related-topics"></a>Verwandte Themen

* [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md)
* [Beispiel für eine Hintergrundaufgabe code](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BackgroundTask)
* [Erstellen und Registrieren einer In-Process-Hintergrundaufgabe](create-and-register-an-inproc-background-task.md)
* [Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe](create-and-register-a-background-task.md)
* [Debuggen einer Hintergrundaufgabe](debug-a-background-task.md)
* [Deklarieren von Hintergrundaufgaben im Anwendungsmanifest](declare-background-tasks-in-the-application-manifest.md)
* [Freigeben von Speicher, wenn die App in den Hintergrund verschoben wird](reduce-memory-usage.md)
* [Behandeln einer abgebrochenen Hintergrundaufgabe](handle-a-cancelled-background-task.md)
* [So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)](http://go.microsoft.com/fwlink/p/?linkid=254345)
* [Überwachen des Status und Abschlusses von Hintergrundaufgaben](monitor-background-task-progress-and-completion.md)
* [Verschieben des Anhaltens der App mithilfe der erweiterten Ausführung](run-minimized-with-extended-execution.md)
* [Registrieren einer Hintergrundaufgabe](register-a-background-task.md)
* [Reagieren auf Systemereignisse mit Hintergrundaufgaben](respond-to-system-events-with-background-tasks.md)
* [Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md)
* [Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe](update-a-live-tile-from-a-background-task.md)
* [Verwenden eines Wartungsauslösers](use-a-maintenance-trigger.md)
