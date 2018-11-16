---
author: TylerMSFT
title: Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe
description: Erstellen Sie eine Out-of-Process-Hintergrundaufgabenklasse, und registrieren Sie sie für die Ausführung, wenn Ihre App nicht im Vordergrund ausgeführt wird.
ms.assetid: 4F98F6A3-0D3D-4EFB-BA8E-30ED37AE098B
ms.author: twhitney
ms.date: 07/02/2018
ms.topic: article
keywords: Windows 10, Uwp, Hintergrundaufgabe, für die
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
ms.openlocfilehash: 8d32b4559e91cc898944f3767d4b082935359d49
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6846761"
---
# <a name="create-and-register-an-out-of-process-background-task"></a>Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe

**Wichtige APIs**

-   [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)
-   [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)
-   [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781)

Erstellen Sie eine Hintergrundaufgabenklasse, und registrieren Sie diese für die Ausführung, wenn sich die App nicht im Vordergrund befindet. In diesem Thema wird gezeigt, wie Sie eine Hintergrundaufgabe erstellen und registrieren, die in einem vom App-Prozess getrennten Prozess ausgeführt wird. Informationen zum Ausführen von Hintergrundarbeiten direkt in der Vordergrundanwendung finden Sie unter [Erstellen und Registrieren einer In-Process-Hintergrundaufgabe](create-and-register-an-inproc-background-task.md).

> [!NOTE]
> Wenn Sie eine Hintergrundaufgabe zur Medienwiedergabe im Hintergrund verwenden, finden Sie unter [Wiedergeben von Medien im Hintergrund](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio) Informationen zu Verbesserungen in Windows10, Version1607, die dies wesentlich erleichtern.

## <a name="create-the-background-task-class"></a>Erstellen einer Hintergrundaufgabenklasse

Sie können Code im Hintergrund ausführen, indem Sie Klassen schreiben, die die [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)-Schnittstelle implementieren. Dieser Code wird ausgeführt, wenn ein bestimmtes Ereignis ausgelöst wird, verwenden, z. B. [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839) oder [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700517).

Die folgenden Schritte zeigen, wie Sie eine neue Klasse zum Implementieren der [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)-Schnittstelle schreiben.

1.  Erstellen Sie ein neues Projekt für Hintergrundaufgaben, und fügen Sie es zu Ihrer Projektmappe hinzu. Zu diesem Zweck mit der rechten Maustaste auf Ihren Projektmappenknoten im **Projektmappen-Explorer** , und wählen Sie **Hinzufügen** \> **Neues Projekt**. Wählen Sie den Projekttyp **Windows-Runtime-Komponente** , nennen Sie das Projekt, und klicken Sie auf OK.
2.  Verweisen Sie auf das Hintergrundaufgabenprojekt aus dem Projekt für UWP-Apps (Universelle Windows-Plattform). Für eine C#- oder C++-app in Ihrem app-Projekt mit der rechten Maustaste auf **Verweise** , und wählen Sie **Neuen Verweis hinzufügen**. Wählen Sie unter **Projektmappe** die Option **Projekte**. Wählen Sie dann den Namen Ihres Hintergrundaufgabenprojekts aus, und klicken Sie auf **OK**.
3.  Fügen Sie auf das hintergrundaufgabenprojekt eine neue Klasse, die [**IBackgroundTask**](/uwp/api/Windows.ApplicationModel.Background.IBackgroundTask) -Schnittstelle implementiert. Die [**IBackgroundTask.Run**](/uwp/api/windows.applicationmodel.background.ibackgroundtask.run) -Methode ist ein erforderlicher Einstiegspunkt und, die aufgerufen wird, wenn das angegebene Ereignis ausgelöst wird. Diese Methode ist in jeder Hintergrundaufgabe erforderlich.

> [!NOTE]
> Die hintergrundaufgabenklasse selbst&mdash;und alle anderen Klassen im hintergrundaufgabenprojekt&mdash;müssen **Öffentliche** Klassen, die **versiegelt** (oder **letzte**) sind.

Der folgende Beispielcode zeigt einen sehr einfachen Startpunkt für eine hintergrundaufgabenklasse.

