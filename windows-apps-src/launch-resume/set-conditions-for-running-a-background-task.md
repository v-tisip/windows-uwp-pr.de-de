---
author: TylerMSFT
title: Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe
description: Erfahren Sie, wie Bedingungen festgelegt werden, die steuern, wann die Hintergrundaufgabe ausgeführt wird.
ms.assetid: 10ABAC9F-AA8C-41AC-A29D-871CD9AD9471
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Hintergrund Aufgabe
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
ms.openlocfilehash: 556a787eb1e92e4c8adb7457235afb45c02df2dc
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2813782"
---
# <a name="set-conditions-for-running-a-background-task"></a>Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe

**Wichtige APIs**

- [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834)
- [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835)
- [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)

Erfahren Sie, wie Bedingungen festgelegt werden, die steuern, wann die Hintergrundaufgabe ausgeführt wird.

In manchen Fällen erfordern Hintergrundaufgaben bestimmte Zustände, die für den Hintergrund Vorgang erfolgreich eingehalten werden. Wenn Sie Ihre Hintergrundaufgabe registrieren, können Sie mit [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835) eine oder mehrere Bedingungen angeben. Nach der Trigger ausgelöst wurde, wird die Bedingung überprüft werden soll. Klicken Sie dann die Hintergrundaufgabe Warteschlange abgelegt werden, aber es wird nicht ausgeführt, bis alle erforderlichen Bedingungen erfüllt sind.

Bedingungen auf Hintergrundaufgaben an speichert Akkulaufzeit und CPU indem verhindert, dass Aufgaben unnötig ausgeführt. Wenn Ihre Hintergrundaufgabe z. B. nach einem Timer ausgeführt wird und eine Internetverbindung benötigt, fügen Sie die **InternetAvailable**-Bedingung zum [**TaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) hinzu, bevor Sie die Aufgabe registrieren. So wird verhindert, dass die Aufgabe unnötig Systemressourcen nutzt und Akkulaufzeit beansprucht, da nur die Hintergrundaufgabe ausgeführt wird, wenn der Timer abgelaufen *und* das Internet verfügbar ist.

Es ist auch möglich, mehrere Bedingungen durch Aufrufen von **AddCondition** mehrmals für den gleichen [**TaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)kombinieren. Achten Sie darauf, keine in Konflikt stehenden Bedingungen wie **UserPresent** und **UserNotPresent** hinzuzufügen.

## <a name="create-a-systemcondition-object"></a>Erstellen eines SystemCondition-Objekts

Dieses Thema setzt voraus, dass Sie Ihrer App bereits eine Hintergrundaufgabe zugeordnet haben und dass Ihre App Code enthält, der ein [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)-Objekt namens **taskBuilder** erstellt.  Wenn Sie zuerst eine Hintergrundaufgabe erstellen müssen, lesen Sie [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen](create-and-register-an-inproc-background-task.md) oder [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](create-and-register-a-background-task.md).

Dieses Thema gilt für Hintergrundaufgaben, die in einem Prozess außerhalb von Prozessen ausgeführt werden, sowie für solche, die im gleichen Prozess wie die Vordergrund-App ausgeführt werden.

Erstellen Sie bevor Sie die Bedingung hinzufügen ein [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834) -Objekt, um die Bedingung darstellen, die in Kraft für einen Vorgang Hintergrund ausgeführt werden müssen. Geben Sie in den Konstruktor die Bedingung, die mit einer [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835) -Enumerationswert erfüllt sein muss.

Der folgende Code erstellt ein [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834) -Objekt, das die Bedingung **InternetAvailable** angibt:

```csharp
SystemCondition internetCondition = new SystemCondition(SystemConditionType.InternetAvailable);
```

```cppwinrt
Windows::ApplicationModel::Background::SystemCondition internetCondition{
    Windows::ApplicationModel::Background::SystemConditionType::InternetAvailable };
```

```cpp
SystemCondition ^ internetCondition = ref new SystemCondition(SystemConditionType::InternetAvailable);
```

## <a name="add-the-systemcondition-object-to-your-background-task"></a>Hinzufügen des SystemCondition-Objekts zur Hintergrundaufgabe

