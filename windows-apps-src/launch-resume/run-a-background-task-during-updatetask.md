---
author: TylerMSFT
title: Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird
description: Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die ausgeführt wird, wenn die Store-App Ihrer Universellen Windows-Plattform (UWP) aktualisiert wird.
ms.author: twhitney
ms.date: 04/21/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Update, Hintergrund, Updatetask, Hintergrundaufgabe
ms.localizationpriority: medium
ms.openlocfilehash: fcba2cb736f86cebc6d2664e2ec3b557d47c86d7
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2810885"
---
# <a name="run-a-background-task-when-your-uwp-app-is-updated"></a>Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird

Erfahren Sie, wie eine Hintergrundaufgabe zu schreiben, die ausgeführt wird, nach der Aktualisierung Ihrer universellen Windows-Plattform (UWP) Store-app.

Die Aufgabe aktualisieren Hintergrundaufgabe wird vom Betriebssystem aufgerufen, nachdem der Benutzer eine app, die auf dem Gerät installiert ist, ein Update installiert. Dadurch kann Ihre app für Initialisierung Aufgaben wie die Initialisierung eines neuen Push Notification-Kanals, Datenbankschema usw., zu aktualisieren, bevor der Benutzer Ihre aktualisierte app startet.

Die Update-Aufgabe unterscheidet sich von Starten einer Hintergrundaufgabe den Auslöser [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) verwenden, da in diesem Fall Ihre app mindestens einmal ausgeführt werden muss, bevor sie aktualisiert werden, um die Hintergrundaufgabe zu registrieren, die durch die **aktiviert werden ServicingComplete** Trigger.  Die Aufgabe aktualisieren ist nicht registriert, und eine app, die nie ausgeführt wurden, aber, die aktualisiert wird, muss also noch seine Update Aufgabe ausgelöst.

## <a name="step-1-create-the-background-task-class"></a>Schritt 1: Erstellen der Hintergrund Task-Klasse

Als implementieren mit anderen Arten von Hintergrundaufgaben, Sie die Update-Task Hintergrundaufgabe als Windows-Runtime-Komponente. Wenn diese Komponente erstellen möchten, führen Sie die Schritte im Abschnitt **Erstellen der Hintergrundtask-Klasse** [Erstellen](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)und Registrieren einer Hintergrundaufgabe Out-of-Process. Dazu gehören die folgenden Schritte:

- Hinzufügen eines Projekts für eine Komponente für Windows-Runtime zu Ihrer Projektmappe
- Erstellen einen Verweis aus Ihrer app für die Komponente.
- Erstellen einer öffentlichen, versiegelten-Klasse in der Komponente implementiert [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794).
- Implementieren die [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811) -Methode, ist die der erforderlichen Einstiegspunkt, der aufgerufen wird, wenn die Update-Task ausgeführt wird. Wenn Sie beabsichtigen, asynchrone Aufrufe von Ihrer Hintergrundaufgabe erläutert [Erstellen und Registrieren einer Hintergrundaufgabe Out-of-Process-](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) eine Rückstellung in die **Run** -Methode verwenden.

Sie müssen sich nicht für diese Hintergrundaufgabe (dem Bereich "Registrieren die Hintergrundtask ausgeführt" im Thema **Create and Register eine Hintergrundaufgabe Out-of-Process-** ) anmelden, um den Update-Vorgang verwenden. Dies ist der Hauptgrund eine Update-Task verwendet werden, da Sie keinen Code Ihrer app brauchen so registrieren Sie die Aufgabe hinzufügen und die app muss nicht mindestens einmal aufrufen, bevor aktualisiert, um die Hintergrundaufgabe registrieren ausgeführt werden.

Der folgende Beispielcode zeigt grundlegenden Ausgangspunkt für eine Update-Task Hintergrund Task-Klasse in c#. Der Hintergrund Task-Klasse selbst- und alle anderen Klassen im Hintergrund Aufgabe Projekt - müssen **Öffentliche** und **versiegelt**sein. Die Hintergrund Task-Klasse muss **IBackgroundTask** ableiten und verfügen über eine öffentliche **Run()** -Methode mit der Signatur der unten gezeigten:

