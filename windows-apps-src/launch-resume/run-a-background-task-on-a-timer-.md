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
keywords: Windows 10, Uwp, Hintergrund Aufgabe
ms.localizationpriority: medium
ms.openlocfilehash: 25e3c76ae09ed6835f89f0d98c308f11c7a99624
ms.sourcegitcommit: 753dfcd0f9fdfc963579dd0b217b445c4b110a18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "2862800"
---
# <a name="run-a-background-task-on-a-timer"></a>Ausführen einer Hintergrundaufgabe für einen Timer

Erfahren Sie, wie die [**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843) verwenden, um einen einmaligen Hintergrundtask planen, oder führen Sie eine periodische Hintergrundaufgabe.

Finden Sie unter **Scenario4** im [Hintergrund Aktivierung Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BackgroundActivation) sehen Sie ein Beispiel zum Implementieren die Zeit ausgelöste Hintergrund beschrieben in diesem Thema.

In diesem Thema wird davon ausgegangen, dass Sie eine Hintergrundaufgabe verfügen, die in regelmäßigen Abständen oder zu einem bestimmten Zeitpunkt ausgeführt werden soll. Wenn Sie bereits eine Hintergrundaufgabe ist, ist an vorhanden eine Beispiel Hintergrundaufgabe [BackgroundActivity.cs](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackgroundActivation/cs/BackgroundActivity.cs). Oder führen Sie die Schritte in [Erstellen und Registrieren einer Hintergrundaufgabe in-Process](create-and-register-an-inproc-background-task.md) oder [Erstellen und Registrieren einer Hintergrundaufgabe Out-of-Process-](create-and-register-a-background-task.md) zu erstellen.

## <a name="create-a-time-trigger"></a>Erstellen eines Zeitauslösers

Erstellen Sie einen neuen Zeitauslöser ([**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843)). Der zweite Parameter (*OneShot*) gibt an, ob die Hintergrundaufgabe einmalig oder regelmäßig ausgeführt wird. Wenn *OneShot* auf „true“ festgelegt ist, gibt der erste Parameter (*FreshnessTime*) an, wie lange mit der Planung der Hintergrundaufgabe gewartet werden soll (in Minuten). Wenn *OneShot* auf „false“ festgelegt ist, gibt *FreshnessTime* die Häufigkeit an, mit der die Hintergrundaufgabe ausgeführt wird.

Der integrierte Timer für auf Desktop- oder Mobilgeräte ausgerichtete UWP-Apps führt Hintergrundaufgaben in einem 15-Minuten-Intervall aus. (Der Timer führt alle 15 Minuten, sodass das System muss nur einmal alle 15 Minuten reaktivieren, um apps reaktivieren, die Power speichert TimerTriggers--angefordert haben.)

- Wenn *FreshnessTime* auf 15Minuten und *OneShot* auf „true“ festgelegt ist, wird die Aufgabe einmalig innerhalb der ersten 15 und 30Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant. Wenn sie auf 25Minuten und *OneShot* auf „true“ festgelegt ist, wird die Aufgabe einmalig innerhalb der ersten 25 und 40Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant.

- Wenn *FreshnessTime* auf 15Minuten und *OneShot* auf „false“ festgelegt ist, wird die Aufgabe alle 15Minuten innerhalb der ersten 15 und 30Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant. Wenn sie auf „n” Minuten und *OneShot* auf „false“ festgelegt ist, wird die Aufgabe alle „n” Minuten innerhalb der ersten „n” und „n+15” Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant.

> [!NOTE]
> Wenn *FreshnessTime* auf weniger als 15 Minuten festgelegt ist, wird eine Ausnahme ausgelöst, wenn Sie versuchen, die Hintergrundaufgabe zu registrieren.
 
Angenommen, verursacht diese Trigger einen Hintergrundtask einmal pro Stunde ausgeführt.

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

Sie können eine Bedingung Hintergrund Aufgabe Steuerelement erstellen, wenn der Task ausgeführt wird. Eine Bedingung wird verhindert, dass die Hintergrundaufgabe ausführt, bis die Bedingung erfüllt ist. Weitere Informationen finden Sie unter [Festlegen von Bedingungen für die Ausführung einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md).

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

Ausführlichere Informationen auf Bedingungen und Arten von Triggern Hintergrund finden Sie unter [Unterstützung Ihrer app mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).

##  <a name="call-requestaccessasync"></a>Aufrufen von RequestAccessAsync()