Um die Bedingung hinzuzufügen, rufen Sie die [**AddCondition**](https://msdn.microsoft.com/library/windows/apps/br224769)-Methode für das [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)-Objekt auf, und übergeben Sie das [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834)-Objekt an die Methode.

Der folgende Code verwendet **TaskBuilder** , um die Bedingung **InternetAvailable** hinzuzufügen.

```csharp
taskBuilder.AddCondition(internetCondition);
```

```cppwinrt
taskBuilder.AddCondition(internetCondition);
```

```cpp
taskBuilder->AddCondition(internetCondition);
```

## <a name="register-your-background-task"></a>Registrieren Sie die Hintergrundaufgabe.

Sie können nun Ihre Hintergrundaufgabe registrieren, mit der [**Registrieren**](https://msdn.microsoft.com/library/windows/apps/br224772) -Methode und der Hintergrundtask wird nicht gestartet werden, bis die angegebene Bedingung erfüllt ist.

Der folgende Code registriert die Aufgabe und speichert das resultierende BackgroundTaskRegistration-Objekt:

```csharp
BackgroundTaskRegistration task = taskBuilder.Register();
```

```cppwinrt
Windows::ApplicationModel::Background::BackgroundTaskRegistration task{ recurringTaskBuilder.Register() };
```

```cpp
BackgroundTaskRegistration ^ task = taskBuilder->Register();
```

> [!NOTE]
> Universelle Windows-Apps müssen jedoch [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen, bevor Hintergrund-Triggertypen registriert werden.

Rufen Sie [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) und anschließend [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) auf, wenn die App nach der Aktualisierung gestartet wird, um sicherzustellen, dass Ihre universelle Windows-App nach der Veröffentlichung eines Updates weiterhin ordnungsgemäß ausgeführt wird. Weitere Informationen finden Sie unter [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md).

> [!NOTE]
> Parameter für die Registrierung von Hintergrundaufgaben werden zum Zeitpunkt der Registrierung überprüft. Bei ungültigen Registrierungsparametern wird ein Fehler zurückgegeben. Stellen Sie sicher, dass Ihre App Szenarien, in denen die Registrierung von Hintergrundaufgaben einen Fehler verursacht, problemlos verarbeitet.

## <a name="place-multiple-conditions-on-your-background-task"></a>Einfügen mehrerer Bedingungen für die Hintergrundaufgabe

Zum Hinzufügen mehrerer Bedingungen ruft Ihre App die [**AddCondition**](https://msdn.microsoft.com/library/windows/apps/br224769) -Methode mehrmals auf. Diese Aufrufe müssen stattfinden, bevor die Aufgabenregistrierung wirksam wird.

> [!NOTE]
> Achten Sie darauf, einer Hintergrundaufgabe keine in Konflikt stehenden Bedingungen hinzuzufügen.

Der folgende Codeausschnitt zeigt mehrere Bedingungen im Kontext von erstellen und Registrieren einer Hintergrundaufgabe.

```csharp
// Set up the background task.
TimeTrigger hourlyTrigger = new TimeTrigger(60, false);

var recurringTaskBuilder = new BackgroundTaskBuilder();

recurringTaskBuilder.Name           = "Hourly background task";
recurringTaskBuilder.TaskEntryPoint = "Tasks.ExampleBackgroundTaskClass";
recurringTaskBuilder.SetTrigger(hourlyTrigger);

// Begin adding conditions.
SystemCondition userCondition     = new SystemCondition(SystemConditionType.UserPresent);
SystemCondition internetCondition = new SystemCondition(SystemConditionType.InternetAvailable);

recurringTaskBuilder.AddCondition(userCondition);
recurringTaskBuilder.AddCondition(internetCondition);

// Done adding conditions, now register the background task.

BackgroundTaskRegistration task = recurringTaskBuilder.Register();
```

```cppwinrt
// Set up the background task.
Windows::ApplicationModel::Background::TimeTrigger hourlyTrigger{ 60, false };

Windows::ApplicationModel::Background::BackgroundTaskBuilder recurringTaskBuilder;

recurringTaskBuilder.Name(L"Hourly background task");
recurringTaskBuilder.TaskEntryPoint(L"Tasks.ExampleBackgroundTaskClass");
recurringTaskBuilder.SetTrigger(hourlyTrigger);

// Begin adding conditions.
Windows::ApplicationModel::Background::SystemCondition userCondition{
    Windows::ApplicationModel::Background::SystemConditionType::UserPresent };
Windows::ApplicationModel::Background::SystemCondition internetCondition{
    Windows::ApplicationModel::Background::SystemConditionType::InternetAvailable };

recurringTaskBuilder.AddCondition(userCondition);
recurringTaskBuilder.AddCondition(internetCondition);

// Done adding conditions, now register the background task.
Windows::ApplicationModel::Background::BackgroundTaskRegistration task{ recurringTaskBuilder.Register() };
```

```cpp
// Set up the background task.
TimeTrigger ^ hourlyTrigger = ref new TimeTrigger(60, false);

auto recurringTaskBuilder = ref new BackgroundTaskBuilder();

recurringTaskBuilder->Name           = "Hourly background task";
recurringTaskBuilder->TaskEntryPoint = "Tasks.ExampleBackgroundTaskClass";
recurringTaskBuilder->SetTrigger(hourlyTrigger);

// Begin adding conditions.
SystemCondition ^ userCondition     = ref new SystemCondition(SystemConditionType::UserPresent);
SystemCondition ^ internetCondition = ref new SystemCondition(SystemConditionType::InternetAvailable);

recurringTaskBuilder->AddCondition(userCondition);
recurringTaskBuilder->AddCondition(internetCondition);

// Done adding conditions, now register the background task.
BackgroundTaskRegistration ^ task = recurringTaskBuilder->Register();
```

## <a name="remarks"></a>Hinweise

> [!NOTE]
> Wählen Sie die Bedingungen für Ihre Hintergrundaufgabe, sodass er nur ausgeführt wird, wenn es erforderlich ist, und wird nicht ausgeführt, wenn es sollte nicht. Unter [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835) finden Sie Beschreibungen der verschiedenen Bedingungen für Hintergrundaufgaben.

## <a name="related-topics"></a>Verwandte Themen

* [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](create-and-register-a-background-task.md)
* [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen](create-and-register-an-inproc-background-task.md)
* [Deklarieren von Hintergrundaufgaben im Anwendungsmanifest](declare-background-tasks-in-the-application-manifest.md)
* [Behandeln einer abgebrochenen Hintergrundaufgabe](handle-a-cancelled-background-task.md)
* [Überwachen des Status und Abschlusses von Hintergrundaufgaben](monitor-background-task-progress-and-completion.md)
* [Registrieren einer Hintergrundaufgabe](register-a-background-task.md)
* [Reagieren auf Systemereignisse mit Hintergrundaufgaben](respond-to-system-events-with-background-tasks.md)
* [Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe](update-a-live-tile-from-a-background-task.md)
* [Verwenden eines Wartungsauslösers](use-a-maintenance-trigger.md)
* [Ausführen einer Hintergrundaufgabe für einen Timer](run-a-background-task-on-a-timer-.md)
* [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md)
* [Debuggen einer Hintergrundaufgabe](debug-a-background-task.md)
* [So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)](http://go.microsoft.com/fwlink/p/?linkid=254345)