```cs
using Windows.ApplicationModel.Background;

namespace BackgroundTasks
{
    public sealed class UpdateTask : IBackgroundTask
    {
        public void Run(IBackgroundTaskInstance taskInstance)
        {
            // your app migration/update code here
        }
    }
}
```

## <a name="step-2-declare-your-background-task-in-the-package-manifest"></a>Schritt 2: Deklarieren Sie Ihrer Hintergrundaufgabe in der Paketmanifest

In Visual Studio-Projektmappen-Explorer mit der rechten Maustaste **Package.appxmanifest** , und klicken Sie auf **Code anzeigen** , um das Paketmanifest anzuzeigen. Fügen Sie die folgenden `<Extensions>` XML Update-Task deklariert:

```XML
<Package ...>
    ...
  <Applications>  
    <Application ...>  
        ...
      <Extensions>  
        <Extension Category="windows.updateTask"  EntryPoint="BackgroundTasks.UpdateTask">  
        </Extension>  
      </Extensions>

    </Application>  
  </Applications>  
</Package>
```

In den XML sicher, dass die `EntryPoint` -Attribut wird auf den Namen Namespace.Klasse Ihrer Update-Task-Klasse festgelegt. Der Name ist die Groß-/Kleinschreibung beachtet.

## <a name="step-3-debugtest-your-update-task"></a>Schritt 3: Debug/Test Update-task

Stellen Sie sicher, dass Sie Ihre app auf Ihrem Computer bereitgestellt haben, sodass etwas aktualisieren.

Setzen Sie einen Haltepunkt in der Run()-Methode der Hintergrundaufgabe.

![Haltepunkt festlegen](images/run-func-breakpoint.png)

Im nächsten Schritt im Projektmappen-Explorer mit der rechten Maustaste Ihrer app-Projekt (nicht das Vorgangsfeld Projekt Hintergrund), und klicken Sie dann auf **Eigenschaften**. Klicken Sie im Fenster Eigenschaften Application auf der linken Seite auf **Debuggen** , und wählen Sie dann **nicht gestartet, aber mein Code beim Start zu debuggen**:

![Debug-Einstellungen](images/do-not-launch-but-debug.png)

Im nächsten Schritt, um sicherzustellen, dass die UpdateTask ausgelöst wird, erhöhen Sie das Paket Versionsnummer an. Doppelklicken Sie im Projektmappen-Explorer auf Ihre app **Package.appxmanifest** Datei, um den Paketdesigner zu öffnen, und klicken Sie dann aktualisieren Sie **der Buildnummer** :

![Aktualisieren der version](images/bump-version.png)

Nun in Visual Studio 2017 Wenn Sie F5 drücken, Ihre app werden aktualisiert, und das System wird die UpdateTask-Komponente im Hintergrund aktiviert. Der Debugger wird automatisch an den Hintergrundprozess. Der Haltepunkt wird erreicht erhalten möchten, und können Sie Ihr Code Aktualisierungslogik durchlaufen.

Wenn die Hintergrundaufgabe abgeschlossen ist, können Sie die Vordergrund-app aus dem Windows-Startmenü innerhalb der gleichen Sitzung Debuggen starten. Der Debugger wird automatisch erneut angefügt werden, diesmal den Prozess Vordergrund und können Sie Ihre app Logik durchlaufen.

> [!NOTE]
> Benutzer von Visual Studio 2015: die oben beschriebenen Schritte gelten für Visual Studio 2017. Wenn Sie Visual Studio 2015 verwenden, können Sie dieselben Techniken Trigger und Testen der UpdateTask, mit Ausnahme von Visual Studio nicht darauf angefügt wird. Ein alternatives Verfahren in VS 2015 ist zum Einrichten einer [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) , die die UpdateTask als ihr Einstiegspunkt festlegt, und lösen die Ausführung direkt in den Vordergrund-app.

## <a name="see-also"></a>Weitere Informationen

[Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)