```csharp
// ExampleBackgroundTask.cs
using Windows.ApplicationModel.Background;

namespace Tasks
{
    public sealed class ExampleBackgroundTask : IBackgroundTask
    {
        public void Run(IBackgroundTaskInstance taskInstance)
        {
            
        }        
    }
}
```

```cppwinrt
// First, add ExampleBackgroundTask.idl, and then build.
// ExampleBackgroundTask.idl
namespace Tasks
{
    [default_interface]
    runtimeclass ExampleBackgroundTask : Windows.ApplicationModel.Background.IBackgroundTask
    {
        ExampleBackgroundTask();
    }
}

// ExampleBackgroundTask.h
#pragma once

#include "ExampleBackgroundTask.g.h"

namespace winrt::Tasks::implementation
{
    struct ExampleBackgroundTask : ExampleBackgroundTaskT<ExampleBackgroundTask>
    {
        ExampleBackgroundTask() = default;

        void Run(Windows::ApplicationModel::Background::IBackgroundTaskInstance const& taskInstance);
    };
}

namespace winrt::Tasks::factory_implementation
{
    struct ExampleBackgroundTask : ExampleBackgroundTaskT<ExampleBackgroundTask, implementation::ExampleBackgroundTask>
    {
    };
}

// ExampleBackgroundTask.cpp
#include "pch.h"
#include "ExampleBackgroundTask.h"

namespace winrt::Tasks::implementation
{
    void ExampleBackgroundTask::Run(Windows::ApplicationModel::Background::IBackgroundTaskInstance const& taskInstance)
    {
        throw hresult_not_implemented();
    }
}
```

```cpp
// ExampleBackgroundTask.h
#pragma once

using namespace Windows::ApplicationModel::Background;

namespace Tasks
{
    public ref class ExampleBackgroundTask sealed : public IBackgroundTask
    {

    public:
        ExampleBackgroundTask();

        virtual void Run(IBackgroundTaskInstance^ taskInstance);
        void OnCompleted(
            BackgroundTaskRegistration^ task,
            BackgroundTaskCompletedEventArgs^ args
        );
    };
}

// ExampleBackgroundTask.cpp
#include "ExampleBackgroundTask.h"

using namespace Tasks;

void ExampleBackgroundTask::Run(IBackgroundTaskInstance^ taskInstance)
{
}
```

4.  Wenn asynchroner Code in der Hintergrundaufgabe ausgeführt wird, muss in der Hintergrundaufgabe eine Verzögerung verwendet werden. Wenn Sie keine Verzögerung verwenden, können dann die Hintergrund unerwartet beendet werden, wenn die **Run** -Methode zurückgegeben wird, bevor alle asynchronen Vorgänge bis zum Abschluss ausgeführt wurde.

Fordern Sie die Verzögerung in der **Run** -Methode vor Aufruf der asynchronen Methode. Speichern Sie die Verzögerung auf einen Daten Klassenmember, damit es von der asynchronen Methode zugegriffen werden kann. Deklarieren Sie das Objekt so, dass die Verzögerung nach Abschluss des asynchronen Codes abgeschlossen wird.

Der folgende Beispielcode ruft die Verzögerung, speichert sie und gibt sie nach Abschluss des asynchronen Codes frei.

```csharp
BackgroundTaskDeferral _deferral; // Note: defined at class scope so that we can mark it complete inside the OnCancel() callback if we choose to support cancellation
public async void Run(IBackgroundTaskInstance taskInstance)
{
    _deferral = taskInstance.GetDeferral()
    //
    // TODO: Insert code to start one or more asynchronous methods using the
    //       await keyword, for example:
    //
    // await ExampleMethodAsync();
    //

    _deferral.Complete();
}
```

```cppwinrt
// ExampleBackgroundTask.h
...
private:
    Windows::ApplicationModel::Background::BackgroundTaskDeferral m_deferral{ nullptr };

// ExampleBackgroundTask.cpp
...
Windows::Foundation::IAsyncAction ExampleBackgroundTask::Run(
    Windows::ApplicationModel::Background::IBackgroundTaskInstance const& taskInstance)
{
    m_deferral = taskInstance.GetDeferral(); // Note: defined at class scope so that we can mark it complete inside the OnCancel() callback if we choose to support cancellation.
    // TODO: Modify the following line of code to call a real async function.
    co_await ExampleCoroutineAsync(); // Run returns at this point, and resumes when ExampleCoroutineAsync completes.
    m_deferral.Complete();
}
```

