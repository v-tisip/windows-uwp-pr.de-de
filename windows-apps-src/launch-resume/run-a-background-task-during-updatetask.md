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
ms.sourcegitcommit: 3727445c1d6374401b867c78e4ff8b07d92b7adc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "2909767"
---
# <a name="run-a-background-task-when-your-uwp-app-is-updated"></a>Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird

Erfahren Sie, wie Sie eine Hintergrundaufgabe zu schreiben, die ausgeführt wird, nachdem Ihre universelle Windows-Plattform (UWP)-Store-app aktualisiert wird.

Die Hintergrundaufgabe aktualisieren Aufgabe wird vom Betriebssystem aufgerufen, nachdem der Benutzer ein Update für eine app installiert hat, die auf dem Gerät installiert ist. Dadurch können Ihre app an die Initialisierung Aufgaben, z. B. initialisieren einen neuen Kanal für Pushbenachrichtigungen, Datenbankschema usw., aktualisieren, bevor der Benutzer die aktualisierte app startet.

Die Update-Aufgabe unterscheidet sich von Starten einer Hintergrundaufgabe mithilfe des [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) Triggers, da in diesem Fall Ihre app mindestens einmal ausführen muss, bevor er aktualisiert wird, um die Hintergrundaufgabe zu registrieren, die durch die **aktiviert werden ServicingComplete** Trigger.  Die Aufgabe aktualisieren ist nicht registriert und daher eine app, die nie ausgeführt wurde, aber, die aktualisiert wird, wird auch seine Aktualisierungsaufgabe ausgelöst.

## <a name="step-1-create-the-background-task-class"></a>Schritt 1: Erstellen der hintergrundaufgabenklasse

Als implementiert mit anderen Arten von Hintergrundaufgaben, die Hintergrundaufgabe Update-Task als Windows-Runtime-Komponente. Um diese Komponente zu erstellen, führen Sie die Schritte im Abschnitt **zum Erstellen der Hintergrundaufgabe-Klasse** [Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task). Dazu gehören die folgenden Schritte:

- Hinzufügen eines Projekts für eine Komponente für Windows-Runtime zu Ihrer Projektmappe
- Erstellen einen Verweis auf die Komponente aus Ihrer app.
- Erstellen einer Klasse öffentlichen und versiegelten in der Komponente, die wird [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)implementiert.
- Implementieren die [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811) -Methode, d.h. der erforderlichen Einstiegspunkt, der aufgerufen wird, wenn die Update-Aufgabe ausgeführt wird. Wenn Sie beabsichtigen, asynchrone Aufrufe über Ihre Hintergrundaufgabe auszuführen, erläutert [Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) eine Verzögerung in der **Run** -Methode zu verwenden.

Sie müssen diese Hintergrundaufgabe ("Registrieren der Hintergrundaufgabe ausgeführt" im Abschnitt im Thema **Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe** ) zu registrieren, um die Update-Aufgabe zu verwenden. Dies ist der Hauptgrund für eine Aufgabe Update verwenden, da Sie keinen Code zu Ihrer app zum Registrieren der Aufgabe hinzufügen müssen und die app muss nicht mindestens einmal vor dem aktualisiert, um die Hintergrundaufgabe registrieren ausgeführt werden.

Der folgende Beispielcode zeigt einen einfachen Startpunkt für eine hintergrundaufgabenklasse Aktualisierungsaufgabe in c#. Die hintergrundaufgabenklasse selbst- und alle anderen Klassen im hintergrundaufgabenprojekt - müssen **öffentlich** und **versiegelt**sein. Die Klasse der Hintergrundaufgabe muss **IBackgroundTask** ableiten und verfügen über eine öffentliche **Run()** -Methode mit der Signatur unten dargestellt:

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

Klicken Sie im Visual Studio-Projektmappen-Explorer mit der rechten Maustaste **"Package.appxmanifest"** , und klicken Sie auf **Code anzeigen** , um das Paketmanifest anzuzeigen. Fügen Sie die folgenden `<Extensions>` XML, Ihre Update-Aufgabe zu deklarieren:

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

Im XML-Code oben, stellen Sie sicher, dass die `EntryPoint` -Attribut auf den Namen namespace.class Ihre Update Task-Klasse festgelegt ist. Der Name ist Groß-/Kleinschreibung berücksichtigt.

## <a name="step-3-debugtest-your-update-task"></a>Schritt 3: Debug/Test Ihrer Aufgabe Update

Stellen Sie sicher, dass Sie Ihre app auf Ihrem Computer bereitgestellt haben, damit etwas zu aktualisieren.

Legen Sie einen Haltepunkt in der Methode Run() Ihrer Hintergrundaufgabe.

![Set-Haltepunkt](images/run-func-breakpoint.png)

Als Nächstes im Projektmappen-Explorer mit der rechten Maustaste in der app Projekt (nicht das hintergrundaufgabenprojekt), und klicken Sie dann auf **Eigenschaften**. Im Eigenschaftenfenster Anwendung auf **Debuggen** , auf der linken Seite, und wählen Sie **zunächst nicht starten, sondern Debuggen Sie eigenen Code beim Starten**:

![Debugeinstellungen legen](images/do-not-launch-but-debug.png)

Um sicherzustellen, dass die UpdateTask ausgelöst wird, erhöhen Sie als Nächstes Versionsnummer des Pakets. Klicken Sie im Projektmappen-Explorer doppelklicken Sie auf der app **Datei "Package.appxmanifest** ", um den Designer zu öffnen, und aktualisieren Sie die **Build** -Nummer:

![Aktualisieren Sie die version](images/bump-version.png)

Nun, in Visual Studio 2017 Wenn Sie F5 drücken, wird Ihre app aktualisiert und das System wird Ihre Komponente UpdateTask im Hintergrund aktivieren. Der Debugger wird automatisch mit um den Hintergrundprozess. Ihre Haltepunkt wird erreicht abrufen und Sie können über Ihre Codelogik Update schrittweise.

Wenn die Hintergrundaufgabe abgeschlossen ist, können Sie die Vordergrund-app aus dem Windows-Startmenü innerhalb der gleichen Debugsitzung starten. Automatisch wieder der Debugger angehängt wird, wird dieses Mal im Vordergrund-Prozess, und Sie können Ihre app-Logik durchlaufen.

> [!NOTE]
> Visual Studio 2015-Benutzer: die oben genannten Schritte gelten für Visual Studio 2017. Wenn Sie Visual Studio 2015 verwenden, können Sie die gleichen Techniken zur Trigger und Testen der UpdateTask, mit Ausnahme von Visual Studio keine Verbindung herstellen wird. Eine andere Möglichkeit ist, richten Sie eine [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) , die die UpdateTask wie den Einstiegspunkt festlegt, und lösen Sie die Ausführung direkt von der Vordergrund-app in VS 2015.

## <a name="see-also"></a>Weitere Informationen:

[Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)
