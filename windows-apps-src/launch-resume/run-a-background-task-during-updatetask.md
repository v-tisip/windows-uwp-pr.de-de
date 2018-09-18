---
author: TylerMSFT
title: Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird
description: Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die ausgeführt wird, wenn die Store-App Ihrer Universellen Windows-Plattform (UWP) aktualisiert wird.
ms.author: twhitney
ms.date: 04/21/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Update, Hintergrundaufgabe, Updatetask, Hintergrundaufgabe
ms.localizationpriority: medium
ms.openlocfilehash: fcba2cb736f86cebc6d2664e2ec3b557d47c86d7
ms.sourcegitcommit: f5321b525034e2b3af202709e9b942ad5557e193
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2018
ms.locfileid: "4022474"
---
# <a name="run-a-background-task-when-your-uwp-app-is-updated"></a>Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird

Erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die ausgeführt wird, nachdem Ihre universelle Windows-Plattform (UWP)-Store-app aktualisiert wird.

Die Hintergrundaufgabe Update Aufgabe wird vom Betriebssystem aufgerufen, nachdem der Benutzer zu einer app ein Update installiert, die auf dem Gerät installiert ist. Dies kann Ihre app Initialisierung Aufgaben, z. B. initialisieren einen neuen pushbenachrichtigungskanal, das Schema der Datenbank usw., zu aktualisieren, bevor der Benutzer die aktualisierte app startet.

Die Update Aufgabe unterscheidet sich von Starten einer Hintergrundaufgabe mithilfe des [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) Triggers, da in diesem Fall Ihre app mindestens einmal ausführen muss, bevor er aktualisiert wird, um die Hintergrundaufgabe zu registrieren, die mit der **aktiviert werden ServicingComplete** Trigger.  Die Aufgabe aktualisieren ist nicht registriert und so eine app, die nie ausgeführt wurde, jedoch, die aktualisiert wird, wird auch seine Update Aufgabe ausgelöst.

## <a name="step-1-create-the-background-task-class"></a>Schritt 1: Erstellen der hintergrundaufgabenklasse

Als implementiert mit anderen Arten von Hintergrundaufgaben, die Hintergrundaufgabe Update Aufgabe als Windows-Runtime-Komponente. Um diese Komponente zu erstellen, führen Sie die Schritte im Abschnitt **zum Erstellen der Hintergrundaufgabe-Klasse** [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task). Dazu gehören die folgenden Schritte:

- Hinzufügen eines Projekts für eine Komponente für Windows-Runtime zu Ihrer Projektmappe
- Erstellen einen Verweis auf die Komponente aus Ihrer app.
- Eine Klasse öffentliche und versiegelte in der Komponente erstellen, die wird [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)implementiert.
- Implementieren die [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811) -Methode, ist die der erforderlichen Einstiegspunkt, der aufgerufen wird, wenn das Update Aufgabe ausgeführt wird. Wenn Sie beabsichtigen, asynchrone Aufrufe über Ihre Hintergrundaufgabe auszuführen, erläutert [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) , wie Sie eine Verzögerung in der **Run** -Methode zu verwenden.

Sie müssen diese Hintergrundaufgabe ("Registrieren der Hintergrundaufgabe ausgeführt" im Abschnitt im Thema **Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen** ) zu registrieren, um die Update Aufgabe zu verwenden. Dies ist der Hauptgrund, ein Update Aufgabe zu verwenden, da Sie keinen Code zu Ihrer app zum Registrieren der Aufgabe hinzufügen müssen und die app nicht mindestens einmal vor dem aktualisiert, um die Hintergrundaufgabe registrieren ausgeführt werden.

Der folgende Beispielcode zeigt einen einfachen Startpunkt für eine hintergrundaufgabenklasse Update Aufgabe in c#. Die hintergrundaufgabenklasse selbst- und alle anderen Klassen im hintergrundaufgabenprojekt - müssen **öffentlich** und **versiegelt**sein. Die Klasse der Hintergrundaufgabe muss **IBackgroundTask** ableiten und verfügen über eine öffentliche **Run()** -Methode mit der Signatur unten dargestellt:

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

## <a name="step-2-declare-your-background-task-in-the-package-manifest"></a>Schritt 2: Deklarieren der Hintergrundaufgabe im Paketmanifest

Im Visual Studio-Projektmappen-Explorer mit der rechten Maustaste **"Package.appxmanifest"** , und klicken Sie auf **Code anzeigen** , um das Paketmanifest anzuzeigen. Fügen Sie die folgenden `<Extensions>` XML, Ihre Update Aufgabe zu deklarieren:

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

Im obigen XML stellen sicher, dass die `EntryPoint` -Attribut auf den namespace.class Namen der Klasse Update Aufgabe festgelegt ist. Der Name ist Groß-/Kleinschreibung berücksichtigt.

## <a name="step-3-debugtest-your-update-task"></a>Schritt 3: Debug/Test Ihrer Update Aufgabe

Stellen Sie sicher, dass Sie Ihre app auf Ihrem Computer bereitgestellt haben, damit etwas zu aktualisieren.

Legen Sie einen Haltepunkt in der Methode Run() Ihrer Hintergrundaufgabe.

![Set-Haltepunkt](images/run-func-breakpoint.png)

Als Nächstes im Projektmappen-Explorer mit der rechten Maustaste in der app Projekt (nicht das hintergrundaufgabenprojekt), und klicken Sie dann auf **Eigenschaften**. Klicken Sie im Eigenschaftenfenster Anwendung klicken Sie auf der linken Seite auf **Debuggen** , und wählen Sie **zunächst nicht starten, sondern Debuggen Sie eigenen Code beim Starten**:

![Legen Sie die Debugeinstellungen](images/do-not-launch-but-debug.png)

Um sicherzustellen, dass die UpdateTask ausgelöst wird, erhöhen Sie als Nächstes Versionsnummer des Pakets. Klicken Sie im Projektmappen-Explorer doppelklicken Sie auf der app **Datei "Package.appxmanifest** ", um den Designer zu öffnen, und aktualisieren Sie die **Build** -Nummer:

![Aktualisieren Sie die version](images/bump-version.png)

Nun in Visual Studio 2017, wenn Sie F5 drücken, wird Ihre app aktualisiert und wird das System Ihre Komponente UpdateTask im Hintergrund aktivieren. Der Debugger wird automatisch mit um den Hintergrundprozess. Der Haltepunkt wird erreicht erhalten und können Sie Ihre Update-Codelogik durchlaufen.

Wenn die Hintergrundaufgabe abgeschlossen ist, können Sie die Vordergrund-app aus dem Windows-Startmenü innerhalb der gleichen Debugsitzung starten. Automatisch wieder der Debugger angehängt wird, wird dieses Mal im Vordergrund-Prozess, und Sie können Ihre app-Logik durchlaufen.

> [!NOTE]
> Benutzer von Visual Studio 2015: die oben genannten Schritte gelten für Visual Studio 2017. Wenn Sie Visual Studio 2015 verwenden, können Sie dasselbe Trigger und Testen der UpdateTask, mit Ausnahme von Visual Studio nicht darauf angefügt wird. Eine andere Möglichkeit ist, richten Sie eine [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) , die den Einstiegspunkt der UpdateTask festgelegt, und lösen Sie die Ausführung direkt von der Vordergrund-app in Visual Studio 2015.

## <a name="see-also"></a>Weitere Informationen:

[Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)
