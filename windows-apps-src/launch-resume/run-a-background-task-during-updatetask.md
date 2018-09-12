---
author: TylerMSFT
title: Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird
description: Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die ausgeführt wird, wenn die Store-App Ihrer Universellen Windows-Plattform (UWP) aktualisiert wird.
ms.author: twhitney
ms.date: 04/21/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10 Uwp Update, Hintergrund, Updatetask, Hintergrund
ms.localizationpriority: medium
ms.openlocfilehash: fcba2cb736f86cebc6d2664e2ec3b557d47c86d7
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2018
ms.locfileid: "3931282"
---
# <a name="run-a-background-task-when-your-uwp-app-is-updated"></a>Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird

Erfahren Sie, wie eine Hintergrundaufgabe schreiben, nachdem Ihre app universelle Windows-Plattform (UWP) Speicher aktualisiert.

Hintergrundtask Aktualisierung wird vom Betriebssystem aufgerufen, nachdem ein Update auf eine Anwendung installiert, die auf dem Gerät installiert ist. Dadurch wird Ihre app Initialisierung Aufgaben wie initialisieren einen neuen Kanal zur Push-Benachrichtigung, Datenbankschema usw., zu aktualisieren, bevor der Benutzer die aktualisierte Anwendung startet.

Unterscheidet sich der Update-Task starten eine Hintergrundaufgabe [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) Trigger verwenden, da in diesem Fall Ihre Anwendung mindestens einmal ausgeführt werden muss vor der Aktualisierung den Hintergrundtask registrieren, der von der **aktiviert werden ServicingComplete** Trigger.  Update-Task ist nicht registriert und so eine app, die nie ausgeführt wurden aber, die aktualisiert wird, wird weiterhin der Update-Task ausgelöst.

## <a name="step-1-create-the-background-task-class"></a>Schritt 1: Erstellen der hintergrundaufgabenklasse

Als implementiert mit anderen Hintergrundaufgaben Hintergrundtask Aktualisierungstask als Windows-Runtime-Komponente. Um diese Komponente zu erstellen, führen Sie die Schritte im Abschnitt **Erstellen Hintergrundtask Klasse** [Erstellen](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)und einen prozessexternen der Hintergrundaufgabe. Dazu gehören die folgenden Schritte:

- Hinzufügen eines Projekts für eine Komponente für Windows-Runtime zu Ihrer Projektmappe
- Erstellen eines Verweises auf die Komponente Ihrer App.
- Öffentliche, versiegelte Klasse in der Komponente erstellen, die implementiert [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794).
- Implementieren der Methode [**ausgeführt**](https://msdn.microsoft.com/library/windows/apps/br224811) , ist die erforderlichen Einstiegspunkt, der aufgerufen wird, wenn der Update-Task ausgeführt wird. Wenn Sie asynchrone Aufrufe von der Hintergrundaufgabe möchten, erläutert [Erstellen und Registrieren einer prozessexternen der Hintergrundtask](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) eine Rückstellung in der **Run** -Methode verwenden.

Sie müssen diese Hintergrundaufgabe (dem Bereich "Registrieren der Hintergrundtask ausgeführt" im Thema **Erstellen und Registrieren einer Hintergrundaufgabe von prozessexternen** ) anmelden den Update-Task. Dies ist der Hauptgrund, einen Update-Task verwenden, da Sie Code für Ihre Anwendung registrieren die Aufgabe hinzufügen müssen und die app nicht mindestens einmal vor der Aktualisierung registrieren Hintergrundtask ausgeführt.

Der folgende Beispielcode zeigt grundlegenden Ausgangspunkt für eine Update-Task hintergrundaufgabenklasse in C#. Hintergrundaufgabenklasse selbst- und andere Klassen im Projekt Aufgabe Hintergrund - müssen **Öffentliche** und **versiegelt**sein. Die Hintergrund Aufgabenklasse muss **IBackgroundTask** ableiten und öffentliche **Run()** Methode mit der Signatur unten:

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

## <a name="step-2-declare-your-background-task-in-the-package-manifest"></a>Schritt 2: Deklarieren der Hintergrundtask im Paketmanifest

Im Visual Studio-Projektmappen-Explorer mit der rechten Maustaste **Package.appxmanifest** und klicken Sie auf **Code anzeigen** , um das Paketmanifest anzuzeigen. Fügen Sie den folgenden `<Extensions>` XML der Aktualisierungstask deklarieren:

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

Im obigen XML stellen sicher, dass die `EntryPoint` Attributsatz namespace.class Namen der Klasse Aufgabe aktualisieren. Der Namen beachtet werden.

## <a name="step-3-debugtest-your-update-task"></a>Schritt 3: Debug/Test der Update-task

Stellen Sie sicher, dass Sie Ihre Anwendung auf Ihrem Computer bereitgestellt haben, damit etwas aktualisieren.

Legen Sie einen Haltepunkt in der Run() der Hintergrundaufgabe.

![Haltepunkt festlegen](images/run-func-breakpoint.png)

Anschließend im Projektmappen-Explorer klicken Sie app Projekt (nicht der Hintergrund Task) und dann auf **Eigenschaften**. Im Eigenschaftenfenster Anwendung **Debuggen** links klicken **nicht gestartet, aber mein Code beim Start zu debuggen**:

![Festlegen von Debuggereinstellungen](images/do-not-launch-but-debug.png)

Weiter, um sicherzustellen, dass die UpdateTask ausgelöst wird, erhöhen Sie das Paket Versionsnummer. Doppelklicken Sie im Projektmappen-Explorer auf Ihre app **Package.appxmanifest** im Paket-Designer öffnen und aktualisieren Sie **der Buildnummer** :

![Aktualisieren Sie die version](images/bump-version.png)

Nun Visual Studio 2017 Wenn Sie F5 drücken, Ihre app aktualisiert und das System aktivieren UpdateTask Komponente im Hintergrund. Der Debugger wird automatisch im Hintergrundprozess zugeordnet. Der Haltepunkt getroffen wird und der Aktualisierungslogik Code durchgehen.

Wenn der Hintergrundtask können Sie die Vordergrund-app im Windows-Startmenü innerhalb derselben Debugsitzung starten. Debugger wird automatisch angefügt, diesmal der Vordergrundprozess und der Anwendungslogik durchlaufen.

> [!NOTE]
> Visual Studio 2015 Benutzer: die oben beschriebenen Schritte gelten für Visual Studio 2017. Wenn Sie Visual Studio 2015 verwenden, können Sie dasselbe Trigger und Test UpdateTask mit Ausnahme von Visual Studio nicht anfügen wird. Eine andere Möglichkeit ist eine [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) , die die UpdateTask als Einsprungpunkt festlegt, zu lösen die Ausführung direkt von der Vordergrund-app VS 2015.

## <a name="see-also"></a>Weitere Informationen:

[Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)
