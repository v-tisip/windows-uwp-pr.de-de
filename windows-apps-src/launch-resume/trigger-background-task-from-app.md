---
author: TylerMSFT
title: Auslösen einer Hintergrundaufgabe in Ihrer App
description: Beschreibt, wie Sie eine Hintergrundaufgabe innerhalb einer Anwendung auslösen
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Trigger Hintergrundaufgabe, Hintergrundaufgabe
ms.localizationpriority: medium
ms.openlocfilehash: 5ccd171f53795ef71830ffb022d0468facb3ac4f
ms.sourcegitcommit: 914b38559852aaefe7e9468f6f53a7465bf36e30
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "3390460"
---
# <a name="trigger-a-background-task-from-within-your-app"></a>Auslösen einer Hintergrundaufgabe in Ihrer App

Hier erfahren Sie, wie Sie den [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger) zum Aktivieren einer Hintergrundaufgabe in Ihrer App verwenden.

Ein Beispiel für So erstellen Sie einen Anwendungs-Trigger finden Sie in diesem [Beispiel](https://github.com/Microsoft/Windows-universal-samples/blob/v2.0.0/Samples/BackgroundTask/cs/BackgroundTask/Scenario5_ApplicationTriggerTask.xaml.cs).

In diesem Thema wird davon ausgegangen, dass Sie eine Hintergrundaufgabe verfügen, die Sie von Ihrer Anwendung aktivieren möchten. Wenn Sie bereits über eine Hintergrundaufgabe besitzen, besteht eine Beispiel-Hintergrundaufgabe am [BackgroundActivity.cs](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackgroundActivation/cs/BackgroundActivity.cs). Oder führen Sie die Schritte in [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](create-and-register-a-background-task.md) , eine zu erstellen.

## <a name="why-use-an-application-trigger"></a>Gründe für die Verwendung eines Anwendungs-Triggers

Verwenden Sie eine **ApplicationTrigger** , Code in einem separaten Prozess von der Vordergrund-app auszuführen. Ein **ApplicationTrigger** ist geeignet, wenn Ihre app arbeiten, die im Hintergrund – ausgeführt werden soll, auch wenn der Benutzer die Vordergrund-app schließt. Wenn Hintergrundarbeiten anhalten sollten wenn die app geschlossen, oder sollte in den Zustand des Prozesses Vordergrund gebunden werden, und klicken Sie dann [Extended Execution](run-minimized-with-extended-execution.md) soll, stattdessen verwendet werden.

## <a name="create-an-application-trigger"></a>Erstellen Sie einen Anwendungs-trigger

Erstellen Sie eine neue [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger). Es könnte in einem Feld gespeichert werden, wie im folgenden Codeausschnitt erfolgt. Dies ist für Komfort, damit wir nicht um eine neue Instanz später zu erstellen, wenn wir den Trigger signalisieren möchten. Sie können jedoch jede Instanz **ApplicationTrigger** um den Trigger zu signalisieren.

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

Sie können eine Bedingung für Hintergrundaufgaben Steuerelement erstellen, wenn die Aufgabe ausgeführt wird. Eine Bedingung wird verhindert, dass die Hintergrundaufgabe ausgeführt wird, bis die Bedingung erfüllt ist. Weitere Informationen finden Sie unter [Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md).

In diesem Beispiel wird die Bedingung auf **InternetAvailable** festgelegt ist, sodass einmal ausgelöst, wird die Aufgabe nur ausgeführt, nachdem Zugriff auf das Internet verfügbar ist. Eine Liste mit möglichen Bedingungen finden Sie in [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).

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

Ausführlichere Informationen zu Bedingungen und Typen von Hintergrund-Triggern finden Sie unter [Unterstützung Ihrer app mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).

##  <a name="call-requestaccessasync"></a>Aufrufen von RequestAccessAsync()

Rufen Sie vor dem Registrieren der Hintergrundaufgabe **ApplicationTrigger** , [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700494) , um die Menge der Hintergrundaktivitäten zu ermitteln, die dem Benutzer ermöglicht, da der Benutzer Hintergrundaktivitäten für Ihre app deaktiviert haben möglicherweise ein. Sehen Sie, dass [Optimieren von Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen über die Möglichkeiten Benutzer die Einstellungen für Hintergrundaktivitäten steuern können.

```csharp
var requestStatus = await Windows.ApplicationModel.Background.BackgroundExecutionManager.RequestAccessAsync();
if (requestStatus != BackgroundAccessStatus.AlwaysAllowed)
{
   // Depending on the value of requestStatus, provide an appropriate response
   // such as notifying the user which functionality won't work as expected
}
```

## <a name="register-the-background-task"></a>Registrieren der Hintergrundaufgabe

Registrieren Sie die Hintergrundaufgabe, indem Sie die Funktion zum Registrieren der Hintergrundaufgabe aufrufen. Weitere Informationen zum Registrieren von Hintergrundaufgaben, und die Definition der **RegisterBackgroundTask()** -Methode im folgenden Beispielcode finden Sie unter [Registrieren einer Hintergrundaufgabe](register-a-background-task.md).

Wenn Sie erwägen, verwenden eine Anwendungs-Trigger, um die Lebensdauer der Vordergrund-Prozess zu erweitern, sollten Sie [Extended Execution](run-minimized-with-extended-execution.md) stattdessen. Die Anwendungs-Trigger dient zum Erstellen eines separat gehosteten Prozess Aufgaben in. Der folgende Codeausschnitt wird einen Out-of-Process-Hintergrund-Trigger registriert.

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

Bevor Sie die Hintergrundaufgabe auslösen, verwenden Sie [BackgroundTaskRegistration](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskRegistration) , um sicherzustellen, dass die Hintergrundaufgabe registriert ist. Ein guter Zeitpunkt, um sicherzustellen, dass alle Ihre Hintergrundaufgaben registriert sind, ist beim Starten der app.

Auslösen der Hintergrundaufgabe durch Aufrufen von [ApplicationTrigger.RequestAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtrigger). Jede Instanz **ApplicationTrigger** werden durchführen.

Beachten Sie, dass **ApplicationTrigger.RequestAsync** aufgerufen werden kann, von der Hintergrundaufgabe selbst, oder wenn die app im Hintergrund Zustand ausgeführt wird (siehe [App-Lebenszyklus](app-lifecycle.md) Weitere Informationen zur Anwendungszustände).
Es kann [DisabledByPolicy](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult) zurückgeben, wenn der Benutzer Energie oder Datenschutz-Richtlinien festgelegt hat, die verhindern, dass die app Hintergrundaktivitäten durchführen.
Darüber hinaus kann nur ein AppTrigger zu einem Zeitpunkt ausgeführt werden. Wenn Sie versuchen, eine AppTrigger auszuführen, während ein anderes bereits ausgeführt wird, wird die Funktion [CurrentlyRunning](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult)zurückgegeben.

```csharp
var result = await _AppTrigger.RequestAsync();
```

## <a name="manage-resources-for-your-background-task"></a>Verwalten von Ressourcen für die Hintergrundaufgabe

Um zu ermitteln, ob der Benutzer die Hintergrundaktivität Ihrer App begrenzt hat, verwenden Sie [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx). Achten Sie auf die Akkunutzung, und führen Sie Ihre App nur dann im Hintergrund aus, wenn dies zum Ausführen einer vom Benutzer gewünschten Aktion notwendig ist. Sehen Sie, dass [Optimieren von Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen über die Möglichkeiten Benutzer die Einstellungen für Hintergrundaktivitäten steuern können.  

- Arbeitsspeicher: Optimieren Ihrer app Arbeitsspeicher und Energieverbrauch ist Schlüssel, um sicherzustellen, dass das Betriebssystem die Hintergrundaufgabe ausgeführt werden kann. Verwenden Sie die [Speicherverwaltungs-APIs](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) zu ermitteln, wie viel Arbeitsspeicher Ihre Hintergrundaufgabe verwendet wird. Mehr Arbeitsspeicher Ihre Hintergrundaufgabe verwendet, desto schwieriger wird für das Betriebssystem, weiter ausgeführt, wenn eine andere app im Vordergrund befindet. Der Benutzer hat letztendlich die Kontrolle über alle Hintergrundaktivitäten, die Ihre App ausführen kann, und kann die Auswirkungen Ihrer App auf den Akkuverbrauch erkennen.  
- CPU-Zeit: Hintergrundaufgaben sind durch die Zeitspanne gesamtbetrachtungszeit-Nutzung erhalten sie Triggertyp Grundlage eingeschränkt. Durch die Anwendungs-Trigger ausgelöste Hintergrundaufgaben sind auf etwa 10 Minuten beschränkt.

Die für Hintergrundaufgaben geltenden Ressourcenbeschränkungen finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).

## <a name="remarks"></a>Hinweise

Ab Windows 10, ist es nicht mehr erforderlich ist, damit der Benutzer Ihre app zum Sperrbildschirm hinzufügen, um Hintergrundaufgaben zu nutzen.

Eine Hintergrundaufgabe ausgeführt wird nur mit einer **ApplicationTrigger** , wenn Sie vorher [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufgerufen haben.

## <a name="related-topics"></a>Verwandte Themen

* [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md)
* [Beispiel für eine Hintergrundaufgabe code](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BackgroundTask)
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