```cpp
void ExampleBackgroundTask::Run(IBackgroundTaskInstance^ taskInstance)
{
    m_deferral = taskInstance->GetDeferral(); // Note: defined at class scope so that we can mark it complete inside the OnCancel() callback if we choose to support cancellation.

    //
    // TODO: Modify the following line of code to call a real async function.
    //       Note that the task<void> return type applies only to async
    //       actions. If you need to call an async operation instead, replace
    //       task<void> with the correct return type.
    //
    task<void> myTask(ExampleFunctionAsync());

    myTask.then([=]() {
        m_deferral->Complete();
    });
}
```

> [!NOTE]
> In C# werden asynchrone Methoden für Hintergrundaufgaben mithilfe der Schlagwörter **async/await** aufgerufen. In C++ / CX ein ähnliches Ergebnis kann mithilfe einer Aufgabenabfolge erreicht werden.

Weitere Informationen zu asynchronen Mustern finden Sie unter [Asynchrone Programmierung](https://msdn.microsoft.com/library/windows/apps/mt187335). Weitere Beispiele zum Verhindern der vorzeitigen Beendigung einer Hintergrundaufgabe mithilfe von Verzögerungen finden Sie im [Beispiel zu Hintergrundaufgaben](http://go.microsoft.com/fwlink/p/?LinkId=618666).

Die folgenden Schritte werden in einer Ihrer App-Klassen durchgeführt (beispielsweise in "MainPage.xaml.cs").

> [!NOTE]
> Sie können auch eine Funktion für die Registrierung von Hintergrundaufgaben dedicated erstellen&mdash;finden Sie unter [Registrieren einer Hintergrundaufgabe](register-a-background-task.md). In diesem Fall anstelle der nächsten drei Schritte können einfach den Auslöser konstruieren und der Registrierungsfunktion zusammen mit dem Aufgabennamen, Einstiegspunkt und (optional) eine Bedingung zur Verfügung stellen.

## <a name="register-the-background-task-to-run"></a>Registrieren der auszuführenden Hintergrundaufgabe

1.  Erfahren Sie, ob die Hintergrundaufgabe bereits registriert ist, durch die Eigenschaft [**BackgroundTaskRegistration.AllTasks**](https://msdn.microsoft.com/library/windows/apps/br224787) durchlaufen. Dieser Schritt ist sehr wichtig. Sollte Ihre App nicht überprüfen, ob Hintergrundaufgaberegistrierungen vorhanden sind, könnte es passieren, dass sie die Aufgabe mehrere Male registriert, was zu Leistungseinbrüchen führt und die verfügbare CPU-Zeit der Aufgabe maximiert, bevor die Arbeit abgeschlossen werden kann.

Das folgende Beispiel durchläuft die **AllTasks** -Eigenschaft und legt eine kennzeichenvariable auf "true", wenn die Aufgabe bereits registriert ist.

```csharp
var taskRegistered = false;
var exampleTaskName = "ExampleBackgroundTask";

foreach (var task in BackgroundTaskRegistration.AllTasks)
{
    if (task.Value.Name == exampleTaskName)
    {
        taskRegistered = true;
        break;
    }
}
```

```cppwinrt
std::wstring exampleTaskName{ L"ExampleBackgroundTask" };

auto allTasks{ Windows::ApplicationModel::Background::BackgroundTaskRegistration::AllTasks() };

bool taskRegistered{ false };
for (auto const& task : allTasks)
{
    if (task.Value().Name() == exampleTaskName)
    {
        taskRegistered = true;
        break;
    }
}

// The code in the next step goes here.
```

```cpp
boolean taskRegistered = false;
Platform::String^ exampleTaskName = "ExampleBackgroundTask";

auto iter = BackgroundTaskRegistration::AllTasks->First();
auto hascur = iter->HasCurrent;

while (hascur)
{
    auto cur = iter->Current->Value;

    if(cur->Name == exampleTaskName)
    {
        taskRegistered = true;
        break;
    }

    hascur = iter->MoveNext();
}
```

2.  Wenn die Hintergrundaufgabe noch nicht registriert ist, verwenden Sie [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768), um eine Instanz Ihrer Hintergrundaufgabe zu generieren. Bei dem Einstiegspunkt der Aufgabe sollte es sich um den Namen der Hintergrundaufgabenklasse mit dem Namespace als Präfix handeln.

Der Hintergrundaufgabenauslöser bestimmt, ob die Hintergrundaufgabe ausgeführt wird. Eine Liste mit möglichen Auslösern erhalten Sie unter [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839).

Beispielsweise wird dieser Code erstellt eine neue Hintergrundaufgabe und wird ausgeführt, wenn der Trigger **TimeZoneChanged** tritt auf:

```csharp
var builder = new BackgroundTaskBuilder();

builder.Name = exampleTaskName;
builder.TaskEntryPoint = "Tasks.ExampleBackgroundTask";
builder.SetTrigger(new SystemTrigger(SystemTriggerType.TimeZoneChange, false));
```

```cppwinrt
if (!taskRegistered)
{
    Windows::ApplicationModel::Background::BackgroundTaskBuilder builder;
    builder.Name(exampleTaskName);
    builder.TaskEntryPoint(L"Tasks.ExampleBackgroundTask");
    builder.SetTrigger(Windows::ApplicationModel::Background::SystemTrigger{
        Windows::ApplicationModel::Background::SystemTriggerType::TimeZoneChange, false });
    // The code in the next step goes here.
}
```

```cpp
auto builder = ref new BackgroundTaskBuilder();

builder->Name = exampleTaskName;
builder->TaskEntryPoint = "Tasks.ExampleBackgroundTask";
builder->SetTrigger(ref new SystemTrigger(SystemTriggerType::TimeZoneChange, false));
```

3.  Sie können eine Bedingung hinzufügen, die bestimmt, wann Ihre Aufgabe ausgeführt wird, nachdem das Auslöseereignis eintritt (optional). Wenn Sie zum Beispiel möchten, dass die Aufgabe erst ausgeführt wird, wenn der Benutzer anwesend ist, verwenden Sie die Bedingung **UserPresent**. Eine Liste mit möglichen Bedingungen finden Sie in [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).

Der folgende Beispielcode weist eine Bedingung zu, die die Anwesenheit des Benutzers voraussetzt:

```csharp
builder.AddCondition(new SystemCondition(SystemConditionType.UserPresent));
```

```cppwinrt
builder.AddCondition(Windows::ApplicationModel::Background::SystemCondition{ Windows::ApplicationModel::Background::SystemConditionType::UserPresent });
// The code in the next step goes here.
```

```cpp
builder->AddCondition(ref new SystemCondition(SystemConditionType::UserPresent));
```

4.  Registrieren Sie die Hintergrundaufgabe, indem Sie die Register-Methode für das [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)-Objekt aufrufen. Speichern Sie das [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786)-Ergebnis, sodass es im nächsten Schritt verwendet werden kann.

Der folgende Code registriert die Hintergrundaufgabe und speichert das Ergebnis:

```csharp
BackgroundTaskRegistration task = builder.Register();
```

```cppwinrt
Windows::ApplicationModel::Background::BackgroundTaskRegistration task{ builder.Register() };
```

```cpp
BackgroundTaskRegistration^ task = builder->Register();
```

> [!NOTE]
> Universelle Windows-Apps müssen jedoch [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen, bevor Hintergrundtriggertypen registriert werden.

Verwenden Sie den **ServicingComplete**-Trigger (siehe [SystemTriggerType](https://msdn.microsoft.com/library/windows/apps/br224839)) zum Ausführen von Konfigurationsänderungen nach dem Update wie Migrieren der Datenbank der App und Registrieren von Hintergrundaufgaben, um sicherzustellen, dass Ihre universelle Windows-App nach der Veröffentlichung eines Updates weiterhin ordnungsgemäß ausgeführt wird. Es empfiehlt sich, die Registrierung von Hintergrundaufgaben im Zusammenhang mit der vorherigen Version der App aufzuheben (siehe [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471)) und die Hintergrundaufgaben für die neue Version der App zu registrieren (siehe [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485)).

Weitere Informationen finden Sie unter [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md).

## <a name="handle-background-task-completion-using-event-handlers"></a>Behandeln des Abschlusses der Hintergrundaufgabe mithilfe von Ereignishandlern

Sie sollten eine Methode mit dem [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781)-Element registrieren, damit Ihre App Ergebnisse von der Hintergrundaufgabe abrufen kann. Wenn die app gestartet oder fortgesetzt wird, wird die markierte Methode aufgerufen werden, wenn die Hintergrundaufgabe seit dem letzten abgeschlossen hat, die die app im Vordergrund befand. (Die OnCompleted-Methode wird sofort aufgerufen, wenn die Hintergrundaufgabe abgeschlossen wird, während sich Ihre App im Vordergrund befindet.)

1.  Schreiben Sie eine OnCompleted-Methode, um den Abschluss von Hintergrundaufgaben zu behandeln. Das Ergebnis der Hintergrundaufgabe kann z.B. eine Aktualisierung der Benutzeroberfläche auslösen. Das hier gezeigte Methodenprofil ist für die OnCompleted-Ereignishandlermethode erforderlich, obwohl dieses Beispiel nicht den *args*-Parameter verwendet.

Der folgende Beispielcode erkennt den Abschluss der Hintergrundaufgabe und ruft eine Beispielmethode zur Aktualisierung der Benutzeroberfläche auf, die eine Meldungszeichenfolge erfordert.

```csharp
private void OnCompleted(IBackgroundTaskRegistration task, BackgroundTaskCompletedEventArgs args)
{
    var settings = Windows.Storage.ApplicationData.Current.LocalSettings;
    var key = task.TaskId.ToString();
    var message = settings.Values[key].ToString();
    UpdateUI(message);
}
```

```cppwinrt
void UpdateUI(winrt::hstring const& message)
{
    MyTextBlock().Dispatcher().RunAsync(Windows::UI::Core::CoreDispatcherPriority::Normal, [=]()
    {
        MyTextBlock().Text(message);
    });
}

void OnCompleted(
    Windows::ApplicationModel::Background::BackgroundTaskRegistration const& sender,
    Windows::ApplicationModel::Background::BackgroundTaskCompletedEventArgs const& /* args */)
{
    // You'll previously have inserted this key into local settings.
    auto settings{ Windows::Storage::ApplicationData::Current().LocalSettings().Values() };
    auto key{ winrt::to_hstring(sender.TaskId()) };
    auto message{ winrt::unbox_value<winrt::hstring>(settings.Lookup(key)) };

    UpdateUI(message);
}
```

```cpp
void MainPage::OnCompleted(BackgroundTaskRegistration^ task, BackgroundTaskCompletedEventArgs^ args)
{
    auto settings = ApplicationData::Current->LocalSettings->Values;
    auto key = task->TaskId.ToString();
    auto message = dynamic_cast<String^>(settings->Lookup(key));
    UpdateUI(message);
}
```

> [!NOTE]
> Aktualisierungen der Benutzeroberfläche sollten asynchron durchgeführt werden, um den Benutzeroberflächenthread nicht zu blockieren. Ein Beispiel dazu finden Sie in der UpdateUI-Methode im [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666).

2.  Gehen Sie dorthin zurück, wo Sie die Hintergrundaufgabe registriert haben. Fügen Sie nach dieser Codezeile ein neues [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781)-Objekt hinzu. Stellen Sie Ihre OnCompleted-Methode als Parameter für den **BackgroundTaskCompletedEventHandler**-Konstruktor zur Verfügung.

Der folgende Beispielcode fügt dem [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786)-Element ein [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781)-Element hinzu:

```csharp
task.Completed += new BackgroundTaskCompletedEventHandler(OnCompleted);
```

```cppwinrt
task.Completed({ this, &MainPage::OnCompleted });
```

```cpp
task->Completed += ref new BackgroundTaskCompletedEventHandler(this, &MainPage::OnCompleted);
```

## <a name="declare-in-the-app-manifest-that-your-app-uses-background-tasks"></a>Deklarieren Sie in der app-Manifest, dass Ihre app Hintergrundaufgaben verwendet

Bevor Ihre App Hintergrundaufgaben ausführen kann, müssen Sie alle Hintergrundaufgaben im App-Manifest deklarieren. Wenn Ihre app versucht, eine Hintergrundaufgabe mit einem Trigger zu registrieren, die nicht im Manifest aufgeführt ist, wird die Registrierung der Hintergrundaufgabe mit dem Fehler "Runtime-Klasse nicht registriert" fehl.

1.  Öffnen Sie den Paketmanifest-Designer durch Öffnen der Datei namens „Package.appxmanifest“.
2.  Öffnen Sie die Registerkarte **Deklarationen**.
3.  Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Hintergrundaufgaben** aus, und klicken Sie auf **Hinzufügen**.
4.  Aktivieren Sie das Kontrollkästchen **Systemereignis**.
5.  In der **Einstiegspunkt:** Textbox, geben Sie den Namespace und den Namen der Hintergrundklasse in diesem Beispiel Tasks.ExampleBackgroundTask lautet.
6.  Schließen Sie den Manifest-Designer.

Das folgende Erweiterungselement wird zur Datei „Package.appxmanifest“ hinzugefügt, um die Hintergrundaufgabe zu registrieren:

```xml
<Extensions>
  <Extension Category="windows.backgroundTasks" EntryPoint="Tasks.ExampleBackgroundTask">
    <BackgroundTasks>
      <Task Type="systemEvent" />
    </BackgroundTasks>
  </Extension>
</Extensions>
```

## <a name="summary-and-next-steps"></a>Zusammenfassung und nächste Schritte

Sie sollten jetzt über die Grundlagen verfügen, um eine Hintergrundaufgabenklasse zu schreiben, die Hintergrundaufgabe in Ihrer App zu registrieren und Ihre App so zu konfigurieren, dass Sie den Abschluss der Hintergrundaufgabe erkennt. Sie sollten auch mit der Aktualisierung des Anwendungsmanifests vertraut sein, damit Ihre App die Hintergrundaufgabe erfolgreich registrieren kann.

> [!NOTE]
> Laden Sie das [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) herunter, um ähnliche Codebeispiele im Kontext einer vollständigen und stabilen UWP-App (Universelle Windows-Plattform) mit Hintergrundaufgaben zu erhalten.

Eine API-Referenz, konzeptionelle Richtlinien zu Hintergrundaufgaben und ausführlichere Anweisungen zum Schreiben von Apps, die Hintergrundaufgaben verwenden, finden Sie unter den folgenden verwandten Themen:

## <a name="related-topics"></a>Verwandte Themen

**Ausführliche Themen mit Anweisungen zu Hintergrundaufgaben**

* [Reagieren auf Systemereignisse mit Hintergrundaufgaben](respond-to-system-events-with-background-tasks.md)
* [Registrieren einer Hintergrundaufgabe](register-a-background-task.md)
* [Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md)
* [Verwenden eines Wartungsauslösers](use-a-maintenance-trigger.md)
* [Behandeln einer abgebrochenen Hintergrundaufgabe](handle-a-cancelled-background-task.md)
* [Überwachen des Status und Abschlusses von Hintergrundaufgaben](monitor-background-task-progress-and-completion.md)
* [Ausführen einer Hintergrundaufgabe für einen Timer](run-a-background-task-on-a-timer-.md)
* [Erstellen und Registrieren einer In-Process-Hintergrundaufgabe](create-and-register-an-inproc-background-task.md).
* [Konvertieren einer Out-of-Process-Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe](convert-out-of-process-background-task.md)  

**Ratschläge zu Hintergrundaufgaben**

* [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md)
* [Debuggen einer Hintergrundaufgabe](debug-a-background-task.md)
* [So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)](http://go.microsoft.com/fwlink/p/?linkid=254345)

**Hintergrundaufgabe – API-Referenz**

* [**Windows.ApplicationModel.Background**](https://msdn.microsoft.com/library/windows/apps/br224847)
