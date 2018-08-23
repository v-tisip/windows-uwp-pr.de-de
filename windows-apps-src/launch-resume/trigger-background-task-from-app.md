---
author: TylerMSFT
title: Auslösen einer Hintergrundaufgabe in Ihrer App
description: Beschreibt das Auslösen der Hintergrundaufgabe von innerhalb einer Anwendung
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Hintergrund Aufgabe Trigger, Hintergrundaufgabe
ms.localizationpriority: medium
ms.openlocfilehash: 5ccd171f53795ef71830ffb022d0468facb3ac4f
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2816352"
---
# <a name="trigger-a-background-task-from-within-your-app"></a>Auslösen einer Hintergrundaufgabe in Ihrer App

Hier erfahren Sie, wie Sie den [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger) zum Aktivieren einer Hintergrundaufgabe in Ihrer App verwenden.

Ein Beispiel dafür, wie Sie zum Erstellen eines Anwendung Triggers finden in diesem [Beispiel](https://github.com/Microsoft/Windows-universal-samples/blob/v2.0.0/Samples/BackgroundTask/cs/BackgroundTask/Scenario5_ApplicationTriggerTask.xaml.cs).

In diesem Thema wird davon ausgegangen, dass Sie eine Hintergrundaufgabe verfügen, die Sie in Ihrer Anwendung aktivieren möchten. Wenn Sie bereits eine Hintergrundaufgabe ist, ist an vorhanden eine Beispiel Hintergrundaufgabe [BackgroundActivity.cs](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackgroundActivation/cs/BackgroundActivity.cs). Oder führen Sie die Schritte in [Erstellen und Registrieren einer Hintergrundaufgabe Out-of-Process-](create-and-register-a-background-task.md) zu erstellen.

## <a name="why-use-an-application-trigger"></a>Gründe für die Verwendung eines Anwendung Triggers

Verwenden Sie ein **ApplicationTrigger** zum Ausführen von Code in einem gesonderten Prozess von der Vordergrund-app. Ein **ApplicationTrigger** ist geeignet, wenn Ihre app Arbeit, die im Hintergrund – ausgeführt werden soll verfügt, auch wenn der Benutzer die Vordergrund-app wird geschlossen. Wenn Hintergrund Arbeit anhalten sollte Wenn die app wird geschlossen oder sollte auf den Status des Prozesses Vordergrund gebunden, und klicken Sie dann [Erweitert Ausführung](run-minimized-with-extended-execution.md) soll, stattdessen verwendet werden.

## <a name="create-an-application-trigger"></a>Erstellen Sie einen Anwendung trigger

Erstellen Sie eine neue [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger). Es konnte in einem Feld gespeichert werden, wie im folgenden Codeausschnitt erfolgt. Dies ist der Einfachheit, damit es nicht um eine neue Instanz später erstellen, wenn wir den Auslöser signalisieren möchten. Aber Sie können jede Instanz **ApplicationTrigger** verwenden, um den Auslöser signalisieren.

```csharp
// _AppTrigger is an ApplicationTrigger field defined at a scope that will keep it alive
// as long as you need to trigger the background task.
// Or, you could create a new ApplicationTrigger instance and use that when you want to
// trigger the background task.
_AppTrigger = new ApplicationTrigger();
```

```cppwinrt
// _AppTrigger is an ApplicationTrigger field defined at a scope that will keep it alive
// as long as you need to trigger the background task.
// Or, you could create a new ApplicationTrigger instance and use that when you want to
// trigger the background task.
Windows::ApplicationModel::Background::ApplicationTrigger _AppTrigger;
```

```cpp
// _AppTrigger is an ApplicationTrigger field defined at a scope that will keep it alive
// as long as you need to trigger the background task.
// Or, you could create a new ApplicationTrigger instance and use that when you want to
// trigger the background task.
ApplicationTrigger ^ _AppTrigger = ref new ApplicationTrigger();
```

## <a name="optional-add-a-condition"></a>(Optional) Hinzufügen einer Bedingung

Sie können eine Bedingung Hintergrund Aufgabe Steuerelement erstellen, wenn der Task ausgeführt wird. Eine Bedingung wird verhindert, dass die Hintergrundaufgabe ausführt, bis die Bedingung erfüllt ist. Weitere Informationen finden Sie unter [Festlegen von Bedingungen für die Ausführung einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md).

In diesem Beispiel wird die Bedingung auf **InternetAvailable** festgelegt ist, sodass einmal ausgelöst, die Aufgabe nur einmal ausgeführt Internetzugang verfügbar ist. Eine Liste mit möglichen Bedingungen finden Sie in [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).

```csharp
SystemCondition internetCondition = new SystemCondition(SystemConditionType.InternetAvailable);
```

```cppwinrt
Windows::ApplicationModel::Background::SystemCondition internetCondition{
    Windows::ApplicationModel::Background::SystemConditionType::InternetAvailable };
```

```cpp
SystemCondition ^ internetCondition = ref new SystemCondition(SystemConditionType::InternetAvailable)
```

Ausführlichere Informationen auf Bedingungen und Arten von Triggern Hintergrund finden Sie unter [Unterstützung Ihrer app mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).

##  <a name="call-requestaccessasync"></a>Aufrufen von RequestAccessAsync()

Rufen Sie vor der Registrierung der Aufgabe **ApplicationTrigger** Hintergrund [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700494) , um die Hintergrundaktivitäten bestimmen, die dem Benutzer ermöglicht, da der Benutzer Hintergrundaktivitäten für Ihre app deaktiviert haben, kann ein. Finden Sie unter [Optimieren Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen zu den Arten Benutzern die Einstellungen für Hintergrundaktivitäten steuern können.

```csharp
var requestStatus = await Windows.ApplicationModel.Background.BackgroundExecutionManager.RequestAccessAsync();
if (requestStatus != BackgroundAccessStatus.AlwaysAllowed)
{
   // Depending on the value of requestStatus, provide an appropriate response
   // such as notifying the user which functionality won't work as expected
}
```

## <a name="register-the-background-task"></a>Registrieren der Hintergrundaufgabe

Registrieren Sie die Hintergrundaufgabe, indem Sie die Funktion zum Registrieren der Hintergrundaufgabe aufrufen. Weitere Informationen zum Registrieren von Hintergrundaufgaben und sehen Sie die Definition der **RegisterBackgroundTask()** -Methode in der folgenden Beispielcode finden Sie unter [Registrieren eine Hintergrundaufgabe](register-a-background-task.md).

Sie verwenden eine Anwendung Trigger zum Erweitern der Lebensdauer des Upgradevorgangs Vordergrund erwägen, sollten Sie [Erweiterte Ausführung](run-minimized-with-extended-execution.md) stattdessen verwenden. Die Anwendung Trigger dient zum Erstellen eines Prozesses separat gehosteten Aufgaben in. Im folgenden Codeausschnitt wird einen Out-of-Process Hintergrund Trigger registriert.

```csharp
string entryPoint = "Tasks.ExampleBackgroundTaskClass";
string taskName   = "Example application trigger";

BackgroundTaskRegistration task = RegisterBackgroundTask(entryPoint, taskName, appTrigger, internetCondition);
```

```cppwinrt
std::wstring entryPoint{ L"Tasks.ExampleBackgroundTaskClass" };
std::wstring taskName{ L"Example application trigger" };

Windows::ApplicationModel::Background::BackgroundTaskRegistration task{
    RegisterBackgroundTask(entryPoint, taskName, appTrigger, internetCondition) };
```

```cpp
String ^ entryPoint = "Tasks.ExampleBackgroundTaskClass";
String ^ taskName   = "Example application trigger";

BackgroundTaskRegistration ^ task = RegisterBackgroundTask(entryPoint, taskName, appTrigger, internetCondition);
```

Parameter für die Registrierung von Hintergrundaufgaben werden zum Zeitpunkt der Registrierung überprüft. Bei ungültigen Registrierungsparametern wird ein Fehler zurückgegeben. Stellen Sie sicher, dass Ihre App problemlos mit Szenarien ohne erfolgreiche Registrierung von Hintergrundaufgaben zurechtkommt. Andernfalls stürzt die App unter Umständen ab, wenn sie so konzipiert ist, dass nach dem Versuch, eine Aufgabe zu registrieren, ein gültiges Registrierungsobjekt vorhanden sein muss.

## <a name="trigger-the-background-task"></a>Auslösen der Hintergrundaufgabe

Bevor Sie den Vorgang Hintergrund auslösen, verwenden Sie [BackgroundTaskRegistration](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskRegistration) , um sicherzustellen, dass die Hintergrundaufgabe registriert ist. Stellen Sie sicher, dass alle von Vorgängen Hintergrund registriert werden sollten Sie jetzt ist während der app-Start.

Auslösen der Hintergrundaufgabe durch Aufrufen von [ApplicationTrigger.RequestAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtrigger). Jede Instanz **ApplicationTrigger** geschieht.

Beachten Sie, dass **ApplicationTrigger.RequestAsync** aus dem Hintergrund Vorgang selbst, oder wenn die app im Hintergrund Zustand "aktiv" ist nicht aufgerufen werden können (Weitere Informationen zum Anwendungsstatus finden Sie unter [App-Lebenszyklus](app-lifecycle.md) ).
Es kann [DisabledByPolicy](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult) zurück, wenn der Benutzer Energie oder private Richtlinien festgelegt hat, die verhindern, dass die app Hintergrundaktivität ausführen.
Darüber hinaus kann nur eine AppTrigger zu einem Zeitpunkt ausgeführt werden. Wenn Sie versuchen, ein AppTrigger auszuführen, während eine andere bereits ausgeführt wird, gibt die Funktion [CurrentlyRunning](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult)zurück.

```csharp
var result = await _AppTrigger.RequestAsync();
```

## <a name="manage-resources-for-your-background-task"></a>Verwalten von Ressourcen für Ihre Hintergrundaufgabe

Um zu ermitteln, ob der Benutzer die Hintergrundaktivität Ihrer App begrenzt hat, verwenden Sie [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx). Achten Sie auf die Akkunutzung, und führen Sie Ihre App nur dann im Hintergrund aus, wenn dies zum Ausführen einer vom Benutzer gewünschten Aktion notwendig ist. Finden Sie unter [Optimieren Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen zu den Arten Benutzern die Einstellungen für Hintergrundaktivitäten steuern können.  

- Arbeitsspeicher: Zur Optimierung Ihrer app Arbeitsspeicher und weniger Energie Verwendung ist Grundvoraussetzung, dass das Betriebssystem Hintergrundtask ausgeführt werden kann. Verwenden Sie die [APIs für die Verwaltung von Arbeitsspeicher](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) , um wie viel Arbeitsspeicher finden Sie unter Ihrer Hintergrundaufgabe verwendet wird. Mehr Arbeitsspeicher Ihrer Hintergrundaufgabe verwendet, desto mehr ist für das Betriebssystem aktiviert bleiben bei einer anderen Anwendung im Vordergrund befindet. Der Benutzer hat letztendlich die Kontrolle über alle Hintergrundaktivitäten, die Ihre App ausführen kann, und kann die Auswirkungen Ihrer App auf den Akkuverbrauch erkennen.  
- CPU-Zeit: Hintergrundaufgaben werden durch die Zeitspanne Wand Uhr Usage erhalten sie Triggertyp Basis begrenzt. Hintergrundaufgaben, die von der Anwendung Trigger ausgelöst können nur etwa 10 Minuten.

Die für Hintergrundaufgaben geltenden Ressourcenbeschränkungen finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).

## <a name="remarks"></a>Hinweise

Beginnend mit Windows 10, ist es nicht mehr erforderlich für den Benutzer Ihre app auf dem Sperrbildschirm hinzufügen, um Hintergrundaufgaben nutzen.

Hintergrund läuft nur unter Verwendung einer **ApplicationTrigger** , wenn Sie zuerst [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufgerufen haben.

## <a name="related-topics"></a>Verwandte Themen

* [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md)
* [Hintergrund Task-Codebeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BackgroundTask)
* [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb des Prozesses](create-and-register-an-inproc-background-task.md)
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