Rufen Sie vor der Registrierung der Aufgabe **ApplicationTrigger** Hintergrund [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700494) , um die Hintergrundaktivitäten bestimmen, die dem Benutzer ermöglicht, da der Benutzer Hintergrundaktivitäten für Ihre app deaktiviert haben, kann ein. Finden Sie unter [Optimieren Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen zu den Arten Benutzern die Einstellungen für Hintergrundaktivitäten steuern können.

```cs
var requestStatus = await Windows.ApplicationModel.Background.BackgroundExecutionManager.RequestAccessAsync();
if (requestStatus != BackgroundAccessStatus.AlwaysAllowed)
{
    // Depending on the value of requestStatus, provide an appropriate response
    // such as notifying the user which functionality won't work as expected
}
```

## <a name="register-the-background-task"></a>Registrieren der Hintergrundaufgabe

Registrieren Sie die Hintergrundaufgabe, indem Sie die Funktion zum Registrieren der Hintergrundaufgabe aufrufen. Weitere Informationen zum Registrieren von Hintergrundaufgaben und sehen Sie die Definition der **RegisterBackgroundTask()** -Methode in der folgenden Beispielcode finden Sie unter [Registrieren eine Hintergrundaufgabe](register-a-background-task.md).

> [!IMPORTANT]
> Für Hintergrund in demselben Prozess wie Ihre app ausgeführten Aufgaben, stellen Sie keine `entryPoint`. Legen Sie für Hintergrund, auf denen Ihre app in einem eigenen Prozess ausgeführt Aufgaben, `entryPoint` werden den Namespace '. ", und den Namen der Klasse, die Implementierung Ihrer Hintergrund Aufgabe enthält.

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

## <a name="manage-resources-for-your-background-task"></a>Verwalten von Ressourcen für Ihre Hintergrundaufgabe

Um zu ermitteln, ob der Benutzer die Hintergrundaktivität Ihrer App begrenzt hat, verwenden Sie [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx). Achten Sie auf die Akkunutzung, und führen Sie Ihre App nur dann im Hintergrund aus, wenn dies zum Ausführen einer vom Benutzer gewünschten Aktion notwendig ist. Finden Sie unter [Optimieren Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen zu den Arten Benutzern die Einstellungen für Hintergrundaktivitäten steuern können.

- Arbeitsspeicher: Zur Optimierung Ihrer app Arbeitsspeicher und weniger Energie Verwendung ist Grundvoraussetzung, dass das Betriebssystem Hintergrundtask ausgeführt werden kann. Verwenden Sie die [APIs für die Verwaltung von Arbeitsspeicher](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) , um wie viel Arbeitsspeicher finden Sie unter Ihrer Hintergrundaufgabe verwendet wird. Mehr Arbeitsspeicher Ihrer Hintergrundaufgabe verwendet, desto mehr ist für das Betriebssystem aktiviert bleiben bei einer anderen Anwendung im Vordergrund befindet. Der Benutzer hat letztendlich die Kontrolle über alle Hintergrundaktivitäten, die Ihre App ausführen kann, und kann die Auswirkungen Ihrer App auf den Akkuverbrauch erkennen.  
- CPU-Zeit: Hintergrundaufgaben werden durch die Zeitspanne Wand Uhr Usage erhalten sie Triggertyp Basis begrenzt.

Die für Hintergrundaufgaben geltenden Ressourcenbeschränkungen finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).

## <a name="remarks"></a>Hinweise

Beginnend mit Windows 10, ist es nicht mehr erforderlich für den Benutzer Ihre app auf dem Sperrbildschirm hinzufügen, um Hintergrundaufgaben nutzen.

Hintergrund läuft nur unter Verwendung einer **TimeTrigger** , wenn Sie zuerst [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufgerufen haben.

## <a name="related-topics"></a>Verwandte Themen

* [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md)
* [Hintergrund Task-Codebeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BackgroundTask)
* [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen](create-and-register-an-inproc-background-task.md)
* [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses](create-and-register-a-background-task.md)
* [Debuggen einer Hintergrundaufgabe](debug-a-background-task.md)
* [Deklarieren von Hintergrundaufgaben im Anwendungsmanifest](declare-background-tasks-in-the-application-manifest.md)
* [Geben Sie Speicher frei, wenn Ihre App in den Hintergrund verschoben wird](reduce-memory-usage.md)
* [Behandeln einer abgebrochenen Hintergrundaufgabe](handle-a-cancelled-background-task.md)
* [So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)](http://go.microsoft.com/fwlink/p/?linkid=254345)
* [Überwachen des Status und Abschlusses von Hintergrundaufgaben](monitor-background-task-progress-and-completion.md)
* [Verschieben der angehaltenen App mithilfe der erweiterten Ausführung](run-minimized-with-extended-execution.md)
* [Registrieren einer Hintergrundaufgabe](register-a-background-task.md)
* [Reagieren auf Systemereignisse mit Hintergrundaufgaben](respond-to-system-events-with-background-tasks.md)
* [Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md)
* [Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe](update-a-live-tile-from-a-background-task.md)
* [Verwenden eines Wartungsauslösers](use-a-maintenance-trigger.md)
